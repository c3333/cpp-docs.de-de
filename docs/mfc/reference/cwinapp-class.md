---
title: CWinApp-Klasse
ms.date: 07/15/2019
f1_keywords:
- CWinApp
- AFXWIN/CWinApp
- AFXWIN/CWinApp::CWinApp
- AFXWIN/CWinApp::AddDocTemplate
- AFXWIN/CWinApp::AddToRecentFileList
- AFXWIN/CWinApp::ApplicationRecoveryCallback
- AFXWIN/CWinApp::CloseAllDocuments
- AFXWIN/CWinApp::CreatePrinterDC
- AFXWIN/CWinApp::DelRegTree
- AFXWIN/CWinApp::DoMessageBox
- AFXWIN/CWinApp::DoWaitCursor
- AFXWIN/CWinApp::EnableD2DSupport
- AFXWIN/CWinApp::EnableHtmlHelp
- AFXWIN/CWinApp::EnableTaskbarInteraction
- AFXWIN/CWinApp::ExitInstance
- AFXWIN/CWinApp::GetApplicationRecoveryParameter
- AFXWIN/CWinApp::GetApplicationRecoveryPingInterval
- AFXWIN/CWinApp::GetApplicationRestartFlags
- AFXWIN/CWinApp::GetAppRegistryKey
- AFXWIN/CWinApp::GetDataRecoveryHandler
- AFXWIN/CWinApp::GetFirstDocTemplatePosition
- AFXWIN/CWinApp::GetHelpMode
- AFXWIN/CWinApp::GetNextDocTemplate
- AFXWIN/CWinApp::GetPrinterDeviceDefaults
- AFXWIN/CWinApp::GetProfileBinary
- AFXWIN/CWinApp::GetProfileInt
- AFXWIN/CWinApp::GetProfileString
- AFXWIN/CWinApp::GetSectionKey
- AFXWIN/CWinApp::HideApplication
- AFXWIN/CWinApp::HtmlHelp
- AFXWIN/CWinApp::InitInstance
- AFXWIN/CWinApp::IsTaskbarInteractionEnabled
- AFXWIN/CWinApp::LoadCursor
- AFXWIN/CWinApp::LoadIcon
- AFXWIN/CWinApp::LoadOEMCursor
- AFXWIN/CWinApp::LoadOEMIcon
- AFXWIN/CWinApp::LoadStandardCursor
- AFXWIN/CWinApp::LoadStandardIcon
- AFXWIN/CWinApp::OnDDECommand
- AFXWIN/CWinApp::OnIdle
- AFXWIN/CWinApp::OpenDocumentFile
- AFXWIN/CWinApp::ParseCommandLine
- AFXWIN/CWinApp::PreTranslateMessage
- AFXWIN/CWinApp::ProcessMessageFilter
- AFXWIN/CWinApp::ProcessShellCommand
- AFXWIN/CWinApp::ProcessWndProcException
- AFXWIN/CWinApp::Register
- AFXWIN/CWinApp::RegisterWithRestartManager
- AFXWIN/CWinApp::ReopenPreviousFilesAtRestart
- AFXWIN/CWinApp::RestartInstance
- AFXWIN/CWinApp::RestoreAutosavedFilesAtRestart
- AFXWIN/CWinApp::Run
- AFXWIN/CWinApp::RunAutomated
- AFXWIN/CWinApp::RunEmbedded
- AFXWIN/CWinApp::SaveAllModified
- AFXWIN/CWinApp::SelectPrinter
- AFXWIN/CWinApp::SetHelpMode
- AFXWIN/CWinApp::SupportsApplicationRecovery
- AFXWIN/CWinApp::SupportsAutosaveAtInterval
- AFXWIN/CWinApp::SupportsAutosaveAtRestart
- AFXWIN/CWinApp::SupportsRestartManager
- AFXWIN/CWinApp::Unregister
- AFXWIN/CWinApp::WinHelp
- AFXWIN/CWinApp::WriteProfileBinary
- AFXWIN/CWinApp::WriteProfileInt
- AFXWIN/CWinApp::WriteProfileString
- AFXWIN/CWinApp::EnableShellOpen
- AFXWIN/CWinApp::LoadStdProfileSettings
- AFXWIN/CWinApp::OnContextHelp
- AFXWIN/CWinApp::OnFileNew
- AFXWIN/CWinApp::OnFileOpen
- AFXWIN/CWinApp::OnFilePrintSetup
- AFXWIN/CWinApp::OnHelp
- AFXWIN/CWinApp::OnHelpFinder
- AFXWIN/CWinApp::OnHelpIndex
- AFXWIN/CWinApp::OnHelpUsing
- AFXWIN/CWinApp::RegisterShellFileTypes
- AFXWIN/CWinApp::SetAppID
- AFXWIN/CWinApp::SetRegistryKey
- AFXWIN/CWinApp::UnregisterShellFileTypes
- AFXWIN/CWinApp::m_bHelpMode
- AFXWIN/CWinApp::m_eHelpType
- AFXWIN/CWinApp::m_hInstance
- AFXWIN/CWinApp::m_lpCmdLine
- AFXWIN/CWinApp::m_nCmdShow
- AFXWIN/CWinApp::m_pActiveWnd
- AFXWIN/CWinApp::m_pszAppID
- AFXWIN/CWinApp::m_pszAppName
- AFXWIN/CWinApp::m_pszExeName
- AFXWIN/CWinApp::m_pszHelpFilePath
- AFXWIN/CWinApp::m_pszProfileName
- AFXWIN/CWinApp::m_pszRegistryKey
- AFXWIN/CWinApp::m_dwRestartManagerSupportFlags
- AFXWIN/CWinApp::m_nAutosaveInterval
- AFXWIN/CWinApp::m_pDataRecoveryHandler
helpviewer_keywords:
- CWinApp [MFC], CWinApp
- CWinApp [MFC], AddDocTemplate
- CWinApp [MFC], AddToRecentFileList
- CWinApp [MFC], ApplicationRecoveryCallback
- CWinApp [MFC], CloseAllDocuments
- CWinApp [MFC], CreatePrinterDC
- CWinApp [MFC], DelRegTree
- CWinApp [MFC], DoMessageBox
- CWinApp [MFC], DoWaitCursor
- CWinApp [MFC], EnableD2DSupport
- CWinApp [MFC], EnableHtmlHelp
- CWinApp [MFC], EnableTaskbarInteraction
- CWinApp [MFC], ExitInstance
- CWinApp [MFC], GetApplicationRecoveryParameter
- CWinApp [MFC], GetApplicationRecoveryPingInterval
- CWinApp [MFC], GetApplicationRestartFlags
- CWinApp [MFC], GetAppRegistryKey
- CWinApp [MFC], GetDataRecoveryHandler
- CWinApp [MFC], GetFirstDocTemplatePosition
- CWinApp [MFC], GetHelpMode
- CWinApp [MFC], GetNextDocTemplate
- CWinApp [MFC], GetPrinterDeviceDefaults
- CWinApp [MFC], GetProfileBinary
- CWinApp [MFC], GetProfileInt
- CWinApp [MFC], GetProfileString
- CWinApp [MFC], GetSectionKey
- CWinApp [MFC], HideApplication
- CWinApp [MFC], HtmlHelp
- CWinApp [MFC], InitInstance
- CWinApp [MFC], IsTaskbarInteractionEnabled
- CWinApp [MFC], LoadCursor
- CWinApp [MFC], LoadIcon
- CWinApp [MFC], LoadOEMCursor
- CWinApp [MFC], LoadOEMIcon
- CWinApp [MFC], LoadStandardCursor
- CWinApp [MFC], LoadStandardIcon
- CWinApp [MFC], OnDDECommand
- CWinApp [MFC], OnIdle
- CWinApp [MFC], OpenDocumentFile
- CWinApp [MFC], ParseCommandLine
- CWinApp [MFC], PreTranslateMessage
- CWinApp [MFC], ProcessMessageFilter
- CWinApp [MFC], ProcessShellCommand
- CWinApp [MFC], ProcessWndProcException
- CWinApp [MFC], Register
- CWinApp [MFC], RegisterWithRestartManager
- CWinApp [MFC], ReopenPreviousFilesAtRestart
- CWinApp [MFC], RestartInstance
- CWinApp [MFC], RestoreAutosavedFilesAtRestart
- CWinApp [MFC], Run
- CWinApp [MFC], RunAutomated
- CWinApp [MFC], RunEmbedded
- CWinApp [MFC], SaveAllModified
- CWinApp [MFC], SelectPrinter
- CWinApp [MFC], SetHelpMode
- CWinApp [MFC], SupportsApplicationRecovery
- CWinApp [MFC], SupportsAutosaveAtInterval
- CWinApp [MFC], SupportsAutosaveAtRestart
- CWinApp [MFC], SupportsRestartManager
- CWinApp [MFC], Unregister
- CWinApp [MFC], WinHelp
- CWinApp [MFC], WriteProfileBinary
- CWinApp [MFC], WriteProfileInt
- CWinApp [MFC], WriteProfileString
- CWinApp [MFC], EnableShellOpen
- CWinApp [MFC], LoadStdProfileSettings
- CWinApp [MFC], OnContextHelp
- CWinApp [MFC], OnFileNew
- CWinApp [MFC], OnFileOpen
- CWinApp [MFC], OnFilePrintSetup
- CWinApp [MFC], OnHelp
- CWinApp [MFC], OnHelpFinder
- CWinApp [MFC], OnHelpIndex
- CWinApp [MFC], OnHelpUsing
- CWinApp [MFC], RegisterShellFileTypes
- CWinApp [MFC], SetAppID
- CWinApp [MFC], SetRegistryKey
- CWinApp [MFC], UnregisterShellFileTypes
- CWinApp [MFC], m_bHelpMode
- CWinApp [MFC], m_eHelpType
- CWinApp [MFC], m_hInstance
- CWinApp [MFC], m_lpCmdLine
- CWinApp [MFC], m_nCmdShow
- CWinApp [MFC], m_pActiveWnd
- CWinApp [MFC], m_pszAppID
- CWinApp [MFC], m_pszAppName
- CWinApp [MFC], m_pszExeName
- CWinApp [MFC], m_pszHelpFilePath
- CWinApp [MFC], m_pszProfileName
- CWinApp [MFC], m_pszRegistryKey
- CWinApp [MFC], m_dwRestartManagerSupportFlags
- CWinApp [MFC], m_nAutosaveInterval
- CWinApp [MFC], m_pDataRecoveryHandler
ms.assetid: e426a3cd-0d15-40d6-bd55-beaa5feb2343
ms.openlocfilehash: e65ad8b5d8b14ff747adc55b517d9e695d9cbb66
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426408"
---
# <a name="cwinapp-class"></a>CWinApp-Klasse

Die Basisklasse, von der ein Windows-Anwendungsobjekt abgeleitet wird.

## <a name="syntax"></a>Syntax

```
class CWinApp : public CWinThread
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CWinApp:: CWinApp](#cwinapp)|Erstellt ein `CWinApp`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CWinApp:: AddDocTemplate](#adddoctemplate)|Fügt der Liste der verfügbaren Dokumentvorlagen der Anwendung eine Dokument Vorlage hinzu.|
|[CWinApp:: addtor ecentfilelist](#addtorecentfilelist)|Fügt der zuletzt verwendeten Datei Liste (MRU) einen Dateinamen hinzu.|
|[CWinApp:: applicationwiederherstellungsrückruf](#applicationrecoverycallback)|Wird von Framework aufgerufen, wenn die Anwendung unerwartet beendet wird.|
|[CWinApp:: closealldocuments](#closealldocuments)|Schließt alle geöffneten Dokumente.|
|[CWinApp:: kreateprinterdc](#createprinterdc)|Erstellt einen Drucker Gerätekontext.|
|[CWinApp::D elregtree](#delregtree)|Löscht einen angegebenen Schlüssel und alle zugehörigen Unterschlüssel.|
|[CWinApp::D omessagebox](#domessagebox)|Implementiert [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) für die Anwendung.|
|[CWinApp::D owaitcursor](#dowaitcursor)|Schaltet den warte Cursor ein und aus.|
|[CWinApp:: EnableD2DSupport](#enabled2dsupport)|Aktiviert die Unterstützung von Anwendungs D2D. Rufen Sie diese Methode vor der Initialisierung des Hauptfensters auf.|
|[CWinApp:: enablehtmlhelp](#enablehtmlhelp)|Implementiert HTMLHelp für die Anwendung anstelle von WinHelp.|
|[CWinApp:: enabletaskbarinteraktion](#enabletaskbarinteraction)|Aktiviert die Interaktion in der Taskleiste.|
|[CWinApp:: ExitInstance](#exitinstance)|Außer Kraft Setzung zum Bereinigen, wenn die Anwendung beendet wird.|
|[CWinApp:: getapplicationwiederherstellungsparameter](#getapplicationrecoveryparameter)|Ruft den Eingabeparameter für die Wiederherstellungsmethode der Anwendung ab.|
|[CWinApp:: getapplicationherstellypinginterval](#getapplicationrecoverypinginterval)|Gibt die Zeitspanne zurück, die der Neustart-Manager wartet, bis die Wiederherstellungs Rückruffunktion zurückgegeben wird.|
|[CWinApp:: getapplicationrestartflags](#getapplicationrestartflags)|Gibt die Flags für den Neustart-Manager zurück.|
|[CWinApp:: getappregistrykey](#getappregistrykey)|Gibt den Schlüssel für HKEY_CURRENT_USER\\"Software" \registrykey\profile amezurück.|
|[CWinApp:: getdatarecoveryhandler](#getdatarecoveryhandler)|Ruft den Datenwiederherstellungs-Handler für diese Instanz der Anwendung ab.|
|[CWinApp:: GetFirstDocTemplatePosition](#getfirstdoctemplateposition)|Ruft die Position der ersten Dokument Vorlage ab.|
|[CWinApp:: gethelpmode](#gethelpmode)|Ruft den Typ der von der Anwendung verwendeten Hilfe ab.|
|[CWinApp:: GetNextDocTemplate](#getnextdoctemplate)|Ruft die Position einer Dokument Vorlage ab. Kann rekursiv verwendet werden.|
|[CWinApp:: getprinterdevicedefaults](#getprinterdevicedefaults)|Ruft die Standardeinstellungen des Drucker Geräts ab.|
|[CWinApp:: getprofilebinary](#getprofilebinary)|Ruft Binärdaten von einem Eintrag in der der Anwendung ab. INI-Datei.|
|[CWinApp:: GetProfileInt](#getprofileint)|Ruft eine ganze Zahl aus einem Eintrag in der der Anwendung ab. INI-Datei.|
|[CWinApp:: GetProfileString](#getprofilestring)|Ruft eine Zeichenfolge aus einem Eintrag in der der Anwendung ab. INI-Datei.|
|[CWinApp:: getsectionkey](#getsectionkey)|Gibt den Schlüssel für HKEY_CURRENT_USER\\"Software" \registrykey\appname\lpszsectionzurück.|
|[CWinApp:: hideapplication](#hideapplication)|Blendet die Anwendung aus, bevor alle Dokumente geschlossen werden.|
|[CWinApp:: HTMLHelp](#htmlhelp)|Ruft die `HTMLHelp` Windows-Funktion auf.|
|[CWinApp:: InitInstance](#initinstance)|Überschreiben, um die Initialisierung der Windows-Instanz auszuführen, z. b. das Erstellen von Fenster Objekten|
|[CWinApp:: istaskbarinteraktionaktiviert](#istaskbarinteractionenabled)|Gibt an, ob die Interaktion der Windows 7-Taskleiste aktiviert ist.|
|[CWinApp:: LoadCursor](#loadcursor)|Lädt eine Cursor Ressource.|
|[CWinApp:: LoadIcon](#loadicon)|Lädt eine Symbol Ressource.|
|[CWinApp:: loadoemcursor](#loadoemcursor)|Lädt einen vordefinierten Windows-OEM-Cursor, den die **OCR_** Konstanten in Windows angeben. Micha.|
|[CWinApp:: loadoemicon](#loadoemicon)|Lädt ein von Windows OEM vordefiniertes Symbol, das von den **OIC_** Konstanten in Windows angegeben wird. Micha.|
|[CWinApp:: loadstandardcursor](#loadstandardcursor)|Lädt einen vordefinierten Windows-Cursor, den die **IDC_** Konstanten in Windows angeben. Micha.|
|[CWinApp:: loadstandardische](#loadstandardicon)|Lädt ein vordefiniertes Windows-Symbol, das von den **IDI_** Konstanten in Windows angegeben wird. Micha.|
|[CWinApp:: onddecommand](#onddecommand)|Wird von Framework als Antwort auf einen Execute-Befehl (Dynamic Data Exchange) aufgerufen.|
|[CWinApp:: OnIdle](#onidle)|Überschreiben Sie, um eine anwendungsspezifische Leerlaufzeit Verarbeitung auszuführen.|
|[CWinApp:: OpenDocumentFile](#opendocumentfile)|Wird von Framework aufgerufen, um ein Dokument aus einer Datei zu öffnen.|
|[CWinApp::P arccommandline](#parsecommandline)|Analysiert einzelne Parameter und Flags in der Befehlszeile.|
|[CWinApp::P retranslatemess Age](#pretranslatemessage)|Filtert Nachrichten, bevor diese an die Windows-Funktionen [translatemess](/windows/win32/api/winuser/nf-winuser-translatemessage) und [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)gesendet werden.|
|[CWinApp::P rocess MessageFilter](#processmessagefilter)|Fängt bestimmte Nachrichten ab, bevor Sie die Anwendung erreichen.|
|[CWinApp::P rocess shellcommand](#processshellcommand)|Verarbeitet Befehlszeilenargumente und-Flags.|
|[CWinApp::P rocess wndprocexception](#processwndprocexception)|Fängt alle nicht behandelten Ausnahmen ab, die von der Meldungs-und Befehls Handlers der Anwendung ausgelöst werden.|
|[CWinApp:: Register](#register)|Führt eine angepasste Registrierung aus.|
|[CWinApp:: registerwithrestartmanager](#registerwithrestartmanager)|Registriert die Anwendung beim Neustart-Manager.|
|[CWinApp:: reopenpreviousfilesatrestart](#reopenpreviousfilesatrestart)|Bestimmt, ob der Neustart-Manager die Dateien erneut öffnet, die geöffnet waren, als die Anwendung unerwartet beendet wurde.|
|[CWinApp:: restartinstance](#restartinstance)|Behandelt einen Neustart der Anwendung, der vom Neustart-Manager initiiert wird.|
|[CWinApp:: restoreautosavedfilesatrestart](#restoreautosavedfilesatrestart)|Bestimmt, ob der Neustart-Manager die automatisch gespeicherten Dateien wiederherstellt, wenn die Anwendung neu gestartet wird.|
|[CWinApp:: Run](#run)|Führt die Standard Nachrichten Schleife aus. Überschreiben, um die Nachrichten Schleife anzupassen.|
|[CWinApp:: runautomated](#runautomated)|Testet die Befehlszeile der Anwendung auf die Option **/Automation** . Veraltet. Verwenden Sie stattdessen den Wert in [ccommandlineinfo:: m_bRunAutomated](../../mfc/reference/ccommandlineinfo-class.md#m_brunautomated) nach dem Aufruf von " [parametercommandline](#parsecommandline)".|
|[CWinApp:: RunEmbedded](#runembedded)|Testet die Befehlszeile der Anwendung auf die Option **/Embedding** . Veraltet. Verwenden Sie stattdessen den Wert in [ccommandlineinfo:: m_bRunEmbedded](../../mfc/reference/ccommandlineinfo-class.md#m_brunembedded) nach dem Aufruf von " [parametercommandline](#parsecommandline)".|
|[CWinApp:: saveallmodified](#saveallmodified)|Fordert den Benutzer auf, alle geänderten Dokumente zu speichern.|
|[CWinApp:: selectprinter](#selectprinter)|Wählt einen Drucker aus, der zuvor durch einen Benutzer über das Dialogfeld "Drucken" angegeben wurde.|
|[CWinApp:: Setup Mode](#sethelpmode)|Legt die Art der von der Anwendung verwendeten Hilfe fest und initialisiert sie.|
|[CWinApp:: supportsapplicationrecovery](#supportsapplicationrecovery)|Bestimmt, ob der Neustart-Manager eine Anwendung wiederherstellt, die unerwartet beendet wurde.|
|[CWinApp:: supportsauessaveatinterval](#supportsautosaveatinterval)|Bestimmt, ob der Neustart-Manager geöffnete Dokumente in regelmäßigen Abständen automatisch speichert.|
|[CWinApp:: supportsaudesaveatrestart](#supportsautosaveatrestart)|Bestimmt, ob der Neustart-Manager alle geöffneten Dokumente automatisch speichert, wenn die Anwendung neu gestartet wird.|
|[CWinApp:: supportsrestartmanager](#supportsrestartmanager)|Bestimmt, ob die Anwendung den Neustart-Manager unterstützt.|
|[CWinApp:: Unregister](#unregister)|Hebt die Registrierung aller bekannten Elemente auf, die vom `CWinApp`-Objekt registriert werden.|
|[CWinApp:: WinHelp](#winhelp)|Ruft die `WinHelp` Windows-Funktion auf.|
|[CWinApp:: Beschreib teprofilebinary](#writeprofilebinary)|Schreibt Binärdaten in einen Eintrag in der der Anwendung. INI-Datei.|
|[CWinApp:: Beschreib teprofileint](#writeprofileint)|Schreibt eine Ganzzahl in einen Eintrag in der der Anwendung. INI-Datei.|
|[CWinApp:: Schreib Profil Zeichenfolge](#writeprofilestring)|Schreibt eine Zeichenfolge in einen Eintrag in der der Anwendung. INI-Datei.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CWinApp:: EnableShellOpen](#enableshellopen)|Ermöglicht dem Benutzer das Öffnen von Datendateien aus dem Windows-Datei-Manager.|
|[CWinApp:: LoadStdProfileSettings](#loadstdprofilesettings)|Lädt den Standard. INI-Datei Einstellungen und aktiviert das MRU-Dateilisten Feature.|
|[CWinApp:: oncontexthelp](#oncontexthelp)|Verarbeitet die UMSCHALT + F1-Hilfe in der Anwendung.|
|[CWinApp:: OnFile-Datei](#onfilenew)|Implementiert den ID_FILE_NEW-Befehl.|
|[CWinApp:: OnFileOpen](#onfileopen)|Implementiert den ID_FILE_OPEN-Befehl.|
|[CWinApp:: onfileprintsetup](#onfileprintsetup)|Implementiert den ID_FILE_PRINT_SETUP-Befehl.|
|[CWinApp:: onhelp](#onhelp)|Verarbeitet die F1-Hilfe in der Anwendung (unter Verwendung des aktuellen Kontexts).|
|[CWinApp:: onhelpfinder](#onhelpfinder)|Behandelt die Befehle ID_HELP_FINDER und ID_DEFAULT_HELP.|
|[CWinApp:: onhelpindex](#onhelpindex)|Behandelt den ID_HELP_INDEX Befehl und stellt ein Standard Hilfethema bereit.|
|[CWinApp:: onhelpusing](#onhelpusing)|Behandelt den ID_HELP_USING Befehl.|
|[CWinApp:: RegisterShellFileTypes](#registershellfiletypes)|Registriert alle Dokumenttypen der Anwendung beim Windows-Datei-Manager.|
|[CWinApp:: "abtappid"](#setappid)|Legt die Anwendungs Benutzer Modell-ID für die Anwendung explizit fest. Diese Methode sollte aufgerufen werden, bevor Benutzern eine Benutzeroberfläche angezeigt wird (die beste Stelle ist der Anwendungskonstruktor).|
|[CWinApp:: abtregistrykey](#setregistrykey)|Bewirkt, dass Anwendungseinstellungen in der Registrierung anstelle von gespeichert werden. INI-Dateien.|
|[CWinApp:: unregistershellfiletypes](#unregistershellfiletypes)|Hebt die Registrierung aller Dokumenttypen der Anwendung beim Windows-Datei-Manager auf.|

### <a name="public-data-members"></a>Öffentliche Datenelemente

|Name|Beschreibung|
|----------|-----------------|
|[CWinApp:: m_bHelpMode](#m_bhelpmode)|Gibt an, ob sich der Benutzer im Hilfe Kontext Modus befindet (wird in der Regel mit UMSCHALT + F1 aufgerufen).|
|[CWinApp:: m_eHelpType](#m_ehelptype)|Gibt die Art der Hilfe an, die von der Anwendung verwendet wird.|
|[CWinApp:: m_hInstance](#m_hinstance)|Identifiziert die aktuelle Instanz der Anwendung.|
|[CWinApp:: m_lpCmdLine](#m_lpcmdline)|Verweist auf eine mit NULL endenden Zeichenfolge, die die Befehlszeile für die Anwendung angibt.|
|[CWinApp:: m_nCmdShow](#m_ncmdshow)|Gibt an, wie das Fenster anfänglich angezeigt werden soll.|
|[CWinApp:: m_pActiveWnd](#m_pactivewnd)|Zeiger auf das Hauptfenster der Containeranwendung, wenn ein OLE-Server direkt aktiv ist.|
|[CWinApp:: m_pszAppID](#m_pszappid)|ID des Anwendungs Benutzer Modells.|
|[CWinApp:: m_pszAppName](#m_pszappname)|Gibt den Namen der Anwendung an.|
|[CWinApp:: m_pszExeName](#m_pszexename)|Der Modulname der Anwendung.|
|[CWinApp:: m_pszHelpFilePath](#m_pszhelpfilepath)|Der Pfad zur Hilfedatei der Anwendung.|
|[CWinApp:: m_pszProfileName](#m_pszprofilename)|Der der Anwendung. INI-Dateiname|
|[CWinApp:: m_pszRegistryKey](#m_pszregistrykey)|Wird verwendet, um den vollständigen Registrierungsschlüssel zum Speichern von Anwendungsprofil Einstellungen zu bestimmen.|

### <a name="protected-data-members"></a>Geschützte Datenelemente

|Name|Beschreibung|
|----------|-----------------|
|[CWinApp:: m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags)|Flags, die bestimmen, wie sich der Neustart-Manager verhält.|
|[CWinApp:: m_nAutosaveInterval](#m_nautosaveinterval)|Die Zeitspanne (in Millisekunden) zwischen den AutoSpeichern.|
|[CWinApp:: m_pDataRecoveryHandler](#m_pdatarecoveryhandler)|Zeiger auf den Datenwiederherstellungs-Handler für die Anwendung.|

## <a name="remarks"></a>Hinweise

Ein Anwendungs Objekt stellt Element Funktionen zum Initialisieren Ihrer Anwendung (und jeder Instanz davon) und zum Ausführen der Anwendung bereit.

Jede Anwendung, die die Microsoft Foundation Classes verwendet, kann nur ein von `CWinApp`abgeleitetes Objekt enthalten. Dieses Objekt wird erstellt, wenn C++ andere globale Objekte erstellt werden, und ist bereits verfügbar, wenn Windows die `WinMain`-Funktion aufruft, die vom Microsoft Foundation Class-Bibliothek bereitgestellt wird. Deklarieren Sie das abgeleitete `CWinApp` Objekt auf globaler Ebene.

Wenn Sie eine Anwendungsklasse von `CWinApp`ableiten, überschreiben Sie die [InitInstance](#initinstance) -Member-Funktion, um das Hauptfenster Objekt der Anwendung zu erstellen.

Zusätzlich zu den `CWinApp` Member-Funktionen stellt die Microsoft Foundation Class-Bibliothek die folgenden globalen Funktionen für den Zugriff auf Ihr `CWinApp` Objekt und andere globale Informationen bereit:

- [AfxGetApp](application-information-and-management.md#afxgetapp) Erhält einen Zeiger auf das `CWinApp`-Objekt.

- [AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle) Ruft ein Handle für die aktuelle Anwendungs Instanz ab.

- [AfxGetResourceHandle](application-information-and-management.md#afxgetresourcehandle) Ruft ein Handle für die Ressourcen der Anwendung ab.

- [Afxgetappname](application-information-and-management.md#afxgetappname) Ruft einen Zeiger auf eine Zeichenfolge ab, die den Namen der Anwendung enthält. Wenn Sie einen Zeiger auf das `CWinApp` Objekt haben, können Sie alternativ `m_pszExeName` verwenden, um den Namen der Anwendung zu erhalten.

Weitere Informationen zur `CWinApp`-Klasse finden Sie unter [CWinApp: die Anwendungsklasse](../../mfc/cwinapp-the-application-class.md) , einschließlich einer Übersicht über Folgendes:

- `CWinApp`von abgeleiteter Code, der vom Anwendungs-Assistenten geschrieben wurde.

- die Rolle `CWinApp`in der Ausführungsreihenfolge Ihrer Anwendung.

- die standardmäßigen Member-Funktions Implementierungen von `CWinApp`.

- der Schlüssel des `CWinApp`ist überschrieben.

Das `m_hPrevInstance` Datenmember ist nicht mehr vorhanden. Verwenden Sie einen benannten Mutex, um zu bestimmen, ob eine andere Instanz der Anwendung ausgeführt wird. Wenn das Öffnen des Mutex fehlschlägt, werden keine anderen Instanzen der Anwendung ausgeführt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWinThread](../../mfc/reference/cwinthread-class.md)

`CWinApp`

## <a name="requirements"></a>Voraussetzungen

**Header:** afxwin.h

##  <a name="adddoctemplate"></a>CWinApp:: AddDocTemplate

Diese Member-Funktion wird aufgerufen, um der Liste der verfügbaren Dokumentvorlagen, die von der Anwendung verwaltet werden, eine Dokument Vorlage hinzuzufügen.

```
void AddDocTemplate(CDocTemplate* pTemplate);
```

### <a name="parameters"></a>Parameter

*pTemplate*<br/>
Ein Zeiger auf das hinzu zufügende `CDocTemplate`.

### <a name="remarks"></a>Hinweise

Bevor Sie [RegisterShellFileTypes](#registershellfiletypes)aufrufen, sollten Sie alle Dokumentvorlagen zu einer Anwendung hinzufügen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#35](../../mfc/reference/codesnippet/cpp/cwinapp-class_1.cpp)]

##  <a name="addtorecentfilelist"></a>CWinApp:: addtor ecentfilelist

Diese Member-Funktion wird aufgerufen, um der MRU-Datei Liste *lpszpathname* hinzuzufügen.

```
virtual void AddToRecentFileList(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parameter

*lpszpathname*<br/>
Der Pfad der Datei.

### <a name="remarks"></a>Hinweise

Sie sollten die [LoadStdProfileSettings](#loadstdprofilesettings) -Member-Funktion zum Laden der aktuellen MRU-Datei Liste verwenden, bevor Sie diese Member-Funktion verwenden.

Das Framework ruft diese Member-Funktion auf, wenn eine Datei geöffnet wird, oder führt den Befehl Speichern unter aus, um eine Datei mit einem neuen Namen zu speichern.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#36](../../mfc/reference/codesnippet/cpp/cwinapp-class_2.cpp)]

##  <a name="applicationrecoverycallback"></a>CWinApp:: applicationwiederherstellungsrückruf

Wird von Framework aufgerufen, wenn die Anwendung unerwartet beendet wird.

```
virtual DWORD ApplicationRecoveryCallback(LPVOID lpvParam);
```

### <a name="parameters"></a>Parameter

*lpvparam*<br/>
[in] Reserviert für zukünftige Verwendung.

### <a name="return-value"></a>Rückgabewert

0, wenn diese Methode erfolgreich ist. ungleich 0 (null), wenn ein Fehler auftritt.

### <a name="remarks"></a>Hinweise

Wenn Ihre Anwendung den Neustart-Manager unterstützt, ruft das Framework diese Funktion auf, wenn Ihre Anwendung unerwartet beendet wird.

Die Standard Implementierung von `ApplicationRecoveryCallback` verwendet die `CDataRecoveryHandler`, um die Liste der aktuell geöffneten Dokumente in der Registrierung zu speichern. Bei dieser Methode werden Dateien nicht automatisch gespeichert.

Überschreiben Sie diese Funktion in einer abgeleiteten [CWinApp-Klasse](../../mfc/reference/cwinapp-class.md) , oder übergeben Sie Ihre eigene Anwendungs Wiederherstellungsmethode als Parameter an [CWinApp:: registerwithrestartmanager](#registerwithrestartmanager), um das Verhalten anzupassen.

##  <a name="closealldocuments"></a>CWinApp:: closealldocuments

Diese Member-Funktion wird aufgerufen, um alle geöffneten Dokumente vor dem Beenden zu schließen.

```
void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>Parameter

*bendsitzung*<br/>
Gibt an, ob die Windows-Sitzung beendet wird. Dies ist true, wenn die Sitzung beendet wird. andernfalls false.

### <a name="remarks"></a>Hinweise

Rufen Sie [hideapplication](#hideapplication) auf, bevor Sie `CloseAllDocuments`aufrufen.

##  <a name="createprinterdc"></a>CWinApp:: kreateprinterdc

Rufen Sie diese Member-Funktion auf, um einen Drucker Gerätekontext (DC) aus dem ausgewählten Drucker zu erstellen.

```
BOOL CreatePrinterDC(CDC& dc);
```

### <a name="parameters"></a>Parameter

*dc*<br/>
Ein Verweis auf einen Drucker Gerätekontext.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Drucker Gerätekontext erfolgreich erstellt wurde. andernfalls 0.

### <a name="remarks"></a>Hinweise

`CreatePrinterDC` initialisiert den Gerätekontext, den Sie als Verweis übergeben, sodass Sie ihn zum Drucken verwenden können.

Wenn die Funktion erfolgreich ausgeführt wurde, müssen Sie den Gerätekontext zerstören, wenn der Druckvorgang abgeschlossen ist. Sie können den Dekonstruktor des [CDC](../../mfc/reference/cdc-class.md) -Objekts durchführen lassen, oder Sie können dies explizit durch Aufrufen von [CDC::D eletedc](../../mfc/reference/cdc-class.md#deletedc)tun.

##  <a name="cwinapp"></a>CWinApp:: CWinApp

Erstellt ein `CWinApp` Objekt und übergibt *lpszappname* , der als Anwendungsname gespeichert werden soll.

```
CWinApp(LPCTSTR lpszAppName = NULL);
```

### <a name="parameters"></a>Parameter

*lpszappname*<br/>
Eine auf NULL endenden Zeichenfolge, die den von Windows verwendeten Anwendungsnamen enthält. Wenn dieses Argument nicht angegeben wird oder den Wert NULL hat, verwendet `CWinApp` die Ressourcen Zeichenfolge AFX_IDS_APP_TITLE oder den Dateinamen der ausführbaren Datei.

### <a name="remarks"></a>Hinweise

Sie sollten ein globales Objekt ihrer `CWinApp`-abgeleiteten Klasse erstellen. In Ihrer Anwendung kann nur ein `CWinApp` Objekt vorhanden sein. Der-Konstruktor speichert einen Zeiger auf das `CWinApp` Objekt, sodass `WinMain` die Element Funktionen des-Objekts zum Initialisieren und Ausführen der Anwendung abrufen kann.

##  <a name="delregtree"></a>CWinApp::D elregtree

Löscht einen bestimmten Registrierungsschlüssel und dessen Unterschlüssel.

```
LONG DelRegTree(
    HKEY hParentKey,
    const CString& strKeyName);

LONG DelRegTree(
    HKEY hParentKey,
    const CString& strKeyName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parameter

*hparser Key*<br/>
Handle für einen Registrierungsschlüssel.

*"Strauch Name"*<br/>
Der Name des zu löschenden Registrierungsschlüssels.

*pTM*<br/>
Zeiger auf das Objekt "-Objekt".

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, wird der Rückgabewert ERROR_SUCCESS. Wenn die Funktion fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich 0 (null), der in WinError. h definiert ist.

### <a name="remarks"></a>Hinweise

Mit dieser Funktion können Sie den angegebenen Schlüssel und dessen Unterschlüssel löschen.

##  <a name="domessagebox"></a>CWinApp::D omessagebox

Das Framework ruft diese Member-Funktion auf, um ein Meldungs Feld für die globale Funktion [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)zu implementieren.

```
virtual int DoMessageBox(
    LPCTSTR lpszPrompt,
    UINT nType,
    UINT nIDPrompt);
```

### <a name="parameters"></a>Parameter

*lpszprompt*<br/>
Die Adresse von Text im Meldungs Feld.

*nType*<br/>
Der [Stil](../../mfc/reference/styles-used-by-mfc.md#message-box-styles)des Meldungs Felds.

*nidprompt*<br/>
Ein Index für eine Hilfe Kontext Zeichenfolge.

### <a name="return-value"></a>Rückgabewert

Gibt die gleichen Werte wie `AfxMessageBox`zurück.

### <a name="remarks"></a>Hinweise

Verwenden Sie diese Member-Funktion nicht, um ein Meldungs Feld zu öffnen. Verwenden Sie stattdessen `AfxMessageBox`.

Überschreiben Sie diese Member-Funktion, um die Anwendungs weite Verarbeitung von `AfxMessageBox` aufrufen anzupassen.

##  <a name="dowaitcursor"></a>CWinApp::D owaitcursor

Diese Member-Funktion wird vom Framework aufgerufen, um [cwaitcursor](../../mfc/reference/cwaitcursor-class.md), [CCmdTarget:: beginwaitcursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget:: endwaitcursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)und [CCmdTarget:: restorewaitcursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)zu implementieren.

```
virtual void DoWaitCursor(int nCode);
```

### <a name="parameters"></a>Parameter

*nCode*<br/>
Wenn dieser Parameter 1 ist, wird ein warte Cursor angezeigt. Wenn der Wert 0 ist, wird der Warte Cursor wieder hergestellt, ohne den Verweis Zähler zu erhöhen. Wenn-1, endet der Warte Cursor.

### <a name="remarks"></a>Hinweise

Der Standardwert implementiert einen Sanduhr Cursor. `DoWaitCursor` verwaltet einen Verweis Zähler. Wenn dies positiv ist, wird der Sanduhr Cursor angezeigt.

Obwohl Sie `DoWaitCursor` in der Regel nicht direkt aufzurufen, können Sie diese Member-Funktion überschreiben, um den warte Cursor zu ändern, oder um zusätzliche Verarbeitungsschritte durchzuführen, während der Warte Cursor angezeigt wird.

Verwenden Sie `CWaitCursor`, um eine einfachere und optimierte Methode zum Implementieren eines warte Cursors zu verwenden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#37](../../mfc/reference/codesnippet/cpp/cwinapp-class_3.cpp)]

##  <a name="enabled2dsupport"></a>CWinApp:: EnableD2DSupport

Visual Studio 2010 SP1 wird benötigt.

Aktiviert die Unterstützung von Anwendungs D2D. Rufen Sie diese Methode vor der Initialisierung des Hauptfensters auf.

```
BOOL EnableD2DSupport(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>Parameter

*d2dFactoryType*<br/>
Das Threading Modell der D2D Factory und der von ihr erstellten Ressourcen.

*"Write"-Typ*<br/>
Ein-Wert, der angibt, ob das Write Factory-Objekt freigegeben oder isoliert wird.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die D2D-Unterstützung aktiviert wurde, andernfalls false.

##  <a name="enablehtmlhelp"></a>CWinApp:: enablehtmlhelp

Diese Member-Funktion wird aus dem Konstruktor Ihrer `CWinApp`abgeleiteten Klasse aufgerufen, um HTMLHelp für die Hilfe Ihrer Anwendung zu verwenden.

```
void EnableHtmlHelp();
```

### <a name="remarks"></a>Hinweise

##  <a name="enableshellopen"></a>CWinApp:: EnableShellOpen

Diese Funktion wird in der Regel von der `InitInstance` Außerkraftsetzung aufgerufen, damit die Benutzer Ihrer Anwendung Datendateien öffnen können, wenn Sie im Windows-Datei-Manager auf die Dateien doppelklicken.

```
void EnableShellOpen();
```

### <a name="remarks"></a>Hinweise

Nennen Sie die `RegisterShellFileTypes` Member-Funktion in Verbindung mit dieser Funktion, oder stellen Sie eine bereit. Die reg-Datei mit Ihrer Anwendung für die manuelle Registrierung von Dokumenttypen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#38](../../mfc/reference/codesnippet/cpp/cwinapp-class_4.cpp)]

##  <a name="enabletaskbarinteraction"></a>CWinApp:: enabletaskbarinteraktion

Aktiviert die Interaktion in der Taskleiste.

```
BOOL EnableTaskbarInteraction(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parameter

*benabel*<br/>
Gibt an, ob die Interaktion mit der Windows 7-Taskleiste aktiviert (true) oder deaktiviert (false) sein soll.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Interaktion mit der Taskleiste aktiviert oder deaktiviert werden kann.

### <a name="remarks"></a>Hinweise

Diese Methode muss vor dem Erstellen des Hauptfensters aufgerufen werden, andernfalls wird "false" und "false" zurückgegeben.

##  <a name="exitinstance"></a>CWinApp:: ExitInstance

Wird von Framework innerhalb der `Run` Member-Funktion aufgerufen, um diese Instanz der Anwendung zu beenden.

```
virtual int ExitInstance();
```

### <a name="return-value"></a>Rückgabewert

Der Exitcode der Anwendung; der Wert 0 gibt keine Fehler an, und Werte größer als 0 deuten auf einen Fehler hin. Dieser Wert wird als Rückgabewert aus `WinMain`verwendet.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion nicht von einem beliebigen Ort aus aufrufen, sondern innerhalb der `Run` Member-Funktion.

Die Standard Implementierung dieser Funktion schreibt frameworkoptionen in die der Anwendung. INI-Datei. Überschreiben Sie diese Funktion, um zu bereinigen, wenn die Anwendung beendet wird

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#39](../../mfc/reference/codesnippet/cpp/cwinapp-class_5.cpp)]

##  <a name="getapplicationrecoveryparameter"></a>CWinApp:: getapplicationwiederherstellungsparameter

Ruft den Eingabeparameter für die Wiederherstellungsmethode der Anwendung ab.

```
virtual LPVOID GetApplicationRecoveryParameter();
```

### <a name="return-value"></a>Rückgabewert

Der Standardeingabe Parameter für die Anwendungs Wiederherstellungsmethode.

### <a name="remarks"></a>Hinweise

Das Standardverhalten dieser Funktion gibt NULL zurück.

Weitere Informationen finden Sie unter [CWinApp:: applicationwiederherstellungsrückruf](#applicationrecoverycallback).

##  <a name="getapplicationrecoverypinginterval"></a>CWinApp:: getapplicationherstellypinginterval

Gibt die Zeitspanne zurück, die der Neustart-Manager wartet, bis die Wiederherstellungs Rückruffunktion zurückgegeben wird.

```
virtual DWORD GetApplicationRecoveryPingInterval();
```

### <a name="return-value"></a>Rückgabewert

Die Zeitdauer in Millisekunden.

### <a name="remarks"></a>Hinweise

Wenn eine mit dem Neustart-Manager registrierte Anwendung unerwartet beendet wird, versucht die Anwendung, geöffnete Dokumente zu speichern, und ruft die Wiederherstellungs Rückruffunktion auf. Die standardmäßige Wiederherstellungs Rückruffunktion ist [CWinApp:: applicationrecovery Callback](#applicationrecoverycallback).

Die Zeitspanne, die das Framework darauf wartet, dass die Wiederherstellungs Rückruffunktion zurückgegeben wird, ist das Ping-Intervall. Sie können das Ping-Intervall anpassen, indem Sie `CWinApp::GetApplicationRecoveryPingInterval` überschreiben oder einen benutzerdefinierten Wert für `RegisterWithRestartManager`bereitstellen.

##  <a name="getapplicationrestartflags"></a>CWinApp:: getapplicationrestartflags

Gibt die Flags für den Neustart-Manager zurück.

```
virtual DWORD GetApplicationRestartFlags();
```

### <a name="return-value"></a>Rückgabewert

Die Flags für den Neustart-Manager. Die Standard Implementierung gibt 0 (null) zurück.

### <a name="remarks"></a>Hinweise

Die Flags für den Neustart-Manager haben keine Auswirkungen auf die Standard Implementierung. Diese werden für die zukünftige Verwendung bereitgestellt.

Sie legen die Flags fest, wenn Sie die Anwendung mit dem Neustart-Manager mithilfe von [CWinApp:: registerwithrestartmanager](#registerwithrestartmanager)registrieren.

Die möglichen Werte für die Restart-Manager-Flags lauten wie folgt:

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

##  <a name="getappregistrykey"></a>CWinApp:: getappregistrykey

Gibt den Schlüssel für HKEY_CURRENT_USER\\"Software" \registrykey\profile amezurück.

```
HKEY GetAppRegistryKey(CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parameter

*pTM*<br/>
Zeiger auf ein `CAtlTransactionManager` Objekt.

### <a name="return-value"></a>Rückgabewert

Anwendungs Schlüssel, wenn die Funktion erfolgreich ausgeführt wird. andernfalls NULL.

### <a name="remarks"></a>Hinweise

##  <a name="getdatarecoveryhandler"></a>CWinApp:: getdatarecoveryhandler

Ruft den Datenwiederherstellungs-Handler für diese Instanz der Anwendung ab.

```
virtual CDataRecoveryHandler *GetDataRecoveryHandler();
```

### <a name="return-value"></a>Rückgabewert

Der Datenwiederherstellungs-Handler für diese Instanz der Anwendung.

### <a name="remarks"></a>Hinweise

Jede Anwendung, die den Neustart-Manager verwendet, muss über eine Instanz der [cdatarecoveryhandler-Klasse](../../mfc/reference/cdatarecoveryhandler-class.md)verfügen. Diese Klasse ist für die Überwachung offener Dokumente und das automatische Speichern von Dateien verantwortlich. Das Verhalten des `CDataRecoveryHandler` hängt von der Konfiguration des Neustart-Managers ab. Weitere Informationen finden Sie unter [cdatarecoveryhandler-Klasse](../../mfc/reference/cdatarecoveryhandler-class.md).

Diese Methode gibt NULL auf älteren Betriebssystemen als Windows Vista zurück. Der Neustart-Manager wird auf älteren Betriebssystemen als Windows Vista nicht unterstützt.

Wenn die Anwendung derzeit keinen Datenwiederherstellungs-Handler hat, erstellt diese Methode einen und gibt einen Zeiger darauf zurück.

##  <a name="getfirstdoctemplateposition"></a>CWinApp:: GetFirstDocTemplatePosition

Ruft die Position der ersten Dokument Vorlage in der Anwendung ab.

```
POSITION GetFirstDocTemplatePosition() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Positionswert, der zum Abrufen von Iterationen oder Objekt Zeigern verwendet werden kann. NULL, wenn die Liste leer ist.

### <a name="remarks"></a>Hinweise

Verwenden Sie den Positionswert, der in einem [GetNextDocTemplate](#getnextdoctemplate) -Befehl zurückgegeben wird, um das erste [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) -Objekt abzurufen.

##  <a name="gethelpmode"></a>CWinApp:: gethelpmode

Ruft den Typ der von der Anwendung verwendeten Hilfe ab.

```
AFX_HELP_TYPE GetHelpMode();
```

### <a name="return-value"></a>Rückgabewert

Der von der Anwendung verwendete Hilfstyp. Weitere Informationen finden Sie unter [CWinApp:: m_eHelpType](#m_ehelptype) .

##  <a name="getnextdoctemplate"></a>CWinApp:: GetNextDocTemplate

Ruft die von *POS*identifizierte Dokument Vorlage ab und legt dann *POS* auf den Positionswert fest.

```
CDocTemplate* GetNextDocTemplate(POSITION& pos) const;
```

### <a name="parameters"></a>Parameter

*pos*<br/>
Ein Verweis auf einen Positionswert, der von einem vorherigen Aufrufen von `GetNextDocTemplate` oder [GetFirstDocTemplatePosition](#getfirstdoctemplateposition)zurückgegeben wurde. Der Wert wird durch diesen-Befehl auf die nächste Position aktualisiert.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) -Objekt.

### <a name="remarks"></a>Hinweise

Sie können `GetNextDocTemplate` in einer Forward-Iterations Schleife verwenden, wenn Sie die ursprüngliche Position mit einem `GetFirstDocTemplatePosition`-aufrufenden festgelegt haben.

Sie müssen sicherstellen, dass der Positionswert gültig ist. Wenn Sie ungültig ist, wird die Debugversion des Microsoft Foundation Class-Bibliothek Assert.

Wenn die abgerufene Dokument Vorlage der letzte verfügbare ist, wird der neue Wert von *POS* auf NULL festgelegt.

##  <a name="getprinterdevicedefaults"></a>CWinApp:: getprinterdevicedefaults

Mit dieser Member-Funktion können Sie einen Drucker Gerätekontext zum Drucken vorbereiten.

```
BOOL GetPrinterDeviceDefaults(struct tagPDA* pPrintDlg);
```

### <a name="parameters"></a>Parameter

*pprintdlg*<br/>
Ein Zeiger auf eine [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) -Struktur.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Ruft die aktuellen Drucker Standardwerte aus den Fenstern ab. INI-Datei nach Bedarf, oder verwendet die letzte Druckerkonfiguration, die vom Benutzer im Druck Setup festgelegt wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#40](../../mfc/reference/codesnippet/cpp/cwinapp-class_6.cpp)]

##  <a name="getprofilebinary"></a>CWinApp:: getprofilebinary

Rufen Sie diese Member-Funktion auf, um Binärdaten von einem Eintrag innerhalb eines angegebenen Abschnitts der Registrierung der Anwendung oder abzurufen. INI-Datei.

```
BOOL GetProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE* ppData,
    UINT* pBytes);
```

### <a name="parameters"></a>Parameter

*lpszsection*<br/>
Zeigt auf eine auf NULL endende Zeichenfolge, die den Abschnitt mit dem Eintrag angibt.

*lpszentry*<br/>
Zeigt auf eine auf NULL endende Zeichenfolge, die den Eintrag mit dem abzurufenden Wert enthält.

*ppData*<br/>
Verweist auf einen Zeiger, der die Adresse der Daten empfängt.

*Pbytes*<br/>
Verweist auf einen uint, der die Größe der Daten (in Bytes) empfängt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Bei dieser Member-Funktion wird die Groß-/Kleinschreibung nicht beachtet, sodass sich die Zeichen folgen in den Parametern *lpszsection* und *lpszentry* ggf. unterscheiden

> [!NOTE]
> `GetProfileBinary` ordnet einen Puffer zu und gibt die Adresse in \* *ppData*zurück. Der Aufrufer ist für das Freigeben des Puffers mit **delete []** zuständig.

> [!IMPORTANT]
> Die von dieser Funktion zurückgegebenen Daten enden nicht notwendigerweise auf NULL, und der Aufrufer muss die Validierung ausführen. Weitere Informationen finden Sie unter [Vermeiden von Pufferüberläufen](/windows/win32/SecBP/avoiding-buffer-overruns).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#41](../../mfc/reference/codesnippet/cpp/cwinapp-class_7.cpp)]

Ein weiteres Beispiel finden Sie unter [CWinApp:: Beschreib teprofilebinary](#writeprofilebinary).

##  <a name="getprofileint"></a>CWinApp:: GetProfileInt

Rufen Sie diese Memberfunktion auf, um den Ganzzahlwert aus einem Eintrag in einem angegebenen Abschnitt der Registrierung oder der INI-Datei einer Anwendung abzurufen.

```
UINT GetProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nDefault);
```

### <a name="parameters"></a>Parameter

*lpszsection*<br/>
Zeigt auf eine auf NULL endende Zeichenfolge, die den Abschnitt mit dem Eintrag angibt.

*lpszentry*<br/>
Zeigt auf eine auf NULL endende Zeichenfolge, die den Eintrag mit dem abzurufenden Wert enthält.

*ndefault*<br/>
Gibt den zurückzugebenden Standardwert an, wenn der Eintrag vom Framework nicht gefunden werden kann.

### <a name="return-value"></a>Rückgabewert

Der dem bei erfolgreicher Funktion angegebene Eintrag folgende Ganzzahlwert der Zeichenfolge. Der Rückgabewert ist der Wert des *ndefault* -Parameters, wenn die Funktion den Eintrag nicht findet. Der Rückgabewert ist null (0), wenn der dem angegebenen Eintrag entsprechende Wert keine ganze Zahl ist.

Diese Memberfunktion unterstützt Hexadezimalnotation für den Wert in der INI-Datei. Wenn Sie eine Ganzzahl mit Vorzeichen abrufen, sollten Sie den Wert in einen **int**-Wert umwandeln.

### <a name="remarks"></a>Hinweise

Bei dieser Member-Funktion wird die Groß-/Kleinschreibung nicht beachtet, sodass sich die Zeichen folgen in den Parametern *lpszsection* und *lpszentry* ggf. unterscheiden

> [!IMPORTANT]
> Die von dieser Funktion zurückgegebenen Daten enden nicht notwendigerweise auf NULL, und der Aufrufer muss die Validierung ausführen. Weitere Informationen finden Sie unter [Vermeiden von Pufferüberläufen](/windows/win32/SecBP/avoiding-buffer-overruns).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#42](../../mfc/reference/codesnippet/cpp/cwinapp-class_8.cpp)]

Ein weiteres Beispiel finden Sie unter [CWinApp:: Beschreib teprofileint](#writeprofileint).

##  <a name="getprofilestring"></a>CWinApp:: GetProfileString

Rufen Sie diese Member-Funktion auf, um die Zeichenfolge abzurufen, die einem Eintrag innerhalb des angegebenen Abschnitts in der Registrierung der Anwendung zugeordnet ist. INI-Datei.

```
CString GetProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszDefault = NULL);
```

### <a name="parameters"></a>Parameter

*lpszsection*<br/>
Zeigt auf eine auf NULL endende Zeichenfolge, die den Abschnitt mit dem Eintrag angibt.

*lpszentry*<br/>
Verweist auf eine auf NULL endende Zeichenfolge, die den Eintrag enthält, dessen Zeichenfolge abgerufen werden soll. Dieser Wert darf nicht NULL sein.

*lpszdefault*<br/>
Zeigt auf den Standard Zeichen folgen Wert für den angegebenen Eintrag, wenn der Eintrag nicht in der Initialisierungsdatei gefunden werden kann.

### <a name="return-value"></a>Rückgabewert

Der Rückgabewert ist die Zeichenfolge aus der Anwendung. INI-Datei oder *lpszdefault* , wenn die Zeichenfolge nicht gefunden werden kann. Die maximale Zeichen folgen Länge, die vom Framework unterstützt wird, ist _MAX_PATH. Wenn *lpszdefault* gleich NULL ist, ist der Rückgabewert eine leere Zeichenfolge.

### <a name="remarks"></a>Hinweise

> [!IMPORTANT]
> Die von dieser Funktion zurückgegebenen Daten enden nicht notwendigerweise auf NULL, und der Aufrufer muss die Validierung ausführen. Weitere Informationen finden Sie unter [Vermeiden von Pufferüberläufen](/windows/win32/SecBP/avoiding-buffer-overruns).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

Ein weiteres Beispiel finden Sie im Beispiel für [CWinApp:: GetProfileInt](#getprofileint).

##  <a name="getsectionkey"></a>CWinApp:: getsectionkey

Gibt den Schlüssel für HKEY_CURRENT_USER\\"Software" \registrykey\appname\lpszsectionzurück.

```
HKEY GetSectionKey(
    LPCTSTR lpszSection,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parameter

*lpszsection*<br/>
Der Name des Schlüssels, der abgerufen werden soll.

*pTM*<br/>
Zeiger auf ein `CAtlTransactionManager` Objekt.

### <a name="return-value"></a>Rückgabewert

Abschnitts Taste, wenn die Funktion erfolgreich ausgeführt wird. andernfalls NULL.

### <a name="remarks"></a>Hinweise

##  <a name="hideapplication"></a>CWinApp:: hideapplication

Diese Member-Funktion wird aufgerufen, um eine Anwendung vor dem Schließen der geöffneten Dokumente auszublenden.

```
void HideApplication();
```

##  <a name="htmlhelp"></a>CWinApp:: HTMLHelp

Rufen Sie diese Member-Funktion auf, um die HTMLHelp-Anwendung aufzurufen.

```
virtual void HtmlHelp(
    DWORD_PTR dwData,
    UINT nCmd = 0x000F);
```

### <a name="parameters"></a>Parameter

*dwdata*<br/>
Gibt zusätzliche Daten an. Der verwendete Wert hängt vom Wert des *ncmd* -Parameters ab. Standardmäßig `0x000F`, was [HH_HELP_CONTEXT](/previous-versions/windows/desktop/htmlhelp/hh-help-context-command)bedeutet.

*ncmd*<br/>
Gibt den Typ der angeforderten Hilfe an. Eine Liste möglicher Werte und deren Auswirkung auf den *dwdata* -Parameter finden Sie unter der *ucommand* -Parameter, der in den Funktionen [htmlhelpw](/windows/win32/api/htmlhelp/nf-htmlhelp-htmlhelpw) oder [htmlhelpa](/windows/win32/api/htmlhelp/nf-htmlhelp-htmlhelpa) API in der Windows SDK beschrieben wird. 

### <a name="remarks"></a>Hinweise

Das Framework ruft diese Funktion auch auf, um die HTMLHelp-Anwendung aufzurufen.

Das Framework schließt die HTMLHelp-Anwendung automatisch, wenn die Anwendung beendet wird.

##  <a name="initinstance"></a>CWinApp:: InitInstance

In Windows können mehrere Kopien desselben Programms gleichzeitig ausgeführt werden.

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn die Initialisierung erfolgreich ist. andernfalls 0.

### <a name="remarks"></a>Hinweise

Die Anwendungs Initialisierung ist konzeptionell in zwei Abschnitte unterteilt: einmalige Anwendungs Initialisierung, die bei der ersten Ausführung des Programms ausgeführt wird, und instanzerinitialisierung, die jedes Mal ausgeführt wird, wenn eine Kopie des Programms ausgeführt wird, einschließlich des ersten Zeitraums. Die Implementierung von `WinMain` des Frameworks ruft diese Funktion auf.

Überschreiben Sie `InitInstance`, um jede neue Instanz der Anwendung zu initialisieren, die unter Windows ausgeführt wird. In der Regel überschreiben Sie `InitInstance`, um das Hauptfenster Objekt zu erstellen und den `CWinThread::m_pMainWnd` Datenmember so festzulegen, dass er auf dieses Fenster verweist. Weitere Informationen zum Überschreiben dieser Member-Funktion finden Sie unter [CWinApp: die Anwendungsklasse](../../mfc/cwinapp-the-application-class.md).

> [!NOTE]
> MFC-Anwendungen müssen als Singlethread-Apartment (STA) initialisiert werden. Wenn Sie [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) in der `InitInstance` Außerkraftsetzung aufrufen, geben Sie COINIT_APARTMENTTHREADED (anstelle von COINIT_MULTITHREADED) an.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCListView#9](../../atl/reference/codesnippet/cpp/cwinapp-class_10.cpp)]

##  <a name="istaskbarinteractionenabled"></a>CWinApp:: istaskbarinteraktionaktiviert

Gibt an, ob die Interaktion der Windows 7-Taskleiste aktiviert ist.

```
virtual BOOL IsTaskbarInteractionEnabled();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn `EnableTaskbarInteraction` aufgerufen wurde und das Betriebs System Windows 7 oder höher ist.

### <a name="remarks"></a>Hinweise

Die Interaktion mit der Taskleiste bedeutet, dass die MDI-Anwendung den Inhalt von untergeordneten MDI-Miniaturansichten in separaten Miniaturansichten im Registerkarten Format anzeigt, die angezeigt werden, wenn sich der Mauszeiger über der

##  <a name="loadcursor"></a>CWinApp:: LoadCursor

Lädt die durch " *lpszresourcename* " oder durch " *nidresource* " angegebene Cursor Ressource aus der aktuellen ausführbaren Datei.

```
HCURSOR LoadCursor(LPCTSTR lpszResourceName) const;  HCURSOR LoadCursor(UINT nIDResource) const;
```

### <a name="parameters"></a>Parameter

*lpszresourcename*<br/>
Verweist auf eine mit NULL endenden Zeichenfolge, die den Namen der Cursor Ressource enthält. Sie können eine `CString` für dieses Argument verwenden.

*nidresource*<br/>
Die ID der Cursor Ressource. Eine Liste der Ressourcen finden Sie unter [LoadCursor](/windows/win32/api/winuser/nf-winuser-loadcursorw) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ein Handle für einen Cursor, wenn erfolgreich. andernfalls NULL.

### <a name="remarks"></a>Hinweise

`LoadCursor` lädt den Cursor nur in den Arbeitsspeicher, wenn er noch nicht geladen wurde. Andernfalls wird ein Handle der vorhandenen Ressource abgerufen.

Verwenden Sie die Member-Funktion [loadstandardcursor](#loadstandardcursor) oder [loadoemcursor](#loadoemcursor) , um auf die vordefinierten Windows-Cursor zuzugreifen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#44](../../mfc/reference/codesnippet/cpp/cwinapp-class_11.cpp)]

##  <a name="loadicon"></a>CWinApp:: LoadIcon

Lädt die Symbol Ressource mit dem Namen " *lpszresourcename* " oder wird von " *nidresource* " aus der ausführbaren Datei angegeben.

```
HICON LoadIcon(LPCTSTR lpszResourceName) const;  HICON LoadIcon(UINT nIDResource) const;
```

### <a name="parameters"></a>Parameter

*lpszresourcename*<br/>
Verweist auf eine mit NULL endenden Zeichenfolge, die den Namen der Symbol Ressource enthält. Sie können auch eine `CString` für dieses Argument verwenden.

*nidresource*<br/>
ID-Nummer der Symbol Ressource.

### <a name="return-value"></a>Rückgabewert

Ein Handle für ein Symbol, wenn erfolgreich. andernfalls NULL.

### <a name="remarks"></a>Hinweise

`LoadIcon` lädt das Symbol nur, wenn es nicht bereits geladen wurde. Andernfalls wird ein Handle der vorhandenen Ressource abgerufen.

Für den Zugriff auf die vordefinierten Windows-Symbole können Sie die Member-Funktion [loadstandarmemon](#loadstandardicon) oder [loadoemicon](#loadoemicon) verwenden.

> [!NOTE]
> Diese Member-Funktion Ruft die Win32-API-Funktion [LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw)auf, die nur ein Symbol laden kann, dessen Größe dem SM_CXICON-und SM_CYICON Systemmetrikwerte entspricht.

##  <a name="loadoemcursor"></a>CWinApp:: loadoemcursor

Lädt die von *nidcursor*angegebene vordefinierte Windows-Cursor Ressource.

```
HCURSOR LoadOEMCursor(UINT nIDCursor) const;
```

### <a name="parameters"></a>Parameter

*nidcursor*<br/>
Ein **OCR_** Manifest-Konstantenbezeichner, der einen vordefinierten Windows-Cursor angibt. Sie müssen über `#define OEMRESOURCE` verfügen, bevor `#include \<afxwin.h>`, um Zugriff auf die **OCR_** Konstanten in Windows zu erhalten. Micha.

### <a name="return-value"></a>Rückgabewert

Ein Handle für einen Cursor, wenn erfolgreich. andernfalls NULL.

### <a name="remarks"></a>Hinweise

Verwenden Sie die Member-Funktion `LoadOEMCursor` oder [loadstandardcursor](#loadstandardcursor) , um auf die vordefinierten Windows-Cursor zuzugreifen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#45](../../mfc/reference/codesnippet/cpp/cwinapp-class_12.h)]

[!code-cpp[NVC_MFCWindowing#46](../../mfc/reference/codesnippet/cpp/cwinapp-class_13.cpp)]

##  <a name="loadoemicon"></a>CWinApp:: loadoemicon

Lädt die von *ninist on*angegebene vordefinierte Windows-Symbol Ressource.

```
HICON LoadOEMIcon(UINT nIDIcon) const;
```

### <a name="parameters"></a>Parameter

*nididaktion*<br/>
Ein **OIC_** Manifest-Konstante Bezeichner, der ein vordefiniertes Windows-Symbol angibt. Sie müssen `#define OEMRESOURCE`, bevor `#include \<afxwin.h>`, um auf die **OIC_** Konstanten in Windows zugreifen zu können. Micha.

### <a name="return-value"></a>Rückgabewert

Ein Handle für ein Symbol, wenn erfolgreich. andernfalls NULL.

### <a name="remarks"></a>Hinweise

Verwenden Sie zum Zugreifen auf die vordefinierten Windows-Symbole die Member-Funktion `LoadOEMIcon` oder [loadstandarmemon](#loadstandardicon) .

##  <a name="loadstandardcursor"></a>CWinApp:: loadstandardcursor

Lädt die vordefinierte Windows-Cursor Ressource, die *lpszcursorname* angibt.

```
HCURSOR LoadStandardCursor(LPCTSTR lpszCursorName) const;
```

### <a name="parameters"></a>Parameter

*lpszcurrsorname*<br/>
Ein **IDC_** Manifest-Konstantenbezeichner, der einen vordefinierten Windows-Cursor angibt. Diese Bezeichner werden in Windows definiert. Micha. In der folgenden Liste werden die möglichen vordefinierten Werte und Bedeutungen für *lpszcurrsorname*angezeigt:

- Standard Pfeilcursor IDC_ARROW

- IDC_IBEAM Standard-Text Einfügecursor

- IDC_WAIT Sanduhr Cursor, der verwendet wird, wenn Windows eine zeitaufwändige Aufgabe ausführt

- IDC_CROSS Kreuz-Cursor zur Auswahl

- IDC_UPARROW Pfeil, der auf eine geraden zeigt

- IDC_SIZE veraltet und wird nicht unterstützt. IDC_SIZEALL verwenden

- IDC_SIZEALL einen Pfeil mit vier Spitzen. Der Cursor, der zum Ändern der Größe eines Fensters verwendet werden soll.

- IDC_ICON veraltet und wird nicht unterstützt. Verwenden Sie IDC_ARROW.

- IDC_SIZENWSE Pfeil mit zwei Spitzen mit endet in der linken oberen und unteren rechten Ecke

- IDC_SIZENESW Pfeil mit zwei Spitzen mit endet auf der oberen rechten und unteren linken Seite

- IDC_SIZEWE horizontalen Pfeil mit zwei Spitzen

- IDC_SIZENS senkrechter Pfeil mit zwei Spitzen

### <a name="return-value"></a>Rückgabewert

Ein Handle für einen Cursor, wenn erfolgreich. andernfalls NULL.

### <a name="remarks"></a>Hinweise

Verwenden Sie die Member-Funktion `LoadStandardCursor` oder [loadoemcursor](#loadoemcursor) , um auf die vordefinierten Windows-Cursor zuzugreifen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#47](../../mfc/reference/codesnippet/cpp/cwinapp-class_14.cpp)]

##  <a name="loadstandardicon"></a>CWinApp:: loadstandardische

Lädt die von *lpszikonname* festgelegte Windows-vordefinierte Symbol Ressource.

```
HICON LoadStandardIcon(LPCTSTR lpszIconName) const;
```

### <a name="parameters"></a>Parameter

*lpszikontoname*<br/>
Ein Manifest konstanter Bezeichner, der ein vordefiniertes Windows-Symbol angibt. Diese Bezeichner werden in Windows definiert. Micha. Eine Liste der möglichen vordefinierten Werte und deren Beschreibungen finden Sie unter dem *lpienname* -Parameter in [LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw) in der Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ein Handle für ein Symbol, wenn erfolgreich. andernfalls NULL.

### <a name="remarks"></a>Hinweise

Verwenden Sie die `LoadStandardIcon`-oder [loadoemicon](#loadoemicon) -Member-Funktion, um auf die vordefinierten Windows-Symbole zuzugreifen.

##  <a name="loadstdprofilesettings"></a>CWinApp:: LoadStdProfileSettings

Diese Member-Funktion wird aus der [InitInstance](#initinstance) -Member-Funktion aufgerufen, um die Liste der zuletzt verwendeten Dateien (MRU) und des letzten Vorschau Zustands zu aktivieren und zu laden.

```
void LoadStdProfileSettings(UINT nMaxMRU = _AFX_MRU_COUNT);
```

### <a name="parameters"></a>Parameter

*nmaxmru*<br/>
Die Anzahl der zuletzt verwendeten Dateien, die nachverfolgt werden sollen.

### <a name="remarks"></a>Hinweise

Wenn *nmaxmru* den Wert 0 hat, wird keine MRU-Liste beibehalten.

##  <a name="m_bhelpmode"></a>CWinApp:: m_bHelpMode

TRUE, wenn sich die Anwendung im Hilfe Kontext Modus befindet (mit UMSCHALT + F1 konsistent aufgerufen); andernfalls false.

```
BOOL m_bHelpMode;
```

### <a name="remarks"></a>Hinweise

Im Hilfe Kontext Modus wird der Cursor zu einem Fragezeichen, und der Benutzer kann ihn über den Bildschirm verschieben. Überprüfen Sie dieses Flag, wenn Sie im Hilfe Modus eine spezielle Behandlung implementieren möchten. `m_bHelpMode` ist eine öffentliche Variable des Typs bool.

##  <a name="m_dwrestartmanagersupportflags"></a>CWinApp:: m_dwRestartManagerSupportFlags

Flags, die bestimmen, wie sich der Neustart-Manager verhält.

```
DWORD m_dwRestartManagerSupportFlags;
```

### <a name="remarks"></a>Hinweise

Um den Neustart-Manager zu aktivieren, legen Sie `m_dwRestartManagerSupportFlags` auf das gewünschte Verhalten fest. In der folgenden Tabelle sind die verfügbaren Flags aufgeführt.

|||
|-|-|
|Flag|Beschreibung|
|AFX_RESTART_MANAGER_SUPPORT_RESTART|Die Anwendung wird mit [CWinApp:: registerwithrestartmanager](#registerwithrestartmanager)registriert. Der Neustart-Manager ist dafür verantwortlich, die Anwendung neu zu starten, wenn Sie unerwartet beendet wird.|
|-AFX_RESTART_MANAGER_SUPPORT_RECOVERY|Die Anwendung wird beim Neustart-Manager registriert, und der Neustart-Manager ruft die Wiederherstellungs Rückruffunktion auf, wenn die Anwendung neu gestartet wird. Die standardmäßige Wiederherstellungs Rückruffunktion ist [CWinApp:: applicationrecovery Callback](#applicationrecoverycallback).|
|-AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART|Autosave ist aktiviert, und der Neustart-Manager speichert automatisch alle geöffneten Dokumente, wenn die Anwendung neu gestartet wird.|
|- AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL|Die automatische Speicherung ist aktiviert, und der Neustart-Manager speichert alle geöffneten Dokumente in regelmäßigen Abständen automatisch. Das Intervall wird durch [CWinApp:: m_nAutosaveInterval](#m_nautosaveinterval)definiert.|
|- AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES|Der Neustart-Manager öffnet bereits geöffnete Dokumente, nachdem die Anwendung von einem unerwarteten Beenden neu gestartet wurde. Die [cdatarecoveryhandler-Klasse](../../mfc/reference/cdatarecoveryhandler-class.md) behandelt das Speichern der Liste mit geöffneten Dokumenten und deren Wiederherstellung.|
|-AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES|Der Neustart-Manager fordert den Benutzer auf, automatisch gespeicherte Dateien nach dem Neustart der Anwendung wiederherzustellen. Die `CDataRecoveryHandler`-Klasse fragt den Benutzer ab.|
|- AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE|Die Vereinigung von AFX_RESTART_MANAGER_SUPPORT_RESTART, AFX_RESTART_MANAGER_SUPPORT_RECOVER und AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES.|
|- AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS|Die Vereinigung von AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART, AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL und AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|
|- AFX_RESTART_MANAGER_SUPPORT_RESTART_ASPECTS|Die Vereinigung von AFX_RESTART_MANAGER_SUPPORT_RESTART, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES und AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|
|-AFX_RESTART_MANAGER_SUPPORT_RECOVERY_ASPECTS|Die Union-ofAFX_RESTART_MANAGER_SUPPORT_RECOVERY, die AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES und AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|

##  <a name="m_ehelptype"></a>CWinApp:: m_eHelpType

Der Typ dieses Datenmembers ist der enumerierte Typ AFX_HELP_TYPE, der in der `CWinApp` Klasse definiert ist.

```
AFX_HELP_TYPE m_eHelpType;
```

### <a name="remarks"></a>Hinweise

Die AFX_HELP_TYPE-Enumeration wird wie folgt definiert:

```
enum AFX_HELP_TYPE {
    afxWinHelp = 0,
    afxHTMLHelp = 1
    };
```

- Um die Hilfe der Anwendung auf die HTML-Hilfe festzulegen, wenden Sie [sethelpmode](#sethelpmode) an, und geben Sie `afxHTMLHelp`an.

- Um die Hilfe der Anwendung auf WinHelp festzulegen, wenden Sie `SetHelpMode` an, und geben Sie `afxWinHelp`an.

##  <a name="m_hinstance"></a>CWinApp:: m_hInstance

Entspricht dem von Windows an `WinMain`übergebenen *HINSTANCE* -Parameter.

```
HINSTANCE m_hInstance;
```

### <a name="remarks"></a>Hinweise

Der `m_hInstance` Datenmember ist ein Handle für die aktuelle Instanz der Anwendung, die unter Windows ausgeführt wird. Dies wird von der globalen Funktion [AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle)zurückgegeben. `m_hInstance` ist eine öffentliche Variable des Typs HINSTANCE.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#55](../../mfc/reference/codesnippet/cpp/cwinapp-class_15.cpp)]

##  <a name="m_lpcmdline"></a>CWinApp:: m_lpCmdLine

Entspricht dem *lpCmdLine* -Parameter, der von Windows an `WinMain`übergeben wird.

```
LPTSTR m_lpCmdLine;
```

### <a name="remarks"></a>Hinweise

Verweist auf eine mit NULL endenden Zeichenfolge, die die Befehlszeile für die Anwendung angibt. Verwenden Sie `m_lpCmdLine`, um auf Befehlszeilenargumente zuzugreifen, die der Benutzer beim Starten der Anwendung eingegeben hat. `m_lpCmdLine` ist eine öffentliche Variable des Typs LPTSTR.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

##  <a name="m_nautosaveinterval"></a>CWinApp:: m_nAutosaveInterval

Die Zeitspanne (in Millisekunden) zwischen den AutoSpeichern.

```
int m_nAutosaveInterval;
```

### <a name="remarks"></a>Hinweise

Sie können den Neustart-Manager so konfigurieren, dass geöffnete Dokumente automatisch in festgelegten Intervallen gespeichert werden. Wenn die Anwendung Dateien nicht automatisch speichert, hat dieser Parameter keine Auswirkungen.

##  <a name="m_ncmdshow"></a>CWinApp:: m_nCmdShow

Entspricht dem *nCmdShow* -Parameter, der von Windows an `WinMain`übergeben wird.

```
int m_nCmdShow;
```

### <a name="remarks"></a>Hinweise

Sie sollten `m_nCmdShow` als Argument übergeben, wenn Sie [CWnd:: ShowWindow](../../mfc/reference/cwnd-class.md#showwindow) für das Hauptfenster der Anwendung aufzurufen. `m_nCmdShow` ist eine öffentliche Variable vom Typ **int**.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#56](../../mfc/reference/codesnippet/cpp/cwinapp-class_17.cpp)]

##  <a name="m_pactivewnd"></a>CWinApp:: m_pActiveWnd

Verwenden Sie dieses Datenmember, um einen Zeiger auf das Hauptfenster der OLE-Containeranwendung zu speichern, bei der Ihre OLE-Serveranwendung direkt aktiviert ist.

### <a name="remarks"></a>Hinweise

Wenn dieser Datenmember NULL ist, ist die Anwendung nicht direkt aktiv.

Das Framework legt diese Element Variable fest, wenn das Rahmen Fenster direkt von einer OLE-Containeranwendung aktiviert wird.

##  <a name="m_pdatarecoveryhandler"></a>CWinApp:: m_pDataRecoveryHandler

Zeiger auf den Datenwiederherstellungs-Handler für die Anwendung.

```
CDataRecoveryHandler* m_pDataRecoveryHandler;
```

### <a name="remarks"></a>Hinweise

Der Datenwiederherstellungs-Handler einer Anwendung überwacht geöffnete Dokumente und speichert Sie automatisch. Das Framework verwendet den Datenwiederherstellungs-Handler, um automatisch gespeicherte Dateien wiederherzustellen, wenn eine Anwendung neu gestartet wird, nachdem Sie unerwartet beendet wurde. Weitere Informationen finden Sie unter [cdatarecoveryhandler-Klasse](../../mfc/reference/cdatarecoveryhandler-class.md).

##  <a name="m_pszappname"></a>CWinApp:: m_pszAppName

Gibt den Namen der Anwendung an.

```
LPCTSTR m_pszAppName;
```

### <a name="remarks"></a>Hinweise

Der Anwendungsname kann aus dem Parameter stammen, der an den [CWinApp](#cwinapp) -Konstruktor übergeben wurde, oder, wenn er nicht angegeben ist, an die Ressourcen Zeichenfolge mit der ID AFX_IDS_APP_TITLE. Wenn der Anwendungsname nicht in der Ressource gefunden wird, stammt er vom Programm. EXE-Dateiname

Wird von der globalen Funktion [afxgetappname](application-information-and-management.md#afxgetappname)zurückgegeben. `m_pszAppName` ist eine öffentliche Variable vom Typ " **Konstanten char** <strong>\*</strong>".

> [!NOTE]
> Wenn Sie `m_pszAppName`einen Wert zuweisen, muss er dynamisch auf dem Heap zugeordnet werden. Der `CWinApp` Dekonstruktor Ruft mit diesem Zeiger **Free**() auf. Sie möchten für die Zuordnung die `_tcsdup`()-Lauf Zeit Bibliotheksfunktion verwenden. Außerdem müssen Sie den dem aktuellen Zeiger zugeordneten Arbeitsspeicher freigeben, bevor Sie einen neuen Wert zuweisen. Beispiel:

[!code-cpp[NVC_MFCWindowing#57](../../mfc/reference/codesnippet/cpp/cwinapp-class_18.cpp)]

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#65](../../mfc/reference/codesnippet/cpp/cwinapp-class_19.cpp)]

##  <a name="m_pszexename"></a>CWinApp:: m_pszExeName

Enthält den Namen der ausführbaren Datei der Anwendung ohne Erweiterung.

```
LPCTSTR m_pszExeName;
```

### <a name="remarks"></a>Hinweise

Im Gegensatz zu [m_pszAppName](#m_pszappname)darf dieser Name keine Leerzeichen enthalten. `m_pszExeName` ist eine öffentliche Variable vom Typ " **Konstanten char** <strong>\*</strong>".

> [!NOTE]
> Wenn Sie `m_pszExeName`einen Wert zuweisen, muss er dynamisch auf dem Heap zugeordnet werden. Der `CWinApp` Dekonstruktor Ruft mit diesem Zeiger **Free**() auf. Sie möchten für die Zuordnung die `_tcsdup`()-Lauf Zeit Bibliotheksfunktion verwenden. Außerdem müssen Sie den dem aktuellen Zeiger zugeordneten Arbeitsspeicher freigeben, bevor Sie einen neuen Wert zuweisen. Beispiel:

[!code-cpp[NVC_MFCWindowing#58](../../mfc/reference/codesnippet/cpp/cwinapp-class_20.cpp)]

##  <a name="m_pszhelpfilepath"></a>CWinApp:: m_pszHelpFilePath

Enthält den Pfad zur Hilfedatei der Anwendung.

```
LPCTSTR m_pszHelpFilePath;
```

### <a name="remarks"></a>Hinweise

Standardmäßig initialisiert das Framework `m_pszHelpFilePath` mit dem Namen der Anwendung mit ". HLP "angehängt. Um den Namen der Hilfedatei zu ändern, legen Sie `m_pszHelpFilePath` so fest, dass er auf eine Zeichenfolge verweist, die den kompletten Namen der gewünschten Hilfedatei enthält. Eine bequeme Stelle hierfür ist die [InitInstance](#initinstance) -Funktion der Anwendung. `m_pszHelpFilePath` ist eine öffentliche Variable vom Typ " **Konstanten char** <strong>\*</strong>".

> [!NOTE]
> Wenn Sie `m_pszHelpFilePath`einen Wert zuweisen, muss er dynamisch auf dem Heap zugeordnet werden. Der `CWinApp` Dekonstruktor Ruft mit diesem Zeiger **Free**() auf. Sie möchten für die Zuordnung die `_tcsdup`()-Lauf Zeit Bibliotheksfunktion verwenden. Außerdem müssen Sie den dem aktuellen Zeiger zugeordneten Arbeitsspeicher freigeben, bevor Sie einen neuen Wert zuweisen. Beispiel:

[!code-cpp[NVC_MFCWindowing#59](../../mfc/reference/codesnippet/cpp/cwinapp-class_21.cpp)]

##  <a name="m_pszprofilename"></a>CWinApp:: m_pszProfileName

Enthält den Namen der Anwendung. INI-Datei.

```
LPCTSTR m_pszProfileName;
```

### <a name="remarks"></a>Hinweise

`m_pszProfileName` ist eine öffentliche Variable vom Typ " **Konstanten char** <strong>\*</strong>".

> [!NOTE]
> Wenn Sie `m_pszProfileName`einen Wert zuweisen, muss er dynamisch auf dem Heap zugeordnet werden. Der `CWinApp` Dekonstruktor Ruft mit diesem Zeiger **Free**() auf. Sie möchten für die Zuordnung die `_tcsdup`()-Lauf Zeit Bibliotheksfunktion verwenden. Außerdem müssen Sie den dem aktuellen Zeiger zugeordneten Arbeitsspeicher freigeben, bevor Sie einen neuen Wert zuweisen. Beispiel:

[!code-cpp[NVC_MFCWindowing#60](../../mfc/reference/codesnippet/cpp/cwinapp-class_22.cpp)]

##  <a name="m_pszregistrykey"></a>CWinApp:: m_pszRegistryKey

Wird verwendet, um zu bestimmen, wo Anwendungsprofil Einstellungen in der Registrierung oder der INI-Datei gespeichert werden.

```
LPCTSTR m_pszRegistryKey;
```

### <a name="remarks"></a>Hinweise

Normalerweise wird dieser Datenmember als schreibgeschützt behandelt.

- Der Wert wird in einem Registrierungsschlüssel gespeichert. Der Name der Anwendungsprofil Einstellung wird an den folgenden Registrierungsschlüssel angehängt: HKEY_CURRENT_USER/Software/localappwizard-generated/.

Wenn Sie `m_pszRegistryKey`einen Wert zuweisen, muss er dynamisch auf dem Heap zugeordnet werden. Der `CWinApp` Dekonstruktor Ruft mit diesem Zeiger **Free**() auf. Sie möchten für die Zuordnung die `_tcsdup`()-Lauf Zeit Bibliotheksfunktion verwenden. Außerdem müssen Sie den dem aktuellen Zeiger zugeordneten Arbeitsspeicher freigeben, bevor Sie einen neuen Wert zuweisen. Beispiel:

[!code-cpp[NVC_MFCWindowing#61](../../mfc/reference/codesnippet/cpp/cwinapp-class_23.cpp)]

##  <a name="m_pszappid"></a>CWinApp:: m_pszAppID

ID des Anwendungs Benutzer Modells.

```
LPCTSTR m_pszAppID;
```

### <a name="remarks"></a>Hinweise

##  <a name="oncontexthelp"></a>CWinApp:: oncontexthelp

Verarbeitet die UMSCHALT + F1-Hilfe in der Anwendung.

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>Hinweise

Sie müssen ihrer `CWinApp` Class Message Map eine `ON_COMMAND( ID_CONTEXT_HELP, OnContextHelp )`-Anweisung hinzufügen und außerdem einen Zugriffstasten-Tabelleneintrag hinzufügen (normalerweise UMSCHALT + F1), um diese Element Funktion zu aktivieren.

`OnContextHelp` versetzt die Anwendung in den Hilfe Modus. Der Cursor wechselt zu einem Pfeil und einem Fragezeichen, und der Benutzer kann dann den Mauszeiger bewegen und die linke Maustaste drücken, um ein Dialogfeld, ein Fenster, ein Menü oder eine Befehls Schaltfläche auszuwählen. Diese Member-Funktion Ruft den Hilfe Kontext des-Objekts unter dem Cursor ab und ruft die WinHelp-Funktion von Windows mit diesem Hilfe Kontext auf.

##  <a name="onddecommand"></a>CWinApp:: onddecommand

Wird von Framework aufgerufen, wenn das Hauptrahmen Fenster eine DDE-Execute-Nachricht empfängt.

```
virtual BOOL OnDDECommand(LPTSTR lpszCommand);
```

### <a name="parameters"></a>Parameter

*lpszcommand*<br/>
Verweist auf eine von der Anwendung empfangene DDE-Befehls Zeichenfolge.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Befehl verarbeitet wird. andernfalls 0.

### <a name="remarks"></a>Hinweise

Die Standard Implementierung überprüft, ob der Befehl eine Anforderung zum Öffnen eines Dokuments ist, und öffnet, wenn dies der Fall ist, das angegebene Dokument. Der Windows-Datei-Manager sendet diese DDE-Befehls Zeichenfolgen normalerweise, wenn der Benutzer auf eine Datendatei doppelklickt. Überschreiben Sie diese Funktion, um andere DDE Execute-Befehle zu verarbeiten, z. b. den auszudruckenden Befehl

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#48](../../mfc/reference/codesnippet/cpp/cwinapp-class_24.cpp)]

##  <a name="onfilenew"></a>CWinApp:: OnFile-Datei

Implementiert den ID_FILE_NEW-Befehl.

```
afx_msg void OnFileNew();
```

### <a name="remarks"></a>Hinweise

Sie müssen ihrer `CWinApp` Class Message Map eine `ON_COMMAND( ID_FILE_NEW, OnFileNew )`-Anweisung hinzufügen, um diese Member-Funktion zu aktivieren. Wenn diese Funktion aktiviert ist, wird die Ausführung des Datei neuen Befehls behandelt.

Weitere Informationen zum Standardverhalten und Anleitungen zum Überschreiben dieser Member-Funktion finden [Sie unter Technical Note 22](../../mfc/tn022-standard-commands-implementation.md) .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

##  <a name="onfileopen"></a>CWinApp:: OnFileOpen

Implementiert den ID_FILE_OPEN-Befehl.

```
afx_msg void OnFileOpen();
```

### <a name="remarks"></a>Hinweise

Sie müssen ihrer `CWinApp` Class Message Map eine `ON_COMMAND( ID_FILE_OPEN, OnFileOpen )`-Anweisung hinzufügen, um diese Member-Funktion zu aktivieren. Wenn diese Funktion aktiviert ist, wird die Ausführung des Datei Öffnungs Befehls behandelt.

Weitere Informationen zum Standardverhalten und Anleitungen zum Überschreiben dieser Member-Funktion finden [Sie unter Technical Note 22](../../mfc/tn022-standard-commands-implementation.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

##  <a name="onfileprintsetup"></a>CWinApp:: onfileprintsetup

Implementiert den ID_FILE_PRINT_SETUP-Befehl.

```
afx_msg void OnFilePrintSetup();
```

### <a name="remarks"></a>Hinweise

Sie müssen ihrer `CWinApp` Class Message Map eine `ON_COMMAND( ID_FILE_PRINT_SETUP, OnFilePrintSetup )`-Anweisung hinzufügen, um diese Member-Funktion zu aktivieren. Wenn diese Funktion aktiviert ist, wird die Ausführung des File Print-Befehls behandelt.

Weitere Informationen zum Standardverhalten und Anleitungen zum Überschreiben dieser Member-Funktion finden [Sie unter Technical Note 22](../../mfc/tn022-standard-commands-implementation.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

##  <a name="onhelp"></a>CWinApp:: onhelp

Verarbeitet die F1-Hilfe in der Anwendung (unter Verwendung des aktuellen Kontexts).

```
afx_msg void OnHelp();
```

### <a name="remarks"></a>Hinweise

In der Regel fügen Sie auch einen Zugriffstasten Eintrag für die F1-Taste hinzu. Das Aktivieren der F1-Taste ist nur eine Konvention und keine Anforderung.

Sie müssen ihrer `CWinApp` Class Message Map eine `ON_COMMAND( ID_HELP, OnHelp )`-Anweisung hinzufügen, um diese Member-Funktion zu aktivieren. Wenn diese Option aktiviert ist, wird Sie von Framework aufgerufen, wenn der Benutzer die F1-Taste drückt.

Die Standard Implementierung dieser nachrichtenhandlerfunktion bestimmt den Hilfe Kontext, der dem aktuellen Fenster, Dialogfeld oder Menü Element entspricht, und ruft dann WinHelp auf. Speichert. Wenn derzeit kein Kontext verfügbar ist, verwendet die Funktion den Standardkontext.

Überschreiben Sie diese Member-Funktion, um den Hilfe Kontext auf einen anderen Wert als das Fenster, Dialogfeld, Menü Element oder Symbolleisten Schaltfläche festzulegen, das derzeit den Fokus besitzt. Ruft `WinHelp` mit der gewünschten Hilfe Kontext-ID auf.

##  <a name="onhelpfinder"></a>CWinApp:: onhelpfinder

Behandelt die Befehle ID_HELP_FINDER und ID_DEFAULT_HELP.

```
afx_msg void OnHelpFinder();
```

### <a name="remarks"></a>Hinweise

Sie müssen ihrer `CWinApp` Class Message Map eine `ON_COMMAND( ID_HELP_FINDER, OnHelpFinder )`-Anweisung hinzufügen, um diese Member-Funktion zu aktivieren. Wenn diese Option aktiviert ist, ruft das Framework diese nachrichtenhandlerfunktion auf, wenn der Benutzer der Anwendung den Help Finder-Befehl auswählt, um `WinHelp` mit dem Standard **HELP_FINDER** Thema aufzurufen.

##  <a name="onhelpindex"></a>CWinApp:: onhelpindex

Behandelt den ID_HELP_INDEX Befehl und stellt ein Standard Hilfethema bereit.

```
afx_msg void OnHelpIndex();
```

### <a name="remarks"></a>Hinweise

Sie müssen ihrer `CWinApp` Class Message Map eine `ON_COMMAND( ID_HELP_INDEX, OnHelpIndex )`-Anweisung hinzufügen, um diese Member-Funktion zu aktivieren. Wenn diese Option aktiviert ist, ruft das Framework diese nachrichtenhandlerfunktion auf, wenn der Benutzer der Anwendung den Befehl Help Index auswählt, um `WinHelp` mit dem Standard **HELP_INDEX** Thema aufzurufen.

##  <a name="onhelpusing"></a>CWinApp:: onhelpusing

Behandelt den ID_HELP_USING Befehl.

```
afx_msg void OnHelpUsing();
```

### <a name="remarks"></a>Hinweise

Sie müssen ihrer `CWinApp` Class Message Map eine `ON_COMMAND( ID_HELP_USING, OnHelpUsing )`-Anweisung hinzufügen, um diese Member-Funktion zu aktivieren. Das Framework ruft diese nachrichtenhandlerfunktion auf, wenn der Benutzer der Anwendung den Befehl Hilfe using zum Aufrufen der `WinHelp` Anwendung mit dem Standard **HELP_HELPONHELP** Thema auswählt.

##  <a name="onidle"></a>CWinApp:: OnIdle

Überschreiben Sie diese Member-Funktion, um die Leerlaufzeit Verarbeitung auszuführen.

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>Parameter

*lCount*<br/>
Ein Wert, der jedes Mal erhöht wird, wenn `OnIdle` aufgerufen wird, wenn die Nachrichten Warteschlange der Anwendung leer ist. Diese Anzahl wird jedes Mal auf 0 zurückgesetzt, wenn eine neue Nachricht verarbeitet wird. Sie können den *lCount* -Parameter verwenden, um die relative Zeitspanne zu bestimmen, in der sich die Anwendung im Leerlauf befand, ohne eine Nachricht zu verarbeiten.

### <a name="return-value"></a>Rückgabewert

Nicht NULL, um mehr Leerlauf Verarbeitungszeit zu erhalten. 0, wenn keine Leerlaufzeit mehr benötigt wird.

### <a name="remarks"></a>Hinweise

`OnIdle` wird in der Standard Nachrichten Schleife aufgerufen, wenn die Nachrichten Warteschlange der Anwendung leer ist. Verwenden Sie Ihre außer Kraft setzung, um eigene hintergrundhandleraufgaben im Hintergrund aufzurufen.

`OnIdle` sollte 0 zurückgeben, um anzugeben, dass keine Leerlauf Verarbeitungszeit erforderlich ist. Der *lCount* -Parameter wird jedes Mal inkrementiert, wenn `OnIdle` aufgerufen wird, wenn die Nachrichten Warteschlange leer ist, und auf 0 zurückgesetzt, wenn eine neue Nachricht verarbeitet wird. Basierend auf dieser Anzahl können Sie Ihre verschiedenen Leerlauf Routinen aufzurufen.

Im folgenden wird die Verarbeitung der Leerlauf Schleife zusammengefasst:

1. Wenn die Nachrichten Schleife im Microsoft Foundation Class-Bibliothek die Meldungs Warteschlange überprüft und keine ausstehenden Nachrichten findet, ruft Sie `OnIdle` für das Anwendungs Objekt auf und gibt 0 als *lCount* -Argument an.

2. `OnIdle` führt einige Verarbeitungsvorgänge aus und gibt einen Wert ungleich 0 (null) zurück, um anzugeben, dass er erneut aufgerufen werden soll, um die Verarbeitung

3. Die Nachrichten Schleife prüft die Meldungs Warteschlange erneut. Wenn keine Nachrichten ausstehend sind, wird `OnIdle` erneut aufgerufen, um das *lCount* -Argument zu erhöhen.

4. Schließlich wird `OnIdle` die Verarbeitung aller Leerlauf Tasks abgeschlossen und 0 zurückgegeben. Dadurch wird der Nachrichten Schleife mitgeteilt, dass der Aufruf von `OnIdle` beendet wird, bis die nächste Nachricht von der Nachrichten Warteschlange empfangen wird. zu diesem Zeitpunkt wird der Leerlauf Zyklen neu gestartet, wobei das Argument auf 0 festgelegt ist

Führen Sie während `OnIdle` keine langen Aufgaben aus, da Ihre Anwendung Benutzereingaben erst verarbeiten kann, wenn `OnIdle` zurückgibt.

> [!NOTE]
> Die Standard Implementierung von `OnIdle` aktualisiert Befehls Benutzeroberflächen Objekte, wie z. b. Menü Elemente und Symbolleisten Schaltflächen, und führt eine interne Bereinigung der Datenstruktur durch. Wenn Sie `OnIdle`überschreiben, müssen Sie daher `CWinApp::OnIdle` mit dem `lCount` in der überschriebenen Version aufzurufen. Zuerst wird die gesamte Basisklassen-Leerlauf Verarbeitung aufgerufen (d. h., bis die Basisklasse `OnIdle` 0 zurückgibt). Wenn Sie vor Abschluss der Verarbeitung der Basisklasse Arbeiten ausführen müssen, überprüfen Sie die Basisklassen Implementierung, um die richtige *lCount* -Anweisung auszuwählen, in der Sie Ihre Arbeit erledigen möchten.

Wenn Sie nicht möchten, dass `OnIdle` immer dann aufgerufen wird, wenn eine Nachricht aus der Nachrichten Warteschlange abgerufen wird, können Sie [cwinthreadisidlemessage](../../mfc/reference/cwinthread-class.md#isidlemessage)überschreiben. Wenn eine Anwendung einen sehr kurzen Timer festgelegt hat, oder wenn das System die WM_SYSTIMER Nachricht sendet, wird `OnIdle` wiederholt aufgerufen, und die Leistung wird beeinträchtigt.

### <a name="example"></a>Beispiel

In den folgenden zwei Beispielen wird gezeigt, wie Sie `OnIdle`verwenden. Im ersten Beispiel werden zwei Leerlauf Aufgaben verarbeitet, wobei das *lCount* -Argument verwendet wird, um die Aufgaben zu priorisieren. Die erste Aufgabe ist eine hohe Priorität, und Sie sollten Sie nach Möglichkeit verwenden. Die zweite Aufgabe ist weniger wichtig und sollte nur ausgeführt werden, wenn eine lange Pause in der Benutzereingabe vorliegt. Beachten Sie den Rückruf der Basisklassen Version von `OnIdle`. Im zweiten Beispiel wird eine Gruppe von Leerlauf Tasks mit unterschiedlichen Prioritäten verwaltet.

[!code-cpp[NVC_MFCWindowing#51](../../mfc/reference/codesnippet/cpp/cwinapp-class_27.cpp)]

##  <a name="opendocumentfile"></a>CWinApp:: OpenDocumentFile

Das Framework ruft diese Methode auf, um die benannte [CDocument](../../mfc/reference/cdocument-class.md) -Datei für die Anwendung zu öffnen.

```
virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszFileName
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>Parameter

*lpszfilename*<br/>
in Der Name der Datei, die geöffnet werden soll.

*baddtomru*<br/>
in TRUE gibt an, dass das Dokument eine der aktuellsten Dateien ist. FALSE gibt an, dass das Dokument nicht eine der aktuellsten Dateien ist.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf einen `CDocument`, wenn der Vorgang erfolgreich war. andernfalls NULL.

### <a name="remarks"></a>Hinweise

Wenn ein Dokument mit diesem Namen bereits geöffnet ist, erhält das erste Rahmen Fenster, das das Dokument enthält, den Fokus. Wenn eine Anwendung mehrere Dokumentvorlagen unterstützt, verwendet das Framework die Dateinamenerweiterung, um die entsprechende Dokument Vorlage zum Laden des Dokuments zu suchen. Wenn erfolgreich, erstellt die Dokument Vorlage ein Rahmen Fenster und eine Ansicht für das Dokument.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

##  <a name="parsecommandline"></a>CWinApp::P arccommandline

Mit dieser Member-Funktion können Sie die Befehlszeile analysieren und die Parameter nacheinander an [ccommandlineinfo::P arseparam](../../mfc/reference/ccommandlineinfo-class.md#parseparam)senden.

```
void ParseCommandLine(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>Parameter

*rcmdinfo*<br/>
Ein Verweis auf ein [ccommandlineinfo](../../mfc/reference/ccommandlineinfo-class.md) -Objekt.

### <a name="remarks"></a>Hinweise

Wenn Sie ein neues MFC-Projekt mithilfe des Anwendungs-Assistenten starten, erstellt der Anwendungs-Assistent eine lokale Instanz von `CCommandLineInfo`und ruft dann `ProcessShellCommand` und `ParseCommandLine` in der [InitInstance](#initinstance) -Member-Funktion auf. Eine Befehlszeile folgt der unten beschriebenen Route:

1. Nachdem Sie in `InitInstance`erstellt wurde, wird das `CCommandLineInfo` Objekt an `ParseCommandLine`übermittelt.

2. `ParseCommandLine` ruft dann `CCommandLineInfo::ParseParam` wiederholt auf, einmal für jeden Parameter.

3. `ParseParam` füllt das `CCommandLineInfo`-Objekt, das dann an [ProcessShellCommand](#processshellcommand)weitergeleitet wird.

4. `ProcessShellCommand` behandelt die Befehlszeilenargumente und-Flags.

Beachten Sie, dass Sie `ParseCommandLine` direkt nach Bedarf anrufen können.

Eine Beschreibung der Befehlszeilenflags finden Sie unter [ccommandlineinfo:: m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand).

##  <a name="pretranslatemessage"></a>CWinApp::P retranslatemess Age

Überschreiben Sie diese Funktion, um Fenster Meldungen zu filtern, bevor diese an die Windows-Funktionen [translatemsterage](/windows/win32/api/winuser/nf-winuser-translatemessage) und [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) gesendet werden. die Standard Implementierung führt die Zugriffstasten Übersetzung aus, sodass Sie die `CWinApp::PreTranslateMessage` Member-Funktion in der überschriebenen Version aufrufen müssen.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parameter

*pmsg*<br/>
Ein Zeiger auf eine [msg](/windows/win32/api/winuser/ns-winuser-msg) -Struktur, die die zu verarbeitende Meldung enthält.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn die Nachricht in `PreTranslateMessage` vollständig verarbeitet wurde und nicht weiterverarbeitet werden sollte. 0 (null), wenn die Meldung auf normale Weise verarbeitet werden soll.

##  <a name="processmessagefilter"></a>CWinApp::P rocess MessageFilter

Die Hook-Funktion des Frameworks ruft diese Element Funktion auf, um bestimmte Windows-Meldungen zu filtern und darauf zu reagieren.

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parameter

*Code*<br/>
Gibt einen Hook-Code an. Diese Member-Funktion verwendet den Code, um zu bestimmen, wie *lpmsg* verarbeitet wird.

*lpmsg*<br/>
Ein Zeiger auf eine Windows [msg](/windows/win32/api/winuser/ns-winuser-msg)-truktur.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Nachricht verarbeitet wird. andernfalls 0.

### <a name="remarks"></a>Hinweise

Eine Hook-Funktion verarbeitet Ereignisse, bevor Sie an die normale Nachrichtenverarbeitung der Anwendung gesendet werden.

Wenn Sie diese erweiterte Funktion überschreiben, müssen Sie die Basisklassen Version zum Verwalten der Hook-Verarbeitung des Frameworks aufzurufen.

##  <a name="processshellcommand"></a>CWinApp::P rocess shellcommand

Diese Member-Funktion wird von [InitInstance](#initinstance) aufgerufen, um die Parameter zu akzeptieren, die vom `CCommandLineInfo` Objekt übergeben werden, das von *rcmdinfo*identifiziert wird, und die angegebene Aktion auszuführen.

```
BOOL ProcessShellCommand(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>Parameter

*rcmdinfo*<br/>
Ein Verweis auf ein [ccommandlineinfo](../../mfc/reference/ccommandlineinfo-class.md) -Objekt.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Shellbefehl erfolgreich verarbeitet wird. Wenn der Wert 0 ist, wird von [InitInstance](#initinstance)false zurückgegeben.

### <a name="remarks"></a>Hinweise

Wenn Sie ein neues MFC-Projekt mithilfe des Anwendungs-Assistenten starten, erstellt der Anwendungs-Assistent eine lokale Instanz von `CCommandLineInfo`und ruft dann `ProcessShellCommand` und " [paramesecommandline](#parsecommandline) " in der `InitInstance` Member-Funktion auf. Eine Befehlszeile folgt der unten beschriebenen Route:

1. Nachdem Sie in `InitInstance`erstellt wurde, wird das `CCommandLineInfo` Objekt an `ParseCommandLine`übermittelt.

2. `ParseCommandLine` ruft dann [ccommandlineingefo auf,:P arseparam](../../mfc/reference/ccommandlineinfo-class.md#parseparam) wiederholt, einmal für jeden Parameter.

3. `ParseParam` füllt das `CCommandLineInfo`-Objekt, das dann an `ProcessShellCommand`weitergegeben wird.

4. `ProcessShellCommand` behandelt die Befehlszeilenargumente und-Flags.

Die Datenmember des `CCommandLineInfo` Objekts, die durch [ccommandlineinfo:: m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand)identifiziert werden, sind vom folgenden enumerierten Typ, der in der `CCommandLineInfo`-Klasse definiert ist.

```
enum {
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE
    };
```

Eine kurze Beschreibung der einzelnen Werte finden Sie unter `CCommandLineInfo::m_nShellCommand`.

##  <a name="processwndprocexception"></a>CWinApp::P rocess wndprocexception

Das Framework ruft diese Member-Funktion immer dann auf, wenn der Handler eine Ausnahme abfängt, die in einer der Meldungs-oder Befehls Handlers Ihrer Anwendung ausgelöst wird.

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>Parameter

*e*<br/>
Ein Zeiger auf eine nicht abgefangene Ausnahme.

*pmsg*<br/>
Eine [Nachrichten](/windows/win32/api/winuser/ns-winuser-msg)-TRUKTUR, die Informationen über die Windows-Meldung enthält, die bewirkt hat, dass das Framework eine Ausnahme ausgelöst hat.

### <a name="return-value"></a>Rückgabewert

Der Wert, der an Windows zurückgegeben werden soll. Normalerweise ist dies 0l für Windows-Meldungen, 1L (true) für Befehls Meldungen.

### <a name="remarks"></a>Hinweise

Nennen Sie diese Member-Funktion nicht direkt.

Die Standard Implementierung dieser Member-Funktion erstellt ein Meldungs Feld. Wenn die nicht abgefangene Ausnahme in einem Menü-, Symbolleisten-oder Zugriffstasten-Befehls Fehler auftritt, wird im Meldungs Feld die Meldung "Fehler beim Befehl" angezeigt. Andernfalls wird die Meldung "Interner Anwendungsfehler" angezeigt.

Überschreiben Sie diese Member-Funktion, um eine globale Behandlung der Ausnahmen bereitzustellen. Wenn Sie möchten, dass das Meldungs Feld angezeigt wird, wird nur die Basisfunktionalität aufgerufen.

##  <a name="register"></a>CWinApp:: Register

Führt alle Registrierungs Aufgaben aus, die nicht von `RegisterShellFileTypes`behandelt werden.

```
virtual BOOL Register();
```

### <a name="return-value"></a>Rückgabewert

Bei Erfolg ein Wert ungleich 0 (null), andernfalls 0 (null).

### <a name="remarks"></a>Hinweise

Die Standard Implementierung gibt einfach "true" zurück. Überschreiben Sie diese Funktion, um alle angepassten Registrierungsschritte bereitzustellen.

##  <a name="registershellfiletypes"></a>CWinApp:: RegisterShellFileTypes

Mit dieser Member-Funktion können Sie alle Dokumenttypen Ihrer Anwendung beim Windows-Datei-Manager registrieren.

```
void RegisterShellFileTypes(BOOL bCompat = FALSE);
```

### <a name="parameters"></a>Parameter

*bcompat*<br/>
in TRUE fügt Registrierungseinträge für Shellbefehle drucken und Drucken hinzu, sodass ein Benutzer Dateien direkt aus der Shell drucken oder die Datei auf ein Drucker Objekt ziehen kann. Außerdem wird ein DefaultIcon-Schlüssel hinzugefügt. Standardmäßig ist dieser Parameter für die Abwärtskompatibilität falsch.

### <a name="remarks"></a>Hinweise

Dadurch kann der Benutzer eine Datendatei öffnen, die von Ihrer Anwendung erstellt wurde, indem Sie im Datei-Manager darauf doppelklicken. Ruft `RegisterShellFileTypes` nach dem Abrufen von [AddDocTemplate](#adddoctemplate) für jede Dokument Vorlage in der Anwendung auf. Außerdem wird die Funktion [EnableShellOpen](#enableshellopen) Member aufgerufen, wenn Sie `RegisterShellFileTypes`aufzurufen.

`RegisterShellFileTypes` durchläuft die Liste der [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) -Objekte, die von der Anwendung verwaltet werden, und fügt für jede Dokument Vorlage der Registrierungsdatenbank Einträge hinzu, die von Windows für Dateizuordnungen verwaltet werden. Der Datei-Manager verwendet diese Einträge, um eine Datendatei zu öffnen, wenn der Benutzer darauf doppelklickt. Dadurch entfällt die Notwendigkeit, eine zu liefern. REG-Datei mit Ihrer Anwendung.

> [!NOTE]
> `RegisterShellFileTypes` funktioniert nur, wenn der Benutzer das Programm mit Administratorrechten ausführt. Wenn das Programm nicht über Administratorrechte verfügt, kann es die Registrierungsschlüssel nicht ändern.

Wenn in der Registrierungsdatenbank eine angegebene Dateinamenerweiterung bereits einem anderen Dateityp zugeordnet ist, wird keine neue Zuordnung erstellt. Das Format der Zeichen folgen, die zum Registrieren dieser Informationen erforderlich sind, finden Sie in der `CDocTemplate`-Klasse.

##  <a name="registerwithrestartmanager"></a>CWinApp:: registerwithrestartmanager

Registriert die Anwendung beim Neustart-Manager.

```
virtual HRESULT RegisterWithRestartManager(
    BOOL bRegisterRecoveryCallback,
    const CString& strRestartIdentifier);

virtual HRESULT RegisterWithRestartManager(
    LPCWSTR pwzCommandLineArgs,
    DWORD dwRestartFlags,
    APPLICATION_RECOVERY_CALLBACK pRecoveryCallback,
    LPVOID lpvParam,
    DWORD dwPingInterval,
    DWORD dwCallbackFlags);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|Beschreibung|
|*bregisterwiederherstellungsrückruf*|in TRUE gibt an, dass diese Instanz der Anwendung eine Wiederherstellungs Rückruffunktion verwendet. FALSE gibt an, dass dies nicht der Fall ist. Das Framework ruft die Wiederherstellungs Rückruffunktion auf, wenn die Anwendung unerwartet beendet wird. Weitere Informationen finden Sie unter [CWinApp:: applicationwiederherstellungsrückruf](#applicationrecoverycallback).|
|*"ertifizierer"*|in Die eindeutige Zeichenfolge, die diese Instanz des Neustart-Managers identifiziert. Der Bezeichner für den Neustart-Manager ist für jede Instanz einer Anwendung eindeutig.|
|*pwzcommandlineargs*|in Eine Zeichenfolge, die alle zusätzlichen Argumente von der Befehlszeile enthält.|
|*dwrestartflags*|in Optionale Flags für den Neustart-Manager. Weitere Informationen finden Sie im Abschnitt "Hinweise".|
|*precoverycallback*|in Die Wiederherstellungs Rückruffunktion. Diese Funktion muss einen LPVOID-Parameter als Eingabe annehmen und ein DWORD zurückgeben. Die standardmäßige Wiederherstellungs Rückruffunktion ist `CWinApp::ApplicationRecoveryCallback`.|
|*lpvparam*|in Der Eingabeparameter für die Wiederherstellungs Rückruffunktion. Weitere Informationen finden Sie unter [CWinApp:: applicationwiederherstellungsrückruf](#applicationrecoverycallback).|
|*dwpinginterval*|in Die Zeitspanne, die der Neustart-Manager wartet, bis die Wiederherstellungs Rückruffunktion zurückgegeben wird. Dieser Parameter ist in Millisekunden angegeben.|
|*dwcallbackflags*|in An die Wiederherstellungs Rückruffunktion übergebenen Flags. Für zukünftige Verwendung reserviert.|

### <a name="return-value"></a>Rückgabewert

S_OK, wenn die Methode erfolgreich ist. andernfalls ein Fehlercode.

### <a name="remarks"></a>Hinweise

Wenn Ihre Anwendung die MFC-Standard Implementierung für das automatische Speichern von Dateien verwendet, sollten Sie die einfache Version von `RegisterWithRestartManager`verwenden. Verwenden Sie die komplexe Version von `RegisterWithRestartManager`, wenn Sie das Verhalten der Anwendung für die automatische Speicherung anpassen möchten.

Wenn Sie diese Methode mit einer leeren Zeichenfolge für " *straurestartidentifier*" aufrufen, erstellt `RegisterWithRestartManager` eine eindeutige Bezeichnerzeichenfolge für diese Instanz des Neustart-Managers.

Wenn eine Anwendung unerwartet beendet wird, startet der Neustart-Manager die Anwendung über die Befehlszeile neu und stellt den eindeutigen Neustart Bezeichner als optionales Argument bereit. In diesem Szenario Ruft das Framework `RegisterWithRestartManager` zweimal auf. Der erste-Befehl stammt aus [CWinApp:: InitInstance](#initinstance) mit einer leeren Zeichenfolge für den Zeichen folgen Bezeichner. Anschließend ruft die Methode [CWinApp::P rocess shellcommand](#processshellcommand) `RegisterWithRestartManager` mit dem eindeutigen Neustart Bezeichner auf.

Nachdem Sie eine Anwendung mit dem Neustart-Manager registriert haben, wird die Anwendung vom Neustart-Manager überwacht. Wenn die Anwendung unerwartet beendet wird, ruft der Neustart-Manager die Wiederherstellungs Rückruffunktion während des Vorgangs zum Herunterfahren auf. Der Neustart-Manager wartet das *dwpinginterval* auf eine Antwort von der Wiederherstellungs Rückruffunktion. Wenn die Wiederherstellungs Rückruffunktion nicht innerhalb dieser Zeit antwortet, wird die Anwendung beendet, ohne dass die Wiederherstellungs Rückruffunktion ausgeführt wird.

Standardmäßig werden die dwrestartflags nicht unterstützt, aber für die zukünftige Verwendung bereitgestellt. Die möglichen Werte für *dwrestartflags* lauten wie folgt:

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

##  <a name="reopenpreviousfilesatrestart"></a>CWinApp:: reopenpreviousfilesatrestart

Bestimmt, ob der Neustart-Manager die Dateien erneut öffnet, die geöffnet waren, als die Anwendung unerwartet beendet wurde.

```
virtual BOOL ReopenPreviousFilesAtRestart() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE gibt an, dass der Neustart-Manager die zuvor geöffneten Dateien erneut öffnet. FALSE gibt an, dass der Neustart-Manager nicht.

##  <a name="restartinstance"></a>CWinApp:: restartinstance

Behandelt einen Neustart der Anwendung, der vom Neustart-Manager initiiert wird.

```
virtual BOOL CWinApp::RestartInstance();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Datenwiederherstellungs Handler bereits geöffnete Dokumente öffnet. FALSE, wenn der Datenwiederherstellungs-Handler einen Fehler aufweist oder wenn keine Dokumente bereits geöffnet sind.

### <a name="remarks"></a>Hinweise

Wenn der Neustart-Manager eine Anwendung neu startet, ruft das Framework diese Methode auf. Diese Methode ruft den Datenwiederherstellungs Handler ab und stellt die automatisch gespeicherten Dateien wieder her. Mit dieser Methode wird [cdatarecoveryhandler:: restoreautosaveddocuments](../../mfc/reference/cdatarecoveryhandler-class.md#restoreautosaveddocuments) aufgerufen, um zu bestimmen, ob der Benutzer die automatisch gespeicherten Dateien wiederherstellen möchte.

Diese Methode gibt false zurück, wenn der [cdatarecoveryhandler](../../mfc/reference/cdatarecoveryhandler-class.md) feststellt, dass es keine geöffneten Dokumente gab. Wenn keine geöffneten Dokumente vorhanden sind, wird die Anwendung normalerweise gestartet.

##  <a name="restoreautosavedfilesatrestart"></a>CWinApp:: restoreautosavedfilesatrestart

Bestimmt, ob der Neustart-Manager die automatisch gespeicherten Dateien wiederherstellt, wenn die Anwendung neu gestartet wird.

```
virtual BOOL RestoreAutosavedFilesAtRestart() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE gibt an, dass der Neustart-Manager automatisch gespeicherte Dateien wiederherstellt. FALSE gibt an, dass der Neustart-Manager nicht.

##  <a name="run"></a>CWinApp:: Run

Stellt eine Standard Nachrichten Schleife bereit.

```
virtual int Run();
```

### <a name="return-value"></a>Rückgabewert

Ein **int** -Wert, der von `WinMain`zurückgegeben wird.

### <a name="remarks"></a>Hinweise

`Run` ruft Windows-Nachrichten ab und sendet Sie, bis die Anwendung eine WM_QUIT Meldung empfängt. Wenn die Nachrichten Warteschlange der Anwendung zurzeit keine Nachrichten enthält, ruft `Run` [OnIdle](#onidle) auf, um die Leerlaufzeit Verarbeitung auszuführen. Eingehende Nachrichten werden an die [pretranslatemess Age](#pretranslatemessage) -Member-Funktion für die spezielle Verarbeitung und dann an die Windows-Funktion `TranslateMessage` für die Standardtastatur Übersetzung weitergeleitet. zum Schluss wird die `DispatchMessage` Windows-Funktion aufgerufen.

`Run` wird nur selten überschrieben, Sie können es jedoch außer Kraft setzen, um ein spezielles Verhalten bereitzustellen.

##  <a name="runautomated"></a>CWinApp:: runautomated

Mit dieser Funktion können Sie ermitteln, ob die Option " **/Automation**" oder " **-Automation**" vorhanden ist, die angibt, ob die Serveranwendung von einer Client Anwendung gestartet wurde.

```
BOOL RunAutomated();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Option gefunden wurde. andernfalls 0.

### <a name="remarks"></a>Hinweise

Wenn diese Option vorhanden ist, wird die Option aus der Befehlszeile entfernt. Weitere Informationen zur OLE-Automatisierung finden Sie im Artikel [Automation Servers (Automatisierungsserver](../../mfc/automation-servers.md)).

##  <a name="runembedded"></a>CWinApp:: RunEmbedded

Mit dieser Funktion können Sie ermitteln, ob die Option " **/Embedding**" oder " **-Einbettungs**" vorhanden ist, die angibt, ob die Serveranwendung von einer Client Anwendung gestartet wurde.

```
BOOL RunEmbedded();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Option gefunden wurde. andernfalls 0.

### <a name="remarks"></a>Hinweise

Wenn diese Option vorhanden ist, wird die Option aus der Befehlszeile entfernt. Weitere Informationen zum Einbetten finden Sie im Artikel [Server: Implementieren eines Servers](../../mfc/servers-implementing-a-server.md).

##  <a name="saveallmodified"></a>CWinApp:: saveallmodified

Wird von Framework aufgerufen, um alle Dokumente zu speichern, wenn das Hauptrahmen Fenster der Anwendung geschlossen werden soll, oder durch eine WM_QUERYENDSESSION Meldung.

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>Rückgabewert

Nicht NULL, wenn sicher, dass die Anwendung beendet werden soll. 0, wenn nicht sicher, dass die Anwendung beendet wird.

### <a name="remarks"></a>Hinweise

Die Standard Implementierung dieser Member-Funktion ruft wiederum die [CDocument:: SaveModified](../../mfc/reference/cdocument-class.md#savemodified) -Member-Funktion für alle geänderten Dokumente innerhalb der Anwendung auf.

##  <a name="selectprinter"></a>CWinApp:: selectprinter

Mit dieser Member-Funktion können Sie einen bestimmten Drucker auswählen und den Drucker freigeben, der zuvor im Dialog Feld "Drucken" ausgewählt wurde.

```
void SelectPrinter(
    HANDLE hDevNames,
    HANDLE hDevMode,
    BOOL bFreeOld = TRUE);
```

### <a name="parameters"></a>Parameter

*hDevNames*<br/>
Ein Handle für eine [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)-TRUKTUR, die die Treiber-, Geräte-und ausgabeportnamen eines bestimmten Druckers identifiziert.

*hDevMode*<br/>
Ein Handle für eine [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) -Struktur, die Informationen über die Geräte Initialisierung und die Umgebung eines Druckers angibt.

*bfreold*<br/>
Gibt den zuvor ausgewählten Drucker frei.

### <a name="remarks"></a>Hinweise

Wenn *hDevMode* und *hDevNames* NULL sind, verwendet `SelectPrinter` den aktuellen Standarddrucker.

##  <a name="sethelpmode"></a>CWinApp:: Setup Mode

Legt den Hilfstyp der Anwendung fest.

```
void SetHelpMode(AFX_HELP_TYPE eHelpType);
```

### <a name="parameters"></a>Parameter

*ehelptype*<br/>
Gibt den Typ der zu verwendenden Hilfe an. Weitere Informationen finden Sie unter [CWinApp:: m_eHelpType](#m_ehelptype) .

### <a name="remarks"></a>Hinweise

Legt den Hilfstyp der Anwendung fest.

Um den Hilfstyp Ihrer Anwendung auf HTMLHelp festzulegen, können Sie [enablehtmlhelp](#enablehtmlhelp)aufzurufen. Nachdem Sie `EnableHTMLHelp`aufgerufen haben, muss die Anwendung HTMLHelp als Hilfe Anwendung verwenden. Wenn Sie die Verwendung von WinHelp ändern möchten, können Sie `SetHelpMode` aufzurufen und *ehelptype* auf `afxWinHelp`festlegen.

##  <a name="setregistrykey"></a>CWinApp:: abtregistrykey

Bewirkt, dass Anwendungseinstellungen in der Registrierung anstelle von INI-Dateien gespeichert werden.

```
void SetRegistryKey(LPCTSTR lpszRegistryKey);
void SetRegistryKey(UINT nIDRegistryKey);
```

### <a name="parameters"></a>Parameter

*lpszregistrykey*<br/>
Zeiger auf eine Zeichenfolge, die den Namen des Schlüssels enthält.

*nidregistrykey*<br/>
ID einer Zeichen folgen Ressource, die den Namen des Registrierungsschlüssels enthält.

### <a name="remarks"></a>Hinweise

Diese Funktion legt *m_pszRegistryKey*fest, die dann von den Funktionen `GetProfileInt`, `GetProfileString`, `WriteProfileInt`und `WriteProfileString` Member von `CWinApp`verwendet wird. Wenn diese Funktion aufgerufen wurde, wird die Liste der zuletzt verwendeten Dateien (MRU) ebenfalls in der Registrierung gespeichert. Der Registrierungsschlüssel ist in der Regel der Name eines Unternehmens. Sie wird in einem Schlüssel der folgenden Form gespeichert: HKEY_CURRENT_USER \Software\\< Firmenname\>\\< Anwendungsname\>\\<-Abschnitts Name\>\\<\>Wert Name.

##  <a name="supportsapplicationrecovery"></a>CWinApp:: supportsapplicationrecovery

Bestimmt, ob der Neustart-Manager eine Anwendung wiederherstellt, die unerwartet beendet wurde.

```
virtual BOOL SupportsApplicationRecovery() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE gibt an, dass der Neustart-Manager die Anwendung wiederherstellt. FALSE gibt an, dass der Neustart-Manager nicht.

##  <a name="supportsautosaveatinterval"></a>CWinApp:: supportsauessaveatinterval

Bestimmt, ob der Neustart-Manager geöffnete Dokumente in regelmäßigen Abständen automatisch speichert.

```
virtual BOOL SupportsAutosaveAtInterval() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE gibt an, dass der Neustart-Manager geöffnete Dokumente automatisch speichert; FALSE gibt an, dass der Neustart-Manager nicht.

##  <a name="supportsautosaveatrestart"></a>CWinApp:: supportsaudesaveatrestart

Bestimmt, ob der Neustart-Manager alle geöffneten Dokumente automatisch speichert, wenn die Anwendung neu gestartet wird.

```
virtual BOOL SupportsAutosaveAtRestart() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE gibt an, dass der Neustart-Manager geöffnete Dokumente automatisch speichert, wenn die Anwendung neu gestartet wird. FALSE gibt an, dass der Neustart-Manager nicht.

##  <a name="supportsrestartmanager"></a>CWinApp:: supportsrestartmanager

Bestimmt, ob die Anwendung den Neustart-Manager unterstützt.

```
virtual BOOL SupportsRestartManager() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE gibt an, dass die Anwendung den Neustart-Manager unterstützt. FALSE gibt an, dass die Anwendung dies nicht tut.

##  <a name="unregister"></a>CWinApp:: Unregister

Hebt die Registrierung aller Dateien auf, die vom Anwendungs Objekt registriert wurden.

```
virtual BOOL Unregister();
```

### <a name="return-value"></a>Rückgabewert

Bei Erfolg ein Wert ungleich 0 (null), andernfalls 0 (null).

### <a name="remarks"></a>Hinweise

Die `Unregister` Funktion macht die vom Anwendungs Objekt und der [Register](#register) Funktion ausgeführte Registrierung unerledigt. Normalerweise werden beide Funktionen implizit von MFC aufgerufen und werden daher nicht im Code angezeigt.

Überschreiben Sie diese Funktion, um benutzerdefinierte Registrierungsschritte auszuführen.

##  <a name="unregistershellfiletypes"></a>CWinApp:: unregistershellfiletypes

Mit dieser Member-Funktion können Sie die Registrierung aller Dokumenttypen Ihrer Anwendung beim Windows-Datei-Manager aufheben.

```
void UnregisterShellFileTypes();
```

##  <a name="winhelp"></a>CWinApp:: WinHelp

Diese Member-Funktion aufrufen, um die WinHelp-Anwendung aufzurufen.

```
virtual void WinHelp(
    DWORD_PTR dwData,
    UINT nCmd = HELP_CONTEXT);
```

### <a name="parameters"></a>Parameter

*dwdata*<br/>
Gibt zusätzliche Daten an. Der verwendete Wert hängt vom Wert des *ncmd* -Parameters ab.

*ncmd*<br/>
Gibt den Typ der angeforderten Hilfe an. Eine Liste möglicher Werte und deren Auswirkung auf den *dwdata* -Parameter finden Sie in der Windows-Funktion [WinHelp](/windows/win32/api/winuser/nf-winuser-winhelpw) .

### <a name="remarks"></a>Hinweise

Das Framework ruft diese Funktion auch auf, um die WinHelp-Anwendung aufzurufen.

Das Framework schließt die WinHelp-Anwendung automatisch, wenn die Anwendung beendet wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#53](../../mfc/reference/codesnippet/cpp/cwinapp-class_28.cpp)]

##  <a name="writeprofilebinary"></a>CWinApp:: Beschreib teprofilebinary

Mit dieser Member-Funktion können Sie Binärdaten in den angegebenen Abschnitt der Registrierung der Anwendung oder schreiben. INI-Datei.

```
BOOL WriteProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE pData,
    UINT nBytes);
```

### <a name="parameters"></a>Parameter

*lpszsection*<br/>
Zeigt auf eine auf NULL endende Zeichenfolge, die den Abschnitt mit dem Eintrag angibt. Wenn der Abschnitt nicht vorhanden ist, wird er erstellt. Der Name des Abschnitts ist unabhängig von der Groß-und Kleinschreibung. die Zeichenfolge kann eine beliebige Kombination aus Groß-und Kleinbuchstaben sein.

*lpszentry*<br/>
Verweist auf eine auf NULL endende Zeichenfolge, die den Eintrag enthält, in den der Wert geschrieben werden soll. Wenn der Eintrag nicht im angegebenen Abschnitt vorhanden ist, wird er erstellt.

*pData*<br/>
Zeigt auf die zu schreibenden Daten.

*nBytes*<br/>
Enthält die Anzahl der Bytes, die geschrieben werden sollen.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

In diesem Beispiel wird `CWinApp* pApp = AfxGetApp();` verwendet, um die CWinApp-Klasse zu verwenden, um zu veranschaulichen, wie `WriteProfileBinary` und `GetProfileBinary` von jeder Funktion in einer MFC-Anwendung verwendet werden können.

[!code-cpp[NVC_MFCWindowing#54](../../mfc/reference/codesnippet/cpp/cwinapp-class_29.cpp)]

Ein weiteres Beispiel finden Sie im Beispiel für [CWinApp:: getprofilebinary](#getprofilebinary).

##  <a name="writeprofileint"></a>CWinApp:: Beschreib teprofileint

Mit dieser Member-Funktion können Sie den angegebenen Wert in den angegebenen Abschnitt der Registrierung der Anwendung oder schreiben. INI-Datei.

```
BOOL WriteProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nValue);
```

### <a name="parameters"></a>Parameter

*lpszsection*<br/>
Zeigt auf eine auf NULL endende Zeichenfolge, die den Abschnitt mit dem Eintrag angibt. Wenn der Abschnitt nicht vorhanden ist, wird er erstellt. Der Name des Abschnitts ist unabhängig von der Groß-und Kleinschreibung. die Zeichenfolge kann eine beliebige Kombination aus Groß-und Kleinbuchstaben sein.

*lpszentry*<br/>
Verweist auf eine auf NULL endende Zeichenfolge, die den Eintrag enthält, in den der Wert geschrieben werden soll. Wenn der Eintrag nicht im angegebenen Abschnitt vorhanden ist, wird er erstellt.

*nWert*<br/>
Enthält den zu schreibenden Wert.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

In diesem Beispiel wird `CWinApp* pApp = AfxGetApp();` verwendet, um die CWinApp-Klasse zu verwenden, um zu veranschaulichen, wie `WriteProfileString`, `WriteProfileInt`, `GetProfileString`und `GetProfileInt` von jeder Funktion in einer MFC-Anwendung verwendet werden können.

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

Ein weiteres Beispiel finden Sie im Beispiel für [CWinApp:: GetProfileInt](#getprofileint).

##  <a name="writeprofilestring"></a>CWinApp:: Schreib Profil Zeichenfolge

Mit dieser Member-Funktion können Sie die angegebene Zeichenfolge in den angegebenen Abschnitt der Registrierung der Anwendung oder schreiben. INI-Datei.

```
BOOL WriteProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszValue);
```

### <a name="parameters"></a>Parameter

*lpszsection*<br/>
Zeigt auf eine auf NULL endende Zeichenfolge, die den Abschnitt mit dem Eintrag angibt. Wenn der Abschnitt nicht vorhanden ist, wird er erstellt. Der Name des Abschnitts ist unabhängig von der Groß-und Kleinschreibung. die Zeichenfolge kann eine beliebige Kombination aus Groß-und Kleinbuchstaben sein.

*lpszentry*<br/>
Verweist auf eine auf NULL endende Zeichenfolge, die den Eintrag enthält, in den der Wert geschrieben werden soll. Wenn der Eintrag nicht im angegebenen Abschnitt vorhanden ist, wird er erstellt. Wenn dieser Parameter NULL ist, wird der von *lpszsection* angegebene Abschnitt gelöscht.

*lpszvalue*<br/>
Zeigt auf die zu schreibende Zeichenfolge. Wenn dieser Parameter NULL ist, wird der durch den *lpszentry* -Parameter angegebene Eintrag gelöscht.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

Ein weiteres Beispiel finden Sie im Beispiel für [CWinApp:: GetProfileInt](#getprofileint).

##  <a name="setappid"></a>CWinApp:: "abtappid"

Legt die Anwendungs Benutzer Modell-ID für die Anwendung explizit fest. Diese Methode sollte aufgerufen werden, bevor dem Benutzer eine Benutzeroberfläche angezeigt wird (die beste Stelle ist der Anwendungskonstruktor).

```
void SetAppID(LPCTSTR lpcszAppID);
```

### <a name="parameters"></a>Parameter

*lpcszappid*<br/>
Gibt die App-Benutzer Modell-ID an.

### <a name="remarks"></a>Hinweise

## <a name="see-also"></a>Siehe auch

[CWinThread-Klasse](../../mfc/reference/cwinthread-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Vorgehensweise: Hinzufügen von Unterstützung für den Neustart-Manager](../../mfc/how-to-add-restart-manager-support.md)
