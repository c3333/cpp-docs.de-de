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
ms.openlocfilehash: c3fabb7a7a6da4129787d219bd83b2a35fa0c4dd
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746610"
---
# <a name="iatlstringmgr-class"></a>IAtlStringMgr-Klasse

Diese Klasse stellt die `CStringT` Schnittstelle zu einem Speicher-Manager dar.

## <a name="syntax"></a>Syntax

```
__interface IAtlStringMgr
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[Zuordnen](#allocate)|Rufen Sie diese Methode auf, um eine neue Zeichenfolgendatenstruktur zuzuweisen.|
|[Klon](#clone)|Rufen Sie diese Methode auf, um einen Zeiger an `CSimpleStringT`einen neuen Zeichenfolgen-Manager zur Verwendung mit einer anderen Instanz von zurückzugeben.|
|[Free](#free)|Rufen Sie diese Methode auf, um eine Zeichenfolgendatenstruktur freizugeben.|
|[GetNilString](#getnilstring)|Gibt einen Zeiger `CStringData` auf das Objekt zurück, das von leeren Zeichenfolgenobjekten verwendet wird.|
|[Reservieren](#reallocate)|Rufen Sie diese Methode auf, um eine Zeichenfolgendatenstruktur neu zuzuweisen.|

## <a name="remarks"></a>Bemerkungen

Diese Schnittstelle verwaltet den Speicher, der von den MFC-unabhängigen Zeichenfolgenklassen verwendet wird. wie [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)und [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md).

Sie können diese Klasse auch verwenden, um einen benutzerdefinierten Speicher-Manager für Ihre benutzerdefinierte Zeichenfolgenklasse zu implementieren. Weitere Informationen finden Sie unter [Speicherverwaltung und CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlsimpstr.h

## <a name="iatlstringmgrallocate"></a><a name="allocate"></a>IAtlStringMgr::Zuweisen

Ordnet eine neue Zeichenfolgendatenstruktur zu.

```
CStringData* Allocate(int nAllocLength,int nCharSize) throw();
```

### <a name="parameters"></a>Parameter

*nAllocLength*<br/>
Die Anzahl der Zeichen im neuen Speicherblock.

*nCharSize*<br/>
Die Größe (in Bytes) des Zeichentyps, der vom Zeichenfolgen-Manager verwendet wird.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf den neu belegten Speicherblock zurück.

> [!NOTE]
> Signalisieren Sie keine fehlgeschlagene Zuordnung, indem Sie eine Ausnahme auslösen. Stattdessen sollte eine fehlgeschlagene Zuordnung durch Rückgabe von NULL signalisiert werden.

### <a name="remarks"></a>Bemerkungen

Rufen Sie [IAtlStringMgr::Free](#free) oder [IAtlStringMgr::ReAllocate](#reallocate) auf, um den von dieser Methode zugewiesenen Speicher freizugeben.

> [!NOTE]
> Anwendungsbeispiele finden Sie unter [Speicherverwaltung und CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrclone"></a><a name="clone"></a>IAtlStringMgr::Klonen

Gibt einen Zeiger an einen neuen Zeichenfolgen-Manager zur Verwendung mit einer anderen Instanz von `CSimpleStringT`zurück.

```
IAtlStringMgr* Clone() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt eine Kopie des `IAtlStringMgr`-Objekts zurück.

### <a name="remarks"></a>Bemerkungen

Wird häufig vom Framework aufgerufen, wenn ein Zeichenfolgen-Manager für eine neue Zeichenfolge benötigt wird. In den meisten Fällen wird **dieser** Zeiger zurückgegeben.

Wenn der Speicher-Manager jedoch die Verwendung durch `CSimpleStringT`mehrere Instanzen von nicht unterstützt, sollte ein Zeiger auf einen sharablen Zeichenfolgen-Manager zurückgegeben werden.

> [!NOTE]
> Anwendungsbeispiele finden Sie unter [Speicherverwaltung und CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrfree"></a><a name="free"></a>IAtlStringMgr::Kostenlos

Gibt eine Zeichenfolgendatenstruktur frei.

```cpp
void Free(CStringData* pData) throw();
```

### <a name="parameters"></a>Parameter

*pData*<br/>
Ein Zeiger auf den Speicherblock, der freigegeben werden soll.

### <a name="remarks"></a>Bemerkungen

Gibt den angegebenen Speicherblock frei, der zuvor von [Allocate](#allocate) oder [Reallocate](../../atl/reference/iatlmemmgr-class.md#reallocate)zugewiesen wurde.

> [!NOTE]
> Anwendungsbeispiele finden Sie unter [Speicherverwaltung und CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrgetnilstring"></a><a name="getnilstring"></a>IAtlStringMgr::GetNilString

Gibt einen Zeiger auf eine Zeichenfolgendatenstruktur für eine leere Zeichenfolge zurück.

```
CStringData* GetNilString() throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CStringData` das Objekt, das zur Darstellung einer leeren Zeichenfolge verwendet wird.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um eine Darstellung einer leeren Zeichenfolge zurückzugeben.

> [!NOTE]
> Beim Implementieren eines benutzerdefinierten Zeichenfolgen-Managers darf diese Funktion niemals fehlschlagen. Sie können dies sicherstellen, `CNilStringData` indem Sie eine Instanz von in die Zeichenfolgen-Manager-Klasse einbetten und einen Zeiger auf diese Instanz zurückgeben.

> [!NOTE]
> Anwendungsbeispiele finden Sie unter [Speicherverwaltung und CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrreallocate"></a><a name="reallocate"></a>IAtlStringMgr::Neuzuordnen

Ordnet eine Zeichenfolgendatenstruktur neu zu.

```
CStringData* Reallocate(
    CStringData* pData,
    int nAllocLength,
    int nCharSize) throw();
```

### <a name="parameters"></a>Parameter

*pData*<br/>
Zeigen Sie auf den Speicher, der zuvor von diesem Speicher-Manager zugewiesen wurde.

*nAllocLength*<br/>
Die Anzahl der Zeichen im neuen Speicherblock.

*nCharSize*<br/>
Die Größe (in Bytes) des Zeichentyps, der vom Zeichenfolgen-Manager verwendet wird.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf den Anfang des neu belegten Speicherblocks zurück.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um die Größe des vorhandenen Speicherblocks zu ändern, der von *pData*angegeben wird.

Rufen Sie [IAtlStringMgr::Free](#free) auf, um den von dieser Methode zugewiesenen Speicher freizugeben.

> [!NOTE]
> Anwendungsbeispiele finden Sie unter [Speicherverwaltung und CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[FREIGEGEBENe ATL/MFC-Klassen](../../atl-mfc-shared/atl-mfc-shared-classes.md)
