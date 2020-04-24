---
title: CDatabase-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDatabase
- AFXDB/CDatabase
- AFXDB/CDatabase::CDatabase
- AFXDB/CDatabase::BeginTrans
- AFXDB/CDatabase::BindParameters
- AFXDB/CDatabase::Cancel
- AFXDB/CDatabase::CanTransact
- AFXDB/CDatabase::CanUpdate
- AFXDB/CDatabase::Close
- AFXDB/CDatabase::CommitTrans
- AFXDB/CDatabase::ExecuteSQL
- AFXDB/CDatabase::GetBookmarkPersistence
- AFXDB/CDatabase::GetConnect
- AFXDB/CDatabase::GetCursorCommitBehavior
- AFXDB/CDatabase::GetCursorRollbackBehavior
- AFXDB/CDatabase::GetDatabaseName
- AFXDB/CDatabase::IsOpen
- AFXDB/CDatabase::OnSetOptions
- AFXDB/CDatabase::Open
- AFXDB/CDatabase::OpenEx
- AFXDB/CDatabase::Rollback
- AFXDB/CDatabase::SetLoginTimeout
- AFXDB/CDatabase::SetQueryTimeout
- AFXDB/CDatabase::m_hdbc
helpviewer_keywords:
- CDatabase [MFC], CDatabase
- CDatabase [MFC], BeginTrans
- CDatabase [MFC], BindParameters
- CDatabase [MFC], Cancel
- CDatabase [MFC], CanTransact
- CDatabase [MFC], CanUpdate
- CDatabase [MFC], Close
- CDatabase [MFC], CommitTrans
- CDatabase [MFC], ExecuteSQL
- CDatabase [MFC], GetBookmarkPersistence
- CDatabase [MFC], GetConnect
- CDatabase [MFC], GetCursorCommitBehavior
- CDatabase [MFC], GetCursorRollbackBehavior
- CDatabase [MFC], GetDatabaseName
- CDatabase [MFC], IsOpen
- CDatabase [MFC], OnSetOptions
- CDatabase [MFC], Open
- CDatabase [MFC], OpenEx
- CDatabase [MFC], Rollback
- CDatabase [MFC], SetLoginTimeout
- CDatabase [MFC], SetQueryTimeout
- CDatabase [MFC], m_hdbc
ms.assetid: bd0de70a-e3c3-4441-bcaa-bbf434426ca8
ms.openlocfilehash: bc920307e09179dc214710a3b6b19ff27a82749d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754642"
---
# <a name="cdatabase-class"></a>CDatabase-Klasse

Stellt eine Verbindung mit einer Datenquelle dar, über welche die Datenquelle bearbeitet werden kann.

## <a name="syntax"></a>Syntax

```
class CDatabase : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDatabase::CDatabase](#cdatabase)|Erstellt ein `CDatabase`-Objekt. Sie müssen das Objekt `OpenEx` initialisieren, indem Sie oder `Open`aufrufen.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDatabase::BeginTrans](#begintrans)|Startet eine "Transaktion" – eine Reihe `AddNew`von `Edit` `Delete`reversiblen Aufrufen der , , und `Update` Memberfunktionen der Klasse `CRecordset` – in der verbundenen Datenquelle. Die Datenquelle muss Transaktionen `BeginTrans` unterstützen, um Auswirkungen zu erzielen.|
|[CDatabase::BindParameters](#bindparameters)|Ermöglicht das Binden von `CDatabase::ExecuteSQL`Parametern vor dem Aufruf von .|
|[CDatabase::Abbrechen](#cancel)|Bricht einen asynchronen Vorgang oder einen Prozess von einem zweiten Thread ab.|
|[CDatabase::CanTransact](#cantransact)|Gibt einen Wert ungleich Null zurück, wenn die Datenquelle Transaktionen unterstützt.|
|[CDatabase::CanUpdate](#canupdate)|Gibt einen Wert `CDatabase` ungleich Null zurück, wenn das Objekt aufrüstbar (nicht schreibgeschützt) ist.|
|[CDatabase::Schließen](#close)|Schließt die Datenquellenverbindung.|
|[CDatabase::CommitTrans](#committrans)|Schließt eine Transaktion `BeginTrans`ab, die mit begonnen wurde. Befehle in der Transaktion, die die Datenquelle ändern, werden ausgeführt.|
|[CDatabase::ExecuteSQL](#executesql)|Führt eine SQL-Anweisung aus. Es werden keine Datensätze zurückgegeben.|
|[CDatabase::GetBookmarkPersistenz](#getbookmarkpersistence)|Identifiziert die Vorgänge, durch die Lesezeichen für Recordset-Objekte beibehalten werden.|
|[CDatabase::GetConnect](#getconnect)|Gibt die ODBC-Verbindungszeichenfolge `CDatabase` zurück, die zum Verbinden des Objekts mit einer Datenquelle verwendet wird.|
|[CDatabase::GetCursorCommitBehavior](#getcursorcommitbehavior)|Identifiziert den Effekt des Commits einer Transaktion auf ein offenes Recordset-Objekt.|
|[CDatabase::GetCursorRollbackBehavior](#getcursorrollbackbehavior)|Identifiziert den Effekt eines Rollbacks einer Transaktion auf ein geöffnetes Recordsetobjekt.|
|[CDatabase::GetDatabaseName](#getdatabasename)|Gibt den Namen der aktuell verwendeten Datenbank zurück.|
|[CDatabase::IsOpen](#isopen)|Gibt einen Wert `CDatabase` ungleich Null zurück, wenn das Objekt derzeit mit einer Datenquelle verbunden ist.|
|[CDatabase::OnSetOptions](#onsetoptions)|Wird vom Framework aufgerufen, um Standardverbindungsoptionen festzulegen. Die Standardimplementierung legt den Abfragetimeoutwert fest. Sie können diese Optionen im `SetQueryTimeout`Voraus festlegen, indem Sie anrufen.|
|[CDatabase::Öffnen](#open)|Stellt eine Verbindung zu einer Datenquelle her (über einen ODBC-Treiber).|
|[CDatabase::OpenEx](#openex)|Stellt eine Verbindung zu einer Datenquelle her (über einen ODBC-Treiber).|
|[CDatabase::Rollback](#rollback)|Kehrt Änderungen um, die während der aktuellen Transaktion vorgenommen wurden. Die Datenquelle kehrt unverändert in ihren vorherigen `BeginTrans` Zustand zurück, wie beim Aufruf definiert.|
|[CDatabase::SetLoginTimeout](#setlogintimeout)|Legt die Anzahl der Sekunden fest, nach denen bei einem Datenquellenverbindungsversuch ein Timeout ausgeführt wird.|
|[CDatabase::SetQueryTimeout](#setquerytimeout)|Legt die Anzahl der Sekunden fest, nach denen Datenbankabfragevorgänge ein Timeout aufweisen. Wirkt sich auf `Open` `AddNew`alle `Edit`nachfolgenden Recordset , , und `Delete` Aufrufe aus.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDatabase::m_hdbc](#m_hdbc)|ODBC-Verbindungshandle (Open Database Connectivity) zu einer Datenquelle. Typ *HDBC*.|

## <a name="remarks"></a>Bemerkungen

Eine Datenquelle ist eine bestimmte Instanz von Daten, die von einem Datenbankverwaltungssystem (DBMS) gehostet werden. Beispiele hierfür sind Microsoft SQL Server, Microsoft Access, Borland dBASE und xBASE. Sie können ein `CDatabase` oder mehrere Objekte gleichzeitig in Ihrer Anwendung aktiv haben.

> [!NOTE]
> Wenn Sie mit den DAO-Klassen (Data Access Objects) und nicht mit den ODBC-Klassen (Open Database Connectivity) arbeiten, verwenden Sie stattdessen die Klasse [CDaoDatabase.](../../mfc/reference/cdaodatabase-class.md) Weitere Informationen finden Sie im Artikel [Übersicht: Datenbankprogrammierung](../../data/data-access-programming-mfc-atl.md).

Um `CDatabase`zu verwenden, erstellen Sie ein `CDatabase` Objekt und rufen seine `OpenEx` Memberfunktion auf. Dadurch wird eine Verbindung geöffnet. Wenn Sie `CRecordset` dann Objekte für den Betrieb auf der verbundenen Datenquelle erstellen, `CDatabase` übergeben Sie dem Recordset-Konstruktor einen Zeiger an das Objekt. Wenn Sie die Verbindung verwenden, rufen Sie die `Close` Memberfunktion auf und zerstören Sie das `CDatabase` Objekt. `Close`schließt alle Recordsets, die Sie zuvor noch nicht geschlossen haben.

Weitere Informationen `CDatabase`zu finden Sie in den Artikeln [Datenquelle (ODBC)](../../data/odbc/data-source-odbc.md) und [Übersicht: Datenbankprogrammierung](../../data/data-access-programming-mfc-atl.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CDatabase`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxdb.h

## <a name="cdatabasebegintrans"></a><a name="begintrans"></a>CDatabase::BeginTrans

Rufen Sie diese Memberfunktion auf, um eine Transaktion mit der verbundenen Datenquelle zu beginnen.

```
BOOL BeginTrans();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Aufruf erfolgreich war und Änderungen nur manuell festgeschrieben werden. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Eine Transaktion besteht aus einem `AddNew`oder `Edit` `Delete`mehreren `Update` Aufrufen der `CRecordset` , , und Memberfunktionen eines Objekts. Vor Dem Start `CDatabase` einer Transaktion muss das Objekt bereits durch `OpenEx` `Open` Aufrufen der oder Memberfunktion mit der Datenquelle verbunden worden sein. Um die Transaktion zu beenden, rufen Sie [CommitTrans](#committrans) auf, um alle Änderungen an der Datenquelle zu akzeptieren (und diese auszuführen) oder [rollback](#rollback) aufzurufen, um die gesamte Transaktion abzubrechen. Rufen `BeginTrans` Sie an, nachdem Sie alle Recordsets geöffnet haben, die an der Transaktion beteiligt sind, und so nah wie möglich an den tatsächlichen Aktualisierungsvorgängen.

> [!CAUTION]
> Je nach ODBC-Treiber kann das `BeginTrans` Öffnen eines Recordsets vor dem Aufruf Probleme beim Aufruf `Rollback`verursachen. Sie sollten den spezifischen Treiber überprüfen, den Sie verwenden. Wenn Sie beispielsweise den Microsoft Access-Treiber verwenden, der im Microsoft ODBC Desktop Driver Pack 3.0 enthalten ist, müssen Sie die Anforderung des Jet-Datenbankmoduls berücksichtigen, dass Sie keine Transaktion für eine Datenbank mit einem geöffneten Cursor beginnen sollten. In den MFC-Datenbankklassen bedeutet ein `CRecordset` geöffneter Cursor ein geöffnetes Objekt. Weitere Informationen finden Sie unter [Technische Anmerkung 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md).

`BeginTrans`kann auch Datensätze auf dem Server sperren, abhängig von der angeforderten Parallelität und den Funktionen der Datenquelle. Informationen zum Sperren von Daten finden Sie im Artikel [Recordset: Locking Records (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).

Benutzerdefinierte Transaktionen werden im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md)erläutert.

`BeginTrans`legt den Zustand fest, in den die Reihenfolge der Transaktionen zurückgesetzt (umgekehrt) werden kann. Um einen neuen Status für Rollbacks einzurichten, `BeginTrans` übertragen Sie jede aktuelle Transaktion, und rufen Sie dann erneut auf.

> [!CAUTION]
> Rufen `BeginTrans` Sie `CommitTrans` erneut `Rollback` auf, ohne aufzurufen, oder ist ein Fehler.

Rufen Sie die [CanTransact-Memberfunktion](#cantransact) auf, um zu ermitteln, ob Ihr Treiber Transaktionen für eine bestimmte Datenbank unterstützt. Sie sollten auch [GetCursorCommitBehavior](#getcursorcommitbehavior) und [GetCursorRollbackBehavior](#getcursorrollbackbehavior) aufrufen, um die Unterstützung für die Cursorerhaltung zu bestimmen.

Weitere Informationen zu Transaktionen finden Sie im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Beispiel

  Siehe den Artikel [Transaktion: Ausführen einer Transaktion in einem Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="cdatabasebindparameters"></a><a name="bindparameters"></a>CDatabase::BindParameters

Überschreiben `BindParameters` Sie, wenn Sie Parameter binden müssen, bevor Sie [CDatabase::ExecuteSQL](#executesql)aufrufen.

```
virtual void BindParameters(HSTMT hstmt);
```

### <a name="parameters"></a>Parameter

*hstmt*<br/>
Das ODBC-Anweisungshandle, für das Sie Parameter binden möchten.

### <a name="remarks"></a>Bemerkungen

Dieser Ansatz ist nützlich, wenn Sie das Resultset aus einer gespeicherten Prozedur nicht benötigen.

Rufen Sie in `SQLBindParameters` Ihrer Außerkraftsetzung und die zugehörigen ODBC-Funktionen an, um die Parameter zu binden. MFC ruft Ihre Außerkraftsetzung `ExecuteSQL`vor Ihrem Aufruf an auf. Sie müssen nicht `SQLPrepare`anrufen; `ExecuteSQL` ruft `SQLExecDirect` und zerstört die *hstmt*, die nur einmal verwendet wird.

## <a name="cdatabasecancel"></a><a name="cancel"></a>CDatabase::Abbrechen

Rufen Sie diese Memberfunktion auf, um anzufordern, dass die Datenquelle entweder einen asynchronen Vorgang oder einen Prozess von einem zweiten Thread abbricht.

```cpp
void Cancel();
```

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass die MFC-ODBC-Klassen keine asynchrone Verarbeitung mehr verwenden. Um einen asynchronen Vorgang auszuführen, müssen Sie direkt die ODBC-API-Funktion [SQLSetConnectOption](/sql/odbc/reference/syntax/sqlsetconnectoption-function)aufrufen. Weitere Informationen finden Sie unter [Asynchrone Ausführung](/sql/odbc/reference/develop-app/asynchronous-execution).

## <a name="cdatabasecantransact"></a><a name="cantransact"></a>CDatabase::CanTransact

Rufen Sie diese Memberfunktion auf, um zu bestimmen, ob die Datenbank Transaktionen zulässt.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich `CDatabase` Null, wenn Recordsets, die dieses Objekt verwenden, Transaktionen zulassen; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Informationen zu Transaktionen finden Sie im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="cdatabasecanupdate"></a><a name="canupdate"></a>CDatabase::CanUpdate

Rufen Sie diese Memberfunktion `CDatabase` auf, um zu bestimmen, ob das Objekt Aktualisierungen zulässt.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert `CDatabase` ungleich Null, wenn das Objekt Aktualisierungen zulässt; Andernfalls 0, was entweder angibt, dass Sie TRUE `CDatabase` in *bReadOnly* übergeben haben, wenn Sie das Objekt geöffnet haben, oder dass die Datenquelle selbst schreibgeschützt ist. Die Datenquelle ist schreibgeschützt, wenn ein Aufruf `SQLGetInfo` der ODBC-API-Funktion für SQL_DATASOURCE_READ_ONLY "y" zurückgibt.

### <a name="remarks"></a>Bemerkungen

Nicht alle Treiber unterstützen Updates.

## <a name="cdatabasecdatabase"></a><a name="cdatabase"></a>CDatabase::CDatabase

Erstellt ein `CDatabase`-Objekt.

```
CDatabase();
```

### <a name="remarks"></a>Bemerkungen

Nach dem Erstellen des Objekts müssen Sie seine `OpenEx` oder `Open` Memberfunktion aufrufen, um eine Verbindung zu einer angegebenen Datenquelle herzustellen.

Möglicherweise ist es praktisch, `CDatabase` das Objekt in Ihre Dokumentklasse einzubetten.

### <a name="example"></a>Beispiel

Dieses Beispiel veranschaulicht `CDatabase` die `CDocument`Verwendung in einer -derived-Klasse.

[!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]

[!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]

## <a name="cdatabaseclose"></a><a name="close"></a>CDatabase::Schließen

Rufen Sie diese Memberfunktion auf, wenn Sie die Verbindung zu einer Datenquelle trennen möchten.

```
virtual void Close();
```

### <a name="remarks"></a>Bemerkungen

Sie müssen alle dem `CDatabase` Objekt zugeordneten Recordsets schließen, bevor Sie diese Memberfunktion aufrufen. Da `Close` das `CDatabase` Objekt nicht zerstört wird, können Sie das Objekt wiederverwenden, indem Sie eine neue Verbindung zu derselben Datenquelle oder einer anderen Datenquelle öffnen.

Alle `AddNew` ausstehenden oder `Edit` Anweisungen von Recordsets, die die Datenbank verwenden, werden abgebrochen, und alle ausstehenden Transaktionen werden zurückgesetzt. Alle vom `CDatabase` Objekt abhängigen Recordsets werden in einem nicht definierten Zustand belassen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]

## <a name="cdatabasecommittrans"></a><a name="committrans"></a>CDatabase::CommitTrans

Rufen Sie diese Memberfunktion auf, wenn Sie Transaktionen abschließen.

```
BOOL CommitTrans();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Aktualisierungen erfolgreich festgeschrieben wurden; andernfalls 0. Wenn `CommitTrans` dieS fehlschlägt, ist der Status der Datenquelle nicht definiert. Sie müssen die Daten überprüfen, um ihren Status zu bestimmen.

### <a name="remarks"></a>Bemerkungen

Eine Transaktion besteht aus einer `AddNew`Reihe `Edit` `Delete`von `Update` Aufrufen der `CRecordset` , , , und Memberfunktionen eines Objekts, die mit einem Aufruf der [BeginTrans-Memberfunktion](#begintrans) begann. `CommitTrans`überträgt die Transaktion. Standardmäßig werden Aktualisierungen sofort festgeschrieben. Aufruf `BeginTrans` führt dazu, dass `CommitTrans` die Zusage von Aktualisierungen verzögert wird, bis aufgerufen wird.

Bis Sie `CommitTrans` eine Transaktion beenden, können Sie die [Rollback-Memberfunktion](#rollback) aufrufen, um die Transaktion abzubrechen und die Datenquelle im ursprünglichen Zustand zu belassen. Rufen Sie erneut an, `BeginTrans` um eine neue Transaktion zu beginnen.

Weitere Informationen zu Transaktionen finden Sie im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Beispiel

  Siehe den Artikel [Transaktion: Ausführen einer Transaktion in einem Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="cdatabaseexecutesql"></a><a name="executesql"></a>CDatabase::ExecuteSQL

Rufen Sie diese Memberfunktion auf, wenn Sie einen SQL-Befehl direkt ausführen müssen.

```cpp
void ExecuteSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Parameter

*Lpszsql*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die einen gültigen SQL-Befehl zum Ausführen enthält. Sie können einen [CString](../../atl-mfc-shared/reference/cstringt-class.md)übergeben.

### <a name="remarks"></a>Bemerkungen

Erstellen Sie den Befehl als null-terminierte Zeichenfolge. `ExecuteSQL`gibt keine Datensätze zurück. Wenn Sie mit Datensätzen arbeiten möchten, verwenden Sie stattdessen ein Recordset-Objekt.

Die meisten Befehle für eine Datenquelle werden über Recordset-Objekte ausgegeben, die Befehle zum Auswählen von Daten, Einfügen neuer Datensätze, Löschen von Datensätzen und Bearbeiten von Datensätzen unterstützen. Allerdings werden nicht alle ODBC-Funktionen direkt von den Datenbankklassen unterstützt, sodass `ExecuteSQL`Sie manchmal einen direkten SQL-Aufruf mit tätigen müssen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]

## <a name="cdatabasegetbookmarkpersistence"></a><a name="getbookmarkpersistence"></a>CDatabase::GetBookmarkPersistenz

Rufen Sie diese Member-Funktion auf, um die Beibehaltung von Lesezeichen auf einem recordset-Objekt nach bestimmten Vorgängen festzulegen.

```
DWORD GetBookmarkPersistence() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Bitmaske, die die Vorgänge identifiziert, mit denen Lesezeichen auf einem recordset-Objekt beibehalten werden. Einzelheiten finden Sie unter "Hinweise".

### <a name="remarks"></a>Bemerkungen

Wenn Sie beispielsweise `CRecordset::GetBookmark` und dann `CRecordset::Requery` aufrufen, ist das Lesezeichen von `GetBookmark` womöglich nicht mehr gültig. Sie sollten `GetBookmarkPersistence` vor `CRecordset::SetBookmark` aufrufen.

Die folgende Tabelle enthält die Bitmaskenwerten, die für den Rückgabewert von `GetBookmarkPersistence` kombiniert werden können.

|Bitmaskenwert|Lesezeichenbeibehaltung|
|-------------------|--------------------------|
|SQL_BP_CLOSE|Lesezeichen sind nach `Requery` einem Vorgang gültig.|
|SQL_BP_DELETE|Die Textmarke für eine Zeile `Delete` ist nach einem Vorgang in dieser Zeile gültig.|
|SQL_BP_DROP|Lesezeichen sind nach `Close` einem Vorgang gültig.|
|SQL_BP_SCROLL|Lesezeichen sind nach `Move` jedem Vorgang gültig. Damit wird mühelos identifiziert, ob Lesezeichen im Datensatz unterstützt werden, wie von `CRecordset::CanBookmark` zurückgegeben.|
|SQL_BP_TRANSACTION|Lesezeichen sind gültig, nachdem eine Transaktion übernommen oder zurückgesetzt wurde.|
|SQL_BP_UPDATE|Das Lesezeichen für eine Zeile `Update` ist nach einem Vorgang in dieser Zeile gültig.|
|SQL_BP_OTHER_HSTMT|Lesezeichen, die mit einem recordset-Objekt verbunden sind, sind in einem zweiten Datensatz gültig.|

Weitere Informationen zu diesem Rückgabewert finden Sie `SQLGetInfo` in der ODBC-API-Funktion im Windows SDK. Weitere Informationen zu Lesezeichen finden Sie im Artikel [Recordset: Lesezeichen und absolute Positionen (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

## <a name="cdatabasegetconnect"></a><a name="getconnect"></a>CDatabase::GetConnect

Rufen Sie diese Memberfunktion auf, um die während des Aufrufs von `OpenEx` oder `Open` verwendete Verbindungszeichenfolge abzurufen, die das `CDatabase`-Objekt mit einer Datenquelle verbunden hat.

```
const CString GetConnect() const;
```

### <a name="return-value"></a>Rückgabewert

Eine **const**[CString,](../../atl-mfc-shared/reference/cstringt-class.md) die `OpenEx` `Open` die Verbindungszeichenfolge enthält, wenn oder wurde sie aufgerufen; Andernfalls eine leere Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

Unter [CDatabase::Open](#open) finden Sie eine Beschreibung, wie die Verbindungszeichenfolge erstellt wird.

## <a name="cdatabasegetcursorcommitbehavior"></a><a name="getcursorcommitbehavior"></a>CDatabase::GetCursorCommitBehavior

Rufen Sie diese Memberfunktion auf, um zu bestimmen, wie sich ein [CommitTrans-Vorgang](#committrans) auf Cursor auf geöffnete Recordset-Objekte auswirkt.

```
int GetCursorCommitBehavior() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der die Auswirkungen von Transaktionen auf offene Recordset-Objekte angibt. Einzelheiten finden Sie unter "Hinweise".

### <a name="remarks"></a>Bemerkungen

In der folgenden Tabelle sind `GetCursorCommitBehavior` die möglichen Rückgabewerte für und der entsprechende Effekt auf das geöffnete Recordset aufgeführt.

|Rückgabewert|Auswirkungen auf CRecordset-Objekte|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Aufruf `CRecordset::Requery` unmittelbar nach dem Transaktionscommit.|
|SQL_CB_DELETE|Aufruf `CRecordset::Close` unmittelbar nach dem Transaktionscommit.|
|SQL_CB_PRESERVE|Fahren Sie `CRecordset` normal mit Operationen fort.|

Weitere Informationen zu diesem Rückgabewert finden Sie `SQLGetInfo` in der ODBC-API-Funktion im Windows SDK. Weitere Informationen zu Transaktionen finden Sie im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="cdatabasegetcursorrollbackbehavior"></a><a name="getcursorrollbackbehavior"></a>CDatabase::GetCursorRollbackBehavior

Rufen Sie diese Memberfunktion auf, um zu bestimmen, wie sich ein [Rollback-Vorgang](#rollback) auf Cursor auf geöffnete Recordset-Objekte auswirkt.

```
int GetCursorRollbackBehavior() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der die Auswirkungen von Transaktionen auf offene Recordset-Objekte angibt. Einzelheiten finden Sie unter "Hinweise".

### <a name="remarks"></a>Bemerkungen

In der folgenden Tabelle sind `GetCursorRollbackBehavior` die möglichen Rückgabewerte für und der entsprechende Effekt auf das geöffnete Recordset aufgeführt.

|Rückgabewert|Auswirkungen auf CRecordset-Objekte|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Rufen `CRecordset::Requery` Sie unmittelbar nach dem Transaktionsrollback auf.|
|SQL_CB_DELETE|Rufen `CRecordset::Close` Sie unmittelbar nach dem Transaktionsrollback auf.|
|SQL_CB_PRESERVE|Fahren Sie `CRecordset` normal mit Operationen fort.|

Weitere Informationen zu diesem Rückgabewert finden Sie `SQLGetInfo` in der ODBC-API-Funktion im Windows SDK. Weitere Informationen zu Transaktionen finden Sie im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="cdatabasegetdatabasename"></a><a name="getdatabasename"></a>CDatabase::GetDatabaseName

Rufen Sie diese Memberfunktion auf, um den Namen der aktuell verbundenen Datenbank abzurufen (vorausgesetzt, die Datenquelle definiert ein benanntes Objekt namens "Datenbank").

```
CString GetDatabaseName() const;
```

### <a name="return-value"></a>Rückgabewert

Ein [CString,](../../atl-mfc-shared/reference/cstringt-class.md) der den Datenbanknamen enthält, wenn er erfolgreich ist; Andernfalls wird `CString`eine leere .

### <a name="remarks"></a>Bemerkungen

Dies entspricht nicht dem im `OpenEx` Oder-Aufruf `Open` angegebenen Datenquellennamen (Data Source Name, DSN). Welche `GetDatabaseName` Renditen erzielt werden, hängt von ODBC ab. Im Allgemeinen ist eine Datenbank eine Sammlung von Tabellen. Wenn diese Entität einen `GetDatabaseName` Namen hat, gibt sie zurück.

Sie können diesen Namen z. B. in einer Überschrift anzeigen. Wenn beim Abrufen des Namens aus ODBC ein Fehler auftritt, `GetDatabaseName` wird eine leere `CString`zurückgegeben.

## <a name="cdatabaseisopen"></a><a name="isopen"></a>CDatabase::IsOpen

Rufen Sie diese Memberfunktion `CDatabase` auf, um zu bestimmen, ob das Objekt derzeit mit einer Datenquelle verbunden ist.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert `CDatabase` ungleich Null, wenn das Objekt derzeit verbunden ist; andernfalls 0.

## <a name="cdatabasem_hdbc"></a><a name="m_hdbc"></a>CDatabase::m_hdbc

Enthält ein öffentliches Handle für eine ODBC-Datenquellenverbindung – ein "Verbindungshandle".

### <a name="remarks"></a>Bemerkungen

Normalerweise müssen Sie nicht direkt auf diese Membervariable zugreifen. Stattdessen weist das Framework das Handle `OpenEx` `Open`zu, wenn Sie aufrufen oder . Das Framework weist das Handle auf, wenn `CDatabase` Sie den **Löschoperator** für das Objekt aufrufen. Beachten Sie, dass die `Close` Memberfunktion die Zuordnung des Handles nicht aufgibt.

Unter bestimmten Umständen müssen Sie das Handle jedoch möglicherweise direkt verwenden. Wenn Sie z. B. ODBC-API-Funktionen `CDatabase`direkt und nicht über die Klasse aufrufen müssen, benötigen Sie möglicherweise ein Verbindungshandle, um als Parameter übergeben zu werden. Siehe das Codebeispiel unten.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]

## <a name="cdatabaseonsetoptions"></a><a name="onsetoptions"></a>CDatabase::OnSetOptions

Das Framework ruft diese Memberfunktion auf, wenn `ExecuteSQL` eine SQL-Anweisung direkt mit der Memberfunktion ausgeführt wird.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parameter

*hstmt*<br/>
Das ODBC-Anweisungshandle, für das Optionen festgelegt werden.

### <a name="remarks"></a>Bemerkungen

`CRecordset::OnSetOptions`ruft auch diese Memberfunktion auf.

`OnSetOptions`legt den Anmeldetimeoutwert fest. Wenn zuvor die `SetQueryTimeout` und Memberfunktion aufrufe, `OnSetOptions` werden die aktuellen Werte wiedergegeben. Andernfalls werden Standardwerte festgelegt.

> [!NOTE]
> Stellen Sie vor MFC `OnSetOptions` 4.2 auch den Verarbeitungsmodus auf snychronooder asynchron ein. Ab MFC 4.2 sind alle Vorgänge synchron. Um einen asynchronen Vorgang auszuführen, müssen Sie einen direkten `SQLSetPos`Aufruf der ODBC-API-Funktion durchführen.

Sie müssen nicht überschreiben, `OnSetOptions` um den Timeoutwert zu ändern. Um stattdessen den Abfragetimeoutwert `SetQueryTimeout` anzupassen, rufen Sie vor dem Erstellen eines Recordsets auf. `OnSetOptions` verwendet den neuen Wert. Die festgelegten Werte gelten für nachfolgende Vorgänge für alle Recordsets oder direkten SQL-Aufrufe.

Überschreiben, `OnSetOptions` wenn Sie zusätzliche Optionen festlegen möchten. Ihre Außerkraftsetzung sollte `OnSetOptions` die Basisklasse entweder vor oder `SQLSetStmtOption`nach dem Aufruf der ODBC-API-Funktion aufrufen. Befolgen Sie die in der Standardimplementierung des Frameworks dargestellte Methode . `OnSetOptions`

## <a name="cdatabaseopen"></a><a name="open"></a>CDatabase::Öffnen

Rufen Sie diese Memberfunktion auf, um ein neu erstelltes `CDatabase` Objekt zu initialisieren.

```
virtual BOOL Open(
    LPCTSTR lpszDSN,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T("ODBC;"),
    BOOL bUseCursorLib = TRUE);
```

### <a name="parameters"></a>Parameter

*lpszDSN*<br/>
Gibt einen Datenquellennamen an – einen Namen, der über das ODBC-Administratorprogramm bei ODBC registriert ist. Wenn ein DSN-Wert in *lpszConnect* angegeben ist (in der Form "DSN=\<data-source>"), darf er in *lpszDSN*nicht erneut angegeben werden. In diesem Fall sollte *lpszDSN* NULL sein. Andernfalls können Sie NULL übergeben, wenn Sie dem Benutzer ein Datenquellendialogfeld anzeigen möchten, in dem der Benutzer eine Datenquelle auswählen kann. Weitere Informationen finden Sie unter Bemerkungen.

*bExklusiv*<br/>
In dieser Version der Klassenbibliothek wird nicht unterstützt. Derzeit schlägt eine Assertion fehl, wenn dieser Parameter TRUE ist. Die Datenquelle wird immer als freigegeben (nicht exklusiv) geöffnet.

*bReadOnly*<br/>
TRUE, wenn Sie beabsichtigen, dass die Verbindung schreibgeschützt ist, und Aktualisierungen der Datenquelle verbieten. Alle abhängigen Recordsets erben dieses Attribut. Der Standardwert ist FALSE.

*lpszConnect*<br/>
Gibt eine Verbindungszeichenfolge an. Die Verbindungszeichenfolge verkettet Informationen, möglicherweise einschließlich eines Datenquellennamens, einer für die Datenquelle gültigen Benutzer-ID, einer Benutzerauthentifizierungszeichenfolge (Kennwort, wenn die Datenquelle eine erfordert) und anderen Informationen. Der gesamten Verbindungszeichenfolge muss die Zeichenfolge "ODBC;" vorangestellt werden. (Groß- oder Kleinbuchstaben). Die Zeichenfolge "ODBC;" wird verwendet, um anzugeben, dass die Verbindung zu einer ODBC-Datenquelle besteht. Dies ist für die Kompatibilität nach oben, wenn zukünftige Versionen der Klassenbibliothek möglicherweise Nicht-ODBC-Datenquellen unterstützen.

*bUseCursorLib*<br/>
TRUE, wenn die ODBC Cursor Library DLL geladen werden soll. Die Cursorbibliothek maskiert einige Funktionen des zugrunde liegenden ODBC-Treibers und verhindert effektiv die Verwendung von Dynasets (wenn der Treiber sie unterstützt). Die einzigen Cursor, die unterstützt werden, wenn die Cursorbibliothek geladen wird, sind statische Snapshots und Forward-Only-Cursor. Der Standardwert ist TRUE. Wenn Sie ein Recordset-Objekt `CRecordset` direkt daraus erstellen möchten, ohne daraus abzuleiten, sollten Sie die Cursorbibliothek nicht laden.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Verbindung erfolgreich hergestellt wurde; Andernfalls 0, wenn der Benutzer Abbrechen auswählt, wenn ein Dialogfeld angezeigt wird, in dem weitere Verbindungsinformationen angefragt werden. In allen anderen Fällen löst das Framework eine Ausnahme aus.

### <a name="remarks"></a>Bemerkungen

Das Datenbankobjekt muss initialisiert werden, bevor Sie es zum Erstellen eines Recordset-Objekts verwenden können.

> [!NOTE]
> Das Aufrufen der [OpenEx-Memberfunktion](#openex) ist die bevorzugte Methode zum Herstellen einer Verbindung mit einer Datenquelle und zum Initialisieren des Datenbankobjekts.

Wenn die Parameter `Open` in Ihrem Anruf nicht genügend Informationen enthalten, um die Verbindung herzustellen, öffnet der ODBC-Treiber ein Dialogfeld, um die erforderlichen Informationen vom Benutzer zu erhalten. Wenn Sie `Open`aufrufen, wird die Verbindungszeichenfolge *lpszConnect*privat im `CDatabase` Objekt gespeichert und ist durch Aufrufen der [GetConnect-Memberfunktion](#getconnect) verfügbar.

Wenn Sie möchten, können Sie Ihr eigenes `Open` Dialogfeld öffnen, bevor Sie aufrufen, um Informationen vom Benutzer abzurufen, z. B. ein Kennwort, und diese Informationen dann der Verbindungszeichenfolge hinzufügen, die Sie an `Open`übergeben. Oder Sie möchten die verbindungszeichenfolge speichern, die Sie übergeben haben, `Open` damit `CDatabase` Sie sie beim nächsten Aufrufen eines Objekts wiederverwenden können.

Sie können die Verbindungszeichenfolge auch für mehrere Ebenen der `CDatabase` Anmeldeautorisierung (jeweils für ein anderes Objekt) oder zum Übermitteln anderer datenquellenspezifischer Informationen verwenden. Weitere Informationen zu Verbindungszeichenfolgen finden Sie in Kapitel 5 im Windows SDK.

Es ist möglich, dass ein Verbindungsversuch ein Timeout ausfällt, wenn z. B. der DBMS-Host nicht verfügbar ist. Wenn der Verbindungsversuch `Open` fehlschlägt, wird eine `CDBException`ausgelöst.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]

## <a name="cdatabaseopenex"></a><a name="openex"></a>CDatabase::OpenEx

Rufen Sie diese Memberfunktion auf, um ein neu erstelltes `CDatabase` Objekt zu initialisieren.

```
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,
    DWORD dwOptions = 0);
```

### <a name="parameters"></a>Parameter

*lpszConnectString*<br/>
Gibt eine ODBC-Verbindungszeichenfolge an. Dazu gehören der Datenquellenname sowie andere optionale Informationen, z. B. eine Benutzer-ID und ein Kennwort. Beispiel: "DSN=SQLServer_Source; UID=SA; PWD=abc123" ist eine mögliche Verbindungszeichenfolge. Beachten Sie, dass ein Dialogfeld Datenquelle den Benutzer auffordert, eine Datenquelle auszuwählen, wenn Sie NULL für *lpszConnectString*übergeben.

*Dwoptions*<br/>
Eine Bitmaske, die eine Kombination der folgenden Werte angibt. Der Standardwert ist 0, d. h., die Datenbank wird als freigegeben für Schreibzugriff geöffnet, die ODBC-Cursorbibliotheks-DLL wird nicht geladen, und das Dialogfeld für odBC-Verbindungen wird nur angezeigt, wenn nicht genügend Informationen zum Herstellen der Verbindung vorhanden sind.

- `CDatabase::openExclusive`In dieser Version der Klassenbibliothek wird nicht unterstützt. Eine Datenquelle wird immer als freigegeben (nicht exklusiv) geöffnet. Derzeit schlägt eine Assertion fehl, wenn Sie diese Option angeben.

- `CDatabase::openReadOnly`Öffnen Sie die Datenquelle schreibgeschützt.

- `CDatabase::useCursorLib`Laden Sie die ODBC Cursor Library DLL. Die Cursorbibliothek maskiert einige Funktionen des zugrunde liegenden ODBC-Treibers und verhindert effektiv die Verwendung von Dynasets (wenn der Treiber sie unterstützt). Die einzigen Cursor, die unterstützt werden, wenn die Cursorbibliothek geladen wird, sind statische Snapshots und Forward-Only-Cursor. Wenn Sie ein Recordset-Objekt `CRecordset` direkt daraus erstellen möchten, ohne daraus abzuleiten, sollten Sie die Cursorbibliothek nicht laden.

- `CDatabase::noOdbcDialog`Zeigen Sie das Dialogfeld ODBC-Verbindung nicht an, unabhängig davon, ob genügend Verbindungsinformationen bereitgestellt werden.

- `CDatabase::forceOdbcDialog`Zeigen Sie immer das Dialogfeld ODBC-Verbindung an.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Verbindung erfolgreich hergestellt wurde; Andernfalls 0, wenn der Benutzer Abbrechen auswählt, wenn ein Dialogfeld angezeigt wird, in dem weitere Verbindungsinformationen angefragt werden. In allen anderen Fällen löst das Framework eine Ausnahme aus.

### <a name="remarks"></a>Bemerkungen

Das Datenbankobjekt muss initialisiert werden, bevor Sie es zum Erstellen eines Recordset-Objekts verwenden können.

Wenn der Parameter *lpszConnectString* in Ihrem `OpenEx` Aufruf nicht genügend Informationen enthält, um die Verbindung herzustellen, öffnet der ODBC-Treiber `CDatabase::forceOdbcDialog` ein Dialogfeld, um die erforderlichen Informationen vom Benutzer zu erhalten, sofern Sie nicht oder im Parameter `CDatabase::noOdbcDialog` *dwOptions* festgelegt haben. Wenn Sie `OpenEx`aufrufen, wird ihre Verbindungszeichenfolge *lpszConnectString*privat im `CDatabase` Objekt gespeichert und ist durch Aufrufen der [GetConnect-Memberfunktion](#getconnect) verfügbar.

Wenn Sie möchten, können Sie Ihr eigenes `OpenEx` Dialogfeld öffnen, bevor Sie aufrufen, um Informationen vom Benutzer abzurufen, z. B. ein Kennwort, und diese Informationen dann der Verbindungszeichenfolge hinzufügen, die Sie an `OpenEx`übergeben. Oder Sie möchten die verbindungszeichenfolge speichern, die Sie übergeben haben, `OpenEx` damit `CDatabase` Sie sie beim nächsten Aufrufen eines Objekts wiederverwenden können.

Sie können die Verbindungszeichenfolge auch für mehrere Ebenen der `CDatabase` Anmeldeautorisierung (jeweils für ein anderes Objekt) oder zum Übermitteln anderer datenquellenspezifischer Informationen verwenden. Weitere Informationen zu Verbindungszeichenfolgen finden Sie in Kapitel 6 in der *ODBC-Programmiererreferenz*.

Es ist möglich, dass ein Verbindungsversuch ein Timeout ausfällt, wenn z. B. der DBMS-Host nicht verfügbar ist. Wenn der Verbindungsversuch `OpenEx` fehlschlägt, wird eine `CDBException`ausgelöst.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]

## <a name="cdatabaserollback"></a><a name="rollback"></a>CDatabase::Rollback

Rufen Sie diese Memberfunktion auf, um die während einer Transaktion vorgenommenen Änderungen rückgängig zu machen.

```
BOOL Rollback();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Transaktion erfolgreich storniert wurde; andernfalls 0. Wenn `Rollback` ein Aufruf fehlschlägt, sind die Datenquelle und der Transaktionszustand nicht definiert. Wenn `Rollback` die Datei 0 zurückgegeben wird, müssen Sie die Datenquelle überprüfen, um ihren Status zu bestimmen.

### <a name="remarks"></a>Bemerkungen

Alle `CRecordset` `AddNew` `Edit`, `Delete`, `Update` und Aufrufe, die seit der letzten [BeginTrans](#begintrans) ausgeführt wurden, werden in den Zustand zurückgesetzt, der zum Zeitpunkt dieses Aufrufs vorhanden war.

Nach einem `Rollback`Aufruf von ist die Transaktion `BeginTrans` beendet, und Sie müssen erneut eine andere Transaktion aufrufen. Der Datensatz, der vor `BeginTrans` dem Aufruf aktuell `Rollback`war, wird nach wieder zum aktuellen Datensatz.

Nach einem Rollback bleibt der Datensatz, der vor dem Rollback aktuell war, aktuell. Weitere Informationen zum Status des Recordsets und der Datenquelle nach einem Rollback finden Sie im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Beispiel

  Siehe den Artikel [Transaktion: Ausführen einer Transaktion in einem Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="cdatabasesetlogintimeout"></a><a name="setlogintimeout"></a>CDatabase::SetLoginTimeout

Rufen Sie diese Memberfunktion `OpenEx` `Open` auf – bevor Sie aufrufen oder – um die standardmäßige Anzahl von Sekunden zu überschreiben, die zulässig sind, bevor eine versuchte Datenquellenverbindung ein Timesout aufweist.

```cpp
void SetLoginTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Parameter

*dwSekunden*<br/>
Die Anzahl der Sekunden, die vor einem Verbindungsversuch zugelassen werden sollen.

### <a name="remarks"></a>Bemerkungen

Ein Verbindungsversuch kann ein Timeout auftreten, wenn z. B. das DBMS nicht verfügbar ist. Rufen `SetLoginTimeout` Sie auf, nachdem `CDatabase` Sie das `OpenEx` nicht `Open`initialisierte Objekt erstellt haben, aber bevor Sie aufrufen oder .

Der Standardwert für Anmeldetimeouts beträgt 15 Sekunden. Nicht alle Datenquellen unterstützen die Möglichkeit, einen Anmeldetimeoutwert anzugeben. Wenn die Datenquelle kein Timeout unterstützt, erhalten Sie die Ablaufverfolgungsausgabe, aber keine Ausnahme. Ein Wert von 0 bedeutet "unendlich".

## <a name="cdatabasesetquerytimeout"></a><a name="setquerytimeout"></a>CDatabase::SetQueryTimeout

Rufen Sie diese Memberfunktion auf, um die Standardanzahl von Sekunden zu überschreiben, um vor nachfolgenden Vorgängen für das Timeout der verbundenen Datenquelle zuzulassen.

```cpp
void SetQueryTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Parameter

*dwSekunden*<br/>
Die Anzahl der Sekunden, die vor einem Abfrageversuch zugelassen werden sollen.

### <a name="remarks"></a>Bemerkungen

Bei einem Vorgang kann aufgrund von Netzwerkzugriffsproblemen, übermäßiger Abfrageverarbeitungszeit usw. ein Zeitproblem auftreten. Rufen `SetQueryTimeout` Sie vor dem Öffnen des Recordsets oder `AddNew` `Update` vor `Delete` dem Aufruf der Recordset-Funktionen oder Memberfunktionen an, wenn Sie den Abfragetimeoutwert ändern möchten. Die Einstellung wirkt `Open` `AddNew`sich `Update`auf `Delete` alle nachfolgenden , `CDatabase` , und Aufrufe von Recordsets aus, die diesem Objekt zugeordnet sind. Wenn Sie den Abfragetimeoutwert für ein Recordset nach dem Öffnen ändern, wird der Wert für das Recordset nicht geändert. Beispielsweise verwenden `Move` nachfolgende Vorgänge den neuen Wert nicht.

Der Standardwert für Abfragetimeouts beträgt 15 Sekunden. Nicht alle Datenquellen unterstützen die Möglichkeit, einen Abfragetimeoutwert festzulegen. Wenn Sie einen Abfragetimeoutwert von 0 festlegen, tritt kein Timeout auf. die Kommunikation mit der Datenquelle reagiert möglicherweise nicht mehr. Dieses Verhalten kann während der Entwicklung nützlich sein. Wenn die Datenquelle kein Timeout unterstützt, erhalten Sie die Ablaufverfolgungsausgabe, aber keine Ausnahme.

## <a name="see-also"></a>Weitere Informationen

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CRecordset-Klasse](../../mfc/reference/crecordset-class.md)
