---
title: _variant_t-Extraktoren
ms.date: 11/04/2016
f1_keywords:
- _variant_t.operatordouble
- operatorlong
- _variant_t::operator_bstr_t
- operatordouble
- _variant_t.operatorCY
- operatorCY
- _variant_t::operatorCY
- _variant_t::operatordouble
- operatorfloat
- operatorBYTE
- _variant_t.operatorDECIMAL
- _variant_t::operatorlong
- operatorIDispatch
- _variant_t.operatorBYTE
- operatorDECIMAL
- _variant_t.operator_bstr_t
- _variant_t::operatorDECIMAL
- _variant_t.operatorIUnknown
- _variant_t.operatorlong
- _variant_t::operatorIDispatch
- _variant_t::operatorIUnknown
- operatorIUnknown
- _variant_t.operatorbool
- _variant_t::operatorBYTE
- _variant_t.operatorfloat
- operator_bstr_t
- _variant_t::operatorbool
- operatorshort
- _variant_t::operatorshort
- _variant_t::operatorfloat
- _variant_t.operatorIDispatch
- _variant_t.operatorshort
helpviewer_keywords:
- extractors, _variant_t class
- operator CY
- operator IDispatch
- operator SHORT
- operator double
- operator long
- operator _bstr_t
- operator DECIMAL
- operator float
- operator bool
- operator BYTE
- operator IUnknown
ms.assetid: 33c1782f-045a-4673-9619-1d750efc83a9
ms.openlocfilehash: a1b7c713b5d82ff54250b622f2d4afe17abac468
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87185605"
---
# <a name="_variant_t-extractors"></a>_variant_t-Extraktoren

**Microsoft-spezifisch**

Extrahieren Sie Daten aus dem gekapselten `VARIANT` Objekt.

## <a name="syntax"></a>Syntax

```
operator short( ) const;
operator long( ) const;
operator float( ) const;
operator double( ) const;
operator CY( ) const;
operator _bstr_t( ) const;
operator IDispatch*( ) const;
operator bool( ) const;
operator IUnknown*( ) const;
operator DECIMAL( ) const;
operator BYTE( ) const;
operator VARIANT() const throw();
operator char() const;
operator unsigned short() const;
operator unsigned long() const;
operator int() const;
operator unsigned int() const;
operator __int64() const;
operator unsigned __int64() const;
```

## <a name="remarks"></a>Bemerkungen

Extrahiert Rohdaten aus einem gekapselten `VARIANT` . Wenn `VARIANT` nicht bereits der richtige Typ ist, `VariantChangeType` wird verwendet, um eine Konvertierung zu versuchen, und bei einem Fehler wird ein Fehler generiert:

- **Operator Short ()** Extrahiert einen **`short`** ganzzahligen Wert.

- **Operator Long ()** Extrahiert einen **`long`** ganzzahligen Wert.

- **Operator float ()** Extrahiert einen **`float`** numerischen Wert.

- **Operator Double ()** Extrahiert einen **`double`** ganzzahligen Wert.

- **Operator CY ()** Extrahiert ein- `CY` Objekt.

- **Operator bool ()** Extrahiert einen **`bool`** Wert.

- **Operator Decimal ()** Extrahiert einen `DECIMAL` Wert.

- **Operator Byte ()** Extrahiert einen `BYTE` Wert.

- **Operator _bstr_t ()** Extrahiert eine Zeichenfolge, die in einem-Objekt gekapselt ist `_bstr_t` .

- der **Operator IDispatch \* ()** extrahiert einen dispinterface-Zeiger aus einem gekapselten `VARIANT` . `AddRef`wird für den resultierenden Zeiger aufgerufen, sodass Sie aufrufen können, `Release` um ihn freizugeben.

- der **Operator IUnknown \* ()** extrahiert einen COM-Schnittstellen Zeiger aus einem gekapselten `VARIANT` . `AddRef`wird für den resultierenden Zeiger aufgerufen, sodass Sie aufrufen können, `Release` um ihn freizugeben.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[_variant_t-Klasse](../cpp/variant-t-class.md)
