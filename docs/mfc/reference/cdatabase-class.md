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
ms.openlocfilehash: ee1503f49f0e60b24e0ef3a9c9631f039ad9355e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223108"
---
# <a name="cdatabase-class"></a>CDatabase-Klasse

Stellt eine Verbindung mit einer Datenquelle dar, über welche die Datenquelle bearbeitet werden kann.

## <a name="syntax"></a>Syntax

```
class CDatabase : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CDatabase:: CDatabase](#cdatabase)|Erstellt ein `CDatabase`-Objekt. Sie müssen das-Objekt initialisieren, indem Sie `OpenEx` oder aufrufen `Open` .|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[CDatabase:: BeginTrans](#begintrans)|Startet eine "Transaction"-– eine Reihe von umkehrbaren aufrufen `AddNew` der `Edit` `Delete` -,-,-und-Element `Update` Funktionen der-Klasse `CRecordset` – für die verbundene Datenquelle. Die Datenquelle muss Transaktionen für unterstützen `BeginTrans` , um eine beliebige Auswirkung zu haben.|
|[CDatabase:: BindParameters](#bindparameters)|Ermöglicht das Binden von Parametern vor dem Aufrufen von `CDatabase::ExecuteSQL` .|
|[CDatabase:: Cancel](#cancel)|Bricht einen asynchronen Vorgang oder einen Prozess von einem zweiten Thread ab.|
|[CDatabase:: CanTransact](#cantransact)|Gibt einen Wert ungleich 0 zurück, wenn die Datenquelle Transaktionen unterstützt.|
|[CDatabase:: CanUpdate](#canupdate)|Gibt einen Wert ungleich 0 (null) zurück, wenn das `CDatabase` Objekt aktualisierbar ist (nicht schreibgeschützt).|
|[CDatabase:: Close](#close)|Schließt die Datenquellen Verbindung.|
|[CDatabase:: CommitTrans](#committrans)|Schließt eine Transaktion ab, die von gestartet wurde `BeginTrans` . Die Befehle in der Transaktion, die die Datenquelle ändern, werden ausgeführt.|
|[CDatabase:: ExecuteSQL](#executesql)|Führt eine SQL-Anweisung aus. Es werden keine Datensätze zurückgegeben.|
|[CDatabase:: getbookmarkpersistenz](#getbookmarkpersistence)|Gibt die Vorgänge an, durch die Lesezeichen für Recordset-Objekte persistent gespeichert werden.|
|[CDatabase::GetConnect](#getconnect)|Gibt die ODBC-Verbindungs Zeichenfolge zurück, mit der das `CDatabase` Objekt mit einer Datenquelle verbunden wird.|
|[CDatabase:: getcurrsorcommitbehavior](#getcursorcommitbehavior)|Gibt die Auswirkung eines Commit für eine Transaktion auf ein offenes Recordset-Objekt an.|
|[CDatabase:: getcurrsorrollbackbehavior](#getcursorrollbackbehavior)|Gibt die Auswirkung eines Rollbacks einer Transaktion auf ein offenes Recordset-Objekt an.|
|[CDatabase:: getDatabaseName](#getdatabasename)|Gibt den Namen der derzeit verwendeten Datenbank zurück.|
|[CDatabase:: IsOpen](#isopen)|Gibt einen Wert ungleich 0 (null) zurück, wenn das `CDatabase` Objekt derzeit mit einer Datenquelle verbunden ist|
|[CDatabase:: ontoptions](#onsetoptions)|Wird von Framework aufgerufen, um Standard Verbindungsoptionen festzulegen. Die Standard Implementierung legt den Timeout Wert für Abfragen fest. Sie können diese Optionen im Vorfeld einrichten, indem Sie aufrufen `SetQueryTimeout` .|
|[CDatabase:: Open](#open)|Stellt eine Verbindung mit einer Datenquelle her (über einen ODBC-Treiber).|
|[CDatabase:: OpenEx](#openex)|Stellt eine Verbindung mit einer Datenquelle her (über einen ODBC-Treiber).|
|[CDatabase:: Rollback](#rollback)|Kehrt Änderungen zurück, die während der aktuellen Transaktion vorgenommen wurden. Die Datenquelle kehrt in ihren vorherigen Zustand zurück, wie im-Befehl definiert `BeginTrans` , nicht geändert.|
|[CDatabase:: setLoginTimeout](#setlogintimeout)|Legt die Anzahl von Sekunden fest, nach denen ein Timeout für eine Datenquellen Verbindung auftritt.|
|[CDatabase:: setQueryTimeout](#setquerytimeout)|Legt die Anzahl von Sekunden fest, nach denen ein Timeout bei Datenbankabfrage Vorgängen auftritt. Wirkt sich auf alle nachfolgenden Recordsets `Open` , `AddNew` , `Edit` und aus `Delete` .|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|Beschreibung|
|----------|-----------------|
|[CDatabase:: M_hdbc](#m_hdbc)|Open Database Connectivity (ODBC)-Verbindungs Handle für eine Datenquelle. Geben Sie *hdbc*ein.|

## <a name="remarks"></a>Bemerkungen

Eine Datenquelle ist eine bestimmte Instanz von Daten, die von einem Datenbankverwaltungssystem (Database Management System, DBMS) gehostet wird. Beispiele hierfür sind Microsoft SQL Server, Microsoft Access, Borland dBase und xbase. Sie können ein oder mehrere `CDatabase` Objekte gleichzeitig in der Anwendung aktiv haben.

> [!NOTE]
> Verwenden Sie stattdessen die Klasse [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) , wenn Sie mit den DAO-Klassen (Data Access Objects) anstelle der Open Database Connectivity-Klassen (ODBC) arbeiten. Weitere Informationen finden Sie im Artikel [Übersicht: Datenbankprogrammierung](../../data/data-access-programming-mfc-atl.md).

Um zu verwenden `CDatabase` , erstellen Sie ein `CDatabase` -Objekt, und nennen Sie seine `OpenEx` Member-Funktion. Dadurch wird eine Verbindung geöffnet. Wenn Sie dann `CRecordset` Objekte erstellen, die für die verbundene Datenquelle ausgeführt werden, übergeben Sie den recordsetkonstruktor einen Zeiger auf das `CDatabase` Objekt. Wenn Sie die Verbindung nicht mehr verwenden, können Sie die `Close` -Member-Funktion aufzurufen und das- `CDatabase` Objekt zerstören. `Close`schließt alle Recordsets, die Sie zuvor noch nicht geschlossen haben.

Weitere Informationen zu finden Sie in `CDatabase` den Artikeln [Datenquelle (ODBC)](../../data/odbc/data-source-odbc.md) und [Übersicht: Datenbankprogrammierung](../../data/data-access-programming-mfc-atl.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CDatabase`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="cdatabasebegintrans"></a><a name="begintrans"></a>CDatabase:: BeginTrans

Mit dieser Member-Funktion können Sie eine Transaktion mit der verbundenen Datenquelle starten.

```
BOOL BeginTrans();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der-Befehl erfolgreich ausgeführt wurde und Änderungen nur manuell ausgeführt werden. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Eine Transaktion besteht aus einem oder mehreren Aufrufen der `AddNew` -, `Edit` `Delete` -,-und- `Update` Member-Funktionen eines- `CRecordset` Objekts. Vor Beginn einer Transaktion muss das `CDatabase` Objekt bereits mit der Datenquelle verbunden sein, indem seine-oder-Member-Funktion aufgerufen wird `OpenEx` `Open` . Um die Transaktion zu beenden, wird [CommitTrans](#committrans) aufgerufen, um alle Änderungen an der Datenquelle zu akzeptieren (und Sie auszuführen) oder [Rollbacks](#rollback) aufzurufen, um die gesamte Transaktion abzubrechen. `BeginTrans`Nach dem Öffnen von Recordsets, die an der Transaktion beteiligt sind, und so nah wie möglich an den eigentlichen Aktualisierungs Vorgängen.

> [!CAUTION]
> Abhängig von Ihrem ODBC-Treiber kann das Öffnen eines Recordsets vor dem Aufrufen von `BeginTrans` Probleme verursachen, wenn aufgerufen wird `Rollback` . Überprüfen Sie den spezifischen Treiber, den Sie verwenden. Wenn Sie z. b. den Microsoft Access-Treiber verwenden, der im Microsoft ODBC Desktop Driver Pack 3,0 enthalten ist, müssen Sie die Anforderung der Jet-Datenbank-Engine berücksichtigen, dass Sie keine Transaktion für eine Datenbank mit einem geöffneten Cursor starten sollten. In den MFC-Datenbankklassen bedeutet ein offener Cursor ein offenes `CRecordset` Objekt. Weitere Informationen finden Sie im [technischen Hinweis 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md).

`BeginTrans`kann auch Datensätze auf dem Server sperren, abhängig von der angeforderten Parallelität und den Funktionen der Datenquelle. Informationen zum Sperren von Daten finden Sie im Artikel [Recordset: Sperren von Datensätzen (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).

Benutzerdefinierte Transaktionen werden im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md)erläutert.

`BeginTrans`Legt den Status fest, in den die Sequenz der Transaktionen zurückgesetzt werden kann (umgekehrt). Wenn Sie einen neuen Zustand für Rollbacks einrichten möchten, führen Sie einen Commit für eine beliebige aktuelle Transaktion aus, `BeginTrans` und rufen Sie

> [!CAUTION]
> Wenn Sie erneut aufrufen, `BeginTrans` ohne oder auszuführen, `CommitTrans` `Rollback` ist ein Fehler aufgetreten.

Ruft die [CanTransact](#cantransact) -Member-Funktion auf, um zu bestimmen, ob der Treiber Transaktionen für eine bestimmte Datenbank unterstützt. Sie sollten auch [GetCursorCommitBehavior](#getcursorcommitbehavior) und [GetCursorRollbackBehavior](#getcursorrollbackbehavior) aufrufen, um die Unterstützung für die Cursor Beibehaltung zu ermitteln.

Weitere Informationen zu Transaktionen finden Sie im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Artikel [Transaktion: Ausführen einer Transaktion in einem Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="cdatabasebindparameters"></a><a name="bindparameters"></a>CDatabase:: BindParameters

`BindParameters`Überschreiben Sie, wenn Sie Parameter vor dem Aufruf von [CDatabase:: ExecuteSQL](#executesql)binden müssen.

```
virtual void BindParameters(HSTMT hstmt);
```

### <a name="parameters"></a>Parameter

*hstmt*<br/>
Das ODBC-Anweisungs Handle, für das Sie Parameter binden möchten.

### <a name="remarks"></a>Bemerkungen

Diese Vorgehensweise ist nützlich, wenn Sie das Resultset nicht aus einer gespeicherten Prozedur benötigen.

In ihrer außer Kraft setzung, `SQLBindParameters` und verwandte ODBC-Funktionen, um die Parameter zu binden. MFC ruft Ihre außer Kraft Setzung vor dem Aufruf von auf `ExecuteSQL` . Sie müssen nicht aufrufen `SQLPrepare` ; `ExecuteSQL` ruft `SQLExecDirect` den *hstmt*auf und zerstört ihn, der nur einmal verwendet wird.

## <a name="cdatabasecancel"></a><a name="cancel"></a>CDatabase:: Cancel

Rufen Sie diese Member-Funktion auf, um anzufordern, dass die Datenquelle entweder einen asynchronen Vorgang in Bearbeitung oder einen Prozess von einem zweiten Thread abbrechen soll.

```cpp
void Cancel();
```

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass die MFC-ODBC-Klassen die asynchrone Verarbeitung nicht mehr verwenden. zum Ausführen eines asynchronen Vorgangs müssen Sie die ODBC-API-Funktion " [SQLSetConnectOption](/sql/odbc/reference/syntax/sqlsetconnectoption-function)" direkt aufrufen. Weitere Informationen finden Sie unter [asynchrone Ausführung](/sql/odbc/reference/develop-app/asynchronous-execution).

## <a name="cdatabasecantransact"></a><a name="cantransact"></a>CDatabase:: CanTransact

Mit dieser Member-Funktion können Sie ermitteln, ob die Datenbank Transaktionen zulässt.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0, wenn Recordsets, die dieses `CDatabase` Objekt verwenden, Transaktionen zulassen; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu Transaktionen finden Sie im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="cdatabasecanupdate"></a><a name="canupdate"></a>CDatabase:: CanUpdate

Mit dieser Member-Funktion können Sie feststellen, ob das `CDatabase` Objekt Updates zulässt.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn das `CDatabase` Objekt Aktualisierungen zulässt; andernfalls 0 (null), um anzugeben, dass Sie "true" in *breadnur* beim Öffnen des Objekts "true" und `CDatabase` die Datenquelle selbst schreibgeschützt haben. Die Datenquelle ist schreibgeschützt, wenn ein Rückruf der ODBC-API-Funktion `SQLGetInfo` für SQL_DATASOURCE_READ_ONLY "y" zurückgibt.

### <a name="remarks"></a>Bemerkungen

Updates werden nicht von allen Treibern unterstützt.

## <a name="cdatabasecdatabase"></a><a name="cdatabase"></a>CDatabase:: CDatabase

Erstellt ein `CDatabase`-Objekt.

```
CDatabase();
```

### <a name="remarks"></a>Bemerkungen

Nach dem Erstellen des-Objekts müssen Sie seine- `OpenEx` oder- `Open` Member-Funktion zum Herstellen einer Verbindung mit einer angegebenen Datenquelle aufruft.

Möglicherweise ist es praktisch, das `CDatabase` Objekt in Ihre Dokument Klasse einzubetten.

### <a name="example"></a>Beispiel

Dieses Beispiel veranschaulicht die Verwendung von `CDatabase` in einer von `CDocument` abgeleiteten Klasse.

[!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]

[!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]

## <a name="cdatabaseclose"></a><a name="close"></a>CDatabase:: Close

Wenn Sie die Verbindung mit einer Datenquelle trennen möchten, wird diese Member-Funktion aufgerufen.

```
virtual void Close();
```

### <a name="remarks"></a>Bemerkungen

Sie müssen alle Recordsets schließen, die dem-Objekt zugeordnet sind, `CDatabase` bevor Sie diese Member-Funktion aufruft. Da `Close` das-Objekt nicht zerstört `CDatabase` , können Sie das-Objekt wieder verwenden, indem Sie eine neue Verbindung zur gleichen Datenquelle oder zu einer anderen Datenquelle öffnen.

Alle ausstehenden `AddNew` oder- `Edit` Anweisungen von Recordsets, die die Datenbank verwenden, werden abgebrochen, und für alle ausstehenden Transaktionen wird ein Rollback ausgeführt. Alle vom Objekt abhängigen Recordsets `CDatabase` bleiben in einem nicht definierten Zustand.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]

## <a name="cdatabasecommittrans"></a><a name="committrans"></a>CDatabase:: CommitTrans

Ruft diese Member-Funktion auf, wenn Transaktionen abgeschlossen werden.

```
BOOL CommitTrans();
```

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn für die Updates erfolgreich ein Commit ausgeführt wurde. andernfalls 0. Wenn `CommitTrans` fehlschlägt, ist der Status der Datenquelle nicht definiert. Sie müssen die Daten überprüfen, um deren Status zu ermitteln.

### <a name="remarks"></a>Bemerkungen

Eine Transaktion besteht aus einer Reihe von Aufrufen der `AddNew` -, `Edit` `Delete` -,-und-Member- `Update` Funktionen eines- `CRecordset` Objekts, das mit einem Aufruf der [BeginTrans](#begintrans) -Member-Funktion begonnen hat. `CommitTrans`führt einen Commit der Transaktion aus. Standardmäßig wird für Updates sofort ein Commit ausgeführt. das Aufrufen `BeginTrans` von bewirkt, dass die Aktualisierung der Updates verzögert wird, bis `CommitTrans` aufgerufen wird.

Bis Sie aufgerufen `CommitTrans` haben, um eine Transaktion zu beenden, können Sie die [Rollback](#rollback) -Member-Funktion aufzurufen, um die Transaktion abzubrechen und die Datenquelle in Ihrem ursprünglichen Zustand zu belassen. Um eine neue Transaktion zu starten, wird `BeginTrans` erneut aufgerufen.

Weitere Informationen zu Transaktionen finden Sie im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Artikel [Transaktion: Ausführen einer Transaktion in einem Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="cdatabaseexecutesql"></a><a name="executesql"></a>CDatabase:: ExecuteSQL

Wenn Sie einen SQL-Befehl direkt ausführen müssen, nennen Sie diese Member-Funktion.

```cpp
void ExecuteSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Parameter

*lpszSQL*<br/>
Zeiger auf eine mit NULL endenden Zeichenfolge, die einen gültigen auszuführenden SQL-Befehl enthält. Sie können eine [CString](../../atl-mfc-shared/reference/cstringt-class.md)übergeben.

### <a name="remarks"></a>Bemerkungen

Erstellen Sie den Befehl als NULL-terminierte Zeichenfolge. `ExecuteSQL`gibt keine Datensätze zurück. Wenn Sie mit Datensätzen arbeiten möchten, verwenden Sie stattdessen ein Recordset-Objekt.

Die meisten ihrer Befehle für eine Datenquelle werden über Recordset-Objekte ausgegeben, die Befehle zum Auswählen von Daten, Einfügen neuer Datensätze, Löschen von Datensätzen und Bearbeiten von Datensätzen unterstützen. Allerdings werden nicht alle ODBC-Funktionen direkt von den Datenbankklassen unterstützt, sodass Sie manchmal einen direkten SQL-Befehl mit erstellen müssen `ExecuteSQL` .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]

## <a name="cdatabasegetbookmarkpersistence"></a><a name="getbookmarkpersistence"></a>CDatabase:: getbookmarkpersistenz

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
|SQL_BP_CLOSE|Lesezeichen sind nach einem- `Requery` Vorgang gültig.|
|SQL_BP_DELETE|Das Lesezeichen für eine Zeile ist nach einem- `Delete` Vorgang in dieser Zeile gültig.|
|SQL_BP_DROP|Lesezeichen sind nach einem- `Close` Vorgang gültig.|
|SQL_BP_SCROLL|Lesezeichen sind nach jedem `Move` Vorgang gültig. Damit wird mühelos identifiziert, ob Lesezeichen im Datensatz unterstützt werden, wie von `CRecordset::CanBookmark` zurückgegeben.|
|SQL_BP_TRANSACTION|Lesezeichen sind gültig, nachdem eine Transaktion übernommen oder zurückgesetzt wurde.|
|SQL_BP_UPDATE|Das Lesezeichen für eine Zeile ist nach einem `Update` Vorgang in dieser Zeile gültig.|
|SQL_BP_OTHER_HSTMT|Lesezeichen, die mit einem recordset-Objekt verbunden sind, sind in einem zweiten Datensatz gültig.|

Weitere Informationen zu diesem Rückgabewert finden Sie unter der ODBC-API-Funktion `SQLGetInfo` in der Windows SDK. Weitere Informationen zu Lesezeichen finden Sie im Artikel [Recordset: Lesezeichen und absolute Positionen (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

## <a name="cdatabasegetconnect"></a><a name="getconnect"></a>CDatabase:: GetConnect

Rufen Sie diese Memberfunktion auf, um die während des Aufrufs von `OpenEx` oder `Open` verwendete Verbindungszeichenfolge abzurufen, die das `CDatabase`-Objekt mit einer Datenquelle verbunden hat.

```
const CString GetConnect() const;
```

### <a name="return-value"></a>Rückgabewert

Ein **`const`** [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Wert, der die Verbindungs Zeichenfolge enthält, wenn `OpenEx` oder `Open` aufgerufen wurde; andernfalls eine leere Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

Eine Beschreibung, wie die Verbindungs Zeichenfolge erstellt wird, finden Sie unter [CDatabase:: Open](#open) .

## <a name="cdatabasegetcursorcommitbehavior"></a><a name="getcursorcommitbehavior"></a>CDatabase:: getcurrsorcommitbehavior

Diese Member-Funktion wird aufgerufen, um zu bestimmen, wie sich ein [CommitTrans](#committrans) -Vorgang auf Cursor bei geöffneten recordsetobjekten auswirkt.

```
int GetCursorCommitBehavior() const;
```

### <a name="return-value"></a>Rückgabewert

Ein-Wert, der die Auswirkung von Transaktionen auf geöffnete Recordset-Objekte angibt. Einzelheiten finden Sie unter "Hinweise".

### <a name="remarks"></a>Bemerkungen

In der folgenden Tabelle sind die möglichen Rückgabewerte für `GetCursorCommitBehavior` und die entsprechenden Auswirkungen auf das geöffnete Recordset aufgeführt.

|Rückgabewert|Auswirkung auf CRecordset-Objekte|
|------------------|----------------------------------|
|SQL_CB_CLOSE|`CRecordset::Requery`Direkt nach dem Transaktionscommit aufzurufen.|
|SQL_CB_DELETE|`CRecordset::Close`Direkt nach dem Transaktionscommit aufzurufen.|
|SQL_CB_PRESERVE|Fahren Sie mit `CRecordset` Vorgängen normal fort.|

Weitere Informationen zu diesem Rückgabewert finden Sie unter der ODBC-API-Funktion `SQLGetInfo` in der Windows SDK. Weitere Informationen zu Transaktionen finden Sie im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="cdatabasegetcursorrollbackbehavior"></a><a name="getcursorrollbackbehavior"></a>CDatabase:: getcurrsorrollbackbehavior

Diese Member-Funktion wird aufgerufen, um zu bestimmen, wie sich ein [Rollback](#rollback) -Vorgang auf Cursor bei geöffneten recordsetobjekten auswirkt.

```
int GetCursorRollbackBehavior() const;
```

### <a name="return-value"></a>Rückgabewert

Ein-Wert, der die Auswirkung von Transaktionen auf geöffnete Recordset-Objekte angibt. Einzelheiten finden Sie unter "Hinweise".

### <a name="remarks"></a>Bemerkungen

In der folgenden Tabelle sind die möglichen Rückgabewerte für `GetCursorRollbackBehavior` und die entsprechenden Auswirkungen auf das geöffnete Recordset aufgeführt.

|Rückgabewert|Auswirkung auf CRecordset-Objekte|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Wird `CRecordset::Requery` unmittelbar nach dem Transaktionsrollback aufgerufen.|
|SQL_CB_DELETE|Wird `CRecordset::Close` unmittelbar nach dem Transaktionsrollback aufgerufen.|
|SQL_CB_PRESERVE|Fahren Sie mit `CRecordset` Vorgängen normal fort.|

Weitere Informationen zu diesem Rückgabewert finden Sie unter der ODBC-API-Funktion `SQLGetInfo` in der Windows SDK. Weitere Informationen zu Transaktionen finden Sie im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="cdatabasegetdatabasename"></a><a name="getdatabasename"></a>CDatabase:: getDatabaseName

Rufen Sie diese Member-Funktion auf, um den Namen der derzeit verbundenen Datenbank abzurufen (vorausgesetzt, die Datenquelle definiert ein benanntes Objekt mit dem Namen "Database").

```
CString GetDatabaseName() const;
```

### <a name="return-value"></a>Rückgabewert

Eine [CString](../../atl-mfc-shared/reference/cstringt-class.md) , die den Datenbanknamen enthält, wenn erfolgreich. andernfalls ein leerer `CString` .

### <a name="remarks"></a>Bemerkungen

Dies ist nicht mit dem Datenquellen Namen (DSN) identisch, der im-oder-Befehl angegeben wurde `OpenEx` `Open` . Was `GetDatabaseName` zurückgibt, hängt von ODBC ab. Im Allgemeinen handelt es sich bei einer Datenbank um eine Sammlung von Tabellen. Wenn diese Entität über einen Namen verfügt, wird `GetDatabaseName` Sie zurückgegeben.

Sie können z. b. diesen Namen in einer Überschrift anzeigen. Wenn beim Abrufen des Namens aus ODBC ein Fehler auftritt, `GetDatabaseName` gibt einen leeren Wert `CString` zurück.

## <a name="cdatabaseisopen"></a><a name="isopen"></a>CDatabase:: IsOpen

Mit dieser Member-Funktion können Sie ermitteln, ob das `CDatabase` Objekt derzeit mit einer Datenquelle verbunden ist.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn das `CDatabase` Objekt derzeit verbunden ist, andernfalls 0.

## <a name="cdatabasem_hdbc"></a><a name="m_hdbc"></a>CDatabase:: M_hdbc

Enthält ein öffentliches Handle für eine ODBC-Datenquellen Verbindung – ein "Verbindungs Handle".

### <a name="remarks"></a>Bemerkungen

Normalerweise ist es nicht erforderlich, direkt auf diese Element Variable zuzugreifen. Stattdessen ordnet das Framework das Handle zu, wenn Sie `OpenEx` oder aufruft `Open` . Das-Framework hebt die Zuordnung des Handles auf, wenn Sie den- **`delete`** Operator für das-Objekt aufzurufen `CDatabase` . Beachten Sie, dass die `Close` Member-Funktion das Handle nicht aufhebt.

Unter bestimmten Umständen müssen Sie das Handle jedoch möglicherweise direkt verwenden. Wenn Sie z. b. ODBC-API-Funktionen direkt anstelle der Klasse aufrufen müssen `CDatabase` , benötigen Sie möglicherweise ein Verbindungs Handle, das als Parameter übergeben wird. Weitere Informationen finden Sie im folgenden Codebeispiel.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]

## <a name="cdatabaseonsetoptions"></a><a name="onsetoptions"></a>CDatabase:: ontoptions

Das Framework ruft diese Member-Funktion auf, wenn eine SQL-Anweisung direkt mit der Member-Funktion ausgeführt wird `ExecuteSQL` .

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parameter

*hstmt*<br/>
Das ODBC-Anweisungs Handle, für das Optionen festgelegt werden.

### <a name="remarks"></a>Bemerkungen

`CRecordset::OnSetOptions`Ruft auch diese Member-Funktion auf.

`OnSetOptions`Legt den Wert für das Anmeldungs Timeout fest. Wenn vorherige Aufrufe der `SetQueryTimeout` -und der-Member-Funktion vorhanden sind, werden `OnSetOptions` die aktuellen Werte wiedergegeben; andernfalls werden Standardwerte festgelegt.

> [!NOTE]
> Legen Sie vor MFC 4,2 `OnSetOptions` auch den Verarbeitungsmodus auf snychronous oder Asynchronous fest. Ab MFC 4,2 sind alle Vorgänge synchron. Zum Ausführen eines asynchronen Vorgangs müssen Sie einen direkten Rückruf für die ODBC-API-Funktion durchführen `SQLSetPos` .

Sie müssen nicht außer Kraft setzen `OnSetOptions` , um den Timeout Wert zu ändern. Um stattdessen den Timeout Wert für Abfragen anzupassen, müssen Sie `SetQueryTimeout` vor dem Erstellen eines Recordsets aufzurufen `OnSetOptions` . verwendet den neuen Wert. Die festgelegten Werte gelten für nachfolgende Vorgänge bei allen Recordsets oder bei direkten SQL-aufrufen.

`OnSetOptions`Überschreiben Sie, wenn Sie zusätzliche Optionen festlegen möchten. Ihre außer Kraft Setzung sollte die Basisklasse `OnSetOptions` entweder vor oder nach dem Abrufen der ODBC-API-Funktion aufruft `SQLSetStmtOption` . Befolgen Sie die-Methode, die in der Standard Implementierung des Frameworks von veranschaulicht wird `OnSetOptions` .

## <a name="cdatabaseopen"></a><a name="open"></a>CDatabase:: Open

Mit dieser Member-Funktion wird ein neu konstruiertes `CDatabase` Objekt initialisiert.

```
virtual BOOL Open(
    LPCTSTR lpszDSN,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T("ODBC;"),
    BOOL bUseCursorLib = TRUE);
```

### <a name="parameters"></a>Parameter

*lpszdsn*<br/>
Gibt einen Namen für die Datenquelle an – einen Namen, der über das ODBC-Administrator Programm bei ODBC registriert ist. Wenn ein DSN-Wert in *lpszconnect* (in der Form "DSN = \<data-source> ") angegeben wird, darf er in *lpszdsn*nicht erneut angegeben werden. In diesem Fall sollte *lpszdsn* NULL sein. Andernfalls können Sie NULL übergeben, wenn Sie dem Benutzer ein Dialogfeld für die Datenquelle präsentieren möchten, in dem der Benutzer eine Datenquelle auswählen kann. Weitere Informationen finden Sie unter "Hinweise".

*bExclusive*<br/>
Wird in dieser Version der Klassenbibliothek nicht unterstützt. Derzeit schlägt eine-Übersetzung fehl, wenn dieser Parameter true ist. Die Datenquelle wird immer als freigegeben (nicht exklusiv) geöffnet.

*nur Bread*<br/>
TRUE, wenn die Verbindung schreibgeschützt sein soll und die Aktualisierung der Datenquelle untersagt werden soll. Alle abhängigen Recordsets erben dieses Attribut. Der Standardwert ist FALSE.

*lpszconnect*<br/>
Gibt eine Verbindungs Zeichenfolge an. Die Verbindungs Zeichenfolge verkettet Informationen, möglicherweise einschließlich eines Datenquellen namens, eine Benutzer-ID, die für die Datenquelle gültig ist, eine Benutzer-Authentifizierungs Zeichenfolge (Kennwort, wenn die Datenquelle eine solche erfordert) und weitere Informationen. Die gesamte Verbindungs Zeichenfolge muss der Zeichenfolge "ODBC;" vorangestellt sein. (Großbuchstaben oder Kleinbuchstaben). Die Zeichenfolge "ODBC;" wird verwendet, um anzugeben, dass die Verbindung mit einer ODBC-Datenquelle hergestellt wird. Dies dient der aufwärts Kompatibilität, wenn in zukünftigen Versionen der Klassenbibliothek möglicherweise nicht-ODBC-Datenquellen unterstützt werden.

*bUseCursorLib*<br/>
TRUE, wenn die ODBC-Cursor-Bibliotheks-DLL geladen werden soll. Die Cursor Bibliothek maskiert einige Funktionen des zugrunde liegenden ODBC-Treibers und verhindert so die Verwendung von Dynasets (wenn Sie vom Treiber unterstützt werden). Die einzigen unterstützten Cursor, wenn die Cursor Bibliothek geladen wird, sind statische Momentaufnahmen und Vorwärts Cursor. Der Standardwert ist TRUE. Wenn Sie Vorhaben, ein Recordset-Objekt direkt aus zu erstellen `CRecordset` , ohne davon abzuleiten, sollten Sie die Cursor Bibliothek nicht laden.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Verbindung erfolgreich hergestellt wurde. andernfalls 0, wenn der Benutzer Abbrechen auswählt, wenn ein Dialogfeld angezeigt wird, das weitere Verbindungsinformationen anfordert. In allen anderen Fällen löst das Framework eine Ausnahme aus.

### <a name="remarks"></a>Bemerkungen

Das Datenbankobjekt muss initialisiert werden, bevor es zum Erstellen eines Recordset-Objekts verwendet werden kann.

> [!NOTE]
> Das Aufrufen der [OpenEx](#openex) -Member-Funktion ist die bevorzugte Methode zum Herstellen einer Verbindung mit einer Datenquelle und zum Initialisieren des Datenbankobjekts.

Wenn die Parameter in Ihrem-Befehl `Open` nicht genügend Informationen enthalten, um die Verbindung herzustellen, öffnet der ODBC-Treiber ein Dialogfeld, in dem die erforderlichen Informationen vom Benutzer abgerufen werden. Wenn Sie aufrufen `Open` , wird die Verbindungs Zeichenfolge *lpszconnect*privat im `CDatabase` -Objekt gespeichert und ist verfügbar, indem die [GetConnect](#getconnect) -Member-Funktion aufgerufen wird.

Wenn Sie möchten, können Sie ein eigenes Dialogfeld öffnen, bevor Sie `Open` zum Abrufen von Informationen vom Benutzer, z. b. ein Kennwort, abrufen und diese Informationen dann der Verbindungs Zeichenfolge hinzufügen, die Sie an übergeben `Open` . Möglicherweise möchten Sie auch die Verbindungs Zeichenfolge speichern, die Sie übergeben, damit Sie Sie wieder verwenden können, wenn die Anwendung das nächste Mal `Open` für ein- `CDatabase` Objekt aufruft.

Sie können auch die Verbindungs Zeichenfolge für mehrere Ebenen der Anmelde Autorisierung (jeweils für ein anderes `CDatabase` Objekt) oder zum übermitteln anderer Datenquellen spezifischer Informationen verwenden. Weitere Informationen zu Verbindungs Zeichenfolgen finden Sie in Kapitel 5 des Windows SDK.

Es ist möglich, dass bei einem Verbindungsversuch ein Timeout auftritt, wenn beispielsweise der DBMS-Host nicht verfügbar ist. Wenn der Verbindungsversuch fehlschlägt, löst `Open` eine aus `CDBException` .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]

## <a name="cdatabaseopenex"></a><a name="openex"></a>CDatabase:: OpenEx

Mit dieser Member-Funktion wird ein neu konstruiertes `CDatabase` Objekt initialisiert.

```
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,
    DWORD dwOptions = 0);
```

### <a name="parameters"></a>Parameter

*lpszconnectstring*<br/>
Gibt eine ODBC-Verbindungs Zeichenfolge an. Dies schließt den Namen der Datenquelle sowie andere optionale Informationen ein, z. b. eine Benutzer-ID und ein Kennwort. Beispiel: "DSN = SQLServer_Source; UID = SA; PWD = abc123 "ist eine mögliche Verbindungs Zeichenfolge. Beachten Sie Folgendes: Wenn Sie NULL für *lpszconnectstring*übergeben, wird der Benutzer im Dialogfeld Datenquelle aufgefordert, eine Datenquelle auszuwählen.

*dwOptions*<br/>
Eine Bitmaske, die eine Kombination der folgenden Werte angibt. Der Standardwert ist 0. Dies bedeutet, dass die Datenbank als Shared mit Schreibzugriff geöffnet wird, dass die ODBC-Cursor Bibliotheks-DLL nicht geladen wird. das Dialogfeld ODBC-Verbindung wird nur dann angezeigt, wenn nicht genügend Informationen vorhanden sind, um die Verbindung herzustellen.

- `CDatabase::openExclusive`Wird in dieser Version der Klassenbibliothek nicht unterstützt. Eine Datenquelle wird immer als freigegeben (nicht exklusiv) geöffnet. Derzeit schlägt eine-Übersetzung fehl, wenn Sie diese Option angeben.

- `CDatabase::openReadOnly`Öffnen Sie die Datenquelle als schreibgeschützt.

- `CDatabase::useCursorLib`Laden Sie die ODBC-Cursor Bibliotheks-DLL. Die Cursor Bibliothek maskiert einige Funktionen des zugrunde liegenden ODBC-Treibers und verhindert so die Verwendung von Dynasets (wenn Sie vom Treiber unterstützt werden). Die einzigen unterstützten Cursor, wenn die Cursor Bibliothek geladen wird, sind statische Momentaufnahmen und Vorwärts Cursor. Wenn Sie Vorhaben, ein Recordset-Objekt direkt aus zu erstellen `CRecordset` , ohne davon abzuleiten, sollten Sie die Cursor Bibliothek nicht laden.

- `CDatabase::noOdbcDialog`Zeigen Sie das Dialogfeld ODBC-Verbindung nicht an, unabhängig davon, ob genügend Verbindungsinformationen bereitgestellt werden.

- `CDatabase::forceOdbcDialog`Zeigt immer das Dialogfeld ODBC-Verbindung an.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Verbindung erfolgreich hergestellt wurde. andernfalls 0, wenn der Benutzer Abbrechen auswählt, wenn ein Dialogfeld angezeigt wird, das weitere Verbindungsinformationen anfordert. In allen anderen Fällen löst das Framework eine Ausnahme aus.

### <a name="remarks"></a>Bemerkungen

Das Datenbankobjekt muss initialisiert werden, bevor es zum Erstellen eines Recordset-Objekts verwendet werden kann.

Wenn der *lpszconnectstring* -Parameter in Ihrem-Befehl `OpenEx` nicht genügend Informationen enthält, um die Verbindung herzustellen, öffnet der ODBC-Treiber ein Dialogfeld, in dem die erforderlichen Informationen vom Benutzer abgerufen werden, sofern Sie nicht `CDatabase::noOdbcDialog` oder `CDatabase::forceOdbcDialog` im *dwOptions* -Parameter festgelegt haben. Wenn Sie aufrufen `OpenEx` , wird die Verbindungs Zeichenfolge *lpszconnectstring*privat im `CDatabase` -Objekt gespeichert und steht durch Aufrufen der [GetConnect](#getconnect) -Member-Funktion zur Verfügung.

Wenn Sie möchten, können Sie ein eigenes Dialogfeld öffnen, bevor Sie `OpenEx` zum Abrufen von Informationen vom Benutzer, z. b. ein Kennwort, abrufen und diese Informationen dann der Verbindungs Zeichenfolge hinzufügen, die Sie an übergeben `OpenEx` . Möglicherweise möchten Sie auch die Verbindungs Zeichenfolge speichern, die Sie übergeben, damit Sie Sie wieder verwenden können, wenn die Anwendung das nächste Mal `OpenEx` für ein- `CDatabase` Objekt aufruft.

Sie können auch die Verbindungs Zeichenfolge für mehrere Ebenen der Anmelde Autorisierung (jeweils für ein anderes `CDatabase` Objekt) oder zum übermitteln anderer Datenquellen spezifischer Informationen verwenden. Weitere Informationen zu Verbindungs Zeichenfolgen finden Sie in Kapitel 6 in der *ODBC Programmer es Reference*.

Es ist möglich, dass bei einem Verbindungsversuch ein Timeout auftritt, wenn beispielsweise der DBMS-Host nicht verfügbar ist. Wenn der Verbindungsversuch fehlschlägt, löst `OpenEx` eine aus `CDBException` .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]

## <a name="cdatabaserollback"></a><a name="rollback"></a>CDatabase:: Rollback

Mit dieser Member-Funktion können Sie die während einer Transaktion vorgenommenen Änderungen umkehren.

```
BOOL Rollback();
```

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn die Transaktion erfolgreich rückgängig gemacht wurde. andernfalls 0. Wenn ein `Rollback` -Rückruf fehlschlägt, sind die Datenquelle und die Transaktions Zustände nicht definiert. Wenn `Rollback` 0 zurückgibt, müssen Sie die Datenquelle überprüfen, um deren Status zu ermitteln.

### <a name="remarks"></a>Bemerkungen

Alle `CRecordset` `AddNew` `Edit` -, `Delete` -,-und-Aufrufe, die `Update` seit dem letzten [BeginTrans](#begintrans) ausgeführt wurden, werden auf den Zustand zurückgesetzt, der zum Zeitpunkt des Aufrufs vorhanden war.

Nach einem-Aufrufvorgang `Rollback` ist die Transaktion abgeschlossen, und Sie müssen `BeginTrans` erneut einen Rückruf für eine andere Transaktion ausführen. Der Datensatz, der vor dem Aufruf von aktuell war, `BeginTrans` wird erneut zum aktuellen Datensatz `Rollback` .

Nach einem Rollback bleibt der Datensatz, der vor dem Rollback aktuell war, aktuell. Ausführliche Informationen zum Status des Recordsets und der Datenquelle nach einem Rollback finden Sie im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Artikel [Transaktion: Ausführen einer Transaktion in einem Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="cdatabasesetlogintimeout"></a><a name="setlogintimeout"></a>CDatabase:: setLoginTimeout

Nennen Sie diese Member-Funktion – vor `OpenEx` `Open` dem Ausführen von oder –, um die zulässige Standard Anzahl von Sekunden vor dem Timeout einer versuchten Datenquellen Verbindung zu überschreiben.

```cpp
void SetLoginTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Parameter

*dwseconds*<br/>
Die Anzahl der Sekunden, die vor dem Timeout eines Verbindungsversuchs zugelassen werden.

### <a name="remarks"></a>Bemerkungen

Bei einem Verbindungsversuch tritt möglicherweise ein Timeout auf, wenn das DBMS beispielsweise nicht verfügbar ist. Wird aufgerufen, `SetLoginTimeout` nachdem Sie das nicht initialisierte Objekt erstellt haben, `CDatabase` aber bevor Sie `OpenEx` oder aufruft `Open` .

Der Standardwert für Anmeldungs Timeouts beträgt 15 Sekunden. Nicht alle Datenquellen unterstützen die Möglichkeit, einen Anmeldungs Timeout Wert anzugeben. Wenn die Datenquelle kein Timeout unterstützt, erhalten Sie eine Ausgabe der Ablauf Verfolgung, aber keine Ausnahme. Der Wert 0 bedeutet "unendlich".

## <a name="cdatabasesetquerytimeout"></a><a name="setquerytimeout"></a>CDatabase:: setQueryTimeout

Diese Member-Funktion wird aufgerufen, um die Standard Anzahl von Sekunden zu überschreiben, die vor nachfolgenden Vorgängen für die verbundene Datenquelle zugelassen werden.

```cpp
void SetQueryTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Parameter

*dwseconds*<br/>
Die Anzahl der Sekunden, die vor dem Timeout eines Abfrage Versuchs zulässig ist.

### <a name="remarks"></a>Bemerkungen

Ein Vorgang kann aufgrund von Netzwerk Zugriffsproblemen, einer übermäßigen Abfrage Verarbeitungszeit usw. zu einem Timeout kommen. Rufen `SetQueryTimeout` Sie vor dem Öffnen des Recordsets oder vor dem Aufrufen der-oder-Element Funktionen des Recordsets auf `AddNew` , `Update` `Delete` Wenn Sie den Abfrage Timeout Wert ändern möchten. Die-Einstellung wirkt sich auf alle nachfolgenden `Open` Aufrufe von, `AddNew` , `Update` und `Delete` auf alle diesem-Objekt zugeordneten Recordsets aus `CDatabase` . Wenn Sie den Wert für das Abfrage Timeout für ein Recordset nach dem Öffnen ändern, wird der Wert für das Recordset nicht geändert. Nachfolgende `Move` Vorgänge verwenden z. b. nicht den neuen Wert.

Der Standardwert für Abfrage Timeouts beträgt 15 Sekunden. Nicht alle Datenquellen unterstützen die Möglichkeit, einen Abfrage Timeout Wert festzulegen. Wenn Sie einen Abfrage Timeout Wert von 0 (null) festlegen, tritt kein Timeout auf. die Kommunikation mit der Datenquelle reagiert möglicherweise nicht mehr. Dieses Verhalten kann während der Entwicklung nützlich sein. Wenn die Datenquelle kein Timeout unterstützt, erhalten Sie eine Ausgabe der Ablauf Verfolgung, aber keine Ausnahme.

## <a name="see-also"></a>Weitere Informationen

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CRecordset-Klasse](../../mfc/reference/crecordset-class.md)
