---
title: CListView-Klasse
ms.date: 11/04/2016
f1_keywords:
- CListView
- AFXCVIEW/CListView
- AFXCVIEW/CListView::CListView
- AFXCVIEW/CListView::GetListCtrl
- AFXCVIEW/CListView::RemoveImageList
helpviewer_keywords:
- CListView [MFC], CListView
- CListView [MFC], GetListCtrl
- CListView [MFC], RemoveImageList
ms.assetid: 7626bdb2-a1b8-4eab-b631-6743710a8432
ms.openlocfilehash: d7f3b7c43d98c4f2c42d0c27c8e224f33e4b3301
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749123"
---
# <a name="clistview-class"></a>CListView-Klasse

Vereinfacht die Verwendung des Listensteuerelements und von [CListCtrl](../../mfc/reference/clistctrl-class.md), der Klasse, die Listensteuerungsfunktionen mit der Dokumentansichtsarchitektur von MFC kapselt.

## <a name="syntax"></a>Syntax

```
class CListView : public CCtrlView
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CListView::CListView](#clistview)|Erstellt ein `CListView`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CListView::GetListCtrl](#getlistctrl)|Gibt das Listensteuerelement zurück, das der Ansicht zugeordnet ist.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CListView::RemoveImageList](#removeimagelist)|Entfernt die angegebene Bildliste aus der Listenansicht.|

## <a name="remarks"></a>Bemerkungen

Weitere Informationen zu dieser Architektur finden Sie in der Übersicht für die [CView-Klasse](../../mfc/reference/cview-class.md) und die dort zitierten Querverweise.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CListView`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxcview.h

## <a name="clistviewclistview"></a><a name="clistview"></a>CListView::CListView

Erstellt ein `CListView`-Objekt.

```
CListView();
```

## <a name="clistviewgetlistctrl"></a><a name="getlistctrl"></a>CListView::GetListCtrl

Rufen Sie diese Memberfunktion auf, um einen Verweis auf das Listensteuerelement abzurufen, das der Ansicht zugeordnet ist.

```
CListCtrl& GetListCtrl() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das Listensteuerelement, das der Ansicht zugeordnet ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCListView#7](../../atl/reference/codesnippet/cpp/clistview-class_1.cpp)]

## <a name="clistviewremoveimagelist"></a><a name="removeimagelist"></a>CListView::RemoveImageList

Entfernt die angegebene Bildliste aus der Listenansicht.

```cpp
void RemoveImageList(int nImageList);
```

### <a name="parameters"></a>Parameter

*nImageList*<br/>
Der nullbasierte Index des zu entfernenden Bildes.

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel ROWLIST](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView-Klasse](../../mfc/reference/cctrlview-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CCtrlView-Klasse](../../mfc/reference/cctrlview-class.md)
