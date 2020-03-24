---
title: CArrayRowset-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL.CArrayRowset<TAccessor>
- ATL.CArrayRowset
- CArrayRowset
- ATL::CArrayRowset
- ATL::CArrayRowset<TAccessor>
- ATL::CArrayRowset::CArrayRowset
- CArrayRowset.CArrayRowset
- ATL.CArrayRowset.CArrayRowset
- ATL.CArrayRowset<TAccessor>.CArrayRowset
- CArrayRowset::CArrayRowset
- CArrayRowset<TAccessor>::CArrayRowset
- ATL::CArrayRowset<TAccessor>::CArrayRowset
- CArrayRowset<TAccessor>.Snapshot
- ATL::CArrayRowset::Snapshot
- Snapshot
- CArrayRowset<TAccessor>::Snapshot
- ATL.CArrayRowset.Snapshot
- ATL.CArrayRowset<TAccessor>.Snapshot
- ATL::CArrayRowset<TAccessor>::Snapshot
- CArrayRowset::Snapshot
- CArrayRowset.Snapshot
- CArrayRowset::operator[]
- CArrayRowset.operator[]
- ATL::CArrayRowset::m_nRowsRead
- ATL::CArrayRowset<TAccessor>::m_nRowsRead
- CArrayRowset<TAccessor>::m_nRowsRead
- ATL.CArrayRowset<TAccessor>.m_nRowsRead
- CArrayRowset.m_nRowsRead
- m_nRowsRead
- ATL.CArrayRowset.m_nRowsRead
- CArrayRowset::m_nRowsRead
helpviewer_keywords:
- CArrayRowset class
- CArrayRowset class, constructor
- Snapshot method
- operator [], arrays
- '[] operator'
- operator[], arrays
- m_nRowsRead
ms.assetid: 511427e1-73ca-4fd8-9ba1-ae9463557cb6
ms.openlocfilehash: 0c5159ac5b834c7c31d980a412f28f8129e15b45
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212263"
---
# <a name="carrayrowset-class"></a>CArrayRowset-Klasse

Greift mithilfe der Array Syntax auf Elemente eines Rowsets zu.

## <a name="syntax"></a>Syntax

```cpp
template < class TAccessor >
class CArrayRowset :
   public CVirtualBuffer <TAccessor>,
   protected CBulkRowset <TAccessor>
```

### <a name="parameters"></a>Parameter

*TAccessor*<br/>
Der Typ der Accessorklasse, die vom Rowset verwendet werden soll.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Methoden

|||
|-|-|
|[CArrayRowset](#carrayrowset)|Konstruktor.|
|[Momentaufnahme](#snapshot)|Liest das gesamte Rowset in den Arbeitsspeicher.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|[KOM&#91;&#93;](#operator)|Greift auf ein Element des Rowsets zu.|

### <a name="data-members"></a>Datenelemente

|||
|-|-|
|[CArrayRowset::m_nRowsRead](#nrowsread)|Die Anzahl der bereits gelesenen Zeilen.|

## <a name="carrayrowsetcarrayrowset"></a><a name="carrayrowset"></a>CArrayRowset:: CArrayRowset

Erstellt ein neues `CArrayRowset`-Objekt.

### <a name="syntax"></a>Syntax

```cpp
CArrayRowset(int nMax = 100000);
```

#### <a name="parameters"></a>Parameter

*nMax*<br/>
in Maximale Anzahl von Zeilen im Rowset.

## <a name="carrayrowsetsnapshot"></a><a name="snapshot"></a>CArrayRowset:: Snapshot

Liest das gesamte Rowset in den Arbeitsspeicher, wobei ein Bild oder eine Momentaufnahme erstellt wird.

### <a name="syntax"></a>Syntax

```cpp
HRESULT Snapshot() throw();
```

## <a name="carrayrowsetoperator"></a><a name="operator"></a>CArrayRowset::-Operator

Stellt eine Array ähnliche Syntax für den Zugriff auf eine Zeile im Rowset bereit.

### <a name="syntax"></a>Syntax

```cpp
TAccessor & operator[](int nrow);
```

#### <a name="parameters"></a>Parameter

*TAccessor*<br/>
Ein Vorlagen Parameter, der den Typ des im Rowset gespeicherten Accessors angibt.

*nzeile*<br/>
in Die Nummer der Zeile (Array Element), auf die Sie zugreifen möchten.

### <a name="return-value"></a>Rückgabewert

Der Inhalt der angeforderten Zeile.

### <a name="remarks"></a>Bemerkungen

Wenn die Anzahl der Zeilen im Rowset von *nrow* überschritten wird, wird eine Ausnahme ausgelöst.

## <a name="carrayrowsetm_nrowsread"></a><a name="nrowsread"></a>CArrayRowset:: m_nRowsRead

Enthält die Anzahl der Zeilen im Rowset, die bereits gelesen wurden.

### <a name="syntax"></a>Syntax

```cpp
ULONG m_nRowsRead;
```

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz der OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CRowset-Klasse](../../data/oledb/crowset-class.md)
