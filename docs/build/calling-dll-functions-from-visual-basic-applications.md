---
title: Aufrufen von DLL-Funktionen aus Visual Basic-Anwendungen heraus
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], calling DLL functions from Visual Basic
- DLL functions [C++]
- function calls [C++], DLL functions
- DLLs [C++], calling
- calling DLL functions from VB applications [C++]
- __stdcall keyword [C++]
- DLL functions [C++], calling
ms.assetid: 282f7fbf-a0f2-4b9f-b277-1982710be56c
ms.openlocfilehash: 23b5692e28b9ea5b70c492e2564b8bf5385b1815
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221198"
---
# <a name="calling-dll-functions-from-visual-basic-applications"></a>Aufrufen von DLL-Funktionen aus Visual Basic-Anwendungen heraus

Damit Visual Basic-Anwendungen (oder Anwendungen in anderen Sprachen wie Pascal oder Fortran) Funktionen in einer C-/C++-DLL aufrufen können, müssen die Funktionen mit der richtigen Aufrufkonvention exportiert werden, ohne dass der Compiler Namensergänzungen vornimmt.

Mithilfe von `__stdcall` wird zwar die richtige Aufrufkonvention für die Funktion erstellt (die aufgerufene Funktion bereinigt den Stapel, und die Parameter werden von rechts nach links übergeben), der Funktionsname wird jedoch unterschiedlich ergänzt. Wenn **__declspec(dllexport)** daher für eine exportierte Funktion in einer DLL verwendet wird, wird der dekorierte Name exportiert.

Durch die `__stdcall`-Namensergänzung beginnt der Symbolname mit einem Unterstrich ( **\_** ) und endet mit einem **\@** -Zeichen, gefolgt von der Anzahl der Bytes in der Argumentliste (dem erforderlichen Stapelplatz). Ist daher eine Funktion wie folgt deklariert:

```C
int __stdcall func (int a, double b)
```

In diesem Fall wird dies in der Ausgabe als `_func@12` dekoriert.

Durch die C-Aufrufkonvention (`__cdecl`) wird der Name mit `_func` ergänzt.

Verwenden Sie [/MAP](reference/map-generate-mapfile.md), um den dekorierten Namen zu ermitteln. Die Verwendung von **__declspec(dllexport)** bewirkt Folgendes:

- Wenn die Funktion nach der C-Aufrufkonvention (`__cdecl`) exportiert wird, wird beim Export der führende Unterstrich ( **\_** ) entfernt.

- Wenn für die exportierte Funktion nicht die C-Aufrufkonvention (z. B. `__stdcall`) verwendet wird, wird der ergänzte Name exportiert.

Da es keine Möglichkeit gibt, die Stapelbereinigung an einer bestimmten Stelle zu überschreiben, muss `__stdcall` verwendet werden. Um eine Namensergänzung mit `__stdcall` rückgängig zu machen, müssen Sie sie im EXPORTS-Abschnitt der DEF-Datei mittels Aliasen angeben. Dies wird anhand der folgenden Funktionsdeklaration veranschaulicht:

```C
int  __stdcall MyFunc (int a, double b);
void __stdcall InitCode (void);
```

In der DEF-Datei:

```
EXPORTS
   MYFUNC=_MyFunc@12
   INITCODE=_InitCode@0
```

Damit DLLs durch Programme in Visual Basic aufgerufen werden können, wird die in diesem Artikel erwähnte Aliastechnik in der DEF-Datei benötigt. Wenn das Aliasing im Visual Basic-Programm durchgeführt wird, ist es in der DEF-Datei nicht notwendig. Zu diesem Zweck wird der [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement)-Anweisung im Visual Basic-Programm eine Aliasklausel hinzugefügt.

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [Exportieren aus einer DLL](exporting-from-a-dll.md)

- [Exportieren aus einer DLL mithilfe von DEF-Dateien](exporting-from-a-dll-using-def-files.md)

- [Exportieren aus einer DLL mithilfe von __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportieren von C++-Funktionen zur Verwendung in ausführbaren C-Dateien](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Festlegen der Exportmethode](determining-which-exporting-method-to-use.md)

- [Dekorierte Namen](reference/decorated-names.md)

## <a name="see-also"></a>Siehe auch

[Erstellen von C/C++-DLLs in Visual Studio](dlls-in-visual-cpp.md)
