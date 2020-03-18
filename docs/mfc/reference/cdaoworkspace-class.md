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
ms.openlocfilehash: c1d235035cee9342c8c54c7aaa4e05a96d5a37e3
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425970"
---
# <a name="cdaoworkspace-class"></a>CDaoWorkspace-Klasse

Verwaltet eine benannte, kennwortgeschützte Datenbanksitzung eines einzelnen Benutzers von der Anmeldung bis zu Abmeldung. DAO wird über Office 2013 unterstützt. DAO 3,6 ist die endgültige Version, die als veraltet eingestuft wird.

## <a name="syntax"></a>Syntax

```
class CDaoWorkspace : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CDaoWorkspace:: CDaoWorkspace](#cdaoworkspace)|Erstellt ein Workspace-Objekt. Anschließend wird `Create` oder `Open`aufgerufen.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CDaoWorkspace:: Append](#append)|Fügt einen neu erstellten Arbeitsbereich für die Datenbank-Engine-Arbeitsbereiche Sammlung an.|
|[CDaoWorkspace:: BeginTrans](#begintrans)|Beginnt eine neue Transaktion, die auf alle Datenbanken, die im Arbeitsbereich geöffnet wird.|
|[CDaoWorkspace:: Close](#close)|Schließt den Arbeitsbereich und alle darin enthaltenen Objekte. Ausstehende Transaktionen ein Rollback ausgeführt.|
|[CDaoWorkspace:: CommitTrans](#committrans)|Schließt die aktuelle Transaktion ab und speichert die Änderungen.|
|[CDaoWorkspace:: CompactDatabase](#compactdatabase)|Eine Datenbank komprimiert (oder dupliziert).|
|[CDaoWorkspace:: Create](#create)|Erstellt ein neues Objekt des DAO-Arbeitsbereich.|
|[CDaoWorkspace:: getdatabasecount](#getdatabasecount)|Gibt die Anzahl der DAO-Datenbankobjekte in der arbeitsbereichssammlung Datenbanken zurück.|
|[CDaoWorkspace:: getdatabaseingefo](#getdatabaseinfo)|Gibt Informationen zu einer angegebenen DAO-Datenbank, die in der datenbankauflistung des Arbeitsbereichs definiert.|
|[CDaoWorkspace:: getinipath](#getinipath)|Gibt den Speicherort der Microsoft Jet-Datenbank-Engine-initialisierungseinstellungen in der Windows-Registrierung zurück.|
|[CDaoWorkspace:: getisolateodbctrans](#getisolateodbctrans)|Gibt einen Wert, der angibt, ob mehrere Transaktionen, bei denen die ODBC-Datenquelle über isoliert sind, mehrere Verbindungen mit der Datenquelle erzwungen.|
|[CDaoWorkspace:: GetLoginTimeout](#getlogintimeout)|Gibt die Anzahl der Sekunden, bevor ein Fehler auftritt, wenn der Benutzer versucht, eine ODBC-Datenbank anmelden.|
|[CDaoWorkspace:: GetName](#getname)|Der benutzerdefinierte Name für die Workspace-Objekt zurückgegeben.|
|[CDaoWorkspace:: GetUserName](#getusername)|Gibt zurück, der Benutzername angegeben, wenn der Arbeitsbereich erstellt wurde. Dies ist der Name der Besitzer des Arbeitsbereichs.|
|[CDaoWorkspace:: GetVersion](#getversion)|Gibt eine Zeichenfolge mit der Version der Datenbank-Engine, die mit dem Arbeitsbereich verknüpft ist.|
|[CDaoWorkspace:: getworkspacecount](#getworkspacecount)|Gibt die Anzahl der Objekte für DAO-Arbeitsbereich in der Datenbank-Engine-arbeitsbereicheauflistung zurück.|
|[CDaoWorkspace:: getworkspaceingefo](#getworkspaceinfo)|Gibt Informationen zu einem angegebenen DAO-Arbeitsbereich in der Datenbank-Engine-arbeitsbereicheauflistung definiert.|
|[CDaoWorkspace:: Leerlauf](#idle)|Können die Datenbank-Engine zum Ausführen von Hintergrundaufgaben.|
|[CDaoWorkspace:: IsOpen](#isopen)|Gibt zurück, die ungleich NULL, wenn der Arbeitsbereich öffnen.|
|[CDaoWorkspace:: Open](#open)|Explizit öffnet ein Workspace-Objekt, das mit DAO Standard-Arbeitsbereich verknüpft ist.|
|[CDaoWorkspace:: repairren Database](#repairdatabase)|Versucht, eine beschädigte Datenbank zu reparieren.|
|[CDaoWorkspace:: Rollback](#rollback)|Beendet die aktuelle Transaktion aus, und die Änderungen nicht gespeichert.|
|[CDaoWorkspace:: SetDefaultPassword](#setdefaultpassword)|Legt das Kennwort, das die Datenbank-Engine verwendet wird, wenn eine Arbeitsbereichsobjekt ohne ein bestimmtes Kennwort erstellt wird.|
|[CDaoWorkspace:: setdefaultuser](#setdefaultuser)|Legt fest, den Benutzernamen ein, dem die Datenbank-Engine verwendet wird, wenn eine Arbeitsbereichsobjekt ohne einen bestimmten Benutzernamen erstellt wird.|
|[CDaoWorkspace:: setinipath](#setinipath)|Legt den Speicherort der Microsoft Jet-Datenbank-Engine-initialisierungseinstellungen in der Windows-Registrierung fest.|
|[CDaoWorkspace:: "abtisolateodbctrans"](#setisolateodbctrans)|Gibt an, ob mehrere Transaktionen, bei denen die ODBC-Datenquelle isoliert werden, indem Sie mehrere Verbindungen mit der Datenquelle zu erzwingen.|
|[CDaoWorkspace:: setLoginTimeout](#setlogintimeout)|Legt die Anzahl der Sekunden, bevor ein Fehler auftritt, wenn der Benutzer versucht, eine ODBC-Datenquelle anmelden.|

### <a name="public-data-members"></a>Öffentliche Datenelemente

|Name|Beschreibung|
|----------|-----------------|
|[CDaoWorkspace:: m_pDAOWorkspace](#m_pdaoworkspace)|Verweist auf das zugrunde liegende DAO-Workspace-Objekt.|

## <a name="remarks"></a>Hinweise

In den meisten Fällen benötigen Sie nicht mehrere Arbeitsbereiche, und Sie müssen keine explizite Workspace-Objekte zu erstellen; Wenn Sie die Datenbank und Recordset-Objekte öffnen, verwenden sie die DAO Standard-Arbeitsbereich. Allerdings können Sie mehrere Sitzungen zu einem Zeitpunkt führen Sie bei Bedarf zusätzliche Workspace-Objekte erstellen. Jedes Arbeitsbereichsobjekt kann mehrere geöffneten Datenbankobjekten in seine eigene Sammlung von Datenbanken enthalten. In MFC ist ein Arbeitsbereich in erster Linie eine Transaktions-Manager, eine Reihe von open Datenbanken angeben, alle in der "Transaktionsprotokoll-Speicherplatz."

> [!NOTE]
>  Die DAO-Datenbankklassen unterscheiden sich von der MFC-Datenbankklassen in Bezug auf Open Database Connectivity (ODBC). Allen Klassennamen der DAO-Datenbank haben ein Präfix "CDao". Im Allgemeinen sind die MFC-Klassen basierend auf DAO leistungsfähiger als die MFC-Klassen basierend auf ODBC. Die DAO-basierten Klassen greifen auf Daten über das Microsoft Jet-Datenbankmodul, einschließlich der ODBC-Treiber. Außerdem unterstützen (Data Definition Language, Datendefinitionssprache)-Vorgänge, z. B. das Erstellen von Datenbanken und Tabellen und Felder, die über die Klassen, ohne direkt aufrufen von DAO hinzufügen.

## <a name="capabilities"></a>Funktionen

Klassen `CDaoWorkspace` stellt Folgendes bereit:

- Explizite Zugriff, falls erforderlich, um eine Standard-Arbeitsbereich, und initialisieren Sie die Datenbank-Engine erstellt. In der Regel verwenden Sie DAOs-Standard-Arbeitsbereich implizit durch das Erstellen der Datenbank und Recordset-Objekte.

- Öffnen Sie ein Transaktionsprotokoll-Speicherplatz in dem Transaktionen gilt für alle Datenbanken im Arbeitsbereich. Sie können zusätzliche Arbeitsbereiche zum Verwalten von separaten Transaktion Speicherplätze erstellen.

- Eine Schnittstelle für viele Eigenschaften der zugrunde liegenden Microsoft Jet-Datenbank-Engine (siehe die statische Memberfunktionen). Öffnen oder Erstellen eines Arbeitsbereichs oder Aufrufen einer statischen Memberfunktion vor dem Öffnen oder erstellen, und initialisiert die Datenbank-Engine.

- Zugriff auf die Datenbank-Engine-Arbeitsbereiche-Auflistung, der alle aktiven Arbeitsbereiche gespeichert, die es angefügt wurden. Sie können auch erstellen und Verwenden von Arbeitsbereichen, ohne auf die Auflistung anfügen.

## <a name="security"></a>Sicherheit

MFC implementiert nicht die Sammlungen für Benutzer und Gruppen über DAO, die für die sicherheitssteuerung verwendet werden. Wenn Sie die Aspekte des DAO benötigen, müssen Sie sie selbst über direkte Aufrufe von DAO-Schnittstellen programmieren. Weitere Informationen finden [Sie im technischen Hinweis 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="usage"></a>Verwendung

Sie können Klassen `CDaoWorkspace` für folgende Zwecke verwenden:

- Öffnen Sie explizit die Standard-Arbeitsbereich.

   Normalerweise ist die Verwendung des Standard Arbeitsbereichs implizit – Wenn Sie neue [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) -oder [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) -Objekte öffnen. Sie müssen jedoch möglicherweise für den Zugriff explizit – z. B. zum Zugriff auf Datenbank-Engine-Eigenschaften oder die Arbeitsbereiche-Auflistung. Nachfolgend finden Sie in der "Impliziten Verwendung der Standard-Arbeitsbereich".

- Neue Arbeitsbereiche zu erstellen. Rufen Sie [Append](#append) auf, wenn Sie Sie der Workspaces-Auflistung hinzufügen möchten.

- Öffnen Sie einen vorhandenen Arbeitsbereich, in der Auflistung der Arbeitsbereiche.

Das Erstellen eines neuen Arbeitsbereichs, der nicht bereits in der Arbeitsbereichs Sammlung vorhanden ist, wird unter der [Create](#create) Member-Funktion beschrieben. Workspace-Objekte beibehalten in keiner Weise zwischen Beispieldatenbank-Engine-Sitzungen nicht. Wenn Ihre Anwendung statisch MFC verknüpft ist, wird beim Beenden der Anwendung die Datenbank-Engine deinitialisiert. Wenn Ihre Anwendung dynamisch mit MFC verknüpft wird, ist die Datenbank-Engine nicht initialisiert, wenn die MFC-DLL entladen wird.

Wenn Sie den Standard Arbeitsbereich explizit öffnen oder einen vorhandenen Arbeitsbereich in der Sammlung "Arbeitsbereiche" öffnen, wird unter der Funktion " [Open](#open) Member" beschrieben.

Beenden Sie eine Arbeitsbereichs Sitzung, indem Sie den Arbeitsbereich mit der [Close](#close) Member-Funktion schließen. `Close` schließt alle Datenbanken, die Sie zuvor nicht geschlossen haben, und stellt für Transaktionen ohne Commit ein Rollback durch.

## <a name="transactions"></a>Transaktionen

DAO verwaltet Transaktionen auf der arbeitsbereichsebene. Transaktionen in einem Arbeitsbereich mit mehreren open-Datenbanken, daher gelten für alle Datenbanken. Wenn beispielsweise zwei Datenbanken über nicht ausgeübte Updates verfügen und [CommitTrans](#committrans)aufgerufen wird, wird für alle Updates ein Commit ausgeführt. Wenn Sie Transaktionen auf eine einzelne Datenbank beschränken möchten, benötigen Sie ein eigenes Workspace-Objekt für sie.

## <a name="implicit-use-of-the-default-workspace"></a>Implizite Verwendung von Standard-Arbeitsbereich

Verwendet MFC-DAO Standard-Arbeitsbereich implizit in den folgenden Situationen:

- Wenn Sie ein neues `CDaoDatabase` Objekt erstellen, aber nicht über ein vorhandenes `CDaoWorkspace` Objekt, erstellt MFC ein temporäres Arbeitsbereichs Objekt für Sie, das dem Standard Arbeitsbereich von DAO entspricht. Wenn Sie für mehrere Datenbanken dazu sind alle Datenbankobjekte mit Standard-Arbeitsbereich verknüpft. Sie können über einen `CDaoDatabase` Datenmember auf den Arbeitsbereich einer Datenbank zugreifen.

- Wenn Sie ein `CDaoRecordset` Objekt erstellen, ohne einen Zeiger auf ein `CDaoDatabase` Objekt bereitzustellen, erstellt MFC ein temporäres Datenbankobjekt und durch Erweiterung ein temporäres Arbeitsbereichs Objekt. Sie können über ein `CDaoRecordset` Datenmember auf die Datenbank eines Recordsets und indirekt auf den Arbeitsbereich zugreifen.

## <a name="other-operations"></a>Andere Vorgänge

Andere Datenbankoperationen werden ebenfalls bereitgestellt, z. B. eine beschädigte Datenbank zu reparieren oder Komprimieren einer Datenbank.

Weitere Informationen zum direkten Aufrufen von DAO und zur DAO-Sicherheit finden [Sie im technischen Hinweis 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CDaoWorkspace`

## <a name="requirements"></a>Voraussetzungen

**Header:** afxdao.h

##  <a name="append"></a>CDaoWorkspace:: Append

Rufen Sie diese Member-Funktion nach dem aufzurufen von [Create](#create)auf.

```
virtual void Append();
```

### <a name="remarks"></a>Hinweise

`Append` fügt ein neu erstelltes Arbeitsbereichs Objekt an die Arbeitsbereichs Sammlung der Datenbank-Engine an. Arbeitsbereiche beibehalten zwischen Datenbank-Engine-Sitzungen nicht; Sie werden nur im Arbeitsspeicher, nicht auf dem Datenträger gespeichert. Sie müssen keine fügen Sie einen Arbeitsbereich; Wenn Sie nicht, können Sie weiterhin verwenden.

Ein angefügter Arbeitsbereich bleibt in der Workspaces-Auflistung in einem aktiven, geöffneten Zustand, bis Sie seine [Close](#close) Member-Funktion aufruft.

Weitere Informationen finden Sie unter dem Thema "Fügen Sie der Methode" in-DAO-Hilfe.

##  <a name="begintrans"></a>CDaoWorkspace:: BeginTrans

Rufen Sie diese Memberfunktion zum Initiieren einer Transaktion.

```
void BeginTrans();
```

### <a name="remarks"></a>Hinweise

Nachdem Sie `BeginTrans`aufgerufen haben, werden Updates, die Sie an Ihrer Daten-oder Datenbankstruktur vornehmen, beim commitcommit der Transaktion wirksam. Da der Arbeitsbereich einen einzelnen Transaktionsbereich definiert, gilt die Transaktion alle geöffneten Datenbanken in den Arbeitsbereich ab. Es gibt zwei Möglichkeiten, um die Transaktion abzuschließen:

- Der [CommitTrans](#committrans) -Member wird aufgerufen, um einen Commit für die Transaktion durchzusetzen und die Änderungen an der Datenquelle zu speichern

- Oder rufen Sie die [Rollback](#rollback) -Member-Funktion auf, um die Transaktion abzubrechen.

Die Workspace-Objekt oder ein Datenbankobjekt schließen, während eine Transaktion ausstehende wird ein Rollback aller anstehende Transaktionen.

Wenn Sie Transaktionen in einer ODBC-Datenquelle von denen in einer anderen ODBC-Datenquelle isolieren müssen, finden Sie weitere Informationen unter der Member-Funktion von " [c tisolateodbctrans](#setisolateodbctrans) ".

##  <a name="cdaoworkspace"></a>CDaoWorkspace:: CDaoWorkspace

Erstellt ein `CDaoWorkspace`-Objekt.

```
CDaoWorkspace();
```

### <a name="remarks"></a>Hinweise

Nach dem Erstellen der C++-Objekt, haben Sie zwei Möglichkeiten:

- Ruft die [Open](#open) Member-Funktion des-Objekts auf, um den Standard Arbeitsbereich zu öffnen oder ein vorhandenes Objekt in der Arbeitsbereichs Auflistung zu öffnen.

- Oder rufen Sie die [Create](#create) Member-Funktion des Objekts auf, um ein neues DAO-Arbeitsbereichs Objekt zu erstellen. Dadurch wird explizit eine neue Arbeitsbereichs Sitzung gestartet, auf die Sie über das `CDaoWorkspace` Objekt verweisen können. Nachdem Sie `Create`aufgerufen haben, können Sie " [Append](#append) " aufrufen, wenn Sie den Arbeitsbereich der Arbeitsbereichs Sammlung der Datenbank-Engine hinzufügen möchten.

Informationen dazu, wann Sie explizit ein `CDaoWorkspace` Objekt erstellen müssen, finden Sie in der Übersicht über die Klassen Übersicht für [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) . Normalerweise verwenden Sie Arbeitsbereiche, die implizit erstellt werden, wenn Sie ein [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) -Objekt öffnen, ohne einen Arbeitsbereich anzugeben, oder wenn Sie ein [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) -Objekt öffnen, ohne ein Datenbankobjekt anzugeben. MFC-DAO-Objekte, die auf diese Weise erstellter verwenden DAO Standard-Arbeitsbereich, das einmal erstellt und wiederverwendet wird.

Um einen Arbeitsbereich und die darin enthaltenen Objekte freizugeben, müssen Sie die [Close](#close) Member-Funktion des Arbeitsbereichs Objekts anrufen.

##  <a name="close"></a>CDaoWorkspace:: Close

Rufen Sie diese Memberfunktion, um die Workspace-Objekt zu schließen.

```
virtual void Close();
```

### <a name="remarks"></a>Hinweise

Schließen ein Objekt Öffnen des Arbeitsbereichs gibt das zugrunde liegende DAO-Objekt und der Arbeitsbereich ist ein Member der Auflistung Arbeitsbereiche aus der Auflistung entfernt. Das Aufrufen von `Close` ist eine gute Programmier Übung.

> [!CAUTION]
>  Ein Workspace-Objekt schließen Schließt alle geöffneten Datenbanken im Arbeitsbereich. Dies führt alle geöffneten Recordsets in den Datenbanken, die ebenfalls geschlossen wird, und alle ausstehenden Änderungen oder Updates ein Rollback. Weitere Informationen finden Sie in den Element Funktionen [CDaoDatabase:: Close](../../mfc/reference/cdaodatabase-class.md#close), [CDaoRecordset:: Close](../../mfc/reference/cdaorecordset-class.md#close), [CDaoTableDef:: Close](../../mfc/reference/cdaotabledef-class.md#close)und [CDaoQueryDef:: Close](../../mfc/reference/cdaoquerydef-class.md#close) .

Workspace-Objekte sind nicht dauerhaft; Sie sind nur vorhanden, während Verweise auf diese vorhanden sind. Dies bedeutet, dass wenn die Datenbank-Engine-Sitzung beendet wird, den Arbeitsbereich und der datenbankauflistung nicht beibehalten werden. Sie müssen sie erneut auf die nächste Sitzung erstellen, indem Sie Ihren Arbeitsbereich und die Datenbanken erneut zu öffnen.

Verwandte Informationen finden Sie im Thema "Close-Methode" in-DAO-Hilfe.

##  <a name="committrans"></a>CDaoWorkspace:: CommitTrans

Rufen Sie diese Memberfunktion zum commit einer Transaktion – eine Gruppe von Änderungen und Aktualisierungen auf eine oder mehrere Datenbanken in den Arbeitsbereich zu speichern.

```
void CommitTrans();
```

### <a name="remarks"></a>Hinweise

Eine Transaktion besteht aus einer Reihe von Änderungen an den Daten der Datenbank oder ihrer Struktur, beginnend mit einem Aufrufen von [BeginTrans](#begintrans). Wenn Sie die Transaktion abgeschlossen haben, führen Sie entweder einen Commit für die Transaktion durch, oder führen Sie ein [Rollback](#rollback)aus (Abbrechen der Änderungen). In der Standardeinstellung ohne Transaktionen sind Updates für Datensätze sofort ein Commit ausgeführt. Das Aufrufen von `BeginTrans` bewirkt, dass die Aktualisierungen verzögert werden, bis Sie `CommitTrans`aufrufen.

> [!CAUTION]
>  In einem Arbeitsbereich Transaktionen sind immer global für den Arbeitsbereich und sind nicht nur eine Datenbank oder ein Recordset auf. Wenn Sie Vorgänge für mehrere Datenbanken oder Recordsets innerhalb einer Arbeitsbereichs Transaktion ausführen, führt `CommitTrans` einen Commit für alle ausstehenden Updates aus, und `Rollback` stellt alle Vorgänge für diese Datenbanken und Recordsets wieder her.

Wenn Sie eine Datenbank oder ein Arbeitsbereichs mit ausstehenden Transaktionen schließen, werden die Transaktionen alle ein Rollback ausgeführt.

> [!NOTE]
>  Dies ist kein Zweiphasen-Commit-Mechanismus. Wenn ein Update ein Fehler auftritt, Commit, führt andere weiterhin einen commit.

##  <a name="compactdatabase"></a>CDaoWorkspace:: CompactDatabase

Rufen Sie diese Memberfunktion zum Komprimieren einer angegebenen Microsoft Jet (. MDB)-Datenbank.

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
Der Name eines vorhandenen geschlossen Datenbank. Dies kann ein vollständiger Pfad und Dateiname sein, z. b. "C:\\\MyDB. MDB ". Wenn der Dateiname eine Erweiterung verfügt, müssen Sie es angeben. Wenn Ihr Netzwerk die Uniform Naming Convention (UNC) unterstützt, können Sie auch einen Netzwerkpfad angeben, z. b. "\\\\\\\myserver\\\meinefreigabe\\\meindir\\\MyDB. MDB ". (Doppelte umgekehrte Schrägstriche sind in den Pfad Zeichenfolgen erforderlich, da "\\C++ " das Escapezeichen ist.)

*lpszdestname*<br/>
Der vollständige Pfad der komprimierten Datenbank, die Sie erstellen. Sie können auch einen Netzwerkpfad wie *lpszsrcname*angeben. Sie können das *lpszdestname* -Argument nicht verwenden, um die gleiche Datenbankdatei wie *lpszsrcname*anzugeben.

*lpszpassword*<br/>
Ein Kennwort verwendet, wenn Sie eine kennwortgeschützte Datenbank komprimiert werden sollen. Beachten Sie Folgendes: Wenn Sie die-Version von `CompactDatabase` verwenden, die ein Kennwort annimmt, müssen Sie alle Parameter angeben. Da es sich hierbei um einen Connect-Parameter handelt, müssen Sie wie folgt eine spezielle Formatierung ausführen:; Pwd = *lpszpassword*. Zum Beispiel:; PWD = "Zufrieden". (Das vorangestellte Semikolon ist erforderlich.)

*lpszlocale*<br/>
Ein Zeichen folgen Ausdruck, mit dem die Sortierreihenfolge zum Erstellen von *lpszdestname*angegeben wird. Wenn Sie dieses Argument weglassen, indem Sie den Standardwert `dbLangGeneral` (siehe unten) akzeptieren, ist das Gebiets Schema der neuen Datenbank mit dem der alten Datenbank identisch. Dabei sind folgende Werte möglich:

- `dbLangGeneral` Englisch, Deutsch, Französisch, Portugiesisch, Italienisch und modern Spanisch

- `dbLangArabic` Arabisch

- `dbLangCyrillic` Russisch

- `dbLangCzech` Tschechisch

- `dbLangDutch` Niederländisch

- `dbLangGreek` Griechisch

- `dbLangHebrew` Hebräisch

- `dbLangHungarian` Ungarisch

- `dbLangIcelandic` Isländisch

- `dbLangNordic` Nordische Sprachen (nur Microsoft Jet-Datenbank-Engine, Version 1,0)

- `dbLangNorwdan` Norwegisch und Dänisch

- `dbLangPolish` Polnisch

- traditionelles Spanisch `dbLangSpanish`

- `dbLangSwedfin` Swedish und Finnisch

- `dbLangTurkish` Türkisch

*noptions*<br/>
Gibt eine oder mehrere Optionen für die Zieldatenbank *lpszdestname*an. Wenn Sie dieses Argument weglassen, indem Sie den Standardwert akzeptieren, weist *lpszdestname* dieselbe Verschlüsselung und dieselbe Version wie *lpszsrcname*auf. Sie können die Option `dbEncrypt` oder `dbDecrypt` mit einer der Versions Optionen kombinieren, indem Sie den bitweisen OR-Operator verwenden. Mögliche Werte, die angeben, einem Datenbankformat, nicht in einer Datenbank-Engine-Version, sind:

- `dbEncrypt` die Datenbank während der Komprimierung zu verschlüsseln.

- `dbDecrypt` die Datenbank während der Komprimierung zu entschlüsseln.

- `dbVersion10` erstellen Sie eine Datenbank, die während der Komprimierung die Microsoft Jet-Datenbank-Engine-Version 1,0 verwendet.

- `dbVersion11` erstellen Sie eine Datenbank, die während der Komprimierung die Microsoft Jet-Datenbank-Engine-Version 1,1 verwendet.

- `dbVersion20` erstellen Sie eine Datenbank, die während der Komprimierung die Microsoft Jet-Datenbank-Engine-Version 2,0 verwendet.

- `dbVersion30` erstellen Sie eine Datenbank, die während der Komprimierung die Microsoft Jet-Datenbank-Engine-Version 3,0 verwendet.

Sie können `dbEncrypt` oder `dbDecrypt` im options-Argument verwenden, um anzugeben, ob die Datenbank verschlüsselt oder entschlüsselt werden soll, wenn Sie komprimiert wird. Wenn Sie eine Verschlüsselungs Konstante weglassen oder sowohl `dbDecrypt` als auch `dbEncrypt`einschließen, weist *lpszdestname* dieselbe Verschlüsselung wie *lpszsrcname*auf. Sie können eine der Konstanten Version im Optionsargument verwenden, um die Version des Datenformats für die komprimierte Datenbank anzugeben. Diese Konstante wirkt sich nur auf die Version des Datenformats von *lpszdestname*aus. Sie können nur eine Versionskonstante angeben. Wenn Sie eine Versions Konstante weglassen, hat *lpszdestname* dieselbe Version wie *lpszsrcname*. Sie können *lpszdestname* nur in eine Version komprimieren, die gleich oder später ist als *lpszsrcname*.

> [!CAUTION]
>  Wenn eine Datenbank nicht verschlüsselt ist, kann, auch wenn Sie Benutzername und Kennwort-Sicherheit implementieren, um direkt die binäre Datenträgerdatei lesen, aus der Datenbank besteht.

### <a name="remarks"></a>Hinweise

Wenn Sie Daten in einer Datenbank ändern, wird die Datenbankdatei kann fragmentiert werden, und verwenden mehr Speicherplatz als nötig. In regelmäßigen Abständen, sollten Sie Ihre Datenbank defragmentieren Sie die Datenbankdatei komprimieren. Die komprimierte Datenbank ist in der Regel kleiner. Sie können auch auswählen, um die Sortierreihenfolge, die Verschlüsselung oder die Version des Datenformats zu ändern, während Sie kopieren und komprimieren Sie die Datenbank.

> [!CAUTION]
>  Die `CompactDatabase` Member-Funktion konvertiert eine vollständige Microsoft Access-Datenbank nicht ordnungsgemäß von einer Version in eine andere. Es wird nur das Datenformat konvertiert. Microsoft Access-Objekte, wie Formulare und Berichte, werden nicht konvertiert. Allerdings werden die Daten ordnungsgemäß konvertiert.

> [!TIP]
>  Sie können auch `CompactDatabase` verwenden, um eine Datenbankdatei zu kopieren.

Weitere Informationen zum Komprimieren von Datenbanken finden Sie im Thema "CompactDatabase Method" in-DAO-Hilfe.

##  <a name="create"></a>CDaoWorkspace:: Create

Rufen Sie diese Member-Funktion auf, um ein neues DAO-Arbeitsbereichs Objekt zu erstellen und es dem MFC-`CDaoWorkspace` Objekt zuzuordnen.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszUserName,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parameter

*lpszname*<br/>
Eine Zeichenfolge mit bis zu 14 Zeichen, die der neue Arbeitsbereich-Objekt eindeutig bezeichnet. Sie müssen einen Namen angeben. Verwandte Informationen finden Sie im Thema "Name-Eigenschaft" in-DAO-Hilfe.

*lpszusername*<br/>
Der Benutzername des Besitzers des Arbeitsbereichs. Informationen zu den Anforderungen finden Sie unter dem *lpszdefaultuser* -Parameter der [setdefaultuser](#setdefaultuser) -Member-Funktion. Weitere Informationen finden Sie unter dem Thema "UserName-Eigenschaft" in-DAO-Hilfe.

*lpszpassword*<br/>
Das Kennwort für das neue Workspace-Objekt. Ein Kennwort kann bis zu 14 Zeichen lang sein und darf Zeichen mit Ausnahme von ASCII 0 (null). Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden. Verwandte Informationen finden Sie im Thema "Password-Eigenschaft" in-DAO-Hilfe.

### <a name="remarks"></a>Hinweise

Der gesamte Erstellungsvorgang ist:

1. Erstellen Sie ein [CDaoWorkspace](#cdaoworkspace) -Objekt.

1. Rufen Sie die `Create` Member-Funktion des-Objekts auf, um den zugrunde liegenden DAO-Arbeitsbereich Geben Sie einen Arbeitsbereichsnamen ein.

1. Rufen Sie optional [Append](#append) auf, wenn Sie den Arbeitsbereich der Arbeitsbereichs Sammlung der Datenbank-Engine hinzufügen möchten. Sie können mit dem Arbeitsbereich arbeiten, ohne es anzuhängen.

Nach dem `Create`-Befehl befindet sich das Arbeitsbereichs Objekt in einem geöffneten Zustand und kann verwendet werden. Nach `Create`werden `Open` nicht mehr aufgerufen. Sie können `Create` nicht abrufen, wenn der Arbeitsbereich bereits in der Arbeitsbereichs Sammlung vorhanden ist. `Create` initialisiert die Datenbank-Engine, wenn Sie nicht bereits für die Anwendung initialisiert wurde.

##  <a name="getdatabasecount"></a>CDaoWorkspace:: getdatabasecount

Rufen Sie diese Memberfunktion zum Abrufen der Anzahl der DAO-Datenbankobjekte in der datenbankauflistung des Arbeitsbereichs – die Anzahl der geöffneten Datenbanken im Arbeitsbereich.

```
short GetDatabaseCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der geöffneten Datenbanken im Arbeitsbereich.

### <a name="remarks"></a>Hinweise

`GetDatabaseCount` ist nützlich, wenn Sie alle definierten Datenbanken in der Datenbanksammlung des Arbeitsbereichs durchlaufen müssen. Informationen zu einer bestimmten Datenbank in der Sammlung finden Sie unter [getDatabaseInfo](#getdatabaseinfo). Die typische Verwendung besteht darin, `GetDatabaseCount` für die Anzahl der geöffneten Datenbanken aufzurufen und diese Zahl dann als Schleifenindex für wiederholte Aufrufe `GetDatabaseInfo`zu verwenden.

##  <a name="getdatabaseinfo"></a>CDaoWorkspace:: getdatabaseingefo

Rufen Sie diese Memberfunktion, um verschiedene Arten von Informationen über eine Datenbank geöffnet, in dem Arbeitsbereich zu erhalten.

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
Der nullbasierte Index des Datenbankobjekts in der datenbankauflistung des Arbeitsbereichs, für die Suche nach Index.

*dbinfo*<br/>
Ein Verweis auf ein [cdaodatabaseinfo](../../mfc/reference/cdaodatabaseinfo-structure.md) -Objekt, das die angeforderten Informationen zurückgibt.

*dwinfooptions*<br/>
Optionen, die angeben, welche Informationen über die Datenbank abgerufen. Die verfügbaren Optionen sind hier aufgeführt, zusammen mit der sie die Funktion zurückgibt verursachen:

- AFX_DAO_PRIMARY_INFO (Standard) Namen aktualisiert werden kann, Transaktionen

- Primäre AFX_DAO_SECONDARY_INFO Informationen plus: Abfragetimeout Version Reihenfolge sortieren

- AFX_DAO_ALL_INFO primären und sekundären Informationen plus: Verbinden

*lpszname*<br/>
Der Name des Datenbankobjekts, für die Suche anhand des Namens. Der Name ist eine Zeichenfolge mit bis zu 14 Zeichen, die der neue Arbeitsbereich-Objekt eindeutig bezeichnet.

### <a name="remarks"></a>Hinweise

Eine Version der Funktion können Sie eine Datenbank über einen Index zu suchen. Die andere Version können Sie eine Datenbank anhand des Namens zu suchen.

Eine Beschreibung der Informationen, die in *dbinfo*zurückgegeben werden, finden Sie in der [cdaodatabaseinfo](../../mfc/reference/cdaodatabaseinfo-structure.md) -Struktur. Diese Struktur enthält Member, die den in der Beschreibung von *dwinfooptions*aufgeführten Elementen der oben aufgeführten Informationen entsprechen. Wenn Sie die Informationen auf einer Ebene anfordern, erhalten Sie Informationen für alle vorherigen Ebenen sowie an.

##  <a name="getinipath"></a>CDaoWorkspace:: getinipath

Rufen Sie diese Memberfunktion um den Speicherort der Microsoft Jet-Datenbank-Engine-Initialisierung-Einstellungen in der Windows-Registrierung abzurufen.

```
static CString PASCAL GetIniPath();
```

### <a name="return-value"></a>Rückgabewert

Eine [CString](../../atl-mfc-shared/reference/cstringt-class.md) , die den Registrierungs Speicherort enthält.

### <a name="remarks"></a>Hinweise

Sie können den Speicherort zum Abrufen von Informationen zu Einstellungen für die Datenbank-Engine verwenden. Die zurückgegebenen Informationen ist tatsächlich auf den Namen der Unterschlüssel der Registrierung.

Weitere Informationen finden Sie unter den Themen "IniPath Property" und "Anpassen von Windows-Registrierung Einstellungen für den Datenzugriff" in-DAO-Hilfe.

##  <a name="getisolateodbctrans"></a>CDaoWorkspace:: getisolateodbctrans

Rufen Sie diese Memberfunktion um den aktuellen Wert der Eigenschaft DAO IsolateODBCTrans für den Arbeitsbereich zu erhalten.

```
BOOL GetIsolateODBCTrans();
```

### <a name="return-value"></a>Rückgabewert

Legen Sie ungleich NULL, wenn es sich bei ODBC-Transaktionen isoliert sind; andernfalls 0.

### <a name="remarks"></a>Hinweise

In einigen Situationen müssen Sie mehrere gleichzeitige Transaktionen mit ausstehender für eine ODBC-Datenbank haben. Zu diesem Zweck müssen Sie einen separaten Arbeitsbereich für jede Transaktion zu öffnen. Bedenken Sie, dass zwar jeden Arbeitsbereich eine eigene ODBC-Verbindung mit der Datenbank verfügen kann, dies die Systemleistung verlangsamt. Da der Transaktionsisolation nicht normal erforderlich ist, werden die ODBC-Verbindungen von mehreren Workspace-Objekte, die vom gleichen Benutzer geöffnet standardmäßig freigegeben.

Einige ODBC-Server, z. B. Microsoft SQL Server zulassen nicht gleichzeitige Transaktionen auf eine einzelne Verbindung. Wenn Sie mehr als eine Transaktion zu einem Zeitpunkt steht aus für eine Datenbank verfügen müssen, legen Sie die IsolateODBCTrans-Eigenschaft auf "true" für jeden Arbeitsbereich, sobald Sie es öffnen. Dies erzwingt, dass eine separate ODBC-Verbindung für jeden Arbeitsbereich.

Verwandte Informationen finden Sie im Thema "IsolateODBCTrans-Eigenschaft" in-DAO-Hilfe.

##  <a name="getlogintimeout"></a>CDaoWorkspace:: GetLoginTimeout

Rufen Sie diese Memberfunktion um den aktuellen Wert der DAO-LoginTimeout-Eigenschaft für den Arbeitsbereich zu erhalten.

```
static short PASCAL GetLoginTimeout();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Sekunden, bevor ein Fehler auftritt, wenn Sie versuchen, eine ODBC-Datenbank anmelden.

### <a name="remarks"></a>Hinweise

Dieser Wert stellt die Anzahl der Sekunden, bevor ein Fehler auftritt, wenn Sie versuchen, eine ODBC-Datenbank anmelden. Die Standardeinstellung für das Anmeldungstimeout beträgt 20 Sekunden. Beim Anmeldungstimeout auf 0 festgelegt ist, wird kein Timeout erfolgt, und die Kommunikation mit der Datenquelle reagiert möglicherweise nicht.

Wenn Sie versuchen, die mit einer ODBC-Datenbank, z. B. Microsoft SQL Server, melden Sie sich möglicherweise die Verbindung aufgrund von Netzwerkfehlern oder weil der Server nicht ausgeführt wird. Anstatt zu warten, der Standardwert 20 Sekunden eine Verbindung herstellen, können Sie angeben, wie lange die Datenbank-Engine wartet, bevor er einen Fehler erzeugt. Anmeldung mit dem Server wird implizit als Teil einer Reihe verschiedener Ereignisse, wie z. B. das Ausführen einer Abfrage in einer externen Server-Datenbank.

Verwandte Informationen finden Sie im Thema "LoginTimeout-Eigenschaft" in-DAO-Hilfe.

##  <a name="getname"></a>CDaoWorkspace:: GetName

Mit dieser Member-Funktion können Sie den benutzerdefinierten Namen des DAO-Arbeitsbereichs Objekts abrufen, das dem `CDaoWorkspace`-Objekt zugrunde liegt.

```
CString GetName();
```

### <a name="return-value"></a>Rückgabewert

Ein [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Wert, der den benutzerdefinierten Namen des DAO-Arbeitsbereichs Objekts enthält.

### <a name="remarks"></a>Hinweise

Der Name ist nützlich für den Zugriff auf die DAO-Workspace-Objekt in der Datenbank-Engine-arbeitsbereicheauflistung nach Namen.

Verwandte Informationen finden Sie im Thema "Name-Eigenschaft" in-DAO-Hilfe.

##  <a name="getusername"></a>CDaoWorkspace:: GetUserName

Rufen Sie diese Memberfunktion zum Abrufen des Namens des Besitzers des Arbeitsbereichs.

```
CString GetUserName();
```

### <a name="return-value"></a>Rückgabewert

Ein [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Wert, der den Besitzer des Arbeitsbereichs Objekts darstellt.

### <a name="remarks"></a>Hinweise

Rufen Sie zum Abrufen oder Festlegen der Berechtigungen für Besitzer des Arbeitsbereichs, DAO direkt, um die Einstellung der Eigenschaft Berechtigungen zu überprüfen. Dadurch wird bestimmt, welche Berechtigungen dieser Benutzer besitzt. Um mit den Berechtigungen zu arbeiten, benötigen Sie ein SYSTEM aus. MDA-Datei.

Weitere Informationen zum direkten Aufrufen von DAO finden [Sie im technischen Hinweis 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md). Weitere Informationen finden Sie unter dem Thema "UserName-Eigenschaft" in-DAO-Hilfe.

##  <a name="getversion"></a>CDaoWorkspace:: GetVersion

Rufen Sie diese Memberfunktion zum Ermitteln der Version von Microsoft Jet-Datenbank-Engine verwendet.

```
static CString PASCAL GetVersion();
```

### <a name="return-value"></a>Rückgabewert

Ein [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Wert, der die Version der Datenbank-Engine angibt, die dem Objekt zugeordnet ist.

### <a name="remarks"></a>Hinweise

Der zurückgegebene Wert stellt die Versionsnummer im Format "Hauptversion.Nebenversion"; z. B. "3.0". Die Versionsnummer des Produkts (z. B. "3.0") besteht aus der Versionsnummer (3), einem Punkt und die Versionsnummer (0).

Verwandte Informationen finden Sie im Thema "Version-Eigenschaft" in-DAO-Hilfe.

##  <a name="getworkspacecount"></a>CDaoWorkspace:: getworkspacecount

Rufen Sie diese Memberfunktion zum Abrufen der Anzahl der DAO-Workspace-Objekte in der Datenbank-Engine-Arbeitsbereiche-Auflistung.

```
short GetWorkspaceCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der geöffneten Arbeitsbereiche in der Auflistung der Arbeitsbereiche.

### <a name="remarks"></a>Hinweise

Diese Zahl umfasst keine öffnen Arbeitsbereiche nicht auf die Auflistung angefügt. `GetWorkspaceCount` ist nützlich, wenn Sie alle definierten Arbeitsbereiche in der Arbeitsbereiche-Auflistung durchlaufen müssen. Informationen zu einem bestimmten Arbeitsbereich in der Sammlung finden Sie unter [GetWorkspaceInfo](#getworkspaceinfo). Die typische Verwendung besteht darin, `GetWorkspaceCount` für die Anzahl der geöffneten Arbeitsbereiche aufzurufen und diese Zahl dann als Schleifenindex für wiederholte Aufrufe `GetWorkspaceInfo`zu verwenden.

##  <a name="getworkspaceinfo"></a>CDaoWorkspace:: getworkspaceingefo

Rufen Sie diese Memberfunktion, um verschiedene Arten von Informationen über einen Arbeitsbereich öffnen, in der Sitzung zu erhalten.

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
Der nullbasierte Index des Datenbankobjekts in der Auflistung Arbeitsbereiche für die Suche nach Index.

*wkspcinfo*<br/>
Ein Verweis auf ein [cdaoworkspaceinfo](../../mfc/reference/cdaoworkspaceinfo-structure.md) -Objekt, das die angeforderten Informationen zurückgibt.

*dwinfooptions*<br/>
Optionen, die angeben, welche Informationen über den Arbeitsbereich abrufen. Die verfügbaren Optionen sind hier aufgeführt, zusammen mit der sie die Funktion zurückgibt verursachen:

- Name der AFX_DAO_PRIMARY_INFO (Standard)

- Primäre AFX_DAO_SECONDARY_INFO Informationen plus: Benutzername

- AFX_DAO_ALL_INFO primären und sekundären Informationen plus: ODBCTrans zu isolieren

*lpszname*<br/>
Der Name des Workspace-Objekts, für die Suche anhand des Namens. Der Name ist eine Zeichenfolge mit bis zu 14 Zeichen, die der neue Arbeitsbereich-Objekt eindeutig bezeichnet.

### <a name="remarks"></a>Hinweise

Eine Beschreibung der Informationen, die in *wkspcinfo*zurückgegeben werden, finden Sie in der [cdaoworkspaceinfo](../../mfc/reference/cdaoworkspaceinfo-structure.md) -Struktur. Diese Struktur enthält Member, die den in der Beschreibung von *dwinfooptions*aufgeführten Elementen der oben aufgeführten Informationen entsprechen. Wenn Sie die Informationen auf einer Ebene anfordern, erhalten Sie Informationen zu vorherigen Ebenen sowie an.

##  <a name="idle"></a>CDaoWorkspace:: Leerlauf

Wenden Sie `Idle` an, um der Datenbank-Engine die Möglichkeit zu bieten, Hintergrundaufgaben auszuführen, die aufgrund intensiver Datenverarbeitung möglicherweise nicht auf dem neuesten Stand sind.

```
static void PASCAL Idle(int nAction = dbFreeLocks);
```

### <a name="parameters"></a>Parameter

*naktionsmeldung*<br/>
Aktion bei der Verarbeitung im Leerlauf ausgeführt werden soll. Zurzeit ist die einzige gültige Aktion `dbFreeLocks`.

### <a name="remarks"></a>Hinweise

Dies ist häufig in mehreren Benutzern, Multitasking-Umgebungen, in dem ist nicht genügend Hintergrundverarbeitungszeit, um alle Datensätze in einem Recordset aktuell zu halten.

> [!NOTE]
>  Das Aufrufen von `Idle` ist bei Datenbanken, die mit Version 3,0 der Microsoft Jet-Datenbank-Engine erstellt wurden, nicht erforderlich Verwenden Sie `Idle` nur für Datenbanken, die mit früheren Versionen erstellt wurden.

In der Regel wird lesen, Sperren entfernt werden, und Daten im lokalen Dynaset eines assistentartigen Recordset-Objekte nur aktualisiert, wenn keine anderen Aktionen (einschließlich mausbewegungen) auftreten. Wenn Sie `Idle`regelmäßig aufzurufen, stellen Sie der Datenbank-Engine Zeit zum Auffangen von Hintergrund Verarbeitungsaufgaben bereit, indem Sie nicht benötigte Lese Sperren freigeben. Die Angabe der `dbFreeLocks` Konstante als Argument verzögert die Verarbeitung, bis alle Lese Sperren freigegeben wurden.

Diese Memberfunktion ist in Umgebungen mit nur einem Benutzer nicht erforderlich, es sei denn, die mehrere Instanzen einer Anwendung ausgeführt werden. Die `Idle` Member-Funktion kann die Leistung in einer mehr Benutzerumgebung verbessern, da die Datenbank-Engine zwingt, Daten auf den Datenträger zu leeren und Sperren für den Arbeitsspeicher freizugeben. Sie können auch Lesesperren freigeben, dazu die Vorgängen Teil einer Transaktion.

Verwandte Informationen finden Sie im Thema "Im Leerlauf Method" in-DAO-Hilfe.

##  <a name="isopen"></a>CDaoWorkspace:: IsOpen

Rufen Sie diese Member-Funktion auf, um zu bestimmen, ob das `CDaoWorkspace` Objekt geöffnet ist – d. h. ob das MFC-Objekt durch einen [Open](#open) -oder [Create](#create)-Befehl initialisiert wurde.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn die Workspace-Objekt geöffnet ist; andernfalls 0.

### <a name="remarks"></a>Hinweise

Sie können keine der Memberfunktionen Funktionen eines Arbeitsbereichs aufrufen, die im geöffneten Zustand ist.

##  <a name="m_pdaoworkspace"></a>CDaoWorkspace:: m_pDAOWorkspace

Ein Zeiger auf das zugrunde liegende DAO-Workspace-Objekt.

### <a name="remarks"></a>Hinweise

Verwenden Sie dieses Datenelement aus, wenn Sie den Zugriff auf das zugrunde liegende DAO-Objekt weiterleiten müssen. Sie können die DAO-Schnittstellen des Objekts über diesen Zeiger aufrufen.

Weitere Informationen zum direkten Zugriff auf DAO-Objekte finden [Sie im technischen Hinweis 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

##  <a name="open"></a>CDaoWorkspace:: Open

Explizit öffnet ein Workspace-Objekt, das mit DAO Standard-Arbeitsbereich verknüpft ist.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Parameter

*lpszname*<br/>
Der Name des Objekts die DAO-Arbeitsbereich zu öffnen, eine Zeichenfolge mit bis zu 14 Zeichen, die den Arbeitsbereich eindeutig bezeichnet. Akzeptieren Sie den Standardwert NULL, um die Standard-Arbeitsbereich explizit zu öffnen. Informationen zu den Benennungs Anforderungen finden Sie unter dem *lpszname* -Parameter für [Create](#create). Verwandte Informationen finden Sie im Thema "Name-Eigenschaft" in-DAO-Hilfe.

### <a name="remarks"></a>Hinweise

Nachdem Sie ein `CDaoWorkspace` Objekt erstellt haben, können Sie diese Member-Funktion für eine der folgenden Aktionen verwenden:

- Öffnen Sie explizit die Standard-Arbeitsbereich. Übergeben Sie für *lpszname*den Wert NULL.

- Öffnen Sie ein vorhandenes `CDaoWorkspace` Objekt, ein Mitglied der Workspaces-Auflistung, nach Namen. Übergeben Sie einen gültigen Namen für ein vorhandenes Workspace-Objekt.

`Open` versetzt das Arbeitsbereichs Objekt in einen geöffneten Zustand und initialisiert die Datenbank-Engine auch, wenn Sie nicht bereits für die Anwendung initialisiert wurde.

Obwohl viele `CDaoWorkspace` Member-Funktionen nur aufgerufen werden können, nachdem der Arbeitsbereich geöffnet wurde, sind die folgenden Member-Funktionen, die auf der Datenbank-Engine ausgeführt werden, C++ nach der Erstellung des-Objekts, aber vor einem Aufruf von `Open`verfügbar:

||||
|-|-|-|
|[Erstellen](#create)|[GetVersion](#getversion)|[Setdefaultuser](#setdefaultuser)|
|[Getinipath](#getinipath)|[Idle](#idle)|[Setinipath](#setinipath)|
|[GetLoginTimeout](#getlogintimeout)|[SetDefaultPassword](#setdefaultpassword)|[SetLoginTimeout](#setlogintimeout)|

##  <a name="repairdatabase"></a>CDaoWorkspace:: repairren Database

Rufen Sie diese Memberfunktion auf, wenn Sie versuchen, eine beschädigte Datenbank zu reparieren, die auf die Microsoft Jet-Datenbank-Engine zugreift müssen.

```
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parameter

*lpszname*<br/>
Der Pfad und Dateiname für eine vorhandene Microsoft Jet-Engine Datenbankdatei. Wenn Sie den Pfad weglassen, wird nur das aktuelle Verzeichnis durchsucht. Wenn Ihr System die Uniform Naming Convention (UNC) unterstützt, können Sie auch einen Netzwerkpfad angeben, z. b.: "\\\\\\\meinserver\\\meinefreigabe\\\meindir\\\MyDB. MDB ". (Doppelte umgekehrte Schrägstriche sind in der Pfad Zeichenfolge erforderlich, da "\\C++ " das Escapezeichen ist.)

### <a name="remarks"></a>Hinweise

Sie müssen die von *lpszname* angegebene Datenbank schließen, bevor Sie Sie reparieren. In einer mehr Benutzerumgebung kann *lpszname* nicht von anderen Benutzern geöffnet werden, während Sie Sie reparieren. Wenn *lpszname* nicht geschlossen ist oder für die ausschließliche Verwendung nicht verfügbar ist, tritt ein Fehler auf.

Diese Memberfunktion versucht, eine Datenbank zu reparieren, die von einer unvollständigen Schreibvorgang als möglicherweise fehlerhaft gekennzeichnet wurde. Dies kann auftreten, wenn eine Anwendung mithilfe der Microsoft Jet-Datenbank-Engine aufgrund eines Problems Power Netzwerkausfall oder einem Hardware unerwartet geschlossen ist. Wenn Sie den Vorgang abschließen und die Funktion zum [Schließen](../../mfc/reference/cdaodatabase-class.md#close) des Members aufzurufen, oder Sie die Anwendung auf die übliche Weise beenden, wird die Datenbank nicht als möglicherweise beschädigt markiert.

> [!NOTE]
>  Nach dem Reparieren einer Datenbank ist es auch ratsam, Sie mit der Element Funktion " [CompactDatabase](#compactdatabase) " zu komprimieren, um die Datei zu defragmentieren und Speicherplatz auf dem Datenträger wiederherzustellen.

Weitere Informationen zum Reparieren von Datenbanken finden Sie im Thema "RepairDatabase Method" in-DAO-Hilfe.

##  <a name="rollback"></a>CDaoWorkspace:: Rollback

Rufen Sie diese Memberfunktion, um die aktuelle Transaktion zu beenden und alle Datenbanken in den Arbeitsbereich in ihren Zustand wiederherstellen, bevor die Transaktion gestartet wurde.

```
void Rollback();
```

### <a name="remarks"></a>Hinweise

> [!CAUTION]
>  In einem Arbeitsbereichsobjekt Transaktionen sind immer global für den Arbeitsbereich und sind nicht nur eine Datenbank oder ein Recordset auf. Wenn Sie Vorgänge für mehrere Datenbanken oder Recordsets innerhalb einer Arbeitsbereichs Transaktion ausführen, stellt `Rollback` alle Vorgänge für alle diese Datenbanken und Recordsets wieder her.

Wenn Sie ein Workspace-Objekt schließen, ohne zu speichern oder ein Rollback aller anstehenden Transaktionen, werden die Transaktionen automatisch zurückgesetzt. Wenn Sie [CommitTrans](#committrans) oder `Rollback` aufrufen, ohne zuerst [BeginTrans](#begintrans)aufzurufen, tritt ein Fehler auf.

> [!NOTE]
>  Wenn Sie eine Transaktion starten, zeichnet die Datenbank-Engine die Vorgänge in einer Datei, in dem durch die Umgebungsvariable "TEMP" auf der Arbeitsstation angegebenen Verzeichnis gespeichert. Wenn die Transaktionsprotokoll Datei den verfügbaren Speicher auf dem temporären Laufwerk erschöpft, bewirkt die Datenbank-Engine, dass MFC eine `CDaoException` auslöst (DAO-Fehler 2004). Wenn Sie an diesem Punkt `CommitTrans`aufgerufen haben, wird für eine unbestimmte Anzahl von Vorgängen ein Commit ausgeführt, aber die restlichen nicht abgeschlossenen Vorgänge gehen verloren, und der Vorgang muss neu gestartet werden. Der Aufruf von `Rollback` gibt das Transaktionsprotokoll frei und führt ein Rollback aller Vorgänge in der Transaktion aus.

##  <a name="setdefaultpassword"></a>CDaoWorkspace:: SetDefaultPassword

Rufen Sie diese Memberfunktion, um das Standardkennwort festzulegen, das die Datenbank-Engine verwendet wird, wenn ein Workspace-Objekt ohne ein bestimmtes Kennwort erstellt wird.

```
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parameter

*lpszpassword*<br/>
Das Standardkennwort. Ein Kennwort kann bis zu 14 Zeichen lang sein und darf Zeichen mit Ausnahme von ASCII 0 (null). Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden.

### <a name="remarks"></a>Hinweise

Das Standardkennwort, das Sie festlegen, gilt für neue Arbeitsbereiche, die Sie nach dem Aufruf zu erstellen. Wenn Sie nachfolgende Arbeitsbereiche erstellen, müssen Sie im [Create](#create) -Befehl kein Kennwort angeben.

So verwenden Sie diese Memberfunktion auf:

1. Erstellen Sie ein `CDaoWorkspace` Objekt, aber `Create`nicht aufzurufen.

1. Rufen Sie `SetDefaultPassword` und, wenn Sie möchten, [setdefaultuser](#setdefaultuser)auf.

1. Ruft `Create` für dieses Arbeitsbereichs Objekt oder nachfolgende, ohne Angabe eines Kennworts auf.

In der Standardeinstellung die DefaultUser-Eigenschaft auf "Admin" festgelegt ist und die Eigenschaft "DefaultPassword" auf eine leere Zeichenfolge festgelegt ist ("").

Weitere Informationen zur Sicherheit finden Sie im Thema "Berechtigungen Property" in-DAO-Hilfe. Weitere Informationen finden Sie unter den Themen "DefaultPassword Property" und "DefaultUser-Eigenschaft" in-DAO-Hilfe.

##  <a name="setdefaultuser"></a>CDaoWorkspace:: setdefaultuser

Rufen Sie diese Memberfunktion um den Standardnamen für den Benutzer festzulegen, den die Datenbank-Engine verwendet wird, wenn ein Workspace-Objekt ohne einen bestimmten Benutzernamen erstellt wird.

```
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```

### <a name="parameters"></a>Parameter

*lpszdefaultuser*<br/>
Der Standardbenutzername. Ein Benutzername kann 1-20 Zeichen lang sein und alphabetische Zeichen enthalten. Sonderzeichen, Zahlen, Leerzeichen und Symbole mit Ausnahme von: "(Anführungszeichen),/(Schrägstrich), \ (umgekehrter Schrägstrich), \[ \] (eckige Klammern),: ( &#124; Doppelpunkt), (Pipe), \< (kleiner-als-Zeichen), > (größer als Vorzeichen), + (Pluszeichen), = (Gleichheitszeichen), (Semikolon),, (Komma), (Fragezeichen), \* (Sternchen), führende Leerzeichen und Steuerzeichen (ASCII 00 bis ASCII 31). Weitere Informationen finden Sie unter dem Thema "UserName-Eigenschaft" in-DAO-Hilfe.

### <a name="remarks"></a>Hinweise

Der Standardname für den Benutzer, die Sie festlegen, gilt für neue Arbeitsbereiche, die Sie nach dem Aufruf zu erstellen. Wenn Sie nachfolgende Arbeitsbereiche erstellen, müssen Sie im [Create](#create) -Befehl keinen Benutzernamen angeben.

So verwenden Sie diese Memberfunktion auf:

1. Erstellen Sie ein `CDaoWorkspace` Objekt, aber `Create`nicht aufzurufen.

1. Aufrufen von `SetDefaultUser` und, wenn Sie möchten, [SetDefaultPassword](#setdefaultpassword).

1. Ruft `Create` für dieses Arbeitsbereichs Objekt oder nachfolgende auf, ohne einen Benutzernamen anzugeben.

In der Standardeinstellung die DefaultUser-Eigenschaft auf "Admin" festgelegt ist und die Eigenschaft "DefaultPassword" auf eine leere Zeichenfolge festgelegt ist ("").

Weitere Informationen finden Sie unter den Themen "DefaultUser Property" und "DefaultPassword-Eigenschaft" in-DAO-Hilfe.

##  <a name="setinipath"></a>CDaoWorkspace:: setinipath

Rufen Sie diese Memberfunktion zum Angeben des Speicherorts der Windows-registrierungseinstellungen für das Microsoft Jet-Datenbankmodul.

```
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```

### <a name="parameters"></a>Parameter

*lpszregistrysubkey*<br/>
Eine Zeichenfolge, die mit dem Namen der einen Windows-Registrierungsunterschlüssel für den Speicherort der Einstellungen für Microsoft Jet-Datenbank-Engine oder für installierbare ISAM-Datenbanken erforderlichen Parameter.

### <a name="remarks"></a>Hinweise

Wenden Sie `SetIniPath` nur an, wenn Sie spezielle Einstellungen angeben müssen. Weitere Informationen finden Sie im Thema "IniPath-Eigenschaft" in-DAO-Hilfe.

> [!NOTE]
>  Ruft während der Anwendungs Installation `SetIniPath` auf, nicht bei der Ausführung der Anwendung. `SetIniPath` müssen vor dem Öffnen von Arbeitsbereichen, Datenbanken oder Recordsets aufgerufen werden. Andernfalls löst MFC eine Ausnahme aus.

Sie können diesen Mechanismus verwenden, auf die Datenbank-Engine mit vom Benutzer bereitgestellte registrierungseinstellungen konfigurieren zu können. Der Gültigkeitsbereich dieses Attributs ist Ihre Anwendung auf und kann nicht geändert werden, ohne Ihre Anwendung neu zu starten.

##  <a name="setisolateodbctrans"></a>CDaoWorkspace:: "abtisolateodbctrans"

Rufen Sie diese Memberfunktion um den Wert der Eigenschaft DAO IsolateODBCTrans für den Arbeitsbereich festzulegen.

```
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```

### <a name="parameters"></a>Parameter

*bisolateodbctrans*<br/>
Übergeben Sie "true", sollten Sie beginnen, Isolieren von ODBC-Transaktionen. Übergeben Sie "false", sollten Sie isolieren ODBC-Transaktionen zu beenden.

### <a name="remarks"></a>Hinweise

In einigen Situationen müssen Sie mehrere gleichzeitige Transaktionen mit ausstehender für eine ODBC-Datenbank haben. Zu diesem Zweck müssen Sie einen separaten Arbeitsbereich für jede Transaktion zu öffnen. Obwohl jeder Arbeitsbereich eine eigene ODBC-Verbindung mit der Datenbank verfügen kann, wird dadurch die Leistung des Systems. Da der Transaktionsisolation nicht normal erforderlich ist, werden die ODBC-Verbindungen von mehreren Workspace-Objekte, die vom gleichen Benutzer geöffnet standardmäßig freigegeben.

Einige ODBC-Server, z. B. Microsoft SQL Server zulassen nicht gleichzeitige Transaktionen auf eine einzelne Verbindung. Wenn Sie mehr als eine Transaktion zu einem Zeitpunkt steht aus für eine Datenbank verfügen müssen, legen Sie die IsolateODBCTrans-Eigenschaft auf "true" für jeden Arbeitsbereich, sobald Sie es öffnen. Dies erzwingt, dass eine separate ODBC-Verbindung für jeden Arbeitsbereich.

##  <a name="setlogintimeout"></a>CDaoWorkspace:: setLoginTimeout

Rufen Sie diese Memberfunktion um den Wert der DAO-LoginTimeout-Eigenschaft für den Arbeitsbereich festzulegen.

```
static void PASCAL SetLoginTimeout(short nSeconds);
```

### <a name="parameters"></a>Parameter

*nSekunden*<br/>
Die Anzahl der Sekunden, bevor ein Fehler auftritt, wenn Sie versuchen, eine ODBC-Datenbank anmelden.

### <a name="remarks"></a>Hinweise

Dieser Wert stellt die Anzahl der Sekunden, bevor ein Fehler auftritt, wenn Sie versuchen, eine ODBC-Datenbank anmelden. Die Standardeinstellung für das Anmeldungstimeout beträgt 20 Sekunden. Beim Anmeldungstimeout auf 0 festgelegt ist, wird kein Timeout erfolgt, und die Kommunikation mit der Datenquelle reagiert möglicherweise nicht.

Wenn Sie versuchen, die mit einer ODBC-Datenbank, z. B. Microsoft SQL Server, melden Sie sich möglicherweise die Verbindung aufgrund von Netzwerkfehlern oder weil der Server nicht ausgeführt wird. Anstatt zu warten, der Standardwert 20 Sekunden eine Verbindung herstellen, können Sie angeben, wie lange die Datenbank-Engine wartet, bevor er einen Fehler erzeugt. Anmelden an den Server wird implizit als Teil einer Reihe verschiedener Ereignisse, wie z. B. das Ausführen einer Abfrage in einer externen Server-Datenbank. Der Timeoutwert wird durch die aktuelle Einstellung der LoginTimeout-Eigenschaft bestimmt.

Verwandte Informationen finden Sie im Thema "LoginTimeout-Eigenschaft" in-DAO-Hilfe.

## <a name="see-also"></a>Siehe auch

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase-Klasse](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset-Klasse](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef-Klasse](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef-Klasse](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoException-Klasse](../../mfc/reference/cdaoexception-class.md)
