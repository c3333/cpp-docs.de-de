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
ms.openlocfilehash: c84a8eca25c90e0790ec8c4991d9d5a116afa59f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442530"
---
# <a name="exporting-from-a-dll-using-__declspecdllexport"></a>Exportieren aus einer DLL mithilfe von "__declspec(dllexport)"

Sie können Daten, Funktionen, Klassen oder Klassenmember-Funktionen mithilfe des Schlüssel Worts **__declspec (dllexport)** aus einer DLL exportieren. **__declspec (dllexport)** fügt die Export Direktive zur Objektdatei hinzu, sodass Sie keine DEF-Datei verwenden müssen.

Am deutlichsten zeigt sich diese einfache Handhabung beim Exportieren von ergänzten C++-Funktionsnamen. Da es keine Standardspezifikation für die Namensergänzung gibt, kann der Name einer exportierten Funktion zwischen den einzelnen Compilerversionen variieren. Wenn Sie **__declspec (dllexport)** verwenden, ist das erneute Kompilieren der dll und der abhängigen exe-Dateien nur erforderlich, um Änderungen an der Benennungs Konvention zu berücksichtigen.

Viele Exportdirektiven, z. B. Ordinalzahlen, NONAME und PRIVATE, können nur in einer DEF-Datei angegeben werden, und es gibt keine Möglichkeit, diese Attribute ohne DEF-Datei festzulegen. Die Verwendung von **__declspec (dllexport)** zusätzlich zur Verwendung einer DEF-Datei führt jedoch nicht zu Buildfehlern.

Zum Exportieren von Funktionen muss das Schlüsselwort **__declspec (dllexport)** links neben dem Schlüsselwort Call-Convention angezeigt werden, wenn ein Schlüsselwort angegeben wird. Beispiel:

```
__declspec(dllexport) void __cdecl Function1(void);
```

Um alle öffentlichen Datenmember und Memberfunktionen einer Klasse zu exportieren, muss das Schlüsselwort, wie im nachfolgenden Beispiel dargestellt, links vom Klassennamen erscheinen:

```
class __declspec(dllexport) CExampleExport : public CObject
{ ... class definition ... };
```

> [!NOTE]
>  `__declspec(dllexport)` kann nicht mit der `__clrcall`-Aufrufkonvention für eine Funktion übernommen werden.

Beim Erstellen der DLL erstellen Sie in der Regel eine Header Datei, die die zu exportierenden Funktionsprototypen und/oder Klassen enthält, und fügen **__declspec (dllexport)** den Deklarationen in der Header Datei hinzu. Um den Code lesbarer zu gestalten, definieren Sie ein Makro für **__declspec (dllexport)** , und verwenden Sie das-Makro mit jedem Symbol, das Sie exportieren:

```
#define DllExport   __declspec( dllexport )
```

**__declspec (dllexport)** speichert Funktionsnamen in der Export Tabelle der dll. Wenn Sie die Größe der Tabelle optimieren möchten, finden Sie weitere [Informationen unter Exportieren von Funktionen aus einer DLL nach Ordinalzahl anstelle des Namens](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

## <a name="what-do-you-want-to-do"></a>Was möchten Sie tun?

- [Exportieren aus einer DLL mithilfe von DEF-Dateien](exporting-from-a-dll-using-def-files.md)

- [Exportieren und Importieren mithilfe AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exportieren C++ von Funktionen zur Verwendung in ausführbaren C-Dateien](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exportieren von c-Funktionen zur Verwendung in C++ausführbaren c-oder-Programmier Dateien](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Bestimmen der zu verwendenden Export Methode](determining-which-exporting-method-to-use.md)

- [Importieren in eine Anwendung mithilfe von __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Initialisieren einer dll](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [Das __declspec-Schlüsselwort](../cpp/declspec.md)

- [Importieren und Exportieren von Inlinefunktionen](importing-and-exporting-inline-functions.md)

- [Gegenseitige Importe](mutual-imports.md)

## <a name="see-also"></a>Weitere Informationen

[Exportieren aus einer DLL](exporting-from-a-dll.md)
