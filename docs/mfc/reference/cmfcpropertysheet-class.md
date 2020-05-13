---
title: CMFCPropertySheet-Klasse
ms.date: 11/19/2018
f1_keywords:
- CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet::CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet::AddPage
- AFXPROPERTYSHEET/CMFCPropertySheet::AddPageToTree
- AFXPROPERTYSHEET/CMFCPropertySheet::AddTreeCategory
- AFXPROPERTYSHEET/CMFCPropertySheet::EnablePageHeader
- AFXPROPERTYSHEET/CMFCPropertySheet::GetHeaderHeight
- AFXPROPERTYSHEET/CMFCPropertySheet::GetLook
- AFXPROPERTYSHEET/CMFCPropertySheet::GetNavBarWidth
- AFXPROPERTYSHEET/CMFCPropertySheet::GetTab
- AFXPROPERTYSHEET/CMFCPropertySheet::InitNavigationControl
- AFXPROPERTYSHEET/CMFCPropertySheet::OnActivatePage
- AFXPROPERTYSHEET/CMFCPropertySheet::OnDrawPageHeader
- AFXPROPERTYSHEET/CMFCPropertySheet::OnRemoveTreePage
- AFXPROPERTYSHEET/CMFCPropertySheet::RemoveCategory
- AFXPROPERTYSHEET/CMFCPropertySheet::RemovePage
- AFXPROPERTYSHEET/CMFCPropertySheet::SetIconsList
- AFXPROPERTYSHEET/CMFCPropertySheet::SetLook
helpviewer_keywords:
- CMFCPropertySheet [MFC], CMFCPropertySheet
- CMFCPropertySheet [MFC], AddPage
- CMFCPropertySheet [MFC], AddPageToTree
- CMFCPropertySheet [MFC], AddTreeCategory
- CMFCPropertySheet [MFC], EnablePageHeader
- CMFCPropertySheet [MFC], GetHeaderHeight
- CMFCPropertySheet [MFC], GetLook
- CMFCPropertySheet [MFC], GetNavBarWidth
- CMFCPropertySheet [MFC], GetTab
- CMFCPropertySheet [MFC], InitNavigationControl
- CMFCPropertySheet [MFC], OnActivatePage
- CMFCPropertySheet [MFC], OnDrawPageHeader
- CMFCPropertySheet [MFC], OnRemoveTreePage
- CMFCPropertySheet [MFC], RemoveCategory
- CMFCPropertySheet [MFC], RemovePage
- CMFCPropertySheet [MFC], SetIconsList
- CMFCPropertySheet [MFC], SetLook
ms.assetid: 01d93573-9698-440f-a6a4-5bebbee879dc
ms.openlocfilehash: 9b1bb2ce9a957b9cd9f7add983b4da7a228d7a1d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750062"
---
# <a name="cmfcpropertysheet-class"></a>CMFCPropertySheet-Klasse

Die Klasse `CMFCPropertySheet` unterstützt ein Eigenschaftenblatt, in dem jede Eigenschaftenseite durch eine Seitenregisterkarte, eine Symbolleisten-Schaltfläche, einen Strukturansichtsknoten oder ein Listenelement angegeben wird.

## <a name="syntax"></a>Syntax

```
class CMFCPropertySheet : public CPropertySheet
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCPropertySheet::CMFCPropertySheet](#cmfcpropertysheet)|Erstellt ein `CMFCPropertySheet`-Objekt.|
|`CMFCPropertySheet::~CMFCPropertySheet`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCPropertySheet::AddPage](#addpage)|Fügt dem Eigenschaftsblatt eine Seite hinzu.|
|[CMFCPropertySheet::AddPageToTree](#addpagetotree)|Fügt dem Struktursteuerelement eine neue Eigenschaftsseite hinzu.|
|[CMFCPropertySheet::AddTreeCategory](#addtreecategory)|Fügt dem Struktursteuerelement einen neuen Knoten hinzu.|
|[CMFCPropertySheet::EnablePageHeader](#enablepageheader)|Reserviert oben auf jeder Seite Platz, um einen benutzerdefinierten Header zu zeichnen.|
|[CMFCPropertySheet::GetHeaderHeight](#getheaderheight)|Ruft die Höhe des aktuellen Headers ab.|
|[CMFCPropertySheet::GetLook](#getlook)|Ruft einen Enumerationswert ab, der das Erscheinungsbild des aktuellen Eigenschaftsblatts angibt.|
|[CMFCPropertySheet::GetNavBarWidth](#getnavbarwidth)|Ruft die Breite der Navigationsleiste in Pixel ab.|
|[CMFCPropertySheet::GetTab](#gettab)|Ruft das interne Registerkarten-Steuerelementobjekt ab, das das aktuelle Eigenschaftsblatt-Steuerelement unterstützt.|
|`CMFCPropertySheet::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|
|[CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol)|Initialisiert das Erscheinungsbild des aktuellen Eigenschaftsblatt-Steuerelements.|
|[CMFCPropertySheet::OnActivatePage](#onactivatepage)|Wird durch das Framework aufgerufen, wenn eine Eigenschaftsseite aktiviert wird.|
|[CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader)|Wird durch das Framework aufgerufen, um einen benutzerdefinierten Eigenschaftsseitenheader zu zeichnen.|
|`CMFCPropertySheet::OnInitDialog`|Behandelt die [WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) Nachricht. (Überschreibt [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|
|[CMFCPropertySheet::OnRemoveTreePage](#onremovetreepage)|Wird durch das Framework aufgerufen, um eine Eigenschaftsseite aus einem Struktursteuerelement zu entfernen.|
|`CMFCPropertySheet::PreTranslateMessage`|Übersetzt Fensternachrichten, bevor sie an die [TranslateMessage-](/windows/win32/api/winuser/nf-winuser-translatemessage) und [DispatchMessage-Windows-Funktionen](/windows/win32/api/winuser/nf-winuser-dispatchmessage) gesendet werden. (Überschreibt `CPropertySheet::PreTranslateMessage`.)|
|[CMFCPropertySheet::RemoveCategory](#removecategory)|Entfernt einen Knoten aus dem Struktursteuerelement.|
|[CMFCPropertySheet::RemovePage](#removepage)|Entfernt eine Eigenschaftenseite aus dem Eigenschaftenblatt.|
|[CMFCPropertySheet::SetIconsList](#seticonslist)|Gibt die Liste der Bilder an, die in der Navigationssteuerung des Outlook-Bereichs verwendet werden.|
|[CMFCPropertySheet::SetLook](#setlook)|Gibt das Erscheinungsbild des Eigenschaftsblatts an.|

## <a name="remarks"></a>Bemerkungen

Die Klasse `CMFCPropertySheet` stellt Eigenschaftsblätter dar, auch als „Dialogfelder im Registerformat“ bezeichnet. Die `CMFCPropertySheet`-Klasse kann eine Eigenschaftsseite in einer Vielzahl von Möglichkeiten anzeigen.

Führen Sie die folgenden Schritte aus, um die `CMFCPropertySheet`-Klasse in Ihrer Anwendung zu verwenden:

1. Leiten Sie eine Klasse aus der `CMFCPropertySheet`-Klasse ab, und benennen Sie die Klasse, beispielsweise als „CMyPropertySheet“.

1. Erstellen Sie ein [CMFCPropertyPage-Objekt](../../mfc/reference/cmfcpropertypage-class.md) für jede Eigenschaftenseite.

1. Rufen Sie die [CMFCPropertySheet::SetLook-Methode](#setlook) im CMyPropertySheet-Konstruktor auf. Ein Parameter dieser Methode gibt an, dass die Eigenschaftsseiten entweder als Registerkarten oben oder links im Eigenschaftsblatt oder als Registerkarten im Stile eines Microsoft OneNote-Eigenschaftsblatts oder als Schaltflächen auf einem Microsoft Outlook-Symbolleistensteuerelement oder als Knoten in einem Gesamtstruktursteuerelement oder als eine Liste von Elementen auf der linken Seite des Eigenschaftsblatt angezeigt werden sollen.

1. Wenn Sie ein Eigenschaftenblatt im Stil einer Microsoft Outlook-Symbolleiste erstellen, rufen Sie die [CMFCPropertySheet::SetIconsList-Methode](#seticonslist) auf, um eine Bildliste zusammen mit den Eigenschaftenseiten zuzuordnen.

1. Rufen Sie die [CMFCPropertySheet::AddPage-Methode](#addpage) für jede Eigenschaftenseite auf.

1. Erstellen Sie ein `CMFCPropertySheet`-Steuerelement, und rufen Sie dessen `DoModal`-Methode auf.

## <a name="illustrations"></a>Abbildungen

In der folgenden Abbildung wird ein Eigenschaftsblatt gezeigt, das im Stile einer eingebetteten Microsoft Outlook-Symbolleiste vorliegt. Die Outlook-Symbolleiste wird auf der linken Seite des Eigenschaftenfensters angezeigt.

![CMFCPropertySheet-Farbsteuerelemente](../../mfc/reference/media/cmfcpropertysheet_color.png "CMFCPropertySheet-Farbsteuerelemente")

Die folgende Abbildung zeigt ein Eigenschaftenblatt, das ein [CMFCPropertyGridCtrl-Klassenobjekt](../../mfc/reference/cmfcpropertygridctrl-class.md) enthält. Bei diesem Objekt handelt es sich um ein Eigenschaftsblatt im Stile eines Eigenschaftsblatts für allgemeine Standardsteuerelemente.

![CMFCPropertySheet-Listen- und Farbsteuerelemente](../../mfc/reference/media/cmfcpropertysheet_list.png "CMFCPropertySheet-Listen- und Farbsteuerelemente")

In der folgenden Abbildung wird ein Eigenschaftsblatt gezeigt, das im Stile eines Struktursteuerelements vorliegt.

![Eigenschaftenbaum](../../mfc/reference/media/proptree.png "Eigenschaftenbaum")

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxpropertysheet.h

## <a name="cmfcpropertysheetaddpage"></a><a name="addpage"></a>CMFCPropertySheet::AddPage

Fügt dem Eigenschaftsblatt eine Seite hinzu.

```cpp
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parameter

*pPage*<br/>
[in] Zeiger auf ein Seitenobjekt. Dieser Parameter darf nicht NULL sein.

### <a name="remarks"></a>Bemerkungen

Diese Methode fügt die angegebene Eigenschaftenseite als ganz rechte Registerkarte im Eigenschaftenblatt hinzu. Verwenden Sie daher diese Methode, um Seiten in links nach rechts zu addieren.

Wenn das Eigenschaftenblatt im Stil von Microsoft Outlook ist, zeigt das Framework eine Liste der Navigationsschaltflächen links neben dem Eigenschaftenblatt an. Nachdem diese Methode eine Eigenschaftenseite hinzugefügt hat, wird der Liste eine entsprechende Schaltfläche hinzugefügt. Um eine Eigenschaftenseite anzuzeigen, klicken Sie auf die entsprechende Schaltfläche. Weitere Informationen zu Formatvorlagen von Eigenschaftenblättern finden Sie unter [CMFCPropertySheet::SetLook](#setlook).

## <a name="cmfcpropertysheetaddpagetotree"></a><a name="addpagetotree"></a>CMFCPropertySheet::AddPageToTree

Fügt dem Struktursteuerelement eine neue Eigenschaftsseite hinzu.

```cpp
void AddPageToTree(
    CMFCPropertySheetCategoryInfo* pCategory,
    CMFCPropertyPage* pPage,
    int nIconNum=-1,
    int nSelIconNum=-1);
```

### <a name="parameters"></a>Parameter

*pKategorie*<br/>
[in] Zeiger auf einen übergeordneten Strukturknoten oder NULL, um die angegebene Seite dem Knoten der obersten Ebene zuzuordnen. Rufen Sie die [CMFCPropertySheet::AddTreeCategory-Methode](#addtreecategory) auf, um diesen Zeiger abzurufen.

*pPage*<br/>
[in] Zeiger auf ein Eigenschaftenseitenobjekt.

*nIconNum*<br/>
[in] Nullbasierter Index eines Symbols oder -1, wenn kein Symbol verwendet wird. Das Symbol wird neben der Eigenschaftenseite des Baumsteuerelements angezeigt, wenn die Seite nicht ausgewählt ist. Der Standardwert ist -1.

*nSelIconNum*<br/>
[in] Nullbasierter Index eines Symbols oder -1, wenn kein Symbol verwendet wird. Das Symbol wird neben der Eigenschaftenseite des Baumsteuerelements angezeigt, wenn die Seite ausgewählt ist. Der Standardwert ist -1.

### <a name="remarks"></a>Bemerkungen

Diese Methode fügt eine Eigenschaftenseite als Blatt eines Baumsteuerelements hinzu. Um eine Eigenschaftenseite hinzuzufügen, `CMFCPropertySheet` erstellen Sie ein Objekt, rufen Sie die [CMFCPropertySheet::SetLook-Methode](#setlook) auf, wobei der *look-Parameter* auf festgelegt `CMFCPropertySheet::PropSheetLook_Tree`ist, und verwenden Sie dann diese Methode, um die Eigenschaftenseite hinzuzufügen.

## <a name="cmfcpropertysheetaddtreecategory"></a><a name="addtreecategory"></a>CMFCPropertySheet::AddTreeCategory

Fügt dem Struktursteuerelement einen neuen Knoten hinzu.

```
CMFCPropertySheetCategoryInfo* AddTreeCategory(
    LPCTSTR lpszLabel,
    int nIconNum=-1,
    int nSelectedIconNum=-1,
    const CMFCPropertySheetCategoryInfo* pParentCategory=NULL);
```

### <a name="parameters"></a>Parameter

*lpszLabel*<br/>
[in] Der Name des Knotens.

*nIconNum*<br/>
[in] Nullbasierter Index eines Symbols oder -1, wenn kein Symbol verwendet wird. Das Symbol wird neben der Eigenschaftenseite des Baumsteuerelements angezeigt, wenn die Seite nicht ausgewählt ist. Der Standardwert ist -1.

*nSelectedIconNum*<br/>
[in] Nullbasierter Index eines Symbols oder -1, wenn kein Symbol verwendet wird. Das Symbol wird neben der Eigenschaftenseite des Baumsteuerelements angezeigt, wenn die Seite ausgewählt ist. Der Standardwert ist -1.

*pParentKategorie*<br/>
[in] Zeiger auf einen übergeordneten Strukturknoten oder NULL, um die angegebene Seite dem Knoten der obersten Ebene zuzuordnen. Legen Sie diesen Parameter mit der [CMFCPropertySheet::AddTreeCategory-Methode](#addtreecategory) fest.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den neuen Knoten im Struktursteuerelement.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um dem Struktursteuerelement einen neuen Knoten hinzuzufügen, der auch als Kategorie bezeichnet wird. Um einen Knoten hinzuzufügen, `CMFCPropertySheet` erstellen Sie ein Objekt, rufen Sie die [CMFCPropertySheet::SetLook-Methode](#setlook) auf, wobei der *look-Parameter* auf `CMFCPropertySheet::PropSheetLook_Tree`festgelegt ist, und verwenden Sie dann diese Methode, um den Knoten hinzuzufügen.

Verwenden Sie den Rückgabewert dieser Methode in nachfolgenden Aufrufen von [CMFCPropertySheet::AddPageToTree](#addpagetotree) und [CMFCPropertySheet::AddTreeCategory](#addtreecategory).

## <a name="cmfcpropertysheetcmfcpropertysheet"></a><a name="cmfcpropertysheet"></a>CMFCPropertySheet::CMFCPropertySheet

Erstellt ein `CMFCPropertySheet`-Objekt.

```
CMFCPropertySheet(
    UINT nIDCaption,
    CWnd* pParentWnd=NULL,
    UINT iSelectPage=0);

CMFCPropertySheet(
    LPCTSTR pszCaption,
    CWnd* pParentWnd=NULL,
    UINT iSelectPage=0);
```

### <a name="parameters"></a>Parameter

*pszCaption*<br/>
[in] Eine Zeichenfolge, die die Eigenschaftenblattbeschriftung enthält. Lässt keine NULL-Werte zu.

*nIDCaption*<br/>
[in] Eine Ressourcen-ID, die die Eigenschaftenblattbeschriftung enthält.

*pParentWnd*<br/>
[in] Zeigen Sie auf das übergeordnete Fenster des Eigenschaftenblatts oder NULL, wenn das übergeordnete Fenster das Hauptfenster der Anwendung ist. Der Standardwert ist NULL.

*iSelectPage*<br/>
[in] Der nullbasierte Index der obersten Eigenschaftenseite. Der Standardwert ist 0.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter den Parametern für den [CPropertySheet::CPropertySheet-Konstruktor.](../../mfc/reference/cpropertysheet-class.md#cpropertysheet)

## <a name="cmfcpropertysheetenablepageheader"></a><a name="enablepageheader"></a>CMFCPropertySheet::EnablePageHeader

Reserviert oben auf jeder Seite Platz, um einen benutzerdefinierten Header zu zeichnen.

```cpp
void EnablePageHeader(int nHeaderHeight);
```

### <a name="parameters"></a>Parameter

*nHeaderHeight*<br/>
[in] Die Höhe des Headers in Pixel.

### <a name="remarks"></a>Bemerkungen

Um den Wert des *Parameters nHeaderHeight* zum Zeichnen eines benutzerdefinierten Headers zu verwenden, überschreiben Sie die [CMFCPropertySheet::OnDrawPageHeader-Methode.](#ondrawpageheader)

## <a name="cmfcpropertysheetgetheaderheight"></a><a name="getheaderheight"></a>CMFCPropertySheet::GetHeaderHeight

Ruft die Höhe des aktuellen Headers ab.

```
int GetHeaderHeight() const;
```

### <a name="return-value"></a>Rückgabewert

Die Höhe des Headers in Pixel.

### <a name="remarks"></a>Bemerkungen

Rufen Sie die [CMFCPropertySheet::EnablePageHeader-Methode](#enablepageheader) auf, bevor Sie diese Methode aufrufen.

## <a name="cmfcpropertysheetgetlook"></a><a name="getlook"></a>CMFCPropertySheet::GetLook

Ruft einen Enumerationswert ab, der das Erscheinungsbild des aktuellen Eigenschaftsblatts angibt.

```
PropSheetLook GetLook() const;
```

### <a name="return-value"></a>Rückgabewert

Einer der Enumerationswerte, der die Darstellung des Eigenschaftenblatts angibt. Eine Liste möglicher Werte finden Sie in der Enumerationstabelle im Abschnitt Hinweise von [CMFCPropertySheet::SetLook](#setlook).

## <a name="cmfcpropertysheetgetnavbarwidth"></a><a name="getnavbarwidth"></a>CMFCPropertySheet::GetNavBarWidth

Ruft die Breite der Navigationsleiste ab.

```
int GetNavBarWidth() const;
```

### <a name="return-value"></a>Rückgabewert

Die Breite der Navigationsleiste in Pixel.

## <a name="cmfcpropertysheetgettab"></a><a name="gettab"></a>CMFCPropertySheet::GetTab

Ruft das interne Registerkarten-Steuerelementobjekt ab, das das aktuelle Eigenschaftsblatt-Steuerelement unterstützt.

```
CMFCTabCtrl& GetTab() const;
```

### <a name="return-value"></a>Rückgabewert

Ein internes Tabstopp-Kontrollobjekt.

### <a name="remarks"></a>Bemerkungen

Sie können ein Eigenschaftenblatt so festlegen, dass es in verschiedenen Formatvorlagen angezeigt wird, z. B. in einem Baumsteuerelement, einer Liste von Navigationsschaltflächen oder einer Reihe von Registerkarten.

Bevor Sie diese Methode aufrufen, rufen Sie die [CMFCPropertySheet::SetLook-Methode](#setlook) auf, um die Darstellung des Eigenschaftenblattsteuerelements festzulegen. Rufen Sie dann die [CMFCPropertySheet::InitNavigationControl-Methode](#initnavigationcontrol) auf, um das interne Tabstopp-Kontrollobjekt zu initialisieren. Verwenden Sie diese Methode, um das Registerkartensteuerelement objekt abzurufen, und verwenden Sie dann dieses Objekt, um mit den Registerkarten auf dem Eigenschaftenblatt zu arbeiten.

Diese Methode wird im Debugmodus bestätigt, wenn das Eigenschaftenblattsteuerelement nicht so eingestellt ist, dass es im Stil von Microsoft OneNote angezeigt wird.

## <a name="cmfcpropertysheetinitnavigationcontrol"></a><a name="initnavigationcontrol"></a>CMFCPropertySheet::InitNavigationControl

Initialisiert das Erscheinungsbild des aktuellen Eigenschaftsblatt-Steuerelements.

```
virtual CWnd* InitNavigationControl();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Fenster des Eigenschaftenblattsteuerelements.

### <a name="remarks"></a>Bemerkungen

Ein Eigenschaftenblattsteuerelement kann in verschiedenen Formularen angezeigt werden, z. B. in einer Reihe von Registerkarten, einem Baumsteuerelement oder einer Liste von Navigationsschaltflächen. Verwenden Sie die [CMFCPropertySheet::SetLook-Methode,](#setlook) um die Darstellung des Eigenschaftenblattsteuerelements anzugeben.

## <a name="cmfcpropertysheetonactivatepage"></a><a name="onactivatepage"></a>CMFCPropertySheet::OnActivatePage

Wird durch das Framework aufgerufen, wenn eine Eigenschaftsseite aktiviert wird.

```
virtual void OnActivatePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parameter

*pPage*<br/>
[in] Zeiger auf ein Eigenschaftenseitenobjekt, das die aktivierte Eigenschaftenseite darstellt.

### <a name="remarks"></a>Bemerkungen

Standardmäßig stellt diese Methode sicher, dass die aktivierte Eigenschaftenseite in die Ansicht gescrollt wird. Wenn der Stil des aktuellen Eigenschaftenblatts einen Microsoft Outlook-Bereich enthält, legt diese Methode die entsprechende Outlook-Schaltfläche auf den status überprüft fest.

## <a name="cmfcpropertysheetondrawpageheader"></a><a name="ondrawpageheader"></a>CMFCPropertySheet::OnDrawPageHeader

Wird vom Framework aufgerufen, um die Kopfzeile für eine benutzerdefinierte Eigenschaftenseite zu zeichnen.

```
virtual void OnDrawPageHeader(
    CDC* pDC,
    int nPage,
    CRect rectHeader);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Zeiger auf einen Gerätekontext.

*nPage*<br/>
[in] Die Null-basierte Eigenschaftsseitennummer.

*rectHeader*<br/>
[in] Ein umgrenzendes Rechteck, das angibt, wo die Kopfzeile gezeichnet werden soll.

### <a name="remarks"></a>Bemerkungen

Standardmäßig führt diese Methode nichts aus. Wenn Sie diese Methode überschreiben, rufen Sie die [CMFCPropertySheet::EnablePageHeader-Methode](#enablepageheader) auf, bevor das Framework diese Methode aufruft.

## <a name="cmfcpropertysheetonremovetreepage"></a><a name="onremovetreepage"></a>CMFCPropertySheet::OnRemoveTreePage

Wird durch das Framework aufgerufen, um eine Eigenschaftsseite aus einem Struktursteuerelement zu entfernen.

```
virtual BOOL OnRemoveTreePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parameter

*pPage*<br/>
[in] Zeiger auf ein Eigenschaftenseitenobjekt, das die zu entfernende Eigenschaftenseite darstellt.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

## <a name="cmfcpropertysheetremovecategory"></a><a name="removecategory"></a>CMFCPropertySheet::RemoveCategory

Entfernt einen Knoten aus dem Struktursteuerelement.

```cpp
void RemoveCategory(CMFCPropertySheetCategoryInfo* pCategory);
```

### <a name="parameters"></a>Parameter

*pKategorie*<br/>
[in] Zeiger auf eine Kategorie (Knoten), die entfernt werden soll.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um einen Knoten, der auch als Kategorie bezeichnet wird, aus einem Struktursteuerelement zu entfernen. Verwenden Sie die [CMFCPropertySheet::AddTreeCategory-Methode,](#addtreecategory) um einem Struktursteuerelement einen Knoten hinzuzufügen.

## <a name="cmfcpropertysheetremovepage"></a><a name="removepage"></a>CMFCPropertySheet::RemovePage

Entfernt eine Eigenschaftenseite aus dem Eigenschaftenblatt.

```cpp
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>Parameter

*pPage*<br/>
[in] Zeiger auf eigenschaftenseitiges Objekt, das die zu entfernende Eigenschaftenseite darstellt. Lässt keine NULL-Werte zu.

*nPage*<br/>
[in] Nullbasierter Index der zu entfernenden Seite.

### <a name="remarks"></a>Bemerkungen

Diese Methode entfernt die angegebene Eigenschaftenseite und zerstört das zugehörige Fenster. Das Eigenschaftenseitenobjekt, das der *pPage-Parameter* angibt, wird erst zerstört, wenn das [CMFCPropertySheet-Fenster](../../mfc/reference/cmfcpropertysheet-class.md) geschlossen wird.

## <a name="cmfcpropertysheetseticonslist"></a><a name="seticonslist"></a>CMFCPropertySheet::SetIconsList

Gibt die Liste der Bilder an, die in der Navigationssteuerung des Outlook-Bereichs verwendet werden.

```
BOOL SetIconsList(
    UINT uiImageListResID,
    int cx,
    COLORREF clrTransparent=RGB(255, 0, 255));
void SetIconsList(HIMAGELIST hIcons);
```

### <a name="parameters"></a>Parameter

*uiImageListResID*<br/>
[in] Die Ressourcen-ID einer Bildliste.

*Cx*<br/>
[in] Die Breite der Symbole in der Bildliste in Pixel.

*clrTransparent*<br/>
[in] Die transparente Bildfarbe. Die Teile des Bildes, die diese Farbe sind, sind transparent. Der Standardwert ist das Farbmagenta, RGB(255,0,255).

*hIcons*<br/>
[in] Ein Handle für eine vorhandene Bildliste.

### <a name="return-value"></a>Rückgabewert

In der ersten Methodenüberladesyntax TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Wenn das Eigenschaftenblatt im Stil von Microsoft Outlook ist, zeigt das Framework eine Liste der Navigationsschaltflächen, das outlook-Bereichssteuerelement, links neben dem Eigenschaftenblatt an. Verwenden Sie diese Methode, um die Bildliste festzulegen, die vom Outlook-Bereichssteuerelement verwendet werden soll.

Weitere Informationen zu den Methoden, die diese Methode unterstützen, finden Sie unter [CImageList::Create](../../mfc/reference/cimagelist-class.md#create) und [CImageList::Add](../../mfc/reference/cimagelist-class.md#add). Weitere Informationen zum Festlegen des Stils eines Eigenschaftenblatts finden Sie unter [CMFCPropertySheet::SetLook](#setlook).

## <a name="cmfcpropertysheetsetlook"></a><a name="setlook"></a>CMFCPropertySheet::SetLook

Gibt das Erscheinungsbild des Eigenschaftsblatts an.

```cpp
void SetLook(
    PropSheetLook look,
    int nNavControlWidth=100);
```

### <a name="parameters"></a>Parameter

*Blick*<br/>
[in] Einer der Enumerationswerte, der die Darstellung des Eigenschaftenblatts angibt. Der Standardstil für ein `CMFCPropertySheet::PropSheetLook_Tabs`Eigenschaftenblatt ist . Weitere Informationen finden Sie in der Tabelle im Abschnitt "Bemerkungen" zu diesem Thema.

*nNavControlWidth*<br/>
[in] Die Breite des Navigationssteuerelements in Pixel. Der Standardwert ist 100.

### <a name="remarks"></a>Bemerkungen

Um ein Eigenschaftenblatt in einem anderen Stil als dem Standard anzuzeigen, rufen Sie diese Methode auf, bevor Sie das Eigenschaftenblattfenster erstellen.

In der folgenden Tabelle sind die Enumerationswerte aufgeführt, die im *Look-Parameter* angegeben werden können.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|`CMFCPropertySheet::PropSheetLook_Tabs`|(Standard) Zeigt eine Registerkarte für jede Eigenschaftenseite an. Registerkarten werden oben auf dem Eigenschaftenblatt angezeigt und gestapelt, wenn mehr Registerkarten vorhanden sind, als in eine einzelne Zeile passen.|
|`CMFCPropertySheet::PropSheetLook_OutlookBar`|Zeigt eine Liste der Navigationsschaltflächen im Stil der Microsoft Outlook-Leiste auf der linken Seite des Eigenschaftenblatts an. Jede Schaltfläche in der Liste entspricht einer Eigenschaftenseite. Das Framework zeigt Bildlaufpfeile an, wenn mehr Schaltflächen vorhanden sind, als in den sichtbaren Bereich der Liste passen.|
|`CMFCPropertySheet::PropSheetLook_Tree`|Zeigt ein Baumsteuerelement auf der linken Seite des Eigenschaftenblatts an. Jeder übergeordnete oder untergeordnete Knoten des Struktursteuerelements entspricht einer Eigenschaftenseite. Das Framework zeigt Bildlaufpfeile an, wenn mehr Knoten vorhanden sind, als in den sichtbaren Bereich des Baumsteuerelements passen.|
|`CMFCPropertySheet::PropSheetLook_OneNoteTabs`|Zeigt für jede Eigenschaftenseite eine Registerkarte im Format von Microsoft OneNote an. Das Framework zeigt Registerkarten oben auf dem Eigenschaftenblatt und Bildlaufpfeile an, wenn mehr Registerkarten vorhanden sind, als in eine einzelne Zeile passen.|
|`CMFCPropertySheet::PropSheetLook_List`|Zeigt eine Liste auf der linken Seite des Eigenschaftenblatts an. Jedes Listenelement entspricht einer Eigenschaftenseite. Das Framework zeigt Bildlaufpfeile an, wenn mehr Listenelemente vorhanden sind, als in den sichtbaren Bereich der Liste passen.|

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyPage-Klasse](../../mfc/reference/cmfcpropertypage-class.md)<br/>
[CMFCOutlookBar-Klasse](../../mfc/reference/cmfcoutlookbar-class.md)
