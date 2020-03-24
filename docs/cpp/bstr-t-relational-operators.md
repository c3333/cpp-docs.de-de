---
title: _bstr_t-Operatoren (relational)
ms.date: 05/07/2019
f1_keywords:
- _bstr_t::operator>
- _bstr_t::operator==
- _bstr_t::operator>=
- _bstr_t::operator!=
- _bstr_t::operator<
- _bstr_t::operator<=
- _bstr_t::operator!
helpviewer_keywords:
- _bstr_t [C++]
ms.assetid: e153da72-37c3-4d8a-b8eb-730d65da64dd
ms.openlocfilehash: a4126eb7771e17db5fb813898d6fa4917f6983bb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190312"
---
# <a name="_bstr_t-relational-operators"></a>_bstr_t-Operatoren (relational)

**Microsoft-spezifisch**

Vergleicht zwei `_bstr_t`-Objekte.

## <a name="syntax"></a>Syntax

```
bool operator!( ) const throw( );
bool operator==(const _bstr_t& str) const throw( );
bool operator!=(const _bstr_t& str) const throw( );
bool operator<(const _bstr_t& str) const throw( );
bool operator>(const _bstr_t& str) const throw( );
bool operator<=(const _bstr_t& str) const throw( );
bool operator>=(const _bstr_t& str) const throw( );
```

## <a name="remarks"></a>Bemerkungen

Diese Operatoren vergleichen zwei `_bstr_t`-Objekte auf lexikografischer Ebene. Die Operatoren geben true zurück, wenn die Vergleiche enthalten; andernfalls wird false zurückgegeben.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_bstr_t-Klasse](../cpp/bstr-t-class.md)
