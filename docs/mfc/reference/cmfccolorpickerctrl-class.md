---
title: CMFCColorPickerCtrl-Klasse
ms.date: 11/19/2018
f1_keywords:
- CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetHLS
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetHue
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetLuminance
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetSaturation
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SelectCellHexagon
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetHLS
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetHue
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetLuminance
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetLuminanceBarWidth
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetOriginalColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetPalette
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetSaturation
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetType
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::DrawCursor
helpviewer_keywords:
- CMFCColorPickerCtrl [MFC], CMFCColorPickerCtrl
- CMFCColorPickerCtrl [MFC], GetColor
- CMFCColorPickerCtrl [MFC], GetHLS
- CMFCColorPickerCtrl [MFC], GetHue
- CMFCColorPickerCtrl [MFC], GetLuminance
- CMFCColorPickerCtrl [MFC], GetSaturation
- CMFCColorPickerCtrl [MFC], SelectCellHexagon
- CMFCColorPickerCtrl [MFC], SetColor
- CMFCColorPickerCtrl [MFC], SetHLS
- CMFCColorPickerCtrl [MFC], SetHue
- CMFCColorPickerCtrl [MFC], SetLuminance
- CMFCColorPickerCtrl [MFC], SetLuminanceBarWidth
- CMFCColorPickerCtrl [MFC], SetOriginalColor
- CMFCColorPickerCtrl [MFC], SetPalette
- CMFCColorPickerCtrl [MFC], SetSaturation
- CMFCColorPickerCtrl [MFC], SetType
- CMFCColorPickerCtrl [MFC], DrawCursor
ms.assetid: b9bbd03c-beb0-4b55-9765-9985fd05e5dc
ms.openlocfilehash: fe35ee5d6fc6484788a2636151c386689f4bdd96
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752535"
---
# <a name="cmfccolorpickerctrl-class"></a>CMFCColorPickerCtrl-Klasse

Die `CMFCColorPickerCtrl` Klasse bietet Funktionen für ein Steuerelement, das zum Auswählen von Farben verwendet wird.

## <a name="syntax"></a>Syntax

```
class CMFCColorPickerCtrl : public CButton
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCColorPickerCtrl::CMFCColorPickerCtrl](#cmfccolorpickerctrl)|Erstellt ein `CMFCColorPickerCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCColorPickerCtrl::GetColor](#getcolor)|Ruft die Vom Benutzer ausgewählte Farbe ab.|
|[CMFCColorPickerStrg::GetHLS](#gethls)|Ruft die Farbton-, Luminanz- und Sättigungswerte der vom Benutzer ausgewählten Farbe ab.|
|[CMFCColorPickerStrg::GetHue](#gethue)|Ruft die Farbtonkomponente der Farbe ab, die der Benutzer auswählt.|
|[CMFCColorPickerStrg::GetLuminance](#getluminance)|Ruft die Luminanzkomponente der Farbe ab, die der Benutzer auswählt.|
|[CMFCColorPickerCtrl::GetAturation](#getsaturation)|Ruft die Sättigungskomponente der Vom Benutzer ausgewählten Farbe ab.|
|[CMFCColorPickerStrg::SelectCellHexagon](#selectcellhexagon)|Legt die aktuelle Farbe auf die Farbe fest, die durch die angegebenen RGB-Farbkomponenten oder das angegebene Zellsechseck definiert wird.|
|[CMFCColorPickerCtrl::SetColor](#setcolor)|Legt die aktuelle Farbe auf den angegebenen RGB-Farbwert fest.|
|[CMFCColorPickerStrg::SetHLS](#sethls)|Legt die aktuelle Farbe auf den angegebenen HLS-Farbwert fest.|
|[CMFCColorPickerStrg::SetHue](#sethue)|Ändert die Farbtonkomponente der aktuell ausgewählten Farbe.|
|[CMFCColorPickerStrg::SetLuminance](#setluminance)|Ändert die Luminanzkomponente der aktuell ausgewählten Farbe.|
|[CMFCColorPickerStrg::SetLuminanceBarWidth](#setluminancebarwidth)|Legt die Breite der Luminanzleiste im Farbauswahlsteuerelement fest.|
|[CMFCColorPickerCtrl::SetOriginalColor](#setoriginalcolor)|Legt die erste ausgewählte Farbe fest.|
|[CMFCColorPickerCtrl::SetPalette](#setpalette)|Legt die aktuelle Farbpalette fest.|
|[CMFCColorPickerCtrl::SetSättigung](#setsaturation)|Ändert die Sättigungskomponente der aktuell ausgewählten Farbe.|
|[CMFCColorPickerCtrl::SetType](#settype)|Legt den Typ des anzuzeigenden Farbauswahlsteuerelements fest.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCColorPickerStrg::DrawCursor](#drawcursor)|Wird vom Framework vor einem Cursor aufgerufen, der auf die ausgewählte Farbe zeigt.|

## <a name="remarks"></a>Bemerkungen

Standardfarben werden aus einer sechseckigen Farbpalette und benutzerdefinierte Farben aus einer Luminanzleiste ausgewählt, in der Farben entweder mit roter/grüner/blauer Notation oder Farbton/Sättigungsnotation angegeben werden.

Die folgende Abbildung `CMFCColorPickerCtrl` zeigt mehrere Objekte.

![CMFCColorPickerCtrl-Dialogfeld](../../mfc/reference/media/colorpicker.png "CMFCColorPickerCtrl-Dialogfeld")

Der `CMFCColorPickerCtrl` unterstützt zwei Stilpaare. Die Stile HEX und HEX_GREYSCALE eignen sich für die Standardfarbauswahl. Die Stile PICKER und LUMINANCE eignen sich für die individuelle Farbauswahl.

Führen Sie die folgenden `CMFCColorPickerCtrl` Schritte aus, um das Steuerelement in das Dialogfeld zu integrieren:

1. Wenn Sie den **ClassWizard**verwenden, fügen Sie ein neues `CMFCColorPickerCtrl` Schaltflächensteuerelement in `CButton` die Dialogfeldvorlage ein (da die Klasse von der Klasse geerbt wird).

1. Fügen Sie eine Membervariable, die dem neuen Schaltflächensteuerelement zugeordnet ist, in die Dialogfeldklasse ein. Ändern Sie dann `CButton` den `CMFCColorPickerCtrl`Variablentyp von in .

1. Fügen `WM_INITDIALOG` Sie den Nachrichtenhandler für die Dialogfeldklasse ein. Legen Sie im Handler den Typ, die Palette `CMFCColorPickerCtrl` und die erste ausgewählte Farbe des Steuerelements fest.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird `CMFCColorPickerCtrl` veranschaulicht, wie ein `CMFCColorPickerCtrl` Objekt mithilfe verschiedener Methoden in der Klasse konfiguriert wird. Im Beispiel wird veranschaulicht, wie der Typ des Auswahlsteuerelements festgelegt wird und wie seine Farbe, der Farbton, die Luminanz und die Sättigung festgelegt werden. Das Beispiel ist Teil des [Beispiels "Neue Steuerelemente "Neue Steuerelemente ".](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_NewControls#4](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#5](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxcolorpickerctrl.h

## <a name="cmfccolorpickerctrlcmfccolorpickerctrl"></a><a name="cmfccolorpickerctrl"></a>CMFCColorPickerCtrl::CMFCColorPickerCtrl

Erstellt ein `CMFCColorPickerCtrl`-Objekt.

```
CMFCColorPickerCtrl();
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolorpickerctrldrawcursor"></a><a name="drawcursor"></a>CMFCColorPickerStrg::DrawCursor

Wird vom Framework vor einem Cursor aufgerufen, der auf die ausgewählte Farbe zeigt.

```
virtual void DrawCursor(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Zeiger auf einen Gerätekontext.

*Rect*<br/>
[in] Gibt einen rechteckigen Bereich um die ausgewählte Farbe an.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, wenn Sie die Form des Cursors ändern müssen, der auf die ausgewählte Farbe zeigt.

## <a name="cmfccolorpickerctrlgetcolor"></a><a name="getcolor"></a>CMFCColorPickerCtrl::GetColor

Ruft die Vom Benutzer ausgewählte Farbe ab.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Rückgabewert

Der RGB-Wert der ausgewählten Farbe.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolorpickerctrlgethls"></a><a name="gethls"></a>CMFCColorPickerStrg::GetHLS

Ruft die Farbton-, Luminanz- und Sättigungswerte der vom Benutzer ausgewählten Farbe ab.

```cpp
void GetHLS(
    double* hue,
    double* luminance,
    double* saturation);
```

### <a name="parameters"></a>Parameter

*Farbton*<br/>
[out] Zeiger auf eine Variable vom Typ double, die Farbtoninformationen empfängt.

*Leuchtdichte*<br/>
[out] Zeiger auf eine Variable vom Typ double, die Luminanzinformationen empfängt.

*Sättigung*<br/>
[out] Zeiger auf eine Variable vom Typ double, die Sättigungsinformationen empfängt.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolorpickerctrlgethue"></a><a name="gethue"></a>CMFCColorPickerStrg::GetHue

Ruft die Farbtonkomponente der Farbe ab, die der Benutzer auswählt.

```
double GetHue() const;
```

### <a name="return-value"></a>Rückgabewert

Die Farbtonkomponente der ausgewählten Farbe.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolorpickerctrlgetluminance"></a><a name="getluminance"></a>CMFCColorPickerStrg::GetLuminance

Ruft die Luminanzkomponente der Farbe ab, die der Benutzer auswählt.

```
double GetLuminance() const;
```

### <a name="return-value"></a>Rückgabewert

Die Luminanzkomponente der ausgewählten Farbe.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolorpickerctrlgetsaturation"></a><a name="getsaturation"></a>CMFCColorPickerCtrl::GetAturation

Ruft den Sättigungswert der Vom Benutzer ausgewählten Farbe ab.

```
double GetSaturation() const;
```

### <a name="return-value"></a>Rückgabewert

Die Sättigungskomponente der ausgewählten Farbe.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolorpickerctrlselectcellhexagon"></a><a name="selectcellhexagon"></a>CMFCColorPickerStrg::SelectCellHexagon

Legt die aktuelle Farbe auf die Farbe fest, die durch die angegebenen RGB-Farbkomponenten oder das angegebene Zellsechseck definiert wird.

```cpp
void SelectCellHexagon(
    BYTE R,
    BYTE G,
    BYTE B);

BOOL SelectCellHexagon(
    int x,
    int y);
```

### <a name="parameters"></a>Parameter

*R*<br/>
[in] Die rote Farbkomponente.

*G*<br/>
[in] Die grüne Farbkomponente.

*B*<br/>
[in] Die blaue Farbkomponente.

*x*<br/>
[in] Die x-Koordinate des Cursors, die auf ein Zellsechseck zeigt.

*Y*<br/>
[in] Die y-Koordinate des Cursors, die auf ein Zellsechseck zeigt.

### <a name="return-value"></a>Rückgabewert

Die zweite Überladung dieser Methode gibt immer FALSE zurück.

### <a name="remarks"></a>Bemerkungen

Die erste Überladung dieser Methode legt die aktuelle Farbe auf die Farbe fest, die den vom Farbauswahlsteuerelement angegebenen Roten, Grünen und Blauen Farbkomponenten entspricht.

Die zweite Überladung dieser Methode legt die aktuelle Farbe auf die Farbe des Zellsechsecks fest, auf die durch die angegebene Cursorposition verwiesen wird.

## <a name="cmfccolorpickerctrlsetcolor"></a><a name="setcolor"></a>CMFCColorPickerCtrl::SetColor

Legt die aktuelle Farbe auf den angegebenen RGB-Farbwert fest.

```cpp
void SetColor(COLORREF Color);
```

### <a name="parameters"></a>Parameter

*Color*<br/>
[in] Ein RGB-Farbwert.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolorpickerctrlsethls"></a><a name="sethls"></a>CMFCColorPickerStrg::SetHLS

Legt die aktuelle Farbe auf den angegebenen HLS-Farbwert fest.

```cpp
void SetHLS(
    double hue,
    double luminance,
    double saturation,
    BOOL bInvalidate=TRUE);
```

### <a name="parameters"></a>Parameter

*Farbton*<br/>
[in] Ein Farbtonwert.

*Leuchtdichte*<br/>
[in] Ein Luminanzwert.

*Sättigung*<br/>
[in] Ein Sättigungswert.

*bUngültig*<br/>
[in] TRUE, um zu erzwingen, dass das Fenster sofort auf die neue Farbe aktualisiert wird; andernfalls FALSE. Der Standardwert ist TRUE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolorpickerctrlsethue"></a><a name="sethue"></a>CMFCColorPickerStrg::SetHue

Ändert den Farbton der aktuell ausgewählten Farbe.

```cpp
void SetHue(double Hue);
```

### <a name="parameters"></a>Parameter

*Farbton*<br/>
[in] Ein Farbtonwert.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolorpickerctrlsetluminance"></a><a name="setluminance"></a>CMFCColorPickerStrg::SetLuminance

Ändert die Luminanz der aktuell ausgewählten Farbe.

```cpp
void SetLuminance(double Luminance);
```

### <a name="parameters"></a>Parameter

*Sättigung*<br/>
[in] Ein Luminanzwert.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolorpickerctrlsetluminancebarwidth"></a><a name="setluminancebarwidth"></a>CMFCColorPickerStrg::SetLuminanceBarWidth

Legt die Breite der Luminanzleiste im Farbauswahlsteuerelement fest.

```cpp
void SetLuminanceBarWidth(int w);
```

### <a name="parameters"></a>Parameter

*w*<br/>
[in] Die Breite der Luminanzleiste, gemessen in Pixeln.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um die Größe der Luminanzleiste zu ändern, die sich auf der Registerkarte **Benutzerdefinierte** des Farbauswahlsteuerelements befindet. Der *Parameter w* gibt die neue Breite der Luminanzleiste an. Der Breitenwert wird ignoriert, wenn er drei Viertel der Clientbereichsbreite überschreitet.

## <a name="cmfccolorpickerctrlsetoriginalcolor"></a><a name="setoriginalcolor"></a>CMFCColorPickerCtrl::SetOriginalColor

Legt die erste ausgewählte Farbe fest.

```cpp
void SetOriginalColor(COLORREF ref);
```

### <a name="parameters"></a>Parameter

*ref*<br/>
[in] Ein RGB-Farbwert.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, wenn das Farbauswahlsteuerelement initialisiert wird.

## <a name="cmfccolorpickerctrlsetpalette"></a><a name="setpalette"></a>CMFCColorPickerCtrl::SetPalette

Legt die aktuelle Farbpalette fest.

```cpp
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Parameter

*pPalette*<br/>
[in] Zeiger auf eine Farbpalette.

### <a name="remarks"></a>Bemerkungen

Die Farbpalette definiert das Array von Farben, das im Farbauswahlsteuerelement angezeigt wird.

## <a name="cmfccolorpickerctrlsetsaturation"></a><a name="setsaturation"></a>CMFCColorPickerCtrl::SetSättigung

Ändert die Sättigung der aktuell ausgewählten Farbe.

```cpp
void SetSaturation(double Saturation);
```

### <a name="parameters"></a>Parameter

*Sättigung*<br/>
[in] Ein Sättigungswert.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolorpickerctrlsettype"></a><a name="settype"></a>CMFCColorPickerCtrl::SetType

Legt den Typ des anzuzeigenden Farbauswahlsteuerelements fest.

```cpp
void SetType(COLORTYPE colorType);
```

### <a name="parameters"></a>Parameter

*Farbtyp*<br/>
[in] Ein Farbauswahlsteuerelementtyp.

Die Typen werden `CMFCColorPickerCtrl::COLORTYPE` durch die Enumeration definiert. Die möglichen Typen sind LUMINANCE, PICKER, HEX und HEX_GREYSCALE. Der Standardtyp ist PICKER.

### <a name="remarks"></a>Bemerkungen

Um einen Farbauswahlsteuerelementtyp anzugeben, rufen Sie diese Methode auf, bevor das Windows-Steuerelement erstellt wird.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog-Klasse](../../mfc/reference/cmfccolordialog-class.md)
