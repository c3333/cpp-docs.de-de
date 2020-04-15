---
title: CMFCToolBarFontComboBox-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::GetFontDesc
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::SetFont
helpviewer_keywords:
- CMFCToolBarFontComboBox [MFC], CMFCToolBarFontComboBox
- CMFCToolBarFontComboBox [MFC], GetFontDesc
- CMFCToolBarFontComboBox [MFC], SetFont
ms.assetid: 25f8e08c-aadd-4cb5-9581-a99d49d444b1
ms.openlocfilehash: 7b31f4b725a6983171162d9805d08224ad787808
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360463"
---
# <a name="cmfctoolbarfontcombobox-class"></a>CMFCToolBarFontComboBox-Klasse

Eine Symbolleistenschaltfläche, die ein Kombinationsfeldsteuerelement enthält, mit dem der Benutzer eine Schriftart aus einer Liste von Systemschriftarten auswählen kann.

## <a name="syntax"></a>Syntax

```
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>Member

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCToolBarFontComboBox::CMFCToolBarFontComboBox](#cmfctoolbarfontcombobox)|Erstellt ein `CMFCToolBarFontComboBox`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|Gibt einen Zeiger `CMFCFontInfo` auf das Objekt für einen angegebenen Index im Kombinationsfeld zurück.|
|[CMFCToolBarFontComboBox::SetFont](#setfont)|Wählt eine Schriftart im Schriftkombinationsfeld entsprechend dem Namen der Schriftart oder dem Präfix und Zeichensatz der Schriftart aus.|

### <a name="data-members"></a>Datenelemente

[CMFCToolBarFontComboBox::m_nFontHeight](#m_nfontheight)<br/>
Die Höhe der Zeichen im Schriftkombinationsfeld.

## <a name="remarks"></a>Bemerkungen

Führen Sie die folgenden Schritte aus, um eine Schaltfläche für die Schriftkombinationsbox zu einer Symbolleiste hinzuzufügen:

1. Reservieren Sie eine Platzhalterressourcen-ID für die Schaltfläche in der übergeordneten Symbolleistenressource.

1. Konstruieren Sie ein `CMFCToolBarFontComboBox`-Objekt.

1. Ersetzen Sie im Nachrichtenhandler, der die AFX_WM_RESETTOOLBAR-Nachricht verarbeitet, die ursprüngliche Schaltfläche durch die neue Kombinationsfeldschaltfläche mithilfe der [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

1. Synchronisieren Sie die im Kombinationsfeld ausgewählte Schriftart mit der Schriftart im Dokument, indem Sie die [CMFCToolBarFontComboBox::SetFont-Methode verwenden.](#setfont)

Um die Schriftart des Dokuments mit der im Kombinationsfeld ausgewählten Schriftart zu synchronisieren, verwenden Sie die [CMFCToolBarFontComboBox::GetFontDesc-Methode,](#getfontdesc) um die Attribute der ausgewählten Schriftart abzurufen, und verwenden Sie diese Attribute, um ein [CFont Class-Objekt](../../mfc/reference/cfont-class.md) zu erstellen.

Die Schaltfläche "Schriftkombinationsbox" ruft die Win32-Funktion [EnumFontFamiliesEx](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesexw) auf, um die bildschirm- und Druckerschriftarten zu ermitteln, die dem System zur Verfügung stehen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxtoolbarfontcombobox.h

## <a name="cmfctoolbarfontcomboboxcmfctoolbarfontcombobox"></a><a name="cmfctoolbarfontcombobox"></a>CMFCToolBarFontComboBox::CMFCToolBarFontComboBox

Erstellt ein [CMFCToolBarFontComboBox-Objekt.](../../mfc/reference/cmfctoolbarfontcombobox-class.md)

```
public:
CMFCToolBarFontComboBox(
    UINT uiID,
    int iImage,
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    DWORD dwStyle = CBS_DROPDOWN,
    int iWidth = 0,
    BYTE nPitchAndFamily = DEFAULT_PITCH);

protected:
CMFCToolBarFontComboBox(
    CObList* pLstFontsExternal,
    int nFontType,
    BYTE nCharSet,
    BYTE nPitchAndFamily);

CMFCToolBarFontComboBox();
```

### <a name="parameters"></a>Parameter

*uiID*<br/>
[in] Die Befehls-ID des Kombinationsfelds.

*iImage*<br/>
[in] Der nullbasierte Index eines Symbolleistenabbilds. Das Bild befindet sich im [CMFCToolBarImages-Klassenobjekt,](../../mfc/reference/cmfctoolbarimages-class.md) das die [CMFCToolBar-Klasse](../../mfc/reference/cmfctoolbar-class.md) verwaltet.

*nFontType*<br/>
[in] Die Schriftarten, die das Kombinationsfeld enthält. Dieser Parameter kann eine Kombination (boolescher ODER) der folgenden Werte sein:

DEVICE_FONTTYPE

RASTER_FONTTYPE

TRUETYPE_FONTTYPE

*nCharSet*<br/>
[in] Wenn auf DEFAULT_CHARSET festgelegt ist, enthält das Kombinationsfeld alle eindeutig benannten Schriftarten in allen Zeichensätzen. (Wenn zwei Schriftarten mit demselben Namen vorhanden sind, enthält das Kombinationsfeld eine davon.) Wenn auf einen gültigen Zeichensatzwert festgelegt, enthält das Kombinationsfeld nur Schriftarten im angegebenen Zeichensatz. Eine Liste möglicher Zeichensätze finden Sie unter [LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

*dwStyle*<br/>
[in] Der Stil des Kombinationsfelds. (siehe [Combo-Box Styles](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles))

*iWidth*<br/>
[in] Die Breite in Pixeln des Bearbeitungssteuerelements.

*nPitchAndFamilie*<br/>
[in] Wenn auf DEFAULT_PITCH festgelegt ist, enthält das Kombinationsfeld Schriftarten unabhängig von der Tonhöhe. Wenn auf FIXED_PITCH oder VARIABLE_PITCH festgelegt ist, enthält das Kombinationsfeld nur Schriftarten mit diesem Abstandstyp. Das Filtern basierend auf der Schriftfamilie wird derzeit nicht unterstützt.

*pLstFontsExtern*<br/>
[out] Zeiger auf ein [CObList-Klassenobjekt,](../../mfc/reference/coblist-class.md) das die verfügbaren Schriftarten speichert.

### <a name="remarks"></a>Bemerkungen

Normalerweise `CMFCToolBarFontComboBox` speichern Objekte die Liste der verfügbaren `CObList` Schriftarten in einem einzelnen freigegebenen Objekt. Wenn Sie die zweite Überladung des Konstruktors verwenden und einen gültigen Zeiger `CMFCToolBarFontComboBox` auf *pLstFontsExternal*bereitstellen, füllt dieses Objekt stattdessen die Punkte aus, auf die `CObList` *pLstFontsExternal* mit verfügbaren Schriftarten verweist.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird `CMFCToolBarFontComboBox` veranschaulicht, wie ein Objekt erstellt wird. Dieser Codeausschnitt ist Teil des [WordPad-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]

## <a name="cmfctoolbarfontcomboboxgetfontdesc"></a><a name="getfontdesc"></a>CMFCToolBarFontComboBox::GetFontDesc

Gibt einen Zeiger `CMFCFontInfo` auf das Objekt für einen angegebenen Index im Kombinationsfeld zurück.

```
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;
```

### <a name="parameters"></a>Parameter

*iIndex*<br/>
[in] Gibt den nullbasierten Index eines Kombinationsfeldelements an.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein `CMFCFontInfo`-Objekt. Wenn *iIndex* keinen gültigen Elementindex angibt, lautet der Rückgabewert NULL.

## <a name="cmfctoolbarfontcomboboxm_nfontheight"></a><a name="m_nfontheight"></a>CMFCToolBarFontComboBox::m_nFontHeight

Gibt die Höhe (in Pixel) von Zeichen im Schriftkombinationsfeld an, wenn das Kombinationsfeld einen Besitzerzeichnungsstil aufweist.

```
static int m_nFontHeight
```

### <a name="remarks"></a>Bemerkungen

Wenn `m_nFontHeight` die Variable 0 ist, wird die Höhe automatisch entsprechend der Standardschriftart des Kombinationsfelds berechnet. Die Höhe umfasst sowohl den Aufstieg von Zeichen über der Grundlinie als auch den Abstieg von Zeichen unterhalb der Grundlinie.

## <a name="cmfctoolbarfontcomboboxsetfont"></a><a name="setfont"></a>CMFCToolBarFontComboBox::SetFont

Wählt die Schriftart im Schriftkombinationsfeld entsprechend dem Schriftnamen und dem Zeichensatz aus, die in den Parametern angegeben sind.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET,
    BOOL bExact=FALSE);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
[in] Gibt den Schriftnamen oder das Präfix an.

*nCharSet*<br/>
[in] Gibt den Zeichensatz an.

*bGenau*<br/>
[in] Gibt an, ob *lpszName* den Schriftartnamen oder das Schriftartpräfix enthält.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Schriftart erfolgreich ausgewählt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn *bExact* TRUE ist, wählt diese Methode eine Schriftart aus, die genau mit dem Namen übereinstimmt, den Sie als *lpszName*angegeben haben. Wenn *bExact* FALSE ist, wählt diese Methode eine Schriftart aus, die mit dem als *lpszName* angegebenen Text beginnt und den Zeichensatz verwendet, den Sie als *nCharSet*angegeben haben. Wenn *nCharSet* auf DEFAULT_CHARSET festgelegt ist, wird der Zeichensatz ignoriert, und nur *lpszName* wird verwendet, um eine Schriftart auszuwählen.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar-Klasse](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton-Klasse](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton-Klasse](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo-Klasse](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Exemplarische Vorgehensweise: Steuerelemente in eine Symbolleiste einfügen](../../mfc/walkthrough-putting-controls-on-toolbars.md)
