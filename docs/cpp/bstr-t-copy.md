---
title: _bstr_t::copy
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::copy
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
ms.openlocfilehash: b6029e98e83b171d9ab9f8f3f0282fa3f46ca167
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227594"
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
**`true`** Gibt an, dass **Copy** eine Kopie der enthaltenen zurückgibt `BSTR` , andernfalls wird der tatsächliche BSTR **copy** -Wert zurückgegeben.

## <a name="remarks"></a>Bemerkungen

Gibt eine neu zugeordnete Kopie des gekapselten `BSTR`-Objekts zurück.

## <a name="example"></a>Beispiel

```cpp
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t
   *pVal = m_bsConStr.copy();
}
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[_bstr_t-Klasse](../cpp/bstr-t-class.md)
