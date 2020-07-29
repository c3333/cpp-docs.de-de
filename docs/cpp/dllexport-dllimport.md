---
title: dllexport, dllimport
ms.date: 11/04/2016
f1_keywords:
- dllimport_cpp
- dllexport_cpp
helpviewer_keywords:
- dllexport __declspec keyword
- __declspec keyword [C++], dllexport
- dllimport __declspec keyword
- __declspec keyword [C++], dllimport
ms.assetid: ff95b645-ef55-4e72-b848-df44657b3208
ms.openlocfilehash: f03c945375cbe8c399e604e12f070b5a63d316f7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221652"
---
# <a name="dllexport-dllimport"></a>dllexport, dllimport

**Microsoft-spezifisch**

Die **`dllexport`** **`dllimport`** Speicher Klassenattribute und sind Microsoft-spezifische Erweiterungen der Programmiersprachen C und C++. Sie können sie verwenden, um Funktionen, Daten und Objekte in eine DLL zu exportieren oder von einer DLL zu importieren.

## <a name="syntax"></a>Syntax

```
   __declspec( dllimport ) declarator
   __declspec( dllexport ) declarator
```

## <a name="remarks"></a>Bemerkungen

Diese Attribute definieren explizit die Schnittstelle der DLL zu dem Client, der die ausführbare Datei oder eine andere DLL sein kann. Durch das Deklarieren von Funktionen als **`dllexport`** entfällt die Notwendigkeit einer Modul Definitionsdatei (. def), zumindest in Bezug auf die Angabe exportierter Funktionen. Das- **`dllexport`** Attribut ersetzt das **__export** -Schlüsselwort.

Wenn eine Klasse als "declspec(dllexport)" gekennzeichnet ist, werden alle Spezialisierungen von Klassenvorlagen in der Klassenhierarchie implizit als "declspec (dllexport)" gekennzeichnet. Das bedeutet, dass Klassenvorlagen explizit instanziiert werden und die Member der Klasse definiert werden müssen.

**`dllexport`** einer Funktion macht die Funktion mit dem ergänzten Namen verfügbar. Bei C++-Funktionen schließt dies Namenszerlegung mit ein. Bei C-Funktionen oder Funktionen, die als `extern "C"` deklariert werden, schließt dies plattfomspezifische Ergänzungen, die auf der Aufrufkonvention basieren, mit ein. Informationen zur namens Ergänzung in C/C++-Code finden Sie unter ergänzte [Namen](../build/reference/decorated-names.md). Es wird keine namens Ergänzung für exportierte C-Funktionen oder C++- `extern "C"` Funktionen verwendet, die die **`__cdecl`** Aufruf Konvention verwenden.

Um einen nicht ergänzten Namen zu exportieren, können Sie bei der Verknüpfung eine Moduldefinitionsdatei (.def) verwenden, die den nicht ergänzten Namen in einem EXPORTS-Abschnitt definiert. Weitere Informationen finden Sie unter [Exporte](../build/reference/exports.md). Eine andere Möglichkeit zum Exportieren eines nicht ergänzten Namens ist die Verwendung einer- `#pragma comment(linker, "/export:alias=decorated_name")` Direktive im Quellcode.

Wenn Sie oder deklarieren **`dllexport`** **`dllimport`** , müssen Sie die [Erweiterte Attribut Syntax](../cpp/declspec.md) und das- **`__declspec`** Schlüsselwort verwenden.

## <a name="example"></a>Beispiel

```cpp
// Example of the dllimport and dllexport class attributes
__declspec( dllimport ) int i;
__declspec( dllexport ) void func();
```

Um den Code lesbarer zu machen, können Sie alternativ Makrodefinitionen verwenden:

```cpp
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport void func();
DllExport int i = 10;
DllImport int j;
DllExport int n;
```

Weitere Informationen finden Sie unter

- [Definitionen und Deklarationen](../cpp/definitions-and-declarations-cpp.md)

- [Definieren von C++-Inline Funktionen mit dllexport und DllImport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

- [Allgemeine Regeln und Einschränkungen](../cpp/general-rules-and-limitations.md)

- [Verwenden von DllImport und dllexport in C++-Klassen](../cpp/using-dllimport-and-dllexport-in-cpp-classes.md)

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[__declspec](../cpp/declspec.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
