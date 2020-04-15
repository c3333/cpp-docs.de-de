---
title: CFtpConnection-Klasse
ms.date: 08/29/2019
f1_keywords:
- CFtpConnection
- AFXINET/CFtpConnection
- AFXINET/CFtpConnection::CFtpConnection
- AFXINET/CFtpConnection::Command
- AFXINET/CFtpConnection::CreateDirectory
- AFXINET/CFtpConnection::GetCurrentDirectory
- AFXINET/CFtpConnection::GetCurrentDirectoryAsURL
- AFXINET/CFtpConnection::GetFile
- AFXINET/CFtpConnection::OpenFile
- AFXINET/CFtpConnection::PutFile
- AFXINET/CFtpConnection::Remove
- AFXINET/CFtpConnection::RemoveDirectory
- AFXINET/CFtpConnection::Rename
- AFXINET/CFtpConnection::SetCurrentDirectory
helpviewer_keywords:
- CFtpConnection [MFC], CFtpConnection
- CFtpConnection [MFC], Command
- CFtpConnection [MFC], CreateDirectory
- CFtpConnection [MFC], GetCurrentDirectory
- CFtpConnection [MFC], GetCurrentDirectoryAsURL
- CFtpConnection [MFC], GetFile
- CFtpConnection [MFC], OpenFile
- CFtpConnection [MFC], PutFile
- CFtpConnection [MFC], Remove
- CFtpConnection [MFC], RemoveDirectory
- CFtpConnection [MFC], Rename
- CFtpConnection [MFC], SetCurrentDirectory
ms.assetid: 5e3a0501-8893-49cf-a3d5-0628d8d6b936
ms.openlocfilehash: a1fe516869aa98cc291597211eee175ef591e45d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373775"
---
# <a name="cftpconnection-class"></a>CFtpConnection-Klasse

Verwaltet Ihre FTP-Verbindung zu einem Internetserver und ermöglicht die direkte Bearbeitung von Verzeichnissen und Dateien auf diesem Server.

## <a name="syntax"></a>Syntax

```
class CFtpConnection : public CInternetConnection
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFtpConnection::CFtpConnection](#cftpconnection)|Erstellt ein `CFtpConnection`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFtpConnection::Befehl](#command)|Sendet einen Befehl direkt an einen FTP-Server.|
|[CFtpConnection::CreateDirectory](#createdirectory)|Erstellt ein Verzeichnis auf dem Server.|
|[CFtpConnection::GetCurrentDirectory](#getcurrentdirectory)|Ruft das aktuelle Verzeichnis für diese Verbindung ab.|
|[CFtpConnection::GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)|Ruft das aktuelle Verzeichnis für diese Verbindung als URL ab.|
|[CFtpConnection::GetFile](#getfile)|Ruft eine Datei vom verbundenen Server ab|
|[CFtpConnection::OpenFile](#openfile)|Öffnet eine Datei auf dem verbundenen Server.|
|[CFtpConnection::PutFile](#putfile)|Platziert eine Datei auf dem Server.|
|[CFtpConnection::Entfernen](#remove)|Entfernt eine Datei vom Server.|
|[CFtpConnection::RemoveDirectory](#removedirectory)|Entfernt das angegebene Verzeichnis vom Server.|
|[CFtpConnection::Umbenennen](#rename)|Benennt eine Datei auf dem Server um.|
|[CFtpConnection::SetCurrentDirectory](#setcurrentdirectory)|Legt das aktuelle FTP-Verzeichnis fest.|

## <a name="remarks"></a>Bemerkungen

FTP ist einer der drei Internetdienste, die von den MFC WinInet-Klassen erkannt werden.

Um mit einem FTP-Internetserver zu kommunizieren, müssen Sie zunächst eine `CFtpConnection` Instanz von [CInternetSession](../../mfc/reference/cinternetsession-class.md)erstellen und dann ein Objekt erstellen. Sie erstellen `CFtpConnection` niemals ein Objekt direkt; Rufen Sie stattdessen [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection) `CFtpConnection` auf, das das Objekt erstellt und einen Zeiger darauf zurückgibt.

Weitere Informationen zur `CFtpConnection` Funktionsweise mit den anderen MFC-Internetklassen finden Sie im Artikel [Internetprogrammierung mit WinInet](../../mfc/win32-internet-extensions-wininet.md). Weitere Informationen zur Kommunikation mit den beiden anderen unterstützten Diensten HTTP und gopher finden Sie in den Klassen [CHttpConnection](../../mfc/reference/chttpconnection-class.md) und [CGopherConnection](../../mfc/reference/cgopherconnection-class.md).

## <a name="example"></a>Beispiel

  Sehen Sie sich das Beispiel in der [CFtpFileFind-Klassenübersicht](../../mfc/reference/cftpfilefind-class.md) an.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CFtpConnection`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxinet.h

## <a name="cftpconnectioncftpconnection"></a><a name="cftpconnection"></a>CFtpConnection::CFtpConnection

Diese Memberfunktion wird aufgerufen, um ein `CFtpConnection` Objekt zu erstellen.

```
CFtpConnection(
    CInternetSession* pSession,
    HINTERNET hConnected,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext);

CFtpConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 0,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    BOOL bPassive = FALSE);
```

### <a name="parameters"></a>Parameter

*pSession*<br/>
Ein Zeiger auf das zugehörige [CInternetSession-Objekt.](../../mfc/reference/cinternetsession-class.md)

*hConnected*<br/>
Das Windows-Handle der aktuellen Internetsitzung.

*pstrServer*<br/>
Ein Zeiger auf eine Zeichenfolge, die den FTP-Servernamen enthält.

*dwContext*<br/>
Der Kontextbezeichner für den Vorgang. *dwContext* identifiziert die Statusinformationen des Vorgangs, die von [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)zurückgegeben werden. Der Standardwert ist auf 1 festgelegt. Sie können dem Vorgang jedoch explizit eine bestimmte Kontext-ID zuweisen. Das Objekt und alle Arbeiten, die es ausführt, werden dieser Kontext-ID zugeordnet.

*pstrUserName*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den Namen des Benutzers angibt, der sich anmelden soll. Wenn NULL, ist der Standardwert anonym.

*pstrPassword*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge, die das Kennwort angibt, das zum Anmelden verwendet werden soll. Wenn sowohl *pstrPassword* als auch *pstrUserName* NULL sind, ist das anonyme Standardkennwort der E-Mail-Name des Benutzers. Wenn *pstrPassword* NULL (oder eine leere Zeichenfolge) ist, *pstrUserName* jedoch nicht NULL ist, wird ein leeres Kennwort verwendet. In der folgenden Tabelle wird das Verhalten für die vier möglichen Einstellungen von *pstrUserName* und *pstrPassword*beschrieben:

|*pstrUserName*|*pstrPassword*|Benutzername, der an FTP-Server gesendet wird|An FTP-Server gesendetes Kennwort|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL oder " "|NULL oder " "|"anonym"|E-Mail-Name des Benutzers|
|Nicht-NULL-Zeichenfolge|NULL oder " "|*pstrUserName*|" "|
|NULL Non- NULL String|ERROR|ERROR||
|Nicht-NULL-Zeichenfolge|Nicht-NULL-Zeichenfolge|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
Eine Zahl, die den TCP/IP-Port identifiziert, der auf dem Server verwendet werden soll.

*bPassiv*<br/>
Gibt den passiven oder aktiven Modus für diese FTP-Sitzung an. Wenn auf TRUE festgelegt, wird die Win32-API *dwFlag* auf INTERNET_FLAG_PASSIVE festgelegt.

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CFtpConnection` nie direkt ein Objekt. Rufen Sie stattdessen [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection) `CFptConnection` auf, wodurch das Objekt erstellt wird.

## <a name="cftpconnectioncommand"></a><a name="command"></a>CFtpConnection::Befehl

Sendet einen Befehl direkt an einen FTP-Server.

```
CInternetFile* Command(
    LPCTSTR pszCommand,
    CmdResponseType eResponse = CmdRespNone,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parameter

*pszCommand*<br/>
Ein Zeiger auf eine Zeichenfolge, die den zu sendenden Befehl enthält.

*eResponse*<br/>
Gibt an, ob eine Antwort vom FTP-Server erwartet wird. Es kann sich um einen der folgenden Werte handeln:

- `CmdRespNone`Es wird keine Antwort erwartet.
- `CmdRespRead`Es wird eine Antwort erwartet.
- `CmdRespWrite`Nicht verwendet.

Der CmdResponseType ist ein Member von CFtpConnection, definiert in *afxinet.h*.

*dwFlags*<br/>
Ein Wert mit den Flags, die diese Funktion steuern. Eine vollständige Liste finden Sie unter [FTPCommand](/windows/win32/api/wininet/nf-wininet-ftpcommandw).

*dwContext*<br/>
Ein Zeiger auf einen Wert mit einem anwendungsdefinierten Wert, der zur Identifizierung des Anwendungskontexts in Rückrufen verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion emuliert die Funktionalität der [FTPCommand-Funktion,](/windows/win32/api/wininet/nf-wininet-ftpcommandw) wie im Windows SDK beschrieben.

Wenn ein Fehler auftritt, löst MFC eine Ausnahme vom Typ [CInternetException](../../mfc/reference/cinternetexception-class.md)aus.

## <a name="cftpconnectioncreatedirectory"></a><a name="createdirectory"></a>CFtpConnection::CreateDirectory

Rufen Sie diese Memberfunktion auf, um ein Verzeichnis auf dem verbundenen Server zu erstellen.

```
BOOL CreateDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parameter

*pstrDirName*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen des zu erstellenden Verzeichnisses enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Windows-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

### <a name="remarks"></a>Bemerkungen

Verwenden `GetCurrentDirectory` Sie diese Option, um das aktuelle Arbeitsverzeichnis für diese Verbindung zum Server zu bestimmen. Gehen Sie nicht davon aus, dass das Remotesystem Sie mit dem Stammverzeichnis verbunden hat.

Der `pstrDirName` Parameter kann entweder ein teilweiser oder ein vollqualifizierter Dateiname relativ zum aktuellen Verzeichnis sein. Ein umgekehrter\\Schrägstrich ( ) oder Schrägstrich (/) kann als Verzeichnistrennzeichen für beide Namen verwendet werden. `CreateDirectory`übersetzt die Verzeichnisnamenstrennzeichen in die entsprechenden Zeichen, bevor sie verwendet werden.

## <a name="cftpconnectiongetcurrentdirectory"></a><a name="getcurrentdirectory"></a>CFtpConnection::GetCurrentDirectory

Rufen Sie diese Memberfunktion auf, um den Namen des aktuellen Verzeichnisses abzurufen.

```
BOOL GetCurrentDirectory(CString& strDirName) const;

BOOL GetCurrentDirectory(
    LPTSTR pstrDirName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>Parameter

*strDirName*<br/>
Ein Verweis auf eine Zeichenfolge, die den Namen des Verzeichnisses erhält.

*pstrDirName*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen des Verzeichnisses erhält.

*lpdwLen*<br/>
Ein Zeiger auf ein DWORD, der die folgenden Informationen enthält:

|||
|-|-|
|Bei der Einreise|Die Größe des Puffers, auf den *pstrDirName*verweist.|
|Bei der Rückkehr|Die Anzahl der in *pstrDirName*gespeicherten Zeichen. Wenn die Memberfunktion fehlschlägt und ERROR_INSUFFICIENT_BUFFER zurückgegeben wird, enthält *lpdwLen* die Anzahl der Bytes, die die Anwendung zuweisen muss, um die Zeichenfolge zu empfangen.|

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

### <a name="remarks"></a>Bemerkungen

Um stattdessen den Verzeichnisnamen als URL abzurufen, rufen Sie [GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)auf.

Die Parameter *pstrDirName* oder *strDirName* können entweder teilweise qualifizierte Dateinamen relativ zum aktuellen Verzeichnis oder voll qualifiziert sein. Ein umgekehrter\\Schrägstrich ( ) oder Schrägstrich (/) kann als Verzeichnistrennzeichen für beide Namen verwendet werden. `GetCurrentDirectory`übersetzt die Verzeichnisnamenstrennzeichen in die entsprechenden Zeichen, bevor sie verwendet werden.

## <a name="cftpconnectiongetcurrentdirectoryasurl"></a><a name="getcurrentdirectoryasurl"></a>CFtpConnection::GetCurrentDirectoryAsURL

Rufen Sie diese Memberfunktion auf, um den Namen des aktuellen Verzeichnisses als URL abzurufen.

```
BOOL GetCurrentDirectoryAsURL(CString& strDirName) const;

BOOL GetCurrentDirectoryAsURL(
    LPTSTR pstrName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>Parameter

*strDirName*<br/>
Ein Verweis auf eine Zeichenfolge, die den Namen des Verzeichnisses erhält.

*pstrDirName*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen des Verzeichnisses erhält.

*lpdwLen*<br/>
Ein Zeiger auf ein DWORD, der die folgenden Informationen enthält:

|||
|-|-|
|Bei der Einreise|Die Größe des Puffers, auf den *pstrDirName*verweist.|
|Bei der Rückkehr|Die Anzahl der in *pstrDirName*gespeicherten Zeichen. Wenn die Memberfunktion fehlschlägt und ERROR_INSUFFICIENT_BUFFER zurückgegeben wird, enthält *lpdwLen* die Anzahl der Bytes, die die Anwendung zuweisen muss, um die Zeichenfolge zu empfangen.|

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

### <a name="remarks"></a>Bemerkungen

`GetCurrentDirectoryAsURL`Verhält sich wie [GetCurrentDirectory](#getcurrentdirectory)

Der Parameter *strDirName* kann entweder teilweise qualifizierte Dateinamen relativ zum aktuellen Verzeichnis oder voll qualifiziert sein. Ein umgekehrter\\Schrägstrich ( ) oder Schrägstrich (/) kann als Verzeichnistrennzeichen für beide Namen verwendet werden. `GetCurrentDirectoryAsURL`übersetzt die Verzeichnisnamenstrennzeichen in die entsprechenden Zeichen, bevor sie verwendet werden.

## <a name="cftpconnectiongetfile"></a><a name="getfile"></a>CFtpConnection::GetFile

Rufen Sie diese Memberfunktion auf, um eine Datei von einem FTP-Server abzurufen und auf dem lokalen Computer zu speichern.

```
BOOL GetFile(
    LPCTSTR pstrRemoteFile,
    LPCTSTR pstrLocalFile,
    BOOL bFailIfExists = TRUE,
    DWORD dwAttributes = FILE_ATTRIBUTE_NORMAL,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parameter

*pstrRemoteFile*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge, die den Namen einer Datei enthält, die vom FTP-Server abgerufen werden soll.

*pstrLocalFile*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge, die den Namen der Datei enthält, die auf dem lokalen System erstellt werden soll.

*bFailIfExists*<br/>
Gibt an, ob der Dateiname möglicherweise bereits von einer vorhandenen Datei verwendet wird. Wenn der lokale Dateiname bereits vorhanden ist `GetFile` und dieser Parameter TRUE ist, schlägt er fehl. Andernfalls `GetFile` wird die vorhandene Kopie der Datei löscht.

*dwAttributes*<br/>
Gibt die Attribute der Datei an. Dies kann eine beliebige Kombination der folgenden FILE_ATTRIBUTE_*-Flags sein.

- FILE_ATTRIBUTE_ARCHIVE Die Datei ist eine Archivdatei. Anwendungen verwenden dieses Attribut, um Dateien für die Sicherung oder Entfernung zu markieren.

- FILE_ATTRIBUTE_COMPRESSED Die Datei oder das Verzeichnis wird komprimiert. Bei einer Datei bedeutet Komprimierung, dass alle Daten in der Datei komprimiert werden. Bei einem Verzeichnis ist die Komprimierung die Standardeinstellung für neu erstellte Dateien und Unterverzeichnisse.

- FILE_ATTRIBUTE_DIRECTORY Die Datei ist ein Verzeichnis.

- FILE_ATTRIBUTE_NORMAL Für die Datei sind keine anderen Attribute festgelegt. Dieses Attribut ist nur gültig, wenn es allein verwendet wird. Alle anderen Dateiattribute überschreiben FILE_ATTRIBUTE_NORMAL:

- FILE_ATTRIBUTE_HIDDEN Die Datei ist ausgeblendet. Es ist nicht in einer gewöhnlichen Verzeichnisliste enthalten.

- FILE_ATTRIBUTE_READONLY Die Datei ist schreibgeschützt. Anwendungen können die Datei lesen, aber nicht darauf schreiben oder löschen.

- FILE_ATTRIBUTE_SYSTEM Die Datei ist Teil des Betriebssystems oder wird ausschließlich vom Betriebssystem verwendet.

- FILE_ATTRIBUTE_TEMPORARY Die Datei wird für den temporären Speicher verwendet. Anwendungen sollten nur dann in die Datei schreiben, wenn dies unbedingt erforderlich ist. Die meisten Daten der Datei verbleiben im Speicher, ohne auf das Medium geleert zu werden, da die Datei bald gelöscht wird.

*dwFlags*<br/>
Gibt die Bedingungen an, unter denen die Übertragung erfolgt. Dieser Parameter kann einer der in [FtpGetFile](/windows/win32/api/wininet/nf-wininet-ftpgetfilew) im Windows SDK beschriebenen *dwFlags-Werte* sein.

*dwContext*<br/>
Der Kontextbezeichner für den Dateiabruf. Weitere Informationen zu *dwContext*finden Sie unter **Hinweise** .

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

### <a name="remarks"></a>Bemerkungen

`GetFile`ist eine Routine auf hoher Ebene, die den gesamten Aufwand übernimmt, der mit dem Lesen einer Datei von einem FTP-Server und dem lokalen Speichern einer Datei verbunden ist. Anwendungen, die nur Dateidaten abrufen oder eine genaue Kontrolle `OpenFile` über die Dateiübertragung erfordern, sollten stattdessen [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read) verwenden.

Wenn *dwFlags* FILE_TRANSFER_TYPE_ASCII ist, konvertiert die Übersetzung von Dateidaten auch Steuerelement- und Formatierungszeichen in Windows-Äquivalente. Die Standardübertragung ist der Binärmodus, in dem die Datei im gleichen Format heruntergeladen wird, wie sie auf dem Server gespeichert ist.

Sowohl *pstrRemoteFile als* auch *pstrLocalFile* können entweder teilweise qualifizierte Dateinamen relativ zum aktuellen Verzeichnis oder voll qualifiziert sein. Ein umgekehrter\\Schrägstrich ( ) oder Schrägstrich (/) kann als Verzeichnistrennzeichen für beide Namen verwendet werden. `GetFile`übersetzt die Verzeichnisnamenstrennzeichen in die entsprechenden Zeichen, bevor sie verwendet werden.

Überschreiben Sie die *standardeinstellung dwContext,* um den Kontextbezeichner auf einen Wert Ihrer Wahl festzulegen. Der Kontextbezeichner ist diesem `CFtpConnection` spezifischen Vorgang des Objekts zugeordnet, das von seinem [CInternetSession-Objekt](../../mfc/reference/cinternetsession-class.md) erstellt wurde. Der Wert wird an [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zurückgegeben, um den Status für den Vorgang bereitzustellen, mit dem er identifiziert wird. Weitere Informationen zum Kontextbezeichner finden Sie im Artikel [Internet First Steps: WinInet.](../../mfc/wininet-basics.md)

## <a name="cftpconnectionopenfile"></a><a name="openfile"></a>CFtpConnection::OpenFile

Rufen Sie diese Memberfunktion auf, um eine Datei zu öffnen, die sich auf einem FTP-Server befindet, zum Lesen oder Schreiben.

```
CInternetFile* OpenFile(
    LPCTSTR pstrFileName,
    DWORD dwAccess = GENERIC_READ,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parameter

*pstrFileName*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen der zu öffnenden Datei enthält.

*dwAccess*<br/>
Bestimmt, wie auf die Datei zugegriffen wird. Kann entweder GENERIC_READ oder GENERIC_WRITE sein, aber nicht beides.

*dwFlags*<br/>
Gibt die Bedingungen an, unter denen nachfolgende Übertragungen stattfinden. Dies kann eine der folgenden FTP_TRANSFER_*-Konstanten sein:

- FTP_TRANSFER_TYPE_ASCII Die Datei übertragungt mit ftp ASCII (Type A) Übertragungsmethode. Konvertiert Steuerelement- und Formatierungsinformationen in lokale Entsprechungen.

- FTP_TRANSFER_TYPE_BINARY Die Datei überträgt Daten mit der FTP-Übertragungsmethode Image (Type I). Die Datei überträgt Daten genau so, wie sie vorhanden sind, ohne Änderungen. Dies ist die Standardübertragungsmethode.

*dwContext*<br/>
Der Kontextbezeichner zum Öffnen der Datei. Weitere Informationen zu *dwContext*finden Sie unter **Hinweise** .

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CInternetFile-Objekt.](../../mfc/reference/cinternetfile-class.md)

### <a name="remarks"></a>Bemerkungen

`OpenFile`sollte in den folgenden Situationen verwendet werden:

- Eine Anwendung verfügt über Daten, die als Datei auf dem FTP-Server gesendet und erstellt werden müssen, diese Daten befinden sich jedoch nicht in einer lokalen Datei. Nach `OpenFile` dem Öffnen einer Datei verwendet die Anwendung [CInternetFile::Write,](../../mfc/reference/cinternetfile-class.md#write) um die FTP-Dateidaten an den Server zu senden.

- Eine Anwendung muss eine Datei vom Server abrufen und in anwendungsgesteuerten Speicher speichern, anstatt sie auf den Datenträger zu schreiben. Die Anwendung verwendet [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read) nach der Verwendung `OpenFile` zum Öffnen der Datei.

- Eine Anwendung benötigt eine feine Kontrolle über eine Dateiübertragung. Beispielsweise kann die Anwendung ein Fortschrittssteuerelement anzeigen, das den Fortschritt des Dateiübertragungsstatus beim Herunterladen einer Datei anzeigt.

Nach `OpenFile` dem Aufruf `CInternetConnection::Close`und bis zum Aufrufen kann die Anwendung nur [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read), [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write), `CInternetConnection::Close`oder [CFtpFileFind::FindFile](../../mfc/reference/cftpfilefind-class.md#findfile)aufrufen. Aufrufe an andere FTP-Funktionen für dieselbe FTP-Sitzung schlagen fehl und legen den Fehlercode auf FTP_ETRANSFER_IN_PROGRESS fest.

Der Parameter *pstrFileName* kann entweder ein teilweise qualifizierter Dateiname relativ zum aktuellen Verzeichnis oder voll qualifiziert sein. Ein umgekehrter\\Schrägstrich ( ) oder Schrägstrich (/) kann als Verzeichnistrennzeichen für beide Namen verwendet werden. `OpenFile`übersetzt die Verzeichnisnamenstrennzeichen in die entsprechenden Zeichen, bevor sie verwendet werden.

Überschreiben Sie die *standardeinstellung dwContext,* um den Kontextbezeichner auf einen Wert Ihrer Wahl festzulegen. Der Kontextbezeichner ist diesem `CFtpConnection` spezifischen Vorgang des Objekts zugeordnet, das von seinem [CInternetSession-Objekt](../../mfc/reference/cinternetsession-class.md) erstellt wurde. Der Wert wird an [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zurückgegeben, um den Status für den Vorgang bereitzustellen, mit dem er identifiziert wird. Weitere Informationen zum Kontextbezeichner finden Sie im Artikel [Internet First Steps: WinInet.](../../mfc/wininet-basics.md)

## <a name="cftpconnectionputfile"></a><a name="putfile"></a>CFtpConnection::PutFile

Rufen Sie diese Memberfunktion auf, um eine Datei auf einem FTP-Server zu speichern.

```
BOOL PutFile(
    LPCTSTR pstrLocalFile,
    LPCTSTR pstrRemoteFile,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parameter

*pstrLocalFile*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen der Datei enthält, die vom lokalen System gesendet werden soll.

*pstrRemoteFile*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen der Datei enthält, die auf dem FTP-Server erstellt werden soll.

*dwFlags*<br/>
Gibt die Bedingungen an, unter denen die Übertragung der Datei erfolgt. Kann eine der in [OpenFile](#openfile)beschriebenen FTP_TRANSFER_*-Konstanten sein.

*dwContext*<br/>
Der Kontextbezeichner zum Platzieren der Datei. Weitere Informationen zu *dwContext*finden Sie unter **Hinweise** .

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

### <a name="remarks"></a>Bemerkungen

`PutFile`ist eine Routine auf hoher Ebene, die alle Vorgänge verarbeitet, die mit dem Speichern einer Datei auf einem FTP-Server verbunden sind. Anwendungen, die nur Daten senden oder eine genauere Kontrolle über die Dateiübertragung erfordern, sollten [OpenFile](#openfile) und [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write)verwenden.

Überschreiben Sie den `dwContext`-Standard, um den Kontextbezeichner auf einen ausgewählten Wert festzulegen. Der Kontextbezeichner ist diesem `CFtpConnection` spezifischen Vorgang des Objekts zugeordnet, das von seinem [CInternetSession-Objekt](../../mfc/reference/cinternetsession-class.md) erstellt wurde. Der Wert wird an [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zurückgegeben, um den Status für den Vorgang bereitzustellen, mit dem er identifiziert wird. Weitere Informationen zum Kontextbezeichner finden Sie im Artikel [Internet First Steps: WinInet.](../../mfc/wininet-basics.md)

## <a name="cftpconnectionremove"></a><a name="remove"></a>CFtpConnection::Entfernen

Rufen Sie diese Memberfunktion auf, um die angegebene Datei vom verbundenen Server zu löschen.

```
BOOL Remove(LPCTSTR pstrFileName);
```

### <a name="parameters"></a>Parameter

*pstrFileName*<br/>
Ein Zeiger auf eine Zeichenfolge, die den zu entfernenden Dateinamen enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

### <a name="remarks"></a>Bemerkungen

Der Parameter *pstrFileName* kann entweder ein teilweise qualifizierter Dateiname relativ zum aktuellen Verzeichnis oder voll qualifiziert sein. Ein umgekehrter\\Schrägstrich ( ) oder Schrägstrich (/) kann als Verzeichnistrennzeichen für beide Namen verwendet werden. Die `Remove` Funktion übersetzt die Verzeichnisnamenstrennzeichen in die entsprechenden Zeichen, bevor sie verwendet werden.

## <a name="cftpconnectionremovedirectory"></a><a name="removedirectory"></a>CFtpConnection::RemoveDirectory

Rufen Sie diese Memberfunktion auf, um das angegebene Verzeichnis vom verbundenen Server zu entfernen.

```
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parameter

*pstrDirName*<br/>
Ein Zeiger auf eine Zeichenfolge, die das zu entfernende Verzeichnis enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie [GetCurrentDirectory,](#getcurrentdirectory) um das aktuelle Arbeitsverzeichnis des Servers zu bestimmen. Gehen Sie nicht davon aus, dass das Remotesystem Sie mit dem Stammverzeichnis verbunden hat.

Der Parameter *pstrDirName* kann entweder ein teilweiser oder vollständig qualifizierter Dateiname relativ zum aktuellen Verzeichnis sein. Ein umgekehrter\\Schrägstrich ( ) oder Schrägstrich (/) kann als Verzeichnistrennzeichen für beide Namen verwendet werden. `RemoveDirectory`übersetzt die Verzeichnisnamenstrennzeichen in die entsprechenden Zeichen, bevor sie verwendet werden.

## <a name="cftpconnectionrename"></a><a name="rename"></a>CFtpConnection::Umbenennen

Rufen Sie diese Memberfunktion auf, um die angegebene Datei auf dem verbundenen Server umzubenennen.

```
BOOL Rename(
    LPCTSTR pstrExisting,
    LPCTSTR pstrNew);
```

### <a name="parameters"></a>Parameter

*pstrVorhanden*<br/>
Ein Zeiger auf eine Zeichenfolge, die den aktuellen Namen der umbenannten Datei enthält.

*pstrNeu*<br/>
Ein Zeiger auf eine Zeichenfolge, die den neuen Namen der Datei enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

### <a name="remarks"></a>Bemerkungen

Die Parameter *pstrExisting* und *pstrNew* können entweder ein teilweise qualifizierter Dateiname relativ zum aktuellen Verzeichnis oder voll qualifiziert sein. Ein umgekehrter\\Schrägstrich ( ) oder Schrägstrich (/) kann als Verzeichnistrennzeichen für beide Namen verwendet werden. `Rename`übersetzt die Verzeichnisnamenstrennzeichen in die entsprechenden Zeichen, bevor sie verwendet werden.

## <a name="cftpconnectionsetcurrentdirectory"></a><a name="setcurrentdirectory"></a>CFtpConnection::SetCurrentDirectory

Rufen Sie diese Memberfunktion auf, um in ein anderes Verzeichnis auf dem FTP-Server zu wechseln.

```
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parameter

*pstrDirName*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen des Verzeichnisses enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

### <a name="remarks"></a>Bemerkungen

Der Parameter *pstrDirName* kann entweder ein teilweiser oder vollständig qualifizierter Dateiname relativ zum aktuellen Verzeichnis sein. Ein umgekehrter\\Schrägstrich ( ) oder Schrägstrich (/) kann als Verzeichnistrennzeichen für beide Namen verwendet werden. `SetCurrentDirectory`übersetzt die Verzeichnisnamenstrennzeichen in die entsprechenden Zeichen, bevor sie verwendet werden.

Verwenden Sie [GetCurrentDirectory,](#getcurrentdirectory) um das aktuelle Arbeitsverzeichnis eines FTP-Servers zu ermitteln. Gehen Sie nicht davon aus, dass das Remotesystem Sie mit dem Stammverzeichnis verbunden hat.

## <a name="see-also"></a>Siehe auch

[CInternetConnection-Klasse](../../mfc/reference/cinternetconnection-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection-Klasse](../../mfc/reference/cinternetconnection-class.md)<br/>
[CInternetSession-Klasse](../../mfc/reference/cinternetsession-class.md)
