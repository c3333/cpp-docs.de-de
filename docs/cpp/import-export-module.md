---
title: module, import, export
ms.date: 12/12/2019
f1_keywords:
- module_cpp
- import_cpp
- export_cpp
helpviewer_keywords:
- modules [C++]
- modules [C++], import
- modules [C++], export
description: Verwenden Sie Import- und Exportdeklarationen, um auf Typen und Funktionen zuzugreifen und diese zu veröffentlichen, die im angegebenen Modul definiert sind.
ms.openlocfilehash: a765e9a406660d3c945ef3d70754178b0648458c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374113"
---
# <a name="module-import-export"></a>module, import, export

Die **Modul-,** **Import-** und Exportdeklarationen sind in C++20 verfügbar und erfordern den Compilerschalter [/experimental:module](../build/reference/experimental-module.md) zusammen mit [/std:c++latest](../build/reference/std-specify-language-standard-version.md). **export** Weitere Informationen finden Sie unter [Übersicht über Module in C++](modules-cpp.md).

## <a name="module"></a>module

Platzieren **module** Sie eine Moduldeklaration am Anfang einer Modulimplementierungsdatei, um anzugeben, dass der Dateiinhalt zum benannten Modul gehört.

```cpp
module ModuleA;
```

## <a name="export"></a>Export

Verwenden Sie eine **Exportmoduldeklaration** für die primäre Schnittstellendatei des Moduls, die die Erweiterung **.ixx**haben muss:

```cpp
export module ModuleA;
```

Verwenden Sie in einer **export** Schnittstellendatei den Exportmodifizierer für Namen, die Teil der öffentlichen Schnittstelle sein sollen:

```cpp
// ModuleA.ixx

export module ModuleA;

namespace Bar
{
   export int f();
   export double d();
   double internal_f(); // not exported
}
```

Nicht exportierte Namen sind für Code, der das Modul importiert, nicht sichtbar:

```cpp
//MyProgram.cpp

import module ModuleA;

int main() {
  Bar::f(); // OK
  Bar::d(); // OK
  Bar::internal_f(); // Ill-formed: error C2065: 'internal_f': undeclared identifier
}
```

Das **Exportschlüsselwort** wird möglicherweise nicht in einer Modulimplementierungsdatei angezeigt. Wenn der **Export** auf einen Namespacenamen angewendet wird, werden alle Namen im Namespace exportiert.

## <a name="import"></a>Import

Verwenden **import** Sie eine Importdeklaration, um die Namen eines Moduls in Ihrem Programm sichtbar zu machen. Die Einfuhrdeklaration muss nach der Moduldeklaration und nach allen #include-Direktiven, jedoch vor allen Deklarationen in der Datei angezeigt werden.

```cpp
module ModuleA;

#include "custom-lib.h"
import std.core;
import std.regex;
import ModuleB;

// begin declarations here:
template <class T>
class Baz
{...};
```

## <a name="remarks"></a>Bemerkungen

Sowohl **Import** als auch **Modul** werden nur dann als Schlüsselwörter behandelt, wenn sie am Anfang einer logischen Zeile angezeigt werden:

```cpp

// OK:
module ;
module module-name
import :
import <
import "
import module-name
export module ;
export module module-name
export import :
export import <
export import "
export import module-name

// Error:
int i; module ;
```

**Microsoft Specific**

In Microsoft C++ sind die **Tokenimport** und **-module** immer Bezeichner und niemals Schlüsselwörter, wenn sie als Argumente für ein Makro verwendet werden.

### <a name="example"></a>Beispiel

```cpp
#define foo(…) __VA_ARGS__
foo(
import // Always an identifier, never a keyword
)
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Übersicht über Module in C++](modules-cpp.md)
