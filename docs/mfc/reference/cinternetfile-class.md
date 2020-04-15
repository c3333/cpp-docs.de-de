---
title: CInternetFile-Klasse
ms.date: 11/04/2016
f1_keywords:
- CInternetFile
- AFXINET/CInternetFile
- AFXINET/CInternetFile::CInternetFile
- AFXINET/CInternetFile::Abort
- AFXINET/CInternetFile::Close
- AFXINET/CInternetFile::Flush
- AFXINET/CInternetFile::GetLength
- AFXINET/CInternetFile::Read
- AFXINET/CInternetFile::ReadString
- AFXINET/CInternetFile::Seek
- AFXINET/CInternetFile::SetReadBufferSize
- AFXINET/CInternetFile::SetWriteBufferSize
- AFXINET/CInternetFile::Write
- AFXINET/CInternetFile::WriteString
- AFXINET/CInternetFile::m_hFile
helpviewer_keywords:
- CInternetFile [MFC], CInternetFile
- CInternetFile [MFC], Abort
- CInternetFile [MFC], Close
- CInternetFile [MFC], Flush
- CInternetFile [MFC], GetLength
- CInternetFile [MFC], Read
- CInternetFile [MFC], ReadString
- CInternetFile [MFC], Seek
- CInternetFile [MFC], SetReadBufferSize
- CInternetFile [MFC], SetWriteBufferSize
- CInternetFile [MFC], Write
- CInternetFile [MFC], WriteString
- CInternetFile [MFC], m_hFile
ms.assetid: 96935681-ee71-4a8d-9783-5abc7b3e6f10
ms.openlocfilehash: e3f1a7167f5464423754951764c4441513197841
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372402"
---
# <a name="cinternetfile-class"></a>CInternetFile-Klasse

Ermöglicht den Zugriff auf Dateien auf Remotesystemen, die Internetprotokolle verwenden.

## <a name="syntax"></a>Syntax

```
class CInternetFile : public CStdioFile
```

## <a name="members"></a>Member

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CInternetFile::CInternetFile](#cinternetfile)|Erstellt ein `CInternetFile`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CInternetFile::Abbruch](#abort)|Schließt die Datei und ignoriert alle Warnungen und Fehler.|
|[CInternetFile::Schließen](#close)|Schließt a `CInternetFile` und gibt seine Ressourcen frei.|
|[CInternetFile::Flush](#flush)|Löscht den Inhalt des Schreibpuffers und stellt sicher, dass die Daten im Speicher auf den Zielcomputer geschrieben werden.|
|[CInternetFile::GetLength](#getlength)|Gibt die Größe der Datei zurück.|
|[CInternetFile::Lesen](#read)|Liest die Anzahl der angegebenen Bytes.|
|[CInternetFile::ReadString](#readstring)|Liest einen Datenstrom von Zeichen.|
|[CInternetFile::Suchen](#seek)|Positioniert den Zeiger in einer geöffneten Datei neu.|
|[CInternetFile::SetReadBufferSize](#setreadbuffersize)|Legt die Größe des Puffers fest, in dem Daten gelesen werden.|
|[CInternetFile::SetWriteBufferSize](#setwritebuffersize)|Legt die Größe des Puffers fest, in den Daten geschrieben werden.|
|[CInternetFile::Schreiben](#write)|Schreibt die Anzahl der angegebenen Bytes.|
|[CInternetFile::WriteString](#writestring)|Schreibt eine null-terminierte Zeichenfolge in eine Datei.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CInternetFile::operator HINTERNET](#operator_hinternet)|Ein Gießereison für einen Internetgriff.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CInternetFile::m_hFile](#m_hfile)|Ein Handle für eine Datei.|

## <a name="remarks"></a>Bemerkungen

Stellt eine Basisklasse für die Dateiklassen [CHttpFile](../../mfc/reference/chttpfile-class.md) und [CGopherFile](../../mfc/reference/cgopherfile-class.md) bereit. Sie erstellen `CInternetFile` nie direkt ein Objekt. Erstellen Sie stattdessen ein Objekt einer seiner abgeleiteten Klassen, indem Sie [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) oder [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest)aufrufen. Sie können ein `CInternetFile` Objekt auch erstellen, indem Sie [CFtpConnection::OpenFile](../../mfc/reference/cftpconnection-class.md#openfile)aufrufen.

Die `CInternetFile` `Open`Memberfunktionen `LockRange` `UnlockRange`, `Duplicate` , und `CInternetFile`sind nicht für implementiert. Wenn Sie diese Funktionen `CInternetFile` für ein Objekt aufrufen, erhalten Sie eine [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Weitere Informationen zur `CInternetFile` Funktionsweise mit den anderen MFC-Internetklassen finden Sie im Artikel [Internetprogrammierung mit WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

`CInternetFile`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxinet.h

## <a name="cinternetfileabort"></a><a name="abort"></a>CInternetFile::Abbruch

Schließt die diesem Objekt zugeordnete Datei und macht die Datei zum Lesen oder Schreiben nicht verfügbar.

```
virtual void Abort();
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie die Datei vor dem Zerstören des Objekts nicht geschlossen haben, schließt der Destruktor sie für Sie.

Bei der Behandlung `Abort` von Ausnahmen unterscheidet sich von [Close](#close) auf zwei wichtige Weisen. Erstens löst `Abort` die Funktion keine Ausnahme bei Fehlern aus, da Sie Fehler ignoriert. Zweitens, `Abort` nicht **ASSERT,** wenn die Datei nicht geöffnet wurde oder zuvor geschlossen wurde.

## <a name="cinternetfilecinternetfile"></a><a name="cinternetfile"></a>CInternetFile::CInternetFile

Diese Memberfunktion wird `CInternetFile` aufgerufen, wenn ein Objekt erstellt wird.

```
CInternetFile(
    HINTERNET hFile,
    LPCTSTR pstrFileName,
    CInternetConnection* pConnection,
    BOOL bReadMode);

CInternetFile(
    HINTERNET hFile,
    HINTERNET hSession,
    LPCTSTR pstrFileName,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext,
    BOOL bReadMode);
```

### <a name="parameters"></a>Parameter

*hDatei*<br/>
Ein Handle für eine Internetdatei.

*pstrFileName*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Dateinamen enthält.

*pConnection*<br/>
Ein Zeiger auf ein [CInternetConnection-Objekt.](../../mfc/reference/cinternetconnection-class.md)

*bReadMode*<br/>
Gibt an, ob die Datei schreibgeschützt ist.

*hSession*<br/>
Ein Handle für eine Internetsitzung.

*pstrServer*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen des Servers enthält.

*dwContext*<br/>
Der Kontextbezeichner für das `CInternetFile` Objekt. Weitere Informationen zum Kontextbezeichner finden Sie unter [WinInet-Grundlagen.](../../mfc/wininet-basics.md)

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CInternetFile` nie direkt ein Objekt. Erstellen Sie stattdessen ein Objekt einer seiner abgeleiteten Klassen, indem Sie [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) oder [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest)aufrufen. Sie können ein `CInternetFile` Objekt auch erstellen, indem Sie [CFtpConnection::OpenFile](../../mfc/reference/cftpconnection-class.md#openfile)aufrufen.

## <a name="cinternetfileclose"></a><a name="close"></a>CInternetFile::Schließen

Schließt a `CInternetFile` und gibt alle Ressourcen frei.

```
virtual void Close();
```

### <a name="remarks"></a>Bemerkungen

Wenn die Datei zum Schreiben geöffnet wurde, gibt es einen impliziten Aufruf von [Flush,](#flush) um sicherzustellen, dass alle gepufferten Daten auf den Host geschrieben werden. Sie sollten `Close` anrufen, wenn Sie mit der Verwendung einer Datei fertig sind.

## <a name="cinternetfileflush"></a><a name="flush"></a>CInternetFile::Flush

Rufen Sie diese Memberfunktion auf, um den Inhalt des Schreibpuffers zu leeren.

```
virtual void Flush();
```

### <a name="remarks"></a>Bemerkungen

Verwenden `Flush` Sie diese Möglichkeit, um sicherzustellen, dass alle Daten im Speicher tatsächlich auf den Zielcomputer geschrieben wurden, und um sicherzustellen, dass Ihre Transaktion mit dem Hostcomputer abgeschlossen wurde. `Flush`ist nur `CInternetFile` für Objekte wirksam, die zum Schreiben geöffnet wurden.

## <a name="cinternetfilegetlength"></a><a name="getlength"></a>CInternetFile::GetLength

Gibt die Größe der Datei zurück.

```
virtual ULONGLONG GetLength() const;
```

## <a name="cinternetfilem_hfile"></a><a name="m_hfile"></a>CInternetFile::m_hFile

Ein Handle für die Datei, die diesem Objekt zugeordnet ist.

```
HINTERNET m_hFile;
```

## <a name="cinternetfileoperator-hinternet"></a><a name="operator_hinternet"></a>CInternetFile::operator HINTERNET

Verwenden Sie diesen Operator, um das Windows-Handle für die aktuelle Internetsitzung abzubekommen.

```
operator HINTERNET() const;
```

## <a name="cinternetfileread"></a><a name="read"></a>CInternetFile::Lesen

Rufen Sie diese Memberfunktion auf, um in den angegebenen Speicher einzulesen, beginnend bei *lpvBuf*, der angegebenen Anzahl von Bytes, *nCount*.

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parameter

*lpBuf*<br/>
Ein Zeiger auf eine Speicheradresse, auf der Dateidaten gelesen werden.

*nCount*<br/>
Die Anzahl der zu schreibenden Bytes.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der in den Puffer übertrageben Bytes. Der Rückgabewert kann kleiner als *nCount* sein, wenn das Ende der Datei erreicht wurde.

### <a name="remarks"></a>Bemerkungen

Die Funktion gibt die Anzahl der tatsächlich gelesenen Bytes zurück – eine Zahl, die kleiner als *nCount* sein kann, wenn die Datei endet. Wenn beim Lesen der Datei ein Fehler auftritt, löst die Funktion ein [CInternetException-Objekt](../../mfc/reference/cinternetexception-class.md) aus, das den Fehler beschreibt. Beachten Sie, dass der Lesevorgang nach dem Ende der Datei nicht als Fehler angesehen und keine Ausnahme ausgelöst wird.

Um sicherzustellen, dass alle Daten abgerufen werden, muss eine Anwendung die `CInternetFile::Read` Methode fortsetzen, bis die Methode Null zurückgibt.

## <a name="cinternetfilereadstring"></a><a name="readstring"></a>CInternetFile::ReadString

Rufen Sie diese Memberfunktion auf, um einen Datenstrom zu lesen, bis ein Zeilenumzufolge gefunden wird.

```
virtual BOOL ReadString(CString& rString);

virtual LPTSTR ReadString(
    LPTSTR pstr,
    UINT nMax);
```

### <a name="parameters"></a>Parameter

*Pstr*<br/>
Ein Zeiger auf eine Zeichenfolge, die die gelesene Zeile empfängt.

*nMax*<br/>
Die maximale Anzahl der zu lesenden Zeichen.

*rString*<br/>
Ein Verweis auf das [CString-Objekt,](../../atl-mfc-shared/reference/cstringt-class.md) das die Lesezeile empfängt.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Puffer, der einfache Daten enthält, die aus dem [CInternetFile-Objekt](../../mfc/reference/cinternetfile-class.md) abgerufen wurden. Unabhängig vom Datentyp des Puffers, der an diese Methode übergeben wird, führt er keine Manipulationen an den Daten durch (z. B. Konvertierung in Unicode), daher müssen Sie die zurückgegebenen Daten der erwarteten Struktur zuordnen, als ob der **void-Typ** <strong>\*</strong> zurückgegeben würde.

NULL, wenn das Ende der Datei erreicht wurde, ohne Daten zu lesen; oder, wenn boolesch, FALSE, wenn das Ende der Datei erreicht wurde, ohne Daten zu lesen.

### <a name="remarks"></a>Bemerkungen

Die Funktion platziert die resultierende Zeile in den Speicher, auf den der *parameter pstr* verweist. Das Lesen von Zeichen wird beendet, wenn die maximale Anzahl von Zeichen erreicht wird, die von *nMax*angegeben wird. Der Puffer empfängt immer ein beendendes Nullzeichen.

Wenn Sie `ReadString` [SetReadBufferSize](#setreadbuffersize)aufrufen, erhalten Sie einen Puffer von 4096 Bytes.

## <a name="cinternetfileseek"></a><a name="seek"></a>CInternetFile::Suchen

Rufen Sie diese Memberfunktion auf, um den Zeiger in einer zuvor geöffneten Datei neu zu positionieren.

```
virtual ULONGLONG Seek(
    LONGLONG lOffset,
    UINT nFrom);
```

### <a name="parameters"></a>Parameter

*lOffset*<br/>
Versatz in Bytes, um den Lese-/Schreibzeiger in der Datei zu verschieben.

*nVon*<br/>
Relative Referenz für den Offset. Dies muss einer der folgenden Werte sein:

- `CFile::begin`Verschieben Sie den Dateizeiger *lOff* Bytes vom Anfang der Datei nach vorne.

- `CFile::current`Verschieben Sie den Dateizeiger *lOff* bytes von der aktuellen Position in der Datei.

- `CFile::end`Verschieben Sie den Dateizeiger *lOff* bytes vom Ende der Datei. *lOff* muss negativ sein, um in die vorhandene Datei zu suchen. positive Werte werden über das Ende der Datei hinaus gesucht.

### <a name="return-value"></a>Rückgabewert

Das neue Byte wird vom Anfang der Datei versetzt, wenn die angeforderte Position rechtmäßig ist; Andernfalls ist der Wert nicht definiert, und ein [CInternetException-Objekt](../../mfc/reference/cinternetexception-class.md) wird ausgelöst.

### <a name="remarks"></a>Bemerkungen

Die `Seek` Funktion ermöglicht den zufälligen Zugriff auf den Inhalt einer Datei, indem der Zeiger einen bestimmten Betrag, absolut oder relativ, bewegt. Während der Suche werden keine Daten gelesen.

Zu diesem Zeitpunkt wird ein Aufruf dieser Memberfunktion `CHttpFile` nur für Daten unterstützt, die Objekten zugeordnet sind. Es wird nicht für FTP- oder Gopher-Anforderungen unterstützt. Wenn Sie `Seek` einen dieser nicht unterstützten Dienste aufrufen, werden Sie an den Win32-Fehlercode ERROR_INTERNET_INVALID_OPERATION zurückgegeben.

Wenn eine Datei geöffnet wird, befindet sich der Dateizeiger im Offset 0, dem Anfang der Datei.

> [!NOTE]
> Die `Seek` Verwendung kann zu einem impliziten Aufruf von [Flush](#flush)führen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für die Basisklassenimplementierung ( [CFile::Seek](../../mfc/reference/cfile-class.md#seek)).

## <a name="cinternetfilesetreadbuffersize"></a><a name="setreadbuffersize"></a>CInternetFile::SetReadBufferSize

Rufen Sie diese Memberfunktion auf, um die `CInternetFile`Größe des temporären Lesepuffers festzulegen, der von einem -derived-Objekt verwendet wird.

```
BOOL SetReadBufferSize(UINT nReadSize);
```

### <a name="parameters"></a>Parameter

*nReadSize*<br/>
Die gewünschte Puffergröße in Bytes.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

### <a name="remarks"></a>Bemerkungen

Die zugrunde liegenden WinInet-APIs führen keine Pufferung durch, daher wählen Sie eine Puffergröße aus, die es Ihrer Anwendung ermöglicht, Daten effizient zu lesen, unabhängig von der Menge der zu lesenden Daten. Wenn jeder Aufruf von [Read](#read) normalerweise eine große Menge an Daten umfasst (z. B. vier oder mehr Kilobyte), sollten Sie keinen Puffer benötigen. Wenn Sie jedoch `Read` kleine Datenblöcke aufrufen oder [ReadString](#readstring) verwenden, um einzelne Zeilen gleichzeitig zu lesen, verbessert ein Lesepuffer die Anwendungsleistung.

Standardmäßig bietet `CInternetFile` ein Objekt keine Pufferung zum Lesen. Wenn Sie diese Memberfunktion aufrufen, müssen Sie sicherstellen, dass die Datei für den Lesezugriff geöffnet wurde.

Sie können die Puffergröße jederzeit erhöhen, aber das Verkleinern des Puffers hat keine Auswirkungen. Wenn Sie [ReadString](#readstring) aufrufen, ohne vorher aufgerufen `SetReadBufferSize`zu haben, erhalten Sie einen Puffer von 4096 Bytes.

## <a name="cinternetfilesetwritebuffersize"></a><a name="setwritebuffersize"></a>CInternetFile::SetWriteBufferSize

Rufen Sie diese Memberfunktion auf, um die `CInternetFile`Größe des temporären Schreibpuffers festzulegen, der von einem -derived-Objekt verwendet wird.

```
BOOL SetWriteBufferSize(UINT nWriteSize);
```

### <a name="parameters"></a>Parameter

*nWriteSize*<br/>
Die Größe des Puffers in Byte.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

### <a name="remarks"></a>Bemerkungen

Die zugrunde liegenden WinInet-APIs führen keine Pufferung durch, daher wählen Sie eine Puffergröße aus, mit der Ihre Anwendung Daten unabhängig von der zu schreibenden Datenmenge effizient schreiben kann. Wenn jeder Aufruf von [Write](#write) normalerweise eine große Datenmenge umfasst (z. B. vier oder mehr Kilobyte gleichzeitig), sollten Sie keinen Puffer benötigen. Wenn Sie jedoch [Write](#write) aufrufen, um kleine Datenblöcke zu schreiben, verbessert ein Schreibpuffer die Leistung Ihrer Anwendung.

Standardmäßig bietet `CInternetFile` ein Objekt keine Pufferung zum Schreiben. Wenn Sie diese Memberfunktion aufrufen, müssen Sie sicherstellen, dass die Datei für den Schreibzugriff geöffnet wurde. Sie können die Größe des Schreibpuffers jederzeit ändern, aber dies bewirkt einen impliziten Aufruf von [Flush](#flush).

## <a name="cinternetfilewrite"></a><a name="write"></a>CInternetFile::Schreiben

Rufen Sie diese Memberfunktion auf, um in den angegebenen *Speicher, lpvBuf*, die angegebene Anzahl von Bytes, *nCount*, zu schreiben.

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parameter

*lpBuf*<br/>
Ein Zeiger auf das erste Byte, das geschrieben werden soll.

*nCount*<br/>
Gibt die Anzahl der zu schreibenden Bytes an.

### <a name="remarks"></a>Bemerkungen

Wenn beim Schreiben der Daten ein Fehler auftritt, löst die Funktion ein [CInternetException-Objekt](../../mfc/reference/cinternetexception-class.md) aus, das den Fehler beschreibt.

## <a name="cinternetfilewritestring"></a><a name="writestring"></a>CInternetFile::WriteString

Diese Funktion schreibt eine null-terminierte Zeichenfolge in die zugeordnete Datei.

```
virtual void WriteString(LPCTSTR pstr);
```

### <a name="parameters"></a>Parameter

*Pstr*<br/>
Ein Zeiger auf eine Zeichenfolge, die den zu schreibenden Inhalt enthält.

### <a name="remarks"></a>Bemerkungen

Wenn beim Schreiben der Daten ein Fehler auftritt, löst die Funktion ein [CInternetException-Objekt](../../mfc/reference/cinternetexception-class.md) aus, das den Fehler beschreibt.

## <a name="see-also"></a>Siehe auch

[CStdioFile-Klasse](../../mfc/reference/cstdiofile-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection-Klasse](../../mfc/reference/cinternetconnection-class.md)
