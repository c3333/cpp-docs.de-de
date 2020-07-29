---
title: _AtlCreateWndData Struktur
ms.date: 11/04/2016
f1_keywords:
- ATL::_AtlCreateWndData
- ATL._AtlCreateWndData
- _AtlCreateWndData
helpviewer_keywords:
- _AtlCreateWndData structure
- AtlCreateWndData structure
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
ms.openlocfilehash: a38ddb7e3575e883c11b14a9b01004bb54fcd4a4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230012"
---
# <a name="_atlcreatewnddata-structure"></a>_AtlCreateWndData Struktur

Diese Struktur enthält klasseninstanzdaten in windowingcode in ATL.

## <a name="syntax"></a>Syntax

```cpp
    struct _AtlCreateWndData{
    void* m_pThis;
    DWORD m_dwThreadID;
    _AtlCreateWndData* m_pNext;
};
```

## <a name="members"></a>Member

`m_pThis`<br/>
Der **`this`** Zeiger, der verwendet wird, um in Fenster Prozeduren auf die Klasseninstanz zuzugreifen.

`m_dwThreadID`<br/>
Die Thread-ID der aktuellen Klasseninstanz.

`m_pNext`<br/>
Zeiger auf das nächste- `_AtlCreateWndData` Objekt.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="see-also"></a>Weitere Informationen

[Klassen und Strukturen](../../atl/reference/atl-classes.md)
