---
title: typeid-Operator
ms.date: 10/04/2019
helpviewer_keywords:
- typeid operator
ms.assetid: 8871cee6-d6b9-4301-a5cb-bf3dc9798d61
ms.openlocfilehash: e17b88d81d9987ec586401e025e108cfbe88cb3b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223523"
---
# <a name="typeid-operator"></a>typeid-Operator

## <a name="syntax"></a>Syntax

```
typeid(type-id)
typeid(expression)
```

## <a name="remarks"></a>Bemerkungen

Der- **`typeid`** Operator ermöglicht, dass der Typ eines Objekts zur Laufzeit bestimmt wird.

Das Ergebnis von **`typeid`** ist ein-Wert `const type_info&` . Der Wert ist ein Verweis auf ein- `type_info` Objekt, das entweder die *Type-ID* oder den Typ des *Ausdrucks*darstellt, je nachdem, welches Formular **`typeid`** verwendet wird. Weitere Informationen finden Sie unter [Type_info-Klasse](../cpp/type-info-class.md).

Der **`typeid`** Operator funktioniert nicht mit verwalteten Typen (abstrakte Deklaratoren oder Instanzen). Weitere Informationen zum Ermitteln der <xref:System.Type> eines angegebenen Typs finden Sie unter [typeid](../extensions/typeid-cpp-component-extensions.md).

Der- **`typeid`** Operator führt eine Lauf Zeit Überprüfung aus, wenn er auf einen l-Wert eines polymorphen Klassen Typs angewendet wird, wobei der tatsächliche Objekttyp nicht durch die bereitgestellten statischen Informationen bestimmt werden kann. Zu solchen Fällen zählen folgende:

- Ein Verweis auf eine Klasse

- Ein Zeiger, dereferenziert mit`*`

- Ein Index ( `[ ]` ). (Es ist nicht sicher, einen Index mit einem Zeiger auf einen polymorphen Typ zu verwenden.)

Wenn der *Ausdruck* auf einen Basis Klassentyp zeigt, aber das Objekt tatsächlich von einem Typ ist, der von dieser Basisklasse abgeleitet ist, `type_info` ist das Ergebnis ein Verweis auf die abgeleitete Klasse. Der *Ausdruck* muss auf einen polymorphen Typ (eine Klasse mit virtuellen Funktionen) zeigen. Andernfalls ist das Ergebnis der `type_info` für die statische-Klasse, auf die im *Ausdruck*verwiesen wird. Außerdem muss der Zeiger dereferenziert werden, damit das verwendete Objekt das Objekt ist, auf das es verweist. Wenn Sie den Zeiger nicht dereferenzieren, ist das Ergebnis der `type_info` für den Zeiger, nicht das, auf das er verweist. Beispiel:

```cpp
// expre_typeid_Operator.cpp
// compile with: /GR /EHsc
#include <iostream>
#include <typeinfo>

class Base {
public:
   virtual void vvfunc() {}
};

class Derived : public Base {};

using namespace std;
int main() {
   Derived* pd = new Derived;
   Base* pb = pd;
   cout << typeid( pb ).name() << endl;   //prints "class Base *"
   cout << typeid( *pb ).name() << endl;   //prints "class Derived"
   cout << typeid( pd ).name() << endl;   //prints "class Derived *"
   cout << typeid( *pd ).name() << endl;   //prints "class Derived"
   delete pd;
}
```

Wenn der *Ausdruck* einen Zeiger dereferenzieren und der Wert dieses Zeigers NULL ist, löst **`typeid`** eine [bad_typeid Ausnahme](../cpp/bad-typeid-exception.md)aus. Wenn der Zeiger nicht auf ein gültiges Objekt zeigt, wird eine- `__non_rtti_object` Ausnahme ausgelöst. Es zeigt an, dass versucht wurde, die rtti zu analysieren, die einen Fehler ausgelöst hat, da das Objekt irgendwie ungültig ist. (Z. b. ist dies ein fehlerhafter Zeiger, oder der Code wurde nicht mit [/gr](../build/reference/gr-enable-run-time-type-information.md)kompiliert).

Wenn der *Ausdruck* kein Zeiger und kein Verweis auf eine Basisklasse des Objekts ist, ist das Ergebnis ein `type_info` Verweis, der den statischen Typ des *Ausdrucks*darstellt. Der *statische Typ* eines Ausdrucks verweist auf den Typ eines Ausdrucks, der zum Zeitpunkt der Kompilierung bekannt ist. Die Ausführungssemantik wird ignoriert, wenn der statische Typ eines Ausdrucks bewertet wird. Außerdem werden wenn möglich Verweise ignoriert, wenn der statische Typ eines Ausdrucks bestimmt wird:

```cpp
// expre_typeid_Operator_2.cpp
#include <typeinfo>

int main()
{
   typeid(int) == typeid(int&); // evaluates to true
}
```

**`typeid`** kann in Vorlagen auch verwendet werden, um den Typ eines Vorlagen Parameters zu bestimmen:

```cpp
// expre_typeid_Operator_3.cpp
// compile with: /c
#include <typeinfo>
template < typename T >
T max( T arg1, T arg2 ) {
   cout << typeid( T ).name() << "s compared." << endl;
   return ( arg1 > arg2 ? arg1 : arg2 );
}
```

## <a name="see-also"></a>Siehe auch

[Lauf Zeittyp Informationen](../cpp/run-time-type-information.md)\
[Schlüsselwörter](../cpp/keywords-cpp.md)
