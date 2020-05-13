---
title: CToolBar-Klasse
ms.date: 11/04/2016
f1_keywords:
- CToolBar
- AFXEXT/CToolBar
- AFXEXT/CToolBar::CToolBar
- AFXEXT/CToolBar::CommandToIndex
- AFXEXT/CToolBar::Create
- AFXEXT/CToolBar::CreateEx
- AFXEXT/CToolBar::GetButtonInfo
- AFXEXT/CToolBar::GetButtonStyle
- AFXEXT/CToolBar::GetButtonText
- AFXEXT/CToolBar::GetItemID
- AFXEXT/CToolBar::GetItemRect
- AFXEXT/CToolBar::GetToolBarCtrl
- AFXEXT/CToolBar::LoadBitmap
- AFXEXT/CToolBar::LoadToolBar
- AFXEXT/CToolBar::SetBitmap
- AFXEXT/CToolBar::SetButtonInfo
- AFXEXT/CToolBar::SetButtons
- AFXEXT/CToolBar::SetButtonStyle
- AFXEXT/CToolBar::SetButtonText
- AFXEXT/CToolBar::SetHeight
- AFXEXT/CToolBar::SetSizes
helpviewer_keywords:
- CToolBar [MFC], CToolBar
- CToolBar [MFC], CommandToIndex
- CToolBar [MFC], Create
- CToolBar [MFC], CreateEx
- CToolBar [MFC], GetButtonInfo
- CToolBar [MFC], GetButtonStyle
- CToolBar [MFC], GetButtonText
- CToolBar [MFC], GetItemID
- CToolBar [MFC], GetItemRect
- CToolBar [MFC], GetToolBarCtrl
- CToolBar [MFC], LoadBitmap
- CToolBar [MFC], LoadToolBar
- CToolBar [MFC], SetBitmap
- CToolBar [MFC], SetButtonInfo
- CToolBar [MFC], SetButtons
- CToolBar [MFC], SetButtonStyle
- CToolBar [MFC], SetButtonText
- CToolBar [MFC], SetHeight
- CToolBar [MFC], SetSizes
ms.assetid: e868da26-5e07-4607-9651-e2f863ad9059
ms.openlocfilehash: cbb2d1bb797737a14e9728d339305bf9c371b543
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752210"
---
# <a name="ctoolbar-class"></a>CToolBar-Klasse

Steuerleisten, die eine Zeile mit Bitmapschaltflächen und optionalen Trennzeichen enthalten.

## <a name="syntax"></a>Syntax

```
class CToolBar : public CControlBar
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CToolBar::CToolBar](#ctoolbar)|Erstellt ein `CToolBar`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CToolBar::CommandToIndex](#commandtoindex)|Gibt den Index einer Schaltfläche mit der angegebenen Befehls-ID zurück.|
|[CToolBar::Erstellen](#create)|Erstellt die Windows-Symbolleiste und `CToolBar` fügt sie an das Objekt an.|
|[CToolBar::CreateEx](#createex)|Erstellt `CToolBar` ein Objekt mit zusätzlichen `CToolBarCtrl` Stilen für das eingebettete Objekt.|
|[CToolBar::GetButtonInfo](#getbuttoninfo)|Ruft die ID, den Stil und die Bildnummer einer Schaltfläche ab.|
|[CToolBar::GetButtonStyle](#getbuttonstyle)|Ruft den Stil für eine Schaltfläche ab.|
|[CToolBar::GetButtonText](#getbuttontext)|Ruft den Text ab, der auf einer Schaltfläche angezeigt wird.|
|[CToolBar::GetItemID](#getitemid)|Gibt die Befehls-ID einer Schaltfläche oder eines Trennzeichens am angegebenen Index zurück.|
|[CToolBar::GetItemRect](#getitemrect)|Ruft das Anzeigerechteck für das Element am angegebenen Index ab.|
|[CToolBar::GetToolBarCtrl](#gettoolbarctrl)|Ermöglicht den direkten Zugriff auf das zugrunde liegende gemeinsame Steuerelement.|
|[CToolBar::LoadBitmap](#loadbitmap)|Lädt die Bitmap mit Bitmap-Schaltflächenbildern.|
|[CToolBar::LoadToolBar](#loadtoolbar)|Lädt eine Symbolleistenressource, die mit dem Ressourcen-Editor erstellt wurde.|
|[CToolBar::SetBitmap](#setbitmap)|Legt ein bitmapiertes Bild fest.|
|[CToolBar::SetButtonInfo](#setbuttoninfo)|Legt die ID, den Stil und die Bildnummer einer Schaltfläche fest.|
|[CToolBar::SetButtons](#setbuttons)|Legt Schaltflächenstile und einen Index von Schaltflächenbildern innerhalb der Bitmap fest.|
|[CToolBar::SetButtonStyle](#setbuttonstyle)|Legt den Stil für eine Schaltfläche fest.|
|[CToolBar::SetButtonText](#setbuttontext)|Legt den Text fest, der auf einer Schaltfläche angezeigt wird.|
|[CToolBar::SetHeight](#setheight)|Legt die Höhe der Symbolleiste fest.|
|[CToolBar::SetSizes](#setsizes)|Legt die Größe von Schaltflächen und deren Bitmaps fest.|

## <a name="remarks"></a>Bemerkungen

Die Tasten können wie Drucktasten, Kontrollkästchen oder Optionsfelder wirken. `CToolBar`Objekte sind in der Regel eingebettete Member von Frame-Fenster-Objekten, die von der Klasse [CFrameWnd](../../mfc/reference/cframewnd-class.md) oder [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)abgeleitet sind.

[CToolBar::GetToolBarCtrl](#gettoolbarctrl), eine Memberfunktion, die neu in MFC 4.0 ist, ermöglicht es Ihnen, die Unterstützung des gemeinsamen Windows-Steuerelements für die Anpassung der Symbolleiste und zusätzliche Funktionen zu nutzen. `CToolBar`Memberfunktionen bieten Ihnen die meisten Funktionen der allgemeinen Windows-Steuerelemente. Wenn Sie jedoch `GetToolBarCtrl`aufrufen, können Sie Ihren Symbolleisten noch mehr der Eigenschaften von Windows 95/98-Symbolleisten geben. Wenn Sie `GetToolBarCtrl`aufrufen, wird ein `CToolBarCtrl` Verweis auf ein Objekt zurückgegeben. Weitere Informationen zum Entwerfen von Symbolleisten mit allgemeinen Windows-Steuerelementen finden Sie unter [CToolBarCtrl.](../../mfc/reference/ctoolbarctrl-class.md) Allgemeinere Informationen zu allgemeinen Steuerelementen finden Sie unter [Allgemeine Steuerelemente](/windows/win32/Controls/common-controls-intro) im Windows SDK.

Visual C++ bietet Ihnen zwei Methoden zum Erstellen einer Symbolleiste. Führen Sie die folgenden Schritte aus, um eine Symbolleistenressource mit dem Ressourcen-Editor zu erstellen:

1. Erstellen Sie eine Symbolleistenressource.

1. Erstellen `CToolBar` Sie das Objekt.

1. Rufen Sie die Funktion [Erstellen](#create) (oder [CreateEx](#createex)) auf, `CToolBar` um die Windows-Symbolleiste zu erstellen und an das Objekt anzufügen.

1. Rufen Sie [LoadToolBar](#loadtoolbar) auf, um die Symbolleistenressource zu laden.

Gehen Sie andernfalls folgendermaßen vor:

1. Erstellen `CToolBar` Sie das Objekt.

1. Rufen Sie die Funktion [Erstellen](#create) (oder [CreateEx](#createex)) auf, `CToolBar` um die Windows-Symbolleiste zu erstellen und an das Objekt anzufügen.

1. Rufen Sie [LoadBitmap](#loadbitmap) auf, um die Bitmap zu laden, die die Symbolleisten-Schaltflächenbilder enthält.

1. Rufen Sie [SetButtons](#setbuttons) auf, um den Schaltflächenstil festzulegen, und ordnen Sie jede Schaltfläche einem Bild in der Bitmap zu.

Alle Schaltflächenbilder in der Symbolleiste stammen aus einer Bitmap, die für jede Schaltfläche ein Bild enthalten muss. Alle Bilder müssen die gleiche Größe haben; Der Standardwert ist 16 Pixel breit und 15 Pixel hoch. Bilder müssen nebeneinander in der Bitmap sein.

Die `SetButtons` Funktion nimmt einen Zeiger auf ein Array von Steuerelement-IDs und eine ganze Zahl, die die Anzahl der Elemente im Array angibt. Die Funktion legt die ID jeder Schaltfläche auf den Wert des entsprechenden Elements des Arrays fest und weist jeder Schaltfläche einen Bildindex zu, der die Position des Bildes der Schaltfläche in der Bitmap angibt. Wenn ein Arrayelement den Wert ID_SEPARATOR hat, wird kein Bildindex zugewiesen.

Die Reihenfolge der Bilder in der Bitmap ist in der Regel die Reihenfolge, in der sie auf dem Bildschirm gezeichnet werden, aber Sie können die [SetButtonInfo-Funktion](#setbuttoninfo) verwenden, um die Beziehung zwischen Bildreihenfolge und Zeichnungsreihenfolge zu ändern.

Alle Schaltflächen in einer Symbolleiste haben die gleiche Größe. Der Standardwert ist 24 x 22 Pixel, gemäß *Windows Interface Guidelines for Software Design*. Jeder zusätzliche Abstand zwischen den Bild- und Schaltflächenbemaßungen wird verwendet, um einen Rahmen um das Bild zu bilden.

Jede Schaltfläche hat ein Bild. Die verschiedenen Schaltflächenzustände und -stile (gedrückt, nach oben, unten, deaktiviert, deaktiviert und unbestimmt) werden aus diesem einen Bild generiert. Obwohl Bitmaps eine beliebige Farbe haben können, können Sie die besten Ergebnisse mit Bildern in Schwarz und Grautönen erzielen.

> [!WARNING]
> `CToolBar`unterstützt Bitmaps mit maximal 16 Farben. Wenn Sie ein Bild in einen Symbolleisten-Editor laden, konvertiert Visual Studio das Bild bei Bedarf automatisch in eine 16-Farben-Bitmap und zeigt eine Warnmeldung an, wenn das Bild konvertiert wurde. Wenn Sie ein Bild mit mehr als 16 Farben verwenden (mit einem externen Editor zum Bearbeiten des Bildes), verhält sich die Anwendung möglicherweise unerwartet.

Symbolleistentasten imitieren standardmäßig Drucktasten. Symbolleistenschaltflächen können jedoch auch Kontrollkästchen- oder Optionsfelder imitieren. Kontrollkästchen-Schaltflächen haben drei Zustände: aktiviert, gelöscht und unbestimmt. Radiotasten haben nur zwei Zustände: aktiviert und gelöscht.

Um eine einzelne Schaltfläche oder einen Trennstil festzulegen, ohne auf ein Array zu zeigen, rufen `SetButtons`Sie [GetButtonStyle](#getbuttonstyle) auf, um den Stil abzurufen, und rufen Sie dann [SetButtonStyle](#setbuttonstyle) anstelle von auf. `SetButtonStyle`ist besonders nützlich, wenn Sie den Stil einer Schaltfläche zur Laufzeit ändern möchten.

Um Text zuzuweisen, der auf einer Schaltfläche angezeigt wird, rufen Sie [GetButtonText](#getbuttontext) auf, um den Text abzurufen, der auf der Schaltfläche angezeigt wird, und rufen Sie dann [SetButtonText](#setbuttontext) auf, um den Text festzulegen.

Um eine Kontrollkästchenschaltfläche zu erstellen, weisen Sie `CCmdUI` ihr den `SetCheck` Stil TBBS_CHECKBOX zu, oder verwenden Sie die Memberfunktion eines Objekts in einem ON_UPDATE_COMMAND_UI Handler. Durch `SetCheck` Aufrufen wird ein Pushbutton in eine Kontrollkästchen-Schaltfläche umgewandelt. Übergeben `SetCheck` Sie ein Argument von 0 für ungeprüft, 1 für überprüft oder 2 für unbestimmt.

Um ein Optionsfeld zu erstellen, rufen Sie die [SetRadio-Memberfunktion](../../mfc/reference/ccmdui-class.md#setradio) eines [CCmdUI-Objekts](../../mfc/reference/ccmdui-class.md) von einem ON_UPDATE_COMMAND_UI-Handler auf. Übergeben `SetRadio` Sie ein Argument von 0 für ungeprüft oder ungleich Null für aktiviert. Um das sich gegenseitig ausschließende Verhalten einer Funkgruppe bereitzustellen, müssen Sie über ON_UPDATE_COMMAND_UI Handler für alle Schaltflächen in der Gruppe verfügen.

Weitere Informationen zur `CToolBar`Verwendung finden Sie im Artikel [MFC Toolbar Implementation](../../mfc/mfc-toolbar-implementation.md) and [Technical Note 31: Control Bars](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CToolBar`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxext.h

## <a name="ctoolbarcommandtoindex"></a><a name="commandtoindex"></a>CToolBar::CommandToIndex

Diese Memberfunktion gibt den Index der ersten Symbolleistenschaltfläche zurück, `nIDFind`beginnend an Position 0, deren Befehls-ID übereinstimmt.

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parameter

*nIDFind*<br/>
Befehls-ID einer Symbolleistenschaltfläche.

### <a name="return-value"></a>Rückgabewert

Der Index der Schaltfläche oder -1, wenn keine Schaltfläche die angegebene Befehls-ID hat.

## <a name="ctoolbarcreate"></a><a name="create"></a>CToolBar::Erstellen

Diese Memberfunktion erstellt eine Windows-Symbolleiste (ein untergeordnetes Fenster) und ordnet sie dem `CToolBar` Objekt zu.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>Parameter

*pParentWnd*<br/>
Zeigen Sie mit dem Zeiger auf das Fenster, das das übergeordnete Fenster der Symbolleiste ist.

*dwStyle*<br/>
Der Symbolleistenstil. Weitere unterstützte Symbolleistenstile sind:

- CBRS_TOP Steuerleiste befindet sich oben im Rahmenfenster.

- CBRS_BOTTOM Steuerleiste befindet sich am unteren Rand des Rahmenfensters.

- CBRS_NOALIGN Steuerleiste wird nicht neu positioniert, wenn die Größe des übergeordneten Elements geändert wird.

- CBRS_TOOLTIPS Steuerleiste zeigt Werkzeugtipps an.

- CBRS_SIZE_DYNAMIC Steuerleiste ist dynamisch.

- CBRS_SIZE_FIXED Steuerleiste ist fixiert.

- CBRS_FLOATING Steuerleiste ist schwebend.

- CBRS_FLYBY Statusleiste zeigt Informationen zur Schaltfläche an.

- CBRS_HIDE_INPLACE Steuerleiste wird dem Benutzer nicht angezeigt.

*nID*<br/>
Die untergeordnete Fenster-ID der Symbolleiste.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Außerdem wird die Symbolleistenhöhe auf einen Standardwert festgelegt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]

## <a name="ctoolbarcreateex"></a><a name="createex"></a>CToolBar::CreateEx

Rufen Sie diese Funktion auf, um eine Windows-Symbolleiste `CToolBar` (ein untergeordnetes Fenster) zu erstellen und sie dem Objekt zuzuordnen.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = TBSTYLE_FLAT,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_ALIGN_TOP,
    CRect rcBorders = CRect(
    0,
    0,
    0,
    0),
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>Parameter

*pParentWnd*<br/>
Zeigen Sie mit dem Zeiger auf das Fenster, das das übergeordnete Fenster der Symbolleiste ist.

*dwCtrlStyle*<br/>
Zusätzliche Stile für die Erstellung des eingebetteten [CToolBarCtrl-Objekts.](../../mfc/reference/ctoolbarctrl-class.md) Standardmäßig ist dieser Wert auf TBSTYLE_FLAT festgelegt. Eine vollständige Liste der Symbolleistenstile finden Sie unter *dwStyle*.

*dwStyle*<br/>
Der Symbolleistenstil. Eine Liste der entsprechenden Formatvorlagen finden Sie unter [Toolleistensteuerung und Schaltflächenstile](/windows/win32/Controls/toolbar-control-and-button-styles) im Windows SDK.

*rcBorders*<br/>
Ein [CRect-Objekt,](../../atl-mfc-shared/reference/crect-class.md) das die Breiten der Symbolleistenfensterränder definiert. Diese Rahmen werden standardmäßig auf 0,0,0,0 festgelegt, was zu einem Symbolleistenfenster ohne Rahmen führt.

*nID*<br/>
Die untergeordnete Fenster-ID der Symbolleiste.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Außerdem wird die Symbolleistenhöhe auf einen Standardwert festgelegt.

Verwenden `CreateEx`Sie anstelle von [Create](#create), wenn bestimmte Stile während der Erstellung des eingebetteten Werkzeugleistensteuerelements vorhanden sein müssen. Legen Sie beispielsweise *dwCtrlStyle* auf TBSTYLE_FLAT &#124; TBSTYLE_TRANSPARENT, um eine Symbolleiste zu erstellen, die den Symbolleisten von Internet Explorer 4 ähnelt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]

## <a name="ctoolbarctoolbar"></a><a name="ctoolbar"></a>CToolBar::CToolBar

Diese Memberfunktion erstellt `CToolBar` ein Objekt und legt die Standardgrößen fest.

```
CToolBar();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie die Memberfunktion [Erstellen](#create) auf, um das Symbolleistenfenster zu erstellen.

## <a name="ctoolbargetbuttoninfo"></a><a name="getbuttoninfo"></a>CToolBar::GetButtonInfo

Diese Memberfunktion ruft die Steuerelement-ID, den Stil und den Bildindex der Symbolleistenschaltfläche oder des Trennzeichens an der von nIndex angegebenen Position *ab.*

```cpp
void GetButtonInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& iImage) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Index der Symbolleistenschaltfläche oder des Trennzeichens, deren Informationen abgerufen werden sollen.

*nID*<br/>
Verweis auf ein UINT, das auf die Befehls-ID der Schaltfläche gesetzt ist.

*nStyle*<br/>
Verweis auf ein UINT, das auf den Stil der Schaltfläche festgelegt ist.

*iImage*<br/>
Verweis auf eine ganze Zahl, die auf den Index des Bildes der Schaltfläche in der Bitmap festgelegt ist.

### <a name="remarks"></a>Bemerkungen

Diese Werte werden den Variablen zugewiesen, auf die von *nID*, *nStyle*und *iImage*verwiesen wird. Der Bildindex ist die Position des Bildes innerhalb der Bitmap, die Bilder für alle Symbolleistenschaltflächen enthält. Das erste Bild befindet sich an Position 0.

Wenn *nIndex* ein Trennzeichen angibt, wird *iImage* in Pixel auf die Trennbreite festgelegt.

## <a name="ctoolbargetbuttonstyle"></a><a name="getbuttonstyle"></a>CToolBar::GetButtonStyle

Rufen Sie diese Memberfunktion auf, um den Stil einer Schaltfläche oder eines Trennzeichens auf der Symbolleiste abzurufen.

```
UINT GetButtonStyle(int nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der Index der Symbolleistenschaltfläche oder des Abtrennstils, der abgerufen werden soll.

### <a name="return-value"></a>Rückgabewert

Der Stil der Schaltfläche oder des Trennzeichens, der von *nIndex*angegeben wird.

### <a name="remarks"></a>Bemerkungen

Der Stil einer Schaltfläche bestimmt, wie die Schaltfläche angezeigt wird und wie sie auf Benutzereingaben reagiert. Unter [SetButtonStyle](#setbuttonstyle) finden Sie Beispiele für Schaltflächenstile.

## <a name="ctoolbargetbuttontext"></a><a name="getbuttontext"></a>CToolBar::GetButtonText

Rufen Sie diese Memberfunktion auf, um den Text abzurufen, der auf einer Schaltfläche angezeigt wird.

```
CString GetButtonText(int nIndex) const;

void GetButtonText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Index des abzuholenden Textes.

*rString*<br/>
Ein Verweis auf ein [CString-Objekt,](../../atl-mfc-shared/reference/cstringt-class.md) das den abzuholenden Text enthält.

### <a name="return-value"></a>Rückgabewert

Ein `CString` Objekt, das den Schaltflächentext enthält.

### <a name="remarks"></a>Bemerkungen

Die zweite Form dieser Memberfunktion `CString` füllt ein Objekt mit dem Zeichenfolgentext.

## <a name="ctoolbargetitemid"></a><a name="getitemid"></a>CToolBar::GetItemID

Diese Memberfunktion gibt die Befehls-ID der von *nIndex*angegebenen Schaltfläche oder des Trennzeichens zurück.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Index des Elements, dessen ID abgerufen werden soll.

### <a name="return-value"></a>Rückgabewert

Die Befehls-ID der Von *nIndex*angegebenen Schaltfläche oder des Trennzeichens .

### <a name="remarks"></a>Bemerkungen

Separatoren geben ID_SEPARATOR zurück.

## <a name="ctoolbargetitemrect"></a><a name="getitemrect"></a>CToolBar::GetItemRect

Diese Memberfunktion füllt `RECT` die Struktur, deren Adresse in *lpRect* enthalten ist, mit den Koordinaten der Schaltfläche oder des Trennzeichens, die von *nIndex*angegeben sind.

```
virtual void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Index des Elements (Schaltfläche oder Trennzeichen), dessen Rechteckkoordinaten abgerufen werden sollen.

*lpRect*<br/>
Adresse der [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die die Koordinaten des Elements enthält.

### <a name="remarks"></a>Bemerkungen

Koordinaten sind in Pixel relativ zur oberen linken Ecke der Symbolleiste.

Verwenden `GetItemRect` Sie diese Option, um die Koordinaten eines Trennzeichens abzurufen, das Sie durch ein Kombinationsfeld oder ein anderes Steuerelement ersetzen möchten.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CToolBar::SetSizes](#setsizes).

## <a name="ctoolbargettoolbarctrl"></a><a name="gettoolbarctrl"></a>CToolBar::GetToolBarCtrl

Diese Memberfunktion ermöglicht den direkten Zugriff auf das zugrunde liegende gemeinsame Steuerelement.

```
CToolBarCtrl& GetToolBarCtrl() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf ein `CToolBarCtrl`-Objekt.

### <a name="remarks"></a>Bemerkungen

Verwenden `GetToolBarCtrl` Sie diese Möglichkeit, um die Funktionalität der allgemeinen Windows-Symbolleiste zu nutzen und die Unterstützung zu nutzen, die [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) für die Anpassung der Symbolleiste bietet.

Weitere Informationen zur Verwendung allgemeiner Steuerelemente finden Sie im Artikel [Steuerelemente](../../mfc/controls-mfc.md) und [allgemeine Steuerelemente](/windows/win32/Controls/common-controls-intro) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]

## <a name="ctoolbarloadbitmap"></a><a name="loadbitmap"></a>CToolBar::LoadBitmap

Rufen Sie diese Memberfunktion auf, `lpszResourceName` `nIDResource`um die von oder angegebene Bitmap zu laden.

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Parameter

*lpszResourceName*<br/>
Zeigen Sie auf den Ressourcennamen der bitmap, die geladen werden soll.

*nIDResource*<br/>
Ressourcen-ID der zu ladenden Bitmap.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Die Bitmap sollte ein Bild für jede Symbolleistenschaltfläche enthalten. Wenn die Bilder nicht der Standardgröße (16 Pixel breit und 15 Pixel hoch) angehören, rufen Sie [SetSizes](#setsizes) auf, um die Schaltflächengrößen und ihre Bilder festzulegen.

> [!WARNING]
> `CToolBar`unterstützt Bitmaps mit maximal 16 Farben. Wenn Sie ein Bild in einen Symbolleisten-Editor laden, konvertiert Visual Studio das Bild bei Bedarf automatisch in eine 16-Farben-Bitmap und zeigt eine Warnmeldung an, wenn das Bild konvertiert wurde. Wenn Sie ein Bild mit mehr als 16 Farben verwenden (mit einem externen Editor zum Bearbeiten des Bildes), verhält sich die Anwendung möglicherweise unerwartet.

## <a name="ctoolbarloadtoolbar"></a><a name="loadtoolbar"></a>CToolBar::LoadToolBar

Rufen Sie diese Memberfunktion auf, um die von *lpszResourceName* oder *nIDResource*angegebene Symbolleiste zu laden.

```
BOOL LoadToolBar(LPCTSTR lpszResourceName);
BOOL LoadToolBar(UINT nIDResource);
```

### <a name="parameters"></a>Parameter

*lpszResourceName*<br/>
Zeigen Sie auf den Ressourcennamen der zu ladenden Symbolleiste.

*nIDResource*<br/>
Ressourcen-ID der zu ladenden Symbolleiste.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zum Erstellen einer Symbolleistenressource finden Sie im [Symbolleisten-Editor](../../windows/toolbar-editor.md) in.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CToolBar::CreateEx](#createex).

## <a name="ctoolbarsetbitmap"></a><a name="setbitmap"></a>CToolBar::SetBitmap

Rufen Sie diese Memberfunktion auf, um das Bitmapbild für die Symbolleiste festzulegen.

```
BOOL SetBitmap(HBITMAP hbmImageWell);
```

### <a name="parameters"></a>Parameter

*hbmImageWell*<br/>
Handle eines Bitmapbilds, das einer Symbolleiste zugeordnet ist.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Rufen Sie `SetBitmap` z. B. an, um das Bitmap-Bild zu ändern, nachdem der Benutzer eine Aktion für ein Dokument durchgeführt hat, die die Aktion einer Schaltfläche ändert.

## <a name="ctoolbarsetbuttoninfo"></a><a name="setbuttoninfo"></a>CToolBar::SetButtonInfo

Rufen Sie diese Memberfunktion auf, um die Befehls-ID, den Stil und die Bildnummer der Schaltfläche festzulegen.

```cpp
void SetButtonInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int iImage);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Nullbasierter Index der Schaltfläche oder des Trennzeichens, für die Informationen festgelegt werden sollen.

*nID*<br/>
Der Wert, auf den die Befehls-ID der Schaltfläche festgelegt ist.

*nStyle*<br/>
Der neue Schaltflächenstil. Die folgenden Schaltflächenstile werden unterstützt:

- TBBS_BUTTON Standard-Taste (Standard)

- TBBS_SEPARATOR Separator

- TBBS_CHECKBOX Auto-Kontrollkästchen-Schaltfläche

- TBBS_GROUP Markiert den Beginn einer Gruppe von Schaltflächen

- TBBS_CHECKGROUP Markiert den Beginn einer Gruppe von Kontrollkästchen-Schaltflächen

- TBBS_DROPDOWN Erstellt eine Dropdown-Listenschaltfläche.

- TBBS_AUTOSIZE Die Breite der Schaltfläche wird basierend auf dem Text der Schaltfläche und nicht auf der Größe des Bildes berechnet.

- TBBS_NOPREFIX Dem Schaltflächentext ist kein Beschleunigerpräfix zugeordnet.

*iImage*<br/>
Neuer Index für das Bild der Schaltfläche in der Bitmap.

### <a name="remarks"></a>Bemerkungen

Für Trennzeichen, die den Stil TBBS_SEPARATOR haben, legt diese Funktion die Breite des Trennzeichens in Pixel auf den in *iImage*gespeicherten Wert fest.

> [!NOTE]
> Sie können auch Schaltflächenzustände mithilfe des Parameters *nStyle* festlegen. Da die Schaltflächenzustände jedoch vom [ON_UPDATE_COMMAND_UI-Handler](message-map-macros-mfc.md#on_update_command_ui) `SetButtonInfo` gesteuert werden, geht jeder Status, den Sie verwenden, während der nächsten Verarbeitung im Leerlauf verloren. Weitere Informationen finden Sie unter Aktualisieren von [Benutzeroberflächenobjekten](../../mfc/how-to-update-user-interface-objects.md) und [TN031: Steuerleisten.](../../mfc/tn031-control-bars.md)

Informationen zu Bitmap-Bildern und -Schaltflächen finden Sie in der [CToolBar-Übersicht](../../mfc/reference/ctoolbar-class.md) und [cToolBar::LoadBitmap](#loadbitmap).

## <a name="ctoolbarsetbuttons"></a><a name="setbuttons"></a>CToolBar::SetButtons

Diese Memberfunktion legt die Befehls-ID jeder Symbolleistenschaltfläche auf den Wert fest, der durch das entsprechende Element des *Arrays lpIDArray*angegeben wird.

```
BOOL SetButtons(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parameter

*lpIDArray*<br/>
Zeiger auf ein Array von Befehls-IDs. Es kann NULL sein, leere Schaltflächen zuzuweisen.

*nIDCount*<br/>
Anzahl der Elemente im Array, auf die von *lpIDArray*verwiesen wird.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Wenn ein Element des Arrays den Wert ID_SEPARATOR hat, wird ein Trennzeichen an der entsprechenden Position der Symbolleiste erstellt. Diese Funktion legt auch den Stil jeder Schaltfläche auf TBBS_BUTTON und den Stil jedes Trennzeichens auf TBBS_SEPARATOR fest und weist jeder Schaltfläche einen Bildindex zu. Der Bildindex gibt die Position des Bildes der Schaltfläche innerhalb der Bitmap an.

Sie müssen keine Trennzeichen in der Bitmap berücksichtigen, da diese Funktion keine Bildindizes für Trennzeichen zuweist. Wenn ihre Symbolleiste Schaltflächen an den Positionen 0, 1 und 3 und ein Trennzeichen an Position 2 enthält, werden die Bilder an den Positionen 0, 1 und 2 in der Bitmap den Schaltflächen an den Positionen 0, 1 und 3 zugewiesen.

Wenn *lpIDArray* NULL ist, weist diese Funktion Speicherplatz für die Anzahl der von *nIDCount*angegebenen Elemente zu. Verwenden Sie [SetButtonInfo,](#setbuttoninfo) um die Attribute jedes Elements festzulegen.

## <a name="ctoolbarsetbuttonstyle"></a><a name="setbuttonstyle"></a>CToolBar::SetButtonStyle

Rufen Sie diese Memberfunktion auf, um den Stil einer Schaltfläche oder eines Trennzeichens festzulegen oder Umschaltflächen zu gruppieren.

```cpp
void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Index der Schaltfläche oder des Trennzeichens, deren Informationen festgelegt werden sollen.

*nStyle*<br/>
Der Schaltflächenstil. Die folgenden Schaltflächenstile werden unterstützt:

- TBBS_BUTTON Standard-Taste (Standard)

- TBBS_SEPARATOR Separator

- TBBS_CHECKBOX Auto-Kontrollkästchen-Schaltfläche

- TBBS_GROUP Markiert den Beginn einer Gruppe von Schaltflächen

- TBBS_CHECKGROUP Markiert den Beginn einer Gruppe von Kontrollkästchen-Schaltflächen

- TBBS_DROPDOWN Erstellt eine Dropdown-Listenschaltfläche

- TBBS_AUTOSIZE Die Breite der Schaltfläche wird basierend auf dem Text der Schaltfläche und nicht auf der Größe des Bildes berechnet.

- TBBS_NOPREFIX Dem Schaltflächentext ist kein Beschleunigerpräfix zugeordnet

### <a name="remarks"></a>Bemerkungen

Der Stil einer Schaltfläche bestimmt, wie die Schaltfläche angezeigt wird und wie sie auf Benutzereingaben reagiert.

Rufen `SetButtonStyle`Sie vor dem Aufruf die [GetButtonStyle-Memberfunktion](#getbuttonstyle) auf, um die Schaltfläche oder den Trennstil abzurufen.

> [!NOTE]
> Sie können auch Schaltflächenzustände mithilfe des Parameters *nStyle* festlegen. Da die Schaltflächenzustände jedoch vom [ON_UPDATE_COMMAND_UI-Handler](message-map-macros-mfc.md#on_update_command_ui) `SetButtonStyle` gesteuert werden, geht jeder Status, den Sie verwenden, während der nächsten Verarbeitung im Leerlauf verloren. Weitere Informationen finden Sie unter Aktualisieren von [Benutzeroberflächenobjekten](../../mfc/how-to-update-user-interface-objects.md) und [TN031: Steuerleisten.](../../mfc/tn031-control-bars.md)

## <a name="ctoolbarsetbuttontext"></a><a name="setbuttontext"></a>CToolBar::SetButtonText

Rufen Sie diese Funktion auf, um den Text auf einer Schaltfläche festzulegen.

```
BOOL SetButtonText(
    int nIndex,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Index der Schaltfläche, deren Text gesetzt werden soll.

*lpszText*<br/>
Zeigt auf den Text, der auf einer Schaltfläche festgelegt werden soll.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CToolBar::GetToolBarCtrl](#gettoolbarctrl).

## <a name="ctoolbarsetheight"></a><a name="setheight"></a>CToolBar::SetHeight

Diese Memberfunktion legt die Höhe der Symbolleiste auf den in *cyHeight*angegebenen Wert in Pixel fest.

```cpp
void SetHeight(int cyHeight);
```

### <a name="parameters"></a>Parameter

*cyHeight*<br/>
Die Höhe in Pixeln der Symbolleiste.

### <a name="remarks"></a>Bemerkungen

Nachdem Sie [SetSizes](#setsizes)aufgerufen haben, verwenden Sie diese Memberfunktion, um die Standardmäßige Symbolleistenhöhe zu überschreiben. Wenn die Höhe zu klein ist, werden die Tasten unten abgeschnitten.

Wenn diese Funktion nicht aufgerufen wird, verwendet das Framework die Größe der Schaltfläche, um die Höhe der Symbolleisten zu bestimmen.

## <a name="ctoolbarsetsizes"></a><a name="setsizes"></a>CToolBar::SetSizes

Rufen Sie diese Memberfunktion auf, um die Schaltflächen der Symbolleiste auf die Größe in Pixel festzulegen, die in *sizeButton*angegeben ist.

```cpp
void SetSizes(
    SIZE sizeButton,
    SIZE sizeImage);
```

### <a name="parameters"></a>Parameter

*sizeButton*<br/>
Die Größe in Pixel jeder Schaltfläche.

*sizeImage*<br/>
Die Größe in Pixeln jedes Bildes.

### <a name="remarks"></a>Bemerkungen

Der *Parameter sizeImage* muss die Größe der Bilder in der Bitmap der Symbolleiste in Pixel enthalten. Die Abmessungen in *sizeButton* müssen ausreichen, um das Bild plus 7 Pixel extra in der Breite und 6 Pixel extra in der Höhe zu halten. Diese Funktion legt auch die Symbolleistenhöhe so fest, dass sie an die Schaltflächen passt.

Rufen Sie diese Memberfunktion nur für Symbolleisten auf, die die *Windows-Schnittstellenrichtlinien für Softwaredesign-Empfehlungen* für Schaltflächen- und Bildgrößen nicht befolgen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel STRGBARS](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel DOCKTOOL](../../overview/visual-cpp-samples.md)<br/>
[CControlBar-Klasse](../../mfc/reference/ccontrolbar-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl-Klasse](../../mfc/reference/ctoolbarctrl-class.md)<br/>
[CControlBar-Klasse](../../mfc/reference/ccontrolbar-class.md)
