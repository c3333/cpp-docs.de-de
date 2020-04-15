---
title: CDocument-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDocument
- AFXWIN/CDocument
- AFXWIN/CDocument::CDocument
- AFXWIN/CDocument::AddView
- AFXWIN/CDocument::BeginReadChunks
- AFXWIN/CDocument::CanCloseFrame
- AFXWIN/CDocument::ClearChunkList
- AFXWIN/CDocument::ClearPathName
- AFXWIN/CDocument::DeleteContents
- AFXWIN/CDocument::FindChunk
- AFXWIN/CDocument::GetAdapter
- AFXWIN/CDocument::GetDocTemplate
- AFXWIN/CDocument::GetFile
- AFXWIN/CDocument::GetFirstViewPosition
- AFXWIN/CDocument::GetNextView
- AFXWIN/CDocument::GetPathName
- AFXWIN/CDocument::GetThumbnail
- AFXWIN/CDocument::GetTitle
- AFXWIN/CDocument::InitializeSearchContent
- AFXWIN/CDocument::IsModified
- AFXWIN/CDocument::IsSearchAndOrganizeHandler
- AFXWIN/CDocument::LoadDocumentFromStream
- AFXWIN/CDocument::OnBeforeRichPreviewFontChanged
- AFXWIN/CDocument::OnChangedViewList
- AFXWIN/CDocument::OnCloseDocument
- AFXWIN/CDocument::OnCreatePreviewFrame
- AFXWIN/CDocument::OnDocumentEvent
- AFXWIN/CDocument::OnDrawThumbnail
- AFXWIN/CDocument::OnLoadDocumentFromStream
- AFXWIN/CDocument::OnNewDocument
- AFXWIN/CDocument::OnOpenDocument
- AFXWIN/CDocument::OnPreviewHandlerQueryFocus
- AFXWIN/CDocument::OnPreviewHandlerTranslateAccelerator
- AFXWIN/CDocument::OnRichPreviewBackColorChanged
- AFXWIN/CDocument::OnRichPreviewFontChanged
- AFXWIN/CDocument::OnRichPreviewSiteChanged
- AFXWIN/CDocument::OnRichPreviewTextColorChanged
- AFXWIN/CDocument::OnSaveDocument
- AFXWIN/CDocument::OnUnloadHandler
- AFXWIN/CDocument::PreCloseFrame
- AFXWIN/CDocument::ReadNextChunkValue
- AFXWIN/CDocument::ReleaseFile
- AFXWIN/CDocument::RemoveChunk
- AFXWIN/CDocument::RemoveView
- AFXWIN/CDocument::ReportSaveLoadException
- AFXWIN/CDocument::SaveModified
- AFXWIN/CDocument::SetChunkValue
- AFXWIN/CDocument::SetModifiedFlag
- AFXWIN/CDocument::SetPathName
- AFXWIN/CDocument::SetTitle
- AFXWIN/CDocument::UpdateAllViews
- AFXWIN/CDocument::OnFileSendMail
- AFXWIN/CDocument::OnUpdateFileSendMail
- AFXWIN/CDocument::m_bGetThumbnailMode
- AFXWIN/CDocument::m_bPreviewHandlerMode
- AFXWIN/CDocument::m_bSearchMode
- AFXWIN/CDocument::m_clrRichPreviewBackColor
- AFXWIN/CDocument::m_clrRichPreviewTextColor
- AFXWIN/CDocument::m_lfRichPreviewFont
helpviewer_keywords:
- CDocument [MFC], CDocument
- CDocument [MFC], AddView
- CDocument [MFC], BeginReadChunks
- CDocument [MFC], CanCloseFrame
- CDocument [MFC], ClearChunkList
- CDocument [MFC], ClearPathName
- CDocument [MFC], DeleteContents
- CDocument [MFC], FindChunk
- CDocument [MFC], GetAdapter
- CDocument [MFC], GetDocTemplate
- CDocument [MFC], GetFile
- CDocument [MFC], GetFirstViewPosition
- CDocument [MFC], GetNextView
- CDocument [MFC], GetPathName
- CDocument [MFC], GetThumbnail
- CDocument [MFC], GetTitle
- CDocument [MFC], InitializeSearchContent
- CDocument [MFC], IsModified
- CDocument [MFC], IsSearchAndOrganizeHandler
- CDocument [MFC], LoadDocumentFromStream
- CDocument [MFC], OnBeforeRichPreviewFontChanged
- CDocument [MFC], OnChangedViewList
- CDocument [MFC], OnCloseDocument
- CDocument [MFC], OnCreatePreviewFrame
- CDocument [MFC], OnDocumentEvent
- CDocument [MFC], OnDrawThumbnail
- CDocument [MFC], OnLoadDocumentFromStream
- CDocument [MFC], OnNewDocument
- CDocument [MFC], OnOpenDocument
- CDocument [MFC], OnPreviewHandlerQueryFocus
- CDocument [MFC], OnPreviewHandlerTranslateAccelerator
- CDocument [MFC], OnRichPreviewBackColorChanged
- CDocument [MFC], OnRichPreviewFontChanged
- CDocument [MFC], OnRichPreviewSiteChanged
- CDocument [MFC], OnRichPreviewTextColorChanged
- CDocument [MFC], OnSaveDocument
- CDocument [MFC], OnUnloadHandler
- CDocument [MFC], PreCloseFrame
- CDocument [MFC], ReadNextChunkValue
- CDocument [MFC], ReleaseFile
- CDocument [MFC], RemoveChunk
- CDocument [MFC], RemoveView
- CDocument [MFC], ReportSaveLoadException
- CDocument [MFC], SaveModified
- CDocument [MFC], SetChunkValue
- CDocument [MFC], SetModifiedFlag
- CDocument [MFC], SetPathName
- CDocument [MFC], SetTitle
- CDocument [MFC], UpdateAllViews
- CDocument [MFC], OnFileSendMail
- CDocument [MFC], OnUpdateFileSendMail
- CDocument [MFC], m_bGetThumbnailMode
- CDocument [MFC], m_bPreviewHandlerMode
- CDocument [MFC], m_bSearchMode
- CDocument [MFC], m_clrRichPreviewBackColor
- CDocument [MFC], m_clrRichPreviewTextColor
- CDocument [MFC], m_lfRichPreviewFont
ms.assetid: e5a2891d-e1e1-4599-8c7e-afa9b4945446
ms.openlocfilehash: 2f8ba8d0b35bd72efa8f8d63dbefd689e645d768
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374052"
---
# <a name="cdocument-class"></a>CDocument-Klasse

Stellt die grundlegende Funktionalität für benutzerdefinierte Dokumentklassen bereit.

## <a name="syntax"></a>Syntax

```
class CDocument : public CCmdTarget
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDocument::CDocument](#cdocument)|Erstellt ein `CDocument`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDocument::AddView](#addview)|Fügt dem Dokument eine Ansicht an.|
|[CDocument::BeginReadChunks](#beginreadchunks)|Initialisiert das Stücklesen.|
|[CDocument::CanCloseFrame](#cancloseframe)|Fortgeschrittene überschreibbare; vor dem Schließen eines Rahmenfensters aufgerufen werden, in dem dieses Dokument angezeigt wird.|
|[CDocument::ClearChunkList](#clearchunklist)|Löscht die Chunk-Liste.|
|[CDocument::ClearPathName](#clearpathname)|Löscht den Pfad des Dokumentobjekts.|
|[CDocument::DeleteContents](#deletecontents)|Wird aufgerufen, um die Bereinigung des Dokuments durchzuführen.|
|[CDocument::FindChunk](#findchunk)|Sucht nach einem Chunk mit der angegebenen GUID.|
|[CDocument::GetAdapter](#getadapter)|Gibt einen Zeiger auf `IDocument` die Objektimplementierungsschnittstelle zurück.|
|[CDocument::GetDocTemplate](#getdoctemplate)|Gibt einen Zeiger auf die Dokumentvorlage zurück, die den Typ des Dokuments beschreibt.|
|[CDocument::GetFile](#getfile)|Gibt einen Zeiger auf `CFile` das gewünschte Objekt zurück.|
|[CDocument::GetFirstViewPosition](#getfirstviewposition)|Gibt die Position der ersten in der Liste der Ansichten zurück. verwendet, um die Iteration zu beginnen.|
|[CDocument::GetNextView](#getnextview)|Durchgeht die Liste der Ansichten, die dem Dokument zugeordnet sind.|
|[CDocument::GetPathName](#getpathname)|Gibt den Pfad der Datendatei des Dokuments zurück.|
|[CDocument::GetThumbnail](#getthumbnail)|Wird aufgerufen, um eine Bitmap zu erstellen, die vom Miniaturansichtsanbieter zum Anzeigen der Miniaturansicht verwendet werden soll.|
|[CDocument::GetTitle](#gettitle)|Gibt den Titel des Dokuments zurück.|
|[CDocument::InitializeSearchContent](#initializesearchcontent)|Wird aufgerufen, um Suchinhalte für Search Handler zu initialisieren.|
|[CDocument::IsModified](#ismodified)|Gibt an, ob das Dokument seit dem letzten Speichern geändert wurde.|
|[CDocument::IsSearchAndOrganizeHandler](#issearchandorganizehandler)|Gibt an, `CDocument` ob diese Instanz des Objekts für Search & Organize-Handler erstellt wurde.|
|[CDocument::LoadDocumentFromStream](#loaddocumentfromstream)|Wird aufgerufen, um Dokumentdaten aus dem Stream zu laden.|
|[CDocument::OnBeforeRichPreviewfontChanged](#onbeforerichpreviewfontchanged)|Wird aufgerufen, bevor die Rich Preview-Schriftart geändert wird.|
|[CDocument::OnChangedViewList](#onchangedviewlist)|Wird aufgerufen, nachdem eine Ansicht dem Dokument hinzugefügt oder daraus entfernt wurde.|
|[CDocument::OnCloseDocument](#onclosedocument)|Wird aufgerufen, um das Dokument zu schließen.|
|[CDocument::OnCreatePreviewFrame](#oncreatepreviewframe)|Wird vom Framework aufgerufen, wenn es einen Vorschaurahmen für Rich Preview erstellen muss.|
|[CDocument::OnDocumentEvent](#ondocumentevent)|Wird vom Framework als Reaktion auf ein Dokumentereignis aufgerufen.|
|[CDocument::OnDrawThumbnail](#ondrawthumbnail)|Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um Deninhalt der Miniaturansicht zu zeichnen.|
|[CDocument::OnLoadDocumentFromStream](#onloaddocumentfromstream)|Wird vom Framework aufgerufen, wenn es die Dokumentdaten aus dem Stream laden muss.|
|[CDocument::OnNewDocument](#onnewdocument)|Wird aufgerufen, um ein neues Dokument zu erstellen.|
|[CDocument::OnOpenDocument](#onopendocument)|Wird aufgerufen, um ein vorhandenes Dokument zu öffnen.|
|[CDocument::OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|Weist den Vorschauhandler an, die HWND vom Aufrufen der GetFocus-Funktion zurückzugeben.|
|[CDocument::OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|Weist den Vorschauhandler an, einen Tastenanschlag zu verarbeiten, der von der Nachrichtenpumpe des Prozesses übergeben wird, in dem der Vorschauhandler ausgeführt wird.|
|[CDocument::OnRichPreviewBackColorChanged](#onrichpreviewbackcolorchanged)|Wird aufgerufen, wenn sich die Hintergrundfarbe der Rich Preview geändert hat.|
|[CDocument::OnRichPreviewFontChanged](#onrichpreviewfontchanged)|Wird aufgerufen, wenn die Rich Preview-Schriftart geändert wurde.|
|[CDocument::OnRichPreviewSiteChanged](#onrichpreviewsitechanged)|Wird aufgerufen, wenn die Rich Preview-Website geändert wurde.|
|[CDocument::OnRichPreviewTextColorChanged](#onrichpreviewtextcolorchanged)|Wird aufgerufen, wenn sich die Textfarbe der Rich Preview geändert hat.|
|[CDocument::OnSaveDocument](#onsavedocument)|Wird aufgerufen, um das Dokument auf dem Datenträger zu speichern.|
|[CDocument::OnUnloadHandler](#onunloadhandler)|Wird vom Framework aufgerufen, wenn der Vorschauhandler entladen wird.|
|[CDocument::PreCloseFrame](#precloseframe)|Wird aufgerufen, bevor das Rahmenfenster geschlossen wird.|
|[CDocument::ReadNextChunkValue](#readnextchunkvalue)|Liest den nächsten Chunk-Wert.|
|[CDocument::ReleaseFile](#releasefile)|Gibt eine Datei frei, um sie für andere Anwendungen verfügbar zu machen.|
|[CDocument::RemoveChunk](#removechunk)|Entfernt einen Chunk mit der angegebenen GUID.|
|[CDocument::RemoveView](#removeview)|Trennt eine Ansicht aus dem Dokument.|
|[CDocument::ReportSaveLoadException](#reportsaveloadexception)|Fortgeschrittene überschreibbare; wird aufgerufen, wenn ein Öffnungs- oder Speichervorgang aufgrund einer Ausnahme nicht abgeschlossen werden kann.|
|[CDocument::SaveModified](#savemodified)|Fortgeschrittene überschreibbare; , um den Benutzer zu fragen, ob das Dokument gespeichert werden soll.|
|[CDocument::SetChunkValue](#setchunkvalue)|Legt einen Chunk-Wert fest.|
|[CDocument::SetModifiedFlag](#setmodifiedflag)|Legt ein Flag fest, das angibt, dass Sie das Dokument seit dem letzten Speichern geändert haben.|
|[CDocument::SetPathName](#setpathname)|Legt den Pfad der vom Dokument verwendeten Datendatei fest.|
|[CDocument::SetTitle](#settitle)|Legt den Titel des Dokuments fest.|
|[CDocument::UpdateAllViews](#updateallviews)|Benachrichtigt alle Ansichten, dass das Dokument geändert wurde.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDocument::OnFileSendMail](#onfilesendmail)|Sendet eine E-Mail-Nachricht mit dem angehängten Dokument.|
|[CDocument::OnUpdateFileSendMail](#onupdatefilesendmail)|Aktiviert den Befehl E-Mail senden, wenn E-Mail-Support vorhanden ist.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDocument::m_bGetThumbnailMode](#m_bgetthumbnailmode)|Gibt an, dass das `CDocument` Objekt von dllhost für Miniaturansichten erstellt wurde. Sollte eingecheckt `CView::OnDraw`werden.|
|[CDocument::m_bPreviewHandlerMode](#m_bpreviewhandlermode)|Gibt an, dass das `CDocument` Objekt `Rich Preview`von prevhost für erstellt wurde. Sollte eingecheckt `CView::OnDraw`werden.|
|[CDocument::m_bSearchMode](#m_bsearchmode)|Gibt an, dass das `CDocument` Objekt von einem Indexer oder einer anderen Suchanwendung erstellt wurde.|
|[CDocument::m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|Gibt die Hintergrundfarbe des Rich Preview-Fensters an. Diese Farbe wird vom Host festgelegt.|
|[CDocument::m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|Gibt die Vordergrundfarbe des Rich-Vorschaufensters an. Diese Farbe wird vom Host festgelegt.|
|[CDocument::m_lfRichPreviewFont](#m_lfrichpreviewfont)|Gibt die Textschriftart für das Rich-Vorschaufenster an. Diese Schriftartinformationen werden vom Host festgelegt.|

## <a name="remarks"></a>Bemerkungen

Ein Dokument stellt die Dateneinheit dar, die der Benutzer normalerweise mit dem Befehl Dateiöffnen öffnet und mit dem Befehl Dateispeichern speichert.

`CDocument`unterstützt Standardvorgänge wie das Erstellen, Laden und Speichern eines Dokuments. Das Framework bearbeitet Dokumente mithilfe `CDocument`der von definierten Schnittstelle.

Eine Anwendung kann mehr als einen Dokumenttyp unterstützen. Eine Anwendung kann z. B. sowohl Tabellenkalkulationen als auch Textdokumente unterstützen. Jedem Dokumenttyp ist eine Dokumentvorlage zugeordnet. Die Dokumentvorlage gibt an, welche Ressourcen (z. B. Menü, Symbol oder Beschleunigertabelle) für diesen Dokumenttyp verwendet werden. Jedes Dokument enthält einen Zeiger `CDocTemplate` auf das zugeordnete Objekt.

Benutzer interagieren mit einem Dokument über die ihm zugeordneten [CView-Objekte.](../../mfc/reference/cview-class.md) Eine Ansicht rendert ein Bild des Dokuments in einem Rahmenfenster und interpretiert Benutzereingaben als Vorgänge für das Dokument. Einem Dokument können mehrere Ansichten zugeordnet sein. Wenn der Benutzer ein Fenster in einem Dokument öffnet, erstellt das Framework eine Ansicht und fügt sie an das Dokument an. Die Dokumentvorlage gibt an, welche Art von Ansicht und Rahmenfenster zum Anzeigen der einzelnen Dokumenttypen verwendet werden.

Dokumente sind Teil des Standardbefehlsroutings des Frameworks und erhalten daher Befehle von Standardkomponenten der Benutzeroberfläche (z. B. dem Menüpunkt Dateispeichern). Ein Dokument empfängt Befehle, die von der aktiven Ansicht weitergeleitet werden. Wenn das Dokument einen bestimmten Befehl nicht verarbeitet, leitet es den Befehl an die Dokumentvorlage weiter, die es verwaltet.

Wenn die Daten eines Dokuments geändert werden, muss jede seiner Ansichten diese Änderungen widerspiegeln. `CDocument`stellt die [UpdateAllViews-Memberfunktion](#updateallviews) bereit, mit der Sie die Ansichten über solche Änderungen benachrichtigen können, damit sich die Ansichten bei Bedarf neu zeichnen können. Das Framework fordert den Benutzer außerdem auf, eine geänderte Datei vor dem Schließen zu speichern.

Um Dokumente in einer typischen Anwendung zu implementieren, müssen Sie die folgenden Schritte ausführen:

- Leiten Sie eine `CDocument` Klasse für jeden Dokumenttyp ab.

- Fügen Sie Membervariablen hinzu, um die Daten jedes Dokuments zu speichern.

- Implementieren Sie Memberfunktionen zum Lesen und Ändern der Dokumentdaten. Die Ansichten des Dokuments sind die wichtigsten Benutzer dieser Memberfunktionen.

- Überschreiben Sie die [CObject::Serialize-Memberfunktion](../../mfc/reference/cobject-class.md#serialize) in Ihrer Dokumentklasse, um die Daten des Dokuments auf und von der Festplatte zu schreiben und zu lesen.

`CDocument`unterstützt das Versenden Ihres Dokuments per E-Mail, wenn E-Mail-Support (MAPI) vorhanden ist. Siehe die Artikel [MAPI](../../mfc/mapi.md) und [MAPI Support in MFC](../../mfc/mapi-support-in-mfc.md).

Weitere Informationen `CDocument`zu finden Sie unter [Serialisierung](../../mfc/serialization-in-mfc.md), [Dokument-/Ansichtsarchitekturthemen](../../mfc/document-view-architecture.md)und [Dokument-/Ansichtserstellung](../../mfc/document-view-creation.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocument`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="cdocumentaddview"></a><a name="addview"></a>CDocument::AddView

Rufen Sie diese Funktion auf, um dem Dokument eine Ansicht anzufügen.

```
void AddView(CView* pView);
```

### <a name="parameters"></a>Parameter

*Pview*<br/>
Zeigt auf die hinzugefügte Ansicht.

### <a name="remarks"></a>Bemerkungen

Diese Funktion fügt die angegebene Ansicht der Liste der Ansichten hinzu, die dem Dokument zugeordnet sind. Die Funktion legt auch den Dokumentzeiger der Ansicht auf dieses Dokument fest. Das Framework ruft diese Funktion auf, wenn ein neu erstelltes Ansichtsobjekt an ein Dokument angefügt wird. Dies geschieht als Reaktion auf einen Befehl "Datei neu", "Datei geöffnet" oder "Neues Fenster" oder wenn ein Splitterfenster geteilt wird.

Rufen Sie diese Funktion nur auf, wenn Sie eine Ansicht manuell erstellen und anfügen. In der Regel lassen Sie das Framework Dokumente und Ansichten verbinden, indem Sie ein [CDocTemplate-Objekt](../../mfc/reference/cdoctemplate-class.md) definieren, um eine Dokumentklasse, Eine Ansichtsklasse und eine Rahmenfensterklasse zuzuordnen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]

## <a name="cdocumentbeginreadchunks"></a><a name="beginreadchunks"></a>CDocument::BeginReadChunks

Initialisiert das Stücklesen.

```
virtual void BeginReadChunks ();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cdocumentcancloseframe"></a><a name="cancloseframe"></a>CDocument::CanCloseFrame

Wird vom Framework aufgerufen, bevor ein Rahmenfenster, in dem das Dokument angezeigt wird, geschlossen wird.

```
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Parameter

*pFrame*<br/>
Zeigt auf das Rahmenfenster einer Ansicht, die dem Dokument zugeordnet ist.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Rahmenfenster sicher geschlossen werden kann. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung überprüft, ob andere Rahmenfenster das Dokument anzeigen. Wenn das angegebene Rahmenfenster das letzte ist, in dem das Dokument angezeigt wird, fordert die Funktion den Benutzer auf, das Dokument zu speichern, wenn es geändert wurde. Überschreiben Sie diese Funktion, wenn Sie eine spezielle Verarbeitung durchführen möchten, wenn ein Rahmenfenster geschlossen wird. Dies ist ein fortgeschrittenes Überridable.

## <a name="cdocumentcdocument"></a><a name="cdocument"></a>CDocument::CDocument

Erstellt ein `CDocument`-Objekt.

```
CDocument();
```

### <a name="remarks"></a>Bemerkungen

Das Framework verarbeitet die Dokumenterstellung für Sie. Überschreiben Sie die [OnNewDocument-Memberfunktion,](#onnewdocument) um die Initialisierung pro Dokument durchzuführen. Dies ist besonders wichtig bei SDI-Anwendungen (Single Document Interface).

## <a name="cdocumentclearchunklist"></a><a name="clearchunklist"></a>CDocument::ClearChunkList

Löscht die Chunk-Liste.

```
virtual void ClearChunkList ();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cdocumentclearpathname"></a><a name="clearpathname"></a>CDocument::ClearPathName

Löscht den Pfad des Dokumentobjekts.

```
virtual void ClearPathName();
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie den `CDocument` Pfad von einem Objekt löschen, fordert die Anwendung den Benutzer auf, wenn das Dokument das nächste Jahr gespeichert wird. Dadurch verhält sich ein **Save-Befehl** wie ein **Save-As-Befehl.**

## <a name="cdocumentdeletecontents"></a><a name="deletecontents"></a>CDocument::DeleteContents

Wird vom Framework aufgerufen, um die Daten `CDocument` des Dokuments zu löschen, ohne das Objekt selbst zu zerstören.

```
virtual void DeleteContents();
```

### <a name="remarks"></a>Bemerkungen

Es wird kurz vor der Vernichtung des Dokuments aufgerufen. Es wird auch aufgerufen, um sicherzustellen, dass ein Dokument leer ist, bevor es wiederverwendet wird. Dies ist besonders wichtig für eine SDI-Anwendung, die nur ein Dokument verwendet. Das Dokument wird wiederverwendet, wenn der Benutzer ein anderes Dokument erstellt oder öffnet. Rufen Sie diese Funktion auf, um einen Befehl "Alle löschen" oder einen ähnlichen Befehl zu implementieren, der alle Dokumentdaten löscht. Bei der Standardimplementierung dieser Funktion wird keine Aktion ausgeführt. Überschreiben Sie diese Funktion, um die Daten in Ihrem Dokument zu löschen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]

## <a name="cdocumentfindchunk"></a><a name="findchunk"></a>CDocument::FindChunk

Sucht nach einem Chunk mit einer angegebenen GUID.

```
virtual POSITION FindChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Parameter

*guid*<br/>
Gibt die GUID eines zu suchenden Abschnitts an.

*pid*<br/>
Gibt eine PID eines zu suchenden Blocks an.

### <a name="return-value"></a>Rückgabewert

Positionieren Sie die interne Chunk-Liste, falls dies erfolgreich ist. Andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

## <a name="cdocumentgetadapter"></a><a name="getadapter"></a>CDocument::GetAdapter

Gibt einen Zeiger auf ein `IDocument` Objekt zurück, das die Schnittstelle implementiert.

```
virtual ATL::IDocument* GetAdapter();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein `IDocument` Objekt, das die Schnittstelle implementiert.

### <a name="remarks"></a>Bemerkungen

## <a name="cdocumentgetdoctemplate"></a><a name="getdoctemplate"></a>CDocument::GetDocTemplate

Rufen Sie diese Funktion auf, um einen Zeiger auf die Dokumentvorlage für diesen Dokumenttyp abzurufen.

```
CDocTemplate* GetDocTemplate() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die Dokumentvorlage für diesen Dokumenttyp oder NULL, wenn das Dokument nicht von einer Dokumentvorlage verwaltet wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]

## <a name="cdocumentgetfile"></a><a name="getfile"></a>CDocument::GetFile

Rufen Sie diese Memberfunktion auf, `CFile` um einen Zeiger auf ein Objekt abzurufen.

```
virtual CFile* GetFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError);
```

### <a name="parameters"></a>Parameter

*lpszFileName*<br/>
Eine Zeichenfolge, die den Pfad zur gewünschten Datei ist. Der Pfad kann relativ oder absolut sein.

*pError*<br/>
Ein Zeiger auf ein vorhandenes Dateiausnahmeobjekt, das den Abschlussstatus des Vorgangs angibt.

*nOpenFlags*<br/>
Freigabe- und Zugriffsmodus. Gibt die Aktion an, die beim Öffnen der Datei zu ergreifen ist. Sie können die im CFile-Konstruktor [CFile::CFile](../../mfc/reference/cfile-class.md#cfile) aufgeführten Optionen mithilfe des operator bitweiser ODER (&#124;) kombinieren. Eine Zugriffsberechtigung und eine Freigabeoption sind erforderlich. und `modeCreate` `modeNoInherit` Modi sind optional.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein `CFile`-Objekt.

## <a name="cdocumentgetfirstviewposition"></a><a name="getfirstviewposition"></a>CDocument::GetFirstViewPosition

Rufen Sie diese Funktion auf, um die Position der ersten Ansicht in der Liste der Ansichten abzurufen, die dem Dokument zugeordnet sind.

```
virtual POSITION GetFirstViewPosition() const;
```

### <a name="return-value"></a>Rückgabewert

Ein POSITION-Wert, der für die Iteration mit der [GetNextView-Memberfunktion](#getnextview) verwendet werden kann.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

## <a name="cdocumentgetnextview"></a><a name="getnextview"></a>CDocument::GetNextView

Rufen Sie diese Funktion auf, um alle Ansichten des Dokuments zu durchlaufen.

```
virtual CView* GetNextView(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parameter

*Rposition*<br/>
Ein Verweis auf einen POSITION-Wert, `GetNextView` der von einem vorherigen Aufruf der oder [GetFirstViewPosition-Memberfunktionen](#getfirstviewposition) zurückgegeben wird. Dieser Wert darf nicht NULL sein.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die Ansicht, die durch *rPosition*identifiziert wird.

### <a name="remarks"></a>Bemerkungen

Die Funktion gibt die durch *rPosition* identifizierte Ansicht zurück und legt dann *rPosition* auf den POSITION-Wert der nächsten Ansicht in der Liste fest. Wenn die abgerufene Ansicht die letzte in der Liste ist, wird *rPosition* auf NULL gesetzt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

## <a name="cdocumentgetpathname"></a><a name="getpathname"></a>CDocument::GetPathName

Rufen Sie diese Funktion auf, um den vollqualifizierten Pfad der Datenträgerdatei des Dokuments abzurufen.

```
const CString& GetPathName() const;
```

### <a name="return-value"></a>Rückgabewert

Der vollqualifizierte Pfad des Dokuments. Diese Zeichenfolge ist leer, wenn dem Dokument nicht oder keine Datenträgerdatei zugeordnet ist.

## <a name="cdocumentgetthumbnail"></a><a name="getthumbnail"></a>CDocument::GetThumbnail

Erstellt eine Bitmap, die vom Miniaturansichtsanbieter zum Anzeigen der Miniaturansicht verwendet werden soll.

```
virtual BOOL GetThumbnail(
    UINT cx,
    HBITMAP* phbmp,
    DWORD* pdwAlpha);
```

### <a name="parameters"></a>Parameter

*Cx*<br/>
Gibt die Breite und Höhe der Bitmap an.

*phbmp*<br/>
Enthält ein Handle für eine Bitmap, wenn die Funktion erfolgreich zurückgegeben wird.

*pdwAlpha*<br/>
Enthält ein DWORD, das den Alphakanalwert angibt, wenn die Funktion erfolgreich zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn eine Bitmap für die Miniaturansicht erfolgreich erstellt wurde. andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cdocumentgettitle"></a><a name="gettitle"></a>CDocument::GetTitle

Rufen Sie diese Funktion auf, um den Titel des Dokuments abzurufen, der normalerweise vom Dateinamen des Dokuments abgeleitet wird.

```
const CString& GetTitle() const;
```

### <a name="return-value"></a>Rückgabewert

Der Titel des Dokuments.

## <a name="cdocumentinitializesearchcontent"></a><a name="initializesearchcontent"></a>CDocument::InitializeSearchContent

Wird aufgerufen, um Suchinhalte für den Suchhandler zu initialisieren.

```
virtual void InitializeSearchContent ();
```

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um Suchinhalt zu initialisieren. Der Inhalt sollte eine Zeichenfolge sein, deren Teile durch ";" begrenzt sind. Beispiel: "Punkt; Rechteck; ole item".

## <a name="cdocumentismodified"></a><a name="ismodified"></a>CDocument::IsModified

Rufen Sie diese Funktion auf, um zu bestimmen, ob das Dokument seit dem letzten Speichern geändert wurde.

```
virtual BOOL IsModified();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Dokument seit dem letzten Speichern geändert wurde. andernfalls 0.

## <a name="cdocumentissearchandorganizehandler"></a><a name="issearchandorganizehandler"></a>CDocument::IsSearchAndOrganizeHandler

Gibt an, `CDocument` ob diese Instanz von für den Search & Organize-Handler erstellt wurde.

```
BOOL IsSearchAndOrganizeHandler() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, `CDocument` wenn diese Instanz von für den Search & Organize-Handler erstellt wurde.

### <a name="remarks"></a>Bemerkungen

Derzeit gibt diese Funktion TRUE nur für Rich Preview-Handler zurück, die in einem Nicht-Prozessserver implementiert sind. Sie können die entsprechenden Flags (m_bPreviewHandlerMode, m_bSearchMode, m_bGetThumbnailMode) auf Anwendungsebene festlegen, damit diese Funktion TRUE zurückgibt.

## <a name="cdocumentloaddocumentfromstream"></a><a name="loaddocumentfromstream"></a>CDocument::LoadDocumentFromStream

Wird aufgerufen, um Dokumentdaten aus einem Stream zu laden.

```
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,
    DWORD dwGrfMode);
```

### <a name="parameters"></a>Parameter

*pStream*<br/>
Ein Zeiger auf einen Stream. Dieser Stream wird von der Shell bereitgestellt.

*dwGrfMode*<br/>
Zugriffsmodus auf den Stream.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn der Ladevorgang erfolgreich ist, andernfalls HRESULT mit einem Fehlercode.

### <a name="remarks"></a>Bemerkungen

Sie können diese Methode in einer abgeleiteten Klasse überschreiben, um anzupassen, wie Daten aus dem Stream geladen werden.

## <a name="cdocumentm_bgetthumbnailmode"></a><a name="m_bgetthumbnailmode"></a>CDocument::m_bGetThumbnailMode

Gibt an, `CDocument` dass das Objekt von dllhost für Miniaturansichten erstellt wurde. Sollte eingecheckt `CView::OnDraw`werden.

```
BOOL m_bGetThumbnailMode;
```

### <a name="remarks"></a>Bemerkungen

`TRUE`gibt an, dass das Dokument von dllhost für Miniaturansichten erstellt wurde.

## <a name="cdocumentm_bpreviewhandlermode"></a><a name="m_bpreviewhandlermode"></a>CDocument::m_bPreviewHandlerMode

Gibt an, `CDocument` dass das Objekt von prevhost for Rich Preview erstellt wurde. Sollte eingecheckt `CView::OnDraw`werden.

```
BOOL m_bPreviewHandlerMode;
```

### <a name="remarks"></a>Bemerkungen

TRUE gibt an, dass das Dokument von prevhost for Rich Preview erstellt wurde.

## <a name="cdocumentm_bsearchmode"></a><a name="m_bsearchmode"></a>CDocument::m_bSearchMode

Gibt an, `CDocument` dass das Objekt von einem Indexer oder einer anderen Suchanwendung erstellt wurde.

```
BOOL m_bSearchMode;
```

### <a name="remarks"></a>Bemerkungen

`TRUE`gibt an, dass das Dokument von einem Indexer oder einer anderen Suchanwendung erstellt wurde.

## <a name="cdocumentm_clrrichpreviewbackcolor"></a><a name="m_clrrichpreviewbackcolor"></a>CDocument::m_clrRichPreviewBackColor

Gibt die Hintergrundfarbe des Rich Preview-Fensters an. Diese Farbe wird vom Host festgelegt.

```
COLORREF m_clrRichPreviewBackColor;
```

### <a name="remarks"></a>Bemerkungen

## <a name="cdocumentm_clrrichpreviewtextcolor"></a><a name="m_clrrichpreviewtextcolor"></a>CDocument::m_clrRichPreviewTextColor

Gibt die Vordergrundfarbe des Rich Preview-Fensters an. Diese Farbe wird vom Host festgelegt.

```
COLORREF m_clrRichPreviewTextColor;
```

### <a name="remarks"></a>Bemerkungen

## <a name="cdocumentm_lfrichpreviewfont"></a><a name="m_lfrichpreviewfont"></a>CDocument::m_lfRichPreviewFont

Gibt die Textschriftart für das Rich-Vorschaufenster an. Diese Schriftartinformationen werden vom Host festgelegt.

```
CFont m_lfRichPreviewFont;
```

### <a name="remarks"></a>Bemerkungen

## <a name="cdocumentonbeforerichpreviewfontchanged"></a><a name="onbeforerichpreviewfontchanged"></a>CDocument::OnBeforeRichPreviewfontChanged

Wird aufgerufen, bevor die Rich Preview-Schriftart geändert wird.

```
virtual void OnBeforeRichPreviewFontChanged();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cdocumentonchangedviewlist"></a><a name="onchangedviewlist"></a>CDocument::OnChangedViewList

Wird vom Framework aufgerufen, nachdem eine Ansicht dem Dokument hinzugefügt oder daraus entfernt wurde.

```
virtual void OnChangedViewList();
```

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung dieser Funktion prüft, ob die letzte Ansicht entfernt wird, und löscht ggf. das Dokument. Überschreiben Sie diese Funktion, wenn Sie eine spezielle Verarbeitung durchführen möchten, wenn das Framework eine Ansicht hinzufügt oder entfernt. Wenn Sie z. B. möchten, dass ein Dokument geöffnet bleibt, auch wenn ihm keine Ansichten zugeordnet sind, überschreiben Sie diese Funktion.

## <a name="cdocumentonclosedocument"></a><a name="onclosedocument"></a>CDocument::OnCloseDocument

Wird vom Framework aufgerufen, wenn das Dokument geschlossen wird, in der Regel als Teil des Befehls "Dateischließen".

```
virtual void OnCloseDocument();
```

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung dieser Funktion zerstört alle Frames, die zum Anzeigen des Dokuments verwendet werden, schließt die Ansicht, bereinigt den Inhalt des Dokuments und ruft dann die [Memberfunktion DeleteContents](#deletecontents) auf, um die Daten des Dokuments zu löschen.

Überschreiben Sie diese Funktion, wenn Sie eine spezielle Bereinigungsverarbeitung durchführen möchten, wenn das Framework ein Dokument schließt. Wenn das Dokument z. B. einen Datensatz in einer Datenbank darstellt, sollten Sie diese Funktion überschreiben, um die Datenbank zu schließen. Sie sollten die Basisklassenversion dieser Funktion über Ihre Außerkraftsetzung aufrufen.

## <a name="cdocumentoncreatepreviewframe"></a><a name="oncreatepreviewframe"></a>CDocument::OnCreatePreviewFrame

Wird vom Framework aufgerufen, wenn es einen Vorschaurahmen für Rich Preview erstellen muss.

```
virtual BOOL OnCreatePreviewFrame();
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn der Frame erfolgreich erstellt wurde. andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cdocumentondocumentevent"></a><a name="ondocumentevent"></a>CDocument::OnDocumentEvent

Wird vom Framework als Reaktion auf ein Dokumentereignis aufgerufen.

```
virtual void OnDocumentEvent(DocumentEvent deEvent);
```

### <a name="parameters"></a>Parameter

*deEvent*<br/>
[in] Ein aufgezählter Datentyp, der den Ereignistyp beschreibt.

### <a name="remarks"></a>Bemerkungen

Dokumentereignisse können mehrere Klassen betreffen. Diese Methode ist für die Behandlung von Dokumentereignissen verantwortlich, die sich auf andere Klassen als die [CDocument-Klasse](../../mfc/reference/cdocument-class.md)auswirken. Derzeit ist die einzige Klasse, die auf Dokumentereignisse reagieren muss, die [CDataRecoveryHandler-Klasse](../../mfc/reference/cdatarecoveryhandler-class.md). Die `CDocument` Klasse verfügt über andere überschreibbare Methoden, die für die Behandlung der Auswirkungen auf die `CDocument`verantwortlich sind.

In der folgenden Tabelle sind die möglichen Werte für *deEvent* und die Ereignisse aufgeführt, denen sie entsprechen.

|Wert|Entsprechendes Ereignis|
|-----------|-------------------------|
|`onAfterNewDocument`|Ein neues Dokument wurde erstellt.|
|`onAfterOpenDocument`|Ein neues Dokument wurde geöffnet.|
|`onAfterSaveDocument`|Das Dokument wurde gespeichert.|
|`onAfterCloseDocument`|Das Dokument wurde geschlossen.|

## <a name="cdocumentondrawthumbnail"></a><a name="ondrawthumbnail"></a>CDocument::OnDrawThumbnail

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um die Miniaturansicht zu zeichnen.

```
virtual void OnDrawThumbnail(
    CDC& dc,
    LPRECT lprcBounds);
```

### <a name="parameters"></a>Parameter

*Dc*<br/>
Ein Verweis auf einen Gerätekontext.

*lprcBounds*<br/>
Gibt ein umgrenzendes Rechteck des Bereichs an, in dem die Miniaturansicht gezeichnet werden soll.

### <a name="remarks"></a>Bemerkungen

## <a name="cdocumentonfilesendmail"></a><a name="onfilesendmail"></a>CDocument::OnFileSendMail

Sendet eine Nachricht über den residenten E-Mail-Host (falls vorhanden) mit dem Dokument als Anlage.

```
void OnFileSendMail();
```

### <a name="remarks"></a>Bemerkungen

`OnFileSendMail`ruft [OnSaveDocument](#onsavedocument) auf, um unbenannte und geänderte Dokumente in eine temporäre Datei zu serialisieren (speichern), die dann per E-Mail gesendet wird. Wenn das Dokument nicht geändert wurde, wird keine temporäre Datei benötigt. das Original gesendet wird. `OnFileSendMail`lädt MAPI32. DLL, wenn sie noch nicht geladen wurde.

Eine spezielle `OnFileSendMail` Implementierung von für [COleDocument](../../mfc/reference/coledocument-class.md) verarbeitet zusammengesetzte Dateien korrekt.

`CDocument`unterstützt das Versenden Ihres Dokuments per E-Mail, wenn E-Mail-Support (MAPI) vorhanden ist. Weitere Informationen finden Sie in den Artikeln [MAPI Topics](../../mfc/mapi.md) und [MAPI Support in MFC](../../mfc/mapi-support-in-mfc.md).

## <a name="cdocumentonloaddocumentfromstream"></a><a name="onloaddocumentfromstream"></a>CDocument::OnLoadDocumentFromStream

Wird vom Framework aufgerufen, wenn es die Dokumentdaten aus einem Stream laden muss.

```
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,
    DWORD grfMode);
```

### <a name="parameters"></a>Parameter

*pStream*<br/>
Ein Zeiger auf einen eingehenden Stream.

*grfMode*<br/>
Zugriffsmodus auf den Stream.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn die Last erfolgreich ist; andernfalls ein Fehlercode.

### <a name="remarks"></a>Bemerkungen

## <a name="cdocumentonnewdocument"></a><a name="onnewdocument"></a>CDocument::OnNewDocument

Wird vom Framework als Teil des Befehls Datei neu aufgerufen.

```
virtual BOOL OnNewDocument();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Dokument erfolgreich initialisiert wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung dieser Funktion ruft die [DeleteContents-Memberfunktion](#deletecontents) auf, um sicherzustellen, dass das Dokument leer ist, und markiert dann das neue Dokument als bereinigend. Überschreiben Sie diese Funktion, um die Datenstruktur für ein neues Dokument zu initialisieren. Sie sollten die Basisklassenversion dieser Funktion über Ihre Außerkraftsetzung aufrufen.

Wenn der Benutzer den Befehl "Neu speichern" in einer SDI-Anwendung auswählt, verwendet das Framework diese Funktion, um das vorhandene Dokument erneut zu initialisieren, anstatt ein neues Dokument zu erstellen. Wenn der Benutzer In einer MDI-Anwendung (Multiple Document Interface) Datei neu auswählt, erstellt das Framework jedes Mal ein neues Dokument und ruft diese Funktion dann auf, um es zu initialisieren. Sie müssen Ihren Initialisierungscode in dieser Funktion statt im Konstruktor platzieren, damit der Befehl Datei neu in SDI-Anwendungen wirksam ist.

Beachten Sie, dass `OnNewDocument` es Fälle gibt, in denen zweimal aufgerufen wird. Dies tritt auf, wenn das Dokument als ActiveX Document Server eingebettet ist. Die Funktion wird zuerst `CreateInstance` von der `COleObjectFactory`Methode aufgerufen (verfügbar durch die `InitNew` -derived-Klasse) und ein zweites Mal von der Methode (verfügbar durch die `COleServerDoc`-derived-Klasse).

### <a name="example"></a>Beispiel

Die folgenden Beispiele veranschaulichen alternative Methoden zum Initialisieren eines Dokumentobjekts.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

## <a name="cdocumentonopendocument"></a><a name="onopendocument"></a>CDocument::OnOpenDocument

Wird vom Framework als Teil des File Open-Befehls aufgerufen.

```
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parameter

*lpszPathName*<br/>
Zeigt auf den Pfad des zu öffnenden Dokuments.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Dokument erfolgreich geladen wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung dieser Funktion öffnet die angegebene Datei, ruft die [DeleteContents-Memberfunktion](#deletecontents) auf, um sicherzustellen, dass das Dokument leer ist, ruft [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) auf, um den Inhalt der Datei zu lesen, und markiert dann das Dokument als bereinigend. Überschreiben Sie diese Funktion, wenn Sie etwas anderes als den Archivierungsmechanismus oder den Dateimechanismus verwenden möchten. Sie können z. B. eine Anwendung schreiben, in der Dokumente Datensätze in einer Datenbank und nicht separate Dateien darstellen.

Wenn der Benutzer den Befehl Datei öffnen in einer SDI-Anwendung auswählt, `CDocument` verwendet das Framework diese Funktion, um das vorhandene Objekt erneut zu initialisieren, anstatt ein neues zu erstellen. Wenn der Benutzer Datei öffnen in einer MDI-Anwendung `CDocument` auswählt, erstellt das Framework jedes Mal ein neues Objekt und ruft diese Funktion dann auf, um es zu initialisieren. Sie müssen Ihren Initialisierungscode in dieser Funktion und nicht im Konstruktor platzieren, damit der Befehl Dateigeöffnet in SDI-Anwendungen wirksam ist.

### <a name="example"></a>Beispiel

Die folgenden Beispiele veranschaulichen alternative Methoden zum Initialisieren eines Dokumentobjekts.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

[!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]

## <a name="cdocumentonpreviewhandlerqueryfocus"></a><a name="onpreviewhandlerqueryfocus"></a>CDocument::OnPreviewHandlerQueryFocus

Weist den Vorschauhandler an, die HWND `GetFocus` zurückzugeben, die vom Aufrufen der Funktion abgerufen wurde.

```
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```

### <a name="parameters"></a>Parameter

*phwnd*<br/>
[out] Wenn diese Methode zurückgegeben wird, enthält einen Zeiger `GetFocus` auf die HWND, die vom Aufrufen der Funktion aus dem Vordergrundthread des Vorschauhandlers zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück, wenn erfolgreich; oder einen Fehlerwert.

### <a name="remarks"></a>Bemerkungen

## <a name="cdocumentonpreviewhandlertranslateaccelerator"></a><a name="onpreviewhandlertranslateaccelerator"></a>CDocument::OnPreviewHandlerTranslateAccelerator

Weist den Vorschauhandler an, einen Tastenanschlag zu verarbeiten, der von der Nachrichtenpumpe des Prozesses übergeben wird, in dem der Vorschauhandler ausgeführt wird.

```
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```

### <a name="parameters"></a>Parameter

*pmsg*<br/>
[in] Ein Zeiger auf eine Fensternachricht.

### <a name="return-value"></a>Rückgabewert

Wenn die Tastenanschlagnachricht vom Vorschauhandler verarbeitet werden kann, verarbeitet der Handler sie und gibt S_OK zurück. Wenn der Vorschauhandler die Tastenanschlagnachricht nicht verarbeiten kann, wird sie dem Host über `IPreviewHandlerFrame::TranslateAccelerator`angeboten. Wenn der Host die Nachricht verarbeitet, gibt diese Methode S_OK zurück. Wenn der Host die Nachricht nicht verarbeitet, gibt diese Methode S_FALSE zurück.

### <a name="remarks"></a>Bemerkungen

## <a name="cdocumentonrichpreviewbackcolorchanged"></a><a name="onrichpreviewbackcolorchanged"></a>CDocument::OnRichPreviewBackColorChanged

Wird aufgerufen, wenn sich die Hintergrundfarbe der Rich Preview geändert hat.

```
virtual void OnRichPreviewBackColorChanged();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cdocumentonrichpreviewfontchanged"></a><a name="onrichpreviewfontchanged"></a>CDocument::OnRichPreviewFontChanged

Wird aufgerufen, wenn sich die Rich Preview-Schriftart geändert hat.

```
virtual void OnRichPreviewFontChanged();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cdocumentonrichpreviewsitechanged"></a><a name="onrichpreviewsitechanged"></a>CDocument::OnRichPreviewSiteChanged

Wird aufgerufen, wenn sich die Rich Preview-Website geändert hat.

```
virtual void OnRichPreviewSiteChanged();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cdocumentonrichpreviewtextcolorchanged"></a><a name="onrichpreviewtextcolorchanged"></a>CDocument::OnRichPreviewTextColorChanged

Wird aufgerufen, wenn sich die Textfarbe "Rich Preview" geändert hat.

```
virtual void OnRichPreviewTextColorChanged();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cdocumentonsavedocument"></a><a name="onsavedocument"></a>CDocument::OnSaveDocument

Wird vom Framework als Teil des Befehls Datei speichern oder Speichern unter speichern aufgerufen.

```
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parameter

*lpszPathName*<br/>
Zeigt auf den vollqualifizierten Pfad, in dem die Datei gespeichert werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Dokument erfolgreich gespeichert wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung dieser Funktion öffnet die angegebene Datei, ruft [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) auf, um die Daten des Dokuments in die Datei zu schreiben, und markiert dann das Dokument als bereinigend. Überschreiben Sie diese Funktion, wenn Sie eine spezielle Verarbeitung durchführen möchten, wenn das Framework ein Dokument speichert. Sie können z. B. eine Anwendung schreiben, in der Dokumente Datensätze in einer Datenbank und nicht separate Dateien darstellen.

## <a name="cdocumentonunloadhandler"></a><a name="onunloadhandler"></a>CDocument::OnUnloadHandler

Wird vom Framework aufgerufen, wenn der Vorschauhandler entladen wird.

```
virtual void OnUnloadHandler();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cdocumentonupdatefilesendmail"></a><a name="onupdatefilesendmail"></a>CDocument::OnUpdateFileSendMail

Aktiviert den ID_FILE_SEND_MAIL Befehl, wenn Mail-Support (MAPI) vorhanden ist.

```
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parameter

*pCmdUI*<br/>
Ein Zeiger auf das [CCmdUI-Objekt,](../../mfc/reference/ccmdui-class.md) das dem Befehl ID_FILE_SEND_MAIL zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Andernfalls entfernt die Funktion den ID_FILE_SEND_MAIL Befehl aus dem Menü, einschließlich Trennzeichen oberhalb oder unterhalb des Menüelements. MAPI ist aktiviert, wenn MAPI32. DLL ist im Pfad und im Abschnitt [Mail] des WIN vorhanden. INI-Datei, MAPI=1. Die meisten Anwendungen setzen diesen Befehl in das Menü Datei.

`CDocument`unterstützt das Versenden Ihres Dokuments per E-Mail, wenn E-Mail-Support (MAPI) vorhanden ist. Weitere Informationen finden Sie in den Artikeln [MAPI Topics](../../mfc/mapi.md) und [MAPI Support in MFC](../../mfc/mapi-support-in-mfc.md).

## <a name="cdocumentprecloseframe"></a><a name="precloseframe"></a>CDocument::PreCloseFrame

Diese Memberfunktion wird vom Framework aufgerufen, bevor das Rahmenfenster zerstört wird.

```
virtual void PreCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Parameter

*pFrame*<br/>
Zeiger auf das [CFrameWnd,](../../mfc/reference/cframewnd-class.md) `CDocument` das das zugeordnete Objekt enthält.

### <a name="remarks"></a>Bemerkungen

Es kann überschrieben werden, um eine benutzerdefinierte Bereinigung bereitzustellen, aber achten Sie darauf, auch die Basisklasse aufzurufen.

Der Standardwert `PreCloseFrame` von `CDocument`tut nichts in . Die `CDocument`-abgeleiteten Klassen [COleDocument](../../mfc/reference/coledocument-class.md) und [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) verwenden diese Memberfunktion.

## <a name="cdocumentreadnextchunkvalue"></a><a name="readnextchunkvalue"></a>CDocument::ReadNextChunkValue

Liest den nächsten Chunk-Wert.

```
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```

### <a name="parameters"></a>Parameter

*ppValue*<br/>
[out] Wenn die Funktion zurückgegeben wird, enthält *ppValue* den Wert, der gelesen wurde.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

## <a name="cdocumentreleasefile"></a><a name="releasefile"></a>CDocument::ReleaseFile

Diese Memberfunktion wird vom Framework aufgerufen, um eine Datei freizugeben, sodass sie für andere Anwendungen verfügbar ist.

```
virtual void ReleaseFile(
    CFile* pFile,
    BOOL bAbort);
```

### <a name="parameters"></a>Parameter

*pFile*<br/>
Ein Zeiger auf das freizugebende CFile-Objekt.

*bAbort*<br/>
Gibt an, ob die Datei mithilfe `CFile::Close` `CFile::Abort`von oder freigegeben werden soll. FALSE, wenn die Datei mit [CFile::Close](../../mfc/reference/cfile-class.md#close)freigegeben werden soll; TRUE, wenn die Datei mit [CFile::Abort](../../mfc/reference/cfile-class.md#abort)freigegeben werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn *bAbort* TRUE `ReleaseFile` `CFile::Abort`ist, ruft , und die Datei wird freigegeben. `CFile::Abort`löst keine Ausnahme aus.

Wenn *bAbort* FALSE `ReleaseFile` `CFile::Close` ist, ruft die Datei auf und die Datei wird freigegeben.

Überschreiben Sie diese Memberfunktion, um eine Aktion des Benutzers zu verlangen, bevor die Datei freigegeben wird.

## <a name="cdocumentremovechunk"></a><a name="removechunk"></a>CDocument::RemoveChunk

Entfernt einen Chunk mit der angegebenen GUID.

```
virtual void RemoveChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Parameter

*Guid*<br/>
Gibt die GUID eines zu entfernenden Abschnitts an.

*Pid*<br/>
Gibt die PID eines zu entfernenden Abschnitts an.

### <a name="remarks"></a>Bemerkungen

## <a name="cdocumentremoveview"></a><a name="removeview"></a>CDocument::RemoveView

Rufen Sie diese Funktion auf, um eine Ansicht von einem Dokument zu trennen.

```
void RemoveView(CView* pView);
```

### <a name="parameters"></a>Parameter

*Pview*<br/>
Zeigt auf die Ansicht, die entfernt wird.

### <a name="remarks"></a>Bemerkungen

Diese Funktion entfernt die angegebene Ansicht aus der Liste der Ansichten, die dem Dokument zugeordnet sind. Außerdem wird der Dokumentzeiger der Ansicht auf NULL festgelegt. Diese Funktion wird vom Framework aufgerufen, wenn ein Rahmenfenster geschlossen oder ein Bereich eines Splitterfensters geschlossen wird.

Rufen Sie diese Funktion nur auf, wenn Sie eine Ansicht manuell trennen. In der Regel lassen Sie das Framework Dokumente und Ansichten trennen, indem Sie ein [CDocTemplate-Objekt](../../mfc/reference/cdoctemplate-class.md) definieren, um eine Dokumentklasse, Eine Ansichtsklasse und eine Rahmenfensterklasse zuzuordnen.

Im Beispiel unter [AddView](#addview) finden Sie eine Beispielimplementierung.

## <a name="cdocumentreportsaveloadexception"></a><a name="reportsaveloadexception"></a>CDocument::ReportSaveLoadException

Wird aufgerufen, wenn beim Speichern oder Laden des Dokuments eine Ausnahme ausgelöst wird (in der Regel eine [CFileException](../../mfc/reference/cfileexception-class.md) oder [CArchiveException](../../mfc/reference/carchiveexception-class.md)).

```
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,
    CException* e,
    BOOL bSaving,
    UINT nIDPDefault);
```

### <a name="parameters"></a>Parameter

*lpszPathName*<br/>
Zeigt auf den Namen des Dokuments, das gespeichert oder geladen wurde.

*E*<br/>
Zeigt auf die ausgelöste Ausnahme. Kann NULL sein.

*bSparen*<br/>
Flag, das angibt, welcher Vorgang ausgeführt wurde; Ungleich Null, wenn das Dokument gespeichert wurde, 0, wenn das Dokument geladen wurde.

*nIDPDefault*<br/>
Bezeichner der Fehlermeldung, die angezeigt werden soll, wenn die Funktion keine spezifischere angibt.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung untersucht das Ausnahmeobjekt und sucht nach einer Fehlermeldung, die die Ursache genau beschreibt. Wenn eine bestimmte Nachricht nicht gefunden wird oder *wenn e* NULL ist, wird die allgemeine Meldung verwendet, die durch den Parameter *nIDPDefault* angegeben wird. Die Funktion zeigt dann ein Meldungsfeld mit der Fehlermeldung an. Überschreiben Sie diese Funktion, wenn Sie zusätzliche, benutzerdefinierte Fehlermeldungen bereitstellen möchten. Dies ist ein fortgeschrittenes Überridable.

## <a name="cdocumentsavemodified"></a><a name="savemodified"></a>CDocument::SaveModified

Wird vom Framework aufgerufen, bevor ein geändertes Dokument geschlossen werden soll.

```
virtual BOOL SaveModified();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Dokument sicher fortgesetzt und geschlossen werden kann. 0, wenn das Dokument nicht geschlossen werden soll.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung dieser Funktion zeigt ein Meldungsfeld an, in dem der Benutzer gefragt wird, ob die Änderungen am Dokument gespeichert werden sollen, falls vorhanden. Überschreiben Sie diese Funktion, wenn Ihr Programm eine andere Eingabeaufforderung erfordert. Dies ist ein fortgeschrittenes Überridable.

## <a name="cdocumentsetchunkvalue"></a><a name="setchunkvalue"></a>CDocument::SetChunkValue

Legt einen Chunk-Wert fest.

```
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>Parameter

*pValue*<br/>
Gibt einen zu legenden Chunk-Wert an.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

## <a name="cdocumentsetmodifiedflag"></a><a name="setmodifiedflag"></a>CDocument::SetModifiedFlag

Rufen Sie diese Funktion auf, nachdem Sie Änderungen am Dokument vorgenommen haben.

```
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parameter

*bModified*<br/>
Flag, das angibt, ob das Dokument geändert wurde.

### <a name="remarks"></a>Bemerkungen

Indem Sie diese Funktion konsistent aufrufen, stellen Sie sicher, dass das Framework den Benutzer auffordert, Änderungen vor dem Schließen eines Dokuments zu speichern. In der Regel sollten Sie den Standardwert TRUE für den *Parameter bModified* verwenden. Um ein Dokument als sauber (unverändert) zu markieren, rufen Sie diese Funktion mit dem Wert FALSE auf.

## <a name="cdocumentsetpathname"></a><a name="setpathname"></a>CDocument::SetPathName

Rufen Sie diese Funktion auf, um den vollqualifizierten Pfad der Datenträgerdatei des Dokuments anzugeben.

```
virtual void SetPathName(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>Parameter

*lpszPathName*<br/>
Zeigt auf die Zeichenfolge, die als Pfad für das Dokument verwendet werden soll.

*bAddToMRU*<br/>
Bestimmt, ob der Dateiname der zuletzt verwendeten (MRU)-Dateiliste hinzugefügt wird. Wenn TRUE, wird der Dateiname hinzugefügt. wenn FALSE, wird es nicht hinzugefügt.

### <a name="remarks"></a>Bemerkungen

Abhängig vom Wert von *bAddToMRU* wird der Pfad der von der Anwendung verwalteten MRU-Liste hinzugefügt oder nicht hinzugefügt. Beachten Sie, dass einige Dokumente keiner Datenträgerdatei zugeordnet sind. Rufen Sie diese Funktion nur auf, wenn Sie die Standardimplementierung zum Öffnen und Speichern von Dateien überschreiben, die vom Framework verwendet werden.

## <a name="cdocumentsettitle"></a><a name="settitle"></a>CDocument::SetTitle

Rufen Sie diese Funktion auf, um den Titel des Dokuments anzugeben (die Zeichenfolge, die in der Titelleiste eines Rahmenfensters angezeigt wird).

```
virtual void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>Parameter

*lpszTitle*<br/>
Zeigt auf die Zeichenfolge, die als Titel des Dokuments verwendet werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn Sie diese Funktion aufrufen, werden die Titel aller Rahmenfenster aktualisiert, in denen das Dokument angezeigt wird.

## <a name="cdocumentupdateallviews"></a><a name="updateallviews"></a>CDocument::UpdateAllViews

Rufen Sie diese Funktion auf, nachdem das Dokument geändert wurde.

```
void UpdateAllViews(
    CView* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL);
```

### <a name="parameters"></a>Parameter

*pSender*<br/>
Zeigt auf die Ansicht, die das Dokument geändert hat, oder NULL, wenn alle Ansichten aktualisiert werden sollen.

*lHint*<br/>
Enthält Informationen zur Änderung.

*pHint*<br/>
Verweist auf ein Objekt, das Informationen über die Änderung speichert.

### <a name="remarks"></a>Bemerkungen

Sie sollten diese Funktion aufrufen, nachdem Sie die [SetModifiedFlag-Memberfunktion](#setmodifiedflag) aufrufen. Diese Funktion informiert jede dem Dokument zugeordnete Ansicht, mit Ausnahme der von *pSender*angegebenen Ansicht, dass das Dokument geändert wurde. Normalerweise rufen Sie diese Funktion aus Ihrer Ansichtsklasse auf, nachdem der Benutzer das Dokument über eine Ansicht geändert hat.

Diese Funktion ruft die [CView::OnUpdate-Memberfunktion](../../mfc/reference/cview-class.md#onupdate) für jede der Ansichten des Dokuments mit Ausnahme der sendenden Ansicht, übergeben *pHint* und *lHint*auf. Verwenden Sie diese Parameter, um Informationen zu den Ansichten über die am Dokument vorgenommenen Änderungen zu übermitteln. Sie können Informationen mit *lHint* und/oder [CObject](../../mfc/reference/cobject-class.md)definieren, um Informationen über die Änderungen zu speichern und ein Objekt dieser Klasse mit *pHint*zu übergeben. Überschreiben `CView::OnUpdate` Sie die Memberfunktion in Ihrer [CView](../../mfc/reference/cview-class.md)-derived-Klasse, um die Aktualisierung der Anzeige der Ansicht basierend auf den übergebenen Informationen zu optimieren.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel-NPP](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)<br/>
[CView-Klasse](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate-Klasse](../../mfc/reference/cdoctemplate-class.md)
