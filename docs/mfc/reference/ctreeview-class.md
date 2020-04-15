---
title: CTreeView-Klasse
ms.date: 11/04/2016
f1_keywords:
- CTreeView
- AFXCVIEW/CTreeView
- AFXCVIEW/CTreeView::CTreeView
- AFXCVIEW/CTreeView::GetTreeCtrl
helpviewer_keywords:
- CTreeView [MFC], CTreeView
- CTreeView [MFC], GetTreeCtrl
ms.assetid: 5df583a6-d69f-42ca-9d8d-57e04558afff
ms.openlocfilehash: 2ef93152c83d3bbec2b89ada0596ee612b24701b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373292"
---
# <a name="ctreeview-class"></a>CTreeView-Klasse

Vereinfacht die Verwendung des Struktursteuerelements und von [CTreeCtrl](../../mfc/reference/ctreectrl-class.md), der Klasse, die die Struktursteuerungsfunktionalität mit der Dokumentansichtsarchitektur von MFC kapselt.

## <a name="syntax"></a>Syntax

```
class CTreeView : public CCtrlView
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTreeView::CTreeView](#ctreeview)|Erstellt ein `CTreeView`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTreeView::GetTreeCtrl](#gettreectrl)|Gibt das der Ansicht zugeordnete Struktursteuerelement zurück.|

## <a name="remarks"></a>Bemerkungen

Weitere Informationen zu dieser Architektur finden Sie in der Übersicht für die [CView-Klasse](../../mfc/reference/cview-class.md) und die dort zitierten Querverweise.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CTreeView`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxcview.h

## <a name="ctreeviewctreeview"></a><a name="ctreeview"></a>CTreeView::CTreeView

Erstellt ein `CTreeView`-Objekt.

```
CTreeView();
```

## <a name="ctreeviewgettreectrl"></a><a name="gettreectrl"></a>CTreeView::GetTreeCtrl

Gibt einen Verweis auf das Der Ansicht zugeordnete Struktursteuerelement zurück.

```
CTreeCtrl& GetTreeCtrl() const;
```

## <a name="see-also"></a>Siehe auch

[CCtrlView-Klasse](../../mfc/reference/cctrlview-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CView-Klasse](../../mfc/reference/cview-class.md)<br/>
[CCtrlView-Klasse](../../mfc/reference/cctrlview-class.md)<br/>
[CTreeCtrl-Klasse](../../mfc/reference/ctreectrl-class.md)
