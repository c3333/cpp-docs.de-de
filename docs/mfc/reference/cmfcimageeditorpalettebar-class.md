---
title: CMFCImageEditorPaletteBar-Klasse
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
ms.openlocfilehash: 33d4bc0c72718d028031ac11bc67da6aec5e4907
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374426"
---
# <a name="cmfcimageeditorpalettebar-class"></a>CMFCImageEditorPaletteBar-Klasse

Stellt Palettenleistenfunktionen für ein Bildeditor-Dialogfeld bereit.

## <a name="syntax"></a>Syntax

```
class CMFCImageEditorPaletteBar : public CMFCToolBar
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|||
|-|-|
|Name|BESCHREIBUNG|
|[CMFCImageEditorPaletteBar::GetRowHeight](#getrowheight)|Gibt die Höhe der Symbolleistenschaltflächen zurück. (Überschreibt [CMFCToolBar::GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight).)|
|[CMFCImageEditorPaletteBar::IsButtonExtraSizeverfügbar](#isbuttonextrasizeavailable)|Bestimmt, ob die Symbolleiste Schaltflächen mit erweiterten Rahmen anzeigen kann. (Überschreibt [CMFCToolBar::IsButtonExtraSizeVerfügbar](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).)|

### <a name="remarks"></a>Bemerkungen

Diese Klasse ist nicht für die direkte Verwendung im Code vorgesehen.

Das Framework verwendet diese Klasse, um eine Palettenleiste in einem Bildeditor-Dialogfeld anzuzeigen. Weitere Informationen zum Dialogfeld Bildeditor finden Sie unter [CMFCImageEditorDialog Class](../../mfc/reference/cmfcimageeditordialog-class.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBa](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCImageEditorPaletteBar](../../mfc/reference/cmfcimageeditorpalettebar-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afximageeditordialog.h

## <a name="cmfcimageeditorpalettebargetrowheight"></a><a name="getrowheight"></a>CMFCImageEditorPaletteBar::GetRowHeight

Gibt die Höhe der Symbolleistenschaltflächen zurück.

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>Rückgabewert

Die Höhe jeder Schaltfläche auf der Symbolleiste.

## <a name="cmfcimageeditorpalettebarisbuttonextrasizeavailable"></a><a name="isbuttonextrasizeavailable"></a>CMFCImageEditorPaletteBar::IsButtonExtraSizeverfügbar

Bestimmt, ob die Symbolleiste Schaltflächen mit erweiterten Rahmen anzeigen kann.

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>Rückgabewert

Diese Methode gibt FALSE zurück.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImageEditorDialog-Klasse](../../mfc/reference/cmfcimageeditordialog-class.md)
