---
title: CMFCRibbonFontComboBox-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::BuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetCharSet
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontDesc
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontType
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetPitchAndFamily
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::RebuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::SetFont
helpviewer_keywords:
- CMFCRibbonFontComboBox [MFC], CMFCRibbonFontComboBox
- CMFCRibbonFontComboBox [MFC], BuildFonts
- CMFCRibbonFontComboBox [MFC], GetCharSet
- CMFCRibbonFontComboBox [MFC], GetFontDesc
- CMFCRibbonFontComboBox [MFC], GetFontType
- CMFCRibbonFontComboBox [MFC], GetPitchAndFamily
- CMFCRibbonFontComboBox [MFC], RebuildFonts
- CMFCRibbonFontComboBox [MFC], SetFont
ms.assetid: 33b4db50-df4f-45fa-8f05-2e6e73c31435
ms.openlocfilehash: 822f4f6fe76bb5b82b455daec54ed96568ea6ba7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375164"
---
# <a name="cmfcribbonfontcombobox-class"></a>CMFCRibbonFontComboBox-Klasse

Implementiert ein Kombinationsfeld, das eine Liste von Schriftarten enthält. Das Kombinationsfeld kann in einem Menübandbereich platziert werden.

## <a name="syntax"></a>Syntax

```
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|Destruktor.|

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](#cmfcribbonfontcombobox)|Erstellt und initialisiert ein `CMFCRibbonFontComboBox`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)|Füllt das Schriftartkombinationsfeld für das Menüband mit Schriftarten des angegebenen Schriftarttyps, Zeichensatzes, der Zeichenbreite und Schriftfamilie auf.|
|`CMFCRibbonFontComboBox::CreateObject`|Wird vom Framework verwendet, um eine dynamische Instanz dieses Klassentyps zu erstellen.|
|[CMFCRibbonFontComboBox::GetCharSet](#getcharset)|Gibt den angegebenen Zeichensatz zurück.|
|[CMFCRibbonFontComboBox::GetFontDesc](#getfontdesc)||
|[CMFCRibbonFontComboBox::GetFontType](#getfonttype)|Gibt zurück, welche Schriftarttypen im Kombinationsfeld angezeigt werden. Gültige Optionen sind DEVICE_FONTTYPE, RASTER_FONTTYPE, und TRUETYPE_FONTTYPE oder jede bitweise Kombination davon.|
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|Gibt die Schriftbreite und Schriftfamilie der Schriftarten zurück, die im Kombinationsfeld angezeigt werden.|
|`CMFCRibbonFontComboBox::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|Füllt das Schriftartkombinationsfeld für das Menüband mit Schriftarten des zuvor angegebenen Schriftarttyps, Zeichensatzes, der Zeichenbreite und Schriftfamilie auf.|
|[CMFCRibbonFontComboBox::SetFont](#setfont)|Wählt die angegebene Schriftart im Kombinationsfeld aus.|

## <a name="remarks"></a>Bemerkungen

Nachdem Sie `CMFCRibbonFontComboBox` ein Objekt erstellt haben, fügen Sie es einem Multifunktionsleistenbedienfeld hinzu, indem Sie [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add)aufrufen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

[CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxRibbonComboBox.h

## <a name="cmfcribbonfontcomboboxbuildfonts"></a><a name="buildfonts"></a>CMFCRibbonFontComboBox::BuildFonts

Füllt das Kombinationsfeld auf dem Menüband mit Schriftarten.

```
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```

### <a name="parameters"></a>Parameter

*nFontType*<br/>
[in] Gibt den Schriftarttyp der hinzuzufügenden Schriftarten an.

*nCharSet*<br/>
[in] Gibt den Zeichensatz der hinzuzufügenden Schriftarten an.

*nPitchAndFamilie*<br/>
[in] Gibt die Tonhöhe und die Familie der hinzuzufügenden Schriftarten an.

## <a name="cmfcribbonfontcomboboxcmfcribbonfontcombobox"></a><a name="cmfcribbonfontcombobox"></a>CMFCRibbonFontComboBox::CMFCRibbonFontComboBox

Erstellt und initialisiert ein [CMFCRibbonFontComboBox-Objekt.](../../mfc/reference/cmfcribbonfontcombobox-class.md)

```
CMFCRibbonFontComboBox(
    UINT nID,
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH,
    int nWidth = -1);
```

### <a name="parameters"></a>Parameter

*nID*<br/>
[in] Die Befehls-ID des Befehls, der ausgeführt wird, wenn der Benutzer ein Element aus dem Kombinationsfeld auswählt.

*nFontType*<br/>
[in] Gibt an, welche Schriftarten im Kombinationsfeld angezeigt werden sollen. Gültige Optionen sind DEVICE_FONTTYPE, RASTER_FONTTYPE, und TRUETYPE_FONTTYPE oder jede bitweise Kombination davon.

*nCharSet*<br/>
[in] Filtert die Schriftarten im Kombinationsfeld nach Schriftarten, die zum angegebenen Zeichensatz gehören.

*nPitchAndFamilie*<br/>
[in] Gibt die Tonhöhe und die Familie der Schriftarten an, die im Kombinationsfeld angezeigt werden.

*nWidth*<br/>
[in] Gibt die Breite des Kombinationsfelds in Pixel an.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu möglichen *nFontType-Parameterwerten* finden Sie unter [EnumFontFamProc](/previous-versions/dd162621\(v=vs.85\)) in der Windows SDK-Dokumentation.

Weitere Informationen zu gültigen Zeichensätzen, die *nCharSet*zugewiesen werden können, und zu gültigen Werten, die *nPitchAndFamily*zugewiesen werden können, finden Sie unter [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) in der Windows SDK-Dokumentation.

## <a name="cmfcribbonfontcomboboxgetfontdesc"></a><a name="getfontdesc"></a>CMFCRibbonFontComboBox::GetFontDesc

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

```
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;
```

### <a name="parameters"></a>Parameter

[in] *iIndex*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonfontcomboboxrebuildfonts"></a><a name="rebuildfonts"></a>CMFCRibbonFontComboBox::RebuildFonts

Füllt das Kombinationsfeld auf dem Menüband mit Schriftarten eines zuvor angegebenen Schrifttyps, Zeichensatzes sowie Tonhöhe und Familie.

```
void RebuildFonts();
```

### <a name="remarks"></a>Bemerkungen

Sie können den Schrifttyp, den Zeichensatz sowie die Tonhöhe und die Familie der Schriftarten angeben, die in das Kombinationsfeld Multifunktionsleistenschriftkombination im [Konstruktor](#cmfcribbonfontcombobox) für diese Klasse aufgenommen werden sollen, oder indem Sie [CMFCRibbonFontComboBox::BuildFonts](#buildfonts)aufrufen.

## <a name="cmfcribbonfontcomboboxsetfont"></a><a name="setfont"></a>CMFCRibbonFontComboBox::SetFont

Wählt die angegebene Schriftart im Kombinationsfeld aus.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet = DEFAULT_CHARSET,
    BOOL bExact = FALSE);
```

### <a name="parameters"></a>Parameter

'lpszName* Gibt den Namen der auszuwählenden Schriftart an.

*nCharSet*<br/>
Gibt den Zeichensatz für die ausgewählte Schriftart an.

*bGenau*<br/>
TRUE, um anzugeben, dass der Zeichensatz bei der Auswahl einer Schriftart übereinstimmen muss; FALSE, um anzugeben, dass der Zeichensatz bei der Auswahl einer Schriftart ignoriert werden kann.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die angegebene Schriftart gefunden und ausgewählt wurde; andernfalls Null.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonfontcomboboxgetcharset"></a><a name="getcharset"></a>CMFCRibbonFontComboBox::GetCharSet

Gibt den angegebenen Zeichensatz zurück.

```
BYTE GetCharSet() const;
```

### <a name="return-value"></a>Rückgabewert

Zeichensatz (siehe LOGFONT in der Windows SDK-Dokumentation).

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonfontcomboboxgetfonttype"></a><a name="getfonttype"></a>CMFCRibbonFontComboBox::GetFontType

Gibt zurück, welche Schriftarttypen im Kombinationsfeld angezeigt werden. Gültige Optionen sind DEVICE_FONTTYPE, RASTER_FONTTYPE, und TRUETYPE_FONTTYPE oder jede bitweise Kombination davon.

```
int GetFontType() const;
```

### <a name="return-value"></a>Rückgabewert

Schriftarten (siehe EnumFontFamProc in der Windows SDK-Dokumentation).

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonfontcomboboxgetpitchandfamily"></a><a name="getpitchandfamily"></a>CMFCRibbonFontComboBox::GetPitchAndFamilie

Gibt die Schriftbreite und Schriftfamilie der Schriftarten zurück, die im Kombinationsfeld angezeigt werden.

```
BYTE GetPitchAndFamily() const;
```

### <a name="return-value"></a>Rückgabewert

Pitch und die Familie (siehe LOGFONT in der Windows SDK-Dokumentation).

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonComboBox-Klasse](../../mfc/reference/cmfcribboncombobox-class.md)
