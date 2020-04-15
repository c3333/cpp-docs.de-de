---
title: CMFCRibbonMiniToolBar-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsContextMenuMode
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::SetCommands
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::Show
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::ShowWithContextMenu
helpviewer_keywords:
- CMFCRibbonMiniToolBar [MFC], IsContextMenuMode
- CMFCRibbonMiniToolBar [MFC], IsRibbonMiniToolBar
- CMFCRibbonMiniToolBar [MFC], SetCommands
- CMFCRibbonMiniToolBar [MFC], Show
- CMFCRibbonMiniToolBar [MFC], ShowWithContextMenu
ms.assetid: 7017e963-aeaf-4fe9-b540-e15a7ed41e94
ms.openlocfilehash: 10b1d35c331df6563d09be0bea3c97c73e89acaa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375090"
---
# <a name="cmfcribbonminitoolbar-class"></a>CMFCRibbonMiniToolBar-Klasse

Implementiert eine kontextbezogene Popup-Symbolleiste.

## <a name="syntax"></a>Syntax

```
class CMFCRibbonMiniToolBar : public CMFCRibbonPanelMenu
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMFCRibbonMiniToolBar::CMFCRibbonMiniToolBar`|Der Standardkonstruktor.|
|`CMFCRibbonMiniToolBar::~CMFCRibbonMiniToolBar`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMFCRibbonMiniToolBar::CreateObject`|Wird vom Framework verwendet, um eine dynamische Instanz dieses Klassentyps zu erstellen.|
|`CMFCRibbonMiniToolBar::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|
|[CMFCRibbonMiniToolBar::IsContextMenuMode](#iscontextmenumode)||
|[CMFCRibbonMiniToolBar::IsRibbonMiniToolBar](#isribbonminitoolbar)|(Überschreibt `CMFCPopupMenu::IsRibbonMiniToolBar`.)|
|[CMFCRibbonMiniToolBar::SetCommands](#setcommands)|Legt die Liste der auf der Symbolleiste anzuzeigenden Befehle fest.|
|[CMFCRibbonMiniToolBar::Show](#show)|Zeigt die Minisymbolleiste an den angegebenen Bildschirmkoordinaten an.|
|[CMFCRibbonMiniToolBar::ShowWithContextMenu](#showwithcontextmenu)|Zeigt die Minisymbolleiste zusammen mit einem Kontextmenü an.|

## <a name="remarks"></a>Bemerkungen

Die Minisymbolleiste wird meist angezeigt, nachdem ein Benutzer ein Objekt in einem Dokument ausgewählt hat. Nachdem der Benutzer einen Textblock in einem Textverarbeitungsprogramm auswählt, zeigt die Anwendung z. B. eine Minisymbolleiste mit Textformatierungsbefehlen an.

Die Minisymbolleiste wird transparent, wenn der Mauszeiger sich außerhalb des gültigen Bereichs der Minisymbolleiste befindet.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

`CMFCRibbonPanelMenu`

[CMFCRibbonMiniToolBar](../../mfc/reference/cmfcribbonminitoolbar-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxRibbonMiniToolBar.h

## <a name="cmfcribbonminitoolbarsetcommands"></a><a name="setcommands"></a>CMFCRibbonMiniToolBar::SetBefehle

Legt die Liste der auf der Symbolleiste anzuzeigenden Befehle fest.

```
void SetCommands(
    CMFCRibbonBar* pRibbonBar,
    const CList<UINT,UINT>& lstCommands);
```

### <a name="parameters"></a>Parameter

*pRibbonBar*<br/>
[in] Die Multifunktionsleistenleiste, die in der Minisymbolleiste nach den anzuzeigenden Schaltflächen durchsucht werden soll.

*lstCommands*<br/>
[in] Die Liste der Befehle, die auf der Minisymbolleiste angezeigt werden sollen. Alle Menübandkategorien werden durchsucht, um die zugehörigen Schaltflächen zu finden.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um die Liste der Befehle festzulegen, die in der Minisymbolleiste angezeigt werden sollen.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird `SetCommands` veranschaulicht, `CMFCRibbonMiniToolBar` wie die Methode der Klasse verwendet wird. Dieser Codeausschnitt ist Teil des [MS Office 2007-Demobeispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#9](../../mfc/reference/codesnippet/cpp/cmfcribbonminitoolbar-class_1.cpp)]

## <a name="cmfcribbonminitoolbarshow"></a><a name="show"></a>CMFCRibbonMiniToolBar::Anzeigen

Zeigt die Minisymbolleiste an den angegebenen Bildschirmkoordinaten an.

```
BOOL Show(
    int x,
    int y);
```

### <a name="parameters"></a>Parameter

*X*<br/>
[in] Gibt die horizontale Position der Minisymbolleiste in Bildschirmkoordinaten an.

*y*<br/>
[in] Gibt die vertikale Position der Minisymbolleiste in Bildschirmkoordinaten an.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Mini-Symbolleiste erfolgreich angezeigt wurde; andernfalls FALSE.

## <a name="cmfcribbonminitoolbarshowwithcontextmenu"></a><a name="showwithcontextmenu"></a>CMFCRibbonMiniToolBar::ShowWithContextMenu

Zeigt die Minisymbolleiste zusammen mit einem Kontextmenü an.

```
BOOL ShowWithContextMenu(
    int x,
    int y,
    UINT uiMenuResID,
    CWnd* pWndOwner);
```

### <a name="parameters"></a>Parameter

*X*<br/>
[in] Gibt die horizontale Position des Kontextmenüs in Bildschirmkoordinaten an.

*y*<br/>
[in] Gibt die vertikale Position des Kontextmenüs in Bildschirmkoordinaten an.

*uiMenuResID*<br/>
[in] Gibt die Ressourcen-ID des anzuzeigenden Kontextmenüs an.

*pWndOwner*<br/>
[in] Identifiziert das Fenster, das Nachrichten aus dem Kontextmenü empfängt.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Kontextmenü erfolgreich angezeigt wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um eine Minisymbolleiste mit einem Kontextmenü anzuzeigen. Das Kontextmenü befindet sich 15 Pixel unterhalb der Mini-Symbolleiste.

## <a name="cmfcribbonminitoolbariscontextmenumode"></a><a name="iscontextmenumode"></a>CMFCRibbonMiniToolBar::IsContextMenuMode

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

```
BOOL IsContextMenuMode() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonminitoolbarisribbonminitoolbar"></a><a name="isribbonminitoolbar"></a>CMFCRibbonMiniToolBar::IsRibbonMiniToolBar

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

```
virtual BOOL IsRibbonMiniToolBar() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
