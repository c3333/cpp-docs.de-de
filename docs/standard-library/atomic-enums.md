---
title: '&lt;atomic&gt;-Enumerationen'
ms.date: 11/04/2016
f1_keywords:
- atomic/std::memory_order
ms.assetid: cd3a81c5-a19e-448f-952a-c34c717f21a9
helpviewer_keywords:
- std::memory_order
ms.openlocfilehash: d8a4e9196e27933c75a32c256114e968b55678a6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834894"
---
# <a name="ltatomicgt-enums"></a>&lt;atomic&gt;-Enumerationen

## <a name="memory_order-enum"></a><a name="memory_order_enum"></a> memory_order-Aufzählung

Stellt symbolische Namen für Synchronisierungsvorgänge auf Speicheradressen bereit. Diese Vorgänge wirken sich auf das Sichtbarwerden der Zuweisung eines Thread in einem anderen aus.

```cpp
typedef enum memory_order {
    memory_order_relaxed,
    memory_order_consume,
    memory_order_acquire,
    memory_order_release,
    memory_order_acq_rel,
    memory_order_seq_cst,
} memory_order;
```

### <a name="enumeration-members"></a>Enumerationsmember

|Name|Beschreibung|
|-|-|
|`memory_order_relaxed`|Keine Reihenfolge erforderlich.|
|`memory_order_consume`|Ein Ladevorgang fungiert als Nutzungsvorgang auf der Speicheradresse.|
|`memory_order_acquire`|Ein Ladevorgang fungiert als Abrufvorgang auf der Speicheradresse.|
|`memory_order_release`|Ein Speichervorgang fungiert als eine Befreiungsaktion auf der Speicheradresse.|
|`memory_order_acq_rel`|Kombiniert `memory_order_acquire` und `memory_order_release`.|
|`memory_order_seq_cst`|Kombiniert `memory_order_acquire` und `memory_order_release`. Als `memory_order_seq_cst` gekennzeichnete Speicherzugriffe müssen nacheinander konsistent sein.|

## <a name="see-also"></a>Weitere Informationen

[\<atomic>](../standard-library/atomic.md)
