---
title: CMemFile-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMemFile
- AFX/CMemFile
- AFX/CMemFile::CMemFile
- AFX/CMemFile::Attach
- AFX/CMemFile::Detach
- AFX/CMemFile::Alloc
- AFX/CMemFile::Free
- AFX/CMemFile::GrowFile
- AFX/CMemFile::Memcpy
- AFX/CMemFile::Realloc
helpviewer_keywords:
- CMemFile [MFC], CMemFile
- CMemFile [MFC], Attach
- CMemFile [MFC], Detach
- CMemFile [MFC], Alloc
- CMemFile [MFC], Free
- CMemFile [MFC], GrowFile
- CMemFile [MFC], Memcpy
- CMemFile [MFC], Realloc
ms.assetid: 20e86515-e465-4f73-b2ea-e49789d63165
ms.openlocfilehash: 1bd88ad17bdb047de4c344ab96f3d9aecbe23c31
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752638"
---
# <a name="cmemfile-class"></a>CMemFile-Klasse

Die [CFile](../../mfc/reference/cfile-class.md)-derived-Klasse, die Speicherdateien unterstützt.

## <a name="syntax"></a>Syntax

```
class CMemFile : public CFile
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMemFile::CMemFile](#cmemfile)|Erstellt ein Speicherdateiobjekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMemFile::Anfügen](#attach)|Fügt einen Speicherblock `CMemFile`an an .|
|[CMemFile::Detach](#detach)|Trennt den Speicherblock und `CMemFile` gibt einen Zeiger an den getrennten Speicherblock zurück.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMemFile::Alloc](#alloc)|Überschreiben, um das Speicherzuweisungsverhalten zu ändern.|
|[CMemFile::Kostenlos](#free)|Überschreiben, um das Speicherzuweisungsverhalten zu ändern.|
|[CMemFile::GrowFile](#growfile)|Überschreiben, um das Verhalten beim Erstellen einer Datei zu ändern.|
|[CMemFile::Memcpy](#memcpy)|Überschreiben, um das Verhalten beim Lesen und Schreiben von Dateien zu ändern.|
|[CMemFile::Realloc](#realloc)|Überschreiben, um das Verhalten der Speicherumverteilung zu ändern.|

## <a name="remarks"></a>Bemerkungen

Diese Speicherdateien verhalten sich wie Festplattendateien, außer dass die Datei im RAM und nicht auf dem Datenträger gespeichert ist. Eine Speicherdatei ist nützlich für den schnellen temporären Speicher oder für die Übertragung von Unformatbytes oder serialisierten Objekten zwischen unabhängigen Prozessen.

`CMemFile`Objekte können automatisch ihren eigenen Speicher zuweisen oder Sie `CMemFile` können einen eigenen Speicherblock an das Objekt anfügen, indem Sie [Attach](#attach)aufrufen. In beiden Fällen wird der Speicher zum `nGrowBytes`Automatischen Erweitern der `nGrowBytes` Speicherdatei in Schritten in -Größe zugewiesen, wenn nicht Null ist.

Der Speicherblock wird automatisch bei `CMemFile` der Zerstörung des Objekts `CMemFile` gelöscht, wenn der Speicher ursprünglich vom Objekt zugewiesen wurde. Andernfalls sind Sie dafür verantwortlich, den Speicher, den Sie an das Objekt angefügt haben, zu verteilen.

Sie können über den bereitgestellten Zeiger auf den Speicherblock zugreifen, wenn Sie ihn vom `CMemFile` Objekt trennen, indem Sie [Detach](#detach)aufrufen.

Die häufigste Verwendung `CMemFile` besteht darin, ein `CMemFile` Objekt zu erstellen und es durch Aufrufen von [CFile-Memberfunktionen](../../mfc/reference/cfile-class.md) zu verwenden. Beachten Sie, `CMemFile` dass das Erstellen eines automatisch öffnet: Sie rufen [CFile::Open](../../mfc/reference/cfile-class.md#open)nicht auf, das nur für Datenträgerdateien verwendet wird. Da `CMemFile` keine Datenträgerdatei verwendet wird, `CFile::m_hFile` wird das Datenmember nicht verwendet.

Die `CFile` Memberfunktionen [Duplicate](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange)und [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) sind für `CMemFile`nicht implementiert. Wenn Sie diese Funktionen `CMemFile` für ein Objekt aufrufen, erhalten Sie eine [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

`CMemFile`verwendet die Laufzeitbibliotheksfunktionen [malloc](../../c-runtime-library/reference/malloc.md), [realloc](../../c-runtime-library/reference/realloc.md)und [frei,](../../c-runtime-library/reference/free.md) Speicher zuzuweisen, neu zuzuweisen und zuverteilen. und die intrinsische [Memcpy,](../../c-runtime-library/reference/memcpy-wmemcpy.md) um kopierspeicher beim Lesen und Schreiben zu blockieren. Wenn Sie dieses Verhalten oder das Verhalten `CMemFile` beim Erstellen einer Datei ändern `CMemFile` möchten, leiten Sie Ihre eigene Klasse ab, und überschreiben Sie die entsprechenden Funktionen.

Weitere Informationen `CMemFile`finden Sie in den Artikeln [Dateien in MFC](../../mfc/files-in-mfc.md) und [Speicherverwaltung (MFC)](../../mfc/memory-management.md) und unter [Dateiverarbeitung](../../c-runtime-library/file-handling.md) in der *Laufzeitbibliotheksreferenz*.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CMemFile`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afx.h

## <a name="cmemfilealloc"></a><a name="alloc"></a>CMemFile::Alloc

Diese Funktion wird `CMemFile` von Memberfunktionen aufgerufen.

```
virtual BYTE* Alloc(SIZE_T nBytes);
```

### <a name="parameters"></a>Parameter

*nBytes*<br/>
Anzahl der zuzuweisenden Bytes des Zuteilungsspeichers.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Speicherblock, der zugewiesen wurde, oder NULL, wenn die Zuweisung fehlgeschlagen ist.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um die benutzerdefinierte Speicherzuweisung zu implementieren. Wenn Sie diese Funktion überschreiben, sollten Sie wahrscheinlich auch [Free](#free) und [Realloc](#realloc) überschreiben.

Die Standardimplementierung verwendet die Laufzeitbibliotheksfunktion [malloc,](../../c-runtime-library/reference/malloc.md) um Speicher zuzuweisen.

## <a name="cmemfileattach"></a><a name="attach"></a>CMemFile::Anfügen

Rufen Sie diese Funktion auf, `CMemFile`um einen Speicherblock an an anzuhängen.

```cpp
void Attach(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>Parameter

*lpBuffer*<br/>
Zeiger auf den Puffer, `CMemFile`der an angefügt werden soll.

*nBufferSize*<br/>
Eine ganze Zahl, die die Größe des Puffers in Bytes angibt.

*nGrowBytes*<br/>
Das Speicherzuweisungsinkrement in Bytes.

### <a name="remarks"></a>Bemerkungen

Dies `CMemFile` bewirkt, dass der Speicherblock als Speicherdatei verwendet wird.

Wenn *nGrowBytes* 0 `CMemFile` ist, wird die Dateilänge auf *nBufferSize*festgelegt. Dies bedeutet, dass die Daten im `CMemFile` Speicherblock, an die er angefügt wurde, als Datei verwendet werden. Speicherdateien, die auf diese Weise erstellt wurden, können nicht vergrößert werden.

Da die Datei nicht vergrößert werden `CMemFile` kann, achten Sie darauf, dass Sie nicht versuchen, die Datei zu vergrößern. Rufen Sie beispielsweise `CMemFile` die Überschreibungen von [CFile:Write](../../mfc/reference/cfile-class.md#write) nicht auf, um das Ende zu überschreiben, oder rufen Sie [CFile:SetLength](../../mfc/reference/cfile-class.md#setlength) nicht mit einer Länge auf, die länger als *nBufferSize*ist.

Wenn *nGrowBytes* größer als `CMemFile` 0 ist, wird der Inhalt des Speicherblocks ignoriert, den Sie angefügt haben. Sie müssen den Inhalt der Speicherdatei von Grund `CMemFile` auf `CFile::Write`neu schreiben, indem Sie die Überschreibung von . Wenn Sie versuchen, das Ende der Datei zu überschreiten `CMemFile` oder `CFile::SetLength`die `CMemFile` Datei durch Aufrufen der Außerkraftsetzung von zu vergrößern, vergrößert sich die Speicherzuweisung in Schritten von *nGrowBytes*. Das Erweitern der Speicherzuweisung schlägt fehl, `Attach` wenn der Speicherblock, an den Sie übergeben, nicht mit einer Methode zugewiesen wurde, die mit [Alloc](#alloc)kompatibel ist. Um mit der Standardimplementierung `Alloc`von kompatibel zu sein, müssen Sie den Speicher mit der Laufzeitbibliotheksfunktion [malloc](../../c-runtime-library/reference/malloc.md) oder [calloc](../../c-runtime-library/reference/calloc.md)zuweisen.

## <a name="cmemfilecmemfile"></a><a name="cmemfile"></a>CMemFile::CMemFile

Die erste Überladung öffnet eine leere Speicherdatei.

```
CMemFile(UINT nGrowBytes = 1024);

CMemFile(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>Parameter

*nGrowBytes*<br/>
Das Speicherzuweisungsinkrement in Bytes.

*lpBuffe*r Zeiger auf einen Puffer, der Informationen der Größe *nBufferSize*empfängt.

*nBufferSize*<br/>
Eine ganze Zahl, die die Größe des Dateipuffers in Bytes angibt.

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass die Datei vom Konstruktor geöffnet wird und Sie [CFile::Open](../../mfc/reference/cfile-class.md#open)nicht aufrufen sollten.

Die zweite Überladung funktioniert genauso, als ob Sie den ersten Konstruktor verwendet und sofort [Attach](#attach) mit den gleichen Parametern aufgerufen haben. Einzelheiten dazu finden Sie unter `Attach`.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#36](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]

## <a name="cmemfiledetach"></a><a name="detach"></a>CMemFile::Detach

Rufen Sie diese Funktion auf, um einen `CMemFile`Zeiger auf den Speicherblock abzurufen, der von verwendet wird.

```
BYTE* Detach();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Speicherblock, der den Inhalt der Speicherdatei enthält.

### <a name="remarks"></a>Bemerkungen

Durch Aufrufen dieser Funktion `CMemFile`wird auch die geschlossen. Sie können den Speicherblock `CMemFile` erneut anfügen, indem Sie [Attach](#attach)aufrufen. Wenn Sie die Datei erneut anhängen und die darin gespeicherten Daten verwenden möchten, rufen Sie `Detach` [CFile::GetLength](../../mfc/reference/cfile-class.md#getlength) auf, um die Länge der Datei vor dem Aufruf abzurufen. Beachten Sie, dass Sie `CMemFile` die Speicherdatei nicht vergrößern `nGrowBytes` können, wenn Sie einen Speicherblock anfügen, damit Sie seine Daten verwenden können ( == 0).

## <a name="cmemfilefree"></a><a name="free"></a>CMemFile::Kostenlos

Diese Funktion wird `CMemFile` von Memberfunktionen aufgerufen.

```
virtual void Free(BYTE* lpMem);
```

### <a name="parameters"></a>Parameter

*lpMem*<br/>
Zeiger auf den zu behandelnden Speicher.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um die benutzerdefinierte Speicherzuweisung zu implementieren. Wenn Sie diese Funktion überschreiben, sollten Sie wahrscheinlich auch [Alloc](#alloc) und [Realloc](#realloc) überschreiben.

## <a name="cmemfilegrowfile"></a><a name="growfile"></a>CMemFile::GrowFile

Diese Funktion wird von `CMemFile` mehreren Memberfunktionen aufgerufen.

```
virtual void GrowFile(SIZE_T dwNewLen);
```

### <a name="parameters"></a>Parameter

*dwNewLen*<br/>
Neue Größe der Speicherdatei.

### <a name="remarks"></a>Bemerkungen

Sie können es überschreiben, wenn `CMemFile` Sie ändern möchten, wie die Datei wächst. Die Standardimplementierung ruft [Realloc](#realloc) auf, um einen vorhandenen Block (oder [Alloc,](#alloc) um `nGrowBytes` einen Speicherblock zu erstellen) zu vergrößern und Speicher in Vielfachen des im Konstruktor oder [Attach-Aufruf](#attach) angegebenen Werts zuzuweisen.

## <a name="cmemfilememcpy"></a><a name="memcpy"></a>CMemFile::Memcpy

Diese Funktion wird `CMemFile` durch die Überschreibungen von [CFile::Read](../../mfc/reference/cfile-class.md#read) und [CFile::Write](../../mfc/reference/cfile-class.md#write) aufgerufen, um Daten in und aus der Speicherdatei zu übertragen.

```
virtual BYTE* Memcpy(
    BYTE* lpMemTarget,
    const BYTE* lpMemSource,
    SIZE_T nBytes);
```

### <a name="parameters"></a>Parameter

*lpMemTarget*<br/>
Zeiger auf den Speicherblock, in den der Quellspeicher kopiert wird.

*lpMemSource*<br/>
Zeiger auf den Quellspeicherblock.

*nBytes*<br/>
Anzahl der zu kopierenden Bytes.

### <a name="return-value"></a>Rückgabewert

Eine Kopie von *lpMemTarget*.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, wenn `CMemFile` Sie die Art und Weise ändern möchten, wie diese Speicherkopien bewirkt werden.

## <a name="cmemfilerealloc"></a><a name="realloc"></a>CMemFile::Realloc

Diese Funktion wird `CMemFile` von Memberfunktionen aufgerufen.

```
virtual BYTE* Realloc(
    BYTE* lpMem,
    SIZE_T nBytes);
```

### <a name="parameters"></a>Parameter

*lpMem*<br/>
Ein Zeiger auf den Speicherblock, der neu verteilt werden soll.

*nBytes*<br/>
Neue Größe für den Speicherblock.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Speicherblock, der neu verteilt (und möglicherweise verschoben) wurde, oder NULL, wenn die Neuzuweisung fehlgeschlagen ist.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um eine benutzerdefinierte Speicherneuzuweisung zu implementieren. Wenn Sie diese Funktion überschreiben, sollten Sie wahrscheinlich auch [Alloc](#alloc) und [Free](#free) überschreiben.

## <a name="see-also"></a>Weitere Informationen

[CFile-Klasse](../../mfc/reference/cfile-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
