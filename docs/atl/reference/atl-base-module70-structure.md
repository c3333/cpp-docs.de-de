---
title: _ATL_BASE_MODULE70 Struktur
ms.date: 11/04/2016
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
ms.openlocfilehash: 3893e4ce4fcd24f48d9e981ad24505f82dc98833
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168643"
---
# <a name="_atl_base_module70-structure"></a>_ATL_BASE_MODULE70 Struktur

Wird von jedem Projekt verwendet, das ATL verwendet.

## <a name="syntax"></a>Syntax

```cpp
struct _ATL_BASE_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInst;
    HINSTANCE m_hInstResource;
    bool m_bNT5orWin98;
    DWORD dwAtlBuildVer;
    GUID* pguidVer;
    CRITICAL_SECTION m_csResource;
    CSimpleArray<HINSTANCE> m_rgResourceInstance;
};
```

## <a name="members"></a>Member

`cbSize`<br/>
Die Größe der-Struktur, die für die Versionsverwaltung verwendet wird.

`m_hInst`<br/>
Die `hInstance` für dieses Modul (entweder exe oder dll).

`m_hInstResource`<br/>
Standard-instanzressourcenhandle.

`m_bNT5orWin98`<br/>
Informationen zur Betriebssystemversion. Wird intern von ATL verwendet.

`dwAtlBuildVer`<br/>
Speichert die ATL-Version. Zurzeit 0x7.

`pguidVer`<br/>
Interne GUID der ATL.

`m_csResource`<br/>
Wird zum Synchronisieren des Zugriffs auf `m_rgResourceInstance` das Array verwendet. Wird intern von ATL verwendet.

`m_rgResourceInstance`<br/>
Array, das für die Suche nach Ressourcen in allen Ressourcen Instanzen verwendet wird, von denen ATL abhängig ist. Wird intern von ATL verwendet.

## <a name="remarks"></a>Bemerkungen

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module) ist als typedef _ATL_BASE_MODULE70 definiert.

## <a name="requirements"></a>Anforderungen

**Header:** atlcore. h

## <a name="see-also"></a>Weitere Informationen:

[Klassen und Strukturen](../../atl/reference/atl-classes.md)
