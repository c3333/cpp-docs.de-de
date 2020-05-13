---
title: CMFCColorDialog-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::GetColor
- AFXCOLORDIALOG/CMFCColorDialog::GetPalette
- AFXCOLORDIALOG/CMFCColorDialog::RebuildPalette
- AFXCOLORDIALOG/CMFCColorDialog::SetCurrentColor
- AFXCOLORDIALOG/CMFCColorDialog::SetNewColor
- AFXCOLORDIALOG/CMFCColorDialog::SetPageOne
- AFXCOLORDIALOG/CMFCColorDialog::SetPageTwo
helpviewer_keywords:
- CMFCColorDialog [MFC], CMFCColorDialog
- CMFCColorDialog [MFC], GetColor
- CMFCColorDialog [MFC], GetPalette
- CMFCColorDialog [MFC], RebuildPalette
- CMFCColorDialog [MFC], SetCurrentColor
- CMFCColorDialog [MFC], SetNewColor
- CMFCColorDialog [MFC], SetPageOne
- CMFCColorDialog [MFC], SetPageTwo
ms.assetid: 235bbbbc-a3b1-46e0-801b-fb55093ec579
ms.openlocfilehash: 1d4bd31d5095f572ee80f0357a2d7526482f1caa
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752547"
---
# <a name="cmfccolordialog-class"></a>CMFCColorDialog-Klasse

Die `CMFCColorDialog` Klasse stellt ein Dialogfeld für die Farbauswahl dar.

## <a name="syntax"></a>Syntax

```
class CMFCColorDialog : public CDialogEx
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCColorDialog::CMFCColorDialog](#cmfccolordialog)|Erstellt ein `CMFCColorDialog`-Objekt.|
|`CMFCColorDialog::~CMFCColorDialog`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCColorDialog::GetColor](#getcolor)|Gibt die aktuell ausgewählte Farbe zurück.|
|[CMFCColorDialog::GetPalette](#getpalette)|Gibt die Farbpalette zurück.|
|`CMFCColorDialog::PreTranslateMessage`|Übersetzt Fensternachrichten, bevor sie an die [TranslateMessage-](/windows/win32/api/winuser/nf-winuser-translatemessage) und [DispatchMessage-Windows-Funktionen](/windows/win32/api/winuser/nf-winuser-dispatchmessage) gesendet werden. Syntax und weitere Informationen finden Sie unter [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Überschreibt `CDialogEx::PreTranslateMessage`.)|
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|Leitet eine Palette aus der Systempalette ab.|
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|Legt die aktuell ausgewählte Farbe fest.|
|[CMFCColorDialog::SetNewColor](#setnewcolor)|Legt die Farbe fest, die einem angegebenen RGB-Wert am ähnlichsten ist.|
|[CMFCColorDialog::SetPageOne](#setpageone)|Wählt einen RGB-Wert für die erste Eigenschaftenseite aus.|
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|Wählt einen RGB-Wert für die zweite Eigenschaftenseite aus.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|`m_bIsMyPalette`|TRUE, wenn das Dialogfeld Farbauswahl eine eigene Farbpalette verwendet, oder FALSE, `CMFCColorDialog` wenn das Dialogfeld eine Im Konstruktor angegebene Palette verwendet.|
|`m_bPickerMode`|TRUE, während der Benutzer eine Farbe aus dem Auswahldialogfeld auswählt; andernfalls FALSE.|
|`m_btnColorSelect`|Die Vom Benutzer ausgewählte Farbschaltfläche.|
|`m_CurrentColor`|Die aktuell ausgewählte Farbe.|
|`m_hcurPicker`|Der Cursor, der zum Auswählen einer Farbe verwendet wird.|
|`m_NewColor`|Die prospektive ausgewählte Farbe, die dauerhaft ausgewählt oder auf die ursprüngliche Farbe zurückgesetzt werden kann.|
|`m_pColourSheetOne`|Ein Zeiger auf die erste Eigenschaftenseite des Eigenschaftenblatts für die Farbauswahl.|
|`m_pColourSheetTwo`|Ein Zeiger auf die zweite Eigenschaftenseite des Eigenschaftenblatts für die Farbauswahl.|
|`m_pPalette`|Die aktuelle logische Palette.|
|`m_pPropSheet`|Ein Zeiger auf das Eigenschaftenblatt für das Dialogfeld Farbauswahl.|
|`m_wndColors`|Ein Farbauswahlsteuerelementobjekt.|
|`m_wndStaticPlaceHolder`|Ein statisches Steuerelement, das ein Platzhalter für das Eigenschaftenblatt für die Farbauswahl ist.|

## <a name="remarks"></a>Bemerkungen

Das Dialogfeld Farbauswahl wird als Eigenschaftenblatt mit zwei Seiten angezeigt. Auf der ersten Seite wählen Sie eine Standardfarbe aus der Systempalette aus. Auf der zweiten Seite wählen Sie eine benutzerdefinierte Farbe aus.

Sie können `CMFCColorDialog` ein Objekt auf dem `DoModal`Stapel erstellen und dann aufrufen, indem Sie die Anfangsfarbe als Parameter an den `CMFCColorDialog` Konstruktor übergeben. Das Dialogfeld Farbauswahl erstellt dann mehrere Objekte der [CMFCColorPickerCtrl-Klasse,](../../mfc/reference/cmfccolorpickerctrl-class.md) um jede Farbpalette zu verarbeiten.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie Sie ein `CMFCColorDialog` Farbdialogfeld mithilfe verschiedener Methoden in der Klasse konfigurieren. Das Beispiel zeigt, wie die aktuelle und die neue Farbe des Dialogfelds festgelegt werden und wie die roten, grünen und blauen Komponenten einer ausgewählten Farbe auf den beiden Eigenschaftenseiten des Farbdialogs festgelegt werden. Dieses Beispiel ist Teil des [Beispiels "Neue Steuerelemente "Neue Steuerelemente ".](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxcolordialog.h

## <a name="cmfccolordialogcmfccolordialog"></a><a name="cmfccolordialog"></a>CMFCColorDialog::CMFCColorDialog

Erstellt ein `CMFCColorDialog`-Objekt.

```
CMFCColorDialog(
    COLORREF clrInit=0,
    DWORD dwFlags=0,
    CWnd* pParentWnd=NULL,
    HPALETTE hPal=NULL);
```

### <a name="parameters"></a>Parameter

*clrInit*<br/>
[in] Die Standardfarbauswahl. Wenn kein Wert angegeben ist, ist der Standardwert RGB(0,0,0) (schwarz).

*dwFlags*<br/>
[in]: Reserviert

*pParentWnd*<br/>
[in] Ein Zeiger auf das übergeordnete oder Besitzerfenster des Dialogfelds.

*hPal*<br/>
[in] Ein Handle für eine Farbpalette.

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolordialoggetcolor"></a><a name="getcolor"></a>CMFCColorDialog::GetColor

Ruft die Farbe ab, die der Benutzer aus dem Farbdialogfeld auswählt.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Rückgabewert

Ein [COLORREF-Wert,](/windows/win32/gdi/colorref) der die RGB-Informationen für die im Farbdialogfeld ausgewählte Farbe enthält.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion `DoModal` auf, nachdem Sie die Methode aufrufen.

## <a name="cmfccolordialoggetpalette"></a><a name="getpalette"></a>CMFCColorDialog::GetPalette

Ruft die Farbpalette ab, die im aktuellen Farbdialog verfügbar ist.

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CPalette` das Objekt, `CMFCColorDialog` das im Konstruktor angegeben wurde.

### <a name="remarks"></a>Bemerkungen

Die Farbpalette gibt die Farben an, die der Benutzer auswählen kann.

## <a name="cmfccolordialogrebuildpalette"></a><a name="rebuildpalette"></a>CMFCColorDialog::RebuildPalette

Leitet eine Palette aus der Systempalette ab.

```cpp
void RebuildPalette();
```

## <a name="cmfccolordialogsetcurrentcolor"></a><a name="setcurrentcolor"></a>CMFCColorDialog::SetCurrentColor

Legt die aktuelle Farbe des Dialogfelds fest.

```cpp
void SetCurrentColor(COLORREF rgb);
```

### <a name="parameters"></a>Parameter

*Rgb*<br/>
[in] Ein RGB-Farbwert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolordialogsetnewcolor"></a><a name="setnewcolor"></a>CMFCColorDialog::SetNewColor

Legt die aktuelle Farbe auf die Farbe in der aktuellen Palette fest, die sich am ähnlichsten befindet.

```cpp
void SetNewColor(COLORREF rgb);
```

### <a name="parameters"></a>Parameter

*Rgb*<br/>
[in] Ein [COLORREF,](/windows/win32/gdi/colorref) der eine RGB-Farbe angibt.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolordialogsetpageone"></a><a name="setpageone"></a>CMFCColorDialog::SetPageOne

Gibt explizit die roten, grünen und blauen Komponenten einer ausgewählten Farbe auf der ersten Eigenschaftenseite eines Farbdialogs an.

```cpp
void SetPageOne(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Parameter

*R*<br/>
[in] Gibt die rote Komponente des RGB-Werts an.

*G*<br/>
[in] Gibt die grüne Komponente des RGB-Werts an.

*B*<br/>
[in] Gibt die blaue Komponente des RGB-Werts an.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolordialogsetpagetwo"></a><a name="setpagetwo"></a>CMFCColorDialog::SetPageTwo

Gibt explizit die roten, grünen und blauen Komponenten einer ausgewählten Farbe auf der zweiten Eigenschaftenseite eines Farbdialogs an.

```cpp
void SetPageTwo(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Parameter

*R*<br/>
[in] Gibt eine rote Komponente des RGB-Werts an

*G*<br/>
[in] Gibt eine grüne Komponente eines RGB-Werts an

*B*<br/>
[in] Gibt eine blaue Komponente eines RGB-Werts an

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorPickerCtrl-Klasse](../../mfc/reference/cmfccolorpickerctrl-class.md)
