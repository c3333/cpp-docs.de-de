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
ms.openlocfilehash: 8e4053bf16672d693adc104c9e88bb46a67ba7dd
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845912"
---
# <a name="cmditabinfo-class"></a>CMDITabInfo-Klasse

Die- `CMDITabInfo` Klasse wird verwendet, um Parameter an die [CMDIFrameWndEx:: EnableMDITabbedGroups](../../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups) -Methode zu übergeben. Legen Sie Member dieser Klasse fest, um das Verhalten der MDI-Gruppen im Registerkartenformat zu steuern.

## <a name="syntax"></a>Syntax

```
class CMDITabInfo
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|`CMDITabInfo::CMDITabInfo`|Standardkonstruktor|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[CMDITabInfo:: Serialize](#serialize)|Liest oder schreibt dieses Objekt aus einem oder in ein Archiv.|

### <a name="data-members"></a>Datenelemente

|Name|Beschreibung|
|----------|-----------------|
|[CMDITabInfo:: m_bActiveTabCloseButton;](#m_bactivetabclosebutton_)|Gibt an, ob die Schaltfläche **Schließen** in der Bezeichnung der aktiven Registerkarte angezeigt wird.|
|[CMDITabInfo:: m_bAutoColor](#m_bautocolor)|Gibt an, ob die MDI-Registerkarten farblich angezeigt werden.|
|[CMDITabInfo:: m_bDocumentMenu](#m_bdocumentmenu)|Gibt an, ob die Registerkarten Gruppe ein Popup Menü anzeigt, das eine Liste geöffneter Dokumente anzeigt oder Bild Lauf Schaltflächen anzeigt.|
|[CMDITabInfo:: m_bEnableTabSwap](#m_benabletabswap)|Gibt an, ob der Benutzer die Positionen von Registerkarten durchziehen austauschen kann.|
|[CMDITabInfo:: m_bFlatFrame](#m_bflatframe)|Gibt an, ob Registerkarten einen flachen Rahmen aufweisen.|
|[CMDITabInfo:: m_bTabCloseButton](#m_btabclosebutton)|Gibt an, ob jede Registerkarten Bezeichnung eine Schaltfläche zum **Schließen** anzeigt.|
|[CMDITabInfo:: m_bTabCustomTooltips](#m_btabcustomtooltips)|Gibt an, ob benutzerdefinierte Quick Infos aktiviert sind.|
|[CMDITabInfo:: m_bTabIcons](#m_btabicons)|Gibt an, ob Symbole auf MDI-Registerkarten angezeigt werden sollen.|
|[CMDITabInfo:: m_nTabBorderSize](#m_ntabbordersize)|Gibt die Rahmengröße jedes Registerkarten Fensters an.|
|[CMDITabInfo:: m_style](#m_style)|Gibt den Stil der Registerkarten Bezeichnungen an.|
|[CMDITabInfo:: m_tabLocation](#m_tablocation)|Gibt an, ob sich die Bezeichnungen der Registerkarten oben oder unten auf der Seite befinden.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse gibt die Parameter der MDI-Registerkarten Gruppen an, die vom Framework erstellt werden.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie die Werte der verschiedenen Element Variablen in der-Klasse festgelegt werden `CMDITabInfo` .

[!code-cpp[NVC_MFC_MDITab#1](../../mfc/reference/codesnippet/cpp/cmditabinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CMDITabInfo](../../mfc/reference/cmditabinfo-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxmdiclientareawnd. h

## <a name="cmditabinfom_bactivetabclosebutton"></a><a name="m_bactivetabclosebutton_"></a> CMDITabInfo:: m_bActiveTabCloseButton;

Gibt an, ob die Schaltfläche **Schließen** in der Bezeichnung der aktiven Registerkarte angezeigt wird.

```
BOOL m_bActiveTabCloseButton;
```

### <a name="remarks"></a>Bemerkungen

Wenn der Wert true ist, wird in der Bezeichnung der aktiven Registerkarte die Schaltfläche **Schließen** angezeigt. Die Schaltfläche **Schließen** wird in der rechten oberen Ecke des Registerkarten Bereichs entfernt. Andernfalls wird in der Bezeichnung der Registerkarte "aktiv" keine Schaltfläche " **Schließen** " angezeigt. Die Schaltfläche **Schließen** wird in der rechten oberen Ecke des Registerkarten Bereichs angezeigt.

## <a name="cmditabinfom_bautocolor"></a><a name="m_bautocolor"></a> CMDITabInfo:: m_bAutoColor

Gibt an, ob jede MDI-Registerkarte über eine eigene Farbe verfügt.

```
BOOL m_bAutoColor;
```

### <a name="remarks"></a>Bemerkungen

TRUE gibt an, dass jede Registerkarte eine eigene Farbe hat. Der Satz von Farben wird von der MFC-Bibliothek verwaltet. Andernfalls werden die Registerkarten in weiß angezeigt. Der Standardwert ist FALSE.

## <a name="cmditabinfom_bdocumentmenu"></a><a name="m_bdocumentmenu"></a> CMDITabInfo:: m_bDocumentMenu

Gibt an, ob jede Registerkarte ein Popup Menü anzeigt, das eine Liste der geöffneten Dokumente am rechten Rand des Registerkarten Bereichs anzeigt.

```
BOOL m_bDocumentMenu;
```

### <a name="remarks"></a>Bemerkungen

Bei "true" wird für jedes Registerkarten Fenster ein Popup Menü angezeigt, in dem eine Liste der geöffneten Dokumente am rechten Rand des Registerkarten Bereichs angezeigt wird. Andernfalls zeigt das Registerkarten Fenster am rechten Rand des Registerkarten Bereichs Bild Lauf Schaltflächen an. Der Standardwert ist FALSE.

## <a name="cmditabinfom_benabletabswap"></a><a name="m_benabletabswap"></a> CMDITabInfo:: m_bEnableTabSwap

Gibt an, ob der Benutzer die Positionen von Registerkarten durchziehen austauschen kann.

```
BOOL m_bEnableTabSwap;
```

### <a name="remarks"></a>Bemerkungen

TRUE gibt an, dass der Benutzer die Positionen der Tabstopps durchziehen der Registerkarten ändern kann. Andernfalls kann der Benutzer die Positionen der Registerkarten nicht ändern. Der Standardwert ist TRUE.

## <a name="cmditabinfom_bflatframe"></a><a name="m_bflatframe"></a> CMDITabInfo:: m_bFlatFrame

Gibt an, ob jedes Registerkarten Fenster über einen flachen Rahmen verfügt.

```
BOOL m_bFlatFrame;
```

## <a name="cmditabinfom_btabclosebutton"></a><a name="m_btabclosebutton"></a> CMDITabInfo:: m_bTabCloseButton

Gibt an, ob jedes Registerkarten Fenster eine Schaltfläche zum **Schließen** anzeigt.

```
BOOL m_bTabCloseButton;
```

### <a name="remarks"></a>Bemerkungen

Wenn true, wird in jedem Registerkarten Fenster am rechten Rand der Registerkarte die Schaltfläche **Schließen** angezeigt. andernfalls wird die Schaltfläche **Schließen** nicht angezeigt. Der Standardwert ist TRUE.

## <a name="cmditabinfom_btabcustomtooltips"></a><a name="m_btabcustomtooltips"></a> CMDITabInfo:: m_bTabCustomTooltips

Gibt an, ob die Registerkarten Quick Infos anzeigen.

```
BOOL m_bTabCustomTooltips;
```

### <a name="remarks"></a>Bemerkungen

TRUE gibt an, dass die Anwendung eine AFX_WM_ON_GET_TAB_TOOLTIP Meldung an den Hauptframe sendet. Sie können diese Nachricht mit dem ON_REGISTERED_MESSAGE-Makro verarbeiten.

## <a name="cmditabinfom_btabicons"></a><a name="m_btabicons"></a> CMDITabInfo:: m_bTabIcons

Gibt an, ob Symbole auf MDI-Registerkarten angezeigt werden sollen.

```
BOOL m_bTabIcons;
```

### <a name="remarks"></a>Bemerkungen

TRUE gibt an, dass Symbole auf jeder MDI-Registerkarte angezeigt werden. andernfalls werden Symbole nicht auf Registerkarten angezeigt. Der Standardwert ist FALSE.

## <a name="cmditabinfom_ntabbordersize"></a><a name="m_ntabbordersize"></a> CMDITabInfo:: m_nTabBorderSize

Gibt die Rahmengröße jedes Registerkarten Fensters in Pixel an.

```
int m_nTabBorderSize;
```

### <a name="remarks"></a>Bemerkungen

[CMFCVisualManager:: getmditabsborderssize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize) gibt den Standardwert zurück.

## <a name="cmditabinfom_style"></a><a name="m_style"></a> CMDITabInfo:: m_style

Gibt den Stil der Registerkarten Bezeichnungen an.

```
CMFCTabCtrl::Style m_style
```

### <a name="remarks"></a>Bemerkungen

Geben Sie einen der folgenden Stile für die Registerkarten Bezeichnungen an:

|Makro|Beschreibung|
|-|-|
|STYLE_3D|3D-Stil.  |
|STYLE_3D_ONENOTE|Microsoft OneNote-Stil.  |
|STYLE_3D_VS2005|Microsoft Visual Studio 2005-Stil.  |
|STYLE_3D_SCROLLED|3D-Stil mit Rechteck Registerkarten Bezeichnungen.  |
|STYLE_FLAT_SHARED_HORZ_SCROLL|Flacher Stil mit der freigegebenen horizontalen Scrollleiste.  |
|STYLE_3D_ROUNDED_SCROLL|3D-Stil mit runden Registerkarten Bezeichnungen.  |

## <a name="cmditabinfom_tablocation"></a><a name="m_tablocation"></a> CMDITabInfo:: m_tabLocation

Gibt an, ob sich die Bezeichnungen der Registerkarten oben oder unten auf der Seite befinden.

```
CMFCTabCtrl::Location m_tabLocation;
```

### <a name="remarks"></a>Bemerkungen

Wenden Sie auf die Registerkarten eines der folgenden Speicherort Flags an:

- LOCATION_BOTTOM: die Registerkarten Bezeichnungen befinden sich am unteren Rand der Seite.

- LOCATION_TOP: die Registerkarten Bezeichnungen befinden sich oben auf der Seite.

## <a name="cmditabinfoserialize"></a><a name="serialize"></a> CMDITabInfo:: Serialize

Liest oder schreibt dieses Objekt aus einem Archiv oder in ein Archiv.

```cpp
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parameter

*Tempel*<br/>
in Ein [CArchive-Klassen](../../mfc/reference/carchive-class.md) Objekt, das serialisiert werden soll.

## <a name="see-also"></a>Weitere Informationen

[CMDIFrameWndEx-Klasse](../../mfc/reference/cmdiframewndex-class.md)<br/>
[MDI-Gruppen im Registerkarten Format](../../mfc/mdi-tabbed-groups.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
