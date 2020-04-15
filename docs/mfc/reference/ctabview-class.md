---
title: CTabView-Klasse
ms.date: 11/04/2016
f1_keywords:
- CTabView
- AFXTABVIEW/CTabView
- AFXTABVIEW/CTabView::AddView
- AFXTABVIEW/CTabView::FindTab
- AFXTABVIEW/CTabView::GetActiveView
- AFXTABVIEW/CTabView::GetTabControl
- AFXTABVIEW/CTabView::RemoveView
- AFXTABVIEW/CTabView::SetActiveView
- AFXTABVIEW/CTabView::IsScrollBar
- AFXTABVIEW/CTabView::OnActivateView
helpviewer_keywords:
- CTabView [MFC], AddView
- CTabView [MFC], FindTab
- CTabView [MFC], GetActiveView
- CTabView [MFC], GetTabControl
- CTabView [MFC], RemoveView
- CTabView [MFC], SetActiveView
- CTabView [MFC], IsScrollBar
- CTabView [MFC], OnActivateView
ms.assetid: 8e6ecd9d-d28d-432b-8ec8-0446f0204d52
ms.openlocfilehash: ad30cbbf5de195708d2d357a76c38b661d095c2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365922"
---
# <a name="ctabview-class"></a>CTabView-Klasse

Die `CTabView` Klasse vereinfacht die Verwendung der Tabstopp-Steuerelementklasse ( [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)) in Anwendungen, die die Dokument-/Ansichtsarchitektur von MFC verwenden.

## <a name="syntax"></a>Syntax

```
class CTabbedView : public CView
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTabView::AddView](#addview)|Fügt dem Registerkartensteuerelement eine neue Ansicht hinzu.|
|[CTabView::FindTab](#findtab)|Gibt den Index der angegebenen Ansicht im Registerkartensteuerelement zurück.|
|[CTabView::GetActiveView](#getactiveview)|Gibt einen Zeiger auf die aktuell aktive Ansicht zurück|
|[CTabView::GetTabControl](#gettabcontrol)|Gibt einen Verweis auf das Registerkartensteuerelement zurück, das der Ansicht zugeordnet ist.|
|[CTabView::RemoveView](#removeview)|Entfernt die Ansicht aus dem Registerkartensteuerelement.|
|[CTabView::SetActiveView](#setactiveview)|Aktiviert eine Ansicht.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CtabView::IsScrollBar](#isscrollbar)|Wird vom Framework beim Erstellen einer Registerkartenansicht aufgerufen, um zu bestimmen, ob die Registerkartenansicht über eine gemeinsame horizontale Bildlaufleiste verfügt.|
|[CTabView::OnActivateView](#onactivateview)|Wird vom Framework aufgerufen, wenn die Registerkartenansicht aktiv oder inaktiv gemacht wird.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse erleichtert das Erstellen einer Registerkartenansicht in einer Dokument-/Ansichtsanwendung. `CTabView`ist `CView`eine -derived-Klasse, `CMFCTabCtrl` die ein eingebettetes Objekt enthält. `CTabView`behandelt alle Nachrichten, die `CMFCTabCtrl` zur Unterstützung des Objekts erforderlich sind. Leiten Sie einfach `CTabView` eine Klasse ab, und `CView`schließen Sie sie `AddView` an Ihre Anwendung an, und fügen Sie dann -abgeleitete Klassen mithilfe der Methode hinzu. Das Registerkartensteuerelement zeigt diese Ansichten als Registerkarten an.

Sie können z. B. ein Dokument haben, das auf unterschiedliche Weise dargestellt werden kann: als Kalkulationstabelle, als Diagramm, als bearbeitbares Formular usw. Sie können einzelne Ansichten erstellen, die die `CTabView`Daten nach Bedarf zeichnen, sie in Ihr -derived-Objekt einfügen und sie ohne zusätzliche Codierung auf die Registerkarte nieren lassen.

[TabbedView-Beispiel: MFC Tabbed View](../../overview/visual-cpp-samples.md) `CTabView`Application veranschaulicht die Verwendung von .

## <a name="example"></a>Beispiel

Das folgende Beispiel `CTabView` zeigt, wie im TabbedView-Beispiel verwendet wird.

[!code-cpp[NVC_MFC_TabbedView#1](../../mfc/reference/codesnippet/cpp/ctabview-class_1.h)]

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxTabView.h

## <a name="ctabviewaddview"></a><a name="addview"></a>CTabView::AddView

Fügt dem Registerkartensteuerelement eine Ansicht hinzu.

```
int AddView(
    CRuntimeClass* pViewClass,
    const CString& strViewLabel,
    int iIndex=-1,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>Parameter

*pViewClass*<br/>
[in] Ein Zeiger auf eine Laufzeitklasse der eingefügten Ansicht.

*strViewLabel*<br/>
[in] Gibt den Text der Registerkarte an.

*iIndex*<br/>
[in] Gibt die nullbasierte Position an, an der die Ansicht eingefügt werden soll. Wenn die Position -1 ist, wird die neue Registerkarte am Ende eingefügt.

*pContext*<br/>
[in] Ein Zeiger auf `CCreateContext` die Ansicht.

### <a name="return-value"></a>Rückgabewert

Ein Ansichtsindex, wenn diese Methode erfolgreich ist. Andernfalls: -1

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um dem In-Frame-Steuerelement, das in einen Frame eingebettet ist, eine Ansicht hinzuzufügen.

## <a name="ctabviewfindtab"></a><a name="findtab"></a>CTabView::FindTab

Gibt den Index der angegebenen Ansicht im Registerkartensteuerelement zurück.

```
int FindTab(HWND hWndView) const;
```

### <a name="parameters"></a>Parameter

*hWndView*<br/>
[in] Das Handle der Ansicht.

### <a name="return-value"></a>Rückgabewert

Der Index der Ansicht, wenn er gefunden wird; andernfalls -1.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um den Index einer Ansicht abzurufen, die über ein angegebenes Handle verfügt.

## <a name="ctabviewgetactiveview"></a><a name="getactiveview"></a>CTabView::GetActiveView

Gibt einen Zeiger auf die aktuell aktive Ansicht zurück.

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>Rückgabewert

Ein gültiger Zeiger auf die aktive Ansicht oder NULL, wenn keine aktive Ansicht vorhanden ist.

### <a name="remarks"></a>Bemerkungen

## <a name="ctabviewgettabcontrol"></a><a name="gettabcontrol"></a>CTabView::GetTabControl

Gibt einen Verweis auf das Registerkartensteuerelement zurück, das der Ansicht zugeordnet ist.

```
DECLARE_DYNCREATE CMFCTabCtrl& GetTabControl();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das Registerkartensteuerelement, das der Ansicht zugeordnet ist.

## <a name="ctabviewisscrollbar"></a><a name="isscrollbar"></a>CtabView::IsScrollBar

Wird vom Framework beim Erstellen einer Registerkartenansicht aufgerufen, um zu bestimmen, ob die Registerkartenansicht über eine gemeinsame horizontale Bildlaufleiste verfügt.

```
virtual BOOL IsScrollBar() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Registerkartenansicht zusammen mit einer freigegebenen Bildlaufleiste erstellt werden soll. Andernfalls lautet der Wert FALSE.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Methode auf, wenn ein *CTabView-Objekt* erstellt wird.

Überschreiben Sie die *IsScrollBar-Methode* in einer *CTabView*-derived-Klasse und geben TRUE zurück, wenn Sie eine Ansicht mit einer freigegebenen horizontalen Bildlaufleiste erstellen möchten.

## <a name="ctabviewonactivateview"></a><a name="onactivateview"></a>CTabView::OnActivateView

Wird vom Framework aufgerufen, wenn die Registerkartenansicht aktiv oder inaktiv gemacht wird.

```
virtual void OnActivateView(CView* view);
```

### <a name="parameters"></a>Parameter

*ansehen*<br/>
[in] Ein Zeiger auf die Ansicht.

### <a name="remarks"></a>Bemerkungen

Bei der Standardimplementierung wird keine Aktion ausgeführt. Überschreiben Sie diese `CTabView`Methode in einer -derived-Klasse, um diese Benachrichtigung zu verarbeiten.

## <a name="ctabviewremoveview"></a><a name="removeview"></a>CTabView::RemoveView

Entfernt die Ansicht aus dem Registerkartensteuerelement.

```
BOOL RemoveView(int iTabNum);
```

### <a name="parameters"></a>Parameter

*iTabNum*<br/>
[in] Der Index der zu entfernenden Ansicht.

### <a name="return-value"></a>Rückgabewert

Der Index der entfernten Ansicht, wenn diese Methode erfolgreich ist. Andernfalls -1.

### <a name="remarks"></a>Bemerkungen

## <a name="ctabviewsetactiveview"></a><a name="setactiveview"></a>CTabView::SetActiveView

Aktiviert eine Ansicht.

```
BOOL SetActiveView(int iTabNum);
```

### <a name="parameters"></a>Parameter

*iTabNum*<br/>
[in] Der nullbasierte Index der Registerkartenansicht.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die angegebene Ansicht aktiviert wurde, FALSE, wenn der Index der Ansicht ungültig ist.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [CMFCTabCtrl::SetActiveTab](../../mfc/reference/cmfctabctrl-class.md#setactivetab).

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCTabCtrl](../../mfc/reference/ctabview-class.md)<br/>
[CView-Klasse](../../mfc/reference/cview-class.md)
