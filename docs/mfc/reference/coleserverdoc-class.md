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
ms.openlocfilehash: eec94a32fa0963d4cf2eccae0fb9e2423e75ffdc
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427002"
---
# <a name="coleserverdoc-class"></a>COleServerDoc-Klasse

Die Basisklasse für OLE-Serverdokumente.

## <a name="syntax"></a>Syntax

```
class AFX_NOVTABLE COleServerDoc : public COleLinkingDoc
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[COleServerDoc:: COleServerDoc](#coleserverdoc)|Erstellt ein `COleServerDoc`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[COleServerDoc:: activatedocobject](#activatedocobject)|Aktiviert das zugeordnete DocObject-Dokument.|
|[COleServerDoc:: activatanplace](#activateinplace)|Aktiviert das Dokument für die direkte Bearbeitung.|
|[COleServerDoc::D eactivateandundo](#deactivateandundo)|Deaktiviert die Benutzeroberfläche des Servers.|
|[COleServerDoc::D iscardundostate](#discardundostate)|Verwirft rückgängig-Statusinformationen.|
|[COleServerDoc:: GetClientSite](#getclientsite)|Ruft einen Zeiger auf die zugrunde liegende `IOleClientSite`-Schnittstelle ab.|
|[COleServerDoc:: getembeddeditem](#getembeddeditem)|Gibt einen Zeiger auf ein Element zurück, das das gesamte Dokument darstellt.|
|[COleServerDoc:: getitemcliprect](#getitemcliprect)|Gibt das aktuelle Clippingrechteck für die direkte Bearbeitung zurück.|
|[COleServerDoc:: getitemposition](#getitemposition)|Gibt das aktuelle Positions Rechteck relativ zum Client Bereich der Containeranwendung für die direkte Bearbeitung zurück.|
|[COleServerDoc:: getzoomfactor](#getzoomfactor)|Gibt den Zoomfaktor in Pixel zurück.|
|[COleServerDoc:: isdocobject](#isdocobject)|Bestimmt, ob das Dokument ein DocObject ist.|
|[COleServerDoc:: isEmbedded](#isembedded)|Gibt an, ob das Dokument in ein Container Dokument eingebettet oder eigenständig ausgeführt wird.|
|[COleServerDoc:: isinplaceactive](#isinplaceactive)|Gibt "true" zurück, wenn das Element gerade direkt aktiviert ist.|
|[COleServerDoc:: notifychanged](#notifychanged)|Benachrichtigt Container, dass der Benutzer das Dokument geändert hat.|
|[COleServerDoc:: notifyclosed](#notifyclosed)|Benachrichtigt Container, dass der Benutzer das Dokument geschlossen hat.|
|[COleServerDoc:: notifyrename](#notifyrename)|Benachrichtigt Container, dass der Benutzer das Dokument umbenannt hat.|
|[COleServerDoc:: notifygespeicherter](#notifysaved)|Benachrichtigt Container, dass der Benutzer das Dokument gespeichert hat.|
|[COleServerDoc:: ondeaktivieren](#ondeactivate)|Wird von Framework aufgerufen, wenn der Benutzer ein Element deaktiviert, das direkt aktiviert wurde.|
|[COleServerDoc:: onde activateui](#ondeactivateui)|Wird von Framework aufgerufen, um Steuerelemente und andere Elemente der Benutzeroberfläche zu zerstören, die für die direkte Aktivierung erstellt wurden.|
|[COleServerDoc:: ondocwindowaktivierungs](#ondocwindowactivate)|Wird von Framework aufgerufen, wenn das Dokument Rahmen Fenster des Containers aktiviert oder deaktiviert wird.|
|[COleServerDoc:: onresizeborder](#onresizeborder)|Wird von Framework aufgerufen, wenn die Größe des Rahmen Fensters oder Dokument Fensters der Containeranwendung geändert wird.|
|[COleServerDoc:: onshowcontrolbars](#onshowcontrolbars)|Wird von Framework aufgerufen, um Steuer leisten zur direkten Bearbeitung anzuzeigen oder auszublenden.|
|[COleServerDoc:: onupdatedocument](#onupdatedocument)|Wird von Framework aufgerufen, wenn ein Server Dokument, das ein eingebettetes Element ist, gespeichert wird und die Kopie des Containers des Containers aktualisiert wird.|
|[COleServerDoc:: requestpositionchange](#requestpositionchange)|Ändert die Position des direkten Bearbeitungs Rahmens.|
|[COleServerDoc:: saveeinbettungen](#saveembedding)|Weist die Containeranwendung an, das Dokument zu speichern.|
|[COleServerDoc:: scrollcontainerby](#scrollcontainerby)|Scrollt im Container Dokument.|
|[COleServerDoc:: updateallitems](#updateallitems)|Benachrichtigt Container, dass der Benutzer das Dokument geändert hat.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|Beschreibung|
|----------|-----------------|
|[COleServerDoc:: kreateinplaceframe](#createinplaceframe)|Wird von Framework aufgerufen, um ein Rahmen Fenster für die direkte Bearbeitung zu erstellen.|
|[COleServerDoc::D estroyinplaceframe](#destroyinplaceframe)|Wird von Framework aufgerufen, um ein Rahmen Fenster für die direkte Bearbeitung zu zerstören.|
|[COleServerDoc:: getdocobjectserver](#getdocobjectserver)|Überschreiben Sie diese Funktion, um ein neues `CDocObjectServer` Objekt zu erstellen, und geben Sie an, dass dieses Dokument ein DocObject-Container ist|
|[COleServerDoc:: OnClose](#onclose)|Wird von Framework aufgerufen, wenn ein Container eine Anforderung zum Schließen des Dokuments anfordert.|
|[COleServerDoc:: onexecolecmd](#onexecolecmd)|Führt einen angegebenen Befehl aus oder zeigt die Hilfe für den Befehl an.|
|[COleServerDoc:: onframewindowaktivierungs](#onframewindowactivate)|Wird von Framework aufgerufen, wenn das Rahmen Fenster des Containers aktiviert oder deaktiviert wird.|
|[COleServerDoc:: OnGetEmbeddedItem](#ongetembeddeditem)|Wird aufgerufen, um einen `COleServerItem` zu erhalten, der das gesamte Dokument darstellt. wird verwendet, um ein eingebettetes Element zu erhalten. Implementierung erforderlich.|
|[COleServerDoc:: onreactivateandundo](#onreactivateandundo)|Wird von Framework aufgerufen, um bei der direkten Bearbeitung vorgenommene Änderungen rückgängig zu machen.|
|[COleServerDoc:: onmenthostnames](#onsethostnames)|Wird von Framework aufgerufen, wenn der Fenstertitel für ein eingebettetes Objekt von einem Container festgelegt wird.|
|[COleServerDoc:: onontitemrects](#onsetitemrects)|Wird von Framework aufgerufen, um das direkte Bearbeitungs Rahmen Fenster im Fenster der Containeranwendung zu positionieren.|
|[COleServerDoc:: onshowdocument](#onshowdocument)|Wird von Framework aufgerufen, um das Dokument anzuzeigen oder auszublenden.|

## <a name="remarks"></a>Hinweise

Ein Server Dokument kann [COleServerItem](../../mfc/reference/coleserveritem-class.md) -Objekte enthalten, die die Server Schnittstelle für eingebettete oder verknüpfte Elemente darstellen. Wenn eine Serveranwendung von einem Container gestartet wird, um ein eingebettetes Element zu bearbeiten, wird das Element als eigenes Server Dokument geladen; Das `COleServerDoc`-Objekt enthält nur ein `COleServerItem`-Objekt, das aus dem gesamten Dokument besteht. Wenn eine Serveranwendung von einem Container gestartet wird, um ein verknüpftes Element zu bearbeiten, wird ein vorhandenes Dokument von der Festplatte geladen. ein Teil des Dokument Inhalts wird hervorgehoben, um das verknüpfte Element anzugeben.

`COleServerDoc` Objekte können auch Elemente der [COleClientItem](../../mfc/reference/coleclientitem-class.md) -Klasse enthalten. Dies ermöglicht es Ihnen, Container Server Anwendungen zu erstellen. Das Framework stellt Funktionen bereit, mit denen die `COleClientItem` Elemente ordnungsgemäß gespeichert werden, während die `COleServerItem` Objekte gewartet werden.

Wenn die Serveranwendung keine Verknüpfungen unterstützt, enthält ein Server Dokument immer nur ein Server Element, das das gesamte eingebettete Objekt als Dokument darstellt. Wenn die Serveranwendung Links unterstützt, muss jedes Mal ein Server Element erstellt werden, wenn eine Auswahl in die Zwischenablage kopiert wird.

Um `COleServerDoc`zu verwenden, leiten Sie eine Klasse davon ab, und implementieren Sie die Member-Funktion [OnGetEmbeddedItem](#ongetembeddeditem) , die dem Server die Unterstützung eingebetteter Elemente ermöglicht. Leiten Sie eine Klasse von `COleServerItem` ab, um die Elemente in den Dokumenten zu implementieren, und geben Sie die Objekte dieser Klasse von `OnGetEmbeddedItem`zurück.

Um verknüpfte Elemente zu unterstützen, `COleServerDoc` die die [ongetlinkeditem](../../mfc/reference/colelinkingdoc-class.md#ongetlinkeditem) -Member-Funktion bereitstellt. Sie können die Standard Implementierung verwenden oder diese überschreiben, wenn Sie über eine eigene Methode zum Verwalten von Dokument Elementen verfügen.

Sie benötigen eine `COleServerDoc`abgeleitete Klasse für jeden Typ von Server Dokument, der von der Anwendung unterstützt wird. Wenn Ihre Serveranwendung z. b. Arbeitsblätter und Diagramme unterstützt, benötigen Sie zwei `COleServerDoc`abgeleitete Klassen.

Weitere Informationen zu Servern finden Sie im Artikel [Server: Implementieren eines Servers](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

`COleServerDoc`

## <a name="requirements"></a>Voraussetzungen

**Header:** Afxole. h

##  <a name="activatedocobject"></a>COleServerDoc:: activatedocobject

Aktiviert das zugeordnete DocObject-Dokument.

```
void ActivateDocObject();
```

### <a name="remarks"></a>Hinweise

Standardmäßig unterstützt `COleServerDoc` keine aktiven Dokumente (auch als docobjects bezeichnet). Informationen zum Aktivieren dieser Unterstützung finden Sie unter [getdocobjectserver](#getdocobjectserver) und Class [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md).

##  <a name="activateinplace"></a>COleServerDoc:: activatanplace

Aktiviert das Element für die direkte Bearbeitung.

```
BOOL ActivateInPlace();
```

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn erfolgreich; andernfalls 0 (null) gibt an, dass das Element vollständig geöffnet ist.

### <a name="remarks"></a>Hinweise

Diese Funktion führt alle Vorgänge aus, die für die direkte Aktivierung erforderlich sind. Es erstellt ein direktes Rahmen Fenster, aktiviert es und passt es an das Element an, richtet freigegebene Menüs und andere Steuerelemente ein, führt einen Bildlauf zum Element durch und legt den Fokus auf das direkte Rahmen Fenster fest.

Diese Funktion wird von der Standard Implementierung von [COleServerItem:: onShow](../../mfc/reference/coleserveritem-class.md#onshow)aufgerufen. Diese Funktion wird aufgerufen, wenn Ihre Anwendung ein anderes Verb für die direkte Aktivierung (z. b. Play) unterstützt.

##  <a name="coleserverdoc"></a>COleServerDoc:: COleServerDoc

Erstellt ein `COleServerDoc` Objekt, ohne eine Verbindung mit den OLE-System-DLLs herzustellen.

```
COleServerDoc();
```

### <a name="remarks"></a>Hinweise

Zum Öffnen der Kommunikation mit OLE muss [COleLinkingDoc:: Register](../../mfc/reference/colelinkingdoc-class.md#register) aufgerufen werden. Wenn Sie in Ihrer Anwendung [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) verwenden, wird `COleLinkingDoc::Register` für Sie durch `COleLinkingDoc`Implementierung von `OnNewDocument`, `OnOpenDocument`und `OnSaveDocument`aufgerufen.

##  <a name="createinplaceframe"></a>COleServerDoc:: kreateinplaceframe

Das Framework ruft diese Funktion auf, um ein Rahmen Fenster für die direkte Bearbeitung zu erstellen.

```
virtual COleIPFrameWnd* CreateInPlaceFrame(CWnd* pParentWnd);
```

### <a name="parameters"></a>Parameter

*pparser*<br/>
Zeiger auf das übergeordnete Fenster der Containeranwendung.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das direkte Rahmen Fenster oder NULL, wenn kein Fehler aufgetreten ist.

### <a name="remarks"></a>Hinweise

Die Standard Implementierung verwendet Informationen, die in der Dokument Vorlage angegeben sind, um den Frame zu erstellen. Die verwendete Ansicht ist die erste Ansicht, die für das Dokument erstellt wurde. Diese Ansicht wird temporär vom ursprünglichen Frame getrennt und an den neu erstellten Frame angefügt.

Hierbei handelt es sich um eine erweiterte über schreibbare.

##  <a name="deactivateandundo"></a>COleServerDoc::D eactivateandundo

Rufen Sie diese Funktion auf, wenn Ihre Anwendung rückgängig unterstützt und der Benutzer nach dem Aktivieren eines Elements rückgängig macht, bevor Sie es bearbeiten.

```
BOOL DeactivateAndUndo();
```

### <a name="return-value"></a>Rückgabewert

Bei Erfolg ein Wert ungleich 0 (null), andernfalls 0 (null).

### <a name="remarks"></a>Hinweise

Wenn die Containeranwendung mithilfe der Microsoft Foundation Class-Bibliothek geschrieben wird, bewirkt das Aufrufen dieser Funktion, dass [COleClientItem:: ondeactivateandundo](../../mfc/reference/coleclientitem-class.md#ondeactivateandundo) aufgerufen wird, wodurch die Benutzeroberfläche des Servers deaktiviert wird.

##  <a name="destroyinplaceframe"></a>COleServerDoc::D estroyinplaceframe

Das Framework ruft diese Funktion auf, um ein direktes Rahmen Fenster zu zerstören und das Dokument Fenster der Serveranwendung vor der direkten Aktivierung wieder in den Zustand zu versetzen.

```
virtual void DestroyInPlaceFrame(COleIPFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Parameter

*pframewnd*<br/>
Ein Zeiger auf das direkte Rahmen Fenster, das zerstört werden soll.

### <a name="remarks"></a>Hinweise

Hierbei handelt es sich um eine erweiterte über schreibbare.

##  <a name="discardundostate"></a>COleServerDoc::D iscardundostate

Wenn der Benutzer einen Bearbeitungsvorgang ausführt, der nicht rückgängig gemacht werden kann, rufen Sie diese Funktion auf, um das Verwerfen der rückgängig-Zustandsinformationen durch die Containeranwendung zu erzwingen.

```
BOOL DiscardUndoState();
```

### <a name="return-value"></a>Rückgabewert

Bei Erfolg ein Wert ungleich 0 (null), andernfalls 0 (null).

### <a name="remarks"></a>Hinweise

Diese Funktion wird bereitgestellt, damit Server, die rückgängig unterstützen, Ressourcen freigeben können, die andernfalls von nicht verwendbaren rückgängig-Zustandsinformationen genutzt werden.

##  <a name="getclientsite"></a>COleServerDoc:: GetClientSite

Ruft einen Zeiger auf die zugrunde liegende `IOleClientSite`-Schnittstelle ab.

```
LPOLECLIENTSITE GetClientSite() const;
```

### <a name="return-value"></a>Rückgabewert

Ruft einen Zeiger auf die zugrunde liegende [IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite) -Schnittstelle ab.

##  <a name="getdocobjectserver"></a>COleServerDoc:: getdocobjectserver

Überschreiben Sie diese Funktion, um ein neues `CDocObjectServer` Element zu erstellen und einen Zeiger darauf zurückzugeben.

```
virtual CDocObjectServer* GetDocObjectServer(LPOLEDOCUMENTSITE pDocSite);
```

### <a name="parameters"></a>Parameter

*pdocsite*<br/>
Ein Zeiger auf die `IOleDocumentSite`-Schnittstelle, die das Dokument mit dem Server verbindet.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf einen `CDocObjectServer`. NULL, wenn der Vorgang fehlgeschlagen ist.

### <a name="remarks"></a>Hinweise

Wenn ein DocObject-Server aktiviert wird, zeigt die Rückgabe eines nicht-NULL-Zeigers, dass der Client docobjects unterstützen kann. Die Standard Implementierung gibt NULL zurück.

Eine typische Implementierung für ein Dokument, das docobjects unterstützt, weist einfach ein neues `CDocObjectServer` Objekt zu und gibt es an den Aufrufer zurück. Beispiel:

[!code-cpp[NVC_MFCOleServer#3](../../mfc/codesnippet/cpp/coleserverdoc-class_1.cpp)]

##  <a name="getembeddeditem"></a>COleServerDoc:: getembeddeditem

Mit dieser Funktion können Sie einen Zeiger auf ein Element abrufen, das das gesamte Dokument darstellt.

```
COleServerItem* GetEmbeddedItem();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein Element, das das gesamte Dokument darstellt. NULL, wenn der Vorgang fehlgeschlagen ist.

### <a name="remarks"></a>Hinweise

Es wird [COleServerDoc:: OnGetEmbeddedItem](#ongetembeddeditem)aufgerufen, eine virtuelle Funktion ohne Standard Implementierung.

##  <a name="getitemcliprect"></a>COleServerDoc:: getitemcliprect

Ruft die `GetItemClipRect` Member-Funktion auf, um die clippingrechtekoordinaten des Elements zu erhalten, das direkt bearbeitet wird.

```
void GetItemClipRect(LPRECT lpClipRect) const;
```

### <a name="parameters"></a>Parameter

*lpcliprect*<br/>
Ein Zeiger auf eine `RECT` Struktur oder ein `CRect` Objekt, um die clippingrechtekoordinaten des Elements zu erhalten.

### <a name="remarks"></a>Hinweise

Die Koordinaten befinden sich in Pixel relativ zum Client Bereich des Container Anwendungsfensters.

Das Zeichnen sollte außerhalb des clippingrechtecks nicht erfolgen. In der Regel wird das Zeichnen automatisch eingeschränkt. Verwenden Sie diese Funktion, um zu bestimmen, ob der Benutzer außerhalb des sichtbaren Teils des Dokuments einen Rollup durchgeführt hat. Wenn dies der Fall ist, Scrollen Sie im Container Dokument nach Bedarf, indem Sie [scrollcontainerby](#scrollcontainerby)aufgerufen haben.

##  <a name="getitemposition"></a>COleServerDoc:: getitemposition

Ruft die `GetItemPosition` Member-Funktion auf, um die Koordinaten des Elements zu erhalten, das direkt bearbeitet wird.

```
void GetItemPosition(LPRECT lpPosRect) const;
```

### <a name="parameters"></a>Parameter

*lpposrect*<br/>
Ein Zeiger auf eine `RECT` Struktur oder ein `CRect` Objekt, um die Koordinaten des Elements zu erhalten.

### <a name="remarks"></a>Hinweise

Die Koordinaten befinden sich in Pixel relativ zum Client Bereich des Container Anwendungsfensters.

Die Position des Elements kann mit dem aktuellen Clippingrechteck verglichen werden, um zu bestimmen, in welchem Umfang das Element auf dem Bildschirm sichtbar (oder nicht sichtbar) ist.

##  <a name="getzoomfactor"></a>COleServerDoc:: getzoomfactor

Die `GetZoomFactor` Member-Funktion bestimmt den "Zoomfaktor" eines Elements, das für die direkte Bearbeitung aktiviert wurde.

```
BOOL GetZoomFactor(
    LPSIZE lpSizeNum = NULL,
    LPSIZE lpSizeDenom = NULL,
    LPCRECT lpPosRect = NULL) const;
```

### <a name="parameters"></a>Parameter

*lpsizenum*<br/>
Zeiger auf ein Objekt der Klasse `CSize`, das den Zähler des Zoom Faktors enthalten wird. Kann NULL sein.

*lpsizedenom*<br/>
Zeiger auf ein Objekt der Klasse `CSize`, das den Nenner des Zoom Faktors enthalten wird. Kann NULL sein.

*lpposrect*<br/>
Zeiger auf ein Objekt der Klasse `CRect`, das die neue Position des Elements beschreibt. Wenn dieses Argument NULL ist, verwendet die Funktion die aktuelle Position des Elements.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Element für die direkte Bearbeitung aktiviert ist, und der Zoomfaktor ist nicht 100% (1:1); andernfalls 0.

### <a name="remarks"></a>Hinweise

Der Zoomfaktor (in Pixel) ist der Anteil der Elementgröße bis zum aktuellen Wertebereich. Wenn die Containeranwendung den Wert des Elements nicht festgelegt hat, wird der natürliche Block (wie durch [COleServerItem:: OnGetExtent](../../mfc/reference/coleserveritem-class.md#ongetextent)festgelegt) verwendet.

Die-Funktion legt die ersten beiden Argumente auf den Zähler und den Nenner des "Zoom Faktors" des Elements fest. Wenn das Element nicht an Ort und Stelle bearbeitet wird, legt die Funktion diese Argumente auf einen Standardwert von 100% (oder 1:1) fest und gibt 0 (null) zurück. Weitere Informationen finden Sie im technischen Hinweis 40, [unter MFC/OLE direkte Größe ändern und Zoomen](../../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).

##  <a name="isdocobject"></a>COleServerDoc:: isdocobject

Bestimmt, ob das Dokument ein DocObject ist.

```
BOOL IsDocObject() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Dokument ein DocObject-Objekt ist. andernfalls false.

##  <a name="isembedded"></a>COleServerDoc:: isEmbedded

Ruft die `IsEmbedded` Member-Funktion auf, um zu bestimmen, ob das Dokument ein in einen Container eingebettetes Objekt darstellt.

```
BOOL IsEmbedded() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das `COleServerDoc` Objekt ein Dokument ist, das ein in einen Container eingebettetes Objekt darstellt. andernfalls 0.

### <a name="remarks"></a>Hinweise

Ein aus einer Datei geladenes Dokument ist nicht eingebettet, obwohl es möglicherweise von einer Containeranwendung als Link bearbeitet wird. Ein Dokument, das in einem Container Dokument eingebettet ist, wird als eingebettet betrachtet.

##  <a name="isinplaceactive"></a>COleServerDoc:: isinplaceactive

Ruft die `IsInPlaceActive` Member-Funktion auf, um zu bestimmen, ob sich das Element zurzeit im direkten aktiven Zustand befindet.

```
BOOL IsInPlaceActive() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das `COleServerDoc` Objekt direkt aktiv ist. andernfalls 0.

##  <a name="notifychanged"></a>COleServerDoc:: notifychanged

Mit dieser Funktion können Sie alle verknüpften Elemente Benachrichtigen, die mit dem Dokument verbunden sind, in dem das Dokument geändert wurde.

```
void NotifyChanged();
```

### <a name="remarks"></a>Hinweise

In der Regel wird diese Funktion aufgerufen, nachdem der Benutzer ein globales Attribut geändert hat, z. b. die Dimensionen des Server Dokuments. Wenn ein OLE-Element mit einem automatischen Link mit dem Dokument verknüpft ist, wird das Element aktualisiert, um die Änderungen widerzuspiegeln. In Container Anwendungen, die mit dem Microsoft Foundation Class-Bibliothek geschrieben wurden, wird die [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) -Member-Funktion von `COleClientItem` aufgerufen.

> [!NOTE]
>  Diese Funktion ist für die Kompatibilität mit OLE 1 enthalten. Neue Anwendungen sollten [updateallitems](#updateallitems)verwenden.

##  <a name="notifyclosed"></a>COleServerDoc:: notifyclosed

Mit dieser Funktion wird der Container benachrichtigt, dass das Dokument geschlossen wurde.

```
void NotifyClosed();
```

### <a name="remarks"></a>Hinweise

Wenn der Benutzer im Menü Datei den Befehl Schließen auswählt, wird `NotifyClosed` von der `COleServerDoc`Implementierung der [onclosedocument](../../mfc/reference/cdocument-class.md#onclosedocument) -Member-Funktion aufgerufen. In Container Anwendungen, die mit dem Microsoft Foundation Class-Bibliothek geschrieben wurden, wird die [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) -Member-Funktion von `COleClientItem` aufgerufen.

##  <a name="notifyrename"></a>COleServerDoc:: notifyrename

Wenn der Benutzer das Server Dokument umbenennt, wird diese Funktion aufgerufen.

```
void NotifyRename(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>Parameter

*lpsznewname*<br/>
Zeiger auf eine Zeichenfolge, die den neuen Namen des Server Dokuments angibt; Dabei handelt es sich normalerweise um einen voll qualifizierten Pfad.

### <a name="remarks"></a>Hinweise

Wenn der Benutzer im Menü Datei den Befehl Speichern als auswählt, wird `NotifyRename` von der `COleServerDoc`Implementierung der [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument) -Member-Funktion aufgerufen. Diese Funktion benachrichtigt die OLE-System-DLLs, die wiederum die Container benachrichtigen. In Container Anwendungen, die mit dem Microsoft Foundation Class-Bibliothek geschrieben wurden, wird die [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) -Member-Funktion von `COleClientItem` aufgerufen.

##  <a name="notifysaved"></a>COleServerDoc:: notifygespeicherter

Diese Funktion wird aufgerufen, nachdem der Benutzer das Server Dokument gespeichert hat.

```
void NotifySaved();
```

### <a name="remarks"></a>Hinweise

Wenn der Benutzer im Menü Datei den Befehl Speichern auswählt, wird `NotifySaved` für Sie durch `COleServerDoc`der Implementierung von [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument)aufgerufen. Diese Funktion benachrichtigt die OLE-System-DLLs, die wiederum die Container benachrichtigen. In Container Anwendungen, die mit dem Microsoft Foundation Class-Bibliothek geschrieben wurden, wird die [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) -Member-Funktion von `COleClientItem` aufgerufen.

##  <a name="onclose"></a>COleServerDoc:: OnClose

Wird von Framework aufgerufen, wenn ein Container anfordert, dass das Server Dokument geschlossen wird.

```
virtual void OnClose(OLECLOSE dwCloseOption);
```

### <a name="parameters"></a>Parameter

*dwcloseoption*<br/>
Ein Wert aus der-Enumeration oleclose. Dieser Parameter kann einen der folgenden Werte aufweisen:

- OLECLOSE_SAVEIFDIRTY die Datei gespeichert wird, wenn Sie geändert wurde.

- OLECLOSE_NOSAVE die Datei geschlossen wird, ohne gespeichert zu werden.

- OLECLOSE_PROMPTSAVE wenn die Datei geändert wurde, wird der Benutzer aufgefordert, die Datei zu speichern.

### <a name="remarks"></a>Hinweise

Die Standard Implementierung ruft `CDocument::OnCloseDocument`auf.

Weitere Informationen und zusätzliche Werte finden Sie unter [oleclose](/windows/win32/api/oleidl/ne-oleidl-oleclose) in der Windows SDK.

##  <a name="ondeactivate"></a>COleServerDoc:: ondeaktivieren

Wird von Framework aufgerufen, wenn der Benutzer ein eingebettetes oder verknüpftes Element deaktiviert, das derzeit aktiv ist.

```
virtual void OnDeactivate();
```

### <a name="remarks"></a>Hinweise

Diese Funktion stellt die Benutzeroberfläche der Containeranwendung in Ihrem ursprünglichen Zustand wieder her und zerstört alle Menüs und anderen Steuerelemente, die für die direkte Aktivierung erstellt wurden.

Die rückgängig-Zustandsinformationen sollten an dieser Stelle bedingungslos freigegeben werden.

Weitere Informationen finden Sie im Artikel [Activation](../../mfc/activation-cpp.md).

##  <a name="ondeactivateui"></a>COleServerDoc:: onde activateui

Wird aufgerufen, wenn der Benutzer ein Element deaktiviert, das direkt aktiviert wurde.

```
virtual void OnDeactivateUI(BOOL bUndoable);
```

### <a name="parameters"></a>Parameter

*bundoable*<br/>
Gibt an, ob die Bearbeitungs Änderungen rückgängig gemacht werden können.

### <a name="remarks"></a>Hinweise

Diese Funktion stellt die Benutzeroberfläche der Containeranwendung in Ihrem ursprünglichen Zustand wieder her und blendet alle Menüs und anderen Steuerelemente aus, die für die direkte Aktivierung erstellt wurden.

Das Framework legt " *bundoable* " immer auf "false" fest. Wenn der Server rückgängig unterstützt und es einen Vorgang gibt, der rückgängig gemacht werden kann, rufen Sie die Basisklassen Implementierung mit " *bundoable* " auf "true" auf.

##  <a name="ondocwindowactivate"></a>COleServerDoc:: ondocwindowaktivierungs

Das Framework ruft diese Funktion auf, um ein Dokument Fenster zur direkten Bearbeitung zu aktivieren oder zu deaktivieren.

```
virtual void OnDocWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>Parameter

*bactivate*<br/>
Gibt an, ob das Dokument Fenster aktiviert oder deaktiviert werden soll.

### <a name="remarks"></a>Hinweise

Mit der Standard Implementierung werden die Benutzeroberflächen Elemente der Frame-Ebene nach Bedarf entfernt oder hinzugefügt. Überschreiben Sie diese Funktion, wenn Sie zusätzliche Aktionen ausführen möchten, wenn das Dokument, das das Element enthält, aktiviert oder deaktiviert wird.

Weitere Informationen finden Sie im Artikel [Activation](../../mfc/activation-cpp.md).

##  <a name="onexecolecmd"></a>COleServerDoc:: onexecolecmd

Das Framework ruft diese Funktion auf, um einen angegebenen Befehl auszuführen oder die Hilfe für den Befehl anzuzeigen.

```
virtual HRESULT OnExecOleCmd(
    const GUID* pguidCmdGroup,
    DWORD nCmdID,
    DWORD nCmdExecOpt,
    VARIANTARG* pvarargIn,
    VARIANTARG* pvarargOut);
```

### <a name="parameters"></a>Parameter

*pguidcmdgroup*<br/>
Ein Zeiger auf eine GUID, die einen Satz von Befehlen identifiziert. Kann NULL sein, um die Standard Befehlsgruppe anzugeben.

*nCmdId*<br/>
Der auszuführende Befehl. Muss in der durch *pguidcmdgroup*identifizierten Gruppe sein.

*ncmdexecout*<br/>
Die Art und Weise, wie das Objekt den Befehl ausführen soll, mindestens einen der folgenden Werte aus der olecmdexecopt-Enumeration:

OLECMDEXECOPT_DODEFAULT

OLECMDEXECOPT_PROMPTUSER

OLECMDEXECOPT_DONTPROMPTUSER

OLECMDEXECOPT_SHOWHELP

*pVarArgIn*<br/>
Ein Zeiger auf einen VARIANTARG-Wert, der Eingabeargumente für den Befehl enthält. Kann NULL sein.

*pvarargout*<br/>
Ein Zeiger auf einen VARIANTARG, um die Ausgabe Rückgabewerte des Befehls zu empfangen. Kann NULL sein.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück, wenn erfolgreich; andernfalls einer der folgenden Fehlercodes:

|Wert|Beschreibung|
|-----------|-----------------|
|E_UNEXPECTED|Unerwarteter Fehler.|
|E_FAIL|Fehler aufgetreten.|
|E_NOTIMPL|Gibt an, dass MFC selbst versuchen soll, den Befehl zu übersetzen und zu verteilen|
|OLECMDERR_E_UNKNOWNGROUP|*pguidcmdgroup* ist nicht NULL, gibt jedoch keine erkannte Befehlsgruppe an.|
|OLECMDERR_E_NOTSUPPORTED|*nCmdId* wird nicht als gültiger Befehl in der Gruppe " *pguidcmdgroup* " erkannt.|
|OLECMDERR_DISABLED|Der von *nCmdId* identifizierte Befehl ist deaktiviert und kann nicht ausgeführt werden.|
|OLECMDERR_NOHELP|Der Aufrufer hat Hilfe zu dem Befehl angefordert, der von *nCmdId identifiziert wurde* , aber es ist keine Hilfe|
|OLECMDERR_CANCELED|Benutzer hat die Ausführung abgebrochen.|

### <a name="remarks"></a>Hinweise

`COleCmdUI` können zum Aktivieren, aktualisieren und Festlegen anderer Eigenschaften von DocObject-Benutzeroberflächen Befehlen verwendet werden. Nachdem die Befehle initialisiert wurden, können Sie Sie mit `OnExecOleCmd`ausführen.

Das Framework ruft die Funktion auf, bevor versucht wird, einen OLE-Dokument Befehl zu übersetzen und zu verteilen. Sie müssen diese Funktion nicht außer Kraft setzen, um standardmäßige OLE-Dokument Befehle zu verarbeiten. Sie müssen jedoch eine außer Kraft setzung für diese Funktion bereitstellen, wenn Sie Ihre eigenen benutzerdefinierten Befehle verarbeiten oder Befehle verarbeiten möchten, die Parameter akzeptieren oder Ergebnisse zurückgeben.

Die meisten Befehle akzeptieren keine Argumente oder Rückgabewerte. Für einen Großteil der Befehle kann der Aufrufer NULL-Werten für *pVarArgIn* und *pvarargout*übergeben. Für Befehle, die Eingabewerte erwarten, kann der Aufrufer eine VARIANTARG-Variable deklarieren und initialisieren und einen Zeiger auf die Variable in *pVarArgIn*übergeben. Für Befehle, die einen einzelnen Wert erfordern, kann das Argument direkt in VARIANTARG gespeichert und an die Funktion übermittelt werden. Mehrere Argumente müssen in VARIANTARG mit einem der unterstützten Typen (z. b. `IDispatch` und SAFEARRAY) verpackt werden.

Wenn ein Befehl Argumente zurückgibt, wird der Aufrufer auf ähnliche Weise eine VARIANTARG deklarieren, ihn mit VT_EMPTY initialisieren und seine Adresse in *pvarargout*übergeben. Wenn ein Befehl einen einzelnen Wert zurückgibt, kann das Objekt diesen Wert direkt in *pvarargout*speichern. Mehrere Ausgabewerte müssen auf irgendeine Weise für VARIANTARG verpackt werden.

Die Basisklassen Implementierung dieser Funktion durchläuft die OLE_COMMAND_MAP Strukturen, die dem Befehls Ziel zugeordnet sind, und versucht, den Befehl an einen geeigneten Handler zu senden. Die Basisklassen Implementierung funktioniert nur mit Befehlen, die keine Argumente oder Rückgabewerte akzeptieren. Wenn Sie Befehle verarbeiten müssen, die Argumente oder Rückgabewerte akzeptieren, müssen Sie diese Funktion überschreiben und mit den Parametern *pVarArgIn* und *pvarargout* arbeiten.

##  <a name="onframewindowactivate"></a>COleServerDoc:: onframewindowaktivierungs

Das Framework ruft diese Funktion auf, wenn das Rahmen Fenster der Containeranwendung aktiviert oder deaktiviert wird.

```
virtual void OnFrameWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>Parameter

*bactivate*<br/>
Gibt an, ob das Rahmen Fenster aktiviert oder deaktiviert werden soll.

### <a name="remarks"></a>Hinweise

Die Standard Implementierung bricht alle Hilfe Modi ab, in denen sich das Rahmen Fenster befinden könnte. Überschreiben Sie diese Funktion, wenn Sie eine besondere Verarbeitung durchführen möchten, wenn das Rahmen Fenster aktiviert oder deaktiviert wird.

Weitere Informationen finden Sie im Artikel [Activation](../../mfc/activation-cpp.md).

##  <a name="ongetembeddeditem"></a>COleServerDoc:: OnGetEmbeddedItem

Wird von Framework aufgerufen, wenn eine Containeranwendung die Serveranwendung aufruft, um ein eingebettetes Element zu erstellen oder zu bearbeiten.

```
virtual COleServerItem* OnGetEmbeddedItem() = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein Element, das das gesamte Dokument darstellt. NULL, wenn der Vorgang fehlgeschlagen ist.

### <a name="remarks"></a>Hinweise

Es ist keine Standardimplementierung vorhanden. Sie müssen diese Funktion überschreiben, um ein Element zurückzugeben, das das gesamte Dokument darstellt. Dieser Rückgabewert sollte ein Objekt einer `COleServerItem`von abgeleiteten Klasse sein.

##  <a name="onreactivateandundo"></a>COleServerDoc:: onreactivateandundo

Das Framework ruft diese Funktion auf, wenn sich der Benutzer entscheidet, die an einem Element vorgenommenen Änderungen rückgängig zu machen, das direkt aktiviert, geändert und anschließend deaktiviert wurde.

```
virtual BOOL OnReactivateAndUndo();
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Die Standard Implementierung bewirkt nichts, außer wenn false zurückgegeben wird, um einen Fehler anzugeben.

Überschreiben Sie diese Funktion, wenn Ihre Anwendung rückgängig unterstützt. Normalerweise führen Sie den Rückgängig-Vorgang aus und aktivieren dann das Element durch Aufrufen von `ActivateInPlace`. Wenn die Containeranwendung mit dem Microsoft Foundation Class-Bibliothek geschrieben wird, bewirkt der Aufruf von `COleClientItem::ReactivateAndUndo`, dass diese Funktion aufgerufen wird.

##  <a name="onresizeborder"></a>COleServerDoc:: onresizeborder

Das Framework ruft diese Funktion auf, wenn die Rahmen Fenster der Containeranwendung die Größe ändern.

```
virtual void OnResizeBorder(
    LPCRECT lpRectBorder,
    LPOLEINPLACEUIWINDOW lpUIWindow,
    BOOL bFrame);
```

### <a name="parameters"></a>Parameter

*lprectborder*<br/>
Ein Zeiger auf eine `RECT` Struktur oder ein `CRect` Objekt, das die Koordinaten des Rahmens angibt.

*lpuiwindow*<br/>
Zeiger auf ein Objekt der Klasse `IOleInPlaceUIWindow`, das die aktuelle direkte Bearbeitungs Sitzung besitzt.

*bframe*<br/>
TRUE, wenn *lpuiwindow* auf das Rahmen Fenster der obersten Ebene der Containeranwendung zeigt, oder false, wenn *lpuiwindow* auf das Rahmen Fenster auf Dokument Ebene der Containeranwendung zeigt.

### <a name="remarks"></a>Hinweise

Diese Funktion ändert die Größe von Symbolleisten und anderen Elementen der Benutzeroberfläche entsprechend der neuen Fenstergröße.

Weitere Informationen finden Sie unter [IOleInPlaceUIWindow](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceuiwindow) in der Windows SDK.

Hierbei handelt es sich um eine erweiterte über schreibbare.

##  <a name="onsethostnames"></a>COleServerDoc:: onmenthostnames

Wird von Framework aufgerufen, wenn der Container die Hostnamen für dieses Dokument festlegt oder ändert.

```
virtual void OnSetHostNames(
    LPCTSTR lpszHost,
    LPCTSTR lpszHostObj);
```

### <a name="parameters"></a>Parameter

*lpszhost*<br/>
Zeiger auf eine Zeichenfolge, die den Namen der Containeranwendung angibt.

*lpszhostobj*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen des Containers für das Dokument angibt.

### <a name="remarks"></a>Hinweise

Die Standard Implementierung ändert den Dokumenttitel für alle Sichten, die auf dieses Dokument verweisen.

Überschreiben Sie diese Funktion, wenn die Titel der Anwendung durch einen anderen Mechanismus festgelegt werden.

##  <a name="onsetitemrects"></a>COleServerDoc:: onontitemrects

Das Framework ruft diese Funktion auf, um das direkte Bearbeitungs Rahmen Fenster im Rahmen Fenster der Containeranwendung zu positionieren.

```
virtual void OnSetItemRects(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>Parameter

*lpposrect*<br/>
Ein Zeiger auf eine `RECT` Struktur oder ein `CRect` Objekt, das die Position des direkten Frame Fensters relativ zum Client Bereich der Containeranwendung angibt.

*lpcliprect*<br/>
Ein Zeiger auf eine `RECT` Struktur oder ein `CRect` Objekt, das das Clippingrechteck des direkten Frame Fensters relativ zum Client Bereich der Containeranwendung angibt.

### <a name="remarks"></a>Hinweise

Überschreiben Sie diese Funktion, um den Zoomfaktor der Ansicht bei Bedarf zu aktualisieren.

Diese Funktion wird in der Regel als Reaktion auf einen `RequestPositionChange` Aufruf aufgerufen, obwohl Sie jederzeit vom Container aufgerufen werden kann, um eine Positionsänderung für das direkte Element anzufordern.

##  <a name="onshowcontrolbars"></a>COleServerDoc:: onshowcontrolbars

Das Framework ruft diese Funktion auf, um die Steuer leisten der Serveranwendung, die dem durch *pframewnd*identifizierten Rahmen Fenster zugeordnet sind, anzuzeigen oder auszublenden.

```
virtual void OnShowControlBars(
    CFrameWnd* pFrameWnd,
    BOOL bShow);
```

### <a name="parameters"></a>Parameter

*pframewnd*<br/>
Ein Zeiger auf das Rahmen Fenster, dessen Steuer leisten ausgeblendet oder angezeigt werden sollen.

*bShow*<br/>
Bestimmt, ob Steuer leisten angezeigt oder ausgeblendet werden.

### <a name="remarks"></a>Hinweise

Die Standard Implementierung listet alle Steuer leisten im Besitz dieses Rahmen Fensters auf und blendet sie aus bzw. zeigt diese an.

##  <a name="onshowdocument"></a>COleServerDoc:: onshowdocument

Das Framework ruft die `OnShowDocument`-Funktion auf, wenn das Server Dokument ausgeblendet oder angezeigt werden muss.

```
virtual void OnShowDocument(BOOL bShow);
```

### <a name="parameters"></a>Parameter

*bShow*<br/>
Gibt an, ob die Benutzeroberfläche des Dokuments angezeigt oder ausgeblendet werden soll.

### <a name="remarks"></a>Hinweise

Wenn *bShow* den Wert true hat, aktiviert die Standard Implementierung ggf. die Serveranwendung und bewirkt, dass die Containeranwendung im Fenster einen Bildlauf durchführen kann, sodass das Element sichtbar ist. Wenn *bShow* den Wert false hat, wird das Element durch die Standard Implementierung durch einen `OnDeactivate`-aufrufungstyp deaktiviert. Anschließend werden alle Rahmen Fenster, die für das Dokument erstellt wurden, mit Ausnahme des ersten, zerstört oder ausgeblendet. Wenn keine sichtbaren Dokumente verbleiben, wird die Serveranwendung in der Standard Implementierung ausgeblendet.

##  <a name="onupdatedocument"></a>COleServerDoc:: onupdatedocument

Wird vom Framework aufgerufen, wenn ein Dokument gespeichert wird, das ein eingebettetes Element in einem Verbund Dokument ist.

```
virtual BOOL OnUpdateDocument();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Dokument erfolgreich aktualisiert wurde. andernfalls 0.

### <a name="remarks"></a>Hinweise

Die Standard Implementierung ruft die Funktionen [COleServerDoc:: notifygespeichund](#notifysaved) [COleServerDoc:: saveeinbettmember](#saveembedding) auf und markiert das Dokument dann als Clean. Überschreiben Sie diese Funktion, wenn Sie beim Aktualisieren eines eingebetteten Elements eine besondere Verarbeitung durchführen möchten.

##  <a name="requestpositionchange"></a>COleServerDoc:: requestpositionchange

Mit dieser Member-Funktion wird die Position des Elements von der Containeranwendung geändert.

```
void RequestPositionChange(LPCRECT lpPosRect);
```

### <a name="parameters"></a>Parameter

*lpposrect*<br/>
Ein Zeiger auf eine `RECT` Struktur oder ein `CRect` Objekt, das die neue Position des Elements enthält.

### <a name="remarks"></a>Hinweise

Diese Funktion wird in der Regel (zusammen mit `UpdateAllItems`) aufgerufen, wenn sich die Daten in einem direkt aktiven Element geändert haben. Nach diesem Aufruf führt der Container die Änderung möglicherweise aus, indem er `OnSetItemRects`aufruft. Die resultierende Position kann sich von der angeforderten Position unterscheiden.

##  <a name="saveembedding"></a>COleServerDoc:: saveeinbettungen

Mit dieser Funktion wird der Containeranwendung mitgeteilt, dass das eingebettete Objekt gespeichert werden soll.

```
void SaveEmbedding();
```

### <a name="remarks"></a>Hinweise

Diese Funktion wird automatisch aus `OnUpdateDocument`aufgerufen. Beachten Sie, dass diese Funktion bewirkt, dass das Element auf dem Datenträger aktualisiert wird, sodass es in der Regel nur als Ergebnis einer bestimmten Benutzeraktion aufgerufen wird.

##  <a name="scrollcontainerby"></a>COleServerDoc:: scrollcontainerby

Ruft die `ScrollContainerBy` Member-Funktion auf, um das Container Dokument um den durch `sizeScroll`gekennzeichneten Betrag in Pixel zu scrollen.

```
BOOL ScrollContainerBy(CSize sizeScroll);
```

### <a name="parameters"></a>Parameter

*sizescroll*<br/>
Gibt an, wie weit das Container Dokument einen Bildlauf durchführen soll.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Positive Werte geben den Bildlauf nach unten und nach rechts an. negative Werte geben den Bildlauf nach oben und nach links an.

##  <a name="updateallitems"></a>COleServerDoc:: updateallitems

Mit dieser Funktion können Sie alle verknüpften Elemente Benachrichtigen, die mit dem Dokument verbunden sind, in dem das Dokument geändert wurde.

```
void UpdateAllItems(
    COleServerItem* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL,
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>Parameter

*psender*<br/>
Zeiger auf das Element, das das Dokument geändert hat, oder NULL, wenn alle Elemente aktualisiert werden sollen.

*lHint*<br/>
Enthält Informationen über die Änderung.

*phint*<br/>
Zeiger auf ein Objekt, das Informationen über die Änderung speichert.

*ndrawaspect*<br/>
Bestimmt, wie das Element gezeichnet werden soll. Dies ist ein Wert aus der DVASPECT-Enumeration. Dieser Parameter kann einen der folgenden Werte aufweisen:

- DVASPECT_CONTENT Element wird so dargestellt, dass es als eingebettetes Objekt in seinem Container angezeigt werden kann.

- DVASPECT_THUMBNAIL Element wird in einer "Miniaturansicht"-Darstellung gerendert, sodass es in einem Browsertool angezeigt werden kann.

- DVASPECT_ICON Element wird durch ein Symbol dargestellt.

- DVASPECT_DOCPRINT Element wird dargestellt, als ob es mithilfe des Befehls Drucken im Menü Datei gedruckt wurde.

### <a name="remarks"></a>Hinweise

Diese Funktion wird in der Regel aufgerufen, nachdem der Benutzer das Server Dokument geändert hat. Wenn ein OLE-Element mit einem automatischen Link mit dem Dokument verknüpft ist, wird das Element aktualisiert, um die Änderungen widerzuspiegeln. In Container Anwendungen, die mit dem Microsoft Foundation Class-Bibliothek geschrieben wurden, wird die [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) -Member-Funktion von `COleClientItem` aufgerufen.

Diese Funktion Ruft die `OnUpdate` Member-Funktion für jedes Dokument Element mit Ausnahme des sendenden Elements auf, wobei *phint*, *lHint*und *ndrawaspect*übergeben werden. Verwenden Sie diese Parameter, um Informationen über die an dem Dokument vorgenommenen Änderungen an die Elemente zu übergeben. Sie können Informationen mithilfe von *lHint* codieren, oder Sie können eine `CObject`abgeleitete Klasse definieren, um Informationen über die Änderungen zu speichern und ein Objekt dieser Klasse mithilfe von *phint*zu übergeben. Überschreiben Sie die `OnUpdate` Member-Funktion in der von `COleServerItem`abgeleiteten Klasse, um die Aktualisierung der einzelnen Elemente in Abhängigkeit davon zu optimieren, ob sich die Darstellung geändert hat.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel Hierarchien](../../overview/visual-cpp-samples.md)<br/>
[COleLinkingDoc-Klasse](../../mfc/reference/colelinkingdoc-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleDocument-Klasse](../../mfc/reference/coledocument-class.md)<br/>
[COleLinkingDoc-Klasse](../../mfc/reference/colelinkingdoc-class.md)<br/>
[COleTemplateServer-Klasse](../../mfc/reference/coletemplateserver-class.md)
