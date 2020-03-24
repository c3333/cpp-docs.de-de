---
title: Triviale Typen sowie Standardlayout-, POD- und Literaltypen
ms.date: 04/05/2018
ms.assetid: 2b23a7be-9bad-49fc-8298-31a9a7c556b0
ms.openlocfilehash: b31fefd31b32a5fc4aa3f655b90d39f60a524ca4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188063"
---
# <a name="trivial-standard-layout-pod-and-literal-types"></a>Triviale Typen sowie Standardlayout-, POD- und Literaltypen

Der Begriff *Layout* bezieht sich auf die Art und Weise, wie die Member eines Objekts einer Klasse, einer Struktur oder eines Union-Typs im Speicher angeordnet sind. Manchmal wird das Layout genau von der Sprachspezifikation definiert. Wenn eine Klasse oder Struktur allerdings bestimmte C++-Sprachfeatures wie virtuelle Basisklassen, virtuelle Funktionen und Member mit unterschiedlicher Zugriffssteuerung enthält, kann der Compiler ein beliebiges Layout auswählen. Je nachdem, welche Optimierungen ausgeführt werden, kann dieses Layout variieren, und häufig nimmt das Objekt nicht einmal einen zusammenhängenden Bereich des Speichers ein. Wenn eine Klasse beispielsweise über virtuelle Funktionen verfügt, teilen möglicherweise alle Instanzen dieser Klasse eine einzige virtuelle Funktionstabelle. Typen wie diese sind zwar einerseits sehr nützlich, es gelten aber andererseits auch Einschränkungen. Da das Layout nicht definiert ist, können diese Typen nicht an Programme übergeben werden, die in anderen Sprachen (z. B. C) geschrieben sind. Außerdem können sie nicht zuverlässig über schnelle Funktionen auf unterster Ebene wie `memcopy` kopiert oder über ein Netzwerk serialisiert werden, da sie möglicherweise nicht zusammenhängen.

C++14 hat die folgenden drei Kategorien einfacher Klassen und Strukturen eingeführt, damit Compiler, C++-Programme und Metaprogramme ermitteln können, ob sich ein bestimmter Vorgangstyp eignet, der von einem bestimmten Speicherlayout abhängig ist: *trivial*, *standard-layout* und *POD* (Plain Old Data). Die Standardbibliothek verfügt über die Funktionsvorlagen `is_trivial<T>`, `is_standard_layout<T>` und `is_pod<T>`, die bestimmen, ob der jeweilige Typ einer vorhandenen Kategorie zugeordnet werden kann.

## <a name="trivial-types"></a>Triviale Typen

Wenn eine Klasse oder Struktur in C++ vom Compiler bereitgestellte oder explizit auf den Standardwert festgelegte Memberfunktionen aufweist, handelt es sich um einen trivialen Typ. Dieser nimmt einen zusammenhängenden Speicherbereich ein. Er kann Member mit unterschiedlichen Zugriffsspezifizierern aufweisen. In C++ kann der Compiler die Sortierung der Member in dieser Situation selbst bestimmen. Aus diesem Grund können Sie zwar die Funktion „memcopy“ für diese Objekte ausführen, aber Sie können sie nicht zuverlässig über ein C-Programm verarbeiten. Ein trivialer Typ (T) kann zuerst in ein Array vom Typ „char“ oder „unsigned char“ kopiert und anschließend wieder sicher in eine T-Variable zurückkopiert werden. Aufgrund von Ausrichtungsanforderungen gibt es möglicherweise zwischen den Typmembern Bytes zum Auffüllen.

Triviale Typen verfügen über einen einfachen Standard- und Kopierkonstruktor, einen einfachen Kopierzuweisungsoperator und einen einfachen Destruktor. *Einfach* bedeutet hier, dass der Konstruktor/Operator/Destruktor nicht vom Benutzer bereitgestellt wird und einer Klasse angehört, die

- keine virtuellen Funktionen oder Basisklassen aufweist

- keine Basisklassen mit einem zugehörigen nicht trivialen Konstruktor/Operator/Destruktor aufweist

- keine Datenelemente von Basisklassen mit einem zugehörigen nicht trivialen Konstruktor/Operator/Destruktor aufweist

Im folgenden Beispiel werden triviale Typen dargestellt. In „Trivial2“ müssen Sie einen Standardkonstruktor angeben, weil ein `Trivial2(int a, int b)`-Konstruktor vorhanden ist. Damit der Typ als „trivial“ bezeichnet werden kann, müssen Sie diesen Konstruktor explizit auf den Standardwert festlegen.

```cpp
struct Trivial
{
      int i;
private:
   int j;
   };

struct Trivial2
{
   int i;
   Trivial2(int a, int b) : i(a), j(b) {}
   Trivial2() = default;
   private:
   int j;   // Different access control
};
```

## <a name="standard-layout-types"></a>Standardlayouttypen

Wenn eine Klasse oder Struktur bestimmte C++-Sprachfeatures wie virtuelle Funktionen nicht enthält, die es in der C-Sprache nicht gibt, und alle Member über dieselbe Zugriffssteuerung verfügen, handelt es sich um einen Standardlayouttyp. Auf diesen Typ kann die Funktion „memcopy“ angewendet werden und das Layout ist so umfassend definiert, dass C-Programme verarbeitet werden können. Standardlayouttypen können über besondere benutzerdefinierte Memberfunktionen verfügen. Außerdem weisen sie die folgenden Eigenschaften auf:

- keine virtuellen Funktionen oder Basisklassen

- alle nicht statischen Datenelemente verfügen über dieselbe Zugriffssteuerung

- alle nicht statischen Member von Klassen gehören dem Standardlayouttyp an

- sämtliche Basisklassen gehören dem Standardlayouttyp an

- keine Basisklassen des Typs, dem das erste nicht statische Datenelement angehört

- eine der folgenden Bedingungen wird erfüllt:

  - keine nicht statischen Datenelemente in der Klasse mit den meisten Ableitungen und nicht mehr als eine Basisklasse mit nicht statischen Datenelementen

  - keine Basisklassen mit nicht statischen Datenelementen

Der folgende Codeausschnitt enthält ein Beispiel eines Standardlayouttyps:

```cpp
struct SL
{
   // All members have same access:
   int i;
   int j;
   SL(int a, int b) : i(a), j(b) {} // User-defined constructor OK
};
```

Die letzten beiden Anforderungen lassen sich möglicherweise besser anhand eines Codebeispiels darstellen. Im nächsten Beispiel gehört `Derived` nicht dem Standardlayouttyp an, obwohl „Base“ diesem Typ zuzuordnen ist, da sowohl die Klasse mit den meisten Ableitungen als auch `Base` nicht statische Datenelemente aufweisen:

```cpp
struct Base
{
   int i;
   int j;
};

// std::is_standard_layout<<Derived> == false!
struct Derived : public Base
{
   int x;
   int y;
};
```

In diesem Beispiel ist `Derived` vom Typ „Standardlayout“, da `Base` keine nicht statischen Datenelemente aufweist.

```cpp
struct Base
{
   void Foo() {}
};

// std::is_standard_layout<<Derived> == true
struct Derived : public Base
{
   int x;
   int y;
};
```

Auch wenn `Base` die Datenelemente und `Derived` nur Memberfunktionen aufweisen würde, wäre „Derived“ vom Typ „Standardlayout“.

## <a name="pod-types"></a>POD-Typen

Wenn eine Klasse oder Struktur sowohl dem Typ „Trivial“ als auch dem Typ „Standardlayout“ zugeordnet werden kann, handelt es sich um einen POD-Typ (Plain Old Data). Das Speicherlayout von POD-Typen ist daher zusammenhängend, und jeder Member hat eine höhere Adresse als der Member, der jeweils davor deklariert wurde. Daher können Kopien Byte für Byte und binäre E/A-Vorgänge für diese Typen durchgeführt werden.  Auch Skalartypen wie „int“ gehören zu den POD-Typen. POD-Typen, bei denen es sich um Klassen handelt, können POD-Typen nur als nicht statische Datenelemente aufweisen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel werden die Unterschiede zwischen trivialen Typen sowie Standardlayout- und POD-Typen dargestellt:

```cpp
#include <type_traits>
#include <iostream>

using namespace std;

struct B
{
protected:
   virtual void Foo() {}
};

// Neither trivial nor standard-layout
struct A : B
{
      int a;
   int b;
   void Foo() override {} // Virtual function
};

// Trivial but not standard-layout
struct C
   {
      int a;
private:
   int b;   // Different access control
};

// Standard-layout but not trivial
struct D
{
   int a;
   int b;
   D() {} //User-defined constructor
};

struct POD
{
   int a;
   int b;
};

int main()
{
   cout << boolalpha;
   cout << "A is trivial is " << is_trivial<A>() << endl; // false
   cout << "A is standard-layout is " << is_standard_layout<A>() << endl;  // false

   cout << "C is trivial is " << is_trivial<C>() << endl; // true
   cout << "C is standard-layout is " << is_standard_layout<C>() << endl;  // false

   cout << "D is trivial is " << is_trivial<D>() << endl;  // false
   cout << "D is standard-layout is " << is_standard_layout<D>() << endl; // true

   cout << "POD is trivial is " << is_trivial<POD>() << endl; // true
   cout << "POD is standard-layout is " << is_standard_layout<POD>() << endl; // true

   return 0;
}
```

## <a name="literal-types"></a><a name="literal_types"></a> Literaltypen

Das Layout eines Literaltyps kann zur Kompilierzeit bestimmt werden. Folgende Typen sind Literaltypen:

- void
- Skalare Typen
- Verweise
- Void-Arrays, skalare Typen oder Verweise
- Eine Klasse, die einen trivialen Destruktor und einen oder mehrere constexpr-Konstruktoren aufweist, die keine Konstruktoren zum Verschieben oder Kopieren sind. Darüber hinaus müssen alle nicht statischen Datenmember und Basisklassen Literaltypen und permanent sein.

## <a name="see-also"></a>Weitere Informationen

[Grundlegende Konzepte](../cpp/basic-concepts-cpp.md)
