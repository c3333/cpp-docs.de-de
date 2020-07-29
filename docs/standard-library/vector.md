---
title: '&lt;vector&gt;'
ms.date: 11/04/2016
f1_keywords:
- <vector>
helpviewer_keywords:
- vector header
ms.assetid: c1431ad8-c0b6-4dbb-89c4-5f651e432d7f
ms.openlocfilehash: 4e9f3e4a35cd772897e326fafedf359062e6128b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224525"
---
# <a name="ltvectorgt"></a>&lt;vector&gt;

Definiert den Containerklassen Vorlagen Vektor und mehrere unterstützende Vorlagen.

Der `vector` ist ein Container, der Elemente eines bestimmten Typs in einer linearen Sequenz organisiert. Er ermöglicht schnellen zufälligen Zugriff auf alle Elemente sowie dynamische Hinzufügungen und Entfernungen zu und aus der Sequenz. Der `vector` ist der bevorzugte Container für eine Sequenz, wenn die Leistung mit wahlfreiem Zugriff ein wichtiger Faktor ist.

> [!NOTE]
> Die \<vector> Bibliothek verwendet auch die- `#include <initializer_list>` Anweisung.

Weitere Informationen zur `vector`-Klasse finden Sie unter [vector-Klasse](../standard-library/vector-class.md). Weitere Informationen zur Spezialisierung `vector<bool>` finden Sie unter [Vector- \<bool> Klasse](../standard-library/vector-bool-class.md).

## <a name="syntax"></a>Syntax

```cpp
namespace std {
template <class Type, class Allocator>
class vector;
template <class Allocator>
class vector<bool>;

template <class Allocator>
struct hash<vector<bool, Allocator>>;

// TEMPLATE FUNCTIONS
template <class Type, class Allocator>
bool operator== (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator!= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator<(
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator> (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator<= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator>= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
void swap (
    vector<Type, Allocator>& left,
    vector<Type, Allocator>& right);

}  // namespace std
```

### <a name="parameters"></a>Parameter

*Sorte*\
Der Vorlagenparameter für den Typ der Daten, die im Vektor gespeichert sind.

*Allocator*\
Der Vorlagenparameter für das gespeicherte Zuweisungsobjekt, das für die Speicherbelegung und -freigabe verantwortlich ist.

*linken*\
Der erste (linke) Vektor in einem Vergleichsvorgang.

*Richting*\
Der zweite (rechte) Vektor in einem Vergleichsvorgang.

## <a name="members"></a>Member

### <a name="operators"></a>Operatoren

|||
|-|-|
|[KOM! =](../standard-library/vector-operators.md#op_neq)|Testet, ob das Vektorobjekt links vom Operator ungleich dem Vektorobjekt rechts vom Operator ist.|
|[Operator<](../standard-library/vector-operators.md#op_lt)|Testet, ob das Vektorobjekt links vom Operator kleiner als das Vektorobjekt auf der rechten Seite ist.|
|[KOM\<=](../standard-library/vector-operators.md#op_gt_eq)|Testet, ob das Vektorobjekt links vom Operator kleiner als oder gleich dem Vektorobjekt rechts vom Operator ist.|
|[Operator = =](../standard-library/vector-operators.md#op_eq_eq)|Testet, ob das Vektorobjekt links vom Operator gleich dem Vektorobjekt rechts vom Operator ist.|
|[Operator>](../standard-library/vector-operators.md#op_gt)|Testet, ob das Vektorobjekt links vom Operator größer als das Vektorobjekt auf der rechten Seite ist.|
|[Operator>=](../standard-library/vector-operators.md#op_gt_eq)|Testet, ob das Vektorobjekt links vom Operator größer als oder gleich dem Vektorobjekt rechts vom Operator ist.|

### <a name="classes"></a>Klassen

|||
|-|-|
|[Vector-Klasse](../standard-library/vector-class.md)|Eine Klassenvorlage von Sequenzcontainern, die Elemente eines bestimmten Typs in einer linearen Anordnung anordnen und schnellen zufälligen Zugriff auf ein Element ermöglichen.|

### <a name="specializations"></a>Spezialisierungen

|||
|-|-|
|hash|Gibt einen Hashwert des Vektors zurück.|
|[Vector- \<bool> Klasse](../standard-library/vector-bool-class.md)|Eine vollständige Spezialisierung des Klassen Vorlagen Vektors für Elemente des Typs **`bool`** mit einer Zuweisung für den zugrunde liegenden Typ, der von der Spezialisierung verwendet wird.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<vector>

**Namespace:** std

## <a name="see-also"></a>Siehe auch

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++-Standard Bibliotheks Referenz](../standard-library/cpp-standard-library-reference.md)
