---
title: CMemFile-Klasse
description: Beschreibt die Funktionen, die in der CMemFile-Klasse verfügbar sind und die Ihnen die Arbeit mit Speicherdateien ermöglichen.
ms.date: 07/23/2020
f1_keywords:
- CMemFile
- AFX/CMemFile
- AFX/CMemFile::CMemFile
- AFX/CMemFile::Attach
- AFX/CMemFile::Detach
- AFX/CMemFile::Alloc
- AFX/CMemFile::Free
- AFX/CmemFile::GetBufferPtr
- AFX/CMemFile::GrowFile"
- AFX/CMemFile::Memcpy
- AFX/CMemFile::Realloc
helpviewer_keywords:
- CMemFile [MFC], CMemFile
- CMemFile [MFC], Attach
- CMemFile [MFC], Detach
- CMemFile [MFC], Alloc
- CMemFile [MFC], Free
- CMemFile [MFC], GetBufferPtr
- CMemFile [MFC], GrowFile
- CMemFile [MFC], Memcpy
- CMemFile [MFC], Realloc
ms.assetid: 20e86515-e465-4f73-b2ea-e49789d63165
ms.openlocfilehash: edd1d8b8d3979427602bdb61fc7647aec15d58b5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222939"
---
# <a name="cmemfile-class"></a>CMemFile-Klasse

Die von [CFile](../../mfc/reference/cfile-class.md)abgeleitete Klasse, die Arbeitsspeicher Dateien unterstützt.

## <a name="syntax"></a>Syntax

```
class CMemFile : public CFile
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CMemFile:: CMemFile](#cmemfile)|Erstellt ein Speicherdatei Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[CMemFile:: Attach](#attach)|Fügt einen Speicherblock an `CMemFile` .|
|[CMemFile::D Etach](#detach)|Trennt den Speicherblock von `CMemFile` und gibt einen Zeiger auf den Speicherblock getrennt zurück.|
|[CMemFile:: getbufferptr](#getbufferptr)|Hiermit wird der Arbeitsspeicher Puffer, der eine Speicherdatei sichert, in den Arbeitsspeicher Puffer geschrieben|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CMemFile:: Zuweisung](#alloc)|Überschreiben, um das Verhalten der Speicher Belegung zu ändern.|
|[CMemFile:: Free](#free)|Überschreiben Sie, um das Verhalten der Speicher Belegung zu ändern|
|[CMemFile:: growfile](#growfile)|Überschreiben, um das Verhalten beim Vergrößern einer Datei zu ändern.|
|[CMemFile:: memcpy](#memcpy)|Überschreiben, um das Verhalten beim Kopieren von Daten beim Lesen und Schreiben von Dateien zu ändern|
|[CMemFile:: rezuweisung](#realloc)|Überschreiben, um das Verhalten der Speicher Neuzuordnung zu ändern|

## <a name="remarks"></a>Bemerkungen

Diese Speicherdateien Verhalten sich wie Datenträger Dateien, es sei denn, die Datei wird im Arbeitsspeicher gespeichert und nicht auf dem Datenträger Eine Speicherdatei eignet sich für folgende Aktionen:

- schneller temporärer Speicher
- Übertragen von Rohdaten Bytes zwischen unabhängigen Prozessen
- übertragen serialisierter Objekte zwischen unabhängigen Prozessen

`CMemFile`-Objekte können automatisch Ihren eigenen Arbeitsspeicher zuordnen. Sie können auch einen eigenen Speicherblock an das Objekt anfügen, `CMemFile` indem Sie [Anfügen](#attach)aufrufen. In beiden Fällen wird der Arbeitsspeicher für die Vergrößerung der Speicherdatei automatisch in `nGrowBytes` Schritten, wenn `nGrowBytes` nicht 0 (null) ist.

Der Speicherblock wird bei der Zerstörung des Objekts automatisch gelöscht `CMemFile` , wenn der Arbeitsspeicher ursprünglich durch das Objekt reserviert wurde `CMemFile` . andernfalls sind Sie dafür verantwortlich, die Zuordnung des Arbeitsspeichers aufzuheben, den Sie an das Objekt angefügt haben.

Sie können über den angegebenen Zeiger auf den Speicherblock zugreifen, wenn Sie ihn `CMemFile` durch Aufrufen von [trennen](#detach)vom Objekt trennen.

Die häufigste Verwendung von `CMemFile` ist die Erstellung eines `CMemFile` -Objekts und dessen Verwendung durch Aufrufen von [CFile](../../mfc/reference/cfile-class.md) -Element Funktionen. Beim Erstellen eines wird `CMemFile` es automatisch geöffnet: Sie können [CFile:: Open](../../mfc/reference/cfile-class.md#open)nicht aufzurufen, das nur für Datenträger Dateien verwendet wird. Da `CMemFile` keine Datenträger Datei verwendet, wird der Datenmember `CFile::m_hFile` nicht verwendet.

Die `CFile` Member-Funktionen " [Duplicate](../../mfc/reference/cfile-class.md#duplicate)", " [lockrange](../../mfc/reference/cfile-class.md#lockrange)" und " [unlockrange](../../mfc/reference/cfile-class.md#unlockrange) " sind für nicht implementiert `CMemFile` . Wenn Sie diese Funktionen für ein- `CMemFile` Objekt aufzurufen, erhalten Sie eine [cnotsupportedexception](../../mfc/reference/cnotsupportedexception-class.md).

`CMemFile`verwendet die Lauf Zeit Bibliotheksfunktionen [malloc](../../c-runtime-library/reference/malloc.md), [realloc](../../c-runtime-library/reference/realloc.md)und Free, um Speicher zuzuordnen, neu zuzuordnen und [frei](../../c-runtime-library/reference/free.md) zugeben. und die systeminterne [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md) zum Blockieren des Kopier Speichers beim Lesen und schreiben. Wenn Sie dieses Verhalten oder das Verhalten ändern möchten `CMemFile` , wenn eine Datei wächst, leiten Sie eine eigene Klasse von ab, `CMemFile` und überschreiben Sie die entsprechenden Funktionen.

Weitere Informationen zu finden Sie in `CMemFile` den Artikeln [Dateien in MFC](../../mfc/files-in-mfc.md) und in der [Speicherverwaltung (MFC)](../../mfc/memory-management.md) und unter [Datei Behandlung](../../c-runtime-library/file-handling.md) in der *Lauf Zeit Bibliotheks Referenz*.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CMemFile`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFX. h

## <a name="cmemfilealloc"></a><a name="alloc"></a>CMemFile:: Zuweisung

Diese Funktion wird von Element `CMemFile` Funktionen aufgerufen.

```
virtual BYTE* Alloc(SIZE_T nBytes);
```

### <a name="parameters"></a>Parameter

*nBytes*<br/>
Anzahl der zugeordneten Arbeitsspeicher bytes.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den zugeordneten Speicherblock oder NULL, wenn die Zuordnung fehlgeschlagen ist.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um benutzerdefinierte Speicher Belegung zu implementieren. Wenn Sie diese Funktion überschreiben, möchten Sie wahrscheinlich auch die [Kostenlose](#free) und [erneute Zuweisung](#realloc) überschreiben.

Die Standard Implementierung verwendet die Lauf Zeit Bibliotheksfunktion [malloc](../../c-runtime-library/reference/malloc.md) , um Arbeitsspeicher zuzuweisen.

## <a name="cmemfileattach"></a><a name="attach"></a>CMemFile:: Attach

Mit dieser Funktion können Sie einen Speicherblock an anfügen `CMemFile` .

```cpp
void Attach(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>Parameter

*lpBuffer*<br/>
Zeiger auf den Puffer, der angefügt werden soll `CMemFile` .

*nbuffersize*<br/>
Eine ganze Zahl, die die Größe des Puffers in Bytes angibt.

*ngrowbytes*<br/>
Das Inkrement der Arbeitsspeicher Belegung in Bytes.

### <a name="remarks"></a>Bemerkungen

Dies bewirkt `CMemFile` , dass der Speicherblock als Speicherdatei verwendet wird.

Wenn *ngrowbytes* den Wert 0 hat, `CMemFile` wird die Dateilänge von auf *nbuffersize*festgelegt. Dies bedeutet, dass die Daten im Speicherblock, vor dem Sie angefügt wurden, `CMemFile` als Datei verwendet werden. Speicherdateien, die auf diese Weise erstellt werden, können nicht vergrößert werden.

Da die Datei nicht vergrößert werden kann, sollten Sie darauf achten, dass Sie nicht `CMemFile` versuchen, die Datei zu vergrößern. Beispielsweise müssen Sie nicht die außer `CMemFile` Kraft setzungen von [CFile: Write](../../mfc/reference/cfile-class.md#write) aufrufen, um über das Ende hinaus zu schreiben, oder [CFile: SetLength](../../mfc/reference/cfile-class.md#setlength) mit einer Länge, die länger als *nbuffersize*ist, nicht aufrufen.

Wenn *ngrowbytes* größer als 0 (null) ist, `CMemFile` wird der Inhalt des angefügten Speicherblocks von ignoriert. Sie müssen den Inhalt der Speicherdatei mit der außer Kraft Setzung von neu schreiben `CMemFile` `CFile::Write` . Wenn Sie versuchen, über das Dateiende hinaus zu schreiben oder die Datei durch Aufrufen der- `CMemFile` Überschreibung von zu vergrößern `CFile::SetLength` , `CMemFile` wächst die Speicher Belegung in Inkrementen von *ngrowbytes*. Das Vergrößern der Speicher Belegung schlägt fehl, wenn der von Ihnen übergebene Speicherblock `Attach` nicht mit einer mit [Alloc](#alloc)kompatiblen Methode zugeordnet wurde. Um mit der Standard Implementierung von kompatibel zu sein `Alloc` , müssen Sie den Arbeitsspeicher der Lauf Zeit Bibliotheksfunktion " [malloc](../../c-runtime-library/reference/malloc.md) " oder " [calloc](../../c-runtime-library/reference/calloc.md)" zuordnen.

## <a name="cmemfilecmemfile"></a><a name="cmemfile"></a>CMemFile:: CMemFile

Die erste Überladung öffnet eine leere Speicherdatei.

```
CMemFile(UINT nGrowBytes = 1024);

CMemFile(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>Parameter

*ngrowbytes*<br/>
Das Inkrement der Arbeitsspeicher Belegung in Bytes.

*lpBuffer* Ein Zeiger auf einen Puffer, der Informationen über die Größe *nbuffersize*empfängt.

*nbuffersize*<br/>
Eine ganze Zahl, die die Größe des Datei Puffers in Bytes angibt.

### <a name="remarks"></a>Bemerkungen

Die Datei wird vom-Konstruktor geöffnet. [CFile:: Open](../../mfc/reference/cfile-class.md#open)nicht aufzurufen.

Die zweite Überladung verhält sich wie, wenn Sie den ersten Konstruktor verwendet und sofort [Attach](#attach) mit denselben Parametern aufgerufen haben. Einzelheiten dazu finden Sie unter `Attach`.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#36](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]

## <a name="cmemfiledetach"></a><a name="detach"></a>CMemFile::D Etach

Mit dieser Funktion können Sie einen Zeiger auf den Speicherblock abrufen, der von verwendet wird `CMemFile` .

```
BYTE* Detach();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Speicherblock, der den Inhalt der Speicherdatei enthält.

### <a name="remarks"></a>Bemerkungen

Durch den Aufruf dieser Funktion wird auch das geschlossen `CMemFile` . Sie können den Speicherblock erneut an anfügen, `CMemFile` indem Sie [Anfügen](#attach)aufrufen. Wenn Sie die Datei erneut anfügen und die darin verwendeten Daten verwenden möchten, sollten Sie [CFile:: GetLength](../../mfc/reference/cfile-class.md#getlength) aufrufen, um die Länge der Datei vor dem Aufrufen von zu erhalten `Detach` . Wenn Sie einen Speicherblock an `CMemFile` Anfügen, sodass Sie seine Daten ( `nGrowBytes` = = 0) verwenden können, können Sie die Speicherdatei nicht vergrößern.

## <a name="cmemfilefree"></a><a name="free"></a>CMemFile:: Free

Diese Funktion wird von Element `CMemFile` Funktionen aufgerufen.

```
virtual void Free(BYTE* lpMem);
```

### <a name="parameters"></a>Parameter

*lpmem*<br/>
Zeiger auf den Arbeitsspeicher, dessen Zuordnung aufgehoben werden soll.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um eine benutzerdefinierte Speicherfreigabe zu implementieren. Wenn Sie diese Funktion außer Kraft setzen, sollten Sie [Zuordnungs](#alloc) -und [rezuweisung](#realloc) auch überschreiben.

## <a name="cmemfilegetbufferptr"></a><a name="getbufferptr"></a>CMemFile:: getbufferptr

Hiermit wird der Arbeitsspeicher Puffer, der eine Speicherdatei sichert, in den Arbeitsspeicher Puffer geschrieben

```cpp
virtual UINT GetBufferPtr(
    UINT nCommand,
    UINT nCount = 0,
    void** ppBufStart = NULL,
    void** ppBufMax = NULL
);
```

### <a name="parameters"></a>Parameter

*nausgeführter Befehl*<br/>
Der [buffercommand](buffercommand-enumeration.md) , der durchgeführt `bufferCheck` werden soll (, `bufferCommit` , `bufferRead` oder `bufferWrite` ).

*nCount*<br/>
Abhängig von *nCommand*die Anzahl der Bytes im Puffer, die gelesen, geschrieben oder mit Commit geschrieben werden sollen. Geben Sie beim Lesen aus dem Puffer-1 an, um einen Puffer von der aktuellen Position bis zum Ende der Datei zurückzugeben.

*ppbuf starten*<br/>
vorgenommen Der Anfang des Puffers. Muss sein, `NULL` Wenn *nCommand* den Wert hat `bufferCommit` .

*ppbuf Max*<br/>
vorgenommen Das Ende des Puffers. Muss sein, `NULL` Wenn nCommand den Wert hat `bufferCommit` .

### <a name="return-value"></a>Rückgabewert

| *Befehls* Wert | Rückgabewert |
|--|--|
| `buffercheck` | Gibt [bufferdirect](buffercommand-enumeration.md) zurück, wenn direkte Pufferung unterstützt wird; andernfalls 0. |
| `bufferCommit` | Gibt `0` zurück. |
| `bufferRead` oder `bufferWrite` | Gibt die Anzahl der Bytes im zurückgegebenen Pufferbereich zurück. *ppbufstart* und *ppbufmax* zeigen auf den Anfang und das Ende des Lese-/Schreibpuffers.  |

### <a name="remarks"></a>Bemerkungen

Die aktuelle Position im Speicherpuffer ( `m_nPosition` ) wird abhängig von *nCommand*auf die folgenden Arten erweitert:

| *nausgeführter Befehl* | Puffer Position |
|-|-|
| `bufferCommit` | Die aktuelle Position wechselt um die Größe des zugesicherte Puffers. |
| `bufferRead` | Die aktuelle Position wechselt um die Größe des Lese Puffers. |

## <a name="cmemfilegrowfile"></a><a name="growfile"></a>CMemFile:: growfile

Diese Funktion wird von mehreren der- `CMemFile` Member-Funktionen aufgerufen.

```
virtual void GrowFile(SIZE_T dwNewLen);
```

### <a name="parameters"></a>Parameter

*dwnewlen*<br/>
Die neue Größe der Speicherdatei.

### <a name="remarks"></a>Bemerkungen

Sie können Sie überschreiben, wenn Sie ändern möchten, wie `CMemFile` die Datei vergrößert. Die Standard Implementierung ruft [rebelegc](#realloc) auf, um einen vorhandenen Block (oder [Zuweisungs](#alloc) Zuweisung zum Erstellen eines Speicherblocks) zu vergrößern, wobei Speicher in Vielfachen des `nGrowBytes` im Konstruktor oder [Anfüge](#attach) Aufruf angegebenen Werts zugeordnet wird.

## <a name="cmemfilememcpy"></a><a name="memcpy"></a>CMemFile:: memcpy

Diese Funktion wird durch die außer Kraft setzungen `CMemFile` von [CFile:: Read](../../mfc/reference/cfile-class.md#read) und [CFile:: Write](../../mfc/reference/cfile-class.md#write) aufgerufen, um Daten in die und aus der Speicherdatei zu übertragen.

```
virtual BYTE* Memcpy(
    BYTE* lpMemTarget,
    const BYTE* lpMemSource,
    SIZE_T nBytes);
```

### <a name="parameters"></a>Parameter

*lpmemtarget*<br/>
Zeiger auf den Speicherblock, in den der Quell Speicher kopiert wird.

*lpmemsource*<br/>
Zeiger auf den Quell Speicherblock.

*nBytes*<br/>
Anzahl der zu kopierenden Bytes.

### <a name="return-value"></a>Rückgabewert

Eine Kopie von *lpmemtarget*.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, wenn Sie die Art und Weise ändern möchten, in der `CMemFile` Diese Speicher Kopien verwendet werden.

## <a name="cmemfilerealloc"></a><a name="realloc"></a>CMemFile:: rezuweisung

Diese Funktion wird von Element `CMemFile` Funktionen aufgerufen.

```
virtual BYTE* Realloc(
    BYTE* lpMem,
    SIZE_T nBytes);
```

### <a name="parameters"></a>Parameter

*lpmem*<br/>
Ein Zeiger auf den Speicherblock, der neu zugeordnet werden soll.

*nBytes*<br/>
Neue Größe für den Speicherblock.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Speicherblock, der neu zugeordnet (und möglicherweise verschoben) wurde, oder NULL, wenn die erneute Zuordnung fehlgeschlagen ist.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um eine benutzerdefinierte Speicherzuweisung zu implementieren. Wenn Sie diese Funktion überschreiben, möchten Sie wahrscheinlich auch die [Zuordnungs](#alloc) -und [Kostenlose](#free) außer Kraft setzen.

## <a name="see-also"></a>Weitere Informationen

[CFile-Klasse](../../mfc/reference/cfile-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)
