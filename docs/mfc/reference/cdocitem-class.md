---
title: CDocItem-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDocItem
- AFXOLE/CDocItem
- AFXOLE/CDocItem::GetDocument
- AFXOLE/CDocItem::IsBlank
helpviewer_keywords:
- CDocItem [MFC], GetDocument
- CDocItem [MFC], IsBlank
ms.assetid: 84fb8610-a4c8-4211-adc0-e70e8d002c11
ms.openlocfilehash: 438bc2a03239946dbfca53d5f2989c731b682ab0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375625"
---
# <a name="cdocitem-class"></a>CDocItem-Klasse

Die Basisklasse für Dokumentelemente, die Komponenten der Daten eines Dokuments sind.

## <a name="syntax"></a>Syntax

```
class CDocItem : public CCmdTarget
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDocItem::GetDocument](#getdocument)|Gibt das Dokument zurück, das das Element enthält.|
|[CDocItem::IsBlank](#isblank)|Bestimmt, ob das Element Informationen enthält.|

## <a name="remarks"></a>Bemerkungen

`CDocItem`Objekte werden verwendet, um OLE-Elemente sowohl in Client- als auch in Serverdokumenten darzustellen.

Weitere Informationen finden Sie im Artikel [Container: Implementieren eines Containers](../../mfc/containers-implementing-a-container.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocItem`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxole.h

## <a name="cdocitemgetdocument"></a><a name="getdocument"></a>CDocItem::GetDocument

Rufen Sie diese Funktion auf, um das Dokument abzurufen, das das Element enthält.

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Dokument, das das Element enthält; NULL, wenn das Element nicht Teil eines Dokuments ist.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird in den abgeleiteten Klassen [COleClientItem](../../mfc/reference/coleclientitem-class.md) und [COleServerItem](../../mfc/reference/coleserveritem-class.md)überschrieben und gibt einen Zeiger entweder auf ein [COleDocument](../../mfc/reference/coledocument-class.md), ein [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)oder ein [COleServerDoc-Objekt](../../mfc/reference/coleserverdoc-class.md) zurück.

## <a name="cdocitemisblank"></a><a name="isblank"></a>CDocItem::IsBlank

Wird vom Framework aufgerufen, wenn die Standardserialisierung auftritt.

```
virtual BOOL IsBlank() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Element keine Informationen enthält; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Standardmäßig sind `CDocItem` Objekte nicht leer. [COleClientItem-Objekte](../../mfc/reference/coleclientitem-class.md) sind manchmal leer, `CDocItem`da sie direkt von abstammen. [COleServerItem-Objekte](../../mfc/reference/coleserveritem-class.md) sind jedoch immer leer. Standardmäßig werden OLE-Anwendungen, die Objekte ohne x- oder y-Ausdehnung enthalten, `COleClientItem` serialisiert. Dies geschieht, indem TRUE von `IsBlank` einer Außerkraftsetzung zurückgegeben wird, wenn das Element keine x- oder y-Ausdehnung hat.

Überschreiben Sie diese Funktion, wenn Sie während der Serialisierung andere Aktionen implementieren möchten.

## <a name="see-also"></a>Siehe auch

[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleDocument-Klasse](../../mfc/reference/coledocument-class.md)<br/>
[COleServerItem-Klasse](../../mfc/reference/coleserveritem-class.md)<br/>
[COleClientItem-Klasse](../../mfc/reference/coleclientitem-class.md)
