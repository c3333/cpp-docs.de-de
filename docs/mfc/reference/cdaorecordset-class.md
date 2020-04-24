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
ms.openlocfilehash: 6a1475d1b0bc083cfd180ea5a211e752c973e2f8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754678"
---
# <a name="cdaorecordset-class"></a>CDaoRecordset-Klasse

Stellt eine Gruppe von Datensätzen dar, die aus einer Datenquelle ausgewählt wurden.

## <a name="syntax"></a>Syntax

```
class CDaoRecordset : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoRecordset::CDaoRecordset](#cdaorecordset)|Erstellt ein `CDaoRecordset`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoRecordset::Neu hinzufügen](#addnew)|Bereitet das Hinzufügen eines neuen Datensatzes vor. Rufen Sie [Update](#update) auf, um den Zusatz abzuschließen.|
|[CDaoRecordset::CanAppend](#canappend)|Gibt einen Wert ungleich Null zurück, wenn dem Recordset über die [AddNew-Memberfunktion](#addnew) neue Datensätze hinzugefügt werden können.|
|[CDaoRecordset::CanBookmark](#canbookmark)|Gibt einen Wert ungleich Null zurück, wenn das Recordset Lesezeichen unterstützt.|
|[CDaoRecordset::AbbrechenUpdate](#cancelupdate)|Bricht alle ausstehenden Aktualisierungen aufgrund eines [Edit-](#edit) oder [AddNew-Vorgangs](#addnew) ab.|
|[CDaoRecordset::CanNeustart](#canrestart)|Gibt einen Wert ungleich Null zurück, wenn [Requery](#requery) aufgerufen werden kann, um die Recordset-Abfrage erneut auszuführen.|
|[CDaoRecordset::CanScroll](#canscroll)|Gibt einen Wert ungleich Null zurück, wenn Sie durch die Datensätze scrollen können.|
|[CDaoRecordset::CanTransact](#cantransact)|Gibt einen Wert ungleich Null zurück, wenn die Datenquelle Transaktionen unterstützt.|
|[CDaoRecordset::CanUpdate](#canupdate)|Gibt einen Wert ungleich Null zurück, wenn das Recordset aktualisiert werden kann (Sie können Datensätze hinzufügen, aktualisieren oder löschen).|
|[CDaoRecordset::Schließen](#close)|Schließt das Recordset.|
|[CDaoRecordset::Delete](#delete)|Löscht den aktuellen Datensatz aus dem Recordset. Sie müssen nach dem Löschen explizit zu einem anderen Datensatz scrollen.|
|[CDaoRecordset::DoFieldExchange](#dofieldexchange)|Wird aufgerufen, um Daten (in beide Richtungen) zwischen den Felddatenelementen des Recordsets und dem entsprechenden Datensatz in der Datenquelle auszutauschen. Implementiert DAO-Datensatzfeldaustausch (DFX).|
|[CDaoRecordset::Bearbeiten](#edit)|Bereitet sich auf Änderungen am aktuellen Datensatz vor. Rufen `Update` Sie an, um die Bearbeitung abzuschließen.|
|[CDaoRecordset::FillCache](#fillcache)|Füllt den gesamten oder einen Teil eines lokalen Caches für ein Recordset-Objekt, das Daten aus einer ODBC-Datenquelle enthält.|
|[CDaoRecordset::Suchen](#find)|Sucht die erste, nächste, vorherige oder letzte Position einer bestimmten Zeichenfolge in einem Recordset vom Typ Dynaset, das die angegebenen Kriterien erfüllt und diesen Datensatz zum aktuellen Datensatz macht.|
|[CDaoRecordset::FindFirst](#findfirst)|Sucht den ersten Datensatz in einem Datensatz vom Typ Dynaset oder Snapshot, der die angegebenen Kriterien erfüllt und diesen Datensatz zum aktuellen Datensatz macht.|
|[CDaoRecordset::FindLast](#findlast)|Sucht den letzten Datensatz in einem Datensatz vom Typ Dynaset oder Snapshot, der die angegebenen Kriterien erfüllt und diesen Datensatz zum aktuellen Datensatz macht.|
|[CDaoRecordset::FindNext](#findnext)|Sucht den nächsten Datensatz in einem Datensatz vom Typ Dynaset oder Snapshot, der die angegebenen Kriterien erfüllt und diesen Datensatz zum aktuellen Datensatz macht.|
|[CDaoRecordset::FindPrev](#findprev)|Sucht den vorherigen Datensatz in einem Datensatz vom Typ Dynaset oder Snapshot, der die angegebenen Kriterien erfüllt und diesen Datensatz zum aktuellen Datensatz macht.|
|[CDaoRecordset::GetAbsolutePosition](#getabsoluteposition)|Gibt die Datensatznummer des aktuellen Datensatzes eines Recordset-Objekts zurück.|
|[CDaoRecordset::GetBookmark](#getbookmark)|Gibt einen Wert zurück, der die Textmarke in einem Datensatz darstellt.|
|[CDaoRecordset::GetCacheSize](#getcachesize)|Gibt einen Wert zurück, der die Anzahl der Datensätze in einem Recordset vom Typ Dynaset angibt, der Daten enthält, die lokal aus einer ODBC-Datenquelle zwischengespeichert werden sollen.|
|[CDaoRecordset::GetCacheStart](#getcachestart)|Gibt einen Wert zurück, der die Textmarke des ersten Datensatzes im zwischenspeichernden Recordset angibt.|
|[CDaoRecordset::GetCurrentIndex](#getcurrentindex)|Gibt `CString` einen zurück, der den Namen des Indexenthälts `CDaoRecordset`enthält, der zuletzt für einen indizierten Tabellentyp verwendet wurde.|
|[CDaoRecordset::GetDateCreated](#getdatecreated)|Gibt das Datum und die `CDaoRecordset` Uhrzeit zurück, zu der die Basistabelle, die einem Objekt zugrunde liegt, erstellt wurde|
|[CDaoRecordset::GetDateLastUpdated](#getdatelastupdated)|Gibt das Datum und die Uhrzeit der letzten Änderung zurück, die am Entwurf einer Basistabelle vorgenommen wurde, die einem `CDaoRecordset` Objekt zugrunde liegt.|
|[CDaoRecordset::GetDefaultDBName](#getdefaultdbname)|Gibt den Namen der Standarddatenquelle zurück.|
|[CDaoRecordset::GetDefaultSQL](#getdefaultsql)|Wird aufgerufen, um die standardmäßige SQL-Zeichenfolge auszuführen.|
|[CDaoRecordset::GetEditMode](#geteditmode)|Gibt einen Wert zurück, der den Bearbeitungsstatus für den aktuellen Datensatz angibt.|
|[CDaoRecordset::GetFieldCount](#getfieldcount)|Gibt einen Wert zurück, der die Anzahl der Felder in einem Recordset darstellt.|
|[CDaoRecordset::GetFieldInfo](#getfieldinfo)|Gibt bestimmte Arten von Informationen zu den Feldern im Recordset zurück.|
|[CDaoRecordset::GetFieldValue](#getfieldvalue)|Gibt den Wert eines Felds in einem Recordset zurück.|
|[CDaoRecordset::GetIndexCount](#getindexcount)|Ruft die Anzahl der Indizes in einer Tabelle ab, die einem Recordset zugrunde liegt.|
|[CDaoRecordset::GetIndexInfo](#getindexinfo)|Gibt verschiedene Arten von Informationen zu einem Index zurück.|
|[CDaoRecordset::GetLastModifiedBookmark](#getlastmodifiedbookmark)|Wird verwendet, um den zuletzt hinzugefügten oder aktualisierten Datensatz zu ermitteln.|
|[CDaoRecordset::GetLockingMode](#getlockingmode)|Gibt einen Wert zurück, der den Typ der Sperrung angibt, der während der Bearbeitung wirksam ist.|
|[CDaoRecordset::GetName](#getname)|Gibt `CString` eine zurück, die den Namen des Recordsets enthält.|
|[CDaoRecordset::GetParamValue](#getparamvalue)|Ruft den aktuellen Wert des angegebenen Parameters ab, der im zugrunde liegenden DAOParameter-Objekt gespeichert ist.|
|[CDaoRecordset::GetPercentPosition](#getpercentposition)|Gibt die Position des aktuellen Datensatzes als Prozentsatz der Gesamtzahl der Datensätze zurück.|
|[CDaoRecordset::GetRecordCount](#getrecordcount)|Gibt die Anzahl der Datensätze zurück, auf die in einem Recordset-Objekt zugegriffen wird.|
|[CDaoRecordset::GetSQL](#getsql)|Ruft die SQL-Zeichenfolge ab, die zum Auswählen von Datensätzen für das Recordset verwendet wird.|
|[CDaoRecordset::GetType](#gettype)|Wird aufgerufen, um den Typ eines Recordsets zu bestimmen: Tabellentyp, Dynaset- oder Snapshot-Typ.|
|[CDaoRecordset::GetValidationRule](#getvalidationrule)|Gibt `CString` einen zurück, der den Wert enthält, der Daten überprüft, während sie in ein Feld eingegeben werden.|
|[CDaoRecordset::GetValidationText](#getvalidationtext)|Ruft den Text ab, der angezeigt wird, wenn eine Validierungsregel nicht erfüllt ist.|
|[CDaoRecordset::IsBOF](#isbof)|Gibt einen Wert ungleich Null zurück, wenn das Recordset vor dem ersten Datensatz positioniert wurde. Es ist kein aktueller Datensatz vorhanden.|
|[CDaoRecordset::IsDeleted](#isdeleted)|Gibt einen Wert ungleich Null zurück, wenn das Recordset auf einem gelöschten Datensatz positioniert ist.|
|[CDaoRecordset::IsEOF](#iseof)|Gibt einen Wert ungleich Null zurück, wenn das Recordset nach dem letzten Datensatz positioniert wurde. Es ist kein aktueller Datensatz vorhanden.|
|[CDaoRecordset::IsFieldDirty](#isfielddirty)|Gibt einen Wert ungleich Null zurück, wenn das angegebene Feld im aktuellen Datensatz geändert wurde.|
|[CDaoRecordset::IsFieldNull](#isfieldnull)|Gibt einen Wert ungleich Null zurück, wenn das angegebene Feld im aktuellen Datensatz Null ist (ohne Wert).|
|[CDaoRecordset::IsFieldNullable](#isfieldnullable)|Gibt einen Wert ungleich Null zurück, wenn das angegebene Feld im aktuellen Datensatz auf Null festgelegt werden kann (ohne Wert).|
|[CDaoRecordset::IsOpen](#isopen)|Gibt einen Wert ungleich Null zurück, wenn [Open](#open) zuvor aufgerufen wurde.|
|[CDaoRecordset::Bewegen](#move)|Positioniert das Recordset in eine angegebene Anzahl von Datensätzen aus dem aktuellen Datensatz in beide Richtungen.|
|[CDaoRecordset::MoveFirst](#movefirst)|Positioniert den aktuellen Datensatz auf dem ersten Datensatz im Recordset.|
|[CDaoRecordset::MoveLast](#movelast)|Positioniert den aktuellen Datensatz auf dem letzten Datensatz im Recordset.|
|[CDaoRecordset::MoveNext](#movenext)|Positioniert den aktuellen Datensatz auf dem nächsten Datensatz im Recordset .|
|[CDaoRecordset::MovePrev](#moveprev)|Positioniert den aktuellen Datensatz auf dem vorherigen Datensatz im Recordset.|
|[CDaoRecordset::Öffnen](#open)|Erstellt ein neues Recordset aus einer Tabelle, einem Dynaset oder einem Snapshot.|
|[CDaoRecordset::Requery](#requery)|Führt die Abfrage des Recordsets erneut aus, um die ausgewählten Datensätze zu aktualisieren.|
|[CDaoRecordset::Suchen](#seek)|Sucht den Datensatz in einem indizierten Recordset-Objekt vom Tabellentyp, das die angegebenen Kriterien für den aktuellen Index erfüllt und diesen Datensatz zum aktuellen Datensatz macht.|
|[CDaoRecordset::SetAbsolutePosition](#setabsoluteposition)|Legt die Datensatznummer des aktuellen Datensatzes eines Record-Objekts fest.|
|[CDaoRecordset::SetBookmark](#setbookmark)|Positioniert das Recordset in einem Datensatz, der das angegebene Lesezeichen enthält.|
|[CDaoRecordset::SetCacheSize](#setcachesize)|Legt einen Wert fest, der die Anzahl der Datensätze in einem Recordset vom Typ Dynaset angibt, der Daten enthält, die lokal aus einer ODBC-Datenquelle zwischengespeichert werden sollen.|
|[CDaoRecordset::SetCacheStart](#setcachestart)|Legt einen Wert fest, der die Textmarke des ersten Datensatzes im zwischenspeichernden Recordset angibt.|
|[CDaoRecordset::SetCurrentIndex](#setcurrentindex)|Wird aufgerufen, um einen Index für ein Datensatzsatz vom Tabellentyp festzulegen.|
|[CDaoRecordset::SetFieldDirty](#setfielddirty)|Markiert das angegebene Feld im aktuellen Datensatz als geändert.|
|[CDaoRecordset::SetFieldNull](#setfieldnull)|Legt den Wert des angegebenen Felds im aktuellen Datensatz auf Null fest (ohne Wert).|
|[CDaoRecordset::SetFieldValue](#setfieldvalue)|Legt den Wert eines Felds in einem Recordset fest.|
|[CDaoRecordset::SetFieldValueNull](#setfieldvaluenull)|Legt den Wert eines Felds in einem Recordset auf Null fest. (ohne Wert).|
|[CDaoRecordset::SetLockingMode](#setlockingmode)|Legt einen Wert fest, der den Typ der Sperrung angibt, die während der Bearbeitung wirksam werden soll.|
|[CDaoRecordset::SetParamValue](#setparamvalue)|Legt den aktuellen Wert des angegebenen Parameters fest, der im zugrunde liegenden DAOParameter-Objekt gespeichert ist.|
|[CDaoRecordset::SetParamValueNull](#setparamvaluenull)|Legt den aktuellen Wert des angegebenen Parameters auf Null fest (ohne Wert).|
|[CDaoRecordset::SetPercentPosition](#setpercentposition)|Legt die Position des aktuellen Datensatzes auf einen Speicherort fest, der einem Prozentsatz der Gesamtzahl der Datensätze in einem Datensatz entspricht.|
|[CDaoRecordset::Update](#update)|Schließt einen `AddNew` `Edit` oder einen Vorgang ab, indem die neuen oder bearbeiteten Daten in der Datenquelle gespeichert werden.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoRecordset::m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)|Enthält ein Flag, das angibt, ob Felder automatisch als geändert markiert werden.|
|[CDaoRecordset::m_nFields](#m_nfields)|Enthält die Anzahl der Felddatenmember in der Recordset-Klasse und die Anzahl der Spalten, die vom Recordset aus der Datenquelle ausgewählt wurden.|
|[CDaoRecordset::m_nParams](#m_nparams)|Enthält die Anzahl der Parameterdatenmember in der Recordset-Klasse – die Anzahl der Parameter, die mit der Abfrage des Recordsets übergeben wurden|
|[CDaoRecordset::m_pDAORecordset](#m_pdaorecordset)|Ein Zeiger auf die DAO-Schnittstelle, die dem Recordset-Objekt zugrunde liegt.|
|[CDaoRecordset::m_pDatabase](#m_pdatabase)|Quelldatenbank für dieses Resultset. Enthält einen Zeiger auf ein [CDaoDatabase-Objekt.](../../mfc/reference/cdaodatabase-class.md)|
|[CDaoRecordset::m_strFilter](#m_strfilter)|Enthält eine Zeichenfolge, die zum Erstellen einer SQL **WHERE-Anweisung** verwendet wird.|
|[CDaoRecordset::m_strSort](#m_strsort)|Enthält eine Zeichenfolge, die zum Erstellen einer SQL **ORDER BY-Anweisung** verwendet wird.|

## <a name="remarks"></a>Bemerkungen

Objekte, die als `CDaoRecordset` "Recordsets" bezeichnet werden, sind in den folgenden drei Formen verfügbar:

- Tabellentyp-Recordsets stellen eine Basistabelle dar, mit der Sie Datensätze aus einer einzelnen Datenbanktabelle untersuchen, hinzufügen, ändern oder löschen können.

- Dynaset-Typ-Recordsets sind das Ergebnis einer Abfrage, die über aktualisierbare Datensätze verfügen kann. Bei diesen Recordsets handelt es sich um einen Satz von Datensätzen, mit denen Sie Datensätze aus einer zugrunde liegenden Datenbanktabelle oder Tabellen untersuchen, hinzufügen, ändern oder löschen können. Recordsets vom Typ Dynaset können Felder aus einer oder mehreren Tabellen in einer Datenbank enthalten.

- Recordsets vom Typ Snapshot sind eine statische Kopie eines Satzes von Datensätzen, mit denen Sie Daten suchen oder Berichte generieren können. Diese Recordsets können Felder aus einer oder mehreren Tabellen in einer Datenbank enthalten, können jedoch nicht aktualisiert werden.

Jede Form von Recordset stellt eine Gruppe von Datensätzen dar, die zum Zeitpunkt des Öffnens des Recordsets festgelegt wurden. Wenn Sie zu einem Datensatz in einem Tabellentyp-Recordset oder einem Dynaset-Datensatzset scrollen, spiegelt er Änderungen wider, die nach dem Öffnen des Recordsets vorgenommen wurden, entweder von anderen Benutzern oder von anderen Recordsets in Ihrer Anwendung. (Ein Snapshot-Recordset kann nicht aktualisiert werden.) Sie können `CDaoRecordset` direkt verwenden oder eine anwendungsspezifische `CDaoRecordset`Recordset-Klasse von ableiten. Sie können anschließend folgende Aktionen durchführen:

- Blättern Sie durch die Datensätze.

- Legen Sie einen Index fest, und suchen Sie schnell nach Datensätzen mit [Seek](#seek) (nur Datensatzsätze vom Tabellentyp).

- Suchen Sie Datensätze basierend auf einem\<Zeichenfolgenvergleich: "<", " =", "=", ">=" oder ">" (Dynaset-Typ- und Snapshot-Recordsets).

- Aktualisieren Sie die Datensätze, und geben Sie einen Sperrmodus an (außer Snapshot-Recordsets).

- Filtern Sie das Recordset, um zu beschränken, welche Datensätze es aus den in der Datenquelle verfügbaren Datensätzen auswählt.

- Sortieren Sie das Recordset.

- Parametrierbe des Recordsets, um seine Auswahl mit Informationen anzupassen, die erst zur Laufzeit bekannt sind.

Die `CDaoRecordset` Klasse stellt eine Schnittstelle `CRecordset`bereit, die der von class ähnelt. Der Hauptunterschied besteht `CDaoRecordset` darin, dass die Klasse über ein Data Access Object (DAO) auf basisiger OLE auf Daten zugreift. Die `CRecordset` Klasse greift über Open Database Connectivity (ODBC) und einen ODBC-Treiber für dieses DBMS auf das DBMS zu.

> [!NOTE]
> Die DAO-Datenbankklassen unterscheiden sich von den MFC-Datenbankklassen, die auf Open Database Connectivity (ODBC) basieren. Alle DAO-Datenbankklassennamen haben das Präfix "CDao". Sie können weiterhin mit den DAO-Klassen auf ODBC-Datenquellen zugreifen. Die DAO-Klassen bieten im Allgemeinen überlegene Funktionen, da sie für das Microsoft Jet-Datenbankmodul spezifisch sind.

Sie können `CDaoRecordset` entweder direkt verwenden oder `CDaoRecordset`eine Klasse von ableiten. Um in beiden Fällen eine Recordset-Klasse zu verwenden, öffnen Sie eine Datenbank und `CDaoDatabase` erstellen Sie ein Recordset-Objekt, indem Sie dem Konstruktor einen Zeiger an das Objekt übergeben. Sie können auch `CDaoRecordset` ein Objekt erstellen und `CDaoDatabase` MFC ein temporäres Objekt für Sie erstellen lassen. Rufen Sie dann die [Open](#open) Open-Member-Funktion des Recordsets auf und geben an, ob es sich bei dem Objekt um ein Datensatzset vom Typ Tabellentyp, ein Recordset vom Typ Dynaset oder ein Recordset vom Typ Snapshot handelt. Beim `Open` Aufrufen werden Daten aus der Datenbank ausgewählt und der erste Datensatz abgerufen.

Verwenden Sie die Memberfunktionen und Datenmember des Objekts, um durch die Datensätze zu scrollen und sie zu bedienen. Die verfügbaren Vorgänge hängen davon ab, ob es sich bei dem Objekt um ein Datensatzset vom Tabellentyp, ein Recordset vom Typ Dynaset oder ein Recordset vom Typ Snapshot handelt und ob es aktualisierbar oder schreibgeschützt ist – dies hängt von der Fähigkeit der Datenbank oder der ODBC-Datenquelle (Open Database Connectivity) ab. Um Datensätze zu aktualisieren, die seit `Open` dem Aufruf möglicherweise geändert oder hinzugefügt wurden, rufen Sie die [Requery-Memberfunktion](#requery) des Objekts auf. Rufen Sie die `Close` Memberfunktion des Objekts auf, und zerstören Sie das Objekt, wenn Sie damit fertig sind.

`CDaoRecordset`verwendet DAO-Datensatzfeldaustausch (DFX), um das Lesen und Aktualisieren von Datensatzfeldern `CDaoRecordset` `CDaoRecordset`über typsichere C++-Member Ihrer oder -abgeleiteten Klasse zu unterstützen. Sie können auch die dynamische Bindung von Spalten in einer Datenbank implementieren, ohne den DFX-Mechanismus mit [GetFieldValue](#getfieldvalue) und [SetFieldValue](#setfieldvalue)zu verwenden.

Weitere Informationen finden Sie im Thema "Recordset-Objekt" in der DAO-Hilfe.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CDaoRecordset`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdao.h

## <a name="cdaorecordsetaddnew"></a><a name="addnew"></a>CDaoRecordset::Neu hinzufügen

Rufen Sie diese Memberfunktion auf, um einem Datensatz vom Typ Tabellentyp oder Dynaset einen neuen Datensatz hinzuzufügen.

```
virtual void AddNew();
```

### <a name="remarks"></a>Bemerkungen

Die Felder des Datensatzes sind zunächst Null. (In der Datenbankterminologie bedeutet Null "keinen Wert" und ist nicht identisch mit NULL in C++.) Um den Vorgang abzuschließen, müssen Sie die [Funktion Member aktualisieren](#update) aufrufen. `Update`speichert Ihre Änderungen in der Datenquelle.

> [!CAUTION]
> Wenn Sie einen Datensatz bearbeiten und dann `Update`zu einem anderen Datensatz scrollen, ohne aufzurufen, gehen Ihre Änderungen ohne Warnung verloren.

Wenn Sie einem Recordset vom Typ Dynaset einen Datensatz hinzufügen, indem Sie [AddNew](#addnew)aufrufen, ist der Datensatz `CDaoRecordset` im Recordset sichtbar und in der zugrunde liegenden Tabelle enthalten, in der er für alle neuen Objekte sichtbar wird.

Die Position des neuen Datensatzes hängt vom Typ des Recordsets ab:

- In einem Recordset vom Typ Dynaset, in das der neue Datensatz eingefügt wird, ist dies nicht garantiert. Dieses Verhalten hat sich mit Microsoft Jet 3.0 aus Gründen der Leistung und Parallelität geändert. Wenn Ihr Ziel darin besteht, den neu hinzugefügten Datensatz zum aktuellen Datensatz zu machen, erhalten Sie das Lesezeichen des zuletzt geänderten Datensatzes, und wechseln Sie zu diesem Lesezeichen:

[!code-cpp[NVC_MFCDatabase#1](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]

- In einem Datensatz vom Tabellentyp, für das ein Index angegeben wurde, werden Datensätze an ihrer richtigen Stelle in der Sortierreihenfolge zurückgegeben. Wenn kein Index angegeben wurde, werden am Ende des Recordsets neue Datensätze zurückgegeben.

Der Datensatz, der vor `AddNew` der Verwendung aktuell war, bleibt aktuell. Wenn Sie den neuen Datensatz aktuell machen möchten und das Recordset Lesezeichen unterstützt, rufen Sie [SetBookmark](#setbookmark) auf die Textmarke auf, die durch die LastModified-Eigenschaftseinstellung des zugrunde liegenden DAO-Recordset-Objekts identifiziert wird. Dies ist nützlich, um den Wert für Zählerfelder (auto-increment) in einem hinzugefügten Datensatz zu bestimmen. Weitere Informationen finden Sie unter [GetLastModifiedBookmark](#getlastmodifiedbookmark).

Wenn die Datenbank Transaktionen unterstützt, `AddNew` können Sie Ihren Anruf zu einem Teil einer Transaktion machen. Weitere Informationen zu Transaktionen finden Sie unter Klasse [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md). Beachten Sie, dass Sie [CDaoWorkspace::BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans) aufrufen sollten, bevor Sie anrufen. `AddNew`

Es ist unzulässig, ein Recordset aufzurufen, `AddNew` dessen [Open-Memberfunktion](#open) nicht aufgerufen wurde. A `CDaoException` wird ausgelöst, `AddNew` wenn Sie ein Recordset aufrufen, das nicht angehängt werden kann. Sie können bestimmen, ob das Recordset aktualisiert werden kann, indem Sie [CanAppend](#canappend)aufrufen.

Das Framework markiert geänderte Felddatenmember, um sicherzustellen, dass sie vom DFX-Mechanismus (DAO Record Field Exchange) in den Datensatz in der Datenquelle geschrieben werden. Wenn Sie den Wert eines Felds ändern, wird das Feld im Allgemeinen automatisch verschmutzt, sodass Sie [SetFieldDirty](#setfielddirty) selten selbst aufrufen müssen, aber Sie möchten manchmal sicherstellen, dass Spalten explizit aktualisiert oder eingefügt werden, unabhängig davon, welcher Wert sich im Felddatenelement befindet. Der DFX-Mechanismus verwendet auch die Verwendung von **PSEUDO NULL**. Weitere Informationen finden Sie unter [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Wenn der Doppelpuffermechanismus nicht verwendet wird, wird das Feld durch Ändern des Werts des Felds nicht automatisch als verschmutzt festgelegt. In diesem Fall ist es notwendig, das Feld explizit zu schmutzig zu setzen. Das in [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) enthaltene Flag steuert diese automatische Feldüberprüfung.

> [!NOTE]
> Wenn Datensätze doppelt gepuffert sind (d. h. `CancelUpdate` die automatische Feldüberprüfung aktiviert ist), werden beim Aufrufen die Membervariablen auf die Werte zurückhergestellt, die sie zuvor `AddNew` hatten oder `Edit` aufgerufen wurden.

Weitere Informationen finden Sie in den Themen "AddNew Method", "CancelUpdate Method", "LastModified Property" und "EditMode Property" in der DAO-Hilfe.

## <a name="cdaorecordsetcanappend"></a><a name="canappend"></a>CDaoRecordset::CanAppend

Rufen Sie diese Memberfunktion auf, um zu bestimmen, ob Das zuvor geöffnete Recordset das Hinzufügen neuer Datensätze ermöglicht, indem Sie die [AddNew-Memberfunktion](#addnew) aufrufen.

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Recordset das Hinzufügen neuer Datensätze zulässt; andernfalls 0. `CanAppend`gibt 0 zurück, wenn Sie das Recordset als schreibgeschützt geöffnet haben.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im Thema "Append-Methode" in der DAO-Hilfe.

## <a name="cdaorecordsetcanbookmark"></a><a name="canbookmark"></a>CDaoRecordset::CanBookmark

Rufen Sie diese Memberfunktion auf, um zu bestimmen, ob Sie mit dem zuvor geöffneten Recordset Datensätze einzeln mit Lesezeichen markieren können.

```
BOOL CanBookmark();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Recordset Lesezeichen unterstützt, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn Sie Recordsets verwenden, die vollständig auf Microsoft Jet-Datenbankmodultabellen basieren, können Lesezeichen verwendet werden, außer bei Snapshot-Recordsets, die als vorwärtsgerichtete Scrolldatensätze gekennzeichnet sind. Andere Datenbankprodukte (externe ODBC-Datenquellen) unterstützen möglicherweise keine Lesezeichen.

Weitere Informationen finden Sie im Thema "Lesezeichenable Property" in der DAO-Hilfe.

## <a name="cdaorecordsetcancelupdate"></a><a name="cancelupdate"></a>CDaoRecordset::AbbrechenUpdate

Die `CancelUpdate` Memberfunktion bricht alle ausstehenden Aktualisierungen aufgrund eines [Edit-](#edit) oder [AddNew-Vorgangs](#addnew) ab.

```
virtual void CancelUpdate();
```

### <a name="remarks"></a>Bemerkungen

Wenn z. B. `Edit` eine `AddNew` Anwendung die oder Memberfunktion aufruft und `Edit` `AddNew` nicht [Update](#update)aufgerufen hat, `CancelUpdate` werden alle Änderungen abgebrochen, die nach oder nach dem Aufruf vorgenommen wurden.

> [!NOTE]
> Wenn Datensätze doppelt gepuffert sind (d. h. `CancelUpdate` die automatische Feldüberprüfung aktiviert ist), werden beim Aufrufen die Membervariablen auf die Werte zurückhergestellt, die sie zuvor `AddNew` hatten oder `Edit` aufgerufen wurden.

Wenn kein `Edit` oder `AddNew` ein `CancelUpdate` Vorgang aussteht, wird bei MFC eine Ausnahme ausgelöst. Rufen Sie die [GetEditMode-Memberfunktion](#geteditmode) auf, um festzustellen, ob ein ausstehender Vorgang vorhanden ist, der abgebrochen werden kann.

Weitere Informationen finden Sie im Thema "CancelUpdate-Methode" in der DAO-Hilfe.

## <a name="cdaorecordsetcanrestart"></a><a name="canrestart"></a>CDaoRecordset::CanNeustart

Rufen Sie diese Memberfunktion auf, um zu bestimmen, ob das Recordset das Neustarten seiner Abfrage (zum Aktualisieren der Datensätze) ermöglicht, indem es die `Requery` Memberfunktion aufruft.

```
BOOL CanRestart();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert `Requery` ungleich Null, wenn aufgerufen werden kann, um die Abfrage des Recordsets erneut auszuführen, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Tabellentyp-Recordsets unterstützen `Requery`nicht .

Wenn `Requery` nicht unterstützt wird, rufen Sie [Close](#close) [und](#open) öffnen sie auf, um die Daten zu aktualisieren. Sie können `Requery` aufrufen, um die zugrunde liegende Parameterabfrage eines Recordset-Objekts zu aktualisieren, nachdem die Parameterwerte geändert wurden.

Weitere Informationen finden Sie im Thema "Neustartfähige Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetcanscroll"></a><a name="canscroll"></a>CDaoRecordset::CanScroll

Rufen Sie diese Memberfunktion auf, um zu bestimmen, ob das Recordset ein Bildlauf ermöglicht.

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn Sie durch die Datensätze scrollen können, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn Sie [Open](#open) Open `dbForwardOnly`with aufrufen, kann das Recordset nur vorwärts scrollen.

Weitere Informationen finden Sie im Thema "Positionieren des aktuellen Datensatzzeigers mit DAO" in der DAO-Hilfe.

## <a name="cdaorecordsetcantransact"></a><a name="cantransact"></a>CDaoRecordset::CanTransact

Rufen Sie diese Memberfunktion auf, um zu bestimmen, ob das Recordset Transaktionen zulässt.

```
BOOL CanTransact();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die zugrunde liegende Datenquelle Transaktionen unterstützt, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im Thema "Transaktionseigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetcanupdate"></a><a name="canupdate"></a>CDaoRecordset::CanUpdate

Rufen Sie diese Memberfunktion auf, um zu bestimmen, ob das Recordset aktualisiert werden kann.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Recordset aktualisiert werden kann (Datensätze hinzufügen, aktualisieren und löschen), andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Ein Recordset ist möglicherweise schreibgeschützt, wenn die zugrunde liegende `dbReadOnly` Datenquelle schreibgeschützt ist oder wenn Sie für *nOptions* angegeben haben, wenn Sie Für das Recordset [öffnen.](#open)

Weitere Informationen finden Sie in den Themen "AddNew Method", "Edit Method", "Delete Method", "Update Method" und "Updatable Property" in der DAO-Hilfe.

## <a name="cdaorecordsetcdaorecordset"></a><a name="cdaorecordset"></a>CDaoRecordset::CDaoRecordset

Erstellt ein `CDaoRecordset`-Objekt.

```
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>Parameter

*pDatabase*<br/>
Enthält einen Zeiger auf ein [CDaoDatabase-Objekt](../../mfc/reference/cdaodatabase-class.md) oder den Wert NULL. Wenn nicht NULL `CDaoDatabase` und `Open` die Memberfunktion des Objekts aufgerufen wurden, um es mit der Datenquelle zu verbinden, versucht das Recordset, es während seines eigenen [Open-Aufrufs](#open) für Sie zu öffnen. Wenn Sie NULL `CDaoDatabase` übergeben, wird ein Objekt erstellt und mit den Datenquelleninformationen verbunden, die Sie angegeben haben, wenn Sie die Recordset-Klasse von `CDaoRecordset`abgeleitet haben.

### <a name="remarks"></a>Bemerkungen

Sie können `CDaoRecordset` entweder direkt verwenden oder eine `CDaoRecordset`anwendungsspezifische Klasse von ableiten. Sie können ClassWizard verwenden, um Ihre Recordset-Klassen abzuleiten.

> [!NOTE]
> Wenn Sie eine `CDaoRecordset` Klasse ableiten, muss die abgeleitete Klasse einen eigenen Konstruktor bereitstellen. Rufen Sie im Konstruktor der abgeleiteten `CDaoRecordset::CDaoRecordset`Klasse den Konstruktor auf und übergeben Sie die entsprechenden Parameter an ihn weiter.

Übergeben Sie NULL an Ihren Recordset-Konstruktor, damit ein `CDaoDatabase` Objekt automatisch für Sie erstellt und verbunden ist. Dies ist eine nützliche Verknüpfung, für die `CDaoDatabase` Sie vor dem Erstellen des Recordsets kein Objekt erstellen und verbinden müssen. Wenn `CDaoDatabase` das Objekt nicht geöffnet ist, wird auch ein [CDaoWorkspace-Objekt](../../mfc/reference/cdaoworkspace-class.md) für Sie erstellt, das den Standardarbeitsbereich verwendet. Weitere Informationen finden Sie unter [CDaoDatabase::CDaoDatabase](../../mfc/reference/cdaodatabase-class.md#cdaodatabase).

## <a name="cdaorecordsetclose"></a><a name="close"></a>CDaoRecordset::Schließen

Durch `CDaoRecordset` das Schließen eines Objekts wird es aus der Auflistung offener Recordsets in der zugeordneten Datenbank entfernt.

```
virtual void Close();
```

### <a name="remarks"></a>Bemerkungen

Da `Close` das `CDaoRecordset` Objekt nicht zerstört wird, können `Open` Sie das Objekt wiederverwenden, indem Sie dieselbe Datenquelle oder eine andere Datenquelle aufrufen.

Alle ausstehenden [AddNew-](#addnew) oder [Edit-Anweisungen](#edit) werden abgebrochen, und alle ausstehenden Transaktionen werden zurückgesetzt. Wenn Sie ausstehende Ergänzungen oder Bearbeitungen beibehalten `Close` möchten, rufen Sie [Update](#update) auf, bevor Sie jedes Recordset aufrufen.

Sie können `Open` nach `Close`dem Aufruf erneut anrufen. Auf diese Weise können Sie das Recordset-Objekt wiederverwenden. Eine bessere Alternative ist, [Requery](#requery)aufzurufen, wenn möglich.

Weitere Informationen finden Sie im Thema "Close-Methode" in der DAO-Hilfe.

## <a name="cdaorecordsetdelete"></a><a name="delete"></a>CDaoRecordset::Delete

Rufen Sie diese Memberfunktion auf, um den aktuellen Datensatz in einem geöffneten Recordset-Objekt vom Typ Dynaset oder Tabellentyp zu löschen.

```
virtual void Delete();
```

### <a name="remarks"></a>Bemerkungen

Nach einem erfolgreichen Löschen werden die Felddatenmember des Recordsets auf einen Nullwert festgelegt, und Sie müssen explizit eine der Recordset-Navigationsmemberfunktionen aufrufen ( [Verschieben](#move), [Suchen](#seek), [SetBookmark](#setbookmark)usw.), um den gelöschten Datensatz zu entfernen. Wenn Sie Datensätze aus einem Recordset löschen, muss ein aktueller `Delete`Datensatz im Recordset vorhanden sein, bevor Sie aufrufen. Andernfalls löst MFC eine Ausnahme aus.

`Delete`entfernt den aktuellen Datensatz und macht ihn unzugänglich. Obwohl Sie den gelöschten Datensatz nicht bearbeiten oder verwenden können, bleibt er aktuell. Nachdem Sie zu einem anderen Datensatz verschoben haben, können Sie den gelöschten Datensatz jedoch nicht mehr auf den aktuellen Datensatz zurückversetzen.

> [!CAUTION]
> Das Recordset muss updaierbar sein, und beim Aufruf `Delete`muss ein gültiger Datensatz im Recordset vorhanden sein. Wenn Sie z. B. einen Datensatz löschen, aber `Delete` nicht `Delete` zu einem neuen Datensatz scrollen, bevor Sie erneut aufrufen, wird eine [CDaoException](../../mfc/reference/cdaoexception-class.md)ausgelöst.

Sie können einen Datensatz rückgängig machen, wenn Sie Transaktionen verwenden und die [CDaoWorkspace::Rollback-Memberfunktion](../../mfc/reference/cdaoworkspace-class.md#rollback) aufrufen. Wenn die Basistabelle die primäre Tabelle in einer kaskadierten Löschbeziehung ist, kann das Löschen des aktuellen Datensatzes auch einen oder mehrere Datensätze in einer fremden Tabelle löschen. Weitere Informationen finden Sie in der Definition "Kaskadenlöschen" in der DAO-Hilfe.

Im `AddNew` `Edit`Gegensatz zu `Delete` und wird einem Aufruf `Update`nicht gefolgt, der von einem Aufruf an gefolgt wird.

Weitere Informationen finden Sie in den Themen "AddNew Method", "Edit Method", "Delete Method", "Update Method" und "Updatable Property" in der DAO-Hilfe.

## <a name="cdaorecordsetdofieldexchange"></a><a name="dofieldexchange"></a>CDaoRecordset::DoFieldExchange

Das Framework ruft diese Memberfunktion auf, um automatisch Daten zwischen den Felddatenmembern des Recordset-Objekts und den entsprechenden Spalten des aktuellen Datensatzes in der Datenquelle auszutauschen.

```
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Enthält einen Zeiger `CDaoFieldExchange` auf ein Objekt. Das Framework hat dieses Objekt bereits eingerichtet, um einen Kontext für den Feldaustauschvorgang anzugeben.

### <a name="remarks"></a>Bemerkungen

Außerdem werden Ihre Parameterdatenmember, falls vorhanden, an Parameterplatzhalter in der SQL-Anweisungszeichenfolge für die Auswahl des Recordsets gebunden. Der Austausch von Felddaten, genannt DAO Record Field Exchange (DFX), funktioniert in beide Richtungen: von den Felddatenmembern des Recordset-Objekts zu den Feldern des Datensatzes in der Datenquelle und vom Datensatz in der Datenquelle bis zum Recordset-Objekt. Wenn Sie Spalten dynamisch binden, müssen `DoFieldExchange`Sie nicht implementieren.

Die einzige Aktion, die `DoFieldExchange` Sie normalerweise für die abgeleitete Recordset-Klasse implementieren müssen, besteht darin, die Klasse mit ClassWizard zu erstellen und die Namen und Datentypen der Felddatenmember anzugeben. Sie können auch Code hinzufügen, was ClassWizard schreibt, um Parameterdatenmember anzugeben. Wenn alle Felder dynamisch gebunden werden sollen, ist diese Funktion inaktiv, es sei denn, Sie geben Parameterdatenmember an.

Wenn Sie Die abgeleitete Recordset-Klasse mit ClassWizard `DoFieldExchange` deklarieren, schreibt der Assistent eine Außerkraftsetzung von für Sie, die dem folgenden Beispiel ähnelt:

[!code-cpp[NVC_MFCDatabase#2](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]

## <a name="cdaorecordsetedit"></a><a name="edit"></a>CDaoRecordset::Bearbeiten

Rufen Sie diese Memberfunktion auf, um Änderungen am aktuellen Datensatz zuzulassen.

```
virtual void Edit();
```

### <a name="remarks"></a>Bemerkungen

Nachdem Sie `Edit` die Memberfunktion aufrufen, werden Änderungen an den Feldern des aktuellen Datensatzes in den Kopierpuffer kopiert. Nachdem Sie die gewünschten Änderungen am `Update` Datensatz vorgenommen haben, rufen Sie an, um die Änderungen zu speichern. `Edit`speichert die Werte der Datenmember des Recordsets. Wenn Sie `Edit`aufrufen , Änderungen `Edit` vornehmen und dann erneut aufrufen, werden die Werte `Edit` des Datensatzes auf das zurückgestellt, was sie vor dem ersten Aufruf waren.

> [!CAUTION]
> Wenn Sie einen Datensatz bearbeiten und dann einen Vorgang `Update`ausführen, der zu einem anderen Datensatz verschoben wird, ohne zuvor aufgerufen zu haben, gehen die Änderungen ohne Warnung verloren. Wenn Sie das Recordset oder die übergeordnete Datenbank schließen, wird der bearbeitete Datensatz außerdem ohne Warnung verworfen.

In einigen Fällen können Sie eine Spalte aktualisieren, indem Sie sie null machen (ohne Daten). Rufen Sie `SetFieldNull` dazu mit dem Parameter TRUE auf, um das Feld Null zu markieren. Dadurch wird auch die Spalte aktualisiert. Wenn ein Feld in die Datenquelle geschrieben werden soll, obwohl `SetFieldDirty` sich sein Wert nicht geändert hat, rufen Sie den Aufruf mit dem Parameter TRUE auf. Dies funktioniert auch dann, wenn das Feld den Wert Null hat.

Das Framework markiert geänderte Felddatenmember, um sicherzustellen, dass sie vom DFX-Mechanismus (DAO Record Field Exchange) in den Datensatz in der Datenquelle geschrieben werden. Wenn Sie den Wert eines Felds ändern, wird das Feld im Allgemeinen automatisch verschmutzt, sodass Sie [SetFieldDirty](#setfielddirty) selten selbst aufrufen müssen, aber Sie möchten manchmal sicherstellen, dass Spalten explizit aktualisiert oder eingefügt werden, unabhängig davon, welcher Wert sich im Felddatenelement befindet. Der DFX-Mechanismus verwendet auch die Verwendung von **PSEUDO NULL**. Weitere Informationen finden Sie unter [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Wenn der Doppelpuffermechanismus nicht verwendet wird, wird das Feld durch Ändern des Werts des Felds nicht automatisch als verschmutzt festgelegt. In diesem Fall ist es notwendig, das Feld explizit zu schmutzig zu setzen. Das in [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) enthaltene Flag steuert diese automatische Feldüberprüfung.

Wenn das Recordset-Objekt pessimistisch in einer Mehrbenutzerumgebung gesperrt ist, bleibt der Datensatz von der Zeit, `Edit` die verwendet wird, bis die Aktualisierung abgeschlossen ist, gesperrt. Wenn das Recordset optimistisch gesperrt ist, wird der Datensatz gesperrt und mit dem vorbearbeiteten Datensatz verglichen, kurz bevor er in der Datenbank aktualisiert wird. Wenn sich der Datensatz `Edit`seit `Update` dem Aufruf geändert hat, schlägt der Vorgang fehl, und MFC löst eine Ausnahme aus. Sie können den Sperrmodus mit `SetLockingMode`ändern.

> [!NOTE]
> Optimistische Sperren werden immer für externe Datenbankformate wie ODBC und installierbares ISAM verwendet.

Der aktuelle Datensatz bleibt `Edit`nach dem Aufruf aktuell. Zum `Edit`Aufrufen muss ein aktueller Datensatz vorhanden sein. Wenn kein aktueller Datensatz vorhanden ist oder das Recordset nicht auf ein geöffnetes Recordset- oder Dynaset-Typ-Recordset-Objekt verweist, tritt eine Ausnahme auf. Aufruf `Edit` bewirkt, dass eine `CDaoException` unter den folgenden Bedingungen ausgelöst wird:

- Es ist kein aktueller Datensatz vorhanden.

- Die Datenbank oder das Recordset ist schreibgeschützt.

- Keine Felder im Datensatz sind aufrüstbar.

- Die Datenbank oder das Recordset wurde für die exklusive Verwendung durch einen anderen Benutzer geöffnet.

- Ein anderer Benutzer hat die Seite mit Ihrem Datensatz gesperrt.

Wenn die Datenquelle Transaktionen unterstützt, können `Edit` Sie den Aufruf zum Teil einer Transaktion machen. Beachten Sie, `CDaoWorkspace::BeginTrans` dass `Edit` Sie vor dem Aufruf und nach dem Öffnen des Recordsets anrufen sollten. Beachten Sie `CDaoWorkspace::CommitTrans` außerdem, dass der `Update` Aufruf `Edit` kein Ersatz für aufrufe, um den Vorgang abzuschließen. Weitere Informationen zu Transaktionen finden `CDaoWorkspace`Sie unter Class .

Weitere Informationen finden Sie in den Themen "AddNew Method", "Edit Method", "Delete Method", "Update Method" und "Updatable Property" in der DAO-Hilfe.

## <a name="cdaorecordsetfillcache"></a><a name="fillcache"></a>CDaoRecordset::FillCache

Rufen Sie diese Memberfunktion auf, um eine angegebene Anzahl von Datensätzen aus dem Recordset zwischenzuspeichern.

```cpp
void FillCache(
    long* pSize = NULL,
    COleVariant* pBookmark = NULL);
```

### <a name="parameters"></a>Parameter

*pSize*<br/>
Gibt die Anzahl der Zeilen an, die im Cache ausgefüllt werden sollen. Wenn Sie diesen Parameter weglassen, wird der Wert durch die CacheSize-Eigenschaftseinstellung des zugrunde liegenden DAO-Objekts bestimmt.

*pBookmark*<br/>
Ein [COleVariant,](../../mfc/reference/colevariant-class.md) der eine Textmarke angibt. Der Cache wird ausgehend von dem datensatz gefüllt, der durch dieses Lesezeichen angegeben ist. Wenn Sie diesen Parameter weglassen, wird der Cache ausgehend von dem Datensatz gefüllt, der durch die CacheStart-Eigenschaft des zugrunde liegenden DAO-Objekts angegeben wird.

### <a name="remarks"></a>Bemerkungen

Zwischenspeichern verbessert die Leistung einer Anwendung, die Daten von einem Remoteserver abruft oder abruft. Ein Cache ist Speicherplatz im lokalen Speicher, der die zuletzt vom Server abgerufenen Daten enthält, in der Annahme, dass die Daten wahrscheinlich erneut angefordert werden, während die Anwendung ausgeführt wird. Wenn Daten angefordert werden, überprüft das Microsoft Jet-Datenbankmodul den Cache zuerst auf die Daten, anstatt sie vom Server abzurufen, was mehr Zeit in Anspruch nimmt. Die Verwendung von Datenzwischenspeichern für Nicht-ODBC-Datenquellen hat keine Auswirkungen, da die Daten nicht im Cache gespeichert werden.

Anstatt darauf zu warten, dass der Cache beim Abrufen mit Datensätzen gefüllt wird, `FillCache` können Sie den Cache jederzeit explizit füllen, indem Sie die Memberfunktion aufrufen. Dies ist eine schnellere Möglichkeit, den Cache zu füllen, da `FillCache` mehrere Datensätze gleichzeitig statt nacheinander abgerufen werden. Wenn z. B. jeder Bildschirm mit Datensätzen angezeigt `FillCache` wird, können Sie ihren Anwendungsaufruf aufrufen lassen, um den nächsten Bildschirm von Datensätzen abzurufen.

Jede ODBC-Datenbank, auf die mit Recordset-Objekten zugegriffen wird, kann über einen lokalen Cache verfügen. Um den Cache zu erstellen, öffnen Sie ein Recordset-Objekt aus der Remote-Datenquelle, und rufen Sie dann die `SetCacheSize` und `SetCacheStart` Memberfunktionen des Recordsets auf. Wenn *lSize* und *lBookmark* einen Bereich erstellen, der `SetCacheSize` teilweise `SetCacheStart`oder vollständig außerhalb des von und angegebenen Bereichs liegt, wird der Teil des Recordsets außerhalb dieses Bereichs ignoriert und nicht in den Cache geladen. Wenn `FillCache` mehr Datensätze anfordern werden, als in der Remotedatenquelle verbleiben, werden nur die verbleibenden Datensätze abgerufen, und es wird keine Ausnahme ausgelöst.

Aus dem Cache abgerufene Datensätze spiegeln keine Änderungen wider, die gleichzeitig von anderen Benutzern an den Quelldaten vorgenommen wurden.

`FillCache`ruft nur Datensätze ab, die nicht bereits zwischengespeichert sind. Um eine Aktualisierung aller zwischengespeicherten Daten `SetCacheSize` zu erzwingen, rufen Sie die `SetCacheSize` Memberfunktion mit einem *lSize-Parameter* gleich 0 auf, rufen `FillCache`Sie erneut mit dem *Parameter lSize* auf, der der Größe des ursprünglich angeforderten Caches entspricht, und rufen Sie dann auf.

Weitere Informationen finden Sie im Thema "FillCache-Methode" in der DAO-Hilfe.

## <a name="cdaorecordsetfind"></a><a name="find"></a>CDaoRecordset::Suchen

Rufen Sie diese Memberfunktion auf, um eine bestimmte Zeichenfolge in einem Dynaset- oder Snapshot-Recordset mithilfe eines Vergleichsoperators zu suchen.

```
virtual BOOL Find(
    long lFindType,
    LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parameter

*lFindType*<br/>
Ein Wert, der den typ des gewünschten Findvorgangs angibt. Mögliche Werte:

- AFX_DAO_NEXT Suchen Sie den nächsten Speicherort einer übereinstimmenden Zeichenfolge.

- AFX_DAO_PREV Suchen Sie den vorherigen Speicherort einer übereinstimmenden Zeichenfolge.

- AFX_DAO_FIRST Suchen Sie den ersten Speicherort einer übereinstimmenden Zeichenfolge.

- AFX_DAO_LAST Suchen Sie die letzte Position einer übereinstimmenden Zeichenfolge.

*lpszFilter*<br/>
Ein Zeichenfolgenausdruck (wie die **WHERE-Klausel** in einer SQL-Anweisung ohne das Wort **WHERE**), der zum Suchen des Datensatzes verwendet wird. Beispiel:

[!code-cpp[NVC_MFCDatabase#3](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn übereinstimmende Datensätze gefunden werden, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie können die erste, nächste, vorherige oder letzte Instanz der Zeichenfolge finden. `Find`ist eine virtuelle Funktion, sodass Sie sie überschreiben und Eine eigene Implementierung hinzufügen können. Die `FindFirst` `FindLast`Funktionen `FindNext`, `FindPrev` , und `Find` Member rufen die `Find` Memberfunktion auf, sodass Sie das Verhalten aller Find-Vorgänge steuern können.

Um einen Datensatz in einem Datensatz vom Typ Tabellen typ zu suchen, rufen Sie die [Suchmemberfunktion](#seek) auf.

> [!TIP]
> Je kleiner der Satz von Datensätzen, die Sie haben, desto effektiver `Find` wird sein. Im Allgemeinen, insbesondere bei ODBC-Daten, ist es besser, eine neue Abfrage zu erstellen, die nur die gewünschten Datensätze abruft.

Weitere Informationen finden Sie im Thema "FindFirst, FindLast, FindNext, FindPrevious Methods" in der DAO-Hilfe.

## <a name="cdaorecordsetfindfirst"></a><a name="findfirst"></a>CDaoRecordset::FindFirst

Rufen Sie diese Memberfunktion auf, um den ersten Datensatz zu finden, der einer angegebenen Bedingung entspricht.

```
BOOL FindFirst(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parameter

*lpszFilter*<br/>
Ein Zeichenfolgenausdruck (wie die **WHERE-Klausel** in einer SQL-Anweisung ohne das Wort **WHERE**), der zum Suchen des Datensatzes verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn übereinstimmende Datensätze gefunden werden, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die `FindFirst` Memberfunktion beginnt ihre Suche vom Anfang des Recordsets und sucht bis zum Ende des Recordsets.

Wenn Sie alle Datensätze in die Suche einbeziehen möchten (nicht nur diejenigen, die eine bestimmte Bedingung erfüllen), verwenden Sie einen der Move-Vorgänge, um von Datensatz zu Datensatz zu wechseln. Rufen Sie die `Seek` Memberfunktion auf, um einen Datensatz in einem Datensatz vom Typ Tabellentyp zu suchen.

Wenn sich ein Datensatz, der den Kriterien entspricht, nicht `FindFirst` befindet, ist der aktuelle Datensatzzeiger unbestimmt und gibt Null zurück. Wenn das Recordset mehr als einen Datensatz enthält, `FindFirst` der die Kriterien `FindNext` erfüllt, sucht das erste Vorkommen, sucht das nächste Vorkommen usw.

> [!CAUTION]
> Wenn Sie den aktuellen Datensatz bearbeiten, müssen Sie `Update` die Änderungen speichern, indem Sie die Memberfunktion aufrufen, bevor Sie zu einem anderen Datensatz wechseln. Wenn Sie zu einem anderen Datensatz wechseln, ohne zu aktualisieren, gehen Ihre Änderungen ohne Warnung verloren.

Die `Find` Memberfunktionen suchen von der Position aus und in die in der folgenden Tabelle angegebene Richtung:

|Suchen von Vorgängen|Begin|Suchrichtung|
|---------------------|-----------|----------------------|
|`FindFirst`|Beginn des Recordsets|Ende des Recordsets|
|`FindLast`|Ende des Recordsets|Beginn des Recordsets|
|`FindNext`|Aktueller Datensatz|Ende des Recordsets|
|`FindPrevious`|Aktueller Datensatz|Beginn des Recordsets|

> [!NOTE]
> Wenn Sie `FindLast`aufrufen, füllt die Microsoft Jet-Datenbank-Engine Ihr Recordset vollständig auf, bevor Sie mit der Suche beginnen, sofern dies noch nicht geschehen ist. Die erste Suche kann länger dauern als nachfolgende Suchvorgänge.

Die Verwendung eines der Find-Vorgänge `MoveFirst` ist `MoveNext`jedoch nicht dasselbe wie der Aufruf oder , der den ersten oder nächsten Datensatz einfach aktuell macht, ohne eine Bedingung anzugeben. Sie können einen Find-Vorgang mit einem Move-Vorgang verfolgen.

Beachten Sie bei der Verwendung der Find-Vorgänge Folgendes:

- Wenn `Find` ein Wert ungleich Null zurückgegeben wird, ist der aktuelle Datensatz nicht definiert. In diesem Fall müssen Sie den aktuellen Datensatzzeiger wieder auf einen gültigen Datensatz positionieren.

- Sie können einen Find-Vorgang nicht mit einem vorwärts gerichteten Scrolling-Snapshot-Recordset verwenden.

- Sie sollten das US-Datumsformat (Monat-Tag-Jahr) verwenden, wenn Sie nach Feldern suchen, die Datumsangaben enthalten, auch wenn Sie die US-Version der Microsoft Jet-Datenbank-Engine nicht verwenden. Andernfalls werden möglicherweise keine übereinstimmenden Datensätze gefunden.

- Wenn Sie mit ODBC-Datenbanken und großen Dynasets arbeiten, können Sie feststellen, dass die Verwendung der Find-Vorgänge langsam ist, insbesondere wenn Sie mit großen Recordsets arbeiten. Sie können die Leistung verbessern, indem Sie SQL-Abfragen mit `CDaoQuerydef` benutzerdefinierten **ORDERBY-** oder WHERE-Klauseln, Parameterabfragen oder Objekten verwenden, die bestimmte indizierte Datensätze abrufen. **WHERE**

Weitere Informationen finden Sie im Thema "FindFirst, FindLast, FindNext, FindPrevious Methods" in der DAO-Hilfe.

## <a name="cdaorecordsetfindlast"></a><a name="findlast"></a>CDaoRecordset::FindLast

Rufen Sie diese Memberfunktion auf, um den letzten Datensatz zu finden, der einer angegebenen Bedingung entspricht.

```
BOOL FindLast(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parameter

*lpszFilter*<br/>
Ein Zeichenfolgenausdruck (wie die **WHERE-Klausel** in einer SQL-Anweisung ohne das Wort **WHERE**), der zum Suchen des Datensatzes verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn übereinstimmende Datensätze gefunden werden, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die `FindLast` Memberfunktion beginnt ihre Suche am Ende des Recordsets und sucht rückwärts zum Anfang des Recordsets.

Wenn Sie alle Datensätze in die Suche einbeziehen möchten (nicht nur diejenigen, die eine bestimmte Bedingung erfüllen), verwenden Sie einen der Move-Vorgänge, um von Datensatz zu Datensatz zu wechseln. Rufen Sie die `Seek` Memberfunktion auf, um einen Datensatz in einem Datensatz vom Typ Tabellentyp zu suchen.

Wenn sich ein Datensatz, der den Kriterien entspricht, nicht `FindLast` befindet, ist der aktuelle Datensatzzeiger unbestimmt und gibt Null zurück. Wenn das Recordset mehr als einen Datensatz enthält, `FindFirst` der die Kriterien `FindNext` erfüllt, sucht das erste Vorkommen, sucht das nächste Vorkommen nach dem ersten Vorkommen usw.

> [!CAUTION]
> Wenn Sie den aktuellen Datensatz bearbeiten, stellen Sie `Update` sicher, dass Sie die Änderungen speichern, indem Sie die Memberfunktion aufrufen, bevor Sie zu einem anderen Datensatz wechseln. Wenn Sie zu einem anderen Datensatz wechseln, ohne zu aktualisieren, gehen Ihre Änderungen ohne Warnung verloren.

Die Verwendung eines der Find-Vorgänge `MoveFirst` ist `MoveNext`jedoch nicht dasselbe wie der Aufruf oder , der den ersten oder nächsten Datensatz einfach aktuell macht, ohne eine Bedingung anzugeben. Sie können einen Find-Vorgang mit einem Move-Vorgang verfolgen.

Beachten Sie bei der Verwendung der Find-Vorgänge Folgendes:

- Wenn `Find` ein Wert ungleich Null zurückgegeben wird, ist der aktuelle Datensatz nicht definiert. In diesem Fall müssen Sie den aktuellen Datensatzzeiger wieder auf einen gültigen Datensatz positionieren.

- Sie können einen Find-Vorgang nicht mit einem vorwärts gerichteten Scrolling-Snapshot-Recordset verwenden.

- Sie sollten das US-Datumsformat (Monat-Tag-Jahr) verwenden, wenn Sie nach Feldern suchen, die Datumsangaben enthalten, auch wenn Sie die US-Version der Microsoft Jet-Datenbank-Engine nicht verwenden. Andernfalls werden möglicherweise keine übereinstimmenden Datensätze gefunden.

- Wenn Sie mit ODBC-Datenbanken und großen Dynasets arbeiten, können Sie feststellen, dass die Verwendung der Find-Vorgänge langsam ist, insbesondere wenn Sie mit großen Recordsets arbeiten. Sie können die Leistung verbessern, indem Sie SQL-Abfragen mit `CDaoQuerydef` benutzerdefinierten **ORDERBY-** oder WHERE-Klauseln, Parameterabfragen oder Objekten verwenden, die bestimmte indizierte Datensätze abrufen. **WHERE**

Weitere Informationen finden Sie im Thema "FindFirst, FindLast, FindNext, FindPrevious Methods" in der DAO-Hilfe.

## <a name="cdaorecordsetfindnext"></a><a name="findnext"></a>CDaoRecordset::FindNext

Rufen Sie diese Memberfunktion auf, um den nächsten Datensatz zu finden, der einer angegebenen Bedingung entspricht.

```
BOOL FindNext(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parameter

*lpszFilter*<br/>
Ein Zeichenfolgenausdruck (wie die **WHERE-Klausel** in einer SQL-Anweisung ohne das Wort **WHERE**), der zum Suchen des Datensatzes verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn übereinstimmende Datensätze gefunden werden, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die `FindNext` Memberfunktion beginnt mit der Suche am aktuellen Datensatz und sucht bis zum Ende des Recordsets.

Wenn Sie alle Datensätze in die Suche einbeziehen möchten (nicht nur diejenigen, die eine bestimmte Bedingung erfüllen), verwenden Sie einen der Move-Vorgänge, um von Datensatz zu Datensatz zu wechseln. Rufen Sie die `Seek` Memberfunktion auf, um einen Datensatz in einem Datensatz vom Typ Tabellentyp zu suchen.

Wenn sich ein Datensatz, der den Kriterien entspricht, nicht `FindNext` befindet, ist der aktuelle Datensatzzeiger unbestimmt und gibt Null zurück. Wenn das Recordset mehr als einen Datensatz enthält, `FindFirst` der die Kriterien `FindNext` erfüllt, sucht das erste Vorkommen, sucht das nächste Vorkommen usw.

> [!CAUTION]
> Wenn Sie den aktuellen Datensatz bearbeiten, stellen Sie `Update` sicher, dass Sie die Änderungen speichern, indem Sie die Memberfunktion aufrufen, bevor Sie zu einem anderen Datensatz wechseln. Wenn Sie zu einem anderen Datensatz wechseln, ohne zu aktualisieren, gehen Ihre Änderungen ohne Warnung verloren.

Die Verwendung eines der Find-Vorgänge `MoveFirst` ist `MoveNext`jedoch nicht dasselbe wie der Aufruf oder , der den ersten oder nächsten Datensatz einfach aktuell macht, ohne eine Bedingung anzugeben. Sie können einen Find-Vorgang mit einem Move-Vorgang verfolgen.

Beachten Sie bei der Verwendung der Find-Vorgänge Folgendes:

- Wenn `Find` ein Wert ungleich Null zurückgegeben wird, ist der aktuelle Datensatz nicht definiert. In diesem Fall müssen Sie den aktuellen Datensatzzeiger wieder auf einen gültigen Datensatz positionieren.

- Sie können einen Find-Vorgang nicht mit einem vorwärts gerichteten Scrolling-Snapshot-Recordset verwenden.

- Sie sollten das US-Datumsformat (Monat-Tag-Jahr) verwenden, wenn Sie nach Feldern suchen, die Datumsangaben enthalten, auch wenn Sie die US-Version der Microsoft Jet-Datenbank-Engine nicht verwenden. Andernfalls werden möglicherweise keine übereinstimmenden Datensätze gefunden.

- Wenn Sie mit ODBC-Datenbanken und großen Dynasets arbeiten, können Sie feststellen, dass die Verwendung der Find-Vorgänge langsam ist, insbesondere wenn Sie mit großen Recordsets arbeiten. Sie können die Leistung verbessern, indem Sie SQL-Abfragen mit `CDaoQuerydef` benutzerdefinierten **ORDERBY-** oder WHERE-Klauseln, Parameterabfragen oder Objekten verwenden, die bestimmte indizierte Datensätze abrufen. **WHERE**

Weitere Informationen finden Sie im Thema "FindFirst, FindLast, FindNext, FindPrevious Methods" in der DAO-Hilfe.

## <a name="cdaorecordsetfindprev"></a><a name="findprev"></a>CDaoRecordset::FindPrev

Rufen Sie diese Memberfunktion auf, um den vorherigen Datensatz zu finden, der einer angegebenen Bedingung entspricht.

```
BOOL FindPrev(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parameter

*lpszFilter*<br/>
Ein Zeichenfolgenausdruck (wie die **WHERE-Klausel** in einer SQL-Anweisung ohne das Wort **WHERE**), der zum Suchen des Datensatzes verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn übereinstimmende Datensätze gefunden werden, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die `FindPrev` Memberfunktion beginnt ihre Suche am aktuellen Datensatz und sucht rückwärts zum Anfang des Recordsets.

Wenn Sie alle Datensätze in die Suche einbeziehen möchten (nicht nur diejenigen, die eine bestimmte Bedingung erfüllen), verwenden Sie einen der Move-Vorgänge, um von Datensatz zu Datensatz zu wechseln. Rufen Sie die `Seek` Memberfunktion auf, um einen Datensatz in einem Datensatz vom Typ Tabellentyp zu suchen.

Wenn sich ein Datensatz, der den Kriterien entspricht, nicht `FindPrev` befindet, ist der aktuelle Datensatzzeiger unbestimmt und gibt Null zurück. Wenn das Recordset mehr als einen Datensatz enthält, `FindFirst` der die Kriterien `FindNext` erfüllt, sucht das erste Vorkommen, sucht das nächste Vorkommen usw.

> [!CAUTION]
> Wenn Sie den aktuellen Datensatz bearbeiten, stellen Sie `Update` sicher, dass Sie die Änderungen speichern, indem Sie die Memberfunktion aufrufen, bevor Sie zu einem anderen Datensatz wechseln. Wenn Sie zu einem anderen Datensatz wechseln, ohne zu aktualisieren, gehen Ihre Änderungen ohne Warnung verloren.

Die Verwendung eines der Find-Vorgänge `MoveFirst` ist `MoveNext`jedoch nicht dasselbe wie der Aufruf oder , der den ersten oder nächsten Datensatz einfach aktuell macht, ohne eine Bedingung anzugeben. Sie können einen Find-Vorgang mit einem Move-Vorgang verfolgen.

Beachten Sie bei der Verwendung der Find-Vorgänge Folgendes:

- Wenn `Find` ein Wert ungleich Null zurückgegeben wird, ist der aktuelle Datensatz nicht definiert. In diesem Fall müssen Sie den aktuellen Datensatzzeiger wieder auf einen gültigen Datensatz positionieren.

- Sie können einen Find-Vorgang nicht mit einem vorwärts gerichteten Scrolling-Snapshot-Recordset verwenden.

- Sie sollten das US-Datumsformat (Monat-Tag-Jahr) verwenden, wenn Sie nach Feldern suchen, die Datumsangaben enthalten, auch wenn Sie die US-Version der Microsoft Jet-Datenbank-Engine nicht verwenden. Andernfalls werden möglicherweise keine übereinstimmenden Datensätze gefunden.

- Wenn Sie mit ODBC-Datenbanken und großen Dynasets arbeiten, können Sie feststellen, dass die Verwendung der Find-Vorgänge langsam ist, insbesondere wenn Sie mit großen Recordsets arbeiten. Sie können die Leistung verbessern, indem Sie SQL-Abfragen mit `CDaoQuerydef` benutzerdefinierten **ORDERBY-** oder WHERE-Klauseln, Parameterabfragen oder Objekten verwenden, die bestimmte indizierte Datensätze abrufen. **WHERE**

Weitere Informationen finden Sie im Thema "FindFirst, FindLast, FindNext, FindPrevious Methods" in der DAO-Hilfe.

## <a name="cdaorecordsetgetabsoluteposition"></a><a name="getabsoluteposition"></a>CDaoRecordset::GetAbsolutePosition

Gibt die Datensatznummer des aktuellen Datensatzes eines Recordset-Objekts zurück.

```
long GetAbsolutePosition();
```

### <a name="return-value"></a>Rückgabewert

Eine ganze Zahl von 0 bis zur Anzahl der Datensätze im Recordset. Entspricht der Ordinalposition des aktuellen Datensatzes im Recordset.

### <a name="remarks"></a>Bemerkungen

Der AbsolutePosition-Eigenschaftswert des zugrunde liegenden DAO-Objekts ist nullbasiert. eine Einstellung von 0 bezieht sich auf den ersten Datensatz im Recordset. Sie können die Anzahl der ausgefüllten Datensätze im Recordset bestimmen, indem Sie [GetRecordCount](#getrecordcount)aufrufen. Der `GetRecordCount` Aufruf kann einige Zeit in Anspruch nehmen, da er auf alle Datensätze zugreifen muss, um die Anzahl zu bestimmen.

Wenn kein aktueller Datensatz vorhanden ist, wie wenn sich keine Datensätze im Recordset befinden, wird - 1 zurückgegeben. Wenn der aktuelle Datensatz gelöscht wird, wird der AbsolutePosition-Eigenschaftswert nicht definiert, und MFC löst eine Ausnahme aus, wenn darauf verwiesen wird. Bei Recordsets vom Typ Dynaset werden neue Datensätze am Ende der Sequenz hinzugefügt.

> [!NOTE]
> Diese Eigenschaft ist nicht für die Verwendung als Ersatzdatensatznummer vorgesehen. Lesezeichen sind nach wie vor die empfohlene Methode zum Beibehalten und Zurückkehren an eine bestimmte Position und die einzige Möglichkeit, den aktuellen Datensatz für alle Arten von Recordset-Objekten zu positionieren. Insbesondere ändert sich die Position eines bestimmten Datensatzes, wenn der(n) vor ihm vorangehende Datensatz(e) gelöscht wird. Es gibt auch keine Zusicherung, dass ein bestimmter Datensatz die gleiche absolute Position hat, wenn das Recordset erneut erstellt wird, da die Reihenfolge der einzelnen Datensätze innerhalb eines Recordsets nicht garantiert ist, es sei denn, er wird mit einer SQL-Anweisung unter Verwendung einer **ORDERBY-Klausel** erstellt.

> [!NOTE]
> Diese Memberfunktion ist nur für Recordsets vom Typ Dynaset und Snapshot gültig.

Weitere Informationen finden Sie im Thema "AbsolutePosition-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetgetbookmark"></a><a name="getbookmark"></a>CDaoRecordset::GetBookmark

Rufen Sie diese Memberfunktion auf, um den Lesezeichenwert in einem bestimmten Datensatz abzurufen.

```
COleVariant GetBookmark();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Wert zurück, der die Textmarke im aktuellen Datensatz darstellt.

### <a name="remarks"></a>Bemerkungen

Wenn ein Recordset-Objekt erstellt oder geöffnet wird, verfügt jeder Datensatz bereits über ein eindeutiges Lesezeichen, wenn er sie unterstützt. Rufen `CanBookmark` Sie auf, um zu bestimmen, ob ein Recordset Lesezeichen unterstützt.

Sie können die Textmarke für den aktuellen Datensatz speichern, indem `COleVariant` Sie einem Objekt den Wert der Textmarke zuweisen. Um nach dem Wechsel zu einem anderen Datensatz schnell `SetBookmark` zu diesem Datensatz zurückzukehren, `COleVariant` rufen Sie einen Parameter auf, der dem Wert dieses Objekts entspricht.

> [!NOTE]
> Der Aufruf von [Requery](#requery) ändert DAO-Lesezeichen.

Weitere Informationen finden Sie im Thema "Bookmark-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetgetcachesize"></a><a name="getcachesize"></a>CDaoRecordset::GetCacheSize

Rufen Sie diese Memberfunktion auf, um die Anzahl der zwischengespeicherten Datensätze abzurufen.

```
long GetCacheSize();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der die Anzahl der Datensätze in einem Recordset vom Typ Dynaset angibt, die Daten enthalten, die lokal aus einer ODBC-Datenquelle zwischengespeichert werden sollen.

### <a name="remarks"></a>Bemerkungen

Das Zwischenspeichern von Daten verbessert die Leistung einer Anwendung, die Daten von einem Remoteserver über Recordset-Objekte vom Typ Dynaset abruft. Ein Cache ist ein Leerspeicher im lokalen Speicher, der die zuletzt vom Server abgerufenen Daten enthält, falls die Daten erneut angefordert werden, während die Anwendung ausgeführt wird. Wenn Daten angefordert werden, überprüft das Microsoft Jet-Datenbankmodul den Cache zuerst auf die angeforderten Daten, anstatt sie vom Server abzurufen, was mehr Zeit in Anspruch nimmt. Daten, die nicht aus einer ODBC-Datenquelle stammen, werden nicht im Cache gespeichert.

Jede ODBC-Datenquelle, z. B. eine angefügte Tabelle, kann über einen lokalen Cache verfügen.

Weitere Informationen finden Sie im Thema "CacheSize, CacheStart Properties" in der DAO-Hilfe.

## <a name="cdaorecordsetgetcachestart"></a><a name="getcachestart"></a>CDaoRecordset::GetCacheStart

Rufen Sie diese Memberfunktion auf, um den Lesezeichenwert des ersten Datensatzes im zwischenzuspeichernden Recordset abzurufen.

```
COleVariant GetCacheStart();
```

### <a name="return-value"></a>Rückgabewert

A, `COleVariant` das die Textmarke des ersten Datensatzes im zwischenspeichernden Recordset angibt.

### <a name="remarks"></a>Bemerkungen

Das Microsoft Jet-Datenbankmodul fordert Datensätze innerhalb des Cachebereichs aus dem Cache an und fordert Datensätze außerhalb des Cachebereichs vom Server an.

> [!NOTE]
> Aus dem Cache abgerufene Datensätze spiegeln keine Änderungen wider, die gleichzeitig von anderen Benutzern an den Quelldaten vorgenommen wurden.

Weitere Informationen finden Sie im Thema "CacheSize, CacheStart Properties" in der DAO-Hilfe.

## <a name="cdaorecordsetgetcurrentindex"></a><a name="getcurrentindex"></a>CDaoRecordset::GetCurrentIndex

Rufen Sie diese Memberfunktion auf, um den Index `CDaoRecordset` zu bestimmen, der derzeit in einem indizierten Tabellentypobjekt verwendet wird.

```
CString GetCurrentIndex();
```

### <a name="return-value"></a>Rückgabewert

A `CString` enthält den Namen des Indexes, der derzeit mit einem Datensatzsatz vom Tabellentyp verwendet wird. Gibt eine leere Zeichenfolge zurück, wenn kein Index festgelegt wurde.

### <a name="remarks"></a>Bemerkungen

Dieser Index ist die Grundlage für die Reihenfolge von Datensätzen in einem Datensatz vom Tabellentyp und wird von der [Suchmemberfunktion](#seek) zum Suchen von Datensätzen verwendet.

Ein `CDaoRecordset` Objekt kann mehr als einen Index haben, kann jedoch jeweils nur einen Index verwenden (obwohl für ein [CDaoTableDef-Objekt](../../mfc/reference/cdaotabledef-class.md) mehrere Indizes definiert sind).

Weitere Informationen finden Sie im Thema "Indexobjekt" und in der Definition "aktueller Index" in der DAO-Hilfe.

## <a name="cdaorecordsetgetdatecreated"></a><a name="getdatecreated"></a>CDaoRecordset::GetDateCreated

Rufen Sie diese Memberfunktion auf, um das Datum und die Uhrzeit abzurufen, zu der eine Basistabelle erstellt wurde.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Rückgabewert

Ein [COleDateTime-Objekt,](../../atl-mfc-shared/reference/coledatetime-class.md) das das Datum und die Uhrzeit enthält, zu der die Basistabelle erstellt wurde.

### <a name="remarks"></a>Bemerkungen

Datums- und Uhrzeiteinstellungen werden von dem Computer abgeleitet, auf dem die Basistabelle erstellt wurde.

Weitere Informationen finden Sie im Thema "DateCreated, LastUpdated Properties" in der DAO-Hilfe.

## <a name="cdaorecordsetgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoRecordset::GetDateLastUpdated

Rufen Sie diese Memberfunktion auf, um das Datum und die Uhrzeit abzurufen, zu der das Schema zuletzt aktualisiert wurde.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Rückgabewert

Ein [COleDateTime-Objekt,](../../atl-mfc-shared/reference/coledatetime-class.md) das das Datum und die Uhrzeit enthält, zu denen die Basistabellenstruktur (Schema) zuletzt aktualisiert wurde.

### <a name="remarks"></a>Bemerkungen

Datums- und Uhrzeiteinstellungen werden von dem Computer abgeleitet, auf dem die Basistabellenstruktur (Schema) zuletzt aktualisiert wurde.

Weitere Informationen finden Sie im Thema "DateCreated, LastUpdated Properties" in der DAO-Hilfe.

## <a name="cdaorecordsetgetdefaultdbname"></a><a name="getdefaultdbname"></a>CDaoRecordset::GetDefaultDBName

Rufen Sie diese Memberfunktion auf, um den Namen der Datenbank für dieses Recordset zu bestimmen.

```
virtual CString GetDefaultDBName();
```

### <a name="return-value"></a>Rückgabewert

Eine, `CString` die den Pfad und den Namen der Datenbank enthält, von der dieses Recordset abgeleitet wird.

### <a name="remarks"></a>Bemerkungen

Wenn ein Recordset ohne Zeiger auf eine [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)erstellt wird, wird dieser Pfad vom Recordset verwendet, um die Standarddatenbank zu öffnen. Standardmäßig gibt diese Funktion eine leere Zeichenfolge zurück. Wenn ClassWizard ein neues Recordset `CDaoRecordset`von ableitet, wird diese Funktion für Sie erstellt.

Das folgende Beispiel veranschaulicht die Verwendung des\\\\doppelten umgekehrten Schrägstrichs ( ) in der Zeichenfolge, wie es erforderlich ist, damit die Zeichenfolge richtig interpretiert werden kann.

[!code-cpp[NVC_MFCDatabase#4](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]

## <a name="cdaorecordsetgetdefaultsql"></a><a name="getdefaultsql"></a>CDaoRecordset::GetDefaultSQL

Das Framework ruft diese Memberfunktion auf, um die SQL-Standardanweisung abzuruft, auf der das Recordset basiert.

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>Rückgabewert

A, `CString` das die SQL-Standardanweisung enthält.

### <a name="remarks"></a>Bemerkungen

Dies kann ein Tabellenname oder eine SQL **SELECT-Anweisung** sein.

Sie definieren indirekt die SQL-Standardanweisung, indem Sie die Recordset-Klasse mit ClassWizard deklarieren, und ClassWizard führt diese Aufgabe für Sie aus.

Wenn Sie eine NULL-SQL-Zeichenfolge an [Open](#open)übergeben, wird diese Funktion aufgerufen, um den Tabellennamen oder SQL für Ihr Recordset zu bestimmen.

## <a name="cdaorecordsetgeteditmode"></a><a name="geteditmode"></a>CDaoRecordset::GetEditMode

Rufen Sie diese Memberfunktion auf, um den Bearbeitungszustand zu bestimmen, der einer der folgenden Werte ist:

```
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

## <a name="cdaorecordsetgetfieldcount"></a><a name="getfieldcount"></a>CDaoRecordset::GetFieldCount

Rufen Sie diese Memberfunktion auf, um die Anzahl der im Recordset definierten Felder (Spalten) abzurufen.

```
short GetFieldCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Felder im Recordset.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im Thema "Count Property" in der DAO-Hilfe.

## <a name="cdaorecordsetgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoRecordset::GetFieldInfo

Rufen Sie diese Memberfunktion auf, um Informationen zu den Feldern in einem Recordset abzurufen.

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
Der nullbasierte Index des vordefinierten Feldes in der Fields-Auflistung des Recordsets für die Suche nach Index.

*Fieldinfo*<br/>
Ein Verweis auf eine [CDaoFieldInfo-Struktur.](../../mfc/reference/cdaofieldinfo-structure.md)

*dwInfoOptionen*<br/>
Optionen, die angeben, welche Informationen über das abzurufende Recordset abgerufen werden sollen. Die verfügbaren Optionen werden hier zusammen mit dem, was sie verursachen die Funktion zurückgegeben. Rufen Sie für eine optimale Leistung nur die Informationsebene ab, die Sie benötigen:

- `AFX_DAO_PRIMARY_INFO`(Standard) Name, Typ, Größe, Attribute

- `AFX_DAO_SECONDARY_INFO`Primärinformationen, plus: Ordinalposition, Erforderlich, Nulllänge zulassen, Sortierreihenfolge, Fremdname, Quellfeld, Quelltabelle

- `AFX_DAO_ALL_INFO`Primäre und sekundäre Informationen sowie: Standardwert, Validierungsregel, Validierungstext

*lpszName*<br/>
Der Name des Felds.

### <a name="remarks"></a>Bemerkungen

Mit einer Version der Funktion können Sie ein Feld nach Index suchen. Mit der anderen Version können Sie ein Feld nach Namen suchen.

Eine Beschreibung der zurückgegebenen Informationen finden Sie in der [CDaoFieldInfo-Struktur.](../../mfc/reference/cdaofieldinfo-structure.md) Diese Struktur verfügt über Member, die den oben aufgeführten Informationen in der Beschreibung von *dwInfoOptions*entsprechen. Wenn Sie Informationen auf einer Ebene anfordern, erhalten Sie auch Informationen für alle vorherigen Ebenen.

Weitere Informationen finden Sie im Thema "Attributes Property" in der DAO-Hilfe.

## <a name="cdaorecordsetgetfieldvalue"></a><a name="getfieldvalue"></a>CDaoRecordset::GetFieldValue

Rufen Sie diese Memberfunktion auf, um Daten in einem Recordset abzurufen.

```
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

*lpszName*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen eines Felds enthält.

*varValue*<br/>
Ein Verweis `COleVariant` auf ein Objekt, das den Wert eines Felds speichert.

*nIndex*<br/>
Ein nullbasierter Index des Felds in der Fields-Auflistung des Recordsets für die Suche nach Index.

### <a name="return-value"></a>Rückgabewert

Die beiden `GetFieldValue` Versionen dieser Zurückgeben eines Werts geben ein [COleVariant-Objekt](../../mfc/reference/colevariant-class.md) zurück, das den Wert eines Felds enthält.

### <a name="remarks"></a>Bemerkungen

Sie können ein Feld nach Namen oder Ordinalposition suchen.

> [!NOTE]
> Es ist effizienter, eine der Versionen dieser Memberfunktion `COleVariant` aufzurufen, die einen Objektverweis als `COleVariant` Parameter verwendet, anstatt eine Version aufzurufen, die ein Objekt zurückgibt. Die letztgenannten Versionen dieser Funktion werden aus Gründen der Abwärtskompatibilität beibehalten.

Verwenden `GetFieldValue` Sie und [SetFieldValue,](#setfieldvalue) um Felder zur Laufzeit dynamisch zu binden, anstatt Spalten mithilfe des [DoFieldExchange-Mechanismus](#dofieldexchange) statisch zu binden.

`GetFieldValue`und `DoFieldExchange` der Mechanismus kann kombiniert werden, um die Leistung zu verbessern. Verwenden Sie `GetFieldValue` diese Aufgabe beispielsweise, um einen Wert abzurufen, den Sie nur bei Bedarf benötigen, und weisen Sie diesen Aufruf einer Schaltfläche "Weitere Informationen" in der Schnittstelle zu.

Weitere Informationen finden Sie in den Themen "Feldobjekt" und "Werteigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetgetindexcount"></a><a name="getindexcount"></a>CDaoRecordset::GetIndexCount

Rufen Sie diese Memberfunktion auf, um die Anzahl der Indizes zu bestimmen, die für das Datensatzset vom Tabellentyp verfügbar sind.

```
short GetIndexCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Indizes im Datensatzsatz vom Tabellentyp.

### <a name="remarks"></a>Bemerkungen

`GetIndexCount`ist nützlich, um alle Indizes im Recordset zu durchlaufen. Verwenden Sie `GetIndexCount` zu diesem Zweck in Verbindung mit [GetIndexInfo](#getindexinfo). Wenn Sie diese Memberfunktion bei Dynaset- oder Snapshot-Recordsets aufrufen, löst MFC eine Ausnahme aus.

Weitere Informationen finden Sie im Thema "Attributes Property" in der DAO-Hilfe.

## <a name="cdaorecordsetgetindexinfo"></a><a name="getindexinfo"></a>CDaoRecordset::GetIndexInfo

Rufen Sie diese Memberfunktion auf, um verschiedene Arten von Informationen über einen Index abzurufen, der in der Basistabelle definiert ist, die einem Recordset zugrunde liegt.

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
Der nullbasierte Index in der Indexsammlung der Tabelle für die Suche nach numerischer Position.

*indexinfo*<br/>
Ein Verweis auf eine [CDaoIndexInfo-Struktur.](../../mfc/reference/cdaoindexinfo-structure.md)

*dwInfoOptionen*<br/>
Optionen, die angeben, welche Informationen über den abzurufenden Index abgerufen werden sollen. Die verfügbaren Optionen werden hier zusammen mit dem, was sie verursachen die Funktion zurückgegeben. Rufen Sie für eine optimale Leistung nur die Informationsebene ab, die Sie benötigen:

- `AFX_DAO_PRIMARY_INFO`(Standard) Name, Feldinfo, Felder

- `AFX_DAO_SECONDARY_INFO`Primärinformationen, plus: Primär, Eindeutig, Clustered, IgnoreNulls, Erforderlich, Fremd

- `AFX_DAO_ALL_INFO`Primäre und sekundäre Informationen, plus: Distinct Count

*lpszName*<br/>
Ein Zeiger auf den Namen des Indexobjekts für die Suche nach Namen.

### <a name="remarks"></a>Bemerkungen

Mit einer Version der Funktion können Sie einen Index anhand seiner Position in der Auflistung nachschlagen. Mit der anderen Version können Sie einen Index nach Namen suchen.

Eine Beschreibung der zurückgegebenen Informationen finden Sie in der [CDaoIndexInfo-Struktur.](../../mfc/reference/cdaoindexinfo-structure.md) Diese Struktur verfügt über Member, die den oben aufgeführten Informationen in der Beschreibung von *dwInfoOptions*entsprechen. Wenn Sie Informationen auf einer Ebene anfordern, erhalten Sie auch Informationen für alle vorherigen Ebenen.

Weitere Informationen finden Sie im Thema "Attributes Property" in der DAO-Hilfe.

## <a name="cdaorecordsetgetlastmodifiedbookmark"></a><a name="getlastmodifiedbookmark"></a>CDaoRecordset::GetLastModifiedBookmark

Rufen Sie diese Memberfunktion auf, um die Textmarke des zuletzt hinzugefügten oder aktualisierten Datensatzes abzurufen.

```
COleVariant GetLastModifiedBookmark();
```

### <a name="return-value"></a>Rückgabewert

A `COleVariant` enthält eine Textmarke, die den zuletzt hinzugefügten oder geänderten Datensatz angibt.

### <a name="remarks"></a>Bemerkungen

Wenn ein Recordset-Objekt erstellt oder geöffnet wird, verfügt jeder Datensatz bereits über ein eindeutiges Lesezeichen, wenn er sie unterstützt. Rufen Sie [GetBookmark](#getbookmark) auf, um zu ermitteln, ob das Recordset Lesezeichen unterstützt. Wenn das Recordset keine Lesezeichen `CDaoException` unterstützt, wird eine ausgelöst.

Wenn Sie einen Datensatz hinzufügen, wird er am Ende des Recordsets angezeigt und ist nicht der aktuelle Datensatz. Um den neuen Datensatz `GetLastModifiedBookmark` aktuell zu `SetBookmark` machen, rufen Sie den neu hinzugefügten Datensatz auf, und rufen Sie dann an, um zum neu hinzugefügten Datensatz zurückzukehren.

Weitere Informationen finden Sie im Thema "LastModified-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetgetlockingmode"></a><a name="getlockingmode"></a>CDaoRecordset::GetLockingMode

Rufen Sie diese Memberfunktion auf, um den Typ der Sperrung zu bestimmen, die für das Recordset wirksam ist.

```
BOOL GetLockingMode();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Art der Sperrung pessimistisch ist, andernfalls 0 für optimistische Datensatzsperren.

### <a name="remarks"></a>Bemerkungen

Wenn eine pessimistische Sperrung wirksam ist, wird die Datenseite mit dem Datensatz, den Sie bearbeiten, gesperrt, sobald Sie die [Funktion Member bearbeiten](#edit) aufrufen. Die Seite wird entsperrt, wenn Sie die Memberfunktion [Aktualisieren](#update) oder [Schließen](#close) oder einen der Vorgänge Verschieben oder Suchen aufrufen.

Wenn eine optimistische Sperrung wirksam ist, wird die Datenseite, die `Update` den Datensatz enthält, nur gesperrt, während der Datensatz mit der Memberfunktion aktualisiert wird.

Bei der Arbeit mit ODBC-Datenquellen ist der Sperrmodus immer optimistisch.

Weitere Informationen finden Sie in den Themen "LockEdits-Eigenschaft" und "Sperrverhalten in Mehrbenutzeranwendungen" in der DAO-Hilfe.

## <a name="cdaorecordsetgetname"></a><a name="getname"></a>CDaoRecordset::GetName

Rufen Sie diese Memberfunktion auf, um den Namen des Recordsets abzurufen.

```
CString GetName();
```

### <a name="return-value"></a>Rückgabewert

A `CString` enthält den Namen des Recordsets.

### <a name="remarks"></a>Bemerkungen

Der Name des Recordsets muss mit einem Buchstaben beginnen und darf maximal 40 Zeichen enthalten. Sie kann Zahlen und Unterstrichzeichen enthalten, darf jedoch keine Interpunktion oder Leerzeichen enthalten.

Weitere Informationen finden Sie im Thema "Name-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetgetparamvalue"></a><a name="getparamvalue"></a>CDaoRecordset::GetParamValue

Rufen Sie diese Memberfunktion auf, um den aktuellen Wert des angegebenen Parameters abzurufen, der im zugrunde liegenden DAOParameter-Objekt gespeichert ist.

```
virtual COleVariant GetParamValue(int nIndex);
virtual COleVariant GetParamValue(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Die numerische Position des Parameters im zugrunde liegenden DAOParameter-Objekt.

*lpszName*<br/>
Der Name des Parameters, dessen Wert Sie verwenden möchten.

### <a name="return-value"></a>Rückgabewert

Ein Objekt der Klasse [COleVariant,](../../mfc/reference/colevariant-class.md) das den Wert des Parameters enthält.

### <a name="remarks"></a>Bemerkungen

Sie können auf den Parameter entweder durch Den Namen oder über seine numerische Position in der Auflistung zugreifen.

Weitere Informationen finden Sie im Thema "Parameterobjekt" in der DAO-Hilfe.

## <a name="cdaorecordsetgetpercentposition"></a><a name="getpercentposition"></a>CDaoRecordset::GetPercentPosition

Wenn Sie mit einem Recordset vom Typ Dynaset `GetPercentPosition` oder Snapshot-Typ arbeiten, ist der Bewegungsumfang relativ zur Anzahl der Datensätze, auf die zugegriffen wird, wie durch aufrufen [von GetRecordCount](#getrecordcount)angegeben.

```
float GetPercentPosition();
```

### <a name="return-value"></a>Rückgabewert

Eine Zahl zwischen 0 und 100, die die ungefähre Position des aktuellen Datensatzes im Recordset-Objekt basierend auf einem Prozentsatz der Datensätze im Recordset angibt.

### <a name="remarks"></a>Bemerkungen

Sie können zum letzten Datensatz wechseln, indem Sie [MoveLast](#movelast) aufrufen, um die Grundgesamtheit aller Recordsets abzuschließen, aber dies kann eine erhebliche Zeit in Anspruch nehmen.

Sie können `GetPercentPosition` alle drei Typen von Recordset-Objekten aufrufen, einschließlich Tabellen ohne Indizes. Sie können jedoch `GetPercentPosition` keine vorwärtsgerichteten Bildlauf-Snapshots oder ein Recordset aufrufen, das von einer Pass-Through-Abfrage für eine externe Datenbank geöffnet wurde. Wenn kein aktueller Datensatz vorhanden ist oder der `CDaoException` aktuelle Datensatz gelöscht wurde, wird ein ausgelöst.

Weitere Informationen finden Sie im Thema "PercentPosition-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetgetrecordcount"></a><a name="getrecordcount"></a>CDaoRecordset::GetRecordCount

Rufen Sie diese Memberfunktion auf, um herauszufinden, auf wie viele Datensätze in einem Recordset zugegriffen wurden.

```
long GetRecordCount();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Datensätze zurück, auf die in einem Recordset-Objekt zugegriffen wird.

### <a name="remarks"></a>Bemerkungen

`GetRecordCount`gibt nicht an, wie viele Datensätze in einem Recordset vom Typ Dynaset oder Snapshot enthalten sind, bis auf alle Datensätze zugegriffen wurde. Dieser Memberfunktionsaufruf kann eine erhebliche Zeitinanspruch samminieren.

Nachdem auf den letzten Datensatz zugegriffen wurde, gibt der Rückgabewert die Gesamtzahl der nicht gelöschten Datensätze im Recordset an. Um den Zugriff auf den letzten `MoveLast` `FindLast` Datensatz zu erzwingen, rufen Sie die or-Member-Funktion für das Recordset auf. Sie können auch eine SQL-Anzahl verwenden, um die ungefähre Anzahl der Datensätze zu bestimmen, die Ihre Abfrage zurückgibt.

Wenn Ihre Anwendung Datensätze in einem Recordset vom Typ `GetRecordCount` Dynaset löscht, verringert sich der Rückgabewert von. Datensätze, die von anderen Benutzern `GetRecordCount` gelöscht wurden, werden jedoch erst angezeigt, wenn der aktuelle Datensatz in einem gelöschten Datensatz positioniert wurde. Wenn Sie eine Transaktion ausführen, die sich auf `GetRecordCount` die Datensatzanzahl auswirkt, und anschließend ein Rollback für die Buchung durchführen, wird die tatsächliche Anzahl der verbleibenden Datensätze nicht wiedergegeben.

Der Wert `GetRecordCount` von aus einem Snapshot-Datensatzsatz wird nicht durch Änderungen in den zugrunde liegenden Tabellen beeinflusst.

Der Wert `GetRecordCount` von aus einem Datensatz vom Tabellentyp gibt die ungefähre Anzahl der Datensätze in der Tabelle an und wird sofort beeinflusst, wenn Tabellendatensätze hinzugefügt und gelöscht werden.

Ein Recordset ohne Datensätze gibt den Wert 0 zurück. Wenn Sie mit angefügten Tabellen `GetRecordCount` oder ODBC-Datenbanken arbeiten, gibt immer zurück - 1. Wenn `Requery` Sie die Memberfunktion in einem `GetRecordCount` Recordset aufrufen, wird der Wert zurückgesetzt, als ob die Abfrage erneut ausgeführt würde.

Weitere Informationen finden Sie im Thema "RecordCount-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetgetsql"></a><a name="getsql"></a>CDaoRecordset::GetSQL

Rufen Sie diese Memberfunktion auf, um die SQL-Anweisung abzurufen, die zum Auswählen der Datensätze des Recordsets beim Öffnen verwendet wurde.

```
CString GetSQL() const;
```

### <a name="return-value"></a>Rückgabewert

A, `CString` das die SQL-Anweisung enthält.

### <a name="remarks"></a>Bemerkungen

Dies ist im **SELECT** Allgemeinen eine SQL SELECT-Anweisung.

Die zurückgegebene `GetSQL` Zeichenfolge unterscheidet sich in der Regel von jeder Zeichenfolge, die Sie möglicherweise an das Recordset im *lpszSQL-Parameter* an die [Open-Memberfunktion](#open) übergeben haben. Dies liegt daran, dass das Recordset eine vollständige `Open`SQL-Anweisung erstellt, basierend auf dem, was Sie an übergeben haben, was Sie mit ClassWizard angegeben haben und was Sie möglicherweise in den [m_strFilter](#m_strfilter) und [m_strSort](#m_strsort) Datenmembern angegeben haben.

> [!NOTE]
> Rufen Sie diese Memberfunktion erst nach dem Aufruf auf. `Open`

Weitere Informationen finden Sie im Thema "SQL-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetgettype"></a><a name="gettype"></a>CDaoRecordset::GetType

Rufen Sie diese Memberfunktion auf, nachdem Sie das Recordset geöffnet haben, um den Typ des Recordset-Objekts zu bestimmen.

```
short GetType();
```

### <a name="return-value"></a>Rückgabewert

Einer der folgenden Werte, der den Typ eines Recordsets angibt:

- `dbOpenTable`Tabellentyp-Recordset

- `dbOpenDynaset`Dynaset-Recordset

- `dbOpenSnapshot`Snapshot-Recordset

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im Thema "Typeigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetgetvalidationrule"></a><a name="getvalidationrule"></a>CDaoRecordset::GetValidationRule

Rufen Sie diese Memberfunktion auf, um die Regel zu bestimmen, die zum Überprüfen von Daten verwendet wird.

```
CString GetValidationRule();
```

### <a name="return-value"></a>Rückgabewert

Ein `CString` Objekt, das einen Wert enthält, der die Daten in einem Datensatz überprüft, während er geändert oder einer Tabelle hinzugefügt wird.

### <a name="remarks"></a>Bemerkungen

Diese Regel ist textbasiert und wird bei jeder Änderung der zugrunde liegenden Tabelle angewendet. Wenn die Daten nicht legal sind, löst MFC eine Ausnahme aus. Die zurückgegebene Fehlermeldung ist der Text der ValidationText-Eigenschaft des zugrunde liegenden Feldobjekts, sofern angegeben, oder der Text des Ausdrucks, der durch die ValidationRule-Eigenschaft des zugrunde liegenden Feldobjekts angegeben wird. Sie können [GetValidationText](#getvalidationtext) aufrufen, um den Text der Fehlermeldung abzurufen.

Beispielsweise kann ein Feld in einem Datensatz, das den Tag des Monats erfordert, eine Validierungsregel wie "TAG ZWISCHEN 1 UND 31" haben.

Weitere Informationen finden Sie im Thema "ValidationRule-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetgetvalidationtext"></a><a name="getvalidationtext"></a>CDaoRecordset::GetValidationText

Rufen Sie diese Memberfunktion auf, um den Text der ValidationText-Eigenschaft des zugrunde liegenden Feldobjekts abzurufen.

```
CString GetValidationText();
```

### <a name="return-value"></a>Rückgabewert

Ein `CString` Objekt, das den Text der Nachricht enthält, die angezeigt wird, wenn der Wert eines Felds nicht die Validierungsregel des zugrunde liegenden Feldobjekts erfüllt.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im Thema "ValidationText-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetisbof"></a><a name="isbof"></a>CDaoRecordset::IsBOF

Rufen Sie diese Memberfunktion auf, bevor Sie von Datensatz zu Datensatz scrollen, um zu erfahren, ob Sie vor dem ersten Datensatz des Recordsets gegangen sind.

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Recordset keine Datensätze enthält oder wenn Sie vor dem ersten Datensatz rückwärts gescrollt haben; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie können `IsBOF` auch `IsEOF` zusammen mit aufrufen, um zu bestimmen, ob das Recordset Datensätze enthält oder leer ist. Unmittelbar nach `Open`dem Aufruf gibt zurück, `IsBOF` wenn das Recordset keine Datensätze enthält, einen Wert ungleich Null. Wenn Sie ein Recordset öffnen, das mindestens einen Datensatz enthält, ist der erste Datensatz der aktuelle Datensatz und `IsBOF` gibt 0 zurück.

Wenn der erste Datensatz der aktuelle `MovePrev` `IsBOF` Datensatz ist und Sie aufrufen, wird anschließend ein Wert ungleich Null zurückgegeben. Wenn `IsBOF` ein Wert ungleich Null zurückgegeben wird und Sie aufrufen, `MovePrev`wird eine Ausnahme ausgelöst. Wenn `IsBOF` ein Wert ungleich Null zurückgegeben wird, ist der aktuelle Datensatz nicht definiert, und jede Aktion, die einen aktuellen Datensatz erfordert, führt zu einer Ausnahme.

Auswirkungen bestimmter Methoden `IsBOF` `IsEOF` und Einstellungen:

- Wenn `Open*` Sie intern aufrufen, wird der erste `MoveFirst`Datensatz im Datensatz zum aktuellen Datensatz durch Aufrufen von . Daher verursacht `Open` `IsBOF` das Aufrufen eines leeren `IsEOF` Satzes von Datensätzen und gibt einen Wert ungleich Null zurück. (In der folgenden Tabelle finden `MoveFirst` Sie `MoveLast` das Verhalten eines fehlgeschlagenen Aufrufs oder Aufrufs.)

- Alle Move-Vorgänge, die einen `IsBOF` `IsEOF` Datensatz erfolgreich finden, verursachen beide und geben 0 zurück.

- Ein `AddNew` Aufruf gefolgt `Update` von einem Aufruf, der `IsBOF` erfolgreich einen neuen Datensatz `IsEOF` einfügt, führt dazu, dass 0 zurückgegeben wird, jedoch nur, wenn er bereits ungleich Null ist. Der Zustand `IsEOF` des Willens bleibt immer unverändert. Wie vom Microsoft Jet-Datenbankmodul definiert, befindet sich der aktuelle Datensatzzeiger eines leeren Recordsets am Ende einer Datei, sodass jeder neue Datensatz nach dem aktuellen Datensatz eingefügt wird.

- Jeder `Delete` Aufruf, auch wenn er den einzigen verbleibenden Datensatz aus einem `IsBOF` `IsEOF`Recordset entfernt, ändert den Wert von oder nicht.

Diese Tabelle zeigt, welche Move-Vorgänge `IsBOF` /  `IsEOF`mit verschiedenen Kombinationen von zulässig sind.

||MoveFirst, MoveLast|MovePrev,<br /><br /> verschieben < 0|Verschieben 0|Movenext<br /><br /> verschieben > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`=nicht Null,<br /><br /> `IsEOF`=0|Zulässig|Ausnahme|Ausnahme|Zulässig|
|`IsBOF`=0,<br /><br /> `IsEOF`=ungleich Null|Zulässig|Zulässig|Ausnahme|Ausnahme|
|Beide ungleich Null|Ausnahme|Ausnahme|Ausnahme|Ausnahme|
|Beide 0|Zulässig|Zulässig|Zulässig|Zulässig|

Das Zulassen eines Verschiebungsvorgangs bedeutet nicht, dass der Vorgang einen Datensatz erfolgreich lokalisiert. Es gibt lediglich an, dass ein Versuch, den angegebenen Move-Vorgang auszuführen, zulässig ist und keine Ausnahme generiert. Der Wert `IsBOF` der `IsEOF` und Memberfunktionen kann sich als Ergebnis der versuchten Verschiebung ändern.

Die Auswirkungen von Verschiebungsvorgängen, die keinen `IsBOF` `IsEOF` Datensatz auf den Wert und die Einstellungen finden, werden in der folgenden Tabelle angezeigt.

||Isbof|Iseof|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|Nonzero|Nonzero|
|`Move` 0|Keine Änderung|Keine Änderung|
|`MovePrev`, `Move` < 0|Nonzero|Keine Änderung|
|`MoveNext`, `Move` > 0|Keine Änderung|Nonzero|

Weitere Informationen finden Sie im Thema "BOF, EOF Properties" in der DAO-Hilfe.

## <a name="cdaorecordsetisdeleted"></a><a name="isdeleted"></a>CDaoRecordset::IsDeleted

Rufen Sie diese Memberfunktion auf, um zu bestimmen, ob der aktuelle Datensatz gelöscht wurde.

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Recordset auf einem gelöschten Datensatz positioniert ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn Sie zu einem `IsDeleted` Datensatz scrollen und TRUE (ungleich Null) zurückgeben, müssen Sie zu einem anderen Datensatz scrollen, bevor Sie andere Recordset-Vorgänge ausführen können.

> [!NOTE]
> Sie müssen den gelöschten Status für Datensätze in einem Snapshot- oder Tabellentyp-Recordset nicht überprüfen. Da Datensätze nicht aus einem Snapshot gelöscht werden `IsDeleted`können, ist es nicht erforderlich, aufzurufen. Bei Datensatzsätzen vom Tabellentyp werden gelöschte Datensätze tatsächlich aus dem Recordset entfernt. Nachdem ein Datensatz entweder von Ihnen, einem anderen Benutzer oder in einem anderen Recordset gelöscht wurde, können Sie nicht zu diesem Datensatz zurückblättern. Daher ist es nicht `IsDeleted`erforderlich, anzurufen.

Wenn Sie einen Datensatz aus einem Dynaset löschen, wird er aus dem Recordset entfernt, und Sie können nicht zu diesem Datensatz zurückblättern. Wenn jedoch ein Datensatz in einem Dynaset entweder von einem anderen Benutzer oder `IsDeleted` in einem anderen Recordset, das auf derselben Tabelle basiert, gelöscht wird, wird TRUE zurückgegeben, wenn Sie später zu diesem Datensatz scrollen.

Weitere Informationen finden Sie in den Themen "Löschmethode", "LastModified-Eigenschaft" und "EditMode-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetiseof"></a><a name="iseof"></a>CDaoRecordset::IsEOF

Rufen Sie diese Memberfunktion auf, während Sie von Datensatz zu Datensatz scrollen, um zu erfahren, ob Sie über den letzten Datensatz des Recordsets hinausgegangen sind.

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Recordset keine Datensätze enthält oder wenn Sie über den letzten Datensatz hinaus gescrollt haben; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie können `IsEOF` auch aufrufen, um zu bestimmen, ob das Recordset Datensätze enthält oder leer ist. Unmittelbar nach `Open`dem Aufruf gibt zurück, `IsEOF` wenn das Recordset keine Datensätze enthält, einen Wert ungleich Null. Wenn Sie ein Recordset öffnen, das mindestens einen Datensatz enthält, ist der erste Datensatz der aktuelle Datensatz und `IsEOF` gibt 0 zurück.

Wenn der letzte Datensatz der aktuelle `MoveNext` `IsEOF` Datensatz ist, wenn Sie aufrufen, wird anschließend ein Wert ungleich Null zurückgegeben. Wenn `IsEOF` ein Wert ungleich Null zurückgegeben wird und Sie aufrufen, `MoveNext`wird eine Ausnahme ausgelöst. Wenn `IsEOF` ein Wert ungleich Null zurückgegeben wird, ist der aktuelle Datensatz nicht definiert, und jede Aktion, die einen aktuellen Datensatz erfordert, führt zu einer Ausnahme.

Auswirkungen bestimmter Methoden `IsBOF` `IsEOF` und Einstellungen:

- Wenn `Open` Sie intern aufrufen, wird der erste `MoveFirst`Datensatz im Datensatz zum aktuellen Datensatz durch Aufrufen von . Daher verursacht `Open` `IsBOF` das Aufrufen eines leeren `IsEOF` Satzes von Datensätzen und gibt einen Wert ungleich Null zurück. (In der folgenden Tabelle finden `MoveFirst` Sie das Verhalten eines fehlgeschlagenen Aufrufs.)

- Alle Move-Vorgänge, die einen `IsBOF` `IsEOF` Datensatz erfolgreich finden, verursachen beide und geben 0 zurück.

- Ein `AddNew` Aufruf gefolgt `Update` von einem Aufruf, der `IsBOF` erfolgreich einen neuen Datensatz `IsEOF` einfügt, führt dazu, dass 0 zurückgegeben wird, jedoch nur, wenn er bereits ungleich Null ist. Der Zustand `IsEOF` des Willens bleibt immer unverändert. Wie vom Microsoft Jet-Datenbankmodul definiert, befindet sich der aktuelle Datensatzzeiger eines leeren Recordsets am Ende einer Datei, sodass jeder neue Datensatz nach dem aktuellen Datensatz eingefügt wird.

- Jeder `Delete` Aufruf, auch wenn er den einzigen verbleibenden Datensatz aus einem `IsBOF` `IsEOF`Recordset entfernt, ändert den Wert von oder nicht.

Diese Tabelle zeigt, welche Move-Vorgänge `IsBOF` /  `IsEOF`mit verschiedenen Kombinationen von zulässig sind.

||MoveFirst, MoveLast|MovePrev,<br /><br /> verschieben < 0|Verschieben 0|Movenext<br /><br /> verschieben > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`=nicht Null,<br /><br /> `IsEOF`=0|Zulässig|Ausnahme|Ausnahme|Zulässig|
|`IsBOF`=0,<br /><br /> `IsEOF`=ungleich Null|Zulässig|Zulässig|Ausnahme|Ausnahme|
|Beide ungleich Null|Ausnahme|Ausnahme|Ausnahme|Ausnahme|
|Beide 0|Zulässig|Zulässig|Zulässig|Zulässig|

Das Zulassen eines Verschiebungsvorgangs bedeutet nicht, dass der Vorgang einen Datensatz erfolgreich lokalisiert. Es gibt lediglich an, dass ein Versuch, den angegebenen Move-Vorgang auszuführen, zulässig ist und keine Ausnahme generiert. Der Wert `IsBOF` der `IsEOF` und Memberfunktionen kann sich als Ergebnis der versuchten Verschiebung ändern.

Die Auswirkungen von Verschiebungsvorgängen, die keinen `IsBOF` `IsEOF` Datensatz auf den Wert und die Einstellungen finden, werden in der folgenden Tabelle angezeigt.

||Isbof|Iseof|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|Nonzero|Nonzero|
|`Move` 0|Keine Änderung|Keine Änderung|
|`MovePrev`, `Move` < 0|Nonzero|Keine Änderung|
|`MoveNext`, `Move` > 0|Keine Änderung|Nonzero|

Weitere Informationen finden Sie im Thema "BOF, EOF Properties" in der DAO-Hilfe.

## <a name="cdaorecordsetisfielddirty"></a><a name="isfielddirty"></a>CDaoRecordset::IsFieldDirty

Rufen Sie diese Memberfunktion auf, um zu bestimmen, ob das angegebene Felddatenelement eines Dynasets als "schmutzig" (geändert) gekennzeichnet wurde.

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>Parameter

*Pv*<br/>
Ein Zeiger auf das Felddatenelement, dessen Status Sie überprüfen möchten, oder NULL, um zu bestimmen, ob eines der Felder verschmutzt ist.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das angegebene Felddatenelement als "schmutzig" gekennzeichnet ist. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Daten in allen schmutzigen Felddatenelementen werden in den Datensatz in der Datenquelle `Update` übertragen, `CDaoRecordset` wenn der aktuelle `Edit` `AddNew`Datensatz durch einen Aufruf der Memberfunktion von (nach einem Aufruf von oder ) aktualisiert wird. Mit diesem Wissen können Sie weitere Schritte ausführen, z. B. das Entflaggungselement des Felddatenelements, um die Spalte zu markieren, damit sie nicht in die Datenquelle geschrieben wird.

`IsFieldDirty`wird durch `DoFieldExchange`implementiert.

## <a name="cdaorecordsetisfieldnull"></a><a name="isfieldnull"></a>CDaoRecordset::IsFieldNull

Rufen Sie diese Memberfunktion auf, um zu bestimmen, ob das angegebene Felddatenelement eines Recordsets als Null gekennzeichnet wurde.

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>Parameter

*Pv*<br/>
Ein Zeiger auf das Felddatenelement, dessen Status Sie überprüfen möchten, oder NULL, um zu bestimmen, ob eines der Felder Null ist.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das angegebene Felddatenelement als Null gekennzeichnet ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

(In der Datenbankterminologie bedeutet Null "keinen Wert" und ist nicht identisch mit NULL in C++.) Wenn ein Felddatenelement als Null gekennzeichnet ist, wird es als Spalte des aktuellen Datensatzes interpretiert, für den kein Wert vorhanden ist.

> [!NOTE]
> In bestimmten Situationen `IsFieldNull` kann die Verwendung ineffizient sein, wie das folgende Codebeispiel zeigt:

[!code-cpp[NVC_MFCDatabase#5](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]

> [!NOTE]
> Wenn Sie eine dynamische Datensatzbindung verwenden, `CDaoRecordset`ohne von abzuleiten, stellen Sie sicher, dass sie VT_NULL verwenden, wie im Beispiel gezeigt.

## <a name="cdaorecordsetisfieldnullable"></a><a name="isfieldnullable"></a>CDaoRecordset::IsFieldNullable

Rufen Sie diese Memberfunktion auf, um zu bestimmen, ob das angegebene Felddatenelement "nullable" ist (kann auf einen Nullwert festgelegt werden; C++ NULL ist nicht identisch mit Null, was in der Datenbankterminologie bedeutet, dass "kein Wert" vorhanden ist.

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>Parameter

*Pv*<br/>
Ein Zeiger auf das Felddatenelement, dessen Status Sie überprüfen möchten, oder NULL, um zu bestimmen, ob eines der Felder Null ist.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das angegebene Felddatenelement zum Nullwert gemacht werden kann. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Ein Feld, das nicht Null sein kann, muss einen Wert haben. Wenn Sie beim Hinzufügen oder Aktualisieren eines Datensatzes versuchen, ein solches Feld auf `Update` Null festzulegen, lehnt die Datenquelle das Hinzufügen oder Aktualisieren ab und löst eine Ausnahme aus. Die Ausnahme tritt `Update`auf, wenn `SetFieldNull`Sie aufrufen, nicht beim Aufrufen von .

## <a name="cdaorecordsetisopen"></a><a name="isopen"></a>CDaoRecordset::IsOpen

Rufen Sie diese Memberfunktion auf, um zu ermitteln, ob das Recordset geöffnet ist.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, `Open` `Requery` wenn die Funktion des Recordset-Objekts oder der Memberfunktion zuvor aufgerufen wurde und das Recordset nicht geschlossen wurde. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

## <a name="cdaorecordsetm_bcheckcachefordirtyfields"></a><a name="m_bcheckcachefordirtyfields"></a>CDaoRecordset::m_bCheckCacheForDirtyFields

Enthält ein Flag, das angibt, ob zwischengespeicherte Felder automatisch als "schmutzig" (geändert) und "Null" markiert werden.

### <a name="remarks"></a>Bemerkungen

Das Flag ist standardmäßig TRUE. Die Einstellung in diesem Datenmember steuert den gesamten Doppelpuffermechanismus. Wenn Sie das Flag auf TRUE setzen, können Sie die Zwischenspeicherung feldweise mithilfe des DFX-Mechanismus deaktivieren. Wenn Sie das Flag auf FALSE `SetFieldDirty` `SetFieldNull` setzen, müssen Sie anrufen und sich selbst.

Legen Sie dieses `Open`Datenelement fest, bevor Sie . Dieser Mechanismus dient in erster Linie zur Benutzerfreundlichkeit. Die Leistung kann aufgrund der doppelten Pufferung von Feldern langsamer sein, wenn Änderungen vorgenommen werden.

## <a name="cdaorecordsetm_nfields"></a><a name="m_nfields"></a>CDaoRecordset::m_nFields

Enthält die Anzahl der Felddatenmember in der Recordset-Klasse und die Anzahl der Spalten, die vom Recordset aus der Datenquelle ausgewählt wurden.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor für die Recordset-Klasse muss mit der richtigen Anzahl statisch gebundener Felder initialisiert `m_nFields` werden. ClassWizard schreibt diese Initialisierung für Sie, wenn Sie sie verwenden, um Ihre Recordset-Klasse zu deklarieren. Sie können es auch manuell schreiben.

Das Framework verwendet diese Nummer, um die Interaktion zwischen den Felddatenmembern und den entsprechenden Spalten des aktuellen Datensatzes in der Datenquelle zu verwalten.

> [!NOTE]
> Diese Nummer muss der Anzahl der `DoFieldExchange` Ausgabespalten entsprechen, die nach einem Aufruf `SetFieldType` mit dem Parameter `CDaoFieldExchange::outputColumn`registriert wurden.

Sie können Spalten dynamisch `CDaoRecordset::GetFieldValue` über `CDaoRecordset::SetFieldValue`und binden. Wenn Sie dies tun, müssen Sie `m_nFields` die Anzahl nicht erhöhen, um `DoFieldExchange` die Anzahl der DFX-Funktionsaufrufe in Ihrer Memberfunktion widerzuspiegeln.

## <a name="cdaorecordsetm_nparams"></a><a name="m_nparams"></a>CDaoRecordset::m_nParams

Enthält die Anzahl der Parameterdatenmember in der Recordset-Klasse – die Anzahl der Parameter, die mit der Abfrage des Recordsets übergeben wurden.

### <a name="remarks"></a>Bemerkungen

Wenn Ihre Recordset-Klasse Parameterdatenmember enthält, muss der Konstruktor für die Klasse *m_nParams* mit der richtigen Nummer initialisieren. Der Wert von *m_nParams* ist standardmäßig 0. Wenn Sie Parameterdatenmember hinzufügen – was Sie manuell tun müssen – müssen Sie auch manuell eine Initialisierung im Klassenkonstruktor hinzufügen, um die Anzahl der Parameter widerzuspiegeln (die mindestens so groß sein muss wie die Anzahl der ''-Platzhalter in Ihrem *m_strFilter* oder *m_strSort* Zeichenfolge).

Das Framework verwendet diese Nummer, wenn es die Abfrage des Recordsets parametrisiert.

> [!NOTE]
> Diese Nummer muss der Anzahl der "Params" entsprechen, die `DoFieldExchange` nach einem Aufruf `SetFieldType` mit dem Parameter `CFieldExchange::param`registriert wurden.

Weitere Informationen finden Sie im Thema "Parameterobjekt" in der DAO-Hilfe.

## <a name="cdaorecordsetm_pdaorecordset"></a><a name="m_pdaorecordset"></a>CDaoRecordset::m_pDAORecordset

Enthält einen Zeiger auf die OLE-Schnittstelle für das `CDaoRecordset` DAO Recordset-Objekt, das dem Objekt zugrunde liegt.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diesen Zeiger, wenn Sie direkt auf die DAO-Schnittstelle zugreifen müssen.

Weitere Informationen finden Sie im Thema "Recordset-Objekt" in der DAO-Hilfe.

## <a name="cdaorecordsetm_pdatabase"></a><a name="m_pdatabase"></a>CDaoRecordset::m_pDatabase

Enthält einen Zeiger `CDaoDatabase` auf das Objekt, über das das Recordset mit einer Datenquelle verbunden ist.

### <a name="remarks"></a>Bemerkungen

Diese Variable wird auf zwei Arten festgelegt. In der Regel übergeben Sie beim `CDaoDatabase` Erstellen des Recordset-Objekts einen Zeiger an ein bereits geöffnetes Objekt. Wenn Sie stattdessen `CDaoRecordset` NULL `CDaoDatabase` übergeben, erstellt ein Objekt für Sie und öffnet es. In beiden `CDaoRecordset` Fällen wird der Zeiger in dieser Variablen gespeichert.

Normalerweise müssen Sie den in `m_pDatabase`gespeicherten Zeiger nicht direkt verwenden. Wenn Sie jedoch eigene `CDaoRecordset`Erweiterungen für schreiben, müssen Sie möglicherweise den Zeiger verwenden. Sie benötigen z. B. den Zeiger, `CDaoException`wenn Sie Ihre eigenen (n) werfen.

Weitere Informationen finden Sie im Thema "Datenbankobjekt" in der DAO-Hilfe.

## <a name="cdaorecordsetm_strfilter"></a><a name="m_strfilter"></a>CDaoRecordset::m_strFilter

Enthält eine Zeichenfolge, die zum Erstellen der **WHERE-Klausel** einer SQL-Anweisung verwendet wird.

### <a name="remarks"></a>Bemerkungen

Es enthält nicht das reservierte Wort **WHERE,** um das Recordset zu filtern. Die Verwendung dieses Datenmembers gilt nicht für Datensatzsätze vom Tabellentyp. Die Verwendung `m_strFilter` von hat keine Auswirkungen, `CDaoQueryDef` wenn ein Recordset mit einem Zeiger geöffnet wird.

Verwenden Sie das US-Datumsformat (Monat-Tag-Jahr), wenn Sie Felder filtern, die Datumsangaben enthalten, auch wenn Sie die US-Version des Microsoft Jet-Datenbankmoduls nicht verwenden. Andernfalls werden die Daten möglicherweise nicht wie erwartet gefiltert.

Weitere Informationen finden Sie im Thema "Filtereigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetm_strsort"></a><a name="m_strsort"></a>CDaoRecordset::m_strSort

Enthält eine Zeichenfolge, die die **ORDERBY-Klausel** einer SQL-Anweisung ohne die reservierten Wörter **ORDERBY**enthält.

### <a name="remarks"></a>Bemerkungen

Sie können nach Recordset-Objekten im Dynaset- und Snapshot-Typ sortieren.

Sie können Recordset-Objekte vom Tabellentyp nicht sortieren. Um die Sortierreihenfolge eines Datensatzes vom Typ Tabellen zu bestimmen, rufen Sie [SetCurrentIndex](#setcurrentindex)auf.

Die Verwendung von *m_strSort* hat keine Auswirkungen, `CDaoQueryDef` wenn ein Recordset mit einem Zeiger geöffnet wird.

Weitere Informationen finden Sie im Thema "Eigenschaft sortieren" in der DAO-Hilfe.

## <a name="cdaorecordsetmove"></a><a name="move"></a>CDaoRecordset::Bewegen

Rufen Sie diese Memberfunktion auf, um die *Recordset-lRows-Datensätze* aus dem aktuellen Datensatz zu positionieren.

```
virtual void Move(long lRows);
```

### <a name="parameters"></a>Parameter

*lRows*<br/>
Die Anzahl der Datensätze, die vorwärts oder rückwärts verschoben werden sollen. Positive Werte bewegen sich vorwärts, gegen Ende des Recordsets. Negative Werte bewegen sich rückwärts, zum Anfang.

### <a name="remarks"></a>Bemerkungen

Sie können vorwärts oder rückwärts gehen. `Move( 1 )`entspricht `MoveNext`dem `Move( -1 )` `MovePrev`von , und entspricht .

> [!CAUTION]
> Wenn eine `Move` der Funktionen aufgerufen wird, wird eine Ausnahme ausgelöst, wenn das Recordset keine Datensätze enthält. Rufen Sie im `IsBOF` `IsEOF` Allgemeinen sowohl und vor einem Move-Vorgang auf, um zu ermitteln, ob das Recordset über Datensätze verfügt. Nachdem Sie `Open` `Requery`angerufen haben `IsBOF` `IsEOF`oder anrufen Sie entweder oder .

> [!NOTE]
> Wenn Sie am Anfang oder Ende des Recordsets `IsEOF` (oder einem Wert `Move` ungleich Null) vorbeigescrollt haben, `CDaoException` `IsBOF` wird ein Aufruf zum Auswerfen einer ausgelöst.

> [!NOTE]
> Wenn Sie eine `Move` der Funktionen aufrufen, während der aktuelle Datensatz aktualisiert oder hinzugefügt wird, gehen die Aktualisierungen ohne Warnung verloren.

Wenn Sie `Move` einen Vorwärts-Scrolling-Snapshot aufrufen, muss der *lRows-Parameter* eine positive ganze Zahl sein, und Lesezeichen sind nicht zulässig, sodass Sie nur vorwärts gehen können.

Um den ersten, letzten, nächsten oder vorherigen Datensatz in einem `MoveFirst`Recordset `MoveNext`zum `MovePrev` aktuellen Datensatz zu machen, rufen Sie die Funktion , `MoveLast`, , oder Member auf.

Weitere Informationen finden Sie in den Themen "Move Method" und "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" in der DAO-Hilfe.

## <a name="cdaorecordsetmovefirst"></a><a name="movefirst"></a>CDaoRecordset::MoveFirst

Rufen Sie diese Memberfunktion auf, um den ersten Datensatz im Recordset (falls vorhanden) zum aktuellen Datensatz zu machen.

```cpp
void MoveFirst();
```

### <a name="remarks"></a>Bemerkungen

Sie müssen nicht `MoveFirst` sofort anrufen, nachdem Sie das Recordset geöffnet haben. Zu diesem Zeitpunkt ist der erste Datensatz (falls vorhanden) automatisch der aktuelle Datensatz.

> [!CAUTION]
> Wenn eine `Move` der Funktionen aufgerufen wird, wird eine Ausnahme ausgelöst, wenn das Recordset keine Datensätze enthält. Rufen Sie im `IsBOF` `IsEOF` Allgemeinen sowohl und vor einem Move-Vorgang auf, um zu ermitteln, ob das Recordset über Datensätze verfügt. Nachdem Sie `Open` `Requery`angerufen haben `IsBOF` `IsEOF`oder anrufen Sie entweder oder .

> [!NOTE]
> Wenn Sie eine `Move` der Funktionen aufrufen, während der aktuelle Datensatz aktualisiert oder hinzugefügt wird, gehen die Aktualisierungen ohne Warnung verloren.

Verwenden `Move` Sie die Funktionen, um von Datensatz zu Datensatz zu wechseln, ohne eine Bedingung anzuwenden. Verwenden Sie die Suchvorgänge, um Datensätze in einem Recordset-Objekt vom Typ Dynaset oder Snapshot zu suchen, die eine bestimmte Bedingung erfüllen. Um einen Datensatz in einem Recordset-Objekt `Seek`vom Tabellentyp zu suchen, rufen Sie auf.

Wenn sich das Recordset auf ein Datensatzset vom Tabellentyp bezieht, folgt die Bewegung dem aktuellen Index der Tabelle. Sie können den aktuellen Index mithilfe der Index-Eigenschaft des zugrunde liegenden DAO-Objekts festlegen. Wenn Sie den aktuellen Index nicht festlegen, ist die Reihenfolge der zurückgegebenen Datensätze nicht definiert.

Wenn Sie `MoveLast` ein Recordset-Objekt aufrufen, das auf einer SQL-Abfrage oder querydef basiert, wird die Abfrage zum Abschluss gezwungen, und das Recordset-Objekt ist vollständig aufgefüllt.

Sie können `MoveFirst` die `MovePrev` oder Memberfunktion nicht mit einem vorwärts gerichteten Bildlauf-Snapshot aufrufen.

Um die Position des aktuellen Datensatzes in einem Recordset-Objekt um `Move`eine bestimmte Anzahl von Datensätzen vorwärts oder rückwärts zu verschieben, rufen Sie an.

Weitere Informationen finden Sie in den Themen "Move Method" und "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" in der DAO-Hilfe.

## <a name="cdaorecordsetmovelast"></a><a name="movelast"></a>CDaoRecordset::MoveLast

Rufen Sie diese Memberfunktion auf, um den letzten Datensatz (falls vorhanden) im Recordset zum aktuellen Datensatz zu machen.

```cpp
void MoveLast();
```

### <a name="remarks"></a>Bemerkungen

> [!CAUTION]
> Wenn eine `Move` der Funktionen aufgerufen wird, wird eine Ausnahme ausgelöst, wenn das Recordset keine Datensätze enthält. Rufen Sie im `IsBOF` `IsEOF` Allgemeinen sowohl und vor einem Move-Vorgang auf, um zu ermitteln, ob das Recordset über Datensätze verfügt. Nachdem Sie `Open` `Requery`angerufen haben `IsBOF` `IsEOF`oder anrufen Sie entweder oder .

> [!NOTE]
> Wenn Sie eine `Move` der Funktionen aufrufen, während der aktuelle Datensatz aktualisiert oder hinzugefügt wird, gehen die Aktualisierungen ohne Warnung verloren.

Verwenden `Move` Sie die Funktionen, um von Datensatz zu Datensatz zu wechseln, ohne eine Bedingung anzuwenden. Verwenden Sie die Suchvorgänge, um Datensätze in einem Recordset-Objekt vom Typ Dynaset oder Snapshot zu suchen, die eine bestimmte Bedingung erfüllen. Um einen Datensatz in einem Recordset-Objekt `Seek`vom Tabellentyp zu suchen, rufen Sie auf.

Wenn sich das Recordset auf ein Datensatzset vom Tabellentyp bezieht, folgt die Bewegung dem aktuellen Index der Tabelle. Sie können den aktuellen Index mithilfe der Index-Eigenschaft des zugrunde liegenden DAO-Objekts festlegen. Wenn Sie den aktuellen Index nicht festlegen, ist die Reihenfolge der zurückgegebenen Datensätze nicht definiert.

Wenn Sie `MoveLast` ein Recordset-Objekt aufrufen, das auf einer SQL-Abfrage oder querydef basiert, wird die Abfrage zum Abschluss gezwungen, und das Recordset-Objekt ist vollständig aufgefüllt.

Um die Position des aktuellen Datensatzes in einem Recordset-Objekt um `Move`eine bestimmte Anzahl von Datensätzen vorwärts oder rückwärts zu verschieben, rufen Sie an.

Weitere Informationen finden Sie in den Themen "Move Method" und "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" in der DAO-Hilfe.

## <a name="cdaorecordsetmovenext"></a><a name="movenext"></a>CDaoRecordset::MoveNext

Rufen Sie diese Memberfunktion auf, um den nächsten Datensatz im Recordset zum aktuellen Datensatz zu machen.

```cpp
void MoveNext();
```

### <a name="remarks"></a>Bemerkungen

Es wird empfohlen, `IsBOF` dass Sie anrufen, bevor Sie versuchen, zum vorherigen Datensatz zu wechseln. Ein Aufruf `MovePrev` an `CDaoException` wird `IsBOF` eine wenn zurückwirft, die ungleich Null zurückgibt, was entweder angibt, dass Sie bereits vor dem ersten Datensatz gescrollt haben oder dass keine Datensätze vom Recordset ausgewählt wurden.

> [!CAUTION]
> Wenn eine `Move` der Funktionen aufgerufen wird, wird eine Ausnahme ausgelöst, wenn das Recordset keine Datensätze enthält. Rufen Sie im `IsBOF` `IsEOF` Allgemeinen sowohl und vor einem Move-Vorgang auf, um zu ermitteln, ob das Recordset über Datensätze verfügt. Nachdem Sie `Open` `Requery`angerufen haben `IsBOF` `IsEOF`oder anrufen Sie entweder oder .

> [!NOTE]
> Wenn Sie eine `Move` der Funktionen aufrufen, während der aktuelle Datensatz aktualisiert oder hinzugefügt wird, gehen die Aktualisierungen ohne Warnung verloren.

Verwenden `Move` Sie die Funktionen, um von Datensatz zu Datensatz zu wechseln, ohne eine Bedingung anzuwenden. Verwenden Sie die Suchvorgänge, um Datensätze in einem Recordset-Objekt vom Typ Dynaset oder Snapshot zu suchen, die eine bestimmte Bedingung erfüllen. Um einen Datensatz in einem Recordset-Objekt `Seek`vom Tabellentyp zu suchen, rufen Sie auf.

Wenn sich das Recordset auf ein Datensatzset vom Tabellentyp bezieht, folgt die Bewegung dem aktuellen Index der Tabelle. Sie können den aktuellen Index mithilfe der Index-Eigenschaft des zugrunde liegenden DAO-Objekts festlegen. Wenn Sie den aktuellen Index nicht festlegen, ist die Reihenfolge der zurückgegebenen Datensätze nicht definiert.

Um die Position des aktuellen Datensatzes in einem Recordset-Objekt um `Move`eine bestimmte Anzahl von Datensätzen vorwärts oder rückwärts zu verschieben, rufen Sie an.

Weitere Informationen finden Sie in den Themen "Move Method" und "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" in der DAO-Hilfe.

## <a name="cdaorecordsetmoveprev"></a><a name="moveprev"></a>CDaoRecordset::MovePrev

Rufen Sie diese Memberfunktion auf, um den vorherigen Datensatz im Recordset zum aktuellen Datensatz zu machen.

```cpp
void MovePrev();
```

### <a name="remarks"></a>Bemerkungen

Es wird empfohlen, `IsBOF` dass Sie anrufen, bevor Sie versuchen, zum vorherigen Datensatz zu wechseln. Ein Aufruf `MovePrev` an `CDaoException` wird `IsBOF` eine wenn zurückwirft, die ungleich Null zurückgibt, was entweder angibt, dass Sie bereits vor dem ersten Datensatz gescrollt haben oder dass keine Datensätze vom Recordset ausgewählt wurden.

> [!CAUTION]
> Wenn eine `Move` der Funktionen aufgerufen wird, wird eine Ausnahme ausgelöst, wenn das Recordset keine Datensätze enthält. Rufen Sie im `IsBOF` `IsEOF` Allgemeinen sowohl und vor einem Move-Vorgang auf, um zu ermitteln, ob das Recordset über Datensätze verfügt. Nachdem Sie `Open` `Requery`angerufen haben `IsBOF` `IsEOF`oder anrufen Sie entweder oder .

> [!NOTE]
> Wenn Sie eine `Move` der Funktionen aufrufen, während der aktuelle Datensatz aktualisiert oder hinzugefügt wird, gehen die Aktualisierungen ohne Warnung verloren.

Verwenden `Move` Sie die Funktionen, um von Datensatz zu Datensatz zu wechseln, ohne eine Bedingung anzuwenden. Verwenden Sie die Suchvorgänge, um Datensätze in einem Recordset-Objekt vom Typ Dynaset oder Snapshot zu suchen, die eine bestimmte Bedingung erfüllen. Um einen Datensatz in einem Recordset-Objekt `Seek`vom Tabellentyp zu suchen, rufen Sie auf.

Wenn sich das Recordset auf ein Datensatzset vom Tabellentyp bezieht, folgt die Bewegung dem aktuellen Index der Tabelle. Sie können den aktuellen Index mithilfe der Index-Eigenschaft des zugrunde liegenden DAO-Objekts festlegen. Wenn Sie den aktuellen Index nicht festlegen, ist die Reihenfolge der zurückgegebenen Datensätze nicht definiert.

Sie können `MoveFirst` die `MovePrev` oder Memberfunktion nicht mit einem vorwärts gerichteten Bildlauf-Snapshot aufrufen.

Um die Position des aktuellen Datensatzes in einem Recordset-Objekt um `Move`eine bestimmte Anzahl von Datensätzen vorwärts oder rückwärts zu verschieben, rufen Sie an.

Weitere Informationen finden Sie in den Themen "Move Method" und "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" in der DAO-Hilfe.

## <a name="cdaorecordsetopen"></a><a name="open"></a>CDaoRecordset::Öffnen

Sie müssen diese Memberfunktion aufrufen, um die Datensätze für das Recordset abzurufen.

```
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

- `dbOpenDynaset`Ein Recordset vom Typ Dynaset mit bidirektionazielem Scrollen. Dies ist die Standardoption.

- `dbOpenTable`Ein Datensatz vom Typ Tabellen typ mit bidirektionazielem Scrollen.

- `dbOpenSnapshot`Ein Snapshot-Recordset mit bidirektionazielem Scrollen.

*Lpszsql*<br/>
Eine Zeichenfolge, in der eines der folgenden Elemente enthalten ist:

- Ein NULL-Zeiger.

- Der Name eines oder mehrerer tabledefs und/oder querydefs (kommasgetrennt).

- Eine SQL **SELECT-Anweisung** (optional mit einer SQL **WHERE-** oder **ORDERBY-Klausel).**

- Eine Pass-Through-Abfrage.

*nOptionen*<br/>
Eine oder mehrere der unten aufgeführten Optionen. Der Standardwert ist 0. Folgende Werte sind möglich:

- `dbAppendOnly`Sie können nur neue Datensätze anhängen (nur ein Recordset vom Typ Dynaset). Diese Option bedeutet buchstäblich, dass Datensätze nur angehängt werden dürfen. Die MFC ODBC-Datenbankklassen verfügen über eine Nur-Anfügt-Option, mit der Datensätze abgerufen und angehängt werden können.

- `dbForwardOnly`Das Recordset ist ein Vorwärts-Bildlauf-Snapshot.

- `dbSeeChanges`Generieren Sie eine Ausnahme, wenn ein anderer Benutzer die von Ihnen bearbeiteten Daten ändert.

- `dbDenyWrite`Andere Benutzer können keine Datensätze ändern oder hinzufügen.

- `dbDenyRead`Andere Benutzer können keine Datensätze anzeigen (nur Datensatzsätze vom Tabellentyp).

- `dbReadOnly`Sie können nur Datensätze anzeigen. andere Benutzer können sie ändern.

- `dbInconsistent`Inkonsistente Aktualisierungen sind zulässig (nur Recordset vom Typ Dynaset).

- `dbConsistent`Nur konsistente Aktualisierungen sind zulässig (nur Recordset vom Typ Dynaset).

> [!NOTE]
> Die `dbConsistent` Konstanten `dbInconsistent` und schließen sich gegenseitig aus. Sie können die eine oder andere verwenden, jedoch `Open`nicht beides in einer bestimmten Instanz von .

*pTableDef*<br/>
Ein Zeiger auf ein [CDaoTableDef-Objekt.](../../mfc/reference/cdaotabledef-class.md) Diese Version ist nur für Datensatzsätze vom Tabellentyp gültig. Wenn Sie diese `CDaoDatabase` Option verwenden, wird `CDaoRecordset` der Zeiger, der zum Erstellen des verwendet wird, nicht verwendet. Stattdessen wird die Datenbank verwendet, in der sich die tabledef befindet.

*pQueryDef*<br/>
Ein Zeiger auf ein [CDaoQueryDef-Objekt.](../../mfc/reference/cdaoquerydef-class.md) Diese Version ist nur für Recordsets vom Typ Dynaset und Snapshot gültig. Wenn Sie diese `CDaoDatabase` Option verwenden, wird `CDaoRecordset` der Zeiger, der zum Erstellen des verwendet wird, nicht verwendet. Stattdessen wird die Datenbank verwendet, in der sich die querydef befindet.

### <a name="remarks"></a>Bemerkungen

Vor `Open`dem Aufruf müssen Sie das Recordset-Objekt erstellen. Dafür stehen verschiedene Möglichkeiten zur Verfügung:

- Wenn Sie das Recordset-Objekt erstellen, `CDaoDatabase` übergeben Sie einen Zeiger an ein Objekt, das bereits geöffnet ist.

- Wenn Sie das Recordset-Objekt erstellen, `CDaoDatabase` übergeben Sie einen Zeiger an ein Objekt, das nicht geöffnet ist. Das Recordset `CDaoDatabase` öffnet ein Objekt, schließt es jedoch nicht, wenn das Recordset-Objekt geschlossen wird.

- Wenn Sie das Recordset-Objekt erstellen, übergeben Sie einen NULL-Zeiger. Das Recordset-Objekt ruft `GetDefaultDBName` auf, um den Namen von Microsoft Access abzubekommen. MDB-Datei zu öffnen. Das Recordset öffnet `CDaoDatabase` dann ein Objekt und hält es geöffnet, solange das Recordset geöffnet ist. Wenn Sie `Close` das Recordset `CDaoDatabase` aufrufen, wird das Objekt ebenfalls geschlossen.

    > [!NOTE]
    >  Wenn das Recordset `CDaoDatabase` das Objekt öffnet, öffnet es die Datenquelle mit nicht exklusivem Zugriff.

Für die `Open` Version, die den *Parameter lpszSQL* verwendet, können Sie nach dem Öffnen des Recordsets Datensätze auf eine von mehreren Arten abrufen. Die erste Option ist, DFX-Funktionen in Ihrem `DoFieldExchange`zu haben. Die zweite Option besteht darin, `GetFieldValue` die dynamische Bindung zu verwenden, indem die Memberfunktion aufgerufen wird. Diese Optionen können separat oder in Kombination implementiert werden. Wenn sie kombiniert werden, müssen Sie die SQL-Anweisung `Open`selbst beim Aufruf von übergeben.

Wenn Sie die zweite `Open` Version verwenden, `CDaoTableDef` in der Sie ein Objekt übergeben, `DoFieldExchange` stehen Ihnen die resultierenden Spalten `GetFieldValue`zum Binden über und den DFX-Mechanismus und/oder dynamisch über zur Verfügung.

> [!NOTE]
> Sie können `Open` nur `CDaoTableDef` mit einem Objekt für Tabellentyp-Recordsets aufrufen.

Wenn Sie die dritte `Open` Version verwenden, `CDaoQueryDef` in der Sie ein Objekt übergeben, wird diese Abfrage ausgeführt, und die resultierenden Spalten stehen Ihnen zum Binden über `DoFieldExchange` und den DFX-Mechanismus und/oder dynamisch über zur `GetFieldValue`Verfügung.

> [!NOTE]
> Sie können `Open` nur `CDaoQueryDef` mithilfe eines Objekts für Recordsets vom Typ Dynaset und Snapshot aufrufen.

Für die erste `Open` Version, `lpszSQL` die den Parameter verwendet, werden Datensätze basierend auf den in der folgenden Tabelle angegebenen Kriterien ausgewählt.

|Der Wert des Parameters `lpszSQL`.|Die ausgewählten Datensätze werden von folgenden Aspekten bestimmt:|Beispiel|
|--------------------------------------|----------------------------------------|-------------|
|NULL|Die von `GetDefaultSQL` zurückgegebene Zeichenfolge.||
|Eine durch Kommas getrennte Liste mit einem oder mehreren tabledefs- und/oder querydef-Namen.|Alle Spalten, `DoFieldExchange`die im dargestellt werden.|`"Customer"`|
|**SELECT-Spaltenliste** **VON** Tabellenliste|Die angegebenen Spalten aus den angegebenen tabledef(s) und/oder querydef(s).|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|

Das übliche Verfahren ist, `Open`NULL an zu übergeben; Ruft in `Open` diesem `GetDefaultSQL`Fall eine überschreibbare Memberfunktion auf, `CDaoRecordset`die ClassWizard beim Erstellen einer -derived-Klasse generiert. Dieser Wert gibt die tabledef(s) und/oder querydef-Namen an, die Sie in ClassWizard angegeben haben. Sie können stattdessen andere Informationen im Parameter *lpszSQL* angeben.

Unabhängig davon, `Open` was Sie übergeben, erstellt eine letzte SQL-Zeichenfolge für die Abfrage (die Zeichenfolge kann SQL **WHERE-** und **ORDERBY-Klauseln** an die *übergebene lpszSQL-Zeichenfolge* angehängt haben) und führt dann die Abfrage aus. Sie können die konstruierte `GetSQL` Zeichenfolge `Open`überprüfen, indem Sie nach dem Aufruf aufrufen.

Die Felddatenmember der Recordset-Klasse sind an die Spalten der ausgewählten Daten gebunden. Falls Datensätze zurückgegeben werden, wird der erste Datensatz zum aktuellen Datensatz.

Wenn Sie Optionen für das Recordset festlegen möchten, z. `m_strFilter` B. einen Filter oder eine `Open`Sortierung, legen Sie oder `m_strSort` nach dem Erstellen des Recordset-Objekts fest, aber vor dem Aufruf . Wenn Sie die Datensätze im Recordset aktualisieren möchten, nachdem `Requery`das Recordset bereits geöffnet ist, rufen Sie an.

Wenn Sie `Open` ein Recordset vom Typ Dynaset oder Snapshot aufrufen oder wenn die Datenquelle auf eine SQL-Anweisung oder `dbOpenTable` eine tabledef verweist, die eine angefügte Tabelle darstellt, können Sie das Typargument nicht verwenden. Wenn Sie dies tun, löst MFC eine Ausnahme aus. Um zu bestimmen, ob ein tabledef-Objekt eine angefügte Tabelle darstellt, erstellen Sie ein [CDaoTableDef-Objekt,](../../mfc/reference/cdaotabledef-class.md) und rufen Sie die [GetConnect-Memberfunktion](../../mfc/reference/cdaotabledef-class.md#getconnect) auf.

Verwenden `dbSeeChanges` Sie das Flag, wenn Sie Änderungen, die von einem anderen Benutzer oder einem anderen Programm auf Ihrem Computer vorgenommen wurden, beim Bearbeiten oder Löschen desselben Datensatzes abfangen möchten. Wenn z. B. zwei Benutzer mit der Bearbeitung desselben `Update` Datensatzes beginnen, ist der erste Benutzer, der die Memberfunktion aufruft, erfolgreich. Wenn `Update` der zweite Benutzer aufgerufen `CDaoException` wird, wird eine ausgelöst. Wenn der zweite Benutzer versucht, den Datensatz aufzurufen, `Delete` und er vom ersten `CDaoException` Benutzer bereits geändert wurde, tritt eine auf.

Wenn der Benutzer dies `CDaoException` während der Aktualisierung erhält, sollte der Code in der Regel den Inhalt der Felder aktualisieren und die neu geänderten Werte abrufen. Wenn die Ausnahme beim Löschen auftritt, kann der Code dem Benutzer die neuen Datensatzdaten und eine Meldung anzeigen, die darauf hinweist, dass sich die Daten kürzlich geändert haben. An dieser Stelle kann Ihr Code eine Bestätigung anfordern, dass der Benutzer den Datensatz weiterhin löschen möchte.

> [!TIP]
> Verwenden Sie die Option nur`dbForwardOnly`vorwärts scrollen ( ), um die Leistung zu verbessern, wenn Ihre Anwendung einen einzelnen Durchlauf durch ein Recordset durchführt, das von einer ODBC-Datenquelle geöffnet wird.

Weitere Informationen finden Sie im Thema "OpenRecordset-Methode" in der DAO-Hilfe.

## <a name="cdaorecordsetrequery"></a><a name="requery"></a>CDaoRecordset::Requery

Rufen Sie diese Memberfunktion auf, um ein Recordset neu zu erstellen (aktualisieren).

```
virtual void Requery();
```

### <a name="remarks"></a>Bemerkungen

Falls Datensätze zurückgegeben werden, wird der erste Datensatz zum aktuellen Datensatz.

Damit das Recordset die Hinzufügungen und Löschungen widerspiegelt, die Sie oder andere Benutzer an `Requery`der Datenquelle vorgenommen haben, müssen Sie das Recordset durch Aufrufen neu erstellen. Wenn es sich bei dem Recordset um ein Dynaset handelt, werden automatisch Aktualisierungen widergespiegelt, die Sie oder andere Benutzer an den vorhandenen Datensätzen (jedoch nicht an Ergänzungen) vornehmen. Wenn es sich bei dem Recordset um einen Snapshot handelt, müssen Sie aufrufen, `Requery` um Bearbeitungen anderer Benutzer sowie Ergänzungen und Löschungen widerzuspiegeln.

Rufen Sie für ein Dynaset `Requery` oder einen Snapshot jederzeit auf, wenn Sie das Recordset mithilfe von Parameterwerten neu erstellen möchten. Legen Sie den neuen Filter oder die `Requery`neue Sortierung fest, indem Sie [m_strFilter](#m_strfilter) und [m_strSort](#m_strsort) vor dem Aufruf festlegen. Legen Sie neue Parameter fest, indem Sie `Requery`parameterdatenmembern neue Werte zuweisen, bevor Sie aufrufen.

Wenn der Versuch, das Recordset neu zu erstellen, fehlschlägt, wird das Recordset geschlossen. Bevor Sie `Requery`aufrufen, können Sie bestimmen, ob das Recordset erneut abgefragt werden kann, indem Sie die [CanRestart-Memberfunktion](#canrestart) aufrufen. `CanRestart`garantiert nicht, `Requery` dass dies gelingt.

> [!CAUTION]
> Rufen `Requery` Sie erst `Open`an, nachdem Sie angerufen haben.

> [!NOTE]
> Der Aufruf von [Requery](#requery) ändert DAO-Lesezeichen.

Sie können kein `Requery` Recordset vom Typ Dynaset oder Snapshot `CanRestart` aufrufen, wenn das Aufrufen von 0 zurückgegeben wird, und Sie können es auch nicht für ein Datensatzset vom Tabellentyp verwenden.

Wenn `IsBOF` beide `IsEOF` und nach dem `Requery`Aufruf einen Wert ungleich Null zurückgeben, hat die Abfrage keine Datensätze zurückgegeben, und das Recordset enthält keine Daten.

Weitere Informationen finden Sie im Thema "Abfragemethode" in der DAO-Hilfe.

## <a name="cdaorecordsetseek"></a><a name="seek"></a>CDaoRecordset::Suchen

Rufen Sie diese Memberfunktion auf, um den Datensatz in einem indizierten Recordset-Objekt mit Tabellentyp zu suchen, das die angegebenen Kriterien für den aktuellen Index erfüllt, und diesen Datensatz zum aktuellen Datensatz zu machen.

```
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

*lpszVergleich*<br/>
Einer der folgenden Zeichenfolgenausdrücke:\<"<", " =", "=", ">=" oder ">".

*pKey1*<br/>
Ein Zeiger auf eine [COleVariant,](../../mfc/reference/colevariant-class.md) deren Wert dem ersten Feld im Index entspricht. Erforderlich.

*pKey2*<br/>
Ein Zeiger auf `COleVariant` einen, dessen Wert dem zweiten Feld im Index entspricht, falls vorhanden. Standardwerte auf NULL.

*pKey3*<br/>
Ein Zeiger auf `COleVariant` einen, dessen Wert dem dritten Feld im Index entspricht, falls vorhanden. Standardwerte auf NULL.

*pKeyArray*<br/>
Ein Zeiger auf ein Array von Varianten. Die Arraygröße entspricht der Anzahl der Felder im Index.

*nTasten*<br/>
Eine ganze Zahl, die der Größe des Arrays entspricht, d. h. der Anzahl der Felder im Index.

> [!NOTE]
> Geben Sie keine Platzhalter in den Schlüsseln an. Platzhalter führen `Seek` dazu, dass keine übereinstimmenden Datensätze zurückgegeben werden.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn übereinstimmende Datensätze gefunden werden, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die zweite `Seek` (Array-)Version von, um Indizes von vier oder mehr Feldern zu behandeln.

`Seek`ermöglicht die Hochleistungsindexsuche nach Datensatzsätzen vom Typ Tabellentyp. Sie müssen den aktuellen `SetCurrentIndex` Index `Seek`festlegen, indem Sie vor dem Aufruf aufrufen . Wenn der Index ein nicht eindeutiges `Seek` Schlüsselfeld oder Felder identifiziert, sucht der erste Datensatz, der die Kriterien erfüllt. Wenn Sie keinen Index festlegen, wird eine Ausnahme ausgelöst.

Beachten Sie, dass die `COleVariant` Objekte explizit als ANSI deklariert werden müssen, wenn Sie kein UNICODE-Recordset erstellen. Dies kann durch die Verwendung der [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** Form des Konstruktors mit *vtSrc* festgelegt `VT_BSTRT` (ANSI) oder mit der `COleVariant` Funktion [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** mit *vtSrc* auf `VT_BSTRT`.

Wenn Sie `Seek`aufrufen, übergeben Sie einen oder mehrere Schlüsselwerte\<und einen Vergleichsoperator ("<", "=", "=", ">=" oder ">"). `Seek`durchsucht die angegebenen Schlüsselfelder und sucht den ersten Datensatz, der die von *lpszComparison* und *pKey1*angegebenen Kriterien erfüllt. Sobald dieser `Seek` Wert gefunden wurde, gibt er einen Wert ungleich Null zurück und macht diesen Datensatz aktuell. Wenn `Seek` eine Übereinstimmung nicht `Seek` gefunden werden kann, wird Null zurückgegeben, und der aktuelle Datensatz ist nicht definiert. Wenn Sie DAO direkt verwenden, müssen Sie die NoMatch-Eigenschaft explizit überprüfen.

Wenn `lpszComparison` "=", ">=" oder `Seek` ">" ist, beginnt sie am Anfang des Indexes. Wenn *lpszComparison* "<" oder "<=" ist, `Seek` beginnt am Ende des Indexes und sucht rückwärts, es sei denn, es gibt doppelte Indexeinträge am Ende. In diesem `Seek` Fall beginnt er mit einem beliebigen Eintrag unter den doppelten Indexeinträgen am Ende des Indexes.

Bei Verwendung `Seek`muss kein aktueller Datensatz vorhanden sein.

Verwenden Sie die Suchvorgänge, um einen Datensatz in einem Datensatz vom Typ Dynaset oder Snapshot zu suchen, der eine bestimmte Bedingung erfüllt. Um alle Datensätze einzuschließen, nicht nur solche, die eine bestimmte Bedingung erfüllen, verwenden Sie die Vorgänge Verschieben, um von Datensatz zu Datensatz zu wechseln.

Sie können `Seek` keine angefügte Tabelle eines beliebigen Typs aufrufen, da angefügte Tabellen als Recordsets vom Typ Dynaset oder Snapshot geöffnet werden müssen. Wenn Sie jedoch `CDaoDatabase::Open` aufrufen, eine installierbare ISAM-Datenbank direkt zu öffnen, können Sie Tabellen in dieser Datenbank aufrufen, `Seek` auch wenn die Leistung möglicherweise langsam ist.

Weitere Informationen finden Sie im Thema "Suchmethode" in der DAO-Hilfe.

## <a name="cdaorecordsetsetabsoluteposition"></a><a name="setabsoluteposition"></a>CDaoRecordset::SetAbsolutePosition

Legt die relative Datensatznummer des aktuellen Datensatzes eines Recordset-Objekts fest.

```cpp
void SetAbsolutePosition(long lPosition);
```

### <a name="parameters"></a>Parameter

*lPosition*<br/>
Entspricht der Ordinalposition des aktuellen Datensatzes im Recordset.

### <a name="remarks"></a>Bemerkungen

Durch `SetAbsolutePosition` Aufrufen können Sie den aktuellen Datensatzzeiger basierend auf seiner Ordinalposition in einem Recordset vom Typ Dynaset oder Snapshot-Datensatz auf einen bestimmten Datensatz positionieren. Sie können auch die aktuelle Datensatznummer ermitteln, indem Sie [GetAbsolutePosition](#getabsoluteposition)aufrufen.

> [!NOTE]
> Diese Memberfunktion ist nur für Recordsets vom Typ Dynaset und Snapshot gültig.

Der AbsolutePosition-Eigenschaftswert des zugrunde liegenden DAO-Objekts ist nullbasiert. eine Einstellung von 0 bezieht sich auf den ersten Datensatz im Recordset. Wenn Sie einen Wert festlegen, der größer als die Anzahl der aufgefüllten Datensätze ist, wird bei MFC eine Ausnahme ausgelöst. Sie können die Anzahl der ausgefüllten Datensätze `GetRecordCount` im Recordset bestimmen, indem Sie die Memberfunktion aufrufen.

Wenn der aktuelle Datensatz gelöscht wird, wird der AbsolutePosition-Eigenschaftswert nicht definiert, und MFC löst eine Ausnahme aus, wenn darauf verwiesen wird. Neue Datensätze werden am Ende der Sequenz hinzugefügt.

> [!NOTE]
> Diese Eigenschaft ist nicht für die Verwendung als Ersatzdatensatznummer vorgesehen. Lesezeichen sind nach wie vor die empfohlene Methode zum Beibehalten und Zurückkehren an eine bestimmte Position und die einzige Möglichkeit, den aktuellen Datensatz für alle Arten von Recordset-Objekten zu positionieren, die Lesezeichen unterstützen. Insbesondere ändert sich die Position eines bestimmten Datensatzes, wenn der(n) vor ihm vorangehende Datensatz(e) gelöscht wird. Es gibt auch keine Zusicherung, dass ein bestimmter Datensatz die gleiche absolute Position hat, wenn das Recordset erneut erstellt wird, da die Reihenfolge der einzelnen Datensätze innerhalb eines Recordsets nicht garantiert ist, es sei denn, er wird mit einer SQL-Anweisung unter Verwendung einer **ORDERBY-Klausel** erstellt.

Weitere Informationen finden Sie im Thema "AbsolutePosition-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetsetbookmark"></a><a name="setbookmark"></a>CDaoRecordset::SetBookmark

Rufen Sie diese Memberfunktion auf, um das Recordset auf dem Datensatz zu positionieren, der das angegebene Lesezeichen enthält.

```cpp
void SetBookmark(COleVariant varBookmark);
```

### <a name="parameters"></a>Parameter

*varBookmark*<br/>
Ein [COleVariant-Objekt,](../../mfc/reference/colevariant-class.md) das den Lesezeichenwert für einen bestimmten Datensatz enthält.

### <a name="remarks"></a>Bemerkungen

Wenn ein Recordset-Objekt erstellt oder geöffnet wird, verfügt jeder Datensatz bereits über ein eindeutiges Lesezeichen. Sie können die Textmarke für den `GetBookmark` aktuellen Datensatz abrufen, indem Sie den Wert aufrufen und in einem `COleVariant` Objekt speichern. Sie können später zu diesem `SetBookmark` Datensatz zurückkehren, indem Sie den gespeicherten Lesezeichenwert aufrufen.

> [!NOTE]
> Der Aufruf von [Requery](#requery) ändert DAO-Lesezeichen.

Beachten Sie, dass das `COleVariant` Objekt explizit als ANSI deklariert werden muss, wenn Sie kein UNICODE-Recordset erstellen. Dies kann durch die Verwendung der [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** Form des Konstruktors mit *vtSrc* festgelegt `VT_BSTRT` (ANSI) oder mit der `COleVariant` Funktion [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** mit *vtSrc* auf `VT_BSTRT`.

Weitere Informationen finden Sie in den Themen "Bookmark-Eigenschaft" und Lesezeichen-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetsetcachesize"></a><a name="setcachesize"></a>CDaoRecordset::SetCacheSize

Rufen Sie diese Memberfunktion auf, um die Anzahl der zwischenzuspeichernden Datensätze festzulegen.

```cpp
void SetCacheSize(long lSize);
```

### <a name="parameters"></a>Parameter

*lGröße*<br/>
Gibt die Anzahl der Datensätze an. Ein typischer Wert ist 100. Mit einer Einstellung von 0 wird die Zwischenspeicherung deaktiviert. Die Einstellung muss zwischen 5 und 1200 Datensätzen liegen. Der Cache kann eine beträchtliche Menge an Arbeitsspeicher verwenden.

### <a name="remarks"></a>Bemerkungen

Ein Cache ist ein Leerspeicher im lokalen Speicher, der die zuletzt vom Server abgerufenen Daten enthält, falls die Daten erneut angefordert werden, während die Anwendung ausgeführt wird. Das Zwischenspeichern von Daten verbessert die Leistung einer Anwendung, die Daten von einem Remoteserver über Recordset-Objekte vom Typ Dynaset abruft. Wenn Daten angefordert werden, überprüft das Microsoft Jet-Datenbankmodul den Cache zuerst auf die angeforderten Daten, anstatt sie vom Server abzurufen, was mehr Zeit in Anspruch nimmt. Daten, die nicht aus einer ODBC-Datenquelle stammen, werden nicht im Cache gespeichert.

Jede ODBC-Datenquelle, z. B. eine angefügte Tabelle, kann über einen lokalen Cache verfügen. Um den Cache zu erstellen, öffnen Sie ein Recordset-Objekt aus der Remote-Datenquelle, rufen Sie die `SetCacheSize` und `SetCacheStart` Memberfunktionen auf, und rufen Sie dann die `FillCache` Memberfunktion auf oder durchlaufen Sie die Datensätze mithilfe eines der Move-Vorgänge. Der *parameter lSize* der `SetCacheSize` Memberfunktion kann auf der Anzahl der Datensätze basieren, mit denen Ihre Anwendung gleichzeitig arbeiten kann. Wenn Sie z. B. ein Recordset als Quelle der Daten verwenden, `SetCacheSize` die auf dem Bildschirm angezeigt werden sollen, können Sie den *parameter lSize* als 20 übergeben, um 20 Datensätze gleichzeitig anzuzeigen.

Weitere Informationen finden Sie im Thema "CacheSize, CacheStart Properties" in der DAO-Hilfe.

## <a name="cdaorecordsetsetcachestart"></a><a name="setcachestart"></a>CDaoRecordset::SetCacheStart

Rufen Sie diese Memberfunktion auf, um das Lesezeichen des ersten Datensatzes im Zwischenspeichern anzugeben.

```cpp
void SetCacheStart(COleVariant varBookmark);
```

### <a name="parameters"></a>Parameter

*varBookmark*<br/>
Eine [COleVariant,](../../mfc/reference/colevariant-class.md) die die Textmarke des ersten Datensatzes im zwischenspeichernden Recordset angibt.

### <a name="remarks"></a>Bemerkungen

Sie können den Lesezeichenwert eines beliebigen Datensatzes für `SetCacheStart` den *varBookmark-Parameter* der Memberfunktion verwenden. Erstellen Sie den Datensatz, den Sie den Cache mit dem aktuellen Datensatz starten möchten, richten Sie eine Textmarke für diesen Datensatz mithilfe von [SetBookmark](#setbookmark)ein, und übergeben Sie den Lesezeichenwert als Parameter für die `SetCacheStart` Memberfunktion.

Das Microsoft Jet-Datenbankmodul fordert Datensätze innerhalb des Cachebereichs aus dem Cache an und fordert Datensätze außerhalb des Cachebereichs vom Server an.

Aus dem Cache abgerufene Datensätze spiegeln keine Änderungen wider, die gleichzeitig von anderen Benutzern an den Quelldaten vorgenommen wurden.

Um eine Aktualisierung aller zwischengespeicherten Daten zu erzwingen, übergeben Sie den *lSize-Parameter* von `SetCacheSize` als 0, rufen `SetCacheSize` Sie erneut mit der Größe des ursprünglich angeforderten Caches auf, und rufen Sie dann die `FillCache` Memberfunktion auf.

Beachten Sie, dass das `COleVariant` Objekt explizit als ANSI deklariert werden muss, wenn Sie kein UNICODE-Recordset erstellen. Dies kann durch die Verwendung der [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** Form des Konstruktors mit *vtSrc* festgelegt `VT_BSTRT` (ANSI) oder mit der `COleVariant` Funktion [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** mit *vtSrc* auf `VT_BSTRT`.

Weitere Informationen finden Sie im Thema CacheSize, CacheStart-Eigenschaften" in der DAO-Hilfe.

## <a name="cdaorecordsetsetcurrentindex"></a><a name="setcurrentindex"></a>CDaoRecordset::SetCurrentIndex

Rufen Sie diese Memberfunktion auf, um einen Index für ein Datensatzset vom Tabellentyp festzulegen.

```cpp
void SetCurrentIndex(LPCTSTR lpszIndex);
```

### <a name="parameters"></a>Parameter

*lpszIndex*<br/>
Ein Zeiger, der den Namen des festzulegenden Indexes enthält.

### <a name="remarks"></a>Bemerkungen

Datensätze in Basistabellen werden nicht in einer bestimmten Reihenfolge gespeichert. Durch festlegen eines Indexes wird die Reihenfolge der aus der Datenbank zurückgegebenen Datensätze geändert, die Reihenfolge, in der die Datensätze gespeichert werden, jedoch nicht beeinflusst. Der angegebene Index muss bereits definiert sein. Wenn Sie versuchen, ein Indexobjekt zu verwenden, das nicht vorhanden ist, oder wenn der Index beim Aufrufen von [Seek](#seek)nicht festgelegt ist, löst MFC eine Ausnahme aus.

Sie können einen neuen Index für die Tabelle erstellen, indem Sie [CDaoTableDef::CreateIndex](../../mfc/reference/cdaotabledef-class.md#createindex) aufrufen und den neuen Index an die Indexes-Auflistung der zugrunde liegenden tabledef anhängen, indem Sie [CDaoTableDef::Append](../../mfc/reference/cdaotabledef-class.md#append)aufrufen und dann das Recordset erneut öffnen.

Datensätze, die von einem Datensatz vom Tabellentyp zurückgegeben werden, können nur nach den Indizes sortiert werden, die für die zugrunde liegende tabledef definiert sind. Um Datensätze in einer anderen Reihenfolge zu sortieren, können Sie ein Recordset vom Typ Dynaset oder Snapshot mithilfe einer SQL **ORDERBY-Klausel** öffnen, die in [CDaoRecordset::m_strSort](#m_strsort)gespeichert ist.

Weitere Informationen finden Sie im Thema "Indexobjekt" und in der Definition "aktueller Index" in der DAO-Hilfe.

## <a name="cdaorecordsetsetfielddirty"></a><a name="setfielddirty"></a>CDaoRecordset::SetFieldDirty

Rufen Sie diese Memberfunktion auf, um ein Felddatenelement des Recordsets als geändert oder unverändert zu kennzeichnen.

```cpp
void SetFieldDirty(
    void* pv,
    BOOL bDirty = TRUE);
```

### <a name="parameters"></a>Parameter

*Pv*<br/>
Enthält die Adresse eines Felddatenelements im Recordset oder NULL. Wenn NULL, werden alle Felddatenmember im Recordset gekennzeichnet. (C++ NULL ist in der Datenbankterminologie nicht identisch mit Null, was bedeutet, dass "keinen Wert hat").

*bDirty*<br/>
TRUE, wenn das Felddatenelement als "schmutzig" (geändert) gekennzeichnet werden soll. Andernfalls FALSE, wenn das Felddatenelement als "sauber" (unverändert) gekennzeichnet werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn Sie Felder unverändert markieren, wird sichergestellt, dass das Feld nicht aktualisiert wird.

Das Framework markiert geänderte Felddatenmember, um sicherzustellen, dass sie vom DFX-Mechanismus (DAO Record Field Exchange) in den Datensatz in der Datenquelle geschrieben werden. Wenn Sie den Wert eines Felds ändern, wird das `SetFieldDirty` Feld im Allgemeinen automatisch verschmutzt, sodass Sie sich selten selbst aufrufen müssen, aber Sie möchten manchmal sicherstellen, dass Spalten explizit aktualisiert oder eingefügt werden, unabhängig davon, welcher Wert sich im Felddatenelement befindet. Der DFX-Mechanismus verwendet auch die Verwendung von PSEUDONULL. Weitere Informationen finden Sie unter [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Wenn der Doppelpuffermechanismus nicht verwendet wird, wird das Feld durch Ändern des Werts des Felds nicht automatisch als verschmutzt festgelegt. In diesem Fall ist es notwendig, das Feld explizit als "schmutzig" festzulegen. Das in [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) enthaltene Flag steuert diese automatische Feldüberprüfung.

> [!NOTE]
> Rufen Sie diese Memberfunktion erst auf, nachdem Sie [Bearbeiten](#edit) oder [AddNew](#addnew)aufgerufen haben.

Wenn Sie NULL für das erste Argument der `outputColumn` Funktion verwenden, wird `CDaoFieldExchange`die Funktion auf alle Felder angewendet, nicht auf **param-Felder** in . Zum Beispiel wird der Anruf

[!code-cpp[NVC_MFCDatabase#6](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]

setzt nur `outputColumn` Felder auf NULL; **param-Felder** bleiben davon unberührt.

Um an einem **Param**zu arbeiten, müssen Sie die tatsächliche Adresse des einzelnen **Params** angeben, an dem Sie arbeiten möchten, z. B.:

[!code-cpp[NVC_MFCDatabase#7](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]

Dies bedeutet, dass Sie nicht alle **Param-Felder** auf NULL setzen können, wie Sie es mit `outputColumn` Feldern können.

`SetFieldDirty`wird durch `DoFieldExchange`implementiert.

## <a name="cdaorecordsetsetfieldnull"></a><a name="setfieldnull"></a>CDaoRecordset::SetFieldNull

Rufen Sie diese Memberfunktion auf, um ein Felddatenelement des Recordsets als Null (insbesondere ohne Wert) oder als Nicht-Null zu kennzeichnen.

```cpp
void SetFieldNull(
    void* pv,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parameter

*Pv*<br/>
Enthält die Adresse eines Felddatenelements im Recordset oder NULL. Wenn NULL, werden alle Felddatenmember im Recordset gekennzeichnet. (C++ NULL ist in der Datenbankterminologie nicht identisch mit Null, was bedeutet, dass "keinen Wert hat").

*bNull*<br/>
Ein Wert ungleich Null, wenn das Felddatenelement als mit keinem Wert (Null) gekennzeichnet werden soll. Andernfalls 0, wenn das Felddatenelement als nicht-Null gekennzeichnet werden soll.

### <a name="remarks"></a>Bemerkungen

`SetFieldNull`wird für Felder verwendet, die `DoFieldExchange` im Mechanismus gebunden sind.

Wenn Sie einem Recordset einen neuen Datensatz hinzufügen, werden alle Felddatenmember zunächst auf einen Nullwert festgelegt und als "schmutzig" (geändert) gekennzeichnet. Wenn Sie einen Datensatz aus einer Datenquelle abrufen, haben seine Spalten entweder bereits Werte oder sind Null. Wenn es nicht angemessen ist, ein Feld Null zu machen, wird eine [CDaoException](../../mfc/reference/cdaoexception-class.md) ausgelöst.

Wenn Sie z. B. den Mechanismus für die doppelte Pufferung verwenden, wenn Sie ein Feld `SetFieldNull` des aktuellen Datensatzes ausdrücklich als nicht mit einem Wert kennzeichnen möchten, rufen Sie den Aufruf auf, bei dem *bNull* auf TRUE festgelegt ist, um es als Null zu kennzeichnen. Wenn ein Feld zuvor als Null markiert wurde und Sie ihm nun einen Wert geben möchten, legen Sie einfach seinen neuen Wert fest. Sie müssen das Null-Flag `SetFieldNull`nicht mit entfernen. Um zu bestimmen, ob das Feld Null sein darf, rufen Sie [IsFieldNullable](#isfieldnullable)auf.

Wenn Sie den Doppelpuffermechanismus nicht verwenden, wird das Feld durch Ändern des Werts des Felds nicht automatisch als schmutzig und nicht Null festgelegt. Sie müssen die Felder speziell als schmutzig und nicht null festlegen. Das in [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) enthaltene Flag steuert diese automatische Feldüberprüfung.

Der DFX-Mechanismus verwendet die Verwendung von PSEUDONULL. Weitere Informationen finden Sie unter [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

> [!NOTE]
> Rufen Sie diese Memberfunktion erst auf, nachdem Sie [Bearbeiten](#edit) oder [AddNew](#addnew)aufgerufen haben.

Wenn Sie NULL für das erste Argument der `outputColumn` Funktion verwenden, wird `CDaoFieldExchange`die Funktion nur auf Felder angewendet, nicht **auf Paramfelder** in . Zum Beispiel wird der Anruf

[!code-cpp[NVC_MFCDatabase#8](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]

setzt nur `outputColumn` Felder auf NULL; **param-Felder** bleiben davon unberührt.

## <a name="cdaorecordsetsetfieldvalue"></a><a name="setfieldvalue"></a>CDaoRecordset::SetFieldValue

Rufen Sie diese Memberfunktion auf, um den Wert eines Felds entweder durch Ordinalposition oder durch Ändern des Wertes der Zeichenfolge festzulegen.

```
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

*lpszName*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen eines Felds enthält.

*varValue*<br/>
Ein Verweis auf ein [COleVariant-Objekt,](../../mfc/reference/colevariant-class.md) das den Wert des Feldinhalts enthält.

*nIndex*<br/>
Eine ganze Zahl, die die Ordinalposition des Felds in der Fields-Auflistung des Recordsets (nullbasiert) darstellt.

*lpszValue*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Wert des Feldinhalts enthält.

### <a name="remarks"></a>Bemerkungen

Verwenden `SetFieldValue` Sie und [GetFieldValue,](#getfieldvalue) um Felder zur Laufzeit dynamisch zu binden, anstatt Spalten mithilfe des [DoFieldExchange-Mechanismus](#dofieldexchange) statisch zu binden.

Beachten Sie, dass Sie, wenn Sie kein UNICODE-Recordset erstellen, entweder eine Form `SetFieldValue` verwenden müssen, die keinen `COleVariant` Parameter enthält, oder das `COleVariant` Objekt muss explizit als ANSI deklariert werden. Dies kann durch die Verwendung der [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** Form des Konstruktors mit *vtSrc* festgelegt `VT_BSTRT` (ANSI) oder mit der `COleVariant` Funktion [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** mit *vtSrc* auf `VT_BSTRT`.

Weitere Informationen finden Sie in den Themen "Feldobjekt" und "Werteigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetsetfieldvaluenull"></a><a name="setfieldvaluenull"></a>CDaoRecordset::SetFieldValueNull

Rufen Sie diese Memberfunktion auf, um das Feld auf einen Null-Wert festzulegen.

```cpp
void SetFieldValueNull(int nIndex);
void SetFieldValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der Index des Feldes im Recordset für die Suche nach nullbasiertem Index.

*lpszName*<br/>
Der Name des Felds im Recordset für die Suche nach Namen.

### <a name="remarks"></a>Bemerkungen

C++ NULL ist nicht identisch mit Null, was in der Datenbankterminologie bedeutet, dass "keinen Wert" hat.

Weitere Informationen finden Sie in den Themen "Feldobjekt" und "Werteigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetsetlockingmode"></a><a name="setlockingmode"></a>CDaoRecordset::SetLockingMode

Rufen Sie diese Memberfunktion auf, um den Typ der Sperrung für das Recordset festzulegen.

```cpp
void SetLockingMode(BOOL bPessimistic);
```

### <a name="parameters"></a>Parameter

*bPessimistisch*<br/>
Ein Flag, das den Typ der Sperrung angibt.

### <a name="remarks"></a>Bemerkungen

Wenn eine pessimistische Sperrung wirksam ist, wird die 2K-Seite mit dem `Edit` Datensatz, den Sie bearbeiten, gesperrt, sobald Sie die Memberfunktion aufrufen. Die Seite wird entsperrt, wenn Sie die `Update` oder `Close` Memberfunktion oder einen der Aktionen Verschieben oder Suchen aufrufen.

Wenn eine optimistische Sperrung wirksam ist, wird die 2K-Seite, die `Update` den Datensatz enthält, nur gesperrt, während der Datensatz mit der Memberfunktion aktualisiert wird.

Wenn eine Seite gesperrt ist, kann kein anderer Benutzer Datensätze auf derselben Seite bearbeiten. Wenn Sie `SetLockingMode` einen Wert ungleich Null aufrufen und übergeben und ein anderer `Edit`Benutzer die Seite bereits gesperrt hat, wird beim Aufrufen eine Ausnahme ausgelöst. Andere Benutzer können Daten von gesperrten Seiten lesen.

Wenn Sie `SetLockingMode` mit einem Nullwert `Update` und einem späteren Aufruf aufrufen, während die Seite von einem anderen Benutzer gesperrt ist, tritt eine Ausnahme auf. Um die Änderungen anzuzeigen, die ein anderer Benutzer an `SetBookmark` Ihrem Datensatz vorgenommen hat (und Ihre Änderungen verliert), rufen Sie die Memberfunktion mit dem Lesezeichenwert des aktuellen Datensatzes auf.

Bei der Arbeit mit ODBC-Datenquellen ist der Sperrmodus immer optimistisch.

## <a name="cdaorecordsetsetparamvalue"></a><a name="setparamvalue"></a>CDaoRecordset::SetParamValue

Rufen Sie diese Memberfunktion auf, um den Wert eines Parameters im Recordset zur Laufzeit festzulegen.

```
virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);

virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Die numerische Position des Parameters in der Parameters-Auflistung der querydef.

*var*<br/>
Der festzulegende Wert; siehe Anmerkungen.

*lpszName*<br/>
Der Name des Parameters, dessen Wert Sie festlegen möchten.

### <a name="remarks"></a>Bemerkungen

Der Parameter muss bereits als Teil der SQL-Zeichenfolge des Recordsets eingerichtet worden sein. Sie können auf den Parameter entweder nach Namen oder über seine Indexposition in der Auflistung zugreifen.

Geben Sie den Wert `COleVariant` an, der als Objekt festgelegt werden soll. Informationen zum Festlegen des gewünschten Werts und der Eingabe in Ihrem `COleVariant` Objekt finden Sie unter Klasse [COleVariant](../../mfc/reference/colevariant-class.md). Beachten Sie, dass das `COleVariant` Objekt explizit als ANSI deklariert werden muss, wenn Sie kein UNICODE-Recordset erstellen. Dies kann durch die Verwendung der [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** Form des Konstruktors mit *vtSrc* festgelegt `VT_BSTRT` (ANSI) oder mit der `COleVariant` Funktion [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** mit *vtSrc* auf `VT_BSTRT`.

## <a name="cdaorecordsetsetparamvaluenull"></a><a name="setparamvaluenull"></a>CDaoRecordset::SetParamValueNull

Rufen Sie diese Memberfunktion auf, um den Parameter auf einen Null-Wert festzulegen.

```cpp
void SetParamValueNull(int nIndex);
void SetParamValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der Index des Feldes im Recordset für die Suche nach nullbasiertem Index.

*lpszName*<br/>
Der Name des Felds im Recordset für die Suche nach Namen.

### <a name="remarks"></a>Bemerkungen

C++ NULL ist nicht identisch mit Null, was in der Datenbankterminologie bedeutet, dass "keinen Wert" hat.

## <a name="cdaorecordsetsetpercentposition"></a><a name="setpercentposition"></a>CDaoRecordset::SetPercentPosition

Rufen Sie diese Memberfunktion auf, um einen Wert festzulegen, der die ungefähre Position des aktuellen Datensatzes im Recordset-Objekt basierend auf einem Prozentsatz der Datensätze im Recordset ändert.

```cpp
void SetPercentPosition(float fPosition);
```

### <a name="parameters"></a>Parameter

*fPosition*<br/>
Eine Zahl zwischen 0 und 100.

### <a name="remarks"></a>Bemerkungen

Wenn Sie mit einem Recordset vom Typ Dynaset oder Snapshot arbeiten, füllen Sie das `SetPercentPosition`Recordset zuerst auf, indem Sie zum letzten Datensatz wechseln, bevor Sie aufrufen. Wenn Sie `SetPercentPosition` aufrufen, bevor Sie das Recordset vollständig auffüllen, ist der Bewegungsumfang relativ zur Anzahl der Datensätze, auf die zugegriffen wird, wie durch den Wert von [GetRecordCount](#getrecordcount)angegeben. Sie können zum letzten Datensatz `MoveLast`wechseln, indem Sie aufrufen.

Sobald Sie `SetPercentPosition`aufrufen, wird der Datensatz an der ungefähren Position, die diesem Wert entspricht, aktuell.

> [!NOTE]
> Das `SetPercentPosition` Aufrufen zum Verschieben des aktuellen Datensatzes in einen bestimmten Datensatz in einem Recordset wird nicht empfohlen. Rufen Sie stattdessen die [SetBookmark-Memberfunktion](#setbookmark) auf.

Weitere Informationen finden Sie im Thema "PercentPosition-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaorecordsetupdate"></a><a name="update"></a>CDaoRecordset::Update

Rufen Sie diese Memberfunktion `AddNew` nach `Edit` einem Aufruf der oder Memberfunktion auf.

```
virtual void Update();
```

### <a name="remarks"></a>Bemerkungen

Dieser Aufruf ist erforderlich, `Edit` um den oder den `AddNew` Vorgang abzuschließen.

Sowohl `AddNew` `Edit` und bereiten Sie einen Bearbeitungspuffer vor, in dem die hinzugefügten oder bearbeiteten Daten zum Speichern in der Datenquelle platziert werden. `Update`speichert die Daten. Nur die Felder, die als geändert markiert oder erkannt wurden, werden aktualisiert.

Wenn die Datenquelle Transaktionen unterstützt, können `Update` Sie den `AddNew` Aufruf `Edit` (und den entsprechenden oder Aufruf) zu einem Teil einer Transaktion machen.

> [!CAUTION]
> Wenn Sie `Update` aufrufen, `AddNew` ohne `Edit` `Update` vorher `CDaoException`eine oder anzurufen, wird eine ausgelöst. Wenn Sie `AddNew` `Edit`aufrufen oder `Update` , müssen Sie aufrufen, bevor Sie [MoveNext](#movenext) aufrufen oder entweder das Recordset oder die Datenquellenverbindung schließen. Andernfalls gehen Ihre Änderungen ohne Benachrichtigung verloren.

Wenn das Recordset-Objekt pessimistisch in einer Mehrbenutzerumgebung gesperrt ist, bleibt der Datensatz von der Zeit, `Edit` die verwendet wird, bis die Aktualisierung abgeschlossen ist, gesperrt. Wenn das Recordset optimistisch gesperrt ist, wird der Datensatz gesperrt und mit dem vorbearbeiteten Datensatz verglichen, kurz bevor er in der Datenbank aktualisiert wird. Wenn sich der Datensatz `Edit`seit `Update` dem Aufruf geändert hat, schlägt der Vorgang fehl, und MFC löst eine Ausnahme aus. Sie können den Sperrmodus mit `SetLockingMode`ändern.

> [!NOTE]
> Optimistische Sperren werden immer für externe Datenbankformate wie ODBC und installierbares ISAM verwendet.

Weitere Informationen finden Sie in den Themen "AddNew Method", "CancelUpdate Method", "Delete Method", "LastModified Property", "Update Method" und "EditMode Property" in der DAO-Hilfe.

## <a name="see-also"></a>Weitere Informationen

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDaoTableDef-Klasse](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoWorkspace-Klasse](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase-Klasse](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoQueryDef-Klasse](../../mfc/reference/cdaoquerydef-class.md)<br/>
