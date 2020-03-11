---
title: CDocTemplate-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDocTemplate
- AFXWIN/CDocTemplate
- AFXWIN/CDocTemplate::CDocTemplate
- AFXWIN/CDocTemplate::AddDocument
- AFXWIN/CDocTemplate::CloseAllDocuments
- AFXWIN/CDocTemplate::CreateNewDocument
- AFXWIN/CDocTemplate::CreateNewFrame
- AFXWIN/CDocTemplate::CreateOleFrame
- AFXWIN/CDocTemplate::CreatePreviewFrame
- AFXWIN/CDocTemplate::GetDocString
- AFXWIN/CDocTemplate::GetFirstDocPosition
- AFXWIN/CDocTemplate::GetNextDoc
- AFXWIN/CDocTemplate::InitialUpdateFrame
- AFXWIN/CDocTemplate::LoadTemplate
- AFXWIN/CDocTemplate::MatchDocType
- AFXWIN/CDocTemplate::OpenDocumentFile
- AFXWIN/CDocTemplate::RemoveDocument
- AFXWIN/CDocTemplate::SaveAllModified
- AFXWIN/CDocTemplate::SetContainerInfo
- AFXWIN/CDocTemplate::SetDefaultTitle
- AFXWIN/CDocTemplate::SetPreviewInfo
- AFXWIN/CDocTemplate::SetServerInfo
helpviewer_keywords:
- CDocTemplate [MFC], CDocTemplate
- CDocTemplate [MFC], AddDocument
- CDocTemplate [MFC], CloseAllDocuments
- CDocTemplate [MFC], CreateNewDocument
- CDocTemplate [MFC], CreateNewFrame
- CDocTemplate [MFC], CreateOleFrame
- CDocTemplate [MFC], CreatePreviewFrame
- CDocTemplate [MFC], GetDocString
- CDocTemplate [MFC], GetFirstDocPosition
- CDocTemplate [MFC], GetNextDoc
- CDocTemplate [MFC], InitialUpdateFrame
- CDocTemplate [MFC], LoadTemplate
- CDocTemplate [MFC], MatchDocType
- CDocTemplate [MFC], OpenDocumentFile
- CDocTemplate [MFC], RemoveDocument
- CDocTemplate [MFC], SaveAllModified
- CDocTemplate [MFC], SetContainerInfo
- CDocTemplate [MFC], SetDefaultTitle
- CDocTemplate [MFC], SetPreviewInfo
- CDocTemplate [MFC], SetServerInfo
ms.assetid: 14b41a1f-bf9d-4eac-b6a8-4c54ffcc77f6
ms.openlocfilehash: 3b2d84af9be8e5c606cde8794b51e12207dcdec9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855523"
---
# <a name="cdoctemplate-class"></a>CDocTemplate-Klasse

Eine abstrakte Basisklasse, die die grundlegende Funktionalität für Dokumentvorlagen definiert.

## <a name="syntax"></a>Syntax

```
class CDocTemplate : public CCmdTarget
```

## <a name="members"></a>Members

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDocTemplate:: CDocTemplate](#cdoctemplate)|Erstellt ein `CDocTemplate`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDocTemplate:: adddocument](#adddocument)|Fügt einer Vorlage ein Dokument hinzu.|
|[CDocTemplate:: closealldocuments](#closealldocuments)|Schließt alle dieser Vorlage zugeordneten Dokumente.|
|[CDocTemplate:: kreatenewdocument](#createnewdocument)|Erstellt ein neues Dokument.|
|[CDocTemplate:: kreatenewframe](#createnewframe)|Erstellt ein neues Rahmen Fenster, das ein Dokument und eine Ansicht enthält.|
|[CDocTemplate:: kreateoleframe](#createoleframe)|Erstellt ein OLE-fähiges Rahmen Fenster.|
|[CDocTemplate:: "kreatepreviewframe"](#createpreviewframe)|Erstellt einen für Rich Preview verwendeten untergeordneten Frame.|
|[CDocTemplate:: getdocstring](#getdocstring)|Ruft eine Zeichenfolge ab, die dem Dokumenttyp zugeordnet ist.|
|[CDocTemplate:: getfirstdocposition](#getfirstdocposition)|Ruft die Position des ersten Dokuments ab, das dieser Vorlage zugeordnet ist.|
|[CDocTemplate:: getnextdoc](#getnextdoc)|Ruft ein Dokument und die Position des nächsten ab.|
|[CDocTemplate:: initialupdateframe](#initialupdateframe)|Initialisiert das Rahmen Fenster und macht es optional sichtbar.|
|[CDocTemplate:: LoadTemplate](#loadtemplate)|Lädt die Ressourcen für eine angegebene `CDocTemplate` oder eine abgeleitete Klasse.|
|[CDocTemplate:: matchdoctype](#matchdoctype)|Bestimmt den Grad des Konfidenz Werts in der Übereinstimmung zwischen einem Dokumenttyp und dieser Vorlage.|
|[CDocTemplate:: OpenDocumentFile](#opendocumentfile)|Öffnet eine durch einen Pfadnamen angegebene Datei.|
|[CDocTemplate:: RemoveDocument](#removedocument)|Entfernt ein Dokument aus einer Vorlage.|
|[CDocTemplate:: saveallmodified](#saveallmodified)|Speichert alle dieser Vorlage zugeordneten Dokumente, die geändert wurden.|
|[CDocTemplate:: setcontainerinfo](#setcontainerinfo)|Bestimmt die Ressourcen für OLE-Container, wenn ein direktes OLE-Element bearbeitet wird.|
|[CDocTemplate:: setdefaulttitle](#setdefaulttitle)|Zeigt den Standard Titel in der Titelleiste des Dokument Fensters an.|
|[CDocTemplate:: setpreviewinfo](#setpreviewinfo)|Einrichtung des Out-of-Process-Vorschau Handlers.|
|[CDocTemplate:: setserverinfo](#setserverinfo)|Bestimmt die Ressourcen und Klassen, wenn das Server Dokument direkt eingebettet oder bearbeitet wird.|

## <a name="remarks"></a>Bemerkungen

In der Regel erstellen Sie eine oder mehrere Dokumentvorlagen in der Implementierung der `InitInstance` Funktion Ihrer Anwendung. Eine Dokument Vorlage definiert die Beziehungen zwischen drei Typen von Klassen:

- Eine Dokument Klasse, die Sie von `CDocument`ableiten.

- Eine Ansichts Klasse, die Daten aus der oben aufgeführten Dokument Klasse anzeigt. Sie können diese Klasse von `CView`, `CScrollView`, `CFormView`oder `CEditView`ableiten. (Sie können auch `CEditView` direkt verwenden.)

- Eine Frame Fenster Klasse, die die Ansicht enthält. Bei einer Anwendung mit einer einzelnen Dokument Schnittstelle (SDI) leiten Sie diese Klasse von `CFrameWnd`ab. Bei einer MDI-Anwendung (Multiple Document Interface) leiten Sie diese Klasse von `CMDIChildWnd`ab. Wenn Sie das Verhalten des Rahmen Fensters nicht anpassen müssen, können Sie `CFrameWnd` oder `CMDIChildWnd` direkt verwenden, ohne Ihre eigene Klasse zu ableiten.

Die Anwendung verfügt über eine Dokument Vorlage für jeden unterstützten Dokumenttyp. Wenn Ihre Anwendung z. b. sowohl Tabellen-als auch Textdokumente unterstützt, verfügt die Anwendung über zwei Dokumentvorlagen Objekte. Jede Dokument Vorlage ist für das Erstellen und Verwalten aller Dokumente seines Typs zuständig.

In der Dokument Vorlage werden Zeiger auf die `CRuntimeClass`-Objekte für die Dokument-, Ansichts-und Rahmen Fenster Klassen gespeichert. Diese `CRuntimeClass` Objekte werden beim Erstellen einer Dokument Vorlage angegeben.

Die Dokument Vorlage enthält die ID der Ressourcen, die mit dem Dokumenttyp verwendet werden (z. b. Menü-, Symbol-oder Zugriffstasten-Tabellen Ressourcen). Die Dokument Vorlage enthält auch Zeichen folgen, die zusätzliche Informationen über den Dokumenttyp enthalten. Hierzu gehören der Name des Dokument Typs (z. b. "Arbeitsblatt") und die Dateierweiterung (z. b. ". xls"). Optional können Sie auch andere Zeichen folgen enthalten, die von der Benutzeroberfläche der Anwendung, vom Windows-Datei-Manager und von der Unterstützung für das Verknüpfen und Einbetten von Objekten verwendet werden.

Wenn es sich bei Ihrer Anwendung um einen OLE-Container und/oder-Server handelt, wird in der Dokument Vorlage auch die ID des Menüs definiert, das während der direkten Aktivierung verwendet wird. Wenn es sich bei Ihrer Anwendung um einen OLE-Server handelt, definiert die Dokument Vorlage die ID der Symbolleiste und des Menüs, die während der direkten Aktivierung verwendet werden. Sie geben diese zusätzlichen OLE-Ressourcen durch Aufrufen von `SetContainerInfo` und `SetServerInfo`an.

Da `CDocTemplate` eine abstrakte Klasse ist, können Sie die-Klasse nicht direkt verwenden. Eine typische Anwendung verwendet eine der beiden vom Microsoft Foundation Class-Bibliothek bereitgestellten `CDocTemplate`abgeleiteten Klassen: `CSingleDocTemplate`, die SDI implementiert, und `CMultiDocTemplate`, die MDI implementiert. Weitere Informationen zur Verwendung von Dokumentvorlagen finden Sie in diesen Klassen.

Wenn Ihre Anwendung ein Benutzeroberflächen Paradigma erfordert, das sich grundlegend von SDI oder MDI unterscheidet, können Sie eine eigene Klasse von `CDocTemplate`ableiten.

Weitere Informationen zu `CDocTemplate`finden Sie unter [Dokumentvorlagen und der Erstellungs Vorgang für Dokumente und Ansichten](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocTemplate`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

##  <a name="adddocument"></a>CDocTemplate:: adddocument

Verwenden Sie diese Funktion, um ein Dokument zu einer Vorlage hinzuzufügen.

```
virtual void AddDocument(CDocument* pDoc);
```

### <a name="parameters"></a>Parameter

*pDoc*<br/>
Ein Zeiger auf das hinzu zufügende Dokument.

### <a name="remarks"></a>Bemerkungen

Die abgeleiteten Klassen [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) und [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) überschreiben diese Funktion. Wenn Sie Ihre eigene Dokumentvorlagen Klasse von `CDocTemplate`ableiten, muss die abgeleitete Klasse diese Funktion überschreiben.

##  <a name="cdoctemplate"></a>CDocTemplate:: CDocTemplate

Erstellt ein `CDocTemplate`-Objekt.

```
CDocTemplate (
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Parameter

*nidresource*<br/>
Gibt die ID der Ressourcen an, die mit dem Dokumenttyp verwendet werden. Dies kann Menü, Symbol, Zugriffstasten Tabelle und Zeichen folgen Ressourcen umfassen.

Die Zeichen folgen Ressource besteht aus bis zu sieben Teil Zeichenfolgen, die durch das Zeichen ' \n ' getrennt sind (das Zeichen ' \n ' wird als Platzhalter benötigt, wenn keine Teil Zeichenfolge eingeschlossen wird. nachfolgende ' \n '-Zeichen sind jedoch nicht erforderlich); Diese Teil Zeichenfolgen beschreiben den Dokumenttyp. Weitere Informationen zu den Teil Zeichenfolgen finden Sie unter [getdocstring](#getdocstring). Diese Zeichen folgen Ressource befindet sich in der Ressourcen Datei der Anwendung. Beispiel:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

Beachten Sie, dass die Zeichenfolge mit dem Zeichen "\n" beginnt. Dies liegt daran, dass die erste Teil Zeichenfolge nicht für MDI-Anwendungen verwendet wird und daher nicht eingeschlossen ist. Sie können diese Zeichenfolge mit dem Zeichen folgen-Editor bearbeiten. die gesamte Zeichenfolge wird als einzelner Eintrag im Zeichen folgen-Editor angezeigt, nicht als sieben separate Einträge.

*pdocclass*<br/>
Verweist auf das `CRuntimeClass` Objekt der Document-Klasse. Diese Klasse ist eine von `CDocument`abgeleitete Klasse, die Sie zur Darstellung Ihrer Dokumente definieren.

*pframeclass*<br/>
Verweist auf das `CRuntimeClass` Objekt der Rahmen Fenster Klasse. Diese Klasse kann eine `CFrameWnd`abgeleitete Klasse sein, oder Sie kann `CFrameWnd` selbst sein, wenn Sie das Standardverhalten für das Hauptrahmen Fenster wünschen.

*pviewclass*<br/>
Verweist auf das `CRuntimeClass` Objekt der Ansichts Klasse. Diese Klasse ist eine von `CView`abgeleitete Klasse, die Sie zum Anzeigen der Dokumente definieren.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Member-Funktion, um ein `CDocTemplate`-Objekt zu erstellen. Weisen Sie dynamisch ein `CDocTemplate` Objekt zu, und übergeben Sie es an [CWinApp:: AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) aus der `InitInstance` Member-Funktion Ihrer Anwendungsklasse.

##  <a name="closealldocuments"></a>CDocTemplate:: closealldocuments

Mit dieser Member-Funktion schließen Sie alle geöffneten Dokumente.

```
virtual void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>Parameter

*bendsitzung*<br/>
Wird nicht verwendet.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion wird in der Regel als Teil des File Exit-Befehls verwendet. Die Standard Implementierung dieser Funktion Ruft die [CDocument::D eletecontents](../../mfc/reference/cdocument-class.md#deletecontents) -Member-Funktion auf, um die Daten des Dokuments zu löschen, und schließt dann die Rahmen Fenster für alle Sichten, die an das Dokument angefügt sind.

Überschreiben Sie diese Funktion, wenn Sie festlegen möchten, dass der Benutzer vor dem Schließen des Dokuments eine spezielle Bereinigungs Verarbeitung durchführt. Wenn das Dokument beispielsweise einen Datensatz in einer Datenbank darstellt, empfiehlt es sich, diese Funktion zu überschreiben, um die Datenbank zu schließen.

##  <a name="createnewdocument"></a>CDocTemplate:: kreatenewdocument

Rufen Sie diese Member-Funktion auf, um ein neues Dokument mit dem Typ zu erstellen, der dieser Dokument Vorlage zugeordnet ist.

```
virtual CDocument* CreateNewDocument();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das neu erstellte Dokument oder NULL, wenn ein Fehler auftritt.

##  <a name="createnewframe"></a>CDocTemplate:: kreatenewframe

Erstellt ein neues Rahmen Fenster, das ein Dokument und eine Ansicht enthält.

```
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,
    CFrameWnd* pOther);
```

### <a name="parameters"></a>Parameter

*pDoc*<br/>
Das Dokument, auf das das neue Rahmen Fenster verweisen soll. Kann den Wert NULL haben.

*nach oben*<br/>
Das Rahmen Fenster, auf dem das neue Rahmen Fenster basieren soll. Kann den Wert NULL haben.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das neu erstellte Rahmen Fenster oder NULL, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

`CreateNewFrame` verwendet die `CRuntimeClass` Objekte, die an den Konstruktor übergeben werden, um ein neues Rahmen Fenster mit angefügter Ansicht und angefügtem Dokument zu erstellen. Wenn der *Pdoc* -Parameter NULL ist, gibt das Framework eine Ablauf Verfolgungs Meldung aus.

Der *pother* -Parameter wird verwendet, um den Windows New-Befehl zu implementieren. Es stellt ein Rahmen Fenster bereit, in dem das neue Rahmen Fenster modelliert werden kann. Das neue Rahmen Fenster wird normalerweise unsichtbar erstellt. Rufen Sie diese Funktion auf, um Rahmen Fenster außerhalb der Standard Framework-Implementierung von "Datei neu" und "Datei öffnen" zu erstellen

##  <a name="createoleframe"></a>CDocTemplate:: kreateoleframe

Erstellt ein OLE-Rahmen Fenster.

```
CFrameWnd* CreateOleFrame(
    CWnd* pParentWnd,
    CDocument* pDoc,
    BOOL bCreateView);
```

### <a name="parameters"></a>Parameter

*pparser*<br/>
Ein Zeiger auf das übergeordnete Fenster des Frames.

*pDoc*<br/>
Ein Zeiger auf das Dokument, auf das das neue OLE-Rahmen Fenster verweisen soll.

*bkreateview*<br/>
Bestimmt, ob eine Ansicht zusammen mit dem Frame erstellt wird.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein Rahmen Fenster, wenn erfolgreich. andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Wenn *bkreateview* NULL ist, wird ein leerer Frame erstellt.

##  <a name="getdocstring"></a>CDocTemplate:: getdocstring

Ruft eine Zeichenfolge ab, die dem Dokumenttyp zugeordnet ist.

```
virtual BOOL GetDocString(
    CString& rString,
    enum DocStringIndex index) const;
```

### <a name="parameters"></a>Parameter

*RString*<br/>
Ein Verweis auf ein `CString` Objekt, das die Zeichenfolge enthält, wenn die Funktion zurückgegeben wird.

*Index*<br/>
Ein Index der Teil Zeichenfolge, die aus der Zeichenfolge abgerufen wird, die den Dokumenttyp beschreibt. Dieser Parameter kann einen der folgenden Werte aufweisen:

- `CDocTemplate::windowTitle` Name, der in der Titelleiste des Anwendungsfensters angezeigt wird (z. b. "Microsoft Excel"). Nur in der Dokument Vorlage für SDI-Anwendungen vorhanden.

- `CDocTemplate::docName` Stamm für den Standarddokument Namen (z. b. "Sheet"). Dieser Stamm plus eine Zahl wird für den Standardnamen eines neuen Dokuments dieses Typs verwendet, wenn der Benutzer den neuen Befehl aus dem Menü Datei auswählt (z. b. "Sheet1" oder "Tabelle2"). Wenn keine Angabe erfolgt, wird als Standardwert "undefiniert" verwendet.

- `CDocTemplate::fileNewName` Name dieses Dokument Typs. Wenn die Anwendung mehr als einen Dokumenttyp unterstützt, wird diese Zeichenfolge im Dialogfeld "Datei neu" angezeigt (z. b. "Arbeitsblatt"). Wenn kein Wert angegeben wird, kann auf den Dokumenttyp nicht mithilfe des File New-Befehls zugegriffen werden.

- `CDocTemplate::filterName` Beschreibung des Dokument Typs und ein Platzhalter Filter, der mit Dokumenten dieses Typs übereinstimmt. Diese Zeichenfolge wird in der Dropdown Liste Dateityp auflisten im Dialogfeld Datei öffnen angezeigt (z. b. "Arbeitsblätter (*. xls)"). Wenn nicht angegeben, ist der Dokumenttyp mit dem Befehl zum Öffnen von Dateien nicht zugänglich.

- `CDocTemplate::filterExt` Erweiterung für Dokumente dieses Typs (z. b. ". xls"). Wenn nicht angegeben, ist der Dokumenttyp mit dem Befehl zum Öffnen von Dateien nicht zugänglich.

- `CDocTemplate::regFileTypeId` Bezeichner für den Dokumenttyp, der in der von Windows verwalteten Registrierungsdatenbank gespeichert werden soll. Diese Zeichenfolge ist nur für die interne Verwendung vorgesehen (z. b. "excelworksheet"). Wenn nichts angegeben ist, kann der Dokumenttyp nicht beim Windows-Datei-Manager registriert werden.

- `CDocTemplate::regFileTypeName` Name des Dokument Typs, der in der Registrierungsdatenbank gespeichert werden soll. Diese Zeichenfolge kann in Dialogfeldern der Anwendungen angezeigt werden, die auf die Registrierungsdatenbank zugreifen (z. b. "Microsoft Excel-Arbeitsblatt").

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn die angegebene Teil Zeichenfolge gefunden wurde. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Mit dieser Funktion rufen Sie eine bestimmte Teil Zeichenfolge ab, die den Dokumenttyp beschreibt. Die Zeichenfolge, die diese Teil Zeichenfolgen enthält, wird in der Dokument Vorlage gespeichert und aus einer Zeichenfolge in der Ressourcen Datei für die Anwendung abgeleitet. Das Framework ruft diese Funktion auf, um die benötigten Zeichen folgen für die Benutzeroberfläche der Anwendung zu erhalten. Wenn Sie eine Dateinamenerweiterung für die Dokumente Ihrer Anwendung angegeben haben, ruft das Framework auch diese Funktion auf, wenn der Windows-Registrierungsdatenbank ein Eintrag hinzugefügt wird. Dadurch können Dokumente über den Windows-Datei-Manager geöffnet werden.

Diese Funktion wird nur aufgerufen, wenn Sie eine eigene Klasse von `CDocTemplate`ableiten.

##  <a name="getfirstdocposition"></a>CDocTemplate:: getfirstdocposition

Ruft die Position des ersten Dokuments ab, das dieser Vorlage zugeordnet ist.

```
virtual POSITION GetFirstDocPosition() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein Positionswert, der verwendet werden kann, um die Liste der dieser Dokument Vorlage zugeordneten Dokumente zu durchlaufen. oder NULL, wenn die Liste leer ist.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um die Position des ersten Dokuments in der Liste der Dokumente, die dieser Vorlage zugeordnet sind, zu erhalten. Verwenden Sie den Positionswert als Argument für [CDocTemplate:: getnextdoc](#getnextdoc) , um die Liste der der Vorlage zugeordneten Dokumente zu durchlaufen.

[CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) und [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) überschreiben diese reine virtuelle Funktion. Jede Klasse, die Sie von `CDocTemplate` ableiten, muss diese Funktion ebenfalls überschreiben.

##  <a name="getnextdoc"></a>CDocTemplate:: getnextdoc

Ruft das Listenelement ab, das von *RPOs*identifiziert wird, und legt dann *RPOs* auf den Positionswert des nächsten Eintrags in der Liste fest.

```
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das nächste Dokument in der Liste der dieser Vorlage zugeordneten Dokumente.

### <a name="parameters"></a>Parameter

*rPos*<br/>
Ein Verweis auf einen Positionswert, der von einem vorherigen Rückruf von [getfirstdocposition](#getfirstdocposition) oder `GetNextDoc`zurückgegeben wurde.

### <a name="remarks"></a>Bemerkungen

Wenn das abgerufene Element das letzte in der Liste ist, wird der neue Wert von *RPOs* auf NULL festgelegt.

Sie können `GetNextDoc` in einer Forward-Iterations Schleife verwenden, wenn Sie die ursprüngliche Position mit einem Aufrufen von [getfirstdocposition](#getfirstdocposition)einrichten.

Sie müssen sicherstellen, dass der Positionswert eine gültige Position in der Liste darstellt. Wenn Sie ungültig ist, wird die Debugversion des Microsoft Foundation Class-Bibliothek Assert.

##  <a name="initialupdateframe"></a>CDocTemplate:: initialupdateframe

Initialisiert das Rahmen Fenster und macht es optional sichtbar.

```
virtual void InitialUpdateFrame(
    CFrameWnd* pFrame,
    CDocument* pDoc,
    BOOL bMakeVisible = TRUE);
```

### <a name="parameters"></a>Parameter

*pFrame*<br/>
Das Rahmen Fenster, das das erste Update benötigt.

*pDoc*<br/>
Das Dokument, dem der Frame zugeordnet ist. Kann den Wert NULL haben.

*bmakevisible*<br/>
Gibt an, ob der Frame sichtbar und aktiv werden soll.

### <a name="remarks"></a>Bemerkungen

Ruft `IntitialUpdateFrame` nach dem Erstellen eines neuen Frames mit `CreateNewFrame`auf. Das Aufrufen dieser Funktion bewirkt, dass die Ansichten in diesem Rahmen Fenster Ihre `OnInitialUpdate` Aufrufe empfangen. Wenn zuvor noch keine aktive Ansicht vorhanden war, wird die primäre Ansicht des Rahmen Fensters aktiv. die primäre Ansicht ist eine Ansicht mit der untergeordneten ID AFX_IDW_PANE_FIRST. Schließlich wird das Rahmen Fenster sichtbar gemacht, wenn *bmakevisible* ungleich 0 (null) ist. Wenn *bmakevisible* gleich 0 (null) ist, bleiben der aktuelle Fokus und der sichtbare Zustand des Rahmen Fensters unverändert.

Es ist nicht erforderlich, diese Funktion aufzurufen, wenn Sie die Implementierung des Frameworks von Datei New und Datei Open verwenden.

##  <a name="loadtemplate"></a>CDocTemplate:: LoadTemplate

Lädt die Ressourcen für eine angegebene `CDocTemplate` oder eine abgeleitete Klasse.

```
virtual void LoadTemplate();
```

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion wird vom Framework aufgerufen, um die Ressourcen für ein bestimmtes `CDocTemplate` oder eine abgeleitete Klasse zu laden. Normalerweise wird Sie während der Erstellung aufgerufen, außer wenn die Vorlage Global erstellt wird. In diesem Fall wird der Aufruf von `LoadTemplate` verzögert, bis [CWinApp:: AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) aufgerufen wird.

##  <a name="matchdoctype"></a>CDocTemplate:: matchdoctype

Bestimmt den Grad des Konfidenz Werts in der Übereinstimmung zwischen einem Dokumenttyp und dieser Vorlage.

```
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,
    CDocument*& rpDocMatch);
```

### <a name="parameters"></a>Parameter

*lpszpathname*<br/>
Pfadname der Datei, deren Typ bestimmt werden soll.

*rpdocmatch*<br/>
Zeiger auf ein Dokument, dem das übereinstimmende Dokument zugewiesen ist, wenn die von *lpszpathname* angegebene Datei bereits geöffnet ist.

### <a name="return-value"></a>Rückgabewert

Ein Wert aus der **Konfidenz** Enumeration, der wie folgt definiert wird:

```
enum Confidence
    {
    noAttempt,
    maybeAttemptForeign,
    maybeAttemptNative,
    yesAttemptForeign,
    yesAttemptNative,
    yesAlreadyOpen
    };
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um den Typ der Dokument Vorlage zu bestimmen, die zum Öffnen einer Datei verwendet werden soll. Wenn Ihre Anwendung mehrere Dateitypen unterstützt, können Sie diese Funktion beispielsweise verwenden, um zu bestimmen, welche der verfügbaren Dokumentvorlagen für eine bestimmte Datei geeignet ist, indem Sie `MatchDocType` für jede Vorlage aufrufen und eine Vorlage entsprechend dem zurückgegebenen Vertrauens Wert auswählen.

Wenn die von *lpszpathname* angegebene Datei bereits geöffnet ist, gibt diese Funktion `CDocTemplate::yesAlreadyOpen` zurück und kopiert das `CDocument` Objekt der Datei in das-Objekt bei *rpdocmatch*.

Wenn die Datei nicht geöffnet ist, aber die Erweiterung in *lpszpathname* mit der durch `CDocTemplate::filterExt`angegebenen Erweiterung übereinstimmt, gibt diese Funktion `CDocTemplate::yesAttemptNative` zurück und legt *rpdocmatch* auf NULL fest. Weitere Informationen zu `CDocTemplate::filterExt`finden Sie unter [CDocTemplate:: getdocstring](#getdocstring).

Wenn keiner der Fälle true ist, gibt die Funktion `CDocTemplate::yesAttemptForeign`zurück.

Die Standard Implementierung gibt weder `CDocTemplate::maybeAttemptForeign` noch `CDocTemplate::maybeAttemptNative`zurück. Überschreiben Sie diese Funktion, um eine für die Anwendung geeignete typübereinstimmungs Logik zu implementieren, und verwenden Sie möglicherweise diese beiden Werte aus der **Konfidenz** Auflistung

##  <a name="opendocumentfile"></a>CDocTemplate:: OpenDocumentFile

Öffnet eine Datei, die durch einen Pfad angegeben wird.

```
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;

virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU) = 0;
```

### <a name="parameters"></a>Parameter

*lpszpathname*<br/>
in Zeiger auf den Pfad der Datei, die das zu öffnende Dokument enthält.

*baddtomru*<br/>
in TRUE gibt an, dass das Dokument eine der aktuellsten Dateien ist. FALSE gibt an, dass das Dokument nicht eine der aktuellsten Dateien ist.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Dokument, dessen Datei von *lpszpathname*; benannt wird. NULL, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Öffnet die Datei, deren Pfad von *lpszpathname*angegeben wird. Wenn *lpszpathname* NULL ist, wird eine neue Datei erstellt, die ein Dokument mit dem dieser Vorlage zugeordneten Typ enthält.

##  <a name="removedocument"></a>CDocTemplate:: RemoveDocument

Entfernt das Dokument, auf das von *Pdoc* verwiesen wird, aus der Liste der Dokumente, die dieser Vorlage zugeordnet sind.

```
virtual void RemoveDocument(CDocument* pDoc);
```

### <a name="parameters"></a>Parameter

*pDoc*<br/>
Zeiger auf das zu entfernende Dokument.

### <a name="remarks"></a>Bemerkungen

Die abgeleiteten Klassen `CMultiDocTemplate` und `CSingleDocTemplate` diese Funktion überschreiben. Wenn Sie Ihre eigene Dokumentvorlagen Klasse von `CDocTemplate`ableiten, muss die abgeleitete Klasse diese Funktion überschreiben.

##  <a name="saveallmodified"></a>CDocTemplate:: saveallmodified

Speichert alle Dokumente, die geändert wurden.

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn erfolgreich; andernfalls 0.

##  <a name="setcontainerinfo"></a>CDocTemplate:: setcontainerinfo

Bestimmt die Ressourcen für OLE-Container, wenn ein direktes OLE-Element bearbeitet wird.

```
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```

### <a name="parameters"></a>Parameter

*nidoleingeplacecontainer*<br/>
Die ID der Ressourcen, die verwendet werden, wenn ein eingebettetes Objekt aktiviert wird.

### <a name="remarks"></a>Bemerkungen

Mit dieser Funktion können Sie die Ressourcen festlegen, die verwendet werden sollen, wenn ein OLE-Objekt direkt aktiviert wird. Diese Ressourcen können Menüs und Zugriffstasten Tabellen enthalten. Diese Funktion wird in der Regel in der [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) -Funktion Ihrer Anwendung aufgerufen.

Das Menü, das *nidoleinplacecontainer* zugeordnet ist, enthält Trennzeichen, mit denen das Menü des aktivierten direkten Elements mit dem Menü der Containeranwendung zusammengeführt werden kann. Weitere Informationen zum Zusammenführen von Server-und Container Menüs finden Sie im Artikel [Menüs und Ressourcen (OLE)](../../mfc/menus-and-resources-ole.md).

##  <a name="setdefaulttitle"></a>CDocTemplate:: setdefaulttitle

Mit dieser Funktion wird der Standard Titel des Dokuments geladen und in der Titelleiste des Dokuments angezeigt.

```
virtual void SetDefaultTitle(CDocument* pDocument) = 0;
```

### <a name="parameters"></a>Parameter

*pdocument*<br/>
Zeiger auf das Dokument, dessen Titel festgelegt werden soll.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zum Standard Titel finden Sie in der Beschreibung `CDocTemplate::docName` in [CDocTemplate:: getdocstring](#getdocstring).

##  <a name="setserverinfo"></a>CDocTemplate:: setserverinfo

Bestimmt die Ressourcen und Klassen, wenn das Server Dokument direkt eingebettet oder bearbeitet wird.

```
void SetServerInfo(
    UINT nIDOleEmbedding,
    UINT nIDOleInPlaceServer = 0,
    CRuntimeClass* pOleFrameClass = NULL,
    CRuntimeClass* pOleViewClass = NULL);
```

### <a name="parameters"></a>Parameter

*nidoleeinbettungen*<br/>
Die ID der Ressourcen, die verwendet werden, wenn ein eingebettetes Objekt in einem separaten Fenster geöffnet wird.

*nidoleingeplaceserver*<br/>
Die ID der Ressourcen, die verwendet werden, wenn ein eingebettetes Objekt direkt aktiviert wird.

*poleframeclass*<br/>
Ein Zeiger auf eine [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) -Struktur, die Klassen Informationen für das Rahmen Fenster Objekt enthält, das erstellt wird, wenn die direkte Aktivierung stattfindet.

*poleviewclass*<br/>
Ein Zeiger auf eine `CRuntimeClass` Struktur, die Klassen Informationen für das Ansichts Objekt enthält, das erstellt wird, wenn die direkte Aktivierung stattfindet.

### <a name="remarks"></a>Bemerkungen

Mit dieser Member-Funktion können Sie Ressourcen identifizieren, die von der Serveranwendung verwendet werden, wenn der Benutzer die Aktivierung eines eingebetteten Objekts anfordert. Diese Ressourcen bestehen aus Menüs und Zugriffstasten Tabellen. Diese Funktion wird in der Regel im `InitInstance` Ihrer Anwendung aufgerufen.

Das Menü, das *nidoleinplaceserver* zugeordnet ist, enthält Trennzeichen, mit denen das Server Menü mit dem Menü des Containers zusammengeführt werden kann. Weitere Informationen zum Zusammenführen von Server-und Container Menüs finden Sie im Artikel [Menüs und Ressourcen (OLE)](../../mfc/menus-and-resources-ole.md).

##  <a name="createpreviewframe"></a>CDocTemplate:: "kreatepreviewframe"

Erstellt einen für Rich Preview verwendeten untergeordneten Frame.

```
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,
    CDocument* pDoc);
```

### <a name="parameters"></a>Parameter

*pparser*<br/>
Ein Zeiger auf ein übergeordnetes Fenster (in der Regel von der Shell bereitgestellt).

*pDoc*<br/>
Ein Zeiger auf ein Dokument Objekt, dessen Inhalt in der Vorschau angezeigt wird.

### <a name="return-value"></a>Rückgabewert

Ein gültiger Zeiger auf ein `CFrameWnd` Objekt oder NULL, wenn die Erstellung fehlschlägt.

### <a name="remarks"></a>Bemerkungen

##  <a name="setpreviewinfo"></a>CDocTemplate:: setpreviewinfo

Richtet den Out-of-Process-Vorschau Handler ein.

```
void SetPreviewInfo(
    UINT nIDPreviewFrame,
    CRuntimeClass* pPreviewFrameClass = NULL,
    CRuntimeClass* pPreviewViewClass = NULL);
```

### <a name="parameters"></a>Parameter

*nidpreviewframe*<br/>
Gibt eine Ressourcen-ID des Vorschau Rahmens an.

*ppreviewframeclass*<br/>
Gibt einen Zeiger auf eine Lauf Zeit Klassen-Informationsstruktur des Vorschau Rahmens an.

*ppreviewviewclass*<br/>
Gibt einen Zeiger auf eine Lauf Zeit Klassen-Informationsstruktur der Vorschau Ansicht an.

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Weitere Informationen

[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CSingleDocTemplate-Klasse](../../mfc/reference/csingledoctemplate-class.md)<br/>
[CMultiDocTemplate-Klasse](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[CDocument-Klasse](../../mfc/reference/cdocument-class.md)<br/>
[CView-Klasse](../../mfc/reference/cview-class.md)<br/>
[CScrollView-Klasse](../../mfc/reference/cscrollview-class.md)<br/>
[CEditView-Klasse](../../mfc/reference/ceditview-class.md)<br/>
[CFormView-Klasse](../../mfc/reference/cformview-class.md)<br/>
[CFrameWnd-Klasse](../../mfc/reference/cframewnd-class.md)<br/>
[CMDIChildWnd-Klasse](../../mfc/reference/cmdichildwnd-class.md)
