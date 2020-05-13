---
title: _ATL_COM_MODULE70 Struktur
ms.date: 11/04/2016
f1_keywords:
- ATL::_ATL_COM_MODULE70
- ATL._ATL_COM_MODULE70
- _ATL_COM_MODULE70
helpviewer_keywords:
- _ATL_COM_MODULE70 structure
- ATL_COM_MODULE70 structure
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
ms.openlocfilehash: c2e9e3d6695a7fbbcc87c489edf2e96fcdffb835
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168630"
---
# <a name="_atl_com_module70-structure"></a>_ATL_COM_MODULE70 Struktur

Wird von com-bezogenes Code in ATL verwendet.

## <a name="syntax"></a>Syntax

```cpp
struct _ATL_COM_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInstTypeLib;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapFirst;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapLast;
    CRITICAL_SECTION m_csObjMap;
};
```

## <a name="members"></a>Member

`cbSize`<br/>
Die Größe der-Struktur, die für die Versionsverwaltung verwendet wird.

`m_hInstTypeLib`<br/>
Die Handle-Instanz für die Typbibliothek für dieses Modul.

`m_ppAutoObjMapFirst`<br/>
Adresse des Array Elements, das den Anfang der Objekt Zuordnungs Einträge für dieses Modul angibt.

`m_ppAutoObjMapLast`<br/>
Adresse des Array Elements, das das Ende der Objekt Zuordnungs Einträge für dieses Modul angibt.

`m_csObjMap`<br/>
Kritischer Abschnitt zum Serialisieren des Zugriffs auf die Objekt Zuordnungs Einträge. Wird intern von ATL verwendet.

## <a name="remarks"></a>Bemerkungen

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module) ist als typedef _ATL_COM_MODULE70 definiert.

## <a name="requirements"></a>Anforderungen

**Header:** atlbase. h

## <a name="see-also"></a>Weitere Informationen:

[Klassen und Strukturen](../../atl/reference/atl-classes.md)
