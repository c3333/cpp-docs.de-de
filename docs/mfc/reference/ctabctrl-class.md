---
title: CTabCtrl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CTabCtrl
- AFXCMN/CTabCtrl
- AFXCMN/CTabCtrl::CTabCtrl
- AFXCMN/CTabCtrl::AdjustRect
- AFXCMN/CTabCtrl::Create
- AFXCMN/CTabCtrl::CreateEx
- AFXCMN/CTabCtrl::DeleteAllItems
- AFXCMN/CTabCtrl::DeleteItem
- AFXCMN/CTabCtrl::DeselectAll
- AFXCMN/CTabCtrl::DrawItem
- AFXCMN/CTabCtrl::GetCurFocus
- AFXCMN/CTabCtrl::GetCurSel
- AFXCMN/CTabCtrl::GetExtendedStyle
- AFXCMN/CTabCtrl::GetImageList
- AFXCMN/CTabCtrl::GetItem
- AFXCMN/CTabCtrl::GetItemCount
- AFXCMN/CTabCtrl::GetItemRect
- AFXCMN/CTabCtrl::GetItemState
- AFXCMN/CTabCtrl::GetRowCount
- AFXCMN/CTabCtrl::GetToolTips
- AFXCMN/CTabCtrl::HighlightItem
- AFXCMN/CTabCtrl::HitTest
- AFXCMN/CTabCtrl::InsertItem
- AFXCMN/CTabCtrl::RemoveImage
- AFXCMN/CTabCtrl::SetCurFocus
- AFXCMN/CTabCtrl::SetCurSel
- AFXCMN/CTabCtrl::SetExtendedStyle
- AFXCMN/CTabCtrl::SetImageList
- AFXCMN/CTabCtrl::SetItem
- AFXCMN/CTabCtrl::SetItemExtra
- AFXCMN/CTabCtrl::SetItemSize
- AFXCMN/CTabCtrl::SetItemState
- AFXCMN/CTabCtrl::SetMinTabWidth
- AFXCMN/CTabCtrl::SetPadding
- AFXCMN/CTabCtrl::SetToolTips
helpviewer_keywords:
- CTabCtrl [MFC], CTabCtrl
- CTabCtrl [MFC], AdjustRect
- CTabCtrl [MFC], Create
- CTabCtrl [MFC], CreateEx
- CTabCtrl [MFC], DeleteAllItems
- CTabCtrl [MFC], DeleteItem
- CTabCtrl [MFC], DeselectAll
- CTabCtrl [MFC], DrawItem
- CTabCtrl [MFC], GetCurFocus
- CTabCtrl [MFC], GetCurSel
- CTabCtrl [MFC], GetExtendedStyle
- CTabCtrl [MFC], GetImageList
- CTabCtrl [MFC], GetItem
- CTabCtrl [MFC], GetItemCount
- CTabCtrl [MFC], GetItemRect
- CTabCtrl [MFC], GetItemState
- CTabCtrl [MFC], GetRowCount
- CTabCtrl [MFC], GetToolTips
- CTabCtrl [MFC], HighlightItem
- CTabCtrl [MFC], HitTest
- CTabCtrl [MFC], InsertItem
- CTabCtrl [MFC], RemoveImage
- CTabCtrl [MFC], SetCurFocus
- CTabCtrl [MFC], SetCurSel
- CTabCtrl [MFC], SetExtendedStyle
- CTabCtrl [MFC], SetImageList
- CTabCtrl [MFC], SetItem
- CTabCtrl [MFC], SetItemExtra
- CTabCtrl [MFC], SetItemSize
- CTabCtrl [MFC], SetItemState
- CTabCtrl [MFC], SetMinTabWidth
- CTabCtrl [MFC], SetPadding
- CTabCtrl [MFC], SetToolTips
ms.assetid: 42e4aff6-46ae-4b2c-beaa-d1dce8d82138
ms.openlocfilehash: 42d4b24222b1760bc418e904881edb2bb0e5a1f4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752309"
---
# <a name="ctabctrl-class"></a>CTabCtrl-Klasse

Stellt die Funktionalität des allgemeinen Windows-Registerkarten-Steuerelements bereit.

## <a name="syntax"></a>Syntax

```
class CTabCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTabCtrl::CTabCtrl](#ctabctrl)|Erstellt ein `CTabCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTabCtrl::AdjustRect](#adjustrect)|Berechnet den Anzeigebereich eines Registerkartensteuerelements mit einem Fensterrechteck oder berechnet das Fensterrechteck, das einem bestimmten Anzeigebereich entspricht.|
|[CTabCtrl::Erstellen](#create)|Erstellt ein Registerkartensteuerelement und fügt es `CTabCtrl` an eine Instanz eines Objekts an.|
|[CTabCtrl::CreateEx](#createex)|Erstellt ein Registerkartensteuerelement mit den angegebenen erweiterten Windows-Stilen und fügt es an eine Instanz eines `CTabCtrl` Objekts an.|
|[CTabCtrl::DeleteAllItems](#deleteallitems)|Entfernt alle Elemente aus einem Registerkartensteuerelement.|
|[CTabCtrl::DeleteItem](#deleteitem)|Entfernt ein Element aus einem Registerkartensteuerelement.|
|[CTabCtrl::DeselectAlle](#deselectall)|Setzt Elemente in einem Registerkartensteuerelement zurück und löscht alle, die gedrückt wurden.|
|[CTabCtrl::DrawItem](#drawitem)|Zeichnet ein angegebenes Element eines Registerkartensteuerelements.|
|[CTabCtrl::GetCurFocus](#getcurfocus)|Ruft die Registerkarte mit dem aktuellen Fokus eines Registerkartensteuerelements ab.|
|[CTabCtrl::GetCurSel](#getcursel)|Bestimmt die aktuell ausgewählte Registerkarte in einem Registerkartensteuerelement.|
|[CTabCtrl::GetExtendedStyle](#getextendedstyle)|Ruft die erweiterten Stile ab, die derzeit für das Registerkartensteuerelement verwendet werden.|
|[CTabCtrl::GetImageList](#getimagelist)|Ruft die Bildliste ab, die einem Registerkartensteuerelement zugeordnet ist.|
|[CTabCtrl::GetItem](#getitem)|Ruft Informationen zu einer Registerkarte in einem Registerkartensteuerelement ab.|
|[CTabCtrl::GetItemCount](#getitemcount)|Ruft die Anzahl der Registerkarten im Registerkartensteuerelement ab.|
|[CTabCtrl::GetItemRect](#getitemrect)|Ruft das umgrenzende Rechteck für eine Registerkarte in einem Registerkartensteuerelement ab.|
|[CTabCtrl::GetItemState](#getitemstate)|Ruft den Status des angegebenen Registerkartensteuerelements ab.|
|[CTabCtrl::GetRowCount](#getrowcount)|Ruft die aktuelle Anzahl von Zeilen von Registerkarten in einem Registerkartensteuerelement ab.|
|[CTabCtrl::GetToolTipps](#gettooltips)|Ruft das Handle des QuickInfo-Steuerelements ab, das einem Registerkartensteuerelement zugeordnet ist.|
|[CTabCtrl::HighlightItem](#highlightitem)|Legt den Hervorhebungsstatus eines Registerkartenelements fest.|
|[CTabCtrl::HitTest](#hittest)|Bestimmt, welche Registerkarte sich ggf. an einer angegebenen Bildschirmposition befindet.|
|[CTabCtrl::InsertItem](#insertitem)|Fügt eine neue Registerkarte in ein Registerkartensteuerelement ein.|
|[CTabCtrl::RemoveImage](#removeimage)|Entfernt ein Bild aus der Bildliste eines Registerkartensteuerelements.|
|[CTabCtrl::SetCurFocus](#setcurfocus)|Legt den Fokus auf eine angegebene Registerkarte in einem Registerkartensteuerelement fest.|
|[CTabCtrl::SetCurSel](#setcursel)|Wählt eine Registerkarte in einem Registerkartensteuerelement aus.|
|[CTabCtrl::SetExtendedStyle](#setextendedstyle)|Legt die erweiterten Stile für ein Registerkartensteuerelement fest.|
|[CTabCtrl::SetImageList](#setimagelist)|Weist einem Registerkartensteuerelement eine Bildliste zu.|
|[CTabCtrl::SetItem](#setitem)|Legt einige oder alle Attribute einer Registerkarte fest.|
|[CTabCtrl::SetItemExtra](#setitemextra)|Legt die Anzahl der Bytes pro Registerkarte fest, die für anwendungsdefinierte Daten in einem Registerkartensteuerelement reserviert sind.|
|[CTabCtrl::SetItemSize](#setitemsize)|Legt die Breite und Höhe eines Elements fest.|
|[CTabCtrl::SetItemState](#setitemstate)|Legt den Status des angegebenen Registerkartensteuerelements fest.|
|[CTabCtrl::SetMinTabWidth](#setmintabwidth)|Legt die mindestbreite von Elementen in einem Registerkartensteuerelement fest.|
|[CTabCtrl::SetPadding](#setpadding)|Legt den Abstand (Auffüllung) um das Symbol und die Beschriftung jeder Registerkarte in einem Registerkartensteuerelement fest.|
|[CTabCtrl::SetToolTips](#settooltips)|Weist einem Registerkartensteuerelement ein QuickInfo-Steuerelement zu.|

## <a name="remarks"></a>Bemerkungen

Ein "Tab-Steuerelement" entspricht den Trennwänden in einem Notizbuch oder den Beschriftungen in einem Aktenschrank. Durch Verwenden eines Registerkarten-Steuerelements können in einer Anwendung mehrere Seiten für denselben Bereich in einem Fenster oder Dialogfeld definiert werden. Jede Seite besteht aus einer Gruppe von Informationen oder einer Gruppe von Steuerelementen, die die Anwendung anzeigt, wenn der Benutzer die entsprechende Registerkarte auswählt. Ein spezieller Typ von Registerkartensteuerung zeigt Registerkarten an, die wie Schaltflächen aussehen. Wenn Sie auf eine Schaltfläche klicken, sollten Sie sofort einen Befehl ausführen, anstatt eine Seite anzuzeigen.

Dieses Steuerelement (und `CTabCtrl` damit die Klasse) ist nur für Programme verfügbar, die unter Windows 95/98 und Windows NT Version 3.51 und höher ausgeführt werden.

Weitere Informationen zur `CTabCtrl`Verwendung finden Sie unter [Steuerelemente](../../mfc/controls-mfc.md) und [Verwenden von CTabCtrl](../../mfc/using-ctabctrl.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CTabCtrl`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcmn.h

## <a name="ctabctrladjustrect"></a><a name="adjustrect"></a>CTabCtrl::AdjustRect

Berechnet den Anzeigebereich eines Registerkartensteuerelements mit einem Fensterrechteck oder berechnet das Fensterrechteck, das einem bestimmten Anzeigebereich entspricht.

```cpp
void AdjustRect(BOOL bLarger,   LPRECT lpRect);
```

### <a name="parameters"></a>Parameter

*bLarger*<br/>
Gibt an, welcher Vorgang ausgeführt werden soll. Wenn dieser Parameter TRUE ist, gibt *lpRect* ein Anzeigerechteck an und empfängt das entsprechende Fensterrechteck. Wenn dieser Parameter FALSE ist, gibt *lpRect* ein Fensterrechteck an und empfängt das entsprechende Anzeigerechteck.

*lpRect*<br/>
Zeiger auf eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die das angegebene Rechteck angibt und das berechnete Rechteck empfängt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTabCtrl#1](../../mfc/reference/codesnippet/cpp/ctabctrl-class_1.cpp)]

## <a name="ctabctrlcreate"></a><a name="create"></a>CTabCtrl::Erstellen

Erstellt ein Registerkartensteuerelement und fügt es `CTabCtrl` an eine Instanz eines Objekts an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwStyle*<br/>
Gibt den Stil des Registerkartensteuerelements an. Wenden Sie eine beliebige Kombination von [Registerkartensteuerelementstilen](/windows/win32/Controls/tab-control-styles)an, die im Windows SDK beschrieben werden. Eine Liste der Fensterstile, die Sie auch auf das Steuerelement anwenden können, finden Sie unter **Hinweise.**

*Rect*<br/>
Gibt die Größe und Position des Registerkartensteuerelements an. Dabei kann es sich entweder um ein [CRect-Objekt](../../atl-mfc-shared/reference/crect-class.md) oder eine [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) handelt.

*pParentWnd*<br/>
Gibt das übergeordnete Fenster des Registerkartensteuerelements an, in der Regel eine `CDialog`. Es darf nicht NULL sein.

*nID*<br/>
Gibt die ID des Registerkartensteuerelements an.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Initialisierung des Objekts erfolgreich war; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CTabCtrl` ein Objekt in zwei Schritten. Rufen Sie zuerst den Konstruktor `Create`auf, und rufen Sie dann `CTabCtrl` auf, das das Registerkartensteuerelement erstellt und an das Objekt anfügt.

Zusätzlich zu den Registerkartensteuerungsstilen können Sie die folgenden Fensterstile auf ein Registerkartensteuerelement anwenden:

- WS_CHILD Erstellt ein untergeordnetes Fenster, das das Registerkartensteuerelement darstellt. Kann nicht mit dem WS_POPUP-Stil verwendet werden.

- WS_VISIBLE Erstellt ein Registerkartensteuerelement, das zunächst sichtbar ist.

- WS_DISABLED Erstellt ein Fenster, das zunächst deaktiviert ist.

- WS_GROUP Gibt das erste Steuerelement einer Gruppe von Steuerelementen an, in der der Benutzer mit den Pfeiltasten von einem Steuerelement zum nächsten wechseln kann. Alle Steuerelemente, die nach dem ersten Steuerelement mit dem WS_GROUP-Stil definiert wurden, gehören zur gleichen Gruppe. Das nächste Steuerelement mit dem Stil WS_GROUP beendet die Stilgruppe und startet die nächste Gruppe (d. h. eine Gruppe endet an der Stelle, an der die nächste beginnt).

- WS_TABSTOP Gibt eines von einer beliebigen Anzahl von Steuerelementen an, durch die der Benutzer mithilfe der TAB-Taste wechseln kann. Mit der TAB-TASTE wechselt der Benutzer zum nächsten Steuerelement, das durch den WS_TABSTOP-Stil angegeben ist.

Um ein Registerkartensteuerelement mit erweiterten Fensterstilen zu erstellen, `Create`rufen Sie [CTabCtrl::CreateEx](#createex) anstelle von auf.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTabCtrl#2](../../mfc/reference/codesnippet/cpp/ctabctrl-class_2.cpp)]

## <a name="ctabctrlcreateex"></a><a name="createex"></a>CTabCtrl::CreateEx

Erstellt ein Steuerelement (ein untergeordnetes Fenster) und ordnet es dem `CTabCtrl` Objekt zu.

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
Gibt den Stil des Registerkartensteuerelements an. Wenden Sie eine beliebige Kombination von [Registerkartensteuerelementstilen](/windows/win32/Controls/tab-control-styles)an, die im Windows SDK beschrieben werden. Unter **Hinweise** unter [Erstellen](#create) finden Sie eine Liste von Fensterstilen, die Sie auch auf das Steuerelement anwenden können.

*Rect*<br/>
Ein Verweis auf eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die die Größe und Position des zu erstellenden Fensters in den Clientkoordinaten von *pParentWnd*beschreibt.

*pParentWnd*<br/>
Ein Zeiger auf das Fenster, das das übergeordnete Steuerelement ist.

*nID*<br/>
Die untergeordnete Fenster-ID des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn andernfalls 0 erfolgreich ist.

### <a name="remarks"></a>Bemerkungen

Verwenden `CreateEx` Sie anstelle von [Erstellen,](#create) um erweiterte Windows-Formatvorlagen anzuwenden, die durch das Erweiterte Windows-Stilvorwort **WS_EX_** angegeben werden.

`CreateEx`erstellt das Steuerelement mit den erweiterten Windows-Stilen, die von *dwExStyle*angegeben werden. Legen Sie erweiterte Stile fest, die für ein Steuerelement mit [SetExtendedStyle](#setextendedstyle)spezifisch sind. Verwenden Sie `CreateEx` z. B., um `SetExtendedStyle` Stile wie WS_EX_CONTEXTHELP festzulegen, aber verwenden Sie, um Stile wie TCS_EX_FLATSEPARATORS festzulegen. Weitere Informationen finden Sie in den Unterformatvorlagen, die unter Erweiterte Formatvorlagen für [die Registerkartensteuerung](/windows/win32/Controls/tab-control-extended-styles) im Windows SDK beschrieben werden.

## <a name="ctabctrlctabctrl"></a><a name="ctabctrl"></a>CTabCtrl::CTabCtrl

Erstellt ein `CTabCtrl`-Objekt.

```
CTabCtrl();
```

## <a name="ctabctrldeleteallitems"></a><a name="deleteallitems"></a>CTabCtrl::DeleteAllItems

Entfernt alle Elemente aus einem Registerkartensteuerelement.

```
BOOL DeleteAllItems();
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

## <a name="ctabctrldeleteitem"></a><a name="deleteitem"></a>CTabCtrl::DeleteItem

Entfernt das angegebene Element aus einem Registerkartensteuerelement.

```
BOOL DeleteItem(int nItem);
```

### <a name="parameters"></a>Parameter

*nItem*<br/>
Nullbasierter Wert des zu löschenden Elements.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTabCtrl#3](../../mfc/reference/codesnippet/cpp/ctabctrl-class_3.cpp)]

## <a name="ctabctrldeselectall"></a><a name="deselectall"></a>CTabCtrl::DeselectAlle

Setzt Elemente in einem Registerkartensteuerelement zurück und löscht alle, die gedrückt wurden.

```cpp
void DeselectAll(BOOL fExcludeFocus);
```

### <a name="parameters"></a>Parameter

*fExcludeFocus*<br/>
Flag, das den Gültigkeitsbereich der Elementauswahl angibt. Wenn dieser Parameter auf FALSE gesetzt ist, werden alle Registerkartenschaltflächen zurückgesetzt. Wenn sie auf TRUE festgelegt ist, werden alle Tabstoppelemente mit Ausnahme des aktuell ausgewählten wiedergesetzt.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der Win32-Nachricht [TCM_DESELECTALL](/windows/win32/Controls/tcm-deselectall), wie im Windows SDK beschrieben.

## <a name="ctabctrldrawitem"></a><a name="drawitem"></a>CTabCtrl::DrawItem

Wird vom Framework aufgerufen, wenn sich ein visueller Aspekt eines Besitzerzeichnungs-Registerkartensteuerelements ändert.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parameter

*lpDrawItemStruct*<br/>
Ein Zeiger auf eine [DRAWITEMSTRUCT-Struktur,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) die das zu malende Element beschreibt.

### <a name="remarks"></a>Bemerkungen

Das `itemAction` Element `DRAWITEMSTRUCT` der Struktur definiert die Zeichnungsaktion, die ausgeführt werden soll.

Standardmäßig führt diese Memberfunktion nichts aus. Überschreiben Sie diese Memberfunktion, um `CTabCtrl` die Zeichnung für ein Besitzerzeichnungsobjekt zu implementieren.

Die Anwendung sollte alle GDI-Objekte (Graphics Device Interface) wiederherstellen, die für den in *lpDrawItemStruct* bereitgestellten Anzeigekontext ausgewählt wurden, bevor diese Memberfunktion beendet wird.

## <a name="ctabctrlgetcurfocus"></a><a name="getcurfocus"></a>CTabCtrl::GetCurFocus

Ruft den Index der Registerkarte mit dem aktuellen Fokus ab.

```
int GetCurFocus() const;
```

### <a name="return-value"></a>Rückgabewert

Der nullbasierte Index der Registerkarte mit dem aktuellen Fokus.

## <a name="ctabctrlgetcursel"></a><a name="getcursel"></a>CTabCtrl::GetCurSel

Ruft die aktuell ausgewählte Registerkarte in einem Registerkartensteuerelement ab.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Rückgabewert

Nullbasierter Index der ausgewählten Registerkarte, wenn erfolgreich oder - 1, wenn keine Registerkarte ausgewählt ist.

## <a name="ctabctrlgetextendedstyle"></a><a name="getextendedstyle"></a>CTabCtrl::GetExtendedStyle

Ruft die erweiterten Stile ab, die derzeit für das Registerkartensteuerelement verwendet werden.

```
DWORD GetExtendedStyle();
```

### <a name="return-value"></a>Rückgabewert

Stellt die erweiterten Stile dar, die derzeit für das Registerkartensteuerelement verwendet werden. Dieser Wert ist eine Kombination [erweiterter Formatvorlagen für das Registerkartensteuerelement](/windows/win32/Controls/tab-control-extended-styles), wie im Windows SDK beschrieben.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [TCM_GETEXTENDEDSTYLE](/windows/win32/Controls/tcm-getextendedstyle)Win32-TCM_GETEXTENDEDSTYLE , wie im Windows SDK beschrieben.

## <a name="ctabctrlgetimagelist"></a><a name="getimagelist"></a>CTabCtrl::GetImageList

Ruft die einem Tab-Steuerelement zugeordnete Bildliste ab.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich ist es ein Zeiger auf die Bildliste des Registersteuerelements, andernfalls NULL.

## <a name="ctabctrlgetitem"></a><a name="getitem"></a>CTabCtrl::GetItem

Ruft Informationen zu einer Registerkarte in einem Registerkartensteuerelement ab.

```
BOOL GetItem(int nItem,   TCITEM* pTabCtrlItem) const;
```

### <a name="parameters"></a>Parameter

*nItem*<br/>
Nullbasierter Index der Registerkarte.

*pTabCtrlItem*<br/>
Zeiger auf eine [TCITEM-Struktur,](/windows/win32/api/commctrl/ns-commctrl-tcitemw) die verwendet wird, um die abzurufenden Informationen anzugeben. Wird auch verwendet, um Informationen über die Registerkarte zu erhalten. Diese Struktur wird `InsertItem`mit `GetItem`den `SetItem` Funktionen , und Member verwendet.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn erfolgreich; FALSE sonst.

### <a name="remarks"></a>Bemerkungen

Wenn die Nachricht gesendet `mask` wird, gibt das Element an, welche Attribute zurückgegeben werden sollen. Wenn `mask` das Element den wert `pszText` TCIF_TEXT angibt, muss das Element die Adresse `cchTextMax` des Puffers enthalten, der den Elementtext empfängt, und das Element muss die Größe des Puffers angeben.

- `mask`

   Wert, der `TCITEM` angibt, welche Strukturmember abgerufen oder festgelegt werden sollen. Dieser Member kann Null oder eine Kombination der folgenden Werte sein:

  - TCIF_TEXT `pszText` Das Mitglied ist gültig.

  - TCIF_IMAGE `iImage` Das Mitglied ist gültig.

  - TCIF_PARAM `lParam` Das Mitglied ist gültig.

  - TCIF_RTLREADING Der `pszText` Text von wird in der Lesereihenfolge von rechts nach links auf hebräischen oder arabischen Systemen angezeigt.

  - TCIF_STATE `dwState` Das Mitglied ist gültig.

- `pszText`

   Zeigen Sie auf eine null-terminierte Zeichenfolge, die den Registerkartentext enthält, wenn die Struktur Informationen zu einer Registerkarte enthält. Wenn die Struktur Informationen empfängt, gibt dieses Element die Adresse des Puffers an, der den Registerkartentext empfängt.

- `cchTextMax`

   Größe des Puffers, `pszText`auf den von verwiesen wird. Dieser Member wird ignoriert, wenn die Struktur keine Informationen empfängt.

- `iImage`Indizieren Sie in die Bildliste des Tab-Steuerelements, oder - 1, wenn kein Bild für die Registerkarte vorhanden ist.

- `lParam`

   Anwendungsdefinierte Daten, die der Registerkarte zugeordnet sind. Wenn pro Registerkarte mehr als vier Bytes anwendungsdefinierter Daten vorhanden sind, muss `TCITEM` eine Anwendung eine Struktur definieren und anstelle der Struktur verwenden. Das erste Element der anwendungsdefinierten Struktur muss eine [TCITEMHEADER-Struktur](/windows/win32/api/commctrl/ns-commctrl-tcitemheaderw)sein. Die `TCITEMHEADER` Struktur ist `TCITEM` identisch mit der `lParam` Struktur, jedoch ohne das Element. Der Unterschied zwischen der Größe der Struktur `TCITEMHEADER` und der Größe der Struktur sollte der Anzahl der zusätzlichen Bytes pro Registerkarte entsprechen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTabCtrl#4](../../mfc/reference/codesnippet/cpp/ctabctrl-class_4.cpp)]

## <a name="ctabctrlgetitemcount"></a><a name="getitemcount"></a>CTabCtrl::GetItemCount

Ruft die Anzahl der Registerkarten im Registerkartensteuerelement ab.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Rückgabewert

Anzahl der Elemente im Registerkartensteuerelement.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctabctrlgetitemrect"></a><a name="getitemrect"></a>CTabCtrl::GetItemRect

Ruft das umgrenzende Rechteck für die angegebene Registerkarte in einem Registerkartensteuerelement ab.

```
BOOL GetItemRect(int nItem,   LPRECT lpRect) const;
```

### <a name="parameters"></a>Parameter

*nItem*<br/>
Nullbasierter Index des Registerkartenelements.

*lpRect*<br/>
Zeiger auf eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die das umgrenzende Rechteck der Registerkarte empfängt. Diese Koordinaten verwenden den aktuellen Zuordnungsmodus des Ansichtsfensters.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctabctrlgetitemstate"></a><a name="getitemstate"></a>CTabCtrl::GetItemState

Ruft den Status des Tabstopp-Steuerelements ab, das von *nItem*identifiziert wurde.

```
DWORD GetItemState(
    int nItem,
    DWORD dwMask) const;
```

### <a name="parameters"></a>Parameter

*nItem*<br/>
Die nullbasierte Indexnummer des Elements, für das Statusinformationen abgerufen werden sollen.

*dwMask*<br/>
Maske, die angibt, welche der Statusflags des Elements zurückgegeben werden sollen. Eine Liste der Werte finden Sie im Maskenelement der [TCITEM-Struktur,](/windows/win32/api/commctrl/ns-commctrl-tcitemw) wie im Windows SDK beschrieben.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf einen DWORD-Wert, der die Statusinformationen empfängt. Es kann sich um einen der folgenden Werte handeln:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|Das Registerkartensteuerelement ist ausgewählt.|
|TCIS_HIGHLIGHTED|Das Registerkartensteuerelement element wird hervorgehoben, und die Registerkarte und der Text werden mit der aktuellen Hervorhebungsfarbe gezeichnet. Bei Verwendung der Hervorhebungsfarbe ist dies eine echte Interpolation, keine gedithere Farbe.|

### <a name="remarks"></a>Bemerkungen

Der Status eines Elements wird `dwState` vom `TCITEM` Element der Struktur angegeben.

## <a name="ctabctrlgetrowcount"></a><a name="getrowcount"></a>CTabCtrl::GetRowCount

Ruft die aktuelle Anzahl von Zeilen in einem Registerkartensteuerelement ab.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Zeilen von Registerkarten im Registerkartensteuerelement.

### <a name="remarks"></a>Bemerkungen

Nur Registerkartensteuerelemente mit dem Stil TCS_MULTILINE können über mehrere Zeilen von Registerkarten verfügen.

## <a name="ctabctrlgettooltips"></a><a name="gettooltips"></a>CTabCtrl::GetToolTipps

Ruft das Handle des QuickInfo-Steuerelements ab, das einem Registerkartensteuerelement zugeordnet ist.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Rückgabewert

Griff der Werkzeugspitzensteuerung, wenn erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Ein Registerkartensteuerelement erstellt ein QuickInfo-Steuerelement, wenn es den TCS_TOOLTIPS Stil hat. Sie können einem Registerkartensteuerelement auch ein QuickInfo-Steuerelement zuweisen, indem Sie die `SetToolTips` Memberfunktion verwenden.

## <a name="ctabctrlhighlightitem"></a><a name="highlightitem"></a>CTabCtrl::HighlightItem

Legt den Hervorhebungsstatus eines Registerkartenelements fest.

```
BOOL HighlightItem(int idItem,   BOOL fHighlight = TRUE);
```

### <a name="parameters"></a>Parameter

*idItem*<br/>
Nullbasierter Index eines Registerkartensteuerelements.

*fHighlight*<br/>
Wert, der den zu setzenden Hervorhebungszustand angibt. Wenn dieser Wert TRUE ist, wird die Registerkarte hervorgehoben. Wenn FALSE, wird die Registerkarte auf den Standardzustand gesetzt.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert die Win32-Meldung [TCM_HIGHLIGHTITEM](/windows/win32/Controls/tcm-highlightitem), wie im Windows SDK beschrieben.

## <a name="ctabctrlhittest"></a><a name="hittest"></a>CTabCtrl::HitTest

Bestimmt, welche Registerkarte sich ggf. an der angegebenen Bildschirmposition befindet.

```
int HitTest(TCHITTESTINFO* pHitTestInfo) const;
```

### <a name="parameters"></a>Parameter

*pHitTestInfo*<br/>
Zeiger auf eine [TCHITTESTINFO-Struktur,](/windows/win32/api/commctrl/ns-commctrl-tchittestinfo) wie im Windows SDK beschrieben, die die zu testende Bildschirmposition angibt.

### <a name="return-value"></a>Rückgabewert

Gibt den nullbasierten Index der Registerkarte oder - 1 zurück, wenn sich keine Registerkarte an der angegebenen Position befindet.

## <a name="ctabctrlinsertitem"></a><a name="insertitem"></a>CTabCtrl::InsertItem

Fügt eine neue Registerkarte in ein vorhandenes Registerkartensteuerelement ein.

```
LONG InsertItem(
    int nItem,
    TCITEM* pTabCtrlItem);

LONG InsertItem(
    int nItem,
    LPCTSTR lpszItem);

LONG InsertItem(
    int nItem,
    LPCTSTR lpszItem,
    int nImage);

LONG InsertItem(
    UINT nMask,
    int nItem,
    LPCTSTR lpszItem,
    int nImage,
    LPARAM lParam);

LONG InsertItem(
    UINT nMask,
    int nItem,
    LPCTSTR lpszItem,
    int nImage,
    LPARAM lParam,
    DWORD dwState,
    DWORD dwStateMask);
```

### <a name="parameters"></a>Parameter

*nItem*<br/>
Nullbasierter Index der neuen Registerkarte.

*pTabCtrlItem*<br/>
Zeiger auf eine [TCITEM-Struktur,](/windows/win32/api/commctrl/ns-commctrl-tcitemw) die die Attribute der Registerkarte angibt.

*lpszItem*<br/>
Adresse einer null-terminierten Zeichenfolge, die den Text der Registerkarte enthält.

*nImage*<br/>
Der nullbasierte Index eines Bildes, das aus einer Bildliste eingefügt werden soll.

*nMaske*<br/>
Gibt an, welche `TCITEM` Strukturattribute festgelegt werden sollen. Kann Null oder eine Kombination der folgenden Werte sein:

- TCIF_TEXT `pszText` Das Mitglied ist gültig.

- TCIF_IMAGE `iImage` Das Mitglied ist gültig.

- TCIF_PARAM Das *lParam-Member* ist gültig.

- TCIF_RTLREADING Der `pszText` Text von wird in der Lesereihenfolge von rechts nach links auf hebräischen oder arabischen Systemen angezeigt.

- TCIF_STATE Das *dwState-Mitglied* ist gültig.

*lParam*<br/>
Anwendungsdefinierte Daten, die der Registerkarte zugeordnet sind.

*dwState*<br/>
Gibt Werte für die Zustände des Elements an. Weitere Informationen finden Sie unter [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) im Windows SDK.

*dwStateMask*<br/>
Gibt an, welche Zustände festgelegt werden sollen. Weitere Informationen finden Sie unter [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Nullbasierter Index der neuen Registerkarte, falls erfolgreich; ansonsten - 1.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTabCtrl#5](../../mfc/reference/codesnippet/cpp/ctabctrl-class_5.cpp)]

## <a name="ctabctrlremoveimage"></a><a name="removeimage"></a>CTabCtrl::RemoveImage

Entfernt das angegebene Bild aus der Bildliste eines Registerkartensteuerelements.

```cpp
void RemoveImage(int nImage);
```

### <a name="parameters"></a>Parameter

*nImage*<br/>
Nullbasierter Index des zu entfernenden Bildes.

### <a name="remarks"></a>Bemerkungen

Das Registerkartensteuerelement aktualisiert den Bildindex jeder Registerkarte, sodass jede Registerkarte mit demselben Bild verknüpft bleibt.

## <a name="ctabctrlsetcurfocus"></a><a name="setcurfocus"></a>CTabCtrl::SetCurFocus

Legt den Fokus auf eine angegebene Registerkarte in einem Registerkartensteuerelement fest.

```cpp
void SetCurFocus(int nItem);
```

### <a name="parameters"></a>Parameter

*nItem*<br/>
Gibt den Index der Registerkarte an, die den Fokus erhält.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der Win32-Meldung [TCM_SETCURFOCUS](/windows/win32/Controls/tcm-setcurfocus), wie im Windows SDK beschrieben.

## <a name="ctabctrlsetcursel"></a><a name="setcursel"></a>CTabCtrl::SetCurSel

Wählt eine Registerkarte in einem Registerkartensteuerelement aus.

```
int SetCurSel(int nItem);
```

### <a name="parameters"></a>Parameter

*nItem*<br/>
Der nullbasierte Index des ausgewählten Elements.

### <a name="return-value"></a>Rückgabewert

Nullbasierter Index der zuvor ausgewählten Registerkarte, falls erfolgreich, andernfalls - 1.

### <a name="remarks"></a>Bemerkungen

Ein Registerkartensteuerelement sendet keine TCN_SELCHANGING- oder TCN_SELCHANGE Benachrichtigung, wenn eine Registerkarte mit dieser Funktion ausgewählt wird. Diese Benachrichtigungen werden mithilfe WM_NOTIFY gesendet, wenn der Benutzer auf die Tastatur klickt oder sie zum Ändern von Registerkarten verwendet.

## <a name="ctabctrlsetextendedstyle"></a><a name="setextendedstyle"></a>CTabCtrl::SetExtendedStyle

Legt die erweiterten Stile für ein Registerkartensteuerelement fest.

```
DWORD SetExtendedStyle(DWORD dwNewStyle,   DWORD dwExMask = 0);
```

### <a name="parameters"></a>Parameter

*dwNewStyle*<br/>
Wert, der eine Kombination erweiterter Stile des Tab-Steuerelements angibt.

*dwExMask*<br/>
Ein DWORD-Wert, der angibt, welche Stile in *dwNewStyle* betroffen sein sollen. Nur die erweiterten Stile in *dwExMask* werden geändert. Alle anderen Stile werden beibehalten, wie sie sind. Wenn dieser Parameter Null ist, sind alle Stile in *dwNewStyle* betroffen.

### <a name="return-value"></a>Rückgabewert

Ein DWORD-Wert, der die erweiterten Formatvorlagen des vorherigen [Registerkartensteuerelements](/windows/win32/Controls/tab-control-extended-styles)enthält, wie im Windows SDK beschrieben.

### <a name="return-value"></a>Rückgabewert

Diese Memberfunktion implementiert das Verhalten der [TCM_SETEXTENDEDSTYLE](/windows/win32/Controls/tcm-setextendedstyle)Win32-TCM_SETEXTENDEDSTYLE , wie im Windows SDK beschrieben.

## <a name="ctabctrlsetimagelist"></a><a name="setimagelist"></a>CTabCtrl::SetImageList

Weist einem Registerkartensteuerelement eine Bildliste zu.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parameter

*pImageList*<br/>
Zeigen Sie auf die Bildliste, die dem Registerkartensteuerelement zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf die vorherige Bildliste oder NULL zurück, wenn keine vorherige Bildliste vorhanden ist.

## <a name="ctabctrlsetitem"></a><a name="setitem"></a>CTabCtrl::SetItem

Legt einige oder alle Attribute einer Registerkarte fest.

```
BOOL SetItem(int nItem,   TCITEM* pTabCtrlItem);
```

### <a name="parameters"></a>Parameter

*nItem*<br/>
Nullbasierter Index des Elements.

*pTabCtrlItem*<br/>
Zeiger auf eine [TCITEM-Struktur,](/windows/win32/api/commctrl/ns-commctrl-tcitemw) die die neuen Elementattribute enthält. Der `mask` Member gibt an, welche Attribute festgelegt werden sollen. Wenn `mask` das Element den TCIF_TEXT-Wert angibt, ist der `pszText` Member die `cchTextMax` Adresse einer null-beendeten Zeichenfolge, und der Member wird ignoriert.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

  Siehe Beispiel für [GetItem](#getitem).

## <a name="ctabctrlsetitemextra"></a><a name="setitemextra"></a>CTabCtrl::SetItemExtra

Legt die Anzahl der Bytes pro Registerkarte fest, die für anwendungsdefinierte Daten in einem Registerkartensteuerelement reserviert sind.

```
BOOL SetItemExtra(int nBytes);
```

### <a name="parameters"></a>Parameter

*nBytes*<br/>
Die Anzahl der zu setzenden zusätzlichen Bytes.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der Win32-Meldung [TCM_SETITEMEXTRA](/windows/win32/Controls/tcm-setitemextra), wie im Windows SDK beschrieben.

## <a name="ctabctrlsetitemsize"></a><a name="setitemsize"></a>CTabCtrl::SetItemSize

Legt die Breite und Höhe des Registerkarten-Steuerelements fest.

```
CSize SetItemSize(CSize size);
```

### <a name="parameters"></a>Parameter

*size*<br/>
Die neue Breite und Höhe des Registerkarten-Steuerelements in Pixeln.

### <a name="return-value"></a>Rückgabewert

Gibt die alte Breite und Höhe des Registerkarten-Steuerelements zurück.

## <a name="ctabctrlsetitemstate"></a><a name="setitemstate"></a>CTabCtrl::SetItemState

Legt den Status des von *nItem*identifizierten Registerkartensteuerelements fest.

```
BOOL SetItemState(
    int nItem,
    DWORD dwMask,
    DWORD dwState);
```

### <a name="parameters"></a>Parameter

*nItem*<br/>
Die nullbasierte Indexnummer des Elements, für das Statusinformationen festgelegt werden sollen.

*dwMask*<br/>
Maske, die angibt, welche der Statusflags des Elements festgelegt werden sollen. Eine Liste der Werte finden Sie im Maskenelement der [TCITEM-Struktur,](/windows/win32/api/commctrl/ns-commctrl-tcitemw) wie im Windows SDK beschrieben.

*dwState*<br/>
Ein Verweis auf einen DWORD-Wert, der die Statusinformationen enthält. Es kann sich um einen der folgenden Werte handeln:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|Das Registerkartensteuerelement ist ausgewählt.|
|TCIS_HIGHLIGHTED|Das Registerkartensteuerelement element wird hervorgehoben, und die Registerkarte und der Text werden mit der aktuellen Hervorhebungsfarbe gezeichnet. Bei Verwendung der Hervorhebungsfarbe ist dies eine echte Interpolation, keine gedithere Farbe.|

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

## <a name="ctabctrlsetmintabwidth"></a><a name="setmintabwidth"></a>CTabCtrl::SetMinTabWidth

Legt die mindestbreite von Elementen in einem Registerkartensteuerelement fest.

```
int SetMinTabWidth(int cx);
```

### <a name="parameters"></a>Parameter

*Cx*<br/>
Mindestbreite, die für ein Registerkartensteuerelement festgelegt werden soll. Wenn dieser Parameter auf -1 festgelegt ist, verwendet das Steuerelement die Standard-Tab-Breite.

### <a name="return-value"></a>Rückgabewert

Die vorherige minimale Tabstoppbreite.

### <a name="return-value"></a>Rückgabewert

Diese Memberfunktion implementiert das Verhalten der Win32-Meldung [TCM_SETMINTABWIDTH](/windows/win32/Controls/tcm-setmintabwidth), wie im Windows SDK beschrieben.

## <a name="ctabctrlsetpadding"></a><a name="setpadding"></a>CTabCtrl::SetPadding

Legt den Abstand (Auffüllung) um das Symbol und die Beschriftung jeder Registerkarte in einem Registerkartensteuerelement fest.

```cpp
void SetPadding(CSize size);
```

### <a name="parameters"></a>Parameter

*size*<br/>
Legt den Abstand (Auffüllung) um das Symbol und die Beschriftung jeder Registerkarte in einem Registerkartensteuerelement fest.

## <a name="ctabctrlsettooltips"></a><a name="settooltips"></a>CTabCtrl::SetToolTips

Weist einem Registerkartensteuerelement ein QuickInfo-Steuerelement zu.

```cpp
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Parameter

*pWndTip*<br/>
Griff der Werkzeugspitzensteuerung.

### <a name="remarks"></a>Bemerkungen

Sie können das QuickInfo-Steuerelement, das einem Registerkartensteuerelement zugeordnet ist, abrufen, indem Sie einen Aufruf an `GetToolTips`durchführen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="see-also"></a>Weitere Informationen

[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CHeaderCtrl-Klasse](../../mfc/reference/cheaderctrl-class.md)<br/>
[CListCtrl-Klasse](../../mfc/reference/clistctrl-class.md)
