---
title: IRowsetCreatorImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetCreatorImpl
- ATL.IRowsetCreatorImpl
- ATL::IRowsetCreatorImpl<T>
- ATL.IRowsetCreatorImpl<T>
- IRowsetCreatorImpl
- IRowsetCreatorImpl.SetSite
- IRowsetCreatorImpl<T>::SetSite
- IRowsetCreatorImpl::SetSite
- SetSite
- ATL.IRowsetCreatorImpl.SetSite
- ATL::IRowsetCreatorImpl<T>::SetSite
- ATL::IRowsetCreatorImpl::SetSite
- ATL.IRowsetCreatorImpl<T>.SetSite
helpviewer_keywords:
- IRowsetCreatorImpl class
- SetSite method
ms.assetid: 92cc950f-7978-4754-8d9a-defa63867d82
ms.openlocfilehash: c1ad2c5e97dfe975a3b545e44b512dff7bf512a0
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843443"
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl-Klasse

Führt dieselben Funktionen wie aus, `IObjectWithSite` aktiviert jedoch auch die OLE DB Eigenschaften `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS` .

## <a name="syntax"></a>Syntax

```cpp
template < class T >
class ATL_NO_VTABLE IRowsetCreatorImpl
   : public IObjectWithSiteImpl< T >
```

### <a name="parameters"></a>Parameter

*T*<br/>
Eine von abgeleitete Klasse `IRowsetCreator` .

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** „atldb.h“

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

| Name | Beschreibung |
|-|-|
|[SetSite](#setsite)|Legt die Site fest, die das Rowsetobjekt enthält.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse erbt von [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) und überschreibt [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite). Wenn ein Anbieter Befehl oder ein Sitzungs Objekt ein Rowset erstellt, ruft es `QueryInterface` für das Rowsetobjekt auf und ruft auf, um die `IObjectWithSite` `SetSite` Schnittstelle des Rowsetobjekt `IUnkown` als Website Schnittstelle zu übergeben.

## <a name="irowsetcreatorimplsetsite"></a><a name="setsite"></a> Irowsetkreatorimpl:: SetSite

Legt die Site fest, die das Rowsetobjekt enthält. Weitere Informationen finden Sie unter [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite).

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(SetSite )(IUnknown* pCreator);
```

#### <a name="parameters"></a>Parameter

*pcreator*<br/>
in Zeiger auf den `IUnknown` Schnittstellen Zeiger der Site, die das Rowsetobjekt verwaltet.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Außerdem `IRowsetCreatorImpl::SetSite` aktiviert die OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS` Eigenschaften.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur der OLE DB-Anbieter Vorlage](../../data/oledb/ole-db-provider-template-architecture.md)
