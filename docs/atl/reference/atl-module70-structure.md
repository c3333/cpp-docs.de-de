---
title: _ATL_MODULE70 Struktur
ms.date: 11/04/2016
f1_keywords:
- _ATL_MODULE70
- ATL::_ATL_MODULE70
- ATL._ATL_MODULE70
helpviewer_keywords:
- ATL_MODULE70 structure
- _ATL_MODULE70 structure
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
ms.openlocfilehash: 8d39cdd281e09cdfe09546627aa630a11d12464e
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168565"
---
# <a name="_atl_module70-structure"></a>_ATL_MODULE70 Struktur

Enthält Daten, die von jedem ATL-Modul verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
struct _ATL_MODULE70 {
    UINT cbSize;
    LONG m_nLockCnt;
    _ATL_TERMFUNC_ELEM* m_pTermFuncs;
    CComCriticalSection m_csStaticDataInitAndTypeInfo;
};
```

## <a name="members"></a>Member

`cbSize`<br/>
Die Größe der-Struktur, die für die Versionsverwaltung verwendet wird.

`m_nLockCnt`<br/>
Verweis Zähler, um zu bestimmen, wie lange das Modul aktiv bleiben soll.

`m_pTermFuncs`<br/>
Verfolgt Funktionen, die registriert wurden, um aufgerufen zu werden, wenn ATL heruntergefahren wird.

`m_csStaticDataInitAndTypeInfo`<br/>
Wird verwendet, um den Zugriff auf interne Daten in Multithread-Situationen zu koordinieren.

## <a name="remarks"></a>Bemerkungen

[_ATL_MODULE](atl-typedefs.md#_atl_module) ist als typedef von `_ATL_MODULE70`definiert.

## <a name="requirements"></a>Anforderungen

**Header:** atlbase. h

## <a name="see-also"></a>Weitere Informationen:

[Klassen und Strukturen](../../atl/reference/atl-classes.md)
