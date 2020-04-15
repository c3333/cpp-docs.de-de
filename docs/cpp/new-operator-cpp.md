---
title: new-Operator (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
ms.openlocfilehash: ac89bf37b8aaaa9d77393b714a233f8a4c998139
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367870"
---
# <a name="new-operator-c"></a>new-Operator (C++)

Ordnet Speicher für ein Objekt oder Array von Objekten mit *Typname* aus dem freien Speicher zu und gibt einen entsprechend typisierten, ungleich Nullen-Zeiger an das Objekt zurück.

> [!NOTE]
> Microsoft C++ Component Extensions bietet Unterstützung für das **neue** Schlüsselwort zum Hinzufügen von vtable Slot-Einträgen. Weitere Informationen finden Sie unter [Neu (neuer Steckplatz in vtable)](../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)

## <a name="syntax"></a>Syntax

```
[::] new [placement] new-type-name [new-initializer]
[::] new [placement] ( type-name ) [new-initializer]
```

## <a name="remarks"></a>Bemerkungen

Wenn dies nicht der Fall ist, gibt **New** Null zurück oder löst eine Ausnahme aus. Weitere Informationen finden Sie unter [Neue und Löschen von Operatoren.](../cpp/new-and-delete-operators.md) Sie können dieses Standardverhalten ändern, indem Sie eine benutzerdefinierte Ausnahmebehandlungsroutine schreiben und die [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) Laufzeitbibliotheksfunktion mit Ihrem Funktionsnamen als Argument aufrufen.

Informationen zum Erstellen eines Objekts auf dem verwalteten Heap finden Sie unter [gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md).

Wenn **new** verwendet wird, um Speicher für ein C++-Klassenobjekt zuzuweisen, wird der Konstruktor des Objekts aufgerufen, nachdem der Speicher zugewiesen wurde.

Verwenden Sie den [Delete-Operator,](../cpp/delete-operator-cpp.md) um den dem **neuen** Operator zugewiesenen Speicher zuzuweisen.

Im folgenden Beispiel wird ein zweidimensionales Array der Größe `dim` durch 10 zugewiesen und dann freigegeben. Beim Zuweisen eines mehrdimensionalen Arrays müssen alle Dimensionen mit Ausnahme der ersten Konstantenausdrücke sein, die zu positiven Werten ausgewertet werden. Die Arraydimension ganz links kann ein beliebiger Ausdruck sein, der zu einem positiven Wert ausgewertet wird. Beim Zuweisen eines Arrays mit dem **neuen** Operator kann die erste Dimension Null sein – der **neue** Operator gibt einen eindeutigen Zeiger zurück.

```cpp
char (*pchar)[10] = new char[dim][10];
delete [] pchar;
```

Der *Typname* darf keine **const**-, **volatile-,** Klassendeklarationen oder Enumerationsdeklarationen enthalten. Daher ist der folgende Ausdruck ungültig:

```cpp
volatile char *vch = new volatile char[20];
```

Der **neue** Operator weist keine Verweistypen zu, da sie keine Objekte sind.

Der **neue** Operator kann nicht zum Zuweisen einer Funktion verwendet werden, aber er kann verwendet werden, um Zeigern auf Funktionen zuzuweisen. Im folgenden Beispiel wird ein Array von sieben Zeigern auf Funktionen, die ganze Zahlen zurückgeben, zugewiesen und dann freigegeben.

```cpp
int (**p) () = new (int (*[7]) ());
delete *p;
```

Wenn Sie den Operator **new** ohne zusätzliche Argumente verwenden und mit der Option [/GX](../build/reference/gx-enable-exception-handling.md), [/EHa](../build/reference/eh-exception-handling-model.md)oder [/EHs](../build/reference/eh-exception-handling-model.md) kompilieren, generiert der Compiler Code zum Aufrufen von **Operatordelete,** wenn der Konstruktor eine Ausnahme auslöst.

In der folgenden Liste werden die Grammatikelemente **von neuen**beschrieben:

*Platzierung*<br/>
Bietet eine Möglichkeit, zusätzliche Argumente zu übergeben, wenn Sie **neue**überladen.

*Typname*<br/>
Gibt den zuzuweisenden Typ an. Es kann entweder ein integrierter oder ein benutzerdefinierter Typ sein. Eine komplizierte Typspezifikation können Sie in Klammern einschließen, um die Reihenfolge der Bindung zu erzwingen.

*initializer*<br/>
Stellt einen Wert für das initialisierte Objekt bereit. Für Arrays können keine Initialisierer angegeben werden. Der **neue** Operator erstellt Arrays von Objekten nur, wenn die Klasse über einen Standardkonstruktor verfügt.

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

Wenn Sie die neue Platzierungsform des **neuen** Operators verwenden, unterstützt der Compiler neben der Größe der Zuordnung das Formular mit Argumenten, ein Platzierungsformular des **löschoperators** nicht, wenn der Konstruktor eine Ausnahme auslöst. Beispiel:

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

Ein optionales *Initialisierungsfeld* ist in der Grammatik für den **neuen** Operator enthalten. Dadurch können neue Objekte mit benutzerdefinierten Konstruktoren initialisiert werden. Weitere Informationen zur Initialisierung finden Sie unter [Initialisierer](../cpp/initializers.md). Im folgenden Beispiel wird veranschaulicht, wie ein Initialisierungsausdruck mit dem **neuen** Operator verwendet wird:

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

In diesem Beispiel `CheckingAcct` wird das Objekt mit dem **neuen** Operator zugewiesen, es wird jedoch keine Standardinitialisierung angegeben. Deshalb wird der Standardkonstruktor für die `Acct()`-Klasse aufgerufen. Anschließend wird das Objekt `SavingsAcct` auf die gleiche Weise zugeordnet, mit der Ausnahme, dass es explizit mit 34,98 initialisiert wird. Da 34.98 vom Typ **double**ist, wird der Konstruktor, der ein Argument dieses Typs verwendet, aufgerufen, um die Initialisierung zu verarbeiten. Schließlich wird der Nichtklassentyp `HowMuch` mit 43,0 initialisiert.

Wenn ein Objekt von einem Klassentyp ist und diese Klasse über Konstruktoren verfügt (wie im vorherigen Beispiel), kann das Objekt vom **neuen** Operator nur initialisiert werden, wenn eine dieser Bedingungen erfüllt ist:

- Die Argumente, die im Initialisierer bereitgestellt werden, stimmen mit denen eines Konstruktors überein.

- Die Klasse verfügt über einen Standardkonstruktor (einen Konstruktor, der ohne Argumente aufgerufen werden kann).

Beim Zuweisen von Arrays mit dem **neuen** Operator kann keine explizite Pro-Element-Initialisierung durchgeführt werden. Nur der Standardkonstruktor, falls vorhanden, wird aufgerufen. Weitere Informationen finden Sie unter [Standardargumente.](../cpp/default-arguments.md)

Wenn die Speicherzuordnung fehlschlägt **(Operator new** gibt den Wert 0 zurück), wird keine Initialisierung durchgeführt. Dies schützt vor Versuchen, Daten zu initialisieren, die nicht vorhanden sind.

Wie bei Funktionsaufrufen ist auch bei initialisierten Ausdrücken die Reihenfolge der Auswertung nicht festgelegt. Darüber hinaus sollten Sie sich nicht darauf verlassen, dass diese Ausdrücke vollständig ausgewertet werden, bevor die Speicherbelegung ausgeführt wird. Wenn die Speicherzuweisung fehlschlägt und der **neue** Operator Null zurückgibt, werden einige Ausdrücke im Initialisierer möglicherweise nicht vollständig ausgewertet.

## <a name="lifetime-of-objects-allocated-with-new"></a>Lebensdauer von mit „new“ zugeordneten Objekten

Objekte, die dem **neuen** Operator zugewiesen sind, werden nicht zerstört, wenn der Bereich, in dem sie definiert sind, beendet wird. Da der **neue** Operator einen Zeiger auf die zugeteilten Objekte zurückgibt, muss das Programm einen Zeiger mit dem geeigneten Bereich definieren, um auf diese Objekte zuzugreifen. Beispiel:

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

Der *Allocation-Ausdruck* – der Ausdruck, der den **neuen** Operator enthält – führt drei Dinge aus:

- Sucht und reserviert Speicher für das zuzuweisende Objekt bzw. die zuzuweisenden Objekte. Nach Abschluss dieser Phase wird die richtige Menge an Speicherplatz zugewiesen. Es handelt sich jedoch noch nicht um ein Objekt.

- Initialisiert das/die Objekt(e). Sobald die Initialisierung abgeschlossen wurde, sind genügend Informationen vorhanden, damit der zugeordnete Speicher ein Objekt sein kann.

- Gibt einen Zeiger auf das Objekt(n) eines Zeigertyps zurück, der von *new-type-name* oder *type-name*abgeleitet ist. Das Programm verwendet diesen Zeiger, um auf das neu zugeordnete Objekt zuzugreifen.

Der **neue** Operator ruft den **Funktionsoperator new**auf. Für Arrays eines beliebigen Typs und für Objekte, die nicht von **Klassen-,** **Struktur-** oder **Union-Typen** stammen, wird eine globale Funktion, **::operator new**, aufgerufen, um Speicher zuzuweisen. Klassentypobjekte können ihre eigene **statische Operatorfunktion** pro Klasse definieren.

Wenn der Compiler auf den **neuen** Operator trifft, um ein `type`Objekt vom Typ **Typ**zuzuweisen, gibt er einen Aufruf von **::operator new( sizeof(** `type` **) )** aus, oder, wenn kein benutzerdefinierter Operator **new** definiert ist, **::operator new( sizeof(** `type` **) )**. Daher kann der **neue** Operator die richtige Speichermenge für das Objekt zuweisen.

> [!NOTE]
> Das Argument für den `size_t`Operator **new** ist vom Typ . Dieser Typ ist \<in direct.h>, \<malloc.h>, \<memory.h>, \<search.h>, \<stddef.h>, \<stdio.h>, \<stdlib.h>, \<string.h> und \<time.h> definiert.

Eine Option in der Grammatik ermöglicht die Spezifikation der *Platzierung* (siehe Grammatik für [neuen Operator](../cpp/new-operator-cpp.md)). Der *Platzierungsparameter* kann nur für benutzerdefinierte Implementierungen des **Operators new**verwendet werden. Es ermöglicht die Weitergabe zusätzlicher Informationen an **den Operator new**. Ein Ausdruck mit einem `T *TObject = new ( 0x0040 ) T;` *Platzierungsfeld,* wie es übersetzt wird, `T *TObject = ::operator new( sizeof( T ), 0x0040 );` `T *TObject = T::operator new( sizeof( T ), 0x0040 );` wenn Klasse T den Memberoperator neu hat, andernfalls in .

Die ursprüngliche Absicht *placement* des Platzierungsfeldes bestand darin, die Zuweisung hardwareabhängiger Objekte an benutzerdefinierten Adressen zu ermöglichen.

> [!NOTE]
> Obwohl das obige Beispiel nur ein Argument im *Platzierungsfeld* zeigt, gibt es keine Einschränkung, wie viele zusätzliche Argumente auf diese Weise an den **Operator new** übergeben werden können.

Selbst wenn der **Operator new** für einen Klassentyp definiert wurde, kann der globale Operator mithilfe der Form dieses Beispiels verwendet werden:

```cpp
T *TObject =::new TObject;
```

Der Scope-Resolution-Operator (`::`) erzwingt den Einsatz des globalen **neuen** Operators.

## <a name="see-also"></a>Siehe auch

[Ausdrücke mit unären Operatoren](../cpp/expressions-with-unary-operators.md)<br/>
[Keywords](../cpp/keywords-cpp.md)<br/>
[Neue und löschen operatoren](../cpp/new-and-delete-operators.md)
