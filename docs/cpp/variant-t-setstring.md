---
title: _variant_t::SetString
ms.date: 11/04/2016
f1_keywords:
- _variant_t::SetString
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
ms.openlocfilehash: 0cd300a09c29668c496d93109d1bc862947e948c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187556"
---
# <a name="_variant_tsetstring"></a>_variant_t::SetString

**Microsoft-spezifisch**

Weist diesem `_variant_t`-Objekt eine Zeichenfolge zu.

## <a name="syntax"></a>Syntax

```
void SetString(const char* pSrc);
```

#### <a name="parameters"></a>Parameter

*pSrc*<br/>
Zeiger auf die Zeichenfolge.

## <a name="remarks"></a>Bemerkungen

Konvertiert eine Zeichenfolge mit ANSI-Zeichen in eine Unicode-`BSTR`-Zeichenfolge und weist sie diesem `_variant_t`-Objekt zu.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_variant_t-Klasse](../cpp/variant-t-class.md)
