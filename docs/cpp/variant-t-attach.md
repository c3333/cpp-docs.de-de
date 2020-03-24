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
ms.openlocfilehash: 3792ed4d0fcd86c4a4e846771c450413fda130b5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187764"
---
# <a name="_variant_tattach"></a>_variant_t::Attach

**Microsoft-spezifisch**

Fügt ein `VARIANT` Objekt an das **_variant_t** Objekt an.

## <a name="syntax"></a>Syntax

```
void Attach(VARIANT& varSrc);
```

#### <a name="parameters"></a>Parameter

*varSrc*<br/>
Ein `VARIANT`-Objekt, das an dieses **_variant_t** Objekt angefügt werden soll.

## <a name="remarks"></a>Bemerkungen

Übernimmt den Besitz der `VARIANT`, indem Sie gekapselt wird. Diese Member-Funktion gibt alle vorhandenen gekapselten `VARIANT`frei, kopiert dann die angegebene `VARIANT`und legt deren `VARTYPE` auf VT_EMPTY fest, um sicherzustellen, dass Ihre Ressourcen nur vom **_variant_t** -destrukturtor freigegeben werden können.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_variant_t-Klasse](../cpp/variant-t-class.md)
