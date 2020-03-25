---
title: _bstr_t::GetBSTR
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetBSTR
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
ms.openlocfilehash: da438c65256d9a7e5bf5b02e108fee1385171d2d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181212"
---
# <a name="_bstr_tgetbstr"></a>_bstr_t::GetBSTR

**Microsoft-spezifisch**

Zeigt auf den Anfang des `BSTR`, das vom `_bstr_t` umschlossen ist.

## <a name="syntax"></a>Syntax

```
BSTR& GetBSTR( );
```

## <a name="return-value"></a>Rückgabewert

Der Anfang des `BSTR`, der vom `_bstr_t` umschlossen ist.

## <a name="remarks"></a>Bemerkungen

**GetBSTR** wirkt sich auf alle `_bstr_t` Objekte aus, die eine `BSTR`gemeinsam verwenden. Mehrere `_bstr_t` können eine `BSTR` mithilfe des Kopierkonstruktors und des **Operators =** gemeinsam verwenden.

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von **GetBSTR**finden Sie unter [_bstr_t:: Assign](../cpp/bstr-t-assign.md) .

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_bstr_t-Klasse](../cpp/bstr-t-class.md)
