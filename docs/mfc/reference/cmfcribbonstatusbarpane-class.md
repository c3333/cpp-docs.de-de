---
title: CMFCRibbonStatusBarPane-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsExtended
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnDrawBorder
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFillBackground
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAnimationList
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StartAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StopAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFinishAnimation
helpviewer_keywords:
- CMFCRibbonStatusBarPane [MFC], CMFCRibbonStatusBarPane
- CMFCRibbonStatusBarPane [MFC], GetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], GetTextAlign
- CMFCRibbonStatusBarPane [MFC], IsAnimation
- CMFCRibbonStatusBarPane [MFC], IsExtended
- CMFCRibbonStatusBarPane [MFC], OnDrawBorder
- CMFCRibbonStatusBarPane [MFC], OnFillBackground
- CMFCRibbonStatusBarPane [MFC], SetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], SetAnimationList
- CMFCRibbonStatusBarPane [MFC], SetTextAlign
- CMFCRibbonStatusBarPane [MFC], StartAnimation
- CMFCRibbonStatusBarPane [MFC], StopAnimation
- CMFCRibbonStatusBarPane [MFC], OnFinishAnimation
ms.assetid: 5d034c3c-ecca-4267-b88c-0f55a2884dd0
ms.openlocfilehash: bb4e09eabab17061812ed22b2739d06accd57fee
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753505"
---
# <a name="cmfcribbonstatusbarpane-class"></a>CMFCRibbonStatusBarPane-Klasse

Die `CMFCRibbonStatusBarPane` Klasse implementiert ein Multifunktionsleistenelement, das Sie einer Multifunktionsleistenstatusleiste hinzufügen können.

## <a name="syntax"></a>Syntax

```
class CMFCRibbonStatusBarPane : public CMFCRibbonButton
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane](#cmfcribbonstatusbarpane)|Erstellt und initialisiert ein `CMFCRibbonStatusBarPane`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonStatusBarPane::GetalmostLargeText](#getalmostlargetext)|Gibt die Zeichenfolge zurück, die die längste Textzeichenfolge definiert, die im Bereich ohne Abschneiden angezeigt werden kann.|
|[CMFCRibbonStatusBarPane::GetTextAlign](#gettextalign)|Gibt die aktuelle Einstellung der Textausrichtung zurück.|
|[CMFCRibbonStatusBarPane::IsAnimation](#isanimation)|Bestimmt, ob die Animation ausgeführt wird.|
|[CMFCRibbonStatusBarPane::IsExtended](#isextended)|Bestimmt, ob sich der Bereich im erweiterten Bereich der Multifunktionsleisten-Statusleiste befindet.|
|[CMFCRibbonStatusbarPane::OnDrawBorder](#ondrawborder)|(Überschreibt [CMFCRibbonButton::OnDrawBorder](../../mfc/reference/cmfcribbonbutton-class.md#ondrawborder).)|
|[CMFCRibbonStatusBarPane::OnFillBackground](#onfillbackground)|(Überschreibt [CMFCRibbonButton::OnFillBackground](../../mfc/reference/cmfcribbonbutton-class.md#onfillbackground).)|
|[CMFCRibbonStatusBarPane::SetAlmostLargeText](#setalmostlargetext)|Definiert die längste Textzeichenfolge, die ohne Abschneide im Bereich angezeigt werden kann.|
|[CMFCRibbonStatusBarPane::SetAnimationList](#setanimationlist)|Weist dem Bereich eine Bildliste zu, die für Animationen verwendet werden kann.|
|[CMFCRibbonStatusBarPane::SetTextAlign](#settextalign)|Legt die Textausrichtung fest.|
|[CMFCRibbonStatusBarPane::StartAnimation](#startanimation)|Startet die Animation, die dem Bereich zugewiesen ist.|
|[CMFCRibbonStatusBarPane::StopAnimation](#stopanimation)|Beendet die Animation, die dem Bereich zugewiesen ist. .|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonStatusBarPane::OnFinishAnimation](#onfinishanimation)|Wird vom Framework aufgerufen, wenn die Animation, die dem Bereich zugewiesen ist, beendet wird.|

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Verwendung der unterschiedlichen Methoden in der `CMFCRibbonStatusBarPane`-Klasse veranschaulicht. Das Beispiel zeigt, `CMFCRibbonStatusBarPane` wie Sie ein Objekt erstellen, die Textausrichtung der Beschriftung des Statusleistenbereichs festlegen, den längsten Text definieren, der im Statusleistenbereich ohne Abschneiden angezeigt werden kann, an den Statusleistenbereich eine Bildliste anfügen, die für Animationen verwendet werden kann, und die Animation starten.

[!code-cpp[NVC_MFC_RibbonApp#2](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbarpane-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxribbonstatusbarpane.h

## <a name="cmfcribbonstatusbarpanecmfcribbonstatusbarpane"></a><a name="cmfcribbonstatusbarpane"></a>CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane

Erstellen Sie ein Bereichsobjekt in der Statusleiste.

```
CMFCRibbonStatusBarPane(
    UINT nCmdID,
    LPCTSTR lpszText,
    BOOL bIsStatic=FALSE,
    HICON hIcon=NULL,
    LPCTSTR lpszAlmostLargeText=NULL);

CMFCRibbonStatusBarPane(
    UINT nCmdID,
    LPCTSTR lpszText,
    HBITMAP hBmpAnimationList,
    int cxAnimation=16,
    COLORREF clrTrnsp=RGB(192,192 1,192) 1,
    HICON hIcon=NULL,
    BOOL bIsStatic=FALSE);

CMFCRibbonStatusBarPane(
    UINT nCmdID,
    LPCTSTR lpszText,
    UINT uiAnimationListResID,
    int cxAnimation=16,
    COLORREF clrTrnsp=RGB(192, 192 1, 192) 1,
    HICON hIcon=NULL,
    BOOL bIsStatic=FALSE);
```

### <a name="parameters"></a>Parameter

*nCmdID*<br/>
[in] Gibt die Befehls-ID des Bereichs an.

*lpszText*<br/>
[in] Gibt textzeichenfolge an, die im Bereich angezeigt werden soll.

*bIsStatic*<br/>
[in] Wenn TRUE, kann der Statusbereich nicht hervorgehoben oder ausgewählt werden, indem Sie darauf klicken.

*hIcon*<br/>
[in] Gibt ein Handle für ein Symbol an, das im Bereich angezeigt werden soll.

*lpszAlmostLargeText*<br/>
[in] Gibt die längste Textzeichenfolge an, die vom Bereich angezeigt werden kann.

*hBmpAnimationList*<br/>
[in] Gibt ein Handle für eine Bildliste an, die für Animationen verwendet wird.

*cxAnimation*<br/>
[in] Gibt die Breite des Symbols in der Bildliste, die für Animationen verwendet wird, in Pixel an.

*clrTrnsp*<br/>
[in] Gibt die transparente Farbe von Bildern in der Bildliste an, die für Animationen verwendet werden.

*uiAnimationListResID*<br/>
[in] Gibt eine Ressourcen-ID einer Bildliste an, die für Animationen verwendet wird.

## <a name="cmfcribbonstatusbarpanegetalmostlargetext"></a><a name="getalmostlargetext"></a>CMFCRibbonStatusBarPane::GetalmostLargeText

Ruft die längste Textzeichenfolge ab, die im Statusleistenbereich angezeigt werden kann.

```
LPCTSTR GetAlmostLargeText() const;
```

### <a name="return-value"></a>Rückgabewert

Die längste Textzeichenfolge, die im Statusleistenbereich angezeigt werden kann.

## <a name="cmfcribbonstatusbarpanegettextalign"></a><a name="gettextalign"></a>CMFCRibbonStatusBarPane::GetTextAlign

Ruft die aktuelle Einstellung der Textausrichtung der Beschriftung des Statusleistenbereichs ab.

```
int GetTextAlign() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Textausrichtung, die eine der folgenden sein kann:

- TA_LEFT

- TA_CENTER

- TA_RIGHT.

## <a name="cmfcribbonstatusbarpaneisanimation"></a><a name="isanimation"></a>CMFCRibbonStatusBarPane::IsAnimation

Bestimmt, ob die Animation ausgeführt wird.

```
BOOL IsAnimation() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn animationiert wird; FALSE sonst.

## <a name="cmfcribbonstatusbarpaneisextended"></a><a name="isextended"></a>CMFCRibbonStatusBarPane::IsExtended

Bestimmen Sie, ob sich der Bereich im erweiterten Bereich der Multifunktionsleisten-Statusleiste befindet.

```
BOOL IsExtended() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn sich der Bereich im erweiterten Bereich der Statusleiste befindet. FALSE sonst.

## <a name="cmfcribbonstatusbarpaneondrawborder"></a><a name="ondrawborder"></a>CMFCRibbonStatusbarPane::OnDrawBorder

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

```
virtual void OnDrawBorder(CDC*);
```

### <a name="parameters"></a>Parameter

[in] *CDC&#42;*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonstatusbarpaneonfillbackground"></a><a name="onfillbackground"></a>CMFCRibbonStatusBarPane::OnFillBackground

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

```
virtual COLORREF OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>Parameter

[in] *pDC*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonstatusbarpaneonfinishanimation"></a><a name="onfinishanimation"></a>CMFCRibbonStatusBarPane::OnFinishAnimation

Framework ruft diese Methode auf, wenn die Animation, die dem Bereich zugewiesen ist, endet.

```
virtual void OnFinishAnimation();
```

### <a name="remarks"></a>Bemerkungen

`StopAnimation`Methode ruft `OnFinishAnimation` die Methode auf, die Sie verwenden können, um Daten zu bereinigen, wenn die Animation endet.

## <a name="cmfcribbonstatusbarpanesetalmostlargetext"></a><a name="setalmostlargetext"></a>CMFCRibbonStatusBarPane::SetAlmostLargeText

Definieren Sie den längsten Text, der im Statusleistenbereich ohne Abschneide angezeigt werden kann.

```cpp
void SetAlmostLargeText(LPCTSTR lpszAlmostLargeText);
```

### <a name="parameters"></a>Parameter

*lpszAlmostLargeText*<br/>
[in] Gibt die längste Zeichenfolge an, die im Statusleistenbereich ohne Abschneide angezeigt werden kann.

### <a name="remarks"></a>Bemerkungen

Die Bibliothek berechnet die Größe des Textes, die *lpszAlmostLargeText* angibt, und ändert die Größe des Bereichs entsprechend. Der Text wird abgeschnitten, wenn er immer noch nicht in den Bereich passt.

## <a name="cmfcribbonstatusbarpanesetanimationlist"></a><a name="setanimationlist"></a>CMFCRibbonStatusBarPane::SetAnimationList

Fügt dem Statusleistenbereich eine Bildliste an, die für Animationen verwendet werden kann.

```cpp
void SetAnimationList(
    HBITMAP hBmpAnimationList,
    int cxAnimation=16,
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);

BOOL SetAnimationList(
    UINT uiAnimationListResID,
    int cxAnimation=16,
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);
```

### <a name="parameters"></a>Parameter

*hBmpAnimationList*<br/>
[in] Gibt ein Handle für eine Bildliste an.

*cxAnimation*<br/>
[in] Gibt die Breite des Rahmens in der Bildliste in Pixel an.

*clrTransp*<br/>
[in] Gibt die transparente Farbe der Bildliste an.

*uiAnimationListResID*<br/>
[in] Gibt die Ressourcen-ID der Bildliste an.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Bildliste erfolgreich an den Statusleistenbereich angefügt wurde; FALSE sonst.

## <a name="cmfcribbonstatusbarpanesettextalign"></a><a name="settextalign"></a>CMFCRibbonStatusBarPane::SetTextAlign

Legt die Textausrichtung der Beschriftung des Statusleistenbereichs fest.

```cpp
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>Parameter

*nAlign*<br/>
[in] Gibt die Textausrichtung an.

### <a name="remarks"></a>Bemerkungen

*nAlign* kann einen der folgenden Werte haben:

- TA_LEFT: linke Ausrichtung

- TA_CENTER: Mittelausrichtung

- TA_RIGHT: rechte Ausrichtung

## <a name="cmfcribbonstatusbarpanestartanimation"></a><a name="startanimation"></a>CMFCRibbonStatusBarPane::StartAnimation

Startet die Animation, die Sie dem Bereich zuweisen.

```cpp
void StartAnimation(
    UINT nFrameDelay=500,
    UINT nDuration=-1);
```

### <a name="parameters"></a>Parameter

*nFrameDelay*<br/>
[in] Gibt die Animationsbildrate in Millisekunden an.

*nDuration*<br/>
[in] Gibt an, wie lange die Animation in Millisekunden wiedergegeben werden soll. Verwenden Sie -1 für eine Endlosschleife.

### <a name="remarks"></a>Bemerkungen

Sie müssen ein Handle für eine `StartAnimation` Bildliste `SetAnimationList`angeben, bevor Sie mit aufrufen.

## <a name="cmfcribbonstatusbarpanestopanimation"></a><a name="stopanimation"></a>CMFCRibbonStatusBarPane::StopAnimation

Beendet die Animation, die Sie dem Statusleistenbereich zugewiesen haben.

```cpp
void StopAnimation();
```

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton-Klasse](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonStatusBar-Klasse](../../mfc/reference/cmfcribbonstatusbar-class.md)
