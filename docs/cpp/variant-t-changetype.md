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
ms.openlocfilehash: b0692c9befaa6b7e787ada624dcbb56b074c9f9d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160462"
---
# <a name="_variant_tchangetype"></a>_variant_t::ChangeType

**Microsoft-spezifisch**

Ändert den Typ des `_variant_t` Objekts in den angegeben `VARTYPE`.

## <a name="syntax"></a>Syntax

```
void ChangeType(
   VARTYPE vartype,
   const _variant_t* pSrc = NULL
);
```

#### <a name="parameters"></a>Parameter

*VarType*<br/>
Die `VARTYPE` für dieses `_variant_t`-Objekt.

*pSrc*<br/>
Ein Zeiger auf das `_variant_t`-Objekt, das umgewandelt werden soll. Wenn dieser Wert NULL ist, wird die Konvertierung direkt ausgeführt.

## <a name="remarks"></a>Bemerkungen

Diese Member-Funktion konvertiert ein `_variant_t` Objekt in die ange`VARTYPE`angezeigt. Wenn *psrc* den Wert NULL hat, erfolgt die Konvertierung direkt. andernfalls wird dieses `_variant_t` Objekt aus *psrc* kopiert und anschließend konvertiert.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_variant_t-Klasse](../cpp/variant-t-class.md)
