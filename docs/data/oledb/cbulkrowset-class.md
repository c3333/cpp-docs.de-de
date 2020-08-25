---
title: CBulkRowset-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL::CBulkRowset
- ATL.CBulkRowset
- ATL::CBulkRowset<TAccessor>
- CBulkRowset
- ATL.CBulkRowset<TAccessor>
- CBulkRowset::AddRefRows
- CBulkRowset.AddRefRows
- ATL.CBulkRowset<TAccessor>.AddRefRows
- ATL::CBulkRowset::AddRefRows
- CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset.AddRefRows
- ATL::CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset<TAccessor>.CBulkRowset
- ATL::CBulkRowset::CBulkRowset
- CBulkRowset.CBulkRowset
- CBulkRowset::CBulkRowset
- ATL.CBulkRowset.CBulkRowset
- ATL::CBulkRowset<TAccessor>::CBulkRowset
- CBulkRowset<TAccessor>::CBulkRowset
- ATL.CBulkRowset.MoveFirst
- CBulkRowset<TAccessor>.MoveFirst
- ATL.CBulkRowset<TAccessor>.MoveFirst
- ATL::CBulkRowset::MoveFirst
- ATL::CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset::MoveFirst
- CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset.MoveFirst
- CBulkRowset.MoveLast
- ATL.CBulkRowset.MoveLast
- ATL::CBulkRowset<TAccessor>::MoveLast
- CBulkRowset::MoveLast
- CBulkRowset<TAccessor>.MoveLast
- ATL::CBulkRowset::MoveLast
- ATL.CBulkRowset<TAccessor>.MoveLast
- CBulkRowset<TAccessor>::MoveLast
- ATL.CBulkRowset<TAccessor>.MoveNext
- ATL::CBulkRowset::MoveNext
- CBulkRowset::MoveNext
- ATL.CBulkRowset.MoveNext
- CBulkRowset.MoveNext
- ATL::CBulkRowset<TAccessor>::MoveNext
- CBulkRowset<TAccessor>.MoveNext
- CBulkRowset<TAccessor>::MoveNext
- CBulkRowset::MovePrev
- CBulkRowset<TAccessor>::MovePrev
- ATL::CBulkRowset<TAccessor>::MovePrev
- CBulkRowset<TAccessor>.MovePrev
- ATL::CBulkRowset::MovePrev
- CBulkRowset.MovePrev
- ATL.CBulkRowset.MovePrev
- ATL.CBulkRowset<TAccessor>.MovePrev
- CBulkRowset<TAccessor>::MoveToBookmark
- CBulkRowset.MoveToBookmark
- ATL.CBulkRowset.MoveToBookmark
- CBulkRowset::MoveToBookmark
- ATL::CBulkRowset<TAccessor>::MoveToBookmark
- ATL::CBulkRowset::MoveToBookmark
- CBulkRowset.MoveToRatio
- ATL::CBulkRowset::MoveToRatio
- CBulkRowset::MoveToRatio
- ATL.CBulkRowset<TAccessor>.MoveToRatio
- ATL::CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset.MoveToRatio
- CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset<TAccessor>.ReleaseRows
- ATL::CBulkRowset<TAccessor>::ReleaseRows
- ATL.CBulkRowset.ReleaseRows
- CBulkRowset<TAccessor>::ReleaseRows
- ATL::CBulkRowset::ReleaseRows
- CBulkRowset::ReleaseRows
- CBulkRowset.ReleaseRows
- ATL.CBulkRowset.SetRows
- CBulkRowset::SetRows
- CBulkRowset<TAccessor>.SetRows
- ATL.CBulkRowset<TAccessor>.SetRows
- CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset::SetRows
- CBulkRowset.SetRows
- SetRows
helpviewer_keywords:
- CBulkRowset class
- AddRefRows method
- CBulkRowset class, constructor
- MoveFirst method
- MoveLast method
- MoveNext method
- MovePrev method
- MoveToBookmark method
- MoveToRatio method
- ReleaseRows method
- SetRows method
ms.assetid: c6bde426-c543-4022-a98a-9519d9e2ae59
ms.openlocfilehash: 5c1c7bc381d30f701bad123807689b08ea47f65d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838463"
---
# <a name="cbulkrowset-class"></a>CBulkRowset-Klasse

Ruft Zeilen ab und manipuliert Sie, um Daten in einem Massen Vorgang zu bearbeiten, indem mehrere Zeilen Handles mit einem einzigen-Befehl abgerufen werden.

## <a name="syntax"></a>Syntax

```cpp
template <class TAccessor>
class CBulkRowset : public CRowset<TAccessor>
```

### <a name="parameters"></a>Parameter

*TAccessor*<br/>
Eine Accessor-Klasse.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldbcli.h

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

| Name | Beschreibung |
|-|-|
|[AddRefRows](#addrefrows)|Erhöht den Verweis Zähler.|
|[CBulkRowset](#cbulkrowset)|Konstruktor.|
|[MoveFirst](#movefirst)|Ruft die erste Daten Zeile ab und führt ggf. einen neuen Massen Abruf aus.|
|[MoveLast](#movelast)|Wechselt zur letzten Zeile.|
|[MoveNext](#movenext)|Ruft die nächste Daten Zeile ab.|
|[MovePrev](#moveprev)|Wechselt zur vorherigen Zeile.|
|[MoveToBookmark](#movetobookmark)|Ruft die Zeile ab, die durch ein Lesezeichen oder die Zeile an einem angegebenen Offset aus diesem Lesezeichen gekennzeichnet ist.|
|[MoveToRatio](#movetoratio)|Ruft Zeilen ab einer Bruch Position im Rowset ab.|
|[ReleaseRows](#releaserows)|Legt die aktuelle Zeile ( `m_nCurrentRow` ) auf 0 (null) fest und gibt alle Zeilen frei.|
|[SetRows](#setrows)|Legt die Anzahl der Zeilen Handles fest, die durch einen-Befehl abgerufen werden sollen.|

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Verwendung der- `CBulkRowset` Klasse veranschaulicht.

[!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/cpp/cbulkrowset-class_1.cpp)]

## <a name="cbulkrowsetaddrefrows"></a><a name="addrefrows"></a> CBulkRowset:: adressfrows

Ruft [IRowset:: adressfrows](/previous-versions/windows/desktop/ms719619(v=vs.85)) auf, um den Verweis Zähler für alle derzeit aus dem BULK-Rowset abgerufenen Zeilen zu erhöhen.

### <a name="syntax"></a>Syntax

```cpp
HRESULT AddRefRows() throw();
```

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

## <a name="cbulkrowsetcbulkrowset"></a><a name="cbulkrowset"></a> CBulkRowset:: CBulkRowset

Erstellt ein neues `CBulkRowset` -Objekt und legt die Standardzeilen Anzahl auf 10 fest.

### <a name="syntax"></a>Syntax

```cpp
CBulkRowset();
```

## <a name="cbulkrowsetmovefirst"></a><a name="movefirst"></a> CBulkRowset:: vfirst

Ruft die erste Daten Zeile ab.

### <a name="syntax"></a>Syntax

```cpp
HRESULT MoveFirst() throw();
```

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

## <a name="cbulkrowsetmovelast"></a><a name="movelast"></a> CBulkRowset:: muvelast

Wechselt zur letzten Zeile.

### <a name="syntax"></a>Syntax

```cpp
HRESULT MoveLast() throw();
```

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

## <a name="cbulkrowsetmovenext"></a><a name="movenext"></a> CBulkRowset:: wvenext

Ruft die nächste Daten Zeile ab.

### <a name="syntax"></a>Syntax

```cpp
HRESULT MoveNext() throw();
```

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard. Wenn das Ende des Rowsets erreicht ist, gibt DB_S_ENDOFROWSET zurück.

## <a name="cbulkrowsetmoveprev"></a><a name="moveprev"></a> CBulkRowset:: vprev

Wechselt zur vorherigen Zeile.

### <a name="syntax"></a>Syntax

```cpp
HRESULT MovePrev() throw();
```

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

## <a name="cbulkrowsetmovetobookmark"></a><a name="movetobookmark"></a> CBulkRowset:: muvedebookmark

Ruft die Zeile ab, die durch ein Lesezeichen oder die Zeile an einem angegebenen Offset (*lskip*) aus diesem Lesezeichen gekennzeichnet ist.

### <a name="syntax"></a>Syntax

```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark,
   DBCOUNTITEM lSkip = 0) throw();
```

#### <a name="parameters"></a>Parameter

*bookmark*<br/>
in Ein Lesezeichen, das den Speicherort markiert, von dem aus Sie Daten abrufen möchten.

*lskip*<br/>
in Die Anzahl der Zeilen aus dem Lesezeichen in die Zielzeile. Wenn *lskip* 0 (null) ist, wird die erste abgerufene Zeile in der Zeile mit Lesezeichen angezeigt. Wenn *lskip* den Wert 1 hat, ist die erste abgerufene Zeile die Zeile nach der Zeile mit Lesezeichen. Wenn *lskip* den Wert-1 hat, ist die erste Zeile, die abgerufen wird, die Zeile vor der Zeile mit Lesezeichen.

### <a name="return-value"></a>Rückgabewert

Weitere Informationen finden Sie unter [IRowset:: GetData](/previous-versions/windows/desktop/ms716988(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="cbulkrowsetmovetoratio"></a><a name="movetoratio"></a> CBulkRowset:: wvetoratio

Ruft Zeilen ab einer Bruch Position im Rowset ab.

### <a name="syntax"></a>Syntax

```cpp
HRESULT MoveToRatio(DBCOUNTITEM nNumerator,
   DBCOUNTITEM nDenominator)throw();
```

#### <a name="parameters"></a>Parameter

*nzähler*<br/>
in Der Zähler, der verwendet wird, um die Bruch Position zu bestimmen, von der Daten abgerufen werden sollen.

*nnenner*<br/>
in Der Nenner, der verwendet wird, um die Bruch Position zu bestimmen, von der Daten abgerufen werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

`MoveToRatio` die Zeilen werden ungefähr gemäß der folgenden Formel abgerufen:

`(nNumerator *  RowsetSize ) / nDenominator`

`RowsetSize`Dabei ist die Größe des Rowsets, gemessen in Zeilen. Die Genauigkeit dieser Formel hängt vom jeweiligen Anbieter ab. Weitere Informationen finden Sie unter [IRowsetScroll:: GetRowsAtRatio](/previous-versions/windows/desktop/ms709602(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="cbulkrowsetreleaserows"></a><a name="releaserows"></a> CBulkRowset:: ReleaseRows

Ruft [IRowset:: ReleaseRows](/previous-versions/windows/desktop/ms719771(v=vs.85)) auf, um den Verweis Zähler für alle derzeit aus dem BULK-Rowset abgerufenen Zeilen zu verringern.

### <a name="syntax"></a>Syntax

```cpp
HRESULT ReleaseRows() throw();
```

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

## <a name="cbulkrowsetsetrows"></a><a name="setrows"></a> CBulkRowset:: setRows

Legt die Anzahl der Zeilen Handles fest, die von jedem-Befehl abgerufen werden.

### <a name="syntax"></a>Syntax

```cpp
void SetRows(DBROWCOUNT nRows) throw();
```

#### <a name="parameters"></a>Parameter

*nRows*<br/>
in Die neue Größe des Rowsets (Anzahl der Zeilen).

### <a name="remarks"></a>Bemerkungen

Wenn Sie diese Funktion aufzurufen, muss Sie vor dem Öffnen des Rowsets liegen.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz zu OLE DB Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)
