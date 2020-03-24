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
ms.openlocfilehash: 685df7285e58e0cf2ceeded5ac27641364897298
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187699"
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

Extrahiert Rohdaten aus einem gekapselten `VARIANT`. Wenn die `VARIANT` nicht bereits den richtigen Typ hat, wird `VariantChangeType` verwendet, um eine Konvertierung zu versuchen, und bei einem Fehler wird ein Fehler generiert:

- **Operator Short ()** Extrahiert einen **kurzen** ganzzahligen Wert.

- **Operator Long ()** Extrahiert einen **Long** Integer-Wert.

- **Operator float ()** Extrahiert einen numerischen **float** -Wert.

- **Operator Double ()** Extrahiert einen **doppelten** ganzzahligen Wert.

- **Operator CY ()** Extrahiert ein `CY`-Objekt.

- **Operator bool ()** Extrahiert einen **booleschen** Wert.

- **Operator Decimal ()** Extrahiert einen `DECIMAL` Wert.

- **Operator Byte ()** Extrahiert einen `BYTE` Wert.

- **Operator _bstr_t ()** Extrahiert eine Zeichenfolge, die in einem `_bstr_t` Objekt gekapselt ist.

- **Operator IDispatch\*()** Extrahiert einen dispinterface-Zeiger aus einem gekapselten `VARIANT`. `AddRef` für den resultierenden Zeiger aufgerufen wird, müssen Sie `Release` aufrufen, um Sie freizugeben.

- **Operator IUnknown\*()** Extrahiert einen COM-Schnittstellen Zeiger aus einem gekapselten `VARIANT`. `AddRef` für den resultierenden Zeiger aufgerufen wird, müssen Sie `Release` aufrufen, um Sie freizugeben.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_variant_t-Klasse](../cpp/variant-t-class.md)
