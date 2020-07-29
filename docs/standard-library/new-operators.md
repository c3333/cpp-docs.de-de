---
title: '&lt;neue &gt; Operatoren und Aufstände'
ms.date: 11/04/2016
f1_keywords:
- new/std::operator delete
- new/std::operator new
ms.assetid: d1af4b56-9a95-4c65-ab01-bf43e982c7bd
ms.openlocfilehash: 2af2b3bc24e045d66626607781bc97f83686d559
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215633"
---
# <a name="ltnewgt-operators-and-enums"></a>&lt;neue &gt; Operatoren und Aufstände

## <a name="enum-align_val_t"></a><a name="op_align_val_t"></a>Aufzählungs align_val_t

```cpp
enum class align_val_t : size_t {};
```

## <a name="operator-delete"></a><a name="op_delete"></a>Operator löschen

Die Funktion, die von einem DELETE-Ausdruck aufgerufen wird, um Speicher für einzelne Objekte zuzuweisen.

```cpp
void operator delete(void* ptr) throw();
void operator delete(void *, void*) throw();
void operator delete(void* ptr, const std::nothrow_t&) throw();
```

### <a name="parameters"></a>Parameter

*PTR*\
Der Zeiger, dessen Wert durch den Löschvorgang als ungültig gerendert werden soll.

### <a name="remarks"></a>Bemerkungen

Die erste Funktion wird von einem DELETE-Ausdruck aufgerufen, um den Wert von *ptr* ungültig zu erzeugen. Das Programm kann eine Funktion mit dieser Funktionssignatur definieren, die die von der C++-Standardbibliothek definierte Standardversion ersetzt. Das erforderliche Verhalten besteht darin, einen Wert von *ptr* zu akzeptieren, der NULL ist oder durch einen früheren- [Operator new](../standard-library/new-operators.md#op_new)(**size_t**) zurückgegeben wurde.

Das Standardverhalten für einen NULL-Wert von *ptr* besteht darin, nichts zu tun. Jeder andere Wert von *ptr* muss ein Wert sein, der zuvor von einem-Befehl zurückgegeben wurde, wie zuvor beschrieben. Das Standardverhalten für einen solchen Wert, der nicht *NULL ist, besteht darin,* den Speicher freizugeben, der durch den vorherigen-Befehl reserviert wurde. Der Wert ist nicht angegeben, unter welchen Bedingungen oder der gesamte freigegebene Speicher durch einen nachfolgenden Aufrufvorgang `operator new` (**size_t**) oder zu einem beliebigen von `calloc` ( **size_t**), `malloc` ( **size_t**) oder `realloc` ( **`void`** <strong>\*</strong> , **size_t**) zugeordnet wird.

Die zweite Funktion wird durch einen Platzierungs Lösch Ausdruck aufgerufen, der einem neuen Ausdruck in der Form entspricht **`new`** ( **Std:: size_t**). Dabei wird keine Aktion ausgeführt.

Die dritte Funktion wird durch einen Platzierungs Lösch Ausdruck aufgerufen, der einem neuen Ausdruck in der Form entspricht **`new`** ( **Std:: size_t**, **conststd:: nothrow_t&**). Das Programm kann eine Funktion mit dieser Funktionssignatur definieren, die die von der C++-Standardbibliothek definierte Standardversion ersetzt. Als erforderliches Verhalten soll ein Wert von `ptr` akzeptiert werden, der gleich 0 (null) ist oder durch einen früheren Aufruf von `operator new`( **size_t**). zurückgegeben wurde. Das Standardverhalten ist die Auswertung von **`delete`** ( `ptr` ).

### <a name="example"></a>Beispiel

Unter [Operator new](../standard-library/new-operators.md#op_new) finden Sie ein Beispiel für die Verwendung von **Operator Delete**.

## <a name="operator-delete"></a><a name="op_delete_arr"></a>Delete-Operator []

Die Funktion, die durch einen Löschausdruck (delete-Ausdruck) aufgerufen wird, um Speicher für ein Array von Objekten freizugeben.

```cpp
void operator delete[](void* ptr) throw();
void operator delete[](void *, void*) throw();
void operator delete[](void* ptr, const std::nothrow_t&) throw();
```

### <a name="parameters"></a>Parameter

*PTR*\
Der Zeiger, dessen Wert durch den Löschvorgang als ungültig gerendert werden soll.

### <a name="remarks"></a>Bemerkungen

Die erste Funktion wird von einem `delete[]` Ausdruck aufgerufen, um den Wert von *ptr* ungültig zu erzeugen. Die Funktion lässt sich ersetzen, da das Programm eine Funktion mit dieser Funktionssignatur definieren kann, die die von der C++-Standardbibliothek definierte Standardversion ersetzt. Das erforderliche Verhalten besteht darin, einen Wert von *ptr* zu akzeptieren, der NULL ist oder durch einen früheren aufrufsoperator [New&#91;&#93;](../standard-library/new-operators.md#op_new_arr)(**size_t**) zurückgegeben wurde. Das Standardverhalten für einen NULL-Wert von *ptr* besteht darin, nichts zu tun. Jeder andere Wert von *ptr* muss ein Wert sein, der zuvor von einem-Befehl zurückgegeben wurde, wie zuvor beschrieben. Das Standardverhalten für einen solchen Wert, der nicht NULL *ist, besteht darin,* den Speicher freizugeben, der durch den vorherigen-Befehl reserviert wurde. Es wird nicht angegeben, unter welchen Bedingungen bzw. dem gesamten freigegebenen Speicher durch einen nachfolgenden aufrufdes [Operators new](../standard-library/new-operators.md#op_new)(**size_t**) oder eines beliebigen von `calloc` (**size_t**), `malloc` (**size_t**) oder `realloc` ( **`void`** <strong>\*</strong> , **size_t**) zugeordnet wird.

Die zweite Funktion wird von einem Platzierungs `delete[]` Ausdruck aufgerufen, der einem-Ausdruck in `new[]` der Form entspricht `new[]` (**Std:: size_t**). Dabei wird keine Aktion ausgeführt.

Die dritte Funktion wird durch einen Placement-delete-Ausdruck für einen entsprechenden `new[]`-Ausdruck der Form `new[]`( **std::size_t**, **const std::nothrow_t&**) aufgerufen. Das Programm kann eine Funktion mit dieser Funktionssignatur definieren, die die von der C++-Standardbibliothek definierte Standardversion ersetzt. Das erforderliche Verhalten besteht darin, einen Wert von *ptr* zu akzeptieren, der NULL ist oder durch einen früheren Operator `new[]` (**size_t**) zurückgegeben wurde. Standardmäßig wird `delete[]`( `ptr`) ausgewertet.

### <a name="example"></a>Beispiel

Unter [operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr) finden Sie Beispiele für die Verwendung von `operator delete[]`.

## <a name="operator-new"></a><a name="op_new"></a>New-Operator

Die Funktion, die durch einen new-Ausdruck aufgerufen wird, um Speicher für einzelne Objekte zu belegen.

```cpp
void* operator new(std::size_t count) throw(bad_alloc);
void* operator new(std::size_t count, const std::nothrow_t&) throw();
void* operator new(std::size_t count, void* ptr) throw();
```

### <a name="parameters"></a>Parameter

*Countdown*\
Der zu belegende Speicherplatz in Bytes.

*PTR*\
Der Zeiger, der zurückgegeben werden soll.

### <a name="return-value"></a>Rückgabewert

Entweder ein Zeiger auf die niedrigste Byteadresse des neu belegten Speichers Oder *ptr*.

### <a name="remarks"></a>Bemerkungen

Die erste Funktion wird durch einen new-Ausdruck aufgerufen, um genau auf alle Objekte dieser Größe ausgerichtete `count`-Bytes im Speicher zu belegen. Die Funktion lässt sich ersetzen, da das Programm eine Funktion mit dieser Funktionssignatur definieren kann, die die von der C++-Standardbibliothek definierte Standardversion ersetzt.

Das erforderliche Verhalten besteht darin, nur dann einen nicht-NULL-Zeiger zurückzugeben, wenn der Speicher wie angefordert zugewiesen werden kann. Alle Zuordnungen dieser Art geben einen Zeiger auf Speicherplatz aus, der nicht mit belegtem Speicherplatz zusammenhängt. Reihenfolge und Kontinuität von durch aufeinanderfolgende Aufrufe belegtem Speicherplatz werden nicht angegeben. Auch der anfänglich gespeicherte Wert wird nicht angegeben. Der zurückgegebene Zeiger verweist auf den Anfang (niedrigste Byteadresse) des belegten Speicherplatzes. Wenn die Anzahl 0 (null) ist, entspricht der zurückgegebene Wert keinem der anderen Werte, die von der Funktion zurückgegeben wurden.

Standardmäßig wird eine Schleife ausgeführt. Innerhalb der Schleife versucht die Funktion zuerst den angeforderten Speicherplatz zu belegen. Es wird nicht angegeben, ob der Versuch einen Aufruf von `malloc`( **size_t**) umfasst. Wenn der Versuch erfolgreich ist, gibt die Funktion einen Zeiger auf den belegten Speicherplatz zurück. Ansonsten gibt die Funktion den festgelegten [new handler](../standard-library/new-typedefs.md#new_handler) zurück. Führt die aufgerufene Funktion eine Rückgabe aus, wird die Schleife wiederholt. Die Schleife wird beendet, wenn ein Versuch zur Belegung des angeforderten Speichers erfolgreich ist oder eine aufgerufene Funktion keine Rückgabe ausführt.

Als erforderliches Verhalten für einen neuen Handler ist eine der folgenden Operationen auszuführen:

- Stellt zusätzlichen Speicherplatz für die Zuordnung bereit und springt anschließend zurück.

- Ruft entweder `abort` oder auf `exit` .

- Lösen Sie ein Objekt vom Typ aus `bad_alloc` .

Standardmäßig wird für einen [new handler](../standard-library/new-typedefs.md#new_handler) ein Objekt des Typs `bad_alloc` ausgelöst. Ein NULL-Zeiger legt den neuen Standard-Handler fest.

Der von aufeinander folgenden Aufrufen an (size_t) zugeordnete Speicherbedarf und die zusammenhängende Zusammenstellung `operator new` ist nicht angegeben, wie die anfänglichen Werte, die dort gespeichert werden.**size_t**

Die zweite Funktion wird durch einen Placement-new-Ausdruck aufgerufen, um genau auf alle Objekte dieser Größe ausgerichtete `count`-Bytes im Speicher zu belegen. Die Funktion lässt sich ersetzen, da das Programm eine Funktion mit dieser Funktionssignatur definieren kann, die die von der C++-Standardbibliothek definierte Standardversion ersetzt.

Das Standardverhalten besteht darin, `operator new` ( `count` ) zurückzugeben, wenn diese Funktion erfolgreich ausgeführt wird. Ansonsten gibt sie einen NULL-Zeiger zurück.

Die dritte Funktion wird von einem Platzierungs **`new`** Ausdruck in der Form aufgerufen `new ( args ) T` . In diesem Fall besteht *args* aus einem einzelnen Objektzeiger. Dies kann sich beim Erstellen eines Objekts an einer bekannten Adresse als nützlich erweisen. Die Funktion gibt *ptr* zurück.

Um Speicher freizugeben, der von **Operator new**zugewiesen wird, nennen Sie [Operator Delete](../standard-library/new-operators.md#op_delete).

Informationen zum Auslösen oder nicht ausgelösten Verhalten von New finden Sie [unter den New-und DELETE-Operatoren](../cpp/new-and-delete-operators.md).

### <a name="example"></a>Beispiel

```cpp
// new_op_new.cpp
// compile with: /EHsc
#include<new>
#include<iostream>

using namespace std;

class MyClass
{
public:
   MyClass( )
   {
      cout << "Construction MyClass." << this << endl;
   };

   ~MyClass( )
   {
      imember = 0; cout << "Destructing MyClass." << this << endl;
   };
   int imember;
};

int main( )
{
   // The first form of new delete
   MyClass* fPtr = new MyClass;
   delete fPtr;

   // The second form of new delete
   MyClass* fPtr2 = new( nothrow ) MyClass;
   delete fPtr2;

   // The third form of new delete
   char x[sizeof( MyClass )];
   MyClass* fPtr3 = new( &x[0] ) MyClass;
   fPtr3 -> ~MyClass();
   cout << "The address of x[0] is : " << ( void* )&x[0] << endl;
}
```

## <a name="operator-new"></a><a name="op_new_arr"></a>New-Operator []

Die Zuordnungsfunktion, die durch einen new-Ausdruck aufgerufen wird, um Speicherplatz für ein Array von Objekten zu belegen.

```cpp
void* operator new[](std::size_t count) throw(std::bad_alloc);
void* operator new[](std::size_t count, const std::nothrow_t&) throw();
void* operator new[](std::size_t count, void* ptr) throw();
```

### <a name="parameters"></a>Parameter

*Countdown*\
Der Speicherplatz in Bytes, der für ein Array-Objekt belegt werden soll.

*PTR*\
Der Zeiger, der zurückgegeben werden soll.

### <a name="return-value"></a>Rückgabewert

Entweder ein Zeiger auf die niedrigste Byteadresse des neu belegten Speichers Oder *ptr*.

### <a name="remarks"></a>Bemerkungen

Die erste Funktion wird durch einen `new[]`-Ausdruck aufgerufen, um `count`-Bytes im Speicher zu belegen, die genau auf alle Array-Objekte ausgerichtet sind, die höchstens diese Größe aufweisen. Das Programm kann eine Funktion mit dieser Funktionssignatur definieren, die die von der C++-Standardbibliothek definierte Standardversion ersetzt. Das erforderliche Verhalten ist das gleiche wie bei [New-Operator](../standard-library/new-operators.md#op_new)(**size_t**). Standardmäßig wird `operator new`( `count`) zurückgegeben.

Die zweite Funktion wird durch einen Placement-`new[]`-Ausdruck aufgerufen, um genau auf alle Objekte dieser Größe ausgerichtete `count`-Bytes im Speicher zu belegen. Das Programm kann eine Funktion mit dieser Funktionssignatur definieren, die die von der C++-Standardbibliothek definierte Standardversion ersetzt. Das Standardverhalten ist die Rückgabe von **operatornew**( `count` ), wenn diese Funktion erfolgreich ausgeführt wird. Ansonsten gibt sie einen NULL-Zeiger zurück.

Die dritte Funktion wird von einem Platzierungs `new[]` Ausdruck in der Form **`new`** ( *args*) **T**[ **N**] aufgerufen. In diesem Fall besteht *args* aus einem einzelnen Objektzeiger. Die Funktion gibt `ptr` zurück.

Rufen Sie [operator delete&#91;&#93;](../standard-library/new-operators.md#op_delete_arr) auf, um durch `operator new[]` belegten Speicherplatz freizugeben.

Informationen zum Auslöseverhalten von „new“ finden Sie unter [new-Operator und delete-Operator](../cpp/new-and-delete-operators.md).

### <a name="example"></a>Beispiel

```cpp
// new_op_alloc.cpp
// compile with: /EHsc
#include <new>
#include <iostream>

using namespace std;

class MyClass {
public:
   MyClass() {
      cout << "Construction MyClass." << this << endl;
   };

   ~MyClass() {
      imember = 0; cout << "Destructing MyClass." << this << endl;
      };
   int imember;
};

int main() {
   // The first form of new delete
   MyClass* fPtr = new MyClass[2];
   delete[ ] fPtr;

   // The second form of new delete
   char x[2 * sizeof( MyClass ) + sizeof(int)];

   MyClass* fPtr2 = new( &x[0] ) MyClass[2];
   fPtr2[1].~MyClass();
   fPtr2[0].~MyClass();
   cout << "The address of x[0] is : " << ( void* )&x[0] << endl;

   // The third form of new delete
   MyClass* fPtr3 = new( nothrow ) MyClass[2];
   delete[ ] fPtr3;
}
```
