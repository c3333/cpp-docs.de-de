---
title: CRecordset-Klasse
ms.date: 11/04/2016
f1_keywords:
- CRecordset
- AFXDB/CRecordset
- AFXDB/CRecordset::CRecordset
- AFXDB/CRecordset::AddNew
- AFXDB/CRecordset::CanAppend
- AFXDB/CRecordset::CanBookmark
- AFXDB/CRecordset::Cancel
- AFXDB/CRecordset::CancelUpdate
- AFXDB/CRecordset::CanRestart
- AFXDB/CRecordset::CanScroll
- AFXDB/CRecordset::CanTransact
- AFXDB/CRecordset::CanUpdate
- AFXDB/CRecordset::CheckRowsetError
- AFXDB/CRecordset::Close
- AFXDB/CRecordset::Delete
- AFXDB/CRecordset::DoBulkFieldExchange
- AFXDB/CRecordset::DoFieldExchange
- AFXDB/CRecordset::Edit
- AFXDB/CRecordset::FlushResultSet
- AFXDB/CRecordset::GetBookmark
- AFXDB/CRecordset::GetDefaultConnect
- AFXDB/CRecordset::GetDefaultSQL
- AFXDB/CRecordset::GetFieldValue
- AFXDB/CRecordset::GetODBCFieldCount
- AFXDB/CRecordset::GetODBCFieldInfo
- AFXDB/CRecordset::GetRecordCount
- AFXDB/CRecordset::GetRowsetSize
- AFXDB/CRecordset::GetRowsFetched
- AFXDB/CRecordset::GetRowStatus
- AFXDB/CRecordset::GetSQL
- AFXDB/CRecordset::GetStatus
- AFXDB/CRecordset::GetTableName
- AFXDB/CRecordset::IsBOF
- AFXDB/CRecordset::IsDeleted
- AFXDB/CRecordset::IsEOF
- AFXDB/CRecordset::IsFieldDirty
- AFXDB/CRecordset::IsFieldNull
- AFXDB/CRecordset::IsFieldNullable
- AFXDB/CRecordset::IsOpen
- AFXDB/CRecordset::Move
- AFXDB/CRecordset::MoveFirst
- AFXDB/CRecordset::MoveLast
- AFXDB/CRecordset::MoveNext
- AFXDB/CRecordset::MovePrev
- AFXDB/CRecordset::OnSetOptions
- AFXDB/CRecordset::OnSetUpdateOptions
- AFXDB/CRecordset::Open
- AFXDB/CRecordset::RefreshRowset
- AFXDB/CRecordset::Requery
- AFXDB/CRecordset::SetAbsolutePosition
- AFXDB/CRecordset::SetBookmark
- AFXDB/CRecordset::SetFieldDirty
- AFXDB/CRecordset::SetFieldNull
- AFXDB/CRecordset::SetLockingMode
- AFXDB/CRecordset::SetParamNull
- AFXDB/CRecordset::SetRowsetCursorPosition
- AFXDB/CRecordset::SetRowsetSize
- AFXDB/CRecordset::Update
- AFXDB/CRecordset::m_hstmt
- AFXDB/CRecordset::m_nFields
- AFXDB/CRecordset::m_nParams
- AFXDB/CRecordset::m_pDatabase
- AFXDB/CRecordset::m_strFilter
- AFXDB/CRecordset::m_strSort
helpviewer_keywords:
- CRecordset [MFC], CRecordset
- CRecordset [MFC], AddNew
- CRecordset [MFC], CanAppend
- CRecordset [MFC], CanBookmark
- CRecordset [MFC], Cancel
- CRecordset [MFC], CancelUpdate
- CRecordset [MFC], CanRestart
- CRecordset [MFC], CanScroll
- CRecordset [MFC], CanTransact
- CRecordset [MFC], CanUpdate
- CRecordset [MFC], CheckRowsetError
- CRecordset [MFC], Close
- CRecordset [MFC], Delete
- CRecordset [MFC], DoBulkFieldExchange
- CRecordset [MFC], DoFieldExchange
- CRecordset [MFC], Edit
- CRecordset [MFC], FlushResultSet
- CRecordset [MFC], GetBookmark
- CRecordset [MFC], GetDefaultConnect
- CRecordset [MFC], GetDefaultSQL
- CRecordset [MFC], GetFieldValue
- CRecordset [MFC], GetODBCFieldCount
- CRecordset [MFC], GetODBCFieldInfo
- CRecordset [MFC], GetRecordCount
- CRecordset [MFC], GetRowsetSize
- CRecordset [MFC], GetRowsFetched
- CRecordset [MFC], GetRowStatus
- CRecordset [MFC], GetSQL
- CRecordset [MFC], GetStatus
- CRecordset [MFC], GetTableName
- CRecordset [MFC], IsBOF
- CRecordset [MFC], IsDeleted
- CRecordset [MFC], IsEOF
- CRecordset [MFC], IsFieldDirty
- CRecordset [MFC], IsFieldNull
- CRecordset [MFC], IsFieldNullable
- CRecordset [MFC], IsOpen
- CRecordset [MFC], Move
- CRecordset [MFC], MoveFirst
- CRecordset [MFC], MoveLast
- CRecordset [MFC], MoveNext
- CRecordset [MFC], MovePrev
- CRecordset [MFC], OnSetOptions
- CRecordset [MFC], OnSetUpdateOptions
- CRecordset [MFC], Open
- CRecordset [MFC], RefreshRowset
- CRecordset [MFC], Requery
- CRecordset [MFC], SetAbsolutePosition
- CRecordset [MFC], SetBookmark
- CRecordset [MFC], SetFieldDirty
- CRecordset [MFC], SetFieldNull
- CRecordset [MFC], SetLockingMode
- CRecordset [MFC], SetParamNull
- CRecordset [MFC], SetRowsetCursorPosition
- CRecordset [MFC], SetRowsetSize
- CRecordset [MFC], Update
- CRecordset [MFC], m_hstmt
- CRecordset [MFC], m_nFields
- CRecordset [MFC], m_nParams
- CRecordset [MFC], m_pDatabase
- CRecordset [MFC], m_strFilter
- CRecordset [MFC], m_strSort
ms.assetid: dd89a21d-ef39-4aab-891b-1e373d67c855
ms.openlocfilehash: d00764205b3b81e9f01dbe53d0c67372ebb2532e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219624"
---
# <a name="crecordset-class"></a>CRecordset-Klasse

Stellt eine Gruppe von Datensätzen dar, die aus einer Datenquelle ausgewählt wurden.

## <a name="syntax"></a>Syntax

```
class CRecordset : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRecordset:: CRecordset](#crecordset)|Erstellt ein `CRecordset`-Objekt. Ihre abgeleitete Klasse muss einen Konstruktor bereitstellen, der diese aufruft.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[CRecordset:: AddNew](#addnew)|Bereitet das Hinzufügen eines neuen Datensatzes vor. Wird aufgerufen `Update` , um die Addition abzuschließen.|
|[CRecordset:: CanAppend](#canappend)|Gibt einen Wert ungleich 0 (null) zurück, wenn dem Recordset über die Member-Funktion neue Datensätze hinzugefügt werden `AddNew`|
|[CRecordset:: CanBookmark](#canbookmark)|Gibt einen Wert ungleich 0 zurück, wenn das Recordset Lesezeichen unterstützt|
|[CRecordset:: Cancel](#cancel)|Bricht einen asynchronen Vorgang oder einen Prozess von einem zweiten Thread ab.|
|[CRecordset:: CancelUpdate](#cancelupdate)|Bricht ausstehende Updates aufgrund eines-oder- `AddNew` `Edit` Vorgangs ab.|
|[CRecordset:: canrestart](#canrestart)|Gibt einen Wert ungleich 0 zurück `Requery` , wenn aufgerufen werden kann, um die Abfrage des Recordsets erneut auszuführen.|
|[CRecordset:: CanScroll](#canscroll)|Gibt einen Wert ungleich 0 (null) zurück, wenn Sie durch die Datensätze|
|[CRecordset:: CanTransact](#cantransact)|Gibt einen Wert ungleich 0 zurück, wenn die Datenquelle Transaktionen unterstützt.|
|[CRecordset:: CanUpdate](#canupdate)|Gibt einen Wert ungleich 0 (null) zurück, wenn das Recordset aktualisiert werden kann (Sie können Datensätze hinzufügen, aktualisieren oder löschen).|
|[CRecordset:: checkrowseterror](#checkrowseterror)|Wird aufgerufen, um beim Abrufen von Datensätzen generierte Fehler zu behandeln.|
|[CRecordset:: Close](#close)|Schließt das Recordset und den zugeordneten ODBC hstmt.|
|[CRecordset::D Elete](#delete)|Löscht den aktuellen Datensatz aus dem Recordset. Sie müssen nach dem Löschen explizit einen Bildlauf zu einem anderen Datensatz durchführen.|
|[CRecordset::D obulkfieldexchange](#dobulkfieldexchange)|Wird aufgerufen, um Massendaten Zeilen aus der Datenquelle in das Recordset auszutauschen. Implementiert Massendaten Satz Feld Austausch (Bulk RFX).|
|[CRecordset::D ofieldexchange](#dofieldexchange)|Wird aufgerufen, um Daten (in beide Richtungen) zwischen den Felddatenmembern des Recordsets und dem entsprechenden Datensatz in der Datenquelle auszutauschen. Implementiert Daten Satz Feld Austausch (RFX).|
|[CRecordset:: Edit](#edit)|Bereitet Änderungen am aktuellen Datensatz vor. Ruft `Update` auf, um die Bearbeitung abzuschließen.|
|[CRecordset:: flushresultset](#flushresultset)|Gibt einen Wert ungleich 0 (null) zurück, wenn ein anderes Resultset abgerufen wird, wenn eine vordefinierte Abfrage verwendet wird.|
|[CRecordset:: GetBookmark](#getbookmark)|Weist dem Parameter Objekt den Lesezeichen Wert eines Datensatzes zu.|
|[CRecordset:: GetDefaultConnect](#getdefaultconnect)|Aufgerufen, um die Standard Verbindungs Zeichenfolge zu erhalten.|
|[CRecordset:: getdefaulzql](#getdefaultsql)|Wird aufgerufen, um die auszuführende SQL-Standard Zeichenfolge zu erhalten|
|[CRecordset:: GetFieldValue](#getfieldvalue)|Gibt den Wert eines Felds in einem Recordset zurück.|
|[CRecordset:: getodbcfieldcount](#getodbcfieldcount)|Gibt die Anzahl der Felder im Recordset zurück.|
|[CRecordset:: GetODBCFieldInfo](#getodbcfieldinfo)|Gibt bestimmte Arten von Informationen zu den Feldern in einem Recordset zurück.|
|[CRecordset:: GetRecordCount](#getrecordcount)|Gibt die Anzahl der Datensätze im Recordset zurück.|
|[CRecordset:: getrowsetsize](#getrowsetsize)|Gibt die Anzahl der Datensätze zurück, die während eines einzelnen Abruf Vorgangs abgerufen werden sollen.|
|[CRecordset:: getrowsfetch](#getrowsfetched)|Gibt die tatsächliche Anzahl von Zeilen zurück, die während eines Abruf Vorgangs abgerufen wurden.|
|[CRecordset:: GetRowStatus](#getrowstatus)|Gibt den Status der Zeile nach einem Abruf Vorgang zurück.|
|[CRecordset:: gezql](#getsql)|Ruft die SQL-Zeichenfolge ab, mit der Datensätze für das Recordset ausgewählt werden.|
|[CRecordset:: GetStatus](#getstatus)|Ruft den Status des Recordsets ab: den Index des aktuellen Datensatzes und ob die endgültige Anzahl der Datensätze abgerufen wurde.|
|[CRecordset:: GetTableName](#gettablename)|Ruft den Namen der Tabelle ab, auf der das Recordset basiert.|
|[CRecordset:: IsBOF](#isbof)|Gibt einen Wert ungleich 0 (null) zurück, wenn das Recordset vor dem ersten Datensatz positioniert wurde. Es ist kein aktueller Datensatz vorhanden.|
|[CRecordset:: isDeleted](#isdeleted)|Gibt einen Wert ungleich 0 (null) zurück, wenn das Recordset auf einem gelöschten Datensatz positioniert|
|[CRecordset:: IsEOF](#iseof)|Gibt einen Wert ungleich 0 (null) zurück, wenn das Recordset nach dem letzten Datensatz positioniert wurde. Es ist kein aktueller Datensatz vorhanden.|
|[CRecordset:: IsFieldDirty](#isfielddirty)|Gibt einen Wert ungleich 0 (null) zurück, wenn das angegebene Feld im aktuellen Datensatz geändert wurde.|
|[CRecordset:: IsFieldNull](#isfieldnull)|Gibt einen Wert ungleich 0 (null) zurück, wenn das angegebene Feld im aktuellen Datensatz NULL ist (weist keinen Wert auf).|
|[CRecordset:: IsFieldNullable](#isfieldnullable)|Gibt einen Wert ungleich 0 (null) zurück, wenn das angegebene Feld im aktuellen Datensatz auf NULL (ohne Wert) festgelegt werden kann.|
|[CRecordset:: IsOpen](#isopen)|Gibt einen Wert ungleich 0 zurück, wenn `Open` zuvor aufgerufen wurde.|
|[CRecordset:: Move](#move)|Positioniert das Recordset auf eine angegebene Anzahl von Datensätzen aus dem aktuellen Datensatz in beide Richtungen.|
|[CRecordset:: muvefirst](#movefirst)|Positioniert den aktuellen Datensatz auf dem ersten Datensatz im Recordset. Testen Sie `IsBOF` zunächst.|
|[CRecordset:: muvelast](#movelast)|Positioniert den aktuellen Datensatz im letzten Datensatz oder im letzten Rowset. Testen Sie `IsEOF` zunächst.|
|[CRecordset:: wvenext](#movenext)|Positioniert den aktuellen Datensatz im nächsten Datensatz oder im nächsten Rowset. Testen Sie `IsEOF` zunächst.|
|[CRecordset:: weprev](#moveprev)|Positioniert den aktuellen Datensatz für den vorherigen Datensatz oder für das vorherige Rowset. Testen Sie `IsBOF` zunächst.|
|[CRecordset:: OnSetOptions](#onsetoptions)|Wird aufgerufen, um Optionen für die angegebene ODBC-Anweisung festzulegen (bei Auswahl verwendet).|
|[CRecordset:: onsetupdateoptions](#onsetupdateoptions)|Wird aufgerufen, um Optionen für die angegebene ODBC-Anweisung festzulegen (bei Update verwendet).|
|[CRecordset:: Open](#open)|Öffnet das Recordset, indem die Tabelle abgerufen oder die vom Recordset darstellte Abfrage durchgeführt wird.|
|[CRecordset:: erfrischendes Rowset](#refreshrowset)|Aktualisiert die Daten und den Status der angegebenen Zeile (n).|
|[CRecordset:: Requery](#requery)|Führt die Abfrage des Recordsets erneut aus, um die ausgewählten Datensätze zu aktualisieren.|
|[CRecordset:: SetAbsolutePosition](#setabsoluteposition)|Positioniert das Recordset auf dem Datensatz, der der angegebenen Datensatznummer entspricht.|
|[CRecordset:: SetBookmark](#setbookmark)|Positioniert das Recordset in dem durch das Lesezeichen angegebenen Datensatz.|
|[CRecordset:: SetFieldDirty](#setfielddirty)|Markiert das angegebene Feld im aktuellen Datensatz als geändert.|
|[CRecordset:: SetFieldNull](#setfieldnull)|Legt den Wert des angegebenen Felds im aktuellen Datensatz auf NULL fest (ohne Wert).|
|[CRecordset:: SetLockingMode](#setlockingmode)|Legt den Sperrmodus auf die "optimistische" Sperrung (Standardeinstellung) oder die "pessimistische" Sperre fest. Bestimmt, wie Datensätze für Updates gesperrt werden.|
|[CRecordset:: SetParamNull](#setparamnull)|Legt den angegebenen Parameter auf NULL (ohne Wert) fest.|
|[CRecordset:: setrowsetcurrsorposition](#setrowsetcursorposition)|Positioniert den Cursor in der angegebenen Zeile im Rowset.|
|[CRecordset:: SetRowsetSize](#setrowsetsize)|Gibt die Anzahl der Datensätze an, die während eines Abruf Vorgangs abgerufen werden sollen.|
|[CRecordset:: Update](#update)|Schließt einen- `AddNew` Vorgang oder-Vorgang ab, `Edit` indem die neuen oder bearbeiteten Daten in der Datenquelle gespeichert werden.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRecordset:: m_hstmt](#m_hstmt)|Enthält das ODBC-Anweisungs Handle für das Recordset. Geben Sie `HSTMT` ein.|
|[CRecordset:: m_nFields](#m_nfields)|Enthält die Anzahl der Felddatenmember im Recordset. Geben Sie `UINT` ein.|
|[CRecordset:: m_nParams](#m_nparams)|Enthält die Anzahl der Parameterdatenmember im Recordset. Geben Sie `UINT` ein.|
|[CRecordset:: m_pDatabase](#m_pdatabase)|Enthält einen Zeiger auf das- `CDatabase` Objekt, über das das Recordset mit einer Datenquelle verbunden ist.|
|[CRecordset:: m_strFilter](#m_strfilter)|Enthält eine `CString` , die eine strukturierte Abfragesprache (SQL)- `WHERE` Klausel angibt. Wird als Filter verwendet, um nur die Datensätze auszuwählen, die bestimmte Kriterien erfüllen.|
|[CRecordset:: m_strSort](#m_strsort)|Enthält eine `CString` , die eine SQL- `ORDER BY` Klausel angibt. Wird verwendet, um zu steuern, wie die Datensätze sortiert werden.|

## <a name="remarks"></a><a name="remarks"></a> Hinweise

Objekte, die als "Recordsets" bezeichnet `CRecordset` werden, werden in der Regel in zwei Formen verwendet: Dynasets und Momentaufnahmen. Ein Dynaset bleibt mit den von anderen Benutzern vorgenommenen Datenaktualisierungen synchronisiert. Eine Momentaufnahme ist eine statische Ansicht der Daten. Jedes Formular stellt einen Satz von Datensätzen dar, die zum Zeitpunkt des Öffnens des Recordsets festgelegt werden. Wenn Sie jedoch einen Bildlauf zu einem Datensatz in einem Dynaset durchführen, werden die Änderungen, die anschließend an dem Datensatz vorgenommen werden, entweder von anderen Benutzern oder von anderen Recordsets in der Anwendung angezeigt.

> [!NOTE]
> Verwenden Sie stattdessen die Klasse [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) , wenn Sie mit den DAO-Klassen (Data Access Objects) anstatt mit den Open Database Connectivity-Klassen (ODBC) arbeiten. Weitere Informationen finden Sie im Artikel [Übersicht: Datenbankprogrammierung](../../data/data-access-programming-mfc-atl.md).

Um mit beiden Arten von Recordsets arbeiten zu können, leiten Sie in der Regel eine anwendungsspezifische Recordsetklasse von ab `CRecordset` . Recordsets wählen Sie Datensätze aus einer Datenquelle aus, und Sie können dann folgende Aktionen ausführen:

- Scrollen Sie durch die Datensätze.

- Aktualisieren Sie die Datensätze, und legen Sie einen Sperrmodus fest.

- Filtern Sie das Recordset, um einzuschränken, welche Datensätze aus den in der Datenquelle verfügbaren Datensätzen ausgewählt werden.

- Sortieren Sie das Recordset.

- Parametrisieren Sie das Recordset, um seine Auswahl mit Informationen anzupassen, die bis zur Laufzeit nicht bekannt sind.

Um die Klasse zu verwenden, öffnen Sie eine Datenbank, und erstellen Sie ein Recordset-Objekt, indem Sie dem Konstruktor einen Zeiger auf das `CDatabase` Objekt übergeben. Anschließend wird die Member-Funktion des Recordsets aufgerufen, mit der `Open` Sie angeben können, ob es sich bei dem Objekt um ein Dynaset oder eine Momentaufnahme handelt. `Open`Durch den Aufruf von werden Daten aus der Datenquelle ausgewählt. Nachdem das Recordset-Objekt geöffnet wurde, können Sie mithilfe seiner Element Funktionen und Datenmember einen Bildlauf durch die Datensätze durchführen und darauf anwenden. Welche Vorgänge verfügbar sind, hängt davon ab, ob das Objekt ein Dynaset oder eine Momentaufnahme ist, ob es aktualisierbar oder schreibgeschützt ist (Dies hängt von der Funktion der Open Database Connectivity (ODBC)-Datenquelle ab) und davon, ob Sie das Massen Abrufen von Zeilen implementiert haben. Um Datensätze zu aktualisieren, die seit dem-Befehl geändert oder hinzugefügt wurden, können Sie `Open` die Member-Funktion des-Objekts aufzurufen `Requery` . Nennen Sie die Member-Funktion des-Objekts, `Close` und zerstören Sie das-Objekt, wenn Sie damit fertig sind.

In einer abgeleiteten `CRecordset` Klasse wird der Daten Satz Feld Austausch (RFX) oder der Massendaten Satz Feld Austausch (Bulk RFX) verwendet, um das Lesen und Aktualisieren von Daten Satz Feldern zu unterstützen.

Weitere Informationen zu Recordsets und Daten Satz Feld Austausch finden Sie in der Artikel [Übersicht: Datenbankprogrammierung](../../data/data-access-programming-mfc-atl.md), [Recordset (ODBC)](../../data/odbc/recordset-odbc.md), [Recordset: Abrufen von Datensätzen in einem Massen Vorgang (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)und Daten [Satz Feld Austausch (RFX)](../../data/odbc/record-field-exchange-rfx.md). Einen Schwerpunkt auf Dynasets und Momentaufnahmen finden Sie in den Artikeln [Dynaset](../../data/odbc/dynaset.md) und [Snapshot](../../data/odbc/snapshot.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CRecordset`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="crecordsetaddnew"></a><a name="addnew"></a>CRecordset:: AddNew

Bereitet das Hinzufügen eines neuen Datensatzes zur Tabelle vor.

```
virtual void AddNew();
```

### <a name="remarks"></a>Bemerkungen

Um den neu hinzugefügten Datensatz anzuzeigen, müssen Sie die Funktion " [Requery](#requery) Member" aufzurufen. Die Felder des Datensatzes sind anfänglich NULL. (In der Daten Bank Terminologie bedeutet NULL, dass kein Wert vorhanden ist, und ist nicht mit NULL in C++ identisch.) Um den Vorgang abzuschließen, müssen Sie die [Update](#update) Member-Funktion aufzurufen. `Update`speichert die Änderungen an der Datenquelle.

> [!NOTE]
> Wenn Sie das Massen Abrufen von Zeilen implementiert haben, können Sie nicht aufzurufen `AddNew` . Dies führt zu einer fehlgeschlagenen Bestätigung. Obwohl die-Klasse `CRecordset` keinen Mechanismus zum Aktualisieren von Massendaten Zeilen bereitstellt, können Sie Ihre eigenen Funktionen mithilfe der ODBC-API-Funktion schreiben `SQLSetPos` . Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`AddNew`bereitet einen neuen, leeren Datensatz mithilfe der Felddatenmember des Recordsets vor. Nachdem Sie aufgerufen `AddNew` haben, legen Sie die gewünschten Werte in den Felddatenmembern des Recordsets fest. (Sie müssen die Funktion zum [Bearbeiten](#edit) von Membern nicht für diesen Zweck aufzurufen, sondern `Edit` nur für vorhandene Datensätze verwenden.) Wenn Sie anschließend aufzurufen `Update` , werden geänderte Werte in den Felddatenmembern in der Datenquelle gespeichert.

> [!CAUTION]
> Wenn Sie vor dem aufzurufen einen Bildlauf zu einem neuen Datensatz ausführen `Update` , geht der neue Datensatz verloren, und es wird keine Warnung ausgegeben.

Wenn die Datenquelle Transaktionen unterstützt, können Sie den `AddNew` anzurufenden Teil einer Transaktion durchführen. Weitere Informationen zu Transaktionen finden Sie unter Class [CDatabase](../../mfc/reference/cdatabase-class.md). Beachten Sie, dass Sie [CDatabase:: BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) aufrufen sollten, bevor Sie aufrufen `AddNew` .

> [!NOTE]
> Für Dynasets werden dem Recordset neue Datensätze als letzter Datensatz hinzugefügt. Hinzugefügte Datensätze werden keinen Momentaufnahmen hinzugefügt. Sie müssen aufzurufen `Requery` , um das Recordset zu aktualisieren.

Es ist unzulässig, `AddNew` für ein Recordset aufzurufen, dessen `Open` Member-Funktion nicht aufgerufen wurde. Eine `CDBException` wird ausgelöst, wenn Sie `AddNew` für ein Recordset aufzurufen, das nicht an angefügt werden kann. Sie können ermitteln, ob das Recordset aktualisierbar ist, indem Sie " [CanAppend](#canappend)" aufrufen.

Weitere Informationen finden Sie in den folgenden Artikeln: [Recordset: Wie Recordsets Update Einträge (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md), [Recordset: Hinzufügen, aktualisieren und Löschen von Datensätzen (](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)ODBC) und [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Artikel [Transaktion: Ausführen einer Transaktion in einem Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="crecordsetcanappend"></a><a name="canappend"></a>CRecordset:: CanAppend

Bestimmt, ob mit dem zuvor geöffneten Recordset neue Datensätze hinzugefügt werden können.

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0, wenn das Recordset das Hinzufügen neuer Datensätze zulässt andernfalls 0. `CanAppend`gibt 0 zurück, wenn Sie das Recordset als schreibgeschützt geöffnet haben.

## <a name="crecordsetcanbookmark"></a><a name="canbookmark"></a>CRecordset:: CanBookmark

Bestimmt, ob das Recordset es Ihnen ermöglicht, Datensätze mithilfe von Lesezeichen zu markieren.

```
BOOL CanBookmark() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn das Recordset Lesezeichen unterstützt. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist unabhängig von der- `CRecordset::useBookmarks` Option im *dwOptions* -Parameter der [Open](#open) Member-Funktion. `CanBookmark`Gibt an, ob der angegebene ODBC-Treiber und der Cursor Typ Lesezeichen unterstützen. `CRecordset::useBookmarks`Gibt an, ob Lesezeichen verfügbar sind, sofern diese unterstützt werden.

> [!NOTE]
> Lesezeichen werden für Vorwärts-Recordsets nicht unterstützt.

Weitere Informationen zu Lesezeichen und Recordsetnavigation finden Sie in den Artikeln [Recordset: Lesezeichen und absolute Positionen (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) und [Recordset: Scrollen (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetcancel"></a><a name="cancel"></a>CRecordset:: Cancel

Fordert an, dass die Datenquelle entweder einen laufenden asynchronen Vorgang oder einen Prozess von einem zweiten Thread abbricht.

```cpp
void Cancel();
```

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass die MFC-ODBC-Klassen die asynchrone Verarbeitung nicht mehr verwenden. zum Ausführen eines asynchronen Vorgangs müssen Sie die ODBC-API-Funktion direkt aufrufen `SQLSetConnectOption` . Weitere Informationen finden Sie im Thema zum asynchronen Ausführen von Funktionen im *ODBC SDK-Programmier Handbuch*.

## <a name="crecordsetcancelupdate"></a><a name="cancelupdate"></a>CRecordset:: CancelUpdate

Bricht alle ausstehenden Updates ab, die durch einen [Edit](#edit) -oder [AddNew](#addnew) -Vorgang verursacht wurden, bevor [Update](#update) aufgerufen wird.

```cpp
void CancelUpdate();
```

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Diese Member-Funktion ist für Recordsets, die das Abrufen von Massen Zeilen verwenden, nicht anwendbar, da solche Recordsets, oder nicht abrufen können `Edit` `AddNew` `Update` . Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Wenn die automatische Überprüfung der geänderten Felder aktiviert ist, `CancelUpdate` werden die Element Variablen in den Werten wieder hergestellt, die Sie vor `Edit` oder `AddNew` aufgerufen haben. Andernfalls bleiben alle Wertänderungen erhalten. Standardmäßig ist die automatische Feld Überprüfung aktiviert, wenn das Recordset geöffnet wird. Um dies zu deaktivieren, müssen Sie die `CRecordset::noDirtyFieldCheck` im *dwOptions* -Parameter der [Open](#open) Member-Funktion angeben.

Weitere Informationen zum Aktualisieren von Daten finden Sie im Artikel [Recordset: Hinzufügen, aktualisieren und Löschen von Datensätzen (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md).

## <a name="crecordsetcanrestart"></a><a name="canrestart"></a>CRecordset:: canrestart

Bestimmt, ob das Recordset das Neustarten der Abfrage (zum Aktualisieren der zugehörigen Datensätze) durch Aufrufen der `Requery` Member-Funktion zulässt.

```
BOOL CanRestart() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Anforderung zulässig ist. andernfalls 0.

## <a name="crecordsetcanscroll"></a><a name="canscroll"></a>CRecordset:: CanScroll

Bestimmt, ob das Recordset einen Bildlauf zulässt.

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn das Recordset einen Bildlauf zulässt. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zum Scrollen finden Sie im Artikel [Recordset: Scrollen (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetcantransact"></a><a name="cantransact"></a>CRecordset:: CanTransact

Bestimmt, ob das Recordset Transaktionen zulässt.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Recordset Transaktionen zulässt. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="crecordsetcanupdate"></a><a name="canupdate"></a>CRecordset:: CanUpdate

Bestimmt, ob das Recordset aktualisiert werden kann.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Recordset aktualisiert werden kann. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Ein Recordset ist möglicherweise schreibgeschützt, wenn die zugrunde liegende Datenquelle schreibgeschützt ist, oder wenn Sie beim `CRecordset::readOnly` Öffnen des Recordsets im *dwOptions* -Parameter angegeben haben.

## <a name="crecordsetcheckrowseterror"></a><a name="checkrowseterror"></a>CRecordset:: checkrowseterror

Wird aufgerufen, um beim Abrufen von Datensätzen generierte Fehler zu behandeln.

```
virtual void CheckRowsetError(RETCODE nRetCode);
```

### <a name="parameters"></a>Parameter

*nretcode*<br/>
Ein Rückgabecode der ODBC-API-Funktion. Einzelheiten finden Sie unter "Hinweise".

### <a name="remarks"></a>Bemerkungen

Diese Funktion für virtuelle Member behandelt Fehler, die auftreten, wenn Datensätze abgerufen werden, und ist beim Abrufen von Massen Zeilen nützlich. Möglicherweise möchten Sie außer Kraft `CheckRowsetError` setzen, um eine eigene Fehlerbehandlung zu implementieren.

`CheckRowsetError`wird automatisch in einem Cursor Navigations Vorgang aufgerufen, z. b. `Open` , `Requery` oder jeder `Move` Vorgang. Es wird der Rückgabewert der ODBC-API-Funktion an Sie übermittelt `SQLExtendedFetch` . In der folgenden Tabelle sind die möglichen Werte für den *nretcode* -Parameter aufgeführt.

|nretcode|BESCHREIBUNG|
|--------------|-----------------|
|SQL_SUCCESS|Die Funktion wurde erfolgreich abgeschlossen. Es sind keine zusätzlichen Informationen verfügbar.|
|SQL_SUCCESS_WITH_INFO|Die Funktion wurde erfolgreich abgeschlossen, möglicherweise mit einem nicht schwerwiegenden Fehler. Zusätzliche Informationen können durch Aufrufen von abgerufen werden `SQLError` .|
|SQL_NO_DATA_FOUND|Alle Zeilen aus dem Resultset wurden abgerufen.|
|SQL_ERROR|Fehler bei der Funktion. Zusätzliche Informationen können durch Aufrufen von abgerufen werden `SQLError` .|
|SQL_INVALID_HANDLE|Funktion konnte aufgrund eines ungültigen Umgebungs Handles, Verbindungs Handles oder Anweisungs Handles nicht ausgeführt werden. Dies weist auf einen Programmierfehler hin. In sind keine weiteren Informationen verfügbar `SQLError` .|
|SQL_STILL_EXECUTING|Eine Funktion, die asynchron gestartet wurde, wird weiterhin ausgeführt. Beachten Sie, dass MFC standardmäßig niemals diesen Wert an übergeben wird `CheckRowsetError` . MFC wird weiterhin aufrufen, `SQLExtendedFetch` bis SQL_STILL_EXECUTING nicht mehr zurückgegeben wird.|

Weitere Informationen zu finden Sie in `SQLError` der Windows SDK. Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetclose"></a><a name="close"></a>CRecordset:: Close

Schließt das Recordset.

```
virtual void Close();
```

### <a name="remarks"></a>Bemerkungen

Der ODBC hstmt und der gesamte Arbeitsspeicher, dem das für das Recordset zugewiesene Framework zugewiesen wird, werden aufgehoben. Nach dem Aufruf `Close` von löschen Sie in der Regel das C++ Recordset-Objekt, wenn es mit zugeordnet wurde **`new`** .

Sie können `Open` nach dem Aufrufen von erneut aufrufen `Close` . Auf diese Weise können Sie das Recordset-Objekt wieder verwenden. Die Alternative besteht darin, aufzurufen `Requery` .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]

## <a name="crecordsetcrecordset"></a><a name="crecordset"></a>CRecordset:: CRecordset

Erstellt ein `CRecordset`-Objekt.

```
CRecordset(CDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>Parameter

*pdatabase*<br/>
Enthält einen Zeiger auf ein- `CDatabase` Objekt oder den Wert NULL. Wenn not NULL und die `CDatabase` Member- `Open` Funktion des Objekts nicht aufgerufen wurde, um Sie mit der Datenquelle zu verbinden, versucht das Recordset, es während des eigenen Aufrufs für Sie zu öffnen `Open` . Wenn NULL übergeben wird, `CDatabase` wird ein-Objekt erstellt und mit den Datenquellen Informationen verbunden, die Sie beim Ableiten Ihrer Recordset-Klasse mit ClassWizard angegeben haben.

### <a name="remarks"></a>Bemerkungen

Sie können entweder `CRecordset` direkt verwenden oder eine anwendungsspezifische Klasse von ableiten `CRecordset` . Sie können den Klassen-Assistenten verwenden, um die recordsetklassen abzuleiten.

> [!NOTE]
> Eine abgeleitete Klasse *muss* ihren eigenen Konstruktor bereitstellen. Nennen Sie den Konstruktor im Konstruktor ihrer abgeleiteten Klasse `CRecordset::CRecordset` , indem Sie die entsprechenden Parameter an den Konstruktor übergeben.

Übergeben Sie NULL an den recordsetkonstruktor, `CDatabase` damit ein-Objekt automatisch erstellt und verbunden wird. Dies ist eine hilfreiche Kurzform, die nicht erfordert, dass Sie ein-Objekt erstellen und verbinden, bevor Sie das `CDatabase` Recordset erstellen.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Artikel [Recordset: Deklarieren einer Klasse für eine Tabelle (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).

## <a name="crecordsetdelete"></a><a name="delete"></a>CRecordset::D Elete

Löscht den aktuellen Datensatz.

```
virtual void Delete();
```

### <a name="remarks"></a>Bemerkungen

Nach einem erfolgreichen Löschvorgang werden die Felddatenmember des Recordsets auf einen NULL-Wert festgelegt, und Sie müssen explizit eine der Funktionen abrufen, um `Move` den gelöschten Datensatz zu verschieben. Nachdem Sie den gelöschten Datensatz verschoben haben, ist es nicht möglich, dorthin zurückzukehren. Wenn die Datenquelle Transaktionen unterstützt, können Sie den `Delete` callpart einer Transaktion ausführen. Weitere Informationen finden Sie im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

> [!NOTE]
> Wenn Sie das Massen Abrufen von Zeilen implementiert haben, können Sie nicht aufzurufen `Delete` . Dies führt zu einer fehlgeschlagenen Bestätigung. Obwohl die-Klasse `CRecordset` keinen Mechanismus zum Aktualisieren von Massendaten Zeilen bereitstellt, können Sie Ihre eigenen Funktionen mithilfe der ODBC-API-Funktion schreiben `SQLSetPos` . Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!CAUTION]
> Das Recordset muss aktualisierbar sein, und es muss ein gültiger Datensatz im Recordset vorhanden sein, wenn Sie aufrufen `Delete` ; andernfalls tritt ein Fehler auf. Wenn Sie z. b. einen Datensatz löschen, aber keinen Bildlauf zu einem neuen Datensatz ausführen, bevor Sie den Vorgang `Delete` erneut ausführen, löst `Delete` eine [CDBException](../../mfc/reference/cdbexception-class.md)aus.

Anders als bei [AddNew](#addnew) und [Edit](#edit)folgt ein-Rückruf `Delete` nicht einem [Update-Update](#update). Wenn ein- `Delete` Rückruf fehlschlägt, bleiben die Felddatenmember unverändert.

### <a name="example"></a>Beispiel

Dieses Beispiel zeigt ein Recordset, das im Rahmen einer Funktion erstellt wurde. Im Beispiel wird davon ausgegangen, dass das vorhanden sein `m_dbCust` einer Element Variablen vom Typ `CDatabase` bereits mit der Datenquelle verbunden ist.

[!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]

## <a name="crecordsetdobulkfieldexchange"></a><a name="dobulkfieldexchange"></a>CRecordset::D obulkfieldexchange

Wird aufgerufen, um Massendaten Zeilen aus der Datenquelle in das Recordset auszutauschen. Implementiert Massendaten Satz Feld Austausch (Bulk RFX).

```
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) -Objekt. Das Framework hat dieses Objekt bereits so eingerichtet, dass ein Kontext für den Feld Austausch Vorgang angegeben wird.

### <a name="remarks"></a>Bemerkungen

Wenn das Massen Abrufen von Zeilen implementiert ist, ruft das Framework diese Member-Funktion auf, um automatisch Daten aus der Datenquelle in das Recordset-Objekt zu übertragen. `DoBulkFieldExchange`bindet auch die Parameter Datenmember, sofern vorhanden, an die Parameter Platzhalter in der SQL-Anweisungs Zeichenfolge für die Auswahl des Recordsets.

Wenn das Abrufen von Massen Zeilen nicht implementiert ist, ruft das Framework [DoFieldExchange](#dofieldexchange)auf. Um das Abrufen von Massen Zeilen zu implementieren, müssen Sie die- `CRecordset::useMultiRowFetch` Option des *dwOptions* -Parameters in der [Open](#open) Member-Funktion angeben.

> [!NOTE]
> `DoBulkFieldExchange`ist nur verfügbar, wenn Sie eine von abgeleitete Klasse verwenden `CRecordset` . Wenn Sie ein Recordset-Objekt direkt aus erstellt haben `CRecordset` , müssen Sie die [GetFieldValue](#getfieldvalue) -Member-Funktion aufrufen, um Daten abzurufen.

Der Massendaten Satz Feld Austausch (Bulk RFX) ähnelt dem Daten Satz Feld Austausch (RFX). Daten werden automatisch aus der Datenquelle in das Recordset-Objekt übertragen. Sie können jedoch nicht `AddNew` , `Edit` , `Delete` oder `Update` zum Übertragen von Änderungen an die Datenquelle abrufen. Die Klasse stellt `CRecordset` derzeit keinen Mechanismus zum Aktualisieren von Massendaten Zeilen bereit. Sie können jedoch eigene Funktionen mithilfe der ODBC-API-Funktion schreiben `SQLSetPos` .

Beachten Sie, dass ClassWizard keinen Massendaten Satz Feld Austausch unterstützt. Daher müssen Sie `DoBulkFieldExchange` manuell überschreiben, indem Sie Aufrufe der Bulk-RFX-Funktionen schreiben. Weitere Informationen zu diesen Funktionen finden Sie im Thema [Daten Satz Feld Austausch-Funktionen](../../mfc/reference/record-field-exchange-functions.md).

Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Weitere Informationen finden Sie im Artikel [Daten Satz Feld Austausch (RFX)](../../data/odbc/record-field-exchange-rfx.md).

## <a name="crecordsetdofieldexchange"></a><a name="dofieldexchange"></a>CRecordset::D ofieldexchange

Wird aufgerufen, um Daten (in beide Richtungen) zwischen den Felddatenmembern des Recordsets und dem entsprechenden Datensatz in der Datenquelle auszutauschen. Implementiert Daten Satz Feld Austausch (RFX).

```
virtual void DoFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) -Objekt. Das Framework hat dieses Objekt bereits so eingerichtet, dass ein Kontext für den Feld Austausch Vorgang angegeben wird.

### <a name="remarks"></a>Bemerkungen

Wenn das Massen Abrufen von Zeilen nicht implementiert ist, ruft das Framework diese Member-Funktion auf, um automatisch Daten zwischen den Felddatenmembern des Recordset-Objekts und den entsprechenden Spalten des aktuellen Datensatzes in der Datenquelle auszutauschen. `DoFieldExchange`bindet auch die Parameter Datenmember, sofern vorhanden, an die Parameter Platzhalter in der SQL-Anweisungs Zeichenfolge für die Auswahl des Recordsets.

Wenn das Massen Abrufen von Zeilen implementiert ist, ruft das Framework [DoBulkFieldExchange](#dobulkfieldexchange)auf. Um das Abrufen von Massen Zeilen zu implementieren, müssen Sie die- `CRecordset::useMultiRowFetch` Option des *dwOptions* -Parameters in der [Open](#open) Member-Funktion angeben.

> [!NOTE]
> `DoFieldExchange`ist nur verfügbar, wenn Sie eine von abgeleitete Klasse verwenden `CRecordset` . Wenn Sie ein Recordset-Objekt direkt aus erstellt haben `CRecordset` , müssen Sie die [GetFieldValue](#getfieldvalue) -Member-Funktion aufrufen, um Daten abzurufen.

Der Austausch von Felddaten, die als Daten Satz Feld Austausch (RFX) bezeichnet werden, funktioniert in beide Richtungen: aus den Felddatenmembern des Recordset-Objekts zu den Feldern des Datensatzes in der Datenquelle und aus dem Datensatz in der Datenquelle in das Recordset-Objekt.

Die einzige Aktion, die Sie normalerweise ausführen müssen, um `DoFieldExchange` für die abgeleitete Recordset-Klasse zu implementieren, besteht darin, die-Klasse mit ClassWizard zu erstellen und die Namen und Datentypen der Felddatenmember anzugeben. Sie können auch Code hinzufügen, der von ClassWizard zum Angeben von Parameterdatenmembern oder zum Behandeln von Spalten, die Sie dynamisch binden, geschrieben wird. Weitere Informationen finden Sie im Artikel [Recordset: Dynamisches Binden von Datenspalten (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Wenn Sie die abgeleitete Recordsetklasse mit ClassWizard deklarieren, schreibt der Assistent eine außer Kraft Setzung von `DoFieldExchange` für Sie, die dem folgenden Beispiel ähnelt:

[!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]

Weitere Informationen zu den RFX-Funktionen finden Sie im Thema [Daten Satz Feld Austausch-Funktionen](../../mfc/reference/record-field-exchange-functions.md).

Weitere Beispiele und Details zu `DoFieldExchange` finden Sie im Artikel [Daten Satz Feld Austausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Allgemeine Informationen zu RFX finden Sie im Artikel [Daten Satz Feld Austausch](../../data/odbc/record-field-exchange-rfx.md).

## <a name="crecordsetedit"></a><a name="edit"></a>CRecordset:: Edit

Ermöglicht das Ändern des aktuellen Datensatzes.

```
virtual void Edit();
```

### <a name="remarks"></a>Bemerkungen

Nachdem Sie aufgerufen `Edit` haben, können Sie die Felddatenmember ändern, indem Sie Ihre Werte direkt zurücksetzen. Der Vorgang wird abgeschlossen, wenn Sie anschließend die Funktion zum [Aktualisieren](#update) des Members aufzurufen, um die Änderungen in der Datenquelle zu speichern.

> [!NOTE]
> Wenn Sie das Massen Abrufen von Zeilen implementiert haben, können Sie nicht aufzurufen `Edit` . Dies führt zu einer fehlgeschlagenen Bestätigung. Obwohl die-Klasse `CRecordset` keinen Mechanismus zum Aktualisieren von Massendaten Zeilen bereitstellt, können Sie Ihre eigenen Funktionen mithilfe der ODBC-API-Funktion schreiben `SQLSetPos` . Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`Edit`speichert die Werte der Datenmember des Recordsets. Wenn Sie den Befehl ausführen `Edit` , Änderungen vornehmen und dann erneut aufzurufen `Edit` , werden die Werte des Datensatzes vor dem ersten-Befehl wieder hergestellt `Edit` .

In einigen Fällen möchten Sie möglicherweise eine Spalte aktualisieren, indem Sie Sie auf NULL (ohne Daten) festlegen. Dazu muss [SetFieldNull](#setfieldnull) mit dem Parameter "true" aufgerufen werden, um das Feld "Null" zu markieren. Dies bewirkt auch, dass die Spalte aktualisiert wird. Wenn Sie möchten, dass ein Feld in die Datenquelle geschrieben wird, auch wenn der Wert nicht geändert wurde, können Sie [SetFieldDirty](#setfielddirty) mit dem Parameter true aufrufen. Dies funktioniert auch, wenn das Feld den Wert NULL aufweist.

Wenn die Datenquelle Transaktionen unterstützt, können Sie den `Edit` callpart einer Transaktion ausführen. Beachten Sie, dass Sie [CDatabase:: BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) vor dem Aufrufen von `Edit` und nach dem Öffnen des Recordsets aufrufen sollten. Beachten Sie auch, dass der Aufruf von [CDatabase:: CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) kein Ersatz für den Aufruf von ist `Update` , um den `Edit` Vorgang abzuschließen. Weitere Informationen zu Transaktionen finden Sie unter Class [CDatabase](../../mfc/reference/cdatabase-class.md).

Abhängig vom aktuellen Sperrmodus kann der zu Aktualisier Ende Datensatz von gesperrt werden `Edit` , bis Sie `Update` einen anderen Datensatz anrufen oder einen Bildlauf zu einem anderen Datensatz durchführen oder ihn nur während des `Edit` Aufrufens sperren. Sie können den Sperrmodus mit [SetLockingMode](#setlockingmode)ändern.

Der vorherige Wert des aktuellen Datensatzes wird wieder hergestellt, wenn Sie einen Bildlauf zu einem neuen Datensatz ausführen, bevor Sie aufrufen `Update` . Eine `CDBException` wird ausgelöst, wenn Sie `Edit` für ein Recordset aufzurufen, das nicht aktualisiert werden kann, oder wenn kein aktueller Datensatz vorhanden ist.

Weitere Informationen finden Sie in den Artikeln [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md) und [Recordset: Sperren von Datensätzen (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]

## <a name="crecordsetflushresultset"></a><a name="flushresultset"></a>CRecordset:: flushresultset

Ruft das nächste Resultset einer vordefinierten Abfrage (gespeicherte Prozedur) ab, wenn mehrere Resultsets vorhanden sind.

```
BOOL FlushResultSet();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn mehr Resultsets abgerufen werden sollen. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie sollten `FlushResultSet` nur dann anrufen, wenn Sie den Cursor auf dem aktuellen Resultset vollständig abgeschlossen haben. Beachten Sie, dass der `FlushResultSet` Cursor für dieses Resultset nicht gültig ist, wenn Sie das nächste Resultset abrufen, indem Sie [MoveNext](#movenext) aufrufen `FlushResultSet` .

Wenn eine vordefinierte Abfrage einen Ausgabeparameter oder Eingabe-/Ausgabeparameter verwendet, müssen Sie aufrufen, `FlushResultSet` bis Sie `FALSE` (den Wert 0) zurückgibt, um diese Parameterwerte zu erhalten.

`FlushResultSet`Ruft die ODBC-API-Funktion auf `SQLMoreResults` . Wenn `SQLMoreResults` SQL_ERROR oder SQL_INVALID_HANDLE zurückgibt, löst `FlushResultSet` eine Ausnahme aus. Weitere Informationen zu finden Sie in `SQLMoreResults` der Windows SDK.

Die gespeicherte Prozedur muss gebundene Felder haben, wenn aufgerufen werden soll `FlushResultSet` .

### <a name="example"></a>Beispiel

Der folgende Code geht davon aus, dass `COutParamRecordset` ein `CRecordset` von abgeleitetes Objekt ist, das auf einer vordefinierten Abfrage mit einem Eingabeparameter und einem Output-Parameter basiert und über mehrere Resultsets verfügt. Beachten Sie, dass die Struktur von [DoFieldExchange](#dofieldexchange) außer Kraft gesetzt wird.

[!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]

[!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]

## <a name="crecordsetgetbookmark"></a><a name="getbookmark"></a>CRecordset:: GetBookmark

Ruft den Lesezeichen Wert für den aktuellen Datensatz ab.

```cpp
void GetBookmark(CDBVariant& varBookmark);
```

### <a name="parameters"></a>Parameter

*varbookmark*<br/>
Ein Verweis auf ein [CDBVariant](../../mfc/reference/cdbvariant-class.md) -Objekt, das das Lesezeichen für den aktuellen Datensatz darstellt.

### <a name="remarks"></a>Bemerkungen

Um zu ermitteln, ob Lesezeichen für das Recordset unterstützt werden, nennen Sie [CanBookmark](#canbookmark). Um Lesezeichen verfügbar zu machen, wenn Sie unterstützt werden, müssen Sie die- `CRecordset::useBookmarks` Option im *dwOptions* -Parameter der [Open](#open) Member-Funktion festlegen.

> [!NOTE]
> Wenn Lesezeichen nicht unterstützt werden oder nicht verfügbar sind, wird durch das Aufrufen von `GetBookmark` eine Ausnahme ausgelöst. Lesezeichen werden für Vorwärts-Recordsets nicht unterstützt.

`GetBookmark`weist dem-Objekt den Wert des Lesezeichens für den aktuellen Datensatz zu `CDBVariant` . Um zu diesem Datensatz zu einem beliebigen Zeitpunkt nach dem Wechsel zu einem anderen Datensatz zurückzukehren, müssen Sie [SetBookmark](#setbookmark) mit dem entsprechenden- `CDBVariant` Objekt aufrufen.

> [!NOTE]
> Nach bestimmten recordsetvorgängen sind Lesezeichen möglicherweise nicht mehr gültig. Wenn Sie z `GetBookmark` . b. den Befehl gefolgt von aufzurufen `Requery` , können Sie möglicherweise nicht mit dem Datensatz zurückkehren `SetBookmark` . [CDatabase:: getbookmarkpersistenz](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) aufrufen, um zu überprüfen, ob Sie sicher aufrufen können `SetBookmark` .

Weitere Informationen zu Lesezeichen und Recordsetnavigation finden Sie in den Artikeln [Recordset: Lesezeichen und absolute Positionen (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) und [Recordset: Scrollen (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetgetdefaultconnect"></a><a name="getdefaultconnect"></a>CRecordset:: GetDefaultConnect

Aufgerufen, um die Standard Verbindungs Zeichenfolge zu erhalten.

```
virtual CString GetDefaultConnect();
```

### <a name="return-value"></a>Rückgabewert

Eine `CString` , die die Standard Verbindungs Zeichenfolge enthält.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Member-Funktion auf, um die Standard Verbindungs Zeichenfolge für die Datenquelle zu erhalten, auf der das Recordset basiert. ClassWizard implementiert diese Funktion für Sie, indem die gleiche Datenquelle identifiziert wird, die Sie in ClassWizard verwenden, um Informationen zu Tabellen und Spalten zu erhalten. Bei der Entwicklung ihrer Anwendung ist es wahrscheinlich praktisch, dass Sie sich auf diese Standardverbindung verlassen. Die Standardverbindung eignet sich jedoch möglicherweise nicht für Benutzer Ihrer Anwendung. Wenn dies der Fall ist, sollten Sie diese Funktion neu implementieren und die Version von ClassWizard verwerfen. Weitere Informationen zu Verbindungs Zeichenfolgen finden Sie im Artikel [Datenquelle (ODBC)](../../data/odbc/data-source-odbc.md).

## <a name="crecordsetgetdefaultsql"></a><a name="getdefaultsql"></a>CRecordset:: getdefaulzql

Wird aufgerufen, um die auszuführende SQL-Standard Zeichenfolge zu erhalten

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>Rückgabewert

Ein-Wert `CString` , der die SQL-Standard Anweisung enthält.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Member-Funktion auf, um die SQL-Standard Anweisung zu erhalten, auf der das Recordset basiert. Dabei kann es sich um einen Tabellennamen oder eine SQL **Select** -Anweisung handeln.

Sie definieren indirekt die Standard-SQL-Anweisung, indem Sie Ihre Recordset-Klasse mit ClassWizard deklarieren, und ClassWizard führt diese Aufgabe für Sie aus.

Wenn Sie die SQL-Anweisungs Zeichenfolge für Ihre eigene Verwendung benötigen, können Sie den Befehl verwenden `GetSQL` , um die SQL-Anweisung zurückgegeben, mit der die Datensätze des Recordsets beim Öffnen ausgewählt wurden. Sie können die Standard-SQL-Zeichenfolge in der Überschreibung der-Klasse von bearbeiten `GetDefaultSQL` . Sie können z. b. einen aufzurufenden Abfragebefehl mithilfe einer **callananweisung** angeben. (Beachten Sie jedoch, dass `GetDefaultSQL` Sie bei der Bearbeitung von auch ändern müssen, damit Sie `m_nFields` der Anzahl der Spalten in der Datenquelle entsprechen.)

Weitere Informationen finden Sie im Artikel [Recordset: Deklarieren einer Klasse für eine Tabelle (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).

> [!CAUTION]
> Der Tabellenname ist leer, wenn das Framework einen Tabellennamen nicht identifizieren konnte, wenn mehrere Tabellennamen angegeben wurden, oder wenn eine Anweisung zum **Abrufen** nicht interpretiert werden konnte. Beachten Sie, dass Sie bei Verwendung einer **callananweisung** keine Leerzeichen zwischen der geschweiften Klammer und dem Schlüsselwort "-Schlüsselwort" einfügen dürfen, auch wenn Sie keine Leerzeichen vor der geschweiften Klammer oder vor dem **Select** - **Schlüsselwort in** einer **Select** -Anweisung einfügen.

## <a name="crecordsetgetfieldvalue"></a><a name="getfieldvalue"></a>CRecordset:: GetFieldValue

Ruft Felddaten im aktuellen Datensatz ab.

```cpp
void GetFieldValue(
    LPCTSTR lpszName,
    CDBVariant& varValue,
    short nFieldType = DEFAULT_FIELD_TYPE);

void GetFieldValue(
    short nIndex,
    CDBVariant& varValue,
    short nFieldType = DEFAULT_FIELD_TYPE);

void GetFieldValue(
    short nIndex,
    CStringA& strValue);

void GetFieldValue(
    short nIndex,
    CStringW& strValue);
```

### <a name="parameters"></a>Parameter

*lpszname*<br/>
Der Name eines Felds.

*varvalu*e ein Verweis auf ein [CDBVariant](../../mfc/reference/cdbvariant-class.md) -Objekt, das den Wert des Felds speichert.

*nfieldtype*<br/>
Der ODBC-C-Datentyp des Felds. Wenn Sie den Standardwert (DEFAULT_FIELD_TYPE) verwenden, erzwingt, `GetFieldValue` den C-Datentyp anhand der folgenden Tabelle aus dem SQL-Datentyp zu ermitteln. Andernfalls können Sie den Datentyp direkt angeben oder einen kompatiblen Datentyp auswählen. Beispielsweise können Sie beliebige Datentypen in SQL_C_CHAR speichern.

|C-Datentyp|SQL-Datentyp|
|-----------------|-------------------|
|SQL_C_BIT|SQL_BIT|
|SQL_C_UTINYINT|SQL_TINYINT|
|SQL_C_SSHORT|SQL_SMALLINT|
|SQL_C_SLONG|SQL_INTEGER|
|SQL_C_FLOAT|SQL_REAL|
|SQL_C_DOUBLE|SQL_FLOATSQL_DOUBLE|
|SQL_C_TIMESTAMP|SQL_DATESQL_TIMESQL_TIMESTAMP|
|SQL_C_CHAR|SQL_NUMERICSQL_DECIMALSQL_BIGINTSQL_CHARSQL_VARCHARSQL_LONGVARCHAR|
|SQL_C_BINARY|SQL_BINARYSQL_VARBINARYSQL_LONGVARBINARY|

Weitere Informationen zu ODBC-Datentypen finden Sie in den Themen "SQL-Datentypen" und "C-Datentypen" in Anhang D des Windows SDK.

*nIndex*<br/>
Der null basierte Index des Felds.

*strValue*<br/>
Ein Verweis auf ein [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Objekt, in dem der Wert des Felds, der in Text konvertiert wird, unabhängig vom Datentyp des Felds gespeichert wird.

### <a name="remarks"></a>Bemerkungen

Sie können ein Feld nach dem Namen oder nach dem Index suchen. Der Feldwert kann entweder in einem- `CDBVariant` Objekt oder in einem-Objekt gespeichert werden `CString` .

Wenn Sie das Massen Abrufen von Zeilen implementiert haben, wird der aktuelle Datensatz immer auf dem ersten Datensatz in einem Rowset positioniert. Wenn `GetFieldValue` Sie in einem Datensatz in einem bestimmten Rowset verwenden möchten, müssen Sie zuerst die Member-Funktion [setrowsetcursorposition](#setrowsetcursorposition) aufrufen, um den Cursor in die gewünschte Zeile in diesem Rowset zu verschieben. Anschließend wird `GetFieldValue` für diese Zeile aufgerufen. Um das Abrufen von Massen Zeilen zu implementieren, müssen Sie die- `CRecordset::useMultiRowFetch` Option des *dwOptions* -Parameters in der [Open](#open) Member-Funktion angeben.

Sie können `GetFieldValue` zum dynamischen Abrufen von Feldern zur Laufzeit verwenden, anstatt Sie zur Entwurfszeit statisch zu binden. Wenn Sie z. b. ein Recordset-Objekt direkt aus deklariert haben `CRecordset` , müssen Sie `GetFieldValue` zum Abrufen der Felddaten verwenden. Daten Satz Feld Austausch (RFX) oder Massendaten Satz Feld Austausch (Bulk RFX) ist nicht implementiert.

> [!NOTE]
> Wenn Sie ein Recordset-Objekt deklarieren, ohne von abgeleitet zu `CRecordset` werden, lassen Sie die ODBC-Cursor Bibliothek nicht geladen. Die Cursor Bibliothek erfordert, dass das Recordset mindestens eine gebundene Spalte hat. Wenn Sie jedoch direkt verwenden `CRecordset` , ist keine der Spalten gebunden. Die Member-Funktionen [CDatabase:: OpenEx](../../mfc/reference/cdatabase-class.md#openex) und [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) steuern, ob die Cursor Bibliothek geladen wird.

`GetFieldValue`Ruft die ODBC-API-Funktion auf `SQLGetData` . Wenn der Treiber den Wert SQL_NO_TOTAL für die tatsächliche Länge des Feldwerts ausgibt, löst `GetFieldValue` eine Ausnahme aus. Weitere Informationen zu finden Sie in `SQLGetData` der Windows SDK.

### <a name="example"></a>Beispiel

Der folgende Beispielcode veranschaulicht Aufrufe von `GetFieldValue` für ein Recordset-Objekt, das direkt aus deklariert wird `CRecordset` .

[!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]

> [!NOTE]
> Im Gegensatz zur DAO-Klasse verfügt `CDaoRecordset` `CRecordset` nicht über eine `SetFieldValue` Member-Funktion. Wenn Sie ein Objekt direkt aus erstellen `CRecordset` , ist es praktisch schreibgeschützt.

Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetgetodbcfieldcount"></a><a name="getodbcfieldcount"></a>CRecordset:: getodbcfieldcount

Ruft die Gesamtanzahl der Felder in Ihrem Recordset-Objekt ab.

```
short GetODBCFieldCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Felder im Recordset.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zum Erstellen von Recordsets finden Sie im Artikel [Recordset: Erstellen und Schließen von Recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

## <a name="crecordsetgetodbcfieldinfo"></a><a name="getodbcfieldinfo"></a>CRecordset:: GetODBCFieldInfo

Ruft Informationen zu den Feldern im Recordset ab.

```cpp
void GetODBCFieldInfo(
    LPCTSTR lpszName,
    CODBCFieldInfo& fieldinfo);

void GetODBCFieldInfo(
    short nIndex,
    CODBCFieldInfo& fieldinfo);
```

### <a name="parameters"></a>Parameter

*lpszname*<br/>
Der Name eines Felds.

*FieldInfo*<br/>
Ein Verweis auf eine- `CODBCFieldInfo` Struktur.

*nIndex*<br/>
Der null basierte Index des Felds.

### <a name="remarks"></a>Bemerkungen

Mit einer Version der-Funktion können Sie nach einem Feld nach dem Namen suchen. Die andere Version ermöglicht es Ihnen, ein Feld nach Index zu suchen.

Eine Beschreibung der zurückgegebenen Informationen finden Sie in der [codbcfieldinfo](../../mfc/reference/codbcfieldinfo-structure.md) -Struktur.

Weitere Informationen zum Erstellen von Recordsets finden Sie im Artikel [Recordset: Erstellen und Schließen von Recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

## <a name="crecordsetgetrecordcount"></a><a name="getrecordcount"></a>CRecordset:: GetRecordCount

Bestimmt die Größe des Recordsets.

```
long GetRecordCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Datensätze im Recordset. 0, wenn das Recordset keine Datensätze enthält. oder-1, wenn die Anzahl der Datensätze nicht bestimmt werden kann.

### <a name="remarks"></a>Bemerkungen

> [!CAUTION]
> Die Anzahl der Datensätze wird als "obere Grenze" beibehalten, und der höchste nummerierte Datensatz wird noch angezeigt, wenn der Benutzer die Datensätze durchläuft. Die Gesamtanzahl der Datensätze ist erst bekannt, wenn der Benutzer den letzten Datensatz überschritten hat. Aus Leistungsgründen wird die Anzahl nicht aktualisiert, wenn aufgerufen wird `MoveLast` . Um die Datensätze selbst zu zählen, wird wiederholt aufgerufen, bis eine ungleich `MoveNext` `IsEOF` NULL zurückgibt Das Hinzufügen eines Datensatzes über `CRecordset:AddNew` und `Update` erhöht die Anzahl. durch das Löschen eines Datensatzes über wird `CRecordset::Delete` die Anzahl verringert.

## <a name="crecordsetgetrowsetsize"></a><a name="getrowsetsize"></a>CRecordset:: getrowsetsize

Ruft die aktuelle Einstellung für die Anzahl der Zeilen ab, die während eines bestimmten Abruf Vorgangs abgerufen werden sollen.

```
DWORD GetRowsetSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Zeilen, die während eines bestimmten Abruf Vorgangs abgerufen werden sollen.

### <a name="remarks"></a>Bemerkungen

Wenn Sie das Massen Abrufen von Zeilen verwenden, ist die standardrowsetgröße beim Öffnen des Recordsets 25. Andernfalls ist der Wert 1.

Um das Abrufen von Massen Zeilen zu implementieren, müssen Sie die- `CRecordset::useMultiRowFetch` Option im *dwOptions* -Parameter der [Open](#open) Member-Funktion angeben. Um die Einstellung für die Rowsetgröße zu ändern, müssen Sie [SetRowsetSize](#setrowsetsize)aufrufen.

Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetgetrowsfetched"></a><a name="getrowsfetched"></a>CRecordset:: getrowsfetch

Bestimmt, wie viele Datensätze nach dem Abrufen tatsächlich abgerufen wurden.

```
DWORD GetRowsFetched() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Zeilen, die nach einem bestimmten Abruf Vorgang aus der Datenquelle abgerufen wurden.

### <a name="remarks"></a>Bemerkungen

Dies ist nützlich, wenn Sie das Massen Abrufen von Zeilen implementiert haben. Die Rowsetgröße gibt normalerweise an, wie viele Zeilen von einem Abruf Vorgang abgerufen werden. die Gesamtanzahl der Zeilen im Recordset wirkt sich jedoch auch darauf aus, wie viele Zeilen in einem Rowset abgerufen werden. Wenn das Recordset z. b. 10 Datensätze mit einer Rowsetgröße von 4 aufweist, führt die Schleife durch das durch Aufrufen des Recordsets dazu, dass `MoveNext` das abschließende Rowset nur über zwei Datensätze verfügt.

Um das Abrufen von Massen Zeilen zu implementieren, müssen Sie die- `CRecordset::useMultiRowFetch` Option im *dwOptions* -Parameter der [Open](#open) Member-Funktion angeben. Um die Rowsetgröße anzugeben, nennen Sie [SetRowsetSize](#setrowsetsize).

Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]

## <a name="crecordsetgetrowstatus"></a><a name="getrowstatus"></a>CRecordset:: GetRowStatus

Ruft den Status für eine Zeile im aktuellen Rowset ab.

```
WORD GetRowStatus(WORD wRow) const;
```

### <a name="parameters"></a>Parameter

*wrow*<br/>
Die einbasierte Position einer Zeile im aktuellen Rowset. Dieser Wert kann zwischen 1 und der Größe des Rowsets liegen.

### <a name="return-value"></a>Rückgabewert

Ein Statuswert für die Zeile. Einzelheiten finden Sie unter "Hinweise".

### <a name="remarks"></a>Bemerkungen

`GetRowStatus`Gibt einen Wert zurück, der entweder jede Änderung des Status der Zeile seit dem letzten Abrufen aus der Datenquelle angibt, oder dass keine Zeile abgerufen wurde, die *wrow* entspricht. In der folgenden Tabelle sind die möglichen Rückgabewerte aufgelistet:

|Statuswert|BESCHREIBUNG|
|------------------|-----------------|
|SQL_ROW_SUCCESS|Die Zeile ist unverändert.|
|SQL_ROW_UPDATED|Die Zeile wurde aktualisiert.|
|SQL_ROW_DELETED|Die Zeile wurde gelöscht.|
|SQL_ROW_ADDED|Die Zeile wurde hinzugefügt.|
|SQL_ROW_ERROR|Die Zeile kann aufgrund eines Fehlers nicht abgerufen werden.|
|SQL_ROW_NOROW|Es gibt keine Zeile, die *wrow*entspricht.|

Weitere Informationen finden Sie unter der ODBC-API-Funktion `SQLExtendedFetch` in der Windows SDK.

## <a name="crecordsetgetstatus"></a><a name="getstatus"></a>CRecordset:: GetStatus

Bestimmt den Index des aktuellen Datensatzes im Recordset und gibt an, ob der letzte Datensatz erkannt wurde.

```cpp
void GetStatus(CRecordsetStatus& rStatus) const;
```

### <a name="parameters"></a>Parameter

*rstatus*<br/>
Ein Verweis auf ein `CRecordsetStatus`-Objekt. Weitere Informationen finden Sie im Abschnitt zu den Hinweisen.

### <a name="remarks"></a>Bemerkungen

`CRecordset`versucht, den Index zu verfolgen, unter bestimmten Umständen ist dies jedoch möglicherweise nicht möglich. Eine Erläuterung finden Sie unter [GetRecordCount](#getrecordcount) .

Die `CRecordsetStatus` Struktur weist die folgende Form auf:

```cpp
struct CRecordsetStatus
{
    long m_lCurrentRecord;
    BOOL m_bRecordCountFinal;
};
```

Die beiden Member von `CRecordsetStatus` haben die folgenden Bedeutungen:

- `m_lCurrentRecord`Enthält den NULL basierten Index des aktuellen Datensatzes im Recordset, sofern bekannt. Wenn der Index nicht bestimmt werden kann, enthält dieser Member AFX_CURRENT_RECORD_UNDEFINED (-2). Wenn `IsBOF` true ist (leeres Recordset oder Versuch, vor dem ersten Datensatz zu scrollen), `m_lCurrentRecord` wird auf AFX_CURRENT_RECORD_BOF (-1) festgelegt. Wenn im ersten Datensatz auf 0, zweiter Datensatz 1 usw. festgelegt ist.

- `m_bRecordCountFinal`Ein Wert ungleich 0 (null), wenn die Gesamtanzahl der Datensätze im Recordset ermittelt wurde. Dies muss im Allgemeinen erreicht werden, indem am Anfang des Recordsets begonnen und aufgerufen wird, bis den Wert ungleich `MoveNext` `IsEOF` 0 (null) zurückgibt. Wenn dieser Member 0 (null) ist, ist die Anzahl der von zurückgegebenen Daten `GetRecordCount` Sätze, wenn nicht-1, nur eine "hohe Grenze" der Datensätze.

## <a name="crecordsetgetsql"></a><a name="getsql"></a>CRecordset:: gezql

Mit dieser Member-Funktion können Sie die SQL-Anweisung abrufen, die zum Auswählen der Datensätze des Recordsets beim Öffnen verwendet wurde.

```
const CString& GetSQL() const;
```

### <a name="return-value"></a>Rückgabewert

Ein **`const`** Verweis auf eine `CString` , die die SQL-Anweisung enthält.

### <a name="remarks"></a>Bemerkungen

Dabei handelt es sich im Allgemeinen um eine SQL- **Select** -Anweisung. Die von zurückgegebene Zeichenfolge ist schreibgeschützt `GetSQL` .

Die von zurückgegebene Zeichenfolge `GetSQL` unterscheidet sich in der Regel von jeder Zeichenfolge, die Sie möglicherweise an das Recordset im *lpszSQL* -Parameter an die Member-Funktion übergeben haben `Open` . Dies liegt daran, dass das Recordset eine vollständige SQL-Anweisung erstellt, basierend auf dem, das Sie an weitergegeben haben `Open` , was Sie mit ClassWizard angegeben haben, was Sie möglicherweise in den `m_strFilter` Datenmembern und angegeben haben und welche `m_strSort` Parameter Sie möglicherweise angegeben haben. Ausführliche Informationen dazu, wie das Recordset diese SQL-Anweisung erstellt, finden [Sie im Artikel Recordset: Wie Recordsets Select Records (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

> [!NOTE]
> Diese Member-Funktion nur aufrufen, nachdem Sie [geöffnet](#open)aufgerufen haben.

## <a name="crecordsetgettablename"></a><a name="gettablename"></a>CRecordset:: GetTableName

Ruft den Namen der SQL-Tabelle ab, auf der die Abfrage des Recordsets basiert.

```
const CString& GetTableName() const;
```

### <a name="return-value"></a>Rückgabewert

Ein **`const`** Verweis auf einen `CString` , der den Tabellennamen enthält, wenn das Recordset auf einer Tabelle basiert, andernfalls eine leere Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

`GetTableName`ist nur gültig, wenn das Recordset auf einer Tabelle basiert, nicht auf einem Join mehrerer Tabellen oder einer vordefinierten Abfrage (gespeicherte Prozedur). Der Name ist schreibgeschützt.

> [!NOTE]
> Diese Member-Funktion nur aufrufen, nachdem Sie [geöffnet](#open)aufgerufen haben.

## <a name="crecordsetisbof"></a><a name="isbof"></a>CRecordset:: IsBOF

Gibt einen Wert ungleich 0 (null) zurück, wenn das Recordset vor dem ersten Datensatz positioniert wurde. Es ist kein aktueller Datensatz vorhanden.

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Recordset keine Datensätze enthält oder wenn Sie vor dem ersten Datensatz einen Rollup durchgeführt haben. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Nennen Sie diese Member-Funktion, bevor Sie einen Bildlauf von Datensatz zu Datensatz durchführen, um zu erfahren, ob Sie vor dem ersten Datensatz des Recordsets gegangen sind. Sie können auch `IsBOF` zusammen mit verwenden `IsEOF` , um zu bestimmen, ob das Recordset Datensätze enthält oder leer ist. `Open`Wenn das Recordset keine Datensätze enthält, wird unmittelbar nach dem-Befehl ein Wert ungleich `IsBOF` NULL zurückgegeben. Wenn Sie ein Recordset öffnen, das mindestens einen Datensatz enthält, ist der erste Datensatz der aktuelle Datensatz und `IsBOF` gibt 0 zurück.

Wenn es sich bei dem ersten Datensatz um den aktuellen Datensatz handelt und Sie den Befehl aufzurufen, wird von ein Wert ungleich `MovePrev` `IsBOF` 0 Wenn `IsBOF` einen Wert ungleich 0 (null) zurückgibt und Sie aufzurufen `MovePrev` , tritt ein Fehler Wenn `IsBOF` einen Wert ungleich 0 (null) zurückgibt, ist der aktuelle Datensatz nicht definiert, und jede Aktion, die einen aktuellen Datensatz erfordert, führt zu einem Fehler.

### <a name="example"></a>Beispiel

In diesem Beispiel werden `IsBOF` und verwendet `IsEOF` , um die Grenzwerte eines Recordsets zu erkennen, während der Code das Recordset in beide Richtungen durchläuft.

[!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]

## <a name="crecordsetisdeleted"></a><a name="isdeleted"></a>CRecordset:: isDeleted

Bestimmt, ob der aktuelle Datensatz gelöscht wurde.

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Recordset auf einem gelöschten Datensatz positioniert ist. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn Sie einen Bildlauf zu einem Datensatz `IsDeleted` ausführen und true (nicht null) zurückgeben, müssen Sie einen Bildlauf zu einem anderen Datensatz ausführen, bevor Sie andere recordsetvorgänge ausführen können.

Das Ergebnis von `IsDeleted` hängt von vielen Faktoren ab, z. b. vom Recordsettyp, davon, ob das Recordset aktualisierbar ist, ob Sie die `CRecordset::skipDeletedRecords` Option beim Öffnen des Recordsets angegeben haben, ob der Treiber gelöschte Datensätze verpackt hat und ob mehrere Benutzer vorhanden sind.

Weitere Informationen zu `CRecordset::skipDeletedRecords` und der Treiber Verpackung finden Sie in der [Open](#open) Member-Funktion.

> [!NOTE]
> Wenn Sie das Massen Abrufen von Zeilen implementiert haben, sollten Sie nicht aufzurufen `IsDeleted` . Aufrufen Sie stattdessen die [GetRowStatus](#getrowstatus) -Member-Funktion. Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetiseof"></a><a name="iseof"></a>CRecordset:: IsEOF

Gibt einen Wert ungleich 0 (null) zurück, wenn das Recordset nach dem letzten Datensatz positioniert wurde. Es ist kein aktueller Datensatz vorhanden.

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Recordset keine Datensätze enthält oder wenn Sie einen Rollup über den letzten Datensatz ausgeführt haben. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Nennen Sie diese Member-Funktion, während Sie einen Bildlauf von Datensatz zu Datensatz durchführen, um zu erfahren, ob Sie den letzten Datensatz des Recordsets überschritten haben. Sie können auch verwenden `IsEOF` , um zu bestimmen, ob das Recordset Datensätze enthält oder leer ist. `Open`Wenn das Recordset keine Datensätze enthält, wird unmittelbar nach dem-Befehl ein Wert ungleich `IsEOF` NULL zurückgegeben. Wenn Sie ein Recordset öffnen, das mindestens einen Datensatz enthält, ist der erste Datensatz der aktuelle Datensatz und `IsEOF` gibt 0 zurück.

Wenn der letzte Datensatz der aktuelle Datensatz ist, wenn aufgerufen wird, gibt den Wert ungleich `MoveNext` `IsEOF` 0 (null) zurück. Wenn `IsEOF` einen Wert ungleich 0 (null) zurückgibt und Sie aufzurufen `MoveNext` , tritt ein Fehler Wenn `IsEOF` einen Wert ungleich 0 (null) zurückgibt, ist der aktuelle Datensatz nicht definiert, und jede Aktion, die einen aktuellen Datensatz erfordert, führt zu einem Fehler.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [IsBOF](#isbof).

## <a name="crecordsetisfielddirty"></a><a name="isfielddirty"></a>CRecordset:: IsFieldDirty

Bestimmt, ob das angegebene Feld Datenelement geändert wurde, seit " [Edit](#edit) " oder " [AddNew](#addnew) " aufgerufen wurde.

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>Parameter

*teuren*<br/>
Ein Zeiger auf den Felddatenmember, dessen Status Sie überprüfen möchten, oder NULL, um zu bestimmen, ob eines der Felder geändert wird.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0, wenn sich der angegebene Felddatenmember seit dem Aufruf von oder geändert hat `AddNew` `Edit` ; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Daten in allen modifizierten Felddatenmembern werden an den Datensatz in der Datenquelle übertragen, wenn der aktuelle Datensatz durch einen Rückruf der [Update](#update) Member-Funktion von `CRecordset` (nach einem-oder-Rückruf) aktualisiert wird `Edit` `AddNew` .

> [!NOTE]
> Diese Member-Funktion ist für Recordsets, die das Abrufen von Massen Zeilen verwenden, nicht anwendbar. Wenn Sie das Massen Abrufen von Zeilen implementiert haben, `IsFieldDirty` gibt immer false zurück und führt zu einer fehlgeschlagenen Assertion. Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Durch `IsFieldDirty` das Aufrufen von werden die Auswirkungen vorheriger Aufrufe von [SetFieldDirty](#setfielddirty) zurückgesetzt, da der geänderte Status des Felds erneut ausgewertet wird. Wenn sich `AddNew` der aktuelle Feldwert vom Pseudo-NULL-Wert unterscheidet, wird der Feld Status auf "Dirty" festgelegt. `Edit`Wenn der Feldwert vom zwischengespeicherten Wert abweicht, wird der Feld Status auf geändert festgelegt.

`IsFieldDirty`wird durch [DoFieldExchange](#dofieldexchange)implementiert.

Weitere Informationen zum Dirty-Flag finden Sie im Artikel [Recordset: Wie Recordsets Select Records (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

## <a name="crecordsetisfieldnull"></a><a name="isfieldnull"></a>CRecordset:: IsFieldNull

Gibt einen Wert ungleich 0 (null) zurück, wenn das angegebene Feld im aktuellen Datensatz NULL ist (weist keinen Wert auf).

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>Parameter

*teuren*<br/>
Ein Zeiger auf den Felddatenmember, dessen Status Sie überprüfen möchten, oder NULL, um zu bestimmen, ob eines der Felder NULL ist.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn der angegebene Felddatenmember als NULL gekennzeichnet ist. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Mit dieser Member-Funktion können Sie ermitteln, ob der angegebene Felddatenmember eines Recordsets als NULL gekennzeichnet wurde. (In der Daten Bank Terminologie bedeutet NULL, dass kein Wert vorhanden ist, und ist nicht mit NULL in C++ identisch.) Wenn ein Felddatenmember als NULL gekennzeichnet ist, wird er als Spalte des aktuellen Datensatzes interpretiert, für den kein Wert vorhanden ist.

> [!NOTE]
> Diese Member-Funktion ist für Recordsets, die das Abrufen von Massen Zeilen verwenden, nicht anwendbar. Wenn Sie das Massen Abrufen von Zeilen implementiert haben, `IsFieldNull` gibt immer false zurück und führt zu einer fehlgeschlagenen Assertion. Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`IsFieldNull`wird durch [DoFieldExchange](#dofieldexchange)implementiert.

## <a name="crecordsetisfieldnullable"></a><a name="isfieldnullable"></a>CRecordset:: IsFieldNullable

Gibt einen Wert ungleich 0 (null) zurück, wenn das angegebene Feld im aktuellen Datensatz auf NULL (ohne Wert) festgelegt werden kann.

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>Parameter

*teuren*<br/>
Ein Zeiger auf den Felddatenmember, dessen Status Sie überprüfen möchten, oder NULL, um zu bestimmen, ob eines der Felder auf einen NULL-Wert festgelegt werden kann.

### <a name="remarks"></a>Bemerkungen

Mit dieser Member-Funktion wird bestimmt, ob der angegebene Felddatenmember "Nullable" ist (kann auf einen NULL-Wert festgelegt werden; C++ NULL ist nicht identisch mit NULL, was in der Daten Bank Terminologie bedeutet, dass kein Wert vorhanden ist.)

> [!NOTE]
> Wenn Sie das Massen Abrufen von Zeilen implementiert haben, können Sie nicht aufzurufen `IsFieldNullable` . Aufrufen Sie stattdessen die Member-Funktion von [GetODBCFieldInfo](#getodbcfieldinfo) , um zu bestimmen, ob ein Feld auf einen NULL-Wert festgelegt werden kann. Beachten Sie, dass Sie immer abrufen können `GetODBCFieldInfo` , unabhängig davon, ob Sie das Massen Abrufen von Zeilen implementiert haben. Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Ein Feld, das nicht NULL sein kann, muss über einen Wert verfügen. Wenn Sie versuchen, ein solches Feld beim Hinzufügen oder Aktualisieren eines Datensatzes auf NULL festzulegen, lehnt die Datenquelle das Hinzufügen oder aktualisieren ab, und die [Aktualisierung](#update) löst eine Ausnahme aus. Die Ausnahme tritt auf, wenn Sie aufrufen `Update` , nicht beim Aufrufen von [SetFieldNull](#setfieldnull).

Wenn NULL für das erste Argument der Funktion verwendet wird, wird die Funktion nur auf `outputColumn` Felder, nicht auf `param` Felder angewendet. Beispielsweise ist der-Befehl

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

legt nur `outputColumn` Felder auf NULL fest `param` . Felder sind nicht betroffen.

Zum Bearbeiten von `param` Feldern müssen Sie die tatsächliche Adresse der Person angeben `param` , an der Sie arbeiten möchten, z. b.:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

Dies bedeutet, dass Sie nicht alle `param` Felder wie bei Feldern auf NULL festlegen können `outputColumn` .

`IsFieldNullable`wird durch [DoFieldExchange](#dofieldexchange)implementiert.

## <a name="crecordsetisopen"></a><a name="isopen"></a>CRecordset:: IsOpen

Bestimmt, ob das Recordset bereits geöffnet ist.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn die [Open](#open) -oder [Requery](#requery) -Member-Funktion des Recordset-Objekts zuvor aufgerufen wurde und das Recordset nicht geschlossen wurde. andernfalls 0.

## <a name="crecordsetm_hstmt"></a><a name="m_hstmt"></a>CRecordset:: m_hstmt

Enthält ein Handle für die Datenstruktur der ODBC-Anweisung vom Typ HSTMT, die dem Recordset zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Jede Abfrage an eine ODBC-Datenquelle ist einem hstmt zugeordnet.

> [!CAUTION]
> Nicht verwenden, `m_hstmt` bevor [Open](#open) aufgerufen wurde.

Normalerweise müssen Sie nicht direkt auf das hstmt zugreifen, Sie benötigen es jedoch möglicherweise für die direkte Ausführung von SQL-Anweisungen. Die `ExecuteSQL` Member-Funktion der-Klasse `CDatabase` bietet ein Beispiel für die Verwendung von `m_hstmt` .

## <a name="crecordsetm_nfields"></a><a name="m_nfields"></a>CRecordset:: m_nFields

Enthält die Anzahl der Felddatenmember in der Recordset-Klasse. Das heißt, die Anzahl der Spalten, die vom Recordset aus der Datenquelle ausgewählt werden.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor für die Recordset-Klasse muss `m_nFields` mit der richtigen Zahl initialisiert werden. Wenn Sie das Massen Abrufen von Zeilen nicht implementiert haben, schreibt ClassWizard diese Initialisierung für Sie, wenn Sie Sie zum Deklarieren der Recordsetklasse verwenden. Sie können Sie auch manuell schreiben.

Das Framework verwendet diese Zahl, um die Interaktion zwischen den Felddatenmembern und den entsprechenden Spalten des aktuellen Datensatzes in der Datenquelle zu verwalten.

> [!CAUTION]
> Diese Zahl muss der Anzahl der "Output Columns" entsprechen, die in `DoFieldExchange` oder `DoBulkFieldExchange` nach einem Aufrufen von [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) mit dem-Parameter registriert ist `CFieldExchange::outputColumn` .

Sie können Spalten dynamisch binden, wie im Artikel "Recordset: Dynamisches Binden von Datenspalten" erläutert. Wenn Sie dies tun, müssen Sie die Anzahl in erhöhen, `m_nFields` um die Anzahl von RFX-oder Bulk-RFX-Funktionsaufrufen in `DoFieldExchange` der-oder-Member- `DoBulkFieldExchange` Funktion für die dynamisch gebundenen Spalten widerzuspiegeln.

Weitere Informationen finden Sie in den Artikeln [Recordset: Dynamisches Binden von Datenspalten (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) und [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Beispiel

Weitere Informationen finden [Sie im Artikeldaten Satz Feld Austausch: Verwenden von RFX](../../data/odbc/record-field-exchange-using-rfx.md).

## <a name="crecordsetm_nparams"></a><a name="m_nparams"></a>CRecordset:: m_nParams

Enthält die Anzahl der Parameterdatenmember in der Recordset-Klasse. Das heißt, die Anzahl der Parameter, die mit der Abfrage des Recordsets übermittelt werden.

### <a name="remarks"></a>Bemerkungen

Wenn die Recordsetklasse über Parameter Datenmember verfügt, muss der Konstruktor für die Klasse `m_nParams` mit der richtigen Zahl initialisiert werden. Der Wert von ist `m_nParams` standardmäßig 0. Wenn Sie Parameter Datenmember hinzufügen (was Sie manuell tun müssen), müssen Sie auch manuell eine Initialisierung im Klassenkonstruktor hinzufügen, um die Anzahl von Parametern (die mindestens so groß wie die Anzahl der Platzhalter in der- `m_strFilter` oder-Zeichenfolge sein muss) wiederzugeben `m_strSort` .

Das Framework verwendet diese Zahl, wenn die Abfrage des Recordsets parametrisiert wird.

> [!CAUTION]
> Diese Zahl muss der Anzahl von "Parametern" entsprechen, die in `DoFieldExchange` oder `DoBulkFieldExchange` nach einem Aufrufen von [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) mit dem Parameterwert `CFieldExchange::inputParam` , `CFieldExchange::param` , `CFieldExchange::outputParam` oder `CFieldExchange::inoutParam` registriert wurde.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie in den Artikeln [Recordset: parametrialisieren eines Recordsets (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) und [Daten Satz Feld Austausch: Verwenden von RFX](../../data/odbc/record-field-exchange-using-rfx.md).

## <a name="crecordsetm_pdatabase"></a><a name="m_pdatabase"></a>CRecordset:: m_pDatabase

Enthält einen Zeiger auf das- `CDatabase` Objekt, über das das Recordset mit einer Datenquelle verbunden ist.

### <a name="remarks"></a>Bemerkungen

Diese Variable wird auf zwei Arten festgelegt. In der Regel übergeben Sie einen Zeiger auf ein bereits verbundenes `CDatabase` Objekt, wenn Sie das Recordset-Objekt erstellen. Wenn Sie stattdessen NULL übergeben, `CRecordset` erstellt ein `CDatabase` -Objekt für Sie und verbindet es. In beiden Fällen `CRecordset` speichert den Zeiger in dieser Variablen.

Normalerweise müssen Sie den in gespeicherten Zeiger nicht direkt verwenden `m_pDatabase` . Wenn Sie jedoch eigene Erweiterungen in schreiben, `CRecordset` müssen Sie möglicherweise den-Zeiger verwenden. Beispielsweise können Sie den-Zeiger benötigen, wenn Sie Ihre eigenen `CDBException` s auslösen. Oder Sie benötigen es, wenn Sie ein Objekt mit demselben Objekt ausführen müssen `CDatabase` , z. b. das Ausführen von Transaktionen, das Festlegen von Timeouts oder das Aufrufen der `ExecuteSQL` Member-Funktion der-Klasse, `CDatabase` um SQL-Anweisungen direkt auszuführen.

## <a name="crecordsetm_strfilter"></a><a name="m_strfilter"></a>CRecordset:: m_strFilter

Verwenden Sie nach dem Erstellen des Recordset-Objekts, aber bevor Sie seine Member-Funktion aufzurufen `Open` , dieses Datenmember, um eine `CString` mit einer SQL- **Where** -Klausel zu speichern.

### <a name="remarks"></a>Bemerkungen

Das Recordset verwendet diese Zeichenfolge, um die Datensätze einzuschränken (oder zu filtern), die während der-oder-Aufrufe ausgewählt werden `Open` `Requery` . Dies ist nützlich, wenn Sie eine Teilmenge der Datensätze auswählen, z. b. "alle Vertriebsmitarbeiter, die in Kalifornien basieren" ("State = ca"). Die ODBC-SQL-Syntax für eine **Where** -Klausel lautet:

`WHERE search-condition`

Beachten Sie, dass Sie das **Where** -Schlüsselwort nicht in die Zeichenfolge einschließen. Das Framework stellt es bereit.

Sie können auch die Filter Zeichenfolge parametrisieren, indem Sie ""-Platzhalter darin platzieren, einen Parameter Datenmember in der Klasse für jeden Platzhalter deklarieren und Parameter zur Laufzeit an das Recordset übergeben. Auf diese Weise können Sie den Filter zur Laufzeit erstellen. Weitere Informationen finden Sie im Artikel [Recordset: parametrialisieren eines Recordsets (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

Weitere Informationen zu SQL- **Where** -Klauseln finden Sie im Artikel [SQL](../../data/odbc/sql.md). Weitere Informationen zum auswählen und Filtern von Datensätzen finden Sie im Artikel [Recordset: Filtern von Datensätzen (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]

## <a name="crecordsetm_strsort"></a><a name="m_strsort"></a>CRecordset:: m_strSort

Nachdem Sie das Recordset-Objekt erstellt haben, aber bevor Sie seine Member-Funktion aufzurufen `Open` , speichern Sie mit diesem Datenmember ein, das `CString` eine SQL **Order by** -Klausel enthält.

### <a name="remarks"></a>Bemerkungen

Das Recordset verwendet diese Zeichenfolge zum Sortieren der Datensätze, die während des- `Open` oder- `Requery` Aufrufes ausgewählt werden Mit dieser Funktion können Sie ein Recordset nach einer oder mehreren Spalten sortieren. Die ODBC-SQL-Syntax für eine **Order by** -Klausel lautet:

`ORDER BY sort-specification [, sort-specification]...`

Dabei ist eine Sort-Specification eine Ganzzahl oder ein Spaltenname. Sie können auch eine aufsteigende oder absteigende Reihenfolge angeben (die Reihenfolge ist standardmäßig aufsteigend), indem Sie "ASC" oder "de SC" an die Spaltenliste in der Sortier Zeichenfolge anhängen. Die ausgewählten Datensätze werden zuerst nach der ersten aufgeführten Spalte, dann nach der zweiten Spalte usw. sortiert. Beispielsweise können Sie einen "Customers"-Recordset nach Nachnamen und dann nach "Vorname" anordnen. Die Anzahl der Spalten, die Sie auflisten können, hängt von der Datenquelle ab. Weitere Informationen finden Sie unter Windows SDK.

Beachten Sie, dass Sie das **Order by** -Schlüsselwort nicht in die Zeichenfolge einschließen. Das Framework stellt es bereit.

Weitere Informationen zu SQL-Klauseln finden Sie im Artikel [SQL](../../data/odbc/sql.md). Weitere Informationen zum Sortieren von Datensätzen finden Sie im Artikel [Recordset: Sortieren von Datensätzen (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]

## <a name="crecordsetmove"></a><a name="move"></a>CRecordset:: Move

Verschiebt den aktuellen Daten Satz Zeiger innerhalb des Recordsets (vorwärts oder rückwärts).

```
virtual void Move(
    long nRows,
    WORD wFetchType = SQL_FETCH_RELATIVE);
```

### <a name="parameters"></a>Parameter

*nRows*<br/>
Die Anzahl der Zeilen, für die vorwärts oder rückwärts verschoben werden soll. Positive Werte werden vorwärts bis zum Ende des Recordsets verschoben. Negative Werte werden nach hinten verschoben.

*wfetchtype*<br/>
Bestimmt das Rowset, das abgerufen `Move` wird. Einzelheiten finden Sie unter "Hinweise".

### <a name="remarks"></a>Bemerkungen

Wenn Sie für *nrows*den Wert 0 übergeben, `Move` wird der aktuelle Datensatz aktualisiert; `Move` jeder aktuelle- `AddNew` oder-Modus wird beendet `Edit` , und der Wert des aktuellen Datensatzes wird vor `AddNew` oder `Edit` aufgerufen.

> [!NOTE]
> Wenn Sie ein Recordset durchlaufen, können Sie gelöschte Datensätze nicht überspringen. Weitere Informationen finden Sie unter [CRecordset:: IsDeleted](#isdeleted) . Wenn Sie einen `CRecordset` mit der `skipDeletedRecords` Option Set öffnen, `Move` wird bestätigt, wenn der *nrows* -Parameter den Wert 0 hat. Dieses Verhalten verhindert die Aktualisierung von Zeilen, die von anderen Client Anwendungen mit denselben Daten gelöscht werden. Eine Beschreibung von finden Sie unter dem *dwOption* -Parameter in [Open](#open) `skipDeletedRecords` .

`Move`positioniert das Recordset nach Rowsets. Ruft basierend auf den Werten für *nrows* und *wfetchtype* `Move` das entsprechende Rowset ab und erstellt dann den ersten Datensatz in diesem Rowset mit dem aktuellen Datensatz. Wenn Sie das Massen Abrufen von Zeilen nicht implementiert haben, ist die Rowsetgröße immer 1. Beim Abrufen eines Rowsets `Move` ruft direkt die [checkrowseterror](#checkrowseterror) -Member-Funktion auf, um alle Fehler zu behandeln, die durch das Abrufen entstehen.

Abhängig von den Werten, die Sie übergeben, `Move` entspricht anderen Element `CRecordset` Funktionen. Insbesondere kann der Wert von *wfetchtype* auf eine Element Funktion hindeuten, die intuitiver und häufig die bevorzugte Methode zum Verschieben des aktuellen Datensatzes ist.

In der folgenden Tabelle sind die möglichen Werte für *wfetchtype*, das Rowset, das auf der `Move` Grundlage von *wfetchtype* und *nrows*abgerufen wird, sowie alle äquivalenten Member-Funktionen, die *wfetchtype*entsprechen, aufgeführt.

|wfetchtype|Abgerufene Rowset|Äquivalente Member-Funktion|
|----------------|--------------------|--------------------------------|
|SQL_FETCH_RELATIVE (Standardwert)|Das Rowset, das *nrows* -Zeile (n) aus der ersten Zeile im aktuellen Rowset startet.||
|SQL_FETCH_NEXT|Das nächste Rowset; *nrows* wird ignoriert.|[MoveNext](#movenext)|
|SQL_FETCH_PRIOR|Das vorherige Rowset; *nrows* wird ignoriert.|[MovePrev](#moveprev)|
|SQL_FETCH_FIRST|Das erste Rowset im Recordset. *nrows* wird ignoriert.|[MoveFirst](#movefirst)|
|SQL_FETCH_LAST|Das letzte komplette Rowset im Recordset. *nrows* wird ignoriert.|[MoveLast](#movelast)|
|SQL_FETCH_ABSOLUTE|Wenn *nrows* > 0, beginnt das Rowset mit *nrows* -Zeile (n) vom Anfang des Recordsets. Wenn *nrows* < 0 ist, beginnt das Rowset mit *nrows* -Zeile (n) vom Ende des Recordsets. Wenn *nrows* = 0 ist, wird eine Dateityp-Bedingung (BOF) zurückgegeben.|["Settabsoluteposition"](#setabsoluteposition)|
|SQL_FETCH_BOOKMARK|Das Rowset, beginnend bei der Zeile, deren Lesezeichen Wert *nrows*entspricht.|[SetBookmark](#setbookmark)|

> [!NOTE]
> Für Vorwärts-Recordsets `Move` ist nur mit dem Wert SQL_FETCH_NEXT für *wfetchtype*gültig.

> [!CAUTION]
> Durch Aufrufen von `Move` wird eine Ausnahme ausgelöst, wenn das Recordset keine Datensätze enthält. Um zu ermitteln, ob das Recordset über Datensätze verfügt, wenden Sie [IsBOF](#isbof) und [IsEOF](#iseof)an.

> [!NOTE]
> Wenn Sie einen Rollup über den Anfang oder das Ende des Recordsets durchgeführt haben ( `IsBOF` oder einen Wert ungleich `IsEOF` NULL zurückgibt), löst der Aufruf einer `Move` Funktion möglicherweise eine aus `CDBException` . Wenn beispielsweise einen Wert ungleich `IsEOF` 0 (null) zurückgibt `IsBOF` , der nicht ist, `MoveNext` wird eine Ausnahme ausgelöst, aber `MovePrev` nicht.

> [!NOTE]
> Wenn Sie `Move` beim Aktualisieren des aktuellen Datensatzes oder beim Hinzufügen des aktuellen Datensatzes aufzurufen, gehen die Aktualisierungen ohne Warnung verloren.

Weitere Informationen zur Recordsetnavigation finden Sie in den Artikeln [Recordset: Scroll (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) und [Recordset: Lesezeichen und absolute Positionen (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Weitere Informationen finden Sie unter der ODBC-API-Funktion `SQLExtendedFetch` in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]

## <a name="crecordsetmovefirst"></a><a name="movefirst"></a>CRecordset:: muvefirst

Legt den ersten Datensatz im ersten Rowset als aktuellen Datensatz fest.

```cpp
void MoveFirst();
```

### <a name="remarks"></a>Bemerkungen

Unabhängig davon, ob das Massen Abrufen von Zeilen implementiert wurde, ist dies immer der erste Datensatz im Recordset.

Sie müssen nicht `MoveFirst` sofort nach dem Öffnen des Recordsets aufzurufen. Zu diesem Zeitpunkt ist der erste Datensatz (sofern vorhanden) automatisch der aktuelle Datensatz.

> [!NOTE]
> Diese Member-Funktion ist für Vorwärts-Recordsets ungültig.

> [!NOTE]
> Wenn Sie ein Recordset durchlaufen, können Sie gelöschte Datensätze nicht überspringen. Ausführliche Informationen finden Sie in der [isDeleted](#isdeleted) -Member-Funktion.

> [!CAUTION]
> Wenn Sie eine der `Move` Funktionen aufrufen, wird eine Ausnahme ausgelöst, wenn das Recordset keine Datensätze enthält. Um zu ermitteln, ob das Recordset über Datensätze verfügt, müssen Sie und aufzurufen `IsBOF` `IsEOF` .

> [!NOTE]
> Wenn Sie eine der Funktionen aufzurufen `Move` , während der aktuelle Datensatz aktualisiert oder hinzugefügt wird, gehen die Aktualisierungen ohne Warnung verloren.

Weitere Informationen zur Recordsetnavigation finden Sie in den Artikeln [Recordset: Scroll (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) und [Recordset: Lesezeichen und absolute Positionen (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [IsBOF](#isbof).

## <a name="crecordsetmovelast"></a><a name="movelast"></a>CRecordset:: muvelast

Erstellt den ersten Datensatz im letzten abgeschlossenen Rowset zum aktuellen Datensatz.

```cpp
void MoveLast();
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie das Massen Abrufen von Zeilen nicht implementiert haben, hat das Recordset die Rowsetgröße 1, sodass Sie `MoveLast` einfach zum letzten Datensatz im Recordset wechselt.

> [!NOTE]
> Diese Member-Funktion ist für Vorwärts-Recordsets ungültig.

> [!NOTE]
> Wenn Sie ein Recordset durchlaufen, können Sie gelöschte Datensätze nicht überspringen. Ausführliche Informationen finden Sie in der [isDeleted](#isdeleted) -Member-Funktion.

> [!CAUTION]
> Wenn Sie eine der `Move` Funktionen aufrufen, wird eine Ausnahme ausgelöst, wenn das Recordset keine Datensätze enthält. Um zu ermitteln, ob das Recordset über Datensätze verfügt, müssen Sie und aufzurufen `IsBOF` `IsEOF` .

> [!NOTE]
> Wenn Sie eine der Funktionen aufzurufen `Move` , während der aktuelle Datensatz aktualisiert oder hinzugefügt wird, gehen die Aktualisierungen ohne Warnung verloren.

Weitere Informationen zur Recordsetnavigation finden Sie in den Artikeln [Recordset: Scroll (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) und [Recordset: Lesezeichen und absolute Positionen (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [IsBOF](#isbof).

## <a name="crecordsetmovenext"></a><a name="movenext"></a>CRecordset:: wvenext

Führt den ersten Datensatz im nächsten Rowset zum aktuellen Datensatz.

```cpp
void MoveNext();
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie das Massen Abrufen von Zeilen nicht implementiert haben, hat das Recordset eine Rowsetgröße von 1, sodass Sie `MoveNext` einfach zum nächsten Datensatz wechselt.

> [!NOTE]
> Wenn Sie ein Recordset durchlaufen, können Sie gelöschte Datensätze nicht überspringen. Ausführliche Informationen finden Sie in der [isDeleted](#isdeleted) -Member-Funktion.

> [!CAUTION]
> Wenn Sie eine der `Move` Funktionen aufrufen, wird eine Ausnahme ausgelöst, wenn das Recordset keine Datensätze enthält. Um zu ermitteln, ob das Recordset über Datensätze verfügt, müssen Sie und aufzurufen `IsBOF` `IsEOF` .

> [!NOTE]
> Es wird auch empfohlen, vor dem Aufruf von aufzurufen `IsEOF` `MoveNext` . Wenn Sie z. b. einen Rollup über das Ende des Recordsets durchgeführt haben, `IsEOF` gibt einen Wert ungleich 0 (null) zurück. ein nachfolgende-Befehl löst `MoveNext` eine Ausnahme aus.

> [!NOTE]
> Wenn Sie eine der Funktionen aufzurufen `Move` , während der aktuelle Datensatz aktualisiert oder hinzugefügt wird, gehen die Aktualisierungen ohne Warnung verloren.

Weitere Informationen zur Recordsetnavigation finden Sie in den Artikeln [Recordset: Scroll (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) und [Recordset: Lesezeichen und absolute Positionen (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [IsBOF](#isbof).

## <a name="crecordsetmoveprev"></a><a name="moveprev"></a>CRecordset:: weprev

Führt den ersten Datensatz im vorherigen Rowset zum aktuellen Datensatz.

```cpp
void MovePrev();
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie das Massen Abrufen von Zeilen nicht implementiert haben, hat das Recordset eine Rowsetgröße von 1, sodass Sie `MovePrev` einfach zum vorherigen Datensatz wechselt.

> [!NOTE]
> Diese Member-Funktion ist für Vorwärts-Recordsets ungültig.

> [!NOTE]
> Wenn Sie ein Recordset durchlaufen, können Sie gelöschte Datensätze nicht überspringen. Ausführliche Informationen finden Sie in der [isDeleted](#isdeleted) -Member-Funktion.

> [!CAUTION]
> Wenn Sie eine der `Move` Funktionen aufrufen, wird eine Ausnahme ausgelöst, wenn das Recordset keine Datensätze enthält. Um zu ermitteln, ob das Recordset über Datensätze verfügt, müssen Sie und aufzurufen `IsBOF` `IsEOF` .

> [!NOTE]
> Es wird auch empfohlen, vor dem Aufruf von aufzurufen `IsBOF` `MovePrev` . Wenn Sie z. b. vor dem Anfang des Recordsets einen Rollup durchgeführt haben, `IsBOF` gibt einen Wert ungleich 0 (null) zurück. bei einem nachfolgenden-Befehl wird `MovePrev` eine Ausnahme ausgelöst.

> [!NOTE]
> Wenn Sie eine der Funktionen aufzurufen `Move` , während der aktuelle Datensatz aktualisiert oder hinzugefügt wird, gehen die Aktualisierungen ohne Warnung verloren.

Weitere Informationen zur Recordsetnavigation finden Sie in den Artikeln [Recordset: Scroll (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) und [Recordset: Lesezeichen und absolute Positionen (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [IsBOF](#isbof).

## <a name="crecordsetonsetoptions"></a><a name="onsetoptions"></a>CRecordset:: OnSetOptions

Wird aufgerufen, um Optionen für die angegebene ODBC-Anweisung festzulegen (bei Auswahl verwendet).

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parameter

*hstmt*<br/>
Das hstmt der ODBC-Anweisung, deren Optionen festgelegt werden sollen.

### <a name="remarks"></a>Bemerkungen

Ruft `OnSetOptions` für die angegebene ODBC-Anweisung den SET-Optionen auf (bei Auswahl verwendet). Das Framework ruft diese Member-Funktion auf, um die anfänglichen Optionen für das Recordset festzulegen. `OnSetOptions`bestimmt die Unterstützung der Datenquelle für scrollbare Cursor und für die Cursor Parallelität und legt die Optionen des Recordsets entsprechend fest. (Während `OnSetOptions` für Auswahl Vorgänge verwendet wird, `OnSetUpdateOptions` wird für Aktualisierungs Vorgänge verwendet.)

`OnSetOptions`Überschreiben Sie, um spezifische Optionen für den Treiber oder die Datenquelle festzulegen. Wenn Ihre Datenquelle z. b. das Öffnen für exklusiven Zugriff unterstützt, können Sie überschreiben, `OnSetOptions` um diese Möglichkeit zu nutzen.

Weitere Informationen zu Cursorn finden Sie im Artikel [ODBC](../../data/odbc/odbc-basics.md).

## <a name="crecordsetonsetupdateoptions"></a><a name="onsetupdateoptions"></a>CRecordset:: onsetupdateoptions

Wird aufgerufen, um Optionen für die angegebene ODBC-Anweisung festzulegen (bei Update verwendet).

```
virtual void OnSetUpdateOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parameter

*hstmt*<br/>
Das hstmt der ODBC-Anweisung, deren Optionen festgelegt werden sollen.

### <a name="remarks"></a>Bemerkungen

Ruft `OnSetUpdateOptions` beim Festlegen von Optionen (bei Update) für die angegebene ODBC-Anweisung auf. Das Framework ruft diese Member-Funktion auf, nachdem ein hstmt zum Aktualisieren von Datensätzen in einem Recordset erstellt wurde. (Wird `OnSetOptions` für Auswahl Vorgänge verwendet, `OnSetUpdateOptions` wird für Aktualisierungs Vorgänge verwendet.) `OnSetUpdateOptions` bestimmt die Unterstützung der Datenquelle für scrollbare Cursor und für die Cursor Parallelität und legt die Optionen des Recordsets entsprechend fest.

`OnSetUpdateOptions`Überschreiben Sie, um Optionen einer ODBC-Anweisung festzulegen, bevor diese Anweisung verwendet wird, um auf eine Datenbank zuzugreifen.

Weitere Informationen zu Cursorn finden Sie im Artikel [ODBC](../../data/odbc/odbc-basics.md).

## <a name="crecordsetopen"></a><a name="open"></a>CRecordset:: Open

Öffnet das Recordset, indem die Tabelle abgerufen oder die vom Recordset darstellte Abfrage durchgeführt wird.

```
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    DWORD dwOptions = none);
```

### <a name="parameters"></a>Parameter

*nOpenType*<br/>
Übernehmen Sie den Standardwert AFX_DB_USE_DEFAULT_TYPE, oder verwenden Sie einen der folgenden Werte aus `enum OpenType` :

- `CRecordset::dynaset`Ein Recordset mit bidirektionalem Bildlauf. Die Mitgliedschaft und die Reihenfolge der Datensätze werden beim Öffnen des Recordsets bestimmt. Die von anderen Benutzern an den Datenwerten vorgenommenen Änderungen sind nach einem Abrufvorgang allerdings sichtbar. Dynasets sind auch als keysetgesteuerte Recordsets bekannt.

- `CRecordset::snapshot`Ein statisches Recordset mit bidirektionalem Bildlauf. Die Mitgliedschaft und die Reihenfolge der Datensätze werden beim Öffnen des Recordsets und die Datenwerte beim Abrufen der Datensätze bestimmt. Die von anderen Benutzern vorgenommenen Änderungen sind nicht sichtbar, bis das Recordset geschlossen und erneut geöffnet wird.

- `CRecordset::dynamic`Ein Recordset mit bidirektionalem Bildlauf. Die von anderen Benutzern an der Mitgliedschaft, der Reihenfolge und den Datenwerten vorgenommen Änderungen sind nach einem Abrufvorgang sichtbar. Beachten Sie, dass dieser Recordsettyp von vielen ODBC-Treibern nicht unterstützt wird.

- `CRecordset::forwardOnly`Ein Schreib geschütztes Recordset mit nur vorwärts Bildlauf.

   `CRecordset`Der Standardwert für ist `CRecordset::snapshot` . Mithilfe des Standardwertmechanismus kann bei Visual C++-Assistenten mit ODBC-`CRecordset` sowie DAO- `CDaoRecordset`, die über unterschiedliche Standardwerte verfügen, interagiert werden.

Weitere Informationen zu diesen recordsettypen finden Sie im Artikel [Recordset (ODBC)](../../data/odbc/recordset-odbc.md). Weitere Informationen finden Sie im Artikel "Verwenden von Block-und scrollfähigen Cursorn" in der Windows SDK.

> [!CAUTION]
> Wenn der angeforderte Typ nicht unterstützt wird, löst das Framework eine Ausnahme aus.

*lpszSQL*<br/>
Eine Zeichenfolge, in der eines der folgenden Elemente enthalten ist:

- Ein NULL-Zeiger.

- Name der Tabelle

- Eine SQL- **Select** -Anweisung (optional mit einer SQL- **Where** -oder **Order by** -Klausel).

- Eine-Anweisung, die den **Namen einer vordefinierten** Abfrage (gespeicherte Prozedur) angibt. Achten Sie darauf, dass Sie keine Leerzeichen zwischen der geschweiften Klammer und dem **callschlüsselwort** einfügen.

Weitere Informationen zu dieser Zeichenfolge finden Sie in der Tabelle und in der Beschreibung der Rolle von ClassWizard im Abschnitt " [Hinweise](#remarks) ".

> [!NOTE]
> Die Reihenfolge der Spalten im Resultset muss mit der Reihenfolge der RFX-oder Bulk-RFX-Funktionsaufrufe in der [DoFieldExchange](#dofieldexchange) -Funktion oder der [DoBulkFieldExchange](#dobulkfieldexchange) -Funktion außer Kraft gesetzt werden.

*dwOptions*<br/>
Eine Bitmaske, die eine Kombination der unten aufgeführten Werte angeben kann. Einige davon schließen sich einander aus. Der Standardwert ist " **None**".

- `CRecordset::none`Es wurden keine Optionen festgelegt. Dieser Parameterwert und alle anderen Werte schließen einander aus. Standardmäßig kann das Recordset mit " [Bearbeiten](#edit) " oder " [Löschen](#delete) " aktualisiert werden und ermöglicht das Anfügen neuer Datensätze mit " [AddNew](#addnew)". Aktualisierbarkeit hängt von der Datenquelle und der von Ihnen angegebenen *nOpenType* -Option ab. Optimierung für Massenhinzufügeaktionen ist nicht verfügbar. Das gesammelte Abrufen von Zeilen wird nicht implementiert. Gelöschte Datensätze werden während der Recordsetnavigation nicht übersprungen. Lesezeichen sind nicht verfügbar. Automatische Überprüfung fehlerhafter Felder wird implementiert.

- `CRecordset::appendOnly`Lässt `Edit` `Delete` das Recordset oder nicht zu. Lassen Sie nur `AddNew` zu. Diese Option und `CRecordset::readOnly` schließen einander aus.

- `CRecordset::readOnly`Öffnen Sie das Recordset als schreibgeschützt. Diese Option und `CRecordset::appendOnly` schließen einander aus.

- `CRecordset::optimizeBulkAdd`Verwenden Sie eine vorbereitete SQL-Anweisung, um das Hinzufügen vieler Datensätze gleichzeitig zu optimieren. Gilt nur, wenn Sie die ODBC-API-Funktion nicht `SQLSetPos` zum Aktualisieren des Recordsets verwenden. Das erste Update bestimmt die geänderten Felder. Diese Option und `CRecordset::useMultiRowFetch` schließen einander aus.

- `CRecordset::useMultiRowFetch`Implementieren Sie das Massen Abrufen von Zeilen, damit mehrere Zeilen in einem einzelnen Abruf Vorgang abgerufen werden können. Das ist eine erweiterte Funktion, die zum Verbessern der Leistung entworfen wurde. Allerdings wird der Massenaustausch von Datensatzfeldern von ClassWizard nicht unterstützt. Diese Option und `CRecordset::optimizeBulkAdd` schließen einander aus. Beachten Sie Folgendes: Wenn Sie angeben `CRecordset::useMultiRowFetch` , wird die Option `CRecordset::noDirtyFieldCheck` automatisch aktiviert (doppelte Pufferung ist nicht verfügbar). bei Vorwärts Recordsets wird die Option `CRecordset::useExtendedFetch` automatisch aktiviert. Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

- `CRecordset::skipDeletedRecords`Alle gelöschten Datensätze beim Navigieren durch das Recordset überspringen. Das verlangsamt in bestimmten relativen Abrufen die Leistung. Diese Option ist bei forward-only-Recordsets ungültig. Wenn Sie [verschieben](#move) aufrufen, wobei der *nrows* -Parameter auf 0 festgelegt ist und die- `CRecordset::skipDeletedRecords` Option festgelegt ist, `Move` wird von Assert. Beachten Sie, dass die `CRecordset::skipDeletedRecords` *Treiber Verpackung*ähnlich ist, was bedeutet, dass gelöschte Zeilen aus dem Recordset entfernt werden. Wenn der Treiber allerdings Datensätze verpackt, werden nur die von Ihnen gelöschten Datensätze übersprungen. Die von anderen Benutzern gelöschten Datensätze werden nicht übersprungen, solange das Recordset geöffnet ist. `CRecordset::skipDeletedRecords`von werden von anderen Benutzern gelöschte Zeilen übersprungen.

- `CRecordset::useBookmarks`Verwendet möglicherweise Lesezeichen für das Recordset, sofern dies unterstützt wird. Lesezeichen verlangsamen den Datenabruf, verbessern aber die Leistung bei der Datennavigation. In forward-only-Recordsets ist das ungültig. Weitere Informationen finden Sie im Artikel [Recordset: Lesezeichen und absolute Positionen (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

- `CRecordset::noDirtyFieldCheck`Deaktivieren Sie die automatische Überprüfung auf geänderte Felder (doppelte Pufferung). Dadurch wird die Leistung verbessert. Sie müssen allerdings Felder manuell als geändert kennzeichnen, indem Sie die Memberfunktionen `SetFieldDirty` und `SetFieldNull` aufrufen. Beachten Sie, dass die doppelte Pufferung in der `CRecordset`-Klasse der doppelten Pufferung in der `CDaoRecordset`-Klasse ähnelt. Bei `CRecordset` können Sie die doppelte Pufferung allerdings nicht für einzelne Felder aktivieren. Sie können sie für alle Felder aktivieren oder deaktivieren. Beachten Sie Folgendes: Wenn Sie die-Option angeben `CRecordset::useMultiRowFetch` , `CRecordset::noDirtyFieldCheck` wird automatisch aktiviert. allerdings `SetFieldDirty` `SetFieldNull` können und nicht für Recordsets verwendet werden, die das Abrufen von Massen Zeilen implementieren.

- `CRecordset::executeDirect`Verwenden Sie keine vorbereitete SQL-Anweisung. Um die Leistung zu verbessern, geben Sie diese Option an, wenn die `Requery` Member-Funktion niemals aufgerufen wird.

- `CRecordset::useExtendedFetch`Implementieren Sie `SQLExtendedFetch` anstelle von `SQLFetch` . Dies wurde für das Implementieren des gesammelten Abrufens von Zeilen in forward-only-Recordsets entworfen. Wenn Sie die-Option `CRecordset::useMultiRowFetch` für ein Vorwärts Recordset angeben, `CRecordset::useExtendedFetch` wird automatisch aktiviert.

- `CRecordset::userAllocMultiRowBuffers`Der Benutzer weist Speicherpuffer für die Daten zu. Verwenden Sie diese Option in Verbindung mit `CRecordset::useMultiRowFetch`, wenn Sie Ihren eigenen Speicher zuordnen möchten. Andernfalls ordnet wird der notwendigen Speicher vom Framework automatisch zugeordnet. Weitere Informationen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Beachten Sie, dass die Angabe von `CRecordset::userAllocMultiRowBuffers` ohne Angabe von `CRecordset::useMultiRowFetch` zu einer fehlgeschlagenen Erklärung führt.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich `CRecordset` 0 (null), wenn das Objekt erfolgreich geöffnet wurde; andernfalls 0, wenn [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) (sofern aufgerufen) 0 zurückgibt.

### <a name="remarks"></a>Bemerkungen

Sie müssen diese Memberfunktion zum Ausführen der vom Recordset definierten Abfrage aufrufen. Vor dem Aufrufen von `Open` müssen Sie das Recordset-Objekt erstellen.

Die Verbindung dieses Recordsets mit der Datenquelle hängt davon ab, wie Sie das Recordset vor dem Aufruf von erstellen `Open` . Wenn Sie ein [CDatabase](../../mfc/reference/cdatabase-class.md) -Objekt an den recordsetkonstruktor übergeben, der nicht mit der Datenquelle verbunden wurde, verwendet diese Member-Funktion [GetDefaultConnect](#getdefaultconnect) , um das Datenbankobjekt zu öffnen. Wenn Sie NULL an den recordsetkonstruktor übergeben, erstellt der Konstruktor ein `CDatabase` -Objekt für Sie und `Open` versucht, das Datenbankobjekt zu verbinden. Ausführliche Informationen zum Schließen des Recordsets und der Verbindung unter diesen unterschiedlichen Umständen finden Sie unter [Close](#close).

> [!NOTE]
> Der Zugriff auf eine Datenquelle durch ein `CRecordset`-Objekt wird immer freigegeben. Anders als die `CDaoRecordset`-Klasse können Sie kein `CRecordset`-Objekt zum Öffnen einer Datenquelle mit exklusivem Zugriff verwenden.

Beim Abrufen `Open` von wählt eine Abfrage (in der Regel eine SQL- **Select** -Anweisung) Datensätze basierend auf den in der folgenden Tabelle aufgeführten Kriterien aus.

|Der Wert des lpszSQL-Parameters.|Die ausgewählten Datensätze werden von folgenden Aspekten bestimmt:|Beispiel|
|------------------------------------|----------------------------------------|-------------|
|NULL|Die von `GetDefaultSQL` zurückgegebene Zeichenfolge.||
|SQL-Tabellenname|Alle Spalten der Tabellenliste in `DoFieldExchange` oder `DoBulkFieldExchange`.|`"Customer"`|
|Der vordefinierte Name der Abfrage (gespeicherten Prozedur)|Die Spalten, zu denen die Abfrage per Definition zurückgibt.|`"{call OverDueAccts}"`|
|**Select** Column-List **from** Table-List|Die angegebenen Spalten aus den angegebenen Tabellen.|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|

> [!CAUTION]
> Achten Sie darauf, dass keine zusätzlichen Leerzeichen in der SQL-Zeichenfolge eingefügt werden. Wenn Sie z. b. Leerzeichen zwischen der geschweiften Klammer und **dem Schlüsselwort** "-Schlüsselwort" einfügen, interpretiert MFC die SQL-Zeichenfolge nicht als Tabellennamen und integriert Sie in eine **Select** -Anweisung, was dazu führt, dass eine Ausnahme ausgelöst wird. Wenn die vordefinierte Abfrage einen Output-Parameter verwendet, fügen Sie auch keinen Leerraum zwischen der geschweiften Klammer und dem Symbol "" ein. Schließlich dürfen Sie keinen Leerraum vor der geschweiften Klammer in einer **callananweisung** oder vor dem **Select** -Schlüsselwort in einer **Select** -Anweisung einfügen.

Die übliche Vorgehensweise besteht darin, NULL an zu übergeben `Open` . in diesem Fall wird `Open` [getdefaultql](#getdefaultsql)von aufgerufen. Wenn Sie eine abgeleitete `CRecordset` Klasse verwenden, `GetDefaultSQL` gibt die Tabellennamen an, die Sie in ClassWizard angegeben haben. Sie können stattdessen andere Informationen im `lpszSQL`-Parameter angeben.

Wenn Sie alle übergeben, wird `Open` eine abschließende SQL-Zeichenfolge für die Abfrage erstellt (die Zeichenfolge kann SQL **Where** -und **Order by** -Klauseln enthalten, die an die `lpszSQL` übergebene Zeichenfolge angehängt wurden) und anschließend die Abfrage ausführt. Nachdem Sie aufgerufen haben, können Sie die erstellte Zeichenfolge durch Aufrufen von [getionql](#getsql) überprüfen `Open` . Weitere Details dazu, wie das Recordset eine SQL-Anweisung erstellt und Datensätze auswählt, finden Sie im Artikel [Recordset: Wie Recordsets Select Records (ODBC) auswählen](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

Die Felddatenmember der Recordset-Klasse sind an die Spalten der ausgewählten Daten gebunden. Falls Datensätze zurückgegeben werden, wird der erste Datensatz zum aktuellen Datensatz.

Wenn Sie Optionen für das Recordset festlegen möchten, z. b. einen Filter oder eine Sortierung, geben Sie diese an, nachdem Sie das Recordset-Objekt erstellt haben, aber bevor Sie aufzurufen `Open` . Wenn Sie die Datensätze im Recordset aktualisieren möchten, nachdem das Recordset bereits geöffnet ist, wenden Sie sich an " [Requery](#requery)".

Weitere Informationen, einschließlich zusätzlicher Beispiele, finden Sie in den Artikeln [Recordset (ODBC)](../../data/odbc/recordset-odbc.md), [Recordset: Wie Recordsets Select Records (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)und [Recordset: Erstellen und Schließen von Recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

### <a name="example"></a>Beispiel

Die folgenden Codebeispiele zeigen verschiedene Formen des `Open` Aufrufes.

[!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]

## <a name="crecordsetrefreshrowset"></a><a name="refreshrowset"></a>CRecordset:: erfrischendes Rowset

Aktualisiert die Daten und den Status einer Zeile im aktuellen Rowset.

```cpp
void RefreshRowset(
    WORD wRow,
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>Parameter

*wrow*<br/>
Die einbasierte Position einer Zeile im aktuellen Rowset. Dieser Wert kann zwischen 0 und der Größe des Rowsets liegen.

*wlocktype*<br/>
Ein Wert, der angibt, wie die Zeile nach der Aktualisierung gesperrt wird. Einzelheiten finden Sie unter "Hinweise".

### <a name="remarks"></a>Bemerkungen

Wenn Sie für *wrow*den Wert 0 (null) übergeben, wird jede Zeile im Rowset aktualisiert.

Um zu verwenden `RefreshRowset` , müssen Sie das Massen Abrufen von Zeilen durch Angabe der- `CRecordset::useMulitRowFetch` Option in der [Open](#open) Member-Funktion implementiert haben.

`RefreshRowset`Ruft die ODBC-API-Funktion auf `SQLSetPos` . Der *wlocktype* -Parameter gibt den Sperr Zustand der Zeile an, nachdem `SQLSetPos` ausgeführt wurde. In der folgenden Tabelle werden die möglichen Werte für *wlocktype*beschrieben.

|wlocktype|BESCHREIBUNG|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (Standardwert)|Der Treiber oder die Datenquelle stellt sicher, dass sich die Zeile in demselben gesperrten oder ungesperrten Zustand befindet wie vor dem Aufruf von `RefreshRowset` .|
|SQL_LOCK_EXCLUSIVE|Der Treiber oder die Datenquelle sperrt die Zeile exklusiv. Diese Art von Sperre wird nicht von allen Datenquellen unterstützt.|
|SQL_LOCK_UNLOCK|Der Treiber oder die Datenquelle entsperrt die Zeile. Diese Art von Sperre wird nicht von allen Datenquellen unterstützt.|

Weitere Informationen zu finden Sie in `SQLSetPos` der Windows SDK. Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetrequery"></a><a name="requery"></a>CRecordset:: Requery

Erstellt (aktualisiert) ein Recordset neu.

```
virtual BOOL Requery();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Recordset erfolgreich neu erstellt wurde. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Falls Datensätze zurückgegeben werden, wird der erste Datensatz zum aktuellen Datensatz.

Damit das Recordset die Ergänzungen und Löschungen widerspiegelt, die Sie oder andere Benutzer an der Datenquelle vornehmen, müssen Sie das Recordset durch Aufrufen von neu erstellen `Requery` . Wenn das Recordset ein Dynaset ist, spiegelt es automatisch Updates wider, die Sie oder andere Benutzer an den vorhandenen Datensätzen vornehmen (aber nicht an Ergänzungen). Wenn das Recordset eine Momentaufnahme ist, müssen Sie aufrufen, `Requery` um Änderungen durch andere Benutzer sowie Ergänzungen und Löschungen widerzuspiegeln.

Wenn Sie ein Dynaset oder eine Momentaufnahme `Requery` erstellen möchten, können Sie jedes Mal aufrufen, wenn Sie das Recordset mithilfe eines neuen Filters oder einer neuen Sortierung oder neuer Parameterwerte neu erstellen möchten. Legen Sie die neue Filter-oder Sort-Eigenschaft fest, indem Sie vor dem Aufruf von neue Werte zuweisen `m_strFilter` `m_strSort` `Requery` . Legen Sie neue Parameter fest, indem Sie Parameter Datenmembern neue Werte zuweisen, bevor Sie aufrufen `Requery` . Wenn die Filter-und Sortier Zeichenfolgen unverändert bleiben, können Sie die Abfrage wieder verwenden, wodurch die Leistung verbessert wird.

Wenn der Versuch, das Recordset neu zu erstellen, fehlschlägt, wird das Recordset geschlossen. Vor dem Aufrufen `Requery` von können Sie bestimmen, ob das Recordset durch Aufrufen der Member-Funktion abgefragt werden kann `CanRestart` . `CanRestart`garantiert nicht, dass `Requery` erfolgreich ist.

> [!CAUTION]
> Nur aufrufen, `Requery` nachdem Sie " [Öffnen](#open)" aufgerufen haben.

### <a name="example"></a>Beispiel

In diesem Beispiel wird ein Recordset neu erstellt, um eine andere Sortierreihenfolge anzuwenden.

[!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]

## <a name="crecordsetsetabsoluteposition"></a><a name="setabsoluteposition"></a>CRecordset:: SetAbsolutePosition

Positioniert das Recordset auf dem Datensatz, der der angegebenen Datensatznummer entspricht.

```cpp
void SetAbsolutePosition(long nRows);
```

### <a name="parameters"></a>Parameter

*nRows*<br/>
Die einbasierte Ordinalposition für den aktuellen Datensatz im Recordset.

### <a name="remarks"></a>Bemerkungen

`SetAbsolutePosition`Verschiebt den aktuellen Daten Satz Zeiger basierend auf dieser Ordinalposition.

> [!NOTE]
> Diese Member-Funktion ist für Vorwärts-Recordsets ungültig.

Bei ODBC-Recordsets verweist die absolute Positionseinstellung 1 auf den ersten Datensatz im Recordset. eine Einstellung von 0 bezieht sich auf die Anfangs-der-Datei-Position (BOF).

Sie können auch negative Werte an übergeben `SetAbsolutePosition` . In diesem Fall wird die Position des Recordsets vom Ende des Recordsets ausgewertet. `SetAbsolutePosition( -1 )`Verschiebt z. b. den aktuellen Daten Satz Zeiger auf den letzten Datensatz im Recordset.

> [!NOTE]
> Absolute Position ist nicht für die Verwendung als Ersatz Datensatznummer vorgesehen. Lesezeichen sind immer noch die empfohlene Methode zum beibehalten und zurückkehren zu einer bestimmten Position, da sich die Position eines Datensatzes ändert, wenn vorangehende Datensätze gelöscht werden. Außerdem können Sie nicht sicher sein, dass ein bestimmter Datensatz die gleiche absolute Position hat, wenn der Recordset erneut erstellt wird, da die Reihenfolge der einzelnen Datensätze in einem Recordset nicht garantiert wird, es sei denn, Sie wird mit einer SQL-Anweisung mit einer **Order by** -Klausel erstellt.

Weitere Informationen zu Recordsetnavigation und Lesezeichen finden Sie in den Artikeln [Recordset: Scroll (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) und [Recordset: Lesezeichen und absolute Positionen (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

## <a name="crecordsetsetbookmark"></a><a name="setbookmark"></a>CRecordset:: SetBookmark

Positioniert das Recordset im Datensatz, der das angegebene Lesezeichen enthält.

```cpp
void SetBookmark(const CDBVariant& varBookmark);
```

### <a name="parameters"></a>Parameter

*varbookmark*<br/>
Ein Verweis auf ein [CDBVariant](../../mfc/reference/cdbvariant-class.md) -Objekt, das den Lesezeichen Wert für einen bestimmten Datensatz enthält.

### <a name="remarks"></a>Bemerkungen

Um zu ermitteln, ob Lesezeichen für das Recordset unterstützt werden, nennen Sie [CanBookmark](#canbookmark). Um Lesezeichen verfügbar zu machen, wenn Sie unterstützt werden, müssen Sie die- `CRecordset::useBookmarks` Option im *dwOptions* -Parameter der [Open](#open) Member-Funktion festlegen.

> [!NOTE]
> Wenn Lesezeichen nicht unterstützt werden oder nicht verfügbar sind, wird durch das Aufrufen von `SetBookmark` eine Ausnahme ausgelöst. Lesezeichen werden für Vorwärts-Recordsets nicht unterstützt.

Rufen Sie zum ersten Abrufen des Lesezeichens für den aktuellen Datensatz [GetBookmark](#getbookmark)auf, wodurch der Lesezeichen Wert in einem-Objekt gespeichert wird `CDBVariant` . Später können Sie zu diesem Datensatz zurückkehren, indem Sie `SetBookmark` mithilfe des gespeicherten Lesezeichen Werts aufrufen.

> [!NOTE]
> Nach bestimmten recordsetvorgängen sollten Sie die Lesezeichen Persistenz vor dem Aufrufen von überprüfen `SetBookmark` . Wenn Sie z. b. ein Lesezeichen mit Abrufen `GetBookmark` und dann aufrufen `Requery` , ist das Lesezeichen möglicherweise nicht mehr gültig. [CDatabase:: getbookmarkpersistenz](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) aufrufen, um zu überprüfen, ob Sie sicher aufrufen können `SetBookmark` .

Weitere Informationen zu Lesezeichen und Recordsetnavigation finden Sie in den Artikeln [Recordset: Lesezeichen und absolute Positionen (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) und [Recordset: Scrollen (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetsetfielddirty"></a><a name="setfielddirty"></a>CRecordset:: SetFieldDirty

Markiert einen Felddatenmember des Recordsets als geändert oder als unverändert.

```cpp
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```

### <a name="parameters"></a>Parameter

*teuren*<br/>
Enthält die Adresse eines Felddatenmembers im Recordset oder NULL. Wenn der Wert NULL ist, werden alle Felddatenmember im Recordset gekennzeichnet. (C++ NULL ist in der Daten Bank Terminologie nicht identisch mit NULL, was bedeutet, dass kein Wert vorhanden ist.)

*bdirty*<br/>
TRUE, wenn der Felddatenmember als "Dirty" (geändert) gekennzeichnet werden soll. Andernfalls false, wenn der Felddatenmember als "Clean" (unverändert) gekennzeichnet werden soll.

### <a name="remarks"></a>Bemerkungen

Durch Markieren von Feldern als unverändert wird sichergestellt, dass das Feld nicht aktualisiert wird und weniger SQL-Datenverkehr verursacht.

> [!NOTE]
> Diese Member-Funktion ist für Recordsets, die das Abrufen von Massen Zeilen verwenden, nicht anwendbar. Wenn Sie das Massen Abrufen von Zeilen implementiert haben, `SetFieldDirty` führt zu einer fehlgeschlagenen-Erklärung. Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Das Framework markiert geänderte Felddatenmember, um sicherzustellen, dass Sie vom RFX-Mechanismus (Record Field Exchange) in den Datensatz in der Datenquelle geschrieben werden. Wenn Sie den Wert eines Felds ändern, wird das Feld in der Regel automatisch geändert, sodass Sie sich nur selten selbst anrufen müssen `SetFieldDirty` . Sie können jedoch manchmal sicherstellen, dass die Spalten explizit aktualisiert oder eingefügt werden, unabhängig davon, welcher Wert im Feld Datenmember liegt.

> [!CAUTION]
> Diese Member-Funktion nur aufrufen, nachdem Sie [Edit](#edit) oder [AddNew](#addnew)aufgerufen haben.

Wenn NULL für das erste Argument der Funktion verwendet wird, wird die Funktion nur auf `outputColumn` Felder, nicht auf `param` Felder angewendet. Beispielsweise ist der-Befehl

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

legt nur `outputColumn` Felder auf NULL fest `param` . Felder sind nicht betroffen.

Zum Bearbeiten von `param` Feldern müssen Sie die tatsächliche Adresse der Person angeben `param` , an der Sie arbeiten möchten, z. b.:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

Dies bedeutet, dass Sie nicht alle `param` Felder wie bei Feldern auf NULL festlegen können `outputColumn` .

## <a name="crecordsetsetfieldnull"></a><a name="setfieldnull"></a>CRecordset:: SetFieldNull

Gibt einen Felddatenmember des Recordsets als NULL (ohne Wert) oder als nicht-NULL-Wert an.

```cpp
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parameter

*teuren*<br/>
Enthält die Adresse eines Felddatenmembers im Recordset oder NULL. Wenn der Wert NULL ist, werden alle Felddatenmember im Recordset gekennzeichnet. (C++ NULL ist in der Daten Bank Terminologie nicht identisch mit NULL, was bedeutet, dass kein Wert vorhanden ist.)

*bNULL*<br/>
Ein Wert ungleich 0 (null), wenn für den Felddatenmember kein Wert (null) gekennzeichnet werden soll. Andernfalls 0, wenn der Felddatenmember als nicht-NULL gekennzeichnet werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn Sie einem Recordset einen neuen Datensatz hinzufügen, werden alle Felddatenmember anfänglich auf einen NULL-Wert festgelegt und als "Dirty" (geändert) gekennzeichnet. Wenn Sie einen Datensatz aus einer Datenquelle abrufen, verfügen seine Spalten entweder bereits über Werte oder sind NULL.

> [!NOTE]
> Rufen Sie diese Member-Funktion nicht für Recordsets auf, die das Massen Abrufen von Zeilen verwenden. Wenn Sie das Massen Abrufen von Zeilen implementiert haben, führt das Aufrufen von `SetFieldNull` zu einer fehlgeschlagenen Assertion. Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Wenn Sie ein Feld des aktuellen Datensatzes ohne einen Wert festlegen möchten, müssen Sie `SetFieldNull` mit *bNULL* auf true festlegen, um ihn als Null zu kennzeichnen. Wenn ein Feld zuvor als NULL gekennzeichnet war und Sie diesem nun einen Wert zuordnen möchten, legen Sie einfach den neuen Wert fest. Sie müssen das NULL-Flag nicht mit entfernen `SetFieldNull` . Um zu ermitteln, ob das Feld NULL sein darf, geben Sie an `IsFieldNullable` .

> [!CAUTION]
> Diese Member-Funktion nur aufrufen, nachdem Sie [Edit](#edit) oder [AddNew](#addnew)aufgerufen haben.

Wenn NULL für das erste Argument der Funktion verwendet wird, wird die Funktion nur auf `outputColumn` Felder, nicht auf `param` Felder angewendet. Beispielsweise ist der-Befehl

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

legt nur `outputColumn` Felder auf NULL fest `param` . Felder sind nicht betroffen.

Zum Bearbeiten von `param` Feldern müssen Sie die tatsächliche Adresse der Person angeben `param` , an der Sie arbeiten möchten, z. b.:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

Dies bedeutet, dass Sie nicht alle `param` Felder wie bei Feldern auf NULL festlegen können `outputColumn` .

> [!NOTE]
> Beim Festlegen von Parametern auf NULL führt ein-Rückruf, `SetFieldNull` bevor das Recordset geöffnet wird, zu einer-Erklärung. Nennen Sie in diesem Fall [SetParamNull](#setparamnull).

`SetFieldNull`wird durch [DoFieldExchange](#dofieldexchange)implementiert.

## <a name="crecordsetsetlockingmode"></a><a name="setlockingmode"></a>CRecordset:: SetLockingMode

Legt den Sperrmodus auf die "optimistische" Sperrung (Standardeinstellung) oder die "pessimistische" Sperre fest. Bestimmt, wie Datensätze für Updates gesperrt werden.

```cpp
void SetLockingMode(UINT nMode);
```

### <a name="parameters"></a>Parameter

*nmode*<br/>
Enthält einen der folgenden Werte aus `enum LockMode` :

- `optimistic`Die optimistische Sperre sperrt den Datensatz, der nur während des Aufrufens von aktualisiert wird `Update` .

- `pessimistic`Das pessimistische sperren sperrt den Datensatz `Edit` , sobald aufgerufen wird, und hält ihn gesperrt `Update` , bis der Aufruf abgeschlossen ist oder Sie zu einem neuen Datensatz wechseln.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion wird aufgerufen, wenn Sie angeben müssen, welche der beiden Daten Satz Sperr Strategien das Recordset für Updates verwendet. Standardmäßig ist der Sperrmodus eines Recordsets `optimistic` . Dies kann zu einer vorsichtigeren `pessimistic` Sperr Strategie wechseln. Wird aufgerufen, `SetLockingMode` nachdem Sie das Recordset-Objekt erstellt und geöffnet haben, aber bevor Sie aufzurufen `Edit` .

## <a name="crecordsetsetparamnull"></a><a name="setparamnull"></a>CRecordset:: SetParamNull

Markiert einen Parameter als NULL (ohne Wert) oder als nicht-NULL.

```cpp
void SetParamNull(
    int nIndex,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der nullbasierte Index des Parameters.

*bNULL*<br/>
TRUE (der Standardwert) gibt an, dass der Parameter als NULL gekennzeichnet wird. Andernfalls wird der-Parameter als nicht-NULL gekennzeichnet.

### <a name="remarks"></a>Bemerkungen

Anders als bei [SetFieldNull](#setfieldnull)können Sie aufrufen, `SetParamNull` bevor Sie das Recordset geöffnet haben.

`SetParamNull`wird in der Regel mit vordefinierten Abfragen (gespeicherte Prozeduren) verwendet.

## <a name="crecordsetsetrowsetcursorposition"></a><a name="setrowsetcursorposition"></a>CRecordset:: setrowsetcurrsorposition

Verschiebt den Cursor in eine Zeile im aktuellen Rowset.

```cpp
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>Parameter

*wrow*<br/>
Die einbasierte Position einer Zeile im aktuellen Rowset. Dieser Wert kann zwischen 1 und der Größe des Rowsets liegen.

*wlocktype*<br/>
Wert, der angibt, wie die Zeile nach der Aktualisierung gesperrt wird. Einzelheiten finden Sie unter "Hinweise".

### <a name="remarks"></a>Bemerkungen

Beim Implementieren des Massen Abruf von Zeilen werden Datensätze von Rowsets abgerufen, wobei der erste Datensatz im abgerufenen Rowset der aktuelle Datensatz ist. Um einen weiteren Datensatz innerhalb des Rowsets im aktuellen Datensatz zu erstellen, geben Sie an `SetRowsetCursorPosition` . Beispielsweise können Sie eine Kombination `SetRowsetCursorPosition` mit der [GetFieldValue](#getfieldvalue) -Member-Funktion durchführen, um die Daten dynamisch aus jedem Datensatz Ihres Recordsets abzurufen.

Zum verwenden `SetRowsetCursorPosition` von müssen Sie das Massen Abrufen von Zeilen implementieren, indem Sie die- `CRecordset::useMultiRowFetch` Option des *dwOptions* -Parameters in der [Open](#open) Member-Funktion angeben.

`SetRowsetCursorPosition`Ruft die ODBC-API-Funktion auf `SQLSetPos` . Der *wlocktype* -Parameter gibt den Sperr Zustand der Zeile an, nachdem `SQLSetPos` ausgeführt wurde. In der folgenden Tabelle werden die möglichen Werte für *wlocktype*beschrieben.

|wlocktype|BESCHREIBUNG|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (Standardwert)|Der Treiber oder die Datenquelle stellt sicher, dass sich die Zeile in demselben gesperrten oder ungesperrten Zustand befindet wie vor dem Aufruf von `SetRowsetCursorPosition` .|
|SQL_LOCK_EXCLUSIVE|Der Treiber oder die Datenquelle sperrt die Zeile exklusiv. Diese Art von Sperre wird nicht von allen Datenquellen unterstützt.|
|SQL_LOCK_UNLOCK|Der Treiber oder die Datenquelle entsperrt die Zeile. Diese Art von Sperre wird nicht von allen Datenquellen unterstützt.|

Weitere Informationen zu finden Sie in `SQLSetPos` der Windows SDK. Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetsetrowsetsize"></a><a name="setrowsetsize"></a>CRecordset:: SetRowsetSize

Gibt die Anzahl der Datensätze an, die während eines Abruf Vorgangs abgerufen werden sollen.

```
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```

### <a name="parameters"></a>Parameter

*dwnewrowsetsize*<br/>
Die Anzahl der Zeilen, die während eines bestimmten Abruf Vorgangs abgerufen werden sollen.

### <a name="remarks"></a>Bemerkungen

Diese Funktion für virtuelle Member gibt an, wie viele Zeilen bei einem einzelnen Abruf Vorgang abgerufen werden sollen, wenn das Massen Abrufen von Zeilen verwendet wird. Um das Abrufen von Massen Zeilen zu implementieren, müssen Sie die- `CRecordset::useMultiRowFetch` Option im *dwOptions* -Parameter der [Open](#open) Member-Funktion festlegen.

> [!NOTE]
> Wenn Sie aufrufen, ohne das Massen Abrufen von `SetRowsetSize` Zeilen zu implementieren, führt dies zu einer fehlgeschlagenen

Rufen `SetRowsetSize` `Open` Sie auf, bevor Sie aufrufen, um anfänglich die Rowsetgröße für das Recordset festzulegen. Die standardrowsetgröße bei der Implementierung des Massen Abruf Vorgangs beträgt 25.

> [!NOTE]
> Verwenden Sie beim Aufrufen von Vorsicht `SetRowsetSize` . Wenn Sie Speicher für die Daten manuell zuweisen (wie durch die `CRecordset::userAllocMultiRowBuffers` Option des Parameters dwOptions in angegeben `Open` ), sollten Sie überprüfen, ob Sie diese Speicherpuffer nach dem Aufrufen von neu zuordnen müssen `SetRowsetSize` , aber bevor Sie einen Cursor Navigations Vorgang ausführen.

Um die aktuelle Einstellung für die Rowsetgröße zu erhalten, rufen Sie [getrowsetsize](#getrowsetsize)auf.

Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetupdate"></a><a name="update"></a>CRecordset:: Update

Schließt einen- `AddNew` Vorgang oder-Vorgang ab, `Edit` indem die neuen oder bearbeiteten Daten in der Datenquelle gespeichert werden.

```
virtual BOOL Update();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn ein Datensatz erfolgreich aktualisiert wurde. andernfalls 0, wenn keine Spalten geändert wurden. Wenn keine Datensätze aktualisiert wurden oder mehr als ein Datensatz aktualisiert wurde, wird eine Ausnahme ausgelöst. Eine Ausnahme wird auch für andere Fehler in der Datenquelle ausgelöst.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion wird nach einem Rückruf der [AddNew](#addnew) -oder [Edit](#edit) Member-Funktion aufgerufen. Dieser Befehl ist erforderlich, um den- `AddNew` Vorgang oder den- `Edit` Vorgang abzuschließen.

> [!NOTE]
> Wenn Sie das Massen Abrufen von Zeilen implementiert haben, können Sie nicht aufzurufen `Update` . Dies führt zu einer fehlgeschlagenen Bestätigung. Obwohl die-Klasse `CRecordset` keinen Mechanismus zum Aktualisieren von Massendaten Zeilen bereitstellt, können Sie Ihre eigenen Funktionen mithilfe der ODBC-API-Funktion schreiben `SQLSetPos` . Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`AddNew`Und `Edit` bereiten einen Bearbeitungs Puffer vor, in dem die hinzugefügten oder bearbeiteten Daten zum Speichern in der Datenquelle platziert werden. `Update`speichert die Daten. Nur die Felder, die als geändert markiert oder erkannt wurden, werden aktualisiert.

Wenn die Datenquelle Transaktionen unterstützt, können Sie den `Update` -Befehl (und den entsprechenden- `AddNew` oder- `Edit` Rückruf) einer Transaktion ausführen. Weitere Informationen zu Transaktionen finden Sie im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

> [!CAUTION]
> Wenn Sie aufrufen `Update` , ohne zuerst entweder `AddNew` oder aufzurufen `Edit` , löst eine aus `Update` `CDBException` . Wenn Sie `AddNew` oder aufruft `Edit` , müssen Sie `Update` vor dem aufzurufen eines- `Move` Vorgangs oder vor dem Schließen des Recordsets oder der Datenquellen Verbindung aufzurufen. Andernfalls gehen die Änderungen ohne Benachrichtigung verloren.

Ausführliche Informationen zur `Update` Fehlerbehandlung finden Sie im Artikel [Recordset: Wie Recordsets Update Datensätze (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Artikel [Transaktion: Ausführen einer Transaktion in einem Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="see-also"></a>Weitere Informationen

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CDatabase-Klasse](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordView-Klasse](../../mfc/reference/crecordview-class.md)
