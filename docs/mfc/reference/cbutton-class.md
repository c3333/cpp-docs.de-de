---
title: CButton-Klasse
ms.date: 11/04/2016
f1_keywords:
- CButton
- AFXWIN/CButton
- AFXWIN/CButton::CButton
- AFXWIN/CButton::Create
- AFXWIN/CButton::DrawItem
- AFXWIN/CButton::GetBitmap
- AFXWIN/CButton::GetButtonStyle
- AFXWIN/CButton::GetCheck
- AFXWIN/CButton::GetCursor
- AFXWIN/CButton::GetIcon
- AFXWIN/CButton::GetIdealSize
- AFXWIN/CButton::GetImageList
- AFXWIN/CButton::GetNote
- AFXWIN/CButton::GetNoteLength
- AFXWIN/CButton::GetSplitGlyph
- AFXWIN/CButton::GetSplitImageList
- AFXWIN/CButton::GetSplitInfo
- AFXWIN/CButton::GetSplitSize
- AFXWIN/CButton::GetSplitStyle
- AFXWIN/CButton::GetState
- AFXWIN/CButton::GetTextMargin
- AFXWIN/CButton::SetBitmap
- AFXWIN/CButton::SetButtonStyle
- AFXWIN/CButton::SetCheck
- AFXWIN/CButton::SetCursor
- AFXWIN/CButton::SetDropDownState
- AFXWIN/CButton::SetIcon
- AFXWIN/CButton::SetImageList
- AFXWIN/CButton::SetNote
- AFXWIN/CButton::SetSplitGlyph
- AFXWIN/CButton::SetSplitImageList
- AFXWIN/CButton::SetSplitInfo
- AFXWIN/CButton::SetSplitSize
- AFXWIN/CButton::SetSplitStyle
- AFXWIN/CButton::SetState
- AFXWIN/CButton::SetTextMargin
helpviewer_keywords:
- CButton [MFC], CButton
- CButton [MFC], Create
- CButton [MFC], DrawItem
- CButton [MFC], GetBitmap
- CButton [MFC], GetButtonStyle
- CButton [MFC], GetCheck
- CButton [MFC], GetCursor
- CButton [MFC], GetIcon
- CButton [MFC], GetIdealSize
- CButton [MFC], GetImageList
- CButton [MFC], GetNote
- CButton [MFC], GetNoteLength
- CButton [MFC], GetSplitGlyph
- CButton [MFC], GetSplitImageList
- CButton [MFC], GetSplitInfo
- CButton [MFC], GetSplitSize
- CButton [MFC], GetSplitStyle
- CButton [MFC], GetState
- CButton [MFC], GetTextMargin
- CButton [MFC], SetBitmap
- CButton [MFC], SetButtonStyle
- CButton [MFC], SetCheck
- CButton [MFC], SetCursor
- CButton [MFC], SetDropDownState
- CButton [MFC], SetIcon
- CButton [MFC], SetImageList
- CButton [MFC], SetNote
- CButton [MFC], SetSplitGlyph
- CButton [MFC], SetSplitImageList
- CButton [MFC], SetSplitInfo
- CButton [MFC], SetSplitSize
- CButton [MFC], SetSplitStyle
- CButton [MFC], SetState
- CButton [MFC], SetTextMargin
ms.assetid: cdc76d5b-31da-43c5-bc43-fde4cb39de5b
ms.openlocfilehash: 7e2156c7fba6d5c621ab9e73b4739be45941fcc5
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561985"
---
# <a name="cbutton-class"></a>CButton-Klasse

Stellt die Funktionalität von Windows-Schaltflächensteuerelementen bereit.

## <a name="syntax"></a>Syntax

```
class CButton : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|BESCHREIBUNG|
|----------|-----------------|
|[CButton:: CButton](#cbutton)|Erstellt ein `CButton`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[CButton:: Create](#create)|Erstellt das Windows-Schaltflächen-Steuerelement und fügt es an das- `CButton` Objekt an.|
|[CButton::D rawitem](#drawitem)|Überschreiben, um ein vom Besitzer gezeichnetes Objekt zu zeichnen `CButton` .|
|[CButton:: getbitmap](#getbitmap)|Ruft das Handle der Bitmap ab, die zuvor mit [SetBitmap](#setbitmap)festgelegt wurde.|
|[CButton:: GetButtonStyle](#getbuttonstyle)|Ruft Informationen zum Steuerelement Stil der Schaltfläche ab.|
|[CButton:: getcheck](#getcheck)|Ruft den Prüf Zustand eines Schaltflächen-Steuer Elements ab.|
|[CButton:: GetCursor](#getcursor)|Ruft das Handle des Cursor Bilds ab, das zuvor mit [SetCursor](#setcursor)festgelegt wurde.|
|[CButton:: getIcon](#geticon)|Ruft das Handle des Symbols ab, das zuvor mit [SetIcon](#seticon)festgelegt wurde.|
|[CButton:: getidealsize](#getidealsize)|Ruft die ideale Größe des Schaltflächen-Steuer Elements ab.|
|[CButton:: GetImageList](#getimagelist)|Ruft die Bildliste des Schaltflächen-Steuer Elements ab.|
|[CButton:: GetNote](#getnote)|Ruft die Notiz Komponente des aktuellen Befehls Link-Steuer Elements ab.|
|[CButton:: getnotelength](#getnotelength)|Ruft die Länge des Notiz Texts für das aktuelle Befehls Link Steuerelement ab.|
|[CButton:: getsplitglyph](#getsplitglyph)|Ruft das Symbol ab, das dem aktuellen Steuerelement für die unterteilte Schaltfläche zugeordnet ist.|
|[CButton:: getsplitimagelist](#getsplitimagelist)|Ruft die Bildliste für das aktuelle unterteilte Schaltflächen-Steuerelement ab.|
|[CButton:: getsplitinfo](#getsplitinfo)|Ruft Informationen ab, die das aktuelle Steuerelement für unterteilte Schaltflächen definieren.|
|[CButton:: getsplitsize](#getsplitsize)|Ruft das umgebende Rechteck der Dropdown Komponente des aktuellen unterteilten Schaltflächen-Steuer Elements ab.|
|[CButton:: getsplitstyle](#getsplitstyle)|Ruft die unterteilten Schaltflächen Formate ab, die das aktuelle Steuerelement unterteilte Schaltflächen definieren.|
|[CButton:: GetState](#getstate)|Ruft den Prüf Zustand, den Hervorhebungs Zustand und den Fokus Zustand eines Schaltflächen-Steuer Elements ab.|
|[CButton:: gettextmargin](#gettextmargin)|Ruft den Textrand des Schaltflächen-Steuer Elements ab.|
|[CButton:: SetBitmap](#setbitmap)|Gibt eine Bitmap an, die auf der Schaltfläche angezeigt werden soll.|
|[CButton:: setbuttonstyle](#setbuttonstyle)|Ändert den Stil einer Schaltfläche.|
|[CButton:: setcheck](#setcheck)|Legt den Prüf Zustand eines Schaltflächen-Steuer Elements fest.|
|[CButton:: SetCursor](#setcursor)|Gibt ein Cursor Bild an, das auf der Schaltfläche angezeigt werden soll.|
|[CButton:: setdropdownstate](#setdropdownstate)|Legt den Dropdown Zustand des aktuellen Steuer Elements für eine unterteilte Schaltfläche fest.|
|[CButton:: abticon](#seticon)|Gibt ein Symbol an, das auf der Schaltfläche angezeigt werden soll.|
|[CButton:: SetImageList](#setimagelist)|Legt die Bildliste des Schaltflächen-Steuer Elements fest.|
|[CButton:: setnote](#setnote)|Legt den Hinweis auf das aktuelle Befehls Link Steuerelement fest.|
|[CButton:: setsplitglyph](#setsplitglyph)|Ordnet ein angegebenes Symbol dem aktuellen Steuerelement für die unterteilte Schaltfläche zu.|
|[CButton:: setsplitimagelist](#setsplitimagelist)|Ordnet dem aktuellen Steuerelement für die unterteilte Schaltfläche eine Bildliste zu.|
|[CButton:: setsplitinfo](#setsplitinfo)|Gibt Informationen an, die das aktuelle Steuerelement unterteilte Schaltflächen definieren.|
|[CButton:: setsplitsize](#setsplitsize)|Legt das umgebende Rechteck der Dropdown Komponente des aktuellen unterteilten Schaltflächen-Steuer Elements fest.|
|[CButton:: setsplitstyle](#setsplitstyle)|Legt den Stil des aktuellen Steuer Elements für eine unterteilte Schaltfläche fest.|
|[CButton:: SetState](#setstate)|Legt den Hervorhebungs Zustand eines Schaltflächen-Steuer Elements fest.|
|[CButton:: settextmargin](#settextmargin)|Legt den Textrand des Schaltflächen-Steuer Elements fest.|

## <a name="remarks"></a>Bemerkungen

Ein Schaltflächen-Steuerelement ist ein kleines, rechteckiges untergeordnetes Fenster, das ein-und ausgeschaltet werden kann. Schaltflächen können allein oder in Gruppen verwendet werden und können entweder als bezeichnet oder ohne Text angezeigt werden. Eine Schaltfläche ändert in der Regel die Darstellung, wenn der Benutzer darauf klickt.

Typische Schaltflächen sind das Kontrollkästchen, das Optionsfeld und die pushtaste. Ein- `CButton` Objekt kann je nach dem bei der Initialisierung durch die [Create](#create) Member-Funktion angegebenen [Schaltflächen Stil](../../mfc/reference/styles-used-by-mfc.md#button-styles) zu einem beliebigen werden.

Außerdem unterstützt die von abgeleitete [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md) -Klasse die Erstellung von Schaltflächen-Steuerelementen, die `CButton` mit Bitmapbildern anstelle von Text bezeichnet werden. Ein `CBitmapButton` kann über separate Bitmaps für die Zustände "hoch", "nach oben", "fokussiert" und "deaktiviert" verfügen.

Sie können ein Schaltflächen-Steuerelement entweder aus einer Dialogfeld Vorlage oder direkt im Code erstellen. Rufen Sie in beiden Fällen zuerst den Konstruktor `CButton` auf, um das `CButton` Objekt zu erstellen. Rufen Sie dann die `Create` Member-Funktion auf, um das Windows-Schaltflächen-Steuerelement zu erstellen, und fügen Sie es an `CButton`

Die Konstruktion kann ein einstufiger Prozess in einer von abgeleiteten Klasse sein `CButton` . Schreiben Sie einen Konstruktor für die abgeleitete Klasse, und geben Sie `Create` im Konstruktor ein.

Wenn Sie Windows-Benachrichtigungs Meldungen verarbeiten möchten, die von einem Schaltflächen-Steuerelement an das übergeordnete Element gesendet werden (normalerweise eine von [CDialog](../../mfc/reference/cdialog-class.md)abgeleitete Klasse), fügen Sie der übergeordneten Klasse für jede Nachricht einen Meldungs Zuordnungs Eintrag und eine nachrichtenhandlerelementfunktion

Jeder Nachrichten Zuordnungs Eintrag hat die folgende Form:

**Ein \_ ** _Benachrichtigung_ **(** _ID_, _mitgliedungsfxn_ **)**

Where *ID* gibt die untergeordnete Fenster-ID des Steuer Elements an, das die Benachrichtigung sendet, und *mitgliedschaftenname* ist der Name der übergeordneten Element Funktion, die Sie zum Verarbeiten der Benachrichtigung geschrieben haben.

Der Prototyp der übergeordneten Funktion ist wie folgt:

`afx_msg void memberFxn();`

Mögliche Nachrichten Zuordnungs Einträge lauten wie folgt:

|Zuordnungs Eintrag|An übergeordnetes Element gesendet, wenn...|
|---------------|----------------------------|
|ON_BN_CLICKED|Der Benutzer klickt auf eine Schaltfläche.|
|ON_BN_DOUBLECLICKED|Der Benutzer doppelklickt auf eine Schaltfläche.|

Wenn Sie ein- `CButton` Objekt aus einer Dialogfeld Ressource erstellen, `CButton` wird das Objekt automatisch zerstört, wenn der Benutzer das Dialogfeld schließt.

Wenn Sie ein- `CButton` Objekt in einem-Fenster erstellen, müssen Sie es möglicherweise zerstören. Wenn Sie das- `CButton` Objekt auf dem Heap mithilfe der- **`new`** Funktion erstellen, müssen Sie für das-Objekt aufzurufen, **`delete`** um es zu zerstören, wenn der Benutzer das Windows-Schaltflächen-Steuerelement schließt. Wenn Sie das `CButton` Objekt im Stapel erstellen oder es in das übergeordnete Dialog Objekt eingebettet ist, wird es automatisch zerstört.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CButton`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="cbuttoncbutton"></a><a name="cbutton"></a> CButton:: CButton

Erstellt ein `CButton`-Objekt.

```
CButton();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]

## <a name="cbuttoncreate"></a><a name="create"></a> CButton:: Create

Erstellt das Windows-Schaltflächen-Steuerelement und fügt es an das- `CButton` Objekt an.

```
virtual BOOL Create(
    LPCTSTR lpszCaption,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*lpszcaption*<br/>
Gibt den Text des Schaltflächen Steuer Elements an.

*dwstyle*<br/>
Gibt den Stil des Schaltflächen Steuer Elements an. Wendet eine beliebige Kombination von [Schaltflächen Stilen](../../mfc/reference/styles-used-by-mfc.md#button-styles) auf die Schaltfläche an.

*Rect*<br/>
Gibt die Größe und Position des Schaltflächen Steuer Elements an. Dies kann entweder ein- `CRect` Objekt oder eine- `RECT` Struktur sein.

*pparser*<br/>
Gibt das übergeordnete Fenster des Schaltflächen Steuer Elements an, normalerweise ein `CDialog` . Er darf nicht NULL sein.

*nID*<br/>
Gibt die ID des Schaltflächen-Steuer Elements an.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Sie erstellen ein- `CButton` Objekt in zwei Schritten. Zuerst wird der-Konstruktor aufgerufen und dann aufgerufen `Create` , wodurch das Windows-Schaltflächen-Steuerelement erstellt und an das-Objekt angefügt wird `CButton` .

Wenn die WS_VISIBLE-Formatvorlage angegeben ist, sendet Windows das Schaltflächen-Steuerelement alle Nachrichten, die zum Aktivieren und Anzeigen der Schaltfläche erforderlich sind.

Wenden Sie die folgenden [Fenster Stile](../../mfc/reference/styles-used-by-mfc.md#window-styles) auf ein Schaltflächen-Steuerelement an:

- Immer WS_CHILD

- WS_VISIBLE in der Regel

- WS_DISABLED selten

- WS_GROUP zum Gruppieren von Steuerelementen

- WS_TABSTOP, um die Schaltfläche in die Tabstopps aufzunehmen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]

## <a name="cbuttondrawitem"></a><a name="drawitem"></a> CButton::D rawitem

Wird von Framework aufgerufen, wenn sich ein visueller Aspekt einer vom Besitzer gezeichneten Schaltfläche geändert hat.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parameter

*lpdrawitemstruct*<br/>
Ein langer Zeiger auf eine [drawitemstruct](/windows/win32/api/winuser/ns-winuser-drawitemstruct) -Struktur. Die-Struktur enthält Informationen zu dem Element, das gezeichnet werden soll, und zum Zeichentyp, der gezeichnet werden soll.

### <a name="remarks"></a>Bemerkungen

Für eine vom Besitzer gezeichnete Schaltfläche ist das BS_OWNERDRAW Format festgelegt. Überschreiben Sie diese Element Funktion, um das Zeichnen für ein vom Besitzer gezeichnetes Objekt zu implementieren `CButton` Die Anwendung sollte alle GDI-Objekte (Graphics Device Interface) wiederherstellen, die für den in *lpdrawitemstruct* angegebenen Anzeige Kontext ausgewählt wurden, bevor die Element Funktion beendet wird.

Weitere Informationen finden Sie auch in den [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) -Stilwerten.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]

## <a name="cbuttongetbitmap"></a><a name="getbitmap"></a> CButton:: getbitmap

Mit dieser Member-Funktion können Sie das Handle einer Bitmap abrufen, die zuvor mit [SetBitmap](#setbitmap)festgelegt wurde, das einer Schaltfläche zugeordnet ist.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für eine Bitmap. NULL, wenn zuvor keine Bitmap angegeben wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

## <a name="cbuttongetbuttonstyle"></a><a name="getbuttonstyle"></a> CButton:: GetButtonStyle

Ruft Informationen zum Steuerelement Stil der Schaltfläche ab.

```
UINT GetButtonStyle() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die Schaltflächen Stile für dieses- `CButton` Objekt zurück. Diese Funktion gibt nur die [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) Stilwerte zurück, nicht die anderen Fenster Stile.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

## <a name="cbuttongetcheck"></a><a name="getcheck"></a> CButton:: getcheck

Ruft den Status der Überprüfung eines Options Felds oder eines Kontrollkästchens ab.

```
int GetCheck() const;
```

### <a name="return-value"></a>Rückgabewert

Der Rückgabewert eines Schaltflächen-Steuer Elements, das mit der BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON oder BS_3STATE Style erstellt wurde, ist einer der folgenden Werte:

|Wert|Bedeutung|
|-----------|-------------|
|BST_UNCHECKED|Der Schaltflächen Zustand ist nicht aktiviert.|
|BST_CHECKED|Der Schaltflächen Zustand ist aktiviert.|
|BST_INDETERMINATE|Der Schaltflächen Zustand ist unbestimmt (gilt nur, wenn die Schaltfläche die BS_3STATE oder BS_AUTO3STATE Stil aufweist).|

Wenn die Schaltfläche einen anderen Stil hat, wird der Rückgabewert BST_UNCHECKED.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

## <a name="cbuttongetcursor"></a><a name="getcursor"></a> CButton:: GetCursor

Mit dieser Member-Funktion können Sie das Handle eines Cursors abrufen, der zuvor mit [SetCursor](#setcursor)festgelegt wurde, der einer Schaltfläche zugeordnet ist.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für ein Cursor Bild. NULL, wenn zuvor kein Cursor angegeben wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

## <a name="cbuttongeticon"></a><a name="geticon"></a> CButton:: getIcon

Mit dieser Member-Funktion können Sie das Handle eines Symbols abrufen, das zuvor mit [SetIcon](#seticon)festgelegt wurde, das einer Schaltfläche zugeordnet ist.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für ein Symbol. NULL, wenn zuvor kein Symbol angegeben wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

## <a name="cbuttongetidealsize"></a><a name="getidealsize"></a> CButton:: getidealsize

Ruft die ideale Größe für das Schaltflächen-Steuerelement ab.

```
BOOL GetIdealSize(SIZE* psize);
```

### <a name="parameters"></a>Parameter

*Psize*<br/>
Ein Zeiger auf die aktuelle Größe der Schaltfläche.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion emuliert die Funktionalität der BCM_GETIDEALSIZE Nachricht, wie im [Schalt](/windows/win32/controls/buttons) Flächen Abschnitt der Windows SDK beschrieben.

## <a name="cbuttongetimagelist"></a><a name="getimagelist"></a> CButton:: GetImageList

Mit dieser Methode können Sie die Bildliste aus dem Schaltflächen-Steuerelement abrufen.

```
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Parameter

*pbuttonimagelist*<br/>
Ein Zeiger auf die Bildliste des- `CButton` Objekts.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion emuliert die Funktionalität der BCM_GETIMAGELIST Nachricht, wie im [Schalt](/windows/win32/controls/buttons) Flächen Abschnitt der Windows SDK beschrieben.

## <a name="cbuttongetnote"></a><a name="getnote"></a> CButton:: GetNote

Ruft den Hinweis Text ab, der dem aktuellen Befehls Link Steuerelement zugeordnet ist.

```
CString GetNote() const;

BOOL GetNote(
    LPTSTR lpszNote,
    UINT* cchNote) const;
```

### <a name="parameters"></a>Parameter

*lpsznote*\
vorgenommen Zeiger auf einen Puffer, den der Aufrufer für die Zuordnung und Aufhebung der Zuordnung zuständig ist. Wenn der Rückgabewert true ist, enthält der Puffer den Hinweis Text, der dem aktuellen Befehls Link Steuerelement zugeordnet ist. Andernfalls ist der Puffer unverändert.

*cchnote*\
[in, out] Ein Zeiger auf eine ganzzahlige Variable ohne Vorzeichen. Wenn diese Methode aufgerufen wird, enthält die Variable die Größe des Puffers, der durch den *lpsznote* -Parameter angegeben wird. Wenn diese Methode zurückgibt, enthält die Variable, wenn der Rückgabewert true ist, die Größe der Notiz, die dem aktuellen Befehls Link Steuerelement zugeordnet ist. Wenn der Rückgabewert FALSE ist, enthält die Variable die für den Hinweis erforderliche Puffergröße.

### <a name="return-value"></a>Rückgabewert

In der ersten Überladung ein [CString](../../atl-mfc-shared/using-cstring.md) -Objekt, das den Hinweis Text enthält, der dem aktuellen Befehls Link Steuerelement zugeordnet ist.

- oder -

In der zweiten Überladung true, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur für Steuerelemente, deren Schaltflächen Stil BS_COMMANDLINK oder BS_DEFCOMMANDLINK ist.

Diese Methode sendet die [BCM_GETNOTE](/windows/win32/Controls/bcm-getnote) Nachricht, die in der Windows SDK beschrieben wird.

## <a name="cbuttongetnotelength"></a><a name="getnotelength"></a> CButton:: getnotelength

Ruft die Länge des Notiz Texts für das aktuelle Befehls Link Steuerelement ab.

```
UINT GetNoteLength() const;
```

### <a name="return-value"></a>Rückgabewert

Die Länge des Notiz Texts in 16-Bit-Unicode-Zeichen für das aktuelle Befehls Link Steuerelement.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur für Steuerelemente, deren Schaltflächen Stil BS_COMMANDLINK oder BS_DEFCOMMANDLINK ist.

Diese Methode sendet die [BCM_GETNOTELENGTH](/windows/win32/Controls/bcm-getnotelength) Nachricht, die in der Windows SDK beschrieben wird.

## <a name="cbuttongetsplitglyph"></a><a name="getsplitglyph"></a> CButton:: getsplitglyph

Ruft das Symbol ab, das dem aktuellen Steuerelement für die unterteilte Schaltfläche zugeordnet ist.

```
TCHAR GetSplitGlyph() const;
```

### <a name="return-value"></a>Rückgabewert

Das Symbol Zeichen, das dem aktuellen Steuerelement für die unterteilte Schaltfläche zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Ein Glyphe ist die physische Darstellung eines Zeichens in einer bestimmten Schriftart. Beispielsweise kann ein Steuerelement für eine unterteilte Schaltfläche mit dem Symbol des Unicode-Häkchen Zeichens (U + 2713) versehen werden.

Verwenden Sie diese Methode nur für Steuerelemente, deren Schaltflächen Stil BS_SPLITBUTTON oder BS_DEFSPLITBUTTON ist.

Diese Methode initialisiert den `mask` Member einer [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) -Struktur mit dem BCSIF_GLYPH-Flag und sendet diese Struktur dann in der [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) -Meldung, die in der Windows SDK beschrieben wird. Wenn die Message-Funktion zurückgegeben wird, ruft diese Methode das Symbol aus dem- `himlGlyph` Member der-Struktur ab.

## <a name="cbuttongetsplitimagelist"></a><a name="getsplitimagelist"></a> CButton:: getsplitimagelist

Ruft die [Bildliste](../../mfc/reference/cimagelist-class.md) für das aktuelle unterteilte Schaltflächen-Steuerelement ab.

```
CImageList* GetSplitImageList() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CImageList](../../mfc/reference/cimagelist-class.md) -Objekt.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur für Steuerelemente, deren Schaltflächen Stil BS_SPLITBUTTON oder BS_DEFSPLITBUTTON ist.

Diese Methode initialisiert den `mask` Member einer [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) -Struktur mit dem BCSIF_IMAGE-Flag und sendet diese Struktur dann in der [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) -Meldung, die in der Windows SDK beschrieben wird. Wenn die Message-Funktion zurückgegeben wird, ruft diese Methode die Bildliste aus dem- `himlGlyph` Member der-Struktur ab.

## <a name="cbuttongetsplitinfo"></a><a name="getsplitinfo"></a> CButton:: getsplitinfo

Ruft Parameter ab, die bestimmen, wie Windows das aktuelle Steuerelement unterteilte Schaltflächen zeichnet.

```
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;
```

### <a name="parameters"></a>Parameter

*pinfo*\
vorgenommen Ein Zeiger auf eine [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) Struktur, die Informationen über das aktuelle Steuerelement für die unterteilte Schaltfläche empfängt. Der Aufrufer ist für das Zuordnen der-Struktur verantwortlich.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur für Steuerelemente, deren Schaltflächen Stil BS_SPLITBUTTON oder BS_DEFSPLITBUTTON ist.

Diese Methode sendet die [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) Nachricht, die in der Windows SDK beschrieben wird.

## <a name="cbuttongetsplitsize"></a><a name="getsplitsize"></a> CButton:: getsplitsize

Ruft das umgebende Rechteck der Dropdown Komponente des aktuellen unterteilten Schaltflächen-Steuer Elements ab.

```
BOOL GetSplitSize(LPSIZE pSize) const;
```

### <a name="parameters"></a>Parameter

*Psize*\
vorgenommen Ein Zeiger auf eine [Größen](/windows/win32/api/windef/ns-windef-size) Struktur, die die Beschreibung eines Rechtecks empfängt.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur für Steuerelemente, deren Schaltflächen Stil BS_SPLITBUTTON oder BS_DEFSPLITBUTTON ist.

Wenn das Steuerelement für die unterteilte Schaltfläche erweitert wird, kann es eine Dropdown-Komponente wie ein Listen Steuerelement oder ein Pager-Steuerelement anzeigen. Diese Methode ruft das umgebende Rechteck ab, das die Dropdown Komponente enthält.

Diese Methode initialisiert den `mask` Member einer [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) -Struktur mit dem BCSIF_SIZE-Flag und sendet diese Struktur dann in der [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) -Meldung, die in der Windows SDK beschrieben wird. Wenn die Message-Funktion zurückgegeben wird, ruft diese Methode das umgebende Rechteck aus dem- `size` Member der-Struktur ab.

## <a name="cbuttongetsplitstyle"></a><a name="getsplitstyle"></a> CButton:: getsplitstyle

Ruft die unterteilten Schaltflächen Formate ab, die das aktuelle Steuerelement unterteilte Schaltflächen definieren.

```
UINT GetSplitStyle() const;
```

### <a name="return-value"></a>Rückgabewert

Eine bitweise Kombination von unterteilten Schaltflächen Stilen. Weitere Informationen finden Sie unter dem- `uSplitStyle` Member der [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) -Struktur.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur für Steuerelemente, deren Schaltflächen Stil BS_SPLITBUTTON oder BS_DEFSPLITBUTTON ist.

Die Stile der unterteilten Schaltflächen geben die Ausrichtung, das Seitenverhältnis und das grafische Format an, mit dem Windows ein Symbol für eine unterteilte Schaltfläche zeichnet

Diese Methode initialisiert den `mask` Member einer [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) -Struktur mit dem BCSIF_STYLE-Flag und sendet diese Struktur dann in der [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) -Meldung, die in der Windows SDK beschrieben wird. Wenn die Message-Funktion zurückgegeben wird, ruft diese Methode die unterteilten Schaltflächen Stile aus dem- `uSplitStyle` Member der-Struktur ab.

## <a name="cbuttongetstate"></a><a name="getstate"></a> CButton:: GetState

Ruft den Zustand eines Schaltflächen-Steuer Elements ab.

```
UINT GetState() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Bitfeld, das die Kombination von Werten enthält, die den aktuellen Zustand eines Schaltflächen-Steuer Elements angeben. In der folgenden Tabelle sind die möglichen Werte aufgeführt.

|Schaltflächen Zustand|Wert|BESCHREIBUNG|
|------------------|-----------|-----------------|
|BST_UNCHECKED|0x0000|Der Anfangszustand.|
|BST_CHECKED|0x0001|Das Schaltflächen-Steuerelement ist aktiviert.|
|BST_INDETERMINATE|0x0002|Der Zustand ist unbestimmt (nur möglich, wenn das Schaltflächen-Steuerelement drei Zustände aufweist).|
|BST_PUSHED|0x0004|Das Schaltflächen-Steuerelement wird gedrückt.|
|BST_FOCUS|0x0008|Das Schaltflächen-Steuerelement besitzt den Fokus.|

### <a name="remarks"></a>Bemerkungen

Ein Schaltflächen-Steuerelement mit der Schaltfläche "BS_3STATE" oder "BS_AUTO3STATE Schaltfläche" erstellt ein Kontrollkästchen mit einem dritten Zustand, der den unbestimmten Zustand aufweist. Der Status "unbestimmt" gibt an, dass das Kontrollkästchen weder aktiviert noch deaktiviert ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

## <a name="cbuttongettextmargin"></a><a name="gettextmargin"></a> CButton:: gettextmargin

Ruft diese Methode auf, um den Textrand des `CButton` Objekts abzurufen.

```
BOOL GetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Parameter

*pmargin*<br/>
Ein Zeiger auf den texrand des- `CButton` Objekts.

### <a name="return-value"></a>Rückgabewert

Gibt den texrand zurück.

### <a name="remarks"></a>Bemerkungen

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion emuliert die Funktionalität der BCM_GETTEXTMARGIN Nachricht, wie im [Schalt](/windows/win32/controls/buttons) Flächen Abschnitt der Windows SDK beschrieben.

## <a name="cbuttonsetbitmap"></a><a name="setbitmap"></a> CButton:: SetBitmap

Diese Member-Funktion wird aufgerufen, um der Schaltfläche eine neue Bitmap zuzuordnen.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parameter

*HBITMAP*<br/>
Das Handle einer Bitmap.

### <a name="return-value"></a>Rückgabewert

Das Handle einer Bitmap, die zuvor der Schaltfläche zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Die Bitmap wird automatisch auf der Vorderseite der Schaltfläche platziert, die standardmäßig zentriert ist. Wenn die Bitmap für die Schaltfläche zu groß ist, wird Sie auf beiden Seiten abgeschnitten. Sie können auch andere Ausrichtungsoptionen auswählen, einschließlich der folgenden:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

Im Unterschied zu [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), das vier Bitmaps pro Schaltfläche verwendet, `SetBitmap` verwendet nur eine Bitmap pro Schaltfläche. Wenn die Schaltfläche gedrückt wird, wird die Bitmap nach unten und nach rechts verschoben.

Sie sind dafür verantwortlich, die Bitmap freizugeben, wenn Sie damit abgeschlossen sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

## <a name="cbuttonsetbuttonstyle"></a><a name="setbuttonstyle"></a> CButton:: setbuttonstyle

Ändert den Stil einer Schaltfläche.

```cpp
void SetButtonStyle(
    UINT nStyle,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parameter

*nStyle*<br/>
Gibt den [Stil der Schaltfläche](../../mfc/reference/styles-used-by-mfc.md#button-styles)an.

*bredraw*<br/>
Gibt an, ob die Schaltfläche neu gezeichnet werden soll. Ein Wert ungleich 0 (null) zeichnet die Schaltfläche neu. Bei einem Wert von 0 wird die Schaltfläche nicht neu gezeichnet. Die Schaltfläche wird standardmäßig neu gezeichnet.

### <a name="remarks"></a>Bemerkungen

Verwenden `GetButtonStyle` Sie die Member-Funktion, um den Schaltflächen Stil abzurufen. Das nieder wertige Wort des Schaltflächen Stils Complete ist der Schaltflächen spezifische Stil.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

## <a name="cbuttonsetcheck"></a><a name="setcheck"></a> CButton:: setcheck

Legt den Status des Kontrollkästchens oder des Kontrollkästchens fest oder setzt ihn zurück.

```cpp
void SetCheck(int nCheck);
```

### <a name="parameters"></a>Parameter

*nPrüfen*<br/>
Gibt den Status der Überprüfung an. Der Parameter kann eine der folgenden Einstellungen haben:

|Wert|Bedeutung|
|-----------|-------------|
|BST_UNCHECKED|Legen Sie den Zustand der Schaltfläche auf deaktiviert fest.|
|BST_CHECKED|Legen Sie den Zustand der Schaltfläche auf aktiviert fest.|
|BST_INDETERMINATE|Legen Sie den Zustand der Schaltfläche auf unbestimmt fest. Dieser Wert kann nur verwendet werden, wenn die Schaltfläche die BS_3STATE oder BS_AUTO3STATE Format hat.|

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion hat keine Auswirkung auf eine PUSHBUTTON.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

## <a name="cbuttonsetcursor"></a><a name="setcursor"></a> CButton:: SetCursor

Diese Member-Funktion wird aufgerufen, um der Schaltfläche einen neuen Cursor zuzuordnen.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Parameter

*hcursor*<br/>
Das Handle eines Cursors.

### <a name="return-value"></a>Rückgabewert

Das Handle eines Cursors, der zuvor der Schaltfläche zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Der Cursor wird automatisch auf der Vorderseite der Schaltfläche platziert, die standardmäßig zentriert ist. Wenn der Cursor für die Schaltfläche zu groß ist, wird er auf jeder Seite abgeschnitten. Sie können auch andere Ausrichtungsoptionen auswählen, einschließlich der folgenden:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

Im Unterschied zu [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), das vier Bitmaps pro Schaltfläche verwendet, `SetCursor` verwendet nur einen Cursor pro Schaltfläche. Wenn die Schaltfläche gedrückt wird, wird der Cursor nach unten und nach rechts verschoben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

## <a name="cbuttonsetdropdownstate"></a><a name="setdropdownstate"></a> CButton:: setdropdownstate

Legt den Dropdown Zustand des aktuellen Steuer Elements für eine unterteilte Schaltfläche fest.

```
BOOL SetDropDownState(BOOL fDropDown);
```

### <a name="parameters"></a>Parameter

*Dropdown Liste*\
in TRUE, wenn BST_DROPDOWNPUSHED Zustand festgelegt werden soll. andernfalls false.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Ein Steuerelement für eine unterteilte Schaltfläche verfügt über einen Stil von BS_SPLITBUTTON oder BS_DEFSPLITBUTTON und besteht aus einer Schaltfläche und einem Dropdown Pfeil auf der rechten Seite. Weitere Informationen finden Sie unter [Schaltflächen Stile](/windows/win32/Controls/button-styles). Normalerweise wird der Dropdown Zustand festgelegt, wenn der Benutzer auf den Dropdown Pfeil klickt. Verwenden Sie diese Methode, um den Dropdown Zustand des-Steuer Elements Programm gesteuert festzulegen. Der Dropdown Pfeil wird schattiert, um den Zustand anzugeben.

Diese Methode sendet die [BCM_SETDROPDOWNSTATE](/windows/win32/Controls/bcm-setdropdownstate) Nachricht, die in der Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die-Variable definiert, *m_splitButton*, die verwendet wird, um Programm gesteuert auf das Steuerelement für die geteilte Schaltfläche zuzugreifen. Diese Variable wird im folgenden Beispiel verwendet.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird der Zustand des Steuer Elements unterteilte Schaltflächen festgelegt, um anzugeben, dass der Dropdown Pfeil per Pushvorgang übermittelt wird.

[!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]

## <a name="cbuttonsetelevationrequired"></a><a name="setelevationrequired"></a> CButton:: ab.

Legt den Zustand des aktuellen Schaltflächen-Steuer Elements auf fest `elevation required` . Dies ist erforderlich, damit das-Steuerelement ein Symbol für erhöhte Sicherheit anzeigt.

```
BOOL SetElevationRequired(BOOL fElevationRequired);
```

### <a name="parameters"></a>Parameter

*felevationrequired*\
in TRUE, wenn der Zustand festgelegt werden soll, `elevation required` andernfalls false.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Wenn für eine Schaltfläche oder ein Befehls Link Steuerelement erhöhte Sicherheits Berechtigungen erforderlich sind, um eine Aktion auszuführen, legen Sie das Steuerelement auf `elevation required` State fest Anschließend zeigt Windows das Schild Symbol der Benutzerkontensteuerung (User Account Control, UAC) auf dem Steuerelement an. Weitere Informationen finden Sie unter [Benutzerkontensteuerung](/windows/win32/uxguide/winenv-uac).

Diese Methode sendet die [BCM_SETSHIELD](/windows/win32/Controls/bcm-setshield) Nachricht, die in der Windows SDK beschrieben wird.

## <a name="cbuttonseticon"></a><a name="seticon"></a> CButton:: abticon

Diese Member-Funktion wird aufgerufen, um der Schaltfläche ein neues Symbol zuzuordnen.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Parameter

*hIcon*<br/>
Das Handle eines Symbols.

### <a name="return-value"></a>Rückgabewert

Das Handle eines Symbols, das zuvor der Schaltfläche zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Das Symbol wird automatisch auf der Vorderseite der Schaltfläche platziert, die standardmäßig zentriert ist. Wenn das Symbol für die Schaltfläche zu groß ist, wird es auf beiden Seiten abgeschnitten. Sie können auch andere Ausrichtungsoptionen auswählen, einschließlich der folgenden:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

Im Unterschied zu [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), das vier Bitmaps pro Schaltfläche verwendet, wird von `SetIcon` nur ein Symbol für die Schaltfläche verwendet. Wenn die Schaltfläche gedrückt wird, wird das Symbol nach unten und nach rechts verschoben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

## <a name="cbuttonsetimagelist"></a><a name="setimagelist"></a> CButton:: SetImageList

Ruft diese Methode auf, um die Bildliste des-Objekts festzulegen `CButton` .

```
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Parameter

*pbuttonimagelist*<br/>
Ein Zeiger auf die neue Bildliste.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, false bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion emuliert die Funktionalität der BCM_SETIMAGELIST Nachricht, wie im [Schalt](/windows/win32/controls/buttons) Flächen Abschnitt der Windows SDK beschrieben.

## <a name="cbuttonsetnote"></a><a name="setnote"></a> CButton:: setnote

Legt den Hinweis Text für das aktuelle Befehls Link Steuerelement fest.

```
BOOL SetNote(LPCTSTR lpszNote);
```

### <a name="parameters"></a>Parameter

*lpsznote*\
in Ein Zeiger auf eine Unicode-Zeichenfolge, die als Hinweis Text für das Befehls Link Steuerelement festgelegt wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur für Steuerelemente, deren Schaltflächen Stil BS_COMMANDLINK oder BS_DEFCOMMANDLINK ist.

Diese Methode sendet die [BCM_SETNOTE](/windows/win32/Controls/bcm-setnote) Nachricht, die in der Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die-Variable definiert, *m_cmdLink*, die für den programmgesteuerten Zugriff auf das Befehls Link Steuerelement verwendet wird. Diese Variable wird im folgenden Beispiel verwendet.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird der Hinweis Text für das Befehls Link Steuerelement festgelegt.

[!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]

## <a name="cbuttonsetsplitglyph"></a><a name="setsplitglyph"></a> CButton:: setsplitglyph

Ordnet ein angegebenes Symbol dem aktuellen Steuerelement für die unterteilte Schaltfläche zu.

```
BOOL SetSplitGlyph(TCHAR chGlyph);
```

### <a name="parameters"></a>Parameter

*Zeichen*\
in Ein Zeichen, das das Symbol angibt, das als Dropdown Pfeil für die unterteilte Schaltfläche verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur mit Steuerelementen, die den Schaltflächen Stil BS_SPLITBUTTON oder BS_DEFSPLITBUTTON haben.

Ein Glyphe ist die physische Darstellung eines Zeichens in einer bestimmten Schriftart. Der *chglyph* -Parameter wird nicht als Symbol verwendet, sondern stattdessen verwendet, um ein Symbol aus einer Reihe von System definierten Symbolen auszuwählen. Der Standard-Dropdown-Pfeilsymbol wird durch ein Zeichen "6" angegeben und ähnelt dem Unicode-Zeichen "Black Down-pointedreieck" (U + 25bc).

Diese Methode initialisiert den `mask` Member einer [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) -Struktur mit dem BCSIF_GLYPH-Flag und dem- `himlGlyph` Member mit dem *chglyph* -Parameter und sendet diese Struktur dann in der [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) -Meldung, die in der Windows SDK beschrieben wird.

## <a name="cbuttonsetsplitimagelist"></a><a name="setsplitimagelist"></a> CButton:: setsplitimagelist

Ordnet dem aktuellen Steuerelement für die unterteilte Schaltfläche eine [Bildliste](../../mfc/reference/cimagelist-class.md) zu.

```
BOOL SetSplitImageList(CImageList* pSplitImageList);
```

### <a name="parameters"></a>Parameter

*psplitimagelist*\
in Zeiger auf ein [CImageList](../../mfc/reference/cimagelist-class.md) -Objekt, das dem aktuellen Steuerelement für unterteilte Schaltflächen zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur für Steuerelemente, deren Schaltflächen Stil BS_SPLITBUTTON oder BS_DEFSPLITBUTTON ist.

Diese Methode initialisiert den `mask` Member einer [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) -Struktur mit dem BCSIF_IMAGE-Flag und dem- `himlGlyph` Member mit dem *psplitimagelist* -Parameter und sendet diese Struktur dann in der [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) -Meldung, die in der Windows SDK beschrieben wird.

## <a name="cbuttonsetsplitinfo"></a><a name="setsplitinfo"></a> CButton:: setsplitinfo

Gibt Parameter an, die bestimmen, wie Windows das aktuelle Steuerelement unterteilte Schaltflächen zeichnet.

```
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```

### <a name="parameters"></a>Parameter

*pinfo*\
in Zeiger auf eine [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) -Struktur, die das aktuelle unterteilte Schaltflächen-Steuerelement definiert.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur für Steuerelemente, deren Schaltflächen Stil BS_SPLITBUTTON oder BS_DEFSPLITBUTTON ist.

Diese Methode sendet die [BCM_SETSPLITINFO](/windows/win32/Controls/bcm-setsplitinfo) Nachricht, die in der Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die-Variable definiert, die `m_splitButton` für den programmgesteuerten Zugriff auf das Steuerelement für die unterteilte Schaltfläche verwendet wird.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird das Symbol geändert, das für den Dropdown Pfeil unterteilte Schaltfläche verwendet wird. Im Beispiel wird ein nach oben zeigendes Dreiecks Symbol für das standardmäßige nach unten zeigenden Dreieck Symbol ersetzt. Welches Symbol angezeigt wird, hängt von dem Zeichen ab, das Sie im- `himlGlyph` Member der- `BUTTON_SPLITINFO` Struktur angeben. Das nach unten zeigenden Dreiecks Symbol wird durch das Zeichen ' 6 ' angegeben, und das nach oben zeigenden Dreiecks Symbol wird durch das Zeichen ' 5 ' angegeben. Informationen zum Vergleich finden Sie unter der Hilfsmethode [CButton:: setsplitglyph](#setsplitglyph).

[!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]

## <a name="cbuttonsetsplitsize"></a><a name="setsplitsize"></a> CButton:: setsplitsize

Legt das umgebende Rechteck der Dropdown Komponente des aktuellen unterteilten Schaltflächen-Steuer Elements fest.

```
BOOL SetSplitSize(LPSIZE pSize);
```

### <a name="parameters"></a>Parameter

*Psize*\
in Ein Zeiger auf eine [Größen](/windows/win32/api/windef/ns-windef-size) Struktur, die ein umschließendes Rechteck beschreibt.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur für Steuerelemente, deren Schaltflächen Stil BS_SPLITBUTTON oder BS_DEFSPLITBUTTON ist.

Wenn das Steuerelement für die unterteilte Schaltfläche erweitert wird, kann es eine Dropdown-Komponente wie ein Listen Steuerelement oder ein Pager-Steuerelement anzeigen. Diese Methode gibt die Größe des umgebenden Rechtecks an, das die Dropdown Komponente enthält.

Diese Methode initialisiert den `mask` Member einer [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) -Struktur mit dem BCSIF_SIZE-Flag und dem- `size` Member mit dem *Psize* -Parameter und sendet diese Struktur dann in der [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) -Meldung, die in der Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die-Variable definiert, die `m_splitButton` für den programmgesteuerten Zugriff auf das Steuerelement für die unterteilte Schaltfläche verwendet wird. Diese Variable wird im folgenden Beispiel verwendet.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die Größe des Dropdown Pfeils der unterteilten Schaltfläche verdoppelt.

[!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]

## <a name="cbuttonsetsplitstyle"></a><a name="setsplitstyle"></a> CButton:: setsplitstyle

Legt den Stil des aktuellen Steuer Elements für eine unterteilte Schaltfläche fest.

```
BOOL SetSplitStyle(UINT uSplitStyle);
```

### <a name="parameters"></a>Parameter

*usplitstyle*\
in Eine bitweise Kombination von unterteilten Schaltflächen Stilen. Weitere Informationen finden Sie unter dem- `uSplitStyle` Member der [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) -Struktur.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur für Steuerelemente, deren Schaltflächen Stil BS_SPLITBUTTON oder BS_DEFSPLITBUTTON ist.

Die Stile der unterteilten Schaltflächen geben die Ausrichtung, das Seitenverhältnis und das grafische Format an, mit dem Windows ein Symbol für eine unterteilte Schaltfläche zeichnet Weitere Informationen finden Sie unter dem- `uSplitStyle` Member der [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) -Struktur.

Diese Methode initialisiert den `mask` Member einer [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) -Struktur mit dem BCSIF_STYLE-Flag und dem- `uSplitStyle` Member mit dem *usplitstyle* -Parameter und sendet diese Struktur dann in der [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) -Meldung, die in der Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die-Variable definiert, die `m_splitButton` für den programmgesteuerten Zugriff auf das Steuerelement für die unterteilte Schaltfläche verwendet wird.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird der Stil der Dropdown Schaltfläche für die unterteilte Schaltfläche festgelegt. Der BCSS_ALIGNLEFT Stil zeigt den Pfeil auf der linken Seite der Schaltfläche an, während der BCSS_STRETCH Stil die Proportionen des Dropdown Pfeils bei der Größenänderung der Schaltfläche beibehält.

[!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]

## <a name="cbuttonsetstate"></a><a name="setstate"></a> CButton:: SetState

Legt fest, ob ein Schaltflächen-Steuerelement hervorgehoben ist.

```cpp
void SetState(BOOL bHighlight);
```

### <a name="parameters"></a>Parameter

*bhighlight*<br/>
Gibt an, ob die Schaltfläche hervorgehoben werden soll. Mit einem Wert ungleich 0 wird die Schaltfläche hervorgehoben. der Wert 0 entfernt alle Hervorhebungen.

### <a name="remarks"></a>Bemerkungen

Hervorhebung wirkt sich auf das äußere eines Schaltflächen-Steuer Elements aus Dies hat keine Auswirkung auf den Status des Kontrollkästchens oder des Kontrollkästchens.

Ein Schaltflächen-Steuerelement wird automatisch hervorgehoben, wenn der Benutzer mit der linken Maustaste klickt. Die Hervorhebung wird entfernt, wenn der Benutzer die Maustaste loslässt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

## <a name="cbuttonsettextmargin"></a><a name="settextmargin"></a> CButton:: settextmargin

Mit dieser Methode wird der Textrand des-Objekts festgelegt `CButton` .

```
BOOL SetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Parameter

*pmargin*<br/>
Ein Zeiger auf den neuen texrand.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, false bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion emuliert die Funktionalität der BCM_SETTEXTMARGIN Nachricht, wie im [Schalt](/windows/win32/controls/buttons) Flächen Abschnitt der Windows SDK beschrieben.

## <a name="see-also"></a>Weitere Informationen

[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[CComboBox-Klasse](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit-Klasse](../../mfc/reference/cedit-class.md)<br/>
[CListBox-Klasse](../../mfc/reference/clistbox-class.md)<br/>
[Cscrollbar-Klasse](../../mfc/reference/cscrollbar-class.md)<br/>
[Cstatic-Klasse](../../mfc/reference/cstatic-class.md)<br/>
[CBitmapButton-Klasse](../../mfc/reference/cbitmapbutton-class.md)<br/>
[CDialog-Klasse](../../mfc/reference/cdialog-class.md)
