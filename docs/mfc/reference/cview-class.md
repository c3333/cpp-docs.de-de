---
title: CView-Klasse
ms.date: 11/04/2016
f1_keywords:
- CView
- AFXWIN/CView
- AFXWIN/CView::CView
- AFXWIN/CView::DoPreparePrinting
- AFXWIN/CView::GetDocument
- AFXWIN/CView::IsSelected
- AFXWIN/CView::OnDragEnter
- AFXWIN/CView::OnDragLeave
- AFXWIN/CView::OnDragOver
- AFXWIN/CView::OnDragScroll
- AFXWIN/CView::OnDrop
- AFXWIN/CView::OnDropEx
- AFXWIN/CView::OnInitialUpdate
- AFXWIN/CView::OnPrepareDC
- AFXWIN/CView::OnScroll
- AFXWIN/CView::OnScrollBy
- AFXWIN/CView::OnActivateFrame
- AFXWIN/CView::OnActivateView
- AFXWIN/CView::OnBeginPrinting
- AFXWIN/CView::OnDraw
- AFXWIN/CView::OnEndPrinting
- AFXWIN/CView::OnEndPrintPreview
- AFXWIN/CView::OnPreparePrinting
- AFXWIN/CView::OnPrint
- AFXWIN/CView::OnUpdate
helpviewer_keywords:
- CView [MFC], CView
- CView [MFC], DoPreparePrinting
- CView [MFC], GetDocument
- CView [MFC], IsSelected
- CView [MFC], OnDragEnter
- CView [MFC], OnDragLeave
- CView [MFC], OnDragOver
- CView [MFC], OnDragScroll
- CView [MFC], OnDrop
- CView [MFC], OnDropEx
- CView [MFC], OnInitialUpdate
- CView [MFC], OnPrepareDC
- CView [MFC], OnScroll
- CView [MFC], OnScrollBy
- CView [MFC], OnActivateFrame
- CView [MFC], OnActivateView
- CView [MFC], OnBeginPrinting
- CView [MFC], OnDraw
- CView [MFC], OnEndPrinting
- CView [MFC], OnEndPrintPreview
- CView [MFC], OnPreparePrinting
- CView [MFC], OnPrint
- CView [MFC], OnUpdate
ms.assetid: 9cff3c56-7564-416b-b9a4-71a9254ed755
ms.openlocfilehash: f6be846e80209ce94c84222d61c37a7964baad03
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855540"
---
# <a name="cview-class"></a>CView-Klasse

Stellt die grundlegende Funktionalität für benutzerdefinierte Ansichtsklassen bereit.

## <a name="syntax"></a>Syntax

```
class AFX_NOVTABLE CView : public CWnd
```

## <a name="members"></a>Members

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CView:: CView](#cview)|Erstellt ein `CView`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CView::D oprepareprinting](#doprepareprinting)|Zeigt das Dialogfeld Drucken an und erstellt den Drucker Gerätekontext. wird beim Überschreiben der `OnPreparePrinting` Member-Funktion aufgerufen.|
|[CView:: GetDocument](#getdocument)|Gibt das Dokument zurück, das der Ansicht zugeordnet ist.|
|[CView:: issgewählt](#isselected)|Testet, ob ein Dokument Element ausgewählt ist. Erforderlich für die OLE-Unterstützung.|
|[CView:: OnDragEnter](#ondragenter)|Wird aufgerufen, wenn ein Element zum ersten Mal in den Drag & Drop-Bereich einer Ansicht gezogen wird.|
|[CView:: OnDragLeave](#ondragleave)|Wird aufgerufen, wenn ein gezogenes Element den Drag & Drop-Bereich einer Ansicht verlässt.|
|[CView:: OnDragOver](#ondragover)|Wird aufgerufen, wenn ein Element über den Drag & Drop-Bereich einer Ansicht gezogen wird.|
|[CView:: ondragscroll](#ondragscroll)|Wird aufgerufen, um zu bestimmen, ob der Cursor in den scrollbereich des Fensters gezogen wird.|
|[CView:: OnDrop](#ondrop)|Wird aufgerufen, wenn ein Element in den Drag & Drop-Bereich einer Ansicht, des Standard Handlers, abgelegt wurde.|
|[CView:: ondropex](#ondropex)|Wird aufgerufen, wenn ein Element in den Drag & Drop-Bereich einer Ansicht, des primären Handlers, abgelegt wurde.|
|[CView:: OnInitialUpdate](#oninitialupdate)|Wird aufgerufen, nachdem eine Ansicht erstmalig an ein Dokument angefügt wurde.|
|[CView:: OnPrepareDC](#onpreparedc)|Wird aufgerufen, bevor die `OnDraw` Member-Funktion für die Bildschirm Anzeige aufgerufen wird, oder wenn die `OnPrint` Member-Funktion für das Drucken oder die Seitenansicht aufgerufen wird.|
|[CView:: OnScroll](#onscroll)|Wird aufgerufen, wenn OLE-Elemente über die Rahmen der Ansicht hinausgezogen werden.|
|[CView:: onscrollby](#onscrollby)|Wird aufgerufen, wenn eine Sicht, die aktive direkte OLE-Elemente enthält, gescrollt wird.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CView:: onactivateframe](#onactivateframe)|Wird aufgerufen, wenn das Rahmen Fenster, das die Ansicht enthält, aktiviert oder deaktiviert wird.|
|[CView:: OnActivateView](#onactivateview)|Wird aufgerufen, wenn eine Ansicht aktiviert wird.|
|[CView:: OnBeginPrinting](#onbeginprinting)|Wird aufgerufen, wenn ein Druckauftrag beginnt. außer Kraft Setzung zum Zuordnen von GDI-Ressourcen (Graphics Device Interface).|
|[CView:: OnDraw](#ondraw)|Wird aufgerufen, um ein Bild des Dokuments für Bildschirm Anzeige, Druck oder Druckvorschau zu erzeugen. Implementierung erforderlich.|
|[CView:: OnEndPrinting](#onendprinting)|Wird aufgerufen, wenn ein Druckauftrag beendet wird. außer Kraft Setzung zum Freigabe von GDI-Ressourcen.|
|[CView:: onendprintpreview](#onendprintpreview)|Wird aufgerufen, wenn der Vorschaumodus beendet wird.|
|[CView:: OnPreparePrinting](#onprepareprinting)|Wird aufgerufen, bevor ein Dokument gedruckt oder in der Vorschau angezeigt wird. überschreiben, um das Dialogfeld Drucken zu initialisieren.|
|[CView:: OnPrint](#onprint)|Wird aufgerufen, um eine Seite des Dokuments zu drucken oder eine Vorschau anzuzeigen.|
|[CView:: OnUpdate](#onupdate)|Wird aufgerufen, um eine Ansicht zu benachrichtigen, dass das Dokument geändert wurde.|

## <a name="remarks"></a>Bemerkungen

Eine Sicht wird an ein Dokument angefügt und fungiert als Vermittler zwischen dem Dokument und dem Benutzer: die Ansicht rendert ein Bild des Dokuments auf dem Bildschirm oder Drucker und interpretiert Benutzereingaben als Vorgänge auf dem Dokument.

Eine Ansicht ist ein untergeordnetes Element eines Rahmen Fensters. Mehr als eine Sicht kann ein Rahmen Fenster gemeinsam verwenden, wie im Fall eines Splitter Fensters. Die Beziehung zwischen einer Ansichts Klasse, einer Rahmen Fenster Klasse und einer Dokument Klasse wird von einem `CDocTemplate` Objekt hergestellt. Wenn der Benutzer ein neues Fenster öffnet oder ein vorhandenes Fenster teilt, erstellt das Framework eine neue Sicht und fügt Sie an das Dokument an.

Eine Sicht kann nur an ein Dokument angefügt werden, aber an ein Dokument können gleichzeitig mehrere Ansichten angefügt werden – z. b., wenn das Dokument in einem Splitter Fenster oder in mehreren untergeordneten Fenstern in einer MDI-Anwendung (Multiple Document Interface) angezeigt wird. Die Anwendung kann unterschiedliche Typen von Sichten für einen bestimmten Dokumenttyp unterstützen. Beispielsweise kann ein Textverarbeitungsprogramm eine vollständige Textansicht eines Dokuments und eine Gliederungs Ansicht bereitstellen, in der nur die Abschnittsüberschriften angezeigt werden. Diese unterschiedlichen Sicht Typen können in separaten Rahmen Fenstern oder in separaten Bereichen eines einzelnen Rahmen Fensters platziert werden, wenn Sie ein Splitter Fenster verwenden.

Eine Sicht ist möglicherweise für die Verarbeitung verschiedener Typen von Eingaben zuständig, wie z. b. Tastatureingaben, Maus Eingaben oder Eingaben per Drag & Drop sowie Befehle aus Menüs, Symbolleisten oder Scrollleisten. Eine Sicht empfängt Befehle, die über das Rahmen Fenster weitergeleitet werden. Wenn die Ansicht einen angegebenen Befehl nicht behandelt, leitet Sie den Befehl an das zugehörige Dokument weiter. Wie alle Befehls Ziele verarbeitet eine Ansicht Nachrichten über eine Meldungs Zuordnung.

Die Sicht ist dafür verantwortlich, die Daten des Dokuments anzuzeigen und zu ändern, aber nicht zum Speichern. Das Dokument enthält die Ansicht mit den erforderlichen Details zu seinen Daten. Sie können zulassen, dass die Ansicht direkt auf die Datenmember des Dokuments zugreift, oder Sie können Element Funktionen in der Document-Klasse bereitstellen, um die Ansichts Klasse aufzurufen.

Wenn sich die Daten eines Dokuments ändern, ruft die für die Änderungen verantwortliche Sicht in der Regel die [CDocument:: UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) -Funktion für das Dokument auf, das alle anderen Ansichten benachrichtigt, indem die `OnUpdate` Member-Funktion für jede aufgerufen wird. Die Standard Implementierung von `OnUpdate` den gesamten Client Bereich der Ansicht für ungültig erklären. Sie können Sie außer Kraft setzen, sodass nur die Regionen des Client Bereichs ungültig werden, die den geänderten Teilen des Dokuments zugeordnet sind.

Um `CView`zu verwenden, leiten Sie eine Klasse davon ab, und implementieren Sie die `OnDraw` Member-Funktion, um die Bildschirm Anzeige auszuführen. Sie können auch `OnDraw` verwenden, um die Druck-und Druckvorschau auszuführen. Das Framework verarbeitet die Druck Schleife, um das Dokument zu drucken und in der Vorschau anzuzeigen.

In einer Ansicht werden Bild Lauf leisten Meldungen mit den Element Funktionen [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) und [CWnd:: OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) behandelt. Sie können die Meldungs Behandlung für die Scrollleiste in diesen Funktionen implementieren, oder Sie können die von `CView` abgeleitete Klasse [CScrollView](../../mfc/reference/cscrollview-class.md) verwenden, um den Bildlauf für Sie zu verarbeiten.

Neben `CScrollView`stellt die Microsoft Foundation Class-Bibliothek neun andere Klassen bereit, die von `CView`abgeleitet sind:

- [Cctrlview](../../mfc/reference/cctrlview-class.md), eine Ansicht, die die Verwendung der Dokument-/Ansichtsarchitektur mit Struktur-, Listen-und Rich-Edit-Steuerelementen ermöglicht.

- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md), eine Ansicht, in der Datenbankdaten Sätze in Dialogfeld-Steuerelementen angezeigt werden.

- [CEditView](../../mfc/reference/ceditview-class.md), eine Ansicht, die einen einfachen mehrzeiligen Text-Editor bereitstellt. Sie können ein `CEditView` Objekt als Steuerelement in einem Dialogfeld sowie eine Ansicht in einem Dokument verwenden.

- [CFormView](../../mfc/reference/cformview-class.md), eine Bild lauffähigen Sicht, die Dialogfeld-Steuerelemente enthält und auf einer Dialogfeld Vorlagen Ressource basiert.

- [CListView](../../mfc/reference/clistview-class.md), eine Ansicht, die die Verwendung der Dokument-/Ansichtsarchitektur mit Listen Steuerelementen ermöglicht.

- [CRecordView](../../mfc/reference/crecordview-class.md), eine Ansicht, in der Datenbankdaten Sätze in Dialogfeld-Steuerelementen angezeigt werden.

- [CRichEditView](../../mfc/reference/cricheditview-class.md), eine Ansicht, die die Verwendung der Dokument-/Ansichtsarchitektur mit Rich-Edit-Steuerelementen ermöglicht.

- [CScrollView](../../mfc/reference/cscrollview-class.md), eine Ansicht, die automatisch Scrollunterstützung bereitstellt.

- [CTreeView](../../mfc/reference/ctreeview-class.md), eine Ansicht, die die Verwendung der Dokument-/Ansichtsarchitektur mit Struktur Steuerelementen ermöglicht.

Die `CView`-Klasse verfügt auch über eine abgeleitete Implementierungs Klasse mit dem Namen `CPreviewView`, die vom Framework verwendet wird, um die Druckvorschau auszuführen. Diese Klasse bietet Unterstützung für die Features, die für das Fenster "Druckvorschau" eindeutig sind, wie z. b. eine Symbolleiste, eine Einzel-oder eine Doppelseiten Vorschau und Zoomen, d. h. die Vergrößerung des Vorschau Bilds. Sie müssen keine der Element Funktionen von `CPreviewView`anrufen oder außer Kraft setzen, es sei denn, Sie möchten eine eigene Schnittstelle für die Seitenansicht implementieren (z. b. Wenn Sie die Bearbeitung im Seiten Ansichtsmodus unterstützen möchten). Weitere Informationen zur Verwendung von `CView`finden Sie unter [Dokument-/Ansichtarchitektur](../../mfc/document-view-architecture.md) und [Drucken](../../mfc/printing.md). Weitere Informationen zum Anpassen der Druckvorschau finden Sie außerdem unter [Technical Note 30](../../mfc/tn030-customizing-printing-and-print-preview.md) .

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CView`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

##  <a name="cview"></a>CView:: CView

Erstellt ein `CView`-Objekt.

```
CView();
```

### <a name="remarks"></a>Bemerkungen

Das Framework ruft den Konstruktor auf, wenn ein neues Rahmen Fenster erstellt oder ein Fenster geteilt wird. Überschreiben Sie die [OnInitialUpdate](#oninitialupdate) -Member-Funktion, um die Sicht zu initialisieren, nachdem das Dokument angefügt wurde.

##  <a name="doprepareprinting"></a>CView::D oprepareprinting

Rufen Sie diese Funktion aus der außer Kraft Setzung von [OnPreparePrinting](#onprepareprinting) auf, um das Dialogfeld Drucken aufzurufen und einen Drucker Gerätekontext zu erstellen.

```
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parameter

*pinfo*<br/>
Verweist auf eine [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) -Struktur, die den aktuellen Druckauftrag beschreibt.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn Druck-oder Druckvorschau beginnen kann. 0, wenn der Vorgang abgebrochen wurde.

### <a name="remarks"></a>Bemerkungen

Das Verhalten dieser Funktion hängt davon ab, ob Sie für Druck-oder Druckvorschau aufgerufen wird (angegeben durch den `m_bPreview` Member des *pinfo* -Parameters). Wenn eine Datei gedruckt wird, ruft diese Funktion das Dialogfeld Drucken auf, wobei die Werte in der [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) -Struktur verwendet werden, auf die *pinfo* zeigt. Nachdem der Benutzer das Dialogfeld geschlossen hat, erstellt die Funktion einen Drucker Gerätekontext basierend auf den Einstellungen, die der Benutzer im Dialogfeld angegeben hat, und gibt diesen Gerätekontext über den *pinfo* -Parameter zurück. Dieser Gerätekontext wird verwendet, um das Dokument zu drucken.

Wenn eine Datei in der Vorschau angezeigt wird, erstellt diese Funktion einen Drucker Gerätekontext mithilfe der aktuellen Druckereinstellungen. dieser Gerätekontext wird zum Simulieren des Druckers während der Vorschau verwendet.

##  <a name="getdocument"></a>CView:: GetDocument

Mit dieser Funktion können Sie einen Zeiger auf das Dokument der Ansicht abrufen.

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das [CDocument](../../mfc/reference/cdocument-class.md) -Objekt, das der Ansicht zugeordnet ist. NULL, wenn die Sicht nicht an ein Dokument angefügt ist.

### <a name="remarks"></a>Bemerkungen

Dies ermöglicht es Ihnen, die Element Funktionen des Dokuments aufzurufen.

##  <a name="isselected"></a>CView:: issgewählt

Wird von Framework aufgerufen, um zu überprüfen, ob das angegebene Dokument Element ausgewählt ist.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Parameter

*pdocitem*<br/>
Verweist auf das Dokument Element, das getestet wird.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das angegebene Dokument Element ausgewählt ist. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Standard Implementierung dieser Funktion gibt false zurück. Überschreiben Sie diese Funktion, wenn Sie die Auswahl mit [CDocItem](../../mfc/reference/cdocitem-class.md) -Objekten implementieren. Sie müssen diese Funktion überschreiben, wenn die Ansicht OLE-Elemente enthält.

##  <a name="onactivateframe"></a>CView:: onactivateframe

Wird von Framework aufgerufen, wenn das Rahmen Fenster, das die Ansicht enthält, aktiviert oder deaktiviert wird.

```
virtual void OnActivateFrame(
    UINT nState,
    CFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Parameter

*nstatusinformationen*<br/>
Gibt an, ob das Rahmen Fenster aktiviert oder deaktiviert wird. Es kann sich um einen der folgenden Werte handeln:

- WA_INACTIVE das Rahmen Fenster deaktiviert wird.

- WA_ACTIVE das Rahmen Fenster durch eine andere Methode als einen Mausklick aktiviert wird (z. b. durch Verwendung der Tastaturschnittstelle zum Auswählen des Fensters).

- WA_CLICKACTIVE das Rahmen Fenster durch einen Mausklick aktiviert wird.

*pframewnd*<br/>
Zeiger auf das Rahmen Fenster, das aktiviert werden soll.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Member-Funktion, wenn Sie eine besondere Verarbeitung durchführen möchten, wenn das der Ansicht zugeordnete Rahmen Fenster aktiviert oder deaktiviert wird. [CFormView](../../mfc/reference/cformview-class.md) führt diese außer Kraft Setzung beispielsweise aus, wenn das Steuerelement, das den Fokus besitzt, gespeichert und wieder hergestellt wird.

##  <a name="onactivateview"></a>CView:: OnActivateView

Wird von Framework aufgerufen, wenn eine Ansicht aktiviert oder deaktiviert wird.

```
virtual void OnActivateView(
    BOOL bActivate,
    CView* pActivateView,
    CView* pDeactiveView);
```

### <a name="parameters"></a>Parameter

*bactivate*<br/>
Gibt an, ob die Ansicht aktiviert oder deaktiviert wird.

*pactivateview*<br/>
Verweist auf das Ansichts Objekt, das aktiviert wird.

*pdebug-View*<br/>
Verweist auf das Ansichts Objekt, das deaktiviert wird.

### <a name="remarks"></a>Bemerkungen

Mit der Standard Implementierung dieser Funktion wird der Fokus auf die Ansicht festgelegt, die aktiviert wird. Überschreiben Sie diese Funktion, wenn Sie eine besondere Verarbeitung durchführen möchten, wenn eine Ansicht aktiviert oder deaktiviert wird. Wenn Sie beispielsweise besondere visuelle Hinweise bereitstellen möchten, die die aktive Ansicht von den inaktiven Ansichten unterscheiden, überprüfen Sie den *bactivate* -Parameter und aktualisieren die Darstellung der Ansicht entsprechend.

Die Parameter *pactivateview* und *pdeactiveview* zeigen auf dieselbe Sicht, wenn das Hauptrahmen Fenster der Anwendung ohne Änderung in der aktiven Ansicht aktiviert wird – z. b. wenn der Fokus von einer anderen Anwendung in diese Datei übertragen wird, nicht von einer Ansicht in eine andere in der Anwendung oder beim Wechsel zwischen untergeordneten MDI-Fenstern. Dies ermöglicht es einer Ansicht, die Palette bei Bedarf wieder zu erkennen.

Diese Parameter unterscheiden sich, wenn [CFrameWnd:: abtactiveview](../../mfc/reference/cframewnd-class.md#setactiveview) mit einer Ansicht aufgerufen wird, die sich von der Rückgabe von [CFrameWnd:: GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview) unterscheidet. Dies tritt am häufigsten bei Splitter Fenstern auf.

##  <a name="onbeginprinting"></a>CView:: OnBeginPrinting

Wird zu Beginn eines Druckauftrags oder Seitenansichtauftrags vom Framework aufgerufen, nachdem `OnPreparePrinting` aufgerufen wurde.

```
virtual void OnBeginPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Verweist auf den Druckergerätekontext.

*pinfo*<br/>
Verweist auf eine [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) -Struktur, die den aktuellen Druckauftrag beschreibt.

### <a name="remarks"></a>Bemerkungen

Bei der Standardimplementierung dieser Funktion wird keine Aktion ausgeführt. Überschreiben Sie diese Funktion, um alle speziell für den Druck benötigten GDI-Ressourcen, z. B. Stifte oder Schriftarten, zuzuordnen. Wählen Sie die GDI-Objekte für den Gerätekontext aus der [OnPrint](#onprint) -Memberfunktion für jede Seite auf, von der sie verwendet werden. Wenn Sie das gleiche Ansichtsobjekt verwenden, um den Bildschirm anzuzeigen und zu drucken, verwenden Sie separate Variablen für die für jeden Bildschirm erforderlichen GDI-Ressourcen. Dadurch können Sie den Bildschirm während des Druckens aktualisieren.

Mit dieser Funktion können Sie auch Initialisierungen durchführen, die von Eigenschaften des Druckergerätekontextes abhängig sind. Beispielsweise kann die Anzahl der Seiten, die zum Drucken des Dokuments benötigt werden, von den Einstellungen abhängig sein, die der Benutzer im Dialogfeld „Drucken“ (z. B. Seitenlänge) angibt. In einem solchen Fall können Sie die Länge des Dokuments nicht wie normalerweise in der [OnPreparePrinting](#onprepareprinting) -Memberfunktion angeben; Sie müssen warten, bis der Druckergerätekontext basierend auf den Einstellungen des Dialogfelds erstellt wurde. [OnBeginPrinting](#onbeginprinting) ist die erste überschreibbare Funktion, die Ihnen sofortigen Zugriff auf das [CDC](../../mfc/reference/cdc-class.md) -Objekt gibt, das den Druckergerätekontext darstellt, daher können Sie die Länge des Dokuments mithilfe dieser Funktion festlegen. Wenn die Länge des Dokuments nicht zu diesem Zeitpunkt angegeben wird, wird in der Seitenansicht keine Bildlaufleiste angezeigt.

##  <a name="ondragenter"></a>CView:: OnDragEnter

Wird von Framework aufgerufen, wenn der Mauszeiger zum ersten Mal in den nicht-scrollbereich des Ablage Zielfensters wechselt.

```
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parameter

*pDataObject*<br/>
Verweist auf das [COleDataObject](../../mfc/reference/coledataobject-class.md) , das in den Ablage Bereich der Ansicht gezogen wird.

*dwkeystate*<br/>
Enthält den Zustand der Modifizierertasten. Dies ist eine Kombination aus einer beliebigen Anzahl von folgenden: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON und MK_RBUTTON.

*Punkt*<br/>
Die aktuelle Mausposition relativ zum Client Bereich der Ansicht.

### <a name="return-value"></a>Rückgabewert

Ein Wert aus dem enumerierten drogffect-Typ, der den Typ des Ablage Werts angibt, der auftritt, wenn der Benutzer das Objekt an dieser Position abgelegt hat. Der Typ von Drop hängt in der Regel vom aktuellen Schlüssel Zustand ab, der von *dwkeystate*angegeben wird. Eine Standard Zuordnung von KeyStates zu dropffect-Werten lautet:

- DROPEFFECT_NONE das Datenobjekt kann in diesem Fenster nicht gelöscht werden.

- DROPEFFECT_LINK für MK_CONTROL &#124; MK_SHIFT eine Verknüpfung zwischen dem Objekt und seinem Server erstellt.

- DROPEFFECT_COPY für MK_CONTROL erstellt eine Kopie des gelöschten Objekts.

- DROPEFFECT_MOVE für MK_ALT erstellt eine Kopie des gelöschten Objekts und löscht das ursprüngliche Objekt. Dies ist normalerweise der Standard-Drop-Effekt, wenn die Sicht dieses Datenobjekt akzeptieren kann.

Weitere Informationen finden Sie unter MFC Advanced Concepts Sample [OCLIENT](../../overview/visual-cpp-samples.md).

### <a name="remarks"></a>Bemerkungen

Die Standard Implementierung besteht darin, nichts zu tun und DROPEFFECT_NONE zurückzugeben.

Überschreiben Sie diese Funktion, um zukünftige Aufrufe der [OnDragOver](#ondragover) -Member-Funktion vorzubereiten. Alle Daten, die vom Datenobjekt benötigt werden, sollten zu diesem Zeitpunkt für die spätere Verwendung in der `OnDragOver` Member-Funktion abgerufen werden. Die Ansicht sollte auch zu diesem Zeitpunkt aktualisiert werden, um dem Benutzer visuelles Feedback zu geben. Weitere Informationen finden Sie im Artikel [OLE Drag & Drop: Implementieren eines Ablage Ziels](../../mfc/drag-and-drop-ole.md#implement-a-drop-target).

##  <a name="ondragleave"></a>CView:: OnDragLeave

Wird von Framework während eines Zieh Vorgangs aufgerufen, wenn die Maus aus dem gültigen Ablage Bereich für dieses Fenster verschoben wird.

```
virtual void OnDragLeave();
```

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, wenn die aktuelle Ansicht alle Aktionen bereinigen muss, die bei [OnDragEnter](#ondragenter) -oder [OnDragOver](#ondragover) -aufrufen ausgeführt werden, z. b. das Entfernen aller visuellen Benutzer Feedback, während das Objekt gezogen und abgelegt wurde.

##  <a name="ondragover"></a>CView:: OnDragOver

Wird von Framework während eines Zieh Vorgangs aufgerufen, wenn die Maus über das Ablage Zielfenster bewegt wird.

```
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parameter

*pDataObject*<br/>
Verweist auf das [COleDataObject](../../mfc/reference/coledataobject-class.md) , das über das Ablage Ziel gezogen wird.

*dwkeystate*<br/>
Enthält den Zustand der Modifizierertasten. Dies ist eine Kombination aus einer beliebigen Anzahl von folgenden: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON und MK_RBUTTON.

*Punkt*<br/>
Die aktuelle Mausposition relativ zum Ansichts Client Bereich.

### <a name="return-value"></a>Rückgabewert

Ein Wert aus dem enumerierten drogffect-Typ, der den Typ des Ablage Werts angibt, der auftritt, wenn der Benutzer das Objekt an dieser Position abgelegt hat. Der Typ von Drop hängt häufig vom aktuellen Schlüssel Zustand ab, wie von *dwkeystate*angegeben. Eine Standard Zuordnung von KeyStates zu dropffect-Werten lautet:

- DROPEFFECT_NONE das Datenobjekt kann in diesem Fenster nicht gelöscht werden.

- DROPEFFECT_LINK für MK_CONTROL &#124; MK_SHIFT eine Verknüpfung zwischen dem Objekt und seinem Server erstellt.

- DROPEFFECT_COPY für MK_CONTROL erstellt eine Kopie des gelöschten Objekts.

- DROPEFFECT_MOVE für MK_ALT erstellt eine Kopie des gelöschten Objekts und löscht das ursprüngliche Objekt. Dies ist normalerweise der Standard-Drop-Effekt, wenn die Sicht das Datenobjekt akzeptieren kann.

Weitere Informationen finden Sie unter MFC Advanced Concepts Sample [OCLIENT](../../overview/visual-cpp-samples.md).

### <a name="remarks"></a>Bemerkungen

Die Standard Implementierung besteht darin, nichts zu tun und DROPEFFECT_NONE zurückzugeben.

Überschreiben Sie diese Funktion, um dem Benutzer während des Zieh Vorgangs visuelles Feedback zu geben. Da diese Funktion kontinuierlich aufgerufen wird, sollte jeglicher darin enthaltener Code so weit wie möglich optimiert werden. Weitere Informationen finden Sie im Artikel [OLE Drag & Drop: Implementieren eines Ablage Ziels](../../mfc/drag-and-drop-ole.md#implement-a-drop-target).

##  <a name="ondragscroll"></a>CView:: ondragscroll

Wird vom Framework aufgerufen, bevor [OnDragEnter](#ondragenter) oder [OnDragOver](#ondragover) aufgerufen wird, um zu bestimmen, ob sich der Punkt im scrollbereich befindet.

```
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parameter

*dwkeystate*<br/>
Enthält den Zustand der Modifizierertasten. Dies ist eine Kombination aus einer beliebigen Anzahl von folgenden: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON und MK_RBUTTON.

*Punkt*<br/>
Enthält die Position des Cursors relativ zum Bildschirm in Pixel.

### <a name="return-value"></a>Rückgabewert

Ein Wert aus dem enumerierten drogffect-Typ, der den Typ des Ablage Werts angibt, der auftritt, wenn der Benutzer das Objekt an dieser Position abgelegt hat. Der Typ von Drop hängt in der Regel vom aktuellen Schlüssel Zustand ab, der von *dwkeystate*angegeben wird. Eine Standard Zuordnung von KeyStates zu dropffect-Werten lautet:

- DROPEFFECT_NONE das Datenobjekt kann in diesem Fenster nicht gelöscht werden.

- DROPEFFECT_LINK für MK_CONTROL &#124; MK_SHIFT eine Verknüpfung zwischen dem Objekt und seinem Server erstellt.

- DROPEFFECT_COPY für MK_CONTROL erstellt eine Kopie des gelöschten Objekts.

- DROPEFFECT_MOVE für MK_ALT erstellt eine Kopie des gelöschten Objekts und löscht das ursprüngliche Objekt.

- DROPEFFECT_SCROLL gibt an, dass ein Drag Scroll-Vorgang im Begriff ist oder in der Ziel Ansicht auftritt.

Weitere Informationen finden Sie unter MFC Advanced Concepts Sample [OCLIENT](../../overview/visual-cpp-samples.md).

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, wenn Sie ein spezielles Verhalten für dieses Ereignis bereitstellen möchten. Die Standard Implementierung führt automatisch einen Bildlauf zwischen Fenstern durch, wenn der Cursor in den Standardbild Laufbereich innerhalb des Rahmens der einzelnen Fenster gezogen wird. Weitere Informationen finden Sie im Artikel [OLE Drag & Drop: Implementieren eines Ablage Ziels](../../mfc/drag-and-drop-ole.md#implement-a-drop-target).

##  <a name="ondraw"></a>CView:: OnDraw

Wird von Framework aufgerufen, um ein Bild des Dokuments zu erzeugen.

```
virtual void OnDraw(CDC* pDC) = 0;
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Zeigt auf den Gerätekontext, der zum Rendern eines Bilds des Dokuments verwendet werden soll.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Funktion auf, um Bildschirm Anzeige, Druck und Druckvorschau auszuführen, und übergibt in jedem Fall einen anderen Gerätekontext. Es ist keine Standardimplementierung vorhanden.

Sie müssen diese Funktion überschreiben, um die Ansicht des Dokuments anzuzeigen. Sie können GDI (Graphic Device Interface)-Aufrufe mithilfe des [CDC](../../mfc/reference/cdc-class.md) -Objekts durchführen, auf das der *PDC* -Parameter verweist. Sie können GDI-Ressourcen, z. b. Stifte oder Schriftarten, vor dem Zeichnen in den Gerätekontext auswählen und diese anschließend deaktivieren. Häufig kann der Zeichnungs Code Geräte unabhängig sein. Dies bedeutet, dass keine Informationen über den Typ des Geräts erforderlich sind, das das Bild anzeigt.

Um das Zeichnen zu optimieren, müssen Sie die Funktion " [rectvisible](../../mfc/reference/cdc-class.md#rectvisible) Member" des Geräte Kontexts abrufen, um herauszufinden, ob ein bestimmtes Rechteck gezeichnet wird. Wenn Sie zwischen normaler Bildschirm Anzeige und Druck unterscheiden müssen, müssen Sie die [IsPrinting](../../mfc/reference/cdc-class.md#isprinting) -Member-Funktion des Geräte Kontexts aufrufen.

##  <a name="ondrop"></a>CView:: OnDrop

Wird von Framework aufgerufen, wenn der Benutzer ein Datenobjekt über ein gültiges Ablage Ziel freigibt.

```
virtual BOOL OnDrop(
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>Parameter

"pdataobject *" verweist auf das [COleDataObject](../../mfc/reference/coledataobject-class.md) , das in das Ablage Ziel abgelegt wird.

*dropffect*<br/>
Der vom Benutzer angeforderte Ablage Effekt.

- DROPEFFECT_COPY erstellt eine Kopie des Datenobjekts, das gelöscht wird.

- DROPEFFECT_MOVE verschiebt das Datenobjekt an die aktuelle Mausposition.

- DROPEFFECT_LINK erstellt eine Verknüpfung zwischen einem Datenobjekt und seinem Server.

*Punkt*<br/>
Die aktuelle Mausposition relativ zum Ansichts Client Bereich.

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn der Löschvorgang erfolgreich war. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Standard Implementierung führt keine Aktion aus und gibt false zurück.

Überschreiben Sie diese Funktion, um die Auswirkung einer OLE-Ablage in den Client Bereich der Ansicht zu implementieren. Das Datenobjekt kann über *pdataobject* für Zwischenablage Datenformate und Daten untersucht werden, die am angegebenen Punkt abgelegt werden.

> [!NOTE]
>  Das Framework ruft diese Funktion nicht auf, wenn in dieser Ansichts Klasse eine außer Kraft setzung für [ondropex](#ondropex) vorhanden ist.

##  <a name="ondropex"></a>CView:: ondropex

Wird von Framework aufgerufen, wenn der Benutzer ein Datenobjekt über ein gültiges Ablage Ziel freigibt.

```
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Parameter

*pDataObject*<br/>
Verweist auf das [COleDataObject](../../mfc/reference/coledataobject-class.md) , das in das Ablage Ziel abgelegt wird.

*dropDefault*<br/>
Der Effekt, den der Benutzer für den Standard Ablage Vorgang basierend auf dem aktuellen Schlüssel Zustand ausgewählt hat. Möglicherweise ist es DROPEFFECT_NONE. Drop Effects werden im Abschnitt "Hinweise" erläutert.

*droplist*<br/>
Eine Liste der Ablage Effekte, die von der Drop-Quelle unterstützt werden. Drop Effect-Werte können mithilfe des bitweisen or ( **&#124;** )-Vorgangs kombiniert werden. Drop Effects werden im Abschnitt "Hinweise" erläutert.

*Punkt*<br/>
Die aktuelle Mausposition relativ zum Ansichts Client Bereich.

### <a name="return-value"></a>Rückgabewert

Der Ablage Effekt, der aus dem Drop-Versuch an der durch *Punkt*angegebenen Position resultiert. Dies muss einer der Werte sein, die von *dropeer ffectlist*angegeben werden. Drop Effects werden im Abschnitt "Hinweise" erläutert.

### <a name="remarks"></a>Bemerkungen

Die Standard Implementierung besteht darin, nichts zu tun und einen Dummywert (-1) zurückzugeben, um anzugeben, dass das Framework den [OnDrop](#ondrop) -Handler aufruft.

Überschreiben Sie diese Funktion, um die Auswirkung einer Drag & Drop-Taste mit der rechten Maustaste zu implementieren. Mit der rechten Maustaste per Drag & Drop wird in der Regel ein Menü mit Auswahlmöglichkeiten angezeigt, wenn die Rechte Maustaste losgelassen wird.

Die außer Kraft Setzung von `OnDropEx` sollte die Rechte Maustaste Abfragen. Sie können [GetKeyState](/windows/win32/api/winuser/nf-winuser-getkeystate) aufrufen oder den rechten MouseButton-Zustand des [OnDragEnter](#ondragenter) -Handlers speichern.

- Wenn die Rechte Maustaste gedrückt ist, sollte bei der außer Kraft Setzung ein Popup Menü angezeigt werden, das die Unterstützung von Drop-Effekten durch die Ablage Quelle bietet.

   - Untersuchen Sie *droplist* , um die von der Ablage Quelle unterstützten Ablage Effekte zu ermitteln. Aktivieren Sie nur diese Aktionen im Popupmenü.

   - Verwenden Sie [setmenudefaultitem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem) , um die Standardaktion basierend auf *dropdefault*festzulegen.

   - Führen Sie abschließend die durch die Benutzer Auswahl im Popupmenü angezeigten Aktionen aus.

- Wenn die Rechte Maustaste nicht angezeigt wird, sollte Ihre außer Kraft Setzung dies als Standard-Drop Request verarbeiten. Verwenden Sie den in *dropdefault*angegebenen Ablage Effekt. Alternativ kann die Überschreibung den Dummy-Wert zurückgeben (-1), um anzugeben, dass `OnDrop` diesen Drop-Vorgang behandelt.

Verwenden Sie *pdataobject* , um die `COleDataObject` für das Datenformat der Zwischenablage und die am angegebenen Punkt abgelegten Daten zu untersuchen.

Drop Effects beschreibt die Aktion, die einem Drop-Vorgang zugeordnet ist. Weitere Informationen finden Sie in der folgenden Dropdown Liste:

- DROPEFFECT_NONE Drop wäre nicht zulässig.

- DROPEFFECT_COPY ein Kopiervorgang ausgeführt wird.

- DROPEFFECT_MOVE ein Verschiebe Vorgang ausgeführt wird.

- DROPEFFECT_LINK eine Verknüpfung von den gelöschten Daten zu den ursprünglichen Daten erstellt werden.

- DROPEFFECT_SCROLL gibt an, dass ein Drag-Scroll-Vorgang stattfindet oder im Ziel auftritt.

Weitere Informationen zum Festlegen des Standardmenü Befehls finden Sie unter [setmenudefaultitem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem) in den Windows SDK und [CMenu:: gezafehmenu](../../mfc/reference/cmenu-class.md#getsafehmenu) in diesem Volume.

##  <a name="onendprinting"></a>CView:: OnEndPrinting

Wird von Framework aufgerufen, nachdem ein Dokument gedruckt oder in der Vorschau angezeigt wurde.

```
virtual void OnEndPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Verweist auf den Druckergerätekontext.

*pinfo*<br/>
Verweist auf eine [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) -Struktur, die den aktuellen Druckauftrag beschreibt.

### <a name="remarks"></a>Bemerkungen

Bei der Standardimplementierung dieser Funktion wird keine Aktion ausgeführt. Überschreiben Sie diese Funktion, um GDI-Ressourcen freizugeben, die Sie in der [OnBeginPrinting](#onbeginprinting) -Element Funktion zugewiesen haben.

##  <a name="onendprintpreview"></a>CView:: onendprintpreview

Wird von Framework aufgerufen, wenn der Benutzer den Druckvor Schau Modus beendet.

```
virtual void OnEndPrintPreview(
    CDC* pDC,
    CPrintInfo* pInfo,
    POINT point,
    CPreviewView* pView);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Verweist auf den Druckergerätekontext.

*pinfo*<br/>
Verweist auf eine [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) -Struktur, die den aktuellen Druckauftrag beschreibt.

*Punkt*<br/>
Gibt den Punkt auf der Seite an, der zuletzt im Vorschaumodus angezeigt wurde.

*pView*<br/>
Verweist auf das Ansichts Objekt, das für die Vorschau verwendet wird.

### <a name="remarks"></a>Bemerkungen

Die Standard Implementierung dieser Funktion Ruft die [OnEndPrinting](#onendprinting) -Member-Funktion auf und stellt das Hauptrahmen Fenster in dem Zustand wieder her, in dem Sie sich vor Beginn der Druckvorschau befand. Überschreiben Sie diese Funktion, um eine besondere Verarbeitung auszuführen, wenn der Vorschaumodus beendet wird. Wenn Sie z. b. die Position des Benutzers im Dokument beim Wechsel vom Vorschaumodus in den normalen Anzeigemodus beibehalten möchten, können Sie einen Bildlauf zu der durch den *Punkt* Parameter beschriebenen Position durchführen und den `m_nCurPage` Member der `CPrintInfo` Struktur, auf die der *pinfo* -Parameter verweist.

Nennen Sie immer die Basisklassen Version von `OnEndPrintPreview` von der außer Kraft Setzung aus, in der Regel am Ende der Funktion.

##  <a name="oninitialupdate"></a>CView:: OnInitialUpdate

Wird von Framework aufgerufen, nachdem die Ansicht zum ersten Mal an das Dokument angefügt wurde, aber bevor die Ansicht anfänglich angezeigt wird.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Bemerkungen

Die Standard Implementierung dieser Funktion Ruft die [OnUpdate](#onupdate) -Member-Funktion ohne Hinweis Informationen auf (d. h. mit den Standardwerten 0 für den *lHint* -Parameter und NULL für den Parameter " *phint* "). Überschreiben Sie diese Funktion, um eine einmalige Initialisierung durchzuführen, die Informationen über das Dokument erfordert. Wenn Ihre Anwendung z. b. Dokumente mit fester Größe enthält, können Sie diese Funktion verwenden, um die scrolllimits einer Ansicht basierend auf der Dokument Größe zu initialisieren. Wenn Ihre Anwendung Dokumente variabler Größe unterstützt, verwenden Sie [OnUpdate](#onupdate) , um die scrolllimits bei jeder Änderung des Dokuments zu aktualisieren.

##  <a name="onpreparedc"></a>CView:: OnPrepareDC

Wird von Framework aufgerufen, bevor die [OnDraw](#ondraw) -Member-Funktion für die Bildschirm Anzeige aufgerufen wird und bevor die [OnPrint](#onprint) -Member-Funktion für jede Seite während des Druckens oder der Druckvorschau aufgerufen wird.

```
virtual void OnPrepareDC(
    CDC* pDC,
    CPrintInfo* pInfo = NULL);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Zeigt auf den Gerätekontext, der zum Rendern eines Bilds des Dokuments verwendet werden soll.

*pinfo*<br/>
Verweist auf eine [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) -Struktur, die den aktuellen Druckauftrag beschreibt, wenn `OnPrepareDC` für Druck-oder Druckvorschau aufgerufen wird. der `m_nCurPage` Member gibt die Seite an, die gedruckt werden soll. Dieser Parameter ist NULL, wenn `OnPrepareDC` für die Bildschirm Anzeige aufgerufen wird.

### <a name="remarks"></a>Bemerkungen

Die Standard Implementierung dieser Funktion bewirkt nichts, wenn die Funktion für die Bildschirm Anzeige aufgerufen wird. Diese Funktion wird jedoch in abgeleiteten Klassen, wie z. b. [CScrollView](../../mfc/reference/cscrollview-class.md), überschrieben, um Attribute des Geräte Kontexts anzupassen. Folglich sollten Sie immer die Basisklassen Implementierung am Anfang der außer Kraft Setzung abrufen.

Wenn die Funktion zum Drucken aufgerufen wird, werden die im *pinfo* -Parameter gespeicherten Seiten Informationen von der Standard Implementierung überprüft. Wenn die Länge des Dokuments nicht angegeben wurde, nimmt `OnPrepareDC` an, dass das Dokument eine Seite lang ist, und beendet die Druck Schleife, nachdem eine Seite gedruckt wurde. Die-Funktion beendet die Druck Schleife, indem der `m_bContinuePrinting`-Member der-Struktur auf false festgelegt wird.

Überschreiben Sie `OnPrepareDC` aus einem der folgenden Gründe:

- , Um die Attribute des Geräte Kontexts nach Bedarf für die angegebene Seite anzupassen. Wenn Sie z. b. den Zuordnungs Modus oder andere Eigenschaften des Geräte Kontexts festlegen müssen, führen Sie dies in dieser Funktion durch.

- , Um die Druck Zeit Paginierung auszuführen. Normalerweise geben Sie die Länge des Dokuments an, wenn der Druck beginnt, indem Sie die [OnPreparePrinting](#onprepareprinting) -Member-Funktion verwenden. Wenn Sie jedoch nicht im Voraus wissen, wie lange das Dokument ist (z. b. Wenn Sie eine unbestimmte Anzahl von Datensätzen aus einer Datenbank drucken), überschreiben Sie `OnPrepareDC`, um das Ende des Dokuments zu testen, während es gedruckt wird. Wenn das zu druckende Dokument nicht mehr vorhanden ist, legen Sie den `m_bContinuePrinting`-Member der `CPrintInfo`-Struktur auf false fest.

- , Um Escapecodes seitenweise an den Drucker zu senden. Um Escapecodes aus `OnPrepareDC`zu senden, müssen Sie die `Escape` Member-Funktion des *PDC* -Parameters aufrufen.

Nennen Sie die Basisklassen Version von `OnPrepareDC` zu Beginn der außer Kraft Setzung.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]

##  <a name="onprepareprinting"></a>CView:: OnPreparePrinting

Wird von Framework aufgerufen, bevor ein Dokument gedruckt oder in der Vorschau angezeigt wird.

```
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parameter

*pinfo*<br/>
Verweist auf eine [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) -Struktur, die den aktuellen Druckauftrag beschreibt.

### <a name="return-value"></a>Rückgabewert

Nicht NULL, um mit dem Drucken zu beginnen. 0, wenn der Druckauftrag abgebrochen wurde.

### <a name="remarks"></a>Bemerkungen

Bei der Standardimplementierung wird keine Aktion ausgeführt.

Sie müssen diese Funktion überschreiben, um das Drucken und die Seitenansicht zu aktivieren. Nennen Sie die Funktion " [dopparameeprinting](#doprepareprinting) ", übergeben Sie Sie an den *pinfo* -Parameter, und geben Sie dann den Rückgabewert zurück. `DoPreparePrinting` zeigt das Dialogfeld Drucken an und erstellt einen Drucker Gerätekontext. Wenn Sie das Dialogfeld Drucken mit anderen als den Standardwerten initialisieren möchten, weisen Sie den Membern von *pinfo*Werte zu. Wenn Sie z. b. die Länge des Dokuments kennen, übergeben Sie den Wert an die [SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage) -Member-Funktion von *pinfo* , bevor Sie `DoPreparePrinting`aufrufen. Dieser Wert wird im Dialogfeld "Drucken" im Bereich "an:" angezeigt.

in `DoPreparePrinting` wird das Dialogfeld Drucken für einen Vorschau Auftrag nicht angezeigt. Wenn Sie das Dialogfeld Drucken für einen Druckauftrag umgehen möchten, überprüfen Sie, ob das `m_bPreview` Mitglied von *pinfo* false ist, und legen Sie es dann auf true fest, bevor Sie es an `DoPreparePrinting`übergeben. setzen Sie Sie anschließend auf false zurück.

Wenn Sie Initialisierungen ausführen müssen, die Zugriff auf das `CDC` Objekt benötigen, das den Drucker Gerätekontext darstellt (wenn Sie z. b. die Seitengröße kennen müssen, bevor Sie die Länge des Dokuments angeben), überschreiben Sie die `OnBeginPrinting` Member-Funktion.

Wenn Sie den Wert der `m_nNumPreviewPages` oder `m_strPageDesc` Member des *pinfo* -Parameters festlegen möchten, führen Sie dies nach dem Aufrufen von `DoPreparePrinting`durch. Die `DoPreparePrinting` Member-Funktion legt `m_nNumPreviewPages` auf den Wert fest, der in der der Anwendung gefunden wurde. INI-Datei, und legt `m_strPageDesc` auf ihren Standardwert fest.

### <a name="example"></a>Beispiel

  Überschreiben Sie `OnPreparePrinting`, und rufen Sie `DoPreparePrinting` aus der Überschreibung auf, damit das Framework ein Druck Dialogfeld anzeigt und einen Drucker-DC für Sie erstellt.

[!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]

Wenn Sie wissen, wie viele Seiten das Dokument enthält, legen Sie die maximale Seite in `OnPreparePrinting` vor dem Aufrufen von `DoPreparePrinting`fest. Im Rahmen des Frameworks wird im Dialogfeld Drucken die maximale Seitenzahl im Feld "bis" angezeigt.

[!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]

##  <a name="onprint"></a>CView:: OnPrint

Wird von Framework aufgerufen, um eine Seite des Dokuments zu drucken oder eine Vorschau anzuzeigen.

```
virtual void OnPrint(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Verweist auf den Druckergerätekontext.

*pinfo*<br/>
Verweist auf eine `CPrintInfo` Struktur, die den aktuellen Druckauftrag beschreibt.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Funktion für jede gedruckte Seite unmittelbar nach dem Aufruf der [OnPrepareDC](#onpreparedc) -Member-Funktion auf. Die Seite, die gedruckt wird, wird durch den `m_nCurPage` Member der [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) -Struktur angegeben, auf die *pinfo* verweist. Die Standard Implementierung ruft die [OnDraw](#ondraw) -Member-Funktion auf und übergibt sie an den Drucker Gerätekontext.

Überschreiben Sie diese Funktion aus einem der folgenden Gründe:

- , Um das Drucken von mehrseitigen Dokumenten zuzulassen. Rendernur den Teil des Dokuments, der der aktuell gedruckten Seite entspricht. Wenn Sie `OnDraw` zum Rendern verwenden, können Sie den Ansichts Port so anpassen, dass nur der entsprechende Teil des Dokuments gedruckt wird.

- , Damit das gedruckte Bild von der Bildschirm Abbildung abweicht (d. h., wenn die Anwendung nicht WYSIWYG ist). Anstatt den Drucker Gerätekontext an `OnDraw`zu übergeben, verwenden Sie den Gerätekontext zum Rendering eines Bilds mithilfe von Attributen, die nicht auf dem Bildschirm angezeigt werden.

   Wenn Sie GDI-Ressourcen zum Drucken benötigen, die Sie nicht für die Bildschirm Anzeige verwenden, wählen Sie diese vor dem Zeichnen in den Gerätekontext aus, und deaktivieren Sie Sie anschließend. Diese GDI-Ressourcen sollten in [OnBeginPrinting](#onbeginprinting) zugeordnet und in [OnEndPrinting](#onendprinting)veröffentlicht werden.

- Zum Implementieren von Kopf-oder Fußzeilen. Sie können weiterhin `OnDraw` verwenden, um das Rendering durchzuführen, indem Sie den Bereich einschränken, in dem Sie drucken können.

Beachten Sie, dass der `m_rectDraw` Member des *pinfo* -Parameters den druckbaren Bereich der Seite in logischen Einheiten beschreibt.

`OnPrepareDC` in ihrer außer Kraft Setzung `OnPrint`nicht aufzurufen; Das Framework ruft `OnPrepareDC` automatisch auf, bevor er `OnPrint`aufruft.

### <a name="example"></a>Beispiel

Im folgenden finden Sie ein Gerüst für eine überschriebene `OnPrint`-Funktion:

[!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]

Ein weiteres Beispiel finden Sie unter [CRichEditView::P rintinsiderect](../../mfc/reference/cricheditview-class.md#printinsiderect).

##  <a name="onscroll"></a>CView:: OnScroll

Wird von Framework aufgerufen, um zu bestimmen, ob ein Bildlauf möglich ist.

```
virtual BOOL OnScroll(
    UINT nScrollCode,
    UINT nPos,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parameter

*nscrollcode*<br/>
Ein Bild Lauf leisten Code, der die scrollanforderung des Benutzers angibt. Dieser Parameter setzt sich aus zwei Teilen zusammen: einem Byte mit niedriger Reihenfolge, das den Typ des horizontalen Bildlaufs bestimmt, und einem Byte mit hoher Reihenfolge, das den Typ des vertikal auftretenden Bildlaufs bestimmt:

- SB_BOTTOM einen Bildlauf nach unten durch.

- SB_LINEDOWN führt einen Bildlauf nach unten durch.

- SB_LINEUP führt einen Bildlauf nach oben aus.

- SB_PAGEDOWN führt einen Bildlauf nach unten durch.

- SB_PAGEUP Scrollt eine Seite nach oben.

- SB_THUMBTRACK ziehen Sie das Bild Lauf Feld zur angegebenen Position. Die aktuelle Position wird in *NPOs*angegeben.

- SB_TOP einen Bildlauf nach oben durch.

*NPOs*<br/>
Enthält die aktuelle Position des Bild Lauf Felds, wenn der Bild Lauf leisten Code SB_THUMBTRACK ist. Andernfalls wird Sie nicht verwendet. Je nach dem anfänglichen scrollbereich können *NPOs* negativ sein und sollten bei Bedarf in einen **int** -Wert umgewandelt werden.

*bdoscroll*<br/>
Bestimmt, ob die angegebene scrollaktion tatsächlich ausgeführt werden soll. TRUE gibt an, dass der Bildlauf stattfinden soll. Wenn der Wert false ist, sollte kein Bildlauf ausgeführt werden.

### <a name="return-value"></a>Rückgabewert

Wenn *bdoscroll* den Wert true aufweist und die Ansicht tatsächlich einen Bildlauf durchgeführt hat, geben Sie einen Wert ungleich 0 zurück. andernfalls 0. Wenn *bdoscroll* auf false festgelegt ist, geben Sie den Wert zurück, der zurückgegeben wurde, wenn *bdoscroll* true war, auch wenn Sie den Bildlauf nicht tatsächlich durchführen.

### <a name="remarks"></a>Bemerkungen

In einem Fall wird diese Funktion vom Framework aufgerufen, wobei *bdoscroll* auf true festgelegt ist, wenn die Sicht eine Bild Lauf Leiste-Nachricht empfängt. In diesem Fall sollten Sie einen Bildlauf in der Ansicht durchführen. Im anderen Fall wird diese Funktion aufgerufen, wenn *bdoscroll* auf false festgelegt ist, wenn ein OLE-Element anfänglich in den Auto-scrollbereich eines Ablage Ziels gezogen wird, bevor der Bildlauf tatsächlich durchgeführt wird. In diesem Fall sollten Sie den Bildlauf in der Ansicht nicht durchführen.

##  <a name="onscrollby"></a>CView:: onscrollby

Wird von Framework aufgerufen, wenn der Benutzer einen Bereich über der aktuellen Ansicht des Dokuments hinweg anzeigt, indem er ein OLE-Element auf die aktuellen Rahmen der Sicht zieht oder die vertikalen oder horizontalen Scrollleisten bearbeitet.

```
virtual BOOL OnScrollBy(
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parameter

*sizescroll*<br/>
Die Anzahl der Pixel, die horizontal und vertikal gescrollt wurden.

*bdoscroll*<br/>
Bestimmt, ob das Scrollen der Ansicht auftritt. TRUE gibt an, dass der Bildlauf ausgeführt wird. Wenn der Wert false ist, wird kein Bildlauf ausgeführt.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn für die Sicht ein Rollup durchgeführt werden konnte. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

In abgeleiteten Klassen prüft diese Methode, ob die Ansicht in der vom Benutzer angeforderten Richtung scrollfähig ist, und aktualisiert dann ggf. die neue Region. Diese Funktion wird automatisch von [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) und [CWnd:: OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) aufgerufen, um die tatsächliche scrollanforderung auszuführen.

Die Standard Implementierung dieser Methode ändert nicht die Sicht, aber wenn Sie nicht aufgerufen wird, führt die Sicht keinen Bildlauf in einer `CScrollView`-abgeleiteten Klasse aus.

Wenn die Breite oder Höhe des Dokuments 32767 Pixel überschreitet, schlägt der Bildlauf hinter 32767 fehl, da `OnScrollBy` mit einem ungültigen *sizescroll* -Argument aufgerufen wird.

##  <a name="onupdate"></a>CView:: OnUpdate

Wird von Framework aufgerufen, nachdem das Dokument der Ansicht geändert wurde. Diese Funktion wird von [CDocument:: UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) aufgerufen und ermöglicht der Ansicht, die Anzeige zu aktualisieren, um diese Änderungen widerzuspiegeln.

```
virtual void OnUpdate(
    CView* pSender,
    LPARAM lHint,
    CObject* pHint);
```

### <a name="parameters"></a>Parameter

*psender*<br/>
Verweist auf die Ansicht, die das Dokument geändert hat, oder NULL, wenn alle Sichten aktualisiert werden sollen.

*lHint*<br/>
Enthält Informationen zu den Änderungen.

*phint*<br/>
Verweist auf ein Objekt, das Informationen zu den Änderungen speichert.

### <a name="remarks"></a>Bemerkungen

Sie wird auch von der Standard Implementierung von [OnInitialUpdate](#oninitialupdate)aufgerufen. Die Standard Implementierung macht den gesamten Client Bereich ungültig und kennzeichnet ihn für das Zeichnen, wenn die nächste WM_PAINT Nachricht empfangen wird. Überschreiben Sie diese Funktion, wenn Sie nur die Regionen aktualisieren möchten, die den geänderten Teilen des Dokuments zugeordnet sind. Zu diesem Zweck müssen Sie Informationen zu den Änderungen mithilfe der Hint-Parameter übergeben.

Um *lHint*zu verwenden, definieren Sie spezielle Hinweis Werte, in der Regel eine Bitmaske oder einen enumerierten Typ, und lassen Sie das Dokument einen dieser Werte übergeben. Um *phint*zu verwenden, leiten Sie eine Hint-Klasse von [CObject](../../mfc/reference/cobject-class.md) ab, und lassen Sie das Dokument einen Zeiger auf ein Hinweis Objekt übergeben. Wenn Sie `OnUpdate`überschreiben, verwenden Sie die Member-Funktion [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof) , um den Lauf Zeittyp des Hinweis Objekts zu bestimmen.

In der Regel sollten Sie keine Zeichnungen direkt aus `OnUpdate`ausführen. Legen Sie stattdessen das Rechteck fest, das in Geräte Koordinaten den Bereich beschreibt, der aktualisiert werden muss. übergeben Sie dieses Rechteck an [CWnd:: invalidaterier.](../../mfc/reference/cwnd-class.md#invalidaterect) Dies bewirkt, dass das Zeichnen beim nächsten empfangen einer [WM_PAINT](/windows/win32/gdi/wm-paint) Nachricht auftritt.

Wenn der *lHint* -Wert 0 und der *phint* NULL ist, hat das Dokument eine generische Aktualisierungs Benachrichtigung gesendet. Wenn eine Sicht eine generische Update Benachrichtigung empfängt oder die Hinweise nicht decodiert werden können, sollte Sie den gesamten Client Bereich für ungültig erklären.

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[CFrameWnd-Klasse](../../mfc/reference/cframewnd-class.md)<br/>
[CSplitterWnd-Klasse](../../mfc/reference/csplitterwnd-class.md)<br/>
[CDC-Klasse](../../mfc/reference/cdc-class.md)<br/>
[CDocTemplate-Klasse](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument-Klasse](../../mfc/reference/cdocument-class.md)
