---
title: '&lt;set&gt;'
ms.date: 11/04/2016
f1_keywords:
- <set>
helpviewer_keywords:
- set header
ms.assetid: 43cb1ab2-6383-48cf-8bdc-2b96d7203596
ms.openlocfilehash: 4ac5c0bbf94c4d17389efb424d2e12b84717c4a9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846224"
---
# <a name="ltsetgt"></a>&lt;set&gt;

Definiert die Containerklassen Vorlagen und die Multimenge und deren unterstützende Vorlagen.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<set>

**Namespace:** std

> [!NOTE]
> Die \<set> Bibliothek verwendet auch die- `#include <initializer_list>` Anweisung.

## <a name="members"></a>Member

### <a name="operators"></a>Operatoren

|set-Version|multiset-Version|Beschreibung|
|-|-|-|
|[Operator! = (Set)](../standard-library/set-operators.md#op_neq)|[Operator! = (Multimenge)](../standard-library/set-operators.md#op_neq)|Überprüft, ob das set- oder multiset-Objekt links vom Operator ungleich dem set- oder multiset-Objekt rechts vom Operator ist.|
|[Operator< (Set)](../standard-library/set-operators.md#op_lt)|[Operator< (Multimenge)](../standard-library/set-operators.md#op_lt_multiset)|Überprüft, ob das set- oder multiset-Objekt links vom Operator kleiner als das set- oder multiset-Objekt rechts vom Operator ist.|
|[Operator<= (Set)](../standard-library/set-operators.md#op_lt_eq)|[operator\<= (multiset)](../standard-library/set-operators.md#op_lt_eq_multiset)|Überprüft, ob das set- oder multiset-Objekt links vom Operator kleiner gleich dem set- oder multiset-Objekt rechts vom Operator ist.|
|[Operator = = (Set)](../standard-library/set-operators.md#op_eq_eq)|[Operator = = (Multimenge)](../standard-library/set-operators.md#op_eq_eq_multiset)|Überprüft, ob das set- oder multiset-Objekt links vom Operator gleich dem set- oder multiset-Objekt rechts vom Operator ist.|
|[Operator> (Set)](../standard-library/set-operators.md#op_gt)|[Operator> (Multimenge)](../standard-library/set-operators.md#op_gt_multiset)|Überprüft, ob das set- oder multiset-Objekt links vom Operator größer als das set- oder multiset-Objekt rechts vom Operator ist.|
|[Operator>= (Set)](../standard-library/set-operators.md#op_gt_eq)|[Operator>= (Multimenge)](../standard-library/set-operators.md#op_gt_eq_multiset)|Überprüft, ob das set- oder multiset-Objekt links vom Operator größer gleich dem set- oder multiset-Objekt rechts vom Operator ist.|

### <a name="specialized-template-functions"></a>Spezialisierte Vorlagenfunktionen

|set-Version|multiset-Version|Beschreibung|
|-|-|-|
|[swap](../standard-library/set-functions.md#swap)|[swap (multiset)](../standard-library/set-functions.md#swap_multiset)|Tauscht die Elemente von zwei set- oder multiset-Objekten aus.|

### <a name="classes"></a>Klassen

|name|Beschreibung|
|-|-|
|[Set-Klasse](../standard-library/set-class.md)|Wird zum Speichern und Abrufen von Daten aus einer Sammlung verwendet, in der die Werte der enthaltenen Elemente eindeutig sind und als Schlüsselwerte dienen, entsprechend denen die Daten automatisch geordnet werden.|
|[multiset-Klasse](../standard-library/multiset-class.md)|Wird zum Speichern von Daten in und zum Abrufen von Daten aus einer Sammlung verwendet, in der die Werte der enthaltenen Elemente nicht eindeutig sein müssen und als Schlüsselwerte dienen, entsprechend denen die Daten automatisch geordnet werden.|

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++-Standard Bibliotheks Referenz](../standard-library/cpp-standard-library-reference.md)
