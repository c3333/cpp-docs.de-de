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
ms.openlocfilehash: 402251592a87b723d75fd1b2cd0786be7b17dbfc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187621"
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

- **Operator = (** *varSrc* **)** Weist einem `_variant_t` Objekt eine vorhandene `VARIANT` zu.

- **Operator = (** *pvarSrc* **)** Weist einem `_variant_t` Objekt eine vorhandene `VARIANT` zu.

- **Operator = (** *var_t_Src* **)** Weist einem `_variant_t`-Objekt ein vorhandenes `_variant_t`-Objekt zu.

- **Operator = (** *SSRC* **)** Weist einem `_variant_t`-Objekt einen **kurzen** ganzzahligen Wert zu.

- **Operator = (** `lSrc` **)** Weist einem `_variant_t`-Objekt einen **langen** ganzzahligen Wert zu.

- **Operator = (** *flgsrc* **)** Weist einem `_variant_t`-Objekt einen numerischen **float** -Wert zu.

- **Operator = (** *dblsrc* **)** Weist einem `_variant_t`-Objekt einen **doppelten** numerischen Wert zu.

- **Operator = (** *cysrc* **)** Weist einem `_variant_t`-Objekt ein `CY`-Objekt zu.

- **Operator = (** *bstrausrc* **)** Weist einem `_variant_t`-Objekt ein `BSTR`-Objekt zu.

- **Operator = (**  *wstrinsrc*  **)** Weist einer `_variant_t`-Objekt eine Unicode-Zeichenfolge zu.

- **Operator = (** `strSrc` **)** Weist einer `_variant_t`-Objekt eine Multibytezeichenfolge zu.

- **Operator = (** `bSrc` **)** Weist einem `_variant_t` Objekt einen **booleschen** Wert zu.

- **Operator = (** *pdispsrc* **)** Weist einem `_variant_t`-Objekt ein `VT_DISPATCH`-Objekt zu.

- **Operator = (** *piunknownsrc* **)** Weist einem `_variant_t`-Objekt ein `VT_UNKNOWN`-Objekt zu.

- **Operator = (** *decsrc* **)** Weist einem `_variant_t`-Objekt einen `DECIMAL` Wert zu.

- **Operator = (** `bSrc` **)** Weist einem `_variant_t`-Objekt einen `BYTE` Wert zu.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_variant_t-Klasse](../cpp/variant-t-class.md)
