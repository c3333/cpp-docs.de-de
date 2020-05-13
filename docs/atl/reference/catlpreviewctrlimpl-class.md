---
title: Klasse "-Klasse"
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
ms.openlocfilehash: fd94d0d6fe43d80b45def3f747c7b7d558de31d4
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167876"
---
# <a name="catlpreviewctrlimpl-class"></a>Klasse "-Klasse"

Diese Klasse ist eine ATL-Implementierung eines Fensters, das in einem Host Fenster platziert wird, das von der Shell für eine umfangreiche Vorschau bereitgestellt wird.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|["" ("" "" "" "") ""](#dtor)|Zerstört ein Vorschau Steuerelement Objekt.|
|["" "" "" "" "" "".](#catlpreviewctrlimpl)|Erstellt ein Vorschau Steuerelement Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|["": Create ""](#create)|Wird von einem Rich Preview-Handler aufgerufen, um das Windows-Fenster zu erstellen.|
|["Katlpreviewctrlimpl"::D estroy](#destroy)|Wird von einem Rich Preview-Handler aufgerufen, wenn er dieses Steuerelement zerstören muss.|
|["": Fokus ""](#focus)|Legt den Eingabefokus auf dieses Steuerelement fest.|
|["" "" "" "" "".](#onpaint)|Behandelt die WM_PAINT Meldung.|
|[' ' ' ' ' ' ' ' ' ' ' ' ' ' '](#redraw)|Weist dieses Steuerelement an, neu zu zeichnen.|
|["Ctrlimpl:: lthost"](#sethost)|Legt ein neues übergeordnetes Element für dieses Steuerelement fest.|
|["": Setpreviewvisualisierungen "](#setpreviewvisuals)|Wird von einem Rich Preview-Handler aufgerufen, wenn Visualisierungen von umfangreichen Vorschau Inhalten festgelegt werden müssen.|
|["Chanlpreviewctrlimpl:: SetRect"](#setrect)|Legt ein neues Begrenzungs Rechteck für dieses Steuerelement fest.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|["' ' ' ' ' ' ' ' ' ' '":D](#dopaint)|Wird vom Framework aufgerufen, um die Vorschau zu Rendering.|

### <a name="protected-constants"></a>Geschützte Konstanten

|Name|BESCHREIBUNG|
|----------|-----------------|
|["" ""-M_plf](#m_plf)|Schriftart, die zum Anzeigen von Text im Vorschau Fenster verwendet wird.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|["" ""-M_clrBack](#m_clrback)|Hintergrundfarbe des Vorschaufensters.|
|["" ""-M_clrText](#m_clrtext)|Textfarbe des Vorschaufensters.|

## <a name="remarks"></a>Bemerkungen

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`TBase`

`ATL::CMessageMap`

`ATL::CWindowImplRoot<TBase>`

`ATL::CWindowImplBaseT<TBase,TWinTraits>`

[ATL:: CWindowImpl\<-CWindowImpl->](../../atl/reference/cwindowimpl-class.md)

`IPreviewCtrl`

`ATL::CAtlPreviewCtrlImpl`

## <a name="requirements"></a>Anforderungen

**Header:** atlpreviewctrlimpl. h

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="catlpreviewctrlimpl"></a>"" "" "" "" "" "".

Erstellt ein Vorschau Steuerelement Objekt.

```cpp
CAtlPreviewCtrlImpl(void) : m_clrText(0),
   m_clrBack(RGB(255, 255, 255)), m_plf(NULL);
```

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="dtor"></a>"" ("" "" "" "") ""

Zerstört ein Vorschau Steuerelement Objekt.

```cpp
virtual ~CAtlPreviewCtrlImpl(void);
```

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimplcreate"></a><a name="create"></a>"": Create ""

Wird von einem Rich Preview-Handler aufgerufen, um das Windows-Fenster zu erstellen.

```cpp
virtual BOOL Create(HWND hWndParent, const RECT* prc);
```

### <a name="parameters"></a>Parameter

*hwndParent*<br/>
Ein Handle für das Host Fenster, das von der Shell für die umfangreiche Vorschau bereitgestellt wird.

*PRC*<br/>
Gibt die anfängliche Größe und Position des Fensters an.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimpldestroy"></a><a name="destroy"></a>"Katlpreviewctrlimpl"::D estroy

Wird von einem Rich Preview-Handler aufgerufen, wenn er dieses Steuerelement zerstören muss.

```cpp
virtual void Destroy();
```

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimpldopaint"></a><a name="dopaint"></a>"' ' ' ' ' ' ' ' ' ' '":D

Wird vom Framework aufgerufen, um die Vorschau zu Rendering.

```cpp
virtual void DoPaint(HDC hdc);
```

### <a name="parameters"></a>Parameter

*HDC*<br/>
Ein Handle für einen Gerätekontext zum Zeichnen.

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimplfocus"></a><a name="focus"></a>"": Fokus ""

Legt den Eingabefokus auf dieses Steuerelement fest.

```cpp
virtual void Focus();
```

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimplm_clrback"></a><a name="m_clrback"></a>"" ""-M_clrBack

Hintergrundfarbe des Vorschaufensters.

```cpp
COLORREF m_clrBack;
```

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimplm_clrtext"></a><a name="m_clrtext"></a>"" ""-M_clrText

Textfarbe des Vorschaufensters.

```cpp
COLORREF m_clrText;
```

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimplm_plf"></a><a name="m_plf"></a>"" ""-M_plf

Schriftart, die zum Anzeigen von Text im Vorschau Fenster verwendet wird.

```cpp
const LOGFONTW* m_plf;
```

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimplonpaint"></a><a name="onpaint"></a>"" "" "" "" "".

Behandelt die WM_PAINT Meldung.

```cpp
LRESULT OnPaint(
    UINT nMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parameter

*nMsg*<br/>
Legen Sie auf WM_PAINT fest.

*wParam*<br/>
Dieser Parameter wird nicht verwendet.

*lParam*<br/>
Dieser Parameter wird nicht verwendet.

*bHandled*<br/>
Wenn diese Funktion zurückgibt, enthält Sie "true".

### <a name="return-value"></a>Rückgabewert

Es wird immer 0 zurückgegeben.

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimplredraw"></a><a name="redraw"></a>' ' ' ' ' ' ' ' ' ' ' ' ' ' '

Weist dieses Steuerelement an, neu zu zeichnen.

```cpp
virtual void Redraw();
```

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimplsethost"></a><a name="sethost"></a>"Ctrlimpl:: lthost"

Legt ein neues übergeordnetes Element für dieses Steuerelement fest.

```cpp
virtual void SetHost(HWND hWndParent);
```

### <a name="parameters"></a>Parameter

*hwndParent*<br/>
Ein Handle für das neue übergeordnete Fenster.

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimplsetpreviewvisuals"></a><a name="setpreviewvisuals"></a>"": Setpreviewvisualisierungen "

Wird von einem Rich Preview-Handler aufgerufen, wenn Visualisierungen von umfangreichen Vorschau Inhalten festgelegt werden müssen.

```cpp
virtual void SetPreviewVisuals(
    COLORREF clrBack,
    COLORREF clrText,
    const LOGFONTW* plf);
```

### <a name="parameters"></a>Parameter

*clrback*<br/>
Hintergrundfarbe des Vorschaufensters.

*clrText*<br/>
Textfarbe des Vorschaufensters.

*PLF*<br/>
Schriftart, die zum Anzeigen von Text im Vorschau Fenster verwendet wird.

### <a name="remarks"></a>Bemerkungen

## <a name="catlpreviewctrlimplsetrect"></a><a name="setrect"></a>"Chanlpreviewctrlimpl:: SetRect"

Legt ein neues Begrenzungs Rechteck für dieses Steuerelement fest.

```cpp
virtual void SetRect(const RECT* prc, BOOL bRedraw);
```

### <a name="parameters"></a>Parameter

*PRC*<br/>
Gibt die neue Größe und Position des Vorschau Steuer Elements an.

*bredraw*<br/>
Gibt an, ob das Steuerelement neu gezeichnet werden soll.

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Weitere Informationen:

[ATL-COM-Desktop-Komponenten](../../atl/atl-com-desktop-components.md)
