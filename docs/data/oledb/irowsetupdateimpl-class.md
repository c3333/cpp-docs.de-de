---
title: IRowsetUpdateImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IRowsetUpdateImpl
- ATL.IRowsetUpdateImpl
- ATL::IRowsetUpdateImpl
- IRowsetUpdateImpl::SetData
- IRowsetUpdateImpl.SetData
- ATL::IRowsetUpdateImpl::SetData
- ATL.IRowsetUpdateImpl.SetData
- ATL.IRowsetUpdateImpl.GetOriginalData
- IRowsetUpdateImpl.GetOriginalData
- ATL::IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetPendingRows
- GetPendingRows
- IRowsetUpdateImpl.GetPendingRows
- ATL::IRowsetUpdateImpl::GetPendingRows
- ATL.IRowsetUpdateImpl.GetPendingRows
- ATL.IRowsetUpdateImpl.GetRowStatus
- IRowsetUpdateImpl::GetRowStatus
- IRowsetUpdateImpl.GetRowStatus
- ATL::IRowsetUpdateImpl::GetRowStatus
- ATL.IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Update
- IRowsetUpdateImpl::Update
- IRowsetUpdateImpl.Update
- ATL.IRowsetUpdateImpl.Update
- IRowsetUpdateImpl::IsUpdateAllowed
- IRowsetUpdateImpl.IsUpdateAllowed
- IsUpdateAllowed
- IRowsetUpdateImpl.m_mapCachedData
- IRowsetUpdateImpl::m_mapCachedData
- m_mapCachedData
helpviewer_keywords:
- providers, updatable
- IRowsetUpdateImpl class
- updatable providers, deferred update
- SetData method
- GetOriginalData method
- GetPendingRows method
- GetRowStatus method
- Undo method
- Update method
- IsUpdateAllowed method
- m_mapCachedData
ms.assetid: f85af76b-ab6f-4f8b-8f4a-337c9679d68f
ms.openlocfilehash: dba962c761fac0408a3c68a46ec6447aa7832522
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545720"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl-Klasse

Die OLE DB Vorlagen Implementierung der [IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85)) -Schnittstelle.

## <a name="syntax"></a>Syntax

```cpp
template <
   class T,
   class Storage,
   class UpdateArray = CAtlArray<Storage>,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>
>

class IRowsetUpdateImpl : public IRowsetChangeImpl<
   T,
   Storage,
   IRowsetUpdate,
   RowClass,
   MapClass>
```

### <a name="parameters"></a>Parameter

*T*<br/>
Eine von `IRowsetUpdateImpl`abgeleitete Klasse.

*Storage*<br/>
Der Benutzerdaten Satz.

*Update Array*<br/>
Ein Array, das zwischengespeicherte Daten zum Aktualisieren des Rowsets enthält.

*RowClass*<br/>
Die Speichereinheit für die `HROW`.

*Mapclass*<br/>
Die Speichereinheit für alle Zeilen Handles, die vom Anbieter gehalten werden.

## <a name="requirements"></a>Voraussetzungen

**Header:** atldb.h

## <a name="members"></a>Member

### <a name="interface-methods-used-with-irowsetchange"></a>Schnittstellen Methoden (mit IRowsetChange verwendet)

|||
|-|-|
|[SetData](#setdata)|Legt Datenwerte in einer oder mehreren Spalten fest.|

### <a name="interface-methods-used-with-irowsetupdate"></a>Schnittstellen Methoden (mit IRowsetUpdate verwendet)

|||
|-|-|
|[GetOriginalData](#getoriginaldata)|Ruft die Daten ab, die zuletzt an die Datenquelle übertragen oder von dieser abgerufen wurden, wobei ausstehende Änderungen ignoriert werden.|
|[GetPendingRows](#getpendingrows)|Gibt eine Liste von Zeilen mit ausstehenden Änderungen zurück.|
|[GetRowStatus](#getrowstatus)|Gibt den Status der angegebenen Zeilen zurück.|
|[Rückgängig](#undo)|Macht Änderungen an der Zeile seit dem letzten Abrufen oder aktualisieren unverändert.|
|[Aktualisieren](#update)|Überträgt alle Änderungen, die seit dem letzten Abrufen oder aktualisieren an der Zeile vorgenommen wurden.|

### <a name="implementation-methods-callback"></a>Implementierungs Methoden (Rückruf)

|||
|-|-|
|[IsUpdateAllowed](#isupdateallowed)|Dient zum Überprüfen auf Sicherheit, Integrität usw., bevor Updates zugelassen werden.|

### <a name="data-members"></a>Datenelemente

|||
|-|-|
|[m_mapCachedData](#mapcacheddata)|Enthält die ursprünglichen Daten für den verzögerten Vorgang.|

## <a name="remarks"></a>Hinweise

Sie sollten zunächst die Dokumentation für [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))lesen und verstehen, da alles, was hier beschrieben wird, auch hier gilt. Lesen Sie außerdem Kapitel 6 der *OLE DB Programmierer-Referenz* zum Festlegen von Daten.

`IRowsetUpdateImpl` implementiert die OLE DB `IRowsetUpdate`-Schnittstelle, mit der Consumer die Übertragung von Änderungen, die mit `IRowsetChange` vorgenommen wurden, an die Datenquelle und die Änderungen vor der Übertragung verzögern können.

> [!IMPORTANT]
>  Es wird dringend empfohlen, dass Sie die folgende Dokumentation lesen, bevor Sie versuchen, Ihren Anbieter zu implementieren:

- [Erstellen eines aktualisierbaren Anbieters](../../data/oledb/creating-an-updatable-provider.md)

- Kapitel 6 der *OLE DB Programmierer-Referenz*

- Siehe auch, wie die `RUpdateRowset`-Klasse im [Update](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) Panel-Beispiel verwendet wird.

## <a name="irowsetupdateimplsetdata"></a><a name="setdata"></a>IRowsetUpdateImpl:: SetData

Legt Datenwerte in einer oder mehreren Spalten fest.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IRowsetChange:: SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

### <a name="remarks"></a>Hinweise

Diese Methode überschreibt die [IRowsetChangeImpl:: SetData](../../data/oledb/irowsetchangeimpl-setdata.md) -Methode, beinhaltet jedoch das Zwischenspeichern ursprünglicher Daten, um die sofortige oder verzögerte Verarbeitung des Vorgangs zuzulassen.

## <a name="irowsetupdateimplgetoriginaldata"></a><a name="getoriginaldata"></a>IRowsetUpdateImpl:: GetOriginalData

Ruft die Daten ab, die zuletzt an die Datenquelle übertragen oder von dieser abgerufen wurden, wobei ausstehende Änderungen ignoriert werden.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (GetOriginalData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pData);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IRowsetUpdate:: GetOriginalData](/previous-versions/windows/desktop/ms709947(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="irowsetupdateimplgetpendingrows"></a><a name="getpendingrows"></a>IRowsetUpdateImpl:: getpdinwächst

Gibt eine Liste von Zeilen mit ausstehenden Änderungen zurück.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (GetPendingRows )(HCHAPTER /* hReserved */,
   DBPENDINGSTATUS dwRowStatus,
   DBCOUNTITEM* pcPendingRows,
   HROW** prgPendingRows,
   DBPENDINGSTATUS** prgPendingStatus);
```

#### <a name="parameters"></a>Parameter

*hreserved*<br/>
in Entspricht dem *hChapter* -Parameter in [IRowsetUpdate:: getpdingens](/previous-versions/windows/desktop/ms719626(v=vs.85)).

Informationen zu anderen Parametern finden Sie unter [IRowsetUpdate:: getpdinwächst](/previous-versions/windows/desktop/ms719626(v=vs.85)) in der *OLE DB-Programmier Referenz*.

### <a name="remarks"></a>Hinweise

Weitere Informationen finden Sie unter [IRowsetUpdate:: getpdinwächst](/previous-versions/windows/desktop/ms719626(v=vs.85)) in der *OLE DB-Programmier Referenz*.

## <a name="irowsetupdateimplgetrowstatus"></a><a name="getrowstatus"></a>IRowsetUpdateImpl:: GetRowStatus

Gibt den Status der angegebenen Zeilen zurück.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (GetRowStatus )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBPENDINGSTATUS rgPendingStatus[]);
```

#### <a name="parameters"></a>Parameter

*hreserved*<br/>
in Entspricht dem *hChapter* -Parameter in [IRowsetUpdate:: GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)).

Informationen zu anderen Parametern finden Sie unter [IRowsetUpdate:: GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="irowsetupdateimplundo"></a><a name="undo"></a>IRowsetUpdateImpl:: Undo

Macht Änderungen an der Zeile seit dem letzten Abrufen oder aktualisieren unverändert.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (Undo )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[ ],
   DBCOUNTITEM* pcRowsUndone,
   HROW** prgRowsUndone,
   DBROWSTATUS** prgRowStatus);
```

#### <a name="parameters"></a>Parameter

*hreserved*<br/>
in Entspricht dem *hChapter* -Parameter in [IRowsetUpdate:: Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

*pcrowsundone*<br/>
vorgenommen Entspricht dem *pcRows* -Parameter in [IRowsetUpdate:: Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

*prgrowsundone*<br/>
in Entspricht dem Parameter *prwächst* in [IRowsetUpdate:: Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

Informationen zu anderen Parametern finden Sie unter [IRowsetUpdate:: Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="irowsetupdateimplupdate"></a><a name="update"></a>IRowsetUpdateImpl:: Update

Überträgt alle Änderungen, die seit dem letzten Abrufen oder aktualisieren an der Zeile vorgenommen wurden.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (Update )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBCOUNTITEM* pcRows,
   HROW** prgRows,
   DBROWSTATUS** prgRowStatus);
```

#### <a name="parameters"></a>Parameter

*hreserved*<br/>
in Entspricht dem *hChapter* -Parameter in [IRowsetUpdate:: Update](/previous-versions/windows/desktop/ms719709(v=vs.85)).

Informationen zu anderen Parametern finden Sie unter [IRowsetUpdate:: Update](/previous-versions/windows/desktop/ms719709(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

### <a name="remarks"></a>Hinweise

Änderungen werden durch Aufrufen von [IRowsetChangeImpl:: FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md)übertragen. Der Consumer muss [CRowset:: Update](../../data/oledb/crowset-update.md) anrufen, damit die Änderungen wirksam werden. Legen Sie *prgRowStatus* auf einen geeigneten Wert fest, wie in den [Zeilen](/previous-versions/windows/desktop/ms722752(v=vs.85)) Status in der *OLE DB Programmierer-Referenz*beschrieben.

## <a name="irowsetupdateimplisupdateallowed"></a><a name="isupdateallowed"></a>IRowsetUpdateImpl:: IsUpdateAllowed

Überschreiben Sie diese Methode, um vor Updates die Sicherheit, Integrität usw. zu überprüfen.

### <a name="syntax"></a>Syntax

```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,
   HROW /* [in] */ /* hRowUpdate */,
   DBROWSTATUS* /* [out] */ /* pRowStatus */);
```

#### <a name="parameters"></a>Parameter

*status*<br/>
in Der Status von ausstehenden Vorgängen in den Zeilen.

*hrowupdate*<br/>
in Handle für die Zeilen, die der Benutzer aktualisieren möchte.

*prowstatus*<br/>
vorgenommen Der Status, der an den Benutzer zurückgegeben wird.

### <a name="remarks"></a>Hinweise

Wenn Sie feststellen, dass ein Update zulässig sein soll, wird S_OK zurückgegeben. Andernfalls wird E_FAIL zurückgegeben. Wenn Sie ein Update zulassen, müssen Sie auch die `DBROWSTATUS` in [IRowsetUpdateImpl:: Update](../../data/oledb/irowsetupdateimpl-update.md) auf einen entsprechenden [Zeilen Status](/previous-versions/windows/desktop/ms722752(v=vs.85))festlegen.

## <a name="irowsetupdateimplm_mapcacheddata"></a><a name="mapcacheddata"></a>IRowsetUpdateImpl:: m_mapCachedData

Eine Karte, die die ursprünglichen Daten für den verzögerten Vorgang enthält.

### <a name="syntax"></a>Syntax

```cpp
CAtlMap<
   HROW hRow, 
   Storage* pData
>
m_mapCachedData;
```

#### <a name="parameters"></a>Parameter

*HROW*<br/>
Handle für die Zeilen für die Daten.

*pData*<br/>
Ein Zeiger auf die Daten, die zwischengespeichert werden sollen. Die Daten sind vom Typ " *Storage* " (die Benutzerdaten Satz-Klasse). Weitere Informationen finden Sie unter dem *Storage* Template-Argument in der [IRowsetUpdateImpl-Klasse](../../data/oledb/irowsetupdateimpl-class.md).

## <a name="see-also"></a>Siehe auch

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur von OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Erstellen eines aktualisierbaren Anbieters](../../data/oledb/creating-an-updatable-provider.md)