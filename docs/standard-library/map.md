---
title: '&lt;map&gt;'
ms.date: 11/04/2016
f1_keywords:
- <map>
helpviewer_keywords:
- map header
ms.assetid: bbf76680-7362-456e-88fa-ecda93561b6a
ms.openlocfilehash: 9a58160c573fac7d4ad170f589c04c75b456299a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846432"
---
# <a name="ltmapgt"></a>&lt;map&gt;

Definiert die Containerklassen Vorlagen Map und Multimap und deren unterstützende Vorlagen.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<map>

**Namespace:** std

> [!NOTE]
> Die \<map> Bibliothek verwendet auch die- `#include <initializer_list>` Anweisung.

## <a name="members"></a>Member

### <a name="operators"></a>Operatoren

|map-Version|multimap-Version|Beschreibung|
|-----------------|----------------------|-----------------|
|[Operator! = (Map)](../standard-library/map-operators.md#op_neq)|[Operator! = (Multimap)](../standard-library/map-operators.md#op_neq)|Überprüft, ob das map- oder multimap-Objekt links vom Operator ungleich dem map- oder multimap-Objekt rechts vom Operator ist.|
|[Operator< (Map)](../standard-library/map-operators.md#op_eq_eq)|[Operator< (Multimap)](../standard-library/map-operators.md#op_eq_eq)|Überprüft, ob das map- oder multimap-Objekt links vom Operator kleiner als das map- oder multimap-Objekt rechts vom Operator ist.|
|[Operator<= (Map)](../standard-library/map-operators.md#op_lt)|[Operator \< = (Multimap)](../standard-library/map-operators.md#op_lt)|Überprüft, ob das map- oder multimap-Objekt links vom Operator kleiner gleich dem map- oder multimap-Objekt rechts vom Operator ist.|
|[Operator = = (Map)](../standard-library/map-operators.md#op_eq_eq)|[Operator = = (Multimap)](../standard-library/map-operators.md#op_eq_eq_multimap)|Überprüft, ob das map- oder multimap-Objekt links vom Operator gleich dem map- oder multimap-Objekt rechts vom Operator ist.|
|[operator> (map)](../standard-library/map-operators.md#op_gt)|[Operator> (Multimap)](../standard-library/map-operators.md#op_gt_multimap)|Überprüft, ob das map- oder multimap-Objekt links vom Operator größer als das map- oder multimap-Objekt rechts vom Operator ist.|
|[Operator>= (Map)](../standard-library/map-operators.md#op_gt_eq)|[operator>= (multimap)](../standard-library/map-operators.md#op_gt_eq_multimap)|Überprüft, ob das map- oder multimap-Objekt links vom Operator größer gleich dem map- oder multimap-Objekt rechts vom Operator ist.|

### <a name="specialized-template-functions"></a>Spezialisierte Vorlagenfunktionen

|map-Version|multimap-Version|Beschreibung|
|-----------------|----------------------|-----------------|
|[swap (map)](../standard-library/map-functions.md#swap)|[swap (multimap)](../standard-library/map-functions.md#swap_multimap)|Tauscht die Elemente zweier map- oder multimap-Objekte aus.|

### <a name="classes"></a>Klassen

|name|Beschreibung|
|-|-|
|[Value_compare-Klasse](../standard-library/value-compare-class-map.md)|Stellt ein Funktionsobjekt bereit, das die Elemente einer Zuordnung vergleichen kann, indem die Werte ihrer Schlüssel verglichen werden, um deren relative Reihenfolge in der Zuordnung zu bestimmen.|
|[Map-Klasse](../standard-library/map-class.md)|Wird zum Speichern und Abrufen von Daten aus einer Sammlung verwendet, in der jedes der Elemente einen eindeutigen Schlüssel hat, mit dem die Daten automatisch geordnet werden.|
|[multimap-Klasse](../standard-library/multimap-class.md)|Wird zum Speichern und Abrufen von Daten aus einer Sammlung verwendet, in der jedes der Elemente einen Schlüssel hat, mit dem die Daten automatisch geordnet werden. Die Schlüssel müssen keine eindeutigen Werte haben.|

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++-Standard Bibliotheks Referenz](../standard-library/cpp-standard-library-reference.md)
