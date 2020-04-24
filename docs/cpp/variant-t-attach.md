---
title: _variant_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _variant_t::Attach
- _variant_t.Attach
helpviewer_keywords:
- Attach method [C++]
- VARIANT object [C++], attach
- VARIANT object
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
ms.openlocfilehash: d0822dfc730cbbb64f8364e6fa8fe8bc7207f9f9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750742"
---
# <a name="_variant_tattach"></a>_variant_t::Attach

**Microsoft Specific**

Fügt ein `VARIANT` Objekt an das **_variant_t-Objekt** an.

## <a name="syntax"></a>Syntax

```cpp
void Attach(VARIANT& varSrc);
```

#### <a name="parameters"></a>Parameter

*varSrc*<br/>
Ein `VARIANT` Objekt, das diesem **_variant_t** Objekt angefügt werden soll.

## <a name="remarks"></a>Bemerkungen

Übernimmt das `VARIANT` Eigentum an der, indem sie es einkapselt. Diese Memberfunktion gibt alle vorhandenen `VARIANT`gekapselten `VARIANT`frei, kopiert `VARTYPE` dann die angegebene , und legt ihre auf VT_EMPTY fest, um sicherzustellen, dass ihre Ressourcen nur vom _variant_t-Destruktor freigegeben werden können. **_variant_t**

**END Microsoft Spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_variant_t-Klasse](../cpp/variant-t-class.md)
