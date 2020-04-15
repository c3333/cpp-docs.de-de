---
title: CMFCRibbonLabel-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::SetACCData
helpviewer_keywords:
- CMFCRibbonLabel [MFC], CMFCRibbonLabel
- CMFCRibbonLabel [MFC], SetACCData
ms.assetid: 0346c891-83bf-4f20-b8a1-c84cf2aadced
ms.openlocfilehash: cd30e374441661368d3ea7abf5177424f8dffb3c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375125"
---
# <a name="cmfcribbonlabel-class"></a>CMFCRibbonLabel-Klasse

Implementiert eine nicht anklickbare Bezeichnung für ein Menüband.

## <a name="syntax"></a>Syntax

```
class CMFCRibbonLabel : public CMFCRibbonButton
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonLabel::CMFCRibbonLabel](#cmfcribbonlabel)|Erstellt und initialisiert `CMFCRibbonLabel` ein Objekt mit der angegebenen Textzeichenfolge.|
|`CMFCRibbonLabel::~CMFCRibbonLabel`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMFCRibbonLabel::CreateObject`|Wird vom Framework verwendet, um eine dynamische Instanz dieses Klassentyps zu erstellen.|
|`CMFCRibbonLabel::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|
|[CMFCRibbonLabel::SetACCData](#setaccdata)|Bestimmt die Eingabehilfendaten für das aktuelle Multifunktionsbandbeschriftungselement. (Überschreibt [CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|

### <a name="remarks"></a>Bemerkungen

Nachdem Sie eine Multifunktionsleistenbeschriftung erstellt haben, fügen Sie sie einem Bedienfeld hinzu, indem Sie [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add)aufrufen.

Sie können der Schnellzugriffssymbolleiste keine Multifunktionsleistenbeschriftung hinzufügen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxRibbonLabel.h

## <a name="cmfcribbonlabelcmfcribbonlabel"></a><a name="cmfcribbonlabel"></a>CMFCRibbonLabel::CMFCRibbonLabel

Erstellt und initialisiert ein [CMFCRibbonLabel-Objekt,](../../mfc/reference/cmfcribbonlabel-class.md) das die angegebene Textzeichenfolge anzeigt.

```
CMFCRibbonLabel(
    LPCTSTR lpszText,
    BOOL bIsMultiLine = FALSE);
```

### <a name="parameters"></a>Parameter

*lpszText*<br/>
[in] Der Text, der in der Beschriftung angezeigt werden soll.

*bIsMultiLine*<br/>
[in] TRUE, um anzugeben, dass es sich bei der Bezeichnung um eine mehrzeilige Beschriftung handelt. andernfalls FALSE.

## <a name="cmfcribbonlabelsetaccdata"></a><a name="setaccdata"></a>CMFCRibbonLabel::SetACCData

Bestimmt die Eingabehilfendaten für das aktuelle Multifunktionsbandbeschriftungselement.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parameter

*pParent*<br/>
[in] Stellt das übergeordnete Fenster der aktuellen Multifunktionsleistenbeschriftung dar.

*Daten*<br/>
[out] Ein Objekt `CAccessibilityData` des Typs, das mit den Eingabehilfendaten der aktuellen Multifunktionsleistenbeschriftung aufgefüllt wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der *Datenparameter* erfolgreich mit den Eingabehilfendaten der aktuellen Multifunktionsbandbeschriftung aufgefüllt wurde. andernfalls FALSE.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton-Klasse](../../mfc/reference/cmfcribbonbutton-class.md)
