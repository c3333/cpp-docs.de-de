---
title: CSession-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSession
- ATL::CSession
- ATL.CSession
- CSession.Abort
- CSession::Abort
- ATL.CSession.Abort
- ATL::CSession::Abort
- CSession::Close
- ATL.CSession.Close
- CSession.Close
- ATL::CSession::Close
- CSession.Commit
- ATL.CSession.Commit
- ATL::CSession::Commit
- CSession::Commit
- GetTransactionInfo
- CSession.GetTransactionInfo
- ATL.CSession.GetTransactionInfo
- CSession::GetTransactionInfo
- ATL::CSession::GetTransactionInfo
- ATL::CSession::Open
- CSession::Open
- CSession.Open
- ATL.CSession.Open
- CSession::StartTransaction
- StartTransaction
- ATL.CSession.StartTransaction
- CSession.StartTransaction
- ATL::CSession::StartTransaction
helpviewer_keywords:
- CSession class
- Abort method
- Close method
- Commit method
- GetTransactionInfo method
- Open method
- StartTransaction method
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
ms.openlocfilehash: f507ed432e107f586d34bb6b08fa9d3f7dc509d8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507243"
---
# <a name="csession-class"></a>CSession-Klasse

Stellt eine einzelne Datenbankzugriffs Sitzung dar.

## <a name="syntax"></a>Syntax

```cpp
class CSession
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Methoden

| Name | Beschreibung |
|-|-|
|[Abbruch](#abort)|Bricht die Transaktion ab (beendet Sie).|
|[Schließen](#close)|Schließt die Sitzung.|
|[Commit](#commit)|Führt ein Commit der Transaktion aus.|
|[GetTransactionInfo](#gettransactioninfo)|Gibt Informationen zu einer Transaktion zurück.|
|[Öffnen](#open)|Öffnet eine neue Sitzung für das Datenquellen Objekt.|
|[Start Transaction](#starttransaction)|Startet eine neue Transaktion für diese Sitzung.|

## <a name="remarks"></a>Bemerkungen

Eine oder mehrere Sitzungen können jeder Anbieter Verbindung (Datenquelle) zugeordnet werden, die durch ein [CDataSource](../../data/oledb/cdatasource-class.md) -Objekt dargestellt wird. Um einen neuen `CSession` für einen zu erstellen `CDataSource` , rufen Sie [CSession:: Open](#open)auf. Zum Starten einer Datenbanktransaktion `CSession` stellt die- `StartTransaction` Methode bereit. Nachdem eine Transaktion gestartet wurde, können Sie Sie mithilfe der-Methode übertragen `Commit` oder mit der- `Abort` Methode abbrechen.

## <a name="csessionabort"></a><a name="abort"></a> CSession:: Abort

Beendet die Transaktion.

### <a name="syntax"></a>Syntax

```cpp
HRESULT Abort(BOID* pboidReason = NULL,
   BOOL bRetaining = FALSE,
   BOOL bAsync = FALSE) const throw();
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [ITransaction:: Abort](/previous-versions/windows/desktop/ms709833(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

## <a name="csessionclose"></a><a name="close"></a> CSession:: Close

Schließt die Sitzung, die von [CSession:: Open](#open)geöffnet wurde.

### <a name="syntax"></a>Syntax

```cpp
void Close() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt den- `m_spOpenRowset` Zeiger frei.

## <a name="csessioncommit"></a><a name="commit"></a> CSession:: Commit

Führt ein Commit der Transaktion aus.

### <a name="syntax"></a>Syntax

```cpp
HRESULT Commit(BOOL bRetaining = FALSE,
   DWORD grfTC = XACTTC_SYNC,
   DWORD grfRM = 0) const throw();
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [ITransaction:: Commit](/previous-versions/windows/desktop/ms713008(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [ITransaction:: Commit](/previous-versions/windows/desktop/ms713008(v=vs.85)).

## <a name="csessiongettransactioninfo"></a><a name="gettransactioninfo"></a> CSession:: gettransaktioninfo

Gibt Informationen zu einer Transaktion zurück.

### <a name="syntax"></a>Syntax

```cpp
HRESULT GetTransactionInfo(XACTTRANSINFO* pInfo) const throw();
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [ITransaction:: gettransaktioninfo](/previous-versions/windows/desktop/ms714975(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [ITransaction:: gettransaktioninfo](/previous-versions/windows/desktop/ms714975(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="csessionopen"></a><a name="open"></a> CSession:: Open

Öffnet eine neue Sitzung für das Datenquellen Objekt.

### <a name="syntax"></a>Syntax

```cpp
HRESULT Open(const CDataSource& ds,
   DBPROPSET *pPropSet = NULL,
   ULONG ulPropSets = 0) throw();
```

#### <a name="parameters"></a>Parameter

*DS*<br/>
in Die Datenquelle, für die die Sitzung geöffnet werden soll.

*pPropSet*<br/>
in Ein Zeiger auf ein Array von [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) -Strukturen, das Eigenschaften und Werte enthält, die festgelegt werden sollen. Informationen zu [Eigenschafts Sätzen und Eigenschafts Gruppen](/previous-versions/windows/desktop/ms713696(v=vs.85)) finden Sie in der *OLE DB Programmierer-Referenz* im Windows SDK.

*ulpropsets*<br/>
in Die Anzahl von [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) -Strukturen, die im *ppropset* -Argument übergeben werden.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Sie müssen das Datenquellen Objekt mithilfe von [CDataSource:: Open](./cdatasource-class.md#open) öffnen, bevor Sie es an übergeben `CSession::Open` .

## <a name="csessionstarttransaction"></a><a name="starttransaction"></a> CSession:: Start Transaction

Startet eine neue Transaktion für diese Sitzung.

### <a name="syntax"></a>Syntax

```cpp
HRESULT StartTransaction(ISOLEVEL isoLevel = ISOLATIONLEVEL_READCOMMITTED,
   ULONG isoFlags = 0,
   ITransactionOptions* pOtherOptions = NULL,
   ULONG* pulTransactionLevel = NULL) const throw();
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie in der *OLE DB Programmierer-Referenz*unter [ITransaction local:: Start Transaction](/previous-versions/windows/desktop/ms709786(v=vs.85)) .

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [ITransaction local:: Start Transaction](/previous-versions/windows/desktop/ms709786(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="see-also"></a>Weitere Informationen

[CatDB](../../overview/visual-cpp-samples.md)<br/>
[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz zu OLE DB Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)
