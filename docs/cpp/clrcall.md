---
title: __clrcall
ms.date: 11/04/2016
f1_keywords:
- __clrcall_cpp
helpviewer_keywords:
- __clrcall keyword [C++]
ms.assetid: 92096695-683a-40ed-bf65-0c8443572152
ms.openlocfilehash: 85e9025c26cc821cdbd8e5218e184f05e2b96b24
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685830"
---
# <a name="__clrcall"></a>__clrcall

Gibt an, dass eine Funktion nur aus verwaltetem Code aufgerufen werden kann.  Verwenden Sie **__clrcall** für alle virtuellen Funktionen, die nur aus verwaltetem Code aufgerufen werden. Allerdings kann diese Aufrufkonvention nicht für Funktionen verwendet werden, die vom nativen Code aufgerufen werden. Der **__clrcall** Modifizierer ist Microsoft-spezifisch.

Verwenden Sie **__clrcall** , um die Leistung zu verbessern, wenn Sie von einer verwalteten Funktion zu einer virtuellen verwalteten Funktion oder von einer verwalteten Funktion an eine verwaltete Funktion über Zeiger aufrufen.

Einstiegspunkte sind separate, vom Compiler generierte Funktionen. Wenn eine Funktion sowohl über die systemeigenen als auch über verwaltete Einstiegspunkte verfügt, ist eine von ihnen die tatsächliche Funktion mit der Funktionsimplementierung. Die andere Funktion ist eine separate Funktion (ein Thunk), welche die tatsächliche Funktion aufruft und die Common Language Runtime PInvoke ausführen lässt. Wenn Sie eine Funktion als **__clrcall**markieren, geben Sie an, dass die Funktions Implementierung MSIL sein muss und dass die native Einstiegspunkt Funktion nicht generiert wird.

Wenn **__clrcall** nicht angegeben ist, verwendet der Compiler den systemeigenen Einstiegspunkt, wenn die Adresse einer nativen Funktion übernommen wird. **__clrcall** gibt an, dass die Funktion verwaltet wird, und es ist nicht erforderlich, den Übergang von verwaltet zu System eigen zu durchlaufen. In diesem Fall verwendet der Compiler den verwalteten Einstiegspunkt.

Wenn `/clr` (nicht `/clr:pure` oder `/clr:safe` ) verwendet wird und **__clrcall** nicht verwendet wird, gibt die Adresse einer Funktion immer die Adresse der systemeigenen Einstiegspunkt Funktion zurück. Wenn **__clrcall** verwendet wird, wird die native Einstiegspunkt Funktion nicht erstellt, sodass Sie die Adresse der verwalteten Funktion und keine Einstiegspunkt-Thunk-Funktion erhalten. Weitere Informationen finden Sie unter [Double Thunking](../dotnet/double-thunking-cpp.md). Die Compileroptionen **/clr: pure** und **/clr: Safe** sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 nicht unterstützt.

[/CLR (Common Language Runtime-Kompilierung)](../build/reference/clr-common-language-runtime-compilation.md) impliziert, dass alle Funktionen und Funktionszeiger **__clrcall** werden und der Compiler nicht zulässt, dass eine Funktion in der Kompilierung etwas anderes als **__clrcall**markiert wird. Wenn **/clr: pure** verwendet wird, können **__clrcall** nur für Funktionszeiger und externe Deklarationen angegeben werden.

Sie können **__clrcall** Funktionen aus vorhandenem C++-Code, der mithilfe von **/CLR** kompiliert wurde, direkt aufzurufen, sofern diese Funktion über eine MSIL-Implementierung verfügt. **__clrcall** Funktionen können nicht direkt aus Funktionen aufgerufen werden, die über Inline-ASM verfügen, und auch CPU-spezifische intrinisics aufrufen, auch wenn diese Funktionen mit kompiliert werden `/clr` .

**__clrcall** Funktionszeiger sind nur für die Verwendung in der Anwendungsdomäne bestimmt, in der Sie erstellt wurden.  Anstatt **__clrcall** Funktionszeiger über Anwendungs Domänen hinweg zu übergeben, verwenden Sie <xref:System.CrossAppDomainDelegate> . Weitere Informationen finden Sie unter [Anwendungs Domänen und Visual C++](../dotnet/application-domains-and-visual-cpp.md).

## <a name="examples"></a>Beispiele

Beachten Sie, dass beim Deklarieren einer Funktion mit **__clrcall**Code bei Bedarf generiert wird. Wenn beispielsweise die-Funktion aufgerufen wird.

```cpp
// clrcall2.cpp
// compile with: /clr
using namespace System;
int __clrcall Func1() {
   Console::WriteLine("in Func1");
   return 0;
}

// Func1 hasn't been used at this point (code has not been generated),
// so runtime returns the adddress of a stub to the function
int (__clrcall *pf)() = &Func1;

// code calls the function, code generated at difference address
int i = pf();   // comment this line and comparison will pass

int main() {
   if (&Func1 == pf)
      Console::WriteLine("&Func1 == pf, comparison succeeds");
   else
      Console::WriteLine("&Func1 != pf, comparison fails");

   // even though comparison fails, stub and function call are correct
   pf();
   Func1();
}
```

```Output
in Func1
&Func1 != pf, comparison fails
in Func1
in Func1
```

Das folgende Beispiel zeigt, wie ein Funktionszeiger so definiert werden kann, dass deklariert wird, dass der Funktionszeiger nur von verwaltetem Code aufgerufen wird. Dies ermöglicht es dem Compiler, die verwaltete Funktion direkt aufzurufen und den systemeigenen Einstiegspunkt (doppeltes Thunk-Problem) zu vermeiden.

```cpp
// clrcall3.cpp
// compile with: /clr
void Test() {
   System::Console::WriteLine("in Test");
}

int main() {
   void (*pTest)() = &Test;
   (*pTest)();

   void (__clrcall *pTest2)() = &Test;
   (*pTest2)();
}
```

## <a name="see-also"></a>Weitere Informationen

[Argument Übergabe und Benennungs Konventionen](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
