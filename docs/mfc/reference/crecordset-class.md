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
ms.openlocfilehash: ab6cde9f478dc6f2e3cb0ba5bb338a3852f083fd
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750503"
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
|[CRecordset::CRecordset](#crecordset)|Erstellt ein `CRecordset`-Objekt. Ihre abgeleitete Klasse muss einen Konstruktor bereitstellen, der diesen aufruft.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRecordset::Neue Hinzufügen](#addnew)|Bereitet das Hinzufügen eines neuen Datensatzes vor. Rufen `Update` Sie an, um den Zusatz abzuschließen.|
|[CRecordset::CanAppend](#canappend)|Gibt einen Wert ungleich Null zurück, wenn `AddNew` dem Recordset über die Memberfunktion neue Datensätze hinzugefügt werden können.|
|[CRecordset::CanBookmark](#canbookmark)|Gibt einen Wert ungleich Null zurück, wenn das Recordset Lesezeichen unterstützt.|
|[CRecordset::Abbrechen](#cancel)|Bricht einen asynchronen Vorgang oder einen Prozess von einem zweiten Thread ab.|
|[CRecordset::AbbrechenUpdate](#cancelupdate)|Bricht alle ausstehenden Aktualisierungen `Edit` aufgrund eines Oder-Vorgangs `AddNew` ab.|
|[CRecordset::CanRestart](#canrestart)|Gibt einen `Requery` Wert ungleich Null zurück, wenn aufgerufen werden kann, um die Abfrage des Recordsets erneut auszuführen.|
|[CRecordset::CanScroll](#canscroll)|Gibt einen Wert ungleich Null zurück, wenn Sie durch die Datensätze scrollen können.|
|[CRecordset::CanTransact](#cantransact)|Gibt einen Wert ungleich Null zurück, wenn die Datenquelle Transaktionen unterstützt.|
|[CRecordset::CanUpdate](#canupdate)|Gibt einen Wert ungleich Null zurück, wenn das Recordset aktualisiert werden kann (Sie können Datensätze hinzufügen, aktualisieren oder löschen).|
|[CRecordset::CheckRowsetError](#checkrowseterror)|Wird aufgerufen, um Fehler zu behandeln, die beim Abrufen von Datensätzen generiert wurden.|
|[CRecordset::Schließen](#close)|Schließt das Recordset und das ihm zugeordnete ODBC HSTMT.|
|[CRecordset::Delete](#delete)|Löscht den aktuellen Datensatz aus dem Recordset. Sie müssen nach dem Löschen explizit zu einem anderen Datensatz scrollen.|
|[CRecordset::DoBulkFieldExchange](#dobulkfieldexchange)|Wird aufgerufen, um Massendaten von der Datenquelle in das Recordset auszutauschen. Implementiert Massendatensatzfeldaustausch (Bulk RFX).|
|[CRecordset::DoFieldExchange](#dofieldexchange)|Wird aufgerufen, um Daten (in beide Richtungen) zwischen den Felddatenelementen des Recordsets und dem entsprechenden Datensatz in der Datenquelle auszutauschen. Implementiert Datensatzfeldaustausch (RFX).|
|[CRecordset::Bearbeiten](#edit)|Bereitet sich auf Änderungen am aktuellen Datensatz vor. Rufen `Update` Sie an, um die Bearbeitung abzuschließen.|
|[CRecordset::FlushResultSet](#flushresultset)|Gibt einen Wert ungleich Null zurück, wenn bei Verwendung einer vordefinierten Abfrage ein anderes Resultset abgerufen werden soll.|
|[CRecordset::GetBookmark](#getbookmark)|Weist dem Parameterobjekt den Lesezeichenwert eines Datensatzes zu.|
|[CRecordset::GetDefaultConnect](#getdefaultconnect)|Wird aufgerufen, um die Standardverbindungszeichenfolge abzubekommen.|
|[CRecordset::GetDefaultSQL](#getdefaultsql)|Wird aufgerufen, um die standardmäßige SQL-Zeichenfolge auszuführen.|
|[CRecordset::GetFieldValue](#getfieldvalue)|Gibt den Wert eines Felds in einem Recordset zurück.|
|[CRecordset::GetODBCFieldCount](#getodbcfieldcount)|Gibt die Anzahl der Felder im Recordset zurück.|
|[CRecordset::GetODBCFieldInfo](#getodbcfieldinfo)|Gibt bestimmte Arten von Informationen zu den Feldern in einem Recordset zurück.|
|[CRecordset::GetRecordCount](#getrecordcount)|Gibt die Anzahl der Datensätze im Recordset zurück.|
|[CRecordset::GetRowsetSize](#getrowsetsize)|Gibt die Anzahl der Datensätze zurück, die Sie während eines einzelnen Abrufs abrufen möchten.|
|[CRecordset::GetRowsFetched](#getrowsfetched)|Gibt die tatsächliche Anzahl der Zeilen zurück, die während eines Abrufs abgerufen wurden.|
|[CRecordset::GetRowStatus](#getrowstatus)|Gibt den Status der Zeile nach einem Abruf zurück.|
|[CRecordset::GetSQL](#getsql)|Ruft die SQL-Zeichenfolge ab, die zum Auswählen von Datensätzen für das Recordset verwendet wird.|
|[CRecordset::GetStatus](#getstatus)|Ruft den Status des Recordsets ab: den Index des aktuellen Datensatzes und ob eine endgültige Anzahl der Datensätze abgerufen wurde.|
|[CRecordset::GetTableName](#gettablename)|Ruft den Namen der Tabelle ab, auf der das Recordset basiert.|
|[CRecordset::IsBOF](#isbof)|Gibt einen Wert ungleich Null zurück, wenn das Recordset vor dem ersten Datensatz positioniert wurde. Es ist kein aktueller Datensatz vorhanden.|
|[CRecordset::IsDeleted](#isdeleted)|Gibt einen Wert ungleich Null zurück, wenn das Recordset auf einem gelöschten Datensatz positioniert ist.|
|[CRecordset::IsEOF](#iseof)|Gibt einen Wert ungleich Null zurück, wenn das Recordset nach dem letzten Datensatz positioniert wurde. Es ist kein aktueller Datensatz vorhanden.|
|[CRecordset::IsFieldDirty](#isfielddirty)|Gibt einen Wert ungleich Null zurück, wenn das angegebene Feld im aktuellen Datensatz geändert wurde.|
|[CRecordset::IsFieldNull](#isfieldnull)|Gibt einen Wert ungleich Null zurück, wenn das angegebene Feld im aktuellen Datensatz null ist (hat keinen Wert).|
|[CRecordset::IsFieldNullable](#isfieldnullable)|Gibt einen Wert ungleich Null zurück, wenn das angegebene Feld im aktuellen Datensatz auf null festgelegt werden kann (ohne Wert).|
|[CRecordset::IsOpen](#isopen)|Gibt einen `Open` Wert ungleich Null zurück, wenn zuvor aufgerufen wurde.|
|[CRecordset::Bewegen](#move)|Positioniert das Recordset in eine angegebene Anzahl von Datensätzen aus dem aktuellen Datensatz in beide Richtungen.|
|[CRecordset::MoveFirst](#movefirst)|Positioniert den aktuellen Datensatz auf dem ersten Datensatz im Recordset. Testen `IsBOF` Sie zuerst.|
|[CRecordset::MoveLast](#movelast)|Positioniert den aktuellen Datensatz auf dem letzten Datensatz oder im letzten Rowset. Testen `IsEOF` Sie zuerst.|
|[CRecordset::MoveNext](#movenext)|Positioniert den aktuellen Datensatz auf dem nächsten Datensatz oder im nächsten Rowset. Testen `IsEOF` Sie zuerst.|
|[CRecordset::MovePrev](#moveprev)|Positioniert den aktuellen Datensatz auf dem vorherigen Datensatz oder im vorherigen Rowset. Testen `IsBOF` Sie zuerst.|
|[CRecordset::OnSetOptions](#onsetoptions)|Wird aufgerufen, um Optionen (bei der Auswahl verwendet) für die angegebene ODBC-Anweisung festzulegen.|
|[CRecordset::OnSetUpdateOptions](#onsetupdateoptions)|Wird aufgerufen, um Optionen (bei Aktualisierung verwendet) für die angegebene ODBC-Anweisung festzulegen.|
|[CRecordset::Öffnen](#open)|Öffnet das Recordset, indem die Tabelle abgerufen oder die vom Recordset darstellte Abfrage durchgeführt wird.|
|[CRecordset::RefreshRowset](#refreshrowset)|Aktualisiert die Daten und den Status der angegebenen Zeilen.|
|[CRecordset::Requery](#requery)|Führt die Abfrage des Recordsets erneut aus, um die ausgewählten Datensätze zu aktualisieren.|
|[CRecordset::SetAbsolutePosition](#setabsoluteposition)|Positioniert das Recordset auf dem Datensatz entsprechend der angegebenen Datensatznummer.|
|[CRecordset::SetBookmark](#setbookmark)|Positioniert das Recordset auf dem datensatz, der durch das Lesezeichen angegeben wird.|
|[CRecordset::SetFieldDirty](#setfielddirty)|Markiert das angegebene Feld im aktuellen Datensatz als geändert.|
|[CRecordset::SetFieldNull](#setfieldnull)|Legt den Wert des angegebenen Felds im aktuellen Datensatz auf null fest (ohne Wert).|
|[CRecordset::SetLockingMode](#setlockingmode)|Legt den Sperrmodus auf "optimistische" Sperrung (Standard) oder "pessimistische" Sperre fest. Bestimmt, wie Datensätze für Aktualisierungen gesperrt werden.|
|[CRecordset::SetParamNull](#setparamnull)|Legt den angegebenen Parameter auf null fest (ohne Wert).|
|[CRecordset::SetRowsetCursorPosition](#setrowsetcursorposition)|Positioniert den Cursor in der angegebenen Zeile innerhalb des Rowsets.|
|[CRecordset::SetRowsetSize](#setrowsetsize)|Gibt die Anzahl der Datensätze an, die Sie während eines Abrufs abrufen möchten.|
|[CRecordset::Update](#update)|Schließt einen `AddNew` `Edit` oder einen Vorgang ab, indem die neuen oder bearbeiteten Daten in der Datenquelle gespeichert werden.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRecordset::m_hstmt](#m_hstmt)|Enthält das ODBC-Anweisungshandle für das Recordset. Geben Sie `HSTMT` ein.|
|[CRecordset::m_nFields](#m_nfields)|Enthält die Anzahl der Felddatenelemente im Recordset. Geben Sie `UINT` ein.|
|[CRecordset::m_nParams](#m_nparams)|Enthält die Anzahl der Parameterdatenmember im Recordset. Geben Sie `UINT` ein.|
|[CRecordset::m_pDatabase](#m_pdatabase)|Enthält einen Zeiger `CDatabase` auf das Objekt, über das das Recordset mit einer Datenquelle verbunden ist.|
|[CRecordset::m_strFilter](#m_strfilter)|Enthält `CString` eine, die eine SQL-Klausel `WHERE` (Structured Query Language) angibt. Wird als Filter verwendet, um nur die Datensätze auszuwählen, die bestimmte Kriterien erfüllen.|
|[CRecordset::m_strSort](#m_strsort)|Enthält `CString` eine, die `ORDER BY` eine SQL-Klausel angibt. Wird verwendet, um zu steuern, wie die Datensätze sortiert werden.|

## <a name="remarks"></a>Hinweise zu <a name="remarks"></a>

Objekte, die als `CRecordset` "Recordsets" bezeichnet werden, werden in der Regel in zwei Formen verwendet: Dynasets und Snapshots. Ein Dynaset bleibt mit Datenaktualisierungen anderer Benutzer synchronisiert. Ein Snapshot ist eine statische Ansicht der Daten. Jedes Formular stellt einen Satz von Datensätzen dar, die zum Zeitpunkt des Öffnens des Recordsets festgelegt wurden, aber wenn Sie zu einem Datensatz in einem Dynaset scrollen, spiegelt es Änderungen wider, die anschließend an dem Datensatz vorgenommen wurden, entweder von anderen Benutzern oder von anderen Recordsets in Ihrer Anwendung.

> [!NOTE]
> Wenn Sie mit den DAO-Klassen (Data Access Objects) und nicht mit den ODBC-Klassen (Open Database Connectivity) arbeiten, verwenden Sie stattdessen die Klasse [CDaoRecordset.](../../mfc/reference/cdaorecordset-class.md) Weitere Informationen finden Sie im Artikel [Übersicht: Datenbankprogrammierung](../../data/data-access-programming-mfc-atl.md).

Um mit beiden Arten von Recordset zu arbeiten, leiten Sie `CRecordset`in der Regel eine anwendungsspezifische Recordset-Klasse von ab. Recordsets wählen Datensätze aus einer Datenquelle aus, und Sie können dann:

- Blättern Sie durch die Datensätze.

- Aktualisieren Sie die Datensätze, und geben Sie einen Sperrmodus an.

- Filtern Sie das Recordset, um zu beschränken, welche Datensätze es aus den in der Datenquelle verfügbaren Datensätzen auswählt.

- Sortieren Sie das Recordset.

- Parametrierbe des Recordsets, um seine Auswahl mit Informationen anzupassen, die erst zur Laufzeit bekannt sind.

Um Ihre Klasse zu verwenden, öffnen Sie eine Datenbank und erstellen Sie `CDatabase` ein Recordset-Objekt, indem Sie dem Konstruktor einen Zeiger an das Objekt übergeben. Rufen Sie dann die `Open` Memberfunktion des Recordsets auf, in der Sie angeben können, ob es sich bei dem Objekt um ein Dynaset oder einen Snapshot handelt. Beim `Open` Aufrufen werden Daten aus der Datenquelle ausgewählt. Nachdem das Recordset-Objekt geöffnet wurde, verwenden Sie seine Memberfunktionen und Datenmember, um durch die Datensätze zu scrollen und sie zu bedienen. Die verfügbaren Vorgänge hängen davon ab, ob es sich bei dem Objekt um ein Dynaset oder einen Snapshot handelt, ob es aufrüstbar oder schreibgeschützt ist (dies hängt von der Fähigkeit der ODBC-Datenquelle (Open Database Connectivity) ab) ab und ob Sie das Abrufen von Massenzeilen implementiert haben. Um Datensätze zu aktualisieren, die seit `Open` dem Aufruf möglicherweise `Requery` geändert oder hinzugefügt wurden, rufen Sie die Memberfunktion des Objekts auf. Rufen Sie die `Close` Memberfunktion des Objekts auf, und zerstören Sie das Objekt, wenn Sie damit fertig sind.

In einer `CRecordset` abgeleiteten Klasse wird Datensatzfeldaustausch (RFX) oder Massendatensatzfeldaustausch (Bulk RFX) verwendet, um das Lesen und Aktualisieren von Datensatzfeldern zu unterstützen.

Weitere Informationen zu Recordsets und Datensatzfeldaustausch finden Sie in den Artikeln [Übersicht: Datenbankprogrammierung](../../data/data-access-programming-mfc-atl.md), [Recordset (ODBC)](../../data/odbc/recordset-odbc.md), [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)und [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md). Ein Schwerpunkt auf Dynasets und Snapshots finden Sie in den Artikeln [Dynaset](../../data/odbc/dynaset.md) und [Snapshot](../../data/odbc/snapshot.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CRecordset`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxdb.h

## <a name="crecordsetaddnew"></a><a name="addnew"></a>CRecordset::Neue Hinzufügen

Bereitet das Hinzufügen eines neuen Datensatzes zur Tabelle vor.

```
virtual void AddNew();
```

### <a name="remarks"></a>Bemerkungen

Sie müssen die [Requery-Memberfunktion](#requery) aufrufen, um den neu hinzugefügten Datensatz anzuzeigen. Die Felder des Datensatzes sind zunächst Null. (In der Datenbankterminologie bedeutet Null "keinen Wert" und ist nicht identisch mit NULL in C++.) Um den Vorgang abzuschließen, müssen Sie die [Funktion Member aktualisieren](#update) aufrufen. `Update`speichert Ihre Änderungen in der Datenquelle.

> [!NOTE]
> Wenn Sie das Abrufen von Massenzeilen `AddNew`implementiert haben, können Sie nicht aufrufen. Dies führt zu einer fehlgeschlagenen Behauptung. Obwohl `CRecordset` die Klasse keinen Mechanismus zum Aktualisieren von Massendatenzeilen bereitstellt, können Sie `SQLSetPos`ihre eigenen Funktionen mithilfe der ODBC-API-Funktion schreiben. Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`AddNew`erstellt einen neuen, leeren Datensatz mithilfe der Felddatenmember des Recordsets. Legen Sie `AddNew`nach dem Aufruf die gewünschten Werte in den Felddatenmembern des Recordsets fest. (Sie müssen die Funktion Member [bearbeiten](#edit) zu diesem `Edit` Zweck nicht aufrufen; nur für vorhandene Datensätze verwenden.) Wenn Sie `Update`anschließend aufrufen, werden geänderte Werte in den Felddatenmembern in der Datenquelle gespeichert.

> [!CAUTION]
> Wenn Sie vor dem Aufruf `Update`zu einem neuen Datensatz scrollen, geht der neue Datensatz verloren, und es wird keine Warnung angezeigt.

Wenn die Datenquelle Transaktionen unterstützt, können `AddNew` Sie Ihren Anruf zu einem Teil einer Transaktion machen. Weitere Informationen zu Transaktionen finden Sie unter Klasse [CDatabase](../../mfc/reference/cdatabase-class.md). Beachten Sie, dass Sie [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) aufrufen sollten, bevor Sie aufrufen. `AddNew`

> [!NOTE]
> Bei Dynasets werden dem Recordset als letzter Datensatz neue Datensätze hinzugefügt. Hinzugefügte Datensätze werden snapshots nicht hinzugefügt. Sie müssen `Requery` aufrufen, um das Recordset zu aktualisieren.

Es ist unzulässig, ein Recordset aufzurufen, `AddNew` dessen `Open` Memberfunktion nicht aufgerufen wurde. A `CDBException` wird ausgelöst, `AddNew` wenn Sie ein Recordset aufrufen, an das nicht angehängt werden kann. Sie können bestimmen, ob das Recordset aufrüstbar ist, indem Sie [CanAppend](#canappend)aufrufen.

Weitere Informationen finden Sie in den folgenden Artikeln: [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md), [Recordset: Adding, Updating, and Deleting Records (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), und [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Beispiel

Siehe den Artikel [Transaktion: Ausführen einer Transaktion in einem Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="crecordsetcanappend"></a><a name="canappend"></a>CRecordset::CanAppend

Legt fest, ob Sie mit dem zuvor geöffneten Recordset neue Datensätze hinzufügen können.

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Recordset das Hinzufügen neuer Datensätze zulässt; andernfalls 0. `CanAppend`gibt 0 zurück, wenn Sie das Recordset als schreibgeschützt geöffnet haben.

## <a name="crecordsetcanbookmark"></a><a name="canbookmark"></a>CRecordset::CanBookmark

Bestimmt, ob Sie mit dem Recordset Datensätze mit Lesezeichen markieren können.

```
BOOL CanBookmark() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Recordset Lesezeichen unterstützt; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist `CRecordset::useBookmarks` unabhängig von der Option im Parameter *dwOptions* der Open-Member-Funktion. [Open](#open) `CanBookmark`gibt an, ob der angegebene ODBC-Treiber und Cursortyp Lesezeichen unterstützen. `CRecordset::useBookmarks`gibt an, ob Lesezeichen verfügbar sind, sofern sie unterstützt werden.

> [!NOTE]
> Lesezeichen werden in Vorwärts-Recordsets nicht unterstützt.

Weitere Informationen zur Lesezeichen- und Recordsetnavigation finden Sie in den Artikeln [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) und [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetcancel"></a><a name="cancel"></a>CRecordset::Abbrechen

Fordert an, dass die Datenquelle entweder einen laufenden asynchronen Vorgang oder einen Prozess von einem zweiten Thread abbricht.

```cpp
void Cancel();
```

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass die MFC-ODBC-Klassen keine asynchrone Verarbeitung mehr verwenden. Um einen asychronen Vorgang auszuführen, müssen Sie `SQLSetConnectOption`direkt die ODBC-API-Funktion aufrufen. Weitere Informationen finden Sie im Thema "Ausführen von Funktionen asynchron" im *ODBC SDK Programmer es Guide*.

## <a name="crecordsetcancelupdate"></a><a name="cancelupdate"></a>CRecordset::AbbrechenUpdate

Bricht alle ausstehenden Aktualisierungen ab, die durch einen [Edit-](#edit) oder [AddNew-Vorgang](#addnew) verursacht werden, bevor [Update](#update) aufgerufen wird.

```cpp
void CancelUpdate();
```

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Diese Memberfunktion ist nicht für Recordsets anwendbar, die Massenzeilenabruf `Edit` `AddNew`verwenden, `Update`da solche Recordsets nicht aufrufen können , oder . Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Wenn die automatische Schmutzfeldprüfung aktiviert ist, `CancelUpdate` werden die `Edit` Membervariablen auf die Werte zurückhergestellt, die sie zuvor hatten oder `AddNew` aufgerufen wurden. Andernfalls bleiben Wertänderungen bestehen. Standardmäßig ist die automatische Feldprüfung aktiviert, wenn das Recordset geöffnet wird. Um es zu deaktivieren, `CRecordset::noDirtyFieldCheck` müssen Sie den Parameter im *dwOptions* der [Open-Memberfunktion](#open) angeben.

Weitere Informationen zum Aktualisieren von Daten finden Sie im Artikel [Recordset: Hinzufügen, Aktualisieren und Löschen von Datensätzen (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md).

## <a name="crecordsetcanrestart"></a><a name="canrestart"></a>CRecordset::CanRestart

Bestimmt, ob das Recordset das Neustarten seiner Abfrage `Requery` (zum Aktualisieren seiner Datensätze) durch Aufrufen der Memberfunktion ermöglicht.

```
BOOL CanRestart() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn eine erneute Abfrage zulässig ist; andernfalls 0.

## <a name="crecordsetcanscroll"></a><a name="canscroll"></a>CRecordset::CanScroll

Bestimmt, ob das Recordset einen Bildlauf zulässt.

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Recordset einen Bildlauf zulässt; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zum Scrollen finden Sie im Artikel [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetcantransact"></a><a name="cantransact"></a>CRecordset::CanTransact

Bestimmt, ob das Recordset Transaktionen zulässt.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Recordset Transaktionen zulässt; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="crecordsetcanupdate"></a><a name="canupdate"></a>CRecordset::CanUpdate

Bestimmt, ob das Recordset aktualisiert werden kann.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Recordset aktualisiert werden kann; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Ein Recordset kann schreibgeschützt sein, wenn die zugrunde liegende `CRecordset::readOnly` Datenquelle schreibgeschützt ist oder wenn Sie beim Öffnen des Recordsets im Parameter *dwOptions* angegeben haben.

## <a name="crecordsetcheckrowseterror"></a><a name="checkrowseterror"></a>CRecordset::CheckRowsetError

Wird aufgerufen, um Fehler zu behandeln, die beim Abrufen von Datensätzen generiert wurden.

```
virtual void CheckRowsetError(RETCODE nRetCode);
```

### <a name="parameters"></a>Parameter

*nRetCode*<br/>
Ein ODBC-API-Funktionsrückgabecode. Einzelheiten finden Sie unter "Hinweise".

### <a name="remarks"></a>Bemerkungen

Diese funktion als virtuelle S-Member behandelt Fehler, die beim Abrufen von Datensätzen auftreten, und ist beim Abrufen von Massenzeilen nützlich. Sie sollten das Überschreiben `CheckRowsetError` in Betracht ziehen, um Ihre eigene Fehlerbehandlung zu implementieren.

`CheckRowsetError`wird automatisch in einem Cursornavigationsvorgang `Open` `Requery`aufgerufen, `Move` z. B. , oder einem beliebigen Vorgang. Es wird der Rückgabewert der ODBC-API-Funktion `SQLExtendedFetch`übergeben. In der folgenden Tabelle sind die möglichen Werte für den Parameter *nRetCode* aufgeführt.

|nRetCode|BESCHREIBUNG|
|--------------|-----------------|
|SQL_SUCCESS|Funktion erfolgreich abgeschlossen; Es sind keine zusätzlichen Informationen verfügbar.|
|Sql_success_with_info|Die Funktion wurde erfolgreich abgeschlossen, möglicherweise mit einem nicht schwerwiegenden Fehler. Weitere Informationen erhalten Sie `SQLError`unter .|
|SQL_NO_DATA_FOUND|Alle Zeilen aus dem Resultset wurden abgerufen.|
|SQL_ERROR|Funktion fehlgeschlagen. Weitere Informationen erhalten Sie `SQLError`unter .|
|SQL_INVALID_HANDLE|Die Funktion ist aufgrund eines ungültigen Umgebungshandles, Verbindungshandles oder Anweisungshandles fehlgeschlagen. Dies weist auf einen Programmierfehler hin. Weitere Informationen sind `SQLError`unter nicht verfügbar.|
|SQL_STILL_EXECUTING|Eine Funktion, die asynchron gestartet wurde, wird immer noch ausgeführt. Beachten Sie, dass MFC diesen Wert `CheckRowsetError`standardmäßig niemals an übergeben wird. MFC ruft `SQLExtendedFetch` so lange an, bis es nicht mehr SQL_STILL_EXECUTING zurückkehrt.|

Weitere Informationen `SQLError`zu finden Sie unter Windows SDK. Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetclose"></a><a name="close"></a>CRecordset::Schließen

Schließt das Recordset.

```
virtual void Close();
```

### <a name="remarks"></a>Bemerkungen

Der ODBC HSTMT und der gesamte Speicher, der dem Recordset zugewiesen wurde, werden verteilt. Normalerweise löschen `Close`Sie nach dem Aufruf das C++-Recordset-Objekt, wenn es mit **neuen**zugeordnet wurde.

Sie können `Open` nach `Close`dem Aufruf erneut anrufen. Auf diese Weise können Sie das Recordset-Objekt wiederverwenden. Die Alternative ist, anzurufen. `Requery`

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]

## <a name="crecordsetcrecordset"></a><a name="crecordset"></a>CRecordset::CRecordset

Erstellt ein `CRecordset`-Objekt.

```
CRecordset(CDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>Parameter

*pDatabase*<br/>
Enthält einen Zeiger `CDatabase` auf ein Objekt oder den Wert NULL. Wenn nicht NULL `CDatabase` und `Open` die Memberfunktion des Objekts aufgerufen wurden, um es mit der Datenquelle zu `Open` verbinden, versucht das Recordset, es während seines eigenen Aufrufs für Sie zu öffnen. Wenn Sie NULL `CDatabase` übergeben, wird ein Objekt erstellt und verbunden, das für Sie mithilfe der Datenquelleninformationen verwendet wird, die Sie beim Ableiten der Recordset-Klasse mit ClassWizard angegeben haben.

### <a name="remarks"></a>Bemerkungen

Sie können `CRecordset` entweder direkt verwenden oder eine `CRecordset`anwendungsspezifische Klasse von ableiten. Sie können ClassWizard verwenden, um Ihre Recordset-Klassen abzuleiten.

> [!NOTE]
> Eine abgeleitete Klasse *muss* einen eigenen Konstruktor bereitstellen. Rufen Sie im Konstruktor der abgeleiteten `CRecordset::CRecordset`Klasse den Konstruktor auf und übergeben Sie die entsprechenden Parameter an ihn weiter.

Übergeben Sie NULL an Ihren Recordset-Konstruktor, damit ein `CDatabase` Objekt automatisch für Sie erstellt und verbunden ist. Dies ist eine nützliche Abkürzung, bei der `CDatabase` Sie vor dem Erstellen des Recordsets kein Objekt erstellen und verbinden müssen.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Artikel [Recordset: Deklarieren einer Klasse für eine Tabelle (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).

## <a name="crecordsetdelete"></a><a name="delete"></a>CRecordset::Delete

Löscht den aktuellen Datensatz.

```
virtual void Delete();
```

### <a name="remarks"></a>Bemerkungen

Nach einem erfolgreichen Löschen werden die Felddatenmember des Recordsets auf einen Nullwert `Move` festgelegt, und Sie müssen explizit eine der Funktionen aufrufen, um den gelöschten Datensatz zu entfernen. Sobald Sie den gelöschten Datensatz entfernt haben, ist es nicht mehr möglich, zu ihm zurückzukehren. Wenn die Datenquelle Transaktionen unterstützt, können `Delete` Sie den Aufruf zum Teil einer Transaktion machen. Weitere Informationen finden Sie im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

> [!NOTE]
> Wenn Sie das Abrufen von Massenzeilen `Delete`implementiert haben, können Sie nicht aufrufen. Dies führt zu einer fehlgeschlagenen Behauptung. Obwohl `CRecordset` die Klasse keinen Mechanismus zum Aktualisieren von Massendatenzeilen bereitstellt, können Sie `SQLSetPos`ihre eigenen Funktionen mithilfe der ODBC-API-Funktion schreiben. Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!CAUTION]
> Das Recordset muss updaierbar sein, und beim Aufruf `Delete`muss ein gültiger Datensatz im Recordset vorhanden sein. Andernfalls tritt ein Fehler auf. Wenn Sie z. B. einen Datensatz löschen, aber `Delete` nicht `Delete` zu einem neuen Datensatz scrollen, bevor Sie erneut aufrufen, wird eine [CDBException](../../mfc/reference/cdbexception-class.md)ausgelöst.

Im Gegensatz zu [AddNew](#addnew) `Delete` und [Edit](#edit)wird einem Aufruf nicht ein Aufruf von [Update](#update)folgen. Wenn `Delete` ein Aufruf fehlschlägt, bleiben die Felddatenmember unverändert.

### <a name="example"></a>Beispiel

Dieses Beispiel zeigt ein Recordset, das auf dem Frame einer Funktion erstellt wurde. Im Beispiel wird `m_dbCust`das Vorhandensein von `CDatabase` angenommen, eine Membervariable des Typs, die bereits mit der Datenquelle verbunden ist.

[!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]

## <a name="crecordsetdobulkfieldexchange"></a><a name="dobulkfieldexchange"></a>CRecordset::DoBulkFieldExchange

Wird aufgerufen, um Massendaten von der Datenquelle in das Recordset auszutauschen. Implementiert Massendatensatzfeldaustausch (Bulk RFX).

```
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein [CFieldExchange-Objekt.](../../mfc/reference/cfieldexchange-class.md) Das Framework hat dieses Objekt bereits eingerichtet, um einen Kontext für den Feldaustauschvorgang anzugeben.

### <a name="remarks"></a>Bemerkungen

Wenn das Abrufen von Massenzeilen implementiert ist, ruft das Framework diese Memberfunktion auf, um Automatisch Daten aus der Datenquelle an das Recordset-Objekt zu übertragen. `DoBulkFieldExchange`Bindet ihre Parameterdatenmember ggf. auch an Parameterplatzhalter in der SQL-Anweisungszeichenfolge für die Auswahl des Recordsets.

Wenn das Abrufen von Massenzeilen nicht implementiert ist, ruft das Framework [DoFieldExchange](#dofieldexchange)auf. Um das Abrufen von Massenzeilen `CRecordset::useMultiRowFetch` zu implementieren, müssen Sie die Option des *Parameters dwOptions* in der [Memberfunktion Öffnen](#open) angeben.

> [!NOTE]
> `DoBulkFieldExchange`ist nur verfügbar, wenn Sie `CRecordset`eine von abgeleitete Klasse verwenden. Wenn Sie ein Recordset-Objekt `CRecordset`direkt aus erstellt haben, müssen Sie die [GetFieldValue-Memberfunktion](#getfieldvalue) aufrufen, um Daten abzurufen.

Der Massendatensatzfeldaustausch (Bulk RFX) ähnelt dem Datensatzfeldaustausch (RFX). Daten werden automatisch von der Datenquelle an das Recordset-Objekt übertragen. Sie können jedoch `AddNew` `Edit`nicht `Delete`, `Update` , oder Änderungen zurück in die Datenquelle übertragen. Die `CRecordset` Klasse bietet derzeit keinen Mechanismus zum Aktualisieren von Massendatenzeilen. Sie können jedoch Ihre eigenen Funktionen mit der `SQLSetPos`ODBC-API-Funktion schreiben.

Beachten Sie, dass ClassWizard den Massendatensatzfeldaustausch nicht unterstützt. Daher müssen Sie `DoBulkFieldExchange` manuell überschreiben, indem Sie Aufrufe an die Bulk RFX-Funktionen schreiben. Weitere Informationen zu diesen Funktionen finden Sie im Thema [Datensatzfeldaustauschfunktionen](../../mfc/reference/record-field-exchange-functions.md).

Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Weitere Informationen finden Sie im Artikel [Datensatzfeldaustausch (RFX)](../../data/odbc/record-field-exchange-rfx.md).

## <a name="crecordsetdofieldexchange"></a><a name="dofieldexchange"></a>CRecordset::DoFieldExchange

Wird aufgerufen, um Daten (in beide Richtungen) zwischen den Felddatenelementen des Recordsets und dem entsprechenden Datensatz in der Datenquelle auszutauschen. Implementiert Datensatzfeldaustausch (RFX).

```
virtual void DoFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein [CFieldExchange-Objekt.](../../mfc/reference/cfieldexchange-class.md) Das Framework hat dieses Objekt bereits eingerichtet, um einen Kontext für den Feldaustauschvorgang anzugeben.

### <a name="remarks"></a>Bemerkungen

Wenn das Abrufen von Massenzeilen nicht implementiert ist, ruft das Framework diese Memberfunktion auf, um automatisch Daten zwischen den Felddatenmembern des Recordset-Objekts und den entsprechenden Spalten des aktuellen Datensatzes in der Datenquelle auszutauschen. `DoFieldExchange`Bindet ihre Parameterdatenmember ggf. auch an Parameterplatzhalter in der SQL-Anweisungszeichenfolge für die Auswahl des Recordsets.

Wenn das Abrufen von Massenzeilen implementiert ist, ruft das Framework [DoBulkFieldExchange](#dobulkfieldexchange)auf. Um das Abrufen von Massenzeilen `CRecordset::useMultiRowFetch` zu implementieren, müssen Sie die Option des *Parameters dwOptions* in der [Memberfunktion Öffnen](#open) angeben.

> [!NOTE]
> `DoFieldExchange`ist nur verfügbar, wenn Sie `CRecordset`eine von abgeleitete Klasse verwenden. Wenn Sie ein Recordset-Objekt `CRecordset`direkt aus erstellt haben, müssen Sie die [GetFieldValue-Memberfunktion](#getfieldvalue) aufrufen, um Daten abzurufen.

Der Austausch von Felddaten, genannt Datensatzfeldaustausch (RFX), funktioniert in beide Richtungen: von den Felddatenmembern des Recordset-Objekts zu den Feldern des Datensatzes in der Datenquelle und vom Datensatz in der Datenquelle bis zum Recordset-Objekt.

Die einzige Aktion, die `DoFieldExchange` Sie normalerweise für die abgeleitete Recordset-Klasse implementieren müssen, besteht darin, die Klasse mit ClassWizard zu erstellen und die Namen und Datentypen der Felddatenmember anzugeben. Sie können auch Code hinzufügen, was ClassWizard schreibt, um Parameterdatenmember anzugeben oder um mit allen Spalten umzugehen, die Sie dynamisch binden. Weitere Informationen finden Sie im Artikel [Recordset: Dynamically Binding Data Columns (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Wenn Sie Die abgeleitete Recordset-Klasse mit ClassWizard `DoFieldExchange` deklarieren, schreibt der Assistent eine Außerkraftsetzung von für Sie, die dem folgenden Beispiel ähnelt:

[!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]

Weitere Informationen zu den RFX-Funktionen finden Sie im Thema [Datensatzfeldaustauschfunktionen](../../mfc/reference/record-field-exchange-functions.md).

Weitere Beispiele und `DoFieldExchange`Details zu , siehe den Artikel [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md). Allgemeine Informationen zu RFX finden Sie im Artikel [Datensatzfeldaustausch](../../data/odbc/record-field-exchange-rfx.md).

## <a name="crecordsetedit"></a><a name="edit"></a>CRecordset::Bearbeiten

Ermöglicht Änderungen am aktuellen Datensatz.

```
virtual void Edit();
```

### <a name="remarks"></a>Bemerkungen

Nach dem `Edit`Aufruf können Sie die Felddatenelemente ändern, indem Sie deren Werte direkt zurücksetzen. Der Vorgang wird abgeschlossen, wenn Sie anschließend die [Memberfunktion Aktualisieren](#update) aufrufen, um ihre Änderungen in der Datenquelle zu speichern.

> [!NOTE]
> Wenn Sie das Abrufen von Massenzeilen `Edit`implementiert haben, können Sie nicht aufrufen. Dies führt zu einer fehlgeschlagenen Behauptung. Obwohl `CRecordset` die Klasse keinen Mechanismus zum Aktualisieren von Massendatenzeilen bereitstellt, können Sie `SQLSetPos`ihre eigenen Funktionen mithilfe der ODBC-API-Funktion schreiben. Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`Edit`speichert die Werte der Datenmember des Recordsets. Wenn Sie `Edit`aufrufen , Änderungen `Edit` vornehmen und dann erneut aufrufen, werden die Werte `Edit` des Datensatzes auf das zurückgestellt, was sie vor dem ersten Aufruf waren.

In einigen Fällen können Sie eine Spalte aktualisieren, indem Sie sie null machen (ohne Daten). Rufen Sie dazu [SetFieldNull](#setfieldnull) mit dem Parameter TRUE auf, um das Feld Null zu markieren. Dadurch wird auch die Spalte aktualisiert. Wenn ein Feld in die Datenquelle geschrieben werden soll, obwohl sich sein Wert nicht geändert hat, rufen Sie [SetFieldDirty](#setfielddirty) mit dem Parameter TRUE auf. Dies funktioniert auch dann, wenn das Feld den Wert Null hat.

Wenn die Datenquelle Transaktionen unterstützt, können `Edit` Sie den Aufruf zum Teil einer Transaktion machen. Beachten Sie, dass Sie [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) aufrufen sollten, bevor Sie aufrufen `Edit` und nachdem das Recordset geöffnet wurde. Beachten Sie außerdem, dass das Aufrufen von [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) kein Ersatz für Aufrufe `Update` zum Abschließen des `Edit` Vorgangs ist. Weitere Informationen zu Transaktionen finden Sie unter Klasse [CDatabase](../../mfc/reference/cdatabase-class.md).

Je nach aktuellem Sperrmodus wird der aktualisierte Datensatz möglicherweise gesperrt, `Edit` bis Sie einen anderen Datensatz aufrufen `Update` oder zu einem anderen Datensatz scrollen, oder er wird nur während des `Edit` Anrufs gesperrt. Sie können den Sperrmodus mit [SetLockingMode](#setlockingmode)ändern.

Der vorherige Wert des aktuellen Datensatzes wird wiederhergestellt, `Update`wenn Sie vor dem Aufruf zu einem neuen Datensatz scrollen. A `CDBException` wird ausgelöst, `Edit` wenn Sie ein Recordset aufrufen, das nicht aktualisiert werden kann, oder wenn kein aktueller Datensatz vorhanden ist.

Weitere Informationen finden Sie in den Artikeln [Transaction (ODBC)](../../data/odbc/transaction-odbc.md) und [Recordset: Locking Records (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]

## <a name="crecordsetflushresultset"></a><a name="flushresultset"></a>CRecordset::FlushResultSet

Ruft das nächste Resultset einer vordefinierten Abfrage (gespeicherte Prozedur) ab, wenn mehrere Resultsets vorhanden sind.

```
BOOL FlushResultSet();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn weitere Resultsets abgerufen werden sollen. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie sollten `FlushResultSet` nur aufrufen, wenn Sie mit dem Cursor auf dem aktuellen Resultset vollständig fertig sind. Beachten Sie, dass der Cursor `FlushResultSet`beim Abrufen des nächsten Resultsets durch Aufrufen für dieses Resultset ungültig ist. Sie sollten die [MoveNext-Memberfunktion](#movenext) aufrufen, nachdem Sie aufgerufen `FlushResultSet`haben.

Wenn eine vordefinierte Abfrage einen Ausgabeparameter oder Eingabe-/Ausgabeparameter verwendet, müssen Sie aufrufen, `FlushResultSet` bis sie zurückkehrt `FALSE` (der Wert 0), um diese Parameterwerte zu erhalten.

`FlushResultSet`ruft die ODBC-API-Funktion `SQLMoreResults`auf. Wenn `SQLMoreResults` SQL_ERROR oder SQL_INVALID_HANDLE `FlushResultSet` zurückgegeben wird, wird eine Ausnahme ausgelöst. Weitere Informationen `SQLMoreResults`zu finden Sie unter Windows SDK.

Ihre gespeicherte Prozedur muss über gebundene `FlushResultSet`Felder verfügen, wenn Sie aufrufen möchten.

### <a name="example"></a>Beispiel

Der folgende Code `COutParamRecordset` geht `CRecordset`davon aus, dass es sich um ein -derived-Objekt handelt, das auf einer vordefinierten Abfrage mit einem Eingabeparameter und einem Ausgabeparameter basiert und über mehrere Resultsets verfügt. Beachten Sie die Struktur der [DoFieldExchange-Überschreibung.](#dofieldexchange)

[!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]

[!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]

## <a name="crecordsetgetbookmark"></a><a name="getbookmark"></a>CRecordset::GetBookmark

Ruft den Lesezeichenwert für den aktuellen Datensatz ab.

```cpp
void GetBookmark(CDBVariant& varBookmark);
```

### <a name="parameters"></a>Parameter

*varBookmark*<br/>
Ein Verweis auf ein [CDBVariant-Objekt,](../../mfc/reference/cdbvariant-class.md) das die Textmarke auf dem aktuellen Datensatz darstellt.

### <a name="remarks"></a>Bemerkungen

Um zu ermitteln, ob Lesezeichen auf dem Recordset unterstützt werden, rufen Sie [CanBookmark](#canbookmark)auf. Um Lesezeichen verfügbar zu machen, wenn sie `CRecordset::useBookmarks` unterstützt werden, müssen Sie die Option im Parameter *dwOptions* der [Memberfunktion Öffnen](#open) festlegen.

> [!NOTE]
> Wenn Lesezeichen nicht unterstützt werden `GetBookmark` oder nicht verfügbar sind, führt der Aufruf dazu, dass eine Ausnahme ausgelöst wird. Lesezeichen werden in Vorwärts-Recordsets nicht unterstützt.

`GetBookmark`weist einem `CDBVariant` Objekt den Wert der Textmarke für den aktuellen Datensatz zu. Um nach dem Wechsel zu einem anderen Datensatz jederzeit zu diesem `CDBVariant` Datensatz zurückzukehren, rufen Sie [SetBookmark](#setbookmark) mit dem entsprechenden Objekt auf.

> [!NOTE]
> Nach bestimmten Recordset-Vorgängen sind Lesezeichen möglicherweise nicht mehr gültig. Wenn Sie z. `GetBookmark` B. gefolgt von `Requery`aufrufen, können Sie `SetBookmark`möglicherweise nicht zum Datensatz mit zurückkehren. Rufen Sie [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) auf, `SetBookmark`um zu überprüfen, ob Sie sicher aufrufen können.

Weitere Informationen zur Lesezeichen- und Recordsetnavigation finden Sie in den Artikeln [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) und [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetgetdefaultconnect"></a><a name="getdefaultconnect"></a>CRecordset::GetDefaultConnect

Wird aufgerufen, um die Standardverbindungszeichenfolge abzubekommen.

```
virtual CString GetDefaultConnect();
```

### <a name="return-value"></a>Rückgabewert

A, `CString` das die Standardverbindungszeichenfolge enthält.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Memberfunktion auf, um die Standardverbindungszeichenfolge für die Datenquelle abzuruft, auf der das Recordset basiert. ClassWizard implementiert diese Funktion für Sie, indem dieselbe Datenquelle identifiziert wird, die Sie in ClassWizard verwenden, um Informationen zu Tabellen und Spalten abzubekommen. Sie werden es wahrscheinlich bequem finden, sich auf diese Standardverbindung zu verlassen, während Sie Ihre Anwendung entwickeln. Die Standardverbindung ist jedoch möglicherweise nicht für Benutzer Ihrer Anwendung geeignet. Wenn dies der Fall ist, sollten Sie diese Funktion erneut implementieren und die Version von ClassWizard verwerfen. Weitere Informationen zu Verbindungszeichenfolgen finden Sie im Artikel [Datenquelle (ODBC)](../../data/odbc/data-source-odbc.md).

## <a name="crecordsetgetdefaultsql"></a><a name="getdefaultsql"></a>CRecordset::GetDefaultSQL

Wird aufgerufen, um die standardmäßige SQL-Zeichenfolge auszuführen.

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>Rückgabewert

A, `CString` das die SQL-Standardanweisung enthält.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Memberfunktion auf, um die SQL-Standardanweisung abzuruft, auf der das Recordset basiert. Dies kann ein Tabellenname oder eine SQL **SELECT-Anweisung** sein.

Sie definieren indirekt die SQL-Standardanweisung, indem Sie die Recordset-Klasse mit ClassWizard deklarieren, und ClassWizard führt diese Aufgabe für Sie aus.

Wenn Sie die SQL-Anweisungszeichenfolge für `GetSQL`Ihre eigene Verwendung benötigen, rufen Sie , die die SQL-Anweisung zurückgibt, die verwendet wird, um die Datensätze des Recordsets auszuwählen, als es geöffnet wurde. Sie können die SQL-Standardzeichenfolge in der `GetDefaultSQL`Außerkraftsetzung von . Sie können z. B. mithilfe einer **CALL-Anweisung** einen Aufruf einer vordefinierten Abfrage angeben. (Beachten Sie jedoch, dass `GetDefaultSQL`Sie beim Bearbeiten `m_nFields` auch ändern müssen, um der Anzahl der Spalten in der Datenquelle zu entsprechen.)

Weitere Informationen finden Sie im Artikel [Recordset: Deklarieren einer Klasse für eine Tabelle (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).

> [!CAUTION]
> Der Tabellenname ist leer, wenn das Framework keinen Tabellennamen identifizieren konnte, wenn mehrere Tabellennamen angegeben wurden oder wenn eine **CALL-Anweisung** nicht interpretiert werden konnte. Beachten Sie, dass Sie bei der Verwendung einer **CALL-Anweisung** weder Leerzeichen zwischen der geschweiften Klammer und dem **CALL-Schlüsselwort** einfügen dürfen, noch Leerzeichen vor der geschweiften Klammer oder vor dem **SCHLÜSSELwort SELECT** in eine **SELECT-Anweisung** einfügen sollten.

## <a name="crecordsetgetfieldvalue"></a><a name="getfieldvalue"></a>CRecordset::GetFieldValue

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

*lpszName*<br/>
Der Name eines Felds.

*varValu*e Ein Verweis auf ein [CDBVariant-Objekt,](../../mfc/reference/cdbvariant-class.md) das den Wert des Felds speichert.

*nFieldType*<br/>
Der ODBC C-Datentyp des Felds. Mit dem Standardwert DEFAULT_FIELD_TYPE, um `GetFieldValue` den C-Datentyp aus dem SQL-Datentyp basierend auf der folgenden Tabelle zu bestimmen. Andernfalls können Sie den Datentyp direkt angeben oder einen kompatiblen Datentyp auswählen. Sie können z. B. einen beliebigen Datentyp in SQL_C_CHAR speichern.

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
Der nullbasierte Index des Felds.

*strValue*<br/>
Ein Verweis auf ein [CString-Objekt,](../../atl-mfc-shared/reference/cstringt-class.md) das den in Text konvertierten Wert des Felds unabhängig vom Datentyp des Felds speichert.

### <a name="remarks"></a>Bemerkungen

Sie können ein Feld entweder nach Namen oder nach Index suchen. Sie können den Feldwert `CDBVariant` entweder in `CString` einem Objekt oder in einem Objekt speichern.

Wenn Sie das Abrufen von Massenzeilen implementiert haben, wird der aktuelle Datensatz immer auf dem ersten Datensatz in einem Rowset positioniert. Um `GetFieldValue` einen Datensatz innerhalb eines bestimmten Rowsets verwenden zu können, müssen Sie zuerst die [SetRowsetCursorPosition-Memberfunktion](#setrowsetcursorposition) aufrufen, um den Cursor in die gewünschte Zeile innerhalb dieses Rowsets zu verschieben. Rufen `GetFieldValue` Sie dann nach dieser Zeile. Um das Abrufen von Massenzeilen `CRecordset::useMultiRowFetch` zu implementieren, müssen Sie die Option des *Parameters dwOptions* in der [Memberfunktion Öffnen](#open) angeben.

Sie können `GetFieldValue` Felder zur Laufzeit dynamisch abrufen, anstatt sie zur Entwurfszeit statisch zu binden. Wenn Sie z. B. ein Recordset-Objekt direkt aus `CRecordset`deklariert haben, müssen Sie die Felddaten abrufen. `GetFieldValue` Datensatzfeldaustausch (RFX) oder Massendatensatzfeldaustausch (Bulk RFX) ist nicht implementiert.

> [!NOTE]
> Wenn Sie ein Recordset-Objekt deklarieren, ohne von abzuleiten, `CRecordset`müssen Sie die ODBC-Cursorbibliothek nicht geladen haben. Die Cursorbibliothek erfordert, dass das Recordset über mindestens eine gebundene Spalte verfügt. Wenn Sie jedoch `CRecordset` direkt verwenden, ist keine der Spalten gebunden. Die Memberfunktionen [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) und [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) steuern, ob die Cursorbibliothek geladen wird.

`GetFieldValue`ruft die ODBC-API-Funktion `SQLGetData`auf. Wenn der Treiber den Wert SQL_NO_TOTAL für die tatsächliche `GetFieldValue` Länge des Feldwerts ausgibt, wird eine Ausnahme ausgelöst. Weitere Informationen `SQLGetData`zu finden Sie unter Windows SDK.

### <a name="example"></a>Beispiel

Der folgende Beispielcode veranschaulicht `GetFieldValue` Aufrufe für ein Recordset-Objekt, das direkt aus `CRecordset`deklariert wurde.

[!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]

> [!NOTE]
> Im Gegensatz zur `CDaoRecordset` `CRecordset` DAO-Klasse `SetFieldValue` verfügt sie nicht über eine Memberfunktion. Wenn Sie ein Objekt `CRecordset`direkt aus erstellen, ist es effektiv schreibgeschützt.

Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetgetodbcfieldcount"></a><a name="getodbcfieldcount"></a>CRecordset::GetODBCFieldCount

Ruft die Gesamtzahl der Felder in Ihrem Recordset-Objekt ab.

```
short GetODBCFieldCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Felder im Recordset.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zum Erstellen von Recordsets finden Sie im Artikel [Recordset: Erstellen und Schließen von Recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

## <a name="crecordsetgetodbcfieldinfo"></a><a name="getodbcfieldinfo"></a>CRecordset::GetODBCFieldInfo

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

*lpszName*<br/>
Der Name eines Felds.

*Fieldinfo*<br/>
Ein Verweis `CODBCFieldInfo` auf eine Struktur.

*nIndex*<br/>
Der nullbasierte Index des Felds.

### <a name="remarks"></a>Bemerkungen

Mit einer Version der Funktion können Sie ein Feld nach Namen suchen. Mit der anderen Version können Sie ein Feld nach Index suchen.

Eine Beschreibung der zurückgegebenen Informationen finden Sie in der [CodBCFieldInfo-Struktur.](../../mfc/reference/codbcfieldinfo-structure.md)

Weitere Informationen zum Erstellen von Recordsets finden Sie im Artikel [Recordset: Erstellen und Schließen von Recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

## <a name="crecordsetgetrecordcount"></a><a name="getrecordcount"></a>CRecordset::GetRecordCount

Bestimmt die Größe des Recordsets.

```
long GetRecordCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Datensätze im Recordset; 0, wenn das Recordset keine Datensätze enthält; oder -1, wenn die Datensatzanzahl nicht ermittelt werden kann.

### <a name="remarks"></a>Bemerkungen

> [!CAUTION]
> Die Rekordanzahl wird als "Hochwassermarke" beibehalten, der höchste Datensatz, der bisher angezeigt wird, wenn sich der Benutzer durch die Datensätze bewegt. Die Gesamtzahl der Datensätze ist erst bekannt, nachdem der Benutzer über den letzten Datensatz hinausgegangen ist. Aus Leistungsgründen wird die Anzahl beim `MoveLast`Aufruf nicht aktualisiert. Um die Datensätze selbst `MoveNext` zu `IsEOF` zählen, rufen Sie wiederholt auf, bis ein Wert ungleich Null zurückgegeben wird. Hinzufügen eines `CRecordset:AddNew` Datensatzes über und `Update` erhöht die Anzahl; Das Löschen `CRecordset::Delete` eines Datensatzes über verringert die Anzahl.

## <a name="crecordsetgetrowsetsize"></a><a name="getrowsetsize"></a>CRecordset::GetRowsetSize

Ruft die aktuelle Einstellung für die Anzahl der Zeilen ab, die Sie während eines bestimmten Abrufs abrufen möchten.

```
DWORD GetRowsetSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Zeilen, die während eines bestimmten Abrufs abgerufen werden sollen.

### <a name="remarks"></a>Bemerkungen

Wenn Sie das Abrufen von Massenzeilen verwenden, ist die Standardgröße des Rowsets beim Öffnen des Recordsets 25. andernfalls ist es 1.

Um das Abrufen von Massenzeilen `CRecordset::useMultiRowFetch` zu implementieren, müssen Sie die Option im *Parameter dwOptions* der [Memberfunktion Öffnen](#open) angeben. Um die Einstellung für die Rowsetgröße zu ändern, rufen Sie [SetRowsetSize](#setrowsetsize)auf.

Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetgetrowsfetched"></a><a name="getrowsfetched"></a>CRecordset::GetRowsFetched

Bestimmt, wie viele Datensätze nach einem Abruf tatsächlich abgerufen wurden.

```
DWORD GetRowsFetched() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Zeilen, die nach einem bestimmten Abruf aus der Datenquelle abgerufen wurden.

### <a name="remarks"></a>Bemerkungen

Dies ist nützlich, wenn Sie das Abrufen von Massenzeilen implementiert haben. Die Rowsetgröße gibt normalerweise an, wie viele Zeilen aus einem Abruf abgerufen werden. Die Gesamtzahl der Zeilen im Recordset wirkt sich jedoch auch darauf aus, wie viele Zeilen in einem Rowset abgerufen werden. Wenn Ihr Recordset beispielsweise über 10 Datensätze mit einer Rowset-Größeneinstellung von 4 `MoveNext` verfügt, führt das Durchlaufen einer Schleife durch das Recordset durch Aufrufen dazu, dass das letzte Rowset nur 2 Datensätze enthält.

Um das Abrufen von Massenzeilen `CRecordset::useMultiRowFetch` zu implementieren, müssen Sie die Option im *Parameter dwOptions* der [Memberfunktion Öffnen](#open) angeben. Um die Rowsetgröße anzugeben, rufen Sie [SetRowsetSize](#setrowsetsize)auf.

Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]

## <a name="crecordsetgetrowstatus"></a><a name="getrowstatus"></a>CRecordset::GetRowStatus

Ruft den Status für eine Zeile im aktuellen Rowset ab.

```
WORD GetRowStatus(WORD wRow) const;
```

### <a name="parameters"></a>Parameter

*wRow*<br/>
Die one-basierte Position einer Zeile im aktuellen Rowset. Dieser Wert kann zwischen 1 und der Größe des Rowsets liegen.

### <a name="return-value"></a>Rückgabewert

Ein Statuswert für die Zeile. Einzelheiten finden Sie unter "Hinweise".

### <a name="remarks"></a>Bemerkungen

`GetRowStatus`gibt einen Wert zurück, der entweder eine Änderung des Status der Zeile seit dem letzten Abruf aus der Datenquelle angibt oder dass keine Zeile abgerufen wurde, die *wRow* entspricht. In der folgenden Tabelle sind die möglichen Rückgabewerte aufgelistet:

|Statuswert|BESCHREIBUNG|
|------------------|-----------------|
|SQL_ROW_SUCCESS|Die Zeile ist unverändert.|
|SQL_ROW_UPDATED|Die Zeile wurde aktualisiert.|
|SQL_ROW_DELETED|Die Zeile wurde gelöscht.|
|SQL_ROW_ADDED|Die Zeile wurde hinzugefügt.|
|SQL_ROW_ERROR|Die Zeile ist aufgrund eines Fehlers nicht wiederhersetzbar.|
|SQL_ROW_NOROW|Es gibt keine Zeile, die *wRow*entspricht.|

Weitere Informationen finden Sie in `SQLExtendedFetch` der ODBC-API-Funktion im Windows SDK.

## <a name="crecordsetgetstatus"></a><a name="getstatus"></a>CRecordset::GetStatus

Bestimmt den Index des aktuellen Datensatzes im Recordset und ob der letzte Datensatz gesehen wurde.

```cpp
void GetStatus(CRecordsetStatus& rStatus) const;
```

### <a name="parameters"></a>Parameter

*rStatus*<br/>
Ein Verweis auf ein `CRecordsetStatus`-Objekt. Weitere Informationen finden Sie im Abschnitt zu den Hinweisen.

### <a name="remarks"></a>Bemerkungen

`CRecordset`versucht, den Index zu verfolgen, aber unter bestimmten Umständen ist dies möglicherweise nicht möglich. Eine Erklärung finden Sie unter [GetRecordCount.](#getrecordcount)

Die `CRecordsetStatus` Struktur hat die folgende Form:

```cpp
struct CRecordsetStatus
{
    long m_lCurrentRecord;
    BOOL m_bRecordCountFinal;
};
```

Die beiden `CRecordsetStatus` Mitglieder von haben folgende Bedeutungen:

- `m_lCurrentRecord`Enthält den nullbasierten Index des aktuellen Datensatzes im Recordset, sofern bekannt. Wenn der Index nicht ermittelt werden kann, enthält dieses Element AFX_CURRENT_RECORD_UNDEFINED (-2). Wenn `IsBOF` TRUE (leeres Recordset oder Versuch, `m_lCurrentRecord` vor dem ersten Datensatz zu scrollen), wird auf AFX_CURRENT_RECORD_BOF (-1) gesetzt. Wenn auf dem ersten Datensatz, dann wird es auf 0, zweiten Datensatz 1, und so weiter gesetzt.

- `m_bRecordCountFinal`Ein Wert ungleich Null, wenn die Gesamtzahl der Datensätze im Recordset ermittelt wurde. Im Allgemeinen muss dies erreicht werden, indem `MoveNext` am `IsEOF` Anfang des Recordsets begonnen und aufgerufen wird, bis ein Wert von ungleich Null zurückgegeben wird. Wenn dieses Element Null ist, ist `GetRecordCount`die Datensatzanzahl als zurückgegeben von , wenn nicht -1, nur eine "hohe Wassermarke" der Datensätze.

## <a name="crecordsetgetsql"></a><a name="getsql"></a>CRecordset::GetSQL

Rufen Sie diese Memberfunktion auf, um die SQL-Anweisung abzurufen, die zum Auswählen der Datensätze des Recordsets beim Öffnen verwendet wurde.

```
const CString& GetSQL() const;
```

### <a name="return-value"></a>Rückgabewert

Ein **const-Verweis** auf eine, `CString` der die SQL-Anweisung enthält.

### <a name="remarks"></a>Bemerkungen

Dies ist im **SELECT** Allgemeinen eine SQL SELECT-Anweisung. Die von `GetSQL` zurückgegebene Zeichenfolge ist schreibgeschützt.

Die zurückgegebene `GetSQL` Zeichenfolge unterscheidet sich in der Regel von jeder Zeichenfolge, die `Open` Sie möglicherweise an das Recordset im *lpszSQL-Parameter* an die Memberfunktion übergeben haben. Dies liegt daran, dass das Recordset eine vollständige `Open`SQL-Anweisung erstellt, basierend auf dem, `m_strFilter` was `m_strSort` Sie an übergeben haben, was Sie mit ClassWizard angegeben haben, was Sie möglicherweise in den und Datenmembern angegeben haben, und alle Parameter, die Sie möglicherweise angegeben haben. Weitere Informationen dazu, wie das Recordset diese SQL-Anweisung erstellt, finden Sie im Artikel [Recordset: How Recordsets Select Records (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

> [!NOTE]
> Rufen Sie diese Memberfunktion erst auf, nachdem Sie [Open](#open)aufgerufen haben.

## <a name="crecordsetgettablename"></a><a name="gettablename"></a>CRecordset::GetTableName

Ruft den Namen der SQL-Tabelle ab, auf der die Abfrage des Recordsets basiert.

```
const CString& GetTableName() const;
```

### <a name="return-value"></a>Rückgabewert

Ein **const-Verweis** auf eine, `CString` die den Tabellennamen enthält, wenn das Recordset auf einer Tabelle basiert; Andernfalls eine leere Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

`GetTableName`ist nur gültig, wenn das Recordset auf einer Tabelle basiert, nicht auf einer Verknüpfung mehrerer Tabellen oder einer vordefinierten Abfrage (gespeicherte Prozedur). Der Name ist schreibgeschützt.

> [!NOTE]
> Rufen Sie diese Memberfunktion erst auf, nachdem Sie [Open](#open)aufgerufen haben.

## <a name="crecordsetisbof"></a><a name="isbof"></a>CRecordset::IsBOF

Gibt einen Wert ungleich Null zurück, wenn das Recordset vor dem ersten Datensatz positioniert wurde. Es ist kein aktueller Datensatz vorhanden.

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Recordset keine Datensätze enthält oder wenn Sie vor dem ersten Datensatz rückwärts gescrollt haben; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Memberfunktion auf, bevor Sie von Datensatz zu Datensatz scrollen, um zu erfahren, ob Sie vor dem ersten Datensatz des Recordsets gegangen sind. Sie können `IsBOF` auch `IsEOF` zusammen mit verwenden, um zu bestimmen, ob das Recordset Datensätze enthält oder leer ist. Unmittelbar nach `Open`dem Aufruf gibt zurück, `IsBOF` wenn das Recordset keine Datensätze enthält, einen Wert ungleich Null. Wenn Sie ein Recordset öffnen, das mindestens einen Datensatz enthält, ist der erste Datensatz der aktuelle Datensatz und `IsBOF` gibt 0 zurück.

Wenn der erste Datensatz der aktuelle `MovePrev` `IsBOF` Datensatz ist und Sie aufrufen, wird anschließend ein Wert ungleich Null zurückgegeben. Wenn `IsBOF` ein Fehler ungleich Null zurückgegeben wird und Sie aufrufen, `MovePrev`tritt ein Fehler auf. Wenn `IsBOF` ein Wert ungleich Null zurückgegeben wird, ist der aktuelle Datensatz nicht definiert, und jede Aktion, die einen aktuellen Datensatz erfordert, führt zu einem Fehler.

### <a name="example"></a>Beispiel

In diesem `IsBOF` `IsEOF` Beispiel werden die Grenzen eines Recordsets verwendet und erkannt, wenn der Code in beide Richtungen durch das Recordset scrollt.

[!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]

## <a name="crecordsetisdeleted"></a><a name="isdeleted"></a>CRecordset::IsDeleted

Bestimmt, ob der aktuelle Datensatz gelöscht wurde.

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Recordset auf einem gelöschten Datensatz positioniert ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn Sie zu einem `IsDeleted` Datensatz scrollen und TRUE (ungleich Null) zurückgeben, müssen Sie zu einem anderen Datensatz scrollen, bevor Sie andere Recordset-Vorgänge ausführen können.

Das Ergebnis `IsDeleted` hängt von vielen Faktoren ab, z. B. von Ihrem Recordset-Typ, davon, ob Ihr Recordset aufrüstbar ist, ob Sie die `CRecordset::skipDeletedRecords` Option beim Öffnen des Recordsets angegeben haben, ob der Treiber gelöschte Datensätze packt und ob mehrere Benutzer vorhanden sind.

Weitere Informationen `CRecordset::skipDeletedRecords` zum Und zum Packen des Treibers finden Sie in der Funktion [Öffnen](#open) von Membern.

> [!NOTE]
> Wenn Sie das Abrufen von Massenzeilen `IsDeleted`implementiert haben, sollten Sie nicht aufrufen. Rufen Sie stattdessen die [GetRowStatus-Memberfunktion](#getrowstatus) auf. Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetiseof"></a><a name="iseof"></a>CRecordset::IsEOF

Gibt einen Wert ungleich Null zurück, wenn das Recordset nach dem letzten Datensatz positioniert wurde. Es ist kein aktueller Datensatz vorhanden.

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Recordset keine Datensätze enthält oder wenn Sie über den letzten Datensatz hinaus gescrollt haben; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Memberfunktion auf, während Sie von Datensatz zu Datensatz scrollen, um zu erfahren, ob Sie über den letzten Datensatz des Recordsets hinausgegangen sind. Sie können `IsEOF` auch bestimmen, ob das Recordset Datensätze enthält oder leer ist. Unmittelbar nach `Open`dem Aufruf gibt zurück, `IsEOF` wenn das Recordset keine Datensätze enthält, einen Wert ungleich Null. Wenn Sie ein Recordset öffnen, das mindestens einen Datensatz enthält, ist der erste Datensatz der aktuelle Datensatz und `IsEOF` gibt 0 zurück.

Wenn der letzte Datensatz der aktuelle `MoveNext` `IsEOF` Datensatz ist, wenn Sie aufrufen, wird anschließend ein Wert ungleich Null zurückgegeben. Wenn `IsEOF` ein Fehler ungleich Null zurückgegeben wird und Sie aufrufen, `MoveNext`tritt ein Fehler auf. Wenn `IsEOF` ein Wert ungleich Null zurückgegeben wird, ist der aktuelle Datensatz nicht definiert, und jede Aktion, die einen aktuellen Datensatz erfordert, führt zu einem Fehler.

### <a name="example"></a>Beispiel

Siehe Beispiel für [IsBOF](#isbof).

## <a name="crecordsetisfielddirty"></a><a name="isfielddirty"></a>CRecordset::IsFieldDirty

Bestimmt, ob das angegebene Felddatenelement seit dem Aufruf von [Bearbeiten](#edit) oder [AddNew](#addnew) geändert wurde.

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>Parameter

*Pv*<br/>
Ein Zeiger auf das Felddatenelement, dessen Status Sie überprüfen möchten, oder NULL, um zu bestimmen, ob eines der Felder verschmutzt ist.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn `AddNew` sich `Edit`das angegebene Felddatenelement seit dem Aufruf geändert hat oder ; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Daten in allen schmutzigen Felddatenelementen werden in den Datensatz in der Datenquelle übertragen, wenn der aktuelle `Edit` Datensatz `AddNew`durch einen Aufruf der [Update-Memberfunktion](#update) von `CRecordset` aktualisiert wird (nach einem Aufruf von oder ).

> [!NOTE]
> Diese Memberfunktion ist nicht für Recordsets anwendbar, die Massenzeilenabrufe verwenden. Wenn Sie das Abrufen von `IsFieldDirty` Massenzeilen implementiert haben, wird immer FALSE zurückgegeben, was zu einer fehlgeschlagenen Assertion führt. Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Durch `IsFieldDirty` aufrufen werden die Auswirkungen vorheriger Aufrufe von [SetFieldDirty](#setfielddirty) zurückgesetzt, da der schmutzige Status des Felds neu ausgewertet wird. `AddNew` Wenn sich der aktuelle Feldwert vom Pseudo-Nullwert unterscheidet, wird der Feldstatus als schmutzig festgelegt. Wenn `Edit` sich der Feldwert vom zwischengespeicherten Wert unterscheidet, wird der Feldstatus als schmutzig festgelegt.

`IsFieldDirty`wird über [DoFieldExchange](#dofieldexchange)implementiert.

Weitere Informationen zum schmutzigen Flag finden Sie im Artikel [Recordset: How Recordsets Select Records (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

## <a name="crecordsetisfieldnull"></a><a name="isfieldnull"></a>CRecordset::IsFieldNull

Gibt einen Wert ungleich Null zurück, wenn das angegebene Feld im aktuellen Datensatz Null ist (hat keinen Wert).

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>Parameter

*Pv*<br/>
Ein Zeiger auf das Felddatenelement, dessen Status Sie überprüfen möchten, oder NULL, um zu bestimmen, ob eines der Felder Null ist.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das angegebene Felddatenelement als Null gekennzeichnet ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Memberfunktion auf, um zu bestimmen, ob das angegebene Felddatenelement eines Recordsets als Null gekennzeichnet wurde. (In der Datenbankterminologie bedeutet Null "keinen Wert" und ist nicht identisch mit NULL in C++.) Wenn ein Felddatenelement als Null gekennzeichnet ist, wird es als Spalte des aktuellen Datensatzes interpretiert, für den kein Wert vorhanden ist.

> [!NOTE]
> Diese Memberfunktion ist nicht für Recordsets anwendbar, die Massenzeilenabrufe verwenden. Wenn Sie das Abrufen von `IsFieldNull` Massenzeilen implementiert haben, wird immer FALSE zurückgegeben, was zu einer fehlgeschlagenen Assertion führt. Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`IsFieldNull`wird über [DoFieldExchange](#dofieldexchange)implementiert.

## <a name="crecordsetisfieldnullable"></a><a name="isfieldnullable"></a>CRecordset::IsFieldNullable

Gibt einen Wert ungleich Null zurück, wenn das angegebene Feld im aktuellen Datensatz auf Null festgelegt werden kann (ohne Wert).

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>Parameter

*Pv*<br/>
Ein Zeiger auf das Felddatenelement, dessen Status Sie überprüfen möchten, oder NULL, um zu bestimmen, ob eines der Felder auf einen Nullwert festgelegt werden kann.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Memberfunktion auf, um zu bestimmen, ob das angegebene Felddatenelement "nullable" ist (kann auf einen Nullwert festgelegt werden; C++ NULL ist nicht identisch mit Null, was in der Datenbankterminologie bedeutet, dass "kein Wert" vorhanden ist.

> [!NOTE]
> Wenn Sie das Abrufen von Massenzeilen `IsFieldNullable`implementiert haben, können Sie nicht aufrufen. Rufen Sie stattdessen die [GetODBCFieldInfo-Memberfunktion](#getodbcfieldinfo) auf, um zu bestimmen, ob ein Feld auf einen Null-Wert festgelegt werden kann. Beachten Sie, dass `GetODBCFieldInfo`Sie immer aufrufen können, unabhängig davon, ob Sie das Abrufen von Massenzeilen implementiert haben. Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Ein Feld, das nicht Null sein kann, muss einen Wert haben. Wenn Sie beim Hinzufügen oder Aktualisieren eines Datensatzes versuchen, ein solches Feld auf Null zu setzen, lehnt die Datenquelle das Hinzufügen oder Aktualisieren ab, und [Update](#update) löst eine Ausnahme aus. Die Ausnahme tritt `Update`auf, wenn Sie aufrufen, nicht, wenn Sie [SetFieldNull](#setfieldnull)aufrufen.

Wenn Sie NULL für das erste Argument der `outputColumn` Funktion `param` verwenden, wird die Funktion nur auf Felder und nicht auf Felder angewendet. Zum Beispiel wird der Anruf

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

setzt nur `outputColumn` Felder auf NULL; `param` Felder bleiben davon unberührt.

Um an `param` Feldern zu arbeiten, müssen Sie `param` die tatsächliche Adresse der Person angeben, an der Sie arbeiten möchten, z. B.:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

Dies bedeutet, `param` dass Sie nicht alle `outputColumn` Felder auf NULL festlegen können, wie Sie es mit Feldern können.

`IsFieldNullable`wird über [DoFieldExchange](#dofieldexchange)implementiert.

## <a name="crecordsetisopen"></a><a name="isopen"></a>CRecordset::IsOpen

Bestimmt, ob das Recordset bereits geöffnet ist.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die [Memberfunktion "Öffnen"](#open) oder ["Requery"](#requery) des Recordset-Objekts zuvor aufgerufen wurde und das Recordset nicht geschlossen wurde. andernfalls 0.

## <a name="crecordsetm_hstmt"></a><a name="m_hstmt"></a>CRecordset::m_hstmt

Enthält ein Handle für die ODBC-Anweisungsdatenstruktur vom Typ HSTMT, das dem Recordset zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Jede Abfrage an eine ODBC-Datenquelle ist einem HSTMT zugeordnet.

> [!CAUTION]
> Nicht verwenden, `m_hstmt` bevor [Open](#open) aufgerufen wurde.

Normalerweise müssen Sie nicht direkt auf das HSTMT zugreifen, aber Sie benötigen es möglicherweise für die direkte Ausführung von SQL-Anweisungen. Die `ExecuteSQL` Memberfunktion `CDatabase` der Klasse stellt `m_hstmt`ein Beispiel für die Verwendung von bereit.

## <a name="crecordsetm_nfields"></a><a name="m_nfields"></a>CRecordset::m_nFields

Enthält die Anzahl der Felddatenmember in der Recordset-Klasse; d. h. die Anzahl der Spalten, die vom Recordset aus der Datenquelle ausgewählt wurden.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor für die Recordset-Klasse muss mit der richtigen Zahl initialisiert `m_nFields` werden. Wenn Sie das Abrufen von Massenzeilen nicht implementiert haben, schreibt ClassWizard diese Initialisierung für Sie, wenn Sie sie zum Deklarieren der Recordset-Klasse verwenden. Sie können es auch manuell schreiben.

Das Framework verwendet diese Nummer, um die Interaktion zwischen den Felddatenmembern und den entsprechenden Spalten des aktuellen Datensatzes in der Datenquelle zu verwalten.

> [!CAUTION]
> Diese Nummer muss der Anzahl der "Ausgabespalten" entsprechen, die `DoFieldExchange` in oder `CFieldExchange::outputColumn` `DoBulkFieldExchange` nach einem Aufruf von [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) mit dem Parameter registriert sind.

Sie können Spalten dynamisch binden, wie im Artikel "Recordset: Dynamisch bindende Datenspalten" erläutert. Wenn Sie dies tun, müssen `m_nFields` Sie die Anzahl erhöhen, um die Anzahl `DoFieldExchange` `DoBulkFieldExchange` der RFX- oder Bulk-RFX-Funktionsaufrufe in Ihrer oder Memberfunktion für die dynamisch gebundenen Spalten widerzuspiegeln.

Weitere Informationen finden Sie in den Artikeln [Recordset: Dynamically Binding Data Columns (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) und [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Beispiel

Siehe den Artikel [Record Field Exchange: Using RFX](../../data/odbc/record-field-exchange-using-rfx.md).

## <a name="crecordsetm_nparams"></a><a name="m_nparams"></a>CRecordset::m_nParams

Enthält die Anzahl der Parameterdatenmember in der Recordset-Klasse; das heißt, die Anzahl der Parameter, die mit der Abfrage des Recordsets übergeben wurden.

### <a name="remarks"></a>Bemerkungen

Wenn Ihre Recordset-Klasse Parameterdatenmember enthält, muss der `m_nParams` Konstruktor für die Klasse mit der richtigen Nummer initialisiert werden. Der Wert `m_nParams` von Defaults auf 0. Wenn Sie Parameterdatenmember hinzufügen (was Sie manuell tun müssen), müssen Sie auch manuell eine Initialisierung im Klassenkonstruktor hinzufügen, um die Anzahl der `m_strFilter` Parameter `m_strSort` widerzuspiegeln (die mindestens so groß sein muss wie die Anzahl der ''-Platzhalter in Ihrem oder String).

Das Framework verwendet diese Nummer, wenn es die Abfrage des Recordsets parametrisiert.

> [!CAUTION]
> Diese Nummer muss der Anzahl der in `DoFieldExchange` oder `DoBulkFieldExchange` nach einem Aufruf von [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) registrierten "params" mit dem Parameterwert , `CFieldExchange::inputParam` `CFieldExchange::param`, `CFieldExchange::outputParam`oder `CFieldExchange::inoutParam`entsprechen.

### <a name="example"></a>Beispiel

  Siehe die Artikel [Recordset: Parametrierung eines Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) und [Record Field Exchange: Using RFX](../../data/odbc/record-field-exchange-using-rfx.md).

## <a name="crecordsetm_pdatabase"></a><a name="m_pdatabase"></a>CRecordset::m_pDatabase

Enthält einen Zeiger `CDatabase` auf das Objekt, über das das Recordset mit einer Datenquelle verbunden ist.

### <a name="remarks"></a>Bemerkungen

Diese Variable wird auf zwei Arten festgelegt. In der Regel übergeben Sie beim `CDatabase` Erstellen des Recordset-Objekts einen Zeiger an ein bereits verbundenes Objekt. Wenn Sie stattdessen `CRecordset` NULL `CDatabase` übergeben, erstellt ein Objekt für Sie und verbindet es. In beiden `CRecordset` Fällen wird der Zeiger in dieser Variablen gespeichert.

Normalerweise müssen Sie den in `m_pDatabase`gespeicherten Zeiger nicht direkt verwenden. Wenn Sie jedoch eigene `CRecordset`Erweiterungen für schreiben, müssen Sie möglicherweise den Zeiger verwenden. Sie benötigen z. B. den Zeiger, `CDBException`wenn Sie Ihre eigenen s werfen. Oder Sie benötigen es, wenn Sie etwas `CDatabase` mit demselben Objekt ausführen müssen, z. B. das Ausführen von Transaktionen, das Festlegen von Timeouts oder das Aufrufen der `ExecuteSQL` Memberfunktion der Klasse, `CDatabase` um SQL-Anweisungen direkt auszuführen.

## <a name="crecordsetm_strfilter"></a><a name="m_strfilter"></a>CRecordset::m_strFilter

Nachdem Sie das Recordset-Objekt erstellt `Open` haben, aber bevor Sie seine `CString` Memberfunktion aufrufen, verwenden Sie diesen Datenmember, um eine SQL **WHERE-Klausel** zu speichern.

### <a name="remarks"></a>Bemerkungen

Das Recordset verwendet diese Zeichenfolge, um die Datensätze einzuschränken `Open` (oder zu filtern), die es während des Oder-Aufrufs `Requery` auswählt. Dies ist nützlich, um eine Teilmenge von Datensätzen auszuwählen, z. B. "alle Verkäufer mit Sitz in Kalifornien" ("State = CA"). Die ODBC SQL-Syntax für eine **WHERE-Klausel** ist

`WHERE search-condition`

Beachten Sie, dass Sie das **SCHLÜSSELwort WHERE** nicht in Ihre Zeichenfolge aufnehmen. Der Rahmen liefert sie.

Sie können die Filterzeichenfolge auch parametrisieren, indem Sie ''-Platzhalter darin platzieren, einen Parameterdatenmember in Ihrer Klasse für jeden Platzhalter deklarieren und Parameter zur Laufzeit an das Recordset übergeben. Auf diese Weise können Sie den Filter zur Laufzeit erstellen. Weitere Informationen finden Sie im Artikel [Recordset: Parametrieren eines Recordsets (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

Weitere Informationen zu SQL **WHERE-Klauseln** finden Sie im Artikel [SQL](../../data/odbc/sql.md). Weitere Informationen zum Auswählen und Filtern von Datensätzen finden Sie im Artikel [Recordset: Filtering Records (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]

## <a name="crecordsetm_strsort"></a><a name="m_strsort"></a>CRecordset::m_strSort

Nachdem Sie das Recordset-Objekt erstellt `Open` haben, aber bevor Sie seine `CString` Memberfunktion aufrufen, verwenden Sie diesen Datenmember, um eine SQL **ORDER BY-Klausel** zu speichern.

### <a name="remarks"></a>Bemerkungen

Das Recordset verwendet diese Zeichenfolge, um die `Open` `Requery` Datensätze zu sortieren, die es während des Oder-Aufrufs auswählt. Sie können diese Funktion verwenden, um ein Recordset in einer oder mehreren Spalten zu sortieren. Die ODBC SQL-Syntax für eine **ORDER BY-Klausel** ist

`ORDER BY sort-specification [, sort-specification]...`

wobei eine Sortierspezifikation eine ganze Zahl oder ein Spaltenname ist. Sie können auch aufsteigende oder absteigende Reihenfolge (die Reihenfolge ist standardmäßig aufsteigend) angeben, indem Sie "ASC" oder "DESC" an die Spaltenliste in der Sortierzeichenfolge anhängen. Die ausgewählten Datensätze werden zuerst nach der ersten aufgelisteten Spalte, dann nach der zweiten usw. sortiert. Sie können z. B. ein "Customers"-Recordset nach Nachnamen und dann nach dem Vornamen bestellen. Die Anzahl der Spalten, die Sie auflisten können, hängt von der Datenquelle ab. Weitere Informationen finden Sie im Windows SDK.

Beachten Sie, dass Sie das **Order BY-Schlüsselwort** nicht in Ihre Zeichenfolge aufnehmen. Der Rahmen liefert sie.

Weitere Informationen zu SQL-Klauseln finden Sie im Artikel [SQL](../../data/odbc/sql.md). Weitere Informationen zum Sortieren von Datensätzen finden Sie im Artikel [Recordset: Sorting Records (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]

## <a name="crecordsetmove"></a><a name="move"></a>CRecordset::Bewegen

Verschiebt den aktuellen Datensatzzeiger innerhalb des Recordsets vorwärts oder rückwärts.

```
virtual void Move(
    long nRows,
    WORD wFetchType = SQL_FETCH_RELATIVE);
```

### <a name="parameters"></a>Parameter

*nRows*<br/>
Die Anzahl der Zeilen, die vorwärts oder rückwärts verschoben werden sollen. Positive Werte bewegen sich vorwärts, gegen Ende des Recordsets. Negative Werte bewegen sich rückwärts, zum Anfang.

*wFetchType*<br/>
Bestimmt das Rowset, das `Move` abgerufen wird. Einzelheiten finden Sie unter "Hinweise".

### <a name="remarks"></a>Bemerkungen

Wenn Sie den Wert 0 für `Move` *nRows*übergeben, wird der aktuelle Datensatz aktualisiert. `Move` beendet jeden `AddNew` Strom `Edit` oder Modus und stellt den Wert `AddNew` `Edit` des aktuellen Datensatzes vor oder wurde aufgerufen.

> [!NOTE]
> Wenn Sie sich durch ein Recordset bewegen, können Sie gelöschte Datensätze nicht überspringen. Weitere Informationen finden Sie unter [CRecordset::IsDeleted.](#isdeleted) Wenn Sie `CRecordset` eine `skipDeletedRecords` mit dem `Move` Optionssatz öffnen, wird bestätigt, ob der *NRows-Parameter* 0 ist. Dieses Verhalten verhindert die Aktualisierung von Zeilen, die von anderen Clientanwendungen mit denselben Daten gelöscht werden. Eine *dwOption* Beschreibung von `skipDeletedRecords` [Open](#open) .

`Move`positioniert das Recordset nach Rowsets neu. Basierend auf den Werten für *nRows* und *wFetchType* `Move` ruft das entsprechende Rowset ab und macht dann den ersten Datensatz in diesem Rowset zum aktuellen Datensatz. Wenn Sie das Abrufen von Massenzeilen nicht implementiert haben, ist die Rowsetgröße immer 1. Ruft beim Abrufen eines `Move` Rowsets direkt die [CheckRowsetError-Memberfunktion](#checkrowseterror) auf, um alle Fehler zu behandeln, die sich aus dem Abruf ergeben.

Abhängig von den Werten, die Sie übergeben, `Move` entspricht dies anderen `CRecordset` Memberfunktionen. Insbesondere kann der Wert von *wFetchType* auf eine Memberfunktion hinweisen, die intuitiver ist und häufig die bevorzugte Methode zum Verschieben des aktuellen Datensatzes ist.

In der folgenden Tabelle sind die möglichen Werte `Move` für *wFetchType*, das Rowset, das basierend auf *wFetchType* und *nRows*abruft, sowie alle entsprechenden Memberfunktionen, die *wFetchType*entsprechen, aufgeführt.

|wFetchType|Abgerufenes Rowset|Äquivalente Memberfunktion|
|----------------|--------------------|--------------------------------|
|SQL_FETCH_RELATIVE (der Standardwert)|Das Rowset, das *nRows* row(s) aus der ersten Zeile im aktuellen Rowset startet.||
|SQL_FETCH_NEXT|Das nächste Rowset; *nRows* wird ignoriert.|[MoveNext](#movenext)|
|SQL_FETCH_PRIOR|Das vorherige Rowset; *nRows* wird ignoriert.|[MovePrev](#moveprev)|
|SQL_FETCH_FIRST|Das erste Rowset im Recordset; *nRows* wird ignoriert.|[Movefirst](#movefirst)|
|SQL_FETCH_LAST|Das letzte vollständige Rowset im Recordset; *nRows* wird ignoriert.|[Movelast](#movelast)|
|SQL_FETCH_ABSOLUTE|Wenn *nRows* > 0, das Rowset *startet nRows* row(s) vom Anfang des Recordsets. Wenn *nRows* 0 <, beginnt das Rowset *nRows* row(s) vom Ende des Recordsets. Wenn *nRows* = 0, dann wird eine BOF-Bedingung (Anfang-of-File) zurückgegeben.|[SetAbsolutePosition](#setabsoluteposition)|
|SQL_FETCH_BOOKMARK|Das Rowset, das in der Zeile beginnt, deren Lesezeichenwert *nRows*entspricht.|[SetBookmark](#setbookmark)|

> [!NOTE]
> Für Nur-Forward-Recordsets `Move` ist nur der Wert SQL_FETCH_NEXT für *wFetchType*gültig.

> [!CAUTION]
> Beim `Move` Aufrufen wird eine Ausnahme ausgelöst, wenn das Recordset keine Datensätze enthält. Um zu bestimmen, ob das Recordset Datensätze enthält, rufen Sie [IsBOF](#isbof) und [IsEOF](#iseof)auf.

> [!NOTE]
> Wenn Sie am Anfang oder Ende des Recordsets `IsEOF` vorbei gescrollt `Move` haben (`IsBOF` `CDBException`oder einen Wert ungleich Null zurückgegeben haben), wird durch das Aufrufen einer Funktion möglicherweise eine . Wenn z. `IsEOF` B. `IsBOF` ein Wert `MoveNext` ungleich Null zurückgegeben `MovePrev` wird und dies nicht der Fall ist, wird eine Ausnahme ausgelöst, dies jedoch nicht der Fall ist.

> [!NOTE]
> Wenn Sie `Move` aufrufen, während der aktuelle Datensatz aktualisiert oder hinzugefügt wird, gehen die Aktualisierungen ohne Warnung verloren.

Weitere Informationen zur Recordset-Navigation finden Sie in den Artikeln [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) und [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Weitere Informationen finden Sie in `SQLExtendedFetch` der ODBC-API-Funktion im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]

## <a name="crecordsetmovefirst"></a><a name="movefirst"></a>CRecordset::MoveFirst

Macht den ersten Datensatz im ersten Rowset zum aktuellen Datensatz.

```cpp
void MoveFirst();
```

### <a name="remarks"></a>Bemerkungen

Unabhängig davon, ob das Abrufen von Massenzeilen implementiert wurde, ist dies immer der erste Datensatz im Recordset.

Sie müssen nicht `MoveFirst` sofort anrufen, nachdem Sie das Recordset geöffnet haben. Zu diesem Zeitpunkt ist der erste Datensatz (falls vorhanden) automatisch der aktuelle Datensatz.

> [!NOTE]
> Diese Memberfunktion ist nicht für Forward-Only-Recordsets gültig.

> [!NOTE]
> Wenn Sie sich durch ein Recordset bewegen, können Sie gelöschte Datensätze nicht überspringen. Weitere [IsDeleted](#isdeleted) Informationen finden Sie in der IsDeleted-Memberfunktion.

> [!CAUTION]
> Wenn eine `Move` der Funktionen aufgerufen wird, wird eine Ausnahme ausgelöst, wenn das Recordset keine Datensätze enthält. Um zu bestimmen, ob das `IsBOF` Recordset Datensätze enthält, rufen Sie an und `IsEOF`rufen Sie an.

> [!NOTE]
> Wenn Sie eine `Move` der Funktionen aufrufen, während der aktuelle Datensatz aktualisiert oder hinzugefügt wird, gehen die Aktualisierungen ohne Warnung verloren.

Weitere Informationen zur Recordset-Navigation finden Sie in den Artikeln [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) und [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Beispiel

  Siehe Beispiel für [IsBOF](#isbof).

## <a name="crecordsetmovelast"></a><a name="movelast"></a>CRecordset::MoveLast

Macht den ersten Datensatz im letzten vollständigen Rowset zum aktuellen Datensatz.

```cpp
void MoveLast();
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie das Abrufen von Massenzeilen nicht implementiert haben, hat `MoveLast` Ihr Recordset eine Rowsetgröße von 1.

> [!NOTE]
> Diese Memberfunktion ist nicht für Forward-Only-Recordsets gültig.

> [!NOTE]
> Wenn Sie sich durch ein Recordset bewegen, können Sie gelöschte Datensätze nicht überspringen. Weitere [IsDeleted](#isdeleted) Informationen finden Sie in der IsDeleted-Memberfunktion.

> [!CAUTION]
> Wenn eine `Move` der Funktionen aufgerufen wird, wird eine Ausnahme ausgelöst, wenn das Recordset keine Datensätze enthält. Um zu bestimmen, ob das `IsBOF` Recordset Datensätze enthält, rufen Sie an und `IsEOF`rufen Sie an.

> [!NOTE]
> Wenn Sie eine `Move` der Funktionen aufrufen, während der aktuelle Datensatz aktualisiert oder hinzugefügt wird, gehen die Aktualisierungen ohne Warnung verloren.

Weitere Informationen zur Recordset-Navigation finden Sie in den Artikeln [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) und [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Beispiel

  Siehe Beispiel für [IsBOF](#isbof).

## <a name="crecordsetmovenext"></a><a name="movenext"></a>CRecordset::MoveNext

Macht den ersten Datensatz im nächsten Rowset zum aktuellen Datensatz.

```cpp
void MoveNext();
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie das Abrufen von Massenzeilen nicht implementiert haben, hat `MoveNext` Ihr Recordset eine Rowsetgröße von 1.

> [!NOTE]
> Wenn Sie sich durch ein Recordset bewegen, können Sie gelöschte Datensätze nicht überspringen. Weitere [IsDeleted](#isdeleted) Informationen finden Sie in der IsDeleted-Memberfunktion.

> [!CAUTION]
> Wenn eine `Move` der Funktionen aufgerufen wird, wird eine Ausnahme ausgelöst, wenn das Recordset keine Datensätze enthält. Um zu bestimmen, ob das `IsBOF` Recordset Datensätze enthält, rufen Sie an und `IsEOF`rufen Sie an.

> [!NOTE]
> Es wird auch empfohlen, `MoveNext`dass Sie vor dem Aufruf anrufen. `IsEOF` Wenn Sie z. B. über das Ende `IsEOF` des Recordsets gescrollt haben, wird ein Wert ungleich Null zurückgegeben. ein nachfolgender Aufruf `MoveNext` an würde eine Ausnahme auslösen.

> [!NOTE]
> Wenn Sie eine `Move` der Funktionen aufrufen, während der aktuelle Datensatz aktualisiert oder hinzugefügt wird, gehen die Aktualisierungen ohne Warnung verloren.

Weitere Informationen zur Recordset-Navigation finden Sie in den Artikeln [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) und [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Beispiel

  Siehe Beispiel für [IsBOF](#isbof).

## <a name="crecordsetmoveprev"></a><a name="moveprev"></a>CRecordset::MovePrev

Macht den ersten Datensatz im vorherigen Rowset zum aktuellen Datensatz.

```cpp
void MovePrev();
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie das Abrufen von Massenzeilen nicht implementiert haben, hat `MovePrev` Ihr Recordset eine Rowsetgröße von 1.

> [!NOTE]
> Diese Memberfunktion ist nicht für Forward-Only-Recordsets gültig.

> [!NOTE]
> Wenn Sie sich durch ein Recordset bewegen, können Sie gelöschte Datensätze nicht überspringen. Weitere [IsDeleted](#isdeleted) Informationen finden Sie in der IsDeleted-Memberfunktion.

> [!CAUTION]
> Wenn eine `Move` der Funktionen aufgerufen wird, wird eine Ausnahme ausgelöst, wenn das Recordset keine Datensätze enthält. Um zu bestimmen, ob das `IsBOF` Recordset Datensätze enthält, rufen Sie an und `IsEOF`rufen Sie an.

> [!NOTE]
> Es wird auch empfohlen, `MovePrev`dass Sie vor dem Aufruf anrufen. `IsBOF` Wenn Sie z. B. vor dem Anfang des `IsBOF` Recordsets gescrollt haben, wird ein Wert ungleich Null zurückgegeben. ein nachfolgender Aufruf `MovePrev` an würde eine Ausnahme auslösen.

> [!NOTE]
> Wenn Sie eine `Move` der Funktionen aufrufen, während der aktuelle Datensatz aktualisiert oder hinzugefügt wird, gehen die Aktualisierungen ohne Warnung verloren.

Weitere Informationen zur Recordset-Navigation finden Sie in den Artikeln [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) und [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Beispiel

  Siehe Beispiel für [IsBOF](#isbof).

## <a name="crecordsetonsetoptions"></a><a name="onsetoptions"></a>CRecordset::OnSetOptions

Wird aufgerufen, um Optionen (bei der Auswahl verwendet) für die angegebene ODBC-Anweisung festzulegen.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parameter

*hstmt*<br/>
Die HSTMT der ODBC-Anweisung, deren Optionen festgelegt werden sollen.

### <a name="remarks"></a>Bemerkungen

Rufen `OnSetOptions` Sie die Einstellung von Optionen (bei der Auswahl verwendet) für die angegebene ODBC-Anweisung auf. Das Framework ruft diese Memberfunktion auf, um erste Optionen für das Recordset festzulegen. `OnSetOptions`bestimmt die Unterstützung der Datenquelle für scrollbare Cursor und für Cursorparallelität und legt die Optionen des Recordsets entsprechend fest. (Wird `OnSetOptions` für Auswahlvorgänge `OnSetUpdateOptions` verwendet und wird für Aktualisierungsvorgänge verwendet.)

Überschreiben, `OnSetOptions` um Optionen festzulegen, die für den Treiber oder die Datenquelle spezifisch sind. Wenn Ihre Datenquelle z. B. das Öffnen für `OnSetOptions` exklusiven Zugriff unterstützt, können Sie überschreiben, um diese Fähigkeit zu nutzen.

Weitere Informationen zu Cursorn finden Sie im Artikel [ODBC](../../data/odbc/odbc-basics.md).

## <a name="crecordsetonsetupdateoptions"></a><a name="onsetupdateoptions"></a>CRecordset::OnSetUpdateOptions

Wird aufgerufen, um Optionen (bei Aktualisierung verwendet) für die angegebene ODBC-Anweisung festzulegen.

```
virtual void OnSetUpdateOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parameter

*hstmt*<br/>
Die HSTMT der ODBC-Anweisung, deren Optionen festgelegt werden sollen.

### <a name="remarks"></a>Bemerkungen

Rufen `OnSetUpdateOptions` Sie die Einstellung von Optionen (bei der Aktualisierung) für die angegebene ODBC-Anweisung auf. Das Framework ruft diese Memberfunktion auf, nachdem es ein HSTMT erstellt hat, um Datensätze in einem Recordset zu aktualisieren. (Wird `OnSetOptions` für Auswahlvorgänge `OnSetUpdateOptions` verwendet und wird für Aktualisierungsvorgänge verwendet.) `OnSetUpdateOptions` bestimmt die Unterstützung der Datenquelle für scrollbare Cursor und für Cursorparallelität und legt die Optionen des Recordsets entsprechend fest.

Überschreiben, `OnSetUpdateOptions` um Optionen einer ODBC-Anweisung festzulegen, bevor diese Anweisung für den Zugriff auf eine Datenbank verwendet wird.

Weitere Informationen zu Cursorn finden Sie im Artikel [ODBC](../../data/odbc/odbc-basics.md).

## <a name="crecordsetopen"></a><a name="open"></a>CRecordset::Öffnen

Öffnet das Recordset, indem die Tabelle abgerufen oder die vom Recordset darstellte Abfrage durchgeführt wird.

```
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    DWORD dwOptions = none);
```

### <a name="parameters"></a>Parameter

*nOpenType*<br/>
Akzeptieren Sie den Standardwert, AFX_DB_USE_DEFAULT_TYPE, oder verwenden `enum OpenType`Sie einen der folgenden Werte aus dem:

- `CRecordset::dynaset`Ein Recordset mit bidirektionalem Scrollen. Die Mitgliedschaft und die Reihenfolge der Datensätze werden beim Öffnen des Recordsets bestimmt. Die von anderen Benutzern an den Datenwerten vorgenommenen Änderungen sind nach einem Abrufvorgang allerdings sichtbar. Dynasets sind auch als keysetgesteuerte Recordsets bekannt.

- `CRecordset::snapshot`Ein statisches Recordset mit bidirektionalem Scrollen. Die Mitgliedschaft und die Reihenfolge der Datensätze werden beim Öffnen des Recordsets und die Datenwerte beim Abrufen der Datensätze bestimmt. Die von anderen Benutzern vorgenommenen Änderungen sind nicht sichtbar, bis das Recordset geschlossen und erneut geöffnet wird.

- `CRecordset::dynamic`Ein Recordset mit bidirektionalem Scrollen. Die von anderen Benutzern an der Mitgliedschaft, der Reihenfolge und den Datenwerten vorgenommen Änderungen sind nach einem Abrufvorgang sichtbar. Beachten Sie, dass dieser Recordsettyp von vielen ODBC-Treibern nicht unterstützt wird.

- `CRecordset::forwardOnly`Ein schreibgeschütztes Recordset mit nur vorwärts gerichtetem Scrollen.

   Für `CRecordset`ist `CRecordset::snapshot`der Standardwert . Mithilfe des Standardwertmechanismus kann bei Visual C++-Assistenten mit ODBC-`CRecordset` sowie DAO- `CDaoRecordset`, die über unterschiedliche Standardwerte verfügen, interagiert werden.

Weitere Informationen zu diesen Recordset-Typen finden Sie im Artikel [Recordset (ODBC)](../../data/odbc/recordset-odbc.md). Weitere Informationen finden Sie im Artikel "Verwenden von Block- und Scrollable-Cursors" im Windows SDK.

> [!CAUTION]
> Wenn der angeforderte Typ nicht unterstützt wird, löst das Framework eine Ausnahme aus.

*Lpszsql*<br/>
Eine Zeichenfolge, in der eines der folgenden Elemente enthalten ist:

- Ein NULL-Zeiger.

- Name der Tabelle

- Eine SQL **SELECT-Anweisung** (optional mit einer SQL **WHERE-** oder **ORDER BY-Klausel).**

- Eine **CALL** CALL-Anweisung, die den Namen einer vordefinierten Abfrage (gespeicherte Prozedur) angibt. Achten Sie darauf, dass Sie keine Leerzeichen **CALL** zwischen der geschweiften Klammer und dem Call-Schlüsselwort einfügen.

Weitere Informationen zu dieser Zeichenfolge finden Sie in der Tabelle und in der Erläuterung der Rolle von ClassWizard unter ["Bemerkungen".](#remarks)

> [!NOTE]
> Die Reihenfolge der Spalten in Ihrem Resultset muss mit der Reihenfolge der RFX- oder Bulk-RFX-Funktionsaufrufe in Ihrer [DoFieldExchange-](#dofieldexchange) oder [DoBulkFieldExchange-Funktionsüberschreibung](#dobulkfieldexchange) übereinstimmen.

*Dwoptions*<br/>
Eine Bitmaske, die eine Kombination der unten aufgeführten Werte angeben kann. Einige davon schließen sich einander aus. Der Standardwert ist **none**.

- `CRecordset::none`Es werden keine Optionen festgelegt. Dieser Parameterwert und alle anderen Werte schließen einander aus. Standardmäßig kann das Recordset mit [Bearbeiten](#edit) oder [Löschen](#delete) aktualisiert werden und ermöglicht das Anfügen neuer Datensätze mit [AddNew](#addnew). Die Updatabilität hängt von der Datenquelle sowie von der von Ihnen angegebenen *NOpenType-Option* ab. Optimierung für Massenhinzufügeaktionen ist nicht verfügbar. Das gesammelte Abrufen von Zeilen wird nicht implementiert. Gelöschte Datensätze werden während der Recordsetnavigation nicht übersprungen. Lesezeichen sind nicht verfügbar. Automatische Überprüfung fehlerhafter Felder wird implementiert.

- `CRecordset::appendOnly`Nicht zulassen `Edit` `Delete` oder auf dem Recordset. Lassen Sie nur `AddNew` zu. Diese Option und `CRecordset::readOnly` schließen einander aus.

- `CRecordset::readOnly`Öffnen Sie das Recordset als schreibgeschützt. Diese Option und `CRecordset::appendOnly` schließen einander aus.

- `CRecordset::optimizeBulkAdd`Verwenden Sie eine vorbereitete SQL-Anweisung, um das Hinzufügen vieler Datensätze gleichzeitig zu optimieren. Gilt nur, wenn Sie die ODBC-API-Funktion `SQLSetPos` nicht verwenden, um das Recordset zu aktualisieren. Das erste Update bestimmt die geänderten Felder. Diese Option und `CRecordset::useMultiRowFetch` schließen einander aus.

- `CRecordset::useMultiRowFetch`Implementieren Sie das Abrufen von Massenzeilen, damit mehrere Zeilen in einem einzelnen Abrufvorgang abgerufen werden können. Das ist eine erweiterte Funktion, die zum Verbessern der Leistung entworfen wurde. Allerdings wird der Massenaustausch von Datensatzfeldern von ClassWizard nicht unterstützt. Diese Option und `CRecordset::optimizeBulkAdd` schließen einander aus. Beachten Sie, `CRecordset::useMultiRowFetch`dass, wenn `CRecordset::noDirtyFieldCheck` Sie angeben, die Option automatisch aktiviert wird (doppelte Pufferung ist nicht verfügbar); bei nur Vorwärts-Recordsets `CRecordset::useExtendedFetch` wird die Option automatisch aktiviert. Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

- `CRecordset::skipDeletedRecords`Überspringen Sie alle gelöschten Datensätze, wenn Sie durch das Recordset navigieren. Das verlangsamt in bestimmten relativen Abrufen die Leistung. Diese Option ist bei forward-only-Recordsets ungültig. Wenn Sie [Move](#move) aufrufen, wobei der Parameter `CRecordset::skipDeletedRecords` *nRows* auf 0 festgelegt ist und der Optionssatz festgelegt ist, `Move` wird dies bestätigt. Beachten `CRecordset::skipDeletedRecords` Sie, dass dies dem *Treiberpacken*ähnelt, was bedeutet, dass gelöschte Zeilen aus dem Recordset entfernt werden. Wenn der Treiber allerdings Datensätze verpackt, werden nur die von Ihnen gelöschten Datensätze übersprungen. Die von anderen Benutzern gelöschten Datensätze werden nicht übersprungen, solange das Recordset geöffnet ist. `CRecordset::skipDeletedRecords`überspringt Zeilen, die von anderen Benutzern gelöscht wurden.

- `CRecordset::useBookmarks`Kann Lesezeichen auf dem Recordset verwenden, wenn unterstützt. Lesezeichen verlangsamen den Datenabruf, verbessern aber die Leistung bei der Datennavigation. In forward-only-Recordsets ist das ungültig. Weitere Informationen finden Sie im Artikel [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

- `CRecordset::noDirtyFieldCheck`Deaktivieren Sie die automatische Schmutzfeldprüfung (doppelte Pufferung). Dadurch wird die Leistung verbessert. Sie müssen allerdings Felder manuell als geändert kennzeichnen, indem Sie die Memberfunktionen `SetFieldDirty` und `SetFieldNull` aufrufen. Beachten Sie, dass die doppelte Pufferung in der `CRecordset`-Klasse der doppelten Pufferung in der `CDaoRecordset`-Klasse ähnelt. Bei `CRecordset` können Sie die doppelte Pufferung allerdings nicht für einzelne Felder aktivieren. Sie können sie für alle Felder aktivieren oder deaktivieren. Beachten Sie, dass, `CRecordset::useMultiRowFetch`wenn `CRecordset::noDirtyFieldCheck` Sie die Option angeben, die Option automatisch aktiviert wird. `SetFieldDirty` und `SetFieldNull` kann jedoch nicht für Recordsets verwendet werden, die das Abrufen von Massenzeilen implementieren.

- `CRecordset::executeDirect`Verwenden Sie keine vorbereitete SQL-Anweisung. Um die Leistung zu verbessern, geben Sie diese Option an, wenn die `Requery` Memberfunktion nie aufgerufen wird.

- `CRecordset::useExtendedFetch`Implementieren `SQLExtendedFetch` statt `SQLFetch`. Dies wurde für das Implementieren des gesammelten Abrufens von Zeilen in forward-only-Recordsets entworfen. Wenn Sie die `CRecordset::useMultiRowFetch` Option für ein Nur-Forward-Recordset angeben, wird die `CRecordset::useExtendedFetch` Option automatisch aktiviert.

- `CRecordset::userAllocMultiRowBuffers`Der Benutzer weist Speicherpuffer für die Daten zu. Verwenden Sie diese Option in Verbindung mit `CRecordset::useMultiRowFetch`, wenn Sie Ihren eigenen Speicher zuordnen möchten. Andernfalls ordnet wird der notwendigen Speicher vom Framework automatisch zugeordnet. Weitere Informationen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Beachten Sie, `CRecordset::userAllocMultiRowBuffers` dass `CRecordset::useMultiRowFetch` die Angabe ohne Angabe von angegeben zu einer fehlgeschlagenen Assertion führt.

### <a name="return-value"></a>Rückgabewert

Ein Wert `CRecordset` ungleich Null, wenn das Objekt erfolgreich geöffnet wurde; Andernfalls 0, wenn [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) (falls aufgerufen) 0 zurückgibt.

### <a name="remarks"></a>Bemerkungen

Sie müssen diese Memberfunktion zum Ausführen der vom Recordset definierten Abfrage aufrufen. Vor `Open`dem Aufruf müssen Sie das Recordset-Objekt erstellen.

Die Verbindung dieses Recordsets mit der Datenquelle hängt davon ab, wie Sie das Recordset vor dem Aufruf `Open`erstellen. Wenn Sie ein [CDatabase-Objekt](../../mfc/reference/cdatabase-class.md) an den Recordset-Konstruktor übergeben, der nicht mit der Datenquelle verbunden ist, verwendet diese Memberfunktion [GetDefaultConnect,](#getdefaultconnect) um zu versuchen, das Datenbankobjekt zu öffnen. Wenn Sie NULL an den Recordset-Konstruktor übergeben, erstellt der Konstruktor ein `CDatabase` Objekt für Sie und `Open` versucht, das Datenbankobjekt zu verbinden. Weitere Informationen zum Schließen des Recordsets und der Verbindung unter diesen unterschiedlichen Umständen finden Sie unter [Schließen](#close).

> [!NOTE]
> Der Zugriff auf eine Datenquelle durch ein `CRecordset`-Objekt wird immer freigegeben. Anders als die `CDaoRecordset`-Klasse können Sie kein `CRecordset`-Objekt zum Öffnen einer Datenquelle mit exklusivem Zugriff verwenden.

Wenn Sie `Open`eine Abfrage aufrufen, in der Regel eine SQL **SELECT-Anweisung,** werden Datensätze basierend auf Dener Kriterien ausgewählt, die in der folgenden Tabelle angezeigt werden.

|Der Wert des lpszSQL-Parameters.|Die ausgewählten Datensätze werden von folgenden Aspekten bestimmt:|Beispiel|
|------------------------------------|----------------------------------------|-------------|
|NULL|Die von `GetDefaultSQL` zurückgegebene Zeichenfolge.||
|SQL-Tabellenname|Alle Spalten der Tabellenliste in `DoFieldExchange` oder `DoBulkFieldExchange`.|`"Customer"`|
|Der vordefinierte Name der Abfrage (gespeicherten Prozedur)|Die Spalten, zu denen die Abfrage per Definition zurückgibt.|`"{call OverDueAccts}"`|
|**SELECT-Spaltenliste** **VON** Tabellenliste|Die angegebenen Spalten aus den angegebenen Tabellen.|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|

> [!CAUTION]
> Achten Sie darauf, dass keine zusätzlichen Leerzeichen in der SQL-Zeichenfolge eingefügt werden. Wenn Sie z. B. Leerzeichen zwischen **CALL** der geschweiften Klammer und dem Call-Schlüsselwort einfügen, interpretiert MFC die SQL-Zeichenfolge als Tabellennamen falsch und fügt sie in eine **SELECT-Anweisung** ein, was dazu führt, dass eine Ausnahme ausgelöst wird. Wenn Ihre vordefinierte Abfrage einen Ausgabeparameter verwendet, fügen Sie auch keine Leerzeichen zwischen der geschweiften Klammer und dem Symbol '' ein. Schließlich dürfen Sie leerzeichen vor der geschweiften Klammer nicht in eine **CALL-Anweisung** oder vor dem **SELECT-Schlüsselwort** in einer **SELECT-Anweisung** einfügen.

Das übliche Verfahren ist, `Open`NULL an zu übergeben; Ruft in `Open` diesem Fall [GetDefaultSQL](#getdefaultsql)auf. Wenn Sie eine `CRecordset` abgeleitete `GetDefaultSQL` Klasse verwenden, geben Sie den Tabellennamen an, den Sie in ClassWizard angegeben haben. Sie können stattdessen andere Informationen im `lpszSQL`-Parameter angeben.

Unabhängig davon, `Open` was Sie übergeben, erstellt eine letzte SQL-Zeichenfolge für die Abfrage (die Zeichenfolge kann SQL **WHERE-** und **ORDER BY-Klauseln** an die `lpszSQL` übergebene Zeichenfolge angehängt haben) und führt dann die Abfrage aus. Sie können die konstruierte Zeichenfolge untersuchen, indem Sie [GetSQL](#getsql) nach dem Aufruf aufrufen. `Open` Weitere Informationen dazu, wie das Recordset eine SQL-Anweisung erstellt und Datensätze auswählt, finden Sie im Artikel [Recordset: How Recordsets Select Records (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

Die Felddatenmember der Recordset-Klasse sind an die Spalten der ausgewählten Daten gebunden. Falls Datensätze zurückgegeben werden, wird der erste Datensatz zum aktuellen Datensatz.

Wenn Sie Optionen für das Recordset festlegen möchten, z. B. einen Filter oder eine `Open`Sortierung, geben Sie diese an, nachdem Sie das Recordset-Objekt erstellt haben, aber vor dem Aufruf . Wenn Sie die Datensätze im Recordset aktualisieren möchten, nachdem das Recordset bereits geöffnet ist, rufen Sie [Requery](#requery)auf.

Weitere Informationen, einschließlich zusätzlicher Beispiele, finden Sie in den Artikeln [Recordset (ODBC)](../../data/odbc/recordset-odbc.md), [Recordset: How Recordsets Select Records (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)und [Recordset: Creating and Closing Recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

### <a name="example"></a>Beispiel

Die folgenden Codebeispiele zeigen `Open` verschiedene Formen des Aufrufs.

[!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]

## <a name="crecordsetrefreshrowset"></a><a name="refreshrowset"></a>CRecordset::RefreshRowset

Aktualisiert die Daten und den Status für eine Zeile im aktuellen Rowset.

```cpp
void RefreshRowset(
    WORD wRow,
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>Parameter

*wRow*<br/>
Die one-basierte Position einer Zeile im aktuellen Rowset. Dieser Wert kann von Null bis zur Größe des Rowsets reichen.

*wLockType*<br/>
Ein Wert, der angibt, wie die Zeile gesperrt werden soll, nachdem sie aktualisiert wurde. Einzelheiten finden Sie unter "Hinweise".

### <a name="remarks"></a>Bemerkungen

Wenn Sie den Wert Null für *wRow*übergeben, wird jede Zeile im Rowset aktualisiert.

Um `RefreshRowset`zu verwenden, müssen Sie das Abrufen `CRecordset::useMulitRowFetch` von Massenzeilen implementiert haben, indem Sie die Option in der [Funktion Öffnen](#open) von Membern angeben.

`RefreshRowset`ruft die ODBC-API-Funktion `SQLSetPos`auf. Der *parameter wLockType* gibt den Sperrstatus `SQLSetPos` der Zeile an, nachdem er ausgeführt wurde. In der folgenden Tabelle werden die möglichen Werte für *wLockType*beschrieben.

|wLockType|BESCHREIBUNG|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (der Standardwert)|Der Treiber oder die Datenquelle stellt sicher, dass sich die Zeile `RefreshRowset` im gleichen gesperrten oder entsperrten Zustand befindet, wie sie zuvor aufgerufen wurde.|
|SQL_LOCK_EXCLUSIVE|Der Treiber oder die Datenquelle sperrt die Zeile ausschließlich. Nicht alle Datenquellen unterstützen diese Art von Sperre.|
|SQL_LOCK_UNLOCK|Der Treiber oder die Datenquelle entsperrt die Zeile. Nicht alle Datenquellen unterstützen diese Art von Sperre.|

Weitere Informationen `SQLSetPos`zu finden Sie unter Windows SDK. Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetrequery"></a><a name="requery"></a>CRecordset::Requery

Erstellt ein Recordset neu (aktualisiert).

```
virtual BOOL Requery();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Recordset erfolgreich neu erstellt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Falls Datensätze zurückgegeben werden, wird der erste Datensatz zum aktuellen Datensatz.

Damit das Recordset die Hinzufügungen und Löschungen widerspiegelt, die Sie oder andere Benutzer an `Requery`der Datenquelle vorgenommen haben, müssen Sie das Recordset durch Aufrufen neu erstellen. Wenn es sich bei dem Recordset um ein Dynaset handelt, werden automatisch Aktualisierungen widergespiegelt, die Sie oder andere Benutzer an den vorhandenen Datensätzen (jedoch nicht an Ergänzungen) vornehmen. Wenn es sich bei dem Recordset um einen Snapshot handelt, müssen Sie aufrufen, `Requery` um Bearbeitungen anderer Benutzer sowie Ergänzungen und Löschungen widerzuspiegeln.

Rufen `Requery` Sie für ein Dynaset oder einen Snapshot jederzeit auf, wenn Sie das Recordset mithilfe eines neuen Filters oder einer neuen Sortierung oder neuer Parameterwerte neu erstellen möchten. Legen Sie die neue Filter- oder `m_strFilter` Sortiereigenschaft fest, indem Sie neue Werte für und `m_strSort` vor dem Aufruf zuweisen. `Requery` Legen Sie neue Parameter fest, indem Sie `Requery`parameterdatenmembern neue Werte zuweisen, bevor Sie aufrufen. Wenn die Filter- und Sortierzeichenfolgen unverändert bleiben, können Sie die Abfrage wiederverwenden, was die Leistung verbessert.

Wenn der Versuch, das Recordset neu zu erstellen, fehlschlägt, wird das Recordset geschlossen. Vor dem `Requery`Aufruf können Sie bestimmen, ob das Recordset `CanRestart` erneut abgefragt werden kann, indem Sie die Memberfunktion aufrufen. `CanRestart`garantiert nicht, `Requery` dass dies gelingt.

> [!CAUTION]
> Rufen `Requery` Sie erst an, nachdem Sie [Open](#open)aufgerufen haben.

### <a name="example"></a>Beispiel

In diesem Beispiel wird ein Recordset neu erstellt, um eine andere Sortierreihenfolge anzuwenden.

[!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]

## <a name="crecordsetsetabsoluteposition"></a><a name="setabsoluteposition"></a>CRecordset::SetAbsolutePosition

Positioniert das Recordset auf dem Datensatz entsprechend der angegebenen Datensatznummer.

```cpp
void SetAbsolutePosition(long nRows);
```

### <a name="parameters"></a>Parameter

*nRows*<br/>
Die one-basierte Ordinalposition für den aktuellen Datensatz im Recordset.

### <a name="remarks"></a>Bemerkungen

`SetAbsolutePosition`verschiebt den aktuellen Datensatzzeiger basierend auf dieser Ordinalposition.

> [!NOTE]
> Diese Memberfunktion ist für Forward-Only-Recordsets nicht gültig.

Bei ODBC-Recordsets bezieht sich eine absolute Positionseinstellung von 1 auf den ersten Datensatz im Recordset; eine Einstellung von 0 bezieht sich auf die Position des Anfangs der Datei (BOF).

Sie können auch negative `SetAbsolutePosition`Werte an übergeben. In diesem Fall wird die Position des Recordsets vom Ende des Recordsets aus ausgewertet. `SetAbsolutePosition( -1 )` Verschiebt z. B. den aktuellen Datensatzzeiger auf den letzten Datensatz im Recordset.

> [!NOTE]
> Absolute Position ist nicht als Ersatzdatensatznummer vorgesehen. Lesezeichen sind nach wie vor die empfohlene Methode zum Beibehalten und Zurückkehren an eine bestimmte Position, da sich die Position eines Datensatzes ändert, wenn vorhergehende Datensätze gelöscht werden. Darüber hinaus können Sie nicht sicher sein, dass ein bestimmter Datensatz dieselbe absolute Position hat, wenn das Recordset erneut erstellt wird, da die Reihenfolge der einzelnen Datensätze innerhalb eines Recordsets nur garantiert ist, wenn er mit einer SQL-Anweisung mithilfe einer **ORDER BY-Klausel** erstellt wird.

Weitere Informationen zur Recordset-Navigation und Lesezeichen finden Sie in den Artikeln [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) und [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

## <a name="crecordsetsetbookmark"></a><a name="setbookmark"></a>CRecordset::SetBookmark

Positioniert das Recordset auf dem Datensatz, der das angegebene Lesezeichen enthält.

```cpp
void SetBookmark(const CDBVariant& varBookmark);
```

### <a name="parameters"></a>Parameter

*varBookmark*<br/>
Ein Verweis auf ein [CDBVariant-Objekt,](../../mfc/reference/cdbvariant-class.md) das den Lesezeichenwert für einen bestimmten Datensatz enthält.

### <a name="remarks"></a>Bemerkungen

Um zu ermitteln, ob Lesezeichen auf dem Recordset unterstützt werden, rufen Sie [CanBookmark](#canbookmark)auf. Um Lesezeichen verfügbar zu machen, wenn sie `CRecordset::useBookmarks` unterstützt werden, müssen Sie die Option im Parameter *dwOptions* der [Memberfunktion Öffnen](#open) festlegen.

> [!NOTE]
> Wenn Lesezeichen nicht unterstützt werden `SetBookmark` oder nicht verfügbar sind, führt der Aufruf dazu, dass eine Ausnahme ausgelöst wird. Lesezeichen werden in Vorwärts-Recordsets nicht unterstützt.

Um zuerst die Textmarke für den aktuellen Datensatz abzurufen, rufen Sie `CDBVariant` [GetBookmark](#getbookmark)auf, wodurch der Lesezeichenwert in einem Objekt spart. Später können Sie zu diesem `SetBookmark` Datensatz zurückkehren, indem Sie den gespeicherten Lesezeichenwert aufrufen.

> [!NOTE]
> Nach bestimmten Recordsetvorgängen sollten Sie die Lesezeichenpersistenz überprüfen, bevor Sie aufrufen. `SetBookmark` Wenn Sie z. B. `GetBookmark` ein Lesezeichen `Requery`mit abrufen und dann aufrufen, ist die Textmarke möglicherweise nicht mehr gültig. Rufen Sie [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) auf, `SetBookmark`um zu überprüfen, ob Sie sicher aufrufen können.

Weitere Informationen zur Lesezeichen- und Recordsetnavigation finden Sie in den Artikeln [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) und [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetsetfielddirty"></a><a name="setfielddirty"></a>CRecordset::SetFieldDirty

Kennzeichnet ein Felddatenelement des Recordsets als geändert oder unverändert.

```cpp
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```

### <a name="parameters"></a>Parameter

*Pv*<br/>
Enthält die Adresse eines Felddatenelements im Recordset oder NULL. Wenn NULL, werden alle Felddatenmember im Recordset gekennzeichnet. (C++ NULL ist in der Datenbankterminologie nicht identisch mit Null, was bedeutet, dass "keinen Wert hat").

*bDirty*<br/>
TRUE, wenn das Felddatenelement als "schmutzig" (geändert) gekennzeichnet werden soll. Andernfalls FALSE, wenn das Felddatenelement als "sauber" (unverändert) gekennzeichnet werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn Sie Felder unverändert markieren, wird sichergestellt, dass das Feld nicht aktualisiert wird und weniger SQL-Datenverkehr entsteht.

> [!NOTE]
> Diese Memberfunktion ist nicht für Recordsets anwendbar, die Massenzeilenabrufe verwenden. Wenn Sie das Abrufen von `SetFieldDirty` Massenzeilen implementiert haben, führt dies zu einer fehlgeschlagenen Assertion. Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Das Framework markiert geänderte Felddatenmember, um sicherzustellen, dass sie vom RFX-Mechanismus (Record Field Exchange) in den Datensatz in der Datenquelle geschrieben werden. Wenn Sie den Wert eines Felds ändern, wird das `SetFieldDirty` Feld im Allgemeinen automatisch verschmutzt, sodass Sie sich selten selbst aufrufen müssen, aber Sie möchten manchmal sicherstellen, dass Spalten explizit aktualisiert oder eingefügt werden, unabhängig davon, welcher Wert sich im Felddatenelement befindet.

> [!CAUTION]
> Rufen Sie diese Memberfunktion erst auf, nachdem Sie [Bearbeiten](#edit) oder [AddNew](#addnew)aufgerufen haben.

Wenn Sie NULL für das erste Argument der `outputColumn` Funktion `param` verwenden, wird die Funktion nur auf Felder und nicht auf Felder angewendet. Zum Beispiel wird der Anruf

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

setzt nur `outputColumn` Felder auf NULL; `param` Felder bleiben davon unberührt.

Um an `param` Feldern zu arbeiten, müssen Sie `param` die tatsächliche Adresse der Person angeben, an der Sie arbeiten möchten, z. B.:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

Dies bedeutet, `param` dass Sie nicht alle `outputColumn` Felder auf NULL festlegen können, wie Sie es mit Feldern können.

## <a name="crecordsetsetfieldnull"></a><a name="setfieldnull"></a>CRecordset::SetFieldNull

Kenntiert ein Felddatenelement des Recordsets als Null (insbesondere ohne Wert) oder als Nicht-Null.

```cpp
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parameter

*Pv*<br/>
Enthält die Adresse eines Felddatenelements im Recordset oder NULL. Wenn NULL, werden alle Felddatenmember im Recordset gekennzeichnet. (C++ NULL ist in der Datenbankterminologie nicht identisch mit Null, was bedeutet, dass "keinen Wert hat").

*bNull*<br/>
Ein Wert ungleich Null, wenn das Felddatenelement als mit keinem Wert (Null) gekennzeichnet werden soll. Andernfalls 0, wenn das Felddatenelement als nicht-Null gekennzeichnet werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn Sie einem Recordset einen neuen Datensatz hinzufügen, werden alle Felddatenmember zunächst auf einen Nullwert festgelegt und als "schmutzig" (geändert) gekennzeichnet. Wenn Sie einen Datensatz aus einer Datenquelle abrufen, haben seine Spalten entweder bereits Werte oder sind Null.

> [!NOTE]
> Rufen Sie diese Memberfunktion nicht für Recordsets auf, die Massenzeilenabrufe verwenden. Wenn Sie das Abrufen von `SetFieldNull` Massenzeilen implementiert haben, führt das Aufrufen zu einer fehlgeschlagenen Assertion. Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Wenn Sie ein Feld des aktuellen Datensatzes ausdrücklich als `SetFieldNull` nicht mit einem Wert angeben möchten, rufen Sie den Aufruf mit *bNull* auf TRUE fest, um es als Null zu kennzeichnen. Wenn ein Feld zuvor als Null markiert wurde und Sie ihm nun einen Wert geben möchten, legen Sie einfach seinen neuen Wert fest. Sie müssen das Null-Flag `SetFieldNull`nicht mit entfernen. Um zu bestimmen, ob das Feld `IsFieldNullable`Null sein darf, rufen Sie auf.

> [!CAUTION]
> Rufen Sie diese Memberfunktion erst auf, nachdem Sie [Bearbeiten](#edit) oder [AddNew](#addnew)aufgerufen haben.

Wenn Sie NULL für das erste Argument der `outputColumn` Funktion `param` verwenden, wird die Funktion nur auf Felder und nicht auf Felder angewendet. Zum Beispiel wird der Anruf

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

setzt nur `outputColumn` Felder auf NULL; `param` Felder bleiben davon unberührt.

Um an `param` Feldern zu arbeiten, müssen Sie `param` die tatsächliche Adresse der Person angeben, an der Sie arbeiten möchten, z. B.:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

Dies bedeutet, `param` dass Sie nicht alle `outputColumn` Felder auf NULL festlegen können, wie Sie es mit Feldern können.

> [!NOTE]
> Beim Festlegen von Parametern `SetFieldNull` auf Null führt ein Aufruf vor dem Öffnen des Recordsets zu einer Assertion. Rufen Sie in diesem Fall [SetParamNull](#setparamnull)auf.

`SetFieldNull`wird über [DoFieldExchange](#dofieldexchange)implementiert.

## <a name="crecordsetsetlockingmode"></a><a name="setlockingmode"></a>CRecordset::SetLockingMode

Legt den Sperrmodus auf "optimistische" Sperrung (Standard) oder "pessimistische" Sperre fest. Bestimmt, wie Datensätze für Aktualisierungen gesperrt werden.

```cpp
void SetLockingMode(UINT nMode);
```

### <a name="parameters"></a>Parameter

*nMode*<br/>
Enthält einen der folgenden `enum LockMode`Werte aus der :

- `optimistic`Die optimistische Sperrung sperrt den `Update`Datensatz, der nur während des Aufrufs von aktualisiert wird.

- `pessimistic`Pessimistische sperren den Datensatz, `Edit` sobald er aufgerufen wird, und hält ihn gesperrt, bis der `Update` Anruf abgeschlossen ist oder Sie zu einem neuen Datensatz wechseln.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Memberfunktion auf, wenn Sie angeben müssen, welche von zwei Datensatzsperrstrategien das Recordset für Aktualisierungen verwendet. Standardmäßig ist `optimistic`der Sperrmodus eines Recordsets . Sie können dies in `pessimistic` eine vorsichtigere Sperrstrategie ändern. Rufen `SetLockingMode` Sie auf, nachdem Sie das Recordset-Objekt erstellt und geöffnet haben, aber bevor Sie aufrufen. `Edit`

## <a name="crecordsetsetparamnull"></a><a name="setparamnull"></a>CRecordset::SetParamNull

Flags einen Parameter als Null (speziell ohne Wert) oder als nicht Null.

```cpp
void SetParamNull(
    int nIndex,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der nullbasierte Index des Parameters.

*bNull*<br/>
Wenn TRUE (der Standardwert), wird der Parameter als Null gekennzeichnet. Andernfalls wird der Parameter als nicht Null gekennzeichnet.

### <a name="remarks"></a>Bemerkungen

Im Gegensatz zu [SetFieldNull](#setfieldnull)können Sie aufrufen, `SetParamNull` bevor Sie das Recordset geöffnet haben.

`SetParamNull`wird in der Regel mit vordefinierten Abfragen (gespeicherte Prozeduren) verwendet.

## <a name="crecordsetsetrowsetcursorposition"></a><a name="setrowsetcursorposition"></a>CRecordset::SetRowsetCursorPosition

Verschiebt den Cursor in eine Zeile innerhalb des aktuellen Rowsets.

```cpp
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>Parameter

*wRow*<br/>
Die one-basierte Position einer Zeile im aktuellen Rowset. Dieser Wert kann zwischen 1 und der Größe des Rowsets liegen.

*wLockType*<br/>
Wert, der angibt, wie die Zeile gesperrt werden soll, nachdem sie aktualisiert wurde. Einzelheiten finden Sie unter "Hinweise".

### <a name="remarks"></a>Bemerkungen

Beim Implementieren des Abrufens von Massenzeilen werden Datensätze von Rowsets abgerufen, wobei der erste Datensatz im abgerufenen Rowset der aktuelle Datensatz ist. Um einen weiteren Datensatz innerhalb des Rowsets `SetRowsetCursorPosition`zum aktuellen Datensatz zu machen, rufen Sie an. Sie können z. `SetRowsetCursorPosition` B. mit der [GetFieldValue-Memberfunktion](#getfieldvalue) kombinieren, um die Daten dynamisch aus einem beliebigen Datensatz Ihres Recordsets abzurufen.

Um `SetRowsetCursorPosition`zu verwenden, müssen Sie das Abrufen `CRecordset::useMultiRowFetch` von Massenzeilen implementiert haben, indem Sie die Option des Parameters *dwOptions* in der [Memberfunktion Öffnen](#open) angeben.

`SetRowsetCursorPosition`ruft die ODBC-API-Funktion `SQLSetPos`auf. Der *parameter wLockType* gibt den Sperrstatus `SQLSetPos` der Zeile an, nachdem er ausgeführt wurde. In der folgenden Tabelle werden die möglichen Werte für *wLockType*beschrieben.

|wLockType|BESCHREIBUNG|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (der Standardwert)|Der Treiber oder die Datenquelle stellt sicher, dass sich die Zeile `SetRowsetCursorPosition` im gleichen gesperrten oder entsperrten Zustand befindet, wie sie zuvor aufgerufen wurde.|
|SQL_LOCK_EXCLUSIVE|Der Treiber oder die Datenquelle sperrt die Zeile ausschließlich. Nicht alle Datenquellen unterstützen diese Art von Sperre.|
|SQL_LOCK_UNLOCK|Der Treiber oder die Datenquelle entsperrt die Zeile. Nicht alle Datenquellen unterstützen diese Art von Sperre.|

Weitere Informationen `SQLSetPos`zu finden Sie unter Windows SDK. Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetsetrowsetsize"></a><a name="setrowsetsize"></a>CRecordset::SetRowsetSize

Gibt die Anzahl der Datensätze an, die Sie während eines Abrufs abrufen möchten.

```
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```

### <a name="parameters"></a>Parameter

*dwNewRowsetSize*<br/>
Die Anzahl der Zeilen, die während eines bestimmten Abrufs abgerufen werden sollen.

### <a name="remarks"></a>Bemerkungen

Diese Funktion für virtuelle Member gibt an, wie viele Zeilen Sie während eines einzelnen Abrufs abrufen möchten, wenn Sie das Abrufen von Massenzeilen verwenden. Um das Abrufen von Massenzeilen `CRecordset::useMultiRowFetch` zu implementieren, müssen Sie die Option im *Parameter dwOptions* der [Memberfunktion Öffnen](#open) festlegen.

> [!NOTE]
> Der `SetRowsetSize` Aufruf ohne Massenzeilenabruf führt zu einer fehlgeschlagenen Assertion.

Rufen `SetRowsetSize` Sie `Open` vor dem Aufruf an, um zunächst die Rowsetgröße für das Recordset festzulegen. Die Standardgröße des Rowsets beim Implementieren des Abrufens von Massenzeilen beträgt 25.

> [!NOTE]
> Seien Sie `SetRowsetSize`vorsichtig, wenn Sie anrufen. Wenn Sie den Speicher für die Daten manuell `CRecordset::userAllocMultiRowBuffers` zuweisen (wie durch `Open`die Option des Parameters dwOptions in angegeben), sollten `SetRowsetSize`Sie überprüfen, ob Sie diese Speicherpuffer nach dem Aufruf neu zuordnen müssen, aber bevor Sie einen Cursornavigationsvorgang ausführen.

Um die aktuelle Einstellung für die Rowsetgröße zu erhalten, rufen Sie [GetRowsetSize](#getrowsetsize)auf.

Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetupdate"></a><a name="update"></a>CRecordset::Update

Schließt einen `AddNew` `Edit` oder einen Vorgang ab, indem die neuen oder bearbeiteten Daten in der Datenquelle gespeichert werden.

```
virtual BOOL Update();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn ein Datensatz erfolgreich aktualisiert wurde; andernfalls 0, wenn sich keine Spalten geändert haben. Wenn keine Datensätze aktualisiert wurden oder wenn mehr als ein Datensatz aktualisiert wurde, wird eine Ausnahme ausgelöst. Eine Ausnahme wird auch für alle anderen Fehler in der Datenquelle ausgelöst.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Memberfunktion nach einem Aufruf der [AddNew-](#addnew) oder [Edit-Memberfunktion](#edit) auf. Dieser Aufruf ist erforderlich, `Edit` um den oder den `AddNew` Vorgang abzuschließen.

> [!NOTE]
> Wenn Sie das Abrufen von Massenzeilen `Update`implementiert haben, können Sie nicht aufrufen. Dies führt zu einer fehlgeschlagenen Behauptung. Obwohl `CRecordset` die Klasse keinen Mechanismus zum Aktualisieren von Massendatenzeilen bereitstellt, können Sie `SQLSetPos`ihre eigenen Funktionen mithilfe der ODBC-API-Funktion schreiben. Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Sowohl `AddNew` `Edit` und bereiten Sie einen Bearbeitungspuffer vor, in dem die hinzugefügten oder bearbeiteten Daten zum Speichern in der Datenquelle platziert werden. `Update`speichert die Daten. Nur die Felder, die als geändert markiert oder erkannt wurden, werden aktualisiert.

Wenn die Datenquelle Transaktionen unterstützt, können `Update` Sie den `AddNew` Aufruf `Edit` (und den entsprechenden oder Aufruf) zu einem Teil einer Transaktion machen. Weitere Informationen zu Transaktionen finden Sie im Artikel [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

> [!CAUTION]
> Wenn Sie `Update` aufrufen, `AddNew` ohne `Edit` `Update` vorher `CDBException`eine oder anzurufen, wird eine ausgelöst. Wenn Sie `AddNew` `Edit`oder aufrufen, `Update` müssen Sie `Move` aufrufen, bevor Sie einen Vorgang aufrufen oder bevor Sie entweder das Recordset oder die Datenquellenverbindung schließen. Andernfalls gehen Ihre Änderungen ohne Benachrichtigung verloren.

Weitere Informationen `Update` zur Behandlung von Fehlern finden Sie im Artikel [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

### <a name="example"></a>Beispiel

Siehe den Artikel [Transaktion: Ausführen einer Transaktion in einem Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="see-also"></a>Weitere Informationen

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDatabase-Klasse](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordView-Klasse](../../mfc/reference/crecordview-class.md)
