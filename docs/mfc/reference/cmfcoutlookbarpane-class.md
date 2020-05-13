---
title: CMFCOutlookBarPane-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::AddButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::CanBeAttached
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::ClearAll
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::Create
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnablePageScrollMode
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::GetRegularColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsBackgroundTexture
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsDrawShadedHighlight
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackImage
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetDefaultState
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetExtraSpace
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTextColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTransparentColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnableContextMenuItems
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveAllButtons
helpviewer_keywords:
- CMFCOutlookBarPane [MFC], AddButton
- CMFCOutlookBarPane [MFC], CanBeAttached
- CMFCOutlookBarPane [MFC], ClearAll
- CMFCOutlookBarPane [MFC], Create
- CMFCOutlookBarPane [MFC], EnablePageScrollMode
- CMFCOutlookBarPane [MFC], GetRegularColor
- CMFCOutlookBarPane [MFC], IsBackgroundTexture
- CMFCOutlookBarPane [MFC], IsDrawShadedHighlight
- CMFCOutlookBarPane [MFC], RemoveButton
- CMFCOutlookBarPane [MFC], SetBackColor
- CMFCOutlookBarPane [MFC], SetBackImage
- CMFCOutlookBarPane [MFC], SetDefaultState
- CMFCOutlookBarPane [MFC], SetExtraSpace
- CMFCOutlookBarPane [MFC], SetTextColor
- CMFCOutlookBarPane [MFC], SetTransparentColor
- CMFCOutlookBarPane [MFC], EnableContextMenuItems
- CMFCOutlookBarPane [MFC], RemoveAllButtons
ms.assetid: 094e2ef3-a118-487e-a4cc-27626108fe08
ms.openlocfilehash: 97c7edde26bdf13e899d823dcf88d143068d86a4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749607"
---
# <a name="cmfcoutlookbarpane-class"></a>CMFCOutlookBarPane-Klasse

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

Ein von [der CMFCToolBar-Klasse](../../mfc/reference/cmfctoolbar-class.md) abgeleitetes Steuerelement, das in eine Outlook-Leiste eingefügt werden kann ( [CMFCOutlookBar-Klasse](../../mfc/reference/cmfcoutlookbar-class.md)). Der Outlook-Leistenbereich enthält eine Spalte mit großen Schaltflächen. Der Benutzer kann einen Bildlauf durchführen, um die Liste der Schaltflächen nach oben bzw. unten zu verschieben, wenn sie größer ist als der Bereich. Wenn der Benutzer einen Outlook-Leistenbereich von der Outlook-Leiste trennt, ist er frei positionierbar oder kann im Hauptrahmenfenster andocken.

## <a name="syntax"></a>Syntax

```
class CMFCOutlookBarPane : public CMFCToolBar
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMFCOutlookBarPane::CMFCOutlookBarPane`|Der Standardkonstruktor.|
|`CMFCOutlookBarPane::~CMFCOutlookBarPane`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCOutlookBarPane::AddButton](#addbutton)|Fügt dem Outlook-Leistenbereich eine Schaltfläche hinzu.|
|[CMFCOutlookBarPane::CanBeAttached](#canbeattached)|Legt fest, ob der Bereich an einen anderen Bereich oder ein anderes Rahmenfenster angedockt werden kann. (Überschreibt [CBasePane::CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached).)|
|`CMFCOutlookBarPane::CanBeRestored`|Bestimmt, ob das System eine Symbolleiste nach der Anpassung in den ursprünglichen Zustand zurückversetzen kann. (Überschreibt [CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|
|[CMFCOutlookBarPane::ClearAll](#clearall)|Gibt die ressourcen frei, die von den Bildern im Outlook-Leistenbereich verwendet werden.|
|[CMFCOutlookBarPane::Erstellen](#create)|Erstellt den Outlook-Leistenbereich.|
|`CMFCOutlookBarPane::CreateObject`|Wird vom Framework verwendet, um eine dynamische Instanz dieses Klassentyps zu erstellen.|
|`CMFCOutlookBarPane::Dock`|Wird vom Framework aufgerufen, um den Outlook-Leistenbereich andocken zu können. (Überschreibt `CPane::Dock`.)|
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|Gibt an, ob die Bildlaufpfeile im Outlook-Leistenbereich die Liste der Schaltflächen nach Seite oder nach Schaltfläche voranbringen.|
|[CMFCOutlookBarPane::GetRegularColor](#getregularcolor)|Gibt die reguläre (nicht ausgewählte) Textfarbe des Outlook-Leistenbereichs zurück.|
|`CMFCOutlookBarPane::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|
|[CMFCOutlookBarPane::IsBackgroundTexture](#isbackgroundtexture)|Bestimmt, ob ein Hintergrundbild für den Outlook-Leistenbereich geladen ist.|
|`CMFCOutlookBarPane::IsChangeState`|Bestimmt, ob ein unverankerter Bereich angedockt werden kann. (Überschreibt `CPane::IsChangeState`.)|
|[CMFCOutlookBarPane::IsDrawShadedHighlight](#isdrawshadedhighlight)|Legt fest, ob der Schaltflächenrahmen schattiert ist, wenn eine Schaltfläche hervorgehoben und ein Hintergrundbild angezeigt wird.|
|`CMFCOutlookBarPane::OnBeforeFloat`|Wird vom Framework aufgerufen, wenn ein Bereich schweben soll. (Überschreibt [CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat).)|
|[CMFCOutlookBarPane::RemoveButton](#removebutton)|Entfernt die Schaltfläche mit einer angegebenen Befehls-ID.|
|`CMFCOutlookBarPane::RestoreOriginalstate`|Stellt den originalen Zustand einer Symbolleiste wieder her. (Überschreibt [CMFCToolBar::RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate).)|
|[CMFCOutlookBarPane::SetBackColor](#setbackcolor)|Legt die Hintergrundfarbe fest.|
|[CMFCOutlookBarPane::SetBackImage](#setbackimage)|Legt das Hintergrundbild fest.|
|[CMFCOutlookBarPane::SetDefaultState](#setdefaultstate)|Setzt den Outlook-Leistenbereich auf den ursprünglichen Satz von Schaltflächen zurück.|
|[CMFCOutlookBarPane::SetExtraSpace](#setextraspace)|Legt die Anzahl der Pixel des Auffüllens fest, die um Schaltflächen im Outlook-Leistenbereich verwendet werden.|
|[CMFCOutlookBarPane::SetTextColor](#settextcolor)|Legt die Farben des regulären und hervorgehobenen Texts im Outlook-Leistenbereich fest.|
|[CMFCOutlookBarPane::SetTransparentColor](#settransparentcolor)|Legt die transparente Farbe für den Outlook-Leistenbereich fest.|
|`CMFCOutlookBarPane::SmartUpdate`|Wird intern verwendet, um die Outlook-Leiste zu aktualisieren. (Überschreibt `CMFCToolBar::SmartUpdate`.)|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCOutlookBarPane::EnableContextMenuItems](#enablecontextmenuitems)|Gibt an, welche Verknüpfungsmenüelemente im Anpassungsmodus angezeigt werden.|
|[CMFCOutlookBarPane::RemoveAllButtons](#removeallbuttons)|Entfernt alle Schaltflächen aus dem Outlook-Leistenbereich. (Überschreibt [CMFCToolBar::RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons).)|

## <a name="remarks"></a>Bemerkungen

Informationen zum Implementieren einer Outlookleiste finden Sie unter [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).

Ein Beispiel für eine Outlook-Leiste finden Sie im OutlookDemo-Beispielprojekt.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCOutlookBarPane` wie verschiedene Methoden der Klasse verwendet werden. Das Beispiel zeigt, wie Sie einen Outlook-Leistenbereich erstellen, den Seitenbildlaufmodus aktivieren, das Andocken aktivieren und die Hintergrundfarbe der Outlook-Leiste festlegen. Dieser Codeausschnitt ist Teil des [Outlook Multi Views-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookMultiViews#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#4](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxoutlookbarpane.h

## <a name="cmfcoutlookbarpaneaddbutton"></a><a name="addbutton"></a>CMFCOutlookBarPane::AddButton

Fügt dem Outlook-Leistenbereich eine Schaltfläche hinzu.

```
BOOL AddButton(
    UINT uiImage,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    UINT uiImage,
    UINT uiLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    LPCTSTR szBmpFileName,
    LPCTSTR szLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    HBITMAP hBmp,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    HICON hIcon,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1,
    BOOL bAlphaBlend=FALSE);
```

### <a name="parameters"></a>Parameter

*uiImage*<br/>
[in] Gibt den Ressourcenbezeichner einer Bitmap an.

*lpszLabel*<br/>
[in] Gibt den Text der Schaltfläche an.

*iIdCommand*<br/>
[in] Gibt die ID des Schaltflächensteuerelements an.

*iInsertAt*<br/>
[in] Gibt den nullbasierten Index auf der Seite der Outlook-Leiste an, auf der die Schaltfläche eingefügt werden soll.

*uiLabel*<br/>
[in] Eine Zeichenfolgenressourcen-ID.

*szBmpFileName*<br/>
[in] Gibt den Namen der zu ladenden Datenträgerabbilddatei an.

*szLabel*<br/>
[in] Gibt den Text der Schaltfläche an.

*hBmp*<br/>
[in] Ein Handle zur Bitmap einer Schaltfläche.

*hIcon*<br/>
[in] Ein Handle zum Symbol einer Schaltfläche.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn eine Schaltfläche erfolgreich hinzugefügt wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um eine neue Schaltfläche in die Seite einer Outlook-Leiste einzufügen. Das Abbild der Schaltfläche kann entweder aus den Anwendungsressourcen oder aus einer Datenträgerdatei geladen werden.

Wenn die von *uiPageID* angegebene Seiten-ID -1 ist, wird die Schaltfläche in die erste Seite eingefügt.

Wenn der von *iInsertAt* angegebene Index -1 ist, wird die Schaltfläche am Ende der Seite hinzugefügt.

## <a name="cmfcoutlookbarpanecanbeattached"></a><a name="canbeattached"></a>CMFCOutlookBarPane::CanBeAttached

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcoutlookbarpaneclearall"></a><a name="clearall"></a>CMFCOutlookBarPane::ClearAll

Gibt die Ressourcen frei, die von den Bildern im Outlook-Leistenbereich verwendet werden.

```cpp
void ClearAll();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft [DIREKT CMFCToolBarImages::Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear)auf, das für die Bilder aufgerufen wird, die vom Outlook-Leistenbereich verwendet werden.

## <a name="cmfcoutlookbarpanecreate"></a><a name="create"></a>CMFCOutlookBarPane::Erstellen

Erstellt den Outlook-Leistenbereich.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,
    UINT uiID=(UINT)-1,
    DWORD dwControlBarStyle=0);
```

### <a name="parameters"></a>Parameter

*pParentWnd*<br/>
[in] Gibt das übergeordnete Fenster des Outlook-Leistenbereichssteuerelements an. Darf nicht NULL sein.

*dwStyle*<br/>
[in] Der Fensterstil.  Eine Liste der Fensterstile finden Sie unter [Fensterformate](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*uiID*<br/>
[in] Die Steuerelement-ID. Muss eindeutig sein, um das Speichern des Steuerelementstatus zu ermöglichen.

*dwControlBarStyle*<br/>
[in] Gibt spezielle Formatvorlagen an, die das Verhalten des Outlook-Leistenbereichssteuerelements definieren, wenn es von der Outlook-Leiste getrennt wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich war; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Um ein `CMFCOutlookBarPane` Objekt zu erstellen, rufen Sie `Create`zuerst den Konstruktor auf, und rufen `CMFCOutlookBarPane` Sie dann auf, wodurch das Outlook-Leistenbereichssteuerelement erstellt und an das Objekt angefügt wird.

Weitere Informationen `dwControlBarStyle` finden Sie unter [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).

## <a name="cmfcoutlookbarpaneenablecontextmenuitems"></a><a name="enablecontextmenuitems"></a>CMFCOutlookBarPane::EnableContextMenuItems

Gibt an, welche Verknüpfungsmenüelemente im Anpassungsmodus angezeigt werden.

```
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,
    CMenu* pPopup);
```

### <a name="parameters"></a>Parameter

*pButton*<br/>
[in] Ein Zeiger auf eine Symbolleistenschaltfläche, auf die ein Benutzer geklickt hat.

*pPopup*<br/>
[in] Ein Zeiger auf das Kontextmenü.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das Kontextmenü angezeigt werden soll; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, um das Frameworkstandard-Shortcutmenü zu ändern, das das Framework im Anpassungsmodus anzeigt.

Die Standardimplementierung überprüft den Anpassungsmodus ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)) und wenn sie auf TRUE festgelegt ist, deaktiviert alle Kontextmenüelemente außer **Delete**. Dann werden einfach die Eingabeparameter an `CMFCToolBar::EnableContextMenuItems`übergibt.

> [!NOTE]
> *Kontextmenü* ist ein Synonym für Shortcut-Menü.

## <a name="cmfcoutlookbarpaneenablepagescrollmode"></a><a name="enablepagescrollmode"></a>CMFCOutlookBarPane::EnablePageScrollMode

Gibt an, ob die Bildlaufpfeile im Outlook-Leistenbereich die Liste der Schaltflächen Seite für Seite oder die Schaltfläche nach Derenkzeichen voranbringen.

```cpp
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```

### <a name="parameters"></a>Parameter

*bPageScroll*<br/>
[in] Wenn TRUE, aktivieren Sie den Seitenbildlaufmodus. Wenn FALSE, deaktivieren Sie den Seitenbildlaufmodus.

## <a name="cmfcoutlookbarpanegetregularcolor"></a><a name="getregularcolor"></a>CMFCOutlookBarPane::GetRegularColor

Gibt die reguläre (d. h. nicht ausgewählte) Textfarbe des Outlook-Leistenbereichs zurück.

```
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Textfarbe als RGB-Farbwert.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie [CMFCOutlookBarPane::SetTextColor,](#settextcolor) um die aktuelle (normale und ausgewählte) Textfarbe der Outlook-Leiste festzulegen. Sie können die Standardtextfarbe abrufen, indem Sie die [GetSysColor-Funktion](/windows/win32/api/winuser/nf-winuser-getsyscolor) mit dem COLOR_WINDOW Index aufrufen.

## <a name="cmfcoutlookbarpaneisbackgroundtexture"></a><a name="isbackgroundtexture"></a>CMFCOutlookBarPane::IsBackgroundTexture

Bestimmt, ob ein Hintergrundbild für den Outlook-Leistenbereich geladen ist.

```
BOOL IsBackgroundTexture() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn ein Hintergrundbild angezeigt werden soll; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Sie können ein Hintergrundbild hinzufügen, indem Sie die [CmFCOutlookBarPane::SetBackImage-Funktion](#setbackimage) aufrufen.

Wenn kein Hintergrundbild vorhanden ist, wird der Hintergrund mit einer Farbe gezeichnet, die mit [CMFCOutlookBarPane::SetBackColor](#setbackcolor)angegeben wird.

## <a name="cmfcoutlookbarpaneisdrawshadedhighlight"></a><a name="isdrawshadedhighlight"></a>CMFCOutlookBarPane::IsDrawShadedHighlight

Legt fest, ob der Schaltflächenrahmen schattiert ist, wenn eine Schaltfläche hervorgehoben und ein Hintergrundbild angezeigt wird.

```
BOOL IsDrawShadedHighlight() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Ränder der Schaltfläche schattiert sind; andernfalls FALSE.

## <a name="cmfcoutlookbarpaneremoveallbuttons"></a><a name="removeallbuttons"></a>CMFCOutlookBarPane::RemoveAllButtons

Entfernt alle Schaltflächen aus dem Outlook-Leistenbereich.

```
virtual void RemoveAllButtons();
```

## <a name="cmfcoutlookbarpaneremovebutton"></a><a name="removebutton"></a>CMFCOutlookBarPane::RemoveButton

Entfernt die Schaltfläche mit einer angegebenen Befehls-ID.

```
BOOL RemoveButton(UINT iIdCommand);
```

### <a name="parameters"></a>Parameter

*iIdCommand*<br/>
[in] Gibt die Befehls-ID einer zu entfernenden Schaltfläche an.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Schaltfläche erfolgreich entfernt wurde; FALSE, wenn die angegebene Befehls-ID ungültig ist.

## <a name="cmfcoutlookbarpanesetbackcolor"></a><a name="setbackcolor"></a>CMFCOutlookBarPane::SetBackColor

Legt die Hintergrundfarbe der Outlook-Leiste fest.

```cpp
void SetBackColor(COLORREF color);
```

### <a name="parameters"></a>Parameter

*Farbe*<br/>
[in] Gibt die neue Hintergrundfarbe an.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um die aktuelle Hintergrundfarbe für die Outlook-Leiste festzulegen. Die Hintergrundfarbe wird nur verwendet, wenn kein Hintergrundbild vorhanden ist.

## <a name="cmfcoutlookbarpanesetbackimage"></a><a name="setbackimage"></a>CMFCOutlookBarPane::SetBackImage

Legt das Hintergrundbild fest.

```cpp
void SetBackImage(UINT uiImageID);
```

### <a name="parameters"></a>Parameter

*uiImageID*<br/>
[in] Gibt die Bildressourcen-ID an.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um das Hintergrundbild der Outlook-Leiste festzulegen. Die Liste der Hintergrundbilder wird vom eingebetteten [CMFCToolBarImages-Klassenobjekt](../../mfc/reference/cmfctoolbarimages-class.md) verwaltet.

## <a name="cmfcoutlookbarpanesetdefaultstate"></a><a name="setdefaultstate"></a>CMFCOutlookBarPane::SetDefaultState

Setzt den Outlook-Leistenbereich auf den ursprünglichen Satz von Schaltflächen zurück.

```cpp
void SetDefaultState();
```

### <a name="remarks"></a>Bemerkungen

Mit dieser Methode werden die Outlook-Leiste-Schaltflächen auf den ursprünglichen Satz zurückgesetzt. Diese Methode `CMFCOutlookBarPane::RestoreOriginalstate`ist wie , außer dass sie keine Neuzeichnung des Outlook-Leistenbereichs auslöst.

## <a name="cmfcoutlookbarpanesetextraspace"></a><a name="setextraspace"></a>CMFCOutlookBarPane::SetExtraSpace

Legt die Anzahl der Pixel des Auffüllens fest, die um Schaltflächen im Outlook-Leistenbereich verwendet werden.

```cpp
void SetExtraSpace()
```

## <a name="cmfcoutlookbarpanesettextcolor"></a><a name="settextcolor"></a>CMFCOutlookBarPane::SetTextColor

Legt die Farben des regulären und hervorgehobenen Texts im Outlook-Leistenbereich fest.

```cpp
void SetTextColor(
    COLORREF clrRegText,
    COLORREF clrSelText=0);
```

### <a name="parameters"></a>Parameter

*clrRegText*<br/>
[in] Gibt die neue Farbe für nicht ausgewählten Text an.

*clrSelText*<br/>
[in] Gibt die neue Farbe für markierten Text an.

## <a name="cmfcoutlookbarpanesettransparentcolor"></a><a name="settransparentcolor"></a>CMFCOutlookBarPane::SetTransparentColor

Legt die transparente Farbe für den Outlook-Leistenbereich fest.

```cpp
void SetTransparentColor(COLORREF color);
```

### <a name="parameters"></a>Parameter

*Farbe*<br/>
Gibt die neue transparente Farbe an.

### <a name="remarks"></a>Bemerkungen

Die transparente Farbe ist erforderlich, um transparente Bilder anzuzeigen. Jedes Vorkommen dieser Farbe in einem Bild wird stattdessen mit der Hintergrundfarbe gezeichnet.  Es gibt keine Verschmelzung von Hintergrund- und Vordergrundbildern.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar-Klasse](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCOutlookBar-Klasse](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarTabCtrl-Klasse](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
