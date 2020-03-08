---
title: CDaoQueryDef-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDaoQueryDef
- AFXDAO/CDaoQueryDef
- AFXDAO/CDaoQueryDef::CDaoQueryDef
- AFXDAO/CDaoQueryDef::Append
- AFXDAO/CDaoQueryDef::CanUpdate
- AFXDAO/CDaoQueryDef::Close
- AFXDAO/CDaoQueryDef::Create
- AFXDAO/CDaoQueryDef::Execute
- AFXDAO/CDaoQueryDef::GetConnect
- AFXDAO/CDaoQueryDef::GetDateCreated
- AFXDAO/CDaoQueryDef::GetDateLastUpdated
- AFXDAO/CDaoQueryDef::GetFieldCount
- AFXDAO/CDaoQueryDef::GetFieldInfo
- AFXDAO/CDaoQueryDef::GetName
- AFXDAO/CDaoQueryDef::GetODBCTimeout
- AFXDAO/CDaoQueryDef::GetParameterCount
- AFXDAO/CDaoQueryDef::GetParameterInfo
- AFXDAO/CDaoQueryDef::GetParamValue
- AFXDAO/CDaoQueryDef::GetRecordsAffected
- AFXDAO/CDaoQueryDef::GetReturnsRecords
- AFXDAO/CDaoQueryDef::GetSQL
- AFXDAO/CDaoQueryDef::GetType
- AFXDAO/CDaoQueryDef::IsOpen
- AFXDAO/CDaoQueryDef::Open
- AFXDAO/CDaoQueryDef::SetConnect
- AFXDAO/CDaoQueryDef::SetName
- AFXDAO/CDaoQueryDef::SetODBCTimeout
- AFXDAO/CDaoQueryDef::SetParamValue
- AFXDAO/CDaoQueryDef::SetReturnsRecords
- AFXDAO/CDaoQueryDef::SetSQL
- AFXDAO/CDaoQueryDef::m_pDAOQueryDef
- AFXDAO/CDaoQueryDef::m_pDatabase
helpviewer_keywords:
- CDaoQueryDef [MFC], CDaoQueryDef
- CDaoQueryDef [MFC], Append
- CDaoQueryDef [MFC], CanUpdate
- CDaoQueryDef [MFC], Close
- CDaoQueryDef [MFC], Create
- CDaoQueryDef [MFC], Execute
- CDaoQueryDef [MFC], GetConnect
- CDaoQueryDef [MFC], GetDateCreated
- CDaoQueryDef [MFC], GetDateLastUpdated
- CDaoQueryDef [MFC], GetFieldCount
- CDaoQueryDef [MFC], GetFieldInfo
- CDaoQueryDef [MFC], GetName
- CDaoQueryDef [MFC], GetODBCTimeout
- CDaoQueryDef [MFC], GetParameterCount
- CDaoQueryDef [MFC], GetParameterInfo
- CDaoQueryDef [MFC], GetParamValue
- CDaoQueryDef [MFC], GetRecordsAffected
- CDaoQueryDef [MFC], GetReturnsRecords
- CDaoQueryDef [MFC], GetSQL
- CDaoQueryDef [MFC], GetType
- CDaoQueryDef [MFC], IsOpen
- CDaoQueryDef [MFC], Open
- CDaoQueryDef [MFC], SetConnect
- CDaoQueryDef [MFC], SetName
- CDaoQueryDef [MFC], SetODBCTimeout
- CDaoQueryDef [MFC], SetParamValue
- CDaoQueryDef [MFC], SetReturnsRecords
- CDaoQueryDef [MFC], SetSQL
- CDaoQueryDef [MFC], m_pDAOQueryDef
- CDaoQueryDef [MFC], m_pDatabase
ms.assetid: 9676a4a3-c712-44d4-8c5d-d1cc78288d3a
ms.openlocfilehash: 08fb2909a4fd2e5bda3dfc63d19224a515c7c699
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883888"
---
# <a name="cdaoquerydef-class"></a>CDaoQueryDef-Klasse

Stellt eine Abfragedefinition ("Querydef") dar, die in einer Datenbank gespeichert ist.

## <a name="syntax"></a>Syntax

```
class CDaoQueryDef : public CObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoQueryDef:: CDaoQueryDef](#cdaoquerydef)|Erstellt ein `CDaoQueryDef`-Objekt. Der nächste Rückruf `Open` oder `Create`, je nach Ihren Anforderungen.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoQueryDef:: Append](#append)|Fügt QueryDef als gespeicherte Abfrage an die Querydefs-Sammlung der Datenbank an.|
|[CDaoQueryDef:: CanUpdate](#canupdate)|Gibt einen Wert ungleich 0 (null) zurück, wenn die Abfrage die Datenbank aktualisieren|
|[CDaoQueryDef:: Close](#close)|Schließt das Querydef-Objekt. Löschen Sie C++ das-Objekt, wenn Sie damit fertig sind.|
|[CDaoQueryDef:: Create](#create)|Erstellt das zugrunde liegende DAO Querydef-Objekt. Verwenden Sie QueryDef als temporäre Abfrage, oder führen Sie `Append` aus, um Sie in der Datenbank zu speichern.|
|[CDaoQueryDef:: Execute](#execute)|Führt die Abfrage aus, die vom QueryDef-Objekt definiert wird.|
|[CDaoQueryDef:: GetConnect](#getconnect)|Gibt die Verbindungs Zeichenfolge zurück, die QueryDef zugeordnet ist. Die Verbindungs Zeichenfolge identifiziert die Datenquelle. (Nur bei SQL-Pass-Through-Abfragen, andernfalls eine leere Zeichenfolge.)|
|[CDaoQueryDef:: getdatecreated](#getdatecreated)|Gibt das Datum zurück, an dem die gespeicherte Abfrage erstellt wurde.|
|[CDaoQueryDef:: getdatelastupveraltet](#getdatelastupdated)|Gibt das Datum zurück, an dem die gespeicherte Abfrage zuletzt aktualisiert wurde.|
|[CDaoQueryDef:: GetFieldCount](#getfieldcount)|Gibt die Anzahl der Felder zurück, die von QueryDef definiert werden.|
|[CDaoQueryDef:: getfieldinfo](#getfieldinfo)|Gibt Informationen zu einem angegebenen Feld zurück, das in der Abfrage definiert ist.|
|[CDaoQueryDef:: GetName](#getname)|Gibt den Namen der Querydef zurück.|
|[CDaoQueryDef:: getodbctimeout](#getodbctimeout)|Gibt den Timeout Wert zurück, der von ODBC (für eine ODBC-Abfrage) beim Ausführen von QueryDef verwendet wird. Dadurch wird festgelegt, wie lange es dauert, bis die Abfrage Aktion beendet ist.|
|[CDaoQueryDef:: GetParameterCount](#getparametercount)|Gibt die Anzahl von Parametern zurück, die für die Abfrage definiert sind.|
|[CDaoQueryDef:: GetParameterInfo](#getparameterinfo)|Gibt Informationen zu einem angegebenen Parameter an die Abfrage zurück.|
|[CDaoQueryDef:: GetParamValue](#getparamvalue)|Gibt den Wert eines angegebenen Parameters für die Abfrage zurück.|
|[CDaoQueryDef:: getrecordsafffiziert](#getrecordsaffected)|Gibt die Anzahl der Datensätze zurück, die von einer Aktions Abfrage betroffen sind.|
|[CDaoQueryDef:: getreturnrecords](#getreturnsrecords)|Gibt einen Wert ungleich 0 (null) zurück, wenn die von QueryDef definierte Abfrage Datensätze zurückgibt|
|[CDaoQueryDef:: gezql](#getsql)|Gibt die SQL-Zeichenfolge zurück, die die von QueryDef definierte Abfrage angibt.|
|[CDaoQueryDef:: GetType](#gettype)|Gibt den Abfragetyp zurück: "Delete", "Update", "append", "Make-Table" usw.|
|[CDaoQueryDef:: IsOpen](#isopen)|Gibt einen Wert ungleich 0 (null) zurück, wenn QueryDef geöffnet ist und ausgeführt werden kann.|
|[CDaoQueryDef:: Open](#open)|Öffnet ein vorhandenes Querydef, das in der Querydefs-Sammlung der Datenbank gespeichert ist.|
|[CDaoQueryDef:: SetConnect](#setconnect)|Legt die Verbindungs Zeichenfolge für eine SQL-Pass-Through-Abfrage für eine ODBC-Datenquelle fest.|
|[CDaoQueryDef:: SetName](#setname)|Legt den Namen der gespeicherten Abfrage fest und ersetzt dabei den Namen, der beim Erstellen von QueryDef verwendet wurde.|
|[CDaoQueryDef:: abkout](#setodbctimeout)|Legt den von ODBC (für eine ODBC-Abfrage) verwendeten Timeout Wert fest, wenn QueryDef ausgeführt wird.|
|[CDaoQueryDef:: SetParamValue](#setparamvalue)|Legt den Wert eines angegebenen Parameters auf die Abfrage fest.|
|[CDaoQueryDef:: abtreturnrecords](#setreturnsrecords)|Gibt an, ob QueryDef Datensätze zurückgibt. Das Festlegen dieses Attributs auf "true" ist nur für SQL-Pass-Through-Abfragen gültig.|
|[CDaoQueryDef:: s](#setsql)|Legt die SQL-Zeichenfolge fest, die die von QueryDef definierte Abfrage angibt.|

### <a name="public-data-members"></a>Öffentliche Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoQueryDef:: m_pDAOQueryDef](#m_pdaoquerydef)|Ein Zeiger auf die OLE-Schnittstelle für das zugrunde liegende DAO Querydef-Objekt.|
|[CDaoQueryDef:: m_pDatabase](#m_pdatabase)|Ein Zeiger auf das `CDaoDatabase` Objekt, dem die QueryDef zugeordnet ist. Querydef kann in der Datenbank gespeichert werden.|

## <a name="remarks"></a>Bemerkungen

Ein QueryDef ist ein Datenzugriffs Objekt, das die SQL-Anweisung enthält, die eine Abfrage beschreibt, sowie deren Eigenschaften, z. b. "Erstellungsdatum" und "ODBC-Timeout". Sie können auch temporäre QueryDef-Objekte erstellen, ohne Sie zu speichern, aber es ist praktisch – und viel effizienter –, häufig wiederverwendete Abfragen in einer Datenbank zu speichern. Ein [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) -Objekt verwaltet eine Auflistung, die als Querydefs-Sammlung bezeichnet wird und die gespeicherten Querydefs enthält.

> [!NOTE]
>  Die DAO-Datenbankklassen unterscheiden sich von der MFC-Datenbankklassen in Bezug auf Open Database Connectivity (ODBC). Alle DAO-Datenbank-Klassennamen haben das Präfix "CDao". Sie können weiterhin mit den DAO-Klassen auf ODBC-Datenquellen zugreifen. Im Allgemeinen sind die MFC-Klassen basierend auf DAO leistungsfähiger als die MFC-Klassen basierend auf ODBC; die DAO-basierten Klassen können Daten, einschließlich über ODBC-Treiber, über eigene Datenbank-Engine zugreifen. Die DAO-basierten Klassen unterstützen auch Vorgänge wie das Hinzufügen von Tabellen über die Klassen, ohne direkt aufrufen von DAO (Data Definition Language, Datendefinitionssprache).

## <a name="usage"></a>Verwendung

Verwenden Sie QueryDef-Objekte, um mit einer vorhandenen gespeicherten Abfrage zu arbeiten oder eine neue gespeicherte Abfrage oder temporäre Abfrage zu erstellen:

1. Erstellen Sie in allen Fällen zuerst ein `CDaoQueryDef` Objekt, und stellen Sie einen Zeiger auf das [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) -Objekt bereit, zu dem die Abfrage gehört.

1. Führen Sie dann die folgenden Schritte aus, je nachdem, was Sie möchten:

   - Um eine vorhandene gespeicherte Abfrage zu verwenden, müssen Sie die [Open](#open) -Member-Funktion des QueryDef-Objekts abrufen und dabei den Namen der gespeicherten Abfrage angeben.

   - Um eine neue gespeicherte Abfrage zu erstellen, rufen Sie die [Create](#create) Member-Funktion des QueryDef-Objekts auf und stellen den Namen der Abfrage bereit. Rufen Sie dann [Append](#append) auf, um die Abfrage zu speichern, indem Sie Sie an die Querydefs-Sammlung der Datenbank anhängen. `Create` versetzt QueryDef in einen geöffneten Zustand, sodass Sie nach dem Aufrufen von `Create` nicht `Open`aufrufen.

   - Um einen temporären QueryDef zu erstellen, rufen Sie `Create`auf. Übergeben Sie eine leere Zeichenfolge für den Abfrage Namen. Rufen Sie `Append` nicht auf.

Wenn Sie die Verwendung eines QueryDef-Objekts abgeschlossen haben, müssen Sie dessen [Close](#close) Member-Funktion aufzurufen. Löschen Sie dann das Querydef-Objekt.

> [!TIP]
>  Die einfachste Möglichkeit zum Erstellen gespeicherter Abfragen besteht darin, Sie zu erstellen und mithilfe von Microsoft Access in der Datenbank zu speichern. Anschließend können Sie diese in Ihrem MFC-Code öffnen und verwenden.

## <a name="purposes"></a>Verwendet

Sie können ein QueryDef-Objekt für die folgenden Zwecke verwenden:

- So erstellen Sie ein `CDaoRecordset` Objekt

- So führen Sie die `Execute` Member-Funktion des Objekts aus, um eine Aktions Abfrage oder eine SQL-Pass-Through-Abfrage direkt auszuführen

Sie können ein QueryDef-Objekt für beliebige Abfrage Typen verwenden, einschließlich SELECT, Action, crosstab, DELETE, Update, Append, Make-Table, Data Definition, SQL Pass-Through, Union und Bulk queries. Der Abfragetyp wird durch den Inhalt der von Ihnen bereitgestellten SQL-Anweisung bestimmt. Weitere Informationen zu Abfrage Typen finden Sie unter den `Execute`-und [GetType](#gettype) -Member-Funktionen. Recordsets werden häufig für Abfragen mit Zeilen Rückgabe verwendet, normalerweise mithilfe der **SELECT... Aus** Schlüsselwörtern. `Execute` wird am häufigsten für Massen Vorgänge verwendet. Weitere Informationen finden Sie unter [Execute](#execute) und [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

## <a name="querydefs-and-recordsets"></a>Querydefs und Recordsets

Um ein QueryDef-Objekt zum Erstellen eines `CDaoRecordset` Objekts zu verwenden, erstellen oder öffnen Sie in der Regel eine Querydef, wie oben beschrieben. Erstellen Sie dann ein Recordset-Objekt, und übergeben Sie einen Zeiger auf das Querydef-Objekt, wenn Sie [CDaoRecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open)aufgerufen haben. Der von Ihnen übergebene QueryDef muss sich in einem geöffneten Zustand befinden. Weitere Informationen finden Sie unter Class [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Sie können eine QueryDef nicht zum Erstellen eines Recordsets verwenden (die häufigste Verwendung für eine QueryDef), es sei denn, Sie befindet sich in einem geöffneten Zustand. Versetzen Sie QueryDef in einen geöffneten Zustand, indem Sie entweder `Open` oder `Create`aufrufen.

## <a name="external-databases"></a>Externe Datenbanken

QueryDef-Objekte sind die bevorzugte Methode, um den nativen SQL-Dialekt einer externen Datenbank-Engine zu verwenden. Beispielsweise können Sie eine Transact SQL-Abfrage (wie auf Microsoft SQL Server verwendet) erstellen und in einem QueryDef-Objekt speichern. Wenn Sie eine SQL-Abfrage verwenden müssen, die nicht auf der Microsoft Jet-Datenbank-Engine basiert, müssen Sie eine Verbindungs Zeichenfolge bereitstellen, die auf die externe Datenquelle verweist. Bei Abfragen mit gültigen Verbindungs Zeichenfolgen wird die Datenbank-Engine umgangen, und die Abfrage wird zur Verarbeitung direkt an den externen Datenbankserver übergeben.

> [!TIP]
>  Die bevorzugte Methode zum Arbeiten mit ODBC-Tabellen ist das Anfügen an einen Microsoft Jet (. MDB).

Weitere Informationen finden Sie in den Themen "QueryDef-Objekt", "Querydefs Collection" und "cdbdatabase Object" im DAO SDK.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CDaoQueryDef`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdao.h

##  <a name="append"></a>CDaoQueryDef:: Append

Rufen Sie diese Member-Funktion auf, nachdem Sie [Create](#create) zum Erstellen eines neuen QueryDef-Objekts aufgerufen haben.

```
virtual void Append();
```

### <a name="remarks"></a>Bemerkungen

`Append` speichert QueryDef in der Datenbank, indem das Objekt an die Querydefs-Sammlung der Datenbank angehängt wird. Sie können QueryDef als temporäres Objekt verwenden, ohne es Anhängen zu müssen. Wenn Sie es jedoch beibehalten möchten, müssen Sie `Append`abrufen.

Wenn Sie versuchen, ein temporäres QueryDef-Objekt anzufügen, löst MFC eine Ausnahme vom Typ [CDaoException](../../mfc/reference/cdaoexception-class.md)aus.

##  <a name="canupdate"></a>CDaoQueryDef:: CanUpdate

Mit dieser Member-Funktion können Sie feststellen, ob Sie die QueryDef-– ändern können, beispielsweise den Namen oder die SQL-Zeichenfolge ändern.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Querydef geändert werden darf. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie können QueryDef ändern, wenn:

- Sie basiert nicht auf einer Datenbank, die schreibgeschützt geöffnet ist.

- Sie verfügen über Aktualisierungs Berechtigungen für die Datenbank.

   Dies hängt davon ab, ob Sie Sicherheitsfeatures implementiert haben. MFC bietet keine Unterstützung für die Sicherheit. Sie müssen es selbst implementieren, indem Sie DAO direkt aufrufen oder Microsoft Access verwenden. Weitere Informationen finden Sie im Thema "Berechtigungs Eigenschaft" in der DAO-Hilfe

##  <a name="cdaoquerydef"></a>CDaoQueryDef:: CDaoQueryDef

Erstellt ein `CDaoQueryDef`-Objekt.

```
CDaoQueryDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Parameter

*pdatabase*<br/>
Ein Zeiger auf ein offenes [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) -Objekt.

### <a name="remarks"></a>Bemerkungen

Das-Objekt kann eine vorhandene QueryDef darstellen, die in der Querydefs-Sammlung der Datenbank gespeichert ist, eine neue Abfrage, die in der Auflistung gespeichert werden soll, oder eine temporäre Abfrage, die nicht gespeichert werden soll. Der nächste Schritt hängt vom Typ von QueryDef ab:

- Wenn das-Objekt eine vorhandene QueryDef darstellt, müssen Sie die [Open](#open) Member-Funktion des-Objekts zum Initialisieren des Objekts aufzurufen.

- Wenn das-Objekt eine neue abzuspeichernde QueryDef-Eigenschaft darstellt, rufen Sie die [Create](#create) Member-Funktion des-Objekts auf. Dadurch wird das Objekt der Querydefs-Sammlung der Datenbank hinzugefügt. Anschließend können Sie `CDaoQueryDef` Member-Funktionen aufzurufen, um die Attribute des Objekts festzulegen. Rufen Sie schließlich [Append](#append)auf.

- Wenn das-Objekt einen temporären QueryDef darstellt (nicht in der Datenbank gespeichert), wenden Sie `Create`an, und übergeben Sie eine leere Zeichenfolge für den Namen der Abfrage. Nachdem Sie `Create`aufgerufen haben, initialisieren Sie Querydef, indem Sie die zugehörigen Attribute direkt festlegen. Rufen Sie `Append` nicht auf.

Zum Festlegen der Attribute von Querydef können Sie die Element Funktionen [SetName](#setname), [sezql](#setsql), [SetConnect](#setconnect), [setodbctimeout](#setodbctimeout)und [setreturnsrecords](#setreturnsrecords) verwenden.

Wenn Sie mit dem QueryDef-Objekt fertig sind, müssen Sie dessen [Close](#close) Member-Funktion aufzurufen. Wenn Sie einen Zeiger auf QueryDef haben, verwenden Sie den **Delete** -Operator, um C++ das Objekt zu zerstören.

##  <a name="close"></a>CDaoQueryDef:: Close

Wenn Sie die Verwendung des QueryDef-Objekts beenden, wird diese Member-Funktion aufgerufen.

```
virtual void Close();
```

### <a name="remarks"></a>Bemerkungen

Durch das Schließen von QueryDef wird das zugrunde liegende DAO-Objekt freigegeben, das gespeicherte DAO-Querydef-Objekt oder das C++ `CDaoQueryDef` Objekt wird jedoch nicht zerstört. Dies ist nicht identisch mit [CDaoDatabase::D eletequerydef](../../mfc/reference/cdaodatabase-class.md#deletequerydef), die QueryDef aus der Querydefs-Sammlung der Datenbank in DAO löscht (wenn es sich nicht um eine temporäre QueryDef handelt).

##  <a name="create"></a>CDaoQueryDef:: Create

Rufen Sie diese Member-Funktion auf, um eine neue gespeicherte Abfrage oder eine neue temporäre Abfrage zu erstellen.

```
virtual void Create(
    LPCTSTR lpszName = NULL,
    LPCTSTR lpszSQL = NULL);
```

### <a name="parameters"></a>Parameter

*lpszname*<br/>
Der eindeutige Name der in der Datenbank gespeicherten Abfrage. Ausführliche Informationen über die Zeichenfolge finden Sie im Thema "Methode" der Methode "Methode" in der DAO-Hilfe. Wenn Sie den Standardwert, eine leere Zeichenfolge, übernehmen, wird eine temporäre QueryDef erstellt. Eine solche Abfrage wird nicht in der QueryDefs-Auflistung gespeichert.

*lpszSQL*<br/>
Die SQL-Zeichenfolge, die die Abfrage definiert. Wenn Sie den Standardwert NULL akzeptieren, müssen Sie später [setql](#setsql) zum Festlegen der Zeichenfolge aufzurufen. Bis dahin ist die Abfrage nicht definiert. Sie können jedoch die nicht definierte Abfrage zum Öffnen eines Recordsets verwenden. Weitere Informationen finden Sie in den hinweisen. Die SQL-Anweisung muss definiert werden, bevor Sie QueryDef an die QueryDefs-Auflistung anfügen können.

### <a name="remarks"></a>Bemerkungen

Wenn Sie einen Namen in " *lpszname*" übergeben, können Sie " [Append](#append) " zum Speichern von "QueryDef" in der Querydefs-Sammlung der Datenbank aufzurufen. Andernfalls handelt es sich bei dem Objekt um ein temporäres Querydef, das nicht gespeichert wird. In beiden Fällen befindet sich der QueryDef in einem geöffneten Zustand, und Sie können ihn verwenden, um ein [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) -Objekt zu erstellen oder die [Execute](#execute) Member-Funktion von QueryDef aufzurufen.

Wenn Sie in *lpszSQL*keine SQL-Anweisung angeben, können Sie die Abfrage nicht mit `Execute` ausführen, Sie können Sie jedoch zum Erstellen eines Recordsets verwenden. In diesem Fall verwendet MFC die SQL-Standard Anweisung des Recordsets.

##  <a name="execute"></a>CDaoQueryDef:: Execute

Mit dieser Member-Funktion können Sie die vom QueryDef-Objekt definierte Abfrage ausführen.

```
virtual void Execute(int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Parameter

*noptions*<br/>
Eine ganze Zahl, die die Merkmale der Abfrage bestimmt. Weitere Informationen finden Sie im Thema "Execute Method" in der DAO-Hilfe. Sie können den bitweisen OR-Operator ( **&#124;** ) verwenden, um die folgenden Konstanten für dieses Argument zu kombinieren:

- `dbDenyWrite` die Schreib Berechtigung für andere Benutzer zu verweigern.

- `dbInconsistent` inkonsistente Updates.

- `dbConsistent` konsistente Updates.

- `dbSQLPassThrough` SQL-Pass-Through. Bewirkt, dass die SQL-Anweisung zur Verarbeitung an eine ODBC-Datenbank übermittelt wird.

- der Standardwert `dbFailOnError`. Ausführen eines Rollbacks für Updates, wenn ein Fehler auftritt, und melden des Fehlers an den Benutzer.

- `dbSeeChanges` generieren Sie einen Laufzeitfehler, wenn ein anderer Benutzer die Daten ändert, die Sie bearbeiten.

> [!NOTE]
>  Eine Erläuterung der Begriffe "inkonsistent" und "konsistent" finden Sie im Thema "Execute Method" in der DAO-Hilfe.

### <a name="remarks"></a>Bemerkungen

QueryDef-Objekte, die für die Ausführung auf diese Weise verwendet werden, können nur einen der folgenden Abfrage Typen darstellen:

- Aktions Abfragen

- SQL-Pass-Through-Abfragen

`Execute` funktioniert nicht für Abfragen, die Datensätze zurückgeben, z. b. Select-Abfragen. `Execute` wird häufig für Massen Vorgangs Abfragen verwendet, z. b. **Update**-, **Insert**-oder **SELECT INTO**-Vorgänge oder DDL-Vorgänge (Data Definition Language, Datendefinitionssprache).

> [!TIP]
>  Die bevorzugte Methode zum Arbeiten mit ODBC-Datenquellen ist das Anfügen von Tabellen an einen Microsoft Jet (. MDB). Weitere Informationen finden Sie im Thema zum Zugreifen auf externe Datenbanken mit DAO in der DAO-Hilfe.

Aufrufen der [getrecordsaff-](#getrecordsaffected) Member-Funktion des QueryDef-Objekts, um die Anzahl der Datensätze zu ermitteln, die vom letzten `Execute`-aufrufsaufgerufen werden. `GetRecordsAffected` gibt z. b. Informationen über die Anzahl der Datensätze zurück, die beim Ausführen einer Aktions Abfrage gelöscht, aktualisiert oder eingefügt wurden. Die Anzahl die zurückgegebenen spiegeln sich nicht auf Änderungen in verknüpften Tabellen auf, wenn Cascade aktualisiert oder löscht wirksam sind.

Wenn Sie sowohl `dbInconsistent` als auch `dbConsistent` einschließen, oder wenn Sie keines von beiden einschließen, ist das Ergebnis der Standardwert `dbInconsistent`.

`Execute` gibt kein Recordset zurück. Die Verwendung von `Execute` in einer Abfrage, die Datensätze auswählt, bewirkt, dass MFC eine Ausnahme vom Typ [CDaoException](../../mfc/reference/cdaoexception-class.md)auslöst.

##  <a name="getconnect"></a>CDaoQueryDef:: GetConnect

Mit dieser Member-Funktion können Sie die Verbindungs Zeichenfolge abrufen, die der Datenquelle von QueryDef zugeordnet ist.

```
CString GetConnect();
```

### <a name="return-value"></a>Rückgabewert

Ein [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Wert, der die Verbindungs Zeichenfolge für QueryDef enthält.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird nur für ODBC-Datenquellen und bestimmte ISAM-Treiber verwendet. Es wird nicht mit Microsoft Jet () verwendet. MDB) Datenbanken; in diesem Fall gibt `GetConnect` eine leere Zeichenfolge zurück. Weitere Informationen finden Sie unter [SetConnect](#setconnect).

> [!TIP]
>  Die bevorzugte Methode zum Arbeiten mit ODBC-Tabellen besteht darin, Sie an einen anzufügen. MDB-Datenbank. Weitere Informationen finden Sie im Thema zum Zugreifen auf externe Datenbanken mit DAO in der DAO-Hilfe.

Weitere Informationen zu Verbindungs Zeichenfolgen finden Sie im Thema "Connect Property" in der DAO-Hilfe.

##  <a name="getdatecreated"></a>CDaoQueryDef:: getdatecreated

Mit dieser Member-Funktion können Sie das Datum abrufen, an dem das Querydef-Objekt erstellt wurde.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Rückgabewert

Ein [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) -Objekt, das das Datum und die Uhrzeit der Erstellung von QueryDef enthält.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im Thema "DateCreated, lastupated Properties" in der DAO-Hilfe.

##  <a name="getdatelastupdated"></a>CDaoQueryDef:: getdatelastupveraltet

Mit dieser Member-Funktion wird das Datum der letzten Aktualisierung des QueryDef-Objekts abgerufen – wenn eine ihrer Eigenschaften geändert wurde, z. b. der Name, die zugehörige SQL-Zeichenfolge oder die zugehörige Verbindungs Zeichenfolge.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Rückgabewert

Ein [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) -Objekt, das das Datum und die Uhrzeit des letzten Updates von QueryDef enthält.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im Thema "DateCreated, lastupated Properties" in der DAO-Hilfe.

##  <a name="getfieldcount"></a>CDaoQueryDef:: GetFieldCount

Rufen Sie diese Member-Funktion auf, um die Anzahl der Felder in der Abfrage abzurufen.

```
short GetFieldCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Felder, die in der Abfrage definiert sind.

### <a name="remarks"></a>Bemerkungen

`GetFieldCount` ist zum Durchlaufen aller Felder in QueryDef nützlich. Verwenden Sie zu diesem Zweck `GetFieldCount` in Verbindung mit [getfieldinfo](#getfieldinfo).

##  <a name="getfieldinfo"></a>CDaoQueryDef:: getfieldinfo

Mit dieser Member-Funktion können Sie verschiedene Arten von Informationen zu einem Feld abrufen, das in QueryDef definiert ist.

```
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
Der null basierte Index des gewünschten Felds in der Fields-Auflistung von QueryDef für die Suche nach Index.

*FieldInfo*<br/>
Ein Verweis auf ein `CDaoFieldInfo` Objekt, das die angeforderten Informationen zurückgibt.

*dwinfooptions*<br/>
Optionen, die angeben, welche Informationen über das Feld abgerufen werden sollen. Die verfügbaren Optionen sind hier aufgeführt, zusammen mit der sie die Funktion zurückgibt verursachen:

- AFX_DAO_PRIMARY_INFO (Standard) Name, Typ, Größe, Attribute

- AFX_DAO_SECONDARY_INFO Primärinformationen Plus: Ordinalposition, erforderlich, Null Länge zulassen, Quellfeld, fremd Name, Quell Tabelle, Sortierreihenfolge

- AFX_DAO_ALL_INFO primäre und sekundäre Informationen Plus: Standardwert, Validierungs Text, Validierungs Regel

*lpszname*<br/>
Eine Zeichenfolge, die den Namen des gewünschten Felds für die Suche nach Namen enthält. Sie können ein [CString-Zeichen](../../atl-mfc-shared/reference/cstringt-class.md)verwenden.

### <a name="remarks"></a>Bemerkungen

Eine Beschreibung der Informationen, die in *FieldInfo*zurückgegeben werden, finden Sie in der [cdaofieldinfo](../../mfc/reference/cdaofieldinfo-structure.md) -Struktur. Diese Struktur enthält Member, die den beschreibenden Informationen unter *dwinfooptions* oben entsprechen. Wenn Sie eine Ebene Informationen anfordern, erhalten Sie alle vorherigen Ebenen sowie Informationen.

##  <a name="getname"></a>CDaoQueryDef:: GetName

Rufen Sie diese Member-Funktion auf, um den Namen der durch QueryDef dargestellten Abfrage abzurufen.

```
CString GetName();
```

### <a name="return-value"></a>Rückgabewert

Der Name der Abfrage.

### <a name="remarks"></a>Bemerkungen

Querydef-Namen sind eindeutige benutzerdefinierte Namen. Weitere Informationen zu Querydef-Namen finden Sie im Thema "Name Property" in der DAO-Hilfe.

##  <a name="getodbctimeout"></a>CDaoQueryDef:: getodbctimeout

Rufen Sie diese Member-Funktion auf, um das aktuelle Zeit Limit abzurufen, bevor eine Abfrage an eine ODBC-Datenquelle ein Timeout eintritt.

```
short GetODBCTimeout();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Sekunden, nach denen ein Timeout bei einer Abfrage eintritt.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu diesem Zeit Limit finden Sie im Thema "ODBCTimeout-Eigenschaft" in der DAO-Hilfe.

> [!TIP]
>  Die bevorzugte Methode zum Arbeiten mit ODBC-Tabellen ist das Anfügen an einen Microsoft Jet (. MDB). Weitere Informationen finden Sie im Thema zum Zugreifen auf externe Datenbanken mit DAO in der DAO-Hilfe.

##  <a name="getparametercount"></a>CDaoQueryDef:: GetParameterCount

Rufen Sie diese Member-Funktion auf, um die Anzahl der Parameter in der gespeicherten Abfrage abzurufen.

```
short GetParameterCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Parametern, die in der Abfrage definiert sind.

### <a name="remarks"></a>Bemerkungen

`GetParameterCount` ist zum Durchlaufen aller Parameter in QueryDef nützlich. Verwenden Sie zu diesem Zweck `GetParameterCount` in Verbindung mit [GetParameterInfo](#getparameterinfo).

Weitere Informationen finden Sie in den Themen "Parameter Objekt", "Parameters Collection" und "Parameters Declaration (SQL)" in der DAO-Hilfe.

##  <a name="getparameterinfo"></a>CDaoQueryDef:: GetParameterInfo

Rufen Sie diese Member-Funktion auf, um Informationen zu einem Parameter abzurufen, der in QueryDef definiert ist.

```
void GetParameterInfo(
    int nIndex,
    CDaoParameterInfo& paraminfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetParameterInfo(
    LPCTSTR lpszName,
    CDaoParameterInfo& paraminfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der null basierte Index des gewünschten Parameters in der Parameter Auflistung von QueryDef für die Suche nach Index.

*paramInfo*<br/>
Ein Verweis auf ein [cdaoparameterinfo](../../mfc/reference/cdaoparameterinfo-structure.md) -Objekt, das die angeforderten Informationen zurückgibt.

*dwinfooptions*<br/>
Optionen, die angeben, welche Informationen über den Parameter abgerufen werden sollen. Die verfügbare Option ist hier aufgeführt und gibt an, was die Funktion bewirkt, dass die Funktion zurückgegeben wird:

- AFX_DAO_PRIMARY_INFO (Standard)-Namen, Typ

*lpszname*<br/>
Eine Zeichenfolge, die den Namen des gewünschten Parameters für die Suche nach Namen enthält. Sie können ein [CString-Zeichen](../../atl-mfc-shared/reference/cstringt-class.md)verwenden.

### <a name="remarks"></a>Bemerkungen

Eine Beschreibung der Informationen, die in *paramInfo*zurückgegeben werden, finden Sie in der [cdaoparameterinfo](../../mfc/reference/cdaoparameterinfo-structure.md) -Struktur. Diese Struktur enthält Member, die den beschreibenden Informationen unter *dwinfooptions* oben entsprechen.

Weitere Informationen finden Sie im Thema "Parameter Deklaration (SQL)" in der DAO-Hilfe.

##  <a name="getparamvalue"></a>CDaoQueryDef:: GetParamValue

Rufen Sie diese Member-Funktion auf, um den aktuellen Wert des angegebenen Parameters abzurufen, der in der Parameter Auflistung von QueryDef gespeichert ist.

```
virtual COleVariant GetParamValue(LPCTSTR lpszName);
virtual COleVariant GetParamValue(int nIndex);
```

### <a name="parameters"></a>Parameter

*lpszname*<br/>
Der Name des Parameters, dessen Wert für die Suche nach Name angegeben werden soll.

*nIndex*<br/>
Der null basierte Index des Parameters in der Parameter Auflistung von QueryDef für die Suche nach Index. Sie können diesen Wert mit Aufrufen von " [GetParameterCount](#getparametercount) " und " [GetParameterInfo](#getparameterinfo)" abrufen.

### <a name="return-value"></a>Rückgabewert

Ein Objekt der Klasse [COleVariant](../../mfc/reference/colevariant-class.md) , das den Wert des Parameters enthält.

### <a name="remarks"></a>Bemerkungen

Sie können auf den-Parameter entweder über den Namen oder seine Ordinalposition in der Auflistung zugreifen.

Weitere Informationen finden Sie im Thema "Parameter Deklaration (SQL)" in der DAO-Hilfe.

##  <a name="getrecordsaffected"></a>CDaoQueryDef:: getrecordsafffiziert

Mit dieser Member-Funktion können Sie ermitteln, wie viele Datensätze vom letzten [Execute of Execute](#execute)betroffen waren.

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der betroffenen Datensätze.

### <a name="remarks"></a>Bemerkungen

Die Anzahl die zurückgegebenen spiegeln sich nicht auf Änderungen in verknüpften Tabellen auf, wenn Cascade aktualisiert oder löscht wirksam sind.

Weitere Informationen finden Sie im Thema "recordsaffzierte Eigenschaft" in der DAO-Hilfe.

##  <a name="getreturnsrecords"></a>CDaoQueryDef:: getreturnrecords

Mit dieser Member-Funktion können Sie ermitteln, ob QueryDef auf einer Abfrage basiert, die Datensätze zurückgibt.

```
BOOL GetReturnsRecords();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn QueryDef auf einer Abfrage basiert, die Datensätze zurückgibt. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion wird nur für SQL-Pass-Through-Abfragen verwendet. Weitere Informationen zu SQL-Abfragen finden Sie unter der [Execute](#execute) Member-Funktion. Weitere Informationen zum Arbeiten mit SQL-Pass-Through-Abfragen finden Sie in der Member-Funktion von " [ltreturnrecords](#setreturnsrecords) ".

Weitere Informationen finden Sie im Thema "ReturnsRecords Property" in der DAO-Hilfe.

##  <a name="getsql"></a>CDaoQueryDef:: gezql

Rufen Sie diese Member-Funktion auf, um die SQL-Anweisung abzurufen, die die Abfrage definiert, auf der Querydef basiert.

```
CString GetSQL();
```

### <a name="return-value"></a>Rückgabewert

Die SQL-Anweisung, die die Abfrage definiert, auf der Querydef basiert.

### <a name="remarks"></a>Bemerkungen

Sie werden dann wahrscheinlich die Zeichenfolge für Schlüsselwörter, Tabellennamen usw. analysieren.

Weitere Informationen finden Sie in den Themen "SQL-Eigenschaft", Vergleich von Microsoft Jet Datenbank-Engine SQL und ANSI SQL und "Abfragen einer Datenbank mit SQL in Code" in der DAO-Hilfe.

##  <a name="gettype"></a>CDaoQueryDef:: GetType

Mit dieser Member-Funktion können Sie den Abfragetyp von QueryDef bestimmen.

```
short GetType();
```

### <a name="return-value"></a>Rückgabewert

Der Typ der Abfrage, die von QueryDef definiert wird. Informationen zu-Werten finden Sie unter Hinweise.

### <a name="remarks"></a>Bemerkungen

Der Abfragetyp wird durch den Wert festgelegt, den Sie in der SQL-Zeichenfolge von QueryDef angeben, wenn Sie QueryDef erstellen oder eine vorhandene [setionsql](#setsql) -Member-Funktion von QueryDef aufzurufen. Der Abfragetyp, der von dieser Funktion zurückgegeben wird, kann einen der folgenden Werte aufweisen:

- `dbQSelect` auswählen

- `dbQAction`-Aktion

- `dbQCrosstab` crosstab

- `dbQDelete` löschen

- `dbQUpdate` Update

- `dbQAppend` anfügen

- `dbQMakeTable` Make-Table

- `dbQDDL` Datendefinition

- Pass-Through-`dbQSQLPassThrough`

- `dbQSetOperation` Union

- `dbQSPTBulk` mit `dbQSQLPassThrough` verwendet, um eine Abfrage anzugeben, die keine Datensätze zurückgibt.

> [!NOTE]
>  Um eine SQL-Pass-Through-Abfrage zu erstellen, legen Sie die `dbSQLPassThrough` Konstante nicht fest. Diese wird automatisch von der Microsoft Jet-Datenbank-Engine festgelegt, wenn Sie ein QueryDef-Objekt erstellen und die Verbindungs Zeichenfolge festlegen.

Weitere Informationen zu SQL-Zeichen folgen finden Sie unter [gezql](#getsql). Weitere Informationen zu Abfrage Typen finden Sie unter [Execute](#execute).

##  <a name="isopen"></a>CDaoQueryDef:: IsOpen

Mit dieser Member-Funktion können Sie ermitteln, ob das `CDaoQueryDef` Objekt derzeit geöffnet ist.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das `CDaoQueryDef` Objekt derzeit geöffnet ist. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Eine QueryDef muss sich in einem geöffneten Zustand befinden, bevor Sie zum [Ausführen von Execute](#execute) oder zum Erstellen eines [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) -Objekts verwendet werden kann. Um eine QueryDef in einen geöffneten Status aufzurufen, [Erstellen](#create) Sie entweder (für ein neues QueryDef) oder [Öffnen](#open) (für eine vorhandene QueryDef).

##  <a name="m_pdatabase"></a>CDaoQueryDef:: m_pDatabase

Enthält einen Zeiger auf das [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) -Objekt, das dem QueryDef-Objekt zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diesen Zeiger, wenn Sie direkt auf die Datenbank zugreifen müssen, z. –. um Zeiger auf andere QueryDef-oder Recordset-Objekte in den Auflistungen der Datenbank zu erhalten.

##  <a name="m_pdaoquerydef"></a>CDaoQueryDef:: m_pDAOQueryDef

Enthält einen Zeiger auf die OLE-Schnittstelle für das zugrunde liegende DAO Querydef-Objekt.

### <a name="remarks"></a>Bemerkungen

Dieser Zeiger wird aus Gründen der Vollständigkeit und Konsistenz mit den anderen Klassen bereitgestellt. Da der MFC DAO-Querydefs jedoch nicht vollständig kapselt, ist es unwahrscheinlich, dass Sie ihn benötigen. Wenn Sie dies tun, sollten Sie dies vorsichtig – insbesondere den Wert des Zeigers nicht ändern, es sei denn, Sie wissen, was Sie tun.

##  <a name="open"></a>CDaoQueryDef:: Open

Mit dieser Member-Funktion Öffnen Sie eine Querydef, die zuvor in der Querydefs-Sammlung der Datenbank gespeichert wurde.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Parameter

*lpszname*<br/>
Eine Zeichenfolge, die den Namen der gespeicherten abzuöffnenden QueryDef-Datei enthält. Sie können ein [CString-Zeichen](../../atl-mfc-shared/reference/cstringt-class.md)verwenden.

### <a name="remarks"></a>Bemerkungen

Nachdem QueryDef geöffnet ist, können Sie seine [Execute](#execute) Member-Funktion oder QueryDef verwenden, um ein [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) -Objekt zu erstellen.

##  <a name="setconnect"></a>CDaoQueryDef:: SetConnect

Mit dieser Member-Funktion wird die Verbindungs Zeichenfolge des QueryDef-Objekts festgelegt.

```
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Parameter

*lpszconnect*<br/>
Eine Zeichenfolge, die eine Verbindungs Zeichenfolge für das zugeordnete [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) -Objekt enthält.

### <a name="remarks"></a>Bemerkungen

Die Verbindungszeichenfolge wird zum Übergeben zusätzlicher Informationen auf ODBC und nach Bedarf bestimmte ISAM-Treiber verwendet. Er wird nicht für Microsoft Jet (. MDB).

> [!TIP]
>  Die bevorzugte Methode zum Arbeiten mit ODBC-Tabellen besteht darin, Sie an einen anzufügen. MDB-Datenbank.

Bevor Sie eine QueryDef ausführen, die eine SQL-Pass-Through-Abfrage an eine ODBC-Datenquelle darstellt, legen Sie die Verbindungs Zeichenfolge mit `SetConnect` fest, und geben Sie [setreturnrecords](#setreturnsrecords) an, um anzugeben, ob die Abfrage Datensätze

Weitere Informationen zur Struktur der Verbindungs Zeichenfolge und Beispiele für Verbindungs Zeichenfolgen-Komponenten finden Sie im Thema "Connect Property" in der DAO-Hilfe.

##  <a name="setname"></a>CDaoQueryDef:: SetName

Wenn Sie den Namen einer nicht temporären QueryDef ändern möchten, wird diese Member-Funktion aufgerufen.

```
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parameter

*lpszname*<br/>
Eine Zeichenfolge, die den neuen Namen für eine nicht temporäre Abfrage im zugeordneten [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) -Objekt enthält.

### <a name="remarks"></a>Bemerkungen

Querydef-Namen sind eindeutige und benutzerdefinierte Namen. Sie können `SetName` vor dem Anhängen des QueryDef-Objekts an die QueryDefs-Auflistung abrufen.

##  <a name="setodbctimeout"></a>CDaoQueryDef:: abkout

Mit dieser Member-Funktion können Sie das Zeitlimit festlegen, bevor für eine Abfrage einer ODBC-Datenquelle ein Timeout auftritt.

```
void SetODBCTimeout(short nODBCTimeout);
```

### <a name="parameters"></a>Parameter

*nodbctimeout*<br/>
Die Anzahl von Sekunden, nach denen ein Timeout bei einer Abfrage eintritt.

### <a name="remarks"></a>Bemerkungen

Mit dieser Member-Funktion können Sie die Standard Anzahl von Sekunden vor nachfolgenden Vorgängen für die verbundene Datenquelle außer Kraft setzen. Ein Vorgang kann aufgrund von Netzwerkproblemen für den Zugriff, übermäßige Abfrage Verarbeitungszeit und usw. Timeout. Ruft `SetODBCTimeout` vor dem Ausführen einer Abfrage mit diesem QueryDef-Wert auf, wenn Sie den Timeout Wert der Abfrage ändern möchten. (Da ODBC Verbindungen wieder verwendet, ist der Timeout Wert für alle Clients derselben Verbindung identisch.)

Der Standardwert für die Abfragetimeouts beträgt 60 Sekunden.

##  <a name="setparamvalue"></a>CDaoQueryDef:: SetParamValue

Mit dieser Member-Funktion können Sie den Wert eines Parameters in QueryDef zur Laufzeit festlegen.

```
virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);

virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);
```

### <a name="parameters"></a>Parameter

*lpszname*<br/>
Der Name des Parameters, dessen Wert Sie festlegen möchten.

*varValue*<br/>
Der festzulegende Wert. siehe Hinweise.

*nIndex*<br/>
Die Ordinalposition des Parameters in der Parameter Auflistung von QueryDef. Sie können diesen Wert mit Aufrufen von " [GetParameterCount](#getparametercount) " und " [GetParameterInfo](#getparameterinfo)" abrufen.

### <a name="remarks"></a>Bemerkungen

Der-Parameter muss bereits als Teil der SQL-Zeichenfolge von QueryDef eingerichtet worden sein. Sie können auf den-Parameter entweder über den Namen oder seine Ordinalposition in der Auflistung zugreifen.

Geben Sie den Wert an, der als `COleVariant` Objekt festgelegt werden soll. Weitere Informationen zum Festlegen des gewünschten Werts und zum Eingeben des `COleVariant` Objekts finden Sie Unterklasse [COleVariant](../../mfc/reference/colevariant-class.md).

##  <a name="setreturnsrecords"></a>CDaoQueryDef:: abtreturnrecords

Diese Member-Funktion als Teil des Prozesses zum Einrichten einer SQL-Pass-Through-Abfrage an eine externe Datenbank aufzurufen.

```
void SetReturnsRecords(BOOL bReturnsRecords);
```

### <a name="parameters"></a>Parameter

*breturnrecords*<br/>
Übergeben Sie true, wenn die Abfrage für eine externe Datenbank Datensätze zurückgibt. andernfalls false.

### <a name="remarks"></a>Bemerkungen

In einem solchen Fall müssen Sie QueryDef erstellen und seine Eigenschaften mit anderen `CDaoQueryDef`-Element Funktionen festlegen. Eine Beschreibung externer Datenbanken finden Sie unter [SetConnect](#setconnect).

##  <a name="setsql"></a>CDaoQueryDef:: s

Mit dieser Member-Funktion legen Sie die SQL-Anweisung fest, die von QueryDef ausgeführt wird.

```
void SetSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Parameter

*lpszSQL*<br/>
Eine Zeichenfolge, die eine für die Ausführung geeignete vollständige SQL-Anweisung enthält. Die Syntax dieser Zeichenfolge hängt von dem DBMS ab, auf das die Abfrage abzielt. Eine Erläuterung der Syntax, die in der Microsoft Jet-Datenbank-Engine verwendet wird, finden Sie im Thema "Building SQL-Anweisungen in Code" in der DAO-Hilfe.

### <a name="remarks"></a>Bemerkungen

Eine typische Verwendung von `SetSQL` ist das Einrichten eines QueryDef-Objekts für die Verwendung in einer SQL-Pass-Through-Abfrage. (Informationen zur Syntax von SQL-Pass-Through-Abfragen für das Ziel-DBMS finden Sie in der Dokumentation zu Ihrem DBMS.)

## <a name="see-also"></a>Weitere Informationen

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset-Klasse](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoDatabase-Klasse](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoTableDef-Klasse](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoException-Klasse](../../mfc/reference/cdaoexception-class.md)
