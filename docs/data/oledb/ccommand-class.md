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
ms.openlocfilehash: 52c7e2ce5acdd2df33e2a6422535a337f0a43aec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368632"
---
# <a name="ccommand-class"></a>CCommand-Klasse

Stellt Methoden zum Festlegen und Ausführen eines Befehls bereit.

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
Der Typ der Accessorklasse `CDynamicParameterAccessor` `CDynamicStringAccessor`(z. B. , oder `CEnumeratorAccessor`), den der Befehl verwenden soll. Der Standardwert ist `CNoAccessor`, was angibt, dass die Klasse keine Parameter oder Ausgabespalten unterstützt.

*TRowset*<br/>
Der Typ der Rowset-Klasse (z. B. `CArrayRowset` oder `CNoRowset`), die der Befehl verwenden soll. Der Standardwert lautet `CRowset`.

*TMultiple*<br/>
Um einen OLE DB-Befehl zu verwenden, der mehrere Ergebnisse zurückgeben kann, geben Sie [CMultipleResults](../../data/oledb/cmultipleresults-class.md)an. Andernfalls verwenden Sie [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md). Weitere Informationen finden Sie unter [IMultipleResults](/previous-versions/windows/desktop/ms721289(v=vs.85)).

## <a name="requirements"></a>Anforderungen

**Header:** atldbcli.h

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[Schließen](#close)|Schließt den aktuellen Befehl.|
|[GetNextResult](#getnextresult)|Ruft das nächste Ergebnis ab, wenn mehrere Resultsets verwendet werden.|
|[Öffnen](#open)|Führt den Befehl aus und bindet ihn optional.|

### <a name="inherited-methods"></a>Geerbte Methoden

|||
|-|-|
|[Erstellen](#create)|Erstellt einen neuen Befehl für die angegebene Sitzung und legt dann den Befehlstext fest.|
|[CreateCommand](#createcommand)|Erstellt einen neuen Befehl.|
|[GetParameterInfo](#getparameterinfo)|Ruft eine Liste der Parameter des Befehls, ihrer Namen und ihrer Typen ab.|
|[Vorbereiten](#prepare)|Überprüft und optimiert den aktuellen Befehl.|
|[ReleaseCommand](#releasecommand)|Gibt den Parameteraccessor bei Bedarf frei und gibt dann den Befehl frei.|
|[Setparameterinfo](#setparameterinfo)|Gibt den systemeigenen Typ der einzelnen Befehlsparameter an.|
|[Unprepare](#unprepare)|Verwirft den aktuellen Befehlsausführungsplan.|

## <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Klasse, wenn Sie einen parameterbasierten Vorgang ausführen oder einen Befehl ausführen müssen. Wenn Sie lediglich ein einfaches Rowset öffnen müssen, verwenden Sie stattdessen [CTable.](../../data/oledb/ctable-class.md)

Die verwendete Accessorklasse bestimmt die Methode der Bindung von Parametern und Daten.

Beachten Sie, dass Sie gespeicherte Prozeduren nicht mit dem OLE DB-Anbieter für Jet verwenden können, da dieser Anbieter keine gespeicherten Prozeduren unterstützt (nur Konstanten sind in Abfragezeichenfolgen zulässig).

## <a name="ccommandclose"></a><a name="close"></a>CCommand::Schließen

Gibt das dem Befehl zugeordnete Accessor-Rowset frei.

### <a name="syntax"></a>Syntax

```cpp
void Close();
```

### <a name="remarks"></a>Bemerkungen

Ein Befehl verwendet ein Rowset, einen Resultset-Accessor und (optional) einen Parameteraccessor (im Gegensatz zu Tabellen, die keine Parameter unterstützen und keinen Parameteraccessor benötigen).

Wenn Sie einen Befehl ausführen, `Close` sollten Sie sowohl releaseCommand als auch [ReleaseCommand](../../data/oledb/ccommand-releasecommand.md) nach dem Befehl aufrufen.

Wenn Sie denselben Befehl wiederholt ausführen möchten, sollten Sie `Close` jeden `Execute`Ergebnissatzaccessor freigeben, indem Sie vor dem Aufruf aufrufen. Am Ende der Serie sollten Sie den Parameteraccessor freigeben, indem Sie aufrufen. `ReleaseCommand` Ein weiteres häufiges Szenario ist das Aufrufen einer gespeicherten Prozedur mit Ausgabeparametern. Auf vielen Anbietern (z. B. dem OLE DB-Anbieter für SQL Server) sind die Ausgabeparameterwerte erst dann zugänglich, wenn Sie den Ergebnissatzaccessor schließen. Aufruf `Close` zum Schließen des zurückgegebenen Rowset- und Resultset-Accessors, jedoch nicht des Parameteraccessors, sodass Sie die Ausgabeparameterwerte abrufen können.

### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie Sie `Close` und `ReleaseCommand` aufrufen, wenn Sie wiederholt den gleichen Befehl ausführen.

[!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]

## <a name="ccommandgetnextresult"></a><a name="getnextresult"></a>CCommand::GetNextResult

Ruft das nächste Resultset ab, wenn eines verfügbar ist.

### <a name="syntax"></a>Syntax

```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected,
   bool bBind = true) throw();
```

#### <a name="parameters"></a>Parameter

*pulRowsAffected*<br/>
[Ein/Aus] Ein Zeiger auf den Speicher, in dem die Anzahl der Zeilen zurückgegeben wird, die von einem Befehl betroffen sind.

*bBind*<br/>
[in] Gibt an, ob der Befehl nach der Ausführung automatisch gebunden werden soll. Der Standardwert ist **true**, wodurch der Befehl automatisch gebunden wird. Durch festlegen *von bBind* auf **false** wird die automatische Bindung des Befehls verhindert, sodass Sie manuell binden können. (Die manuelle Bindung ist für OLAP-Benutzer von besonderem Interesse.)

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT.

### <a name="remarks"></a>Bemerkungen

Wenn zuvor ein Resultset abgerufen wurde, gibt diese Funktion das vorherige Resultset frei und löst die Bindung der Spalten. Wenn *bBind* **true**ist, bindet es die neuen Spalten.

Sie sollten diese Funktion nur aufrufen, wenn `CCommand` Sie mehrere Ergebnisse angegeben haben, indem Sie den Vorlagenparameter *TMultiple*=`CMultipleResults`festlegen.

## <a name="ccommandopen"></a><a name="open"></a>CCommand::Öffnen

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

*session*<br/>
[in] Die Sitzung, in der der Befehl ausgeführt werden soll.

*wszCommand*<br/>
[in] Der auszuführende Befehl, der als Unicode-Zeichenfolge übergeben wird. Kann NULL sein, wenn `CAccessor`, in diesem Fall wird der Befehl aus dem Wert abgerufen, der an das [DEFINE_COMMAND-Makro](../../data/oledb/define-command.md) übergeben wird. Weitere Informationen finden Sie unter [ICommand::Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) in the *OLE DB Programmer es Reference.*

*szCommand*<br/>
[in] Genauso wie *wszCommand,* außer dass dieser Parameter eine ANSI-Befehlszeichenfolge verwendet. Die vierte Form dieser Methode kann einen NULL-Wert annehmen. Weitere Informationen finden Sie unter "Bemerkungen" weiter unten in diesem Thema.

*pPropSet*<br/>
[in] Ein Zeiger auf ein Array von [DBPROPSET-Strukturen,](/previous-versions/windows/desktop/ms714367(v=vs.85)) die eigenschaften und werte enthalten, die festgelegt werden sollen. Weitere Informationen finden Sie unter [Eigenschaftensätze und Eigenschaftengruppen](/previous-versions/windows/desktop/ms713696(v=vs.85)) in der *Ole DB-Programmierreferenz* im Windows SDK.

*pRowsAffected*<br/>
[Ein/Aus] Ein Zeiger auf den Speicher, in dem die Anzahl der Zeilen zurückgegeben wird, die von einem Befehl betroffen sind. Wenn * \*pRowsAffected* NULL ist, wird keine Zeilenanzahl zurückgegeben. Andernfalls `Open` setzt * \*pRowsAffected* gemäß den folgenden Bedingungen:

|Wenn|Then|
|--------|----------|
|Das `cParamSets` Element `pParams` von ist größer als 1|pRowsAffected stellt die Gesamtzahl der Zeilen dar, die von allen in der Ausführung angegebenen Parametersätzen betroffen sind. * \**|
|Die Anzahl der betroffenen Zeilen ist nicht verfügbar.|pRowsAffected ist auf -1 gesetzt. * \**|
|Der Befehl aktualisiert, löscht oder fügt keine Zeilen ein.|pRowsAffected ist nicht definiert. * \**|

*guidCommand*<br/>
[in] Eine GUID, die die Syntax und allgemeine Regeln angibt, die der Anbieter beim Analysieren des Befehlstextes verwenden soll. Weitere Informationen finden Sie unter [ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) und [ICommandText::SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)) in der *Ole DB Programmer-Referenz.*

*bBind*<br/>
[in] Gibt an, ob der Befehl nach der Ausführung automatisch gebunden werden soll. Der Standardwert ist **true**, wodurch der Befehl automatisch gebunden wird. Durch festlegen *von bBind* auf **false** wird die automatische Bindung des Befehls verhindert, sodass Sie manuell binden können. (Die manuelle Bindung ist für OLAP-Benutzer von besonderem Interesse.)

*ulPropSets*<br/>
[in] Die Anzahl der [DBPROPSET-Strukturen,](/previous-versions/windows/desktop/ms714367(v=vs.85)) die im *pPropSet-Argument* übergeben wurden.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT.

### <a name="remarks"></a>Bemerkungen

Die ersten drei `Open` Formen der Sitzung nehmen, einen Befehl erstellen und den Befehl ausführen, und binden alle Parameter nach Bedarf.

Die erste `Open` Form von nimmt eine Unicode-Befehlszeichenfolge an und hat keinen Standardwert.

Die zweite `Open` Form von nimmt eine ANSI-Befehlszeichenfolge und keinen Standardwert an (für Abwärtskompatibilität mit vorhandenen ANSI-Anwendungen bereitgestellt).

Die dritte `Open` Form von lässt die Befehlszeichenfolge NULL sein, da der Typ **int** den Standardwert NULL hat. Sie wird zum `Open(session, NULL);` `Open(session);` Aufrufen bereitgestellt oder weil NULL vom Typ **int**ist. Diese Version erfordert und behauptet, dass der **int-Parameter** NULL ist.

Verwenden Sie die `Open` vierte Form, wenn Sie bereits einen Befehl erstellt haben und eine einzelne [Vorbereitung](../../data/oledb/ccommand-prepare.md) und mehrere Ausführungen ausführen möchten.

> [!NOTE]
> `Open`Aufrufe `Execute`, die `GetNextResult`wiederum ruft .

## <a name="ccommandcreate"></a><a name="create"></a>CCommand::Erstellen

Ruft [CCommand::CreateCommand](../../data/oledb/ccommand-createcommand.md) auf, um einen Befehl für die angegebene Sitzung zu erstellen, und ruft dann [ICommandText::SetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) auf, um den Befehlstext anzugeben.

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

*session*<br/>
[in] Eine Sitzung, in der der Befehl erstellt werden soll.

*wszCommand*<br/>
[in] Ein Zeiger auf den Unicode-Text der Befehlszeichenfolge.

*szCommand*<br/>
[in] Ein Zeiger auf den ANSI-Text der Befehlszeichenfolge.

*guidCommand*<br/>
[in] Eine GUID, die die Syntax und allgemeine Regeln angibt, die der Anbieter beim Analysieren des Befehlstextes verwenden soll. Eine Beschreibung von Dialekten finden Sie unter [ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) in der *Ole DB Programmer-Referenz*.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT.

### <a name="remarks"></a>Bemerkungen

Die erste `Create` Form von nimmt eine Unicode-Befehlszeichenfolge an. Die zweite `Create` Form von nimmt eine ANSI-Befehlszeichenfolge an (für Die Abwärtskompatibilität mit vorhandenen ANSI-Anwendungen bereitgestellt).

## <a name="ccommandcreatecommand"></a><a name="createcommand"></a>CCommand::CreateCommand

Erstellt einen neuen Befehl.

### <a name="syntax"></a>Syntax

```cpp
HRESULT CCommandBase::CreateCommand(const CSession& session) throw ();
```

#### <a name="parameters"></a>Parameter

*session*<br/>
[in] Ein `CSession` Objekt, das dem neuen Befehl zugeordnet werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT.

### <a name="remarks"></a>Bemerkungen

Diese Methode erstellt einen Befehl mit dem angegebenen Sitzungsobjekt.

## <a name="ccommandgetparameterinfo"></a><a name="getparameterinfo"></a>CCommand::GetParameterInfo

Ruft eine Liste der Parameter des Befehls, ihrer Namen und ihrer Typen ab.

### <a name="syntax"></a>Syntax

```cpp
HRESULT CCommandBase::GetParameterInfo(DB_UPARAMS* pParams,
   DBPARAMINFO** ppParamInfo,
   OLECHAR** ppNamesBuffer) throw ();
```

#### <a name="parameters"></a>Parameter

Siehe [ICommandWithParameters::GetParameterInfo](/previous-versions/windows/desktop/ms714917(v=vs.85)) in der *Referenz des OLE DB-Programmierers*.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT.

## <a name="ccommandprepare"></a><a name="prepare"></a>CCommand::Prepare

Überprüft und optimiert den aktuellen Befehl.

### <a name="syntax"></a>Syntax

```cpp
HRESULT CCommandBase::Prepare(ULONG cExpectedRuns = 0) throw();
```

#### <a name="parameters"></a>Parameter

*cExpectedRuns*<br/>
[in] Die Häufigkeit, mit der Sie den Befehl ausführen möchten.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT.

### <a name="remarks"></a>Bemerkungen

Diese Methode umschließt die OLE DB-Methode [ICommandPrepare::Prepare](/previous-versions/windows/desktop/ms718370(v=vs.85)).

## <a name="ccommandreleasecommand"></a><a name="releasecommand"></a>CCommand::ReleaseCommand

Gibt den Parameteraccessor frei und gibt dann den Befehl selbst frei.

### <a name="syntax"></a>Syntax

```cpp
void CCommandBase::ReleaseCommand() throw();
```

### <a name="remarks"></a>Bemerkungen

`ReleaseCommand`wird in Verbindung `Close`mit verwendet. Siehe [Schließen](../../data/oledb/ccommand-close.md) für Nutzungsdetails.

## <a name="ccommandsetparameterinfo"></a><a name="setparameterinfo"></a>CCommand::SetParameterInfo

Gibt den systemeigenen Typ der einzelnen Befehlsparameter an.

### <a name="syntax"></a>Syntax

```cpp
HRESULT CCommandBase::SetParameterInfo(DB_UPARAMS ulParams,
   const DBORDINAL* pOrdinals,
   const DBPARAMBINDINFO* pParamInfo) throw();
```

#### <a name="parameters"></a>Parameter

Siehe [ICommandWithParameters::SetParameterInfo](/previous-versions/windows/desktop/ms725393(v=vs.85)) in der *Referenz des OLE DB-Programmierers*.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT.

## <a name="ccommandunprepare"></a><a name="unprepare"></a>CCommand::Unprepare

Verwirft den aktuellen Befehlsausführungsplan.

### <a name="syntax"></a>Syntax

```cpp
HRESULT CCommandBase::Unprepare() throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT.

### <a name="remarks"></a>Bemerkungen

Diese Methode umschließt die OLE DB-Methode [ICommandPrepare::Unprepare](/previous-versions/windows/desktop/ms719635(v=vs.85)).

## <a name="see-also"></a>Siehe auch

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Ole DB Consumer Templates Referenz](../../data/oledb/ole-db-consumer-templates-reference.md)
