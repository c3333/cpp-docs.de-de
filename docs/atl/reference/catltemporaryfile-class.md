---
title: CAtlTemporaryFile-Klasse
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
ms.openlocfilehash: 605e4bcbe7208b18d8d1a50507e8e142a93bde5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321305"
---
# <a name="catltemporaryfile-class"></a>CAtlTemporaryFile-Klasse

Diese Klasse stellt Methoden zum Erstellen und Verwenden einer temporären Datei bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CAtlTemporaryFile
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)|Der Konstruktor.|
|[CAtlTemporaryFile::'CAtlTemporaryFile](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlTemporaryFile::Schließen](#close)|Rufen Sie diese Methode auf, um eine temporäre Datei zu schließen und ihren Inhalt zu löschen oder unter dem angegebenen Dateinamen zu speichern.|
|[CAtlTemporaryFile::Erstellen](#create)|Rufen Sie diese Methode auf, um eine temporäre Datei zu erstellen.|
|[CAtlTemporaryFile::Flush](#flush)|Rufen Sie diese Methode auf, um zu erzwingen, dass alle im Dateipuffer verbleibenden Daten in die temporäre Datei geschrieben werden.|
|[CAtlTemporaryFile::GetPosition](#getposition)|Rufen Sie diese Methode auf, um die aktuelle Dateizeigerposition abzurufen.|
|[CAtlTemporaryFile::GetSize](#getsize)|Rufen Sie diese Methode auf, um die Größe in Bytes der temporären Datei abzurufen.|
|[CAtlTemporaryFile::HandsOff](#handsoff)|Rufen Sie diese Methode auf, `CAtlTemporaryFile` um die Zuordnung der Datei vom Objekt zu trennen.|
|[CAtlTemporaryFile::HandsOn](#handson)|Rufen Sie diese Methode auf, um eine vorhandene temporäre Datei zu öffnen und den Zeiger am Ende der Datei zu positionieren.|
|[CAtlTemporaryFile::LockRange](#lockrange)|Rufen Sie diese Methode auf, um einen Bereich in der Datei zu sperren, um zu verhindern, dass andere Prozesse darauf zugreifen.|
|[CAtlTemporaryFile::Lesen](#read)|Rufen Sie diese Methode auf, um Daten aus der temporären Datei zu lesen, die an der vom Dateizeiger angegebenen Position beginnen.|
|[CAtlTemporaryFile::Suchen](#seek)|Rufen Sie diese Methode auf, um den Dateizeiger der temporären Datei zu verschieben.|
|[CAtlTemporaryFile::SetSize](#setsize)|Rufen Sie diese Methode auf, um die Größe der temporären Datei festzulegen.|
|[CAtlTemporaryFile::TempFileName](#tempfilename)|Rufen Sie diese Methode auf, um den Namen der temporären Datei zurückzugeben.|
|[CAtlTemporaryFile::UnlockRange](#unlockrange)|Rufen Sie diese Methode auf, um einen Bereich der temporären Datei freizuschalten.|
|[CAtlTemporaryFile::Schreiben](#write)|Rufen Sie diese Methode auf, um Daten in die temporäre Datei zu schreiben, beginnend an der Position, die vom Dateizeiger angegeben wird.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlTemporaryFile::operator HANDLE](#operator_handle)|Gibt ein Handle an die temporäre Datei zurück.|

## <a name="remarks"></a>Bemerkungen

`CAtlTemporaryFile`erleichtert das Erstellen und Verwenden einer temporären Datei. Die Datei wird automatisch benannt, geöffnet, geschlossen und gelöscht. Wenn der Dateiinhalt nach dem Schließen der Datei erforderlich ist, können sie in einer neuen Datei mit einem angegebenen Namen gespeichert werden.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlfile.h

## <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilecatltemporaryfile"></a><a name="catltemporaryfile"></a>CAtlTemporaryFile::CAtlTemporaryFile

Der Konstruktor.

```
CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Bemerkungen

Eine Datei wird erst geöffnet, wenn [CAtlTemporaryFile::Create](#create)aufgerufen wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#73](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]

## <a name="catltemporaryfilecatltemporaryfile"></a><a name="dtor"></a>CAtlTemporaryFile::'CAtlTemporaryFile

Der Destruktor.

```
~CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Bemerkungen

Der Destruktor ruft [CAtlTemporaryFile::Close](#close)auf.

## <a name="catltemporaryfileclose"></a><a name="close"></a>CAtlTemporaryFile::Schließen

Rufen Sie diese Methode auf, um eine temporäre Datei zu schließen und ihren Inhalt zu löschen oder unter dem angegebenen Dateinamen zu speichern.

```
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```

### <a name="parameters"></a>Parameter

*szNewName*<br/>
Der Name für die neue Datei, in der der Inhalt der temporären Datei gespeichert werden soll. Wenn dieses Argument NULL ist, wird der Inhalt der temporären Datei gelöscht.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilecreate"></a><a name="create"></a>CAtlTemporaryFile::Erstellen

Rufen Sie diese Methode auf, um eine temporäre Datei zu erstellen.

```
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```

### <a name="parameters"></a>Parameter

*pszDir*<br/>
Der Pfad für die temporäre Datei. Wenn dies NULL ist, wird [GetTempPath](/windows/win32/api/fileapi/nf-fileapi-gettemppathw) aufgerufen, um einen Pfad zuzuweisen.

*dwDesiredAccess*<br/>
Der gewünschte Zugriff. Siehe *dwDesiredAccess* in [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfileflush"></a><a name="flush"></a>CAtlTemporaryFile::Flush

Rufen Sie diese Methode auf, um zu erzwingen, dass alle im Dateipuffer verbleibenden Daten in die temporäre Datei geschrieben werden.

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Ähnlich wie [CAtlTemporaryFile::HandsOff](#handsoff), außer dass die Datei nicht geschlossen ist.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilegetposition"></a><a name="getposition"></a>CAtlTemporaryFile::GetPosition

Rufen Sie diese Methode auf, um die aktuelle Dateizeigerposition abzurufen.

```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>Parameter

*Npos*<br/>
Die Position in Bytes.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Um die Dateizeigerposition zu ändern, verwenden Sie [CAtlTemporaryFile::Seek](#seek).

## <a name="catltemporaryfilegetsize"></a><a name="getsize"></a>CAtlTemporaryFile::GetSize

Rufen Sie diese Methode auf, um die Größe in Bytes der temporären Datei abzurufen.

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Parameter

*nLen*<br/>
Die Anzahl der Bytes in der Datei.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="catltemporaryfilehandsoff"></a><a name="handsoff"></a>CAtlTemporaryFile::HandsOff

Rufen Sie diese Methode auf, `CAtlTemporaryFile` um die Zuordnung der Datei vom Objekt zu trennen.

```
HRESULT HandsOff() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

`HandsOff`und [CAtlTemporaryFile::HandsOn](#handson) werden verwendet, um die Zuordnung der Datei vom Objekt zu trennen und bei Bedarf erneut anzufügen. `HandsOff`erzwingt, dass alle im Dateipuffer verbleibenden Daten in die temporäre Datei geschrieben werden, und schließt dann die Datei. Wenn Sie die Datei dauerhaft schließen und löschen möchten oder wenn Sie den Inhalt der Datei mit einem bestimmten Namen schließen und beibehalten möchten, verwenden Sie [CAtlTemporaryFile::Close](#close).

## <a name="catltemporaryfilehandson"></a><a name="handson"></a>CAtlTemporaryFile::HandsOn

Rufen Sie diese Methode auf, um eine vorhandene temporäre Datei zu öffnen und den Zeiger am Ende der Datei zu positionieren.

```
HRESULT HandsOn() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

[CAtlTemporaryFile::HandsOff](#handsoff) `HandsOn` und werden verwendet, um die Zuordnung der Datei vom Objekt zu trennen und bei Bedarf erneut anzufügen.

## <a name="catltemporaryfilelockrange"></a><a name="lockrange"></a>CAtlTemporaryFile::LockRange

Rufen Sie diese Methode auf, um einen Bereich in der temporären Datei zu sperren, um zu verhindern, dass andere Prozesse darauf zugreifen.

```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parameter

*Npos*<br/>
Die Position in der Datei, an der die Sperre beginnen soll.

*nCount*<br/>
Die Länge des zu verriegelnden Bytebereichs.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Das Sperren von Bytes in einer Datei verhindert den Zugriff auf diese Bytes durch andere Prozesse. Sie können mehr als einen Bereich einer Datei sperren, aber es sind keine überlappenden Bereiche zulässig. Um eine Region erfolgreich zu entsperren, verwenden Sie [CAtlTemporaryFile::UnlockRange](#unlockrange), um sicherzustellen, dass der Bytebereich genau dem Bereich entspricht, der zuvor gesperrt war. `LockRange`führt keine angrenzenden Regionen zusammen; Wenn zwei gesperrte Bereiche nebeneinander liegen, müssen Sie jeden separat entsperren.

## <a name="catltemporaryfileoperator-handle"></a><a name="operator_handle"></a>CAtlTemporaryFile::operator HANDLE

Gibt ein Handle an die temporäre Datei zurück.

```
operator HANDLE() throw();
```

## <a name="catltemporaryfileread"></a><a name="read"></a>CAtlTemporaryFile::Lesen

Rufen Sie diese Methode auf, um Daten aus der temporären Datei zu lesen, die an der vom Dateizeiger angegebenen Position beginnen.

```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```

### <a name="parameters"></a>Parameter

*pBuffer*<br/>
Zeiger auf den Puffer, der die aus der Datei gelesenen Daten empfängt.

*nBufSize*<br/>
Die Puffergröße in Byte.

*nBytesRead*<br/>
Die Anzahl der gelesenen Bytes.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Ruft [CAtlFile::Read](../../atl/reference/catlfile-class.md#read)auf. Um die Position des Dateizeigers zu ändern, rufen Sie [CAtlTemporaryFile::Seek](#seek)auf.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfileseek"></a><a name="seek"></a>CAtlTemporaryFile::Suchen

Rufen Sie diese Methode auf, um den Dateizeiger der temporären Datei zu verschieben.

```
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Parameter

*nOffset*<br/>
Der Offset in Bytes vom von *dwFrom* angegebenen Startpunkt.

*dwVon*<br/>
Der Startpunkt (FILE_BEGIN, FILE_CURRENT oder FILE_END).

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Ruft [CAtlFile::Seek](../../atl/reference/catlfile-class.md#seek)auf. Um die aktuelle Dateizeigerposition zu erhalten, rufen Sie [CAtlTemporaryFile::GetPosition](#getposition)auf.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilesetsize"></a><a name="setsize"></a>CAtlTemporaryFile::SetSize

Rufen Sie diese Methode auf, um die Größe der temporären Datei festzulegen.

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Parameter

*nNewLen*<br/>
Die neue Länge der Datei in Bytes.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Ruft [CAtlFile::SetSize](../../atl/reference/catlfile-class.md#setsize)auf. Bei der Rückgabe wird der Dateizeiger am Ende der Datei positioniert.

## <a name="catltemporaryfiletempfilename"></a><a name="tempfilename"></a>CAtlTemporaryFile::TempFileName

Rufen Sie diese Methode auf, um den Namen der temporären Datei zurückzugeben.

```
LPCTSTR TempFileName() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den LPCTSTR zurück, der auf den Dateinamen verweist.

### <a name="remarks"></a>Bemerkungen

Der Dateiname wird in [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile) mit einem Aufruf der [GetTempFile](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamew)Windows SDK-Funktion generiert. Die Dateierweiterung ist immer "TFR" für die temporäre Datei.

## <a name="catltemporaryfileunlockrange"></a><a name="unlockrange"></a>CAtlTemporaryFile::UnlockRange

Rufen Sie diese Methode auf, um einen Bereich der temporären Datei freizuschalten.

```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parameter

*Npos*<br/>
Die Position in der Datei, an der die Entsperrung beginnen soll.

*nCount*<br/>
Die Länge des freizuschaltenden Bytebereichs.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Ruft [CAtlFile::UnlockRange](../../atl/reference/catlfile-class.md#unlockrange)auf.

## <a name="catltemporaryfilewrite"></a><a name="write"></a>CAtlTemporaryFile::Schreiben

Rufen Sie diese Methode auf, um Daten in die temporäre Datei zu schreiben, beginnend an der Position, die vom Dateizeiger angegeben wird.

```
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```

### <a name="parameters"></a>Parameter

*pBuffer*<br/>
Der Puffer, der die Daten enthält, die in die Datei geschrieben werden sollen.

*nBufSize*<br/>
Die Anzahl der Bytes, die aus dem Puffer übertragen werden sollen.

*pnBytesWritten*<br/>
Die Anzahl der geschriebenen Byte

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Ruft [CAtlFile::Write](../../atl/reference/catlfile-class.md#write)auf.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[CAtlFile-Klasse](../../atl/reference/catlfile-class.md)
