---
title: Aliase und Typedefs (C++)
ms.date: 11/04/2016
f1_keywords:
- typedef_cpp
ms.assetid: af1c24d2-4bfd-408a-acfc-482e264232f5
ms.openlocfilehash: 7a45c4570341aca056b9d4c30ea496317a1ac96f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181563"
---
# <a name="aliases-and-typedefs-c"></a>Aliase und Typedefs (C++)

Sie können eine *Alias Deklaration* verwenden, um einen Namen zu deklarieren, der als Synonym für einen zuvor deklarierten Typ verwendet werden soll. (Dieser Mechanismus wird auch als *Typalias*bezeichnet). Sie können diesen Mechanismus auch verwenden, um eine *Alias Vorlage*zu erstellen, die besonders für benutzerdefinierte Zuweisungen nützlich sein kann.

## <a name="syntax"></a>Syntax

```
using identifier = type;
```

## <a name="remarks"></a>Bemerkungen

*identifier*<br/>
Die Bezeichnung des Alias.

*type*<br/>
Der Typbezeichner, für den Sie einen Alias erstellen.

Ein Alias führt keinen neuen Typ ein und kann die Bedeutung eines vorhandenen Typnamens nicht ändern.

Die einfachste Form eines Alias entspricht dem **typedef** -Mechanismus von c++ 03:

```cpp
// C++11
using counter = long;

// C++03 equivalent:
// typedef long counter;
```

Beides ermöglicht die Erstellung von Variablen des Typs "counter". Nützlicherer wäre ein Typalias wie dieser für `std::ios_base::fmtflags`:

```cpp
// C++11
using fmtfl = std::ios_base::fmtflags;

// C++03 equivalent:
// typedef std::ios_base::fmtflags fmtfl;

fmtfl fl_orig = std::cout.flags();
fmtfl fl_hex = (fl_orig & ~std::cout.basefield) | std::cout.showbase | std::cout.hex;
// ...
std::cout.flags(fl_hex);
```

Aliase funktionieren auch mit Funktions Zeigern, sind aber viel besser lesbar als die entsprechende typedef:

```cpp
// C++11
using func = void(*)(int);

// C++03 equivalent:
// typedef void (*func)(int);

// func can be assigned to a function pointer value
void actual_function(int arg) { /* some code */ }
func fptr = &actual_function;
```

Eine Einschränkung des **typedef** -Mechanismus besteht darin, dass er nicht mit Vorlagen funktioniert. Die Typaliassyntax in C++11 ermöglicht jedoch die Erstellung von Aliasvorlagen:

```cpp
template<typename T> using ptr = T*;

// the name 'ptr<T>' is now an alias for pointer to T
ptr<int> ptr_int;
```

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt die Verwendung einer Aliasvorlage mit einer benutzerdefinierten Zuweisung, in diesem Fall einem ganzzahligen Vektortyp. Sie können einen beliebigen Typ für **int** ersetzen, um einen praktischen Alias zum Ausblenden der komplexen Parameterlisten im Haupt Funktionscode zu erstellen. Indem Sie die benutzerdefinierte Zuordnung im gesamten Code verwenden, können Sie die Lesbarkeit verbessern und das Risiko von Fehlern verringern, die sich aufgrund von Schreibfehlern einschleichen können.

```cpp
#include <stdlib.h>
#include <new>

template <typename T> struct MyAlloc {
    typedef T value_type;

    MyAlloc() { }
    template <typename U> MyAlloc(const MyAlloc<U>&) { }

    bool operator==(const MyAlloc&) const { return true; }
    bool operator!=(const MyAlloc&) const { return false; }

    T * allocate(const size_t n) const {
        if (n == 0) {
            return nullptr;
        }

        if (n > static_cast<size_t>(-1) / sizeof(T)) {
            throw std::bad_array_new_length();
        }

        void * const pv = malloc(n * sizeof(T));

        if (!pv) {
            throw std::bad_alloc();
        }

        return static_cast<T *>(pv);
    }

    void deallocate(T * const p, size_t) const {
        free(p);
    }
};

#include <vector>
using MyIntVector = std::vector<int, MyAlloc<int>>;

#include <iostream>

int main ()
{
    MyIntVector foov = { 1701, 1764, 1664 };

    for (auto a: foov) std::cout << a << " ";
    std::cout << "\n";

    return 0;
}
```

```Output
1701 1764 1664
```

## <a name="typedefs"></a>TypeDefs

Eine **typedef** -Deklaration führt einen Namen ein, der innerhalb des Gültigkeits Bereichs zu einem Synonym für den Typ wird, der durch den *Type-Declaration-* Teil der Deklaration angegeben wird.

Sie können typedef-Deklarationen verwenden, um kürzere oder aussagekräftigere Namen für Typen zu erstellen, die bereits von der Programmiersprache definiert sind, oder für Typen, die deklariert wurden. Mithilfe von typedef-Namen können Sie die Implementierungsdetails kapseln, die sich möglicherweise ändern.

Im Gegensatz zu den **Klassen**-, **Struktur**-, **Union**-und Enumerationsdeklarationen führen **typedef** - **Deklarationen keine** neuen Typen ein – Sie führen neue Namen für vorhandene Typen ein.

Mit **typedef** deklarierte Namen belegen denselben Namespace wie andere Bezeichner (außer Anweisungs Bezeichnungen). Deshalb können sie nicht den gleichen Bezeichner wie ein zuvor deklarierter Name verwenden. Nur in einer Klassentypdeklaration ist dies möglich. Betrachten Sie das folgenden Beispiel:

```cpp
// typedef_names1.cpp
// C2377 expected
typedef unsigned long UL;   // Declare a typedef name, UL.
int UL;                     // C2377: redefined.
```

Die Regeln zum Ausblenden von Namen, die andere Bezeichner betreffen, Steuern auch die Sichtbarkeit von Namen, die mithilfe von **typedef**deklariert wurden. Deshalb ist das folgenden Beispiel in C++ zulässig:

```cpp
// typedef_names2.cpp
typedef unsigned long UL;   // Declare a typedef name, UL
int main()
{
   unsigned int UL;   // Redeclaration hides typedef name
}

// typedef UL back in scope
```

```cpp
// typedef_specifier1.cpp
typedef char FlagType;

int main()
{
}

void myproc( int )
{
    int FlagType;
}
```

Wenn ein Bezeichner für den lokalen Gültigkeitsbereich mit dem gleichen Namen wie eine typedef deklariert wird oder wenn ein Member einer Struktur oder Union im gleichen Gültigkeitsbereich oder im inneren Bereich deklariert wird, muss der Typspezifizierer angegeben werden. Beispiel:

```cpp
typedef char FlagType;
const FlagType x;
```

Um den `FlagType`-Namen für einen Bezeichner, einen Strukturmember oder einen Unionsmember wiederzuverwenden, muss der Typ angegeben werden:

```cpp
const int FlagType;  // Type specifier required
```

Folgendes ist nicht ausreichend:

```cpp
const FlagType;      // Incomplete specification
```

Das liegt daran, dass `FlagType` als ein Teil des Typs angesehen wird, und nicht als Bezeichner, der neu deklariert wird. Diese Deklaration wird als ungültige Deklaration angesehen, wie etwa

```cpp
int;  // Illegal declaration
```

Sie können einen beliebigen Typ mit typedef deklarieren, einschließlich Zeiger-, Funktions- und Arraytypen. Sie können einen typedef-Namen für einen Zeiger auf einen Struktur- oder einen Union-Typ deklarieren, bevor Sie den Struktur- oder Union-Typ definieren, solange die Definition die gleiche Sichtbarkeit wie die Deklaration aufweist.

### <a name="examples"></a>Beispiele

Eine Verwendung von **typedef** -Deklarationen besteht darin, Deklarationen einheitlicher und kompakter zu gestalten. Beispiel:

```cpp
typedef char CHAR;          // Character type.
typedef CHAR * PSTR;        // Pointer to a string (char *).
PSTR strchr( PSTR source, CHAR target );
typedef unsigned long ulong;
ulong ul;     // Equivalent to "unsigned long ul;"
```

Wenn Sie **typedef** verwenden möchten, um grundlegende und abgeleitete Typen in der gleichen Deklaration anzugeben, können Sie Deklaratoren durch Kommas trennen. Beispiel:

```cpp
typedef char CHAR, *PSTR;
```

Im folgenden Beispiel wird der Typ `DRAWF` für eine Funktion bereitgestellt, die keinen Wert zurückgibt und zwei int-Argumente akzeptiert:

```cpp
typedef void DRAWF( int, int );
```

Nach der obigen **typedef** -Anweisung wird die Deklaration

```cpp
DRAWF box;
```

dieser Deklaration:

```cpp
void box( int, int );
```

**typedef** wird häufig mit **struct** kombiniert, um benutzerdefinierte Typen zu deklarieren und zu benennen:

```cpp
// typedef_specifier2.cpp
#include <stdio.h>

typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;

int main()
{
    mystruct ms;
    ms.i = 10;
    ms.f = 0.99;
    printf_s("%d   %f\n", ms.i, ms.f);
}
```

```Output
10   0.990000
```

### <a name="re-declaration-of-typedefs"></a>Neudeklaration von Typdefinitionen

Die **typedef** -Deklaration kann verwendet werden, um denselben Namen erneut zu deklarieren, um auf denselben Typ zu verweisen. Beispiel:

```cpp
// FILE1.H
typedef char CHAR;

// FILE2.H
typedef char CHAR;

// PROG.CPP
#include "file1.h"
#include "file2.h"   // OK
```

Das Programm *Prog. Cpp* enthält zwei Header Dateien, von denen beide **typedef** -Deklarationen für den Namen `CHAR`enthalten. Solange die beiden Deklarationen auf denselben Typ verweisen, ist eine solche Neudeklaration zulässig.

Ein Name, der zuvor als anderer Typ deklariert wurde, kann nicht von einer **typedef** neu definiert werden. Wenn *File2. H* enthält

```cpp
// FILE2.H
typedef int CHAR;     // Error
```

, gibt der Compiler aufgrund des Versuchs, den Namen `CHAR` erneut zu deklarieren, um auf einen anderen Typ zu verweisen, einen Fehler aus. Dies erstreckt sich auf Konstrukte wie die Folgenden:

```cpp
typedef char CHAR;
typedef CHAR CHAR;      // OK: redeclared as same type

typedef union REGS      // OK: name REGS redeclared
{                       //  by typedef name with the
    struct wordregs x;  //  same meaning.
    struct byteregs h;
} REGS;
```

### <a name="typedefs-in-c-vs-c"></a>Typedefs in C++ vs. C

Die Verwendung des **typedef** -Spezifizierers mit Klassentypen wird größtenteils aufgrund der ANSI C-Übung zum Deklarieren unbenannter Strukturen in **typedef** -Deklarationen unterstützt. Zum Beispiel verwenden viele C-Programmierer Folgendes:

```cpp
// typedef_with_class_types1.cpp
// compile with: /c
typedef struct {   // Declare an unnamed structure and give it the
                   // typedef name POINT.
   unsigned x;
   unsigned y;
} POINT;
```

Der Vorteil einer solchen Deklaration ist, das Deklarationen wie folgt ermöglicht werden:

```cpp
POINT ptOrigin;
```

Anstelle von:

```cpp
struct point_t ptOrigin;
```

In C++unterscheidet sich der Unterschied zwischen **typedef** -Namen und Real-Typen (deklariert mit den Schlüsselwörtern **Class**, **struct**, **Union**und **Enumeration** ). Obwohl die C-Übung, eine namenlose Struktur in einer **typedef** -Anweisung zu deklarieren, weiterhin funktioniert, bietet Sie keine anzuzeigende Notations Vorteile wie in C.

```cpp
// typedef_with_class_types2.cpp
// compile with: /c /W1
typedef struct {
   int POINT();
   unsigned x;
   unsigned y;
} POINT;
```

Im vorangehenden Beispiel wird eine Klasse mit dem Namen `POINT` mithilfe der unbenannten **typedef** -Syntax deklariert. `POINT` wird als Klassenname behandelt. Es gelten jedoch folgende Einschränkungen für Namen, die auf diese Weise eingeführt werden:

- Der Name (das Synonym) kann nicht nach einem **Klassen**-, **Struktur**-oder **Union** -Präfix angezeigt werden.

- Der Name darf nicht als Konstruktor- oder Destruktorname innerhalb einer Klassendeklaration verwendet werden.

Zusammenfassend stellt diese Syntax keinen Mechanismus für die Vererbung, Konstruktion oder Löschung bereit.
