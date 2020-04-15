---
title: CAtlFile-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAtlFile
- ATLFILE/ATL::CAtlFile
- ATLFILE/ATL::CAtlFile::CAtlFile
- ATLFILE/ATL::CAtlFile::Create
- ATLFILE/ATL::CAtlFile::Flush
- ATLFILE/ATL::CAtlFile::GetOverlappedResult
- ATLFILE/ATL::CAtlFile::GetPosition
- ATLFILE/ATL::CAtlFile::GetSize
- ATLFILE/ATL::CAtlFile::LockRange
- ATLFILE/ATL::CAtlFile::Read
- ATLFILE/ATL::CAtlFile::Seek
- ATLFILE/ATL::CAtlFile::SetSize
- ATLFILE/ATL::CAtlFile::UnlockRange
- ATLFILE/ATL::CAtlFile::Write
- ATLFILE/ATL::CAtlFile::m_pTM
helpviewer_keywords:
- CAtlFile class
ms.assetid: 93ed160b-af2a-448c-9cbe-e5fa46c199bb
ms.openlocfilehash: 39f323874ccde5178722235b9beb34c2572407a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318967"
---
# <a name="catlfile-class"></a>CAtlFile-Klasse

Diese Klasse stellt einen dünnen Wrapper um die Windows-Dateiverarbeitungs-API bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CAtlFile : public CHandle
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlFile::CAtlDatei](#catlfile)|Der Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlFile::Erstellen](#create)|Rufen Sie diese Methode auf, um eine Datei zu erstellen oder zu öffnen.|
|[CAtlFile::Flush](#flush)|Rufen Sie diese Methode auf, um die Puffer für die Datei zu löschen und dazu zu führen, dass alle gepufferten Daten in die Datei geschrieben werden.|
|[CAtlFile::GetOverlappedResult](#getoverlappedresult)|Rufen Sie diese Methode auf, um die Ergebnisse eines überlappenden Vorgangs für die Datei abzurufen.|
|[CAtlFile::GetPosition](#getposition)|Rufen Sie diese Methode auf, um die aktuelle Dateizeigerposition aus der Datei abzurufen.|
|[CAtlFile::GetSize](#getsize)|Rufen Sie diese Methode auf, um die Größe in Bytes der Datei abzurufen.|
|[CAtlFile::LockRange](#lockrange)|Rufen Sie diese Methode auf, um einen Bereich in der Datei zu sperren, um zu verhindern, dass andere Prozesse darauf zugreifen.|
|[CAtlFile::Lesen](#read)|Rufen Sie diese Methode auf, um Daten aus einer Datei zu lesen, die an der vom Dateizeiger angegebenen Position beginnt.|
|[CAtlFile::Suchen](#seek)|Rufen Sie diese Methode auf, um den Dateizeiger der Datei zu verschieben.|
|[CAtlFile::SetSize](#setsize)|Rufen Sie diese Methode auf, um die Größe der Datei festzulegen.|
|[CAtlFile::UnlockRange](#unlockrange)|Rufen Sie diese Methode auf, um einen Bereich der Datei zu entsperren.|
|[CAtlFile::Schreiben](#write)|Rufen Sie diese Methode auf, um Daten in die Datei zu schreiben, die an der vom Dateizeiger angegebenen Position beginnen.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlFile::m_pTM](#m_ptm)|Zeiger auf `CAtlTransactionManager` Objekt|

## <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Klasse, wenn die Anforderungen an die Dateiverarbeitung relativ einfach sind, aber mehr Abstraktion als die Windows-API bietet, ohne MFC-Abhängigkeiten einzubeziehen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CHandle](../../atl/reference/chandle-class.md)

`CAtlFile`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlfile.h

## <a name="catlfilecatlfile"></a><a name="catlfile"></a>CAtlFile::CAtlDatei

Der Konstruktor.

```
CAtlFile() throw();
CAtlFile(CAtlTransactionManager* pTM = NULL) throw();
CAtlFile(CAtlFile& file) throw();
explicit CAtlFile(HANDLE hFile) throw();
```

### <a name="parameters"></a>Parameter

*Datei*<br/>
Das Dateiobjekt.

*hDatei*<br/>
Das Dateihandle.

*Ptm*<br/>
Zeiger auf CAtlTransactionManager-Objekt

### <a name="remarks"></a>Bemerkungen

Der Kopierkonstruktor überträgt den Besitz `CAtlFile` des Dateihandles vom ursprünglichen Objekt auf das neu erstellte Objekt.

## <a name="catlfilecreate"></a><a name="create"></a>CAtlFile::Erstellen

Rufen Sie diese Methode auf, um eine Datei zu erstellen oder zu öffnen.

```
HRESULT Create(
    LPCTSTR szFilename,
    DWORD dwDesiredAccess,
    DWORD dwShareMode,
    DWORD dwCreationDisposition,
    DWORD dwFlagsAndAttributes = FILE_ATTRIBUTE_NORMAL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    HANDLE hTemplateFile = NULL) throw();
```

### <a name="parameters"></a>Parameter

*szDateiname*<br/>
Der Name der Datei.

*dwDesiredAccess*<br/>
Der gewünschte Zugriff. Siehe *dwDesiredAccess* in [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew) im Windows SDK.

*dwShareMode*<br/>
Der Freigabemodus. Siehe *dwShareMode* in `CreateFile`.

*dwCreationDisposition*<br/>
Die Schöpfungsdisposition. Siehe *dwCreationDisposition* in `CreateFile`.

*dwFlagsAndAttributes*<br/>
Die Flags und Attribute. Siehe *dwFlagsAndAttributes* in `CreateFile`.

*lpsa*<br/>
Die Sicherheitsattribute. Siehe *lpSecurityAttributes* in `CreateFile`.

*hTemplateFile*<br/>
Die Vorlagendatei. Siehe *hTemplateFile* in `CreateFile`.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Ruft [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew) auf, um die Datei zu erstellen oder zu öffnen.

## <a name="catlfileflush"></a><a name="flush"></a>CAtlFile::Flush

Rufen Sie diese Methode auf, um die Puffer für die Datei zu löschen und dazu zu führen, dass alle gepufferten Daten in die Datei geschrieben werden.

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Ruft [FlushFileBuffers](/windows/win32/api/fileapi/nf-fileapi-flushfilebuffers) auf, um gepufferte Daten in die Datei zu löschen.

## <a name="catlfilegetoverlappedresult"></a><a name="getoverlappedresult"></a>CAtlFile::GetOverlappedResult

Rufen Sie diese Methode auf, um die Ergebnisse eines überlappenden Vorgangs für die Datei abzurufen.

```
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```

### <a name="parameters"></a>Parameter

*pOverlapped*<br/>
Die überlappende Struktur. Siehe *lpOverlapped* in [GetOverlappedResult](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult) im Windows SDK.

*dwBytesTransferred*<br/>
Die übertragenen Bytes. Siehe *lpNumberOfBytesTransferred* in `GetOverlappedResult`.

*bWarten*<br/>
Die Warteoption. Siehe *bWarten* in `GetOverlappedResult`.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Ruft [GetOverlappedResult](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult) auf, um die Ergebnisse eines überlappenden Vorgangs für die Datei abzubekommen.

## <a name="catlfilegetposition"></a><a name="getposition"></a>CAtlFile::GetPosition

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

Ruft [SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) auf, um die aktuelle Dateizeigerposition abzubekommen.

## <a name="catlfilegetsize"></a><a name="getsize"></a>CAtlFile::GetSize

Rufen Sie diese Methode auf, um die Größe in Bytes der Datei abzurufen.

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Parameter

*nLen*<br/>
Die Anzahl der Bytes in der Datei.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Ruft [GetFileSize](/windows/win32/api/fileapi/nf-fileapi-getfilesize) auf, um die Größe in Bytes der Datei abzubekommen.

## <a name="catlfilelockrange"></a><a name="lockrange"></a>CAtlFile::LockRange

Rufen Sie diese Methode auf, um einen Bereich in der Datei zu sperren, um zu verhindern, dass andere Prozesse darauf zugreifen.

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

Ruft [LockFile](/windows/win32/api/fileapi/nf-fileapi-lockfile) auf, um einen Bereich in der Datei zu sperren. Das Sperren von Bytes in einer Datei verhindert den Zugriff auf diese Bytes durch andere Prozesse. Sie können mehr als einen Bereich einer Datei sperren, aber es sind keine überlappenden Bereiche zulässig. Wenn Sie eine Region mit [CAtlFile::UnlockRange](#unlockrange)entsperren, muss der Bytebereich genau dem Bereich entsprechen, der zuvor gesperrt war. `LockRange`führt keine angrenzenden Regionen zusammen; Wenn zwei gesperrte Bereiche nebeneinander liegen, müssen Sie jeden separat entsperren.

## <a name="catlfilem_ptm"></a><a name="m_ptm"></a>CAtlFile::m_pTM

Zeiger auf `CAtlTransactionManager` ein Objekt.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Bemerkungen

## <a name="catlfileread"></a><a name="read"></a>CAtlFile::Lesen

Rufen Sie diese Methode auf, um Daten aus einer Datei zu lesen, die an der vom Dateizeiger angegebenen Position beginnt.

```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();
```

### <a name="parameters"></a>Parameter

*pBuffer*<br/>
Zeiger auf den Puffer, der die aus der Datei gelesenen Daten empfängt.

*nBufSize*<br/>
Die Puffergröße in Byte.

*nBytesRead*<br/>
Die Anzahl der gelesenen Bytes.

*pOverlapped*<br/>
Die überlappende Struktur. Siehe *lpOverlapped* in [ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile) im Windows SDK.

*pfnCompletionRoutine*<br/>
Die Abschlussroutine. Siehe *lpCompletionRoutine* in [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Die ersten drei Formulare rufen [ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile)auf, den letzten [ReadFileEx,](/windows/win32/api/fileapi/nf-fileapi-readfileex) um Daten aus der Datei zu lesen. Verwenden Sie [CAtlFile::Seek,](#seek) um den Dateizeiger zu verschieben.

## <a name="catlfileseek"></a><a name="seek"></a>CAtlFile::Suchen

Rufen Sie diese Methode auf, um den Dateizeiger der Datei zu verschieben.

```
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Parameter

*nOffset*<br/>
Der Offset vom Von *dwFrom*angegebenen Startpunkt.

*dwVon*<br/>
Der Startpunkt (FILE_BEGIN, FILE_CURRENT oder FILE_END).

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Ruft [SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) auf, um den Dateizeiger zu verschieben.

## <a name="catlfilesetsize"></a><a name="setsize"></a>CAtlFile::SetSize

Rufen Sie diese Methode auf, um die Größe der Datei festzulegen.

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Parameter

*nNewLen*<br/>
Die neue Länge der Datei in Bytes.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Ruft [SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) und [SetEndOfFile](/windows/win32/api/fileapi/nf-fileapi-setendoffile) auf, um die Größe der Datei festzulegen. Bei der Rückgabe wird der Dateizeiger am Ende der Datei positioniert.

## <a name="catlfileunlockrange"></a><a name="unlockrange"></a>CAtlFile::UnlockRange

Rufen Sie diese Methode auf, um einen Bereich der Datei zu entsperren.

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

Ruft [UnlockFile](/windows/win32/api/fileapi/nf-fileapi-unlockfile) auf, um einen Bereich der Datei zu entsperren.

## <a name="catlfilewrite"></a><a name="write"></a>CAtlFile::Schreiben

Rufen Sie diese Methode auf, um Daten in die Datei zu schreiben, die an der vom Dateizeiger angegebenen Position beginnen.

```
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();
```

### <a name="parameters"></a>Parameter

*pBuffer*<br/>
Der Puffer, der die Daten enthält, die in die Datei geschrieben werden sollen.

*nBufSize*<br/>
Die Anzahl der Bytes, die aus dem Puffer übertragen werden sollen.

*pOverlapped*<br/>
Die überlappende Struktur. Siehe *lpOverlapped* in [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile) im Windows SDK.

*pfnCompletionRoutine*<br/>
Die Abschlussroutine. Siehe *lpCompletionRoutine* in [WriteFileEx](/windows/win32/api/fileapi/nf-fileapi-writefileex) im Windows SDK.

*pnBytesWritten*<br/>
Die geschriebenen Bytes.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Die ersten drei Formulare rufen [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile)auf, der letzte ruft [WriteFileEx](/windows/win32/api/fileapi/nf-fileapi-writefileex) auf, um Daten in die Datei zu schreiben. Verwenden Sie [CAtlFile::Seek,](#seek) um den Dateizeiger zu verschieben.

## <a name="see-also"></a>Siehe auch

[Marquee-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[CHandle-Klasse](../../atl/reference/chandle-class.md)
