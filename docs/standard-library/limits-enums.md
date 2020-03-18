---
title: '&lt;limits&gt;-Enumerationen'
ms.date: 11/04/2016
f1_keywords:
- limits/std::float_denorm_style
- limits/std::float_round_style
ms.assetid: c86680a2-ba97-4ed9-8c20-a448857d7dc5
ms.openlocfilehash: 567e0538f59c40d57f85d652a8919be6e034cf0b
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425610"
---
# <a name="ltlimitsgt-enums"></a>&lt;limits&gt;-Enumerationen

## <a name="float_denorm_style"></a>float_denorm_style

Die Enumeration beschreibt die verschiedenen Methoden, die eine Implementierung für die Darstellung eines denormalisierten Gleitkommawerts auswählen kann – für Werte, die zu klein sind, um als normalisierte Werte dargestellt zu werden:

```cpp
enum float_denorm_style {
    denorm_indeterminate = -1,
    denorm_absent = 0,
    denorm_present = 1    };
```

### <a name="return-value"></a>Rückgabewert

Die Enumeration gibt Folgendes zurück:

- `denorm_indeterminate`, wenn das vorhanden sein oder Fehlen von denormalisierten Formularen bei der Übersetzung nicht bestimmt werden kann.

- `denorm_absent`, wenn denormalisierte Formulare nicht vorhanden sind.

- `denorm_present`, wenn denormalisierte Formulare vorhanden sind.

### <a name="example"></a>Beispiel

Unter [numeric_limits::has_denorm](../standard-library/numeric-limits-class.md#has_denorm) finden Sie ein Beispiel, in dem auf die Werte dieser Enumeration zugegriffen werden kann.

## <a name="float_round_style"></a>float_round_style

Die Enumeration beschreibt die verschiedenen Methoden, die eine Implementierung für die Rundung eines Gleitkommawerts auf einen ganzzahligen Wert auswählen kann.

```cpp
enum float_round_style {
    round_indeterminate = -1,
    round_toward_zero = 0,
    round_to_nearest = 1,
    round_toward_infinity = 2,
    round_toward_neg_infinity = 3    };
```

### <a name="return-value"></a>Rückgabewert

Die Enumeration gibt Folgendes zurück:

- `round_indeterminate`, wenn die Rundungs Methode nicht bestimmt werden kann.

- `round_toward_zero`, wenn die Runde Richtung 0 (null) ist.

- `round_to_nearest`, wenn der auf die nächste ganze Zahl abgerundet wird.

- `round_toward_infinity`, wenn die Runde von NULL entfernt wird.

- `round_toward_neg_infinity`, wenn die auf eine negative ganze Zahl gerundet wird.

### <a name="example"></a>Beispiel

Unter [numeric_limits::round_style](../standard-library/numeric-limits-class.md#round_style) finden Sie ein Beispiel, in dem auf die Werte dieser Enumeration zugegriffen werden kann.
