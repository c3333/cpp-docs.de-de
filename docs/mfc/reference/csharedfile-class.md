---
title: CSharedFile-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSharedFile
- AFXADV/CSharedFile
- AFXADV/CSharedFile::CSharedFile
- AFXADV/CSharedFile::Detach
- AFXADV/CSharedFile::SetHandle
helpviewer_keywords:
- CSharedFile [MFC], CSharedFile
- CSharedFile [MFC], Detach
- CSharedFile [MFC], SetHandle
ms.assetid: 5d000422-9ede-4318-a8c9-f7412b674f39
ms.openlocfilehash: c715ca1b8a2b647f89ada008f3c6606ca5e58783
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750393"
---
# <a name="csharedfile-class"></a>CSharedFile-Klasse

Die [CMemFile](../../mfc/reference/cmemfile-class.md)-derived-Klasse, die freigegebene Speicherdateien unterstützt.

## <a name="syntax"></a>Syntax

```
class CSharedFile : public CMemFile
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSharedFile::CSharedFile](#csharedfile)|Erstellt ein `CSharedFile`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSharedFile::Detach](#detach)|Schließt die freigegebene Speicherdatei und gibt das Handle des Speicherblocks zurück.|
|[CSharedFile::SetHandle](#sethandle)|Fügt die freigegebene Speicherdatei an einen Speicherblock an.|

## <a name="remarks"></a>Bemerkungen

Speicherdateien verhalten sich wie Datenträgerdateien. Der Unterschied ist, dass eine Speicherdatei im RAM und nicht auf dem Datenträger gespeichert wird. Eine Speicherdatei ist nützlich für den schnellen temporären Speicher oder für die Übertragung von Unformatbytes oder serialisierten Objekten zwischen unabhängigen Prozessen.

Freigegebene Speicherdateien unterscheiden sich von anderen Speicherdateien dadurch, dass speicherfür sie mit der [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) Windows-Funktion zugewiesen wird. Die `CSharedFile` Klasse speichert Daten in einem global `GlobalAlloc`zugeordneten Speicherblock (erstellt mit ), und dieser Speicherblock kann mit DDE, der `IDataObject`Zwischenablage oder anderen OLE/COM-einheitlichen Datenübertragungsvorgängen freigegeben werden, z. B. mithilfe von .

`GlobalAlloc`gibt ein HGLOBAL-Handle anstelle eines Zeigers auf den Speicher zurück, z. B. den von [malloc](../../c-runtime-library/reference/malloc.md)zurückgegebenen Zeiger . Der HGLOBAL-Handle wird in bestimmten Anwendungen benötigt. Um beispielsweise Daten in die Zwischenablage zu stellen, benötigen Sie ein HGLOBAL-Handle.

`CSharedFile`verwendet keine Speicherzuordnungsdateien, und die Daten können nicht direkt zwischen Prozessen freigegeben werden.

`CSharedFile`Objekte können automatisch ihren eigenen Speicher zuweisen. Sie können auch einen eigenen Speicherblock an das `CSharedFile` Objekt anfügen, indem Sie [CSharedFile::SetHandle](#sethandle)aufrufen. In beiden Fällen wird der Speicher zum `nGrowBytes`Erhöhen der Speicherdatei automatisch in Schritten in -Größe zugewiesen, wenn `nGrowBytes` es nicht Null ist.

Weitere Informationen finden Sie im Artikel [Dateien in MFC](../../mfc/files-in-mfc.md) und [Dateiverarbeitung](../../c-runtime-library/file-handling.md) in der *Laufzeitbibliotheksreferenz*.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CMemFile](../../mfc/reference/cmemfile-class.md)

`CSharedFile`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxadv.h

## <a name="csharedfilecsharedfile"></a><a name="csharedfile"></a>CSharedFile::CSharedFile

Erstellt ein `CSharedFile` Objekt und weist ihm Speicher zu.

```
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,
    UINT nGrowBytes = 4096);
```

### <a name="parameters"></a>Parameter

*nAllocFlags*<br/>
Flags, die angeben, wie Speicher zugewiesen werden soll. Eine Liste gültiger Flagwerte finden Sie unter [GlobalAlloc.](/windows/win32/api/winbase/nf-winbase-globalalloc)

*nGrowBytes*<br/>
Das Speicherzuweisungsinkrement in Bytes.

## <a name="csharedfiledetach"></a><a name="detach"></a>CSharedFile::Detach

Rufen Sie diese Funktion auf, um die Speicherdatei zu schließen und vom Speicherblock zu trennen.

```
HGLOBAL Detach();
```

### <a name="return-value"></a>Rückgabewert

Das Handle des Speicherblocks, der den Inhalt der Speicherdatei enthält.

### <a name="remarks"></a>Bemerkungen

Sie können es erneut öffnen, indem Sie [SetHandle](#sethandle)aufrufen, indem Sie das von **Detach**zurückgegebene Handle verwenden.

## <a name="csharedfilesethandle"></a><a name="sethandle"></a>CSharedFile::SetHandle

Rufen Sie diese Funktion auf, um `CSharedFile` einen Block des globalen Speichers an das Objekt anzuhängen.

```cpp
void SetHandle(
    HGLOBAL hGlobalMemory,
    BOOL bAllowGrow = TRUE);
```

### <a name="parameters"></a>Parameter

*hGlobalMemory*<br/>
Behandeln Sie den globalen Speicher, `CSharedFile`der an die angefügt werden soll.

*bAllowGrow*<br/>
Gibt an, ob der Speicherblock vergrößert werden darf.

### <a name="remarks"></a>Bemerkungen

Wenn *bAllowGrow* ungleich Null ist, wird die Größe des Speicherblocks bei Bedarf erhöht, z. B. wenn Sie versuchen, mehr Bytes in die Datei zu schreiben als die Größe des Speicherblocks.

## <a name="see-also"></a>Weitere Informationen

[CMemFile-Klasse](../../mfc/reference/cmemfile-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CMemFile-Klasse](../../mfc/reference/cmemfile-class.md)
