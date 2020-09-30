---
title: CCommand-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL::CCommand
- CCommand
- ATL.CCommand
- CCommand.Close
- CCommand::Close
- CCommand.Create
- CCommand::Create
- CCommand.CreateCommand
- CreateCommand
- CCommand::CreateCommand
- ATL::CCommand::GetNextResult
- CCommand::GetNextResult
- GetNextResult
- CCommand.GetNextResult
- ATL.CCommand.GetNextResult
- GetParameterInfo
- CCommand.GetParameterInfo
- CCommand::GetParameterInfo
- ATL.CCommand.Open
- ATL::CCommand::Open
- CCommand.Open
- CCommand::Open
- CCommand.Prepare
- CCommand::Prepare
- Prepare
- CCommand.ReleaseCommand
- ReleaseCommand
- CCommand::ReleaseCommand
- SetParameterInfo
- CCommand.SetParameterInfo
- CCommand::SetParameterInfo
- Unprepare
- CCommand.Unprepare
- CCommand::Unprepare
helpviewer_keywords:
- CCommand class
- Close method
- Create method [C++]
- CreateCommand method
- GetNextResult method
- GetParameterInfo method
- Open method
- Prepare method
- ReleaseCommand method
- SetParameterInfo method
- Unprepare method
ms.assetid: 0760bfc5-b9ee-4aee-8e54-31bd78714d3a
ms.openlocfilehash: 109998dd742828b3c41672fa2afa8716e4687f6a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501009"
---
# <a name="ccommand-class"></a>CCommand-Klasse

Stellt Methoden bereit, um einen Befehl festzulegen und auszuführen.

## <a name="syntax"></a>Syntax

```cpp
template <class TAccessor = CNoAccessor,
   template <typename T> class TRowset = CRowset,
   class TMultiple = CNoMultipleResults>
class CCommand :
   public CAccessorRowset <TAccessor, TRowset>,
   public CCommandBase,
   public TMultiple
```

### <a name="parameters"></a>Parameter

*TAccessor*<br/>
Der Typ der Accessorklasse (z. b. `CDynamicParameterAccessor` , `CDynamicStringAccessor` oder `CEnumeratorAccessor` ), die vom Befehl verwendet werden soll. Der Standardwert ist. `CNoAccessor` dieser gibt an, dass die Klasse keine Parameter oder Ausgabespalten unterstützt.

*TRowset*<br/>
Der Typ der Rowsetklasse (z. b. `CArrayRowset` oder `CNoRowset` ), die vom Befehl verwendet werden soll. Der Standardwert lautet `CRowset`.

*TMultiple*<br/>
Um einen OLE DB Befehl zu verwenden, der mehrere Ergebnisse zurückgeben kann, geben Sie [CMultipleResults](../../data/oledb/cmultipleresults-class.md)an. Verwenden Sie andernfalls [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md). Weitere Informationen finden Sie unter [IMultipleResults](/previous-versions/windows/desktop/ms721289(v=vs.85)).

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Methoden

| Name | Beschreibung |
|-|-|
|[Schließen](#close)|Schließt den aktuellen Befehl.|
|[GetNextResult](#getnextresult)|Ruft das nächste Ergebnis ab, wenn mehrere Resultsets verwendet werden.|
|[Öffnen](#open)|Führt den Befehl aus und bindet ihn optional.|

### <a name="inherited-methods"></a>Geerbte Methoden

| Name | BESCHREIBUNG |
|-|-|
|[Erstellen](#create)|Erstellt einen neuen Befehl für die angegebene Sitzung und legt dann den Befehls Text fest.|
|[CreateCommand](#createcommand)|Erstellt einen neuen Befehl.|
|[GetParameterInfo](#getparameterinfo)|Ruft eine Liste mit den Parametern des Befehls, deren Namen und deren Typen ab.|
|[Vorbereiten](#prepare)|Überprüft und optimiert den aktuellen Befehl.|
|[ReleaseCommand](#releasecommand)|Gibt ggf. den Parameter Accessor frei und gibt dann den Befehl frei.|
|[SetParameterInfo](#setparameterinfo)|Gibt den systemeigenen Typ der einzelnen Befehlsparameter an.|
|[Unprepare](#unprepare)|Verwirft den aktuellen Befehls Ausführungsplan.|

## <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Klasse, wenn Sie einen Parameter basierten Vorgang ausführen oder einen Befehl ausführen müssen. Wenn Sie nur ein einfaches Rowset öffnen müssen, verwenden Sie stattdessen " [CTable](../../data/oledb/ctable-class.md) ".

Die von Ihnen verwendete Accessor-Klasse bestimmt die Methode zum Binden von Parametern und Daten.

Beachten Sie, dass Sie keine gespeicherten Prozeduren mit dem OLE DB Anbieter für Jet verwenden können, da dieser Anbieter keine gespeicherten Prozeduren unterstützt (nur Konstanten sind in Abfrage Zeichenfolgen zulässig).

## <a name="ccommandclose"></a><a name="close"></a> CCommand:: Close

Gibt das dem Befehl zugeordnete accessorrowset frei.

### <a name="syntax"></a>Syntax

```cpp
void Close();
```

### <a name="remarks"></a>Bemerkungen

Ein Befehl verwendet ein Rowset, einen resultsetaccessor und (optional) einen Parameter Accessor (im Gegensatz zu Tabellen, die keine Parameter unterstützen und keinen Parameter Accessor benötigen).

Wenn Sie einen Befehl ausführen, müssen Sie sowohl als `Close` auch [ReleaseCommand](#releasecommand) nach dem Befehl ausführen.

Wenn Sie denselben Befehl wiederholt ausführen möchten, sollten Sie jeden resultsetaccessor freigeben, indem Sie aufrufen, `Close` bevor Sie aufrufen `Execute` . Am Ende der Reihe sollten Sie den Parameter Accessor freigeben, indem Sie aufrufen `ReleaseCommand` . Ein weiteres häufiges Szenario ist das Aufrufen einer gespeicherten Prozedur mit Ausgabeparametern. Bei vielen Anbietern (z. b. der OLE DB Anbieter für SQL Server) ist der Zugriff auf die Ausgabeparameter Werte erst möglich, wenn Sie den resultsetaccessor schließen. Rufen `Close` Sie auf, um das zurückgegebene Rowset und den resultsetaccessor zu schließen, jedoch nicht den Parameter Accessor, damit Sie die Ausgabeparameter Werte abrufen können.

### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie Sie `Close` und `ReleaseCommand` aufrufen, wenn Sie wiederholt den gleichen Befehl ausführen.

[!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]

## <a name="ccommandgetnextresult"></a><a name="getnextresult"></a> CCommand:: GetNextResult

Ruft das nächste Resultset ab, sofern ein solches vorhanden ist.

### <a name="syntax"></a>Syntax

```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected,
   bool bBind = true) throw();
```

#### <a name="parameters"></a>Parameter

*pulrowsafffiziert*<br/>
[in/out] Ein Zeiger auf den Arbeitsspeicher, in dem die Anzahl der von einem Befehl betroffenen Zeilen zurückgegeben wird.

*bbind*<br/>
in Gibt an, ob der Befehl nach der Ausführung automatisch gebunden werden soll. Der Standardwert ist **`true`** , wodurch der Befehl automatisch gebunden wird. Wenn Sie *bbind* auf festlegen, wird **`false`** die automatische Bindung des Befehls verhindert, sodass Sie die Bindung manuell vornehmen können. (Manuelle Bindung ist für OLAP-Benutzer besonders interessant.)

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Wenn ein Resultset bereits abgerufen wurde, gibt diese Funktion das vorherige Resultset frei und hebt die Bindung der Spalten auf. Wenn *bbind* ist **`true`** , bindet es die neuen Spalten.

Sie sollten diese Funktion nur aufrufen, wenn Sie mehrere Ergebnisse angegeben haben, indem Sie den `CCommand` Vorlagen Parameter " *TMultiple*" festlegen = `CMultipleResults` .

## <a name="ccommandopen"></a><a name="open"></a> CCommand:: Open

Führt den Befehl aus und bindet ihn optional.

### <a name="syntax"></a>Syntax

```cpp
HRESULT Open(const CSession& session,
   LPCWSTR wszCommand,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(const CSession& session,
   LPCSTR szCommand,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(const CSession& session,
   INT szCommand = NULL,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();
```

#### <a name="parameters"></a>Parameter

*Sitzung*<br/>
in Die Sitzung, in der der Befehl ausgeführt werden soll.

*wszcommand*<br/>
in Der Befehl, der ausgeführt werden soll, als Unicode-Zeichenfolge. Kann NULL sein, wenn verwendet wird `CAccessor` . in diesem Fall wird der Befehl aus dem Wert abgerufen, der an das [DEFINE_COMMAND](./macros-and-global-functions-for-ole-db-consumer-templates.md#define_command) -Makro übermittelt wurde. Weitere Informationen finden Sie unter [ICommand:: Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) in der *OLE DB Programmierer-Referenz* .

*szCommand*<br/>
in Identisch mit *wszcommand* mit der Ausnahme, dass dieser Parameter eine ANSI-Befehls Zeichenfolge annimmt. Die vierte Form dieser Methode kann einen NULL-Wert annehmen. Weitere Informationen finden Sie unter "Hinweise" weiter unten in diesem Thema.

*pPropSet*<br/>
in Ein Zeiger auf ein Array von [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) -Strukturen, das Eigenschaften und Werte enthält, die festgelegt werden sollen. Informationen zu [Eigenschafts Sätzen und Eigenschafts Gruppen](/previous-versions/windows/desktop/ms713696(v=vs.85)) finden Sie in der *OLE DB Programmierer-Referenz* im Windows SDK.

*prowsafffiziert*<br/>
[in/out] Ein Zeiger auf den Arbeitsspeicher, in dem die Anzahl der von einem Befehl betroffenen Zeilen zurückgegeben wird. Wenn " * \* prowsafffiziert* " NULL ist, wird keine Zeilen Anzahl zurückgegeben. Andernfalls wird `Open` * \* prowsaff.* gemäß den folgenden Bedingungen festgelegt:

|Wenn|Then|
|--------|----------|
|Das- `cParamSets` Element von `pParams` ist größer als 1.|" * \* prowsaffzierte* " stellt die Gesamtzahl der Zeilen dar, die von allen in der Ausführung angegebenen Parametersätzen betroffen sind.|
|Die Anzahl der betroffenen Zeilen ist nicht verfügbar.|" * \* prowsafffiziert* " ist auf "-1" festgelegt.|
|Mit dem Befehl werden keine Zeilen aktualisiert, gelöscht oder eingefügt.|Das * \* Profil* ist nicht definiert.|

*guidcommand*<br/>
in Eine GUID, die die Syntax und die allgemeinen Regeln angibt, die der Anbieter zum Übernehmen des Befehls Texts verwenden soll. Weitere Informationen finden Sie unter [ICommandText:: getcommandtext](/previous-versions/windows/desktop/ms709825(v=vs.85)) und [ICommandText:: SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)) in der *OLE DB-Programmier Referenz* .

*bbind*<br/>
in Gibt an, ob der Befehl nach der Ausführung automatisch gebunden werden soll. Der Standardwert ist **`true`** , wodurch der Befehl automatisch gebunden wird. Wenn Sie *bbind* auf festlegen, wird **`false`** die automatische Bindung des Befehls verhindert, sodass Sie die Bindung manuell vornehmen können. (Manuelle Bindung ist für OLAP-Benutzer besonders interessant.)

*ulpropsets*<br/>
in Die Anzahl von [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) -Strukturen, die im *ppropset* -Argument übergeben werden.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Die ersten drei Formen von `Open` nehmen eine Sitzung an, erstellen einen Befehl und führen den Befehl aus, wobei alle Parameter nach Bedarf gebunden werden.

Die erste Form von `Open` übernimmt eine Unicode-Befehls Zeichenfolge und hat keinen Standardwert.

Die zweite Form von `Open` erfordert eine ANSI-Befehls Zeichenfolge und keinen Standardwert (zur Abwärtskompatibilität mit vorhandenen ANSI-Anwendungen).

Die dritte Form von `Open` ermöglicht, dass die Befehls Zeichenfolge aufgrund des Typs **`int`** mit dem Standardwert NULL NULL ist. Sie wird zum Aufrufen von oder bereitgestellt, `Open(session, NULL);` `Open(session);` da NULL vom Typ ist **`int`** . Diese Version erfordert und bestätigt, dass der **`int`** Parameter NULL ist.

Verwenden Sie die vierte Form von `Open` , wenn Sie bereits einen Befehl erstellt haben und eine einzelne [Vorbereitung](#prepare) und mehrere Ausführungen ausführen möchten.

> [!NOTE]
> `Open` Ruft `Execute` auf, das wiederum aufruft `GetNextResult` .

## <a name="ccommandcreate"></a><a name="create"></a> CCommand:: Create

Ruft [CCommand:: kreatecommand](#createcommand) auf, um einen Befehl für die angegebene Sitzung zu erstellen, und ruft dann [ICommandText:: SetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) auf, um den Befehls Text anzugeben.

### <a name="syntax"></a>Syntax

```cpp
HRESULT CCommandBase::Create(const CSession& session,
   LPCWSTR wszCommand,
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();

HRESULT CCommandBase::Create(const CSession& session,
   LPCSTR szCommand,
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();
```

#### <a name="parameters"></a>Parameter

*Sitzung*<br/>
in Eine Sitzung, für die der Befehl erstellt werden soll.

*wszcommand*<br/>
in Ein Zeiger auf den Unicode-Text der Befehls Zeichenfolge.

*szCommand*<br/>
in Ein Zeiger auf den ANSI-Text der Befehls Zeichenfolge.

*guidcommand*<br/>
in Eine GUID, die die Syntax und die allgemeinen Regeln angibt, die der Anbieter zum Übernehmen des Befehls Texts verwenden soll. Eine Beschreibung der Dialekte finden Sie unter [ICommandText:: getcommandtext](/previous-versions/windows/desktop/ms709825(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Die erste Form von `Create` nimmt eine Unicode-Befehls Zeichenfolge an. Die zweite Form von `Create` erfordert eine ANSI-Befehls Zeichenfolge (aus Gründen der Abwärtskompatibilität mit vorhandenen ANSI-Anwendungen).

## <a name="ccommandcreatecommand"></a><a name="createcommand"></a> CCommand:: kreatecommand

Erstellt einen neuen Befehl.

### <a name="syntax"></a>Syntax

```cpp
HRESULT CCommandBase::CreateCommand(const CSession& session) throw ();
```

#### <a name="parameters"></a>Parameter

*Sitzung*<br/>
in Ein- `CSession` Objekt, das dem neuen Befehl zugeordnet werden soll.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Diese Methode erstellt mit dem angegebenen Sitzungs Objekt einen Befehl.

## <a name="ccommandgetparameterinfo"></a><a name="getparameterinfo"></a> CCommand:: GetParameterInfo

Ruft eine Liste mit den Parametern des Befehls, deren Namen und deren Typen ab.

### <a name="syntax"></a>Syntax

```cpp
HRESULT CCommandBase::GetParameterInfo(DB_UPARAMS* pParams,
   DBPARAMINFO** ppParamInfo,
   OLECHAR** ppNamesBuffer) throw ();
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [ICommandWithParameters:: GetParameterInfo](/previous-versions/windows/desktop/ms714917(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

## <a name="ccommandprepare"></a><a name="prepare"></a> CCommand::P repare

Überprüft und optimiert den aktuellen Befehl.

### <a name="syntax"></a>Syntax

```cpp
HRESULT CCommandBase::Prepare(ULONG cExpectedRuns = 0) throw();
```

#### <a name="parameters"></a>Parameter

*cexpectedruns*<br/>
in Gibt an, wie oft der Befehl ausgeführt werden soll.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Diese Methode umschließt die OLE DB [ICommandPrepare::P repare](/previous-versions/windows/desktop/ms718370(v=vs.85))-Methode.

## <a name="ccommandreleasecommand"></a><a name="releasecommand"></a> CCommand:: ReleaseCommand

Gibt den Parameter Accessor frei und gibt dann den Befehl selbst frei.

### <a name="syntax"></a>Syntax

```cpp
void CCommandBase::ReleaseCommand() throw();
```

### <a name="remarks"></a>Bemerkungen

`ReleaseCommand` wird in Verbindung mit verwendet `Close` . Weitere Informationen zur Verwendung finden Sie unter [Close](#close) .

## <a name="ccommandsetparameterinfo"></a><a name="setparameterinfo"></a> CCommand:: SetParameterInfo

Gibt den systemeigenen Typ der einzelnen Befehlsparameter an.

### <a name="syntax"></a>Syntax

```cpp
HRESULT CCommandBase::SetParameterInfo(DB_UPARAMS ulParams,
   const DBORDINAL* pOrdinals,
   const DBPARAMBINDINFO* pParamInfo) throw();
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [ICommandWithParameters:: SetParameterInfo](/previous-versions/windows/desktop/ms725393(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

## <a name="ccommandunprepare"></a><a name="unprepare"></a> CCommand:: Unprepare

Verwirft den aktuellen Befehls Ausführungsplan.

### <a name="syntax"></a>Syntax

```cpp
HRESULT CCommandBase::Unprepare() throw();
```

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Diese Methode umschließt die OLE DB [ICommandPrepare:: Unprepare](/previous-versions/windows/desktop/ms719635(v=vs.85))-Methode.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz zu OLE DB Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)
