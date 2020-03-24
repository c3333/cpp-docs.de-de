---
title: Compilerfehler C3862
ms.date: 11/04/2016
f1_keywords:
- C3862
helpviewer_keywords:
- C3862
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
ms.openlocfilehash: 0b9c1e1213949d7d700094caa6687232df881ce6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165482"
---
# <a name="compiler-error-c3862"></a>Compilerfehler C3862

> "*Function*": eine nicht verwaltete Funktion kann nicht mit/CLR: pure oder/CLR: safe kompiliert werden.

## <a name="remarks"></a>Bemerkungen

Die Compileroptionen **/clr: pure** und **/clr: Safe** sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 nicht unterstützt.

Eine Kompilierung mit **/clr: pure** oder **/clr: Safe** erzeugt ein nur-MSIL-Image, ein Bild ohne nativen (nicht verwalteten) Code.  Daher können Sie das `unmanaged`-Pragma nicht in einer **/clr: pure** -oder **/clr: Safe** -Kompilierung verwenden.

Weitere Informationen finden Sie unter [/CLR (Common Language Runtime-Kompilierung)](../../build/reference/clr-common-language-runtime-compilation.md) und [verwaltet, nicht verwaltet](../../preprocessor/managed-unmanaged.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3862 generiert:

```cpp
// C3862.cpp
// compile with: /clr:pure /c
#pragma unmanaged
void f() {}   // C3862
```
