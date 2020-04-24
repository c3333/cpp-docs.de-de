---
title: CComboBoxEx-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComboBoxEx
- AFXCMN/CComboBoxEx
- AFXCMN/CComboBoxEx::CComboBoxEx
- AFXCMN/CComboBoxEx::Create
- AFXCMN/CComboBoxEx::CreateEx
- AFXCMN/CComboBoxEx::DeleteItem
- AFXCMN/CComboBoxEx::GetComboBoxCtrl
- AFXCMN/CComboBoxEx::GetEditCtrl
- AFXCMN/CComboBoxEx::GetExtendedStyle
- AFXCMN/CComboBoxEx::GetImageList
- AFXCMN/CComboBoxEx::GetItem
- AFXCMN/CComboBoxEx::HasEditChanged
- AFXCMN/CComboBoxEx::InsertItem
- AFXCMN/CComboBoxEx::SetExtendedStyle
- AFXCMN/CComboBoxEx::SetImageList
- AFXCMN/CComboBoxEx::SetItem
- AFXCMN/CComboBoxEx::SetWindowTheme
helpviewer_keywords:
- CComboBoxEx [MFC], CComboBoxEx
- CComboBoxEx [MFC], Create
- CComboBoxEx [MFC], CreateEx
- CComboBoxEx [MFC], DeleteItem
- CComboBoxEx [MFC], GetComboBoxCtrl
- CComboBoxEx [MFC], GetEditCtrl
- CComboBoxEx [MFC], GetExtendedStyle
- CComboBoxEx [MFC], GetImageList
- CComboBoxEx [MFC], GetItem
- CComboBoxEx [MFC], HasEditChanged
- CComboBoxEx [MFC], InsertItem
- CComboBoxEx [MFC], SetExtendedStyle
- CComboBoxEx [MFC], SetImageList
- CComboBoxEx [MFC], SetItem
- CComboBoxEx [MFC], SetWindowTheme
ms.assetid: 33ca960a-2409-478c-84a4-a2ee8ecfe8f7
ms.openlocfilehash: a948d54be17103fa83848ff5f0e86dd2c522f0a3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754825"
---
# <a name="ccomboboxex-class"></a>CComboBoxEx-Klasse

Erweitert das Kombinationsfeld-Steuerelement durch die Unterstützung für Bildlisten.

## <a name="syntax"></a>Syntax

```
class CComboBoxEx : public CComboBox
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComboBoxEx::CComboBoxEx](#ccomboboxex)|Erstellt ein `CComboBoxEx`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComboBoxEx::Erstellen](#create)|Erstellt das Kombinationsfeld und `CComboBoxEx` fügt es an das Objekt an.|
|[CComboBoxEx::CreateEx](#createex)|Erstellt ein Kombinationsfeld mit den angegebenen erweiterten `ComboBoxEx` Windows-Stilen und fügt es an ein Objekt an.|
|[CComboBoxEx::DeleteItem](#deleteitem)|Entfernt ein Element `ComboBoxEx` aus einem Steuerelement.|
|[CComboBoxEx::GetComboBoxCtrl](#getcomboboxctrl)|Ruft einen Zeiger auf das untergeordnete Kombinationsfeldsteuerelement ab.|
|[CComboBoxEx::GetEditCtrl](#geteditctrl)|Ruft das Handle zum Bearbeitungssteuerelementteil `ComboBoxEx` eines Steuerelements ab.|
|[CComboBoxEx::GetExtendedStyle](#getextendedstyle)|Ruft die erweiterten Stile ab, `ComboBoxEx` die für ein Steuerelement verwendet werden.|
|[CComboBoxEx::GetImageList](#getimagelist)|Ruft einen Zeiger auf die Bildliste `ComboBoxEx` ab, die einem Steuerelement zugewiesen ist.|
|[CComboBoxEx::GetItem](#getitem)|Ruft Artikelinformationen für `ComboBoxEx` ein bestimmtes Element ab.|
|[CComboBoxEx::HasEditChanged](#haseditchanged)|Bestimmt, ob der Benutzer den `ComboBoxEx` Inhalt des Bearbeitungssteuerelements durch Eingabe geändert hat.|
|[CComboBoxEx::InsertItem](#insertitem)|Fügt ein neues Element `ComboBoxEx` in ein Steuerelement ein.|
|[CComboBoxEx::SetExtendedStyle](#setextendedstyle)|Legt erweiterte Stile `ComboBoxEx` innerhalb eines Steuerelements fest.|
|[CComboBoxEx::SetImageList](#setimagelist)|Legt eine Bildliste `ComboBoxEx` für ein Steuerelement fest.|
|[CComboBoxEx::SetItem](#setitem)|Legt die Attribute für ein `ComboBoxEx` Element in einem Steuerelement fest.|
|[CComboBoxEx::SetWindowTheme](#setwindowtheme)|Legt den visuellen Stil des erweiterten Kombinationsfeldsteuerelements fest.|

## <a name="remarks"></a>Bemerkungen

Wenn `CComboBoxEx` Sie Kombinationsfeldsteuerelemente erstellen, müssen Sie keinen eigenen Bildzeichnungscode mehr implementieren. Verwenden Sie `CComboBoxEx` stattdessen den Zugriff auf Bilder aus einer Bildliste.

## <a name="image-list-support"></a>Image List-Unterstützung

In einem Standard-Kombinationsfeld ist der Besitzer des Kombinationsfelds für das Zeichnen eines Bildes verantwortlich, indem er das Kombinationsfeld als Besitzer-Zeichnungssteuerelement erstellt. Wenn Sie `CComboBoxEx`verwenden, müssen Sie die Zeichnungsstile nicht festlegen, CBS_OWNERDRAWFIXED und CBS_HASSTRINGS, da sie impliziert sind. Andernfalls müssen Sie Code schreiben, um Zeichnungsvorgänge auszuführen. Ein `CComboBoxEx` Steuerelement unterstützt bis zu drei Bilder pro Element: eines für einen ausgewählten Zustand, eines für einen nicht ausgewählten Zustand und eines für ein Überlagerungsbild.

## <a name="styles"></a>Stile

`CComboBoxEx`unterstützt die Stile CBS_SIMPLE, CBS_DROPDOWN, CBS_DROPDOWNLIST und WS_CHILD. Alle anderen Stile, die beim Erstellen des Fensters übergeben wurden, werden vom Steuerelement ignoriert. Nachdem das Fenster erstellt wurde, können Sie weitere `CComboBoxEx` Kombinationsfeldstile bereitstellen, indem Sie die Memberfunktion [SetExtendedStyle](#setextendedstyle)aufrufen. Mit diesen Stilen können Sie:

- Legen Sie Zeichenfolgensuchen in der Liste fest, dass die Groß-/Kleinschreibung beachtet wird.

- Erstellen Sie ein Kombinationsfeldsteuerelement, das die Schrägstriche\\('/'), den umgekehrten Schrägstrich (' '') und die Periodenzeichen ('.') als Worttrennzeichen verwendet. Dadurch können Benutzer mit der Tastenkombination STRG+ ARROW von Wort zu Wort springen.

- Legen Sie das Kombinationsfeldsteuerelement so fest, dass ein Bild angezeigt oder nicht angezeigt wird. Wenn kein Bild angezeigt wird, kann das Kombinationsfeld den Texteinzug entfernen, der ein Bild enthält.

- Erstellen Sie ein schmales Kombinationsfeldsteuerelement, einschließlich der Größe, sodass es das darin enthaltene breitere Kombinationsfeld schneidet.

Diese Stilflags werden weiter unter [Verwenden von CComboBoxEx](../../mfc/using-ccomboboxex.md)beschrieben.

## <a name="item-retention-and-callback-item-attributes"></a>Artikelaufbewahrungs- und Rückrufelementattribute

Elementinformationen, wie Z. B. Indizes für Elemente und Bilder, Einzugswerte und Textzeichenfolgen, werden in der Win32-Struktur [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw)gespeichert, wie im Windows SDK beschrieben. Die Struktur enthält auch Elemente, die Rückrufflags entsprechen.

Eine ausführliche, konzeptionelle Diskussion finden Sie unter [Verwenden von CComboBoxEx](../../mfc/using-ccomboboxex.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

`CComboBoxEx`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcmn.h

## <a name="ccomboboxexccomboboxex"></a><a name="ccomboboxex"></a>CComboBoxEx::CComboBoxEx

Rufen Sie diese Memberfunktion auf, um ein `CComboBoxEx` Objekt zu erstellen.

```
CComboBoxEx();
```

## <a name="ccomboboxexcreate"></a><a name="create"></a>CComboBoxEx::Erstellen

Erstellt das Kombinationsfeld und `CComboBoxEx` fügt es an das Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwStyle*<br/>
Gibt die Kombination von Kombinationsfeldstilen an, die auf das Kombinationsfeld angewendet werden. Weitere Informationen zu Stilen finden Sie unter **Anmerkungen** unten.

*Rect*<br/>
Ein Verweis auf ein [CRect-Objekt](../../atl-mfc-shared/reference/crect-class.md) oder eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) d. h. die Position und Größe des Kombinationsfelds.

*pParentWnd*<br/>
Ein Zeiger auf ein [CWnd-Objekt,](../../mfc/reference/cwnd-class.md) das das übergeordnete `CDialog`Fenster des Kombinationsfelds ist (in der Regel a ). Es darf nicht NULL sein.

*nID*<br/>
Gibt die Steuer-ID des Kombinationsfelds an.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Objekt erfolgreich erstellt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Erstellen `CComboBoxEx` Sie ein Objekt in zwei Schritten:

1. Rufen Sie [CComboBoxEx](#ccomboboxex) auf, um ein `CComboBoxEx` Objekt zu erstellen.

1. Rufen Sie diese Memberfunktion auf, die das erweiterte `CComboBoxEx` Windows-Kombinationsfeld erstellt und an das Objekt anfügt.

Beim Aufruf `Create`initialisiert MFC die allgemeinen Steuerelemente.

Wenn Sie das Kombinationsfeld erstellen, können Sie einen oder alle der folgenden Kombinationsfeldstile angeben:

- CBS_SIMPLE

- CBS_DROPDOWN

- CBS_DROPDOWNLIST

- CBS_AUTOHSCROLL

- Ws_child

Alle anderen Stile, die beim Erstellen des Fensters übergeben wurden, werden ignoriert. Das `ComboBoxEx` Steuerelement unterstützt auch erweiterte Stile, die zusätzliche Funktionen bereitstellen. Diese Stile werden in [ComboBoxEx-Steuerelement-Erweiterten Stilen](/windows/win32/Controls/comboboxex-control-extended-styles)im Windows SDK beschrieben. Legen Sie diese Stile fest, indem Sie [SetExtendedStyle](#setextendedstyle)aufrufen.

Wenn Sie erweiterte Fensterstile mit Ihrem Steuerelement verwenden `Create`möchten, rufen Sie [CreateEx](#createex) anstelle von auf.

## <a name="ccomboboxexcreateex"></a><a name="createex"></a>CComboBoxEx::CreateEx

Rufen Sie diese Funktion auf, um ein erweitertes Kombinationsfeldsteuerelement (ein untergeordnetes Fenster) zu erstellen und es dem `CComboBoxEx` Objekt zuzuordnen.

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
Der Stil des Kombinationsfeldsteuerelements. Weitere Informationen finden Sie [unter Erstellen](#create) einer Liste von Stilen.

*Rect*<br/>
Ein Verweis auf eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die die Größe und Position des zu erstellenden Fensters in den Clientkoordinaten von *pParentWnd*beschreibt.

*pParentWnd*<br/>
Ein Zeiger auf das Fenster, das das übergeordnete Steuerelement ist.

*nID*<br/>
Die untergeordnete Fenster-ID des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Verwenden `CreateEx` Sie, anstatt `Create` erweiterte Windows-Formatvorlagen anzuwenden, die durch das Windows-Vorwort für erweiterte Stile **WS_EX_** angegeben werden.

`CreateEx`erstellt das Steuerelement mit den erweiterten Windows-Stilen, die von *dwExStyle*angegeben werden. Sie müssen erweiterte Stile festlegen, die für ein erweitertes Kombinationsfeldsteuerelement mit [SetExtendedStyle](#setextendedstyle)spezifisch sind. Verwenden Sie `CreateEx` z. B., um `SetExtendedStyle` Stile wie WS_EX_CONTEXTHELP festzulegen, aber verwenden Sie, um Stile wie CBES_EX_CASESENSITIVE festzulegen. Weitere Informationen finden Sie in den Imformat [ComboBoxEx Control Extended Styles](/windows/win32/Controls/comboboxex-control-extended-styles) im Windows SDK.

## <a name="ccomboboxexdeleteitem"></a><a name="deleteitem"></a>CComboBoxEx::DeleteItem

Entfernt ein Element `ComboBoxEx` aus einem Steuerelement.

```
int DeleteItem(int iIndex);
```

### <a name="parameters"></a>Parameter

*iIndex*<br/>
Nullbasierter Index des zu entfernenden Elements.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente, die im Steuerelement verbleiben. Wenn *iIndex* ungültig ist, gibt die Funktion CB_ERR zurück.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert die Funktionalität der Meldung [CBEM_DELETEITEM](/windows/win32/Controls/cbem-deleteitem), wie im Windows SDK beschrieben. Wenn Sie DeleteItem aufrufen, wird eine [WM_NOTIFY](/windows/win32/controls/wm-notify) Nachricht mit CBEN_DELETEITEM Benachrichtigung an das übergeordnete Fenster gesendet.

## <a name="ccomboboxexgetcomboboxctrl"></a><a name="getcomboboxctrl"></a>CComboBoxEx::GetComboBoxCtrl

Rufen Sie diese Memberfunktion auf, um einen `CComboBoxEx` Zeiger auf ein Kombinationsfeldsteuerelement innerhalb eines Objekts abzurufen.

```
CComboBox* GetComboBoxCtrl();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein `CComboBox`-Objekt.

### <a name="remarks"></a>Bemerkungen

Das `CComboBoxEx` Steuerelement besteht aus einem übergeordneten Fenster, `CComboBox`das eine kapselt.

Das `CComboBox` Objekt, auf das der Rückgabewert zeigt, ist ein temporäres Objekt und wird während der nächsten Verarbeitungszeit im Leerlauf zerstört.

## <a name="ccomboboxexgeteditctrl"></a><a name="geteditctrl"></a>CComboBoxEx::GetEditCtrl

Rufen Sie diese Memberfunktion auf, um einen Zeiger auf das Bearbeitungssteuerelement für ein Kombinationsfeld abzurufen.

```
CEdit* GetEditCtrl();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CEdit-Objekt.](../../mfc/reference/cedit-class.md)

### <a name="remarks"></a>Bemerkungen

Ein `CComboBoxEx` Steuerelement verwendet ein Bearbeitungsfeld, wenn es mit dem Stil CBS_DROPDOWN erstellt wird.

Das `CEdit` Objekt, auf das der Rückgabewert zeigt, ist ein temporäres Objekt und wird während der nächsten Verarbeitungszeit im Leerlauf zerstört.

## <a name="ccomboboxexgetextendedstyle"></a><a name="getextendedstyle"></a>CComboBoxEx::GetExtendedStyle

Rufen Sie diese Memberfunktion auf, `CComboBoxEx` um die erweiterten Stile abzurufen, die für ein Steuerelement verwendet werden.

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>Rückgabewert

Der DWORD-Wert, der die erweiterten Stile enthält, die für das Kombinationsfeldsteuerelement verwendet werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu diesen Stilen finden Sie unter [ComboBoxEx Control Extended Styles](/windows/win32/Controls/comboboxex-control-extended-styles) im Windows SDK.

## <a name="ccomboboxexgetimagelist"></a><a name="getimagelist"></a>CComboBoxEx::GetImageList

Rufen Sie diese Memberfunktion auf, um einen `CComboBoxEx` Zeiger auf die Bildliste zu erhalten, die von einem Steuerelement verwendet wird.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CImageList-Objekt.](../../mfc/reference/cimagelist-class.md) Wenn dies fehlschlägt, gibt diese Memberfunktion NULL zurück.

### <a name="remarks"></a>Bemerkungen

Das `CImageList` Objekt, auf das der Rückgabewert zeigt, ist ein temporäres Objekt und wird während der nächsten Verarbeitungszeit im Leerlauf zerstört.

## <a name="ccomboboxexgetitem"></a><a name="getitem"></a>CComboBoxEx::GetItem

Ruft Artikelinformationen für `ComboBoxEx` ein bestimmtes Element ab.

```
BOOL GetItem(COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parameter

*pCBItem*<br/>
Ein Zeiger auf eine [COMBOBOXEXITEM-Struktur,](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) die die Elementinformationen empfängt.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Vorgang erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert die Funktionalität der Meldung [CBEM_GETITEM](/windows/win32/Controls/cbem-getitem), wie im Windows SDK beschrieben.

## <a name="ccomboboxexhaseditchanged"></a><a name="haseditchanged"></a>CComboBoxEx::HasEditChanged

Bestimmt, ob der Benutzer den `ComboBoxEx` Inhalt des Bearbeitungssteuerelements durch Eingabe geändert hat.

```
BOOL HasEditChanged();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Benutzer das Bearbeitungsfeld des Steuerelements eingegeben hat; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert die Funktionalität der Meldung [CBEM_HASEDITCHANGED](/windows/win32/Controls/cbem-haseditchanged), wie im Windows SDK beschrieben.

## <a name="ccomboboxexinsertitem"></a><a name="insertitem"></a>CComboBoxEx::InsertItem

Fügt ein neues Element `ComboBoxEx` in ein Steuerelement ein.

```
int InsertItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parameter

*pCBItem*<br/>
Ein Zeiger auf eine [COMBOBOXEXITEM-Struktur,](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) die die Elementinformationen empfängt. Diese Struktur enthält Rückrufflagwerte für das Element.

### <a name="return-value"></a>Rückgabewert

Der Index, an dem das neue Element eingefügt wurde, wenn es erfolgreich ist; andernfalls -1.

### <a name="remarks"></a>Bemerkungen

Wenn Sie `InsertItem`anrufen, wird eine [WM_NOTIFY](/windows/win32/controls/wm-notify) Nachricht mit [CBEN_INSERTITEM](/windows/win32/Controls/cben-insertitem) Benachrichtigung an das übergeordnete Fenster gesendet.

## <a name="ccomboboxexsetextendedstyle"></a><a name="setextendedstyle"></a>CComboBoxEx::SetExtendedStyle

Rufen Sie diese Memberfunktion auf, um die erweiterten Stile festzulegen, die für ein erweitertes Steuerelement im Kombinationsfeld verwendet werden.

```
DWORD SetExtendedStyle(
    DWORD dwExMask,
    DWORD dwExStyles);
```

### <a name="parameters"></a>Parameter

*dwExMask*<br/>
Ein DWORD-Wert, der angibt, welche Stile in *dwExStyles* betroffen sein sollen. Nur die erweiterten Stile in *dwExMask* werden geändert. Alle anderen Stile werden beibehalten, wie sie sind. Wenn dieser Parameter Null ist, sind alle Stile in *dwExStyles* betroffen.

*dwExStyles*<br/>
Ein DWORD-Wert, der erweiterte Formatvorlagen für das Kombinationsfeldsteuerelement enthält, das für das Steuerelement festgelegt werden soll.

### <a name="return-value"></a>Rückgabewert

Ein DWORD-Wert, der die erweiterten Stile enthält, die zuvor für das Steuerelement verwendet wurden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu diesen Stilen finden Sie unter [ComboBoxEx Control Extended Styles](/windows/win32/Controls/comboboxex-control-extended-styles) im Windows SDK.

Um ein erweitertes Kombinationsfeld mit erweiterten Fensterstilen zu erstellen, verwenden Sie [CreateEx](#createex).

## <a name="ccomboboxexsetimagelist"></a><a name="setimagelist"></a>CComboBoxEx::SetImageList

Legt eine Bildliste `ComboBoxEx` für ein Steuerelement fest.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parameter

*pImageList*<br/>
Ein Zeiger auf `CImageList` ein Objekt, das `CComboBoxEx` die Bilder enthält, die mit dem Steuerelement verwendet werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CImageList-Objekt,](../../mfc/reference/cimagelist-class.md) das `CComboBoxEx` die zuvor vom Steuerelement verwendeten Bilder enthält. NULL, wenn zuvor keine Bildliste festgelegt wurde.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert die Funktionalität der [CBEM_SETIMAGELIST](/windows/win32/Controls/cbem-setimagelist), wie im Windows SDK beschrieben. Wenn Sie die Höhe des Standardmäßigen Bearbeitungssteuerelements ändern, rufen Sie die Win32-Funktion [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) auf, um die Größe des Steuerelements nach dem Aufruf zu `SetImageList`ändern, oder es wird nicht ordnungsgemäß angezeigt.

Das `CImageList` Objekt, auf das der Rückgabewert zeigt, ist ein temporäres Objekt und wird während der nächsten Verarbeitungszeit im Leerlauf zerstört.

## <a name="ccomboboxexsetitem"></a><a name="setitem"></a>CComboBoxEx::SetItem

Legt die Attribute für ein `ComboBoxEx` Element in einem Steuerelement fest.

```
BOOL SetItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parameter

*pCBItem*<br/>
Ein Zeiger auf eine [COMBOBOXEXITEM-Struktur,](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) die die Elementinformationen empfängt.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Vorgang erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert die Funktionalität der Meldung [CBEM_SETITEM](/windows/win32/Controls/cbem-setitem), wie im Windows SDK beschrieben.

## <a name="ccomboboxexsetwindowtheme"></a><a name="setwindowtheme"></a>CComboBoxEx::SetWindowTheme

Legt den visuellen Stil des erweiterten Kombinationsfeldsteuerelements fest.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Parameter

*pszSubAppName*<br/>
Ein Zeiger auf eine Unicode-Zeichenfolge, die den zu setzenden erweiterten visuellen Stil des Kombinationsfelds enthält.

### <a name="return-value"></a>Rückgabewert

Der Rückgabewert wird nicht verwendet.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion emuliert die Funktionalität der [CBEM_SETWINDOWTHEME](/windows/win32/Controls/cbem-setwindowtheme) Nachricht, wie im Windows SDK beschrieben.

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel-MFCIE](../../overview/visual-cpp-samples.md)<br/>
[CComboBox-Klasse](../../mfc/reference/ccombobox-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CComboBox-Klasse](../../mfc/reference/ccombobox-class.md)
