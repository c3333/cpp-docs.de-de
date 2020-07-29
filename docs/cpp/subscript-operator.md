---
title: Index Operator []
ms.date: 11/04/2016
f1_keywords:
- '[]'
helpviewer_keywords:
- operators [C++], subscript
- postfix operators [C++]
- '[] operator'
- subscript operator [C++], syntax
ms.assetid: 69c31494-52da-4dd0-8bbe-6ccbfd50f197
ms.openlocfilehash: a4eb878a18aa38b7047104903d10d96d66cc6720
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231090"
---
# <a name="subscript-operator-"></a>Index Operator []

## <a name="syntax"></a>Syntax

```
postfix-expression [ expression ]
```

## <a name="remarks"></a>Bemerkungen

Ein Postfix Ausdruck (bei dem es sich auch um einen primären Ausdruck handeln kann), gefolgt vom Index Operator **[]**, gibt die Array Indizierung an.

Informationen zu verwalteten Arrays in C++/CLI finden Sie unter [Arrays](../extensions/arrays-cpp-component-extensions.md).

Normalerweise ist der von *Postfix-Expression* dargestellte Wert ein Zeiger Wert, z. b. ein Array Bezeichner, und *Expression* ist ein ganzzahliger Wert (einschließlich Enumerationstypen). Syntaktisch erforderlich ist allerdings nur, dass einer der Ausdrücke vom Zeigertyp und der andere Ausdruck vom Ganzzahltyp ist. Folglich könnte der ganzzahlige Wert an der *Postfix-Expression-* Position liegen, und der Zeiger Wert kann sich in den Klammern des *Ausdrucks* oder der Indexposition befinden. Betrachten Sie das folgende Codefragment:

```cpp
int nArray[5] = { 0, 1, 2, 3, 4 };
cout << nArray[2] << endl;            // prints "2"
cout << 2[nArray] << endl;            // prints "2"
```

Im vorherigen Beispiel ist der Ausdruck `nArray[2]` identisch mit dem Ausdruck `2[nArray]`. Der Grund hierfür ist, dass das Ergebnis eines Index Ausdrucks `e1[e2]` durch Folgendes angegeben wird:

`*((e2) + (e1))`

Die vom Ausdruck zurückgegebene Adresse ist nicht *E2* -Bytes aus der Adresse *E1*. Stattdessen wird die Adresse skaliert, um das nächste Objekt im Array *E2*zu erzielen. Beispiel:

```cpp
double aDbl[2];
```

Die Adressen von `aDb[0]` und `aDb[1]` sind 8 Bytes voneinander entfernt – die Größe eines Objekts vom Typ **`double`** . Diese Skalierung gemäß dem Objekttyp erfolgt automatisch durch die C++-Sprache und wird in [Additiven Operatoren](../cpp/additive-operators-plus-and.md) definiert, wenn Addition und Subtraktion von Operanden des Zeiger Typs erläutert werden.

Ein indexierte Ausdruck kann auch mehrere Indizes haben, wie folgt:

*expression1* **[** *expression2* **] [** *expression3* **]** ...

indexierte Ausdrücke sind von links nach rechts angeordnet. Der äußerste linke Indexausdruck *Ausdruck1* **[** *Ausdruck2* **]** wird zuerst ausgewertet. Die Adresse, die sich aus dem Hinzufügen von *expression1* und *expression2* ergibt, bildet einen Zeigerausdruck. Dann wird *expression3* zu diesem Zeigerausdruck hinzugefügt, um einen neuen Zeigerausdruck zu bilden. Dies geht so lange weiter, bis der letzte Subscriptausdruck hinzugefügt wurde. Der <strong>\*</strong> Dereferenzierungsoperator () wird angewendet, nachdem der letzte Index Ausdruck ausgewertet wurde, es sei denn, der abschließende Zeiger Wert adressiert einen Arraytyp.

Ausdrücke mit mehreren Indizes verweisen auf Elemente aus mehrdimensionalen Arrays. Ein mehrdimensionales Array ist ein Array, dessen Elemente Arrays sind. Beispielsweise ist das erste Element eines dreidimensionalen Arrays ein Array mit zwei Dimensionen. Im folgenden Beispiel wird ein einfaches, zweidimensionales Array aus Zeichen deklariert und initialisiert:

```cpp
// expre_Subscript_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
#define MAX_ROWS 2
#define MAX_COLS 2

int main() {
  char c[ MAX_ROWS ][ MAX_COLS ] = { { 'a', 'b' }, { 'c', 'd' } };
  for ( int i = 0; i < MAX_ROWS; i++ )
     for ( int j = 0; j < MAX_COLS; j++ )
        cout << c[ i ][ j ] << endl;
}
```

## <a name="positive-and-negative-subscripts"></a>Positive und negative Indizes

Das erste Element eines Arrays ist Element 0. Der Bereich eines C++-Arrays liegt zwischen *Array*[0] und *Array*[*size* -1]. C++ unterstützt jedoch die positiven und negativen Indizes. Negative Indizes müssen innerhalb der Array-Grenzen liegen. Andernfalls sind die Ergebnisse unvorhersehbar. Der folgende Code zeigt positive und negative Arrayfeldindizes:

```cpp
#include <iostream>
using namespace std;

int main() {
    int intArray[1024];
    for (int i = 0, j = 0; i < 1024; i++)
    {
        intArray[i] = j++;
    }

    cout << intArray[512] << endl;   // 512

    cout << 257[intArray] << endl;   // 257

    int *midArray = &intArray[512];  // pointer to the middle of the array

    cout << midArray[-256] << endl;  // 256

    cout << intArray[-256] << endl;  // unpredictable, may crash
}
```

Der negative Index in der letzten Zeile kann zu einem Laufzeitfehler führen, da er auf eine Adresse 256 zeigt, **`int`** die kleiner als der Ursprung des Arrays ist. Der Zeiger `midArray` wird mit der Mitte von initialisiert `intArray` . Daher ist es möglich (aber gefährlich), positive und negative Array Indizes dafür zu verwenden. Array-Indexfehler generieren keine Fehler zur Kompilierzeit, führen jedoch zu unvorhersehbaren Ergebnissen.

Der Indexoperator ist kommutativ. Daher sind die Ausdrücke *Array*[*Index*] und *Index*[*Array*] garantiert gleichwertig, solange der Index Operator nicht überladen wird (siehe [überladene Operatoren](../cpp/operator-overloading.md)). Die erste Form entspricht der gängigsten Codierungspraxis, aber beide funktionieren.

## <a name="see-also"></a>Siehe auch

[Postfix Ausdrücke](../cpp/postfix-expressions.md)<br/>
[Integrierte C++-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Arrays](../cpp/arrays-cpp.md)<br/>
[Eindimensionale Arrays](../c-language/one-dimensional-arrays.md)<br/>
[Mehrdimensionale Arrays](../c-language/multidimensional-arrays-c.md)<br/>
