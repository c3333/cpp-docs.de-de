---
title: CAccessorRowset-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAccessorRowset
- ATL.CAccessorRowset
- ATL::CAccessorRowset
- CAccessorRowset.Bind
- CAccessorRowset::Bind
- CAccessorRowset::CAccessorRowset
- CAccessorRowset.CAccessorRowset
- ATL.CAccessorRowset.CAccessorRowset
- ATL::CAccessorRowset::CAccessorRowset
- CAccessorRowset.Close
- CAccessorRowset::Close
- CAccessorRowset::FreeRecordMemory
- CAccessorRowset.FreeRecordMemory
- CAccessorRowset.GetColumnInfo
- CAccessorRowset::GetColumnInfo
helpviewer_keywords:
- CAccessorRowset class
- CAccessorRowset class, methods
- CAccessorRowset class, members
- Bind method
- CAccessorRowset class, constructor
- Close method
- FreeRecordMemory method
- GetColumnInfo method
ms.assetid: bd4f58ed-cebf-4d43-8985-1e5fcbf06953
ms.openlocfilehash: 9ad4292b69d0219aa1732638ae250758e4456f4b
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843286"
---
# <a name="caccessorrowset-class"></a>CAccessorRowset-Klasse

Kapselt ein Rowset und die zugeordneten Accessoren in einer einzelnen Klasse.

## <a name="syntax"></a>Syntax

```cpp
template <class TAccessor = CNoAccessor,
   template <typename T> class TRowset = CRowset>
class CAccessorRowset : public TAccessor, public TRowset<TAccessor>
```

### <a name="parameters"></a>Parameter

*TAccessor*<br/>
Eine Accessor-Klasse.

*TRowset*<br/>
Eine Rowsetklasse.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldbcli.h

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

| Name | BESCHREIBUNG |
|--|--|
| [Zwick](#bind) | Erstellt Bindungen (wird verwendet, wenn `bBind` als **`false`** in [CCommand:: Open](../../data/oledb/ccommand-open.md)angegeben ist). |
| [CAccessorRowset](#caccessorrowset) | Konstruktor. |
| [Schließen](#close) | Schließt das Rowset und alle Accessoren. |
| [FreeRecordMemory](#freerecordmemory) | Gibt alle Spalten im aktuellen Datensatz frei, die freigegeben werden müssen. |
| [GetColumnInfo](#getcolumninfo) | Implementiert [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)). |

## <a name="remarks"></a>Bemerkungen

Die-Klasse `TAccessor` verwaltet den-Accessor. Die Klasse *TRowset* verwaltet das Rowset.

## <a name="caccessorrowsetbind"></a><a name="bind"></a> CAccessorRowset:: Bind

Erstellt die Bindungen, wenn Sie `bBind` als **`false`** in [CCommand:: Open](../../data/oledb/ccommand-open.md)angegeben haben.

### <a name="syntax"></a>Syntax

```cpp
HRESULT Bind();
```

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

## <a name="caccessorrowsetcaccessorrowset"></a><a name="caccessorrowset"></a> CAccessorRowset:: CAccessorRowset

Initialisiert das `CAccessorRowset`-Objekt.

### <a name="syntax"></a>Syntax

```cpp
CAccessorRowset();
```

## <a name="caccessorrowsetclose"></a><a name="close"></a> CAccessorRowset:: Close

Gibt alle aktiven Accessoren und das Rowset frei.

### <a name="syntax"></a>Syntax

```cpp
void Close();
```

### <a name="remarks"></a>Bemerkungen

Gibt jeden zugeordneten Arbeitsspeicher frei.

## <a name="caccessorrowsetfreerecordmemory"></a><a name="freerecordmemory"></a> CAccessorRowset:: freerecordmemory

Gibt alle Spalten im aktuellen Datensatz frei, die freigegeben werden müssen.

### <a name="syntax"></a>Syntax

```cpp
void FreeRecordMemory();
```

## <a name="caccessorrowsetgetcolumninfo"></a><a name="getcolumninfo"></a> CAccessorRowset:: GetColumnInfo

Ruft Spalten Informationen aus dem geöffneten Rowset ab.

### <a name="syntax"></a>Syntax

```cpp
HRESULT GetColumnInfo(DBORDINAL* pulColumns,
   DBCOLUMNINFO** ppColumnInfo,
   LPOLESTR* ppStrings) const;

HRESULT GetColumnInfo(DBORDINAL* pColumns,
   DBCOLUMNINFO** ppColumnInfo);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) in der *OLE DB-Programmier Referenz*.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Der Benutzer muss die zurückgegebenen Spalten Informationen und den Zeichen folgen Puffer freigeben. Verwenden Sie die zweite Version dieser Methode, wenn Sie [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) verwenden und die Bindungen überschreiben müssen.

Weitere Informationen finden Sie unter [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) in der *OLE DB-Programmier Referenz*.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz zu OLE DB Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)
