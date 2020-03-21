---
title: 'Wert Kategorien: Lvalues und Rvalues (C++)'
ms.date: 05/07/2019
helpviewer_keywords:
- R-values [C++]
- L-values [C++]
ms.assetid: a8843344-cccc-40be-b701-b71f7b5cdcaf
ms.openlocfilehash: 23625ddf44d16a4dc408b87f27b9cdfba7a9cbd4
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077234"
---
# <a name="lvalues-and-rvalues-c"></a>Lvalues und Rvalues (C++)

Jeder C++ Ausdruck weist einen Typ auf, der zu einer *Wert Kategorie*gehört. Die Wert Kategorien bilden die Grundlage für Regeln, die Compiler beim Erstellen, kopieren und Verschieben von temporären Objekten während der Ausdrucks Auswertung befolgen müssen.

Der c++ 17-Standard definiert Ausdruckswert Kategorien wie folgt:

- Ein *glvalue* ist ein Ausdruck, dessen Auswertung die Identität eines Objekts, eines Bitfelds oder einer Funktion bestimmt.
- Ein *prvalue* ist ein Ausdruck, dessen Auswertung ein Objekt oder ein Bitfeld initialisiert oder den Wert des Operanden eines Operators berechnet, wie er durch den Kontext angegeben wird, in dem er angezeigt wird.
- Ein *xValue* ist ein glvalue, das ein Objekt oder ein Bitfeld angibt, dessen Ressourcen wieder verwendet werden können (in der Regel, weil es sich in der Nähe des Endes seiner Lebensdauer befindet). Beispiel: bestimmte Arten von Ausdrücken mit Rvalue-verweisen (8.3.2) ergeben xValues, wie z. b. einen Rückruf einer Funktion, deren Rückgabetyp ein rvalue-Verweis oder eine Umwandlung in einen Rvalue-Verweistyp ist.
- Ein *Lvalue* ist ein glvalue, bei dem es sich nicht um einen xValue handelt.
- Ein *Rvalue* -Wert ist ein prvalue-oder xValue-Wert.

Im folgenden Diagramm werden die Beziehungen zwischen den Kategorien veranschaulicht:

![C++Ausdruckswert Kategorien](media/value_categories.png "C++Ausdruckswert Kategorien")

Ein Lvalue verfügt über eine Adresse, auf die das Programm zugreifen kann. Beispiele für lvalue-Ausdrücke sind Variablennamen, einschließlich **Konstanten** Variablen, Array Elementen, Funktionsaufrufen, die einen Lvalue-Verweis, Bitfelder, Unions und Klassenmember zurückgeben.

Ein prvalue-Ausdruck hat keine Adresse, auf die das Programm zugreifen kann. Beispiele für prvalue-Ausdrücke sind Literale, Funktionsaufrufe, die einen nicht Verweistyp zurückgeben, sowie temporäre Objekte, die während der Ausdrucks Auswertung erstellt werden, auf die jedoch nur der Compiler zugreifen kann.

Ein xValue-Ausdruck verfügt über eine Adresse, die nicht mehr für das Programm zugänglich ist, aber zum Initialisieren eines Rvalue-Verweises verwendet werden kann, der den Zugriff auf den Ausdruck ermöglicht. Beispiele hierfür sind Funktionsaufrufe, die einen rvalue-Verweis zurückgeben, und das Array Index, Member und Zeiger auf Member-Ausdrücke, wobei das Array oder das Objekt ein rvalue-Verweis ist.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt mehrere korrekte und falsche Verwendungen von lvalues und rvalues:

```cpp
// lvalues_and_rvalues2.cpp
int main()
{
    int i, j, *p;

    // Correct usage: the variable i is an lvalue and the literal 7 is a prvalue.
    i = 7;

    // Incorrect usage: The left operand must be an lvalue (C2106).`j * 4` is a prvalue.
    7 = i; // C2106
    j * 4 = 7; // C2106

    // Correct usage: the dereferenced pointer is an lvalue.
    *p = i;

    // Correct usage: the conditional operator returns an lvalue.
    ((i < 3) ? i : j) = 7;

    // Incorrect usage: the constant ci is a non-modifiable lvalue (C3892).
    const int ci = 7;
    ci = 9; // C3892
}
```

> [!NOTE]
> Die Beispiele zu diesem Thema veranschaulichen die korrekte und falsche Verwendung, wenn Operatoren nicht überladen werden. Indem Sie Operatoren überladen, können Sie aus einem Ausdruck wie `j * 4` einen lvalue machen.

Die Begriffe *Lvalue* und *Rvalue* werden häufig verwendet, wenn Sie auf Objekt Verweise verweisen. Weitere Informationen zu verweisen finden Sie unter [Lvalue Reference declarator: &](../cpp/lvalue-reference-declarator-amp.md) und [rvalue reference declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Weitere Informationen

[Grundlegende Konzepte](../cpp/basic-concepts-cpp.md)<br/>
[Lvalue-Verweisdeklarator: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Rvalue-Verweisdeklarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md)
