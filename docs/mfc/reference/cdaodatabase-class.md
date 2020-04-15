---
title: CDaoDatabase-Klasse
ms.date: 09/17/2019
f1_keywords:
- CDaoDatabase
- AFXDAO/CDaoDatabase
- AFXDAO/CDaoDatabase::CDaoDatabase
- AFXDAO/CDaoDatabase::CanTransact
- AFXDAO/CDaoDatabase::CanUpdate
- AFXDAO/CDaoDatabase::Close
- AFXDAO/CDaoDatabase::Create
- AFXDAO/CDaoDatabase::CreateRelation
- AFXDAO/CDaoDatabase::DeleteQueryDef
- AFXDAO/CDaoDatabase::DeleteRelation
- AFXDAO/CDaoDatabase::DeleteTableDef
- AFXDAO/CDaoDatabase::Execute
- AFXDAO/CDaoDatabase::GetConnect
- AFXDAO/CDaoDatabase::GetName
- AFXDAO/CDaoDatabase::GetQueryDefCount
- AFXDAO/CDaoDatabase::GetQueryDefInfo
- AFXDAO/CDaoDatabase::GetQueryTimeout
- AFXDAO/CDaoDatabase::GetRecordsAffected
- AFXDAO/CDaoDatabase::GetRelationCount
- AFXDAO/CDaoDatabase::GetRelationInfo
- AFXDAO/CDaoDatabase::GetTableDefCount
- AFXDAO/CDaoDatabase::GetTableDefInfo
- AFXDAO/CDaoDatabase::GetVersion
- AFXDAO/CDaoDatabase::IsOpen
- AFXDAO/CDaoDatabase::Open
- AFXDAO/CDaoDatabase::SetQueryTimeout
- AFXDAO/CDaoDatabase::m_pDAODatabase
- AFXDAO/CDaoDatabase::m_pWorkspace
helpviewer_keywords:
- CDaoDatabase [MFC], CDaoDatabase
- CDaoDatabase [MFC], CanTransact
- CDaoDatabase [MFC], CanUpdate
- CDaoDatabase [MFC], Close
- CDaoDatabase [MFC], Create
- CDaoDatabase [MFC], CreateRelation
- CDaoDatabase [MFC], DeleteQueryDef
- CDaoDatabase [MFC], DeleteRelation
- CDaoDatabase [MFC], DeleteTableDef
- CDaoDatabase [MFC], Execute
- CDaoDatabase [MFC], GetConnect
- CDaoDatabase [MFC], GetName
- CDaoDatabase [MFC], GetQueryDefCount
- CDaoDatabase [MFC], GetQueryDefInfo
- CDaoDatabase [MFC], GetQueryTimeout
- CDaoDatabase [MFC], GetRecordsAffected
- CDaoDatabase [MFC], GetRelationCount
- CDaoDatabase [MFC], GetRelationInfo
- CDaoDatabase [MFC], GetTableDefCount
- CDaoDatabase [MFC], GetTableDefInfo
- CDaoDatabase [MFC], GetVersion
- CDaoDatabase [MFC], IsOpen
- CDaoDatabase [MFC], Open
- CDaoDatabase [MFC], SetQueryTimeout
- CDaoDatabase [MFC], m_pDAODatabase
- CDaoDatabase [MFC], m_pWorkspace
ms.assetid: 8ff5b342-964d-449d-bef1-d0ff56aadf6d
ms.openlocfilehash: debba137878da49921df83da7630003a7d62db2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369015"
---
# <a name="cdaodatabase-class"></a>CDaoDatabase-Klasse

Stellt eine Verbindung zu einer Access-Datenbank mithilfe von Datenzugriffsobjekten (Data Access Objects, DAO) dar. DAO wird über Office 2013 unterstützt. DAO 3.6 ist die endgültige Version und gilt als veraltet.

## <a name="syntax"></a>Syntax

```
class CDaoDatabase : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoDatabase::CDaoDatabase](#cdaodatabase)|Erstellt ein `CDaoDatabase`-Objekt. Rufen `Open` Sie auf, um das Objekt mit einer Datenbank zu verbinden.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoDatabase::CanTransact](#cantransact)|Gibt einen Wert ungleich Null zurück, wenn die Datenbank Transaktionen unterstützt.|
|[CDaoDatabase::CanUpdate](#canupdate)|Gibt einen Wert `CDaoDatabase` ungleich Null zurück, wenn das Objekt aufrüstbar (nicht schreibgeschützt) ist.|
|[CDaoDatabase::Schließen](#close)|Schließt die Datenbankverbindung.|
|[CDaoDatabase::Erstellen](#create)|Erstellt das zugrunde liegende DAO-Datenbankobjekt und initialisiert das `CDaoDatabase` Objekt.|
|[CDaoDatabase::CreateRelation](#createrelation)|Definiert eine neue Beziehung zwischen den Tabellen in der Datenbank.|
|[CDaoDatabase::DeleteQueryDef](#deletequerydef)|Löscht ein querydef-Objekt, das in der QueryDefs-Auflistung der Datenbank gespeichert ist.|
|[CDaoDatabase::DeleteRelation](#deleterelation)|Löscht eine vorhandene Beziehung zwischen Tabellen in der Datenbank.|
|[CDaoDatabase::DeleteTableDef](#deletetabledef)|Löscht die Definition einer Tabelle in der Datenbank. Dadurch werden die tatsächliche Tabelle und alle zugehörigen Daten gelöscht.|
|[CDaoDatabase::Ausführen](#execute)|Führt eine Aktionsabfrage aus. Wenn `Execute` Sie eine Abfrage aufrufen, die Ergebnisse zurückgibt, wird eine Ausnahme ausgelöst.|
|[CDaoDatabase::GetConnect](#getconnect)|Gibt die Verbindungszeichenfolge zurück, die zum Verbinden des `CDaoDatabase` Objekts mit einer Datenbank verwendet wird. Wird für ODBC verwendet.|
|[CDaoDatabase::GetName](#getname)|Gibt den Namen der aktuell verwendeten Datenbank zurück.|
|[CDaoDatabase::GetQueryDefCount](#getquerydefcount)|Gibt die Anzahl der für die Datenbank definierten Abfragen zurück.|
|[CDaoDatabase::GetQueryDefInfo](#getquerydefinfo)|Gibt Informationen zu einer angegebenen Abfrage zurück, die in der Datenbank definiert ist.|
|[CDaoDatabase::GetQueryTimeout](#getquerytimeout)|Gibt die Anzahl der Sekunden zurück, nach denen Datenbankabfragevorgänge ein Timeout aufweisen. Wirkt sich auf alle nachfolgenden Öffnens, Neuen, Aktualisierungs- und Bearbeitungsvorgänge `Execute` und andere Vorgänge in ODBC-Datenquellen (nur) aus, z. B. Aufrufe.|
|[CDaoDatabase::GetRecordsAffected](#getrecordsaffected)|Gibt die Anzahl der Datensätze zurück, die von der letzten `Execute`Aktualisierung, Bearbeitung oder dem Hinzufügen von Vorgang oder einem Aufruf von betroffen sind.|
|[CDaoDatabase::GetRelationCount](#getrelationcount)|Gibt die Anzahl der Beziehungen zurück, die zwischen Tabellen in der Datenbank definiert sind.|
|[CDaoDatabase::GetRelationInfo](#getrelationinfo)|Gibt Informationen zu einer angegebenen Beziehung zurück, die zwischen Tabellen in der Datenbank definiert ist.|
|[CDaoDatabase::GetTableDefCount](#gettabledefcount)|Gibt die Anzahl der in der Datenbank definierten Tabellen zurück.|
|[CDaoDatabase::GetTableDefInfo](#gettabledefinfo)|Gibt Informationen zu einer angegebenen Tabelle in der Datenbank zurück.|
|[CDaoDatabase::GetVersion](#getversion)|Gibt die Version des Datenbankmoduls zurück, das der Datenbank zugeordnet ist.|
|[CDaoDatabase::IsOpen](#isopen)|Gibt einen Wert `CDaoDatabase` ungleich Null zurück, wenn das Objekt derzeit mit einer Datenbank verbunden ist.|
|[CDaoDatabase::Öffnen](#open)|Stellt eine Verbindung zu einer Datenbank her.|
|[CDaoDatabase::SetQueryTimeout](#setquerytimeout)|Legt die Anzahl der Sekunden fest, nach denen Datenbankabfragevorgänge (nur für ODBC-Datenquellen) ein Timeout ausgeführt werden. Wirkt sich auf alle nachfolgenden Öffnungs-, Neu-, Aktualisierungs- und Löschvorgänge aus.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoDatabase::m_pDAODatabase](#m_pdaodatabase)|Ein Zeiger auf das zugrunde liegende DAO-Datenbankobjekt.|
|[CDaoDatabase::m_pWorkspace](#m_pworkspace)|Ein Zeiger auf das [CDaoWorkspace-Objekt,](../../mfc/reference/cdaoworkspace-class.md) das die Datenbank enthält und deren Transaktionsbereich definiert.|

## <a name="remarks"></a>Bemerkungen

Informationen zu den unterstützten Datenbankformaten finden Sie in der [GetName-Memberfunktion.](../../mfc/reference/cdaoworkspace-class.md#getname) Sie können ein `CDaoDatabase` oder mehrere Objekte gleichzeitig in einem bestimmten "Arbeitsbereich" aktiv haben, der durch ein [CDaoWorkspace-Objekt](../../mfc/reference/cdaoworkspace-class.md) dargestellt wird. Der Arbeitsbereich verwaltet eine Auflistung offener Datenbankobjekte, die als Databases-Auflistung bezeichnet wird.

## <a name="usage"></a>Verwendung

Sie können Datenbankobjekte implizit erstellen, wenn Sie Recordset-Objekte erstellen. Sie können aber auch Datenbankobjekte explizit erstellen. Um eine vorhandene Datenbank `CDaoDatabase`explizit mit zu verwenden, gehen Sie wie folgt vor:

- Erstellen `CDaoDatabase` Sie ein Objekt, indem Sie einen Zeiger an ein geöffnetes [CDaoWorkspace-Objekt](../../mfc/reference/cdaoworkspace-class.md) übergeben.

- Oder erstellen `CDaoDatabase` Sie ein Objekt, ohne den Arbeitsbereich anzugeben (MFC erstellt ein temporäres Arbeitsbereichsobjekt).

So erstellen Sie einen neuen Microsoft Jet (. MDB) Datenbank, `CDaoDatabase` erstellen Sie ein Objekt und rufen Sie die [Create](#create) Member-Funktion auf. Rufen *not* `Open` Sie `Create`nicht nach an.

Um eine vorhandene Datenbank `CDaoDatabase` zu öffnen, erstellen Sie ein Objekt und rufen sie die [Open-Memberfunktion](#open) auf.

Jede dieser Techniken fügt das DAO-Datenbankobjekt an die Datenbanksammlung des Arbeitsbereichs an und öffnet eine Verbindung zu den Daten. Wenn Sie dann [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)-, [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)- oder [CDaoQueryDef-Objekte](../../mfc/reference/cdaoquerydef-class.md) für die Bedienung in der `CDaoDatabase` verbundenen Datenbank erstellen, übergeben Sie die Konstruktoren für diese Objekte einen Zeiger auf Ihr Objekt. Wenn Sie die Verbindung verwenden, rufen Sie `CDaoDatabase` die Memberfunktion [Schließen](#close) auf, und zerstören Sie das Objekt. `Close`schließt alle Recordsets, die Sie zuvor noch nicht geschlossen haben.

## <a name="transactions"></a>Transaktionen

Die Datenbanktransaktionsverarbeitung wird auf Arbeitsbereichsebene bereitgestellt – siehe [BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans), `CDaoWorkspace` [CommitTrans](../../mfc/reference/cdaoworkspace-class.md#committrans)und [Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback) Memberfunktionen der Klasse .

## <a name="odbc-connections"></a>ODBC-Verbindungen

Die empfohlene Methode zum Arbeiten mit ODBC-Datenquellen besteht darin, externe Tabellen an einen Microsoft Jet (. MDB)-Datenbank.

## <a name="collections"></a>Auflistungen

Jede Datenbank verwaltet ihre eigenen Auflistungen von tabledef-, querydef-, recordset- und relation-Objekten. Die `CDaoDatabase` Klasse stellt Memberfunktionen zum Bearbeiten dieser Objekte bereit.

> [!NOTE]
> Die Objekte werden in DAO und nicht im MFC-Datenbankobjekt gespeichert. MFC stellt Klassen für tabledef-, querydef- und recordset-Objekte, jedoch nicht für Beziehungsobjekte zur Verfügung.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CDaoDatabase`

## <a name="requirements"></a>Anforderungen

**Header:** afxdao.h

## <a name="cdaodatabasecantransact"></a><a name="cantransact"></a>CDaoDatabase::CanTransact

Rufen Sie diese Memberfunktion auf, um zu bestimmen, ob die Datenbank Transaktionen zulässt.

```
BOOL CanTransact();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Datenbank Transaktionen unterstützt; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Transaktionen werden im Arbeitsbereich der Datenbank verwaltet.

## <a name="cdaodatabasecanupdate"></a><a name="canupdate"></a>CDaoDatabase::CanUpdate

Rufen Sie diese Memberfunktion `CDaoDatabase` auf, um zu bestimmen, ob das Objekt Aktualisierungen zulässt.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert `CDaoDatabase` ungleich Null, wenn das Objekt Aktualisierungen zulässt; Andernfalls 0, was entweder angibt, dass Sie TRUE `CDaoDatabase` in *bReadOnly* übergeben haben, wenn Sie das Objekt geöffnet haben, oder dass die Datenbank selbst schreibgeschützt ist. Siehe [open](#open) member function.

### <a name="remarks"></a>Bemerkungen

Informationen zur Aktuierbarkeit der Datenbank finden Sie im Thema "Updatable-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaodatabasecdaodatabase"></a><a name="cdaodatabase"></a>CDaoDatabase::CDaoDatabase

Erstellt ein `CDaoDatabase`-Objekt.

```
CDaoDatabase(CDaoWorkspace* pWorkspace = NULL);
```

### <a name="parameters"></a>Parameter

*pWorkspace*<br/>
Ein Zeiger auf `CDaoWorkspace` das Objekt, das das neue Datenbankobjekt enthält. Wenn Sie den Standardwert NULL akzeptieren, erstellt `CDaoWorkspace` der Konstruktor ein temporäres Objekt, das den Standard-DAO-Arbeitsbereich verwendet. Sie können über das [m_pWorkspace](#m_pworkspace) Datenmember einen Zeiger auf das Workspace-Objekt abrufen.

### <a name="remarks"></a>Bemerkungen

Wenn Sie nach dem Erstellen des Objekts einen neuen Microsoft Jet (. MDB) Datenbank, rufen Sie die [Memberfunktion Create](#create) des Objekts auf. Wenn Sie stattdessen eine vorhandene Datenbank öffnen, rufen [Open](#open) Sie die Open-Memberfunktion des Objekts auf.

Wenn Sie mit dem Objekt fertig sind, sollten Sie `CDaoDatabase` seine [Memberfunktion Schließen](#close) aufrufen und dann das Objekt zerstören.

Möglicherweise ist es sinnvoll, `CDaoDatabase` das Objekt in Ihre Dokumentklasse einzubetten.

> [!NOTE]
> Ein `CDaoDatabase` Objekt wird auch implizit erstellt, wenn Sie ein [CDaoRecordset-Objekt](../../mfc/reference/cdaorecordset-class.md) öffnen, ohne einen Zeiger an ein vorhandenes `CDaoDatabase` Objekt zu übergeben. Dieses Datenbankobjekt wird geschlossen, wenn Sie das Recordset-Objekt schließen.

## <a name="cdaodatabaseclose"></a><a name="close"></a>CDaoDatabase::Schließen

Rufen Sie diese Memberfunktion auf, um die Verbindung zu einer Datenbank zu trennen und alle geöffneten Recordsets, Tabledefs und Querydefs zu schließen, die der Datenbank zugeordnet sind.

```
virtual void Close();
```

### <a name="remarks"></a>Bemerkungen

Es ist sinnvoll, diese Objekte selbst zu schließen, bevor Sie diese Memberfunktion aufrufen. Beim `CDaoDatabase` Schließen eines Objekts wird es aus der Databases-Auflistung im zugeordneten [Arbeitsbereich entfernt.](../../mfc/reference/cdaoworkspace-class.md) Da `Close` das `CDaoDatabase` Objekt nicht zerstört wird, können Sie das Objekt wiederverwenden, indem Sie dieselbe Datenbank oder eine andere Datenbank öffnen.

> [!CAUTION]
> Rufen Sie die [Funktion "Member aktualisieren"](../../mfc/reference/cdaorecordset-class.md#update) (falls ausstehende Bearbeitungen vorhanden sind) und die `Close` Memberfunktion für alle geöffneten Recordset-Objekte auf, bevor Sie eine Datenbank schließen. Wenn Sie eine Funktion beenden, die `CDaoDatabase` [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) oder Objekte auf dem Stapel deklariert, wird die Datenbank geschlossen, alle nicht gespeicherten Änderungen gehen verloren, alle ausstehenden Transaktionen werden zurückgesetzt, und alle ausstehenden Änderungen an Ihren Daten gehen verloren.

> [!CAUTION]
> Wenn Sie versuchen, ein Datenbankobjekt zu schließen, während Recordset-Objekte geöffnet sind, oder wenn Sie versuchen, ein Arbeitsbereichsobjekt zu schließen, während alle Datenbankobjekte, die zu diesem bestimmten Arbeitsbereich gehören, geöffnet sind, werden diese Recordset-Objekte geschlossen, und alle ausstehenden Aktualisierungen oder Bearbeitungen werden zurückgesetzt. Wenn Sie versuchen, ein Arbeitsbereichsobjekt zu schließen, während alle datenbanken Objekte, die zu diesem Objekt gehören, geöffnet sind, schließt der Vorgang alle Datenbankobjekte, die zu diesem bestimmten Arbeitsbereichsobjekt gehören, was dazu führen kann, dass nicht geschlossene Recordset-Objekte geschlossen werden. Wenn Sie das Datenbankobjekt nicht schließen, meldet MFC einen Assertionsfehler in Debugbuilds.

Wenn das Datenbankobjekt außerhalb des Bereichs einer Funktion definiert ist und Sie die Funktion beenden, ohne sie zu schließen, bleibt das Datenbankobjekt geöffnet, bis es explizit geschlossen ist oder das Modul, in dem es definiert ist, außerhalb des Gültigkeitsbereichs liegt.

## <a name="cdaodatabasecreate"></a><a name="create"></a>CDaoDatabase::Erstellen

So erstellen Sie einen neuen Microsoft Jet (. MDB)-Datenbank, rufen Sie diese `CDaoDatabase` Memberfunktion auf, nachdem Sie ein Objekt erstellt haben.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int dwOptions = 0);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
Ein Zeichenfolgenausdruck, der der Name der Datenbankdatei ist, die Sie erstellen. Dabei kann es sich um den vollständigen Pfad\\und Dateinamen handelt, z. B. "C: MDB". Sie müssen einen Namen angeben. Wenn Sie keine Dateinamenerweiterung angeben, . MDB wird angehängt. Wenn Ihr Netzwerk die einheitliche Benennungskonvention (UNC) unterstützt, können\\\\\\Sie\\auch einen\\Netzwerkpfad angeben, z. B. " "MYSERVER "MYSHARE " MYDIR ,MYDIR\\'MYDB'". Nur Microsoft Jet (. MDB) Datenbankdateien können mit dieser Memberfunktion erstellt werden. (Doppelte umgekehrte Schrägstriche sind in\\Zeichenfolgenliteralen erforderlich, da " " das C++-Escapezeichen ist.)

*lpszLocale*<br/>
Ein Zeichenfolgenausdruck, der verwendet wird, um die Sortierreihenfolge zum Erstellen der Datenbank anzugeben. Der Standardwert ist `dbLangGeneral`. Mögliche Werte:

- `dbLangGeneral`Englisch, Deutsch, Französisch, Portugiesisch, Italienisch und Modernes Spanisch

- `dbLangArabic`Arabisch

- `dbLangCyrillic`Russisch

- `dbLangCzech`Tschechisch

- `dbLangDutch`Holländisch

- `dbLangGreek`Griechisch

- `dbLangHebrew`Hebräisch

- `dbLangHungarian`Ungarisch

- `dbLangIcelandic`Isländisch

- `dbLangNordic`Nordische Sprachen (nur Microsoft Jet-Datenbankmodul Version 1.0)

- `dbLangNorwdan`Norwegisch und Dänisch

- `dbLangPolish`Polnisch

- `dbLangSpanish`Traditionelles Spanisch

- `dbLangSwedfin`Schwedisch und Finnisch

- `dbLangTurkish`Türkisch

*Dwoptions*<br/>
Eine ganze Zahl, die eine oder mehrere Optionen angibt. Mögliche Werte:

- `dbEncrypt`Erstellen Sie eine verschlüsselte Datenbank.

- `dbVersion10`Erstellen Sie eine Datenbank mit Microsoft Jet-Datenbankversion 1.0.

- `dbVersion11`Erstellen Sie eine Datenbank mit Microsoft Jet-Datenbankversion 1.1.

- `dbVersion20`Erstellen Sie eine Datenbank mit Microsoft Jet-Datenbankversion 2.0.

- `dbVersion30`Erstellen Sie eine Datenbank mit Microsoft Jet-Datenbankversion 3.0.

Wenn Sie die Verschlüsselungskonstante weglassen, wird eine unverschlüsselte Datenbank erstellt. Sie können nur eine Versionskonstante angeben. Wenn Sie eine Versionskonstante weglassen, wird eine Datenbank erstellt, die die Microsoft Jet-Datenbankversion 3.0 verwendet.

> [!CAUTION]
> Wenn eine Datenbank nicht verschlüsselt ist, ist es möglich, auch wenn Sie Benutzer-/Kennwortsicherheit implementieren, die Binärdatenträgerdatei, aus der die Datenbank besteht, direkt zu lesen.

### <a name="remarks"></a>Bemerkungen

`Create`erstellt die Datenbankdatei und das zugrunde liegende DAO-Datenbankobjekt und initialisiert das C++-Objekt. Das Objekt wird an die Databases-Auflistung des zugeordneten Arbeitsbereichs angehängt. Das Datenbankobjekt befindet sich in einem offenen Zustand. nicht nach `Open*` `Create`anrufen.

> [!NOTE]
> Mit `Create`können Sie nur Microsoft Jet (. MDB)-Datenbanken. Sie können keine ISAM-Datenbanken oder ODBC-Datenbanken erstellen.

## <a name="cdaodatabasecreaterelation"></a><a name="createrelation"></a>CDaoDatabase::CreateRelation

Rufen Sie diese Memberfunktion auf, um eine Beziehung zwischen einem oder mehreren Feldern in einer Primärtabelle in der Datenbank und einem oder mehreren Feldern in einer fremden Tabelle (einer anderen Tabelle in der Datenbank) herzustellen.

```
void CreateRelation(
    LPCTSTR lpszName,
    LPCTSTR lpszTable,
    LPCTSTR lpszForeignTable,
    long lAttributes,
    LPCTSTR lpszField,
    LPCTSTR lpszForeignField);

void CreateRelation(CDaoRelationInfo& relinfo);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
Der eindeutige Name des Beziehungsobjekts. Der Name muss mit einem Buchstaben beginnen und darf maximal 40 Zeichen enthalten. Sie kann Zahlen und Unterstrichzeichen enthalten, aber keine Interpunktion oder Leerzeichen.

*lpszTable*<br/>
Der Name der Primärtabelle in der Beziehung. Wenn die Tabelle nicht vorhanden ist, löst MFC eine Ausnahme vom Typ [CDaoException](../../mfc/reference/cdaoexception-class.md)aus.

*lpszForeignTable*<br/>
Der Name der Fremdtabelle in der Beziehung. Wenn die Tabelle nicht vorhanden ist, löst `CDaoException`MFC eine Ausnahme vom Typ aus.

*lAttributes*<br/>
Ein langer Wert, der Informationen über den Beziehungstyp enthält. Sie können diesen Wert unter anderem verwenden, um die referenzielle Integrität zu erzwingen. Sie können den bitwise-OR-Operator ( **&#124;**) verwenden, um einen der folgenden Werte zu kombinieren (solange die Kombination sinnvoll ist):

- `dbRelationUnique`Die Beziehung ist eins zu eins.

- `dbRelationDontEnforce`Die Beziehung wird nicht erzwungen (keine referenzielle Integrität).

- `dbRelationInherited`Die Beziehung ist in einer nicht aktuellen Datenbank vorhanden, die die beiden angefügten Tabellen enthält.

- `dbRelationUpdateCascade`Aktualisierungen werden kaskadiert (weitere Informationen zu Kaskaden finden Sie unter Hinweise).

- `dbRelationDeleteCascade`Löschungen werden kaskadiert.

*lpszField*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge, die den Namen eines Felds in der primären Tabelle enthält (benannt nach *lpszTable*).

*lpszForeignField*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge, die den Namen eines Felds in der Fremdtabelle enthält (benannt nach *lpszForeignTable*).

*relinfo*<br/>
Ein Verweis auf ein [CDaoRelationInfo-Objekt,](../../mfc/reference/cdaorelationinfo-structure.md) das Informationen über die Beziehung enthält, die Sie erstellen möchten.

### <a name="remarks"></a>Bemerkungen

Die Beziehung kann keine Abfrage oder eine angefügte Tabelle aus einer externen Datenbank umfassen.

Verwenden Sie die erste Version der Funktion, wenn die Beziehung ein Feld in jeder der beiden Tabellen umfasst. Verwenden Sie die zweite Version, wenn die Beziehung mehrere Felder umfasst. Die maximale Anzahl von Feldern in einer Beziehung beträgt 14.

Diese Aktion erstellt ein zugrunde liegendes DAO-Beziehungsobjekt, ist jedoch ein MFC-Implementierungsdetail, da die Kapselung von Beziehungsobjekten von MFC in der Klasse `CDaoDatabase`enthalten ist. MFC stellt keine Klasse für Beziehungen zur Verfügung.

Wenn Sie die Attribute des Beziehungsobjekts so festlegen, dass Kaskadenvorgänge aktiviert werden, aktualisiert oder löscht das Datenbankmodul automatisch Datensätze in einer oder mehreren anderen Tabellen, wenn Änderungen an verknüpften Primärschlüsseltabellen vorgenommen werden.

Angenommen, Sie richten eine kaskadierte Löschbeziehung zwischen einer Customers-Tabelle und einer Tabelle "Bestellungen" ein. Wenn Sie Datensätze aus der Tabelle Customers löschen, werden auch Datensätze in der Tabelle Bestellungen gelöscht, die sich auf diesen Debitor beziehen. Wenn Sie kaskadierte Löschbeziehungen zwischen der Tabelle Orders und anderen Tabellen einrichten, werden Datensätze aus diesen Tabellen automatisch gelöscht, wenn Sie Datensätze aus der Tabelle Customers löschen.

Weitere Informationen finden Sie im Thema "CreateRelation-Methode" in der DAO-Hilfe.

## <a name="cdaodatabasedeletequerydef"></a><a name="deletequerydef"></a>CDaoDatabase::DeleteQueryDef

Rufen Sie diese Memberfunktion auf, um die `CDaoDatabase` angegebene querydef – gespeicherte Abfrage – aus der QueryDefs-Auflistung des Objekts zu löschen.

```
void DeleteQueryDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
Der Name der gespeicherten Abfrage, die gelöscht werden soll.

### <a name="remarks"></a>Bemerkungen

Danach wird diese Abfrage nicht mehr in der Datenbank definiert.

Informationen zum Erstellen von querydef-Objekten finden Sie unter Klasse [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Ein querydef-Objekt wird `CDaoDatabase` einem bestimmten Objekt `CDaoQueryDef` zugeordnet, wenn Sie das Objekt erstellen und es einen Zeiger an das Datenbankobjekt übergeben.

## <a name="cdaodatabasedeleterelation"></a><a name="deleterelation"></a>CDaoDatabase::DeleteRelation

Rufen Sie diese Memberfunktion auf, um eine vorhandene Beziehung aus der Relations-Auflistung des Datenbankobjekts zu löschen.

```
void DeleteRelation(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
Der Name der zu löschenden Beziehung.

### <a name="remarks"></a>Bemerkungen

Danach ist die Beziehung nicht mehr vorhanden.

Weitere Informationen finden Sie im Thema "Methode löschen" in der DAO-Hilfe.

## <a name="cdaodatabasedeletetabledef"></a><a name="deletetabledef"></a>CDaoDatabase::DeleteTableDef

Rufen Sie diese Memberfunktion auf, um die `CDaoDatabase` angegebene Tabelle und alle zugehörigen Daten aus der TableDefs-Auflistung des Objekts zu löschen.

```
void DeleteTableDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
Der Name der zu löschenden tabledef.

### <a name="remarks"></a>Bemerkungen

Danach wird diese Tabelle nicht mehr in der Datenbank definiert.

> [!NOTE]
> Achten Sie sehr darauf, Keine Systemtabellen zu löschen.

Informationen zum Erstellen von tabledef-Objekten finden Sie unter Klasse [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md). Ein tabledef-Objekt wird `CDaoDatabase` einem bestimmten Objekt `CDaoTableDef` zugeordnet, wenn Sie das Objekt erstellen und es einen Zeiger an das Datenbankobjekt übergeben.

Weitere Informationen finden Sie im Thema "Methode löschen" in der DAO-Hilfe.

## <a name="cdaodatabaseexecute"></a><a name="execute"></a>CDaoDatabase::Ausführen

Rufen Sie diese Memberfunktion auf, um eine Aktionsabfrage auszuführen oder eine SQL-Anweisung in der Datenbank auszuführen.

```
void Execute(
    LPCTSTR lpszSQL,
    int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Parameter

*Lpszsql*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die einen gültigen SQL-Befehl zum Ausführen enthält.

*nOptionen*<br/>
Eine ganze Zahl, die Optionen für die Integrität der Abfrage angibt. Sie können den bitwise-OR-Operator ( **&#124;**) verwenden, um eine der folgenden Konstanten zu `dbInconsistent` `dbConsistent`kombinieren (vorausgesetzt, die Kombination ist sinnvoll, z. B. würden Sie nicht mit kombinieren):

- `dbDenyWrite`Verweigern Sie anderen Benutzern schreibberechtigte Berechtigungen.

- `dbInconsistent`(Standard) Inkonsistente Aktualisierungen.

- `dbConsistent`Konsistente Aktualisierungen.

- `dbSQLPassThrough`SQL-Pass-Through. Bewirkt, dass die SQL-Anweisung zur Verarbeitung an eine ODBC-Datenquelle übergeben wird.

- `dbFailOnError`Rollbackaktualisierungen, wenn ein Fehler auftritt.

- `dbSeeChanges`Generieren Sie einen Laufzeitfehler, wenn ein anderer Benutzer Die von Ihnen bearbeiteten Daten ändert.

> [!NOTE]
> Wenn `dbInconsistent` beide `dbConsistent` enthalten sind oder wenn keines enthalten ist, ist das Ergebnis der Standardwert. Eine Erläuterung dieser Konstanten finden Sie im Thema "Execute Method" in der DAO-Hilfe.

### <a name="remarks"></a>Bemerkungen

`Execute`funktioniert nur für Aktionsabfragen oder SQL-Pass-Through-Abfragen, die keine Ergebnisse zurückgeben. Es funktioniert nicht für ausgewählte Abfragen, die Datensätze zurückgeben.

Eine Definition und Informationen zu Aktionsabfragen finden Sie in den Themen "Aktionsabfrage" und "Ausführungsmethode" in der DAO-Hilfe.

> [!TIP]
> Bei einer syntaktisch korrekten SQL-Anweisung `Execute` und den richtigen Berechtigungen schlägt die Memberfunktion auch dann nicht fehl, wenn nicht eine einzelne Zeile geändert oder gelöscht werden kann. Verwenden Sie daher `dbFailOnError` immer die `Execute` Option, wenn Sie die Memberfunktion verwenden, um eine Aktualisierungs- oder Löschabfrage auszuführen. Diese Option bewirkt, dass MFC eine Ausnahme vom Typ [CDaoException](../../mfc/reference/cdaoexception-class.md) auslöst und alle erfolgreichen Änderungen zurücksetzt, wenn einer der betroffenen Datensätze gesperrt ist und nicht aktualisiert oder gelöscht werden kann. Beachten Sie, dass `GetRecordsAffected` Sie immer anrufen können, um zu sehen, wie viele Datensätze betroffen waren.

Rufen Sie die [GetRecordsAffected-Memberfunktion](#getrecordsaffected) des Datenbankobjekts auf, `Execute` um die Anzahl der Datensätze zu ermitteln, die vom letzten Aufruf betroffen sind. Gibt `GetRecordsAffected` beispielsweise Informationen über die Anzahl der Datensätze zurück, die beim Ausführen einer Aktionsabfrage gelöscht, aktualisiert oder eingefügt wurden. Die zurückgegebene Anzahl spiegelt keine Änderungen in verknüpften Tabellen wider, wenn kaskadierte Aktualisierungen oder Löschungen wirksam sind.

`Execute`gibt kein Recordset zurück. Die `Execute` Verwendung einer Abfrage, die Datensätze auswählt, `CDaoException`bewirkt, dass MFC eine Ausnahme vom Typ auslöst. (Es gibt `ExecuteSQL` keine Memberfunktion `CDatabase::ExecuteSQL`analog zu .)

## <a name="cdaodatabasegetconnect"></a><a name="getconnect"></a>CDaoDatabase::GetConnect

Rufen Sie diese Memberfunktion auf, um `CDaoDatabase` die Verbindungszeichenfolge abzurufen, die zum Verbinden des Objekts mit einer ODBC- oder ISAM-Datenbank verwendet wird.

```
CString GetConnect();
```

### <a name="return-value"></a>Rückgabewert

Die Verbindungszeichenfolge, wenn [Open](#open) erfolgreich für eine ODBC-Datenquelle aufgerufen wurde; Andernfalls eine leere Zeichenfolge. Für einen Microsoft Jet (. MDB) ist die Zeichenfolge immer leer, es sei `dbSQLPassThrough` denn, Sie legen sie für die Verwendung mit der Option fest, die mit der [Memberfunktion Ausführen](#execute) verwendet wird oder zum Öffnen eines Recordsets verwendet wird.

### <a name="remarks"></a>Bemerkungen

Die Zeichenfolge enthält Informationen über die Quelle einer geöffneten Datenbank oder einer Datenbank, die in einer Pass-Through-Abfrage verwendet wird. Die Verbindungszeichenfolge besteht aus einem Datenbanktypbezeichner und null oder mehr Parametern, die durch Semikolons getrennt sind.

> [!NOTE]
> Die Verwendung der MFC-DAO-Klassen zum Herstellen einer Verbindung mit einer Datenquelle über ODBC ist weniger effizient als das Herstellen einer Verbindung über eine angefügte Tabelle.

> [!NOTE]
> Die Verbindungszeichenfolge wird verwendet, um bei Bedarf zusätzliche Informationen an ODBC und bestimmte ISAM-Treiber zu übergeben. Es wird nicht für verwendet. MDB-Datenbanken. Bei Microsoft Jet-Datenbankbasistabellen ist die Verbindungszeichenfolge eine leere Zeichenfolge (""), außer wenn Sie sie für eine SQL-Pass-Through-Abfrage verwenden, wie oben unter Rückgabewert beschrieben.

Eine Beschreibung, wie die Verbindungszeichenfolge erstellt wird, finden Sie in der Funktion [Öffnen](#open) von Membern. Nachdem die Verbindungszeichenfolge im `Open` Aufruf festgelegt wurde, können Sie sie später verwenden, um die Einstellung zu überprüfen, um den Typ, pfad, benutzer-ID, Kennwort oder ODBC-Datenquelle der Datenbank zu bestimmen.

## <a name="cdaodatabasegetname"></a><a name="getname"></a>CDaoDatabase::GetName

Rufen Sie diese Memberfunktion auf, um den Namen der aktuell geöffneten Datenbank abzurufen, d. h. den Namen einer vorhandenen Datenbankdatei oder den Namen einer registrierten ODBC-Datenquelle.

```
CString GetName();
```

### <a name="return-value"></a>Rückgabewert

Der vollständige Pfad und Dateiname der Datenbank, falls erfolgreich; Andernfalls wird ein [leerer CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Bemerkungen

Wenn Ihr Netzwerk die einheitliche Benennungskonvention (UNC) unterstützt, können\\\\\\Sie auch\\einen\\Netzwerkpfad\\angeben, z. B. " " "MYSERVER " MYSHARE , MYDIR , MYDB. MDB". (Doppelte umgekehrte Schrägstriche sind in\\Zeichenfolgenliteralen erforderlich, da " " das C++-Escapezeichen ist.)

Sie können diesen Namen z. B. in einer Überschrift anzeigen. Wenn beim Abrufen des Namens ein Fehler auftritt, löst MFC eine Ausnahme vom Typ [CDaoException](../../mfc/reference/cdaoexception-class.md)aus.

> [!NOTE]
> Um eine bessere Leistung beim Zugriff auf externe Datenbanken zu erzielen, wird empfohlen, externe Datenbanktabellen an eine Microsoft Jet-Datenbank anzufügen (. MDB), anstatt eine direkte Verbindung mit der Datenquelle herzustellen.

Der Datenbanktyp wird durch die Datei oder das Verzeichnis angezeigt, auf die der Pfad wie folgt zeigt:

|Pfadname zeigt auf..|Datenbanktyp|
|--------------------------|-------------------|
|. MDB-Datei|Microsoft Jet-Datenbank (Microsoft Access)|
|Verzeichnis, das enthält. DBF-Datei(n)|dBASE-Datenbank|
|Verzeichnis, das enthält. XLS-Datei|Microsoft Excel-Datenbank|
|Verzeichnis, das enthält. PDX-Datei(n)|Paradox-Datenbank|
|Verzeichnis, das entsprechend formatierte Textdatenbankdateien enthält|Textformatdatenbank|

Bei ODBC-Datenbanken wie SQL Server und Oracle identifiziert die Verbindungszeichenfolge der Datenbank einen Datenquellennamen (DSN), der von ODBC registriert ist.

## <a name="cdaodatabasegetquerydefcount"></a><a name="getquerydefcount"></a>CDaoDatabase::GetQueryDefCount

Rufen Sie diese Memberfunktion auf, um die Anzahl der Abfragen abzurufen, die in der QueryDefs-Auflistung der Datenbank definiert sind.

```
short GetQueryDefCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der in der Datenbank definierten Abfragen.

### <a name="remarks"></a>Bemerkungen

`GetQueryDefCount`ist nützlich, wenn Sie alle Querydefs in der QueryDefs-Auflistung durchlaufen müssen. Informationen zu einer bestimmten Abfrage in der Auflistung finden Sie unter [GetQueryDefInfo](#getquerydefinfo).

## <a name="cdaodatabasegetquerydefinfo"></a><a name="getquerydefinfo"></a>CDaoDatabase::GetQueryDefInfo

Rufen Sie diese Memberfunktion auf, um verschiedene Arten von Informationen zu einer in der Datenbank definierten Abfrage abzurufen.

```
void GetQueryDefInfo(
    int nIndex,
    CDaoQueryDefInfo& querydefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetQueryDefInfo(
    LPCTSTR lpszName,
    CDaoQueryDefInfo& querydefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der Index der vordefinierten Abfrage in der QueryDefs-Auflistung der Datenbank für die Suche nach Index.

*querydefinfo*<br/>
Ein Verweis auf ein [CDaoQueryDefInfo-Objekt,](../../mfc/reference/cdaoquerydefinfo-structure.md) das die angeforderten Informationen zurückgibt.

*dwInfoOptionen*<br/>
Optionen, die angeben, welche Informationen über das abzurufende Recordset abgerufen werden sollen. Die verfügbaren Optionen werden hier zusammen mit dem, was sie bewirken, dass die Funktion über das Recordset zurückgegeben:

- AFX_DAO_PRIMARY_INFO (Standard) Name, Typ

- AFX_DAO_SECONDARY_INFO Primärinformationen plus: Erstelltes Datum, Datum der letzten Aktualisierung, Rückgabedatensätze, Aktualtable

- AFX_DAO_ALL_INFO Primäre und sekundäre Informationen plus: SQL, Connect, ODBCTimeout

*lpszName*<br/>
Eine Zeichenfolge, die den Namen einer in der Datenbank definierten Abfrage für die Suche nach Namen enthält.

### <a name="remarks"></a>Bemerkungen

Es werden zwei Versionen der Funktion bereitgestellt, sodass Sie eine Abfrage entweder nach Index in der QueryDefs-Auflistung der Datenbank oder nach dem Namen der Abfrage auswählen können.

Eine Beschreibung der in *querydefinfo*zurückgegebenen Informationen finden Sie in der [CDaoQueryDefInfo-Struktur.](../../mfc/reference/cdaoquerydefinfo-structure.md) Diese Struktur verfügt über Member, die den oben aufgeführten Informationen in der Beschreibung von *dwInfoOptions*entsprechen. Wenn Sie eine Informationsebene anfordern, erhalten Sie auch frühere Informationsebenen.

## <a name="cdaodatabasegetquerytimeout"></a><a name="getquerytimeout"></a>CDaoDatabase::GetQueryTimeout

Rufen Sie diese Memberfunktion auf, um die aktuelle Anzahl von Sekunden abzurufen, die angezeigt werden sollen, bevor ein Timeout für nachfolgende Vorgänge in der verbundenen Datenbank überschritten wird.

```
short GetQueryTimeout();
```

### <a name="return-value"></a>Rückgabewert

Eine kurze Ganzenebene, die den Timeoutwert in Sekunden enthält.

### <a name="remarks"></a>Bemerkungen

Bei einem Vorgang kann aufgrund von Netzwerkzugriffsproblemen, übermäßiger Abfrageverarbeitungszeit usw. ein Zeitproblem auftreten. Während die Einstellung wirksam ist, wirkt sie sich auf alle Öffnen-, Neu-, Aktualisierungs- und Löschvorgänge für alle Recordsets aus, die diesem `CDaoDatabase` Objekt zugeordnet sind. Sie können die aktuelle Timeouteinstellung ändern, indem Sie [SetQueryTimeout](#setquerytimeout)aufrufen. Wenn Sie den Abfragetimeoutwert für ein Recordset nach dem Öffnen ändern, wird der Wert für das Recordset nicht geändert. Bei nachfolgenden [Move](../../mfc/reference/cdaorecordset-class.md#move) Move-Vorgängen wird z. B. der neue Wert nicht verwendet. Der Standardwert wird zunächst festgelegt, wenn das Datenbankmodul initialisiert wird.

Der Standardwert für Abfragetimeouts wird aus der Windows-Registrierung übernommen. Wenn keine Registrierungseinstellung vorhanden ist, ist die Standardeinstellung 60 Sekunden. Nicht alle Datenbanken unterstützen die Möglichkeit, einen Abfragetimeoutwert festzulegen. Wenn Sie einen Abfragetimeoutwert von 0 festlegen, tritt kein Timeout auf. und die Kommunikation mit der Datenbank reagiert möglicherweise nicht mehr. Dieses Verhalten kann während der Entwicklung nützlich sein. Wenn der Aufruf fehlschlägt, löst MFC eine Ausnahme vom Typ [CDaoException](../../mfc/reference/cdaoexception-class.md)aus.

Weitere Informationen finden Sie im Thema "QueryTimeout-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaodatabasegetrecordsaffected"></a><a name="getrecordsaffected"></a>CDaoDatabase::GetRecordsAffected

Rufen Sie diese Memberfunktion auf, um die Anzahl [Execute](#execute) der Datensätze zu ermitteln, die vom letzten Aufruf der Execute-Memberfunktion betroffen sind.

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Rückgabewert

Eine lange ganze Zahl, die die Anzahl der betroffenen Datensätze enthält.

### <a name="remarks"></a>Bemerkungen

Der zurückgegebene Wert enthält die Anzahl der Datensätze, die von `Execute`einer Aktionsabfrage, die mit ausgeführt wird, gelöscht, aktualisiert oder eingefügt wurden. Die zurückgegebene Anzahl spiegelt keine Änderungen in verknüpften Tabellen wider, wenn kaskadierte Aktualisierungen oder Löschungen wirksam sind.

Weitere Informationen finden Sie im Thema "RecordsAffected Property" in der DAO-Hilfe.

## <a name="cdaodatabasegetrelationcount"></a><a name="getrelationcount"></a>CDaoDatabase::GetRelationCount

Rufen Sie diese Memberfunktion auf, um die Anzahl der Beziehungen abzurufen, die zwischen Tabellen in der Datenbank definiert sind.

```
short GetRelationCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Beziehungen, die zwischen Tabellen in der Datenbank definiert sind.

### <a name="remarks"></a>Bemerkungen

`GetRelationCount`ist nützlich, wenn Sie alle definierten Beziehungen in der Relations-Auflistung der Datenbank durchlaufen müssen. Informationen zu einer bestimmten Beziehung in der Auflistung finden Sie unter [GetRelationInfo](#getrelationinfo).

Um das Konzept einer Beziehung zu veranschaulichen, betrachten Sie eine Suppliers-Tabelle und eine Tabelle "Produkte", die möglicherweise eine 1:n-Beziehung aufweisen. In dieser Beziehung kann ein Lieferant mehr als ein Produkt liefern. Andere Beziehungen sind eins zu eins und viele.

## <a name="cdaodatabasegetrelationinfo"></a><a name="getrelationinfo"></a>CDaoDatabase::GetRelationInfo

Rufen Sie diese Memberfunktion auf, um Informationen über eine angegebene Beziehung in der Relations-Auflistung der Datenbank abzurufen.

```
void GetRelationInfo(
    int nIndex,
    CDaoRelationInfo& relinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetRelationInfo(
    LPCTSTR lpszName,
    CDaoRelationInfo& relinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der Index des Beziehungsobjekts in der Relations-Auflistung der Datenbank für die Suche nach Index.

*relinfo*<br/>
Ein Verweis auf ein [CDaoRelationInfo-Objekt,](../../mfc/reference/cdaorelationinfo-structure.md) das die angeforderten Informationen zurückgibt.

*dwInfoOptionen*<br/>
Optionen, die angeben, welche Informationen über die abzurufende Beziehung abgerufen werden sollen. Die verfügbaren Optionen werden hier zusammen mit dem, was sie bewirken, dass die Funktion über die Beziehung zurückgegeben:

- AFX_DAO_PRIMARY_INFO (Standard) Name, Tabelle, Fremde Tabelle

- AFX_DAO_SECONDARY_INFO Attribute, Feldinformationen

Die Feldinformationen sind ein [CDaoRelationFieldInfo-Objekt,](../../mfc/reference/cdaorelationfieldinfo-structure.md) das die Felder aus der primären Tabelle enthält, die an der Beziehung beteiligt sind.

*lpszName*<br/>
Eine Zeichenfolge, die den Namen des Beziehungsobjekts enthält, für die Suche nach Namen.

### <a name="remarks"></a>Bemerkungen

Zwei Versionen dieser Funktion ermöglichen den Zugriff entweder nach Index oder nach Namen. Eine Beschreibung der in *relinfo*zurückgegebenen Informationen finden Sie in der [CDaoRelationInfo-Struktur.](../../mfc/reference/cdaorelationinfo-structure.md) Diese Struktur verfügt über Member, die den oben aufgeführten Informationen in der Beschreibung von *dwInfoOptions*entsprechen. Wenn Sie Informationen auf einer Ebene anfordern, erhalten Sie auch Informationen auf allen vorherigen Ebenen.

> [!NOTE]
> Wenn Sie die Attribute des Beziehungsobjekts so`dbRelationUpdateCascades` festlegen, dass Kaskadenvorgänge ( oder `dbRelationDeleteCascades`) aktiviert werden, aktualisiert oder löscht das Microsoft Jet-Datenbankmodul automatisch Datensätze in einer oder mehreren anderen Tabellen, wenn Änderungen an verwandten Primärschlüsseltabellen vorgenommen werden. Angenommen, Sie richten eine kaskadierte Löschbeziehung zwischen einer Customers-Tabelle und einer Tabelle "Bestellungen" ein. Wenn Sie Datensätze aus der Tabelle Customers löschen, werden auch Datensätze in der Tabelle Bestellungen gelöscht, die sich auf diesen Debitor beziehen. Wenn Sie kaskadierte Löschbeziehungen zwischen der Tabelle Orders und anderen Tabellen einrichten, werden Datensätze aus diesen Tabellen automatisch gelöscht, wenn Sie Datensätze aus der Tabelle Customers löschen.

## <a name="cdaodatabasegettabledefcount"></a><a name="gettabledefcount"></a>CDaoDatabase::GetTableDefCount

Rufen Sie diese Memberfunktion auf, um die Anzahl der in der Datenbank definierten Tabellen abzurufen.

```
short GetTableDefCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der in der Datenbank definierten Tabledefs.

### <a name="remarks"></a>Bemerkungen

`GetTableDefCount`ist nützlich, wenn Sie alle Tabellenefs in der TableDefs-Auflistung der Datenbank durchlaufen müssen. Informationen zu einer bestimmten Tabelle in der Auflistung finden Sie unter [GetTableDefInfo](#gettabledefinfo).

## <a name="cdaodatabasegettabledefinfo"></a><a name="gettabledefinfo"></a>CDaoDatabase::GetTableDefInfo

Rufen Sie diese Memberfunktion auf, um verschiedene Arten von Informationen zu einer in der Datenbank definierten Tabelle abzurufen.

```
void GetTableDefInfo(
    int nIndex,
    CDaoTableDefInfo& tabledefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetTableDefInfo(
    LPCTSTR lpszName,
    CDaoTableDefInfo& tabledefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der Index des tabledef-Objekts in der TableDefs-Auflistung der Datenbank für die Suche nach Index.

*tabledefinfo*<br/>
Ein Verweis auf ein [CDaoTableDefInfo-Objekt,](../../mfc/reference/cdaotabledefinfo-structure.md) das die angeforderten Informationen zurückgibt.

*dwInfoOptionen*<br/>
Optionen, die angeben, welche Informationen über die abzurufende Tabelle abgerufen werden sollen. Die verfügbaren Optionen werden hier zusammen mit dem, was sie bewirken, dass die Funktion über die Beziehung zurückgegeben:

- AFX_DAO_PRIMARY_INFO (Standard)-Name, Updatable, Attribute

- AFX_DAO_SECONDARY_INFO Primärinformationen plus: Erstelltes Datum, Datum der letzten Aktualisierung, Quelltabellenname, Verbinden

- AFX_DAO_ALL_INFO Primär- und Sekundärinformationen plus: Validierungsregel, Validierungstext, Datensatzanzahl

*lpszName*<br/>
Der Name des tabledef-Objekts für die Suche nach Namen.

### <a name="remarks"></a>Bemerkungen

Es werden zwei Versionen der Funktion bereitgestellt, sodass Sie eine Tabelle entweder nach Index in der TableDefs-Auflistung der Datenbank oder nach dem Namen der Tabelle auswählen können.

Eine Beschreibung der in *tabledefinfo*zurückgegebenen Informationen finden Sie in der [CDaoTableDefInfo-Struktur.](../../mfc/reference/cdaotabledefinfo-structure.md) Diese Struktur verfügt über Member, die den oben aufgeführten Informationen in der Beschreibung von *dwInfoOptions*entsprechen. Wenn Sie Informationen auf einer Ebene anfordern, erhalten Sie auch Informationen für alle vorherigen Ebenen.

> [!NOTE]
> Die Option AFX_DAO_ALL_INFO enthält Informationen, die nur langsam zu erhalten sind. In diesem Fall kann das Zählen der Datensätze in der Tabelle sehr zeitaufwändig sein, wenn viele Datensätze vorhanden sind.

## <a name="cdaodatabasegetversion"></a><a name="getversion"></a>CDaoDatabase::GetVersion

Rufen Sie diese Memberfunktion auf, um die Version der Microsoft Jet-Datenbankdatei zu ermitteln.

```
CString GetVersion();
```

### <a name="return-value"></a>Rückgabewert

Ein [CString,](../../atl-mfc-shared/reference/cstringt-class.md) der die Version der dem Objekt zugeordneten Datenbankdatei angibt.

### <a name="remarks"></a>Bemerkungen

Der zurückgegebene Wert stellt die Versionsnummer in der Form "major.minor" dar. z. B. "3.0". Die Produktversionsnummer (z. B. 3.0) besteht aus der Versionsnummer (3), einem Punkt und der Versionsnummer (0). Die bisherigen Versionen sind 1.0, 1.1, 2.0 und 3.0.

Weitere Informationen finden Sie im Thema "Versionseigenschaft" in der DAO-Hilfe.

## <a name="cdaodatabaseisopen"></a><a name="isopen"></a>CDaoDatabase::IsOpen

Rufen Sie diese Memberfunktion `CDaoDatabase` auf, um zu bestimmen, ob das Objekt derzeit in einer Datenbank geöffnet ist.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert `CDaoDatabase` ungleich Null, wenn das Objekt derzeit geöffnet ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

## <a name="cdaodatabasem_pdaodatabase"></a><a name="m_pdaodatabase"></a>CDaoDatabase::m_pDAODatabase

Enthält einen Zeiger auf die OLE-Schnittstelle für `CDaoDatabase` das DAO-Datenbankobjekt, das dem Objekt zugrunde liegt.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diesen Zeiger, wenn Sie direkt auf die DAO-Schnittstelle zugreifen müssen.

Informationen zum direkten Aufruf von DAO finden Sie unter [Technisches Hinweis 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="cdaodatabasem_pworkspace"></a><a name="m_pworkspace"></a>CDaoDatabase::m_pWorkspace

Enthält einen Zeiger auf das [CDaoWorkspace-Objekt,](../../mfc/reference/cdaoworkspace-class.md) das das Datenbankobjekt enthält.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diesen Zeiger, wenn Sie direkt auf den Arbeitsbereich zugreifen müssen, z. B. um Zeiger auf andere Datenbankobjekte in der Datenbanksammlung des Arbeitsbereichs abzurufen.

## <a name="cdaodatabaseopen"></a><a name="open"></a>CDaoDatabase::Öffnen

Sie müssen diese Memberfunktion aufrufen, `CDaoDatabase` um ein neu erstelltes Objekt zu initialisieren, das eine vorhandene Datenbank darstellt.

```
virtual void Open(
    LPCTSTR lpszName,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T(""));
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
Ein Zeichenfolgenausdruck, der der Name eines vorhandenen Microsoft Jet (. MDB) Datenbankdatei. Wenn der Dateiname eine Erweiterung hat, ist er erforderlich. Wenn Ihr Netzwerk die einheitliche Benennungskonvention (UNC) unterstützt, können\\\\\\Sie\\auch einen\\Netzwerkpfad angeben, z. B. " " "MYSERVER " MYSHARE , MYDIR\\, MYDB. MDB". (Doppelte umgekehrte Schrägstriche sind in\\Zeichenfolgenliteralen erforderlich, da " " das C++-Escapezeichen ist.)

Bei der Verwendung von *lpszName*gelten einige Überlegungen. Wenn es:

- Bezieht sich auf eine Datenbank, die bereits für den exklusiven Zugriff durch einen anderen Benutzer geöffnet ist, löst MFC eine Ausnahme vom Typ [CDaoException](../../mfc/reference/cdaoexception-class.md)aus. Machen Sie diese Ausnahme auf, um den Benutzer darüber zu informieren, dass die Datenbank nicht verfügbar ist.

- Ist eine leere Zeichenfolge ("") und *lpszConnect* ist "ODBC;", ein Dialogfeld mit allen registrierten ODBC-Datenquellennamen wird angezeigt, damit der Benutzer eine Datenbank auswählen kann. Sie sollten direkte Verbindungen zu ODBC-Datenquellen vermeiden. verwenden Sie stattdessen eine angefügte Tabelle.

- Andernfalls bezieht sich MFC nicht auf eine vorhandene Datenbank oder einen `CDaoException`gültigen ODBC-Datenquellennamen, MFC löst eine Ausnahme vom Typ aus.

> [!NOTE]
> Weitere Informationen zu DAO-Fehlercodes finden Sie im DAOERR. H-Datei. Weitere Informationen finden Sie im Thema "Trappable Data Access Errors" in der DAO-Hilfe.

*bExklusiv*<br/>
Ein boolescher Wert, der TRUE ist, wenn die Datenbank für exklusiven (nicht freigegebenen) Zugriff geöffnet werden soll, und FALSE, wenn die Datenbank für den freigegebenen Zugriff geöffnet werden soll. Wenn Sie dieses Argument weglassen, wird die Datenbank für den freigegebenen Zugriff geöffnet.

*bReadOnly*<br/>
Ein boolescher Wert, der TRUE ist, wenn die Datenbank für den schreibgeschützten Zugriff geöffnet werden soll, und FALSE, wenn die Datenbank für den Lese-/Schreibzugriff geöffnet werden soll. Wenn Sie dieses Argument weglassen, wird die Datenbank für den Lese-/Schreibzugriff geöffnet. Alle abhängigen Recordsets erben dieses Attribut.

*lpszConnect*<br/>
Ein Zeichenfolgenausdruck, der zum Öffnen der Datenbank verwendet wird. Diese Zeichenfolge stellt die ODBC-Verbindungsargumente dar. Sie müssen die exklusiven und schreibgeschützten Argumente angeben, um eine Quellzeichenfolge anzugeben. Wenn es sich bei der Datenbank um eine Microsoft Jet-Datenbank handelt (. MDB) ist diese Zeichenfolge leer (""). Die Syntax für den Standardwert – **_T**("") – stellt Die Portabilität für Unicode sowie ANSI-Builds Ihrer Anwendung bereit.

### <a name="remarks"></a>Bemerkungen

`Open`ordnet die Datenbank dem zugrunde liegenden DAO-Objekt zu. Sie können das Datenbankobjekt erst verwenden, um Recordset-, tabledef- oder querydef-Objekte zu erstellen, bis es initialisiert wurde. `Open`fügt das Datenbankobjekt an die Databases-Auflistung des zugeordneten Arbeitsbereichs an.

Verwenden Sie die Parameter wie folgt:

- Wenn Sie einen Microsoft Jet (. MDB) datenbank, verwenden Sie den Parameter *lpszName* und übergeben Sie eine leere Zeichenfolge für den *lpszConnect-Parameter* oder übergeben Sie eine Kennwortzeichenfolge des Formulars "; PWD=password", wenn die Datenbank kennwortgeschützt ist (. Nur MDB-Datenbanken).

- Wenn Sie eine ODBC-Datenquelle öffnen, übergeben Sie eine gültige ODBC-Verbindungszeichenfolge in *lpszConnect* und eine leere Zeichenfolge in *lpszName*.

Weitere Informationen finden Sie im Thema "OpenDatabase-Methode" in der DAO-Hilfe.

> [!NOTE]
> Für eine bessere Leistung beim Zugriff auf externe Datenbanken, einschließlich ISAM-Datenbanken und ODBC-Datenquellen, wird empfohlen, externe Datenbanktabellen an eine Microsoft Jet-Moduldatenbank anzuhängen (. MDB), anstatt eine direkte Verbindung mit der Datenquelle herzustellen.

Es ist möglich, dass ein Verbindungsversuch ein Timeout ausfällt, wenn z. B. der DBMS-Host nicht verfügbar ist. Wenn der Verbindungsversuch `Open` fehlschlägt, wird eine Ausnahme vom Typ [CDaoException](../../mfc/reference/cdaoexception-class.md)ausgelöst.

Die übrigen Bemerkungen gelten nur für ODBC-Datenbanken:

Wenn es sich bei der Datenbank um `Open` eine ODBC-Datenbank handelt und die Parameter in Ihrem Aufruf nicht genügend Informationen enthalten, um die Verbindung herzustellen, öffnet der ODBC-Treiber ein Dialogfeld, um die erforderlichen Informationen vom Benutzer zu erhalten. Wenn Sie `Open`aufrufen, wird ihre Verbindungszeichenfolge *lpszConnect*privat gespeichert und ist durch Aufrufen der [GetConnect-Memberfunktion](#getconnect) verfügbar.

Wenn Sie möchten, können Sie Ihr eigenes `Open` Dialogfeld öffnen, bevor Sie aufrufen, um Informationen vom Benutzer abzurufen, z. B. ein Kennwort, und diese Informationen dann der Verbindungszeichenfolge hinzufügen, die Sie an `Open`übergeben. Oder Sie möchten die Verbindungszeichenfolge speichern, die Sie übergeben haben (z. B. in `Open` der `CDaoDatabase` Windows-Registrierung), damit Sie sie beim nächsten Aufrufen eines Objekts wiederverwenden können.

Sie können die Verbindungszeichenfolge auch für mehrere Ebenen der `CDaoDatabase` Anmeldeautorisierung (jeweils für ein anderes Objekt) oder zum Übermitteln anderer datenbankspezifischer Informationen verwenden.

## <a name="cdaodatabasesetquerytimeout"></a><a name="setquerytimeout"></a>CDaoDatabase::SetQueryTimeout

Rufen Sie diese Memberfunktion auf, um die Standardanzahl von Sekunden zu überschreiben, um vor nachfolgenden Vorgängen für die verbundene Datenbank ein Timeout zu ermöglichen.

```
void SetQueryTimeout(short nSeconds);
```

### <a name="parameters"></a>Parameter

*nSekunden*<br/>
Die Anzahl der Sekunden, die vor einem Abfrageversuch zugelassen werden sollen.

### <a name="remarks"></a>Bemerkungen

Bei einem Vorgang kann aufgrund von Netzwerkzugriffsproblemen, übermäßiger Abfrageverarbeitungszeit usw. ein Zeitproblem auftreten. Rufen `SetQueryTimeout` Sie vor dem Öffnen des Recordsets oder vor dem Aufrufen der [Memberfunktionen AddNew](../../mfc/reference/cdaorecordset-class.md#addnew), [Update](../../mfc/reference/cdaorecordset-class.md#update)oder [Delete](../../mfc/reference/cdaorecordset-class.md#delete) des Recordsets auf, wenn Sie den Abfragetimeoutwert ändern möchten. Die Einstellung wirkt sich `Update`auf `Delete` alle nachfolgenden [Open](../../mfc/reference/cdaorecordset-class.md#open) `AddNew`, `CDaoDatabase` , und Aufrufe von Recordsets aus, die diesem Objekt zugeordnet sind. Wenn Sie den Abfragetimeoutwert für ein Recordset nach dem Öffnen ändern, wird der Wert für das Recordset nicht geändert. Bei nachfolgenden [Move](../../mfc/reference/cdaorecordset-class.md#move) Move-Vorgängen wird z. B. der neue Wert nicht verwendet.

Der Standardwert für Abfragetimeouts beträgt 60 Sekunden. Nicht alle Datenbanken unterstützen die Möglichkeit, einen Abfragetimeoutwert festzulegen. Wenn Sie einen Abfragetimeoutwert von 0 festlegen, tritt kein Timeout auf. die Kommunikation mit der Datenbank reagiert möglicherweise nicht mehr. Dieses Verhalten kann während der Entwicklung nützlich sein.

Weitere Informationen finden Sie im Thema "QueryTimeout-Eigenschaft" in der DAO-Hilfe.

## <a name="see-also"></a>Siehe auch

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDaoWorkspace-Klasse](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoRecordset-Klasse](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef-Klasse](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef-Klasse](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDatabase-Klasse](../../mfc/reference/cdatabase-class.md)<br/>
[CDaoException-Klasse](../../mfc/reference/cdaoexception-class.md)
