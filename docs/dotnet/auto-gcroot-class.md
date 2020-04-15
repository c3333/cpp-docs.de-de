---
title: auto_gcroot-Klasse
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::auto_gcroot::auto_gcroot
- msclr::auto_gcroot::attach
- msclr::auto_gcroot::get
- msclr::auto_gcroot::release
- msclr::auto_gcroot::reset
- msclr::auto_gcroot::swap
- msclr::auto_gcroot::operator=
- msclr::auto_gcroot::operator->
- msclr::auto_gcroot::operator!
- msclr::auto_gcroot::operator auto_gcroot
helpviewer_keywords:
- msclr::auto_gcroot
ms.assetid: b5790912-265d-463e-a486-47302e91042a
ms.openlocfilehash: 87e6703f759888b36ed89daed10df937701c6dbd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372553"
---
# <a name="auto_gcroot-class"></a>auto_gcroot-Klasse

Automatische Ressourcenverwaltung (z. B. [auto_ptr Klasse](../standard-library/auto-ptr-class.md)), die zum Einbetten eines virtuellen Handles in einen systemeigenen Typ verwendet werden kann.

## <a name="syntax"></a>Syntax

```cpp
template<typename _element_type>
class auto_gcroot;
```

### <a name="parameters"></a>Parameter

*_element_type*<br/>
Der verwaltete Typ, der eingebettet werden soll.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|---------|-----------|
|[auto_gcroot::auto_gcroot](#auto-gcroot)|Der `auto_gcroot` Konstruktor.|
|[auto_gcroot::~auto_gcroot](#tilde-auto-gcroot)|Der `auto_gcroot` Destruktor.
|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|---------|-----------|
|[auto_gcroot::attach](#attach)|An `auto_gcroot` ein Objekt anfügen.|
|[auto_gcroot::get](#get)|Ruft das enthaltene Objekt ab.|
|[auto_gcroot::release](#release)|Gibt das `auto_gcroot` Objekt aus der Verwaltung frei.|
|[auto_gcroot::reset](#reset)|Zerstören Sie das aktuelle Objekt im Besitz, und nehmen Sie optional ein neues Objekt in Besitz.|
|[auto_gcroot::swap](#swap)|Tauscht Objekte `auto_gcroot`mit einem anderen .|

### <a name="public-operators"></a>Öffentliche Betreiber

|Name|BESCHREIBUNG|
|---------|-----------|
|[auto_gcroot::Operator-&gt;](#operator-arrow)|Der Memberzugriffsoperator.|  
|[auto_gcroot::operator=](#operator-assign)|Zuweisungsoperator.|
|[auto_gcroot::Operator&nbsp;auto_gcroot](#operator-auto-gcroot)|Typ-Cast-Operator `auto_gcroot` zwischen und kompatiblen Typen.|
|[auto_gcroot::operator&nbsp;bool](#operator-bool)|Operator für `auto_gcroot` die Verwendung in einem bedingten Ausdruck.|  
|[auto_gcroot::Operator!](#operator-logical-not)|Operator für `auto_gcroot` die Verwendung in einem bedingten Ausdruck.|

## <a name="requirements"></a>Anforderungen

**Headerdatei** \<msclr-auto_gcroot.h>

**Namespace** msclr

## <a name="auto_gcrootauto_gcroot"></a><a name="auto-gcroot"></a>auto_gcroot::auto_gcroot

Der `auto_gcroot` Konstruktor.

```cpp
auto_gcroot(
   _element_type _ptr = nullptr
);
auto_gcroot(
   auto_gcroot<_element_type> & _right
);
template<typename _other_type>
auto_gcroot(
   auto_gcroot<_other_type> & _right
);
```

### <a name="parameters"></a>Parameter

*_ptr*<br/>
Das zu besitzende Objekt.

*_right*<br/>
Ein vorhandener `auto_gcroot`.

### <a name="remarks"></a>Bemerkungen

Beim Erstellen `auto_gcroot` einer `auto_gcroot`aus einer `auto_gcroot` vorhandenen gibt das vorhandene Objekt sein `auto_gcroot`Objekt frei, bevor der Besitz des Objekts auf die neue übertragen wird.

### <a name="example"></a>Beispiel

```cpp
// msl_auto_gcroot_auto_gcroot.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

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

class ClassA { //unmanaged class
private:
   auto_gcroot<RefClassA^> m_a;

public:
   ClassA() : m_a( gcnew RefClassA( "unmanaged" ) ) {}
   ~ClassA() {} //no need to delete m_a

   void DoSomething() {
      m_a->PrintHello();
   }
};

int main()
{
   {
      ClassA a;
      a.DoSomething();
   } // a.m_a is automatically destroyed as a goes out of scope

   {
      auto_gcroot<RefClassA^> a(gcnew RefClassA( "first" ) );
      a->PrintHello();
   }

   {
      auto_gcroot<RefClassB^> b(gcnew RefClassB( "second" ) );
      b->PrintHello();
      auto_gcroot<RefClassA^> a(b); //construct from derived type
      a->PrintHello();
      auto_gcroot<RefClassA^> a2(a); //construct from same type
      a2->PrintHello();
   }

   Console::WriteLine("done");
}
```

```Output
in RefClassA constructor: unmanaged
Hello from unmanaged A!
in RefClassA destructor: unmanaged
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

## <a name="auto_gcrootauto_gcroot"></a><a name="tilde-auto-gcroot"></a>auto_gcroot::auto_gcroot

Der `auto_gcroot` Destruktor.

```cpp
~auto_gcroot();
```

### <a name="remarks"></a>Bemerkungen

Der Destruktor zerstört auch das eigene Objekt.

### <a name="example"></a>Beispiel

```cpp
// msl_auto_gcroot_dtor.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

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
      auto_gcroot<ClassA^> a = gcnew ClassA;
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

## <a name="auto_gcrootattach"></a><a name="attach"></a>auto_gcroot::anbringen

An `auto_gcroot` ein Objekt anfügen.

```cpp
auto_gcroot<_element_type> & attach(
   _element_type _right
);
auto_gcroot<_element_type> & attach(
   auto_gcroot<_element_type> & _right
);
template<typename _other_type>
auto_gcroot<_element_type> & attach(
   auto_gcroot<_other_type> & _right
);
```

### <a name="parameters"></a>Parameter

*_right*<br/>
Das anzufügende Objekt `auto_gcroot` oder ein anzufügendes Objekt.

### <a name="return-value"></a>Rückgabewert

Der aktuelle `auto_gcroot`.

### <a name="remarks"></a>Bemerkungen

Wenn `_right` es `auto_gcroot`sich um ein handelt, gibt es den `auto_gcroot`Besitz seines Objekts frei, bevor das Objekt an den aktuellen angehängt wird.

### <a name="example"></a>Beispiel

```cpp
// msl_auto_gcroot_attach.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class ClassA {
protected:
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {
      Console::WriteLine( "in ClassA constructor:" + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "in ClassA destructor:" + m_s );
   }

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
   auto_gcroot<ClassA^> a( gcnew ClassA( "first" ) );
   a->PrintHello();
   a.attach( gcnew ClassA( "second" ) ); // attach same type
   a->PrintHello();
   ClassA^ ha = gcnew ClassA( "third" );
   a.attach( ha ); // attach raw handle
   a->PrintHello();
   auto_gcroot<ClassB^> b( gcnew ClassB("fourth") );
   b->PrintHello();
   a.attach( b ); // attach derived type
   a->PrintHello();
}
```

```Output
in ClassA constructor:first
Hello from first A!
in ClassA constructor:second
in ClassA destructor:first
Hello from second A!
in ClassA constructor:third
in ClassA destructor:second
Hello from third A!
in ClassA constructor:fourth
Hello from fourth B!
in ClassA destructor:third
Hello from fourth A!
in ClassA destructor:fourth
```

## <a name="auto_gcrootget"></a><a name="get"></a>auto_gcroot::get

Ruft das enthaltene Objekt ab.

```cpp
_element_type get() const;
```

### <a name="return-value"></a>Rückgabewert

Das enthaltene Objekt.

### <a name="example"></a>Beispiel

```cpp
// msl_auto_gcroot_get.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

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
   auto_gcroot<ClassA^> a = gcnew ClassA( "first" );
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

## <a name="auto_gcrootrelease"></a><a name="release"></a>auto_gcroot::Release

Gibt das `auto_gcroot` Objekt aus der Verwaltung frei.

```cpp
_element_type release();
```

### <a name="return-value"></a>Rückgabewert

Das freigegebene Objekt.

### <a name="example"></a>Beispiel

```cpp
// msl_auto_gcroot_release.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

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
      auto_gcroot<ClassA^> agc1 = gcnew ClassA( "first" );
      auto_gcroot<ClassA^> agc2 = gcnew ClassA( "second" );
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

## <a name="auto_gcrootreset"></a><a name="reset"></a>auto_gcroot::reset

Zerstören Sie das aktuelle Objekt im Besitz, und nehmen Sie optional ein neues Objekt in Besitz.

```cpp
void reset(
   _element_type _new_ptr = nullptr
);
```

### <a name="parameters"></a>Parameter

*_new_ptr*<br/>
(Optional) Das neue Objekt.

### <a name="example"></a>Beispiel

```cpp
// msl_auto_gcroot_reset.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

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
   auto_gcroot<ClassA^> agc1 = gcnew ClassA( "first" );
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

## <a name="auto_gcrootswap"></a><a name="swap"></a>auto_gcroot::swap

Tauscht Objekte `auto_gcroot`mit einem anderen .

```cpp
void swap(
   auto_gcroot<_element_type> & _right
);
```

### <a name="parameters"></a>Parameter

*_right*<br/>
Die, `auto_gcroot` mit der Objekte ausgetauscht werden sollen.

### <a name="example"></a>Beispiel

```cpp
// msl_auto_gcroot_swap.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

int main() {
   auto_gcroot<String^> s1 = "string one";
   auto_gcroot<String^> s2 = "string two";

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

## <a name="auto_gcrootoperator-gt"></a><a name="operator-arrow"></a>auto_gcroot::Operator-&gt;

Der Memberzugriffsoperator.

```cpp
_element_type operator->() const;
```

### <a name="return-value"></a>Rückgabewert

Das Objekt, das `auto_gcroot`von umschlossen wird.

### <a name="example"></a>Beispiel

```cpp
// msl_auto_gcroot_op_arrow.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

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
   auto_gcroot<ClassA^> a( gcnew ClassA( "first" ) );
   a->PrintHello();

   a->m_i = 5;
   Console::WriteLine( "a->m_i = {0}", a->m_i );
}
```

```Output
Hello from first A!
a->m_i = 5
```

## <a name="auto_gcrootoperator"></a><a name="operator-assign"></a>auto_gcroot::operator=

Zuweisungsoperator.

```cpp
auto_gcroot<_element_type> & operator=(
   _element_type _right
);
auto_gcroot<_element_type> & operator=(
   auto_gcroot<_element_type> & _right
);
template<typename _other_type>
auto_gcroot<_element_type> & operator=(
   auto_gcroot<_other_type> & _right
);
```

### <a name="parameters"></a>Parameter

*_right*<br/>
Das Objekt `auto_gcroot` oder das dem `auto_gcroot`aktuellen zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Die `auto_gcroot`aktuelle , `_right`jetzt besitzen .

### <a name="example"></a>Beispiel

```cpp
// msl_auto_gcroot_operator_equals.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

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
   auto_gcroot<ClassA^> a;
   auto_gcroot<ClassA^> a2(gcnew ClassA( "first" ) );
   a = a2; // assign from same type
   a->PrintHello();

   ClassA^ ha = gcnew ClassA( "second" );
   a = ha; // assign from raw handle

   auto_gcroot<ClassB^> b(gcnew ClassB( "third" ) );
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
in ClassA destructor: first
in ClassA constructor: third
Hello from third B!
in ClassA destructor: second
Hello from third A!
done
in ClassA destructor: third
```

## <a name="auto_gcrootoperator-auto_gcroot"></a><a name="operator-auto-gcroot"></a>auto_gcroot::Operator auto_gcroot

Typ-Cast-Operator `auto_gcroot` zwischen und kompatiblen Typen.

```cpp
template<typename _other_type>
operator auto_gcroot<_other_type>();
```

### <a name="return-value"></a>Rückgabewert

Die `auto_gcroot` aktuelle `auto_gcroot<_other_type>`Umwandlung auf .

### <a name="example"></a>Beispiel

```cpp
// msl_auto_gcroot_op_auto_gcroot.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

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
   auto_gcroot<ClassB^> b = gcnew ClassB("first");
   b->PrintHello();
   auto_gcroot<ClassA^> a = (auto_gcroot<ClassA^>)b;
   a->PrintHello();
}
```

```Output
Hello from first B!
Hello from first A!
```

## <a name="auto_gcrootoperator-bool"></a><a name="operator-bool"></a>auto_gcroot::operator bool

Operator für `auto_gcroot` die Verwendung in einem bedingten Ausdruck.

```cpp
operator bool() const;
```

### <a name="return-value"></a>Rückgabewert

`true`wenn das umschlossene Objekt gültig ist; `false` andernfalls.

### <a name="remarks"></a>Bemerkungen

Dieser Operator konvertiert `_detail_class::_safe_bool`tatsächlich in , `bool` was sicherer ist, als weil er nicht in einen integralen Typ konvertiert werden kann.

### <a name="example"></a>Beispiel

```cpp
// msl_auto_gcroot_operator_bool.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

int main() {
   auto_gcroot<String^> s;
   if ( s ) Console::WriteLine( "s is valid" );
   if ( !s ) Console::WriteLine( "s is invalid" );
   s = "something";
   if ( s ) Console::WriteLine( "now s is valid" );
   if ( !s ) Console::WriteLine( "now s is invalid" );
   s.reset();
   if ( s ) Console::WriteLine( "now s is valid" );
   if ( !s ) Console::WriteLine( "now s is invalid" );
}
```

```Output
s is invalid
now s is valid
now s is invalid
```

## <a name="auto_gcrootoperator"></a><a name="operator-logical-not"></a>auto_gcroot::Operator!

Operator für `auto_gcroot` die Verwendung in einem bedingten Ausdruck.

```cpp
bool operator!() const;
```

### <a name="return-value"></a>Rückgabewert

`true`wenn das umschlossene Objekt ungültig ist; `false` andernfalls.

### <a name="example"></a>Beispiel

```cpp
// msl_auto_gcroot_operator_not.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

int main() {
   auto_gcroot<String^> s;
   if ( s ) Console::WriteLine( "s is valid" );
   if ( !s ) Console::WriteLine( "s is invalid" );
   s = "something";
   if ( s ) Console::WriteLine( "now s is valid" );
   if ( !s ) Console::WriteLine( "now s is invalid" );
   s.reset();
   if ( s ) Console::WriteLine( "now s is valid" );
   if ( !s ) Console::WriteLine( "now s is invalid" );
}
```

```Output
s is invalid
now s is valid
now s is invalid
```
