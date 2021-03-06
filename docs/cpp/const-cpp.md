---
title: const (C++)
ms.date: 11/04/2016
f1_keywords:
- const_cpp
helpviewer_keywords:
- const keyword [C++]
ms.assetid: b21c0271-1ad0-40a0-b21c-5e812bba0318
ms.openlocfilehash: db79e228f1fabc4b2da0a7778126a1b576a67768
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229037"
---
# <a name="const-c"></a>const (C++)

Beim Ändern einer Daten Deklaration **`const`** gibt das Schlüsselwort an, dass das Objekt oder die Variable nicht geändert werden kann.

## <a name="syntax"></a>Syntax

```
const declaration ;
member-function const ;
```

## <a name="const-values"></a>Konstante Werte

Das **`const`** Schlüsselwort gibt an, dass der Wert einer Variablen konstant ist, und weist den Compiler an, den Programmierer daran zu hindern, ihn zu ändern.

```cpp
// constant_values1.cpp
int main() {
   const int i = 5;
   i = 10;   // C3892
   i++;   // C2105
}
```

In C++ können Sie das- **`const`** Schlüsselwort anstelle der [#define](../preprocessor/hash-define-directive-c-cpp.md) Präprozessordirektive verwenden, um konstante Werte zu definieren. Werte **`const`** , die mit definiert werden, unterliegen der Typüberprüfung und können anstelle konstanter Ausdrücke verwendet werden. In C++ können Sie die Größe eines Arrays mit einer **`const`** Variablen wie folgt angeben:

```cpp
// constant_values2.cpp
// compile with: /c
const int maxarray = 255;
char store_char[maxarray];  // allowed in C++; not allowed in C
```

In C erhalten konstante Werte standardmäßig den Wert einer externen Bindung. Daher können sie nur in den Quelldateien stehen. In C++ erhalten konstante Werte standardmäßig den Wert einer internen Bindung, daher können sie in den Headerdateien angezeigt werden.

Das- **`const`** Schlüsselwort kann auch in Zeiger Deklarationen verwendet werden.

```cpp
// constant_values3.cpp
int main() {
   char *mybuf = 0, *yourbuf;
   char *const aptr = mybuf;
   *aptr = 'a';   // OK
   aptr = yourbuf;   // C3892
}
```

Ein Zeiger auf eine Variable, die als deklariert wurde, **`const`** kann nur einem Zeiger zugewiesen werden, der auch als deklariert ist **`const`** .

```cpp
// constant_values4.cpp
#include <stdio.h>
int main() {
   const char *mybuf = "test";
   char *yourbuf = "test2";
   printf_s("%s\n", mybuf);

   const char *bptr = mybuf;   // Pointer to constant data
   printf_s("%s\n", bptr);

   // *bptr = 'a';   // Error
}
```

Sie können Zeiger auf konstante Daten als Funktionsparameter verwenden, um zu verhindern, dass die Funktion einen Parameter ändert, der über einen Zeiger übergeben wird.

Bei Objekten, die als deklariert werden **`const`** , können Sie nur konstante Element Funktionen aufzurufen. Dadurch wird sichergestellt, dass das konstante Objekt nie geändert wird.

```cpp
birthday.getMonth();    // Okay
birthday.setMonth( 4 ); // Error
```

Sie können für ein nicht konstantes Objekt konstante oder nicht konstante Memberfunktionen aufrufen. Sie können eine Element Funktion auch mithilfe des **`const`** Schlüssel Worts überladen. Dadurch kann eine andere Version der Funktion für konstante und nicht konstante Objekte aufgerufen werden.

Sie können keine Konstruktoren oder Dekonstruktoren mit dem- **`const`** Schlüsselwort deklarieren.

## <a name="const-member-functions"></a>Konstante Memberfunktionen

Das Deklarieren einer Member-Funktion mit dem- **`const`** Schlüsselwort gibt an, dass es sich bei der Funktion um eine schreibgeschützte Funktion handelt, die das Objekt, für das Sie aufgerufen wird, nicht ändert. Eine Konstante Member-Funktion kann keine nicht statischen Datenmember ändern oder keine Element Funktionen aufzurufen, die nicht konstant sind. Um eine Konstante Member-Funktion zu deklarieren, platzieren Sie das- **`const`** Schlüsselwort nach der schließenden Klammer der Argumentliste. Das **`const`** Schlüsselwort ist sowohl in der Deklaration als auch in der Definition erforderlich.

```cpp
// constant_member_function.cpp
class Date
{
public:
   Date( int mn, int dy, int yr );
   int getMonth() const;     // A read-only function
   void setMonth( int mn );   // A write function; can't be const
private:
   int month;
};

int Date::getMonth() const
{
   return month;        // Doesn't modify anything
}
void Date::setMonth( int mn )
{
   month = mn;          // Modifies data member
}
int main()
{
   Date MyDate( 7, 4, 1998 );
   const Date BirthDate( 1, 18, 1953 );
   MyDate.setMonth( 4 );    // Okay
   BirthDate.getMonth();    // Okay
   BirthDate.setMonth( 4 ); // C2662 Error
}
```

## <a name="c-and-c-const-differences"></a>C-und C++-Konstanten Unterschiede

Wenn Sie eine Variable als **`const`** in einer C-Quell Code Datei deklarieren, gehen Sie wie folgt vor:

```cpp
const int i = 2;
```

Sie können diese Variable dann in einem anderen Modul wie folgt verwenden:

```cpp
extern const int i;
```

Um jedoch das gleiche Verhalten in C++ zu erzielen, müssen Sie die **`const`** Variable wie folgt deklarieren:

```cpp
extern const int i = 2;
```

Wenn Sie eine **`extern`** Variable in einer C++-Quell Code Datei für die Verwendung in einer C-Quell Code Datei deklarieren möchten, verwenden Sie Folgendes:

```cpp
extern "C" const int x=10;
```

um die Namenszerlegung durch den C++-Compiler zu verhindern.

## <a name="remarks"></a>Bemerkungen

Beim Befolgen der Parameterliste einer Element Funktion gibt das- **`const`** Schlüsselwort an, dass die Funktion das Objekt, für das Sie aufgerufen wird, nicht ändert.

Weitere Informationen zu finden Sie in **`const`** den folgenden Themen:

- [Konstante und flüchtige Zeiger](../cpp/const-and-volatile-pointers.md)

- [Typqualifizierer (C-Programmiersprachenreferenz)](../c-language/type-qualifiers.md)

- [volatile](../cpp/volatile-cpp.md)

- [#define](../preprocessor/hash-define-directive-c-cpp.md)

## <a name="see-also"></a>Siehe auch

[Schlüsselwörter](../cpp/keywords-cpp.md)
