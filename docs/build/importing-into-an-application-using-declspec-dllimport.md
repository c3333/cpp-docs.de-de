---
title: Importieren in eine Anwendung mithilfe von __declspec(dllimport)
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: edb4da4e-f83a-44cf-a668-9239d49dbe42
ms.openlocfilehash: fd7d42ec5a76b92aa789a3a20f38e6b2c0fd2cb1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440411"
---
# <a name="import-into-an-application-using-__declspecdllimport"></a>Importieren in eine Anwendung mithilfe von __declspec(dllimport)

Wenn ein Programm öffentliche, durch eine DLL definierte Symbole verwendet, wird dieser Vorgang als Importieren bezeichnet. Wenn Sie Header Dateien für Anwendungen erstellen, die ihre DLLs zum Erstellen mit verwenden, verwenden Sie **__declspec (dllimport)** für die Deklarationen der öffentlichen Symbole. Das Schlüsselwort **__declspec (dllimport)** funktioniert unabhängig davon, ob Sie mit DEF-Dateien oder mit dem Schlüsselwort **__declspec (dllexport)** exportieren.

Um den Code lesbarer zu gestalten, definieren Sie ein Makro für **__declspec (dllimport)** , und verwenden Sie dann das-Makro, um jedes importierte Symbol zu deklarieren:

```
#define DllImport   __declspec( dllimport )

DllImport int  j;
DllImport void func();
```

Die Verwendung von **__declspec (dllimport)** ist bei Funktions Deklarationen optional, aber der Compiler erzeugt effizienteren Code, wenn Sie dieses Schlüsselwort verwenden. Sie müssen jedoch **__declspec (dllimport)** für die importierte ausführbare Datei verwenden, um auf die öffentlichen Daten Symbole und-Objekte der DLL zuzugreifen. Beachten Sie, dass die Benutzer Ihrer DLL noch eine Verknüpfung mit einer Importbibliothek herstellen müssen.

Sie können dieselbe Headerdatei sowohl für die DLL als auch für die Clientanwendung nutzen. Verwenden Sie zu diesem Zweck ein spezielles Präprozessorsymbol, das angibt, ob die DLL oder die Clientanwendung erstellt wird. Beispiel:

```
#ifdef _EXPORTING
   #define CLASS_DECLSPEC    __declspec(dllexport)
#else
   #define CLASS_DECLSPEC    __declspec(dllimport)
#endif

class CLASS_DECLSPEC CExampleA : public CObject
{ ... class definition ... };
```

## <a name="what-do-you-want-to-do"></a>Was möchten Sie tun?

- [Initialisieren einer dll](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [Importieren und Exportieren von Inlinefunktionen](importing-and-exporting-inline-functions.md)

- [Gegenseitige Importe](mutual-imports.md)

## <a name="see-also"></a>Weitere Informationen

[Importieren in eine Anwendung](importing-into-an-application.md)
