---
title: struct (C++)
ms.date: 11/04/2016
f1_keywords:
- struct_cpp
helpviewer_keywords:
- struct constructors
ms.assetid: 3c6ba273-e248-4ff1-8c69-d2abcf1263c6
ms.openlocfilehash: 5f247a99d3f04a15ebd54718a46dae8512a580d6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231116"
---
# <a name="struct-c"></a>struct (C++)

Das **`struct`** Schlüsselwort definiert einen Strukturtyp und/oder eine Variable eines Struktur Typs.

## <a name="syntax"></a>Syntax

```
[template-spec] struct [ms-decl-spec] [tag [: base-list ]]
{
   member-list
} [declarators];
[struct] tag declarators;
```

#### <a name="parameters"></a>Parameter

*Vorlagen Spezifikation*<br/>
Optionale Vorlagenspezifikationen. Weitere Informationen finden Sie unter [Vorlagen Spezifikationen](templates-cpp.md).

*struct*<br/>
Das **`struct`** Schlüsselwort.

*MS-decl-spec*<br/>
Optionale Speicherklassenspezifikation. Weitere Informationen finden Sie unter [__declspec](../cpp/declspec.md) -Schlüsselwort.

*Tag*<br/>
Der Typname, der für die Struktur angegeben wurde. Das Tag wird ein reserviertes Wort innerhalb des Gültigkeitsbereichs der Struktur. Das Tag ist optional. Wenn es nicht angegeben wird, wird eine anonyme Struktur definiert. Weitere Informationen finden Sie unter [Anonyme Klassentypen](../cpp/anonymous-class-types.md).

*base-list*<br/>
Optionale Liste von Klassen oder Strukturen, von denen diese Struktur ihre Member ableitet. Weitere Informationen finden Sie unter [Basisklassen](../cpp/base-classes.md) . Jedem Basisklassen-oder Struktur Namen kann ein Zugriffsspezifizierer ([Public](../cpp/public-cpp.md), [private](../cpp/private-cpp.md), [Protected](../cpp/protected-cpp.md)) und das [Virtual](../cpp/virtual-cpp.md) -Schlüsselwort vorangestellt werden. Weitere Informationen finden Sie in der Tabelle "Member-Access" unter [Steuern des Zugriffs auf Klassenmember](member-access-control-cpp.md) .

*Mitgliederliste*<br/>
Liste der Strukturmember. Weitere Informationen finden Sie unter [Übersicht über Klassenmember](../cpp/class-member-overview.md) . Der einzige Unterschied besteht darin, dass **`struct`** anstelle von verwendet wird **`class`** .

*Deklaratoren*<br/>
Deklaratorliste, die die Namen der Struktur angibt. Deklaratorlisten deklarieren eine oder mehrere Instanzen des Strukturtyps. Deklaratoren können Initialisiererlisten einschließen, wenn alle Datenmember der Struktur sind **`public`** . Initialisiererlisten werden in-Strukturen häufig angezeigt, da Datenmember **`public`** Standardmäßig sind.  Weitere Informationen finden Sie [unter Übersicht über Deklaratoren](../cpp/overview-of-declarators.md) .

## <a name="remarks"></a>Bemerkungen

Ein Strukturtyp ist ein benutzerdefinierter zusammengesetzter Typ. Er setzt sich aus Feldern oder Membern zusammen, die unterschiedliche Typen aufweisen können.

In C++ ist eine-Struktur dieselbe wie eine-Klasse, außer dass deren Member **`public`** Standardmäßig sind.

Informationen zu verwalteten Klassen und Strukturen in C++/CLI finden Sie unter [Klassen und Strukturen](../extensions/classes-and-structs-cpp-component-extensions.md).

## <a name="using-a-structure"></a>Verwenden einer Struktur

In C müssen Sie explizit das- **`struct`** Schlüsselwort verwenden, um eine-Struktur zu deklarieren. In C++ müssen Sie das-Schlüsselwort nicht verwenden, **`struct`** nachdem der Typ definiert wurde.

Sie können Variablen deklarieren, wenn der Strukturtyp so definiert wurde, dass mindestens ein durch Trennzeichen getrennter Variablenname zwischen schließender Klammer und Semikolon steht.

Strukturvariablen können initialisiert werden. Die Initialisierung für jede Variable muss in Klammern eingeschlossen sein.

Weitere Informationen finden Sie unter [Klasse](../cpp/class-cpp.md), [Union](../cpp/unions.md)und Enumeration [.](../cpp/enumerations-cpp.md)

## <a name="example"></a>Beispiel

```cpp
#include <iostream>
using namespace std;

struct PERSON {   // Declare PERSON struct type
    int age;   // Declare member types
    long ss;
    float weight;
    char name[25];
} family_member;   // Define object of type PERSON

struct CELL {   // Declare CELL bit field
    unsigned short character  : 8;  // 00000000 ????????
    unsigned short foreground : 3;  // 00000??? 00000000
    unsigned short intensity  : 1;  // 0000?000 00000000
    unsigned short background : 3;  // 0???0000 00000000
    unsigned short blink      : 1;  // ?0000000 00000000
} screen[25][80];       // Array of bit fields

int main() {
    struct PERSON sister;   // C style structure declaration
    PERSON brother;   // C++ style structure declaration
    sister.age = 13;   // assign values to members
    brother.age = 7;
    cout << "sister.age = " << sister.age << '\n';
    cout << "brother.age = " << brother.age << '\n';

    CELL my_cell;
    my_cell.character = 1;
    cout << "my_cell.character = " << my_cell.character;
}
// Output:
// sister.age = 13
// brother.age = 7
// my_cell.character = 1
```
