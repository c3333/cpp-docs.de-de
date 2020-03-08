---
title: '&lt;exception&gt;-Funktionen'
ms.date: 11/04/2016
f1_keywords:
- exception/std::current_exception
- exception/std::get_terminate
- exception/std::get_unexpected
- exception/std::make_exception_ptr
- exception/std::rethrow_exception
- exception/std::set_terminate
- exception/std::set_unexpected
- exception/std::terminate
- exception/std::uncaught_exception
- exception/std::unexpected
ms.assetid: c09ac569-5e35-4fe8-872d-ca5810274dd7
helpviewer_keywords:
- std::current_exception [C++]
- std::get_terminate [C++]
- std::get_unexpected [C++]
- std::make_exception_ptr [C++]
- std::rethrow_exception [C++]
- std::set_terminate [C++]
- std::set_unexpected [C++]
- std::terminate [C++]
- std::uncaught_exception [C++]
- std::unexpected [C++]
ms.openlocfilehash: 34a34c48be8bb0e319a7d0eebeccba805cafbc1f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854904"
---
# <a name="ltexceptiongt-functions"></a>&lt;exception&gt;-Funktionen

## <a name="current_exception"></a>current_exception

Erhält einen intelligenten Zeiger auf die aktuelle Ausnahme.

```cpp
exception_ptr current_exception();
```

### <a name="return-value"></a>Rückgabewert

Ein [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)-Objekt, das auf die aktuelle Ausnahme zeigt.

### <a name="remarks"></a>Bemerkungen

Rufen Sie die `current_exception`-Funktion in einem catch-Block auf. Wenn eine Ausnahme aktiv ist und die Ausnahme vom catch-Block nicht abgefangen werden kann, gibt die `current_exception`-Funktion ein `exception_ptr`-Objekt zurück, das auf die Ausnahme verweist. Andernfalls gibt die Funktion ein NULL-`exception_ptr`-Objekt zurück.

Die `current_exception`-Funktion erfasst die Ausnahme, die aktiv ist, unabhängig davon, ob die **catch** -Anweisung eine [Exception-Declaration-](../cpp/try-throw-and-catch-statements-cpp.md) Anweisung angibt.

Der Dekonstruktor für die aktuelle Ausnahme wird am Ende des **catch** -Blocks aufgerufen, wenn die Ausnahme nicht erneut ausgelöst wird. Auch wenn Sie die `current_exception`-Funktion im Destruktor aufrufen, gibt die Funktion ein `exception_ptr`-Objekt zurück, das auf die aktuelle Ausnahme verweist.

Aufeinander folgende Aufrufe der `current_exception`-Funktion geben `exception_ptr`-Objekte zurück, die sich auf unterschiedliche Kopien der aktuellen Ausnahme beziehen. Folglich sind die Objekte bei einem Vergleich ungleich, da sie auf unterschiedliche Kopien verweisen, auch wenn die Kopien den gleichen Binärwert aufweisen.

## <a name="make_exception_ptr"></a>make_exception_ptr

Erstellt ein [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)-Objekt, das eine Kopie einer Ausnahme enthält.

```cpp
template <class E>
    exception_ptr make_exception_ptr(E Except);
```

### <a name="parameters"></a>Parameter

*Außer*\
Die Klasse mit der zu kopierenden Ausnahme. Normalerweise geben Sie ein [exception class](../standard-library/exception-class.md)-Objekt als Argument für die `make_exception_ptr`-Funktion an, obwohl jedes Klassenobjekt als Argument zulässig ist.

### <a name="return-value"></a>Rückgabewert

Ein [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) Objekt, das auf eine Kopie der aktuellen Ausnahme für *außer*verweist.

### <a name="remarks"></a>Bemerkungen

Das Aufrufen der `make_exception_ptr`-Funktion ist gleichbedeutend mit dem Auslösen einer C++-Ausnahme, die in einem catch-Block abgefangen wird, und dem anschließenden Aufrufen der [current_exception](../standard-library/exception-functions.md#current_exception)-Funktion, um ein `exception_ptr`-Objekt zurückzugeben, das auf die Ausnahme verwiest. Die Microsoft-Implementierung der `make_exception_ptr`-Funktion ist effizienter als das Auslösen und anschließende Abfangen einer Ausnahme.

Eine Anwendung erfordert in der Regel nicht die `make_exception_ptr` -Funktion, und es wird von ihrer Verwendung abgeraten.

## <a name="rethrow_exception"></a>rethrow_exception

Löst eine Ausnahme aus, die als Parameter übergeben wird.

```cpp
void rethrow_exception(exception_ptr P);
```

### <a name="parameters"></a>Parameter

*P* -\
Die erneut auszulösende abgefangene Ausnahme. Wenn *P* ein NULL- [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)ist, löst die Funktion [Std:: Bad_exception](../standard-library/bad-exception-class.md)aus.

### <a name="remarks"></a>Bemerkungen

Nachdem Sie eine abgefangene Ausnahme in einem `exception_ptr`-Objekt gespeichert haben, kann der primäre Thread das Objekt verarbeiten. Rufen Sie in Ihrem primären Thread die `rethrow_exception`-Funktion zusammen mit dem `exception_ptr`-Objekt als Argument auf. Die `rethrow_exception`-Funktion extrahiert die Ausnahme vom `exception_ptr`-Objekt und löst die Ausnahme anschließend im Kontext des primären Threads aus.

## <a name="get_terminate"></a>get_terminate

Ruft die aktuelle `terminate_handler`-Funktion ab.

```cpp
terminate_handler get_terminate();
```

## <a name="set_terminate"></a>set_terminate

Richtet ein neues `terminate_handler`-Element ein, das bei Beendigung des Programms aufgerufen wird.

```cpp
terminate_handler set_terminate(terminate_handler fnew) throw();
```

### <a name="parameters"></a>Parameter

*neue*\
Die bei Beendigung aufzurufende Funktion.

### <a name="return-value"></a>Rückgabewert

Die Adresse der vorherigen Funktion, die von bei Beendigung aufgerufen wurde.

### <a name="remarks"></a>Bemerkungen

Die Funktion erstellt eine neue [terminate_handler](../standard-library/exception-typedefs.md#terminate_handler) als *Funktion * "* *". Daher darf " *f new* " kein NULL-Zeiger sein. Die Funktion gibt die Adresse des vorherigen terminate-Handlers zurück.

### <a name="example"></a>Beispiel

```cpp
// exception_set_terminate.cpp
// compile with: /EHsc
#include <exception>
#include <iostream>

using namespace std;

void termfunction()
{
    cout << "My terminate function called." << endl;
    abort();
}

int main()
{
    terminate_handler oldHandler = set_terminate(termfunction);

    // Throwing an unhandled exception would also terminate the program
    // or we could explicitly call terminate();

    //throw bad_alloc();
    terminate();
}
```

## <a name="get_unexpected"></a>get_unexpected

Ruft die aktuelle `unexpected_handler`-Funktion ab.

```cpp
unexpected_handler get_unexpected();
```

## <a name="rethrow_if_nested"></a>rethrow_if_nested

```cpp
template <class E> 
    void rethrow_if_nested(const E& e);
```

### <a name="remarks"></a>Bemerkungen

Wenn es sich nicht um einen polymorphen Klassentyp handelt oder wenn `nested_exception` nicht zugänglich oder mehrdeutig ist, gibt es keine Auswirkungen. Andernfalls führt eine dynamische Umwandlung aus.

## <a name="set_unexpected"></a>set_unexpected

Richtet ein neues `unexpected_handler` ein, das bei einer unerwarteten Ausnahme auftritt.

```cpp
unexpected_handler set_unexpected(unexpected_handler fnew) throw();
```

### <a name="parameters"></a>Parameter

*neue*\
Die Funktion, die bei einer unerwarteten Ausnahme aufgerufen wird.

### <a name="return-value"></a>Rückgabewert

Die Adresse des vorherigen `unexpected_handler`-Elements.

### <a name="remarks"></a>Bemerkungen

" *f new* " darf kein NULL-Zeiger sein.

Für den C++-Standard ist es erforderlich, dass `unexpected` aufgerufen wird, wenn eine Funktion eine Ausnahme auslöst, die nicht auf der Auslöseliste aufgeführt wird. Die augenblickliche Implementierung unterstützt das nicht. Im folgenden Beispiel ruft `unexpected` direkt auf, woraufhin `unexpected_handler` aufgerufen wird.

### <a name="example"></a>Beispiel

```cpp
// exception_set_unexpected.cpp
// compile with: /EHsc
#include <exception>
#include <iostream>

using namespace std;

void uefunction()
{
    cout << "My unhandled exception function called." << endl;
    terminate(); // this is what unexpected() calls by default
}

int main()
{
    unexpected_handler oldHandler = set_unexpected(uefunction);

    unexpected(); // library function to force calling the
                  // current unexpected handler
}
```

## <a name="terminate"></a>aufzu

Ruft einen terminate-Handler auf.

```cpp
void terminate();
```

### <a name="remarks"></a>Bemerkungen

Die Funktion Ruft einen Beendigungs Handler auf, eine Funktion vom Typ " **void**". Wenn `terminate` direkt vom Programm aufgerufen wird, ist der Beendigungs Handler der zuletzt durch einen Aufruf von [Set_terminate](../standard-library/exception-functions.md#set_terminate)festgelegte. Wenn `terminate` aus verschiedenen anderen Gründen während der Auswertung eines Throw-Ausdrucks aufgerufen wird, ist der Beendigungs Handler sofort nach der Auswertung des Throw-Ausdrucks wirksam.

Ein terminate-Handler kehrt möglicherweise nicht zum Aufrufer zurück. Beim Programmstart ist der Beendigungs Handler eine Funktion, die `abort`aufruft.

### <a name="example"></a>Beispiel

Ein Beispiel zur Verwendung von [ finden Sie unter ](../standard-library/exception-functions.md#set_unexpected)set_unexpected`terminate`.

## <a name="throw_with_nested"></a>throw_with_nested

```cpp
template <class T> [[noreturn]]
    void throw_with_nested(T&& t);
```

### <a name="remarks"></a>Bemerkungen

Löst eine Ausnahme mit Ausnahme Fehlern aus.

## <a name="uncaught_exception"></a>uncaught_exception

Gibt nur dann **TRUE** zurück, wenn augenblicklich eine Ausnahme verarbeitet wird.

```cpp
bool uncaught_exception();
```

### <a name="return-value"></a>Rückgabewert

Gibt **true** zurück, nachdem die Auswertung eines Throw-Ausdrucks abgeschlossen wurde und bevor die Initialisierung der Ausnahme Deklaration im übereinstimmenden Handler abgeschlossen oder [unerwartete](../standard-library/exception-functions.md#unexpected) als Ergebnis des Throw-Ausdrucks aufgerufen wurde. Insbesondere gibt `uncaught_exception` " **true** " zurück, wenn er von einem Dekonstruktor aufgerufen wird, der während einer Ausnahme Entladung aufgerufen wird. Auf Geräten wird `uncaught_exception` nur auf Windows CE 5.00 und höheren Versionen, darunter Windows Mobile 2005-Plattformen unterstützt.

### <a name="example"></a>Beispiel

```cpp
// exception_uncaught_exception.cpp
// compile with: /EHsc
#include <exception>
#include <iostream>
#include <string>

class Test
{
public:
   Test( std::string msg ) : m_msg( msg )
   {
      std::cout << "In Test::Test(\"" << m_msg << "\")" << std::endl;
   }
   ~Test( )
   {
      std::cout << "In Test::~Test(\"" << m_msg << "\")" << std::endl
         << "        std::uncaught_exception( ) = "
         << std::uncaught_exception( )
         << std::endl;
   }
private:
    std::string m_msg;
};

// uncaught_exception will be true in the destructor
// for the object created inside the try block because
// the destructor is being called as part of the unwind.

int main( void )
   {
      Test t1( "outside try block" );
      try
      {
         Test t2( "inside try block" );
         throw 1;
      }
      catch (...) {
   }
}
```

```Output
In Test::Test("outside try block")
In Test::Test("inside try block")
In Test::~Test("inside try block")
        std::uncaught_exception( ) = 1
In Test::~Test("outside try block")
        std::uncaught_exception( ) = 0
```

## <a name="unexpected"></a>te

Ruft den unerwarteten Handler auf.

```cpp
void unexpected();
```

### <a name="remarks"></a>Bemerkungen

Für den C++-Standard ist es erforderlich, dass `unexpected` aufgerufen wird, wenn eine Funktion eine Ausnahme auslöst, die nicht auf der Auslöseliste aufgeführt wird. Die augenblickliche Implementierung unterstützt das nicht. Das Beispiel ruft `unexpected` direkt auf, wodurch der unerwartete Handler aufgerufen wird.

Die-Funktion Ruft einen unerwarteten Handler auf, eine Funktion vom Typ " **void**". Wenn `unexpected` direkt vom Programm aufgerufen wird, ist der unerwartete Handler durch einen Aufruf von [set_unexpected](../standard-library/exception-functions.md#set_unexpected) der zuletzt festgelegte Handler.

Ein unerwarteter Handler kehrt möglicherweise nicht zum Aufrufer zurück. Die Ausführung kann hierdurch beendet werden:

- Auslösen eines Objekts eines Typs, das in der Ausnahmespezifikation gelistet ist oder eines Objekts jeglichen Typs, wenn der unerwartete Handler direkt durch das Programm aufgerufen wird.

- Auslösen eines Objekt des Typs [bad_exception](../standard-library/bad-exception-class.md).

- Aufrufen von [Beenden](../standard-library/exception-functions.md#terminate), `abort` oder **Beenden**(`int`).

Bei Programmstart ist der unerwartete Handler eine Funktion, die [erminate](../standard-library/exception-functions.md#terminate) aufruft.

### <a name="example"></a>Beispiel

Ein Beispiel zur Verwendung von [ finden Sie unter ](../standard-library/exception-functions.md#set_unexpected)set_unexpected`unexpected`.
