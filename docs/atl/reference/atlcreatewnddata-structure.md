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
ms.openlocfilehash: 6453156a59b73bcb06c7c86920e1dc524874cef8
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168539"
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
Der **this** -Zeiger, der verwendet wird, um in Fenster Prozeduren auf die-Klasseninstanz zuzugreifen.

`m_dwThreadID`<br/>
Die Thread-ID der aktuellen Klasseninstanz.

`m_pNext`<br/>
Zeiger auf das nächste `_AtlCreateWndData` -Objekt.

## <a name="requirements"></a>Anforderungen

**Header:** atlbase. h

## <a name="see-also"></a>Weitere Informationen:

[Klassen und Strukturen](../../atl/reference/atl-classes.md)
