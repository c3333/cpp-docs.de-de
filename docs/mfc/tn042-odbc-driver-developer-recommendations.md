---
title: 'TN042: Empfehlungen für ODBC-Treiberentwickler'
ms.date: 11/04/2016
f1_keywords:
- vc.odbc
helpviewer_keywords:
- ODBC drivers [MFC], writing
- databases [MFC], ODBC
- TN042
ms.assetid: ecc6b5d9-f480-4582-9e22-8309fe561dad
ms.openlocfilehash: 67f7a86a247b60be66dabb0a89f04d39ce76222b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372139"
---
# <a name="tn042-odbc-driver-developer-recommendations"></a>TN042: Empfehlungen für ODBC-Treiberentwickler

> [!NOTE]
> Der folgende technische Hinweis wurde seit dem ersten Erscheinen in der Onlinedokumentation nicht aktualisiert. Daher können einige Verfahren und Themen veraltet oder falsch sein. Um aktuelle Informationen zu erhalten, wird empfohlen, das gewünschte Thema im Index der Onlinedokumentation zu suchen.

Dieser Hinweis beschreibt Richtlinien für ODBC-Treiberschreiber. Es beschreibt allgemeine Anforderungen und Annahmen der ODBC-Funktionalität, die die MFC-Datenbankklassen machen, und verschiedene erwartete semantische Details. Erforderliche Treiberfunktionalität zur `CRecordset` Unterstützung der drei Open-Modi (**forwardOnly**, **Snapshot** und **Dynaset**) werden beschrieben.

## <a name="odbcs-cursor-library"></a>OdBC-Cursorbibliothek

Die MFC-Datenbankklassen bieten dem Benutzer Funktionen, die in vielen Fällen die Funktionalität der meisten ODBC-Treiber der Ebene 1 übertreffen. Glücklicherweise wird die Cursorbibliothek von ODBC sich zwischen den Datenbankklassen und dem Treiber überlagern und automatisch einen Großteil dieser zusätzlichen Funktionen bereitstellen.

Beispielsweise unterstützen die meisten 1.0-Treiber kein Rückwärts-Scrollen. Die Cursorbibliothek kann dies erkennen und Zeilen aus dem Treiber zwischenspeichern und sie wie bei FETCH_PREV Aufrufen in `SQLExtendedFetch`präsentieren.

Ein weiteres wichtiges Beispiel für die Abhängigkeit von Cursorbibliotheken sind positionierte Aktualisierungen. Die meisten 1.0-Treiber verfügen auch nicht über positionierte Aktualisierungen, aber die Cursorbibliothek generiert Aktualisierungsanweisungen, die eine Zielzeile in der Datenquelle basierend auf ihren aktuellen zwischengespeicherten Datenwerten oder einem zwischengespeicherten Zeitstempelwert identifizieren.

Die Klassenbibliothek verwendet nie mehrere Rowsets. Daher werden `SQLSetPos` die wenigen Anweisungen immer auf Zeile 1 des Rowsets angewendet.

## <a name="cdatabases"></a>CDatabases

Jeder `CDatabase` weist eine einzelne **HDBC**zu. (Wenn `CDatabase`die `ExecuteSQL` Funktion 's verwendet wird, wird vorübergehend ein **HSTMT** zugewiesen.) Wenn also `CDatabase`mehrere 's erforderlich sind, müssen mehrere **HDBC**s pro **HENV** unterstützt werden.

Die Datenbankklassen erfordern die Cursorbibliothek. Dies spiegelt `SQLSetConnections` sich in einem Aufruf **SQL_ODBC_CURSORS wider,** **SQL_CUR_USE_ODBC**.

`SQLDriverConnect`**, SQL_DRIVER_COMPLETE** verwendet `CDatabase::Open` wird, um die Verbindung zur Datenquelle herzustellen.

Der Treiber `SQLGetInfo SQL_ODBC_API_CONFORMANCE`  >= muss `SQLGetInfo SQL_ODBC_SQL_CONFORMANCE`  >=  **SQL_OAC_LEVEL1**, **SQL_OSC_MINIMUM**unterstützen.

Damit Transaktionen `CDatabase` für die und ihre abhängigen Recordsets unterstützt werden, `SQLGetInfo SQL_CURSOR_COMMIT_BEHAVIOR` müssen **SQL_CURSOR_ROLLBACK_BEHAVIOR** **SQL_CR_PRESERVE**haben. Andernfalls werden Versuche, die Transaktionssteuerung auszuführen, ignoriert.

`SQLGetInfo SQL_DATA_SOURCE_READ_ONLY`muss unterstützt werden. Wenn "Y" zurückgegeben wird, werden keine Aktualisierungsvorgänge für die Datenquelle ausgeführt.

Wenn `CDatabase` der ReadOnly geöffnet wird, wird versucht, die Datenquelle `SQLSetConnectOption SQL_ACCESS_MODE`schreibgeschützt festzulegen, mit , **SQL_MODE_READ_ONLY**.

Wenn Bezeichner ein Anschreiben erfordern, sollten diese `SQLGetInfo SQL_IDENTIFIER_QUOTE_CHAR` Informationen vom Treiber mit einem Anruf zurückgegeben werden.

Zu Debugzwecken `SQLGetInfo SQL_DBMS_VER` werden **SQL_DBMS_NAME** vom Treiber abgerufen.

`SQLSetStmtOption SQL_QUERY_TIMEOUT`und **SQL_ASYNC_ENABLE** kann auf `CDatabase`einem 's **HDBC**aufgerufen werden.

`SQLError`kann mit einem oder allen Argumenten NULL aufgerufen werden.

Natürlich , `SQLAllocEnv` `SQLAllocConnect` `SQLDisconnect` und `SQLFreeConnect` muss unterstützt werden.

## <a name="executesql"></a>ExecuteSQL

Zusätzlich zum Zuweisen und Befreien einer temporären `SQLExecDirect` `SQLFetch` **HSTMT** `ExecuteSQL` , ruft , , `SQLNumResultCol` und `SQLMoreResults`. `SQLCancel`kann auf dem **HSTMT**aufgerufen werden.

## <a name="getdatabasename"></a>GetDatabaseName

`SQLGetInfo SQL_DATABASE_NAME`aufgerufen werden.

## <a name="begintrans-committrans-rollback"></a>BeginTrans, CommitTrans, Rollback

`SQLSetConnectOption SQL_AUTOCOMMIT`und `SQLTransact SQL_COMMIT`, **SQL_ROLLBACK** und **SQL_AUTOCOMMIT** werden aufgerufen, wenn Transaktionsanforderungen gestellt werden.

## <a name="crecordsets"></a>CRecordsets

`SQLAllocStmt`, `SQLPrepare` `SQLExecute` (Für `Open` `Requery`und `SQLExecDirect` ) (für `SQLFreeStmt` Aktualisierungsvorgänge) muss unterstützt werden. `SQLNumResultCols`und `SQLDescribeCol` werden zu verschiedenen Zeiten auf die ergebnisse abgerufen.

`SQLSetParam`wird ausgiebig zum Binden von Parameterdaten und **DATA_AT_EXEC** Verwendet.

`SQLBindCol`wird ausgiebig verwendet, um Ausgabespalten-Datenspeicherstandorte bei ODBC zu registrieren.

Zwei `SQLGetData` Aufrufe werden verwendet, um **SQL_LONG_VARCHAR-** und **SQL_LONG_VARBINARY** Daten abzurufen. Beim ersten Aufruf wird versucht, die Gesamtlänge `SQLGetData` des Spaltenwerts zu ermitteln, indem mit cbMaxValue von 0, aber mit einem gültigen pcbValue aufgerufen wird. Wenn pcbValue **SQL_NO_TOTAL**enthält, wird eine Ausnahme ausgelöst. Andernfalls wird ein **HGLOBAL** zugewiesen `SQLGetData` und ein weiterer Aufruf zum Abrufen des gesamten Ergebnisses durchgeführt.

## <a name="updating"></a>Wird aktualisiert

Wenn eine pessimistische `SQLGetInfo SQL_LOCK_TYPES` Sperrung beantragt wird, wird abgefragt. Wenn **SQL_LCK_EXCLUSIVE** nicht unterstützt wird, wird eine Ausnahme ausgelöst.

Versuche, einen `CRecordset` (**Snapshot** oder **Dynaset**) zu aktualisieren, führen dazu, dass eine zweite **HSTMT** zugewiesen wird. Für Treiber, die das zweite **HSTMT**nicht unterstützen, simuliert die Cursorbibliothek diese Funktionalität. Leider kann dies manchmal bedeuten, dass die aktuelle Abfrage auf dem ersten **HSTMT** abgeschlossen wird, bevor die zweite **HSTMT-Anforderung**verarbeitet wird.

`SQLFreeStmt SQL_CLOSE`und **SQL_RESET_PARAMS** SQL_RESET_PARAMS `SQLGetCursorName` und werden während des Aktualisierungsbetriebs aufgerufen.

Wenn **cLongBinarys** in den **outputColumns**vorhanden sind, müssen **die DATA_AT_EXEC-Funktionalität** von ODBC unterstützt werden. Dazu gehört auch `SQLExecDirect` `SQLParamData` die `SQLPutData`Rückgabe **SQL_NEED_DATA** von und .

`SQLRowCount`wird nach der Ausführung aufgerufen, um zu `SQLExecDirect`überprüfen, ob nur 1 Datensatz von der aktualisiert wurde.

## <a name="forwardonly-cursors"></a>ForwardOnly Cursors

Nur `SQLFetch` für die `Move` Vorgänge ist erforderlich. Beachten Sie, dass **forwardOnly-Cursor** keine Updates unterstützen.

## <a name="snapshot-cursors"></a>Snapshot-Cursor

Die Snapshot-Funktionalität erfordert `SQLExtendedFetch` Unterstützung. Wie oben erwähnt, erkennt die ODBC-Cursorbibliothek, `SQLExtendedFetch`wenn ein Treiber nicht unterstützt, und stellt die erforderliche Unterstützung selbst bereit.

`SQLGetInfo`**müssen SQL_SCROLL_OPTIONS** **SQL_SO_STATIC**unterstützen.

## <a name="dynaset-cursors"></a>Dynaset-Cursor

Im Folgenden finden Sie die minimale Unterstützung, die zum Öffnen eines Dynasets erforderlich ist:

`SQLGetInfo`**müssen SQL_ODBC_VER** > "01" zurückgeben.

`SQLGetInfo`**müssen SQL_SCROLL_OPTIONS** **SQL_SO_KEYSET_DRIVEN**unterstützen.

`SQLGetInfo`**müssen SQL_ROW_UPDATES** "Y" zurückgeben.

`SQLGetInfo`**müssen SQL_POSITIONED_UPDATES** **SQL_PS_POSITIONED_DELETE** und **SQL_PS_POSITIONED_UPDATE**unterstützen.

Wenn pessimistischesperren angefordert werden, wird `SQLSetPos` außerdem ein Aufruf an irow 1, fRefresh FALSE und fLock **SQL_LCK_EXCLUSIVE** durchgeführt.

## <a name="see-also"></a>Siehe auch

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)
