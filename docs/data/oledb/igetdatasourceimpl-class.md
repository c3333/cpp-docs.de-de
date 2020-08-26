---
title: IGetDataSourceImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IGetDataSourceImpl
- ATL.IGetDataSourceImpl<T>
- ATL.IGetDataSourceImpl
- ATL::IGetDataSourceImpl
- ATL::IGetDataSourceImpl<T>
- GetDataSource
- IGetDataSourceImpl.GetDataSource
- IGetDataSourceImpl::GetDataSource
helpviewer_keywords:
- IGetDataSourceImpl class
- GetDataSource method
ms.assetid: d63f3178-d663-4f01-8c09-8aab2dd6805a
ms.openlocfilehash: 4c8af66f41724c5a99dfe271a7dd8babc3a993a5
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843962"
---
# <a name="igetdatasourceimpl-class"></a>IGetDataSourceImpl-Klasse

Stellt eine Implementierung des [IGetDataSource](/previous-versions/windows/desktop/ms709721(v=vs.85)) -Objekts bereit.

## <a name="syntax"></a>Syntax

```cpp
template <class T>
class ATL_NO_VTABLE IGetDataSourceImpl : public IGetDataSource
```

### <a name="parameters"></a>Parameter

*T*<br/>
Die von abgeleitete Klasse `IGetDataSourceImpl` .

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** „atldb.h“

## <a name="members"></a>Member

### <a name="interface-methods"></a>Schnittstellenmethoden

| Name | Beschreibung |
|-|-|
|[GetDataSource](#getdatasource)|Gibt einen Schnittstellen Zeiger für das Datenquellen Objekt zurück, das die Sitzung erstellt hat.|

## <a name="remarks"></a>Bemerkungen

Dies ist eine erforderliche Schnittstelle für die Sitzung, um einen Schnittstellen Zeiger auf das Datenquellen Objekt zu erhalten.

## <a name="igetdatasourceimplgetdatasource"></a><a name="getdatasource"></a> Igetdatasourceimpl:: GetDataSource

Gibt einen Schnittstellen Zeiger für das Datenquellen Objekt zurück, das die Sitzung erstellt hat.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(GetDataSource)(REFIID riid,
   IUnknown ** ppDataSource);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IGetDataSource:: GetDataSource](/previous-versions/windows/desktop/ms725443(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

### <a name="remarks"></a>Bemerkungen

Nützlich, wenn Sie auf Eigenschaften im Datenquellen Objekt zugreifen müssen.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur der OLE DB-Anbieter Vorlage](../../data/oledb/ole-db-provider-template-architecture.md)
