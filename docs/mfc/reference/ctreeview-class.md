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
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883992"
---
# <a name="ctreeview-class"></a>CTreeView-Klasse

Vereinfacht die Verwendung des Struktur Steuer Elements und von [CTreeCtrl](../../mfc/reference/ctreectrl-class.md), der Klasse, die die Struktur Steuerungs Funktionalität kapselt, mit der MFC-Dokument-/Ansichtsarchitektur.

## <a name="syntax"></a>Syntax

```
class CTreeView : public CCtrlView
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTreeView:: CTreeView](#ctreeview)|Erstellt ein `CTreeView`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTreeView:: GetTreeCtrl](#gettreectrl)|Gibt das Struktur Steuerelement zurück, das der Ansicht zugeordnet ist.|

## <a name="remarks"></a>Bemerkungen

Weitere Informationen zu dieser Architektur finden Sie in der Übersicht über die [CView](../../mfc/reference/cview-class.md) -Klasse und in den hier erwähnten Querverweise.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[Cctrlview](../../mfc/reference/cctrlview-class.md)

`CTreeView`

## <a name="requirements"></a>Requirements (Anforderungen)

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

## <a name="see-also"></a>Weitere Informationen

[CCtrlView-Klasse](../../mfc/reference/cctrlview-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CView-Klasse](../../mfc/reference/cview-class.md)<br/>
[CCtrlView-Klasse](../../mfc/reference/cctrlview-class.md)<br/>
[CTreeCtrl Class](../../mfc/reference/ctreectrl-class.md)
