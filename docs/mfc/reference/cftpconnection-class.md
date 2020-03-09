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
ms.openlocfilehash: 94ee4cb938ee061470282eb2f08a94d83c908805
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890783"
---
# <a name="cftpconnection-class"></a>CFtpConnection-Klasse

Verwaltet die FTP-Verbindung mit einem Internet Server und ermöglicht die direkte Bearbeitung von Verzeichnissen und Dateien auf diesem Server.

## <a name="syntax"></a>Syntax

```
class CFtpConnection : public CInternetConnection
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFtpConnection:: CFtpConnection](#cftpconnection)|Erstellt ein `CFtpConnection`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFtpConnection:: Command](#command)|Sendet einen Befehl direkt an einen FTP-Server.|
|[CFtpConnection:: kreatedirectory](#createdirectory)|Erstellt ein Verzeichnis auf dem Server.|
|[CFtpConnection:: GetCurrentDirectory](#getcurrentdirectory)|Ruft das aktuelle Verzeichnis für diese Verbindung ab.|
|[CFtpConnection:: getcurrentdirector yasurl](#getcurrentdirectoryasurl)|Ruft das aktuelle Verzeichnis für diese Verbindung als URL ab.|
|[CFtpConnection:: GetFile](#getfile)|Ruft eine Datei vom verbundenen Server ab.|
|[CFtpConnection:: OpenFile](#openfile)|Öffnet eine Datei auf dem verbundenen Server.|
|[CFtpConnection::P utfile](#putfile)|Platziert eine Datei auf dem Server.|
|[CFtpConnection:: Remove](#remove)|Entfernt eine Datei vom Server.|
|[CFtpConnection:: RemoveDirectory](#removedirectory)|Entfernt das angegebene Verzeichnis vom Server.|
|[CFtpConnection:: Rename](#rename)|Benennt eine Datei auf dem Server um.|
|[CFtpConnection:: SetCurrentDirectory](#setcurrentdirectory)|Legt das aktuelle FTP-Verzeichnis fest.|

## <a name="remarks"></a>Bemerkungen

FTP ist einer der drei Internet Dienste, die von den MFC-WinInet-Klassen erkannt werden.

Um mit einem FTP-Internet Server zu kommunizieren, müssen Sie zuerst eine Instanz von [cinternetzession](../../mfc/reference/cinternetsession-class.md)erstellen und dann ein `CFtpConnection` Objekt erstellen. Sie erstellen niemals direkt ein `CFtpConnection` Objekt. Stattdessen wird [cinternetzession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)aufgerufen, das das `CFtpConnection` Objekt erstellt und einen Zeiger darauf zurückgibt.

Weitere Informationen zur Funktionsweise von `CFtpConnection` mit den anderen MFC-Internet Klassen finden Sie im Artikel [Internet Programmierung mit WinInet](../../mfc/win32-internet-extensions-wininet.md). Weitere Informationen zur Kommunikation mit den anderen beiden unterstützten Diensten, http und Gopher, finden Sie unter den Klassen " [CHttpConnection](../../mfc/reference/chttpconnection-class.md) " und " [CGopherConnection](../../mfc/reference/cgopherconnection-class.md)".

## <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel in der Übersicht über die [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) -Klasse.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CFtpConnection`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXINET. h

##  <a name="cftpconnection"></a>CFtpConnection:: CFtpConnection

Diese Member-Funktion wird aufgerufen, um ein `CFtpConnection` Objekt zu erstellen.

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

*psession*<br/>
Ein Zeiger auf das zugehörige [cinternetzession](../../mfc/reference/cinternetsession-class.md) -Objekt.

*hconnected*<br/>
Das Windows-Handle der aktuellen Internet Sitzung.

*pstrinserver*<br/>
Ein Zeiger auf eine Zeichenfolge, die den FTP-Servernamen enthält.

*dwcontext*<br/>
Der Kontext Bezeichner für den Vorgang. *dwcontext* identifiziert die von [cinternetzession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)zurückgegebenen Statusinformationen des Vorgangs. Der Standardwert wird auf 1 festgelegt. Sie können jedoch explizit eine bestimmte Kontext-ID für den Vorgang zuweisen. Das-Objekt und alle Aufgaben, die es durchführt, werden mit dieser Kontext-ID verknüpft.

*pstrusername*<br/>
Zeiger auf eine mit NULL endenden Zeichenfolge, die den Namen des Benutzers angibt, der angemeldet werden soll. Wenn der Wert NULL ist, ist der Standardwert Anonymous.

*pstraupassword*<br/>
Ein Zeiger auf eine mit NULL endende Zeichenfolge, die das Kennwort für die Anmeldung angibt. Wenn sowohl *pstraupassword* als auch *pstrusername* NULL sind, ist das anonyme Standard Kennwort der e-Mail-Name des Benutzers. Wenn *pstraupassword* NULL (oder eine leere Zeichenfolge) ist, aber *pstrusername* nicht NULL ist, wird ein leeres Kennwort verwendet. In der folgenden Tabelle wird das Verhalten der vier möglichen Einstellungen von *pstrusername* und *pstrinpassword*beschrieben:

|*pstrusername*|*pstraupassword*|An FTP-Server gesendeter Benutzername|Kennwort an FTP-Server gesendet|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL oder ""|NULL oder ""|Anonymous|E-Mail-Name des Benutzers|
|Zeichenfolge ungleich NULL|NULL oder ""|*pstrusername*|„ “|
|NULL-Zeichenfolge ungleich NULL|ERROR|ERROR||
|Zeichenfolge ungleich NULL|Zeichenfolge ungleich NULL|*pstrusername*|*pstraupassword*|

*Nport*<br/>
Eine Zahl, die den auf dem Server zu verwendenden TCP/IP-Port identifiziert.

*bpassiv*<br/>
Gibt den passiven oder aktiven Modus für diese FTP-Sitzung an. Wenn der Wert auf true festgelegt ist, wird das Win32-API- *dwFlag* auf INTERNET_FLAG_PASSIVE festgelegt.

### <a name="remarks"></a>Bemerkungen

Sie erstellen niemals direkt ein `CFtpConnection` Objekt. Aufrufen Sie stattdessen [cinternetzession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), wodurch das `CFptConnection` Objekt erstellt wird.

##  <a name="command"></a>CFtpConnection:: Command

Sendet einen Befehl direkt an einen FTP-Server.

```
CInternetFile* Command(
    LPCTSTR pszCommand,
    CmdResponseType eResponse = CmdRespNone,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parameter

*pszcommand*<br/>
Ein Zeiger auf eine Zeichenfolge, die den zu sendenden Befehl enthält.

*eresponse*<br/>
Gibt an, ob eine Antwort vom FTP-Server erwartet wird. Es kann sich um einen der folgenden Werte handeln:

- `CmdRespNone` es wird keine Antwort erwartet.
- `CmdRespRead` eine Antwort erwartet wird.
- `CmdRespWrite` nicht verwendet.

Der cmdresponctype ist ein Member von "CFtpConnection", der in " *AFXINET. h*" definiert ist.

*dwFlags*<br/>
Ein Wert mit den Flags, die diese Funktion steuern. Eine komplette Liste finden Sie unter [ftpcommand](/windows/win32/api/wininet/nf-wininet-ftpcommandw).

*dwcontext*<br/>
Ein Zeiger auf einen Wert mit einem anwendungsdefinierten Wert, der zur Identifizierung des Anwendungskontexts in Rückrufen verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion emuliert die Funktionalität der [ftpcommand](/windows/win32/api/wininet/nf-wininet-ftpcommandw) -Funktion, wie im Windows SDK beschrieben.

Wenn ein Fehler auftritt, löst MFC eine Ausnahme vom Typ [cinternettexception](../../mfc/reference/cinternetexception-class.md)aus.

##  <a name="createdirectory"></a>CFtpConnection:: kreatedirectory

Rufen Sie diese Member-Funktion auf, um ein Verzeichnis auf dem verbundenen Server zu erstellen.

```
BOOL CreateDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parameter

*pstrindirname*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen des zu erstellenden Verzeichnisses enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Windows-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie `GetCurrentDirectory`, um das aktuelle Arbeitsverzeichnis für diese Verbindung mit dem Server zu ermitteln. Gehen Sie nicht davon aus, dass das Remote System eine Verbindung mit dem Stammverzeichnis hergestellt hat.

Der `pstrDirName`-Parameter kann entweder ein teilweise oder ein voll qualifizierter Dateiname sein, der relativ zum aktuellen Verzeichnis ist. Ein umgekehrter Schrägstrich (\\) oder ein Schrägstrich (/) kann als Verzeichnis Trennzeichen für beide Namen verwendet werden. `CreateDirectory` übersetzt die Verzeichnisnamen Trennzeichen in die entsprechenden Zeichen, bevor Sie verwendet werden.

##  <a name="getcurrentdirectory"></a>CFtpConnection:: GetCurrentDirectory

Mit dieser Member-Funktion können Sie den Namen des aktuellen Verzeichnisses abrufen.

```
BOOL GetCurrentDirectory(CString& strDirName) const;

BOOL GetCurrentDirectory(
    LPTSTR pstrDirName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>Parameter

*"Strauch Name"*<br/>
Ein Verweis auf eine Zeichenfolge, die den Namen des Verzeichnisses empfängt.

*pstrindirname*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen des Verzeichnisses empfängt.

*lpdwlen*<br/>
Ein Zeiger auf ein DWORD, das die folgenden Informationen enthält:

|||
|-|-|
|Bei Eintrag|Die Größe des Puffers, auf den von *pstrindirname*verwiesen wird.|
|Bei Rückgabe|Die Anzahl der in " *pstrindirname*" gespeicherten Zeichen. Wenn die Member-Funktion fehlschlägt und ERROR_INSUFFICIENT_BUFFER zurückgegeben wird, enthält *lpdwlen* die Anzahl von Bytes, die die Anwendung zuordnen muss, um die Zeichenfolge zu empfangen.|

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

### <a name="remarks"></a>Bemerkungen

Wenn Sie stattdessen den Verzeichnisnamen als URL abrufen möchten, müssen Sie [GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)aufrufen.

Bei den Parametern " *pstrindirname* " oder " *Strauch Name* " kann es sich entweder um teilweise qualifizierte Dateinamen in Bezug auf das aktuelle Verzeichnis oder um einen voll qualifizierten Ein umgekehrter Schrägstrich (\\) oder ein Schrägstrich (/) kann als Verzeichnis Trennzeichen für beide Namen verwendet werden. `GetCurrentDirectory` übersetzt die Verzeichnisnamen Trennzeichen in die entsprechenden Zeichen, bevor Sie verwendet werden.

##  <a name="getcurrentdirectoryasurl"></a>CFtpConnection:: getcurrentdirector yasurl

Mit dieser Member-Funktion können Sie den Namen des aktuellen Verzeichnisses als URL abrufen.

```
BOOL GetCurrentDirectoryAsURL(CString& strDirName) const;

BOOL GetCurrentDirectoryAsURL(
    LPTSTR pstrName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>Parameter

*"Strauch Name"*<br/>
Ein Verweis auf eine Zeichenfolge, die den Namen des Verzeichnisses empfängt.

*pstrindirname*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen des Verzeichnisses empfängt.

*lpdwlen*<br/>
Ein Zeiger auf ein DWORD, das die folgenden Informationen enthält:

|||
|-|-|
|Bei Eintrag|Die Größe des Puffers, auf den von *pstrindirname*verwiesen wird.|
|Bei Rückgabe|Die Anzahl der in " *pstrindirname*" gespeicherten Zeichen. Wenn die Member-Funktion fehlschlägt und ERROR_INSUFFICIENT_BUFFER zurückgegeben wird, enthält *lpdwlen* die Anzahl von Bytes, die die Anwendung zuordnen muss, um die Zeichenfolge zu empfangen.|

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

### <a name="remarks"></a>Bemerkungen

`GetCurrentDirectoryAsURL` verhält sich wie [GetCurrentDirectory](#getcurrentdirectory) .

Der Parameter *"* " "" "" "" "" "" "" "" "" "" "" "". Ein umgekehrter Schrägstrich (\\) oder ein Schrägstrich (/) kann als Verzeichnis Trennzeichen für beide Namen verwendet werden. `GetCurrentDirectoryAsURL` übersetzt die Verzeichnisnamen Trennzeichen in die entsprechenden Zeichen, bevor Sie verwendet werden.

##  <a name="getfile"></a>CFtpConnection:: GetFile

Mit dieser Member-Funktion können Sie eine Datei von einem FTP-Server abrufen und auf dem lokalen Computer speichern.

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

*pstrinremotefile*<br/>
Ein Zeiger auf eine NULL-terminierte Zeichenfolge mit dem Namen einer Datei, die vom FTP-Server abgerufen werden soll.

*pstrinlocalfile*<br/>
Ein Zeiger auf eine NULL-terminierte Zeichenfolge, die den Namen der Datei enthält, die auf dem lokalen System erstellt werden soll.

*bfailif vorhanden*<br/>
Gibt an, ob der Dateiname bereits von einer vorhandenen Datei verwendet werden kann. Wenn der Name der lokalen Datei bereits vorhanden ist und dieser Parameter true ist, schlägt `GetFile` fehl. Andernfalls wird `GetFile` die vorhandene Kopie der Datei löschen.

*dwattributes*<br/>
Gibt die Attribute der Datei an. Dabei kann es sich um eine beliebige Kombination der folgenden FILE_ATTRIBUTE_ *-Flags handeln.

- FILE_ATTRIBUTE_ARCHIVE die Datei eine Archivdatei ist. Anwendungen verwenden dieses Attribut, um Dateien für die Sicherung oder Entfernung zu markieren.

- FILE_ATTRIBUTE_COMPRESSED die Datei oder das Verzeichnis komprimiert ist. Bei einer Datei bedeutet die Komprimierung, dass alle Daten in der Datei komprimiert sind. Für ein Verzeichnis ist die Komprimierung der Standardwert für neu erstellte Dateien und Unterverzeichnisse.

- FILE_ATTRIBUTE_DIRECTORY die Datei ein Verzeichnis ist.

- FILE_ATTRIBUTE_NORMAL für die Datei sind keine anderen Attribute festgelegt. Dieses Attribut ist nur gültig, wenn es allein verwendet wird. Alle anderen Dateiattribute überschreiben FILE_ATTRIBUTE_NORMAL:

- FILE_ATTRIBUTE_HIDDEN die Datei ausgeblendet ist. Er darf nicht in eine gewöhnliche Verzeichnis Auflistung eingeschlossen werden.

- FILE_ATTRIBUTE_READONLY die Datei schreibgeschützt ist. Anwendungen können die Datei lesen, aber nicht schreiben oder löschen.

- FILE_ATTRIBUTE_SYSTEM die Datei Teil von ist oder ausschließlich vom Betriebs System verwendet wird.

- FILE_ATTRIBUTE_TEMPORARY die Datei für den temporären Speicher verwendet wird. Anwendungen sollten nur dann in die Datei schreiben, wenn dies unbedingt erforderlich ist. Die meisten Daten der Datei verbleiben im Arbeitsspeicher, ohne auf die Medien geleert zu werden, da die Datei in Kürze gelöscht wird.

*dwFlags*<br/>
Gibt die Bedingungen an, unter denen die Übertragung erfolgt. Dieser Parameter kann ein beliebiger *dwFlags* -Wert sein, der in der Windows SDK unter [ftpgetfile](/windows/win32/api/wininet/nf-wininet-ftpgetfilew) beschrieben wird.

*dwcontext*<br/>
Der Kontext Bezeichner für das Abrufen von Dateien. Weitere Informationen zu *dwcontext*finden Sie unter " **Hinweise** ".

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

### <a name="remarks"></a>Bemerkungen

`GetFile` ist eine allgemeine Routine, die den gesamten Aufwand für das Lesen einer Datei von einem FTP-Server und die lokale Speicherung behandelt. Anwendungen, die nur Datei Daten abrufen oder die eine schließende Kontrolle über die Dateiübertragung benötigen, sollten stattdessen `OpenFile` und [CInternetFile:: Read](../../mfc/reference/cinternetfile-class.md#read) verwenden.

Wenn *dwFlags* FILE_TRANSFER_TYPE_ASCII ist, werden von der Übersetzung von Datei Daten auch Steuerzeichen und Formatierungszeichen in Windows-Entsprechungen konvertiert. Die Standard Übertragung ist der binäre Modus, bei dem die Datei im gleichen Format wie auf dem Server heruntergeladen wird.

Sowohl *pstrauremotefile* als auch *pstrinlocalfile* können entweder teilweise qualifizierte Dateinamen in Relation zum aktuellen Verzeichnis oder voll qualifiziert sein. Ein umgekehrter Schrägstrich (\\) oder ein Schrägstrich (/) kann als Verzeichnis Trennzeichen für beide Namen verwendet werden. `GetFile` übersetzt die Verzeichnisnamen Trennzeichen in die entsprechenden Zeichen, bevor Sie verwendet werden.

Überschreiben Sie den *dwcontext* -Standard, um den Kontext Bezeichner auf einen Wert Ihrer Wahl festzulegen. Der Kontext Bezeichner ist diesem speziellen Vorgang des `CFtpConnection` Objekts zugeordnet, das vom [cinternetzession](../../mfc/reference/cinternetsession-class.md) -Objekt erstellt wurde. Der Wert wird an [cinternetzession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zurückgegeben, um den Status für den Vorgang bereitzustellen, mit dem er identifiziert wird. Weitere Informationen zum Kontext Bezeichner finden Sie im Artikel [Internet First Steps: WinInet](../../mfc/wininet-basics.md) .

##  <a name="openfile"></a>CFtpConnection:: OpenFile

Mit dieser Member-Funktion können Sie eine Datei öffnen, die sich auf einem FTP-Server zum Lesen oder schreiben befindet.

```
CInternetFile* OpenFile(
    LPCTSTR pstrFileName,
    DWORD dwAccess = GENERIC_READ,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parameter

*pstrinfilename*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen der zu öffnenden Datei enthält.

*dwaccess*<br/>
Bestimmt, wie auf die Datei zugegriffen wird. Kann entweder GENERIC_READ oder GENERIC_WRITE sein, aber nicht beides.

*dwFlags*<br/>
Gibt die Bedingungen an, unter denen nachfolgende Übertragungen stattfinden. Dies kann eine der folgenden FTP_TRANSFER_ *-Konstanten sein:

- FTP_TRANSFER_TYPE_ASCII die Dateiübertragungen mithilfe der FTP-ASCII-Übertragungsmethode (Typ A). Konvertiert Steuerelement-und Formatierungsinformationen in lokale Entsprechungen.

- FTP_TRANSFER_TYPE_BINARY die Datei Daten mithilfe der FTP-Abbild Übertragungsmethode (Typ I) überträgt. Die Datei überträgt Daten genau so, wie Sie vorhanden sind, ohne Änderungen. Dies ist die Standard Übertragungsmethode.

*dwcontext*<br/>
Der Kontext Bezeichner zum Öffnen der Datei. Weitere Informationen zu *dwcontext*finden Sie unter " **Hinweise** ".

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CInternetFile](../../mfc/reference/cinternetfile-class.md) -Objekt.

### <a name="remarks"></a>Bemerkungen

`OpenFile` sollten in den folgenden Situationen verwendet werden:

- Eine Anwendung verfügt über Daten, die als Datei auf dem FTP-Server gesendet und erstellt werden müssen, diese Daten befinden sich jedoch nicht in einer lokalen Datei. Nachdem `OpenFile` eine Datei geöffnet hat, verwendet die Anwendung [CInternetFile:: Write](../../mfc/reference/cinternetfile-class.md#write) , um die FTP-Datei Daten an den Server zu senden.

- Eine Anwendung muss eine Datei vom Server abrufen und in Anwendungs gesteuerten Speicher platzieren, anstatt Sie auf den Datenträger zu schreiben. Die Anwendung verwendet [CInternetFile:: Read](../../mfc/reference/cinternetfile-class.md#read) , nachdem `OpenFile` zum Öffnen der Datei verwendet wurde.

- Eine Anwendung benötigt eine gute Steuerungsebene für eine Dateiübertragung. Die Anwendung kann z. b. ein Status-Steuerelement anzeigen, das den Fortschritt des Datei Übertragungs Status beim Herunterladen einer Datei anzeigt.

Nachdem Sie `OpenFile` aufgerufen und `CInternetConnection::Close`aufgerufen haben, kann die Anwendung nur [CInternetFile:: Read](../../mfc/reference/cinternetfile-class.md#read), [CInternetFile:: Write](../../mfc/reference/cinternetfile-class.md#write), `CInternetConnection::Close`oder [CFtpFileFind:: FindFile](../../mfc/reference/cftpfilefind-class.md#findfile)aufrufen. Aufrufe an andere FTP-Funktionen für dieselbe FTP-Sitzung schlagen fehl, und der Fehlercode wird auf FTP_ETRANSFER_IN_PROGRESS festgelegt.

Der *pstrinfilename* -Parameter kann entweder ein teilweise qualifizierter Dateiname relativ zum aktuellen Verzeichnis oder voll qualifiziert sein. Ein umgekehrter Schrägstrich (\\) oder ein Schrägstrich (/) kann als Verzeichnis Trennzeichen für beide Namen verwendet werden. `OpenFile` übersetzt die Verzeichnisnamen Trennzeichen vor der Verwendung in die entsprechenden Zeichen.

Überschreiben Sie den *dwcontext* -Standard, um den Kontext Bezeichner auf einen Wert Ihrer Wahl festzulegen. Der Kontext Bezeichner ist diesem speziellen Vorgang des `CFtpConnection` Objekts zugeordnet, das vom [cinternetzession](../../mfc/reference/cinternetsession-class.md) -Objekt erstellt wurde. Der Wert wird an [cinternetzession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zurückgegeben, um den Status für den Vorgang bereitzustellen, mit dem er identifiziert wird. Weitere Informationen zum Kontext Bezeichner finden Sie im Artikel [Internet First Steps: WinInet](../../mfc/wininet-basics.md) .

##  <a name="putfile"></a>CFtpConnection::P utfile

Mit dieser Member-Funktion können Sie eine Datei auf einem FTP-Server speichern.

```
BOOL PutFile(
    LPCTSTR pstrLocalFile,
    LPCTSTR pstrRemoteFile,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parameter

*pstrinlocalfile*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen der Datei enthält, die vom lokalen System gesendet werden soll.

*pstrinremotefile*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen der Datei enthält, die auf dem FTP-Server erstellt werden soll.

*dwFlags*<br/>
Gibt die Bedingungen an, unter denen die Übertragung der Datei erfolgt. Kann eine der in [OpenFile](#openfile)beschriebenen FTP_TRANSFER_ *-Konstanten sein.

*dwcontext*<br/>
Der Kontext Bezeichner zum Platzieren der Datei. Weitere Informationen zu *dwcontext*finden Sie unter " **Hinweise** ".

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

### <a name="remarks"></a>Bemerkungen

`PutFile` ist eine allgemeine Routine, die alle Vorgänge behandelt, die mit dem Speichern einer Datei auf einem FTP-Server verbunden sind. Anwendungen, die nur Daten senden oder eine genauere Kontrolle über die Dateiübertragung benötigen, sollten [OpenFile](#openfile) und [CInternetFile:: Write](../../mfc/reference/cinternetfile-class.md#write)verwenden.

Überschreiben Sie den `dwContext`-Standard, um den Kontextbezeichner auf einen ausgewählten Wert festzulegen. Der Kontext Bezeichner ist diesem speziellen Vorgang des `CFtpConnection` Objekts zugeordnet, das vom [cinternetzession](../../mfc/reference/cinternetsession-class.md) -Objekt erstellt wurde. Der Wert wird an [cinternetzession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zurückgegeben, um den Status für den Vorgang bereitzustellen, mit dem er identifiziert wird. Weitere Informationen zum Kontext Bezeichner finden Sie im Artikel [Internet First Steps: WinInet](../../mfc/wininet-basics.md) .

##  <a name="remove"></a>CFtpConnection:: Remove

Mit dieser Member-Funktion wird die angegebene Datei vom verbundenen Server gelöscht.

```
BOOL Remove(LPCTSTR pstrFileName);
```

### <a name="parameters"></a>Parameter

*pstrinfilename*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Dateinamen enthält, der entfernt werden soll.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

### <a name="remarks"></a>Bemerkungen

Der *pstrinfilename* -Parameter kann entweder ein teilweise qualifizierter Dateiname relativ zum aktuellen Verzeichnis oder voll qualifiziert sein. Ein umgekehrter Schrägstrich (\\) oder ein Schrägstrich (/) kann als Verzeichnis Trennzeichen für beide Namen verwendet werden. Die `Remove`-Funktion übersetzt die Verzeichnisnamen Trennzeichen in die entsprechenden Zeichen, bevor Sie verwendet werden.

##  <a name="removedirectory"></a>CFtpConnection:: RemoveDirectory

Mit dieser Member-Funktion wird das angegebene Verzeichnis vom verbundenen Server entfernt.

```
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parameter

*pstrindirname*<br/>
Ein Zeiger auf eine Zeichenfolge, die das zu entfernende Verzeichnis enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie [GetCurrentDirectory](#getcurrentdirectory) , um das aktuelle Arbeitsverzeichnis des Servers zu bestimmen. Gehen Sie nicht davon aus, dass das Remote System eine Verbindung mit dem Stammverzeichnis hergestellt hat.

Der *pstrindirname* -Parameter kann entweder ein teilweise oder voll qualifizierter Dateiname relativ zum aktuellen Verzeichnis sein. Ein umgekehrter Schrägstrich (\\) oder ein Schrägstrich (/) kann als Verzeichnis Trennzeichen für beide Namen verwendet werden. `RemoveDirectory` übersetzt die Verzeichnisnamen Trennzeichen in die entsprechenden Zeichen, bevor Sie verwendet werden.

##  <a name="rename"></a>CFtpConnection:: Rename

Mit dieser Member-Funktion können Sie die angegebene Datei auf dem verbundenen Server umbenennen.

```
BOOL Rename(
    LPCTSTR pstrExisting,
    LPCTSTR pstrNew);
```

### <a name="parameters"></a>Parameter

*pstrexisting*<br/>
Ein Zeiger auf eine Zeichenfolge, die den aktuellen Namen der Datei enthält, die umbenannt werden soll.

*pstraunew*<br/>
Ein Zeiger auf eine Zeichenfolge, die den neuen Namen der Datei enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

### <a name="remarks"></a>Bemerkungen

Die Parameter *pstrexisting* und *pstrenew* können entweder ein teilweise qualifizierter Dateiname relativ zum aktuellen Verzeichnis oder voll qualifiziert sein. Ein umgekehrter Schrägstrich (\\) oder ein Schrägstrich (/) kann als Verzeichnis Trennzeichen für beide Namen verwendet werden. `Rename` übersetzt die Verzeichnisnamen Trennzeichen in die entsprechenden Zeichen, bevor Sie verwendet werden.

##  <a name="setcurrentdirectory"></a>CFtpConnection:: SetCurrentDirectory

Mit dieser Member-Funktion können Sie in ein anderes Verzeichnis auf dem FTP-Server wechseln.

```
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parameter

*pstrindirname*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen des Verzeichnisses enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

### <a name="remarks"></a>Bemerkungen

Der *pstrindirname* -Parameter kann entweder ein teilweise oder voll qualifizierter Dateiname relativ zum aktuellen Verzeichnis sein. Ein umgekehrter Schrägstrich (\\) oder ein Schrägstrich (/) kann als Verzeichnis Trennzeichen für beide Namen verwendet werden. `SetCurrentDirectory` übersetzt die Verzeichnisnamen Trennzeichen in die entsprechenden Zeichen, bevor Sie verwendet werden.

Verwenden Sie [GetCurrentDirectory](#getcurrentdirectory) , um das aktuelle Arbeitsverzeichnis eines FTP-Servers zu bestimmen. Gehen Sie nicht davon aus, dass das Remote System eine Verbindung mit dem Stammverzeichnis hergestellt hat.

## <a name="see-also"></a>Weitere Informationen

[CInternetConnection-Klasse](../../mfc/reference/cinternetconnection-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection-Klasse](../../mfc/reference/cinternetconnection-class.md)<br/>
[CInternetSession-Klasse](../../mfc/reference/cinternetsession-class.md)
