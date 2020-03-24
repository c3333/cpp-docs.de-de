---
title: _bstr_t::wchar_t *, _bstr_t::char*
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::wchar_t*
- _bstr_t::char*
helpviewer_keywords:
- operator wchar_t* [C++]
- operator char* [C++]
ms.assetid: acd9f4a7-b427-42c2-aaae-acae21cab317
ms.openlocfilehash: 5fdce29b0be7e9aabae9e3c602822045a7bccafd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190299"
---
# <a name="_bstr_twchar_t-_bstr_tchar"></a>_bstr_t::wchar_t\*, _bstr_t::char\*

**Microsoft-spezifisch**

Gibt die BSTR-Zeichen als Array von schmalen oder breiten Zeichen zurück.

## <a name="syntax"></a>Syntax

```
operator const wchar_t*( ) const throw( );
operator wchar_t*( ) const throw( );
operator const char*( ) const;
operator char*( ) const;
```

## <a name="remarks"></a>Bemerkungen

Diese Operatoren können verwendet werden, um die Zeichendaten zu extrahieren, die vom `BSTR`-Objekt gekapselt werden. Durch die Zuweisung eines neuen Werts zum zurückgegebenen Zeiger werden die ursprünglichen BSTR-Daten nicht geändert.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_bstr_t-Klasse](../cpp/bstr-t-class.md)
