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
ms.openlocfilehash: 3376b8febe8ae4586ce649f3f83386875acb678f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375519"
---
# <a name="cdoctemplate-class"></a>CDocTemplate-Klasse

Eine abstrakte Basisklasse, die die grundlegende Funktionalität für Dokumentvorlagen definiert.

## <a name="syntax"></a>Syntax

```
class CDocTemplate : public CCmdTarget
```

## <a name="members"></a>Member

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDocTemplate::CDocTemplate](#cdoctemplate)|Erstellt ein `CDocTemplate`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDocTemplate::Dokument hinzufügen](#adddocument)|Fügt einer Vorlage ein Dokument hinzu.|
|[CDocTemplate::CloseAllDocuments](#closealldocuments)|Schließt alle Dokumente, die dieser Vorlage zugeordnet sind.|
|[CDocTemplate::CreateNewDocument](#createnewdocument)|Erstellt ein neues Dokument.|
|[CDocTemplate::CreateNewFrame](#createnewframe)|Erstellt ein neues Rahmenfenster, das ein Dokument und eine Ansicht enthält.|
|[CDocTemplate::CreateOleFrame](#createoleframe)|Erstellt ein OLE-fähiges Rahmenfenster.|
|[CDocTemplate::CreatePreviewFrame](#createpreviewframe)|Erstellt einen untergeordneten Rahmen, der für Rich Preview verwendet wird.|
|[CDocTemplate::GetDocString](#getdocstring)|Ruft eine Zeichenfolge ab, die dem Dokumenttyp zugeordnet ist.|
|[CDocTemplate::GetFirstDocPosition](#getfirstdocposition)|Ruft die Position des ersten Dokuments ab, das dieser Vorlage zugeordnet ist.|
|[CDocTemplate::GetNextDoc](#getnextdoc)|Ruft ein Dokument und die Position des nächsten Dokuments ab.|
|[CDocTemplate::InitialUpdateFrame](#initialupdateframe)|Initialisiert das Rahmenfenster und macht es optional sichtbar.|
|[CDocTemplate::LoadTemplate](#loadtemplate)|Lädt die Ressourcen `CDocTemplate` für eine bestimmte oder abgeleitete Klasse.|
|[CDocTemplate::MatchDocType](#matchdoctype)|Bestimmt den Grad der Vertrauensart in die Übereinstimmung zwischen einem Dokumenttyp und dieser Vorlage.|
|[CDocTemplate::OpenDocumentFile](#opendocumentfile)|Öffnet eine Datei, die durch einen Pfadnamen angegeben wird.|
|[CDocTemplate::RemoveDocument](#removedocument)|Entfernt ein Dokument aus einer Vorlage.|
|[CDocTemplate::SaveAllModified](#saveallmodified)|Speichert alle Dokumente, die dieser Vorlage zugeordnet sind und die geändert wurden.|
|[CDocTemplate::SetContainerInfo](#setcontainerinfo)|Bestimmt die Ressourcen für OLE-Container beim Bearbeiten eines ortsgebundenen OLE-Elements.|
|[CDocTemplate::SetDefaultTitle](#setdefaulttitle)|Zeigt den Standardtitel in der Titelleiste des Dokumentfensters an.|
|[CDocTemplate::SetPreviewInfo](#setpreviewinfo)|Setups aout of process preview handler.|
|[CDocTemplate::SetServerInfo](#setserverinfo)|Bestimmt die Ressourcen und Klassen, wenn das Serverdokument direkt eingebettet oder bearbeitet wird.|

## <a name="remarks"></a>Bemerkungen

In der Regel erstellen Sie eine oder mehrere Dokumentvorlagen in der Implementierung der `InitInstance` Anwendungsfunktion. Eine Dokumentvorlage definiert die Beziehungen zwischen drei Klassentypen:

- Eine Dokumentklasse, von der `CDocument`Sie ableiten.

- Eine Ansichtsklasse, die Daten aus der oben aufgeführten Dokumentklasse anzeigt. Sie können diese Klasse `CView` `CScrollView`von `CFormView`, `CEditView`, oder ableiten. (Sie können `CEditView` es auch direkt verwenden.)

- Eine Rahmenfensterklasse, die die Ansicht enthält. Für eine SDI-Anwendung (Single Document Interface) `CFrameWnd`leiten Sie diese Klasse von ab. Bei einer MDI-Anwendung (Multiple Document Interface) `CMDIChildWnd`leiten Sie diese Klasse von ab. Wenn Sie das Verhalten des Rahmenfensters nicht anpassen `CFrameWnd` müssen, können Sie die eigene Klasse verwenden oder `CMDIChildWnd` direkt erstellen, ohne ihre eigene Klasse abzuleiten.

Ihre Anwendung verfügt über eine Dokumentvorlage für jeden dokumenttyp, den sie unterstützt. Wenn Ihre Anwendung beispielsweise sowohl Tabellenkalkulationen als auch Textdokumente unterstützt, verfügt die Anwendung über zwei Dokumentvorlagenobjekte. Jede Dokumentvorlage ist für das Erstellen und Verwalten aller Dokumente des Typs verantwortlich.

Die Dokumentvorlage speichert Zeiger `CRuntimeClass` auf die Objekte für die Dokument-, Ansichts- und Rahmenfensterklassen. Diese `CRuntimeClass` Objekte werden beim Erstellen einer Dokumentvorlage angegeben.

Die Dokumentvorlage enthält die ID der Ressourcen, die mit dem Dokumenttyp verwendet werden (z. B. Menü-, Symbol- oder Beschleunigertabellenressourcen). Die Dokumentvorlage enthält auch Zeichenfolgen, die zusätzliche Informationen zum Dokumenttyp enthalten. Dazu gehören der Name des Dokumenttyps (z. B. "Arbeitsblatt") und die Dateierweiterung (z. B. ".xls"). Optional kann es andere Zeichenfolgen enthalten, die von der Benutzeroberfläche der Anwendung, dem Windows-Datei-Manager und der OLE-Unterstützung (Object Linking and Embedding) verwendet werden.

Wenn es sich bei Ihrer Anwendung um einen OLE-Container und/oder -Server handelt, definiert die Dokumentvorlage auch die ID des Menüs, das bei der Ortsaktivierung verwendet wird. Wenn es sich bei Ihrer Anwendung um einen OLE-Server handelt, definiert die Dokumentvorlage die ID der Symbolleiste und des Menüs, die während der ortsseitigen Aktivierung verwendet werden. Sie geben diese zusätzlichen `SetContainerInfo` OLE-Ressourcen durch Aufrufen und `SetServerInfo`an.

Da `CDocTemplate` es sich um eine abstrakte Klasse handelt, können Sie die Klasse nicht direkt verwenden. Eine typische Anwendung verwendet `CDocTemplate`eine der beiden von der Microsoft `CSingleDocTemplate`Foundation-Klassenbibliothek bereitgestellten `CMultiDocTemplate`Klassen: , die SDI implementiert, und , die MDI implementiert. Weitere Informationen zur Verwendung von Dokumentvorlagen finden Sie in diesen Klassen.

Wenn Ihre Anwendung ein Benutzeroberflächenparadigma benötigt, das sich grundlegend von SDI oder `CDocTemplate`MDI unterscheidet, können Sie Ihre eigene Klasse von ableiten.

Weitere Informationen `CDocTemplate`finden Sie unter [Dokumentvorlagen und den Dokument-/Ansichtserstellungsprozess](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocTemplate`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="cdoctemplateadddocument"></a><a name="adddocument"></a>CDocTemplate::Dokument hinzufügen

Verwenden Sie diese Funktion, um einer Vorlage ein Dokument hinzuzufügen.

```
virtual void AddDocument(CDocument* pDoc);
```

### <a name="parameters"></a>Parameter

*pDoc*<br/>
Ein Zeiger auf das hinzuzufügende Dokument.

### <a name="remarks"></a>Bemerkungen

Die abgeleiteten Klassen [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) und [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) überschreiben diese Funktion. Wenn Sie eine eigene Dokumentvorlagenklasse `CDocTemplate`von ableiten, muss die abgeleitete Klasse diese Funktion überschreiben.

## <a name="cdoctemplatecdoctemplate"></a><a name="cdoctemplate"></a>CDocTemplate::CDocTemplate

Erstellt ein `CDocTemplate`-Objekt.

```
CDocTemplate (
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Parameter

*nIDResource*<br/>
Gibt die ID der Ressourcen an, die mit dem Dokumenttyp verwendet werden. Dies kann Menü-, Symbol-, Beschleunigertabelle und Zeichenfolgenressourcen umfassen.

Die Zeichenfolgenressource besteht aus bis zu sieben Teilzeichenfolgen, die durch das Zeichen ''n' getrennt sind (das Zeichen ''n' wird als Platzhalter benötigt, wenn eine Teilzeichenfolge nicht enthalten ist; jedoch sind nachfolgende 'n'-Zeichen nicht erforderlich); Diese Teilzeichenfolgen beschreiben den Dokumenttyp. Informationen zu den Teilzeichenfolgen finden Sie unter [GetDocString](#getdocstring). Diese Zeichenfolgenressource befindet sich in der Ressourcendatei der Anwendung. Beispiel:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

Beachten Sie, dass die Zeichenfolge mit einem Zeichen ''n' beginnt. Dies liegt daran, dass die erste Teilzeichenfolge nicht für MDI-Anwendungen verwendet wird und daher nicht enthalten ist. Sie können diese Zeichenfolge mit dem Zeichenfolgen-Editor bearbeiten. Die gesamte Zeichenfolge wird als einzelner Eintrag im String-Editor und nicht als sieben separate Einträge angezeigt.

*pDocClass*<br/>
Zeigt auf `CRuntimeClass` das Objekt der Dokumentklasse. Diese Klasse `CDocument`ist eine -abgeleitete Klasse, die Sie definieren, um Ihre Dokumente darzustellen.

*pFrameClass*<br/>
Zeigt auf `CRuntimeClass` das Objekt der Rahmenfensterklasse. Diese Klasse kann `CFrameWnd`eine -derived-Klasse `CFrameWnd` sein, oder sie kann selbst sein, wenn Sie das Standardverhalten für das Hauptframefenster verwenden möchten.

*pViewClass*<br/>
Zeigt auf `CRuntimeClass` das Objekt der Ansichtsklasse. Diese Klasse `CView`ist eine -abgeleitete Klasse, die Sie zum Anzeigen Ihrer Dokumente definieren.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Memberfunktion, um ein `CDocTemplate` Objekt zu erstellen. Weisen Sie `CDocTemplate` ein Objekt dynamisch zu und übergeben Sie `InitInstance` es aus der Memberfunktion Ihrer Anwendungsklasse an [CWinApp::AddDocTemplate.](../../mfc/reference/cwinapp-class.md#adddoctemplate)

## <a name="cdoctemplateclosealldocuments"></a><a name="closealldocuments"></a>CDocTemplate::CloseAllDocuments

Rufen Sie diese Memberfunktion auf, um alle geöffneten Dokumente zu schließen.

```
virtual void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>Parameter

*bEndSession*<br/>
Wird nicht verwendet.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird in der Regel als Teil des Befehls Dateibeenden verwendet. Die Standardimplementierung dieser Funktion ruft die [CDocument::DeleteContents-Memberfunktion](../../mfc/reference/cdocument-class.md#deletecontents) auf, um die Dokumentdaten zu löschen, und schließt dann die Rahmenfenster für alle dem Dokument zugeordneten Ansichten.

Überschreiben Sie diese Funktion, wenn Sie den Benutzer dazu verpflichten möchten, eine spezielle Bereinigungsverarbeitung durchzuführen, bevor das Dokument geschlossen wird. Wenn das Dokument z. B. einen Datensatz in einer Datenbank darstellt, sollten Sie diese Funktion überschreiben, um die Datenbank zu schließen.

## <a name="cdoctemplatecreatenewdocument"></a><a name="createnewdocument"></a>CDocTemplate::CreateNewDocument

Rufen Sie diese Memberfunktion auf, um ein neues Dokument des Typs zu erstellen, der dieser Dokumentvorlage zugeordnet ist.

```
virtual CDocument* CreateNewDocument();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das neu erstellte Dokument oder NULL, wenn ein Fehler auftritt.

## <a name="cdoctemplatecreatenewframe"></a><a name="createnewframe"></a>CDocTemplate::CreateNewFrame

Erstellt ein neues Rahmenfenster, das ein Dokument und eine Ansicht enthält.

```
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,
    CFrameWnd* pOther);
```

### <a name="parameters"></a>Parameter

*pDoc*<br/>
Das Dokument, auf das sich das neue Rahmenfenster beziehen soll. Kann den Wert NULL haben.

*pOther*<br/>
Das Rahmenfenster, auf dem das neue Rahmenfenster basieren soll. Kann den Wert NULL haben.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das neu erstellte Rahmenfenster oder NULL, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

`CreateNewFrame`verwendet `CRuntimeClass` die an den Konstruktor übergebenen Objekte, um ein neues Rahmenfenster mit einer Ansicht und einem zugeordneten Dokument zu erstellen. Wenn der *pDoc-Parameter* NULL ist, gibt das Framework eine TRACE-Nachricht aus.

Der Parameter *pOther* wird verwendet, um den Befehl Window New zu implementieren. Es stellt ein Rahmenfenster bereit, auf dem das neue Rahmenfenster modellieren werden kann. Das neue Rahmenfenster wird in der Regel unsichtbar erstellt. Rufen Sie diese Funktion auf, um Rahmenfenster außerhalb der Standardframeworkimplementierung von File New und File Open zu erstellen.

## <a name="cdoctemplatecreateoleframe"></a><a name="createoleframe"></a>CDocTemplate::CreateOleFrame

Erstellt ein OLE-Rahmenfenster.

```
CFrameWnd* CreateOleFrame(
    CWnd* pParentWnd,
    CDocument* pDoc,
    BOOL bCreateView);
```

### <a name="parameters"></a>Parameter

*pParentWnd*<br/>
Ein Zeiger auf das übergeordnete Fenster des Rahmens.

*pDoc*<br/>
Ein Zeiger auf das Dokument, auf das sich das neue OLE-Rahmenfenster beziehen soll.

*bCreateView*<br/>
Bestimmt, ob eine Ansicht zusammen mit dem Rahmen erstellt wird.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein Rahmenfenster, wenn erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Wenn *bCreateView* Null ist, wird ein leerer Rahmen erstellt.

## <a name="cdoctemplategetdocstring"></a><a name="getdocstring"></a>CDocTemplate::GetDocString

Ruft eine Zeichenfolge ab, die dem Dokumenttyp zugeordnet ist.

```
virtual BOOL GetDocString(
    CString& rString,
    enum DocStringIndex index) const;
```

### <a name="parameters"></a>Parameter

*rString*<br/>
Ein Verweis `CString` auf ein Objekt, das die Zeichenfolge enthält, wenn die Funktion zurückgegeben wird.

*Index*<br/>
Ein Index der Teilzeichenfolge, die aus der Zeichenfolge abgerufen wird, die den Dokumenttyp beschreibt. Dieser Parameter kann einen der folgenden Werte aufweisen:

- `CDocTemplate::windowTitle`Name, der in der Titelleiste des Anwendungsfensters angezeigt wird (z. B. "Microsoft Excel"). Nur in der Dokumentvorlage für SDI-Anwendungen vorhanden.

- `CDocTemplate::docName`Stamm für den Standarddokumentnamen (z. B. "Sheet"). Dieser Stamm wird zusammen mit einer Zahl für den Standardnamen eines neuen Dokuments dieses Typs verwendet, wenn der Benutzer den Befehl Neu aus dem Menü Datei auswählt (z. B. "Sheet1" oder "Sheet2"). Wenn nicht angegeben, wird "Untitled" als Standard verwendet.

- `CDocTemplate::fileNewName`Name dieses Dokumenttyps. Wenn die Anwendung mehr als einen Dokumenttyp unterstützt, wird diese Zeichenfolge im Dialogfeld Datei neu angezeigt (z. B. "Arbeitsblatt"). Wenn nicht angegeben, kann auf den Dokumenttyp mit dem Befehl "Neu" nicht zugegriffen werden.

- `CDocTemplate::filterName`Beschreibung des Dokumenttyps und eines Platzhalterfilters, der mit Dokumenten dieses Typs übereinstimmt. Diese Zeichenfolge wird in der Dropdown-Liste "Dateien des Typs" im Dialogfeld Datei öffnen angezeigt (z. B. "Arbeitsblätter (*.xls)"). Wenn nicht angegeben, kann auf den Dokumenttyp mit dem Befehl Dateiöffnen nicht zugegriffen werden.

- `CDocTemplate::filterExt`Erweiterung für Dokumente dieses Typs (z. B. ".xls"). Wenn nicht angegeben, kann auf den Dokumenttyp mit dem Befehl Dateiöffnen nicht zugegriffen werden.

- `CDocTemplate::regFileTypeId`Bezeichner für den Dokumenttyp, der in der von Windows verwalteten Registrierungsdatenbank gespeichert werden soll. Diese Zeichenfolge ist nur für die interne Verwendung vorgesehen (z. B. "ExcelWorksheet"). Wenn nicht angegeben, kann der Dokumenttyp nicht beim Windows-Datei-Manager registriert werden.

- `CDocTemplate::regFileTypeName`Name des Dokumenttyps, der in der Registrierungsdatenbank gespeichert werden soll. Diese Zeichenfolge kann in Dialogfeldern von Anwendungen angezeigt werden, die auf die Registrierungsdatenbank zugreifen (z. B. "Microsoft Excel Worksheet").

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die angegebene Teilzeichenfolge gefunden wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um eine bestimmte Teilzeichenfolge abzurufen, die den Dokumenttyp beschreibt. Die Zeichenfolge, die diese Teilzeichenfolgen enthält, wird in der Dokumentvorlage gespeichert und von einer Zeichenfolge in der Ressourcendatei für die Anwendung abgeleitet. Das Framework ruft diese Funktion auf, um die Zeichenfolgen abzubekommen, die es für die Benutzeroberfläche der Anwendung benötigt. Wenn Sie eine Dateinamenerweiterung für die Dokumente Ihrer Anwendung angegeben haben, ruft das Framework diese Funktion auch auf, wenn Sie einen Eintrag zur Windows-Registrierungsdatenbank hinzufügen. Dadurch können Dokumente über den Windows-Datei-Manager geöffnet werden.

Rufen Sie diese Funktion nur auf, wenn `CDocTemplate`Sie Ihre eigene Klasse von ableiten.

## <a name="cdoctemplategetfirstdocposition"></a><a name="getfirstdocposition"></a>CDocTemplate::GetFirstDocPosition

Ruft die Position des ersten Dokuments ab, das dieser Vorlage zugeordnet ist.

```
virtual POSITION GetFirstDocPosition() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein POSITION-Wert, der zum Durchlaufen der Liste der Dokumente verwendet werden kann, die dieser Dokumentvorlage zugeordnet sind. oder NULL, wenn die Liste leer ist.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um die Position des ersten Dokuments in der Liste der Dieser Vorlage zugeordneten Dokumente abzuspeichern. Verwenden Sie den POSITION-Wert als Argument für [CDocTemplate::GetNextDoc,](#getnextdoc) um die Liste der der Vorlage zugeordneten Dokumente zu durchlaufen.

[CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) und [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) überschreiben beide diese reine virtuelle Funktion. Jede Klasse, von `CDocTemplate` der Sie ableiten, muss diese Funktion ebenfalls überschreiben.

## <a name="cdoctemplategetnextdoc"></a><a name="getnextdoc"></a>CDocTemplate::GetNextDoc

Ruft das von *rPos*identifizierte Listenelement ab und legt *dann rPos* auf den POSITION-Wert des nächsten Eintrags in der Liste fest.

```
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das nächste Dokument in der Liste der Dokumente, die dieser Vorlage zugeordnet sind.

### <a name="parameters"></a>Parameter

*rPos*<br/>
Ein Verweis auf einen POSITION-Wert, der von `GetNextDoc`einem vorherigen Aufruf von [GetFirstDocPosition](#getfirstdocposition) oder zurückgegeben wird.

### <a name="remarks"></a>Bemerkungen

Wenn das abgerufene Element das letzte in der Liste ist, wird der neue Wert von *rPos* auf NULL gesetzt.

Sie können `GetNextDoc` in einer Vorwärtsiterationsschleife verwenden, wenn Sie die Ausgangsposition mit einem Aufruf von [GetFirstDocPosition](#getfirstdocposition)festlegen.

Sie müssen sicherstellen, dass Ihr POSITION-Wert eine gültige Position in der Liste darstellt. Wenn sie ungültig ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt.

## <a name="cdoctemplateinitialupdateframe"></a><a name="initialupdateframe"></a>CDocTemplate::InitialUpdateFrame

Initialisiert das Rahmenfenster und macht es optional sichtbar.

```
virtual void InitialUpdateFrame(
    CFrameWnd* pFrame,
    CDocument* pDoc,
    BOOL bMakeVisible = TRUE);
```

### <a name="parameters"></a>Parameter

*pFrame*<br/>
Das Rahmenfenster, das die erste Aktualisierung benötigt.

*pDoc*<br/>
Das Dokument, dem der Rahmen zugeordnet ist. Kann den Wert NULL haben.

*bMakeVisible*<br/>
Gibt an, ob der Rahmen sichtbar und aktiv werden soll.

### <a name="remarks"></a>Bemerkungen

Rufen `IntitialUpdateFrame` Sie an, `CreateNewFrame`nachdem Sie einen neuen Frame mit erstellt haben. Wenn Sie diese Funktion aufrufen, werden `OnInitialUpdate` die Ansichten in diesem Rahmenfenster ihre Aufrufe empfangen. Wenn zuvor keine aktive Ansicht vorhanden war, wird die primäre Ansicht des Rahmenfensters aktiviert. Die primäre Ansicht ist eine Ansicht mit einer untergeordneten ID von AFX_IDW_PANE_FIRST. Schließlich wird das Rahmenfenster sichtbar gemacht, wenn *bMakeVisible* ungleich Null ist. Wenn *bMakeVisible* Null ist, bleiben der aktuelle Fokus und der sichtbare Status des Rahmenfensters unverändert.

Es ist nicht erforderlich, diese Funktion aufzurufen, wenn sie die Implementierung von File New und File Open des Frameworks verwendet.

## <a name="cdoctemplateloadtemplate"></a><a name="loadtemplate"></a>CDocTemplate::LoadTemplate

Lädt die Ressourcen `CDocTemplate` für eine bestimmte oder abgeleitete Klasse.

```
virtual void LoadTemplate();
```

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird vom Framework aufgerufen, um `CDocTemplate` die Ressourcen für eine bestimmte oder abgeleitete Klasse zu laden. Normalerweise wird es während der Konstruktion aufgerufen, es sei denn, die Vorlage wird global erstellt. In diesem Fall wird `LoadTemplate` der Aufruf von verzögert, bis [CWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) aufgerufen wird.

## <a name="cdoctemplatematchdoctype"></a><a name="matchdoctype"></a>CDocTemplate::MatchDocType

Bestimmt den Grad der Vertrauensart in die Übereinstimmung zwischen einem Dokumenttyp und dieser Vorlage.

```
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,
    CDocument*& rpDocMatch);
```

### <a name="parameters"></a>Parameter

*lpszPathName*<br/>
Pfadname der Datei, deren Typ bestimmt werden soll.

*rpDocMatch*<br/>
Zeiger auf ein Dokument, dem das übereinstimmende Dokument zugewiesen ist, wenn die von *lpszPathName* angegebene Datei bereits geöffnet ist.

### <a name="return-value"></a>Rückgabewert

Ein Wert **Confidence** aus der Confidence-Enumeration, der wie folgt definiert ist:

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

Verwenden Sie diese Funktion, um den Typ der Dokumentvorlage zu bestimmen, die zum Öffnen einer Datei verwendet werden soll. Wenn Ihre Anwendung z. B. mehrere Dateitypen unterstützt, können Sie mit dieser Funktion ermitteln, `MatchDocType` welche der verfügbaren Dokumentvorlagen für eine bestimmte Datei geeignet ist, indem Sie nacheinander für jede Vorlage aufrufen und eine Vorlage entsprechend dem zurückgegebenen Konfidenzwert auswählen.

Wenn die von *lpszPathName* angegebene Datei bereits `CDocTemplate::yesAlreadyOpen` geöffnet ist, `CDocument` gibt diese Funktion das Objekt der Datei zurück und kopiert es in das Objekt bei *rpDocMatch*.

Wenn die Datei nicht geöffnet ist, aber die Erweiterung `CDocTemplate::filterExt`in *lpszPathName* mit der von angegebenen Erweiterung übereinstimmt, gibt diese Funktion zurück `CDocTemplate::yesAttemptNative` und setzt *rpDocMatch* auf NULL. Weitere Informationen `CDocTemplate::filterExt`zu finden Sie unter [CDocTemplate::GetDocString](#getdocstring).

Wenn keiner der beiden Argumente `CDocTemplate::yesAttemptForeign`wahr ist, gibt die Funktion zurück.

Die Standardimplementierung gibt `CDocTemplate::maybeAttemptForeign` `CDocTemplate::maybeAttemptNative`nicht zurück oder . Überschreiben Sie diese Funktion, um typgerechte Logik zu implementieren, **Confidence** die für Ihre Anwendung geeignet ist, und verwenden Sie diese beiden Werte möglicherweise aus der Confidence-Enumeration.

## <a name="cdoctemplateopendocumentfile"></a><a name="opendocumentfile"></a>CDocTemplate::OpenDocumentFile

Öffnet eine Datei, die durch einen Pfad angegeben wird.

```
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;

virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU) = 0;
```

### <a name="parameters"></a>Parameter

*lpszPathName*<br/>
[in] Zeigen Sie mit dem Zeiger auf den Pfad der Datei, die das zu öffnende Dokument enthält.

*bAddToMRU*<br/>
[in] TRUE gibt an, dass das Dokument eine der neuesten Dateien ist. FALSE gibt an, dass das Dokument nicht zu den neuesten Dateien gehört.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Dokument, dessen Datei von *lpszPathName*benannt ist; NULL, wenn sie nicht erfolgreich ist.

### <a name="remarks"></a>Bemerkungen

Öffnet die Datei, deren Pfad von *lpszPathName*angegeben ist. Wenn *lpszPathName* NULL ist, wird eine neue Datei erstellt, die ein Dokument des Typs enthält, der dieser Vorlage zugeordnet ist.

## <a name="cdoctemplateremovedocument"></a><a name="removedocument"></a>CDocTemplate::RemoveDocument

Entfernt das Dokument, auf das *pDoc* zeigt, aus der Liste der Dokumente, die dieser Vorlage zugeordnet sind.

```
virtual void RemoveDocument(CDocument* pDoc);
```

### <a name="parameters"></a>Parameter

*pDoc*<br/>
Zeigen Sie auf das zu entfernende Dokument.

### <a name="remarks"></a>Bemerkungen

Die abgeleiteten Klassen `CMultiDocTemplate` und `CSingleDocTemplate` überschreiben diese Funktion. Wenn Sie eine eigene Dokumentvorlagenklasse `CDocTemplate`von ableiten, muss die abgeleitete Klasse diese Funktion überschreiben.

## <a name="cdoctemplatesaveallmodified"></a><a name="saveallmodified"></a>CDocTemplate::SaveAllModified

Speichert alle Dokumente, die geändert wurden.

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>Rückgabewert

Un-Null, wenn erfolgreich; andernfalls 0.

## <a name="cdoctemplatesetcontainerinfo"></a><a name="setcontainerinfo"></a>CDocTemplate::SetContainerInfo

Bestimmt die Ressourcen für OLE-Container beim Bearbeiten eines ortsgebundenen OLE-Elements.

```
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```

### <a name="parameters"></a>Parameter

*nIDOleInPlaceContainer*<br/>
Die ID der Ressourcen, die verwendet werden, wenn ein eingebettetes Objekt aktiviert wird.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um die Ressourcen festzulegen, die verwendet werden sollen, wenn ein OLE-Objekt an Ort und Stelle aktiviert ist. Diese Ressourcen können Menüs und Beschleunigertabellen enthalten. Diese Funktion wird in der Regel in der [CWinApp::InitInstance-Funktion](../../mfc/reference/cwinapp-class.md#initinstance) Ihrer Anwendung aufgerufen.

Das mit *nIDOleInPlaceContainer* verknüpfte Menü enthält Trennzeichen, mit denen das Menü des aktivierten in-Place-Elements mit dem Menü der Containeranwendung zusammengeführt werden kann. Weitere Informationen zum Zusammenführen von Server- und Containermenüs finden Sie im Artikel [Menüs und Ressourcen (OLE)](../../mfc/menus-and-resources-ole.md).

## <a name="cdoctemplatesetdefaulttitle"></a><a name="setdefaulttitle"></a>CDocTemplate::SetDefaultTitle

Rufen Sie diese Funktion auf, um den Standardtitel des Dokuments zu laden und in der Titelleiste des Dokuments anzuzeigen.

```
virtual void SetDefaultTitle(CDocument* pDocument) = 0;
```

### <a name="parameters"></a>Parameter

*pDocument*<br/>
Zeiger auf das Dokument, dessen Titel festgelegt werden soll.

### <a name="remarks"></a>Bemerkungen

Informationen zum Standardtitel finden Sie `CDocTemplate::docName` in der Beschreibung von [cDocTemplate::GetDocString](#getdocstring).

## <a name="cdoctemplatesetserverinfo"></a><a name="setserverinfo"></a>CDocTemplate::SetServerInfo

Bestimmt die Ressourcen und Klassen, wenn das Serverdokument direkt eingebettet oder bearbeitet wird.

```
void SetServerInfo(
    UINT nIDOleEmbedding,
    UINT nIDOleInPlaceServer = 0,
    CRuntimeClass* pOleFrameClass = NULL,
    CRuntimeClass* pOleViewClass = NULL);
```

### <a name="parameters"></a>Parameter

*nIDOleEmbedding*<br/>
Die ID der Ressourcen, die beim Öffnen eines eingebetteten Objekts in einem separaten Fenster verwendet werden.

*nIDOleInPlaceServer*<br/>
Die ID der Ressourcen, die verwendet werden, wenn ein eingebettetes Objekt an Ort und Stelle aktiviert wird.

*pOleFrameClass*<br/>
Zeiger auf eine [CRuntimeClass-Struktur, die](../../mfc/reference/cruntimeclass-structure.md) Klasseninformationen für das Framefensterobjekt enthält, das bei der ortsnahe Aktivierung erstellt wurde.

*pOleViewClass*<br/>
Zeiger auf `CRuntimeClass` eine Struktur, die Klasseninformationen für das Ansichtsobjekt enthält, das bei der ortsnahe Aktivierung erstellt wurde.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Memberfunktion auf, um Ressourcen zu identifizieren, die von der Serveranwendung verwendet werden, wenn der Benutzer die Aktivierung eines eingebetteten Objekts anfordert. Diese Ressourcen bestehen aus Menüs und Beschleunigertabellen. Diese Funktion wird in `InitInstance` der Regel in der Ihrer Anwendung aufgerufen.

Das mit *nIDOleInPlaceServer* verknüpfte Menü enthält Trennzeichen, mit denen das Servermenü mit dem Menü des Containers zusammengeführt werden kann. Weitere Informationen zum Zusammenführen von Server- und Containermenüs finden Sie im Artikel [Menüs und Ressourcen (OLE)](../../mfc/menus-and-resources-ole.md).

## <a name="cdoctemplatecreatepreviewframe"></a><a name="createpreviewframe"></a>CDocTemplate::CreatePreviewFrame

Erstellt einen untergeordneten Rahmen, der für Rich Preview verwendet wird.

```
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,
    CDocument* pDoc);
```

### <a name="parameters"></a>Parameter

*pParentWnd*<br/>
Ein Zeiger auf ein übergeordnetes Fenster (in der Regel von der Shell bereitgestellt).

*pDoc*<br/>
Ein Zeiger auf ein Dokumentobjekt, dessen Inhalt in der Vorschau angezeigt wird.

### <a name="return-value"></a>Rückgabewert

Ein gültiger Zeiger `CFrameWnd` auf ein Objekt oder NULL, wenn die Erstellung fehlschlägt.

### <a name="remarks"></a>Bemerkungen

## <a name="cdoctemplatesetpreviewinfo"></a><a name="setpreviewinfo"></a>CDocTemplate::SetPreviewInfo

Richtet den Out-of-Process-Vorschauhandler ein.

```
void SetPreviewInfo(
    UINT nIDPreviewFrame,
    CRuntimeClass* pPreviewFrameClass = NULL,
    CRuntimeClass* pPreviewViewClass = NULL);
```

### <a name="parameters"></a>Parameter

*nIDPreviewFrame*<br/>
Gibt eine Ressourcen-ID des Vorschaurahmens an.

*pPreviewFrameClass*<br/>
Gibt einen Zeiger auf eine Laufzeitklasseninformationsstruktur des Vorschauframes an.

*pPreviewViewClass*<br/>
Gibt einen Zeiger auf eine Laufzeitklasseninformationsstruktur der Vorschauansicht an.

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

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
