---
title: '&lt;neuer&gt; Operatoren und-aufumstellungs'
ms.date: 11/04/2016
f1_keywords:
- new/std::operator delete
- new/std::operator new
ms.assetid: d1af4b56-9a95-4c65-ab01-bf43e982c7bd
ms.openlocfilehash: a3fd5b825fe1eaf3a07d9d001f03b9d0c64ffa31
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425370"
---
# <a name="ltnewgt-operators-and-enums"></a>&lt;neuer&gt; Operatoren und-aufumstellungs

## <a name="op_align_val_t"></a>Aufzählungs align_val_t

```cpp
enum class align_val_t : size_t {};
```

## <a name="op_delete"></a>Operator löschen

Die Funktion, die von einem DELETE-Ausdruck aufgerufen wird, um Speicher für einzelne Objekte zuzuweisen.

```cpp
void operator delete(void* ptr) throw();
void operator delete(void *, void*) throw();
void operator delete(void* ptr, const std::nothrow_t&) throw();
```

### <a name="parameters"></a>Parameter

*ptr* -\
Der Zeiger, dessen Wert durch den Löschvorgang als ungültig gerendert werden soll.

### <a name="remarks"></a>Hinweise

Die erste Funktion wird von einem DELETE-Ausdruck aufgerufen, um den Wert von *ptr* ungültig zu erzeugen. Das Programm kann eine Funktion mit dieser Funktionssignatur definieren, die die von der C++-Standardbibliothek definierte Standardversion ersetzt. Das erforderliche Verhalten besteht darin, einen Wert von *ptr* zu akzeptieren, der NULL ist oder durch einen früheren- [Operator new](../standard-library/new-operators.md#op_new)(**size_t**) zurückgegeben wurde.

Das Standardverhalten für einen NULL-Wert von *ptr* besteht darin, nichts zu tun. Jeder andere Wert von *ptr* muss ein Wert sein, der zuvor von einem-Befehl zurückgegeben wurde, wie zuvor beschrieben. Das Standardverhalten für einen solchen Wert, der nicht *NULL ist, besteht darin,* den Speicher freizugeben, der durch den vorherigen-Befehl reserviert wurde. Es wird nicht angegeben, unter welchen Bedingungen oder der gesamte freigegebene Speicherung durch einen nachfolgenden `operator new`(**size_t**) oder einen `calloc`( **size_t**), `malloc`( **size_t**) oder `realloc`( **void** <strong>\*</strong>, **size_t**) zugeordnet wird.

Die zweite Funktion wird durch einen Placement-delete-Ausdruck für einen entsprechenden new-Ausdruck der Form **new**( **std:: size_t**) aufgerufen. Dabei wird keine Aktion ausgeführt.

Die dritte Funktion wird durch einen Placement-delete-Ausdruck für einen entsprechenden new-Ausdruck der Form **new**( **std::size_t**, **conststd::nothrow_t&** ) aufgerufen. Das Programm kann eine Funktion mit dieser Funktionssignatur definieren, die die von der C++-Standardbibliothek definierte Standardversion ersetzt. Als erforderliches Verhalten soll ein Wert von `ptr` akzeptiert werden, der gleich 0 (null) ist oder durch einen früheren Aufruf von `operator new`( **size_t**). zurückgegeben wurde. Das Standardverhalten ist die Auswertung von **Delete**(`ptr`).

### <a name="example"></a>Beispiel

Unter [Operator new](../standard-library/new-operators.md#op_new) finden Sie ein Beispiel für die Verwendung von **Operator Delete**.

## <a name="op_delete_arr"></a>Delete-Operator []

Die Funktion, die durch einen Löschausdruck (delete-Ausdruck) aufgerufen wird, um Speicher für ein Array von Objekten freizugeben.

```cpp
void operator delete[](void* ptr) throw();
void operator delete[](void *, void*) throw();
void operator delete[](void* ptr, const std::nothrow_t&) throw();
```

### <a name="parameters"></a>Parameter

*ptr* -\
Der Zeiger, dessen Wert durch den Löschvorgang als ungültig gerendert werden soll.

### <a name="remarks"></a>Hinweise

Die erste Funktion wird von einem `delete[]` Ausdruck aufgerufen, um den Wert von *ptr* ungültig zu erzeugen. Die Funktion lässt sich ersetzen, da das Programm eine Funktion mit dieser Funktionssignatur definieren kann, die die von der C++-Standardbibliothek definierte Standardversion ersetzt. Das erforderliche Verhalten besteht darin, einen Wert von *ptr* zu akzeptieren, der NULL ist oder durch einen früheren- [Operator&#91;New](../standard-library/new-operators.md#op_new_arr)(**size_t**) zurückgegeben wurde. Das Standardverhalten für einen NULL-Wert von *ptr* besteht darin, nichts zu tun. Jeder andere Wert von *ptr* muss ein Wert sein, der zuvor von einem-Befehl zurückgegeben wurde, wie zuvor beschrieben. Das Standardverhalten für einen solchen Wert, der nicht NULL *ist, besteht darin,* den Speicher freizugeben, der durch den vorherigen-Befehl reserviert wurde. Es wird nicht angegeben, unter welchen Bedingungen oder der gesamte freigegebene Speicher durch einen nachfolgenden [Operator new](../standard-library/new-operators.md#op_new)(**size_t**) oder einen beliebigen `calloc`(**size_t**), `malloc`(**size_t**) oder `realloc`( **void** <strong>\*</strong>, **size_t**) zugeordnet wird.

Die zweite Funktion wird von einem Platzierungs `delete[]` Ausdruck aufgerufen, der einem `new[]` Ausdruck der Form `new[]`(**Std:: size_t**) entspricht. Dabei wird keine Aktion ausgeführt.

Die dritte Funktion wird durch einen Placement-delete-Ausdruck für einen entsprechenden `new[]`-Ausdruck der Form `new[]`( **std::size_t**, **const std::nothrow_t&** ) aufgerufen. Das Programm kann eine Funktion mit dieser Funktionssignatur definieren, die die von der C++-Standardbibliothek definierte Standardversion ersetzt. Das erforderliche Verhalten besteht darin, einen Wert von *ptr* zu akzeptieren, der NULL ist oder durch einen früheren Operator `new[]`(**size_t**) zurückgegeben wurde. Standardmäßig wird `delete[]`( `ptr`) ausgewertet.

### <a name="example"></a>Beispiel

Unter [operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr) finden Sie Beispiele für die Verwendung von `operator delete[]`.

## <a name="op_new"></a>New-Operator

Die Funktion, die durch einen new-Ausdruck aufgerufen wird, um Speicher für einzelne Objekte zu belegen.

```cpp
void* operator new(std::size_t count) throw(bad_alloc);
void* operator new(std::size_t count, const std::nothrow_t&) throw();
void* operator new(std::size_t count, void* ptr) throw();
```

### <a name="parameters"></a>Parameter

*Anzahl*\
Der zu belegende Speicherplatz in Bytes.

*ptr* -\
Der Zeiger, der zurückgegeben werden soll.

### <a name="return-value"></a>Rückgabewert

Entweder ein Zeiger auf die niedrigste Byteadresse des neu belegten Speichers Oder *ptr*.

### <a name="remarks"></a>Hinweise

Die erste Funktion wird durch einen new-Ausdruck aufgerufen, um genau auf alle Objekte dieser Größe ausgerichtete `count`-Bytes im Speicher zu belegen. Die Funktion lässt sich ersetzen, da das Programm eine Funktion mit dieser Funktionssignatur definieren kann, die die von der C++-Standardbibliothek definierte Standardversion ersetzt.

Als erforderliches Verhalten wird ein nicht-NULL-Zeiger nur dann zurückgegeben, wenn Speicherplatz wie gewünscht belegt werden kann. Alle Zuordnungen dieser Art geben einen Zeiger auf Speicherplatz aus, der nicht mit belegtem Speicherplatz zusammenhängt. Reihenfolge und Kontinuität von durch aufeinanderfolgende Aufrufe belegtem Speicherplatz werden nicht angegeben. Auch der anfänglich gespeicherte Wert wird nicht angegeben. Der zurückgegebene Zeiger verweist auf den Anfang (niedrigste Byteadresse) des belegten Speicherplatzes. Wenn die Anzahl 0 (null) ist, entspricht der zurückgegebene Wert keinem der anderen Werte, die von der Funktion zurückgegeben wurden.

Standardmäßig wird eine Schleife ausgeführt. Innerhalb der Schleife versucht die Funktion zuerst den angeforderten Speicherplatz zu belegen. Es wird nicht angegeben, ob der Versuch einen Aufruf von `malloc`( **size_t**) umfasst. Wenn der Versuch erfolgreich ist, gibt die Funktion einen Zeiger auf den belegten Speicherplatz zurück. Ansonsten gibt die Funktion den festgelegten [new handler](../standard-library/new-typedefs.md#new_handler) zurück. Führt die aufgerufene Funktion eine Rückgabe aus, wird die Schleife wiederholt. Die Schleife wird beendet, wenn ein Versuch zur Belegung des angeforderten Speichers erfolgreich ist oder eine aufgerufene Funktion keine Rückgabe ausführt.

Als erforderliches Verhalten für einen neuen Handler ist eine der folgenden Operationen auszuführen:

- Stellt zusätzlichen Speicherplatz für die Zuordnung bereit und springt anschließend zurück.

- Ruft entweder **Abbruch** oder **Exit**(`int`) auf.

- Löst ein Objekt des Typs **bad_alloc** aus.

Standardmäßig wird für einen [new handler](../standard-library/new-typedefs.md#new_handler) ein Objekt des Typs `bad_alloc` ausgelöst. Ein NULL-Zeiger legt den neuen Standard-Handler fest.

Die Reihenfolge und zusammen hängigkeit des Speichers, der durch aufeinander folgende Aufrufe an `operator new`(**size_t**) belegt wird, ist nicht angegeben, wie die anfänglichen Werte, die dort gespeichert werden.

Die zweite Funktion wird durch einen Placement-new-Ausdruck aufgerufen, um genau auf alle Objekte dieser Größe ausgerichtete `count`-Bytes im Speicher zu belegen. Die Funktion lässt sich ersetzen, da das Programm eine Funktion mit dieser Funktionssignatur definieren kann, die die von der C++-Standardbibliothek definierte Standardversion ersetzt.

Standardmäßig wird `operator new`(`count`) zurückgegeben, wenn diese Funktion erfolgreich ausgeführt wird. Ansonsten gibt sie einen NULL-Zeiger zurück.

Die dritte Funktion wird durch einen Placement-**new**-Ausdruck der Form **new** ( *args*) T aufgerufen. In diesem Fall besteht *args* aus einem einzelnen Objektzeiger. Dies kann sich beim Erstellen eines Objekts an einer bekannten Adresse als nützlich erweisen. Die Funktion gibt *ptr* zurück.

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

## <a name="op_new_arr"></a>New-Operator []

Die Zuordnungsfunktion, die durch einen new-Ausdruck aufgerufen wird, um Speicherplatz für ein Array von Objekten zu belegen.

```cpp
void* operator new[](std::size_t count) throw(std::bad_alloc);
void* operator new[](std::size_t count, const std::nothrow_t&) throw();
void* operator new[](std::size_t count, void* ptr) throw();
```

### <a name="parameters"></a>Parameter

*Anzahl*\
Der Speicherplatz in Bytes, der für ein Array-Objekt belegt werden soll.

*ptr* -\
Der Zeiger, der zurückgegeben werden soll.

### <a name="return-value"></a>Rückgabewert

Entweder ein Zeiger auf die niedrigste Byteadresse des neu belegten Speichers Oder *ptr*.

### <a name="remarks"></a>Hinweise

Die erste Funktion wird durch einen `new[]`-Ausdruck aufgerufen, um `count`-Bytes im Speicher zu belegen, die genau auf alle Array-Objekte ausgerichtet sind, die höchstens diese Größe aufweisen. Das Programm kann eine Funktion mit dieser Funktionssignatur definieren, die die von der C++-Standardbibliothek definierte Standardversion ersetzt. Das erforderliche Verhalten ist das gleiche wie bei [New-Operator](../standard-library/new-operators.md#op_new)(**size_t**). Standardmäßig wird `operator new`( `count`) zurückgegeben.

Die zweite Funktion wird durch einen Placement-`new[]`-Ausdruck aufgerufen, um genau auf alle Objekte dieser Größe ausgerichtete `count`-Bytes im Speicher zu belegen. Das Programm kann eine Funktion mit dieser Funktionssignatur definieren, die die von der C++-Standardbibliothek definierte Standardversion ersetzt. Das Standardverhalten ist die Rückgabe von **operatornew**(`count`), wenn diese Funktion erfolgreich ausgeführt wird. Ansonsten gibt sie einen NULL-Zeiger zurück.

Die dritte Funktion wird durch einen Placement-`new[]`-Ausdruck der Form **new** ( *args*) **T**[ **N**] aufgerufen. In diesem Fall besteht *args* aus einem einzelnen Objektzeiger. Die Funktion gibt `ptr`zurück.

Rufen Sie `operator new[]`operator delete&#91;&#93;[ auf, um durch ](../standard-library/new-operators.md#op_delete_arr) belegten Speicherplatz freizugeben.

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
