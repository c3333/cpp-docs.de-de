---
title: appdomain
ms.date: 11/04/2016
f1_keywords:
- appdomain_cpp
helpviewer_keywords:
- appdomain __declspec keyword
- __declspec keyword [C++], appdomain
ms.assetid: 29d843cb-cb6b-4d1b-a48d-d928a877234d
ms.openlocfilehash: 7ac74e8774204b316712a15975f7af3fb8835a9e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181485"
---
# <a name="appdomain"></a>appdomain

Gibt an, dass jede Anwendungsdomäne der verwalteten Anwendung eine eigene Kopie einer bestimmten globalen Variable oder statischen Membervariable haben soll. Weitere Informationen finden Sie unter [Anwendungs Domänen und Visualisierung C++ ](../dotnet/application-domains-and-visual-cpp.md) .

Jede Anwendungsdomäne verfügt über eine eigene Kopie einer Anwendungsdomänenvariable. Ein Konstruktor einer Anwendungsdomänenvariable wird ausgeführt, wenn eine Assembly in eine Anwendungsdomäne geladen wird, und der Destruktor wird ausgeführt, wenn die Anwendungsdomäne entladen wird.

Wenn alle Anwendungsdomänen innerhalb eines Prozesses in der Common Language Runtime eine globale Variable gemeinsam nutzen sollen, verwenden Sie den `__declspec(process)`-Modifizierer. `__declspec(process)` ist standardmäßig unter [/CLR](../build/reference/clr-common-language-runtime-compilation.md)aktiviert. Die Compileroptionen **/clr: pure** und **/clr: Safe** sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 nicht unterstützt.

`__declspec(appdomain)` ist nur gültig, wenn eine der **/CLR** -Compileroptionen verwendet wird. Nur eine globale Variable, eine statische Membervariable oder eine statische lokale Variable kann mit `__declspec(appdomain)` markiert werden. Es ist nicht zulässig, `__declspec(appdomain)` auf statische Member von verwalteten Typen anzuwenden, da diese immer dieses Verhalten aufweisen.

Die Verwendung von `__declspec(appdomain)` ähnelt der Verwendung von [Thread lokalem Speicher (TLS)](../parallel/thread-local-storage-tls.md). Threads verfügen über einen eigenen Speicher, genau wie Anwendungsdomänen. Die Verwendung `__declspec(appdomain)` stellt sicher, dass die globale Variable einen eigenen Speicher in jeder Anwendungsdomäne aufweist, die für die Anwendung erstellt wird.

Die Kombination der Verwendung von pro Prozess-und pro-AppDomain-Variablen ist begrenzt. Weitere Informationen finden Sie unter [Process](../cpp/process.md) .

Beim Programmstart werden beispielsweise alle pro-Prozess-Variablen initialisiert, gefolgt von alle pro-AppDomain-Variablen. Wenn eine pro-Prozess-Variable initialisiert wird, kann sie also nicht vom Wert einer pro-AppDomain-Variablen abhängen. Es ist nicht üblich, die Verwendung (Zuweisung) der pro-Prozess- und pro-AppDomain-Variablen zu kombinieren.

Informationen dazu, wie Sie eine Funktion in einer bestimmten Anwendungsdomäne aufzurufen, finden Sie unter [Call_in_appdomain Funktion](../dotnet/call-in-appdomain-function.md).

## <a name="example"></a>Beispiel

```cpp
// declspec_appdomain.cpp
// compile with: /clr
#include <stdio.h>
using namespace System;

class CGlobal {
public:
   CGlobal(bool bProcess) {
      Counter = 10;
      m_bProcess = bProcess;
      Console::WriteLine("__declspec({0}) CGlobal::CGlobal constructor", m_bProcess ? (String^)"process" : (String^)"appdomain");
   }

   ~CGlobal() {
      Console::WriteLine("__declspec({0}) CGlobal::~CGlobal destructor", m_bProcess ? (String^)"process" : (String^)"appdomain");
   }

   int Counter;

private:
   bool m_bProcess;
};

__declspec(process) CGlobal process_global = CGlobal(true);
__declspec(appdomain) CGlobal appdomain_global = CGlobal(false);

value class Functions {
public:
   static void change() {
      ++appdomain_global.Counter;
   }

   static void display() {
      Console::WriteLine("process_global value in appdomain '{0}': {1}",
         AppDomain::CurrentDomain->FriendlyName,
         process_global.Counter);

      Console::WriteLine("appdomain_global value in appdomain '{0}': {1}",
         AppDomain::CurrentDomain->FriendlyName,
         appdomain_global.Counter);
   }
};

int main() {
   AppDomain^ defaultDomain = AppDomain::CurrentDomain;
   AppDomain^ domain = AppDomain::CreateDomain("Domain 1");
   AppDomain^ domain2 = AppDomain::CreateDomain("Domain 2");
   CrossAppDomainDelegate^ changeDelegate = gcnew CrossAppDomainDelegate(&Functions::change);
   CrossAppDomainDelegate^ displayDelegate = gcnew CrossAppDomainDelegate(&Functions::display);

   // Print the initial values of appdomain_global in all appdomains.
   Console::WriteLine("Initial value");
   defaultDomain->DoCallBack(displayDelegate);
   domain->DoCallBack(displayDelegate);
   domain2->DoCallBack(displayDelegate);

   // Changing the value of appdomain_global in the domain and domain2
   // appdomain_global value in "default" appdomain remain unchanged
   process_global.Counter = 20;
   domain->DoCallBack(changeDelegate);
   domain2->DoCallBack(changeDelegate);
   domain2->DoCallBack(changeDelegate);

   // Print values again
   Console::WriteLine("Changed value");
   defaultDomain->DoCallBack(displayDelegate);
   domain->DoCallBack(displayDelegate);
   domain2->DoCallBack(displayDelegate);

   AppDomain::Unload(domain);
   AppDomain::Unload(domain2);
}
```

```Output
__declspec(process) CGlobal::CGlobal constructor
__declspec(appdomain) CGlobal::CGlobal constructor
Initial value
process_global value in appdomain 'declspec_appdomain.exe': 10
appdomain_global value in appdomain 'declspec_appdomain.exe': 10
__declspec(appdomain) CGlobal::CGlobal constructor
process_global value in appdomain 'Domain 1': 10
appdomain_global value in appdomain 'Domain 1': 10
__declspec(appdomain) CGlobal::CGlobal constructor
process_global value in appdomain 'Domain 2': 10
appdomain_global value in appdomain 'Domain 2': 10
Changed value
process_global value in appdomain 'declspec_appdomain.exe': 20
appdomain_global value in appdomain 'declspec_appdomain.exe': 10
process_global value in appdomain 'Domain 1': 20
appdomain_global value in appdomain 'Domain 1': 11
process_global value in appdomain 'Domain 2': 20
appdomain_global value in appdomain 'Domain 2': 12
__declspec(appdomain) CGlobal::~CGlobal destructor
__declspec(appdomain) CGlobal::~CGlobal destructor
__declspec(appdomain) CGlobal::~CGlobal destructor
__declspec(process) CGlobal::~CGlobal destructor
```

## <a name="see-also"></a>Weitere Informationen

[__declspec](../cpp/declspec.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
