---
title: '&lt;optional&gt;'
ms.date: 08/06/2019
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.openlocfilehash: 31a3d9aad539e45bb835331a4ef63690d0e16f49
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842675"
---
# <a name="ltoptionalgt"></a>&lt;optional&gt;

Definiert die Containerklassen Vorlage `optional` und verschiedene unterstützende Vorlagen.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<optional>

**Namespace:** std

## <a name="members"></a>Member

### <a name="operators"></a>Operatoren

|Name|Beschreibung|
|-|-|
|[Operator = =](../standard-library/optional-operators.md#op_eq_eq)|Testet, ob ein Objekt gleich einem anderen Objekt ist.|
|[Operator! =](../standard-library/optional-operators.md#op_neq)|Testet, ob ein Objekt ungleich einem anderen Objekt ist.|
|[Operator<](../standard-library/optional-operators.md#op_lt)|Testet, ob das Objekt auf der linken Seite kleiner ist als das Objekt auf der rechten Seite.|
|[Operator<=](../standard-library/optional-operators.md#op_lt_eq)|Testet, ob das-Objekt Links kleiner als oder gleich dem-Objekt auf der rechten Seite ist.|
|[Operator>](../standard-library/optional-operators.md#op_gt)|Testet, ob das-Objekt auf der linken Seite größer als das-Objekt auf der rechten Seite ist.|
|[Operator>=](../standard-library/optional-operators.md#op_lt_eq)|Testet, ob das-Objekt auf der linken Seite größer als oder gleich dem-Objekt auf der rechten Seite ist.|

> [!NOTE]
> Zusätzlich zu relationalen vergleichen \<optional> unterstützen Operatoren auch Vergleiche mit **nullopt** und `T` .

### <a name="functions"></a>Functions

|Name|Beschreibung|
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|Macht ein-Objekt optional.|
|[swap](../standard-library/optional-functions.md#swap)|Vertauscht die enthaltenen Werte von zwei- `optional` Objekten.|

### <a name="classes-and-structs"></a>Klassen und Strukturen

|Name|Beschreibung|
|-|-|
|hash|Gibt einen Hash des enthaltenen-Objekts zurück.|
|[optional-Klasse](../standard-library/optional-class.md)|Beschreibt ein Objekt, das einen Wert enthalten kann.|
|[nullopt_t-Struktur](../standard-library/nullopt-t-structure.md)|Beschreibt ein Objekt, das keinen Wert enthält.|
|[bad_optional_access-Klasse](../standard-library/bad-optional-access-class.md)|Beschreibt ein Objekt, das als Ausnahme ausgelöst wurde, um einen Versuch, auf einen Wert zuzugreifen, zu melden.|

### <a name="objects"></a>Objekte

|Name|Beschreibung|
|-|-|
|[nullopt](../standard-library/optional-functions.md#nullopt)|Eine Instanz von `nullopt_t` für Vergleiche.|

## <a name="see-also"></a>Weitere Informationen

[Headerdateienreferenz](../standard-library/cpp-standard-library-header-files.md)
