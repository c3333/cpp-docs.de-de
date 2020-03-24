---
title: Compilerwarnung C4956
ms.date: 11/04/2016
f1_keywords:
- C4956
helpviewer_keywords:
- C4956
ms.assetid: 9154f2d1-d49f-4e07-90d2-0e9bc028011a
ms.openlocfilehash: 474bdfa6eb670f39a2876b0c1490e7254cf216e7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164900"
---
# <a name="compiler-warning-c4956"></a>Compilerwarnung C4956

> '*Typ*': dieser Typ ist nicht überprüfbar.

## <a name="remarks"></a>Bemerkungen

Diese Warnung wird generiert, wenn [/clr:safe](../../build/reference/clr-common-language-runtime-compilation.md) angegeben ist und Ihr Code einen Typ enthält, der nicht überprüfbar ist. Die **/clr: Safe** -Compileroption ist in Visual Studio 2015 veraltet und wird in Visual Studio 2017 nicht unterstützt.

Weitere Informationen finden Sie unter [reiner und überprüfbarerC++Code (/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

Diese Warnung wird als Fehler ausgegeben. Sie kann mithilfe des [warning](../../preprocessor/warning.md) -Pragmas oder der Compileroption [/wd](../../build/reference/compiler-option-warning-level.md) deaktiviert werden.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4956 generiert:

```cpp
// C4956.cpp
// compile with: /clr:safe
int* p;   // C4956
```
