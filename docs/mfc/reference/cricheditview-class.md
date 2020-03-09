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
ms.openlocfilehash: b32578cc3c9ad4f7a89b8ee76449259c0fa0b43b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883656"
---
# <a name="cricheditview-class"></a>CRichEditView-Klasse

Mit [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) und [cricheditcntetem](../../mfc/reference/cricheditcntritem-class.md)stellt die Funktionalität des Rich-Edit-Steuer Elements im Kontext der MFC-Dokument Ansichts Architektur bereit.

## <a name="syntax"></a>Syntax

```
class CRichEditView : public CCtrlView
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRichEditView:: CRichEditView](#cricheditview)|Erstellt ein `CRichEditView`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRichEditView:: Bild Dialogposition](#adjustdialogposition)|Verschiebt ein Dialogfeld so, dass die aktuelle Auswahl nicht verdeckt wird.|
|[CRichEditView:: CanPaste](#canpaste)|Gibt an, ob die Zwischenablage Daten enthält, die in die umfangreiche Bearbeitungs Ansicht eingefügt werden können.|
|[CRichEditView::D opaste](#dopaste)|Fügt ein OLE-Element in diese Rich-Edit-Ansicht ein.|
|[CRichEditView:: FindText](#findtext)|Sucht den angegebenen Text, der den warte Cursor aufruft.|
|[CRichEditView:: findtextsimple](#findtextsimple)|Sucht den angegebenen Text.|
|[CRichEditView:: getcharformatselection](#getcharformatselection)|Ruft die Zeichen Formatierungs Attribute für die aktuelle Auswahl ab.|
|[CRichEditView:: GetDocument](#getdocument)|Ruft einen Zeiger auf das verwandte [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)ab.|
|[CRichEditView:: getinplaceactiveitem](#getinplaceactiveitem)|Ruft das OLE-Element ab, das gerade direkt in der Rich-Bearbeitungs Ansicht aktiv ist.|
|[CRichEditView:: getMargin](#getmargins)|Ruft die Ränder für diese Rich-Edit-Ansicht ab.|
|[CRichEditView:: getpageru](#getpagerect)|Ruft das Seiten Rechteck für diese Rich-Edit-Ansicht ab.|
|[CRichEditView:: getpapersize](#getpapersize)|Ruft das Papierformat für diese Rich-Edit-Ansicht ab.|
|[CRichEditView:: getparaformatselection](#getparaformatselection)|Ruft die Absatz Formatierungs Attribute für die aktuelle Auswahl ab.|
|[CRichEditView:: getprintrect](#getprintrect)|Ruft das Druck Rechteck für diese Rich-Edit-Ansicht ab.|
|[CRichEditView:: getprintwidth](#getprintwidth)|Ruft die Druckbreite für diese Rich-Edit-Ansicht ab.|
|[CRichEditView:: GetRichEditCtrl](#getricheditctrl)|Ruft das Rich Edit-Steuerelement ab.|
|[CRichEditView:: getSelectedItem](#getselecteditem)|Ruft das ausgewählte Element aus der Rich-Edit-Ansicht ab.|
|[CRichEditView:: getTextLength](#gettextlength)|Ruft die Länge des Texts in der Rich-Edit-Ansicht ab.|
|[CRichEditView:: gettextverlänex](#gettextlengthex)|Ruft die Anzahl der Zeichen oder Bytes in der Rich-Edit-Ansicht ab. Erweiterte flagliste für die Methode zur Bestimmung der Länge.|
|[CRichEditView:: insertfileasobject](#insertfileasobject)|Fügt eine Datei als OLE-Element ein.|
|[CRichEditView:: InsertItem](#insertitem)|Fügt ein neues Element als OLE-Element ein.|
|[CRichEditView:: isricheditformat](#isricheditformat)|Gibt an, ob die Zwischenablage Daten in einem Rich-Edit-oder Text-Format enthält.|
|[CRichEditView:: onchareffect](#onchareffect)|Schaltet die Zeichen Formatierung für die aktuelle Auswahl um.|
|[CRichEditView:: onparaalign](#onparaalign)|Ändert die Ausrichtung von Absätzen.|
|[CRichEditView:: onupdatechareffect](#onupdatechareffect)|Aktualisiert die Befehls Benutzeroberfläche für öffentliche Zeichenfunktionen.|
|[CRichEditView:: onupdateparaalign](#onupdateparaalign)|Aktualisiert die Befehls Benutzeroberfläche für öffentliche Absatz Funktionen von Absätzen.|
|[CRichEditView::P rintinsiderect](#printinsiderect)|Formatiert den angegebenen Text innerhalb des angegebenen Rechtecks.|
|[CRichEditView::P rintpage](#printpage)|Formatiert den angegebenen Text innerhalb der angegebenen Seite.|
|[CRichEditView:: setcharformat](#setcharformat)|Legt die Zeichen Formatierungs Attribute für die aktuelle Auswahl fest.|
|[CRichEditView:: setMargin](#setmargins)|Legt die Ränder für diese Rich-Edit-Ansicht fest.|
|[CRichEditView:: setpapersize](#setpapersize)|Legt das Papierformat für diese Rich-Edit-Ansicht fest.|
|[CRichEditView:: SetParaFormat](#setparaformat)|Legt die Absatz Formatierungs Attribute für die aktuelle Auswahl fest.|
|[CRichEditView:: TextNotFound](#textnotfound)|Setzt den internen Such Zustand des-Steuer Elements zurück.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRichEditView:: GetClipboardData](#getclipboarddata)|Ruft ein Zwischenablage Objekt für einen Bereich in dieser Rich-Edit-Ansicht ab.|
|[CRichEditView:: GetContextMenu](#getcontextmenu)|Ruft ein Kontextmenü ab, das mit der rechten Maustaste gedrückt werden soll.|
|[CRichEditView:: issgewählt](#isselected)|Gibt an, ob das angegebene OLE-Element ausgewählt ist.|
|[CRichEditView:: onfindnext](#onfindnext)|Sucht das nächste Vorkommen einer Teil Zeichenfolge.|
|[CRichEditView:: OnInitialUpdate](#oninitialupdate)|Aktualisiert eine Ansicht, wenn Sie zum ersten Mal an ein Dokument angefügt wird.|
|[CRichEditView:: onpstenativeobject](#onpastenativeobject)|Ruft systemeigene Daten von einem OLE-Element ab.|
|[CRichEditView:: onprinterchanged](#onprinterchanged)|Legt die Druckeigenschaften für das angegebene Gerät fest.|
|[CRichEditView:: onreplaceall](#onreplaceall)|Ersetzt alle Vorkommen einer angegebenen Zeichenfolge durch eine neue Zeichenfolge.|
|[CRichEditView:: onreplacesel](#onreplacesel)|Ersetzt die aktuelle Auswahl.|
|[CRichEditView:: ontextnotfound](#ontextnotfound)|Behandelt die Benutzer Benachrichtigung, dass der angeforderte Text nicht gefunden wurde.|
|[CRichEditView:: queryakzeptdata](#queryacceptdata)|Abfragen, um Informationen zu den Daten auf dem `IDataObject`anzuzeigen.|
|[CRichEditView:: wrapchanged](#wrapchanged)|Passt das Ziel Ausgabegerät für diese Rich-Edit-Ansicht an, basierend auf dem Wert `m_nWordWrap`.|

### <a name="public-data-members"></a>Öffentliche Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRichEditView:: m_nBulletIndent](#m_nbulletindent)|Gibt den Einzug für Aufzählungs Listen an.|
|[CRichEditView:: m_nWordWrap](#m_nwordwrap)|Gibt die Zeilenumbruch Einschränkungen an.|

## <a name="remarks"></a>Bemerkungen

Ein "Rich Edit-Steuerelement" ist ein Fenster, in dem der Benutzer Text eingeben und bearbeiten kann. Dem Text kann eine Zeichen-und Absatz Formatierung zugewiesen werden, die eingebettete OLE-Objekte enthalten kann. Rich Edit-Steuerelemente stellen eine Programmierschnittstelle zum Formatieren von Text bereit. Allerdings muss eine Anwendung alle Benutzeroberflächen Komponenten implementieren, die für das verfügbar machen von Formatierungs Vorgängen für den Benutzer erforderlich sind.

`CRichEditView` behält den Text und die Formatierungs Eigenschaft von Text bei. `CRichEditDoc` verwaltet die Liste der OLE-Client Elemente in der Ansicht. `CRichEditCntrItem` bietet Container seitigen Zugriff auf das OLE-Client Element.

Dieses allgemeine Windows-Steuerelement (und daher die [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) -Klasse und verwandte Klassen) ist nur für Programme verfügbar, die unter Windows 95/98 und Windows NT, Version 3,51 und höher, ausgeführt werden.

Ein Beispiel für die Verwendung einer Rich-Edit-Ansicht in einer MFC-Anwendung finden Sie unter [WordPad](../../overview/visual-cpp-samples.md) -Beispielanwendung.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[Cctrlview](../../mfc/reference/cctrlview-class.md)

`CRichEditView`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxrich. h

##  <a name="adjustdialogposition"></a>CRichEditView:: Bild Dialogposition

Diese Funktion wird aufgerufen, um das angegebene Dialogfeld zu verschieben, sodass die aktuelle Auswahl nicht verdeckt wird.

```
void AdjustDialogPosition(CDialog* pDlg);
```

### <a name="parameters"></a>Parameter

*pdlg*<br/>
Zeiger auf ein `CDialog` Objekt.

##  <a name="canpaste"></a>CRichEditView:: CanPaste

Mit dieser Funktion können Sie feststellen, ob die Zwischenablage Informationen enthält, die in diese Rich-Edit-Ansicht eingefügt werden können.

```
BOOL CanPaste() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Zwischenablage Daten in einem Format enthält, das diese Rich-Edit-Ansicht annehmen kann andernfalls 0.

##  <a name="cricheditview"></a>CRichEditView:: CRichEditView

Rufen Sie diese Funktion auf, um ein `CRichEditView` Objekt zu erstellen.

```
CRichEditView();
```

##  <a name="dopaste"></a>CRichEditView::D opaste

Diese Funktion wird aufgerufen, um das OLE-Element in *dataobj* in dieses Rich-Edit-Dokument/Ansicht einzufügen.

```
void DoPaste(
    COleDataObject& dataobj,
    CLIPFORMAT cf,
    HMETAFILEPICT hMetaPict);
```

### <a name="parameters"></a>Parameter

*dataobj*<br/>
Das [COleDataObject](../../mfc/reference/coledataobject-class.md) , das die einzuschließenden Daten enthält.

*CF*<br/>
Das gewünschte Zwischenablage Format.

*hmetapict*<br/>
Die Metadatendatei, die das eingefügte Element darstellt.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Funktion als Teil der Standard Implementierung von [queryakzeptdata](#queryacceptdata)auf.

Diese Funktion bestimmt den Typ des Einfüge Vorgangs basierend auf den Ergebnissen des Handlers für das Einfügen von Sonderzeichen. Wenn *CF* den Wert 0 hat, wird für das neue Element die aktuelle ikonischen Darstellung verwendet. Wenn *CF* ungleich NULL und *hmetapict* nicht NULL ist, verwendet das neue Element *hmetapict* für seine Darstellung.

##  <a name="findtext"></a>CRichEditView:: FindText

Mit dieser Funktion können Sie den angegebenen Text suchen und als aktuelle Auswahl festlegen.

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>Parameter

*lpszfind*<br/>
Enthält die Zeichenfolge, nach der gesucht werden soll.

*bcase*<br/>
Gibt an, ob bei der Suche Groß-und Kleinschreibung

*bWord*<br/>
Gibt an, ob die Suche nur ganze Wörter, keine Teile von Wörtern, entsprechen soll.

*bnext*<br/>
Gibt die Suchrichtung an. TRUE gibt an, dass die Suchrichtung an das Ende des Puffers gerichtet ist. FALSE gibt an, dass die Suchrichtung an den Anfang des Puffers gerichtet ist.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der *lpszfind* -Text gefunden wird. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion zeigt den warte Cursor während des Such Vorgangs an.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#151](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]

##  <a name="findtextsimple"></a>CRichEditView:: findtextsimple

Mit dieser Funktion können Sie den angegebenen Text suchen und als aktuelle Auswahl festlegen.

```
BOOL FindTextSimple(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>Parameter

*lpszfind*<br/>
Enthält die Zeichenfolge, nach der gesucht werden soll.

*bcase*<br/>
Gibt an, ob bei der Suche Groß-und Kleinschreibung

*bWord*<br/>
Gibt an, ob die Suche nur ganze Wörter, keine Teile von Wörtern, entsprechen soll.

*bnext*<br/>
Gibt die Suchrichtung an. TRUE gibt an, dass die Suchrichtung an das Ende des Puffers gerichtet ist. FALSE gibt an, dass die Suchrichtung an den Anfang des Puffers gerichtet ist.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der *lpszfind* -Text gefunden wird. andernfalls 0.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CRichEditView:: FindText](#findtext).

##  <a name="getcharformatselection"></a>CRichEditView:: getcharformatselection

Mit dieser Funktion werden die Zeichen Formatierungs Attribute der aktuellen Auswahl abzurufen.

```
CHARFORMAT2& GetCharFormatSelection();
```

### <a name="return-value"></a>Rückgabewert

Eine [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) -Struktur, die die Zeichen Formatierungs Attribute der aktuellen Auswahl enthält.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie in den [EM_GETCHARFORMAT](/windows/win32/Controls/em-getcharformat) -und [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) -Struktur im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

##  <a name="getclipboarddata"></a>CRichEditView:: GetClipboardData

Das Framework ruft diese Funktion im Rahmen der Verarbeitung von [IRichEditOleCallback:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata)auf.

```
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,
    DWORD dwReco,
    LPDATAOBJECT lpRichDataObj,
    LPDATAOBJECT* lplpdataobj);
```

### <a name="parameters"></a>Parameter

*lpchrg*<br/>
Ein Zeiger auf die [charrange](/windows/win32/api/richedit/ns-richedit-charrange) -Struktur, die den Zeichenbereich (und die OLE-Elemente) angibt, der in das von *lplpdataobj*angegebene Datenobjekt kopiert werden soll.

*dwreco*<br/>
Flag für Zwischenablage Vorgang. Kann einen der folgenden Werte aufweisen.

- RECO_COPY in die Zwischenablage kopieren.

- RECO_CUT in die Zwischenablage ausgeschnitten.

- RECO_DRAG Zieh Vorgang (Drag & Drop).

- RECO_DROP Drop-Vorgang (Drag & Drop).

- RECO_PASTE aus der Zwischenablage einfügen.

*lprichdataobj*<br/>
Ein Zeiger auf ein [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) -Objekt, das die Zwischenablage Daten aus dem Rich-Edit-Steuerelement ( [iricheditole:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata)) enthält.

*lplpdataobj*<br/>
Ein Zeiger auf die Zeiger Variable, die die Adresse des `IDataObject` Objekts empfängt, das den im *lpchrg* -Parameter angegebenen Bereich darstellt. Der Wert von *lplpdataobj* wird ignoriert, wenn ein Fehler zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Wert, der den Erfolg des Vorgangs meldet. Weitere Informationen zu HRESULT finden Sie unter [Struktur von com-Fehler Codes](/windows/win32/com/structure-of-com-error-codes) in der Windows SDK.

### <a name="remarks"></a>Bemerkungen

Wenn der Rückgabewert Erfolg angibt, gibt `IRichEditOleCallback::GetClipboardData` den `IDataObject` zurück, auf den von " *lplpdataobj*" zugegriffen wird. Andernfalls wird der Wert zurückgegeben, auf den von *lprichdataobj*zugegriffen wird. Überschreiben Sie diese Funktion, um Ihre eigenen Zwischenablage Daten bereitzustellen. Die Standard Implementierung dieser Funktion gibt E_NOTIMPL zurück.

Hierbei handelt es sich um eine erweiterte über schreibbare.

Weitere Informationen finden Sie unter [iricheditole:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata), [IRichEditOleCallback:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata)und [charrange](/windows/win32/api/richedit/ns-richedit-charrange) im Windows SDK und unter [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) im Windows SDK.

##  <a name="getcontextmenu"></a>CRichEditView:: GetContextMenu

Das Framework ruft diese Funktion im Rahmen der Verarbeitung von [IRichEditOleCallback:: GetContextMenu](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu)auf.

```
virtual HMENU GetContextMenu(
    WORD seltyp,
    LPOLEOBJECT lpoleobj,
    CHARRANGE* lpchrg);
```

### <a name="parameters"></a>Parameter

*selyp*<br/>
Der Auswahltyp. Die Werte für den Auswahltyp werden im Abschnitt "Hinweise" beschrieben.

*lpoleobj*<br/>
Ein Zeiger auf eine `OLEOBJECT` Struktur, die das erste ausgewählte OLE-Objekt angibt, wenn die Auswahl ein oder mehrere OLE-Elemente enthält. Wenn die Auswahl keine Elemente enthält, ist *lpoleobj* NULL. Die `OLEOBJECT`-Struktur enthält einen Zeiger auf ein OLE-Objekt v-Table.

*lpchrg*<br/>
Zeiger auf eine [charrange](/windows/win32/api/richedit/ns-richedit-charrange) -Struktur, die die aktuelle Auswahl enthält.

### <a name="return-value"></a>Rückgabewert

Handle für das Kontextmenü.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist ein typischer Teil der nach-unten-Verarbeitung mit der rechten Maustaste.

Der Auswahltyp kann eine beliebige Kombination der folgenden Flags sein:

- SEL_EMPTY gibt an, dass keine aktuelle Auswahl vorhanden ist.

- SEL_TEXT gibt an, dass die aktuelle Auswahl Text enthält.

- SEL_OBJECT gibt an, dass die aktuelle Auswahl mindestens ein OLE-Element enthält.

- SEL_MULTICHAR gibt an, dass die aktuelle Auswahl mehr als ein Textzeichen enthält.

- SEL_MULTIOBJECT gibt an, dass die aktuelle Auswahl mehr als ein OLE-Objekt enthält.

Die Standard Implementierung gibt NULL zurück. Hierbei handelt es sich um eine erweiterte über schreibbare.

Weitere Informationen finden Sie unter [IRichEditOleCallback:: GetContextMenu](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu) und [charrange](/windows/win32/api/richedit/ns-richedit-charrange) in der Windows SDK.

##  <a name="getdocument"></a>CRichEditView:: GetDocument

Mit dieser Funktion können Sie einen Zeiger auf den `CRichEditDoc` abrufen, der dieser Ansicht zugeordnet ist.

```
CRichEditDoc* GetDocument() const;
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf ein [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) -Objekt, das mit dem `CRichEditView` Objekt verknüpft ist.

##  <a name="getinplaceactiveitem"></a>CRichEditView:: getinplaceactiveitem

Mit dieser Funktion können Sie das OLE-Element abrufen, das derzeit in diesem `CRichEditView` Objekt aktiviert ist.

```
CRichEditCntrItem* GetInPlaceActiveItem() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das einzelne, direkte aktive [cricheditcnytem](../../mfc/reference/cricheditcntritem-class.md) -Objekt in dieser Rich-Edit-Ansicht. NULL, wenn sich zurzeit kein OLE-Element im direkten aktiven Zustand befindet.

##  <a name="getmargins"></a>CRichEditView:: getMargin

Rufen Sie diese Funktion auf, um die beim Drucken verwendeten aktuellen Ränder abzurufen.

```
CRect GetMargins() const;
```

### <a name="return-value"></a>Rückgabewert

Die beim Drucken verwendeten Ränder, gemessen in MM_TWIPS.

##  <a name="getpagerect"></a>CRichEditView:: getpageru

Mit dieser Funktion können Sie die Dimensionen der Seite abrufen, die beim Drucken verwendet wird.

```
CRect GetPageRect() const;
```

### <a name="return-value"></a>Rückgabewert

Die Begrenzungen der beim Drucken verwendeten Seite, gemessen in MM_TWIPS.

### <a name="remarks"></a>Bemerkungen

Dieser Wert basiert auf dem Papierformat.

##  <a name="getpapersize"></a>CRichEditView:: getpapersize

Rufen Sie diese Funktion auf, um das aktuelle Papierformat abzurufen.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Größe des im Druck verwendeten Papier, gemessen in MM_TWIPS.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]

##  <a name="getparaformatselection"></a>CRichEditView:: getparaformatselection

Mit dieser Funktion werden die Absatz Formatierungs Attribute der aktuellen Auswahl abzurufen.

```
PARAFORMAT2& GetParaFormatSelection();
```

### <a name="return-value"></a>Rückgabewert

Eine [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) -Struktur, die die Absatz Formatierungs Attribute der aktuellen Auswahl enthält.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [EM_GETPARAFORMAT](/windows/win32/Controls/em-getparaformat) -Message-und [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) -Struktur im Windows SDK.

##  <a name="getprintrect"></a>CRichEditView:: getprintrect

Rufen Sie diese Funktion auf, um die Begrenzungen des Druck Bereichs innerhalb des Seiten Rechtecks abzurufen.

```
CRect GetPrintRect() const;
```

### <a name="return-value"></a>Rückgabewert

Die Begrenzungen des beim Drucken verwendeten Bildbereichs, gemessen in MM_TWIPS.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]

##  <a name="getprintwidth"></a>CRichEditView:: getprintwidth

Mit dieser Funktion können Sie die Breite des Druck Bereichs bestimmen.

```
int GetPrintWidth() const;
```

### <a name="return-value"></a>Rückgabewert

Die Breite des Druck Bereichs, gemessen in MM_TWIPS.

##  <a name="getricheditctrl"></a>CRichEditView:: GetRichEditCtrl

Rufen Sie diese Funktion auf, um das [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) -Objekt abzurufen, das dem `CRichEditView` Objekt zugeordnet ist.

```
CRichEditCtrl& GetRichEditCtrl() const;
```

### <a name="return-value"></a>Rückgabewert

Das `CRichEditCtrl`-Objekt für diese Ansicht.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CRichEditView:: FindText](#findtext).

##  <a name="getselecteditem"></a>CRichEditView:: getSelectedItem

Rufen Sie diese Funktion auf, um das OLE-Element (ein `CRichEditCntrItem` Objekt) abzurufen, das momentan in diesem `CRichEditView` Objekt ausgewählt ist.

```
CRichEditCntrItem* GetSelectedItem() const;
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf ein im `CRichEditView` Objekt ausgewähltes [cricheditcnselektitem](../../mfc/reference/cricheditcntritem-class.md) -Objekt. NULL, wenn kein Element in dieser Ansicht ausgewählt ist.

##  <a name="gettextlength"></a>CRichEditView:: getTextLength

Rufen Sie diese Funktion auf, um die Länge des Texts in diesem `CRichEditView` Objekt abzurufen.

```
long GetTextLength() const;
```

### <a name="return-value"></a>Rückgabewert

Die Länge des Texts in diesem `CRichEditView` Objekt.

##  <a name="gettextlengthex"></a>CRichEditView:: gettextverlänex

Diese Member-Funktion wird aufgerufen, um die Länge des Texts in diesem `CRichEditView` Objekt zu berechnen.

```
long GetTextLengthEx(
    DWORD dwFlags,
    UINT uCodePage = -1) const;
```

### <a name="parameters"></a>Parameter

*dwFlags*<br/>
-Wert, der die Methode angibt, die zum Bestimmen der Textlänge verwendet werden soll. Bei diesem Element kann es sich um einen oder mehrere der Werte handeln, die im Flags-Member von [gettextlängen Ex](/windows/win32/api/richedit/ns-richedit-gettextlengthex) aufgeführt sind, der in der Windows SDK beschrieben wird.

*ucodepage*<br/>
Codepage für Übersetzung (CP_ACP für die ANSI-Codepage 1200 für Unicode).

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Zeichen oder Bytes im Bearbeitungs Steuerelement. Wenn inkompatible Flags in *dwFlags*festgelegt wurden, gibt diese Member-Funktion E_INVALIDARG zurück.

### <a name="remarks"></a>Bemerkungen

`GetTextLengthEx` bietet zusätzliche Möglichkeiten, die Länge des Texts zu bestimmen. Es unterstützt die umfassende Edit 2,0-Funktionalität. Weitere Informationen finden Sie unter Informationen [zu Rich Edit](/windows/win32/Controls/about-rich-edit-controls) -Steuerelementen in der Windows SDK.

##  <a name="insertfileasobject"></a>CRichEditView:: insertfileasobject

Mit dieser Funktion wird die angegebene Datei (als [cricheditcnytem](../../mfc/reference/cricheditcntritem-class.md) -Objekt) in eine Rich-Edit-Ansicht eingefügt.

```
void InsertFileAsObject(LPCTSTR lpszFileName);
```

### <a name="parameters"></a>Parameter

*lpszfilename*<br/>
Zeichenfolge, die den Namen der einzufügenden Datei enthält.

##  <a name="insertitem"></a>CRichEditView:: InsertItem

Mit dieser Funktion wird ein [cricheditcnytem](../../mfc/reference/cricheditcntritem-class.md) -Objekt in eine Rich-Bearbeitungs Ansicht eingefügt.

```
HRESULT InsertItem(CRichEditCntrItem* pItem);
```

### <a name="parameters"></a>Parameter

*pitem*<br/>
Zeiger auf das einzufügende Element.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Wert, der den Erfolg der Einfügung angibt.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu HRESULT finden Sie unter [Struktur von com-Fehler Codes](/windows/win32/com/structure-of-com-error-codes) in der Windows SDK.

##  <a name="isricheditformat"></a>CRichEditView:: isricheditformat

Mit dieser Funktion können Sie feststellen, ob *CF* ein Zwischenablage Format ist, bei dem es sich um Text, Rich Text oder Rich Text mit OLE-Elementen handelt.

```
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```

### <a name="parameters"></a>Parameter

*CF*<br/>
Das interessante Zwischenablage Format.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn *CF* ein umfassendes Bearbeitungs-oder Text Zwischenablage Format ist.

##  <a name="isselected"></a>CRichEditView:: issgewählt

Mit dieser Funktion wird ermittelt, ob das angegebene OLE-Element derzeit in dieser Ansicht ausgewählt ist.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Parameter

*pdocitem*<br/>
Zeiger auf ein Objekt in der Ansicht.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Objekt ausgewählt ist. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, wenn die abgeleitete Ansichts Klasse über eine andere Methode zum Behandeln der Auswahl von OLE-Elementen verfügt.

##  <a name="m_nbulletindent"></a>CRichEditView:: m_nBulletIndent

Der Einzug für Aufzählungs Elemente in einer Liste. Standardmäßig 720 Einheiten, d. h. 1/2 Zoll.

```
int m_nBulletIndent;
```

##  <a name="m_nwordwrap"></a>CRichEditView:: m_nWordWrap

Gibt den Typ des Zeilenumbruch für diese Rich-Edit-Ansicht an.

```
int m_nWordWrap;
```

### <a name="remarks"></a>Bemerkungen

Einer der folgenden Werte:

- `WrapNone` gibt an, dass keine automatische Wort Umbruch erfolgt.

- `WrapToWindow` gibt den Zeilenumbruch basierend auf der Breite des Fensters an.

- `WrapToTargetDevice` gibt die Wort Umbruch auf der Grundlage der Merkmale des Zielgeräts an.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CRichEditView:: wrapchanged](#wrapchanged).

##  <a name="onchareffect"></a>CRichEditView:: onchareffect

Mit dieser Funktion können Sie die Zeichen Formatierungs Effekte für die aktuelle Auswahl umschalten.

```
void OnCharEffect(
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Parameter

*dwMask*<br/>
Die Zeichen Formatierungs Effekte, die in der aktuellen Auswahl geändert werden sollen.

*dweffect*<br/>
Die gewünschte Liste der Zeichen Formatierungs Effekte, die gewechselt werden soll.

### <a name="remarks"></a>Bemerkungen

Jeder Aufrufe dieser Funktion schaltet die angegebenen Formatierungs Effekte für die aktuelle Auswahl um.

Weitere Informationen zu den Parametern *dwMask* und *dweffect* und ihren möglichen Werten finden Sie in den entsprechenden Datenmembern von [Charformat](/windows/win32/api/richedit/ns-richedit-charformata) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#155](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]

##  <a name="onfindnext"></a>CRichEditView:: onfindnext

Wird von Framework aufgerufen, wenn Befehle im Dialogfeld Suchen/Ersetzen verarbeitet werden.

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>Parameter

*lpszfind*<br/>
Die zu suchende Zeichenfolge.

*bnext*<br/>
Die zu durchsuchende Richtung: true gibt an, dass nach unten FALSE, up.

*bcase*<br/>
Gibt an, ob bei der Suche die Groß-/Kleinschreibung beachtet wird

*bWord*<br/>
Gibt an, ob bei der Suche nur ganze Wörter gefunden werden sollen.

### <a name="remarks"></a>Bemerkungen

Mit dieser Funktion können Sie nach Text innerhalb der `CRichEditView`suchen. Überschreiben Sie diese Funktion, um Such Eigenschaften für die abgeleitete Ansichts Klasse zu ändern.

##  <a name="oninitialupdate"></a>CRichEditView:: OnInitialUpdate

Wird von Framework aufgerufen, nachdem die Ansicht zum ersten Mal an das Dokument angefügt wurde, aber bevor die Ansicht anfänglich angezeigt wird.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Bemerkungen

Die Standard Implementierung dieser Funktion Ruft die [CView:: OnUpdate](../../mfc/reference/cview-class.md#onupdate) -Member-Funktion ohne Hinweis Informationen auf (d. h. mit den Standardwerten 0 für den *lHint* -Parameter und NULL für den Parameter " *phint* "). Überschreiben Sie diese Funktion, um eine einmalige Initialisierung durchzuführen, die Informationen über das Dokument erfordert. Wenn Ihre Anwendung z. b. Dokumente mit fester Größe enthält, können Sie diese Funktion verwenden, um die scrolllimits einer Ansicht basierend auf der Dokument Größe zu initialisieren. Wenn Ihre Anwendung Dokumente variabler Größe unterstützt, verwenden Sie `OnUpdate`, um die Bildlauf-Limits bei jeder Änderung des Dokuments zu aktualisieren.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CRichEditView:: m_nWordWrap](#m_nwordwrap).

##  <a name="onpastenativeobject"></a>CRichEditView:: onpstenativeobject

Verwenden Sie diese Funktion, um systemeigene Daten aus einem eingebetteten Element zu laden.

```
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```

### <a name="parameters"></a>Parameter

*lpstg*<br/>
Zeiger auf ein [IStorage](/windows/win32/api/objidl/nn-objidl-istorage) -Objekt.

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn erfolgreich; andernfalls 0;

### <a name="remarks"></a>Bemerkungen

Dies würden Sie in der Regel tun, indem Sie eine [colestreamfile-Datei](../../mfc/reference/colestreamfile-class.md) um die `IStorage`erstellen. Der `COleStreamFile` kann mit einem Archiv und [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) aufgerufen werden, um die Daten zu laden.

Hierbei handelt es sich um eine erweiterte über schreibbare.

Weitere Informationen finden Sie unter [IStorage](/windows/win32/api/objidl/nn-objidl-istorage) in der Windows SDK.

##  <a name="onparaalign"></a>CRichEditView:: onparaalign

Mit dieser Funktion können Sie die Absatz Ausrichtung für die ausgewählten Absätze ändern.

```
void OnParaAlign(WORD wAlign);
```

### <a name="parameters"></a>Parameter

*walign*<br/>
Gewünschte Absatz Ausrichtung. Einer der folgenden Werte:

- PFA_LEFT die Absätze am linken Rand ausrichten.

- PFA_RIGHT die Absätze am rechten Rand ausrichten.

- PFA_CENTER die Absätze zwischen den Rändern zentrieren.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]

##  <a name="onprinterchanged"></a>CRichEditView:: onprinterchanged

Überschreiben Sie diese Funktion, um die Eigenschaften für diese Rich-Bearbeitungs Ansicht zu ändern, wenn sich der Drucker ändert

```
virtual void OnPrinterChanged(const CDC& dcPrinter);
```

### <a name="parameters"></a>Parameter

*dcprinter*<br/>
Ein [CDC](../../mfc/reference/cdc-class.md) -Objekt für den neuen Drucker.

### <a name="remarks"></a>Bemerkungen

Mit der Standard Implementierung wird das Papierformat auf die physische Höhe und Breite für das Ausgabegerät (Drucker) festgelegt. Wenn *dcprinter*kein Gerätekontext zugeordnet ist, legt die Standard Implementierung das Papierformat auf 8,5 x 11 Zoll fest.

##  <a name="onreplaceall"></a>CRichEditView:: onreplaceall

Wird von Framework aufgerufen, wenn die Verarbeitung aller Befehle aus dem Dialogfeld "ersetzen" ersetzt wird.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>Parameter

*lpszfind*<br/>
Der zu ersetzende Text.

*lpszreplace*<br/>
Der Ersatztext.

*bcase*<br/>
Gibt an, ob bei der Suche Groß-und Kleinschreibung

*bWord*<br/>
Gibt an, ob bei der Suche ganze Wörter ausgewählt werden müssen oder nicht.

### <a name="remarks"></a>Bemerkungen

Mit dieser Funktion können Sie alle Vorkommen von angegebenem Text durch eine andere Zeichenfolge ersetzen. Überschreiben Sie diese Funktion, um die Such Eigenschaften für diese Ansicht zu ändern.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CRichEditView:: FindText](#findtext).

##  <a name="onreplacesel"></a>CRichEditView:: onreplacesel

Wird von Framework aufgerufen, wenn Replace-Befehle aus dem Replace-Dialogfeld verarbeitet werden.

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>Parameter

*lpszfind*<br/>
Der zu ersetzende Text.

*bnext*<br/>
Gibt die Suchrichtung an: true ist nicht zutreffend; FALSE, up.

*bcase*<br/>
Gibt an, ob bei der Suche Groß-und Kleinschreibung

*bWord*<br/>
Gibt an, ob bei der Suche ganze Wörter ausgewählt werden müssen oder nicht.

*lpszreplace*<br/>
Der Ersatztext.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird aufgerufen, um ein Vorkommen eines bestimmten Texts durch eine andere Zeichenfolge zu ersetzen. Überschreiben Sie diese Funktion, um die Such Eigenschaften für diese Ansicht zu ändern.

##  <a name="ontextnotfound"></a>CRichEditView:: ontextnotfound

Wird von Framework aufgerufen, wenn bei einer Suche ein Fehler auftritt.

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parameter

*lpszfind*<br/>
Der Text, der nicht gefunden wurde.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um die Ausgabe Benachrichtigung von einem [MessageBeep](/windows/win32/api/winuser/nf-winuser-messagebeep)zu ändern.

Weitere Informationen finden Sie unter [MessageBeep](/windows/win32/api/winuser/nf-winuser-messagebeep) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#157](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]

##  <a name="onupdatechareffect"></a>CRichEditView:: onupdatechareffect

Das Framework ruft diese Funktion auf, um die Befehls Benutzeroberfläche für Zeichen Effekt Befehle zu aktualisieren.

```
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Parameter

*pCmdUI*<br/>
Zeiger auf ein [CCmdUI](../../mfc/reference/ccmdui-class.md) -Objekt.

*dwMask*<br/>
Gibt die Zeichen Formatierungs Maske an.

*dweffect*<br/>
Gibt den Zeichen Formatierungs Effekt an.

### <a name="remarks"></a>Bemerkungen

Die Maske *dwMask* gibt an, welche Zeichen Formatierungs Attribute überprüft werden sollen. Die Flags *dweffect* listet die Zeichen Formatierungs Attribute auf, die festgelegt/gelöscht werden sollen.

Weitere Informationen zu den Parametern *dwMask* und *dweffect* und ihren möglichen Werten finden Sie in den entsprechenden Datenmembern von [Charformat](/windows/win32/api/richedit/ns-richedit-charformata) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]

##  <a name="onupdateparaalign"></a>CRichEditView:: onupdateparaalign

Das Framework ruft diese Funktion auf, um die Befehls Benutzeroberfläche für Absatz Effekt Befehle zu aktualisieren.

```
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,
    WORD wAlign);
```

### <a name="parameters"></a>Parameter

*pCmdUI*<br/>
Zeiger auf ein [CCmdUI](../../mfc/reference/ccmdui-class.md) -Objekt.

*walign*<br/>
Die zu Überprüfung der Absatz Ausrichtung. Einer der folgenden Werte:

- PFA_LEFT die Absätze am linken Rand ausrichten.

- PFA_RIGHT die Absätze am rechten Rand ausrichten.

- PFA_CENTER die Absätze zwischen den Rändern zentrieren.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]

##  <a name="printinsiderect"></a>CRichEditView::P rintinsiderect

Mit dieser Funktion können Sie einen Textbereich in einem Rich-Edit-Steuerelement formatieren, das in das *rectlayout* für das von *PDC*angegebene Gerät passt.

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

*Neulayout*<br/>
[Rect](/windows/win32/api/windef/ns-windef-rect) oder [CRect](../../atl-mfc-shared/reference/crect-class.md) , das den Ausgabebereich definiert.

*nindexstart*<br/>
Der null basierte Index des ersten Zeichens, das formatiert werden soll.

*nindexstoppt*<br/>
Der null basierte Index des letzten Zeichens, das formatiert werden soll.

*boutput*<br/>
Gibt an, ob der Text gerendert werden soll. FALSE gibt an, dass der Text gerade gemessen wird.

### <a name="return-value"></a>Rückgabewert

Der Index des letzten Zeichens, das in den Ausgabebereich passt, plus eins.

### <a name="remarks"></a>Bemerkungen

Normalerweise folgt diesem-Befehl ein aufrufswert für [CRichEditCtrl::D isplayband](../../mfc/reference/cricheditctrl-class.md#displayband) , der die Ausgabe generiert.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CRichEditView:: getpapersize](#getpapersize).

##  <a name="printpage"></a>CRichEditView::P rintpage

Mit dieser Funktion können Sie einen Textbereich in einem Rich-Edit-Steuerelement für das von *PDC*angegebene Ausgabegerät formatieren.

```
long PrintPage(
    CDC* pDC,
    long nIndexStart,
    long nIndexStop);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Zeiger auf einen Gerätekontext für die Seiten Ausgabe.

*nindexstart*<br/>
Der null basierte Index des ersten Zeichens, das formatiert werden soll.

*nindexstoppt*<br/>
Der null basierte Index des letzten Zeichens, das formatiert werden soll.

### <a name="return-value"></a>Rückgabewert

Der Index des letzten Zeichens, das auf die Seite passt, plus eins.

### <a name="remarks"></a>Bemerkungen

Das Layout jeder Seite wird von [getpagerup](#getpagerect) und [getprintrect](#getprintrect)gesteuert. Normalerweise folgt diesem-Befehl ein aufrufswert für [CRichEditCtrl::D isplayband](../../mfc/reference/cricheditctrl-class.md#displayband) , der die Ausgabe generiert.

Beachten Sie, dass die Ränder relativ zur physischen Seite sind, nicht zur logischen Seite. Daher wird der Text durch Ränder von 0 (null) häufig geclistet, da viele Drucker nicht Druck Bare Bereiche auf der Seite haben. Um das Abschneiden von Text zu vermeiden, sollten Sie [setMargin](#setmargins) aufrufen und vor dem Drucken angemessene Ränder festlegen.

##  <a name="queryacceptdata"></a>CRichEditView:: queryakzeptdata

Wird von Framework aufgerufen, um ein Objekt in den Rich-Edit-Code einzufügen.

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
Zeiger auf das [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) , das abgefragt werden soll.

*lpcfformat*<br/>
Zeiger auf das akzeptable Datenformat.

*dwreco*<br/>
Wird nicht verwendet.

*vollständig*<br/>
Gibt an, ob der Einfügevorgang fortgesetzt werden soll.

*HMETAFILE*<br/>
Ein Handle für die Metadatendatei, die zum Zeichnen des Element Symbols verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Wert, der den Erfolg des Vorgangs meldet.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um eine andere Organisation der com-Elemente in der abgeleiteten Dokument Klasse zu verarbeiten. Hierbei handelt es sich um eine erweiterte über schreibbare.

Weitere Informationen zu HRESULT und `IDataObject`finden Sie unter [Struktur von com-Fehler Codes](/windows/win32/com/structure-of-com-error-codes) bzw. [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]

##  <a name="setcharformat"></a>CRichEditView:: setcharformat

Diese Funktion wird aufgerufen, um die Zeichen Formatierungs Attribute für neuen Text in diesem `CRichEditView` Objekt festzulegen.

```
void SetCharFormat(CHARFORMAT2 cf);
```

### <a name="parameters"></a>Parameter

*CF*<br/>
[CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) -Struktur, die die neuen Standard Zeichen Formatierungs Attribute enthält.

### <a name="remarks"></a>Bemerkungen

Nur die Attribute, die vom `dwMask`-Member von *CF* angegeben werden, werden von dieser Funktion geändert.

Weitere Informationen finden Sie unter [EM_SETCHARFORMAT](/windows/win32/Controls/em-setcharformat) -Message-und [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) -Struktur im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

##  <a name="setmargins"></a>CRichEditView:: setMargin

Mit dieser Funktion können Sie die Druckränder für diese Rich-Edit-Ansicht festlegen.

```
void SetMargins(const CRect& rectMargin);
```

### <a name="parameters"></a>Parameter

*rectmargin*<br/>
Die neuen Randwerte für den Druck, gemessen in MM_TWIPS.

### <a name="remarks"></a>Bemerkungen

Wenn [m_nWordWrap](#m_nwordwrap) `WrapToTargetDevice`ist, sollte [wrapchanged](#wrapchanged) aufgerufen werden, nachdem diese Funktion zum Anpassen von Druckeigenschaften verwendet wurde.

Beachten Sie, dass die von [PrintPage](#printpage) verwendeten Ränder relativ zur physischen Seite, nicht zur logischen Seite sind. Daher wird der Text durch Ränder von 0 (null) häufig geclistet, da viele Drucker nicht Druck Bare Bereiche auf der Seite haben. Um das Abschneiden des Texts zu vermeiden, sollten Sie `SetMargins` verwenden, um vor dem Drucken sinnvolle Drucker Ränder festzulegen.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CRichEditView:: getpapersize](#getpapersize).

##  <a name="setpapersize"></a>CRichEditView:: setpapersize

Mit dieser Funktion können Sie das Papierformat für das Drucken dieser Rich-Bearbeitungs Ansicht festlegen.

```
void SetPaperSize(CSize sizePaper);
```

### <a name="parameters"></a>Parameter

*sizepaper*<br/>
Die neuen Papiergrößen Werte zum Drucken, gemessen in MM_TWIPS.

### <a name="remarks"></a>Bemerkungen

Wenn [m_nWordWrap](#m_nwordwrap) `WrapToTargetDevice`ist, sollte [wrapchanged](#wrapchanged) aufgerufen werden, nachdem diese Funktion zum Anpassen von Druckeigenschaften verwendet wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]

##  <a name="setparaformat"></a>CRichEditView:: SetParaFormat

Mit dieser Funktion werden die Absatz Formatierungs Attribute für die aktuelle Auswahl in diesem `CRichEditView` Objekt festgelegt.

```
BOOL SetParaFormat(PARAFORMAT2& pf);
```

### <a name="parameters"></a>Parameter

*pf*<br/>
[PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) -Struktur, die die neuen standardmäßigen Absatz Formatierungs Attribute enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn erfolgreich, andernfalls 0 (null).

### <a name="remarks"></a>Bemerkungen

Nur die Attribute, die vom `dwMask`-Member von *PF* angegeben werden, werden von dieser Funktion geändert.

Weitere Informationen finden Sie unter [EM_SETPARAFORMAT](/windows/win32/Controls/em-setparaformat) -Message-und [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) -Struktur im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]

##  <a name="textnotfound"></a>CRichEditView:: TextNotFound

Mit dieser Funktion können Sie den internen Such Zustand des [CRichEditView](../../mfc/reference/cricheditview-class.md) -Steuer Elements nach einem fehlgeschlagenen [FindText](#findtext)-Befehl Zurücksetzen.

```
void TextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parameter

*lpszfind*<br/>
Enthält die Text Zeichenfolge, die nicht gefunden wurde.

### <a name="remarks"></a>Bemerkungen

Es wird empfohlen, diese Methode unmittelbar nach fehlgeschlagenen Aufrufen von [FindText](#findtext) aufzurufen, damit der interne Such Zustand des Steuer Elements ordnungsgemäß zurückgesetzt wird.

Der *lpszfind* -Parameter sollte denselben Inhalt wie die für [FindText](#findtext)bereitgestellte Zeichenfolge enthalten. Nach dem Zurücksetzen des internen Such Zustands ruft diese Methode die [ontextnotfound](#ontextnotfound) -Methode mit der angegebenen Such Zeichenfolge auf.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CRichEditView:: FindText](#findtext).

##  <a name="wrapchanged"></a>CRichEditView:: wrapchanged

Diese Funktion aufrufen, wenn sich die Druckeigenschaften geändert haben ( [setMargin](#setmargins) oder [setpapersize](#setpapersize)).

```
virtual void WrapChanged();
```

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um die Methode zu ändern, mit der die Rich-Edit-Ansicht auf Änderungen in [m_nWordWrap](#m_nwordwrap) oder den Druck Merkmalen ( [onprinterchanged](#onprinterchanged)) antwortet.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel WordPad](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView-Klasse](../../mfc/reference/cctrlview-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc-Klasse](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditCntrItem-Klasse](../../mfc/reference/cricheditcntritem-class.md)
