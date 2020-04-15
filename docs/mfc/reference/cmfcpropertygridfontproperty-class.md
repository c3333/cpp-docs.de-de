---
title: CMFCPropertyGridFontProperty-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetLogFont
helpviewer_keywords:
- CMFCPropertyGridFontProperty [MFC], CMFCPropertyGridFontProperty
- CMFCPropertyGridFontProperty [MFC], GetColor
- CMFCPropertyGridFontProperty [MFC], GetLogFont
ms.assetid: 83693f33-bbd3-4fcb-a9ad-fa79fcf2ca24
ms.openlocfilehash: a1c9905d8d7f32a049496c4e164c9eaac13455d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361841"
---
# <a name="cmfcpropertygridfontproperty-class"></a>CMFCPropertyGridFontProperty-Klasse

Die `CMFCPropertyGridFileProperty` Klasse unterstützt ein Eigenschaftenlistensteuerelement, das ein Dialogfeld für die Schriftartauswahl öffnet.

## <a name="syntax"></a>Syntax

```
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty](#cmfcpropertygridfontproperty)|Erstellt ein `CMFCPropertyGridFontProperty`-Objekt.|
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMFCPropertyGridFontProperty::FormatProperty`|Formatiert die Textdarstellung eines Eigenschaftswerts. (Überschreibt [CMFCPropertyGridProperty::FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|
|[CMFCPropertyGridFontProperty::GetColor](#getcolor)|Ruft die Schriftartfarbe ab, die der Benutzer aus dem Dialogfeld Schriftart auswählt.|
|[CMFCPropertyGridFontProperty::GetLogFont](#getlogfont)|Ruft die Schriftart ab, die der Benutzer aus dem Dialogfeld Schriftart auswählt.|
|`CMFCPropertyGridFontProperty::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|
|`CMFCPropertyGridFontProperty::OnClickButton`|Wird vom Framework aufgerufen, wenn der Benutzer auf eine Schaltfläche klickt, die in einer Eigenschaft enthalten ist. (Überschreibt [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

## <a name="remarks"></a>Bemerkungen

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)

## <a name="requirements"></a>Anforderungen

**Kopf:** afxpropertygridctrl.h

## <a name="cmfcpropertygridfontpropertycmfcpropertygridfontproperty"></a><a name="cmfcpropertygridfontproperty"></a>CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty

Erstellt ein `CMFCPropertyGridFontProperty`-Objekt.

```
CMFCPropertyGridFontProperty(
    const CString& strName,
    LOGFONT& lf,
    DWORD dwFontDialogFlags = CF_EFFECTS | CF_SCREENFONTS,
    LPCTSTR lpszDescr = NULL,
    DWORD_PTR dwData = 0,
    COLORREF color = (COLORREF)-1);
```

### <a name="parameters"></a>Parameter

*strName*<br/>
[in] Der Name der Eigenschaft.

*Lf*<br/>
[in] Eine logische Schriftartstruktur, die die Attribute der Schriftart angibt.

*dwFontDialogFlags*<br/>
[in] Formatvorlagen, die auf das Schriftartdialogfeld angewendet werden, das angezeigt wird, wenn Sie auf die Dropdown-Schaltfläche Eigenschaftenwert klicken. Der Standardwert ist die bitweise Kombination (OR) von CF_EFFECTS und CF_SCREENFONTS. Weitere Informationen finden Sie im *Parameter Flags* der [CHOOSEFONT-Struktur](/windows/win32/api/commdlg/ns-commdlg-choosefontw).

*lpszDescr*<br/>
[in] Beschreibung der font-Eigenschaft. Der Standardwert ist NULL.

*dwData*<br/>
[in] Anwendungsspezifische Daten, z. B. eine ganze Zahl oder ein Zeiger auf andere Daten, die der Eigenschaft zugeordnet sind. Der Standardwert ist 0.

*Farbe*<br/>
[in] Die Farbe der Schriftart. Der Standardwert ist die Standardfarbe.

### <a name="remarks"></a>Bemerkungen

Ein `CMFCPropertyGridFontProperty` Objekt stellt eine Schriftarteigenschaft in einem Eigenschaftenraster-Schriftartsteuerelement dar.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCPropertyGridFontProperty` wie ein Objekt der Klasse erstellt wird. Dieses Beispiel ist Teil des [Beispiels "Neue Steuerelemente "Neue Steuerelemente ".](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]

## <a name="cmfcpropertygridfontpropertygetcolor"></a><a name="getcolor"></a>CMFCPropertyGridFontProperty::GetColor

Ruft die Schriftartfarbe ab, die der Benutzer aus dem Dialogfeld Schriftart auswählt.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Rückgabewert

Ein RGB-Farbwert, der die ausgewählte Schriftfarbe darstellt.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcpropertygridfontpropertygetlogfont"></a><a name="getlogfont"></a>CMFCPropertyGridFontProperty::GetLogFont

Ruft die Schriftart ab, die der Benutzer aus dem Dialogfeld Schriftart auswählt.

```
LPLOGFONT GetLogFont();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine [LOGFONT-Struktur,](/windows/win32/api/wingdi/ns-wingdi-logfontw) die die ausgewählte Schriftart beschreibt.

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl-Klasse](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty-Klasse](../../mfc/reference/cmfcpropertygridproperty-class.md)
