---
title: Compilerwarnung C4957
ms.date: 11/04/2016
f1_keywords:
- C4957
helpviewer_keywords:
- C4957
ms.assetid: a18c52d4-23e2-44f1-b4b5-f7fa5a7f3987
ms.openlocfilehash: 340c26c97d0b5b686eee487cd3fd8b6b05bdf373
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164904"
---
# <a name="compiler-warning-c4957"></a>Compilerwarnung C4957

> '*Cast*': die explizite Umwandlung von '*cast_from*' in '*cast_to*' ist nicht überprüfbar.

## <a name="remarks"></a>Bemerkungen

Eine Umwandlung ergibt ein nicht überprüfbares Image.

Einige Umwandlungen sind sicher (z. B. eine `static_cast` die benutzerdefinierte Umwandlungen auslöst, und eine `const_cast`). Eine [safe_cast](../../extensions/safe-cast-cpp-component-extensions.md) generiert auf jeden Fall überprüfbaren Code.

Weitere Informationen finden Sie unter [reiner und überprüfbarerC++Code (/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

Die **/clr: Safe** -Compileroption ist in Visual Studio 2015 veraltet und wird in Visual Studio 2017 nicht unterstützt.

Diese Warnung wird als Fehler ausgegeben. Sie kann mithilfe des [warning](../../preprocessor/warning.md) -Pragmas oder der Compileroption [/wd](../../build/reference/compiler-option-warning-level.md) deaktiviert werden.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4957 generiert:

```cpp
// C4957.cpp
// compile with: /clr:safe
// #pragma warning( disable : 4957 )
using namespace System;
int main() {
   Object ^ o = "Hello, World!";
   String ^ s = static_cast<String^>(o);   // C4957
   String ^ s2 = safe_cast<String^>(o);   // OK
}
```
