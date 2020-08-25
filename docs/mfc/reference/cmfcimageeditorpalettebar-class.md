---
title: Cmficimageeditorpalettebar-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCImageEditorPaletteBar
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar::GetRowHeight
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable
helpviewer_keywords:
- CMFCImageEditorPaletteBar [MFC], GetRowHeight
- CMFCImageEditorPaletteBar [MFC], IsButtonExtraSizeAvailable
ms.assetid: 3fb7ba8e-f254-4d56-b913-9941b4ed8138
ms.openlocfilehash: 007fa94269a6a42bf076d2d75a18860896503aa1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831163"
---
# <a name="cmfcimageeditorpalettebar-class"></a>Cmficimageeditorpalettebar-Klasse

Stellt eine Palette leisten Funktionalität für ein Bild-Editor-Dialogfeld bereit.

## <a name="syntax"></a>Syntax

```
class CMFCImageEditorPaletteBar : public CMFCToolBar
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|-|-|
|[Cmficimageeditor palettebar:: getRowHeight](#getrowheight)|Gibt die Höhe von Symbolleisten-Schaltflächen zurück. (Überschreibt [cmfctoolbar:: getRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight).)|
|[Cmficimageeditor palettebar:: isbuttonextrasizeavailable](#isbuttonextrasizeavailable)|Bestimmt, ob die Symbolleiste Schaltflächen mit erweiterten Rahmen anzeigen kann. (Überschreibt [cmfctoolbar:: isbuttonextrasizeavailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).)|

### <a name="remarks"></a>Bemerkungen

Diese Klasse ist nicht für die direkte Verwendung im Code vorgesehen.

Das Framework verwendet diese Klasse, um einen palettenbalken in einem Bild-Editor-Dialogfeld anzuzeigen. Weitere Informationen zum Dialogfeld Bildbearbeitung finden Sie unter [cmfcimageeditordialog-Klasse](../../mfc/reference/cmfcimageeditordialog-class.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[Cmfcbasetoolba](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[Cmficimageeditor palettebar](../../mfc/reference/cmfcimageeditorpalettebar-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afximageeditor Dialog. h

## <a name="cmfcimageeditorpalettebargetrowheight"></a><a name="getrowheight"></a> Cmficimageeditor palettebar:: getRowHeight

Gibt die Höhe von Symbolleisten-Schaltflächen zurück.

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>Rückgabewert

Die Höhe der einzelnen Schaltflächen auf der Symbolleiste.

## <a name="cmfcimageeditorpalettebarisbuttonextrasizeavailable"></a><a name="isbuttonextrasizeavailable"></a> Cmficimageeditor palettebar:: isbuttonextrasizeavailable

Bestimmt, ob die Symbolleiste Schaltflächen mit erweiterten Rahmen anzeigen kann.

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>Rückgabewert

Diese Methode gibt false zurück.

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[Cmficimageeditordialog-Klasse](../../mfc/reference/cmfcimageeditordialog-class.md)
