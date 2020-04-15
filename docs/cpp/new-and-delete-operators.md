---
title: Operatoren "new" und "delete"
ms.date: 11/19/2019
helpviewer_keywords:
- new keyword [C++]
- delete keyword [C++]
ms.assetid: fa721b9e-0374-4f04-bb87-032ea775bcc8
ms.openlocfilehash: fd170c1500e2d80879fdd89f7d825930189ae942
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367891"
---
# <a name="new-and-delete-operators"></a>Operatoren new und delete

C++ unterstützt die dynamische Zuweisung und Deallation von Objekten mithilfe der [neuen](new-operator-cpp.md) und [löschoperatoren.](delete-operator-cpp.md) Diese Operatoren belegen Speicher für Objekte aus einem Pool, der als freier Speicher bezeichnet wird. Der **neue** Operator ruft den speziellen [Funktionsoperator neu](new-operator-cpp.md)auf, und der **delete-Operator** ruft den speziellen [Funktionsoperator delete](delete-operator-cpp.md)auf.

Die **neue** Funktion in der C++-Standardbibliothek unterstützt das im C++-Standard angegebene Verhalten, d. h. das Auslösen einer std::bad_alloc Ausnahme, wenn die Speicherzuweisung fehlschlägt. Wenn Sie immer noch die nicht werfende Version von **new**möchten, verknüpfen Sie Ihr Programm mit nothrownew.obj. Wenn Sie jedoch eine Verknüpfung mit nothrownew.obj herstellen, funktioniert der **Standardoperator neu** in der C++-Standardbibliothek nicht mehr.

Eine Liste der Bibliotheksdateien, aus denen die C-Laufzeitbibliothek und die C++-Standardbibliothek bestehen, finden Sie unter [CRT-Bibliotheksfeatures](../c-runtime-library/crt-library-features.md).

## <a name="the-new-operator"></a><a id="new_operator"> </a> Der neue Betreiber

Wenn eine Anweisung wie die folgende in einem Programm gefunden wird, wird sie in einen Aufruf an den **Funktionsoperator neu**übersetzt:

```cpp
char *pch = new char[BUFFER_SIZE];
```

Wenn es sich bei der Anforderung um Null Bytes Speicher handelt, gibt **der Operator new** einen Zeiger auf ein anderes Objekt zurück (d. h. wiederholte Aufrufe neuer **Operatoraufrufe** geben unterschiedliche Zeiger zurück). Wenn nicht genügend Arbeitsspeicher für die Zuweisungsanforderung vorhanden ist, löst **der Operator new** eine `std::bad_alloc` Ausnahme aus oder gibt **nullptr** zurück, wenn Sie eine Verknüpfung mit neuer Unterstützung **für den** nicht auslösenden Operator erhalten haben.

Sie können eine Routine schreiben, die versucht, Speicher freizugeben, und die Zuweisung wiederholen. weitere Informationen finden Sie [in _set_new_handler.](../c-runtime-library/reference/set-new-handler.md) Weitere Informationen zum Wiederherstellungsschema finden Sie im Abschnitt Umgang mit unzureichendem Arbeitsspeicher in diesem Thema.

Die beiden Bereiche für **neue** Operatorfunktionen werden in der folgenden Tabelle beschrieben.

### <a name="scope-for-operator-new-functions"></a>Spielraum für neue Funktionen des Bedieners

|Operator|Bereich|
|--------------|-----------|
|**::Operator neu**|Global|
|*Klassenname* **::operator neu**|Klasse|

Das erste Argument für **operator** `size_t` new muss vom \<Typ sein (ein Typ, der in stddef.h> definiert ist), und der Rückgabetyp ist immer **void** <strong>\*</strong>.

Die **neue** Funktion des globalen Operators wird aufgerufen, wenn der **neue** Operator verwendet wird, um Objekte integrierter Typen, Objekte vom Klassentyp, die keine benutzerdefinierten **Operator-Neuenfunktionen** enthalten, und Arrays eines beliebigen Typs zuzuweisen. Wenn der **neue** Operator verwendet wird, um Objekte eines Klassentyps zuzuweisen, bei dem ein **neuer Operator** definiert ist, wird der **Operator new** dieser Klasse aufgerufen.

Eine für eine Klasse definierte **Operator-Neue-Funktion** ist eine statische Memberfunktion (die daher nicht virtuell sein kann), die die neue Funktion des globalen **Operators** für Objekte dieses Klassentyps ausblendet. Betrachten Sie den Fall, in dem **new** verwendet wird, um Speicher zuzuweisen und auf einen bestimmten Wert festzulegen:

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

Das Argument, das in **new** Klammern zu `Blanks::operator new` neu `chInit` angegeben wird, wird als Argument übergeben. Die neue Funktion des globalen **Operators** ist jedoch ausgeblendet, sodass Code wie der folgende einen Fehler generiert:

```cpp
Blanks *SomeBlanks = new Blanks;
```

Der Compiler unterstützt Member Array **new** und **delete** operators in einer Klassendeklaration. Beispiel:

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

Tests auf fehlgeschlagene Speicherzuweisung können wie hier gezeigt durchgeführt werden:

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

Es gibt eine weitere Möglichkeit, fehlgeschlagene Speicherzuweisungsanforderungen zu behandeln. Schreiben Sie eine benutzerdefinierte Wiederherstellungsroutine, um einen solchen Fehler zu behandeln, und registrieren Sie dann Ihre Funktion, indem Sie die [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) Laufzeitfunktion aufrufen.

## <a name="the-delete-operator"></a><a id="delete_operator"> </a> Der Löschoperator

Speicher, der dynamisch mit dem **neuen** Operator zugewiesen wird, kann mit dem **Delete-Operator** freigegeben werden. Der delete-Operator ruft die **Operatorlöschfunktion auf,** die den Speicher wieder in den verfügbaren Pool freigibt. Die Verwendung des **delete-Operators** bewirkt auch, dass der Klassendestruktor (falls vorhanden) aufgerufen wird.

Es gibt globale und klassenbezogene **Operatorlöschfunktionen.** Für eine bestimmte Klasse kann nur eine **Operatorlöschfunktion** definiert werden. Wenn definiert, blendet es die **Löschfunktion** des globalen Operators aus. Die **Löschfunktion** des globalen Operators wird immer für Arrays eines beliebigen Typs aufgerufen.

Die **Löschfunktion** des globalen Operators. Für die **Löschfunktionen** des globalen **Operators** und des Klassenmemberoperators sind zwei Formulare vorhanden:

```cpp
void operator delete( void * );
void operator delete( void *, size_t );
```

Für eine bestimmte Klasse kann nur eines der beiden vorhergehenden Formulare vorhanden sein. Die erste Form hat ein `void *`einzelnes Argument vom Typ , das einen Zeiger auf das zu verteilende Objekt enthält. Die zweite Form – die Größe der Deallocation – verwendet zwei Argumente, von denen das erste ein Zeiger auf den Speicherblock ist, der die Zuweisung aufheben soll, und das zweite ist die Anzahl der Bytes, die deallocatezugewiesen werden sollen. Der Rückgabetyp beider Formulare ist **void** **(Operator delete** kann keinen Wert zurückgeben).

Die Absicht des zweiten Formulars besteht darin, die Suche nach der richtigen Größenkategorie des zu löschenden Objekts zu beschleunigen, die oft nicht in der Nähe der Zuordnung selbst gespeichert und wahrscheinlich nicht zwischengespeichert wird. Das zweite Formular ist nützlich, wenn eine **Operatorlöschfunktion** aus einer Basisklasse verwendet wird, um ein Objekt einer abgeleiteten Klasse zu löschen.

Die **Löschfunktion des Operators** ist statisch. daher kann es nicht virtuell sein. Die **Operatorlöschfunktion** gehorcht der Zugriffssteuerung, wie unter [Member-Access Control](member-access-control-cpp.md)beschrieben.

Das folgende Beispiel zeigt benutzerdefinierte **Operator-Neue-** und **Operatorlöschfunktionen** zum Protokollieren von Zuweisungen und Speicherzuweisungen:

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

Mit dem vorangehenden Code kann "Arbeitsspeicherverlust" erkannt werden, also Arbeitsspeicher, der im freien Speicher zugeordnet, jedoch nicht freigegeben wurde. Um diese Erkennung durchzuführen, werden die globalen **neuen** und **löschoperatoren** neu definiert, um die Zuweisung und Zuweisung des Speichers zu zählen.

Der Compiler unterstützt Member Array **new** und **delete** operators in einer Klassendeklaration. Beispiel:

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
