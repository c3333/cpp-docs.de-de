---
title: COleServerDoc-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleServerDoc
- AFXOLE/COleServerDoc
- AFXOLE/COleServerDoc::COleServerDoc
- AFXOLE/COleServerDoc::ActivateDocObject
- AFXOLE/COleServerDoc::ActivateInPlace
- AFXOLE/COleServerDoc::DeactivateAndUndo
- AFXOLE/COleServerDoc::DiscardUndoState
- AFXOLE/COleServerDoc::GetClientSite
- AFXOLE/COleServerDoc::GetEmbeddedItem
- AFXOLE/COleServerDoc::GetItemClipRect
- AFXOLE/COleServerDoc::GetItemPosition
- AFXOLE/COleServerDoc::GetZoomFactor
- AFXOLE/COleServerDoc::IsDocObject
- AFXOLE/COleServerDoc::IsEmbedded
- AFXOLE/COleServerDoc::IsInPlaceActive
- AFXOLE/COleServerDoc::NotifyChanged
- AFXOLE/COleServerDoc::NotifyClosed
- AFXOLE/COleServerDoc::NotifyRename
- AFXOLE/COleServerDoc::NotifySaved
- AFXOLE/COleServerDoc::OnDeactivate
- AFXOLE/COleServerDoc::OnDeactivateUI
- AFXOLE/COleServerDoc::OnDocWindowActivate
- AFXOLE/COleServerDoc::OnResizeBorder
- AFXOLE/COleServerDoc::OnShowControlBars
- AFXOLE/COleServerDoc::OnUpdateDocument
- AFXOLE/COleServerDoc::RequestPositionChange
- AFXOLE/COleServerDoc::SaveEmbedding
- AFXOLE/COleServerDoc::ScrollContainerBy
- AFXOLE/COleServerDoc::UpdateAllItems
- AFXOLE/COleServerDoc::CreateInPlaceFrame
- AFXOLE/COleServerDoc::DestroyInPlaceFrame
- AFXOLE/COleServerDoc::GetDocObjectServer
- AFXOLE/COleServerDoc::OnClose
- AFXOLE/COleServerDoc::OnExecOleCmd
- AFXOLE/COleServerDoc::OnFrameWindowActivate
- AFXOLE/COleServerDoc::OnGetEmbeddedItem
- AFXOLE/COleServerDoc::OnReactivateAndUndo
- AFXOLE/COleServerDoc::OnSetHostNames
- AFXOLE/COleServerDoc::OnSetItemRects
- AFXOLE/COleServerDoc::OnShowDocument
helpviewer_keywords:
- COleServerDoc [MFC], COleServerDoc
- COleServerDoc [MFC], ActivateDocObject
- COleServerDoc [MFC], ActivateInPlace
- COleServerDoc [MFC], DeactivateAndUndo
- COleServerDoc [MFC], DiscardUndoState
- COleServerDoc [MFC], GetClientSite
- COleServerDoc [MFC], GetEmbeddedItem
- COleServerDoc [MFC], GetItemClipRect
- COleServerDoc [MFC], GetItemPosition
- COleServerDoc [MFC], GetZoomFactor
- COleServerDoc [MFC], IsDocObject
- COleServerDoc [MFC], IsEmbedded
- COleServerDoc [MFC], IsInPlaceActive
- COleServerDoc [MFC], NotifyChanged
- COleServerDoc [MFC], NotifyClosed
- COleServerDoc [MFC], NotifyRename
- COleServerDoc [MFC], NotifySaved
- COleServerDoc [MFC], OnDeactivate
- COleServerDoc [MFC], OnDeactivateUI
- COleServerDoc [MFC], OnDocWindowActivate
- COleServerDoc [MFC], OnResizeBorder
- COleServerDoc [MFC], OnShowControlBars
- COleServerDoc [MFC], OnUpdateDocument
- COleServerDoc [MFC], RequestPositionChange
- COleServerDoc [MFC], SaveEmbedding
- COleServerDoc [MFC], ScrollContainerBy
- COleServerDoc [MFC], UpdateAllItems
- COleServerDoc [MFC], CreateInPlaceFrame
- COleServerDoc [MFC], DestroyInPlaceFrame
- COleServerDoc [MFC], GetDocObjectServer
- COleServerDoc [MFC], OnClose
- COleServerDoc [MFC], OnExecOleCmd
- COleServerDoc [MFC], OnFrameWindowActivate
- COleServerDoc [MFC], OnGetEmbeddedItem
- COleServerDoc [MFC], OnReactivateAndUndo
- COleServerDoc [MFC], OnSetHostNames
- COleServerDoc [MFC], OnSetItemRects
- COleServerDoc [MFC], OnShowDocument
ms.assetid: a9cdd96a-e0ac-43bb-9203-2c29237e965c
ms.openlocfilehash: 8e75ec5c00c614a225a059a2b3cf97a7a307c61c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753777"
---
# <a name="coleserverdoc-class"></a>COleServerDoc-Klasse

Die Basisklasse für OLE-Serverdokumente.

## <a name="syntax"></a>Syntax

```
class AFX_NOVTABLE COleServerDoc : public COleLinkingDoc
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleServerdoc::COleServerdoc](#coleserverdoc)|Erstellt ein `COleServerDoc`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleServerDoc::ActivateDocObject](#activatedocobject)|Aktiviert das zugehörige DocObject-Dokument.|
|[COleServerdoc::ActivateInPlace](#activateinplace)|Aktiviert das Dokument für die ortsspezifische Bearbeitung.|
|[COleServerDoc::DeactivateAndUndo](#deactivateandundo)|Deaktiviert die Benutzeroberfläche des Servers.|
|[COleServerDoc::DiscardUndoState](#discardundostate)|Verwirft Rückgängig-Statusinformationen.|
|[COleServerDoc::GetClientSite](#getclientsite)|Ruft einen Zeiger auf `IOleClientSite` die zugrunde liegende Schnittstelle ab.|
|[COleServerDoc::GetEmbeddedItem](#getembeddeditem)|Gibt einen Zeiger auf ein Element zurück, das das gesamte Dokument darstellt.|
|[COleServerDoc::GetItemClipRect](#getitemcliprect)|Gibt das aktuelle Zuschneiderechteck für die ortsspezifische Bearbeitung zurück.|
|[COleServerDoc::GetItemPosition](#getitemposition)|Gibt das aktuelle Positionsrechteck relativ zum Clientbereich der Containeranwendung zur ortsseitigen Bearbeitung zurück.|
|[COleServerDoc::GetZoomFactor](#getzoomfactor)|Gibt den Zoomfaktor in Pixelzurück zurück.|
|[COleServerDoc::IsDocObject](#isdocobject)|Bestimmt, ob es sich bei dem Dokument um ein DocObject handelt.|
|[COleServerdoc::IsEmbedded](#isembedded)|Gibt an, ob das Dokument in ein Containerdokument eingebettet ist oder eigenständig ausgeführt wird.|
|[COleServerdoc::IsInPlaceActive](#isinplaceactive)|Gibt TRUE zurück, wenn das Element derzeit aktiviert ist.|
|[COleServerDoc::NotifyChanged](#notifychanged)|Benachrichtigt Container, dass der Benutzer das Dokument geändert hat.|
|[COleServerDoc::NotifyClosed](#notifyclosed)|Benachrichtigt Container, dass der Benutzer das Dokument geschlossen hat.|
|[COleServerDoc::NotifyRename](#notifyrename)|Benachrichtigt Container, dass der Benutzer das Dokument umbenannt hat.|
|[COleServerDoc::NotifySaved](#notifysaved)|Benachrichtigt Container, dass der Benutzer das Dokument gespeichert hat.|
|[COleServerDoc::OnDeactivate](#ondeactivate)|Wird vom Framework aufgerufen, wenn der Benutzer ein Element deaktiviert, das an Ort und Stelle aktiviert wurde.|
|[COleServerDoc::OnDeactivateUI](#ondeactivateui)|Wird vom Framework aufgerufen, um Steuerelemente und andere Benutzeroberflächenelemente zu zerstören, die für die ortsnahe Aktivierung erstellt wurden.|
|[COleServerdoc::OnDocWindowActivate](#ondocwindowactivate)|Wird vom Framework aufgerufen, wenn das Dokumentrahmenfenster des Containers aktiviert oder deaktiviert wird.|
|[COleServerDoc::OnResizeBorder](#onresizeborder)|Wird vom Framework aufgerufen, wenn die Größe des Rahmenfensters oder Dokumentfensters der Containeranwendung geändert wird.|
|[COleServerdoc::OnShowControlBars](#onshowcontrolbars)|Wird vom Framework aufgerufen, um Steuerleisten für die ortsnahe Bearbeitung ein- oder auszublenden.|
|[COleServerDoc::OnUpdateDocument](#onupdatedocument)|Wird vom Framework aufgerufen, wenn ein Serverdokument gespeichert wird, das ein eingebettetes Element ist, und die Kopie des Elements des Containers aktualisiert.|
|[COleServerDoc::RequestPositionChange](#requestpositionchange)|Ändert die Position des in-Place-Bearbeitungsrahmens.|
|[COleServerDoc::Einbetten speichern](#saveembedding)|Weist die Containeranwendung an, das Dokument zu speichern.|
|[COleServerDoc::ScrollContainerBy](#scrollcontainerby)|Scrollt das Containerdokument.|
|[COleServerDoc::UpdateAllItems](#updateallitems)|Benachrichtigt Container, dass der Benutzer das Dokument geändert hat.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleServerDoc::CreateInPlaceFrame](#createinplaceframe)|Wird vom Framework aufgerufen, um ein Rahmenfenster für die ortsnahe Bearbeitung zu erstellen.|
|[COleServerDoc::DestroyInPlaceFrame](#destroyinplaceframe)|Wird vom Framework aufgerufen, um ein Rahmenfenster für die ortsnahe Bearbeitung zu zerstören.|
|[COleServerDoc::GetDocObjectServer](#getdocobjectserver)|Überschreiben Sie diese Funktion, um ein neues `CDocObjectServer` Objekt zu erstellen, und geben Sie an, dass es sich bei diesem Dokument um einen DocObject-Container handelt.|
|[COleServerDoc::OnClose](#onclose)|Wird vom Framework aufgerufen, wenn ein Container das Dokument schließen soll.|
|[COleServerDoc::OnExecOleCmd](#onexecolecmd)|Führt einen angegebenen Befehl aus oder zeigt Hilfe für den Befehl an.|
|[COleServerDoc::OnFrameWindowActivate](#onframewindowactivate)|Wird vom Framework aufgerufen, wenn das Rahmenfenster des Containers aktiviert oder deaktiviert wird.|
|[COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem)|Wird aufgerufen, `COleServerItem` um eine zu erhalten, die das gesamte Dokument darstellt. verwendet, um ein eingebettetes Element zu erhalten. Implementierung erforderlich.|
|[COleServerDoc::OnReactivateAndUndo](#onreactivateandundo)|Wird vom Framework aufgerufen, um Änderungen rückgängig zu machen, die während der ortsseitigen Bearbeitung vorgenommen wurden.|
|[COleServerDoc::OnSetHostNames](#onsethostnames)|Wird vom Framework aufgerufen, wenn ein Container den Fenstertitel für ein eingebettetes Objekt festlegt.|
|[COleServerDoc::OnSetItemRects](#onsetitemrects)|Wird vom Framework aufgerufen, um das platznahe Bearbeitungsrahmenfenster innerhalb des Fensters der Containeranwendung zu positionieren.|
|[COleServerDoc::OnShowDocument](#onshowdocument)|Wird vom Framework aufgerufen, um das Dokument ein- oder auszublenden.|

## <a name="remarks"></a>Bemerkungen

Ein Serverdokument kann [COleServerItem-Objekte](../../mfc/reference/coleserveritem-class.md) enthalten, die die Serverschnittstelle zu eingebetteten oder verknüpften Elementen darstellen. Wenn eine Serveranwendung von einem Container gestartet wird, um ein eingebettetes Element zu bearbeiten, wird das Element als eigenes Serverdokument geladen. Das `COleServerDoc` Objekt enthält `COleServerItem` nur ein Objekt, das aus dem gesamten Dokument besteht. Wenn eine Serveranwendung von einem Container gestartet wird, um ein verknüpftes Element zu bearbeiten, wird ein vorhandenes Dokument vom Datenträger geladen. ein Teil des Dokumentinhalts wird hervorgehoben, um das verknüpfte Element anzuzeigen.

`COleServerDoc`Objekte können auch Elemente der [COleClientItem-Klasse](../../mfc/reference/coleclientitem-class.md) enthalten. Auf diese Weise können Sie Container-Server-Anwendungen erstellen. Das Framework bietet Funktionen `COleClientItem` zum ordnungsgemäßen `COleServerItem` Speichern der Elemente während der Wartung der Objekte.

Wenn Ihre Serveranwendung keine Verknüpfungen unterstützt, enthält ein Serverdokument immer nur ein Serverelement, das das gesamte eingebettete Objekt als Dokument darstellt. Wenn Ihre Serveranwendung Verknüpfungen unterstützt, muss sie jedes Mal ein Serverelement erstellen, wenn eine Auswahl in die Zwischenablage kopiert wird.

Um `COleServerDoc`zu verwenden, leiten Sie daraus eine Klasse ab und implementieren Sie die [OnGetEmbeddedItem-Memberfunktion,](#ongetembeddeditem) mit der Der Server eingebettete Elemente unterstützen kann. Leiten Sie eine `COleServerItem` Klasse ab, um die Elemente in Ihren `OnGetEmbeddedItem`Dokumenten zu implementieren, und geben Sie Objekte dieser Klasse aus zurück.

Um verknüpfte `COleServerDoc` Elemente zu unterstützen, wird die [OnGetLinkedItem-Memberfunktion](../../mfc/reference/colelinkingdoc-class.md#ongetlinkeditem) angezeigt. Sie können die Standardimplementierung verwenden oder überschreiben, wenn Sie über eine eigene Möglichkeit zum Verwalten von Dokumentelementen verfügen.

Sie benötigen `COleServerDoc`eine -abgeleitete Klasse für jeden Serverdokumenttyp, den Ihre Anwendung unterstützt. Wenn Ihre Serveranwendung z. B. Arbeitsblätter `COleServerDoc`und Diagramme unterstützt, benötigen Sie zwei von -abgeleitete Klassen.

Weitere Informationen zu Servern finden Sie im Artikel [Server: Implementieren eines Servers](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

`COleServerDoc`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxole.h

## <a name="coleserverdocactivatedocobject"></a><a name="activatedocobject"></a>COleServerDoc::ActivateDocObject

Aktiviert das zugehörige DocObject-Dokument.

```cpp
void ActivateDocObject();
```

### <a name="remarks"></a>Bemerkungen

Unterstützt standardmäßig `COleServerDoc` keine aktiven Dokumente (auch als DocObjects bezeichnet). Informationen zum Aktivieren dieser Unterstützung finden Sie unter [GetDocObjectServer](#getdocobjectserver) und die Klasse [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md).

## <a name="coleserverdocactivateinplace"></a><a name="activateinplace"></a>COleServerdoc::ActivateInPlace

Aktiviert das Element für die ortsspezifische Bearbeitung.

```
BOOL ActivateInPlace();
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich; andernfalls 0, was angibt, dass das Element vollständig geöffnet ist.

### <a name="remarks"></a>Bemerkungen

Diese Funktion führt alle Vorgänge aus, die für die Ortsaktivierung erforderlich sind. Es erstellt ein ortsnahes Rahmenfenster, aktiviert es und passt es auf das Element an, richtet freigegebene Menüs und andere Steuerelemente ein, scrollt das Element in die Ansicht und legt den Fokus auf das ortsbezogene Rahmenfenster fest.

Diese Funktion wird von der Standardimplementierung von [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow)aufgerufen. Rufen Sie diese Funktion auf, wenn Ihre Anwendung ein anderes Verb für die ortsspezifische Aktivierung unterstützt (z. B. Play).

## <a name="coleserverdoccoleserverdoc"></a><a name="coleserverdoc"></a>COleServerdoc::COleServerdoc

Erstellt ein `COleServerDoc` Objekt, ohne eine Verbindung mit den OLE-System-DLLs herzustellen.

```
COleServerDoc();
```

### <a name="remarks"></a>Bemerkungen

Sie müssen [COleLinkingDoc::Register](../../mfc/reference/colelinkingdoc-class.md#register) aufrufen, um die Kommunikation mit OLE zu öffnen. Wenn Sie [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) in Ihrer `COleLinkingDoc::Register` Anwendung verwenden, `COleLinkingDoc`wird für `OnNewDocument` `OnOpenDocument`Sie `OnSaveDocument`durch die Implementierung von aufgerufen, , und .

## <a name="coleserverdoccreateinplaceframe"></a><a name="createinplaceframe"></a>COleServerDoc::CreateInPlaceFrame

Das Framework ruft diese Funktion auf, um ein Rahmenfenster für die ortsnahe Bearbeitung zu erstellen.

```
virtual COleIPFrameWnd* CreateInPlaceFrame(CWnd* pParentWnd);
```

### <a name="parameters"></a>Parameter

*pParentWnd*<br/>
Zeigen Sie auf das übergeordnete Fenster der Containeranwendung.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das platzeins-Bildfenster oder NULL, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung verwendet Informationen, die in der Dokumentvorlage angegeben sind, um den Rahmen zu erstellen. Die verwendete Ansicht ist die erste Ansicht, die für das Dokument erstellt wurde. Diese Ansicht wird vorübergehend vom ursprünglichen Rahmen getrennt und an den neu erstellten Rahmen angefügt.

Dies ist ein fortgeschrittenes Überridable.

## <a name="coleserverdocdeactivateandundo"></a><a name="deactivateandundo"></a>COleServerDoc::DeactivateAndUndo

Rufen Sie diese Funktion auf, wenn Ihre Anwendung Rückgängig unterstützt und der Benutzer Nach dem Aktivieren eines Elements, aber vor der Bearbeitung Rückgängig auswählt.

```
BOOL DeactivateAndUndo();
```

### <a name="return-value"></a>Rückgabewert

Bei Erfolg ein Wert ungleich 0 (null), andernfalls 0 (null).

### <a name="remarks"></a>Bemerkungen

Wenn die Containeranwendung mithilfe der Microsoft Foundation-Klassenbibliothek geschrieben wird, wird durch Aufrufen dieser Funktion [COleClientItem::OnDeactivateAndundo](../../mfc/reference/coleclientitem-class.md#ondeactivateandundo) aufgerufen, wodurch die Benutzeroberfläche des Servers deaktiviert wird.

## <a name="coleserverdocdestroyinplaceframe"></a><a name="destroyinplaceframe"></a>COleServerDoc::DestroyInPlaceFrame

Das Framework ruft diese Funktion auf, um ein ortsnahes Framefenster zu zerstören und das Dokumentfenster der Serveranwendung vor der ortsseitigen Aktivierung in den Zustand zurückzuversetzen.

```
virtual void DestroyInPlaceFrame(COleIPFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Parameter

*pFrameWnd*<br/>
Zeigen Sie auf das zu zerstörende Bildfenster.

### <a name="remarks"></a>Bemerkungen

Dies ist ein fortgeschrittenes Überridable.

## <a name="coleserverdocdiscardundostate"></a><a name="discardundostate"></a>COleServerDoc::DiscardUndoState

Wenn der Benutzer einen Bearbeitungsvorgang ausführt, der nicht rückgängig gemacht werden kann, rufen Sie diese Funktion auf, um die Containeranwendung zu zwingen, ihre Rückgängig-Statusinformationen zu verwerfen.

```
BOOL DiscardUndoState();
```

### <a name="return-value"></a>Rückgabewert

Bei Erfolg ein Wert ungleich 0 (null), andernfalls 0 (null).

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird bereitgestellt, damit Server, die Undo unterstützen, Ressourcen freilassen können, die andernfalls von Rückgängig-Statusinformationen verbraucht würden, die nicht verwendet werden können.

## <a name="coleserverdocgetclientsite"></a><a name="getclientsite"></a>COleServerDoc::GetClientSite

Ruft einen Zeiger auf `IOleClientSite` die zugrunde liegende Schnittstelle ab.

```
LPOLECLIENTSITE GetClientSite() const;
```

### <a name="return-value"></a>Rückgabewert

Ruft einen Zeiger auf die zugrunde liegende [IOleClientSite-Schnittstelle](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite) ab.

## <a name="coleserverdocgetdocobjectserver"></a><a name="getdocobjectserver"></a>COleServerDoc::GetDocObjectServer

Überschreiben Sie diese Funktion, um ein neues `CDocObjectServer` Element zu erstellen und einen Zeiger darauf zurückzugeben.

```
virtual CDocObjectServer* GetDocObjectServer(LPOLEDOCUMENTSITE pDocSite);
```

### <a name="parameters"></a>Parameter

*pDocSite*<br/>
Zeigen Sie `IOleDocumentSite` mit dem Zeiger auf die Schnittstelle, die dieses Dokument mit dem Server verbindet.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CDocObjectServer`ein ; NULL, wenn der Vorgang fehlgeschlagen ist.

### <a name="remarks"></a>Bemerkungen

Wenn ein DocObject-Server aktiviert ist, zeigt die Rückgabe eines Nicht-NULL-Zeigers an, dass der Client DocObjects unterstützen kann. Die Standardimplementierung gibt NULL zurück.

Eine typische Implementierung für ein Dokument, das `CDocObjectServer` DocObjects unterstützt, weist einfach ein neues Objekt zu und gibt es an den Aufrufer zurück. Beispiel:

[!code-cpp[NVC_MFCOleServer#3](../../mfc/codesnippet/cpp/coleserverdoc-class_1.cpp)]

## <a name="coleserverdocgetembeddeditem"></a><a name="getembeddeditem"></a>COleServerDoc::GetEmbeddedItem

Rufen Sie diese Funktion auf, um einen Zeiger auf ein Element abzurufen, das das gesamte Dokument darstellt.

```
COleServerItem* GetEmbeddedItem();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein Element, das das gesamte Dokument darstellt; NULL, wenn der Vorgang fehlgeschlagen ist.

### <a name="remarks"></a>Bemerkungen

Es ruft [COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem)auf , eine virtuelle Funktion ohne Standardimplementierung.

## <a name="coleserverdocgetitemcliprect"></a><a name="getitemcliprect"></a>COleServerDoc::GetItemClipRect

Rufen `GetItemClipRect` Sie die Memberfunktion auf, um die Clipping-Rechteck-Koordinaten des Elements abzurufen, das bearbeitet wird.

```cpp
void GetItemClipRect(LPRECT lpClipRect) const;
```

### <a name="parameters"></a>Parameter

*lpClipRect*<br/>
Zeigen Sie `RECT` mit dem `CRect` Zeiger auf eine Struktur oder ein Objekt, um die Clipping-Rechteck-Koordinaten des Elements zu empfangen.

### <a name="remarks"></a>Bemerkungen

Koordinaten sind in Pixel relativ zum Clientbereich des Containeranwendungsfensters.

Das Zeichnen sollte nicht außerhalb des Zuschneiderechtecks erfolgen. Normalerweise wird das Zeichnen automatisch eingeschränkt. Verwenden Sie diese Funktion, um zu bestimmen, ob der Benutzer außerhalb des sichtbaren Teils des Dokuments gescrollt hat. Wenn dies der Fall ist, scrollen Sie das Containerdokument nach Bedarf durch einen Aufruf von [ScrollContainerBy](#scrollcontainerby).

## <a name="coleserverdocgetitemposition"></a><a name="getitemposition"></a>COleServerDoc::GetItemPosition

Rufen `GetItemPosition` Sie die Memberfunktion auf, um die Koordinaten des zu bearbeitenden Elements abzurufen.

```cpp
void GetItemPosition(LPRECT lpPosRect) const;
```

### <a name="parameters"></a>Parameter

*lpPosRect*<br/>
Zeigen Sie `RECT` auf eine `CRect` Struktur oder ein Objekt, um die Koordinaten des Elements zu empfangen.

### <a name="remarks"></a>Bemerkungen

Koordinaten sind in Pixel relativ zum Clientbereich des Containeranwendungsfensters.

Die Position des Elements kann mit dem aktuellen Zuschneiderechteck verglichen werden, um zu bestimmen, inwieweit das Element auf dem Bildschirm sichtbar (oder nicht sichtbar) ist.

## <a name="coleserverdocgetzoomfactor"></a><a name="getzoomfactor"></a>COleServerDoc::GetZoomFactor

Die `GetZoomFactor` Memberfunktion bestimmt den "Zoomfaktor" eines Elements, das für die ortsspezifische Bearbeitung aktiviert wurde.

```
BOOL GetZoomFactor(
    LPSIZE lpSizeNum = NULL,
    LPSIZE lpSizeDenom = NULL,
    LPCRECT lpPosRect = NULL) const;
```

### <a name="parameters"></a>Parameter

*lpSizeNum*<br/>
Zeiger auf ein Klasseobjekt, `CSize` das den Zähler des Zoomfaktors enthält. Kann den Wert NULL haben.

*lpSizeDenom*<br/>
Zeiger auf ein Klasseobjekt, `CSize` das den Nenner des Zoomfaktors enthält. Kann den Wert NULL haben.

*lpPosRect*<br/>
Zeiger auf ein Klasseobjekt, `CRect` das die neue Position des Elements beschreibt. Wenn dieses Argument NULL ist, verwendet die Funktion die aktuelle Position des Elements.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn das Element für die ortsspezifische Bearbeitung aktiviert ist und sein Zoomfaktor nicht 100 % (1:1) beträgt; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Der Zoomfaktor in Pixel ist der Anteil der Größe des Elements an seiner aktuellen Ausdehnung. Wenn die Containeranwendung die Ausdehnung des Elements nicht festgelegt hat, wird seine natürliche Ausdehnung (wie durch [COleServerItem::OnGetExtent](../../mfc/reference/coleserveritem-class.md#ongetextent)bestimmt) verwendet.

Die Funktion legt die ersten beiden Argumente auf den Zähler und Nenner des "Zoom-Faktors" des Elements fest. Wenn das Element nicht bearbeitet wird, legt die Funktion diese Argumente auf einen Standardwert von 100 % (oder 1:1) fest und gibt Null zurück. Weitere Informationen finden Sie unter Technical Note 40, [MFC/OLE In-Place Reizing and Zooming](../../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).

## <a name="coleserverdocisdocobject"></a><a name="isdocobject"></a>COleServerDoc::IsDocObject

Bestimmt, ob es sich bei dem Dokument um ein DocObject handelt.

```
BOOL IsDocObject() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn es sich bei dem Dokument um ein DocObject handelt; andernfalls FALSE.

## <a name="coleserverdocisembedded"></a><a name="isembedded"></a>COleServerdoc::IsEmbedded

Rufen `IsEmbedded` Sie die Memberfunktion auf, um zu bestimmen, ob das Dokument ein objekt darstellt, das in einen Container eingebettet ist.

```
BOOL IsEmbedded() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert `COleServerDoc` ungleich Null, wenn es sich bei dem Objekt um ein Dokument handelt, das ein in einen Container eingebettetes Objekt darstellt. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Ein aus einer Datei geladenes Dokument ist nicht eingebettet, obwohl es von einer Containeranwendung als Verknüpfung bearbeitet werden kann. Ein Dokument, das in ein Containerdokument eingebettet ist, gilt als eingebettet.

## <a name="coleserverdocisinplaceactive"></a><a name="isinplaceactive"></a>COleServerdoc::IsInPlaceActive

Rufen `IsInPlaceActive` Sie die Memberfunktion auf, um zu bestimmen, ob sich das Element derzeit im aktiven Zustand befindet.

```
BOOL IsInPlaceActive() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert `COleServerDoc` ungleich Null, wenn das Objekt aktiv ist; andernfalls 0.

## <a name="coleserverdocnotifychanged"></a><a name="notifychanged"></a>COleServerDoc::NotifyChanged

Rufen Sie diese Funktion auf, um alle verknüpften Elemente, die mit dem Dokument verbunden sind, zu benachrichtigen, dass sich das Dokument geändert hat.

```cpp
void NotifyChanged();
```

### <a name="remarks"></a>Bemerkungen

In der Regel rufen Sie diese Funktion auf, nachdem der Benutzer einige globale Attribute wie die Dimensionen des Serverdokuments geändert hat. Wenn ein OLE-Element mit dem Dokument mit einer automatischen Verknüpfung verknüpft ist, wird das Element aktualisiert, um die Änderungen widerzuspiegeln. In Containeranwendungen, die mit der Microsoft Foundation-Klassenbibliothek geschrieben wurden, wird die [OnChange-Memberfunktion](../../mfc/reference/coleclientitem-class.md#onchange) von `COleClientItem` aufgerufen.

> [!NOTE]
> Diese Funktion ist für die Kompatibilität mit OLE 1 enthalten. Neue Anwendungen sollten [UpdateAllItems](#updateallitems)verwenden.

## <a name="coleserverdocnotifyclosed"></a><a name="notifyclosed"></a>COleServerDoc::NotifyClosed

Rufen Sie diese Funktion auf, um die Container darüber zu benachrichtigen, dass das Dokument geschlossen wurde.

```cpp
void NotifyClosed();
```

### <a name="remarks"></a>Bemerkungen

Wenn der Benutzer den Befehl Schließen aus `NotifyClosed` dem `COleServerDoc`Menü Datei auswählt, wird von der Implementierung der [OnCloseDocument-Memberfunktion](../../mfc/reference/cdocument-class.md#onclosedocument) aufgerufen. In Containeranwendungen, die mit der Microsoft Foundation-Klassenbibliothek geschrieben wurden, wird die [OnChange-Memberfunktion](../../mfc/reference/coleclientitem-class.md#onchange) von `COleClientItem` aufgerufen.

## <a name="coleserverdocnotifyrename"></a><a name="notifyrename"></a>COleServerDoc::NotifyRename

Rufen Sie diese Funktion auf, nachdem der Benutzer das Serverdokument umbenannt hat.

```cpp
void NotifyRename(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>Parameter

*lpszNewName*<br/>
Zeiger auf eine Zeichenfolge, die den neuen Namen des Serverdokuments angibt; Dies ist in der Regel ein vollqualifizierter Pfad.

### <a name="remarks"></a>Bemerkungen

Wenn der Benutzer den Befehl Speichern unter `NotifyRename` aus dem `COleServerDoc`Menü Datei auswählt, wird von der Implementierung der [OnSaveDocument-Memberfunktion](../../mfc/reference/cdocument-class.md#onsavedocument) aufgerufen. Diese Funktion benachrichtigt die OLE-System-DLLs, die wiederum die Container benachrichtigen. In Containeranwendungen, die mit der Microsoft Foundation-Klassenbibliothek geschrieben wurden, wird die [OnChange-Memberfunktion](../../mfc/reference/coleclientitem-class.md#onchange) von `COleClientItem` aufgerufen.

## <a name="coleserverdocnotifysaved"></a><a name="notifysaved"></a>COleServerDoc::NotifySaved

Rufen Sie diese Funktion auf, nachdem der Benutzer das Serverdokument speichert.

```cpp
void NotifySaved();
```

### <a name="remarks"></a>Bemerkungen

Wenn der Benutzer den Befehl Speichern aus `NotifySaved` dem Menü `COleServerDoc`Datei auswählt, wird von der Implementierung von [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument)für Sie aufgerufen. Diese Funktion benachrichtigt die OLE-System-DLLs, die wiederum die Container benachrichtigen. In Containeranwendungen, die mit der Microsoft Foundation-Klassenbibliothek geschrieben wurden, wird die [OnChange-Memberfunktion](../../mfc/reference/coleclientitem-class.md#onchange) von `COleClientItem` aufgerufen.

## <a name="coleserverdoconclose"></a><a name="onclose"></a>COleServerDoc::OnClose

Wird vom Framework aufgerufen, wenn ein Container anfordert, dass das Serverdokument geschlossen wird.

```
virtual void OnClose(OLECLOSE dwCloseOption);
```

### <a name="parameters"></a>Parameter

*dwCloseOption*<br/>
Ein Wert aus der Enumeration OLECLOSE. Dieser Parameter kann einen der folgenden Werte aufweisen:

- OLECLOSE_SAVEIFDIRTY Die Datei wird gespeichert, wenn sie geändert wurde.

- OLECLOSE_NOSAVE Die Datei wird geschlossen, ohne gespeichert zu werden.

- OLECLOSE_PROMPTSAVE Wenn die Datei geändert wurde, wird der Benutzer zum Speichern aufgefordert.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung `CDocument::OnCloseDocument`sruft auf.

Weitere Informationen und zusätzliche Werte finden Sie unter [OLECLOSE](/windows/win32/api/oleidl/ne-oleidl-oleclose) im Windows SDK.

## <a name="coleserverdocondeactivate"></a><a name="ondeactivate"></a>COleServerDoc::OnDeactivate

Wird vom Framework aufgerufen, wenn der Benutzer ein eingebettetes oder verknüpftes Element deaktiviert, das derzeit aktiv ist.

```
virtual void OnDeactivate();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion stellt die Benutzeroberfläche der Containeranwendung in ihren ursprünglichen Zustand wieder her und zerstört alle Menüs und andere Steuerelemente, die für die aktive Aktivierung an Ort und Stelle erstellt wurden.

Die Undo-Statusinformationen sollten an dieser Stelle bedingungslos freigegeben werden.

Weitere Informationen finden Sie im Artikel [Aktivierung](../../mfc/activation-cpp.md)..

## <a name="coleserverdocondeactivateui"></a><a name="ondeactivateui"></a>COleServerDoc::OnDeactivateUI

Wird aufgerufen, wenn der Benutzer ein Element deaktiviert, das an Ort und Stelle aktiviert wurde.

```
virtual void OnDeactivateUI(BOOL bUndoable);
```

### <a name="parameters"></a>Parameter

*bUndoable*<br/>
Gibt an, ob die Bearbeitungsänderungen rückgängig gemacht werden können.

### <a name="remarks"></a>Bemerkungen

Diese Funktion stellt die Benutzeroberfläche der Containeranwendung in ihren ursprünglichen Zustand zurück und blendt alle Menüs und andere Steuerelemente aus, die für die aktive Aktivierung an Ort und Stelle erstellt wurden.

Das Framework legt *bUndoable* immer auf FALSE fest. Wenn der Server Rückgängig machen unterstützt und ein Vorgang ausgeführt werden kann, rufen Sie die Basisklassenimplementierung auf, wobei *bUndoable* auf TRUE festgelegt ist.

## <a name="coleserverdocondocwindowactivate"></a><a name="ondocwindowactivate"></a>COleServerdoc::OnDocWindowActivate

Das Framework ruft diese Funktion auf, um ein Dokumentfenster für die ortsnahe Bearbeitung zu aktivieren oder zu deaktivieren.

```
virtual void OnDocWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>Parameter

*bAktivieren*<br/>
Gibt an, ob das Dokumentfenster aktiviert oder deaktiviert werden soll.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung entfernt oder fügt die Benutzeroberflächenelemente auf Frameebene entsprechend hinzu. Überschreiben Sie diese Funktion, wenn Sie zusätzliche Aktionen ausführen möchten, wenn das Dokument, das Ihr Element enthält, aktiviert oder deaktiviert ist.

Weitere Informationen finden Sie im Artikel [Aktivierung](../../mfc/activation-cpp.md)..

## <a name="coleserverdoconexecolecmd"></a><a name="onexecolecmd"></a>COleServerDoc::OnExecOleCmd

Das Framework ruft diese Funktion auf, um einen angegebenen Befehl auszuführen oder Hilfe für den Befehl anzuzeigen.

```
virtual HRESULT OnExecOleCmd(
    const GUID* pguidCmdGroup,
    DWORD nCmdID,
    DWORD nCmdExecOpt,
    VARIANTARG* pvarargIn,
    VARIANTARG* pvarargOut);
```

### <a name="parameters"></a>Parameter

*pguidCmdGroup*<br/>
Ein Zeiger auf eine GUID, der eine Reihe von Befehlen identifiziert. Kann NULL sein, um die Standardbefehlsgruppe anzugeben.

*nCmdID*<br/>
Den auszuführenden Befehl. Muss sich in der von *pguidCmdGroup*identifizierten Gruppe aufgeben.

*nCmdExecOut*<br/>
Die Art und Weise, wie das Objekt den Befehl ausführen soll, einen oder mehrere der folgenden Werte aus der OLECMDEXECOPT-Enumeration:

OLECMDEXECOPT_DODEFAULT

OLECMDEXECOPT_PROMPTUSER

OLECMDEXECOPT_DONTPROMPTUSER

OLECMDEXECOPT_SHOWHELP

*pvarargIn*<br/>
Zeiger auf ein VARIANTARG, das Eingabeargumente für den Befehl enthält. Kann den Wert NULL haben.

*pvarargOut*<br/>
Zeiger auf ein VARIANTARG, um die Ausgaberückgabewerte vom Befehl zu empfangen. Kann den Wert NULL haben.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück, wenn erfolgreich; andernfalls einer der folgenden Fehlercodes:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|E_UNEXPECTED|Unerwarteter Fehler|
|E_FAIL|Fehler aufgetreten.|
|E_NOTIMPL|Gibt an, dass MFC selbst versuchen sollte, den Befehl zu übersetzen und zu senden|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* ist nicht NULL, gibt jedoch keine erkannte Befehlsgruppe an|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID* wird in der Gruppe *pguidCmdGroup* nicht als gültiger Befehl erkannt|
|OLECMDERR_DISABLED|Der von *nCmdID* identifizierte Befehl ist deaktiviert und kann nicht ausgeführt werden.|
|OLECMDERR_NOHELP|Anrufer bat um Hilfe für den von *nCmdID* identifizierten Befehl, aber es ist keine Hilfe verfügbar.|
|OLECMDERR_CANCELED|Benutzer hat die Ausführung abgebrochen|

### <a name="remarks"></a>Bemerkungen

`COleCmdUI`kann zum Aktivieren, Aktualisieren und Festlegen anderer Eigenschaften von DocObject-Benutzeroberflächenbefehlen verwendet werden. Nachdem die Befehle initialisiert wurden, `OnExecOleCmd`können Sie sie mit ausführen.

Das Framework ruft die Funktion auf, bevor versucht wird, einen OLE-Dokumentbefehl zu übersetzen und zu verschicken. Sie müssen diese Funktion nicht überschreiben, um Standard-OLE-Dokumentbefehle zu verarbeiten, aber Sie müssen eine Außerkraftsetzung dieser Funktion bereitstellen, wenn Sie Ihre eigenen benutzerdefinierten Befehle behandeln oder Befehle behandeln möchten, die Parameter akzeptieren oder Ergebnisse zurückgeben.

Die meisten Befehle verwenden keine Argumente oder geben Keine Werte zurück. Für die meisten Befehle kann der Aufrufer NULLs für *pvarargIn* und *pvarargOut*übergeben. Bei Befehlen, die Eingabewerte erwarten, kann der Aufrufer eine VARIANTARG-Variable deklarieren und initialisieren und einen Zeiger an die Variable in *pvarargIn*übergeben. Bei Befehlen, die einen einzelnen Wert erfordern, kann das Argument direkt im VARIANTARG gespeichert und an die Funktion übergeben werden. Innerhalb des VARIANTARG müssen mehrere Argumente mit einem der `IDispatch` unterstützten Typen (z. B. SAFEARRAY ) gepackt werden.

Wenn ein Befehl Argumente zurückgibt, wird erwartet, dass der Aufrufer ein VARIANTARG deklariert, es in VT_EMPTY initialisiert und seine Adresse in *pvarargOut*übergibt. Wenn ein Befehl einen einzelnen Wert zurückgibt, kann das Objekt diesen Wert direkt in *pvarargOut*speichern. Mehrere Ausgabewerte müssen in einer weise verpackt werden, die für das VARIANTARG geeignet ist.

Die Basisklassenimplementierung dieser Funktion führt die OLE_COMMAND_MAP Strukturen, die dem Befehlsziel zugeordnet sind, und versucht, den Befehl an einen entsprechenden Handler zu senden. Die Basisklassenimplementierung funktioniert nur mit Befehlen, die keine Argumente akzeptieren oder Werte zurückgeben. Wenn Sie Befehle behandeln müssen, die Argumente akzeptieren oder Werte zurückgeben, müssen Sie diese Funktion überschreiben und selbst mit den Parametern *pvarargIn* und *pvarargOut* arbeiten.

## <a name="coleserverdoconframewindowactivate"></a><a name="onframewindowactivate"></a>COleServerDoc::OnFrameWindowActivate

Das Framework ruft diese Funktion auf, wenn das Framefenster der Containeranwendung aktiviert oder deaktiviert wird.

```
virtual void OnFrameWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>Parameter

*bAktivieren*<br/>
Gibt an, ob das Rahmenfenster aktiviert oder deaktiviert werden soll.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung bricht alle Hilfemodi ab, in denen sich das Rahmenfenster befinden könnte. Überschreiben Sie diese Funktion, wenn Sie eine spezielle Verarbeitung durchführen möchten, wenn das Rahmenfenster aktiviert oder deaktiviert ist.

Weitere Informationen finden Sie im Artikel [Aktivierung](../../mfc/activation-cpp.md)..

## <a name="coleserverdocongetembeddeditem"></a><a name="ongetembeddeditem"></a>COleServerDoc::OnGetEmbeddedItem

Wird vom Framework aufgerufen, wenn eine Containeranwendung die Serveranwendung aufruft, um ein eingebettetes Element zu erstellen oder zu bearbeiten.

```
virtual COleServerItem* OnGetEmbeddedItem() = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein Element, das das gesamte Dokument darstellt; NULL, wenn der Vorgang fehlgeschlagen ist.

### <a name="remarks"></a>Bemerkungen

Es ist keine Standardimplementierung vorhanden. Sie müssen diese Funktion überschreiben, um ein Element zurückzugeben, das das gesamte Dokument darstellt. Dieser Rückgabewert sollte ein `COleServerItem`Objekt einer -derived-Klasse sein.

## <a name="coleserverdoconreactivateandundo"></a><a name="onreactivateandundo"></a>COleServerDoc::OnReactivateAndUndo

Das Framework ruft diese Funktion auf, wenn der Benutzer Änderungen rückgängig macht, die an einem Element vorgenommen wurden, das aktiviert, geändert und anschließend deaktiviert wurde.

```
virtual BOOL OnReactivateAndUndo();
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung führt nichts aus, außer FALSE zurückzugeben, um einen Fehler anzuzeigen.

Überschreiben Sie diese Funktion, wenn Ihre Anwendung Rückgängig machen unterstützt. Normalerweise führen Sie den Rückgängig-Vorgang aus und `ActivateInPlace`aktivieren das Element dann, indem Sie aufrufen. Wenn die Containeranwendung mit der Microsoft Foundation-Klassenbibliothek geschrieben wird, bewirkt der Aufruf, `COleClientItem::ReactivateAndUndo` dass diese Funktion aufgerufen wird.

## <a name="coleserverdoconresizeborder"></a><a name="onresizeborder"></a>COleServerDoc::OnResizeBorder

Das Framework ruft diese Funktion auf, wenn die Rahmenfenster der Containeranwendung die Größe ändern.

```
virtual void OnResizeBorder(
    LPCRECT lpRectBorder,
    LPOLEINPLACEUIWINDOW lpUIWindow,
    BOOL bFrame);
```

### <a name="parameters"></a>Parameter

*lpRectBorder*<br/>
Zeiger auf `RECT` eine Struktur `CRect` oder ein Objekt, das die Koordinaten des Rahmens angibt.

*lpUIWindow*<br/>
Zeiger auf ein Klasseobjekt, `IOleInPlaceUIWindow` das die aktuelle in-Ort-Bearbeitungssitzung besitzt.

*bFrame*<br/>
TRUE, wenn *lpUIWindow* auf das Framefenster der obersten Ebene der Containeranwendung verweist, oder FALSE, wenn *lpUIWindow* auf das Rahmenfenster der Containeranwendung auf Dokumentebene verweist.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ändert die Größe und passt Symbolleisten und andere Benutzeroberflächenelemente entsprechend der neuen Fenstergröße an.

Weitere Informationen finden Sie unter [IOleInPlaceUIWindow](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceuiwindow) im Windows SDK.

Dies ist ein fortgeschrittenes Überridable.

## <a name="coleserverdoconsethostnames"></a><a name="onsethostnames"></a>COleServerDoc::OnSetHostNames

Wird vom Framework aufgerufen, wenn der Container die Hostnamen für dieses Dokument festlegt oder ändert.

```
virtual void OnSetHostNames(
    LPCTSTR lpszHost,
    LPCTSTR lpszHostObj);
```

### <a name="parameters"></a>Parameter

*lpszHost*<br/>
Zeiger auf eine Zeichenfolge, die den Namen der Containeranwendung angibt.

*lpszHostObj*<br/>
Zeiger auf eine Zeichenfolge, die den Namen des Containers für das Dokument angibt.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung ändert den Dokumenttitel für alle Ansichten, die auf dieses Dokument verweisen.

Überschreiben Sie diese Funktion, wenn Ihre Anwendung die Titel durch einen anderen Mechanismus festlegt.

## <a name="coleserverdoconsetitemrects"></a><a name="onsetitemrects"></a>COleServerDoc::OnSetItemRects

Das Framework ruft diese Funktion auf, um das platznahe Bearbeitungsrahmenfenster innerhalb des Rahmenfensters der Containeranwendung zu positionieren.

```
virtual void OnSetItemRects(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>Parameter

*lpPosRect*<br/>
Zeiger auf `RECT` eine Struktur `CRect` oder ein Objekt, das die Position des platzierten Rahmenfensters relativ zum Clientbereich der Containeranwendung angibt.

*lpClipRect*<br/>
Zeiger auf `RECT` eine Struktur `CRect` oder ein Objekt, das das Clipping-Rechteck des platzierten Rahmenfensters relativ zum Clientbereich der Containeranwendung angibt.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um ggf. den Zoomfaktor der Ansicht zu aktualisieren.

Diese Funktion wird in der `RequestPositionChange` Regel als Reaktion auf einen Aufruf aufgerufen, obwohl sie jederzeit vom Container aufgerufen werden kann, um eine Positionsänderung für das eingefügte Element anzufordern.

## <a name="coleserverdoconshowcontrolbars"></a><a name="onshowcontrolbars"></a>COleServerdoc::OnShowControlBars

Das Framework ruft diese Funktion auf, um die Steuerleisten der Serveranwendung anzuzeigen oder auszublenden, die dem Framefenster zugeordnet sind, das von *pFrameWnd*identifiziert wird.

```
virtual void OnShowControlBars(
    CFrameWnd* pFrameWnd,
    BOOL bShow);
```

### <a name="parameters"></a>Parameter

*pFrameWnd*<br/>
Zeigen Sie mit dem Zeiger auf das Rahmenfenster, dessen Steuerleisten ausgeblendet oder angezeigt werden sollen.

*bShow*<br/>
Bestimmt, ob Steuerleisten angezeigt oder ausgeblendet werden.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung zählt alle Steuerelementleisten auf, die sich im Besitz dieses Rahmenfensters befinden, und blendet sie aus oder zeigt sie an.

## <a name="coleserverdoconshowdocument"></a><a name="onshowdocument"></a>COleServerDoc::OnShowDocument

Das Framework `OnShowDocument` ruft die Funktion auf, wenn das Serverdokument ausgeblendet oder angezeigt werden muss.

```
virtual void OnShowDocument(BOOL bShow);
```

### <a name="parameters"></a>Parameter

*bShow*<br/>
Gibt an, ob die Benutzeroberfläche für das Dokument angezeigt oder ausgeblendet werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn *bShow* TRUE ist, aktiviert die Standardimplementierung ggf. die Serveranwendung und bewirkt, dass die Containeranwendung das Fenster scrollt, damit das Element sichtbar ist. Wenn *bShow* FALSE ist, deaktiviert die Standardimplementierung das `OnDeactivate`Element durch einen Aufruf von , und zerstört oder blendet dann alle Rahmenfenster aus, die für das Dokument erstellt wurden, mit Ausnahme des ersten. Wenn keine sichtbaren Dokumente verbleiben, blendet die Standardimplementierung die Serveranwendung aus.

## <a name="coleserverdoconupdatedocument"></a><a name="onupdatedocument"></a>COleServerDoc::OnUpdateDocument

Wird vom Framework aufgerufen, wenn ein Dokument gespeichert wird, das ein eingebettetes Element in einem zusammengesetzten Dokument ist.

```
virtual BOOL OnUpdateDocument();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Dokument erfolgreich aktualisiert wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung ruft die [Memberfunktionen COleServerDoc::NotifySaved](#notifysaved) und [COleServerDoc::SaveEmbedding](#saveembedding) auf und markiert dann das Dokument als sauber. Überschreiben Sie diese Funktion, wenn Sie beim Aktualisieren eines eingebetteten Elements eine spezielle Verarbeitung durchführen möchten.

## <a name="coleserverdocrequestpositionchange"></a><a name="requestpositionchange"></a>COleServerDoc::RequestPositionChange

Rufen Sie diese Memberfunktion auf, damit die Containeranwendung die Position des Elements ändert.

```cpp
void RequestPositionChange(LPCRECT lpPosRect);
```

### <a name="parameters"></a>Parameter

*lpPosRect*<br/>
Zeiger auf `RECT` eine Struktur `CRect` oder ein Objekt, das die neue Position des Elements enthält.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird in der `UpdateAllItems`Regel aufgerufen (in Verbindung mit ), wenn sich die Daten in einem aktiven Objekt an Ort und Stelle geändert haben. Nach diesem Aufruf kann der Container die Änderung `OnSetItemRects`durch Aufrufen von ausführen. Die resultierende Position kann sich von der angeforderten unterscheiden.

## <a name="coleserverdocsaveembedding"></a><a name="saveembedding"></a>COleServerDoc::Einbetten speichern

Rufen Sie diese Funktion auf, um die Containeranwendung anzuweisen, das eingebettete Objekt zu speichern.

```cpp
void SaveEmbedding();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird `OnUpdateDocument`automatisch von aufgerufen. Beachten Sie, dass diese Funktion bewirkt, dass das Element auf dem Datenträger aktualisiert wird, sodass es normalerweise nur als Ergebnis einer bestimmten Benutzeraktion aufgerufen wird.

## <a name="coleserverdocscrollcontainerby"></a><a name="scrollcontainerby"></a>COleServerDoc::ScrollContainerBy

Rufen `ScrollContainerBy` Sie die Memberfunktion auf, um das Containerdokument `sizeScroll`um den Betrag in Pixel zu scrollen, der durch angegeben wird.

```
BOOL ScrollContainerBy(CSize sizeScroll);
```

### <a name="parameters"></a>Parameter

*sizeScroll*<br/>
Gibt an, wie weit das Containerdokument gescrollt werden soll.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Positive Werte zeigen an, nach unten und rechts zu scrollen; negative Werte zeigen an, dass der Bildlauf nach oben und nach links führt.

## <a name="coleserverdocupdateallitems"></a><a name="updateallitems"></a>COleServerDoc::UpdateAllItems

Rufen Sie diese Funktion auf, um alle verknüpften Elemente, die mit dem Dokument verbunden sind, zu benachrichtigen, dass sich das Dokument geändert hat.

```cpp
void UpdateAllItems(
    COleServerItem* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL,
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>Parameter

*pSender*<br/>
Zeigen Sie auf das Element, das das Dokument geändert hat, oder NULL, wenn alle Elemente aktualisiert werden sollen.

*lHint*<br/>
Enthält Informationen zur Änderung.

*pHint*<br/>
Zeiger auf ein Objekt, das Informationen über die Änderung speichert.

*nDrawAspect*<br/>
Bestimmt, wie das Element gezeichnet werden soll. Dies ist ein Wert aus der DVASPECT-Enumeration. Dieser Parameter kann einen der folgenden Werte aufweisen:

- DVASPECT_CONTENT-Element wird so dargestellt, dass es als eingebettetes Objekt in seinem Container angezeigt werden kann.

- DVASPECT_THUMBNAIL Element wird in einer "Miniaturansicht"-Darstellung gerendert, sodass es in einem Browsertool angezeigt werden kann.

- DVASPECT_ICON Element wird durch ein Symbol dargestellt.

- DVASPECT_DOCPRINT-Element wird dargestellt, als ob es mit dem Befehl Drucken aus dem Menü Datei gedruckt würde.

### <a name="remarks"></a>Bemerkungen

In der Regel rufen Sie diese Funktion auf, nachdem der Benutzer das Serverdokument geändert hat. Wenn ein OLE-Element mit dem Dokument mit einer automatischen Verknüpfung verknüpft ist, wird das Element aktualisiert, um die Änderungen widerzuspiegeln. In Containeranwendungen, die mit der Microsoft Foundation-Klassenbibliothek geschrieben wurden, wird die [OnChange-Memberfunktion](../../mfc/reference/coleclientitem-class.md#onchange) von `COleClientItem` aufgerufen.

Diese Funktion `OnUpdate` ruft die Memberfunktion für jedes Element des Dokuments mit Ausnahme des sendenden Elements, der übergebenden *pHint*, *lHint*und *nDrawAspect*auf. Verwenden Sie diese Parameter, um Informationen zu den Elementen über die am Dokument vorgenommenen Änderungen zu übergeben. Sie können Informationen mit *lHint* kodieren oder eine `CObject`-abgeleitete Klasse definieren, um Informationen über die Änderungen zu speichern und ein Objekt dieser Klasse mit *pHint*zu übergeben. Überschreiben `OnUpdate` Sie die `COleServerItem`Memberfunktion in ihrer -derived-Klasse, um die Aktualisierung jedes Elements zu optimieren, je nachdem, ob sich die Darstellung geändert hat.

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COleLinkingDoc-Klasse](../../mfc/reference/colelinkingdoc-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleDocument-Klasse](../../mfc/reference/coledocument-class.md)<br/>
[COleLinkingDoc-Klasse](../../mfc/reference/colelinkingdoc-class.md)<br/>
[COleTemplateServer-Klasse](../../mfc/reference/coletemplateserver-class.md)
