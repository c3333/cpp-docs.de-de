---
title: _variant_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _variant_t::Detach
- _variant_t.Detach
helpviewer_keywords:
- VARIANT object [C++], detatch
- Detach method [C++]
- VARIANT object
ms.assetid: c348ac08-62cf-4657-a16f-974a79c12158
ms.openlocfilehash: 9737db6b77483fa55e1dad90b9464752cd8537a5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187738"
---
# <a name="_variant_tdetach"></a>_variant_t::Detach

**Microsoft-spezifisch**

Trennt das gekapselte `VARIANT`-Objekt von diesem `_variant_t`-Objekt.

## <a name="syntax"></a>Syntax

```
VARIANT Detach( );
```

## <a name="return-value"></a>Rückgabewert

Der gekapselte `VARIANT`.

## <a name="remarks"></a>Bemerkungen

Extrahiert und gibt das gekapselte `VARIANT`zurück und löscht dann das `_variant_t` Objekt, ohne es zu zerstören. Diese Member-Funktion entfernt die `VARIANT` aus der Kapselung und legt die `VARTYPE` dieses `_variant_t` Objekts auf VT_EMPTY fest. Sie müssen die zurückgegebenen `VARIANT` freigeben, indem Sie die [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear) -Funktion aufrufen.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_variant_t-Klasse](../cpp/variant-t-class.md)
