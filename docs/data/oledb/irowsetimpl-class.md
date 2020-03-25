---
title: IRowsetImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IRowsetImpl
- IRowsetImpl::AddRefRows
- IRowsetImpl.AddRefRows
- ATL::IRowsetImpl::AddRefRows
- ATL.IRowsetImpl.AddRefRows
- IRowsetImpl.CreateRow
- ATL.IRowsetImpl.CreateRow
- ATL::IRowsetImpl::CreateRow
- CreateRow
- IRowsetImpl::CreateRow
- ATL.IRowsetImpl.GetData
- ATL::IRowsetImpl::GetData
- IRowsetImpl::GetData
- IRowsetImpl.GetData
- GetDBStatus
- IRowsetImpl.GetDBStatus
- IRowsetImpl::GetDBStatus
- GetNextRows
- ATL.IRowsetImpl.GetNextRows
- ATL::IRowsetImpl::GetNextRows
- IRowsetImpl::GetNextRows
- IRowsetImpl.GetNextRows
- IRowsetImpl.IRowsetImpl
- ATL::IRowsetImpl::IRowsetImpl
- ATL.IRowsetImpl.IRowsetImpl
- IRowsetImpl::IRowsetImpl
- ATL::IRowsetImpl::RefRows
- ATL.IRowsetImpl.RefRows
- IRowsetImpl.RefRows
- RefRows
- IRowsetImpl::RefRows
- ATL.IRowsetImpl.ReleaseRows
- IRowsetImpl::ReleaseRows
- ATL::IRowsetImpl::ReleaseRows
- IRowsetImpl.ReleaseRows
- ATL.IRowsetImpl.RestartPosition
- IRowsetImpl::RestartPosition
- RestartPosition
- ATL::IRowsetImpl::RestartPosition
- IRowsetImpl.RestartPosition
- IRowsetImpl.SetDBStatus
- IRowsetImpl::SetDBStatus
- SetDBStatus
- ATL.IRowsetImpl.m_bCanFetchBack
- ATL::IRowsetImpl::m_bCanFetchBack
- IRowsetImpl.m_bCanFetchBack
- IRowsetImpl::m_bCanFetchBack
- m_bCanFetchBack
- IRowsetImpl::m_bCanScrollBack
- ATL::IRowsetImpl::m_bCanScrollBack
- IRowsetImpl.m_bCanScrollBack
- ATL.IRowsetImpl.m_bCanScrollBack
- m_bCanScrollBack
- ATL.IRowsetImpl.m_bReset
- IRowsetImpl.m_bReset
- m_bReset
- IRowsetImpl::m_bReset
- ATL::IRowsetImpl::m_bReset
- IRowsetImpl::m_iRowset
- IRowsetImpl.m_iRowset
- ATL::IRowsetImpl::m_iRowset
- ATL.IRowsetImpl.m_iRowset
- m_iRowset
- IRowsetImpl::m_rgRowHandles
- IRowsetImpl.m_rgRowHandles
- m_rgRowHandles
- ATL::IRowsetImpl::m_rgRowHandles
- ATL.IRowsetImpl.m_rgRowHandles
helpviewer_keywords:
- IRowsetImpl class
- AddRefRows method
- CreateRow method
- GetData method [OLE DB]
- GetDBStatus method
- GetNextRows method
- IRowsetImpl constructor
- RefRows method
- ReleaseRows method
- RestartPosition method
- SetDBStatus method
- m_bCanFetchBack
- m_bCanScrollBack
- m_bReset
- m_iRowset
- m_rgRowHandles
ms.assetid: 6a9189af-7556-45b1-adcb-9d62bb36704c
ms.openlocfilehash: db12af1aecc094e6c04ab37b5a70a0acd97e39e9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210417"
---
# <a name="irowsetimpl-class"></a>IRowsetImpl-Klasse

Stellt eine Implementierung der `IRowset`-Schnittstelle bereit.

## <a name="syntax"></a>Syntax

```cpp
template <
   class T,
   class RowsetInterface,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <
      RowClass::KeyType,
      RowClass*>>
class ATL_NO_VTABLE IRowsetImpl : public RowsetInterface
```

### <a name="parameters"></a>Parameter

*T*<br/>
Die von `IRowsetImpl`abgeleitete Klasse.

*RowsetInterface*<br/>
Eine von `IRowsetImpl`abgeleitete Klasse.

*RowClass*<br/>
Speichereinheit für die `HROW`.

*Mapclass*<br/>
Speichereinheit für alle Zeilen Handles, die vom Anbieter gehalten werden.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldb.h

## <a name="members"></a>Members

### <a name="methods"></a>Methoden

|||
|-|-|
|[AddRefRows](#addrefrows)|Fügt einem vorhandenen Zeilenhandle einen Verweiszähler hinzu.|
|[CreateRow](#createrow)|Wird von [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) aufgerufen, um eine neue `HROW`zuzuordnen. Wird nicht direkt vom Benutzer aufgerufen.|
|[GetData](#getdata)|Ruft Daten von der Zeilenkopie des Rowsets ab.|
|[GetDBStatus](#getdbstatus)|Gibt den Status für das angegebene Feld zurück.|
|[GetNextRows](#getnextrows)|Ruft Zeilen sequenziell ab und speichert die vorherige Position.|
|[IRowsetImpl](#irowsetimpl)|Der Konstruktor. Wird nicht direkt vom Benutzer aufgerufen.|
|[RefRows](#refrows)|Wird von [adressfrows](../../data/oledb/irowsetimpl-addrefrows.md) und [ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)aufgerufen. Wird nicht direkt vom Benutzer aufgerufen.|
|[ReleaseRows](#releaserows)|Gibt Zeilen frei.|
|[Restart Position](#restartposition)|Positioniert die nächste Abruf Position an der Anfangsposition. Das heißt, die Position, zu der das Rowset erstmalig erstellt wurde.|
|[SetDBStatus](#setdbstatus)|Legt die Statusflags für das angegebene Feld fest.|

### <a name="data-members"></a>Datenelemente

|||
|-|-|
|[m_bCanFetchBack](#bcanfetchback)|Gibt an, ob ein Anbieter das rückwärts abrufen unterstützt.|
|[m_bCanScrollBack](#bcanscrollback)|Gibt an, ob der Cursor von einem Anbieter Rückwärtsscrollen kann.|
|[m_bReset](#breset)|Gibt an, ob ein Anbieter seine Cursorposition zurückgesetzt hat. Dies hat eine besondere Bedeutung, wenn Sie Rückwärtsscrollen oder rückwärts in [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)abrufen.|
|[m_iRowset](#irowset)|Ein Index für das Rowset, das den Cursor darstellt.|
|[m_rgRowHandles](#rgrowhandles)|Eine Liste der Zeilen Handles.|

## <a name="remarks"></a>Bemerkungen

[IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85)) ist die basisrowsetschnittstelle.

## <a name="irowsetimpladdrefrows"></a><a name="addrefrows"></a>IRow-timpl:: adressfrows

Fügt einem vorhandenen Zeilenhandle einen Verweiszähler hinzu.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(AddRefRows )(DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IRowset:: adressfrows](/previous-versions/windows/desktop/ms719619(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="irowsetimplcreaterow"></a><a name="createrow"></a>Irowctimpl:: kreaterow

Eine Hilfsmethode, die von [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) aufgerufen wird, um eine neue `HROW`zuzuordnen.

### <a name="syntax"></a>Syntax

```cpp
HRESULT CreateRow(DBROWOFFSET lRowsOffset,
   DBCOUNTITEM& cRowsObtained,
   HROW* rgRows);
```

#### <a name="parameters"></a>Parameter

*lrowsoffset*<br/>
Cursor Position der Zeile, die erstellt wird.

*crowsobgepflegt*<br/>
Ein Verweis, der an den Benutzer zurückgegeben wird, der die Anzahl der erstellten Zeilen angibt.

*rwächst*<br/>
Ein Array von `HROW`s, das mit den neu erstellten Zeilen Handles an den Aufrufer zurückgegeben wird.

### <a name="remarks"></a>Bemerkungen

Wenn die Zeile vorhanden ist, ruft diese Methode " [adressfrows](../../data/oledb/irowsetimpl-addrefrows.md) " auf und gibt zurück. Andernfalls wird eine neue Instanz der RowClass-Vorlagen Variablen zugewiesen, und Sie wird [m_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md)hinzugefügt.

## <a name="irowsetimplgetdata"></a><a name="getdata"></a>Irowctimpl:: GetData

Ruft Daten von der Zeilenkopie des Rowsets ab.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(GetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pDstData);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IRowset:: GetData](/previous-versions/windows/desktop/ms716988(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

Einige Parameter entsprechen *OLE DB Programmier Verweis* Parametern unterschiedlicher Namen, die in `IRowset::GetData`beschrieben werden:

|Parameter für OLE DB Vorlage|*Verweis Parameter für OLE DB Programmierer*|
|--------------------------------|------------------------------------------------|
|*pdstdata*|*pData*|

### <a name="remarks"></a>Bemerkungen

Behandelt auch die Datenkonvertierung mithilfe der OLE DB Daten Konvertierungs-DLL.

## <a name="irowsetimplgetdbstatus"></a><a name="getdbstatus"></a>Irowctimpl:: GetDBStatus

Gibt die DBStatus-Statusflags für das angegebene Feld zurück.

### <a name="syntax"></a>Syntax

```cpp
virtual DBSTATUS GetDBStatus(RowClass* currentRow,
   ATLCOLUMNINFO* columnNames);
```

#### <a name="parameters"></a>Parameter

*CurrentRow*<br/>
in Die aktuelle Zeile.

*columnNames*<br/>
in Die Spalte, für die der Status angefordert wird.

### <a name="return-value"></a>Rückgabewert

Die [dbstatusflags](/previous-versions/windows/desktop/ms722617(v=vs.85)) für die Spalte.

## <a name="irowsetimplgetnextrows"></a><a name="getnextrows"></a>Irowctimpl:: GetNextRows

Ruft Zeilen sequenziell ab und speichert die vorherige Position.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(GetNextRows )(HCHAPTER hReserved,
   DBROWOFFSET lRowsOffset,
   DBROWCOUNT cRows,
   DBCOUNTITEM* pcRowsObtained,
   HROW** prghRows);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IRowset:: GetNextRows](/previous-versions/windows/desktop/ms709827(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="irowsetimplirowsetimpl"></a><a name="irowsetimpl"></a>IRow-timpl:: IRow-timpl

Der Konstruktor.

### <a name="syntax"></a>Syntax

```cpp
IRowsetImpl();
```

### <a name="remarks"></a>Bemerkungen

Normalerweise ist es nicht erforderlich, diese Methode direkt aufzurufen.

## <a name="irowsetimplrefrows"></a><a name="refrows"></a>Irowantimpl:: refrows

Wird von [adressfrows](../../data/oledb/irowsetimpl-addrefrows.md) und [ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md) aufgerufen, um einen Verweis Zähler für ein vorhandenes Zeilen Handle zu erhöhen oder freizugeben.

### <a name="syntax"></a>Syntax

```cpp
HRESULT RefRows(DBCOUNTITEM cRows,
   const HROWrghRows[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[],
   BOOL bAdd);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IRowset:: adressfrows](/previous-versions/windows/desktop/ms719619(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

## <a name="irowsetimplreleaserows"></a><a name="releaserows"></a>Irowantimpl:: ReleaseRows

Gibt Zeilen frei.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(ReleaseRows )(DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWOPTIONS rgRowOptions[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IRowset:: ReleaseRows](/previous-versions/windows/desktop/ms719771(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="irowsetimplrestartposition"></a><a name="restartposition"></a>IRowsetImpl:: RestartPosition

Positioniert die nächste Abruf Position an der Anfangsposition. Das heißt, die Position, zu der das Rowset erstmalig erstellt wurde.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(RestartPosition )(HCHAPTER /* hReserved */);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IRowset:: RestartPosition](/previous-versions/windows/desktop/ms712877(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

### <a name="remarks"></a>Bemerkungen

Die Rowsetposition ist nicht definiert, bis `GetNextRow` aufgerufen wird. Sie können sich rückwärts in einem ronass bewegen, indem Sie `RestartPosition` aufrufen und dann den Abruf oder den Bildlauf rückwärts ausführen.

## <a name="irowsetimplsetdbstatus"></a><a name="setdbstatus"></a>IRowsetImpl:: SetDBStatus

Legt die DBStatus-Statusflags für das angegebene Feld fest.

### <a name="syntax"></a>Syntax

```cpp
virtual HRESULT SetDBStatus(DBSTATUS* statusFlags,
   RowClass* currentRow,
   ATLCOLUMNINFO* columnInfo);
```

#### <a name="parameters"></a>Parameter

*Status Flags*<br/>
Die [dbstatusflags](/previous-versions/windows/desktop/ms722617(v=vs.85)) , die für die Spalte festgelegt werden sollen.

*CurrentRow*<br/>
Die aktuelle Zeile.

*ColumnInfo*<br/>
Die Spalte, für die der Status festgelegt wird.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Bemerkungen

Der Anbieter überschreibt diese Funktion, um eine spezielle Verarbeitung für DBSTATUS_S_ISNULL und DBSTATUS_S_DEFAULT bereitzustellen.

## <a name="irowsetimplm_bcanfetchback"></a><a name="bcanfetchback"></a>IRow-timpl:: m_bCanFetchBack

Gibt an, ob ein Anbieter das rückwärts abrufen unterstützt.

### <a name="syntax"></a>Syntax

```cpp
unsigned m_bCanFetchBack:1;
```

### <a name="remarks"></a>Bemerkungen

Verknüpft mit der `DBPROP_CANFETCHBACKWARDS`-Eigenschaft in der `DBPROPSET_ROWSET` Gruppe. Der Anbieter muss `DBPROP_CANFETCHBACKWARDS` für `m_bCanFetchBackwards` unter **stützen.**

## <a name="irowsetimplm_bcanscrollback"></a><a name="bcanscrollback"></a>IRow-timpl:: m_bCanScrollBack

Gibt an, ob der Cursor von einem Anbieter Rückwärtsscrollen kann.

### <a name="syntax"></a>Syntax

```cpp
unsigned  m_bCanScrollBack:1;
```

### <a name="remarks"></a>Bemerkungen

Verknüpft mit der `DBPROP_CANSCROLLBACKWARDS`-Eigenschaft in der `DBPROPSET_ROWSET` Gruppe. Der Anbieter muss `DBPROP_CANSCROLLBACKWARDS` für `m_bCanFetchBackwards` unter **stützen.**

## <a name="irowsetimplm_breset"></a><a name="breset"></a>IRow-timpl:: m_bReset

Ein Bitflag, das verwendet wird, um zu bestimmen, ob die Cursorposition für das Rowset definiert ist.

### <a name="syntax"></a>Syntax

```cpp
unsigned m_bReset:1;
```

### <a name="remarks"></a>Bemerkungen

Wenn der Consumer [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) mit einem negativen `lOffset` oder *Crows* aufruft und `m_bReset` true ist, wechselt `GetNextRows` zum Ende des Rowsets. Wenn `m_bReset` false ist, empfängt der Consumer in Übereinstimmung mit der OLE DB Spezifikation einen Fehlercode. Das `m_bReset`-Flag wird auf **true** festgelegt, wenn das Rowset erstmalig erstellt wird, und wenn der Consumer [IRowsetImpl:: RestartPosition](../../data/oledb/irowsetimpl-restartposition.md)aufruft. Wenn Sie `GetNextRows`aufzurufen, wird er auf " **false** " festgelegt.

## <a name="irowsetimplm_irowset"></a><a name="irowset"></a>IRow-timpl:: m_iRowset

Ein Index für das Rowset, das den Cursor darstellt.

### <a name="syntax"></a>Syntax

```cpp
DBROWOFFSET m_iRowset;
```

## <a name="irowsetimplm_rgrowhandles"></a><a name="rgrowhandles"></a>IRow-timpl:: m_rgRowHandles

Eine Zuordnung von Zeilen Handles, die derzeit im Anbieter als Reaktion auf `GetNextRows`enthalten sind.

### <a name="syntax"></a>Syntax

```cpp
MapClass m_rgRowHandles;
```

### <a name="remarks"></a>Bemerkungen

Zeilen Handles werden durch Aufrufen von `ReleaseRows`entfernt. Weitere Informationen zur Definition von *mapclass*finden Sie unter [irowctimpl Overview](../../data/oledb/irowsetimpl-class.md) .

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur von OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[CSimpleRow-Klasse](../../data/oledb/csimplerow-class.md)
