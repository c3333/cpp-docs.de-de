---
title: '&lt;limits&gt;'
ms.date: 11/04/2016
f1_keywords:
- limits/std::<limits>
- <limits>
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
ms.openlocfilehash: 1527672bd51682bf32c82601ff54a94ea4154a0b
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841908"
---
# <a name="ltlimitsgt"></a>&lt;limits&gt;

Definiert die Klassen Vorlage `numeric_limits` und zwei Enumerationen zu Gleit Komma Darstellungen und Rundung.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<limits>

**Namespace:** std

## <a name="remarks"></a>Bemerkungen

Explizite Spezialisierungs spezizierungen der- `numeric_limits` Klasse beschreiben viele Eigenschaften der grundlegenden Typen, einschließlich der Zeichen-, ganzzahligen und Gleit Komma Typen, die **`bool`** durch die Implementierung definiert und nicht durch die Regeln der C++-Sprache festgelegt werden. Zu den in beschriebenen Eigenschaften \<limits> gehören Genauigkeit, Darstellungen von minimalen und maximalen Größen, Rundungs-und Signalisierungs Typfehler.

## <a name="members"></a>Member

### <a name="enumerations"></a>Enumerationen

|Name|Beschreibung|
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|Die Enumeration beschreibt die verschiedenen Methoden, die eine Implementierung für die Darstellung eines denormalisierten Gleitkommawerts auswählen kann – für Werte, die zu klein sind, um als normalisierte Werte dargestellt zu werden:|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|Die Enumeration beschreibt die verschiedenen Methoden, die eine Implementierung für die Rundung eines Gleitkommawerts auf einen ganzzahligen Wert auswählen kann.|

### <a name="classes"></a>Klassen

|name|Beschreibung|
|-|-|
|[Numeric_limits-Klasse](../standard-library/numeric-limits-class.md)|Die Klassen Vorlage beschreibt arithmetische Eigenschaften integrierter numerischer Typen.|

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
