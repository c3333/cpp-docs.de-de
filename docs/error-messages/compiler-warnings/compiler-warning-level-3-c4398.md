---
title: Compilerwarnung (Stufe 3) C4398
ms.date: 11/04/2016
f1_keywords:
- C4398
helpviewer_keywords:
- C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
ms.openlocfilehash: 041bf9f6bfce17b16f301604bb8706be30095c13
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198665"
---
# <a name="compiler-warning-level-3-c4398"></a>Compilerwarnung (Stufe 3) C4398

> "*Variable*": das prozessübergreifende globale Objekt funktioniert möglicherweise nicht ordnungsgemäß mit mehreren Anwendungs Domänen. Verwenden Sie __declspec (AppDomain).

## <a name="remarks"></a>Bemerkungen

Eine virtuelle Funktion mit [__clrcall](../../cpp/clrcall.md) Aufruf Konvention in einem systemeigenen Typ bewirkt, dass eine pro Anwendungs Domänen-Vtable erstellt wird. Eine solche Variable ist möglicherweise nicht richtig korrekt, wenn Sie in mehreren Anwendungs Domänen verwendet wird.

Sie können diese Warnung beheben, indem Sie die Variable `__declspec(appdomain)`explizit markieren. In Versionen von Visual Studio vor Visual Studio 2017 können Sie diese Warnung beheben, indem Sie eine Kompilierung mit **/clr: pure**durchführt, wodurch globale Variablen pro AppDomain standardmäßig erstellt werden. Die **/clr: pure** -Compileroption ist in Visual Studio 2015 veraltet und wird in Visual Studio 2017 nicht unterstützt.

Weitere Informationen finden Sie unter [AppDomain](../../cpp/appdomain.md) und [Anwendungs Domänen und C++Visual ](../../dotnet/application-domains-and-visual-cpp.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4398 generiert.

```cpp
// C4398.cpp
// compile with: /clr /W3 /c
struct S {
   virtual void f( System::String ^ );   // String^ parameter makes function __clrcall
};

S glob_s;   // C4398
__declspec(appdomain) S glob_s2;   // OK
```
