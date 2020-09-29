---
title: class (C++)
ms.date: 11/04/2016
f1_keywords:
- class_cpp
helpviewer_keywords:
- class types [C++], class statements
- class keyword [C++]
ms.assetid: dd23c09f-6598-4069-8bff-69c7f2518b9f
ms.openlocfilehash: 1dfa0b5e2dd65567b965be756ff171a3df75370a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499819"
---
# <a name="class-c"></a>class (C++)

Das- **`class`** Schlüsselwort deklariert einen Klassentyp oder definiert ein Objekt eines Klassen Typs.

## <a name="syntax"></a>Syntax

```
[template-spec]
class [ms-decl-spec] [tag [: base-list ]]
{
   member-list
} [declarators];
[ class ] tag declarators;
```

#### <a name="parameters"></a>Parameter

*Vorlagen Spezifikation*<br/>
Optionale Vorlagenspezifikationen. Weitere Informationen finden Sie unter [Vorlagen](templates-cpp.md).

*class*<br/>
Das **`class`** Schlüsselwort.

*MS-decl-spec*<br/>
Optionale Speicherklassenspezifikation. Weitere Informationen finden Sie unter [__declspec](../cpp/declspec.md) -Schlüsselwort.

*das Tag*<br/>
Der Typname, der für die Klasse angegeben wurde. Das Tag ist ein reserviertes Wort innerhalb des Gültigkeitsbereichs der Klasse. Das Tag ist optional. Wenn es nicht angegeben wird, wird eine anonyme Klasse definiert. Weitere Informationen finden Sie unter [Anonyme Klassentypen](../cpp/anonymous-class-types.md).

*base-list*<br/>
Optionale Liste von Klassen oder Strukturen, von denen diese Klasse ihre Member ableitet. Weitere Informationen finden Sie unter [Basisklassen](../cpp/base-classes.md) . Jedem Basisklassen-oder Struktur Namen kann ein Zugriffsspezifizierer ([Public](../cpp/public-cpp.md), [private](../cpp/private-cpp.md), [Protected](../cpp/protected-cpp.md)) und das [Virtual](../cpp/virtual-cpp.md) -Schlüsselwort vorangestellt werden. Weitere Informationen finden Sie in der Tabelle "Member-Access" unter [Steuern des Zugriffs auf Klassenmember](member-access-control-cpp.md) .

*Mitgliederliste*<br/>
Liste von Klassenmembern. Weitere Informationen finden Sie unter [Übersicht über Klassenmember](../cpp/class-member-overview.md) .

*Deklaratoren*<br/>
Deklaratorliste, die die Namen von mindestens einer Instanz eines Klassentyps festlegt. Deklaratoren können Initialisiererlisten einschließen, wenn alle Datenmember der-Klasse sind **`public`** . Dies kommt häufiger in Strukturen vor, deren Datenmember **`public`** Standardmäßig sind, als in Klassen. Weitere Informationen finden Sie [unter Übersicht über Deklaratoren](./declarations-and-definitions-cpp.md) .

## <a name="remarks"></a>Bemerkungen

Weitere Informationen zu Klassen im Allgemeinen finden Sie in einem der folgenden Themen:

- [struct](../cpp/struct-cpp.md)

- [union](../cpp/unions.md)

- [__multiple_inheritance](../cpp/inheritance-keywords.md)

- [__single_inheritance](../cpp/inheritance-keywords.md)

- [__virtual_inheritance](../cpp/inheritance-keywords.md)

Informationen zu verwalteten Klassen und Strukturen in C++/CLI und C++/CX finden Sie unter [Klassen und Strukturen](../extensions/classes-and-structs-cpp-component-extensions.md) .

## <a name="example"></a>Beispiel

```cpp
// class.cpp
// compile with: /EHsc
// Example of the class keyword
// Exhibits polymorphism/virtual functions.

#include <iostream>
#include <string>
using namespace std;

class dog
{
public:
   dog()
   {
      _legs = 4;
      _bark = true;
   }

   void setDogSize(string dogSize)
   {
      _dogSize = dogSize;
   }
   virtual void setEars(string type)      // virtual function
   {
      _earType = type;
   }

private:
   string _dogSize, _earType;
   int _legs;
   bool _bark;

};

class breed : public dog
{
public:
   breed( string color, string size)
   {
      _color = color;
      setDogSize(size);
   }

   string getColor()
   {
      return _color;
   }

   // virtual function redefined
   void setEars(string length, string type)
   {
      _earLength = length;
      _earType = type;
   }

protected:
   string _color, _earLength, _earType;
};

int main()
{
   dog mongrel;
   breed labrador("yellow", "large");
   mongrel.setEars("pointy");
   labrador.setEars("long", "floppy");
   cout << "Cody is a " << labrador.getColor() << " labrador" << endl;
}
```

## <a name="see-also"></a>Weitere Informationen

[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[Klassen und Strukturen](../cpp/classes-and-structs-cpp.md)
