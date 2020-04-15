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
ms.openlocfilehash: 763e36b0736ce588e7e2aded25e50347f9e0ca70
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373202"
---
# <a name="cview-class"></a>CView-Klasse

Stellt die grundlegende Funktionalität für benutzerdefinierte Ansichtsklassen bereit.

## <a name="syntax"></a>Syntax

```
class AFX_NOVTABLE CView : public CWnd
```

## <a name="members"></a>Member

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CView::CView](#cview)|Erstellt ein `CView`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CView::DoPreparePrinting](#doprepareprinting)|Zeigt das Dialogfeld Drucken an und erstellt den Kontext des Druckergeräts. beim Überschreiben `OnPreparePrinting` der Memberfunktion aufrufen.|
|[CView::GetDocument](#getdocument)|Gibt das Der Ansicht zugeordnete Dokument zurück.|
|[CView::IsSelected](#isselected)|Testet, ob ein Belegelement ausgewählt ist. Erforderlich für OLE-Unterstützung.|
|[CView::OnDragEnter](#ondragenter)|Wird aufgerufen, wenn ein Element zum ersten Mal in den Drag-and-Drop-Bereich einer Ansicht gezogen wird.|
|[CView::OnDragLeave](#ondragleave)|Wird aufgerufen, wenn ein gezogenes Element den Drag-and-Drop-Bereich einer Ansicht verlässt.|
|[CView::OnDragOver](#ondragover)|Wird aufgerufen, wenn ein Element über den Drag-and-Drop-Bereich einer Ansicht gezogen wird.|
|[CView::OnDragScroll](#ondragscroll)|Wird aufgerufen, um zu bestimmen, ob der Cursor in den Bildlaufbereich des Fensters gezogen wird.|
|[CView::OnDrop](#ondrop)|Wird aufgerufen, wenn ein Element in den Drag-and-Drop-Bereich einer Ansicht, standardhandler, abgelegt wurde.|
|[CView::OnDropEx](#ondropex)|Wird aufgerufen, wenn ein Element in den Drag-and-Drop-Bereich einer Ansicht, dem primären Handler, abgelegt wurde.|
|[CView::OnInitialUpdate](#oninitialupdate)|Wird aufgerufen, nachdem eine Ansicht zuerst an ein Dokument angefügt wurde.|
|[CView::OnPrepareDC](#onpreparedc)|Wird aufgerufen, bevor die `OnDraw` Memberfunktion `OnPrint` für die Bildschirmanzeige oder die Memberfunktion zum Drucken oder Drucken der Vorschau aufgerufen wird.|
|[CView::OnScroll](#onscroll)|Wird aufgerufen, wenn OLE-Elemente über die Grenzen der Ansicht hinausgezogen werden.|
|[CView::OnscrollBy](#onscrollby)|Wird aufgerufen, wenn eine Ansicht mit aktiven, ortsseitig eingerichteten Elementen gescrollt wird.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CView::OnActivateFrame](#onactivateframe)|Wird aufgerufen, wenn das Rahmenfenster, das die Ansicht enthält, aktiviert oder deaktiviert ist.|
|[CView::OnActivateView](#onactivateview)|Wird aufgerufen, wenn eine Ansicht aktiviert ist.|
|[CView::OnBeginPrinting](#onbeginprinting)|Wird aufgerufen, wenn ein Druckauftrag beginnt; überschreiben, um GDI-Ressourcen (Graphics Device Interface) zuzuweisen.|
|[CView::OnDraw](#ondraw)|Wird aufgerufen, um ein Bild des Dokuments für die Bildschirmanzeige, den Druck oder die Druckvorschau zu rendern. Implementierung erforderlich.|
|[CView::OnEndPrinting](#onendprinting)|Wird aufgerufen, wenn ein Druckauftrag endet; um GDI-Ressourcen zu deallocateen.|
|[CView::OnEndPrintPreview](#onendprintpreview)|Wird aufgerufen, wenn der Vorschaumodus beendet wird.|
|[CView::OnPreparePrinting](#onprepareprinting)|Wird aufgerufen, bevor ein Dokument gedruckt oder in der Vorschau angezeigt wird. um das Dialogfeld Drucken zu initialisieren.|
|[CView::OnPrint](#onprint)|Wird aufgerufen, um eine Seite des Dokuments zu drucken oder in der Vorschau anzuzeigen.|
|[CView::OnUpdate](#onupdate)|Wird aufgerufen, um eine Ansicht zu benachrichtigen, dass sein Dokument geändert wurde.|

## <a name="remarks"></a>Bemerkungen

Eine Ansicht ist an ein Dokument angehängt und fungiert als Vermittler zwischen dem Dokument und dem Benutzer: Die Ansicht rendert ein Bild des Dokuments auf dem Bildschirm oder Drucker und interpretiert Benutzereingaben als Vorgänge für das Dokument.

Eine Ansicht ist ein untergeordnetes Element eines Rahmenfensters. Mehr als eine Ansicht kann ein Rahmenfenster gemeinsam nutzen, wie im Fall eines Splitterfensters. Die Beziehung zwischen einer Ansichtsklasse, einer Rahmenfensterklasse und `CDocTemplate` einer Dokumentklasse wird von einem Objekt hergestellt. Wenn der Benutzer ein neues Fenster öffnet oder ein vorhandenes aufteilt, erstellt das Framework eine neue Ansicht und fügt sie an das Dokument an.

Eine Ansicht kann nur einem Dokument zugeordnet werden, aber einem Dokument können mehrere Ansichten gleichzeitig zugeordnet werden, z. B. wenn das Dokument in einem Splitterfenster oder in mehreren untergeordneten Fenstern in einer MDI-Anwendung (Multiple Document Interface) angezeigt wird. Ihre Anwendung kann verschiedene Arten von Ansichten für einen bestimmten Dokumenttyp unterstützen. Beispielsweise kann ein Textverarbeitungsprogramm sowohl eine vollständige Textansicht eines Dokuments als auch eine Gliederungsansicht bereitstellen, in der nur die Abschnittsüberschriften angezeigt werden. Diese verschiedenen Ansichten können in separaten Rahmenfenstern oder in separaten Bereichen eines einzelnen Rahmenfensters platziert werden, wenn Sie ein Splitterfenster verwenden.

Eine Ansicht kann für die Verarbeitung verschiedener Eingabetypen verantwortlich sein, z. B. Tastatureingabe, Mauseingabe oder -eingabe per Drag-and-Drop sowie Befehle aus Menüs, Symbolleisten oder Bildlaufleisten. Eine Ansicht empfängt Befehle, die von ihrem Rahmenfenster weitergeleitet werden. Wenn die Ansicht einen bestimmten Befehl nicht verarbeitet, leitet sie den Befehl an das zugehörige Dokument weiter. Wie alle Befehlsziele verarbeitet eine Ansicht Nachrichten über eine Meldungszuordnung.

Die Ansicht ist für das Anzeigen und Ändern der Dokumentdaten, jedoch nicht für das Speichern verantwortlich. Das Dokument stellt der Ansicht die erforderlichen Details zu seinen Daten zur Verfügung. Sie können die Ansicht direkt auf die Datenmember des Dokuments zugreifen lassen oder Memberfunktionen in der Dokumentklasse bereitstellen, damit die Ansichtsklasse aufrufen kann.

Wenn sich die Daten eines Dokuments ändern, ruft die für die Änderungen verantwortliche Ansicht in der Regel die Funktion `OnUpdate` [CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) für das Dokument auf, die alle anderen Ansichten benachrichtigt, indem die Memberfunktion für jede aufgerufen wird. Die Standardimplementierung `OnUpdate` von macht den gesamten Clientbereich der Ansicht ungültig. Sie können sie überschreiben, um nur die Bereiche des Clientbereichs ungültig zu machen, die den geänderten Teilen des Dokuments zugeordnet sind.

Um `CView`zu verwenden, leiten Sie daraus `OnDraw` eine Klasse ab, und implementieren Sie die Memberfunktion, um die Bildschirmanzeige auszuführen. Sie können `OnDraw` auch zum Drucken und Drucken der Vorschau verwenden. Das Framework verarbeitet die Druckschleife zum Drucken und Anzeigen der Vorschau Des Dokuments.

Eine Ansicht verarbeitet Scrollleistenmeldungen mit den Memberfunktionen [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) und [CWnd::OnVScroll.](../../mfc/reference/cwnd-class.md#onvscroll) Sie können die Bildlaufleisten-Nachrichtenbehandlung in diesen `CView` Funktionen implementieren oder die abgeleitete Klasse [CScrollView](../../mfc/reference/cscrollview-class.md) verwenden, um das Scrollen für Sie zu verarbeiten.

Darüber `CScrollView`hinaus bietet die Microsoft Foundation-Klassenbibliothek neun weitere Klassen, die von `CView`: abgeleitet sind:

- [CCtrlView](../../mfc/reference/cctrlview-class.md), eine Ansicht, die die Verwendung von Dokument- Ansichtsarchitektur mit Struktur-, Listen- und Rich-Edit-Steuerelementen ermöglicht.

- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md), eine Ansicht, die Datenbankdatensätze in Dialogfeldsteuerelementen anzeigt.

- [CEditView](../../mfc/reference/ceditview-class.md), eine Ansicht, die einen einfachen mehrzeiligen Texteditor bereitstellt. Sie können `CEditView` ein Objekt als Steuerelement in einem Dialogfeld sowie als Ansicht eines Dokuments verwenden.

- [CFormView](../../mfc/reference/cformview-class.md), eine bildlauffähige Ansicht, die Dialogfeldsteuerelemente enthält und auf einer Dialogfeldvorlagenressource basiert.

- [CListView](../../mfc/reference/clistview-class.md), eine Ansicht, die die Verwendung von Dokument - Ansichtsarchitektur mit Listensteuerelementen ermöglicht.

- [CRecordView](../../mfc/reference/crecordview-class.md), eine Ansicht, die Datenbankdatensätze in Dialogfeldsteuerelementen anzeigt.

- [CRichEditView](../../mfc/reference/cricheditview-class.md), eine Ansicht, die die Verwendung von Dokument- Ansichtsarchitektur mit umfangreichen Bearbeitungssteuerelementen ermöglicht.

- [CScrollView](../../mfc/reference/cscrollview-class.md), eine Ansicht, die automatisch Scrolling-Unterstützung bietet.

- [CTreeView](../../mfc/reference/ctreeview-class.md), eine Ansicht, die die Verwendung von Dokument - Ansichtsarchitektur mit Struktursteuerelementen ermöglicht.

Die `CView` Klasse verfügt auch über `CPreviewView`eine abgeleitete Implementierungsklasse mit dem Namen , die vom Framework für die Druckvorschau verwendet wird. Diese Klasse bietet Unterstützung für die Features, die für das Druckvorschaufenster einzigartig sind, z. B. eine Symbolleiste, eine ein- oder zweiseitige Vorschau und das Zoomen, d. h. das Vergrößern des in der Vorschau angezeigten Bildes. Sie müssen keine der Mitgliedsfunktionen von `CPreviewView`', es sei denn, Sie möchten eine eigene Schnittstelle für die Druckvorschau implementieren (z. B. wenn Sie die Bearbeitung im Druckvorschaumodus unterstützen möchten). Weitere Informationen zur `CView`Verwendung finden Sie unter [Dokument-/Ansichtsarchitektur](../../mfc/document-view-architecture.md) und [Drucken](../../mfc/printing.md). Weitere Informationen zum Anpassen der Druckvorschau finden Sie unter [Technische Anmerkung 30.](../../mfc/tn030-customizing-printing-and-print-preview.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CView`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="cviewcview"></a><a name="cview"></a>CView::CView

Erstellt ein `CView`-Objekt.

```
CView();
```

### <a name="remarks"></a>Bemerkungen

Das Framework ruft den Konstruktor auf, wenn ein neues Rahmenfenster erstellt oder ein Fenster geteilt wird. Überschreiben Sie die [OnInitialUpdate-Memberfunktion,](#oninitialupdate) um die Ansicht zu initialisieren, nachdem das Dokument angefügt wurde.

## <a name="cviewdoprepareprinting"></a><a name="doprepareprinting"></a>CView::DoPreparePrinting

Rufen Sie diese Funktion über die Außerkraftsetzung von [OnPreparePrinting](#onprepareprinting) auf, um das Dialogfeld Drucken aufzurufen und einen Druckergerätekontext zu erstellen.

```
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parameter

*Pinfo*<br/>
Verweist auf eine [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) -Struktur, die den aktuellen Druckauftrag beschreibt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn der Druck oder die Druckvorschau beginnen kann; 0, wenn der Vorgang abgebrochen wurde.

### <a name="remarks"></a>Bemerkungen

Das Verhalten dieser Funktion hängt davon ab, ob sie zum `m_bPreview` Drucken oder zur Druckvorschau aufgerufen wird (angegeben durch das Element des *Parameters pInfo).* Wenn eine Datei gedruckt wird, ruft diese Funktion das Dialogfeld Drucken auf, wobei die Werte in der [CPrintInfo-Struktur](../../mfc/reference/cprintinfo-structure.md) verwendet werden, auf die *pInfo* verweist. Nachdem der Benutzer das Dialogfeld geschlossen hat, erstellt die Funktion einen Druckergerätekontext basierend auf den Einstellungen, die der Benutzer im Dialogfeld angegeben hat, und gibt diesen Gerätekontext über den Parameter *pInfo* zurück. Dieser Gerätekontext wird zum Drucken des Dokuments verwendet.

Wenn eine Datei in der Vorschau angezeigt wird, erstellt diese Funktion einen Druckergerätekontext mit den aktuellen Druckereinstellungen. Dieser Gerätekontext wird zum Simulieren des Druckers während der Vorschau verwendet.

## <a name="cviewgetdocument"></a><a name="getdocument"></a>CView::GetDocument

Rufen Sie diese Funktion auf, um einen Zeiger auf das Dokument der Ansicht abzurufen.

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das [CDocument-Objekt,](../../mfc/reference/cdocument-class.md) das der Ansicht zugeordnet ist. NULL, wenn die Ansicht nicht an ein Dokument angefügt ist.

### <a name="remarks"></a>Bemerkungen

Auf diese Weise können Sie die Memberfunktionen des Dokuments aufrufen.

## <a name="cviewisselected"></a><a name="isselected"></a>CView::IsSelected

Wird vom Framework aufgerufen, um zu überprüfen, ob das angegebene Dokumentelement ausgewählt ist.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Parameter

*pDocItem*<br/>
Zeigt auf das zu prüfende Dokumentelement.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das angegebene Belegelement ausgewählt ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung dieser Funktion gibt FALSE zurück. Überschreiben Sie diese Funktion, wenn Sie die Auswahl mithilfe von [CDocItem-Objekten](../../mfc/reference/cdocitem-class.md) implementieren. Sie müssen diese Funktion überschreiben, wenn Ihre Ansicht OLE-Elemente enthält.

## <a name="cviewonactivateframe"></a><a name="onactivateframe"></a>CView::OnActivateFrame

Wird vom Framework aufgerufen, wenn das Rahmenfenster, das die Ansicht enthält, aktiviert oder deaktiviert wird.

```
virtual void OnActivateFrame(
    UINT nState,
    CFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Parameter

*nState*<br/>
Gibt an, ob das Rahmenfenster aktiviert oder deaktiviert wird. Es kann sich um einen der folgenden Werte handeln:

- WA_INACTIVE Das Rahmenfenster wird deaktiviert.

- WA_ACTIVE Das Rahmenfenster wird durch eine andere Methode als einen Mausklick aktiviert (z. B. über die Tastaturschnittstelle, um das Fenster auszuwählen).

- WA_CLICKACTIVE Das Rahmenfenster wird per Mausklick aktiviert

*pFrameWnd*<br/>
Zeigen Sie mit dem Zeiger auf das Rahmenfenster, das aktiviert werden soll.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Memberfunktion, wenn Sie eine spezielle Verarbeitung durchführen möchten, wenn das der Ansicht zugeordnete Rahmenfenster aktiviert oder deaktiviert ist. Beispielsweise führt [CFormView](../../mfc/reference/cformview-class.md) diese Außerkraftsetzung aus, wenn das Steuerelement mit Fokus speichert und wiederhergestellt wird.

## <a name="cviewonactivateview"></a><a name="onactivateview"></a>CView::OnActivateView

Wird vom Framework aufgerufen, wenn eine Ansicht aktiviert oder deaktiviert ist.

```
virtual void OnActivateView(
    BOOL bActivate,
    CView* pActivateView,
    CView* pDeactiveView);
```

### <a name="parameters"></a>Parameter

*bAktivieren*<br/>
Gibt an, ob die Ansicht aktiviert oder deaktiviert wird.

*pActivateView*<br/>
Zeigt auf das Ansichtsobjekt, das aktiviert wird.

*pDeactiveView*<br/>
Zeigt auf das Ansichtsobjekt, das deaktiviert wird.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung dieser Funktion legt den Fokus auf die aktivierte Ansicht fest. Überschreiben Sie diese Funktion, wenn Sie eine spezielle Verarbeitung durchführen möchten, wenn eine Ansicht aktiviert oder deaktiviert ist. Wenn Sie z. B. spezielle visuelle Hinweise bereitstellen möchten, die die aktive Ansicht von den inaktiven Ansichten unterscheiden, untersuchen Sie den *Parameter bActivate* und aktualisieren die Darstellung der Ansicht entsprechend.

Die Parameter *pActivateView* und *pDeactiveView* zeigen auf dieselbe Ansicht, wenn das Hauptframefenster der Anwendung ohne Änderung in der aktiven Ansicht aktiviert wird, z. B. wenn der Fokus von einer anderen Anwendung auf diese Anwendung übertragen wird, und nicht von einer Ansicht in eine andere innerhalb der Anwendung oder beim Wechseln zwischen untergeordneten MDI-Fenstern. Dies ermöglicht es einer Ansicht, ihre Palette bei Bedarf neu zu realisieren.

Diese Parameter unterscheiden sich, wenn [CFrameWnd::SetActiveView](../../mfc/reference/cframewnd-class.md#setactiveview) mit einer Ansicht aufgerufen wird, die sich von der, die [CFrameWnd::GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview) zurückgeben würde, unterscheidet. Dies geschieht am häufigsten bei Splitterfenstern.

## <a name="cviewonbeginprinting"></a><a name="onbeginprinting"></a>CView::OnBeginPrinting

Wird zu Beginn eines Druckauftrags oder Seitenansichtauftrags vom Framework aufgerufen, nachdem `OnPreparePrinting` aufgerufen wurde.

```
virtual void OnBeginPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Verweist auf den Druckergerätekontext.

*Pinfo*<br/>
Verweist auf eine [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) -Struktur, die den aktuellen Druckauftrag beschreibt.

### <a name="remarks"></a>Bemerkungen

Bei der Standardimplementierung dieser Funktion wird keine Aktion ausgeführt. Überschreiben Sie diese Funktion, um alle speziell für den Druck benötigten GDI-Ressourcen, z. B. Stifte oder Schriftarten, zuzuordnen. Wählen Sie die GDI-Objekte für den Gerätekontext aus der [OnPrint](#onprint) -Memberfunktion für jede Seite auf, von der sie verwendet werden. Wenn Sie das gleiche Ansichtsobjekt verwenden, um den Bildschirm anzuzeigen und zu drucken, verwenden Sie separate Variablen für die für jeden Bildschirm erforderlichen GDI-Ressourcen. Dadurch können Sie den Bildschirm während des Druckens aktualisieren.

Mit dieser Funktion können Sie auch Initialisierungen durchführen, die von Eigenschaften des Druckergerätekontextes abhängig sind. Beispielsweise kann die Anzahl der Seiten, die zum Drucken des Dokuments benötigt werden, von den Einstellungen abhängig sein, die der Benutzer im Dialogfeld „Drucken“ (z. B. Seitenlänge) angibt. In einem solchen Fall können Sie die Länge des Dokuments nicht wie normalerweise in der [OnPreparePrinting](#onprepareprinting) -Memberfunktion angeben; Sie müssen warten, bis der Druckergerätekontext basierend auf den Einstellungen des Dialogfelds erstellt wurde. [OnBeginPrinting](#onbeginprinting) ist die erste überschreibbare Funktion, die Ihnen sofortigen Zugriff auf das [CDC](../../mfc/reference/cdc-class.md) -Objekt gibt, das den Druckergerätekontext darstellt, daher können Sie die Länge des Dokuments mithilfe dieser Funktion festlegen. Wenn die Länge des Dokuments nicht zu diesem Zeitpunkt angegeben wird, wird in der Seitenansicht keine Bildlaufleiste angezeigt.

## <a name="cviewondragenter"></a><a name="ondragenter"></a>CView::OnDragEnter

Wird vom Framework aufgerufen, wenn die Maus zum ersten Mal den nicht scrollenden Bereich des Ablagezielfensters betritt.

```
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parameter

*pDataObject*<br/>
Zeigt auf das [COleDataObject,](../../mfc/reference/coledataobject-class.md) das in den Ablagebereich der Ansicht gezogen wird.

*dwKeyState*<br/>
Enthält den Status der Modifikatorschlüssel. Dies ist eine Kombination aus einer beliebigen Anzahl von folgenden: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON und MK_RBUTTON.

*Punkt*<br/>
Die aktuelle Mausposition relativ zum Clientbereich der Ansicht.

### <a name="return-value"></a>Rückgabewert

Ein Wert aus dem DROPEFFECT-Enumeriertentyp, der den Drop-Typ angibt, der auftreten würde, wenn der Benutzer das Objekt an dieser Position ablegen würde. Der Typ des Abwurfs hängt in der Regel vom aktuellen Schlüsselstatus ab, der von *dwKeyState*angegeben wird. Eine Standardzuordnung von Schlüsselzuständen zu DROPEFFECT-Werten ist:

- DROPEFFECT_NONE Das Datenobjekt kann in diesem Fenster nicht gelöscht werden.

- DROPEFFECT_LINK für MK_CONTROL &#124; MK_SHIFT Erstellt eine Verknüpfung zwischen dem Objekt und seinem Server.

- DROPEFFECT_COPY für MK_CONTROL Erstellt eine Kopie des gelöschten Objekts.

- DROPEFFECT_MOVE für MK_ALT Erstellt eine Kopie des gelöschten Objekts, und löscht das ursprüngliche Objekt. Dies ist in der Regel der Standard-Drop-Effekt, wenn die Ansicht dieses Datenobjekt akzeptieren kann.

Weitere Informationen finden Sie im MFC Advanced Concepts-Beispiel [OCLIENT](../../overview/visual-cpp-samples.md).

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung besteht darin, nichts zu tun und DROPEFFECT_NONE zurückzugeben.

Überschreiben Sie diese Funktion, um zukünftige Aufrufe der [OnDragOver-Memberfunktion](#ondragover) vorzubereiten. Alle Daten, die aus dem Datenobjekt benötigt werden, `OnDragOver` sollten zu diesem Zeitpunkt für die spätere Verwendung in der Memberfunktion abgerufen werden. Die Ansicht sollte zu diesem Zeitpunkt ebenfalls aktualisiert werden, um dem Benutzer visuelles Feedback zu geben. Weitere Informationen finden Sie im Artikel [OLE drag and drop: Implement a drop target](../../mfc/drag-and-drop-ole.md#implement-a-drop-target).

## <a name="cviewondragleave"></a><a name="ondragleave"></a>CView::OnDragLeave

Wird vom Framework während eines Ziehvorgangs aufgerufen, wenn die Maus aus dem gültigen Ablagebereich für dieses Fenster verschoben wird.

```
virtual void OnDragLeave();
```

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, wenn die aktuelle Ansicht alle Aktionen bereinigen muss, die während [OnDragEnter-](#ondragenter) oder [OnDragOver-Aufrufen](#ondragover) ausgeführt wurden, z. B. das Entfernen von visuellem Benutzerfeedback, während das Objekt gezogen und gelöscht wurde.

## <a name="cviewondragover"></a><a name="ondragover"></a>CView::OnDragOver

Wird vom Framework während eines Ziehvorgangs aufgerufen, wenn die Maus über das Ablagezielfenster bewegt wird.

```
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parameter

*pDataObject*<br/>
Zeigt auf das [COleDataObject,](../../mfc/reference/coledataobject-class.md) das über das Ablageziel gezogen wird.

*dwKeyState*<br/>
Enthält den Status der Modifikatorschlüssel. Dies ist eine Kombination aus einer beliebigen Anzahl von folgenden: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON und MK_RBUTTON.

*Punkt*<br/>
Die aktuelle Mausposition relativ zum Ansichtsclientbereich.

### <a name="return-value"></a>Rückgabewert

Ein Wert aus dem DROPEFFECT-Enumeriertentyp, der den Drop-Typ angibt, der auftreten würde, wenn der Benutzer das Objekt an dieser Position ablegen würde. Die Art des Abwurfs hängt oft vom aktuellen Schlüsselstatus ab, der von *dwKeyState*angegeben wird. Eine Standardzuordnung von Schlüsselzuständen zu DROPEFFECT-Werten ist:

- DROPEFFECT_NONE Das Datenobjekt kann in diesem Fenster nicht gelöscht werden.

- DROPEFFECT_LINK für MK_CONTROL &#124; MK_SHIFT Erstellt eine Verknüpfung zwischen dem Objekt und seinem Server.

- DROPEFFECT_COPY für MK_CONTROL Erstellt eine Kopie des gelöschten Objekts.

- DROPEFFECT_MOVE für MK_ALT Erstellt eine Kopie des gelöschten Objekts, und löscht das ursprüngliche Objekt. Dies ist in der Regel der Standard-Drop-Effekt, wenn die Ansicht das Datenobjekt akzeptieren kann.

Weitere Informationen finden Sie im MFC Advanced Concepts-Beispiel [OCLIENT](../../overview/visual-cpp-samples.md).

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung besteht darin, nichts zu tun und DROPEFFECT_NONE zurückzugeben.

Überschreiben Sie diese Funktion, um dem Benutzer während des Ziehvorgangs visuelles Feedback zu geben. Da diese Funktion kontinuierlich aufgerufen wird, sollte jeder darin enthaltene Code so weit wie möglich optimiert werden. Weitere Informationen finden Sie im Artikel [OLE drag and drop: Implement a drop target](../../mfc/drag-and-drop-ole.md#implement-a-drop-target).

## <a name="cviewondragscroll"></a><a name="ondragscroll"></a>CView::OnDragScroll

Wird vom Framework aufgerufen, bevor [OnDragEnter](#ondragenter) oder [OnDragOver](#ondragover) aufgerufen wird, um zu bestimmen, ob sich der Punkt im Bildlaufbereich befindet.

```
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parameter

*dwKeyState*<br/>
Enthält den Status der Modifikatorschlüssel. Dies ist eine Kombination aus einer beliebigen Anzahl von folgenden: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON und MK_RBUTTON.

*Punkt*<br/>
Enthält die Position des Cursors in Pixel relativ zum Bildschirm.

### <a name="return-value"></a>Rückgabewert

Ein Wert aus dem DROPEFFECT-Enumeriertentyp, der den Drop-Typ angibt, der auftreten würde, wenn der Benutzer das Objekt an dieser Position ablegen würde. Der Typ des Abwurfs hängt in der Regel vom aktuellen Schlüsselstatus ab, der von *dwKeyState*angegeben wird. Eine Standardzuordnung von Schlüsselzuständen zu DROPEFFECT-Werten ist:

- DROPEFFECT_NONE Das Datenobjekt kann in diesem Fenster nicht gelöscht werden.

- DROPEFFECT_LINK für MK_CONTROL &#124; MK_SHIFT Erstellt eine Verknüpfung zwischen dem Objekt und seinem Server.

- DROPEFFECT_COPY für MK_CONTROL Erstellt eine Kopie des gelöschten Objekts.

- DROPEFFECT_MOVE für MK_ALT Erstellt eine Kopie des gelöschten Objekts, und löscht das ursprüngliche Objekt.

- DROPEFFECT_SCROLL Gibt an, dass ein Ziehbildvorgang in der Zielansicht ausgeführt wird oder auftritt.

Weitere Informationen finden Sie im MFC Advanced Concepts-Beispiel [OCLIENT](../../overview/visual-cpp-samples.md).

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, wenn Sie ein spezielles Verhalten für dieses Ereignis bereitstellen möchten. Die Standardimplementierung scrollt automatisch Fenster, wenn der Cursor in den Standard-Bildlaufbereich innerhalb des Rahmens jedes Fensters gezogen wird. Weitere Informationen finden Sie im Artikel [OLE drag and drop: Implement a drop target](../../mfc/drag-and-drop-ole.md#implement-a-drop-target).

## <a name="cviewondraw"></a><a name="ondraw"></a>CView::OnDraw

Wird vom Framework aufgerufen, um ein Abbild des Dokuments zu rendern.

```
virtual void OnDraw(CDC* pDC) = 0;
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Verweist auf den Gerätekontext, der zum Rendern eines Bildes des Dokuments verwendet werden soll.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Funktion auf, um Bildschirmanzeige, Drucken und Druckvorschau durchzuführen, und übergibt jeweils einen anderen Gerätekontext. Es ist keine Standardimplementierung vorhanden.

Sie müssen diese Funktion überschreiben, um die Ansicht des Dokuments anzuzeigen. Sie können GDI-Aufrufe (Graphic Device [CDC](../../mfc/reference/cdc-class.md) Interface) mithilfe des CDC-Objekts erstellen, auf das der *pDC-Parameter* zeigt. Sie können GDI-Ressourcen, z. B. Stifte oder Schriftarten, vor dem Zeichnen in den Gerätekontext auswählen und anschließend die Auswahl aufheben. Häufig kann Ihr Zeichencode geräteunabhängig sein. das heißt, es erfordert keine Informationen darüber, welcher Gerätetyp das Bild anzeigt.

Um das Zeichnen zu optimieren, rufen Sie die [RectVisible-Memberfunktion](../../mfc/reference/cdc-class.md#rectvisible) des Gerätekontexts auf, um herauszufinden, ob ein bestimmtes Rechteck gezeichnet wird. Wenn Sie zwischen normaler Bildschirmanzeige und Drucken unterscheiden müssen, rufen Sie die [IsPrinting-Memberfunktion](../../mfc/reference/cdc-class.md#isprinting) des Gerätekontexts auf.

## <a name="cviewondrop"></a><a name="ondrop"></a>CView::OnDrop

Wird vom Framework aufgerufen, wenn der Benutzer ein Datenobjekt über ein gültiges Ablageziel freigibt.

```
virtual BOOL OnDrop(
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>Parameter

'pDataObject* verweist auf das [COleDataObject,](../../mfc/reference/coledataobject-class.md) das in das Ablageziel abgelegt wird.

*dropEffect*<br/>
Der vom Benutzer angeforderte Dropeffekt.

- DROPEFFECT_COPY Erstellt eine Kopie des Datenobjekts, das gelöscht wird.

- DROPEFFECT_MOVE Verschiebt das Datenobjekt an die aktuelle Mausposition.

- DROPEFFECT_LINK Erstellt eine Verknüpfung zwischen einem Datenobjekt und seinem Server.

*Punkt*<br/>
Die aktuelle Mausposition relativ zum Ansichtsclientbereich.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Drop erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung bewirkt nichts und gibt FALSE zurück.

Überschreiben Sie diese Funktion, um den Effekt eines OLE-Abwurfs in den Clientbereich der Ansicht zu implementieren. Das Datenobjekt kann über *pDataObject* für Zwischenablage-Datenformate und daten, die am angegebenen Punkt abgelegt werden, untersucht werden.

> [!NOTE]
> Das Framework ruft diese Funktion nicht auf, wenn in dieser Ansichtsklasse eine Außerkraftsetzung von [OnDropEx](#ondropex) vorliegt.

## <a name="cviewondropex"></a><a name="ondropex"></a>CView::OnDropEx

Wird vom Framework aufgerufen, wenn der Benutzer ein Datenobjekt über ein gültiges Ablageziel freigibt.

```
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Parameter

*pDataObject*<br/>
Zeigt auf das [COleDataObject,](../../mfc/reference/coledataobject-class.md) das in das Ablageziel abgelegt wird.

*dropDefault*<br/>
Der Effekt, den der Benutzer für den Standardablagevorgang basierend auf dem aktuellen Schlüsselstatus ausgewählt hat. Es kann DROPEFFECT_NONE sein. Drop-Effekte werden im Abschnitt "Bemerkungen" erläutert.

*dropList*<br/>
Eine Liste der Drop-Effekte, die von der Ablagequelle unterstützt werden. Dropeffektwerte können mit dem bitweisen ODER - **&#124;**) Vorgang kombiniert werden. Drop-Effekte werden im Abschnitt "Bemerkungen" erläutert.

*Punkt*<br/>
Die aktuelle Mausposition relativ zum Ansichtsclientbereich.

### <a name="return-value"></a>Rückgabewert

Der Dropeffekt, der sich aus dem Drop-Versuch an der durch *Punkt*angegebenen Position ergab. Dies muss einer der Werte sein, die von *dropEffectList*angegeben werden. Drop-Effekte werden im Abschnitt "Bemerkungen" erläutert.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung besteht darin, nichts zu tun und einen Dummywert ( -1 ) zurückzugeben, um anzugeben, dass das Framework den [OnDrop-Handler](#ondrop) aufrufen soll.

Überschreiben Sie diese Funktion, um den Effekt eines Rechts-Maus-Percperdes zu implementieren. Rechts-Maus-Taste Drag & Drop zeigt in der Regel ein Menü mit Optionen, wenn die rechte Maustaste freigegeben wird.

Ihre Überschreibung `OnDropEx` von sollte abfrage für die rechte Maustaste. Sie können [GetKeyState](/windows/win32/api/winuser/nf-winuser-getkeystate) aufrufen oder den richtigen Maustastenstatus von Ihrem [OnDragEnter-Handler](#ondragenter) speichern.

- Wenn die rechte Maustaste nach unten ist, sollte Ihre Außerkraftsetzung ein Popup-Menü anzeigen, das die Drop-Effekte-Unterstützung durch die Drop-Quelle bietet.

  - Untersuchen Sie *dropList,* um die Dropeffekte zu ermitteln, die von der Ablagequelle unterstützt werden. Aktivieren Sie nur diese Aktionen im Popupmenü.

  - Verwenden Sie [SetMenuDefaultItem,](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem) um die Standardaktion basierend auf *dropDefault*festzulegen.

  - Führen Sie schließlich die durch die Benutzerauswahl angezeigte Aktion aus dem Popupmenü aus.

- Wenn die rechte Maustaste nicht nach unten ist, sollte Ihre Außerkraftsetzung dies als Standard-Drop-Anforderung verarbeiten. Verwenden Sie den in *dropDefault*angegebenen Dropeffekt . Alternativ kann Ihre Außerkraftsetzung den Dummywert ( -1 ) zurückgeben, um anzugeben, dass `OnDrop` dieser Ablagevorgang behandelt wird.

Verwenden Sie *pDataObject,* um das Datenformat für die `COleDataObject` Zwischenablage und die am angegebenen Punkt abgelegten Daten zu untersuchen.

Dropeffekte beschreiben die Aktion, die einem Ablagevorgang zugeordnet ist. Sehen Sie sich die folgende Liste der Drop-Effekte an:

- DROPEFFECT_NONE Ein Tropfen wäre nicht erlaubt.

- DROPEFFECT_COPY ein Kopiervorgang durchgeführt.

- DROPEFFECT_MOVE Ein Umzugsvorgang wird ausgeführt.

- DROPEFFECT_LINK Eine Verknüpfung von den gelöschten Daten zu den ursprünglichen Daten hergestellt werden würde.

- DROPEFFECT_SCROLL Gibt an, dass ein Ziehbildvorgang im Ziel ausgeführt wird oder stattfindet.

Weitere Informationen zum Festlegen des Standardmenübefehls finden Sie unter [SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem) im Windows SDK und [CMenu::GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu) in diesem Handbuch.

## <a name="cviewonendprinting"></a><a name="onendprinting"></a>CView::OnEndPrinting

Wird vom Framework aufgerufen, nachdem ein Dokument gedruckt oder in der Vorschau angezeigt wurde.

```
virtual void OnEndPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Verweist auf den Druckergerätekontext.

*Pinfo*<br/>
Verweist auf eine [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) -Struktur, die den aktuellen Druckauftrag beschreibt.

### <a name="remarks"></a>Bemerkungen

Bei der Standardimplementierung dieser Funktion wird keine Aktion ausgeführt. Überschreiben Sie diese Funktion, um alle GDI-Ressourcen freizugeben, die Sie in der [OnBeginPrinting-Memberfunktion](#onbeginprinting) zugewiesen haben.

## <a name="cviewonendprintpreview"></a><a name="onendprintpreview"></a>CView::OnEndPrintPreview

Wird vom Framework aufgerufen, wenn der Benutzer den Druckvorschaumodus verlässt.

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

*Pinfo*<br/>
Verweist auf eine [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) -Struktur, die den aktuellen Druckauftrag beschreibt.

*Punkt*<br/>
Gibt den Punkt auf der Seite an, der zuletzt im Vorschaumodus angezeigt wurde.

*Pview*<br/>
Zeigt auf das Ansichtsobjekt, das für die Vorschau verwendet wird.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung dieser Funktion ruft die [OnEndPrinting-Memberfunktion](#onendprinting) auf und stellt das Hauptrahmenfenster in den Zustand zurück, in dem es sich vor Beginn der Druckvorschau befand. Überschreiben Sie diese Funktion, um eine spezielle Verarbeitung durchzuführen, wenn der Vorschaumodus beendet wird. Wenn Sie z. B. die Position des Benutzers im Dokument beibehalten möchten, wenn Sie vom Vorschaumodus in `m_nCurPage` den normalen `CPrintInfo` Anzeigemodus wechseln, können Sie zu der Position scrollen, die durch den *Punktparameter* und das Element der Struktur beschrieben wird, auf die der *Parameter pInfo* zeigt.

Rufen Sie immer die `OnEndPrintPreview` Basisklassenversion von aus Ihrer Außerkraftsetzung auf, in der Regel am Ende der Funktion.

## <a name="cviewoninitialupdate"></a><a name="oninitialupdate"></a>CView::OnInitialUpdate

Wird vom Framework aufgerufen, nachdem die Ansicht zuerst an das Dokument angefügt wurde, aber bevor die Ansicht zuerst angezeigt wird.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung dieser Funktion ruft die [OnUpdate-Memberfunktion](#onupdate) ohne Hinweisinformationen auf (d. h. die Standardwerte 0 für den *Parameter lHint* und NULL für den *pHint-Parameter).* Überschreiben Sie diese Funktion, um eine einmalige Initialisierung durchzuführen, die Informationen über das Dokument erfordert. Wenn Ihre Anwendung beispielsweise Dokumente mit fester Größe enthält, können Sie diese Funktion verwenden, um die Bildlauflimits einer Ansicht basierend auf der Dokumentgröße zu initialisieren. Wenn Ihre Anwendung Dokumente mit variabler Größe unterstützt, aktualisieren Sie die Bildlauflimits bei jeder Änderung des Dokuments mithilfe von [OnUpdate.](#onupdate)

## <a name="cviewonpreparedc"></a><a name="onpreparedc"></a>CView::OnPrepareDC

Wird vom Framework aufgerufen, bevor die [OnDraw-Memberfunktion](#ondraw) für die Bildschirmanzeige und vor der [OnPrint-Memberfunktion](#onprint) für jede Seite während des Druckens oder der Druckvorschau aufgerufen wird.

```
virtual void OnPrepareDC(
    CDC* pDC,
    CPrintInfo* pInfo = NULL);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Verweist auf den Gerätekontext, der zum Rendern eines Bildes des Dokuments verwendet werden soll.

*Pinfo*<br/>
Verweist auf eine [CPrintInfo-Struktur,](../../mfc/reference/cprintinfo-structure.md) die `OnPrepareDC` den aktuellen Druckauftrag beschreibt, wenn er für den Druck oder die Druckvorschau aufgerufen wird. Das `m_nCurPage` Mitglied gibt die Seite an, die gedruckt werden soll. Dieser Parameter ist `OnPrepareDC` NULL, wenn für die Bildschirmanzeige aufgerufen wird.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung dieser Funktion bewirkt nichts, wenn die Funktion für die Bildschirmanzeige aufgerufen wird. Diese Funktion wird jedoch in abgeleiteten Klassen wie [CScrollView](../../mfc/reference/cscrollview-class.md)überschrieben, um Attribute des Gerätekontexts anzupassen. Daher sollten Sie immer die Basisklassenimplementierung zu Beginn der Außerkraftsetzung aufrufen.

Wenn die Funktion zum Drucken aufgerufen wird, überprüft die Standardimplementierung die im Parameter *pInfo* gespeicherten Seiteninformationen. Wenn die Länge des Dokuments `OnPrepareDC` nicht angegeben wurde, wird davon ausgegangen, dass das Dokument eine Seite lang ist, und stoppt die Druckschleife, nachdem eine Seite gedruckt wurde. Die Funktion stoppt die Druckschleife, indem das `m_bContinuePrinting` Element der Struktur auf FALSE gesetzt wird.

Außerkraftsetzung `OnPrepareDC` aus einem der folgenden Gründe:

- So passen Sie die Attribute des Gerätekontexts nach Bedarf für die angegebene Seite an. Wenn Sie z. B. den Zuordnungsmodus oder andere Merkmale des Gerätekontexts festlegen müssen, tun Sie dies in dieser Funktion.

- So führen Sie die Druckzeitpaginierung durch. Normalerweise geben Sie die Länge des Dokuments zu Beginn des Druckvorgangs mithilfe der [OnPreparePrinting-Memberfunktion](#onprepareprinting) an. Wenn Sie jedoch nicht im Voraus wissen, wie lange das Dokument ist (z. B. beim `OnPrepareDC` Drucken einer unbestimmten Anzahl von Datensätzen aus einer Datenbank), überschreiben Sie, um das Ende des Dokuments während des Druckens zu testen. Wenn das Dokument nicht mehr gedruckt werden `m_bContinuePrinting` soll, `CPrintInfo` legen Sie das Element der Struktur auf FALSE fest.

- So senden Sie Escapecodes Seite für Seite an den Drucker. Um Escapecodes `OnPrepareDC`von zu `Escape` senden, rufen Sie die Memberfunktion des *pDC-Parameters* auf.

Rufen Sie die `OnPrepareDC` Basisklassenversion von am Anfang der Außerkraftsetzung auf.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]

## <a name="cviewonprepareprinting"></a><a name="onprepareprinting"></a>CView::OnPreparePrinting

Wird vom Framework aufgerufen, bevor ein Dokument gedruckt oder in der Vorschau angezeigt wird.

```
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parameter

*Pinfo*<br/>
Verweist auf eine [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) -Struktur, die den aktuellen Druckauftrag beschreibt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, um mit dem Drucken zu beginnen; 0, wenn der Druckauftrag abgebrochen wurde.

### <a name="remarks"></a>Bemerkungen

Bei der Standardimplementierung wird keine Aktion ausgeführt.

Sie müssen diese Funktion überschreiben, um die Druck- und Druckvorschau zu aktivieren. Rufen Sie die [DoPreparePrinting-Memberfunktion](#doprepareprinting) auf, übergeben Sie den *pInfo-Parameter,* und geben Sie dann den Rückgabewert zurück. `DoPreparePrinting` zeigt das Dialogfeld Drucken an und erstellt einen Druckergerätekontext. Wenn Sie das Dialogfeld Drucken mit anderen Werten als den Standardwerten initialisieren möchten, weisen Sie den Mitgliedern von *pInfo*Werte zu. Wenn Sie beispielsweise die Länge des Dokuments kennen, übergeben Sie den Wert an `DoPreparePrinting`die [SetMaxPage-Memberfunktion](../../mfc/reference/cprintinfo-structure.md#setmaxpage) von *pInfo,* bevor Sie aufrufen. Dieser Wert wird im Feld An: im Bereich des Dialogfelds Drucken angezeigt.

`DoPreparePrinting`zeigt das Dialogfeld Drucken für einen Vorschauauftrag nicht an. Wenn Sie das Dialogfeld Drucken für einen Druckauftrag `m_bPreview` umgehen möchten, überprüfen Sie, ob das Element `DoPreparePrinting`von *pInfo* FALSE ist, und legen Sie es dann auf TRUE fest, bevor Sie es an übergeben. setzen Sie es anschließend auf FALSE zurück.

Wenn Sie Initialisierungen durchführen müssen, `CDC` die Zugriff auf das Objekt erfordern, das den Kontext des Druckergeräts darstellt (z. `OnBeginPrinting` B. wenn Sie die Seitengröße kennen müssen, bevor Sie die Länge des Dokuments angeben), überschreiben Sie die Memberfunktion.

Wenn Sie den Wert des `m_nNumPreviewPages` `m_strPageDesc` oder Members des *pInfo-Parameters* `DoPreparePrinting`festlegen möchten, tun Sie dies nach dem Aufruf . Die `DoPreparePrinting` Memberfunktion `m_nNumPreviewPages` legt den Wert in der Anwendung fest. INI-Datei `m_strPageDesc` und legt den Standardwert fest.

### <a name="example"></a>Beispiel

  Überschreiben `OnPreparePrinting` und `DoPreparePrinting` Aufrufen aus der Außerkraftsetzung, sodass das Framework ein Dialogfeld Drucken anzeigt und einen Drucker-DC für Sie erstellt.

[!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]

Wenn Sie wissen, wie viele Seiten das `OnPreparePrinting` Dokument `DoPreparePrinting`enthält, legen Sie die maximale Seite vor dem Aufruf fest. Das Framework zeigt die maximale Seitenzahl im Feld "an" des Dialogfelds Drucken an.

[!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]

## <a name="cviewonprint"></a><a name="onprint"></a>CView::OnPrint

Wird vom Framework aufgerufen, um eine Seite des Dokuments zu drucken oder in der Vorschau anzuzeigen.

```
virtual void OnPrint(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Verweist auf den Druckergerätekontext.

*Pinfo*<br/>
Zeigt auf `CPrintInfo` eine Struktur, die den aktuellen Druckauftrag beschreibt.

### <a name="remarks"></a>Bemerkungen

Für jede gedruckte Seite ruft das Framework diese Funktion unmittelbar nach dem Aufruf der [OnPrepareDC-Memberfunktion](#onpreparedc) auf. Die zu druckende Seite `m_nCurPage` wird vom Element der [CPrintInfo-Struktur](../../mfc/reference/cprintinfo-structure.md) angegeben, auf das *pInfo* verweist. Die Standardimplementierung ruft die [OnDraw-Memberfunktion](#ondraw) auf und übergibt sie an den Druckergerätekontext.

Überschreiben Sie diese Funktion aus einem der folgenden Gründe:

- So ermöglichen Sie das Drucken von mehrseitigen Dokumenten. Rendern Sie nur den Teil des Dokuments, der der aktuell gedruckten Seite entspricht. Wenn Sie das `OnDraw` Rendering ausführen, können Sie den Ursprung des Ansichtsfensters so anpassen, dass nur der entsprechende Teil des Dokuments gedruckt wird.

- Damit das gedruckte Bild anders aussieht als das Bildschirmbild (d. h., wenn Ihre Anwendung nicht WYSIWYG ist). Anstatt den Druckergerätekontext `OnDraw`an zu übergeben, verwenden Sie den Gerätekontext, um ein Bild mit Attributen zu rendern, die nicht auf dem Bildschirm angezeigt werden.

   Wenn Sie GDI-Ressourcen zum Drucken benötigen, die Sie nicht für die Bildschirmanzeige verwenden, wählen Sie sie vor dem Zeichnen im Gerätekontext aus, und deaktivieren Sie sie anschließend. Diese GDI-Ressourcen sollten in [OnBeginPrinting](#onbeginprinting) zugewiesen und in [OnEndPrinting](#onendprinting)veröffentlicht werden.

- So implementieren Sie Kopf- oder Fußzeilen. Sie können `OnDraw` das Rendering weiterhin verwenden, indem Sie den Bereich einschränken, auf dem es drucken kann.

Beachten Sie, dass der `m_rectDraw` Member des parameters *pInfo* den druckbaren Bereich der Seite in logischen Einheiten beschreibt.

Rufen `OnPrepareDC` Sie nicht in `OnPrint`Ihrer Außerkraftsetzung von auf; Das Framework `OnPrepareDC` ruft `OnPrint`automatisch auf, bevor es aufgerufen wird .

### <a name="example"></a>Beispiel

Im Folgenden finden Sie ein `OnPrint` Skelett für eine überschriebene Funktion:

[!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]

Ein weiteres Beispiel finden Sie unter [CRichEditView::PrintInsideRect](../../mfc/reference/cricheditview-class.md#printinsiderect).

## <a name="cviewonscroll"></a><a name="onscroll"></a>CView::OnScroll

Wird vom Framework aufgerufen, um zu bestimmen, ob ein Bildlauf möglich ist.

```
virtual BOOL OnScroll(
    UINT nScrollCode,
    UINT nPos,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parameter

*nScrollCode*<br/>
Ein Bildlaufleistencode, der die Bildlaufanforderung des Benutzers angibt. Dieser Parameter besteht aus zwei Teilen: einem Byte niedriger Ordnung, das den horizontal auftretenden Scrolltyp bestimmt, und einem Byte hoher Ordnung, das den vertikal enkrechten Bildlauftyp bestimmt:

- SB_BOTTOM Scrolls nach unten.

- SB_LINEDOWN Scrollt eine Zeile nach unten.

- SB_LINEUP Scrollt eine Reihe nach oben.

- SB_PAGEDOWN Scrollt eine Seite nach unten.

- SB_PAGEUP Scrollt eine Seite nach oben.

- SB_THUMBTRACK Ziehbildungsfeld an die angegebene Position. Die aktuelle Position wird in *nPos*angegeben.

- SB_TOP Scrolls nach oben.

*Npos*<br/>
Enthält die aktuelle Bildlauffeldposition, wenn der Scroll-Barcode SB_THUMBTRACK ist. andernfalls wird es nicht verwendet. Je nach anfänglichem Bildlaufbereich kann *nPos* negativ sein und sollte bei Bedarf in eine **int** gegossen werden.

*bDoScroll*<br/>
Bestimmt, ob Sie tatsächlich die angegebene Bildlaufaktion durchführen sollten. Wenn TRUE, dann sollte scrollen sollte stattfinden; Wenn FALSE, dann sollte kein Scrollen stattfinden.

### <a name="return-value"></a>Rückgabewert

Wenn *bDoScroll* TRUE ist und die Ansicht tatsächlich gescrollt wurde, geben Sie einen Wert ungleich Null zurück. andernfalls 0. Wenn *bDoScroll* FALSE ist, geben Sie den Wert zurück, den Sie zurückgegeben hätten, wenn *bDoScroll* TRUE wäre, obwohl Sie das Scrollen nicht tatsächlich durchführen.

### <a name="remarks"></a>Bemerkungen

In einem Fall wird diese Funktion vom Framework aufgerufen, wobei *bDoScroll* auf TRUE gesetzt ist, wenn die Ansicht eine Bildlaufleistennachricht empfängt. In diesem Fall sollten Sie tatsächlich einen Bildlauf in der Ansicht durchführen. Im anderen Fall wird diese Funktion aufgerufen, wobei *bDoScroll* auf FALSE gesetzt ist, wenn ein OLE-Element zunächst in den Auto-Scrolling-Bereich eines Ablageziels gezogen wird, bevor tatsächlich gescrollt wird. In diesem Fall sollten Sie die Ansicht nicht tatsächlich scrollen.

## <a name="cviewonscrollby"></a><a name="onscrollby"></a>CView::OnscrollBy

Wird vom Framework aufgerufen, wenn der Benutzer einen Bereich außerhalb der aktuellen Ansicht des Dokuments anzeigt, indem entweder ein OLE-Element an die aktuellen Ränder der Ansicht gezogen wird oder indem die vertikalen oder horizontalen Bildlaufleisten manipuliert werden.

```
virtual BOOL OnScrollBy(
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parameter

*sizeScroll*<br/>
Anzahl der Pixel, die horizontal und vertikal gescrollt wurden.

*bDoScroll*<br/>
Bestimmt, ob ein Bildlauf der Ansicht erfolgt. Wenn TRUE, dann wird gescrollt; wenn FALSE, dann wird kein Bildlauf durchgeführt.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Ansicht gescrollt werden konnte; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

In abgeleiteten Klassen überprüft diese Methode, ob die Ansicht in die vom Benutzer angeforderte Richtung scrollbar ist, und aktualisiert dann ggf. die neue Region. Diese Funktion wird automatisch von [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) und [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) aufgerufen, um die eigentliche Scrolling-Anforderung auszuführen.

Die Standardimplementierung dieser Methode ändert die Ansicht nicht, aber wenn sie nicht `CScrollView`aufgerufen wird, wird die Ansicht nicht in einer -derived-Klasse gescrollt.

Wenn die Dokumentbreite oder -höhe 32767 Pixel überschreitet, schlägt ein `OnScrollBy` Bildlauf über 32767 fehl, da ein ungültiges *sizeScroll-Argument* aufgerufen wird.

## <a name="cviewonupdate"></a><a name="onupdate"></a>CView::OnUpdate

Wird vom Framework aufgerufen, nachdem das Dokument der Ansicht geändert wurde; Diese Funktion wird von [CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) aufgerufen und ermöglicht es der Ansicht, ihre Anzeige zu aktualisieren, um diese Änderungen widerzuspiegeln.

```
virtual void OnUpdate(
    CView* pSender,
    LPARAM lHint,
    CObject* pHint);
```

### <a name="parameters"></a>Parameter

*pSender*<br/>
Zeigt auf die Ansicht, die das Dokument geändert hat, oder NULL, wenn alle Ansichten aktualisiert werden sollen.

*lHint*<br/>
Enthält Informationen zu den Änderungen.

*pHint*<br/>
Verweist auf ein Objekt, das Informationen zu den Änderungen speichert.

### <a name="remarks"></a>Bemerkungen

Es wird auch von der Standardimplementierung von [OnInitialUpdate](#oninitialupdate)aufgerufen. Die Standardimplementierung macht den gesamten Clientbereich ungültig und markiert ihn zum Malen, wenn die nächste WM_PAINT Nachricht empfangen wird. Überschreiben Sie diese Funktion, wenn Sie nur die Regionen aktualisieren möchten, die den geänderten Teilen des Dokuments zugeordnet sind. Dazu müssen Sie Informationen über die Änderungen mithilfe der Hinweisparameter übergeben.

Um *lHint*zu verwenden, definieren Sie spezielle Hinweiswerte, in der Regel eine Bitmaske oder einen aufgezählten Typ, und lassen Sie das Dokument einen dieser Werte übergeben. Um *pHint*zu verwenden, leiten Sie eine Hint-Klasse von [CObject](../../mfc/reference/cobject-class.md) ab, und lassen Sie das Dokument einen Zeiger an ein Hint-Objekt übergeben. beim Überschreiben `OnUpdate`verwenden Sie die [Memberfunktion CObject::IsKindOf,](../../mfc/reference/cobject-class.md#iskindof) um den Laufzeittyp des Hint-Objekts zu bestimmen.

In der Regel sollten Sie `OnUpdate`keine Zeichnung direkt aus durchführen. Bestimmen Sie stattdessen das Rechteck, das in Gerätekoordinaten den Bereich beschreibt, der aktualisiert werden muss. Übergeben Sie dieses Rechteck an [CWnd::InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect). Dies bewirkt, dass das Malen auftritt, wenn das nächste Mal eine [WM_PAINT](/windows/win32/gdi/wm-paint) Nachricht empfangen wird.

Wenn *lHint* 0 und *pHint* NULL ist, hat das Dokument eine allgemeine Aktualisierungsbenachrichtigung gesendet. Wenn eine Ansicht eine generische Aktualisierungsbenachrichtigung empfängt oder die Hinweise nicht decodieren kann, sollte sie den gesamten Clientbereich ungültig machen.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[CFrameWnd-Klasse](../../mfc/reference/cframewnd-class.md)<br/>
[CSplitterWnd-Klasse](../../mfc/reference/csplitterwnd-class.md)<br/>
[CDC-Klasse](../../mfc/reference/cdc-class.md)<br/>
[CDocTemplate-Klasse](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument-Klasse](../../mfc/reference/cdocument-class.md)
