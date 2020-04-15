---
title: COleDropSource-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleDropSource
- AFXOLE/COleDropSource
- AFXOLE/COleDropSource::COleDropSource
- AFXOLE/COleDropSource::GiveFeedback
- AFXOLE/COleDropSource::OnBeginDrag
- AFXOLE/COleDropSource::QueryContinueDrag
helpviewer_keywords:
- COleDropSource [MFC], COleDropSource
- COleDropSource [MFC], GiveFeedback
- COleDropSource [MFC], OnBeginDrag
- COleDropSource [MFC], QueryContinueDrag
ms.assetid: d3eecc5f-a70b-4a01-b705-7d2c098ebe17
ms.openlocfilehash: 324c4b7273f021b43c319fb0a494ac843856c78a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375023"
---
# <a name="coledropsource-class"></a>COleDropSource-Klasse

Ermöglicht das Ziehen von Daten an ein Ablageziel.

## <a name="syntax"></a>Syntax

```
class COleDropSource : public CCmdTarget
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDropSource::COleDropSource](#coledropsource)|Erstellt ein `COleDropSource`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDropSource::GiveFeedback](#givefeedback)|Ändert den Cursor während eines Drag-and-Drop-Vorgangs.|
|[ColeDropSource::OnBeginDrag](#onbegindrag)|Behandelt die Mausaufnahme während eines Drag-and-Drop-Vorgangs.|
|[COleDropSource::QueryContinueDrag](#querycontinuedrag)|Überprüft, ob das Ziehen fortgesetzt werden soll.|

## <a name="remarks"></a>Bemerkungen

Die [COleDropTarget-Klasse](../../mfc/reference/coledroptarget-class.md) verarbeitet den empfangenden Teil des Drag-and-Drop-Vorgangs. Das `COleDropSource` Objekt ist dafür verantwortlich, zu bestimmen, wann ein Ziehvorgang beginnt, Feedback während des Ziehvorgangs bereitzustellen und zu bestimmen, wann der Ziehvorgang endet.

Um ein `COleDropSource` Objekt zu verwenden, rufen Sie einfach den Konstruktor auf. Dies vereinfacht das Bestimmen, welche Ereignisse, z. B. ein Mausklick, einen Ziehvorgang mit [COleDataSource::DoDragDrop](../../mfc/reference/coledatasource-class.md#dodragdrop), [COleClientItem::DoDragDrop](../../mfc/reference/coleclientitem-class.md#dodragdrop)oder [COleServerItem::DoDragDrop-Funktion](../../mfc/reference/coleserveritem-class.md#dodragdrop) starten. Diese Funktionen erstellen `COleDropSource` ein Objekt für Sie. Sie können das Standardverhalten der `COleDropSource` überschreibbaren Funktionen ändern. Diese Memberfunktionen werden zu den entsprechenden Zeiten vom Framework aufgerufen.

Weitere Informationen zu Drag-and-Drop-Vorgängen mit OLE finden Sie im Artikel [OLE drag and drop](../../mfc/drag-and-drop-ole.md).

Weitere Informationen finden Sie unter [IDropSource](/windows/win32/api/oleidl/nn-oleidl-idropsource) im Windows SDK.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropSource`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxole.h

## <a name="coledropsourcecoledropsource"></a><a name="coledropsource"></a>COleDropSource::COleDropSource

Erstellt ein `COleDropSource`-Objekt.

```
COleDropSource();
```

## <a name="coledropsourcegivefeedback"></a><a name="givefeedback"></a>COleDropSource::GiveFeedback

Wird vom Framework nach dem Aufruf von [COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover) oder [COleDropTarget::DragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter)aufgerufen.

```
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```

### <a name="parameters"></a>Parameter

*dropEffect*<br/>
Der Effekt, den Sie dem Benutzer anzeigen möchten, der in der Regel angibt, was passieren würde, wenn an dieser Stelle ein Drop mit den ausgewählten Daten auftritt. In der Regel ist dies der Wert, der vom letzten Aufruf von [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter) oder [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover)zurückgegeben wird. Es kann einer oder mehrere der folgenden sein:

- DROPEFFECT_NONE Ein Tropfen wäre nicht erlaubt.

- DROPEFFECT_COPY ein Kopiervorgang durchgeführt.

- DROPEFFECT_MOVE Ein Umzugsvorgang wird ausgeführt.

- DROPEFFECT_LINK Eine Verknüpfung von den gelöschten Daten zu den ursprünglichen Daten hergestellt werden würde.

- DROPEFFECT_SCROLL Ein Ziehbildvorgang wird im Begriff sein oder im Ziel auftreten.

### <a name="return-value"></a>Rückgabewert

Gibt DRAGDROP_S_USEDEFAULTCURSORS zurück, wenn das Ziehen ausgeführt wird, NOERROR, wenn dies nicht der Fall ist.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um dem Benutzer Feedback darüber zu geben, was passieren würde, wenn zu diesem Zeitpunkt ein Drop eintritt. Die Standardimplementierung verwendet die OLE-Standardcursor. Weitere Informationen zu Drag-and-Drop-Vorgängen mit OLE finden Sie im Artikel [OLE drag and drop](../../mfc/drag-and-drop-ole.md).

Weitere Informationen finden Sie unter [IDropSource::GiveFeedback](/windows/win32/api/oleidl/nf-oleidl-idropsource-givefeedback), [IDropTarget::DragOver](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover)und [IDropTarget::DragEnter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) im Windows SDK.

## <a name="coledropsourceonbegindrag"></a><a name="onbegindrag"></a>ColeDropSource::OnBeginDrag

Wird vom Framework aufgerufen, wenn ein Ereignis auftritt, das einen Ziehvorgang starten könnte, z. B. durch Drücken der linken Maustaste.

```
virtual BOOL OnBeginDrag(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Zeigt auf das Fenster, das die ausgewählten Daten enthält.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Ziehen zulässig ist, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, wenn Sie die Art und Weise ändern möchten, wie der Ziehvorgang gestartet wird. Die Standardimplementierung erfasst die Maus und bleibt im Drag-Modus, bis der Benutzer auf die linke oder rechte Maustaste klickt oder ESC trifft.

## <a name="coledropsourcequerycontinuedrag"></a><a name="querycontinuedrag"></a>COleDropSource::QueryContinueDrag

Nachdem das Ziehen begonnen wurde, wird diese Funktion vom Framework wiederholt aufgerufen, bis der Ziehvorgang abgebrochen oder abgeschlossen wird.

```
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed,
    DWORD dwKeyState);
```

### <a name="parameters"></a>Parameter

*bEscapePressed*<br/>
gibt an, ob der ESC-Schlüssel `COleDropSource::QueryContinueDrag`seit dem letzten Aufruf an gedrückt wurde.

*dwKeyState*<br/>
Enthält den Status der Modifikatortasten auf der Tastatur. Dies ist eine Kombination aus einer beliebigen Anzahl von folgenden: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON und MK_RBUTTON.

### <a name="return-value"></a>Rückgabewert

DRAGDROP_S_CANCEL, wenn die ESC-Taste oder die rechte Taste gedrückt wird oder die linke Taste ausgelöst wird, bevor das Ziehen beginnt. DRAGDROP_S_DROP, wenn ein Ablagevorgang auftreten soll. Sonst S_OK.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, wenn Sie den Punkt ändern möchten, an dem das Ziehen abgebrochen wird oder ein Drop auftritt.

Die Standardimplementierung initiiert das Ablegen oder bricht den Drag wie folgt ab. Es bricht einen Ziehvorgang ab, wenn die ESC-Taste oder die rechte Maustaste gedrückt wird. Es initiiert einen Drop-Vorgang, wenn die linke Maustaste nach dem Ziehen ausgelöst wird. Andernfalls gibt sie S_OK zurück und führt keine weiteren Vorgänge aus.

Da diese Funktion häufig aufgerufen wird, sollte sie so weit wie möglich optimiert werden.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
