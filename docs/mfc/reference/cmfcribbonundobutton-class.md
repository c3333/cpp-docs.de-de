---
title: CMFCRibbonUndoButton-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::AddUndoAction
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CleanUpUndoList
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::GetActionNumber
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::HasMenu
helpviewer_keywords:
- CMFCRibbonUndoButton [MFC], CMFCRibbonUndoButton
- CMFCRibbonUndoButton [MFC], AddUndoAction
- CMFCRibbonUndoButton [MFC], CleanUpUndoList
- CMFCRibbonUndoButton [MFC], GetActionNumber
- CMFCRibbonUndoButton [MFC], HasMenu
ms.assetid: 5c42adf7-871d-4239-901e-47ae7fb816fc
ms.openlocfilehash: f30e6f78b0988b791617ee0926cf649377972ce2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368812"
---
# <a name="cmfcribbonundobutton-class"></a>CMFCRibbonUndoButton-Klasse

Die `CMFCRibbonUndoButton` Klasse implementiert eine Dropdown-Listenschaltfläche, die die neuesten Benutzerbefehle enthält. Benutzer können einen oder mehrere der neuesten Befehle aus der Dropdownliste auswählen, um sie entweder erneut zu wiederholen oder rückgängig zu machen.

## <a name="syntax"></a>Syntax

```
class CMFCRibbonUndoButton : public CMFCRibbonGallery
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonUndoButton::CMFCRibbonUndoButton](#cmfcribbonundobutton)|Erstellt ein `CMFCRibbonUndoButton` neues Objekt mithilfe der von Ihnen angegebenen Befehls-ID, Textbeschriftung und Bilder aus der Bildliste des übergeordneten Objekts.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonUndoButton::AddUndoAction](#addundoaction)|Fügt der Liste der Aktionen eine neue Aktion hinzu.|
|[CMFCRibbonUndoButton::CleanUpUndoList](#cleanupundolist)|Löscht die Aktionsliste, d. h. die Dropdownliste.|
|[CMFCRibbonUndoButton::GetActionNumber](#getactionnumber)|Bestimmt die Anzahl der Elemente, die ein Benutzer aus der Dropdownliste ausgewählt hat.|
|[CMFCRibbonUndoButton::HasMenu](#hasmenu)|Gibt an, ob das Objekt ein Menü enthält.|

## <a name="remarks"></a>Bemerkungen

Die `CMFCRibbonUndoButton` Klasse verwendet einen Stapel, um die Dropdownliste darzustellen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCRibbonUndoButton` wie ein Objekt der Klasse erstellt und der Liste der Aktionen eine neue Aktion hinzugefügt wird. Dieser Codeausschnitt ist Teil des Beispiels für [Multifunktionsleisten-Gadgets](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_RibbonGadgets#2](../../mfc/reference/codesnippet/cpp/cmfcribbonundobutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)

[CMFCRibbonUndoButton](../../mfc/reference/cmfcribbonundobutton-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxribbonundobutton.h

## <a name="cmfcribbonundobuttonaddundoaction"></a><a name="addundoaction"></a>CMFCRibbonUndoButton::AddUndoAction

Fügt der Liste der Aktionen eine neue Aktion hinzu.

```
void AddUndoAction(LPCTSTR lpszLabel);
```

### <a name="parameters"></a>Parameter

*lpszLabel*<br/>
[in] Die Aktionsbeschriftung, die in der Dropdownliste angezeigt wird.

## <a name="cmfcribbonundobuttoncleanupundolist"></a><a name="cleanupundolist"></a>CMFCRibbonUndoButton::CleanUpUndoList

Löscht die Aktionsliste, d. h. die Dropdownliste.

```
void CleanUpUndoList();
```

## <a name="cmfcribbonundobuttoncmfcribbonundobutton"></a><a name="cmfcribbonundobutton"></a>CMFCRibbonUndoButton::CMFCRibbonUndoButton

Erstellt ein `CMFCRibbonUndoButton` neues Objekt mithilfe der von Ihnen angegebenen Befehls-ID, Textbeschriftung und Bilder aus der Bildliste des übergeordneten Objekts.

```
CMFCRibbonUndoButton(
    UINT nID,
    LPCTSTR lpszText,
    int nSmallImageIndex=-1,
    int nLargeImageIndex=-1);

CMFCRibbonUndoButton(
    UINT nID,
    LPCTSTR lpszText,
    HICON hIcon);
```

### <a name="parameters"></a>Parameter

*nID*<br/>
[in] Gibt den Befehlsbezeichner an.

*lpszText*<br/>
[in] Gibt die Textbeschriftung der Schaltfläche an.

*nSmallImageIndex*<br/>
[in] Nullbasierter Index in der Bildliste des übergeordneten Objekts für das kleine Bild der Schaltfläche.

*nLargeImageIndex*<br/>
[in] Nullbasierter Index in der Bildliste des übergeordneten Objekts für das große Bild der Schaltfläche.

*hIcon*<br/>
[in] Ein Handle für ein Symbol, das Sie als Schaltflächenbild verwenden können.

## <a name="cmfcribbonundobuttongetactionnumber"></a><a name="getactionnumber"></a>CMFCRibbonUndoButton::GetActionNumber

Bestimmt die Anzahl der Elemente, die ein Benutzer aus der Dropdownliste ausgewählt hat.

```
int GetActionNumber() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente, die ein Benutzer ausgewählt hat.

## <a name="cmfcribbonundobuttonhasmenu"></a><a name="hasmenu"></a>CMFCRibbonUndoButton::HasMenu

Gibt an, ob das Objekt ein Menü enthält.

```
virtual BOOL HasMenu() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt immer TRUE zurück.

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonGallery-Klasse](../../mfc/reference/cmfcribbongallery-class.md)<br/>
[CMFCRibbonButton-Klasse](../../mfc/reference/cmfcribbonbutton-class.md)
