---
title: CSimpleRow-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSimpleRow
- ATL::CSimpleRow
- ATL.CSimpleRow
- CSimpleRow::AddRefRow
- AddRefRow
- ATL.CSimpleRow.AddRefRow
- ATL::CSimpleRow::AddRefRow
- CSimpleRow.AddRefRow
- CSimpleRow.Compare
- CSimpleRow::Compare
- ATL::CSimpleRow::CSimpleRow
- CSimpleRow.CSimpleRow
- ATL.CSimpleRow.CSimpleRow
- CSimpleRow::CSimpleRow
- ATL::CSimpleRow::ReleaseRow
- CSimpleRow::ReleaseRow
- ReleaseRow
- CSimpleRow.ReleaseRow
- ATL.CSimpleRow.ReleaseRow
- CSimpleRow.m_dwRef
- CSimpleRow::m_dwRef
- CSimpleRow::m_iRowset
- CSimpleRow.m_iRowset
helpviewer_keywords:
- CSimpleRow class
- AddRefRow method
- Compare method
- CSimpleRow class, constructor
- ReleaseRow method
- m_dwRef
- m_iRowset
ms.assetid: 06d9621d-60cc-4508-8b0c-528d1b1a809b
ms.openlocfilehash: c0d7ea0966b9a582e4a6969573458bca2e8a0fea
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507222"
---
# <a name="csimplerow-class"></a>CSimpleRow-Klasse

Stellt eine Standard Implementierung für das Zeilen Handle bereit, das in der [irowmentimpl](../../data/oledb/irowsetimpl-class.md) -Klasse verwendet wird.

## <a name="syntax"></a>Syntax

```cpp
class CSimpleRow
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** „atldb.h“

## <a name="members"></a>Members

### <a name="methods"></a>Methoden

| Name | Beschreibung |
|-|-|
|[AddRefRow](#addrefrow)|Fügt einem vorhandenen Zeilenhandle einen Verweiszähler hinzu.|
|[Vergleichen](#compare)|Vergleicht zwei Zeilen, um festzustellen, ob Sie auf dieselbe Zeilen Instanz verweisen.|
|[CSimpleRow](#csimplerow)|Der Konstruktor.|
|[ReleaseRow](#releaserow)|Gibt Zeilen frei.|

### <a name="data-members"></a>Datenelemente

| Name | Beschreibung |
|-|-|
|[m_dwRef](#dwref)|Verweis Zähler auf ein vorhandenes Zeilen handle.|
|[m_iRowset](#irowset)|Ein Index für das Rowset, das den Cursor darstellt.|

## <a name="remarks"></a>Bemerkungen

Ein Zeilen Handle ist logisch ein eindeutiges Tag für eine Ergebniszeile. `IRowsetImpl` erstellt ein neues `CSimpleRow` für jede in [IRowset timpl:: GetNextRows](./irowsetimpl-class.md#getnextrows)angeforderte Zeile. `CSimpleRow` kann auch durch ihre eigene Implementierung des Zeilen Handles ersetzt werden, da es sich um ein Standardvorlagen Argument für handelt `IRowsetImpl` . Die einzige Anforderung, diese Klasse zu ersetzen, besteht darin, dass die Ersetzungs Klasse einen Konstruktor bereitstellt, der einen einzelnen Parameter vom Typ **Long**akzeptiert.

## <a name="csimplerowaddrefrow"></a><a name="addrefrow"></a> Csimplerow:: Adresszeilen

Fügt einem vorhandenen Zeilen handle Thread sicher einen Verweis Zähler hinzu.

### <a name="syntax"></a>Syntax

```cpp
DWORD AddRefRow();
```

## <a name="csimplerowcompare"></a><a name="compare"></a> Csimplerow:: Compare

Vergleicht zwei Zeilen, um festzustellen, ob Sie auf dieselbe Zeilen Instanz verweisen.

### <a name="syntax"></a>Syntax

```cpp
HRESULT Compare(CSimpleRow* pRow);
```

#### <a name="parameters"></a>Parameter

*pRow*<br/>
Ein Zeiger auf ein `CSimpleRow`-Objekt.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Wert, der in der Regel S_OK ist, der angibt, dass die beiden Zeilen dieselbe Zeilen Instanz oder S_FALSE sind, was bedeutet, dass die beiden Zeilen unterschiedlich sind. Weitere mögliche Rückgabewerte finden Sie unter [irowsee tidentity:: IsSameRow](/previous-versions/windows/desktop/ms719629(v=vs.85)) in der *OLE DB Programmierer*

## <a name="csimplerowcsimplerow"></a><a name="csimplerow"></a> Csimplerow:: csimplerow

Der Konstruktor.

### <a name="syntax"></a>Syntax

```cpp
CSimpleRow(DBCOUNTITEM iRowsetCur);
```

#### <a name="parameters"></a>Parameter

*irowsetcur*<br/>
in Index für das aktuelle Rowset.

### <a name="remarks"></a>Bemerkungen

Legt [m_iRowset](#irowset) auf *irowsetcur*fest.

## <a name="csimplerowreleaserow"></a><a name="releaserow"></a> Csimplerow:: releaserow

Gibt Zeilen auf Thread sichere Weise frei.

### <a name="syntax"></a>Syntax

```cpp
DWORD ReleaseRow();
```

## <a name="csimplerowm_dwref"></a><a name="dwref"></a> Csimplerow:: m_dwRef

Verweis Zähler auf ein vorhandenes Zeilen handle.

### <a name="syntax"></a>Syntax

```cpp
DWORD m_dwRef;
```

## <a name="csimplerowm_irowset"></a><a name="irowset"></a> Csimplerow:: m_iRowset

Index für das Rowset, das den Cursor darstellt.

### <a name="syntax"></a>Syntax

```cpp
KeyType m_iRowset;
```

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur der OLE DB-Anbieter Vorlage](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRow-timpl-Klasse](../../data/oledb/irowsetimpl-class.md)
