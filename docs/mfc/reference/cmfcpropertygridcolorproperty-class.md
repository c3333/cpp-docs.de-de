---
title: CMFCPropertyGridColorProperty-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableAutomaticButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableOtherButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColumnsNumber
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetOriginalValue
helpviewer_keywords:
- CMFCPropertyGridColorProperty [MFC], CMFCPropertyGridColorProperty
- CMFCPropertyGridColorProperty [MFC], EnableAutomaticButton
- CMFCPropertyGridColorProperty [MFC], EnableOtherButton
- CMFCPropertyGridColorProperty [MFC], GetColor
- CMFCPropertyGridColorProperty [MFC], SetColor
- CMFCPropertyGridColorProperty [MFC], SetColumnsNumber
- CMFCPropertyGridColorProperty [MFC], SetOriginalValue
ms.assetid: af37be93-a91e-40a2-9a65-0f3412c6f0f8
ms.openlocfilehash: 62015f384fa5f72ceeceed2605cbf9a6b646a1eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375319"
---
# <a name="cmfcpropertygridcolorproperty-class"></a>CMFCPropertyGridColorProperty-Klasse

Die `CMFCPropertyGridColorProperty`-Klasse unterstützt ein Eigenschaftslisten-Steuerelement, über das ein Farbauswahl-Dialogfeld geöffnet werden kann.

## <a name="syntax"></a>Syntax

```
class CMFCPropertyGridColorProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty](#cmfcpropertygridcolorproperty)|Erstellt ein `CMFCPropertyGridColorProperty`-Objekt.|
|`CMFCPropertyGridColorProperty::~CMFCPropertyGridColorProperty`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCPropertyGridColorProperty::EnableAutomaticButton](#enableautomaticbutton)|Aktiviert die *automatische* Schaltfläche im Dialogfeld Farbauswahl. (Die Standard-Automatiktaste ist mit **Automatisch**beschriftet.)|
|[CMFCPropertyGridColorProperty::EnableOtherButton](#enableotherbutton)|Aktiviert die *andere* Schaltfläche im Dialogfeld Farbauswahl. (Die andere Standardschaltfläche ist mit **Mehr Farben**beschriftet .)|
|`CMFCPropertyGridColorProperty::FormatProperty`|Formatiert die Textdarstellung eines Eigenschaftswerts. (Überschreibt [CMFCPropertyGridProperty::FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|
|[CMFCPropertyGridColorProperty::GetColor](#getcolor)|Ruft die aktuelle Farbe der Eigenschaft ab.|
|`CMFCPropertyGridColorProperty::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|
|`CMFCPropertyGridColorProperty::OnClickButton`|Wird vom Framework aufgerufen, wenn der Benutzer auf eine Schaltfläche klickt, die in einer Eigenschaft enthalten ist. (Überschreibt [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|
|`CMFCPropertyGridColorProperty::OnDrawValue`|Wird vom Framework aufgerufen, um die Liste der Eigenschaftenwerte anzuzeigen. (Überschreibt [CMFCPropertyGridProperty::OnDrawValue](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawvalue).)|
|`CMFCPropertyGridColorProperty::OnEdit`|Wird vom Framework aufgerufen, wenn der Benutzer dabei ist, einen Eigenschaftenwert zu bearbeiten. (Überschreibt [CMFCPropertyGridProperty::OnEdit](../../mfc/reference/cmfcpropertygridproperty-class.md#onedit).)|
|`CMFCPropertyGridColorProperty::OnUpdateValue`|Wird vom Framework aufgerufen, wenn der Wert einer änderbaren Eigenschaft geändert wurde. (Überschreibt [CMFCPropertyGridProperty::OnUpdateValue](../../mfc/reference/cmfcpropertygridproperty-class.md#onupdatevalue).)|
|[CMFCPropertyGridColorProperty::SetColor](#setcolor)|Legt eine neue Farbe für die Eigenschaft fest.|
|[CMFCPropertyGridColorProperty::SetColumnsNumber](#setcolumnsnumber)|Gibt die Anzahl der Spalten in der aktuellen Farbe des Eigenschaftenrasters an.|
|[CMFCPropertyGridColorProperty::SetOriginalValue](#setoriginalvalue)|Legt den ursprünglichen Wert einer bearbeitbaren Eigenschaft fest.|

## <a name="remarks"></a>Bemerkungen

Die `CMFCPropertyGridColorProperty` -Klasse unterstützt eine Farbeigenschaft, die zu einem Eigenschaftenlisten-Steuerelement hinzugefügt werden kann. Weitere Informationen finden Sie in der [CMFCPropertyGridCtrl-Klasse](../../mfc/reference/cmfcpropertygridctrl-class.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie ein Objekt `CMFCPropertyGridColorProperty`- Klasse erstellt und mithilfe der verschiedenen Methoden der `CMFCPropertyGridColorProperty`-Klasse konfiguriert wird. Der Code erläutert, wie die Schaltflächen „automatisch“ und „sonstige“ aktiviert werden und wie die Farbe und die Spaltenanzahl festgelegt wird. Dieses Beispiel ist Teil des [Beispiels "Neue Steuerelemente "Neue Steuerelemente ".](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_NewControls#13](../../mfc/reference/codesnippet/cpp/cmfcpropertygridcolorproperty-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridColorProperty](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)

## <a name="requirements"></a>Anforderungen

**Kopf:** afxpropertygridctrl.h

## <a name="cmfcpropertygridcolorpropertycmfcpropertygridcolorproperty"></a><a name="cmfcpropertygridcolorproperty"></a>CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty

Erstellt ein `CMFCPropertyGridColorProperty`-Objekt.

```
CMFCPropertyGridColorProperty(
    const CString& strName,
    const COLORREF& color,
    CPalette* pPalette = NULL,
    LPCTSTR lpszDescr = NULL,
    DWORD_PTR dwData = 0);
```

### <a name="parameters"></a>Parameter

*strName*<br/>
[in] Der Name der Eigenschaft.

*Farbe*<br/>
[in] Der Farbwert der Eigenschaft.

*pPalette*<br/>
[in] Zeiger auf eine Farbpalette. Der Standardwert ist NULL.

*lpszDescr*<br/>
[in] Die Eigenschaftenbeschreibung. Der Standardwert ist NULL.

*dwData*<br/>
[in] Anwendungsspezifische Daten, z. B. eine ganze Zahl oder ein Zeiger auf andere Daten, die der Eigenschaft zugeordnet sind. Der Standardwert ist 0.

## <a name="cmfcpropertygridcolorpropertyenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCPropertyGridColorProperty::EnableAutomaticButton

Aktiviert die *automatische* Schaltfläche im Dialogfeld Farbauswahl. (Die Standard-Automatiktaste ist mit **Automatisch**beschriftet.)

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parameter

*lpszLabel*<br/>
[in] Der Beschriftungstext der automatischen Schaltfläche.

*colorAutomatic*<br/>
[in] Der RGB-Farbwert der automatischen (Standard-)Farbe.

*bEnable*<br/>
[in] TRUE, um die automatische Taste zu aktivieren; andernfalls FALSE. Der Standardwert ist TRUE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcpropertygridcolorpropertyenableotherbutton"></a><a name="enableotherbutton"></a>CMFCPropertyGridColorProperty::EnableOtherButton

Aktiviert die *andere* Schaltfläche im Dialogfeld Farbauswahl. (Die andere Standardschaltfläche ist mit **Mehr Farben**beschriftet .)

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg = TRUE,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parameter

*lpszLabel*<br/>
[in] Der Beschriftungstext der anderen Schaltfläche.

*bAltColorDlg*<br/>
[in] TRUE, um `CMFCColorDialog` das Dialogfeld anzuzeigen; FALSE, um das Dialogfeld für die Standardfarbauswahl anzuzeigen. Der Standardwert ist TRUE.

*bEnable*<br/>
[in] TRUE, um die andere Schaltfläche anzuzeigen; andernfalls FALSE.  Der Standardwert ist TRUE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcpropertygridcolorpropertygetcolor"></a><a name="getcolor"></a>CMFCPropertyGridColorProperty::GetColor

Ruft die aktuelle Farbe der Eigenschaft ab.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Rückgabewert

Ein RGB-Farbwert.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcpropertygridcolorpropertysetcolor"></a><a name="setcolor"></a>CMFCPropertyGridColorProperty::SetColor

Legt eine neue Farbe für die Eigenschaft fest.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parameter

*Farbe*<br/>
[in] Ein RGB-Farbwert.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcpropertygridcolorpropertysetcolumnsnumber"></a><a name="setcolumnsnumber"></a>CMFCPropertyGridColorProperty::SetColumnsNumber

Gibt die Anzahl der Spalten in der aktuellen Farbe des Eigenschaftenrasters an.

```
void SetColumnsNumber(int nColumnsNumber);
```

### <a name="parameters"></a>Parameter

*nColumnsNumber*<br/>
[in] Die bevorzugte Anzahl von Spalten im Farbeigenschaftsraster.

### <a name="remarks"></a>Bemerkungen

Diese Methode legt den `m_nColumnsNumber` Wert des geschützten Datenmembers fest.

## <a name="cmfcpropertygridcolorpropertysetoriginalvalue"></a><a name="setoriginalvalue"></a>CMFCPropertyGridColorProperty::SetOriginalValue

Legt den ursprünglichen Wert einer bearbeitbaren Eigenschaft fest.

```
virtual void SetOriginalValue(const COleVariant& varValue);
```

### <a name="parameters"></a>Parameter

*varValue*<br/>
[in] Ein Wert.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die [CMFCPropertyGridProperty::ResetOriginalValue-Methode,](../../mfc/reference/cmfcpropertygridproperty-class.md#resetoriginalvalue) um den ursprünglichen Wert einer bearbeiteten Eigenschaft zurückzusetzen.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl-Klasse](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty-Klasse](../../mfc/reference/cmfcpropertygridproperty-class.md)
