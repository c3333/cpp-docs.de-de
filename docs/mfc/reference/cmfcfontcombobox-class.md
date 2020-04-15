---
title: CMFCFontComboBox-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::GetSelFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::SelectFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::Setup
- AFXFONTCOMBOBOX/CMFCFontComboBox::m_bDrawUsingFont
helpviewer_keywords:
- CMFCFontComboBox [MFC], CMFCFontComboBox
- CMFCFontComboBox [MFC], GetSelFont
- CMFCFontComboBox [MFC], SelectFont
- CMFCFontComboBox [MFC], Setup
- CMFCFontComboBox [MFC], m_bDrawUsingFont
ms.assetid: 9a53fb0c-7b45-486d-8187-2a4c723d9fbb
ms.openlocfilehash: 60b4b7cdfdace2332de35dd93c43eacf592e99e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367494"
---
# <a name="cmfcfontcombobox-class"></a>CMFCFontComboBox-Klasse

Die `CMFCFontComboBox` Klasse erstellt ein Kombinationsfeldsteuerelement, das eine Liste von Schriftarten enthält.

## <a name="syntax"></a>Syntax

```
class CMFCFontComboBox : public CComboBox
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCFontComboBox::CMFCFontComboBox](#cmfcfontcombobox)|Erstellt ein `CMFCFontComboBox`-Objekt.|
|`CMFCFontComboBox::~CMFCFontComboBox`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMFCFontComboBox::CompareItem`|Wird vom Framework aufgerufen, um die relative Position eines neuen Elements im sortierten Listenfeld des aktuellen Schriftkombinationsfeldsteuerelements zu bestimmen. (Überschreibt [CComboBox::CompareItem](../../mfc/reference/ccombobox-class.md#compareitem).)|
|`CMFCFontComboBox::DrawItem`|Wird vom Framework aufgerufen, um ein angegebenes Element im aktuellen Schriftkombinationsfeldsteuerelement zu zeichnen. (Überschreibt [CComboBox::DrawItem](../../mfc/reference/ccombobox-class.md#drawitem).)|
|[CMFCFontComboBox::GetSelFont](#getselfont)|Ruft Informationen zur aktuell ausgewählten Schriftart ab.|
|`CMFCFontComboBox::MeasureItem`|Wird vom Framework aufgerufen, um Windows über die Dimensionen des Listenfelds im aktuellen Steuerelement für die Schriftkombinationskombination zu informieren. (Überschreibt [CComboBox::MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem).)|
|`CMFCFontComboBox::PreTranslateMessage`|Übersetzt Fensternachrichten, bevor sie an die [TranslateMessage-](/windows/win32/api/winuser/nf-winuser-translatemessage) und [DispatchMessage-Windows-Funktionen](/windows/win32/api/winuser/nf-winuser-dispatchmessage) gesendet werden. (Überschreibt [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCFontComboBox::SelectFont](#selectfont)|Wählt die Schriftart aus, die den angegebenen Kriterien entspricht, aus dem Feld "Schriftkombination".|
|[CMFCFontComboBox::Setup](#setup)|Initialisiert die Liste der Elemente im Schriftkombinationsfeld.|

### <a name="data-members"></a>Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCFontComboBox::m_bDrawUsingFont](#m_bdrawusingfont)|Gibt dem Framework an, welche Schriftart zum Zeichnen der Elementbeschriftungen im aktuellen Schriftkombinationsfeld verwendet werden soll.|

## <a name="remarks"></a>Bemerkungen

Um ein `CMFCFontComboBox` Objekt in einem Dialogfeld zu verwenden, fügen Sie der Dialogfeldklasse eine `CMFCFontComboBox` Variable hinzu. Rufen Sie `OnInitDialog` dann in der Methode der Dialogfeldklasse die [CMFCFontComboBox::Setup-Methode](#setup) auf, um die Liste der Elemente im Kombinationsfeldsteuerelement zu initialisieren.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

[CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxfontcombobox.h

## <a name="cmfcfontcomboboxcmfcfontcombobox"></a><a name="cmfcfontcombobox"></a>CMFCFontComboBox::CMFCFontComboBox

Erstellt ein `CMFCFontComboBox`-Objekt.

```
CMFCFontComboBox();
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcfontcomboboxgetselfont"></a><a name="getselfont"></a>CMFCFontComboBox::GetSelFont

Ruft Informationen zur aktuell ausgewählten Schriftart ab.

```
CMFCFontInfo* GetSelFont() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das [CMFCFontInfo-Klassenobjekt,](../../mfc/reference/cmfcfontinfo-class.md) das eine Schriftart beschreibt. Es kann NULL sein, wenn im Kombinationsfeld keine Schriftart ausgewählt ist.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcfontcomboboxm_bdrawusingfont"></a><a name="m_bdrawusingfont"></a>CMFCFontComboBox::m_bDrawUsingFont

Gibt dem Framework an, welche Schriftart zum Zeichnen der Elementbeschriftungen im aktuellen Schriftkombinationsfeld verwendet werden soll.

```
static BOOL m_bDrawUsingFont;
```

### <a name="remarks"></a>Bemerkungen

Legen Sie diesen Member auf TRUE fest, um das Framework anzuweisen, dieselbe Schriftart zum Zeichnen jeder Elementbeschriftung zu verwenden. Legen Sie diesen Member auf FALSE fest, um das Framework anzuweisen, jede Elementbeschriftung mit der Schriftart zu zeichnen, deren Name mit der Beschriftung identisch ist. Der Standardwert dieses Elements ist FALSE.

## <a name="cmfcfontcomboboxselectfont"></a><a name="selectfont"></a>CMFCFontComboBox::SelectFont

Wählt die Schriftart aus, die den angegebenen Kriterien entspricht, aus dem Feld "Schriftkombination".

```
BOOL SelectFont(CMFCFontInfo* pDesc);

BOOL SelectFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET);
```

### <a name="parameters"></a>Parameter

*pDesc*<br/>
[in] Zeigt auf ein Schriftartbeschreibungsobjekt.

*lpszName*<br/>
[in] Gibt einen Schriftartnamen an.

*nCharSet*<br/>
[in] Gibt einen Zeichensatz an. Der Standardwert ist DEFAULT_CHARSET. Weitere Informationen finden `lfCharSet` Sie im Member der [LOGFONT-Struktur.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

### <a name="return-value"></a>Rückgabewert

TRUE, wenn ein Element im Schriftkombinationsfeld mit dem angegebenen Schriftartbeschreibungsobjekt oder Schriftartennamen und Zeichensatz übereinstimmt; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um das Element im Schriftkombinationsfeld auszuwählen und zu scrollen, das der angegebenen Schriftart entspricht.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird `SelectFont` veranschaulicht, `CMFCFontComboBox` wie die Methode in der Klasse verwendet wird. Dieses Beispiel ist Teil des [Beispiels "Neue Steuerelemente "Neue Steuerelemente ".](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#35](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]

## <a name="cmfcfontcomboboxsetup"></a><a name="setup"></a>CMFCFontComboBox::Setup

Initialisiert die Liste der Elemente im Schriftkombinationsfeld.

```
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,
    BYTE nCharSet=DEFAULT_CHARSET,
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```

### <a name="parameters"></a>Parameter

*nFontType*<br/>
[in] Gibt den Schrifttyp an. Der Standardwert ist die bitweise Kombination (OR) von DEVICE_FONTTYPE, RASTER_FONTTYPE und TRUETYPE_FONTTYPE.

*nCharSet*<br/>
[in] Gibt den Schriftzeichensatz an. Der Standardwert ist DEFAULT_CHARSET.

*nPitchAndFamilie*<br/>
[in] Gibt die Schriftabstand und die Familie an. Der Standardwert ist DEFAULT_PITCH.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Schriftkombinationsfeld erfolgreich initialisiert wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode initialisiert das Schriftkombinationsfeld, indem die aktuell installierten Schriftarten aufgezählt werden, die den angegebenen Parametern entsprechen, und diese Schriftartnamen in das Schriftkombinationsfeld einfügen.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird `Setup` veranschaulicht, `CMFCFontComboBox` wie die Methode in der Klasse verwendet wird. Dieses Beispiel ist Teil des [Beispiels "Neue Steuerelemente "Neue Steuerelemente ".](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#36](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox-Klasse](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCFontInfo-Klasse](../../mfc/reference/cmfcfontinfo-class.md)
