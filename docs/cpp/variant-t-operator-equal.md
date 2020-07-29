---
title: _variant_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _variant_t::operator=
helpviewer_keywords:
- operator= [C++], variant
- operator = [C++], variant
- = operator [C++], with specific Visual C++ objects
ms.assetid: 77622723-6e49-4dec-9e0f-fa74028f1a3c
ms.openlocfilehash: 2db26a378526cd5f48992cb32ea46e9677125e66
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226957"
---
# <a name="_variant_toperator-"></a>_variant_t::operator =

**Microsoft-spezifisch**

## <a name="syntax"></a>Syntax

```
_variant_t& operator=(
   const VARIANT& varSrc
);

_variant_t& operator=(
   const VARIANT* pVarSrc
);

_variant_t& operator=(
   const _variant_t& var_t_Src
);

_variant_t& operator=(
   short sSrc
);

_variant_t& operator=(
   long lSrc
);

_variant_t& operator=(
   float fltSrc
);

_variant_t& operator=(
   double dblSrc
);

_variant_t& operator=(
   const CY& cySrc
);

_variant_t& operator=(
   const _bstr_t& bstrSrc
);

_variant_t& operator=(
   const wchar_t* wstrSrc
);

_variant_t& operator=(
   const char* strSrc
);

_variant_t& operator=(
   IDispatch* pDispSrc
);

_variant_t& operator=(
   bool bSrc
);

_variant_t& operator=(
   IUnknown* pSrc
);

_variant_t& operator=(
   const DECIMAL& decSrc
);

_variant_t& operator=(
   BYTE bSrc
);

_variant_t& operator=(
   char cSrc
);

_variant_t& operator=(
   unsigned short usSrc
);

_variant_t& operator=(
   unsigned long ulSrc
);

_variant_t& operator=(
   int iSrc
);

_variant_t& operator=(
   unsigned int uiSrc
);

_variant_t& operator=(
   __int64 i8Src
);

_variant_t& operator=(
   unsigned __int64 ui8Src
);
```

## <a name="remarks"></a>Bemerkungen

Der Operator weist dem `_variant_t`-Objekt einen neuen Wert zu:

- **Operator = (**  *varSrc*  **)** Weist einem-Objekt ein vorhandenes `VARIANT` zu `_variant_t` .

- **Operator = (**  *pvarSrc*  **)** Weist einem-Objekt ein vorhandenes `VARIANT` zu `_variant_t` .

- **Operator = (**  *var_t_Src*  **)** Weist ein vorhandenes- `_variant_t` Objekt einem- `_variant_t` Objekt zu.

- **Operator = (**  *SSRC*  **)** Weist einem- **`short`** Objekt einen ganzzahligen Wert zu `_variant_t` .

- **Operator = (** `lSrc` **)** weist einen **`long`** ganzzahligen Wert einem- `_variant_t` Objekt zu.    

- **Operator = (**  *flgsrc*  **)** Weist einem- **`float`** Objekt einen numerischen Wert zu `_variant_t` .

- **Operator = (**  *dblsrc*  **)** Weist einem- **`double`** Objekt einen numerischen Wert zu `_variant_t` .

- **Operator = (**  *cysrc*  **)** Weist ein- `CY` Objekt einem- `_variant_t` Objekt zu.

- **Operator = (**  *bstrausrc*  **)** Weist ein- `BSTR` Objekt einem- `_variant_t` Objekt zu.

- **Operator = (**  *wstrinsrc*  **)** Weist einem-Objekt eine Unicode-Zeichenfolge zu `_variant_t` .

- **Operator = (** `strSrc` **)** weist einem-Objekt eine Multibytezeichenfolge zu `_variant_t` .    

- **Operator = (** `bSrc` **)** weist einem- **`bool`** Objekt einen Wert zu `_variant_t` .  

- **Operator = (**  *pdispsrc*  **)** Weist ein- `VT_DISPATCH` Objekt einem- `_variant_t` Objekt zu.

- **Operator = (**  *piunknownsrc*  **)** Weist ein- `VT_UNKNOWN` Objekt einem- `_variant_t` Objekt zu.

- **Operator = (**  *decsrc*  **)** Weist einem- `DECIMAL` Objekt einen Wert zu `_variant_t` .

- **Operator = (** `bSrc` **)** weist einem- `BYTE` Objekt einen Wert zu `_variant_t` .  

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[_variant_t-Klasse](../cpp/variant-t-class.md)
