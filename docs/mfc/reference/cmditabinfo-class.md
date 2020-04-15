---
title: CMDITabInfo-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo::Serialize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bAutoColor
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bDocumentMenu
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bEnableTabSwap
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bFlatFrame
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCloseButton
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCustomTooltips
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabIcons
- AFXMDICLIENTAREAWND/CMDITabInfo::m_nTabBorderSize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_style
- AFXMDICLIENTAREAWND/CMDITabInfo::m_tabLocation
helpviewer_keywords:
- CMDITabInfo [MFC], Serialize
- CMDITabInfo [MFC], m_bAutoColor
- CMDITabInfo [MFC], m_bDocumentMenu
- CMDITabInfo [MFC], m_bEnableTabSwap
- CMDITabInfo [MFC], m_bFlatFrame
- CMDITabInfo [MFC], m_bTabCloseButton
- CMDITabInfo [MFC], m_bTabCustomTooltips
- CMDITabInfo [MFC], m_bTabIcons
- CMDITabInfo [MFC], m_nTabBorderSize
- CMDITabInfo [MFC], m_style
- CMDITabInfo [MFC], m_tabLocation
ms.assetid: 988ae1b7-4f7f-4239-b88f-7e28b3291c5e
ms.openlocfilehash: 0d230d2a3401ab556adc1183f4c4210ec6ff3c29
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370033"
---
# <a name="cmditabinfo-class"></a>CMDITabInfo-Klasse

Die `CMDITabInfo` Klasse wird verwendet, um Parameter an die [CMDIFrameWndEx::EnableMDITabbedGroups-Methode](../../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups) zu übergeben. Legen Sie Member dieser Klasse fest, um das Verhalten der MDI-Gruppen im Registerkartenformat zu steuern.

## <a name="syntax"></a>Syntax

```
class CMDITabInfo
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMDITabInfo::CMDITabInfo`|Der Standardkonstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMDITabInfo::Serialisieren](#serialize)|Liest oder schreibt dieses Objekt aus einem oder in ein Archiv.|

### <a name="data-members"></a>Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMDITabInfo::m_bActiveTabCloseButton;](#m_bactivetabclosebutton_)|Gibt an, ob eine Schaltfläche **Schließen** auf der Beschriftung der aktiven Registerkarte angezeigt wird.|
|[CMDITabInfo::m_bAutoColor](#m_bautocolor)|Gibt an, ob die MDI-Registerkarten farblich befärbt werden sollen.|
|[CMDITabInfo::m_bDocumentMenu](#m_bdocumentmenu)|Gibt an, ob die Registerkartengruppe ein Popupmenü anzeigt, das eine Liste geöffneter Dokumente oder Bildlaufschaltflächen anzeigt.|
|[CMDITabInfo::m_bEnableTabSwap](#m_benabletabswap)|Gibt an, ob der Benutzer die Positionen von Registerkarten durch Ziehen austauschen kann.|
|[CMDITabInfo::m_bFlatFrame](#m_bflatframe)|Gibt an, ob Registerkarten einen flachen Rahmen haben.|
|[CMDITabInfo::m_bTabCloseButton](#m_btabclosebutton)|Gibt an, ob jede Registerkartenbeschriftung eine Schaltfläche **Schließen** anzeigt.|
|[CMDITabInfo::m_bTabCustomTooltips](#m_btabcustomtooltips)|Gibt an, ob benutzerdefinierte QuickInfos aktiviert sind.|
|[CMDITabInfo::m_bTabIcons](#m_btabicons)|Gibt an, ob Symbole auf MDI-Registerkarten angezeigt werden sollen.|
|[CMDITabInfo::m_nTabBorderSize](#m_ntabbordersize)|Gibt die Rahmengröße jedes Registerkartenfensters an.|
|[CMDITabInfo::m_style](#m_style)|Gibt den Stil der Registerkartenbeschriftungen an.|
|[CMDITabInfo::m_tabLocation](#m_tablocation)|Gibt an, ob sich die Registerkartenbeschriftungen oben oder unten auf der Seite befinden.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse gibt die Parameter der MDI-Registerkartengruppen an, die das Framework erstellt.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie die `CMDITabInfo` Werte der verschiedenen Membervariablen in der Klasse festgelegt werden.

[!code-cpp[NVC_MFC_MDITab#1](../../mfc/reference/codesnippet/cpp/cmditabinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CMDITabInfo](../../mfc/reference/cmditabinfo-class.md)

## <a name="requirements"></a>Anforderungen

**Kopf:** afxmdiclientareawnd.h

## <a name="cmditabinfom_bactivetabclosebutton"></a><a name="m_bactivetabclosebutton_"></a>CMDITabInfo::m_bActiveTabCloseButton;

Gibt an, ob eine Schaltfläche **Schließen** auf der Beschriftung der aktiven Registerkarte angezeigt wird.

```
BOOL m_bActiveTabCloseButton;
```

### <a name="remarks"></a>Bemerkungen

Wenn TRUE, wird auf der Beschriftung der aktiven Registerkarte eine Schaltfläche **Schließen** angezeigt. Die Schaltfläche **Schließen** wird aus der rechten oberen Ecke des Tab-Bereichs entfernt. Andernfalls wird auf der Beschriftung der aktiven Registerkarte keine Schaltfläche **Schließen** angezeigt. Die Schaltfläche **Schließen** wird in der rechten oberen Ecke des Tab-Bereichs angezeigt.

## <a name="cmditabinfom_bautocolor"></a><a name="m_bautocolor"></a>CMDITabInfo::m_bAutoColor

Gibt an, ob jede MDI-Registerkarte eine eigene Farbe hat.

```
BOOL m_bAutoColor;
```

### <a name="remarks"></a>Bemerkungen

Wenn TRUE, hat jede Registerkarte ihre eigene Farbe. Der Farbsatz wird von der MFC-Bibliothek verwaltet. Andernfalls werden die Registerkarten weiß angezeigt. Der Standardwert ist FALSE.

## <a name="cmditabinfom_bdocumentmenu"></a><a name="m_bdocumentmenu"></a>CMDITabInfo::m_bDocumentMenu

Gibt an, ob jede Registerkarte ein Popupmenü anzeigt, das eine Liste geöffneter Dokumente am rechten Rand des Registerkartenbereichs anzeigt.

```
BOOL m_bDocumentMenu;
```

### <a name="remarks"></a>Bemerkungen

Wenn TRUE, zeigt jedes Registerkartenfenster ein Popupmenü an, das eine Liste der geöffneten Dokumente am rechten Rand des Registerkartenbereichs anzeigt. Andernfalls werden im Registerkartenfenster Bildlaufschaltflächen am rechten Rand des Tab-Bereichs angezeigt. Der Standardwert ist FALSE.

## <a name="cmditabinfom_benabletabswap"></a><a name="m_benabletabswap"></a>CMDITabInfo::m_bEnableTabSwap

Gibt an, ob der Benutzer die Positionen von Registerkarten durch Ziehen austauschen kann.

```
BOOL m_bEnableTabSwap;
```

### <a name="remarks"></a>Bemerkungen

Wenn TRUE, kann der Benutzer die Registerkartenpositionen ändern, indem er die Registerkarten zieht. Andernfalls kann der Benutzer die Registerkartenpositionen nicht ändern. Der Standardwert ist TRUE.

## <a name="cmditabinfom_bflatframe"></a><a name="m_bflatframe"></a>CMDITabInfo::m_bFlatFrame

Gibt an, ob jedes Registerkartenfenster über einen flachen Rahmen verfügt.

```
BOOL m_bFlatFrame;
```

## <a name="cmditabinfom_btabclosebutton"></a><a name="m_btabclosebutton"></a>CMDITabInfo::m_bTabCloseButton

Gibt an, ob jedes Registerkartenfenster eine Schaltfläche **Schließen** anzeigt.

```
BOOL m_bTabCloseButton;
```

### <a name="remarks"></a>Bemerkungen

Wenn TRUE, zeigt jedes Tab-Fenster die **Schaltfläche Schließen** am rechten Rand der Registerkarte an. Andernfalls wird die Schaltfläche **Schließen** nicht angezeigt. Der Standardwert ist TRUE.

## <a name="cmditabinfom_btabcustomtooltips"></a><a name="m_btabcustomtooltips"></a>CMDITabInfo::m_bTabCustomTooltips

Gibt an, ob auf den Registerkarten QuickInfos angezeigt werden.

```
BOOL m_bTabCustomTooltips;
```

### <a name="remarks"></a>Bemerkungen

Wenn TRUE, sendet die Anwendung eine AFX_WM_ON_GET_TAB_TOOLTIP Nachricht an den Hauptframe. Sie können diese Nachricht mithilfe des ON_REGISTERED_MESSAGE-Makros verarbeiten.

## <a name="cmditabinfom_btabicons"></a><a name="m_btabicons"></a>CMDITabInfo::m_bTabIcons

Gibt an, ob Symbole auf MDI-Registerkarten angezeigt werden sollen.

```
BOOL m_bTabIcons;
```

### <a name="remarks"></a>Bemerkungen

Wenn TRUE, werden Symbole auf jeder MDI-Registerkarte angezeigt. Andernfalls werden Symbole nicht auf Registerkarten angezeigt. Der Standardwert ist FALSE.

## <a name="cmditabinfom_ntabbordersize"></a><a name="m_ntabbordersize"></a>CMDITabInfo::m_nTabBorderSize

Gibt die Rahmengröße jedes Registerkartenfensters in Pixel an.

```
int m_nTabBorderSize;
```

### <a name="remarks"></a>Bemerkungen

[CMFCVisualManager::GetMDITabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize) gibt den Standardwert zurück.

## <a name="cmditabinfom_style"></a><a name="m_style"></a>CMDITabInfo::m_style

Gibt den Stil der Registerkartenbeschriftungen an.

```
CMFCTabCtrl::Style m_style
```

### <a name="remarks"></a>Bemerkungen

Geben Sie einen der folgenden Formatvorlagen für die Registerkartenbeschriftungen an:

|||
|-|-|
|STYLE_3D|3D-Stil.  |
|STYLE_3D_ONENOTE|Microsoft OneNote-Stil.  |
|STYLE_3D_VS2005|Microsoft Visual Studio 2005-Stil.  |
|STYLE_3D_SCROLLED|3D-Stil mit Rechteck-Registerkartenbeschriftungen.  |
|STYLE_FLAT_SHARED_HORZ_SCROLL|Flacher Stil mit gemeinsamer horizontaler Bildlaufleiste.  |
|STYLE_3D_ROUNDED_SCROLL|3D-Stil mit runden Tab-Etiketten.  |

## <a name="cmditabinfom_tablocation"></a><a name="m_tablocation"></a>CMDITabInfo::m_tabLocation

Gibt an, ob sich die Registerkartenbeschriftungen oben oder unten auf der Seite befinden.

```
CMFCTabCtrl::Location m_tabLocation;
```

### <a name="remarks"></a>Bemerkungen

Auf die Registerkarten eines der folgenden Standortflags anwenden:

- LOCATION_BOTTOM: Die Registerkartenbeschriftungen befinden sich unten auf der Seite.

- LOCATION_TOP: Die Registerkartenbeschriftungen befinden sich oben auf der Seite

## <a name="cmditabinfoserialize"></a><a name="serialize"></a>CMDITabInfo::Serialisieren

Liest oder schreibt dieses Objekt aus einem Archiv oder in ein Archiv.

```
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parameter

*ar*<br/>
[in] Ein zu serialisierendes [CArchive-Klassenobjekt.](../../mfc/reference/carchive-class.md)

## <a name="see-also"></a>Siehe auch

[CMDIFrameWndEx-Klasse](../../mfc/reference/cmdiframewndex-class.md)<br/>
[MDI-Gruppen im Registerkartenformat](../../mfc/mdi-tabbed-groups.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
