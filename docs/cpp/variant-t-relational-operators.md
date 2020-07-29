---
title: _variant_t-Operatoren (relational)
ms.date: 11/04/2016
f1_keywords:
- _variant_t::operator==
- _variant_t::operator!=
helpviewer_keywords:
- '!= operator'
- relational operators [C++], _variant_t class
- operator!= [C++], variant
- operator!= [C++], relational operators
- operator != [C++], variant
- operator == [C++], variant
- operator== [C++], variant
- operator != [C++], relational operators
- == operator [C++], with specific Visual C++ objects
ms.assetid: 141bacb8-41a2-44dd-b3c0-4ad1f884f4ea
ms.openlocfilehash: 6e0296a2bf4ce97e41fdf6208c3dd1c6b91215dc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226938"
---
# <a name="_variant_t-relational-operators"></a>_variant_t-Operatoren (relational)

**Microsoft-spezifisch**

Überprüft zwei `_variant_t`-Objekte auf Gleichheit bzw. Ungleichheit.

## <a name="syntax"></a>Syntax

```
bool operator==(
   const VARIANT& varSrc) const;
bool operator==(
   const VARIANT* pSrc) const;
bool operator!=(
   const VARIANT& varSrc) const;
bool operator!=(
   const VARIANT* pSrc) const;
```

#### <a name="parameters"></a>Parameter

*varSrc*<br/>
Ein `VARIANT` , der mit dem-Objekt verglichen werden soll `_variant_t` .

*pSrc*<br/>
Ein Zeiger auf den `VARIANT` , der mit dem-Objekt verglichen werden soll `_variant_t` .

## <a name="return-value"></a>Rückgabewert

Gibt zurück **`true`** , wenn der Vergleich den Wert enthält, **`false`** andernfalls.

## <a name="remarks"></a>Bemerkungen

Vergleicht ein- `_variant_t` Objekt mit einem `VARIANT` und testet auf Gleichheit oder Ungleichheit.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[_variant_t-Klasse](../cpp/variant-t-class.md)
