---
title: CDBException-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDBException
- AFXDB/CDBException
- AFXDB/CDBException::m_nRetCode
- AFXDB/CDBException::m_strError
- AFXDB/CDBException::m_strStateNativeOrigin
helpviewer_keywords:
- CDBException [MFC], m_nRetCode
- CDBException [MFC], m_strError
- CDBException [MFC], m_strStateNativeOrigin
ms.assetid: eb9e1119-89f5-49a7-b9d4-b91cee1ccc82
ms.openlocfilehash: 1ab7daeb3af55c92985c951c632b1d4050681474
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321892"
---
# <a name="cdbexception-class"></a>CDBException-Klasse

Stellt eine Ausnahmebedingung dar, die von Datenbankklassen ausgelöst wird.

## <a name="syntax"></a>Syntax

```
class CDBException : public CException
```

## <a name="members"></a>Member

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDBAusnahme::m_nRetCode](#m_nretcode)|Enthält einen ODBC-Rückgabecode (Open Database Connectivity) vom Typ RETCODE.|
|[CDBAusnahme::m_strError](#m_strerror)|Enthält eine Zeichenfolge, die den Fehler in alphanumerischen Begriffen beschreibt.|
|[CDBAusnahme::m_strStateNativeOrigin](#m_strstatenativeorigin)|Enthält eine Zeichenfolge, die den Fehler in Bezug auf die von ODBC zurückgegebenen Fehlercodes beschreibt.|

## <a name="remarks"></a>Bemerkungen

Die Klasse enthält zwei öffentliche Datenmember, mit denen Sie die Ursache der Ausnahme ermitteln oder eine Textnachricht anzeigen können, die die Ausnahme beschreibt. `CDBException`Objekte werden von Memberfunktionen der Datenbankklassen erstellt und ausgelöst.

> [!NOTE]
> Diese Klasse ist eine der ODBC-Klassen (Open Database Connectivity) von MFC. Wenn Sie stattdessen die neueren DAO-Klassen (Data Access Objects) verwenden, verwenden Sie stattdessen [CDaoException.](../../mfc/reference/cdaoexception-class.md) Alle DAO-Klassennamen haben "CDao" als Präfix. Weitere Informationen finden Sie im Artikel [Übersicht: Datenbankprogrammierung](../../data/data-access-programming-mfc-atl.md).

Ausnahmen sind Fälle ungewöhnlicher Ausführung mit Bedingungen, die außerhalb der Kontrolle des Programms liegen, z. B. Datenquellen- oder Netzwerk-E/A-Fehler. Fehler, die sie im normalen Verlauf der Ausführung des Programms erwarten, werden in der Regel nicht als Ausnahmen betrachtet.

Sie können im Rahmen eines **CATCH-Ausdrucks** auf diese Objekte zugreifen. Sie können `CDBException` auch Objekte aus Ihrem `AfxThrowDBException` eigenen Code mit der globalen Funktion auslösen.

Weitere Informationen zur Ausnahmebehandlung im `CDBException` Allgemeinen oder zu Objekten finden Sie in den Artikeln [Exception Handling (MFC)](../../mfc/exception-handling-in-mfc.md) und [Exceptions: Database Exceptions](../../mfc/exceptions-database-exceptions.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDBException`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdb.h

## <a name="cdbexceptionm_nretcode"></a><a name="m_nretcode"></a>CDBAusnahme::m_nRetCode

Enthält einen ODBC-Fehlercode vom Typ RETCODE, der von einer API-Funktion (ODBC Application Programming Interface) zurückgegeben wird.

### <a name="remarks"></a>Bemerkungen

Dieser Typ enthält SQL-Präfixiertcodes, die von ODBC definiert werden, und AFX_SQL-Vor-Präfixcodes, die von den Datenbankklassen definiert werden. Für `CDBException`eine enthält dieser Member einen der folgenden Werte:

- AFX_SQL_ERROR_API_CONFORMANCE Der Treiber `CDatabase::OpenEx` `CDatabase::Open` für einen oder einen Aufruf entspricht nicht den erforderlichen ODBC-API-Konformitätsstufen 1 ( SQL_OAC_LEVEL1).

- AFX_SQL_ERROR_CONNECT_FAIL Verbindung mit der Datenquelle ist fehlgeschlagen. Sie haben`CDatabase` einen NULL-Zeiger an den Recordsetkonstruktor übergeben, `GetDefaultConnect` und der anschließende Versuch, eine Verbindung basierend auf dem Fehler zu erstellen, haben übergeben.

- AFX_SQL_ERROR_DATA_TRUNCATED Sie haben mehr Daten angefordert, als Sie gespeichert haben. Informationen zum Erhöhen der bereitgestellten `CByteArray` Datenspeicherung für `nMaxLength` `CString` oder datentypen finden Sie im Argument für [RFX_Text](record-field-exchange-functions.md#rfx_text) und [RFX_Binary](record-field-exchange-functions.md#rfx_binary) unter "Makros und Globale".

- AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED Ein `CRecordset::Open` Aufruf zum Anfordern eines Dynasets ist fehlgeschlagen. Dynasets werden vom Treiber nicht unterstützt.

- AFX_SQL_ERROR_EMPTY_COLUMN_LIST Sie versucht haben, eine Tabelle zu öffnen (oder was Sie gegeben haben, konnte nicht als Prozeduraufruf oder **SELECT-Anweisung** identifiziert werden), aber es sind keine Spalten in RFX-Funktionsaufrufen (Record Field Exchange) in Ihrer `DoFieldExchange` Außerkraftsetzung identifiziert.

- AFX_SQL_ERROR_FIELD_SCHEMA_MISMATCH Der Typ einer RFX-Funktion in Ihrer `DoFieldExchange` Außerkraftsetzung ist nicht mit dem Spaltendatentyp im Recordset kompatibel.

- AFX_SQL_ERROR_ILLEGAL_MODE Sie `CRecordset::Update` angerufen `CRecordset::AddNew` haben, ohne vorher anzurufen oder `CRecordset::Edit`.

- AFX_SQL_ERROR_LOCK_MODE_NOT_SUPPORTED Ihre Anforderung, Datensätze für die Aktualisierung zu sperren, konnte nicht erfüllt werden, da Ihr ODBC-Treiber das Sperren nicht unterstützt.

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED Sie `CRecordset::Update` `Delete` eine Tabelle ohne eindeutigen Schlüssel aufgerufen und mehrere Datensätze geändert haben.

- AFX_SQL_ERROR_NO_CURRENT_RECORD Sie haben versucht, einen zuvor gelöschten Datensatz zu bearbeiten oder zu löschen. Sie müssen nach dem Löschen zu einem neuen aktuellen Datensatz scrollen.

- AFX_SQL_ERROR_NO_POSITIONED_UPDATES Ihre Anforderung für ein Dynaset konnte nicht erfüllt werden, da Ihr ODBC-Treiber keine positionierten Updates unterstützt.

- AFX_SQL_ERROR_NO_ROWS_AFFECTED Sie `CRecordset::Update` `Delete`aufgerufen haben oder , aber als der Vorgang begann, konnte der Datensatz nicht mehr gefunden werden.

- AFX_SQL_ERROR_ODBC_LOAD_FAILED Ein Versuch, den ODBC zu laden. DLL fehlgeschlagen; Windows konnte diese DLL nicht finden oder nicht laden. Dieser Fehler ist schwerwiegend.

- AFX_SQL_ERROR_ODBC_V2_REQUIRED Ihre Anforderung für ein Dynaset konnte nicht erfüllt werden, da ein ODBC-Treiber der Stufe 2 erforderlich ist.

- AFX_SQL_ERROR_RECORDSET_FORWARD_ONLY Ein Bildlaufversuch war nicht erfolgreich, da die Datenquelle kein Rückwärts-Scrollen unterstützt.

- AFX_SQL_ERROR_SNAPSHOT_NOT_SUPPORTED Ein `CRecordset::Open` Aufruf zum Anfordern eines Snapshots ist fehlgeschlagen. Snapshots werden vom Treiber nicht unterstützt. (Dies sollte nur auftreten, wenn die ODBC-Cursorbibliothek ODBCCURS. DLL ist nicht vorhanden.)

- AFX_SQL_ERROR_SQL_CONFORMANCE Der Treiber `CDatabase::OpenEx` `CDatabase::Open` für einen oder einen Aufruf entspricht nicht der erforderlichen ODBC SQL-Konformitätsstufe von "Minimum" (SQL_OSC_MINIMUM).

- AFX_SQL_ERROR_SQL_NO_TOTAL Der ODBC-Treiber konnte die Gesamtgröße eines `CLongBinary` Datenwerts nicht angeben. Der Vorgang ist wahrscheinlich fehlgeschlagen, da ein globaler Speicherblock nicht vorab zugeordnet werden konnte.

- AFX_SQL_ERROR_RECORDSET_READONLY Sie haben versucht, ein schreibgeschütztes Recordset zu aktualisieren, oder die Datenquelle ist schreibgeschützt. Mit dem Recordset oder dem `CDatabase` Objekt, dem es zugeordnet ist, können keine Aktualisierungsvorgänge ausgeführt werden.

- SQL_ERROR Funktion ist fehlgeschlagen. Die von der ODBC-Funktion `SQLError` zurückgegebene `m_strError` Fehlermeldung wird im Datenmember gespeichert.

- SQL_INVALID_HANDLE Function ist aufgrund eines ungültigen Umgebungshandles, Verbindungshandles oder Anweisungshandles fehlgeschlagen. Dies weist auf einen Programmierfehler hin. Über die ODBC-Funktion `SQLError`sind keine zusätzlichen Informationen verfügbar.

Die SQL-Präfixiertcodes werden von ODBC definiert. Die AFX-Vordefinierten Codes werden in AFXDB definiert. H, gefunden in MFC-INCLUDE.

## <a name="cdbexceptionm_strerror"></a><a name="m_strerror"></a>CDBAusnahme::m_strError

Enthält eine Zeichenfolge, die den Fehler beschreibt, der die Ausnahme verursacht hat.

### <a name="remarks"></a>Bemerkungen

Die Zeichenfolge beschreibt den Fehler in alphanumerischen Begriffen. Ausführlichere Informationen und ein `m_strStateNativeOrigin`Beispiel finden Sie unter .

## <a name="cdbexceptionm_strstatenativeorigin"></a><a name="m_strstatenativeorigin"></a>CDBAusnahme::m_strStateNativeOrigin

Enthält eine Zeichenfolge, die den Fehler beschreibt, der die Ausnahme verursacht hat.

### <a name="remarks"></a>Bemerkungen

Die Zeichenfolge hat die Form "State:%s,Native:%ld,Origin:%s", wobei die Formatcodes in der Reihenfolge durch Werte ersetzt werden, die beschreiben:

- Die SQLSTATE, eine null-terminierte Zeichenfolge, die einen fünfstelligen Fehlercode enthält, `SQLError`der im *szSqlState-Parameter* der ODBC-Funktion zurückgegeben wird. SQLSTATE-Werte sind in Anhang A, [ODBC-Fehlercodes](/sql/odbc/reference/appendixes/appendix-a-odbc-error-codes), in der *ODBC-Programmiererreferenz*aufgeführt. Beispiel: "S0022".

- Der systemeigene Fehlercode, der für die Datenquelle spezifisch ist, wird im *Parameter pfNativeError* der `SQLError` Funktion zurückgegeben. Beispiel: 207.

- Der Im *SzErrorMsg-Parameter* der `SQLError` Funktion zurückgegebene Fehlermeldungstext. Diese Meldung besteht aus mehreren in Klammern gesetzten Namen. Wenn ein Fehler von der Quelle an den Benutzer übergeben wird, fügt jede ODBC-Komponente (Datenquelle, Treiber, Treiber-Manager) ihren eigenen Namen an. Diese Informationen helfen, den Ursprung des Fehlers zu ermitteln. Beispiel: [Microsoft][ODBC SQL Server Driver][SQL Server]

Das Framework interpretiert die Fehlerzeichenfolge und `m_strStateNativeOrigin`fügt ihre Komponenten in ; Wenn `m_strStateNativeOrigin` Informationen für mehr als einen Fehler enthalten, werden die Fehler durch Zeilenlinien getrennt. Das Framework fügt den alphanumerischen Fehlertext in `m_strError`ein.

Weitere Informationen zu den Codes, aus denen diese Zeichenfolge besteht, finden Sie in der [SQLError-Funktion](/sql/odbc/reference/syntax/sqlerror-function) in der *ODBC-Programmiererreferenz*.

### <a name="example"></a>Beispiel

Aus ODBC:\["State:S0022,Native:207,Origin:\[Microsoft] ODBC\[SQL Server Driver] SQL Server] Ungültiger Spaltenname 'ColName'"

In `m_strStateNativeOrigin`: "State:S0022,Native:207,Origin:\[Microsoft]\[ODBC SQL Server Driver]\[SQL Server]"

In `m_strError`: "Ungültiger Spaltenname 'ColName'"

## <a name="see-also"></a>Siehe auch

[CException-Klasse](../../mfc/reference/cexception-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDatabase-Klasse](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset-Klasse](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange-Klasse](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::Update](../../mfc/reference/crecordset-class.md#update)<br/>
[CRecordset::Delete](../../mfc/reference/crecordset-class.md#delete)<br/>
[CException-Klasse](../../mfc/reference/cexception-class.md)
