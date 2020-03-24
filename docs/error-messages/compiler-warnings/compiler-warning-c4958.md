---
title: Compilerwarnung C4958
ms.date: 11/04/2016
f1_keywords:
- C4958
helpviewer_keywords:
- C4958
ms.assetid: e79b9e9c-d572-4a3a-a3b6-60962b70864a
ms.openlocfilehash: 63371d91367902c1eab539cb370e55440fcbf917
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164884"
---
# <a name="compiler-warning-c4958"></a>Compilerwarnung C4958

> '*Operation*': die Zeigerarithmetik ist nicht überprüfbar.

## <a name="remarks"></a>Bemerkungen

Bei Verwendung der Zeigerarithmetik wird ein nicht überprüfbares Image erstellt.

Weitere Informationen finden Sie unter [reiner und überprüfbarerC++Code (/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

Die **/clr: Safe** -Compileroption ist in Visual Studio 2015 veraltet und wird in Visual Studio 2017 nicht unterstützt.

Diese Warnung wird als Fehler ausgegeben. Sie kann mithilfe des [warning](../../preprocessor/warning.md) -Pragmas oder der Compileroption [/wd](../../build/reference/compiler-option-warning-level.md) deaktiviert werden.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4958 generiert:

```cpp
// C4958.cpp
// compile with: /clr:safe
// #pragma warning( disable : 4958 )
using namespace System;

int main( ) {
   Int32 arr[] = new Int32[10];
   Int32* p = &arr[0];
   p++;   // C4958
}
```

Der Compiler implementiert Arrayoperationen mit Zeigerarithmetik. Daher sind systemeigene Arrays nicht überprüfbar. Verwenden Sie stattdessen ein CLR-Array. Weitere Informationen finden Sie unter [Array](../../extensions/arrays-cpp-component-extensions.md).

Im folgenden Beispiel wird C4958 generiert:

```cpp
// C4958b.cpp
// compile with: /clr:safe
// #pragma warning( disable : 4958 )

int main() {
   int array[5];
   array[4] = 0;   // C4958
}
```
