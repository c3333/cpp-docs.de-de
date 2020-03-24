---
title: _variant_t::_variant_t
ms.date: 11/04/2016
f1_keywords:
- _variant_t::_variant_t
helpviewer_keywords:
- _variant_t class [C++], constructor
- _variant_t method [C++]
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
ms.openlocfilehash: fff116ef04967a1887eaa075d92d3ea0283d5427
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187530"
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
Ein Zeiger auf ein `VARIANT` Objekt, das in das neue `_variant_t`-Objekt kopiert werden soll.

*var_t_Src*<br/>
Ein `_variant_t`-Objekt, das in das neue `_variant_t`-Objekt kopiert werden soll.

*Kopie*<br/>
Wenn der Wert **false**ist, wird das angegebene `VARIANT` Objekt an das neue `_variant_t`-Objekt angefügt, ohne dass eine neue Kopie von `VariantCopy`wird.

*ISRC, SSRC*<br/>
Ein ganzer Wert, der in das neue `_variant_t` -Objekt kopiert werden soll.

*VFS*<br/>
Der `VARTYPE` für das neue `_variant_t`-Objekt.

*flwahrheits RC, dblsrc*<br/>
Ein in das neue `_variant_t`-Objekt zu kopierender numerischer Wert.

*cysrc*<br/>
Ein `CY`-Objekt, das in das neue `_variant_t`-Objekt kopiert werden soll.

*bstrausrc*<br/>
Ein `_bstr_t`-Objekt, das in das neue `_variant_t`-Objekt kopiert werden soll.

*"Straume", "wstrausrc"*<br/>
Eine Zeichenfolge, die in das neue `_variant_t`-Objekt kopiert werden soll.

*bsrc*<br/>
Ein **boolescher** Wert, der in das neue `_variant_t`-Objekt kopiert werden soll.

*piuknownsrc*<br/>
Ein COM-Schnittstellen Zeiger auf ein VT_UNKNOWN Objekt, das in das neue `_variant_t`-Objekt gekapselt werden soll.

*pdispsrc*<br/>
Ein COM-Schnittstellen Zeiger auf ein VT_DISPATCH Objekt, das in das neue `_variant_t`-Objekt gekapselt werden soll.

*decsrc*<br/>
Ein `DECIMAL`-Wert, der in das neue `_variant_t`-Objekt kopiert werden soll.

*bsrc*<br/>
Ein `BYTE`-Wert, der in das neue `_variant_t`-Objekt kopiert werden soll.

*CSRC*<br/>
Ein **char** -Wert, der in das neue `_variant_t`-Objekt kopiert werden soll.

*ussrc*<br/>
Ein **Kurzwert ohne** Vorzeichen, der in das neue `_variant_t`-Objekt kopiert werden soll.

*ulsrc*<br/>
Ein **Long** -Wert ohne Vorzeichen, der in das neue `_variant_t`-Objekt kopiert werden soll.

*ISRC*<br/>
Ein **int** -Wert, der in das neue `_variant_t`-Objekt kopiert werden soll.

*uisrc*<br/>
Ein **int** -Wert ohne Vorzeichen, der in das neue `_variant_t`-Objekt kopiert werden soll.

*i8Src*<br/>
Ein **__int64** Wert, der in das neue `_variant_t`-Objekt kopiert werden soll.

*ui8Src*<br/>
Ein **__int64 Wert ohne** Vorzeichen, der in das neue `_variant_t`-Objekt kopiert werden soll.

## <a name="remarks"></a>Bemerkungen

- **_variant_t ()** Erstellt ein leeres `_variant_t` Objekt, `VT_EMPTY`.

- **_variant_t (Variant &**  *varSrc*  **)** Erstellt ein `_variant_t`-Objekt aus einer Kopie des `VARIANT` Objekts. Der Varianttyp wird beibehalten.

- **_variant_t (Variant** <strong>\*</strong> *pvarSrc* **)** Erstellt ein `_variant_t`-Objekt aus einer Kopie des `VARIANT` Objekts. Der Varianttyp wird beibehalten.

- **_variant_t (_variant_t &**  *var_t_Src*  **)** Erstellt ein `_variant_t` Objekt aus einem anderen `_variant_t`-Objekt. Der Varianttyp wird beibehalten.

- **_variant_t (Variant &** *varSrc* **, bool**`fCopy` **)** Erstellt ein `_variant_t` Objekt aus einem vorhandenen `VARIANT`-Objekt. Wenn *fCopy* auf **false**festgelegt ist, wird das **Variant** -Objekt an das neue Objekt angefügt, ohne eine Kopie zu erstellen.

- **_variant_t (kurzes***SSRC* **, VarType**`vtSrc` **= VT_I2)** Erstellt ein `_variant_t` Objekt vom Typ VT_I2 oder VT_BOOL aus einem **kurzen** ganzzahligen Wert. Alle anderen `VARTYPE` führen zu einem E_INVALIDARG Fehler.

- **_variant_t (Long**`lSrc` **, VarType**`vtSrc` **= VT_I4)** Erstellt ein `_variant_t` Objekt vom Typ "VT_I4", "VT_BOOL" oder "VT_ERROR" aus einem **Long** Integer-Wert. Alle anderen `VARTYPE` führen zu einem E_INVALIDARG Fehler.

- **_variant_t (float** -`fltSrc` **)** Erstellt ein `_variant_t` Objekt vom Typ VT_R4 **aus einem numerischen** Gleit Komma Wert.

- **_variant_t (Double**`dblSrc` **, VarType**`vtSrc` **= VT_R8)** Erstellt ein `_variant_t` Objekt vom Typ VT_R8 oder VT_DATE aus einem **doppelten** numerischen Wert. Alle anderen `VARTYPE` führen zu einem E_INVALIDARG Fehler.

- **_variant_t (CY &** `cySrc` **)** Erstellt ein `_variant_t` Objekt vom Typ VT_CY aus einem `CY`-Objekt.

- **_variant_t (_bstr_t &** `bstrSrc` **)** Erstellt ein `_variant_t` Objekt vom Typ VT_BSTR aus einem `_bstr_t`-Objekt. Ein neues `BSTR` wird zugeordnet.

- **_variant_t (wchar_t** <strong>\*</strong> *wstrinsrc*  **)** Erstellt ein `_variant_t` Objekt vom Typ, das aus einer Unicode-Zeichenfolge VT_BSTR. Ein neues `BSTR` wird zugeordnet.

- **_variant_t (Char** <strong>\*</strong>`strSrc` **)** Erstellt ein `_variant_t` Objekt vom Typ, das aus einer Zeichenfolge VT_BSTR. Ein neues `BSTR` wird zugeordnet.

- **_variant_t (bool**`bSrc` **)** Erstellt ein `_variant_t` Objekt vom Typ VT_BOOL aus einem **booleschen** Wert.

- **_variant_t (IUnknown** <strong>\*</strong>`pIUknownSrc` **, bool**`fAddRef` **= true)** Erstellt ein `_variant_t` Objekt vom Typ VT_UNKNOWN aus einem COM-Schnittstellen Zeiger. Wenn `fAddRef` **true**ist, wird `AddRef` für den angegebenen Schnittstellen Zeiger aufgerufen, um den Aufruf von `Release` abzugleichen, der auftritt, wenn das `_variant_t` Objekt zerstört wird. Sie müssen `Release` für den angegebenen Schnittstellen Zeiger aufzurufen. Wenn `fAddRef` **false**ist, übernimmt dieser Konstruktor den Besitz des angegebenen Schnittstellen Zeigers. `Release` für den angegebenen Schnittstellen Zeiger nicht aufzurufen.

- **_variant_t (IDispatch** <strong>\*</strong>`pDispSrc` **, bool**`fAddRef` **= true)** Erstellt ein `_variant_t` Objekt vom Typ VT_DISPATCH aus einem COM-Schnittstellen Zeiger. Wenn `fAddRef` **true**ist, wird `AddRef` für den angegebenen Schnittstellen Zeiger aufgerufen, um den Aufruf von `Release` abzugleichen, der auftritt, wenn das `_variant_t` Objekt zerstört wird. Sie müssen `Release` für den angegebenen Schnittstellen Zeiger aufzurufen. Wenn `fAddRef` **false**ist, übernimmt dieser Konstruktor den Besitz des angegebenen Schnittstellen Zeigers. `Release` für den angegebenen Schnittstellen Zeiger nicht aufzurufen.

- **_variant_t (Decimal &** `decSrc` **)** Erstellt ein `_variant_t` Objekt vom Typ VT_DECIMAL aus einem `DECIMAL` Wert.

- **_variant_t (Byte**`bSrc` **)** Erstellt ein `_variant_t` Objekt vom Typ `VT_UI1` aus einem `BYTE` Wert.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_variant_t-Klasse](../cpp/variant-t-class.md)
