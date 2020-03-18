---
title: Operatoren "new" und "delete"
ms.date: 11/19/2019
helpviewer_keywords:
- new keyword [C++]
- delete keyword [C++]
ms.assetid: fa721b9e-0374-4f04-bb87-032ea775bcc8
ms.openlocfilehash: 2fd665ce2570bbe7750684057cdf7f517f6f64f3
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445446"
---
# <a name="new-and-delete-operators"></a>Operatoren new und delete

C++unterstützt die dynamische Zuordnung und Aufhebung der Zuordnung von Objekten mithilfe der [New](new-operator-cpp.md) -und [Delete](delete-operator-cpp.md) -Operatoren. Diese Operatoren belegen Speicher für Objekte aus einem Pool, der als freier Speicher bezeichnet wird. Der **New** -Operator Ruft den besonderen Funktions [Operator new](new-operator-cpp.md)auf, und der **Delete** -Operator Ruft den speziellen Funktions [Operator Delete](delete-operator-cpp.md)auf.

Die **neue** Funktion in der C++ Standardbibliothek unterstützt das im C++ Standard angegebene Verhalten, das eine Std:: bad_alloc-Ausnahme auslöst, wenn die Speicher Belegung fehlschlägt. Wenn Sie weiterhin die nicht auslösende Version von **New**benötigen, verknüpfen Sie Ihr Programm mit nothrownew. obj. Wenn Sie jedoch mit nothrownew. obj verknüpfen, funktioniert der Standard **Operator new** in der C++ Standard Bibliothek nicht mehr.

Eine Liste der Bibliotheksdateien, die die C-Lauf Zeit Bibliothek und die C++ Standard Bibliothek enthalten, finden Sie unter [Funktionen der CRT-Bibliothek](../c-runtime-library/crt-library-features.md).

##  <a id="new_operator"> </a> Der New-Operator

Wenn eine-Anweisung wie die folgende in einem Programm gefunden wird, wird Sie in einen aufzurufenden Funktions **Operator new**übersetzt:

```cpp
char *pch = new char[BUFFER_SIZE];
```

Wenn die Anforderung eine Speichergröße von 0 (null) aufweist, gibt **Operator new** einen Zeiger auf ein unterschiedliches Objekt zurück (das heißt, dass wiederholte Aufrufe von **Operator new** andere Zeiger zurückgeben). Wenn für die Zuordnungs Anforderung nicht genügend Arbeitsspeicher verfügbar ist, löst **Operator new** eine `std::bad_alloc` Ausnahme aus oder gibt **nullptr** zurück, wenn Sie in einer nicht ausgelösten **Operator new** -Unterstützung verknüpft haben.

Sie können eine Routine schreiben, die versucht, Arbeitsspeicher freizugeben und die Zuordnung wiederherzustellen. Weitere Informationen finden Sie unter [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) . Weitere Informationen zum Wiederherstellungs Schema finden Sie im Abschnitt verarbeiten von unzureichendem Speicher dieses Themas.

Die beiden Bereiche für **Operator new** -Funktionen werden in der folgenden Tabelle beschrieben.

### <a name="scope-for-operator-new-functions"></a>Bereich für Operator new-Funktionen

|Operator|`Scope`|
|--------------|-----------|
|**:: Operator New**|Global|
|*Class-Name* **:: Operator new**|Klasse|

Das erste Argument für **Operator new** muss vom Typ `size_t` sein (ein Typ, der in \<STDDEF. h-> definiert ist), und der Rückgabetyp ist immer **void** <strong>\*</strong>.

Die globale **Operator new** -Funktion wird aufgerufen, wenn der **New** -Operator verwendet wird, um Objekte von integrierten Typen, Objekte des Klassen Typs, die keine benutzerdefinierten **Operator new** -Funktionen enthalten, sowie Arrays eines beliebigen Typs zuzuordnen. Wenn der **New** -Operator verwendet wird, um Objekte eines Klassen Typs zuzuordnen, bei dem ein **Operator new** definiert ist, wird der **New** -Operator der Klasse aufgerufen.

Eine **Operator new** -Funktion, die für eine Klasse definiert ist, ist eine statische Member-Funktion (die daher nicht virtuell sein kann), die die globale **Operator new** -Funktion für Objekte dieses Klassen Typs ausblendet. Beachten Sie den Fall, in dem **New** verwendet wird, um einen bestimmten Wert zuzuweisen und Arbeitsspeicher festzulegen:

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

Das Argument, das in Klammern für **New** angegeben ist, wird an `Blanks::operator new` als `chInit`-Argument übergeben. Allerdings wird die globale **Operator new** -Funktion ausgeblendet und bewirkt, dass Code wie der folgende einen Fehler generiert:

```cpp
Blanks *SomeBlanks = new Blanks;
```

Der Compiler unterstützt Member Array **New** -und **Delete** -Operatoren in einer Klassen Deklaration. Beispiel:

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

Es gibt eine weitere Möglichkeit, fehlgeschlagene Speicher Belegungs Anforderungen zu verarbeiten. Schreiben Sie eine benutzerdefinierte Wiederherstellungs Routine, um einen derartigen Fehler zu behandeln, und registrieren Sie die Funktion, indem Sie die [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) Lauf Zeitfunktion aufrufen.

##  <a id="delete_operator"> </a> Der Delete-Operator

Speicher, der mithilfe des **New** -Operators dynamisch zugewiesen wird, kann mithilfe des **Delete** -Operators freigegeben werden. Der Delete-Operator Ruft die **Operator Delete** -Funktion auf, die Arbeitsspeicher wieder an den verfügbaren Pool freigibt. Die Verwendung des **Delete** -Operators bewirkt auch, dass der klassendekonstruktor (sofern vorhanden) aufgerufen wird.

Es gibt globale und klassenspezifische **Operator Lösch** Funktionen. Für eine bestimmte Klasse kann nur eine **Delete-Operator** Funktion definiert werden. Wenn Sie definiert ist, wird die globale **Operator Delete** -Funktion ausgeblendet. Die globale **Operator Delete** -Funktion wird immer für Arrays eines beliebigen Typs aufgerufen.

Die globale **Operator Delete** -Funktion. Es gibt zwei Formen für die DELETE-und Klassenmember- **Operator Delete** -Funktionen des globalen **Operators** :

```cpp
void operator delete( void * );
void operator delete( void *, size_t );
```

Für eine bestimmte Klasse kann nur eine der beiden vorangehenden Formen vorhanden sein. Das erste Formular übernimmt ein einzelnes Argument vom Typ `void *`, das einen Zeiger auf das Objekt enthält, dessen Freigabe aufgehoben werden soll. Die zweite Form zum Aufheben der Zuordnung mit –-Größe – erfordert zwei Argumente, wobei der erste ein Zeiger auf den Speicherblock ist, dessen Zuordnung aufgehoben werden soll, und der zweite Wert ist die Anzahl der Bytes, deren Zuordnung aufgehoben werden soll. Der Rückgabetyp beider Formulare ist " **void** " (der**Operator "Delete** " kann keinen Wert zurückgeben).

Die zweite Form besteht darin, die Suche nach der richtigen Größen Kategorie des zu löschenden Objekts zu beschleunigen, das häufig nicht in der Nähe der Zuordnung selbst gespeichert wird und wahrscheinlich nicht zwischengespeichert ist. Die zweite Form ist nützlich, wenn eine **Operator Delete** -Funktion aus einer Basisklasse verwendet wird, um ein Objekt einer abgeleiteten Klasse zu löschen.

Die **Operator Delete** -Funktion ist statisch. Daher kann er nicht virtuell sein. Die **Operator Delete** -Funktion befolgt die Zugriffs Steuerung, wie in [Member-Access Control](member-access-control-cpp.md)beschrieben.

Das folgende Beispiel zeigt die benutzerdefinierten **Operatoren New** und **Operator Delete** , die zum Protokollieren von Zuordnungen und zum Entfernen von Speicher Belegungen dienen:

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

Mit dem vorangehenden Code kann "Arbeitsspeicherverlust" erkannt werden, also Arbeitsspeicher, der im freien Speicher zugeordnet, jedoch nicht freigegeben wurde. Um diese Erkennung auszuführen, werden die globalen **New** -und **Delete** -Operatoren neu definiert, um die Belegung und Freigabe von Arbeitsspeicher zu zählen.

Der Compiler unterstützt Member Array **New** -und **Delete** -Operatoren in einer Klassen Deklaration. Beispiel:

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
