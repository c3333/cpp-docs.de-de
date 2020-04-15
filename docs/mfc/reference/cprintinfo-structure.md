---
title: CPrintInfo-Struktur
ms.date: 11/04/2016
f1_keywords:
- CPrintInfo
helpviewer_keywords:
- CPrintInfo structure [MFC]
ms.assetid: 0b3de849-d050-4386-9a14-f4c1a25684f7
ms.openlocfilehash: cf0a1e6b7e742e950663f1ed9cc9ff2ddabd9d6f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364021"
---
# <a name="cprintinfo-structure"></a>CPrintInfo-Struktur

Speichert Informationen zu einem Druck- oder Druckvorschauauftrag.

## <a name="syntax"></a>Syntax

```
struct CPrintInfo
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPrintInfo::GetFromPage](#getfrompage)|Gibt die Nummer der ersten zu druckenden Seite zurück.|
|[CPrintInfo::GetMaxPage](#getmaxpage)|Gibt die Nummer der letzten Seite des Dokuments zurück.|
|[CPrintInfo::GetMinPage](#getminpage)|Gibt die Nummer der ersten Seite des Dokuments zurück.|
|[CPrintInfo::GetOffsetPage](#getoffsetpage)|Gibt die Anzahl der Seiten zurück, die der ersten Seite eines DocObject-Elements vorangehen, das in einem kombinierten DocObject-Druckauftrag gedruckt wird.|
|[CPrintInfo::GetToPage](#gettopage)|Gibt die Nummer der zuletzt gedruckten Seite zurück.|
|[CPrintInfo::SetMaxPage](#setmaxpage)|Legt die Nummer der letzten Seite des Dokuments fest.|
|[CPrintInfo::SetMinPage](#setminpage)|Legt die Nummer der ersten Seite des Dokuments fest.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPrintInfo::m_bContinuePrinting](#m_bcontinueprinting)|Enthält ein Flag, das angibt, ob das Framework die Druckschleife fortsetzen soll.|
|[CPrintInfo::m_bDirect](#m_bdirect)|Enthält ein Flag, das angibt, ob das Dokument direkt gedruckt wird (ohne das Dialogfeld Drucken anzuzeigen).|
|[CPrintInfo::m_bDocObject](#m_bdocobject)|Enthält ein Flag, das angibt, ob es sich bei dem gedruckten Dokument um ein DocObject handelt.|
|[CPrintInfo::m_bPreview](#m_bpreview)|Enthält ein Flag, das angibt, ob das Dokument in der Vorschau angezeigt wird.|
|[CPrintInfo::m_dwFlags](#m_dwflags)|Gibt DocObject-Druckvorgänge an.|
|[CPrintInfo::m_lpUserData](#m_lpuserdata)|Enthält einen Zeiger auf eine vom Benutzer erstellte Struktur.|
|[CPrintInfo::m_nCurPage](#m_ncurpage)|Gibt die Nummer der Seite an, die gerade gedruckt wird.|
|[CPrintInfo::m_nJobNumber](#m_njobnumber)|Gibt die Auftragsnummer an, die vom Betriebssystem für den aktuellen Druckauftrag zugewiesen wurde.|
|[CPrintInfo::m_nNumPreviewPages](#m_nnumpreviewpages)|Identifiziert die Anzahl der im Vorschaufenster angezeigten Seiten. entweder 1 oder 2.|
|[CPrintInfo::m_nOffsetPage](#m_noffsetpage)|Gibt den Offset der ersten Seite eines bestimmten DocObject in einem kombinierten DocObject-Druckauftrag an.|
|[CPrintInfo::m_pPD](#m_ppd)|Enthält einen Zeiger `CPrintDialog` auf das Objekt, das für das Dialogfeld Drucken verwendet wird.|
|[CPrintInfo::m_rectDraw](#m_rectdraw)|Gibt ein Rechteck an, das den aktuellen nutzbaren Seitenbereich definiert.|
|[CPrintInfo::m_strPageDesc](#m_strpagedesc)|Enthält eine Formatzeichenfolge für die Seitennummernanzeige.|

## <a name="remarks"></a>Bemerkungen

`CPrintInfo`ist eine Struktur und hat keine Basisklasse.

Das Framework erstellt `CPrintInfo` ein Objekt, das jedes Mal, wenn der Befehl Druck oder Druckvorschau ausgewählt wird, und zerstört es, wenn der Befehl abgeschlossen ist.

`CPrintInfo`enthält Informationen sowohl zum Druckauftrag als Ganzes, z. B. zum Zudrucken des Seitenbereichs, als auch zum aktuellen Status des Druckauftrags, z. B. zur Seite, die gerade gedruckt wird. Einige Informationen werden in einem [zugeordneten CPrintDialog-Objekt](../../mfc/reference/cprintdialog-class.md) gespeichert. Dieses Objekt enthält die Vom Benutzer im Dialogfeld Drucken eingegebenen Werte.

Ein `CPrintInfo` Objekt wird während des Druckvorgangs zwischen dem Framework und der Ansichtsklasse übergeben und wird zum Austausch von Informationen zwischen den beiden Objekten verwendet. Das Framework informiert z. B. die Ansichtsklasse darüber, welche Seite `m_nCurPage` des `CPrintInfo`Dokuments gedruckt werden soll, indem dem Member von ein Wert zugewiesen wird. Die Ansichtsklasse ruft den Wert ab und führt den tatsächlichen Druck der angegebenen Seite durch.

Ein weiteres Beispiel ist der Fall, in dem die Länge des Dokuments erst bekannt ist, wenn es gedruckt wird. In diesem Fall testet die Ansichtsklasse jedes Mal, wenn eine Seite gedruckt wird, das Ende des Dokuments. Wenn das Ende erreicht ist, `m_bContinuePrinting` legt `CPrintInfo` die Ansichtsklasse den Member von auf FALSE fest. dies informiert das Framework, um die Druckschleife zu stoppen.

`CPrintInfo`wird von den Memberfunktionen von `CView` unter "Siehe auch" aufgeführt verwendet. Weitere Informationen zur Druckarchitektur der Microsoft Foundation-Klassenbibliothek finden Sie unter [Rahmenfenster und](../../mfc/frame-windows.md) [Dokument-/Ansichtsarchitektur](../../mfc/document-view-architecture.md) sowie in den Artikeln [Drucken](../../mfc/printing.md) und [Drucken: Mehrseitige Dokumente](../../mfc/multipage-documents.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CPrintInfo`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxext.h

## <a name="cprintinfogetfrompage"></a><a name="getfrompage"></a>CPrintInfo::GetFromPage

Rufen Sie diese Funktion auf, um die Nummer der ersten zu druckenden Seite abzurufen.

```
UINT GetFromPage() const;
```

### <a name="return-value"></a>Rückgabewert

Die Nummer der ersten zu druckenden Seite.

### <a name="remarks"></a>Bemerkungen

Dies ist der vom Benutzer im Dialogfeld Drucken angegebene `CPrintDialog` Wert, der `m_pPD` im Objekt gespeichert wird, auf das vom Element verwiesen wird. Wenn der Benutzer keinen Wert angegeben hat, ist der Standardwert die erste Seite des Dokuments.

## <a name="cprintinfogetmaxpage"></a><a name="getmaxpage"></a>CPrintInfo::GetMaxPage

Rufen Sie diese Funktion auf, um die Nummer der letzten Seite des Dokuments abzurufen.

```
UINT GetMaxPage() const;
```

### <a name="return-value"></a>Rückgabewert

Die Nummer der letzten Seite des Dokuments.

### <a name="remarks"></a>Bemerkungen

Dieser Wert wird `CPrintDialog` im Objekt gespeichert, auf das `m_pPD` der Member verweist.

## <a name="cprintinfogetminpage"></a><a name="getminpage"></a>CPrintInfo::GetMinPage

Rufen Sie diese Funktion auf, um die Nummer der ersten Seite des Dokuments abzurufen.

```
UINT GetMinPage() const;
```

### <a name="return-value"></a>Rückgabewert

Die Nummer der ersten Seite des Dokuments.

### <a name="remarks"></a>Bemerkungen

Dieser Wert wird `CPrintDialog` im Objekt gespeichert, auf das `m_pPD` der Member verweist.

## <a name="cprintinfogetoffsetpage"></a><a name="getoffsetpage"></a>CPrintInfo::GetOffsetPage

Rufen Sie diese Funktion auf, um den Offset abzurufen, wenn mehrere DocObject-Elemente von einem DocObject-Client gedruckt werden.

```
UINT GetOffsetPage() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Seiten vor der ersten Seite eines DocObject-Elements, die in einem kombinierten DocObject-Druckauftrag gedruckt werden.

### <a name="remarks"></a>Bemerkungen

Auf diesen Wert wird `m_nOffsetPage` vom Member verwiesen. Die erste Seite Ihres Dokuments `m_nOffsetPage` wird mit dem Wert + 1 nummeriert, wenn sie als DocObject mit anderen aktiven Dokumenten gedruckt wird. Der `m_nOffsetPage` Member ist nur `m_bDocObject` gültig, wenn der Wert TRUE ist.

## <a name="cprintinfogettopage"></a><a name="gettopage"></a>CPrintInfo::GetToPage

Rufen Sie diese Funktion auf, um die Nummer der letzten zu druckenden Seite abzurufen.

```
UINT GetToPage() const;
```

### <a name="return-value"></a>Rückgabewert

Die Nummer der letzten zu druckenden Seite.

### <a name="remarks"></a>Bemerkungen

Dies ist der vom Benutzer im Dialogfeld Drucken angegebene `CPrintDialog` Wert, der `m_pPD` im Objekt gespeichert wird, auf das vom Element verwiesen wird. Wenn der Benutzer keinen Wert angegeben hat, ist der Standardwert die letzte Seite des Dokuments.

## <a name="cprintinfom_bcontinueprinting"></a><a name="m_bcontinueprinting"></a>CPrintInfo::m_bContinuePrinting

Enthält ein Flag, das angibt, ob das Framework die Druckschleife fortsetzen soll.

### <a name="remarks"></a>Bemerkungen

Wenn Sie die Druckzeitpaginierung vorgenommen haben, können Sie diesen `CView::OnPrepareDC` Member in Ihrer Außerkraftsetzung auf FALSE festlegen, sobald das Ende des Dokuments erreicht ist. Sie müssen diese Variable nicht ändern, wenn Sie die Länge des Dokuments `SetMaxPage` zu Beginn des Druckauftrags mithilfe der Memberfunktion angegeben haben. Der `m_bContinuePrinting` Member ist eine öffentliche Variable vom Typ BOOL.

## <a name="cprintinfom_bdirect"></a><a name="m_bdirect"></a>CPrintInfo::m_bDirect

Das Framework legt diesen Member auf TRUE fest, wenn das Dialogfeld Drucken für den Direktdruck umgangen wird. FALSE sonst.

### <a name="remarks"></a>Bemerkungen

Das Dialogfeld Drucken wird normalerweise umgangen, wenn Sie aus der Shell drucken oder wenn das Drucken mit der Befehls-ID ID_FILE_PRINT_DIRECT erfolgt.

Normalerweise ändern Sie dieses Mitglied normalerweise nicht, aber wenn Sie es ändern, ändern Sie es, bevor Sie [CView::DoPreparePrinting](../../mfc/reference/cview-class.md#doprepareprinting) in Ihrer Außerkraftsetzung von [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)aufrufen.

## <a name="cprintinfom_bdocobject"></a><a name="m_bdocobject"></a>CPrintInfo::m_bDocObject

Enthält ein Flag, das angibt, ob es sich bei dem gedruckten Dokument um ein DocObject handelt.

### <a name="remarks"></a>Bemerkungen

Datenmember `m_dwFlags` `m_nOffsetPage` und sind ungültig, es sei denn, dieses Flag ist TRUE.

## <a name="cprintinfom_bpreview"></a><a name="m_bpreview"></a>CPrintInfo::m_bPreview

Enthält ein Flag, das angibt, ob das Dokument in der Vorschau angezeigt wird.

### <a name="remarks"></a>Bemerkungen

Dies wird vom Framework festgelegt, je nachdem, welcher Befehl der Benutzer ausgeführt hat. Das Dialogfeld Drucken wird für einen Druckvorschauauftrag nicht angezeigt. Der `m_bPreview` Member ist eine öffentliche Variable vom Typ BOOL.

## <a name="cprintinfom_dwflags"></a><a name="m_dwflags"></a>CPrintInfo::m_dwFlags

Enthält eine Kombination von Flags, die DocObject-Druckvorgänge angeben.

### <a name="remarks"></a>Bemerkungen

Gültig nur, `m_bDocObject` wenn das Datenmember TRUE ist.

Die Flags können einer oder mehrere der folgenden Werte sein:

- PRINTFLAG_MAYBOTHERUSER

- PRINTFLAG_PROMPTUSER

- PRINTFLAG_USERMAYCHANGEPRINTER

- PRINTFLAG_RECOMPOSETODEVICE

- PRINTFLAG_DONTACTUALLYPRINT

- PRINTFLAG_FORCEPROPERTIES

- PRINTFLAG_PRINTTOFILE

## <a name="cprintinfom_lpuserdata"></a><a name="m_lpuserdata"></a>CPrintInfo::m_lpUserData

Enthält einen Zeiger auf eine vom Benutzer erstellte Struktur.

### <a name="remarks"></a>Bemerkungen

Sie können dies verwenden, um druckspezifische Daten zu speichern, die Sie nicht in Ihrer Ansichtsklasse speichern möchten. Der `m_lpUserData` Member ist eine öffentliche Variable vom Typ LPVOID.

## <a name="cprintinfom_ncurpage"></a><a name="m_ncurpage"></a>CPrintInfo::m_nCurPage

Enthält die Nummer der aktuellen Seite.

### <a name="remarks"></a>Bemerkungen

Das Framework `CView::OnPrepareDC` `CView::OnPrint` ruft und einmal für jede Seite des Dokuments, wobei jedes Mal ein anderer Wert für dieses Element angegeben wird. seine Werte reichen von `GetFromPage` dem Wert, `GetToPage`der von zurückgegeben wird, bis zu dem Wert, der von zurückgegeben wird. Verwenden Sie dieses Element `CView::OnPrepareDC` in `CView::OnPrint` Ihren Außerkraftsetzungen und zum Drucken der angegebenen Seite des Dokuments.

Wenn der Vorschaumodus zum ersten Mal aufgerufen wird, liest das Framework den Wert dieses Elements, um zu bestimmen, welche Seite des Dokuments ursprünglich in der Vorschau angezeigt werden soll. Sie können den Wert dieses Elements in `CView::OnPreparePrinting` Ihrer Außerkraftsetzung festlegen, um die aktuelle Position des Benutzers im Dokument beizubehalten, wenn Sie in den Vorschaumodus wechseln. Der `m_nCurPage` Member ist eine öffentliche Variable vom Typ UINT.

## <a name="cprintinfom_njobnumber"></a><a name="m_njobnumber"></a>CPrintInfo::m_nJobNumber

Gibt die Auftragsnummer an, die vom Betriebssystem für den aktuellen Druckauftrag zugewiesen wurde.

### <a name="remarks"></a>Bemerkungen

Dieser Wert kann SP_ERROR sein, wenn der Auftrag noch nicht `CPrintInfo` gedruckt wurde (d. h., wenn das Objekt neu erstellt wurde und noch nicht zum Drucken verwendet wurde) oder wenn beim Starten des Auftrags ein Fehler aufgetreten ist.

## <a name="cprintinfom_nnumpreviewpages"></a><a name="m_nnumpreviewpages"></a>CPrintInfo::m_nNumPreviewPages

Enthält die Anzahl der im Vorschaumodus angezeigten Seiten. es kann entweder 1 oder 2 sein.

### <a name="remarks"></a>Bemerkungen

Der `m_nNumPreviewPages` Member ist eine öffentliche Variable vom Typ UINT.

## <a name="cprintinfom_noffsetpage"></a><a name="m_noffsetpage"></a>CPrintInfo::m_nOffsetPage

Enthält die Anzahl der Seiten vor der ersten Seite eines bestimmten DocObject in einem kombinierten DocObject-Druckauftrag.

## <a name="cprintinfom_ppd"></a><a name="m_ppd"></a>CPrintInfo::m_pPD

Enthält einen Zeiger `CPrintDialog` auf das Objekt, das zum Anzeigen des Dialogfelds Drucken für den Druckauftrag verwendet wird.

### <a name="remarks"></a>Bemerkungen

Das `m_pPD` Member ist eine öffentliche Variable, `CPrintDialog`die als Zeiger auf deklariert wird.

## <a name="cprintinfom_rectdraw"></a><a name="m_rectdraw"></a>CPrintInfo::m_rectDraw

Gibt den verwendbaren Zeichenbereich des Zeichenblatts in logischen Koordinaten an.

### <a name="remarks"></a>Bemerkungen

Darauf sollten Sie in Ihrer Außerkraftsetzung von `CView::OnPrint`verweisen. Sie können dieses Element verwenden, um nachzuverfolgen, welcher Bereich nach dem Drucken von Kopfzeilen, Fußzeilen usw. weiterhin verwendet werden kann. Der `m_rectDraw` Member ist eine `CRect`öffentliche Variable vom Typ .

## <a name="cprintinfom_strpagedesc"></a><a name="m_strpagedesc"></a>CPrintInfo::m_strPageDesc

Enthält eine Formatzeichenfolge, die zum Anzeigen der Seitenzahlen während der Druckvorschau verwendet wird. Diese Zeichenfolge besteht aus zwei Teilzeichenfolgen, eine für die einseitige Anzeige und eine für die doppelseitige Anzeige, die jeweils durch ein Zeichen von ''n' beendet werden.

### <a name="remarks"></a>Bemerkungen

Das Framework verwendet "Page %u'nPages %u-%u'n" als Standardwert. Wenn Sie ein anderes Format für die Seitenzahlen wünschen, `CView::OnPreparePrinting`geben Sie in der Außerkraftsetzung von eine Formatzeichenfolge an. Der `m_strPageDesc` Member ist eine `CString`öffentliche Variable vom Typ .

## <a name="cprintinfosetmaxpage"></a><a name="setmaxpage"></a>CPrintInfo::SetMaxPage

Rufen Sie diese Funktion auf, um die Nummer der letzten Seite des Dokuments anzugeben.

```
void SetMaxPage(UINT nMaxPage);
```

### <a name="parameters"></a>Parameter

*nMaxPage*<br/>
Nummer der letzten Seite des Dokuments.

### <a name="remarks"></a>Bemerkungen

Dieser Wert wird `CPrintDialog` im Objekt gespeichert, auf das `m_pPD` der Member verweist. Wenn die Länge des Dokuments vor dem Drucken bekannt ist, `CView::OnPreparePrinting`rufen Sie diese Funktion aus ihrer Außerkraftsetzung von auf. Wenn die Länge des Dokuments von einer Einstellung abhängt, die vom Benutzer im `CView::OnBeginPrinting`Dialogfeld Drucken angegeben wird, rufen Sie diese Funktion über die Außerkraftsetzung von auf. Wenn die Länge des Dokuments erst bekannt ist, wenn es gedruckt wird, verwenden Sie das `m_bContinuePrinting` Element, um die Druckschleife zu steuern.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting).

## <a name="cprintinfosetminpage"></a><a name="setminpage"></a>CPrintInfo::SetMinPage

Rufen Sie diese Funktion auf, um die Nummer der ersten Seite des Dokuments anzugeben.

```
void SetMinPage(UINT nMinPage);
```

### <a name="parameters"></a>Parameter

*nMinPage*<br/>
Nummer der ersten Seite des Dokuments.

### <a name="remarks"></a>Bemerkungen

Seitenzahlen beginnen normalerweise bei 1. Dieser Wert wird `CPrintDialog` im Objekt gespeichert, auf das `m_pPD` der Member verweist.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)<br/>
[CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)<br/>
[CView::OnEndPrintPreview](../../mfc/reference/cview-class.md#onendprintpreview)<br/>
[CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)<br/>
[CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)<br/>
[CView::OnPrint](../../mfc/reference/cview-class.md#onprint)
