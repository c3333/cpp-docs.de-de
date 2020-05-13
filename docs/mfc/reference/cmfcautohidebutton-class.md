---
title: CMFCAutoHideButton-Klasse
ms.date: 10/18/2018
f1_keywords:
- CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::BringToTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Create
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAlignment
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAutoHideWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetParentToolBar
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetRect
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetTextSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::HighlightButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsActive
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHighlighted
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHorizontal
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsVisible
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Move
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDraw
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDrawBorder
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnFillBackground
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ReplacePane
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowAttachedWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::UnSetAutoHideMode
helpviewer_keywords:
- CMFCAutoHideButton [MFC], BringToTop
- CMFCAutoHideButton [MFC], Create
- CMFCAutoHideButton [MFC], GetAlignment
- CMFCAutoHideButton [MFC], GetAutoHideWindow
- CMFCAutoHideButton [MFC], GetParentToolBar
- CMFCAutoHideButton [MFC], GetRect
- CMFCAutoHideButton [MFC], GetSize
- CMFCAutoHideButton [MFC], GetTextSize
- CMFCAutoHideButton [MFC], HighlightButton
- CMFCAutoHideButton [MFC], IsActive
- CMFCAutoHideButton [MFC], IsHighlighted
- CMFCAutoHideButton [MFC], IsHorizontal
- CMFCAutoHideButton [MFC], IsTop
- CMFCAutoHideButton [MFC], IsVisible
- CMFCAutoHideButton [MFC], Move
- CMFCAutoHideButton [MFC], OnDraw
- CMFCAutoHideButton [MFC], OnDrawBorder
- CMFCAutoHideButton [MFC], OnFillBackground
- CMFCAutoHideButton [MFC], ReplacePane
- CMFCAutoHideButton [MFC], ShowAttachedWindow
- CMFCAutoHideButton [MFC], ShowButton
- CMFCAutoHideButton [MFC], UnSetAutoHideMode
ms.assetid: c80e6b8b-25ca-4d12-9d27-457731028ab0
ms.openlocfilehash: 3ea6ce13b8cca7e0130fe14459a832b476391b0c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751671"
---
# <a name="cmfcautohidebutton-class"></a>CMFCAutoHideButton-Klasse

Eine Schaltfläche, die [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) anzeigt oder ausblendet (vorausgesetzt, die Klasse ist so konfiguriert, dass sie ausgeblendet werden kann).

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

## <a name="syntax"></a>Syntax

```
class CMFCAutoHideButton : public CObject
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCAutoHideButton::BringToTop](#bringtotop)||
|[CMFCAutoHideButton::Create](#create)|Erstellt und initialisiert die Schaltfläche zum automatischen Ausblenden.|
|[CMFCAutoHideButton::GetAlignment](#getalignment)|Ruft die Ausrichtung der Schaltfläche zum automatischen Ausblenden ab.|
|[CMFCAutoHideButton::GetAutoHideWindow](#getautohidewindow)|Gibt das [CDockablePane-Objekt zurück,](../../mfc/reference/cdockablepane-class.md) das der Schaltfläche "Auto-Ausblenden" zugeordnet ist.|
|[CMFCAutoHideButton::GetParentToolBar](#getparenttoolbar)||
|[CMFCAutoHideButton::GetRect](#getrect)||
|[CMFCAutoHideButton::GetSize](#getsize)|Legt die Größe der Schaltfläche zum automatischen Ausblenden fest.|
|[CMFCAutoHideButton::GetTextSize](#gettextsize)|Gibt die Größe der Textbeschriftung für die Schaltfläche zum automatischen Ausblenden zurück.|
|[CMFCAutoHideButton::HighlightButton](#highlightbutton)|Hebt die Schaltfläche zum automatischen Ausblenden hervor.|
|[CMFCAutoHideButton::IsActive](#isactive)|Gibt an, ob die Schaltfläche zum automatischen Ausblenden aktiv ist.|
|[CMFCAutoHideButton::IsHighlighted](#ishighlighted)|Gibt den Hervorhebestatus der Schaltfläche zum automatischen Ausblenden zurück.|
|[CMFCAutoHideButton::IsHorizontal](#ishorizontal)|Bestimmt, ob die Schaltfläche zum automatischen Ausblenden horizontal oder vertikal ist.|
|[CMFCAutoHideButton::IsTop](#istop)||
|[CMFCAutoHideButton::IsVisible](#isvisible)|Gibt an, ob die Schaltfläche sichtbar ist.|
|[CMFCAutoHideButton::Move](#move)||
|[CMFCAutoHideButton::OnDraw](#ondraw)|Das Framework ruft diese Methode auf, wenn es die Schaltfläche zum automatischen Ausblenden zeichnet.|
|[CMFCAutoHideButton::OnDrawBorder](#ondrawborder)|Das Framework ruft diese Methode auf, wenn es den Rahmen einer Schaltfläche zum automatischen Ausblenden zeichnet.|
|[CMFCAutoHideButton::OnFillBackground](#onfillbackground)|Das Framework ruft diese Methode auf, wenn es den Hintergrund einer Schaltfläche zum automatischen Ausblenden füllt.|
|[CMFCAutoHideButton::ReplacePane](#replacepane)||
|[CMFCAutoHideButton::ShowAttachedWindow](#showattachedwindow)|Zeigt die zugehörige [CDockablePane-Klasse](../../mfc/reference/cdockablepane-class.md)ein oder blendet sie aus.|
|[CMFCAutoHideButton::ShowButton](#showbutton)|Blendet die Schaltfläche zum automatischen Ausblenden ein oder aus.|
|[CMFCAutoHideButton::UnSetAutoHideMode](#unsetautohidemode)||

## <a name="remarks"></a>Bemerkungen

Bei der `CMFCAutoHideButton` Erstellung wird das Objekt an eine [CDockablePane-Klasse](../../mfc/reference/cdockablepane-class.md)angefügt. Das `CDockablePane`-Objekt wird ausgeblendet oder angezeigt, wenn der Benutzer mit dem `CMFCAutoHideButton`-Objekt interagiert.

Standardmäßig erstellt das Framework automatisch eine `CMFCAutoHideButton`, wenn der Benutzer das automatische Ausblenden aktiviert. Das Framework kann ein Element einer benutzerdefinierten Benutzeroberflächenklasse erstellen, anstatt der `CMFCAutoHideButton`-Klasse. Um festzulegen, welche benutzerdefinierte Benutzeroberflächenklasse das Framework verwenden soll, legen Sie die statische Membervariable `CMFCAutoHideBar::m_pAutoHideButtonRTS` auf den gleichen Wert wie die benutzerdefinierte Benutzeroberflächenklasse fest. Standardmäßig ist diese Variable auf `CMFCAutoHideButton` festgelegt.

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht das Erstellen eines `CMFCAutoHideButton`-Objekts, und die Verwendung verschiedener Methoden in der `CMFCAutoHideButton`-Klasse. Das Beispiel veranschaulicht, wie Sie ein `CMFCAutoHideButton`-Objekt mithilfe seiner `Create`-Methode initialisieren, die zugeordnete `CDockablePane`-Klasse anzeigen und die Schaltfläche zum automatischen Ausblenden anzeigen.

[!code-cpp[NVC_MFC_RibbonApp#32](../../mfc/reference/codesnippet/cpp/cmfcautohidebutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CMFCAutoHideButton`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxautohidebutton.h

## <a name="cmfcautohidebuttonbringtotop"></a><a name="bringtotop"></a>CMFCAutoHideButton::BringToTop

```cpp
void BringToTop();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcautohidebuttoncreate"></a><a name="create"></a>CMFCAutoHideButton::Erstellen

Erstellt und initialisiert eine Schaltfläche zum automatischen Ausblenden.

```
virtual BOOL Create(
    CMFCAutoHideBar* pParentBar,
    CDockablePane* pAutoHideWnd,
    DWORD dwAlignment);
```

### <a name="parameters"></a>Parameter

*pParentBar*<br/>
[in] Ein Zeiger auf die übergeordnete Symbolleiste.

*pAutoHideWnd*<br/>
[in] Ein Zeiger auf ein [CDockablePane-Objekt.](../../mfc/reference/cdockablepane-class.md) Diese Auto-Hide-Schaltfläche blendet `CDockablePane`aus und zeigt an, dass .

*dwAlignment*<br/>
[in] Ein Wert, der die Ausrichtung der Schaltfläche mit dem Hauptrahmenfenster angibt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Wenn Sie `CMFCAutoHideButton` ein Objekt erstellen, müssen Sie die `CDockablePane`Schaltfläche zum automatischen Ausblenden einer bestimmten . Der Benutzer kann die Schaltfläche "Auto-Hide" `CDockablePane`verwenden, um die zugehörige ausblenden und anzuzeigen.

Der *Parameter dwAlignment* gibt an, wo sich die Schaltfläche zum automatischen Ausblenden in der Anwendung befindet. Der Parameter kann auf einen der folgenden Werte festgelegt werden:

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebuttongetalignment"></a><a name="getalignment"></a>CMFCAutoHideButton::GetAlignment

Ruft die Ausrichtung der Schaltfläche zum automatischen Ausblenden ab.

```
DWORD GetAlignment() const;
```

### <a name="return-value"></a>Rückgabewert

Ein DWORD-Wert, der die aktuelle Ausrichtung der Schaltfläche "Automatisches Ausblenden" enthält.

### <a name="remarks"></a>Bemerkungen

Die Ausrichtung der Schaltfläche "Auto-Ausblenden" gibt an, wo sich die Schaltfläche in der Anwendung befindet. Es kann einer der folgenden Werte sein:

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CRBS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebuttongetautohidewindow"></a><a name="getautohidewindow"></a>CMFCAutoHideButton::GetAutoHideWindow

Gibt das [CDockablePane-Objekt zurück,](../../mfc/reference/cdockablepane-class.md) das der Schaltfläche "Auto-Ausblenden" zugeordnet ist.

```
CDockablePane* GetAutoHideWindow() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CDockablePane` das zugeordnete Objekt.

### <a name="remarks"></a>Bemerkungen

Um eine Auto-Hide-Schaltfläche `CDockablePane`einem `CDockablePane` zuzuordnen, übergeben Sie den als Parameter an die [CMFCAutoHideButton::Create-Methode.](#create)

## <a name="cmfcautohidebuttongetparenttoolbar"></a><a name="getparenttoolbar"></a>CMFCAutoHideButton::GetParentToolBar

```
CMFCAutoHideBar* GetParentToolBar();
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcautohidebuttongetrect"></a><a name="getrect"></a>CMFCAutoHideButton::GetRect

```
CRect GetRect() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcautohidebuttongetsize"></a><a name="getsize"></a>CMFCAutoHideButton::GetSize

Legt die Größe der Schaltfläche zum automatischen Ausblenden fest.

```
CSize GetSize() const;
```

### <a name="return-value"></a>Rückgabewert

Ein `CSize` Objekt, das die Schaltflächengröße enthält.

### <a name="remarks"></a>Bemerkungen

Die berechnete Größe enthält die Größe des Rahmens der Schaltfläche zum automatischen Ausblenden.

## <a name="cmfcautohidebuttongettextsize"></a><a name="gettextsize"></a>CMFCAutoHideButton::GetTextSize

Gibt die Größe der Textbeschriftung für die Schaltfläche zum automatischen Ausblenden zurück.

```
virtual CSize GetTextSize() const;
```

### <a name="return-value"></a>Rückgabewert

Ein [CSize-Objekt,](../../atl-mfc-shared/reference/csize-class.md) das die Größe des Textes für die Schaltfläche zum automatischen Ausblenden enthält.

## <a name="cmfcautohidebuttonisactive"></a><a name="isactive"></a>CMFCAutoHideButton::IsActive

Gibt an, ob die Schaltfläche zum automatischen Ausblenden aktiv ist.

```
BOOL IsActive() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Schaltfläche zum automatischen Ausblenden aktiv ist; FALSE sonst.

### <a name="remarks"></a>Bemerkungen

Eine Schaltfläche zum automatischen Ausblenden ist aktiv, wenn das zugehörige [CDockablePane-Klassenfenster](../../mfc/reference/cdockablepane-class.md) angezeigt wird.

## <a name="cmfcautohidebuttonishorizontal"></a><a name="ishorizontal"></a>CMFCAutoHideButton::IsHorizontal

Bestimmt, ob die Schaltfläche zum automatischen Ausblenden horizontal oder vertikal ist.

```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Schaltfläche horizontal ist; 0 sonst.

### <a name="remarks"></a>Bemerkungen

Das Framework legt die Ausrichtung eines [CMFCAutoHideButton-Objekts](../../mfc/reference/cmfcautohidebutton-class.md) fest, wenn Sie es erstellen.  Sie können die Ausrichtung steuern, indem Sie den Parameter *dwAlignment* in der [CMFCAutoHideButton::Create-Methode](#create) verwenden.

## <a name="cmfcautohidebuttonistop"></a><a name="istop"></a>CMFCAutoHideButton::IsTop

```
BOOL IsTop() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcautohidebuttonisvisible"></a><a name="isvisible"></a>CMFCAutoHideButton::IsVisible

Gibt an, ob die Schaltfläche "Auto-Ausblenden" sichtbar ist.

```
virtual BOOL IsVisible() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Schaltfläche sichtbar ist; FALSE sonst.

## <a name="cmfcautohidebuttonondraw"></a><a name="ondraw"></a>CMFCAutoHideButton::OnDraw

Das Framework ruft diese Methode auf, wenn es die Schaltfläche zum automatischen Ausblenden zeichnet.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

### <a name="remarks"></a>Bemerkungen

Wenn Sie die Darstellung von Schaltflächen zum automatischen Ausblenden in `CMFCAutoHideButton`Ihrer Anwendung anpassen möchten, erstellen Sie eine neue Klasse, die von abgeleitet ist. Überschreiben Sie in der abgeleiteten Klasse diese Methode.

## <a name="cmfcautohidebuttonondrawborder"></a><a name="ondrawborder"></a>CMFCAutoHideButton::OnDrawBorder

Das Framework ruft diese Methode auf, wenn es den Rahmen einer Schaltfläche zum automatischen Ausblenden zeichnet.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rectBounds,
    CRect rectBorderSize);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

*rectBounds*<br/>
[in] Das umgrenzende Rechteck der Schaltfläche zum automatischen Ausblenden.

*rectBorderSize*<br/>
[in] Die Rahmenstärke für jede Seite der Auto-Hide-Schaltfläche.

### <a name="remarks"></a>Bemerkungen

Wenn Sie den Rahmen jeder Auto-Hide-Schaltfläche in Ihrer Anwendung anpassen `CMFCAutoHideButton`möchten, erstellen Sie eine neue Klasse, die von der abgeleitet ist. Überschreiben Sie in der abgeleiteten Klasse diese Methode.

## <a name="cmfcautohidebuttononfillbackground"></a><a name="onfillbackground"></a>CMFCAutoHideButton::OnFillBackground

Das Framework ruft diese Methode auf, wenn es den Hintergrund einer Schaltfläche zum automatischen Ausblenden füllt.

```
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

*Rect*<br/>
[in] Das umgrenzende Rechteck der Schaltfläche zum automatischen Ausblenden.

### <a name="remarks"></a>Bemerkungen

Wenn Sie den Hintergrund für automatisches Ausblenden von Schaltflächen in `CMFCAutoHideButton`Ihrer Anwendung anpassen möchten, erstellen Sie eine neue Klasse, die von der abgeleitet ist. Überschreiben Sie in der abgeleiteten Klasse diese Methode.

## <a name="cmfcautohidebuttonshowattachedwindow"></a><a name="showattachedwindow"></a>CMFCAutoHideButton::ShowAttachedWindow

Zeigt die zugehörige [CDockablePane-Klasse](../../mfc/reference/cdockablepane-class.md)ein oder blendet sie aus.

```cpp
void ShowAttachedWindow(BOOL bShow);
```

### <a name="parameters"></a>Parameter

*bShow*<br/>
[in] Ein boolescher Wert, der angibt, ob diese Methode die angefügte anzeigt. `CDockablePane`

## <a name="cmfcautohidebuttonshowbutton"></a><a name="showbutton"></a>CMFCAutoHideButton::ShowButton

Blendet die Schaltfläche zum automatischen Ausblenden ein oder aus.

```
virtual void ShowButton(BOOL bShow);
```

### <a name="parameters"></a>Parameter

*bShow*<br/>
[in] Ein boolescher Wert, der angibt, ob die Schaltfläche zum automatischen Ausblenden angezeigt werden soll.

## <a name="cmfcautohidebuttonmove"></a><a name="move"></a>CMFCAutoHideButton::Verschieben

```cpp
void Move(int nOffset);
```

### <a name="parameters"></a>Parameter

[in] *nOffset*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcautohidebuttonreplacepane"></a><a name="replacepane"></a>CMFCAutoHideButton::ReplacePane

```cpp
void ReplacePane(CDockablePane* pNewBar);
```

### <a name="parameters"></a>Parameter

[in] *pNewBar*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcautohidebuttonunsetautohidemode"></a><a name="unsetautohidemode"></a>CMFCAutoHideButton::UnSetAutoHideMode

Deaktiviert den automatischen Ausblendemodus.

```
virtual void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup);
```

### <a name="parameters"></a>Parameter

*pFirstBarInGroup*<br/>
[in] Ein Zeiger auf den ersten Balken in der Gruppe.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcautohidebuttonhighlightbutton"></a><a name="highlightbutton"></a>CMFCAutoHideButton::HighlightButton

Hebt die Auto-Ausblend-Schaltfläche hervor.

```
virtual void HighlightButton(BOOL bHighlight);
```

### <a name="parameters"></a>Parameter

*bHighlight*<br/>
Gibt den neuen Automatischen Ausblendschaltflächenstatus an. TRUE gibt an, dass die Schaltfläche hervorgehoben ist, FALSE zeigt an, dass die Schaltfläche nicht hervorgehoben ist.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcautohidebuttonishighlighted"></a><a name="ishighlighted"></a>CMFCAutoHideButton::Hervorgehoben

Gibt den Hervorhebungsstatus der Schaltfläche "Auto-Ausblendung" zurück.

```
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn die Schaltfläche "Auto ausblenden" hervorgehoben ist. andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCAutoHideBar-Klasse](../../mfc/reference/cmfcautohidebar-class.md)<br/>
[CAutoHideDockSite-Klasse](../../mfc/reference/cautohidedocksite-class.md)
