---
title: COleDropTarget-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleDropTarget
- AFXOLE/COleDropTarget
- AFXOLE/COleDropTarget::COleDropTarget
- AFXOLE/COleDropTarget::OnDragEnter
- AFXOLE/COleDropTarget::OnDragLeave
- AFXOLE/COleDropTarget::OnDragOver
- AFXOLE/COleDropTarget::OnDragScroll
- AFXOLE/COleDropTarget::OnDrop
- AFXOLE/COleDropTarget::OnDropEx
- AFXOLE/COleDropTarget::Register
- AFXOLE/COleDropTarget::Revoke
helpviewer_keywords:
- COleDropTarget [MFC], COleDropTarget
- COleDropTarget [MFC], OnDragEnter
- COleDropTarget [MFC], OnDragLeave
- COleDropTarget [MFC], OnDragOver
- COleDropTarget [MFC], OnDragScroll
- COleDropTarget [MFC], OnDrop
- COleDropTarget [MFC], OnDropEx
- COleDropTarget [MFC], Register
- COleDropTarget [MFC], Revoke
ms.assetid: a58c9a48-6a93-4357-b078-4594df258311
ms.openlocfilehash: 01eb277da029d06ee44d8e048cf3244f4371a9ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374990"
---
# <a name="coledroptarget-class"></a>COleDropTarget-Klasse

Stellt den Kommunikationsmechanismus zwischen einem Fenster und den OLE-Bibliotheken bereit.

## <a name="syntax"></a>Syntax

```
class COleDropTarget : public CCmdTarget
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDropTarget::COleDropTarget](#coledroptarget)|Erstellt ein `COleDropTarget`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ColeDropTarget::OnDragEnter](#ondragenter)|Wird aufgerufen, wenn der Cursor zum ersten Mal in das Fenster eintritt.|
|[ColeDropTarget::OnDragLeave](#ondragleave)|Wird aufgerufen, wenn der Cursor aus dem Fenster gezogen wird.|
|[ColeDropTarget::OnDragover](#ondragover)|Wird wiederholt aufgerufen, wenn der Cursor über das Fenster gezogen wird.|
|[ColeDropTarget::OnDragScroll](#ondragscroll)|Wird aufgerufen, um zu bestimmen, ob der Cursor in den Bildlaufbereich des Fensters gezogen wird.|
|[COleDropTarget::OnDrop](#ondrop)|Wird aufgerufen, wenn Daten in das Fenster abgelegt werden, Standardhandler.|
|[COleDropTarget::OnDropEx](#ondropex)|Wird aufgerufen, wenn Daten in das Fenster, den ersten Handler, abgelegt werden.|
|[COleDropTarget::Registrieren](#register)|Registriert das Fenster als gültiges Ablageziel.|
|[COleDropTarget::Widerrufen](#revoke)|Bewirkt, dass das Fenster kein gültiges Ablageziel mehr ist.|

## <a name="remarks"></a>Bemerkungen

Das Erstellen eines Objekts dieser Klasse ermöglicht es einem Fenster, Daten über den OLE-Drag-and-Drop-Mechanismus zu akzeptieren.

Um ein Fenster zum Akzeptieren von Drop-Befehlen `COleDropTarget` zu erhalten, sollten Sie zuerst ein Objekt `CWnd` der Klasse erstellen und dann die [Registerfunktion](#register) mit einem Zeiger auf das gewünschte Objekt als einzigen Parameter aufrufen.

Weitere Informationen zu Drag-and-Drop-Vorgängen mit OLE finden Sie im Artikel [OLE drag and drop](../../mfc/drag-and-drop-ole.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropTarget`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxole.h

## <a name="coledroptargetcoledroptarget"></a><a name="coledroptarget"></a>COleDropTarget::COleDropTarget

Erstellt ein Objekt `COleDropTarget`der Klasse .

```
COleDropTarget();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie [Register](#register) auf, um dieses Objekt einem Fenster zuzuordnen.

## <a name="coledroptargetondragenter"></a><a name="ondragenter"></a>ColeDropTarget::OnDragEnter

Wird vom Framework aufgerufen, wenn der Cursor zum ersten Mal in das Fenster gezogen wird.

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Zeigt auf das Fenster, in das der Cursor einschlägt.

*pDataObject*<br/>
Zeigt auf das Datenobjekt, das die Daten enthält, die gelöscht werden können.

*dwKeyState*<br/>
Enthält den Status der Modifikatorschlüssel. Dies ist eine Kombination aus einer beliebigen Anzahl von folgenden: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON und MK_RBUTTON.

*Punkt*<br/>
Enthält die aktuelle Position des Cursors in Clientkoordinaten.

### <a name="return-value"></a>Rückgabewert

Der Effekt, der sich ergeben würde, wenn ein Drop an der durch *Punkt*angegebenen Position versucht würde. Es kann einer oder mehrere der folgenden sein:

- DROPEFFECT_NONE Ein Tropfen wäre nicht erlaubt.

- DROPEFFECT_COPY ein Kopiervorgang durchgeführt.

- DROPEFFECT_MOVE Ein Umzugsvorgang wird ausgeführt.

- DROPEFFECT_LINK Eine Verknüpfung von den gelöschten Daten zu den ursprünglichen Daten hergestellt werden würde.

- DROPEFFECT_SCROLL Ein Ziehbildvorgang wird im Begriff sein oder im Ziel auftreten.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, damit Drop-Operationen im Fenster auftreten können. Die Standardimplementierung ruft [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter)auf, wodurch standardmäßig DROPEFFECT_NONE zurückgegeben wird.

Weitere Informationen finden Sie unter [IDropTarget::DragEnter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) im Windows SDK.

## <a name="coledroptargetondragleave"></a><a name="ondragleave"></a>ColeDropTarget::OnDragLeave

Wird vom Framework aufgerufen, wenn der Cursor das Fenster verlässt, während ein Ziehvorgang wirksam ist.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Zeigt auf das Fenster, das der Cursor verlässt.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, wenn Sie ein spezielles Verhalten wünschen, wenn der Ziehvorgang das angegebene Fenster verlässt. Die Standardimplementierung dieser Funktion ruft [CView::OnDragLeave](../../mfc/reference/cview-class.md#ondragleave)auf.

Weitere Informationen finden Sie unter [IDropTarget::DragLeave](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragleave) im Windows SDK.

## <a name="coledroptargetondragover"></a><a name="ondragover"></a>ColeDropTarget::OnDragover

Wird vom Framework aufgerufen, wenn der Cursor über das Fenster gezogen wird.

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Zeigt auf das Fenster, über dem der Cursor ist.

*pDataObject*<br/>
Zeigt auf das Datenobjekt, das die abzulegenden Daten enthält.

*dwKeyState*<br/>
Enthält den Status der Modifikatorschlüssel. Dies ist eine Kombination aus einer beliebigen Anzahl von folgenden: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON und MK_RBUTTON.

*Punkt*<br/>
Enthält die aktuelle Position des Cursors in Clientkoordinaten.

### <a name="return-value"></a>Rückgabewert

Der Effekt, der sich ergeben würde, wenn ein Drop an der durch *Punkt*angegebenen Position versucht würde. Es kann einer oder mehrere der folgenden sein:

- DROPEFFECT_NONE Ein Tropfen wäre nicht erlaubt.

- DROPEFFECT_COPY ein Kopiervorgang durchgeführt.

- DROPEFFECT_MOVE Ein Umzugsvorgang wird ausgeführt.

- DROPEFFECT_LINK Eine Verknüpfung von den gelöschten Daten zu den ursprünglichen Daten hergestellt werden würde.

- DROPEFFECT_SCROLL Gibt an, dass ein Ziehbildvorgang im Ziel ausgeführt wird oder stattfindet.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte überschrieben werden, damit Drop-Vorgänge im Fenster ausgeführt werden können. Die Standardimplementierung dieser Funktion ruft [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover)auf, das standardmäßig DROPEFFECT_NONE zurückgibt. Da diese Funktion während eines Drag-and-Drop-Vorgangs häufig aufgerufen wird, sollte sie so weit wie möglich optimiert werden.

Weitere Informationen finden Sie unter [IDropTarget::DragOver](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]

## <a name="coledroptargetondragscroll"></a><a name="ondragscroll"></a>ColeDropTarget::OnDragScroll

Wird vom Framework aufgerufen, bevor [OnDragEnter](#ondragenter) oder [OnDragOver](#ondragover) aufgerufen wird, um zu bestimmen, ob sich der *Punkt* im Bildlaufbereich befindet.

```
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Zeigt auf das Fenster, in dem der Cursor gerade vorbei ist.

*dwKeyState*<br/>
Enthält den Status der Modifikatorschlüssel. Dies ist eine Kombination aus einer beliebigen Anzahl von folgenden: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON und MK_RBUTTON.

*Punkt*<br/>
Enthält die Position des Cursors in Pixel relativ zum Bildschirm.

### <a name="return-value"></a>Rückgabewert

Der Effekt, der sich ergeben würde, wenn ein Drop an der durch *Punkt*angegebenen Position versucht würde. Es kann einer oder mehrere der folgenden sein:

- DROPEFFECT_NONE Ein Tropfen wäre nicht erlaubt.

- DROPEFFECT_COPY ein Kopiervorgang durchgeführt.

- DROPEFFECT_MOVE Ein Umzugsvorgang wird ausgeführt.

- DROPEFFECT_LINK Eine Verknüpfung von den gelöschten Daten zu den ursprünglichen Daten hergestellt werden würde.

- DROPEFFECT_SCROLL Gibt an, dass ein Ziehbildvorgang im Ziel ausgeführt wird oder stattfindet.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, wenn Sie ein spezielles Verhalten für dieses Ereignis bereitstellen möchten. Die Standardimplementierung dieser Funktion ruft [CView::OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll)auf, das DROPEFFECT_NONE zurückgibt und das Fenster scrollt, wenn der Cursor in den Standard-Bildlaufbereich innerhalb des Rahmens des Fensters gezogen wird.

## <a name="coledroptargetondrop"></a><a name="ondrop"></a>COleDropTarget::OnDrop

Wird vom Framework aufgerufen, wenn ein Ablagevorgang ausgeführt werden soll.

```
virtual BOOL OnDrop(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Zeigt auf das Fenster, in dem der Cursor gerade vorbei ist.

*pDataObject*<br/>
Zeigt auf das Datenobjekt, das die abzulegenden Daten enthält.

*dropEffect*<br/>
Der Effekt, den der Benutzer für den Ablagevorgang ausgewählt hat. Es kann einer oder mehrere der folgenden sein:

- DROPEFFECT_COPY ein Kopiervorgang durchgeführt.

- DROPEFFECT_MOVE Ein Umzugsvorgang wird ausgeführt.

- DROPEFFECT_LINK Eine Verknüpfung von den gelöschten Daten zu den ursprünglichen Daten hergestellt werden würde.

*Punkt*<br/>
Enthält die Position des Cursors in Pixel relativ zum Bildschirm.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Drop erfolgreich ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft zuerst [OnDropEx](#ondropex)auf. Wenn `OnDropEx` die Funktion den Drop nicht verarbeitet, ruft `OnDrop`das Framework diese Memberfunktion auf. In der Regel überschreibt die Anwendung [OnDropEx](../../mfc/reference/cview-class.md#ondropex) in der Ansichtsklasse, um das Ziehen und Ablegen der rechten Maustaste zu verarbeiten. In der Regel wird die Ansichtsklasse [OnDrop](../../mfc/reference/cview-class.md#ondrop) verwendet, um einfaches Ziehen und Ablegen zu handhaben.

Die Standardimplementierung `COleDropTarget::OnDrop` von Aufrufen [CView::OnDrop](../../mfc/reference/cview-class.md#ondrop), die einfach FALSE standardmäßig zurückgibt.

Weitere Informationen finden Sie unter [IDropTarget::Drop](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) im Windows SDK.

## <a name="coledroptargetondropex"></a><a name="ondropex"></a>COleDropTarget::OnDropEx

Wird vom Framework aufgerufen, wenn ein Ablagevorgang ausgeführt werden soll.

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Zeigt auf das Fenster, in dem der Cursor gerade vorbei ist.

*pDataObject*<br/>
Zeigt auf das Datenobjekt, das die abzulegenden Daten enthält.

*dropDefault*<br/>
Der Effekt, den der Benutzer für den Standardablagevorgang basierend auf dem aktuellen Schlüsselstatus ausgewählt hat. Es kann DROPEFFECT_NONE sein. Drop-Effekte werden im Abschnitt "Bemerkungen" erläutert.

*dropList*<br/>
Eine Liste der Drop-Effekte, die von der Ablagequelle unterstützt werden. Dropeffektwerte können mit dem bitweisen ODER -**&#124;**) Vorgang kombiniert werden. Drop-Effekte werden im Abschnitt "Bemerkungen" erläutert.

*Punkt*<br/>
Enthält die Position des Cursors in Pixel relativ zum Bildschirm.

### <a name="return-value"></a>Rückgabewert

Der Dropeffekt, der sich aus dem Drop-Versuch an der durch *Punkt*angegebenen Position ergab. Drop-Effekte werden im Abschnitt "Bemerkungen" erläutert.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Funktion zuerst auf. Wenn der Drop nicht verarbeitet wird, ruft das Framework [OnDrop](#ondrop)auf. In der Regel überschreiben Sie [OnDropEx](../../mfc/reference/cview-class.md#ondropex) in der Ansichtsklasse, um das Ziehen und Ablegen der rechten Maustaste zu unterstützen. In der Regel wird die Ansichtsklasse [OnDrop](../../mfc/reference/cview-class.md#ondrop) verwendet, um den Fall der Unterstützung für einfaches Ziehen und Ablegen zu behandeln.

Die Standardimplementierung `COleDropTarget::OnDropEx` von Aufrufen [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex). Standardmäßig gibt [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex) einfach einen Dummy-Wert zurück, um anzugeben, dass die [OnDrop-Memberfunktion](#ondrop) aufgerufen werden soll.

Dropeffekte beschreiben die Aktion, die einem Ablagevorgang zugeordnet ist. Sehen Sie sich die folgende Liste der Drop-Effekte an:

- DROPEFFECT_NONE Ein Tropfen wäre nicht erlaubt.

- DROPEFFECT_COPY ein Kopiervorgang durchgeführt.

- DROPEFFECT_MOVE Ein Umzugsvorgang wird ausgeführt.

- DROPEFFECT_LINK Eine Verknüpfung von den gelöschten Daten zu den ursprünglichen Daten hergestellt werden würde.

- DROPEFFECT_SCROLL Gibt an, dass ein Ziehbildvorgang im Ziel ausgeführt wird oder stattfindet.

Weitere Informationen finden Sie unter [IDropTarget::Drop](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) im Windows SDK.

## <a name="coledroptargetregister"></a><a name="register"></a>COleDropTarget::Registrieren

Rufen Sie diese Funktion auf, um Ihr Fenster bei den OLE-DLLs als gültiges Ablageziel zu registrieren.

```
BOOL Register(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Zeigt auf das Fenster, das als Ablageziel registriert werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Registrierung erfolgreich ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion muss aufgerufen werden, damit Drop-Operationen akzeptiert werden.

Weitere Informationen finden Sie unter [RegisterDragDrop](/windows/win32/api/ole2/nf-ole2-registerdragdrop) im Windows SDK.

## <a name="coledroptargetrevoke"></a><a name="revoke"></a>COleDropTarget::Widerrufen

Rufen Sie diese Funktion auf, bevor Sie ein Fenster zerstören, das als Drop-Ziel durch einen Aufruf von [Register](#register) registriert wurde, um sie aus der Liste der Drop-Ziele zu entfernen.

```
virtual void Revoke();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird automatisch vom [OnDestroy-Handler](../../mfc/reference/cwnd-class.md#ondestroy) für das registrierte Fenster aufgerufen, sodass es in der Regel nicht erforderlich ist, diese Funktion explizit aufzurufen.

Weitere Informationen finden Sie unter [RevokeDragDrop](/windows/win32/api/ole2/nf-ole2-revokedragdrop) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleDropSource-Klasse](../../mfc/reference/coledropsource-class.md)
