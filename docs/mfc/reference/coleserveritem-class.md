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
ms.openlocfilehash: bdb91168a7c0ae718ca7d7514448b55965186aa8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753744"
---
# <a name="coleserveritem-class"></a>COleServerItem-Klasse

Stellt die Serverschnittstelle zu OLE-Elementen bereit.

## <a name="syntax"></a>Syntax

```
class COleServerItem : public CDocItem
```

## <a name="members"></a>Member

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleServerItem::COleServerItem](#coleserveritem)|Erstellt ein `COleServerItem`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleServerItem::AddOtherClipboardData](#addotherclipboarddata)|Platziert Präsentations- und `COleDataSource` Konvertierungsformate in einem Objekt.|
|[COleServerItem::CopyToClipboard](#copytoclipboard)|Kopiert das Element in die Zwischenablage.|
|[COleServerItem::DoDragDrop](#dodragdrop)|Führt einen Drag-and-Drop-Vorgang aus.|
|[COleServerItem::GetClipboardData](#getclipboarddata)|Ruft die Datenquelle für die Verwendung bei der Datenübertragung ab (Drag & Drop oder Zwischenablage).|
|[COleServerItem::GetDocument](#getdocument)|Gibt das Serverdokument zurück, das das Element enthält.|
|[COleServerItem::GetEmbedSourceData](#getembedsourcedata)|Ruft die CF_EMBEDSOURCE Daten für ein OLE-Element ab.|
|[COleServerItem::GetItemName](#getitemname)|Gibt den Namen des Elements zurück. Wird nur für verknüpfte Artikel verwendet.|
|[COleServerItem::GetLinkSourceData](#getlinksourcedata)|Ruft die CF_LINKSOURCE Daten für ein OLE-Element ab.|
|[COleServerItem::GetObjectDescriptorData](#getobjectdescriptordata)|Ruft die CF_OBJECTDESCRIPTOR Daten für ein OLE-Element ab.|
|[COleServerItem::IsConnected](#isconnected)|Gibt an, ob das Element derzeit einem aktiven Container zugeordnet ist.|
|[COleServerItem::IsLinkedItem](#islinkeditem)|Gibt an, ob das Element ein verknüpftes OLE-Element darstellt.|
|[COleServerItem::NotifyChanged](#notifychanged)|Aktualisiert alle Container mit automatischer Linkaktualisierung.|
|[COleServerItem::OnDoverb](#ondoverb)|Wird aufgerufen, um ein Verb auszuführen.|
|[COleServerItem::OnDraw](#ondraw)|Wird aufgerufen, wenn der Container das Element zeichnen möchte; Umsetzung erforderlich ist.|
|[COleServerItem::OnDrawex](#ondrawex)|Wird für spezielle Artikelzeichnung aufgerufen.|
|[COleServerItem::OnGetClipboardData](#ongetclipboarddata)|Wird vom Framework aufgerufen, um die Daten abzubekommen, die in die Zwischenablage kopiert werden.|
|[COleServerItem::OnGetExtent](#ongetextent)|Wird vom Framework aufgerufen, um die Größe des OLE-Elements abzurufen.|
|[COleServerItem::OnInitFromData](#oninitfromdata)|Wird vom Framework aufgerufen, um ein OLE-Element mithilfe des angegebenen Inhalts des Datenübertragungsobjekts zu initialisieren.|
|[COleServerItem::OnQueryUpdateItems](#onqueryupdateitems)|Wird aufgerufen, um zu bestimmen, ob verknüpfte Elemente aktualisiert werden müssen.|
|[COleServerItem::OnRenderdata](#onrenderdata)|Ruft Daten als Teil des verzögerten Renderings ab.|
|[COleServerItem::OnRenderFileData](#onrenderfiledata)|Ruft Daten in `CFile` einem Objekt als Teil des verzögerten Renderings ab.|
|[COleServerItem::OnRenderGlobalData](#onrenderglobaldata)|Ruft Daten in einem HGLOBAL als Teil des verzögerten Renderings ab.|
|[COleServerItem::OnSetColorScheme](#onsetcolorscheme)|Wird aufgerufen, um das Farbschema des Elements festzulegen.|
|[COleServerItem::OnSetdata](#onsetdata)|Wird aufgerufen, um die Daten des Elements festzulegen.|
|[COleServerItem::OnSetExtent](#onsetextent)|Wird vom Framework aufgerufen, um die Größe des OLE-Elements festzulegen.|
|[COleServerItem::OnUpdate](#onupdate)|Wird aufgerufen, wenn ein Teil des Dokuments, in das das Element gehört, geändert wird.|
|[COleServerItem::OnUpdateItems](#onupdateitems)|Wird aufgerufen, um den Präsentationscache aller Elemente im Serverdokument zu aktualisieren.|
|[COleServerItem::SetItemName](#setitemname)|Legt den Namen des Elements fest. Wird nur für verknüpfte Artikel verwendet.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleServerItem::GetDataSource](#getdatasource)|Ruft das Objekt ab, das zum Speichern von Konvertierungsformaten verwendet wird.|
|[COleServerItem::OnHide](#onhide)|Wird vom Framework aufgerufen, um das OLE-Element auszublenden.|
|[COleServerItem::OnOpen](#onopen)|Wird vom Framework aufgerufen, um das OLE-Element in einem eigenen Fenster der obersten Ebene anzuzeigen.|
|[COleServerItem::OnShow](#onshow)|Wird aufgerufen, wenn der Container anfordert, das Element anzuzeigen.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleServerItem::m_sizeExtent](#m_sizeextent)|Informiert den Server darüber, wie viel des OLE-Elements sichtbar ist.|

## <a name="remarks"></a>Bemerkungen

Ein verknüpftes Element kann einen Teil oder das gesamte Serverdokument darstellen. Ein eingebettetes Element stellt immer ein gesamtes Serverdokument dar.

Die `COleServerItem` Klasse definiert mehrere überschreibbare Memberfunktionen, die von den OLE-System-Dynamic-Link-Bibliotheken (DLLs) aufgerufen werden, in der Regel als Reaktion auf Anforderungen der Containeranwendung. Diese Memberfunktionen ermöglichen es der Containeranwendung, das Element indirekt auf verschiedene Weise zu bearbeiten, z. B. indem es angezeigt, seine Verben ausgeführt oder seine Daten in verschiedenen Formaten abgerufen werden.

Um `COleServerItem`zu verwenden, leiten Sie daraus eine Klasse ab und implementieren Sie die [Memberfunktionen OnDraw](#ondraw) und [Serialize.](../../mfc/reference/cobject-class.md#serialize) Die `OnDraw` Funktion stellt die Metadateidarstellung eines Elements bereit, sodass es angezeigt werden kann, wenn eine Containeranwendung ein zusammengesetztes Dokument öffnet. Die `Serialize` Funktion `CObject` von stellt die systemeigene Darstellung eines Elements bereit, sodass ein eingebettetes Element zwischen server- und containeranwendungen übertragen werden kann. [OnGetExtent](#ongetextent) stellt dem Container die natürliche Größe des Elements zur Verfügung, sodass der Container die Größe des Elements ändern kann.

Weitere Informationen zu Servern und verwandten Themen finden Sie im Artikel [Server: Implementieren eines Servers](../../mfc/servers-implementing-a-server.md) und "Erstellen einer Container/Server-Anwendung" im Artikel [Container: Erweiterte Funktionen](../../mfc/containers-advanced-features.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

`COleServerItem`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxole.h

## <a name="coleserveritemaddotherclipboarddata"></a><a name="addotherclipboarddata"></a>COleServerItem::AddOtherClipboardData

Rufen Sie diese Funktion auf, um die Präsentations- und Konvertierungsformate für das OLE-Element im angegebenen `COleDataSource` Objekt zu platzieren.

```cpp
void AddOtherClipboardData(COleDataSource* pDataSource);
```

### <a name="parameters"></a>Parameter

*pDataSource*<br/>
Zeigen Sie `COleDataSource` auf das Objekt, in dem die Daten platziert werden sollen.

### <a name="remarks"></a>Bemerkungen

Sie müssen die [OnDraw-Memberfunktion](#ondraw) implementiert haben, um das Präsentationsformat (ein Metadateibild) für das Element bereitzustellen. Um andere Konvertierungsformate zu unterstützen, registrieren Sie sie mit dem von [GetDataSource](#getdatasource) zurückgegebenen [COleDataSource-Objekt,](../../mfc/reference/coledatasource-class.md) und überschreiben Sie die [OnRenderData-Memberfunktion,](#onrenderdata) um Daten in den Formaten bereitzustellen, die Sie unterstützen möchten.

## <a name="coleserveritemcoleserveritem"></a><a name="coleserveritem"></a>COleServerItem::COleServerItem

Erstellt ein `COleServerItem` Objekt und fügt es der Auflistung von Dokumentelementen des Serverdokuments hinzu.

```
COleServerItem(
    COleServerDoc* pServerDoc,
    BOOL bAutoDelete);
```

### <a name="parameters"></a>Parameter

*pServerDoc*<br/>
Zeigen Sie auf das Dokument, das das neue Element enthält.

*bAutoDelete*<br/>
Flag, das angibt, ob das Objekt gelöscht werden kann, wenn ein Link zu ihm freigegeben wird. Legen Sie diesen `COleServerItem` Vorgang auf FALSE fest, wenn das Objekt ein integraler Bestandteil der Dokumentdaten ist, die Sie löschen müssen. Legen Sie diesen Wert auf TRUE fest, wenn es sich bei dem Objekt um eine sekundäre Struktur handelt, die zum Identifizieren eines Bereichs in den Dokumentdaten verwendet wird, der vom Framework gelöscht werden kann.

## <a name="coleserveritemcopytoclipboard"></a><a name="copytoclipboard"></a>COleServerItem::CopyToClipboard

Rufen Sie diese Funktion auf, um das OLE-Element in die Zwischenablage zu kopieren.

```cpp
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```

### <a name="parameters"></a>Parameter

*bIncludeLink*<br/>
Legen Sie diesen Wert auf TRUE fest, wenn Verknüpfungsdaten in die Zwischenablage kopiert werden sollen. Legen Sie diesen Satz auf FALSE fest, wenn Ihre Serveranwendung keine Links unterstützt.

### <a name="remarks"></a>Bemerkungen

Die Funktion verwendet die [OnGetClipboardData-Memberfunktion,](#ongetclipboarddata) um ein [COleDataSource-Objekt](../../mfc/reference/coledatasource-class.md) zu erstellen, das die Daten des OLE-Elements in den unterstützten Formaten enthält. Die Funktion platziert `COleDataSource` das Objekt dann in der Zwischenablage, indem sie die Funktion [COleDataSource::SetClipboard](../../mfc/reference/coledatasource-class.md#setclipboard) verwendet. Das `COleDataSource` Objekt enthält die systemeigenen Daten des Elements und seine Darstellung im CF_METAFILEPICT Format sowie Daten in allen Konvertierungsformaten, die Sie unterstützen möchten. Sie müssen [Serialize](../../mfc/reference/cobject-class.md#serialize) und [OnDraw](#ondraw) implementiert haben, damit diese Memberfunktion funktioniert.

## <a name="coleserveritemdodragdrop"></a><a name="dodragdrop"></a>COleServerItem::DoDragDrop

Rufen `DoDragDrop` Sie die Memberfunktion auf, um einen Drag-and-Drop-Vorgang auszuführen.

```
DROPEFFECT DoDragDrop(
    LPCRECT lpRectItem,
    CPoint ptOffset,
    BOOL bIncludeLink = FALSE,
    DWORD dwEffects = DROPEFFECT_COPY | DROPEFFECT_MOVE,
    LPCRECT lpRectStartDrag = NULL);
```

### <a name="parameters"></a>Parameter

*lpRectItem*<br/>
Das Rechteck des Elements auf dem Bildschirm in Pixel relativ zum Clientbereich.

*ptOffset*<br/>
Der Offset von *lpItemRect,* an dem sich die Mausposition zum Zeitpunkt des Ziehens befand.

*bIncludeLink*<br/>
Legen Sie diesen Wert auf TRUE fest, wenn Verknüpfungsdaten in die Zwischenablage kopiert werden sollen. Legen Sie sie auf FALSE fest, wenn Ihre Anwendung keine Links unterstützt.

*dwEffects*<br/>
Bestimmt die Effekte, die die Ziehquelle im Ziehvorgang zulässt (eine Kombination aus Kopieren, Verschieben und Verknüpfen).

*lpRectStartDrag*<br/>
Zeigen Sie mit dem Zeiger auf das Rechteck, das definiert, wo der Ziehvorgang tatsächlich beginnt. Weitere Informationen finden Sie im folgenden Abschnitt "Hinweise".

### <a name="return-value"></a>Rückgabewert

Ein Wert aus der DROPEFFECT-Enumeration. Wenn es sich um DROPEFFECT_MOVE, sollten die ursprünglichen Daten entfernt werden.

### <a name="remarks"></a>Bemerkungen

Der Drag-and-Drop-Vorgang wird nicht sofort gestartet. Es wartet, bis der Mauszeiger das von *lpRectStartDrag* angegebene Rechteck verlässt oder bis eine angegebene Anzahl von Millisekunden vergangen ist. Wenn *lpRectStartDrag* NULL ist, wird ein Standardrechteck verwendet, sodass der Ziehvorgang gestartet wird, wenn der Mauszeiger ein Pixel bewegt.

Die Verzögerungszeit wird durch eine Registrierungsschlüsseleinstellung angegeben. Sie können die Verzögerungszeit ändern, indem Sie [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) oder [CWinApp::WriteProfileInt aufrufen.](../../mfc/reference/cwinapp-class.md#writeprofileint) Wenn Sie die Verzögerungszeit nicht angeben, wird ein Standardwert von 200 Millisekunden verwendet. Die Verzögerungszeit des Ziehvorgangs wird wie folgt gespeichert:

- Die Verzögerungszeit für den Windows NT-Drag-Verzögerungszeit wird in HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-Windows-,NT-Nt-CurrentVersion-IniFileMapping-Win.ini-Windows-DragDelay gespeichert.

- Windows 3.x Drag Delay Time wird in der WIN gespeichert. INI-Datei unter dem Abschnitt [Windows".

- Windows 95/98 Drag Delay Time wird in einer zwischengespeicherten Version von WIN gespeichert. Ini.

Weitere Informationen dazu, wie Drag Delay-Informationen in der Registrierung oder im gespeichert werden. INI-Datei, siehe [WriteProfileString](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) im Windows SDK.

## <a name="coleserveritemgetclipboarddata"></a><a name="getclipboarddata"></a>COleServerItem::GetClipboardData

Rufen Sie diese Funktion auf, um das angegebene [COleDataSource-Objekt](../../mfc/reference/coledatasource-class.md) mit allen Daten auszufüllen, die in die Zwischenablage kopiert würden, wenn Sie [CopyToClipboard](#copytoclipboard) aufrufen (die gleichen Daten würden auch übertragen, wenn Sie [DoDragDrop](#dodragdrop)genannt haben).

```cpp
void GetClipboardData(
    COleDataSource* pDataSource,
    BOOL bIncludeLink = FALSE,
    LPPOINT lpOffset = NULL,
    LPSIZE lpSize = NULL);
```

### <a name="parameters"></a>Parameter

*pDataSource*<br/>
Zeigen Sie `COleDataSource` mit dem Zeiger auf das Objekt, das die Daten des OLE-Elements in allen unterstützten Formaten empfängt.

*bIncludeLink*<br/>
TRUE, wenn Verknüpfungsdaten in die Zwischenablage kopiert werden sollen. FALSE, wenn Ihre Serveranwendung keine Links unterstützt.

*lpOffset*<br/>
Der Versatz (in Pixel) des Mauszeigers vom Ursprung des Objekts.

*lpSize*<br/>
Die Größe des Objekts in Pixel.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ruft die [GetEmbedSourceData-Memberfunktion](#getembedsourcedata) auf, um die systemeigenen Daten für das OLE-Element abzudateien, und ruft die [AddOtherClipboardData-Memberfunktion](#addotherclipboarddata) auf, um das Präsentationsformat und alle unterstützten Konvertierungsformate abzufragen. Wenn *bIncludeLink* TRUE ist, ruft die Funktion auch [GetLinkSourceData](#getlinksourcedata) auf, um die Verknüpfungsdaten für das Element abzubekommen.

Überschreiben Sie diese Funktion, wenn `COleDataSource` Sie Formate in einem `CopyToClipboard`Objekt vor oder nach den von bereitgestellten Formaten ablegieren möchten.

## <a name="coleserveritemgetdatasource"></a><a name="getdatasource"></a>COleServerItem::GetDataSource

Rufen Sie diese Funktion auf, um das [COleDataSource-Objekt](../../mfc/reference/coledatasource-class.md) abzurufen, das zum Speichern der Konvertierungsformate verwendet wird, die von der Serveranwendung unterstützt werden.

```
COleDataSource* GetDataSource();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `COleDataSource` das Objekt, das zum Speichern der Konvertierungsformate verwendet wird.

### <a name="remarks"></a>Bemerkungen

Wenn Sie möchten, dass Ihre Serveranwendung daten in einer Vielzahl von `COleDataSource` Formaten während der Datenübertragung sbereitet, registrieren Sie diese Formate mit dem von dieser Funktion zurückgegebenen Objekt. Wenn Sie z. B. eine CF_TEXT Darstellung des OLE-Elements für Zwischenablage- oder Drag-and-Drop-Vorgänge bereitstellen möchten, registrieren Sie das Format mit dem Objekt, das `COleDataSource` diese Funktion zurückgibt, und überschreiben dann die `OnRenderXxxData` Memberfunktion, um die Daten bereitzustellen.

## <a name="coleserveritemgetdocument"></a><a name="getdocument"></a>COleServerItem::GetDocument

Rufen Sie diese Funktion auf, um einen Zeiger auf das Dokument abzurufen, das das Element enthält.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Dokument, das das Element enthält; NULL, wenn das Element nicht Teil eines Dokuments ist.

### <a name="remarks"></a>Bemerkungen

Dadurch kann auf das Serverdokument, das Sie `COleServerItem` als Argument an den Konstruktor übergeben haben, zugreifen.

## <a name="coleserveritemgetembedsourcedata"></a><a name="getembedsourcedata"></a>COleServerItem::GetEmbedSourceData

Rufen Sie diese Funktion auf, um die CF_EMBEDSOURCE Daten für ein OLE-Element abzurufen.

```cpp
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parameter

*lpStgMedium*<br/>
Zeiger auf die [STGMEDIUM-Struktur,](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) die die CF_EMBEDSOURCE Daten für das OLE-Element empfängt.

### <a name="remarks"></a>Bemerkungen

Dieses Format enthält die systemeigenen Daten des Elements. Sie müssen die `Serialize` Memberfunktion implementiert haben, damit diese Funktion ordnungsgemäß funktioniert.

Das Ergebnis kann dann mithilfe von [COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata)zu einer Datenquelle hinzugefügt werden. Diese Funktion wird automatisch von [COleServerItem::OnGetClipboardData](#ongetclipboarddata)aufgerufen.

Weitere Informationen finden Sie unter [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) im Windows SDK.

## <a name="coleserveritemgetitemname"></a><a name="getitemname"></a>COleServerItem::GetItemName

Rufen Sie diese Funktion auf, um den Namen des Elements abzurufen.

```
const CString& GetItemName() const;
```

### <a name="return-value"></a>Rückgabewert

Name des Elements.

### <a name="remarks"></a>Bemerkungen

In der Regel rufen Sie diese Funktion nur für verknüpfte Elemente auf.

## <a name="coleserveritemgetlinksourcedata"></a><a name="getlinksourcedata"></a>COleServerItem::GetLinkSourceData

Rufen Sie diese Funktion auf, um die CF_LINKSOURCE Daten für ein OLE-Element abzurufen.

```
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parameter

*lpStgMedium*<br/>
Zeiger auf die [STGMEDIUM-Struktur,](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) die die CF_LINKSOURCE Daten für das OLE-Element empfängt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Dieses Format enthält die CLSID, die den Typ des OLE-Elements beschreibt, sowie die Informationen, die zum Suchen des Dokuments mit dem OLE-Element erforderlich sind.

Das Ergebnis kann dann einer Datenquelle mit [COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata)hinzugefügt werden. Diese Funktion wird automatisch von [OnGetClipboardData](#ongetclipboarddata)aufgerufen.

Weitere Informationen finden Sie unter [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) im Windows SDK.

## <a name="coleserveritemgetobjectdescriptordata"></a><a name="getobjectdescriptordata"></a>COleServerItem::GetObjectDescriptorData

Rufen Sie diese Funktion auf, um die CF_OBJECTDESCRIPTOR Daten für ein OLE-Element abzurufen.

```cpp
void GetObjectDescriptorData(
    LPPOINT lpOffset,
    LPSIZE lpSize,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parameter

*lpOffset*<br/>
Versatz des Mausklicks aus der oberen linken Ecke des OLE-Elements. Kann den Wert NULL haben.

*lpSize*<br/>
Größe des OLE-Elements. Kann den Wert NULL haben.

*lpStgMedium*<br/>
Zeiger auf die [STGMEDIUM-Struktur,](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) die die CF_OBJECTDESCRIPTOR Daten für das OLE-Element empfängt.

### <a name="remarks"></a>Bemerkungen

Die Informationen werden `STGMEDIUM` in die Struktur kopiert, auf die *lpStgMedium*zeigt. Dieses Format enthält die Informationen, die für das Dialogfeld "Spezial einfügen" benötigt werden.

Weitere Informationen finden Sie unter [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) im Windows SDK.

## <a name="coleserveritemisconnected"></a><a name="isconnected"></a>COleServerItem::IsConnected

Rufen Sie diese Funktion auf, um festzustellen, ob das OLE-Element verbunden ist.

```
BOOL IsConnected() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Element verbunden ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Ein OLE-Element gilt als verbunden, wenn ein oder mehrere Container Verweise auf das Element enthalten. Ein Element ist verbunden, wenn seine Referenzanzahl größer als 0 ist oder wenn es sich um ein eingebettetes Element handelt.

## <a name="coleserveritemislinkeditem"></a><a name="islinkeditem"></a>COleServerItem::IsLinkedItem

Rufen Sie diese Funktion auf, um festzustellen, ob es sich bei dem OLE-Element um ein verknüpftes Element handelt.

```
BOOL IsLinkedItem() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn es sich bei dem Artikel um ein verknüpftes Element handelt; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Ein Element wird verknüpft, wenn das Element gültig ist, und wird nicht in der Liste der eingebetteten Elemente des Dokuments zurückgegeben. Ein verknüpftes Element ist möglicherweise nicht mit einem Container verbunden.

Es ist üblich, dieselbe Klasse für verknüpfte und eingebettete Elemente zu verwenden. `IsLinkedItem`ermöglicht es Ihnen, verknüpfte Elemente anders zu verhalten als eingebettete Elemente, obwohl der Code häufig vorkommt.

## <a name="coleserveritemm_sizeextent"></a><a name="m_sizeextent"></a>COleServerItem::m_sizeExtent

Dieses Element teilt dem Server mit, wie viel des Objekts im Containerdokument sichtbar ist.

```
CSize m_sizeExtent;
```

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung von [OnSetExtent](#onsetextent) legt diesen Member fest.

## <a name="coleserveritemnotifychanged"></a><a name="notifychanged"></a>COleServerItem::NotifyChanged

Rufen Sie diese Funktion auf, nachdem das verknüpfte Element geändert wurde.

```cpp
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>Parameter

*nDrawAspect*<br/>
Ein Wert aus der DVASPECT-Enumeration, der angibt, welcher Aspekt des OLE-Elements geändert wurde. Dieser Parameter kann einen der folgenden Werte aufweisen:

- DVASPECT_CONTENT-Element wird so dargestellt, dass es als eingebettetes Objekt in seinem Container angezeigt werden kann.

- DVASPECT_THUMBNAIL Element wird in einer "Miniaturansicht"-Darstellung gerendert, sodass es in einem Browsertool angezeigt werden kann.

- DVASPECT_ICON Element wird durch ein Symbol dargestellt.

- DVASPECT_DOCPRINT-Element wird dargestellt, als ob es mit dem Befehl Drucken aus dem Menü Datei gedruckt würde.

### <a name="remarks"></a>Bemerkungen

Wenn ein Containerelement mit dem Dokument mit einer automatischen Verknüpfung verknüpft ist, wird das Element aktualisiert, um die Änderungen widerzuspiegeln. In Containeranwendungen, die mit der Microsoft Foundation-Klassenbibliothek geschrieben wurden, wird [COleClientItem::OnChange](../../mfc/reference/coleclientitem-class.md#onchange) als Antwort aufgerufen.

## <a name="coleserveritemondoverb"></a><a name="ondoverb"></a>COleServerItem::OnDoverb

Wird vom Framework aufgerufen, um das angegebene Verb auszuführen.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>Parameter

*iVerb*<br/>
Gibt das auszuführende Verb an. Es kann eine der folgenden sein:

|Wert|Bedeutung|Symbol|
|-----------|-------------|------------|
|0|Primäres Verb|OLEIVERB_PRIMARY|
|1|Sekundäres Verb|(Keine)|
|- 1|Element zur Bearbeitung anzeigen|OLEIVERB_SHOW|
|- 2|Bearbeiten des Elements in einem separaten Fenster|OLEIVERB_OPEN|
|- 3|Ausblenden von Gegenständen|OLEIVERB_HIDE|

Der -1-Wert ist in der Regel ein Alias für ein anderes Verb. Wenn die offene Bearbeitung nicht unterstützt wird, hat -2 den gleichen Effekt wie -1. Weitere Werte finden Sie unter [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) im Windows SDK.

### <a name="remarks"></a>Bemerkungen

Wenn die Containeranwendung mit der Microsoft Foundation-Klassenbibliothek geschrieben wurde, wird diese Funktion aufgerufen, `COleClientItem` wenn die [COleClientItem::Activate-Memberfunktion](../../mfc/reference/coleclientitem-class.md#activate) des entsprechenden Objekts aufgerufen wird. Die Standardimplementierung ruft die [OnShow-Memberfunktion](#onshow) auf, wenn das primäre Verb oder OLEIVERB_SHOW angegeben ist, [OnOpen,](#onopen) wenn das sekundäre Verb oder OLEIVERB_OPEN angegeben ist, und [OnHide,](#onhide) wenn OLEIVERB_HIDE angegeben ist. Die Standardimplementierung `OnShow` ruft auf, wenn *iVerb* nicht eines der oben aufgeführten Verben ist.

Überschreiben Sie diese Funktion, wenn das primäre Verb das Element nicht anzeigt. Wenn es sich bei dem Element beispielsweise um eine Tonaufnahme handelt und sein primäres Verb Play lautet, müssen Sie die Serveranwendung nicht anzeigen, um das Element wiederzugeben.

Weitere Informationen finden Sie unter [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) im Windows SDK.

## <a name="coleserveritemondraw"></a><a name="ondraw"></a>COleServerItem::OnDraw

Wird vom Framework aufgerufen, um das OLE-Element in eine Metadatei zu rendern.

```
virtual BOOL OnDraw(
    CDC* pDC,
    CSize& rSize) = 0;
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Ein Zeiger auf [CDC](../../mfc/reference/cdc-class.md) das CDC-Objekt, auf das das Element gezeichnet werden soll. Der Anzeigekontext wird automatisch mit dem Attributanzeigekontext verbunden, sodass Sie Attributfunktionen aufrufen können, obwohl dies die Metadatei gerätespezifisch machen würde.

*rSize*<br/>
Größe, in HIMETRIC-Einheiten, in denen die Metadatei gezeichnet werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Element erfolgreich gezeichnet wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Metadateidarstellung des OLE-Elements wird verwendet, um das Element in der Containeranwendung anzuzeigen. Wenn die Containeranwendung mit der Microsoft Foundation-Klassenbibliothek geschrieben [Draw](../../mfc/reference/coleclientitem-class.md#draw) wurde, wird die Metadatei von der Draw-Memberfunktion des entsprechenden [COleClientItem-Objekts](../../mfc/reference/coleclientitem-class.md) verwendet. Es ist keine Standardimplementierung vorhanden. Sie müssen diese Funktion überschreiben, um das Element in den angegebenen Gerätekontext zu zeichnen.

## <a name="coleserveritemondrawex"></a><a name="ondrawex"></a>COleServerItem::OnDrawex

Wird vom Framework für alle Zeichnungen aufgerufen.

```
virtual BOOL OnDrawEx(
    CDC* pDC,
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Ein Zeiger auf [CDC](../../mfc/reference/cdc-class.md) das CDC-Objekt, auf das das Element gezeichnet werden soll. Der DC wird automatisch mit dem Attribut DC verbunden, sodass Sie Attributfunktionen aufrufen können, obwohl dies die Metadatei gerätespezifisch machen würde.

*nDrawAspect*<br/>
Ein Wert aus der DVASPECT-Enumeration. Dieser Parameter kann einen der folgenden Werte aufweisen:

- DVASPECT_CONTENT-Element wird so dargestellt, dass es als eingebettetes Objekt in seinem Container angezeigt werden kann.

- DVASPECT_THUMBNAIL Element wird in einer "Miniaturansicht"-Darstellung gerendert, sodass es in einem Browsertool angezeigt werden kann.

- DVASPECT_ICON Element wird durch ein Symbol dargestellt.

- DVASPECT_DOCPRINT-Element wird dargestellt, als ob es mit dem Befehl Drucken aus dem Menü Datei gedruckt würde.

*rSize*<br/>
Größe des Artikels in HIMETRIC-Einheiten.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Element erfolgreich gezeichnet wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung `OnDraw` wird aufgerufen, wenn DVASPECT gleich DVASPECT_CONTENT ist. andernfalls schlägt es fehl.

Überschreiben Sie diese Funktion, um Präsentationsdaten für andere Aspekte als DVASPECT_CONTENT bereitzustellen, z. B. DVASPECT_ICON oder DVASPECT_THUMBNAIL.

## <a name="coleserveritemongetclipboarddata"></a><a name="ongetclipboarddata"></a>COleServerItem::OnGetClipboardData

Wird vom Framework aufgerufen, um ein `COleDataSource` Objekt abzurufen, das alle Daten enthält, die durch einen Aufruf der [CopyToClipboard-Memberfunktion](#copytoclipboard) in der Zwischenablage platziert würden.

```
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,
    LPPOINT lpOffset,
    LPSIZE lpSize);
```

### <a name="parameters"></a>Parameter

*bIncludeLink*<br/>
Legen Sie diesen Wert auf TRUE fest, wenn Verknüpfungsdaten in die Zwischenablage kopiert werden sollen. Legen Sie diesen Satz auf FALSE fest, wenn Ihre Serveranwendung keine Links unterstützt.

*lpOffset*<br/>
Der Versatz des Mauszeigers vom Ursprung des Objekts in Pixeln.

*lpSize*<br/>
Die Größe des Objekts in Pixel.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [COleDataSource-Objekt,](../../mfc/reference/coledatasource-class.md) das die Zwischenablagedaten enthält.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung dieser Funktion ruft [GetClipboardData](#getclipboarddata)auf.

## <a name="coleserveritemongetextent"></a><a name="ongetextent"></a>COleServerItem::OnGetExtent

Wird vom Framework aufgerufen, um die Größe des OLE-Elements in HIMETRIC-Einheiten abzurufen.

```
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Parameter

*nDrawAspect*<br/>
Gibt den Aspekt des OLE-Elements an, dessen Grenzen abgerufen werden sollen. Dieser Parameter kann einen der folgenden Werte aufweisen:

- DVASPECT_CONTENT-Element wird so dargestellt, dass es als eingebettetes Objekt in seinem Container angezeigt werden kann.

- DVASPECT_THUMBNAIL Element wird in einer "Miniaturansicht"-Darstellung gerendert, sodass es in einem Browsertool angezeigt werden kann.

- DVASPECT_ICON Element wird durch ein Symbol dargestellt.

- DVASPECT_DOCPRINT-Element wird dargestellt, als ob es mit dem Befehl Drucken aus dem Menü Datei gedruckt würde.

*rSize*<br/>
Verweis auf `CSize` ein Objekt, das die Größe des OLE-Elements erhält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Wenn die Containeranwendung mit der Microsoft Foundation-Klassenbibliothek geschrieben wurde, wird diese `COleClientItem` Funktion aufgerufen, wenn die [GetExtent-Memberfunktion](../../mfc/reference/coleclientitem-class.md#getextent) des entsprechenden Objekts aufgerufen wird. Bei der Standardimplementierung wird keine Aktion ausgeführt. Sie müssen es selbst implementieren. Überschreiben Sie diese Funktion, wenn Sie eine spezielle Verarbeitung durchführen möchten, wenn Sie eine Anforderung für die Größe des OLE-Elements verarbeiten.

## <a name="coleserveritemonhide"></a><a name="onhide"></a>COleServerItem::OnHide

Wird vom Framework aufgerufen, um das OLE-Element auszublenden.

```
virtual void OnHide();
```

### <a name="remarks"></a>Bemerkungen

Die Standardaufrufe `COleServerDoc::OnShowDocument( FALSE )`. Die Funktion benachrichtigt den Container auch darüber, dass das OLE-Element ausgeblendet wurde. Überschreiben Sie diese Funktion, wenn Sie beim Ausblenden eines OLE-Elements eine spezielle Verarbeitung durchführen möchten.

## <a name="coleserveritemoninitfromdata"></a><a name="oninitfromdata"></a>COleServerItem::OnInitFromData

Wird vom Framework aufgerufen, um ein OLE-Element mit dem Inhalt von *pDataObject*zu initialisieren.

```
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,
    BOOL bCreation);
```

### <a name="parameters"></a>Parameter

*pDataObject*<br/>
Zeiger auf ein OLE-Datenobjekt, das Daten in verschiedenen Formaten zum Initialisieren des OLE-Elements enthält.

*bCreation*<br/>
TRUE, wenn die Funktion aufgerufen wird, um ein OLE-Element zu initialisieren, das von einer Containeranwendung neu erstellt wird. FALSE, wenn die Funktion aufgerufen wird, um den Inhalt eines bereits vorhandenen OLE-Elements zu ersetzen.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Wenn *bCreation* TRUE ist, wird diese Funktion aufgerufen, wenn ein Container Insert New Object basierend auf der aktuellen Auswahl implementiert. Die ausgewählten Daten werden beim Erstellen des neuen OLE-Elements verwendet. Wenn Sie z. B. einen Zellbereich in einem Tabellenkalkulationsprogramm auswählen und dann das Neue Objekt einfügen verwenden, um ein Diagramm basierend auf den Werten im ausgewählten Bereich zu erstellen. Bei der Standardimplementierung wird keine Aktion ausgeführt. Überschreiben Sie diese Funktion, um ein akzeptables Format aus dem von *pDataObject* angebotenen Format auszuwählen, und initialisieren Sie das OLE-Element basierend auf den bereitgestellten Daten. Dies ist ein fortgeschrittenes Überridable.

Weitere Informationen finden Sie unter [IOleObject::InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) im Windows SDK.

## <a name="coleserveritemonopen"></a><a name="onopen"></a>COleServerItem::OnOpen

Wird vom Framework aufgerufen, um das OLE-Element in einer separaten Instanz der Serveranwendung anzuzeigen und nicht in Der Ort.

```
virtual void OnOpen();
```

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung aktiviert das erste Rahmenfenster, in dem das Dokument angezeigt wird, das das OLE-Element enthält. Wenn es sich bei der Anwendung um einen Miniserver handelt, zeigt die Standardimplementierung das Hauptfenster an. Die Funktion benachrichtigt den Container auch darüber, dass das OLE-Element geöffnet wurde.

Überschreiben Sie diese Funktion, wenn Sie beim Öffnen eines OLE-Elements eine spezielle Verarbeitung durchführen möchten. Dies ist besonders häufig bei verknüpften Elementen der Letzter, bei denen Sie die Auswahl beim Öffnen auf den Link festlegen möchten.

Weitere Informationen finden Sie unter [IOleClientSite::OnShowWindow](/windows/win32/api/oleidl/nf-oleidl-ioleclientsite-onshowwindow) im Windows SDK.

## <a name="coleserveritemonqueryupdateitems"></a><a name="onqueryupdateitems"></a>COleServerItem::OnQueryUpdateItems

Wird vom Framework aufgerufen, um zu bestimmen, ob verknüpfte Elemente im aktuellen Serverdokument veraltet sind.

```
virtual BOOL OnQueryUpdateItems();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Dokument Überelemente enthält, die aktualisiert werden müssen; 0, wenn alle Artikel auf dem neuesten Stand sind.

### <a name="remarks"></a>Bemerkungen

Ein Element ist veraltet, wenn das Quelldokument geändert wurde, aber das verknüpfte Element nicht aktualisiert wurde, um die Änderungen im Dokument widerzuspiegeln.

## <a name="coleserveritemonrenderdata"></a><a name="onrenderdata"></a>COleServerItem::OnRenderdata

Wird vom Framework aufgerufen, um Daten im angegebenen Format abzurufen.

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parameter

*lpFormatEtc*<br/>
Verweist auf die [FORMATETC-Struktur,](/windows/win32/api/objidl/ns-objidl-formatetc) die das Format angibt, in dem Informationen angefordert werden.

*lpStgMedium*<br/>
Zeigt auf eine [STGMEDIUM-Struktur,](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) in der die Daten zurückgegeben werden sollen.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Das angegebene Format ist ein `COleDataSource` formatiertes, das zuvor mit der [Memberfunktion DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) oder [DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata) für verzögertes Rendern im Objekt platziert wurde. Die Standardimplementierung dieser Funktion ruft [OnRenderFileData](#onrenderfiledata) bzw. [OnRenderGlobalData](#onrenderglobaldata)auf, wenn das angegebene Speichermedium entweder eine Datei oder einen Speicher ist. Wenn keines dieser Formate angegeben wird, gibt die Standardimplementierung 0 zurück und führt nichts aus.

Wenn *lpStgMedium*-> *tymed* TYMED_NULL ist, sollte der STGMEDIUM gemäß *lpFormatEtc->tymed*zugeordnet und gefüllt werden. Wenn nicht TYMED_NULL, sollte der STGMEDIUM mit den Daten ausgefüllt werden.

Dies ist ein fortgeschrittenes Überridable. Überschreiben Sie diese Funktion, um Ihre Daten im angeforderten Format und Medium bereitzustellen. Abhängig von Ihren Daten können Sie stattdessen eine der anderen Versionen dieser Funktion überschreiben. Wenn Ihre Daten klein und fest `OnRenderGlobalData`formatiert sind, überschreiben Sie . Wenn sich Ihre Daten in einer Datei befinden `OnRenderFileData`oder eine variable Größe haben, überschreiben Sie .

Weitere Informationen finden Sie unter [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1), [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)und [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) im Windows SDK.

## <a name="coleserveritemonrenderfiledata"></a><a name="onrenderfiledata"></a>COleServerItem::OnRenderFileData

Wird vom Framework aufgerufen, um Daten im angegebenen Format abzurufen, wenn es sich bei dem Speichermedium um eine Datei handelt.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Parameter

*lpFormatEtc*<br/>
Verweist auf die [FORMATETC-Struktur,](/windows/win32/api/objidl/ns-objidl-formatetc) die das Format angibt, in dem Informationen angefordert werden.

*pFile*<br/>
Zeigt auf `CFile` ein Objekt, in dem die Daten gerendert werden sollen.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Das angegebene Format ist ein `COleDataSource` Format, das zuvor im Objekt platziert wurde, indem die [DelayRenderData-Memberfunktion](../../mfc/reference/coledatasource-class.md#delayrenderdata) für verzögertes Rendern verwendet wird. Die Standardimplementierung dieser Funktion gibt einfach FALSE zurück.

Dies ist ein fortgeschrittenes Überridable. Überschreiben Sie diese Funktion, um Ihre Daten im angeforderten Format und Medium bereitzustellen. Je nach Daten können Sie stattdessen eine der anderen Versionen dieser Funktion überschreiben. Wenn Sie mehrere Speichermedien verarbeiten möchten, überschreiben Sie [OnRenderData](#onrenderdata). Wenn sich Ihre Daten in einer Datei befinden oder variable Größe haben, überschreiben Sie [OnRenderFileData](#onrenderfiledata).

Weitere Informationen finden Sie unter [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) und [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) im Windows SDK.

## <a name="coleserveritemonrenderglobaldata"></a><a name="onrenderglobaldata"></a>COleServerItem::OnRenderGlobalData

Wird vom Framework aufgerufen, um Daten im angegebenen Format abzurufen, wenn das angegebene Speichermedium globaler Speicher ist.

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>Parameter

*lpFormatEtc*<br/>
Verweist auf die [FORMATETC-Struktur,](/windows/win32/api/objidl/ns-objidl-formatetc) die das Format angibt, in dem Informationen angefordert werden.

*phGlobal*<br/>
Verweist auf ein Handle im globalen Speicher, in dem die Daten zurückgegeben werden sollen. Wenn kein Speicher reserviert wurde, kann dieser Parameter NULL sein.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Das angegebene Format ist ein `COleDataSource` Format, das zuvor im Objekt platziert wurde, indem die [DelayRenderData-Memberfunktion](../../mfc/reference/coledatasource-class.md#delayrenderdata) für verzögertes Rendern verwendet wird. Die Standardimplementierung dieser Funktion gibt einfach FALSE zurück.

Wenn *phGlobal* NULL ist, sollte ein neuer HGLOBAL zugewiesen und in *phGlobal*zurückgegeben werden. Andernfalls sollte der von *phGlobal* angegebene HGLOBAL mit den Daten gefüllt werden. Die im HGLOBAL platzierte Datenmenge darf die aktuelle Größe des Speicherblocks nicht überschreiten. Außerdem kann der Block nicht auf eine größere Größe umverteilt werden.

Dies ist ein fortgeschrittenes Überridable. Überschreiben Sie diese Funktion, um Ihre Daten im angeforderten Format und Medium bereitzustellen. Abhängig von Ihren Daten können Sie stattdessen eine der anderen Versionen dieser Funktion überschreiben. Wenn Sie mehrere Speichermedien verarbeiten möchten, überschreiben Sie [OnRenderData](#onrenderdata). Wenn sich Ihre Daten in einer Datei befinden oder variable Größe haben, überschreiben Sie [OnRenderFileData](#onrenderfiledata).

Weitere Informationen finden Sie unter [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) und [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) im Windows SDK.

## <a name="coleserveritemonsetcolorscheme"></a><a name="onsetcolorscheme"></a>COleServerItem::OnSetColorScheme

Wird vom Framework aufgerufen, um eine Farbpalette anzugeben, die beim Bearbeiten des OLE-Elements verwendet werden soll.

```
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```

### <a name="parameters"></a>Parameter

*lpLogPalette*<br/>
Zeiger auf eine Windows [LOGPALETTE-Struktur.](/windows/win32/api/wingdi/ns-wingdi-logpalette)

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Farbpalette verwendet wird; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn die Containeranwendung mit der Microsoft Foundation-Klassenbibliothek geschrieben wurde, wird diese Funktion aufgerufen, `COleClientItem` wenn die [IOleObject::SetColorScheme-Funktion](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) des entsprechenden Objekts aufgerufen wird. Die Standardimplementierung gibt FALSE zurück. Überschreiben Sie diese Funktion, wenn Sie die empfohlene Palette verwenden möchten. Die Serveranwendung ist nicht erforderlich, um die vorgeschlagene Palette zu verwenden.

Weitere Informationen finden Sie unter [IOleObject::SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) im Windows SDK.

## <a name="coleserveritemonsetdata"></a><a name="onsetdata"></a>COleServerItem::OnSetdata

Wird vom Framework aufgerufen, um die Daten des OLE-Elements durch die angegebenen Daten zu ersetzen.

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>Parameter

*lpFormatEtc*<br/>
Zeiger auf eine [FORMATETC-Struktur,](/windows/win32/api/objidl/ns-objidl-formatetc) die das Format der Daten angibt.

*lpStgMedium*<br/>
Zeiger auf eine [STGMEDIUM-Struktur,](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) in der sich die Daten befinden.

*bRelease*<br/>
Gibt an, wer nach Abschluss des Funktionsaufrufs eigentümer das Speichermedium ist. Der Aufrufer entscheidet, wer für die Freigabe der im Auftrag des Speichermediums zugewiesenen Ressourcen zuständig ist. Der Aufrufer tut dies, indem er *bRelease*setzt. Wenn *bRelease* ungleich Null ist, übernimmt das Serverelement den Besitz und gibt das Medium frei, wenn es die Verwendung beendet hat. Wenn *bRelease* 0 ist, behält der Aufrufer den Besitz, und das Serverelement kann das Speichermedium nur für die Dauer des Anrufs verwenden.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Das Serverelement übernimmt erst dann den Besitz der Daten, wenn es erfolgreich abgerufen wurde. Das heißt, es übernimmt nicht die Verantwortung, wenn es 0 zurückgibt. Wenn die Datenquelle den Besitz übernimmt, wird das Speichermedium durch Aufrufen der [ReleaseStgMedium-Funktion](/windows/win32/api/ole2/nf-ole2-releasestgmedium) freigegeben.

Bei der Standardimplementierung wird keine Aktion ausgeführt. Überschreiben Sie diese Funktion, um die Daten des OLE-Elements durch die angegebenen Daten zu ersetzen. Dies ist ein fortgeschrittenes Überridable.

Weitere Informationen finden Sie unter [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1), [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)und [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) im Windows SDK.

## <a name="coleserveritemonsetextent"></a><a name="onsetextent"></a>COleServerItem::OnSetExtent

Wird vom Framework aufgerufen, um dem OLE-Element mitzuteilen, wie viel Speicherplatz im Containerdokument zur Verfügung steht.

```
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,
    const CSize& size);
```

### <a name="parameters"></a>Parameter

*nDrawAspect*<br/>
Gibt den Aspekt des OLE-Elements an, dessen Grenzen angegeben werden. Dieser Parameter kann einen der folgenden Werte aufweisen:

- DVASPECT_CONTENT-Element wird so dargestellt, dass es als eingebettetes Objekt in seinem Container angezeigt werden kann.

- DVASPECT_THUMBNAIL Element wird in einer "Miniaturansicht"-Darstellung gerendert, sodass es in einem Browsertool angezeigt werden kann.

- DVASPECT_ICON Element wird durch ein Symbol dargestellt.

- DVASPECT_DOCPRINT-Element wird dargestellt, als ob es mit dem Befehl Drucken aus dem Menü Datei gedruckt würde.

*size*<br/>
Eine [CSize-Struktur,](../../atl-mfc-shared/reference/csize-class.md) die die neue Größe des OLE-Elements angibt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Wenn die Containeranwendung mit der Microsoft Foundation-Klassenbibliothek geschrieben wurde, wird diese `COleClientItem` Funktion aufgerufen, wenn die [SetExtent-Memberfunktion](../../mfc/reference/coleclientitem-class.md#setextent) des entsprechenden Objekts aufgerufen wird. Die Standardimplementierung legt den [m_sizeExtent-Member](#m_sizeextent) auf die angegebene Größe fest, wenn *nDrawAspect* DVASPECT_CONTENT ist. Andernfalls wird 0 zurückgegeben. Überschreiben Sie diese Funktion, um eine spezielle Verarbeitung durchzuführen, wenn Sie die Größe des Elements ändern.

## <a name="coleserveritemonshow"></a><a name="onshow"></a>COleServerItem::OnShow

Wird vom Framework aufgerufen, um die Serveranwendung anzuweisen, das OLE-Element an Ort und Stelle anzuzeigen.

```
virtual void OnShow();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird in der Regel aufgerufen, wenn der Benutzer der Containeranwendung ein Element erstellt oder ein Verb ausführt, z. B. Bearbeiten, für das das Element angezeigt werden muss. Die Standardimplementierung versucht die an Ort und Stelle zu aktivieren. Wenn dies fehlschlägt, `OnOpen` ruft die Funktion die Memberfunktion auf, um das OLE-Element in einem separaten Fenster anzuzeigen.

Überschreiben Sie diese Funktion, wenn Sie eine spezielle Verarbeitung durchführen möchten, wenn ein OLE-Element angezeigt wird.

## <a name="coleserveritemonupdate"></a><a name="onupdate"></a>COleServerItem::OnUpdate

Wird vom Framework aufgerufen, wenn ein Element geändert wurde.

```
virtual void OnUpdate(
    COleServerItem* pSender,
    LPARAM lHint,
    CObject* pHint,
    DVASPECT nDrawAspect);
```

### <a name="parameters"></a>Parameter

*pSender*<br/>
Zeigen Sie auf das Element, das das Dokument geändert hat. Kann den Wert NULL haben.

*lHint*<br/>
Enthält Informationen zur Änderung.

*pHint*<br/>
Zeiger auf ein Objekt, das Informationen über die Änderung speichert.

*nDrawAspect*<br/>
Ein Wert aus der DVASPECT-Enumeration. Dieser Parameter kann einen der folgenden Werte aufweisen:

- DVASPECT_CONTENT-Element wird so dargestellt, dass es als eingebettetes Objekt in seinem Container angezeigt werden kann.

- DVASPECT_THUMBNAIL Element wird in einer "Miniaturansicht"-Darstellung gerendert, sodass es in einem Browsertool angezeigt werden kann.

- DVASPECT_ICON Element wird durch ein Symbol dargestellt.

- DVASPECT_DOCPRINT-Element wird dargestellt, als ob es mit dem Befehl Drucken aus dem Menü Datei gedruckt würde.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung ruft [NotifyChanged](#notifychanged)auf, unabhängig vom Hinweis oder Absender.

## <a name="coleserveritemonupdateitems"></a><a name="onupdateitems"></a>COleServerItem::OnUpdateItems

Wird vom Framework aufgerufen, um alle Elemente im Serverdokument zu aktualisieren.

```
virtual void OnUpdateItems();
```

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung ruft [UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink) für alle `COleClientItem` Objekte im Dokument auf.

## <a name="coleserveritemsetitemname"></a><a name="setitemname"></a>COleServerItem::SetItemName

Rufen Sie diese Funktion auf, wenn Sie ein verknüpftes Element erstellen, um dessen Namen festzulegen.

```cpp
void SetItemName(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Parameter

*lpszItemName*<br/>
Zeigen Sie auf den neuen Namen des Elements.

### <a name="remarks"></a>Bemerkungen

Der Name muss innerhalb des Dokuments eindeutig sein. Wenn eine Serveranwendung aufgerufen wird, um ein verknüpftes Element zu bearbeiten, verwendet die Anwendung diesen Namen, um das Element zu finden. Sie müssen diese Funktion für eingebettete Elemente nicht aufrufen.

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CDocItem-Klasse](../../mfc/reference/cdocitem-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem-Klasse](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerDoc-Klasse](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleTemplateServer-Klasse](../../mfc/reference/coletemplateserver-class.md)
