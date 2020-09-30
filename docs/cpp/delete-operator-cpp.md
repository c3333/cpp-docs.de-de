---
title: delete-Operator (C++)
ms.date: 08/12/2019
f1_keywords:
- delete_cpp
helpviewer_keywords:
- delete keyword [C++], syntax
- delete keyword [C++], deallocating objects
- delete keyword [C++]
ms.assetid: de39c900-3f57-489c-9598-dcb73c4b3930
ms.openlocfilehash: 8ce9b8e606d5bbc2051af76e6dc4ac1350ec81a6
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509140"
---
# <a name="delete-operator-c"></a>delete-Operator (C++)

Gibt einen Speicherblock frei.

## <a name="syntax"></a>Syntax

> [ `::` ] `delete` *Cast-Ausdruck*\
> [ `::` ] `delete []` *Cast-Ausdruck*

## <a name="remarks"></a>Bemerkungen

Das *Cast-Expression-* Argument muss ein Zeiger auf einen Speicherblock sein, der zuvor für ein Objekt zugeordnet wurde, das mit dem [New-Operator](../cpp/new-operator-cpp.md)erstellt wurde. Der **`delete`** -Operator hat ein Ergebnis vom Typ **`void`** und gibt daher keinen Wert zurück. Beispiel:

```cpp
CDialog* MyDialog = new CDialog;
// use MyDialog
delete MyDialog;
```

Die Verwendung **`delete`** von für einen Zeiger auf ein Objekt, das nicht mit zugeordnet ist, **`new`** liefert unvorhersehbare Ergebnisse Sie können jedoch **`delete`** auf einem Zeiger mit dem Wert 0 verwenden. Diese Bereitstellung bedeutet, dass, wenn bei **`new`** einem Fehler 0 zurückgibt, das Löschen des Ergebnisses eines fehlgeschlagenen **`new`** Vorgangs harmlos ist. Weitere Informationen finden Sie [unter den Operatoren "New" und "Delete](../cpp/new-and-delete-operators.md)".

Die **`new`** **`delete`** Operatoren und können auch für integrierte Typen, einschließlich Arrays, verwendet werden. Wenn `pointer` auf ein Array verweist, platzieren Sie leere Klammern ( `[]` ) vor `pointer` :

```cpp
int* set = new int[100];
//use set[]
delete [] set;
```

Die Verwendung des- **`delete`** Operators für ein Objekt hebt die Zuordnung des Arbeitsspeichers auf. Ein Programm, das einen Zeiger dereferenziert, nachdem das Objekt gelöscht wurde, kann zu unvorhersehbaren Ergebnissen führen oder abstürzen.

Wenn zum Aufheben der **`delete`** Zuordnung von Arbeitsspeicher für ein C++-Klassenobjekt verwendet wird, wird der Dekonstruktor des Objekts aufgerufen, bevor der Speicher des Objekts freigegeben wird (wenn das Objekt über einen Dekonstruktor verfügt).

Wenn der Operand für den **`delete`** Operator ein änderbarer l-Wert ist, ist der Wert nach dem Löschen des Objekts nicht definiert.

Wenn die Compileroption [/SDL (zusätzliche Sicherheitsüberprüfungen aktivieren)](../build/reference/sdl-enable-additional-security-checks.md) angegeben wird, wird der Operand für den **`delete`** Operator auf einen ungültigen Wert festgelegt, nachdem das Objekt gelöscht wurde.

## <a name="using-delete"></a>Verwenden von "delete"

Es gibt zwei syntaktische Varianten für den [Delete-Operator](../cpp/delete-operator-cpp.md): einen für einzelne Objekte und den anderen für Arrays von-Objekten. Das folgende Code Fragment zeigt, wie sich diese unterscheiden:

```cpp
// expre_Using_delete.cpp
struct UDType
{
};

int main()
{
   // Allocate a user-defined object, UDObject, and an object
   //  of type double on the free store using the
   //  new operator.
   UDType *UDObject = new UDType;
   double *dObject = new double;
   // Delete the two objects.
   delete UDObject;
   delete dObject;
   // Allocate an array of user-defined objects on the
   // free store using the new operator.
   UDType (*UDArr)[7] = new UDType[5][7];
   // Use the array syntax to delete the array of objects.
   delete [] UDArr;
}
```

Die folgenden beiden Fälle verursachen nicht definierte Ergebnisse: Verwenden der `delete []` Arrayform von Delete () für ein Objekt und Verwenden der nicht-Array-Form von DELETE für ein Array.

## <a name="example"></a>Beispiel

Beispiele für die Verwendung von **`delete`** finden Sie unter [New-Operator](../cpp/new-operator-cpp.md).

## <a name="how-delete-works"></a>Funktionsweise von „delete“

Der Delete-Operator Ruft den Funktions **Operator Delete**auf.

Für Objekte, die nicht den Klassentyp ([Klasse](../cpp/class-cpp.md), [Struktur](../cpp/struct-cpp.md)oder [Union](../cpp/unions.md)) haben, wird der globale Delete-Operator aufgerufen. Bei Objekten des Klassen Typs wird der Name der Funktion zum Aufheben der Zuordnung im globalen Gültigkeitsbereich aufgelöst, wenn der DELETE-Ausdruck mit dem unären Bereichs Auflösungs Operator ( `::` ) beginnt. Andernfalls ruft der delete-Operator den Destruktor für ein Objekt vor dem Freigeben des Speichers auf (wenn der Zeiger nicht NULL ist). Der delete-Operator kann auf Basis einer einzelnen Klasse definiert werden; wenn keine solche Definition für eine bestimmte Klasse vorliegt, wird der globale delete-Operator aufgerufen. Wenn der Löschausdruck verwendet wird, um ein Klassenobjekt freizugeben, dessen statischer Typ einen virtuellen Destruktor aufweist, wird die Funktion zum Aufheben der Zuordnung vom virtuellen Destruktor des dynamischen Typs des Objekts aufgelöst.

## <a name="see-also"></a>Weitere Informationen

[Ausdrücke mit unären Operatoren](../cpp/expressions-with-unary-operators.md)\
[Keywords](../cpp/keywords-cpp.md)\
[New-und DELETE-Operatoren](../cpp/new-and-delete-operators.md)
