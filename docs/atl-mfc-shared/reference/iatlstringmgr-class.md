---
title: IAtlStringMgr-Klasse
ms.date: 10/18/2018
f1_keywords:
- IAtlStringMgr
- ATLSIMPSTR/ATL::IAtlStringMgr
- ATLSIMPSTR/ATL::Allocate
- ATLSIMPSTR/ATL::Clone
- ATLSIMPSTR/ATL::Free
- ATLSIMPSTR/ATL::GetNilString
- ATLSIMPSTR/ATL::Reallocate
helpviewer_keywords:
- shared classes, IAtlStringMgr
- memory, managing
- IAtlStringMgr class
ms.assetid: 722f0346-a770-4aa7-8f94-177be8dba823
ms.openlocfilehash: bee9c3d27ea05a40d6835d69079fc3e0a56efb86
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219052"
---
# <a name="iatlstringmgr-class"></a>IAtlStringMgr-Klasse

Diese Klasse stellt die Schnittstelle zu einem `CStringT` Speicher-Manager dar.

## <a name="syntax"></a>Syntax

```
__interface IAtlStringMgr
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[Jugend](#allocate)|Diese Methode wird aufgerufen, um eine neue Zeichen folgen Datenstruktur zuzuordnen.|
|[Klonen](#clone)|Ruft diese Methode auf, um einen Zeiger auf einen neuen Zeichen folgen-Manager für die Verwendung mit einer anderen Instanz von zurückzugeben `CSimpleStringT` .|
|[Free](#free)|Mit dieser Methode können Sie eine Zeichen folgen Datenstruktur freigeben.|
|[GetNilString](#getnilstring)|Gibt einen Zeiger auf das-Objekt zurück, das `CStringData` von leeren Zeichen folgen Objekten verwendet wird.|
|[Erneuten Zuweisen](#reallocate)|Mit dieser Methode können Sie eine Zeichen folgen Datenstruktur neu zuordnen.|

## <a name="remarks"></a>Bemerkungen

Diese Schnittstelle verwaltet den von den MFC-unabhängigen Zeichen folgen Klassen verwendeten Arbeitsspeicher. z. b. [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)und [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md).

Sie können diese Klasse auch verwenden, um einen benutzerdefinierten Speicher-Manager für die benutzerdefinierte Zeichen folgen Klasse zu implementieren. Weitere Informationen finden Sie unter [Speicherverwaltung und CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlsimpstr. h

## <a name="iatlstringmgrallocate"></a><a name="allocate"></a>IAtlStringMgr:: zuordnen

Ordnet eine neue Zeichen folgen Datenstruktur zu.

```
CStringData* Allocate(int nAllocLength,int nCharSize) throw();
```

### <a name="parameters"></a>Parameter

*nzuweisung*<br/>
Die Anzahl der Zeichen im neuen Speicherblock.

*ncharsize*<br/>
Die Größe (in Bytes) des Zeichen Typs, der vom Zeichen folgen-Manager verwendet wird.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf den neu belegten Speicherblock zurück.

> [!NOTE]
> Signalisieren Sie keine fehlgeschlagene Zuordnung, indem Sie eine Ausnahme auslösen. Stattdessen sollte eine fehlerhafte Zuordnung signalisiert werden, indem NULL zurückgegeben wird.

### <a name="remarks"></a>Bemerkungen

Nennen Sie [IAtlStringMgr:: Free](#free) oder [IAtlStringMgr:: rezuordnen](#reallocate) , um den von dieser Methode belegten Arbeitsspeicher freizugeben.

> [!NOTE]
> Verwendungs Beispiele finden Sie unter [Speicherverwaltung und CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrclone"></a><a name="clone"></a>IAtlStringMgr:: Clone

Gibt einen Zeiger auf einen neuen Zeichen folgen-Manager zurück, der mit einer anderen Instanz von verwendet werden soll `CSimpleStringT` .

```
IAtlStringMgr* Clone() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt eine Kopie des `IAtlStringMgr`-Objekts zurück.

### <a name="remarks"></a>Bemerkungen

Wird häufig von Framework aufgerufen, wenn ein Zeichen folgen-Manager für eine neue Zeichenfolge benötigt wird. In den meisten Fällen wird der- **`this`** Zeiger zurückgegeben.

Wenn der Speicher-Manager die Verwendung durch mehrere Instanzen von jedoch nicht unterstützt `CSimpleStringT` , sollte ein Zeiger auf einen freigegeben-Zeichen folgen-Manager zurückgegeben werden.

> [!NOTE]
> Verwendungs Beispiele finden Sie unter [Speicherverwaltung und CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrfree"></a><a name="free"></a>IAtlStringMgr:: Free

Gibt eine Zeichen folgen Datenstruktur frei.

```cpp
void Free(CStringData* pData) throw();
```

### <a name="parameters"></a>Parameter

*pData*<br/>
Ein Zeiger auf den Speicherblock, der freigegeben werden soll.

### <a name="remarks"></a>Bemerkungen

Gibt den angegebenen Speicherblock frei, der zuvor durch [zuordnen](#allocate) oder [Neuzuordnen reserviert](../../atl/reference/iatlmemmgr-class.md#reallocate)wurde.

> [!NOTE]
> Verwendungs Beispiele finden Sie unter [Speicherverwaltung und CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrgetnilstring"></a><a name="getnilstring"></a>IAtlStringMgr:: GetNilString

Gibt einen Zeiger auf eine Zeichen folgen Datenstruktur für eine leere Zeichenfolge zurück.

```
CStringData* GetNilString() throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das- `CStringData` Objekt, das verwendet wird, um eine leere Zeichenfolge darzustellen.

### <a name="remarks"></a>Bemerkungen

Mit dieser Funktion wird eine Darstellung einer leeren Zeichenfolge zurückgegeben.

> [!NOTE]
> Bei der Implementierung eines benutzerdefinierten Zeichen folgen-Managers darf diese Funktion nie fehlschlagen. Dies können Sie sicherstellen, indem Sie eine Instanz von `CNilStringData` in der String Manager-Klasse einbetten und einen Zeiger auf diese Instanz zurückgeben.

> [!NOTE]
> Verwendungs Beispiele finden Sie unter [Speicherverwaltung und CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrreallocate"></a><a name="reallocate"></a>IAtlStringMgr:: Neuzuordnung

Ordnet eine Zeichen folgen Datenstruktur neu zu.

```
CStringData* Reallocate(
    CStringData* pData,
    int nAllocLength,
    int nCharSize) throw();
```

### <a name="parameters"></a>Parameter

*pData*<br/>
Zeiger auf den Arbeitsspeicher, der zuvor von diesem Speicher-Manager zugewiesen wurde.

*nzuweisung*<br/>
Die Anzahl der Zeichen im neuen Speicherblock.

*ncharsize*<br/>
Die Größe (in Bytes) des Zeichen Typs, der vom Zeichen folgen-Manager verwendet wird.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf den Anfang des neu belegten Speicherblocks zurück.

### <a name="remarks"></a>Bemerkungen

Mit dieser Funktion können Sie die Größe des vorhandenen Speicherblocks ändern, der von *pData*angegeben wird.

Nennen Sie [IAtlStringMgr:: Free](#free) , um den von dieser Methode belegten Arbeitsspeicher freizugeben.

> [!NOTE]
> Verwendungs Beispiele finden Sie unter [Speicherverwaltung und CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Gemeinsam genutzte ATL/MFC-Klassen](../../atl-mfc-shared/atl-mfc-shared-classes.md)
