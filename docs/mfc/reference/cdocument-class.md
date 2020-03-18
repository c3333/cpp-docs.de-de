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
ms.openlocfilehash: 2d87ff67000fb5b70c0a5c965638875e6f50b22c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424458"
---
# <a name="cdocument-class"></a>CDocument-Klasse

Stellt die grundlegende Funktionalität für benutzerdefinierte Dokumentklassen bereit.

## <a name="syntax"></a>Syntax

```
class CDocument : public CCmdTarget
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CDocument:: CDocument](#cdocument)|Erstellt ein `CDocument`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CDocument:: AddView](#addview)|Fügt eine Ansicht an das Dokument an.|
|[CDocument:: BeginRead Blöcke](#beginreadchunks)|Initialisiert das Lesen von Blöcken.|
|[CDocument:: cancloseframe](#cancloseframe)|Erweiterte über schreibbar; wird aufgerufen, bevor ein Rahmen Fenster geschlossen wird, das dieses Dokument anzeigen.|
|[CDocument:: clearchunklist](#clearchunklist)|Löscht die Blockliste.|
|[CDocument:: clearpathname](#clearpathname)|Löscht den Pfad des Dokument Objekts.|
|[CDocument::D eletecontent](#deletecontents)|Wird aufgerufen, um die Bereinigung des Dokuments auszuführen.|
|[CDocument:: findchunk](#findchunk)|Sucht nach einem Block mit der angegebenen GUID.|
|[CDocument:: GetAdapter](#getadapter)|Gibt einen Zeiger auf ein Objekt zurück, das `IDocument` Schnittstelle implementiert.|
|[CDocument:: GetDocTemplate](#getdoctemplate)|Gibt einen Zeiger auf die Dokument Vorlage zurück, die den Typ des Dokuments beschreibt.|
|[CDocument:: GetFile](#getfile)|Gibt einen Zeiger auf das gewünschte `CFile` Objekt zurück.|
|[CDocument:: GetFirstViewPosition](#getfirstviewposition)|Gibt die Position der ersten in der Liste der Ansichten zurück. wird verwendet, um die Iterationen zu starten.|
|[CDocument:: GetNextView](#getnextview)|Durchläuft die Liste der Sichten, die dem Dokument zugeordnet sind.|
|[CDocument:: getPathname](#getpathname)|Gibt den Pfad der Datendatei des Dokuments zurück.|
|[CDocument:: getminiatur](#getthumbnail)|Wird aufgerufen, um eine Bitmap zu erstellen, die vom Miniatur Ansichts Anbieter verwendet wird, um Miniaturansichten anzuzeigen|
|[CDocument:: getTitle](#gettitle)|Gibt den Titel des Dokuments zurück.|
|[CDocument:: initializesearchcontent](#initializesearchcontent)|Wird aufgerufen, um den Such Inhalt für den Suchhandler zu initialisieren.|
|[CDocument:: IsModified](#ismodified)|Gibt an, ob das Dokument seit der letzten Speicherung geändert wurde.|
|[CDocument:: issearchandorganizehandler](#issearchandorganizehandler)|Gibt an, ob diese Instanz von `CDocument`-Objekt für Search & Organisations Handler erstellt wurde.|
|[CDocument:: loaddocumentfromstream](#loaddocumentfromstream)|Wird aufgerufen, um Dokument Daten aus dem Stream zu laden.|
|[CDocument:: onbeforerichpreviewfontchanged](#onbeforerichpreviewfontchanged)|Wird aufgerufen, bevor die Schriftart der großen Vorschau geändert wird.|
|[CDocument:: onchangedviewlist](#onchangedviewlist)|Wird aufgerufen, nachdem dem Dokument eine Ansicht hinzugefügt oder daraus entfernt wurde.|
|[CDocument:: onclosedocument](#onclosedocument)|Wird aufgerufen, um das Dokument zu schließen.|
|[CDocument:: onkreatepreviewframe](#oncreatepreviewframe)|Wird von Framework aufgerufen, wenn es einen Vorschau Rahmen für eine umfangreiche Vorschauversion erstellen muss.|
|[CDocument:: ondocumentevent](#ondocumentevent)|Wird von Framework als Reaktion auf ein Dokument Ereignis aufgerufen.|
|[CDocument:: ondrawminiatur](#ondrawthumbnail)|Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um Inhalte der Miniaturansicht zu zeichnen.|
|[CDocument:: onloaddocumentfromstream](#onloaddocumentfromstream)|Wird von Framework aufgerufen, wenn die Dokument Daten aus dem Stream geladen werden müssen.|
|[CDocument:: OnNewDocument](#onnewdocument)|Wird aufgerufen, um ein neues Dokument zu erstellen.|
|[CDocument:: OnOpenDocument](#onopendocument)|Wird aufgerufen, um ein vorhandenes Dokument zu öffnen.|
|[CDocument:: onpreviewhandlerqueryfocus](#onpreviewhandlerqueryfocus)|Weist den Vorschau Handler an, das HWND vom Aufruf der GetFocus-Funktion zurückzugeben.|
|[CDocument:: onpreviewhandlertranslateaccelerator](#onpreviewhandlertranslateaccelerator)|Weist den Vorschau Handler an, eine Tastatureingabe zu verarbeiten, die von der Meldungs Pumpe des Prozesses, in dem der Vorschau Handler ausgeführt wird, übergeben wird.|
|[CDocument:: onrichpreviewbackcolorchanged](#onrichpreviewbackcolorchanged)|Wird aufgerufen, wenn die Rich Preview-Hintergrundfarbe geändert wurde.|
|[CDocument:: onrichpreviewfontchanged](#onrichpreviewfontchanged)|Wird aufgerufen, wenn die umfangreiche Vorschau Schriftart geändert wurde.|
|[CDocument:: onrichpreviewsitechanged](#onrichpreviewsitechanged)|Wird aufgerufen, wenn eine umfangreiche Vorschau Site geändert wurde.|
|[CDocument:: onrichpreviewtextcolorchanged](#onrichpreviewtextcolorchanged)|Wird aufgerufen, wenn sich die Textfarbe für Rich Preview geändert hat.|
|[CDocument:: OnSaveDocument](#onsavedocument)|Wird aufgerufen, um das Dokument auf Datenträger zu speichern.|
|[CDocument:: onunloadhandler](#onunloadhandler)|Wird von Framework aufgerufen, wenn der Vorschau Handler entladen wird.|
|[CDocument::P recloseframe](#precloseframe)|Wird aufgerufen, bevor das Rahmen Fenster geschlossen wird.|
|[CDocument:: infonextchunkvalue](#readnextchunkvalue)|Liest den nächsten Block Wert.|
|[CDocument:: Releasefile](#releasefile)|Gibt eine Datei frei, um Sie für die Verwendung durch andere Anwendungen verfügbar zu machen.|
|[CDocument:: removechunk](#removechunk)|Entfernt einen Block mit der angegebenen GUID.|
|[CDocument:: removeview](#removeview)|Trennt eine Ansicht aus dem Dokument.|
|[CDocument:: reportsaveloadexception](#reportsaveloadexception)|Erweiterte über schreibbar; wird aufgerufen, wenn ein Öffnungs-oder Speichervorgang aufgrund einer Ausnahme nicht abgeschlossen werden kann.|
|[CDocument:: SaveModified](#savemodified)|Erweiterte über schreibbar; wird aufgerufen, um den Benutzer zu Fragen, ob das Dokument gespeichert werden soll.|
|[CDocument:: setchunkvalue](#setchunkvalue)|Legt einen Segment Wert fest.|
|[CDocument:: SetModifiedFlag](#setmodifiedflag)|Legt ein Flag fest, das angibt, dass Sie das Dokument seit der letzten Speicherung geändert haben.|
|[CDocument:: setpathname](#setpathname)|Legt den Pfad der Datendatei fest, die vom Dokument verwendet wird.|
|[CDocument:: SetTitle](#settitle)|Legt den Titel des Dokuments fest.|
|[CDocument:: UpdateAllViews](#updateallviews)|Benachrichtigt alle Sichten, dass das Dokument geändert wurde.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CDocument:: OnFileSendMail](#onfilesendmail)|Sendet eine e-Mail-Nachricht mit angefügtem Dokument.|
|[CDocument:: OnUpdateFileSendMail](#onupdatefilesendmail)|Aktiviert den Befehl Mail senden, wenn die Unterstützung von e-Mails vorhanden ist.|

### <a name="public-data-members"></a>Öffentliche Datenelemente

|Name|Beschreibung|
|----------|-----------------|
|[CDocument:: m_bGetThumbnailMode](#m_bgetthumbnailmode)|Gibt an, dass `CDocument` Objekt von dllhost für Miniaturansichten erstellt wurde. Muss in `CView::OnDraw`eingeglichen werden.|
|[CDocument:: m_bPreviewHandlerMode](#m_bpreviewhandlermode)|Gibt an, dass `CDocument` Objekt von prevhost für `Rich Preview`erstellt wurde. Muss in `CView::OnDraw`eingeglichen werden.|
|[CDocument:: m_bSearchMode](#m_bsearchmode)|Gibt an, dass `CDocument` Objekt von Indexer oder einer anderen Suchanwendung erstellt wurde.|
|[CDocument:: m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|Gibt die Hintergrundfarbe für das umfangreiche Vorschau Fenster an. Diese Farbe wird vom Host festgelegt.|
|[CDocument:: m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|Gibt die Vordergrundfarbe des Rich-Vorschau Fensters an. Diese Farbe wird vom Host festgelegt.|
|[CDocument:: m_lfRichPreviewFont](#m_lfrichpreviewfont)|Gibt die Text Schriftart für das umfangreiche Vorschau Fenster an. Diese Schriftart Informationen werden vom Host festgelegt.|

## <a name="remarks"></a>Hinweise

Ein Dokument stellt die Dateneinheit dar, die der Benutzer in der Regel mit dem Befehl zum Öffnen von Dateien öffnet und mit dem Befehl zum Speichern von Dateien speichert.

`CDocument` unterstützt Standard Vorgänge, z. b. das Erstellen eines Dokuments, das Laden und Speichern des Dokuments. Das Framework bearbeitet Dokumente mithilfe der-Schnittstelle, die durch `CDocument`definiert wird.

Eine Anwendung kann mehr als einen Dokumenttyp unterstützen. Beispielsweise kann eine Anwendung sowohl Tabellen-als auch Textdokumente unterstützen. Jedem Dokumenttyp ist eine Dokument Vorlage zugeordnet. die Dokument Vorlage gibt an, welche Ressourcen (z. b. Menü, Symbol oder Zugriffstasten Tabelle) für diesen Dokumenttyp verwendet werden. Jedes Dokument enthält einen Zeiger auf das zugeordnete `CDocTemplate` Objekt.

Benutzer interagieren mit einem Dokument über die zugeordneten [CView](../../mfc/reference/cview-class.md) -Objekte. Eine Ansicht rendert ein Bild des Dokuments in einem Rahmen Fenster und interpretiert Benutzereingaben als Vorgänge für das Dokument. Einem Dokument können mehrere Ansichten zugeordnet sein. Wenn der Benutzer ein Fenster in einem Dokument öffnet, erstellt das Framework eine Ansicht und fügt Sie an das Dokument an. Die Dokument Vorlage gibt an, welche Art von Ansicht und Rahmen Fenster zum Anzeigen der einzelnen Dokumenttypen verwendet werden.

Dokumente sind Teil des Standard Befehls Routings des Frameworks und erhalten folglich Befehle von standardmäßigen Benutzeroberflächen Komponenten (z. b. dem Menü Element Datei speichern). Ein Dokument empfängt Befehle, die von der aktiven Ansicht weitergeleitet werden. Wenn das Dokument einen angegebenen Befehl nicht behandelt, leitet es den Befehl an die Dokument Vorlage weiter, die ihn verwaltet.

Wenn die Daten eines Dokuments geändert werden, muss jeder seiner Sichten diese Änderungen widerspiegeln. `CDocument` stellt die [UpdateAllViews](#updateallviews) -Member-Funktion bereit, damit Sie die Sichten über solche Änderungen benachrichtigen können, sodass sich die Ansichten bei Bedarf selbst neu zeichnen können. Das Framework fordert den Benutzer außerdem auf, eine geänderte Datei vor dem Schließen zu speichern.

Zum Implementieren von Dokumenten in einer typischen Anwendung müssen Sie folgende Schritte ausführen:

- Leiten Sie eine Klasse von `CDocument` für jeden Dokumenttyp ab.

- Fügen Sie Element Variablen zum Speichern der einzelnen Dokument Daten hinzu.

- Implementieren Sie Member-Funktionen zum Lesen und Ändern der Dokument Daten. Die Dokument Sichten sind die wichtigsten Benutzer dieser Member-Funktionen.

- Überschreiben Sie die [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) -Member-Funktion in der Document-Klasse, um die Daten des Dokuments zu schreiben und auf den Datenträger zu lesen.

`CDocument` unterstützt das Senden Ihres Dokuments per e-Mail, wenn der e-Mail-Support (MAPI) vorhanden ist. Weitere Informationen finden Sie in den Artikeln [MAPI](../../mfc/mapi.md) und [MAPI-Unterstützung in MFC](../../mfc/mapi-support-in-mfc.md).

Weitere Informationen zu `CDocument`finden Sie in den Themen [Serialisierung](../../mfc/serialization-in-mfc.md), [Dokument-/Ansichtarchitektur](../../mfc/document-view-architecture.md)und [Dokument-/Ansicht-Erstellung](../../mfc/document-view-creation.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocument`

## <a name="requirements"></a>Voraussetzungen

**Header:** afxwin.h

##  <a name="addview"></a>CDocument:: AddView

Mit dieser Funktion können Sie eine Ansicht an das Dokument anfügen.

```
void AddView(CView* pView);
```

### <a name="parameters"></a>Parameter

*pView*<br/>
Verweist auf die Ansicht, die hinzugefügt wird.

### <a name="remarks"></a>Hinweise

Diese Funktion fügt die angegebene Ansicht der Liste der Ansichten hinzu, die dem Dokument zugeordnet sind. die-Funktion legt auch den Dokument Zeiger der Ansicht auf dieses Dokument fest. Das Framework ruft diese Funktion auf, wenn ein neu erstelltes Ansichts Objekt an ein Dokument angefügt wird. Dies tritt in Reaktion auf den Befehl Datei neu, Datei öffnen oder neuer Fenster oder, wenn ein Splitter Fenster geteilt wird, auf.

Diese Funktion wird nur aufgerufen, wenn Sie eine Ansicht manuell erstellen und anfügen. In der Regel lassen Sie das Framework Dokumente und Ansichten verbinden, indem Sie ein [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) -Objekt definieren, um eine Dokument Klasse, eine Ansichts Klasse und eine Frame Fenster Klasse zuzuordnen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]

##  <a name="beginreadchunks"></a>CDocument:: BeginRead Blöcke

Initialisiert das Lesen von Blöcken.

```
virtual void BeginReadChunks ();
```

### <a name="remarks"></a>Hinweise

##  <a name="cancloseframe"></a>CDocument:: cancloseframe

Wird von Framework aufgerufen, bevor ein Rahmen Fenster, in dem das Dokument angezeigt wird, geschlossen wird.

```
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Parameter

*pFrame*<br/>
Verweist auf das Rahmen Fenster einer Ansicht, die an das Dokument angefügt ist.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Rahmen Fenster sicher geschlossen werden kann. andernfalls 0.

### <a name="remarks"></a>Hinweise

Die Standard Implementierung überprüft, ob andere Rahmen Fenster das Dokument anzeigen. Wenn das angegebene Rahmen Fenster das letzte ist, das das Dokument anzeigt, wird der Benutzer von der-Funktion aufgefordert, das Dokument zu speichern, wenn es geändert wurde. Überschreiben Sie diese Funktion, wenn Sie eine besondere Verarbeitung durchführen möchten, wenn ein Rahmen Fenster geschlossen wird. Hierbei handelt es sich um eine erweiterte über schreibbare.

##  <a name="cdocument"></a>CDocument:: CDocument

Erstellt ein `CDocument`-Objekt.

```
CDocument();
```

### <a name="remarks"></a>Hinweise

Das Framework behandelt die Dokument Erstellung für Sie. Überschreiben Sie die [OnNewDocument](#onnewdocument) -Member-Funktion, um die Initialisierung pro Dokument auszuführen. Dies ist insbesondere in SDI-Anwendungen (Single Document Interface) wichtig.

##  <a name="clearchunklist"></a>CDocument:: clearchunklist

Löscht die Blockliste.

```
virtual void ClearChunkList ();
```

### <a name="remarks"></a>Hinweise

##  <a name="clearpathname"></a>CDocument:: clearpathname

Löscht den Pfad des Dokument Objekts.

```
virtual void ClearPathName();
```

### <a name="remarks"></a>Hinweise

Das Löschen des Pfads aus einem `CDocument` Objekt bewirkt, dass die Anwendung den Benutzer auffordert, wenn das Dokument das nächste Mal gespeichert wird. Dadurch verhält sich ein **Save** -Befehl wie ein " **Speichern** unter"-Befehl.

##  <a name="deletecontents"></a>CDocument::D eletecontent

Wird von Framework aufgerufen, um die Daten des Dokuments zu löschen, ohne das `CDocument` Objekt selbst zu zerstören.

```
virtual void DeleteContents();
```

### <a name="remarks"></a>Hinweise

Sie wird aufgerufen, kurz bevor das Dokument zerstört werden soll. Außerdem wird Sie aufgerufen, um sicherzustellen, dass ein Dokument leer ist, bevor es wieder verwendet wird. Dies ist besonders wichtig für eine SDI-Anwendung, bei der nur ein Dokument verwendet wird. das Dokument wird immer wieder verwendet, wenn der Benutzer ein anderes Dokument erstellt oder öffnet. Mit dieser Funktion können Sie den Befehl "Alle löschen" oder einen ähnlichen Befehl implementieren, mit dem alle Dokument Daten gelöscht werden. Bei der Standardimplementierung dieser Funktion wird keine Aktion ausgeführt. Überschreiben Sie diese Funktion, um die Daten in Ihrem Dokument zu löschen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]

##  <a name="findchunk"></a>CDocument:: findchunk

Sucht einen Block mit einer angegebenen GUID.

```
virtual POSITION FindChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Parameter

*guid*<br/>
Gibt die GUID eines zu suchenden Blocks an.

*pid*<br/>
Gibt eine PID eines zu suchenden Blocks an.

### <a name="return-value"></a>Rückgabewert

Position in der internen Blockliste, wenn erfolgreich. Andernfalls NULL.

### <a name="remarks"></a>Hinweise

##  <a name="getadapter"></a>CDocument:: GetAdapter

Gibt einen Zeiger auf ein Objekt zurück, das die `IDocument`-Schnittstelle implementiert.

```
virtual ATL::IDocument* GetAdapter();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein Objekt, das die `IDocument`-Schnittstelle implementiert.

### <a name="remarks"></a>Hinweise

##  <a name="getdoctemplate"></a>CDocument:: GetDocTemplate

Mit dieser Funktion können Sie einen Zeiger auf die Dokument Vorlage für diesen Dokumenttyp abrufen.

```
CDocTemplate* GetDocTemplate() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die Dokument Vorlage für diesen Dokumenttyp oder NULL, wenn das Dokument nicht durch eine Dokument Vorlage verwaltet wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]

##  <a name="getfile"></a>CDocument:: GetFile

Mit dieser Member-Funktion können Sie einen Zeiger auf ein `CFile`-Objekt abrufen.

```
virtual CFile* GetFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError);
```

### <a name="parameters"></a>Parameter

*lpszfilename*<br/>
Eine Zeichenfolge, die den Pfad zur gewünschten Datei ist. Der Pfad kann relativ oder absolut sein.

*pError*<br/>
Ein Zeiger auf ein vorhandenes Datei Ausnahme Objekt, das den Abschluss Status des Vorgangs angibt.

*nopenflags*<br/>
Freigabe-und Zugriffsmodus. Gibt die Aktion an, die beim Öffnen der Datei ausgeführt werden soll. Sie können die im CFile-Konstruktor [CFile:: CFile](../../mfc/reference/cfile-class.md#cfile) aufgeführten Optionen mithilfe des bitweisen or (&#124;)-Operators kombinieren. Eine Zugriffsberechtigung und eine Freigabe Option sind erforderlich. die `modeCreate`-und `modeNoInherit` Modi sind optional.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein `CFile` -Objekt.

##  <a name="getfirstviewposition"></a>CDocument:: GetFirstViewPosition

Mit dieser Funktion können Sie die Position der ersten Ansicht in der Liste der Sichten abrufen, die dem Dokument zugeordnet sind.

```
virtual POSITION GetFirstViewPosition() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Positionswert, der für die Iterationen mit der [GetNextView](#getnextview) -Member-Funktion verwendet werden kann.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

##  <a name="getnextview"></a>CDocument:: GetNextView

Mit dieser Funktion können Sie alle Dokument Sichten durchlaufen.

```
virtual CView* GetNextView(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parameter

*rPosition zurück*<br/>
Ein Verweis auf einen Positionswert, der von einem vorherigen Aufrufen der Element Funktionen `GetNextView` oder [GetFirstViewPosition](#getfirstviewposition) zurückgegeben wurde. Dieser Wert darf nicht NULL sein.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die durch *rPosition*identifizierte Ansicht.

### <a name="remarks"></a>Hinweise

Die-Funktion gibt die durch *rPosition* identifizierte Ansicht zurück und legt dann *rPosition* auf den Positionswert der nächsten Ansicht in der Liste fest. Wenn die abgerufene Ansicht der letzte in der Liste ist, wird *rPosition* auf NULL festgelegt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

##  <a name="getpathname"></a>CDocument:: getPathname

Mit dieser Funktion können Sie den voll qualifizierten Pfad der Datenträger Datei des Dokuments abrufen.

```
const CString& GetPathName() const;
```

### <a name="return-value"></a>Rückgabewert

Der voll qualifizierte Pfad des Dokuments. Diese Zeichenfolge ist leer, wenn das Dokument nicht gespeichert wurde oder keine Datenträger Datei zugeordnet ist.

##  <a name="getthumbnail"></a>CDocument:: getminiatur

Erstellt eine Bitmap, die vom Miniatur Ansichts Anbieter verwendet wird, um die Miniaturansicht anzuzeigen.

```
virtual BOOL GetThumbnail(
    UINT cx,
    HBITMAP* phbmp,
    DWORD* pdwAlpha);
```

### <a name="parameters"></a>Parameter

*verschoben*<br/>
Gibt die Breite und Höhe der Bitmap an.

*phbmp*<br/>
Enthält ein Handle für eine Bitmap, wenn die Funktion erfolgreich zurückgegeben wird.

*pdwalpha*<br/>
Enthält ein DWORD, das den Wert des Alphakanals angibt, wenn die Funktion erfolgreich zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn eine Bitmap für die Miniaturansicht erfolgreich erstellt wurde. andernfalls false.

### <a name="remarks"></a>Hinweise

##  <a name="gettitle"></a>CDocument:: getTitle

Mit dieser Funktion können Sie den Titel des Dokuments abrufen, der normalerweise aus dem Dateinamen des Dokuments abgeleitet ist.

```
const CString& GetTitle() const;
```

### <a name="return-value"></a>Rückgabewert

Der Titel des Dokuments.

##  <a name="initializesearchcontent"></a>CDocument:: initializesearchcontent

Wird aufgerufen, um den Such Inhalt für den Such Handler zu initialisieren.

```
virtual void InitializeSearchContent ();
```

### <a name="remarks"></a>Hinweise

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um Such Inhalte zu initialisieren. Der Inhalt muss eine Zeichenfolge mit Teilen sein, die durch ";" getrennt sind. Beispiel: "Point; Rollen OLE-Element ".

##  <a name="ismodified"></a>CDocument:: IsModified

Mit dieser Funktion können Sie ermitteln, ob das Dokument seit der letzten Speicherung geändert wurde.

```
virtual BOOL IsModified();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn das Dokument seit der letzten Speicherung geändert wurde. andernfalls 0.

##  <a name="issearchandorganizehandler"></a>CDocument:: issearchandorganizehandler

Gibt an, ob diese Instanz von `CDocument` für den Such & Organisations Handler erstellt wurde.

```
BOOL IsSearchAndOrganizeHandler() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn diese Instanz von `CDocument` für den Such & Organisations Handler erstellt wurde.

### <a name="remarks"></a>Hinweise

Diese Funktion gibt zurzeit nur dann true zurück, wenn umfassende Vorschau Handler in einem Out-of-Process-Server implementiert werden. Sie können die geeigneten Flags (m_bPreviewHandlerMode m_bSearchMode m_bGetThumbnailMode) auf der Anwendungsebene festlegen, damit diese Funktion true zurückgibt.

##  <a name="loaddocumentfromstream"></a>CDocument:: loaddocumentfromstream

Wird aufgerufen, um Dokument Daten aus einem Stream zu laden.

```
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,
    DWORD dwGrfMode);
```

### <a name="parameters"></a>Parameter

*pStream*<br/>
Ein Zeiger auf einen Stream. Dieser Stream wird von der Shell bereitgestellt.

*dwgrsmode*<br/>
Zugriffsmodus auf den Stream.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn der Ladevorgang erfolgreich ist, andernfalls HRESULT mit einem Fehlercode.

### <a name="remarks"></a>Hinweise

Sie können diese Methode in einer abgeleiteten Klasse überschreiben, um anzupassen, wie Daten aus dem Stream geladen werden.

##  <a name="m_bgetthumbnailmode"></a>CDocument:: m_bGetThumbnailMode

Gibt an, dass das `CDocument` Objekt von dllhost für Miniaturansichten erstellt wurde. Muss in `CView::OnDraw`eingeglichen werden.

```
BOOL m_bGetThumbnailMode;
```

### <a name="remarks"></a>Hinweise

`TRUE` gibt an, dass das Dokument von dllhost für Miniaturansichten erstellt wurde.

##  <a name="m_bpreviewhandlermode"></a>CDocument:: m_bPreviewHandlerMode

Gibt an, dass das `CDocument` Objekt von prevhost für die umfangreiche Vorschauversion erstellt wurde. Muss in `CView::OnDraw`eingeglichen werden.

```
BOOL m_bPreviewHandlerMode;
```

### <a name="remarks"></a>Hinweise

TRUE gibt an, dass das Dokument von prevhost für die umfangreiche Vorschauversion erstellt wurde.

##  <a name="m_bsearchmode"></a>CDocument:: m_bSearchMode

Gibt an, dass das `CDocument` Objekt vom Indexer oder von einer anderen Suchanwendung erstellt wurde.

```
BOOL m_bSearchMode;
```

### <a name="remarks"></a>Hinweise

`TRUE` gibt an, dass das Dokument vom Indexer oder von einer anderen Suchanwendung erstellt wurde.

##  <a name="m_clrrichpreviewbackcolor"></a>CDocument:: m_clrRichPreviewBackColor

Gibt die Hintergrundfarbe für das umfangreiche Vorschau Fenster an. Diese Farbe wird vom Host festgelegt.

```
COLORREF m_clrRichPreviewBackColor;
```

### <a name="remarks"></a>Hinweise

##  <a name="m_clrrichpreviewtextcolor"></a>CDocument:: m_clrRichPreviewTextColor

Gibt die Vordergrundfarbe des Rich-Preview-Fensters an. Diese Farbe wird vom Host festgelegt.

```
COLORREF m_clrRichPreviewTextColor;
```

### <a name="remarks"></a>Hinweise

##  <a name="m_lfrichpreviewfont"></a>CDocument:: m_lfRichPreviewFont

Gibt die Text Schriftart für das umfangreiche Vorschau Fenster an. Diese Schriftart Informationen werden vom Host festgelegt.

```
CFont m_lfRichPreviewFont;
```

### <a name="remarks"></a>Hinweise

##  <a name="onbeforerichpreviewfontchanged"></a>CDocument:: onbeforerichpreviewfontchanged

Wird aufgerufen, bevor die Schriftart für die umfangreiche Vorschau geändert wird.

```
virtual void OnBeforeRichPreviewFontChanged();
```

### <a name="remarks"></a>Hinweise

##  <a name="onchangedviewlist"></a>CDocument:: onchangedviewlist

Wird von Framework aufgerufen, nachdem dem Dokument eine Ansicht hinzugefügt oder daraus entfernt wurde.

```
virtual void OnChangedViewList();
```

### <a name="remarks"></a>Hinweise

Die Standard Implementierung dieser Funktion überprüft, ob die letzte Ansicht entfernt wird, und löscht, wenn dies der Fall ist, das Dokument. Überschreiben Sie diese Funktion, wenn Sie eine besondere Verarbeitung durchführen möchten, wenn das Framework eine Ansicht hinzufügt oder entfernt. Wenn Sie z. b. möchten, dass ein Dokument geöffnet bleibt, auch wenn keine angefügten Sichten vorhanden sind, überschreiben Sie diese Funktion.

##  <a name="onclosedocument"></a>CDocument:: onclosedocument

Wird vom Framework aufgerufen, wenn das Dokument geschlossen wird, in der Regel als Teil des Befehls zum Schließen der Datei.

```
virtual void OnCloseDocument();
```

### <a name="remarks"></a>Hinweise

Die Standard Implementierung dieser Funktion zerstört alle Frames, die zum Anzeigen des Dokuments verwendet werden, schließt die Ansicht, bereinigt den Inhalt des Dokuments und ruft dann die [DeleteContents](#deletecontents) -Member-Funktion auf, um die Daten des Dokuments zu löschen.

Überschreiben Sie diese Funktion, wenn Sie eine besondere Bereinigungs Verarbeitung durchführen möchten, wenn das Framework ein Dokument schließt. Wenn das Dokument beispielsweise einen Datensatz in einer Datenbank darstellt, empfiehlt es sich, diese Funktion zu überschreiben, um die Datenbank zu schließen. Sie sollten die Basisklassen Version dieser Funktion von ihrer außer Kraft Setzung aus abrufen.

##  <a name="oncreatepreviewframe"></a>CDocument:: onkreatepreviewframe

Wird von Framework aufgerufen, wenn es einen Vorschau Rahmen für eine umfangreiche Vorschauversion erstellen muss.

```
virtual BOOL OnCreatePreviewFrame();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn der Frame erfolgreich erstellt wurde. andernfalls false.

### <a name="remarks"></a>Hinweise

##  <a name="ondocumentevent"></a>CDocument:: ondocumentevent

Wird von Framework als Reaktion auf ein Dokument Ereignis aufgerufen.

```
virtual void OnDocumentEvent(DocumentEvent deEvent);
```

### <a name="parameters"></a>Parameter

*wird deaktiviert*<br/>
in Ein enumerierter Datentyp, der den Ereignistyp beschreibt.

### <a name="remarks"></a>Hinweise

Dokument Ereignisse können sich auf mehrere Klassen auswirken. Diese Methode ist für die Verarbeitung von Dokument Ereignissen zuständig, die andere Klassen als die [CDocument-Klasse](../../mfc/reference/cdocument-class.md)betreffen. Derzeit ist die einzige Klasse, die auf Dokument Ereignisse reagieren muss, die [cdatarecoveryhandler-Klasse](../../mfc/reference/cdatarecoveryhandler-class.md). Die `CDocument`-Klasse verfügt über andere über schreibbare Methoden, die für die Behandlung der Auswirkung auf die `CDocument`zuständig sind.

In der folgenden Tabelle sind die möglichen Werte für " *deevent* " und die Ereignisse aufgeführt, denen Sie entsprechen.

|Wert|Entsprechendes Ereignis|
|-----------|-------------------------|
|`onAfterNewDocument`|Es wurde ein neues Dokument erstellt.|
|`onAfterOpenDocument`|Ein neues Dokument wurde geöffnet.|
|`onAfterSaveDocument`|Das Dokument wurde gespeichert.|
|`onAfterCloseDocument`|Das Dokument wurde geschlossen.|

##  <a name="ondrawthumbnail"></a>CDocument:: ondrawminiatur

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um die Miniaturansicht zu zeichnen.

```
virtual void OnDrawThumbnail(
    CDC& dc,
    LPRECT lprcBounds);
```

### <a name="parameters"></a>Parameter

*dc*<br/>
Ein Verweis auf einen Gerätekontext.

*lprcbounds*<br/>
Gibt ein Begrenzungs Rechteck des Bereichs an, in dem die Miniaturansicht gezeichnet werden soll.

### <a name="remarks"></a>Hinweise

##  <a name="onfilesendmail"></a>CDocument:: OnFileSendMail

Sendet eine Nachricht über den residenten Mailhost (sofern vorhanden) mit dem Dokument als Anlage.

```
void OnFileSendMail();
```

### <a name="remarks"></a>Hinweise

`OnFileSendMail` wird [OnSaveDocument](#onsavedocument) aufgerufen, um unbenannte und geänderte Dokumente in einer temporären Datei zu serialisieren (speichern), die dann per elektronischer e-Mail gesendet wird. Wenn das Dokument nicht geändert wurde, wird keine temporäre Datei benötigt. das Original wird gesendet. `OnFileSendMail` lädt Datei "Mapi32. DLL, wenn Sie nicht bereits geladen wurde.

Eine spezielle Implementierung `OnFileSendMail` für [COleDocument](../../mfc/reference/coledocument-class.md) verarbeitet Verbund Dateien ordnungsgemäß.

`CDocument` unterstützt das Senden Ihres Dokuments per e-Mail, wenn der e-Mail-Support (MAPI) vorhanden ist. Weitere Informationen finden Sie in den Artikeln [MAPI-Themen](../../mfc/mapi.md) und [MAPI-Unterstützung in MFC](../../mfc/mapi-support-in-mfc.md)

##  <a name="onloaddocumentfromstream"></a>CDocument:: onloaddocumentfromstream

Wird von Framework aufgerufen, wenn die Dokument Daten aus einem Stream geladen werden müssen.

```
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,
    DWORD grfMode);
```

### <a name="parameters"></a>Parameter

*pStream*<br/>
Ein Zeiger auf einen eingehenden Datenstrom.

*GRF-Modus*<br/>
Zugriffsmodus auf den Stream.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn der Ladevorgang erfolgreich ist. andernfalls ein Fehlercode.

### <a name="remarks"></a>Hinweise

##  <a name="onnewdocument"></a>CDocument:: OnNewDocument

Wird von Framework als Teil des Datei neuen Befehls aufgerufen.

```
virtual BOOL OnNewDocument();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Dokument erfolgreich initialisiert wurde. andernfalls 0.

### <a name="remarks"></a>Hinweise

Die Standard Implementierung dieser Funktion Ruft die [DeleteContents](#deletecontents) -Member-Funktion auf, um sicherzustellen, dass das Dokument leer ist, und markiert das neue Dokument dann als Clean. Überschreiben Sie diese Funktion, um die Datenstruktur für ein neues Dokument zu initialisieren. Sie sollten die Basisklassen Version dieser Funktion von ihrer außer Kraft Setzung aus abrufen.

Wenn der Benutzer den Befehl "neue Datei" in einer SDI-Anwendung auswählt, verwendet das Framework diese Funktion, um das vorhandene Dokument erneut zu initialisieren, anstatt ein neues zu erstellen. Wenn der Benutzer in einer MDI-Anwendung (Multiple Document Interface) die Datei neu auswählt, erstellt das Framework jedes Mal ein neues Dokument und ruft dann diese Funktion auf, um es zu initialisieren. Sie müssen den Initialisierungs Code in dieser Funktion anstelle von im Konstruktor platzieren, damit der Befehl "Datei neu" in SDI-Anwendungen wirksam ist.

Beachten Sie, dass es Fälle gibt, in denen `OnNewDocument` zweimal aufgerufen wird. Dies tritt auf, wenn das Dokument als ActiveX-Dokument Server eingebettet ist. Die-Funktion wird zuerst von der `CreateInstance`-Methode aufgerufen (die von der `COleObjectFactory`abgeleiteten Klasse verfügbar gemacht wird), und ein zweites Mal durch die `InitNew`-Methode (die von der `COleServerDoc`abgeleiteten Klasse verfügbar gemacht wird).

### <a name="example"></a>Beispiel

In den folgenden Beispielen werden alternative Methoden zum Initialisieren eines Dokument Objekts veranschaulicht.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

##  <a name="onopendocument"></a>CDocument:: OnOpenDocument

Wird von Framework als Teil des Datei Öffnungs Befehls aufgerufen.

```
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parameter

*lpszpathname*<br/>
Zeigt auf den Pfad des zu öffnenden Dokuments.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Dokument erfolgreich geladen wurde. andernfalls 0.

### <a name="remarks"></a>Hinweise

Die Standard Implementierung dieser Funktion öffnet die angegebene Datei, ruft die [DeleteContents](#deletecontents) -Member-Funktion auf, um sicherzustellen, dass das Dokument leer ist, ruft [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) auf, um den Inhalt der Datei zu lesen, und markiert das Dokument dann als Clean. Überschreiben Sie diese Funktion, wenn Sie etwas anderes als den Archive-Mechanismus oder den File-Mechanismus verwenden möchten. Sie können z. b. eine Anwendung schreiben, bei der Dokumente Datensätze in einer Datenbank und nicht als separate Dateien darstellen.

Wenn der Benutzer den Befehl zum Öffnen der Datei in einer SDI-Anwendung auswählt, verwendet das Framework diese Funktion, um das vorhandene `CDocument` Objekt erneut zu initialisieren, anstatt ein neues zu erstellen. Wenn der Benutzer in einer MDI-Anwendung Datei öffnen auswählt, erstellt das Framework jedes Mal ein neues `CDocument` Objekt und ruft dann diese Funktion auf, um es zu initialisieren. Sie müssen den Initialisierungs Code in dieser Funktion anstelle von im Konstruktor platzieren, damit der Befehl zum Öffnen von Dateien in SDI-Anwendungen wirksam ist.

### <a name="example"></a>Beispiel

In den folgenden Beispielen werden alternative Methoden zum Initialisieren eines Dokument Objekts veranschaulicht.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

[!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]

##  <a name="onpreviewhandlerqueryfocus"></a>CDocument:: onpreviewhandlerqueryfocus

Weist den Vorschau Handler an, das vom Aufruf der `GetFocus` Funktion abgerufene HWND zurückzugeben.

```
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```

### <a name="parameters"></a>Parameter

*phwnd*<br/>
vorgenommen Wenn diese Methode zurückgegeben wird, enthält Sie einen Zeiger auf das HWND, das vom Aufruf der `GetFocus`-Funktion vom Vordergrund Thread des Vorschau Handlers zurückgegeben wurde.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück, wenn erfolgreich; andernfalls ein Fehlerwert.

### <a name="remarks"></a>Hinweise

##  <a name="onpreviewhandlertranslateaccelerator"></a>CDocument:: onpreviewhandlertranslateaccelerator

Weist den Vorschau Handler an, eine Tastatureingabe zu verarbeiten, die von der Meldungs Pumpe des Prozesses, in dem der Vorschau Handler ausgeführt wird, übergeben wird.

```
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```

### <a name="parameters"></a>Parameter

*pmsg*<br/>
in Ein Zeiger auf eine Fenster Meldung.

### <a name="return-value"></a>Rückgabewert

Wenn die Tastatureingabe-Nachricht vom Vorschau Handler verarbeitet werden kann, wird Sie vom Handler verarbeitet, und es wird S_OK zurückgegeben. Wenn der Vorschau Handler die Tastatureingabe Nachricht nicht verarbeiten kann, wird er über `IPreviewHandlerFrame::TranslateAccelerator`dem Host zur Anwendung angeboten. Wenn der Host die Nachricht verarbeitet, gibt diese Methode S_OK zurück. Wenn der Host die Nachricht nicht verarbeitet, gibt diese Methode S_FALSE zurück.

### <a name="remarks"></a>Hinweise

##  <a name="onrichpreviewbackcolorchanged"></a>CDocument:: onrichpreviewbackcolorchanged

Wird aufgerufen, wenn die Rich Preview-Hintergrundfarbe geändert wurde.

```
virtual void OnRichPreviewBackColorChanged();
```

### <a name="remarks"></a>Hinweise

##  <a name="onrichpreviewfontchanged"></a>CDocument:: onrichpreviewfontchanged

Wird aufgerufen, wenn sich die Schriftart der Rich-Vorschau geändert hat.

```
virtual void OnRichPreviewFontChanged();
```

### <a name="remarks"></a>Hinweise

##  <a name="onrichpreviewsitechanged"></a>CDocument:: onrichpreviewsitechanged

Wird aufgerufen, wenn die Rich Preview-Website geändert wurde.

```
virtual void OnRichPreviewSiteChanged();
```

### <a name="remarks"></a>Hinweise

##  <a name="onrichpreviewtextcolorchanged"></a>CDocument:: onrichpreviewtextcolorchanged

Wird aufgerufen, wenn sich die Textfarbe für Rich Preview geändert hat.

```
virtual void OnRichPreviewTextColorChanged();
```

### <a name="remarks"></a>Hinweise

##  <a name="onsavedocument"></a>CDocument:: OnSaveDocument

Wird von Framework als Teil des File Save-oder File Save as-Befehls aufgerufen.

```
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parameter

*lpszpathname*<br/>
Zeigt auf den voll qualifizierten Pfad, in dem die Datei gespeichert werden soll.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Dokument erfolgreich gespeichert wurde. andernfalls 0.

### <a name="remarks"></a>Hinweise

Die Standard Implementierung dieser Funktion öffnet die angegebene Datei, ruft [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) auf, um die Dokument Daten in die Datei zu schreiben, und markiert das Dokument dann als bereinigt. Überschreiben Sie diese Funktion, wenn Sie eine besondere Verarbeitung durchführen möchten, wenn das Framework ein Dokument speichert. Sie können z. b. eine Anwendung schreiben, bei der Dokumente Datensätze in einer Datenbank und nicht als separate Dateien darstellen.

##  <a name="onunloadhandler"></a>CDocument:: onunloadhandler

Wird von Framework aufgerufen, wenn der Vorschau Handler entladen wird.

```
virtual void OnUnloadHandler();
```

### <a name="remarks"></a>Hinweise

##  <a name="onupdatefilesendmail"></a>CDocument:: OnUpdateFileSendMail

Aktiviert den ID_FILE_SEND_MAIL Befehl, wenn e-Mail-Unterstützung (MAPI) vorhanden ist.

```
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parameter

*pCmdUI*<br/>
Ein Zeiger auf das [CCmdUI](../../mfc/reference/ccmdui-class.md) -Objekt, das mit dem ID_FILE_SEND_MAIL-Befehl verknüpft ist.

### <a name="remarks"></a>Hinweise

Andernfalls entfernt die Funktion den ID_FILE_SEND_MAIL Befehl aus dem Menü, einschließlich Trennzeichen oberhalb oder unterhalb des Menü Elements. MAPI ist aktiviert, wenn Datei "Mapi32. Die dll ist im Pfad und im Abschnitt [Mail] des Gewinns vorhanden. INI-Datei, MAPI = 1. Die meisten Anwendungen platzieren diesen Befehl im Menü Datei.

`CDocument` unterstützt das Senden Ihres Dokuments per e-Mail, wenn der e-Mail-Support (MAPI) vorhanden ist. Weitere Informationen finden Sie in den Artikeln [MAPI-Themen](../../mfc/mapi.md) und [MAPI-Unterstützung in MFC](../../mfc/mapi-support-in-mfc.md)

##  <a name="precloseframe"></a>CDocument::P recloseframe

Diese Member-Funktion wird von Framework aufgerufen, bevor das Rahmen Fenster zerstört wird.

```
virtual void PreCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Parameter

*pFrame*<br/>
Ein Zeiger auf das [CFrameWnd](../../mfc/reference/cframewnd-class.md) , das das zugeordnete `CDocument` Objekt enthält.

### <a name="remarks"></a>Hinweise

Sie kann überschrieben werden, um eine benutzerdefinierte Bereinigung bereitzustellen, aber stellen Sie sicher, dass Sie auch die Basisklasse aufzurufen.

Der Standardwert von `PreCloseFrame` in `CDocument`nichts bewirkt. Die von `CDocument`abgeleiteten Klassen [COleDocument](../../mfc/reference/coledocument-class.md) und [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) verwenden diese Member-Funktion.

##  <a name="readnextchunkvalue"></a>CDocument:: infonextchunkvalue

Liest den nächsten Segment Wert.

```
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```

### <a name="parameters"></a>Parameter

*ppValue*<br/>
vorgenommen Wenn die Funktion zurückgegeben wird, enthält *ppValue* den gelesenen Wert.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

##  <a name="releasefile"></a>CDocument:: Releasefile

Diese Member-Funktion wird vom Framework aufgerufen, um eine Datei freizugeben, sodass Sie von anderen Anwendungen verwendet werden kann.

```
virtual void ReleaseFile(
    CFile* pFile,
    BOOL bAbort);
```

### <a name="parameters"></a>Parameter

*pFile*<br/>
Ein Zeiger auf das CFile-Objekt, das freigegeben werden soll.

*babort*<br/>
Gibt an, ob die Datei mit `CFile::Close` oder `CFile::Abort`freigegeben werden soll. FALSE, wenn die Datei mit [CFile:: Close](../../mfc/reference/cfile-class.md#close)veröffentlicht werden soll. TRUE, wenn die Datei mit [CFile:: Abort](../../mfc/reference/cfile-class.md#abort)freigegeben werden soll.

### <a name="remarks"></a>Hinweise

Wenn " *babort* " den Wert "true" hat, ruft `ReleaseFile` `CFile::Abort`auf, und die Datei wird veröffentlicht. `CFile::Abort` löst keine Ausnahme aus.

Wenn " *babort* " auf "false" gesetzt ist, werden `ReleaseFile` `CFile::Close` aufgerufen und die Datei freigegeben.

Überschreiben Sie diese Member-Funktion, um eine Aktion durch den Benutzer anzufordern, bevor die Datei freigegeben wird.

##  <a name="removechunk"></a>CDocument:: removechunk

Entfernt einen Block mit der angegebenen GUID.

```
virtual void RemoveChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Parameter

*Guid*<br/>
Gibt die GUID eines zu entfernenden Blocks an.

*Lauer*<br/>
Gibt die PID eines zu entfernenden Blocks an.

### <a name="remarks"></a>Hinweise

##  <a name="removeview"></a>CDocument:: removeview

Mit dieser Funktion wird eine Ansicht von einem Dokument getrennt.

```
void RemoveView(CView* pView);
```

### <a name="parameters"></a>Parameter

*pView*<br/>
Verweist auf die Ansicht, die entfernt wird.

### <a name="remarks"></a>Hinweise

Diese Funktion entfernt die angegebene Sicht aus der Liste der Sichten, die dem Dokument zugeordnet sind. Außerdem wird der Dokument Zeiger der Ansicht auf NULL festgelegt. Diese Funktion wird vom Framework aufgerufen, wenn ein Rahmen Fenster geschlossen oder ein Bereich eines Splitter Fensters geschlossen wird.

Diese Funktion wird nur aufgerufen, wenn Sie eine Ansicht manuell trennen. In der Regel lassen Sie das Framework Dokumente und Sichten trennen, indem Sie ein [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) -Objekt definieren, um eine Dokument Klasse, eine Ansichts Klasse und eine Frame Fenster Klasse zuzuordnen.

Im Beispiel zu [AddView](#addview) finden Sie eine Beispiel Implementierung.

##  <a name="reportsaveloadexception"></a>CDocument:: reportsaveloadexception

Wird aufgerufen, wenn eine Ausnahme ausgelöst wird (in der Regel eine [CFileException](../../mfc/reference/cfileexception-class.md) oder [carchiveexception](../../mfc/reference/carchiveexception-class.md)), während das Dokument gespeichert oder geladen wird.

```
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,
    CException* e,
    BOOL bSaving,
    UINT nIDPDefault);
```

### <a name="parameters"></a>Parameter

*lpszpathname*<br/>
Zeigt auf den Namen des Dokuments, das gespeichert oder geladen wurde.

*e*<br/>
Verweist auf die ausgelöste Ausnahme. Kann möglicherweise NULL sein.

*bSpeichern*<br/>
Flag, das angibt, welcher Vorgang ausgeführt wurde. ein Wert ungleich 0 (null), wenn das Dokument gespeichert wurde, 0, wenn das Dokument geladen wurde.

*nidpdefault*<br/>
Der Bezeichner der Fehlermeldung, die angezeigt werden soll, wenn die Funktion keine spezifischere angibt.

### <a name="remarks"></a>Hinweise

Die Standard Implementierung überprüft das Ausnahme Objekt und sucht nach einer Fehlermeldung, in der die Ursache speziell beschrieben wird. Wenn eine bestimmte Nachricht nicht gefunden wird oder *e* NULL ist, wird die durch den Parameter " *nidpdefault* " angegebene allgemeine Meldung verwendet. Die Funktion zeigt dann ein Meldungs Feld mit der Fehlermeldung an. Überschreiben Sie diese Funktion, wenn Sie zusätzliche, angepasste Fehlermeldungen bereitstellen möchten. Hierbei handelt es sich um eine erweiterte über schreibbare.

##  <a name="savemodified"></a>CDocument:: SaveModified

Wird von Framework aufgerufen, bevor ein modifiziertes Dokument geschlossen wird.

```
virtual BOOL SaveModified();
```

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn es sicher ist, den Vorgang fortzusetzen und das Dokument zu schließen. 0, wenn das Dokument nicht geschlossen werden soll.

### <a name="remarks"></a>Hinweise

Die Standard Implementierung dieser Funktion zeigt ein Meldungs Feld an, in dem der Benutzer gefragt wird, ob die Änderungen im Dokument gespeichert werden sollen, sofern vorhanden. Überschreiben Sie diese Funktion, wenn für das Programm eine andere Aufforderungs Prozedur erforderlich ist. Hierbei handelt es sich um eine erweiterte über schreibbare.

##  <a name="setchunkvalue"></a>CDocument:: setchunkvalue

Legt einen Segment Wert fest.

```
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>Parameter

*pValue*<br/>
Gibt einen festzulegenden Block Wert an.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

##  <a name="setmodifiedflag"></a>CDocument:: SetModifiedFlag

Diese Funktion wird aufgerufen, nachdem Sie Änderungen am Dokument vorgenommen haben.

```
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parameter

*bmodified*<br/>
Flag zum angeben, ob das Dokument geändert wurde.

### <a name="remarks"></a>Hinweise

Durch konsistentes Aufrufen dieser Funktion stellen Sie sicher, dass das Framework den Benutzer auffordert, Änderungen zu speichern, bevor ein Dokument geschlossen wird. In der Regel sollten Sie den Standardwert true für den *bmodified* -Parameter verwenden. Um ein Dokument als "bereinigt" (nicht geändert) zu markieren, wird diese Funktion mit dem Wert "false" aufgerufen.

##  <a name="setpathname"></a>CDocument:: setpathname

Mit dieser Funktion können Sie den voll qualifizierten Pfad der Datenträger Datei des Dokuments angeben.

```
virtual void SetPathName(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>Parameter

*lpszpathname*<br/>
Verweist auf die Zeichenfolge, die als Pfad für das Dokument verwendet werden soll.

*baddtomru*<br/>
Bestimmt, ob der Dateiname der zuletzt verwendeten Datei Liste (MRU) hinzugefügt wird. Wenn true, wird der Dateiname hinzugefügt. Wenn der Wert false ist, wird er nicht hinzugefügt.

### <a name="remarks"></a>Hinweise

Abhängig vom Wert von *baddtomru* wird der Pfad der von der Anwendung verwalteten MRU-Liste hinzugefügt oder nicht hinzugefügt. Beachten Sie, dass einige Dokumente keiner Datenträger Datei zugeordnet sind. Diese Funktion wird nur aufgerufen, wenn Sie die Standard Implementierung zum Öffnen und Speichern von Dateien überschreiben, die vom Framework verwendet werden.

##  <a name="settitle"></a>CDocument:: SetTitle

Mit dieser Funktion können Sie den Titel des Dokuments angeben (die Zeichenfolge, die in der Titelleiste eines Rahmen Fensters angezeigt wird).

```
virtual void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>Parameter

*lpsztitle*<br/>
Verweist auf die Zeichenfolge, die als Titel des Dokuments verwendet werden soll.

### <a name="remarks"></a>Hinweise

Wenn Sie diese Funktion aufrufen, werden die Titel aller Rahmen Fenster aktualisiert, in denen das Dokument angezeigt wird.

##  <a name="updateallviews"></a>CDocument:: UpdateAllViews

Diese Funktion wird aufgerufen, nachdem das Dokument geändert wurde.

```
void UpdateAllViews(
    CView* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL);
```

### <a name="parameters"></a>Parameter

*psender*<br/>
Verweist auf die Ansicht, die das Dokument geändert hat, oder NULL, wenn alle Sichten aktualisiert werden sollen.

*lHint*<br/>
Enthält Informationen über die Änderung.

*phint*<br/>
Verweist auf ein Objekt, das Informationen über die Änderung speichert.

### <a name="remarks"></a>Hinweise

Sie sollten diese Funktion aufrufen, nachdem Sie die [SetModifiedFlag](#setmodifiedflag) -Member-Funktion aufgerufen haben. Diese Funktion informiert jede Ansicht, die an das Dokument angefügt ist, mit Ausnahme der von *psender*angegebenen Ansicht, dass das Dokument geändert wurde. Diese Funktion wird in der Regel von der Ansichts Klasse aufgerufen, nachdem der Benutzer das Dokument in einer Ansicht geändert hat.

Diese Funktion Ruft die [CView:: OnUpdate](../../mfc/reference/cview-class.md#onupdate) -Member-Funktion für jede der Dokument Sichten außer der sendenden Ansicht auf, wobei *phint* und *lHint*übergeben werden. Verwenden Sie diese Parameter, um Informationen über die an dem Dokument vorgenommenen Änderungen an die Sichten zu übergeben. Sie können Informationen mithilfe von *lHint* codieren und/oder eine von [CObject](../../mfc/reference/cobject-class.md)abgeleitete Klasse definieren, um Informationen über die Änderungen zu speichern und ein Objekt dieser Klasse mithilfe von *phint*zu übergeben. Überschreiben Sie die `CView::OnUpdate` Member-Funktion in Ihrer [CView](../../mfc/reference/cview-class.md)-abgeleiteten Klasse, um die Aktualisierung der Anzeige der Ansicht auf der Grundlage der übergebenen Informationen zu optimieren.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel NPP](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)<br/>
[CView-Klasse](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate-Klasse](../../mfc/reference/cdoctemplate-class.md)
