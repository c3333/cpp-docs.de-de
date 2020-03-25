---
title: _bstr_t::GetAddress
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetAddress
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
ms.openlocfilehash: ca78bd1b607ba4a86bbc824887a7ec767cd5476e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181251"
---
# <a name="_bstr_tgetaddress"></a>_bstr_t::GetAddress

**Microsoft-spezifisch**

Setzt etwaig vorhandene Zeichenfolgen frei und gibt die Adresse einer neu zugeordneten Zeichenfolge zurück.

## <a name="syntax"></a>Syntax

```
BSTR* GetAddress( );
```

## <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den `BSTR` umschlossen von `_bstr_t`.

## <a name="remarks"></a>Bemerkungen

**GetAddress** wirkt sich auf alle `_bstr_t` Objekte aus, die eine `BSTR`gemeinsam verwenden. Mehrere `_bstr_t` können eine `BSTR` mithilfe des Kopierkonstruktors und des **Operators =** gemeinsam verwenden.

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von **GetAddress**finden Sie unter [_bstr_t:: Assign](../cpp/bstr-t-assign.md) .

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_bstr_t-Klasse](../cpp/bstr-t-class.md)
