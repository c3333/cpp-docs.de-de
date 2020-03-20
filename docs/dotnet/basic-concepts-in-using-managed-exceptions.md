---
title: Grundlegende Konzepte zur Verwendung verwalteter Ausnahmen
ms.date: 11/04/2016
helpviewer_keywords:
- try-catch exception handling, managed applications
- __finally keyword, managed exceptions
- exceptions, managed
- try-catch exception handling
- catch blocks
- throwing exceptions, managed exceptions
- Visual C++, handling managed exceptions
ms.assetid: 40ce8931-1ecc-491a-815f-733b23fcba35
ms.openlocfilehash: cf241d4e599ad58c2e39680d8ed4e4e250b42b18
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545378"
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>Grundlegende Konzepte zur Verwendung verwalteter Ausnahmen

In diesem Thema wird die Ausnahmebehandlung in verwalteten Anwendungen erläutert. Das heißt, eine Anwendung, die mit der **/CLR** -Compileroption kompiliert wird.

## <a name="in-this-topic"></a>In diesem Thema

- [Auslösen von Ausnahmen unter/CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor1)

- [Try/catch-Blöcke für CLR-Erweiterungen](#vcconbasicconceptsinusingmanagedexceptionsanchor2)

## <a name="remarks"></a>Hinweise

Wenn Sie mit der **/CLR** -Option kompilieren, können Sie CLR-Ausnahmen behandeln, und Standard <xref:System.Exception> Klasse stellt viele nützliche Methoden zum Verarbeiten von CLR-Ausnahmen bereit und wird als Basisklasse für benutzerdefinierte Ausnahme Klassen empfohlen.

Das Abfangen von Ausnahme Typen, die von einer Schnittstelle abgeleitet werden, wird unter **/CLR** Außerdem ermöglicht der Common Language Runtime nicht, Stapelüberlauf Ausnahmen abzufangen. eine Stapelüberlauf Ausnahme beendet den Prozess.

Weitere Informationen zu Unterschieden bei der Ausnahmebehandlung in verwalteten und nicht verwalteten Anwendungen finden Sie [unter Unterschiede im Ausnahme Behandlungs Verhalten unter C++Managed Extensions for ](../dotnet/differences-in-exception-handling-behavior-under-clr.md).

##  <a name="throwing-exceptions-under-clr"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a>Auslösen von Ausnahmen unter/CLR

Der C++ Throw-Ausdruck wird so erweitert, dass ein Handle für einen CLR-Typ ausgelöst wird. Im folgenden Beispiel wird ein benutzerdefinierter Ausnahmetyp erstellt und dann eine Instanz dieses Typs ausgelöst:

```cpp
// clr_exception_handling.cpp
// compile with: /clr /c
ref struct MyStruct: public System::Exception {
public:
   int i;
};

void GlobalFunction() {
   MyStruct^ pMyStruct = gcnew MyStruct;
   throw pMyStruct;
}
```

Vor dem auslösen muss ein Werttyp geschachtelt werden:

```cpp
// clr_exception_handling_2.cpp
// compile with: /clr /c
value struct MyValueStruct {
   int i;
};

void GlobalFunction() {
   MyValueStruct v = {11};
   throw (MyValueStruct ^)v;
}
```

##  <a name="trycatch-blocks-for-clr-extensions"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a>Try/catch-Blöcke für CLR-Erweiterungen

Dieselbe **try**/**catch** -Blockstruktur kann zum Abfangen von CLR-und nativen Ausnahmen verwendet werden:

```cpp
// clr_exception_handling_3.cpp
// compile with: /clr
using namespace System;
ref struct MyStruct : public Exception {
public:
   int i;
};

struct CMyClass {
public:
   double d;
};

void GlobalFunction() {
   MyStruct^ pMyStruct = gcnew MyStruct;
   pMyStruct->i = 11;
   throw pMyStruct;
}

void GlobalFunction2() {
   CMyClass c = {2.0};
   throw c;
}

int main() {
   for ( int i = 1; i >= 0; --i ) {
      try {
         if ( i == 1 )
            GlobalFunction2();
         if ( i == 0 )
            GlobalFunction();
      }
      catch ( CMyClass& catchC ) {
         Console::WriteLine( "In 'catch(CMyClass& catchC)'" );
         Console::WriteLine( catchC.d );
      }
      catch ( MyStruct^ catchException ) {
         Console::WriteLine( "In 'catch(MyStruct^ catchException)'" );
         Console::WriteLine( catchException->i );
      }
   }
}
```

### <a name="output"></a>Ausgabe

```
In 'catch(CMyClass& catchC)'
2
In 'catch(MyStruct^ catchException)'
11
```

### <a name="order-of-unwinding-for-c-objects"></a>Reihenfolge der Entwickelung für C++ Objekte

Die Entwickelung tritt C++ für alle Objekte mit Dekonstruktoren auf, die sich auf dem Lauf Zeit Stapel zwischen der auslösenden Funktion und der Behandlungs Funktion befinden können. Da CLR-Typen auf dem Heap zugeordnet sind, wird die Entwickelung nicht angewendet.

Die Reihenfolge der Ereignisse für eine ausgelöste Ausnahme lautet wie folgt:

1. Die Runtime durchläuft den Stapel, der nach der entsprechenden catch-Klausel sucht, oder im Fall von Seh, mit Ausnahme von Filter für Seh, um die Ausnahme abzufangen. Catch-Klauseln werden zuerst in lexikalischer Reihenfolge durchsucht und dann dynamisch in der-aufrufsstapel angezeigt.

1. Nachdem der richtige Handler gefunden wurde, wird der Stapel an diesen Punkt entwickelt. Für jeden Funktions aufrufauf dem Stapel werden die lokalen Objekte zerstört, und es werden __finally Blöcke ausgeführt, von den meisten nach außen.

1. Sobald der Stapel entwickelt ist, wird die catch-Klausel ausgeführt.

### <a name="catching-unmanaged-types"></a>Abfangen von nicht verwalteten Typen

Wenn ein nicht verwalteter Objekttyp ausgelöst wird, wird er mit einer Ausnahme vom Typ <xref:System.Runtime.InteropServices.SEHException>umgerückt. Bei der Suche nach der entsprechenden **catch** -Klausel gibt es zwei Möglichkeiten.

- Wenn ein System C++ eigener Typ gefunden wird, wird die Ausnahme entpackt und mit dem gefundenen Typ verglichen. Dieser Vergleich ermöglicht, dass C++ ein System eigener Typ auf normale Weise abgefangen wird.

- Wenn jedoch eine **catch** -Klausel vom Typ " **SEHException** " oder einer der zugehörigen Basisklassen zuerst überprüft wird, wird die Ausnahme von der-Klausel abgefangen. Daher sollten Sie alle catch-Klauseln, die systemeigene C++ Typen erfassen, zuerst vor allen catch-Klauseln von CLR-Typen platzieren.

Dabei ist Folgendes zu beachten:

```
catch(Object^)
```

und

```
catch(...)
```

fängt alle ausgelösten Typen, einschließlich SEH-Ausnahmen, ab.

Wenn ein nicht verwalteter Typ durch catch (Objekt ^) abgefangen wird, wird das ausgelöste Objekt nicht zerstört.

Wenn Sie nicht verwaltete Ausnahmen auslösen oder abfangen, empfiehlt es sich, die [/EHsc](../build/reference/eh-exception-handling-model.md) -Compileroption anstelle von **/EHS** oder **/EHa**zu verwenden.

## <a name="see-also"></a>Siehe auch

[Behandlung von Ausnahmen](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[Behandlung von Ausnahmen](../cpp/exception-handling-in-visual-cpp.md)
