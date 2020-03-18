---
title: COleServerItem-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleServerItem
- AFXOLE/COleServerItem
- AFXOLE/COleServerItem::COleServerItem
- AFXOLE/COleServerItem::AddOtherClipboardData
- AFXOLE/COleServerItem::CopyToClipboard
- AFXOLE/COleServerItem::DoDragDrop
- AFXOLE/COleServerItem::GetClipboardData
- AFXOLE/COleServerItem::GetDocument
- AFXOLE/COleServerItem::GetEmbedSourceData
- AFXOLE/COleServerItem::GetItemName
- AFXOLE/COleServerItem::GetLinkSourceData
- AFXOLE/COleServerItem::GetObjectDescriptorData
- AFXOLE/COleServerItem::IsConnected
- AFXOLE/COleServerItem::IsLinkedItem
- AFXOLE/COleServerItem::NotifyChanged
- AFXOLE/COleServerItem::OnDoVerb
- AFXOLE/COleServerItem::OnDraw
- AFXOLE/COleServerItem::OnDrawEx
- AFXOLE/COleServerItem::OnGetClipboardData
- AFXOLE/COleServerItem::OnGetExtent
- AFXOLE/COleServerItem::OnInitFromData
- AFXOLE/COleServerItem::OnQueryUpdateItems
- AFXOLE/COleServerItem::OnRenderData
- AFXOLE/COleServerItem::OnRenderFileData
- AFXOLE/COleServerItem::OnRenderGlobalData
- AFXOLE/COleServerItem::OnSetColorScheme
- AFXOLE/COleServerItem::OnSetData
- AFXOLE/COleServerItem::OnSetExtent
- AFXOLE/COleServerItem::OnUpdate
- AFXOLE/COleServerItem::OnUpdateItems
- AFXOLE/COleServerItem::SetItemName
- AFXOLE/COleServerItem::GetDataSource
- AFXOLE/COleServerItem::OnHide
- AFXOLE/COleServerItem::OnOpen
- AFXOLE/COleServerItem::OnShow
- AFXOLE/COleServerItem::m_sizeExtent
helpviewer_keywords:
- COleServerItem [MFC], COleServerItem
- COleServerItem [MFC], AddOtherClipboardData
- COleServerItem [MFC], CopyToClipboard
- COleServerItem [MFC], DoDragDrop
- COleServerItem [MFC], GetClipboardData
- COleServerItem [MFC], GetDocument
- COleServerItem [MFC], GetEmbedSourceData
- COleServerItem [MFC], GetItemName
- COleServerItem [MFC], GetLinkSourceData
- COleServerItem [MFC], GetObjectDescriptorData
- COleServerItem [MFC], IsConnected
- COleServerItem [MFC], IsLinkedItem
- COleServerItem [MFC], NotifyChanged
- COleServerItem [MFC], OnDoVerb
- COleServerItem [MFC], OnDraw
- COleServerItem [MFC], OnDrawEx
- COleServerItem [MFC], OnGetClipboardData
- COleServerItem [MFC], OnGetExtent
- COleServerItem [MFC], OnInitFromData
- COleServerItem [MFC], OnQueryUpdateItems
- COleServerItem [MFC], OnRenderData
- COleServerItem [MFC], OnRenderFileData
- COleServerItem [MFC], OnRenderGlobalData
- COleServerItem [MFC], OnSetColorScheme
- COleServerItem [MFC], OnSetData
- COleServerItem [MFC], OnSetExtent
- COleServerItem [MFC], OnUpdate
- COleServerItem [MFC], OnUpdateItems
- COleServerItem [MFC], SetItemName
- COleServerItem [MFC], GetDataSource
- COleServerItem [MFC], OnHide
- COleServerItem [MFC], OnOpen
- COleServerItem [MFC], OnShow
- COleServerItem [MFC], m_sizeExtent
ms.assetid: 80256df6-3888-4256-944b-787d4b2e6b0d
ms.openlocfilehash: dcae304e8571ecb5743002638ea23f13c3e21517
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426480"
---
# <a name="coleserveritem-class"></a>COleServerItem-Klasse

Stellt die Serverschnittstelle zu OLE-Elementen bereit.

## <a name="syntax"></a>Syntax

```
class COleServerItem : public CDocItem
```

## <a name="members"></a>Member

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[COleServerItem:: COleServerItem](#coleserveritem)|Erstellt ein `COleServerItem`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[COleServerItem:: addotherclipboarddata](#addotherclipboarddata)|Platziert Präsentations-und Konvertierungs Formate in einem `COleDataSource`-Objekt.|
|[COleServerItem:: CopyTo Clipboard](#copytoclipboard)|Kopiert das Element in die Zwischenablage.|
|[COleServerItem::D odragdrop](#dodragdrop)|Führt einen Drag & Drop-Vorgang aus.|
|[COleServerItem:: GetClipboardData](#getclipboarddata)|Ruft die Datenquelle für die Verwendung bei der Datenübertragung (Drag & Drop oder Zwischenablage) ab.|
|[COleServerItem:: GetDocument](#getdocument)|Gibt das Server Dokument zurück, das das Element enthält.|
|[COleServerItem:: getembedsourcedata](#getembedsourcedata)|Ruft die CF_EMBEDSOURCE Daten für ein OLE-Element ab.|
|[COleServerItem:: GetItemName](#getitemname)|Gibt den Namen des Elements zurück. Wird nur für verknüpfte Elemente verwendet.|
|[COleServerItem:: getlinksourcedata](#getlinksourcedata)|Ruft die CF_LINKSOURCE Daten für ein OLE-Element ab.|
|[COleServerItem:: getobjectdescriptor Data](#getobjectdescriptordata)|Ruft die CF_OBJECTDESCRIPTOR Daten für ein OLE-Element ab.|
|[COleServerItem:: IsConnected](#isconnected)|Gibt an, ob das Element zurzeit an einen aktiven Container angefügt ist.|
|[COleServerItem:: islinkeditem](#islinkeditem)|Gibt an, ob das Element ein verknüpftes OLE-Element darstellt.|
|[COleServerItem:: notifychanged](#notifychanged)|Aktualisiert alle Container mit automatischer Link Aktualisierung.|
|[COleServerItem:: ondoverb](#ondoverb)|Wird aufgerufen, um ein Verb auszuführen.|
|[COleServerItem:: OnDraw](#ondraw)|Wird aufgerufen, wenn der Container das Zeichnen des Elements anfordert. Implementierung erforderlich.|
|[COleServerItem:: ondrawex](#ondrawex)|Wird zum Zeichnen spezieller Elemente aufgerufen.|
|[COleServerItem:: OnGetClipboardData](#ongetclipboarddata)|Wird von Framework aufgerufen, um die Daten zu erhalten, die in die Zwischenablage kopiert werden.|
|[COleServerItem:: OnGetExtent](#ongetextent)|Wird von Framework aufgerufen, um die Größe des OLE-Elements abzurufen.|
|[COleServerItem:: oninitfromdata](#oninitfromdata)|Wird von Framework aufgerufen, um ein OLE-Element mit dem Inhalt des angegebenen Datenübertragungs Objekts zu initialisieren.|
|[COleServerItem:: onqueryupdateitems](#onqueryupdateitems)|Wird aufgerufen, um zu bestimmen, ob verknüpfte Elemente aktualisiert werden müssen.|
|[COleServerItem:: OnRenderData](#onrenderdata)|Ruft Daten im Rahmen des verzögerten Renderings ab.|
|[COleServerItem:: onrenderfiledata](#onrenderfiledata)|Ruft Daten im Rahmen des verzögerten Renderings in ein `CFile` Objekt ab.|
|[COleServerItem:: onrenderglobaldata](#onrenderglobaldata)|Ruft Daten im Rahmen des verzögerten Renderings in einen HGLOBAL ab.|
|[COleServerItem:: onsetcolorscheme](#onsetcolorscheme)|Wird aufgerufen, um das Farbschema des Elements festzulegen.|
|[COleServerItem:: onsetdata](#onsetdata)|Wird aufgerufen, um die Daten des Elements festzulegen.|
|[COleServerItem:: onabtextent](#onsetextent)|Wird von Framework aufgerufen, um die Größe des OLE-Elements festzulegen.|
|[COleServerItem:: OnUpdate](#onupdate)|Wird aufgerufen, wenn ein Teil des Dokuments, zu dem das Element gehört, geändert wird.|
|[COleServerItem:: onupdateitems](#onupdateitems)|Wird aufgerufen, um den Präsentations Cache für alle Elemente im Server Dokument zu aktualisieren.|
|[COleServerItem:: Servername](#setitemname)|Legt den Namen des Elements fest. Wird nur für verknüpfte Elemente verwendet.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|Beschreibung|
|----------|-----------------|
|[COleServerItem:: GetDataSource](#getdatasource)|Ruft das Objekt ab, das zum Speichern von Konvertierungs Formaten verwendet wird|
|[COleServerItem:: onHide](#onhide)|Wird von Framework aufgerufen, um das OLE-Element auszublenden.|
|[COleServerItem:: OnOpen](#onopen)|Wird von Framework aufgerufen, um das OLE-Element in einem eigenen Fenster der obersten Ebene anzuzeigen.|
|[COleServerItem:: onShow](#onshow)|Wird aufgerufen, wenn der Container anfordert, das Element anzuzeigen.|

### <a name="public-data-members"></a>Öffentliche Datenelemente

|Name|Beschreibung|
|----------|-----------------|
|[COleServerItem:: m_sizeExtent](#m_sizeextent)|Teilt dem Server mit, wie viel des OLE-Elements sichtbar ist.|

## <a name="remarks"></a>Hinweise

Ein verknüpftes Element kann ein oder alle ein Server Dokument darstellen. Ein eingebettetes Element stellt immer ein gesamtes Server Dokument dar.

Die `COleServerItem`-Klasse definiert mehrere über schreibbare Member-Funktionen, die von den OLE-System-DLLs (Dynamic-Link Libraries) aufgerufen werden, normalerweise als Reaktion auf Anforderungen von der Containeranwendung. Diese Member-Funktionen ermöglichen es der Containeranwendung, das Element indirekt auf verschiedene Weise zu bearbeiten, z. b. durch die Anzeige, das Ausführen der Verben oder das Abrufen seiner Daten in verschiedenen Formaten.

Um `COleServerItem`zu verwenden, leiten Sie eine Klasse davon ab, und implementieren Sie die [OnDraw](#ondraw) -und [serialize](../../mfc/reference/cobject-class.md#serialize) -Member-Funktionen. Die `OnDraw`-Funktion stellt die metadateidarstellung eines Elements bereit und ermöglicht die Anzeige, wenn eine Containeranwendung ein Verbund Dokument öffnet. Die `Serialize` Funktion von `CObject` stellt die systemeigene Darstellung eines Elements bereit und ermöglicht so die Übertragung eines eingebetteten Elements zwischen den Server-und Container Anwendungen. [OnGetExtent](#ongetextent) stellt die natürliche Größe des Elements für den Container bereit, sodass der Container die Größe des Elements anpassen kann.

Weitere Informationen zu Servern und verwandten Themen finden Sie in den Artikeln [Server: Implementieren eines Servers](../../mfc/servers-implementing-a-server.md) und "Erstellen einer Container-/Serveranwendung" im Artikel [Container: Erweiterte Funktionen](../../mfc/containers-advanced-features.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

`COleServerItem`

## <a name="requirements"></a>Voraussetzungen

**Header:** Afxole. h

##  <a name="addotherclipboarddata"></a>COleServerItem:: addotherclipboarddata

Diese Funktion wird aufgerufen, um die Präsentations-und Konvertierungs Formate für das OLE-Element in der angegebenen `COleDataSource` Objekt zu platzieren.

```
void AddOtherClipboardData(COleDataSource* pDataSource);
```

### <a name="parameters"></a>Parameter

*pDatasource*<br/>
Zeiger auf das `COleDataSource` Objekt, in dem die Daten abgelegt werden sollen.

### <a name="remarks"></a>Hinweise

Sie müssen die [OnDraw](#ondraw) -Member-Funktion implementiert haben, um das Darstellungsformat (ein Metadateibild) für das Element bereitzustellen. Um andere Konvertierungs Formate zu unterstützen, registrieren Sie diese mithilfe des [COleDataSource](../../mfc/reference/coledatasource-class.md) -Objekts, das von [GetDataSource](#getdatasource) zurückgegeben wurde, und überschreiben die [OnRenderData](#onrenderdata) -Member-Funktion, um Daten in den Formaten bereitzustellen, die

##  <a name="coleserveritem"></a>COleServerItem:: COleServerItem

Erstellt ein `COleServerItem` Objekt und fügt es der Auflistung von Dokument Elementen des Server Dokuments hinzu.

```
COleServerItem(
    COleServerDoc* pServerDoc,
    BOOL bAutoDelete);
```

### <a name="parameters"></a>Parameter

*pserverdoc*<br/>
Zeiger auf das Dokument, das das neue Element enthalten soll.

*Bauto DELETE*<br/>
Flag zum angeben, ob das Objekt gelöscht werden kann, wenn ein Link zu ihm freigegeben wird. Legen Sie diese Einstellung auf "false" fest, wenn das `COleServerItem` Objekt ein integraler Bestandteil der Daten Ihres Dokuments ist, das Sie löschen müssen. Legen Sie diese Einstellung auf "true" fest, wenn das Objekt eine sekundäre Struktur ist, mit der ein Bereich in den Daten des Dokuments identifiziert wird, die vom Framework gelöscht werden können.

##  <a name="copytoclipboard"></a>COleServerItem:: CopyTo Clipboard

Mit dieser Funktion wird das OLE-Element in die Zwischenablage kopiert.

```
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```

### <a name="parameters"></a>Parameter

*bincludelta Ink*<br/>
Legen Sie diese Einstellung auf true fest, wenn Verknüpfungs Daten in die Zwischenablage kopiert werden sollen. Legen Sie diese Einstellung auf "false" fest, wenn die Serveranwendung keine Links unterstützt.

### <a name="remarks"></a>Hinweise

Die-Funktion verwendet die [OnGetClipboardData](#ongetclipboarddata) -Member-Funktion, um ein [COleDataSource](../../mfc/reference/coledatasource-class.md) -Objekt zu erstellen, das die Daten des OLE-Elements in den unterstützten Formaten enthält. Die Funktion platziert dann das `COleDataSource` Objekt mithilfe der [COleDataSource:: setClipboard](../../mfc/reference/coledatasource-class.md#setclipboard) -Funktion in der Zwischenablage. Das `COleDataSource`-Objekt enthält die systemeigenen Daten des Elements und seine Darstellung in CF_METAFILEPICT Format sowie Daten in beliebigen Konvertierungs Formaten, die Sie unterstützen möchten. Sie müssen [serialize](../../mfc/reference/cobject-class.md#serialize) und [OnDraw](#ondraw) implementiert haben, damit diese Member-Funktion funktioniert.

##  <a name="dodragdrop"></a>COleServerItem::D odragdrop

Ruft die `DoDragDrop` Member-Funktion auf, um einen Drag & Drop-Vorgang auszuführen.

```
DROPEFFECT DoDragDrop(
    LPCRECT lpRectItem,
    CPoint ptOffset,
    BOOL bIncludeLink = FALSE,
    DWORD dwEffects = DROPEFFECT_COPY | DROPEFFECT_MOVE,
    LPCRECT lpRectStartDrag = NULL);
```

### <a name="parameters"></a>Parameter

*lprectitem*<br/>
Das Rechteck des Elements auf dem Bildschirm in Pixel relativ zum Client Bereich.

*"ptoffset"*<br/>
Der Offset von *lpitemrect* , an dem sich die Mausposition zum Zeitpunkt des Zieh Vorgangs befand.

*bincludelta Ink*<br/>
Legen Sie diese Einstellung auf true fest, wenn Verknüpfungs Daten in die Zwischenablage kopiert werden sollen. Legen Sie diese Einstellung auf "false" fest, wenn Ihre Anwendung keine Links unterstützt.

*dweffects*<br/>
Bestimmt die Auswirkungen, die die Zieh Quelle im Zieh Vorgang zulässt (eine Kombination aus kopieren, verschieben und verknüpfen).

*lprectstartdrag*<br/>
Zeiger auf das Rechteck, das definiert, wo der Zieh Vorgang tatsächlich gestartet wird. Weitere Informationen finden Sie im folgenden Abschnitt "Hinweise".

### <a name="return-value"></a>Rückgabewert

Ein Wert aus der dropinffect-Enumeration. Wenn Sie DROPEFFECT_MOVE, sollten die ursprünglichen Daten entfernt werden.

### <a name="remarks"></a>Hinweise

Der Drag & Drop-Vorgang wird nicht sofort gestartet. Sie wartet, bis der Mauszeiger das von *lprectstartdrag* angegebene Rechteck verlässt oder bis eine angegebene Anzahl von Millisekunden verstrichen ist. Wenn *lprectstartdrag* den Wert NULL hat, wird ein Standard Rechteck verwendet, sodass der Zieh Vorgang beginnt, wenn der Mauszeiger ein Pixel verschiebt.

Die Verzögerungszeit wird durch eine Registrierungsschlüssel Einstellung angegeben. Sie können die Verzögerungszeit ändern, indem Sie [CWinApp:: schreiteprofilestring](../../mfc/reference/cwinapp-class.md#writeprofilestring) oder [CWinApp:: Beschreib teprofileint](../../mfc/reference/cwinapp-class.md#writeprofileint)aufrufen. Wenn Sie die Verzögerungszeit nicht angeben, wird ein Standardwert von 200 Millisekunden verwendet. Die Zeit für die Zieh Verzögerung wird wie folgt gespeichert:

- Die Zeit für die Drag-Verzögerung von Windows NT wird in HKEY_LOCAL_MACHINE \software\microsoft\windows\nt\currentversion\inifilemapping\win.ini\windows\dragdelta gespeichert.

- Windows 3. x-Zieh Verzögerungszeit wird im Gewinn gespeichert. INI-Datei im Abschnitt [Windows} '.

- Windows 95/98-Zieh Verzögerungszeit wird in einer zwischengespeicherten Version von Win gespeichert. Geleitet.

Weitere Informationen zur Art und Weise, in der Informationen zu Drag Delay in der Registrierung oder in gespeichert werden. Die INI-Datei finden Sie unter " [Beschreib teprofilestring](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) " in der Windows SDK.

##  <a name="getclipboarddata"></a>COleServerItem:: GetClipboardData

Diese Funktion wird aufgerufen, um das angegebene [COleDataSource](../../mfc/reference/coledatasource-class.md) -Objekt mit allen Daten auszufüllen, die in die Zwischenablage kopiert werden, wenn Sie " [CopyTo Clipboard](#copytoclipboard) " aufgerufen haben (die gleichen Daten werden ebenfalls übertragen, wenn Sie " [DoDragDrop](#dodragdrop)" aufrufen).

```
void GetClipboardData(
    COleDataSource* pDataSource,
    BOOL bIncludeLink = FALSE,
    LPPOINT lpOffset = NULL,
    LPSIZE lpSize = NULL);
```

### <a name="parameters"></a>Parameter

*pDatasource*<br/>
Zeiger auf das `COleDataSource` Objekt, das die Daten des OLE-Elements in allen unterstützten Formaten empfängt.

*bincludelta Ink*<br/>
TRUE, wenn Verknüpfungs Daten in die Zwischenablage kopiert werden sollen. FALSE, wenn die Serveranwendung keine Verknüpfungen unterstützt.

*lpoffset*<br/>
Der Offset des Mauszeigers vom Ursprung des-Objekts in Pixel.

*lpsize*<br/>
Die Größe des-Objekts in Pixel.

### <a name="remarks"></a>Hinweise

Diese Funktion Ruft die [getembedsourcedata](#getembedsourcedata) -Element Funktion auf, um die systemeigenen Daten für das OLE-Element abzurufen, und ruft die Member-Funktion von [addotherclipboarddata](#addotherclipboarddata) auf, um das Präsentationsformat und alle unterstützten Konvertierungs Formate abzurufen. Wenn *bincludelta Ink* den Wert true hat, ruft die Funktion auch [getlinksourcedata](#getlinksourcedata) auf, um die Linkdaten für das Element abzurufen.

Überschreiben Sie diese Funktion, wenn Sie Formate in einem `COleDataSource` Objekt vor oder nach den von `CopyToClipboard`angegebenen Formaten platzieren möchten.

##  <a name="getdatasource"></a>COleServerItem:: GetDataSource

Mit dieser Funktion können Sie das [COleDataSource](../../mfc/reference/coledatasource-class.md) -Objekt abrufen, das zum Speichern der von der Serveranwendung unterstützten Konvertierungs Formate verwendet wird.

```
COleDataSource* GetDataSource();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das `COleDataSource` Objekt, das verwendet wird, um die Konvertierungs Formate zu speichern.

### <a name="remarks"></a>Hinweise

Wenn die Serveranwendung Daten in einer Vielzahl von Formaten während der Datenübertragungs Vorgänge anbieten soll, registrieren Sie diese Formate mit dem `COleDataSource` Objekt, das von dieser Funktion zurückgegeben wird. Wenn Sie z. b. eine CF_TEXT Darstellung des OLE-Elements für Zwischenablage-oder Drag & Drop-Vorgänge angeben möchten, registrieren Sie das Format bei dem `COleDataSource` Objekt, das von dieser Funktion zurückgegeben wird, und überschreiben Sie dann die `OnRenderXxxData` Member-Funktion, um die Daten bereitzustellen.

##  <a name="getdocument"></a>COleServerItem:: GetDocument

Mit dieser Funktion können Sie einen Zeiger auf das Dokument abrufen, das das Element enthält.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Dokument, das das Element enthält. NULL, wenn das Element nicht Teil eines Dokuments ist.

### <a name="remarks"></a>Hinweise

Dies ermöglicht den Zugriff auf das Server Dokument, das Sie als Argument an den `COleServerItem`-Konstruktor übergeben haben.

##  <a name="getembedsourcedata"></a>COleServerItem:: getembedsourcedata

Mit dieser Funktion werden die CF_EMBEDSOURCE Daten für ein OLE-Element abzurufen.

```
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parameter

*lpstgmedium*<br/>
Ein Zeiger auf die [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) -Struktur, die die CF_EMBEDSOURCE Daten für das OLE-Element empfängt.

### <a name="remarks"></a>Hinweise

Dieses Format schließt die systemeigenen Daten des Elements ein. Sie müssen die `Serialize` Member-Funktion implementiert haben, damit diese Funktion ordnungsgemäß funktioniert.

Das Ergebnis kann dann mithilfe von [COleDataSource:: CacheData](../../mfc/reference/coledatasource-class.md#cachedata)zu einer Datenquelle hinzugefügt werden. Diese Funktion wird automatisch von [COleServerItem:: OnGetClipboardData](#ongetclipboarddata)aufgerufen.

Weitere Informationen finden Sie unter [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) in der Windows SDK.

##  <a name="getitemname"></a>COleServerItem:: GetItemName

Mit dieser Funktion können Sie den Namen des Elements abrufen.

```
const CString& GetItemName() const;
```

### <a name="return-value"></a>Rückgabewert

Der Name des Elements.

### <a name="remarks"></a>Hinweise

Diese Funktion wird in der Regel nur für verknüpfte Elemente aufgerufen.

##  <a name="getlinksourcedata"></a>COleServerItem:: getlinksourcedata

Mit dieser Funktion werden die CF_LINKSOURCE Daten für ein OLE-Element abzurufen.

```
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parameter

*lpstgmedium*<br/>
Ein Zeiger auf die [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) -Struktur, die die CF_LINKSOURCE Daten für das OLE-Element empfängt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Dieses Format enthält die CLSID, die den Typ des OLE-Elements beschreibt, sowie die Informationen, die erforderlich sind, um das Dokument zu finden, das das OLE-Element

Das Ergebnis kann dann mit [COleDataSource:: CacheData](../../mfc/reference/coledatasource-class.md#cachedata)zu einer Datenquelle hinzugefügt werden. Diese Funktion wird automatisch von [OnGetClipboardData](#ongetclipboarddata)aufgerufen.

Weitere Informationen finden Sie unter [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) in der Windows SDK.

##  <a name="getobjectdescriptordata"></a>COleServerItem:: getobjectdescriptor Data

Mit dieser Funktion werden die CF_OBJECTDESCRIPTOR Daten für ein OLE-Element abzurufen.

```
void GetObjectDescriptorData(
    LPPOINT lpOffset,
    LPSIZE lpSize,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parameter

*lpoffset*<br/>
Offset des Mausklicks von der linken oberen Ecke des OLE-Elements. Kann NULL sein.

*lpsize*<br/>
Größe des OLE-Elements. Kann NULL sein.

*lpstgmedium*<br/>
Ein Zeiger auf die [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) -Struktur, die die CF_OBJECTDESCRIPTOR Daten für das OLE-Element empfängt.

### <a name="remarks"></a>Hinweise

Die Informationen werden in die `STGMEDIUM` Struktur kopiert, auf die von *lpstgmedium*verwiesen wird. Dieses Format enthält die Informationen, die für das Dialogfeld "spezielles einfügen" benötigt werden.

Weitere Informationen finden Sie unter [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) in der Windows SDK.

##  <a name="isconnected"></a>COleServerItem:: IsConnected

Mit dieser Funktion können Sie feststellen, ob das OLE-Element verbunden ist.

```
BOOL IsConnected() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Element verbunden ist. andernfalls 0.

### <a name="remarks"></a>Hinweise

Ein OLE-Element wird als verbunden betrachtet, wenn ein oder mehrere Container Verweise auf das Element aufweisen. Ein Element ist verbunden, wenn der Verweis Zähler größer als 0 (null) ist, oder wenn es sich um ein eingebettetes Element handelt.

##  <a name="islinkeditem"></a>COleServerItem:: islinkeditem

Mit dieser Funktion können Sie feststellen, ob das OLE-Element ein verknüpftes Element ist.

```
BOOL IsLinkedItem() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Element ein verknüpftes Element ist. andernfalls 0.

### <a name="remarks"></a>Hinweise

Ein Element wird verknüpft, wenn das Element gültig ist und nicht in der Liste der eingebetteten Elemente des Dokuments zurückgegeben wird. Ein verknüpftes Element ist möglicherweise mit einem Container verbunden.

Es kommt häufig vor, dass die gleiche Klasse sowohl für verknüpfte als auch für eingebettete Elemente verwendet wird. `IsLinkedItem` ermöglicht es Ihnen, verknüpfte Elemente anders zu gestalten als eingebettete Elemente, obwohl der Code häufig häufig vorkommen kann.

##  <a name="m_sizeextent"></a>COleServerItem:: m_sizeExtent

Dieser Member teilt dem Server mit, wie viel des Objekts im Container Dokument sichtbar ist.

```
CSize m_sizeExtent;
```

### <a name="remarks"></a>Hinweise

Die Standard Implementierung von [onsetextent](#onsetextent) legt diesen Member fest.

##  <a name="notifychanged"></a>COleServerItem:: notifychanged

Diese Funktion wird aufgerufen, nachdem das verknüpfte Element geändert wurde.

```
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>Parameter

*ndrawaspect*<br/>
Ein Wert aus der DVASPECT-Enumeration, der angibt, welcher Aspekt des OLE-Elements geändert wurde. Dieser Parameter kann einen der folgenden Werte aufweisen:

- DVASPECT_CONTENT Element wird so dargestellt, dass es als eingebettetes Objekt in seinem Container angezeigt werden kann.

- DVASPECT_THUMBNAIL Element wird in einer "Miniaturansicht"-Darstellung gerendert, sodass es in einem Browsertool angezeigt werden kann.

- DVASPECT_ICON Element wird durch ein Symbol dargestellt.

- DVASPECT_DOCPRINT Element wird dargestellt, als ob es mithilfe des Befehls Drucken im Menü Datei gedruckt wurde.

### <a name="remarks"></a>Hinweise

Wenn ein Containerelement mit einem automatischen Link mit dem Dokument verknüpft ist, wird das Element aktualisiert, um die Änderungen widerzuspiegeln. In mithilfe des Microsoft Foundation Class-Bibliothek geschriebenen Container Anwendungen wird [COleClientItem:: OnChange](../../mfc/reference/coleclientitem-class.md#onchange) als Antwort aufgerufen.

##  <a name="ondoverb"></a>COleServerItem:: ondoverb

Wird von Framework aufgerufen, um das angegebene Verb auszuführen.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>Parameter

*iVerb*<br/>
Gibt das auszuführende Verb an. Dabei kann es sich um einen der folgenden handeln:

|Wert|Bedeutung|Symbol|
|-----------|-------------|------------|
|0|Primäres Verb|OLEIVERB_PRIMARY|
|1|Sekundäres Verb|(Kein)|
|- 1|Element zur Bearbeitung anzeigen|OLEIVERB_SHOW|
|- 2|Element im separaten Fenster bearbeiten|OLEIVERB_OPEN|
|- 3|Element ausblenden|OLEIVERB_HIDE|

Der-1-Wert ist in der Regel ein Alias für ein anderes Verb. Wenn offene Bearbeitung nicht unterstützt wird, hat-2 denselben Effekt wie-1. Weitere Werte finden Sie unter [IOleObject::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) in der Windows SDK.

### <a name="remarks"></a>Hinweise

Wenn die Containeranwendung mit dem Microsoft Foundation Class-Bibliothek geschrieben wurde, wird diese Funktion aufgerufen, wenn die [COleClientItem:: Aktivierungs](../../mfc/reference/coleclientitem-class.md#activate) -Member-Funktion des entsprechenden `COleClientItem` Objekts aufgerufen wird. Die Standard Implementierung ruft die [onShow](#onshow) -Element Funktion auf, wenn das primäre Verb oder OLEIVERB_SHOW angegeben ist, [OnOpen](#onopen) , wenn das sekundäre Verb oder OLEIVERB_OPEN angegeben ist, und [onHide](#onhide) , wenn OLEIVERB_HIDE angegeben ist. Die Standard Implementierung ruft `OnShow` auf, wenn *iVerb* nicht eines der oben aufgeführten Verben ist.

Überschreiben Sie diese Funktion, wenn das primäre Verb das Element nicht anzeigt. Wenn das Element z. b. eine Sound Aufzeichnung ist und das primäre Verb wiedergegeben wird, müssen Sie die Serveranwendung nicht anzeigen, um das Element wiederzugeben.

Weitere Informationen finden Sie unter [IOleObject::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) in der Windows SDK.

##  <a name="ondraw"></a>COleServerItem:: OnDraw

Wird von Framework aufgerufen, um das OLE-Element in einer Metadatei zu Rendering.

```
virtual BOOL OnDraw(
    CDC* pDC,
    CSize& rSize) = 0;
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Ein Zeiger auf das [CDC](../../mfc/reference/cdc-class.md) -Objekt, für das das Element gezeichnet werden soll. Der Anzeige Kontext wird automatisch mit dem Attribut Anzeige Kontext verbunden, sodass Sie Attribut Funktionen aufrufen können. Dies würde jedoch dazu führen, dass die Metadatei gerätespezifisch ist.

*rSize*<br/>
Größe in HIMETRIC-Einheiten, in der die Metadatei gezeichnet werden soll.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Element erfolgreich gezeichnet wurde. andernfalls 0.

### <a name="remarks"></a>Hinweise

Die metadateidarstellung des OLE-Elements wird verwendet, um das Element in der Containeranwendung anzuzeigen. Wenn die Containeranwendung mit dem Microsoft Foundation Class-Bibliothek geschrieben wurde, wird die Metadatendatei von der [Draw](../../mfc/reference/coleclientitem-class.md#draw) -Member-Funktion des entsprechenden [COleClientItem](../../mfc/reference/coleclientitem-class.md) -Objekts verwendet. Es ist keine Standardimplementierung vorhanden. Sie müssen diese Funktion überschreiben, um das Element in den angegebenen Gerätekontext zu zeichnen.

##  <a name="ondrawex"></a>COleServerItem:: ondrawex

Wird vom Framework für alle Zeichnungen aufgerufen.

```
virtual BOOL OnDrawEx(
    CDC* pDC,
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Ein Zeiger auf das [CDC](../../mfc/reference/cdc-class.md) -Objekt, für das das Element gezeichnet werden soll. Der Domänen Controller wird automatisch mit dem Attribut Domänen Controller verbunden, sodass Sie Attribut Funktionen aufzurufen, obwohl dies dazu führen würde, dass die Metadatei gerätespezifisch ist.

*ndrawaspect*<br/>
Ein Wert aus der DVASPECT-Enumeration. Dieser Parameter kann einen der folgenden Werte aufweisen:

- DVASPECT_CONTENT Element wird so dargestellt, dass es als eingebettetes Objekt in seinem Container angezeigt werden kann.

- DVASPECT_THUMBNAIL Element wird in einer "Miniaturansicht"-Darstellung gerendert, sodass es in einem Browsertool angezeigt werden kann.

- DVASPECT_ICON Element wird durch ein Symbol dargestellt.

- DVASPECT_DOCPRINT Element wird dargestellt, als ob es mithilfe des Befehls Drucken im Menü Datei gedruckt wurde.

*rSize*<br/>
Größe des Elements in HIMETRIC-Einheiten.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Element erfolgreich gezeichnet wurde. andernfalls 0.

### <a name="remarks"></a>Hinweise

Die Standard Implementierung ruft `OnDraw` auf, wenn DVASPECT gleich DVASPECT_CONTENT ist. Andernfalls tritt ein Fehler auf.

Überschreiben Sie diese Funktion, um Präsentationsdaten für andere Aspekte als DVASPECT_CONTENT bereitzustellen, z. b. DVASPECT_ICON oder DVASPECT_THUMBNAIL.

##  <a name="ongetclipboarddata"></a>COleServerItem:: OnGetClipboardData

Wird von Framework aufgerufen, um ein `COleDataSource` Objekt abzurufen, das alle Daten enthält, die durch einen Aufruf der [CopyTo Clipboard](#copytoclipboard) -Member-Funktion in der Zwischenablage platziert werden.

```
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,
    LPPOINT lpOffset,
    LPSIZE lpSize);
```

### <a name="parameters"></a>Parameter

*bincludelta Ink*<br/>
Legen Sie diese Einstellung auf true fest, wenn Verknüpfungs Daten in die Zwischenablage kopiert werden sollen. Legen Sie diese Einstellung auf "false" fest, wenn die Serveranwendung keine Links unterstützt.

*lpoffset*<br/>
Der Offset des Maus Cursors vom Ursprung des-Objekts in Pixel.

*lpsize*<br/>
Die Größe des-Objekts in Pixel.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [COleDataSource](../../mfc/reference/coledatasource-class.md) -Objekt, das die Zwischenablage Daten enthält.

### <a name="remarks"></a>Hinweise

Die Standard Implementierung dieser Funktion ruft [GetClipboardData](#getclipboarddata)auf.

##  <a name="ongetextent"></a>COleServerItem:: OnGetExtent

Wird von Framework aufgerufen, um die Größe des OLE-Elements in HIMETRIC-Einheiten abzurufen.

```
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Parameter

*ndrawaspect*<br/>
Gibt den Aspekt des OLE-Elements an, dessen Begrenzungen abgerufen werden sollen. Dieser Parameter kann einen der folgenden Werte aufweisen:

- DVASPECT_CONTENT Element wird so dargestellt, dass es als eingebettetes Objekt in seinem Container angezeigt werden kann.

- DVASPECT_THUMBNAIL Element wird in einer "Miniaturansicht"-Darstellung gerendert, sodass es in einem Browsertool angezeigt werden kann.

- DVASPECT_ICON Element wird durch ein Symbol dargestellt.

- DVASPECT_DOCPRINT Element wird dargestellt, als ob es mithilfe des Befehls Drucken im Menü Datei gedruckt wurde.

*rSize*<br/>
Verweis auf ein `CSize` Objekt, das die Größe des OLE-Elements empfängt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Wenn die Containeranwendung mit dem Microsoft Foundation Class-Bibliothek geschrieben wurde, wird diese Funktion aufgerufen, wenn die [GetExtent](../../mfc/reference/coleclientitem-class.md#getextent) -Member-Funktion des entsprechenden `COleClientItem` Objekts aufgerufen wird. Bei der Standardimplementierung wird keine Aktion ausgeführt. Sie müssen Sie selbst implementieren. Überschreiben Sie diese Funktion, wenn Sie bei der Verarbeitung einer Anforderung für die Größe des OLE-Elements eine besondere Verarbeitung durchführen möchten.

##  <a name="onhide"></a>COleServerItem:: onHide

Wird von Framework aufgerufen, um das OLE-Element auszublenden.

```
virtual void OnHide();
```

### <a name="remarks"></a>Hinweise

Der Standard Aufruf `COleServerDoc::OnShowDocument( FALSE )`. Die Funktion benachrichtigt den Container außerdem darüber, dass das OLE-Element ausgeblendet wurde. Überschreiben Sie diese Funktion, wenn Sie beim Ausblenden eines OLE-Elements eine besondere Verarbeitung durchführen möchten.

##  <a name="oninitfromdata"></a>COleServerItem:: oninitfromdata

Wird von Framework aufgerufen, um ein OLE-Element mit dem Inhalt von *pdataobject*zu initialisieren.

```
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,
    BOOL bCreation);
```

### <a name="parameters"></a>Parameter

*pDataObject*<br/>
Zeiger auf ein OLE-Datenobjekt, das Daten in verschiedenen Formaten zum Initialisieren des OLE-Elements enthält.

*bcreation*<br/>
TRUE, wenn die Funktion aufgerufen wird, um ein OLE-Element zu initialisieren, das von einer Containeranwendung neu erstellt wird. FALSE, wenn die Funktion aufgerufen wird, um den Inhalt eines bereits vorhandenen OLE-Elements zu ersetzen.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Wenn *bcreation* den Wert true hat, wird diese Funktion aufgerufen, wenn ein Container das Einfügen eines neuen Objekts auf der Grundlage der aktuellen Auswahl implementiert. Die ausgewählten Daten werden beim Erstellen des neuen OLE-Elements verwendet. Wenn Sie z. b. einen Zellbereich in einem Tabellenkalkulationsprogramm auswählen und dann das Insert New-Objekt verwenden, um ein Diagramm auf der Grundlage der Werte im ausgewählten Bereich zu erstellen. Bei der Standardimplementierung wird keine Aktion ausgeführt. Überschreiben Sie diese Funktion, um ein akzeptables Format auszuwählen, das von *pdataobject* angeboten wird, und initialisieren Sie das OLE-Element auf der Grundlage der bereitgestellten Daten. Hierbei handelt es sich um eine erweiterte über schreibbare.

Weitere Informationen finden Sie unter [IOleObject:: initfromdata](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) in der Windows SDK.

##  <a name="onopen"></a>COleServerItem:: OnOpen

Wird von Framework aufgerufen, um das OLE-Element in einer separaten Instanz der Serveranwendung anstatt direkt anzuzeigen.

```
virtual void OnOpen();
```

### <a name="remarks"></a>Hinweise

Die Standard Implementierung aktiviert das erste Rahmen Fenster, das das Dokument anzeigt, das das OLE-Element enthält. Wenn es sich bei der Anwendung um einen Miniserver handelt, wird in der Standard Implementierung das Hauptfenster angezeigt. Die Funktion benachrichtigt den Container außerdem darüber, dass das OLE-Element geöffnet wurde.

Überschreiben Sie diese Funktion, wenn Sie beim Öffnen eines OLE-Elements eine besondere Verarbeitung durchführen möchten. Dies ist insbesondere bei verknüpften Elementen der Fall, in denen Sie die Auswahl auf den Link festlegen möchten, wenn Sie geöffnet wird.

Weitere Informationen finden Sie unter [IOleClientSite:: onshowwindow](/windows/win32/api/oleidl/nf-oleidl-ioleclientsite-onshowwindow) in der Windows SDK.

##  <a name="onqueryupdateitems"></a>COleServerItem:: onqueryupdateitems

Wird von Framework aufgerufen, um zu bestimmen, ob verknüpfte Elemente im aktuellen Server Dokument veraltet sind.

```
virtual BOOL OnQueryUpdateItems();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn für das Dokument Elemente erforderlich sind 0, wenn alle Elemente auf dem neuesten Stand sind.

### <a name="remarks"></a>Hinweise

Ein Element ist veraltet, wenn das Quelldokument geändert wurde, aber das verknüpfte Element nicht aktualisiert wurde, um die Änderungen im Dokument widerzuspiegeln.

##  <a name="onrenderdata"></a>COleServerItem:: OnRenderData

Wird von Framework aufgerufen, um Daten im angegebenen Format abzurufen.

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parameter

*lpformatusw.*<br/>
Verweist auf die [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur, die das Format angibt, in dem Informationen angefordert werden.

*lpstgmedium*<br/>
Verweist auf eine [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) -Struktur, in der die Daten zurückgegeben werden sollen.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Das angegebene Format ist ein zuvor im `COleDataSource` Objekt angegebenes-Objekt, das die Element Funktion " [Delta Data](../../mfc/reference/coledatasource-class.md#delayrenderdata) " oder " [Delta Data](../../mfc/reference/coledatasource-class.md#delayrenderfiledata) " für verzögertes Rendering verwendet. Die Standard Implementierung dieser Funktion ruft [onrenderfiledata](#onrenderfiledata) bzw. [onrenderglobaldata](#onrenderglobaldata)auf, wenn es sich bei dem angegebenen Speichermedium entweder um eine Datei oder einen Arbeitsspeicher handelt. Wenn keines dieser Formate angegeben wird, gibt die Standard Implementierung 0 zurück und bewirkt nichts.

Wenn *lpstgmedium*-> *TYMED* TYMED_NULL ist, sollte STGMEDIUM entsprechend der Angabe durch *lpformatusw-> TYMED*zugeordnet und ausgefüllt werden. Wenn nicht TYMED_NULL, sollte das STGMEDIUM mit den Daten aufgefüllt werden.

Hierbei handelt es sich um eine erweiterte über schreibbare. Überschreiben Sie diese Funktion, um die Daten im angeforderten Format und Medium bereitzustellen. Abhängig von den Daten können Sie stattdessen eine der anderen Versionen dieser Funktion überschreiben. Wenn Ihre Daten klein und in der Größe liegen, überschreiben Sie `OnRenderGlobalData`. Wenn sich die Daten in einer Datei befinden oder eine Variable Größe hat, überschreiben Sie `OnRenderFileData`.

Weitere Informationen finden Sie unter " [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata)", " [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)", " [formatusw](/windows/win32/api/objidl/ns-objidl-formatetc)" und " [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) " in der Windows SDK.

##  <a name="onrenderfiledata"></a>COleServerItem:: onrenderfiledata

Wird von Framework aufgerufen, um Daten im angegebenen Format abzurufen, wenn das Speichermedium eine Datei ist.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Parameter

*lpformatusw.*<br/>
Verweist auf die [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur, die das Format angibt, in dem Informationen angefordert werden.

*pFile*<br/>
Verweist auf ein `CFile` Objekt, in dem die Daten gerendert werden sollen.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Das angegebene Format ist ein zuvor im `COleDataSource` Objekt angegebenes-Objekt, das die Funktion " [Delta Data](../../mfc/reference/coledatasource-class.md#delayrenderdata) " für verzögertes Rendering verwendet. Die Standard Implementierung dieser Funktion gibt einfach false zurück.

Hierbei handelt es sich um eine erweiterte über schreibbare. Überschreiben Sie diese Funktion, um die Daten im angeforderten Format und Medium bereitzustellen. Abhängig von den Daten können Sie stattdessen eine der anderen Versionen dieser Funktion überschreiben. Wenn Sie mehrere Speichermedien verarbeiten möchten, überschreiben Sie [OnRenderData](#onrenderdata). Wenn sich Ihre Daten in einer Datei befinden oder eine Variable Größe haben, überschreiben Sie [onrenderfiledata](#onrenderfiledata).

Weitere Informationen finden Sie unter [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) und [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) in der Windows SDK.

##  <a name="onrenderglobaldata"></a>COleServerItem:: onrenderglobaldata

Wird von Framework aufgerufen, um Daten im angegebenen Format abzurufen, wenn das angegebene Speichermedium globaler Speicher ist.

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>Parameter

*lpformatusw.*<br/>
Verweist auf die [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur, die das Format angibt, in dem Informationen angefordert werden.

*phglobal*<br/>
Verweist auf ein Handle für den globalen Speicher, in dem die Daten zurückgegeben werden sollen. Wenn kein Arbeitsspeicher zugeordnet wurde, kann dieser Parameter NULL sein.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Das angegebene Format ist ein zuvor im `COleDataSource` Objekt angegebenes-Objekt, das die Funktion " [Delta Data](../../mfc/reference/coledatasource-class.md#delayrenderdata) " für verzögertes Rendering verwendet. Die Standard Implementierung dieser Funktion gibt einfach false zurück.

Wenn *phglobal* NULL ist, sollte ein neues HGLOBAL zugeordnet und in *phglobal*zurückgegeben werden. Andernfalls sollte der von *phglobal* angegebene HGLOBAL mit den Daten gefüllt werden. Die Menge der in der hglobal platzierten Daten darf die aktuelle Größe des Speicherblocks nicht überschreiten. Außerdem kann der Block nicht neu zugeordnet werden.

Hierbei handelt es sich um eine erweiterte über schreibbare. Überschreiben Sie diese Funktion, um die Daten im angeforderten Format und Medium bereitzustellen. Abhängig von den Daten können Sie stattdessen eine der anderen Versionen dieser Funktion überschreiben. Wenn Sie mehrere Speichermedien verarbeiten möchten, überschreiben Sie [OnRenderData](#onrenderdata). Wenn sich Ihre Daten in einer Datei befinden oder eine Variable Größe haben, überschreiben Sie [onrenderfiledata](#onrenderfiledata).

Weitere Informationen finden Sie unter [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) und [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) in der Windows SDK.

##  <a name="onsetcolorscheme"></a>COleServerItem:: onsetcolorscheme

Wird von Framework aufgerufen, um eine Farbpalette anzugeben, die beim Bearbeiten des OLE-Elements verwendet werden soll.

```
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```

### <a name="parameters"></a>Parameter

*lplogpalette*<br/>
Zeiger auf eine Windows- [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) -Struktur.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Farbpalette verwendet wird; andernfalls 0.

### <a name="remarks"></a>Hinweise

Wenn die Containeranwendung mithilfe des Microsoft Foundation Class-Bibliothek geschrieben wurde, wird diese Funktion aufgerufen, wenn die [IOleObject:: SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) -Funktion des entsprechenden `COleClientItem` Objekts aufgerufen wird. Die Standard Implementierung gibt false zurück. Überschreiben Sie diese Funktion, wenn Sie die empfohlene Palette verwenden möchten. Die Serveranwendung muss die vorgeschlagene Palette nicht verwenden.

Weitere Informationen finden Sie unter [IOleObject:: SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) in der Windows SDK.

##  <a name="onsetdata"></a>COleServerItem:: onsetdata

Wird von Framework aufgerufen, um die Daten des OLE-Elements durch die angegebenen Daten zu ersetzen.

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>Parameter

*lpformatusw.*<br/>
Ein Zeiger auf eine [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur, die das Format der Daten angibt.

*lpstgmedium*<br/>
Zeiger auf eine [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) -Struktur, in der sich die Daten befinden.

*brelease*<br/>
Gibt an, wer den Besitz des Speichermediums nach Abschluss des Funktions Aufrufes besitzt. Der Aufrufer entscheidet, wer für das Freigeben der im Auftrag des Speichermediums zugewiesenen Ressourcen zuständig ist. Der Aufrufer legt dies durch Festlegen von *brelease*fest. Wenn die *brelease* ungleich NULL ist, übernimmt das Server Element den Besitz und gibt das Medium frei, wenn es nicht mehr verwendet wird. Wenn *brelease* den Wert 0 hat, behält der Aufrufer den Besitz, und das Server Element kann das Speichermedium nur für die Dauer des Aufrufes verwenden.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Das Server Element übernimmt den Besitz der Daten erst, wenn es erfolgreich abgerufen wurde. Dies bedeutet, dass Sie keinen Besitz übernimmt, wenn Sie 0 zurückgibt. Wenn die Datenquelle den Besitz übernimmt, wird das Speichermedium durch Aufrufen der [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) -Funktion freigegeben.

Bei der Standardimplementierung wird keine Aktion ausgeführt. Überschreiben Sie diese Funktion, um die Daten des OLE-Elements durch die angegebenen Daten zu ersetzen. Hierbei handelt es sich um eine erweiterte über schreibbare.

Weitere Informationen finden Sie im Windows SDK unter [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1), [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)und [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) .

##  <a name="onsetextent"></a>COleServerItem:: onabtextent

Wird von Framework aufgerufen, um dem OLE-Element mitzuteilen, wie viel Speicherplatz im Container Dokument verfügbar ist.

```
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,
    const CSize& size);
```

### <a name="parameters"></a>Parameter

*ndrawaspect*<br/>
Gibt den Aspekt des OLE-Elements an, dessen Begrenzungen angegeben werden. Dieser Parameter kann einen der folgenden Werte aufweisen:

- DVASPECT_CONTENT Element wird so dargestellt, dass es als eingebettetes Objekt in seinem Container angezeigt werden kann.

- DVASPECT_THUMBNAIL Element wird in einer "Miniaturansicht"-Darstellung gerendert, sodass es in einem Browsertool angezeigt werden kann.

- DVASPECT_ICON Element wird durch ein Symbol dargestellt.

- DVASPECT_DOCPRINT Element wird dargestellt, als ob es mithilfe des Befehls Drucken im Menü Datei gedruckt wurde.

*size*<br/>
Eine [CSize](../../atl-mfc-shared/reference/csize-class.md) -Struktur, die die neue Größe des OLE-Elements angibt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Wenn die Containeranwendung mit dem Microsoft Foundation Class-Bibliothek geschrieben wurde, wird diese Funktion aufgerufen, wenn die [SetExtent](../../mfc/reference/coleclientitem-class.md#setextent) -Member-Funktion des entsprechenden `COleClientItem` Objekts aufgerufen wird. Mit der Standard Implementierung wird der [m_sizeExtent](#m_sizeextent) Member auf die angegebene Größe festgelegt, wenn *ndrawaspect* DVASPECT_CONTENT ist. Andernfalls wird 0 zurückgegeben. Überschreiben Sie diese Funktion, um eine besondere Verarbeitung durchzuführen, wenn Sie die Größe des Elements ändern.

##  <a name="onshow"></a>COleServerItem:: onShow

Wird von Framework aufgerufen, um die Serveranwendung anzuweisen, das OLE-Element direkt anzuzeigen.

```
virtual void OnShow();
```

### <a name="remarks"></a>Hinweise

Diese Funktion wird in der Regel aufgerufen, wenn der Benutzer der Containeranwendung ein Element erstellt oder ein Verb ausführt, z. b. "Bearbeiten", bei dem das Element angezeigt werden muss. Die Standard Implementierung versucht, eine direkte Aktivierung durchgeführt werden. Wenn dies nicht möglich ist, ruft die Funktion die `OnOpen` Member-Funktion auf, um das OLE-Element in einem separaten Fenster anzuzeigen.

Überschreiben Sie diese Funktion, wenn Sie eine besondere Verarbeitung durchführen möchten, wenn ein OLE-Element angezeigt wird.

##  <a name="onupdate"></a>COleServerItem:: OnUpdate

Wird von Framework aufgerufen, wenn ein Element geändert wurde.

```
virtual void OnUpdate(
    COleServerItem* pSender,
    LPARAM lHint,
    CObject* pHint,
    DVASPECT nDrawAspect);
```

### <a name="parameters"></a>Parameter

*psender*<br/>
Zeiger auf das Element, das das Dokument geändert hat. Kann NULL sein.

*lHint*<br/>
Enthält Informationen über die Änderung.

*phint*<br/>
Zeiger auf ein Objekt, das Informationen über die Änderung speichert.

*ndrawaspect*<br/>
Ein Wert aus der DVASPECT-Enumeration. Dieser Parameter kann einen der folgenden Werte aufweisen:

- DVASPECT_CONTENT Element wird so dargestellt, dass es als eingebettetes Objekt in seinem Container angezeigt werden kann.

- DVASPECT_THUMBNAIL Element wird in einer "Miniaturansicht"-Darstellung gerendert, sodass es in einem Browsertool angezeigt werden kann.

- DVASPECT_ICON Element wird durch ein Symbol dargestellt.

- DVASPECT_DOCPRINT Element wird dargestellt, als ob es mithilfe des Befehls Drucken im Menü Datei gedruckt wurde.

### <a name="remarks"></a>Hinweise

Die Standard Implementierung ruft [notifychanged](#notifychanged)auf, ungeachtet des Hinweises oder Absenders.

##  <a name="onupdateitems"></a>COleServerItem:: onupdateitems

Wird von Framework aufgerufen, um alle Elemente im Server Dokument zu aktualisieren.

```
virtual void OnUpdateItems();
```

### <a name="remarks"></a>Hinweise

Die Standard Implementierung ruft [UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink) für alle `COleClientItem`-Objekte im Dokument auf.

##  <a name="setitemname"></a>COleServerItem:: Servername

Rufen Sie diese Funktion auf, wenn Sie ein verknüpftes Element erstellen, um seinen Namen festzulegen.

```
void SetItemName(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Parameter

*lpszitemname*<br/>
Zeiger auf den neuen Namen des Elements.

### <a name="remarks"></a>Hinweise

Der Name muss innerhalb des Dokuments eindeutig sein. Wenn eine Serveranwendung aufgerufen wird, um ein verknüpftes Element zu bearbeiten, verwendet die Anwendung diesen Namen, um das Element zu suchen. Sie müssen diese Funktion nicht für eingebettete Elemente aufzurufen.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel Hierarchien](../../overview/visual-cpp-samples.md)<br/>
[CDocItem-Klasse](../../mfc/reference/cdocitem-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem-Klasse](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerDoc-Klasse](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleTemplateServer-Klasse](../../mfc/reference/coletemplateserver-class.md)
