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
ms.openlocfilehash: eea3fb29f219890ebe596c5d8109257e9d422054
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839789"
---
# <a name="cdaoworkspace-class"></a>CDaoWorkspace-Klasse

Verwaltet eine benannte, kennwortgeschützte Datenbanksitzung eines einzelnen Benutzers von der Anmeldung bis zu Abmeldung. DAO wird über Office 2013 unterstützt. DAO 3,6 ist die endgültige Version, die als veraltet eingestuft wird.

## <a name="syntax"></a>Syntax

```
class CDaoWorkspace : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|[CDaoWorkspace:: CDaoWorkspace](#cdaoworkspace)|Erstellt ein Arbeitsbereichs Objekt. Anschließend wird `Create` oder aufgerufen `Open` .|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[CDaoWorkspace:: Append](#append)|Fügt einen neu erstellten Arbeitsbereich an die Arbeitsbereichs Sammlung der Datenbank-Engine an.|
|[CDaoWorkspace:: BeginTrans](#begintrans)|Startet eine neue Transaktion, die für alle Datenbanken gilt, die im Arbeitsbereich geöffnet sind.|
|[CDaoWorkspace:: Close](#close)|Schließt den Arbeitsbereich und alle darin enthaltenen-Objekte. Für ausstehende Transaktionen wird ein Rollback ausgeführt.|
|[CDaoWorkspace:: CommitTrans](#committrans)|Schließt die aktuelle Transaktion ab und speichert die Änderungen.|
|[CDaoWorkspace:: CompactDatabase](#compactdatabase)|Komprimiert (oder dupliziert) eine Datenbank.|
|[CDaoWorkspace:: Create](#create)|Erstellt ein neues DAO-Arbeitsbereichs Objekt.|
|[CDaoWorkspace:: getdatabasecount](#getdatabasecount)|Gibt die Anzahl der DAO-Datenbankobjekte in der Datenbanksammlung des Arbeitsbereichs zurück.|
|[CDaoWorkspace:: getdatabaseingefo](#getdatabaseinfo)|Gibt Informationen zu einer angegebenen DAO-Datenbank zurück, die in der Datenbanksammlung des Arbeitsbereichs definiert ist.|
|[CDaoWorkspace:: getinipath](#getinipath)|Gibt den Speicherort der Initialisierungs Einstellungen der Microsoft Jet-Datenbank-Engine in der Windows-Registrierung zurück.|
|[CDaoWorkspace:: getisolateodbctrans](#getisolateodbctrans)|Gibt einen Wert zurück, der angibt, ob mehrere Transaktionen, die dieselbe ODBC-Datenquelle einbeziehen, durch erzwungene mehrfache Verbindungen mit der Datenquelle isoliert sind.|
|[CDaoWorkspace:: GetLoginTimeout](#getlogintimeout)|Gibt die Anzahl von Sekunden zurück, bevor ein Fehler auftritt, wenn der Benutzer versucht, sich bei einer ODBC-Datenbank anzumelden.|
|[CDaoWorkspace:: GetName](#getname)|Gibt den benutzerdefinierten Namen für das Arbeitsbereichs Objekt zurück.|
|[CDaoWorkspace:: GetUserName](#getusername)|Gibt den Benutzernamen zurück, der beim Erstellen des Arbeitsbereichs angegeben wurde. Dies ist der Name des Arbeitsbereichs Besitzers.|
|[CDaoWorkspace:: GetVersion](#getversion)|Gibt eine Zeichenfolge zurück, die die Version der Datenbank-Engine enthält, die dem Arbeitsbereich zugeordnet ist.|
|[CDaoWorkspace:: getworkspacecount](#getworkspacecount)|Gibt die Anzahl der DAO-Arbeitsbereichs Objekte in der Arbeitsbereichs Sammlung der Datenbank-Engine zurück.|
|[CDaoWorkspace:: getworkspaceingefo](#getworkspaceinfo)|Gibt Informationen zu einem angegebenen DAO-Arbeitsbereich zurück, der in der Arbeitsbereichs Sammlung der Datenbank-Engine definiert ist.|
|[CDaoWorkspace:: Leerlauf](#idle)|Ermöglicht der Datenbank-Engine das Ausführen von Hintergrundaufgaben.|
|[CDaoWorkspace:: IsOpen](#isopen)|Gibt einen Wert ungleich 0 zurück, wenn der Arbeitsbereich geöffnet ist.|
|[CDaoWorkspace:: Open](#open)|Öffnet explizit ein Arbeitsbereichs Objekt, das mit dem Standard Arbeitsbereich von DAO verknüpft ist.|
|[CDaoWorkspace:: repairren Database](#repairdatabase)|Versucht, eine beschädigte Datenbank zu reparieren.|
|[CDaoWorkspace:: Rollback](#rollback)|Beendet die aktuelle Transaktion und speichert die Änderungen nicht.|
|[CDaoWorkspace:: SetDefaultPassword](#setdefaultpassword)|Legt das Kennwort fest, das von der Datenbank-Engine verwendet wird, wenn ein Arbeitsbereichs Objekt ohne bestimmtes Kennwort erstellt wird.|
|[CDaoWorkspace:: setdefaultuser](#setdefaultuser)|Legt den Benutzernamen fest, den die Datenbank-Engine verwendet, wenn ein Arbeitsbereichs Objekt ohne einen bestimmten Benutzernamen erstellt wird.|
|[CDaoWorkspace:: setinipath](#setinipath)|Legt den Speicherort der Initialisierungs Einstellungen der Microsoft Jet-Datenbank-Engine in der Windows-Registrierung fest.|
|[CDaoWorkspace:: "abtisolateodbctrans"](#setisolateodbctrans)|Gibt an, ob mehrere Transaktionen, die dieselbe ODBC-Datenquelle einbeziehen, durch erzwingen mehrerer Verbindungen mit der Datenquelle isoliert werden.|
|[CDaoWorkspace:: setLoginTimeout](#setlogintimeout)|Legt die Anzahl von Sekunden fest, bevor ein Fehler auftritt, wenn der Benutzer versucht, sich bei einer ODBC-Datenquelle anzumelden.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|Beschreibung|
|----------|-----------------|
|[CDaoWorkspace:: m_pDAOWorkspace](#m_pdaoworkspace)|Verweist auf das zugrunde liegende DAO-Arbeitsbereichs Objekt.|

## <a name="remarks"></a>Bemerkungen

In den meisten Fällen benötigen Sie nicht mehrere Arbeitsbereiche, und Sie müssen keine expliziten Arbeitsbereichs Objekte erstellen. Wenn Sie Datenbank-und Recordset-Objekte öffnen, wird der Standard Arbeitsbereich von DAO verwendet. Allerdings können Sie bei Bedarf mehrere Sitzungen gleichzeitig ausführen, indem Sie zusätzliche Arbeitsbereichs Objekte erstellen. Jedes Arbeitsbereichs Objekt kann mehrere geöffnete Datenbankobjekte in der eigenen Datenbanksammlung enthalten. In MFC ist ein Arbeitsbereich primär ein Transaktions-Manager, der einen Satz offener Datenbanken im gleichen "Transaktions Bereich" angibt.

> [!NOTE]
> Die DAO-Datenbankklassen unterscheiden sich von den MFC-Datenbankklassen, die auf Open Database Connectivity (ODBC) basieren. Alle DAO-Datenbankklassen Namen haben ein "CDAO"-Präfix. Im Allgemeinen sind die MFC-Klassen, die auf DAO basieren, besser geeignet als die MFC-Klassen auf der Grundlage von ODBC. Die DAO-basierten Klassen greifen auf Daten über die Microsoft Jet-Datenbank-Engine zu, einschließlich ODBC-Treibern. Außerdem unterstützen Sie DDL-Vorgänge (Data Definition Language), wie z. b. das Erstellen von Datenbanken und das Hinzufügen von Tabellen und Feldern über die Klassen, ohne DAO direkt aufrufen zu müssen.

## <a name="capabilities"></a>Funktionen

Die-Klasse `CDaoWorkspace` stellt Folgendes bereit:

- Expliziter Zugriff auf einen Standard Arbeitsbereich, der durch Initialisieren der Datenbank-Engine erstellt wurde. Normalerweise verwenden Sie den Standard Arbeitsbereich von DAO implizit, indem Sie Datenbank-und Recordset-Objekte erstellen.

- Ein Transaktions Bereich, in dem Transaktionen für alle Datenbanken gelten, die im Arbeitsbereich geöffnet sind. Sie können zusätzliche Arbeitsbereiche erstellen, um separate Transaktions Bereiche zu verwalten.

- Eine Schnittstelle zu vielen Eigenschaften der zugrunde liegenden Microsoft Jet-Datenbank-Engine (siehe statische Member-Funktionen). Wenn Sie einen Arbeitsbereich öffnen oder erstellen oder eine statische Element Funktion vor dem Öffnen oder erstellen aufrufen, wird die Datenbank-Engine initialisiert.

- Zugriff auf die Arbeitsbereichs Sammlung der Datenbank-Engine, in der alle aktiven Arbeitsbereiche gespeichert werden, die an die Datenbank angefügt wurden. Sie können Arbeitsbereiche auch erstellen und bearbeiten, ohne Sie an die Sammlung anzufügen.

## <a name="security"></a>Sicherheit

MFC implementiert die Benutzer-und Gruppen Sammlungen in DAO nicht, die für die Sicherheitssteuerung verwendet werden. Wenn Sie diese Aspekte von DAO benötigen, müssen Sie Sie selbst über direkte Aufrufe der DAO-Schnittstellen programmieren. Weitere Informationen finden [Sie im technischen Hinweis 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="usage"></a>Verwendung

Sie können die-Klasse für Folgendes verwenden `CDaoWorkspace` :

- Öffnen Sie explizit den Standard Arbeitsbereich.

   Normalerweise ist die Verwendung des Standard Arbeitsbereichs implizit – Wenn Sie neue [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) -oder [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) -Objekte öffnen. Sie müssen jedoch möglicherweise explizit darauf zugreifen – beispielsweise für den Zugriff auf Datenbankmodul Eigenschaften oder die Arbeitsbereichs Sammlung. Siehe "implizite Verwendung des Standard Arbeitsbereichs" weiter unten.

- Erstellen Sie neue Arbeitsbereiche. Rufen Sie [Append](#append) auf, wenn Sie Sie der Workspaces-Auflistung hinzufügen möchten.

- Öffnen Sie einen vorhandenen Arbeitsbereich in der Sammlung "Arbeitsbereiche".

Das Erstellen eines neuen Arbeitsbereichs, der nicht bereits in der Arbeitsbereichs Sammlung vorhanden ist, wird unter der [Create](#create) Member-Funktion beschrieben. Arbeitsbereichobjekte werden zwischen den Sitzungen der Banken-Engine nicht beibehalten. Wenn Ihre Anwendung MFC statisch verknüpft, wird durch das Beenden der Anwendung die Datenbank-Engine nicht mehr initialisiert. Wenn die Anwendung dynamisch mit MFC verknüpft ist, wird die Datenbank-Engine nicht initialisiert, wenn die MFC-DLL entladen wird.

Wenn Sie den Standard Arbeitsbereich explizit öffnen oder einen vorhandenen Arbeitsbereich in der Sammlung "Arbeitsbereiche" öffnen, wird unter der Funktion " [Open](#open) Member" beschrieben.

Beenden Sie eine Arbeitsbereichs Sitzung, indem Sie den Arbeitsbereich mit der [Close](#close) Member-Funktion schließen. `Close` schließt alle Datenbanken, die Sie zuvor nicht geschlossen haben, und stellt für Transaktionen ohne Commit ein Rollback durch.

## <a name="transactions"></a>Transaktionen

DAO verwaltet Transaktionen auf der Arbeitsbereichs Ebene. Daher gelten Transaktionen in einem Arbeitsbereich mit mehreren geöffneten Datenbanken für alle Datenbanken. Wenn beispielsweise zwei Datenbanken über nicht ausgeübte Updates verfügen und [CommitTrans](#committrans)aufgerufen wird, wird für alle Updates ein Commit ausgeführt. Wenn Sie Transaktionen auf eine einzelne Datenbank beschränken möchten, benötigen Sie ein separates Arbeitsbereichs Objekt.

## <a name="implicit-use-of-the-default-workspace"></a>Implizite Verwendung des Standard Arbeitsbereichs

MFC verwendet in den folgenden Situationen implizit den Standard Arbeitsbereich von DAO:

- Wenn Sie ein neues `CDaoDatabase` Objekt erstellen, aber nicht über ein vorhandenes `CDaoWorkspace` Objekt, erstellt MFC ein temporäres Arbeitsbereichs Objekt für Sie, das dem Standard Arbeitsbereich von DAO entspricht. Wenn Sie dies für mehrere Datenbanken tun, werden alle Datenbankobjekte dem Standard Arbeitsbereich zugeordnet. Sie können über einen Datenmember auf den Arbeitsbereich einer Datenbank zugreifen `CDaoDatabase` .

- Wenn Sie ein-Objekt erstellen, `CDaoRecordset` ohne einen Zeiger auf ein- `CDaoDatabase` Objekt bereitzustellen, erstellt MFC ein temporäres Datenbankobjekt und durch Erweiterung ein temporäres Arbeitsbereichs Objekt. Sie können über einen Datenmember auf die Datenbank eines Recordsets und indirekt auf den Arbeitsbereich zugreifen `CDaoRecordset` .

## <a name="other-operations"></a>Weitere Vorgänge

Es werden auch andere Daten Bank Vorgänge bereitgestellt, wie z. b. das Reparieren einer beschädigten Datenbank oder das Komprimieren einer Datenbank.

Weitere Informationen zum direkten Aufrufen von DAO und zur DAO-Sicherheit finden [Sie im technischen Hinweis 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CDaoWorkspace`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdao.h

## <a name="cdaoworkspaceappend"></a><a name="append"></a> CDaoWorkspace:: Append

Rufen Sie diese Member-Funktion nach dem aufzurufen von [Create](#create)auf.

```
virtual void Append();
```

### <a name="remarks"></a>Bemerkungen

`Append` Fügt ein neu erstelltes Arbeitsbereichs Objekt an die Arbeitsbereichs Sammlung der Datenbank-Engine an. Arbeitsbereiche bleiben nicht zwischen Datenbank-Engine-Sitzungen erhalten. Sie werden nur im Arbeitsspeicher gespeichert, nicht auf dem Datenträger. Sie müssen keinen Arbeitsbereich anfügen. Andernfalls können Sie Sie weiterhin verwenden.

Ein angefügter Arbeitsbereich bleibt in der Workspaces-Auflistung in einem aktiven, geöffneten Zustand, bis Sie seine [Close](#close) Member-Funktion aufruft.

Weitere Informationen finden Sie im Thema "Append Method" in der DAO-Hilfe.

## <a name="cdaoworkspacebegintrans"></a><a name="begintrans"></a> CDaoWorkspace:: BeginTrans

Mit dieser Member-Funktion können Sie eine Transaktion initiieren.

```cpp
void BeginTrans();
```

### <a name="remarks"></a>Bemerkungen

Nachdem Sie aufgerufen `BeginTrans` haben, werden Updates, die Sie an Ihrer Daten-oder Datenbankstruktur vornehmen, beim commitcommit der Transaktion wirksam. Da der Arbeitsbereich einen einzelnen Transaktions Bereich definiert, gilt die Transaktion für alle geöffneten Datenbanken im Arbeitsbereich. Es gibt zwei Möglichkeiten, die Transaktion abzuschließen:

- Der [CommitTrans](#committrans) -Member wird aufgerufen, um einen Commit für die Transaktion durchzusetzen und die Änderungen an der Datenquelle zu speichern

- Oder rufen Sie die [Rollback](#rollback) -Member-Funktion auf, um die Transaktion abzubrechen.

Das Schließen des Arbeitsbereichs Objekts oder eines Datenbankobjekts während einer ausstehenden Transaktion führt ein Rollback aller ausstehenden Transaktionen aus.

Wenn Sie Transaktionen in einer ODBC-Datenquelle von denen in einer anderen ODBC-Datenquelle isolieren müssen, finden Sie weitere Informationen unter der Member-Funktion von " [c tisolateodbctrans](#setisolateodbctrans) ".

## <a name="cdaoworkspacecdaoworkspace"></a><a name="cdaoworkspace"></a> CDaoWorkspace:: CDaoWorkspace

Erstellt ein `CDaoWorkspace`-Objekt.

```
CDaoWorkspace();
```

### <a name="remarks"></a>Bemerkungen

Nach dem Erstellen des C++-Objekts haben Sie zwei Möglichkeiten:

- Ruft die [Open](#open) Member-Funktion des-Objekts auf, um den Standard Arbeitsbereich zu öffnen oder ein vorhandenes Objekt in der Arbeitsbereichs Auflistung zu öffnen.

- Oder rufen Sie die [Create](#create) Member-Funktion des Objekts auf, um ein neues DAO-Arbeitsbereichs Objekt zu erstellen. Dadurch wird explizit eine neue Arbeitsbereichs Sitzung gestartet, auf die Sie über das-Objekt verweisen können `CDaoWorkspace` . Nachdem Sie aufgerufen `Create` haben, können Sie " [Append](#append) " aufrufen, wenn Sie den Arbeitsbereich der Arbeitsbereichs Sammlung der Datenbank-Engine hinzufügen möchten.

Informationen dazu, wann Sie explizit ein-Objekt erstellen müssen, finden Sie unter Übersicht über [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) in der-Klasse `CDaoWorkspace` . Normalerweise verwenden Sie Arbeitsbereiche, die implizit erstellt werden, wenn Sie ein [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) -Objekt öffnen, ohne einen Arbeitsbereich anzugeben, oder wenn Sie ein [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) -Objekt öffnen, ohne ein Datenbankobjekt anzugeben. Auf diese Weise erstellte MFC-DAO-Objekte verwenden den Standard Arbeitsbereich von DAO, der einmal erstellt und wieder verwendet wird.

Um einen Arbeitsbereich und die darin enthaltenen Objekte freizugeben, müssen Sie die [Close](#close) Member-Funktion des Arbeitsbereichs Objekts anrufen.

## <a name="cdaoworkspaceclose"></a><a name="close"></a> CDaoWorkspace:: Close

Mit dieser Member-Funktion schließen Sie das Arbeitsbereichsobjekt.

```
virtual void Close();
```

### <a name="remarks"></a>Bemerkungen

Durch das Schließen eines geöffneten Arbeitsbereichs Objekts wird das zugrunde liegende DAO-Objekt freigegeben. wenn der Arbeitsbereich ein Member der Arbeitsbereichs Auflistung ist, wird dieser aus der Sammlung entfernt. Das Aufrufen von `Close` ist eine gute Programmier Übung.

> [!CAUTION]
> Durch das Schließen eines Arbeitsbereichs Objekts werden alle geöffneten Datenbanken im Arbeitsbereich geschlossen. Dies führt dazu, dass in den Datenbanken auch beliebige Recordsets geöffnet werden, und alle ausstehenden Änderungen oder Updates werden zurückgesetzt. Weitere Informationen finden Sie in den Element Funktionen [CDaoDatabase:: Close](../../mfc/reference/cdaodatabase-class.md#close), [CDaoRecordset:: Close](../../mfc/reference/cdaorecordset-class.md#close), [CDaoTableDef:: Close](../../mfc/reference/cdaotabledef-class.md#close)und [CDaoQueryDef:: Close](../../mfc/reference/cdaoquerydef-class.md#close) .

Arbeitsbereichobjekte sind nicht permanent. Sie sind nur vorhanden, wenn Verweise auf Sie vorhanden sind. Dies bedeutet, dass beim Beenden der Datenbank-Engine-Sitzung der Arbeitsbereich und die zugehörige Datenbanksammlung nicht beibehalten werden. Sie müssen diese für die nächste Sitzung neu erstellen, indem Sie den Arbeitsbereich und die Datenbank (en) erneut öffnen.

Weitere Informationen finden Sie im Thema "close method" in der DAO-Hilfe.

## <a name="cdaoworkspacecommittrans"></a><a name="committrans"></a> CDaoWorkspace:: CommitTrans

Diese Member-Funktion zum committen einer Transaktion – speichern Sie eine Gruppe von Änderungen und Updates für eine oder mehrere Datenbanken im Arbeitsbereich.

```cpp
void CommitTrans();
```

### <a name="remarks"></a>Bemerkungen

Eine Transaktion besteht aus einer Reihe von Änderungen an den Daten der Datenbank oder ihrer Struktur, beginnend mit einem Aufrufen von [BeginTrans](#begintrans). Wenn Sie die Transaktion abgeschlossen haben, führen Sie entweder einen Commit für die Transaktion durch, oder führen Sie ein [Rollback](#rollback)aus (Abbrechen der Änderungen). Standardmäßig wird für Updates von Datensätzen ohne Transaktionen sofort ein Commit ausgeführt. Das Aufrufen `BeginTrans` von bewirkt, dass die Aktualisierung von Updates verzögert wird, bis Sie aufrufen `CommitTrans` .

> [!CAUTION]
> Innerhalb eines Arbeitsbereichs sind Transaktionen immer global für den Arbeitsbereich, und Sie sind nicht auf eine Datenbank oder ein Recordset beschränkt. Wenn Sie Vorgänge für mehrere Datenbanken oder Recordsets innerhalb einer Arbeitsbereichs Transaktion ausführen, führt einen Commit für `CommitTrans` alle ausstehenden Updates aus und `Rollback` stellt alle Vorgänge für diese Datenbanken und Recordsets wieder her.

Wenn Sie eine Datenbank oder einen Arbeitsbereich mit ausstehenden Transaktionen schließen, wird für die Transaktionen ein Rollback ausgeführt.

> [!NOTE]
> Dies ist kein Zweiphasencommit-Mechanismus. Wenn ein Update nicht ausgeführt werden kann, wird für andere Benutzer weiterhin ein Commit ausgeführt.

## <a name="cdaoworkspacecompactdatabase"></a><a name="compactdatabase"></a> CDaoWorkspace:: CompactDatabase

Diese Member-Funktion zum Komprimieren eines angegebenen Microsoft Jet (. MDB).

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

*lpszsrcname*<br/>
Der Name einer vorhandenen, geschlossenen Datenbank. Dies kann ein vollständiger Pfad und Dateiname sein, z. b. "C: \\ \MyDB. MDB ". Wenn der Dateiname über eine Erweiterung verfügt, müssen Sie diese angeben. Wenn Ihr Netzwerk die Uniform Naming Convention (UNC) unterstützt, können Sie auch einen Netzwerkpfad angeben, z. b. " \\ \\ \\ \meinserver\meinefreigabe \meineverzeichnis \ \\ \\ \\ mydb. MDB ". (Doppelte umgekehrte Schrägstriche sind in den Pfad Zeichenfolgen erforderlich, da " \\ " das Escapezeichen "C++" ist.)

*lpszdestname*<br/>
Der vollständige Pfad der zu erstellenden komprimierte Datenbank. Sie können auch einen Netzwerkpfad wie *lpszsrcname*angeben. Sie können das *lpszdestname* -Argument nicht verwenden, um die gleiche Datenbankdatei wie *lpszsrcname*anzugeben.

*lpszpassword*<br/>
Ein Kennwort, das verwendet wird, wenn Sie eine Kenn Wort geschützte Datenbank komprimieren möchten. Beachten Sie, dass Sie, wenn Sie die-Version von verwenden `CompactDatabase` , die ein Kennwort annimmt, alle Parameter angeben müssen. Da es sich hierbei um einen Connect-Parameter handelt, müssen Sie wie folgt eine spezielle Formatierung ausführen:; Pwd = *lpszpassword*. Beispiel:; Pwd = "Happy". (Das vorangehende Semikolon ist erforderlich.)

*lpszlocale*<br/>
Ein Zeichen folgen Ausdruck, mit dem die Sortierreihenfolge zum Erstellen von *lpszdestname*angegeben wird. Wenn Sie dieses Argument weglassen, indem Sie den Standardwert `dbLangGeneral` (siehe unten) akzeptieren, ist das Gebiets Schema der neuen Datenbank mit dem der alten Datenbank identisch. Mögliche Werte:

- `dbLangGeneral` Englisch, Deutsch, Französisch, Portugiesisch, Italienisch und modern Spanisch

- `dbLangArabic` Arabisch

- `dbLangCyrillic` Russisch

- `dbLangCzech` Tschechisch

- `dbLangDutch` Holländisch

- `dbLangGreek` Griechisch

- `dbLangHebrew` Hebräisch

- `dbLangHungarian` Ungarisch

- `dbLangIcelandic` Isländisch

- `dbLangNordic` Nordische Sprachen (nur Microsoft Jet-Datenbank-Engine, Version 1,0)

- `dbLangNorwdan` Norwegisch und Dänisch

- `dbLangPolish` Polnisch

- `dbLangSpanish` Traditionelles Spanisch

- `dbLangSwedfin` Schwedisch und Finnisch

- `dbLangTurkish` Türkisch

*noptions*<br/>
Gibt eine oder mehrere Optionen für die Zieldatenbank *lpszdestname*an. Wenn Sie dieses Argument weglassen, indem Sie den Standardwert akzeptieren, weist *lpszdestname* dieselbe Verschlüsselung und dieselbe Version wie *lpszsrcname*auf. Sie können die `dbEncrypt` `dbDecrypt` -Option oder die-Option mit einer der Versions Optionen mit dem bitweisen OR-Operator kombinieren. Mögliche Werte, die ein Datenbankformat und keine Datenbank-Engine-Version angeben, sind:

- `dbEncrypt` Verschlüsseln Sie die Datenbank während der Komprimierung.

- `dbDecrypt` Entschlüsseln Sie die Datenbank während der Komprimierung.

- `dbVersion10` Erstellen Sie eine Datenbank, die während der Komprimierung die Microsoft Jet-Datenbank-Engine-Version 1,0 verwendet.

- `dbVersion11` Erstellen Sie eine Datenbank, die während der Komprimierung die Microsoft Jet-Datenbank-Engine-Version 1,1 verwendet.

- `dbVersion20` Erstellen Sie eine Datenbank, die während der Komprimierung die Microsoft Jet-Datenbank-Engine-Version 2,0 verwendet.

- `dbVersion30` Erstellen Sie eine Datenbank, die während der Komprimierung die Microsoft Jet-Datenbank-Engine-Version 3,0 verwendet.

Sie können `dbEncrypt` oder `dbDecrypt` im options-Argument verwenden, um anzugeben, ob die Datenbank verschlüsselt oder entschlüsselt werden soll, wenn Sie komprimiert wird. Wenn Sie eine Verschlüsselungs Konstante weglassen oder wenn Sie sowohl als auch einschließen `dbDecrypt` `dbEncrypt` , weist *lpszdestname* dieselbe Verschlüsselung wie *lpszsrcname*auf. Sie können eine der Versions Konstanten im options-Argument verwenden, um die Version des Datenformats für die komprimierte Datenbank anzugeben. Diese Konstante wirkt sich nur auf die Version des Datenformats von *lpszdestname*aus. Sie können nur eine Versions Konstante angeben. Wenn Sie eine Versions Konstante weglassen, hat *lpszdestname* dieselbe Version wie *lpszsrcname*. Sie können *lpszdestname* nur in eine Version komprimieren, die gleich oder später ist als *lpszsrcname*.

> [!CAUTION]
> Wenn eine Datenbank nicht verschlüsselt ist, ist es möglich, auch wenn Sie die Benutzer-/Kennwort-Sicherheit implementieren, die Binär Datenträgerdatei direkt zu lesen, die die Datenbank darstellt.

### <a name="remarks"></a>Bemerkungen

Wenn Sie Daten in einer Datenbank ändern, kann die Datenbankdatei fragmentiert werden und mehr Speicherplatz als notwendig nutzen. In regelmäßigen Abständen sollten Sie die Datenbank komprimieren, um die Datenbankdatei zu defragmentieren. Die komprimierte Datenbank ist normalerweise kleiner. Sie können auch festlegen, dass die Sortierreihenfolge, die Verschlüsselung oder die Version des Datenformats beim Kopieren und Komprimieren der Datenbank geändert wird.

> [!CAUTION]
> Die `CompactDatabase` Member-Funktion konvertiert eine vollständige Microsoft Access-Datenbank nicht ordnungsgemäß von einer Version in eine andere. Nur das Datenformat wird konvertiert. Von Microsoft Access definierte Objekte, wie z. b. Formulare und Berichte, werden nicht konvertiert. Die Daten werden jedoch ordnungsgemäß konvertiert.

> [!TIP]
> Sie können auch verwenden `CompactDatabase` , um eine Datenbankdatei zu kopieren.

Weitere Informationen zur Komprimierung von Datenbanken finden Sie im Thema "CompactDatabase Method" in der DAO-Hilfe.

## <a name="cdaoworkspacecreate"></a><a name="create"></a> CDaoWorkspace:: Create

Rufen Sie diese Member-Funktion auf, um ein neues DAO-Arbeitsbereichs Objekt zu erstellen und es dem MFC- `CDaoWorkspace` Objekt zuzuordnen.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszUserName,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parameter

*lpszname*<br/>
Eine Zeichenfolge mit bis zu 14 Zeichen, die das neue Arbeitsbereichs Objekt eindeutig benennt. Sie müssen einen Namen angeben. Weitere Informationen finden Sie im Thema "Name Property" in der DAO-Hilfe.

*lpszusername*<br/>
Der Benutzername des Besitzers des Arbeitsbereichs. Informationen zu den Anforderungen finden Sie unter dem *lpszdefaultuser* -Parameter der [setdefaultuser](#setdefaultuser) -Member-Funktion. Weitere Informationen finden Sie im Thema "username Property" in der DAO-Hilfe.

*lpszpassword*<br/>
Das Kennwort für das neue Arbeitsbereichs Objekt. Ein Kennwort kann bis zu 14 Zeichen lang sein und kann ein beliebiges Zeichen mit Ausnahme von ASCII 0 (null) enthalten. Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden. Weitere Informationen finden Sie im Thema "Password Property" in der DAO-Hilfe.

### <a name="remarks"></a>Bemerkungen

Der Gesamt Erstellungs Vorgang lautet:

1. Erstellen Sie ein [CDaoWorkspace](#cdaoworkspace) -Objekt.

1. Rufen Sie die Element `Create` Funktion des Objekts auf, um den zugrunde liegenden DAO-Arbeitsbereich zu erstellen Sie müssen einen Arbeitsbereichs Namen angeben.

1. Rufen Sie optional [Append](#append) auf, wenn Sie den Arbeitsbereich der Arbeitsbereichs Sammlung der Datenbank-Engine hinzufügen möchten. Sie können mit dem Arbeitsbereich arbeiten, ohne ihn Anhängen zu können.

Nach dem-Befehl `Create` befindet sich das Arbeitsbereichs Objekt in einem geöffneten Zustand und kann verwendet werden. Sie werden nicht `Open` nach aufgerufen `Create` . Sie werden nicht aufgerufen, `Create` Wenn der Arbeitsbereich bereits in der Arbeitsbereichs Sammlung vorhanden ist. `Create` Initialisiert die Datenbank-Engine, wenn Sie nicht bereits für die Anwendung initialisiert wurde.

## <a name="cdaoworkspacegetdatabasecount"></a><a name="getdatabasecount"></a> CDaoWorkspace:: getdatabasecount

Rufen Sie diese Member-Funktion auf, um die Anzahl der DAO-Datenbankobjekte in der Datenbanksammlung des Arbeitsbereichs abzurufen – die Anzahl der geöffneten Datenbanken im Arbeitsbereich.

```
short GetDatabaseCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der geöffneten Datenbanken im Arbeitsbereich.

### <a name="remarks"></a>Bemerkungen

`GetDatabaseCount` ist nützlich, wenn Sie alle definierten Datenbanken in der Datenbanksammlung des Arbeitsbereichs durchlaufen müssen. Informationen zu einer bestimmten Datenbank in der Sammlung finden Sie unter [getDatabaseInfo](#getdatabaseinfo). Die typische Verwendung besteht darin, `GetDatabaseCount` die Anzahl der geöffneten Datenbanken aufzurufen und diese Zahl dann als Schleifenindex für wiederholte Aufrufe von zu verwenden `GetDatabaseInfo` .

## <a name="cdaoworkspacegetdatabaseinfo"></a><a name="getdatabaseinfo"></a> CDaoWorkspace:: getdatabaseingefo

Mit dieser Member-Funktion können Sie verschiedene Arten von Informationen zu einer Datenbank abrufen, die im Arbeitsbereich geöffnet ist.

```cpp
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
Der null basierte Index des Datenbankobjekts in der Datenbanksammlung des Arbeitsbereichs für die Suche nach Index.

*dbinfo*<br/>
Ein Verweis auf ein [cdaodatabaseinfo](../../mfc/reference/cdaodatabaseinfo-structure.md) -Objekt, das die angeforderten Informationen zurückgibt.

*dwinfooptions*<br/>
Optionen, die angeben, welche Informationen über die Datenbank abgerufen werden sollen. Die verfügbaren Optionen werden hier zusammen mit den Funktionen aufgelistet, die von der Funktion zurückgegeben werden:

- AFX_DAO_PRIMARY_INFO (Standard) Name, aktualisierbar, Transaktionen

- AFX_DAO_SECONDARY_INFO primäre Informationen Plus: Version, Sortierreihenfolge, Abfrage Timeout

- AFX_DAO_ALL_INFO primäre und sekundäre Informationen Plus: Connect

*lpszname*<br/>
Der Name des Datenbankobjekts für die Suche nach Namen. Der Name ist eine Zeichenfolge mit bis zu 14 Zeichen, die das neue Arbeitsbereichs Objekt eindeutig benennen.

### <a name="remarks"></a>Bemerkungen

Eine Version der-Funktion ermöglicht es Ihnen, eine Datenbank nach Index zu suchen. Mit der anderen Version können Sie eine Datenbank nach Namen suchen.

Eine Beschreibung der Informationen, die in *dbinfo*zurückgegeben werden, finden Sie in der [cdaodatabaseinfo](../../mfc/reference/cdaodatabaseinfo-structure.md) -Struktur. Diese Struktur enthält Member, die den in der Beschreibung von *dwinfooptions*aufgeführten Elementen der oben aufgeführten Informationen entsprechen. Wenn Sie Informationen auf einer Ebene anfordern, erhalten Sie auch Informationen zu allen vorherigen Ebenen.

## <a name="cdaoworkspacegetinipath"></a><a name="getinipath"></a> CDaoWorkspace:: getinipath

Rufen Sie diese Member-Funktion auf, um den Speicherort der Initialisierungs Einstellungen der Microsoft Jet-Datenbank-Engine in der Windows-Registrierung abzurufen.

```
static CString PASCAL GetIniPath();
```

### <a name="return-value"></a>Rückgabewert

Eine [CString](../../atl-mfc-shared/reference/cstringt-class.md) , die den Registrierungs Speicherort enthält.

### <a name="remarks"></a>Bemerkungen

Sie können den Speicherort zum Abrufen von Informationen zu Einstellungen für die Datenbank-Engine verwenden. Die zurückgegebenen Informationen sind tatsächlich der Name eines Registrierungs unter Schlüssels.

Weitere Informationen finden Sie in den Themen "INIPath-Eigenschaft" und "Anpassen von Windows-Registrierungs Einstellungen für den Datenzugriff" in der DAO-Hilfe.

## <a name="cdaoworkspacegetisolateodbctrans"></a><a name="getisolateodbctrans"></a> CDaoWorkspace:: getisolateodbctrans

Mit dieser Member-Funktion können Sie den aktuellen Wert der DAO IsolateODBCTrans-Eigenschaft für den Arbeitsbereich abrufen.

```
BOOL GetIsolateODBCTrans();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn ODBC-Transaktionen isoliert sind. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

In einigen Situationen müssen möglicherweise mehrere gleichzeitige Transaktionen in der gleichen ODBC-Datenbank ausstehen. Zu diesem Zweck müssen Sie für jede Transaktion einen separaten Arbeitsbereich öffnen. Beachten Sie, dass der Arbeitsbereich zwar über eine eigene ODBC-Verbindung mit der Datenbank verfügen kann, dies verlangsamt jedoch die Systemleistung. Da die Transaktions Isolation normalerweise nicht erforderlich ist, werden ODBC-Verbindungen von mehreren Arbeitsbereichs Objekten, die vom gleichen Benutzer geöffnet wurden, standardmäßig freigegeben.

Einige ODBC-Server, wie z. b. Microsoft SQL Server, lassen keine gleichzeitigen Transaktionen auf einer einzelnen Verbindung zu. Wenn Sie mehr als eine Transaktion gleichzeitig für eine solche Datenbank ausstehend benötigen, legen Sie die IsolateODBCTrans-Eigenschaft für jeden Arbeitsbereich auf "true" fest, sobald Sie Sie öffnen. Dies erzwingt eine separate ODBC-Verbindung für jeden Arbeitsbereich.

Weitere Informationen finden Sie im Thema "IsolateODBCTrans Property" in der DAO-Hilfe.

## <a name="cdaoworkspacegetlogintimeout"></a><a name="getlogintimeout"></a> CDaoWorkspace:: GetLoginTimeout

Mit dieser Member-Funktion können Sie den aktuellen Wert der DAO LoginTimeout-Eigenschaft für den Arbeitsbereich abrufen.

```
static short PASCAL GetLoginTimeout();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Sekunden, bevor ein Fehler auftritt, wenn Sie versuchen, sich bei einer ODBC-Datenbank anzumelden.

### <a name="remarks"></a>Bemerkungen

Dieser Wert gibt die Anzahl der Sekunden an, bevor ein Fehler auftritt, wenn Sie versuchen, sich bei einer ODBC-Datenbank anzumelden. Die Standardeinstellung für LoginTimeOut beträgt 20 Sekunden. Wenn LoginTimeout auf 0 festgelegt ist, tritt kein Timeout auf, und die Kommunikation mit der Datenquelle reagiert möglicherweise nicht mehr.

Wenn Sie versuchen, sich bei einer ODBC-Datenbank anzumelden, wie z. b. Microsoft SQL Server, kann die Verbindung aufgrund von Netzwerkfehlern fehlschlagen oder weil der Server nicht ausgeführt wird. Anstatt auf die standardmäßigen 20 Sekunden für die Verbindungs Herstellung zu warten, können Sie angeben, wie lange die Datenbank-Engine wartet, bevor ein Fehler erzeugt wird. Das Anmelden beim Server erfolgt implizit als Teil einer Reihe von verschiedenen Ereignissen, z. b. beim Ausführen einer Abfrage für eine externe Server Datenbank.

Weitere Informationen finden Sie im Thema "LoginTimeout-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaoworkspacegetname"></a><a name="getname"></a> CDaoWorkspace:: GetName

Mit dieser Member-Funktion können Sie den benutzerdefinierten Namen des DAO-Arbeitsbereichs Objekts abrufen, das dem-Objekt zugrunde liegt `CDaoWorkspace` .

```
CString GetName();
```

### <a name="return-value"></a>Rückgabewert

Ein [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Wert, der den benutzerdefinierten Namen des DAO-Arbeitsbereichs Objekts enthält.

### <a name="remarks"></a>Bemerkungen

Der Name ist hilfreich für den Zugriff auf das DAO-Arbeitsbereichs Objekt in der Arbeitsbereichs Sammlung der Datenbank-Engine anhand des Namens.

Weitere Informationen finden Sie im Thema "Name Property" in der DAO-Hilfe.

## <a name="cdaoworkspacegetusername"></a><a name="getusername"></a> CDaoWorkspace:: GetUserName

Rufen Sie diese Member-Funktion auf, um den Namen des Besitzers des Arbeitsbereichs zu erhalten.

```
CString GetUserName();
```

### <a name="return-value"></a>Rückgabewert

Ein [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Wert, der den Besitzer des Arbeitsbereichs Objekts darstellt.

### <a name="remarks"></a>Bemerkungen

Zum Abrufen oder Festlegen der Berechtigungen für den Besitzer des Arbeitsbereichs wird DAO direkt aufgerufen, um die Eigenschafts Einstellung der Berechtigungen zu überprüfen. Dadurch wird festgelegt, welche Berechtigungen für den Benutzer gelten. Um mit Berechtigungen arbeiten zu können, benötigen Sie ein System. MDA-Datei.

Weitere Informationen zum direkten Aufrufen von DAO finden [Sie im technischen Hinweis 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md). Weitere Informationen finden Sie im Thema "username Property" in der DAO-Hilfe.

## <a name="cdaoworkspacegetversion"></a><a name="getversion"></a> CDaoWorkspace:: GetVersion

Mit dieser Member-Funktion können Sie die Version der verwendeten Microsoft Jet-Datenbank-Engine bestimmen.

```
static CString PASCAL GetVersion();
```

### <a name="return-value"></a>Rückgabewert

Ein [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Wert, der die Version der Datenbank-Engine angibt, die dem Objekt zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Der zurückgegebene Wert stellt die Versionsnummer im Format "Major. Minor" dar. Beispiel: "3,0". Die Produkt Versionsnummer (z. b. 3,0) besteht aus der Versionsnummer (3), einem Zeitraum und der Releasenummer (0).

Weitere Informationen finden Sie im Thema "Versions Eigenschaft" in der DAO-Hilfe.

## <a name="cdaoworkspacegetworkspacecount"></a><a name="getworkspacecount"></a> CDaoWorkspace:: getworkspacecount

Rufen Sie diese Member-Funktion auf, um die Anzahl von DAO-Arbeitsbereichs Objekten in der Arbeitsbereichs Sammlung der Datenbank-Engine abzurufen.

```
short GetWorkspaceCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der geöffneten Arbeitsbereiche in der Auflistung der Arbeitsbereiche.

### <a name="remarks"></a>Bemerkungen

Diese Anzahl umfasst keine geöffneten Arbeitsbereiche, die nicht an die Auflistung angefügt werden. `GetWorkspaceCount` ist nützlich, wenn Sie alle definierten Arbeitsbereiche in der Arbeitsbereiche-Auflistung durchlaufen müssen. Informationen zu einem bestimmten Arbeitsbereich in der Sammlung finden Sie unter [GetWorkspaceInfo](#getworkspaceinfo). Die typische Verwendung besteht darin, `GetWorkspaceCount` die Anzahl der geöffneten Arbeitsbereiche aufzurufen und diese Zahl dann als Schleifenindex für wiederholte Aufrufe von zu verwenden `GetWorkspaceInfo` .

## <a name="cdaoworkspacegetworkspaceinfo"></a><a name="getworkspaceinfo"></a> CDaoWorkspace:: getworkspaceingefo

Rufen Sie diese Member-Funktion auf, um verschiedene Arten von Informationen über einen in der Sitzung geöffneten Arbeitsbereich zu erhalten.

```cpp
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
Der null basierte Index des Datenbankobjekts in der Workspaces-Auflistung für die Suche nach Index.

*wkspcinfo*<br/>
Ein Verweis auf ein [cdaoworkspaceinfo](../../mfc/reference/cdaoworkspaceinfo-structure.md) -Objekt, das die angeforderten Informationen zurückgibt.

*dwinfooptions*<br/>
Optionen, die angeben, welche Informationen zum Arbeitsbereich abgerufen werden sollen. Die verfügbaren Optionen werden hier zusammen mit den Funktionen aufgelistet, die von der Funktion zurückgegeben werden:

- Name der AFX_DAO_PRIMARY_INFO (Standard)

- AFX_DAO_SECONDARY_INFO primäre Informationen Plus: Benutzer Name

- AFX_DAO_ALL_INFO primäre und sekundäre Informationen Plus: isolieren von odbctrans

*lpszname*<br/>
Der Name des Arbeitsbereichs Objekts für die Suche nach Namen. Der Name ist eine Zeichenfolge mit bis zu 14 Zeichen, die das neue Arbeitsbereichs Objekt eindeutig benennen.

### <a name="remarks"></a>Bemerkungen

Eine Beschreibung der Informationen, die in *wkspcinfo*zurückgegeben werden, finden Sie in der [cdaoworkspaceinfo](../../mfc/reference/cdaoworkspaceinfo-structure.md) -Struktur. Diese Struktur enthält Member, die den in der Beschreibung von *dwinfooptions*aufgeführten Elementen der oben aufgeführten Informationen entsprechen. Wenn Sie Informationen auf einer Ebene anfordern, erhalten Sie auch Informationen für vorherige Ebenen.

## <a name="cdaoworkspaceidle"></a><a name="idle"></a> CDaoWorkspace:: Leerlauf

`Idle`Wird aufgerufen, um der Datenbank-Engine die Möglichkeit zu bieten, Hintergrundaufgaben auszuführen, die aufgrund intensiver Datenverarbeitung möglicherweise nicht auf dem neuesten Stand sind.

```
static void PASCAL Idle(int nAction = dbFreeLocks);
```

### <a name="parameters"></a>Parameter

*naktionsmeldung*<br/>
Eine Aktion, die während der Leerlauf Verarbeitung ausgeführt werden soll. Derzeit ist die einzige gültige Aktion `dbFreeLocks` .

### <a name="remarks"></a>Bemerkungen

Dies gilt häufig für Multibenutzer-Multitasking-Umgebungen, in denen nicht genügend Hintergrund Verarbeitungszeiten vorhanden sind, um alle Datensätze in einem Recordset aktuell zu halten.

> [!NOTE]
> `Idle`Das Aufrufen von ist nicht erforderlich für Datenbanken, die mit Version 3,0 der Microsoft Jet-Datenbank-Engine erstellt wurden. Wird `Idle` nur für Datenbanken verwendet, die in früheren Versionen erstellt wurden.

Lese Sperren werden normalerweise entfernt, und Daten in lokalen "Dynaset-Type"-recordsetobjekten werden nur aktualisiert, wenn keine anderen Aktionen (einschließlich Mausbewegungen) auftreten. Wenn Sie in regelmäßigen Abständen aufzurufen `Idle` , stellen Sie der Datenbank-Engine Zeit zum Auffangen von Hintergrund Verarbeitungsaufgaben bereit, indem Sie nicht benötigte Lese Sperren freigeben. Die Angabe der `dbFreeLocks` Konstante als Argument verzögert die Verarbeitung, bis alle Lese Sperren freigegeben wurden.

Diese Member-Funktion wird in Umgebungen mit nur einem Benutzer nicht benötigt, es sei denn, es werden mehrere Instanzen einer Anwendung ausgeführt. Die `Idle` Member-Funktion kann die Leistung in einer mehr Benutzerumgebung verbessern, da die Datenbank-Engine zwingt, Daten auf den Datenträger zu leeren und Sperren für den Arbeitsspeicher freizugeben. Sie können auch Lese Sperren freigeben, indem Sie Vorgänge an einer Transaktion vornehmen.

Weitere Informationen finden Sie im Thema "Leerlauf Methode" in der DAO-Hilfe.

## <a name="cdaoworkspaceisopen"></a><a name="isopen"></a> CDaoWorkspace:: IsOpen

Rufen Sie diese Member-Funktion auf, um zu bestimmen, ob das `CDaoWorkspace` Objekt geöffnet ist, d. –. ob das MFC-Objekt durch einen [Open](#open) -oder [Create](#create)-Befehl initialisiert wurde.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Arbeitsbereichs Objekt geöffnet ist. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie können jede der Element Funktionen eines Arbeitsbereichs mit einem geöffneten Zustand abrufen.

## <a name="cdaoworkspacem_pdaoworkspace"></a><a name="m_pdaoworkspace"></a> CDaoWorkspace:: m_pDAOWorkspace

Ein Zeiger auf das zugrunde liegende DAO-Arbeitsbereichs Objekt.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Datenmember, wenn Sie direkten Zugriff auf das zugrunde liegende DAO-Objekt benötigen. Mithilfe dieses Zeigers können Sie die Schnittstellen des DAO-Objekts abrufen.

Weitere Informationen zum direkten Zugriff auf DAO-Objekte finden [Sie im technischen Hinweis 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="cdaoworkspaceopen"></a><a name="open"></a> CDaoWorkspace:: Open

Öffnet explizit ein Arbeitsbereichs Objekt, das mit dem Standard Arbeitsbereich von DAO verknüpft ist.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Parameter

*lpszname*<br/>
Der Name des zu öffnenden DAO-Arbeitsbereichs Objekts – eine Zeichenfolge mit bis zu 14 Zeichen, die den Arbeitsbereich eindeutig benennen. Akzeptieren Sie den Standardwert NULL, um den Standard Arbeitsbereich explizit zu öffnen. Informationen zu den Benennungs Anforderungen finden Sie unter dem *lpszname* -Parameter für [Create](#create). Weitere Informationen finden Sie im Thema "Name Property" in der DAO-Hilfe.

### <a name="remarks"></a>Bemerkungen

Nach dem Erstellen eines- `CDaoWorkspace` Objekts können Sie diese Member-Funktion für eine der folgenden Aktionen verwenden:

- Öffnen Sie explizit den Standard Arbeitsbereich. Übergeben Sie für *lpszname*den Wert NULL.

- Öffnen Sie ein vorhandenes- `CDaoWorkspace` Objekt, ein Mitglied der Workspaces-Auflistung, nach dem Namen. Übergeben Sie einen gültigen Namen für ein vorhandenes Arbeitsbereichs Objekt.

`Open` versetzt das Arbeitsbereichs Objekt in einen geöffneten Zustand und initialisiert die Datenbank-Engine auch, wenn Sie nicht bereits für die Anwendung initialisiert wurde.

Obwohl viele Element `CDaoWorkspace` Funktionen nur aufgerufen werden können, nachdem der Arbeitsbereich geöffnet wurde, sind die folgenden Member-Funktionen, die auf der Datenbank-Engine ausgeführt werden, nach der Erstellung des C++-Objekts, jedoch vor einem Aufruf von verfügbar. `Open`

:::row:::
   :::column span="":::
      [Stelle](#create)\
      [Getinipath](#getinipath)\
      [GetLoginTimeout](#getlogintimeout)
   :::column-end:::
   :::column span="":::
      [GetVersion](#getversion)\
      [Idle](#idle)
   :::column-end:::
   :::column span="":::
      [SetDefaultPassword](#setdefaultpassword)\
      [Setdefaultuser](#setdefaultuser)
   :::column-end:::
   :::column span="":::
      [Setinipath](#setinipath)\
      [SetLoginTimeout](#setlogintimeout)
   :::column-end:::
:::row-end:::

## <a name="cdaoworkspacerepairdatabase"></a><a name="repairdatabase"></a> CDaoWorkspace:: repairren Database

Wenn Sie versuchen, eine beschädigte Datenbank zu reparieren, die auf das Microsoft Jet-Datenbankmodul zugreift, müssen Sie diese Member-Funktion abrufen.

```
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parameter

*lpszname*<br/>
Der Pfad und Dateiname für eine vorhandene Microsoft Jet Engine-Datenbankdatei. Wenn Sie den Pfad weglassen, wird nur das aktuelle Verzeichnis durchsucht. Wenn Ihr System die Uniform Naming Convention (UNC) unterstützt, können Sie auch einen Netzwerkpfad angeben, z. b.: " \\ \\ \meinserver\meinefreigabe\meineverzeichnis \\ \\ \\ \\ \ MyDB. MDB ". (Doppelte umgekehrte Schrägstriche sind in der Pfad Zeichenfolge erforderlich, da " \\ " das Escapezeichen "C++" ist.)

### <a name="remarks"></a>Bemerkungen

Sie müssen die von *lpszname* angegebene Datenbank schließen, bevor Sie Sie reparieren. In einer mehr Benutzerumgebung kann *lpszname* nicht von anderen Benutzern geöffnet werden, während Sie Sie reparieren. Wenn *lpszname* nicht geschlossen ist oder für die ausschließliche Verwendung nicht verfügbar ist, tritt ein Fehler auf.

Diese Member-Funktion versucht, eine Datenbank zu reparieren, die durch einen unvollständigen Schreibvorgang als möglicherweise beschädigt gekennzeichnet wurde. Dies kann vorkommen, wenn eine Anwendung, die das Microsoft Jet-Datenbankmodul verwendet, aufgrund eines Stromausfalls oder Computer Hardware Problems unerwartet geschlossen wird. Wenn Sie den Vorgang abschließen und die Funktion zum [Schließen](../../mfc/reference/cdaodatabase-class.md#close) des Members aufzurufen, oder Sie die Anwendung auf die übliche Weise beenden, wird die Datenbank nicht als möglicherweise beschädigt markiert.

> [!NOTE]
> Nach dem Reparieren einer Datenbank ist es auch ratsam, Sie mit der Element Funktion " [CompactDatabase](#compactdatabase) " zu komprimieren, um die Datei zu defragmentieren und Speicherplatz auf dem Datenträger wiederherzustellen.

Weitere Informationen zum Reparieren von Datenbanken finden Sie im Thema "repairidatabase Method" in der DAO-Hilfe.

## <a name="cdaoworkspacerollback"></a><a name="rollback"></a> CDaoWorkspace:: Rollback

Mit dieser Member-Funktion können Sie die aktuelle Transaktion beenden und alle Datenbanken im Arbeitsbereich vor dem Beginn der Transaktion wiederherstellen.

```cpp
void Rollback();
```

### <a name="remarks"></a>Bemerkungen

> [!CAUTION]
> Innerhalb eines Arbeitsbereichs Objekts sind Transaktionen immer global für den Arbeitsbereich und nicht auf eine Datenbank oder ein Recordset beschränkt. Wenn Sie Vorgänge für mehrere Datenbanken oder Recordsets innerhalb einer Arbeitsbereichs Transaktion ausführen, `Rollback` stellt alle Vorgänge für alle diese Datenbanken und Recordsets wieder her.

Wenn Sie ein Arbeitsbereichs Objekt schließen, ohne ausstehende Transaktionen zu speichern oder zurücksetzen, wird für die Transaktionen automatisch ein Rollback ausgeführt. Wenn Sie [CommitTrans](#committrans) aufrufen `Rollback` , oder ohne zuerst [BeginTrans](#begintrans)aufzurufen, tritt ein Fehler auf.

> [!NOTE]
> Wenn Sie eine Transaktion beginnen, zeichnet die Datenbank-Engine die Vorgänge in einer Datei auf, die in dem von der TEMP-Umgebungsvariablen auf der Arbeitsstation angegebenen Verzeichnis gespeichert ist. Wenn die Transaktionsprotokoll Datei den verfügbaren Speicher auf dem temporären Laufwerk erschöpft, bewirkt die Datenbank-Engine, dass MFC einen `CDaoException` (DAO-Fehler 2004) auslöst. An diesem Punkt wird bei der Ausführung `CommitTrans` von eine unbestimmte Anzahl von Vorgängen committet, aber die restlichen nicht abgeschlossenen Vorgänge gehen verloren, und der Vorgang muss neu gestartet werden. Durch den Aufruf von wird `Rollback` das Transaktionsprotokoll freigegeben, und es wird ein Rollback für alle Vorgänge

## <a name="cdaoworkspacesetdefaultpassword"></a><a name="setdefaultpassword"></a> CDaoWorkspace:: SetDefaultPassword

Mit dieser Member-Funktion können Sie das Standard Kennwort festlegen, das von der Datenbank-Engine verwendet wird, wenn ein Arbeitsbereichs Objekt ohne bestimmtes Kennwort erstellt wird.

```
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parameter

*lpszpassword*<br/>
Das Standard Kennwort. Ein Kennwort kann bis zu 14 Zeichen lang sein und kann ein beliebiges Zeichen mit Ausnahme von ASCII 0 (null) enthalten. Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden.

### <a name="remarks"></a>Bemerkungen

Das von Ihnen festgelegte Standard Kennwort gilt für neue Arbeitsbereiche, die Sie nach dem-Befehl erstellen. Wenn Sie nachfolgende Arbeitsbereiche erstellen, müssen Sie im [Create](#create) -Befehl kein Kennwort angeben.

So verwenden Sie diese Member-Funktion:

1. Erstellen Sie ein- `CDaoWorkspace` Objekt, aber nicht aufzurufen `Create` .

1. Rufen `SetDefaultPassword` Sie und, falls gewünscht, [setdefaultuser](#setdefaultuser)auf.

1. Ruft `Create` für dieses Arbeitsbereichs Objekt oder nachfolgende Objekte auf, ohne ein Kennwort anzugeben.

Standardmäßig ist die DefaultUser-Eigenschaft auf "admin" festgelegt, und die DefaultPassword-Eigenschaft wird auf eine leere Zeichenfolge ("") festgelegt.

Weitere Informationen zur Sicherheit finden Sie im Thema "Berechtigungs Eigenschaft" in der DAO-Hilfe. Weitere Informationen finden Sie in den Themen "DefaultPassword Property" und "DefaultUser Property" in der DAO-Hilfe.

## <a name="cdaoworkspacesetdefaultuser"></a><a name="setdefaultuser"></a> CDaoWorkspace:: setdefaultuser

Mit dieser Member-Funktion können Sie den Standardbenutzer Namen festlegen, der von der Datenbank-Engine verwendet wird, wenn ein Arbeitsbereichs Objekt ohne einen bestimmten Benutzernamen erstellt wird.

```
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```

### <a name="parameters"></a>Parameter

*lpszdefaultuser*<br/>
Der Standardbenutzername. Ein Benutzername kann 1-20 Zeichen lang sein und alphabetische Zeichen enthalten. Zeichen mit Vorzeichen, Ziffern, Leerzeichen und Symbolen mit Ausnahme von: "(Anführungszeichen),/(Schrägstrich), \ (umgekehrter Schrägstrich), \[ \] (Klammern),: (Doppelpunkt), &#124; (Pipe), \< (less-than sign), > (größer als Vorzeichen), + (Pluszeichen), = (Gleichheitszeichen),; (Semikolon),, (Komma), (Fragezeichen), \* (Sternchen), führende Leerzeichen und Steuerzeichen (ASCII 00 bis ASCII 31). Weitere Informationen finden Sie im Thema "username Property" in der DAO-Hilfe.

### <a name="remarks"></a>Bemerkungen

Der von Ihnen festgelegte Standardbenutzer Name gilt für neue Arbeitsbereiche, die Sie nach dem-Befehl erstellen. Wenn Sie nachfolgende Arbeitsbereiche erstellen, müssen Sie im [Create](#create) -Befehl keinen Benutzernamen angeben.

So verwenden Sie diese Member-Funktion:

1. Erstellen Sie ein- `CDaoWorkspace` Objekt, aber nicht aufzurufen `Create` .

1. Aufrufen von `SetDefaultUser` und, wenn Sie möchten, [SetDefaultPassword](#setdefaultpassword).

1. `Create`Für dieses Arbeitsbereichs Objekt oder nachfolgende Objekte ohne Angabe eines Benutzernamens aufzurufen.

Standardmäßig ist die DefaultUser-Eigenschaft auf "admin" festgelegt, und die DefaultPassword-Eigenschaft wird auf eine leere Zeichenfolge ("") festgelegt.

Weitere Informationen finden Sie in den Themen "DefaultUser Property" und "DefaultPassword Property" in der DAO-Hilfe.

## <a name="cdaoworkspacesetinipath"></a><a name="setinipath"></a> CDaoWorkspace:: setinipath

Mit dieser Member-Funktion geben Sie den Speicherort der Windows-Registrierungs Einstellungen für die Microsoft Jet-Datenbank-Engine an.

```
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```

### <a name="parameters"></a>Parameter

*lpszregistrysubkey*<br/>
Eine Zeichenfolge mit dem Namen eines Windows-Registrierungs unter Schlüssels für den Speicherort der Microsoft Jet-Datenbank-Engine-Einstellungen oder Parameter, die für installierbare ISAM-Datenbanken erforderlich sind

### <a name="remarks"></a>Bemerkungen

`SetIniPath`Wird nur aufgerufen, wenn Sie spezielle Einstellungen angeben müssen. Weitere Informationen finden Sie im Thema "INIPath-Eigenschaft" in der DAO-Hilfe.

> [!NOTE]
> `SetIniPath`Wird während der Anwendungs Installation aufgerufen, nicht bei der Ausführung der Anwendung. `SetIniPath` muss vor dem Öffnen von Arbeitsbereichen, Datenbanken oder Recordsets aufgerufen werden. Andernfalls löst MFC eine Ausnahme aus.

Sie können diesen Mechanismus verwenden, um die Datenbank-Engine mit vom Benutzer bereitgestellten Registrierungs Einstellungen zu konfigurieren. Der Gültigkeitsbereich dieses Attributs ist auf Ihre Anwendung beschränkt und kann nicht geändert werden, ohne die Anwendung neu zu starten.

## <a name="cdaoworkspacesetisolateodbctrans"></a><a name="setisolateodbctrans"></a> CDaoWorkspace:: "abtisolateodbctrans"

Mit dieser Member-Funktion können Sie den Wert der DAO IsolateODBCTrans-Eigenschaft für den Arbeitsbereich festlegen.

```cpp
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```

### <a name="parameters"></a>Parameter

*bisolateodbctrans*<br/>
Übergeben Sie true, wenn Sie mit der Isolierung von ODBC-Transaktionen beginnen möchten. Übergeben Sie false, wenn Sie die Isolierung von ODBC-Transaktionen abbrechen möchten.

### <a name="remarks"></a>Bemerkungen

In einigen Situationen müssen möglicherweise mehrere gleichzeitige Transaktionen in der gleichen ODBC-Datenbank ausstehen. Zu diesem Zweck müssen Sie für jede Transaktion einen separaten Arbeitsbereich öffnen. Obwohl jeder Arbeitsbereich über eine eigene ODBC-Verbindung mit der Datenbank verfügen kann, verlangsamt dies die Systemleistung. Da die Transaktions Isolation normalerweise nicht erforderlich ist, werden ODBC-Verbindungen von mehreren Arbeitsbereichs Objekten, die vom gleichen Benutzer geöffnet wurden, standardmäßig freigegeben.

Einige ODBC-Server, wie z. b. Microsoft SQL Server, lassen keine gleichzeitigen Transaktionen auf einer einzelnen Verbindung zu. Wenn Sie mehr als eine Transaktion gleichzeitig für eine solche Datenbank ausstehend benötigen, legen Sie die IsolateODBCTrans-Eigenschaft für jeden Arbeitsbereich auf "true" fest, sobald Sie Sie öffnen. Dies erzwingt eine separate ODBC-Verbindung für jeden Arbeitsbereich.

## <a name="cdaoworkspacesetlogintimeout"></a><a name="setlogintimeout"></a> CDaoWorkspace:: setLoginTimeout

Mit dieser Member-Funktion können Sie den Wert der DAO LoginTimeout-Eigenschaft für den Arbeitsbereich festlegen.

```
static void PASCAL SetLoginTimeout(short nSeconds);
```

### <a name="parameters"></a>Parameter

*nSekunden*<br/>
Die Anzahl der Sekunden, bevor ein Fehler auftritt, wenn Sie versuchen, sich bei einer ODBC-Datenbank anzumelden.

### <a name="remarks"></a>Bemerkungen

Dieser Wert gibt die Anzahl der Sekunden an, bevor ein Fehler auftritt, wenn Sie versuchen, sich bei einer ODBC-Datenbank anzumelden. Die Standardeinstellung für LoginTimeOut beträgt 20 Sekunden. Wenn LoginTimeout auf 0 festgelegt ist, tritt kein Timeout auf, und die Kommunikation mit der Datenquelle reagiert möglicherweise nicht mehr.

Wenn Sie versuchen, sich bei einer ODBC-Datenbank anzumelden, wie z. b. Microsoft SQL Server, kann die Verbindung aufgrund von Netzwerkfehlern fehlschlagen oder weil der Server nicht ausgeführt wird. Anstatt auf die standardmäßigen 20 Sekunden für die Verbindungs Herstellung zu warten, können Sie angeben, wie lange die Datenbank-Engine wartet, bevor ein Fehler erzeugt wird. Das Anmelden beim Server erfolgt implizit als Teil einer Reihe von verschiedenen Ereignissen, z. b. beim Ausführen einer Abfrage für eine externe Server Datenbank. Der Timeout Wert wird durch die aktuelle Einstellung der LoginTimeout-Eigenschaft bestimmt.

Weitere Informationen finden Sie im Thema "LoginTimeout-Eigenschaft" in der DAO-Hilfe.

## <a name="see-also"></a>Weitere Informationen

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase-Klasse](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset-Klasse](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef-Klasse](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef-Klasse](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoException-Klasse](../../mfc/reference/cdaoexception-class.md)
