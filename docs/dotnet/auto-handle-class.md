---
title: auto_handle-Klasse
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::auto_handle::auto_handle
- msclr::auto_handle::get
- msclr::auto_handle::release
- msclr::auto_handle::reset
- msclr::auto_handle::swap
- msclr::auto_handle::operator->
- msclr::auto_handle::operator=
- msclr::auto_handle::operator auto_handle
- msclr::auto_handle::operator!
helpviewer_keywords:
- msclr::auto_handle class
ms.assetid: a65604d1-ecbb-44fd-ae2f-696ddeeed9d6
ms.openlocfilehash: 701669d1dbc6f3363f76c113dc98e38db04681a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372537"
---
# <a name="auto_handle-class"></a>auto_handle-Klasse

Automatische Ressourcenverwaltung, die zum Einbetten eines virtuellen Handles in einen verwalteten Typ verwendet werden kann.

## <a name="syntax"></a>Syntax

```cpp
template<typename _element_type>
ref class auto_handle;
```

### <a name="parameters"></a>Parameter

*_element_type*<br/>
Der verwaltete Typ, der eingebettet werden soll.

## <a name="members"></a><a name="members"></a>Mitglieder

### <a name="public-constructors"></a>Öffentliche Konstruktoren  

|Name|BESCHREIBUNG|  
|---------|-----------|  
|[auto_handle::auto_handle](#auto-handle)|Der `auto_handle` Konstruktor.|  
|[auto_handle::auto_handle](#tilde-auto-handle)|Der `auto_handle` Destruktor.|  

### <a name="public-methods"></a>Öffentliche Methoden  

|Name|BESCHREIBUNG|  
|---------|-----------|  
|[auto_handle::get](#get)|Ruft das enthaltene Objekt ab.|  
|[auto_handle::release](#release)|Gibt das `auto_handle` Objekt aus der Verwaltung frei.|
|[auto_handle::reset](#reset)|Zerstören Sie das aktuelle Objekt im Besitz, und nehmen Sie optional ein neues Objekt in Besitz.|
|[auto_handle::swap](#swap)|Tauscht Objekte `auto_handle`mit einem anderen .|  

### <a name="public-operators"></a>Öffentliche Betreiber

|Name|BESCHREIBUNG|  
|---------|-----------|
|[auto_handle::Operator-&gt;](#operator-arrow)|Der Memberzugriffsoperator.|
|[auto_handle::operator=](#operator-assign)|Zuweisungsoperator.|
|[auto_handle::operator auto_handle](#operator-auto-handle)|Typ-Cast-Operator `auto_handle` zwischen und kompatiblen Typen.|  
|[auto_handle::operator bool](#operator-bool)|Operator für `auto_handle` die Verwendung in einem bedingten Ausdruck.|
|[auto_handle::Operator!](#operator-logical-not)|Operator für `auto_handle` die Verwendung in einem bedingten Ausdruck.|  

## <a name="requirements"></a>Anforderungen

**Headerdatei** \<msclr-auto_handle.h>

**Namespace** msclr

## <a name="auto_handleauto_handle"></a><a name="auto-handle"></a>auto_handle::auto_handle

Der `auto_handle` Konstruktor.

```cpp
auto_handle();
auto_handle(
   _element_type ^ _ptr
);
auto_handle(
   auto_handle<_element_type> % _right
);
template<typename _other_type>
auto_handle(
   auto_handle<_other_type> % _right
);
```

### <a name="parameters"></a>Parameter

*_ptr*<br/>
Das zu besitzende Objekt.

*_right*<br/>
Ein vorhandener `auto_handle`.

### <a name="example"></a>Beispiel

```cpp
// msl_auto_handle_auto_handle.cpp
// compile with: /clr
#include "msclr\auto_handle.h"

using namespace System;
using namespace msclr;
ref class RefClassA {
protected:
   String^ m_s;
public:
   RefClassA(String^ s) : m_s(s) {
      Console::WriteLine( "in RefClassA constructor: " + m_s );
   }
   ~RefClassA() {
      Console::WriteLine( "in RefClassA destructor: " + m_s );
   }

   virtual void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

ref class RefClassB : RefClassA {
public:
   RefClassB( String^ s ) : RefClassA( s ) {}
   virtual void PrintHello() new {
      Console::WriteLine( "Hello from {0} B!", m_s );
   }
};

int main()
{
   {
      auto_handle<RefClassA> a(gcnew RefClassA( "first" ) );
      a->PrintHello();
   }

   {
      auto_handle<RefClassB> b(gcnew RefClassB( "second" ) );
      b->PrintHello();
      auto_handle<RefClassA> a(b); //construct from derived type
      a->PrintHello();
      auto_handle<RefClassA> a2(a); //construct from same type
      a2->PrintHello();
   }

   Console::WriteLine("done");
}
```

```Output
in RefClassA constructor: first
Hello from first A!
in RefClassA destructor: first
in RefClassA constructor: second
Hello from second B!
Hello from second A!
Hello from second A!
in RefClassA destructor: second
done
```

## <a name="auto_handleauto_handle"></a><a name="tilde-auto-handle"></a>auto_handle::auto_handle

Der `auto_handle` Destruktor.

```cpp
~auto_handle();
```

### <a name="remarks"></a>Bemerkungen

Der Destruktor zerstört auch das eigene Objekt.

### <a name="example"></a>Beispiel

```cpp
// msl_auto_handle_dtor.cpp
// compile with: /clr
#include "msclr\auto_handle.h"

using namespace System;
using namespace msclr;

ref class ClassA {
public:
   ClassA() { Console::WriteLine( "ClassA constructor" ); }
   ~ClassA() { Console::WriteLine( "ClassA destructor" ); }
};

int main()
{
   // create a new scope for a:
   {
      auto_handle<ClassA> a = gcnew ClassA;
   }
   // a goes out of scope here, invoking its destructor
   // which in turns destructs the ClassA object.

   Console::WriteLine( "done" );
}
```

```Output
ClassA constructor
ClassA destructor
done
```

## <a name="auto_handleget"></a><a name="get"></a>auto_handle::get

Ruft das enthaltene Objekt ab.

```cpp
_element_type ^ get();
```

### <a name="return-value"></a>Rückgabewert

Das enthaltene Objekt.

### <a name="example"></a>Beispiel

```cpp
// msl_auto_handle_get.cpp
// compile with: /clr
#include "msclr\auto_handle.h"

using namespace System;
using namespace msclr;

ref class ClassA {
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ){
      Console::WriteLine( "in ClassA constructor:" + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "in ClassA destructor:" + m_s );
   }

   void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

void PrintA( ClassA^ a ) {
   a->PrintHello();
}

int main() {
   auto_handle<ClassA> a = gcnew ClassA( "first" );
   a->PrintHello();

   ClassA^ a2 = a.get();
   a2->PrintHello();

   PrintA( a.get() );
}
```

```Output
in ClassA constructor:first
Hello from first A!
Hello from first A!
Hello from first A!
in ClassA destructor:first
```

## <a name="auto_handlerelease"></a><a name="release"></a>auto_handle::Release

Gibt das `auto_handle` Objekt aus der Verwaltung frei.

```cpp
_element_type ^ release();
```

### <a name="return-value"></a>Rückgabewert

Das freigegebene Objekt.

### <a name="example"></a>Beispiel

```cpp
// msl_auto_handle_release.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

ref class ClassA {
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {
      Console::WriteLine( "ClassA constructor: " + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "ClassA destructor: " + m_s );
   }

   void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

int main()
{
   ClassA^ a;

   // create a new scope:
   {
      auto_handle<ClassA> agc1 = gcnew ClassA( "first" );
      auto_handle<ClassA> agc2 = gcnew ClassA( "second" );
      a = agc1.release();
   }
   // agc1 and agc2 go out of scope here

   a->PrintHello();

   Console::WriteLine( "done" );
}
```

```Output
ClassA constructor: first
ClassA constructor: second
ClassA destructor: second
Hello from first A!
done
```

## <a name="auto_handlereset"></a><a name="reset"></a>auto_handle::reset

Zerstören Sie das aktuelle Objekt im Besitz, und nehmen Sie optional ein neues Objekt in Besitz.

```cpp
void reset(
   _element_type ^ _new_ptr
);
void reset();
```

### <a name="parameters"></a>Parameter

*_new_ptr*<br/>
(Optional) Das neue Objekt.

### <a name="example"></a>Beispiel

```cpp
// msl_auto_handle_reset.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

ref class ClassA {
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {
      Console::WriteLine( "ClassA constructor: " + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "ClassA destructor: " + m_s );
   }

   void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

int main()
{
   auto_handle<ClassA> agc1 = gcnew ClassA( "first" );
   agc1->PrintHello();

   ClassA^ ha = gcnew ClassA( "second" );
   agc1.reset( ha ); // release first object, reference second
   agc1->PrintHello();

   agc1.reset(); // release second object, set to nullptr

   Console::WriteLine( "done" );
}
```

```Output
ClassA constructor: first
Hello from first A!
ClassA constructor: second
ClassA destructor: first
Hello from second A!
ClassA destructor: second
done
```

## <a name="auto_handleswap"></a><a name="swap"></a>auto_handle::swap

Tauscht Objekte `auto_handle`mit einem anderen .

```cpp
void swap(
   auto_handle<_element_type> % _right
);
```

### <a name="parameters"></a>Parameter

*_right*<br/>
Die, `auto_handle` mit der Objekte ausgetauscht werden sollen.

### <a name="example"></a>Beispiel

```cpp
// msl_auto_handle_swap.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

int main() {
   auto_handle<String> s1 = "string one";
   auto_handle<String> s2 = "string two";

   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",
      s1->ToString(), s2->ToString() );
   s1.swap( s2 );
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",
      s1->ToString(), s2->ToString() );
}
```

```Output
s1 = 'string one', s2 = 'string two'
s1 = 'string two', s2 = 'string one'
```

## <a name="auto_handleoperator-gt"></a><a name="operator-arrow"></a>auto_handle::Operator-&gt;

Der Memberzugriffsoperator.

```cpp
_element_type ^ operator->();
```

### <a name="return-value"></a>Rückgabewert

Das Objekt, das `auto_handle`von umschlossen wird.

### <a name="example"></a>Beispiel

```cpp
// msl_auto_handle_op_arrow.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

ref class ClassA {
protected:
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {}

   virtual void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }

   int m_i;
};

int main() {
   auto_handle<ClassA> a( gcnew ClassA( "first" ) );
   a->PrintHello();

   a->m_i = 5;
   Console::WriteLine( "a->m_i = {0}", a->m_i );
}
```

```Output
Hello from first A!
a->m_i = 5
```

## <a name="auto_handleoperator"></a><a name="operator-assign"></a>auto_handle::operator=

Zuweisungsoperator.

```cpp
auto_handle<_element_type> % operator=(
   auto_handle<_element_type> % _right
);
template<typename _other_type>
auto_handle<_element_type> % operator=(
   auto_handle<_other_type> % _right
);
```

### <a name="parameters"></a>Parameter

*_right*<br/>
Die, `auto_handle` die der `auto_handle`aktuellen zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Die `auto_handle`aktuelle , `_right`jetzt besitzen .

### <a name="example"></a>Beispiel

```cpp
// msl_auto_handle_op_assign.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

ref class ClassA {
protected:
   String^ m_s;
public:
   ClassA(String^ s) : m_s(s) {
      Console::WriteLine( "in ClassA constructor: " + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "in ClassA destructor: " + m_s );
   }

   virtual void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

ref class ClassB : ClassA {
public:
   ClassB( String^ s ) : ClassA( s ) {}
   virtual void PrintHello() new {
      Console::WriteLine( "Hello from {0} B!", m_s );
   }
};

int main()
{
   auto_handle<ClassA> a;
   auto_handle<ClassA> a2(gcnew ClassA( "first" ) );
   a = a2; // assign from same type
   a->PrintHello();

   auto_handle<ClassB> b(gcnew ClassB( "second" ) );
   b->PrintHello();
   a = b; // assign from derived type
   a->PrintHello();

   Console::WriteLine("done");
}
```

```Output
in ClassA constructor: first
Hello from first A!
in ClassA constructor: second
Hello from second B!
in ClassA destructor: first
Hello from second A!
done
in ClassA destructor: second
```

## <a name="auto_handleoperator-auto_handle"></a><a name="operator-auto-handle"></a>auto_handle::Operator auto_handle

Typ-Cast-Operator `auto_handle` zwischen und kompatiblen Typen.

```cpp
template<typename _other_type>
operator auto_handle<_other_type>();
```

### <a name="return-value"></a>Rückgabewert

Die `auto_handle` aktuelle `auto_handle<_other_type>`Umwandlung auf .

### <a name="example"></a>Beispiel

```cpp
// msl_auto_handle_op_auto_handle.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

ref class ClassA {
protected:
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {}

   virtual void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

ref class ClassB : ClassA {
public:
   ClassB( String ^ s) : ClassA( s ) {}
   virtual void PrintHello() new {
      Console::WriteLine( "Hello from {0} B!", m_s );
   }
};

int main() {
   auto_handle<ClassB> b = gcnew ClassB("first");
   b->PrintHello();
   auto_handle<ClassA> a = (auto_handle<ClassA>)b;
   a->PrintHello();
}
```

```Output
Hello from first B!
Hello from first A!
```

## <a name="auto_handleoperator-bool"></a><a name="operator-bool"></a>auto_handle::operator bool

Operator für `auto_handle` die Verwendung in einem bedingten Ausdruck.

```cpp
operator bool();
```

### <a name="return-value"></a>Rückgabewert

`true`wenn das umschlossene Objekt gültig ist; `false` andernfalls.

### <a name="remarks"></a>Bemerkungen

Dieser Operator konvertiert `_detail_class::_safe_bool` tatsächlich in `bool` die sicherer als weil es nicht in einen integralen Typ konvertiert werden kann.

### <a name="example"></a>Beispiel

```cpp
// msl_auto_handle_operator_bool.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

int main() {
   auto_handle<String> s1;
   auto_handle<String> s2 = "hi";
   if ( s1 ) Console::WriteLine( "s1 is valid" );
   if ( !s1 ) Console::WriteLine( "s1 is invalid" );
   if ( s2 ) Console::WriteLine( "s2 is valid" );
   if ( !s2 ) Console::WriteLine( "s2 is invalid" );
   s2.reset();
   if ( s2 ) Console::WriteLine( "s2 is now valid" );
   if ( !s2 ) Console::WriteLine( "s2 is now invalid" );
}
```

```Output
s1 is invalid
s2 is valid
s2 is now invalid
```

## <a name="auto_handleoperator"></a><a name="operator-logical-not"></a>auto_handle::Operator!

Operator für `auto_handle` die Verwendung in einem bedingten Ausdruck.

```cpp
bool operator!();
```

### <a name="return-value"></a>Rückgabewert

`true`wenn das umschlossene Objekt ungültig ist; `false` andernfalls.

### <a name="example"></a>Beispiel

```cpp
// msl_auto_handle_operator_not.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

int main() {
   auto_handle<String> s1;
   auto_handle<String> s2 = "something";
   if ( s1) Console::WriteLine( "s1 is valid" );
   if ( !s1 ) Console::WriteLine( "s1 is invalid" );
   if ( s2 ) Console::WriteLine( "s2 is valid" );
   if ( !s2 ) Console::WriteLine( "s2 is invalid" );
   s2.reset();
   if ( s2 ) Console::WriteLine( "s2 is now valid" );
   if ( !s2 ) Console::WriteLine( "s2 is now invalid" );
}
```

```Output
s1 is invalid
s2 is valid
s2 is now invalid
```
