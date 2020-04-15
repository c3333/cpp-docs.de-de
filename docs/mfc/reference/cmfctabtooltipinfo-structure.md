---
title: CMFCTabToolTipInfo-Struktur
ms.date: 11/04/2016
f1_keywords:
- CMFCTabToolTipInfo
helpviewer_keywords:
- CMFCTabToolTipInfo struct
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
ms.openlocfilehash: a507d1e69b3524074e50fde0e87fc5ebb6e5ca03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367341"
---
# <a name="cmfctabtooltipinfo-structure"></a>CMFCTabToolTipInfo-Struktur

Diese Struktur enthält Informationen zur Registerkarte MDI, über die der Benutzer mit der Maus auf den Mauszeiger schwebt.

## <a name="syntax"></a>Syntax

```
struct CMFCTabToolTipInfo
```

## <a name="members"></a>Member

### <a name="data-members"></a>Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCTabToolTipInfo::m_nTabIndex](#m_ntabindex)|Gibt den Index des Registerkartensteuerelements an.|
|[CMFCTabToolTipInfo::m_pTabWnd](#m_ptabwnd)|Ein Zeiger auf das Registerkartensteuerelement.|
|[CMFCTabToolTipInfo::m_strText](#m_strtext)|Der QuickInfo-Text.|

## <a name="remarks"></a>Bemerkungen

Ein Zeiger auf `CMFCTabToolTipInfo` eine Struktur wird als Parameter der AFX_WM_ON_GET_TAB_TOOLTIP Nachricht übergeben. Diese Meldung wird generiert, wenn MDI-Registerkarten aktiviert sind und der Benutzer den Mauszeiger über ein Registerkartensteuerelement schwebt.

## <a name="example"></a>Beispiel

Das folgende Beispiel `CMFCTabToolTipInfo` zeigt, wie im [MDITabsDemo-Beispiel verwendet wird: MFC Tabbed MDI-Anwendung](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CMFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)

## <a name="requirements"></a>Anforderungen

**Header:** afxbasetabctrl.h

## <a name="cmfctabtooltipinfom_ntabindex"></a><a name="m_ntabindex"></a>CMFCTabToolTipInfo::m_nTabIndex

Gibt den Index des Registerkartensteuerelements an.

```
int m_nTabIndex;
```

### <a name="remarks"></a>Bemerkungen

Index der Registerkarte, über die der Benutzer schwebt.

### <a name="example"></a>Beispiel

Das folgende Beispiel `m_nTabIndex` zeigt, wie im [MDITabsDemo-Beispiel verwendet wird: MFC Tabbed MDI-Anwendung](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="cmfctabtooltipinfom_ptabwnd"></a><a name="m_ptabwnd"></a>CMFCTabToolTipInfo::m_pTabWnd

Ein Zeiger auf das Registerkartensteuerelement.

```
CMFCBaseTabCtrl* m_pTabWnd;
```

### <a name="example"></a>Beispiel

Das folgende Beispiel `m_pTabWnd` zeigt, wie im [MDITabsDemo-Beispiel verwendet wird: MFC Tabbed MDI-Anwendung](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="cmfctabtooltipinfom_strtext"></a><a name="m_strtext"></a>CMFCTabToolTipInfo::m_strText

Der QuickInfo-Text.

```
CString m_strText;
```

### <a name="remarks"></a>Bemerkungen

Wenn die Zeichenfolge leer ist, wird die QuickInfo nicht angezeigt.

### <a name="example"></a>Beispiel

Das folgende Beispiel `m_strText` zeigt, wie im [MDITabsDemo-Beispiel verwendet wird: MFC Tabbed MDI-Anwendung](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
