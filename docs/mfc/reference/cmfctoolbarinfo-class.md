---
title: CMFCToolBarInfo-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo::m_uiColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuResID
helpviewer_keywords:
- CMFCToolBarInfo [MFC], m_uiColdResID
- CMFCToolBarInfo [MFC], m_uiDisabledResID
- CMFCToolBarInfo [MFC], m_uiHotResID
- CMFCToolBarInfo [MFC], m_uiLargeColdResID
- CMFCToolBarInfo [MFC], m_uiLargeDisabledResID
- CMFCToolBarInfo [MFC], m_uiLargeHotResID
- CMFCToolBarInfo [MFC], m_uiMenuDisabledResID
- CMFCToolBarInfo [MFC], m_uiMenuResID
ms.assetid: 6dc84482-eaaa-491f-aa5d-dd7a57886b46
ms.openlocfilehash: 593d1665751f7322fc2a9cee307620df88d46876
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376192"
---
# <a name="cmfctoolbarinfo-class"></a>CMFCToolBarInfo-Klasse

Enthält die Ressourcen-IDs von Symbolleistenbildern in unterschiedlichen Zuständen. `CMFCToolBarInfo`ist eine Hilfsklasse, die als Parameter der [CMFCToolBar::LoadToolBarEx-Methode](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) verwendet wird.

## <a name="syntax"></a>Syntax

```
class CMFCToolBarInfo
```

## <a name="members"></a>Member

### <a name="data-members"></a>Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCToolBarInfo::m_uiColdResID](#m_uicoldresid)|Ressourcen-ID der Symbolleisten-Bitmap, die regelmäßige (kalte) Symbolleistenbilder enthält.|
|[CMFCToolBarInfo::m_uiDisabledResID](#m_uidisabledresid)|Ressourcen-ID der Symbolleisten-Bitmap, die deaktivierte Symbolleistenbilder enthält.|
|[CMFCToolBarInfo::m_uiHotResID](#m_uihotresid)|Ressourcen-ID der Symbolleisten-Bitmap, die ausgewählte (heiße) Symbolleistenbilder enthält.|
|[CMFCToolBarInfo::m_uiLargeColdResID](#m_uilargecoldresid)|Ressourcen-ID der Symbolleisten-Bitmap, die große, reguläre Symbolleistenbilder enthält.|
|[CMFCToolBarInfo::m_uiLargeDisabledResID](#m_uilargedisabledresid)|Ressourcen-ID der Symbolleisten-Bitmap, die große, deaktivierte Symbolleistenbilder enthält.|
|[CMFCToolBarInfo::m_uiLargeHotResID](#m_uilargehotresid)|Ressourcen-ID der Symbolleisten-Bitmap, die große, ausgewählte Symbolleistenbilder enthält.|
|[CMFCToolBarInfo::m_uiMenuDisabledResID](#m_uimenudisabledresid)|Ressourcen-ID der Symbolleisten-Bitmap, die deaktivierte Menübilder enthält.|
|[CMFCToolBarInfo::m_uiMenuResID](#m_uimenuresid)|Ressourcen-ID der Symbolleisten-Bitmap, die Menübilder enthält.|

## <a name="remarks"></a>Bemerkungen

Eine vollständige Symbolleisten-Bitmap besteht aus kleinen Symbolleistenbildern (Schaltflächen) mit fester Größe. Jede Ressourcen-ID, die `CMFCToolBarInfo` in einem Objekt gespeichert ist, ist eine Bitmap, die einen vollständigen Satz von Symbolleistenbildern in einem einzigen Zustand enthält (z. B. ausgewählte, deaktivierte, große oder Menübilder).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxtoolbar.h

## <a name="cmfctoolbarinfom_uicoldresid"></a><a name="m_uicoldresid"></a>CMFCToolBarInfo::m_uiColdResID

Gibt eine Ressourcen-ID für alle regulären Schaltflächenbilder einer Symbolleiste an.

```
UINT m_uiColdResID;
```

## <a name="cmfctoolbarinfom_uidisabledresid"></a><a name="m_uidisabledresid"></a>CMFCToolBarInfo::m_uiDisabledResID

Gibt eine Ressourcen-ID für die schaltflächenfreien Bilder einer Symbolleiste an.

```
UINT m_uiDisabledResID;
```

## <a name="cmfctoolbarinfom_uihotresid"></a><a name="m_uihotresid"></a>CMFCToolBarInfo::m_uiHotResID

Gibt eine Ressourcen-ID für alle hervorgehobenen Schaltflächenbilder einer Symbolleiste an.

```
UINT m_uiHotResID
```

## <a name="cmfctoolbarinfom_uilargecoldresid"></a><a name="m_uilargecoldresid"></a>CMFCToolBarInfo::m_uiLargeColdResID

Gibt eine Ressourcen-ID für alle großen regulären Schaltflächenbilder einer Symbolleiste an.

```
UINT m_uiLargeColdResID
```

## <a name="cmfctoolbarinfom_uilargedisabledresid"></a><a name="m_uilargedisabledresid"></a>CMFCToolBarInfo::m_uiLargeDisabledResID

Gibt eine Ressourcen-ID für alle großen deaktivierten Schaltflächenbilder einer Symbolleiste an.

```
UINT m_uiLargeDisabledResID;
```

## <a name="cmfctoolbarinfom_uilargehotresid"></a><a name="m_uilargehotresid"></a>CMFCToolBarInfo::m_uiLargeHotResID

Gibt eine Ressourcen-ID für alle großen hervorgehobenen Bilder einer Symbolleiste an.

```
UINT m_uiLargeHotResID;
```

## <a name="cmfctoolbarinfom_uimenudisabledresid"></a><a name="m_uimenudisabledresid"></a>CMFCToolBarInfo::m_uiMenuDisabledResID

Gibt eine Ressourcen-ID für die befehlsfreien Bilder einer Symbolleiste an.

```
UINT m_uiMenuDisabledResID;
```

## <a name="cmfctoolbarinfom_uimenuresid"></a><a name="m_uimenuresid"></a>CMFCToolBarInfo::m_uiMenuResID

Gibt eine Ressourcen-ID für alle regulären Menüelementbilder einer Symbolleiste an.

```
UINT m_uiMenuResID;
```

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar-Klasse](../../mfc/reference/cmfctoolbar-class.md)
