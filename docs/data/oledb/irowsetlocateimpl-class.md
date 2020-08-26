---
title: IRowsetLocateImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IRowsetLocateImpl
- ATL.IRowsetLocateImpl.Compare
- IRowsetLocateImpl::Compare
- IRowsetLocateImpl.Compare
- ATL::IRowsetLocateImpl::Compare
- GetRowsAt
- IRowsetLocateImpl.GetRowsAt
- ATL::IRowsetLocateImpl::GetRowsAt
- IRowsetLocateImpl::GetRowsAt
- ATL.IRowsetLocateImpl.GetRowsAt
- IRowsetLocateImpl::GetRowsByBookmark
- IRowsetLocateImpl.GetRowsByBookmark
- GetRowsByBookmark
- IRowsetLocateImpl::Hash
- IRowsetLocateImpl.Hash
- m_rgBookmarks
- IRowsetLocateImpl::m_rgBookmarks
- ATL.IRowsetLocateImpl.m_rgBookmarks
- ATL::IRowsetLocateImpl::m_rgBookmarks
- IRowsetLocateImpl.m_rgBookmarks
helpviewer_keywords:
- providers, bookmarks
- IRowsetLocateImpl class
- bookmarks, OLE DB
- Compare method
- GetRowsAt method
- GetRowsByBookmark method
- Hash method
- m_rgbookmarks
ms.assetid: a8aa3149-7ce8-4976-a680-2da193fd3234
ms.openlocfilehash: a45b7ef1a31c3ecf34b15ee35bce48559465a905
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840309"
---
# <a name="irowsetlocateimpl-class"></a>IRowsetLocateImpl-Klasse

Implementiert die [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85)) -Schnittstelle OLE DB, die beliebige Zeilen aus einem Rowset abruft.

## <a name="syntax"></a>Syntax

```cpp
template <
   class T,
   class RowsetInterface,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap < RowClass::KeyType, RowClass* >,
   class BookmarkKeyType = LONG,
   class BookmarkType = LONG,
   class BookmarkMapClass = CAtlMap < RowClass::KeyType, RowClass* >>
class ATL_NO_VTABLE IRowsetLocateImpl : public IRowsetImpl<
       T,
       RowsetInterface,
       RowClass,
       MapClass>
```

### <a name="parameters"></a>Parameter

*T*<br/>
Eine von abgeleitete Klasse `IRowsetLocateImpl` .

*RowsetInterface*<br/>
Eine von abgeleitete Klasse `IRowsetImpl` .

*RowClass*<br/>
Die Speichereinheit für das `HROW` .

*Mapclass*<br/>
Die Speichereinheit für alle Zeilen Handles, die vom Anbieter gehalten werden.

*Bookmarkkeytype*<br/>
Der Typ des Lesezeichens, z. b. eine lange oder eine Zeichenfolge. Gewöhnliche Lesezeichen müssen eine Länge von mindestens zwei Bytes aufweisen. (Die Einzel Byte Länge ist für die OLE DB [Standard-Lesezeichen](/previous-versions/windows/desktop/ms712954(v=vs.85)) `DBBMK_FIRST` , `DBBMK_LAST` und reserviert `DBBMK_INVALID` .)

*Bookmarktype*<br/>
Der Mapping-Mechanismus zum Verwalten von Lesezeichen-zu-Daten-Beziehungen.

*Bookmarkmapclass*<br/>
Die Speichereinheit für alle Zeilen Handles, die vom Lesezeichen gehalten werden.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header**: Atldb. h

## <a name="members"></a>Member

### <a name="interface-methods"></a>Schnittstellenmethoden

| Name | Beschreibung |
|-|-|
|[Vergleichen](#compare)|Vergleicht zwei Lesezeichen.|
|[GetRowsAt](#getrowsat)|Ruft Zeilen ab, beginnend mit der Zeile, die durch einen Offset von einem Lesezeichen angegeben wird.|
|[GetRowsByBookmark](#getrowsbybookmark)|Ruft die Zeilen ab, die den angegebenen Lesezeichen entsprechen.|
|[Hash](#hash)|Gibt Hashwerte für die angegebenen Lesezeichen zurück.|

### <a name="data-members"></a>Datenelemente

| Name | Beschreibung |
|-|-|
|[m_rgBookmarks](#rgbookmarks)|Ein Array von Lesezeichen.|

## <a name="remarks"></a>Bemerkungen

`IRowsetLocateImpl` ist die OLE DB Vorlagen Implementierung der [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85)) -Schnittstelle. `IRowsetLocate` dient zum Abrufen beliebiger Zeilen aus einem Rowset. Ein Rowset, das diese Schnittstelle nicht implementiert, ist ein `sequential` Rowset. Wenn `IRowsetLocate` in einem Rowset vorhanden ist, ist Spalte 0 das Lesezeichen für die Zeilen. beim Lesen dieser Spalte wird ein Lesezeichen Wert abgerufen, der zum Neupositionieren der gleichen Zeile verwendet werden kann.

`IRowsetLocateImpl` wird verwendet, um die Lesezeichen Unterstützung in-Anbietern zu implementieren. Lesezeichen sind Platzhalter (Indizes für ein Rowset), mit denen der Consumer schnell zu einer Zeile zurückkehren kann, sodass hoch Geschwindigkeits Zugriff auf Daten möglich ist. Der Anbieter bestimmt, welche Lesezeichen eine Zeile eindeutig identifizieren können. Mithilfe von `IRowsetLocateImpl` Methoden können Sie Lesezeichen vergleichen, Zeilen nach Offset abrufen, Zeilen nach Lesezeichen abrufen und Hashwerte für Lesezeichen zurückgeben.

Damit OLE DB Lesezeichen in einem Rowset unterstützt werden, müssen Sie das Rowset von dieser Klasse erben.

Informationen zum Implementieren der Lesezeichen Unterstützung finden Sie unter [Anbieter Unterstützung für Lesezeichen](../../data/oledb/provider-support-for-bookmarks.md) im *Visual C++ Programmierer-Handbuch* und [Lesezeichen](/previous-versions/windows/desktop/ms709728(v=vs.85)) in der *OLE DB Programmierer-Referenz* im Platform SDK.

## <a name="irowsetlocateimplcompare"></a><a name="compare"></a> Irowsetloreseimpl:: Compare

Vergleicht zwei Lesezeichen.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (Compare )(HCHAPTER /* hReserved */,
   DBBKMARK cbBookmark1,
   const BYTE* pBookmark1,
   DBBKMARK cbBookmark2,
   const BYTE* pBookmark2,
   DBCOMPARE* pComparison);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IRowsetLocate:: Compare](/previous-versions/windows/desktop/ms709539(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

### <a name="remarks"></a>Bemerkungen

Eines der Lesezeichen kann ein Standard OLE DB definiertes [Standard-Lesezeichen](/previous-versions/windows/desktop/ms712954(v=vs.85)) ( `DBBMK_FIRST` , `DBBMK_LAST` oder `DBBMK_INVALID` ) sein. Der in zurückgegebene Wert `pComparison` gibt die Beziehung zwischen den beiden Lesezeichen an:

- DBCOMPARE_LT ( `cbBookmark1` ist vor `cbBookmark2` .)

- DBCOMPARE_EQ ( `cbBookmark1` ist gleich `cbBookmark2` .)

- DBCOMPARE_GT ( `cbBookmark1` ist nach `cbBookmark2` .)

- DBCOMPARE_NE (die Lesezeichen sind gleich und nicht geordnet.)

- DBCOMPARE_NOTCOMPARABLE (die Lesezeichen können nicht verglichen werden.)

## <a name="irowsetlocateimplgetrowsat"></a><a name="getrowsat"></a> Irowsetloalisieimpl:: GetRowsAt

Ruft Zeilen ab, beginnend mit der Zeile, die durch einen Offset von einem Lesezeichen angegeben wird.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (GetRowsAt )(HWATCHREGION /* hReserved1 */,
   HCHAPTER hReserved2,
   DBBKMARK cbBookmark,
   const BYTE* pBookmark,
   DBROWOFFSET lRowsOffset,
   DBROWCOUNT cRows,
   DBCOUNTITEM* pcRowsObtained,
   HROW** prghRows);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IRowsetLocate:: GetRowsAt](/previous-versions/windows/desktop/ms723031(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

### <a name="remarks"></a>Bemerkungen

Um stattdessen von der Cursorposition abzurufen, verwenden Sie [IRowset:: GetRowsAt](/previous-versions/windows/desktop/ms723031(v=vs.85)).

`IRowsetLocateImpl::GetRowsAt` die Cursorposition wird nicht geändert.

## <a name="irowsetlocateimplgetrowsbybookmark"></a><a name="getrowsbybookmark"></a> Irowsetloalisieimpl:: GetRowsByBookmark

Ruft eine oder mehrere Zeilen ab, die den angegebenen Lesezeichen entsprechen.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (GetRowsByBookmark )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const DBBKMARK rgcbBookmarks[],
   const BYTE* rgpBookmarks,
   HROW rghRows[],
   DBROWSTATUS* rgRowStatus[]);
```

#### <a name="parameters"></a>Parameter

*hreserved*<br/>
in Entspricht dem *hChapter* -Parameter für [IRowsetLocate:: GetRowsByBookmark](/previous-versions/windows/desktop/ms725420(v=vs.85)).

Informationen zu anderen Parametern finden Sie unter [IRowsetLocate:: GetRowsByBookmark](/previous-versions/windows/desktop/ms725420(v=vs.85)) in der *OLE DB-Programmier Referenz*.

### <a name="remarks"></a>Bemerkungen

Beim Lesezeichen kann es sich um einen von Ihnen definierten Wert oder um OLE DB [Standard-Lesezeichen](/previous-versions/windows/desktop/ms712954(v=vs.85)) ( `DBBMK_FIRST` oder `DBBMK_LAST` ) handeln. Die Cursorposition wird nicht geändert.

## <a name="irowsetlocateimplhash"></a><a name="hash"></a> Irowsetloalisieimpl:: Hash

Gibt Hashwerte für die angegebenen Lesezeichen zurück.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (Hash )(HCHAPTER /* hReserved */,
   DBBKMARK cbBookmarks,
   const DBBKMARK* rgcbBookmarks[],
   const BYTE* rgpBookmarks[],
   DBHASHVALUE rgHashValues[],
   DBROWSTATUS rgBookmarkStatus[]);
```

#### <a name="parameters"></a>Parameter

*hreserved*<br/>
in Entspricht dem *hChapter* -Parameter für [IRowsetLocate:: Hash](/previous-versions/windows/desktop/ms709697(v=vs.85)).

Informationen zu anderen Parametern finden Sie unter [IRowsetLocate:: Hash](/previous-versions/windows/desktop/ms709697(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="irowsetlocateimplm_rgbookmarks"></a><a name="rgbookmarks"></a> Irowsetloalisieimpl:: m_rgBookmarks

Ein Array von Lesezeichen.

### <a name="syntax"></a>Syntax

```cpp
CAtlArray<DBROWCOUNT> m_rgBookmarks;
```

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur der OLE DB-Anbieter Vorlage](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetLocate: IRowset](/previous-versions/windows/desktop/ms721190(v=vs.85)) 
 [Anbieter Unterstützung für Lesezeichen](../../data/oledb/provider-support-for-bookmarks.md)<br/>
[Lesezeichen](/previous-versions/windows/desktop/ms709728(v=vs.85))
