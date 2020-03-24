---
title: Compilerfehler C3641
ms.date: 11/04/2016
f1_keywords:
- C3641
helpviewer_keywords:
- C3641
ms.assetid: e8d3613e-5e8d-46fe-a516-eb7d1de7cd21
ms.openlocfilehash: 44356fb1a1818a02102d23e6b308457f2f39506b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200511"
---
# <a name="compiler-error-c3641"></a>Compilerfehler C3641

> "*Function*": Ungültige Aufruf Konvention "calling_convention" für die mit/CLR: pure oder/CLR: safe kompilierte Funktion

## <a name="remarks"></a>Bemerkungen

Die Compileroptionen **/clr: pure** und **/clr: Safe** sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 nicht unterstützt.

Nur [__clrcall](../../cpp/clrcall.md) Aufruf Konvention ist mit [/clr: pure](../../build/reference/clr-common-language-runtime-compilation.md)zulässig.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3641 generiert:

```cpp
// C3641.cpp
// compile with: /clr:pure /c
void __cdecl f() {}   // C3641
```
