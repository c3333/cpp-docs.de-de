---
title: COleDataSource-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleDataSource
- AFXOLE/COleDataSource
- AFXOLE/COleDataSource::COleDataSource
- AFXOLE/COleDataSource::CacheData
- AFXOLE/COleDataSource::CacheGlobalData
- AFXOLE/COleDataSource::DelayRenderData
- AFXOLE/COleDataSource::DelayRenderFileData
- AFXOLE/COleDataSource::DelaySetData
- AFXOLE/COleDataSource::DoDragDrop
- AFXOLE/COleDataSource::Empty
- AFXOLE/COleDataSource::FlushClipboard
- AFXOLE/COleDataSource::GetClipboardOwner
- AFXOLE/COleDataSource::OnRenderData
- AFXOLE/COleDataSource::OnRenderFileData
- AFXOLE/COleDataSource::OnRenderGlobalData
- AFXOLE/COleDataSource::OnSetData
- AFXOLE/COleDataSource::SetClipboard
helpviewer_keywords:
- COleDataSource [MFC], COleDataSource
- COleDataSource [MFC], CacheData
- COleDataSource [MFC], CacheGlobalData
- COleDataSource [MFC], DelayRenderData
- COleDataSource [MFC], DelayRenderFileData
- COleDataSource [MFC], DelaySetData
- COleDataSource [MFC], DoDragDrop
- COleDataSource [MFC], Empty
- COleDataSource [MFC], FlushClipboard
- COleDataSource [MFC], GetClipboardOwner
- COleDataSource [MFC], OnRenderData
- COleDataSource [MFC], OnRenderFileData
- COleDataSource [MFC], OnRenderGlobalData
- COleDataSource [MFC], OnSetData
- COleDataSource [MFC], SetClipboard
ms.assetid: 02c8ee7d-8e10-4463-8613-bb2a0305ca69
ms.openlocfilehash: 5cd573590bc1adb303e0b4c5cd600b9fa6c685b2
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855750"
---
# <a name="coledatasource-class"></a>COleDataSource-Klasse

Dient als Cache, in den eine Anwendung die Daten für Datenübertragungsoperationen ablegt, beispielsweise bei Zwischenablage- oder Drag & Drop-Operationen.

## <a name="syntax"></a>Syntax

```
class COleDataSource : public CCmdTarget
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDataSource:: COleDataSource](#coledatasource)|Erstellt ein `COleDataSource`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDataSource:: CacheData](#cachedata)|Bietet Daten in einem angegebenen Format unter Verwendung einer `STGMEDIUM` Struktur.|
|[COleDataSource:: CacheGlobalData](#cacheglobaldata)|Bietet Daten in einem angegebenen Format mithilfe eines HGLOBAL.|
|[COleDataSource::D elayrenderdata](#delayrenderdata)|Bietet Daten in einem angegebenen Format mithilfe eines verzögerten Renderings.|
|[COleDataSource::D elayrenderfiledata](#delayrenderfiledata)|Bietet Daten in einem angegebenen Format in einem `CFile`-Zeiger.|
|[COleDataSource::D elaysetdata](#delaysetdata)|Wird für jedes Format aufgerufen, das in `OnSetData`unterstützt wird.|
|[COleDataSource::D odragdrop](#dodragdrop)|Führt Drag & amp; Drop-Vorgänge mit einer Datenquelle aus.|
|[COleDataSource:: Empty](#empty)|Leert das `COleDataSource` Objekt der Daten.|
|[COleDataSource:: flushclipboard](#flushclipboard)|Rendert alle Daten in der Zwischenablage.|
|[COleDataSource:: getclipboardowner](#getclipboardowner)|Überprüft, ob die in der Zwischenablage platzierten Daten weiterhin vorhanden sind.|
|[COleDataSource:: OnRenderData](#onrenderdata)|Ruft Daten im Rahmen des verzögerten Renderings ab.|
|[COleDataSource:: onrenderfiledata](#onrenderfiledata)|Ruft Daten im Rahmen des verzögerten Renderings in eine `CFile` ab.|
|[COleDataSource:: onrenderglobaldata](#onrenderglobaldata)|Ruft Daten im Rahmen des verzögerten Renderings in einen HGLOBAL ab.|
|[COleDataSource:: onsetdata](#onsetdata)|Wird aufgerufen, um die Daten im `COleDataSource` Objekt zu ersetzen.|
|[COleDataSource:: setClipboard](#setclipboard)|Fügt ein `COleDataSource` Objekt in der Zwischenablage ein.|

## <a name="remarks"></a>Bemerkungen

OLE-Datenquellen können direkt erstellt werden. Alternativ erstellen die Klassen [COleClientItem](../../mfc/reference/coleclientitem-class.md) und [COleServerItem](../../mfc/reference/coleserveritem-class.md) OLE-Datenquellen als Reaktion auf Ihre `CopyToClipboard`-und `DoDragDrop` Member-Funktionen. Eine kurze Beschreibung finden Sie unter [COleServerItem:: CopyTo Clipboard](../../mfc/reference/coleserveritem-class.md#copytoclipboard) . Überschreiben Sie die `OnGetClipboardData` Member-Funktion des Client Elements oder der Server Element Klasse, um den Daten in der OLE-Datenquelle, die für die `CopyToClipboard`-oder `DoDragDrop` Member-Funktion erstellt wurde, zusätzliche Zwischenablage Formate hinzuzufügen

Wenn Sie Daten für eine Übertragung vorbereiten möchten, sollten Sie ein Objekt dieser Klasse erstellen und mit Ihren Daten auffüllen, indem Sie die am besten geeignete Methode für Ihre Daten verwenden. Die Art und Weise, wie Sie in eine Datenquelle eingefügt wird, hängt direkt davon ab, ob die Daten sofort (sofortiges Rendering) oder Bedarfs gesteuert (verzögertes Rendering) bereitgestellt werden. Rufen Sie für jedes Zwischenablage Format, in dem Sie Daten bereitstellen, indem Sie das zu verwendende Zwischenablage Format (und eine optionale [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur) an, " [Delta Data](#delayrenderdata)".

Weitere Informationen zu Datenquellen und zur Datenübertragung finden Sie im Artikel [Datenobjekte und Datenquellen (OLE)](../../mfc/data-objects-and-data-sources-ole.md). Außerdem wird im Artikel [Zwischenablage Themen](../../mfc/clipboard.md) der OLE-Zwischenablage Mechanismus beschrieben.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDataSource`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Afxole. h

##  <a name="cachedata"></a>COleDataSource:: CacheData

Mit dieser Funktion können Sie ein Format angeben, in dem Daten während der Datenübertragungs Vorgänge angeboten werden.

```
void CacheData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parameter

*cfFormat*<br/>
Das Zwischenablage Format, in dem die Daten angeboten werden sollen. Dieser Parameter kann eines der vordefinierten Zwischenablage Formate oder der Wert sein, der von der systemeigenen Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) -Funktion zurückgegeben wird.

*lpstgmedium*<br/>
Verweist auf eine [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) -Struktur, die die Daten im angegebenen Format enthält.

*lpformatusw.*<br/>
Verweist auf eine [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur, die das Format beschreibt, in dem die Daten angeboten werden sollen. Geben Sie einen Wert für diesen Parameter an, wenn Sie zusätzliche Formatierungsinformationen angeben möchten, die über das in *cfFormat*angegebene Zwischenablage Format hinausgehen. Wenn er NULL ist, werden für die anderen Felder in der `FORMATETC` Struktur Standardwerte verwendet.

### <a name="remarks"></a>Bemerkungen

Sie müssen die Daten bereitstellen, da diese Funktion Sie mithilfe von sofortigem Rendering bereitstellt. Die Daten werden bis zum benötigten Cache zwischengespeichert.

Stellen Sie die Daten mithilfe einer [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) -Struktur bereit. Sie können auch die `CacheGlobalData` Member-Funktion verwenden, wenn die Menge der von Ihnen bereitgestellten Daten klein genug ist, um mithilfe eines HGLOBAL effizient übertragen zu werden.

Nach dem Aufruf von `CacheData` die `ptd` Member von `lpFormatEtc` und der Inhalt von *lpstgmedium* im Besitz des Datenobjekts, nicht des Aufrufers.

Um das verzögerte Rendering zu verwenden, müssen Sie die Member-Funktion von " [Delta Data](#delayrenderdata) " oder " [Delta Data](#delayrenderfiledata) " verwenden. Weitere Informationen zum verzögerten Rendering, wie von MFC verarbeitet, finden Sie im Artikel [Datenobjekte und Datenquellen: Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Weitere Informationen finden Sie in den Strukturen " [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) " und " [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) " in der Windows SDK.

Weitere Informationen finden Sie unter [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) im Windows SDK.

##  <a name="cacheglobaldata"></a>COleDataSource:: CacheGlobalData

Mit dieser Funktion können Sie ein Format angeben, in dem Daten während der Datenübertragungs Vorgänge angeboten werden.

```
void CacheGlobalData(
    CLIPFORMAT cfFormat,
    HGLOBAL hGlobal,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parameter

*cfFormat*<br/>
Das Zwischenablage Format, in dem die Daten angeboten werden sollen. Dieser Parameter kann eines der vordefinierten Zwischenablage Formate oder der Wert sein, der von der systemeigenen Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) -Funktion zurückgegeben wird.

*hGlobal*<br/>
Handle für den globalen Speicherblock, der die Daten im angegebenen Format enthält.

*lpformatusw.*<br/>
Verweist auf eine [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur, die das Format beschreibt, in dem die Daten angeboten werden sollen. Geben Sie einen Wert für diesen Parameter an, wenn Sie zusätzliche Formatierungsinformationen angeben möchten, die über das in *cfFormat*angegebene Zwischenablage Format hinausgehen. Wenn er NULL ist, werden für die anderen Felder in der `FORMATETC` Struktur Standardwerte verwendet.

### <a name="remarks"></a>Bemerkungen

Diese Funktion stellt die Daten mithilfe des unmittelbaren Rendering bereit, sodass Sie die Daten beim Aufrufen der Funktion bereitstellen müssen. die Daten werden bis zum benötigten Cache zwischengespeichert. Verwenden Sie die `CacheData` Member-Funktion, wenn Sie eine große Datenmenge bereitstellen oder wenn Sie ein strukturiertes Speichermedium benötigen.

Um das verzögerte Rendering zu verwenden, müssen Sie die Member-Funktion von " [Delta Data](#delayrenderdata) " oder " [Delta Data](#delayrenderfiledata) " verwenden. Weitere Informationen zum verzögerten Rendering, wie von MFC verarbeitet, finden Sie im Artikel [Datenobjekte und Datenquellen: Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Weitere Informationen finden Sie in der [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur im Windows SDK.

Weitere Informationen finden Sie unter [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) im Windows SDK.

##  <a name="coledatasource"></a>COleDataSource:: COleDataSource

Erstellt ein `COleDataSource`-Objekt.

```
COleDataSource();
```

##  <a name="delayrenderdata"></a>COleDataSource::D elayrenderdata

Mit dieser Funktion können Sie ein Format angeben, in dem Daten während der Datenübertragungs Vorgänge angeboten werden.

```
void DelayRenderData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parameter

*cfFormat*<br/>
Das Zwischenablage Format, in dem die Daten angeboten werden sollen. Dieser Parameter kann eines der vordefinierten Zwischenablage Formate oder der Wert sein, der von der systemeigenen Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) -Funktion zurückgegeben wird.

*lpformatusw.*<br/>
Verweist auf eine [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur, die das Format beschreibt, in dem die Daten angeboten werden sollen. Geben Sie einen Wert für diesen Parameter an, wenn Sie zusätzliche Formatierungsinformationen angeben möchten, die über das in *cfFormat*angegebene Zwischenablage Format hinausgehen. Wenn er NULL ist, werden für die anderen Felder in der `FORMATETC` Struktur Standardwerte verwendet.

### <a name="remarks"></a>Bemerkungen

Diese Funktion stellt die Daten mithilfe von verzögertem Rendering bereit, sodass die Daten nicht sofort bereitgestellt werden. Die [OnRenderData](#onrenderdata) -oder [onrenderglobaldata](#onrenderglobaldata) -Member-Funktion wird aufgerufen, um die Daten anzufordern.

Verwenden Sie diese Funktion, wenn Sie die Daten nicht über ein `CFile` Objekt bereitstellen. Wenn Sie die Daten über ein `CFile` Objekt bereitstellen möchten, müssen Sie die Member-Funktion von " [Delta-renderfiledata](#delayrenderfiledata) " aufrufen. Weitere Informationen zum verzögerten Rendering, wie von MFC verarbeitet, finden Sie im Artikel [Datenobjekte und Datenquellen: Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Um das sofortige Rendering zu verwenden, müssen Sie die [CacheData](#cachedata) -oder [CacheGlobalData](#cacheglobaldata) -Member-Funktion aufzurufen.

Weitere Informationen finden Sie in der [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur im Windows SDK.

Weitere Informationen finden Sie unter [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) im Windows SDK.

##  <a name="delayrenderfiledata"></a>COleDataSource::D elayrenderfiledata

Mit dieser Funktion können Sie ein Format angeben, in dem Daten während der Datenübertragungs Vorgänge angeboten werden.

```
void DelayRenderFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parameter

*cfFormat*<br/>
Das Zwischenablage Format, in dem die Daten angeboten werden sollen. Dieser Parameter kann eines der vordefinierten Zwischenablage Formate oder der Wert sein, der von der systemeigenen Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) -Funktion zurückgegeben wird.

*lpformatusw.*<br/>
Verweist auf eine [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur, die das Format beschreibt, in dem die Daten angeboten werden sollen. Geben Sie einen Wert für diesen Parameter an, wenn Sie zusätzliche Formatierungsinformationen angeben möchten, die über das in *cfFormat*angegebene Zwischenablage Format hinausgehen. Wenn er NULL ist, werden für die anderen Felder in der `FORMATETC` Struktur Standardwerte verwendet.

### <a name="remarks"></a>Bemerkungen

Diese Funktion stellt die Daten mithilfe von verzögertem Rendering bereit, sodass die Daten nicht sofort bereitgestellt werden. Die [onrenderfiledata](#onrenderfiledata) -Member-Funktion wird aufgerufen, um die Daten anzufordern.

Verwenden Sie diese Funktion, wenn Sie ein `CFile` Objekt zum Bereitstellen der Daten verwenden möchten. Wenn Sie kein `CFile` Objekt verwenden, müssen Sie die Member-Funktion von " [Delta Data](#delayrenderdata) " aufrufen. Weitere Informationen zum verzögerten Rendering, wie von MFC verarbeitet, finden Sie im Artikel [Datenobjekte und Datenquellen: Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Um das sofortige Rendering zu verwenden, müssen Sie die [CacheData](#cachedata) -oder [CacheGlobalData](#cacheglobaldata) -Member-Funktion aufzurufen.

Weitere Informationen finden Sie in der [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur im Windows SDK.

Weitere Informationen finden Sie unter [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) im Windows SDK.

##  <a name="delaysetdata"></a>COleDataSource::D elaysetdata

Diese Funktion wird aufgerufen, um das Ändern des Inhalts der Datenquelle zu unterstützen.

```
void DelaySetData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parameter

*cfFormat*<br/>
Das Zwischenablage Format, in dem die Daten abgelegt werden sollen. Dieser Parameter kann eines der vordefinierten Zwischenablage Formate oder der Wert sein, der von der systemeigenen Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) -Funktion zurückgegeben wird.

*lpformatusw.*<br/>
Verweist auf eine [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur, die das Format beschreibt, in dem die Daten ersetzt werden sollen. Geben Sie einen Wert für diesen Parameter an, wenn Sie zusätzliche Formatierungsinformationen angeben möchten, die über das in *cfFormat*angegebene Zwischenablage Format hinausgehen. Wenn er NULL ist, werden für die anderen Felder in der `FORMATETC` Struktur Standardwerte verwendet.

### <a name="remarks"></a>Bemerkungen

[Onsetdata](#onsetdata) wird von Framework aufgerufen, wenn dies geschieht. Diese Option wird nur verwendet, wenn das Framework die Datenquelle aus [COleServerItem:: GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource)zurückgibt. Wenn `DelaySetData` nicht aufgerufen wird, wird die Funktion `OnSetData` nie aufgerufen. `DelaySetData` sollten für jede Zwischenablage oder jedes `FORMATETC` Format aufgerufen werden, das Sie unterstützen.

Weitere Informationen finden Sie in der [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur im Windows SDK.

Weitere Informationen finden Sie unter [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) im Windows SDK.

##  <a name="dodragdrop"></a>COleDataSource::D odragdrop

Ruft die `DoDragDrop` Member-Funktion auf, um einen Drag & Drop-Vorgang für diese Datenquelle auszuführen, in der Regel in einem [CWnd:: OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown) -Handler.

```
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,
    LPCRECT lpRectStartDrag = NULL,
    COleDropSource* pDropSource = NULL);
```

### <a name="parameters"></a>Parameter

*dweffects*<br/>
Drag & Drop-Vorgänge, die für diese Datenquelle zulässig sind. Kann eine oder mehrere der folgenden sein:

- DROPEFFECT_COPY ein Kopiervorgang durchgeführt werden konnte.

- DROPEFFECT_MOVE ein Verschiebungs Vorgang durchgeführt werden konnte.

- Es konnte DROPEFFECT_LINK eine Verknüpfung aus den gelöschten Daten zu den ursprünglichen Daten erstellt werden.

- DROPEFFECT_SCROLL gibt an, dass ein Drag-Scroll-Vorgang ausgeführt werden kann.

*lprectstartdrag*<br/>
Zeiger auf das Rechteck, das definiert, wo der Zieh Vorgang tatsächlich gestartet wird. Weitere Informationen finden Sie im folgenden Abschnitt "Hinweise".

*pdropsource*<br/>
Verweist auf eine Ablage Quelle. Wenn der Wert NULL ist, wird eine Standard Implementierung von [COleDropSource](../../mfc/reference/coledropsource-class.md) verwendet.

### <a name="return-value"></a>Rückgabewert

Vom Drag & Drop-Vorgang generierte Drop-Effekte Andernfalls DROPEFFECT_NONE, wenn der Vorgang nie beginnt, da der Benutzer die Maustaste losgelassen hat, bevor er das angegebene Rechteck verlässt.

### <a name="remarks"></a>Bemerkungen

Der Drag & Drop-Vorgang wird nicht sofort gestartet. Sie wartet, bis der Mauszeiger das von *lprectstartdrag* angegebene Rechteck verlässt oder bis eine angegebene Anzahl von Millisekunden verstrichen ist. Wenn *lprectstartdrag* den Wert NULL hat, ist die Größe des Rechtecks ein Pixel.

Die Verzögerungszeit wird durch eine Registrierungsschlüssel Einstellung angegeben. Sie können die Verzögerungszeit ändern, indem Sie [CWinApp:: schreiteprofilestring](../../mfc/reference/cwinapp-class.md#writeprofilestring) oder [CWinApp:: Beschreib teprofileint](../../mfc/reference/cwinapp-class.md#writeprofileint)aufrufen. Wenn Sie die Verzögerungszeit nicht angeben, wird ein Standardwert von 200 Millisekunden verwendet. Die Zeit für die Zieh Verzögerung wird wie folgt gespeichert:

- Die Zeit für die Drag-Verzögerung von Windows NT wird in HKEY_LOCAL_MACHINE \software\microsoft\windows\nt\currentversion\inifilemapping\win.ini\windows\dragdelta gespeichert.

- Windows 3. x-Zieh Verzögerungszeit wird im Gewinn gespeichert. INI-Datei im Abschnitt [Windows} '.

- Windows 95/98-Zieh Verzögerungszeit wird in einer zwischengespeicherten Version von Win gespeichert. Geleitet.

Weitere Informationen zur Art und Weise, in der Informationen zu Drag Delay in der Registrierung oder in gespeichert werden. Die INI-Datei finden Sie unter " [Beschreib teprofilestring](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) " in der Windows SDK.

Weitere Informationen finden Sie im Artikel [OLE Drag](../../mfc/drag-and-drop-ole.md)& amp; Drop.

##  <a name="empty"></a>COleDataSource:: Empty

Mit dieser Funktion können Sie das `COleDataSource` Objekt der Daten leeren.

```
void Empty();
```

### <a name="remarks"></a>Bemerkungen

Sowohl zwischengespeicherte als auch verzögerte Renderingformate werden geleert, sodass Sie wieder verwendet werden können.

Weitere Informationen finden Sie unter [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) in der Windows SDK.

##  <a name="flushclipboard"></a>COleDataSource:: flushclipboard

Rendert Daten, die sich in der Zwischenablage befinden, und ermöglicht das Einfügen von Daten aus der Zwischenablage, nachdem Ihre Anwendung heruntergefahren wurde.

```
static void PASCAL FlushClipboard();
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie [setClipboard](#setclipboard) , um Daten in die Zwischenablage einzufügen.

##  <a name="getclipboardowner"></a>COleDataSource:: getclipboardowner

Bestimmt, ob sich die Daten in der Zwischenablage seit dem letzten Aufruf von [setClipboard](#setclipboard) geändert haben, und identifiziert, wenn dies der Fall ist, den aktuellen Besitzer.

```
static COleDataSource* PASCAL GetClipboardOwner();
```

### <a name="return-value"></a>Rückgabewert

Die Datenquelle, die sich derzeit in der Zwischenablage befindet, oder NULL, wenn in der Zwischenablage nichts vorhanden ist oder die Zwischenablage nicht der aufrufenden Anwendung gehört.

##  <a name="onrenderdata"></a>COleDataSource:: OnRenderData

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

### <a name="remarks"></a>Bemerkungen

Das angegebene Format ist ein zuvor im `COleDataSource` Objekt angegebenes-Objekt, das die Element Funktion " [Delta Data](#delayrenderdata) " oder " [Delta Data](#delayrenderfiledata) " für verzögertes Rendering verwendet. Die Standard Implementierung dieser Funktion ruft [onrenderfiledata](#onrenderfiledata) oder [onrenderglobaldata](#onrenderglobaldata) auf, wenn das angegebene Speichermedium entweder eine Datei bzw. ein Arbeitsspeicher ist. Wenn keines dieser Formate bereitgestellt wird, gibt die Standard Implementierung 0 zurück und führt keine Aktion aus. Weitere Informationen zum verzögerten Rendering, wie von MFC verarbeitet, finden Sie im Artikel [Datenobjekte und Datenquellen: Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Wenn *lpstgmedium*-> *TYMED* TYMED_NULL ist, sollten die `STGMEDIUM` wie von *lpformatetc-> TYMED*angegeben zugeordnet und ausgefüllt werden. Wenn dies TYMED_NULL nicht der Fall ist, sollte die `STGMEDIUM` mit den Daten aufgefüllt werden.

Hierbei handelt es sich um eine erweiterte über schreibbare. Überschreiben Sie diese Funktion, um die Daten im angeforderten Format und Medium bereitzustellen. Abhängig von den Daten können Sie stattdessen eine der anderen Versionen dieser Funktion überschreiben. Wenn Ihre Daten klein und in der Größe liegen, überschreiben Sie `OnRenderGlobalData`. Wenn sich die Daten in einer Datei befinden oder eine Variable Größe hat, überschreiben Sie `OnRenderFileData`.

Weitere Informationen finden Sie in den Strukturen " [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) " und " [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) ", dem [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) -Enumerationstyp und " [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) " in der Windows SDK.

##  <a name="onrenderfiledata"></a>COleDataSource:: onrenderfiledata

Wird von Framework aufgerufen, um Daten im angegebenen Format abzurufen, wenn das angegebene Speichermedium eine Datei ist.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Parameter

*lpformatusw.*<br/>
Verweist auf die [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur, die das Format angibt, in dem Informationen angefordert werden.

*pFile*<br/>
Verweist auf ein [CFile](../../mfc/reference/cfile-class.md) -Objekt, in dem die Daten gerendert werden sollen.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Das angegebene Format ist ein zuvor im `COleDataSource` Objekt angegebenes-Objekt, das die Funktion " [Delta Data](#delayrenderdata) " für verzögertes Rendering verwendet. Die Standard Implementierung dieser Funktion gibt einfach false zurück.

Hierbei handelt es sich um eine erweiterte über schreibbare. Überschreiben Sie diese Funktion, um die Daten im angeforderten Format und Medium bereitzustellen. Abhängig von den Daten können Sie stattdessen eine der anderen Versionen dieser Funktion überschreiben. Wenn Sie mehrere Speichermedien verarbeiten möchten, überschreiben Sie [OnRenderData](#onrenderdata). Wenn sich die Daten in einer Datei befinden oder eine Variable Größe hat, überschreiben Sie `OnRenderFileData`. Weitere Informationen zum verzögerten Rendering, wie von MFC verarbeitet, finden Sie im Artikel [Datenobjekte und Datenquellen: Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Weitere Informationen finden Sie in der [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur und in [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) im Windows SDK.

##  <a name="onrenderglobaldata"></a>COleDataSource:: onrenderglobaldata

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
Verweist auf ein Handle für den globalen Speicher, in dem die Daten zurückgegeben werden sollen. Wenn noch keiner zugeordnet wurde, kann dieser Parameter NULL sein.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Das angegebene Format ist ein zuvor im `COleDataSource` Objekt angegebenes-Objekt, das die Funktion " [Delta Data](#delayrenderdata) " für verzögertes Rendering verwendet. Die Standard Implementierung dieser Funktion gibt einfach false zurück.

Wenn *phglobal* NULL ist, sollte ein neues HGLOBAL zugeordnet und in *phglobal*zurückgegeben werden. Andernfalls sollte der von *phglobal* angegebene HGLOBAL mit den Daten gefüllt werden. Die Menge der in der hglobal platzierten Daten darf die aktuelle Größe des Speicherblocks nicht überschreiten. Außerdem kann der Block nicht neu zugeordnet werden.

Hierbei handelt es sich um eine erweiterte über schreibbare. Überschreiben Sie diese Funktion, um die Daten im angeforderten Format und Medium bereitzustellen. Abhängig von den Daten können Sie stattdessen eine der anderen Versionen dieser Funktion überschreiben. Wenn Sie mehrere Speichermedien verarbeiten möchten, überschreiben Sie [OnRenderData](#onrenderdata). Wenn sich Ihre Daten in einer Datei befinden oder eine Variable Größe haben, überschreiben Sie [onrenderfiledata](#onrenderfiledata). Weitere Informationen zum verzögerten Rendering, wie von MFC verarbeitet, finden Sie im Artikel [Datenobjekte und Datenquellen: Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Weitere Informationen finden Sie in der [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur und in [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) im Windows SDK.

##  <a name="onsetdata"></a>COleDataSource:: onsetdata

Wird von Framework aufgerufen, um die Daten im angegebenen Format im `COleDataSource` Objekt festzulegen oder zu ersetzen.

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>Parameter

*lpformatusw.*<br/>
Verweist auf die [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur, die das Format angibt, in dem Daten ersetzt werden.

*lpstgmedium*<br/>
Verweist auf die [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) -Struktur, die die Daten enthält, die den aktuellen Inhalt des `COleDataSource` Objekts ersetzen.

*brelease*<br/>
Gibt an, wer den Besitz des Speichermediums nach Abschluss des Funktions Aufrufes besitzt. Der Aufrufer entscheidet, wer für das Freigeben der im Auftrag des Speichermediums zugewiesenen Ressourcen zuständig ist. Der Aufrufer legt dies durch Festlegen von *brelease*fest. Wenn die *brelease* ungleich NULL ist, übernimmt die Datenquelle den Besitz und gibt das Medium frei, wenn es nicht mehr verwendet wird. Wenn *brelease* den Wert 0 hat, behält der Aufrufer den Besitz, und die Datenquelle kann das Speichermedium nur für die Dauer des Aufrufes verwenden.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Die Datenquelle übernimmt den Besitz der Daten erst, nachdem Sie erfolgreich abgerufen wurde. Dies bedeutet, dass Sie keinen Besitz übernimmt, wenn `OnSetData` 0 zurückgibt. Wenn die Datenquelle den Besitz übernimmt, wird das Speichermedium durch Aufrufen der [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) -Funktion freigegeben.

Bei der Standardimplementierung wird keine Aktion ausgeführt. Überschreiben Sie diese Funktion, um die Daten im angegebenen Format zu ersetzen. Hierbei handelt es sich um eine erweiterte über schreibbare.

Weitere Informationen finden Sie in den Funktionen " [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) " und " [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) " und " [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) " und " [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) " in der Windows SDK.

##  <a name="setclipboard"></a>COleDataSource:: setClipboard

Speichert die Daten, die im `COleDataSource` Objekt enthalten sind, nach dem Aufrufen einer der folgenden Funktionen in der Zwischenablage: [CacheData](#cachedata), [CacheGlobalData](#cacheglobaldata), [Delta-renderData](#delayrenderdata)oder [Delta Data](#delayrenderfiledata).

```
void SetClipboard();
```

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel Hierarchien](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleDataObject-Klasse](../../mfc/reference/coledataobject-class.md)
