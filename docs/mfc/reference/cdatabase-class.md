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
ms.openlocfilehash: ebc36d82af9bfe12ab30a86214e58610b5eaab95
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424506"
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
|[CDatabase:: CDatabase](#cdatabase)|Erstellt ein `CDatabase`-Objekt. Sie müssen das-Objekt durch Aufrufen von `OpenEx` oder `Open`initialisieren.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CDatabase:: BeginTrans](#begintrans)|Startet eine "Transaktion" – eine Reihe von umkehrbaren Aufrufen an die Funktionen `AddNew`, `Edit`, `Delete`und `Update` Member der Klasse `CRecordset` – für die verbundene Datenquelle. Die Datenquelle muss Transaktionen unterstützen, damit `BeginTrans` eine beliebige Auswirkung haben.|
|[CDatabase:: BindParameters](#bindparameters)|Ermöglicht das Binden von Parametern, bevor `CDatabase::ExecuteSQL`aufgerufen wird.|
|[CDatabase:: Cancel](#cancel)|Bricht einen asynchronen Vorgang oder einen Prozess von einem zweiten Thread ab.|
|[CDatabase:: CanTransact](#cantransact)|Gibt einen Wert ungleich 0 zurück, wenn die Datenquelle Transaktionen unterstützt.|
|[CDatabase:: CanUpdate](#canupdate)|Gibt einen Wert ungleich 0 (null) zurück, wenn das `CDatabase` Objekt aktualisierbar ist (nicht schreibgeschützt).|
|[CDatabase:: Close](#close)|Schließt die Datenquellen Verbindung.|
|[CDatabase:: CommitTrans](#committrans)|Schließt eine Transaktion ab, die von `BeginTrans`gestartet wurde. Die Befehle in der Transaktion, die die Datenquelle ändern, werden ausgeführt.|
|[CDatabase:: ExecuteSQL](#executesql)|Führt eine SQL-Anweisung aus. Es werden keine Datensätze zurückgegeben.|
|[CDatabase:: getbookmarkpersistenz](#getbookmarkpersistence)|Gibt die Vorgänge an, durch die Lesezeichen für Recordset-Objekte persistent gespeichert werden.|
|[CDatabase:: GetConnect](#getconnect)|Gibt die ODBC-Verbindungs Zeichenfolge zurück, mit der das `CDatabase`-Objekt mit einer Datenquelle verbunden wird.|
|[CDatabase:: getcurrsorcommitbehavior](#getcursorcommitbehavior)|Gibt die Auswirkung eines Commit für eine Transaktion auf ein offenes Recordset-Objekt an.|
|[CDatabase:: getcurrsorrollbackbehavior](#getcursorrollbackbehavior)|Gibt die Auswirkung eines Rollbacks einer Transaktion auf ein offenes Recordset-Objekt an.|
|[CDatabase:: getDatabaseName](#getdatabasename)|Gibt den Namen der Datenbank, die zurzeit verwendeten zurück.|
|[CDatabase:: IsOpen](#isopen)|Gibt einen Wert ungleich 0 (null) zurück, wenn das `CDatabase` Objekt derzeit mit einer Datenquelle verbunden ist.|
|[CDatabase:: ontoptions](#onsetoptions)|Wird von Framework aufgerufen, um Standard Verbindungsoptionen festzulegen. Die Standard Implementierung legt den Timeout Wert für Abfragen fest. Sie können diese Optionen vorab festlegen, indem Sie `SetQueryTimeout`aufrufen.|
|[CDatabase:: Open](#open)|Stellt eine Verbindung mit einer Datenquelle her (über einen ODBC-Treiber).|
|[CDatabase:: OpenEx](#openex)|Stellt eine Verbindung mit einer Datenquelle her (über einen ODBC-Treiber).|
|[CDatabase:: Rollback](#rollback)|Kehrt Änderungen zurück, die während der aktuellen Transaktion vorgenommen wurden. Die Datenquelle kehrt in ihren vorherigen Zustand zurück, wie im `BeginTrans`-Befehl definiert, nicht geändert.|
|[CDatabase:: setLoginTimeout](#setlogintimeout)|Legt die Anzahl von Sekunden fest, nach denen ein Timeout für eine Datenquellen Verbindung auftritt.|
|[CDatabase:: setQueryTimeout](#setquerytimeout)|Legt die Anzahl von Sekunden fest, nach denen ein Timeout bei Datenbankabfrage Vorgängen auftritt. Wirkt sich auf alle nachfolgenden Recordset-`Open`, `AddNew`-, `Edit`-und `Delete`-Aufrufe aus.|

### <a name="public-data-members"></a>Öffentliche Datenelemente

|Name|Beschreibung|
|----------|-----------------|
|[CDatabase:: M_hdbc](#m_hdbc)|Open Database Connectivity (ODBC)-Verbindungs Handle für eine Datenquelle. Geben Sie *hdbc*ein.|

## <a name="remarks"></a>Hinweise

Eine Datenquelle ist eine bestimmte Instanz von Daten, die von einem Datenbankverwaltungssystem (Database Management System, DBMS) gehostet wird. Beispiele hierfür sind Microsoft SQL Server, Microsoft Access, Borland dBase und xbase. Sie können ein oder mehrere `CDatabase` Objekte gleichzeitig in der Anwendung aktiv haben.

> [!NOTE]
>  Verwenden Sie stattdessen die Klasse [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) , wenn Sie mit den DAO-Klassen (Data Access Objects) anstelle der Open Database Connectivity-Klassen (ODBC) arbeiten. Weitere Informationen finden Sie im Artikel [Übersicht: Datenbankprogrammierung](../../data/data-access-programming-mfc-atl.md).

Um `CDatabase`zu verwenden, erstellen Sie ein `CDatabase` Objekt und nennen seine `OpenEx` Member-Funktion. Dadurch wird eine Verbindung geöffnet. Wenn Sie dann `CRecordset` Objekte erstellen, die für die verbundene Datenquelle ausgeführt werden, übergeben Sie den recordsetkonstruktor einen Zeiger auf das `CDatabase`-Objekt. Wenn Sie die Verbindung nicht mehr verwenden, können Sie die `Close` Member-Funktion aufzurufen und das `CDatabase`-Objekt zerstören. `Close` schließt alle Recordsets, die Sie zuvor noch nicht geschlossen haben.

Weitere Informationen zu `CDatabase`finden Sie in den Artikeln [Datenquelle (ODBC)](../../data/odbc/data-source-odbc.md) und [Übersicht: Datenbankprogrammierung](../../data/data-access-programming-mfc-atl.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CDatabase`

## <a name="requirements"></a>Voraussetzungen

**Header:** AFXDB. h

##  <a name="begintrans"></a>CDatabase:: BeginTrans

Mit dieser Member-Funktion können Sie eine Transaktion mit der verbundenen Datenquelle starten.

```
BOOL BeginTrans();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der-Befehl erfolgreich ausgeführt wurde und Änderungen nur manuell ausgeführt werden. andernfalls 0.

### <a name="remarks"></a>Hinweise

Eine Transaktion besteht aus einem oder mehreren Aufrufen der Funktionen `AddNew`, `Edit`, `Delete`und `Update` Member eines `CRecordset` Objekts. Vor Beginn einer Transaktion muss das `CDatabase` Objekt bereits durch Aufrufen seiner `OpenEx`-oder `Open` Member-Funktion mit der Datenquelle verbunden sein. Um die Transaktion zu beenden, wird [CommitTrans](#committrans) aufgerufen, um alle Änderungen an der Datenquelle zu akzeptieren (und Sie auszuführen) oder [Rollbacks](#rollback) aufzurufen, um die gesamte Transaktion abzubrechen. `BeginTrans` nach dem Öffnen von Recordsets, die an der Transaktion beteiligt sind, und so nah wie möglich an den eigentlichen Aktualisierungs Vorgängen.

> [!CAUTION]
>  Abhängig von Ihrem ODBC-Treiber kann das Öffnen eines Recordsets vor dem Aufrufen von `BeginTrans` Probleme verursachen, wenn `Rollback`aufgerufen wird. Überprüfen Sie den spezifischen Treiber, den Sie verwenden. Wenn Sie z. b. den Microsoft Access-Treiber verwenden, der im Microsoft ODBC Desktop Driver Pack 3,0 enthalten ist, müssen Sie die Anforderung der Jet-Datenbank-Engine berücksichtigen, dass Sie keine Transaktion für eine Datenbank mit einem geöffneten Cursor starten sollten. In den MFC-Datenbankklassen bedeutet ein offener Cursor ein offenes `CRecordset` Objekt. Weitere Informationen finden Sie im [technischen Hinweis 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md).

`BeginTrans` können auch Datensätze auf dem Server sperren, abhängig von der angeforderten Parallelität und den Funktionen der Datenquelle. Informationen zum Sperren von Daten finden Sie im Artikel [Recordset: Sperren von Datensätzen (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).

Benutzerdefinierte Transaktionen werden im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md)erläutert.

`BeginTrans` legt den Status fest, in den die Sequenz der Transaktionen zurückgesetzt werden kann (umgekehrt). Wenn Sie einen neuen Zustand für Rollbacks einrichten möchten, führen Sie einen Commit für eine beliebige aktuelle Transaktion aus, und rufen Sie dann `BeginTrans`

> [!CAUTION]
>  Ein erneuter Aufruf von `BeginTrans`, ohne `CommitTrans` oder `Rollback` aufrufen, ist ein Fehler.

Ruft die [CanTransact](#cantransact) -Member-Funktion auf, um zu bestimmen, ob der Treiber Transaktionen für eine bestimmte Datenbank unterstützt. Sie sollten auch [GetCursorCommitBehavior](#getcursorcommitbehavior) und [GetCursorRollbackBehavior](#getcursorrollbackbehavior) aufrufen, um die Unterstützung für die Cursor Beibehaltung zu ermitteln.

Weitere Informationen zu Transaktionen finden Sie im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Artikel [Transaktion: Ausführen einer Transaktion in einem Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="bindparameters"></a>CDatabase:: BindParameters

Überschreiben Sie `BindParameters`, wenn Sie Parameter vor dem Aufrufen von [CDatabase:: ExecuteSQL](#executesql)binden müssen.

```
virtual void BindParameters(HSTMT hstmt);
```

### <a name="parameters"></a>Parameter

*hstmt*<br/>
Das ODBC-Anweisungs Handle, für das Sie Parameter binden möchten.

### <a name="remarks"></a>Hinweise

Diese Vorgehensweise ist nützlich, wenn Sie das Resultset nicht aus einer gespeicherten Prozedur benötigen.

In ihrer außer Kraft Setzung werden `SQLBindParameters` und verwandte ODBC-Funktionen aufgerufen, um die Parameter zu binden. MFC ruft Ihre außer Kraft Setzung vor dem Aufruf von `ExecuteSQL`auf. Sie müssen `SQLPrepare`nicht aufzurufen. `ExecuteSQL` ruft `SQLExecDirect` auf und zerstört das *hstmt*, das nur einmal verwendet wird.

##  <a name="cancel"></a>CDatabase:: Cancel

Rufen Sie diese Member-Funktion auf, um anzufordern, dass die Datenquelle entweder einen asynchronen Vorgang in Bearbeitung oder einen Prozess von einem zweiten Thread abbrechen soll.

```
void Cancel();
```

### <a name="remarks"></a>Hinweise

Beachten Sie, dass die MFC-ODBC-Klassen die asynchrone Verarbeitung nicht mehr verwenden. zum Ausführen eines asynchronen Vorgangs müssen Sie die ODBC-API-Funktion " [SQLSetConnectOption](/sql/odbc/reference/syntax/sqlsetconnectoption-function)" direkt aufrufen. Weitere Informationen finden Sie unter [asynchrone Ausführung](/sql/odbc/reference/develop-app/asynchronous-execution).

##  <a name="cantransact"></a>CDatabase:: CanTransact

Rufen Sie diese Memberfunktion, um festzustellen, ob der Datenbank Transaktionen zulässig ist.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn Recordsets dieses `CDatabase` Objekt Transaktionen zulassen; andernfalls 0.

### <a name="remarks"></a>Hinweise

Weitere Informationen zu Transaktionen finden Sie im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="canupdate"></a>CDatabase:: CanUpdate

Mit dieser Member-Funktion können Sie ermitteln, ob das `CDatabase` Objekt Updates zulässt.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das `CDatabase` Objekt Updates zulässt. Andernfalls ist der Wert 0 (null), der angibt, dass Sie "true" *nur in Brot* übernommen haben, wenn Sie das `CDatabase` Objekt geöffnet haben oder dass die Datenquelle selbst schreibgeschützt ist Die Datenquelle ist schreibgeschützt, wenn ein Aufrufe der ODBC-API-Funktion `SQLGetInfo` für SQL_DATASOURCE_READ_ONLY "y" zurückgibt.

### <a name="remarks"></a>Hinweise

Updates werden nicht von allen Treibern unterstützt.

##  <a name="cdatabase"></a>CDatabase:: CDatabase

Erstellt ein `CDatabase`-Objekt.

```
CDatabase();
```

### <a name="remarks"></a>Hinweise

Nachdem Sie das-Objekt erstellt haben, müssen Sie dessen `OpenEx` oder `Open` Member-Funktion zum Herstellen einer Verbindung mit einer angegebenen Datenquelle aufruft.

Möglicherweise ist es praktisch, das `CDatabase` Objekt in die Dokument Klasse einzubetten.

### <a name="example"></a>Beispiel

In diesem Beispiel wird die Verwendung von `CDatabase` in einer `CDocument`abgeleiteten Klasse veranschaulicht.

[!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]

[!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]

##  <a name="close"></a>CDatabase:: Close

Wenn Sie die Verbindung mit einer Datenquelle trennen möchten, wird diese Member-Funktion aufgerufen.

```
virtual void Close();
```

### <a name="remarks"></a>Hinweise

Bevor Sie diese Element Funktion aufgerufen haben, müssen Sie alle dem `CDatabase` Objekt zugeordneten Recordsets schließen. Da `Close` das `CDatabase`-Objekt nicht zerstört, können Sie das-Objekt wieder verwenden, indem Sie eine neue Verbindung zur gleichen Datenquelle oder zu einer anderen Datenquelle öffnen.

Alle ausstehenden `AddNew` oder `Edit` Anweisungen von Recordsets, die die Datenbank verwenden, werden abgebrochen, und für alle ausstehenden Transaktionen wird ein Rollback ausgeführt. Alle vom `CDatabase` Objekt abhängigen Recordsets bleiben in einem nicht definierten Zustand.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]

##  <a name="committrans"></a>CDatabase:: CommitTrans

Ruft diese Member-Funktion auf, wenn Transaktionen abgeschlossen werden.

```
BOOL CommitTrans();
```

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn für die Updates erfolgreich ein Commit ausgeführt wurde. andernfalls 0. Wenn `CommitTrans` fehlschlägt, ist der Status der Datenquelle nicht definiert. Sie müssen die Daten überprüfen, um deren Status zu ermitteln.

### <a name="remarks"></a>Hinweise

Eine Transaktion besteht aus einer Reihe von Aufrufen der Funktionen `AddNew`, `Edit`, `Delete`und `Update` Member eines `CRecordset` Objekts, das mit einem Aufruf der [BeginTrans](#begintrans) -Member-Funktion begonnen hat. `CommitTrans` führt einen Commit der Transaktion aus. Standardmäßig wird für Updates sofort ein Commit ausgeführt. das Aufrufen von `BeginTrans` bewirkt, dass die Aktualisierung von Updates verzögert wird, bis `CommitTrans` aufgerufen wird.

Bis Sie `CommitTrans` zum Beenden einer Transaktion aufgerufen haben, können Sie die [Rollback](#rollback) -Member-Funktion aufzurufen, um die Transaktion abzubrechen und die Datenquelle in Ihrem ursprünglichen Zustand zu belassen. Um eine neue Transaktion zu starten, müssen Sie `BeginTrans` erneut aufzurufen.

Weitere Informationen zu Transaktionen finden Sie im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Artikel [Transaktion: Ausführen einer Transaktion in einem Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="executesql"></a>CDatabase:: ExecuteSQL

Wenn Sie einen SQL-Befehl direkt ausführen müssen, nennen Sie diese Member-Funktion.

```
void ExecuteSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Parameter

*lpszSQL*<br/>
Zeiger auf eine Null-terminierte Zeichenfolge, die mit einem gültigen SQL‑Befehl ausgeführt. Sie können eine [CString](../../atl-mfc-shared/reference/cstringt-class.md)übergeben.

### <a name="remarks"></a>Hinweise

Erstellen Sie den Befehl als NULL-terminierte Zeichenfolge. `ExecuteSQL` gibt keine Datensätze zurück. Wenn Sie mit Datensätzen arbeiten möchten, verwenden Sie stattdessen ein Recordset-Objekt.

Die meisten ihrer Befehle für eine Datenquelle werden über Recordset-Objekte ausgegeben, die Befehle zum Auswählen von Daten, Einfügen neuer Datensätze, Löschen von Datensätzen und Bearbeiten von Datensätzen unterstützen. Allerdings werden nicht alle ODBC-Funktionen direkt von den Datenbankklassen unterstützt, sodass Sie manchmal einen direkten SQL-Befehl mit `ExecuteSQL`erstellen müssen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]

##  <a name="getbookmarkpersistence"></a>CDatabase:: getbookmarkpersistenz

Rufen Sie diese Member-Funktion auf, um die Beibehaltung von Lesezeichen auf einem recordset-Objekt nach bestimmten Vorgängen festzulegen.

```
DWORD GetBookmarkPersistence() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Bitmaske, die die Vorgänge identifiziert, mit denen Lesezeichen auf einem recordset-Objekt beibehalten werden. Einzelheiten finden Sie unter "Hinweise".

### <a name="remarks"></a>Hinweise

Wenn Sie beispielsweise `CRecordset::GetBookmark` und dann `CRecordset::Requery` aufrufen, ist das Lesezeichen von `GetBookmark` womöglich nicht mehr gültig. Sie sollten `GetBookmarkPersistence` vor `CRecordset::SetBookmark` aufrufen.

Die folgende Tabelle enthält die Bitmaskenwerten, die für den Rückgabewert von `GetBookmarkPersistence` kombiniert werden können.

|Bitmaskenwert|Lesezeichenbeibehaltung|
|-------------------|--------------------------|
|SQL_BP_CLOSE|Lesezeichen sind nach einem `Requery` Vorgang gültig.|
|SQL_BP_DELETE|Das Lesezeichen für eine Zeile ist nach einem `Delete`-Vorgang in dieser Zeile gültig.|
|SQL_BP_DROP|Lesezeichen sind nach einem `Close` Vorgang gültig.|
|SQL_BP_SCROLL|Lesezeichen sind nach jedem `Move` Vorgang gültig. Damit wird mühelos identifiziert, ob Lesezeichen im Datensatz unterstützt werden, wie von `CRecordset::CanBookmark` zurückgegeben.|
|SQL_BP_TRANSACTION|Lesezeichen sind gültig, nachdem eine Transaktion übernommen oder zurückgesetzt wurde.|
|SQL_BP_UPDATE|Das Lesezeichen für eine Zeile ist nach einem `Update`-Vorgang in dieser Zeile gültig.|
|SQL_BP_OTHER_HSTMT|Lesezeichen, die mit einem recordset-Objekt verbunden sind, sind in einem zweiten Datensatz gültig.|

Weitere Informationen zu diesem Rückgabewert finden Sie in der `SQLGetInfo` der ODBC-API-Funktion im Windows SDK. Weitere Informationen zu Lesezeichen finden Sie im Artikel [Recordset: Lesezeichen und absolute Positionen (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

##  <a name="getconnect"></a>CDatabase:: GetConnect

Rufen Sie diese Memberfunktion auf, um die während des Aufrufs von `OpenEx` oder `Open` verwendete Verbindungszeichenfolge abzurufen, die das `CDatabase`-Objekt mit einer Datenquelle verbunden hat.

```
const CString GetConnect() const;
```

### <a name="return-value"></a>Rückgabewert

Ein **konstanter**[CString](../../atl-mfc-shared/reference/cstringt-class.md) -Wert, der die Verbindungs Zeichenfolge enthält, wenn `OpenEx` oder `Open` aufgerufen wurde. andernfalls eine leere Zeichenfolge.

### <a name="remarks"></a>Hinweise

Eine Beschreibung, wie die Verbindungs Zeichenfolge erstellt wird, finden Sie unter [CDatabase:: Open](#open) .

##  <a name="getcursorcommitbehavior"></a>CDatabase:: getcurrsorcommitbehavior

Diese Member-Funktion wird aufgerufen, um zu bestimmen, wie sich ein [CommitTrans](#committrans) -Vorgang auf Cursor bei geöffneten recordsetobjekten auswirkt.

```
int GetCursorCommitBehavior() const;
```

### <a name="return-value"></a>Rückgabewert

Ein-Wert, der die Auswirkung von Transaktionen auf geöffnete Recordset-Objekte angibt. Einzelheiten finden Sie unter "Hinweise".

### <a name="remarks"></a>Hinweise

In der folgenden Tabelle sind die möglichen Rückgabewerte für `GetCursorCommitBehavior` sowie die entsprechenden Auswirkungen auf das geöffnete Recordset aufgeführt.

|Rückgabewert|Auswirkung auf CRecordset-Objekte|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Ruft `CRecordset::Requery` unmittelbar nach dem Transaktionscommit auf.|
|SQL_CB_DELETE|Ruft `CRecordset::Close` unmittelbar nach dem Transaktionscommit auf.|
|SQL_CB_PRESERVE|Fahren Sie mit `CRecordset` Vorgängen normal fort.|

Weitere Informationen zu diesem Rückgabewert finden Sie in der `SQLGetInfo` der ODBC-API-Funktion im Windows SDK. Weitere Informationen zu Transaktionen finden Sie im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="getcursorrollbackbehavior"></a>CDatabase:: getcurrsorrollbackbehavior

Diese Member-Funktion wird aufgerufen, um zu bestimmen, wie sich ein [Rollback](#rollback) -Vorgang auf Cursor bei geöffneten recordsetobjekten auswirkt.

```
int GetCursorRollbackBehavior() const;
```

### <a name="return-value"></a>Rückgabewert

Ein-Wert, der die Auswirkung von Transaktionen auf geöffnete Recordset-Objekte angibt. Einzelheiten finden Sie unter "Hinweise".

### <a name="remarks"></a>Hinweise

In der folgenden Tabelle sind die möglichen Rückgabewerte für `GetCursorRollbackBehavior` sowie die entsprechenden Auswirkungen auf das geöffnete Recordset aufgeführt.

|Rückgabewert|Auswirkung auf CRecordset-Objekte|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Ruft `CRecordset::Requery` unmittelbar nach dem Transaktionsrollback auf.|
|SQL_CB_DELETE|Ruft `CRecordset::Close` unmittelbar nach dem Transaktionsrollback auf.|
|SQL_CB_PRESERVE|Fahren Sie mit `CRecordset` Vorgängen normal fort.|

Weitere Informationen zu diesem Rückgabewert finden Sie in der `SQLGetInfo` der ODBC-API-Funktion im Windows SDK. Weitere Informationen zu Transaktionen finden Sie im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="getdatabasename"></a>CDatabase:: getDatabaseName

Rufen Sie diese Member-Funktion auf, um den Namen der derzeit verbundenen Datenbank abzurufen (vorausgesetzt, die Datenquelle definiert ein benanntes Objekt mit dem Namen "Database").

```
CString GetDatabaseName() const;
```

### <a name="return-value"></a>Rückgabewert

Eine [CString](../../atl-mfc-shared/reference/cstringt-class.md) , die den Datenbanknamen enthält, wenn erfolgreich. andernfalls eine leere `CString`.

### <a name="remarks"></a>Hinweise

Dies ist nicht identisch mit dem Datenquellen Namen (DSN), der im `OpenEx` oder `Open`-Aufrufens angegeben ist. Welche `GetDatabaseName` zurückgibt, hängt von ODBC ab. Im Allgemeinen handelt es sich bei einer Datenbank um eine Sammlung von Tabellen. Wenn diese Entität einen Namen hat, wird Sie von `GetDatabaseName` zurückgegeben.

Sie könnten z. B. diesen Namen in einer Überschrift anzuzeigen. Wenn beim Abrufen des Namens aus ODBC ein Fehler auftritt, gibt `GetDatabaseName` eine leere `CString`zurück.

##  <a name="isopen"></a>CDatabase:: IsOpen

Mit dieser Member-Funktion können Sie ermitteln, ob das `CDatabase` Objekt derzeit mit einer Datenquelle verbunden ist.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das `CDatabase` Objekt zurzeit verbunden ist. andernfalls 0.

##  <a name="m_hdbc"></a>CDatabase:: M_hdbc

Enthält ein öffentliches Handle für eine ODBC-Datenquellen Verbindung – ein "Verbindungs Handle".

### <a name="remarks"></a>Hinweise

Normalerweise ist es nicht erforderlich, direkt auf diese Element Variable zuzugreifen. Stattdessen ordnet das Framework das Handle zu, wenn Sie `OpenEx` oder `Open`aufgerufen werden. Das Framework hebt die Zuordnung des Handles auf, wenn Sie den **Delete** -Operator für das `CDatabase` Objekt aufzurufen. Beachten Sie, dass die `Close` Member-Funktion das Handle nicht aufhebt.

Unter bestimmten Umständen müssen Sie das Handle jedoch möglicherweise direkt verwenden. Wenn Sie z. b. ODBC-API-Funktionen direkt anstelle von Klassen `CDatabase`aufrufen müssen, benötigen Sie möglicherweise ein Verbindungs Handle, das als Parameter übergeben wird. Weitere Informationen finden Sie im folgenden Codebeispiel.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]

##  <a name="onsetoptions"></a>CDatabase:: ontoptions

Das Framework ruft diese Member-Funktion auf, wenn eine SQL-Anweisung direkt mit der `ExecuteSQL` Member-Funktion ausgeführt wird.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parameter

*hstmt*<br/>
Das ODBC-Anweisungs Handle, für das Optionen festgelegt werden.

### <a name="remarks"></a>Hinweise

`CRecordset::OnSetOptions` ruft auch diese Member-Funktion auf.

`OnSetOptions` legt den Wert für das Anmeldungs Timeout fest. Wenn vorherige Aufrufe der `SetQueryTimeout`-und der Member-Funktion vorhanden waren, werden `OnSetOptions` die aktuellen Werte widergespiegelt. Andernfalls werden Standardwerte festgelegt.

> [!NOTE]
>  Vor MFC 4,2 haben `OnSetOptions` auch den Verarbeitungsmodus entweder auf snychronous oder Asynchronous festgelegt. Ab MFC 4,2 sind alle Vorgänge synchron. Zum Ausführen eines asynchronen Vorgangs müssen Sie einen direkten Rückruf für die ODBC-API-Funktion `SQLSetPos`durchführen.

Sie müssen `OnSetOptions` nicht außer Kraft setzen, um den Timeout Wert zu ändern. Um stattdessen den Timeout Wert für Abfragen anzupassen, müssen Sie `SetQueryTimeout` vor dem Erstellen eines Recordsets abrufen. `OnSetOptions` verwendet den neuen Wert. Die festgelegten Werte gelten für nachfolgende Vorgänge bei allen Recordsets oder bei direkten SQL-aufrufen.

Überschreiben Sie `OnSetOptions`, wenn Sie zusätzliche Optionen festlegen möchten. Ihre außer Kraft Setzung sollte die Basisklasse `OnSetOptions` entweder vor oder nach dem Abrufen der ODBC-API-Funktion `SQLSetStmtOption`aufgerufen werden. Befolgen Sie die-Methode, die in der Standard Implementierung des Frameworks von `OnSetOptions`veranschaulicht wird.

##  <a name="open"></a>CDatabase:: Open

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
Gibt einen Namen für die Datenquelle an – einen Namen, der über das ODBC-Administrator Programm bei ODBC registriert ist. Wenn ein DSN-Wert in *lpszconnect* (in der Form "DSN =\<Data-Source >") angegeben wird, darf er in *lpszdsn*nicht erneut angegeben werden. In diesem Fall sollte *lpszdsn* NULL sein. Andernfalls können Sie NULL übergeben, wenn Sie dem Benutzer ein Dialogfeld für die Datenquelle präsentieren möchten, in dem der Benutzer eine Datenquelle auswählen kann. Weitere Informationen finden Sie unter "Hinweise".

*bExclusive*<br/>
Wird in dieser Version der Klassenbibliothek nicht unterstützt. Derzeit schlägt eine-Übersetzung fehl, wenn dieser Parameter true ist. Die Datenquelle wird immer als freigegeben (nicht exklusiv) geöffnet.

*nur Bread*<br/>
TRUE, wenn die Verbindung schreibgeschützt sein soll und die Aktualisierung der Datenquelle untersagt werden soll. Alle abhängigen Recordsets erben dieses Attribut. Der Standardwert lautet "FALSE".

*lpszconnect*<br/>
Gibt eine Verbindungs Zeichenfolge an. Die Verbindungs Zeichenfolge verkettet Informationen, möglicherweise einschließlich eines Datenquellen namens, eine Benutzer-ID, die für die Datenquelle gültig ist, eine Benutzer-Authentifizierungs Zeichenfolge (Kennwort, wenn die Datenquelle eine solche erfordert) und weitere Informationen. Die gesamte Verbindungs Zeichenfolge muss der Zeichenfolge "ODBC;" vorangestellt sein. (Großbuchstaben oder Kleinbuchstaben). Die Zeichenfolge "ODBC;" wird verwendet, um anzugeben, dass die Verbindung mit einer ODBC-Datenquelle hergestellt wird. Dies dient der aufwärts Kompatibilität, wenn in zukünftigen Versionen der Klassenbibliothek möglicherweise nicht-ODBC-Datenquellen unterstützt werden.

*bUseCursorLib*<br/>
TRUE, wenn die ODBC-Cursor-Bibliotheks-DLL geladen werden soll. Die Cursor Bibliothek maskiert einige Funktionen des zugrunde liegenden ODBC-Treibers und verhindert so die Verwendung von Dynasets (wenn Sie vom Treiber unterstützt werden). Die einzigen unterstützten Cursor, wenn die Cursor Bibliothek geladen wird, sind statische Momentaufnahmen und Vorwärts Cursor. Der Standardwert lautet TRUE. Wenn Sie Vorhaben, ein Recordset-Objekt direkt aus `CRecordset` zu erstellen, ohne davon abzuleiten, sollten Sie die Cursor Bibliothek nicht laden.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Verbindung erfolgreich hergestellt wurde. andernfalls 0, wenn der Benutzer Abbrechen auswählt, wenn ein Dialogfeld angezeigt wird, das weitere Verbindungsinformationen anfordert. In allen anderen Fällen löst das Framework eine Ausnahme aus.

### <a name="remarks"></a>Hinweise

Das Datenbankobjekt muss initialisiert werden, bevor es zum Erstellen eines Recordset-Objekts verwendet werden kann.

> [!NOTE]
>  Das Aufrufen der [OpenEx](#openex) -Member-Funktion ist die bevorzugte Methode zum Herstellen einer Verbindung mit einer Datenquelle und zum Initialisieren des Datenbankobjekts.

Wenn die Parameter in Ihrem `Open`-Befehl nicht genügend Informationen enthalten, um die Verbindung herzustellen, öffnet der ODBC-Treiber ein Dialogfeld, in dem die erforderlichen Informationen vom Benutzer abgerufen werden. Wenn Sie `Open`aufrufen, wird die Verbindungs Zeichenfolge *lpszconnect*privat im `CDatabase` Objekt gespeichert und steht durch Aufrufen der [GetConnect](#getconnect) -Member-Funktion zur Verfügung.

Wenn Sie möchten, können Sie ein eigenes Dialogfeld öffnen, bevor Sie `Open` zum Abrufen von Informationen vom Benutzer abrufen, z. b. ein Kennwort, und diese Informationen dann der Verbindungs Zeichenfolge hinzufügen, die Sie an `Open`übergeben. Möglicherweise möchten Sie auch die Verbindungs Zeichenfolge speichern, die Sie übergeben, damit Sie Sie wieder verwenden können, wenn Ihre Anwendung das nächste Mal `Open` für ein `CDatabase` Objekt aufruft.

Sie können auch die Verbindungs Zeichenfolge für mehrere Ebenen der Anmeldungs Autorisierung (jeweils für ein anderes `CDatabase` Objekt) oder für die Übermittlung anderer Datenquellen spezifischer Informationen verwenden. Weitere Informationen zu Verbindungs Zeichenfolgen finden Sie in Kapitel 5 des Windows SDK.

Es ist möglich, dass ein Verbindungsversuch zu einem Timeout, wenn Sie z. B. der DBMS-Host nicht verfügbar ist. Wenn der Verbindungsversuch fehlschlägt, löst `Open` eine `CDBException`aus.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]

##  <a name="openex"></a>CDatabase:: OpenEx

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

- `CDatabase::openExclusive` in dieser Version der Klassenbibliothek nicht unterstützt. Eine Datenquelle wird immer als freigegeben (nicht exklusiv) geöffnet. Derzeit schlägt eine-Übersetzung fehl, wenn Sie diese Option angeben.

- `CDatabase::openReadOnly` die Datenquelle als schreibgeschützt zu öffnen.

- `CDatabase::useCursorLib` Laden der ODBC-Cursor Bibliotheks-DLL. Die Cursor Bibliothek maskiert einige Funktionen des zugrunde liegenden ODBC-Treibers und verhindert so die Verwendung von Dynasets (wenn Sie vom Treiber unterstützt werden). Die einzigen unterstützten Cursor, wenn die Cursor Bibliothek geladen wird, sind statische Momentaufnahmen und Vorwärts Cursor. Wenn Sie Vorhaben, ein Recordset-Objekt direkt aus `CRecordset` zu erstellen, ohne davon abzuleiten, sollten Sie die Cursor Bibliothek nicht laden.

- `CDatabase::noOdbcDialog` das Dialogfeld ODBC-Verbindung nicht anzeigen, unabhängig davon, ob genügend Verbindungsinformationen bereitgestellt werden.

- `CDatabase::forceOdbcDialog` immer das Dialogfeld ODBC-Verbindung anzeigen.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Verbindung erfolgreich hergestellt wurde. andernfalls 0, wenn der Benutzer Abbrechen auswählt, wenn ein Dialogfeld angezeigt wird, das weitere Verbindungsinformationen anfordert. In allen anderen Fällen löst das Framework eine Ausnahme aus.

### <a name="remarks"></a>Hinweise

Das Datenbankobjekt muss initialisiert werden, bevor es zum Erstellen eines Recordset-Objekts verwendet werden kann.

Wenn der *lpszconnectstring* -Parameter in Ihrem `OpenEx`-Befehl nicht genügend Informationen enthält, um die Verbindung herzustellen, öffnet der ODBC-Treiber ein Dialogfeld, in dem die erforderlichen Informationen vom Benutzer abgerufen werden, sofern Sie im *dwOptions* -Parameter nicht `CDatabase::noOdbcDialog` oder `CDatabase::forceOdbcDialog` festgelegt haben. Wenn Sie `OpenEx`aufrufen, wird die Verbindungs Zeichenfolge *lpszconnectstring*privat im `CDatabase` Objekt gespeichert und steht durch Aufrufen der [GetConnect](#getconnect) -Member-Funktion zur Verfügung.

Wenn Sie möchten, können Sie ein eigenes Dialogfeld öffnen, bevor Sie `OpenEx` zum Abrufen von Informationen vom Benutzer (z. b. ein Kennwort) öffnen und diese Informationen dann der Verbindungs Zeichenfolge hinzufügen, die Sie an `OpenEx`übergeben. Möglicherweise möchten Sie auch die Verbindungs Zeichenfolge speichern, die Sie übergeben, damit Sie Sie wieder verwenden können, wenn Ihre Anwendung das nächste Mal `OpenEx` für ein `CDatabase` Objekt aufruft.

Sie können auch die Verbindungs Zeichenfolge für mehrere Ebenen der Anmeldungs Autorisierung (jeweils für ein anderes `CDatabase` Objekt) oder für die Übermittlung anderer Datenquellen spezifischer Informationen verwenden. Weitere Informationen zu Verbindungs Zeichenfolgen finden Sie in Kapitel 6 in der *ODBC Programmer es Reference*.

Es ist möglich, dass ein Verbindungsversuch zu einem Timeout, wenn Sie z. B. der DBMS-Host nicht verfügbar ist. Wenn der Verbindungsversuch fehlschlägt, löst `OpenEx` eine `CDBException`aus.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]

##  <a name="rollback"></a>CDatabase:: Rollback

Mit dieser Member-Funktion können Sie die während einer Transaktion vorgenommenen Änderungen umkehren.

```
BOOL Rollback();
```

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn die Transaktion erfolgreich rückgängig gemacht wurde. andernfalls 0. Wenn ein `Rollback`-Aufrufe fehlschlägt, sind die Datenquelle und die Transaktions Zustände nicht definiert. Wenn `Rollback` 0 zurückgibt, müssen Sie die Datenquelle überprüfen, um deren Status zu ermitteln.

### <a name="remarks"></a>Hinweise

Alle `CRecordset` `AddNew`, `Edit`, `Delete`und `Update` Aufrufe, die seit dem letzten [BeginTrans](#begintrans) ausgeführt wurden, werden auf den Zustand zurückgesetzt, der zum Zeitpunkt des Aufrufs vorhanden war.

Nach einem `Rollback`-Aufrufe erfolgt die Transaktion, und Sie müssen `BeginTrans` für eine andere Transaktion erneut abrufen. Der Datensatz, der vor dem Aufrufen von `BeginTrans` aktuell ist, wird nach `Rollback`erneut zum aktuellen Datensatz.

Nach einem Rollback bleibt der Datensatz, der vor dem Rollback aktuell war, aktuell. Ausführliche Informationen zum Status des Recordsets und der Datenquelle nach einem Rollback finden Sie im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Artikel [Transaktion: Ausführen einer Transaktion in einem Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="setlogintimeout"></a>CDatabase:: setLoginTimeout

Diese Member-Funktion – vor dem Ausführen von `OpenEx` oder `Open` – zum Überschreiben der zulässigen Standard Anzahl von Sekunden vor dem Timeout einer versuchten Datenquellen Verbindung.

```
void SetLoginTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Parameter

*dwseconds*<br/>
Die Anzahl der Sekunden, die vor dem Timeout eines Verbindungsversuchs zugelassen werden.

### <a name="remarks"></a>Hinweise

Bei einem Verbindungsversuch tritt möglicherweise ein Timeout auf, wenn das DBMS beispielsweise nicht verfügbar ist. Ruft `SetLoginTimeout` auf, nachdem Sie das nicht initialisierte `CDatabase`-Objekt erstellt haben, aber bevor Sie `OpenEx` oder `Open`aufgerufen haben.

Der Standardwert für Anmeldungs Timeouts beträgt 15 Sekunden. Nicht alle Datenquellen unterstützen die Möglichkeit, einen Anmeldungs Timeout Wert anzugeben. Wenn die Datenquelle kein Timeout unterstützt, erhalten Sie eine Ausgabe der Ablauf Verfolgung, aber keine Ausnahme. Der Wert 0 bedeutet "unendlich".

##  <a name="setquerytimeout"></a>CDatabase:: setQueryTimeout

Diese Member-Funktion wird aufgerufen, um die Standard Anzahl von Sekunden zu überschreiben, die vor nachfolgenden Vorgängen für die verbundene Datenquelle zugelassen werden.

```
void SetQueryTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Parameter

*dwseconds*<br/>
Die Anzahl der Sekunden, bevor der abfrageversuch einer ist ein Timeout aufgetreten.

### <a name="remarks"></a>Hinweise

Ein Vorgang kann aufgrund von Netzwerkproblemen für den Zugriff, übermäßige Abfrage Verarbeitungszeit und usw. Timeout. Rufen Sie `SetQueryTimeout` vor dem Öffnen des Recordsets oder vor dem Aufrufen der `AddNew`des Recordsets auf, `Update` oder `Delete` Element Funktionen, wenn Sie den Wert für das Abfrage Timeout ändern möchten. Die-Einstellung wirkt sich auf alle nachfolgenden `Open`-, `AddNew`-, `Update`-und `Delete` Aufrufe von Recordsets aus, die diesem `CDatabase` Objekt zugeordnet sind. Ändern den Timeoutwert für Abfragen für ein Recordset nach Öffnen ändert sich nicht auf den Wert für das Recordset aus. Beispielsweise verwenden nachfolgende `Move` Vorgänge nicht den neuen Wert.

Der Standardwert für Abfrage Timeouts beträgt 15 Sekunden. Nicht alle Datenquellen unterstützen die Möglichkeit, einen Abfrage Timeout Wert festzulegen. Wenn Sie einen Abfrage Timeout Wert von 0 (null) festlegen, tritt kein Timeout auf. die Kommunikation mit der Datenquelle reagiert möglicherweise nicht mehr. Dieses Verhalten kann während der Entwicklung nützlich sein. Wenn die Datenquelle kein Timeout unterstützt, erhalten Sie eine Ausgabe der Ablauf Verfolgung, aber keine Ausnahme.

## <a name="see-also"></a>Siehe auch

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CRecordset-Klasse](../../mfc/reference/crecordset-class.md)
