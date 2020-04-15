---
title: CMFCToolBarsCustomizeDialog-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillAllCommandsList
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillCategoriesComboBox
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillCategoriesListBox
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetCommandName
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetCountInCategory
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetFlags
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::OnInitDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::PostNcDestroy
helpviewer_keywords:
- CMFCToolBarsCustomizeDialog [MFC], CMFCToolBarsCustomizeDialog
- CMFCToolBarsCustomizeDialog [MFC], FillAllCommandsList
- CMFCToolBarsCustomizeDialog [MFC], FillCategoriesComboBox
- CMFCToolBarsCustomizeDialog [MFC], FillCategoriesListBox
- CMFCToolBarsCustomizeDialog [MFC], GetCommandName
- CMFCToolBarsCustomizeDialog [MFC], GetCountInCategory
- CMFCToolBarsCustomizeDialog [MFC], GetFlags
- CMFCToolBarsCustomizeDialog [MFC], OnInitDialog
- CMFCToolBarsCustomizeDialog [MFC], PostNcDestroy
ms.assetid: 78e2cddd-4f13-4097-afc3-1ad646a113f1
ms.openlocfilehash: d47ecf45a7bbfc563be0c05cd15ee84d430f502f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377364"
---
# <a name="cmfctoolbarscustomizedialog-class"></a>CMFCToolBarsCustomizeDialog-Klasse

Ein modusloses Registerkartendialogfeld ( [CPropertySheet-Klasse](../../mfc/reference/cpropertysheet-class.md)), das es dem Benutzer ermöglicht, die Symbolleisten, Menüs, Tastenkombinationen, benutzerdefinierte Werkzeuge und den visuellen Stil in einer Anwendung anzupassen. In der Regel greift der Benutzer durch Auswählen von **Anpassen** im Menü **Tools** auf dieses Dialogfeld zu.

Das Dialogfeld **Anpassen** hat sechs Registerkarten: **Befehle**, **Symbolleisten**, **Werkzeuge**, **Tastatur**, **Menü**und **Optionen**.

## <a name="syntax"></a>Syntax

```
class CMFCToolBarsCustomizeDialog : public CPropertySheet
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog](#cmfctoolbarscustomizedialog)|Erstellt ein `CMFCToolBarsCustomizeDialog`-Objekt.|
|`CMFCToolBarsCustomizeDialog::~CMFCToolBarsCustomizeDialog`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)|Fügt eine Symbolleistenschaltfläche in die Liste der Befehle auf der Seite **Befehle** ein|
|[CMFCToolBarsCustomizeDialog::AddMenu](#addmenu)|Lädt ein Menü aus den Ressourcen und ruft [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) auf, um dieses Menü der Liste der Befehle auf der Seite **Befehle** hinzuzufügen.|
|[CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)|Lädt ein Menü aus den Ressourcen und ruft [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) auf, um dieses Menü der Liste der Befehle auf der Seite **Befehle** hinzuzufügen.|
|[CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar)|Lädt eine Symbolleiste aus den Ressourcen. Dann ruft für jeden Befehl im Menü die [CMFCToolBarsCustomizeDialog::AddButton-Methode](#addbutton) auf, um eine Schaltfläche in die Liste der Befehle auf der Seite **Befehle** unter der angegebenen Kategorie einzufügen.|
|[CMFCToolBarsCustomizeDialog::Erstellen](#create)|Zeigt das Dialogfeld **Anpassung** an.|
|`CMFCToolBarsCustomizeDialog::EnableTools`|Für die zukünftige Verwendung reserviert.|
|[CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars](#enableuserdefinedtoolbars)|Aktiviert oder deaktiviert das Erstellen neuer Symbolleisten mithilfe des Dialogfelds **Anpassen.**|
|[CMFCToolBarsCustomizeDialog::FillAllCommandsList](#fillallcommandslist)|Füllt das bereitgestellte `CListBox` Objekt mit den Befehlen in der Kategorie **Alle Befehle.**|
|[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)|Füllt das bereitgestellte `CComboBox` Objekt mit dem Namen jeder Befehlskategorie im Dialogfeld **Anpassen.**|
|[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)|Füllt das bereitgestellte `CListBox` Objekt mit dem Namen jeder Befehlskategorie im Dialogfeld **Anpassen.**|
|[CMFCToolBarsCustomizeDialog::GetCommandName](#getcommandname)|Ruft den Namen ab, der der angegebenen Befehls-ID zugeordnet ist.|
|[CMFCToolBarsCustomizeDialog::GetCountInCategory](#getcountincategory)|Ruft die Anzahl der Elemente in der bereitgestellten Liste ab, die über eine bestimmte Textbeschriftung verfügen.|
|[CMFCToolBarsCustomizeDialog::GetFlags](#getflags)|Ruft den Satz von Flags ab, die sich auf das Verhalten des Dialogfelds auswirken.|
|`CMFCToolBarsCustomizeDialog::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|
|[CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage](#onedittoolbarmenuimage)|Startet einen Bildeditor, damit ein Benutzer eine Symbolleistenschaltfläche oder ein Menüelementsymbol anpassen kann.|
|[CMFCToolBarsCustomizeDialog::OnInitDialog](#oninitdialog)|Überschreibungen, um die Initialisierung von Eigenschaftenblättern zu erweitern. (Überschreibt [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|
|[CMFCToolBarsCustomizeDialog::PostNcDestroy](#postncdestroy)|Wird vom Framework aufgerufen, nachdem das Fenster zerstört wurde. (Überschreibt `CPropertySheet::PostNcDestroy`.)|
|[CMFCToolBarsCustomizeDialog::RemoveButton](#removebutton)|Entfernt die Schaltfläche mit der angegebenen Befehls-ID aus der angegebenen Kategorie oder aus allen Kategorien.|
|[CMFCToolBarsCustomizeDialog::UmbenennenKategorie](#renamecategory)|Benennt eine Kategorie im Listenfeld der Kategorien auf der Registerkarte **Befehle** um.|
|[CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton)|Ersetzt eine Schaltfläche in der Liste der Befehle auf der Registerkarte **Befehle** durch ein neues Symbolleisten-Schaltflächenobjekt.|
|[CMFCToolBarsCustomizeDialog::SetUserCategory](#setusercategory)|Fügt der Liste der Kategorien eine Kategorie hinzu, die auf der Registerkarte **Befehle** angezeigt wird.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog::CheckToolsGültigkeit](#checktoolsvalidity)|Wird vom Framework aufgerufen, um zu bestimmen, ob die Liste der benutzerdefinierten Tools gültig ist.|
|[CMFCToolBarsCustomizeDialog::OnAfterChangeTool](#onafterchangetool)|Wird vom Framework aufgerufen, wenn sich die Eigenschaften eines benutzerdefinierten Werkzeugs ändern.|
|[CMFCToolBarsCustomizeDialog::OnAssignKey](#onassignkey)|Bestimmt, ob einer Aktion eine angegebene Tastenkombination zugewiesen werden kann.|
|[CMFCToolbarsCustomizeDialog::OnBeforeChangeTool](#onbeforechangetool)|Bestimmt, ob ein benutzerdefiniertes Werkzeug geändert werden kann.|
|[CMFCToolBarsCustomizeDialog::OnInitToolsPage](#oninittoolspage)|Wird vom Framework aufgerufen, wenn der Benutzer die Registerkarte **Extras** auswählt, wird angefordert.|

## <a name="remarks"></a>Bemerkungen

Um das Dialogfeld **Anpassen** `CMFCToolBarsCustomizeDialog` anzuzeigen, erstellen Sie ein Objekt und rufen Sie die [CMFCToolBarsCustomizeDialog::Create-Methode](#create) auf.

Während das Dialogfeld **Anpassen** aktiv ist, arbeitet die Anwendung in einem speziellen Modus, der den Benutzer auf Anpassungsaufgaben beschränkt.

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung verschiedener Methoden in der `CMFCToolBarsCustomizeDialog` -Klasse. Das Beispiel zeigt, wie Sie eine Symbolleistenschaltfläche im Listenfeld der Befehle auf der Seite **Befehle** ersetzen, das Erstellen neuer Symbolleisten mithilfe des Dialogfelds **Anpassen** aktivieren und das Dialogfeld **Anpassung** anzeigen. Dieser Codeausschnitt ist Teil des [IE-Demobeispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

`CMFCToolBarsCustomizeDialog`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxToolBarsCustomizeDialog.h

## <a name="cmfctoolbarscustomizedialogaddbutton"></a><a name="addbutton"></a>CMFCToolBarsCustomizeDialog::AddButton

Fügt eine Symbolleistenschaltfläche in die Liste der Befehle auf der Seite **Befehle** ein.

```
void AddButton(
    UINT uiCategoryId,
    const CMFCToolBarButton& button,
    int iInsertBefore=-1);

void AddButton(
    LPCTSTR lpszCategory,
    const CMFCToolBarButton& button,
    int iInsertBefore=-1);
```

### <a name="parameters"></a>Parameter

*uiCategoryId*<br/>
[in] Gibt die Kategorie-ID an, in die die Schaltfläche eingefügt werden soll.

*Schaltfläche*<br/>
[in] Gibt die einzufügende Schaltfläche an.

*iInsertVor*<br/>
[in] Gibt den nullbasierten Index einer Symbolleistenschaltfläche an, vor der die Schaltfläche eingefügt wird.

*lpszKategorie*<br/>
[in] Gibt die Kategoriezeichenfolge an, um die Schaltfläche einzufügen.

### <a name="remarks"></a>Bemerkungen

Die `AddButton` Methode ignoriert Schaltflächen mit den Standardbefehls-IDs (z. B. ID_FILE_MRU_FILE1), Befehle, die nicht zulässig sind (siehe [CMFCToolBar::IsCommandPermitted](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted)) und Dummy-Schaltflächen.

Diese Methode erstellt ein neues Objekt `button` desselben Typs wie (normalerweise eine [CMFCToolBarButton-Klasse](../../mfc/reference/cmfctoolbarbutton-class.md)) mithilfe der Laufzeitklasse der Schaltfläche. Anschließend wird [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom) zum Kopieren der Datenmember der Schaltfläche aufruft und die Kopie in die angegebene Kategorie eingefügt.

Wenn die neue Schaltfläche eingefügt wird, erhält sie die `OnAddToCustomizePage` Benachrichtigung.

Wenn `iInsertBefore` -1 ist, wird die Schaltfläche an die Liste der Kategorien angehängt. Andernfalls wird es vor dem Element mit dem angegebenen Index eingefügt.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird `AddButton` veranschaulicht, `CMFCToolBarsCustomizeDialog` wie die Methode der Klasse verwendet wird. Dieser Codeausschnitt ist Teil des [Slider-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]

## <a name="cmfctoolbarscustomizedialogaddmenu"></a><a name="addmenu"></a>CMFCToolBarsCustomizeDialog::AddMenu

Lädt ein Menü aus den Ressourcen und ruft [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) auf, um dieses Menü der Liste der Befehle auf der Seite **Befehle** hinzuzufügen.

```
BOOL AddMenu(UINT uiMenuResId);
```

### <a name="parameters"></a>Parameter

*uiMenuResId*<br/>
[in] Gibt die Ressourcen-ID eines zu ladenden Menüs an.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn ein Menü erfolgreich hinzugefügt wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Im Aufruf `AddMenuCommands`von ist *bPopup* FALSE. Daher fügt diese Methode der Liste der Befehle keine Menüelemente hinzu, die Untermenüs enthalten. Diese Methode fügt die Menüelemente in den Untermenüs zur Liste der Befehle hinzu.

## <a name="cmfctoolbarscustomizedialogaddmenucommands"></a><a name="addmenucommands"></a>CMFCToolBarsCustomizeDialog::AddMenuCommands

Fügt elemente zur Liste der Befehle auf der Seite **Befehle** hinzu, um alle Elemente im angegebenen Menü darzustellen.

```
void AddMenuCommands(
    const CMenu* pMenu,
    BOOL bPopup,
    LPCTSTR lpszCategory=NULL,
    LPCTSTR lpszMenuPath=NULL);
```

### <a name="parameters"></a>Parameter

*pMenu*<br/>
[in] Ein Zeiger auf das hinzuzufügende CMenu-Objekt.

*bPopup*<br/>
[in] Gibt an, ob die Popupmenüelemente in die Liste der Befehle eingefügt werden sollen.

*lpszKategorie*<br/>
[in] Der Name der Kategorie, die das Menü einfügen soll.

*lpszMenuPath*<br/>
[in] Ein Präfix, das dem Namen hinzugefügt wird, wenn der Befehl in der Liste **Alle Kategorien** angezeigt wird.

### <a name="remarks"></a>Bemerkungen

Die `AddMenuCommands` Methode überläuft alle Menüelemente von *pMenu*. Für jedes Menüelement, das kein Untermenü enthält, erstellt diese Methode ein [CMFCToolBarButton-Klassenobjekt](../../mfc/reference/cmfctoolbarbutton-class.md) und ruft die [CMFCToolBarsCustomizeDialog::AddButton-Methode](#addbutton) auf, um das Menüelement als Symbolleistenschaltfläche zur Liste der Befehle auf der Seite **Befehle** hinzuzufügen. Separatoren werden dabei ignoriert.

Wenn *bPopup* TRUE ist, erstellt diese Methode für jedes Menüelement, das ein Untermenü enthält, ein [CMFCToolBarMenuButton-Klassenobjekt](../../mfc/reference/cmfctoolbarmenubutton-class.md) und fügt es in die Liste der Befehle ein, indem sie aufruft. `AddButton` Andernfalls werden Menüelemente, die Untermenüs enthalten, nicht in der Liste der Befehle angezeigt. In beiden Fällen `AddMenuCommands` ruft es sich rekursiv auf ein Menüelement mit einem Untermenü auf, indem er einen Zeiger als *pMenu-Parameter* an das Untermenü übergibt und die Bezeichnung des Untermenüs an *lpszMenuPath*anfügt.

## <a name="cmfctoolbarscustomizedialogaddtoolbar"></a><a name="addtoolbar"></a>CMFCToolBarsCustomizeDialog::AddToolBar

Lädt eine Symbolleiste aus den Ressourcen. Dann ruft für jeden Befehl im Menü die [CMFCToolBarsCustomizeDialog::AddButton-Methode](#addbutton) auf, um eine Schaltfläche in die Liste der Befehle auf der Seite **Befehle** unter der angegebenen Kategorie einzufügen.

```
BOOL AddToolBar(
    UINT uiCategoryId,
    UINT uiToolbarResId);

BOOL AddToolBar(
    LPCTSTR lpszCategory,
    UINT uiToolbarResId);
```

### <a name="parameters"></a>Parameter

*uiCategoryId*<br/>
[in] Gibt die Ressourcen-ID der Kategorie an, der die Symbolleiste hinzugefügt werden soll.

*uiToolbarResId*<br/>
[in] Gibt die Ressourcen-ID einer Symbolleiste an, deren Befehle in die Liste der Befehle eingefügt werden.

*lpszKategorie*<br/>
[in] Gibt den Namen der Kategorie an, der die Symbolleiste hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich ist; andernfalls FALSE.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird `AddToolBar` veranschaulicht, `CMFCToolBarsCustomizeDialog` wie die Methode in der Klasse verwendet wird. Dieser Codeausschnitt ist Teil des [WordPad-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]

### <a name="remarks"></a>Bemerkungen

Das Steuerelement, das verwendet wird, um jeden Befehl darzustellen, ist ein [CMFCToolBarButton-Klassenobjekt.](../../mfc/reference/cmfctoolbarbutton-class.md) Nachdem Sie die Symbolleiste hinzugefügt haben, können Sie die Schaltfläche durch ein Steuerelement eines abgeleiteten Typs ersetzen, indem Sie [CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton)aufrufen.

## <a name="cmfctoolbarscustomizedialogchecktoolsvalidity"></a><a name="checktoolsvalidity"></a>CMFCToolBarsCustomizeDialog::CheckToolsGültigkeit

Überprüft die Gültigkeit der Liste der Benutzertools.

```
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```

### <a name="parameters"></a>Parameter

*lstTools*<br/>
[in] Die Liste der benutzerdefinierten Tools, die überprüft werden sollen.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn die Liste der benutzerdefinierten Tools gültig ist; andernfalls FALSE. Die Standardimplementierung gibt immer TRUE zurück.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Methode auf, um die Gültigkeit von Objekten zu überprüfen, die benutzerdefinierte Tools darstellen, die von [CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity)zurückgegeben werden.

Überschreiben `CheckToolsValidity` Sie die Methode `CMFCToolBarsCustomizeDialog` in einer Klasse, die von der Überprüfung der Benutzertools abgeleitet wurde, bevor der Benutzer das Dialogfeld schließt. Wenn diese Methode FALSE zurückgibt, wenn der Benutzer entweder auf die Schaltfläche **Schließen** in der oberen rechten Ecke des Dialogfelds oder auf die Schaltfläche **Schließen** in der unteren rechten Ecke des Dialogfelds klickt, wird im Dialogfeld die Registerkarte **Extras** anstelle des Schließens angezeigt. Wenn diese Methode FALSE zurückgibt, wenn der Benutzer auf eine Registerkarte klickt, um von der Registerkarte **Extras** weg zu navigieren, wird die Navigation nicht ausgeführt. Sie sollten ein geeignetes Meldungsfeld anzeigen, um den Benutzer über das Problem zu informieren, das zum Fehlschlagen der Validierung geführt hat.

## <a name="cmfctoolbarscustomizedialogcmfctoolbarscustomizedialog"></a><a name="cmfctoolbarscustomizedialog"></a>CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog

Erstellt ein `CMFCToolBarsCustomizeDialog`-Objekt.

```
CMFCToolBarsCustomizeDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bAutoSetFromMenus = FALSE,
    UINT uiFlags = (AFX_CUSTOMIZE_MENU_SHADOWS | AFX_CUSTOMIZE_TEXT_LABELS | AFX_CUSTOMIZE_MENU_ANIMATIONS | AFX_CUSTOMIZE_NOHELP),
    CList <CRuntimeClass*, CRuntimeClass*>* p listCustomPages = NULL);
```

### <a name="parameters"></a>Parameter

*pWndParentFrame*<br/>
[in] Ein Zeiger auf den übergeordneten Rahmen. Dieser Parameter darf nicht NULL sein.

*bAutoSetFromMenus*<br/>
[in] Ein boolescher Wert, der angibt, ob die Menübefehle aus allen Menüs zur Liste der Befehle auf der Seite **Befehle** hinzugefügt werden sollen. Wenn dieser Parameter TRUE ist, werden die Menübefehle hinzugefügt. Andernfalls werden die Menübefehle nicht hinzugefügt.

*uiFlags*<br/>
[in] Eine Kombination von Flags, die sich auf das Verhalten des Dialogfelds auswirken. Dieser Parameter kann einer oder mehrere der folgenden Werte sein:

- AFX_CUSTOMIZE_MENU_SHADOWS

- AFX_CUSTOMIZE_TEXT_LABELS

- AFX_CUSTOMIZE_MENU_ANIMATIONS

- AFX_CUSTOMIZE_NOHELP

- AFX_CUSTOMIZE_CONTEXT_HELP

- AFX_CUSTOMIZE_NOTOOLS

- AFX_CUSTOMIZE_MENUAMPERS

- AFX_CUSTOMIZE_NO_LARGE_ICONS

*plistCustomPages*<br/>
[in] Ein Zeiger auf eine `CRuntimeClass` Liste von Objekten, die zusätzliche benutzerdefinierte Seiten angeben.

### <a name="remarks"></a>Bemerkungen

Der Parameter *plistCustomPages* bezieht `CRuntimeClass` sich auf die Liste der Objekte, die zusätzliche benutzerdefinierte Seiten angeben. Der Konstruktor fügt dem Dialogfeld mithilfe der [CRuntimeClass::CreateObject-Methode](../../mfc/reference/cruntimeclass-structure.md#createobject) weitere Seiten hinzu. Im CustomPages-Beispiel finden Sie ein Beispiel, das dem Dialogfeld **Anpassen** weitere Seiten hinzufügt.

Weitere Informationen zu den Werten, die Sie im *UiFlags-Parameter* übergeben können, finden Sie unter [CMFCToolBarsCustomizeDialog::GetFlags](#getflags).

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCToolBarsCustomizeDialog` wie ein Objekt der Klasse erstellt wird. Dieser Codeausschnitt ist Teil des [Beispiels für benutzerdefinierte Seiten](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]

## <a name="cmfctoolbarscustomizedialogcreate"></a><a name="create"></a>CMFCToolBarsCustomizeDialog::Erstellen

Zeigt das Dialogfeld **Anpassung** an.

```
virtual BOOL Create();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Anpassungseigenschaftenblatt erfolgreich erstellt wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Rufen `Create` Sie die Methode erst auf, nachdem Sie die Klasse vollständig initialisiert haben.

## <a name="cmfctoolbarscustomizedialogenableuserdefinedtoolbars"></a><a name="enableuserdefinedtoolbars"></a>CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars

Aktiviert oder deaktiviert das Erstellen neuer Symbolleisten mithilfe des Dialogfelds **Anpassen.**

```
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
[in] TRUE, um die benutzerdefinierten Symbolleisten zu aktivieren; FALSE, um die Symbolleisten zu deaktivieren.

### <a name="remarks"></a>Bemerkungen

Wenn *bEnable* TRUE ist, werden die Schaltflächen **Neu**, **Umbenennen** und **Löschen** auf der Seite **Symbolleisten** angezeigt.

Standardmäßig oder wenn *bEnable* FALSE ist, werden diese Schaltflächen nicht angezeigt, und der Benutzer kann keine neuen Symbolleisten definieren.

## <a name="cmfctoolbarscustomizedialogfillallcommandslist"></a><a name="fillallcommandslist"></a>CMFCToolBarsCustomizeDialog::FillAllCommandsList

Füllt das bereitgestellte `CListBox` Objekt mit den Befehlen in der Kategorie **Alle Befehle.**

```
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;
```

### <a name="parameters"></a>Parameter

*wndListOfCommands*<br/>
[out] Ein Verweis `CListBox` auf das zu füllende Objekt.

### <a name="remarks"></a>Bemerkungen

Die Kategorie **Alle Befehle** enthält die Befehle aller Kategorien. Die [CMFCToolBarsCustomizeDialog::AddButton-Methode](#addbutton) fügt den Befehl, der der bereitgestellten Schaltfläche zugeordnet ist, der Kategorie **Alle Befehle** hinzu.

Diese Methode löscht den Inhalt `CListBox` des bereitgestellten Objekts, bevor es mit den Befehlen in der Kategorie **Alle Befehle** aufgepopt wird.

Die `CMFCMousePropertyPage` Klasse verwendet diese Methode, um das Listenfeld für Doppelklickereignisse aufzufüllen.

## <a name="cmfctoolbarscustomizedialogfillcategoriescombobox"></a><a name="fillcategoriescombobox"></a>CMFCToolBarsCustomizeDialog::FillCategoriesComboBox

Füllt das bereitgestellte `CComboBox` Objekt mit dem Namen jeder Befehlskategorie im Dialogfeld **Anpassen.**

```
void FillCategoriesComboBox(
    CComboBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>Parameter

*wndKategorie*<br/>
[out] Ein Verweis `CComboBox` auf das zu füllende Objekt.

*bAddEmpty*<br/>
[in] Ein boolescher Wert, der angibt, ob dem Kombinationsfeld Kategorien hinzugefügt werden sollen, die keine Befehle haben. Wenn dieser Parameter TRUE ist, werden leere Kategorien zum Kombinationsfeld hinzugefügt. Andernfalls werden keine leeren Kategorien hinzugefügt.

### <a name="remarks"></a>Bemerkungen

Diese Methode ähnelt der [CMFCToolBarsCustomizeDialog::FillCategoriesListBox-Methode,](#fillcategorieslistbox) außer `CComboBox` dass diese Methode mit einem Objekt funktioniert.

Diese Methode löscht den Inhalt `CComboBox` des Objekts nicht, bevor es aufgepopt wird. Es garantiert, dass die Kategorie **Alle Befehle** das letzte Element im Kombinationsfeld ist.

Sie können neue Befehlskategorien hinzufügen, indem Sie die [CMFCToolBarsCustomizeDialog::AddButton-Methode](#addbutton) verwenden. Sie können den Namen einer vorhandenen Kategorie ändern, indem Sie die [CMFCToolBarsCustomizeDialog::RenameCategory-Methode](#renamecategory) verwenden.

Die `CMFCToolBarsKeyboardPropertyPage` `CMFCKeyMapDialog` und-Klassen verwenden diese Methode, um Tastaturzuordnungen zu kategorisieren.

## <a name="cmfctoolbarscustomizedialogfillcategorieslistbox"></a><a name="fillcategorieslistbox"></a>CMFCToolBarsCustomizeDialog::FillCategoriesListBox

Füllt das bereitgestellte `CListBox` Objekt mit dem Namen jeder Befehlskategorie im Dialogfeld **Anpassen.**

```
void FillCategoriesListBox(
    CListBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>Parameter

*wndKategorie*<br/>
[out] Ein Verweis `CListBox` auf das zu füllende Objekt.

*bAddEmpty*<br/>
[in] Ein boolescher Wert, der angibt, ob dem Listenfeld Kategorien hinzugefügt werden sollen, die keine Befehle haben. Wenn dieser Parameter TRUE ist, werden leere Kategorien zum Listenfeld hinzugefügt. Andernfalls werden keine leeren Kategorien hinzugefügt.

### <a name="remarks"></a>Bemerkungen

Diese Methode ähnelt der [CMFCToolBarsCustomizeDialog::FillCategoriesComboBox-Methode,](#fillcategoriescombobox) außer `CListBox` dass diese Methode mit einem Objekt funktioniert.

Diese Methode löscht den Inhalt `CListBox` des Objekts nicht, bevor es aufgepopt wird. Es wird sichergestellt, dass die Kategorie **Alle Befehle** das letzte Element im Listenfeld ist.

Sie können neue Befehlskategorien hinzufügen, indem Sie die [CMFCToolBarsCustomizeDialog::AddButton-Methode](#addbutton) verwenden. Sie können den Namen einer vorhandenen Kategorie ändern, indem Sie die [CMFCToolBarsCustomizeDialog::RenameCategory-Methode](#renamecategory) verwenden.

Die `CMFCToolBarsCommandsPropertyPage` Klasse verwendet diese Methode, um die Liste der Befehle anzuzeigen, die jeder Befehlskategorie zugeordnet sind.

## <a name="cmfctoolbarscustomizedialoggetcommandname"></a><a name="getcommandname"></a>CMFCToolBarsCustomizeDialog::GetCommandName

Ruft den Namen ab, der der angegebenen Befehls-ID zugeordnet ist.

```
LPCTSTR GetCommandName(UINT uiCmd) const;
```

### <a name="parameters"></a>Parameter

*uiCmd*<br/>
[in] Die ID des abzurufenden Befehls.

### <a name="return-value"></a>Rückgabewert

Der Name, der der angegebenen Befehls-ID zugeordnet ist, oder NULL, wenn der Befehl nicht vorhanden ist.

## <a name="cmfctoolbarscustomizedialoggetcountincategory"></a><a name="getcountincategory"></a>CMFCToolBarsCustomizeDialog::GetCountInCategory

Ruft die Anzahl der Elemente in der bereitgestellten Liste ab, die über eine bestimmte Textbeschriftung verfügen.

```
int GetCountInCategory(
    LPCTSTR lpszItemName,
    const CObList& lstCommands) const;
```

### <a name="parameters"></a>Parameter

*lpszItemName*<br/>
[in] Die zu übereinstimmende Textbeschriftung.

*lstCommands*<br/>
[in] Ein Verweis auf eine `CMFCToolBarButton` Liste, die Objekte enthält.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente in der bereitgestellten Liste, deren Textbeschriftung *lpszItemName*entspricht.

### <a name="remarks"></a>Bemerkungen

Jedes Element in der bereitgestellten `CMFCToolBarButton`Objektliste muss vom Typ sein. Diese Methode vergleicht *lpszItemName* mit dem [Datenmember CMFCToolBarButton::m_strText.](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)

## <a name="cmfctoolbarscustomizedialoggetflags"></a><a name="getflags"></a>CMFCToolBarsCustomizeDialog::GetFlags

Ruft den Satz von Flags ab, die sich auf das Verhalten des Dialogfelds auswirken.

```
UINT GetFlags() const;
```

### <a name="return-value"></a>Rückgabewert

Der Satz von Flags, die sich auf das Verhalten des Dialogfelds auswirken.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft den Wert des *uiFlags-Parameters* ab, der an den Konstruktor übergeben wird. Der Rückgabewert kann einer oder mehrere der folgenden Werte sein:

|||
|-|-|
|AFX_CUSTOMIZE_MENU_SHADOWS|Ermöglicht es dem Benutzer, die Schattendarstellung des Menüs anzugeben.  |
|AFX_CUSTOMIZE_TEXT_LABELS|Ermöglicht es dem Benutzer anzugeben, ob Textbeschriftungen unter den Symbolleistensymbolbildern angezeigt werden.  |
|AFX_CUSTOMIZE_MENU_ANIMATIONS|Ermöglicht es dem Benutzer, den Menüanimationsstil anzugeben.  |
|AFX_CUSTOMIZE_NOHELP|Entfernt die Hilfeschaltfläche aus dem Anpassungsdialogfeld.  |
|AFX_CUSTOMIZE_CONTEXT_HELP|Aktiviert den WS_EX_CONTEXTHELP visuellen Stil.  |
|AFX_CUSTOMIZE_NOTOOLS|Entfernt die Seite **Extras** aus dem Anpassungsdialogfeld. Dieses Flag ist gültig, `CUserToolsManager` wenn Ihre Anwendung die Klasse verwendet.  |
|AFX_CUSTOMIZE_MENUAMPERS|Ermöglicht, dass Schaltflächenbeschriftungen das **&** Zeichen "das geprosandsandsandsandsands) enthalten.  |
|AFX_CUSTOMIZE_NO_LARGE_ICONS|Entfernt die Option **Große Symbole** aus dem Anpassungsdialogfeld.  |

Weitere Informationen zum visuellen Stil WS_EX_CONTEXTHELP finden Sie unter [Erweiterte Fensterstile](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).

## <a name="cmfctoolbarscustomizedialogonafterchangetool"></a><a name="onafterchangetool"></a>CMFCToolBarsCustomizeDialog::OnAfterChangeTool

Reagiert unmittelbar nach dem Auftreten auf eine Änderung in einem Benutzertool.

```
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>Parameter

*pSelTool*<br/>
[in, out] Ein Zeiger auf das benutzerweite Werkzeugobjekt, das geändert wurde.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird vom Framework aufgerufen, wenn ein Benutzer die Eigenschaften eines benutzerdefinierten Tools ändert. Bei der Standardimplementierung wird keine Aktion ausgeführt. Überschreiben Sie diese Methode `CMFCToolBarsCustomizeDialog` in einer Klasse, die von der Verarbeitung abgeleitet wurde, nachdem eine Änderung an einem Benutzertool erfolgt ist.

## <a name="cmfctoolbarscustomizedialogonassignkey"></a><a name="onassignkey"></a>CMFCToolBarsCustomizeDialog::OnAssignKey

Überprüft Tastenkombinationen, während ein Benutzer sie definiert.

```
virtual BOOL OnAssignKey(ACCEL* pAccel);
```

### <a name="parameters"></a>Parameter

*pAccel*<br/>
[in, out] Zeiger auf die vorgeschlagene Tastatur-Assigment, die als [ACCEL-Struktur](/windows/win32/api/winuser/ns-winuser-accel) ausgedrückt wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Schlüssel zugewiesen werden kann, oder FALSE, wenn der Schlüssel nicht zugewiesen werden kann. Die Standardimplementierung gibt immer TRUE zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um eine zusätzliche Verarbeitung durchzuführen, wenn ein Benutzer eine neue Tastenkombination zuweist, oder um Tastenkombinationen zu überprüfen, während der Benutzer sie definiert. Um zu verhindern, dass eine Verknüpfung zugewiesen wird, geben Sie FALSE zurück. Sie sollten auch ein Meldungsfeld anzeigen oder den Benutzer anderweitig über den Grund informieren, warum die Tastenkombination abgelehnt wurde.

## <a name="cmfctoolbarscustomizedialogonbeforechangetool"></a><a name="onbeforechangetool"></a>CMFCToolbarsCustomizeDialog::OnBeforeChangeTool

Führt eine benutzerdefinierte Verarbeitung aus, wenn eine Änderung an einem Benutzertool auftritt, wenn der Benutzer eine Änderung anwenden möchte.

```
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>Parameter

*pSelTool*<br/>
[in, out] Ein Zeiger auf das Benutzerwerkzeugobjekt, das gerade ersetzt werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird vom Framework aufgerufen, wenn sich die Eigenschaften eines benutzerdefinierten Werkzeugs ändern werden. Bei der Standardimplementierung wird keine Aktion ausgeführt. Überschreiben `OnBeforeChangeTool` Sie die Methode `CMFCToolBarsCustomizeDialog` in einer Klasse, die von der Verarbeitung abgeleitet ist, bevor eine Änderung an einem Benutzertool erfolgt, z. B. das Freigeben von Ressourcen, die *pSelTool* verwendet.

## <a name="cmfctoolbarscustomizedialogonedittoolbarmenuimage"></a><a name="onedittoolbarmenuimage"></a>CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage

Startet einen Bildeditor, damit ein Benutzer eine Symbolleistenschaltfläche oder ein Menüelementsymbol anpassen kann.

```
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,
    CBitmap& bitmap,
    int nBitsPerPixel);
```

### <a name="parameters"></a>Parameter

*pWndParent*<br/>
[in] Ein Zeiger auf das übergeordnete Fenster.

*Bitmap*<br/>
[in] Ein Verweis auf ein zu bearbeitendes Bitmapobjekt.

*nBitsPerPixel*<br/>
[in] Bitmap-Farbauflösung in Bits pro Pixel.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn eine Änderung festgeschrieben wird; andernfalls FALSE. Die Standardimplementierung zeigt ein Dialogfeld an und gibt TRUE zurück, wenn der Benutzer auf **OK**oder FALSE klickt, wenn der Benutzer auf **Abbrechen** oder die Schaltfläche **Schließen** klickt.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird vom Framework aufgerufen, wenn der Benutzer den Bildeditor ausführt. Die Standardimplementierung zeigt das Dialogfeld [CMFCImageEditorDialog-Klassen](../../mfc/reference/cmfcimageeditordialog-class.md) an. Überschreiben `OnEditToolbarMenuImage` Sie in einer abgeleiteten Klasse, um einen benutzerdefinierten Bildeditor zu verwenden.

## <a name="cmfctoolbarscustomizedialogoninitdialog"></a><a name="oninitdialog"></a>CMFCToolBarsCustomizeDialog::OnInitDialog

Überschreibungen, um die Initialisierung von Eigenschaftenblättern zu erweitern.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Rückgabewert

Das Ergebnis des Aufrufens der [CPropertySheet::OnInitDialog-Methode.](../../mfc/reference/cpropertysheet-class.md#oninitdialog)

### <a name="remarks"></a>Bemerkungen

Diese Methode erweitert die Basisklassenimplementierung [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog), indem die Schaltfläche **Schließen** angezeigt wird, indem sichergestellt wird, dass das Dialogfeld an die aktuelle Bildschirmgröße anpasst, und indem die **Hilfeschaltfläche** in die linke untere Ecke des Dialogfelds bewegt wird.

## <a name="cmfctoolbarscustomizedialogoninittoolspage"></a><a name="oninittoolspage"></a>CMFCToolBarsCustomizeDialog::OnInitToolsPage

Behandelt die Benachrichtigung aus dem Framework, dass die **Seite Tools** kurz vor der Initialisierung steht.

```
virtual void OnInitToolsPage();
```

### <a name="remarks"></a>Bemerkungen

Bei der Standardimplementierung wird keine Aktion ausgeführt. Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um diese Benachrichtigung zu verarbeiten.

## <a name="cmfctoolbarscustomizedialogpostncdestroy"></a><a name="postncdestroy"></a>CMFCToolBarsCustomizeDialog::PostNcDestroy

Wird vom Framework aufgerufen, nachdem das Fenster zerstört wurde.

```
virtual void PostNcDestroy();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode erweitert die Basisklassenimplementierung , `CPropertySheet::PostNcDestroy`indem die Anwendung im vorherigen Modus wiederhergestellt wird.

Die [CMFCToolBarsCustomizeDialog::Create-Methode](#create) versetzt die Anwendung in einen speziellen Modus, der den Benutzer auf Anpassungsaufgaben beschränkt.

## <a name="cmfctoolbarscustomizedialogremovebutton"></a><a name="removebutton"></a>CMFCToolBarsCustomizeDialog::RemoveButton

Entfernt die Schaltfläche mit der angegebenen Befehls-ID aus der angegebenen Kategorie oder aus allen Kategorien.

```
int RemoveButton(
    UINT uiCategoryId,
    UINT uiCmdId);

int RemoveButton(
    LPCTSTR lpszCategory,
    UINT uiCmdId);
```

### <a name="parameters"></a>Parameter

*uiCategoryId*<br/>
[in] Gibt die Kategorie-ID an, aus der die Schaltfläche entfernt werden soll.

*uiCmdId*<br/>
[in] Gibt die Befehls-ID der Schaltfläche an.

*lpszKategorie*<br/>
[in] Gibt den Namen der Kategorie an, aus der die Schaltfläche entfernt werden soll.

### <a name="return-value"></a>Rückgabewert

Der nullbasierte Index der entfernten Schaltfläche oder -1, wenn die angegebene Befehls-ID in der angegebenen Kategorie nicht gefunden wurde. Wenn *uiCategoryId* -1 ist, ist der Rückgabewert 0.

### <a name="remarks"></a>Bemerkungen

Um eine Schaltfläche aus allen Kategorien zu entfernen, rufen Sie die erste Überladung dieser Methode auf und legen Sie *uiCategoryId* auf -1 fest.

## <a name="cmfctoolbarscustomizedialogrenamecategory"></a><a name="renamecategory"></a>CMFCToolBarsCustomizeDialog::UmbenennenKategorie

Benennt eine Kategorie im Listenfeld der Kategorien auf der Seite **Befehle** um.

```
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,
    LPCTSTR lpszCategoryNew);
```

### <a name="parameters"></a>Parameter

*lpszKategorieAlt*<br/>
[in] Der zu ändernde Kategoriename.

*lpszKategorieNeu*<br/>
[in] Der neue Kategoriename.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich war; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Der Kategoriename muss eindeutig sein.

## <a name="cmfctoolbarscustomizedialogreplacebutton"></a><a name="replacebutton"></a>CMFCToolBarsCustomizeDialog::ReplaceButton

Ersetzt eine Symbolleistenschaltfläche im Listenfeld der Befehle auf der Seite **Befehle.**

```
void ReplaceButton(
    UINT uiCmd,
    const CMFCToolBarButton& button);
```

### <a name="parameters"></a>Parameter

*uiCmd*<br/>
[in] Gibt den Befehl der zu ersetzenden Schaltfläche an.

*Schaltfläche*<br/>
[in] Ein **const-Verweis** auf das Symbolleisten-Schaltflächenobjekt, das die alte Schaltfläche ersetzt.

### <a name="remarks"></a>Bemerkungen

Wenn [CMFCToolBarsCustomizeDialog::AddMenu](#addmenu), [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)oder [CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar) einen Befehl zur **Befehlsseite** hinzufügt, ist dieser Befehl in Form eines [CMFCToolBarButton-Klassenobjekts](../../mfc/reference/cmfctoolbarbutton-class.md) (oder eines `AddMenuCommands` [CMFCToolBarMenuButton-Klassenobjekts](../../mfc/reference/cmfctoolbarmenubutton-class.md) für ein Menüelement, das ein von hinzugefügtes Untermenü enthält). Das Framework ruft auch diese drei Methoden auf, um Befehle automatisch hinzuzufügen. Wenn ein Befehl stattdessen durch einen abgeleiteten `ReplaceButton` Typ dargestellt werden soll, rufen Sie eine Schaltfläche des abgeleiteten Typs auf und übergeben Sie sie.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird `ReplaceButton` veranschaulicht, `CMFCToolBarsCustomizeDialog` wie die Methode in der Klasse verwendet wird. Dieser Codeausschnitt ist Teil des [Visual Studio Demo-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]

## <a name="cmfctoolbarscustomizedialogsetusercategory"></a><a name="setusercategory"></a>CMFCToolBarsCustomizeDialog::SetUserCategory

Gibt an, welche Kategorie in der Liste der Kategorien auf der Seite **Befehle** die Benutzerkategorie ist. Sie müssen diese Funktion aufrufen, bevor Sie [CMFCToolBarsCustomizeDialog::Create](#create)aufrufen.

```
BOOL SetUserCategory(LPCTSTR lpszCategory);
```

### <a name="parameters"></a>Parameter

*lpszKategorie*<br/>
[in] Der Name der Kategorie.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Die Benutzerkategorieeinstellung wird derzeit nicht vom Framework verwendet.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CPropertySheet-Klasse](../../mfc/reference/cpropertysheet-class.md)
