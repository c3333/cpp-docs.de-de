---
title: Compilerfehler C2660
ms.date: 11/04/2016
f1_keywords:
- C2660
helpviewer_keywords:
- C2660
ms.assetid: 2e01a1db-4f00-4df6-a04d-cb6f70a6922b
ms.openlocfilehash: 179cdc6379fd26f5acd436d5ca6cacc08df8dce3
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743242"
---
# <a name="compiler-error-c2660"></a>Compilerfehler C2660

'Funktion': Funktion akzeptiert keine 'Anzahl' Parameter

Die Funktion wurde mit einer unzulässigen Anzahl von Parametern aufgerufen.

C2660 kann auftreten, wenn anstelle einer MFC-Memberfunktion versehentlich eine Windows-API-Funktion desselben Namens aufgerufen wurde. So beheben Sie dieses Problem

- Passen Sie den Funktionsaufruf an das Format des Memberfunktionsaufrufs an.

- Verwenden Sie den Bereichsauflösungsoperator (`::`), um den Compiler aufzufordern, den Funktionsnamen im globalen Namespace zu suchen.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C2660 generiert.

```cpp
// C2660.cpp
void func( int, int ) {}

int main() {
   func( 1 );   // C2660 func( int ) not declared
   func( 1, 0 );   // OK
}
```

C2660 kann auch auftreten, wenn Sie die Dispose-Methode eines verwalteten Typs direkt aufrufen. Weitere Informationen finden Sie unter [debugtoren und Finalizer](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers). Im folgenden Beispiel wird C2660 generiert.

```cpp
// C2660_a.cpp
// compile with: /clr
using namespace System;
using namespace System::Threading;

void CheckStatus( Object^ stateInfo ) {}

int main() {
   ManualResetEvent^ event = gcnew ManualResetEvent( false );
   TimerCallback^ timerDelegate = gcnew TimerCallback( &CheckStatus );
   Timer^ stateTimer = gcnew Timer( timerDelegate, event, 1000, 250 );

   stateTimer->Dispose();   // C2660
   stateTimer->~Timer();   // OK
}
```

C2660 tritt auf, wenn eine abgeleitete Klasse eine Funktion ausblendet.

```cpp
// C2660b.cpp
// C2660 expected
#include <stdio.h>

class f {
public:
   void bar() {
      printf_s("in f::bar\n");
    }
};

class f2 : public f {
public:
   void bar(int i){printf("in f2::bar\n");}
   // Uncomment the following line to resolve.
   // using f::bar;   // - using declaration added
   // or
   // void bar(){__super::bar();}
};

int main() {
   f2 fObject;
   fObject.bar();
}
```

C2660 kann auftreten, wenn Sie eine indizierte Eigenschaft falsch aufrufen.

```cpp
// C2660c.cpp
// compile with: /clr
ref class X {
   double d;
public:
   X() : d(1.9) {}
   property double MyProp[] {
      double get(int i) {
         return d;
      }
   }   // end MyProp definition
};

int main() {
   X ^ MyX = gcnew X();
   System::Console::WriteLine(MyX->MyProp(1));   // C2660
   System::Console::WriteLine(MyX->MyProp[1]);   // OK
}
```

C2660 kann auftreten, wenn Sie eine indizierte Eigenschaft falsch aufrufen.

```cpp
// C2660d.cpp
// compile with: /clr
ref class A{
public:
   property int default[int,int] {
      int get(int a, int b) {
         return a + b;
      }
   }
};

int main() {
   A^ a = gcnew A;
   int x = a[3][5];   // C2660
   int x2 = a[3,5];   // OK
}
```

C2660 kann auftreten, wenn Sie einen neuen Operator in einer Vorlagenklasse definieren, dieser neue Operator jedoch ein Objekt erzeugt, dessen Typ vom übergeordneten Typ abweicht.

```cpp
// C2660e.cpp
// compile with: /c
#include <malloc.h>

template <class T> class CA {
private:
    static T** line;
   void* operator new (size_t, int i) {
      return 0;
   }
   void operator delete(void* pMem, int i) {
      free(pMem);
   }

public:
   CA () { new (1) T(); }   // C2660
   // try the following line instead
   // CA () { new (1) CA<int>(); }
};

typedef CA <int> int_CA;

void AAA() {
   int_CA  list;
}
```
