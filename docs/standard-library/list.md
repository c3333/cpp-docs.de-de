---
title: '&lt;list&gt;'
ms.date: 11/04/2016
f1_keywords:
- <list>
helpviewer_keywords:
- list header
ms.assetid: 2345823b-5612-44d8-95d3-aa96ed076d17
ms.openlocfilehash: cbc93500c3fe61b2a4640008b869f3a6b71b5c6c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833308"
---
# <a name="ltlistgt"></a>&lt;list&gt;

Definiert die Containerklassen-Vorlagenliste und mehrere unterstützende Vorlagen.

## <a name="syntax"></a>Syntax

```cpp
#include <list>
```

> [!NOTE]
> Die \<list> Bibliothek verwendet auch die- `#include <initializer_list>` Anweisung.

## <a name="members"></a>Member

### <a name="operators"></a>Operatoren

|Name|Beschreibung|
|-|-|
|[Operator! =](../standard-library/list-operators.md#op_neq)|Testet, ob das Listenobjekt links vom Operator ungleich dem Listenobjekt rechts vom Operator ist.|
|[Operator<](../standard-library/list-operators.md#op_lt)|Testet, ob das Listenobjekt links vom Operator kleiner als das Listenobjekt auf der rechten Seite ist.|
|[KOM\<=](../standard-library/list-operators.md#op_gt_eq)|Testet, ob das Listenobjekt links vom Operator kleiner als oder gleich dem Listenobjekt rechts vom Operator ist.|
|[Operator = =](../standard-library/list-operators.md#op_eq_eq)|Testet, ob das Listenobjekt links vom Operator gleich dem Listenobjekt rechts vom Operator ist.|
|[Operator>](../standard-library/list-operators.md#op_gt)|Testet, ob das Listenobjekt links vom Operator größer als das Listenobjekt auf der rechten Seite ist.|
|[Operator>=](../standard-library/list-operators.md#op_gt_eq)|Testet, ob das Listenobjekt links vom Operator größer als oder gleich dem Listenobjekt rechts vom Operator ist.|

### <a name="functions"></a>Functions

|Name|Beschreibung|
|-|-|
|[swap](../standard-library/list-functions.md#swap)|Tauscht die Elemente zweier Listen aus.|

### <a name="classes"></a>Klassen

|name|Beschreibung|
|-|-|
|[List-Klasse](../standard-library/list-class.md)|Eine Klassen Vorlage von Sequenz Containern, die ihre Elemente in einer linearen Anordnung verwalten und effiziente Einfügungen und Löschungen an einer beliebigen Position innerhalb der Sequenz ermöglichen.|

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++-Standard Bibliotheks Referenz](../standard-library/cpp-standard-library-reference.md)
