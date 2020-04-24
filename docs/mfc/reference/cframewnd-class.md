---
title: CFrameWnd-Klasse
ms.date: 11/04/2016
f1_keywords:
- CFrameWnd
- AFXWIN/CFrameWnd
- AFXWIN/CFrameWnd::CFrameWnd
- AFXWIN/CFrameWnd::ActivateFrame
- AFXWIN/CFrameWnd::BeginModalState
- AFXWIN/CFrameWnd::Create
- AFXWIN/CFrameWnd::CreateView
- AFXWIN/CFrameWnd::DockControlBar
- AFXWIN/CFrameWnd::EnableDocking
- AFXWIN/CFrameWnd::EndModalState
- AFXWIN/CFrameWnd::FloatControlBar
- AFXWIN/CFrameWnd::GetActiveDocument
- AFXWIN/CFrameWnd::GetActiveFrame
- AFXWIN/CFrameWnd::GetActiveView
- AFXWIN/CFrameWnd::GetControlBar
- AFXWIN/CFrameWnd::GetDockState
- AFXWIN/CFrameWnd::GetMenuBarState
- AFXWIN/CFrameWnd::GetMenuBarVisibility
- AFXWIN/CFrameWnd::GetMessageBar
- AFXWIN/CFrameWnd::GetMessageString
- AFXWIN/CFrameWnd::GetTitle
- AFXWIN/CFrameWnd::InitialUpdateFrame
- AFXWIN/CFrameWnd::InModalState
- AFXWIN/CFrameWnd::IsTracking
- AFXWIN/CFrameWnd::LoadAccelTable
- AFXWIN/CFrameWnd::LoadBarState
- AFXWIN/CFrameWnd::LoadFrame
- AFXWIN/CFrameWnd::NegotiateBorderSpace
- AFXWIN/CFrameWnd::OnBarCheck
- AFXWIN/CFrameWnd::OnContextHelp
- AFXWIN/CFrameWnd::OnSetPreviewMode
- AFXWIN/CFrameWnd::OnUpdateControlBarMenu
- AFXWIN/CFrameWnd::RecalcLayout
- AFXWIN/CFrameWnd::SaveBarState
- AFXWIN/CFrameWnd::SetActivePreviewView
- AFXWIN/CFrameWnd::SetActiveView
- AFXWIN/CFrameWnd::SetDockState
- AFXWIN/CFrameWnd::SetMenuBarState
- AFXWIN/CFrameWnd::SetMenuBarVisibility
- AFXWIN/CFrameWnd::SetMessageText
- AFXWIN/CFrameWnd::SetProgressBarPosition
- AFXWIN/CFrameWnd::SetProgressBarRange
- AFXWIN/CFrameWnd::SetProgressBarState
- AFXWIN/CFrameWnd::SetTaskbarOverlayIcon
- AFXWIN/CFrameWnd::SetTitle
- AFXWIN/CFrameWnd::ShowControlBar
- AFXWIN/CFrameWnd::ShowOwnedWindows
- AFXWIN/CFrameWnd::OnCreateClient
- AFXWIN/CFrameWnd::OnHideMenuBar
- AFXWIN/CFrameWnd::OnShowMenuBar
- AFXWIN/CFrameWnd::m_bAutoMenuEnable
- AFXWIN/CFrameWnd::rectDefault
helpviewer_keywords:
- CFrameWnd [MFC], CFrameWnd
- CFrameWnd [MFC], ActivateFrame
- CFrameWnd [MFC], BeginModalState
- CFrameWnd [MFC], Create
- CFrameWnd [MFC], CreateView
- CFrameWnd [MFC], DockControlBar
- CFrameWnd [MFC], EnableDocking
- CFrameWnd [MFC], EndModalState
- CFrameWnd [MFC], FloatControlBar
- CFrameWnd [MFC], GetActiveDocument
- CFrameWnd [MFC], GetActiveFrame
- CFrameWnd [MFC], GetActiveView
- CFrameWnd [MFC], GetControlBar
- CFrameWnd [MFC], GetDockState
- CFrameWnd [MFC], GetMenuBarState
- CFrameWnd [MFC], GetMenuBarVisibility
- CFrameWnd [MFC], GetMessageBar
- CFrameWnd [MFC], GetMessageString
- CFrameWnd [MFC], GetTitle
- CFrameWnd [MFC], InitialUpdateFrame
- CFrameWnd [MFC], InModalState
- CFrameWnd [MFC], IsTracking
- CFrameWnd [MFC], LoadAccelTable
- CFrameWnd [MFC], LoadBarState
- CFrameWnd [MFC], LoadFrame
- CFrameWnd [MFC], NegotiateBorderSpace
- CFrameWnd [MFC], OnBarCheck
- CFrameWnd [MFC], OnContextHelp
- CFrameWnd [MFC], OnSetPreviewMode
- CFrameWnd [MFC], OnUpdateControlBarMenu
- CFrameWnd [MFC], RecalcLayout
- CFrameWnd [MFC], SaveBarState
- CFrameWnd [MFC], SetActivePreviewView
- CFrameWnd [MFC], SetActiveView
- CFrameWnd [MFC], SetDockState
- CFrameWnd [MFC], SetMenuBarState
- CFrameWnd [MFC], SetMenuBarVisibility
- CFrameWnd [MFC], SetMessageText
- CFrameWnd [MFC], SetProgressBarPosition
- CFrameWnd [MFC], SetProgressBarRange
- CFrameWnd [MFC], SetProgressBarState
- CFrameWnd [MFC], SetTaskbarOverlayIcon
- CFrameWnd [MFC], SetTitle
- CFrameWnd [MFC], ShowControlBar
- CFrameWnd [MFC], ShowOwnedWindows
- CFrameWnd [MFC], OnCreateClient
- CFrameWnd [MFC], OnHideMenuBar
- CFrameWnd [MFC], OnShowMenuBar
- CFrameWnd [MFC], m_bAutoMenuEnable
- CFrameWnd [MFC], rectDefault
ms.assetid: e2220aba-5bf4-4002-b960-fbcafcad01f1
ms.openlocfilehash: 3bb93420b39be5d6fb9a6691cec8300fdccb0e73
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754979"
---
# <a name="cframewnd-class"></a>CFrameWnd-Klasse

Stellt die Funktionalität eines Windows-SDI-Rahmenfensters (Single Document Interface) bereit, wobei es sich um ein überlappendes oder ein Popupfenster handeln kann. Ebenfalls bereitgestellt werden Member zum Verwalten des Fensters.

## <a name="syntax"></a>Syntax

```
class CFrameWnd : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFrameWnd::CFrameWnd](#cframewnd)|Erstellt ein `CFrameWnd`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFrameWnd::ActivateFrame](#activateframe)|Macht den Rahmen sichtbar und für den Benutzer verfügbar.|
|[CFrameWnd::BeginModalState](#beginmodalstate)|Legt das Rahmenfenster auf modal fest.|
|[CFrameWnd::Erstellen](#create)|Rufen Sie das Windows-Rahmenfenster auf, `CFrameWnd` das dem Objekt zugeordnet ist, und initialisieren Sie es.|
|[CFrameWnd::CreateView](#createview)|Erstellt eine Ansicht innerhalb eines Rahmens, die nicht von `CView`abgeleitet ist.|
|[CFrameWnd::DockControlBar](#dockcontrolbar)|Dockt eine Steuerleiste an.|
|[CFrameWnd::EnableDocking](#enabledocking)|Ermöglicht das Andocken einer Steuerleiste.|
|[CFrameWnd::EndModalState](#endmodalstate)|Beendet den Modalzustand des Rahmenfensters. Aktiviert alle Fenster, `BeginModalState`die von deaktiviert sind.|
|[CFrameWnd::FloatControlBar](#floatcontrolbar)|Schwimmt eine Steuerleiste.|
|[CFrameWnd::GetActiveDocument](#getactivedocument)|Gibt das `CDocument` aktive Objekt zurück.|
|[CFrameWnd::GetActiveFrame](#getactiveframe)|Gibt das `CFrameWnd` aktive Objekt zurück.|
|[CFrameWnd::GetActiveView](#getactiveview)|Gibt das `CView` aktive Objekt zurück.|
|[CFrameWnd::GetControlBar](#getcontrolbar)|Ruft die Steuerleiste ab.|
|[CFrameWnd::GetDockState](#getdockstate)|Ruft den Dockstatus eines Rahmenfensters ab.|
|[CFrameWnd::GetMenuBarState](#getmenubarstate)|Ruft den Anzeigestatus des Menüs in der aktuellen MFC-Anwendung ab.|
|[CFrameWnd::GetMenuBarVisibility](#getmenubarvisibility)|Gibt an, ob das Standardverhalten des Menüs in der aktuellen MFC-Anwendung ausgeblendet oder sichtbar ist.|
|[CFrameWnd::GetMessageBar](#getmessagebar)|Gibt einen Zeiger auf die Statusleiste zurück, die zum Rahmenfenster gehört.|
|[CFrameWnd::GetMessageString](#getmessagestring)|Ruft eine Nachricht ab, die einer Befehls-ID entspricht.|
|[CFrameWnd::GetTitle](#gettitle)|Ruft den Titel der zugehörigen Steuerleiste ab.|
|[CFrameWnd::InitialUpdateFrame](#initialupdateframe)|Bewirkt, dass die Memberfunktion, die `OnInitialUpdate` zu allen Ansichten im Rahmenfenster gehört, aufgerufen wird.|
|[CFrameWnd::InModalState](#inmodalstate)|Gibt einen Wert zurück, der angibt, ob sich ein Rahmenfenster in einem Modalzustand befindet.|
|[CFrameWnd::IsTracking](#istracking)|Bestimmt, ob die Splitterleiste gerade verschoben wird.|
|[CFrameWnd::LoadAccelTable](#loadacceltable)|Rufen Sie den Laden einer Beschleunigertabelle auf.|
|[CFrameWnd::LoadBarState](#loadbarstate)|Rufen Sie die Einstellungen für die Steuerleiste auf, um die Einstellungen der Steuerleiste wiederherzustellen.|
|[CFrameWnd::LoadFrame](#loadframe)|Aufruf zum dynamischen Erstellen eines Rahmenfensters aus Ressourceninformationen.|
|[CFrameWnd::NegotiateBorderSpace](#negotiateborderspace)|Verhandelt den Rahmenbereich im Rahmenfenster.|
|[CFrameWnd::OnBarCheck](#onbarcheck)|Wird aufgerufen, wenn eine Aktion auf der angegebenen Steuerleiste ausgeführt wird.|
|[CFrameWnd::OnContextHelp](#oncontexthelp)|Behandelt die SHIFT+F1-Hilfe für ortsspezifische Elemente.|
|[CFrameWnd::OnSetPreviewMode](#onsetpreviewmode)|Legt das Hauptrahmenfenster der Anwendung in den Druckvorschaumodus und aus dem Druckvorschaumodus fest.|
|[CFrameWnd::OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|Wird vom Framework aufgerufen, wenn das zugehörige Menü aktualisiert wird.|
|[CFrameWnd::RecalcLayout](#recalclayout)|Positioniert die Steuerleisten `CFrameWnd` des Objekts neu.|
|[CFrameWnd::SaveBarState](#savebarstate)|Rufen Sie an, um die Einstellungen der Steuerleiste zu speichern.|
|[CFrameWnd::SetActivePreviewView](#setactivepreviewview)|Legt die angegebene Ansicht als aktive Ansicht für Rich Preview fest.|
|[CFrameWnd::SetActiveView](#setactiveview)|Legt das `CView` aktive Objekt fest.|
|[CFrameWnd::SetDockState](#setdockstate)|Rufen Sie an, um das Rahmenfenster im Hauptfenster andocken zu können.|
|[CFrameWnd::SetMenuBarState](#setmenubarstate)|Legt den Anzeigestatus des Menüs in der aktuellen MFC-Anwendung auf ausgeblendet oder angezeigt fest.|
|[CFrameWnd::SetMenuBarVisibility](#setmenubarvisibility)|Legt fest, dass das Standardverhalten des Menüs in der aktuellen MFC-Anwendung entweder ausgeblendet oder sichtbar ist.|
|[CFrameWnd::SetMessageText](#setmessagetext)|Legt den Text einer Standardstatusleiste fest.|
|[CFrameWnd::SetProgressBarPosition](#setprogressbarposition)|Legt die aktuelle Position für die auf der Taskleiste angezeigte Windows 7-Fortschrittsleiste fest.|
|[CFrameWnd::SetProgressBarRange](#setprogressbarrange)|Legt den Bereich für die auf der Taskleiste angezeigte Windows 7-Fortschrittsleiste fest.|
|[CFrameWnd::SetProgressBarState](#setprogressbarstate)|Legt den Typ und den Status der Fortschrittsanzeige fest, die auf einer Taskleistenschaltfläche angezeigt wird.|
|[CFrameWnd::SetTaskbarOverlayIcon](#settaskbaroverlayicon)|Ist überladen. Wendet ein Overlay auf eine Taskleistenschaltfläche an, um den Anwendungsstatus oder eine Benachrichtigung an den Benutzer anzugeben.|
|[CFrameWnd::SetTitle](#settitle)|Legt den Titel der zugehörigen Steuerleiste fest.|
|[CFrameWnd::ShowControlBar](#showcontrolbar)|Rufen Sie an, um die Steuerleiste anzuzeigen.|
|[CFrameWnd::ShowOwnedWindows](#showownedwindows)|Zeigt alle Fenster an, `CFrameWnd` die abhängig vom Objekt sind.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFrameWnd::OnCreateClient](#oncreateclient)|Erstellt ein Clientfenster für den Rahmen.|
|[CFrameWnd::OnHideMenuBar](#onhidemenubar)|Wird aufgerufen, bevor das Menü in der aktuellen MFC-Anwendung ausgeblendet ist.|
|[CFrameWnd::OnShowMenuBar](#onshowmenubar)|Wird aufgerufen, bevor das Menü in der aktuellen MFC-Anwendung angezeigt wird.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFrameWnd::m_bAutoMenuEnable](#m_bautomenuenable)|Steuert die automatische Aktivierung und Deaktivierung der Funktionalität für Menüelemente.|
|[CFrameWnd::rectDefault](#rectdefault)|Übergeben Sie `CRect` diese statische Als `CFrameWnd` Parameter beim Erstellen eines Objekts, damit Windows die anfangse Größe und Position des Fensters auswählen kann.|

## <a name="remarks"></a>Bemerkungen

Um ein nützliches Rahmenfenster für Ihre Anwendung `CFrameWnd`zu erstellen, leiten Sie eine Klasse aus ab. Fügen Sie der abgeleiteten Klasse Membervariablen hinzu, um daten zu speichern, die für Ihre Anwendung spezifisch sind. Implementieren Sie Meldungshandler-Memberfunktionen und eine Meldungszuordnung in der abgeleiteten Klasse, um anzugeben, was passiert, wenn Meldungen an das Fenster weitergeleitet werden.

Es gibt drei Möglichkeiten, ein Rahmenfenster zu erstellen:

- Erstellen Sie es direkt mit [Create](#create).

- Erstellen Sie es direkt mit [LoadFrame](#loadframe).

- Erstellen Sie es indirekt mithilfe einer Dokumentvorlage.

Bevor Sie `Create` entweder `LoadFrame`oder aufrufen, müssen Sie das Framewindowobjekt auf dem Heap mithilfe des **neuen** C++-Operators erstellen. Vor `Create`dem Aufruf können Sie auch eine Fensterklasse mit der globalen Funktion [AfxRegisterWndClass](../../mfc/reference/application-information-and-management.md#afxregisterwndclass) registrieren, um das Symbol und die Klassenstile für den Frame festzulegen.

Verwenden `Create` Sie die Memberfunktion, um die Erstellungsparameter des Frames als unmittelbare Argumente zu übergeben.

`LoadFrame`erfordert weniger `Create`Argumente als und ruft stattdessen die meisten Standardwerte aus Ressourcen ab, einschließlich Beschriftung, Symbol, Beschleunigertabelle und Menü des Frames. Um von `LoadFrame`zugreifen zu können, müssen alle diese Ressourcen über dieselbe Ressourcen-ID verfügen (z. B. IDR_MAINFRAME).

Wenn `CFrameWnd` ein Objekt Ansichten und Dokumente enthält, werden sie indirekt vom Framework und nicht direkt vom Programmierer erstellt. Das `CDocTemplate` Objekt orchestriert die Erstellung des Rahmens, die Erstellung der enthaltenden Ansichten und die Verbindung der Ansichten mit dem entsprechenden Dokument. Die Parameter `CDocTemplate` des Konstruktors geben die `CRuntimeClass` der drei beteiligten Klassen an (Dokument, Rahmen und Ansicht). Ein `CRuntimeClass` Objekt wird vom Framework verwendet, um dynamisch neue Frames zu erstellen, wenn vom Benutzer angegeben (z. B. mithilfe des Befehls Datei neu oder des Befehls "Fenster Neu" (Multiple Document Interface, MDI).

Eine von `CFrameWnd` der Frame-Window-Klasse abgeleitete Frame-Window-Klasse muss mit DECLARE_DYNCREATE deklariert werden, damit der obige RUNTIME_CLASS Mechanismus ordnungsgemäß funktioniert.

A `CFrameWnd` enthält Standardimplementierungen, um die folgenden Funktionen eines Hauptfensters in einer typischen Windows-Anwendung auszuführen:

- Ein `CFrameWnd` Rahmenfenster verfolgt eine aktuell aktive Ansicht, die unabhängig vom aktiven Windows-Fenster oder dem aktuellen Eingabefokus ist. Wenn der Rahmen reaktiviert wird, wird `CView::OnActivateView`die aktive Ansicht durch Aufrufen benachrichtigt.

- Befehlsmeldungen und viele allgemeine Frame-Benachrichtigungen, `OnSetFocus`einschließlich `OnHScroll`der `OnVScroll` von `CWnd`der behandelten `CFrameWnd` , und Funktionen von werden von einem Framefenster an die aktuell aktive Ansicht delegiert.

- Die aktuell aktive Ansicht (oder das derzeit aktive mDI-untergeordnete Rahmenfenster im Fall eines MDI-Frames) kann die Beschriftung des Rahmenfensters bestimmen. Diese Funktion kann deaktiviert werden, indem Sie das FWS_ADDTOTITLE Stilbit des Rahmenfensters deaktivieren.

- Ein `CFrameWnd` Rahmenfenster verwaltet die Positionierung der Steuerleisten, Ansichten und anderer untergeordneter Fenster im Clientbereich des Rahmenfensters. Ein Rahmenfenster führt auch eine Leerlaufaktualisierung von Symbolleisten- und anderen Steuerleistenschaltflächen durch. Ein `CFrameWnd` Rahmenfenster verfügt auch über Standardimplementierungen von Befehlen zum Ein- und Ausschalten der Symbol- und Statusleiste.

- Ein `CFrameWnd` Rahmenfenster verwaltet die Hauptmenüleiste. Wenn ein Popupmenü angezeigt wird, verwendet das Rahmenfenster den UPDATE_COMMAND_UI-Mechanismus, um zu bestimmen, welche Menüelemente aktiviert, deaktiviert oder aktiviert werden sollen. Wenn der Benutzer ein Menüelement auswählt, aktualisiert das Rahmenfenster die Statusleiste mit der Nachrichtenzeichenfolge für diesen Befehl.

- Ein `CFrameWnd` Rahmenfenster verfügt über eine optionale Beschleunigertabelle, die Tastaturbeschleuniger automatisch übersetzt.

- In `CFrameWnd` einem Rahmenfenster ist eine `LoadFrame` optionale Hilfe-ID festgelegt, die für kontextabhängige Hilfe verwendet wird. Ein Rahmenfenster ist der Hauptorchestrator von semimodalen Zuständen wie kontextsensitiver Hilfe (SHIFT+F1) und Druckvorschaumodi.

- Ein `CFrameWnd` Rahmenfenster öffnet eine Datei, die aus dem Datei-Manager gezogen und im Rahmenfenster abgelegt wird. Wenn eine Dateierweiterung registriert und der Anwendung zugeordnet ist, reagiert das Framefenster auf die offene Anforderung (Dynamic Data Exchange, DDE), die auftritt, wenn der Benutzer eine Datendatei im Datei-Manager öffnet oder wenn die `ShellExecute` Windows-Funktion aufgerufen wird.

- Wenn das Rahmenfenster das Hauptanwendungsfenster `CWinThread::m_pMainWnd`ist (d. h.), wenn der Benutzer die Anwendung schließt, `OnClose` fordert `OnQueryEndSession`das Rahmenfenster den Benutzer auf, alle geänderten Dokumente zu speichern (für und ).

- Wenn das Rahmenfenster das Hauptanwendungsfenster ist, ist das Rahmenfenster der Kontext für die Ausführung von WinHelp. Beim Schließen des Rahmenfensters wird WINHELP geschlossen. EXE, wenn es für Hilfe für diese Anwendung gestartet wurde.

Verwenden Sie den **C++-Löschoperator** nicht, um ein Rahmenfenster zu zerstören. Verwenden Sie stattdessen `CWnd::DestroyWindow`. Die `CFrameWnd` Implementierung `PostNcDestroy` von löscht das C++-Objekt, wenn das Fenster zerstört wird. Wenn der Benutzer das Rahmenfenster `OnClose` schließt, `DestroyWindow`ruft der Standardhandler auf .

Weitere Informationen `CFrameWnd`zu finden Sie unter [Frame Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CFrameWnd`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="cframewndactivateframe"></a><a name="activateframe"></a>CFrameWnd::ActivateFrame

Rufen Sie diese Memberfunktion auf, um das Rahmenfenster zu aktivieren und wiederherzustellen, damit es sichtbar ist und für den Benutzer verfügbar ist.

```
virtual void ActivateFrame(int nCmdShow = -1);
```

### <a name="parameters"></a>Parameter

*nCmdShow*<br/>
Gibt den Parameter an, der an [CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow)übergeben werden soll. Standardmäßig wird der Frame angezeigt und korrekt wiederhergestellt.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird in der Regel nach einem Ereignis ohne Benutzeroberfläche wie einem DDE, OLE oder einem anderen Ereignis aufgerufen, das dem Benutzer das Rahmenfenster oder seinen Inhalt anzeigen kann.

Die Standardimplementierung aktiviert den Frame und bringt ihn an den oberen Rand der Z-Reihenfolge und führt bei Bedarf die gleichen Schritte für das Hauptframefenster der Anwendung aus.

Überschreiben Sie diese Memberfunktion, um zu ändern, wie ein Frame aktiviert wird. Sie können z. B. erzwingen, dass untergeordnete MDI-Fenster maximiert werden. Fügen Sie die entsprechende Funktionalität hinzu, und rufen Sie dann die Basisklassenversion mit einer expliziten *nCmdShow*auf.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#1](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]

## <a name="cframewndbeginmodalstate"></a><a name="beginmodalstate"></a>CFrameWnd::BeginModalState

Rufen Sie diese Memberfunktion auf, um ein Framefenster modal zu machen.

```
virtual void BeginModalState();
```

## <a name="cframewndcframewnd"></a><a name="cframewnd"></a>CFrameWnd::CFrameWnd

Erstellt ein `CFrameWnd` Objekt, erstellt jedoch nicht das sichtbare Rahmenfenster.

```
CFrameWnd();
```

### <a name="remarks"></a>Bemerkungen

Rufen `Create` Sie an, um das sichtbare Fenster zu erstellen.

## <a name="cframewndcreate"></a><a name="create"></a>CFrameWnd::Erstellen

Rufen Sie das Windows-Rahmenfenster auf, `CFrameWnd` das dem Objekt zugeordnet ist, und initialisieren Sie es.

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    LPCTSTR lpszWindowName,
    DWORD dwStyle = WS_OVERLAPPEDWINDOW,
    const RECT& rect = rectDefault,
    CWnd* pParentWnd = NULL,
    LPCTSTR lpszMenuName = NULL,
    DWORD dwExStyle = 0,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parameter

*lpszClassName*<br/>
Verweist auf eine null-beendete Zeichenfolge, die die Windows-Klasse benennt. Der Klassenname kann ein beliebiger Name sein, der mit der `AfxRegisterWndClass` globalen Funktion oder der Windows-Funktion `RegisterClass` registriert ist. Wenn NULL, verwendet die `CFrameWnd` vordefinierten Standardattribute.

*lpszWindowName*<br/>
Zeigt auf eine null-terminierte Zeichenfolge, die den Fensternamen darstellt. Wird als Text für die Titelleiste verwendet.

*dwStyle*<br/>
Gibt die [Fensterstilattribute](../../mfc/reference/styles-used-by-mfc.md#window-styles) an. Fügen Sie die FWS_ADDTOTITLE-Formateinbereitung ein, wenn die Titelleiste automatisch den Namen des im Fenster dargestellten Dokuments anzeigen soll.

*Rect*<br/>
Gibt die Größe und Position des Fensters an. Mit *dem rectDefault-Wert* kann Windows die Größe und Position des neuen Fensters angeben.

*pParentWnd*<br/>
Gibt das übergeordnete Fenster dieses Rahmenfensters an. Dieser Parameter sollte NULL für Rahmenfenster der obersten Ebene sein.

*lpszMenuName*<br/>
Identifiziert den Namen der Menüressource, die mit dem Fenster verwendet werden soll. Verwenden Sie MAKEINTRESOURCE, wenn das Menü eine ganzzahlige ID anstelle einer Zeichenfolge hat. Dieser Parameter kann NULL sein.

*dwExStyle*<br/>
Gibt die erweiterten [Stilattribute](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) des Fensters an.

*pContext*<br/>
Gibt einen Zeiger auf eine [CCreateContext-Struktur](../../mfc/reference/ccreatecontext-structure.md) an. Dieser Parameter kann NULL sein.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Initialisierung erfolgreich ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Erstellen `CFrameWnd` Sie ein Objekt in zwei Schritten. Rufen Sie zunächst den Konstruktor `CFrameWnd` auf, der `Create`das Objekt erstellt, und rufen Sie `CFrameWnd` dann auf, der das Windows-Rahmenfenster erstellt und an das Objekt anfügt. `Create`initialisiert den Klassennamen und den Fensternamen des Fensters und registriert Standardwerte für den Stil, das übergeordnete Und das zugehörige Menü.

Verwenden `LoadFrame` Sie, anstatt `Create` das Rahmenfenster aus einer Ressource zu laden, anstatt deren Argumente anzugeben.

## <a name="cframewndcreateview"></a><a name="createview"></a>CFrameWnd::CreateView

Rufen `CreateView` Sie auf, um eine Ansicht innerhalb eines Frames zu erstellen.

```
CWnd* CreateView(
    CCreateContext* pContext,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>Parameter

*pContext*<br/>
Gibt den Ansichts- und Dokumenttyp an.

*nID*<br/>
Die ID-Nummer einer Ansicht.

### <a name="return-value"></a>Rückgabewert

Zeiger auf `CWnd` ein Objekt, wenn erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Memberfunktion, um `CView`"Ansichten" zu erstellen, die nicht innerhalb eines Frames abgeleitet sind. Nach `CreateView`dem Aufruf müssen Sie die Ansicht manuell auf aktiv und auf sichtbar festlegen. Diese Aufgaben werden nicht `CreateView`automatisch von ausgeführt.

## <a name="cframewnddockcontrolbar"></a><a name="dockcontrolbar"></a>CFrameWnd::DockControlBar

Bewirkt, dass eine Steuerleiste an das Rahmenfenster angedockt wird.

```cpp
void DockControlBar(
    CControlBar* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parameter

*Pbar*<br/>
Zeigt auf die zu andockende Steuerleiste.

*nDockBarID*<br/>
Bestimmt, welche Seiten des Rahmenfensters für das Andocken in Betracht gezogen werden sollen. Es kann 0 oder einer oder mehrere der folgenden sein:

- AFX_IDW_DOCKBAR_TOP Dock an der Oberseite des Rahmenfensters.

- AFX_IDW_DOCKBAR_BOTTOM Dock an der Unterseite des Rahmenfensters.

- AFX_IDW_DOCKBAR_LEFT Dock auf der linken Seite des Rahmenfensters.

- AFX_IDW_DOCKBAR_RIGHT Dock auf der rechten Seite des Rahmenfensters.

Wenn 0, kann die Steuerleiste an jede Seite angedockt werden, die für das Andocken im Zielrahmenfenster aktiviert ist.

*lpRect*<br/>
Bestimmt in Bildschirmkoordinaten, wo die Steuerleiste im Nichtclientbereich des Zielrahmenfensters angedockt wird.

### <a name="remarks"></a>Bemerkungen

Die Steuerleiste wird an eine der Seiten des Rahmenfensters angedockt, die in den Aufrufen von [CControlBar::EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking) und [CFrameWnd::EnableDocking](#enabledocking)angegeben sind. Die gewählte Seite wird durch *nDockBarID*bestimmt.

## <a name="cframewndenabledocking"></a><a name="enabledocking"></a>CFrameWnd::EnableDocking

Rufen Sie diese Funktion auf, um andockbare Steuerleisten in einem Rahmenfenster zu aktivieren.

```cpp
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parameter

*dwDockStyle*<br/>
Gibt an, welche Seiten des Rahmenfensters als Andockstellen für Steuerleisten dienen können. Es kann einer oder mehrere der folgenden sein:

- CBRS_ALIGN_TOP Ermöglicht das Andocken am oberen Rand des Clientbereichs.

- CBRS_ALIGN_BOTTOM Ermöglicht das Andocken am unteren Rand des Clientbereichs.

- CBRS_ALIGN_LEFT Ermöglicht das Andocken auf der linken Seite des Clientbereichs.

- CBRS_ALIGN_RIGHT Ermöglicht das Andocken auf der rechten Seite des Clientbereichs.

- CBRS_ALIGN_ANY Ermöglicht das Andocken auf jeder Seite des Clientbereichs.

### <a name="remarks"></a>Bemerkungen

Standardmäßig werden Steuerleisten in der folgenden Reihenfolge an eine Seite des Rahmenfensters angedockt: oben, unten, links, rechts.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CToolBar::Create](../../mfc/reference/ctoolbar-class.md#create).

## <a name="cframewndendmodalstate"></a><a name="endmodalstate"></a>CFrameWnd::EndModalState

Rufen Sie diese Memberfunktion auf, um ein Framefenster von einem modalen in einen Status ohne Modus zu ändern.

```
virtual void EndModalState();
```

### <a name="remarks"></a>Bemerkungen

`EndModalState`aktiviert alle von [BeginModalState](#beginmodalstate)deaktivierten Fenster .

## <a name="cframewndfloatcontrolbar"></a><a name="floatcontrolbar"></a>CFrameWnd::FloatControlBar

Rufen Sie diese Funktion auf, um zu bewirken, dass eine Steuerleiste nicht an das Rahmenfenster angedockt wird.

```cpp
void FloatControlBar(
    CControlBar* pBar,
    CPoint point,
    DWORD dwStyle = CBRS_ALIGN_TOP);
```

### <a name="parameters"></a>Parameter

*Pbar*<br/>
Zeigt auf die Steuerleiste, die geplatzt werden soll.

*Punkt*<br/>
Die Position in Bildschirmkoordinaten, an der die obere linke Ecke der Steuerleiste platziert wird.

*dwStyle*<br/>
Gibt an, ob die Steuerleiste horizontal oder vertikal innerhalb des neuen Rahmenfensters ausgerichtet werden soll. Es kann eine der folgenden sein:

- CBRS_ALIGN_TOP richtet die Steuerleiste vertikal aus.

- CBRS_ALIGN_BOTTOM richtet die Steuerleiste vertikal aus.

- CBRS_ALIGN_LEFT richtet die Steuerleiste horizontal aus.

- CBRS_ALIGN_RIGHT richtet die Steuerleiste horizontal aus.

Wenn Stile übergeben werden, die sowohl die horizontale als auch die vertikale Ausrichtung angeben, wird die Symbolleiste horizontal ausgerichtet.

### <a name="remarks"></a>Bemerkungen

In der Regel geschieht dies beim Starten der Anwendung, wenn das Programm einstellungen von der vorherigen Ausführung wiederherstellt.

Diese Funktion wird vom Framework aufgerufen, wenn der Benutzer einen Ablagevorgang verursacht, indem er die linke Maustaste loslässt, während die Steuerleiste über eine Position gezogen wird, die nicht zum Andocken verfügbar ist.

## <a name="cframewndgetactivedocument"></a><a name="getactivedocument"></a>CFrameWnd::GetActiveDocument

Rufen Sie diese Memberfunktion auf, `CDocument` um einen Zeiger auf den aktuellen Wert an die aktuelle aktive Ansicht zu erhalten.

```
virtual CDocument* GetActiveDocument();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das aktuelle [CDocument](../../mfc/reference/cdocument-class.md). Wenn kein aktuelles Dokument vorhanden ist, wird NULL zurückgegeben.

## <a name="cframewndgetactiveframe"></a><a name="getactiveframe"></a>CFrameWnd::GetActiveFrame

Rufen Sie diese Memberfunktion auf, um einen Zeiger auf das untergeordnete MDI-Fenster (Active Multiple Document Interface) eines MDI-Rahmenfensters zu erhalten.

```
virtual CFrameWnd* GetActiveFrame();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das aktive MDI-Untergeordnete Fenster. Wenn es sich bei der Anwendung um eine SDI-Anwendung handelt oder das MDI-Rahmenfenster kein aktives Dokument enthält, wird der implizite **Zeiger** dieser Zeiger zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Wenn kein aktives untergeordnetes MDI-Element vorhanden ist oder die Anwendung eine Single Document Interface (SDI) ist, wird der implizite **Zeiger dieser** Zeiger zurückgegeben.

## <a name="cframewndgetactiveview"></a><a name="getactiveview"></a>CFrameWnd::GetActiveView

Rufen Sie diese Memberfunktion auf, um einen Zeiger auf die aktive `CFrameWnd`Ansicht (falls vorhanden) zu erhalten, die an ein Rahmenfenster angefügt ist ( ).

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die aktuelle [CView](../../mfc/reference/cview-class.md). Wenn keine aktuelle Ansicht vorhanden ist, wird NULL zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Diese Funktion gibt NULL zurück, wenn sie `CMDIFrameWnd`für ein MDI-Hauptrahmenfenster aufgerufen wird ( ). In einer MDI-Anwendung ist dem MDI-Hauptrahmenfenster keine Ansicht zugeordnet. Stattdessen verfügt jedes einzelne `CMDIChildWnd`untergeordnete Fenster ( ) über eine oder mehrere zugeordnete Ansichten. Die aktive Ansicht in einer MDI-Anwendung kann abgerufen werden, indem Sie zuerst das aktive untergeordnete MDI-Fenster und dann die aktive Ansicht für dieses untergeordnete Fenster suchen. Das aktive mDI-Untergeordnete Fenster kann `MDIGetActive` durch `GetActiveFrame` Aufrufen der Funktion oder wie im Folgenden gezeigt gefunden werden:

[!code-cpp[NVC_MFCWindowing#2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]

## <a name="cframewndgetcontrolbar"></a><a name="getcontrolbar"></a>CFrameWnd::GetControlBar

Rufen `GetControlBar` Sie den Zugriff auf die Steuerleiste auf, die der ID zugeordnet ist.

```
CControlBar* GetControlBar(UINT nID);
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Die ID-Nummer einer Steuerleiste.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die Steuerleiste, die der ID zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Der *nID-Parameter* bezieht sich auf `Create` den eindeutigen Bezeichner, der an die Methode der Steuerleiste übergeben wird. Weitere Informationen zu Steuerleisten finden Sie im Thema [Control Bars](../../mfc/control-bars.md).

`GetControlBar`gibt die Steuerleiste zurück, auch wenn sie schwebend ist und daher derzeit kein untergeordnetes Fenster des Rahmens ist.

## <a name="cframewndgetdockstate"></a><a name="getdockstate"></a>CFrameWnd::GetDockState

Rufen Sie diese Memberfunktion auf, um Statusinformationen über `CDockState` die Steuerelementleisten des Rahmenfensters in einem Objekt zu speichern.

```cpp
void GetDockState(CDockState& state) const;
```

### <a name="parameters"></a>Parameter

*state*<br/>
Enthält den aktuellen Status der Kontrollleisten des Rahmenfensters bei der Rückgabe.

### <a name="remarks"></a>Bemerkungen

Sie können dann den `CDockState` Inhalt `CDockState::SaveState` von `Serialize`in den Speicher mit oder schreiben. Wenn Sie die Kontrollleisten später in einen vorherigen Zustand `CDockState::LoadState` `Serialize`zurücksetzen `SetDockState` möchten, laden Sie den Status mit oder , und rufen Sie dann auf, den vorherigen Status auf die Kontrollleisten des Rahmenfensters anzuwenden.

## <a name="cframewndgetmenubarstate"></a><a name="getmenubarstate"></a>CFrameWnd::GetMenuBarState

Ruft den Anzeigestatus des Menüs in der aktuellen MFC-Anwendung ab.

```
virtual DWORD GetMenuBarState();
```

### <a name="return-value"></a>Rückgabewert

Der Rückgabewert kann die folgenden Werte haben:

- AFX_MBS_VISIBLE (0x01) - Das Menü ist sichtbar.

- AFX_MBS_HIDDEN (0x02) - Das Menü ist ausgeblendet.

### <a name="remarks"></a>Bemerkungen

Wenn ein Laufzeitfehler auftritt, wird diese Methode im Debugmodus bestätigt und löst eine Ausnahme aus, die von der [CException-Klasse](../../mfc/reference/cexception-class.md) abgeleitet wurde.

## <a name="cframewndgetmenubarvisibility"></a><a name="getmenubarvisibility"></a>CFrameWnd::GetMenuBarVisibility

Gibt an, ob der Standardstatus des Menüs in der aktuellen MFC-Anwendung ausgeblendet oder sichtbar ist.

```
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```

### <a name="return-value"></a>Rückgabewert

Diese Methode gibt einen der folgenden Werte zurück:

- AFX_MBV_KEEPVISIBLE (0x01) - Das Menü wird jederzeit angezeigt und hat standardmäßig nicht den Fokus.

- AFX_MBV_DISPLAYONFOCUS (0x02) - Das Menü ist standardmäßig ausgeblendet. Wenn das Menü ausgeblendet ist, drücken Sie die ALT-Taste, um das Menü anzuzeigen und ihm den Fokus zu geben. Wenn das Menü angezeigt wird, drücken Sie die ALT- oder ESC-Taste, um es auszublenden.

- AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04) (Bitweise Kombination (OR)) - Das Menü ist standardmäßig ausgeblendet. Wenn das Menü ausgeblendet ist, drücken Sie die F10-Taste, um das Menü anzuzeigen und ihm den Fokus zu geben. Wenn das Menü angezeigt wird, drücken Sie die F10-Taste, um den Fokus auf oder außerhalb des Menüs umzuschalten. Das Menü wird angezeigt, bis Sie die ALT- oder ESC-Taste drücken, um es auszublenden.

### <a name="remarks"></a>Bemerkungen

Wenn ein Laufzeitfehler auftritt, wird diese Methode im Debugmodus bestätigt und löst eine Ausnahme aus, die von der [CException-Klasse](../../mfc/reference/cexception-class.md) abgeleitet wurde.

## <a name="cframewndgetmessagebar"></a><a name="getmessagebar"></a>CFrameWnd::GetMessageBar

Rufen Sie diese Memberfunktion auf, um einen Zeiger auf die Statusleiste abzurufen.

```
virtual CWnd* GetMessageBar();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf das Statusleistenfenster.

## <a name="cframewndgetmessagestring"></a><a name="getmessagestring"></a>CFrameWnd::GetMessageString

Überschreiben Sie diese Funktion, um benutzerdefinierte Zeichenfolgen für Befehls-IDs bereitzustellen.

```
virtual void GetMessageString(
    UINT nID,
    CString& rMessage) const;
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Ressourcen-ID der gewünschten Nachricht.

*rMessage*<br/>
`CString`Objekt, in das die Nachricht platziert werden soll.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung lädt einfach die von *nID* angegebene Zeichenfolge aus der Ressourcendatei. Diese Funktion wird vom Framework aufgerufen, wenn die Nachrichtenzeichenfolge in der Statusleiste aktualisiert werden muss.

## <a name="cframewndgettitle"></a><a name="gettitle"></a>CFrameWnd::GetTitle

Ruft den Titel des Fensterobjekts ab.

```
CString GetTitle() const;
```

### <a name="return-value"></a>Rückgabewert

Ein [CString-Objekt,](../../atl-mfc-shared/reference/cstringt-class.md) das den aktuellen Titel des Fensterobjekts enthält.

## <a name="cframewndinitialupdateframe"></a><a name="initialupdateframe"></a>CFrameWnd::InitialUpdateFrame

Rufen `IntitialUpdateFrame` Sie an, `Create`nachdem Sie einen neuen Frame mit erstellt haben.

```cpp
void InitialUpdateFrame(
    CDocument* pDoc,
    BOOL bMakeVisible);
```

### <a name="parameters"></a>Parameter

*pDoc*<br/>
Zeigt auf das Dokument, dem das Rahmenfenster zugeordnet ist. Kann den Wert NULL haben.

*bMakeVisible*<br/>
Wenn TRUE, gibt an, dass der Rahmen sichtbar und aktiv werden soll. Wenn FALSE, werden keine abhängigen Elemente sichtbar gemacht.

### <a name="remarks"></a>Bemerkungen

Dadurch werden alle Ansichten in diesem `OnInitialUpdate` Rahmenfenster ihre Anrufe empfangen.

Wenn zuvor keine aktive Ansicht vorhanden war, wird die primäre Ansicht des Rahmenfensters aktiviert. Die primäre Ansicht ist eine Ansicht mit der untergeordneten ID AFX_IDW_PANE_FIRST. Schließlich wird das Rahmenfenster sichtbar gemacht, wenn *bMakeVisible* ungleich Null ist. Wenn *bMakeVisible* 0 ist, bleibt der aktuelle Fokus und der sichtbare Status des Rahmenfensters unverändert. Es ist nicht erforderlich, diese Funktion aufzurufen, wenn sie die Implementierung von File New und File Open des Frameworks verwendet.

## <a name="cframewndinmodalstate"></a><a name="inmodalstate"></a>CFrameWnd::InModalState

Rufen Sie diese Memberfunktion auf, um zu überprüfen, ob ein Rahmenfenster modal oder moduslos ist.

```
BOOL InModalState() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, falls ja; andernfalls 0.

## <a name="cframewndistracking"></a><a name="istracking"></a>CFrameWnd::IsTracking

Rufen Sie diese Memberfunktion auf, um zu ermitteln, ob die Splitterleiste im Fenster gerade verschoben wird.

```
BOOL IsTracking() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn ein Splittervorgang ausgeführt wird; andernfalls 0.

## <a name="cframewndloadacceltable"></a><a name="loadacceltable"></a>CFrameWnd::LoadAccelTable

Rufen Sie den Aufruf auf, um die angegebene Beschleunigertabelle zu laden.

```
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```

### <a name="parameters"></a>Parameter

*lpszResourceName*<br/>
Identifiziert den Namen der Beschleunigerressource. Verwenden Sie MAKEINTRESOURCE, wenn die Ressource mit einer ganzzahligen ID identifiziert wird.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Beschleunigertabelle erfolgreich geladen wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Es kann jeweils nur eine Tabelle geladen werden.

Accelerator-Tabellen, die von Ressourcen geladen werden, werden automatisch freigegeben, wenn die Anwendung beendet wird.

Wenn Sie `LoadFrame` aufrufen, das Rahmenfenster zu erstellen, lädt das Framework eine Beschleunigertabelle zusammen mit den Menü- und Symbolressourcen, und ein nachfolgender Aufruf dieser Memberfunktion ist dann nicht erforderlich.

## <a name="cframewndloadbarstate"></a><a name="loadbarstate"></a>CFrameWnd::LoadBarState

Rufen Sie diese Funktion auf, um die Einstellungen jeder Steuerleiste wiederherzustellen, die dem Rahmenfenster gehört.

```cpp
void LoadBarState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Parameter

*lpszProfileName*<br/>
Name eines Abschnitts in der Initialisierungsdatei (INI) oder eines Schlüssels in der Windows-Registrierung, in dem Statusinformationen gespeichert werden.

### <a name="remarks"></a>Bemerkungen

Die wiederhergestellten Informationen umfassen Sichtbarkeit, horizontale/vertikale Ausrichtung, Andockzustand und Position der Steuerleiste.

Die Einstellungen, die Sie wiederherstellen möchten, müssen `LoadBarState`in die Registrierung geschrieben werden, bevor Sie aufrufen. Schreiben Sie die Informationen in die Registrierung, indem Sie [CWinApp::SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey)aufrufen. Schreiben Sie die Informationen in die INI-Datei, indem Sie [SaveBarState](#savebarstate)aufrufen.

## <a name="cframewndloadframe"></a><a name="loadframe"></a>CFrameWnd::LoadFrame

Aufruf zum dynamischen Erstellen eines Rahmenfensters aus Ressourceninformationen.

```
virtual BOOL LoadFrame(
    UINT nIDResource,
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,
    CWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parameter

*nIDResource*<br/>
Die ID der freigegebenen Ressourcen, die dem Rahmenfenster zugeordnet sind.

*dwDefaultStyle*<br/>
Der [Stil](../../mfc/reference/styles-used-by-mfc.md#window-styles)des Rahmens . Fügen Sie die FWS_ADDTOTITLE-Formateinbereitung ein, wenn die Titelleiste automatisch den Namen des im Fenster dargestellten Dokuments anzeigen soll.

*pParentWnd*<br/>
Ein Zeiger auf das übergeordnete Element des Rahmens.

*pContext*<br/>
Ein Zeiger auf eine [CCreateContext-Struktur.](../../mfc/reference/ccreatecontext-structure.md) Dieser Parameter kann NULL sein.

### <a name="remarks"></a>Bemerkungen

Erstellen `CFrameWnd` Sie ein Objekt in zwei Schritten. Rufen Sie zunächst den Konstruktor `CFrameWnd` auf, der `LoadFrame`das Objekt erstellt, und rufen Sie dann auf, `CFrameWnd` der das Windows-Rahmenfenster und die zugehörigen Ressourcen lädt und das Rahmenfenster an das Objekt anfügt. Der Parameter *nIDResource* gibt das Menü, die Beschleunigertabelle, das Symbol und die Zeichenfolgenressource des Titels für das Rahmenfenster an.

Verwenden `Create` Sie die `LoadFrame` Memberfunktion und nicht, wenn Sie alle Erstellungsparameter des Rahmenfensters angeben möchten.

Das Framework `LoadFrame` ruft auf, wenn ein Rahmenfenster mit einem Dokumentvorlagenobjekt erstellt wird.

Das Framework verwendet das *pContext-Argument,* um die Objekte anzugeben, die mit dem Rahmenfenster verbunden werden sollen, einschließlich aller enthaltenen Ansichtsobjekte. Sie können das *pContext-Argument* beim `LoadFrame`Aufrufen auf NULL setzen.

## <a name="cframewndm_bautomenuenable"></a><a name="m_bautomenuenable"></a>CFrameWnd::m_bAutoMenuEnable

Wenn dieses Datenelement aktiviert ist (standardeinstellung), werden Menüelemente, die nicht über ON_UPDATE_COMMAND_UI oder ON_COMMAND Handler verfügen, automatisch deaktiviert, wenn der Benutzer ein Menü herunterzieht.

```
BOOL m_bAutoMenuEnable;
```

### <a name="remarks"></a>Bemerkungen

Menüelemente, die über einen ON_COMMAND Handler, aber keinen ON_UPDATE_COMMAND_UI Handler verfügen, werden automatisch aktiviert.

Wenn dieser Datenmember festgelegt ist, werden Menüelemente automatisch auf die gleiche Weise aktiviert, wie Symbolleistenschaltflächen aktiviert sind.

> [!NOTE]
> `m_bAutoMenuEnable`hat keine Auswirkungen auf Menüpunkte der obersten Ebene.

Dieses Datenelement vereinfacht die Implementierung optionaler Befehle basierend auf der aktuellen Auswahl und reduziert die Notwendigkeit, ON_UPDATE_COMMAND_UI Handler zum Aktivieren und Deaktivieren von Menüelementen zu schreiben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]

## <a name="cframewndnegotiateborderspace"></a><a name="negotiateborderspace"></a>CFrameWnd::NegotiateBorderSpace

Rufen Sie diese Memberfunktion auf, um den Rahmenbereich in einem Rahmenfenster während der OLE-Vor-Ort-Aktivierung auszuhandeln.

```
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,
    LPRECT lpRectBorder);
```

### <a name="parameters"></a>Parameter

*nBorderCmd*<br/>
Enthält einen der folgenden `enum BorderCmd`Werte aus der :

- `borderGet` = 1

- `borderRequest` = 2

- `borderSet` = 3

*lpRectBorder*<br/>
Zeiger auf eine [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) oder ein [CRect-Objekt,](../../atl-mfc-shared/reference/crect-class.md) das die Koordinaten des Rahmens angibt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion `CFrameWnd` ist die Implementierung der OLE-Grenzraumaushandlung.

## <a name="cframewndonbarcheck"></a><a name="onbarcheck"></a>CFrameWnd::OnBarCheck

Wird aufgerufen, wenn eine Aktion auf der angegebenen Steuerleiste ausgeführt wird.

```
afx_msg BOOL OnBarCheck(UINT nID);
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Die ID der angezeigten Steuerleiste.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Kontrollleiste vorhanden war; andernfalls 0.

## <a name="cframewndoncontexthelp"></a><a name="oncontexthelp"></a>CFrameWnd::OnContextHelp

Behandelt die SHIFT+F1-Hilfe für ortsspezifische Elemente.

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>Bemerkungen

Um kontextsensitive Hilfe zu aktivieren, müssen Sie eine

[!code-cpp[NVC_MFCDocViewSDI#16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]

`CFrameWnd` Und fügen Sie außerdem einen Accelerator-Table-Eintrag hinzu, in der Regel UMSCHALT+F1, um diese Memberfunktion zu aktivieren.

Wenn es sich bei `OnContextHelp` Ihrer Anwendung um einen OLE-Container handelt, werden alle im Rahmenfensterobjekt enthaltenen eingefügten Elemente in den Hilfemodus versetzt. Der Cursor ändert sich in einen Pfeil und ein Fragezeichen, und der Benutzer kann dann den Mauszeiger bewegen und die linke Maustaste drücken, um ein Dialogfeld, ein Fenster, ein Menü oder eine Befehlsschaltfläche auszuwählen. Diese Memberfunktion ruft `WinHelp` die Windows-Funktion mit dem Hilfekontext des Objekts unter dem Cursor auf.

## <a name="cframewndoncreateclient"></a><a name="oncreateclient"></a>CFrameWnd::OnCreateClient

Wird vom Framework während `OnCreate`der Ausführung von aufgerufen.

```
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Parameter

*lpcs*<br/>
Ein Zeiger auf eine Windows [CREATESTRUCT-Struktur.](/windows/win32/api/winuser/ns-winuser-createstructw)

*pContext*<br/>
Ein Zeiger auf eine [CCreateContext-Struktur.](../../mfc/reference/ccreatecontext-structure.md)

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion niemals auf.

Die Standardimplementierung dieser Funktion `CView` erstellt nach Möglichkeit ein Objekt aus den in *pContext*bereitgestellten Informationen.

Überschreiben Sie diese Funktion, um `CCreateContext` werte zu überschreiben, die im Objekt übergeben werden, oder um die Art und Weise zu ändern, wie Steuerelemente im Hauptclientbereich des Rahmenfensters erstellt werden. Die `CCreateContext` Member, die Sie überschreiben können, werden in der [CCreateContext-Klasse](../../mfc/reference/ccreatecontext-structure.md) beschrieben.

> [!NOTE]
> Ersetzen Sie keine in `CREATESTRUCT` der Struktur übergebenen Werte. Sie sind nur für den Informationsgebrauch. Wenn Sie z. B. das anfängliche Fensterrechteck `CWnd` überschreiben möchten, überschreiben Sie die Memberfunktion [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).

## <a name="cframewndonhidemenubar"></a><a name="onhidemenubar"></a>CFrameWnd::OnHideMenuBar

Diese Funktion wird aufgerufen, wenn das System die Menüleiste in der aktuellen MFC-Anwendung ausblenden wird.

```
virtual void OnHideMenuBar();
```

### <a name="remarks"></a>Bemerkungen

Dieser Ereignishandler ermöglicht es Der Anwendung, benutzerdefinierte Aktionen auszuführen, wenn das System das Menü ausblenden soll. Sie können nicht verhindern, dass das Menü ausgeblendet wird, aber Sie können z. B. andere Methoden aufrufen, um den Menüstil oder -zustand abzurufen.

## <a name="cframewndonsetpreviewmode"></a><a name="onsetpreviewmode"></a>CFrameWnd::OnSetPreviewMode

Rufen Sie diese Memberfunktion auf, um für das Hauptrahmenfenster den Seitenansichtmodus zu aktivieren oder zu deaktivieren.

```
virtual void OnSetPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>Parameter

*bVorschau*<br/>
Gibt an, ob die Anwendung in den Druckvorschaumodus versetzt werden soll. Legen Sie TRUE fest, um sie in der Druckvorschau zu platzieren, FALSE, um den Vorschaumodus abzubrechen.

*pState*<br/>
Ein Zeiger auf `CPrintPreviewState` eine Struktur.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung deaktiviert alle Standardsymbolleisten und blendet das Hauptmenü und das Hauptclientfenster aus. Dadurch werden MDI-Rahmenfenster zu temporären SDI-Rahmenfenstern.

Überschreiben Sie diese Memberfunktion, um das Ausblenden und Anzeigen von Steuerleisten und anderen Rahmenfensterteilen während der Druckvorschau anzupassen. Rufen Sie die Basisklassenimplementierung innerhalb der überschriebenen Version auf.

## <a name="cframewndonshowmenubar"></a><a name="onshowmenubar"></a>CFrameWnd::OnShowMenuBar

Diese Funktion wird aufgerufen, wenn das System die Menüleiste in der aktuellen MFC-Anwendung anzeigen wird.

```
virtual void OnShowMenuBar();
```

### <a name="remarks"></a>Bemerkungen

Dieser Ereignishandler ermöglicht es Ihrer Anwendung, benutzerdefinierte Aktionen auszuführen, wenn das Menü angezeigt werden soll. Sie können nicht verhindern, dass das Menü angezeigt wird, aber Sie können z. B. andere Methoden aufrufen, um den Menüstil oder -zustand abzurufen.

## <a name="cframewndonupdatecontrolbarmenu"></a><a name="onupdatecontrolbarmenu"></a>CFrameWnd::OnUpdateControlBarMenu

Wird vom Framework aufgerufen, wenn das zugehörige Menü aktualisiert wird.

```
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parameter

*pCmdUI*<br/>
Ein Zeiger auf ein [CCmdUI-Objekt,](../../mfc/reference/ccmdui-class.md) das das Menü darstellt, das den Aktualisierungsbefehl generiert hat. Der Updatehandler ruft die [Memberfunktion Member](../../mfc/reference/ccmdui-class.md#enable) des `CCmdUI` Objekts über *pCmdUI* aktivieren auf, um die Benutzeroberfläche zu aktualisieren.

## <a name="cframewndrecalclayout"></a><a name="recalclayout"></a>CFrameWnd::RecalcLayout

Wird vom Framework aufgerufen, wenn die Standard-Steuerleisten ein- oder ausgeschaltet werden oder wenn die Größe des Rahmenfensters geändert wird.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parameter

*bNotify*<br/>
Bestimmt, ob das aktive an Ort und Stelle für das Rahmenfenster eine Benachrichtigung über die Layoutänderung erhält. Wenn TRUE, wird das Element benachrichtigt. andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung dieser Memberfunktion `CWnd` ruft `RepositionBars` die Memberfunktion auf, alle Steuerleisten im Frame sowie im `CView` Hauptclientfenster (in der Regel ein oder MDICLIENT) neu zu positionieren.

Überschreiben Sie diese Memberfunktion, um das Erscheinungsbild und Verhalten von Steuerleisten zu steuern, nachdem sich das Layout des Rahmenfensters geändert hat. Rufen Sie es beispielsweise auf, wenn Sie Die Steuerleisten ein- oder ausschalten oder eine andere Steuerleiste hinzufügen.

## <a name="cframewndrectdefault"></a><a name="rectdefault"></a>CFrameWnd::rectDefault

Übergeben Sie `CRect` diese statische Als Parameter beim Erstellen eines Fensters, damit Windows die ursprüngliche Größe und Position des Fensters auswählen kann.

```
static AFX_DATA const CRect rectDefault;
```

## <a name="cframewndsavebarstate"></a><a name="savebarstate"></a>CFrameWnd::SaveBarState

Rufen Sie diese Funktion auf, um Informationen zu jeder Steuerleiste zu speichern, die dem Rahmenfenster gehört.

```cpp
void SaveBarState(LPCTSTR lpszProfileName) const;
```

### <a name="parameters"></a>Parameter

*lpszProfileName*<br/>
Name eines Abschnitts in der Initialisierungsdatei oder eines Schlüssels in der Windows-Registrierung, in dem Statusinformationen gespeichert werden.

### <a name="remarks"></a>Bemerkungen

Diese Informationen können aus der Initialisierungsdatei mit [LoadBarState](#loadbarstate)gelesen werden. Zu den gespeicherten Informationen gehören Sichtbarkeit, horizontale/vertikale Ausrichtung, Andockzustand und Position der Steuerleiste.

## <a name="cframewndsetactivepreviewview"></a><a name="setactivepreviewview"></a>CFrameWnd::SetActivePreviewView

Legt die angegebene Ansicht als aktive Ansicht für Rich Preview fest.

```cpp
void SetActivePreviewView(CView* pViewNew);
```

### <a name="parameters"></a>Parameter

*pViewNew*<br/>
Ein Zeiger auf eine zu aktivierende Ansicht.

### <a name="remarks"></a>Bemerkungen

## <a name="cframewndsetactiveview"></a><a name="setactiveview"></a>CFrameWnd::SetActiveView

Rufen Sie diese Memberfunktion auf, um die aktive Ansicht festzulegen.

```cpp
void SetActiveView(
    CView* pViewNew,
    BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parameter

*pViewNew*<br/>
Gibt einen Zeiger auf ein [CView-Objekt](../../mfc/reference/cview-class.md) oder NULL für keine aktive Ansicht an.

*bNotify*<br/>
Gibt an, ob die Ansicht über die Aktivierung benachrichtigt werden soll. Wenn TRUE, `OnActivateView` wird für die neue Ansicht aufgerufen; wenn FALSE, ist es nicht.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Funktion automatisch auf, wenn der Benutzer den Fokus in eine Ansicht innerhalb des Rahmenfensters ändert. Sie können `SetActiveView` explizit aufrufen, um den Fokus auf die angegebene Ansicht zu ändern.

## <a name="cframewndsetdockstate"></a><a name="setdockstate"></a>CFrameWnd::SetDockState

Rufen Sie diese Memberfunktion auf, `CDockState` um in einem Objekt gespeicherte Statusinformationen auf die Steuerelementleisten des Rahmenfensters anzuwenden.

```cpp
void SetDockState(const CDockState& state);
```

### <a name="parameters"></a>Parameter

*state*<br/>
Wenden Sie den gespeicherten Status auf die Kontrollleisten des Rahmenfensters an.

### <a name="remarks"></a>Bemerkungen

Um einen vorherigen Status der Steuerleisten wiederherzustellen, `CDockState::LoadState` können `Serialize`Sie `SetDockState` den gespeicherten Status mit oder laden, und verwenden Sie ihn dann, um ihn auf die Kontrollleisten des Rahmenfensters anzuwenden. Der vorherige Zustand wird `CDockState` im Objekt mit`GetDockState`

## <a name="cframewndsetmenubarstate"></a><a name="setmenubarstate"></a>CFrameWnd::SetMenuBarState

Legt den Anzeigestatus des Menüs in der aktuellen MFC-Anwendung auf ausgeblendet oder angezeigt fest.

```
virtual BOOL SetMenuBarState(DWORD nState);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*nState*|[in] Gibt an, ob das Menü angezeigt oder ausgeblendet werden soll. Der *nState-Parameter* kann die folgenden Werte haben:<br /><br />- AFX_MBS_VISIBLE (0x01) - Zeigt das Menü an, wenn es ausgeblendet ist, hat aber keine Wirkung, wenn es sichtbar ist.<br />- AFX_MBS_HIDDEN (0x02) - Blendet das Menü aus, wenn es sichtbar ist, hat aber keine Wirkung, wenn es ausgeblendet ist.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode den Menüstatus erfolgreich ändert. andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Wenn ein Laufzeitfehler auftritt, wird diese Methode im Debugmodus bestätigt und löst eine Ausnahme aus, die von der [CException-Klasse](../../mfc/reference/cexception-class.md) abgeleitet wurde.

## <a name="cframewndsetmenubarvisibility"></a><a name="setmenubarvisibility"></a>CFrameWnd::SetMenuBarVisibility

Legt fest, dass das Standardverhalten des Menüs in der aktuellen MFC-Anwendung entweder ausgeblendet oder sichtbar ist.

```
virtual void SetMenuBarVisibility(DWORD nStyle);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*nStyle*|[in] Gibt an, ob das Menü standardmäßig ausgeblendet ist oder sichtbar ist und den Fokus hat. Der *nStyle-Parameter* kann die folgenden Werte haben:<br /><br />- AFX_MBV_KEEPVISIBLE (0x01) -<br />     Das Menü wird jederzeit angezeigt und hat standardmäßig nicht den Fokus.<br />- AFX_MBV_DISPLAYONFOCUS (0x02) -<br />     Das Menü ist standardmäßig ausgeblendet. Wenn das Menü ausgeblendet ist, drücken Sie die ALT-Taste, um das Menü anzuzeigen und ihm den Fokus zu geben. Wenn das Menü angezeigt wird, drücken Sie die ALT- oder ESC-Taste, um das Menü auszublenden.<br />- AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04)<br />     (Bitweise Kombination (OR)) - Das Menü ist standardmäßig ausgeblendet. Wenn das Menü ausgeblendet ist, drücken Sie die F10-Taste, um das Menü anzuzeigen und ihm den Fokus zu geben. Wenn das Menü angezeigt wird, drücken Sie die F10-Taste, um den Fokus auf oder außerhalb des Menüs umzuschalten. Das Menü wird angezeigt, bis Sie die ALT- oder ESC-Taste drücken, um es auszublenden.|

### <a name="remarks"></a>Bemerkungen

Wenn der Wert des *nStyle-Parameters* ungültig ist, wird diese Methode im Debugmodus bestätigt und [CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md) im Release-Modus ausgelöst. Bei anderen Laufzeitfehlern wird diese Methode im Debugmodus bestätigt und löst eine Ausnahme aus, die von der [CException-Klasse](../../mfc/reference/cexception-class.md) abgeleitet wurde.

Diese Methode wirkt sich auf den Status von Menüs in Anwendungen aus, die für Windows Vista und höher geschrieben wurden.

## <a name="cframewndsetmessagetext"></a><a name="setmessagetext"></a>CFrameWnd::SetMessageText

Rufen Sie diese Funktion auf, um eine Zeichenfolge im Statusleistenbereich mit der ID 0 zu platzieren.

```cpp
void SetMessageText(LPCTSTR lpszText);
void SetMessageText(UINT nID);
```

### <a name="parameters"></a>Parameter

*lpszText*<br/>
Zeigt auf die Zeichenfolge, die auf der Statusleiste platziert werden soll.

*nID*<br/>
Zeichenfolgenressourcen-ID der Zeichenfolge, die auf der Statusleiste platziert werden soll.

### <a name="remarks"></a>Bemerkungen

Dies ist in der Regel der linke und längste Bereich der Statusleiste.

## <a name="cframewndsetprogressbarposition"></a><a name="setprogressbarposition"></a>CFrameWnd::SetProgressBarPosition

Legt die aktuelle Position für die Auf-Fortschrittsleiste von Windows 7 fest, die auf der Taskleiste angezeigt wird.

```cpp
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>Parameter

*nProgressPos*<br/>
Gibt die festzulegende Position an. Sie muss innerhalb des `SetProgressBarRange`von festgelegten Bereichs liegen.

### <a name="remarks"></a>Bemerkungen

## <a name="cframewndsetprogressbarrange"></a><a name="setprogressbarrange"></a>CFrameWnd::SetProgressBarRange

Legt den Bereich für die Auf-/ Azudeleiste von Windows 7 fest, die auf der Taskleiste angezeigt wird.

```cpp
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>Parameter

*nRangeMin*<br/>
Minimaler Wert.

*nRangeMax*<br/>
Maximalwert.

### <a name="remarks"></a>Bemerkungen

## <a name="cframewndsetprogressbarstate"></a><a name="setprogressbarstate"></a>CFrameWnd::SetProgressBarState

Legt den Typ und den Status der Fortschrittsanzeige fest, die auf einer Taskleistenschaltfläche angezeigt wird.

```cpp
void SetProgressBarState(TBPFLAG tbpFlags);
```

### <a name="parameters"></a>Parameter

*tbpFlags*<br/>
Flags, die den aktuellen Status der Fortschrittsschaltfläche steuern. Geben Sie nur eine der folgenden Flags an, da sich alle Zustände gegenseitig ausschließen: TBPF_NOPROGRESS, TBPF_INDETERMINATE, TBPF_NORMAL, TBPF_ERROR, TBPF_PAUSED.

### <a name="remarks"></a>Bemerkungen

## <a name="cframewndsettaskbaroverlayicon"></a><a name="settaskbaroverlayicon"></a>CFrameWnd::SetTaskbarOverlayIcon

Ist überladen. Wendet ein Overlay auf eine Taskleistenschaltfläche an, um den Anwendungsstatus anzugeben oder den Benutzer zu benachrichtigen.

```
BOOL SetTaskbarOverlayIcon(
    UINT nIDResource,
    LPCTSTR lpcszDescr);

BOOL SetTaskbarOverlayIcon(
    HICON hIcon,
    LPCTSTR lpcszDescr);
```

### <a name="parameters"></a>Parameter

*nIDResource*<br/>
Gibt die Ressourcen-ID eines Symbols an, das als Überlagerung verwendet werden soll. Weitere Informationen finden Sie in der Beschreibung *von hIcon.*

*lpcszDescr*<br/>
Ein Zeiger auf eine Zeichenfolge, die eine Alt-Textversion der durch das Overlay übermittelten Informationen bereitstellt, um den Zugriff zu gewährleisten.

*hIcon*<br/>
Das Handle eines Symbols, das als Überlagerung verwendet werden soll. Dies sollte ein kleines Symbol mit einer Größe von 16x16 Pixeln bei 96 Punkten pro Zoll (dpi) sein. Wenn bereits ein Überlagerungssymbol auf die Taskleistenschaltfläche angewendet wird, wird diese vorhandene Überlagerung ersetzt. Dieser Wert kann NULL sein. Wie ein NULL-Wert behandelt wird, hängt davon ab, ob die Taskleistenschaltfläche ein einzelnes Fenster oder eine Gruppe von Fenstern darstellt. Es liegt in der Verantwortung der aufrufenden Anwendung, *hIcon* freizugeben, wenn es nicht mehr benötigt wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich; FALSE, wenn die Betriebssystemversion kleiner als Windows 7 ist oder wenn beim Festlegen des Symbols ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

## <a name="cframewndsettitle"></a><a name="settitle"></a>CFrameWnd::SetTitle

Legt den Titel des Fensterobjekts fest.

```cpp
void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>Parameter

*lpszTitle*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Titel des Fensterobjekts enthält.

## <a name="cframewndshowcontrolbar"></a><a name="showcontrolbar"></a>CFrameWnd::ShowControlBar

Rufen Sie diese Memberfunktion auf, um die Steuerleiste ein- oder auszublenden.

```cpp
void ShowControlBar(
    CControlBar* pBar,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>Parameter

*Pbar*<br/>
Zeigen Sie mit dem Zeiger auf die Kontrollleiste, die angezeigt oder ausgeblendet werden soll.

*bShow*<br/>
Wenn TRUE, gibt an, dass die Steuerleiste angezeigt werden soll. Wenn FALSE, gibt an, dass die Steuerleiste ausgeblendet werden soll.

*bDelay*<br/>
Wenn TRUE, verzögern Sie die Anzeige der Steuerleiste. Wenn FALSE, zeigen Sie die Steuerleiste sofort an.

## <a name="cframewndshowownedwindows"></a><a name="showownedwindows"></a>CFrameWnd::ShowOwnedWindows

Rufen Sie diese Memberfunktion auf, um `CFrameWnd` alle Fenster anzuzeigen, die abhängig vom Objekt sind.

```cpp
void ShowOwnedWindows(BOOL bShow);
```

### <a name="parameters"></a>Parameter

*bShow*<br/>
Gibt an, ob die eigenen Fenster angezeigt oder ausgeblendet werden sollen.

## <a name="see-also"></a>Weitere Informationen

[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd-Klasse](../../mfc/reference/cmdiframewnd-class.md)<br/>
[CMDIChildWnd-Klasse](../../mfc/reference/cmdichildwnd-class.md)<br/>
[CView-Klasse](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate-Klasse](../../mfc/reference/cdoctemplate-class.md)<br/>
[CRuntimeClass-Struktur](../../mfc/reference/cruntimeclass-structure.md)
