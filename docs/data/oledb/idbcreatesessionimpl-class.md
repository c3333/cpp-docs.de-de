---
title: IDBCreateSessionImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IDBCreateSessionImpl
- ATL.IDBCreateSessionImpl
- ATL::IDBCreateSessionImpl
- IDBCreateSessionImpl::CreateSession
- IDBCreateSessionImpl.CreateSession
- CreateSession
helpviewer_keywords:
- IDBCreateSessionImpl class
- CreateSession method
ms.assetid: 48c02c5c-8362-45ac-af8e-bb119cf8c5c7
ms.openlocfilehash: cff1ca374c9489cb9c5df0dad153c4bf7a4cbc9e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210781"
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl-Klasse

Stellt eine Implementierung für die [idbkreatesession](/previous-versions/windows/desktop/ms724076(v=vs.85)) -Schnittstelle bereit.

## <a name="syntax"></a>Syntax

```cpp
template <class T, class SessionClass>
class ATL_NO_VTABLE IDBCreateSessionImpl
   : public IDBCreateSession
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, abgeleitet von

*Sessionclass*<br/>
Das Sitzungs Objekt.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldb.h

## <a name="members"></a>Members

### <a name="interface-methods"></a>Schnittstellenmethoden

|||
|-|-|
|[CreateSession](#createsession)|Erstellt eine neue Sitzung aus dem Datenquellen Objekt und gibt die angeforderte Schnittstelle für die neu erstellte Sitzung zurück.|

## <a name="remarks"></a>Bemerkungen

Eine erforderliche Schnittstelle für Datenquellen Objekte.

## <a name="idbcreatesessionimplcreatesession"></a><a name="createsession"></a>Idbkreatesessionimpl:: kreatesession

Erstellt eine neue Sitzung aus dem Datenquellen Objekt und gibt die angeforderte Schnittstelle für die neu erstellte Sitzung zurück.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(CreateSession)(IUnknown * pUnkOuter,
   REFIID riid,
   IUnknown ** ppDBSession);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie in der *OLE DB Programmierer-Referenz*unter [idbkreatesession:: erkreatesession](/previous-versions/windows/desktop/ms714942(v=vs.85)) .

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur von OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-template-architecture.md)
