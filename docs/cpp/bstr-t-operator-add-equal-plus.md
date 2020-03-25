---
title: _bstr_t::operator +=, +
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::operator+
- _bstr_t::operator+=
helpviewer_keywords:
- += operator [C++], appending strings
- + operator [C++], _bstr_t objects
ms.assetid: d28316ce-c2c8-4a38-bdb3-44fa4e582c44
ms.openlocfilehash: b9eddca85d66f4978e1b33299ca655cd880cf45e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181147"
---
# <a name="_bstr_toperator--"></a>_bstr_t::operator +=, +

**Microsoft-spezifisch**

Fügt Zeichen am Ende des `_bstr_t`-Objekts hinzu oder verkettet zwei Zeichenfolgen.

## <a name="syntax"></a>Syntax

```
_bstr_t& operator+=( const _bstr_t& s1 );
_bstr_t operator+( const _bstr_t& s1 );
friend _bstr_t operator+( const char* s2, const _bstr_t& s1);
friend _bstr_t operator+( const wchar_t* s3, const _bstr_t& s1);
```

#### <a name="parameters"></a>Parameter

*s1*<br/>
Ein `_bstr_t` -Objekt.

*s2*<br/>
Eine Mehrbytezeichenfolge.

*S3*<br/>
Eine Unicode-Zeichenfolge.

## <a name="remarks"></a>Bemerkungen

Diese Operatoren führen eine Zeichenfolgenverkettung aus:

- **Operator + = (**  *S1*  **)** Fügt die Zeichen in der gekapselten `BSTR` von *S1* an das Ende der gekapselten `BSTR`dieses Objekts an.

- **Operator + (**  *S1*  **)** Gibt die neue `_bstr_t` zurück, die durch Verkettung des `BSTR` dieses Objekts mit dem von *S1*gebildet wird.

- **Operator + (**  *S2*  **&#124;**  *S1*  **)** Gibt eine neue `_bstr_t` zurück, die durch Verkettung einer in Unicode konvertierten Multibytezeichen-Zeichenfolge *S2*gebildet wird, wobei die `BSTR` in *S1*gekapselt ist.

- **Operator + (** *S3* **,** *S1* **)** Gibt eine neue `_bstr_t` zurück, die durch Verkettung einer Unicode-Zeichenfolge *S3* mit der in *S1*gekapselten `BSTR` gebildet wird.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_bstr_t-Klasse](../cpp/bstr-t-class.md)
