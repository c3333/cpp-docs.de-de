---
title: _variant_t::SetString
ms.date: 11/04/2016
f1_keywords:
- _variant_t::SetString
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
ms.openlocfilehash: 60ad1c1bd95eb35f2a4f2800f79d0326c68a1176
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745847"
---
# <a name="_variant_tsetstring"></a>_variant_t::SetString

**Microsoft Specific**

Weist diesem `_variant_t`-Objekt eine Zeichenfolge zu.

## <a name="syntax"></a>Syntax

```cpp
void SetString(const char* pSrc);
```

#### <a name="parameters"></a>Parameter

*pSrc*<br/>
Zeiger auf die Zeichenfolge.

## <a name="remarks"></a>Bemerkungen

Konvertiert eine Zeichenfolge mit ANSI-Zeichen in eine Unicode-`BSTR`-Zeichenfolge und weist sie diesem `_variant_t`-Objekt zu.

**END Microsoft Spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_variant_t-Klasse](../cpp/variant-t-class.md)
