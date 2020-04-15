---
title: Exportieren aus einer DLL mithilfe von "__declspec(dllexport)"
ms.date: 05/06/2019
f1_keywords:
- dllexport
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- names [C++], DLL exports by
- export directives [C++]
- exporting DLLs [C++], __declspec(dllexport) keyword
ms.assetid: a35e25e8-7263-4a04-bad4-00b284458679
ms.openlocfilehash: 075962758773660085ae0b98b668c264524cc6aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328597"
---
# <a name="exporting-from-a-dll-using-__declspecdllexport"></a>Exportieren aus einer DLL mithilfe von "__declspec(dllexport)"

Sie können Daten, Funktionen, Klassen oder Klassenmemberfunktionen aus einer DLL exportieren, indem Sie das Schlüsselwort **__declspec(dllexport)** verwenden. **__declspec(dllexport)** fügt der Objektdatei die Exportdirektive hinzu, sodass Sie keine DEF-Datei verwenden müssen.

Am deutlichsten zeigt sich diese einfache Handhabung beim Exportieren von ergänzten C++-Funktionsnamen. Da es keine Standardspezifikation für die Namensergänzung gibt, kann der Name einer exportierten Funktion zwischen den einzelnen Compilerversionen variieren. Wenn Sie **__declspec(dllexport)** verwenden, ist das erneute Kompilieren der DLL und der abhängigen EXE-Dateien nur erforderlich, um Änderungen an der Namenskonvention zu berücksichtigen.

Viele Exportdirektiven, z. B. Ordinalzahlen, NONAME und PRIVATE, können nur in einer DEF-Datei angegeben werden, und es gibt keine Möglichkeit, diese Attribute ohne DEF-Datei festzulegen. Die Verwendung **von __declspec(dllexport)** sowie die Verwendung einer .def-Datei verursacht jedoch keine Buildfehler.

Zum Exportieren von Funktionen muss das Schlüsselwort **__declspec(dllexport)** links neben dem Schlüsselwort calling-convention angezeigt werden, wenn ein Schlüsselwort angegeben ist. Beispiel:

```
__declspec(dllexport) void __cdecl Function1(void);
```

Um alle öffentlichen Datenmember und Memberfunktionen einer Klasse zu exportieren, muss das Schlüsselwort, wie im nachfolgenden Beispiel dargestellt, links vom Klassennamen erscheinen:

```
class __declspec(dllexport) CExampleExport : public CObject
{ ... class definition ... };
```

> [!NOTE]
> `__declspec(dllexport)` kann nicht mit der `__clrcall`-Aufrufkonvention für eine Funktion übernommen werden.

Beim Erstellen der DLL erstellen Sie in der Regel eine Headerdatei, die die Funktionsprototypen und/oder Klassen enthält, die Sie exportieren, und fügen den Deklarationen in der Headerdatei **__declspec(dllexport)** hinzu. Um den Code lesbarer zu machen, definieren Sie ein Makro für **__declspec(dllexport)** und verwenden Sie das Makro mit jedem Symbol, das Sie exportieren:

```
#define DllExport   __declspec( dllexport )
```

**__declspec(dllexport)** speichert Funktionsnamen in der Exporttabelle der DLL. Wenn Sie die Größe der Tabelle optimieren möchten, finden Sie weitere Informationen unter [Exportieren von Funktionen aus einer DLL nach Ordinal und nicht nach Name](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

## <a name="what-do-you-want-to-do"></a>Was möchten Sie tun?

- [Exportieren aus einer DLL mithilfe von DEF-Dateien](exporting-from-a-dll-using-def-files.md)

- [Exportieren und Importieren mithilfe von AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exportieren von C++-Funktionen zur Verwendung in ausführbaren C-Dateien](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exportieren von C-Funktionen zur Verwendung in ausführbaren C- oder C++-Dateien](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Bestimmen, welche Exportmethode verwendet werden soll](determining-which-exporting-method-to-use.md)

- [Importieren in eine Anwendung mithilfe von __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Initialisieren einer DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [Das __declspec-Schlüsselwort](../cpp/declspec.md)

- [Importieren und Exportieren von Inlinefunktionen](importing-and-exporting-inline-functions.md)

- [Gegenseitige Einfuhren](mutual-imports.md)

## <a name="see-also"></a>Siehe auch

[Exportieren aus einer DLL](exporting-from-a-dll.md)
