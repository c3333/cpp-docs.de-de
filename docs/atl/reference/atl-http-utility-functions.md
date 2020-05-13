---
title: ATL-http-Hilfsprogrammfunktionen
ms.date: 11/04/2016
ms.assetid: 4db57ef2-31fa-4696-bbeb-79a9035033ed
ms.openlocfilehash: c95681503da0d661382e6da33bd33e8f2004838b
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168604"
---
# <a name="atl-http-utility-functions"></a>ATL-http-Hilfsprogrammfunktionen

Diese Funktionen unterstützen die Bearbeitung von URLs.

|||
|-|-|
|[AtlCanonicalizeUrl](#atlcanonicalizeurl)|Kanonisiert eine URL, die das Umwandeln unsicherer Zeichen und Leerzeichen in Escapesequenzen einschließt.|
|[AtlCombineUrl](#atlcombineurl)|Kombiniert eine Basis-URL und eine relative URL in einer einzelnen, kanonischen URL.|
|[AtlEscapeUrl](#atlescapeurl)|Konvertiert alle unsicheren Zeichen in Escapesequenzen.|
|[AtlGetDefaultUrlPort](#atlgetdefaulturlport)|Ruft die Standard Portnummer ab, die einem bestimmten Internet Protokoll oder-Schema zugeordnet ist.|
|[AtlIsUnsafeUrlChar](#atlisunsafeurlchar)|Bestimmt, ob ein Zeichen für die Verwendung in einer URL sicher ist.|
|[AtlUnescapeUrl](#atlunescapeurl)|Konvertiert Escapezeichen zurück in ihre ursprünglichen Werte.|
|[RGBToHtml](#rgbtohtml)|Konvertiert einen [COLORREF](/windows/win32/gdi/colorref) -Wert in den HTML-Text, der diesem Farbwert entspricht.|
|[SystemTimeToHttpDate](#systemtimetohttpdate)|Mit dieser Funktion konvertieren Sie die Systemzeit in eine Zeichenfolge, deren Format sich für die Verwendung in HTTP-Headern eignet.|

## <a name="requirements"></a>Anforderungen

**Header:** atlutil. h

## <a name="atlcanonicalizeurl"></a><a name="atlcanonicalizeurl"></a>Atlcanonicalizeurl

Mit dieser Funktion wird eine URL kanonisiert, wobei unsichere Zeichen und Leerzeichen in Escapesequenzen konvertiert werden.

```cpp
inline BOOL AtlCanonicalizeUrl(
   LPCTSTR szUrl,
   LPTSTR szCanonicalized,
   DWORD* pdwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parameter

*szURL*<br/>
Die URL, die kanonisiert werden soll.

*szcanonicalized*<br/>
Vom Aufrufer zugeordneter Puffer zum Empfangen der kanonisierten URL.

*pdwmaxlength*<br/>
Ein Zeiger auf eine Variable, die die Länge in Zeichen von *szcanonicalized*enthält. Wenn die Funktion erfolgreich ausgeführt wird, empfängt die-Variable die Anzahl der in den Puffer geschriebenen Zeichen, einschließlich des abschließenden NULL-Zeichens. Wenn die Funktion fehlschlägt, erhält die Variable die erforderliche Länge des Puffers in Byte, einschließlich des leer Zeichens für das abschließende Null Zeichen.

*dwFlags*<br/>
ATL_URL Flags, die das Verhalten dieser Funktion steuern.

- ATL_URL_BROWSER_MODE codiert oder decodiert keine Zeichen nach "#" oder "?" und entfernt nachfolgende Leerzeichen nach "?" nicht. Wenn dieser Wert nicht angegeben wird, wird die gesamte URL codiert, und nachfolgende Leerzeichen werden entfernt.

- ATL_URL_DECODE konvertiert alle% XX-Sequenzen in Zeichen, einschließlich Escapesequenzen, bevor die URL analysiert wird.

- ATL_URL_ENCODE_PERCENT codiert alle gefundenen Prozentzeichen. Standardmäßig werden Prozentzeichen nicht codiert.

- ATL_URL_ENCODE_SPACES_ONLY nur Leerzeichen codieren.

- ATL_URL_ESCAPE konvertiert alle Escapesequenzen (% XX) in die entsprechenden Zeichen.

- ATL_URL_NO_ENCODE konvertiert unsichere Zeichen nicht in Escapesequenzen.

- ATL_URL_NO_META entfernt keine Metasequenzen (z. b. "." und "..") aus der URL.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, false bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

Verhält sich wie die aktuelle Version von [internetcanonicalizeurl](/windows/win32/api/wininet/nf-wininet-internetcanonicalizeurlw) , erfordert jedoch nicht, dass WinInet oder Internet Explorer installiert wird.

## <a name="atlcombineurl"></a><a name="atlcombineurl"></a>Atlcombineurl

Mit dieser Funktion wird eine Basis-URL und eine relative URL zu einer einzelnen kanonischen URL zusammengefasst.

```cpp
inline BOOL AtlCombineUrl(
   LPCTSTR szBaseUrl,
   LPCTSTR szRelativeUrl,
   LPTSTR szBuffer,
   DWORD* pdwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parameter

*szbaseurl*<br/>
Der Basis-URL.

*szrelativeurl*<br/>
Die URL relativ zur Basis-URL.

*szBuffer*<br/>
Vom Aufrufer zugeordneter Puffer zum Empfangen der kanonisierten URL.

*pdwmaxlength*<br/>
Ein Zeiger auf eine Variable, die die Länge in Zeichen von *szBuffer*enthält. Wenn die Funktion erfolgreich ausgeführt wird, empfängt die-Variable die Anzahl der in den Puffer geschriebenen Zeichen, einschließlich des abschließenden NULL-Zeichens. Wenn die Funktion fehlschlägt, erhält die Variable die erforderliche Länge des Puffers in Byte, einschließlich des leer Zeichens für das abschließende Null Zeichen.

*dwFlags*<br/>
Flags, die das Verhalten dieser Funktion steuern. Weitere Informationen finden Sie unter [atlcanonicalizeurl](#atlcanonicalizeurl).

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, false bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

Verhält sich wie die aktuelle Version von [internetcombineurl](/windows/win32/api/wininet/nf-wininet-internetcombineurlw) , erfordert jedoch nicht, dass WinInet oder Internet Explorer installiert wird.

## <a name="atlescapeurl"></a><a name="atlescapeurl"></a>Atlescapeurl

Mit dieser Funktion werden alle unsicheren Zeichen in Escapesequenzen konvertiert.

```cpp
inline BOOL AtlEscapeUrl(
   LPCSTR szStringIn,
   LPSTR szStringOut,
   DWORD* pdwStrLen,
   DWORD dwMaxLength,
   DWORD dwFlags = 0) throw();

inline BOOL AtlEscapeUrl(
   LPCWSTR szStringIn,
   LPWSTR szStringOut,
   DWORD* pdwStrLen,
   DWORD dwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parameter

*lpszstringin*<br/>
Die URL, die konvertiert werden soll.

*lpszstringout*<br/>
Der vom Aufrufer zugewiesene Puffer, in den die konvertierte URL geschrieben wird.

*pdwstrinlen*<br/>
Zeiger auf eine DWORD-Variable. Wenn die Funktion erfolgreich ausgeführt wird, empfängt *pdwstraulen* die Anzahl der in den Puffer geschriebenen Zeichen, einschließlich des abschließenden NULL-Zeichens. Wenn die Funktion fehlschlägt, erhält die Variable die erforderliche Länge des Puffers in Byte, einschließlich des leer Zeichens für das abschließende Null Zeichen. Bei Verwendung der breit Zeichen Version dieser Methode empfängt *pdwstraulen* die erforderliche Anzahl von Zeichen, nicht die Anzahl der Bytes.

*dwmaxlength*<br/>
Die Größe des Puffers *lpszstringout*.

*dwFlags*<br/>
ATL_URL Flags, die das Verhalten dieser Funktion steuern. Mögliche Werte finden Sie unter [atlcanonicalizeurl](#atlcanonicalizeurl) .

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, false bei einem Fehler.

## <a name="atlgetdefaulturlport"></a><a name="atlgetdefaulturlport"></a>Atlgetdefaulturlport

Mit dieser Funktion wird die Standardportnummer abgerufen, die einem bestimmten Internetprotokoll oder -schema zugeordnet ist.

```cpp
inline ATL_URL_PORT AtlGetDefaultUrlPort(ATL_URL_SCHEME m_nScheme) throw();
```

### <a name="parameters"></a>Parameter

*m_nScheme*<br/>
Der [ATL_URL_SCHEME](atl-url-scheme-enum.md) -Wert, der das Schema identifiziert, für das Sie die Portnummer abrufen möchten.

### <a name="return-value"></a>Rückgabewert

Die [ATL_URL_PORT](atl-typedefs.md#atl_url_port) , die dem angegebenen Schema zugeordnet ist, oder ATL_URL_INVALID_PORT_NUMBER, wenn das Schema nicht erkannt wird.

## <a name="atlisunsafeurlchar"></a><a name="atlisunsafeurlchar"></a>Atlisunsafeurlchar

Mit dieser Funktion finden Sie heraus, ob die Verwendung eines bestimmten Zeichens in einer URL sicher ist.

```cpp
inline BOOL AtlIsUnsafeUrlChar(char chIn) throw();
```

### <a name="parameters"></a>Parameter

*pflegt*<br/>
Das Zeichen, das auf Sicherheit geprüft werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn das Eingabezeichen unsicher ist, andernfalls false.

### <a name="remarks"></a>Bemerkungen

Zeichen, die nicht in URLs verwendet werden sollen, können mithilfe dieser Funktion getestet und mithilfe von [atlcanonicalizeurl](#atlcanonicalizeurl)konvertiert werden.

## <a name="atlunescapeurl"></a><a name="atlunescapeurl"></a>Atlunescapeurl

Mit dieser Funktion können Sie Escapezeichen zurück in ihre ursprünglichen Werte konvertieren.

```cpp
inline BOOL AtlUnescapeUrl(
   LPCSTR szStringIn,
   LPSTR szStringOut,
   LPDWORD pdwStrLen,
   DWORD dwMaxLength) throw();

inline BOOL AtlUnescapeUrl(
   LPCWSTR szStringIn,
   LPWSTR szStringOut,
   LPDWORD pdwStrLen,
   DWORD dwMaxLength) throw();
```

### <a name="parameters"></a>Parameter

*lpszstringin*<br/>
Die URL, die konvertiert werden soll.

*lpszstringout*<br/>
Der vom Aufrufer zugewiesene Puffer, in den die konvertierte URL geschrieben wird.

*pdwstrinlen*<br/>
Zeiger auf eine DWORD-Variable. Wenn die Funktion erfolgreich ausgeführt wird, empfängt die-Variable die Anzahl der in den Puffer geschriebenen Zeichen, einschließlich des abschließenden NULL-Zeichens. Wenn die Funktion fehlschlägt, erhält die Variable die erforderliche Länge des Puffers in Byte, einschließlich des leer Zeichens für das abschließende Null Zeichen.

*dwmaxlength*<br/>
Die Größe des Puffers *lpszstringout*.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, false bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

Kehrt den von [atlescapeurl](#atlescapeurl)angewendeten Konvertierungsprozess um.

## <a name="rgbtohtml"></a><a name="rgbtohtml"></a>Rgbzu HTML

Konvertiert einen [COLORREF](/windows/win32/gdi/colorref) -Wert in den HTML-Text, der diesem Farbwert entspricht.

```cpp
bool inline RGBToHtml(
   COLORREF color,
   LPTSTR pbOut,
   long nBuffer);
```

### <a name="parameters"></a>Parameter

*color*<br/>
Ein RGB-Farbwert.

*pbout*<br/>
Vom Aufrufer zugeordneter Puffer, der den Text für den HTML-Farbwert empfängt. Der Puffer muss Leerzeichen für mindestens 8 Zeichen enthalten, einschließlich Leerzeichen für das NULL-Terminator.

*npuffer*<br/>
Die Größe des Puffers in Bytes (einschließlich des leer Zeichens für das NULL-Terminator).

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, false bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

Ein HTML-Farbwert ist ein Nummern Zeichen, gefolgt von einem sechsstelligen Hexadezimalwert, wobei zwei Ziffern für jede der roten, grünen und blauen Komponenten der Farbe verwendet werden (z. b. #FFFFFF weiß).

## <a name="systemtimetohttpdate"></a><a name="systemtimetohttpdate"></a>Systemtimedehttpdate

Mit dieser Funktion konvertieren Sie die Systemzeit in eine Zeichenfolge, deren Format sich für die Verwendung in HTTP-Headern eignet.

```cpp
inline void SystemTimeToHttpDate(
   const SYSTEMTIME& st,
   CStringA& strTime);
```

### <a name="parameters"></a>Parameter

*St*<br/>
Die Systemzeit, die als HTTP-Format Zeichenfolge abgerufen werden soll.

*Straume*<br/>
Ein Verweis auf eine Zeichen folgen Variable, die die in RFC 2616 ([https://www.ietf.org/rfc/rfc2616.txt](https://www.ietf.org/rfc/rfc2616.txt)) und RFC 1123 ([https://www.ietf.org/rfc/rfc1123.txt](https://www.ietf.org/rfc/rfc1123.txt)) definierte http-Datumsangabe empfangen soll.

## <a name="see-also"></a>Weitere Informationen:

[Konzepte](../active-template-library-atl-concepts.md)<br/>
[ATL-COM-Desktop-Komponenten](../atl-com-desktop-components.md)<br/>
[Internetcanonicalizeurl](/windows/win32/api/wininet/nf-wininet-internetcanonicalizeurlw)
