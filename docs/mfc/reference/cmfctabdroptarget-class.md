---
title: Cmfctabdroptarget-Klasse
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
ms.openlocfilehash: 9160cfd847977f98ac22eecd72632822c751a3aa
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834231"
---
# <a name="cmfctabdroptarget-class"></a>Cmfctabdroptarget-Klasse

Stellt den Kommunikationsmechanismus zwischen einem Registerkarten-Steuerelement und den OLE-Bibliotheken bereit.

## <a name="syntax"></a>Syntax

```
class CMFCTabDropTarget : public COleDropTarget
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|-|-|
|`CMFCTabDropTarget::CMFCTabDropTarget`|Standardkonstruktor|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|-|-|
|[Cmfctabdroptarget:: OnDragEnter](#ondragenter)|Wird von Framework aufgerufen, wenn der Benutzer ein Objekt in ein Registerkarten Fenster zieht. (Überschreibt [COleDropTarget:: OnDragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).)|
|[Cmfctabdroptarget:: OnDragLeave](#ondragleave)|Wird von Framework aufgerufen, wenn der Benutzer ein Objekt außerhalb des Registerkarten Fensters zieht, das den Fokus besitzt. (Überschreibt [COleDropTarget:: OnDragLeave](../../mfc/reference/coledroptarget-class.md#ondragleave).)|
|[Cmfctabdroptarget:: OnDragOver](#ondragover)|Wird von Framework aufgerufen, wenn der Benutzer ein Objekt auf das Registerkarten Fenster zieht, das den Fokus besitzt. (Überschreibt [COleDropTarget:: OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover).)|
|[Cmfctabdroptarget:: ondropex](#ondropex)|Wird von Framework aufgerufen, wenn der Benutzer die Maustaste am Ende eines Zieh Vorgangs loslässt. (Überschreibt [COleDropTarget:: ondropex](../../mfc/reference/coledroptarget-class.md#ondropex).)|
|[Cmfctabdroptarget:: Register](#register)|Registriert das-Steuerelement als das Ziel eines OLE-Drag & Drop-Vorgangs.|

### <a name="remarks"></a>Bemerkungen

Diese Klasse bietet Drag & Drop-Unterstützung für die- `CMFCBaseTabCtrl` Klasse. Wenn Ihre Anwendung die OLE-Bibliotheken mithilfe der [AfxOLEInit](ole-initialization.md#afxoleinit) -Funktion initialisiert, `CMFCBaseTabCtrl` registrieren sich Objekte selbst für Drag & Drop-Vorgänge.

Die- `CMFCTabDropTarget` Klasse erweitert Ihre Basisklasse, indem die Registerkarte, die sich unter dem Cursor befindet, beim aktiven Drag-Vorgang aktiviert wird. Weitere Informationen zu Drag & amp; Drop-Vorgängen finden Sie unter [OLE Drag & Drop](../../mfc/drag-and-drop-ole.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht das Erstellen eines `CMFCTabDropTarget`-Objekts und die Verwendung der `Register`-Methode.

[!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/cpp/cmfctabdroptarget-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleDropTarget](../../mfc/reference/coledroptarget-class.md)

[Cmfctabdroptarget](../../mfc/reference/cmfctabdroptarget-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxbasetabctrl.h

## <a name="cmfctabdroptargetondragenter"></a><a name="ondragenter"></a> Cmfctabdroptarget:: OnDragEnter

Wird von Framework aufgerufen, wenn der Benutzer ein Objekt in ein Registerkarten Fenster zieht.

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parameter

*folgenden*\
[in] Nicht verwendet.

*pDataObject*\
in Ein Zeiger auf das Objekt, das vom Benutzer gezogen wird.

*dwkeystate*\
in Enthält den Zustand der Modifizierertasten. Dies ist eine Kombination aus einer beliebigen Anzahl von folgenden: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON und MK_RBUTTON.

*Punkt*\
in Die Position des Cursors in Client Koordinaten.

### <a name="return-value"></a>Rückgabewert

Die Auswirkung, die ergibt, wenn der Ablage Vorgang an der durch *Punkt*angegebenen Position auftritt. Dabei kann es sich um eine oder mehrere der folgenden handeln:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt DROPEFFECT_NONE zurück, wenn sich das Symbolleisten Framework nicht im Anpassungsmodus befindet oder wenn das Datenformat der Zwischenablage nicht verfügbar ist. Andernfalls wird das Ergebnis zurückgegeben, das `CMFCBaseTabCtrl::OnDragEnter` mit den bereitgestellten Parametern aufgerufen wird.

Weitere Informationen zum Anpassungsmodus finden Sie unter [cmfctoolbar:: iscustomizemode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Weitere Informationen zu den Datenformaten der Zwischenablage finden Sie unter [COleDataObject:: IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

## <a name="cmfctabdroptargetondragleave"></a><a name="ondragleave"></a> Cmfctabdroptarget:: OnDragLeave

Wird von Framework aufgerufen, wenn der Benutzer ein Objekt außerhalb des Registerkarten Fensters zieht, das den Fokus besitzt.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*folgenden*\
[in] Nicht verwendet.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft die- `CMFCBaseTabCtrl::OnDragLeave` Methode auf, um den Zieh Vorgang auszuführen.

## <a name="cmfctabdroptargetondragover"></a><a name="ondragover"></a> Cmfctabdroptarget:: OnDragOver

Wird von Framework aufgerufen, wenn der Benutzer ein Objekt auf das Registerkarten Fenster zieht, das den Fokus besitzt.

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parameter

*folgenden*\
[in] Nicht verwendet.

*pDataObject*\
in Ein Zeiger auf das Objekt, das vom Benutzer gezogen wird.

*dwkeystate*\
in Enthält den Zustand der Modifizierertasten. Dies ist eine Kombination aus einer beliebigen Anzahl von folgenden: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON und MK_RBUTTON.

*Punkt*\
in Die Position des Mauszeigers in Client Koordinaten.

### <a name="return-value"></a>Rückgabewert

Die Auswirkung, die ergibt, wenn der Ablage Vorgang an der durch *Punkt*angegebenen Position auftritt. Dabei kann es sich um eine oder mehrere der folgenden handeln:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Bemerkungen

Diese Methode macht die Registerkarte, die sich unter dem Cursor befindet, wenn ein Zieh Vorgang aktiv ist. Sie gibt DROPEFFECT_NONE zurück, wenn sich das Symbolleisten Framework nicht im Anpassungsmodus befindet oder wenn das Datenformat der Zwischenablage nicht verfügbar ist. Andernfalls wird das Ergebnis zurückgegeben, das `CMFCBaseTabCtrl::OnDragOver` mit den bereitgestellten Parametern aufgerufen wird.

Weitere Informationen zum Anpassungsmodus finden Sie unter [cmfctoolbar:: iscustomizemode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Weitere Informationen zu den Datenformaten der Zwischenablage finden Sie unter [COleDataObject:: IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

## <a name="cmfctabdroptargetondropex"></a><a name="ondropex"></a> Cmfctabdroptarget:: ondropex

Wird von Framework aufgerufen, wenn der Benutzer die Maustaste am Ende eines Zieh Vorgangs loslässt.

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Parameter

*folgenden*\
[in] Nicht verwendet.

*pDataObject*\
in Ein Zeiger auf das Objekt, das vom Benutzer gezogen wird.

*dropffect*\
in Der Standard-Drop-Vorgang.

*droplist*\
[in] Nicht verwendet.

*Punkt*\
in Die Position des Mauszeigers in Client Koordinaten.

### <a name="return-value"></a>Rückgabewert

Der resultierende Ablage Effekt. Dabei kann es sich um eine oder mehrere der folgenden handeln:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft `CMFCBaseTabCtrl::OnDrop` auf, wenn sich das Symbolleisten Framework im Anpassungsmodus befindet und das Datenformat der Zwischenablage verfügbar ist. Wenn der- `CMFCBaseTabCtrl::OnDrop` Aufrufwert einen Wert ungleich 0 (null) zurückgibt, gibt diese Methode den von *dropeer ffect*angegebenen Standard Ablage Effekt zurück. Andernfalls gibt diese Methode DROPEFFECT_NONE zurück. Weitere Informationen zu Drop Effects finden Sie unter [COleDropTarget:: ondropex](../../mfc/reference/coledroptarget-class.md#ondropex).

Weitere Informationen zum Anpassungsmodus finden Sie unter [cmfctoolbar:: iscustomizemode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Weitere Informationen zu den Datenformaten der Zwischenablage finden Sie unter [COleDataObject:: IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

## <a name="cmfctabdroptargetregister"></a><a name="register"></a> Cmfctabdroptarget:: Register

Registriert das-Steuerelement als das Ziel eines OLE-Drag & Drop-Vorgangs.

```
BOOL Register(CMFCBaseTabCtrl *pOwner);
```

### <a name="parameters"></a>Parameter

*powner*\
in Das Registerkarten-Steuerelement, das als Ablage Ziel registriert werden soll.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Registrierung erfolgreich war. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft [COleDropTarget:: Register](../../mfc/reference/coledroptarget-class.md#register) auf, um das Steuerelement für Drag & Drop-Vorgänge zu registrieren.

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[Drag &amp; Drop (OLE)](../../mfc/drag-and-drop-ole.md)
