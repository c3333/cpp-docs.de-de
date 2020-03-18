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
ms.openlocfilehash: fec8379a3944d981672754274f50dd4e60f71b61
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426774"
---
# <a name="ctreeview-class"></a>CTreeView-Klasse

Vereinfacht die Verwendung des Struktur Steuer Elements und von [CTreeCtrl](../../mfc/reference/ctreectrl-class.md), der Klasse, die die Struktur Steuerungs Funktionalität kapselt, mit der MFC-Dokument-/Ansichtsarchitektur.

## <a name="syntax"></a>Syntax

```
class CTreeView : public CCtrlView
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CTreeView:: CTreeView](#ctreeview)|Erstellt ein `CTreeView`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CTreeView:: GetTreeCtrl](#gettreectrl)|Gibt das Struktur Steuerelement zurück, das der Ansicht zugeordnet ist.|

## <a name="remarks"></a>Hinweise

Weitere Informationen zu dieser Architektur finden Sie in der Übersicht über die [CView](../../mfc/reference/cview-class.md) -Klasse und in den hier erwähnten Querverweise.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[Cctrlview](../../mfc/reference/cctrlview-class.md)

`CTreeView`

## <a name="requirements"></a>Voraussetzungen

**Header:** afxcview. h

##  <a name="ctreeview"></a>CTreeView:: CTreeView

Erstellt ein `CTreeView`-Objekt.

```
CTreeView();
```

##  <a name="gettreectrl"></a>CTreeView:: GetTreeCtrl

Gibt einen Verweis auf das Struktur Steuerelement zurück, das der Ansicht zugeordnet ist.

```
CTreeCtrl& GetTreeCtrl() const;
```

## <a name="see-also"></a>Siehe auch

[CCtrlView-Klasse](../../mfc/reference/cctrlview-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CView-Klasse](../../mfc/reference/cview-class.md)<br/>
[CCtrlView-Klasse](../../mfc/reference/cctrlview-class.md)<br/>
[CTreeCtrl Class](../../mfc/reference/ctreectrl-class.md)
