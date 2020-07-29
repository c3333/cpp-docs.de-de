---
title: new-Operator (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
ms.openlocfilehash: 81dd7483c49a699ac53ea53d33481fa6539d484c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223654"
---
# <a name="new-operator-c"></a>new-Operator (C++)

Ordnet Speicher für ein Objekt oder Array von Objekten vom *Typ "Name* " aus dem freien Speicher zu und gibt einen entsprechend typisierten, nicht-NULL-Zeiger auf das-Objekt zurück.

> [!NOTE]
> Microsoft C++-Komponenten Erweiterungen unterstützen das- **`new`** Schlüsselwort, um Vtable-Slot-Einträge hinzuzufügen. Weitere Informationen finden Sie unter [New (neuer Slot in Vtable)](../extensions/new-new-slot-in-vtable-cpp-component-extensions.md) .

## <a name="syntax"></a>Syntax

```
[::] new [placement] new-type-name [new-initializer]
[::] new [placement] ( type-name ) [new-initializer]
```

## <a name="remarks"></a>Bemerkungen

Wenn nicht erfolgreich, wird **`new`** NULL zurückgegeben, oder es wird eine Ausnahme ausgelöst. Weitere Informationen finden Sie [unter den Operatoren New und DELETE](../cpp/new-and-delete-operators.md) . Sie können dieses Standardverhalten ändern, indem Sie eine benutzerdefinierte Ausnahme Behandlungs Routine schreiben und die [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) Lauf Zeit Bibliotheksfunktion mit Ihrem Funktionsnamen als Argument aufrufen.

Informationen zum Erstellen eines Objekts auf dem verwalteten Heap finden Sie unter [gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md).

Wenn **`new`** verwendet wird, um Speicher für ein C++-Klassenobjekt zuzuweisen, wird der Konstruktor des Objekts aufgerufen, nachdem der Arbeitsspeicher zugewiesen wurde.

Verwenden Sie den [Delete](../cpp/delete-operator-cpp.md) -Operator, um die Zuordnung des dem Operator zugeordneten Arbeitsspeichers zu aufheben **`new`** .

Im folgenden Beispiel wird ein zweidimensionales Array der Größe `dim` durch 10 zugewiesen und dann freigegeben. Beim Zuweisen eines mehrdimensionalen Arrays müssen alle Dimensionen mit Ausnahme der ersten Konstantenausdrücke sein, die zu positiven Werten ausgewertet werden. Die Arraydimension ganz links kann ein beliebiger Ausdruck sein, der zu einem positiven Wert ausgewertet wird. Wenn Sie ein Array mithilfe des- **`new`** Operators zuordnen, kann die erste Dimension 0 (null) sein – der **`new`** Operator gibt einen eindeutigen Zeiger zurück.

```cpp
char (*pchar)[10] = new char[dim][10];
delete [] pchar;
```

*Type-Name* darf nicht **`const`** , **`volatile`** , Klassen Deklarationen oder Enumerationsdeklarationen enthalten. Daher ist der folgende Ausdruck ungültig:

```cpp
volatile char *vch = new volatile char[20];
```

Der- **`new`** Operator weist keine Verweis Typen zu, da es sich nicht um-Objekte handelt.

Der- **`new`** Operator kann nicht zum Zuordnen einer Funktion verwendet werden, kann jedoch verwendet werden, um Funktionen zu zuordnen. Im folgenden Beispiel wird ein Array von sieben Zeigern auf Funktionen, die ganze Zahlen zurückgeben, zugewiesen und dann freigegeben.

```cpp
int (**p) () = new (int (*[7]) ());
delete *p;
```

Wenn Sie den Operator **`new`** ohne zusätzliche Argumente verwenden und mit der [/GX](../build/reference/gx-enable-exception-handling.md)-, [/EHa](../build/reference/eh-exception-handling-model.md)-oder [/EHS](../build/reference/eh-exception-handling-model.md) -Option kompilieren, generiert der Compiler Code, um den Operator aufzurufen, **`delete`** Wenn der Konstruktor eine Ausnahme auslöst.

In der folgenden Liste werden die Grammatik Elemente von beschrieben **`new`** :

*Praktika*<br/>
Bietet eine Möglichkeit, zusätzliche Argumente zu übergeben, wenn Sie überladen **`new`** .

*Typname*<br/>
Gibt den zuzuweisenden Typ an. Es kann entweder ein integrierter oder ein benutzerdefinierter Typ sein. Eine komplizierte Typspezifikation können Sie in Klammern einschließen, um die Reihenfolge der Bindung zu erzwingen.

*initializer*<br/>
Stellt einen Wert für das initialisierte Objekt bereit. Für Arrays können keine Initialisierer angegeben werden. Der- **`new`** Operator erstellt nur dann Arrays von-Objekten, wenn die Klasse über einen Standardkonstruktor verfügt.

## <a name="example"></a>Beispiel

Im folgenden Codebeispiel werden ein Zeichenarray und ein Objekt der Klasse `CName` zugewiesen und dann wieder freigegeben.

```cpp
// expre_new_Operator.cpp
// compile with: /EHsc
#include <string.h>

class CName {
public:
   enum {
      sizeOfBuffer = 256
   };

   char m_szFirst[sizeOfBuffer];
   char m_szLast[sizeOfBuffer];

public:
   void SetName(char* pszFirst, char* pszLast) {
     strcpy_s(m_szFirst, sizeOfBuffer, pszFirst);
     strcpy_s(m_szLast, sizeOfBuffer, pszLast);
   }

};

int main() {
   // Allocate memory for the array
   char* pCharArray = new char[CName::sizeOfBuffer];
   strcpy_s(pCharArray, CName::sizeOfBuffer, "Array of characters");

   // Deallocate memory for the array
   delete [] pCharArray;
   pCharArray = NULL;

   // Allocate memory for the object
   CName* pName = new CName;
   pName->SetName("Firstname", "Lastname");

   // Deallocate memory for the object
   delete pName;
   pName = NULL;
}
```

## <a name="example"></a>Beispiel

Wenn Sie die Platzierung New Form des **`new`** Operators, das Formular mit Argumenten zusätzlich zur Größe der Zuordnung verwenden, unterstützt der Compiler keine Platzierungs Form des **`delete`** Operators, wenn der Konstruktor eine Ausnahme auslöst. Beispiel:

```cpp
// expre_new_Operator2.cpp
// C2660 expected
class A {
public:
   A(int) { throw "Fail!"; }
};
void F(void) {
   try {
      // heap memory pointed to by pa1 will be deallocated
      // by calling ::operator delete(void*).
      A* pa1 = new A(10);
   } catch (...) {
   }
   try {
      // This will call ::operator new(size_t, char*, int).
      // When A::A(int) does a throw, we should call
      // ::operator delete(void*, char*, int) to deallocate
      // the memory pointed to by pa2.  Since
      // ::operator delete(void*, char*, int) has not been implemented,
      // memory will be leaked when the deallocation cannot occur.

      A* pa2 = new(__FILE__, __LINE__) A(20);
   } catch (...) {
   }
}

int main() {
   A a;
}
```

## <a name="initializing-object-allocated-with-new"></a>Initialisieren von mit „new“ zugeordneten Objekten

Ein optionales *initialisiererfeld* ist in der Grammatik für den **`new`** Operator enthalten. Dadurch können neue Objekte mit benutzerdefinierten Konstruktoren initialisiert werden. Weitere Informationen zur Initialisierung finden Sie unter [Initialisierer](../cpp/initializers.md). Im folgenden Beispiel wird veranschaulicht, wie ein Initialisierungs Ausdruck mit dem-Operator verwendet wird **`new`** :

```cpp
// expre_Initializing_Objects_Allocated_with_new.cpp
class Acct
{
public:
    // Define default constructor and a constructor that accepts
    //  an initial balance.
    Acct() { balance = 0.0; }
    Acct( double init_balance ) { balance = init_balance; }
private:
    double balance;
};

int main()
{
    Acct *CheckingAcct = new Acct;
    Acct *SavingsAcct = new Acct ( 34.98 );
    double *HowMuch = new double ( 43.0 );
    // ...
}
```

In diesem Beispiel wird das Objekt `CheckingAcct` mit dem- **`new`** Operator zugeordnet, es wird jedoch keine Standard Initialisierung angegeben. Deshalb wird der Standardkonstruktor für die `Acct()`-Klasse aufgerufen. Anschließend wird das Objekt `SavingsAcct` auf die gleiche Weise zugeordnet, mit der Ausnahme, dass es explizit mit 34,98 initialisiert wird. Da 34,98 vom Typ ist **`double`** , wird der Konstruktor, der ein Argument dieses Typs annimmt, aufgerufen, um die Initialisierung zu verarbeiten. Schließlich wird der Nichtklassentyp `HowMuch` mit 43,0 initialisiert.

Wenn ein Objekt einen Klassentyp aufweist und diese Klasse über Konstruktoren verfügt (wie im vorherigen Beispiel), kann das Objekt nur dann vom Operator initialisiert werden, **`new`** Wenn eine dieser Bedingungen erfüllt ist:

- Die Argumente, die im Initialisierer bereitgestellt werden, stimmen mit denen eines Konstruktors überein.

- Die Klasse verfügt über einen Standardkonstruktor (einen Konstruktor, der ohne Argumente aufgerufen werden kann).

Beim Zuordnen von Arrays mithilfe des-Operators kann keine explizite Initialisierung pro Element ausgeführt werden **`new`** . nur der Standardkonstruktor wird aufgerufen, falls vorhanden. Weitere Informationen finden Sie unter [Standardargumente](../cpp/default-arguments.md) .

Wenn die Speicher Belegung fehlschlägt (**Operator new** gibt den Wert 0 zurück), wird keine Initialisierung ausgeführt. Dies schützt vor Versuchen, Daten zu initialisieren, die nicht vorhanden sind.

Wie bei Funktionsaufrufen ist auch bei initialisierten Ausdrücken die Reihenfolge der Auswertung nicht festgelegt. Darüber hinaus sollten Sie sich nicht darauf verlassen, dass diese Ausdrücke vollständig ausgewertet werden, bevor die Speicherbelegung ausgeführt wird. Wenn die Speicher Belegung fehlschlägt und der **`new`** Operator 0 (null) zurückgibt, können einige Ausdrücke im Initialisierer nicht vollständig ausgewertet werden.

## <a name="lifetime-of-objects-allocated-with-new"></a>Lebensdauer von mit „new“ zugeordneten Objekten

Mit dem-Operator zugeordnete-Objekte **`new`** werden nicht zerstört, wenn der Gültigkeitsbereich, in dem Sie definiert sind, beendet wird. Da der **`new`** Operator einen Zeiger auf die Objekte zurückgibt, die er zuordnet, muss das Programm einen Zeiger mit dem passenden Bereich definieren, um auf diese Objekte zuzugreifen. Beispiel:

```cpp
// expre_Lifetime_of_Objects_Allocated_with_new.cpp
// C2541 expected
int main()
{
    // Use new operator to allocate an array of 20 characters.
    char *AnArray = new char[20];

    for( int i = 0; i < 20; ++i )
    {
        // On the first iteration of the loop, allocate
        //  another array of 20 characters.
        if( i == 0 )
        {
            char *AnotherArray = new char[20];
        }
    }

    delete [] AnotherArray; // Error: pointer out of scope.
    delete [] AnArray;      // OK: pointer still in scope.
}
```

Sobald der Zeiger `AnotherArray` den Gültigkeitsbereich in dem Beispiel verlässt, kann das Objekt nicht mehr gelöscht werden.

## <a name="how-new-works"></a>Funktionsweise von „new“

Der *Zuordnungs Ausdruck* – der Ausdruck, der den **`new`** Operator enthält – führt drei Dinge aus:

- Sucht und reserviert Speicher für das zuzuweisende Objekt bzw. die zuzuweisenden Objekte. Nach Abschluss dieser Phase wird die richtige Menge an Speicherplatz zugewiesen. Es handelt sich jedoch noch nicht um ein Objekt.

- Initialisiert das/die Objekt(e). Sobald die Initialisierung abgeschlossen wurde, sind genügend Informationen vorhanden, damit der zugeordnete Speicher ein Objekt sein kann.

- Gibt einen Zeiger auf die Objekte eines Zeiger Typs zurück, der von *New-Type-Name* oder *Type-Name*abgeleitet wurde. Das Programm verwendet diesen Zeiger, um auf das neu zugeordnete Objekt zuzugreifen.

Der- **`new`** Operator Ruft den Funktions **Operator new**auf. Für Arrays eines beliebigen Typs und für Objekte, die nicht vom Datentyp **`class`** , **`struct`** oder sind **`union`** , wird eine globale Funktion, **:: Operator new**, aufgerufen, um Speicher zuzuweisen. Klassentyp Objekte können einen eigenen Operator für eine **neue** statische Member-Funktion pro Klasse definieren.

Wenn der Compiler auf den-Operator trifft, **`new`** um ein Objekt **type**vom Typ Type zuzuordnen, gibt er einen-Befehl an `type` **:: Operator new (sizeof (** `type` **))** oder, wenn kein benutzerdefinierter **Operator new** definiert ist, **:: Operator new (sizeof (** `type` **))**. Daher kann der **`new`** Operator die richtige Arbeitsspeicher Menge für das Objekt zuweisen.

> [!NOTE]
> Das Argument für **Operator new** ist vom Typ `size_t` . Dieser Typ wird in \<direct.h> , \<malloc.h> , \<memory.h> , \<search.h> , \<stddef.h> , \<stdio.h> , \<stdlib.h> , und definiert \<string.h> \<time.h> .

Eine Option in der Grammatik ermöglicht die Angabe der *Platzierung* (Weitere Informationen finden Sie in der Grammatik für [New-Operator](../cpp/new-operator-cpp.md)). Der *Platzierungs* Parameter kann nur für benutzerdefinierte Implementierungen des **new-Operators**verwendet werden. Dadurch können zusätzliche Informationen an den New- **Operator (New**) übermittelt werden. Ein Ausdruck mit einem *Platzierungs* Feld, z `T *TObject = new ( 0x0040 ) T;` . b., wird in übersetzt, `T *TObject = T::operator new( sizeof( T ), 0x0040 );` Wenn class T den Member-Operator new aufweist, andernfalls `T *TObject = ::operator new( sizeof( T ), 0x0040 );` .

Die ursprüngliche Absicht des *Platzierungs* Felds war es, hardwareabhängige Objekte bei benutzerdefinierten Adressen zuzuweisen.

> [!NOTE]
> Obwohl im vorangehenden Beispiel nur ein Argument im Feld " *Platzierung* " angezeigt wird, gibt es keine Einschränkung, wie viele zusätzliche Argumente auf diese Weise an den **Operator new** weitergegeben werden können.

Auch wenn der **Operator new** für einen Klassentyp definiert wurde, kann der globale Operator in der Form dieses Beispiels verwendet werden:

```cpp
T *TObject =::new TObject;
```

Der Bereichs Auflösungs Operator ( `::` ) erzwingt die Verwendung des globalen **`new`** Operators.

## <a name="see-also"></a>Siehe auch

[Ausdrücke mit unären Operatoren](../cpp/expressions-with-unary-operators.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[Operatoren new und delete](../cpp/new-and-delete-operators.md)
