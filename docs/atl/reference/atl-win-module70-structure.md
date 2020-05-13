---
title: _ATL_WIN_MODULE70 Struktur
ms.date: 11/04/2016
f1_keywords:
- _ATL_WIN_MODULE70
- ATL::_ATL_WIN_MODULE70
- ATL._ATL_WIN_MODULE70
helpviewer_keywords:
- _ATL_WIN_MODULE70 structure
- ATL_WIN_MODULE70 structure
ms.assetid: a0aaf3ea-ca77-46ec-bd53-4dfb61dffbea
ms.openlocfilehash: 770e78e4ad87338528aa654f5ecaa08b45315846
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168552"
---
# <a name="_atl_win_module70-structure"></a>_ATL_WIN_MODULE70 Struktur

Wird von windowingcode in ATL verwendet.

## <a name="syntax"></a>Syntax

```cpp
struct _ATL_WIN_MODULE70 {
    UNIT cbSize;
    CRITICAL_SECTION m_csWindowCreate;
    _AtlCreateWndData* m_pCreateWndList;
    CSimpleArray<ATOM> m_rgWindowClassAtoms;
};
```

## <a name="members"></a>Member

`cbSize`<br/>
Die Größe der-Struktur, die für die Versionsverwaltung verwendet wird.

`m_csWindowCreate`<br/>
Wird verwendet, um den Zugriff auf den Fenster Registrierungscode zu serialisieren. Wird intern von ATL verwendet.

`m_pCreateWndList`<br/>
Wird verwendet, um Fenster an Ihre Objekte zu binden. Wird intern von ATL verwendet.

`m_rgWindowClassAtoms`<br/>
Wird verwendet, um die Registrierung von Fenster Klassen zu verfolgen, sodass Sie bei Beendigung ordnungsgemäß aufgehoben werden können. Wird intern von ATL verwendet.

## <a name="remarks"></a>Bemerkungen

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module) ist als typedef von `_ATL_WIN_MODULE70`definiert.

## <a name="requirements"></a>Anforderungen

**Header:** atlbase. h

## <a name="see-also"></a>Weitere Informationen:

[Klassen und Strukturen](../../atl/reference/atl-classes.md)
