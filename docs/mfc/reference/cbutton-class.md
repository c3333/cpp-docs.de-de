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
ms.openlocfilehash: 74b07dc8144e853714ea73c8235f1259538a0c12
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752752"
---
# <a name="cbutton-class"></a>CButton-Klasse

Stellt die Funktionalität von Windows-Schaltflächensteuerelementen bereit.

## <a name="syntax"></a>Syntax

```
class CButton : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CButton::CButton](#cbutton)|Erstellt ein `CButton`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CButton::Erstellen](#create)|Erstellt das Windows-Schaltflächensteuerelement und `CButton` fügt es an das Objekt an.|
|[CButton::DrawItem](#drawitem)|Überschreiben Sie, um `CButton` ein vom Besitzer gezeichnetes Objekt zu zeichnen.|
|[CButton::GetBitmap](#getbitmap)|Ruft das Handle der Bitmap ab, die zuvor mit [SetBitmap](#setbitmap)festgelegt wurde.|
|[CButton::GetButtonStyle](#getbuttonstyle)|Ruft Informationen zum Schaltflächensteuerungsstil ab.|
|[CButton::GetCheck](#getcheck)|Ruft den Prüfstatus eines Schaltflächensteuerelements ab.|
|[CButton::GetCursor](#getcursor)|Ruft das Handle des Cursorbilds ab, das zuvor mit [SetCursor](#setcursor)festgelegt wurde.|
|[CButton::GetIcon](#geticon)|Ruft das Handle des zuvor mit [SetIcon](#seticon)festgelegten Symbols ab.|
|[CButton::GetIdealSize](#getidealsize)|Ruft die ideale Größe des Tastensteuerelements ab.|
|[CButton::GetImageList](#getimagelist)|Ruft die Bildliste des Schaltflächensteuerelements ab.|
|[CButton::GetNote](#getnote)|Ruft die Notizkomponente des aktuellen Befehlsverknüpfungssteuerelements ab.|
|[CButton::GetNoteLength](#getnotelength)|Ruft die Länge des Notiztexts für das aktuelle Befehlsverknüpfungssteuerelement ab.|
|[CButton::GetSplitGlyph](#getsplitglyph)|Ruft die Glyphe ab, die dem aktuellen Steuerelement für die geteilte Schaltfläche zugeordnet ist.|
|[CButton::GetSplitImageList](#getsplitimagelist)|Ruft die Bildliste für das aktuelle Steuerelement für die geteilte Schaltfläche ab.|
|[CButton::GetSplitInfo](#getsplitinfo)|Ruft Informationen ab, die das aktuelle Steuerelement für die geteilte Schaltfläche definieren.|
|[CButton::GetSplitSize](#getsplitsize)|Ruft das umschließende Rechteck der Dropdown-Komponente des aktuellen Geteiltschaltflächensteuerelements ab.|
|[CButton::GetSplitStyle](#getsplitstyle)|Ruft die Stile der geteilten Schaltfläche ab, die das aktuelle Steuerelement für die geteilte Schaltfläche definieren.|
|[CButton::GetState](#getstate)|Ruft den Prüfzustand, den Hervorhebungsstatus und den Fokusstatus eines Schaltflächensteuerelements ab.|
|[CButton::GetTextMargin](#gettextmargin)|Ruft den Textrand des Schaltflächensteuerelements ab.|
|[CButton::SetBitmap](#setbitmap)|Gibt eine Bitmap an, die auf der Schaltfläche angezeigt werden soll.|
|[CButton::SetButtonStyle](#setbuttonstyle)|Ändert den Stil einer Schaltfläche.|
|[CButton::SetCheck](#setcheck)|Legt den Prüfzustand eines Schaltflächensteuerelements fest.|
|[CButton::SetCursor](#setcursor)|Gibt ein Cursorbild an, das auf der Schaltfläche angezeigt werden soll.|
|[CButton::SetDropDownState](#setdropdownstate)|Legt den Dropdown-Status des aktuellen Split-Button-Steuerelements fest.|
|[CButton::SetIcon](#seticon)|Gibt ein Symbol an, das auf der Schaltfläche angezeigt werden soll.|
|[CButton::SetImageList](#setimagelist)|Legt die Bildliste des Schaltflächensteuerelements fest.|
|[CButton::SetNote](#setnote)|Legt die Notiz für das aktuelle Befehlsverknüpfungssteuerelement fest.|
|[CButton::SetSplitGlyph](#setsplitglyph)|Ordnet eine angegebene Glyphe dem aktuellen Split-Button-Steuerelement zu.|
|[CButton::SetSplitImageList](#setsplitimagelist)|Ordnet eine Bildliste dem aktuellen Split-Button-Steuerelement zu.|
|[CButton::SetSplitInfo](#setsplitinfo)|Gibt Informationen an, die das aktuelle Steuerelement für die geteilte Schaltfläche definieren.|
|[CButton::SetSplitSize](#setsplitsize)|Legt das umschließende Rechteck der Dropdown-Komponente des aktuellen Geteiltschaltflächensteuerelements fest.|
|[CButton::SetSplitStyle](#setsplitstyle)|Legt den Stil des aktuellen Geteiltschaltflächensteuerelements fest.|
|[CButton::SetState](#setstate)|Legt den Hervorhebungszustand eines Schaltflächensteuerelements fest.|
|[CButton::SetTextMargin](#settextmargin)|Legt den Textrand des Schaltflächensteuerelements fest.|

## <a name="remarks"></a>Bemerkungen

Ein Schaltflächensteuerelement ist ein kleines, rechteckiges untergeordnetes Fenster, auf das angeklickt und deaktiviert werden kann. Schaltflächen können allein oder in Gruppen verwendet werden und können entweder beschriftet oder ohne Text angezeigt werden. Eine Schaltfläche ändert in der Regel die Darstellung, wenn der Benutzer darauf klickt.

Typische Tasten sind das Kontrollkästchen, das Optionsfeld und die Taste. Ein `CButton` Objekt kann eines dieser Objekte werden, entsprechend dem [Schaltflächenstil,](../../mfc/reference/styles-used-by-mfc.md#button-styles) der bei seiner Initialisierung durch die Memberfunktion [Erstellen](#create) angegeben wurde.

Darüber hinaus unterstützt die [CBitmapButton-Klasse,](../../mfc/reference/cbitmapbutton-class.md) die von `CButton` der Erstellung von Schaltflächensteuerelementen abgeleitet wurde, die mit Bitmap-Bildern anstelle von Text beschriftet sind. A `CBitmapButton` kann separate Bitmaps für den Nach-, Abwärts-, Fokus- und deaktivierten Zuständen einer Schaltfläche haben.

Sie können ein Schaltflächensteuerelement entweder aus einer Dialogfeldvorlage oder direkt im Code erstellen. Rufen Sie in beiden Fällen `CButton` zuerst `CButton` den Konstruktor auf, um das Objekt zu erstellen. rufen Sie `Create` dann die Memberfunktion auf, um `CButton` das Windows-Schaltflächensteuerelement zu erstellen und es an das Objekt anzuhängen.

Die Konstruktion kann ein einstufiger Prozess `CButton`in einer Klasse sein, die von abgeleitet ist. Schreiben Sie einen Konstruktor für `Create` die abgeleitete Klasse und rufen Sie aus dem Konstruktor heraus.

Wenn Sie Windows-Benachrichtigungen verarbeiten möchten, die von einem Schaltflächensteuerelement an das übergeordnete Element gesendet werden (normalerweise eine von [CDialog](../../mfc/reference/cdialog-class.md)abgeleitete Klasse), fügen Sie der übergeordneten Klasse für jede Nachricht einen Nachrichtenzuordnungseintrag und eine Message-Handler-Memberfunktion hinzu.

Jeder Nachrichtenzuordnungseintrag hat die folgende Form:

**\_ON-Benachrichtigung**_Notification_ **(** _id_, _memberFxn_ **)**

wobei *id* die untergeordnete Fenster-ID des Steuerelements angibt, das die Benachrichtigung sendet, und *memberFxn* der Name der übergeordneten Memberfunktion ist, die Sie geschrieben haben, um die Benachrichtigung zu behandeln.

Der Funktionsprototyp des Übergeordneten ist wie folgt:

`afx_msg void memberFxn();`

Potenzielle Nachrichtenzuordnungseinträge sind wie folgt:

|Karteneintrag|Wird an das übergeordnete Element gesendet, wenn...|
|---------------|----------------------------|
|ON_BN_CLICKED|Der Benutzer klickt auf eine Schaltfläche.|
|ON_BN_DOUBLECLICKED|Der Benutzer doppelklickt auf eine Schaltfläche.|

Wenn Sie `CButton` ein Objekt aus einer `CButton` Dialogfeldressource erstellen, wird das Objekt automatisch zerstört, wenn der Benutzer das Dialogfeld schließt.

Wenn Sie `CButton` ein Objekt in einem Fenster erstellen, müssen Sie es möglicherweise zerstören. Wenn Sie `CButton` das Objekt auf dem Heap mithilfe der **neuen** Funktion erstellen, müssen Sie **das Objekt** löschen aufrufen, um es zu zerstören, wenn der Benutzer das Windows-Schaltflächensteuerelement schließt. Wenn Sie `CButton` das Objekt auf dem Stapel erstellen oder es in das übergeordnete Dialogobjekt eingebettet sind, wird es automatisch zerstört.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CButton`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="cbuttoncbutton"></a><a name="cbutton"></a>CButton::CButton

Erstellt ein `CButton`-Objekt.

```
CButton();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]

## <a name="cbuttoncreate"></a><a name="create"></a>CButton::Erstellen

Erstellt das Windows-Schaltflächensteuerelement und `CButton` fügt es an das Objekt an.

```
virtual BOOL Create(
    LPCTSTR lpszCaption,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*lpszCaption*<br/>
Gibt den Text des Schaltflächensteuerelements an.

*dwStyle*<br/>
Gibt den Stil des Schaltflächensteuerelements an. Wenden Sie eine beliebige Kombination von [Schaltflächenstilen](../../mfc/reference/styles-used-by-mfc.md#button-styles) auf die Schaltfläche an.

*Rect*<br/>
Gibt die Größe und Position des Schaltflächensteuerelements an. Es kann entweder `CRect` ein `RECT` Objekt oder eine Struktur sein.

*pParentWnd*<br/>
Gibt das übergeordnete Fenster des Schaltflächensteuerelements an, in der Regel eine `CDialog`. Es darf nicht NULL sein.

*nID*<br/>
Gibt die ID des Schaltflächensteuerelements an.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CButton` ein Objekt in zwei Schritten. Rufen Sie zunächst den Konstruktor auf, und rufen Sie dann `Create` `CButton` auf, das das Windows-Schaltflächensteuerelement erstellt und an das Objekt anfügt.

Wenn der WS_VISIBLE-Stil angegeben ist, sendet Windows die Schaltflächensteuerung aller Nachrichten, die zum Aktivieren und Anzeigen der Schaltfläche erforderlich sind.

Wenden Sie die folgenden [Fensterstile](../../mfc/reference/styles-used-by-mfc.md#window-styles) auf ein Schaltflächensteuerelement an:

- WS_CHILD Immer

- WS_VISIBLE In der Regel

- WS_DISABLED Selten

- WS_GROUP Zu Gruppensteuerelementen

- WS_TABSTOP So schließen Sie die Schaltfläche in die Tab-Reihenfolge ein

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]

## <a name="cbuttondrawitem"></a><a name="drawitem"></a>CButton::DrawItem

Wird vom Framework aufgerufen, wenn sich ein visueller Aspekt einer vom Besitzer gezeichneten Schaltfläche geändert hat.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parameter

*lpDrawItemStruct*<br/>
Ein langer Zeiger auf eine [DRAWITEMSTRUCT-Struktur.](/windows/win32/api/winuser/ns-winuser-drawitemstruct) Die Struktur enthält Informationen über das zu zeichnende Element und den erforderlichen Zeichnungstyp.

### <a name="remarks"></a>Bemerkungen

Eine vom Besitzer gezeichnete Schaltfläche verfügt über den Stil satzsatz BS_OWNERDRAW. Überschreiben Sie diese Memberfunktion, um `CButton` die Zeichnung für ein vom Besitzer gezeichnetes Objekt zu implementieren. Die Anwendung sollte alle GDI-Objekte (Graphics Device Interface) wiederherstellen, die für den anzeigekontext ausgewählt wurden, der in *lpDrawItemStruct* angegeben wird, bevor die Memberfunktion beendet wird.

Sehen Sie sich auch die [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) Stilwerte an.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]

## <a name="cbuttongetbitmap"></a><a name="getbitmap"></a>CButton::GetBitmap

Rufen Sie diese Memberfunktion auf, um das Handle einer Bitmap abzurufen, die zuvor mit [SetBitmap](#setbitmap)festgelegt wurde und einer Schaltfläche zugeordnet ist.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für eine Bitmap. NULL, wenn zuvor keine Bitmap angegeben wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

## <a name="cbuttongetbuttonstyle"></a><a name="getbuttonstyle"></a>CButton::GetButtonStyle

Ruft Informationen zum Schaltflächensteuerungsstil ab.

```
UINT GetButtonStyle() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die Schaltflächenstile für dieses `CButton` Objekt zurück. Diese Funktion gibt nur die [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) Stilwerte zurück, nicht die anderen Fensterstile.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

## <a name="cbuttongetcheck"></a><a name="getcheck"></a>CButton::GetCheck

Ruft den Kontrollkästchenstatus eines Optionsfelds oder Kontrollkästchens ab.

```
int GetCheck() const;
```

### <a name="return-value"></a>Rückgabewert

Der Rückgabewert eines Schaltflächensteuerelements, das mit dem Stil BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON oder BS_3STATE erstellt wurde, ist einer der folgenden Werte:

|Wert|Bedeutung|
|-----------|-------------|
|BST_UNCHECKED|Der Schaltflächenstatus ist deaktiviert.|
|Bst_checked|Der Schaltflächenstatus ist aktiviert.|
|BST_INDETERMINATE|Der Schaltflächenstatus ist unbestimmt (gilt nur, wenn die Schaltfläche den BS_3STATE oder BS_AUTO3STATE Stil hat).|

Wenn die Schaltfläche einen anderen Stil hat, wird der Rückgabewert BST_UNCHECKED.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

## <a name="cbuttongetcursor"></a><a name="getcursor"></a>CButton::GetCursor

Rufen Sie diese Memberfunktion auf, um das Handle eines Cursors abzurufen, der zuvor mit [SetCursor](#setcursor)festgelegt wurde und einer Schaltfläche zugeordnet ist.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für ein Cursorbild. NULL, wenn zuvor kein Cursor angegeben wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

## <a name="cbuttongeticon"></a><a name="geticon"></a>CButton::GetIcon

Rufen Sie diese Memberfunktion auf, um das Handle eines Symbols abzurufen, das zuvor mit [SetIcon](#seticon)festgelegt wurde und einer Schaltfläche zugeordnet ist.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für ein Symbol. NULL, wenn zuvor kein Symbol angegeben wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

## <a name="cbuttongetidealsize"></a><a name="getidealsize"></a>CButton::GetIdealSize

Ruft die ideale Größe für die Tastensteuerung ab.

```
BOOL GetIdealSize(SIZE* psize);
```

### <a name="parameters"></a>Parameter

*psize*<br/>
Ein Zeiger auf die aktuelle Größe der Schaltfläche.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion emuliert die Funktionalität der BCM_GETIDEALSIZE Nachricht, wie im Abschnitt [Schaltflächen](/windows/win32/controls/buttons) des Windows SDK beschrieben.

## <a name="cbuttongetimagelist"></a><a name="getimagelist"></a>CButton::GetImageList

Rufen Sie diese Methode auf, um die Bildliste aus dem Schaltflächensteuerelement abzurufen.

```
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Parameter

*pbuttonImagelist*<br/>
Ein Zeiger auf die Bildliste des `CButton` Objekts.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion emuliert die Funktionalität der BCM_GETIMAGELIST Nachricht, wie im Abschnitt [Schaltflächen](/windows/win32/controls/buttons) des Windows SDK beschrieben.

## <a name="cbuttongetnote"></a><a name="getnote"></a>CButton::GetNote

Ruft den Notiztext ab, der dem aktuellen Befehlsverknüpfungssteuerelement zugeordnet ist.

```
CString GetNote() const;

BOOL GetNote(
    LPTSTR lpszNote,
    UINT* cchNote) const;
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*lpszNote*|[out] Zeiger auf einen Puffer, für den der Aufrufer verantwortlich ist. Wenn der Rückgabewert TRUE ist, enthält der Puffer den Notiztext, der dem aktuellen Befehlsverknüpfungssteuerelement zugeordnet ist. Andernfalls bleibt der Puffer unverändert.|
|*cchNote*|[in, out] Ein Zeiger auf eine nicht signierte Ganzzahlvariable.<br /><br /> Wenn diese Methode aufgerufen wird, enthält die Variable die Größe des Puffers, der durch den Parameter *lpszNote* angegeben wird.<br /><br /> Wenn diese Methode zurückkehrt, wenn der Rückgabewert TRUE ist, enthält die Variable die Größe der Notiz, die dem aktuellen Befehlsverknüpfungssteuerelement zugeordnet ist. Wenn der Rückgabewert FALSE ist, enthält die Variable die Puffergröße, die erforderlich ist, um die Notiz zu enthalten.|

### <a name="return-value"></a>Rückgabewert

Bei der ersten Überladung ein [CString-Objekt,](../../atl-mfc-shared/using-cstring.md) das den Notiztext enthält, der dem aktuellen Befehlsverknüpfungssteuerelement zugeordnet ist.

Oder

In der zweiten Überladung TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur mit Steuerelementen, deren Schaltflächenstil BS_COMMANDLINK oder BS_DEFCOMMANDLINK ist.

Diese Methode sendet die [BCM_GETNOTE](/windows/win32/Controls/bcm-getnote) Nachricht, die im Windows SDK beschrieben wird.

## <a name="cbuttongetnotelength"></a><a name="getnotelength"></a>CButton::GetNoteLength

Ruft die Länge des Notiztexts für das aktuelle Befehlsverknüpfungssteuerelement ab.

```
UINT GetNoteLength() const;
```

### <a name="return-value"></a>Rückgabewert

Die Länge des Notiztexts in 16-Bit-Unicode-Zeichen für das aktuelle Befehlsverknüpfungssteuerelement.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur mit Steuerelementen, deren Schaltflächenstil BS_COMMANDLINK oder BS_DEFCOMMANDLINK ist.

Diese Methode sendet die [BCM_GETNOTELENGTH](/windows/win32/Controls/bcm-getnotelength) Nachricht, die im Windows SDK beschrieben wird.

## <a name="cbuttongetsplitglyph"></a><a name="getsplitglyph"></a>CButton::GetSplitGlyph

Ruft die Glyphe ab, die dem aktuellen Steuerelement für die geteilte Schaltfläche zugeordnet ist.

```
TCHAR GetSplitGlyph() const;
```

### <a name="return-value"></a>Rückgabewert

Das Glyphenzeichen, das dem aktuellen Steuerelement für die geteilte Schaltfläche zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Eine Glyphe ist die physische Darstellung eines Zeichens in einer bestimmten Schriftart. Beispielsweise kann ein Split-Button-Steuerelement mit der Glyphe des Unicode-Häkchenzeichens (U+2713) verziert werden.

Verwenden Sie diese Methode nur mit Steuerelementen, deren Schaltflächenstil BS_SPLITBUTTON oder BS_DEFSPLITBUTTON ist.

Diese Methode initialisiert `mask` das Member einer [BUTTON_SPLITINFO-Struktur](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) mit dem BCSIF_GLYPH-Flag und sendet diese Struktur dann in der [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) Nachricht, die im Windows SDK beschrieben wird. Wenn die Nachrichtenfunktion zurückgegeben wird, ruft `himlGlyph` diese Methode die Glyphe vom Element der Struktur ab.

## <a name="cbuttongetsplitimagelist"></a><a name="getsplitimagelist"></a>CButton::GetSplitImageList

Ruft die [Bildliste](../../mfc/reference/cimagelist-class.md) für das aktuelle Steuerelement für die geteilte Schaltfläche ab.

```
CImageList* GetSplitImageList() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CImageList-Objekt.](../../mfc/reference/cimagelist-class.md)

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur mit Steuerelementen, deren Schaltflächenstil BS_SPLITBUTTON oder BS_DEFSPLITBUTTON ist.

Diese Methode initialisiert `mask` das Member einer [BUTTON_SPLITINFO-Struktur](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) mit dem BCSIF_IMAGE-Flag und sendet diese Struktur dann in der [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) Nachricht, die im Windows SDK beschrieben wird. Wenn die Nachrichtenfunktion zurückkehrt, ruft diese Methode `himlGlyph` die Bildliste vom Element der Struktur ab.

## <a name="cbuttongetsplitinfo"></a><a name="getsplitinfo"></a>CButton::GetSplitInfo

Ruft Parameter ab, die bestimmen, wie Windows das aktuelle Steuerelement für die geteilte Schaltfläche zeichnet.

```
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Pinfo*|[out] Zeiger auf eine [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) Struktur, die Informationen über das aktuelle Steuerelement für die geteilte Schaltfläche empfängt. Der Aufrufer ist für die Zuweisung der Struktur verantwortlich.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur mit Steuerelementen, deren Schaltflächenstil BS_SPLITBUTTON oder BS_DEFSPLITBUTTON ist.

Diese Methode sendet die [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) Nachricht, die im Windows SDK beschrieben wird.

## <a name="cbuttongetsplitsize"></a><a name="getsplitsize"></a>CButton::GetSplitSize

Ruft das umschließende Rechteck der Dropdown-Komponente des aktuellen Geteiltschaltflächensteuerelements ab.

```
BOOL GetSplitSize(LPSIZE pSize) const;
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*pSize*|[out] Zeiger auf [SIZE](/windows/win32/api/windef/ns-windef-size) eine SIZE-Struktur, die die Beschreibung eines Rechtecks empfängt.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur mit Steuerelementen, deren Schaltflächenstil BS_SPLITBUTTON oder BS_DEFSPLITBUTTON ist.

Wenn das Steuerelement für die geteilte Schaltfläche erweitert wird, kann eine Dropdownkomponente wie ein Listensteuerelement oder ein Pagersteuerelement angezeigt werden. Diese Methode ruft das umschließende Rechteck ab, das die Dropdownkomponente enthält.

Diese Methode initialisiert `mask` das Element einer [BUTTON_SPLITINFO-Struktur](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) mit dem BCSIF_SIZE-Flag und sendet diese Struktur dann in der [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) Nachricht, die im Windows SDK beschrieben wird. Wenn die Nachrichtenfunktion zurückgegeben wird, ruft diese `size` Methode das umgrenzende Rechteck aus dem Element der Struktur ab.

## <a name="cbuttongetsplitstyle"></a><a name="getsplitstyle"></a>CButton::GetSplitStyle

Ruft die Stile der geteilten Schaltfläche ab, die das aktuelle Steuerelement für die geteilte Schaltfläche definieren.

```
UINT GetSplitStyle() const;
```

### <a name="return-value"></a>Rückgabewert

Eine bitweise Kombination von Split-Button-Stilen. Weitere Informationen finden `uSplitStyle` Sie im Member der [BUTTON_SPLITINFO-Struktur.](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur mit Steuerelementen, deren Schaltflächenstil BS_SPLITBUTTON oder BS_DEFSPLITBUTTON ist.

Die Stile der geteilten Schaltfläche geben die Ausrichtung, das Seitenverhältnis und das grafische Format an, mit dem Windows ein Trennschaltflächensymbol zeichnet.

Diese Methode initialisiert `mask` das Element einer [BUTTON_SPLITINFO-Struktur](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) mit dem BCSIF_STYLE-Flag und sendet diese Struktur dann in der [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) Nachricht, die im Windows SDK beschrieben wird. Wenn die Nachrichtenfunktion zurückgegeben wird, ruft diese `uSplitStyle` Methode die Stile der geteilten Schaltfläche vom Element der Struktur ab.

## <a name="cbuttongetstate"></a><a name="getstate"></a>CButton::GetState

Ruft den Status eines Schaltflächensteuerelements ab.

```
UINT GetState() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Bitfeld, das die Kombination von Werten enthält, die den aktuellen Status eines Schaltflächensteuerelements angeben. In der folgenden Tabelle sind mögliche Werte aufgeführt.

|Button-Status|Wert|BESCHREIBUNG|
|------------------|-----------|-----------------|
|BST_UNCHECKED|0x0000|Der Anfangszustand.|
|Bst_checked|0x0001|Das Tastensteuerelement ist aktiviert.|
|BST_INDETERMINATE|0x0002|Der Zustand ist unbestimmt (nur möglich, wenn das Tastensteuerelement drei Zustände hat).|
|BST_PUSHED|0x0004|Die Tastensteuerung wird gedrückt.|
|BST_FOCUS|0x0008|Das Tastensteuerelement hat den Fokus.|

### <a name="remarks"></a>Bemerkungen

Ein Schaltflächensteuerelement mit dem BS_3STATE- oder BS_AUTO3STATE-Schaltflächenstil erstellt ein Kontrollkästchen mit einem dritten Status, der den unbestimmten Status trägt. Der unbestimmte Status gibt an, dass das Kontrollkästchen weder aktiviert noch deaktiviert ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

## <a name="cbuttongettextmargin"></a><a name="gettextmargin"></a>CButton::GetTextMargin

Rufen Sie diese Methode auf, `CButton` um den Textrand des Objekts abzurufen.

```
BOOL GetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Parameter

*pmargin*<br/>
Ein Zeiger auf den Textrand des `CButton` Objekts.

### <a name="return-value"></a>Rückgabewert

Gibt den Textrand zurück.

### <a name="remarks"></a>Bemerkungen

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion emuliert die Funktionalität der BCM_GETTEXTMARGIN Nachricht, wie im Abschnitt [Schaltflächen](/windows/win32/controls/buttons) des Windows SDK beschrieben.

## <a name="cbuttonsetbitmap"></a><a name="setbitmap"></a>CButton::SetBitmap

Rufen Sie diese Memberfunktion auf, um der Schaltfläche eine neue Bitmap zuzuordnen.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parameter

*hBitmap*<br/>
Das Handle einer Bitmap.

### <a name="return-value"></a>Rückgabewert

Das Handle einer Bitmap, die zuvor der Schaltfläche zugeordnet war.

### <a name="remarks"></a>Bemerkungen

Die Bitmap wird automatisch auf der Fläche der Schaltfläche platziert, standardmäßig zentriert. Wenn die Bitmap zu groß für die Schaltfläche ist, wird sie auf beiden Seiten abgeschnitten. Sie können andere Ausrichtungsoptionen auswählen, einschließlich der folgenden:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

Im Gegensatz zu [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), das `SetBitmap` vier Bitmaps pro Schaltfläche verwendet, wird nur eine Bitmap pro Schaltfläche verwendet. Wenn die Taste gedrückt wird, scheint sich die Bitmap nach unten und nach rechts zu verschieben.

Sie sind dafür verantwortlich, die Bitmap freizugeben, wenn Sie damit fertig sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

## <a name="cbuttonsetbuttonstyle"></a><a name="setbuttonstyle"></a>CButton::SetButtonStyle

Ändert den Stil einer Schaltfläche.

```cpp
void SetButtonStyle(
    UINT nStyle,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parameter

*nStyle*<br/>
Gibt den [Schaltflächenstil an.](../../mfc/reference/styles-used-by-mfc.md#button-styles)

*bZeichnung*<br/>
Gibt an, ob die Schaltfläche neu gezeichnet werden soll. Ein Wert ungleich Null zeichnet die Schaltfläche neu. Ein Wert 0 zeichnet die Schaltfläche nicht neu. Die Schaltfläche wird standardmäßig neu gezeichnet.

### <a name="remarks"></a>Bemerkungen

Verwenden `GetButtonStyle` Sie die Memberfunktion, um den Schaltflächenstil abzurufen. Das Wort mit niedriger Ordnung des vollständigen Schaltflächenstils ist der tastenspezifische Stil.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

## <a name="cbuttonsetcheck"></a><a name="setcheck"></a>CButton::SetCheck

Legt den Kontrollkästchenzustand eines Optionsfelds oder Kontrollkästchens fest oder setzt ihn zurück.

```cpp
void SetCheck(int nCheck);
```

### <a name="parameters"></a>Parameter

*nCheck*<br/>
Gibt den Prüfzustand an. Der Parameter kann eine der folgenden Einstellungen haben:

|Wert|Bedeutung|
|-----------|-------------|
|BST_UNCHECKED|Legen Sie den Schaltflächenstatus auf unaktiviert fest.|
|Bst_checked|Legen Sie den Schaltflächenstatus auf aktiviert fest.|
|BST_INDETERMINATE|Legen Sie den Schaltflächenstatus auf unbestimmt fest. Dieser Wert kann nur verwendet werden, wenn die Schaltfläche den BS_3STATE- oder BS_AUTO3STATE-Stil hat.|

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion hat keine Auswirkungen auf einen Druckknopf.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

## <a name="cbuttonsetcursor"></a><a name="setcursor"></a>CButton::SetCursor

Rufen Sie diese Memberfunktion auf, um der Schaltfläche einen neuen Cursor zuzuordnen.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Parameter

*hCursor*<br/>
Das Handle eines Cursors.

### <a name="return-value"></a>Rückgabewert

Das Handle eines Cursors, der zuvor der Schaltfläche zugeordnet war.

### <a name="remarks"></a>Bemerkungen

Der Cursor wird automatisch auf der Fläche der Schaltfläche platziert, standardmäßig zentriert. Wenn der Cursor zu groß für die Schaltfläche ist, wird er auf beiden Seiten abgeschnitten. Sie können andere Ausrichtungsoptionen auswählen, einschließlich der folgenden:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

Im Gegensatz zu [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), das `SetCursor` vier Bitmaps pro Schaltfläche verwendet, wird nur ein Cursor pro Schaltfläche verwendet. Wenn die Taste gedrückt wird, scheint sich der Cursor nach unten und nach rechts zu bewegen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

## <a name="cbuttonsetdropdownstate"></a><a name="setdropdownstate"></a>CButton::SetDropDownState

Legt den Dropdown-Status des aktuellen Split-Button-Steuerelements fest.

```
BOOL SetDropDownState(BOOL fDropDown);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*fDropDown*|[in] TRUE, um BST_DROPDOWNPUSHED Zustand festzulegen; andernfalls FALSE.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Ein Split-Button-Steuerelement hat einen Stil von BS_SPLITBUTTON oder BS_DEFSPLITBUTTON und besteht aus einer Schaltfläche und einem Dropdown-Pfeil auf der rechten Seite. Weitere Informationen finden Sie unter [Schaltflächenstile](/windows/win32/Controls/button-styles). Normalerweise wird der Dropdown-Status festgelegt, wenn der Benutzer auf den Dropdownpfeil klickt. Verwenden Sie diese Methode, um den Dropdown-Status des Steuerelements programmgesteuert festzulegen. Der Dropdown-Pfeil wird schattiert gezeichnet, um den Status anzuzeigen.

Diese Methode sendet die [BCM_SETDROPDOWNSTATE](/windows/win32/Controls/bcm-setdropdownstate) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die Variable *m_splitButton*definiert, die für den programmgesteuerten Zugriff auf das Steuerelement der geteilten Schaltfläche verwendet wird. Diese Variable wird im folgenden Beispiel verwendet.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird der Status des Steuerelements für geteilte Schaltflächen so festgelegt, dass der Dropdownpfeil gedrückt wird.

[!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]

## <a name="cbuttonsetelevationrequired"></a><a name="setelevationrequired"></a>CButton::SetElevationRequired

Legt den Status des aktuellen `elevation required`Schaltflächensteuerelements auf , das erforderlich ist, damit das Steuerelement ein erhöhtes Sicherheitssymbol anzeigt.

```
BOOL SetElevationRequired(BOOL fElevationRequired);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*fElevationRequired*|[in] TRUE, `elevation required` um den Status festzulegen; andernfalls FALSE.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Wenn eine Schaltfläche n- oder Befehlsverknüpfungssteuerung eine erhöhte `elevation required` Sicherheitsberechtigung zum Ausführen einer Aktion erfordert, legen Sie das Steuerelement auf Status fest. Anschließend zeigt Windows das Schildsymbol der Benutzerkontensteuerung (User Account Control, UAC) auf dem Steuerelement an. Weitere Informationen finden Sie unter "Benutzerkontensteuerung" unter [MSDN](https://go.microsoft.com/fwlink/p/?linkid=18507).

Diese Methode sendet die [BCM_SETSHIELD](/windows/win32/Controls/bcm-setshield) Nachricht, die im Windows SDK beschrieben wird.

## <a name="cbuttonseticon"></a><a name="seticon"></a>CButton::SetIcon

Rufen Sie diese Memberfunktion auf, um der Schaltfläche ein neues Symbol zuzuordnen.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Parameter

*hIcon*<br/>
Das Handle eines Symbols.

### <a name="return-value"></a>Rückgabewert

Das Handle eines Symbols, das zuvor der Schaltfläche zugeordnet war.

### <a name="remarks"></a>Bemerkungen

Das Symbol wird automatisch auf der Fläche der Schaltfläche platziert, standardmäßig zentriert. Wenn das Symbol zu groß für die Schaltfläche ist, wird es auf beiden Seiten abgeschnitten. Sie können andere Ausrichtungsoptionen auswählen, einschließlich der folgenden:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

Im Gegensatz zu [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), das `SetIcon` vier Bitmaps pro Schaltfläche verwendet, wird nur ein Symbol pro Schaltfläche verwendet. Wenn die Taste gedrückt wird, scheint sich das Symbol nach unten und nach rechts zu verschieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

## <a name="cbuttonsetimagelist"></a><a name="setimagelist"></a>CButton::SetImageList

Rufen Sie diese Methode auf, `CButton` um die Bildliste des Objekts festzulegen.

```
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Parameter

*pbuttonImagelist*<br/>
Ein Zeiger auf die neue Bildliste.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion emuliert die Funktionalität der BCM_SETIMAGELIST Nachricht, wie im Abschnitt [Schaltflächen](/windows/win32/controls/buttons) des Windows SDK beschrieben.

## <a name="cbuttonsetnote"></a><a name="setnote"></a>CButton::SetNote

Legt den Notiztext für das aktuelle Befehlsverknüpfungssteuerelement fest.

```
BOOL SetNote(LPCTSTR lpszNote);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*lpszNote*|[in] Zeiger auf eine Unicode-Zeichenfolge, die als Notiztext für das Befehlsverknüpfungssteuerelement festgelegt ist.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur mit Steuerelementen, deren Schaltflächenstil BS_COMMANDLINK oder BS_DEFCOMMANDLINK ist.

Diese Methode sendet die [BCM_SETNOTE](/windows/win32/Controls/bcm-setnote) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die Variable *m_cmdLink*definiert, die für den programmgesteuerten Zugriff auf das Befehlsverknüpfungssteuerelement verwendet wird. Diese Variable wird im folgenden Beispiel verwendet.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird der Notiztext für das Befehlsverknüpfungssteuerelement festgelegt.

[!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]

## <a name="cbuttonsetsplitglyph"></a><a name="setsplitglyph"></a>CButton::SetSplitGlyph

Ordnet eine angegebene Glyphe dem aktuellen Split-Button-Steuerelement zu.

```
BOOL SetSplitGlyph(TCHAR chGlyph);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*chGlyph*|[in] Ein Zeichen, das die Glyphe angibt, die als Dropdownpfeil der geteilten Schaltfläche verwendet werden soll.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur mit Steuerelementen, die den Schaltflächenstil BS_SPLITBUTTON oder BS_DEFSPLITBUTTON haben.

Eine Glyphe ist die physische Darstellung eines Zeichens in einer bestimmten Schriftart. Der *Parameter chGlyph* wird nicht als Glyphe verwendet, sondern zum Auswählen einer Glyphe aus einer Reihe systemdefinierter Glyphen. Die standardmäßige Dropdown-Pfeil-Glyphe wird durch ein Zeichen '6' angegeben und ähnelt dem Unicode-Zeichen BLACK DOWN-POINTING TRIANGLE (U+25BC).

Diese Methode initialisiert `mask` das Member einer [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) Struktur `himlGlyph` mit dem BCSIF_GLYPH-Flag und das Member mit dem *Parameter chGlyph* und sendet diese Struktur dann in der [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) Nachricht, die im Windows SDK beschrieben wird.

## <a name="cbuttonsetsplitimagelist"></a><a name="setsplitimagelist"></a>CButton::SetSplitImageList

Ordnet eine [Bildliste](../../mfc/reference/cimagelist-class.md) dem aktuellen Split-Button-Steuerelement zu.

```
BOOL SetSplitImageList(CImageList* pSplitImageList);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*pSplitImageList*|[in] Zeiger auf ein [CImageList-Objekt,](../../mfc/reference/cimagelist-class.md) das dem aktuellen Split-Button-Steuerelement zugewiesen werden soll.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur mit Steuerelementen, deren Schaltflächenstil BS_SPLITBUTTON oder BS_DEFSPLITBUTTON ist.

Diese Methode initialisiert `mask` den Member einer [BUTTON_SPLITINFO-Struktur](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) `himlGlyph` mit dem BCSIF_IMAGE-Flag und das Member mit dem Parameter *pSplitImageList* und sendet diese Struktur dann in der [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) Nachricht, die im Windows SDK beschrieben wird.

## <a name="cbuttonsetsplitinfo"></a><a name="setsplitinfo"></a>CButton::SetSplitInfo

Gibt Parameter an, die bestimmen, wie Windows das aktuelle Steuerelement für die geteilte Schaltfläche zeichnet.

```
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Pinfo*|[in] Zeiger auf eine [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) Struktur, die das aktuelle Steuerelement für geteilte Schaltflächen definiert.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur mit Steuerelementen, deren Schaltflächenstil BS_SPLITBUTTON oder BS_DEFSPLITBUTTON ist.

Diese Methode sendet die [BCM_SETSPLITINFO](/windows/win32/Controls/bcm-setsplitinfo) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird `m_splitButton`die Variable , definiert, die für den programmgesteuerten Zugriff auf das Steuerelement der geteilten Schaltfläche verwendet wird.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die Glyphe geändert, die für den Dropdown-Pfeil der geteilten Schaltfläche verwendet wird. Das Beispiel ersetzt eine nach oben zeigende Dreiecksglyphe für die standardmäßig nach unten zeigende Dreiecksglyphe. Die angezeigte Glyphe hängt von dem `himlGlyph` Zeichen ab, das Sie im Element der `BUTTON_SPLITINFO` Struktur angeben. Die nach unten zeigende Dreiecksglyphe wird durch ein Zeichen '6' und die nach oben zeigende Dreiecksglyphe durch ein Zeichen '5' angegeben. Zum Vergleich siehe die Convenience-Methode [CButton::SetSplitGlyph](#setsplitglyph).

[!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]

## <a name="cbuttonsetsplitsize"></a><a name="setsplitsize"></a>CButton::SetSplitSize

Legt das umschließende Rechteck der Dropdown-Komponente des aktuellen Geteiltschaltflächensteuerelements fest.

```
BOOL SetSplitSize(LPSIZE pSize);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*pSize*|[in] Zeiger auf [SIZE](/windows/win32/api/windef/ns-windef-size) eine SIZE-Struktur, die ein umgrenzendes Rechteck beschreibt.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur mit Steuerelementen, deren Schaltflächenstil BS_SPLITBUTTON oder BS_DEFSPLITBUTTON ist.

Wenn das Steuerelement für die geteilte Schaltfläche erweitert wird, kann eine Dropdownkomponente wie ein Listensteuerelement oder ein Pagersteuerelement angezeigt werden. Diese Methode gibt die Größe des umschließenden Rechtecks an, das die Dropdownkomponente enthält.

Diese Methode initialisiert `mask` das Element einer [BUTTON_SPLITINFO-Struktur](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) `size` mit dem BCSIF_SIZE-Flag und das Member mit dem *Parameter pSize* und sendet diese Struktur dann in der [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird `m_splitButton`die Variable , definiert, die für den programmgesteuerten Zugriff auf das Steuerelement der geteilten Schaltfläche verwendet wird. Diese Variable wird im folgenden Beispiel verwendet.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die Größe des Dropdownpfeils der geteilten Schaltfläche verdoppelt.

[!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]

## <a name="cbuttonsetsplitstyle"></a><a name="setsplitstyle"></a>CButton::SetSplitStyle

Legt den Stil des aktuellen Geteiltschaltflächensteuerelements fest.

```
BOOL SetSplitStyle(UINT uSplitStyle);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*uSplitStyle*|[in] Eine bitweise Kombination von Split-Button-Stilen. Weitere Informationen finden `uSplitStyle` Sie im Member der [BUTTON_SPLITINFO-Struktur.](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur mit Steuerelementen, deren Schaltflächenstil BS_SPLITBUTTON oder BS_DEFSPLITBUTTON ist.

Die Stile der geteilten Schaltfläche geben die Ausrichtung, das Seitenverhältnis und das grafische Format an, mit dem Windows ein Trennschaltflächensymbol zeichnet. Weitere Informationen finden `uSplitStyle` Sie im Member der [BUTTON_SPLITINFO-Struktur.](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)

Diese Methode initialisiert `mask` das Member einer [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) Struktur `uSplitStyle` mit dem BCSIF_STYLE-Flag und das Member mit dem Parameter *uSplitStyle* und sendet diese Struktur dann in der [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird `m_splitButton`die Variable , definiert, die für den programmgesteuerten Zugriff auf das Steuerelement der geteilten Schaltfläche verwendet wird.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird der Stil des Dropdownpfeils für die geteilte Schaltfläche festgelegt. Der Stil BCSS_ALIGNLEFT zeigt den Pfeil auf der linken Seite der Schaltfläche an, und der BCSS_STRETCH-Stil behält die Proportionen des Dropdownpfeils bei, wenn Sie die Größe der Schaltfläche ändern.

[!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]

## <a name="cbuttonsetstate"></a><a name="setstate"></a>CButton::SetState

Legt fest, ob ein Schaltflächensteuerelement hervorgehoben ist oder nicht.

```cpp
void SetState(BOOL bHighlight);
```

### <a name="parameters"></a>Parameter

*bHighlight*<br/>
Gibt an, ob die Schaltfläche hervorgehoben werden soll. Ein Wert ungleich Null hebt die Schaltfläche hervor. ein 0-Wert entfernt alle Hervorhebungen.

### <a name="remarks"></a>Bemerkungen

Die Hervorhebung wirkt sich auf das Äußere eines Schaltflächensteuerelements aus. Es hat keine Auswirkungen auf den Checkstatus eines Optionsfelds oder Kontrollkästchens.

Ein Schaltflächensteuerelement wird automatisch hervorgehoben, wenn der Benutzer auf die linke Maustaste klickt und die linke Maustaste hält. Die Hervorhebung wird entfernt, wenn der Benutzer die Maustaste loslässt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

## <a name="cbuttonsettextmargin"></a><a name="settextmargin"></a>CButton::SetTextMargin

Rufen Sie diese Methode auf, `CButton` um den Textrand des Objekts festzulegen.

```
BOOL SetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Parameter

*pmargin*<br/>
Ein Zeiger auf den neuen Textrand.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion emuliert die Funktionalität der BCM_SETTEXTMARGIN Nachricht, wie im Abschnitt [Schaltflächen](/windows/win32/controls/buttons) des Windows SDK beschrieben.

## <a name="see-also"></a>Weitere Informationen

[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[CComboBox-Klasse](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox-Klasse](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar-Klasse](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic-Klasse](../../mfc/reference/cstatic-class.md)<br/>
[CBitmapButton-Klasse](../../mfc/reference/cbitmapbutton-class.md)<br/>
[CDialog-Klasse](../../mfc/reference/cdialog-class.md)
