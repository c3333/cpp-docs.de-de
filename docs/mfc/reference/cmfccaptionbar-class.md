---
title: CMFCCaptionBar-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar::Create
- AFXCAPTIONBAR/CMFCCaptionBar::DoesAllowDynInsertBefore
- AFXCAPTIONBAR/CMFCCaptionBar::EnableButton
- AFXCAPTIONBAR/CMFCCaptionBar::GetAlignment
- AFXCAPTIONBAR/CMFCCaptionBar::GetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::GetButtonRect
- AFXCAPTIONBAR/CMFCCaptionBar::GetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::IsMessageBarMode
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveButton
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveIcon
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveText
- AFXCAPTIONBAR/CMFCCaptionBar::SetBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::SetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::SetButton
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonPressed
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetFlatBorder
- AFXCAPTIONBAR/CMFCCaptionBar::SetIcon
- AFXCAPTIONBAR/CMFCCaptionBar::SetImageToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::SetText
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBackground
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBorder
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawButton
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawImage
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawText
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBackground
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBorder
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarText
helpviewer_keywords:
- CMFCCaptionBar [MFC], Create
- CMFCCaptionBar [MFC], DoesAllowDynInsertBefore
- CMFCCaptionBar [MFC], EnableButton
- CMFCCaptionBar [MFC], GetAlignment
- CMFCCaptionBar [MFC], GetBorderSize
- CMFCCaptionBar [MFC], GetButtonRect
- CMFCCaptionBar [MFC], GetMargin
- CMFCCaptionBar [MFC], IsMessageBarMode
- CMFCCaptionBar [MFC], RemoveBitmap
- CMFCCaptionBar [MFC], RemoveButton
- CMFCCaptionBar [MFC], RemoveIcon
- CMFCCaptionBar [MFC], RemoveText
- CMFCCaptionBar [MFC], SetBitmap
- CMFCCaptionBar [MFC], SetBorderSize
- CMFCCaptionBar [MFC], SetButton
- CMFCCaptionBar [MFC], SetButtonPressed
- CMFCCaptionBar [MFC], SetButtonToolTip
- CMFCCaptionBar [MFC], SetFlatBorder
- CMFCCaptionBar [MFC], SetIcon
- CMFCCaptionBar [MFC], SetImageToolTip
- CMFCCaptionBar [MFC], SetMargin
- CMFCCaptionBar [MFC], SetText
- CMFCCaptionBar [MFC], OnDrawBackground
- CMFCCaptionBar [MFC], OnDrawBorder
- CMFCCaptionBar [MFC], OnDrawButton
- CMFCCaptionBar [MFC], OnDrawImage
- CMFCCaptionBar [MFC], OnDrawText
- CMFCCaptionBar [MFC], m_clrBarBackground
- CMFCCaptionBar [MFC], m_clrBarBorder
- CMFCCaptionBar [MFC], m_clrBarText
ms.assetid: acb54d5f-14ff-4c96-aeb3-7717cf566d9a
ms.openlocfilehash: 3a1e8890176fe686b54fe4756dfd578869cbcdfb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367798"
---
# <a name="cmfccaptionbar-class"></a>CMFCCaptionBar-Klasse

Ein `CMFCCaptionBar` Objekt ist eine Steuerleiste, die drei Elemente anzeigen kann: eine Schaltfläche, eine Textbeschriftung und eine Bitmap. Es kann jeweils nur ein Element eines Typs angezeigt werden. Sie können jedes Element links, rechts oder in der Mitte des Steuerelements positionieren. Sie können zudem den oberen und unteren Rand der Titelleiste flach oder dreidimensional darstellen.

## <a name="syntax"></a>Syntax

```
class CMFCCaptionBar : public CPane
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCCaptionBar::Erstellen](#create)|Erstellt das Beschriftungsleistensteuerelement und `CMFCCaptionBar` fügt es an das Objekt an.|
|[CMFCCaptionBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Gibt an, ob ein anderer Bereich dynamisch zwischen der Beschriftungsleiste und dem übergeordneten Rahmen eingefügt werden kann. (Überschreibt [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CMFCCaptionBar::EnableButton](#enablebutton)|Aktiviert oder deaktiviert die Schaltfläche in der Beschriftungsleiste.|
|[CMFCCaptionBar::GetAlignment](#getalignment)|Gibt die Ausrichtung des angegebenen Elements zurück.|
|[CMFCCaptionBar::GetBorderSize](#getbordersize)|Gibt die Rahmengröße der Beschriftungsleiste zurück.|
|[CMFCCaptionBar::GetButtonRect](#getbuttonrect)|Ruft das umgrenzende Rechteck der Schaltfläche auf der Beschriftungsleiste ab.|
|[CMFCCaptionBar::GetMargin](#getmargin)|Gibt den Abstand zwischen dem Rand der Beschriftungsleistenelemente und dem Rand des Beschriftungsleistensteuerelements zurück.|
|[CMFCCaptionBar::IsMessageBarMode](#ismessagebarmode)|Gibt an, ob sich die Beschriftungsleiste im Nachrichtenleistenmodus befindet.|
|[CMFCCaptionBar::RemoveBitmap](#removebitmap)|Entfernt das Bitmapbild aus der Beschriftungsleiste.|
|[CMFCCaptionBar::RemoveButton](#removebutton)|Entfernt die Schaltfläche aus der Beschriftungsleiste.|
|[CMFCCaptionBar::RemoveIcon](#removeicon)|Entfernt das Symbol aus der Beschriftungsleiste.|
|[CMFCCaptionBar::RemoveText](#removetext)|Entfernt die Textbeschriftung aus der Beschriftungsleiste.|
|[CMFCCaptionBar::SetBitmap](#setbitmap)|Legt das Bitmapbild für die Beschriftungsleiste fest.|
|[CMFCCaptionBar::SetBorderSize](#setbordersize)|Legt die Rahmengröße der Beschriftungsleiste fest.|
|[CMFCCaptionBar::SetButton](#setbutton)|Legt die Schaltfläche für die Beschriftungsleiste fest.|
|[CMFCCaptionBar::SetButtonPressed](#setbuttonpressed)|Gibt an, ob die Taste gedrückt bleibt.|
|[CMFCCaptionBar::SetButtonToolTip](#setbuttontooltip)|Legt die QuickInfo für die Schaltfläche fest.|
|[CMFCCaptionBar::SetFlatBorder](#setflatborder)|Legt den Rahmenstil der Beschriftungsleiste fest.|
|[CMFCCaptionBar::SetIcon](#seticon)|Legt das Symbol für eine Beschriftungsleiste fest.|
|[CMFCCaptionBar::SetImageToolTip](#setimagetooltip)|Legt die QuickInfo für das Bild für die Beschriftungsleiste fest.|
|[CMFCCaptionBar::SetMargin](#setmargin)|Legt den Abstand zwischen der Kante des Beschriftungsbalkenelements und dem Rand des Beschriftungsleistensteuerelements fest.|
|[CMFCCaptionBar::SetText](#settext)|Legt die Textbeschriftung für die Beschriftungsleiste fest.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCCaptionBar::OnDrawBackground](#ondrawbackground)|Wird vom Framework aufgerufen, um den Hintergrund der Beschriftungsleiste zu füllen.|
|[CMFCCaptionBar::OnDrawBorder](#ondrawborder)|Wird vom Framework aufgerufen, um den Rahmen der Beschriftungsleiste zu zeichnen.|
|[CMFCCaptionBar::OnDrawButton](#ondrawbutton)|Wird vom Framework aufgerufen, um die Beschriftungsleistenschaltfläche zu zeichnen.|
|[CMFCCaptionBar::OnDrawImage](#ondrawimage)|Wird vom Framework aufgerufen, um das Beschriftungsbalkenbild zu zeichnen.|
|[CMFCCaptionBar::OnDrawText](#ondrawtext)|Wird vom Framework aufgerufen, um den Beschriftungsbalkentext zu zeichnen.|

### <a name="data-members"></a>Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground)|Die Hintergrundfarbe der Beschriftungsleiste.|
|[CMFCCaptionBar::m_clrBarBorder](#m_clrbarborder)|Die Farbe des Rahmens der Beschriftungsleiste.|
|[CMFCCaptionBar::m_clrBarText](#m_clrbartext)|Die Farbe des Beschriftungsbalkentexts.|

## <a name="remarks"></a>Bemerkungen

Führen Sie die folgenden Schritte aus, um eine Beschriftungsleiste zu erstellen:

1. Erstellen `CMFCCaptionBar` Sie das Objekt. In der Regel fügen Sie die Beschriftungsleiste einer Rahmenfensterklasse hinzu.

1. Rufen Sie die [CMFCCaptionBar::Create-Methode](#create) auf, um `CMFCCaptionBar` das Beschriftungsleistensteuerelement zu erstellen und es an das Objekt anzufügen.

1. Rufen Sie [CMFCCaptionBar::SetButton](#setbutton), [CMFCCaptionBar::SetText](#settext), [CMFCCaptionBar::SetIcon](#seticon)und [CMFCCaptionBar::SetBitmap](#setbitmap) auf, um die Beschriftungsleistenelemente festzulegen.

Wenn Sie das Schaltflächenelement festlegen, müssen Sie der Schaltfläche eine Befehls-ID zuweisen. Wenn der Benutzer auf die Schaltfläche klickt, leitet die Beschriftungsleiste die WM_COMMAND Nachrichten mit dieser ID an das übergeordnete Rahmenfenster weiter.

Die Beschriftungsleiste kann auch im Nachrichtenleistenmodus funktionieren, der die Nachrichtenleiste emuliert, die in Microsoft Office 2007-Anwendungen angezeigt wird. Im Nachrichtenleistenmodus zeigt die Beschriftungsleiste eine Bitmap, eine Nachricht und eine Schaltfläche an (die normalerweise ein Dialogfeld öffnet). Sie können der Bitmap eine QuickInfo zuweisen.

Um den Nachrichtenleistenmodus zu aktivieren, rufen Sie [CMFCCaptionBar::Create](#create) auf und legen Sie den vierten Parameter (bIsMessageBarMode) auf TRUE fest.

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung verschiedener Methoden in der `CMFCCaptionBar` -Klasse. Das Beispiel zeigt, wie Sie das Beschriftungsleistensteuerelement erstellen, einen 3D-Rahmen der Beschriftungsleiste festlegen, den Abstand in Pixel zwischen dem Rand der Beschriftungsleistenelemente und dem Rand des Beschriftungsleistensteuerelements festlegen, die Schaltfläche für die Beschriftungsleiste festlegen, die QuickInfo für die Schaltfläche festlegen, die Textbeschriftung für die Beschriftungsleiste festlegen, das Bitmapbild für die Beschriftungsleiste festlegen. , und legen Sie die QuickInfo für das Bild in der Beschriftungsleiste fest. Dieser Codeausschnitt ist Teil des [MS Office 2007-Demobeispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#1](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_1.h)]
[!code-cpp[NVC_MFC_MSOffice2007Demo#2](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCCaptionBar](../../mfc/reference/cmfccaptionbar-class.md)

## <a name="requirements"></a>Anforderungen

**Kopf:** afxcaptionbar.h

## <a name="cmfccaptionbarcreate"></a><a name="create"></a>CMFCCaptionBar::Erstellen

Erstellt das Beschriftungsleistensteuerelement und `CMFCCaptionBar` fügt es an das Objekt an.

```
BOOL Create(
    DWORD dwStyle,
    CWnd* pParentWnd,
    UINT uID,
    int nHeight=-1,
    BOOL bIsMessageBarMode=FALSE);
```

### <a name="parameters"></a>Parameter

*dwStyle*<br/>
Die logische ODER-Kombination der Beschriftungsleistenstile.

*pParentWnd*<br/>
Das übergeordnete Fenster des Beschriftungsleistensteuerelements.

*Uid*<br/>
Die ID des Beschriftungsbalkensteuerelements.

*nHeight*<br/>
Die Höhe des Beschriftungsleistensteuerelements in Pixel. Wenn es -1 ist, wird die Höhe entsprechend der Höhe des Symbols, des Textes und der Schaltfläche berechnet, die das Beschriftungsleistensteuerelement anzeigt.

*bIsMessageBarMode*<br/>
TRUE, wenn sich die Beschriftungsleiste im Nachrichtenleistenmodus befindet; FALSE sonst.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Beschriftungsleistensteuerelement erfolgreich erstellt wurde; FALSE sonst.

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CMFCCaptionBar` ein Objekt in zwei Schritten. Zuerst rufen Sie den Konstruktor auf, dann die `Create` Methode, die das `CMFCCaptionBar` Windows-Steuerelement erstellt und an das Objekt anfügt.

## <a name="cmfccaptionbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CMFCCaptionBar::DoesAllowDynInsertBefore

Gibt an, ob ein anderer Bereich dynamisch zwischen der Beschriftungsleiste und dem übergeordneten Rahmen eingefügt werden kann.

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt FALSE zurück, es sei denn, es wird überschrieben.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccaptionbarenablebutton"></a><a name="enablebutton"></a>CMFCCaptionBar::EnableButton

Aktiviert oder deaktiviert die Schaltfläche in der Beschriftungsleiste.

```
void EnableButton(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
[in] TRUE, um die Schaltfläche zu aktivieren, FALSE, um die Schaltfläche zu deaktivieren.

## <a name="cmfccaptionbargetalignment"></a><a name="getalignment"></a>CMFCCaptionBar::GetAlignment

Gibt die Ausrichtung des angegebenen Elements zurück.

```
BarElementAlignment GetAlignment(BarElement elem);
```

### <a name="parameters"></a>Parameter

*Elem*<br/>
[in] Ein Beschriftungsbalkenelement, für das die Ausrichtung abgerufen werden soll.

### <a name="return-value"></a>Rückgabewert

Die Ausrichtung eines Elements, z. B. einer Schaltfläche, einer Bitmap, eines Textes oder eines Symbols.

### <a name="remarks"></a>Bemerkungen

Die Ausrichtung des Elements kann einer der folgenden Werte sein:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbargetbordersize"></a><a name="getbordersize"></a>CMFCCaptionBar::GetBorderSize

Gibt die Rahmengröße der Beschriftungsleiste zurück.

```
int GetBorderSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Größe des Rahmens in Pixel.

## <a name="cmfccaptionbargetbuttonrect"></a><a name="getbuttonrect"></a>CMFCCaptionBar::GetButtonRect

Ruft das umgrenzende Rechteck der Schaltfläche auf der Beschriftungsleiste ab.

```
CRect GetButtonRect() const;
```

### <a name="return-value"></a>Rückgabewert

Ein `CRect` Objekt, das die Koordinaten des umhängenden Rechtecks der Schaltfläche auf der Beschriftungsleiste enthält.

## <a name="cmfccaptionbargetmargin"></a><a name="getmargin"></a>CMFCCaptionBar::GetMargin

Gibt den Abstand zwischen dem Rand der Beschriftungsleistenelemente und dem Rand des Beschriftungsleistensteuerelements zurück.

```
int GetMargin() const;
```

### <a name="return-value"></a>Rückgabewert

Der Abstand (in Pixel) zwischen dem Rand der Beschriftungsleistenelemente und dem Rand des Beschriftungsleistensteuerelements.

## <a name="cmfccaptionbarismessagebarmode"></a><a name="ismessagebarmode"></a>CMFCCaptionBar::IsMessageBarMode

Gibt an, ob sich die Beschriftungsleiste im Nachrichtenleistenmodus befindet.

```
BOOL IsMessageBarMode() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn sich die Beschriftungsleiste im Nachrichtenleistenmodus befindet; FALSE sonst.

### <a name="remarks"></a>Bemerkungen

Im Nachrichtenleistenmodus zeigt die Beschriftungsleiste ein Bild mit einer QuickInfo, einem Nachrichtentext und einer Schaltfläche an.

## <a name="cmfccaptionbarm_clrbarbackground"></a><a name="m_clrbarbackground"></a>CMFCCaptionBar::m_clrBarBackground

Die Hintergrundfarbe der Beschriftungsleiste.

```
COLORREF m_clrBarBackground
```

## <a name="cmfccaptionbarm_clrbarborder"></a><a name="m_clrbarborder"></a>CMFCCaptionBar::m_clrBarBorder

Die Farbe des Rahmens der Beschriftungsleiste.

```
COLORREF m_clrBarBorder
```

## <a name="cmfccaptionbarm_clrbartext"></a><a name="m_clrbartext"></a>CMFCCaptionBar::m_clrBarText

Die Farbe des Beschriftungsbalkentexts.

```
COLORREF m_clrBarText
```

## <a name="cmfccaptionbarondrawbackground"></a><a name="ondrawbackground"></a>CMFCCaptionBar::OnDrawBackground

Wird vom Framework aufgerufen, um den Hintergrund der Beschriftungsleiste zu füllen.

```
virtual void OnDrawBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf den Gerätekontext der Beschriftungsleiste.

*Rect*<br/>
[in] Das zu füllende umschließende Rechteck.

### <a name="remarks"></a>Bemerkungen

Die `OnDrawBackground` Methode wird aufgerufen, wenn der Hintergrund der Beschriftungsleiste gefüllt werden soll. Die Standardimplementierung füllt den Hintergrund mit der [CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground) Farbe.

Überschreiben Sie diese `CMFCCaptionBar` Methode in einer abgeleiteten Klasse, um die Darstellung der Beschriftungsleiste anzupassen.

## <a name="cmfccaptionbarondrawborder"></a><a name="ondrawborder"></a>CMFCCaptionBar::OnDrawBorder

Wird vom Framework aufgerufen, um den Rahmen der Beschriftungsleiste zu zeichnen.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Gerätekontext, der zum Anzeigen der Rahmen verwendet wird.

*Rect*<br/>
[in] Das umgrenzende Rechteck.

### <a name="remarks"></a>Bemerkungen

Standardmäßig haben die Rahmen den flachen Stil.

Überschreiben Sie diese `CMFCCaptionBar` Methode in einer abgeleiteten Klasse, um die Darstellung der Ränder der Beschriftungsleiste anzupassen.

## <a name="cmfccaptionbarondrawbutton"></a><a name="ondrawbutton"></a>CMFCCaptionBar::OnDrawButton

Wird vom Framework aufgerufen, um die Beschriftungsleistenschaltfläche zu zeichnen.

```
virtual void OnDrawButton(
    CDC* pDC,
    CRect rect,
    const CString& strButton,
    BOOL bEnabled);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext, der zum Anzeigen der Schaltfläche verwendet wird.

*Rect*<br/>
[in] Das umgrenzende Rechteck der Schaltfläche.

*strButton*<br/>
[in] Die Textbeschriftung der Schaltfläche.

*bAktiviert*<br/>
[in] TRUE, wenn die Schaltfläche aktiviert ist; FALSE sonst.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese `CMFCCaptionBar` Methode in einer abgeleiteten Klasse, um die Darstellung der Beschriftungsleiste anzupassen.

## <a name="cmfccaptionbarondrawimage"></a><a name="ondrawimage"></a>CMFCCaptionBar::OnDrawImage

Wird vom Framework aufgerufen, um das Beschriftungsbalkenbild zu zeichnen.

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext, der zum Anzeigen des Bildes verwendet wird.

*Rect*<br/>
[in] Gibt das umgrenzende Rechteck des Bildes an.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese `CMFCCaptionBar` Methode in einer abgeleiteten Klasse, um die Bilddarstellung anzupassen.

## <a name="cmfccaptionbarondrawtext"></a><a name="ondrawtext"></a>CMFCCaptionBar::OnDrawText

Wird vom Framework aufgerufen, um den Beschriftungsbalkentext zu zeichnen.

```
virtual void OnDrawText(
    CDC* pDC,
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext, der zum Anzeigen der Schaltfläche verwendet wird.

*Rect*<br/>
[in] Das umgrenzende Rechteck des Textes.

*strText*<br/>
[in] Die anzuzeigende Textzeichenfolge.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung zeigt den `CDC::DrawText` Text mithilfe von [CMFCCaptionBar::m_clrBarText](#m_clrbartext) Farbe an.

Überschreiben Sie diese `CMFCCaptionBar` Methode in einer abgeleiteten Klasse, um die Darstellung des Texts der Beschriftungsleiste anzupassen.

## <a name="cmfccaptionbarremovebitmap"></a><a name="removebitmap"></a>CMFCCaptionBar::RemoveBitmap

Entfernt das Bitmapbild aus der Beschriftungsleiste.

```
void RemoveBitmap();
```

## <a name="cmfccaptionbarremovebutton"></a><a name="removebutton"></a>CMFCCaptionBar::RemoveButton

Entfernt die Schaltfläche aus der Beschriftungsleiste.

```
void RemoveButton();
```

### <a name="remarks"></a>Bemerkungen

Das Layout der Beschriftungsleistenelemente wird automatisch angepasst.

## <a name="cmfccaptionbarremoveicon"></a><a name="removeicon"></a>CMFCCaptionBar::RemoveIcon

Entfernt das Symbol aus der Beschriftungsleiste.

```
void RemoveIcon();
```

## <a name="cmfccaptionbarremovetext"></a><a name="removetext"></a>CMFCCaptionBar::RemoveText

Entfernt die Textbeschriftung aus der Beschriftungsleiste.

```
void RemoveText();
```

## <a name="cmfccaptionbarsetbitmap"></a><a name="setbitmap"></a>CMFCCaptionBar::SetBitmap

Legt das Bitmapbild für die Beschriftungsleiste fest.

```
void SetBitmap(
    HBITMAP hBitmap,
    COLORREF clrTransparent,
    BOOL bStretch=FALSE,
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);

void SetBitmap(
    UINT uiBmpResID,
    COLORREF clrTransparent,
    BOOL bStretch=FALSE,
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>Parameter

*hBitmap*<br/>
[in] Das Handle für die festzulegende Bitmap.

*clrTransparent*<br/>
[in] Ein RGB-Wert, der die transparente Farbe der Bitmap angibt.

*bStretch*<br/>
[in] Wenn TRUE, wird die Bitmap gestreckt, wenn sie nicht in das Bildumgrenzungsrechteck passt. Andernfalls wird die Bitmap nicht gedehnt.

*bmpAlignment*<br/>
[in] Die Ausrichtung der Bitmap.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um eine Bitmap für eine Beschriftungsleiste festzulegen.

Die vorherige Bitmap wird automatisch zerstört. Wenn in der Beschriftungsleiste ein Symbol angezeigt wird, weil Sie die [CMFCCaptionBar::SetIcon-Methode](#seticon) aufgerufen haben, wird die Bitmap nur angezeigt, wenn Sie das Symbol entfernen, indem Sie [CMFCCaptionBar::RemoveIcon](#removeicon)aufrufen.

Die Bitmap wird gemäß dem Parameter *bmpAlignment* ausgerichtet.  Dieser Parameter kann einen der folgenden `BarElementAlignment`-Werte aufweisen:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbarsetbordersize"></a><a name="setbordersize"></a>CMFCCaptionBar::SetBorderSize

Legt die Rahmengröße der Beschriftungsleiste fest.

```
void SetBorderSize(int nSize);
```

### <a name="parameters"></a>Parameter

*nGröße*<br/>
[in] Die neue Größe des Beschriftungsbalkenrahmens in Pixel.

## <a name="cmfccaptionbarsetbutton"></a><a name="setbutton"></a>CMFCCaptionBar::SetButton

Legt die Schaltfläche für die Beschriftungsleiste fest.

```
void SetButton(
    LPCTSTR lpszLabel,
    UINT uiCmdUI,
    BarElementAlignment btnAlignmnet=ALIGN_LEFT,
    BOOL bHasDropDownArrow=TRUE);
```

### <a name="parameters"></a>Parameter

*lpszLabel*<br/>
Die Befehlsbezeichnung der Schaltfläche.

*uiCmdUI*<br/>
Die Befehls-ID der Schaltfläche.

*btnAlignmnet*<br/>
Die Ausrichtung der Schaltfläche.

*bHasDropDownArrow*<br/>
TRUE, wenn die Schaltfläche einen Dropdown-Pfeil anzeigt, andernfalls FALSE.

## <a name="cmfccaptionbarsetbuttonpressed"></a><a name="setbuttonpressed"></a>CMFCCaptionBar::SetButtonPressed

Gibt an, ob die Taste gedrückt bleibt.

```
void SetButtonPressed(BOOL bPresed=TRUE);
```

### <a name="parameters"></a>Parameter

*bPresed*<br/>
TRUE, wenn die Taste ihren gedrückten Zustand behält, ANDERNFALLS FALSE.

## <a name="cmfccaptionbarsetbuttontooltip"></a><a name="setbuttontooltip"></a>CMFCCaptionBar::SetButtonToolTip

Legt die QuickInfo für die Schaltfläche fest.

```
void SetButtonToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>Parameter

*lpszToolTip*<br/>
[in] Die QuickInfo-Beschriftung.

*lpszBeschreibung*<br/>
[in] Die Tooltip-Beschreibung.

## <a name="cmfccaptionbarsetflatborder"></a><a name="setflatborder"></a>CMFCCaptionBar::SetFlatBorder

Legt den Rahmenstil der Beschriftungsleiste fest.

```
void SetFlatBorder(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>Parameter

*bFlat*<br/>
[in] TRUE, wenn der Rahmen einer Beschriftungsleiste flach ist. FALSE, wenn der Rahmen 3D ist.

## <a name="cmfccaptionbarseticon"></a><a name="seticon"></a>CMFCCaptionBar::SetIcon

Legt das Symbol für eine Beschriftungsleiste fest.

```
void SetIcon(
    HICON hIcon,
    BarElementAlignment iconAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>Parameter

*hIcon*<br/>
[in] Das Handle zum zu setzenden Symbol.

*iconAlignment*<br/>
[in] Die Ausrichtung des Symbols.

### <a name="remarks"></a>Bemerkungen

Beschriftungsleisten können entweder Symbole oder Bitmaps anzeigen. Weitere Informationen finden Sie [unter CMFCCaptionBar::SetBitmap,](#setbitmap) um herauszufinden, wie eine Bitmap angezeigt wird. Wenn Sie sowohl ein Symbol als auch eine Bitmap festlegen, wird das Symbol immer angezeigt. Rufen Sie [CMFCCaptionBar::RemoveIcon](#removeicon) auf, um ein Symbol aus der Beschriftungsleiste zu entfernen.

Das Symbol wird entsprechend dem Parameter *iconAlignment* ausgerichtet. Es kann einer der `BarElementAlignment` folgenden Werte sein:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbarsetimagetooltip"></a><a name="setimagetooltip"></a>CMFCCaptionBar::SetImageToolTip

Legt die QuickInfo für das Bild in der Beschriftungsleiste fest.

```
void SetImageToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>Parameter

*lpszToolTip*<br/>
[in] Der Text der QuickInfo.

*lpszBeschreibung*<br/>
[in] Die Tooltip-Beschreibung.

## <a name="cmfccaptionbarsetmargin"></a><a name="setmargin"></a>CMFCCaptionBar::SetMargin

Legt den Abstand zwischen der Kante des Beschriftungsbalkenelements und dem Rand des Beschriftungsleistensteuerelements fest.

```
void SetMargin(int nMargin);
```

### <a name="parameters"></a>Parameter

*nMargin*<br/>
[in] Der Abstand (in Pixel) zwischen dem Rand der Beschriftungsleistenelemente und dem Rand des Beschriftungsleistensteuerelements.

## <a name="cmfccaptionbarsettext"></a><a name="settext"></a>CMFCCaptionBar::SetText

Legt die Textbeschriftung für die Beschriftungsleiste fest.

```
void SetText(
    const CString& strText,
    BarElementAlignment textAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>Parameter

*strText*<br/>
[in] Die festzulegende Textzeichenfolge.

*Textalignment*<br/>
[in] Die Textausrichtung.

### <a name="remarks"></a>Bemerkungen

Die Textbeschriftung wird gemäß dem Parameter *textAlignment* ausgerichtet. Es kann einer der `BarElementAlignment` folgenden Werte sein:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
