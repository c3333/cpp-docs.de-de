---
title: COleDocObjectItem-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleDocObjectItem
- AFXOLE/COleDocObjectItem
- AFXOLE/COleDocObjectItem::COleDocObjectItem
- AFXOLE/COleDocObjectItem::DoDefaultPrinting
- AFXOLE/COleDocObjectItem::ExecCommand
- AFXOLE/COleDocObjectItem::GetActiveView
- AFXOLE/COleDocObjectItem::GetPageCount
- AFXOLE/COleDocObjectItem::OnPreparePrinting
- AFXOLE/COleDocObjectItem::OnPrint
- AFXOLE/COleDocObjectItem::QueryCommand
- AFXOLE/COleDocObjectItem::Release
helpviewer_keywords:
- COleDocObjectItem [MFC], COleDocObjectItem
- COleDocObjectItem [MFC], DoDefaultPrinting
- COleDocObjectItem [MFC], ExecCommand
- COleDocObjectItem [MFC], GetActiveView
- COleDocObjectItem [MFC], GetPageCount
- COleDocObjectItem [MFC], OnPreparePrinting
- COleDocObjectItem [MFC], OnPrint
- COleDocObjectItem [MFC], QueryCommand
- COleDocObjectItem [MFC], Release
ms.assetid: d150d306-8fd3-4831-b06d-afbe71d8fc9b
ms.openlocfilehash: a696226185dd99b9e277e74d92cbe15c95cc900a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375048"
---
# <a name="coledocobjectitem-class"></a>COleDocObjectItem-Klasse

Implementiert "Active Document Containment".

## <a name="syntax"></a>Syntax

```
class COleDocObjectItem : public COleClientItem
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDocObjectItem::COleDocObjectItem](#coledocobjectitem)|Erstellt ein `COleDocObject` Element.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDocObjectItem::DoDefaultPrinting](#dodefaultprinting)|Druckt das Dokument der Containeranwendung mit den Standarddruckereinstellungen.|
|[COleDocObjectItem::ExecCommand](#execcommand)|Führt den vom Benutzer angegebenen Befehl aus.|
|[COleDocObjectItem::GetActiveView](#getactiveview)|Ruft die aktive Ansicht des Dokuments ab.|
|[COleDocObjectItem::GetPageCount](#getpagecount)|Ruft die Anzahl der Seiten im Dokument der Containeranwendung ab.|
|[COleDocObjectItem::OnPreparePrinting](#onprepareprinting)|Bereitet das Dokument der Containeranwendung für den Druck vor.|
|[COleDocObjectItem::OnPrint](#onprint)|Druckt das Dokument der Containeranwendung.|
|[COleDocObjectItem::QueryCommand](#querycommand)|Fragt den Status von Befehlen ab, die von Ereignissen auf der Benutzeroberfläche generiert wurden.|
|[COleDocObjectItem::Release](#release)|Gibt die Verbindung zu einem ole verknüpften Element frei und schließt sie, wenn sie geöffnet war. Zerstört das Clientelement nicht.|

## <a name="remarks"></a>Bemerkungen

In MFC wird ein active-Dokument ähnlich wie eine reguläre, direkte bearbeitbare Einbettung behandelt, mit den folgenden Unterschieden:

- Die `COleDocument`-derived-Klasse verwaltet weiterhin eine Liste der aktuell eingebetteten Elemente. Diese Elemente können `COleDocObjectItem`jedoch -abgeleitete Elemente sein.

- Wenn ein aktives Dokument aktiv ist, nimmt es den gesamten Clientbereich der Ansicht ein, wenn es an Ort und Stelle aktiv ist.

- Ein Active-Dokumentcontainer hat die volle Kontrolle über das **Hilfemenü.**

- Das **Hilfemenü** enthält Menüelemente für den Aktiven Dokumentcontainer und den Server.

Da der Container "Aktives Dokument" eigentümer das **Hilfemenü** ist, ist der Container für die Weiterleitung von **Serverhilfemenünachrichten** an den Server verantwortlich. Diese Integration wird `COleDocObjectItem`von behandelt.

Weitere Informationen zum Menüzusammenführen und Aktivieren von aktiven Dokumenten finden Sie unter Übersicht über [die Eindämmung aktiver Dokumente](../../mfc/active-document-containment.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`COleDocObjectItem`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxole.h

## <a name="coledocobjectitemcoledocobjectitem"></a><a name="coledocobjectitem"></a>COleDocObjectItem::COleDocObjectItem

Rufen Sie diese Memberfunktion `COleDocObjectItem` auf, um das Objekt zu initialisieren.

```
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```

### <a name="parameters"></a>Parameter

*pContainerDoc*<br/>
Ein Zeiger auf `COleDocument` das Objekt, das als aktiver Dokumentcontainer fungiert. Dieser Parameter muss NULL sein, um IMPLEMENT_SERIALIZE zu aktivieren. Normalerweise werden OLE-Elemente mit einem Nicht-NULL-Dokumentzeiger erstellt.

## <a name="coledocobjectitemdodefaultprinting"></a><a name="dodefaultprinting"></a>COleDocObjectItem::DoDefaultPrinting

Wird vom Framework für ein Dokument mit den Standardeinstellungen aufgerufen.

```
static HRESULT DoDefaultPrinting(
    CView* pCaller,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parameter

*pCaller*<br/>
Ein Zeiger auf ein [CView-Objekt,](../../mfc/reference/cview-class.md) das den Druckbefehl sendet.

*Pinfo*<br/>
Ein Zeiger auf ein [CPrintInfo-Objekt,](../../mfc/reference/cprintinfo-structure.md) das den zu druckenden Auftrag beschreibt.

## <a name="coledocobjectitemexeccommand"></a><a name="execcommand"></a>COleDocObjectItem::ExecCommand

Rufen Sie diese Memberfunktion auf, um den vom Benutzer angegebenen Befehl auszuführen.

```
HRESULT ExecCommand(
    DWORD nCmdID,
    DWORD nCmdExecOpt = OLECMDEXECOPT_DONTPROMPTUSER,
    const GUID* pguidCmdGroup = NULL);
```

### <a name="parameters"></a>Parameter

*nCmdID*<br/>
Der Bezeichner des auszuführenden Befehls. Muss sich in der von *pguidCmdGroup*identifizierten Gruppe aufgeben.

*nCmdExecOpt*<br/>
Gibt Befehlsausführungsoptionen an. Legen Sie standardmäßig fest, dass der Befehl ausgeführt wird, ohne den Benutzer dazu aufzufordert. Eine Liste der Werte finden Sie unter [OLECMDEXECOPT.](/windows/win32/api/docobj/ne-docobj-olecmdexecopt)

*pguidCmdGroup*<br/>
Eindeutiger Bezeichner der Befehlsgruppe. Standardmäßig NULL, das die Standardgruppe angibt. Der in *nCmdID* übergebene Befehl muss zur Gruppe gehören.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück, wenn erfolgreich; Andernfalls wird einer der folgenden Fehlercodes zurückgegeben.

|Wert|Beschreibung|
|-----------|-----------------|
|E_UNEXPECTED|Unerwarteter Fehler.|
|E_FAIL|Fehler.|
|E_NOTIMPL|Gibt an, dass MFC selbst versuchen sollte, den Befehl zu übersetzen und zu versenden.|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* ist nicht NULL, gibt jedoch keine erkannte Befehlsgruppe an.|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID* wird in der Gruppe pGroup nicht als gültiger Befehl erkannt.|
|OLECMDERR_DISABLED|Der von *nCmdID* identifizierte Befehl ist deaktiviert und kann nicht ausgeführt werden.|
|OLECMDERR_NOHELP|Der Anrufer bat um Hilfe für den von *nCmdID* identifizierten Befehl, aber es ist keine Hilfe verfügbar.|
|OLECMDERR_CANCELLED|Der Benutzer hat die Ausführung abgebrochen.|

### <a name="remarks"></a>Bemerkungen

Die *pguidCmdGroup* und die *parameter nCmdID* zusammen identifizieren den befehl, der aufgerufen werden soll. Der Parameter *nCmdExecOpt* gibt die genaue Aktion an.

## <a name="coledocobjectitemgetactiveview"></a><a name="getactiveview"></a>COleDocObjectItem::GetActiveView

Rufen Sie diese Memberfunktion auf, `IOleDocumentView` um einen Zeiger auf die Schnittstelle der aktuell aktiven Ansicht abzurufen.

```
LPOLEDOCUMENTVIEW GetActiveView() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die [IOleDocumentView-Schnittstelle](/windows/win32/api/docobj/nn-docobj-ioledocumentview) der aktuell aktiven Ansicht. Wenn keine aktuelle Ansicht vorhanden ist, wird NULL zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Die Verweisanzahl für `IOleDocumentView` den zurückgegebenen Zeiger wird nicht erhöht, bevor er von dieser Funktion zurückgegeben wird.

## <a name="coledocobjectitemgetpagecount"></a><a name="getpagecount"></a>COleDocObjectItem::GetPageCount

Rufen Sie diese Memberfunktion auf, um die Anzahl der Seiten im Dokument abzurufen.

```
BOOL GetPageCount(
    LPLONG pnFirstPage,
    LPLONG pcPages);
```

### <a name="parameters"></a>Parameter

*pnFirstPage*<br/>
Ein Zeiger auf die Nummer der ersten Seite des Dokuments. Kann NULL sein, was angibt, dass der Aufrufer diese Nummer nicht benötigt.

*pcPages*<br/>
Ein Zeiger auf die Gesamtzahl der Seiten im Dokument. Kann NULL sein, was angibt, dass der Aufrufer diese Nummer nicht benötigt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

## <a name="coledocobjectitemonprepareprinting"></a><a name="onprepareprinting"></a>COleDocObjectItem::OnPreparePrinting

Diese Memberfunktion wird vom Framework aufgerufen, um ein Dokument für den Druck vorzubereiten.

```
static BOOL OnPreparePrinting(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>Parameter

*pCaller*<br/>
Ein Zeiger auf ein [CView-Objekt,](../../mfc/reference/cview-class.md) das den Druckbefehl sendet.

*Pinfo*<br/>
Ein Zeiger auf ein [CPrintInfo-Objekt,](../../mfc/reference/cprintinfo-structure.md) das den zu druckenden Auftrag beschreibt.

*bPrintAll*<br/>
Gibt an, ob das gesamte Dokument gedruckt werden soll.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

## <a name="coledocobjectitemonprint"></a><a name="onprint"></a>COleDocObjectItem::OnPrint

Diese Memberfunktion wird vom Framework aufgerufen, um ein Dokument zu drucken.

```
static void OnPrint(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>Parameter

*pCaller*<br/>
Ein Zeiger auf ein CView-Objekt, das den Druckbefehl sendet.

*Pinfo*<br/>
Ein Zeiger auf ein [CPrintInfo-Objekt,](../../mfc/reference/cprintinfo-structure.md) das den zu druckenden Auftrag beschreibt.

*bPrintAll*<br/>
Gibt an, ob das gesamte Dokument gedruckt werden soll.

## <a name="coledocobjectitemquerycommand"></a><a name="querycommand"></a>COleDocObjectItem::QueryCommand

Fragt den Status von Befehlen ab, die von Ereignissen auf der Benutzeroberfläche generiert wurden.

```
HRESULT QueryCommand(
    ULONG nCmdID,
    DWORD* pdwStatus,
    OLECMDTEXT* pCmdText =NULL,
    const GUID* pguidCmdGroup =NULL);
```

### <a name="parameters"></a>Parameter

*nCmdID*<br/>
Bezeichner des Abgefragten Befehls.

*pdwStatus*<br/>
Ein Zeiger auf die Flags, die als Ergebnis der Abfrage zurückgegeben werden. Eine Liste möglicher Werte finden Sie unter [OLECMDF](/windows/win32/api/docobj/ne-docobj-olecmdf).

*pCmdText*<br/>
Zeiger auf eine [OLECMDTEXT-Struktur,](/windows/win32/api/docobj/ns-docobj-olecmdtext) in der Namens- und Statusinformationen für einen einzelnen Befehl zurückgegeben werden sollen. Kann NULL sein, um anzugeben, dass der Aufrufer diese Informationen nicht benötigt.

*pguidCmdGroup*<br/>
Eindeutiger Bezeichner der Befehlsgruppe; kann NULL sein, um die Standardgruppe anzugeben.

### <a name="return-value"></a>Rückgabewert

Eine vollständige Auflistung der Rückgabewerte finden Sie unter [IOleCommandTarget::QueryStatus](/windows/win32/api/docobj/nf-docobj-iolecommandtarget-querystatus) im Windows SDK.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion emuliert die Funktionalität der [IOleCommandTarget::QueryStatus-Methode,](/windows/win32/api/docobj/nf-docobj-iolecommandtarget-querystatus) wie im Windows SDK beschrieben.

## <a name="coledocobjectitemrelease"></a><a name="release"></a>COleDocObjectItem::Release

Gibt die Verbindung zu einem ole verknüpften Element frei und schließt sie, wenn sie geöffnet war. Zerstört das Clientelement nicht.

```
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```

### <a name="parameters"></a>Parameter

*dwCloseOption*<br/>
Flag, das angibt, unter welchen Umständen das OLE-Element gespeichert wird, wenn es in den geladenen Zustand zurückkehrt. Eine Liste möglicher Werte finden Sie unter [COleClientItem::Close](../../mfc/reference/coleclientitem-class.md#close).

### <a name="remarks"></a>Bemerkungen

Zerstört das Clientelement nicht.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem-Klasse](../../mfc/reference/coleclientitem-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem-Klasse](../../mfc/reference/coleclientitem-class.md)<br/>
[CDocObjectServerItem-Klasse](../../mfc/reference/cdocobjectserveritem-class.md)
