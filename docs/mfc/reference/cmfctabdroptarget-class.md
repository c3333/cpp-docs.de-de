---
title: CMFCTabDropTarget-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragEnter
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragLeave
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragOver
- AFXBASETABCTRL/CMFCTabDropTarget::OnDropEx
- AFXBASETABCTRL/CMFCTabDropTarget::Register
helpviewer_keywords:
- CMFCTabDropTarget [MFC], OnDragEnter
- CMFCTabDropTarget [MFC], OnDragLeave
- CMFCTabDropTarget [MFC], OnDragOver
- CMFCTabDropTarget [MFC], OnDropEx
- CMFCTabDropTarget [MFC], Register
ms.assetid: 9777b7b6-10da-4c4b-b1d1-7ea795b0f1cb
ms.openlocfilehash: 83432fdb90fe28214fb1faaf843556deb2f44750
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367353"
---
# <a name="cmfctabdroptarget-class"></a>CMFCTabDropTarget-Klasse

Stellt den Kommunikationsmechanismus zwischen einem Registerkartensteuerelement und den OLE-Bibliotheken bereit.

## <a name="syntax"></a>Syntax

```
class CMFCTabDropTarget : public COleDropTarget
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|||
|-|-|
|Name|BESCHREIBUNG|
|`CMFCTabDropTarget::CMFCTabDropTarget`|Der Standardkonstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|||
|-|-|
|Name|BESCHREIBUNG|
|[CMFCTabDropTarget::OnDragEnter](#ondragenter)|Wird vom Framework aufgerufen, wenn der Benutzer ein Objekt in ein Registerkartenfenster zieht. (Überschreibt [COleDropTarget::OnDragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).)|
|[CMFCTabDropTarget::OnDragLeave](#ondragleave)|Wird vom Framework aufgerufen, wenn der Benutzer ein Objekt außerhalb des Registerkartenfensters mit Fokus zieht. (Überschreibt [COleDropTarget::OnDragLeave](../../mfc/reference/coledroptarget-class.md#ondragleave).)|
|[CMFCTabDropTarget::OnDragOver](#ondragover)|Wird vom Framework aufgerufen, wenn der Benutzer ein Objekt auf das Registerkartenfenster mit Fokus zieht. (Überschreibt [COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover).)|
|[CMFCTabDropTarget::OnDropEx](#ondropex)|Wird vom Framework aufgerufen, wenn der Benutzer die Maustaste am Ende eines Ziehvorgangs loslässt. (Überschreibt [COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).)|
|[CMFCTabDropTarget::Registrieren](#register)|Registriert das Steuerelement als ein Steuerelement, das das Ziel eines OLE-Drag-and-Drop-Vorgangs sein kann.|

### <a name="remarks"></a>Bemerkungen

Diese Klasse bietet Drag-and-Drop-Unterstützung für die `CMFCBaseTabCtrl` Klasse. Wenn Ihre Anwendung die OLE-Bibliotheken mithilfe der Funktion `CMFCBaseTabCtrl` [AfxOleInit](ole-initialization.md#afxoleinit) initialisiert, registrieren sich Objekte selbst für Drag-and-Drop-Vorgänge.

Die `CMFCTabDropTarget` Klasse erweitert ihre Basisklasse, indem sie die Registerkarte unter dem Cursor macht, wenn ein Ziehvorgang ausgeführt wird. Weitere Informationen zu Drag-and-Drop-Vorgängen finden Sie unter [OLE Drag & Drop](../../mfc/drag-and-drop-ole.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht das Erstellen eines `CMFCTabDropTarget`-Objekts und die Verwendung der `Register`-Methode.

[!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/cpp/cmfctabdroptarget-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleDropTarget](../../mfc/reference/coledroptarget-class.md)

[CMFCTabDropTarget](../../mfc/reference/cmfctabdroptarget-class.md)

## <a name="requirements"></a>Anforderungen

**Header:** afxbasetabctrl.h

## <a name="cmfctabdroptargetondragenter"></a><a name="ondragenter"></a>CMFCTabDropTarget::OnDragEnter

Wird vom Framework aufgerufen, wenn der Benutzer ein Objekt in ein Registerkartenfenster zieht.

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|Beschreibung|
|*pWnd*|[in] Nicht verwendet.|
|*pDataObject*|[in] Ein Zeiger auf das Objekt, das der Benutzer zieht.|
|*dwKeyState*|[in] Enthält den Status der Modifikatorschlüssel. Dies ist eine Kombination aus einer beliebigen Anzahl von folgenden: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON und MK_RBUTTON.|
|*Punkt*|[in] Die Position des Cursors in den Clientkoordinaten.|

### <a name="return-value"></a>Rückgabewert

Der Effekt, der entsteht, wenn der Abwurf an der durch *Punkt*angegebenen Position auftritt. Es kann einer oder mehrere der folgenden sein:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt DROPEFFECT_NONE zurück, wenn sich das Symbolleistenframework nicht im Anpassungsmodus befindet oder das Datenformat zwischen der Ablage nicht verfügbar ist. Andernfalls wird das Ergebnis `CMFCBaseTabCtrl::OnDragEnter` des Aufrufs mit den angegebenen Parametern zurückgegeben.

Weitere Informationen zum Anpassungsmodus finden Sie unter [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Weitere Informationen zu Clipboard-Datenformaten finden Sie unter [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

## <a name="cmfctabdroptargetondragleave"></a><a name="ondragleave"></a>CMFCTabDropTarget::OnDragLeave

Wird vom Framework aufgerufen, wenn der Benutzer ein Objekt außerhalb des Registerkartenfensters mit Fokus zieht.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|Beschreibung|
|*pWnd*|[in] Nicht verwendet.|

### <a name="remarks"></a>Bemerkungen

Diese Methode `CMFCBaseTabCtrl::OnDragLeave` ruft die Methode auf, um den Ziehvorgang auszuführen.

## <a name="cmfctabdroptargetondragover"></a><a name="ondragover"></a>CMFCTabDropTarget::OnDragOver

Wird vom Framework aufgerufen, wenn der Benutzer ein Objekt auf das Registerkartenfenster mit Fokus zieht.

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|Beschreibung|
|*pWnd*|[in] Nicht verwendet.|
|*pDataObject*|[in] Ein Zeiger auf das Objekt, das der Benutzer zieht.|
|*dwKeyState*|[in] Enthält den Status der Modifikatorschlüssel. Dies ist eine Kombination aus einer beliebigen Anzahl von folgenden: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON und MK_RBUTTON.|
|*Punkt*|[in] Die Position des Mauszeigers in Clientkoordinaten.|

### <a name="return-value"></a>Rückgabewert

Der Effekt, der entsteht, wenn der Abwurf an der durch *Punkt*angegebenen Position auftritt. Es kann einer oder mehrere der folgenden sein:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Bemerkungen

Diese Methode macht die Registerkarte, die sich unter dem Cursor befindet, wenn ein Ziehvorgang ausgeführt wird, aktiv. Es wird DROPEFFECT_NONE zurückgegeben, wenn sich das Symbolleistenframework nicht im Anpassungsmodus befindet oder das Datenformat zwischen der Ablage nicht verfügbar ist. Andernfalls wird das Ergebnis `CMFCBaseTabCtrl::OnDragOver` des Aufrufs mit den angegebenen Parametern zurückgegeben.

Weitere Informationen zum Anpassungsmodus finden Sie unter [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Weitere Informationen zu Clipboard-Datenformaten finden Sie unter [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

## <a name="cmfctabdroptargetondropex"></a><a name="ondropex"></a>CMFCTabDropTarget::OnDropEx

Wird vom Framework aufgerufen, wenn der Benutzer die Maustaste am Ende eines Ziehvorgangs loslässt.

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|BESCHREIBUNG|
|*pWnd*|[in] Nicht verwendet.|
|*pDataObject*|[in] Ein Zeiger auf das Objekt, das der Benutzer zieht.|
|*dropEffect*|[in] Der Standard-Ablagevorgang.|
|*dropList*|[in] Nicht verwendet.|
|*Punkt*|[in] Die Position des Mauszeigers in Clientkoordinaten.|

### <a name="return-value"></a>Rückgabewert

Der resultierende Drop-Effekt. Es kann einer oder mehrere der folgenden sein:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Bemerkungen

Diese Methode `CMFCBaseTabCtrl::OnDrop` wird aufruft, wenn sich das Symbolleistenframework im Anpassungsmodus befindet und das Datenformat zwischen der Ablage verfügbar ist. Wenn der `CMFCBaseTabCtrl::OnDrop` Aufruf von einen Wert ungleich Null zurückgegeben wird, gibt diese Methode den von *dropEffect*angegebenen Standard-Dropeffekt zurück. Andernfalls gibt diese Methode DROPEFFECT_NONE zurück. Weitere Informationen zu Drop-Effekten finden Sie unter [COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).

Weitere Informationen zum Anpassungsmodus finden Sie unter [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Weitere Informationen zu Clipboard-Datenformaten finden Sie unter [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

## <a name="cmfctabdroptargetregister"></a><a name="register"></a>CMFCTabDropTarget::Registrieren

Registriert das Steuerelement als ein Steuerelement, das das Ziel eines OLE-Drag-and-Drop-Vorgangs sein kann.

```
BOOL Register(CMFCBaseTabCtrl *pOwner);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|BESCHREIBUNG|
|*pOwner*|[in] Das Registerkartensteuerelement, das als Ablageziel registriert werden soll.|

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Registrierung erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft [COleDropTarget::Register](../../mfc/reference/coledroptarget-class.md#register) auf, um das Steuerelement für Drag-and-Drop-Vorgänge zu registrieren.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[Drag &amp; Drop (OLE)](../../mfc/drag-and-drop-ole.md)
