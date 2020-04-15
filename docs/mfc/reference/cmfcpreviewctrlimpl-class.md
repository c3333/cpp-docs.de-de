---
title: CMFCPreviewCtrlImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl::Create
- AFXWIN/CMFCPreviewCtrlImpl::Destroy
- AFXWIN/CMFCPreviewCtrlImpl::Focus
- AFXWIN/CMFCPreviewCtrlImpl::GetDocument
- AFXWIN/CMFCPreviewCtrlImpl::Redraw
- AFXWIN/CMFCPreviewCtrlImpl::SetDocument
- AFXWIN/CMFCPreviewCtrlImpl::SetHost
- AFXWIN/CMFCPreviewCtrlImpl::SetPreviewVisuals
- AFXWIN/CMFCPreviewCtrlImpl::SetRect
- AFXWIN/CMFCPreviewCtrlImpl::DoPaint
- AFXWIN/CMFCPreviewCtrlImpl::m_clrBackColor
- AFXWIN/CMFCPreviewCtrlImpl::m_clrTextColor
- AFXWIN/CMFCPreviewCtrlImpl::m_font
- AFXWIN/CMFCPreviewCtrlImpl::m_pDocument
helpviewer_keywords:
- CMFCPreviewCtrlImpl [MFC], CMFCPreviewCtrlImpl
- CMFCPreviewCtrlImpl [MFC], Create
- CMFCPreviewCtrlImpl [MFC], Destroy
- CMFCPreviewCtrlImpl [MFC], Focus
- CMFCPreviewCtrlImpl [MFC], GetDocument
- CMFCPreviewCtrlImpl [MFC], Redraw
- CMFCPreviewCtrlImpl [MFC], SetDocument
- CMFCPreviewCtrlImpl [MFC], SetHost
- CMFCPreviewCtrlImpl [MFC], SetPreviewVisuals
- CMFCPreviewCtrlImpl [MFC], SetRect
- CMFCPreviewCtrlImpl [MFC], DoPaint
- CMFCPreviewCtrlImpl [MFC], m_clrBackColor
- CMFCPreviewCtrlImpl [MFC], m_clrTextColor
- CMFCPreviewCtrlImpl [MFC], m_font
- CMFCPreviewCtrlImpl [MFC], m_pDocument
ms.assetid: 06257fa0-54c9-478d-9d68-c9698c3f93ed
ms.openlocfilehash: 060e601901fa5725d7ca62f244f66784af3dc11d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375337"
---
# <a name="cmfcpreviewctrlimpl-class"></a>CMFCPreviewCtrlImpl-Klasse

Diese Klasse implementiert ein Fenster, das in einem Hostfenster platziert wird, das von der Shell für Rich Preview bereitgestellt wird.

## <a name="syntax"></a>Syntax

```
class CMFCPreviewCtrlImpl : public CWnd;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::'CMFCPreviewCtrlImpl](#dtor)|Zerstört ein Vorschausteuerelementobjekt.|
|[CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl](#cmfcpreviewctrlimpl)|Erstellt ein Vorschausteuerelementobjekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::Erstellen](#create)|Ist überladen. Wird von einem Rich Preview-Handler aufgerufen, um das Windows-Fenster zu erstellen.|
|[CMFCPreviewCtrlImpl::Destroy](#destroy)|Wird von einem Rich Preview-Handler aufgerufen, wenn dieses Steuerelement zerstört werden muss.|
|[CMFCPreviewCtrlImpl::Fokus](#focus)|Legt den Eingabefokus auf dieses Steuerelement fest.|
|[CMFCPreviewCtrlImpl::GetDocument](#getdocument)|Gibt ein Dokument zurück, das mit diesem Vorschausteuerelement verbunden ist.|
|[CMFCPreviewCtrlImpl::Neuzeichnen](#redraw)|Weist dieses Steuerelement an, neu zu zeichnen.|
|[CMFCPreviewCtrlImpl::SetDocument](#setdocument)|Wird vom Vorschauhandler aufgerufen, um eine Beziehung zwischen der Dokumentimplementierung und dem Vorschausteuerelement zu erstellen.|
|[CMFCPreviewCtrlImpl::SetHost](#sethost)|Legt ein neues übergeordnetes Element für dieses Steuerelement fest.|
|[CMFCPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Wird von einem Rich Preview-Handler aufgerufen, wenn er visuelle Elemente mit umfangreichem Vorschauinhalt festlegen muss.|
|[CMFCPreviewCtrlImpl::SetRect](#setrect)|Legt ein neues umgrenzendes Rechteck für dieses Steuerelement fest.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::DoPaint](#dopaint)|Wird vom Framework aufgerufen, um die Vorschau zu rendern.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::m_clrBackColor](#m_clrbackcolor)|Hintergrundfarbe des Vorschaufensters.|
|[CMFCPreviewCtrlImpl::m_clrTextColor](#m_clrtextcolor)|Textfarbe des Vorschaufensters.|
|[CMFCPreviewCtrlImpl::m_font](#m_font)|Schriftart, die zum Anzeigen von Text im Vorschaufenster verwendet wird.|
|[CMFCPreviewCtrlImpl::m_pDocument](#m_pdocument)|Ein Zeiger auf ein Dokument, dessen Inhalt im Steuerelement in der Vorschau angezeigt wird.|

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCPreviewCtrlImpl](../../mfc/reference/cmfcpreviewctrlimpl-class.md)

## <a name="cmfcpreviewctrlimplcmfcpreviewctrlimpl"></a><a name="cmfcpreviewctrlimpl"></a>CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl

Erstellt ein Vorschausteuerelementobjekt.

### <a name="syntax"></a>Syntax

CMFCPreviewCtrlImpl();

## <a name="cmfcpreviewctrlimplcreate"></a><a name="create"></a>CMFCPreviewCtrlImpl::Erstellen

Ist überladen. Wird von einem Rich Preview-Handler aufgerufen, um das Windows-Fenster zu erstellen.

### <a name="syntax"></a>Syntax

```
virtual BOOL Create(
   HWND hWndParent,
   const RECT* prc
);
virtual BOOL Create(
   HWND hWndParent,
   const RECT* prc,
   CCreateContext* pContext
);
```

### <a name="parameters"></a>Parameter

*hWndEltern*<br/>
Ein Handle für das Hostfenster, das von der Shell für Rich Preview bereitgestellt wird.

*Vr china*<br/>
Gibt die Anfangsgröße und Position des Fensters an.

*pContext*<br/>
Ein Zeiger auf einen Erstellungskontext.

### <a name="return-value"></a>Rückgabewert

„True“, wenn die Erstellung erfolgreich war, andernfalls „false“.

## <a name="cmfcpreviewctrlimpldestroy"></a><a name="destroy"></a>CMFCPreviewCtrlImpl::Destroy

Wird von einem Rich Preview-Handler aufgerufen, wenn dieses Steuerelement zerstört werden muss.

### <a name="syntax"></a>Syntax

```
virtual void Destroy();
```

## <a name="cmfcpreviewctrlimpldopaint"></a><a name="dopaint"></a>CMFCPreviewCtrlImpl::DoPaint

Wird vom Framework aufgerufen, um die Vorschau zu rendern.

### <a name="syntax"></a>Syntax

```
virtual void DoPaint(
   CPaintDC* pDC
);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Ein Zeiger auf einen Gerätekontext zum Malen.

## <a name="cmfcpreviewctrlimplfocus"></a><a name="focus"></a>CMFCPreviewCtrlImpl::Fokus

Legt den Eingabefokus auf dieses Steuerelement fest.

### <a name="syntax"></a>Syntax

```
virtual void Focus();
```

## <a name="cmfcpreviewctrlimplgetdocument"></a><a name="getdocument"></a>CMFCPreviewCtrlImpl::GetDocument

Gibt ein Dokument zurück, das mit diesem Vorschausteuerelement verbunden ist.

### <a name="syntax"></a>Syntax

```
ATL::IDocument* GetDocument();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein Dokument, dessen Inhalt im Steuerelement in der Vorschau angezeigt wird.

## <a name="cmfcpreviewctrlimplm_clrbackcolor"></a><a name="m_clrbackcolor"></a>CMFCPreviewCtrlImpl::m_clrBackColor

Hintergrundfarbe des Vorschaufensters.

### <a name="syntax"></a>Syntax

```
COLORREF m_clrBackColor;
```

## <a name="cmfcpreviewctrlimplm_clrtextcolor"></a><a name="m_clrtextcolor"></a>CMFCPreviewCtrlImpl::m_clrTextColor

Textfarbe des Vorschaufensters.

### <a name="syntax"></a>Syntax

```
COLORREF m_clrTextColor;
```

## <a name="cmfcpreviewctrlimplm_font--font-used-to-display-text-in-the-preview-window"></a><a name="m_font"></a>CMFCPreviewCtrlImpl::m_font Schriftart, die zum Anzeigen von Text im Vorschaufenster verwendet wird.

### <a name="syntax"></a>Syntax

```
CFont m_font;
```

## <a name="cmfcpreviewctrlimplm_pdocument"></a><a name="m_pdocument"></a>CMFCPreviewCtrlImpl::m_pDocument

Ein Zeiger auf ein Dokument, dessen Inhalt im Steuerelement in der Vorschau angezeigt wird.

### <a name="syntax"></a>Syntax

```
ATL::IDocument* m_pDocument;
```

## <a name="cmfcpreviewctrlimplredraw"></a><a name="redraw"></a>CMFCPreviewCtrlImpl::Neuzeichnen

Weist dieses Steuerelement an, neu zu zeichnen.

### <a name="syntax"></a>Syntax

```
virtual void Redraw();
```

## <a name="cmfcpreviewctrlimplsetdocument"></a><a name="setdocument"></a>CMFCPreviewCtrlImpl::SetDocument

Wird vom Vorschauhandler aufgerufen, um eine Beziehung zwischen der Dokumentimplementierung und dem Vorschausteuerelement zu erstellen.

### <a name="syntax"></a>Syntax

```
void SetDocument(
   IDocument* pDocument
);
```

### <a name="parameters"></a>Parameter

*pDocument*<br/>
Ein Zeiger auf die Dokumentimplementierung.

## <a name="cmfcpreviewctrlimplsethost"></a><a name="sethost"></a>CMFCPreviewCtrlImpl::SetHost

Legt ein neues übergeordnetes Element für dieses Steuerelement fest.

### <a name="syntax"></a>Syntax

```
virtual void SetHost(
   HWND hWndParent
);
```

### <a name="parameters"></a>Parameter

*hWndEltern*<br/>
Ein Handle für das neue übergeordnete Fenster.

## <a name="cmfcpreviewctrlimplsetpreviewvisuals"></a><a name="setpreviewvisuals"></a>CMFCPreviewCtrlImpl::SetPreviewVisuals

Wird von einem Rich Preview-Handler aufgerufen, wenn er visuelle Elemente mit umfangreichem Vorschauinhalt festlegen muss.

### <a name="syntax"></a>Syntax

```
virtual void SetPreviewVisuals(
   COLORREF clrBack,
   COLORREF clrText,
   const LOGFONTW *plf
);
```

### <a name="parameters"></a>Parameter

*clrBack*<br/>
Hintergrundfarbe des Vorschaufensters.

*clrText*<br/>
Textfarbe des Vorschaufensters.

*Plf*<br/>
Schriftart, die zum Anzeigen von Text im Vorschaufenster verwendet wird.

## <a name="cmfcpreviewctrlimplsetrect"></a><a name="setrect"></a>CMFCPreviewCtrlImpl::SetRect

Legt ein neues umgrenzendes Rechteck für dieses Steuerelement fest.

### <a name="syntax"></a>Syntax

```
virtual void SetRect(
   const RECT* prc,
   BOOL bRedraw
);
```

### <a name="parameters"></a>Parameter

*Vr china*<br/>
Gibt die neue Größe und Position des Vorschausteuerelements an.

*bZeichnung*<br/>
Gibt an, ob das Steuerelement neu gezeichnet werden soll.

### <a name="remarks"></a>Bemerkungen

Normalerweise wird ein neues umgrenzendes Rechteck festgelegt, wenn die Größe des Hoststeuerelements geändert wird.

## <a name="cmfcpreviewctrlimplcmfcpreviewctrlimpl"></a><a name="dtor"></a>CMFCPreviewCtrlImpl::'CMFCPreviewCtrlImpl

Zerstört ein Vorschausteuerelementobjekt.

### <a name="syntax"></a>Syntax

```
virtual ~CMFCPreviewCtrlImpl();
```
