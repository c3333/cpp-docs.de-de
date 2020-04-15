---
title: CMFCRibbonEdit-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CanBeStretched
- AFXRIBBONEDIT/CMFCRibbonEdit::CopyFrom
- AFXRIBBONEDIT/CMFCRibbonEdit::CreateEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::DestroyCtrl
- AFXRIBBONEDIT/CMFCRibbonEdit::DropDownList
- AFXRIBBONEDIT/CMFCRibbonEdit::EnableSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::GetCompactSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::GetIntermediateSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::GetWidth
- AFXRIBBONEDIT/CMFCRibbonEdit::HasCompactMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasFocus
- AFXRIBBONEDIT/CMFCRibbonEdit::HasLargeMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::IsHighlighted
- AFXRIBBONEDIT/CMFCRibbonEdit::OnAfterChangeRect
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDraw
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawLabelAndImage
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawOnList
- AFXRIBBONEDIT/CMFCRibbonEdit::OnEnable
- AFXRIBBONEDIT/CMFCRibbonEdit::OnHighlight
- AFXRIBBONEDIT/CMFCRibbonEdit::OnKey
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonDown
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonUp
- AFXRIBBONEDIT/CMFCRibbonEdit::OnRTLChanged
- AFXRIBBONEDIT/CMFCRibbonEdit::OnShow
- AFXRIBBONEDIT/CMFCRibbonEdit::Redraw
- AFXRIBBONEDIT/CMFCRibbonEdit::SetACCData
- AFXRIBBONEDIT/CMFCRibbonEdit::SetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::SetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::SetWidth
helpviewer_keywords:
- CMFCRibbonEdit [MFC], CMFCRibbonEdit
- CMFCRibbonEdit [MFC], CanBeStretched
- CMFCRibbonEdit [MFC], CMFCRibbonEdit
- CMFCRibbonEdit [MFC], CopyFrom
- CMFCRibbonEdit [MFC], CreateEdit
- CMFCRibbonEdit [MFC], DestroyCtrl
- CMFCRibbonEdit [MFC], DropDownList
- CMFCRibbonEdit [MFC], EnableSpinButtons
- CMFCRibbonEdit [MFC], GetCompactSize
- CMFCRibbonEdit [MFC], GetEditText
- CMFCRibbonEdit [MFC], GetIntermediateSize
- CMFCRibbonEdit [MFC], GetTextAlign
- CMFCRibbonEdit [MFC], GetWidth
- CMFCRibbonEdit [MFC], HasCompactMode
- CMFCRibbonEdit [MFC], HasFocus
- CMFCRibbonEdit [MFC], HasLargeMode
- CMFCRibbonEdit [MFC], HasSpinButtons
- CMFCRibbonEdit [MFC], IsHighlighted
- CMFCRibbonEdit [MFC], OnAfterChangeRect
- CMFCRibbonEdit [MFC], OnDraw
- CMFCRibbonEdit [MFC], OnDrawLabelAndImage
- CMFCRibbonEdit [MFC], OnDrawOnList
- CMFCRibbonEdit [MFC], OnEnable
- CMFCRibbonEdit [MFC], OnHighlight
- CMFCRibbonEdit [MFC], OnKey
- CMFCRibbonEdit [MFC], OnLButtonDown
- CMFCRibbonEdit [MFC], OnLButtonUp
- CMFCRibbonEdit [MFC], OnRTLChanged
- CMFCRibbonEdit [MFC], OnShow
- CMFCRibbonEdit [MFC], Redraw
- CMFCRibbonEdit [MFC], SetACCData
- CMFCRibbonEdit [MFC], SetEditText
- CMFCRibbonEdit [MFC], SetTextAlign
- CMFCRibbonEdit [MFC], SetWidth
ms.assetid: 9b85f1f2-446b-454e-9af9-104fdad8a897
ms.openlocfilehash: ab621a05f9b658eee9babb14e257680fa95e0f96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375175"
---
# <a name="cmfcribbonedit-class"></a>CMFCRibbonEdit-Klasse

Implementiert ein Bearbeitungssteuerelement, das sich auf einer Multifunktionsleistenleiste befindet.

## <a name="syntax"></a>Syntax

```cpp
class CMFCRibbonEdit : public CMFCRibbonButton
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonBearbeiten::CMFCRibbonBearbeiten](#cmfcribbonedit)|Erstellt ein `CMFCRibbonEdit`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonEdit::CanBeStretched](#canbestretched)|Gibt an, ob `CMFCRibbonEdit` die Höhe des Steuerelements vertikal auf die Höhe einer Multifunktionsleistenreihe ansteigen kann.|
|[CMFCRibbonBearbeiten::CMFCRibbonBearbeiten](#cmfcribbonedit)|Erstellt ein `CMFCRibbonEdit`-Objekt.|
|[CMFCRibbonEdit::CopyFrom](#copyfrom)|Kopiert den Status `CMFCRibbonEdit` des angegebenen `CMFCRibbonEdit` Objekts in das aktuelle Objekt.|
|[CMFCRibbonEdit::CreateEdit](#createedit)|Erstellt ein neues Textfeld für das `CMFCRibbonEdit` Objekt.|
|[CMFCRibbonBearbeiten::DestroyCtrl](#destroyctrl)|Zerstört das `CMFCRibbonEdit`-Objekt.|
|[CMFCRibbonEdit::DropDownList](#dropdownlist)|Löscht ein Listenfeld herunter.|
|[CMFCRibbonEdit::EnableSpinButtons](#enablespinbuttons)|Aktiviert und legt den Bereich der Drehschaltfläche für das Textfeld fest.|
|[CMFCRibbonEdit::GetCompactSize](#getcompactsize)|Ruft die kompakte Größe `CFMCRibbonEdit` des Objekts ab.|
|[CMFCRibbonEdit::GetEditText](#getedittext)|Ruft den Text im Textfeld ab.|
|[CMFCRibbonEdit::GetIntermediateSize](#getintermediatesize)|Ruft die Zwischengröße `CMFCRibbonEdit` des Objekts ab.|
|[CMFCRibbonEdit::GetTextAlign](#gettextalign)|Ruft die Ausrichtung des Textes im Textfeld ab.|
|[CMFCRibbonEdit::GetWidth](#getwidth)|Ruft die Breite des `CMFCRibbonEdit` Steuerelements in Pixel ab.|
|[CMFCRibbonEdit::HasCompactMode](#hascompactmode)|Gibt an, ob `CMFCRibbonEdit` die Anzeigegröße für das Steuerelement kompakt sein kann.|
|[CMFCRibbonEdit::HasFocus](#hasfocus)|Gibt an, ob das `CMFCRIbbonEdit` Steuerelement den Fokus hat.|
|[CMFCRibbonEdit::HasLargeMode](#haslargemode)|Gibt an, ob `CMFCRibbonEdit` die Anzeigegröße für das Steuerelement groß sein kann.|
|[CMFCRibbonEdit::HasSpinButtons](#hasspinbuttons)|Gibt an, ob das Textfeld über eine Drehschaltfläche verfügt.|
|[CMFCRibbonEdit::Hervorgehoben](#ishighlighted)|Gibt an, ob das `CMFCRibbonEdit` Steuerelement hervorgehoben ist.|
|[CMFCRibbonEdit::OnAfterChangeRect](#onafterchangerect)|Wird vom Framework aufgerufen, wenn sich `CMFCRibbonEdit` die Bemaßungen des Anzeigerechtecks für das Steuerelement ändern.|
|[CMFCRibbonEdit::OnDraw](#ondraw)|Wird vom Framework aufgerufen, um das `CMFCRibbonEdit` Steuerelement zu zeichnen.|
|[CMFCRibbonEdit::OnDrawLabelAndImage](#ondrawlabelandimage)|Wird vom Framework aufgerufen, um die `CMFCRibbonEdit` Beschriftung und das Bild für das Steuerelement zu zeichnen.|
|[CMFCRibbonEdit::OnDrawonList](#ondrawonlist)|Wird vom Framework aufgerufen, um das `CMFCRibbonEdit` Steuerelement in einem Befehlslistenfeld zu zeichnen.|
|[CMFCRibbonEdit::OnEnable](#onenable)|Wird vom Framework aufgerufen, `CMFCRibbonEdit` um das Steuerelement zu aktivieren oder zu deaktivieren.|
|[CMFCRibbonEdit::OnHighlight](#onhighlight)|Wird vom Framework aufgerufen, wenn der Zeiger die `CMFCRibbonEdit` Grenzen des Steuerelements ein- oder ausgibt.|
|[CMFCRibbonEdit::OnKey](#onkey)|Wird vom Framework aufgerufen, wenn der Benutzer `CMFCRibbonEdit` eine Keytip drückt und das Steuerelement den Fokus hat.|
|[CMFCRibbonEdit::OnLButtondown](#onlbuttondown)|Wird vom Framework aufgerufen, um das `CMFCRibbonEdit` Steuerelement zu aktualisieren, wenn der Benutzer die linke Maustaste auf dem Steuerelement drückt.|
|[CMFCRibbonEdit::OnLButtonUp](#onlbuttonup)|Wird vom Framework aufgerufen, wenn der Benutzer die linke Maustaste loslässt.|
|[CMFCRibbonEdit::OnRTLChanged](#onrtlchanged)|Wird vom Framework aufgerufen, um das `CMFCRibbonEdit` Steuerelement zu aktualisieren, wenn das Layout die Richtung ändert.|
|[CMFCRibbonEdit::OnShow](#onshow)|Wird vom Framework aufgerufen, `CMFCRibbonEdit` um das Steuerelement ein- oder auszublenden.|
|[CMFCRibbonEdit::Neuzeichnen](#redraw)|Aktualisiert die Anzeige `CMFCRibbonEdit` des Steuerelements.|
|[CMFCRibbonEdit::SetACCData](#setaccdata)|Legt die Eingabehilfendaten `CMFCRibbonEdit` für das Objekt fest.|
|[CMFCRibbonEdit::SetEditText](#setedittext)|Legt den Text im Textfeld fest.|
|[CMFCRibbonEdit::SetTextAlign](#settextalign)|Legt die Textausrichtung des Textfelds fest.|
|[CMFCRibbonEdit::SetWidth](#setwidth)|Legt die Breite des Textfelds für das `CMFCRibbonEdit` Steuerelement fest.|

## <a name="remarks"></a>Bemerkungen

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird `CMFCRibbonEdit` veranschaulicht, wie Sie ein Objekt erstellen, Drehschaltflächen neben dem Bearbeitungssteuerelement anzeigen und den Text des Bearbeitungssteuerelements festlegen. Dieser Codeausschnitt ist Teil des [MS Office 2007-Demobeispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#7](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxRibbonEdit.h

## <a name="cmfcribboneditcanbestretched"></a><a name="canbestretched"></a>CMFCRibbonEdit::CanBeStretched

Gibt an, ob die Höhe des [CMFCRibbonEdit-Steuerelements](../../mfc/reference/cmfcribbonedit-class.md) vertikal auf die Höhe einer Multifunktionsleistenzeile erhöht werden kann.

```cpp
virtual BOOL CanBeStretched();
```

### <a name="return-value"></a>Rückgabewert

Gibt immer FALSE zurück.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboneditcmfcribbonedit"></a><a name="cmfcribbonedit"></a>CMFCRibbonBearbeiten::CMFCRibbonBearbeiten

Erstellt ein [CMFCRibbonEdit-Objekt.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
CMFCRibbonEdit(
    UINT nID,
    int nWidth,
    LPCTSTR lpszLabel = NULL,
    int nImage = -1);

CMFCRibbonEdit();
```

### <a name="parameters"></a>Parameter

*nID*<br/>
[in] Befehls-ID `CMFCRibbonEdit` für das Steuerelement.

*nWidth*<br/>
[in] Die Breite des Textfelds für das `CMFCRibbonEdit` Steuerelement in Pixel.

*lpszLabel*<br/>
[in] Die Bezeichnung `CMFCRibbonEdit` für das Steuerelement.

*nImage*<br/>
[in] Index des kleinen Bildes, `CMFCRibbonEdit` das für das Steuerelement verwendet werden soll. Die Sammlung kleiner Bilder wird von der übergeordneten Menübandkategorie verwaltet.

### <a name="remarks"></a>Bemerkungen

Das `CMFCRibbonEdit` Steuerelement verwendet kein großes Bild.

## <a name="cmfcribboneditcopyfrom"></a><a name="copyfrom"></a>CMFCRibbonEdit::CopyFrom

Kopiert den Status des angegebenen [CMFCRibbonEdit-Objekts](../../mfc/reference/cmfcribbonedit-class.md) in das aktuelle [CMFCRibbonEdit-Objekt.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Parameter

*src*<br/>
[in] Das `CMFCRibbonEdit` Quellobjekt.

### <a name="remarks"></a>Bemerkungen

Der *src-Parameter* muss `CMFCRibbonEdit`vom Typ sein.

## <a name="cmfcribboneditcreateedit"></a><a name="createedit"></a>CMFCRibbonEdit::CreateEdit

Erstellt ein neues Textfeld für das [CMFCRibbonEdit-Objekt.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>Parameter

*pWndParent*<br/>
[in] Ein Zeiger auf das übergeordnete `CMFCRibbonEdit` Fenster des Objekts.

*dwEditStyle*<br/>
[in] Gibt den Stil des Textfelds an. Sie können die im Abschnitt "Hinweise" aufgeführten Fensterstile mit den im Windows SDK beschriebenen [Bearbeitungssteuerelementstilen](/windows/win32/Controls/edit-control-styles) kombinieren.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das neue Textfeld, wenn die Methode erfolgreich war. andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um ein benutzerdefiniertes Textfeld zu erstellen.

Sie können die folgenden [Fensterformatvorlagen](../../mfc/reference/styles-used-by-mfc.md#window-styles) auf ein Textfeld anwenden:

- **Ws_child**

- **Ws_visible**

- **Ws_disabled**

- **WS_GROUP**

- **Ws_tabstop**

## <a name="cmfcribboneditdestroyctrl"></a><a name="destroyctrl"></a>CMFCRibbonBearbeiten::DestroyCtrl

Zerstört das [CMFCRibbonEdit-Objekt.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual void DestroyCtrl();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboneditdropdownlist"></a><a name="dropdownlist"></a>CMFCRibbonEdit::DropDownList

Löscht ein Listenfeld herunter.

```cpp
virtual void DropDownList();
```

### <a name="remarks"></a>Bemerkungen

Standardmäßig führt diese Methode nichts aus. Überschreiben Sie diese Methode, um ein Listenfeld herunterzufahren.

## <a name="cmfcribboneditenablespinbuttons"></a><a name="enablespinbuttons"></a>CMFCRibbonEdit::EnableSpinButtons

Aktiviert und legt den Bereich der Drehschaltfläche für das Textfeld fest.

```cpp
void EnableSpinButtons(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parameter

*Nmin*<br/>
[in] Der Mindestwert der Drehtaste.

*nMax*<br/>
[in] Der maximale Wert der Drehtaste.

### <a name="remarks"></a>Bemerkungen

Drehschaltflächen zeigen einen Auf- und Abwärtspfeil an und ermöglichen es Benutzern, sich durch einen festen Satz von Werten zu bewegen.

## <a name="cmfcribboneditgetcompactsize"></a><a name="getcompactsize"></a>CMFCRibbonEdit::GetCompactSize

Ruft die kompakte Größe des [CMFCRibbonEdit-Objekts](../../mfc/reference/cmfcribbonedit-class.md) ab.

```cpp
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Zeiger auf einen Gerätekontext `CMFCRibbonEdit` für das Objekt.

### <a name="return-value"></a>Rückgabewert

Die kompakte Größe `CMFCRibbonEdit` des Objekts.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboneditgetedittext"></a><a name="getedittext"></a>CMFCRibbonEdit::GetEditText

Ruft den Text im Textfeld ab.

```cpp
CString GetEditText() const;
```

### <a name="return-value"></a>Rückgabewert

Der Text im Textfeld.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboneditgetintermediatesize"></a><a name="getintermediatesize"></a>CMFCRibbonEdit::GetIntermediateSize

Ruft die Zwischengröße des [CMFCRibbonEdit-Objekts](../../mfc/reference/cmfcribbonedit-class.md) ab.

```cpp
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Zeiger auf einen Gerätekontext `CMFCRibbonEdit` für das Objekt.

### <a name="return-value"></a>Rückgabewert

Die Zwischengröße `CMFCRibbonEdit` des Objekts.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboneditgettextalign"></a><a name="gettextalign"></a>CMFCRibbonEdit::GetTextAlign

Ruft die Ausrichtung des Textes im Textfeld ab.

```cpp
int GetTextAlign() const;
```

### <a name="return-value"></a>Rückgabewert

Ein aufgezählter Wert für die Textausrichtung. Weitere Informationen zu möglichen Werten finden Sie im Abschnitt "Bemerkungen".

### <a name="remarks"></a>Bemerkungen

Der zurückgegebene Wert ist einer der folgenden Bearbeitungssteuerelementstile:

- **ES_LEFT** für die linke Ausrichtung

- **ES_CENTER** für die Ausrichtung des Mittelpunkts

- **ES_RIGHT** für die richtige Ausrichtung

Weitere Informationen zu diesen Stilen finden Sie unter Bearbeiten von [Steuerelementstilen](/windows/win32/Controls/edit-control-styles).

## <a name="cmfcribboneditgetwidth"></a><a name="getwidth"></a>CMFCRibbonEdit::GetWidth

Ruft die Breite des [CMFCRibbonEdit-Steuerelements](../../mfc/reference/cmfcribbonedit-class.md) in Pixel ab.

```cpp
int GetWidth(BOOL bInFloatyMode = FALSE) const;
```

### <a name="parameters"></a>Parameter

*bInFloatyMode*<br/>
[in] TRUE, `CMFCRibbonEdit` wenn sich das Steuerelement im floating-Modus befindet; andernfalls FALSE.

### <a name="return-value"></a>Rückgabewert

Die Breite des `CMFCRibbonEdit` Steuerelements in Pixel.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonedithascompactmode"></a><a name="hascompactmode"></a>CMFCRibbonEdit::HasCompactMode

Gibt an, ob die Anzeigegröße für das [CMFCRibbonEdit-Steuerelement](../../mfc/reference/cmfcribbonedit-class.md) kompakt sein kann.

```cpp
virtual BOOL HasCompactMode() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt immer TRUE zurück.

### <a name="remarks"></a>Bemerkungen

Standardmäßig gibt diese Methode immer TRUE zurück. Überschreiben Sie diese Methode, um anzugeben, ob die Anzeigegröße kompakt sein kann.

## <a name="cmfcribbonedithasfocus"></a><a name="hasfocus"></a>CMFCRibbonEdit::HasFocus

Gibt an, ob das [CMFCRibbonEdit-Steuerelement](../../mfc/reference/cmfcribbonedit-class.md) den Fokus hat.

```cpp
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, `CMFCRibbonEdit` wenn das Steuerelement den Fokus hat; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonedithaslargemode"></a><a name="haslargemode"></a>CMFCRibbonEdit::HasLargeMode

Gibt an, ob die Anzeigegröße für das [CMFCRibbonEdit-Steuerelement](../../mfc/reference/cmfcribbonedit-class.md) groß sein kann.

```cpp
virtual BOOL HasLargeMode() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt immer FALSE zurück.

### <a name="remarks"></a>Bemerkungen

Standardmäßig gibt diese Methode immer FALSE zurück. Überschreiben Sie diese Methode, um anzugeben, ob die Anzeigegröße groß sein kann.

## <a name="cmfcribbonedithasspinbuttons"></a><a name="hasspinbuttons"></a>CMFCRibbonEdit::HasSpinButtons

Gibt an, ob das Textfeld über eine Drehschaltfläche verfügt.

```cpp
virtual BOOL HasSpinButtons() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Textfeld über eine Drehschaltfläche verfügt; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboneditishighlighted"></a><a name="ishighlighted"></a>CMFCRibbonEdit::Hervorgehoben

Gibt an, ob das [CMFCRibbonEdit-Steuerelement](../../mfc/reference/cmfcribbonedit-class.md) hervorgehoben ist.

```cpp
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, `CMFCRibbonEdit` wenn das Steuerelement hervorgehoben wird; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboneditonafterchangerect"></a><a name="onafterchangerect"></a>CMFCRibbonEdit::OnAfterChangeRect

Wird vom Framework aufgerufen, wenn sich die Abmessungen des Anzeigerechtecks für das [CMFCRibbonEdit-Steuerelement](../../mfc/reference/cmfcribbonedit-class.md) ändern.

```cpp
virtual void OnAfterChangeRect(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Zeiger auf einen Gerätekontext `CMFCRibbonEdit` für das Steuerelement.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboneditondraw"></a><a name="ondraw"></a>CMFCRibbonEdit::OnDraw

Wird vom Framework aufgerufen, um das [CMFCRibbonEdit-Steuerelement](../../mfc/reference/cmfcribbonedit-class.md) zu zeichnen.

```cpp
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Zeiger auf einen Gerätekontext `CMFCRibbonEdit` für das Steuerelement.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboneditondrawlabelandimage"></a><a name="ondrawlabelandimage"></a>CMFCRibbonEdit::OnDrawLabelAndImage

Wird vom Framework aufgerufen, um die Beschriftung und das Image für das [CMFCRibbonEdit-Steuerelement](../../mfc/reference/cmfcribbonedit-class.md) zu zeichnen.

```cpp
virtual void OnDrawLabelAndImage(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Zeiger auf einen Gerätekontext `CMFCRibbonEdit` für das Steuerelement.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboneditondrawonlist"></a><a name="ondrawonlist"></a>CMFCRibbonEdit::OnDrawonList

Wird vom Framework aufgerufen, um das [CMFCRibbonEdit-Steuerelement](../../mfc/reference/cmfcribbonedit-class.md) in einem Befehlslistenfeld zu zeichnen.

```cpp
virtual void OnDrawOnList(
    CDC* pDC,
    CString strText,
    int nTextOffset,
    CRect rect,
    BOOL bIsSelected,
    BOOL bHighlighted);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Zeiger auf einen Gerätekontext `CMFCRibbonEdit` für das Steuerelement.

*strText*<br/>
[in] Der Anzeigetext [ ](../../mfc/reference/cmfcribbonedit-class.md "cmfcribbonedit-Klasse").

*nTextOffset*<br/>
[in] Entfernung in Pixel von der linken Seite des Listenfelds zum Anzeigetext.

*Rect*<br/>
[in] Das Anzeigerechteck `CMFCRibbonEdit` für das Steuerelement.

*bIsSelected*<br/>
[in] Dieser Parameter wird nicht verwendet.

*bHervorgehoben*<br/>
[in] Dieser Parameter wird nicht verwendet.

### <a name="remarks"></a>Bemerkungen

Im Feld Befehlslistenfeld werden Menübandsteuerelemente angezeigt, mit denen Benutzer die Symbolleiste für den Schnellzugriff anpassen können.

## <a name="cmfcribboneditonenable"></a><a name="onenable"></a>CMFCRibbonEdit::OnEnable

Wird vom Framework aufgerufen, um das [CMFCRibbonEdit-Steuerelement](../../mfc/reference/cmfcribbonedit-class.md) zu aktivieren oder zu deaktivieren.

```cpp
virtual void OnEnable(BOOL bEnable);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
[in] TRUE, um das Steuerelement zu aktivieren; FALSE, um das Steuerelement zu deaktivieren.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboneditonhighlight"></a><a name="onhighlight"></a>CMFCRibbonEdit::OnHighlight

Wird vom Framework aufgerufen, wenn der Zeiger die Grenzen des [CMFCRibbonEdit-Steuerelements](../../mfc/reference/cmfcribbonedit-class.md) ein- oder verlässt.

```cpp
virtual void OnHighlight(BOOL bHighlight);
```

### <a name="parameters"></a>Parameter

*bHighlight*<br/>
[in] TRUE, wenn sich der Zeiger in `CMFCRibbonEdit` den Grenzen des Steuerelements befindet; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboneditonkey"></a><a name="onkey"></a>CMFCRibbonEdit::OnKey

Wird vom Framework aufgerufen, wenn der Benutzer eine Keytip drückt und das [CMFCRibbonEdit-Steuerelement](../../mfc/reference/cmfcribbonedit-class.md) den Fokus hat.

```cpp
virtual BOOL OnKey(BOOL bIsMenuKey);
```

### <a name="parameters"></a>Parameter

*bIsMenuKey*<br/>
[in] TRUE, wenn der Keytip ein Popup-Menü anzeigt; andernfalls FALSE.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Ereignis behandelt wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboneditonlbuttondown"></a><a name="onlbuttondown"></a>CMFCRibbonEdit::OnLButtondown

Wird vom Framework aufgerufen, um das [CMFCRibbonEdit-Steuerelement](../../mfc/reference/cmfcribbonedit-class.md) zu aktualisieren, wenn der Benutzer die linke Maustaste auf dem Steuerelement drückt.

```cpp
virtual void OnLButtonDown(CPoint point);
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
[in] Dieser Parameter wird nicht verwendet.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboneditonlbuttonup"></a><a name="onlbuttonup"></a>CMFCRibbonEdit::OnLButtonUp

Wird vom Framework aufgerufen, wenn der Benutzer die linke Maustaste loslässt.

```cpp
virtual void OnLButtonUp(CPoint point);
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
[in] Dieser Parameter wird nicht verwendet.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboneditonrtlchanged"></a><a name="onrtlchanged"></a>CMFCRibbonEdit::OnRTLChanged

Wird vom Framework aufgerufen, um das [CMFCRibbonEdit-Steuerelement](../../mfc/reference/cmfcribbonedit-class.md) zu aktualisieren, wenn das Layout die Richtung ändert.

```cpp
virtual void OnRTLChanged(BOOL bIsRTL);
```

### <a name="parameters"></a>Parameter

*bIsRTL*<br/>
[in] TRUE, wenn das Layout von rechts nach links ist; FALSE, wenn das Layout von links nach rechts ist.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboneditonshow"></a><a name="onshow"></a>CMFCRibbonEdit::OnShow

Wird vom Framework aufgerufen, um das [CMFCRibbonEdit-Steuerelement](../../mfc/reference/cmfcribbonedit-class.md) ein- oder auszublenden.

```cpp
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parameter

*bShow*<br/>
[in] TRUE, um das Steuerelement anzuzeigen; FALSE, um das Steuerelement auszublenden.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboneditredraw"></a><a name="redraw"></a>CMFCRibbonEdit::Neuzeichnen

Aktualisiert die Anzeige des [CMFCRibbonEdit-Steuerelements.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual void Redraw();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode zeichnet das Anzeigerechteck für das `CMFCRibbonEdit` Objekt neu, indem [cWnd::RedrawWindow](/windows/win32/api/winuser/nf-winuser-redrawwindow) indirekt aufgerufen wird, wobei die RDW_INVALIDATE,RDW_ERASE und RDW_UPDATENOW Flags festgelegt sind.

## <a name="cmfcribboneditsetaccdata"></a><a name="setaccdata"></a>CMFCRibbonEdit::SetACCData

Legt die Eingabehilfendaten für das [CMFCRibbonEdit-Objekt](../../mfc/reference/cmfcribbonedit-class.md) fest.

```cpp
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parameter

*pParent*<br/>
Zeigen Sie mit dem `CMFCRibbonEdit` Zeiger auf das übergeordnete Fenster für das Objekt.

*Daten*<br/>
Die Eingabehilfendaten `CMFCRibbonEdit` für das Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt immer TRUE zurück.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboneditsetedittext"></a><a name="setedittext"></a>CMFCRibbonEdit::SetEditText

Legt den Text im Textfeld fest.

```cpp
void SetEditText(CString strText);
```

### <a name="parameters"></a>Parameter

*strText*<br/>
[in] Der Text für das Textfeld.

## <a name="cmfcribboneditsettextalign"></a><a name="settextalign"></a>CMFCRibbonEdit::SetTextAlign

Legt die Textausrichtung des Textfelds fest.

```cpp
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>Parameter

*nAlign*<br/>
[in] Ein aufgezählter Wert für die Textausrichtung. Weitere Informationen zu möglichen Werten finden Sie im Abschnitt "Bemerkungen".

### <a name="remarks"></a>Bemerkungen

Der Parameter *nAlign* ist einer der folgenden Bearbeitungssteuerelementstile:

- ES_LEFT für die linke Ausrichtung

- ES_CENTER für die Ausrichtung des Mittelpunkts

- ES_RIGHT für die richtige Ausrichtung

Weitere Informationen zu diesen Stilen finden Sie unter Bearbeiten von [Steuerelementstilen](/windows/win32/Controls/edit-control-styles).

## <a name="cmfcribboneditsetwidth"></a><a name="setwidth"></a>CMFCRibbonEdit::SetWidth

Legt die Breite des Textfelds für das [CMFCRibbonEdit-Steuerelement](../../mfc/reference/cmfcribbonedit-class.md) fest.

```cpp
void SetWidth(
    int nWidth,
    BOOL bInFloatyMode = FALSE);
```

### <a name="parameters"></a>Parameter

*nWidth*<br/>
[in] Die Breite des Textfelds in Pixel.

*bInFloatyMode*<br/>
TRUE, um die Breite für den floating-Modus festzulegen; FALSE, um die Breite für den regulären Modus festzulegen.

### <a name="remarks"></a>Bemerkungen

Das `CMFCRibbonEdit` Steuerelement hat je nach Anzeigemodus zwei Breiten: Floating-Modus und normaler Modus.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton-Klasse](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonBar-Klasse](../../mfc/reference/cmfcribbonbar-class.md)
