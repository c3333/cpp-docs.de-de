---
title: CRichEditView-Klasse
ms.date: 11/04/2016
f1_keywords:
- CRichEditView
- AFXRICH/CRichEditView
- AFXRICH/CRichEditView::CRichEditView
- AFXRICH/CRichEditView::AdjustDialogPosition
- AFXRICH/CRichEditView::CanPaste
- AFXRICH/CRichEditView::DoPaste
- AFXRICH/CRichEditView::FindText
- AFXRICH/CRichEditView::FindTextSimple
- AFXRICH/CRichEditView::GetCharFormatSelection
- AFXRICH/CRichEditView::GetDocument
- AFXRICH/CRichEditView::GetInPlaceActiveItem
- AFXRICH/CRichEditView::GetMargins
- AFXRICH/CRichEditView::GetPageRect
- AFXRICH/CRichEditView::GetPaperSize
- AFXRICH/CRichEditView::GetParaFormatSelection
- AFXRICH/CRichEditView::GetPrintRect
- AFXRICH/CRichEditView::GetPrintWidth
- AFXRICH/CRichEditView::GetRichEditCtrl
- AFXRICH/CRichEditView::GetSelectedItem
- AFXRICH/CRichEditView::GetTextLength
- AFXRICH/CRichEditView::GetTextLengthEx
- AFXRICH/CRichEditView::InsertFileAsObject
- AFXRICH/CRichEditView::InsertItem
- AFXRICH/CRichEditView::IsRichEditFormat
- AFXRICH/CRichEditView::OnCharEffect
- AFXRICH/CRichEditView::OnParaAlign
- AFXRICH/CRichEditView::OnUpdateCharEffect
- AFXRICH/CRichEditView::OnUpdateParaAlign
- AFXRICH/CRichEditView::PrintInsideRect
- AFXRICH/CRichEditView::PrintPage
- AFXRICH/CRichEditView::SetCharFormat
- AFXRICH/CRichEditView::SetMargins
- AFXRICH/CRichEditView::SetPaperSize
- AFXRICH/CRichEditView::SetParaFormat
- AFXRICH/CRichEditView::TextNotFound
- AFXRICH/CRichEditView::GetClipboardData
- AFXRICH/CRichEditView::GetContextMenu
- AFXRICH/CRichEditView::IsSelected
- AFXRICH/CRichEditView::OnFindNext
- AFXRICH/CRichEditView::OnInitialUpdate
- AFXRICH/CRichEditView::OnPasteNativeObject
- AFXRICH/CRichEditView::OnPrinterChanged
- AFXRICH/CRichEditView::OnReplaceAll
- AFXRICH/CRichEditView::OnReplaceSel
- AFXRICH/CRichEditView::OnTextNotFound
- AFXRICH/CRichEditView::QueryAcceptData
- AFXRICH/CRichEditView::WrapChanged
- AFXRICH/CRichEditView::m_nBulletIndent
- AFXRICH/CRichEditView::m_nWordWrap
helpviewer_keywords:
- CRichEditView [MFC], CRichEditView
- CRichEditView [MFC], AdjustDialogPosition
- CRichEditView [MFC], CanPaste
- CRichEditView [MFC], DoPaste
- CRichEditView [MFC], FindText
- CRichEditView [MFC], FindTextSimple
- CRichEditView [MFC], GetCharFormatSelection
- CRichEditView [MFC], GetDocument
- CRichEditView [MFC], GetInPlaceActiveItem
- CRichEditView [MFC], GetMargins
- CRichEditView [MFC], GetPageRect
- CRichEditView [MFC], GetPaperSize
- CRichEditView [MFC], GetParaFormatSelection
- CRichEditView [MFC], GetPrintRect
- CRichEditView [MFC], GetPrintWidth
- CRichEditView [MFC], GetRichEditCtrl
- CRichEditView [MFC], GetSelectedItem
- CRichEditView [MFC], GetTextLength
- CRichEditView [MFC], GetTextLengthEx
- CRichEditView [MFC], InsertFileAsObject
- CRichEditView [MFC], InsertItem
- CRichEditView [MFC], IsRichEditFormat
- CRichEditView [MFC], OnCharEffect
- CRichEditView [MFC], OnParaAlign
- CRichEditView [MFC], OnUpdateCharEffect
- CRichEditView [MFC], OnUpdateParaAlign
- CRichEditView [MFC], PrintInsideRect
- CRichEditView [MFC], PrintPage
- CRichEditView [MFC], SetCharFormat
- CRichEditView [MFC], SetMargins
- CRichEditView [MFC], SetPaperSize
- CRichEditView [MFC], SetParaFormat
- CRichEditView [MFC], TextNotFound
- CRichEditView [MFC], GetClipboardData
- CRichEditView [MFC], GetContextMenu
- CRichEditView [MFC], IsSelected
- CRichEditView [MFC], OnFindNext
- CRichEditView [MFC], OnInitialUpdate
- CRichEditView [MFC], OnPasteNativeObject
- CRichEditView [MFC], OnPrinterChanged
- CRichEditView [MFC], OnReplaceAll
- CRichEditView [MFC], OnReplaceSel
- CRichEditView [MFC], OnTextNotFound
- CRichEditView [MFC], QueryAcceptData
- CRichEditView [MFC], WrapChanged
- CRichEditView [MFC], m_nBulletIndent
- CRichEditView [MFC], m_nWordWrap
ms.assetid: bd576b10-4cc0-4050-8f76-e1a0548411e4
ms.openlocfilehash: 2d832f3cc07d39ace9e679901c5344a376cea03c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318636"
---
# <a name="cricheditview-class"></a>CRichEditView-Klasse

Mit [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) und [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)bietet die Funktionalität des Rich Edit-Steuerelements im Kontext der MFC-Dokumentansichtsarchitektur.

## <a name="syntax"></a>Syntax

```
class CRichEditView : public CCtrlView
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRichEditView::CRichEditView](#cricheditview)|Erstellt ein `CRichEditView`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CrichEditView::AdjustDialogPosition](#adjustdialogposition)|Verschiebt ein Dialogfeld, damit die aktuelle Auswahl nicht verdeckt wird.|
|[CRichEditView::CanPaste](#canpaste)|Gibt an, ob die Zwischenablage Daten enthält, die in die umfangreiche Bearbeitungsansicht eingefügt werden können.|
|[CRichEditView::DoPaste](#dopaste)|Fügt ein OLE-Element in diese umfangreiche Bearbeitungsansicht ein.|
|[CRichEditView::FindText](#findtext)|Sucht den angegebenen Text und ruft den Wartecursor auf.|
|[CRichEditView::FindTextSimple](#findtextsimple)|Sucht den angegebenen Text.|
|[CrichEditView::GetCharFormatAuswahl](#getcharformatselection)|Ruft die Zeichenformatierungsattribute für die aktuelle Auswahl ab.|
|[CRichEditView::GetDocument](#getdocument)|Ruft einen Zeiger auf das zugehörige [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)ab.|
|[CrichEditView::GetInPlaceActiveItem](#getinplaceactiveitem)|Ruft das OLE-Element ab, das derzeit in der umfangreichen Bearbeitungsansicht aktiv ist.|
|[CRichEditView::GetMargins](#getmargins)|Ruft die Ränder für diese umfangreiche Bearbeitungsansicht ab.|
|[CRichEditView::GetPageRect](#getpagerect)|Ruft das Seitenrechteck für diese umfangreiche Bearbeitungsansicht ab.|
|[CRichEditView::GetPaperSize](#getpapersize)|Ruft das Papierformat für diese umfangreiche Bearbeitungsansicht ab.|
|[CrichEditView::GetParaFormatAuswahl](#getparaformatselection)|Ruft die Absatzformatierungsattribute für die aktuelle Auswahl ab.|
|[CRichEditView::GetPrintRect](#getprintrect)|Ruft das Druckrechteck für diese umfangreiche Bearbeitungsansicht ab.|
|[CRichEditView::GetPrintWidth](#getprintwidth)|Ruft die Druckbreite für diese umfangreiche Bearbeitungsansicht ab.|
|[CRichEditView::GetRichEditCtrl](#getricheditctrl)|Ruft das umfangreiche Bearbeitungssteuerelement ab.|
|[CRichEditView::GetSelectedItem](#getselecteditem)|Ruft das ausgewählte Element aus der umfangreichen Bearbeitungsansicht ab.|
|[CRichEditView::GetTextLength](#gettextlength)|Ruft die Länge des Textes in der rich edit view ab.|
|[CRichEditView::GetTextLengthEx](#gettextlengthex)|Ruft die Anzahl der Zeichen oder Bytes in der Rich-Edit-Ansicht ab. Erweiterte Flagliste für die Methode zur Bestimmung der Länge.|
|[CrichEditView::InsertFileAsObject](#insertfileasobject)|Fügt eine Datei als OLE-Element ein.|
|[CRichEditView::InsertItem](#insertitem)|Fügt ein neues Element als OLE-Element ein.|
|[CRichEditView::IsRichEditFormat](#isricheditformat)|Gibt an, ob die Zwischenablage Daten in einem Rich-Edit- oder Textformat enthält.|
|[CrichEditView::OnCharEffect](#onchareffect)|Schaltet die Zeichenformatierung für die aktuelle Auswahl um.|
|[CrichEditView::OnParaalign](#onparaalign)|Ändert die Ausrichtung von Absätzen.|
|[CrichEditView::OnUpdateCharEffect](#onupdatechareffect)|Aktualisiert die Befehlsbenutzeroberfläche für öffentliche Zeichenmemberfunktionen.|
|[CrichEditView::OnUpdateParaalign](#onupdateparaalign)|Aktualisiert die Befehlsbenutzeroberfläche für öffentliche Absatzmemberfunktionen.|
|[CRichEditView::PrintInsideRect](#printinsiderect)|Formatiert den angegebenen Text innerhalb des angegebenen Rechtecks.|
|[CRichEditView::PrintPage](#printpage)|Formatiert den angegebenen Text innerhalb der angegebenen Seite.|
|[CRichEditView::SetCharFormat](#setcharformat)|Legt die Zeichenformatierungsattribute für die aktuelle Auswahl fest.|
|[CRichEditView::SetMargins](#setmargins)|Legt die Ränder für diese umfangreiche Bearbeitungsansicht fest.|
|[CRichEditView::SetPaperSize](#setpapersize)|Legt das Papierformat für diese umfangreiche Bearbeitungsansicht fest.|
|[CrichEditView::SetParaFormat](#setparaformat)|Legt die Absatzformatierungsattribute für die aktuelle Auswahl fest.|
|[CRichEditView::TextNotFound](#textnotfound)|Setzt den internen Suchstatus des Steuerelements zurück.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRichEditView::GetClipboardData](#getclipboarddata)|Ruft ein Zwischenablageobjekt für einen Bereich in dieser umfangreichen Bearbeitungsansicht ab.|
|[CRichEditView::GetContextMenu](#getcontextmenu)|Ruft ein Kontextmenü ab, das auf einer rechten Maustaste nach unten verwendet werden kann.|
|[CRichEditView::IsSelected](#isselected)|Gibt an, ob das angegebene OLE-Element ausgewählt ist oder nicht.|
|[CrichEditView::OnFindNext](#onfindnext)|Sucht das nächste Vorkommen einer Teilzeichenfolge.|
|[CrichEditView::OnInitialUpdate](#oninitialupdate)|Aktualisiert eine Ansicht, wenn sie zum ersten Mal an ein Dokument angefügt wird.|
|[CrichEditView::OnPasteNativeObject](#onpastenativeobject)|Ruft systemeigene Daten aus einem OLE-Element ab.|
|[CrichEditView::OnPrinterChanged](#onprinterchanged)|Legt die Druckeigenschaften auf das angegebene Gerät fest.|
|[CrichEditView::OnReplaceAll](#onreplaceall)|Ersetzt alle Vorkommen einer bestimmten Zeichenfolge durch eine neue Zeichenfolge.|
|[CrichEditView::OnReplaceSel](#onreplacesel)|Ersetzt die aktuelle Auswahl.|
|[CrichEditView::OnTextNotFound](#ontextnotfound)|Behandelt Benutzerbenachrichtigungen, dass der angeforderte Text nicht gefunden wurde.|
|[CRichEditView::QueryAcceptData](#queryacceptdata)|Abfragen zu den Daten `IDataObject`auf der .|
|[CRichEditView::WrapChanged](#wrapchanged)|Passt das Zielausgabegerät für diese umfangreiche Bearbeitungsansicht `m_nWordWrap`basierend auf dem Wert von an.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRichEditView::m_nBulletIndent](#m_nbulletindent)|Gibt die Einzugsmenge für Aufzählungszeichen an.|
|[CRichEditView::m_nWordWrap](#m_nwordwrap)|Gibt die Wortumbrucheinschränkungen an.|

## <a name="remarks"></a>Bemerkungen

Ein "Rich-Edit-Steuerelement" ist ein Fenster, in dem der Benutzer Text eingeben und bearbeiten kann. Dem Text können Zeichen- und Absatzformatierungen zugewiesen werden und eingebettete OLE-Objekte enthalten sein. Rich-Edit-Steuerelemente bieten eine Programmierschnittstelle zum Formatieren von Text. Eine Anwendung muss jedoch alle Benutzeroberflächenkomponenten implementieren, die erforderlich sind, um formatierungsvorgänge für den Benutzer verfügbar zu machen.

`CRichEditView`behält das Text- und Formatierungsmerkmal des Textes bei. `CRichEditDoc`verwaltet die Liste der OLE-Clientelemente, die sich in der Ansicht befinden. `CRichEditCntrItem`bietet containerseitigen Zugriff auf das OLE-Clientelement.

Dieses Windows Common-Steuerelement (und damit das [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) und verwandte Klassen) ist nur für Programme verfügbar, die unter Windows 95/98 und Windows NT-Versionen 3.51 und höher ausgeführt werden.

Ein Beispiel für die Verwendung einer umfangreichen Bearbeitungsansicht [WORDPAD](../../overview/visual-cpp-samples.md) in einer MFC-Anwendung finden Sie in der WORDPAD-Beispielanwendung.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CRichEditView`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxrich.h

## <a name="cricheditviewadjustdialogposition"></a><a name="adjustdialogposition"></a>CrichEditView::AdjustDialogPosition

Rufen Sie diese Funktion auf, um das angegebene Dialogfeld so zu verschieben, dass die aktuelle Auswahl nicht verdeckt wird.

```
void AdjustDialogPosition(CDialog* pDlg);
```

### <a name="parameters"></a>Parameter

*pDlg*<br/>
Zeiger auf `CDialog` ein Objekt.

## <a name="cricheditviewcanpaste"></a><a name="canpaste"></a>CRichEditView::CanPaste

Rufen Sie diese Funktion auf, um zu ermitteln, ob die Zwischenablage Informationen enthält, die in diese umfangreiche Bearbeitungsansicht eingefügt werden können.

```
BOOL CanPaste() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Zwischenablage Daten in einem Format enthält, das diese umfangreiche Bearbeitungsansicht akzeptieren kann. andernfalls 0.

## <a name="cricheditviewcricheditview"></a><a name="cricheditview"></a>CRichEditView::CRichEditView

Rufen Sie diese `CRichEditView` Funktion auf, um ein Objekt zu erstellen.

```
CRichEditView();
```

## <a name="cricheditviewdopaste"></a><a name="dopaste"></a>CRichEditView::DoPaste

Rufen Sie diese Funktion auf, um das OLE-Element in *dataobj* in dieses umfangreiche Bearbeitungsdokument/diese umfassende Bearbeitungsdokument/-ansicht einzufügen.

```
void DoPaste(
    COleDataObject& dataobj,
    CLIPFORMAT cf,
    HMETAFILEPICT hMetaPict);
```

### <a name="parameters"></a>Parameter

*dataobj*<br/>
Das [COleDataObject,](../../mfc/reference/coledataobject-class.md) das die einzufügenden Daten enthält.

*Cf*<br/>
Das gewünschte Zwischenablageformat.

*hMetaPict*<br/>
Die Metadatei, die das eingefügte Element darstellt.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Funktion als Teil der Standardimplementierung von [QueryAcceptData](#queryacceptdata)auf.

Diese Funktion bestimmt den Typ der Paste basierend auf den Ergebnissen des Handlers für Paste Special. Wenn *cf* 0 ist, verwendet das neue Element die aktuelle ikonische Darstellung. Wenn *cf* ungleich Null und *hMetaPict* nicht NULL ist, verwendet das neue Element *hMetaPict* für seine Darstellung.

## <a name="cricheditviewfindtext"></a><a name="findtext"></a>CRichEditView::FindText

Rufen Sie diese Funktion auf, um den angegebenen Text zu finden, und legen Sie ihn auf die aktuelle Auswahl fest.

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>Parameter

*lpszFind*<br/>
Enthält die Zeichenfolge, nach der gesucht werden soll.

*bCase*<br/>
Gibt an, ob bei der Suche die Groß-/Kleinschreibung beachtet wird.

*bWord*<br/>
Gibt an, ob die Suche nur mit ganzen Wörtern und nicht mit Teilen von Wörtern übereinstimmen soll.

*bNext*<br/>
Gibt die Richtung der Suche an. Wenn TRUE, befindet sich die Suchrichtung am Ende des Puffers. Wenn FALSE, ist die Suchrichtung zum Anfang des Puffers.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der *text lpszFind* gefunden wird; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion zeigt den Wartecursor während des Suchvorgangs an.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#151](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]

## <a name="cricheditviewfindtextsimple"></a><a name="findtextsimple"></a>CRichEditView::FindTextSimple

Rufen Sie diese Funktion auf, um den angegebenen Text zu finden, und legen Sie ihn auf die aktuelle Auswahl fest.

```
BOOL FindTextSimple(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>Parameter

*lpszFind*<br/>
Enthält die Zeichenfolge, nach der gesucht werden soll.

*bCase*<br/>
Gibt an, ob bei der Suche die Groß-/Kleinschreibung beachtet wird.

*bWord*<br/>
Gibt an, ob die Suche nur mit ganzen Wörtern und nicht mit Teilen von Wörtern übereinstimmen soll.

*bNext*<br/>
Gibt die Richtung der Suche an. Wenn TRUE, befindet sich die Suchrichtung am Ende des Puffers. Wenn FALSE, ist die Suchrichtung zum Anfang des Puffers.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der *text lpszFind* gefunden wird; andernfalls 0.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CRichEditView::FindText](#findtext).

## <a name="cricheditviewgetcharformatselection"></a><a name="getcharformatselection"></a>CrichEditView::GetCharFormatAuswahl

Rufen Sie diese Funktion auf, um die Zeichenformatierungsattribute der aktuellen Auswahl abzurufen.

```
CHARFORMAT2& GetCharFormatSelection();
```

### <a name="return-value"></a>Rückgabewert

Eine [CHARFORMAT2-Struktur,](/windows/win32/api/richedit/ns-richedit-charformat2w) die die Zeichenformatierungsattribute der aktuellen Auswahl enthält.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie in der [EM_GETCHARFORMAT-Meldung](/windows/win32/Controls/em-getcharformat) und der [CHARFORMAT2-Struktur](/windows/win32/api/richedit/ns-richedit-charformat2w) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

## <a name="cricheditviewgetclipboarddata"></a><a name="getclipboarddata"></a>CRichEditView::GetClipboardData

Das Framework ruft diese Funktion als Teil der Verarbeitung von [IRichEditOleCallback::GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata)auf.

```
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,
    DWORD dwReco,
    LPDATAOBJECT lpRichDataObj,
    LPDATAOBJECT* lplpdataobj);
```

### <a name="parameters"></a>Parameter

*lpchrg*<br/>
Zeiger auf die [CHARRANGE-Struktur,](/windows/win32/api/richedit/ns-richedit-charrange) die den Zeichenbereich (und DIE OLE-Elemente) angibt, die in das von *lplpdataobj*angegebene Datenobjekt kopiert werden sollen.

*dwReco*<br/>
Zwischenablage-Betriebsflag. Kann einer dieser Werte sein.

- RECO_COPY In die Zwischenablage kopieren.

- RECO_CUT Schnitt in die Zwischenablage.

- RECO_DRAG Drag-Vorgang (Drag and Drop).

- RECO_DROP Drop-Vorgang (Drag and Drop).

- RECO_PASTE Aus der Zwischenablage einfügen.

*lpRichDataObj*<br/>
Zeiger auf ein [IDataObject-Objekt,](/windows/win32/api/objidl/nn-objidl-idataobject) das die Zwischenablagedaten aus dem Rich Edit-Steuerelement ( [IRichEditOle::GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata)) enthält

*lplpdataobj*<br/>
Zeiger auf die Zeigervariable, die die `IDataObject` Adresse des Objekts empfängt, das den im *Lpchrg-Parameter* angegebenen Bereich darstellt. Der Wert von *lplpdataobj* wird ignoriert, wenn ein Fehler zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Wert, der den Erfolg des Vorgangs meldet. Weitere Informationen zu HRESULT finden Sie unter [Struktur von COM-Fehlercodes](/windows/win32/com/structure-of-com-error-codes) im Windows SDK.

### <a name="remarks"></a>Bemerkungen

Wenn der Rückgabewert `IRichEditOleCallback::GetClipboardData` auf `IDataObject` Erfolg hinweist, wird der Zugriff von *lplpdataobj*zurückgegeben. Andernfalls wird der von *lpRichDataObj*aufgerufene zurückgegeben. Überschreiben Sie diese Funktion, um Ihre eigenen Zwischenablagedaten einzugeben. Die Standardimplementierung dieser Funktion gibt E_NOTIMPL zurück.

Dies ist ein fortgeschrittenes Überridable.

Weitere Informationen finden Sie unter [IRichEditOle::GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata), [IRichEditOleCallback::GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata)und [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) im Windows SDK und siehe [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) im Windows SDK.

## <a name="cricheditviewgetcontextmenu"></a><a name="getcontextmenu"></a>CRichEditView::GetContextMenu

Das Framework ruft diese Funktion als Teil der Verarbeitung von [IRichEditOleCallback::GetContextMenu](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu)auf.

```
virtual HMENU GetContextMenu(
    WORD seltyp,
    LPOLEOBJECT lpoleobj,
    CHARRANGE* lpchrg);
```

### <a name="parameters"></a>Parameter

*seltyp*<br/>
Der Auswahltyp. Die Auswahltypwerte werden im Abschnitt "Bemerkungen" beschrieben.

*lpoleobj*<br/>
Zeigen Sie `OLEOBJECT` auf eine Struktur, die das erste ausgewählte OLE-Objekt angibt, wenn die Auswahl ein oder mehrere OLE-Elemente enthält. Wenn die Auswahl keine Elemente enthält, ist *lpoleobj* NULL. Die `OLEOBJECT` Struktur enthält einen Zeiger auf eine OLE-Objekt-V-Tabelle.

*lpchrg*<br/>
Zeiger auf eine [CHARRANGE-Struktur,](/windows/win32/api/richedit/ns-richedit-charrange) die die aktuelle Auswahl enthält.

### <a name="return-value"></a>Rückgabewert

Handle für das Kontextmenü.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist ein typischer Teil der Rechten-Maus-Taste-Down-Verarbeitung.

Der Auswahltyp kann eine beliebige Kombination der folgenden Flags sein:

- SEL_EMPTY Gibt an, dass keine aktuelle Auswahl vorhanden ist.

- SEL_TEXT Gibt an, dass die aktuelle Auswahl Text enthält.

- SEL_OBJECT Gibt an, dass die aktuelle Auswahl mindestens ein OLE-Element enthält.

- SEL_MULTICHAR Gibt an, dass die aktuelle Auswahl mehr als ein Zeichen Text enthält.

- SEL_MULTIOBJECT Gibt an, dass die aktuelle Auswahl mehr als ein OLE-Objekt enthält.

Die Standardimplementierung gibt NULL zurück. Dies ist ein fortgeschrittenes Überridable.

Weitere Informationen finden Sie unter [IRichEditOleCallback::GetContextMenu](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu) und [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) im Windows SDK.

## <a name="cricheditviewgetdocument"></a><a name="getdocument"></a>CRichEditView::GetDocument

Rufen Sie diese Funktion auf, `CRichEditDoc` um einen Zeiger auf die zugeordnete Ansicht abzurufen.

```
CRichEditDoc* GetDocument() const;
```

### <a name="return-value"></a>Rückgabewert

Zeigen Sie auf ein [CRichEditDoc-Objekt,](../../mfc/reference/cricheditdoc-class.md) das Ihrem `CRichEditView` Objekt zugeordnet ist.

## <a name="cricheditviewgetinplaceactiveitem"></a><a name="getinplaceactiveitem"></a>CrichEditView::GetInPlaceActiveItem

Rufen Sie diese Funktion auf, um das OLE-Element abzurufen, das derzeit in diesem `CRichEditView` Objekt aktiviert ist.

```
CRichEditCntrItem* GetInPlaceActiveItem() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das einzelne, an Ort und Stelle aktive [CRichEditCntrItem-Objekt](../../mfc/reference/cricheditcntritem-class.md) in dieser umfangreichen Bearbeitungsansicht; NULL, wenn sich derzeit kein OLE-Element im aktiven Zustand befindet.

## <a name="cricheditviewgetmargins"></a><a name="getmargins"></a>CRichEditView::GetMargins

Rufen Sie diese Funktion auf, um die aktuellen Ränder abzurufen, die beim Drucken verwendet werden.

```
CRect GetMargins() const;
```

### <a name="return-value"></a>Rückgabewert

Die im Druck verwendeten Ränder, gemessen in MM_TWIPS.

## <a name="cricheditviewgetpagerect"></a><a name="getpagerect"></a>CRichEditView::GetPageRect

Rufen Sie diese Funktion auf, um die Dimensionen der Seite abzurufen, die beim Drucken verwendet wird.

```
CRect GetPageRect() const;
```

### <a name="return-value"></a>Rückgabewert

Die Grenzen der Seite, die beim Drucken verwendet wird, gemessen in MM_TWIPS.

### <a name="remarks"></a>Bemerkungen

Dieser Wert basiert auf dem Papierformat.

## <a name="cricheditviewgetpapersize"></a><a name="getpapersize"></a>CRichEditView::GetPaperSize

Rufen Sie diese Funktion auf, um das aktuelle Papierformat abzurufen.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Größe des papiers, das beim Drucken verwendet wird, gemessen in MM_TWIPS.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]

## <a name="cricheditviewgetparaformatselection"></a><a name="getparaformatselection"></a>CrichEditView::GetParaFormatAuswahl

Rufen Sie diese Funktion auf, um die Absatzformatierungsattribute der aktuellen Auswahl abzurufen.

```
PARAFORMAT2& GetParaFormatSelection();
```

### <a name="return-value"></a>Rückgabewert

Eine [PARAFORMAT2-Struktur,](/windows/win32/api/richedit/ns-richedit-paraformat2) die die Absatzformatierungsattribute der aktuellen Auswahl enthält.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie [unter EM_GETPARAFORMAT](/windows/win32/Controls/em-getparaformat) Nachricht und [paraFORMAT2-Struktur](/windows/win32/api/richedit/ns-richedit-paraformat2) im Windows SDK.

## <a name="cricheditviewgetprintrect"></a><a name="getprintrect"></a>CRichEditView::GetPrintRect

Rufen Sie diese Funktion auf, um die Grenzen des Druckbereichs innerhalb des Seitenrechtecks abzurufen.

```
CRect GetPrintRect() const;
```

### <a name="return-value"></a>Rückgabewert

Die Grenzen des beim Drucken verwendeten Bildbereichs, gemessen in MM_TWIPS.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]

## <a name="cricheditviewgetprintwidth"></a><a name="getprintwidth"></a>CRichEditView::GetPrintWidth

Rufen Sie diese Funktion auf, um die Breite des Druckbereichs zu bestimmen.

```
int GetPrintWidth() const;
```

### <a name="return-value"></a>Rückgabewert

Die Breite des Druckbereichs, gemessen in MM_TWIPS.

## <a name="cricheditviewgetricheditctrl"></a><a name="getricheditctrl"></a>CRichEditView::GetRichEditCtrl

Rufen Sie diese Funktion auf, um das `CRichEditView` dem Objekt zugeordnete [CRichEditCtrl-Objekt](../../mfc/reference/cricheditctrl-class.md) abzurufen.

```
CRichEditCtrl& GetRichEditCtrl() const;
```

### <a name="return-value"></a>Rückgabewert

Das `CRichEditCtrl` Objekt für diese Ansicht.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CRichEditView::FindText](#findtext).

## <a name="cricheditviewgetselecteditem"></a><a name="getselecteditem"></a>CRichEditView::GetSelectedItem

Rufen Sie diese Funktion auf, `CRichEditCntrItem` um das OLE-Element (ein Objekt) abzurufen, das derzeit in diesem `CRichEditView` Objekt ausgewählt ist.

```
CRichEditCntrItem* GetSelectedItem() const;
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf ein [CRichEditCntrItem-Objekt,](../../mfc/reference/cricheditcntritem-class.md) das `CRichEditView` im Objekt ausgewählt ist; NULL, wenn in dieser Ansicht kein Element ausgewählt ist.

## <a name="cricheditviewgettextlength"></a><a name="gettextlength"></a>CRichEditView::GetTextLength

Rufen Sie diese Funktion auf, um `CRichEditView` die Länge des Textes in diesem Objekt abzurufen.

```
long GetTextLength() const;
```

### <a name="return-value"></a>Rückgabewert

Die Länge des Textes in diesem `CRichEditView` Objekt.

## <a name="cricheditviewgettextlengthex"></a><a name="gettextlengthex"></a>CRichEditView::GetTextLengthEx

Rufen Sie diese Memberfunktion auf, um `CRichEditView` die Länge des Textes in diesem Objekt zu berechnen.

```
long GetTextLengthEx(
    DWORD dwFlags,
    UINT uCodePage = -1) const;
```

### <a name="parameters"></a>Parameter

*dwFlags*<br/>
Wert, der die Methode angibt, die zum Bestimmen der Textlänge verwendet werden soll. Bei diesem Member kann es sich um einen oder mehrere der im Flags-Member von [GETTEXTLENGTHEX](/windows/win32/api/richedit/ns-richedit-gettextlengthex) beschriebenen Werte handeln.

*uCodePage*<br/>
Codepage für Übersetzung (CP_ACP für ANSI Code Page, 1200 für Unicode).

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Zeichen oder Bytes im Bearbeitungssteuerelement. Wenn inkompatible Flags in *dwFlags*festgelegt wurden, gibt diese Memberfunktion E_INVALIDARG zurück.

### <a name="remarks"></a>Bemerkungen

`GetTextLengthEx`bietet zusätzliche Möglichkeiten, die Länge des Textes zu bestimmen. Es unterstützt die Rich Edit 2.0-Funktionalität. Weitere Informationen finden Sie unter Weitere Informationen zu [Rich Edit Controls](/windows/win32/Controls/about-rich-edit-controls) im Windows SDK.

## <a name="cricheditviewinsertfileasobject"></a><a name="insertfileasobject"></a>CrichEditView::InsertFileAsObject

Rufen Sie diese Funktion auf, um die angegebene Datei (als [CRichEditCntrItem-Objekt)](../../mfc/reference/cricheditcntritem-class.md) in eine umfangreiche Bearbeitungsansicht einzufügen.

```
void InsertFileAsObject(LPCTSTR lpszFileName);
```

### <a name="parameters"></a>Parameter

*lpszFileName*<br/>
Zeichenfolge, die den Namen der einzufügenden Datei enthält.

## <a name="cricheditviewinsertitem"></a><a name="insertitem"></a>CRichEditView::InsertItem

Rufen Sie diese Funktion auf, um ein [CRichEditCntrItem-Objekt](../../mfc/reference/cricheditcntritem-class.md) in eine umfangreiche Bearbeitungsansicht einzufügen.

```
HRESULT InsertItem(CRichEditCntrItem* pItem);
```

### <a name="parameters"></a>Parameter

*pItem*<br/>
Zeigen Sie mit dem Zeiger auf das element, das eingefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Wert, der den Erfolg der Einfügung angibt.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu HRESULT finden Sie unter [Struktur von COM-Fehlercodes](/windows/win32/com/structure-of-com-error-codes) im Windows SDK.

## <a name="cricheditviewisricheditformat"></a><a name="isricheditformat"></a>CRichEditView::IsRichEditFormat

Rufen Sie diese Funktion auf, um zu bestimmen, ob *cf* ein Zwischenablageformat ist, das Text, Rich Text oder Rich-Text mit OLE-Elementen ist.

```
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```

### <a name="parameters"></a>Parameter

*Cf*<br/>
Das Clipboard-Format von Interesse.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn *cf* ein Rich-Edit- oder Text-Zwischenablageformat ist.

## <a name="cricheditviewisselected"></a><a name="isselected"></a>CRichEditView::IsSelected

Rufen Sie diese Funktion auf, um zu ermitteln, ob das angegebene OLE-Element derzeit in dieser Ansicht ausgewählt ist.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Parameter

*pDocItem*<br/>
Zeiger auf ein Objekt in der Ansicht.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Objekt ausgewählt ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, wenn die abgeleitete Ansichtsklasse über eine andere Methode zum Behandeln der Auswahl von OLE-Elementen verfügt.

## <a name="cricheditviewm_nbulletindent"></a><a name="m_nbulletindent"></a>CRichEditView::m_nBulletIndent

Der Einzug für Aufzählungszeichen in einer Liste; standardmäßig 720 Einheiten, was 1/2 Zoll entspricht.

```
int m_nBulletIndent;
```

## <a name="cricheditviewm_nwordwrap"></a><a name="m_nwordwrap"></a>CRichEditView::m_nWordWrap

Gibt den Typ des Wortumbruchs für diese umfangreiche Bearbeitungsansicht an.

```
int m_nWordWrap;
```

### <a name="remarks"></a>Bemerkungen

Einer der folgenden Werte:

- `WrapNone`Gibt keinen automatischen Wortumbruch an.

- `WrapToWindow`Gibt den Wortumbruch basierend auf der Breite des Fensters an.

- `WrapToTargetDevice`Gibt den Wortumbruch basierend auf den Eigenschaften des Zielgeräts an.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CRichEditView::WrapChanged](#wrapchanged).

## <a name="cricheditviewonchareffect"></a><a name="onchareffect"></a>CrichEditView::OnCharEffect

Rufen Sie diese Funktion auf, um die Zeichenformatierungseffekte für die aktuelle Auswahl umzuschalten.

```
void OnCharEffect(
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Parameter

*dwMask*<br/>
Die Zeichenformatierungseffekte, die in der aktuellen Auswahl geändert werden sollen.

*dwEffect*<br/>
Die gewünschte Liste der zum Umschalten umzuschaltenden Zeichenformatierungseffekte.

### <a name="remarks"></a>Bemerkungen

Bei jedem Aufruf dieser Funktion werden die angegebenen Formatierungseffekte für die aktuelle Auswahl umgeschaltet.

Weitere Informationen zu den Parametern *dwMask* und *dwEffect* und deren potenziellen Werten finden Sie in den entsprechenden Datenmembern von [CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#155](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]

## <a name="cricheditviewonfindnext"></a><a name="onfindnext"></a>CrichEditView::OnFindNext

Wird vom Framework aufgerufen, wenn Befehle aus dem Dialogfeld Suchen/Ersetzen verarbeitet werden.

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>Parameter

*lpszFind*<br/>
Die zu suchende Zeichenfolge.

*bNext*<br/>
Die zu durchsuchende Richtung: TRUE zeigt nach unten an; FALSE, oben.

*bCase*<br/>
Gibt an, ob bei der Suche die Groß-/Kleinschreibung beachtet werden soll.

*bWord*<br/>
Gibt an, ob die Suche nur mit ganzen Wörtern übereinstimmen soll oder nicht.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion `CRichEditView`auf, um Text innerhalb der zu finden. Überschreiben Sie diese Funktion, um die Sucheigenschaften für die abgeleitete Ansichtsklasse zu ändern.

## <a name="cricheditviewoninitialupdate"></a><a name="oninitialupdate"></a>CrichEditView::OnInitialUpdate

Wird vom Framework aufgerufen, nachdem die Ansicht zuerst an das Dokument angefügt wurde, aber bevor die Ansicht zuerst angezeigt wird.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung dieser Funktion ruft die [CView::OnUpdate-Memberfunktion](../../mfc/reference/cview-class.md#onupdate) ohne Hinweisinformationen auf (d. h. die Standardwerte 0 für den *Parameter lHint* und NULL für den *pHint-Parameter).* Überschreiben Sie diese Funktion, um eine einmalige Initialisierung durchzuführen, die Informationen über das Dokument erfordert. Wenn Ihre Anwendung beispielsweise Dokumente mit fester Größe enthält, können Sie diese Funktion verwenden, um die Bildlauflimits einer Ansicht basierend auf der Dokumentgröße zu initialisieren. Wenn Ihre Anwendung Dokumente im `OnUpdate` variablen Format unterstützt, aktualisieren Sie die Bildlauflimits bei jeder Änderung des Dokuments.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CRichEditView::m_nWordWrap](#m_nwordwrap).

## <a name="cricheditviewonpastenativeobject"></a><a name="onpastenativeobject"></a>CrichEditView::OnPasteNativeObject

Verwenden Sie diese Funktion, um systemeigene Daten aus einem eingebetteten Element zu laden.

```
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```

### <a name="parameters"></a>Parameter

*lpStg*<br/>
Zeiger auf ein [IStorage-Objekt.](/windows/win32/api/objidl/nn-objidl-istorage)

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich; andernfalls 0;

### <a name="remarks"></a>Bemerkungen

In der Regel würden Sie dies tun, `IStorage`indem Sie eine [COleStreamFile](../../mfc/reference/colestreamfile-class.md) um die erstellen. Der `COleStreamFile` kann an ein Archiv angefügt werden und [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) wird aufgerufen, um die Daten zu laden.

Dies ist ein fortgeschrittenes Überridable.

Weitere Informationen finden Sie unter [IStorage](/windows/win32/api/objidl/nn-objidl-istorage) im Windows SDK.

## <a name="cricheditviewonparaalign"></a><a name="onparaalign"></a>CrichEditView::OnParaalign

Rufen Sie diese Funktion auf, um die Absatzausrichtung für die ausgewählten Absätze zu ändern.

```
void OnParaAlign(WORD wAlign);
```

### <a name="parameters"></a>Parameter

*wAlign*<br/>
Gewünschte Absatzausrichtung. Einer der folgenden Werte:

- PFA_LEFT Richten Sie die Absätze am linken Rand aus.

- PFA_RIGHT Richten Sie die Absätze am rechten Rand aus.

- PFA_CENTER zentrieren Sie die Absätze zwischen den Rändern.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]

## <a name="cricheditviewonprinterchanged"></a><a name="onprinterchanged"></a>CrichEditView::OnPrinterChanged

Überschreiben Sie diese Funktion, um die Merkmale für diese umfangreiche Bearbeitungsansicht zu ändern, wenn sich der Drucker ändert.

```
virtual void OnPrinterChanged(const CDC& dcPrinter);
```

### <a name="parameters"></a>Parameter

*dcPrinter*<br/>
Ein [CDC-Objekt](../../mfc/reference/cdc-class.md) für den neuen Drucker.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung legt das Papierformat auf die physische Höhe und Breite des Ausgabegeräts (Drucker) fest. Wenn *dcPrinter*kein Gerätekontext zugeordnet ist, legt die Standardimplementierung das Papierformat auf 8,5 x 11 Zoll fest.

## <a name="cricheditviewonreplaceall"></a><a name="onreplaceall"></a>CrichEditView::OnReplaceAll

Wird vom Framework bei der Verarbeitung Alle Befehle ersetzen aus dem Dialogfeld Ersetzen aufgerufen.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>Parameter

*lpszFind*<br/>
Der zu ersetzende Text.

*lpszReplace*<br/>
Der Ersatztext.

*bCase*<br/>
Gibt an, ob bei der Suche die Groß-/Kleinschreibung beachtet wird.

*bWord*<br/>
Gibt an, ob die Suche ganze Wörter auswählen muss oder nicht.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um alle Vorkommen eines bestimmten Textes durch eine andere Zeichenfolge zu ersetzen. Überschreiben Sie diese Funktion, um die Sucheigenschaften für diese Ansicht zu ändern.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CRichEditView::FindText](#findtext).

## <a name="cricheditviewonreplacesel"></a><a name="onreplacesel"></a>CrichEditView::OnReplaceSel

Wird vom Framework bei der Verarbeitung Ersetzen von Befehlen aus dem Dialogfeld Ersetzen aufgerufen.

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>Parameter

*lpszFind*<br/>
Der zu ersetzende Text.

*bNext*<br/>
Gibt die Richtung der Suche an: TRUE ist unten; FALSE, oben.

*bCase*<br/>
Gibt an, ob bei der Suche die Groß-/Kleinschreibung beachtet wird.

*bWord*<br/>
Gibt an, ob die Suche ganze Wörter auswählen muss oder nicht.

*lpszReplace*<br/>
Der Ersatztext.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um ein Vorkommen eines bestimmten Textes durch eine andere Zeichenfolge zu ersetzen. Überschreiben Sie diese Funktion, um die Sucheigenschaften für diese Ansicht zu ändern.

## <a name="cricheditviewontextnotfound"></a><a name="ontextnotfound"></a>CrichEditView::OnTextNotFound

Wird vom Framework aufgerufen, wenn eine Suche fehlschlägt.

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parameter

*lpszFind*<br/>
Der Text, der nicht gefunden wurde.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um die Ausgabebenachrichtigung von einem [MessageBeep](/windows/win32/api/winuser/nf-winuser-messagebeep)zu ändern.

Weitere Informationen finden Sie unter [MessageBeep](/windows/win32/api/winuser/nf-winuser-messagebeep) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#157](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]

## <a name="cricheditviewonupdatechareffect"></a><a name="onupdatechareffect"></a>CrichEditView::OnUpdateCharEffect

Das Framework ruft diese Funktion auf, um die Befehlsbenutzeroberfläche für Zeicheneffektbefehle zu aktualisieren.

```
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Parameter

*pCmdUI*<br/>
Zeiger auf ein [CCmdUI-Objekt.](../../mfc/reference/ccmdui-class.md)

*dwMask*<br/>
Gibt die Zeichenformatierungsmaske an.

*dwEffect*<br/>
Gibt den Zeichenformatierungseffekt an.

### <a name="remarks"></a>Bemerkungen

Die Maske *dwMask* gibt an, welche Zeichenformatierungsattribute überprüft werden sollen. Die Flags *dwEffect* listen die Zeichenformatierungsattribute auf, die festgelegt/löschen sollen.

Weitere Informationen zu den Parametern *dwMask* und *dwEffect* und deren potenziellen Werten finden Sie in den entsprechenden Datenmembern von [CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]

## <a name="cricheditviewonupdateparaalign"></a><a name="onupdateparaalign"></a>CrichEditView::OnUpdateParaalign

Das Framework ruft diese Funktion auf, um die Befehlsbenutzeroberfläche für Absatzeffektbefehle zu aktualisieren.

```
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,
    WORD wAlign);
```

### <a name="parameters"></a>Parameter

*pCmdUI*<br/>
Zeiger auf ein [CCmdUI-Objekt.](../../mfc/reference/ccmdui-class.md)

*wAlign*<br/>
Die zu überprüfende Absatzausrichtung. Einer der folgenden Werte:

- PFA_LEFT Richten Sie die Absätze am linken Rand aus.

- PFA_RIGHT Richten Sie die Absätze am rechten Rand aus.

- PFA_CENTER zentrieren Sie die Absätze zwischen den Rändern.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]

## <a name="cricheditviewprintinsiderect"></a><a name="printinsiderect"></a>CRichEditView::PrintInsideRect

Rufen Sie diese Funktion auf, um einen Textbereich in einem Rich-Edit-Steuerelement so zu formatieren, dass er in *rectLayout* für das von *pDC*angegebene Gerät passt.

```
long PrintInsideRect(
    CDC* pDC,
    RECT& rectLayout,
    long nIndexStart,
    long nIndexStop,
    BOOL bOutput);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Zeiger auf einen Gerätekontext für den Ausgabebereich.

*rectLayout*<br/>
[RECT](/windows/win32/api/windef/ns-windef-rect) oder [CRect,](../../atl-mfc-shared/reference/crect-class.md) das den Ausgabebereich definiert.

*nIndexStart*<br/>
Nullbasierter Index des ersten zu formatierenden Zeichens.

*nIndexStop*<br/>
Nullbasierter Index des letzten zu formatierenden Zeichens.

*bOutput*<br/>
Gibt an, ob der Text gerendert werden soll. Wenn FALSE, wird der Text nur gemessen.

### <a name="return-value"></a>Rückgabewert

Der Index des letzten Zeichens, das in den Ausgabebereich plus eins passt.

### <a name="remarks"></a>Bemerkungen

In der Regel folgt auf diesen Aufruf ein Aufruf von [CRichEditCtrl::DisplayBand,](../../mfc/reference/cricheditctrl-class.md#displayband) das die Ausgabe generiert.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CRichEditView::GetPaperSize](#getpapersize).

## <a name="cricheditviewprintpage"></a><a name="printpage"></a>CRichEditView::PrintPage

Rufen Sie diese Funktion auf, um einen Textbereich in einem Rich-Edit-Steuerelement für das von *pDC*angegebene Ausgabegerät zu formatieren.

```
long PrintPage(
    CDC* pDC,
    long nIndexStart,
    long nIndexStop);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Zeiger auf einen Gerätekontext für die Seitenausgabe.

*nIndexStart*<br/>
Nullbasierter Index des ersten zu formatierenden Zeichens.

*nIndexStop*<br/>
Nullbasierter Index des letzten zu formatierenden Zeichens.

### <a name="return-value"></a>Rückgabewert

Der Index des letzten Zeichens, das auf die Seite plus eins passt.

### <a name="remarks"></a>Bemerkungen

Das Layout jeder Seite wird von [GetPageRect](#getpagerect) und [GetPrintRect](#getprintrect)gesteuert. In der Regel folgt auf diesen Aufruf ein Aufruf von [CRichEditCtrl::DisplayBand,](../../mfc/reference/cricheditctrl-class.md#displayband) das die Ausgabe generiert.

Beachten Sie, dass ränder relativ zur physischen Seite und nicht zur logischen Seite sind. Daher wird der Text häufig mit Null abgeschnitten, da viele Drucker nicht druckbare Bereiche auf der Seite haben. Um das Zuschneiden von Text zu vermeiden, sollten Sie [SetMargins](#setmargins) aufrufen und vor dem Drucken angemessene Ränder festlegen.

## <a name="cricheditviewqueryacceptdata"></a><a name="queryacceptdata"></a>CRichEditView::QueryAcceptData

Wird vom Framework aufgerufen, um ein Objekt in die Rich-Bearbeitung einzufügen.

```
virtual HRESULT QueryAcceptData(
    LPDATAOBJECT lpdataobj,
    CLIPFORMAT* lpcfFormat,
    DWORD dwReco,
    BOOL bReally,
    HGLOBAL hMetaFile);
```

### <a name="parameters"></a>Parameter

*lpdataobj*<br/>
Zeiger auf das zu abfragende [IDataObject.](/windows/win32/api/objidl/nn-objidl-idataobject)

*lpcfFormat*<br/>
Zeiger auf das akzeptable Datenformat.

*dwReco*<br/>
Wird nicht verwendet.

*bReally*<br/>
Gibt an, ob der Einfügevorgang fortgesetzt werden soll oder nicht.

*hMetaFile*<br/>
Ein Handle für die Metadatei, die zum Zeichnen des Elementsymbols verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Wert, der den Erfolg des Vorgangs meldet.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um verschiedene Organisationen von COM-Elementen in der abgeleiteten Dokumentklasse zu behandeln. Dies ist ein fortgeschrittenes Überridable.

Weitere Informationen zu HRESULT und `IDataObject`, siehe Struktur von [COM-Fehlercodes](/windows/win32/com/structure-of-com-error-codes) bzw. [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]

## <a name="cricheditviewsetcharformat"></a><a name="setcharformat"></a>CRichEditView::SetCharFormat

Rufen Sie diese Funktion auf, um die `CRichEditView` Zeichenformatierungsattribute für neuen Text in diesem Objekt festzulegen.

```
void SetCharFormat(CHARFORMAT2 cf);
```

### <a name="parameters"></a>Parameter

*Cf*<br/>
[CHARFORMAT2-Struktur,](/windows/win32/api/richedit/ns-richedit-charformat2w) die die neuen Standardzeichenformatierungsattribute enthält.

### <a name="remarks"></a>Bemerkungen

Nur die vom `dwMask` Cf-Member-Element angegebenen Attribute werden durch diese Funktion geändert. *cf*

Weitere Informationen finden Sie [unter EM_SETCHARFORMAT](/windows/win32/Controls/em-setcharformat) Nachricht und [charFORMAT2-Struktur](/windows/win32/api/richedit/ns-richedit-charformat2w) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

## <a name="cricheditviewsetmargins"></a><a name="setmargins"></a>CRichEditView::SetMargins

Rufen Sie diese Funktion auf, um die Druckränder für diese umfangreiche Bearbeitungsansicht festzulegen.

```
void SetMargins(const CRect& rectMargin);
```

### <a name="parameters"></a>Parameter

*rectMargin*<br/>
Die neuen Randwerte für den Druck, gemessen in MM_TWIPS.

### <a name="remarks"></a>Bemerkungen

Wenn [m_nWordWrap](#m_nwordwrap) m_nWordWrap `WrapToTargetDevice`ist , sollten Sie [WrapChanged](#wrapchanged) aufrufen, nachdem Sie diese Funktion verwendet haben, um die Druckeigenschaften anzupassen.

Beachten Sie, dass die von [PrintPage](#printpage) verwendeten Ränder relativ zur physischen Seite und nicht zur logischen Seite sind. Daher wird der Text häufig mit Null abgeschnitten, da viele Drucker nicht druckbare Bereiche auf der Seite haben. Um das Zuschneiden von Text `SetMargins` zu vermeiden, sollten Sie vor dem Drucken die Verwendung aufrufen, um angemessene Druckerränder festzulegen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CRichEditView::GetPaperSize](#getpapersize).

## <a name="cricheditviewsetpapersize"></a><a name="setpapersize"></a>CRichEditView::SetPaperSize

Rufen Sie diese Funktion auf, um das Papierformat für das Drucken dieser umfangreichen Bearbeitungsansicht festzulegen.

```
void SetPaperSize(CSize sizePaper);
```

### <a name="parameters"></a>Parameter

*sizePapier*<br/>
Die neuen Papierformatwerte für den Druck, gemessen in MM_TWIPS.

### <a name="remarks"></a>Bemerkungen

Wenn [m_nWordWrap](#m_nwordwrap) m_nWordWrap `WrapToTargetDevice`ist , sollten Sie [WrapChanged](#wrapchanged) aufrufen, nachdem Sie diese Funktion verwendet haben, um die Druckeigenschaften anzupassen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]

## <a name="cricheditviewsetparaformat"></a><a name="setparaformat"></a>CrichEditView::SetParaFormat

Rufen Sie diese Funktion auf, um die Absatzformatierungsattribute für die aktuelle Auswahl in diesem `CRichEditView` Objekt festzulegen.

```
BOOL SetParaFormat(PARAFORMAT2& pf);
```

### <a name="parameters"></a>Parameter

*Pf*<br/>
[PARAFORMAT2-Struktur,](/windows/win32/api/richedit/ns-richedit-paraformat2) die die neuen Standardattributformatierungsattribute enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn erfolgreich, andernfalls 0 (null).

### <a name="remarks"></a>Bemerkungen

Nur die vom `dwMask` Element *pf* angegebenen Attribute werden durch diese Funktion geändert.

Weitere Informationen finden Sie [unter EM_SETPARAFORMAT](/windows/win32/Controls/em-setparaformat) Nachricht und [paraFORMAT2-Struktur](/windows/win32/api/richedit/ns-richedit-paraformat2) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]

## <a name="cricheditviewtextnotfound"></a><a name="textnotfound"></a>CRichEditView::TextNotFound

Rufen Sie diese Funktion auf, um den internen Suchstatus des [CRichEditView-Steuerelements](../../mfc/reference/cricheditview-class.md) nach einem fehlgeschlagenen Aufruf von [FindText](#findtext)zurückzusetzen.

```
void TextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parameter

*lpszFind*<br/>
Enthält die Textzeichenfolge, die nicht gefunden wurde.

### <a name="remarks"></a>Bemerkungen

Es wird empfohlen, diese Methode sofort nach fehlgeschlagenen Aufrufen von [FindText](#findtext) aufzurufen, damit der interne Suchstatus des Steuerelements ordnungsgemäß zurückgesetzt wird.

Der Parameter *lpszFind* sollte denselben Inhalt wie die Zeichenfolge enthalten, die [FindText](#findtext)bereitgestellt hat. Nach dem Zurücksetzen des internen Suchstatus ruft diese Methode die [OnTextNotFound-Methode](#ontextnotfound) mit der bereitgestellten Suchzeichenfolge auf.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CRichEditView::FindText](#findtext).

## <a name="cricheditviewwrapchanged"></a><a name="wrapchanged"></a>CRichEditView::WrapChanged

Rufen Sie diese Funktion auf, wenn sich die Druckeigenschaften geändert haben ( [SetMargins](#setmargins) oder [SetPaperSize](#setpapersize)).

```
virtual void WrapChanged();
```

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um zu ändern, wie die Rich-Edit-Ansicht auf Änderungen in [m_nWordWrap](#m_nwordwrap) oder den Druckeigenschaften ( [OnPrinterChanged )](#onprinterchanged)reagiert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView-Klasse](../../mfc/reference/cctrlview-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc-Klasse](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditCntrItem-Klasse](../../mfc/reference/cricheditcntritem-class.md)
