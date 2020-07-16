---
title: C-Laufzeitfehler R6035
ms.date: 11/04/2016
f1_keywords:
- R6035
helpviewer_keywords:
- R6035
ms.assetid: f8fb50b8-18bf-4258-b96a-b0a9de468d16
ms.openlocfilehash: 9b92b1e2e123201d4f50422754b77f62b2ec943b
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404397"
---
# <a name="c-runtime-error-r6035"></a>C-Laufzeitfehler R6035

Microsoft Visual C++-Laufzeitbibliothek, Fehler R6035 – Ein Modul in dieser Anwendung initialisiert das globale Sicherheitscookie dieses Moduls, während eine Funktion aktiv ist, die sich auf dieses Sicherheitscookie stützt.  Rufen Sie zuvor __security_init_cookie auf.

[__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md) muss vor der ersten Verwendung des globalen Sicherheits Cookies aufgerufen werden.

Das globale Sicherheits Cookie wird zum Schutz vor Pufferüberlauf in Code verwendet, der mit [/GS (Puffer-Sicherheitsüberprüfung)](../../build/reference/gs-buffer-security-check.md) kompiliert wurde, und in Code, der die strukturierte Ausnahmebehandlung verwendet. Im Wesentlichen geschieht Folgendes: Beim Einstieg in eine vor Pufferüberlauf geschützte Funktion wird das Cookie auf dem Stapel abgelegt, und bei Funktionsende wird der Wert auf dem Stapel mit dem globalen Cookie verglichen. Jeglicher Unterschied zwischen diesen Werten weist darauf hin, dass ein Pufferüberlauf eingetreten ist. Das Programm wird daraufhin sofort beendet.

Fehler R6035 weist darauf hin, dass `__security_init_cookie` nach Eingabe einer geschützten Funktion aufgerufen wurde. Ein Fortsetzen der Ausführung würde zum Feststellen eines unechten Pufferüberlaufs führen, da das Cookie auf dem Stapel nicht mehr mit dem globalen Cookie übereinstimmt.

Betrachten Sie das folgende DLL-Beispiel. Der DLL-Einstiegspunkt wird durch die Option Linker [/Entry (Einstiegspunkt Symbol)](../../build/reference/entry-entry-point-symbol.md) auf DllEntryPoint festgelegt. Dies umgeht die Initialisierung durch CRT, die normalerweise das globale Sicherheitscookie initialisiert, sodass die DLL selbst `__security_init_cookie` aufrufen muss.

```
// Wrong way to call __security_init_cookie
DllEntryPoint(...) {
   DllInitialize();
   ...
   __try {
      ...
   } __except()... {
      ...
   }
}

void DllInitialize() {
   __security_init_cookie();
}
```

In diesem Beispiel wird Fehler R6035 generiert, weil DllEntryPoint eine strukturierte Ausnahmebehandlung verwendet und daher das Sicherheitscookie zum Erkennen von Pufferüberläufen verwendet. Zum Zeitpunkt des Aufrufs von DllInitialize ist das globale Sicherheitscookie bereits auf dem Stapel abgelegt.

Die richtige Vorgehensweise wird im folgenden Beispiel veranschaulicht:

```
// Correct way to call __security_init_cookie
DllEntryPoint(...) {
   __security_init_cookie();
   DllEntryHelper();
}

void DllEntryHelper() {
   ...
   __try {
      ...
   } __except()... {
      ...
   }
}
```

In diesem Fall ist DllEntryPoint nicht gegen Pufferüberläufe geschützt (es sind keine lokalen Zeichenfolgenpuffer vorhanden, und es wird keine strukturierte Ausnahmebehandlung verwendet). Daher kann hier gefahrlos `__security_init_cookie` aufgerufen werden. Anschließend wird eine geschützte Hilfsfunktion aufgerufen.

> [!NOTE]
> Die Fehlermeldung R6035 wird nur von der x86-Debug-CRT generiert, und dies auch nur für die strukturierte Ausnahmebehandlung. Die zugrunde liegende Bedingung ist jedoch auf allen Plattformen und für alle Formen der Ausnahmebehandlung ein Fehler, z. B. C++ EH.

## <a name="see-also"></a>Weitere Informationen

[Sicherheits Features in MSVC](https://devblogs.microsoft.com/cppblog/security-features-in-microsoft-visual-c/)
