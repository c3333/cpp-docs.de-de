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
ms.openlocfilehash: e0d7ea1a0bcaf8329cff0cdfb0c01154f3c5a73b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187569"
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
Eine `VARIANT`, die mit dem `_variant_t` Objekt verglichen werden soll.

*pSrc*<br/>
Ein Zeiger auf den `VARIANT`, der mit dem `_variant_t` Objekt verglichen werden soll.

## <a name="return-value"></a>Rückgabewert

Gibt **true** zurück, wenn der Vergleich den Wert enthält, andernfalls **false** .

## <a name="remarks"></a>Bemerkungen

Vergleicht ein `_variant_t` Objekt mit einem `VARIANT`und testet auf Gleichheit oder Ungleichheit.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_variant_t-Klasse](../cpp/variant-t-class.md)
