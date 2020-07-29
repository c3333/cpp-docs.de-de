---
title: _bstr_t::_bstr_t
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::_bstr_t
helpviewer_keywords:
- BSTR object
- _bstr_t method [C++]
- _bstr_t class
ms.assetid: 116d994e-5a72-4351-afbe-866c80b4c165
ms.openlocfilehash: 843d6aa0e04595143d7da585e95d58e97fe80db0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221834"
---
# <a name="_bstr_t_bstr_t"></a>_bstr_t::_bstr_t

**Microsoft-spezifisch**

Erstellt ein `_bstr_t`-Objekt.

## <a name="syntax"></a>Syntax

```
_bstr_t( ) throw( );
_bstr_t(
   const _bstr_t& s1
) throw( );
_bstr_t(
   const char* s2
);
_bstr_t(
   const wchar_t* s3
);
_bstr_t(
   const _variant_t& var
);
_bstr_t(
   BSTR bstr,
   bool fCopy
);
```

#### <a name="parameters"></a>Parameter

*S1*<br/>
Ein `_bstr_t`-Objekt, das kopiert werden soll.

*S2*<br/>
Eine Mehrbytezeichenfolge.

*S3*<br/>
Eine Unicode-Zeichenfolge

*var*<br/>
Ein [_variant_t](../cpp/variant-t-class.md) -Objekt.

*bstr*<br/>
Ein vorhandenes `BSTR`-Objekt.

*Kopie*<br/>
**`false`** Gibt an, dass das *BSTR* -Argument an das neue-Objekt angefügt wird, ohne eine Kopie durch Aufrufen von zu erstellen `SysAllocString` .

## <a name="remarks"></a>Bemerkungen

In der folgenden Tabelle werden die `_bstr_t`-Konstruktoren beschrieben.

|Konstruktor|BESCHREIBUNG|
|-----------------|-----------------|
|`_bstr_t( )`|Erstellt ein Standard `_bstr_t` Objekt, das ein NULL- `BSTR` Objekt kapselt.|
|`_bstr_t( _bstr_t&`  `s1`  `)`|Erstellt ein `_bstr_t`-Objekt als Kopie eines anderen.<br /><br /> Dies ist eine *flache* Kopie, bei der der Verweis Zähler des gekapselten Objekts erhöht wird, `BSTR` anstatt einen neuen zu erstellen.|
|`_bstr_t( char*`  `s2`  `)`|Erstellt ein `_bstr_t`-Objekt durch Aufrufen von `SysAllocString`, um ein neues `BSTR`-Objekt zu erstellen und es dann zu kapseln.<br /><br /> Dieser Konstruktor führt zuerst eine Konvertierung von Multibyte in Unicode aus.|
|`_bstr_t( wchar_t*`  `s3`  `)`|Erstellt ein `_bstr_t`-Objekt durch Aufrufen von `SysAllocString`, um ein neues `BSTR`-Objekt zu erstellen und es dann zu kapseln.|
|`_bstr_t( _variant_t&`  `var`  `)`|Erstellt ein `_bstr_t`-Objekt aus einem `_variant_t`-Objekt, indem zunächst ein `BSTR`-Objekt aus dem gekapselten VARIANT-Objekt abgerufen wird.|
|`_bstr_t( BSTR`  `bstr` `, bool`  `fCopy`  `)`|Erstellt ein `_bstr_t`-Objekt aus einem vorhandenen `BSTR` (im Gegensatz zu einer `wchar_t*`-Zeichenfolge). Wenn *fCopy* auf false festgelegt ist, wird der angegebene `BSTR` an das neue-Objekt angefügt, ohne eine neue Kopie mit zu erstellen `SysAllocString` .<br /><br /> Dieser Konstruktor wird von Wrapperfunktionen in Typbibliothekheadern verwendet, um den von einer Schnittstellenmethode zurückgegebenen `BSTR` zu kapseln und dessen Besitz zu übernehmen.|

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[_bstr_t-Klasse](../cpp/bstr-t-class.md)<br/>
[_variant_t-Klasse](../cpp/variant-t-class.md)
