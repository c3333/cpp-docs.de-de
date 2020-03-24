---
title: Compilerwarnung (Stufe 1) C4382
ms.date: 11/04/2016
f1_keywords:
- C4382
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
ms.openlocfilehash: 7b8dbf77defab2a711ad931057c740193908474b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186971"
---
# <a name="compiler-warning-level-1-c4382"></a>Compilerwarnung (Stufe 1) C4382

> Auslösen von "*Typ*": ein Typ mit __clrcall Dekonstruktor oder Kopierkonstruktor kann nur im Modul "/CLR: pure" abgefangen werden.

## <a name="remarks"></a>Bemerkungen

Die **/clr: pure** -Compileroption ist in Visual Studio 2015 veraltet und wird in Visual Studio 2017 nicht unterstützt.

Bei der Kompilierung mit **/CLR** (nicht **/clr: pure**) erwartet die Ausnahmebehandlung, dass die Member-Funktionen in einem systemeigenen Typ [__cdecl](../../cpp/cdecl.md) und nicht [__clrcall](../../cpp/clrcall.md)werden. Systemeigene Typen mit Element Funktionen, die `__clrcall` Aufruf Konvention verwenden, können in einem mit **/CLR**kompilierten Modul nicht abgefangen werden.

Wenn die Ausnahme in einem Modul abgefangen wird, das mit **/clr: pure**kompiliert wurde, können Sie diese Warnung ignorieren.

Weitere Informationen finden Sie unter [/clr (Common Language Runtime-Kompilierung)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4382 generiert.

```cpp
// C4382.cpp
// compile with: /clr /W1 /c
struct S {
   __clrcall ~S() {}
};

struct T {
   ~T() {}
};

int main() {
   S s;
   throw s;   // C4382

   S * ps = &s;
   throw ps;   // OK

   T t;
   throw t;   // OK
}
```
