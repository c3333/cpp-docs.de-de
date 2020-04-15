---
title: CUrl-Klasse
ms.date: 05/06/2019
f1_keywords:
- CUrl
- ATLUTIL/ATL::CUrl
- ATLUTIL/ATL::CUrl::CUrl
- ATLUTIL/ATL::CUrl::Canonicalize
- ATLUTIL/ATL::CUrl::Clear
- ATLUTIL/ATL::CUrl::CrackUrl
- ATLUTIL/ATL::CUrl::CreateUrl
- ATLUTIL/ATL::CUrl::GetExtraInfo
- ATLUTIL/ATL::CUrl::GetExtraInfoLength
- ATLUTIL/ATL::CUrl::GetHostName
- ATLUTIL/ATL::CUrl::GetHostNameLength
- ATLUTIL/ATL::CUrl::GetPassword
- ATLUTIL/ATL::CUrl::GetPasswordLength
- ATLUTIL/ATL::CUrl::GetPortNumber
- ATLUTIL/ATL::CUrl::GetScheme
- ATLUTIL/ATL::CUrl::GetSchemeName
- ATLUTIL/ATL::CUrl::GetSchemeNameLength
- ATLUTIL/ATL::CUrl::GetUrlLength
- ATLUTIL/ATL::CUrl::GetUrlPath
- ATLUTIL/ATL::CUrl::GetUrlPathLength
- ATLUTIL/ATL::CUrl::GetUserName
- ATLUTIL/ATL::CUrl::GetUserNameLength
- ATLUTIL/ATL::CUrl::SetExtraInfo
- ATLUTIL/ATL::CUrl::SetHostName
- ATLUTIL/ATL::CUrl::SetPassword
- ATLUTIL/ATL::CUrl::SetPortNumber
- ATLUTIL/ATL::CUrl::SetScheme
- ATLUTIL/ATL::CUrl::SetSchemeName
- ATLUTIL/ATL::CUrl::SetUrlPath
- ATLUTIL/ATL::CUrl::SetUserName
helpviewer_keywords:
- CUrl class
ms.assetid: b3894d34-47b9-4961-9719-4197153793da
ms.openlocfilehash: 3468e17b031d0a72bc56d915c689fbe4c78859e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330471"
---
# <a name="curl-class"></a>CUrl-Klasse

Diese Klasse stellt eine URL dar. Es ermöglicht Ihnen, jedes Element der URL unabhängig von den anderen zu bearbeiten, ob sie eine vorhandene URL-Zeichenfolge analysieren oder eine Zeichenfolge von Grund auf neu erstellen.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CUrl
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CUrl::CUrl](#curl)|Der Konstruktor.|
|[CUrl::'cUrl](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CUrl::Canonicalize](#canonicalize)|Rufen Sie diese Methode auf, um die URL-Zeichenfolge in kanonische Form zu konvertieren.|
|[CUrl::Klar](#clear)|Rufen Sie diese Methode auf, um alle URL-Felder zu löschen.|
|[CUrl::CrackUrl](#crackurl)|Rufen Sie diese Methode auf, um die URL zu dekodieren und zu analysieren.|
|[CUrl::CreateUrl](#createurl)|Rufen Sie diese Methode auf, um die URL zu erstellen.|
|[Curl::GetExtraInfo](#getextrainfo)|Rufen Sie diese Methode auf, um zusätzliche Informationen (z. B. *Text* oder *Text*) von der URL abzurufen.|
|[Curl::GetExtraInfoLength](#getextrainfolength)|Rufen Sie diese Methode auf, um die Länge der zusätzlichen Informationen (z. B. *Text* oder *Text*) abzurufen, die von der URL abgerufen werden sollen.|
|[CUrl::GetHostName](#gethostname)|Rufen Sie diese Methode auf, um den Hostnamen von der URL abzurufen.|
|[CUrl::GetHostNameLength](#gethostnamelength)|Rufen Sie diese Methode auf, um die Länge des Hostnamens abzurufen.|
|[CUrl::GetPassword](#getpassword)|Rufen Sie diese Methode auf, um das Kennwort von der URL abzurufen.|
|[CUrl::GetPasswordLength](#getpasswordlength)|Rufen Sie diese Methode auf, um die Länge des Kennworts abzurufen.|
|[Curl::GetPortNumber](#getportnumber)|Rufen Sie diese Methode auf, um die Portnummer in Bezug auf ATL_URL_PORT abzurufen.|
|[CUrl::GetScheme](#getscheme)|Rufen Sie diese Methode auf, um das URL-Schema abzurufen.|
|[CUrl::GetSchemeName](#getschemename)|Rufen Sie diese Methode auf, um den Namen des URL-Schemas abzurufen.|
|[CUrl::GetSchemeNameLength](#getschemenamelength)|Rufen Sie diese Methode auf, um die Länge des URL-Schemanamens abzurufen.|
|[CUrl::GetUrlLength](#geturllength)|Rufen Sie diese Methode auf, um die URL-Länge abzurufen.|
|[CUrl::GetUrlPath](#geturlpath)|Rufen Sie diese Methode auf, um den URL-Pfad abzurufen.|
|[CUrl::GetUrlPathLength](#geturlpathlength)|Rufen Sie diese Methode auf, um die URL-Pfadlänge abzurufen.|
|[CUrl::GetUserName](#getusername)|Rufen Sie diese Methode auf, um den Benutzernamen von der URL abzurufen.|
|[CUrl::GetUserNameLength](#getusernamelength)|Rufen Sie diese Methode auf, um die Länge des Benutzernamens abzurufen.|
|[Curl::SetExtraInfo](#setextrainfo)|Rufen Sie diese Methode auf, um die zusätzlichen Informationen (z. B. *Text* oder *Text*) der URL festzulegen.|
|[CUrl::SetHostName](#sethostname)|Rufen Sie diese Methode auf, um den Hostnamen festzulegen.|
|[CUrl::SetPassword](#setpassword)|Rufen Sie diese Methode auf, um das Kennwort festzulegen.|
|[Curl::SetPortNumber](#setportnumber)|Rufen Sie diese Methode auf, um die Portnummer in Bezug auf ATL_URL_PORT festzulegen.|
|[CUrl::SetScheme](#setscheme)|Rufen Sie diese Methode auf, um das URL-Schema festzulegen.|
|[CUrl::SetSchemeName](#setschemename)|Rufen Sie diese Methode auf, um den URL-Schemanamen festzulegen.|
|[CUrl::SetUrlPath](#seturlpath)|Rufen Sie diese Methode auf, um den URL-Pfad festzulegen.|
|[CUrl::SetUserName](#setusername)|Rufen Sie diese Methode auf, um den Benutzernamen festzulegen.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CUrl::operator =](#operator_eq)|Weist das `CUrl` angegebene Objekt `CUrl` dem aktuellen Objekt zu.|

## <a name="remarks"></a>Bemerkungen

`CUrl`können Sie die Felder einer URL bearbeiten, z. B. den Pfad oder die Portnummer. `CUrl`versteht URLs der folgenden Form:

\<Schema\<>:// UserName\<>: Kennwort>\@ \<HostName\<>: \<\<PortNumber>/ UrlPath>ExtraInfo>

(Einige Felder sind optional.) Betrachten Sie beispielsweise diese URL:

`http://someone:secret@www.microsoft.com:80/visualc/stuff.htm#contents`

[CUrl::CrackUrl](#crackurl) analysiert es wie folgt:

- Schema: "http" oder [ATL_URL_SCHEME_HTTP](atl-url-scheme-enum.md)

- Benutzername: "jemand"

- Passwort: "geheim"

- Hostname:`www.microsoft.com`" "

- PortNummer: 80

- UrlPath: "visualc/stuff.htm"

- ExtraInfo: "#contents"

Um das UrlPath-Feld zu bearbeiten (z. B.), verwenden Sie [GetUrlPath](#geturlpath), [GetUrlPathLength](#geturlpathlength)und [SetUrlPath](#seturlpath). Sie würden [CreateUrl](#createurl) verwenden, um die vollständige URL-Zeichenfolge zu erstellen.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlutil.h

## <a name="curlcanonicalize"></a><a name="canonicalize"></a>CUrl::Canonicalize

Rufen Sie diese Methode auf, um die URL-Zeichenfolge in kanonische Form zu konvertieren.

```
inline BOOL Canonicalize(DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parameter

*dwFlags*<br/>
Die Flags, die die Kanonisierung steuern. Wenn keine Flags angegeben sind (*dwFlags* = 0), konvertiert die Methode \\alle unsicheren Zeichen \\und Metasequenzen (z. B. ., . .., und ...) in Escapesequenzen. *dwFlags* kann einer der folgenden Werte sein:

- ATL_URL_BROWSER_MODE: Verschlüsselt oder dekodiert Zeichen nicht nach "A" oder "" und entfernt nach "" keine nachgestellten Leerzeichen. Wenn dieser Wert nicht angegeben ist, wird die gesamte URL codiert und das nachfolgende Leerzeichen entfernt.

- ATL_URL _DECODE: Konvertiert alle %XX-Sequenzen in Zeichen, einschließlich Escapesequenzen, bevor die URL analysiert wird.

- ATL_URL _ENCODE_PERCENT: Codiert alle aufgetretenen Prozentzeichen. Standardmäßig sind Prozentzeichen nicht codiert.

- ATL_URL _ENCODE_SPACES_ONLY: Codiert nur Leerzeichen.

- ATL_URL _NO_ENCODE: Konvertiert keine unsicheren Zeichen in Escapesequenzen.

- ATL_URL _NO_META: Entfernt keine Metasequenzen (z. B. "." und "..") aus der URL.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Das Konvertieren in kanonische Form beinhaltet das Konvertieren unsicherer Zeichen und Leerzeichen in Escapesequenzen.

## <a name="curlclear"></a><a name="clear"></a>CUrl::Klar

Rufen Sie diese Methode auf, um alle URL-Felder zu löschen.

```
inline void Clear() throw();
```

## <a name="curlcrackurl"></a><a name="crackurl"></a>CUrl::CrackUrl

Rufen Sie diese Methode auf, um die URL zu dekodieren und zu analysieren.

```
BOOL CrackUrl(LPCTSTR lpszUrl, DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parameter

*lpszUrl*<br/>
Die URL.

*dwFlags*<br/>
Geben Sie ATL_URL_DECODE oder ATL_URL_ESCAPE an, um alle Escapezeichen in *lpszUrl* nach dem Analysieren in ihre realen Werte zu konvertieren. (Vor Visual C++ 2005 ATL_URL_DECODE alle Escapezeichen vor dem Analysieren konvertiert.)

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

## <a name="curlcreateurl"></a><a name="createurl"></a>CUrl::CreateUrl

Diese Methode erstellt eine URL-Zeichenfolge aus den Komponentenfeldern eines CUrl-Objekts.

```
inline BOOL CreateUrl(
    LPTSTR lpszUrl,
    DWORD* pdwMaxLength,
    DWORD dwFlags = 0) const throw();
```

### <a name="parameters"></a>Parameter

*lpszUrl*<br/>
Ein Zeichenfolgenpuffer, der die vollständige URL-Zeichenfolge enthält.

*pdwMaxLength*<br/>
Die maximale Länge des lpszUrl-Zeichenfolgenpuffers. *lpszUrl*

*dwFlags*<br/>
Geben Sie ATL_URL_ESCAPE an, um alle Escapezeichen in *lpszUrl* in ihre realen Werte zu konvertieren.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Diese Methode fügt ihre einzelnen Felder an, um die vollständige URL-Zeichenfolge mit dem folgenden Format zu erstellen:

**\<schema\<>://user\<>: \@ \<übergeben\<sie \<>\<Domain->: Port>Pfad>zusätzliche>**

Beim Aufrufen dieser Methode sollte der Parameter *pdwMaxLength* zunächst die maximale Länge des Zeichenfolgenpuffers enthalten, auf den der Parameter *lpszUrl* verweist. Der Wert des Parameters *pdwMaxLength* wird mit der tatsächlichen Länge der URL-Zeichenfolge aktualisiert.

### <a name="example"></a>Beispiel

In diesem Beispiel wird die Erstellung eines CUrl-Objekts und das Abrufen der URL-Zeichenfolge veranschaulicht.

[!code-cpp[NVC_ATL_Utilities#133](../../atl/codesnippet/cpp/curl-class_1.cpp)]

## <a name="curlcurl"></a><a name="curl"></a>CUrl::CUrl

Der Konstruktor.

```
CUrl() throw();
CUrl(const CUrl& urlThat) throw();
```

### <a name="parameters"></a>Parameter

*urlThat*<br/>
Das `CUrl` zu kopierende Objekt zum Erstellen der URL.

## <a name="curlcurl"></a><a name="dtor"></a>CUrl::'cUrl

Der Destruktor.

```
~CUrl() throw();
```

## <a name="curlgetextrainfo"></a><a name="getextrainfo"></a>Curl::GetExtraInfo

Rufen Sie diese Methode auf, um zusätzliche Informationen (z. B. *Text* oder *Text*) von der URL abzurufen.

```
inline LPCTSTR GetExtraInfo() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt eine Zeichenfolge zurück, die die zusätzlichen Informationen enthält.

## <a name="curlgetextrainfolength"></a><a name="getextrainfolength"></a>Curl::GetExtraInfoLength

Rufen Sie diese Methode auf, um die Länge der zusätzlichen Informationen (z. B. *Text* oder *Text*) abzurufen, die von der URL abgerufen werden sollen.

```
inline DWORD GetExtraInfoLength() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Länge der Zeichenfolge zurück, die die zusätzlichen Informationen enthält.

## <a name="curlgethostname"></a><a name="gethostname"></a>CUrl::GetHostName

Rufen Sie diese Methode auf, um den Hostnamen von der URL abzurufen.

```
inline LPCTSTR GetHostName() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den Hostnamen zurück.

## <a name="curlgethostnamelength"></a><a name="gethostnamelength"></a>CUrl::GetHostNameLength

Rufen Sie diese Methode auf, um die Länge des Hostnamens abzurufen.

```
inline DWORD GetHostNameLength() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Länge des Hostnamens zurück.

## <a name="curlgetpassword"></a><a name="getpassword"></a>CUrl::GetPassword

Rufen Sie diese Methode auf, um das Kennwort von der URL abzurufen.

```
inline LPCTSTR GetPassword() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt das Kennwort zurück.

## <a name="curlgetpasswordlength"></a><a name="getpasswordlength"></a>CUrl::GetPasswordLength

Rufen Sie diese Methode auf, um die Länge des Kennworts abzurufen.

```
inline DWORD GetPasswordLength() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Kennwortlänge zurück.

## <a name="curlgetportnumber"></a><a name="getportnumber"></a>Curl::GetPortNumber

Rufen Sie diese Methode auf, um die Portnummer abzurufen.

```
inline ATL_URL_PORT GetPortNumber() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Portnummer zurück.

## <a name="curlgetscheme"></a><a name="getscheme"></a>CUrl::GetScheme

Rufen Sie diese Methode auf, um das URL-Schema abzurufen.

```
inline ATL_URL_SCHEME GetScheme() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den [ATL_URL_SCHEME](atl-url-scheme-enum.md) Wert zurück, der das Schema der URL beschreibt.

## <a name="curlgetschemename"></a><a name="getschemename"></a>CUrl::GetSchemeName

Rufen Sie diese Methode auf, um den Namen des URL-Schemas abzurufen.

```
inline LPCTSTR GetSchemeName() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den URL-Schemanamen zurück (z. B. "http" oder "ftp").

## <a name="curlgetschemenamelength"></a><a name="getschemenamelength"></a>CUrl::GetSchemeNameLength

Rufen Sie diese Methode auf, um die Länge des URL-Schemanamens abzurufen.

```
inline DWORD GetSchemeNameLength() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Namenslänge des URL-Schemas zurück.

## <a name="curlgeturllength"></a><a name="geturllength"></a>CUrl::GetUrlLength

Rufen Sie diese Methode auf, um die URL-Länge abzurufen.

```
inline DWORD GetUrlLength() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die URL-Länge zurück.

## <a name="curlgeturlpath"></a><a name="geturlpath"></a>CUrl::GetUrlPath

Rufen Sie diese Methode auf, um den URL-Pfad abzurufen.

```
inline LPCTSTR GetUrlPath() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den URL-Pfad zurück.

## <a name="curlgeturlpathlength"></a><a name="geturlpathlength"></a>CUrl::GetUrlPathLength

Rufen Sie diese Methode auf, um die URL-Pfadlänge abzurufen.

```
inline DWORD GetUrlPathLength() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die URL-Pfadlänge zurück.

## <a name="curlgetusername"></a><a name="getusername"></a>CUrl::GetUserName

Rufen Sie diese Methode auf, um den Benutzernamen von der URL abzurufen.

```
inline LPCTSTR GetUserName() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den Benutzernamen zurück.

## <a name="curlgetusernamelength"></a><a name="getusernamelength"></a>CUrl::GetUserNameLength

Rufen Sie diese Methode auf, um die Länge des Benutzernamens abzurufen.

```
inline DWORD GetUserNameLength() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Länge des Benutzernamens zurück.

## <a name="curloperator-"></a><a name="operator_eq"></a>CUrl::operator =

Weist das `CUrl` angegebene Objekt `CUrl` dem aktuellen Objekt zu.

```
CUrl& operator= (const CUrl& urlThat) throw();
```

### <a name="parameters"></a>Parameter

*urlThat*<br/>
Das `CUrl` Objekt, das in das aktuelle Objekt kopiert werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf das aktuelle Objekt zurück.

## <a name="curlsetextrainfo"></a><a name="setextrainfo"></a>Curl::SetExtraInfo

Rufen Sie diese Methode auf, um die zusätzlichen Informationen (z. B. *Text* oder *Text*) der URL festzulegen.

```
inline BOOL SetExtraInfo(LPCTSTR lpszInfo) throw();
```

### <a name="parameters"></a>Parameter

*lpszInfo*<br/>
Die Zeichenfolge, die die zusätzlichen Informationen enthält, die in die URL aufgenommen werden sollen.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

## <a name="curlsethostname"></a><a name="sethostname"></a>CUrl::SetHostName

Rufen Sie diese Methode auf, um den Hostnamen festzulegen.

```
inline BOOL SetHostName(LPCTSTR lpszHost) throw();
```

### <a name="parameters"></a>Parameter

*lpszHost*<br/>
Der Hostname.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

## <a name="curlsetpassword"></a><a name="setpassword"></a>CUrl::SetPassword

Rufen Sie diese Methode auf, um das Kennwort festzulegen.

```
inline BOOL SetPassword(LPCTSTR lpszPass) throw();
```

### <a name="parameters"></a>Parameter

*lpszPass*<br/>
Das Kennwort.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

## <a name="curlsetportnumber"></a><a name="setportnumber"></a>Curl::SetPortNumber

Rufen Sie diese Methode auf, um die Portnummer festzulegen.

```
inline BOOL SetPortNumber(ATL_URL_PORT nPrt) throw();
```

### <a name="parameters"></a>Parameter

*nPrt*<br/>
Die Portnummer.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

## <a name="curlsetscheme"></a><a name="setscheme"></a>CUrl::SetScheme

Rufen Sie diese Methode auf, um das URL-Schema festzulegen.

```
inline BOOL SetScheme(ATL_URL_SCHEME nScheme) throw();
```

### <a name="parameters"></a>Parameter

*nScheme*<br/>
Einer der [ATL_URL_SCHEME](atl-url-scheme-enum.md) Werte für das Schema.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Sie können das Schema auch nach Namen festlegen (siehe [CUrl::SetSchemeName](#setschemename)).

## <a name="curlsetschemename"></a><a name="setschemename"></a>CUrl::SetSchemeName

Rufen Sie diese Methode auf, um den URL-Schemanamen festzulegen.

```
inline BOOL SetSchemeName(LPCTSTR lpszSchm) throw();
```

### <a name="parameters"></a>Parameter

*lpszSchm*<br/>
Der Name des URL-Schemas.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Sie können das Schema auch mit einer [ATL_URL_SCHEME](atl-url-scheme-enum.md) konstante festlegen (siehe [CUrl::SetScheme](#setscheme)).

## <a name="curlseturlpath"></a><a name="seturlpath"></a>CUrl::SetUrlPath

Rufen Sie diese Methode auf, um den URL-Pfad festzulegen.

```
inline BOOL SetUrlPath(LPCTSTR lpszPath) throw();
```

### <a name="parameters"></a>Parameter

*lpszPath*<br/>
Der URL-Pfad.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

## <a name="curlsetusername"></a><a name="setusername"></a>CUrl::SetUserName

Rufen Sie diese Methode auf, um den Benutzernamen festzulegen.

```
inline BOOL SetUserName(LPCTSTR lpszUser) throw();
```

### <a name="parameters"></a>Parameter

*lpszUser*<br/>
Der Benutzername.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

## <a name="see-also"></a>Siehe auch

[Klassen](../../atl/reference/atl-classes.md)
