---
title: CHeaderCtrl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CHeaderCtrl
- AFXCMN/CHeaderCtrl
- AFXCMN/CHeaderCtrl::CHeaderCtrl
- AFXCMN/CHeaderCtrl::ClearAllFilters
- AFXCMN/CHeaderCtrl::ClearFilter
- AFXCMN/CHeaderCtrl::Create
- AFXCMN/CHeaderCtrl::CreateDragImage
- AFXCMN/CHeaderCtrl::CreateEx
- AFXCMN/CHeaderCtrl::DeleteItem
- AFXCMN/CHeaderCtrl::DrawItem
- AFXCMN/CHeaderCtrl::EditFilter
- AFXCMN/CHeaderCtrl::GetBitmapMargin
- AFXCMN/CHeaderCtrl::GetFocusedItem
- AFXCMN/CHeaderCtrl::GetImageList
- AFXCMN/CHeaderCtrl::GetItem
- AFXCMN/CHeaderCtrl::GetItemCount
- AFXCMN/CHeaderCtrl::GetItemDropDownRect
- AFXCMN/CHeaderCtrl::GetItemRect
- AFXCMN/CHeaderCtrl::GetOrderArray
- AFXCMN/CHeaderCtrl::GetOverflowRect
- AFXCMN/CHeaderCtrl::HitTest
- AFXCMN/CHeaderCtrl::InsertItem
- AFXCMN/CHeaderCtrl::Layout
- AFXCMN/CHeaderCtrl::OrderToIndex
- AFXCMN/CHeaderCtrl::SetBitmapMargin
- AFXCMN/CHeaderCtrl::SetFilterChangeTimeout
- AFXCMN/CHeaderCtrl::SetFocusedItem
- AFXCMN/CHeaderCtrl::SetHotDivider
- AFXCMN/CHeaderCtrl::SetImageList
- AFXCMN/CHeaderCtrl::SetItem
- AFXCMN/CHeaderCtrl::SetOrderArray
helpviewer_keywords:
- CHeaderCtrl [MFC], CHeaderCtrl
- CHeaderCtrl [MFC], ClearAllFilters
- CHeaderCtrl [MFC], ClearFilter
- CHeaderCtrl [MFC], Create
- CHeaderCtrl [MFC], CreateDragImage
- CHeaderCtrl [MFC], CreateEx
- CHeaderCtrl [MFC], DeleteItem
- CHeaderCtrl [MFC], DrawItem
- CHeaderCtrl [MFC], EditFilter
- CHeaderCtrl [MFC], GetBitmapMargin
- CHeaderCtrl [MFC], GetFocusedItem
- CHeaderCtrl [MFC], GetImageList
- CHeaderCtrl [MFC], GetItem
- CHeaderCtrl [MFC], GetItemCount
- CHeaderCtrl [MFC], GetItemDropDownRect
- CHeaderCtrl [MFC], GetItemRect
- CHeaderCtrl [MFC], GetOrderArray
- CHeaderCtrl [MFC], GetOverflowRect
- CHeaderCtrl [MFC], HitTest
- CHeaderCtrl [MFC], InsertItem
- CHeaderCtrl [MFC], Layout
- CHeaderCtrl [MFC], OrderToIndex
- CHeaderCtrl [MFC], SetBitmapMargin
- CHeaderCtrl [MFC], SetFilterChangeTimeout
- CHeaderCtrl [MFC], SetFocusedItem
- CHeaderCtrl [MFC], SetHotDivider
- CHeaderCtrl [MFC], SetImageList
- CHeaderCtrl [MFC], SetItem
- CHeaderCtrl [MFC], SetOrderArray
ms.assetid: b847ac90-5fae-4a87-88e0-ca45f77b8b3b
ms.openlocfilehash: 6b5088526ad2c1f94fdc95ec3b84ab7cf64b59e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366852"
---
# <a name="cheaderctrl-class"></a>CHeaderCtrl-Klasse

Stellt die Funktionalität des allgemeinen Windows-Headersteuerelements bereit.

## <a name="syntax"></a>Syntax

```
class CHeaderCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHeaderCtrl::CHeaderCtrl](#cheaderctrl)|Erstellt ein `CHeaderCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHeaderCtrl::ClearAllFilters](#clearallfilters)|Löscht alle Filter für ein Headersteuerelement.|
|[CHeaderCtrl::ClearFilter](#clearfilter)|Löscht den Filter für ein Headersteuerelement.|
|[CHeaderCtrl::Erstellen](#create)|Erstellt ein Headersteuerelement und fügt `CHeaderCtrl` es an ein Objekt an.|
|[CHeaderCtrl::CreateDragImage](#createdragimage)|Erstellt eine transparente Version des Abbilds eines Elements innerhalb eines Kopfkopfsteuerelements.|
|[CHeaderCtrl::CreateEx](#createex)|Erstellt ein Headersteuerelement mit den angegebenen erweiterten Windows-Stilen und fügt es an ein `CListCtrl` Objekt an.|
|[CHeaderCtrl::DeleteItem](#deleteitem)|Löscht ein Element aus einem Kopfsteuerelement.|
|[CHeaderCtrl::DrawItem](#drawitem)|Zeichnet das angegebene Element eines Kopfsteuerelements.|
|[CHeaderCtrl::EditFilter](#editfilter)|Startet die Bearbeitung des angegebenen Filters eines Headersteuerelements.|
|[CHeaderCtrl::GetBitmapMargin](#getbitmapmargin)|Ruft die Breite des Rands einer Bitmap in einem Headersteuerelement ab.|
|[CHeaderCtrl::GetFocusedItem](#getfocuseditem)|Ruft den Bezeichner des Elements im aktuellen Headersteuerelement ab, das den Fokus hat.|
|[CHeaderCtrl::GetImageList](#getimagelist)|Ruft das Handle einer Bildliste ab, die zum Zeichnen von Kopfzeilenelementen in einem Kopfkopfsteuerelement verwendet wird.|
|[CHeaderCtrl::GetItem](#getitem)|Ruft Informationen zu einem Element in einem Kopfsteuerelement ab.|
|[CHeaderCtrl::GetItemCount](#getitemcount)|Ruft eine Anzahl der Elemente in einem Kopfsteuerelement ab.|
|[CHeaderCtrl::GetItemDropDownRect](#getitemdropdownrect)|Ruft die Informationen zum umgrenzenden Rechteck für die angegebene Dropdown-Schaltfläche in einem Kopfkopfsteuerelement ab.|
|[CHeaderCtrl::GetItemRect](#getitemrect)|Ruft das umgrenzte Rechteck für ein bestimmtes Element in einem Kopfsteuerelement ab.|
|[CHeaderCtrl::GetOrderArray](#getorderarray)|Ruft die Reihenfolge der Elemente in einem Headersteuerelement von links nach rechts ab.|
|[CHeaderCtrl::GetOverflowRect](#getoverflowrect)|Ruft das umlaufende Rechteck der Überlaufschaltfläche für das aktuelle Headersteuerelement ab.|
|[CHeaderCtrl::HitTest](#hittest)|Bestimmt, welches Kopfelement sich ggf. an einem angegebenen Punkt befindet.|
|[CHeaderCtrl::InsertItem](#insertitem)|Fügt ein neues Element in ein Kopfsteuerelement ein.|
|[CHeaderCtrl::Layout](#layout)|Ruft die Größe und Position eines Kopfsteuerelements innerhalb eines bestimmten Rechtecks ab.|
|[CHeaderCtrl::OrderToIndex](#ordertoindex)|Ruft den Indexwert für ein Element basierend auf seiner Reihenfolge im Headersteuerelement ab.|
|[CHeaderCtrl::SetBitmapMargin](#setbitmapmargin)|Legt die Breite des Rands einer Bitmap in einem Headersteuerelement fest.|
|[CHeaderCtrl::SetFilterChangeTimeout](#setfilterchangetimeout)|Legt das Timeoutintervall zwischen dem Zeitpunkt, zu dem eine Änderung `HDN_FILTERCHANGE` in den Filterattributen stattfindet, und der Buchung einer Benachrichtigung fest.|
|[CHeaderCtrl::SetFocusedItem](#setfocuseditem)|Legt den Fokus auf ein angegebenes Kopfelement im aktuellen Kopfsteuerelement fest.|
|[CHeaderCtrl::SetHotDivider](#sethotdivider)|Ändert die Trennlinie zwischen Kopfzeilen, um ein manuelles Ziehen und Ablegen eines Kopfkopfelements anzuzeigen.|
|[CHeaderCtrl::SetImageList](#setimagelist)|Weist einem Kopfkopfsteuerelement eine Bildliste zu.|
|[CHeaderCtrl::SetItem](#setitem)|Legt die Attribute des angegebenen Elements in einem Kopfkopfsteuerelement fest.|
|[CHeaderCtrl::SetOrderArray](#setorderarray)|Legt die Reihenfolge der Elemente von links nach rechts in einem Kopfsteuerelement fest.|

## <a name="remarks"></a>Bemerkungen

Ein Kopfzeilensteuerelement ist ein Fenster, das normalerweise über einer Reihe von Textspalten oder Zahlen positioniert wird. Es enthält einen Titel für jede Spalte und kann in Teile unterteilt werden. Der Benutzer kann die Trennwände ziehen, die die Teile trennen, um die Breite jeder Spalte festzulegen. Eine Abbildung eines Kopfsteuerelements finden Sie unter [Kopfzeilensteuerelemente](/windows/win32/Controls/header-controls).

Dieses Steuerelement (und `CHeaderCtrl` damit die Klasse) ist nur für Programme verfügbar, die unter Windows 95/98 und Windows NT Version 3.51 und höher ausgeführt werden.

Zu den für Windows 95/Internet Explorer 4.0 hinzugefügten Funktionen gehören die folgenden:

- Benutzerdefinierten Artikel.

- Kopfelement drag & Drop, zum Neuanordnen von Kopfzeilenelementen. Verwenden Sie beim Erstellen `CHeaderCtrl` des Objekts den HDS_DRAGDROP Stil.

- Kopfzeilenspaltentext wird während der Größenänderung der Spalte ständig angezeigt. Verwenden Sie den stilHDS_FULLDRAG, wenn Sie ein `CHeaderCtrl` Objekt erstellen.

- Header-Hot-Tracking, das das Kopfelement hervorhebt, wenn der Zeiger darüber schwebt. Verwenden Sie den stilHDS_HOTTRACK, wenn Sie das `CHeaderCtrl` Objekt erstellen.

- Unterstützung der Bildliste. Kopfzeilenelemente können Bilder `CImageList` enthalten, die in einem Objekt oder Text gespeichert sind.

Weitere Informationen zur `CHeaderCtrl`Verwendung von finden Sie unter [Steuerelemente](../../mfc/controls-mfc.md) und [Verwenden von CHeaderCtrl](../../mfc/using-cheaderctrl.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHeaderCtrl`

## <a name="requirements"></a>Anforderungen

**Header:** afxcmn.h

## <a name="cheaderctrlcheaderctrl"></a><a name="cheaderctrl"></a>CHeaderCtrl::CHeaderCtrl

Erstellt ein `CHeaderCtrl`-Objekt.

```
CHeaderCtrl();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CHeaderCtrl#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_1.cpp)]

## <a name="cheaderctrlclearallfilters"></a><a name="clearallfilters"></a>CHeaderCtrl::ClearAllFilters

Löscht alle Filter für ein Headersteuerelement.

```
BOOL ClearAllFilters();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode implementiert das Verhalten der Win32-Meldung [HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter) mit einem Spaltenwert von -1, wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]

## <a name="cheaderctrlclearfilter"></a><a name="clearfilter"></a>CHeaderCtrl::ClearFilter

Löscht den Filter für ein Headersteuerelement.

```
BOOL ClearFilter(int nColumn);
```

### <a name="parameters"></a>Parameter

*nColumn*<br/>
Spaltenwert, der angibt, welcher Filter entfernt werden soll.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode implementiert das Verhalten der [HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter)Win32-HDM_CLEARFILTER , wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CHeaderCtrl#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]

## <a name="cheaderctrlcreate"></a><a name="create"></a>CHeaderCtrl::Erstellen

Erstellt ein Headersteuerelement und fügt `CHeaderCtrl` es an ein Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwStyle*<br/>
Gibt den Stil des Headersteuerelements an. Eine Beschreibung der Headersteuerungsstile finden Sie unter [Headersteuerungsstile](/windows/win32/Controls/header-control-styles) im Windows SDK.

*Rect*<br/>
Gibt die Größe und Position des Kopfsteuerelements an. Dabei kann es sich entweder um ein [CRect-Objekt](../../atl-mfc-shared/reference/crect-class.md) oder eine [RECT-Struktur](/previous-versions/dd162897\(v=vs.85\)) handelt.

*pParentWnd*<br/>
Gibt das übergeordnete Fenster des Headersteuerelements an, in der Regel eine `CDialog`. Es darf nicht NULL sein.

*nID*<br/>
Gibt die ID des Headersteuerelements an.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Initialisierung erfolgreich war; andernfalls Null.

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CHeaderCtrl` ein Objekt in zwei Schritten. Rufen Sie zunächst den Konstruktor auf, und rufen Sie dann auf, `Create`das das Headersteuerelement erstellt und an das `CHeaderCtrl` Objekt anfügt.

Zusätzlich zu den Headersteuerelementstilen können Sie die folgenden allgemeinen Steuerelementstile verwenden, um zu bestimmen, wie die Kopfsteuerelementposition positioniert und die Größe selbst geändert wird (weitere Informationen finden Sie unter [Allgemeine Steuerelementstile):](/windows/win32/Controls/common-control-styles)

- CCS_BOTTOM Bewirkt, dass sich das Steuerelement am unteren Rand des Clientbereichs des übergeordneten Fensters positioniert, und legt fest, dass die Breite mit der Breite des übergeordneten Fensters identisch ist.

- CCS_NODIVIDER Verhindert, dass oben im Steuerelement ein Zwei-Pixel-Highlight gezeichnet wird.

- CCS_NOMOVEY Bewirkt, dass die Größe des Steuerelements als Antwort auf eine WM_SIZE Nachricht horizontal, aber nicht vertikal geändert wird. Wenn der CCS_NORESIZE-Stil verwendet wird, gilt dieser Stil nicht. Headersteuerelemente haben standardmäßig diesen Stil.

- CCS_NOPARENTALIGN Verhindert, dass das Steuerelement automatisch an den oberen oder unteren Rand des übergeordneten Fensters wechselt. Stattdessen behält das Steuerelement seine Position innerhalb des übergeordneten Fensters bei, obwohl sich die Größe des übergeordneten Fensters ändert. Wenn auch der CCS_TOP- oder CCS_BOTTOM-Stil verwendet wird, wird die Höhe an den Standardwert angepasst, Position und Breite bleiben jedoch unverändert.

- CCS_NORESIZE Verhindert, dass das Steuerelement die Standardbreite und -höhe verwendet, wenn die Anfangsgröße oder eine neue Größe eingestellt wird. Stattdessen verwendet das Steuerelement die Breite und Höhe, die in der Anforderung für die Erstellung oder Größe angegeben sind.

- CCS_TOP Bewirkt, dass sich das Steuerelement am oberen Rand des Clientbereichs des übergeordneten Fensters positioniert, und legt fest, dass die Breite mit der Breite des übergeordneten Fensters identisch ist.

Sie können auch die folgenden Fensterstile auf ein Kopfkopfsteuerelement anwenden (weitere Informationen finden Sie unter [Fensterformatvorlagen):](../../mfc/reference/styles-used-by-mfc.md#window-styles)

- WS_CHILD Erstellt ein untergeordnetes Fenster. Kann nicht mit dem WS_POPUP-Stil verwendet werden.

- WS_VISIBLE Erstellt ein Fenster, das zunächst sichtbar ist.

- WS_DISABLED Erstellt ein Fenster, das zunächst deaktiviert ist.

- WS_GROUP Gibt das erste Steuerelement einer Gruppe von Steuerelementen an, in der der Benutzer mit den Pfeiltasten von einem Steuerelement zum nächsten wechseln kann. Alle Steuerelemente, die nach dem ersten Steuerelement mit dem WS_GROUP-Stil definiert wurden, gehören zur gleichen Gruppe. Das nächste Steuerelement mit dem Stil WS_GROUP beendet die Stilgruppe und startet die nächste Gruppe (d. h. eine Gruppe endet an der Stelle, an der die nächste beginnt).

- WS_TABSTOP Gibt eines von einer beliebigen Anzahl von Steuerelementen an, durch die der Benutzer mithilfe der TAB-Taste wechseln kann. Mit der TAB-TASTE wechselt der Benutzer zum nächsten Steuerelement, das durch den WS_TABSTOP-Stil angegeben ist.

Wenn Sie erweiterte Fensterstile mit Ihrem Steuerelement verwenden `Create`möchten, rufen Sie [CreateEx](#createex) anstelle von auf.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]

## <a name="cheaderctrlcreateex"></a><a name="createex"></a>CHeaderCtrl::CreateEx

Erstellt ein Steuerelement (ein untergeordnetes Fenster) und ordnen es dem `CHeaderCtrl` Objekt zu.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwExStyle*<br/>
Gibt den erweiterten Stil des zu erstellenden Steuerelements an. Eine Liste der erweiterten Windows-Stile finden Sie im *dwExStyle-Parameter* für [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) im Windows SDK.

*dwStyle*<br/>
Der Stil des Headersteuerelements. Eine Beschreibung der Headersteuerungsstile finden Sie unter [Headersteuerungsstile](/windows/win32/Controls/header-control-styles) im Windows SDK. Eine Liste zusätzlicher Formatvorlagen finden Sie unter [Erstellen.](#create)

*Rect*<br/>
Ein Verweis auf eine [RECT-Struktur,](/previous-versions/dd162897\(v=vs.85\)) die die Größe und Position des zu erstellenden Fensters in den Clientkoordinaten von *pParentWnd*beschreibt.

*pParentWnd*<br/>
Ein Zeiger auf das Fenster, das das übergeordnete Steuerelement ist.

*nID*<br/>
Die untergeordnete Fenster-ID des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Verwenden `CreateEx` Sie, anstatt `Create` erweiterte Windows-Formatvorlagen anzuwenden, die durch das Windows-Vorwort für erweiterte Stile **WS_EX_** angegeben werden.

## <a name="cheaderctrlcreatedragimage"></a><a name="createdragimage"></a>CHeaderCtrl::CreateDragImage

Erstellt eine transparente Version des Abbilds eines Elements innerhalb eines Kopfkopfsteuerelements.

```
CImageList* CreateDragImage(int nIndex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der nullbasierte Index des Elements innerhalb des Kopfsteuerelements. Das diesem Element zugewiesene Bild ist die Grundlage für das transparente Bild.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CImageList-Objekt,](../../mfc/reference/cimagelist-class.md) wenn erfolgreich; andernfalls NULL. Die zurückgegebene Liste enthält nur ein Bild.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [HDM_CREATEDRAGIMAGE](/windows/win32/Controls/hdm-createdragimage)Win32-HDM_CREATEDRAGIMAGE , wie im Windows SDK beschrieben. Sie wird bereitgestellt, um das Ziehen und Ablegen von Kopfzeilenzugaben zu unterstützen.

Das `CImageList` Objekt, auf das die zurückgegebenen Zeigerzeiger verweisen, ist ein temporäres Objekt und wird bei der nächsten Verarbeitung im Leerlauf gelöscht.

## <a name="cheaderctrldeleteitem"></a><a name="deleteitem"></a>CHeaderCtrl::DeleteItem

Löscht ein Element aus einem Kopfsteuerelement.

```
BOOL DeleteItem(int nPos);
```

### <a name="parameters"></a>Parameter

*Npos*<br/>
Gibt den nullbasierten Index des zu löschenden Elements an.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CHeaderCtrl#5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]

## <a name="cheaderctrldrawitem"></a><a name="drawitem"></a>CHeaderCtrl::DrawItem

Wird vom Framework aufgerufen, wenn sich ein visueller Aspekt eines Besitzerzeichnungsheadersteuerelements ändert.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parameter

*lpDrawItemStruct*<br/>
Ein Zeiger auf eine [DRAWITEMSTRUCT-Struktur,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) die das zu malende Element beschreibt.

### <a name="remarks"></a>Bemerkungen

Das `itemAction` Element `DRAWITEMSTRUCT` der Struktur definiert die Zeichnungsaktion, die ausgeführt werden soll.

Standardmäßig führt diese Memberfunktion nichts aus. Überschreiben Sie diese Memberfunktion, um `CHeaderCtrl` die Zeichnung für ein Besitzerzeichnungsobjekt zu implementieren.

Die Anwendung sollte alle GDI-Objekte (Graphics Device Interface) wiederherstellen, die für den in *lpDrawItemStruct* bereitgestellten Anzeigekontext ausgewählt wurden, bevor diese Memberfunktion beendet wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CHeaderCtrl#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]

## <a name="cheaderctrleditfilter"></a><a name="editfilter"></a>CHeaderCtrl::EditFilter

Beginnt mit der Bearbeitung des angegebenen Filters eines Headersteuerelements.

```
BOOL EditFilter(
    int nColumn,
    BOOL bDiscardChanges);
```

### <a name="parameters"></a>Parameter

*nColumn*<br/>
Die zu bearbeitende Spalte.

*bDiscardChanges*<br/>
Ein Wert, der angibt, wie die Bearbeitungsänderungen des Benutzers behandelt werden sollen, wenn der Benutzer gerade den Filter bearbeitet, wenn die [HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter) Nachricht gesendet wird.

Geben Sie TRUE an, um die vom Benutzer vorgenommenen Änderungen zu verwerfen, oder FALSE, um die vom Benutzer vorgenommenen Änderungen zu akzeptieren.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode implementiert das Verhalten der [HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter)Win32-HDM_EDITFILTER , wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]

## <a name="cheaderctrlgetbitmapmargin"></a><a name="getbitmapmargin"></a>CHeaderCtrl::GetBitmapMargin

Ruft die Breite des Rands einer Bitmap in einem Headersteuerelement ab.

```
int GetBitmapMargin() const;
```

### <a name="return-value"></a>Rückgabewert

Die Breite des Bitmaprands in Pixel.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [HDM_GETBITMAPMARGIN](/windows/win32/Controls/hdm-getbitmapmargin)Win32-HDM_GETBITMAPMARGIN , wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CHeaderCtrl#8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]

## <a name="cheaderctrlgetfocuseditem"></a><a name="getfocuseditem"></a>CHeaderCtrl::GetFocusedItem

Ruft den Index des Elements ab, das den Fokus im aktuellen Headersteuerelement hat.

```
int GetFocusedItem() const;
```

### <a name="return-value"></a>Rückgabewert

Der nullbasierte Index des Kopfelements, der den Fokus hat.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [HDM_GETFOCUSEDITEM](/windows/win32/Controls/hdm-getfocuseditem) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird `m_headerCtrl`die Variable , definiert, die für den Zugriff auf das aktuelle Headersteuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel `SetFocusedItem` `GetFocusedItem` werden die Methoden veranschaulicht. In einem früheren Abschnitt des Codes haben wir ein Headersteuerelement mit fünf Spalten erstellt. Sie können jedoch ein Spaltentrennzeichen ziehen, sodass die Spalte nicht sichtbar ist. Im folgenden Beispiel wird die letzte Spaltenüberschrift als Fokuselement festgelegt und dann bestätigt.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

## <a name="cheaderctrlgetimagelist"></a><a name="getimagelist"></a>CHeaderCtrl::GetImageList

Ruft das Handle einer Bildliste ab, die zum Zeichnen von Kopfzeilenelementen in einem Kopfkopfsteuerelement verwendet wird.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CImageList-Objekt.](../../mfc/reference/cimagelist-class.md)

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [HDM_GETIMAGELIST](/windows/win32/Controls/hdm-getimagelist)Win32-HDM_GETIMAGELIST , wie im Windows SDK beschrieben. Das `CImageList` Objekt, auf das die zurückgegebenen Zeigerzeiger verweisen, ist ein temporäres Objekt und wird bei der nächsten Verarbeitung im Leerlauf gelöscht.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CHeaderCtrl#9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]

## <a name="cheaderctrlgetitem"></a><a name="getitem"></a>CHeaderCtrl::GetItem

Ruft Informationen zu einem Kopfsteuerelementelement ab.

```
BOOL GetItem(
    int nPos,
    HDITEM* pHeaderItem) const;
```

### <a name="parameters"></a>Parameter

*Npos*<br/>
Gibt den nullbasierten Index des abzurufenden Elements an.

*pHeaderItem*<br/>
Zeiger auf eine [HDITEM-Struktur,](/windows/win32/api/commctrl/ns-commctrl-hditemw) die das neue Element empfängt. Diese Struktur wird `InsertItem` mit `SetItem` den und Memberfunktionen verwendet. Alle im `mask` Element gesetzten Flags stellen sicher, dass die Werte in den entsprechenden Elementen bei der Rückgabe ordnungsgemäß ausgefüllt werden. Wenn `mask` das Element auf Null gesetzt ist, sind Werte in den anderen Strukturelementen bedeutungslos.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CHeaderCtrl#10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]

## <a name="cheaderctrlgetitemcount"></a><a name="getitemcount"></a>CHeaderCtrl::GetItemCount

Ruft eine Anzahl der Elemente in einem Kopfsteuerelement ab.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Rückgabewert

Anzahl der Headersteuerelemente, falls erfolgreich; ansonsten - 1.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CHeaderCtrl::DeleteItem](#deleteitem).

## <a name="cheaderctrlgetitemdropdownrect"></a><a name="getitemdropdownrect"></a>CHeaderCtrl::GetItemDropDownRect

Ruft das umschließende Rechteck der Dropdown-Schaltfläche für ein Kopfelement im aktuellen Kopfkopfsteuerelement ab.

```
BOOL GetItemDropDownRect(
    int iItem,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*iItem*|[in] Nullbasierter Index eines Kopfelements, dessen Stil HDF_SPLITBUTTON ist. Weitere Informationen finden `fmt` Sie im Member der [HDITEM-Struktur.](/windows/win32/api/commctrl/ns-commctrl-hditemw)|
|*lpRect*|[out] Zeiger auf eine [RECT-Struktur,](/previous-versions/dd162897\(v=vs.85\)) um die umgrenzenden Rechteckinformationen zu empfangen.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Funktion erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [HDM_GETITEMDROPDOWNRECT](/windows/win32/Controls/hdm-getitemdropdownrect) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird `m_headerCtrl`die Variable , definiert, die für den Zugriff auf das aktuelle Headersteuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel `GetItemDropDownRect` wird die Methode veranschaulicht. In einem früheren Abschnitt des Codes haben wir ein Headersteuerelement mit fünf Spalten erstellt. Im folgenden Codebeispiel wird ein 3D-Rechteck um die Position in der ersten Spalte gezeichnet, die für die Dropdown-Schaltfläche "Header" reserviert ist.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]

## <a name="cheaderctrlgetitemrect"></a><a name="getitemrect"></a>CHeaderCtrl::GetItemRect

Ruft das umgrenzte Rechteck für ein bestimmtes Element in einem Kopfsteuerelement ab.

```
BOOL GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der nullbasierte Index des Kopfsteuerelementselements.

*lpRect*<br/>
Ein Zeiger auf die Adresse einer [RECT-Struktur,](/previous-versions/dd162897\(v=vs.85\)) die die umgrenzenden Rechteckinformationen empfängt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Methode implementiert das Verhalten der [HDM_GETITEMRECT](/windows/win32/Controls/hdm-getitemrect)Win32-HDM_GETITEMRECT , wie im Windows SDK beschrieben.

## <a name="cheaderctrlgetorderarray"></a><a name="getorderarray"></a>CHeaderCtrl::GetOrderArray

Ruft die Reihenfolge der Elemente in einem Headersteuerelement von links nach rechts ab.

```
BOOL GetOrderArray(
    LPINT piArray,
    int iCount);
```

### <a name="parameters"></a>Parameter

*piArray*<br/>
Ein Zeiger auf die Adresse eines Puffers, der die Indexwerte der Elemente im Headersteuerelement in der Reihenfolge empfängt, in der sie von links nach rechts angezeigt werden.

*iCount*<br/>
Die Anzahl der Kopfsteuerelementelemente. Muss nicht negativ sein.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [HDM_GETORDERARRAY](/windows/win32/Controls/hdm-getorderarray)Win32-HDM_GETORDERARRAY , wie im Windows SDK beschrieben. Sie wird bereitgestellt, um die Bestellung von Kopfzeilen zu unterstützen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]

## <a name="cheaderctrlgetoverflowrect"></a><a name="getoverflowrect"></a>CHeaderCtrl::GetOverflowRect

Ruft das umlaufende Rechteck der Überlaufschaltfläche des aktuellen Headersteuerelements ab.

```
BOOL GetOverflowRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*lpRect*|[out] Zeiger auf eine [RECT-Struktur,](/previous-versions/dd162897\(v=vs.85\)) die die umgrenzenden Rechteckinformationen empfängt.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Funktion erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Wenn das Kopfkopfsteuerelement mehr Elemente enthält, als gleichzeitig angezeigt werden können, kann das Steuerelement eine Überlaufschaltfläche anzeigen, die zu Elementen scrollt, die nicht sichtbar sind. Das Headersteuerelement muss über die HDS_OVERFLOW- und HDF_SPLITBUTTON-Stile verfügen, um die Überlaufschaltfläche anzuzeigen. Das umschließende Rechteck umschließt die Überlaufschaltfläche und ist nur vorhanden, wenn die Überlaufschaltfläche angezeigt wird. Weitere Informationen finden Sie unter [Headersteuerungsstile](/windows/win32/Controls/header-control-styles).

Diese Methode sendet die [HDM_GETOVERFLOWRECT](/windows/win32/Controls/hdm-getoverflowrect) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird `m_headerCtrl`die Variable , definiert, die für den Zugriff auf das aktuelle Headersteuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel `GetOverflowRect` wird die Methode veranschaulicht. In einem früheren Abschnitt des Codes haben wir ein Headersteuerelement mit fünf Spalten erstellt. Sie können jedoch ein Spaltentrennzeichen ziehen, sodass die Spalte nicht sichtbar ist. Wenn einige Spalten nicht sichtbar sind, zeichnet das Kopfsteuerelement eine Überlaufschaltfläche. Im folgenden Codebeispiel wird ein 3D-Rechteck um die Position der Überlaufschaltfläche gezeichnet.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]

## <a name="cheaderctrlhittest"></a><a name="hittest"></a>CHeaderCtrl::HitTest

Bestimmt, welches Kopfelement sich ggf. an einem angegebenen Punkt befindet.

```
int HitTest(LPHDHITTESTINFO* phdhti);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*phdhti*|[in, out] Zeiger auf eine [HDHITTESTINFO-Struktur,](/windows/win32/api/commctrl/ns-commctrl-hdhittestinfo) die den zu testenden Punkt angibt und die Testergebnisse empfängt.|

### <a name="return-value"></a>Rückgabewert

Der nullbasierte Index des Kopfelements, falls vorhanden, an der angegebenen Position; andernfalls -1.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [HDM_HITTEST](/windows/win32/Controls/hdm-hittest) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird `m_headerCtrl`die Variable , definiert, die für den Zugriff auf das aktuelle Headersteuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel `HitTest` wird die Methode veranschaulicht. In einem früheren Abschnitt dieses Codebeispiels haben wir ein Headersteuerelement mit fünf Spalten erstellt. Sie können jedoch ein Spaltentrennzeichen ziehen, sodass die Spalte nicht sichtbar ist. In diesem Beispiel wird der Index der Spalte angezeigt, wenn er sichtbar ist, und -1, wenn die Spalte nicht sichtbar ist.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]

## <a name="cheaderctrlinsertitem"></a><a name="insertitem"></a>CHeaderCtrl::InsertItem

Fügt ein neues Element in ein Kopfsteuerelement am angegebenen Index ein.

```
int InsertItem(
    int nPos,
    HDITEM* phdi);
```

### <a name="parameters"></a>Parameter

*Npos*<br/>
Der nullbasierte Index des einzufügenden Elements. Wenn der Wert Null ist, wird das Element am Anfang des Kopfsteuerelements eingefügt. Wenn der Wert größer als der Maximalwert ist, wird das Element am Ende des Kopfsteuerelements eingefügt.

*phdi*<br/>
Zeiger auf eine [HDITEM-Struktur,](/windows/win32/api/commctrl/ns-commctrl-hditemw) die Informationen über das einzufügende Element enthält.

### <a name="return-value"></a>Rückgabewert

Index des neuen Elements, falls erfolgreich; ansonsten - 1.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]

## <a name="cheaderctrllayout"></a><a name="layout"></a>CHeaderCtrl::Layout

Ruft die Größe und Position eines Kopfsteuerelements innerhalb eines bestimmten Rechtecks ab.

```
BOOL Layout(HDLAYOUT* pHeaderLayout);
```

### <a name="parameters"></a>Parameter

*pHeaderLayout*<br/>
Zeiger auf eine [HDLAYOUT-Struktur,](/windows/win32/api/commctrl/ns-commctrl-hdlayout) die Informationen enthält, die zum Festlegen der Größe und Position eines Kopfsteuerelements verwendet werden.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird verwendet, um die geeigneten Dimensionen für ein neues Kopfsteuerelement zu bestimmen, das das angegebene Rechteck belegen soll.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]

## <a name="cheaderctrlordertoindex"></a><a name="ordertoindex"></a>CHeaderCtrl::OrderToIndex

Ruft den Indexwert für ein Element basierend auf seiner Reihenfolge im Headersteuerelement ab.

```
int OrderToIndex(int nOrder) const;
```

### <a name="parameters"></a>Parameter

*nOrder*<br/>
Die nullbasierte Reihenfolge, die das Element im Kopfsteuerelement von links nach rechts angezeigt wird.

### <a name="return-value"></a>Rückgabewert

Der Index des Elements, basierend auf seiner Reihenfolge im Kopfsteuerelement. Der Index zählt von links nach rechts, beginnend mit 0.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [HDM_ORDERTOINDEX](/windows/win32/controls/hdm-ordertoindex)Win32-HDM_ORDERTOINDEX , wie im Windows SDK beschrieben. Sie wird bereitgestellt, um die Bestellung von Kopfzeilen zu unterstützen.

## <a name="cheaderctrlsetbitmapmargin"></a><a name="setbitmapmargin"></a>CHeaderCtrl::SetBitmapMargin

Legt die Breite des Rands einer Bitmap in einem Headersteuerelement fest.

```
int SetBitmapMargin(int nWidth);
```

### <a name="parameters"></a>Parameter

*nWidth*<br/>
Breite (in Pixel angegeben) des Rands, der eine Bitmap innerhalb eines vorhandenen Headersteuerelements umgibt.

### <a name="return-value"></a>Rückgabewert

Die Breite des Bitmaprands in Pixel.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der Win32-Meldung [HDM_SETBITMAPMARGIN](/windows/win32/Controls/hdm-setbitmapmargin), wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]

## <a name="cheaderctrlsetfilterchangetimeout"></a><a name="setfilterchangetimeout"></a>CHeaderCtrl::SetFilterChangeTimeout

Legt das Timeoutintervall zwischen dem Zeitpunkt, zu dem eine Änderung in den Filterattributen stattfindet, und der Buchung einer [HDN_FILTERCHANGE](/windows/win32/Controls/hdn-filterchange) Benachrichtigung fest.

```
int SetFilterChangeTimeout(DWORD dwTimeOut);
```

### <a name="parameters"></a>Parameter

*dwTimeOut*<br/>
Timeoutwert in Millisekunden.

### <a name="return-value"></a>Rückgabewert

Der Index des zu ändernden Filtersteuerelements.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [HDM_SETFILTERCHANGETIMEOUT](/windows/win32/Controls/hdm-setfilterchangetimeout)Win32-HDM_SETFILTERCHANGETIMEOUT , wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]

## <a name="cheaderctrlsetfocuseditem"></a><a name="setfocuseditem"></a>CHeaderCtrl::SetFocusedItem

Legt den Fokus auf ein angegebenes Kopfelement im aktuellen Kopfsteuerelement fest.

```
BOOL SetFocusedItem(int iItem);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*iItem*|[in] Nullbasierter Index eines Kopfelements.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [HDM_SETFOCUSEDITEM](/windows/win32/Controls/hdm-setfocuseditem) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird `m_headerCtrl`die Variable , definiert, die für den Zugriff auf das aktuelle Headersteuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel `SetFocusedItem` `GetFocusedItem` werden die Methoden veranschaulicht. In einem früheren Abschnitt des Codes haben wir ein Headersteuerelement mit fünf Spalten erstellt. Sie können jedoch ein Spaltentrennzeichen ziehen, sodass die Spalte nicht sichtbar ist. Im folgenden Beispiel wird die letzte Spaltenüberschrift als Fokuselement festgelegt und dann bestätigt.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

## <a name="cheaderctrlsethotdivider"></a><a name="sethotdivider"></a>CHeaderCtrl::SetHotDivider

Ändert die Trennlinie zwischen Kopfzeilen, um ein manuelles Ziehen und Ablegen eines Kopfkopfelements anzuzeigen.

```
int SetHotDivider(CPoint pt);
int SetHotDivider(int nIndex);
```

### <a name="parameters"></a>Parameter

*Pt*<br/>
Die Position des Zeigers. Das Headersteuerelement hebt den entsprechenden Teiler basierend auf der Position des Zeigers hervor.

*nIndex*<br/>
Der Index der hervorgehobenen Trennwand.

### <a name="return-value"></a>Rückgabewert

Der Index der hervorgehobenen Trennwand.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der Win32-Meldung [HDM_SETHOTDIVIDER](/windows/win32/Controls/hdm-sethotdivider), wie im Windows SDK beschrieben. Sie wird bereitgestellt, um das Ziehen und Ablegen von Kopfzeilenzugaben zu unterstützen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]

## <a name="cheaderctrlsetimagelist"></a><a name="setimagelist"></a>CHeaderCtrl::SetImageList

Weist einem Kopfkopfsteuerelement eine Bildliste zu.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parameter

*pImageList*<br/>
Ein Zeiger auf `CImageList` ein Objekt, das die Bildliste enthält, die dem Kopfsteuerelement zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das [CImageList-Objekt,](../../mfc/reference/cimagelist-class.md) das zuvor dem Headersteuerelement zugewiesen wurde.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [HDM_SETIMAGELIST](/windows/win32/Controls/hdm-setimagelist)Win32-HDM_SETIMAGELIST , wie im Windows SDK beschrieben. Das `CImageList` Objekt, auf das die zurückgegebenen Zeigerzeiger verweisen, ist ein temporäres Objekt und wird bei der nächsten Verarbeitung im Leerlauf gelöscht.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CHeaderCtrl::GetImageList](#getimagelist).

## <a name="cheaderctrlsetitem"></a><a name="setitem"></a>CHeaderCtrl::SetItem

Legt die Attribute des angegebenen Elements in einem Kopfkopfsteuerelement fest.

```
BOOL SetItem(
    int nPos,
    HDITEM* pHeaderItem);
```

### <a name="parameters"></a>Parameter

*Npos*<br/>
Der nullbasierte Index des zu bearbeitenden Elements.

*pHeaderItem*<br/>
Zeiger auf eine [HDITEM-Struktur,](/windows/win32/api/commctrl/ns-commctrl-hditemw) die Informationen zum neuen Element enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CHeaderCtrl::GetItem](#getitem).

## <a name="cheaderctrlsetorderarray"></a><a name="setorderarray"></a>CHeaderCtrl::SetOrderArray

Legt die Reihenfolge der Elemente von links nach rechts in einem Kopfsteuerelement fest.

```
BOOL SetOrderArray(
    int iCount,
    LPINT piArray);
```

### <a name="parameters"></a>Parameter

*iCount*<br/>
Die Anzahl der Kopfsteuerelementelemente.

*piArray*<br/>
Ein Zeiger auf die Adresse eines Puffers, der die Indexwerte der Elemente im Headersteuerelement in der Reihenfolge empfängt, in der sie von links nach rechts angezeigt werden.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten des Win32-Makros [HDM_SETORDERARRAY](/windows/win32/Controls/hdm-setorderarray), wie im Windows SDK beschrieben. Sie wird bereitgestellt, um die Bestellung von Kopfzeilen zu unterstützen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CHeaderCtrl::GetOrderArray](#getorderarray).

## <a name="see-also"></a>Siehe auch

[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CTabCtrl-Klasse](../../mfc/reference/ctabctrl-class.md)<br/>
[CListCtrl-Klasse](../../mfc/reference/clistctrl-class.md)<br/>
[CImageList-Klasse](../../mfc/reference/cimagelist-class.md)
