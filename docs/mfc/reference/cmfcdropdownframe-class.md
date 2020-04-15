---
title: CMFCDropDownFrame-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::Create
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentMenuBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentPopupMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::RecalcLayout
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::SetAutoDestroy
helpviewer_keywords:
- CMFCDropDownFrame [MFC], Create
- CMFCDropDownFrame [MFC], GetParentMenuBar
- CMFCDropDownFrame [MFC], GetParentPopupMenu
- CMFCDropDownFrame [MFC], RecalcLayout
- CMFCDropDownFrame [MFC], SetAutoDestroy
ms.assetid: 09ff81a9-de00-43ec-9df9-b626f7728c4b
ms.openlocfilehash: a5e95efe1880f1177490d55988ca1fe42c606b15
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367543"
---
# <a name="cmfcdropdownframe-class"></a>CMFCDropDownFrame-Klasse

Bietet Dropdown-Framefensterfunktionen für Dropdown-Symbolleisten und Dropdown-Symbolleistenschaltflächen.

## <a name="syntax"></a>Syntax

```
class CMFCDropDownFrame : public CMiniFrameWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|||
|-|-|
|Name|BESCHREIBUNG|
|`CMFCDropDownFrame::CMFCDropDownFrame`|Der Standardkonstruktor.|
|`CMFCDropDownFrame::~CMFCDropDownFrame`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|||
|-|-|
|Name|BESCHREIBUNG|
|[CMFCDropDownFrame::Erstellen](#create)|Erstellt ein `CMFCDropDownFrame` -Objekt.|
|`CMFCDropDownFrame::CreateObject`|Wird vom Framework verwendet, um eine dynamische Instanz dieses Klassentyps zu erstellen.|
|[CMFCDropDownFrame::GetParentMenuBar](#getparentmenubar)|Ruft die übergeordnete Menüleiste des Dropdown-Frames ab.|
|[CMFCDropDownFrame::GetParentPopupMenu](#getparentpopupmenu)|Ruft das übergeordnete Popupmenü des Dropdown-Frames ab.|
|`CMFCDropDownFrame::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|
|[CMFCDropDownFrame::RecalcLayout](#recalclayout)|Positioniert den Dropdown-Frame neu.|
|[CMFCDropDownFrame::SetAutoDestroy](#setautodestroy)|Legt fest, ob das untergeordnete Dropdown-Symbolleistenfenster automatisch zerstört wird.|

### <a name="remarks"></a>Bemerkungen

Diese Klasse ist nicht für die direkte Verwendung im Code vorgesehen.

Das Framework verwendet diese Klasse, `CMFCDropDownToolbar` um `CMFCDropDownToolbarButton` Frameverhalten für die und Klassen bereitzustellen. Weitere Informationen zu diesen Klassen finden Sie unter [CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md) und [CMFCDropDownToolbarButton Class](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie `CMFCDropDownFrame` Ein `CFrameWnd` Zeiger auf ein Objekt aus einer Klasse abgerufen wird und wie das untergeordnete Dropdown-Symbolleistenfenster automatisch zerstört wird.

[!code-cpp[NVC_MFC_RibbonApp#36](../../mfc/reference/codesnippet/cpp/cmfcdropdownframe-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCDropDownFrame](../../mfc/reference/cmfcdropdownframe-class.md)

## <a name="requirements"></a>Anforderungen

**Header:** afxdropdowntoolbar.h

## <a name="cmfcdropdownframecreate"></a><a name="create"></a>CMFCDropDownFrame::Erstellen

Erstellt ein `CMFCDropDownFrame` -Objekt.

```
virtual BOOL Create(
    CWnd* pWndParent,
    int x,
    int y,
    CMFCDropDownToolBar* pWndOriginToolbar);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|Beschreibung|
|*pWndParent*|[in] Das übergeordnete Fenster des Dropdown-Frames.|
|*X*|[in] Die horizontale Bildschirmkoordinate für die Position des Down-Down-Frames.|
|*y*|[in] Die vertikale Bildschirmkoordinate für die Position des Down-Down-Frames.|
|*pWndOriginToolbar*|[in] Die Symbolleiste mit den Dropdown-Schaltflächen, die diese Methode zum Auffüllen des neuen Dropdown-Frameobjekts verwendet.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Dropdown-Frame erfolgreich erstellt wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft die [CMiniFrameWnd::CreateEx-Basismethode](../../mfc/reference/cminiframewnd-class.md#createex) auf, um das Dropdown-Rahmenfenster mit dem WS_POPUP-Stil zu erstellen. Das Dropdown-Rahmenfenster wird an den angegebenen Bildschirmkoordinaten angezeigt. Diese Methode schlägt fehl, wenn die [CMiniFrameWnd::CreateEx-Methode](../../mfc/reference/cminiframewnd-class.md#createex) FALSE zurückgibt.

Die `CMFCDropDownFrame` Klasse erstellt eine `CMFCDropDownToolBar` Kopie des bereitgestellten Parameters. Diese Methode kopiert die Schaltflächenbilder `pWndOriginToolbar` und `m_pWndOriginToolbar` Schaltflächenzustände vom Parameter in das Datenelement.

## <a name="cmfcdropdownframegetparentmenubar"></a><a name="getparentmenubar"></a>CMFCDropDownFrame::GetParentMenuBar

Ruft die übergeordnete Menüleiste des Dropdown-Frames ab.

```
CMFCMenuBar* GetParentMenuBar() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die übergeordnete Menüleiste des Dropdown-Frames oder NULL, wenn der Rahmen kein übergeordnetes Element hat.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft die übergeordnete Menüleiste von der übergeordneten Schaltfläche ab. Diese Methode gibt NULL zurück, wenn der Dropdownrahmen keine übergeordnete Schaltfläche oder die übergeordnete Schaltfläche keine übergeordnete Menüleiste hat.

## <a name="cmfcdropdownframegetparentpopupmenu"></a><a name="getparentpopupmenu"></a>CMFCDropDownFrame::GetParentPopupMenu

Ruft das übergeordnete Popupmenü des Dropdown-Frames ab.

```
CMFCDropDownFrame* GetParentPopupMenu() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das übergeordnete Dropdownmenü des Dropdown-Frames oder NULL, wenn der Rahmen kein übergeordnetes Element hat.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft das übergeordnete Menü von der übergeordneten Schaltfläche ab. Diese Methode gibt NULL zurück, wenn der Dropdown-Frame keine übergeordnete Schaltfläche oder die übergeordnete Schaltfläche kein übergeordnetes Menü hat.

## <a name="cmfcdropdownframerecalclayout"></a><a name="recalclayout"></a>CMFCDropDownFrame::RecalcLayout

Positioniert den Dropdown-Frame neu.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|Beschreibung|
|*bNotify*|[in] Nicht verwendet.|

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Methode auf, wenn der Dropdown-Frame erstellt oder die Größe des übergeordneten Fensters geändert wird. Diese Methode berechnet die Position und Größe des Dropdown-Rahmens mithilfe der Position und Größe des übergeordneten Fensters.

## <a name="cmfcdropdownframesetautodestroy"></a><a name="setautodestroy"></a>CMFCDropDownFrame::SetAutoDestroy

Legt fest, ob das untergeordnete Dropdown-Symbolleistenfenster automatisch zerstört wird.

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parameter

*bAutoDestroy*<br/>
[in] TRUE, um das zugehörige Dropdown-Symbolleistenfenster automatisch zu zerstören; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Wenn *bAutoDestroy* TRUE ist, zerstört der `CMFCDropDownFrame` Destruktor das zugehörige Dropdown-Symbolleistenfenster. Der Standardwert ist TRUE.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar-Klasse](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCDropDownToolbarButton-Klasse](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)
