---
title: Sicherheitsfunktionen in der CRT
description: Eine Übersicht über die sicheren CRT-Funktionen in der Microsoft C-Laufzeit.
ms.date: 09/29/2020
ms.topic: conceptual
f1_keywords:
- _CRT_SECURE_NO_DEPRECATE
- _CRT_NONSTDC_NO_WARNINGS
- _CRT_SECURE_NO_WARNINGS
helpviewer_keywords:
- security deprecation warnings [C++]
- CRT_NONSTDC_NO_DEPRECATE
- buffers [C++], buffer overruns
- deprecation warnings (security-related), disabling
- _CRT_NONSTDC_NO_WARNINGS
- security [CRT]
- _CRT_SECURE_NO_WARNINGS
- _CRT_NONSTDC_NO_DEPRECATE
- _CRT_SECURE_NO_DEPRECATE
- security-enhanced CRT
- CRT_SECURE_NO_WARNINGS
- CRT_SECURE_NO_DEPRECATE
- deprecation warnings (security-related)
- buffer overruns
- CRT_NONSTDC_NO_WARNINGS
- CRT, security enhancements
- parameters [C++], validation
ms.assetid: d9568b08-9514-49cd-b3dc-2454ded195a3
ms.openlocfilehash: 963f5510350aa3be25586811889189d28a5f7b66
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589886"
---
# <a name="security-features-in-the-crt"></a>Sicherheitsfunktionen in der CRT

Viele alte CRT-Funktionen liegen in neueren, sichereren Versionen vor. Wenn eine sichere Funktion vorhanden ist, wird die ältere, weniger sichere Version als veraltet markiert, und die neue Version hat das `_s`-Suffix („sicher“).

In diesem Kontext bedeutet "deprecated", dass die Verwendung der Funktion nicht empfohlen wird. Dies bedeutet nicht, dass die Funktion aus der CRT entfernt werden soll.

Die sicheren Funktionen verhindern oder korrigieren Sicherheitsfehler. Stattdessen fangen Sie Fehler ab, wenn Sie auftreten. Sie führen zusätzliche Überprüfungen auf Fehlerbedingungen aus. Wenn ein Fehler auftritt, wird ein Fehlerhandler aufgerufen (siehe [Parameter Validierung](../c-runtime-library/parameter-validation.md)).

Die `strcpy` -Funktion kann z. b. nicht erkennen, ob die Zeichenfolge, die Sie kopiert, zu groß für den Ziel Puffer ist. Sein sicheres Pendant, `strcpy_s` , übernimmt die Größe des Puffers als Parameter. Damit kann ermittelt werden, ob ein Pufferüberlauf auftritt. Wenn Sie verwenden, `strcpy_s` um 11 Zeichen in einen 10-Zeichen Puffer zu kopieren, ist dies ein Fehler in Ihrem Teil `strcpy_s` . der Fehler kann nicht behoben werden. Es kann jedoch ihren Fehler erkennen und Sie durch Aufrufen des ungültigen Parameter Handlers informieren.

## <a name="eliminating-deprecation-warnings"></a>Beseitigen von Ablaufwarnungen

Es gibt mehrere Möglichkeiten, um Ablaufwarnungen für die älteren, weniger sicheren Funktionen zu beseitigen. Die einfachste Möglichkeit ist, `_CRT_SECURE_NO_WARNINGS` zu definieren oder das [warning](../preprocessor/warning.md)-Pragma zu verwenden. Deaktiviert entweder die veralteten Warnungen, aber die Sicherheitsprobleme, die die Warnungen verursacht haben, sind weiterhin vorhanden. Es ist besser, die Einstellung für veraltete Warnungen zu aktivieren und die neuen CRT-Sicherheitsfunktionen zu nutzen.

In C++ ist es am einfachsten, [sichere Vorlagen Überladungen](../c-runtime-library/secure-template-overloads.md)zu verwenden. Dadurch werden veraltete Warnungen eliminiert, indem Aufrufe von veralteten Funktionen durch Aufrufe von sicheren Versionen dieser Funktionen ersetzt werden. Ein Beispiel ist dieser veraltete Aufruf von `strcpy`:

```
char szBuf[10];
strcpy(szBuf, "test"); // warning: deprecated
```

Durch Definieren von `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` als 1 wird die Warnung beseitigt, indem der `strcpy`-Aufruf in `strcpy_s` geändert wird, was Pufferüberläufe verhindert. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../c-runtime-library/secure-template-overloads.md).

Für diese veralteten Funktionen ohne sichere Vorlagenüberladungen sollten Sie definitiv erwägen, den Code manuell zu aktualisieren, um die sicheren Versionen zu verwenden.

Eine andere Quelle von Ablaufwarnungen, unabhängig von der Sicherheit, sind POSIX-Funktionen. Ersetzen Sie POSIX-Funktionsnamen durch Ihre Standardentsprechungen (ändern Sie z.B. [access](../c-runtime-library/reference/access-crt.md) in [_access](../c-runtime-library/reference/access-waccess.md)), oder deaktivieren Sie POSIX-bezogene Ablaufwarnungen durch Definieren von `_CRT_NONSTDC_NO_WARNINGS`. Weitere Informationen finden Sie unter [Kompatibilität](compatibility.md).

## <a name="additional-security-features"></a>Zusätzliche Sicherheitsfunktionen

Zu den Sicherheitsfeatures gehören:

- `Parameter Validation`. Überprüfen Sie die Parameter, und überprüfen Sie die Parameter, und viele ihrer unsicheren Gegenstücke. Die Validierung kann Folgendes umfassen:

  - Überprüfen auf **null** -Werte.
  - Überprüfung von Enumerationswerten auf Gültigkeit.
  - Überprüfen, ob ganzzahlige Werte im gültigen Bereiche liegen.

- Weitere Informationen finden Sie unter [Parametervalidierung](../c-runtime-library/parameter-validation.md).

- Auf einen Handler für ungültige Parameter kann auch der Entwickler zugreifen. Wenn eine Funktion einen ungültigen Parameter erkennt, und Sie die Anwendung nicht bestätigen und beenden, können Sie mit der CRT diese Probleme über [_set_invalid_parameter_handler _set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)überprüfen.

- `Sized Buffers`. Sie müssen die Puffergröße an eine beliebige sichere Funktion übergeben, die in einen Puffer schreibt. Die sicheren Versionen überprüfen, ob der Puffer groß genug ist, bevor Sie darin schreiben. Dadurch können gefährliche Pufferüberlauf Fehler vermieden werden, die die Ausführung von bösartigem Code ermöglichen. Diese Funktionen geben in der Regel einen `errno` Fehlercode zurück und rufen den Handler für ungültige Parameter auf, wenn die Größe des Puffers zu klein ist. Funktionen, die wie `gets` aus Eingabepuffern lesen, haben sichere Versionen, die von Ihnen die Angabe einer maximalen Größe fordern.

- `Null termination`. Einige Funktionen, die potenziell nicht beendete Zeichen folgen hinterlassen, haben sichere Versionen, die sicherstellen, dass Zeichen folgen ordnungsgemäß auf Null enden.

- `Enhanced error reporting`. Die sicheren Funktionen geben Fehlercodes mit mehr Fehlerinformationen zurück, als mit den bereits vorhandenen Funktionen verfügbar waren. Die sicheren Funktionen und viele der bereits vorhandenen Funktionen legen nun fest `errno` und geben häufig auch einen `errno` Codetyp zurück, um eine bessere Fehlerberichterstattung bereitzustellen.

- `Filesystem security`. Sichere Datei-E/A-APIs unterstützen sicheren Dateizugriff im Standardfall.

- `Windows security`. Sichere Prozess-APIs setzen Sicherheitsrichtlinien durch und lassen die Angabe von ACLs zu.

- `Format string syntax checking`. Ungültige Zeichenfolgen werden erkannt, z.B. Verwendung falscher Typfeldzeichen in `printf`-Formatzeichenfolgen.

## <a name="see-also"></a>Weitere Informationen

[Parameter Validierung](../c-runtime-library/parameter-validation.md)<br/>
[Sichere Vorlagen Überladungen](../c-runtime-library/secure-template-overloads.md)<br/>
[Funktionen der CRT-Bibliothek](../c-runtime-library/crt-library-features.md)
