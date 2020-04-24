---
title: CMFCCaptionButton-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetHit
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetIconID
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetRect
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetSize
- AFXCAPTIONBUTTON/CMFCCaptionButton::IsMiniFrameButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::Move
- AFXCAPTIONBUTTON/CMFCCaptionButton::OnDraw
- AFXCAPTIONBUTTON/CMFCCaptionButton::SetMiniFrameButton
helpviewer_keywords:
- CMFCCaptionButton [MFC], CMFCCaptionButton
- CMFCCaptionButton [MFC], GetHit
- CMFCCaptionButton [MFC], GetIconID
- CMFCCaptionButton [MFC], GetRect
- CMFCCaptionButton [MFC], GetSize
- CMFCCaptionButton [MFC], IsMiniFrameButton
- CMFCCaptionButton [MFC], Move
- CMFCCaptionButton [MFC], OnDraw
- CMFCCaptionButton [MFC], SetMiniFrameButton
ms.assetid: c5774b38-c0dd-414a-9ede-3b2f78f233ec
ms.openlocfilehash: 1b0a999f1fd1e3df1b0a971220454397cead02a9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752598"
---
# <a name="cmfccaptionbutton-class"></a>CMFCCaptionButton-Klasse

Die `CMFCCaptionButton` Klasse implementiert eine Schaltfläche, die in der Beschriftungsleiste für einen Andockbereich oder ein Miniframefenster angezeigt wird. In der Regel erstellt das Framework Beschriftungsschaltflächen automatisch.

## <a name="syntax"></a>Syntax

```
class CMFCCaptionButton : public CObject
```

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCCaptionButton::CMFCCaptionButton](#cmfccaptionbutton)|Erstellt ein CMFCCaptionButton-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCCaptionButton::GetHit](#gethit)|Gibt den Befehl zurück, der durch die Schaltfläche dargestellt wird.|
|[CMFCCaptionButton::GetIconID](#geticonid)|Gibt die Bild-ID zurück, die der Schaltfläche zugeordnet ist.|
|[CMFCCaptionButton::GetRect](#getrect)|Gibt das rechteckige Rechteck zurück, das von der Schaltfläche belegt ist.|
|[CMFCCaptionButton::GetSize](#getsize)|Gibt die Breite und Höhe der Schaltfläche zurück.|
|[CMFCCaptionButton::IsMiniFrameButton](#isminiframebutton)|Gibt an, ob die Titelleistenhöhe auf Minigröße festgelegt ist.|
|[CMFCCaptionButton::Verschieben](#move)|Legt die Position des Schaltflächenzeichnens und den Anzeigestatus des Fensters fest.|
|[CMFCCaptionButton::OnDraw](#ondraw)|Zeichnet die Beschriftungsschaltfläche.|
|[CMFCCaptionButton::SetMiniFrameButton](#setminiframebutton)|Legt die Minigröße der Titelleiste fest.|

## <a name="remarks"></a>Bemerkungen

Sie können eine Klasse von [der CPaneFrameWnd-Klasse](../../mfc/reference/cpaneframewnd-class.md) ableiten und die geschützte Methode verwenden, `AddButton`um Beschriftungsschaltflächen zu einem Minirahmenfenster hinzuzufügen.

CPaneFrameWnd.h definiert Befehls-IDs für zwei Arten von Beschriftungsschaltflächen:

- AFX_CAPTION_BTN_PIN, die eine Pin-Schaltfläche anzeigt, wenn der Andockbereich den automatischen Ausblendmodus unterstützt.

- AFX_CAPTION_BTN_CLOSE, die eine Schaltfläche **Schließen** anzeigt, wenn der Bereich geschlossen oder ausgeblendet werden kann.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird `CMFCCaptionButton` veranschaulicht, wie ein Objekt erstellt und die Minigröße der Titelleiste festgelegt wird.

[!code-cpp[NVC_MFC_RibbonApp#43](../../mfc/reference/codesnippet/cpp/cmfccaptionbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCCaptionButton](../../mfc/reference/cmfccaptionbutton-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxcaptionbutton.h

## <a name="cmfccaptionbuttoncmfccaptionbutton"></a><a name="cmfccaptionbutton"></a>CMFCCaptionButton::CMFCCaptionButton

Erstellt ein `CMFCCaptionButton`-Objekt.

```
CMFCCaptionButton();

CMFCCaptionButton(
    UINT nHit,
    BOOL bLeftAlign = FALSE);
```

### <a name="parameters"></a>Parameter

*nHit*<br/>
[in] Der der Schaltfläche zugeordnete Befehl.

*bLeftAlign*<br/>
[in] Gibt an, ob die Schaltfläche links ausgerichtet ist.

In der folgenden Tabelle sind mögliche Werte für den Parameter *nHit* aufgeführt.

|Wert|Get-Help|
|-----------|-------------|
|AFX_HTCLOSE|Schaltfläche schließen.|
|HTMINBUTTON|Minimieren Sie die Schaltfläche.|
|HTMAXBUTTON|Maximieren Sie die Schaltfläche.|
|AFX_HTLEFTBUTTON|Linke Pfeiltaste.|
|AFX_HTRIGHTBUTTON|Rechte Pfeiltaste.|
|AFX_HTMENU|Nach unten Pfeil Menü-Taste.|
|HTNOWHERE|Der Standardwert; stellt keinen Befehl dar.|

### <a name="remarks"></a>Bemerkungen

Standardmäßig sind Beschriftungsschaltflächen keinem Befehl zugeordnet.

Beschriftungsschaltflächen werden entweder rechts oder links ausgerichtet.

## <a name="cmfccaptionbuttongethit"></a><a name="gethit"></a>CMFCCaptionButton::GetHit

Gibt den Befehl zurück, der durch die Schaltfläche dargestellt wird.

```
UINT GetHit() const;
```

### <a name="return-value"></a>Rückgabewert

Der Befehl, der durch die Schaltfläche dargestellt wird.

In der folgenden Tabelle sind mögliche Rückgabewerte aufgeführt.

|Wert|Get-Help|
|-----------|-------------|
|AFX_HTCLOSE|Schaltfläche schließen.|
|HTMINBUTTON|Minimieren Sie die Schaltfläche.|
|HTMAXBUTTON|Maximieren Sie die Schaltfläche.|
|AFX_HTLEFTBUTTON|Linke Pfeiltaste.|
|AFX_HTRIGHTBUTTON|Rechte Pfeiltaste.|
|AFX_HTMENU|Nach unten Pfeil Menü-Taste.|
|HTNOWHERE|Der Standardwert; stellt keinen Befehl dar.|

## <a name="cmfccaptionbuttongeticonid"></a><a name="geticonid"></a>CMFCCaptionButton::GetIconID

Gibt die Bild-ID zurück, die der Schaltfläche zugeordnet ist.

```
virtual CMenuImages::IMAGES_IDS GetIconID(
    BOOL bHorz,
    BOOL bMaximized = FALSE) const;
```

### <a name="parameters"></a>Parameter

*bHorz*<br/>
[in] TRUE für Bild-IDs mit linkem oder rechtem Pfeil; FALSE für Bild-IDs nach oben oder unten.

*bMaximiert*<br/>
[in] TRUE für eine maximierung der Bild-ID; FALSE für eine minimale Bild-ID.

### <a name="return-value"></a>Rückgabewert

Die Bild-ID.

### <a name="remarks"></a>Bemerkungen

Die Parameter geben Bild-IDs an, um Beschriftungsschaltflächen zu minimieren oder zu maximieren.

## <a name="cmfccaptionbuttongetrect"></a><a name="getrect"></a>CMFCCaptionButton::GetRect

Gibt das rechteckige Rechteck zurück, das von der Schaltfläche belegt ist.

```
virtual CRect GetRect() const;
```

### <a name="return-value"></a>Rückgabewert

Das Rechteck, das die Position der Schaltfläche darstellt.

### <a name="remarks"></a>Bemerkungen

Wenn die Schaltfläche nicht angezeigt wird, wird die zurückgegebene Größe 0 angezeigt.

## <a name="cmfccaptionbuttongetsize"></a><a name="getsize"></a>CMFCCaptionButton::GetSize

Gibt die Breite und Höhe der Schaltfläche zurück.

```
static CSize GetSize();
```

### <a name="return-value"></a>Rückgabewert

Die äußeren Abmessungen der Taste.

### <a name="remarks"></a>Bemerkungen

Die zurückgegebene Größe enthält Denkrahmen und den Rahmen.

## <a name="cmfccaptionbuttonisminiframebutton"></a><a name="isminiframebutton"></a>CMFCCaptionButton::IsMiniFrameButton

Gibt an, ob die Titelleistenhöhe auf Minigröße festgelegt ist.

```
BOOL IsMiniFrameButton() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Beschriftung auf Minigröße eingestellt ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccaptionbuttonmove"></a><a name="move"></a>CMFCCaptionButton::Verschieben

Legt die Position des Schaltflächenzeichnens und den Anzeigestatus des Fensters fest.

```cpp
void Move(
    const CPoint& ptTo,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parameter

*ptTo*<br/>
[in] Der neue Standort.

*bHide*<br/>
[in] Gibt an, ob die Schaltfläche angezeigt werden soll.

## <a name="cmfccaptionbuttonondraw"></a><a name="ondraw"></a>CMFCCaptionButton::OnDraw

Zeichnet die Beschriftungsschaltfläche.

```
virtual void OnDraw(
    CDC* pDC,
    BOOL bActive,
    BOOL bHorz = TRUE,
    BOOL bMaximized = TRUE,
    BOOL bDisabled = FALSE);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Zeiger auf einen Gerätekontext für die Schaltfläche.

*bAktiv*<br/>
[in] Gibt an, ob ein aktives Schaltflächenbild gezeichnet werden soll.

*bHorz*<br/>
[in] Reserviert für die Verwendung in einer abgeleiteten Klasse.

*bMaximiert*<br/>
[in] Gibt an, ob ein maximiertes Schaltflächenbild gezeichnet werden soll.

*bDeaktiviert*<br/>
[in] Gibt an, ob ein aktiviertes Schaltflächenbild gezeichnet werden soll.

### <a name="remarks"></a>Bemerkungen

Der *Parameter bMaximized* wird verwendet, wenn es sich bei der Schaltfläche um eine Schaltfläche zum Maximieren oder Minimieren handelt.

## <a name="cmfccaptionbuttonsetminiframebutton"></a><a name="setminiframebutton"></a>CMFCCaptionButton::SetMiniFrameButton

Legt die Minigröße der Titelleiste fest.

```cpp
void SetMiniFramebutton(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parameter

*bSet*<br/>
[in] TRUE für Mini-Titelleistenhöhe; FALSE für die Standard-Titelleistenhöhe.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CPaneFrameWnd-Klasse](../../mfc/reference/cpaneframewnd-class.md)<br/>
[CDockablePane-Klasse](../../mfc/reference/cdockablepane-class.md)
