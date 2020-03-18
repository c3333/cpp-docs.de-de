---
title: '&lt;list&gt;'
ms.date: 11/04/2016
f1_keywords:
- <list>
helpviewer_keywords:
- list header
ms.assetid: 2345823b-5612-44d8-95d3-aa96ed076d17
ms.openlocfilehash: 6b67434d36146de87a124fc02f49971425943dc5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447281"
---
# <a name="ltlistgt"></a>&lt;list&gt;

Definiert die Containerklassen-Vorlagenliste und mehrere unterstützende Vorlagen.

## <a name="syntax"></a>Syntax

```cpp
#include <list>
```

> [!NOTE]
> Die \<Liste > Bibliothek verwendet auch die `#include <initializer_list>`-Anweisung.

## <a name="members"></a>Members

### <a name="operators"></a>Operatoren

|||
|-|-|
|[operator!=](../standard-library/list-operators.md#op_neq)|Testet, ob das Listenobjekt links vom Operator ungleich dem Listenobjekt rechts vom Operator ist.|
|[operator<](../standard-library/list-operators.md#op_lt)|Testet, ob das Listenobjekt links vom Operator kleiner als das Listenobjekt auf der rechten Seite ist.|
|[operator\<=](../standard-library/list-operators.md#op_gt_eq)|Testet, ob das Listenobjekt links vom Operator kleiner als oder gleich dem Listenobjekt rechts vom Operator ist.|
|[operator==](../standard-library/list-operators.md#op_eq_eq)|Testet, ob das Listenobjekt links vom Operator gleich dem Listenobjekt rechts vom Operator ist.|
|[operator>](../standard-library/list-operators.md#op_gt)|Testet, ob das Listenobjekt links vom Operator größer als das Listenobjekt auf der rechten Seite ist.|
|[operator>=](../standard-library/list-operators.md#op_gt_eq)|Testet, ob das Listenobjekt links vom Operator größer als oder gleich dem Listenobjekt rechts vom Operator ist.|

### <a name="functions"></a>Functions

|||
|-|-|
|[swap](../standard-library/list-functions.md#swap)|Tauscht die Elemente zweier Listen aus.|

### <a name="classes"></a>Klassen

|||
|-|-|
|[list-Klasse](../standard-library/list-class.md)|Eine Klassen Vorlage von Sequenz Containern, die ihre Elemente in einer linearen Anordnung verwalten und effiziente Einfügungen und Löschungen an einer beliebigen Position innerhalb der Sequenz ermöglichen.|

## <a name="see-also"></a>Weitere Informationen

[Headerdateienreferenz](../standard-library/cpp-standard-library-header-files.md)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ Standard Library Reference (C++-Standardbibliotheksreferenz)](../standard-library/cpp-standard-library-reference.md)
