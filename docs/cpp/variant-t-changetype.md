---
title: _variant_t::ChangeType
ms.date: 11/04/2016
f1_keywords:
- _variant_t::ChangeType
- _variant_t.ChangeType
helpviewer_keywords:
- ChangeType method [C++]
- VARIANT object [C++], ChangeType
- VARIANT object
ms.assetid: 829d2eeb-3338-4a88-9dce-0ca145f47aac
ms.openlocfilehash: c2283158856a6781ab2e12c51f4e2ad0e4f1d531
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750728"
---
# <a name="_variant_tchangetype"></a>_variant_t::ChangeType

**Microsoft Specific**

Ändert den Typ `_variant_t` des Objekts in die angegebene `VARTYPE`.

## <a name="syntax"></a>Syntax

```cpp
void ChangeType(
   VARTYPE vartype,
   const _variant_t* pSrc = NULL
);
```

#### <a name="parameters"></a>Parameter

*Vartype*<br/>
Die `VARTYPE` für `_variant_t` dieses Objekt.

*pSrc*<br/>
Ein Zeiger auf das `_variant_t`-Objekt, das umgewandelt werden soll. Wenn dieser Wert NULL ist, wird die Konvertierung direkt ausgeführt.

## <a name="remarks"></a>Bemerkungen

Diese Memberfunktion konvertiert `_variant_t` ein Objekt `VARTYPE`in die angegebene . Wenn *pSrc* NULL ist, erfolgt die Konvertierung `_variant_t` an Ort und Stelle, andernfalls wird dieses Objekt aus *pSrc* kopiert und dann konvertiert.

**END Microsoft Spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_variant_t-Klasse](../cpp/variant-t-class.md)
