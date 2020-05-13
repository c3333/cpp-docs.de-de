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
ms.openlocfilehash: ed298c40daa9485683d0b989e47b97fdce9f6562
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754711"
---
# <a name="cdaoquerydef-class"></a>CDaoQueryDef-Klasse

Stellt eine Abfragedefinition ("Querydef") dar, die in einer Datenbank gespeichert ist.

## <a name="syntax"></a>Syntax

```
class CDaoQueryDef : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoQueryDef::CDaoQueryDef](#cdaoquerydef)|Erstellt ein `CDaoQueryDef`-Objekt. Nächster `Open` Anruf `Create`oder , je nach Ihren Anforderungen.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoQueryDef::Anfügen](#append)|Fügt die querydef als gespeicherte Abfrage an die QueryDefs-Auflistung der Datenbank an.|
|[CDaoQueryDef::CanUpdate](#canupdate)|Gibt einen Wert ungleich Null zurück, wenn die Abfrage die Datenbank aktualisieren kann.|
|[CDaoQueryDef::Schließen](#close)|Schließt das querydef-Objekt. Zerstören Sie das C++-Objekt, wenn Sie damit fertig sind.|
|[CDaoQueryDef::Erstellen](#create)|Erstellt das zugrunde liegende DAO querydef-Objekt. Verwenden Sie die querydef als `Append` temporäre Abfrage, oder rufen Sie sie auf, um sie in der Datenbank zu speichern.|
|[CDaoQueryDef::Ausführen](#execute)|Führt die vom querydef-Objekt definierte Abfrage aus.|
|[CDaoQueryDef::GetConnect](#getconnect)|Gibt die Verbindungszeichenfolge zurück, die der querydef zugeordnet ist. Die Verbindungszeichenfolge identifiziert die Datenquelle. (Nur für SQL-Pass-Through-Abfragen, andernfalls eine leere Zeichenfolge.)|
|[CDaoQueryDef::GetDateCreated](#getdatecreated)|Gibt das Datum zurück, an dem die gespeicherte Abfrage erstellt wurde.|
|[CDaoQueryDef::GetDateLastUpdated](#getdatelastupdated)|Gibt das Datum zurück, an dem die gespeicherte Abfrage zuletzt aktualisiert wurde.|
|[CDaoQueryDef::GetFieldCount](#getfieldcount)|Gibt die Anzahl der von der querydef definierten Felder zurück.|
|[CDaoQueryDef::GetFieldInfo](#getfieldinfo)|Gibt Informationen zu einem in der Abfrage definierten Feld zurück.|
|[CDaoQueryDef::GetName](#getname)|Gibt den Namen der querydef zurück.|
|[CDaoQueryDef::GetODBCTimeout](#getodbctimeout)|Gibt den Timeoutwert zurück, der von ODBC (für eine ODBC-Abfrage) verwendet wird, wenn die querydef ausgeführt wird. Dadurch wird bestimmt, wie lange die Aktion der Abfrage abgeschlossen werden soll.|
|[CDaoQueryDef::GetParameterCount](#getparametercount)|Gibt die Anzahl der für die Abfrage definierten Parameter zurück.|
|[CDaoQueryDef::GetParameterInfo](#getparameterinfo)|Gibt Informationen zu einem angegebenen Parameter an die Abfrage zurück.|
|[CDaoQueryDef::GetParamValue](#getparamvalue)|Gibt den Wert eines angegebenen Parameters an die Abfrage zurück.|
|[CDaoQueryDef::GetRecordsAffected](#getrecordsaffected)|Gibt die Anzahl der Datensätze zurück, die von einer Aktionsabfrage betroffen sind.|
|[CDaoQueryDef::GetReturnsRecords](#getreturnsrecords)|Gibt einen Wert ungleich Null zurück, wenn die von der querydef definierte Abfrage Datensätze zurückgibt.|
|[CDaoQueryDef::GetSQL](#getsql)|Gibt die SQL-Zeichenfolge zurück, die die von der querydef definierte Abfrage angibt.|
|[CDaoQueryDef::GetType](#gettype)|Gibt den Abfragetyp zurück: Löschen, Aktualisieren, Anfügen, Make-Table usw.|
|[CDaoQueryDef::IsOpen](#isopen)|Gibt einen Wert ungleich Null zurück, wenn die querydef geöffnet ist und ausgeführt werden kann.|
|[CDaoQueryDef::Öffnen](#open)|Öffnet eine vorhandene Querydef, die in der QueryDefs-Auflistung der Datenbank gespeichert ist.|
|[CDaoQueryDef::SetConnect](#setconnect)|Legt die Verbindungszeichenfolge für eine SQL-Pass-Through-Abfrage für eine ODBC-Datenquelle fest.|
|[CDaoQueryDef::SetName](#setname)|Legt den Namen der gespeicherten Abfrage fest und ersetzt den Namen, der beim Erstellen der querydef verwendet wurde.|
|[CDaoQueryDef::SetODBCTimeout](#setodbctimeout)|Legt den Timeoutwert fest, der von ODBC (für eine ODBC-Abfrage) verwendet wird, wenn die querydef ausgeführt wird.|
|[CDaoQueryDef::SetParamValue](#setparamvalue)|Legt den Wert eines angegebenen Parameters für die Abfrage fest.|
|[CDaoQueryDef::SetReturnsRecords](#setreturnsrecords)|Gibt an, ob die querydef Datensätze zurückgibt. Das Festlegen dieses Attributs auf TRUE ist nur für SQL-Pass-Through-Abfragen gültig.|
|[CDaoQueryDef::SetSQL](#setsql)|Legt die SQL-Zeichenfolge fest, die die von der querydef definierte Abfrage angibt.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoQueryDef::m_pDAOQueryDef](#m_pdaoquerydef)|Ein Zeiger auf die OLE-Schnittstelle für das zugrunde liegende DAO-Querydef-Objekt.|
|[CDaoQueryDef::m_pDatabase](#m_pdatabase)|Ein Zeiger auf `CDaoDatabase` das Objekt, dem die querydef zugeordnet ist. Die querydef wird möglicherweise in der Datenbank gespeichert oder nicht.|

## <a name="remarks"></a>Bemerkungen

Ein querydef ist ein Datenzugriffsobjekt, das die SQL-Anweisung enthält, die eine Abfrage beschreibt, und ihre Eigenschaften, z. B. "Datum erstellt" und "ODBC Timeout". Sie können auch temporäre querydef-Objekte erstellen, ohne sie zu speichern, aber es ist bequem – und viel effizienter – häufig wiederverwendete Abfragen in einer Datenbank zu speichern. Ein [CDaoDatabase-Objekt](../../mfc/reference/cdaodatabase-class.md) verwaltet eine Auflistung, die als QueryDefs-Auflistung bezeichnet wird und die gespeicherte querydefs enthält.

> [!NOTE]
> Die DAO-Datenbankklassen unterscheiden sich von den MFC-Datenbankklassen, die auf Open Database Connectivity (ODBC) basieren. Alle DAO-Datenbankklassennamen haben das Präfix "CDao". Sie können weiterhin mit den DAO-Klassen auf ODBC-Datenquellen zugreifen. Im Allgemeinen sind die Aufbasis von DAO basierenden MFC-Klassen leistungsfähiger als die MFC-Klassen, die auf ODBC basieren. Die DAO-basierten Klassen können über ihre eigene Datenbank-Engine auf Daten zugreifen, auch über ODBC-Treiber. Die DAO-basierten Klassen unterstützen auch DDL-Vorgänge (Data Definition Language), z. B. das Hinzufügen von Tabellen über die Klassen, ohne DAO direkt aufrufen zu müssen.

## <a name="usage"></a>Verwendung

Verwenden Sie querydef-Objekte, um entweder mit einer vorhandenen gespeicherten Abfrage zu arbeiten oder eine neue gespeicherte oder temporäre Abfrage zu erstellen:

1. Erstellen Sie in allen `CDaoQueryDef` Fällen zuerst ein Objekt und geben Sie einen Zeiger auf das [CDaoDatabase-Objekt](../../mfc/reference/cdaodatabase-class.md) an, zu dem die Abfrage gehört.

1. Gehen Sie dann wie folgt vor, je nachdem, was Sie möchten:

   - Um eine vorhandene gespeicherte Abfrage zu verwenden, rufen Sie die [Memberfunktion "Öffnen"](#open) des querydef-Objekts auf und geben den Namen der gespeicherten Abfrage an.

   - Um eine neue gespeicherte Abfrage zu erstellen, rufen Sie die Memberfunktion [Create](#create) des querydef-Objekts auf und geben den Namen der Abfrage an. Rufen Sie dann [Append](#append) auf, um die Abfrage zu speichern, indem Sie sie an die QueryDefs-Auflistung der Datenbank anhängen. `Create`setzt die querydef in einen offenen `Create` Zustand, `Open`sodass Sie nach dem Aufruf nicht aufrufen.

   - Um eine temporäre querydef `Create`zu erstellen, rufen Sie auf. Übergeben Sie eine leere Zeichenfolge für den Abfragenamen. Rufen Sie `Append` nicht auf.

Wenn Sie die Verwendung eines querydef-Objekts abgeschlossen haben, rufen Sie die Memberfunktion [Schließen](#close) auf. dann das querydef-Objekt zerstören.

> [!TIP]
> Die einfachste Möglichkeit, gespeicherte Abfragen zu erstellen, besteht darin, sie zu erstellen und mit Microsoft Access in Ihrer Datenbank zu speichern. Dann können Sie sie öffnen und in Ihrem MFC-Code verwenden.

## <a name="purposes"></a>Zwecke

Sie können ein querydef-Objekt für einen der folgenden Zwecke verwenden:

- So erstellen `CDaoRecordset` Sie ein Objekt

- So rufen Sie `Execute` die Memberfunktion des Objekts auf, um eine Aktionsabfrage oder eine SQL-Pass-Through-Abfrage direkt auszuführen

Sie können ein querydef-Objekt für jeden Abfragetyp verwenden, einschließlich Auswahl-, Aktions-, Kreuztabelle-, Lösch-, Aktualisierungs-, Anhängen-, Tabellen-, Datendefinitions-, SQL-Pass-Through-, Union- und Massenabfragen. Der Typ der Abfrage wird durch den Inhalt der SQL-Anweisung bestimmt, die Sie bereitstellen. Informationen zu Abfragetypen finden `Execute` Sie unter und [GetType-Memberfunktionen.](#gettype) Recordsets werden häufig für zeilengebende Abfragen verwendet, in der Regel diejenigen, die die **SELECT ... **FROM-Schlüsselwörter. `Execute`wird am häufigsten für Massenvorgänge verwendet. Weitere Informationen finden Sie unter [Ausführen](#execute) und [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

## <a name="querydefs-and-recordsets"></a>Querydefs und Recordsets

Um ein querydef-Objekt `CDaoRecordset` zum Erstellen eines Objekts zu verwenden, erstellen oder öffnen Sie in der Regel eine querydef wie oben beschrieben. Erstellen Sie dann ein Recordset-Objekt und übergeben Sie einen Zeiger an Ihr querydef-Objekt, wenn Sie [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open)aufrufen. Die querydef, die Sie übergeben, muss sich in einem offenen Zustand befinden. Weitere Informationen finden Sie unter Klasse [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Sie können eine querydef nicht verwenden, um ein Recordset (die häufigste Verwendung für eine querydef) zu erstellen, es sei denn, es befindet sich in einem offenen Zustand. Setzen Sie die querydef in `Open` einen `Create`offenen Zustand, indem Sie entweder oder aufrufen.

## <a name="external-databases"></a>Externe Datenbanken

Querydef-Objekte sind die bevorzugte Methode zur Verwendung des systemeigenen SQL-Dialekts eines externen Datenbankmoduls. Sie können z. B. eine Transact SQL-Abfrage (wie in Microsoft SQL Server verwendet) erstellen und in einem querydef-Objekt speichern. Wenn Sie eine SQL-Abfrage verwenden müssen, die nicht auf dem Microsoft Jet-Datenbankmodul basiert, müssen Sie eine Verbindungszeichenfolge angeben, die auf die externe Datenquelle verweist. Abfragen mit gültigen Verbindungszeichenfolgen umgehen das Datenbankmodul und übergeben die Abfrage zur Verarbeitung direkt an den externen Datenbankserver.

> [!TIP]
> Die bevorzugte Methode zum Arbeiten mit ODBC-Tabellen besteht darin, sie an einen Microsoft Jet (. MDB)-Datenbank.

Weitere Informationen finden Sie in den Themen "QueryDef Object", "QueryDefs Collection" und "CdbDatabase Object" im DAO SDK.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CDaoQueryDef`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdao.h

## <a name="cdaoquerydefappend"></a><a name="append"></a>CDaoQueryDef::Anfügen

Rufen Sie diese Memberfunktion auf, nachdem Sie [Create](#create) aufrufen, um ein neues querydef-Objekt zu erstellen.

```
virtual void Append();
```

### <a name="remarks"></a>Bemerkungen

`Append`speichert die querydef in der Datenbank, indem das Objekt an die QueryDefs-Auflistung der Datenbank angehängt wird. Sie können die querydef als temporäres Objekt verwenden, ohne es anzuhängen, aber wenn Sie möchten, dass es beibehalten wird, müssen Sie aufrufen. `Append`

Wenn Sie versuchen, ein temporäres querydef-Objekt anzuhängen, löst MFC eine Ausnahme vom Typ [CDaoException](../../mfc/reference/cdaoexception-class.md)aus.

## <a name="cdaoquerydefcanupdate"></a><a name="canupdate"></a>CDaoQueryDef::CanUpdate

Rufen Sie diese Memberfunktion auf, um zu bestimmen, ob Sie die querydef ändern können, z. B. den Namen oder die SQL-Zeichenfolge ändern.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn Sie die querydef ändern dürfen; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie können die querydef ändern, wenn:

- Sie basiert nicht auf einer datenbank, die schreibgeschützt geöffnet ist.

- Sie verfügen über Aktualisierungsberechtigungen für die Datenbank.

   Dies hängt davon ab, ob Sie Sicherheitsfunktionen implementiert haben. MFC bietet keine Unterstützung für die Sicherheit. Sie müssen es selbst implementieren, indem Sie DAO direkt oder mit Microsoft Access aufrufen. Siehe das Thema "Berechtigungseigenschaft" in der DAO-Hilfe.

## <a name="cdaoquerydefcdaoquerydef"></a><a name="cdaoquerydef"></a>CDaoQueryDef::CDaoQueryDef

Erstellt ein `CDaoQueryDef`-Objekt.

```
CDaoQueryDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Parameter

*pDatabase*<br/>
Ein Zeiger auf ein geöffnetes [CDaoDatabase-Objekt.](../../mfc/reference/cdaodatabase-class.md)

### <a name="remarks"></a>Bemerkungen

Das Objekt kann eine vorhandene Querydef darstellen, die in der QueryDefs-Auflistung der Datenbank gespeichert ist, eine neue Abfrage, die in der Auflistung gespeichert werden soll, oder eine temporäre Abfrage, die nicht gespeichert werden soll. Der nächste Schritt hängt vom Typ der querydef ab:

- Wenn das Objekt eine vorhandene querydef darstellt, rufen Sie die [Open-Memberfunktion](#open) des Objekts auf, um es zu initialisieren.

- Wenn das Objekt eine neue querydef darstellt, die gespeichert werden soll, rufen Sie die [Memberfunktion Create](#create) des Objekts auf. Dadurch wird das Objekt zur QueryDefs-Auflistung der Datenbank hinzugefügt. Rufen `CDaoQueryDef` Sie dann Memberfunktionen auf, um die Attribute des Objekts festzulegen. Rufen Sie schließlich [Append auf.](#append)

- Wenn das Objekt eine temporäre querydef darstellt (nicht `Create`in der Datenbank gespeichert werden soll), rufen Sie auf , indem Sie eine leere Zeichenfolge für den Namen der Abfrage übergeben. Nach `Create`dem Aufruf initialisieren Sie die querydef, indem Sie ihre Attribute direkt festlegen. Rufen Sie `Append` nicht auf.

Um die Attribute der querydef festzulegen, können Sie die Memberfunktionen [SetName](#setname), [SetSQL](#setsql), [SetConnect](#setconnect), [SetODBCTimeout](#setodbctimeout)und [SetReturnsRecords](#setreturnsrecords) verwenden.

Wenn Sie mit dem querydef-Objekt fertig sind, rufen Sie die Memberfunktion [Schließen](#close) auf. Wenn Sie über einen Zeiger auf die **delete** querydef verfügen, verwenden Sie den delete-Operator, um das C++-Objekt zu zerstören.

## <a name="cdaoquerydefclose"></a><a name="close"></a>CDaoQueryDef::Schließen

Rufen Sie diese Memberfunktion auf, wenn Sie die Verwendung des querydef-Objekts beenden.

```
virtual void Close();
```

### <a name="remarks"></a>Bemerkungen

Beim Schließen der querydef wird das zugrunde liegende DAO-Objekt freigegeben, aber `CDaoQueryDef` das gespeicherte DAO querydef-Objekt oder das C++-Objekt werden nicht zerstört. Dies ist nicht dasselbe wie [CDaoDatabase::DeleteQueryDef](../../mfc/reference/cdaodatabase-class.md#deletequerydef), das die querydef aus der QueryDefs-Auflistung der Datenbank in DAO löscht (wenn nicht eine temporäre querydef).

## <a name="cdaoquerydefcreate"></a><a name="create"></a>CDaoQueryDef::Erstellen

Rufen Sie diese Memberfunktion auf, um eine neue gespeicherte Abfrage oder eine neue temporäre Abfrage zu erstellen.

```
virtual void Create(
    LPCTSTR lpszName = NULL,
    LPCTSTR lpszSQL = NULL);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
Der eindeutige Name der in der Datenbank gespeicherten Abfrage. Weitere Informationen zur Zeichenfolge finden Sie im Thema "CreateQueryDef-Methode" in der DAO-Hilfe. Wenn Sie den Standardwert, eine leere Zeichenfolge, eine temporäre querydef, akzeptieren, wird eine temporäre querydef erstellt. Eine solche Abfrage wird nicht in der QueryDefs-Auflistung gespeichert.

*Lpszsql*<br/>
Die SQL-Zeichenfolge, die die Abfrage definiert. Wenn Sie den Standardwert NULL akzeptieren, müssen Sie später [SetSQL](#setsql) aufrufen, um die Zeichenfolge festzulegen. Bis dahin ist die Abfrage nicht definiert. Sie können jedoch die nicht definierte Abfrage verwenden, um ein Recordset zu öffnen. Siehe Hinweise für Details. Die SQL-Anweisung muss definiert werden, bevor Sie die querydef an die QueryDefs-Auflistung anhängen können.

### <a name="remarks"></a>Bemerkungen

Wenn Sie einen Namen in *lpszName*übergeben, können Sie [dann Append](#append) aufrufen, um die querydef in der QueryDefs-Auflistung der Datenbank zu speichern. Andernfalls ist das Objekt eine temporäre querydef und wird nicht gespeichert. In beiden Fällen befindet sich die querydef in einem offenen Zustand, und Sie können sie entweder zum Erstellen eines [CDaoRecordset-Objekts](../../mfc/reference/cdaorecordset-class.md) verwenden oder die [Execute-Memberfunktion](#execute) der querydef aufrufen.

Wenn Sie keine SQL-Anweisung in *lpszSQL*angeben, `Execute` können Sie die Abfrage nicht mit ausführen, aber Sie können sie verwenden, um ein Recordset zu erstellen. In diesem Fall verwendet MFC die SQL-Standardanweisung des Recordsets.

## <a name="cdaoquerydefexecute"></a><a name="execute"></a>CDaoQueryDef::Ausführen

Rufen Sie diese Memberfunktion auf, um die vom querydef-Objekt definierte Abfrage auszuführen.

```
virtual void Execute(int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Parameter

*nOptionen*<br/>
Eine ganze Zahl, die die Eigenschaften der Abfrage bestimmt. Weitere Informationen finden Sie im Thema "Ausführungsmethode" in der DAO-Hilfe. Sie können den Bitwise-OR-Operator ( **&#124;**) verwenden, um die folgenden Konstanten für dieses Argument zu kombinieren:

- `dbDenyWrite`Verweigern Sie anderen Benutzern schreibberechtigte Berechtigungen.

- `dbInconsistent`Inkonsistente Aktualisierungen.

- `dbConsistent`Konsistente Aktualisierungen.

- `dbSQLPassThrough`SQL-Pass-Through. Bewirkt, dass die SQL-Anweisung zur Verarbeitung an eine ODBC-Datenbank übergeben wird.

- `dbFailOnError`Standardwert. Rollbackaktualisierungen, wenn ein Fehler auftritt, und melden Sie den Fehler an den Benutzer.

- `dbSeeChanges`Generieren Sie einen Laufzeitfehler, wenn ein anderer Benutzer Die von Ihnen bearbeiteten Daten ändert.

> [!NOTE]
> Eine Erläuterung der Begriffe "inkonsistent" und "konsistent" finden Sie im Thema "Ausführungsmethode" in der DAO-Hilfe.

### <a name="remarks"></a>Bemerkungen

Querydef-Objekte, die auf diese Weise für die Ausführung verwendet werden, können nur einen der folgenden Abfragetypen darstellen:

- Aktionsabfragen

- SQL-Pass-Through-Abfragen

`Execute`funktioniert nicht für Abfragen, die Datensätze zurückgeben, z. B. Ausgewählte Abfragen. `Execute`wird häufig für Massenvorgangsabfragen wie **UPDATE**, **INSERT**oder **SELECT INTO**oder für DDL-Vorgänge (Data Definition Language) verwendet.

> [!TIP]
> Die bevorzugte Methode zum Arbeiten mit ODBC-Datenquellen besteht darin, Tabellen an einen Microsoft Jet (. MDB)-Datenbank. Weitere Informationen finden Sie im Thema "Zugriff auf externe Datenbanken mit DAO" in der DAO-Hilfe.

Rufen Sie die [GetRecordsAffected-Memberfunktion](#getrecordsaffected) des querydef-Objekts auf, `Execute` um die Anzahl der Datensätze zu ermitteln, die vom letzten Aufruf betroffen sind. Gibt `GetRecordsAffected` beispielsweise Informationen über die Anzahl der Datensätze zurück, die beim Ausführen einer Aktionsabfrage gelöscht, aktualisiert oder eingefügt wurden. Die zurückgegebene Anzahl spiegelt keine Änderungen in verknüpften Tabellen wider, wenn kaskadierte Aktualisierungen oder Löschungen wirksam sind.

Wenn Sie `dbInconsistent` beides einschließen und `dbConsistent` oder wenn Sie `dbInconsistent`keines der beiden einschließen, ist das Ergebnis der Standardwert .

`Execute`gibt kein Recordset zurück. Die `Execute` Verwendung einer Abfrage, die Datensätze auswählt, bewirkt, dass MFC eine Ausnahme vom Typ [CDaoException](../../mfc/reference/cdaoexception-class.md)auslöst.

## <a name="cdaoquerydefgetconnect"></a><a name="getconnect"></a>CDaoQueryDef::GetConnect

Rufen Sie diese Memberfunktion auf, um die Verbindungszeichenfolge abzurufen, die der Datenquelle der querydef zugeordnet ist.

```
CString GetConnect();
```

### <a name="return-value"></a>Rückgabewert

Ein [CString,](../../atl-mfc-shared/reference/cstringt-class.md) der die Verbindungszeichenfolge für die querydef enthält.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird nur mit ODBC-Datenquellen und bestimmten ISAM-Treibern verwendet. Es wird nicht mit Microsoft Jet (. MDB)-Datenbanken; Gibt in `GetConnect` diesem Fall eine leere Zeichenfolge zurück. Weitere Informationen finden Sie unter [SetConnect](#setconnect).

> [!TIP]
> Die bevorzugte Methode zum Arbeiten mit ODBC-Tabellen besteht darin, sie an eine anzuhängen. MDB-Datenbank. Weitere Informationen finden Sie im Thema "Zugriff auf externe Datenbanken mit DAO" in der DAO-Hilfe.

Informationen zu Verbindungszeichenfolgen finden Sie im Thema "Connect Property" in der DAO-Hilfe.

## <a name="cdaoquerydefgetdatecreated"></a><a name="getdatecreated"></a>CDaoQueryDef::GetDateCreated

Rufen Sie diese Memberfunktion auf, um das Datum abzurufen, an dem das querydef-Objekt erstellt wurde.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Rückgabewert

Ein [COleDateTime-Objekt,](../../atl-mfc-shared/reference/coledatetime-class.md) das das Datum und die Uhrzeit enthält, zu der die Querydef erstellt wurde.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im Thema "DateCreated, LastUpdated Properties" in der DAO-Hilfe.

## <a name="cdaoquerydefgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoQueryDef::GetDateLastUpdated

Rufen Sie diese Memberfunktion auf, um das Datum abzurufen, an dem das querydef-Objekt zuletzt aktualisiert wurde, wenn eine seiner Eigenschaften geändert wurde, z. B. der Name, die SQL-Zeichenfolge oder die Verbindungszeichenfolge.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Rückgabewert

Ein [COleDateTime-Objekt,](../../atl-mfc-shared/reference/coledatetime-class.md) das das Datum und die Uhrzeit enthält, zu der die Querydef zuletzt aktualisiert wurde.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im Thema "DateCreated, LastUpdated Properties" in der DAO-Hilfe.

## <a name="cdaoquerydefgetfieldcount"></a><a name="getfieldcount"></a>CDaoQueryDef::GetFieldCount

Rufen Sie diese Memberfunktion auf, um die Anzahl der Felder in der Abfrage abzurufen.

```
short GetFieldCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der in der Abfrage definierten Felder.

### <a name="remarks"></a>Bemerkungen

`GetFieldCount`ist nützlich, um alle Felder in der querydef zu durchlaufen. Verwenden Sie `GetFieldCount` zu diesem Zweck in Verbindung mit [GetFieldInfo](#getfieldinfo).

## <a name="cdaoquerydefgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoQueryDef::GetFieldInfo

Rufen Sie diese Memberfunktion auf, um verschiedene Arten von Informationen zu einem Feld abzurufen, das in der querydef definiert ist.

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
Der nullbasierte Index des gewünschten Felds in der Fields-Auflistung der querydef für die Suche nach Index.

*Fieldinfo*<br/>
Ein Verweis `CDaoFieldInfo` auf ein Objekt, das die angeforderten Informationen zurückgibt.

*dwInfoOptionen*<br/>
Optionen, die angeben, welche Informationen über das abzurufende Feld abgerufen werden sollen. Die verfügbaren Optionen sind hier zusammen mit dem, was die Funktion zurückgeben lässt aufgeführt:

- AFX_DAO_PRIMARY_INFO (Standard) Name, Typ, Größe, Attribute

- AFX_DAO_SECONDARY_INFO Primärinformationen plus: Ordinalposition, Erforderlich, Nulllänge zulassen, Quellfeld, Fremdname, Quelltabelle, Sortierreihenfolge

- AFX_DAO_ALL_INFO Primär- und Sekundärinformationen plus: Standardwert, Validierungstext, Validierungsregel

*lpszName*<br/>
Eine Zeichenfolge, die den Namen des gewünschten Felds enthält, für die Suche nach Namen. Sie können eine [CString](../../atl-mfc-shared/reference/cstringt-class.md)verwenden.

### <a name="remarks"></a>Bemerkungen

Eine Beschreibung der in *fieldinfo*zurückgegebenen Informationen finden Sie in der [CDaoFieldInfo-Struktur.](../../mfc/reference/cdaofieldinfo-structure.md) Diese Struktur enthält Member, die den beschreibenden Informationen unter *dwInfoOptions* oben entsprechen. Wenn Sie eine Informationsebene anfordern, erhalten Sie auch frühere Informationsebenen.

## <a name="cdaoquerydefgetname"></a><a name="getname"></a>CDaoQueryDef::GetName

Rufen Sie diese Memberfunktion auf, um den Namen der Abfrage abzurufen, die durch die querydef dargestellt wird.

```
CString GetName();
```

### <a name="return-value"></a>Rückgabewert

Der Name der Abfrage.

### <a name="remarks"></a>Bemerkungen

Querydef-Namen sind eindeutige benutzerdefinierte Namen. Weitere Informationen zu querydef-Namen finden Sie im Thema "Name-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaoquerydefgetodbctimeout"></a><a name="getodbctimeout"></a>CDaoQueryDef::GetODBCTimeout

Rufen Sie diese Memberfunktion auf, um das aktuelle Zeitlimit abzurufen, bevor eine Abfrage an eine ODBC-Datenquelle zeitüberschreitung ist.

```
short GetODBCTimeout();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Sekunden, nach denen ein Timeout bei einer Abfrage eintritt.

### <a name="remarks"></a>Bemerkungen

Informationen zu diesem Zeitlimit finden Sie im Thema "ODBCTimeout-Eigenschaft" in der DAO-Hilfe.

> [!TIP]
> Die bevorzugte Methode zum Arbeiten mit ODBC-Tabellen besteht darin, sie an einen Microsoft Jet (. MDB)-Datenbank. Weitere Informationen finden Sie im Thema "Zugriff auf externe Datenbanken mit DAO" in der DAO-Hilfe.

## <a name="cdaoquerydefgetparametercount"></a><a name="getparametercount"></a>CDaoQueryDef::GetParameterCount

Rufen Sie diese Memberfunktion auf, um die Anzahl der Parameter in der gespeicherten Abfrage abzurufen.

```
short GetParameterCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der in der Abfrage definierten Parameter.

### <a name="remarks"></a>Bemerkungen

`GetParameterCount`ist nützlich, um alle Parameter in der querydef zu durchlaufen. Verwenden Sie `GetParameterCount` zu diesem Zweck in Verbindung mit [GetParameterInfo](#getparameterinfo).

Weitere Informationen finden Sie in den Themen "Parameter object", "Parameters Collection" und "PARAMETERS Declaration (SQL)" in der DAO-Hilfe.

## <a name="cdaoquerydefgetparameterinfo"></a><a name="getparameterinfo"></a>CDaoQueryDef::GetParameterInfo

Rufen Sie diese Memberfunktion auf, um Informationen über einen in der querydef definierten Parameter abzurufen.

```cpp
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
Der nullbasierte Index des gewünschten Parameters in der Parameterauflistung der querydef für die Suche nach Index.

*paraminfo*<br/>
Ein Verweis auf ein [CDaoParameterInfo-Objekt,](../../mfc/reference/cdaoparameterinfo-structure.md) das die angeforderten Informationen zurückgibt.

*dwInfoOptionen*<br/>
Optionen, die angeben, welche Informationen über den abzurufenden Parameter abgerufen werden sollen. Die verfügbare Option wird hier zusammen mit dem, was die Funktion zurückgibt, aufgelistet:

- AFX_DAO_PRIMARY_INFO (Standard) Name, Typ

*lpszName*<br/>
Eine Zeichenfolge, die den Namen des gewünschten Parameters enthält, für die Suche nach Namen. Sie können eine [CString](../../atl-mfc-shared/reference/cstringt-class.md)verwenden.

### <a name="remarks"></a>Bemerkungen

Eine Beschreibung der in *paraminfo*zurückgegebenen Informationen finden Sie in der [CDaoParameterInfo-Struktur.](../../mfc/reference/cdaoparameterinfo-structure.md) Diese Struktur enthält Member, die den beschreibenden Informationen unter *dwInfoOptions* oben entsprechen.

Weitere Informationen finden Sie im Thema "PARAMETERS Declaration (SQL)" in der DAO-Hilfe.

## <a name="cdaoquerydefgetparamvalue"></a><a name="getparamvalue"></a>CDaoQueryDef::GetParamValue

Rufen Sie diese Memberfunktion auf, um den aktuellen Wert des angegebenen Parameters abzurufen, der in der Parameters-Auflistung der querydef gespeichert ist.

```
virtual COleVariant GetParamValue(LPCTSTR lpszName);
virtual COleVariant GetParamValue(int nIndex);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
Der Name des Parameters, dessen Wert Sie für die Suche nach Namen verwenden möchten.

*nIndex*<br/>
Der nullbasierte Index des Parameters in der Parameterauflistung der querydef für die Suche nach Index. Sie können diesen Wert mit Aufrufen von [GetParameterCount](#getparametercount) und [GetParameterInfo](#getparameterinfo)erhalten.

### <a name="return-value"></a>Rückgabewert

Ein Objekt der Klasse [COleVariant,](../../mfc/reference/colevariant-class.md) das den Wert des Parameters enthält.

### <a name="remarks"></a>Bemerkungen

Sie können auf den Parameter entweder über den Namen oder über seine Ordinalposition in der Auflistung zugreifen.

Weitere Informationen finden Sie im Thema "PARAMETERS Declaration (SQL)" in der DAO-Hilfe.

## <a name="cdaoquerydefgetrecordsaffected"></a><a name="getrecordsaffected"></a>CDaoQueryDef::GetRecordsAffected

Rufen Sie diese Memberfunktion auf, um zu bestimmen, wie viele Datensätze vom letzten Aufruf von [Execute](#execute)betroffen waren.

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der betroffenen Datensätze.

### <a name="remarks"></a>Bemerkungen

Die zurückgegebene Anzahl spiegelt keine Änderungen in verknüpften Tabellen wider, wenn kaskadierte Aktualisierungen oder Löschungen wirksam sind.

Weitere Informationen finden Sie im Thema "RecordsAffected Property" in der DAO-Hilfe.

## <a name="cdaoquerydefgetreturnsrecords"></a><a name="getreturnsrecords"></a>CDaoQueryDef::GetReturnsRecords

Rufen Sie diese Memberfunktion auf, um zu bestimmen, ob die querydef auf einer Abfrage basiert, die Datensätze zurückgibt.

```
BOOL GetReturnsRecords();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die querydef auf einer Abfrage basiert, die Datensätze zurückgibt; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird nur für SQL-Pass-Through-Abfragen verwendet. Weitere Informationen zu SQL-Abfragen finden Sie unter Die [Memberfunktion Ausführen.For](#execute) more information about SQL queries, see the Execute member function. Weitere Informationen zum Arbeiten mit SQL-Pass-Through-Abfragen finden Sie unter [SetReturnsRecords-Memberfunktion.](#setreturnsrecords)

Weitere Informationen finden Sie im Thema "ReturnsRecords-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaoquerydefgetsql"></a><a name="getsql"></a>CDaoQueryDef::GetSQL

Rufen Sie diese Memberfunktion auf, um die SQL-Anweisung abzurufen, die die Abfrage definiert, auf der die querydef basiert.

```
CString GetSQL();
```

### <a name="return-value"></a>Rückgabewert

Die SQL-Anweisung, die die Abfrage definiert, auf der die querydef basiert.

### <a name="remarks"></a>Bemerkungen

Sie werden dann wahrscheinlich die Zeichenfolge auf Schlüsselwörter, Tabellennamen usw. analysieren.

Weitere Informationen finden Sie in den Themen "SQL-Eigenschaft", "Vergleich von Microsoft Jet Database Engine SQL und ANSI SQL" und "Abfragen einer Datenbank mit SQL in Code" in der DAO-Hilfe.

## <a name="cdaoquerydefgettype"></a><a name="gettype"></a>CDaoQueryDef::GetType

Rufen Sie diese Memberfunktion auf, um den Abfragetyp der querydef zu bestimmen.

```
short GetType();
```

### <a name="return-value"></a>Rückgabewert

Der Typ der Abfrage, die von der querydef definiert wird. Werte finden Sie unter Hinweise.

### <a name="remarks"></a>Bemerkungen

Der Abfragetyp wird durch die Angabe in der SQL-Zeichenfolge von querydef festgelegt, wenn Sie die querydef erstellen oder die [SetSQL-Memberfunktion](#setsql) einer vorhandenen querydef aufrufen. Der von dieser Funktion zurückgegebene Abfragetyp kann einer der folgenden Werte sein:

- `dbQSelect`Auswählen

- `dbQAction`-Aktion

- `dbQCrosstab`Kreuztabelle

- `dbQDelete`Löschen

- `dbQUpdate` Update

- `dbQAppend`Anfügen

- `dbQMakeTable`Make-Table

- `dbQDDL`Datendefinition

- `dbQSQLPassThrough`Pass-Through

- `dbQSetOperation`Union

- `dbQSPTBulk`Wird `dbQSQLPassThrough` mit verwendet, um eine Abfrage anzugeben, die keine Datensätze zurückgibt.

> [!NOTE]
> Um eine SQL-Pass-Through-Abfrage zu `dbSQLPassThrough` erstellen, legen Sie die Konstante nicht fest. Dies wird automatisch vom Microsoft Jet-Datenbankmodul festgelegt, wenn Sie ein querydef-Objekt erstellen und die Verbindungszeichenfolge festlegen.

Informationen zu SQL-Zeichenfolgen finden Sie unter [GetSQL](#getsql). Informationen zu Abfragetypen finden Sie unter [Ausführen](#execute)von .

## <a name="cdaoquerydefisopen"></a><a name="isopen"></a>CDaoQueryDef::IsOpen

Rufen Sie diese Memberfunktion `CDaoQueryDef` auf, um zu bestimmen, ob das Objekt derzeit geöffnet ist.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert `CDaoQueryDef` ungleich Null, wenn das Objekt derzeit geöffnet ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Eine querydef muss sich in einem offenen Zustand befinden, bevor Sie sie verwenden, um [Execute](#execute) aufzurufen oder ein [CDaoRecordset-Objekt](../../mfc/reference/cdaorecordset-class.md) zu erstellen. Um eine querydef in einen offenen Statusaufruf zu setzen, entweder [Create](#create) (für eine neue querydef) oder [Open](#open) (für eine vorhandene querydef).

## <a name="cdaoquerydefm_pdatabase"></a><a name="m_pdatabase"></a>CDaoQueryDef::m_pDatabase

Enthält einen Zeiger auf das [CDaoDatabase-Objekt,](../../mfc/reference/cdaodatabase-class.md) das dem querydef-Objekt zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diesen Zeiger, wenn Sie direkt auf die Datenbank zugreifen müssen, z. B. um Zeiger auf andere Querydef- oder Recordset-Objekte in den Sammlungen der Datenbank zu erhalten.

## <a name="cdaoquerydefm_pdaoquerydef"></a><a name="m_pdaoquerydef"></a>CDaoQueryDef::m_pDAOQueryDef

Enthält einen Zeiger auf die OLE-Schnittstelle für das zugrunde liegende DAO-Querydef-Objekt.

### <a name="remarks"></a>Bemerkungen

Dieser Zeiger wird für vollständigkeit und Konsistenz mit den anderen Klassen bereitgestellt. Da MFC DAO querydefs jedoch ziemlich vollständig kapselt, ist es unwahrscheinlich, dass Sie sie benötigen. Wenn Sie es verwenden, tun Sie dies vorsichtig – insbesondere ändern Sie den Wert des Zeigers nicht, es sei denn, Sie wissen, was Sie tun.

## <a name="cdaoquerydefopen"></a><a name="open"></a>CDaoQueryDef::Öffnen

Rufen Sie diese Memberfunktion auf, um eine Querydef zu öffnen, die zuvor in der QueryDefs-Auflistung der Datenbank gespeichert war.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
Eine Zeichenfolge, die den Namen der gespeicherten querydef enthält, die geöffnet werden soll. Sie können eine [CString](../../atl-mfc-shared/reference/cstringt-class.md)verwenden.

### <a name="remarks"></a>Bemerkungen

Sobald die querydef geöffnet ist, können Sie die [Memberfunktion Execute](#execute) aufrufen oder die querydef verwenden, um ein [CDaoRecordset-Objekt](../../mfc/reference/cdaorecordset-class.md) zu erstellen.

## <a name="cdaoquerydefsetconnect"></a><a name="setconnect"></a>CDaoQueryDef::SetConnect

Rufen Sie diese Memberfunktion auf, um die Verbindungszeichenfolge des querydef-Objekts festzulegen.

```cpp
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Parameter

*lpszConnect*<br/>
Eine Zeichenfolge, die eine Verbindungszeichenfolge für das zugeordnete [CDaoDatabase-Objekt](../../mfc/reference/cdaodatabase-class.md) enthält.

### <a name="remarks"></a>Bemerkungen

Die Verbindungszeichenfolge wird verwendet, um bei Bedarf zusätzliche Informationen an ODBC und bestimmte ISAM-Treiber zu übergeben. Es wird nicht für Microsoft Jet (. MDB)-Datenbanken.

> [!TIP]
> Die bevorzugte Methode zum Arbeiten mit ODBC-Tabellen besteht darin, sie an eine anzuhängen. MDB-Datenbank.

Bevor Sie eine querydef ausführen, die eine SQL-Pass-Through-Abfrage für `SetConnect` eine ODBC-Datenquelle darstellt, legen Sie die Verbindungszeichenfolge mit fest, und rufen Sie [SetReturnsRecords](#setreturnsrecords) auf, um anzugeben, ob die Abfrage Datensätze zurückgibt.

Weitere Informationen zur Struktur der Verbindungszeichenfolge und Beispiele für Verbindungszeichenfolgenkomponenten finden Sie im Thema "Connect Property" in der DAO-Hilfe.

## <a name="cdaoquerydefsetname"></a><a name="setname"></a>CDaoQueryDef::SetName

Rufen Sie diese Memberfunktion auf, wenn Sie den Namen einer querydef ändern möchten, die nicht temporär ist.

```cpp
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
Eine Zeichenfolge, die den neuen Namen für eine nicht temporäre Abfrage im zugeordneten [CDaoDatabase-Objekt](../../mfc/reference/cdaodatabase-class.md) enthält.

### <a name="remarks"></a>Bemerkungen

Querydef-Namen sind eindeutige, benutzerdefinierte Namen. Sie können `SetName` aufrufen, bevor das querydef-Objekt an die QueryDefs-Auflistung angehängt wird.

## <a name="cdaoquerydefsetodbctimeout"></a><a name="setodbctimeout"></a>CDaoQueryDef::SetODBCTimeout

Rufen Sie diese Memberfunktion auf, um das Zeitlimit festzulegen, bevor eine Abfrage auf eine ODBC-Datenquelle zeitüberschreitung erfolgt.

```cpp
void SetODBCTimeout(short nODBCTimeout);
```

### <a name="parameters"></a>Parameter

*nODBCTimeout*<br/>
Die Anzahl von Sekunden, nach denen ein Timeout bei einer Abfrage eintritt.

### <a name="remarks"></a>Bemerkungen

Mit dieser Memberfunktion können Sie die Standardanzahl von Sekunden vor nachfolgenden Vorgängen in der verbundenen Datenquelle "Timeout" überschreiben. Bei einem Vorgang kann aufgrund von Netzwerkzugriffsproblemen, übermäßiger Abfrageverarbeitungszeit usw. ein Zeitproblem auftreten. Rufen `SetODBCTimeout` Sie vor dem Ausführen einer Abfrage mit dieser querydef auf, wenn Sie den Abfragetimeoutwert ändern möchten. (Da ODBC Verbindungen wiederverwendet, ist der Timeoutwert für alle Clients derselben Verbindung gleich.)

Der Standardwert für Abfragetimeouts beträgt 60 Sekunden.

## <a name="cdaoquerydefsetparamvalue"></a><a name="setparamvalue"></a>CDaoQueryDef::SetParamValue

Rufen Sie diese Memberfunktion auf, um den Wert eines Parameters in der querydef zur Laufzeit festzulegen.

```
virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);

virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
Der Name des Parameters, dessen Wert Sie festlegen möchten.

*varValue*<br/>
Der festzulegende Wert; siehe Anmerkungen.

*nIndex*<br/>
Die Ordinalposition des Parameters in der Parameters-Auflistung der querydef. Sie können diesen Wert mit Aufrufen von [GetParameterCount](#getparametercount) und [GetParameterInfo](#getparameterinfo)erhalten.

### <a name="remarks"></a>Bemerkungen

Der Parameter muss bereits als Teil der SQL-Zeichenfolge der querydef eingerichtet worden sein. Sie können auf den Parameter entweder über den Namen oder über seine Ordinalposition in der Auflistung zugreifen.

Geben Sie den Wert `COleVariant` an, der als Objekt festgelegt werden soll. Informationen zum Festlegen des gewünschten Werts und der Eingabe in Ihrem `COleVariant` Objekt finden Sie unter Klasse [COleVariant](../../mfc/reference/colevariant-class.md).

## <a name="cdaoquerydefsetreturnsrecords"></a><a name="setreturnsrecords"></a>CDaoQueryDef::SetReturnsRecords

Rufen Sie diese Memberfunktion als Teil des Einrichtens einer SQL-Pass-Through-Abfrage für eine externe Datenbank auf.

```cpp
void SetReturnsRecords(BOOL bReturnsRecords);
```

### <a name="parameters"></a>Parameter

*bReturnsRecords*<br/>
True übergeben, wenn die Abfrage für eine externe Datenbank Datensätze zurückgibt. andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

In einem solchen Fall müssen Sie die querydef `CDaoQueryDef` erstellen und ihre Eigenschaften mithilfe anderer Memberfunktionen festlegen. Eine Beschreibung externer Datenbanken finden Sie unter [SetConnect](#setconnect).

## <a name="cdaoquerydefsetsql"></a><a name="setsql"></a>CDaoQueryDef::SetSQL

Rufen Sie diese Memberfunktion auf, um die SQL-Anweisung festzulegen, die von der querydef ausgeführt wird.

```cpp
void SetSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Parameter

*Lpszsql*<br/>
Eine Zeichenfolge, die eine vollständige SQL-Anweisung enthält, die für die Ausführung geeignet ist. Die Syntax dieser Zeichenfolge hängt von dem DBMS ab, auf das Ihre Abfrage abzielt. Eine Erläuterung der Syntax, die im Microsoft Jet-Datenbankmodul verwendet wird, finden Sie im Thema "Erstellen von SQL-Anweisungen im Code" in der DAO-Hilfe.

### <a name="remarks"></a>Bemerkungen

Eine typische `SetSQL` Verwendung von ist das Einrichten eines querydef-Objekts für die Verwendung in einer SQL-Pass-Through-Abfrage. (Die Syntax von SQL-Pass-Through-Abfragen auf Ihrem Ziel-DBMS finden Sie in der Dokumentation zu Ihrem DBMS.)

## <a name="see-also"></a>Weitere Informationen

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset-Klasse](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoDatabase-Klasse](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoTableDef-Klasse](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoException-Klasse](../../mfc/reference/cdaoexception-class.md)
