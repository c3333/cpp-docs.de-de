---
title: CMFCDropDownToolbarButton-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CopyFrom
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::DropDownToolbar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::ExportToMenuButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::GetDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsDropDown
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsExtraSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCalculateSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnChangeParentWnd
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClick
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClickUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnContextHelp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCustomizeMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDraw
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDrawOnCustomizeList
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::Serialize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::SetDefaultCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::m_uiShowBarDelay
helpviewer_keywords:
- CMFCDropDownToolbarButton [MFC], CMFCDropDownToolbarButton
- CMFCDropDownToolbarButton [MFC], CopyFrom
- CMFCDropDownToolbarButton [MFC], DropDownToolbar
- CMFCDropDownToolbarButton [MFC], ExportToMenuButton
- CMFCDropDownToolbarButton [MFC], GetDropDownToolBar
- CMFCDropDownToolbarButton [MFC], IsDropDown
- CMFCDropDownToolbarButton [MFC], IsExtraSize
- CMFCDropDownToolbarButton [MFC], OnCalculateSize
- CMFCDropDownToolbarButton [MFC], OnChangeParentWnd
- CMFCDropDownToolbarButton [MFC], OnClick
- CMFCDropDownToolbarButton [MFC], OnClickUp
- CMFCDropDownToolbarButton [MFC], OnContextHelp
- CMFCDropDownToolbarButton [MFC], OnCustomizeMenu
- CMFCDropDownToolbarButton [MFC], OnDraw
- CMFCDropDownToolbarButton [MFC], OnDrawOnCustomizeList
- CMFCDropDownToolbarButton [MFC], Serialize
- CMFCDropDownToolbarButton [MFC], SetDefaultCommand
- CMFCDropDownToolbarButton [MFC], m_uiShowBarDelay
ms.assetid: bc9d69e6-bd3e-4c15-9368-e80a504a0ba7
ms.openlocfilehash: f09a2f3fe66abb86a8f220dbdf6744813ad9db0d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752408"
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>CMFCDropDownToolbarButton-Klasse

Ein Symbolleisten-Schaltflächentyp, der sich wie eine normale Schaltfläche verhält, wenn darauf geklickt wird. Es öffnet jedoch eine Dropdown-Symbolleiste [(CMFCDropDownToolBar-Klasse,](../../mfc/reference/cmfcdropdowntoolbar-class.md) wenn der Benutzer die Symbolleistentaste nach unten drückt und hält.

## <a name="syntax"></a>Syntax

```
class CMFCDropDownToolbarButton : public CMFCToolBarButton
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](#cmfcdropdowntoolbarbutton)|Erstellt ein `CMFCDropDownToolbarButton`-Objekt.|
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCDropDownToolbarButton::Kopierenvon](#copyfrom)|Kopiert die Eigenschaften einer anderen Symbolleistenschaltfläche in die aktuelle Schaltfläche. (Überschreibt [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCDropDownToolbarButton::CreateObject`|Wird vom Framework verwendet, um eine dynamische Instanz dieses Klassentyps zu erstellen.|
|[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)|Öffnet eine Dropdown-Symbolleiste.|
|[CMFCDropDownToolbarButton::ExportToMenuButton](#exporttomenubutton)|Kopiert Text aus der Symbolleistenschaltfläche in ein Menü. (Überschreibt [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton).)|
|[CMFCDropDownToolbarButton::GetDropDownToolBar](#getdropdowntoolbar)|Ruft die Dropdown-Symbolleiste ab, die der Schaltfläche zugeordnet ist.|
|`CMFCDropDownToolbarButton::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|
|[CMFCDropDownToolbarButton::IsDropDown](#isdropdown)|Bestimmt, ob die Dropdown-Symbolleiste derzeit geöffnet ist.|
|[CMFCDropDownToolbarButton::IsExtraSize](#isextrasize)|Legt fest, ob die Schaltfläche mit einem erweiterten Rahmen angezeigt werden kann. (Überschreibt [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).)|
|[CMFCDropDownToolbarButton::OnCalculateSize](#oncalculatesize)|Wird vom Framework aufgerufen, um die Größe der Schaltfläche für den angegebenen Gerätekontext und Andockstatus zu berechnen. (Überschreibt [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|`CMFCDropDownToolbarButton::OnCancelMode`|Wird vom Framework aufgerufen, um die [WM_CANCELMODE](/windows/win32/winmsg/wm-cancelmode) Nachricht zu verarbeiten. (Überschreibt `CMCToolBarButton::OnCancelMode`.)|
|[CMFCDropDownToolbarButton::OnChangeParentWnd](#onchangeparentwnd)|Wird vom Framework aufgerufen, wenn die Schaltfläche in eine neue Symbolleiste eingefügt wird. (Überschreibt [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCDropDownToolbarButton::OnClick](#onclick)|Wird vom Framework aufgerufen, wenn der Benutzer auf die Maustaste klickt. (Überschreibt [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCDropDownToolbarButton::OnClickUp](#onclickup)|Wird vom Framework aufgerufen, wenn der Benutzer die Maustaste loslässt. (Überschreibt [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup).)|
|[CMFCDropDownToolbarButton::OnContextHelp](#oncontexthelp)|Wird vom Framework aufgerufen, wenn die übergeordnete Symbolleiste eine WM_HELPHITTEST Nachricht verarbeitet. (Überschreibt [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp).)|
|[CMFCDropDownToolbarButton::OnCustomizeMenu](#oncustomizemenu)|Ändert das bereitgestellte Menü, wenn die Anwendung ein Kontextmenü auf der übergeordneten Symbolleiste anzeigt. (Überschreibt [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu).)|
|[CMFCDropDownToolbarButton::OnDraw](#ondraw)|Wird vom Framework aufgerufen, um die Schaltfläche mithilfe der angegebenen Stile und Optionen zu zeichnen. (Überschreibt [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Wird vom Framework aufgerufen, um **Commands** die Schaltfläche im Befehlsbereich des Dialogfelds **Anpassen** zu zeichnen. (Überschreibt [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCDropDownToolbarButton::Serialisieren](#serialize)|Liest dieses Objekt aus einem Archiv oder schreibt es in ein Archiv. (Überschreibt [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|[CMFCDropDownToolbarButton::SetDefaultCommand](#setdefaultcommand)|Legt den Standardbefehl fest, den das Framework verwendet, wenn ein Benutzer auf die Schaltfläche klickt.|

### <a name="data-members"></a>Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)|Gibt an, wie lange ein Benutzer die Maustaste gedrückt halten muss, bevor die Dropdown-Symbolleiste angezeigt wird.|

## <a name="remarks"></a>Bemerkungen

A `CMFCDropDownToolBarButton` unterscheidet sich von einem gewöhnlichen Knopf dadurch, dass er einen kleinen Pfeil in der unteren rechten Ecke der Schaltfläche hat. Nachdem der Benutzer eine Schaltfläche in der Dropdown-Symbolleiste ausgewählt hat, zeigt das Framework sein Symbol auf der Symbolleiste der obersten Ebene an (die Schaltfläche mit dem kleinen Pfeil in der unteren rechten Ecke).

Informationen zum Implementieren einer Dropdown-Symbolleiste finden Sie unter [CMFCDropDownToolBar-Klasse](../../mfc/reference/cmfcdropdowntoolbar-class.md).

Das `CMFCDropDownToolBarButton` Objekt kann in ein [CMFCToolBarMenuButton Class-Objekt](../../mfc/reference/cmfctoolbarmenubutton-class.md) exportiert und als Menüschaltfläche mit einem Popup-Menü angezeigt werden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdropdowntoolbar.h

## <a name="cmfcdropdowntoolbarbuttoncopyfrom"></a><a name="copyfrom"></a>CMFCDropDownToolbarButton::Kopierenvon

Kopiert die Eigenschaften einer anderen Symbolleistenschaltfläche in die aktuelle Schaltfläche.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parameter

*src*<br/>
[in] Ein Verweis auf die Quellschaltfläche, aus der kopiert werden soll.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um eine weitere Symbolleistenschaltfläche in diese Symbolleistenschaltfläche zu kopieren. *src* muss vom `CMFCDropDownToolbarButton`Typ sein.

## <a name="cmfcdropdowntoolbarbuttoncmfcdropdowntoolbarbutton"></a><a name="cmfcdropdowntoolbarbutton"></a>CMFCDropDownToolbarButton::CMFCDropDownToolbarButton

Erstellt ein `CMFCDropDownToolbarButton`-Objekt.

```
CMFCDropDownToolbarButton();

CMFCDropDownToolbarButton(
    LPCTSTR lpszName,
    CMFCDropDownToolBar* pToolBar);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
[in] Der Standardtext der Schaltfläche.

*pToolBar*<br/>
[in] Ein Zeiger auf `CMFCDropDownToolBar` das Objekt, das angezeigt wird, wenn der Benutzer die Taste drückt.

### <a name="remarks"></a>Bemerkungen

Die zweite Überladung des Konstruktors kopiert auf die Dropdown-Schaltfläche die erste Schaltfläche aus der Symbolleiste, die *pToolBar* angibt.

In der Regel verwendet eine Dropdown-Symbolleistenschaltfläche den Text aus der zuletzt verwendeten Schaltfläche in der Symbolleiste, die *pToolBar* angibt. Es verwendet den von *lpszName* angegebenen Text, wenn die Schaltfläche in eine Menüschaltfläche konvertiert wird oder auf der Registerkarte **Befehle** im Dialogfeld **Anpassen** angezeigt wird. Weitere Informationen zum Dialogfeld **Anpassen** finden Sie unter [CMFCToolBarsCustomizeDialog Class](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCDropDownToolbarButton` wie ein Objekt der Klasse erstellt wird. Dieser Codeausschnitt ist Teil des [Visual Studio Demo-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]

## <a name="cmfcdropdowntoolbarbuttondropdowntoolbar"></a><a name="dropdowntoolbar"></a>CMFCDropDownToolbarButton::DropDownToolbar

Öffnet eine Dropdown-Symbolleiste.

```
BOOL DropDownToolbar(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
[in] Das übergeordnete Fenster des Dropdown-Frames oder NULL, um das übergeordnete Fenster der Dropdown-Symbolleistenschaltfläche zu verwenden.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Methode erfolgreich ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die [CMFCDropDownToolbarButton::OnClick-Methode](#onclick) ruft diese Methode auf, um die Dropdown-Symbolleiste zu öffnen, wenn der Benutzer die Symbolleistenschaltfläche nach unten drückt und hält.

Diese Methode erstellt die Dropdown-Symbolleiste mithilfe der [CMFCDropDownFrame::Create-Methode.](../../mfc/reference/cmfcdropdownframe-class.md#create) Wenn die übergeordnete Symbolleiste vertikal angedockt ist, positioniert diese Methode die Dropdown-Symbolleiste je nach Anpassung auf der linken oder rechten Seite der übergeordneten Symbolleiste. Andernfalls positioniert diese Methode die Dropdown-Symbolleiste unter der übergeordneten Symbolleiste.

Diese Methode schlägt fehl, wenn *pWnd* NULL ist und die Dropdown-Symbolleistenschaltfläche kein übergeordnetes Fenster hat.

## <a name="cmfcdropdowntoolbarbuttonexporttomenubutton"></a><a name="exporttomenubutton"></a>CMFCDropDownToolbarButton::ExportToMenuButton

Kopiert Text aus der Symbolleistenschaltfläche in ein Menü.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parameter

*menuButton*<br/>
[in] Ein Verweis auf die Zielmenüschaltfläche.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn die Methode erfolgreich ausgeführt wird, andernfalls 0 (null).

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft die Basisklassenimplementierung auf ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) und fügt dann an die Zielmenüschaltfläche ein Popupmenü an, das jedes Menüelement der Symbolleiste in dieser Schaltfläche enthält. Diese Methode fügt keine Untermenüs an das Popupmenü an.

Diese Methode schlägt fehl, `m_pToolBar`wenn die übergeordnete Symbolleiste , null ist oder die Basisklassenimplementierung FALSE zurückgibt.

## <a name="cmfcdropdowntoolbarbuttongetdropdowntoolbar"></a><a name="getdropdowntoolbar"></a>CMFCDropDownToolbarButton::GetDropDownToolBar

Ruft die Dropdown-Symbolleiste ab, die der Schaltfläche zugeordnet ist.

```
CMFCToolBar* GetDropDownToolBar() const;
```

### <a name="return-value"></a>Rückgabewert

Die Dropdown-Symbolleiste, die der Schaltfläche zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Diese Methode `m_pToolBar` gibt den Datenmember zurück.

## <a name="cmfcdropdowntoolbarbuttonisdropdown"></a><a name="isdropdown"></a>CMFCDropDownToolbarButton::IsDropDown

Bestimmt, ob die Dropdown-Symbolleiste derzeit geöffnet ist.

```
BOOL IsDropDown() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Dropdown-Symbolleiste derzeit geöffnet ist. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Das Framework öffnet die Dropdown-Symbolleiste mit der [CMFCDropDownToolbarButton::DropDownToolbar-Methode.](#dropdowntoolbar) Das Framework schließt die Dropdown-Symbolleiste, wenn der Benutzer die linke Maustaste im Nicht-Client-Bereich der Dropdown-Symbolleiste drückt.

## <a name="cmfcdropdowntoolbarbuttonisextrasize"></a><a name="isextrasize"></a>CMFCDropDownToolbarButton::IsExtraSize

Legt fest, ob die Schaltfläche mit einem erweiterten Rahmen angezeigt werden kann.

```
virtual BOOL IsExtraSize() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Symbolleistenschaltfläche mit einem erweiterten Rahmen angezeigt werden kann. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu erweiterten Rahmen finden Sie unter [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).

## <a name="cmfcdropdowntoolbarbuttonm_uishowbardelay"></a><a name="m_uishowbardelay"></a>CMFCDropDownToolbarButton::m_uiShowBarDelay

Gibt an, wie lange ein Benutzer die Maustaste gedrückt halten muss, bevor die Dropdown-Symbolleiste angezeigt wird.

```
static UINT m_uiShowBarDelay;
```

### <a name="remarks"></a>Bemerkungen

Die Verzögerungszeit wird in Millisekunden gemessen. Der Standardwert ist 500. Sie können eine weitere Verzögerung festlegen, indem Sie den Wert dieses freigegebenen Datenelements ändern.

## <a name="cmfcdropdowntoolbarbuttononcalculatesize"></a><a name="oncalculatesize"></a>CMFCDropDownToolbarButton::OnCalculateSize

Wird vom Framework aufgerufen, um die Größe der Schaltfläche für den angegebenen Gerätekontext und Andockstatus zu berechnen.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Der Gerätekontext, der die Schaltfläche anzeigt.

*sizeStandard*<br/>
[in] Die Standardgröße der Schaltfläche.

*bHorz*<br/>
[in] Der Dockstatus der übergeordneten Symbolleiste. Dieser Parameter ist TRUE, wenn die Symbolleiste horizontal angedockt ist oder unverankert ist, oder FALSE, wenn die Symbolleiste vertikal angedockt ist.

### <a name="return-value"></a>Rückgabewert

Eine `SIZE` Struktur, die die Abmessungen der Schaltfläche in Pixel enthält.

### <a name="remarks"></a>Bemerkungen

Diese Methode erweitert die Basisklassenimplementierung ( [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)), indem die Breite des Dropdownpfeils zur horizontalen Dimension der Schaltflächengröße hinzugefügt wird.

## <a name="cmfcdropdowntoolbarbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCDropDownToolbarButton::OnChangeParentWnd

Wird vom Framework aufgerufen, wenn die Schaltfläche in eine neue Symbolleiste eingefügt wird.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parameter

*pWndParent*<br/>
[in] Das neue übergeordnete Fenster.

### <a name="remarks"></a>Bemerkungen

Diese Methode überschreibt die Basisklassenimplementierung ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)), indem die Textbeschriftung ( [CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)) geformatelt und die [Datenmember CMFCToolBarButton::m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext) und [CMFCToolBarButton::m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton) Datenmember auf FALSE festgelegt werden.

## <a name="cmfcdropdowntoolbarbuttononclick"></a><a name="onclick"></a>CMFCDropDownToolbarButton::OnClick

Wird vom Framework aufgerufen, wenn der Benutzer auf die Maustaste klickt.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
[in] Das übergeordnete Fenster der Symbolleistenschaltfläche.

*bDelay*<br/>
[in] TRUE, wenn die Nachricht mit einer Verzögerung behandelt werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Schaltfläche die Klicknachricht verarbeitet; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Methode erweitert die Basisklassenimplementierung [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), indem der Status der Dropdown-Symbolleiste aktualisiert wird.

Wenn ein Benutzer auf die Symbolleistenschaltfläche klickt, erstellt diese Methode einen Timer, der die vom [CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay) Datenelement angegebene Zeitspanne wartet, und öffnet dann die Dropdown-Symbolleiste mithilfe der [CMFCDropDownToolbarButton::DropDownToolbar-Methode.](#dropdowntoolbar) Diese Methode schließt die Dropdown-Symbolleiste, wenn der Benutzer das zweite Mal auf die Symbolleistenschaltfläche klickt.

## <a name="cmfcdropdowntoolbarbuttononclickup"></a><a name="onclickup"></a>CMFCDropDownToolbarButton::OnClickUp

Wird vom Framework aufgerufen, wenn der Benutzer die Maustaste loslässt.

```
virtual BOOL OnClickUp();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Schaltfläche die Klicknachricht verarbeitet; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Methode erweitert die Basisklassenimplementierung [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup), indem der Status der Dropdown-Symbolleiste aktualisiert wird.

Diese Methode stoppt den Dropdown-Toolbar-Timer, wenn er aktiv ist. Es schließt die Dropdown-Symbolleiste, wenn sie geöffnet ist.

Weitere Informationen zur Dropdown-Symbolleiste und zum Dropdown-Toolleisten-Timer finden Sie unter [CMFCDropDownToolbarButton::OnClick](#onclick).

## <a name="cmfcdropdowntoolbarbuttononcontexthelp"></a><a name="oncontexthelp"></a>CMFCDropDownToolbarButton::OnContextHelp

Wird vom Framework aufgerufen, wenn die übergeordnete Symbolleiste eine WM_HELPHITTEST Nachricht verarbeitet.

```
virtual BOOL OnContextHelp(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
[in] Das übergeordnete Fenster der Symbolleistenschaltfläche.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Schaltfläche die Hilfenachricht verarbeitet; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Methode erweitert die Basisklassenimplementierung ( [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)), indem die [CMFCDropDownToolbarButton::OnClick-Methode](#onclick) aufgerufen wird, wobei *bDelay* auf FALSE festgelegt ist. Diese Methode gibt den Wert zurück, der von [CMFCDropDownToolbarButton::OnClick](#onclick)zurückgegeben wird.

Weitere Informationen zur Meldung WM_HELPHITTEST finden Sie unter [TN028: Context-Sensitive Help Support](../../mfc/tn028-context-sensitive-help-support.md).

## <a name="cmfcdropdowntoolbarbuttononcustomizemenu"></a><a name="oncustomizemenu"></a>CMFCDropDownToolbarButton::OnCustomizeMenu

Ändert das bereitgestellte Menü, wenn die Anwendung ein Kontextmenü auf der übergeordneten Symbolleiste anzeigt.

```
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```

### <a name="parameters"></a>Parameter

*pMenu*<br/>
[in] Das zu anpassende Menü.

### <a name="return-value"></a>Rückgabewert

Diese Methode gibt TRUE zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode erweitert die Basisklassenimplementierung ( [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)), indem die folgenden Menüelemente deaktiviert werden:

- **Kopieren von Button-Bild**

- **Button-Darstellung**

- **Image**

- **Text**

- **Bild und Text**

Überschreiben Sie diese Methode, um das Kontextmenü zu ändern, das das Framework im Anpassungsmodus anzeigt.

## <a name="cmfcdropdowntoolbarbuttonondraw"></a><a name="ondraw"></a>CMFCDropDownToolbarButton::OnDraw

Wird vom Framework aufgerufen, um die Schaltfläche mithilfe der angegebenen Stile und Optionen zu zeichnen.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    CMFCToolBarImages* pImages,
    BOOL bHorz = TRUE,
    BOOL bCustomizeMode = FALSE,
    BOOL bHighlight = FALSE,
    BOOL bDrawBorder = TRUE,
    BOOL bGrayDisabledButtons = TRUE);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Der Gerätekontext, der die Schaltfläche anzeigt.

*Rect*<br/>
[in] Das umgrenzende Rechteck der Schaltfläche.

*pImages*<br/>
[in] Die Auflistung von Symbolleistenbildern, die der Schaltfläche zugeordnet ist.

*bHorz*<br/>
[in] Der Dockstatus der übergeordneten Symbolleiste. Dieser Parameter ist TRUE, wenn die Schaltfläche horizontal angedockt ist, und FALSE, wenn die Schaltfläche vertikal angedockt ist.

*bCustomizeMode*<br/>
[in] Gibt an, ob sich die Symbolleiste im Anpassungsmodus befindet. Dieser Parameter ist TRUE, wenn sich die Symbolleiste im Anpassungsmodus befindet, und FALSE, wenn sich die Symbolleiste nicht im Anpassungsmodus befindet.

*bHighlight*<br/>
[in] Gibt an, ob die Schaltfläche hervorgehoben ist. Dieser Parameter ist TRUE, wenn die Schaltfläche hervorgehoben ist, und FALSE, wenn die Schaltfläche nicht hervorgehoben ist.

*bDrawBorder*<br/>
[in] Gibt an, ob die Schaltfläche ihren Rahmen anzeigen soll. Dieser Parameter ist TRUE, wenn die Schaltfläche ihren Rahmen anzeigen soll, und FALSE, wenn die Schaltfläche ihren Rahmen nicht anzeigen soll.

*bGrayDisabledButtons*<br/>
[in] Gibt an, ob deaktivierte Schaltflächen schattieren oder die Sammlung deaktivierter Bilder verwendet werden soll. Dieser Parameter ist TRUE, wenn deaktivierte Schaltflächen schattiert werden sollen, und FALSE, wenn diese Methode die deaktivierte Images-Auflistung verwenden soll.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, um das Zeichnen von Symbolleistenschaltflächen anzupassen.

## <a name="cmfcdropdowntoolbarbuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a>CMFCDropDownToolbarButton::OnDrawOnCustomizeList

Wird vom Framework aufgerufen, um **Commands** die Schaltfläche im Befehlsbereich des Dialogfelds **Anpassen** zu zeichnen.

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Der Gerätekontext, der die Schaltfläche anzeigt.

*Rect*<br/>
[in] Das umgrenzende Rechteck der Schaltfläche.

*bAusgewählt*<br/>
[in] Gibt an, ob die Schaltfläche ausgewählt ist. Wenn dieser Parameter TRUE ist, wird die Schaltfläche ausgewählt. Wenn dieser Parameter FALSE ist, ist die Schaltfläche nicht ausgewählt.

### <a name="return-value"></a>Rückgabewert

Die Breite der Schaltfläche im angegebenen Gerätekontext in Pixel.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird vom Anpassungsdialogfeld (Registerkarte **Befehle)** aufgerufen, wenn die Schaltfläche erforderlich ist, um sich selbst im Listenfeld "Besitzer-Zeichnen" anzuzeigen.

Diese Methode erweitert die Basisklassenimplementierung ( [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)), indem die Textbeschriftung der Schaltfläche in den Namen der Schaltfläche geändert wird (d. h. auf den Wert des *Parameters lpszName,* den Sie an den Konstruktor übergeben haben).

## <a name="cmfcdropdowntoolbarbuttonserialize"></a><a name="serialize"></a>CMFCDropDownToolbarButton::Serialisieren

Liest dieses Objekt aus einem Archiv oder schreibt es in ein Archiv.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parameter

*ar*<br/>
[in] Das `CArchive` Objekt, von dem oder an das serialisiert werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Methode erweitert die Basisklassenimplementierung ( [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)) durch Serialisierung der Ressourcen-ID der übergeordneten Symbolleiste. Wenn das Archiv geladen wird ( [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) gibt einen `m_pToolBar` Wert ungleich Null zurück), legt diese Methode das Datenelement auf die Symbolleiste fest, die die serialisierte Ressourcen-ID enthält.

## <a name="cmfcdropdowntoolbarbuttonsetdefaultcommand"></a><a name="setdefaultcommand"></a>CMFCDropDownToolbarButton::SetDefaultCommand

Legt den Standardbefehl fest, den das Framework verwendet, wenn ein Benutzer auf die Schaltfläche klickt.

```cpp
void SetDefaultCommand(UINT uiCmd);
```

### <a name="parameters"></a>Parameter

*uiCmd*<br/>
[in] Die ID des Standardbefehls.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um einen Standardbefehl anzugeben, den das Framework ausführt, wenn der Benutzer auf die Schaltfläche klickt. Ein Element mit der von *uiCmd* angegebenen Befehls-ID muss sich in der übergeordneten Dropdown-Symbolleiste befinden.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar-Klasse](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCToolBar-Klasse](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarMenuButton-Klasse](../../mfc/reference/cmfctoolbarmenubutton-class.md)<br/>
[Exemplarische Vorgehensweise: Steuerelemente in eine Symbolleiste einfügen](../../mfc/walkthrough-putting-controls-on-toolbars.md)
