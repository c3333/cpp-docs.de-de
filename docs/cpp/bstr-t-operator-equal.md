---
title: _bstr_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::operator=
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
ms.openlocfilehash: 5b7f499dd84a67020232aab84966647378daadad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181069"
---
# <a name="_bstr_toperator-"></a>_bstr_t::operator =

**Microsoft-spezifisch**

Weist einem vorhandenen `_bstr_t`-Objekt einen neuen Wert zu.

## <a name="syntax"></a>Syntax

```
_bstr_t& operator=(const _bstr_t& s1) throw ( );
_bstr_t& operator=(const char* s2);
_bstr_t& operator=(const wchar_t* s3);
_bstr_t& operator=(const _variant_t& var);
```

#### <a name="parameters"></a>Parameter

*s1*<br/>
Ein `_bstr_t`-Objekt, das einem vorhandenen `_bstr_t`-Objekt zugewiesen werden soll.

*s2*<br/>
Eine Multibyte-Zeichenfolge, die einem vorhandenen `_bstr_t` Objekt zugewiesen werden soll.

*S3*<br/>
Eine Unicode-Zeichenfolge, die einem vorhandenen `_bstr_t` Objekt zugewiesen werden soll.

*var*<br/>
Ein `_variant_t`-Objekt, das einem vorhandenen `_bstr_t`-Objekt zugewiesen werden soll.

**Ende Microsoft-spezifisch**

## <a name="example"></a>Beispiel

Unter [_bstr_t:: Assign](../cpp/bstr-t-assign.md) finden Sie ein Beispiel für die Verwendung von **Operator =** .

## <a name="see-also"></a>Weitere Informationen

[_bstr_t-Klasse](../cpp/bstr-t-class.md)
