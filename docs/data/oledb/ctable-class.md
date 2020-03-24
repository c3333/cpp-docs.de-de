---
title: CTable-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL::CTable
- ATL.CTable
- CTable
- ATL.CTable.Open
- ATL::CTable::Open
- CTable::Open
- CTable.Open
helpviewer_keywords:
- CTable class
- Open method
ms.assetid: f13fdaa3-e198-4557-977d-54b0bbc3454d
ms.openlocfilehash: 47c9899889bbbf9b09300779691085786db0e088
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211145"
---
# <a name="ctable-class"></a>CTable-Klasse

Bietet eine Möglichkeit, direkt auf ein einfaches Rowset (ohne Parameter) zuzugreifen.

## <a name="syntax"></a>Syntax

```cpp
template <class TAccessor = CNoAccessor,
            template <typename T> class TRowset = CRowset>
class CTable :
   public CAccessorRowset <TAccessor, TRowset>
```

### <a name="parameters"></a>Parameter

*TAccessor*<br/>
Eine Accessor-Klasse.

*TRowset*<br/>
Eine Rowsetklasse.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Methoden

|||
|-|-|
|[Öffnen](#open)|Öffnet die Tabelle.|

## <a name="remarks"></a>Bemerkungen

Weitere Informationen zum Ausführen eines Befehls für den Zugriff auf ein Rowset finden Sie unter [CCommand](../../data/oledb/ccommand-class.md) .

## <a name="ctableopen"></a><a name="open"></a>CTable:: Open

Öffnet die Tabelle.

### <a name="syntax"></a>Syntax

```cpp
HRESULT Open(const CSession& session,
   LPCWSTR wszTableName,
   DBPROPSET* pPropSet = NULL,
   ULONG ulPropSets = 0) throw ();

HRESULT Open(const CSession& session,
   LPCSTR szTableName,
   DBPROPSET* pPropSet = NULL,
   ULONG ulPropSets = 0) throw ();

HRESULT Open(const CSession& session,
   DBID& dbid,
   DBPROPSET* pPropSet = NULL,
   ULONG ulPropSets = 0) throw ();
```

#### <a name="parameters"></a>Parameter

*Sitzung*<br/>
in Die Sitzung, für die die Tabelle geöffnet wird.

*wsztablename*<br/>
in Der Name der zu öffnenden Tabelle, die als Unicode-Zeichenfolge an Sie übermittelt wird.

*sztablename*<br/>
in Der Name der zu öffnenden Tabelle, die als ANSI-Zeichenfolge übermittelt wird.

*dbid*<br/>
in Der `DBID` der zu öffnenden Tabelle.

*ppropset*<br/>
in Ein Zeiger auf ein Array von [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) -Strukturen, das Eigenschaften und Werte enthält, die festgelegt werden sollen. Informationen zu [Eigenschafts Sätzen und Eigenschafts Gruppen](/previous-versions/windows/desktop/ms713696(v=vs.85)) finden Sie in der *OLE DB Programmierer-Referenz* im Windows SDK. Der Standardwert von NULL gibt keine Eigenschaften an.

*ulpropsets*<br/>
in Die Anzahl von [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) -Strukturen, die im *ppropset* -Argument übergeben werden.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [IOpenRowset:: OPENROWSET](/previous-versions/windows/desktop/ms716724(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz der OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)
