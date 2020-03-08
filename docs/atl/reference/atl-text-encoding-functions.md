---
title: ATL-Text Codierungs Funktionen
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlGetHexValue
- atlbase/ATL::AtlGetVersion
- atlenc/ATL::AtlHexDecode
- atlenc/ATL::AtlHexDecodeGetRequiredLength
- atlenc/ATL::AtlHexEncode
- atlenc/ATL::AtlHexEncodeGetRequiredLength
- atlenc/ATL::AtlHexValue
- atlenc/ATL::BEncode
- atlenc/ATL::BEncodeGetRequiredLength
- atlenc/ATL::EscapeXML
- atlenc/ATL::GetExtendedChars
- atlenc/ATL::IsExtendedChar
- atlenc/ATL::QEncode
- atlenc/ATL::QEncodeGetRequiredLength
- atlenc/ATL::QPDecode
- atlenc/ATL::QPDecodeGetRequiredLength
- atlenc/ATL::QPEncode
- atlenc/ATL::QPEncodeGetRequiredLength
- atlenc/ATL::UUDecode
- atlenc/ATL::UUDecodeGetRequiredLength
- atlenc/ATL::UUEncode
- atlenc/ATL::UUEncodeGetRequiredLength
ms.assetid: 2ae1648b-2b87-4112-92aa-0069fcfd23da
ms.openlocfilehash: 1380d33c485c1ac895558bbcaf86c902c6074cd4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865028"
---
# <a name="atl-text-encoding-functions"></a>ATL-Text Codierungs Funktionen

Diese Funktionen unterstützen die Text Codierung und-Decodierung.

|||
|-|-|
|[Atlgethexvalue](#atlgethexvalue)|Mit dieser Funktion wird der numerische Wert einer Hexadezimalziffer abgerufen.|
|[Atlgetversion](#atlgetversion)|Mit dieser Funktion können Sie die Version der ATL-Bibliothek abrufen, die Sie verwenden.  |
|[Atlhexdecode](#atlhexdecode)|Decodiert eine Zeichenfolge von Daten, die als hexadezimal Text codiert wurde, z. b. durch einen vorherigen-Befehl von [atlhexencode](#atlhexencode).|
|[Atlhexdecodegetrequiredlength](#atlhexdecodegetrequiredlength)|Mit dieser Funktion können Sie die Größe eines Puffers in Bytes abrufen, der die Daten enthalten kann, die aus einer hexadezimal codierten Zeichenfolge der angegebenen Länge decodiert wurden.|
|[Atlhexencode](#atlhexencode)|Mit dieser Funktion werden einige Daten als Zeichenfolge mit hexadezimalem Text codiert.|
|[Atlhexencode getrequiredlength](#atlhexencodegetrequiredlength)|Mit dieser Funktion können Sie die Größe eines Puffers in Zeichen abrufen, der eine Zeichenfolge enthalten kann, die aus Daten der angegebenen Größe codiert wurde.|
|[Atlhexvalue](#atlhexvalue)|Mit dieser Funktion wird der numerische Wert einer Hexadezimalziffer abgerufen. |
|[AtlUnicodeToUTF8](#atlunicodetoutf8)|Mit dieser Funktion können Sie eine Unicode-Zeichenfolge in UTF-8 konvertieren. |
|[BEncode](#bencode)|Mit dieser Funktion werden einige Daten mit "B"-Codierung konvertiert.|
|[Bencodegetrequiredlength](#bencodegetrequiredlength)|Mit dieser Funktion können Sie die Größe eines Puffers in Zeichen abrufen, der eine Zeichenfolge enthalten kann, die aus Daten der angegebenen Größe codiert wurde.|
|["Escapexml"](#escapexml)|Mit dieser Funktion werden für die Verwendung in XML unsichere Zeichen in sichere Zeichen konvertiert.|
|[Getextendecodchars](#getextendedchars)|Mit dieser Funktion können Sie die Anzahl von Sonderzeichen in einer Zeichenfolge abrufen.|
|[Isextendecodchar](#isextendedchar)|Mit dieser Funktion können Sie herausfinden, ob ein bestimmtes Zeichen ein erweitertes Zeichen ist (kleiner als 32, größer als 126 und keine Registerkarte, Zeilenvorschub oder Wagen Rücklauf).|
|[Qcodieren](#qencode)|Mit dieser Funktion werden einige Daten mit "Q"-Codierung konvertiert.  |
|[Qencode getrequiredlength](#qencodegetrequiredlength)|Mit dieser Funktion können Sie die Größe eines Puffers in Zeichen abrufen, der eine Zeichenfolge enthalten kann, die aus Daten der angegebenen Größe codiert wurde.|
|[Qpdecode](#qpdecode)|Decodiert eine Zeichenfolge von Daten, die in einem druckbaren Format in Anführungszeichen codiert wurden, z. b. durch einen vorherigen [qtzcode](#qpencode)-Rückruf.|
|[Qpdecodegetrequiredlength](#qpdecodegetrequiredlength)|Mit dieser Funktion können Sie die Größe eines Puffers in Bytes abrufen, der die Daten enthalten kann, die aus einer Zeichenfolge der angegebenen Länge in einem druckbaren Format mit Anführungszeichen decodiert wurden.|
|[Qpcode](#qpencode)|Mit dieser Funktion können Sie Daten in ein druckbares Format mit Anführungszeichen codieren.|
|[Qarmcodegetrequiredlength](#qpencodegetrequiredlength)|Mit dieser Funktion können Sie die Größe eines Puffers in Zeichen abrufen, der eine Zeichenfolge enthalten kann, die aus Daten der angegebenen Größe codiert wurde.|
|[Uudecode](#uudecode)|Decodiert eine Zeichenfolge von Daten, die uucodiert wurde, wie z. b. durch einen vorherigen-Befehl von [UUEncode](#uuencode).|
|[Uudecodegetrequiredlength](#uudecodegetrequiredlength)|Mit dieser Funktion können Sie die Größe eines Puffers in Bytes abrufen, der die Daten enthalten kann, die aus einer UUEncoded-Zeichenfolge der angegebenen Länge decodiert wurden.|
|[UUEncode](#uuencode)|Mit dieser Funktion können Sie Daten in UUEncoded-Daten codieren. |
|[Uuencodecogetrequiredlength](#uuencodegetrequiredlength)|Mit dieser Funktion können Sie die Größe eines Puffers in Zeichen abrufen, der eine Zeichenfolge enthalten kann, die aus Daten der angegebenen Größe codiert wurde.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlenc. h

## <a name="atlgethexvalue"></a>Atlgethexvalue

Mit dieser Funktion wird der numerische Wert einer Hexadezimalziffer abgerufen.

```
inline char AtlGetHexValue(char chIn) throw();
```

### <a name="parameters"></a>Parameter

*pflegt*<br/>
Das hexadezimale Zeichen ' 0 '-' 9 ', ' a '-' f ' oder ' a '-' f '.

### <a name="return-value"></a>Rückgabewert

Der numerische Wert des Eingabe Zeichens, das als hexadezimale Ziffer interpretiert wird. Eine Eingabe von "0" gibt z. b. den Wert 0 zurück, und die Eingabe von "a" gibt den Wert "10" zurück. Wenn es sich bei dem Eingabezeichen nicht um eine hexadezimale Ziffer handelt, gibt diese Funktion-1 zurück.

## <a name="atlgetversion"></a>Atlgetversion

Mit dieser Funktion können Sie die Version der ATL-Bibliothek abrufen, die Sie verwenden.

```
ATLAPI_(DWORD) AtlGetVersion(void* pReserved);
```

### <a name="parameters"></a>Parameter

*erhaltene*<br/>
Ein reservierter Zeiger.

### <a name="return-value"></a>Rückgabewert

Gibt einen DWORD-ganzzahligen Wert der Version der ATL-Bibliothek zurück, die Sie kompilieren oder ausführen.

## <a name="example"></a>Beispiel

Die-Funktion sollte wie folgt aufgerufen werden.

[!code-cpp[NVC_ATL_Utilities#95](../../atl/codesnippet/cpp/atl-text-encoding-functions_1.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="atlhexdecode"></a>Atlhexdecode

Decodiert eine Zeichenfolge von Daten, die als hexadezimal Text codiert wurde, z. b. durch einen vorherigen-Befehl von [atlhexencode](#atlhexencode).

```
inline BOOL AtlHexDecode(
   LPCSTR pSrcData,
   int nSrcLen,
   LPBYTE pbDest,
   int* pnDestLen) throw();
```

### <a name="parameters"></a>Parameter

*pSrcData*<br/>
Die Zeichenfolge, die die Daten enthält, die decodiert werden sollen.

*nsrclen*<br/>
Die Länge in Zeichen von *pSrcData*.

*pbdest*<br/>
Vom Aufrufer zugeordneter Puffer zum Empfangen der decodierten Daten.

*pndestlen*<br/>
Ein Zeiger auf eine Variable, die die Länge des *pbdest*in Bytes enthält. Wenn die Funktion erfolgreich ausgeführt wird, empfängt die Variable die Anzahl der in den Puffer geschriebenen Bytes. Wenn die Funktion fehlschlägt, erhält die Variable die erforderliche Länge des Puffers in Bytes.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, false bei einem Fehler.

## <a name="atlhexdecodegetrequiredlength"></a>Atlhexdecodegetrequiredlength

Mit dieser Funktion können Sie die Größe eines Puffers in Bytes abrufen, der die Daten enthalten kann, die aus einer hexadezimal codierten Zeichenfolge der angegebenen Länge decodiert wurden.

```
inline int AtlHexDecodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>Parameter

*nsrclen*<br/>
Die Anzahl der Zeichen in der codierten Zeichenfolge.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Bytes, die für einen Puffer erforderlich sind, der eine decodierte Zeichenfolge von *nsrclen* -Zeichen enthalten kann.

## <a name="atlhexencode"></a>Atlhexencode

Mit dieser Funktion werden einige Daten als Zeichenfolge mit hexadezimalem Text codiert.

```
inline BOOL AtlHexEncode(
   const BYTE * pbSrcData,
   int nSrcLen,
   LPSTR szDest,
int * pnDestLen) throw();
```

### <a name="parameters"></a>Parameter

*pbsrcdata*<br/>
Der Puffer, der die zu codierenden Daten enthält.

*nsrclen*<br/>
Die Länge der zu codierenden Daten in Bytes.

*szdest*<br/>
Vom Aufrufer zugeordneter Puffer zum Empfangen der codierten Daten.

*pndestlen*<br/>
Ein Zeiger auf eine Variable, die die Länge in Zeichen von *szdest*enthält. Wenn die Funktion erfolgreich ausgeführt wird, empfängt die Variable die Anzahl der in den Puffer geschriebenen Zeichen. Wenn die Funktion fehlschlägt, erhält die Variable die erforderliche Länge in Zeichen des Puffers.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, false bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

Jedes Byte der Quelldaten wird als zwei hexadezimale Zeichen codiert.

## <a name="atlhexencodegetrequiredlength"></a>Atlhexencode getrequiredlength

Mit dieser Funktion können Sie die Größe eines Puffers in Zeichen abrufen, der eine Zeichenfolge enthalten kann, die aus Daten der angegebenen Größe codiert wurde.

```
inline int AtlHexEncodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>Parameter

*nsrclen*<br/>
Die Anzahl der Daten bytes, die codiert werden sollen.

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Zeichen, die für einen Puffer erforderlich sind, der codierte Daten von *nsrclen* -Bytes enthalten kann.

## <a name="atlhexvalue"></a>Atlhexvalue

Mit dieser Funktion wird der numerische Wert einer Hexadezimalziffer abgerufen.

```
inline short AtlHexValue(char chIn) throw();
```

### <a name="parameters"></a>Parameter

*pflegt*<br/>
Das hexadezimale Zeichen ' 0 '-' 9 ', ' a '-' f ' oder ' a '-' f '.

### <a name="return-value"></a>Rückgabewert

Der numerische Wert des Eingabe Zeichens, das als hexadezimale Ziffer interpretiert wird. Eine Eingabe von "0" gibt z. b. den Wert 0 zurück, und die Eingabe von "a" gibt den Wert "10" zurück. Wenn es sich bei dem Eingabezeichen nicht um eine hexadezimale Ziffer handelt, gibt diese Funktion-1 zurück.

## <a name="atlunicodetoutf8"></a>AtlUnicodeToUTF8

Mit dieser Funktion können Sie eine Unicode-Zeichenfolge in UTF-8 konvertieren.

```
ATL_NOINLINE inline int AtlUnicodeToUTF8(
   LPCWSTR wszSrc,
   int nSrc,
   LPSTR szDest,
   int nDest) throw();
```

### <a name="parameters"></a>Parameter

*wszsrc*<br/>
Die zu konvertierende Unicode-Zeichenfolge

*nsrc*<br/>
Die Länge der Unicode-Zeichenfolge in Zeichen.

*szdest*<br/>
Vom Aufrufer zugewiesener Puffer zum Empfangen der konvertierten Zeichenfolge.

*ndest*<br/>
Die Länge des Puffers in Bytes.

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Zeichen für die konvertierte Zeichenfolge zurück.

### <a name="remarks"></a>Bemerkungen

Um die Größe des Puffers zu bestimmen, der für die konvertierte Zeichenfolge erforderlich ist, müssen Sie diese Funktion mit 0 für *szdest* und *ndest*übergeben.

## <a name="bencode"></a>BEncode

Mit dieser Funktion werden einige Daten mit "B"-Codierung konvertiert.

```
inline BOOL BEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCSTR pszCharSet) throw();
```

### <a name="parameters"></a>Parameter

*pbsrcdata*<br/>
Der Puffer, der die zu codierenden Daten enthält.

*nsrclen*<br/>
Die Länge der zu codierenden Daten in Bytes.

*szdest*<br/>
Vom Aufrufer zugeordneter Puffer zum Empfangen der codierten Daten.

*pndestlen*<br/>
Ein Zeiger auf eine Variable, die die Länge in Zeichen von *szdest*enthält. Wenn die Funktion erfolgreich ausgeführt wird, empfängt die Variable die Anzahl der in den Puffer geschriebenen Zeichen. Wenn die Funktion fehlschlägt, erhält die Variable die erforderliche Länge in Zeichen des Puffers.

*pszcharset*<br/>
Der für die Konvertierung zu verwendende Zeichensatz.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, false bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

Das Codierungsschema "B" wird in RFC 2047 ([https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt)) beschrieben.

## <a name="bencodegetrequiredlength"></a>Bencodegetrequiredlength

Mit dieser Funktion können Sie die Größe eines Puffers in Zeichen abrufen, der eine Zeichenfolge enthalten kann, die aus Daten der angegebenen Größe codiert wurde.

```
inline int BEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();
```

### <a name="parameters"></a>Parameter

*nsrclen*<br/>
Die Anzahl der Daten bytes, die codiert werden sollen.

*ncharsetlen*<br/>
Die Länge in Zeichen des Zeichensatzes, der für die Konvertierung verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Zeichen, die für einen Puffer erforderlich sind, der codierte Daten von *nsrclen* -Bytes enthalten kann.

### <a name="remarks"></a>Bemerkungen

Das Codierungsschema "B" wird in RFC 2047 ([https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt)) beschrieben.

## <a name="escapexml"></a>"Escapexml"

Mit dieser Funktion werden für die Verwendung in XML unsichere Zeichen in sichere Zeichen konvertiert.

```
inline int EscapeXML(
   const wchar_t * szIn,
   int nSrcLen,
   wchar_t * szEsc,
   int nDestLen,
   DWORD dwFlags = ATL_ESC_FLAG_NONE) throw();
```

### <a name="parameters"></a>Parameter

*Szin*<br/>
Die zu konvertierende Zeichenfolge.

*nsrclen*<br/>
Die Länge in Zeichen der zu konvertierenden Zeichenfolge.

*szesc*<br/>
Vom Aufrufer zugewiesener Puffer zum Empfangen der konvertierten Zeichenfolge.

*ndestlen*<br/>
Die Länge in Zeichen des vom Aufrufer zugewiesenen Puffers.

*dwFlags*<br/>
ATL_ESC Flags, die beschreiben, wie die Konvertierung durchgeführt werden soll.

- Standardverhalten ATL_ESC_FLAG_NONE. Anführungszeichen und Apostrophe werden nicht konvertiert.
- ATL_ESC_FLAG_ATTR Anführungszeichen und Apostrophe werden in `&quot;` bzw. `&apos;` konvertiert.

### <a name="return-value"></a>Rückgabewert

Die Länge in Zeichen der konvertierten Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

Mögliche Konvertierungen, die von dieser Funktion durchgeführt werden, werden in der Tabelle angezeigt:

|`Source`|Destination|
|------------|-----------------|
|\<|&lt;|
|>|&gt;|
|&|&amp;|
|'|&apos;|
|"|&quot;|

## <a name="getextendedchars"></a>Getextendecodchars

Mit dieser Funktion können Sie die Anzahl von Sonderzeichen in einer Zeichenfolge abrufen.

```
inline int GetExtendedChars(LPCSTR szSrc, int nSrcLen) throw();
```

### <a name="parameters"></a>Parameter

*szsrc*<br/>
Die zu analysierende Zeichenfolge.

*nsrclen*<br/>
Die Länge der Zeichenfolge in Zeichen.

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der in der Zeichenfolge gefundenen erweiterten Zeichen zurück, wie von [isextendecodchar](#isextendedchar)festgelegt.

## <a name="isextendedchar"></a>Isextendecodchar

Mit dieser Funktion können Sie herausfinden, ob ein bestimmtes Zeichen ein erweitertes Zeichen ist (kleiner als 32, größer als 126 und keine Registerkarte, Zeilenvorschub oder Wagen Rücklauf).

```
inline int IsExtendedChar(char ch) throw();
```

### <a name="parameters"></a>Parameter

*ch*<br/>
Das zu testende Zeichen.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Zeichen erweitert ist, andernfalls false.

## <a name="qencode"></a>Qcodieren

Mit dieser Funktion werden einige Daten mit "Q"-Codierung konvertiert.

```
inline BOOL QEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCSTR pszCharSet,
   int* pnNumEncoded = NULL) throw();
```

### <a name="parameters"></a>Parameter

*pbsrcdata*<br/>
Der Puffer, der die zu codierenden Daten enthält.

*nsrclen*<br/>
Die Länge der zu codierenden Daten in Bytes.

*szdest*<br/>
Vom Aufrufer zugeordneter Puffer zum Empfangen der codierten Daten.

*pndestlen*<br/>
Ein Zeiger auf eine Variable, die die Länge in Zeichen von *szdest*enthält. Wenn die Funktion erfolgreich ausgeführt wird, empfängt die Variable die Anzahl der in den Puffer geschriebenen Zeichen. Wenn die Funktion fehlschlägt, erhält die Variable die erforderliche Länge in Zeichen des Puffers.

*pszcharset*<br/>
Der für die Konvertierung zu verwendende Zeichensatz.

*pnnumcodiert*<br/>
Ein Zeiger auf eine Variable, die bei Rückgabe die Anzahl der unsicheren Zeichen enthält, die konvertiert werden mussten.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, false bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

Das Codierungsschema "Q" wird in RFC 2047 ([https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt)) beschrieben.

## <a name="qencodegetrequiredlength"></a>Qencode getrequiredlength

Mit dieser Funktion können Sie die Größe eines Puffers in Zeichen abrufen, der eine Zeichenfolge enthalten kann, die aus Daten der angegebenen Größe codiert wurde.

```
inline int QEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();
```

### <a name="parameters"></a>Parameter

*nsrclen*<br/>
Die Anzahl der Daten bytes, die codiert werden sollen.

*ncharsetlen*<br/>
Die Länge in Zeichen des Zeichensatzes, der für die Konvertierung verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Zeichen, die für einen Puffer erforderlich sind, der codierte Daten von *nsrclen* -Bytes enthalten kann.

### <a name="remarks"></a>Bemerkungen

Das Codierungsschema "Q" wird in RFC 2047 ([https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt)) beschrieben.

## <a name="qpdecode"></a>Qpdecode

Decodiert eine Zeichenfolge von Daten, die in einem druckbaren Format in Anführungszeichen codiert wurden, z. b. durch einen vorherigen [qtzcode](#qpencode)-Rückruf.

```
inline BOOL QPDecode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parameter

*pbsrcdata*<br/>
in Der Puffer, der die Daten enthält, die decodiert werden sollen.

*nsrclen*<br/>
in Die Länge in Bytes von *pbsrcdata*.

*szdest*<br/>
vorgenommen Vom Aufrufer zugeordneter Puffer zum Empfangen der decodierten Daten.

*pndestlen*<br/>
vorgenommen Ein Zeiger auf eine Variable, die die Länge in Bytes von *szdest*enthält. Wenn die Funktion erfolgreich ausgeführt wird, empfängt die Variable die Anzahl der in den Puffer geschriebenen Bytes. Wenn die Funktion fehlschlägt, erhält die Variable die erforderliche Länge des Puffers in Bytes.

*dwFlags*<br/>
in ATLSMTP_QPENCODE Flags, die beschreiben, wie die Konvertierung durchgeführt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, false bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

Das in Anführungszeichen eindruckbare Codierungsschema wird in RFC 2045 ([https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt)) beschrieben.

## <a name="qpdecodegetrequiredlength"></a>Qpdecodegetrequiredlength

Mit dieser Funktion können Sie die Größe eines Puffers in Bytes abrufen, der die Daten enthalten kann, die aus einer Zeichenfolge der angegebenen Länge in einem druckbaren Format mit Anführungszeichen decodiert wurden.

```
inline int QPDecodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>Parameter

*nsrclen*<br/>
Die Anzahl der Zeichen in der codierten Zeichenfolge.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Bytes, die für einen Puffer erforderlich sind, der eine decodierte Zeichenfolge von *nsrclen* -Zeichen enthalten kann.

### <a name="remarks"></a>Bemerkungen

Das in Anführungszeichen eindruckbare Codierungsschema wird in RFC 2045 ([https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt)) beschrieben.

## <a name="qpencode"></a>Qpcode

Mit dieser Funktion können Sie Daten in ein druckbares Format mit Anführungszeichen codieren.

```
inline BOOL QPEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   DWORD dwFlags = 0) throw ();
```

### <a name="parameters"></a>Parameter

*pbsrcdata*<br/>
Der Puffer, der die zu codierenden Daten enthält.

*nsrclen*<br/>
Die Länge der zu codierenden Daten in Bytes.

*szdest*<br/>
Vom Aufrufer zugeordneter Puffer zum Empfangen der codierten Daten.

*pndestlen*<br/>
Ein Zeiger auf eine Variable, die die Länge in Zeichen von *szdest*enthält. Wenn die Funktion erfolgreich ausgeführt wird, empfängt die Variable die Anzahl der in den Puffer geschriebenen Zeichen. Wenn die Funktion fehlschlägt, erhält die Variable die erforderliche Länge in Zeichen des Puffers.

*dwFlags*<br/>
ATLSMTP_QPENCODE Flags, die beschreiben, wie die Konvertierung durchgeführt werden soll.

- ATLSMTP_QPENCODE_DOT wenn ein Zeitraum am Anfang einer Zeile angezeigt wird, wird er der Ausgabe sowie codiert hinzugefügt.

- ATLSMTP_QPENCODE_TRAILING_SOFT fügt `=\r\n` an die codierte Zeichenfolge an.

Das in Anführungszeichen Druck Bare Codierungsschema wird in [RFC 2045](https://www.ietf.org/rfc/rfc2045.txt)beschrieben.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, false bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

Das in Anführungszeichen eindruckbare Codierungsschema wird in RFC 2045 ([https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt)) beschrieben.

## <a name="qpencodegetrequiredlength"></a>Qarmcodegetrequiredlength

Mit dieser Funktion können Sie die Größe eines Puffers in Zeichen abrufen, der eine Zeichenfolge enthalten kann, die aus Daten der angegebenen Größe codiert wurde.

```
inline int QPEncodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>Parameter

*nsrclen*<br/>
Die Anzahl der Daten bytes, die codiert werden sollen.

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Zeichen, die für einen Puffer erforderlich sind, der codierte Daten von *nsrclen* -Bytes enthalten kann.

### <a name="remarks"></a>Bemerkungen

Das in Anführungszeichen eindruckbare Codierungsschema wird in RFC 2045 ([https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt)) beschrieben.

## <a name="uudecode"></a>Uudecode

Decodiert eine Zeichenfolge von Daten, die uucodiert wurde, wie z. b. durch einen vorherigen-Befehl von [UUEncode](#uuencode).

```
inline BOOL UUDecode(
   BYTE* pbSrcData,
   int nSrcLen,
   BYTE* pbDest,
   int* pnDestLen) throw ();
```

### <a name="parameters"></a>Parameter

*pbsrcdata*<br/>
Die Zeichenfolge, die die Daten enthält, die decodiert werden sollen.

*nsrclen*<br/>
Die Länge in Bytes von *pbsrcdata*.

*pbdest*<br/>
Vom Aufrufer zugeordneter Puffer zum Empfangen der decodierten Daten.

*pndestlen*<br/>
Ein Zeiger auf eine Variable, die die Länge des *pbdest*in Bytes enthält. Wenn die Funktion erfolgreich ausgeführt wird, empfängt die Variable die Anzahl der in den Puffer geschriebenen Bytes. Wenn die Funktion fehlschlägt, erhält die Variable die erforderliche Länge des Puffers in Bytes.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, false bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

Diese uuencoding-Implementierung folgt der POSIX p 1003.2 b/D11-Spezifikation.

## <a name="uudecodegetrequiredlength"></a>Uudecodegetrequiredlength

Mit dieser Funktion können Sie die Größe eines Puffers in Bytes abrufen, der die Daten enthalten kann, die aus einer UUEncoded-Zeichenfolge der angegebenen Länge decodiert wurden.

```
inline int UUDecodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>Parameter

*nsrclen*<br/>
Die Anzahl der Zeichen in der codierten Zeichenfolge.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Bytes, die für einen Puffer erforderlich sind, der eine decodierte Zeichenfolge von *nsrclen* -Zeichen enthalten kann.

### <a name="remarks"></a>Bemerkungen

Diese uuencoding-Implementierung folgt der POSIX p 1003.2 b/D11-Spezifikation.

## <a name="uuencode"></a>UUEncode

Mit dieser Funktion können Sie Daten in UUEncoded-Daten codieren.

```
inline BOOL UUEncode(
   const BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCTSTR lpszFile = _T("file"),
   DWORD dwFlags = 0) throw ();
```

### <a name="parameters"></a>Parameter

*pbsrcdata*<br/>
Der Puffer, der die zu codierenden Daten enthält.

*nsrclen*<br/>
Die Länge der zu codierenden Daten in Bytes.

*szdest*<br/>
Vom Aufrufer zugeordneter Puffer zum Empfangen der codierten Daten.

*pndestlen*<br/>
Ein Zeiger auf eine Variable, die die Länge in Zeichen von *szdest*enthält. Wenn die Funktion erfolgreich ausgeführt wird, empfängt die Variable die Anzahl der in den Puffer geschriebenen Zeichen. Wenn die Funktion fehlschlägt, erhält die Variable die erforderliche Länge in Zeichen des Puffers.

*lpszfile*<br/>
Die Datei, die dem Header hinzugefügt werden soll, wenn ATLSMTP_UUENCODE_HEADER in *dwFlags*angegeben wird.

*dwFlags*<br/>
Flags, die das Verhalten dieser Funktion steuern.

- , ATLSMTP_UUENCODE_HEADE der Header codiert wird.

- ATLSMTP_UUENCODE_END das Ende codiert wird.

- ATLSMTP_UUENCODE_DOT datenstuffing wird ausgeführt.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, false bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

Diese uuencoding-Implementierung folgt der POSIX p 1003.2 b/D11-Spezifikation.

## <a name="uuencodegetrequiredlength"></a>Uuencodecogetrequiredlength

Mit dieser Funktion können Sie die Größe eines Puffers in Zeichen abrufen, der eine Zeichenfolge enthalten kann, die aus Daten der angegebenen Größe codiert wurde.

```
inline int UUEncodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>Parameter

*nsrclen*<br/>
Die Anzahl der Daten bytes, die codiert werden sollen.

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Zeichen, die für einen Puffer erforderlich sind, der codierte Daten von *nsrclen* -Bytes enthalten kann.

### <a name="remarks"></a>Bemerkungen

Diese uuencoding-Implementierung folgt der POSIX p 1003.2 b/D11-Spezifikation.

## <a name="see-also"></a>Weitere Informationen

[Konzepte](../active-template-library-atl-concepts.md)<br/>
[ATL-COM-Desktop-Komponenten](../atl-com-desktop-components.md)
