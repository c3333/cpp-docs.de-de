---
title: Operatoren new und delete
description: Die C++ Language New-und DELETE-Operatoren ermöglichen die Steuerung der Zuordnung.
ms.date: 07/07/2020
helpviewer_keywords:
- new keyword [C++]
- delete keyword [C++]
ms.openlocfilehash: e609d1fdbd4f945ab8709c554d1396100027c4c1
ms.sourcegitcommit: e17cc8a478b51739d67304d7d82422967b35f716
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/08/2020
ms.locfileid: "86127852"
---
# <a name="new-and-delete-operators"></a>Die Operatoren `new` und `delete`

C++ unterstützt die dynamische Zuordnung und Aufhebung der Zuordnung von Objekten mithilfe der [`new`](new-operator-cpp.md) [`delete`](delete-operator-cpp.md) Operatoren und. Diese Operatoren belegen Speicher für Objekte aus einem Pool, der als freier Speicher bezeichnet wird. Der **`new`** -Operator Ruft die Special [`operator new`](new-operator-cpp.md) -Funktion auf, und der- **`delete`** Operator Ruft die Special-Funktion auf [`operator delete`](delete-operator-cpp.md) .

Die- **`new`** Funktion in der C++-Standardbibliothek unterstützt das im C++-Standard angegebene Verhalten, das eine-Ausnahme auslöst, `std::bad_alloc` Wenn die Speicher Belegung fehlschlägt. Wenn Sie weiterhin die nicht auslösende Version von wünschen **`new`** , verknüpfen Sie das Programm mit *`nothrownew.obj`* . Wenn Sie jedoch mit verknüpfen *`nothrownew.obj`* , funktioniert der Standardwert **`operator new`** in der C++-Standard Bibliothek nicht mehr.

Eine Liste der Bibliotheksdateien in der C-Lauf Zeit Bibliothek und der C++-Standard Bibliothek finden Sie unter [Funktionen der CRT-Bibliothek](../c-runtime-library/crt-library-features.md).

## <a name="the-new-operator"></a><a id="new_operator"> </a> Der `new` Operator

Der Compiler übersetzt eine-Anweisung, z. b. diese, in einen-Rückruf der-Funktion **`operator new`** :

```cpp
char *pch = new char[BUFFER_SIZE];
```

Wenn die Anforderung 0 (null) beträgt, **`operator new`** gibt einen Zeiger auf ein unterschiedliches Objekt zurück. Das heißt, dass wiederholte Aufrufe von **`operator new`** andere Zeiger zurückgeben. Wenn für die Zuordnungs Anforderung nicht genügend Arbeitsspeicher verfügbar ist, löst **`operator new`** eine- `std::bad_alloc` Ausnahme aus. Oder es wird zurückgegeben, **`nullptr`** Wenn Sie mit nicht ausgelösten **`operator new`** Unterstützung verknüpft haben.

Sie können eine Routine schreiben, die versucht, Arbeitsspeicher freizugeben und die Zuordnung erneut zu versuchen. Weitere Informationen finden Sie unter [`_set_new_handler`](../c-runtime-library/reference/set-new-handler.md). Ausführliche Informationen zum Wiederherstellungs Schema finden Sie im Abschnitt [Behandlung von unzureichendem Speicher](#handling-insufficient-memory) .

**`operator new`** In der folgenden Tabelle werden die beiden Bereiche für Funktionen beschrieben.

### <a name="scope-for-operator-new-functions"></a>Bereich für `operator new` Funktionen

| Operator | Bereich |
|--|--|
| **`::operator new`** | Global |
| *Klassenname***`::operator new`** | Klasse |

Das erste Argument für **`operator new`** muss vom Typ sein `size_t` , das in definiert ist, \<stddef.h> und der Rückgabetyp ist immer **`void*`** .

Die globale- **`operator new`** Funktion wird aufgerufen, wenn der- **`new`** Operator verwendet wird, um Objekte von integrierten Typen, Objekte des Klassen Typs, die keine benutzerdefinierten **`operator new`** Funktionen enthalten, und Arrays eines beliebigen Typs zuzuordnen. Wenn der **`new`** -Operator verwendet wird, um Objekte eines Klassen Typs zuzuweisen, in dem eine **`operator new`** definiert ist, wird die dieser Klasse **`operator new`** aufgerufen.

Eine **`operator new`** Funktion, die für eine Klasse definiert ist, ist eine statische Member-Funktion (die nicht virtuell sein kann), die die globale **`operator new`** Funktion für Objekte dieses Klassen Typs verbirgt. Beachten Sie den Fall **`new`** , in dem verwendet wird, um einen bestimmten Wert zuzuweisen und Arbeitsspeicher festzulegen:

```cpp
#include <malloc.h>
#include <memory.h>

class Blanks
{
public:
    Blanks(){}
    void *operator new( size_t stAllocateBlock, char chInit );
};
void *Blanks::operator new( size_t stAllocateBlock, char chInit )
{
    void *pvTemp = malloc( stAllocateBlock );
    if( pvTemp != 0 )
        memset( pvTemp, chInit, stAllocateBlock );
    return pvTemp;
}
// For discrete objects of type Blanks, the global operator new function
// is hidden. Therefore, the following code allocates an object of type
// Blanks and initializes it to 0xa5
int main()
{
   Blanks *a5 = new(0xa5) Blanks;
   return a5 != 0;
}
```

Das Argument, das in Klammern für angegeben **`new`** wird, wird `Blanks::operator new` als Argument an übergeben `chInit` . Die globale **`operator new`** Funktion ist jedoch ausgeblendet und bewirkt, dass Code wie der folgende einen Fehler generiert:

```cpp
Blanks *SomeBlanks = new Blanks;
```

Der Compiler unterstützt Member **`new`** -Arrays und- **`delete`** Operatoren in einer Klassen Deklaration. Beispiel:

```cpp
class MyClass
{
public:
   void * operator new[] (size_t)
   {
      return 0;
   }
   void   operator delete[] (void*)
   {
   }
};

int main()
{
   MyClass *pMyClass = new MyClass[5];
   delete [] pMyClass;
}
```

### <a name="handling-insufficient-memory"></a>Behandeln von ungenügendem Arbeitsspeicher

Das Testen auf fehlerhafte Speicher Belegung kann wie hier gezeigt erfolgen:

```cpp
#include <iostream>
using namespace std;
#define BIG_NUMBER 100000000
int main() {
   int *pI = new int[BIG_NUMBER];
   if( pI == 0x0 ) {
      cout << "Insufficient memory" << endl;
      return -1;
   }
}
```

Es gibt eine weitere Möglichkeit, fehlgeschlagene Speicher Belegungs Anforderungen zu verarbeiten. Schreiben Sie eine benutzerdefinierte Wiederherstellungs Routine, um einen derartigen Fehler zu behandeln, und registrieren Sie die Funktion, indem Sie die [`_set_new_handler`](../c-runtime-library/reference/set-new-handler.md) -Lauf Zeitfunktion aufrufen.

## <a name="the-delete-operator"></a><a id="delete_operator"> </a> Der `delete` Operator

Arbeitsspeicher, der mithilfe des-Operators dynamisch zugewiesen wird, **`new`** kann mithilfe des-Operators freigegeben werden **`delete`** . Der Delete-Operator Ruft die- **`operator delete`** Funktion auf, die Arbeitsspeicher für den verfügbaren Pool wieder freigibt. Die Verwendung des- **`delete`** Operators bewirkt auch, dass der Klassen Dekonstruktor (sofern vorhanden) aufgerufen wird.

Es gibt globale und klassenspezifische **`operator delete`** Funktionen. Nur eine **`operator delete`** Funktion kann für eine bestimmte Klasse definiert werden. sofern definiert, blendet sie die globale **`operator delete`** Funktion aus. Die globale **`operator delete`** Funktion wird immer für Arrays eines beliebigen Typs aufgerufen.

Die globale **`operator delete`** Funktion. Für die globalen **`operator delete`** und Klassenmember-Funktionen gibt es zwei Formen **`operator delete`** :

```cpp
void operator delete( void * );
void operator delete( void *, size_t );
```

Für eine bestimmte Klasse kann nur eine der beiden vorangehenden Formen vorhanden sein. Das erste Formular übernimmt ein einzelnes Argument vom Typ **`void *`** , das einen Zeiger auf das Objekt enthält, dessen Zuordnungen aufgehoben werden soll. Das zweite Formular, die Zuordnung mit der Größenanpassung, erfordert zwei Argumente: das erste ist ein Zeiger auf den Speicherblock, dessen Zuordnung aufgehoben werden soll, und der zweite Wert ist die Anzahl der Bytes, deren Zuordnung aufgehoben werden soll. Der Rückgabetyp beider Formulare ist **`void`** ( **`operator delete`** kann keinen Wert zurückgeben).

Die zweite Form besteht darin, die Suche nach der richtigen Größen Kategorie des zu löschenden Objekts zu beschleunigen. Diese Informationen werden häufig nicht in der Nähe der Zuordnung gespeichert und werden wahrscheinlich nicht zwischengespeichert. Die zweite Form ist nützlich, wenn eine **`operator delete`** Funktion aus einer Basisklasse verwendet wird, um ein Objekt einer abgeleiteten Klasse zu löschen.

Die **`operator delete`** Funktion ist statisch und kann daher nicht virtuell sein. Die **`operator delete`** Funktion befolgt die Zugriffs Steuerung, wie in [Member-Access Control](member-access-control-cpp.md)beschrieben.

Im folgenden Beispiel werden benutzerdefinierte **`operator new`** Funktionen und **`operator delete`** Funktionen gezeigt, die zum Protokollieren von Zuordnungen und zum Aufsetzen von Speicher Belegungen dienen

```cpp
#include <iostream>
using namespace std;

int fLogMemory = 0;      // Perform logging (0=no; nonzero=yes)?
int cBlocksAllocated = 0;  // Count of blocks allocated.

// User-defined operator new.
void *operator new( size_t stAllocateBlock ) {
   static int fInOpNew = 0;   // Guard flag.

   if ( fLogMemory && !fInOpNew ) {
      fInOpNew = 1;
      clog << "Memory block " << ++cBlocksAllocated
          << " allocated for " << stAllocateBlock
          << " bytes\n";
      fInOpNew = 0;
   }
   return malloc( stAllocateBlock );
}

// User-defined operator delete.
void operator delete( void *pvMem ) {
   static int fInOpDelete = 0;   // Guard flag.
   if ( fLogMemory && !fInOpDelete ) {
      fInOpDelete = 1;
      clog << "Memory block " << cBlocksAllocated--
          << " deallocated\n";
      fInOpDelete = 0;
   }

   free( pvMem );
}

int main( int argc, char *argv[] ) {
   fLogMemory = 1;   // Turn logging on
   if( argc > 1 )
      for( int i = 0; i < atoi( argv[1] ); ++i ) {
         char *pMem = new char[10];
         delete[] pMem;
      }
   fLogMemory = 0;  // Turn logging off.
   return cBlocksAllocated;
}
```

Der vorangehende Code kann verwendet werden, um "Speicherlecks" zu erkennen, d. h. Arbeitsspeicher, der im freien Speicher zugeordnet ist, aber nie freigegeben wird. Um Verluste zu erkennen, werden die globalen **`new`** **`delete`** Operatoren und neu definiert, um die Belegung und Freigabe von Arbeitsspeicher zu zählen.

Der Compiler unterstützt Member **`new`** -Arrays und- **`delete`** Operatoren in einer Klassen Deklaration. Beispiel:

```cpp
// spec1_the_operator_delete_function2.cpp
// compile with: /c
class X  {
public:
   void * operator new[] (size_t) {
      return 0;
   }
   void operator delete[] (void*) {}
};

void f() {
   X *pX = new X[5];
   delete [] pX;
}
```
