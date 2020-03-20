---
title: IColumnsInfoImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL.IColumnsInfoImpl<T>
- ATL::IColumnsInfoImpl
- IColumnsInfoImpl
- ATL.IColumnsInfoImpl
- ATL::IColumnsInfoImpl<T>
- ATL::IColumnsInfoImpl::GetColumnInfo
- ATL.IColumnsInfoImpl.GetColumnInfo
- ATL::IColumnsInfoImpl<T>::GetColumnInfo
- IColumnsInfoImpl::GetColumnInfo
- IColumnsInfoImpl<T>::GetColumnInfo
- IColumnsInfoImpl.GetColumnInfo
- IColumnsInfoImpl<T>::MapColumnIDs
- MapColumnIDs
- ATL::IColumnsInfoImpl::MapColumnIDs
- IColumnsInfoImpl.MapColumnIDs
- ATL::IColumnsInfoImpl<T>::MapColumnIDs
- IColumnsInfoImpl::MapColumnIDs
- ATL.IColumnsInfoImpl<T>.MapColumnIDs
- ATL.IColumnsInfoImpl.MapColumnIDs
helpviewer_keywords:
- IColumnsInfoImpl class
- GetColumnInfo method
- MapColumnIDs method
ms.assetid: ba74c1c5-2eda-4452-8b57-84919fa0d066
ms.openlocfilehash: 2eb7714762de8ccf810a8fdd04ee33ae24e9d431
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545984"
---
# <a name="icolumnsinfoimpl-class"></a>IColumnsInfoImpl-Klasse

Stellt eine Implementierung der [IColumnsInfo](/previous-versions/windows/desktop/ms724541(v=vs.85)) -Schnittstelle bereit.

## <a name="syntax"></a>Syntax

```cpp
template <class T>
class ATL_NO_VTABLE IColumnsInfoImpl :
   public IColumnsInfo, 
   public CDBIDOps
```

### <a name="parameters"></a>Parameter

*T*<br/>
Die von `IColumnsInfoImpl`abgeleitete Klasse.

## <a name="requirements"></a>Voraussetzungen

**Header:** atldb.h

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[GetColumnInfo](#getcolumninfo)|Gibt die von den meisten Consumern benötigten Spaltenmetadaten zurück.|
|[MapColumnIDs](#mapcolumnids)|Gibt ein Array von Ordnungszahlen der Spalten in einem Rowset zurück, die mit den angegebenen Spalten-IDs gekennzeichnet sind.|

## <a name="remarks"></a>Hinweise

Eine erforderliche Schnittstelle für Rowsets und Befehle. Um das Verhalten der `IColumnsInfo` Implementierung Ihres Anbieters zu ändern, müssen Sie die Zuordnung der Anbieter Spalte ändern.

## <a name="icolumnsinfoimplgetcolumninfo"></a><a name="getcolumninfo"></a>Icolumnsinfoimpl:: GetColumnInfo

Gibt die von den meisten Consumern benötigten Spaltenmetadaten zurück.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (GetColumnInfo)(DBORDINAL* pcColumns,
   DBCOLUMNINFO** prgInfo,
   OLECHAR** ppStringsBuffer);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) in der *OLE DB-Programmier Referenz*.

## <a name="icolumnsinfoimplmapcolumnids"></a><a name="mapcolumnids"></a>Icolumnsinfoimpl:: MapColumnIDs

Gibt ein Array von Ordnungszahlen der Spalten in einem Rowset zurück, die mit den angegebenen Spalten-IDs gekennzeichnet sind.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (MapColumnIDs)(DBORDINAL cColumnIDs,
   const DBID rgColumnIDs[],
   DBORDINAL rgColumns[]);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IColumnsInfo:: MapColumnIDs](/previous-versions/windows/desktop/ms714200(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="see-also"></a>Siehe auch

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur von OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-template-architecture.md)