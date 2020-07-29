---
title: _variant_t::_variant_t
ms.date: 11/04/2016
f1_keywords:
- _variant_t::_variant_t
helpviewer_keywords:
- _variant_t class [C++], constructor
- _variant_t method [C++]
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
ms.openlocfilehash: 50c10eb4ff617f4bcdc69d2e1781a9920b9eb0e5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233560"
---
# <a name="_variant_t_variant_t"></a>_variant_t::_variant_t

**Microsoft-spezifisch**

Erstellt ein `_variant_t`-Objekt.

## <a name="syntax"></a>Syntax

```
_variant_t( ) throw( );

_variant_t(
   const VARIANT& varSrc
);

_variant_t(
   const VARIANT* pVarSrc
);

_variant_t(
   const _variant_t& var_t_Src
);

_variant_t(
   VARIANT& varSrc,
   bool fCopy
);

_variant_t(
   short sSrc,
   VARTYPE vtSrc = VT_I2
);

_variant_t(
   long lSrc,
   VARTYPE vtSrc = VT_I4
);

_variant_t(
   float fltSrc
) throw( );

_variant_t(
   double dblSrc,
   VARTYPE vtSrc = VT_R8
);

_variant_t(
   const CY& cySrc
) throw( );

_variant_t(
   const _bstr_t& bstrSrc
);

_variant_t(
   const wchar_t *wstrSrc
);

_variant_t(
   const char* strSrc
);

_variant_t(
   IDispatch* pDispSrc,
   bool fAddRef = true
) throw( );

_variant_t(
   bool bSrc
) throw( );

_variant_t(
   IUnknown* pIUknownSrc,
   bool fAddRef = true
) throw( );

_variant_t(
   const DECIMAL& decSrc
) throw( );

_variant_t(
   BYTE bSrc
) throw( );

variant_t(
   char cSrc
) throw();

_variant_t(
   unsigned short usSrc
) throw();

_variant_t(
   unsigned long ulSrc
) throw();

_variant_t(
   int iSrc
) throw();

_variant_t(
   unsigned int uiSrc
) throw();

_variant_t(
   __int64 i8Src
) throw();

_variant_t(
   unsigned __int64 ui8Src
) throw();
```

#### <a name="parameters"></a>Parameter

*varSrc*<br/>
Ein `VARIANT`-Objekt, das in das neue `_variant_t`-Objekt kopiert werden soll.

*pVarSrc*<br/>
Zeiger auf ein- `VARIANT` Objekt, das in das neue-Objekt kopiert werden soll `_variant_t` .

*var_t_Src*<br/>
Ein `_variant_t`-Objekt, das in das neue `_variant_t`-Objekt kopiert werden soll.

*Kopie*<br/>
**`false`** Gibt an, dass das angegebene- `VARIANT` Objekt an das neue-Objekt angefügt wird, `_variant_t` ohne dass eine neue Kopie durch eine Kopie `VariantCopy`

*ISrc, sSrc*<br/>
Ein ganzer Wert, der in das neue `_variant_t` -Objekt kopiert werden soll.

*VFS*<br/>
Der `VARTYPE` für das neue- `_variant_t` Objekt.

*fltSrc, dblSrc*<br/>
Ein in das neue `_variant_t`-Objekt zu kopierender numerischer Wert.

*cysrc*<br/>
Ein `CY`-Objekt, das in das neue `_variant_t`-Objekt kopiert werden soll.

*bstrausrc*<br/>
Ein `_bstr_t`-Objekt, das in das neue `_variant_t`-Objekt kopiert werden soll.

*strSrc, wstrSrc*<br/>
Eine Zeichenfolge, die in das neue `_variant_t`-Objekt kopiert werden soll.

*bsrc*<br/>
Ein **`bool`** Wert, der in das neue-Objekt kopiert werden soll `_variant_t` .

*piuknownsrc*<br/>
Ein COM-Schnittstellen Zeiger auf ein VT_UNKNOWN Objekt, das in das neue-Objekt gekapselt werden soll `_variant_t` .

*pdispsrc*<br/>
Ein COM-Schnittstellen Zeiger auf ein VT_DISPATCH Objekt, das in das neue-Objekt gekapselt werden soll `_variant_t` .

*decsrc*<br/>
Ein `DECIMAL`-Wert, der in das neue `_variant_t`-Objekt kopiert werden soll.

*bsrc*<br/>
Ein `BYTE`-Wert, der in das neue `_variant_t`-Objekt kopiert werden soll.

*CSRC*<br/>
Ein **`char`** Wert, der in das neue-Objekt kopiert werden soll `_variant_t` .

*usSrc*<br/>
Ein **`unsigned short`** Wert, der in das neue-Objekt kopiert werden soll `_variant_t` .

*ulsrc*<br/>
Ein **`unsigned long`** Wert, der in das neue-Objekt kopiert werden soll `_variant_t` .

*ISRC*<br/>
Ein- **`int`** Wert, der in das neue-Objekt kopiert werden soll `_variant_t` .

*uiSrc*<br/>
Ein- **`unsigned int`** Wert, der in das neue-Objekt kopiert werden soll `_variant_t` .

*i8Src*<br/>
Ein- **`__int64`** Wert, der in das neue-Objekt kopiert werden soll `_variant_t` .

*ui8Src*<br/>
Ein **__int64 Wert ohne** Vorzeichen, der in das neue-Objekt kopiert werden soll `_variant_t` .

## <a name="remarks"></a>Bemerkungen

- **_variant_t ()** Erstellt ein leeres- `_variant_t` Objekt, `VT_EMPTY` .

- **_variant_t (Variant&** *varSrc***)** Erstellt ein- `_variant_t` Objekt aus einer Kopie des- `VARIANT` Objekts.     Der Varianttyp wird beibehalten.

- **_variant_t (Variant** <strong>\*</strong> *pvarSrc***)** erstellt ein- `_variant_t` Objekt aus einer Kopie des- `VARIANT` Objekts.     Der Varianttyp wird beibehalten.

- **_variant_t (_variant_t&** *var_t_Src***)** Erstellt ein- `_variant_t` Objekt aus einem anderen- `_variant_t` Objekt.     Der Varianttyp wird beibehalten.

- **_variant_t (Variant&** *varSrc* **, bool** `fCopy` **)** erstellt ein- `_variant_t` Objekt aus einem vorhandenen- `VARIANT` Objekt.       Wenn *fCopy* den Wert **`false`** hat, wird das **Variant** -Objekt an das neue Objekt angefügt, ohne eine Kopie zu erstellen.

- **_variant_t (Short***SSRC* **, VarType** `vtSrc` **= VT_I2)** erstellt ein- `_variant_t` Objekt vom Typ VT_I2 oder VT_BOOL aus einem **`short`** ganzzahligen Wert.       Alle anderen `VARTYPE` Ergebnisse führen zu einem E_INVALIDARG Fehler.

- **_variant_t (Long** `lSrc` **, VarType** `vtSrc` **= VT_I4)** erstellt ein- `_variant_t` Objekt vom Typ VT_I4, VT_BOOL oder VT_ERROR aus einem **`long`** ganzzahligen Wert.       Alle anderen `VARTYPE` Ergebnisse führen zu einem E_INVALIDARG Fehler.

- **_variant_t (float** `fltSrc` **)** erstellt ein- `_variant_t` Objekt vom Typ VT_R4 aus einem **`float`** numerischen Wert.    

- **_variant_t (Double** `dblSrc` **, VarType** `vtSrc` **= VT_R8)** erstellt ein- `_variant_t` Objekt vom Typ VT_R8 oder VT_DATE aus einem **`double`** numerischen Wert.       Alle anderen `VARTYPE` Ergebnisse führen zu einem E_INVALIDARG Fehler.

- **_variant_t (CY&** `cySrc` **)** erstellt ein- `_variant_t` Objekt vom Typ VT_CY aus einem- `CY` Objekt.    

- **_variant_t (_bstr_t&** `bstrSrc` **)** erstellt ein- `_variant_t` Objekt vom Typ VT_BSTR aus einem- `_bstr_t` Objekt.     Ein neues `BSTR` wird zugeordnet.

- **_variant_t (wchar_t** <strong>\*</strong> *wstrausrc*  **)** erstellt ein- `_variant_t` Objekt vom Typ VT_BSTR aus einer Unicode-Zeichenfolge. Ein neues `BSTR` wird zugeordnet.

- **_variant_t (Char** <strong>\*</strong> `strSrc` **)** Erstellt ein- `_variant_t` Objekt vom Typ VT_BSTR aus einer Zeichenfolge.     Ein neues `BSTR` wird zugeordnet.

- **_variant_t (bool** `bSrc` **)** erstellt ein- `_variant_t` Objekt vom Typ VT_BOOL aus einem **`bool`** Wert.    

- **_variant_t (IUnknown** <strong>\*</strong> `pIUknownSrc` **, bool** `fAddRef` **= true)** Erstellt ein- `_variant_t` Objekt vom Typ VT_UNKNOWN aus einem COM-Schnittstellen Zeiger.       Wenn `fAddRef` ist **`true`** , `AddRef` wird für den angegebenen Schnittstellen Zeiger aufgerufen, um den Aufruf von abzugleichen, der `Release` auftritt, wenn das `_variant_t` Objekt zerstört wird. Sie müssen für `Release` den angegebenen Schnittstellen Zeiger aufzurufen. Wenn `fAddRef` ist **`false`** , übernimmt dieser Konstruktor den Besitz des angegebenen Schnittstellen Zeigers und ruft nicht `Release` für den bereitgestellten Schnittstellen Zeiger auf.

- **_variant_t (IDispatch)** <strong>\*</strong> `pDispSrc` **, bool** `fAddRef` **= true)** Erstellt ein- `_variant_t` Objekt vom Typ VT_DISPATCH aus einem COM-Schnittstellen Zeiger.       Wenn `fAddRef` ist **`true`** , `AddRef` wird für den angegebenen Schnittstellen Zeiger aufgerufen, um den Aufruf von abzugleichen, der `Release` auftritt, wenn das `_variant_t` Objekt zerstört wird. Sie müssen für `Release` den angegebenen Schnittstellen Zeiger aufzurufen. Wenn `fAddRef` ist **`false`** , übernimmt dieser Konstruktor den Besitz des angegebenen Schnittstellen Zeigers und ruft nicht `Release` für den bereitgestellten Schnittstellen Zeiger auf.

- **_variant_t (Decimal&** `decSrc` **)** erstellt ein- `_variant_t` Objekt vom Typ VT_DECIMAL von einem- `DECIMAL` Wert.    

- **_variant_t (Byte** `bSrc` **)** erstellt ein- `_variant_t` Objekt `VT_UI1` vom Typ aus einem `BYTE` Wert.    

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[_variant_t-Klasse](../cpp/variant-t-class.md)
