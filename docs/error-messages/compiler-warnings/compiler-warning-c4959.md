---
title: Compilerwarnung C4959
ms.date: 11/04/2016
f1_keywords:
- C4959
helpviewer_keywords:
- C4959
ms.assetid: 3a128f3e-4d8a-4565-ba1a-5d32fdeb5982
ms.openlocfilehash: 13d2ed705bff7b42eb3c348692a5829bd54158b0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164871"
---
# <a name="compiler-warning-c4959"></a>Compilerwarnung C4959

> die nicht verwaltete Struktur '*Type*' kann nicht in/CLR: Safe definiert werden, da der Zugriff auf die Member nicht überprüfbaren Code ergibt.

## <a name="remarks"></a>Bemerkungen

Das Zugreifen auf einen Member eines nicht verwalteten Typs resultiert in einem nicht überprüfbaren Abbild (peverify.exe).

Weitere Informationen finden Sie unter [reiner und überprüfbarerC++Code (/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

Die **/clr: Safe** -Compileroption ist in Visual Studio 2015 veraltet und wird in Visual Studio 2017 nicht unterstützt.

Diese Warnung wird als Fehler ausgegeben. Sie kann mithilfe des [warning](../../preprocessor/warning.md) -Pragmas oder der Compileroption [/wd](../../build/reference/compiler-option-warning-level.md) deaktiviert werden.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4959 generiert:

```cpp
// C4959.cpp
// compile with: /clr:safe

// Uncomment the following line to resolve.
// #pragma warning( disable : 4959 )
struct X {
   int data;
};

int main() {
   X x;
   x.data = 10;   // C4959
}
```
