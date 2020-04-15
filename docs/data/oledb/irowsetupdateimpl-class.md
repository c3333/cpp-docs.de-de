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
ms.openlocfilehash: 6347a42b9065239f768c6b50c430946393358df1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370747"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl-Klasse

Die OLE DB Templates-Implementierung der [IRowsetUpdate-Schnittstelle.](/previous-versions/windows/desktop/ms714401(v=vs.85))

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
Eine Klasse, `IRowsetUpdateImpl`die von abgeleitet ist.

*Storage*<br/>
Der Benutzerdatensatz.

*UpdateArray*<br/>
Ein Array, das zwischengespeicherte Daten zum Aktualisieren des Rowsets enthält.

*RowClass*<br/>
Die Speichereinheit `HROW`für die .

*MapClass*<br/>
Die Speichereinheit für alle Zeilenhandles, die sich im Besitz des Anbieters befinden.

## <a name="requirements"></a>Anforderungen

**Header:** „atldb.h“

## <a name="members"></a>Member

### <a name="interface-methods-used-with-irowsetchange"></a>Schnittstellenmethoden (verwendet mit IRowsetChange)

|||
|-|-|
|[Setdata](#setdata)|Legt Datenwerte in einer oder mehreren Spalten fest.|

### <a name="interface-methods-used-with-irowsetupdate"></a>Schnittstellenmethoden (verwendet mit IRowsetUpdate)

|||
|-|-|
|[GetOriginalData](#getoriginaldata)|Ruft die Zuletzt an die Datenquelle übermittelten oder abgerufenen Daten ab, wobei ausstehende Änderungen ignoriert werden.|
|[GetPendingRows](#getpendingrows)|Gibt eine Liste von Zeilen mit ausstehenden Änderungen zurück.|
|[GetRowStatus](#getrowstatus)|Gibt den Status der angegebenen Zeilen zurück.|
|[Rückgängig](#undo)|Macht alle Änderungen an der Zeile seit dem letzten Abruf oder der letzten Aktualisierung auf.|
|[Aktualisieren](#update)|Überträgt alle Änderungen, die seit dem letzten Abruf oder der letzten Aktualisierung an der Zeile vorgenommen wurden.|

### <a name="implementation-methods-callback"></a>Implementierungsmethoden (Callback)

|||
|-|-|
|[IsUpdateAllowed](#isupdateallowed)|Wird verwendet, um die Sicherheit, Integrität usw. zu überprüfen, bevor Updates zugelassen werden.|

### <a name="data-members"></a>Datenelemente

|||
|-|-|
|[m_mapCachedData](#mapcacheddata)|Enthält die ursprünglichen Daten für den verzögerten Vorgang.|

## <a name="remarks"></a>Bemerkungen

Sie sollten zuerst die Dokumentation zu [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))lesen und verstehen, da alles, was dort beschrieben wird, auch hier gilt. Lesen Sie auch Kapitel 6 der Referenz des *OLE DB-Programmierers* zum Festlegen von Daten.

`IRowsetUpdateImpl`implementiert die OLE `IRowsetUpdate` DB-Schnittstelle, die es Verbrauchern ermöglicht, die Übertragung von Änderungen `IRowsetChange` an die Datenquelle zu verzögern und Änderungen vor der Übertragung rückgängig zu machen.

> [!IMPORTANT]
> Es wird dringend empfohlen, die folgende Dokumentation zu lesen, bevor Sie versuchen, Ihren Anbieter zu implementieren:

- [Erstellen eines updatable-Anbieters](../../data/oledb/creating-an-updatable-provider.md)

- Kapitel 6 der Referenz des *OLE DB-Programmierers*

- Sehen Sie `RUpdateRowset` auch, wie die Klasse im [UpdatePV-Beispiel](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) verwendet wird

## <a name="irowsetupdateimplsetdata"></a><a name="setdata"></a>IRowsetUpdateImpl::SetData

Legt Datenwerte in einer oder mehreren Spalten fest.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>Parameter

Siehe [IRowsetChange::SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) in der *Referenz des OLE DB-Programmierers*.

### <a name="remarks"></a>Bemerkungen

Diese Methode überschreibt die [IRowsetChangeImpl::SetData-Methode,](../../data/oledb/irowsetchangeimpl-setdata.md) enthält jedoch das Zwischenspeichern von Originaldaten, um eine sofortige oder verzögerte Verarbeitung des Vorgangs zu ermöglichen.

## <a name="irowsetupdateimplgetoriginaldata"></a><a name="getoriginaldata"></a>IRowsetUpdateImpl::GetOriginalData

Ruft die Zuletzt an die Datenquelle übermittelten oder abgerufenen Daten ab, wobei ausstehende Änderungen ignoriert werden.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (GetOriginalData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pData);
```

#### <a name="parameters"></a>Parameter

Siehe [IRowsetUpdate::GetOriginalData](/previous-versions/windows/desktop/ms709947(v=vs.85)) in der *Referenz des OLE DB-Programmierers*.

## <a name="irowsetupdateimplgetpendingrows"></a><a name="getpendingrows"></a>IRowsetUpdateImpl::GetPendingRows

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

*hReserviert*<br/>
[in] Entspricht dem parameter *hChapter* in [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)).

Weitere Parameter finden Sie unter [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) in der *Referenz des OLE DB-Programmierers*.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) in der *Referenz des OLE DB-Programmierers*.

## <a name="irowsetupdateimplgetrowstatus"></a><a name="getrowstatus"></a>IRowsetUpdateImpl::GetRowStatus

Gibt den Status der angegebenen Zeilen zurück.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (GetRowStatus )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBPENDINGSTATUS rgPendingStatus[]);
```

#### <a name="parameters"></a>Parameter

*hReserviert*<br/>
[in] Entspricht dem *hChapter-Parameter* in [IRowsetUpdate::GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)).

Weitere Parameter finden Sie unter [IRowsetUpdate::GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)) in der *Referenz des OLE DB-Programmierers*.

## <a name="irowsetupdateimplundo"></a><a name="undo"></a>IRowsetUpdateImpl::Rückgängig

Macht alle Änderungen an der Zeile seit dem letzten Abruf oder der letzten Aktualisierung auf.

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

*hReserviert*<br/>
[in] Entspricht dem Parameter *hChapter* in [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

*pcRowsUndone*<br/>
[out] Entspricht dem *parameter pcRows* in [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

*prgRowsUndone*<br/>
[in] Entspricht dem *Parameter prgRows* in [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

Weitere Parameter finden Sie unter [IRowsetUpdate::Rückgängig](/previous-versions/windows/desktop/ms719655(v=vs.85)) in der *Referenz des OLE DB-Programmierers*.

## <a name="irowsetupdateimplupdate"></a><a name="update"></a>IRowsetUpdateImpl::Update

Überträgt alle Änderungen, die seit dem letzten Abruf oder der letzten Aktualisierung an der Zeile vorgenommen wurden.

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

*hReserviert*<br/>
[in] Entspricht dem Parameter *hChapter* in [IRowsetUpdate::Update](/previous-versions/windows/desktop/ms719709(v=vs.85)).

Weitere Parameter finden Sie unter [IRowsetUpdate::Update](/previous-versions/windows/desktop/ms719709(v=vs.85)) in der *Referenz des OLE DB-Programmierers*.

### <a name="remarks"></a>Bemerkungen

Änderungen werden durch Aufrufen von [IRowsetChangeImpl::FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md)übertragen. Der Consumer muss [CRowset::Update aufrufen,](../../data/oledb/crowset-update.md) damit die Änderungen wirksam werden. Legen Sie *prgRowstatus* auf einen geeigneten Wert fest, wie unter [Zeilenzustände](/previous-versions/windows/desktop/ms722752(v=vs.85)) in der Referenz des *OLE DB Programmerbeschriebenen*beschrieben.

## <a name="irowsetupdateimplisupdateallowed"></a><a name="isupdateallowed"></a>IRowsetUpdateImpl::IsUpdateAllowed

Überschreiben Sie diese Methode, um vor Aktualisierungen nach Sicherheit, Integrität usw. zu suchen.

### <a name="syntax"></a>Syntax

```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,
   HROW /* [in] */ /* hRowUpdate */,
   DBROWSTATUS* /* [out] */ /* pRowStatus */);
```

#### <a name="parameters"></a>Parameter

*Status*<br/>
[in] Der Status ausstehender Vorgänge in den Zeilen.

*hRowUpdate*<br/>
[in] Handle für die Zeilen, die der Benutzer aktualisieren möchte.

*pRowStatus*<br/>
[out] Der Status, der an den Benutzer zurückgegeben wurde.

### <a name="remarks"></a>Bemerkungen

Wenn Sie festlegen, dass eine Aktualisierung zulässig sein soll, gibt S_OK zurück. andernfalls gibt E_FAIL zurück. Wenn Sie eine Aktualisierung zulassen, müssen `DBROWSTATUS` Sie auch die in [IRowsetUpdateImpl::Update auf](../../data/oledb/irowsetupdateimpl-update.md) einen entsprechenden [Zeilenstatus](/previous-versions/windows/desktop/ms722752(v=vs.85))festlegen.

## <a name="irowsetupdateimplm_mapcacheddata"></a><a name="mapcacheddata"></a>IRowsetUpdateImpl::m_mapCachedData

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

*hRow*<br/>
Behandeln Sie die Zeilen für die Daten.

*pData*<br/>
Ein Zeiger auf die zwischenzuspeichernden Daten. Die Daten sind vom Typ *Storage* (die Benutzerdatensatzklasse). Siehe das *Argument Speichervorlage* in [iRowsetUpdateImpl Class](../../data/oledb/irowsetupdateimpl-class.md).

## <a name="see-also"></a>Siehe auch

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur von OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Erstellen eines updatable-Anbieters](../../data/oledb/creating-an-updatable-provider.md)
