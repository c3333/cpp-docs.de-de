---
title: CAtlPreviewCtrlImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Create
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Destroy
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Focus
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::OnPaint
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Redraw
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetHost
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetPreviewVisuals
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetRect
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::DoPaint
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_plf
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_clrBack
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_clrText
helpviewer_keywords:
- CAtlPreviewCtrlImpl class
ms.assetid: 39b3299e-07e4-4abc-9b6e-b54bfa3b0802
ms.openlocfilehash: 1ccd01bc4d48dc088538f4799b595cce3fb910ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321365"
---
# <a name="catlpreviewctrlimpl-class"></a>CAtlPreviewCtrlImpl-Klasse

Diese Klasse ist eine ATL-Implementierung eines Fensters, das in einem Hostfenster platziert wird, das von der Shell für Rich Preview bereitgestellt wird.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::'CAtlPreviewCtrlImpl](#dtor)|Zerstört ein Vorschausteuerelementobjekt.|
|[CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl](#catlpreviewctrlimpl)|Erstellt ein Vorschausteuerelementobjekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::Erstellen](#create)|Wird von einem Rich Preview-Handler aufgerufen, um das Windows-Fenster zu erstellen.|
|[CAtlPreviewCtrlImpl::Destroy](#destroy)|Wird von einem Rich Preview-Handler aufgerufen, wenn dieses Steuerelement zerstört werden muss.|
|[CAtlPreviewCtrlImpl::Fokus](#focus)|Legt den Eingabefokus auf dieses Steuerelement fest.|
|[CAtlPreviewCtrlImpl::OnPaint](#onpaint)|Behandelt die WM_PAINT Nachricht.|
|[CAtlPreviewCtrlImpl::Neuzeichnen](#redraw)|Weist dieses Steuerelement an, neu zu zeichnen.|
|[CAtlPreviewCtrlImpl::SetHost](#sethost)|Legt ein neues übergeordnetes Element für dieses Steuerelement fest.|
|[CAtlPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Wird von einem Rich Preview-Handler aufgerufen, wenn er visuelle Elemente mit umfangreichem Vorschauinhalt festlegen muss.|
|[CAtlPreviewCtrlImpl::SetRect](#setrect)|Legt ein neues umgrenzendes Rechteck für dieses Steuerelement fest.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::DoPaint](#dopaint)|Wird vom Framework aufgerufen, um die Vorschau zu rendern.|

### <a name="protected-constants"></a>Geschützte Konstanten

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::m_plf](#m_plf)|Schriftart, die zum Anzeigen von Text im Vorschaufenster verwendet wird.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::m_clrBack](#m_clrback)|Hintergrundfarbe des Vorschaufensters.|
|[CAtlPreviewCtrlImpl::m_clrText](#m_clrtext)|Textfarbe des Vorschaufensters.|

## <a name="remarks"></a>Bemerkungen

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`TBase`

`ATL::CMessageMap`

`ATL::CWindowImplRoot<TBase>`

`ATL::CWindowImplBaseT<TBase,TWinTraits>`

[ATL::CWindowImpl\<CAtlPreviewCtrlImpl>](../../atl/reference/cwindowimpl-class.md)

`IPreviewCtrl`

`ATL::CAtlPreviewCtrlImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlpreviewctrlimpl.h

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="catlpreviewctrlimpl"></a>CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl

Erstellt ein Vorschausteuerelementobjekt.

```
CAtlPreviewCtrlImpl(void) : m_clrText(0),
   m_clrBack(RGB(255, 255, 255)), m_plf(NULL);
```

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="dtor"></a>CAtlPreviewCtrlImpl::'CAtlPreviewCtrlImpl

Zerstört ein Vorschausteuerelementobjekt.

```
virtual ~CAtlPreviewCtrlImpl(void);
```

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimplcreate"></a><a name="create"></a>CAtlPreviewCtrlImpl::Erstellen

Wird von einem Rich Preview-Handler aufgerufen, um das Windows-Fenster zu erstellen.

```
virtual BOOL Create(HWND hWndParent, const RECT* prc);
```

### <a name="parameters"></a>Parameter

*hWndEltern*<br/>
Ein Handle für das Hostfenster, das von der Shell für Rich Preview bereitgestellt wird.

*Vr china*<br/>
Gibt die Anfangsgröße und Position des Fensters an.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimpldestroy"></a><a name="destroy"></a>CAtlPreviewCtrlImpl::Destroy

Wird von einem Rich Preview-Handler aufgerufen, wenn dieses Steuerelement zerstört werden muss.

```
virtual void Destroy();
```

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimpldopaint"></a><a name="dopaint"></a>CAtlPreviewCtrlImpl::DoPaint

Wird vom Framework aufgerufen, um die Vorschau zu rendern.

```
virtual void DoPaint(HDC hdc);
```

### <a name="parameters"></a>Parameter

*Hdc*<br/>
Ein Handle für einen Gerätekontext zum Malen.

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimplfocus"></a><a name="focus"></a>CAtlPreviewCtrlImpl::Fokus

Legt den Eingabefokus auf dieses Steuerelement fest.

```
virtual void Focus();
```

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimplm_clrback"></a><a name="m_clrback"></a>CAtlPreviewCtrlImpl::m_clrBack

Hintergrundfarbe des Vorschaufensters.

```
COLORREF m_clrBack;
```

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimplm_clrtext"></a><a name="m_clrtext"></a>CAtlPreviewCtrlImpl::m_clrText

Textfarbe des Vorschaufensters.

```
COLORREF m_clrText;
```

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimplm_plf"></a><a name="m_plf"></a>CAtlPreviewCtrlImpl::m_plf

Schriftart, die zum Anzeigen von Text im Vorschaufenster verwendet wird.

```
const LOGFONTW* m_plf;
```

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimplonpaint"></a><a name="onpaint"></a>CAtlPreviewCtrlImpl::OnPaint

Behandelt die WM_PAINT Nachricht.

```
LRESULT OnPaint(
    UINT nMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parameter

*nMsg*<br/>
Legen Sie WM_PAINT fest.

*wParam*<br/>
Dieser Parameter wird nicht verwendet.

*lParam*<br/>
Dieser Parameter wird nicht verwendet.

*bBehandelt*<br/>
Wenn diese Funktion zurückkehrt, enthält sie TRUE.

### <a name="return-value"></a>Rückgabewert

Es wird immer 0 zurückgegeben.

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimplredraw"></a><a name="redraw"></a>CAtlPreviewCtrlImpl::Neuzeichnen

Weist dieses Steuerelement an, neu zu zeichnen.

```
virtual void Redraw();
```

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimplsethost"></a><a name="sethost"></a>CAtlPreviewCtrlImpl::SetHost

Legt ein neues übergeordnetes Element für dieses Steuerelement fest.

```
virtual void SetHost(HWND hWndParent);
```

### <a name="parameters"></a>Parameter

*hWndEltern*<br/>
Ein Handle für das neue übergeordnete Fenster.

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimplsetpreviewvisuals"></a><a name="setpreviewvisuals"></a>CAtlPreviewCtrlImpl::SetPreviewVisuals

Wird von einem Rich Preview-Handler aufgerufen, wenn er visuelle Elemente mit umfangreichem Vorschauinhalt festlegen muss.

```
virtual void SetPreviewVisuals(
    COLORREF clrBack,
    COLORREF clrText,
    const LOGFONTW* plf);
```

### <a name="parameters"></a>Parameter

*clrBack*<br/>
Hintergrundfarbe des Vorschaufensters.

*clrText*<br/>
Textfarbe des Vorschaufensters.

*Plf*<br/>
Schriftart, die zum Anzeigen von Text im Vorschaufenster verwendet wird.

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimplsetrect"></a><a name="setrect"></a>CAtlPreviewCtrlImpl::SetRect

Legt ein neues umgrenzendes Rechteck für dieses Steuerelement fest.

```
virtual void SetRect(const RECT* prc, BOOL bRedraw);
```

### <a name="parameters"></a>Parameter

*Vr china*<br/>
Gibt die neue Größe und Position des Vorschausteuerelements an.

*bZeichnung*<br/>
Gibt an, ob das Steuerelement neu gezeichnet werden soll.

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

[ATL-COM-Desktop-Komponenten](../../atl/atl-com-desktop-components.md)
