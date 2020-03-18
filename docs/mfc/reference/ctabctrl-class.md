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
ms.openlocfilehash: a0ca4cbad48c420250fe39e131de5504b1ae70f3
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426342"
---
# <a name="ctabctrl-class"></a>CTabCtrl-Klasse

Stellt die Funktionalität des allgemeinen Windows-Registerkarten-Steuerelements bereit.

## <a name="syntax"></a>Syntax

```
class CTabCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CTabCtrl:: CTabCtrl](#ctabctrl)|Erstellt ein `CTabCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CTabCtrl::-Rect](#adjustrect)|Berechnet den Anzeigebereich eines Registerkarten-Steuer Elements bei Angabe eines Fenster Rechtecks oder berechnet das Fenster Rechteck, das einem angegebenen Anzeigebereich entsprechen würde.|
|[CTabCtrl:: Create](#create)|Erstellt ein Registerkarten-Steuerelement und fügt es an eine Instanz eines `CTabCtrl` Objekts an.|
|[CTabCtrl:: kreateex](#createex)|Erstellt ein Registerkarten-Steuerelement mit den angegebenen erweiterten Windows-Stilen und fügt es an eine Instanz eines `CTabCtrl` Objekts an.|
|[CTabCtrl::D eleteallitems](#deleteallitems)|Entfernt alle Elemente aus einem Registerkarten-Steuerelement.|
|[CTabCtrl::D eleteitem](#deleteitem)|Entfernt ein Element aus einem Registerkarten-Steuerelement.|
|[CTabCtrl::D eselectall](#deselectall)|Setzt Elemente in einem Registerkarten-Steuerelement zurück, wobei alle gedrückten gelöscht werden.|
|[CTabCtrl::D rawitem](#drawitem)|Zeichnet ein angegebenes Element eines Registerkarten-Steuer Elements.|
|[CTabCtrl:: getcurrfocus](#getcurfocus)|Ruft die Registerkarte mit dem aktuellen Fokus eines Registerkarten-Steuer Elements ab.|
|[CTabCtrl:: getcurrsel](#getcursel)|Bestimmt die derzeit ausgewählte Registerkarte in einem Registerkarten-Steuerelement.|
|[CTabCtrl:: GetExtendedStyle](#getextendedstyle)|Ruft die erweiterten Stile ab, die zurzeit für das Registerkarten-Steuerelement verwendet werden.|
|[CTabCtrl:: GetImageList](#getimagelist)|Ruft die einem Registerkarten-Steuerelement zugeordnete Bildliste ab.|
|[CTabCtrl:: GetItem](#getitem)|Ruft Informationen zu einer Registerkarte in einem Registerkarten-Steuerelement ab.|
|[CTabCtrl:: GetItemCount](#getitemcount)|Ruft die Anzahl der Registerkarten im Registerkarten-Steuerelement ab.|
|[CTabCtrl:: GetItemRect](#getitemrect)|Ruft das umgebende Rechteck für eine Registerkarte in einem Registerkarten-Steuerelement ab.|
|[CTabCtrl:: GetItemState](#getitemstate)|Ruft den Zustand des aufgeführten Registerkarten-Steuerelement Elements ab.|
|[CTabCtrl:: GetRowCount](#getrowcount)|Ruft die aktuelle Anzahl der Zeilen von Registerkarten in einem Registerkarten-Steuerelement ab.|
|[CTabCtrl:: gettooltips](#gettooltips)|Ruft das Handle des QuickInfo-Steuer Elements ab, das einem Registerkarten-Steuerelement zugeordnet ist.|
|[CTabCtrl:: highlightitem](#highlightitem)|Legt den Hervorhebungs Zustand eines Registerkarten Elements fest.|
|[CTabCtrl:: HitTest](#hittest)|Bestimmt, welche Registerkarte, falls vorhanden, an einer angegebenen Bildschirmposition ist.|
|[CTabCtrl:: InsertItem](#insertitem)|Fügt eine neue Registerkarte in ein Registerkarten-Steuerelement ein.|
|[CTabCtrl:: removeimage](#removeimage)|Entfernt ein Bild aus der Bildliste eines Registerkarten-Steuer Elements.|
|[CTabCtrl:: setcurrfocus](#setcurfocus)|Legt den Fokus auf eine angegebene Registerkarte in einem Registerkarten-Steuerelement fest.|
|[CTabCtrl:: setcurrsel](#setcursel)|Wählt eine Registerkarte in einem Register Steuerelement aus.|
|[CTabCtrl:: abtextendedstyle](#setextendedstyle)|Legt die erweiterten Stile für ein Registerkarten-Steuerelement fest.|
|[CTabCtrl:: SetImageList](#setimagelist)|Weist einem Registerkarten-Steuerelement eine Bildliste zu.|
|[CTabCtrl:: System Item](#setitem)|Legt einige oder alle Attribute einer Registerkarte fest.|
|[CTabCtrl:: "ctabtemextra"](#setitemextra)|Legt die Anzahl von Bytes pro Registerkarte fest, die für Anwendungs definierte Daten in einem Registerkarten-Steuerelement reserviert ist.|
|[CTabCtrl:: settemsize](#setitemsize)|Legt die Breite und Höhe eines Elements fest.|
|[CTabCtrl:: abtitemstate](#setitemstate)|Legt den Zustand des aufgeführten Register Steuerelement-Steuer Elements fest.|
|[CTabCtrl:: setmintabwidth](#setmintabwidth)|Legt die minimale Breite von Elementen in einem Registerkarten-Steuerelement fest.|
|[CTabCtrl:: setPadding](#setpadding)|Legt den Leerraum (Padding) um das Symbol und die Bezeichnung der einzelnen Registerkarten in einem Registerkarten-Steuerelement fest.|
|[CTabCtrl:: SetToolTips](#settooltips)|Weist einem Registerkarten-Steuerelement ein QuickInfo-Steuerelement zu.|

## <a name="remarks"></a>Hinweise

Ein Registerkarten-Steuerelement ist analog zu den untergeordneten Elementen in einem Notebook oder den Bezeichnungen in einer Datei CAB-Datei. Durch Verwenden eines Registerkarten-Steuerelements können in einer Anwendung mehrere Seiten für denselben Bereich in einem Fenster oder Dialogfeld definiert werden. Jede Seite besteht aus einem Satz von Informationen oder einer Gruppe von Steuerelementen, die von der Anwendung angezeigt werden, wenn der Benutzer die entsprechende Registerkarte auswählt. Eine besondere Art Registerkarten-Steuerelement zeigt Registerkarten an, die wie Schaltflächen aussehen. Wenn Sie auf eine Schaltfläche klicken, sollten Sie sofort einen Befehl ausführen, anstatt eine Seite anzuzeigen.

Dieses Steuerelement (und damit auch die `CTabCtrl`-Klasse) ist nur für Programme verfügbar, die unter Windows 95/98 und Windows NT, Version 3,51 und höher, ausgeführt werden.

Weitere Informationen zur Verwendung von `CTabCtrl`finden Sie unter Steuer [Elemente](../../mfc/controls-mfc.md) und [Verwenden von CTabCtrl](../../mfc/using-ctabctrl.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CTabCtrl`

## <a name="requirements"></a>Voraussetzungen

**Header:** afxcmn.h

##  <a name="adjustrect"></a>CTabCtrl::-Rect

Berechnet den Anzeigebereich eines Registerkarten-Steuer Elements bei Angabe eines Fenster Rechtecks oder berechnet das Fenster Rechteck, das einem angegebenen Anzeigebereich entsprechen würde.

```
void AdjustRect(BOOL bLarger,   LPRECT lpRect);
```

### <a name="parameters"></a>Parameter

*blarger*<br/>
Gibt an, welcher Vorgang durchgeführt werden soll. Wenn dieser Parameter auf true festgelegt ist, gibt *lprect* ein Anzeige Rechteck an und empfängt das entsprechende Fenster Rechteck. Wenn dieser Parameter auf false festgelegt ist, gibt *lprect* ein Fenster Rechteck an und empfängt das entsprechende Anzeige Rechteck.

*lprect*<br/>
Ein Zeiger auf eine [Rect](/previous-versions/dd162897\(v=vs.85\)) -Struktur, die das angegebene Rechteck angibt und das berechnete Rechteck empfängt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTabCtrl#1](../../mfc/reference/codesnippet/cpp/ctabctrl-class_1.cpp)]

##  <a name="create"></a>CTabCtrl:: Create

Erstellt ein Registerkarten-Steuerelement und fügt es an eine Instanz eines `CTabCtrl` Objekts an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwstyle*<br/>
Gibt den Stil des Register Steuer Elements an. Wenden Sie eine beliebige Kombination von [Register Steuer](/windows/win32/Controls/tab-control-styles)Element Formaten an, die im Windows SDK beschrieben werden. Eine Liste der Fenster Stile, die Sie auch auf das Steuerelement anwenden können, finden Sie unter " **Hinweise** ".

*Rect*<br/>
Gibt die Größe und Position des Register Steuer Elements an. Dabei kann es sich entweder um ein [CRect](../../atl-mfc-shared/reference/crect-class.md) -Objekt oder um eine [Rect](/previous-versions/dd162897\(v=vs.85\)) -Struktur handeln.

*pparser*<br/>
Gibt das übergeordnete Fenster des Register Steuer Elements an, in der Regel eine `CDialog`. Er darf nicht NULL sein.

*NID*<br/>
Gibt die ID des Registerkarten-Steuer Elements an.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Initialisierung des Objekts erfolgreich war. andernfalls false.

### <a name="remarks"></a>Hinweise

Sie erstellen ein `CTabCtrl`-Objekt in zwei Schritten. Nennen Sie zuerst den-Konstruktor, und klicken Sie dann auf `Create`, der das Registerkarten-Steuerelement erstellt und an das `CTabCtrl`-Objekt anfügt.

Zusätzlich zu den Steuerelement Formaten für Registerkarten können Sie die folgenden Fenster Stile auf ein Registerkarten-Steuerelement anwenden:

- WS_CHILD erstellt ein untergeordnetes Fenster, das das Registerkarten-Steuerelement darstellt. Kann nicht mit dem WS_POPUP Stil verwendet werden.

- WS_VISIBLE erstellt ein Registerkarten-Steuerelement, das anfänglich sichtbar ist.

- WS_DISABLED erstellt ein Fenster, das anfänglich deaktiviert ist.

- WS_GROUP gibt das erste Steuerelement einer Gruppe von Steuerelementen an, in der der Benutzer mit den Pfeiltasten von einem Steuerelement zum nächsten wechseln kann. Alle Steuerelemente, die nach dem ersten Steuerelement mit dem WS_GROUP Format definiert sind, gehören zur selben Gruppe. Das nächste Steuerelement mit der WS_GROUP-Formatvorlage beendet die Format Gruppe und startet die nächste Gruppe (d. h., eine Gruppe endet an der Stelle, an der der nächste beginnt).

- WS_TABSTOP gibt eine beliebige Anzahl von Steuerelementen an, über die der Benutzer mit der Tab-Taste bewegt werden kann. Mit der TAB-TASTE wechselt der Benutzer zum nächsten Steuerelement, das durch den WS_TABSTOP-Stil angegeben ist.

Rufen Sie zum Erstellen eines Registerkarten-Steuer Elements mit erweiterten Fenster Stilen [CTabCtrl:: deateex](#createex) anstelle von `Create`auf.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTabCtrl#2](../../mfc/reference/codesnippet/cpp/ctabctrl-class_2.cpp)]

##  <a name="createex"></a>CTabCtrl:: kreateex

Erstellt ein-Steuerelement (ein untergeordnetes Fenster) und ordnet es dem `CTabCtrl`-Objekt zu.

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
Gibt die erweiterte Art des zu erstellenden Steuer Elements an. Eine Liste erweiterter Windows-Stile finden Sie unter dem *dwExStyle* -Parameter für " [kreatewindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw) " in der Windows SDK.

*dwstyle*<br/>
Gibt den Stil des Register Steuer Elements an. Wenden Sie eine beliebige Kombination von [Register Steuer](/windows/win32/Controls/tab-control-styles)Element Formaten an, die im Windows SDK beschrieben werden. Unter **Hinweise** in [Create](#create) finden Sie eine Liste der Fenster Stile, die Sie auch auf das-Steuerelement anwenden können.

*Rect*<br/>
Ein Verweis auf eine [Rect](/previous-versions/dd162897\(v=vs.85\)) -Struktur, die die Größe und Position des zu erstellenden Fensters in Client Koordinaten von *pparser*beschreibt.

*pparser*<br/>
Ein Zeiger auf das Fenster, das das übergeordnete Element des Steuer Elements ist.

*NID*<br/>
Die ID des untergeordneten Fensters des Steuer Elements.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Hinweise

Verwenden Sie `CreateEx` anstelle von [Create](#create) , um erweiterte Windows-Stile anzuwenden, die durch den erweiterten Windows-Stil **WS_EX_** angegeben werden.

`CreateEx` erstellt das Steuerelement mit den erweiterten Windows-Stilen, die von *dwExStyle*angegeben werden. Festlegen erweiterter Stile, die für ein Steuerelement spezifisch sind, mithilfe von [setextendecodstyle](#setextendedstyle). Verwenden Sie z. b. `CreateEx`, um solche Stile als WS_EX_CONTEXTHELP festzulegen, verwenden Sie jedoch `SetExtendedStyle`, um solche Stile wie TCS_EX_FLATSEPARATORS festzulegen. Weitere Informationen finden Sie in den unter Registerkarten [Steuerelement erweiterte Stile](/windows/win32/Controls/tab-control-extended-styles) beschriebenen Stilen in der Windows SDK.

##  <a name="ctabctrl"></a>CTabCtrl:: CTabCtrl

Erstellt ein `CTabCtrl`-Objekt.

```
CTabCtrl();
```

##  <a name="deleteallitems"></a>CTabCtrl::D eleteallitems

Entfernt alle Elemente aus einem Registerkarten-Steuerelement.

```
BOOL DeleteAllItems();
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

##  <a name="deleteitem"></a>CTabCtrl::D eleteitem

Entfernt das angegebene Element aus einem Registerkarten-Steuerelement.

```
BOOL DeleteItem(int nItem);
```

### <a name="parameters"></a>Parameter

*nitem*<br/>
Der null basierte Wert des zu löschenden Elements.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTabCtrl#3](../../mfc/reference/codesnippet/cpp/ctabctrl-class_3.cpp)]

##  <a name="deselectall"></a>CTabCtrl::D eselectall

Setzt Elemente in einem Registerkarten-Steuerelement zurück, wobei alle gedrückten gelöscht werden.

```
void DeselectAll(BOOL fExcludeFocus);
```

### <a name="parameters"></a>Parameter

*"f"-Fokus*<br/>
Flag, das den Gültigkeitsbereich der Elementauswahl angibt. Wenn dieser Parameter auf false festgelegt ist, werden alle Tabulator Schaltflächen zurückgesetzt. Wenn der Wert auf true festgelegt ist, werden alle Registerkarten Elemente mit Ausnahme der aktuell ausgewählten Elemente zurückgesetzt.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht, [TCM_DESELECTALL](/windows/win32/Controls/tcm-deselectall), wie in der Windows SDK beschrieben.

##  <a name="drawitem"></a>CTabCtrl::D rawitem

Wird von Framework aufgerufen, wenn sich ein visueller Aspekt eines Registerkarten-Steuer Elements vom Typ "Besitzer" ändert.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parameter

*lpdrawitemstruct*<br/>
Ein Zeiger auf eine [drawitemstruct](/windows/win32/api/winuser/ns-winuser-drawitemstruct) -Struktur, die das zu zeichnende Element beschreibt.

### <a name="remarks"></a>Hinweise

Der `itemAction` Member der `DRAWITEMSTRUCT` Struktur definiert die auszuführende Zeichnungs Aktion.

Standardmäßig führt diese Member-Funktion keine Aktion aus. Überschreiben Sie diese Member-Funktion, um das Zeichnen für einen Besitzer `CTabCtrl` Objekt zu implementieren.

Die Anwendung sollte alle GDI-Objekte (Graphics Device Interface), die für den in *lpdrawitemstruct* angegebenen Anzeige Kontext ausgewählt sind, wiederherstellen, bevor diese Element Funktion beendet wird.

##  <a name="getcurfocus"></a>CTabCtrl:: getcurrfocus

Ruft den Index der Registerkarte mit dem aktuellen Fokus ab.

```
int GetCurFocus() const;
```

### <a name="return-value"></a>Rückgabewert

Der null basierte Index der Registerkarte mit dem aktuellen Fokus.

##  <a name="getcursel"></a>CTabCtrl:: getcurrsel

Ruft die derzeit ausgewählte Registerkarte in einem Registerkarten-Steuerelement ab.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Rückgabewert

NULL basierter Index der ausgewählten Registerkarte, wenn erfolgreich, oder-1, wenn keine Registerkarte ausgewählt ist.

##  <a name="getextendedstyle"></a>CTabCtrl:: GetExtendedStyle

Ruft die erweiterten Stile ab, die zurzeit für das Registerkarten-Steuerelement verwendet werden.

```
DWORD GetExtendedStyle();
```

### <a name="return-value"></a>Rückgabewert

Stellt die erweiterten Stile dar, die derzeit für das Registerkarten-Steuerelement verwendet werden. Dieser Wert ist eine Kombination aus erweiterten Formatvorlagen [Steuer](/windows/win32/Controls/tab-control-extended-styles)Elementen, wie im Windows SDK beschrieben.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [TCM_GETEXTENDEDSTYLE](/windows/win32/Controls/tcm-getextendedstyle), wie in der Windows SDK beschrieben.

##  <a name="getimagelist"></a>CTabCtrl:: GetImageList

Ruft die einem Tab-Steuerelement zugeordnete Bildliste ab.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich ist es ein Zeiger auf die Bildliste des Registersteuerelements, andernfalls NULL.

##  <a name="getitem"></a>CTabCtrl:: GetItem

Ruft Informationen zu einer Registerkarte in einem Registerkarten-Steuerelement ab.

```
BOOL GetItem(int nItem,   TCITEM* pTabCtrlItem) const;
```

### <a name="parameters"></a>Parameter

*nitem*<br/>
Der null basierte Index der Registerkarte.

*ptabctrlitem*<br/>
Zeiger auf eine [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) -Struktur, die verwendet wird, um die abzurufenden Informationen anzugeben. Wird auch zum Empfangen von Informationen über die Registerkarte verwendet. Diese Struktur wird mit den Funktionen `InsertItem`, `GetItem`und `SetItem` Member verwendet.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn erfolgreich; Andernfalls false.

### <a name="remarks"></a>Hinweise

Wenn die Nachricht gesendet wird, gibt der `mask` Member an, welche Attribute zurückgegeben werden sollen. Wenn das `mask`-Element den TCIF_TEXT Wert angibt, muss der `pszText` Member die Adresse des Puffers enthalten, der den Element Text empfängt, und der `cchTextMax` Member muss die Größe des Puffers angeben.

- `mask`

   Wert, der angibt, welche `TCITEM` Strukturmember abgerufen oder festgelegt werden sollen. Dieser Member kann NULL oder eine Kombination der folgenden Werte sein:

   - TCIF_TEXT das `pszText` Mitglied gültig ist.

   - TCIF_IMAGE das `iImage` Mitglied gültig ist.

   - TCIF_PARAM das `lParam` Mitglied gültig ist.

   - TCIF_RTLREADING wird der Text `pszText` mithilfe von rechts-nach-Links-Lesefolge auf Hebräisch-oder arabischen Systemen angezeigt.

   - TCIF_STATE das `dwState` Mitglied gültig ist.

- `pszText`

   Ein Zeiger auf eine mit NULL endenden Zeichenfolge, die den Registerkarten Text enthält, wenn die Strukturinformationen über eine Registerkarte enthält. Wenn die Strukturinformationen empfängt, gibt dieser Member die Adresse des Puffers an, der den Registerkarten Text empfängt.

- `cchTextMax`

   Größe des Puffers, auf den `pszText`zeigt. Dieser Member wird ignoriert, wenn die Struktur keine Informationen empfängt.

- `iImage` Index in der Bildliste des Registerkarten-Steuer Elements oder-1, wenn kein Bild für die Registerkarte vorhanden ist.

- `lParam`

   Anwendungs definierte Daten, die der Registerkarte zugeordnet sind. Wenn pro Registerkarte mehr als vier Bytes von Anwendungs definierten Daten vorhanden sind, muss eine Anwendung eine Struktur definieren und anstelle der `TCITEM` Struktur verwenden. Der erste Member der Anwendungs definierten Struktur muss eine [tcitemheader](/windows/win32/api/commctrl/ns-commctrl-tcitemheaderw)-Struktur sein. Die `TCITEMHEADER`-Struktur ist identisch mit der `TCITEM`-Struktur, aber ohne den `lParam`-Member. Der Unterschied zwischen der Größe ihrer Struktur und der Größe der `TCITEMHEADER` Struktur sollte der Anzahl zusätzlicher Bytes pro Registerkarte entsprechen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTabCtrl#4](../../mfc/reference/codesnippet/cpp/ctabctrl-class_4.cpp)]

##  <a name="getitemcount"></a>CTabCtrl:: GetItemCount

Ruft die Anzahl der Registerkarten im Registerkarten-Steuerelement ab.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Rückgabewert

Anzahl der Elemente im Registerkarten-Steuerelement.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CPropertySheet:: gettabcontrol](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="getitemrect"></a>CTabCtrl:: GetItemRect

Ruft das umgebende Rechteck für die angegebene Registerkarte in einem Registerkarten-Steuerelement ab.

```
BOOL GetItemRect(int nItem,   LPRECT lpRect) const;
```

### <a name="parameters"></a>Parameter

*nitem*<br/>
NULL basierter Index des Registerkarten Elements.

*lprect*<br/>
Ein Zeiger auf eine [Rect](/previous-versions/dd162897\(v=vs.85\)) -Struktur, die das umschließende Rechteck der Registerkarte empfängt. Diese Koordinaten verwenden den aktuellen Kartenmodus des Viewports.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CPropertySheet:: gettabcontrol](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="getitemstate"></a>CTabCtrl:: GetItemState

Ruft den Zustand des Registerkarten-Steuer Elements ab, das durch *nitem*identifiziert wird.

```
DWORD GetItemState(
    int nItem,
    DWORD dwMask) const;
```

### <a name="parameters"></a>Parameter

*nitem*<br/>
Die null basierte Indexnummer des Elements, für das Zustandsinformationen abgerufen werden sollen.

*dwMask*<br/>
Maske, die angibt, welche der Statusflags des Elements zurückgegeben werden soll. Eine Liste der Werte finden Sie unter dem Mask-Member der [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) -Struktur, wie im Windows SDK beschrieben.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf einen DWORD-Wert, der die Zustandsinformationen empfängt. Kann einer der folgenden Werte sein:

|Wert|Beschreibung|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|Das Registerkarten-Steuerelement ist ausgewählt.|
|TCIS_HIGHLIGHTED|Das Registerkarten-Steuerelement wird hervorgehoben, und die Registerkarte und der Text werden mithilfe der aktuellen Hervorhebungs Farbe gezeichnet. Wenn Sie Hervorhebungs Farbe verwenden, handelt es sich hierbei um eine echte Interpolation, nicht um eine Dithering-Farbe.|

### <a name="remarks"></a>Hinweise

Der Zustand eines Elements wird durch den `dwState` Member der `TCITEM`-Struktur angegeben.

##  <a name="getrowcount"></a>CTabCtrl:: GetRowCount

Ruft die aktuelle Anzahl von Zeilen in einem Registerkarten-Steuerelement ab.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Zeilen der Registerkarten im Registerkarten-Steuerelement.

### <a name="remarks"></a>Hinweise

Nur Registerkarten-Steuerelemente mit dem TCS_MULTILINE-Stil können mehrere Zeilen mit Registerkarten enthalten.

##  <a name="gettooltips"></a>CTabCtrl:: gettooltips

Ruft das Handle des QuickInfo-Steuer Elements ab, das einem Registerkarten-Steuerelement zugeordnet ist.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Rückgabewert

Handle des QuickInfo-Steuer Elements, wenn es erfolgreich war. andernfalls NULL.

### <a name="remarks"></a>Hinweise

Ein Registerkarten-Steuerelement erstellt ein QuickInfo-Steuerelement, wenn es den TCS_TOOLTIPS Stil hat. Sie können einem Registerkarten-Steuerelement auch ein QuickInfo-Steuerelement zuweisen, indem Sie die `SetToolTips` Member-Funktion verwenden.

##  <a name="highlightitem"></a>CTabCtrl:: highlightitem

Legt den Hervorhebungs Zustand eines Registerkarten Elements fest.

```
BOOL HighlightItem(int idItem,   BOOL fHighlight = TRUE);
```

### <a name="parameters"></a>Parameter

*iditem*<br/>
NULL basierter Index eines Registerkarten-Steuer Elements.

*f-Hervorhebung*<br/>
Ein Wert, der den festzulegenden Hervorhebungs Zustand angibt. Wenn dieser Wert true ist, wird die Registerkarte hervorgehoben. Wenn der Wert false ist, wird die Registerkarte auf den Standardzustand festgelegt.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert die Win32-Nachricht [TCM_HIGHLIGHTITEM](/windows/win32/Controls/tcm-highlightitem), wie in der Windows SDK beschrieben.

##  <a name="hittest"></a>CTabCtrl:: HitTest

Bestimmt, welche Registerkarte (sofern vorhanden) an der angegebenen Bildschirmposition liegt.

```
int HitTest(TCHITTESTINFO* pHitTestInfo) const;
```

### <a name="parameters"></a>Parameter

*"phittestinfo"*<br/>
Zeiger auf eine [tchittestinfo](/windows/win32/api/commctrl/ns-commctrl-tchittestinfo) -Struktur, wie im Windows SDK beschrieben, die die zu testende Bildschirmposition angibt.

### <a name="return-value"></a>Rückgabewert

Gibt den NULL basierten Index der Registerkarte zurück, oder-1, wenn sich keine Registerkarte an der angegebenen Position befindet.

##  <a name="insertitem"></a>CTabCtrl:: InsertItem

Fügt eine neue Registerkarte in ein vorhandenes Register Steuerelement ein.

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

*nitem*<br/>
NULL basierter Index der neuen Registerkarte.

*ptabctrlitem*<br/>
Ein Zeiger auf eine [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) -Struktur, die die Attribute der Registerkarte angibt.

*lpszitem*<br/>
Adresse einer auf NULL endenden Zeichenfolge, die den Text der Registerkarte enthält.

*nbild*<br/>
Der null basierte Index eines Bilds, das aus einer Bildliste eingefügt werden soll.

*nmask*<br/>
Gibt an, welche `TCITEM` Struktur Attribute festgelegt werden sollen. Kann 0 (null) oder eine Kombination der folgenden Werte sein:

- TCIF_TEXT das `pszText` Mitglied gültig ist.

- TCIF_IMAGE das `iImage` Mitglied gültig ist.

- TCIF_PARAM das *LPARAM* -Element gültig ist.

- TCIF_RTLREADING wird der Text `pszText` mithilfe von rechts-nach-Links-Lesefolge auf Hebräisch-oder arabischen Systemen angezeigt.

- TCIF_STATE das *dwstate* -Member gültig ist.

*lParam*<br/>
Anwendungs definierte Daten, die der Registerkarte zugeordnet sind.

*dwstate*<br/>
Gibt Werte für die Zustände des Elements an. Weitere Informationen finden Sie unter [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) in der Windows SDK.

*dwanemask*<br/>
Gibt an, welche Zustände festgelegt werden sollen. Weitere Informationen finden Sie unter [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) in der Windows SDK.

### <a name="return-value"></a>Rückgabewert

NULL basierter Index der neuen Registerkarte, wenn erfolgreich. andernfalls-1.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTabCtrl#5](../../mfc/reference/codesnippet/cpp/ctabctrl-class_5.cpp)]

##  <a name="removeimage"></a>CTabCtrl:: removeimage

Entfernt das angegebene Bild aus der Bildliste eines Registerkarten-Steuer Elements.

```
void RemoveImage(int nImage);
```

### <a name="parameters"></a>Parameter

*nbild*<br/>
Der null basierte Index des zu entfernenden Bilds.

### <a name="remarks"></a>Hinweise

Das Registerkarten-Steuerelement aktualisiert den Bildindex jeder Registerkarte, sodass jede Registerkarte dem gleichen Bild zugeordnet bleibt.

##  <a name="setcurfocus"></a>CTabCtrl:: setcurrfocus

Legt den Fokus auf eine angegebene Registerkarte in einem Registerkarten-Steuerelement fest.

```
void SetCurFocus(int nItem);
```

### <a name="parameters"></a>Parameter

*nitem*<br/>
Gibt den Index der Registerkarte an, die den Fokus erhält.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [TCM_SETCURFOCUS](/windows/win32/Controls/tcm-setcurfocus), wie in der Windows SDK beschrieben.

##  <a name="setcursel"></a>CTabCtrl:: setcurrsel

Wählt eine Registerkarte in einem Register Steuerelement aus.

```
int SetCurSel(int nItem);
```

### <a name="parameters"></a>Parameter

*nitem*<br/>
Der null basierte Index des Elements, das ausgewählt werden soll.

### <a name="return-value"></a>Rückgabewert

NULL basierter Index der zuvor ausgewählten Registerkarte, wenn erfolgreich, andernfalls-1.

### <a name="remarks"></a>Hinweise

Ein Registerkarten-Steuerelement sendet keine TCN_SELCHANGING oder TCN_SELCHANGE Benachrichtigungs Meldung, wenn mithilfe dieser Funktion eine Registerkarte ausgewählt wird. Diese Benachrichtigungen werden mithilfe von WM_NOTIFY gesendet, wenn der Benutzer auf die Tastatur klickt oder diese verwendet, um die Registerkarten zu ändern.

##  <a name="setextendedstyle"></a>CTabCtrl:: abtextendedstyle

Legt die erweiterten Stile für ein Registerkarten-Steuerelement fest.

```
DWORD SetExtendedStyle(DWORD dwNewStyle,   DWORD dwExMask = 0);
```

### <a name="parameters"></a>Parameter

*dwnewstyle*<br/>
Ein Wert, der eine Kombination aus erweiterten Formatvorlagen für Steuerelemente angibt

*dwexmask*<br/>
Ein DWORD-Wert, der angibt, welche Stile in *dwnewstyle* betroffen sein sollen. Nur die erweiterten Stile in *dwexmask* werden geändert. Alle anderen Stile werden unverändert beibehalten. Wenn dieser Parameter 0 (null) ist, werden alle Stile in *dwnewstyle* beeinträchtigt.

### <a name="return-value"></a>Rückgabewert

Ein DWORD-Wert, der das vorherige [Register Steuerelement erweiterte Stile](/windows/win32/Controls/tab-control-extended-styles)enthält, wie im Windows SDK beschrieben.

### <a name="return-value"></a>Rückgabewert

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [TCM_SETEXTENDEDSTYLE](/windows/win32/Controls/tcm-setextendedstyle), wie in der Windows SDK beschrieben.

##  <a name="setimagelist"></a>CTabCtrl:: SetImageList

Weist einem Registerkarten-Steuerelement eine Bildliste zu.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parameter

*pimagelist*<br/>
Ein Zeiger auf die Bildliste, die dem Registerkarten-Steuerelement zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf die vorherige Bildliste oder NULL zurück, wenn keine vorherige Bildliste vorhanden ist.

##  <a name="setitem"></a>CTabCtrl:: System Item

Legt einige oder alle Attribute einer Registerkarte fest.

```
BOOL SetItem(int nItem,   TCITEM* pTabCtrlItem);
```

### <a name="parameters"></a>Parameter

*nitem*<br/>
Der null basierte Index des Elements.

*ptabctrlitem*<br/>
Zeiger auf eine [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) -Struktur, die die neuen Element Attribute enthält. Der `mask` Member gibt an, welche Attribute festgelegt werden sollen. Wenn das `mask`-Element den TCIF_TEXT Wert angibt, ist der `pszText` Member die Adresse einer auf NULL endenden Zeichenfolge, und der `cchTextMax` Member wird ignoriert.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [GetItem](#getitem).

##  <a name="setitemextra"></a>CTabCtrl:: "ctabtemextra"

Legt die Anzahl von Bytes pro Registerkarte fest, die für Anwendungs definierte Daten in einem Registerkarten-Steuerelement reserviert ist.

```
BOOL SetItemExtra(int nBytes);
```

### <a name="parameters"></a>Parameter

*nBytes*<br/>
Die Anzahl der zusätzlichen bytes, die festgelegt werden sollen.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [TCM_SETITEMEXTRA](/windows/win32/Controls/tcm-setitemextra), wie in der Windows SDK beschrieben.

##  <a name="setitemsize"></a>CTabCtrl:: settemsize

Legt die Breite und Höhe des Registerkarten-Steuerelements fest.

```
CSize SetItemSize(CSize size);
```

### <a name="parameters"></a>Parameter

*size*<br/>
Die neue Breite und Höhe des Registerkarten-Steuerelements in Pixeln.

### <a name="return-value"></a>Rückgabewert

Gibt die alte Breite und Höhe des Registerkarten-Steuerelements zurück.

##  <a name="setitemstate"></a>CTabCtrl:: abtitemstate

Legt den Zustand des Registerkarten-Steuer Elements fest, das von *nitem*identifiziert wird.

```
BOOL SetItemState(
    int nItem,
    DWORD dwMask,
    DWORD dwState);
```

### <a name="parameters"></a>Parameter

*nitem*<br/>
Die null basierte Indexnummer des Elements, für das Zustandsinformationen festgelegt werden sollen.

*dwMask*<br/>
Maske, die angibt, welche der Zustandsflags des Elements festgelegt werden sollen. Eine Liste der Werte finden Sie unter dem Mask-Member der [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) -Struktur, wie im Windows SDK beschrieben.

*dwstate*<br/>
Ein Verweis auf einen DWORD-Wert, der die Zustandsinformationen enthält. Kann einer der folgenden Werte sein:

|Wert|Beschreibung|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|Das Registerkarten-Steuerelement ist ausgewählt.|
|TCIS_HIGHLIGHTED|Das Registerkarten-Steuerelement wird hervorgehoben, und die Registerkarte und der Text werden mithilfe der aktuellen Hervorhebungs Farbe gezeichnet. Wenn Sie Hervorhebungs Farbe verwenden, handelt es sich hierbei um eine echte Interpolation, nicht um eine Dithering-Farbe.|

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

##  <a name="setmintabwidth"></a>CTabCtrl:: setmintabwidth

Legt die minimale Breite von Elementen in einem Registerkarten-Steuerelement fest.

```
int SetMinTabWidth(int cx);
```

### <a name="parameters"></a>Parameter

*verschoben*<br/>
Minimale Breite, die für ein Registerkarten-Steuerelement festgelegt werden soll. Wenn dieser Parameter auf-1 festgelegt ist, verwendet das Steuerelement die Standard Registerkarten Breite.

### <a name="return-value"></a>Rückgabewert

Die vorherige minimale Registerkarten Breite.

### <a name="return-value"></a>Rückgabewert

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [TCM_SETMINTABWIDTH](/windows/win32/Controls/tcm-setmintabwidth), wie in der Windows SDK beschrieben.

##  <a name="setpadding"></a>CTabCtrl:: setPadding

Legt den Leerraum (Padding) um das Symbol und die Bezeichnung der einzelnen Registerkarten in einem Registerkarten-Steuerelement fest.

```
void SetPadding(CSize size);
```

### <a name="parameters"></a>Parameter

*size*<br/>
Legt den Leerraum (Padding) um das Symbol und die Bezeichnung der einzelnen Registerkarten in einem Registerkarten-Steuerelement fest.

##  <a name="settooltips"></a>CTabCtrl:: SetToolTips

Weist einem Registerkarten-Steuerelement ein QuickInfo-Steuerelement zu.

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Parameter

*pwndtip*<br/>
Handle des QuickInfo-Steuer Elements.

### <a name="remarks"></a>Hinweise

Sie können das QuickInfo-Steuerelement, das einem Registerkarten-Steuerelement zugeordnet ist, abrufen, indem Sie `GetToolTips`abrufen.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CPropertySheet:: gettabcontrol](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="see-also"></a>Siehe auch

[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CHeaderCtrl-Klasse](../../mfc/reference/cheaderctrl-class.md)<br/>
[CListCtrl-Klasse](../../mfc/reference/clistctrl-class.md)
