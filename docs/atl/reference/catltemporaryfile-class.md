---
title: Klasse von "Klasse"
ms.date: 11/04/2016
f1_keywords:
- CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::Close
- ATLFILE/ATL::CAtlTemporaryFile::Create
- ATLFILE/ATL::CAtlTemporaryFile::Flush
- ATLFILE/ATL::CAtlTemporaryFile::GetPosition
- ATLFILE/ATL::CAtlTemporaryFile::GetSize
- ATLFILE/ATL::CAtlTemporaryFile::HandsOff
- ATLFILE/ATL::CAtlTemporaryFile::HandsOn
- ATLFILE/ATL::CAtlTemporaryFile::LockRange
- ATLFILE/ATL::CAtlTemporaryFile::Read
- ATLFILE/ATL::CAtlTemporaryFile::Seek
- ATLFILE/ATL::CAtlTemporaryFile::SetSize
- ATLFILE/ATL::CAtlTemporaryFile::TempFileName
- ATLFILE/ATL::CAtlTemporaryFile::UnlockRange
- ATLFILE/ATL::CAtlTemporaryFile::Write
helpviewer_keywords:
- CAtlTemporaryFile class
ms.assetid: 05f0f2a5-94f6-4594-8dae-b114292ff5f9
ms.openlocfilehash: f3d0be66bf0b5a6c07a72c8ae6cc9c90e176728f
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167889"
---
# <a name="catltemporaryfile-class"></a>Klasse von "Klasse"

Diese Klasse stellt Methoden zum Erstellen und Verwenden einer temporären Datei bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
class CAtlTemporaryFile
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|["" "" "".](#catltemporaryfile)|Der Konstruktor.|
|["" "" "".](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|["":](#close)|Mit dieser Methode können Sie eine temporäre Datei schließen und ihre Inhalte entweder löschen oder unter dem angegebenen Dateinamen speichern.|
|["": Create](#create)|Rufen Sie diese Methode auf, um eine temporäre Datei zu erstellen.|
|["":](#flush)|Mit dieser Methode können Sie erzwingen, dass alle im Datei Puffer verbleibenden Daten in die temporäre Datei geschrieben werden.|
|[' ' ' ' ' ' ' ' ' ' ' ' ' '](#getposition)|Mit dieser Methode können Sie die aktuelle Dateizeiger Position abrufen.|
|["" "" ".](#getsize)|Mit dieser Methode können Sie die Größe der temporären Datei in Byte abrufen.|
|["" "".](#handsoff)|Mit dieser Methode wird die Zuordnung der Datei zum- `CAtlTemporaryFile` Objekt aufgehoben.|
|["" "" "" ".](#handson)|Diese Methode wird aufgerufen, um eine vorhandene temporäre Datei zu öffnen und den Zeiger am Ende der Datei zu positionieren.|
|["' ' ' ' ' ' ' ' ': ' '](#lockrange)|Wenn Sie diese Methode aufrufen, wird ein Bereich in der Datei gesperrt, um zu verhindern, dass andere Prozesse darauf zugreifen.|
|["": Lesen](#read)|Mit dieser Methode können Sie Daten aus der temporären Datei beginnend an der durch den Dateizeiger gekennzeichneten Position lesen.|
|["":](#seek)|Mit dieser Methode können Sie den Dateizeiger der temporären Datei verschieben.|
|["" "".](#setsize)|Mit dieser Methode können Sie die Größe der temporären Datei festlegen.|
|["" "" ".](#tempfilename)|Mit dieser Methode wird der Name der temporären Datei zurückgegeben.|
|[' ' ' ' ' ' ' ' ' ' ' ' ' ' '](#unlockrange)|Mit dieser Methode wird ein Bereich der temporären Datei entsperrt.|
|["":](#write)|Ruft diese Methode auf, um Daten in die temporäre Datei zu schreiben, beginnend an der durch den Dateizeiger gekennzeichneten Position.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[""-Operator handle](#operator_handle)|Gibt ein Handle für die temporäre Datei zurück.|

## <a name="remarks"></a>Bemerkungen

`CAtlTemporaryFile`macht es einfach, eine temporäre Datei zu erstellen und zu verwenden. Die Datei wird automatisch benannt, geöffnet, geschlossen und gelöscht. Wenn der Inhalt der Datei nach dem Schließen der Datei erforderlich ist, können Sie in einer neuen Datei mit einem angegebenen Namen gespeichert werden.

## <a name="requirements"></a>Anforderungen

**Header:** atlfile. h

## <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für die [Datei](#catltemporaryfile)"".

## <a name="catltemporaryfilecatltemporaryfile"></a><a name="catltemporaryfile"></a>"" "" "".

Der Konstruktor.

```cpp
CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Bemerkungen

Eine Datei wird erst [geöffnet, wenn](#create)ein Aufrufen von "" für "" "" "" ".

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#73](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]

## <a name="catltemporaryfilecatltemporaryfile"></a><a name="dtor"></a>"" "" "".

Der Destruktor.

```cpp
~CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Bemerkungen

Der Dekonstruktor Ruft die [Datei](#close)"".

## <a name="catltemporaryfileclose"></a><a name="close"></a>"":

Mit dieser Methode können Sie eine temporäre Datei schließen und ihre Inhalte entweder löschen oder unter dem angegebenen Dateinamen speichern.

```cpp
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```

### <a name="parameters"></a>Parameter

*sznewname*<br/>
Der Name der neuen Datei, in der der Inhalt der temporären Datei gespeichert werden soll. Wenn dieses Argument NULL ist, wird der Inhalt der temporären Datei gelöscht.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für die [Datei](#catltemporaryfile)"".

## <a name="catltemporaryfilecreate"></a><a name="create"></a>"": Create

Rufen Sie diese Methode auf, um eine temporäre Datei zu erstellen.

```cpp
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```

### <a name="parameters"></a>Parameter

*pszdir*<br/>
Der Pfad für die temporäre Datei. Wenn dieser Wert NULL ist, wird [GetTempPath](/windows/win32/api/fileapi/nf-fileapi-gettemppathw) aufgerufen, um einen Pfad zuzuweisen.

*dwDesiredAccess*<br/>
Der gewünschte Zugriff. Weitere Informationen finden Sie in der Windows SDK unter *dwDesiredAccess* in der [Datei](/windows/win32/api/fileapi/nf-fileapi-createfilew) "".

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für die [Datei](#catltemporaryfile)"".

## <a name="catltemporaryfileflush"></a><a name="flush"></a>"":

Mit dieser Methode können Sie erzwingen, dass alle im Datei Puffer verbleibenden Daten in die temporäre Datei geschrieben werden.

```cpp
HRESULT Flush() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

Ähnlich wie [bei der](#handsoff)Datei "" von "" mit "", mit dem Unterschied, dass die Datei nicht geschlossen ist.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für die [Datei](#catltemporaryfile)"".

## <a name="catltemporaryfilegetposition"></a><a name="getposition"></a>' ' ' ' ' ' ' ' ' ' ' ' ' '

Mit dieser Methode können Sie die aktuelle Dateizeiger Position abrufen.

```cpp
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>Parameter

*NPOs*<br/>
Die Position in Bytes.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

Um die Position des Dateizeigers zu ändern, verwenden Sie " [chanltemporaryfile:: Seek](#seek)".

## <a name="catltemporaryfilegetsize"></a><a name="getsize"></a>"" "" ".

Mit dieser Methode können Sie die Größe der temporären Datei in Byte abrufen.

```cpp
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Parameter

*nlen*<br/>
Die Anzahl der Bytes in der Datei.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

## <a name="catltemporaryfilehandsoff"></a><a name="handsoff"></a>"" "".

Mit dieser Methode wird die Zuordnung der Datei zum- `CAtlTemporaryFile` Objekt aufgehoben.

```cpp
HRESULT HandsOff() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

`HandsOff`und [die Datei "](#handson) " mit "" ("" "), um die Zuordnung der Datei zum Objekt aufzuheben und bei Bedarf erneut anzufügen. `HandsOff`erzwingt, dass alle im Datei Puffer verbleibenden Daten in die temporäre Datei geschrieben werden, und schließt dann die Datei. Wenn Sie die Datei dauerhaft schließen und löschen möchten, oder wenn Sie den Inhalt der Datei mit einem bestimmten Namen schließen und beibehalten möchten [, verwenden Sie die Datei "](#close)".

## <a name="catltemporaryfilehandson"></a><a name="handson"></a>"" "" "" ".

Diese Methode wird aufgerufen, um eine vorhandene temporäre Datei zu öffnen und den Zeiger am Ende der Datei zu positionieren.

```cpp
HRESULT HandsOn() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

"" Mit "" "", "" und `HandsOn` "" wird verwendet, um die Zuordnung der Datei zum Objekt [aufzuheben und bei](#handsoff) Bedarf erneut anzufügen.

## <a name="catltemporaryfilelockrange"></a><a name="lockrange"></a>"' ' ' ' ' ' ' ' ': ' '

Wenn Sie diese Methode aufrufen, wird ein Bereich in der temporären Datei gesperrt, um zu verhindern, dass andere Prozesse darauf zugreifen.

```cpp
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parameter

*NPOs*<br/>
Die Position in der Datei, an der die Sperre beginnen soll.

*nCount*<br/>
Die Länge des zu sperrenden Byte Bereichs.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

Das Sperren von Bytes in einer Datei verhindert den Zugriff auf diese Bytes durch andere Prozesse. Sie können mehr als einen Bereich einer Dateisperren, aber es sind keine überlappenden Bereiche zulässig. Wenn Sie einen Bereich erfolgreich entsperren möchten [, verwenden Sie](#unlockrange)"" "" "" "" "" "". `LockRange`angrenzende Bereiche werden nicht zusammengeführt. Wenn zwei gesperrte Bereiche nebeneinander liegen, müssen Sie diese separat entsperren.

## <a name="catltemporaryfileoperator-handle"></a><a name="operator_handle"></a>""-Operator handle

Gibt ein Handle für die temporäre Datei zurück.

```cpp
operator HANDLE() throw();
```

## <a name="catltemporaryfileread"></a><a name="read"></a>"": Lesen

Mit dieser Methode können Sie Daten aus der temporären Datei beginnend an der durch den Dateizeiger gekennzeichneten Position lesen.

```cpp
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```

### <a name="parameters"></a>Parameter

*pBuffer*<br/>
Zeiger auf den Puffer, der die aus der Datei gelesenen Daten empfängt.

*nbuf size*<br/>
Die Puffergröße in Byte.

*nbytesread*<br/>
Die Anzahl der gelesenen Bytes.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

Ruft ["](../../atl/reference/catlfile-class.md#read)" "". Um die Position des Dateizeigers zu ändern, nennen Sie " [chanltemporaryfile:: Seek](#seek)".

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für die [Datei](#catltemporaryfile)"".

## <a name="catltemporaryfileseek"></a><a name="seek"></a>"":

Mit dieser Methode können Sie den Dateizeiger der temporären Datei verschieben.

```cpp
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Parameter

*nOffset*<br/>
Der Offset in Bytes vom Startpunkt, der von *dwfrom* angegeben wird.

*dwfrom*<br/>
Der Ausgangspunkt (FILE_BEGIN, FILE_CURRENT oder FILE_END).

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

Ruft ["](../../atl/reference/catlfile-class.md#seek)" "". Rufen Sie zum Abrufen der aktuellen Position des Dateizeigers [die Datei "](#getposition)" mit "".

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für die [Datei](#catltemporaryfile)"".

## <a name="catltemporaryfilesetsize"></a><a name="setsize"></a>"" "".

Mit dieser Methode können Sie die Größe der temporären Datei festlegen.

```cpp
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Parameter

*nnewlen*<br/>
Die neue Länge der Datei in Bytes.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

Ruft ["](../../atl/reference/catlfile-class.md#setsize)" "". Bei der Rückgabe wird der Dateizeiger am Ende der Datei positioniert.

## <a name="catltemporaryfiletempfilename"></a><a name="tempfilename"></a>"" "" ".

Mit dieser Methode wird der Name der temporären Datei zurückgegeben.

```cpp
LPCTSTR TempFileName() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den LPCTSTR zurück, der auf den Dateinamen zeigt.

### <a name="remarks"></a>Bemerkungen

Der Dateiname [wird in der Datei "](#catltemporaryfile) " mit der Funktion " [gettempfile](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamew)Windows SDK" generiert. Die Dateierweiterung ist für die temporäre Datei immer "TFR".

## <a name="catltemporaryfileunlockrange"></a><a name="unlockrange"></a>' ' ' ' ' ' ' ' ' ' ' ' ' ' '

Mit dieser Methode wird ein Bereich der temporären Datei entsperrt.

```cpp
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parameter

*NPOs*<br/>
Die Position in der Datei, an der die Entsperrung beginnen soll.

*nCount*<br/>
Die Länge des zu entsperrenden Byte Bereichs.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

Ruft ["](../../atl/reference/catlfile-class.md#unlockrange)" "".

## <a name="catltemporaryfilewrite"></a><a name="write"></a>"":

Ruft diese Methode auf, um Daten in die temporäre Datei zu schreiben, beginnend an der durch den Dateizeiger gekennzeichneten Position.

```cpp
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```

### <a name="parameters"></a>Parameter

*pBuffer*<br/>
Der Puffer, der die Daten enthält, die in die Datei geschrieben werden sollen.

*nbuf size*<br/>
Die Anzahl der Bytes, die aus dem Puffer übertragen werden sollen.

*pnbyteswritten*<br/>
Die Anzahl der geschriebenen Byte

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

Ruft ["](../../atl/reference/catlfile-class.md#write)" "".

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für die [Datei](#catltemporaryfile)"".

## <a name="see-also"></a>Weitere Informationen:

[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Klasse "-Klasse"](../../atl/reference/catlfile-class.md)
