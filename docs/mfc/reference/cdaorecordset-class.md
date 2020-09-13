---
title: CDaoRecordset-Klasse
ms.date: 08/27/2018
f1_keywords:
- CDaoRecordset
- AFXDAO/CDaoRecordset
- AFXDAO/CDaoRecordset::CDaoRecordset
- AFXDAO/CDaoRecordset::AddNew
- AFXDAO/CDaoRecordset::CanAppend
- AFXDAO/CDaoRecordset::CanBookmark
- AFXDAO/CDaoRecordset::CancelUpdate
- AFXDAO/CDaoRecordset::CanRestart
- AFXDAO/CDaoRecordset::CanScroll
- AFXDAO/CDaoRecordset::CanTransact
- AFXDAO/CDaoRecordset::CanUpdate
- AFXDAO/CDaoRecordset::Close
- AFXDAO/CDaoRecordset::Delete
- AFXDAO/CDaoRecordset::DoFieldExchange
- AFXDAO/CDaoRecordset::Edit
- AFXDAO/CDaoRecordset::FillCache
- AFXDAO/CDaoRecordset::Find
- AFXDAO/CDaoRecordset::FindFirst
- AFXDAO/CDaoRecordset::FindLast
- AFXDAO/CDaoRecordset::FindNext
- AFXDAO/CDaoRecordset::FindPrev
- AFXDAO/CDaoRecordset::GetAbsolutePosition
- AFXDAO/CDaoRecordset::GetBookmark
- AFXDAO/CDaoRecordset::GetCacheSize
- AFXDAO/CDaoRecordset::GetCacheStart
- AFXDAO/CDaoRecordset::GetCurrentIndex
- AFXDAO/CDaoRecordset::GetDateCreated
- AFXDAO/CDaoRecordset::GetDateLastUpdated
- AFXDAO/CDaoRecordset::GetDefaultDBName
- AFXDAO/CDaoRecordset::GetDefaultSQL
- AFXDAO/CDaoRecordset::GetEditMode
- AFXDAO/CDaoRecordset::GetFieldCount
- AFXDAO/CDaoRecordset::GetFieldInfo
- AFXDAO/CDaoRecordset::GetFieldValue
- AFXDAO/CDaoRecordset::GetIndexCount
- AFXDAO/CDaoRecordset::GetIndexInfo
- AFXDAO/CDaoRecordset::GetLastModifiedBookmark
- AFXDAO/CDaoRecordset::GetLockingMode
- AFXDAO/CDaoRecordset::GetName
- AFXDAO/CDaoRecordset::GetParamValue
- AFXDAO/CDaoRecordset::GetPercentPosition
- AFXDAO/CDaoRecordset::GetRecordCount
- AFXDAO/CDaoRecordset::GetSQL
- AFXDAO/CDaoRecordset::GetType
- AFXDAO/CDaoRecordset::GetValidationRule
- AFXDAO/CDaoRecordset::GetValidationText
- AFXDAO/CDaoRecordset::IsBOF
- AFXDAO/CDaoRecordset::IsDeleted
- AFXDAO/CDaoRecordset::IsEOF
- AFXDAO/CDaoRecordset::IsFieldDirty
- AFXDAO/CDaoRecordset::IsFieldNull
- AFXDAO/CDaoRecordset::IsFieldNullable
- AFXDAO/CDaoRecordset::IsOpen
- AFXDAO/CDaoRecordset::Move
- AFXDAO/CDaoRecordset::MoveFirst
- AFXDAO/CDaoRecordset::MoveLast
- AFXDAO/CDaoRecordset::MoveNext
- AFXDAO/CDaoRecordset::MovePrev
- AFXDAO/CDaoRecordset::Open
- AFXDAO/CDaoRecordset::Requery
- AFXDAO/CDaoRecordset::Seek
- AFXDAO/CDaoRecordset::SetAbsolutePosition
- AFXDAO/CDaoRecordset::SetBookmark
- AFXDAO/CDaoRecordset::SetCacheSize
- AFXDAO/CDaoRecordset::SetCacheStart
- AFXDAO/CDaoRecordset::SetCurrentIndex
- AFXDAO/CDaoRecordset::SetFieldDirty
- AFXDAO/CDaoRecordset::SetFieldNull
- AFXDAO/CDaoRecordset::SetFieldValue
- AFXDAO/CDaoRecordset::SetFieldValueNull
- AFXDAO/CDaoRecordset::SetLockingMode
- AFXDAO/CDaoRecordset::SetParamValue
- AFXDAO/CDaoRecordset::SetParamValueNull
- AFXDAO/CDaoRecordset::SetPercentPosition
- AFXDAO/CDaoRecordset::Update
- AFXDAO/CDaoRecordset::m_bCheckCacheForDirtyFields
- AFXDAO/CDaoRecordset::m_nFields
- AFXDAO/CDaoRecordset::m_nParams
- AFXDAO/CDaoRecordset::m_pDAORecordset
- AFXDAO/CDaoRecordset::m_pDatabase
- AFXDAO/CDaoRecordset::m_strFilter
- AFXDAO/CDaoRecordset::m_strSort
helpviewer_keywords:
- CDaoRecordset [MFC], CDaoRecordset
- CDaoRecordset [MFC], AddNew
- CDaoRecordset [MFC], CanAppend
- CDaoRecordset [MFC], CanBookmark
- CDaoRecordset [MFC], CancelUpdate
- CDaoRecordset [MFC], CanRestart
- CDaoRecordset [MFC], CanScroll
- CDaoRecordset [MFC], CanTransact
- CDaoRecordset [MFC], CanUpdate
- CDaoRecordset [MFC], Close
- CDaoRecordset [MFC], Delete
- CDaoRecordset [MFC], DoFieldExchange
- CDaoRecordset [MFC], Edit
- CDaoRecordset [MFC], FillCache
- CDaoRecordset [MFC], Find
- CDaoRecordset [MFC], FindFirst
- CDaoRecordset [MFC], FindLast
- CDaoRecordset [MFC], FindNext
- CDaoRecordset [MFC], FindPrev
- CDaoRecordset [MFC], GetAbsolutePosition
- CDaoRecordset [MFC], GetBookmark
- CDaoRecordset [MFC], GetCacheSize
- CDaoRecordset [MFC], GetCacheStart
- CDaoRecordset [MFC], GetCurrentIndex
- CDaoRecordset [MFC], GetDateCreated
- CDaoRecordset [MFC], GetDateLastUpdated
- CDaoRecordset [MFC], GetDefaultDBName
- CDaoRecordset [MFC], GetDefaultSQL
- CDaoRecordset [MFC], GetEditMode
- CDaoRecordset [MFC], GetFieldCount
- CDaoRecordset [MFC], GetFieldInfo
- CDaoRecordset [MFC], GetFieldValue
- CDaoRecordset [MFC], GetIndexCount
- CDaoRecordset [MFC], GetIndexInfo
- CDaoRecordset [MFC], GetLastModifiedBookmark
- CDaoRecordset [MFC], GetLockingMode
- CDaoRecordset [MFC], GetName
- CDaoRecordset [MFC], GetParamValue
- CDaoRecordset [MFC], GetPercentPosition
- CDaoRecordset [MFC], GetRecordCount
- CDaoRecordset [MFC], GetSQL
- CDaoRecordset [MFC], GetType
- CDaoRecordset [MFC], GetValidationRule
- CDaoRecordset [MFC], GetValidationText
- CDaoRecordset [MFC], IsBOF
- CDaoRecordset [MFC], IsDeleted
- CDaoRecordset [MFC], IsEOF
- CDaoRecordset [MFC], IsFieldDirty
- CDaoRecordset [MFC], IsFieldNull
- CDaoRecordset [MFC], IsFieldNullable
- CDaoRecordset [MFC], IsOpen
- CDaoRecordset [MFC], Move
- CDaoRecordset [MFC], MoveFirst
- CDaoRecordset [MFC], MoveLast
- CDaoRecordset [MFC], MoveNext
- CDaoRecordset [MFC], MovePrev
- CDaoRecordset [MFC], Open
- CDaoRecordset [MFC], Requery
- CDaoRecordset [MFC], Seek
- CDaoRecordset [MFC], SetAbsolutePosition
- CDaoRecordset [MFC], SetBookmark
- CDaoRecordset [MFC], SetCacheSize
- CDaoRecordset [MFC], SetCacheStart
- CDaoRecordset [MFC], SetCurrentIndex
- CDaoRecordset [MFC], SetFieldDirty
- CDaoRecordset [MFC], SetFieldNull
- CDaoRecordset [MFC], SetFieldValue
- CDaoRecordset [MFC], SetFieldValueNull
- CDaoRecordset [MFC], SetLockingMode
- CDaoRecordset [MFC], SetParamValue
- CDaoRecordset [MFC], SetParamValueNull
- CDaoRecordset [MFC], SetPercentPosition
- CDaoRecordset [MFC], Update
- CDaoRecordset [MFC], m_bCheckCacheForDirtyFields
- CDaoRecordset [MFC], m_nFields
- CDaoRecordset [MFC], m_nParams
- CDaoRecordset [MFC], m_pDAORecordset
- CDaoRecordset [MFC], m_pDatabase
- CDaoRecordset [MFC], m_strFilter
- CDaoRecordset [MFC], m_strSort
ms.assetid: 2322067f-1027-4662-a5d7-aa2fc7488630
ms.openlocfilehash: 4a1026c6b652bc5141855670db3b1ee34e7974b9
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040274"
---
# <a name="cdaorecordset-class"></a>CDaoRecordset-Klasse

Stellt eine Gruppe von Datensätzen dar, die aus einer Datenquelle ausgewählt wurden.

## <a name="syntax"></a>Syntax

```cpp
class CDaoRecordset : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoRecordset:: CDaoRecordset](#cdaorecordset)|Erstellt ein `CDaoRecordset`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoRecordset:: AddNew](#addnew)|Bereitet das Hinzufügen eines neuen Datensatzes vor. Aktualisieren Sie die [Aktualisierung](#update) , um die Addition abzuschließen.|
|[CDaoRecordset:: CanAppend](#canappend)|Gibt einen Wert ungleich 0 (null) zurück, wenn dem Recordset mithilfe der [AddNew](#addnew) -Element Funktion neue Datensätze hinzugefügt werden können|
|[CDaoRecordset:: CanBookmark](#canbookmark)|Gibt einen Wert ungleich 0 zurück, wenn das Recordset Lesezeichen unterstützt|
|[CDaoRecordset:: CancelUpdate](#cancelupdate)|Bricht ausstehende Updates aufgrund eines [Edit](#edit) -oder [AddNew](#addnew) -Vorgangs ab.|
|[CDaoRecordset:: canrestart](#canrestart)|Gibt einen Wert ungleich 0 (null) zurück, wenn die [Anforderung](#requery) zum erneuten Ausführen der Abfrage des Recordsets aufgerufen werden kann.|
|[CDaoRecordset:: CanScroll](#canscroll)|Gibt einen Wert ungleich 0 (null) zurück, wenn Sie durch die Datensätze|
|[CDaoRecordset:: CanTransact](#cantransact)|Gibt einen Wert ungleich 0 zurück, wenn die Datenquelle Transaktionen unterstützt.|
|[CDaoRecordset:: CanUpdate](#canupdate)|Gibt einen Wert ungleich 0 (null) zurück, wenn das Recordset aktualisiert werden kann (Sie können Datensätze hinzufügen, aktualisieren oder löschen).|
|[CDaoRecordset:: Close](#close)|Schließt das Recordset.|
|[CDaoRecordset::D Elete](#delete)|Löscht den aktuellen Datensatz aus dem Recordset. Sie müssen nach dem Löschen explizit einen Bildlauf zu einem anderen Datensatz durchführen.|
|[CDaoRecordset::D ofieldexchange](#dofieldexchange)|Wird aufgerufen, um Daten (in beide Richtungen) zwischen den Felddatenmembern des Recordsets und dem entsprechenden Datensatz in der Datenquelle auszutauschen. Implementiert den DAO-Daten Satz Feld Austausch (DFX).|
|[CDaoRecordset:: Edit](#edit)|Bereitet Änderungen am aktuellen Datensatz vor. Ruft `Update` auf, um die Bearbeitung abzuschließen.|
|[CDaoRecordset:: FillCache](#fillcache)|Füllt den gesamten oder einen Teil eines lokalen Caches für ein Recordset-Objekt aus, das Daten aus einer ODBC-Datenquelle enthält.|
|[CDaoRecordset:: Find](#find)|Gibt den ersten, den nächsten, den vorherigen oder den letzten Speicherort einer bestimmten Zeichenfolge in einem "Dynaset-Type"-Recordset an, das die angegebenen Kriterien erfüllt und den Datensatz zum aktuellen Datensatz führt.|
|[CDaoRecordset:: FindFirst](#findfirst)|Gibt den ersten Datensatz in einem Dynaset-Type-oder Snapshot-Type-Recordset an, das die angegebenen Kriterien erfüllt, und legt diesen Datensatz auf den aktuellen Datensatz fest.|
|[CDaoRecordset:: FindLast](#findlast)|Gibt den letzten Datensatz in einem Dynaset-Type-oder Snapshot-Type-Recordset an, das die angegebenen Kriterien erfüllt, und legt diesen Datensatz auf den aktuellen Datensatz fest.|
|[CDaoRecordset:: FindNext](#findnext)|Gibt den nächsten Datensatz in einem Dynaset-Type-oder Snapshot-Type-Recordset an, das die angegebenen Kriterien erfüllt, und legt diesen Datensatz auf den aktuellen Datensatz fest.|
|[CDaoRecordset:: findprev](#findprev)|Gibt den vorherigen Datensatz in einem Dynaset-Type-oder Snapshot-Type-Recordset an, das die angegebenen Kriterien erfüllt, und legt diesen Datensatz auf den aktuellen Datensatz fest.|
|[CDaoRecordset:: GetAbsolutePosition](#getabsoluteposition)|Gibt die Datensatznummer des aktuellen Datensatzes eines Recordset-Objekts zurück.|
|[CDaoRecordset:: GetBookmark](#getbookmark)|Gibt einen Wert zurück, der das Lesezeichen für einen Datensatz darstellt.|
|[CDaoRecordset:: getCacheSize](#getcachesize)|Gibt einen Wert zurück, der die Anzahl der Datensätze in einem Dynaset-Recordset mit Daten angibt, die lokal aus einer ODBC-Datenquelle zwischengespeichert werden sollen.|
|[CDaoRecordset:: getcachestart](#getcachestart)|Gibt einen Wert zurück, der das Lesezeichen des ersten Datensatzes im Recordset angibt, das zwischengespeichert werden soll.|
|[CDaoRecordset:: getcurrentindex](#getcurrentindex)|Gibt einen-Wert zurück, der `CString` den Namen des Indexes enthält, der zuletzt für einen indizierten Tabellen Datentyp verwendet wurde `CDaoRecordset` .|
|[CDaoRecordset:: getdatecreated](#getdatecreated)|Gibt das Datum und die Uhrzeit der Erstellung der Basistabelle zurück, die dem Objekt zugrunde liegt. `CDaoRecordset`|
|[CDaoRecordset:: getdatelastupveraltet](#getdatelastupdated)|Gibt das Datum und die Uhrzeit der letzten Änderung an dem Entwurf einer Basistabelle zurück, die einem- `CDaoRecordset` Objekt zugrunde liegt.|
|[CDaoRecordset:: getdefaultdbname](#getdefaultdbname)|Gibt den Namen der Standarddaten Quelle zurück.|
|[CDaoRecordset:: getdefaulzql](#getdefaultsql)|Wird aufgerufen, um die auszuführende SQL-Standard Zeichenfolge zu erhalten|
|[CDaoRecordset:: geteditmode](#geteditmode)|Gibt einen Wert zurück, der den Bearbeitungsstatus für den aktuellen Datensatz angibt.|
|[CDaoRecordset:: GetFieldCount](#getfieldcount)|Gibt einen Wert zurück, der die Anzahl der Felder in einem Recordset darstellt.|
|[CDaoRecordset:: getfieldinfo](#getfieldinfo)|Gibt bestimmte Arten von Informationen zu den Feldern im Recordset zurück.|
|[CDaoRecordset:: GetFieldValue](#getfieldvalue)|Gibt den Wert eines Felds in einem Recordset zurück.|
|[CDaoRecordset:: GetIndexCount](#getindexcount)|Ruft die Anzahl der Indizes in einer Tabelle ab, die einem Recordset zugrunde liegt.|
|[CDaoRecordset:: getIndexInfo](#getindexinfo)|Gibt verschiedene Arten von Informationen zu einem Index zurück.|
|[CDaoRecordset:: getlastmodifiedbookmark](#getlastmodifiedbookmark)|Wird verwendet, um den zuletzt hinzugefügten oder aktualisierten Datensatz zu ermitteln.|
|[CDaoRecordset:: getlockingmode](#getlockingmode)|Gibt einen Wert zurück, der den Typ der Sperre angibt, die während der Bearbeitung wirksam ist.|
|[CDaoRecordset:: GetName](#getname)|Gibt einen-Wert zurück, der `CString` den Namen des Recordsets enthält.|
|[CDaoRecordset:: GetParamValue](#getparamvalue)|Ruft den aktuellen Wert des angegebenen Parameters ab, der im zugrunde liegenden daoparameter-Objekt gespeichert ist.|
|[CDaoRecordset:: getprozentuposition](#getpercentposition)|Gibt die Position des aktuellen Datensatzes als Prozentsatz der Gesamtanzahl von Datensätzen zurück.|
|[CDaoRecordset:: GetRecordCount](#getrecordcount)|Gibt die Anzahl der Datensätze zurück, auf die in einem Recordsetobjekt zugegriffen wird.|
|[CDaoRecordset:: gezql](#getsql)|Ruft die SQL-Zeichenfolge ab, mit der Datensätze für das Recordset ausgewählt werden.|
|[CDaoRecordset:: GetType](#gettype)|Wird aufgerufen, um den Typ eines Recordsets zu bestimmen: Table-Type, Dynaset-Type oder Snapshot-Type.|
|[CDaoRecordset:: getvalidationrule](#getvalidationrule)|Gibt einen- `CString` Wert zurück, der den Wert enthält, der Daten überprüft, wenn Sie in ein Feld eingegeben werden.|
|[CDaoRecordset:: getvalidationtext](#getvalidationtext)|Ruft den Text ab, der angezeigt wird, wenn eine Validierungs Regel nicht erfüllt wird.|
|[CDaoRecordset:: IsBOF](#isbof)|Gibt einen Wert ungleich 0 (null) zurück, wenn das Recordset vor dem ersten Datensatz positioniert wurde. Es ist kein aktueller Datensatz vorhanden.|
|[CDaoRecordset:: isDeleted](#isdeleted)|Gibt einen Wert ungleich 0 (null) zurück, wenn das Recordset auf einem gelöschten Datensatz positioniert|
|[CDaoRecordset:: IsEOF](#iseof)|Gibt einen Wert ungleich 0 (null) zurück, wenn das Recordset nach dem letzten Datensatz positioniert wurde. Es ist kein aktueller Datensatz vorhanden.|
|[CDaoRecordset:: IsFieldDirty](#isfielddirty)|Gibt einen Wert ungleich 0 (null) zurück, wenn das angegebene Feld im aktuellen Datensatz geändert wurde.|
|[CDaoRecordset:: IsFieldNull](#isfieldnull)|Gibt einen Wert ungleich 0 (null) zurück, wenn das angegebene Feld im aktuellen Datensatz NULL (ohne Wert) ist.|
|[CDaoRecordset:: IsFieldNullable](#isfieldnullable)|Gibt einen Wert ungleich 0 (null) zurück, wenn das angegebene Feld im aktuellen Datensatz auf NULL (ohne Wert) festgelegt werden kann.|
|[CDaoRecordset:: IsOpen](#isopen)|Gibt einen Wert ungleich 0 (null) zurück, wenn [Open](#open) zuvor aufgerufen wurde|
|[CDaoRecordset:: Move](#move)|Positioniert das Recordset auf eine angegebene Anzahl von Datensätzen aus dem aktuellen Datensatz in beide Richtungen.|
|[CDaoRecordset:: vfirst](#movefirst)|Positioniert den aktuellen Datensatz auf dem ersten Datensatz im Recordset.|
|[CDaoRecordset:: muvelast](#movelast)|Positioniert den aktuellen Datensatz auf dem letzten Datensatz im Recordset.|
|[CDaoRecordset:: wvenext](#movenext)|Positioniert den aktuellen Datensatz auf dem nächsten Datensatz im Recordset.|
|[CDaoRecordset:: weprev](#moveprev)|Positioniert den aktuellen Datensatz auf dem vorherigen Datensatz im Recordset.|
|[CDaoRecordset:: Open](#open)|Erstellt ein neues Recordset aus einer Tabelle, einem Dynaset oder einer Momentaufnahme.|
|[CDaoRecordset:: Requery](#requery)|Führt die Abfrage des Recordsets erneut aus, um die ausgewählten Datensätze zu aktualisieren.|
|[CDaoRecordset:: Seek](#seek)|Sucht den Datensatz in einem indizierten Tabellentyp-Recordset-Objekt, das die angegebenen Kriterien für den aktuellen Index erfüllt und den Datensatz zum aktuellen Datensatz führt.|
|[CDaoRecordset:: SetAbsolutePosition](#setabsoluteposition)|Legt die Datensatznummer des aktuellen Datensatzes eines Recordset-Objekts fest.|
|[CDaoRecordset:: SetBookmark](#setbookmark)|Positioniert das Recordset in einem Datensatz, der das angegebene Lesezeichen enthält.|
|[CDaoRecordset:: setCacheSize](#setcachesize)|Legt einen Wert fest, der die Anzahl der Datensätze in einem Dynaset-Recordset mit Daten angibt, die lokal aus einer ODBC-Datenquelle zwischengespeichert werden sollen.|
|[CDaoRecordset:: SetCacheStart](#setcachestart)|Legt einen Wert fest, der das Lesezeichen des ersten Datensatzes im Recordset angibt, das zwischengespeichert werden soll.|
|[CDaoRecordset:: SetCurrentIndex](#setcurrentindex)|Wird aufgerufen, um einen Index für ein Recordset vom Typ "Table" festzulegen.|
|[CDaoRecordset:: SetFieldDirty](#setfielddirty)|Markiert das angegebene Feld im aktuellen Datensatz als geändert.|
|[CDaoRecordset:: SetFieldNull](#setfieldnull)|Legt den Wert des angegebenen Felds im aktuellen Datensatz auf NULL fest (ohne Wert).|
|[CDaoRecordset:: SetFieldValue](#setfieldvalue)|Legt den Wert eines Felds in einem Recordset fest.|
|[CDaoRecordset:: setfieldvaluenull](#setfieldvaluenull)|Legt den Wert eines Felds in einem Recordset auf NULL fest. (kein Wert).|
|[CDaoRecordset:: SetLockingMode](#setlockingmode)|Legt einen Wert fest, der den Typ der Sperre angibt, die während der Bearbeitung wirksam werden soll.|
|[CDaoRecordset:: SetParamValue](#setparamvalue)|Legt den aktuellen Wert des angegebenen Parameters fest, der im zugrunde liegenden daoparameter-Objekt gespeichert ist.|
|[CDaoRecordset:: setparamvaluenull](#setparamvaluenull)|Legt den aktuellen Wert des angegebenen Parameters auf NULL (ohne Wert) fest.|
|[CDaoRecordset:: setprozentuposition](#setpercentposition)|Legt die Position des aktuellen Datensatzes auf einen Speicherort fest, der einem Prozentsatz der Gesamtanzahl von Datensätzen in einem Recordset entspricht.|
|[CDaoRecordset:: Update](#update)|Schließt einen- `AddNew` Vorgang oder-Vorgang ab, `Edit` indem die neuen oder bearbeiteten Daten in der Datenquelle gespeichert werden.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoRecordset:: m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)|Enthält ein Flag, das angibt, ob Felder automatisch als geändert markiert werden.|
|[CDaoRecordset:: m_nFields](#m_nfields)|Enthält die Anzahl der Felddatenmember in der Recordset-Klasse und die Anzahl der Spalten, die vom Recordset aus der Datenquelle ausgewählt werden.|
|[CDaoRecordset:: m_nParams](#m_nparams)|Enthält die Anzahl der Parameterdatenmember in der Recordset-Klasse – die Anzahl von Parametern, die mit der Abfrage des Recordsets übergeben werden.|
|[CDaoRecordset:: m_pDAORecordset](#m_pdaorecordset)|Ein Zeiger auf die DAO-Schnittstelle, die dem Recordset-Objekt zugrunde liegt.|
|[CDaoRecordset:: m_pDatabase](#m_pdatabase)|Die Quelldatenbank für dieses Resultset. Enthält einen Zeiger auf ein [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) -Objekt.|
|[CDaoRecordset:: m_strFilter](#m_strfilter)|Enthält eine Zeichenfolge, mit der eine SQL- **Where** -Anweisung erstellt wird.|
|[CDaoRecordset:: m_strSort](#m_strsort)|Enthält eine Zeichenfolge, die zum Erstellen einer SQL **Order by** -Anweisung verwendet wird.|

## <a name="remarks"></a>Bemerkungen

Objekte, die als "Recordsets" bezeichnet `CDaoRecordset` werden, sind in den folgenden drei Formen verfügbar:

- Tabellentyp-Recordsets stellen eine Basistabelle dar, die Sie verwenden können, um Datensätze aus einer einzelnen Datenbanktabelle zu überprüfen, hinzuzufügen, zu ändern oder zu löschen.

- Dynaset-Recordsets sind das Ergebnis einer Abfrage, die aktualisierbare Datensätze aufweisen kann. Diese Recordsets sind ein Satz von Datensätzen, mit denen Sie Datensätze aus einer zugrunde liegenden Datenbanktabelle oder Tabellen überprüfen, hinzufügen, ändern oder löschen können. Dynaset-Type Recordsets können Felder aus einer oder mehreren Tabellen in einer Datenbank enthalten.

- Momentaufnahme-Recordsets sind eine statische Kopie eines Satzes von Datensätzen, die Sie verwenden können, um Daten zu suchen oder Berichte zu generieren. Diese Recordsets können Felder aus einer oder mehreren Tabellen in einer Datenbank enthalten, können jedoch nicht aktualisiert werden.

Jede Form eines Recordsets stellt einen Satz von Datensätzen dar, die zum Zeitpunkt des Öffnens des Recordsets festgelegt wurden. Wenn Sie einen Bildlauf zu einem Datensatz in einem Tabellentyp-Recordset oder einem Recordset vom Typ "Dynaset" durchführen, werden Änderungen am Datensatz nach dem Öffnen des Recordsets angezeigt. Dies erfolgt entweder von anderen Benutzern oder anderen Recordsets in der Anwendung. (Ein Recordset vom Typ "Snapshot" kann nicht aktualisiert werden.) Sie können `CDaoRecordset` eine anwendungsspezifische Recordsetklasse direkt von verwenden oder diese ableiten `CDaoRecordset` . Sie können anschließend folgende Aktionen durchführen:

- Scrollen Sie durch die Datensätze.

- Legen Sie einen Index fest, und suchen Sie schnell nach Datensätzen mithilfe von [Suchen](#seek) (nur Tabellentyp-Recordsets).

- Suchen Sie Datensätze basierend auf einem Zeichen folgen Vergleich: "<", " \<=", "=", "> =" oder ">" (Dynaset-Type und Snapshot-Type Recordsets).

- Aktualisieren Sie die Datensätze, und geben Sie einen Sperrmodus an (außer Recordsets für Snapshot-Typen).

- Filtern Sie das Recordset, um einzuschränken, welche Datensätze aus den in der Datenquelle verfügbaren Datensätzen ausgewählt werden.

- Sortieren Sie das Recordset.

- Parametrisieren Sie das Recordset, um seine Auswahl mit Informationen anzupassen, die bis zur Laufzeit nicht bekannt sind.

Die-Klasse stellt `CDaoRecordset` eine Schnittstelle bereit, die der-Klasse ähnelt `CRecordset` . Der Hauptunterschied besteht darin, dass die Klasse `CDaoRecordset` auf die Daten über ein Datenzugriffs Objekt (DAO) auf der Grundlage von OLE zugreift. `CRecordset`Die Klasse greift über Open Database Connectivity (ODBC) und einen ODBC-Treiber für dieses DBMS auf das DBMS zu.

> [!NOTE]
> Die DAO-Datenbankklassen unterscheiden sich von den MFC-Datenbankklassen, die auf Open Database Connectivity (ODBC) basieren. Alle DAO-Datenbankklassen Namen haben das Präfix "CDAO". Sie können weiterhin mit den DAO-Klassen auf ODBC-Datenquellen zugreifen. die DAO-Klassen bieten im allgemeinen überlegene Funktionen, da Sie für die Microsoft Jet-Datenbank-Engine spezifisch sind.

Sie können entweder `CDaoRecordset` direkt verwenden oder eine Klasse von ableiten `CDaoRecordset` . Wenn Sie in jedem Fall eine Recordset-Klasse verwenden möchten, öffnen Sie eine Datenbank, und erstellen Sie ein Recordset-Objekt, indem Sie dem Konstruktor einen Zeiger auf das `CDaoDatabase` Objekt übergeben. Sie können auch ein `CDaoRecordset` -Objekt erstellen und es MFC ermöglichen, ein temporäres `CDaoDatabase` Objekt für Sie zu erstellen. Anschließend können Sie die [Open](#open) -Member-Funktion des Recordsets aufzurufen, indem Sie angeben, ob es sich bei dem Objekt um einen Tabellentyp Recordset, einen Dynaset-Typ-Recordset oder ein Recordset vom Typ Snapshot handelt. Durch den Aufruf `Open` von werden Daten aus der Datenbank ausgewählt und der erste Datensatz abgerufen.

Verwenden Sie die Element Funktionen und Datenmember des Objekts, um einen Bildlauf durch die Datensätze durchführen und darauf zu arbeiten. Welche Vorgänge verfügbar sind, hängt davon ab, ob es sich bei dem Objekt um einen Tabellentyp-Recordset, einen "Dynaset-Type"-Recordset oder ein Recordset vom Typ "Snapshot" handelt und ob es aktualisierbar oder schreibgeschützt ist – dies hängt von der Funktion der Datenbank oder Open Database Connectivity (ODBC)-Datenquelle ab. Um Datensätze zu aktualisieren, die seit dem-Befehl geändert oder hinzugefügt wurden, müssen Sie `Open` die [Requery](#requery) -Member-Funktion des Objekts aufzurufen. Nennen Sie die Member-Funktion des-Objekts, `Close` und zerstören Sie das-Objekt, wenn Sie damit fertig sind.

`CDaoRecordset` verwendet den DAO-Daten Satz Feld Austausch (DFX), um das Lesen und Aktualisieren von Daten Satz Feldern über typsichere C++-Member der von `CDaoRecordset` oder `CDaoRecordset` abgeleiteten Klasse zu unterstützen. Sie können auch die dynamische Bindung von Spalten in einer Datenbank implementieren, ohne den DFX-Mechanismus mithilfe von [GetFieldValue](#getfieldvalue) und [SetFieldValue](#setfieldvalue)zu verwenden.

Weitere Informationen finden Sie im Thema "Recordset-Objekt" in der DAO-Hilfe.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CDaoRecordset`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdao.h

## <a name="cdaorecordsetaddnew"></a><a name="addnew"></a> CDaoRecordset:: AddNew

Mit dieser Member-Funktion können Sie einen neuen Datensatz einem Recordset vom Typ "Table-Type" oder "Dynaset" hinzufügen.

```cpp
virtual void AddNew();
```

### <a name="remarks"></a>Bemerkungen

Die Felder des Datensatzes sind anfänglich NULL. (In der Daten Bank Terminologie bedeutet NULL, dass kein Wert vorhanden ist, und ist nicht mit NULL in C++ identisch.) Um den Vorgang abzuschließen, müssen Sie die [Update](#update) Member-Funktion aufzurufen. `Update` speichert die Änderungen an der Datenquelle.

> [!CAUTION]
> Wenn Sie einen Datensatz bearbeiten und dann einen Bildlauf zu einem anderen Datensatz ohne aufrufen durchführen `Update` , gehen Ihre Änderungen ohne Warnung verloren.

Wenn Sie einem Recordset vom Typ Dynaset einen Datensatz hinzufügen, indem Sie [AddNew](#addnew)aufrufen, ist der Datensatz im Recordset sichtbar und in der zugrunde liegenden Tabelle enthalten, wo er für alle neuen Objekte sichtbar wird `CDaoRecordset` .

Die Position des neuen Datensatzes hängt vom Typ des Recordsets ab:

- In einem Dynaset-Typ-Recordset, bei dem der neue Datensatz eingefügt wird, ist nicht garantiert. Dieses Verhalten wurde mit Microsoft Jet 3,0 aus Gründen der Leistung und Parallelität geändert. Wenn Sie den neu hinzugefügten Datensatz zum aktuellen Datensatz machen möchten, können Sie das Lesezeichen des zuletzt geänderten Datensatzes erhalten und zu diesem Lesezeichen wechseln:

[!code-cpp[NVC_MFCDatabase#1](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]

- In einem Recordset vom Typ "Table", für das ein Index angegeben wurde, werden die Datensätze an ihrer richtigen Stelle in der Sortierreihenfolge zurückgegeben. Wenn kein Index angegeben wurde, werden am Ende des Recordsets neue Datensätze zurückgegeben.

Der Datensatz, der vor der Verwendung aktuell war, `AddNew` bleibt aktuell. Wenn Sie den neuen Datensatz aktuell machen möchten und das Recordset Lesezeichen unterstützt, können Sie [SetBookmark](#setbookmark) für das Lesezeichen aufrufen, das durch die LastModified-Eigenschafts Einstellung des zugrunde liegenden DAO-Recordset-Objekts identifiziert wird. Dies ist hilfreich, um den Wert für die Felder "Counter" (automatische Inkrement) in einem hinzugefügten Datensatz zu ermitteln. Weitere Informationen finden Sie unter [getlastmodifiedbookmark](#getlastmodifiedbookmark).

Wenn die Datenbank Transaktionen unterstützt, können Sie den `AddNew` anzurufenden Teil einer Transaktion ausführen. Weitere Informationen zu Transaktionen finden Sie Unterklasse [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md). Beachten Sie, dass Sie [CDaoWorkspace:: BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans) aufrufen sollten, bevor Sie aufrufen `AddNew` .

Es ist unzulässig, `AddNew` für ein Recordset aufzurufen, dessen [Open](#open) Member-Funktion nicht aufgerufen wurde. Eine `CDaoException` wird ausgelöst, wenn Sie `AddNew` für ein Recordset aufzurufen, das nicht angefügt werden kann. Sie können ermitteln, ob das Recordset aktualisierbar ist, indem Sie " [CanAppend](#canappend)" aufrufen.

Das Framework markiert geänderte Felddatenmember, um sicherzustellen, dass Sie durch den DAO-Daten Satz Feld Austausch-Mechanismus (DFX) in den Datensatz der Datenquelle geschrieben werden. Wenn Sie den Wert eines Felds ändern, wird das Feld in der Regel automatisch geändert, sodass Sie nur selten [SetFieldDirty](#setfielddirty) aufrufen müssen. manchmal möchten Sie jedoch sicherstellen, dass die Spalten explizit aktualisiert oder eingefügt werden, unabhängig davon, welcher Wert im Feld Datenmember ist. Der DFX-Mechanismus nutzt auch die Verwendung von **Pseudo-NULL**. Weitere Informationen finden Sie unter [CDaoFieldExchange:: m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Wenn der Mechanismus für die doppelte Pufferung nicht verwendet wird, wird das Feld nicht automatisch als geändert festgelegt, wenn der Wert des Felds geändert wird. In diesem Fall muss das Feld explizit festgelegt werden. Das Flag in [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) steuert diese automatische Feld Überprüfung.

> [!NOTE]
> Wenn Datensätze doppelt gepuffert werden (d. h., die automatische Feld Überprüfung ist aktiviert), `CancelUpdate` werden durch das Aufrufen von die Element Variablen in den Werten wieder hergestellt, die Sie vor `AddNew` oder aufgerufen haben `Edit` .

Weitere Informationen finden Sie in den Themen "AddNew-Methode", "CancelUpdate-Methode", "LastModified-Eigenschaft" und "EditMode-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetcanappend"></a><a name="canappend"></a> CDaoRecordset:: CanAppend

Rufen Sie diese Member-Funktion auf, um zu bestimmen, ob das zuvor geöffnete Recordset es Ihnen ermöglicht, neue Datensätze hinzuzufügen, indem Sie die [AddNew](#addnew) -Member

```cpp
BOOL CanAppend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0, wenn das Recordset das Hinzufügen neuer Datensätze zulässt andernfalls 0. `CanAppend` gibt 0 zurück, wenn Sie das Recordset als schreibgeschützt geöffnet haben.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im Thema "Append Method" in der DAO-Hilfe.

## <a name="cdaorecordsetcanbookmark"></a><a name="canbookmark"></a> CDaoRecordset:: CanBookmark

Mit dieser Member-Funktion können Sie ermitteln, ob mit dem zuvor geöffneten Recordset Datensätze einzeln mithilfe von Lesezeichen markiert werden können.

```cpp
BOOL CanBookmark();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Recordset Lesezeichen unterstützt, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn Sie Recordsets verwenden, die vollständig auf den Tabellen der Microsoft Jet-Datenbank-Engine basieren, können Lesezeichen verwendet werden, mit Ausnahme von Recordsets, die als vorwärts Bildlauf-Recordsets gekennzeichnet sind. Andere Daten Bankprodukte (externe ODBC-Datenquellen) unterstützen möglicherweise keine Lesezeichen.

Weitere Informationen finden Sie im Thema "Bookmarkable-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetcancelupdate"></a><a name="cancelupdate"></a> CDaoRecordset:: CancelUpdate

Die `CancelUpdate` Member-Funktion bricht alle ausstehenden Updates aufgrund eines [Edit](#edit) -oder [AddNew](#addnew) -Vorgangs ab.

```cpp
virtual void CancelUpdate();
```

### <a name="remarks"></a>Bemerkungen

Wenn eine Anwendung z. b. die `Edit` `AddNew` -oder-Member-Funktion aufruft und nicht [Update](#update)aufgerufen hat, `CancelUpdate` bricht alle Änderungen ab, die nach dem Aufruf von vorgenommen wurden `Edit` `AddNew` .

> [!NOTE]
> Wenn Datensätze doppelt gepuffert werden (d. h., die automatische Feld Überprüfung ist aktiviert), `CancelUpdate` werden durch das Aufrufen von die Element Variablen in den Werten wieder hergestellt, die Sie vor `AddNew` oder aufgerufen haben `Edit` .

Wenn kein- `Edit` Vorgang oder-Vorgang aussteht `AddNew` , löst `CancelUpdate` MFC eine Ausnahme aus. Ruft die [geteditmode](#geteditmode) -Member-Funktion auf, um zu bestimmen, ob ein ausstehender Vorgang abgebrochen werden kann.

Weitere Informationen finden Sie im Thema "CancelUpdate Method" in der DAO-Hilfe.

## <a name="cdaorecordsetcanrestart"></a><a name="canrestart"></a> CDaoRecordset:: canrestart

Rufen Sie diese Member-Funktion auf, um zu bestimmen, ob das Recordset das Neustarten der Abfrage (zum Aktualisieren der zugehörigen Datensätze) durch Aufrufen der-Element `Requery` Funktion zulässt

```cpp
BOOL CanRestart();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich NULL `Requery` , wenn aufgerufen werden kann, um die Abfrage des Recordsets erneut auszuführen, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Tabellentyp-Recordsets unterstützen nicht `Requery` .

Wenn `Requery` nicht unterstützt wird, [Schließen Sie Close](#close) und dann [Open](#open) , um die Daten zu aktualisieren. Sie können aufrufen `Requery` , um die zugrunde liegende Parameterabfrage eines Recordset-Objekts zu aktualisieren, nachdem die Parameterwerte geändert wurden.

Weitere Informationen finden Sie im Thema "neu startbare Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetcanscroll"></a><a name="canscroll"></a> CDaoRecordset:: CanScroll

Mit dieser Member-Funktion können Sie feststellen, ob das Recordset einen Bildlauf zulässt.

```cpp
BOOL CanScroll() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn Sie durch die Datensätze scrollen können, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn Sie [Öffnen](#open) mit aufzurufen `dbForwardOnly` , kann das Recordset nur vorwärts scrollen.

Weitere Informationen finden Sie im Thema "Positionieren des aktuellen Daten Satz Zeigers mit DAO" in der DAO-Hilfe.

## <a name="cdaorecordsetcantransact"></a><a name="cantransact"></a> CDaoRecordset:: CanTransact

Mit dieser Member-Funktion können Sie ermitteln, ob das Recordset Transaktionen zulässt.

```cpp
BOOL CanTransact();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die zugrunde liegende Datenquelle Transaktionen unterstützt, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im Thema "Transaktions Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetcanupdate"></a><a name="canupdate"></a> CDaoRecordset:: CanUpdate

Mit dieser Member-Funktion können Sie ermitteln, ob das Recordset aktualisiert werden kann.

```cpp
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn das Recordset aktualisiert werden kann (hinzufügen, aktualisieren und Löschen von Datensätzen), andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Ein Recordset ist möglicherweise schreibgeschützt, wenn die zugrunde liegende Datenquelle schreibgeschützt ist, oder wenn Sie `dbReadOnly` für *noptions* angegeben haben, als Sie [Öffnen](#open) für das Recordset aufgerufen haben.

Weitere Informationen finden Sie in den Themen "AddNew Method", "Edit Method", "Delete Method", "Update Method" und "Updatable Property" in der DAO-Hilfe.

## <a name="cdaorecordsetcdaorecordset"></a><a name="cdaorecordset"></a> CDaoRecordset:: CDaoRecordset

Erstellt ein `CDaoRecordset`-Objekt.

```cpp
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>Parameter

*pdatabase*<br/>
Enthält einen Zeiger auf ein [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) -Objekt oder den Wert NULL. Wenn not NULL und die `CDaoDatabase` Member- `Open` Funktion des Objekts nicht aufgerufen wurde, um Sie mit der Datenquelle zu verbinden, versucht das Recordset, es während des eigenen [öffnenden](#open) Aufrufs für Sie zu öffnen. Wenn NULL übergeben wird, `CDaoDatabase` wird ein-Objekt erstellt und mit den Datenquellen Informationen verbunden, die Sie angegeben haben, wenn Sie Ihre Recordset-Klasse von abgeleitet haben `CDaoRecordset` .

### <a name="remarks"></a>Bemerkungen

Sie können entweder `CDaoRecordset` direkt verwenden oder eine anwendungsspezifische Klasse von ableiten `CDaoRecordset` . Sie können den Klassen-Assistenten verwenden, um die recordsetklassen abzuleiten.

> [!NOTE]
> Wenn Sie eine `CDaoRecordset` Klasse ableiten, muss die abgeleitete Klasse einen eigenen Konstruktor bereitstellen. Nennen Sie den Konstruktor im Konstruktor ihrer abgeleiteten Klasse `CDaoRecordset::CDaoRecordset` , indem Sie die entsprechenden Parameter an den Konstruktor übergeben.

Übergeben Sie NULL an den recordsetkonstruktor, `CDaoDatabase` damit ein-Objekt automatisch erstellt und verbunden wird. Dies ist eine nützliche Verknüpfung, die nicht erfordert, dass Sie ein-Objekt erstellen und verbinden, bevor Sie das `CDaoDatabase` Recordset erstellen. Wenn das `CDaoDatabase` Objekt nicht geöffnet ist, wird auch ein [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) -Objekt für Sie erstellt, das den Standard Arbeitsbereich verwendet. Weitere Informationen finden Sie unter [CDaoDatabase:: CDaoDatabase](../../mfc/reference/cdaodatabase-class.md#cdaodatabase).

## <a name="cdaorecordsetclose"></a><a name="close"></a> CDaoRecordset:: Close

Durch das Schließen eines-Objekts wird dieses `CDaoRecordset` aus der Auflistung offener Recordsets in der zugeordneten Datenbank entfernt.

```cpp
virtual void Close();
```

### <a name="remarks"></a>Bemerkungen

Da `Close` das-Objekt nicht zerstört `CDaoRecordset` , können Sie das-Objekt wieder verwenden, indem Sie `Open` für dieselbe Datenquelle oder eine andere Datenquelle aufrufen.

Alle ausstehenden [AddNew](#addnew) -oder [Edit](#edit) -Anweisungen werden abgebrochen, und für alle ausstehenden Transaktionen wird ein Rollback ausgeführt. Wenn Sie ausstehende Ergänzungen oder bearbeitbare Änderungen beibehalten möchten, müssen Sie [Update](#update) ausführen, bevor Sie `Close` für jedes Recordset aufzurufen.

Sie können `Open` nach dem Aufrufen von erneut aufrufen `Close` . Auf diese Weise können Sie das Recordset-Objekt wieder verwenden. Eine bessere Alternative ist das aufzurufen von [Anforderungen](#requery), wenn möglich.

Weitere Informationen finden Sie im Thema "close method" in der DAO-Hilfe.

## <a name="cdaorecordsetdelete"></a><a name="delete"></a> CDaoRecordset::D Elete

Mit dieser Member-Funktion können Sie den aktuellen Datensatz in einem Open Dynaset-Type-oder Table-Recordset-Objekt löschen.

```cpp
virtual void Delete();
```

### <a name="remarks"></a>Bemerkungen

Nach einem erfolgreichen Löschvorgang werden die Felddatenmember des Recordsets auf einen NULL-Wert festgelegt, und Sie müssen explizit eine der Funktionen des Recordset-Navigations Members aufrufen ( [verschieben](#move), [Suchen](#seek), [SetBookmark](#setbookmark)usw.), um den gelöschten Datensatz zu verschieben. Wenn Sie Datensätze aus einem Recordset löschen, muss vor dem Abrufen ein aktueller Datensatz im Recordset vorhanden sein `Delete` . andernfalls löst MFC eine Ausnahme aus.

`Delete` entfernt den aktuellen Datensatz und macht ihn nicht zugänglich. Obwohl Sie den gelöschten Datensatz nicht bearbeiten oder verwenden können, bleibt er aktuell. Wenn Sie jedoch zu einem anderen Datensatz wechseln, können Sie den gelöschten Datensatz nicht mehr auf dem aktuellen standhalten.

> [!CAUTION]
> Das Recordset muss aktualisierbar sein, und es muss ein gültiger Datensatz im Recordset vorhanden sein, wenn aufgerufen wird `Delete` . Wenn Sie z. b. einen Datensatz löschen, aber keinen Bildlauf zu einem neuen Datensatz ausführen, bevor Sie den Vorgang `Delete` erneut ausführen, wird von `Delete` eine [CDaoException](../../mfc/reference/cdaoexception-class.md)ausgelöst.

Sie können einen Datensatz wiederherstellen, wenn Sie Transaktionen verwenden und die Member-Funktion [CDaoWorkspace:: Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback) aufruft. Wenn die Basistabelle die primäre Tabelle in einer kaskadierenden Lösch Beziehung ist, kann durch das Löschen des aktuellen Datensatzes auch ein oder mehrere Datensätze in einer fremd Tabelle gelöscht werden. Weitere Informationen finden Sie in der Datei "Cascade Delete" in der DAO-Hilfe.

Im Gegensatz zu `AddNew` und `Edit` folgt ein-aufrufsbefehl nicht einem-Befehl `Delete` `Update` .

Weitere Informationen finden Sie in den Themen "AddNew Method", "Edit Method", "Delete Method", "Update Method" und "Updatable Property" in der DAO-Hilfe.

## <a name="cdaorecordsetdofieldexchange"></a><a name="dofieldexchange"></a> CDaoRecordset::D ofieldexchange

Das Framework ruft diese Member-Funktion auf, um automatisch Daten zwischen den Felddatenmembern des Recordset-Objekts und den entsprechenden Spalten des aktuellen Datensatzes in der Datenquelle auszutauschen.

```cpp
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Enthält einen Zeiger auf ein- `CDaoFieldExchange` Objekt. Das Framework hat dieses Objekt bereits so eingerichtet, dass ein Kontext für den Feld Austausch Vorgang angegeben wird.

### <a name="remarks"></a>Bemerkungen

Außerdem werden die Parameter Datenmember, sofern vorhanden, an die Parameter Platzhalter in der SQL-Anweisungs Zeichenfolge für die Auswahl des Recordsets gebunden. Der Austausch von Felddaten, die als DAO-Daten Satz Feld Austausch (DFX) bezeichnet werden, funktioniert in beide Richtungen: von den Felddatenmembern des Recordset-Objekts zu den Feldern des Datensatzes in der Datenquelle und vom Datensatz der Datenquelle zum Recordset-Objekt. Wenn Sie Spalten dynamisch binden, ist es nicht erforderlich, zu implementieren `DoFieldExchange` .

Die einzige Aktion, die Sie normalerweise ausführen müssen, um `DoFieldExchange` für die abgeleitete Recordset-Klasse zu implementieren, besteht darin, die-Klasse mit ClassWizard zu erstellen und die Namen und Datentypen der Felddatenmember anzugeben. Sie können auch Code hinzufügen, der von ClassWizard zum Angeben von Parameterdatenmembern geschrieben wird. Wenn alle Felder dynamisch gebunden werden sollen, ist diese Funktion inaktiv, es sei denn, Sie geben Parameter Datenmember an.

Wenn Sie die abgeleitete Recordsetklasse mit ClassWizard deklarieren, schreibt der Assistent eine außer Kraft Setzung von `DoFieldExchange` für Sie, die dem folgenden Beispiel ähnelt:

[!code-cpp[NVC_MFCDatabase#2](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]

## <a name="cdaorecordsetedit"></a><a name="edit"></a> CDaoRecordset:: Edit

Diese Member-Funktion wird aufgerufen, um Änderungen am aktuellen Datensatz zuzulassen.

```cpp
virtual void Edit();
```

### <a name="remarks"></a>Bemerkungen

Nachdem Sie die `Edit` Member-Funktion aufgerufen haben, werden Änderungen, die an den Feldern des aktuellen Datensatzes vorgenommen werden, in den Kopier Puffer kopiert. Nachdem Sie die gewünschten Änderungen am Datensatz vorgenommen haben, geben Sie `Update` an, um die Änderungen zu speichern. `Edit` speichert die Werte der Datenmember des Recordsets. Wenn Sie den Befehl ausführen `Edit` , Änderungen vornehmen und dann erneut aufzurufen `Edit` , werden die Werte des Datensatzes vor dem ersten-Befehl wieder hergestellt `Edit` .

> [!CAUTION]
> Wenn Sie einen Datensatz bearbeiten und dann einen Vorgang ausführen, der zu einem anderen Datensatz verschoben wird, ohne dass Sie zunächst aufrufen `Update` , gehen Ihre Änderungen ohne Warnung verloren. Wenn Sie das Recordset oder die übergeordnete Datenbank schließen, wird der bearbeitete Datensatz außerdem ohne Warnung verworfen.

In einigen Fällen möchten Sie möglicherweise eine Spalte aktualisieren, indem Sie Sie auf NULL (ohne Daten) festlegen. Um dies zu erreichen, müssen Sie `SetFieldNull` mit dem Parameter true aufrufen, um das Feld NULL zu markieren. Dies bewirkt auch, dass die Spalte aktualisiert wird. Wenn Sie möchten, dass ein Feld in die Datenquelle geschrieben wird, auch wenn der Wert nicht geändert wurde, können Sie `SetFieldDirty` mit dem Parameter true aufrufen. Dies funktioniert auch, wenn das Feld den Wert NULL aufweist.

Das Framework markiert geänderte Felddatenmember, um sicherzustellen, dass Sie durch den DAO-Daten Satz Feld Austausch-Mechanismus (DFX) in den Datensatz der Datenquelle geschrieben werden. Wenn Sie den Wert eines Felds ändern, wird das Feld in der Regel automatisch geändert, sodass Sie nur selten [SetFieldDirty](#setfielddirty) aufrufen müssen. manchmal möchten Sie jedoch sicherstellen, dass die Spalten explizit aktualisiert oder eingefügt werden, unabhängig davon, welcher Wert im Feld Datenmember ist. Der DFX-Mechanismus nutzt auch die Verwendung von **Pseudo-NULL**. Weitere Informationen finden Sie unter [CDaoFieldExchange:: m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Wenn der Mechanismus für die doppelte Pufferung nicht verwendet wird, wird das Feld nicht automatisch als geändert festgelegt, wenn der Wert des Felds geändert wird. In diesem Fall muss das Feld explizit festgelegt werden. Das Flag in [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) steuert diese automatische Feld Überprüfung.

Wenn das Recordset-Objekt pessimistisch in einer mehr Benutzerumgebung gesperrt ist, bleibt der Datensatz von der Zeit `Edit` bis zum Abschluss der Aktualisierung gesperrt. Wenn das Recordset optimistisch gesperrt ist, wird der Datensatz gesperrt und mit dem vorab bearbeiteten Datensatz verglichen, kurz bevor er in der Datenbank aktualisiert wird. Wenn sich der Datensatz geändert hat, seit Sie aufgerufen `Edit` haben, `Update` schlägt der Vorgang fehl, und MFC löst eine Ausnahme aus. Sie können den Sperrmodus mit ändern `SetLockingMode` .

> [!NOTE]
> Die optimistische Sperre wird immer in externen Daten Bank Formaten wie ODBC und installier barer ISAM verwendet.

Der aktuelle Datensatz bleibt nach dem-Befehl aktuell `Edit` . Um aufzurufen `Edit` , muss ein aktueller Datensatz vorhanden sein. Wenn kein aktueller Datensatz vorhanden ist oder das Recordset nicht auf ein offenes Recordset-Objekt vom Typ Table-Type oder Dynaset verweist, tritt eine Ausnahme auf. `Edit` `CDaoException` Das Aufrufen von bewirkt, dass eine unter den folgenden Bedingungen ausgelöst wird:

- Es ist kein aktueller Datensatz vorhanden.

- Die Datenbank oder das Recordset ist schreibgeschützt.

- Im Datensatz sind keine Felder aktualisierbar.

- Die Datenbank oder das Recordset wurde für die ausschließliche Verwendung durch einen anderen Benutzer geöffnet.

- Ein anderer Benutzer hat die Seite mit dem Datensatz gesperrt.

Wenn die Datenquelle Transaktionen unterstützt, können Sie den `Edit` callpart einer Transaktion ausführen. Beachten Sie, dass Sie `CDaoWorkspace::BeginTrans` vor dem Aufrufen von `Edit` und nach dem Öffnen des Recordsets aufrufen sollten. Beachten Sie außerdem, dass `CDaoWorkspace::CommitTrans` der Aufruf von kein Ersatz für den Aufruf von ist `Update` , um den `Edit` Vorgang abzuschließen. Weitere Informationen zu Transaktionen finden Sie unter-Klasse `CDaoWorkspace` .

Weitere Informationen finden Sie in den Themen "AddNew Method", "Edit Method", "Delete Method", "Update Method" und "Updatable Property" in der DAO-Hilfe.

## <a name="cdaorecordsetfillcache"></a><a name="fillcache"></a> CDaoRecordset:: FillCache

Diese Member-Funktion aufrufen, um eine angegebene Anzahl von Datensätzen aus dem Recordset zwischenzuspeichern.

```cpp
void FillCache(
    long* pSize = NULL,
    COleVariant* pBookmark = NULL);
```

### <a name="parameters"></a>Parameter

*Psize*<br/>
Gibt die Anzahl der Zeilen an, die in den Cache aufgefüllt werden sollen. Wenn Sie diesen Parameter weglassen, wird der Wert durch die CacheSize-Eigenschafts Einstellung des zugrunde liegenden DAO-Objekts bestimmt.

*pBookmark*<br/>
Ein [COleVariant](../../mfc/reference/colevariant-class.md) , der ein Lesezeichen angibt. Der Cache wird beginnend mit dem Datensatz gefüllt, der durch dieses Lesezeichen angegeben wird. Wenn Sie diesen Parameter weglassen, wird der Cache beginnend mit dem Datensatz gefüllt, der durch die CacheStart-Eigenschaft des zugrunde liegenden DAO-Objekts angegeben wird.

### <a name="remarks"></a>Bemerkungen

Caching verbessert die Leistung einer Anwendung, die Daten von einem Remote Server abruft oder abruft. Bei einem Cache handelt es sich um Speicherplatz im lokalen Arbeitsspeicher, der die Daten enthält, die zuletzt vom Server abgerufen wurden, wenn davon ausgegangen wird, dass die Daten wahrscheinlich erneut angefordert werden, während die Anwendung ausgeführt wird. Wenn Daten angefordert werden, prüft die Microsoft Jet-Datenbank-Engine zuerst den Cache auf die Daten, anstatt Sie vom Server abzurufen, was mehr Zeit in sich bringt. Die Verwendung der Daten Zwischenspeicherung für nicht-ODBC-Datenquellen hat keine Auswirkung, da die Daten nicht im Cache gespeichert werden.

Anstatt zu warten, bis der Cache mit Datensätzen gefüllt ist, während Sie abgerufen werden, können Sie den Cache jederzeit explizit ausfüllen, indem Sie die- `FillCache` Member-Funktion aufrufen. Dies ist eine schnellere Möglichkeit, den Cache zu füllen, da `FillCache` mehrere Datensätze gleichzeitig statt einzeln von abgerufen werden. Wenn z. b. alle screenys von Datensätzen angezeigt werden, können Sie Ihre Anwendung `FillCache` zum Abrufen der nächsten Datensätze anzeigen lassen.

Jede ODBC-Datenbank, auf die mit Recordset-Objekten zugegriffen wird, kann einen lokalen Cache haben. Um den Cache zu erstellen, öffnen Sie ein Recordset-Objekt aus der Remote Datenquelle, und rufen Sie dann die `SetCacheSize` -und- `SetCacheStart` Member-Funktionen des Recordsets auf. Wenn *LSIZE* und *lBookmark* einen Bereich erstellen, der teilweise oder ganz außerhalb des durch und angegebenen Bereichs liegt `SetCacheSize` `SetCacheStart` , wird der Teil des Recordsets außerhalb dieses Bereichs ignoriert und nicht in den Cache geladen. Wenn `FillCache` mehr Datensätze als in der Remote Datenquelle verbleiben, werden nur die verbleibenden Datensätze abgerufen, und es wird keine Ausnahme ausgelöst.

Datensätze, die aus dem Cache abgerufen werden, spiegeln nicht die von anderen Benutzern gleichzeitig an den Quelldaten vorgenommenen Änderungen wider.

`FillCache` Ruft nur Einträge ab, die noch nicht zwischengespeichert wurden. Um ein Update aller zwischengespeicherten Daten zu erzwingen, müssen `SetCacheSize` Sie die Member-Funktion mit einem *LSIZE* -Parameter gleich 0 aufrufen, den Befehl erneut ausführen, `SetCacheSize` wobei der *LSIZE* -Parameter der Größe des Cache entspricht, den Sie ursprünglich angefordert haben, und dann aufrufen `FillCache` .

Weitere Informationen finden Sie im Thema "FillCache-Methode" in der DAO-Hilfe.

## <a name="cdaorecordsetfind"></a><a name="find"></a> CDaoRecordset:: Find

Mit dieser Member-Funktion können Sie eine bestimmte Zeichenfolge in einem Dynaset-oder Snapshot-Type-Recordset mithilfe eines Vergleichs Operators suchen.

```cpp
virtual BOOL Find(
    long lFindType,
    LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parameter

*lfindtype*<br/>
Ein-Wert, der den Typ des gewünschten Such Vorgangs angibt. Mögliche Werte:

- AFX_DAO_NEXT den nächsten Speicherort einer übereinstimmenden Zeichenfolge suchen.

- AFX_DAO_PREV den vorherigen Speicherort einer übereinstimmenden Zeichenfolge suchen.

- AFX_DAO_FIRST den ersten Speicherort einer übereinstimmenden Zeichenfolge suchen.

- AFX_DAO_LAST den letzten Speicherort einer übereinstimmenden Zeichenfolge suchen.

*lpszfilter*<br/>
Ein Zeichen folgen Ausdruck (wie die **Where** -Klausel in einer SQL-Anweisung ohne das Wort **Where**), der zum Suchen des Datensatzes verwendet wird. Beispiel:

[!code-cpp[NVC_MFCDatabase#3](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn übereinstimmende Datensätze gefunden werden, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie können die erste, nächste, vorherige oder letzte Instanz der Zeichenfolge finden. `Find` ist eine virtuelle Funktion, sodass Sie Sie überschreiben und eine eigene Implementierung hinzufügen können. Die `FindFirst` `FindLast` -, `FindNext` -,-und- `FindPrev` Member-Funktionen nennen die- `Find` Member-Funktion, sodass Sie `Find` zum Steuern des Verhaltens von Such Vorgängen verwenden können.

Um einen Datensatz in einem Recordset des Tabellentyps zu suchen, müssen Sie die [Seek](#seek) -Member-Funktion aufzurufen.

> [!TIP]
> Der kleinere Satz von Datensätzen, desto effektiver ist `Find` . Im allgemeinen und insbesondere bei ODBC-Daten ist es besser, eine neue Abfrage zu erstellen, die nur die gewünschten Datensätze abruft.

Weitere Informationen finden Sie im Thema "FindFirst, FindLast, FindNext, FindPrevious Methods" in der DAO-Hilfe.

## <a name="cdaorecordsetfindfirst"></a><a name="findfirst"></a> CDaoRecordset:: FindFirst

Mit dieser Member-Funktion können Sie den ersten Datensatz ermitteln, der mit einer angegebenen Bedingung übereinstimmt.

```cpp
BOOL FindFirst(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parameter

*lpszfilter*<br/>
Ein Zeichen folgen Ausdruck (wie die **Where** -Klausel in einer SQL-Anweisung ohne das Wort **Where**), der zum Suchen des Datensatzes verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn übereinstimmende Datensätze gefunden werden, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die `FindFirst` Member-Funktion beginnt die Suche am Anfang des Recordsets und sucht bis zum Ende des Recordsets.

Wenn Sie alle Datensätze in die Suche einschließen möchten (nicht nur die, die eine bestimmte Bedingung erfüllen), verwenden Sie einen der Verschiebungs Vorgänge, um von Datensatz zu Datensatz zu wechseln. Um einen Datensatz in einem Recordset des Tabellentyps zu suchen, müssen Sie die-Member-Funktion aufzurufen `Seek` .

Wenn ein Datensatz, der mit den Kriterien übereinstimmt, nicht gefunden wird, wird der aktuelle Daten Satz Zeiger nicht bestimmt und `FindFirst` gibt NULL zurück. Wenn das Recordset mehr als einen Datensatz enthält, der die Kriterien erfüllt, wird `FindFirst` das erste Vorkommen, `FindNext` das nächste Vorkommen und so weiter.

> [!CAUTION]
> Wenn Sie den aktuellen Datensatz bearbeiten, stellen Sie sicher, dass Sie die Änderungen speichern, indem Sie die-Element Funktion aufrufen, `Update` bevor Sie zu einem anderen Datensatz wechseln. Wenn Sie zu einem anderen Datensatz wechseln, ohne zu aktualisieren, gehen Ihre Änderungen ohne Warnung verloren.

Die Element `Find` Funktionen suchen aus dem Speicherort und in der in der folgenden Tabelle angegebenen Richtung:

|Suchen von Vorgängen|Starten|Suchrichtung|
|---------------------|-----------|----------------------|
|`FindFirst`|Anfang des Recordsets|Ende des Recordsets|
|`FindLast`|Ende des Recordsets|Anfang des Recordsets|
|`FindNext`|Aktueller Datensatz|Ende des Recordsets|
|`FindPrevious`|Aktueller Datensatz|Anfang des Recordsets|

> [!NOTE]
> Wenn Sie anrufen `FindLast` , füllt das Microsoft Jet-Datenbankmodul das Recordset vollständig auf, bevor Sie mit der Suche beginnen, sofern dies noch nicht geschehen ist. Die erste Suche kann länger dauern als nachfolgende Suchvorgänge.

Die Verwendung eines der Suchvorgänge ist nicht das gleiche wie das Aufrufen von `MoveFirst` oder `MoveNext` . Dadurch wird der erste oder nächste Datensatz auf den aktuellen Wert festgelegt, ohne dass eine Bedingung angegeben wird. Sie können einen Suchvorgang mit einem Verschiebungs Vorgang ausführen.

Beachten Sie bei der Verwendung der Suchvorgänge Folgendes:

- Wenn einen Wert ungleich `Find` 0 (null) zurückgibt, ist der aktuelle Datensatz nicht definiert. In diesem Fall müssen Sie den aktuellen Daten Satz Zeiger auf einen gültigen Datensatz zurück positionieren.

- Es ist nicht möglich, einen Suchvorgang mit einem Bild lauffähige Recordset mit vorwärts Bildlauf zu verwenden.

- Sie sollten das US-Datumsformat (Monat-Tag-Jahr) verwenden, wenn Sie nach Feldern mit Datumsangaben suchen, auch wenn Sie nicht die US-Version der Microsoft Jet-Datenbank-Engine verwenden. Andernfalls werden übereinstimmende Datensätze möglicherweise nicht gefunden.

- Beim Arbeiten mit ODBC-Datenbanken und großen Dynasets können Sie feststellen, dass die Verwendung der Suchvorgänge langsam ist, insbesondere bei der Arbeit mit großen Recordsets. Sie können die Leistung verbessern, indem Sie SQL-Abfragen mit angepassten **OrderBy** -oder **Where** -Klauseln, Parameterabfragen oder Objekten verwenden, `CDaoQuerydef` die bestimmte indizierte Datensätze abrufen.

Weitere Informationen finden Sie im Thema "FindFirst, FindLast, FindNext, FindPrevious Methods" in der DAO-Hilfe.

## <a name="cdaorecordsetfindlast"></a><a name="findlast"></a> CDaoRecordset:: FindLast

Mit dieser Member-Funktion können Sie den letzten Datensatz ermitteln, der mit einer angegebenen Bedingung übereinstimmt.

```cpp
BOOL FindLast(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parameter

*lpszfilter*<br/>
Ein Zeichen folgen Ausdruck (wie die **Where** -Klausel in einer SQL-Anweisung ohne das Wort **Where**), der zum Suchen des Datensatzes verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn übereinstimmende Datensätze gefunden werden, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die `FindLast` Member-Funktion beginnt die Suche am Ende des Recordsets und wird rückwärts zum Anfang des Recordsets durchsucht.

Wenn Sie alle Datensätze in die Suche einschließen möchten (nicht nur die, die eine bestimmte Bedingung erfüllen), verwenden Sie einen der Verschiebungs Vorgänge, um von Datensatz zu Datensatz zu wechseln. Um einen Datensatz in einem Recordset des Tabellentyps zu suchen, müssen Sie die-Member-Funktion aufzurufen `Seek` .

Wenn ein Datensatz, der mit den Kriterien übereinstimmt, nicht gefunden wird, wird der aktuelle Daten Satz Zeiger nicht bestimmt und `FindLast` gibt NULL zurück. Wenn das Recordset mehr als einen Datensatz enthält, der die Kriterien erfüllt, wird `FindFirst` das erste Vorkommen von lokalisiert, `FindNext` das nächste Vorkommen nach dem ersten Vorkommen und so weiter.

> [!CAUTION]
> Wenn Sie den aktuellen Datensatz bearbeiten, stellen Sie sicher, dass Sie die Änderungen speichern, indem Sie die-Element Funktion aufrufen, `Update` bevor Sie zu einem anderen Datensatz wechseln. Wenn Sie zu einem anderen Datensatz wechseln, ohne zu aktualisieren, gehen Ihre Änderungen ohne Warnung verloren.

Die Verwendung eines der Suchvorgänge ist nicht das gleiche wie das Aufrufen von `MoveFirst` oder `MoveNext` . Dadurch wird der erste oder nächste Datensatz auf den aktuellen Wert festgelegt, ohne dass eine Bedingung angegeben wird. Sie können einen Suchvorgang mit einem Verschiebungs Vorgang ausführen.

Beachten Sie bei der Verwendung der Suchvorgänge Folgendes:

- Wenn einen Wert ungleich `Find` 0 (null) zurückgibt, ist der aktuelle Datensatz nicht definiert. In diesem Fall müssen Sie den aktuellen Daten Satz Zeiger auf einen gültigen Datensatz zurück positionieren.

- Es ist nicht möglich, einen Suchvorgang mit einem Bild lauffähige Recordset mit vorwärts Bildlauf zu verwenden.

- Sie sollten das US-Datumsformat (Monat-Tag-Jahr) verwenden, wenn Sie nach Feldern mit Datumsangaben suchen, auch wenn Sie nicht die US-Version der Microsoft Jet-Datenbank-Engine verwenden. Andernfalls werden übereinstimmende Datensätze möglicherweise nicht gefunden.

- Beim Arbeiten mit ODBC-Datenbanken und großen Dynasets können Sie feststellen, dass die Verwendung der Suchvorgänge langsam ist, insbesondere bei der Arbeit mit großen Recordsets. Sie können die Leistung verbessern, indem Sie SQL-Abfragen mit angepassten **OrderBy** -oder **Where** -Klauseln, Parameterabfragen oder Objekten verwenden, `CDaoQuerydef` die bestimmte indizierte Datensätze abrufen.

Weitere Informationen finden Sie im Thema "FindFirst, FindLast, FindNext, FindPrevious Methods" in der DAO-Hilfe.

## <a name="cdaorecordsetfindnext"></a><a name="findnext"></a> CDaoRecordset:: FindNext

Mit dieser Member-Funktion können Sie den nächsten Datensatz ermitteln, der mit einer angegebenen Bedingung übereinstimmt.

```cpp
BOOL FindNext(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parameter

*lpszfilter*<br/>
Ein Zeichen folgen Ausdruck (wie die **Where** -Klausel in einer SQL-Anweisung ohne das Wort **Where**), der zum Suchen des Datensatzes verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn übereinstimmende Datensätze gefunden werden, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die `FindNext` Member-Funktion beginnt mit der Suche nach dem aktuellen Datensatz und sucht bis zum Ende des Recordsets.

Wenn Sie alle Datensätze in die Suche einschließen möchten (nicht nur die, die eine bestimmte Bedingung erfüllen), verwenden Sie einen der Verschiebungs Vorgänge, um von Datensatz zu Datensatz zu wechseln. Um einen Datensatz in einem Recordset des Tabellentyps zu suchen, müssen Sie die-Member-Funktion aufzurufen `Seek` .

Wenn ein Datensatz, der mit den Kriterien übereinstimmt, nicht gefunden wird, wird der aktuelle Daten Satz Zeiger nicht bestimmt und `FindNext` gibt NULL zurück. Wenn das Recordset mehr als einen Datensatz enthält, der die Kriterien erfüllt, wird `FindFirst` das erste Vorkommen, `FindNext` das nächste Vorkommen und so weiter.

> [!CAUTION]
> Wenn Sie den aktuellen Datensatz bearbeiten, stellen Sie sicher, dass Sie die Änderungen speichern, indem Sie die-Element Funktion aufrufen, `Update` bevor Sie zu einem anderen Datensatz wechseln. Wenn Sie zu einem anderen Datensatz wechseln, ohne zu aktualisieren, gehen Ihre Änderungen ohne Warnung verloren.

Die Verwendung eines der Suchvorgänge ist nicht das gleiche wie das Aufrufen von `MoveFirst` oder `MoveNext` . Dadurch wird der erste oder nächste Datensatz auf den aktuellen Wert festgelegt, ohne dass eine Bedingung angegeben wird. Sie können einen Suchvorgang mit einem Verschiebungs Vorgang ausführen.

Beachten Sie bei der Verwendung der Suchvorgänge Folgendes:

- Wenn einen Wert ungleich `Find` 0 (null) zurückgibt, ist der aktuelle Datensatz nicht definiert. In diesem Fall müssen Sie den aktuellen Daten Satz Zeiger auf einen gültigen Datensatz zurück positionieren.

- Es ist nicht möglich, einen Suchvorgang mit einem Bild lauffähige Recordset mit vorwärts Bildlauf zu verwenden.

- Sie sollten das US-Datumsformat (Monat-Tag-Jahr) verwenden, wenn Sie nach Feldern mit Datumsangaben suchen, auch wenn Sie nicht die US-Version der Microsoft Jet-Datenbank-Engine verwenden. Andernfalls werden übereinstimmende Datensätze möglicherweise nicht gefunden.

- Beim Arbeiten mit ODBC-Datenbanken und großen Dynasets können Sie feststellen, dass die Verwendung der Suchvorgänge langsam ist, insbesondere bei der Arbeit mit großen Recordsets. Sie können die Leistung verbessern, indem Sie SQL-Abfragen mit angepassten **OrderBy** -oder **Where** -Klauseln, Parameterabfragen oder Objekten verwenden, `CDaoQuerydef` die bestimmte indizierte Datensätze abrufen.

Weitere Informationen finden Sie im Thema "FindFirst, FindLast, FindNext, FindPrevious Methods" in der DAO-Hilfe.

## <a name="cdaorecordsetfindprev"></a><a name="findprev"></a> CDaoRecordset:: findprev

Mit dieser Member-Funktion können Sie den vorherigen Datensatz ermitteln, der mit einer angegebenen Bedingung übereinstimmt.

```cpp
BOOL FindPrev(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parameter

*lpszfilter*<br/>
Ein Zeichen folgen Ausdruck (wie die **Where** -Klausel in einer SQL-Anweisung ohne das Wort **Where**), der zum Suchen des Datensatzes verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn übereinstimmende Datensätze gefunden werden, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die `FindPrev` Member-Funktion beginnt mit der Suche im aktuellen Datensatz und sucht rückwärts nach dem Anfang des Recordsets.

Wenn Sie alle Datensätze in die Suche einschließen möchten (nicht nur die, die eine bestimmte Bedingung erfüllen), verwenden Sie einen der Verschiebungs Vorgänge, um von Datensatz zu Datensatz zu wechseln. Um einen Datensatz in einem Recordset des Tabellentyps zu suchen, müssen Sie die-Member-Funktion aufzurufen `Seek` .

Wenn ein Datensatz, der mit den Kriterien übereinstimmt, nicht gefunden wird, wird der aktuelle Daten Satz Zeiger nicht bestimmt und `FindPrev` gibt NULL zurück. Wenn das Recordset mehr als einen Datensatz enthält, der die Kriterien erfüllt, wird `FindFirst` das erste Vorkommen, `FindNext` das nächste Vorkommen und so weiter.

> [!CAUTION]
> Wenn Sie den aktuellen Datensatz bearbeiten, stellen Sie sicher, dass Sie die Änderungen speichern, indem Sie die-Element Funktion aufrufen, `Update` bevor Sie zu einem anderen Datensatz wechseln. Wenn Sie zu einem anderen Datensatz wechseln, ohne zu aktualisieren, gehen Ihre Änderungen ohne Warnung verloren.

Die Verwendung eines der Suchvorgänge ist nicht das gleiche wie das Aufrufen von `MoveFirst` oder `MoveNext` . Dadurch wird der erste oder nächste Datensatz auf den aktuellen Wert festgelegt, ohne dass eine Bedingung angegeben wird. Sie können einen Suchvorgang mit einem Verschiebungs Vorgang ausführen.

Beachten Sie bei der Verwendung der Suchvorgänge Folgendes:

- Wenn einen Wert ungleich `Find` 0 (null) zurückgibt, ist der aktuelle Datensatz nicht definiert. In diesem Fall müssen Sie den aktuellen Daten Satz Zeiger auf einen gültigen Datensatz zurück positionieren.

- Es ist nicht möglich, einen Suchvorgang mit einem Bild lauffähige Recordset mit vorwärts Bildlauf zu verwenden.

- Sie sollten das US-Datumsformat (Monat-Tag-Jahr) verwenden, wenn Sie nach Feldern mit Datumsangaben suchen, auch wenn Sie nicht die US-Version der Microsoft Jet-Datenbank-Engine verwenden. Andernfalls werden übereinstimmende Datensätze möglicherweise nicht gefunden.

- Beim Arbeiten mit ODBC-Datenbanken und großen Dynasets können Sie feststellen, dass die Verwendung der Suchvorgänge langsam ist, insbesondere bei der Arbeit mit großen Recordsets. Sie können die Leistung verbessern, indem Sie SQL-Abfragen mit angepassten **OrderBy** -oder **Where** -Klauseln, Parameterabfragen oder Objekten verwenden, `CDaoQuerydef` die bestimmte indizierte Datensätze abrufen.

Weitere Informationen finden Sie im Thema "FindFirst, FindLast, FindNext, FindPrevious Methods" in der DAO-Hilfe.

## <a name="cdaorecordsetgetabsoluteposition"></a><a name="getabsoluteposition"></a> CDaoRecordset:: GetAbsolutePosition

Gibt die Datensatznummer des aktuellen Datensatzes eines Recordset-Objekts zurück.

```cpp
long GetAbsolutePosition();
```

### <a name="return-value"></a>Rückgabewert

Eine ganze Zahl zwischen 0 und der Anzahl der Datensätze im Recordset. Entspricht der Ordinalposition des aktuellen Datensatzes im Recordset.

### <a name="remarks"></a>Bemerkungen

Der AbsolutePosition-Eigenschafts Wert des zugrunde liegenden DAO-Objekts ist NULL basiert. eine Einstellung von 0 bezieht sich auf den ersten Datensatz im Recordset. Sie können die Anzahl der gefüllten Datensätze im Recordset durch Aufrufen von [GetRecordCount](#getrecordcount)ermitteln. `GetRecordCount`Das Aufrufen von kann einige Zeit in Anspruch nehmen, da der Zugriff auf alle Datensätze erforderlich ist

Wenn kein aktueller Datensatz vorhanden ist, so als wenn keine Datensätze im Recordset vorhanden sind, wird-1 zurückgegeben. Wenn der aktuelle Datensatz gelöscht wird, ist der Wert der AbsolutePosition-Eigenschaft nicht definiert, und MFC löst eine Ausnahme aus, wenn darauf verwiesen wird. Für den Dynaset-Typ Recordsets werden neue Datensätze am Ende der Sequenz hinzugefügt.

> [!NOTE]
> Diese Eigenschaft ist nicht für die Verwendung als Ersatz Zeichenfolge vorgesehen. Lesezeichen sind immer noch die empfohlene Methode zum beibehalten und zurückkehren zu einer gegebenen Position und sind die einzige Möglichkeit, den aktuellen Datensatz für alle Typen von recordsetobjekten zu positionieren. Insbesondere wird die Position eines bestimmten Datensatzes geändert, wenn Datensätze vor dem Löschen gelöscht werden. Es ist auch nicht sichergestellt, dass ein bestimmter Datensatz die gleiche absolute Position hat, wenn der Recordset erneut erstellt wird, da die Reihenfolge der einzelnen Datensätze in einem Recordset nicht garantiert wird, es sei denn, Sie wird mit einer SQL-Anweisung mithilfe einer **OrderBy** -Klausel erstellt.

> [!NOTE]
> Diese Member-Funktion ist nur für den Dynaset-Type-und den Snapshot-Type-Recordsets gültig.

Weitere Informationen finden Sie im Thema "AbsolutePosition-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetgetbookmark"></a><a name="getbookmark"></a> CDaoRecordset:: GetBookmark

Mit dieser Member-Funktion können Sie den Lesezeichen Wert in einem bestimmten Datensatz abrufen.

```cpp
COleVariant GetBookmark();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Wert zurück, der das Lesezeichen für den aktuellen Datensatz darstellt.

### <a name="remarks"></a>Bemerkungen

Wenn ein Recordset-Objekt erstellt oder geöffnet wird, verfügt jeder seiner Datensätze bereits über ein eindeutiges Lesezeichen, wenn es diese unterstützt. Wird aufgerufen `CanBookmark` , um zu bestimmen, ob ein Recordset Lesezeichen unterstützt

Sie können das Lesezeichen für den aktuellen Datensatz speichern, indem Sie den Wert des Lesezeichens einem- `COleVariant` Objekt zuweisen. Um nach dem Wechsel zu einem anderen Datensatz schnell zu diesem Datensatz zurückzukehren, müssen Sie `SetBookmark` mit einem Parameter aufrufen, der dem Wert dieses `COleVariant` Objekts entspricht.

> [!NOTE]
> Der Aufruf von " [Requery](#requery) " ändert DAO-Lesezeichen

Weitere Informationen finden Sie im Thema "Bookmark Property" in der DAO-Hilfe.

## <a name="cdaorecordsetgetcachesize"></a><a name="getcachesize"></a> CDaoRecordset:: getCacheSize

Mit dieser Member-Funktion können Sie die Anzahl der zwischengespeicherten Datensätze abrufen.

```cpp
long GetCacheSize();
```

### <a name="return-value"></a>Rückgabewert

Ein-Wert, der die Anzahl der Datensätze in einem Dynaset-Recordset angibt, das Daten enthält, die lokal aus einer ODBC-Datenquelle zwischengespeichert werden sollen.

### <a name="remarks"></a>Bemerkungen

Das Zwischenspeichern von Daten verbessert die Leistung einer Anwendung, die Daten von einem Remote Server durch Dynaset-Type Recordset-Objekte abruft. Ein Cache ist ein Speicherplatz im lokalen Speicher, der die Daten enthält, die zuletzt vom Server abgerufen wurden, wenn die Daten während der Ausführung der Anwendung erneut angefordert werden. Wenn Daten angefordert werden, überprüft die Microsoft Jet-Datenbank-Engine den Cache zuerst auf die angeforderten Daten, anstatt Sie vom Server abzurufen, was mehr Zeit in sich bringt. Daten, die nicht aus einer ODBC-Datenquelle stammen, werden nicht im Cache gespeichert.

Jede ODBC-Datenquelle, z. b. eine angefügte Tabelle, kann über einen lokalen Cache verfügen.

Weitere Informationen finden Sie im Thema "CacheSize, CacheStart Properties" in der DAO-Hilfe.

## <a name="cdaorecordsetgetcachestart"></a><a name="getcachestart"></a> CDaoRecordset:: getcachestart

Rufen Sie diese Member-Funktion auf, um den Lesezeichen Wert des ersten Datensatzes im Recordset zu erhalten, das zwischengespeichert werden soll.

```cpp
COleVariant GetCacheStart();
```

### <a name="return-value"></a>Rückgabewert

Ein `COleVariant` , der das Lesezeichen des ersten Datensatzes im Recordset angibt, das zwischengespeichert werden soll.

### <a name="remarks"></a>Bemerkungen

Die Microsoft Jet-Datenbank-Engine fordert Datensätze im Cache Bereich aus dem Cache an und fordert Datensätze außerhalb des Cache Bereichs vom Server an.

> [!NOTE]
> Aus dem Cache abgerufene Datensätze enthalten keine Änderungen, die von anderen Benutzern gleichzeitig an den Quelldaten vorgenommen wurden.

Weitere Informationen finden Sie im Thema "CacheSize, CacheStart Properties" in der DAO-Hilfe.

## <a name="cdaorecordsetgetcurrentindex"></a><a name="getcurrentindex"></a> CDaoRecordset:: getcurrentindex

Mit dieser Member-Funktion können Sie den derzeit in einem indizierten Tabellentyp Objekt verwendeten Index ermitteln `CDaoRecordset` .

```cpp
CString GetCurrentIndex();
```

### <a name="return-value"></a>Rückgabewert

Ein-Wert, der `CString` den Namen des derzeit verwendeten Indexes mit einem Recordset des Tabellentyps enthält. Gibt eine leere Zeichenfolge zurück, wenn kein Index festgelegt wurde.

### <a name="remarks"></a>Bemerkungen

Dieser Index ist die Grundlage für das Anordnen von Datensätzen in einem Recordset des Tabellentyps und wird von der [Seek](#seek) Member-Funktion verwendet, um Datensätze zu suchen.

Ein- `CDaoRecordset` Objekt kann über mehr als einen Index verfügen, kann aber jeweils nur einen Index verwenden (obwohl für ein [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) -Objekt möglicherweise mehrere Indizes definiert sind).

Weitere Informationen finden Sie im Thema "Index Objekt" und in der Definition "aktueller Index" in der DAO-Hilfe.

## <a name="cdaorecordsetgetdatecreated"></a><a name="getdatecreated"></a> CDaoRecordset:: getdatecreated

Rufen Sie diese Member-Funktion auf, um das Datum und die Uhrzeit der Erstellung einer Basistabelle abzurufen.

```cpp
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Rückgabewert

Ein [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) -Objekt, das das Datum und die Uhrzeit der Erstellung der Basistabelle enthält.

### <a name="remarks"></a>Bemerkungen

Datums-und Uhrzeit Einstellungen werden von dem Computer abgeleitet, auf dem die Basistabelle erstellt wurde.

Weitere Informationen finden Sie im Thema "DateCreated, lastupated Properties" in der DAO-Hilfe.

## <a name="cdaorecordsetgetdatelastupdated"></a><a name="getdatelastupdated"></a> CDaoRecordset:: getdatelastupveraltet

Rufen Sie diese Member-Funktion auf, um das Datum und die Uhrzeit des letzten Updates des Schemas abzurufen.

```cpp
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Rückgabewert

Ein [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) -Objekt, das das Datum und die Uhrzeit des letzten Updates der Basistabellen Struktur (Schema) enthält.

### <a name="remarks"></a>Bemerkungen

Datums-und Uhrzeit Einstellungen werden von dem Computer abgeleitet, auf dem die Basistabellen Struktur (Schema) zuletzt aktualisiert wurde.

Weitere Informationen finden Sie im Thema "DateCreated, lastupated Properties" in der DAO-Hilfe.

## <a name="cdaorecordsetgetdefaultdbname"></a><a name="getdefaultdbname"></a> CDaoRecordset:: getdefaultdbname

Mit dieser Member-Funktion können Sie den Namen der Datenbank für dieses Recordset ermitteln.

```cpp
virtual CString GetDefaultDBName();
```

### <a name="return-value"></a>Rückgabewert

Ein `CString` , der den Pfad und den Namen der Datenbank enthält, von der dieses Recordset abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

Wenn ein Recordset ohne Zeiger auf eine [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)-Klasse erstellt wird, wird dieser Pfad vom Recordset verwendet, um die Standarddatenbank zu öffnen. Standardmäßig gibt diese Funktion eine leere Zeichenfolge zurück. Wenn ClassWizard ein neues Recordset von ableitet `CDaoRecordset` , wird diese Funktion für Sie erstellt.

Das folgende Beispiel veranschaulicht die Verwendung des doppelten umgekehrten Schrägstrichs ( \\ \\ ) in der Zeichenfolge, wie erforderlich ist, damit die Zeichenfolge ordnungsgemäß interpretiert wird.

[!code-cpp[NVC_MFCDatabase#4](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]

## <a name="cdaorecordsetgetdefaultsql"></a><a name="getdefaultsql"></a> CDaoRecordset:: getdefaulzql

Das Framework ruft diese Member-Funktion auf, um die SQL-Standard Anweisung zu erhalten, auf der das Recordset basiert.

```cpp
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>Rückgabewert

Ein-Wert `CString` , der die SQL-Standard Anweisung enthält.

### <a name="remarks"></a>Bemerkungen

Dabei kann es sich um einen Tabellennamen oder eine SQL **Select** -Anweisung handeln.

Sie definieren indirekt die Standard-SQL-Anweisung, indem Sie Ihre Recordset-Klasse mit ClassWizard deklarieren, und ClassWizard führt diese Aufgabe für Sie aus.

Wenn Sie eine zu [öffnende](#open)Null-SQL-Zeichenfolge übergeben, wird diese Funktion aufgerufen, um den Tabellennamen oder SQL für das Recordset zu ermitteln.

## <a name="cdaorecordsetgeteditmode"></a><a name="geteditmode"></a> CDaoRecordset:: geteditmode

Mit dieser Member-Funktion können Sie den Status der Bearbeitung ermitteln, d. h. einen der folgenden Werte:

```cpp
short GetEditMode();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Wert zurück, der den Bearbeitungsstatus für den aktuellen Datensatz angibt.

### <a name="remarks"></a>Bemerkungen

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|`dbEditNone`|Es wird kein Bearbeitungsvorgang ausgeführt.|
|`dbEditInProgress`|`Edit` wurde aufgerufen.|
|`dbEditAdd`|`AddNew` wurde aufgerufen.|

Weitere Informationen finden Sie im Thema "EditMode-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetgetfieldcount"></a><a name="getfieldcount"></a> CDaoRecordset:: GetFieldCount

Rufen Sie diese Member-Funktion auf, um die im Recordset definierte Anzahl von Feldern (Spalten) abzurufen.

```cpp
short GetFieldCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Felder im Recordset.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im Thema "count Property" in der DAO-Hilfe.

## <a name="cdaorecordsetgetfieldinfo"></a><a name="getfieldinfo"></a> CDaoRecordset:: getfieldinfo

Mit dieser Member-Funktion können Sie Informationen zu den Feldern in einem Recordset abrufen.

```cpp
void GetFieldInfo(
    int nIndex,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetFieldInfo(
    LPCTSTR lpszName,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der null basierte Index des vordefinierten Felds in der Feld Auflistung des Recordsets für die Suche nach Index.

*FieldInfo*<br/>
Ein Verweis auf eine [cdaofieldinfo](../../mfc/reference/cdaofieldinfo-structure.md) -Struktur.

*dwinfooptions*<br/>
Optionen, die angeben, welche Informationen zum Recordset abgerufen werden sollen. Die verfügbaren Optionen werden hier zusammen mit den Funktionen aufgelistet, die die Funktion zurückgibt. Um eine optimale Leistung zu erzielen, rufen Sie nur die Ebene der benötigten Informationen ab:

- `AFX_DAO_PRIMARY_INFO` Vorgegebene Name, Typ, Größe, Attribute

- `AFX_DAO_SECONDARY_INFO` Primärinformationen, plus: Ordinalposition, erforderlich, Null Länge zulassen, Sortierreihenfolge, fremd Name, Quellfeld, Quell Tabelle

- `AFX_DAO_ALL_INFO` Primäre und sekundäre Informationen, plus: Standardwert, Validierungs Regel, Validierungs Text

*lpszname*<br/>
Der Name des Felds.

### <a name="remarks"></a>Bemerkungen

Eine Version der-Funktion ermöglicht es Ihnen, ein Feld nach Index zu suchen. Mit der anderen Version können Sie nach einem Feld nach dem Namen suchen.

Eine Beschreibung der zurückgegebenen Informationen finden Sie in der [cdaofieldinfo](../../mfc/reference/cdaofieldinfo-structure.md) -Struktur. Diese Struktur enthält Member, die den in der Beschreibung von *dwinfooptions*aufgeführten Elementen der oben aufgeführten Informationen entsprechen. Wenn Sie Informationen auf einer Ebene anfordern, erhalten Sie auch Informationen zu allen vorherigen Ebenen.

Weitere Informationen finden Sie im Thema "Attribute-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetgetfieldvalue"></a><a name="getfieldvalue"></a> CDaoRecordset:: GetFieldValue

Rufen Sie diese Member-Funktion auf, um Daten in einem Recordset abzurufen.

```cpp
virtual void GetFieldValue(
    LPCTSTR lpszName,
    COleVariant& varValue);

virtual void GetFieldValue(
    int nIndex,
    COleVariant& varValue);

virtual COleVariant GetFieldValue(LPCTSTR lpszName);
virtual COleVariant GetFieldValue(int nIndex);
```

### <a name="parameters"></a>Parameter

*lpszname*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen eines Felds enthält.

*varValue*<br/>
Ein Verweis auf ein- `COleVariant` Objekt, in dem der Wert eines Felds gespeichert wird.

*nIndex*<br/>
Ein NULL basierter Index des Felds in der Fields-Auflistung des Recordsets für die Suche nach Index.

### <a name="return-value"></a>Rückgabewert

Die zwei Versionen von `GetFieldValue` , die einen Wert zurückgeben, geben ein [COleVariant](../../mfc/reference/colevariant-class.md) -Objekt zurück, das den Wert eines Felds enthält.

### <a name="remarks"></a>Bemerkungen

Sie können ein Feld nach Name oder Ordinalposition suchen.

> [!NOTE]
> Es ist effizienter, eine der Versionen dieser Member-Funktion aufzurufen, die einen- `COleVariant` Objekt Verweis als Parameter annimmt, anstatt eine Version aufzurufen, die ein-Objekt zurückgibt `COleVariant` . Die letztgenannten Versionen dieser Funktion werden aus Gründen der Abwärtskompatibilität beibehalten.

Verwenden `GetFieldValue` Sie und [SetFieldValue](#setfieldvalue) , um Felder zur Laufzeit dynamisch zu binden, anstatt Spalten mit dem [DoFieldExchange](#dofieldexchange) -Mechanismus statisch zu binden.

`GetFieldValue` der `DoFieldExchange` Mechanismus kann kombiniert werden, um die Leistung zu verbessern. Verwenden Sie z. b., `GetFieldValue` um einen Wert abzurufen, den Sie nur bei Bedarf benötigen, und weisen Sie den Aufruf einer Schaltfläche "Weitere Informationen" in der-Schnittstelle zu.

Weitere Informationen finden Sie in den Themen "Field Object" und "Value property" in der DAO-Hilfe.

## <a name="cdaorecordsetgetindexcount"></a><a name="getindexcount"></a> CDaoRecordset:: GetIndexCount

Mit dieser Member-Funktion können Sie die Anzahl der Indizes ermitteln, die für den Tabellentyp-Recordset verfügbar sind.

```cpp
short GetIndexCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Indizes im Recordset des Tabellentyps.

### <a name="remarks"></a>Bemerkungen

`GetIndexCount` ist nützlich, wenn alle Indizes im Recordset durchlaufen werden. Verwenden Sie zu diesem Zweck `GetIndexCount` in Verbindung mit [getIndexInfo](#getindexinfo). Wenn Sie diese Member-Funktion für den Dynaset-Type-oder den Snapshot-Typ-Recordsets aufzurufen, löst MFC eine Ausnahme aus.

Weitere Informationen finden Sie im Thema "Attribute-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetgetindexinfo"></a><a name="getindexinfo"></a> CDaoRecordset:: getIndexInfo

Mit dieser Member-Funktion können Sie verschiedene Arten von Informationen über einen Index abrufen, der in der Basistabelle definiert ist, die einem Recordset zugrunde liegt.

```cpp
void GetIndexInfo(
    int nIndex,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetIndexInfo(
    LPCTSTR lpszName,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der null basierte Index in der Index Auflistung der Tabelle für die Suche nach numerischer Position.

*indexInfo*<br/>
Ein Verweis auf eine [cdaoindexinfo](../../mfc/reference/cdaoindexinfo-structure.md) -Struktur.

*dwinfooptions*<br/>
Optionen, die angeben, welche Informationen über den Index abgerufen werden sollen. Die verfügbaren Optionen werden hier zusammen mit den Funktionen aufgelistet, die die Funktion zurückgibt. Um eine optimale Leistung zu erzielen, rufen Sie nur die Ebene der benötigten Informationen ab:

- `AFX_DAO_PRIMARY_INFO` Vorgegebene Name, Feld Info, Felder

- `AFX_DAO_SECONDARY_INFO` Primärinformationen, plus: primär, eindeutig, geclustert, ignorkoulls, erforderlich, fremd

- `AFX_DAO_ALL_INFO` Primäre und sekundäre Informationen, plus: unterschiedliche Anzahl

*lpszname*<br/>
Ein Zeiger auf den Namen des Index Objekts für die Suche nach Namen.

### <a name="remarks"></a>Bemerkungen

Eine Version der-Funktion ermöglicht es Ihnen, einen Index nach seiner Position in der Auflistung zu suchen. Mit der anderen Version können Sie einen Index nach Namen suchen.

Eine Beschreibung der zurückgegebenen Informationen finden Sie in der [cdaoindexinfo](../../mfc/reference/cdaoindexinfo-structure.md) -Struktur. Diese Struktur enthält Member, die den in der Beschreibung von *dwinfooptions*aufgeführten Elementen der oben aufgeführten Informationen entsprechen. Wenn Sie Informationen auf einer Ebene anfordern, erhalten Sie auch Informationen zu allen vorherigen Ebenen.

Weitere Informationen finden Sie im Thema "Attribute-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetgetlastmodifiedbookmark"></a><a name="getlastmodifiedbookmark"></a> CDaoRecordset:: getlastmodifiedbookmark

Rufen Sie diese Member-Funktion auf, um das Lesezeichen des zuletzt hinzugefügten oder aktualisierten Datensatzes abzurufen.

```cpp
COleVariant GetLastModifiedBookmark();
```

### <a name="return-value"></a>Rückgabewert

Ein `COleVariant` , der ein Lesezeichen enthält, das den zuletzt hinzugefügten oder geänderten Datensatz angibt.

### <a name="remarks"></a>Bemerkungen

Wenn ein Recordset-Objekt erstellt oder geöffnet wird, verfügt jeder seiner Datensätze bereits über ein eindeutiges Lesezeichen, wenn es diese unterstützt. [GetBookmark](#getbookmark) aufrufen, um zu bestimmen, ob das Recordset Lesezeichen unterstützt. Wenn das Recordset keine Lesezeichen unterstützt, `CDaoException` wird eine ausgelöst.

Wenn Sie einen Datensatz hinzufügen, wird er am Ende des Recordsets angezeigt, und ist nicht der aktuelle Datensatz. Um den neuen Datensatz zu erstellen, führen Sie aus, `GetLastModifiedBookmark` und geben Sie dann an, um `SetBookmark` zum neu hinzugefügten Datensatz zurückzukehren.

Weitere Informationen finden Sie im Thema "LastModified-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetgetlockingmode"></a><a name="getlockingmode"></a> CDaoRecordset:: getlockingmode

Mit dieser Member-Funktion können Sie den Typ der Sperre ermitteln, die für das Recordset wirksam ist.

```cpp
BOOL GetLockingMode();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Sperrentyp pessimistisch ist, andernfalls 0 für die vollständige Sperrung von Datensätzen.

### <a name="remarks"></a>Bemerkungen

Wenn die pessimistische Sperrung wirksam ist, wird die Datenseite mit dem zu bearbeitenden Datensatz gesperrt, sobald Sie die [Edit](#edit) Member-Funktion aufgerufen haben. Die Seite wird entsperrt, wenn Sie die Funktion " [Update](#update) " oder " [Close](#close) Member" oder einen der Verschiebungs-oder Suchvorgänge aufzurufen.

Wenn die optimistische Sperre wirksam ist, wird die Datenseite, die den Datensatz enthält, nur gesperrt, während der Datensatz mit der Member-Funktion aktualisiert wird `Update` .

Beim Arbeiten mit ODBC-Datenquellen ist der Sperrmodus immer vollständig.

Weitere Informationen finden Sie in den Themen "LockEdits-Eigenschaft" und "Sperr Verhalten in mehr Benutzer Anwendungen" in der DAO-Hilfe.

## <a name="cdaorecordsetgetname"></a><a name="getname"></a> CDaoRecordset:: GetName

Rufen Sie diese Member-Funktion auf, um den Namen des Recordsets abzurufen.

```cpp
CString GetName();
```

### <a name="return-value"></a>Rückgabewert

Ein-Wert, `CString` der den Namen des Recordsets enthält.

### <a name="remarks"></a>Bemerkungen

Der Name des Recordsets muss mit einem Buchstaben beginnen und darf maximal 40 Zeichen enthalten. Sie kann Zahlen und Unterstriche enthalten, darf jedoch keine Interpunktions Zeichen oder Leerzeichen enthalten.

Weitere Informationen finden Sie im Thema "Name Property" in der DAO-Hilfe.

## <a name="cdaorecordsetgetparamvalue"></a><a name="getparamvalue"></a> CDaoRecordset:: GetParamValue

Rufen Sie diese Member-Funktion auf, um den aktuellen Wert des angegebenen Parameters abzurufen, der im zugrunde liegenden daoparameter-Objekt gespeichert ist.

```cpp
virtual COleVariant GetParamValue(int nIndex);
virtual COleVariant GetParamValue(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Die numerische Position des Parameters im zugrunde liegenden daoparameter-Objekt.

*lpszname*<br/>
Der Name des Parameters, dessen Wert Sie möchten.

### <a name="return-value"></a>Rückgabewert

Ein Objekt der Klasse [COleVariant](../../mfc/reference/colevariant-class.md) , das den Wert des Parameters enthält.

### <a name="remarks"></a>Bemerkungen

Sie können auf den Parameter entweder über den Namen oder seine numerische Position in der Auflistung zugreifen.

Weitere Informationen finden Sie im Thema "Parameter Objekt" in der DAO-Hilfe.

## <a name="cdaorecordsetgetpercentposition"></a><a name="getpercentposition"></a> CDaoRecordset:: getprozentuposition

Wenn Sie bei der Arbeit mit einem Recordset vom Typ "Dynaset-Typ" oder "Snapshot-Type" aufrufen, `GetPercentPosition` bevor Sie das Recordset vollständig auffüllen, ist die Verschiebung relativ zur Anzahl der Datensätze, auf die wie durch Aufrufen von " [GetRecordCount](#getrecordcount)" zugegriffen wird.

```cpp
float GetPercentPosition();
```

### <a name="return-value"></a>Rückgabewert

Eine Zahl zwischen 0 und 100, die den ungefähren Speicherort des aktuellen Datensatzes im Recordset-Objekt basierend auf einem Prozentsatz der Datensätze im Recordset angibt.

### <a name="remarks"></a>Bemerkungen

Sie können zum letzten Datensatz wechseln, indem Sie [MoveLast](#movelast) aufrufen, um die Auffüllung aller Recordsets abzuschließen. Dies kann jedoch eine beträchtliche Zeit in Anspruch nehmen.

Sie können `GetPercentPosition` für alle drei Typen von recordsetobjekten (einschließlich Tabellen ohne Indizes) aufzurufen. Es ist jedoch nicht möglich, `GetPercentPosition` für vorwärts scrollmomentaufnahmen oder für ein Recordset, das aus einer Pass-Through-Abfrage für eine externe Datenbank geöffnet wurde, aufzurufen. Wenn kein aktueller Datensatz vorhanden ist oder der aktuelle Datensatz gelöscht wurde, wird eine ausgelöst `CDaoException` .

Weitere Informationen finden Sie im Thema "prozentualpositions Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetgetrecordcount"></a><a name="getrecordcount"></a> CDaoRecordset:: GetRecordCount

Mit dieser Member-Funktion können Sie feststellen, wie viele Datensätze in einem Recordset aufgerufen wurden.

```cpp
long GetRecordCount();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Datensätze zurück, auf die in einem Recordsetobjekt zugegriffen wird.

### <a name="remarks"></a>Bemerkungen

`GetRecordCount` gibt nicht an, wie viele Datensätze in einem Recordset vom Typ "Dynaset-Type" oder "Snapshot-Type" enthalten sind, bis auf alle Datensätze zugegriffen wurde. Dieser Member-Funktionsaufruf kann eine beträchtliche Zeit in Anspruch nehmen.

Nachdem auf den letzten Datensatz zugegriffen wurde, gibt der Rückgabewert die Gesamtzahl der nicht gelöschten Datensätze im Recordset an. Um den Zugriff auf den letzten Datensatz zu erzwingen, müssen Sie die- `MoveLast` oder- `FindLast` Member-Funktion für das Recordset aufrufen. Sie können auch eine SQL-Anzahl verwenden, um die ungefähre Anzahl von Datensätzen zu bestimmen, die von der Abfrage zurückgegeben werden.

Wenn Ihre Anwendung Datensätze in einem Recordset vom Typ Dynaset löscht, sinkt der Rückgabewert von `GetRecordCount` . Datensätze, die von anderen Benutzern gelöscht werden, werden jedoch nicht durch reflektiert, `GetRecordCount` bis der aktuelle Datensatz in einem gelöschten Datensatz positioniert ist. Wenn Sie eine Transaktion ausführen, die sich auf die Anzahl der Datensätze auswirkt, und anschließend ein Rollback der Transaktion ausführen, `GetRecordCount` spiegelt nicht die tatsächliche Anzahl der verbleibenden Datensätze wider

Der Wert von `GetRecordCount` aus einem Recordset vom Typ "Snapshot" wird von Änderungen in den zugrunde liegenden Tabellen nicht beeinflusst.

Der Wert von `GetRecordCount` aus einem Recordset des Tabellentyps gibt die ungefähre Anzahl von Datensätzen in der Tabelle wieder und wird sofort beeinträchtigt, wenn Tabellendaten Sätze hinzugefügt und gelöscht werden.

Ein Recordset ohne Datensätze gibt den Wert 0 (null) zurück. Beim Arbeiten mit angefügten Tabellen oder ODBC-Datenbanken `GetRecordCount` gibt immer-1 zurück. Durch den Aufruf der `Requery` Member-Funktion für ein Recordset wird der Wert von genauso zurückgesetzt, `GetRecordCount` als ob die Abfrage erneut ausgeführt würde.

Weitere Informationen finden Sie im Thema "RecordCount-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetgetsql"></a><a name="getsql"></a> CDaoRecordset:: gezql

Mit dieser Member-Funktion können Sie die SQL-Anweisung abrufen, die zum Auswählen der Datensätze des Recordsets beim Öffnen verwendet wurde.

```cpp
CString GetSQL() const;
```

### <a name="return-value"></a>Rückgabewert

Eine `CString` , die die SQL-Anweisung enthält.

### <a name="remarks"></a>Bemerkungen

Dabei handelt es sich im Allgemeinen um eine SQL- **Select** -Anweisung.

Die von zurückgegebene Zeichenfolge `GetSQL` unterscheidet sich in der Regel von jeder Zeichenfolge, die Sie möglicherweise an das Recordset im *lpszSQL* -Parameter an die [Open](#open) Member-Funktion übergeben haben. Der Grund hierfür ist, dass das Recordset eine vollständige SQL-Anweisung erstellt, basierend auf dem, das Sie an `Open` den Klassen-Assistenten angegeben haben, und dem, was Sie möglicherweise in den [m_strFilter](#m_strfilter) -und [m_strSort](#m_strsort) Datenmembern angegeben haben.

> [!NOTE]
> Diese Member-Funktion nur aufrufen, nachdem aufgerufen wurde `Open` .

Weitere Informationen finden Sie im Thema "SQL-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetgettype"></a><a name="gettype"></a> CDaoRecordset:: GetType

Diese Member-Funktion wird nach dem Öffnen des Recordsets aufgerufen, um den Typ des Recordset-Objekts zu bestimmen.

```cpp
short GetType();
```

### <a name="return-value"></a>Rückgabewert

Einer der folgenden Werte, der den Typ eines Recordsets angibt:

- `dbOpenTable` Table-Type-Recordset

- `dbOpenDynaset` Dynaset-Recordset-Typ

- `dbOpenSnapshot` Snapshot-Typ Recordset

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im Thema "Type Property" in der DAO-Hilfe.

## <a name="cdaorecordsetgetvalidationrule"></a><a name="getvalidationrule"></a> CDaoRecordset:: getvalidationrule

Mit dieser Member-Funktion können Sie die Regel ermitteln, mit der Daten überprüft werden.

```cpp
CString GetValidationRule();
```

### <a name="return-value"></a>Rückgabewert

Ein- `CString` Objekt, das einen Wert enthält, der die Daten in einem Datensatz überprüft, wenn er geändert oder einer Tabelle hinzugefügt wird.

### <a name="remarks"></a>Bemerkungen

Diese Regel ist Text basiert und wird jedes Mal angewendet, wenn die zugrunde liegende Tabelle geändert wird. Wenn die Daten nicht zulässig sind, löst MFC eine Ausnahme aus. Die zurückgegebene Fehlermeldung ist der Text der ValidationText-Eigenschaft des zugrunde liegenden Feld Objekts, falls angegeben, oder der Text des Ausdrucks, der durch die ValidationRule-Eigenschaft des zugrunde liegenden Field-Objekts angegeben wird. Sie können [getvalidationtext](#getvalidationtext) aufrufen, um den Text der Fehlermeldung zu erhalten.

Beispielsweise kann ein Feld in einem Datensatz, das den Tag des Monats erfordert, über eine Validierungs Regel verfügen, z. b. "Tag zwischen 1 und 31".

Weitere Informationen finden Sie im Thema "ValidationRule Property" in der DAO-Hilfe.

## <a name="cdaorecordsetgetvalidationtext"></a><a name="getvalidationtext"></a> CDaoRecordset:: getvalidationtext

Rufen Sie diese Member-Funktion auf, um den Text der ValidationText-Eigenschaft des zugrunde liegenden Field-Objekts abzurufen.

```cpp
CString GetValidationText();
```

### <a name="return-value"></a>Rückgabewert

Ein- `CString` Objekt, das den Text der Meldung enthält, die angezeigt wird, wenn der Wert eines Felds die Validierungs Regel des zugrunde liegenden Feld Objekts nicht erfüllt.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im Thema "ValidationText Property" in der DAO-Hilfe.

## <a name="cdaorecordsetisbof"></a><a name="isbof"></a> CDaoRecordset:: IsBOF

Nennen Sie diese Member-Funktion, bevor Sie einen Bildlauf von Datensatz zu Datensatz durchführen, um zu erfahren, ob Sie vor dem ersten Datensatz des Recordsets gegangen sind.

```cpp
BOOL IsBOF() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Recordset keine Datensätze enthält oder wenn Sie vor dem ersten Datensatz einen Rollup durchgeführt haben. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie können auch `IsBOF` zusammen mit aufzurufen `IsEOF` , um zu bestimmen, ob das Recordset Datensätze enthält oder leer ist. `Open`Wenn das Recordset keine Datensätze enthält, wird unmittelbar nach dem-Befehl ein Wert ungleich `IsBOF` NULL zurückgegeben. Wenn Sie ein Recordset öffnen, das mindestens einen Datensatz enthält, ist der erste Datensatz der aktuelle Datensatz und `IsBOF` gibt 0 zurück.

Wenn es sich bei dem ersten Datensatz um den aktuellen Datensatz handelt und Sie den Befehl aufzurufen, wird von ein Wert ungleich `MovePrev` `IsBOF` 0 Wenn `IsBOF` einen Wert ungleich 0 (null) zurückgibt und Sie aufruft `MovePrev` , wird eine Ausnahme ausgelöst. Wenn `IsBOF` einen Wert ungleich 0 (null) zurückgibt, ist der aktuelle Datensatz nicht definiert, und jede Aktion, die einen aktuellen Datensatz erfordert, führt zu einer Ausnahme.

Auswirkung spezifischer Methoden auf `IsBOF` -und- `IsEOF` Einstellungen:

- Durch den Aufruf `Open*` von wird der erste Datensatz im Recordset durch Aufrufen von in den Datensatz festgelegt `MoveFirst` . Daher bewirkt das Aufrufen `Open` von für einen leeren Satz von Datensätzen, dass `IsBOF` und ungleich 0 (null) `IsEOF` zurückgeben. (In der folgenden Tabelle finden Sie das Verhalten eines Fehlers `MoveFirst` oder eines `MoveLast` Aufrufes.)

- Alle Verschiebe Vorgänge, die einen Datensatz erfolgreich finden, bewirken, dass sowohl `IsBOF` als auch `IsEOF` 0 zurückgegeben werden.

- Ein- `AddNew` Rückruf, gefolgt von einem-Befehl `Update` , der einen neuen Datensatz erfolgreich einfügt, bewirkt, dass `IsBOF` 0 zurückgibt, jedoch nur, wenn `IsEOF` bereits ungleich NULL ist. Der Status von `IsEOF` bleibt immer unverändert. Gemäß der Definition durch die Microsoft Jet-Datenbank-Engine befindet sich der aktuelle Daten Satz Zeiger eines leeren Recordsets am Ende einer Datei, sodass ein neuer Datensatz nach dem aktuellen Datensatz eingefügt wird.

- Alle `Delete` Aufrufe, auch wenn der einzige verbleibende Datensatz aus einem Recordset entfernt wird, wird der Wert von oder nicht geändert `IsBOF` `IsEOF` .

Diese Tabelle zeigt, welche Verschiebe Vorgänge mit unterschiedlichen Kombinationen von zulässig sind `IsBOF` /  `IsEOF` .

|State|"Muvefirst", "muvelast"|MovePrev<br /><br /> < 0 verschieben|0 verschieben|MoveNext<br /><br /> > 0 verschieben|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`= ungleich 0 (null),<br /><br /> `IsEOF`=0|Zulässig|Ausnahme|Ausnahme|Zulässig|
|`IsBOF`=0,<br /><br /> `IsEOF`= ungleich NULL|Zulässig|Zulässig|Ausnahme|Ausnahme|
|Beide Werte ungleich NULL|Ausnahme|Ausnahme|Ausnahme|Ausnahme|
|Beide 0|Zulässig|Zulässig|Zulässig|Zulässig|

Das zulassen eines Verschiebungs Vorgangs bedeutet nicht, dass der Vorgang einen Datensatz erfolgreich findet. Sie gibt lediglich an, dass ein Versuch, den angegebenen Verschiebungs Vorgang auszuführen, zulässig ist und keine Ausnahme generiert. Der Wert der `IsBOF` -und- `IsEOF` Member-Funktionen kann sich aufgrund des versuchten Verschiebens ändern.

In der folgenden Tabelle sind die Auswirkungen von Verschiebungs Vorgängen, die keinen Datensatz für den Wert von `IsBOF` und Einstellungen finden, `IsEOF` in der folgenden Tabelle aufgeführt.

|Operationen (Operations)|IsBOF|IsEOF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|Ungleich NULL|Ungleich NULL|
|`Move` 0|Keine Änderung|Keine Änderung|
|`MovePrev`, `Move` < 0|Ungleich NULL|Keine Änderung|
|`MoveNext`, `Move` > 0|Keine Änderung|Ungleich NULL|

Weitere Informationen finden Sie im Thema "BOF-EOF-Eigenschaften" in der DAO-Hilfe.

## <a name="cdaorecordsetisdeleted"></a><a name="isdeleted"></a> CDaoRecordset:: isDeleted

Mit dieser Member-Funktion können Sie ermitteln, ob der aktuelle Datensatz gelöscht wurde.

```cpp
BOOL IsDeleted() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Recordset auf einem gelöschten Datensatz positioniert ist. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn Sie einen Bildlauf zu einem Datensatz `IsDeleted` ausführen und true (nicht null) zurückgeben, müssen Sie einen Bildlauf zu einem anderen Datensatz ausführen, bevor Sie andere recordsetvorgänge ausführen können.

> [!NOTE]
> Sie müssen den gelöschten Status für Datensätze in einer Momentaufnahme oder einem Recordset vom Typ "Table" nicht überprüfen. Da Datensätze nicht aus einer Momentaufnahme gelöscht werden können, muss nicht aufgerufen werden `IsDeleted` . Bei Tabellentypen-Recordsets werden gelöschte Datensätze tatsächlich aus dem Recordset entfernt. Nachdem ein Datensatz gelöscht wurde (entweder von Ihnen, einem anderen Benutzer oder einem anderen Recordset), können Sie nicht zurück zu diesem Datensatz scrollen. Daher muss nicht aufgerufen werden `IsDeleted` .

Wenn Sie einen Datensatz aus einem Dynaset löschen, wird er aus dem Recordset entfernt, und Sie können keinen Bildlauf zurück zu diesem Datensatz durchführen. Wenn ein Datensatz in einem Dynaset jedoch entweder von einem anderen Benutzer oder in einem anderen Recordset, das auf derselben Tabelle basiert, gelöscht wird, `IsDeleted` wird bei einem späteren Bildlauf zu diesem Datensatz true zurückgegeben.

Weitere Informationen finden Sie in den Themen "Delete Method", "LastModified Property" und "EditMode Property" in der DAO-Hilfe.

## <a name="cdaorecordsetiseof"></a><a name="iseof"></a> CDaoRecordset:: IsEOF

Nennen Sie diese Member-Funktion, während Sie einen Bildlauf von Datensatz zu Datensatz durchführen, um zu erfahren, ob Sie den letzten Datensatz des Recordsets überschritten haben.

```cpp
BOOL IsEOF() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Recordset keine Datensätze enthält oder wenn Sie einen Rollup über den letzten Datensatz ausgeführt haben. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie können auch aufzurufen `IsEOF` , um zu bestimmen, ob das Recordset Datensätze enthält oder leer ist. `Open`Wenn das Recordset keine Datensätze enthält, wird unmittelbar nach dem-Befehl ein Wert ungleich `IsEOF` NULL zurückgegeben. Wenn Sie ein Recordset öffnen, das mindestens einen Datensatz enthält, ist der erste Datensatz der aktuelle Datensatz und `IsEOF` gibt 0 zurück.

Wenn der letzte Datensatz der aktuelle Datensatz ist, wenn aufgerufen wird, gibt den Wert ungleich `MoveNext` `IsEOF` 0 (null) zurück. Wenn `IsEOF` einen Wert ungleich 0 (null) zurückgibt und Sie aufruft `MoveNext` , wird eine Ausnahme ausgelöst. Wenn `IsEOF` einen Wert ungleich 0 (null) zurückgibt, ist der aktuelle Datensatz nicht definiert, und jede Aktion, die einen aktuellen Datensatz erfordert, führt zu einer Ausnahme.

Auswirkung spezifischer Methoden auf `IsBOF` -und- `IsEOF` Einstellungen:

- Durch den Aufruf `Open` von wird der erste Datensatz im Recordset durch Aufrufen von in den Datensatz festgelegt `MoveFirst` . Daher bewirkt das Aufrufen `Open` von für einen leeren Satz von Datensätzen, dass `IsBOF` und ungleich 0 (null) `IsEOF` zurückgeben. (In der folgenden Tabelle finden Sie das Verhalten eines fehlgeschlagenen `MoveFirst` Aufrufes.)

- Alle Verschiebe Vorgänge, die einen Datensatz erfolgreich finden, bewirken, dass sowohl `IsBOF` als auch `IsEOF` 0 zurückgegeben werden.

- Ein- `AddNew` Rückruf, gefolgt von einem-Befehl `Update` , der einen neuen Datensatz erfolgreich einfügt, bewirkt, dass `IsBOF` 0 zurückgibt, jedoch nur, wenn `IsEOF` bereits ungleich NULL ist. Der Status von `IsEOF` bleibt immer unverändert. Gemäß der Definition durch die Microsoft Jet-Datenbank-Engine befindet sich der aktuelle Daten Satz Zeiger eines leeren Recordsets am Ende einer Datei, sodass ein neuer Datensatz nach dem aktuellen Datensatz eingefügt wird.

- Alle `Delete` Aufrufe, auch wenn der einzige verbleibende Datensatz aus einem Recordset entfernt wird, wird der Wert von oder nicht geändert `IsBOF` `IsEOF` .

Diese Tabelle zeigt, welche Verschiebe Vorgänge mit unterschiedlichen Kombinationen von zulässig sind `IsBOF` /  `IsEOF` .

|State|"Muvefirst", "muvelast"|MovePrev<br /><br /> < 0 verschieben|0 verschieben|MoveNext<br /><br /> > 0 verschieben|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`= ungleich 0 (null),<br /><br /> `IsEOF`=0|Zulässig|Ausnahme|Ausnahme|Zulässig|
|`IsBOF`=0,<br /><br /> `IsEOF`= ungleich NULL|Zulässig|Zulässig|Ausnahme|Ausnahme|
|Beide Werte ungleich NULL|Ausnahme|Ausnahme|Ausnahme|Ausnahme|
|Beide 0|Zulässig|Zulässig|Zulässig|Zulässig|

Das zulassen eines Verschiebungs Vorgangs bedeutet nicht, dass der Vorgang einen Datensatz erfolgreich findet. Sie gibt lediglich an, dass ein Versuch, den angegebenen Verschiebungs Vorgang auszuführen, zulässig ist und keine Ausnahme generiert. Der Wert der `IsBOF` -und- `IsEOF` Member-Funktionen kann sich aufgrund des versuchten Verschiebens ändern.

In der folgenden Tabelle sind die Auswirkungen von Verschiebungs Vorgängen, die keinen Datensatz für den Wert von `IsBOF` und Einstellungen finden, `IsEOF` in der folgenden Tabelle aufgeführt.

|Operationen (Operations)|IsBOF|IsEOF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|Ungleich NULL|Ungleich NULL|
|`Move` 0|Keine Änderung|Keine Änderung|
|`MovePrev`, `Move` < 0|Ungleich NULL|Keine Änderung|
|`MoveNext`, `Move` > 0|Keine Änderung|Ungleich NULL|

Weitere Informationen finden Sie im Thema "BOF-EOF-Eigenschaften" in der DAO-Hilfe.

## <a name="cdaorecordsetisfielddirty"></a><a name="isfielddirty"></a> CDaoRecordset:: IsFieldDirty

Mit dieser Member-Funktion können Sie ermitteln, ob der angegebene Felddatenmember eines Dynaset als "Dirty" (geändert) gekennzeichnet wurde.

```cpp
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>Parameter

*teuren*<br/>
Ein Zeiger auf den Felddatenmember, dessen Status Sie überprüfen möchten, oder NULL, um zu bestimmen, ob eines der Felder geändert wird.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn der angegebene Felddatenmember als geändert gekennzeichnet ist. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Daten in allen modifizierten Felddatenmembern werden an den Datensatz in der Datenquelle übertragen, wenn der aktuelle Datensatz durch einen Rückruf der- `Update` Member-Funktion von `CDaoRecordset` (nach einem-oder-Aufrufe) aktualisiert wird `Edit` `AddNew` . Mit diesem Wissen können Sie weitere Schritte ausführen, z. b. das Kennzeichnen des Felddatenmembers, um die Spalte zu markieren, sodass Sie nicht in die Datenquelle geschrieben wird.

`IsFieldDirty` wird durch implementiert `DoFieldExchange` .

## <a name="cdaorecordsetisfieldnull"></a><a name="isfieldnull"></a> CDaoRecordset:: IsFieldNull

Mit dieser Member-Funktion können Sie ermitteln, ob der angegebene Felddatenmember eines Recordsets als NULL gekennzeichnet wurde.

```cpp
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>Parameter

*teuren*<br/>
Ein Zeiger auf den Felddatenmember, dessen Status Sie überprüfen möchten, oder NULL, um zu bestimmen, ob eines der Felder NULL ist.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn der angegebene Felddatenmember als NULL gekennzeichnet ist. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

(In der Daten Bank Terminologie bedeutet NULL, dass kein Wert vorhanden ist, und ist nicht mit NULL in C++ identisch.) Wenn ein Felddatenmember als NULL gekennzeichnet ist, wird er als Spalte des aktuellen Datensatzes interpretiert, für den kein Wert vorhanden ist.

> [!NOTE]
> In bestimmten Situationen `IsFieldNull` kann die Verwendung von ineffizient sein, wie im folgenden Codebeispiel veranschaulicht:

[!code-cpp[NVC_MFCDatabase#5](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]

> [!NOTE]
> Wenn Sie die dynamische Daten Satz Bindung ohne Ableitung von verwenden, `CDaoRecordset` Stellen Sie sicher, dass Sie VT_NULL wie im Beispiel gezeigt verwenden.

## <a name="cdaorecordsetisfieldnullable"></a><a name="isfieldnullable"></a> CDaoRecordset:: IsFieldNullable

Mit dieser Member-Funktion wird bestimmt, ob der angegebene Felddatenmember "Nullable" ist (kann auf einen NULL-Wert festgelegt werden; C++ NULL ist nicht identisch mit NULL, was in der Daten Bank Terminologie bedeutet, dass kein Wert vorhanden ist.)

```cpp
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>Parameter

*teuren*<br/>
Ein Zeiger auf den Felddatenmember, dessen Status Sie überprüfen möchten, oder NULL, um zu bestimmen, ob eines der Felder NULL ist.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der angegebene Felddatenmember NULL gemacht werden kann. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Ein Feld, das nicht NULL sein kann, muss über einen Wert verfügen. Wenn Sie versuchen, ein solches Feld beim Hinzufügen oder Aktualisieren eines Datensatzes auf NULL festzulegen, lehnt die Datenquelle das Hinzufügen oder aktualisieren ab und löst `Update` eine Ausnahme aus. Die Ausnahme tritt auf, wenn aufgerufen `Update` wird, und nicht, wenn aufgerufen wird `SetFieldNull` .

## <a name="cdaorecordsetisopen"></a><a name="isopen"></a> CDaoRecordset:: IsOpen

Mit dieser Member-Funktion können Sie ermitteln, ob das Recordset geöffnet ist.

```cpp
BOOL IsOpen() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn die-oder-Member-Funktion des Recordset-Objekts `Open` `Requery` zuvor aufgerufen wurde und das Recordset nicht geschlossen wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

## <a name="cdaorecordsetm_bcheckcachefordirtyfields"></a><a name="m_bcheckcachefordirtyfields"></a> CDaoRecordset:: m_bCheckCacheForDirtyFields

Enthält ein Flag, das angibt, ob zwischengespeicherte Felder automatisch als geändert (geändert) und NULL markiert werden.

### <a name="remarks"></a>Bemerkungen

Das Flag ist standardmäßig auf true eingestellt. Die-Einstellung in diesem Datenmember steuert den gesamten Double-bufferingmechanismus. Wenn Sie das-Flag auf "true" festlegen, können Sie das Zwischenspeichern für eine Feld Weise mithilfe des DFX-Mechanismus deaktivieren. Wenn Sie das Flag auf false festlegen, müssen Sie `SetFieldDirty` und `SetFieldNull` selbst anrufen.

Legen Sie diesen Datenmember vor dem Aufrufen von fest `Open` . Dieser Mechanismus ist hauptsächlich für die Benutzerfreundlichkeit zu verwenden. Die Leistung kann aufgrund der doppelten Pufferung von Feldern aufgrund von Änderungen verlangsamt werden.

## <a name="cdaorecordsetm_nfields"></a><a name="m_nfields"></a> CDaoRecordset:: m_nFields

Enthält die Anzahl der Felddatenmember in der Recordset-Klasse und die Anzahl der Spalten, die vom Recordset aus der Datenquelle ausgewählt werden.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor für die Recordset-Klasse muss `m_nFields` mit der richtigen Anzahl von statisch gebundenen Feldern initialisiert werden. Der Klassen-Assistent schreibt diese Initialisierung für Sie, wenn Sie ihn zum Deklarieren der Recordsetklasse verwenden. Sie können Sie auch manuell schreiben.

Das Framework verwendet diese Zahl, um die Interaktion zwischen den Felddatenmembern und den entsprechenden Spalten des aktuellen Datensatzes in der Datenquelle zu verwalten.

> [!NOTE]
> Diese Zahl muss der Anzahl der in registrierten Ausgabespalten entsprechen, `DoFieldExchange` nachdem `SetFieldType` mit dem-Parameter aufgerufen wurde `CDaoFieldExchange::outputColumn` .

Spalten können mithilfe von und dynamisch gebunden werden `CDaoRecordset::GetFieldValue` `CDaoRecordset::SetFieldValue` . Wenn Sie dies tun, müssen Sie die Anzahl in nicht erhöhen, `m_nFields` um die Anzahl von DFX-Funktionsaufrufen in der Member-Funktion widerzuspiegeln `DoFieldExchange` .

## <a name="cdaorecordsetm_nparams"></a><a name="m_nparams"></a> CDaoRecordset:: m_nParams

Enthält die Anzahl der Parameterdatenmember in der Recordset-Klasse – die Anzahl von Parametern, die mit der Abfrage des Recordsets übergeben werden.

### <a name="remarks"></a>Bemerkungen

Wenn die Recordsetklasse über Parameter Datenmember verfügt, muss der Konstruktor für die Klasse *m_nParams* mit der richtigen Anzahl initialisieren. Der Wert von *m_nParams* der Standardwert 0 ist. Wenn Sie Parameterdaten Elemente hinzufügen – was Sie manuell tun müssen – müssen Sie auch manuell eine Initialisierung im Klassenkonstruktor hinzufügen, um die Anzahl der Parameter (die mindestens so groß wie die Anzahl der Platzhalter in der *m_strFilter* oder *m_strSort* Zeichenfolge sein muss) wiederzugeben.

Das Framework verwendet diese Zahl, wenn die Abfrage des Recordsets parametrisiert wird.

> [!NOTE]
> Diese Zahl muss der Anzahl von "Parametern" entsprechen, die in `DoFieldExchange` nach einem Aufrufen von `SetFieldType` mit dem-Parameter registriert ist `CFieldExchange::param` .

Weitere Informationen finden Sie im Thema "Parameter Objekt" in der DAO-Hilfe.

## <a name="cdaorecordsetm_pdaorecordset"></a><a name="m_pdaorecordset"></a> CDaoRecordset:: m_pDAORecordset

Enthält einen Zeiger auf die OLE-Schnittstelle für das DAO-Recordsetobjekt, das dem-Objekt zugrunde liegt `CDaoRecordset` .

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diesen Zeiger, wenn Sie direkt auf die DAO-Schnittstelle zugreifen müssen.

Weitere Informationen finden Sie im Thema "Recordset-Objekt" in der DAO-Hilfe.

## <a name="cdaorecordsetm_pdatabase"></a><a name="m_pdatabase"></a> CDaoRecordset:: m_pDatabase

Enthält einen Zeiger auf das- `CDaoDatabase` Objekt, über das das Recordset mit einer Datenquelle verbunden ist.

### <a name="remarks"></a>Bemerkungen

Diese Variable wird auf zwei Arten festgelegt. In der Regel übergeben Sie einen Zeiger an ein bereits geöffnetes `CDaoDatabase` Objekt, wenn Sie das Recordset-Objekt erstellen. Wenn Sie stattdessen NULL übergeben, wird `CDaoRecordset` `CDaoDatabase` von ein-Objekt für Sie erstellt und geöffnet. In beiden Fällen `CDaoRecordset` speichert den Zeiger in dieser Variablen.

Normalerweise müssen Sie den in gespeicherten Zeiger nicht direkt verwenden `m_pDatabase` . Wenn Sie jedoch eigene Erweiterungen in schreiben, `CDaoRecordset` müssen Sie möglicherweise den-Zeiger verwenden. Beispielsweise können Sie den-Zeiger benötigen, wenn Sie Ihre eigenen `CDaoException` (e) verwerfen.

Weitere Informationen finden Sie im Thema "Datenbankobjekt" in der DAO-Hilfe.

## <a name="cdaorecordsetm_strfilter"></a><a name="m_strfilter"></a> CDaoRecordset:: m_strFilter

Enthält eine Zeichenfolge, die zum Erstellen der **Where** -Klausel einer SQL-Anweisung verwendet wird.

### <a name="remarks"></a>Bemerkungen

Es enthält nicht das reservierte Wort, **in** dem das Recordset gefiltert werden soll. Die Verwendung dieses Datenmembers ist für Recordsets des Tabellentyps nicht anwendbar. Die Verwendung von `m_strFilter` hat keine Auswirkung, wenn ein Recordset mit einem `CDaoQueryDef` Zeiger geöffnet wird.

Verwenden Sie das US-Datumsformat (month-day-year), wenn Sie Felder mit Datumsangaben filtern, auch wenn Sie nicht die US-Version der Microsoft Jet-Datenbank-Engine verwenden. Andernfalls werden die Daten möglicherweise nicht wie erwartet gefiltert.

Weitere Informationen finden Sie im Thema "Filter Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetm_strsort"></a><a name="m_strsort"></a> CDaoRecordset:: m_strSort

Enthält eine Zeichenfolge, die die **OrderBy** -Klausel einer SQL-Anweisung ohne die reservierten Wörter **OrderBy**enthält.

### <a name="remarks"></a>Bemerkungen

Sie können nach Dynaset-und Snapshot-Type-recordsetobjekten sortieren.

Es ist nicht möglich, Recordset-Objekte des Tabellentyps zu sortieren. Um die Sortierreihenfolge eines Tabellentyp-Recordsets zu bestimmen, müssen Sie [SetCurrentIndex](#setcurrentindex)aufrufen.

Die Verwendung von *m_strSort* hat keine Auswirkung, wenn ein Recordset mithilfe eines `CDaoQueryDef` Zeigers geöffnet wird.

Weitere Informationen finden Sie im Thema "Sort property" in der DAO-Hilfe.

## <a name="cdaorecordsetmove"></a><a name="move"></a> CDaoRecordset:: Move

Diese Member-Funktion zum Positionieren der Recordset *lrows* -Datensätze aus dem aktuellen Datensatz aufzurufen.

```cpp
virtual void Move(long lRows);
```

### <a name="parameters"></a>Parameter

*lrows*<br/>
Die Anzahl der Datensätze, die vorwärts oder rückwärts verschoben werden sollen. Positive Werte werden vorwärts bis zum Ende des Recordsets verschoben. Negative Werte werden nach hinten verschoben.

### <a name="remarks"></a>Bemerkungen

Sie können vorwärts oder rückwärts wechseln. `Move( 1 )` entspricht `MoveNext` , und `Move( -1 )` entspricht `MovePrev` .

> [!CAUTION]
> Wenn Sie eine der `Move` Funktionen aufrufen, wird eine Ausnahme ausgelöst, wenn das Recordset keine Datensätze enthält. Im Allgemeinen werden sowohl `IsBOF` als auch `IsEOF` vor einem Verschiebungs Vorgang aufgerufen, um zu bestimmen, ob das Recordset über Datensätze verfügt. Nachdem Sie `Open` oder aufgerufen `Requery` haben, muss entweder oder aufgerufen werden `IsBOF` `IsEOF` .

> [!NOTE]
> Wenn Sie einen Rollup über den Anfang oder das Ende des Recordsets durchgeführt haben ( `IsBOF` oder einen Wert ungleich `IsEOF` 0 zurückgegeben haben), löst ein-Befehl eine aus `Move` `CDaoException` .

> [!NOTE]
> Wenn Sie eine der Funktionen aufzurufen `Move` , während der aktuelle Datensatz aktualisiert oder hinzugefügt wird, gehen die Aktualisierungen ohne Warnung verloren.

Wenn Sie `Move` für eine Momentaufnahme mit vorwärts Scrollen aufrufen, muss der *lrows* -Parameter eine positive Ganzzahl sein, und Lesezeichen sind nicht zulässig, sodass Sie nur vorwärts verschieben können.

Um den ersten, letzten, nächsten oder vorherigen Datensatz in einem Recordset des aktuellen Datensatzes festzulegen, geben Sie die-,-,- `MoveFirst` `MoveLast` oder-Member-Funktion an `MoveNext` `MovePrev` .

Weitere Informationen finden Sie in den Themen "Move Method" und "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" in der DAO-Hilfe.

## <a name="cdaorecordsetmovefirst"></a><a name="movefirst"></a> CDaoRecordset:: vfirst

Mit dieser Member-Funktion können Sie den ersten Datensatz im Recordset (sofern vorhanden) mit dem aktuellen Datensatz erstellen.

```cpp
void MoveFirst();
```

### <a name="remarks"></a>Bemerkungen

Sie müssen nicht `MoveFirst` sofort nach dem Öffnen des Recordsets aufzurufen. Zu diesem Zeitpunkt ist der erste Datensatz (sofern vorhanden) automatisch der aktuelle Datensatz.

> [!CAUTION]
> Wenn Sie eine der `Move` Funktionen aufrufen, wird eine Ausnahme ausgelöst, wenn das Recordset keine Datensätze enthält. Im Allgemeinen werden sowohl `IsBOF` als auch `IsEOF` vor einem Verschiebungs Vorgang aufgerufen, um zu bestimmen, ob das Recordset über Datensätze verfügt. Nachdem Sie `Open` oder aufgerufen `Requery` haben, muss entweder oder aufgerufen werden `IsBOF` `IsEOF` .

> [!NOTE]
> Wenn Sie eine der Funktionen aufzurufen `Move` , während der aktuelle Datensatz aktualisiert oder hinzugefügt wird, gehen die Aktualisierungen ohne Warnung verloren.

Verwenden Sie die- `Move` Funktionen, um von Datensatz zu Datensatz zu wechseln, ohne eine Bedingung anzuwenden. Verwenden Sie die Suchvorgänge, um Datensätze in einem Objekt vom Typ "Dynaset-Type" oder "Snapshot-Type" zu suchen, die eine bestimmte Bedingung erfüllen. Zum Suchen eines Datensatzes in einem Recordset-Objekt vom Typ "Table" wird aufgerufen `Seek` .

Wenn sich das Recordset auf einen Tabellentyp-Recordset bezieht, folgt die Bewegung dem aktuellen Index der Tabelle. Sie können den aktuellen Index festlegen, indem Sie die Index-Eigenschaft des zugrunde liegenden DAO-Objekts verwenden. Wenn Sie den aktuellen Index nicht festlegen, ist die Reihenfolge der zurückgegebenen Datensätze nicht definiert.

Wenn Sie `MoveLast` für ein Recordset-Objekt basierend auf einer SQL-Abfrage oder QueryDef aufzurufen, wird die Abfrage erzwungen, und das Recordset-Objekt wird vollständig aufgefüllt.

Sie können die- `MoveFirst` oder `MovePrev` -Member-Funktion nicht mit einer vorwärts Bild Lauf Momentaufnahme aufzurufen.

Um die Position des aktuellen Datensatzes in einem Recordset-Objekt mit einer bestimmten Anzahl von Datensätzen vorwärts oder rückwärts zu verschieben, wird aufgerufen `Move` .

Weitere Informationen finden Sie in den Themen "Move Method" und "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" in der DAO-Hilfe.

## <a name="cdaorecordsetmovelast"></a><a name="movelast"></a> CDaoRecordset:: muvelast

Mit dieser Member-Funktion können Sie den letzten Datensatz (sofern vorhanden) im Recordset als aktuellen Datensatz festlegen.

```cpp
void MoveLast();
```

### <a name="remarks"></a>Bemerkungen

> [!CAUTION]
> Wenn Sie eine der `Move` Funktionen aufrufen, wird eine Ausnahme ausgelöst, wenn das Recordset keine Datensätze enthält. Im Allgemeinen werden sowohl `IsBOF` als auch `IsEOF` vor einem Verschiebungs Vorgang aufgerufen, um zu bestimmen, ob das Recordset über Datensätze verfügt. Nachdem Sie `Open` oder aufgerufen `Requery` haben, muss entweder oder aufgerufen werden `IsBOF` `IsEOF` .

> [!NOTE]
> Wenn Sie eine der Funktionen aufzurufen `Move` , während der aktuelle Datensatz aktualisiert oder hinzugefügt wird, gehen die Aktualisierungen ohne Warnung verloren.

Verwenden Sie die- `Move` Funktionen, um von Datensatz zu Datensatz zu wechseln, ohne eine Bedingung anzuwenden. Verwenden Sie die Suchvorgänge, um Datensätze in einem Objekt vom Typ "Dynaset-Type" oder "Snapshot-Type" zu suchen, die eine bestimmte Bedingung erfüllen. Zum Suchen eines Datensatzes in einem Recordset-Objekt vom Typ "Table" wird aufgerufen `Seek` .

Wenn sich das Recordset auf einen Tabellentyp-Recordset bezieht, folgt die Bewegung dem aktuellen Index der Tabelle. Sie können den aktuellen Index festlegen, indem Sie die Index-Eigenschaft des zugrunde liegenden DAO-Objekts verwenden. Wenn Sie den aktuellen Index nicht festlegen, ist die Reihenfolge der zurückgegebenen Datensätze nicht definiert.

Wenn Sie `MoveLast` für ein Recordset-Objekt basierend auf einer SQL-Abfrage oder QueryDef aufzurufen, wird die Abfrage erzwungen, und das Recordset-Objekt wird vollständig aufgefüllt.

Um die Position des aktuellen Datensatzes in einem Recordset-Objekt mit einer bestimmten Anzahl von Datensätzen vorwärts oder rückwärts zu verschieben, wird aufgerufen `Move` .

Weitere Informationen finden Sie in den Themen "Move Method" und "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" in der DAO-Hilfe.

## <a name="cdaorecordsetmovenext"></a><a name="movenext"></a> CDaoRecordset:: wvenext

Diese Member-Funktion wird aufgerufen, um den nächsten Datensatz im Recordset zum aktuellen Datensatz zu machen.

```cpp
void MoveNext();
```

### <a name="remarks"></a>Bemerkungen

Es wird empfohlen, dass Sie anrufen, `IsBOF` bevor Sie versuchen, zum vorherigen Datensatz zu wechseln. Ein-Aufrufe `MovePrev` von löst einen aus, wenn einen Wert ungleich `CDaoException` 0 (null) `IsBOF` zurückgibt, der angibt, dass Sie bereits vor dem ersten Datensatz einen Rollup ausgeführt haben oder keine Datensätze vom Recordset ausgewählt wurden.

> [!CAUTION]
> Wenn Sie eine der `Move` Funktionen aufrufen, wird eine Ausnahme ausgelöst, wenn das Recordset keine Datensätze enthält. Im Allgemeinen werden sowohl `IsBOF` als auch `IsEOF` vor einem Verschiebungs Vorgang aufgerufen, um zu bestimmen, ob das Recordset über Datensätze verfügt. Nachdem Sie `Open` oder aufgerufen `Requery` haben, muss entweder oder aufgerufen werden `IsBOF` `IsEOF` .

> [!NOTE]
> Wenn Sie eine der Funktionen aufzurufen `Move` , während der aktuelle Datensatz aktualisiert oder hinzugefügt wird, gehen die Aktualisierungen ohne Warnung verloren.

Verwenden Sie die- `Move` Funktionen, um von Datensatz zu Datensatz zu wechseln, ohne eine Bedingung anzuwenden. Verwenden Sie die Suchvorgänge, um Datensätze in einem Objekt vom Typ "Dynaset-Type" oder "Snapshot-Type" zu suchen, die eine bestimmte Bedingung erfüllen. Zum Suchen eines Datensatzes in einem Recordset-Objekt vom Typ "Table" wird aufgerufen `Seek` .

Wenn sich das Recordset auf einen Tabellentyp-Recordset bezieht, folgt die Bewegung dem aktuellen Index der Tabelle. Sie können den aktuellen Index festlegen, indem Sie die Index-Eigenschaft des zugrunde liegenden DAO-Objekts verwenden. Wenn Sie den aktuellen Index nicht festlegen, ist die Reihenfolge der zurückgegebenen Datensätze nicht definiert.

Um die Position des aktuellen Datensatzes in einem Recordset-Objekt mit einer bestimmten Anzahl von Datensätzen vorwärts oder rückwärts zu verschieben, wird aufgerufen `Move` .

Weitere Informationen finden Sie in den Themen "Move Method" und "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" in der DAO-Hilfe.

## <a name="cdaorecordsetmoveprev"></a><a name="moveprev"></a> CDaoRecordset:: weprev

Diese Member-Funktion wird aufgerufen, um den vorherigen Datensatz im Recordset zum aktuellen Datensatz zu machen.

```cpp
void MovePrev();
```

### <a name="remarks"></a>Bemerkungen

Es wird empfohlen, dass Sie anrufen, `IsBOF` bevor Sie versuchen, zum vorherigen Datensatz zu wechseln. Ein-Aufrufe `MovePrev` von löst einen aus, wenn einen Wert ungleich `CDaoException` 0 (null) `IsBOF` zurückgibt, der angibt, dass Sie bereits vor dem ersten Datensatz einen Rollup ausgeführt haben oder keine Datensätze vom Recordset ausgewählt wurden.

> [!CAUTION]
> Wenn Sie eine der `Move` Funktionen aufrufen, wird eine Ausnahme ausgelöst, wenn das Recordset keine Datensätze enthält. Im Allgemeinen werden sowohl `IsBOF` als auch `IsEOF` vor einem Verschiebungs Vorgang aufgerufen, um zu bestimmen, ob das Recordset über Datensätze verfügt. Nachdem Sie `Open` oder aufgerufen `Requery` haben, muss entweder oder aufgerufen werden `IsBOF` `IsEOF` .

> [!NOTE]
> Wenn Sie eine der Funktionen aufzurufen `Move` , während der aktuelle Datensatz aktualisiert oder hinzugefügt wird, gehen die Aktualisierungen ohne Warnung verloren.

Verwenden Sie die- `Move` Funktionen, um von Datensatz zu Datensatz zu wechseln, ohne eine Bedingung anzuwenden. Verwenden Sie die Suchvorgänge, um Datensätze in einem Objekt vom Typ "Dynaset-Type" oder "Snapshot-Type" zu suchen, die eine bestimmte Bedingung erfüllen. Zum Suchen eines Datensatzes in einem Recordset-Objekt vom Typ "Table" wird aufgerufen `Seek` .

Wenn sich das Recordset auf einen Tabellentyp-Recordset bezieht, folgt die Bewegung dem aktuellen Index der Tabelle. Sie können den aktuellen Index festlegen, indem Sie die Index-Eigenschaft des zugrunde liegenden DAO-Objekts verwenden. Wenn Sie den aktuellen Index nicht festlegen, ist die Reihenfolge der zurückgegebenen Datensätze nicht definiert.

Sie können die- `MoveFirst` oder `MovePrev` -Member-Funktion nicht mit einer vorwärts Bild Lauf Momentaufnahme aufzurufen.

Um die Position des aktuellen Datensatzes in einem Recordset-Objekt mit einer bestimmten Anzahl von Datensätzen vorwärts oder rückwärts zu verschieben, wird aufgerufen `Move` .

Weitere Informationen finden Sie in den Themen "Move Method" und "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" in der DAO-Hilfe.

## <a name="cdaorecordsetopen"></a><a name="open"></a> CDaoRecordset:: Open

Sie müssen diese Member-Funktion aufrufen, um die Datensätze für das Recordset abzurufen.

```cpp
virtual void Open(
    int nOpenType = AFX_DAO_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    int nOptions = 0);

virtual void Open(
    CDaoTableDef* pTableDef,
    int nOpenType = dbOpenTable,
    int nOptions = 0);

virtual void Open(
    CDaoQueryDef* pQueryDef,
    int nOpenType = dbOpenDynaset,
    int nOptions = 0);
```

### <a name="parameters"></a>Parameter

*nOpenType*<br/>
Einer der folgenden Werte:

- `dbOpenDynaset` Ein Dynaset-Recordset mit bidirektionalem Bildlauf. Dies ist die Standardoption.

- `dbOpenTable` Ein Recordset für Tabellentypen mit bidirektionalem Bildlauf.

- `dbOpenSnapshot` Ein Recordset vom Typ "Snapshot" mit bidirektionalem Bildlauf.

*lpszSQL*<br/>
Eine Zeichenfolge, in der eines der folgenden Elemente enthalten ist:

- Ein NULL-Zeiger.

- Der Name einer oder mehrerer Tabledefs und/oder Querydefs (durch Kommas getrennt).

- Eine SQL- **Select** -Anweisung (optional mit einer SQL- **Where** -Klausel oder einer **OrderBy** -Klausel).

- Eine Pass-Through-Abfrage.

*noptions*<br/>
Eine oder mehrere der unten aufgeführten Optionen. Der Standardwert ist 0. Es sind folgende Werte möglich:

- `dbAppendOnly` Sie können nur neue Datensätze anfügen (nur das Recordset "Dynaset-Type"). Diese Option bedeutet, dass Datensätze nur angehängt werden können. Die MFC-ODBC-Datenbankklassen verfügen über eine nur-Append-Option, mit der Datensätze abgerufen und angefügt werden können.

- `dbForwardOnly` Das Recordset ist eine vorwärts Bild Lauf Momentaufnahme.

- `dbSeeChanges` Generieren Sie eine Ausnahme, wenn ein anderer Benutzer die Daten ändert, die Sie bearbeiten.

- `dbDenyWrite` Andere Benutzer können Datensätze nicht ändern oder hinzufügen.

- `dbDenyRead` Andere Benutzer können keine Datensätze anzeigen (nur Tabellentyp-Recordset).

- `dbReadOnly` Sie können nur Datensätze anzeigen. andere Benutzer können diese ändern.

- `dbInconsistent` Inkonsistente Updates sind zulässig (nur das Recordset "Dynaset-Type").

- `dbConsistent` Nur konsistente Updates sind zulässig (nur das Recordset "Dynaset-Type").

> [!NOTE]
> Die Konstanten `dbConsistent` und `dbInconsistent` schließen sich gegenseitig aus. Sie können einen oder den anderen, aber nicht beides in einer bestimmten Instanz von verwenden `Open` .

*ptabledef*<br/>
Ein Zeiger auf ein [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) -Objekt. Diese Version ist nur für Recordsets von Tabellentypen gültig. Wenn Sie diese Option verwenden, `CDaoDatabase` wird der Zeiger, der zum Erstellen von verwendet wird, `CDaoRecordset` nicht verwendet. stattdessen wird die Datenbank verwendet, in der sich die Tabledef befindet.

*pquerydef*<br/>
Ein Zeiger auf ein [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) -Objekt. Diese Version ist nur für die Recordsets "Dynaset-Type" und "Snapshot-Type" gültig. Wenn Sie diese Option verwenden, `CDaoDatabase` wird der Zeiger, der zum Erstellen von verwendet wird, `CDaoRecordset` nicht verwendet. stattdessen wird die Datenbank verwendet, in der sich die QueryDef befindet.

### <a name="remarks"></a>Bemerkungen

Vor dem Aufrufen von `Open` müssen Sie das Recordset-Objekt erstellen. Dafür stehen verschiedene Möglichkeiten zur Verfügung:

- Wenn Sie das Recordset-Objekt erstellen, übergeben Sie einen Zeiger auf ein- `CDaoDatabase` Objekt, das bereits geöffnet ist.

- Wenn Sie das Recordset-Objekt erstellen, übergeben Sie einen Zeiger auf ein- `CDaoDatabase` Objekt, das nicht geöffnet ist. Das Recordset öffnet ein- `CDaoDatabase` Objekt, schließt es jedoch nicht, wenn das Recordset-Objekt geschlossen wird.

- Wenn Sie das Recordset-Objekt erstellen, übergeben Sie einen NULL-Zeiger. Das Recordset-Objekt ruft `GetDefaultDBName` auf, um den Namen von Microsoft Access zu erhalten. Die zu öffnende MDB-Datei. Das Recordset öffnet dann ein `CDaoDatabase` -Objekt und hält es geöffnet, solange das Recordset geöffnet ist. Wenn Sie `Close` für das Recordset aufzurufen, `CDaoDatabase` wird das-Objekt ebenfalls geschlossen.

    > [!NOTE]
    >  Wenn das Recordset das `CDaoDatabase` Objekt öffnet, wird die Datenquelle mit dem nicht exklusiven Zugriff geöffnet.

`Open`Wenn das Recordset geöffnet ist, können Sie für die Version von, die den *lpszSQL* -Parameter verwendet, die Datensätze auf eine von mehreren weisen abrufen. Die erste Option besteht darin, DFX-Funktionen in Ihrem zu haben `DoFieldExchange` . Die zweite Option ist die Verwendung der dynamischen Bindung durch Aufrufen der `GetFieldValue` Member-Funktion. Diese Optionen können separat oder in Kombination implementiert werden. Wenn Sie kombiniert werden, müssen Sie die SQL-Anweisung selbst an den-Befehl übergeben `Open` .

Wenn Sie die zweite Version von verwenden `Open` , an die Sie ein `CDaoTableDef` -Objekt übergeben, stehen die resultierenden Spalten für die Bindung über `DoFieldExchange` und den DFX-Mechanismus und/oder die dynamische Bindung über zur Verfügung `GetFieldValue` .

> [!NOTE]
> Sie können nur `Open` mithilfe eines- `CDaoTableDef` Objekts für Recordsets vom Typ "Table" aufgerufen werden.

Wenn Sie die dritte Version von verwenden `Open` , an die Sie ein `CDaoQueryDef` -Objekt übergeben, wird diese Abfrage ausgeführt, und die resultierenden Spalten können für die Bindung über `DoFieldExchange` und den DFX-Mechanismus und/oder die dynamische Bindung über verwendet werden `GetFieldValue` .

> [!NOTE]
> Sie können nur `Open` mithilfe eines `CDaoQueryDef` -Objekts für die Recordsets Dynaset-Type und Snapshot-Type aufgerufen werden.

Bei der ersten Version von, die `Open` den- `lpszSQL` Parameter verwendet, werden Datensätze basierend auf den in der folgenden Tabelle aufgeführten Kriterien ausgewählt.

|Der Wert des Parameters `lpszSQL`.|Die ausgewählten Datensätze werden von folgenden Aspekten bestimmt:|Beispiel|
|--------------------------------------|----------------------------------------|-------------|
|NULL|Die von `GetDefaultSQL` zurückgegebene Zeichenfolge.||
|Eine durch Trennzeichen getrennte Liste mit einem oder mehreren Tabledefs-und/oder Querydef-Namen.|Alle in dargestellten Spalten `DoFieldExchange` .|`"Customer"`|
|**Select** Column-List **from** Table-List|Die angegebenen Spalten aus den angegebenen Tabledef (s) und/oder QueryDef (s).|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|

Die übliche Vorgehensweise besteht darin, NULL an zu übergeben `Open` . in diesem Fall `Open` ruft `GetDefaultSQL` eine über schreibbare Member-Funktion auf, die von ClassWizard beim Erstellen einer von `CDaoRecordset` abgeleiteten Klasse generiert wird. Dieser Wert gibt die Tabledef (s) und/oder Querydef-Namen an, die Sie in ClassWizard angegeben haben. Sie können stattdessen Weitere Informationen im *lpszSQL* -Parameter angeben.

Wenn Sie alle übergeben, wird `Open` eine abschließende SQL-Zeichenfolge für die Abfrage erstellt (die Zeichenfolge kann SQL **Where** -und **OrderBy** -Klauseln enthalten, die an die übergebene *lpszSQL* -Zeichenfolge angehängt wurden) und anschließend die Abfrage ausführt. Sie können die erstellte Zeichenfolge durch Aufrufen von nach Aufrufen von untersuchen `GetSQL` `Open` .

Die Felddatenmember der Recordset-Klasse sind an die Spalten der ausgewählten Daten gebunden. Falls Datensätze zurückgegeben werden, wird der erste Datensatz zum aktuellen Datensatz.

Wenn Sie Optionen für das Recordset festlegen möchten, z. b. einen Filter oder eine Sortierung, legen Sie `m_strSort` oder `m_strFilter` nach dem Erstellen des Recordset-Objekts fest, aber bevor Sie aufzurufen `Open` . Wenn Sie die Datensätze im Recordset aktualisieren möchten, nachdem das Recordset bereits geöffnet ist, wird aufgerufen `Requery` .

Wenn Sie `Open` für einen Dynaset-Typ oder ein Recordset vom Typ Snapshot verwenden oder wenn sich die Datenquelle auf eine SQL-Anweisung oder eine Tabledef bezieht, die eine angefügte Tabelle darstellt, können Sie nicht `dbOpenTable` für das Typargument verwenden. andernfalls löst MFC eine Ausnahme aus. Um zu ermitteln, ob ein Tabledef-Objekt eine angefügte Tabelle darstellt, erstellen Sie ein [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) -Objekt, und rufen Sie seine [GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect) -Member-Funktion auf

Verwenden Sie das- `dbSeeChanges` Flag, wenn Sie Änderungen, die von einem anderen Benutzer oder einem anderen Programm auf dem Computer vorgenommen werden, beim Bearbeiten oder löschen desselben Datensatzes abfangen möchten. Wenn beispielsweise zwei Benutzer mit der Bearbeitung desselben Datensatzes beginnen, wird der erste Benutzer, der die Member-Funktion aufruft, `Update` erfolgreich ausgeführt. Wenn `Update` vom zweiten Benutzer aufgerufen wird, wird eine ausgelöst `CDaoException` . Wenn der zweite Benutzer versucht, `Delete` zum Löschen des Datensatzes aufzurufen, und er bereits vom ersten Benutzer geändert wurde, tritt ein auf `CDaoException` .

Wenn der Benutzer das `CDaoException` Update beim Aktualisieren erhält, sollte der Code den Inhalt der Felder aktualisieren und die neu geänderten Werte abrufen. Wenn die Ausnahme beim Löschen auftritt, könnte der Code die neuen Daten Satz Daten für den Benutzer anzeigen, und es wird eine Meldung angezeigt, die besagt, dass die Daten vor kurzem geändert wurden. An diesem Punkt kann Ihr Code eine Bestätigung anfordern, dass der Benutzer den Datensatz trotzdem löschen möchte.

> [!TIP]
> Verwenden Sie die vorwärts Bild Lauf Option ( `dbForwardOnly` ), um die Leistung zu verbessern, wenn Ihre Anwendung eine einzelne Durchführung eines Recordsets durchführt, das aus einer ODBC-Datenquelle geöffnet wurde.

Weitere Informationen finden Sie im Thema "OpenRecordset-Methode" in der DAO-Hilfe.

## <a name="cdaorecordsetrequery"></a><a name="requery"></a> CDaoRecordset:: Requery

Diese Member-Funktion zum Neuerstellen (aktualisieren) eines Recordsets aufruft.

```cpp
virtual void Requery();
```

### <a name="remarks"></a>Bemerkungen

Falls Datensätze zurückgegeben werden, wird der erste Datensatz zum aktuellen Datensatz.

Damit das Recordset die Ergänzungen und Löschungen widerspiegelt, die Sie oder andere Benutzer an der Datenquelle vornehmen, müssen Sie das Recordset durch Aufrufen von neu erstellen `Requery` . Wenn das Recordset ein Dynaset ist, spiegelt es automatisch Updates wider, die Sie oder andere Benutzer an den vorhandenen Datensätzen vornehmen (aber nicht an Ergänzungen). Wenn das Recordset eine Momentaufnahme ist, müssen Sie aufrufen, `Requery` um Änderungen durch andere Benutzer sowie Ergänzungen und Löschungen widerzuspiegeln.

Bei einem Dynaset oder einer Momentaufnahme können Sie jederzeit aufrufen, um `Requery` das Recordset mithilfe von Parameterwerten neu zu erstellen. Legen Sie den neuen Filter fest, oder sortieren Sie, indem Sie vor dem Aufrufen von [m_strFilter](#m_strfilter) und [m_strSort](#m_strsort) `Requery` Legen Sie neue Parameter fest, indem Sie Parameter Datenmembern neue Werte zuweisen, bevor Sie aufrufen `Requery` .

Wenn der Versuch, das Recordset neu zu erstellen, fehlschlägt, wird das Recordset geschlossen. Vor dem Aufrufen `Requery` von können Sie bestimmen, ob das Recordset durch Aufrufen der [canrestart](#canrestart) -Member-Funktion angefordert werden kann. `CanRestart` garantiert nicht, dass `Requery` erfolgreich ist.

> [!CAUTION]
> Nur aufrufen, `Requery` nachdem Sie aufgerufen haben `Open` .

> [!NOTE]
> Der Aufruf von " [Requery](#requery) " ändert DAO-Lesezeichen

Sie können nicht `Requery` für einen Dynaset-Type-oder Snapshot-Type-Recordset aufrufen, wenn der Aufruf `CanRestart` von 0 zurückgibt, und Sie können es nicht für ein Recordset vom Typ "Table" verwenden.

Wenn sowohl `IsBOF` als auch nach dem-Befehl einen Wert ungleich `IsEOF` 0 (null) zurückgeben `Requery` , gibt die Abfrage keine Datensätze zurück, und das Recordset enthält keine Daten.

Weitere Informationen finden Sie im Thema "Requery Method" in der DAO-Hilfe.

## <a name="cdaorecordsetseek"></a><a name="seek"></a> CDaoRecordset:: Seek

Mit dieser Member-Funktion können Sie den Datensatz in einem indizierten Tabellentyp-Recordset-Objekt suchen, das die angegebenen Kriterien für den aktuellen Index erfüllt und diesen Datensatz zum aktuellen Datensatz führt.

```cpp
BOOL Seek(
    LPCTSTR lpszComparison,
    COleVariant* pKey1,
    COleVariant* pKey2 = NULL,
    COleVariant* pKey3 = NULL);

BOOL Seek(
    LPCTSTR lpszComparison,
    COleVariant* pKeyArray,
    WORD nKeys);
```

### <a name="parameters"></a>Parameter

*lpszComparison*<br/>
Einer der folgenden Zeichen folgen Ausdrücke: "<", " \<=", "=", "> =" oder ">".

*pKey1*<br/>
Ein Zeiger auf einen [COleVariant](../../mfc/reference/colevariant-class.md) , dessen Wert dem ersten Feld im Index entspricht. Erforderlich.

*pKey2*<br/>
Ein Zeiger auf einen `COleVariant` , dessen Wert dem zweiten Feld im Index entspricht, sofern vorhanden. Der Standardwert ist NULL.

*pKey3*<br/>
Ein Zeiger auf einen `COleVariant` , dessen Wert dem dritten Feld im Index entspricht, sofern vorhanden. Der Standardwert ist NULL.

*pkeyarray*<br/>
Ein Zeiger auf ein Array von Varianten. Die Array Größe entspricht der Anzahl der Felder im Index.

*nkeys*<br/>
Eine ganze Zahl, die der Größe des Arrays entspricht, d. h. die Anzahl der Felder im Index.

> [!NOTE]
> Geben Sie keine Platzhalter in den Schlüsseln an. Platzhalter bewirken `Seek` , dass keine übereinstimmenden Datensätze zurückgibt.

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn übereinstimmende Datensätze gefunden werden, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die zweite Version (Array) von `Seek` , um Indizes von vier Feldern oder mehr zu verarbeiten.

`Seek` aktiviert die Index Suche mit hoher Leistung für Tabellentypen-Recordsets. Sie müssen den aktuellen Index festlegen, indem Sie aufrufen, `SetCurrentIndex` bevor Sie aufrufen `Seek` . Wenn der Index ein nicht eindeutiges Schlüsselfeld oder Felder identifiziert, ermittelt `Seek` den ersten Datensatz, der die Kriterien erfüllt. Wenn Sie keinen Index festlegen, wird eine Ausnahme ausgelöst.

Beachten Sie Folgendes: Wenn Sie kein Unicode-Recordset erstellen, `COleVariant` müssen die Objekte explizit als ANSI deklariert werden. Dies kann mithilfe der [COleVariant:: COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszsrc* **,** *vzrc* **)** -Form des Konstruktors erfolgen, wenn *vtrc* auf (ANSI) festgelegt ist, `VT_BSTRT` oder indem Sie die `COleVariant` Funktion [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszsrc* **,** *vtrc* **)** mit der auf festgelegten *vzrc* verwenden `VT_BSTRT` .

Wenn Sie aufzurufen `Seek` , übergeben Sie mindestens einen Schlüsselwert und einen Vergleichs Operator ("<", " \<=", "=", "> =" oder ">"). `Seek` durchsucht die angegebenen Schlüsselfelder und sucht den ersten Datensatz, der die von *lpszComparison* und *pKey1*angegebenen Kriterien erfüllt. Wenn Sie gefunden wird, gibt einen Wert ungleich `Seek` 0 (null) zurück Wenn keine Entsprechung gefunden `Seek` wird, `Seek` gibt 0 (null) zurück, und der aktuelle Datensatz ist nicht definiert. Wenn DAO direkt verwendet wird, müssen Sie explizit die NoMatch-Eigenschaft überprüfen.

Wenn `lpszComparison` "=", ">=" oder ">" ist, `Seek` beginnt am Anfang des Indexes. Wenn *lpszComparison* den Wert "<" oder "<=" hat, `Seek` beginnt am Ende des Indexes und wird rückwärts durchsucht, es sei denn, es sind doppelte Indexeinträge am Ende vorhanden. In diesem Fall `Seek` beginnt bei einem beliebigen Eintrag unter den doppelten Indexeinträgen am Ende des Indexes.

Es muss kein aktueller Datensatz vorhanden sein, wenn Sie verwenden `Seek` .

Um einen Datensatz in einem "Dynaset-Type"-oder "Snapshot-Type"-Recordset zu suchen, das eine bestimmte Bedingung erfüllt, verwenden Sie die Suchvorgänge. Um alle Datensätze einzuschließen, nicht nur die, die eine bestimmte Bedingung erfüllen, verwenden Sie die Verschiebungs Vorgänge, um von Datensatz zu Datensatz zu wechseln.

Sie können `Seek` für eine angefügte Tabelle eines beliebigen Typs nicht aufzurufen, da angefügte Tabellen als Dynaset-Type-oder Snapshot-Type-Recordsets geöffnet werden müssen. Wenn Sie jedoch anrufen, `CDaoDatabase::Open` um eine installierbare ISAM-Datenbank direkt zu öffnen, können Sie `Seek` für Tabellen in dieser Datenbank aufzurufen, obwohl die Leistung möglicherweise langsam ist.

Weitere Informationen finden Sie im Thema "Seek Method" in der DAO-Hilfe.

## <a name="cdaorecordsetsetabsoluteposition"></a><a name="setabsoluteposition"></a> CDaoRecordset:: SetAbsolutePosition

Legt die relative Datensatznummer des aktuellen Datensatzes eines Recordset-Objekts fest.

```cpp
void SetAbsolutePosition(long lPosition);
```

### <a name="parameters"></a>Parameter

*lposition*<br/>
Entspricht der Ordinalposition des aktuellen Datensatzes im Recordset.

### <a name="remarks"></a>Bemerkungen

Durch Aufrufen von `SetAbsolutePosition` können Sie den aktuellen Daten Satz Zeiger auf einen bestimmten Datensatz auf der Grundlage seiner Ordinalposition in einem "Dynaset-Type"-oder "Snapshot-Type"-Recordset positionieren. Sie können auch die aktuelle Datensatznummer ermitteln, indem Sie [GetAbsolutePosition](#getabsoluteposition)aufrufen.

> [!NOTE]
> Diese Member-Funktion ist nur für den Dynaset-Type-und den Snapshot-Type-Recordsets gültig.

Der AbsolutePosition-Eigenschafts Wert des zugrunde liegenden DAO-Objekts ist NULL basiert. eine Einstellung von 0 bezieht sich auf den ersten Datensatz im Recordset. Wenn Sie einen Wert festlegen, der größer als die Anzahl der aufgefüllten Datensätze ist, löst MFC eine Ausnahme aus. Sie können die Anzahl der gefüllten Datensätze im Recordset ermitteln, indem Sie die- `GetRecordCount` Member-Funktion aufrufen.

Wenn der aktuelle Datensatz gelöscht wird, ist der Wert der AbsolutePosition-Eigenschaft nicht definiert, und MFC löst eine Ausnahme aus, wenn darauf verwiesen wird. Am Ende der Sequenz werden neue Datensätze hinzugefügt.

> [!NOTE]
> Diese Eigenschaft ist nicht für die Verwendung als Ersatz Zeichenfolge vorgesehen. Lesezeichen sind immer noch die empfohlene Methode zum beibehalten und zurückkehren zu einer gegebenen Position und sind die einzige Möglichkeit, den aktuellen Datensatz für alle Typen von Recordset-Objekten zu positionieren, die Lesezeichen unterstützen. Insbesondere wird die Position eines bestimmten Datensatzes geändert, wenn Datensätze vor dem Löschen gelöscht werden. Es ist auch nicht sichergestellt, dass ein bestimmter Datensatz die gleiche absolute Position hat, wenn der Recordset erneut erstellt wird, da die Reihenfolge der einzelnen Datensätze in einem Recordset nicht garantiert wird, es sei denn, Sie wird mit einer SQL-Anweisung mithilfe einer **OrderBy** -Klausel erstellt.

Weitere Informationen finden Sie im Thema "AbsolutePosition-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetsetbookmark"></a><a name="setbookmark"></a> CDaoRecordset:: SetBookmark

Ruft diese Member-Funktion auf, um das Recordset für den Datensatz zu positionieren, der das angegebene Lesezeichen enthält.

```cpp
void SetBookmark(COleVariant varBookmark);
```

### <a name="parameters"></a>Parameter

*varbookmark*<br/>
Ein [COleVariant](../../mfc/reference/colevariant-class.md) -Objekt, das den Lesezeichen Wert für einen bestimmten Datensatz enthält.

### <a name="remarks"></a>Bemerkungen

Wenn ein Recordset-Objekt erstellt oder geöffnet wird, verfügt jeder seiner Datensätze bereits über ein eindeutiges Lesezeichen. Sie können das Lesezeichen für den aktuellen Datensatz abrufen, indem Sie aufrufen `GetBookmark` und den Wert in einem- `COleVariant` Objekt speichern. Sie können später zu diesem Datensatz zurückkehren, indem Sie `SetBookmark` mithilfe des gespeicherten Lesezeichen Werts aufrufen.

> [!NOTE]
> Der Aufruf von " [Requery](#requery) " ändert DAO-Lesezeichen

Beachten Sie Folgendes: Wenn Sie kein Unicode-Recordset erstellen, `COleVariant` muss das Objekt explizit als ANSI deklariert werden. Dies kann mithilfe der [COleVariant:: COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszsrc* **,** *vzrc* **)** -Form des Konstruktors erfolgen, wenn *vtrc* auf (ANSI) festgelegt ist, `VT_BSTRT` oder indem Sie die `COleVariant` Funktion [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszsrc* **,** *vtrc* **)** mit der auf festgelegten *vzrc* verwenden `VT_BSTRT` .

Weitere Informationen finden Sie in den Themen "Bookmark Property" und "Bookmarkable Property" in der DAO-Hilfe.

## <a name="cdaorecordsetsetcachesize"></a><a name="setcachesize"></a> CDaoRecordset:: setCacheSize

Mit dieser Member-Funktion können Sie die Anzahl der Datensätze festlegen, die zwischengespeichert werden sollen.

```cpp
void SetCacheSize(long lSize);
```

### <a name="parameters"></a>Parameter

*LSIZE*<br/>
Gibt die Anzahl der Datensätze an. Ein typischer Wert ist 100. Durch die Einstellung 0 wird die Zwischenspeicherung deaktiviert. Die Einstellung muss zwischen 5 und 1200 Datensätzen liegen. Der Cache kann eine beträchtliche Menge an Arbeitsspeicher beanspruchen.

### <a name="remarks"></a>Bemerkungen

Ein Cache ist ein Speicherplatz im lokalen Speicher, der die Daten enthält, die zuletzt vom Server abgerufen wurden, wenn die Daten während der Ausführung der Anwendung erneut angefordert werden. Das Zwischenspeichern von Daten verbessert die Leistung einer Anwendung, die Daten von einem Remote Server durch Dynaset-Type Recordset-Objekte abruft. Wenn Daten angefordert werden, überprüft die Microsoft Jet-Datenbank-Engine den Cache zuerst auf die angeforderten Daten, anstatt Sie vom Server abzurufen, was mehr Zeit in sich bringt. Daten, die nicht aus einer ODBC-Datenquelle stammen, werden nicht im Cache gespeichert.

Jede ODBC-Datenquelle, z. b. eine angefügte Tabelle, kann über einen lokalen Cache verfügen. Um den Cache zu erstellen, öffnen Sie ein Recordset-Objekt aus der Remote Datenquelle, rufen Sie die `SetCacheSize` -und-Member-Funktionen auf, `SetCacheStart` und rufen Sie dann die-Element Funktion auf, `FillCache` oder durchlaufen Sie die Datensätze mithilfe eines der Verschiebungs Vorgänge. Der *LSIZE* -Parameter der `SetCacheSize` Member-Funktion kann auf der Anzahl von Datensätzen basieren, mit denen Ihre Anwendung gleichzeitig arbeiten kann. Wenn Sie z. b. ein Recordset als Quelle der Daten verwenden, die auf dem Bildschirm angezeigt werden sollen, können Sie den `SetCacheSize` *LSIZE* -Parameter als 20 übergeben, um 20 Datensätze gleichzeitig anzuzeigen.

Weitere Informationen finden Sie im Thema "CacheSize, CacheStart Properties" in der DAO-Hilfe.

## <a name="cdaorecordsetsetcachestart"></a><a name="setcachestart"></a> CDaoRecordset:: SetCacheStart

Diese Member-Funktion wird aufgerufen, um das Lesezeichen des ersten Datensatzes im Recordset anzugeben, das zwischengespeichert werden soll.

```cpp
void SetCacheStart(COleVariant varBookmark);
```

### <a name="parameters"></a>Parameter

*varbookmark*<br/>
Ein [COleVariant](../../mfc/reference/colevariant-class.md) , der das Lesezeichen des ersten Datensatzes im Recordset angibt, das zwischengespeichert werden soll.

### <a name="remarks"></a>Bemerkungen

Sie können den Lesezeichen Wert eines beliebigen Datensatzes für den *varbookmark* -Parameter der `SetCacheStart` Member-Funktion verwenden. Legen Sie den Datensatz, für den Sie den Cache starten möchten, mit dem aktuellen Datensatz fest, richten Sie mithilfe von [SetBookmark](#setbookmark)ein Lesezeichen für diesen Datensatz ein, und übergeben Sie den Lesezeichen Wert als Parameter für die `SetCacheStart` Member-Funktion.

Die Microsoft Jet-Datenbank-Engine fordert Datensätze im Cache Bereich aus dem Cache an und fordert Datensätze außerhalb des Cache Bereichs vom Server an.

Aus dem Cache abgerufene Datensätze enthalten keine Änderungen, die von anderen Benutzern gleichzeitig an den Quelldaten vorgenommen wurden.

Wenn Sie ein Update aller zwischengespeicherten Daten erzwingen möchten, übergeben Sie den *LSIZE* -Parameter von `SetCacheSize` als 0, `SetCacheSize` Wiederholen Sie den Vorgang mit der Größe des ursprünglich angeforderten Caches, und aufrufen Sie dann die `FillCache` Member-Funktion.

Beachten Sie Folgendes: Wenn Sie kein Unicode-Recordset erstellen, `COleVariant` muss das Objekt explizit als ANSI deklariert werden. Dies kann mithilfe der [COleVariant:: COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszsrc* **,** *vzrc* **)** -Form des Konstruktors erfolgen, wenn *vtrc* auf (ANSI) festgelegt ist, `VT_BSTRT` oder indem Sie die `COleVariant` Funktion [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszsrc* **,** *vtrc* **)** mit der auf festgelegten *vzrc* verwenden `VT_BSTRT` .

Weitere Informationen finden Sie im Thema CacheSize, CacheStart Properties in der DAO-Hilfe.

## <a name="cdaorecordsetsetcurrentindex"></a><a name="setcurrentindex"></a> CDaoRecordset:: SetCurrentIndex

Mit dieser Member-Funktion können Sie einen Index für ein Recordset vom Typ "Table" festlegen.

```cpp
void SetCurrentIndex(LPCTSTR lpszIndex);
```

### <a name="parameters"></a>Parameter

*lpszindex*<br/>
Ein Zeiger, der den Namen des festzulegenden Indexes enthält.

### <a name="remarks"></a>Bemerkungen

Datensätze in Basistabellen werden nicht in einer bestimmten Reihenfolge gespeichert. Das Festlegen eines Indexes ändert die Reihenfolge der Datensätze, die von der Datenbank zurückgegeben werden, jedoch nicht die Reihenfolge, in der die Datensätze gespeichert werden. Der angegebene Index muss bereits definiert sein. Wenn Sie versuchen, ein Index Objekt zu verwenden, das nicht vorhanden ist, oder wenn der Index beim aufzurufen von [Seek](#seek)nicht festgelegt wird, löst MFC eine Ausnahme aus.

Sie können einen neuen Index für die Tabelle erstellen, indem Sie [CDaoTableDef:: CreateIndex](../../mfc/reference/cdaotabledef-class.md#createindex) aufrufen und den neuen Index an die Indexes-Auflistung der zugrunde liegenden Tabledef anhängen, indem Sie [CDaoTableDef:: Append](../../mfc/reference/cdaotabledef-class.md#append)aufrufen und dann das Recordset erneut öffnen.

Datensätze, die von einem Recordset des Tabellentyps zurückgegeben werden, können nur von den für die zugrunde liegenden Tabledef definierten Indizes geordnet werden Wenn Sie Datensätze in einer anderen Reihenfolge sortieren möchten, können Sie mithilfe einer in [CDaoRecordset:: m_strSort](#m_strsort)gespeicherten SQL **OrderBy** -Klausel einen Dynaset-Type-oder Snapshot-Type-Recordset öffnen.

Weitere Informationen finden Sie im Thema "Index Objekt" und in der Definition "aktueller Index" in der DAO-Hilfe.

## <a name="cdaorecordsetsetfielddirty"></a><a name="setfielddirty"></a> CDaoRecordset:: SetFieldDirty

Diese Member-Funktion wird aufgerufen, um einen Felddatenmember des Recordsets als geändert oder unverändert zu markieren.

```cpp
void SetFieldDirty(
    void* pv,
    BOOL bDirty = TRUE);
```

### <a name="parameters"></a>Parameter

*teuren*<br/>
Enthält die Adresse eines Felddatenmembers im Recordset oder NULL. Wenn der Wert NULL ist, werden alle Felddatenmember im Recordset gekennzeichnet. (C++ NULL ist in der Daten Bank Terminologie nicht identisch mit NULL, was bedeutet, dass kein Wert vorhanden ist.)

*bdirty*<br/>
TRUE, wenn der Felddatenmember als "Dirty" (geändert) gekennzeichnet werden soll. Andernfalls false, wenn der Felddatenmember als "Clean" (unverändert) gekennzeichnet werden soll.

### <a name="remarks"></a>Bemerkungen

Das Markieren von Feldern als unverändert stellt sicher, dass das Feld nicht aktualisiert wird.

Das Framework markiert geänderte Felddatenmember, um sicherzustellen, dass Sie durch den DAO-Daten Satz Feld Austausch-Mechanismus (DFX) in den Datensatz der Datenquelle geschrieben werden. Wenn Sie den Wert eines Felds ändern, wird das Feld in der Regel automatisch geändert, sodass Sie sich nur selten selbst anrufen müssen `SetFieldDirty` . Sie können jedoch manchmal sicherstellen, dass die Spalten explizit aktualisiert oder eingefügt werden, unabhängig davon, welcher Wert im Feld Datenmember liegt. Der DFX-Mechanismus nutzt auch die Verwendung von pseudonull. Weitere Informationen finden Sie unter [CDaoFieldExchange:: m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Wenn der Mechanismus für die doppelte Pufferung nicht verwendet wird, wird das Feld nicht automatisch als geändert festgelegt, wenn der Wert des Felds geändert wird. In diesem Fall muss das Feld explizit als geändert festgelegt werden. Das Flag in [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) steuert diese automatische Feld Überprüfung.

> [!NOTE]
> Diese Member-Funktion nur aufrufen, nachdem Sie [Edit](#edit) oder [AddNew](#addnew)aufgerufen haben.

Wenn NULL für das erste Argument der Funktion verwendet wird, wird die Funktion auf alle `outputColumn` Felder, **param** nicht auf die Parameter Felder in angewendet `CDaoFieldExchange` . Beispielsweise ist der-Befehl

[!code-cpp[NVC_MFCDatabase#6](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]

legt nur `outputColumn` Felder auf NULL fest. **param** -Felder sind nicht betroffen.

Wenn Sie an einem **param**arbeiten möchten, müssen Sie die tatsächliche Adresse des einzelnen **para** Metern angeben, an dem Sie arbeiten möchten, z. b.:

[!code-cpp[NVC_MFCDatabase#7](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]

Dies bedeutet, dass Sie nicht alle **param** -Felder wie bei Feldern auf NULL festlegen können `outputColumn` .

`SetFieldDirty` wird durch implementiert `DoFieldExchange` .

## <a name="cdaorecordsetsetfieldnull"></a><a name="setfieldnull"></a> CDaoRecordset:: SetFieldNull

Diese Member-Funktion wird aufgerufen, um einen Felddatenmember des Recordsets als NULL (ohne Wert) oder als nicht-NULL zu markieren.

```cpp
void SetFieldNull(
    void* pv,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parameter

*teuren*<br/>
Enthält die Adresse eines Felddatenmembers im Recordset oder NULL. Wenn der Wert NULL ist, werden alle Felddatenmember im Recordset gekennzeichnet. (C++ NULL ist in der Daten Bank Terminologie nicht identisch mit NULL, was bedeutet, dass kein Wert vorhanden ist.)

*bNULL*<br/>
Ein Wert ungleich 0 (null), wenn für den Felddatenmember kein Wert (null) gekennzeichnet werden soll. Andernfalls 0, wenn der Felddatenmember als nicht-NULL gekennzeichnet werden soll.

### <a name="remarks"></a>Bemerkungen

`SetFieldNull` wird für Felder verwendet, die im `DoFieldExchange` Mechanismus gebunden sind.

Wenn Sie einem Recordset einen neuen Datensatz hinzufügen, werden alle Felddatenmember anfänglich auf einen NULL-Wert festgelegt und als "Dirty" (geändert) gekennzeichnet. Wenn Sie einen Datensatz aus einer Datenquelle abrufen, verfügen seine Spalten entweder bereits über Werte oder sind NULL. Wenn es nicht angebracht ist, ein Feld NULL zu machen, wird eine [CDaoException](../../mfc/reference/cdaoexception-class.md) ausgelöst.

Wenn Sie z. b. einen doppelten Puffermechanismus verwenden möchten, z. b. Wenn Sie ausdrücklich ein Feld des aktuellen Datensatzes als keinen Wert festlegen möchten, müssen Sie `SetFieldNull` mit *bNULL* auf true festlegen, um ihn als Null zu kennzeichnen. Wenn ein Feld zuvor als NULL gekennzeichnet war und Sie diesem nun einen Wert zuordnen möchten, legen Sie einfach den neuen Wert fest. Sie müssen das NULL-Flag nicht mit entfernen `SetFieldNull` . Um zu ermitteln, ob das Feld NULL sein darf, nennen Sie [IsFieldNullable](#isfieldnullable).

Wenn Sie den Mechanismus für die doppelte Pufferung nicht verwenden, wird das Feld nicht automatisch als geändert und nicht als NULL festgelegt, wenn Sie den Wert des Felds ändern. Sie müssen die Felder "Dirty" und "non-NULL" festlegen. Das Flag in [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) steuert diese automatische Feld Überprüfung.

Der DFX-Mechanismus verwendet die Verwendung von pseudonull. Weitere Informationen finden Sie unter [CDaoFieldExchange:: m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

> [!NOTE]
> Diese Member-Funktion nur aufrufen, nachdem Sie [Edit](#edit) oder [AddNew](#addnew)aufgerufen haben.

Wenn NULL für das erste Argument der Funktion verwendet wird, wird die Funktion nur auf `outputColumn` Felder, **param** nicht auf Parameter Felder in angewendet `CDaoFieldExchange` . Beispielsweise ist der-Befehl

[!code-cpp[NVC_MFCDatabase#8](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]

legt nur `outputColumn` Felder auf NULL fest. **param** -Felder sind nicht betroffen.

## <a name="cdaorecordsetsetfieldvalue"></a><a name="setfieldvalue"></a> CDaoRecordset:: SetFieldValue

Mit dieser Member-Funktion können Sie den Wert eines Felds entweder durch Ordinalposition oder durch Ändern des Werts der Zeichenfolge festlegen.

```cpp
virtual void SetFieldValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);

virtual void SetFieldValue(
    int nIndex,
    const COleVariant& varValue);

void SetFieldValue(
    LPCTSTR lpszName,
    LPCTSTR lpszValue);

void SetFieldValue(
    int nIndex,
    LPCTSTR lpszValue);
```

### <a name="parameters"></a>Parameter

*lpszname*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen eines Felds enthält.

*varValue*<br/>
Ein Verweis auf ein [COleVariant](../../mfc/reference/colevariant-class.md) -Objekt, das den Wert für den Inhalt des Felds enthält.

*nIndex*<br/>
Eine ganze Zahl, die die Ordnungsposition des Felds in der Feld Auflistung des Recordsets (null basiert) darstellt.

*lpszvalue*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Wert des Feld Inhalts enthält.

### <a name="remarks"></a>Bemerkungen

Verwenden `SetFieldValue` Sie und [GetFieldValue](#getfieldvalue) , um Felder zur Laufzeit dynamisch zu binden, anstatt Spalten mit dem [DoFieldExchange](#dofieldexchange) -Mechanismus statisch zu binden.

Beachten Sie Folgendes: Wenn Sie kein Unicode-Recordset erstellen, müssen Sie entweder eine Form von verwenden, `SetFieldValue` die keinen- `COleVariant` Parameter enthält, oder das- `COleVariant` Objekt muss explizit als ANSI deklariert werden. Dies kann mithilfe der [COleVariant:: COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszsrc* **,** *vzrc* **)** -Form des Konstruktors erfolgen, wenn *vtrc* auf (ANSI) festgelegt ist, `VT_BSTRT` oder indem Sie die `COleVariant` Funktion [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszsrc* **,** *vtrc* **)** mit der auf festgelegten *vzrc* verwenden `VT_BSTRT` .

Weitere Informationen finden Sie in den Themen "Field Object" und "Value property" in der DAO-Hilfe.

## <a name="cdaorecordsetsetfieldvaluenull"></a><a name="setfieldvaluenull"></a> CDaoRecordset:: setfieldvaluenull

Diese Member-Funktion wird aufgerufen, um das Feld auf einen NULL-Wert festzulegen.

```cpp
void SetFieldValueNull(int nIndex);
void SetFieldValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der Index des Felds im Recordset für die Suche durch Null basierten Index.

*lpszname*<br/>
Der Name des Felds im Recordset für die Suche nach Namen.

### <a name="remarks"></a>Bemerkungen

C++ NULL ist nicht identisch mit NULL, was in der Daten Bank Terminologie bedeutet, dass kein Wert vorhanden ist.

Weitere Informationen finden Sie in den Themen "Field Object" und "Value property" in der DAO-Hilfe.

## <a name="cdaorecordsetsetlockingmode"></a><a name="setlockingmode"></a> CDaoRecordset:: SetLockingMode

Mit dieser Member-Funktion wird der Sperrentyp für das Recordset festgelegt.

```cpp
void SetLockingMode(BOOL bPessimistic);
```

### <a name="parameters"></a>Parameter

*bpessimistisch*<br/>
Ein Flag, das den Sperrentyp angibt.

### <a name="remarks"></a>Bemerkungen

Wenn die pessimistische Sperrung wirksam ist, wird die Seite 2 KB mit dem zu bearbeitende Datensatz gesperrt, sobald Sie die Member-Funktion aufgerufen haben `Edit` . Die Seite wird entsperrt, wenn Sie die- `Update` oder-Member-Funktion oder einen der Verschiebe-oder Suchvorgänge aufzurufen `Close` .

Wenn die optimistische Sperre wirksam ist, wird die 2K-Seite, die den Datensatz enthält, nur gesperrt, während der Datensatz mit der Member-Funktion aktualisiert wird `Update` .

Wenn eine Seite gesperrt ist, kann kein anderer Benutzerdaten Sätze auf derselben Seite bearbeiten. Wenn Sie aufzurufen `SetLockingMode` und einen Wert ungleich 0 (null) übergeben und ein anderer Benutzer die Seite bereits gesperrt hat, wird beim aufruft von eine Ausnahme ausgelöst `Edit` . Andere Benutzer können Daten von gesperrten Seiten lesen.

Wenn Sie `SetLockingMode` mit einem Wert von 0 (null) und später aufzurufen `Update` , während die Seite von einem anderen Benutzer gesperrt ist, tritt eine Ausnahme auf. Um die Änderungen anzuzeigen, die von einem anderen Benutzer an Ihrem Datensatz vorgenommen wurden (und die Änderungen verlieren), müssen Sie die `SetBookmark` Member-Funktion mit dem Lesezeichen Wert des aktuellen Datensatzes abrufen.

Beim Arbeiten mit ODBC-Datenquellen ist der Sperrmodus immer vollständig.

## <a name="cdaorecordsetsetparamvalue"></a><a name="setparamvalue"></a> CDaoRecordset:: SetParamValue

Diese Member-Funktion aufrufen, um den Wert eines Parameters im Recordset zur Laufzeit festzulegen.

```cpp
virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);

virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Die numerische Position des Parameters in der Parameter Auflistung von QueryDef.

*var*<br/>
Der festzulegende Wert. siehe Hinweise.

*lpszname*<br/>
Der Name des Parameters, dessen Wert Sie festlegen möchten.

### <a name="remarks"></a>Bemerkungen

Der-Parameter muss bereits als Teil der SQL-Zeichenfolge des Recordsets eingerichtet worden sein. Sie können auf den Parameter entweder über den Namen oder die Indexposition in der Auflistung zugreifen.

Geben Sie den Wert an, der als-Objekt festgelegt wird `COleVariant` . Weitere Informationen zum Festlegen des gewünschten Werts und des Typs in das- `COleVariant` Objekt finden Sie unter Class [COleVariant](../../mfc/reference/colevariant-class.md). Beachten Sie Folgendes: Wenn Sie kein Unicode-Recordset erstellen, `COleVariant` muss das Objekt explizit als ANSI deklariert werden. Dies kann mithilfe der [COleVariant:: COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszsrc* **,** *vzrc* **)** -Form des Konstruktors erfolgen, wenn *vtrc* auf (ANSI) festgelegt ist, `VT_BSTRT` oder indem Sie die `COleVariant` Funktion [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszsrc* **,** *vtrc* **)** mit der auf festgelegten *vzrc* verwenden `VT_BSTRT` .

## <a name="cdaorecordsetsetparamvaluenull"></a><a name="setparamvaluenull"></a> CDaoRecordset:: setparamvaluenull

Diese Member-Funktion aufrufen, um den-Parameter auf einen NULL-Wert festzulegen.

```cpp
void SetParamValueNull(int nIndex);
void SetParamValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der Index des Felds im Recordset für die Suche durch Null basierten Index.

*lpszname*<br/>
Der Name des Felds im Recordset für die Suche nach Namen.

### <a name="remarks"></a>Bemerkungen

C++ NULL ist nicht identisch mit NULL, was in der Daten Bank Terminologie bedeutet, dass kein Wert vorhanden ist.

## <a name="cdaorecordsetsetpercentposition"></a><a name="setpercentposition"></a> CDaoRecordset:: setprozentuposition

Mit dieser Member-Funktion können Sie einen Wert festlegen, der die ungefähre Position des aktuellen Datensatzes im Recordset-Objekt basierend auf einem Prozentsatz der Datensätze im Recordset ändert.

```cpp
void SetPercentPosition(float fPosition);
```

### <a name="parameters"></a>Parameter

*Position*<br/>
Eine Zahl zwischen 0 und 100.

### <a name="remarks"></a>Bemerkungen

Wenn Sie mit einem Recordset vom Typ "Dynaset-Typ" oder "Snapshot" arbeiten, füllen Sie zuerst das Recordset aus, indem Sie zum letzten Datensatz wechseln, bevor Sie den Befehl ausführen `SetPercentPosition` . Wenn Sie aufrufen `SetPercentPosition` , bevor Sie das Recordset vollständig auffüllen, ist die Menge der Verschiebung relativ zur Anzahl der Datensätze, auf die zugegriffen wird, wie durch den Wert von [GetRecordCount](#getrecordcount)angegeben. Sie können zum letzten Datensatz wechseln, indem Sie aufrufen `MoveLast` .

Nachdem Sie aufgerufen `SetPercentPosition` haben, wird der Datensatz an der ungefähren Position, die diesem Wert entspricht, aktuell.

> [!NOTE]
> `SetPercentPosition`Es wird nicht empfohlen, den aktuellen Datensatz zu einem bestimmten Datensatz in einem Recordset zu verschieben. Aufrufen der [SetBookmark](#setbookmark) -Member-Funktion.

Weitere Informationen finden Sie im Thema "prozentualpositions Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetupdate"></a><a name="update"></a> CDaoRecordset:: Update

Diese Member-Funktion wird nach einem-Rückruf der- `AddNew` oder- `Edit` Member-Funktion aufgerufen.

```cpp
virtual void Update();
```

### <a name="remarks"></a>Bemerkungen

Dieser Befehl ist erforderlich, um den- `AddNew` Vorgang oder den- `Edit` Vorgang abzuschließen.

`AddNew`Und `Edit` bereiten einen Bearbeitungs Puffer vor, in dem die hinzugefügten oder bearbeiteten Daten zum Speichern in der Datenquelle platziert werden. `Update` speichert die Daten. Nur die Felder, die als geändert markiert oder erkannt wurden, werden aktualisiert.

Wenn die Datenquelle Transaktionen unterstützt, können Sie den `Update` -Befehl (und den entsprechenden- `AddNew` oder- `Edit` Rückruf) einer Transaktion ausführen.

> [!CAUTION]
> Wenn Sie aufrufen `Update` , ohne zuerst entweder `AddNew` oder aufzurufen `Edit` , löst eine aus `Update` `CDaoException` . Wenn Sie `AddNew` oder oder Ausführen `Edit` , müssen Sie `Update` vor dem Abrufen von " [wvenext](#movenext) " oder dem Schließen des Recordsets oder der Datenquellen Verbindung aufzurufen. Andernfalls gehen die Änderungen ohne Benachrichtigung verloren.

Wenn das Recordset-Objekt pessimistisch in einer mehr Benutzerumgebung gesperrt ist, bleibt der Datensatz von der Zeit `Edit` bis zum Abschluss der Aktualisierung gesperrt. Wenn das Recordset optimistisch gesperrt ist, wird der Datensatz gesperrt und mit dem vorab bearbeiteten Datensatz verglichen, kurz bevor er in der Datenbank aktualisiert wird. Wenn sich der Datensatz geändert hat, seit Sie aufgerufen `Edit` haben, `Update` schlägt der Vorgang fehl, und MFC löst eine Ausnahme aus. Sie können den Sperrmodus mit ändern `SetLockingMode` .

> [!NOTE]
> Die optimistische Sperre wird immer in externen Daten Bank Formaten wie ODBC und installier barer ISAM verwendet.

Weitere Informationen finden Sie in den Themen "AddNew Method", "CancelUpdate Method", "Delete Method", "LastModified Property", "Update Method" und "EditMode Property" in der DAO-Hilfe.

## <a name="see-also"></a>Weitere Informationen

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CDaoTableDef-Klasse](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoWorkspace-Klasse](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase-Klasse](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoQueryDef-Klasse](../../mfc/reference/cdaoquerydef-class.md)<br/>
