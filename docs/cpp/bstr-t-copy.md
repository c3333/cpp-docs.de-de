---
title: _bstr_t::copy
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::copy
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
ms.openlocfilehash: 1fe8cfb5b644b3c7c34cf3325a91ebdf23a04946
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190325"
---
# <a name="_bstr_tcopy"></a>_bstr_t::copy

**Microsoft-spezifisch**

Erstellt eine Kopie des gekapselten `BSTR`.

## <a name="syntax"></a>Syntax

```
BSTR copy( bool fCopy = true ) const;
```

#### <a name="parameters"></a>Parameter

*Kopie*<br/>
TRUE gibt an, dass **Copy** eine Kopie der enthaltenen `BSTR`zurückgibt, andernfalls gibt **Copy** den tatsächlichen BSTR zurück.

## <a name="remarks"></a>Bemerkungen

Gibt eine neu zugeordnete Kopie des gekapselten `BSTR`-Objekts zurück.

## <a name="example"></a>Beispiel

```cpp
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t
   *pVal = m_bsConStr.copy();
}
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_bstr_t-Klasse](../cpp/bstr-t-class.md)
