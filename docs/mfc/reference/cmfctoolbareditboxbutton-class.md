---
title: CMFCToolBarEditBoxButton-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CanBeStretched
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CopyFrom
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetByCmd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetContentsAll
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetContextMenuID
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetEditBorder
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetHwnd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetInvalidateRect
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::HaveHotBorder
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::IsFlatMode
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::NotifyCommand
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnAddToCustomizePage
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnChangeParentWnd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnClick
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnCtlColor
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnGlobalFontsChanged
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnMove
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnShow
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnSize
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnUpdateToolTip
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::SetContextMenuID
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::SetFlatMode
helpviewer_keywords:
- CMFCToolBarEditBoxButton [MFC], CMFCToolBarEditBoxButton
- CMFCToolBarEditBoxButton [MFC], CanBeStretched
- CMFCToolBarEditBoxButton [MFC], CopyFrom
- CMFCToolBarEditBoxButton [MFC], GetByCmd
- CMFCToolBarEditBoxButton [MFC], GetContentsAll
- CMFCToolBarEditBoxButton [MFC], GetContextMenuID
- CMFCToolBarEditBoxButton [MFC], GetEditBorder
- CMFCToolBarEditBoxButton [MFC], GetHwnd
- CMFCToolBarEditBoxButton [MFC], GetInvalidateRect
- CMFCToolBarEditBoxButton [MFC], HaveHotBorder
- CMFCToolBarEditBoxButton [MFC], IsFlatMode
- CMFCToolBarEditBoxButton [MFC], NotifyCommand
- CMFCToolBarEditBoxButton [MFC], OnAddToCustomizePage
- CMFCToolBarEditBoxButton [MFC], OnChangeParentWnd
- CMFCToolBarEditBoxButton [MFC], OnClick
- CMFCToolBarEditBoxButton [MFC], OnCtlColor
- CMFCToolBarEditBoxButton [MFC], OnGlobalFontsChanged
- CMFCToolBarEditBoxButton [MFC], OnMove
- CMFCToolBarEditBoxButton [MFC], OnShow
- CMFCToolBarEditBoxButton [MFC], OnSize
- CMFCToolBarEditBoxButton [MFC], OnUpdateToolTip
- CMFCToolBarEditBoxButton [MFC], SetContextMenuID
- CMFCToolBarEditBoxButton [MFC], SetFlatMode
ms.assetid: b21d9b67-6bf7-4ca9-bd62-b237756e0ab3
ms.openlocfilehash: 064ebe1c8fe377064d410d09e5ef60ed628df2f3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753996"
---
# <a name="cmfctoolbareditboxbutton-class"></a>CMFCToolBarEditBoxButton-Klasse

Eine Symbolleistenschaltfläche, die ein Bearbeitungssteuerelement ( [CEdit-Klasse](../../mfc/reference/cedit-class.md)) enthält.

## <a name="syntax"></a>Syntax

```
class CMFCToolBarEditBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton](#cmfctoolbareditboxbutton)|Erstellt ein `CMFCToolBarEditBoxButton`-Objekt.|
|`CMFCToolBarEditBoxButton::~CMFCToolBarEditBoxButton`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCToolBarEditBoxButton::CanBeStretched](#canbestretched)|Gibt an, ob ein Benutzer die Schaltfläche während der Anpassung dehnen kann. (Überschreibt [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|
|[CMFCToolBarEditBoxButton::Kopieren von](#copyfrom)|Kopiert die Eigenschaften einer anderen Symbolleistenschaltfläche in die aktuelle Schaltfläche. (Überschreibt [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::CreateBearbeiten](#createedit)|Erstellt ein neues Bearbeitungssteuerelement in der Schaltfläche.|
|`CMFCToolBarEditBoxButton::CreateObject`|Wird vom Framework verwendet, um eine dynamische Instanz dieses Klassentyps zu erstellen.|
|[CMFCToolBarEditBoxButton::GetByCmd](#getbycmd)|Ruft das `CMFCToolBarEditBoxButton` erste Objekt in der Anwendung ab, das über die angegebene Befehls-ID verfügt.|
|[CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall)|Ruft den Text des ersten Bearbeitungsfeld-Symbolleistensteuerelements ab, das über die angegebene Befehls-ID verfügt.|
|[CMFCToolBarEditBoxButton::GetContextMenuID](#getcontextmenuid)|Ruft die Ressourcen-ID des Kontextmenüs ab, das der Schaltfläche zugeordnet ist.|
|[CMFCToolBarEditBoxButton::GetEditBorder](#geteditborder)|Ruft das umgrenzende Rechteck des Bearbeitungsteils der Schaltfläche "Bearbeitungsfeld" ab.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::GetEditBox](#geteditbox)|Gibt einen Zeiger auf das Bearbeitungssteuerelement zurück, das in die Schaltfläche eingebettet ist.|
|[CMFCToolBarEditBoxButton::GetHwnd](#gethwnd)|Ruft den Fensterhandle ab, der der Symbolleistenschaltfläche zugeordnet ist. (Überschreibt [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|
|[CMFCToolBarEditBoxButton::GetInvalidateRect](#getinvalidaterect)|Ruft den Bereich des Clientbereichs der Schaltfläche ab, der neu gezeichnet werden muss. (Überschreibt [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect).)|
|`CMFCToolBarEditBoxButton::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|
|[CMFCToolBarEditBoxButton::HaveHotBorder](#havehotborder)|Bestimmt, ob ein Rahmen der Schaltfläche angezeigt wird, wenn ein Benutzer auf die Schaltfläche klickt. (Überschreibt [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|
|[CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode)|Legt fest, ob Bearbeitungsschaltflächen einen flachen Stil haben.|
|[CMFCToolBarEditBoxButton::NotifyCommand](#notifycommand)|Gibt an, ob die Schaltfläche die [WM_COMMAND-Nachricht](/windows/win32/menurc/wm-command) verarbeitet. (Überschreibt [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|
|[CMFCToolbarEditBoxButton::OnAddToCustomizePage](#onaddtocustomizepage)|Wird vom Framework aufgerufen, wenn die Schaltfläche zu einem Dialogfeld **Anpassen** hinzugefügt wird. (Überschreibt [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|
|`CMFCToolBarEditBoxButton::OnCalculateSize`|Wird vom Framework aufgerufen, um die Größe der Schaltfläche für den angegebenen Gerätekontext und Andockstatus zu berechnen. (Überschreibt [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](#onchangeparentwnd)|Wird vom Framework aufgerufen, wenn die Schaltfläche in eine neue Symbolleiste eingefügt wird. (Überschreibt [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCToolBarEditBoxButton::OnClick](#onclick)|Wird vom Framework aufgerufen, wenn der Benutzer auf die Maustaste klickt. (Überschreibt [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCToolBarEditBoxButton::OnCtlColor](#onctlcolor)|Wird vom Framework aufgerufen, wenn die übergeordnete Symbolleiste eine WM_CTLCOLOR Nachricht verarbeitet. (Überschreibt [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|
|`CMFCToolBarEditBoxButton::OnDraw`|Wird vom Framework aufgerufen, um die Schaltfläche mithilfe der angegebenen Stile und Optionen zu zeichnen. (Überschreibt [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|Wird vom Framework aufgerufen, um **Commands** die Schaltfläche im Befehlsbereich des Dialogfelds **Anpassen** zu zeichnen. (Überschreibt [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCToolBarEditBoxButton::OnGlobalFontsChanged](#onglobalfontschanged)|Wird vom Framework aufgerufen, wenn sich die globale Schriftart geändert hat. (Überschreibt [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|
|[CMFCToolBarEditBoxButton::OnMove](#onmove)|Wird vom Framework aufgerufen, wenn die übergeordnete Symbolleiste verschoben wird. (Überschreibt [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|
|[CMFCToolBarEditBoxButton::OnShow](#onshow)|Wird vom Framework aufgerufen, wenn die Schaltfläche sichtbar oder unsichtbar wird. (Überschreibt [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|
|[CMFCToolBarEditBoxButton::OnSize](#onsize)|Wird vom Framework aufgerufen, wenn die übergeordnete Symbolleiste ihre Größe oder Position ändert und diese Änderung dazu führt, dass die Schaltfläche die Größe ändert. (Überschreibt [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|
|[CMFCToolbarEditBoxButton::OnUpdateToolTip](#onupdatetooltip)|Wird vom Framework aufgerufen, wenn die übergeordnete Symbolleiste den QuickInfo-Text aktualisiert. (Überschreibt [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|
|`CMFCToolBarEditBoxButton::Serialize`|Liest dieses Objekt aus einem Archiv oder schreibt es in ein Archiv. (Überschreibt [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|`CMFCToolBarEditBoxButton::SetACCData`|Füllt das bereitgestellte `CAccessibilityData` Objekt mit Eingabehilfendaten aus der Symbolleistenschaltfläche. (Überschreibt [CMFCToolBarButton::SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata).)|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetContents](#setcontents)|Legt den Text im Bearbeitungssteuerelement der Schaltfläche fest.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall)|Sucht die Schaltfläche "Bearbeitungssteuerelement" mit einer angegebenen Befehls-ID und legt den Text im Bearbeitungssteuerelement dieser Schaltfläche fest.|
|[CMFCToolBarEditBoxButton::SetContextMenuID](#setcontextmenuid)|Gibt die Ressourcen-ID des Kontextmenüs an, das der Schaltfläche zugeordnet ist.|
|[CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode)|Gibt die flache Darstellung von Bearbeitungsschaltflächen in der Anwendung an.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetStyle](#setstyle)|Gibt den Stil der Schaltfläche an. (Überschreibt [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|

## <a name="remarks"></a>Bemerkungen

Führen Sie die folgenden Schritte aus, um eine Schaltfläche zum Bearbeiten einer Symbolleiste hinzuzufügen:

1. Reservieren Sie eine Platzhalterressourcen-ID für die Schaltfläche in der übergeordneten Symbolleistenressource.

2. Konstruieren Sie ein `CMFCToolBarEditBoxButton`-Objekt.

3. Ersetzen Sie im Nachrichtenhandler, der die AFX_WM_RESETTOOLBAR-Nachricht verarbeitet, die Dummy-Schaltfläche durch die neue Kombinationsfeldschaltfläche mithilfe der [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Einstecken von Steuerelementen auf Symbolleisten](../../mfc/walkthrough-putting-controls-on-toolbars.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung verschiedener Methoden in der `CMFCToolBarEditBoxButton` -Klasse. Im Beispiel wird gezeigt, wie Sie angeben können, dass ein Benutzer die Schaltfläche während der Anpassung dehnen kann, dass ein Rahmen der Schaltfläche angezeigt wird, wenn ein Benutzer auf die Schaltfläche klickt, den Text im Textfeldsteuerelement festlegen, die flache Darstellung von Bearbeitungsfeldschaltflächen in der Anwendung angeben und den Stil eines Werkzeugleisten-Bearbeitungsfeldsteuerelements angeben.

[!code-cpp[NVC_MFC_RibbonApp#40](../../mfc/reference/codesnippet/cpp/cmfctoolbareditboxbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

`CMFCToolBarEditBoxButton`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxtoolbareditboxbutton.h

## <a name="cmfctoolbareditboxbuttoncanbestretched"></a><a name="canbestretched"></a>CMFCToolBarEditBoxButton::CanBeStretched

Gibt an, ob ein Benutzer die Schaltfläche während der Anpassung dehnen kann.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Rückgabewert

Diese Methode gibt TRUE zurück.

### <a name="remarks"></a>Bemerkungen

Standardmäßig erlaubt das Framework dem Benutzer nicht, eine Symbolleistenschaltfläche während der Anpassung zu dehnen. Diese Methode erweitert die Basisklassenimplementierung ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)), indem dem Benutzer ermöglicht wird, eine Bearbeitungsfeldsymbolleistenschaltfläche während der Anpassung zu dehnen.

## <a name="cmfctoolbareditboxbuttoncmfctoolbareditboxbutton"></a><a name="cmfctoolbareditboxbutton"></a>CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton

Erstellt ein [CMFCToolBarEditBoxButton-Objekt.](../../mfc/reference/cmfctoolbareditboxbutton-class.md)

```
CMFCToolBarEditBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=ES_AUTOHSCROLL,
    int iWidth=0);
```

### <a name="parameters"></a>Parameter

*uiID*<br/>
[in] Gibt die Steuerelement-ID an.

*iImage*<br/>
[in] Gibt den nullbasierten Index eines Symbolleistenabbilds an. Das Bild befindet sich im [CMFCToolBarImages-Klassenobjekt,](../../mfc/reference/cmfctoolbarimages-class.md) das die [CMFCToolBar-Klasse](../../mfc/reference/cmfctoolbar-class.md) verwaltet.

*dwStyle*<br/>
[in] Gibt den Bearbeitungssteuerelementstil an.

*iWidth*<br/>
[in] Gibt die Breite in Pixeln des Bearbeitungssteuerelements an.

### <a name="remarks"></a>Bemerkungen

Der Standardkonstruktor legt den Bearbeitungssteuerelementstil auf die folgende Kombination fest:

WS_CHILD | WS_VISIBLE | ES_AUTOHSCROLL

Die Standardbreite des Steuerelements beträgt 150 Pixel.

## <a name="cmfctoolbareditboxbuttoncopyfrom"></a><a name="copyfrom"></a>CMFCToolBarEditBoxButton::Kopieren von

Kopiert die Eigenschaften einer anderen Symbolleistenschaltfläche in die aktuelle Schaltfläche.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parameter

*src*<br/>
[in] Ein Verweis auf die Quellschaltfläche, aus der kopiert werden soll.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um eine weitere Symbolleistenschaltfläche in diese Symbolleistenschaltfläche zu kopieren. *src* muss vom `CMFCToolBarEditBoxButton`Typ sein.

## <a name="cmfctoolbareditboxbuttoncreateedit"></a><a name="createedit"></a>CMFCToolBarEditBoxButton::CreateBearbeiten

Erstellt ein neues Bearbeitungssteuerelement in der Schaltfläche.

```
virtual CEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>Parameter

*pWndParent*<br/>
[in] Gibt das übergeordnete Fenster des Bearbeitungssteuerelements an. Es darf nicht NULL sein.

*Rect*<br/>
[in] Gibt die Größe und Position des Bearbeitungssteuerelements an.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das neu erstellte Bearbeitungssteuerelement; Es ist NULL, wenn die Erstellung und Anlage des Steuerelements fehlschlagen.

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CMFCToolBarEditBoxButton` ein Objekt in zwei Schritten. Rufen Sie zuerst den Konstruktor auf, und rufen Sie dann `CreateEdit` `CMFCToolBarEditBoxButton` auf, das das Windows-Bearbeitungssteuerelement erstellt und an das Objekt anfügt.

## <a name="cmfctoolbareditboxbuttongetbycmd"></a><a name="getbycmd"></a>CMFCToolBarEditBoxButton::GetByCmd

Ruft das `CMFCToolBarEditBoxButton` erste Objekt in der Anwendung ab, das über die angegebene Befehls-ID verfügt.

```
static CMFCToolBarEditBoxButton* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parameter

*uiCmd*<br/>
[in] Die Befehls-ID der abzurufenden Schaltfläche.

### <a name="return-value"></a>Rückgabewert

Das `CMFCToolBarEditBoxButton` erste Objekt in der Anwendung, das die angegebene Befehls-ID hat, oder NULL, wenn kein solches Objekt vorhanden ist.

### <a name="remarks"></a>Bemerkungen

Diese gemeinsame Dienstprogrammmethode wird von Methoden wie [CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall) und [CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall) verwendet, um den Text des ersten Bearbeitungsfeld-Symbolleistensteuerelements mit der angegebenen Befehls-ID festzulegen oder abzubekommen.

## <a name="cmfctoolbareditboxbuttongetcontentsall"></a><a name="getcontentsall"></a>CMFCToolBarEditBoxButton::GetContentsAll

Ruft den Text des ersten Bearbeitungsfeld-Symbolleistensteuerelements ab, das über die angegebene Befehls-ID verfügt.

```
static CString __stdcall GetContentsAll(UINT uiCmd);
```

### <a name="parameters"></a>Parameter

*uiCmd*<br/>
[in] Die Befehls-ID der Schaltfläche, von der Inhalte abgerufen werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein `CString` Objekt, das den Text des ersten Bearbeitungsfeld-Symbolleistensteuerelements mit der angegebenen Befehls-ID enthält.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt die `CMFCToolBarEditBoxButton` leere Zeichenfolge zurück, wenn keine Objekte über die angegebene Befehls-ID verfügen.

## <a name="cmfctoolbareditboxbuttongetcontextmenuid"></a><a name="getcontextmenuid"></a>CMFCToolBarEditBoxButton::GetContextMenuID

Ruft die Ressourcen-ID des Kontextmenüs ab, das der Schaltfläche zugeordnet ist.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>Rückgabewert

Die Ressourcen-ID des Kontextmenüs, das der Schaltfläche oder 0 zugeordnet ist, wenn der Schaltfläche kein Verknüpfungsmenü zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Das Framework verwendet die Ressourcen-ID, um das Kontextmenü zu erstellen, wenn der Benutzer mit der rechten Maustaste auf die Schaltfläche klickt.

## <a name="cmfctoolbareditboxbuttongeteditborder"></a><a name="geteditborder"></a>CMFCToolBarEditBoxButton::GetEditBorder

Ruft das umgrenzende Rechteck des Bearbeitungsteils der Schaltfläche "Bearbeitungsfeld" ab.

```
virtual void GetEditBorder(CRect& rectBorder);
```

### <a name="parameters"></a>Parameter

*rectBorder*<br/>
[out] Ein Verweis `CRect` auf das Objekt, das das umgrenzende Rechteck empfängt.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft das umgrenzende Rechteck des Bearbeitungssteuerelements in Clientkoordinaten ab. Es erweitert die Größe des Rechtecks in jeder Richtung um ein Pixel.

Die [CMFCVisualManager::OnDrawEditBorder-Methode](../../mfc/reference/cmfcvisualmanager-class.md#ondraweditborder) ruft diese Methode auf, wenn sie den Rahmen um ein `CMFCToolBarEditBoxButton` Objekt zeichnet.

## <a name="cmfctoolbareditboxbuttongeteditbox"></a><a name="geteditbox"></a>CMFCToolBarEditBoxButton::GetEditBox

Gibt einen Zeiger auf das [CEdit-Klassensteuerelement](../../mfc/reference/cedit-class.md) zurück, das in die Schaltfläche eingebettet ist.

```
CEdit* GetEditBox() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das [CEdit-Klassensteuerelement,](../../mfc/reference/cedit-class.md) das die Schaltfläche enthält. Es ist NULL, wenn das `CEdit` Steuerelement noch nicht erstellt wurde.

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CEdit` das Steuerelement, indem Sie [CMFCToolBarEditBoxButton::CreateEdit](#createedit)aufrufen.

## <a name="cmfctoolbareditboxbuttongethwnd"></a><a name="gethwnd"></a>CMFCToolBarEditBoxButton::GetHwnd

Ruft den Fensterhandle ab, der der Symbolleistenschaltfläche zugeordnet ist.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Rückgabewert

Das Fensterhandle, das der Schaltfläche zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Diese Methode überschreibt die [CMFCToolBarButton::GetHwnd-Methode,](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) indem das Fensterhandle des Bearbeitungssteuerelementsteils der Schaltfläche "Bearbeitungsbox" zurückgegeben wird.

## <a name="cmfctoolbareditboxbuttongetinvalidaterect"></a><a name="getinvalidaterect"></a>CMFCToolBarEditBoxButton::GetInvalidateRect

Ruft den Bereich des Clientbereichs der Schaltfläche ab, der neu gezeichnet werden muss.

```
virtual const CRect GetInvalidateRect() const;
```

### <a name="return-value"></a>Rückgabewert

Ein `CRect` Objekt, das den Bereich angibt, der neu gezeichnet werden muss.

### <a name="remarks"></a>Bemerkungen

Diese Methode erweitert die Basisklassenimplementierung [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect), indem in den Bereich der Textbeschriftung eingebunden wird.

## <a name="cmfctoolbareditboxbuttonhavehotborder"></a><a name="havehotborder"></a>CMFCToolBarEditBoxButton::HaveHotBorder

Bestimmt, ob ein Rahmen der Schaltfläche angezeigt wird, wenn ein Benutzer auf die Schaltfläche klickt.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn eine Schaltfläche den Rahmen anzeigt, wenn diese ausgewählt ist. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Methode erweitert die Basisklassenimplementierung [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder), indem ein Wert ungleich Null zurückgegeben wird, wenn das Steuerelement sichtbar ist.

## <a name="cmfctoolbareditboxbuttonisflatmode"></a><a name="isflatmode"></a>CMFCToolBarEditBoxButton::IsFlatMode

Legt fest, ob Bearbeitungsschaltflächen einen flachen Stil haben.

```
static BOOL __stdcall IsFlatMode();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Schaltflächen einen flachen Stil haben; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Standardmäßig haben Bearbeitungsschaltflächen einen flachen Stil. Verwenden Sie die [CMFCToolBarEditBoxButton::SetFlatMode-Methode,](#setflatmode) um die Darstellung des flachen Stils für Ihre Anwendung zu ändern.

## <a name="cmfctoolbareditboxbuttonnotifycommand"></a><a name="notifycommand"></a>CMFCToolBarEditBoxButton::NotifyCommand

Gibt an, ob die Schaltfläche die [WM_COMMAND-Nachricht](/windows/win32/menurc/wm-command) verarbeitet.

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Parameter

*iNotifyCode*<br/>
[in] Die dem Befehl zugeordnete Benachrichtigung.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Schaltfläche die WM_COMMAND Nachricht verarbeitet, oder FALSE, um anzuzeigen, dass die Nachricht von der übergeordneten Symbolleiste behandelt werden muss.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Methode auf, wenn es eine [WM_COMMAND](/windows/win32/menurc/wm-command) Nachricht an das übergeordnete Fenster senden soll.

Diese Methode erweitert die Basisklassenimplementierung ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) durch Verarbeitung der [EN_UPDATE-Benachrichtigung.](/windows/win32/Controls/en-update) Für jedes Bearbeitungsfeld mit derselben Befehls-ID wie dieses Objekt legt es seine Textbeschriftung auf die Textbeschriftung dieses Objekts fest.

## <a name="cmfctoolbareditboxbuttononaddtocustomizepage"></a><a name="onaddtocustomizepage"></a>CMFCToolbarEditBoxButton::OnAddToCustomizePage

Wird vom Framework aufgerufen, wenn die Schaltfläche zu einem Dialogfeld **Anpassen** hinzugefügt wird.

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode erweitert die Basisklassenimplementierung ( [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)), indem die Eigenschaften aus dem Bearbeitungsfeldsteuerelement in jede Symbolleiste kopiert werden, die dieselbe Befehls-ID wie dieses Objekt hat. Diese Methode bewirkt nichts, wenn keine Symbolleiste über ein Bearbeitungsfeldsteuerelement verfügt, das dieselbe Befehls-ID wie dieses Objekt hat.

Weitere Informationen zum Dialogfeld **Anpassen** finden Sie unter [CMFCToolBarsCustomizeDialog Class](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

## <a name="cmfctoolbareditboxbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCToolBarEditBoxButton::OnChangeParentWnd

Wird vom Framework aufgerufen, wenn die Schaltfläche in eine neue Symbolleiste eingefügt wird.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parameter

*pWndParent*<br/>
[in] Ein Zeiger auf das neue übergeordnete Fenster.

### <a name="remarks"></a>Bemerkungen

Diese Methode überschreibt die Basisklassenimplementierung ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)), indem das interne `CEdit` Objekt neu erstellt wird.

## <a name="cmfctoolbareditboxbuttononclick"></a><a name="onclick"></a>CMFCToolBarEditBoxButton::OnClick

Wird vom Framework aufgerufen, wenn der Benutzer auf die Maustaste klickt.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
[in] Nicht verwendet.

*bDelay*<br/>
[in] Nicht verwendet.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Schaltfläche die Klicknachricht verarbeitet; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Methode überschreibt die Basisklassenimplementierung ( [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)), indem `CEdit` ein Wert ungleich Null zurückgegeben wird, wenn das interne Objekt sichtbar ist.

## <a name="cmfctoolbareditboxbuttononctlcolor"></a><a name="onctlcolor"></a>CMFCToolBarEditBoxButton::OnCtlColor

Wird vom Framework aufgerufen, wenn die übergeordnete Symbolleiste eine WM_CTLCOLOR Nachricht verarbeitet.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Der Gerätekontext, der die Schaltfläche anzeigt.

*nCtlColor*<br/>
[in] Nicht verwendet.

### <a name="return-value"></a>Rückgabewert

Ein Handle für den globalen Fensterpinsel.

### <a name="remarks"></a>Bemerkungen

Diese Methode überschreibt die Basisklassenimplementierung ( [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)), indem die Text- und Hintergrundfarben des bereitgestellten Gerätekontexts auf die globalen Text- bzw. Hintergrundfarben gesetzt werden.

Weitere Informationen zu globalen Optionen, die Für Ihre Anwendung verfügbar sind, finden Sie unter [AFX_GLOBAL_DATA Structure](../../mfc/reference/afx-global-data-structure.md).

## <a name="cmfctoolbareditboxbuttononglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolBarEditBoxButton::OnGlobalFontsChanged

Wird vom Framework aufgerufen, wenn sich die globale Schriftart geändert hat.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode erweitert die Basisklassenimplementierung ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)), indem die Schriftart des Steuerelements in die Der globalen Schriftart geändert wird.

Weitere Informationen zu globalen Optionen, die Für Ihre Anwendung verfügbar sind, finden Sie unter [AFX_GLOBAL_DATA Structure](../../mfc/reference/afx-global-data-structure.md).

## <a name="cmfctoolbareditboxbuttononmove"></a><a name="onmove"></a>CMFCToolBarEditBoxButton::OnMove

Wird vom Framework aufgerufen, wenn die übergeordnete Symbolleiste verschoben wird.

```
virtual void OnMove();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode überschreibt die Standardklassenimplementierung ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)), `CEdit` indem die Position des internen Objekts aktualisiert wird.

## <a name="cmfctoolbareditboxbuttononshow"></a><a name="onshow"></a>CMFCToolBarEditBoxButton::OnShow

Wird vom Framework aufgerufen, wenn die Schaltfläche sichtbar oder unsichtbar wird.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parameter

*bShow*<br/>
[in] Gibt an, ob die Schaltfläche sichtbar ist. Wenn dieser Parameter TRUE ist, ist die Schaltfläche sichtbar. Andernfalls ist die Schaltfläche nicht sichtbar.

### <a name="remarks"></a>Bemerkungen

Diese Methode erweitert die Basisklassenimplementierung ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)), indem die Schaltfläche angezeigt wird, wenn *bShow* TRUE ist. Andernfalls blendet diese Methode die Schaltfläche aus.

## <a name="cmfctoolbareditboxbuttononsize"></a><a name="onsize"></a>CMFCToolBarEditBoxButton::OnSize

Wird vom Framework aufgerufen, wenn die übergeordnete Symbolleiste ihre Größe oder Position ändert und diese Änderung dazu führt, dass die Schaltfläche die Größe ändert.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parameter

*iSize*<br/>
[in] Die neue Breite der Schaltfläche in Pixel.

### <a name="remarks"></a>Bemerkungen

Diese Methode überschreibt die Standardklassenimplementierung [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize), indem die `CEdit` Größe und Position des internen Objekts aktualisiert wird.

## <a name="cmfctoolbareditboxbuttononupdatetooltip"></a><a name="onupdatetooltip"></a>CMFCToolbarEditBoxButton::OnUpdateToolTip

Wird vom Framework aufgerufen, wenn die übergeordnete Symbolleiste den QuickInfo-Text aktualisiert.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Parameter

*pWndParent*<br/>
[in] Nicht verwendet.

*iButtonIndex*<br/>
[in] Nicht verwendet.

*wndToolTip*<br/>
[in] Das Steuerelement, das den QuickInfo-Text anzeigt.

*Str*<br/>
[out] Ein `CString` Objekt, das den aktualisierten QuickInfo-Text empfängt.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Methode den QuickInfo-Text aktualisiert. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Methode erweitert die Basisklassenimplementierung ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)), indem der QuickInfo-Text angezeigt wird, der dem Bearbeitungsteil der Schaltfläche zugeordnet ist. Wenn das `CEdit` interne Objekt NULL ist `CEdit` oder das Fensterhandle des Objekts kein vorhandenes Fenster identifiziert, führt diese Methode nichts aus und gibt FALSE zurück.

## <a name="cmfctoolbareditboxbuttonsetcontents"></a><a name="setcontents"></a>CMFCToolBarEditBoxButton::SetContents

Legt den Text im Textfeldsteuerelement fest.

```
virtual void SetContents(const CString& sContents);
```

### <a name="parameters"></a>Parameter

*sContents*<br/>
[in] Gibt den neuen festzulegenden Text an.

## <a name="cmfctoolbareditboxbuttonsetcontentsall"></a><a name="setcontentsall"></a>CMFCToolBarEditBoxButton::SetContentsAll

Sucht ein [CMFCToolBarEditBoxButton-Objekt,](../../mfc/reference/cmfctoolbareditboxbutton-class.md) das über eine angegebene Befehls-ID verfügt und den angegebenen Text in seinem Textfeld festlegt.

```
static BOOL SetContentsAll(
    UINT uiCmd,
    const CString& strContents);
```

### <a name="parameters"></a>Parameter

*uiCmd*<br/>
[in] Gibt die Befehls-ID des Steuerelements an, für das der Text geändert wird.

*strContents*<br/>
[in] Gibt den neuen festzulegenden Text an.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Text festgelegt wurde; 0, `CMFCToolBarEditBoxButton` wenn das Steuerelement mit der angegebenen Befehls-ID nicht vorhanden ist.

## <a name="cmfctoolbareditboxbuttonsetcontextmenuid"></a><a name="setcontextmenuid"></a>CMFCToolBarEditBoxButton::SetContextMenuID

Gibt die Ressourcen-ID des Kontextmenüs an, das der Schaltfläche zugeordnet ist.

```cpp
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>Parameter

*uiCmd*<br/>
[in] Die Ressourcen-ID des Kontextmenüs.

### <a name="remarks"></a>Bemerkungen

Das Framework verwendet die Ressourcen-ID, um das Kontextmenü zu erstellen, wenn der Benutzer mit der rechten Maustaste auf die Symbolleistenschaltfläche klickt.

## <a name="cmfctoolbareditboxbuttonsetflatmode"></a><a name="setflatmode"></a>CMFCToolBarEditBoxButton::SetFlatMode

Gibt die flache Darstellung von Bearbeitungsschaltflächen in der Anwendung an.

```
static void __stdcall SetFlatMode(BOOL bFlat = TRUE);
```

### <a name="parameters"></a>Parameter

*bFlat*<br/>
[in] Der flache Stil für Bearbeitungsfeldschaltflächen. Wenn dieser Parameter TRUE ist, ist die flache Stildarstellung aktiviert. Andernfalls ist das flache Erscheinungsbild deaktiviert.

### <a name="remarks"></a>Bemerkungen

Der Standardstil für Die Schaltflächen zum Bearbeiten von Feldern ist TRUE. Verwenden Sie die [CMFCToolBarEditBoxButton::IsFlatMode-Methode,](#isflatmode) um die flache Darstellung für Ihre Anwendung abzurufen.

## <a name="cmfctoolbareditboxbuttonsetstyle"></a><a name="setstyle"></a>CMFCToolBarEditBoxButton::SetStyle

Gibt den Stil eines Bearbeitungsfeldsteuerelements für die Symbolleiste an.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>Parameter

*nStyle*<br/>
[in] Ein neuer Stil, den festgelegt werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Methode legt [CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle) auf *nStyle* fest Es deaktiviert auch das Textfeld, wenn sich die Anwendung im Anpassungsmodus befindet, und aktiviert es, wenn sich die Anwendung nicht im Anpassungsmodus befindet (siehe [CMFCToolBar::SetCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode) und [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)). Eine Liste gültiger Stilflags finden Sie unter [ToolBar-Steuerelementvorlagen.](../../mfc/reference/toolbar-control-styles.md)

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton-Klasse](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Exemplarische Vorgehensweise: Steuerelemente in eine Symbolleiste einfügen](../../mfc/walkthrough-putting-controls-on-toolbars.md)
