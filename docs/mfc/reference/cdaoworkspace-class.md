---
title: CDaoWorkspace-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDaoWorkspace
- AFXDAO/CDaoWorkspace
- AFXDAO/CDaoWorkspace::CDaoWorkspace
- AFXDAO/CDaoWorkspace::Append
- AFXDAO/CDaoWorkspace::BeginTrans
- AFXDAO/CDaoWorkspace::Close
- AFXDAO/CDaoWorkspace::CommitTrans
- AFXDAO/CDaoWorkspace::CompactDatabase
- AFXDAO/CDaoWorkspace::Create
- AFXDAO/CDaoWorkspace::GetDatabaseCount
- AFXDAO/CDaoWorkspace::GetDatabaseInfo
- AFXDAO/CDaoWorkspace::GetIniPath
- AFXDAO/CDaoWorkspace::GetIsolateODBCTrans
- AFXDAO/CDaoWorkspace::GetLoginTimeout
- AFXDAO/CDaoWorkspace::GetName
- AFXDAO/CDaoWorkspace::GetUserName
- AFXDAO/CDaoWorkspace::GetVersion
- AFXDAO/CDaoWorkspace::GetWorkspaceCount
- AFXDAO/CDaoWorkspace::GetWorkspaceInfo
- AFXDAO/CDaoWorkspace::Idle
- AFXDAO/CDaoWorkspace::IsOpen
- AFXDAO/CDaoWorkspace::Open
- AFXDAO/CDaoWorkspace::RepairDatabase
- AFXDAO/CDaoWorkspace::Rollback
- AFXDAO/CDaoWorkspace::SetDefaultPassword
- AFXDAO/CDaoWorkspace::SetDefaultUser
- AFXDAO/CDaoWorkspace::SetIniPath
- AFXDAO/CDaoWorkspace::SetIsolateODBCTrans
- AFXDAO/CDaoWorkspace::SetLoginTimeout
- AFXDAO/CDaoWorkspace::m_pDAOWorkspace
helpviewer_keywords:
- CDaoWorkspace [MFC], CDaoWorkspace
- CDaoWorkspace [MFC], Append
- CDaoWorkspace [MFC], BeginTrans
- CDaoWorkspace [MFC], Close
- CDaoWorkspace [MFC], CommitTrans
- CDaoWorkspace [MFC], CompactDatabase
- CDaoWorkspace [MFC], Create
- CDaoWorkspace [MFC], GetDatabaseCount
- CDaoWorkspace [MFC], GetDatabaseInfo
- CDaoWorkspace [MFC], GetIniPath
- CDaoWorkspace [MFC], GetIsolateODBCTrans
- CDaoWorkspace [MFC], GetLoginTimeout
- CDaoWorkspace [MFC], GetName
- CDaoWorkspace [MFC], GetUserName
- CDaoWorkspace [MFC], GetVersion
- CDaoWorkspace [MFC], GetWorkspaceCount
- CDaoWorkspace [MFC], GetWorkspaceInfo
- CDaoWorkspace [MFC], Idle
- CDaoWorkspace [MFC], IsOpen
- CDaoWorkspace [MFC], Open
- CDaoWorkspace [MFC], RepairDatabase
- CDaoWorkspace [MFC], Rollback
- CDaoWorkspace [MFC], SetDefaultPassword
- CDaoWorkspace [MFC], SetDefaultUser
- CDaoWorkspace [MFC], SetIniPath
- CDaoWorkspace [MFC], SetIsolateODBCTrans
- CDaoWorkspace [MFC], SetLoginTimeout
- CDaoWorkspace [MFC], m_pDAOWorkspace
ms.assetid: 64f60de6-4df1-4d4a-a65b-c489b5257d52
ms.openlocfilehash: 52aaa4970ef483988194691eb6b870cbfe51f494
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377116"
---
# <a name="cdaoworkspace-class"></a>CDaoWorkspace-Klasse

Verwaltet eine benannte, kennwortgeschützte Datenbanksitzung eines einzelnen Benutzers von der Anmeldung bis zu Abmeldung. DAO wird über Office 2013 unterstützt. DAO 3.6 ist die endgültige Version und gilt als veraltet.

## <a name="syntax"></a>Syntax

```
class CDaoWorkspace : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoWorkspace::CDaoWorkspace](#cdaoworkspace)|Erstellt ein Arbeitsbereichsobjekt. Danach rufen `Create` `Open`Sie an oder .|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoWorkspace::Anfügen](#append)|Fügt einen neu erstellten Arbeitsbereich an die Workspaces-Auflistung des Datenbankmoduls an.|
|[CDaoWorkspace::BeginTrans](#begintrans)|Startet eine neue Transaktion, die für alle im Arbeitsbereich geöffneten Datenbanken gilt.|
|[CDaoWorkspace::Schließen](#close)|Schließt den Arbeitsbereich und alle darin enthaltenen Objekte. Ausstehende Transaktionen werden zurückgesetzt.|
|[CDaoWorkspace::CommitTrans](#committrans)|Schließt die aktuelle Transaktion ab und speichert die Änderungen.|
|[CDaoWorkspace::CompactDatabase](#compactdatabase)|Komprimiert (oder dupliziert) eine Datenbank.|
|[CDaoWorkspace::Erstellen](#create)|Erstellt ein neues DAO-Arbeitsbereichsobjekt.|
|[CDaoWorkspace::GetDatabaseCount](#getdatabasecount)|Gibt die Anzahl der DAO-Datenbankobjekte in der Datenbanksammlung des Arbeitsbereichs zurück.|
|[CDaoWorkspace::GetDatabaseInfo](#getdatabaseinfo)|Gibt Informationen zu einer angegebenen DAO-Datenbank zurück, die in der Datenbanksammlung des Arbeitsbereichs definiert ist.|
|[CDaoWorkspace::GetIniPath](#getinipath)|Gibt den Speicherort der Initialisierungseinstellungen des Microsoft Jet-Datenbankmoduls in der Windows-Registrierung zurück.|
|[CDaoWorkspace::GetIsolateODBCTrans](#getisolateodbctrans)|Gibt einen Wert zurück, der angibt, ob mehrere Transaktionen, die dieselbe ODBC-Datenquelle enthalten, über erzwungene mehrfache Verbindungen zur Datenquelle isoliert werden.|
|[CDaoWorkspace::GetLoginTimeout](#getlogintimeout)|Gibt die Anzahl der Sekunden zurück, bevor ein Fehler auftritt, wenn der Benutzer versucht, sich bei einer ODBC-Datenbank anzumelden.|
|[CDaoWorkspace::GetName](#getname)|Gibt den benutzerdefinierten Namen für das Arbeitsbereichsobjekt zurück.|
|[CDaoWorkspace::GetUserName](#getusername)|Gibt den Benutzernamen zurück, der beim Erstellen des Arbeitsbereichs angegeben wurde. Dies ist der Name des Arbeitsbereichsbesitzers.|
|[CDaoWorkspace::GetVersion](#getversion)|Gibt eine Zeichenfolge zurück, die die Version des Datenbankmoduls enthält, das dem Arbeitsbereich zugeordnet ist.|
|[CDaoWorkspace::GetWorkspaceCount](#getworkspacecount)|Gibt die Anzahl der DAO-Arbeitsbereichsobjekte in der Workspaces-Auflistung des Datenbankmoduls zurück.|
|[CDaoWorkspace::GetWorkspaceInfo](#getworkspaceinfo)|Gibt Informationen zu einem angegebenen DAO-Arbeitsbereich zurück, der in der Workspaces-Auflistung des Datenbankmoduls definiert ist.|
|[CDaoWorkspace::Leerlauf](#idle)|Ermöglicht dem Datenbankmodul die Ausführung von Hintergrundaufgaben.|
|[CDaoWorkspace::IsOpen](#isopen)|Gibt einen Wert ungleich Null zurück, wenn der Arbeitsbereich geöffnet ist.|
|[CDaoWorkspace::Öffnen](#open)|Öffnet explizit ein Arbeitsbereichsobjekt, das dem Standardarbeitsbereich von DAO zugeordnet ist.|
|[CDaoWorkspace::RepairDatabase](#repairdatabase)|Versucht, eine beschädigte Datenbank zu reparieren.|
|[CDaoWorkspace::Rollback](#rollback)|Beendet die aktuelle Transaktion und speichert die Änderungen nicht.|
|[CDaoWorkspace::SetDefaultPassword](#setdefaultpassword)|Legt das Kennwort fest, das das Datenbankmodul verwendet, wenn ein Arbeitsbereichsobjekt ohne ein bestimmtes Kennwort erstellt wird.|
|[CDaoWorkspace::SetDefaultUser](#setdefaultuser)|Legt den Benutzernamen fest, den das Datenbankmodul verwendet, wenn ein Arbeitsbereichsobjekt ohne einen bestimmten Benutzernamen erstellt wird.|
|[CDaoWorkspace::SetIniPath](#setinipath)|Legt den Speicherort der Initialisierungseinstellungen des Microsoft Jet-Datenbankmoduls in der Windows-Registrierung fest.|
|[CDaoWorkspace::SetIsolateODBCTrans](#setisolateodbctrans)|Gibt an, ob mehrere Transaktionen, die dieselbe ODBC-Datenquelle enthalten, isoliert werden, indem mehrere Verbindungen zur Datenquelle erzwungen werden.|
|[CDaoWorkspace::SetLoginTimeout](#setlogintimeout)|Legt die Anzahl der Sekunden fest, bevor ein Fehler auftritt, wenn der Benutzer versucht, sich bei einer ODBC-Datenquelle anzumelden.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoWorkspace::m_pDAOWorkspace](#m_pdaoworkspace)|Zeigt auf das zugrunde liegende DAO-Arbeitsbereichsobjekt.|

## <a name="remarks"></a>Bemerkungen

In den meisten Fällen benötigen Sie nicht mehrere Arbeitsbereiche, und Sie müssen keine expliziten Arbeitsbereichsobjekte erstellen. Wenn Sie Datenbank- und Recordset-Objekte öffnen, verwenden sie den Standardarbeitsbereich von DAO. Bei Bedarf können Sie jedoch mehrere Sitzungen gleichzeitig ausführen, indem Sie zusätzliche Arbeitsbereichsobjekte erstellen. Jedes Arbeitsbereichsobjekt kann mehrere geöffnete Datenbankobjekte in seiner eigenen Datenbankauflistung enthalten. In MFC ist ein Arbeitsbereich in erster Linie ein Transaktions-Manager, der eine Reihe offener Datenbanken im gleichen "Transaktionsbereich" angibt.

> [!NOTE]
> Die DAO-Datenbankklassen unterscheiden sich von den MFC-Datenbankklassen, die auf Open Database Connectivity (ODBC) basieren. Alle DAO-Datenbankklassennamen haben das Präfix "CDao". Im Allgemeinen sind die Aufbasis von DAO basierenden MFC-Klassen leistungsfähiger als die MFC-Klassen, die auf ODBC basieren. Die DAO-basierten Klassen greifen über das Microsoft Jet-Datenbankmodul auf Daten zu, einschließlich ODBC-Treibern. Sie unterstützen auch DDL-Vorgänge (Data Definition Language), z. B. das Erstellen von Datenbanken und das Hinzufügen von Tabellen und Feldern über die Klassen, ohne DAO direkt aufrufen zu müssen.

## <a name="capabilities"></a>Funktionen

Die `CDaoWorkspace` Klasse bietet Folgendes:

- Expliziter Zugriff, falls erforderlich, auf einen Standardarbeitsbereich, der durch Initialisieren des Datenbankmoduls erstellt wird. Normalerweise verwenden Sie den Standardarbeitsbereich von DAO implizit, indem Sie Datenbank- und Recordset-Objekte erstellen.

- Ein Transaktionsbereich, in dem Transaktionen für alle im Arbeitsbereich geöffneten Datenbanken gelten. Sie können zusätzliche Arbeitsbereiche erstellen, um separate Transaktionsbereiche zu verwalten.

- Eine Schnittstelle zu vielen Eigenschaften des zugrunde liegenden Microsoft Jet-Datenbankmoduls (siehe statische Memberfunktionen). Beim Öffnen oder Erstellen eines Arbeitsbereichs oder beim Aufrufen einer statischen Memberfunktion vor dem Öffnen oder Erstellen wird das Datenbankmodul initialisiert.

- Zugriff auf die Workspaces-Auflistung des Datenbankmoduls, in der alle aktiven Arbeitsbereiche gespeichert werden, die an sie angehängt wurden. Sie können auch Arbeitsbereiche erstellen und mit ihnen arbeiten, ohne sie an die Sammlung anzuhängen.

## <a name="security"></a>Sicherheit

MFC implementiert keine Benutzer- und Gruppensammlungen in DAO, die für die Sicherheitskontrolle verwendet werden. Wenn Sie diese Aspekte von DAO benötigen, müssen Sie sie selbst über direkte Aufrufe an DAO-Schnittstellen programmieren. Weitere Informationen finden Sie unter [Technische Anmerkung 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="usage"></a>Verwendung

Sie können `CDaoWorkspace` die Klasse verwenden, um:

- Öffnen Sie den Standardarbeitsbereich explizit.

   Normalerweise ist die Verwendung des Standardarbeitsbereichs implizit, wenn Sie neue [CDaoDatabase-](../../mfc/reference/cdaodatabase-class.md) oder [CDaoRecordset-Objekte](../../mfc/reference/cdaorecordset-class.md) öffnen. Möglicherweise müssen Sie jedoch explizit darauf zugreifen, z. B. um auf Die Eigenschaften des Datenbankmoduls oder auf die Workspaces-Auflistung zuzugreifen. Siehe "Implizite Verwendung des Standardarbeitsbereichs" weiter unten.

- Erstellen Sie neue Arbeitsbereiche. Rufen Sie [Append](#append) auf, wenn Sie sie der Workspaces-Auflistung hinzufügen möchten.

- Öffnen Sie einen vorhandenen Arbeitsbereich in der Workspaces-Auflistung.

Das Erstellen eines neuen Arbeitsbereichs, der noch nicht in der Workspaces-Auflistung vorhanden ist, wird unter [der](#create) Funktion Member erstellen beschrieben. Workspace-Objekte bleiben zwischen Datababase-Engine-Sitzungen in keiner Weise erhalten. Wenn Ihre Anwendung MFC statisch verknüpft, wird das Datenbankmodul durch das Beenden der Anwendung nicht initialisiert. Wenn Ihre Anwendung dynamisch mit MFC verknüpft wird, wird das Datenbankmodul beim Entladen der MFC-DLL nicht initialisiert.

Das explizite Öffnen des Standardarbeitsbereichs oder das Öffnen eines vorhandenen Arbeitsbereichs in der Workspaces-Auflistung wird unter der Funktion [Member öffnen](#open) beschrieben.

Beenden Sie eine Arbeitsbereichssitzung, indem Sie den Arbeitsbereich mit der Memberfunktion [Schließen](#close) schließen schließen. `Close`schließt alle Datenbanken, die Sie zuvor nicht geschlossen haben, und setzt alle nicht festgeschriebenen Transaktionen zurück.

## <a name="transactions"></a>Transaktionen

DAO verwaltet Transaktionen auf Arbeitsbereichsebene. Daher gelten Transaktionen in einem Arbeitsbereich mit mehreren geöffneten Datenbanken für alle Datenbanken. Wenn z. B. zwei Datenbanken nicht festgeschriebene Aktualisierungen haben und Sie [CommitTrans](#committrans)aufrufen, werden alle Updates festgeschrieben. Wenn Sie Transaktionen auf eine einzelne Datenbank beschränken möchten, benötigen Sie dafür ein separates Arbeitsbereichsobjekt.

## <a name="implicit-use-of-the-default-workspace"></a>Implizite Verwendung des Standardarbeitsbereichs

MFC verwendet den Standardarbeitsbereich von DAO implizit unter den folgenden Umständen:

- Wenn Sie ein `CDaoDatabase` neues Objekt erstellen, dies jedoch nicht über ein vorhandenes `CDaoWorkspace` Objekt tun, erstellt MFC ein temporäres Arbeitsbereichsobjekt für Sie, das dem Standardarbeitsbereich von DAO entspricht. Wenn Sie dies für mehrere Datenbanken tun, sind alle Datenbankobjekte dem Standardarbeitsbereich zugeordnet. Sie können über ein `CDaoDatabase` Datenmitglied auf den Arbeitsbereich einer Datenbank zugreifen.

- Wenn Sie ein `CDaoRecordset` Objekt erstellen, ohne einen `CDaoDatabase` Zeiger auf ein Objekt zu geben, erstellt MFC ein temporäres Datenbankobjekt und durch Erweiterung ein temporäres Arbeitsbereichsobjekt. Sie können über ein `CDaoRecordset` Datenmitglied auf die Datenbank eines Recordsets und indirekt auf dessen Arbeitsbereich zugreifen.

## <a name="other-operations"></a>Sonstige Operationen

Andere Datenbankvorgänge werden ebenfalls bereitgestellt, z. B. das Reparieren einer beschädigten Datenbank oder das Komprimieren einer Datenbank.

Informationen zum direkten Aufruf von DAO und zur DAO-Sicherheit finden Sie unter [Technische Anmerkung 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CDaoWorkspace`

## <a name="requirements"></a>Anforderungen

**Header:** afxdao.h

## <a name="cdaoworkspaceappend"></a><a name="append"></a>CDaoWorkspace::Anfügen

Rufen Sie diese Memberfunktion auf, nachdem Sie [Create](#create)aufrufen.

```
virtual void Append();
```

### <a name="remarks"></a>Bemerkungen

`Append`fügt ein neu erstelltes Arbeitsbereichsobjekt an die Workspaces-Auflistung des Datenbankmoduls an. Arbeitsbereiche bleiben nicht zwischen Datenbankmodulsitzungen bestehen. Sie werden nur im Arbeitsspeicher gespeichert, nicht auf dem Datenträger. Sie müssen keinen Arbeitsbereich anhängen. Wenn Sie dies nicht tun, können Sie es trotzdem verwenden.

Ein angehängter Arbeitsbereich verbleibt in der Workspaces-Auflistung in einem aktiven, offenen Zustand, bis Sie die Memberfunktion ["Schließen"](#close) aufrufen.

Weitere Informationen finden Sie im Thema "Append-Methode" in der DAO-Hilfe.

## <a name="cdaoworkspacebegintrans"></a><a name="begintrans"></a>CDaoWorkspace::BeginTrans

Rufen Sie diese Memberfunktion auf, um eine Transaktion zu initiieren.

```
void BeginTrans();
```

### <a name="remarks"></a>Bemerkungen

Nach dem `BeginTrans`Aufruf werden Aktualisierungen, die Sie an Ihren Daten oder der Datenbankstruktur vornehmen, wirksam, wenn Sie die Transaktion festsetzen. Da der Arbeitsbereich einen einzelnen Transaktionsbereich definiert, gilt die Transaktion für alle geöffneten Datenbanken im Arbeitsbereich. Es gibt zwei Möglichkeiten, die Transaktion abzuschließen:

- Rufen Sie die [CommitTrans-Memberfunktion](#committrans) auf, um die Transaktion zu übertragen und Änderungen an der Datenquelle zu speichern.

- Oder rufen Sie die [Rollback-Memberfunktion](#rollback) auf, um die Transaktion abzubrechen.

Beim Schließen des Arbeitsbereichsobjekts oder eines Datenbankobjekts, während eine Transaktion ausstehend ist, werden alle ausstehenden Transaktionen zurückgesetzt.

Wenn Sie Transaktionen auf einer ODBC-Datenquelle von denen in einer anderen ODBC-Datenquelle isolieren müssen, lesen Sie die [SetIsolateODBCTrans-Memberfunktion.](#setisolateodbctrans)

## <a name="cdaoworkspacecdaoworkspace"></a><a name="cdaoworkspace"></a>CDaoWorkspace::CDaoWorkspace

Erstellt ein `CDaoWorkspace`-Objekt.

```
CDaoWorkspace();
```

### <a name="remarks"></a>Bemerkungen

Nach dem Erstellen des C++-Objekts haben Sie zwei Möglichkeiten:

- Rufen Sie die [Memberfunktion "Öffnen"](#open) des Objekts auf, um den Standardarbeitsbereich zu öffnen oder ein vorhandenes Objekt in der Workspaces-Auflistung zu öffnen.

- Oder rufen Sie die Memberfunktion [Erstellen](#create) des Objekts auf, um ein neues DAO-Arbeitsbereichsobjekt zu erstellen. Dadurch wird explizit eine neue Arbeitsbereichssitzung gestartet, auf die Sie über das `CDaoWorkspace` Objekt verweisen können. Nach `Create`dem Aufruf können Sie [Append](#append) aufrufen, wenn Sie den Arbeitsbereich der Workspaces-Auflistung des Datenbankmoduls hinzufügen möchten.

In der Klassenübersicht für [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) finden Sie Informationen `CDaoWorkspace` darüber, wann Sie explizit ein Objekt erstellen müssen. Normalerweise verwenden Sie Arbeitsbereiche, die implizit erstellt werden, wenn Sie ein [CDaoDatabase-Objekt](../../mfc/reference/cdaodatabase-class.md) öffnen, ohne einen Arbeitsbereich anzugeben, oder wenn Sie ein [CDaoRecordset-Objekt](../../mfc/reference/cdaorecordset-class.md) öffnen, ohne ein Datenbankobjekt anzugeben. MFC-DAO-Objekte, die auf diese Weise erstellt wurden, verwenden den Standardarbeitsbereich von DAO, der einmal erstellt und wiederverwendet wird.

Um einen Arbeitsbereich und seine enthaltenen Objekte freizugeben, rufen Sie die [Memberfunktion "Schließen"](#close) des Workspace-Objekts auf.

## <a name="cdaoworkspaceclose"></a><a name="close"></a>CDaoWorkspace::Schließen

Rufen Sie diese Memberfunktion auf, um das Arbeitsbereichsobjekt zu schließen.

```
virtual void Close();
```

### <a name="remarks"></a>Bemerkungen

Beim Schließen eines geöffneten Arbeitsbereichsobjekts wird das zugrunde liegende DAO-Objekt freigegeben und, wenn der Arbeitsbereich Mitglied der Workspaces-Auflistung ist, aus der Auflistung entfernt. Aufrufen `Close` ist eine gute Programmierpraxis.

> [!CAUTION]
> Beim Schließen eines Arbeitsbereichsobjekts werden alle geöffneten Datenbanken im Arbeitsbereich geschlossen. Dies führt dazu, dass alle Recordsets, die in den Datenbanken geöffnet werden, ebenfalls geschlossen werden, und alle ausstehenden Bearbeitungen oder Aktualisierungen werden zurückgesetzt. Weitere Informationen finden Sie in den Memberfunktionen [CDaoDatabase::Close](../../mfc/reference/cdaodatabase-class.md#close), [CDaoRecordset::Close](../../mfc/reference/cdaorecordset-class.md#close), [CDaoTableDef::Close](../../mfc/reference/cdaotabledef-class.md#close)und [CDaoQueryDef::Close.](../../mfc/reference/cdaoquerydef-class.md#close)

Arbeitsbereichsobjekte sind nicht permanent. sie existieren nur, solange Verweise auf sie vorhanden sind. Dies bedeutet, dass der Arbeitsbereich und seine Datenbanksammlung nach dem Ende der Datenbankmodulsitzung nicht beibehalten werden. Sie müssen sie für die nächste Sitzung neu erstellen, indem Sie Den Arbeitsbereich und die Datenbank(n) erneut öffnen.

Weitere Informationen finden Sie im Thema "Close-Methode" in der DAO-Hilfe.

## <a name="cdaoworkspacecommittrans"></a><a name="committrans"></a>CDaoWorkspace::CommitTrans

Rufen Sie diese Memberfunktion auf, um eine Transaktion zu übertragen – speichern Sie eine Gruppe von Änderungen und Aktualisierungen in einer oder mehreren Datenbanken im Arbeitsbereich.

```
void CommitTrans();
```

### <a name="remarks"></a>Bemerkungen

Eine Transaktion besteht aus einer Reihe von Änderungen an den Daten der Datenbank oder ihrer Struktur, beginnend mit einem Aufruf von [BeginTrans](#begintrans). Wenn Sie die Transaktion abschließen, übertragen Sie sie entweder oder setzen Sie sie mit [Rollback](#rollback)zurück (abbrechen Sie die Änderungen). Standardmäßig werden Aktualisierungen von Datensätzen ohne Transaktionen sofort festgeschrieben. Durch `BeginTrans` aufrufen wird die Zusage `CommitTrans`von Aktualisierungen verzögert, bis Sie anrufen.

> [!CAUTION]
> Innerhalb eines Arbeitsbereichs sind Transaktionen immer global für den Arbeitsbereich und nicht auf eine Datenbank oder ein Recordset beschränkt. Wenn Sie Vorgänge für mehr als eine Datenbank oder `CommitTrans` ein Recordset innerhalb `Rollback` einer Arbeitsbereichstransaktion ausführen, überträgt alle ausstehenden Aktualisierungen und stellt alle Vorgänge für diese Datenbanken und Recordsets wieder her.

Wenn Sie eine Datenbank oder einen Arbeitsbereich mit ausstehenden Transaktionen schließen, werden alle Transaktionen zurückgesetzt.

> [!NOTE]
> Dies ist kein zweiphasiges Commit-Verfahren. Wenn eine Aktualisierung nicht übertragen werden kann, werden andere weiterhin einen Commit durchführen.

## <a name="cdaoworkspacecompactdatabase"></a><a name="compactdatabase"></a>CDaoWorkspace::CompactDatabase

Rufen Sie diese Memberfunktion auf, um einen angegebenen Microsoft Jet (. MDB)-Datenbank.

```
static void PASCAL CompactDatabase(
    LPCTSTR lpszSrcName,
    LPCTSTR lpszDestName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int nOptions = 0);

static void PASCAL CompactDatabase(
    LPCTSTR lpszSrcName,
    LPCTSTR lpszDestName,
    LPCTSTR lpszLocale,
    int nOptions,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parameter

*lpszSrcName*<br/>
Der Name einer vorhandenen, geschlossenen Datenbank. Es kann sich um einen vollständigen Pfad und\\Dateinamen handelt, z. B. "C: .MYDB. MDB". Wenn der Dateiname eine Erweiterung hat, müssen Sie ihn angeben. Wenn Ihr Netzwerk die einheitliche Benennungskonvention (UNC) unterstützt, können\\\\\\Sie\\auch einen\\Netzwerkpfad angeben, z. B. " " "MYSERVER " MYSHARE , MYDIR\\, MYDB. MDB". (Doppelte umgekehrte Schrägstriche sind in\\den Pfadzeichenfolgen erforderlich, da " " das C++-Escapezeichen ist.)

*lpszDestName*<br/>
Der vollständige Pfad der komprimierten Datenbank, die Sie erstellen. Sie können auch einen Netzwerkpfad wie bei *lpszSrcName*angeben. Sie können das Argument *lpszDestName* nicht verwenden, um dieselbe Datenbankdatei wie *lpszSrcName*anzugeben.

*lpszPasswort*<br/>
Ein Kennwort, das verwendet wird, wenn Sie eine kennwortgeschützte Datenbank komprimieren möchten. Beachten Sie, dass Sie `CompactDatabase` alle Parameter angeben müssen, wenn Sie die Version davon verwenden, die ein Kennwort erfordert. Da es sich um einen connect-Parameter handelt, erfordert er eine spezielle Formatierung wie folgt: PWD= *lpszPassword*. Zum Beispiel: ; PWD="Glücklich". (Das führende Semikolon ist erforderlich.)

*lpszLocale*<br/>
Ein Zeichenfolgenausdruck, der verwendet wird, um die Sortierungsreihenfolge zum Erstellen von *lpszDestName*anzugeben. Wenn Sie dieses Argument weglassen, `dbLangGeneral` indem Sie den Standardwert von (siehe unten) akzeptieren, entspricht das Gebietsschema der neuen Datenbank dem der alten Datenbank. Mögliche Werte:

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

*nOptionen*<br/>
Gibt eine oder mehrere Optionen für die *Zieldatenbank, lpszDestName*, an. Wenn Sie dieses Argument weglassen, indem Sie den Standardwert akzeptieren, hat der *lpszDestName* dieselbe Verschlüsselung und dieselbe Version wie *lpszSrcName*. Sie können `dbEncrypt` die `dbDecrypt` oder Option mit einer der Versionsoptionen mit dem Bitwise-OR-Operator kombinieren. Mögliche Werte, die ein Datenbankformat und keine Datenbankmodulversion angeben, sind:

- `dbEncrypt`Verschlüsseln Sie die Datenbank beim Komprimieren.

- `dbDecrypt`Entschlüsseln Sie die Datenbank beim Komprimieren.

- `dbVersion10`Erstellen Sie eine Datenbank, die das Microsoft Jet-Datenbankmodul Version 1.0 verwendet, während Sie die Komprimierung verwenden.

- `dbVersion11`Erstellen Sie eine Datenbank, die das Microsoft Jet-Datenbankmodul Version 1.1 verwendet, während Sie die Komprimierung verwenden.

- `dbVersion20`Erstellen Sie eine Datenbank, die das Microsoft Jet-Datenbankmodul Version 2.0 verwendet, während Sie die Komprimierung verwenden.

- `dbVersion30`Erstellen Sie eine Datenbank, die die Microsoft Jet-Datenbankmodulversion 3.0 verwendet, während Sie die Komprimierung verwenden.

Sie können `dbEncrypt` `dbDecrypt` die Datenbank beim Komprimieren verwenden oder im Argument options angeben, ob die Datenbank verschlüsselt oder entschlüsselt werden soll. Wenn Sie eine Verschlüsselungskonstante weglassen `dbDecrypt` `dbEncrypt`oder wenn Sie sowohl als auch einschließen, hat *lpszDestName* dieselbe Verschlüsselung wie *lpszSrcName*. Sie können eine der Versionskonstanten im Optionsargument verwenden, um die Version des Datenformats für die komprimierte Datenbank anzugeben. Diese Konstante wirkt sich nur auf die Version des Datenformats von *lpszDestName*aus. Sie können nur eine Versionskonstante angeben. Wenn Sie eine Versionskonstante weglassen, hat *lpszDestName* dieselbe Version wie *lpszSrcName*. Sie können *lpszDestName* nur auf eine Version komprimieren, die die gleiche oder spätere Version als die von *lpszSrcName*ist.

> [!CAUTION]
> Wenn eine Datenbank nicht verschlüsselt ist, ist es möglich, auch wenn Sie Benutzer-/Kennwortsicherheit implementieren, die Binärdatenträgerdatei, aus der die Datenbank besteht, direkt zu lesen.

### <a name="remarks"></a>Bemerkungen

Wenn Sie Daten in einer Datenbank ändern, kann die Datenbankdatei fragmentiert werden und mehr Speicherplatz als erforderlich verbrauchen. In regelmäßigen Abständen sollten Sie die Datenbank komprimieren, um die Datenbankdatei zu defragmentieren. Die komprimierte Datenbank ist in der Regel kleiner. Sie können auch die Sortierreihenfolge, die Verschlüsselung oder die Version des Datenformats ändern, während Sie die Datenbank kopieren und komprimieren.

> [!CAUTION]
> Die `CompactDatabase` Memberfunktion konvertiert eine vollständige Microsoft Access-Datenbank nicht ordnungsgemäß von einer Version in eine andere. Nur das Datenformat wird konvertiert. Mit Microsoft Access definierte Objekte, z. B. Formulare und Berichte, werden nicht konvertiert. Die Daten werden jedoch korrekt konvertiert.

> [!TIP]
> Sie können `CompactDatabase` auch zum Kopieren einer Datenbankdatei verwenden.

Weitere Informationen zum Komprimieren von Datenbanken finden Sie im Thema "CompactDatabase-Methode" in der DAO-Hilfe.

## <a name="cdaoworkspacecreate"></a><a name="create"></a>CDaoWorkspace::Erstellen

Rufen Sie diese Memberfunktion auf, um ein neues DAO-Arbeitsbereichsobjekt zu erstellen und es dem MFC-Objekt `CDaoWorkspace` zuzuordnen.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszUserName,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
Eine Zeichenfolge mit bis zu 14 Zeichen, die das neue Arbeitsbereichsobjekt eindeutig benennt. Sie müssen einen Namen angeben. Weitere Informationen finden Sie im Thema "Name-Eigenschaft" in der DAO-Hilfe.

*lpszUserName*<br/>
Der Benutzername des Besitzers des Arbeitsbereichs. Informationen zu Anforderungen finden Sie im Parameter *lpszDefaultUser* in der [SetDefaultUser-Memberfunktion.](#setdefaultuser) Weitere Informationen finden Sie im Thema "UserName-Eigenschaft" in der DAO-Hilfe.

*lpszPasswort*<br/>
Das Kennwort für das neue Arbeitsbereichsobjekt. Ein Kennwort kann bis zu 14 Zeichen lang sein und ein beliebiges Zeichen außer ASCII 0 (null) enthalten. Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden. Weitere Informationen finden Sie im Thema "Kennworteigenschaft" in der DAO-Hilfe.

### <a name="remarks"></a>Bemerkungen

Der gesamte Erstellungsprozess ist:

1. Erstellen Sie ein [CDaoWorkspace-Objekt.](#cdaoworkspace)

1. Rufen Sie die `Create` Memberfunktion des Objekts auf, um den zugrunde liegenden DAO-Arbeitsbereich zu erstellen. Sie müssen einen Arbeitsbereichsnamen angeben.

1. Rufen Sie optional [Append](#append) auf, wenn Sie den Arbeitsbereich der Workspaces-Auflistung des Datenbankmoduls hinzufügen möchten. Sie können mit dem Arbeitsbereich arbeiten, ohne ihn anzuhängen.

Nach `Create` dem Aufruf befindet sich das Arbeitsbereichsobjekt in einem offenen Zustand, der einsatzbereit ist. Sie rufen `Open` nicht `Create`nach an. Sie rufen `Create` nicht auf, wenn der Arbeitsbereich bereits in der Workspaces-Auflistung vorhanden ist. `Create`initialisiert das Datenbankmodul, wenn es noch nicht für Ihre Anwendung initialisiert wurde.

## <a name="cdaoworkspacegetdatabasecount"></a><a name="getdatabasecount"></a>CDaoWorkspace::GetDatabaseCount

Rufen Sie diese Memberfunktion auf, um die Anzahl der DAO-Datenbankobjekte in der Datenbanksammlung des Arbeitsbereichs abzurufen – die Anzahl der geöffneten Datenbanken im Arbeitsbereich.

```
short GetDatabaseCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der geöffneten Datenbanken im Arbeitsbereich.

### <a name="remarks"></a>Bemerkungen

`GetDatabaseCount`ist nützlich, wenn Sie alle definierten Datenbanken in der Datenbanksammlung des Arbeitsbereichs durchlaufen müssen. Informationen zu einer bestimmten Datenbank in der Auflistung finden Sie unter [GetDatabaseInfo](#getdatabaseinfo). Typische Verwendung besteht `GetDatabaseCount` darin, die Anzahl der geöffneten Datenbanken aufzurufen und `GetDatabaseInfo`diese Nummer dann als Schleifenindex für wiederholte Aufrufe von zu verwenden.

## <a name="cdaoworkspacegetdatabaseinfo"></a><a name="getdatabaseinfo"></a>CDaoWorkspace::GetDatabaseInfo

Rufen Sie diese Memberfunktion auf, um verschiedene Arten von Informationen über eine im Arbeitsbereich geöffnete Datenbank abzurufen.

```
void GetDatabaseInfo(
    int nIndex,
    CDaoDatabaseInfo& dbinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetDatabaseInfo(
    LPCTSTR lpszName,
    CDaoDatabaseInfo& dbinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der nullbasierte Index des Datenbankobjekts in der Datenbankauflistung des Arbeitsbereichs für die Suche nach Index.

*dbinfo*<br/>
Ein Verweis auf ein [CDaoDatabaseInfo-Objekt,](../../mfc/reference/cdaodatabaseinfo-structure.md) das die angeforderten Informationen zurückgibt.

*dwInfoOptionen*<br/>
Optionen, die angeben, welche Informationen über die abzurufende Datenbank abgerufen werden sollen. Die verfügbaren Optionen sind hier zusammen mit dem, was die Funktion zurückgeben lässt aufgeführt:

- AFX_DAO_PRIMARY_INFO (Standard)-Name, Updatable, Transaktionen

- AFX_DAO_SECONDARY_INFO Primärinformationen plus: Version, Sortierreihenfolge, Abfragetimeout

- AFX_DAO_ALL_INFO Primär- und Sekundärinformationen plus: Verbinden

*lpszName*<br/>
Der Name des Datenbankobjekts für die Suche nach Namen. Der Name ist eine Zeichenfolge mit bis zu 14 Zeichen, die das neue Arbeitsbereichsobjekt eindeutig benennt.

### <a name="remarks"></a>Bemerkungen

Mit einer Version der Funktion können Sie eine Datenbank nach Index suchen. Mit der anderen Version können Sie eine Datenbank nach Namen suchen.

Eine Beschreibung der in *dbinfo*zurückgegebenen Informationen finden Sie in der [CDaoDatabaseInfo-Struktur.](../../mfc/reference/cdaodatabaseinfo-structure.md) Diese Struktur verfügt über Member, die den oben aufgeführten Informationen in der Beschreibung von *dwInfoOptions*entsprechen. Wenn Sie Informationen auf einer Ebene anfordern, erhalten Sie auch Informationen für alle vorherigen Ebenen.

## <a name="cdaoworkspacegetinipath"></a><a name="getinipath"></a>CDaoWorkspace::GetIniPath

Rufen Sie diese Memberfunktion auf, um den Speicherort der Initialisierungseinstellungen des Microsoft Jet-Datenbankmoduls in der Windows-Registrierung abzurufen.

```
static CString PASCAL GetIniPath();
```

### <a name="return-value"></a>Rückgabewert

Ein [CString,](../../atl-mfc-shared/reference/cstringt-class.md) der den Registrierungsspeicherort enthält.

### <a name="remarks"></a>Bemerkungen

Sie können den Speicherort verwenden, um Informationen zu den Einstellungen für das Datenbankmodul zu erhalten. Die zurückgegebenen Informationen sind eigentlich der Name eines Registrierungsunterschlüssels.

Weitere Informationen finden Sie in den Themen "IniPath-Eigenschaft" und "Anpassen der Windows-Registrierungseinstellungen für den Datenzugriff" in der DAO-Hilfe.

## <a name="cdaoworkspacegetisolateodbctrans"></a><a name="getisolateodbctrans"></a>CDaoWorkspace::GetIsolateODBCTrans

Rufen Sie diese Memberfunktion auf, um den aktuellen Wert der DAO IsolateODBCTrans-Eigenschaft für den Arbeitsbereich abzurufen.

```
BOOL GetIsolateODBCTrans();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn ODBC-Transaktionen isoliert sind; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

In einigen Situationen müssen möglicherweise mehrere gleichzeitige Transaktionen für dieselbe ODBC-Datenbank ausstehen. Dazu müssen Sie für jede Transaktion einen separaten Arbeitsbereich öffnen. Beachten Sie, dass jeder Arbeitsbereich zwar über eine eigene ODBC-Verbindung mit der Datenbank verfügen kann, dies jedoch die Systemleistung verlangsamt. Da normalerweise keine Transaktionsisolation erforderlich ist, werden ODBC-Verbindungen von mehreren Arbeitsbereichsobjekten, die vom gleichen Benutzer geöffnet werden, standardmäßig gemeinsam genutzt.

Einige ODBC-Server, z. B. Microsoft SQL Server, lassen keine gleichzeitigen Transaktionen auf einer einzelnen Verbindung zu. Wenn für eine solche Datenbank jeweils mehr als eine Transaktion ausstehen muss, legen Sie die IsolateODBCTrans-Eigenschaft für jeden Arbeitsbereich auf TRUE fest, sobald Sie sie öffnen. Dadurch wird eine separate ODBC-Verbindung für jeden Arbeitsbereich erzwingt.

Weitere Informationen finden Sie im Thema "IsolateODBCTrans-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaoworkspacegetlogintimeout"></a><a name="getlogintimeout"></a>CDaoWorkspace::GetLoginTimeout

Rufen Sie diese Memberfunktion auf, um den aktuellen Wert der DAO LoginTimeout-Eigenschaft für den Arbeitsbereich abzurufen.

```
static short PASCAL GetLoginTimeout();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Sekunden, bevor ein Fehler auftritt, wenn Sie versuchen, sich bei einer ODBC-Datenbank anzumelden.

### <a name="remarks"></a>Bemerkungen

Dieser Wert stellt die Anzahl der Sekunden dar, bevor ein Fehler auftritt, wenn Sie versuchen, sich bei einer ODBC-Datenbank anzumelden. Die Standardeinstellung LoginTimeout beträgt 20 Sekunden. Wenn LoginTimeout auf 0 gesetzt ist, tritt kein Timeout auf, und die Kommunikation mit der Datenquelle reagiert möglicherweise nicht mehr.

Wenn Sie versuchen, sich bei einer ODBC-Datenbank anzumelden, z. B. Microsoft SQL Server, schlägt die Verbindung möglicherweise aufgrund von Netzwerkfehlern oder aufgrund nicht ausgeführter Server fehl. Anstatt auf die standardmäßige Verbindung von 20 Sekunden zu warten, können Sie angeben, wie lange das Datenbankmodul wartet, bevor es einen Fehler auslöst. Die Anmeldung beim Server erfolgt implizit als Teil einer Reihe verschiedener Ereignisse, z. B. beim Ausführen einer Abfrage in einer externen Serverdatenbank.

Weitere Informationen finden Sie im Thema "LoginTimeout-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaoworkspacegetname"></a><a name="getname"></a>CDaoWorkspace::GetName

Rufen Sie diese Memberfunktion auf, um den benutzerdefinierten `CDaoWorkspace` Namen des DAO-Arbeitsbereichsobjekts abzurufen, das dem Objekt zugrunde liegt.

```
CString GetName();
```

### <a name="return-value"></a>Rückgabewert

Ein [CString,](../../atl-mfc-shared/reference/cstringt-class.md) der den benutzerdefinierten Namen des DAO-Arbeitsbereichsobjekts enthält.

### <a name="remarks"></a>Bemerkungen

Der Name ist nützlich für den Zugriff auf das DAO-Arbeitsbereichsobjekt in der Workspaces-Auflistung des Datenbankmoduls nach Namen.

Weitere Informationen finden Sie im Thema "Name-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaoworkspacegetusername"></a><a name="getusername"></a>CDaoWorkspace::GetUserName

Rufen Sie diese Memberfunktion auf, um den Namen des Besitzers des Arbeitsbereichs abzurufen.

```
CString GetUserName();
```

### <a name="return-value"></a>Rückgabewert

Eine [CString,](../../atl-mfc-shared/reference/cstringt-class.md) die den Besitzer des Arbeitsbereichsobjekts darstellt.

### <a name="remarks"></a>Bemerkungen

Um die Berechtigungen für den Arbeitsbereichsbesitzer zu erhalten oder festzulegen, rufen Sie DAO direkt auf, um die Eigenschafteneinstellung Berechtigungen zu überprüfen. Dadurch wird bestimmt, über welche Berechtigungen dieser Benutzer verfügt. Um mit Berechtigungen arbeiten zu können, benötigen Sie ein SYSTEM. MDA-Datei.

Informationen zum direkten Aufruf von DAO finden Sie unter [Technisches Hinweis 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md). Weitere Informationen finden Sie im Thema "UserName-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaoworkspacegetversion"></a><a name="getversion"></a>CDaoWorkspace::GetVersion

Rufen Sie diese Memberfunktion auf, um die Version des verwendeten Microsoft Jet-Datenbankmoduls zu ermitteln.

```
static CString PASCAL GetVersion();
```

### <a name="return-value"></a>Rückgabewert

Ein [CString,](../../atl-mfc-shared/reference/cstringt-class.md) der die Version des Datenbankmoduls angibt, das dem Objekt zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Der zurückgegebene Wert stellt die Versionsnummer in der Form "major.minor" dar. z. B. "3.0". Die Produktversionsnummer (z. B. 3.0) besteht aus der Versionsnummer (3), einem Punkt und der Versionsnummer (0).

Weitere Informationen finden Sie im Thema "Versionseigenschaft" in der DAO-Hilfe.

## <a name="cdaoworkspacegetworkspacecount"></a><a name="getworkspacecount"></a>CDaoWorkspace::GetWorkspaceCount

Rufen Sie diese Memberfunktion auf, um die Anzahl der DAO-Arbeitsbereichsobjekte in der Workspaces-Auflistung des Datenbankmoduls abzurufen.

```
short GetWorkspaceCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der geöffneten Arbeitsbereiche in der Workspaces-Auflistung.

### <a name="remarks"></a>Bemerkungen

Diese Anzahl enthält keine offenen Arbeitsbereiche, die nicht an die Auflistung angehängt sind. `GetWorkspaceCount`ist nützlich, wenn Sie alle definierten Arbeitsbereiche in der Workspaces-Auflistung durchlaufen müssen. Informationen zu einem bestimmten Arbeitsbereich in der Auflistung finden Sie unter [GetWorkspaceInfo](#getworkspaceinfo). Typische Verwendung besteht `GetWorkspaceCount` darin, die Anzahl der geöffneten Arbeitsbereiche aufzurufen und `GetWorkspaceInfo`diese Nummer dann als Schleifenindex für wiederholte Aufrufe von zu verwenden.

## <a name="cdaoworkspacegetworkspaceinfo"></a><a name="getworkspaceinfo"></a>CDaoWorkspace::GetWorkspaceInfo

Rufen Sie diese Memberfunktion auf, um verschiedene Arten von Informationen zu einem in der Sitzung geöffneten Arbeitsbereich abzurufen.

```
void GetWorkspaceInfo(
    int nIndex,
    CDaoWorkspaceInfo& wkspcinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetWorkspaceInfo(
    LPCTSTR lpszName,
    CDaoWorkspaceInfo& wkspcinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der nullbasierte Index des Datenbankobjekts in der Workspaces-Auflistung für die Suche nach Index.

*wkspcinfo*<br/>
Ein Verweis auf ein [CDaoWorkspaceInfo-Objekt,](../../mfc/reference/cdaoworkspaceinfo-structure.md) das die angeforderten Informationen zurückgibt.

*dwInfoOptionen*<br/>
Optionen, die angeben, welche Informationen über den abzurufenden Arbeitsbereich abgerufen werden sollen. Die verfügbaren Optionen sind hier zusammen mit dem, was die Funktion zurückgeben lässt aufgeführt:

- AFX_DAO_PRIMARY_INFO (Standard)-Name

- AFX_DAO_SECONDARY_INFO Primärinformationen plus: Benutzername

- AFX_DAO_ALL_INFO Primär- und Sekundärinformationen plus: ODBCTrans isolieren

*lpszName*<br/>
Der Name des Arbeitsbereichsobjekts für die Suche nach Namen. Der Name ist eine Zeichenfolge mit bis zu 14 Zeichen, die das neue Arbeitsbereichsobjekt eindeutig benennt.

### <a name="remarks"></a>Bemerkungen

Eine Beschreibung der in *wkspcinfo*zurückgegebenen Informationen finden Sie in der [CDaoWorkspaceInfo-Struktur.](../../mfc/reference/cdaoworkspaceinfo-structure.md) Diese Struktur verfügt über Member, die den oben aufgeführten Informationen in der Beschreibung von *dwInfoOptions*entsprechen. Wenn Sie Informationen auf einer Ebene anfordern, erhalten Sie auch Informationen für frühere Ebenen.

## <a name="cdaoworkspaceidle"></a><a name="idle"></a>CDaoWorkspace::Leerlauf

Rufen `Idle` Sie an, um dem Datenbankmodul die Möglichkeit zu geben, Hintergrundaufgaben auszuführen, die aufgrund der intensiven Datenverarbeitung möglicherweise nicht auf dem neuesten Stand sind.

```
static void PASCAL Idle(int nAction = dbFreeLocks);
```

### <a name="parameters"></a>Parameter

*nAction*<br/>
Eine Aktion, die während der Verarbeitung im Leerlauf zu ergreifen ist. Derzeit ist `dbFreeLocks`die einzige gültige Aktion .

### <a name="remarks"></a>Bemerkungen

Dies trifft häufig auf Multiuser-Multitasking-Umgebungen zu, in denen nicht genügend Hintergrundverarbeitungszeit zur Geltung hat, um alle Datensätze in einem Recordset auf dem aktuellen Stand zu halten.

> [!NOTE]
> Ein `Idle` Aufruf ist bei Datenbanken, die mit Version 3.0 des Microsoft Jet-Datenbankmoduls erstellt wurden, nicht erforderlich. Wird `Idle` nur für Datenbanken verwendet, die mit früheren Versionen erstellt wurden.

In der Regel werden Lesesperren entfernt, und Daten in lokalen Recordset-Objekten vom Typ Dynaset werden nur aktualisiert, wenn keine anderen Aktionen (einschließlich Mausbewegungen) ausgeführt werden. Wenn Sie `Idle`regelmäßig aufrufen, haben Sie dem Datenbankmodul Zeit, Hintergrundverarbeitungsaufgaben nachzuholen, indem Sie nicht benötigte Lesesperren freigeben. Die Angabe `dbFreeLocks` der Konstante als Argument verzögert die Verarbeitung, bis alle Lesesperren freigegeben werden.

Diese Memberfunktion ist in Einzelbenutzerumgebungen nur erforderlich, wenn mehrere Instanzen einer Anwendung ausgeführt werden. Die `Idle` Memberfunktion kann die Leistung in einer Mehrbenutzerumgebung erhöhen, da sie das Datenbankmodul zwingt, Daten auf den Datenträger zu löschen, wodurch Sperren für den Arbeitsspeicher freigegeben werden. Sie können Lesesperren auch freigeben, indem Sie Vorgänge zu einem Teil einer Transaktion machen.

Weitere Informationen finden Sie im Thema "Leerlaufmethode" in der DAO-Hilfe.

## <a name="cdaoworkspaceisopen"></a><a name="isopen"></a>CDaoWorkspace::IsOpen

Rufen Sie diese Memberfunktion `CDaoWorkspace` auf, um zu bestimmen, ob das Objekt geöffnet ist, d. h., ob das MFC-Objekt durch einen Aufruf von [Öffnen](#open) oder durch einen Aufruf von [Create](#create)initialisiert wurde.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Workspace-Objekt geöffnet ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie können jede der Memberfunktionen eines Arbeitsbereichs aufrufen, die sich in einem offenen Zustand befindet.

## <a name="cdaoworkspacem_pdaoworkspace"></a><a name="m_pdaoworkspace"></a>CDaoWorkspace::m_pDAOWorkspace

Ein Zeiger auf das zugrunde liegende DAO-Arbeitsbereichsobjekt.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Datenelement, wenn Sie direkten Zugriff auf das zugrunde liegende DAO-Objekt benötigen. Sie können die Schnittstellen des DAO-Objekts über diesen Zeiger aufrufen.

Informationen zum direkten Zugriff auf DAO-Objekte finden Sie unter [Technische Anmerkung 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="cdaoworkspaceopen"></a><a name="open"></a>CDaoWorkspace::Öffnen

Öffnet explizit ein Arbeitsbereichsobjekt, das dem Standardarbeitsbereich von DAO zugeordnet ist.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
Der Name des zu öffnenden DAO-Arbeitsbereichsobjekts – eine Zeichenfolge mit bis zu 14 Zeichen, die den Arbeitsbereich eindeutig benennt. Akzeptieren Sie den Standardwert NULL, um den Standardarbeitsbereich explizit zu öffnen. Benennensanforderungen finden Sie im Parameter *lpszName* für [Erstellen](#create). Weitere Informationen finden Sie im Thema "Name-Eigenschaft" in der DAO-Hilfe.

### <a name="remarks"></a>Bemerkungen

Rufen Sie `CDaoWorkspace` nach dem Erstellen eines Objekts diese Memberfunktion auf, um eine der folgenden Optionen zu ausführen:

- Öffnen Sie den Standardarbeitsbereich explizit. Übergeben Sie NULL für *lpszName*.

- Öffnen Sie `CDaoWorkspace` ein vorhandenes Objekt, ein Mitglied der Workspaces-Auflistung, nach Namen. Übergeben Sie einen gültigen Namen für ein vorhandenes Arbeitsbereichsobjekt.

`Open`versetzt das Workspace-Objekt in einen offenen Zustand und initialisiert auch das Datenbankmodul, wenn es noch nicht für Ihre Anwendung initialisiert wurde.

Obwohl `CDaoWorkspace` viele Memberfunktionen erst aufgerufen werden können, nachdem der Arbeitsbereich geöffnet wurde, stehen die folgenden Memberfunktionen, die auf dem `Open`Datenbankmodul ausgeführt werden, nach dem Erstellen des C++-Objekts, jedoch vor einem Aufruf von:

||||
|-|-|-|
|[Erstellen](#create)|[Getversion](#getversion)|[SetDefaultUser](#setdefaultuser)|
|[GetIniPath](#getinipath)|[Idle](#idle)|[SetIniPath](#setinipath)|
|[GetLoginTimeout](#getlogintimeout)|[SetDefaultPassword](#setdefaultpassword)|[SetLoginTimeout](#setlogintimeout)|

## <a name="cdaoworkspacerepairdatabase"></a><a name="repairdatabase"></a>CDaoWorkspace::RepairDatabase

Rufen Sie diese Memberfunktion auf, wenn Sie versuchen müssen, eine beschädigte Datenbank zu reparieren, die auf das Microsoft Jet-Datenbankmodul zugreift.

```
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
Der Pfad und der Dateiname für eine vorhandene Microsoft Jet-Engine-Moduldatenbankdatei. Wenn Sie den Pfad weglassen, wird nur das aktuelle Verzeichnis durchsucht. Wenn Ihr System die einheitliche Benennungskonvention (UNC) unterstützt, können\\\\\\Sie auch\\einen\\Netzwerkpfad\\angeben, z. B.: " "MYSERVER "MYSHARE " MYDIR " MYDIR " MYDB " MYDB. MDB". (Doppelte umgekehrte Schrägstriche sind in\\der Pfadzeichenfolge erforderlich, da " " das C++-Escapezeichen ist.)

### <a name="remarks"></a>Bemerkungen

Sie müssen die von *lpszName* angegebene Datenbank schließen, bevor Sie sie reparieren. In einer Mehrbenutzerumgebung können andere Benutzer *lpszName* nicht öffnen, während Sie es reparieren. Wenn *lpszName* nicht geschlossen ist oder nicht exklusiv verwendet werden kann, tritt ein Fehler auf.

Diese Memberfunktion versucht, eine Datenbank zu reparieren, die durch einen unvollständigen Schreibvorgang möglicherweise als beschädigt markiert wurde. Dies kann auftreten, wenn eine Anwendung, die das Microsoft Jet-Datenbankmodul verwendet, aufgrund eines Stromausfalls oder eines Computerhardwareproblems unerwartet geschlossen wird. Wenn Sie den Vorgang abschließen und die [Memberfunktion Schließen](../../mfc/reference/cdaodatabase-class.md#close) aufrufen oder die Anwendung auf übliche Weise beenden, wird die Datenbank nicht als möglicherweise beschädigt markiert.

> [!NOTE]
> Nach dem Reparieren einer Datenbank ist es auch eine gute Idee, sie mithilfe der [CompactDatabase-Memberfunktion](#compactdatabase) zu komprimieren, um die Datei zu defragmentieren und Speicherplatz wiederherzustellen.

Weitere Informationen zum Reparieren von Datenbanken finden Sie im Thema "RepairDatabase-Methode" in der DAO-Hilfe.

## <a name="cdaoworkspacerollback"></a><a name="rollback"></a>CDaoWorkspace::Rollback

Rufen Sie diese Memberfunktion auf, um die aktuelle Transaktion zu beenden und alle Datenbanken im Arbeitsbereich in ihren Zustand zu versetzen, bevor die Transaktion gestartet wurde.

```
void Rollback();
```

### <a name="remarks"></a>Bemerkungen

> [!CAUTION]
> Innerhalb eines Arbeitsbereichsobjekts sind Transaktionen immer global für den Arbeitsbereich und nicht auf eine Datenbank oder ein Recordset beschränkt. Wenn Sie Vorgänge für mehr als eine Datenbank oder `Rollback` ein Recordset innerhalb einer Arbeitsbereichstransaktion ausführen, werden alle Vorgänge für alle diese Datenbanken und Recordsets wiederhergestellt.

Wenn Sie ein Arbeitsbereichsobjekt schließen, ohne ausstehende Transaktionen zu speichern oder zurückzufahren, werden die Transaktionen automatisch zurückgesetzt. Wenn Sie [CommitTrans](#committrans) aufrufen oder `Rollback` ohne zuerst [BeginTrans](#begintrans)aufrufen, tritt ein Fehler auf.

> [!NOTE]
> Wenn Sie eine Transaktion beginnen, zeichnet das Datenbankmodul seine Vorgänge in einer Datei auf, die in dem Verzeichnis gespeichert ist, das von der Temp-Umgebungsvariablen auf der Arbeitsstation angegeben wird. Wenn die Transaktionsprotokolldatei den verfügbaren Speicher auf Ihrem TEMP-Laufwerk ausschöpft, bewirkt das Datenbankmodul, dass MFC einen `CDaoException` (DAO-Fehler 2004) auslöst. Wenn Sie aufrufen, `CommitTrans`wird eine unbestimmte Anzahl von Vorgängen festgeschrieben, aber die verbleibenden nicht abgeschlossenen Vorgänge gehen verloren, und der Vorgang muss neu gestartet werden. Durch `Rollback` Aufrufen wird das Transaktionsprotokoll freigegeben und alle Vorgänge in der Transaktion zurückgesetzt.

## <a name="cdaoworkspacesetdefaultpassword"></a><a name="setdefaultpassword"></a>CDaoWorkspace::SetDefaultPassword

Rufen Sie diese Memberfunktion auf, um das Standardkennwort festzulegen, das das Datenbankmodul verwendet, wenn ein Arbeitsbereichsobjekt ohne ein bestimmtes Kennwort erstellt wird.

```
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parameter

*lpszPasswort*<br/>
Das Standardkennwort. Ein Kennwort kann bis zu 14 Zeichen lang sein und ein beliebiges Zeichen außer ASCII 0 (null) enthalten. Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden.

### <a name="remarks"></a>Bemerkungen

Das von Ihnen festgelegte Standardkennwort gilt für neue Arbeitsbereiche, die Sie nach dem Aufruf erstellen. Wenn Sie nachfolgende Arbeitsbereiche erstellen, müssen Sie im [Aufruf erstellen](#create) kein Kennwort angeben.

So verwenden Sie diese Memberfunktion:

1. Erstellen `CDaoWorkspace` Sie ein Objekt, rufen Sie jedoch nicht auf. `Create`

1. Rufen `SetDefaultPassword` Sie SetDefaultUser auf und, wenn Sie möchten, [SetDefaultUser](#setdefaultuser)an.

1. Rufen `Create` Sie dieses Workspace-Objekt oder nachfolgende Objekt auf, ohne ein Kennwort anzugeben.

Standardmäßig ist die DefaultUser-Eigenschaft auf "admin" und die DefaultPassword-Eigenschaft auf eine leere Zeichenfolge ("") festgelegt.

Weitere Informationen zur Sicherheit finden Sie im Thema "Berechtigungseigenschaft" in der DAO-Hilfe. Weitere Informationen finden Sie in den Themen "DefaultPassword-Eigenschaft" und "DefaultUser-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaoworkspacesetdefaultuser"></a><a name="setdefaultuser"></a>CDaoWorkspace::SetDefaultUser

Rufen Sie diese Memberfunktion auf, um den Standardbenutzernamen festzulegen, den das Datenbankmodul verwendet, wenn ein Arbeitsbereichsobjekt ohne einen bestimmten Benutzernamen erstellt wird.

```
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```

### <a name="parameters"></a>Parameter

*lpszDefaultUser*<br/>
Der Standardbenutzername. Ein Benutzername kann 1 - 20 Zeichen lang sein und alphabetische Zeichen, akzentuierte Zeichen, Zahlen, Leerzeichen und Symbole enthalten, \[ \] mit Ausnahme von: " (Anführungszeichen), / (Vorwärtsschrägstrich), (umgekehrter Schrägstrich), (Klammern), : (Kolon), &#124; (Rohr), \< (weniger als Zeichen), > (größer als Zeichen), + (Pluszeichen), = (Gleichheitszeichen), ; (Semikolon), ( Komma), (Fragezeichen), \* (Sternchen), führende Leerzeichen und Steuerzeichen (ASCII 00 bis ASCII 31). Weitere Informationen finden Sie im Thema "UserName-Eigenschaft" in der DAO-Hilfe.

### <a name="remarks"></a>Bemerkungen

Der von Ihnen festgelegte Standardbenutzername gilt für neue Arbeitsbereiche, die Sie nach dem Aufruf erstellen. Wenn Sie nachfolgende Arbeitsbereiche erstellen, müssen Sie im Aufruf [Erstellen](#create) keinen Benutzernamen angeben.

So verwenden Sie diese Memberfunktion:

1. Erstellen `CDaoWorkspace` Sie ein Objekt, rufen Sie jedoch nicht auf. `Create`

1. Rufen `SetDefaultUser` Sie SetDefaultPassword auf und, wenn Sie möchten, [SetDefaultPassword](#setdefaultpassword)an.

1. Rufen `Create` Sie dieses Workspace-Objekt oder nachfolgende Aufforderungen auf, ohne einen Benutzernamen anzugeben.

Standardmäßig ist die DefaultUser-Eigenschaft auf "admin" und die DefaultPassword-Eigenschaft auf eine leere Zeichenfolge ("") festgelegt.

Weitere Informationen finden Sie in den Themen "DefaultUser-Eigenschaft" und "DefaultPassword-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaoworkspacesetinipath"></a><a name="setinipath"></a>CDaoWorkspace::SetIniPath

Rufen Sie diese Memberfunktion auf, um den Speicherort der Windows-Registrierungseinstellungen für das Microsoft Jet-Datenbankmodul anzugeben.

```
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```

### <a name="parameters"></a>Parameter

*lpszRegistrySubkey*<br/>
Eine Zeichenfolge, die den Namen eines Windows-Registrierungsunterschlüssels für den Speicherort der Microsoft Jet-Datenbankmoduleinstellungen oder Parameter enthält, die für installierbare ISAM-Datenbanken erforderlich sind.

### <a name="remarks"></a>Bemerkungen

Rufen `SetIniPath` Sie nur an, wenn Sie spezielle Einstellungen angeben müssen. Weitere Informationen finden Sie im Thema "IniPath-Eigenschaft" in der DAO-Hilfe.

> [!NOTE]
> Rufen `SetIniPath` Sie während der Anwendungsinstallation auf, nicht, wenn die Anwendung ausgeführt wird. `SetIniPath`muss aufgerufen werden, bevor Sie Arbeitsbereiche, Datenbanken oder Recordsets öffnen; Andernfalls löst MFC eine Ausnahme aus.

Mit diesem Mechanismus können Sie das Datenbankmodul mit vom Benutzer bereitgestellten Registrierungseinstellungen konfigurieren. Der Bereich dieses Attributs ist auf Ihre Anwendung beschränkt und kann nicht geändert werden, ohne die Anwendung neu zu starten.

## <a name="cdaoworkspacesetisolateodbctrans"></a><a name="setisolateodbctrans"></a>CDaoWorkspace::SetIsolateODBCTrans

Rufen Sie diese Memberfunktion auf, um den Wert der DAO IsolateODBCTrans-Eigenschaft für den Arbeitsbereich festzulegen.

```
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```

### <a name="parameters"></a>Parameter

*bIsolateODBCTrans*<br/>
Übergeben Sie TRUE, wenn Sie mit der Isolierung von ODBC-Transaktionen beginnen möchten. Übergeben Sie FALSE, wenn Sie die Isolierung von ODBC-Transaktionen beenden möchten.

### <a name="remarks"></a>Bemerkungen

In einigen Situationen müssen möglicherweise mehrere gleichzeitige Transaktionen für dieselbe ODBC-Datenbank ausstehen. Dazu müssen Sie für jede Transaktion einen separaten Arbeitsbereich öffnen. Obwohl jeder Arbeitsbereich über eine eigene ODBC-Verbindung mit der Datenbank verfügen kann, verlangsamt dies die Systemleistung. Da normalerweise keine Transaktionsisolation erforderlich ist, werden ODBC-Verbindungen von mehreren Arbeitsbereichsobjekten, die vom gleichen Benutzer geöffnet werden, standardmäßig gemeinsam genutzt.

Einige ODBC-Server, z. B. Microsoft SQL Server, lassen keine gleichzeitigen Transaktionen auf einer einzelnen Verbindung zu. Wenn für eine solche Datenbank jeweils mehr als eine Transaktion ausstehen muss, legen Sie die IsolateODBCTrans-Eigenschaft für jeden Arbeitsbereich auf TRUE fest, sobald Sie sie öffnen. Dadurch wird eine separate ODBC-Verbindung für jeden Arbeitsbereich erzwingt.

## <a name="cdaoworkspacesetlogintimeout"></a><a name="setlogintimeout"></a>CDaoWorkspace::SetLoginTimeout

Rufen Sie diese Memberfunktion auf, um den Wert der DAO LoginTimeout-Eigenschaft für den Arbeitsbereich festzulegen.

```
static void PASCAL SetLoginTimeout(short nSeconds);
```

### <a name="parameters"></a>Parameter

*nSekunden*<br/>
Die Anzahl der Sekunden, bevor ein Fehler auftritt, wenn Sie versuchen, sich bei einer ODBC-Datenbank anzumelden.

### <a name="remarks"></a>Bemerkungen

Dieser Wert stellt die Anzahl der Sekunden dar, bevor ein Fehler auftritt, wenn Sie versuchen, sich bei einer ODBC-Datenbank anzumelden. Die Standardeinstellung LoginTimeout beträgt 20 Sekunden. Wenn LoginTimeout auf 0 gesetzt ist, tritt kein Timeout auf, und die Kommunikation mit der Datenquelle reagiert möglicherweise nicht mehr.

Wenn Sie versuchen, sich bei einer ODBC-Datenbank anzumelden, z. B. Microsoft SQL Server, schlägt die Verbindung möglicherweise aufgrund von Netzwerkfehlern oder aufgrund nicht ausgeführter Server fehl. Anstatt auf die standardmäßige Verbindung von 20 Sekunden zu warten, können Sie angeben, wie lange das Datenbankmodul wartet, bevor es einen Fehler auslöst. Die Anmeldung am Server erfolgt implizit als Teil einer Reihe verschiedener Ereignisse, z. B. beim Ausführen einer Abfrage in einer externen Serverdatenbank. Der Timeoutwert wird durch die aktuelle Einstellung der LoginTimeout-Eigenschaft bestimmt.

Weitere Informationen finden Sie im Thema "LoginTimeout-Eigenschaft" in der DAO-Hilfe.

## <a name="see-also"></a>Siehe auch

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase-Klasse](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset-Klasse](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef-Klasse](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef-Klasse](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoException-Klasse](../../mfc/reference/cdaoexception-class.md)
