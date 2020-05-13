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
ms.openlocfilehash: 4bb1ade4182424cbdcbf0d7ba69af88bbb88abe6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750674"
---
# <a name="cwinapp-class"></a>CWinApp-Klasse

Die Basisklasse, von der ein Windows-Anwendungsobjekt abgeleitet wird.

## <a name="syntax"></a>Syntax

```
class CWinApp : public CWinThread
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWinApp::CWinApp](#cwinapp)|Erstellt ein `CWinApp`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWinApp::AddDocTemplate](#adddoctemplate)|Fügt der Liste der verfügbaren Dokumentvorlagen der Anwendung eine Dokumentvorlage hinzu.|
|[CWinApp::AddToRecentFileList](#addtorecentfilelist)|Fügt der zuletzt verwendeten Dateiliste (MRU) einen Dateinamen hinzu.|
|[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)|Wird vom Framework aufgerufen, wenn die Anwendung unerwartet beendet wird.|
|[CWinApp::AlleDokumente schließen](#closealldocuments)|Schließt alle geöffneten Dokumente.|
|[CWinApp::CreatePrinterDC](#createprinterdc)|Erstellt einen Druckergerätekontext.|
|[CWinApp::DelRegTree](#delregtree)|Löscht einen angegebenen Schlüssel und alle zugehörigen Unterschlüssel.|
|[CWinApp::DoMessageBox](#domessagebox)|Implementiert [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) für die Anwendung.|
|[CWinApp::DoWaitCursor](#dowaitcursor)|Schaltet den Wartecursor ein und aus.|
|[CWinApp::EnableD2DSupport](#enabled2dsupport)|Ermöglicht die D2D-Unterstützung der Anwendung. Rufen Sie diese Methode vor der Initialisierung des Hauptfensters auf.|
|[CWinApp::EnableHtmlHelp](#enablehtmlhelp)|Implementiert HTMLHelp für die Anwendung anstelle von WinHelp.|
|[CWinApp::EnableTaskbarInteraktion](#enabletaskbarinteraction)|Aktiviert die Taskleisteninteraktion.|
|[CWinApp::ExitInstance](#exitinstance)|Überschreiben, um zu bereinigen, wenn ihre Anwendung beendet wird.|
|[CWinApp::GetApplicationRecoveryParameter](#getapplicationrecoveryparameter)|Ruft den Eingabeparameter für die Anwendungswiederherstellungsmethode ab.|
|[CWinApp::GetApplicationRecoveryPingInterval](#getapplicationrecoverypinginterval)|Gibt die Zeitspanne zurück, die der Neustart-Manager auf die Rückgabe der Wiederherstellungsrückruffunktion wartet.|
|[CWinApp::GetApplicationRestartFlags](#getapplicationrestartflags)|Gibt die Flags für den Neustart-Manager zurück.|
|[CWinApp::GetAppRegistryKey](#getappregistrykey)|Gibt den\\Schlüssel für HKEY_CURRENT_USER "Software" zurück.|
|[CWinApp::GetDataRecoveryHandler](#getdatarecoveryhandler)|Ruft den Datenwiederherstellungshandler für diese Instanz der Anwendung ab.|
|[CWinApp::GetFirstDocTemplatePosition](#getfirstdoctemplateposition)|Ruft die Position der ersten Dokumentvorlage ab.|
|[CWinApp::GetHelpMode](#gethelpmode)|Ruft den Von der Anwendung verwendeten Hilfetyp ab.|
|[CWinApp::GetNextDocTemplate](#getnextdoctemplate)|Ruft die Position einer Dokumentvorlage ab. Kann rekursiv verwendet werden.|
|[CWinApp::GetPrinterDeviceDefaults](#getprinterdevicedefaults)|Ruft die Standardeinstellungen des Druckergeräts ab.|
|[CWinApp::GetProfileBinary](#getprofilebinary)|Ruft Binärdaten aus einem Eintrag in der Anwendung ab. INI-Datei.|
|[CWinApp::GetProfileInt](#getprofileint)|Ruft eine ganze Zahl aus einem Eintrag in der Anwendung ab. INI-Datei.|
|[CWinApp::GetProfileString](#getprofilestring)|Ruft eine Zeichenfolge aus einem Eintrag in der Anwendung ab. INI-Datei.|
|[CWinApp::GetSectionKey](#getsectionkey)|Gibt den\\Schlüssel für HKEY_CURRENT_USER "Software" zurück.|
|[CWinApp::HideApplication](#hideapplication)|Blendet die Anwendung aus, bevor alle Dokumente geschlossen werden.|
|[CWinApp::HtmlHilfe](#htmlhelp)|Ruft `HTMLHelp` die Windows-Funktion auf.|
|[CWinApp::InitInstance](#initinstance)|Überschreiben Sie, um die Windows-Instanzinitialisierung durchzuführen, z. B. das Erstellen von Fensterobjekten.|
|[CWinApp::IsTaskbarInteractionAktiviert](#istaskbarinteractionenabled)|Gibt an, ob die Windows 7-Taskleisteninteraktion aktiviert ist.|
|[CWinApp::LoadCursor](#loadcursor)|Lädt eine Cursorressource.|
|[CWinApp::LoadIcon](#loadicon)|Lädt eine Symbolressource.|
|[CWinApp::LoadOEMCursor](#loadoemcursor)|Lädt einen vordefinierten Windows OEM-Cursor, den die **OCR_** konstanten in WINDOWS angeben. H.|
|[CWinApp::LoadOEMIcon](#loadoemicon)|Lädt ein vordefiniertes Windows OEM-Symbol, das die **OIC_** konstanten in WINDOWS angeben. H.|
|[CWinApp::LoadStandardCursor](#loadstandardcursor)|Lädt einen vordefinierten Windows-Cursor, den die **IDC_** konstanten in WINDOWS angeben. H.|
|[CWinApp::LoadStandardIcon](#loadstandardicon)|Lädt ein vordefiniertes Windows-Symbol, das die **IDI_** konstanten in WINDOWS angeben. H.|
|[CWinApp::OnDDECommand](#onddecommand)|Wird vom Framework als Reaktion auf einen DDE-Ausführungsbefehl (Dynamic Data Exchange) aufgerufen.|
|[CwinApp::OnIdle](#onidle)|Überschreiben, um anwendungsspezifische Leerlaufverarbeitung durchzuführen.|
|[CWinApp::DocumentFile öffnen](#opendocumentfile)|Wird vom Framework aufgerufen, um ein Dokument aus einer Datei zu öffnen.|
|[CWinApp::ParseCommandLine](#parsecommandline)|Analysiert einzelne Parameter und Flags in der Befehlszeile.|
|[CWinApp::PReTranslateMessage](#pretranslatemessage)|Filtert Nachrichten, bevor sie an die Windows-Funktionen [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) und [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)gesendet werden.|
|[CWinApp::ProcessMessageFilter](#processmessagefilter)|Fängt bestimmte Nachrichten ab, bevor sie die Anwendung erreichen.|
|[CWinApp::ProcessShellCommand](#processshellcommand)|Behandelt Befehlszeilenargumente und Flags.|
|[CWinApp::ProcessWndProcAusnahme](#processwndprocexception)|Fängt alle nicht behandelten Ausnahmen ab, die von den Nachrichten- und Befehlshandlern der Anwendung ausgelöst werden.|
|[CWinApp::Registrieren](#register)|Führt eine benutzerdefinierte Registrierung durch.|
|[CWinApp::RegisterWithRestartManager](#registerwithrestartmanager)|Registriert die Anwendung beim Neustart-Manager.|
|[CWinApp::PreviousFilesAtRestart neu öffnen](#reopenpreviousfilesatrestart)|Legt fest, ob der Neustart-Manager die Dateien erneut öffnet, die beim unerwarteten Beenden der Anwendung geöffnet wurden.|
|[CWinApp::RestartInstance](#restartinstance)|Behandelt einen vom Neustart-Manager initiierten Anwendungsneustart.|
|[CWinApp::RestoreAutosavedFilesAtRestart](#restoreautosavedfilesatrestart)|Legt fest, ob der Neustart-Manager die automatisch gespeicherten Dateien wiederherstellt, wenn die Anwendung neu gestartet wird.|
|[CWinApp::Ausführen](#run)|Führt die Standardnachrichtenschleife aus. Überschreiben, um die Nachrichtenschleife anzupassen.|
|[CWinApp::RunAutomatisiert](#runautomated)|Testet die Befehlszeile der Anwendung für die Option **/Automation.** Veraltet. Verwenden Sie stattdessen den Wert in [CCommandLineInfo::m_bRunAutomated](../../mfc/reference/ccommandlineinfo-class.md#m_brunautomated) nach dem Aufruf von [ParseCommandLine](#parsecommandline).|
|[CWinApp::RunEmbedded](#runembedded)|Testet die Befehlszeile der Anwendung für die Option **/Embedding.** Veraltet. Verwenden Sie stattdessen den Wert in [CCommandLineInfo::m_bRunEmbedded](../../mfc/reference/ccommandlineinfo-class.md#m_brunembedded) nach dem Aufruf von [ParseCommandLine](#parsecommandline).|
|[CWinApp::SaveAllModified](#saveallmodified)|Fordert den Benutzer auf, alle geänderten Dokumente zu speichern.|
|[CWinApp::SelectPrinter](#selectprinter)|Wählt einen Drucker aus, der zuvor von einem Benutzer über ein Druckdialogfeld angezeigt wurde.|
|[CWinApp::SetHelpMode](#sethelpmode)|Legt den Von der Anwendung verwendeten Hilfetyp fest und initialisiert diesen.|
|[CWinApp::UnterstütztApplicationRecovery](#supportsapplicationrecovery)|Bestimmt, ob der Neustart-Manager eine Anwendung wiederherstellt, die unerwartet beendet wurde.|
|[CWinApp::UnterstütztAutosaveAtInterval](#supportsautosaveatinterval)|Bestimmt, ob der Neustart-Manager geöffnete Dokumente in einem regelmäßigen Intervall automatisch speichert.|
|[CWinApp::UnterstütztAutosaveAtRestart](#supportsautosaveatrestart)|Bestimmt, ob der Neustart-Manager alle geöffneten Dokumente automatisch speichert, wenn die Anwendung neu gestartet wird.|
|[CWinApp::UnterstütztRestartManager](#supportsrestartmanager)|Bestimmt, ob die Anwendung den Neustart-Manager unterstützt.|
|[CWinApp::Registrieren](#unregister)|Entregistriert alles, was bekanntermaßen `CWinApp` vom Objekt registriert wird.|
|[CWinApp::WinHelp](#winhelp)|Ruft `WinHelp` die Windows-Funktion auf.|
|[CWinApp::WriteProfileBinary](#writeprofilebinary)|Schreibt Binärdaten in einen Eintrag in der Anwendung . INI-Datei.|
|[CWinApp::WriteProfileInt](#writeprofileint)|Schreibt eine ganze Zahl in einen Eintrag in der Anwendung . INI-Datei.|
|[CWinApp::WriteProfileString](#writeprofilestring)|Schreibt eine Zeichenfolge in einen Eintrag in der Anwendung . INI-Datei.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWinApp::EnableShellOpen](#enableshellopen)|Ermöglicht dem Benutzer das Öffnen von Datendateien aus dem Windows-Datei-Manager.|
|[CWinApp::LoadStdProfileEinstellungen](#loadstdprofilesettings)|Lädt Standard . INI-Dateieinstellungen und aktiviert die MRU-Dateilistenfunktion.|
|[CWinApp::OnContextHelp](#oncontexthelp)|Behandelt die SHIFT+F1-Hilfe in der Anwendung.|
|[CWinApp::OnFileNeu](#onfilenew)|Implementiert den Befehl ID_FILE_NEW.|
|[CWinApp::OnFileÖffnen](#onfileopen)|Implementiert den Befehl ID_FILE_OPEN.|
|[CWinApp::OnFilePrintSetup](#onfileprintsetup)|Implementiert den ID_FILE_PRINT_SETUP-Befehl.|
|[CWinApp::Hilfe](#onhelp)|Verarbeitet die F1-Hilfe in der Anwendung (unter Verwendung des aktuellen Kontexts).|
|[CWinApp::OnHelpFinder](#onhelpfinder)|Behandelt die ID_HELP_FINDER- und ID_DEFAULT_HELP-Befehle.|
|[CWinApp::OnHelpIndex](#onhelpindex)|Behandelt den Befehl ID_HELP_INDEX und stellt ein Standardhilfethema bereit.|
|[CWinApp::OnHelpUsing](#onhelpusing)|Behandelt den Befehl ID_HELP_USING.|
|[CWinApp::RegisterShellFileTypes](#registershellfiletypes)|Registriert alle Dokumenttypen der Anwendung im Windows-Datei-Manager.|
|[CWinApp::SetAppID](#setappid)|Legt explizit die Anwendungsbenutzermodell-ID für die Anwendung fest. Diese Methode sollte aufgerufen werden, bevor dem Benutzer eine Benutzeroberfläche angezeigt wird (der beste Ort ist der Anwendungskonstruktor).|
|[CWinApp::SetRegistryKey](#setregistrykey)|Bewirkt, dass Anwendungseinstellungen in der Registrierung anstelle von gespeichert werden. INI-Dateien.|
|[CWinApp::ShellFileTypes aufheben](#unregistershellfiletypes)|Die Registrierung aller Dokumenttypen der Anwendung wird beim Windows-Datei-Manager aufheben.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWinApp::m_bHelpMode](#m_bhelpmode)|Gibt an, ob sich der Benutzer im Hilfekontextmodus befindet (in der Regel mit UMSCHALT+F1 aufgerufen).|
|[CWinApp::m_eHelpType](#m_ehelptype)|Gibt den Hilfetyp an, der von der Anwendung verwendet wird.|
|[CWinApp::m_hInstance](#m_hinstance)|Identifiziert die aktuelle Instanz der Anwendung.|
|[CWinApp::m_lpCmdLine](#m_lpcmdline)|Zeigt auf eine null-terminierte Zeichenfolge, die die Befehlszeile für die Anwendung angibt.|
|[CWinApp::m_nCmdShow](#m_ncmdshow)|Gibt an, wie das Fenster anfänglich angezeigt werden soll.|
|[CWinApp::m_pActiveWnd](#m_pactivewnd)|Zeigen Sie mit dem Zeiger auf das Hauptfenster der Containeranwendung, wenn ein OLE-Server aktiv ist.|
|[CWinApp::m_pszAppID](#m_pszappid)|Anwendungsbenutzermodell-ID.|
|[CWinApp::m_pszAppName](#m_pszappname)|Gibt den Namen der Anwendung an.|
|[CWinApp::m_pszExeName](#m_pszexename)|Der Modulname der Anwendung.|
|[CWinApp::m_pszHelpFilePath](#m_pszhelpfilepath)|Der Pfad zur Hilfedatei der Anwendung.|
|[CWinApp::m_pszProfileName](#m_pszprofilename)|Die Anwendung . INI-Dateiname.|
|[CWinApp::m_pszRegistryKey](#m_pszregistrykey)|Wird verwendet, um den vollständigen Registrierungsschlüssel zum Speichern von Anwendungsprofileinstellungen zu bestimmen.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWinApp::m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags)|Flags, die das Verhalten des Neustart-Managers bestimmen.|
|[CWinApp::m_nAutosaveInterval](#m_nautosaveinterval)|Die Zeitdauer in Millisekunden zwischen Autosaves.|
|[CWinApp::m_pDataRecoveryHandler](#m_pdatarecoveryhandler)|Zeiger auf den Datenwiederherstellungshandler für die Anwendung.|

## <a name="remarks"></a>Bemerkungen

Ein Anwendungsobjekt stellt Memberfunktionen zum Initialisieren ihrer Anwendung (und jeder Instanz) und zum Ausführen der Anwendung bereit.

Jede Anwendung, die die Microsoft Foundation-Klassen `CWinApp`verwendet, kann nur ein Objekt enthalten, das von abgeleitet wurde. Dieses Objekt wird erstellt, wenn andere globale C++-Objekte `WinMain` erstellt werden, und ist bereits verfügbar, wenn Windows die Funktion aufruft, die von der Microsoft Foundation-Klassenbibliothek bereitgestellt wird. Deklarieren `CWinApp` Sie Ihr abgeleitetes Objekt auf globaler Ebene.

Wenn Sie eine Anwendungsklasse `CWinApp`von ableiten, überschreiben Sie die [InitInstance-Memberfunktion,](#initinstance) um das Hauptfensterobjekt Ihrer Anwendung zu erstellen.

Zusätzlich zu `CWinApp` den Memberfunktionen bietet die Microsoft Foundation-Klassenbibliothek `CWinApp` die folgenden globalen Funktionen für den Zugriff auf Ihr Objekt und andere globale Informationen:

- [AfxGetApp](application-information-and-management.md#afxgetapp) Ruft einen Zeiger auf `CWinApp` das Objekt ab.

- [AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle) Ruft ein Handle für die aktuelle Anwendungsinstanz ab.

- [AfxGetResourceHandle](application-information-and-management.md#afxgetresourcehandle) Ruft ein Handle für die Ressourcen der Anwendung ab.

- [AfxGetAppName](application-information-and-management.md#afxgetappname) Ruft einen Zeiger auf eine Zeichenfolge ab, die den Namen der Anwendung enthält. Wenn Sie über einen Zeiger auf `CWinApp` das `m_pszExeName` Objekt verfügen, können Sie den Namen der Anwendung abrufen.

Weitere Informationen zur `CWinApp` Klasse finden Sie unter [CWinApp: The Application Class:](../../mfc/cwinapp-the-application-class.md)

- `CWinApp`-abgeleiteter Code, der vom Anwendungs-Assistenten geschrieben wurde.

- `CWinApp`Rolle in der Ausführungssequenz Ihrer Anwendung.

- `CWinApp`Standard-Memberfunktionsimplementierungen.

- `CWinApp`Schlüsselüberschreibbare.

Das `m_hPrevInstance` Datenelement ist nicht mehr vorhanden. Um zu bestimmen, ob eine andere Instanz der Anwendung ausgeführt wird, verwenden Sie einen benannten Mutex. Wenn das Öffnen des Mutex fehlschlägt, werden keine anderen Instanzen der Anwendung ausgeführt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWinThread](../../mfc/reference/cwinthread-class.md)

`CWinApp`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="cwinappadddoctemplate"></a><a name="adddoctemplate"></a>CWinApp::AddDocTemplate

Rufen Sie diese Memberfunktion auf, um der Liste der verfügbaren Dokumentvorlagen, die von der Anwendung verwaltet werden, eine Dokumentvorlage hinzuzufügen.

```cpp
void AddDocTemplate(CDocTemplate* pTemplate);
```

### <a name="parameters"></a>Parameter

*pTemplate*<br/>
Ein Zeiger auf `CDocTemplate` den hinzuzufügenden.

### <a name="remarks"></a>Bemerkungen

Sie sollten einer Anwendung alle Dokumentvorlagen hinzufügen, bevor Sie [RegisterShellFileTypes](#registershellfiletypes)aufrufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#35](../../mfc/reference/codesnippet/cpp/cwinapp-class_1.cpp)]

## <a name="cwinappaddtorecentfilelist"></a><a name="addtorecentfilelist"></a>CWinApp::AddToRecentFileList

Rufen Sie diese Memberfunktion auf, um *der MRU-Dateiliste lpszPathName* hinzuzufügen.

```
virtual void AddToRecentFileList(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parameter

*lpszPathName*<br/>
Der Pfad der Datei.

### <a name="remarks"></a>Bemerkungen

Sie sollten die [LoadStdProfileSettings-Memberfunktion](#loadstdprofilesettings) aufrufen, um die aktuelle MRU-Dateiliste zu laden, bevor Sie diese Memberfunktion verwenden.

Das Framework ruft diese Memberfunktion auf, wenn es eine Datei öffnet oder den Befehl Speichern unter ausführt, um eine Datei mit einem neuen Namen zu speichern.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#36](../../mfc/reference/codesnippet/cpp/cwinapp-class_2.cpp)]

## <a name="cwinappapplicationrecoverycallback"></a><a name="applicationrecoverycallback"></a>CWinApp::ApplicationRecoveryCallback

Wird vom Framework aufgerufen, wenn die Anwendung unerwartet beendet wird.

```
virtual DWORD ApplicationRecoveryCallback(LPVOID lpvParam);
```

### <a name="parameters"></a>Parameter

*lpvParam*<br/>
[in] Reserviert für zukünftige Verwendung.

### <a name="return-value"></a>Rückgabewert

0, wenn diese Methode erfolgreich ist; ungleich Null, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Wenn Ihre Anwendung den Neustart-Manager unterstützt, ruft das Framework diese Funktion auf, wenn die Anwendung unerwartet beendet wird.

Die Standardimplementierung `ApplicationRecoveryCallback` von `CDataRecoveryHandler` verwendet die, um die Liste der aktuell geöffneten Dokumente in der Registrierung zu speichern. Diese Methode speichert keine Dateien automatisch.

Um das Verhalten anzupassen, überschreiben Sie diese Funktion in einer abgeleiteten [CWinApp-Klasse](../../mfc/reference/cwinapp-class.md) oder übergeben Sie Ihre eigene Anwendungswiederherstellungsmethode als Parameter an [CWinApp::RegisterWithRestartManager](#registerwithrestartmanager).

## <a name="cwinappclosealldocuments"></a><a name="closealldocuments"></a>CWinApp::AlleDokumente schließen

Rufen Sie diese Memberfunktion auf, um alle geöffneten Dokumente vor dem Beenden zu schließen.

```cpp
void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>Parameter

*bEndSession*<br/>
Gibt an, ob die Windows-Sitzung beendet wird. Es ist TRUE, wenn die Sitzung beendet wird; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Rufen Sie [HideApplication](#hideapplication) auf, bevor Sie `CloseAllDocuments`.

## <a name="cwinappcreateprinterdc"></a><a name="createprinterdc"></a>CWinApp::CreatePrinterDC

Rufen Sie diese Memberfunktion auf, um einen Druckergerätekontext (DC) aus dem ausgewählten Drucker zu erstellen.

```
BOOL CreatePrinterDC(CDC& dc);
```

### <a name="parameters"></a>Parameter

*Dc*<br/>
Ein Verweis auf einen Druckergerätekontext.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Druckergerätekontext erfolgreich erstellt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

`CreatePrinterDC`initialisiert den Gerätekontext, den Sie als Verweis übergeben, sodass Sie ihn zum Drucken verwenden können.

Wenn die Funktion erfolgreich ist, müssen Sie den Gerätekontext zerstören, wenn Sie den Druckvorgang abgeschlossen haben. Sie können den Destruktor des [CDC-Objekts](../../mfc/reference/cdc-class.md) dies tun lassen, oder Sie können dies explizit tun, indem Sie [CDC::DeleteDC](../../mfc/reference/cdc-class.md#deletedc)aufrufen.

## <a name="cwinappcwinapp"></a><a name="cwinapp"></a>CWinApp::CWinApp

Erstellt ein `CWinApp` Objekt und übergibt *lpszAppName,* das als Anwendungsname gespeichert werden soll.

```
CWinApp(LPCTSTR lpszAppName = NULL);
```

### <a name="parameters"></a>Parameter

*lpszAppName*<br/>
Eine null-terminierte Zeichenfolge, die den von Windows verwendeten Anwendungsnamen enthält. Wenn dieses Argument nicht angegeben `CWinApp` wird oder NULL ist, wird die Ressourcenzeichenfolge AFX_IDS_APP_TITLE oder der Dateiname der ausführbaren Datei verwendet.

### <a name="remarks"></a>Bemerkungen

Sie sollten ein globales `CWinApp`Objekt Ihrer -derived-Klasse erstellen. Sie können nur `CWinApp` ein Objekt in Ihrer Anwendung haben. Der Konstruktor speichert einen `CWinApp` Zeiger auf `WinMain` das Objekt, sodass die Memberfunktionen des Objekts zum Initialisieren und Ausführen der Anwendung aufrufen können.

## <a name="cwinappdelregtree"></a><a name="delregtree"></a>CWinApp::DelRegTree

Löscht einen bestimmten Registrierungsschlüssel und alle zugehörigen Unterschlüssel.

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

*hParentKey*<br/>
Behandeln Sie einen Registrierungsschlüssel.

*strKeyName*<br/>
Der Name des zu löschenden Registrierungsschlüssels.

*Ptm*<br/>
Zeiger auf das CAtlTransactionManager-Objekt.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, wird der Rückgabewert ERROR_SUCCESS. Wenn die Funktion fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich Null, der in Winerror.h definiert ist.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um den angegebenen Schlüssel und seine Unterschlüssel zu löschen.

## <a name="cwinappdomessagebox"></a><a name="domessagebox"></a>CWinApp::DoMessageBox

Das Framework ruft diese Memberfunktion auf, um ein Meldungsfeld für die globale Funktion [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)zu implementieren.

```
virtual int DoMessageBox(
    LPCTSTR lpszPrompt,
    UINT nType,
    UINT nIDPrompt);
```

### <a name="parameters"></a>Parameter

*lpszPrompt*<br/>
Adresse des Textes im Meldungsfeld.

*nType*<br/>
Der [Meldungsfeldstil](../../mfc/reference/styles-used-by-mfc.md#message-box-styles).

*nIDPrompt*<br/>
Ein Index für eine Hilfekontextzeichenfolge.

### <a name="return-value"></a>Rückgabewert

Gibt dieselben Werte `AfxMessageBox`wie zurück.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Memberfunktion nicht auf, um ein Meldungsfeld zu öffnen. verwenden. `AfxMessageBox`

Überschreiben Sie diese Memberfunktion, um `AfxMessageBox` die anwendungsweite Verarbeitung von Aufrufen anzupassen.

## <a name="cwinappdowaitcursor"></a><a name="dowaitcursor"></a>CWinApp::DoWaitCursor

Diese Memberfunktion wird vom Framework aufgerufen, um [CWaitCursor](../../mfc/reference/cwaitcursor-class.md), [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)und [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)zu implementieren.

```
virtual void DoWaitCursor(int nCode);
```

### <a name="parameters"></a>Parameter

*nCode*<br/>
Wenn dieser Parameter 1 ist, wird ein Wartecursor angezeigt. Wenn 0, wird der Wartecursor wiederhergestellt, ohne die Referenzanzahl zu erhöhen. Wenn -1, endet der Wartecursor.

### <a name="remarks"></a>Bemerkungen

Der Standard implementiert einen Sanduhrcursor. `DoWaitCursor`behält eine Referenzanzahl bei. Wenn positiv, wird der Sanduhrcursor angezeigt.

Obwohl Sie normalerweise `DoWaitCursor` nicht direkt aufrufen würden, können Sie diese Memberfunktion überschreiben, um den Wartecursor zu ändern oder eine zusätzliche Verarbeitung vorzunehmen, während der Wartecursor angezeigt wird.

Verwenden Sie für `CWaitCursor`eine einfachere und optimierte Methode zum Implementieren eines Wartecursors .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#37](../../mfc/reference/codesnippet/cpp/cwinapp-class_3.cpp)]

## <a name="cwinappenabled2dsupport"></a><a name="enabled2dsupport"></a>CWinApp::EnableD2DSupport

Visual Studio 2010 SP1 wird benötigt.

Ermöglicht die D2D-Unterstützung der Anwendung. Rufen Sie diese Methode vor der Initialisierung des Hauptfensters auf.

```
BOOL EnableD2DSupport(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>Parameter

*d2dFactoryType*<br/>
Das Threadingmodell der D2D-Fabrik und die ressourcen, die sie erstellt.

*writeFactoryType*<br/>
Ein Wert, der angibt, ob das Write Factory-Objekt freigegeben oder isoliert wird

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn die D2D-Unterstützung aktiviert war, FALSE - andernfalls

## <a name="cwinappenablehtmlhelp"></a><a name="enablehtmlhelp"></a>CWinApp::EnableHtmlHelp

Rufen Sie diese Memberfunktion innerhalb `CWinApp`des Konstruktors Ihrer -derived-Klasse auf, um HTMLHelp für die Hilfe Ihrer Anwendung zu verwenden.

```cpp
void EnableHtmlHelp();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cwinappenableshellopen"></a><a name="enableshellopen"></a>CWinApp::EnableShellOpen

Rufen Sie diese Funktion `InitInstance` auf, in der Regel über Ihre Außerkraftsetzung, damit die Benutzer Ihrer Anwendung Datendateien öffnen können, wenn sie im Windows-Datei-Manager auf die Dateien doppelklicken.

```cpp
void EnableShellOpen();
```

### <a name="remarks"></a>Bemerkungen

Rufen `RegisterShellFileTypes` Sie die Memberfunktion in Verbindung mit dieser Funktion auf, oder stellen Sie eine zur Verfügung. REG-Datei mit Ihrer Anwendung zur manuellen Registrierung von Dokumententypen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#38](../../mfc/reference/codesnippet/cpp/cwinapp-class_4.cpp)]

## <a name="cwinappenabletaskbarinteraction"></a><a name="enabletaskbarinteraction"></a>CWinApp::EnableTaskbarInteraktion

Aktiviert die Taskleisteninteraktion.

```
BOOL EnableTaskbarInteraction(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
Gibt an, ob die Interaktion mit der Windows 7-Taskleiste aktiviert (TRUE) oder (FALSE) aktiviert werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn die Taskleisteninteraktion aktiviert oder deaktiviert werden kann.

### <a name="remarks"></a>Bemerkungen

Diese Methode muss vor der Erstellung des Hauptfensters aufgerufen werden, andernfalls wird FALSE bestätigt und zurückgegeben.

## <a name="cwinappexitinstance"></a><a name="exitinstance"></a>CWinApp::ExitInstance

Wird vom Framework innerhalb `Run` der Memberfunktion aufgerufen, um diese Instanz der Anwendung zu beenden.

```
virtual int ExitInstance();
```

### <a name="return-value"></a>Rückgabewert

Der Exit-Code der Anwendung; 0 gibt keine Fehler an, und Werte größer als 0 weisen auf einen Fehler hin. Dieser Wert wird als Rückgabewert von `WinMain`verwendet.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Memberfunktion nicht `Run` von überall als innerhalb der Memberfunktion auf.

Die Standardimplementierung dieser Funktion schreibt Frameworkoptionen in die Anwendung . INI-Datei. Überschreiben Sie diese Funktion, um zu bereinigen, wenn die Anwendung beendet wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#39](../../mfc/reference/codesnippet/cpp/cwinapp-class_5.cpp)]

## <a name="cwinappgetapplicationrecoveryparameter"></a><a name="getapplicationrecoveryparameter"></a>CWinApp::GetApplicationRecoveryParameter

Ruft den Eingabeparameter für die Anwendungswiederherstellungsmethode ab.

```
virtual LPVOID GetApplicationRecoveryParameter();
```

### <a name="return-value"></a>Rückgabewert

Der Standardeingabeparameter für die Anwendungswiederherstellungsmethode.

### <a name="remarks"></a>Bemerkungen

Das Standardverhalten dieser Funktion gibt NULL zurück.

Weitere Informationen finden Sie unter [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).

## <a name="cwinappgetapplicationrecoverypinginterval"></a><a name="getapplicationrecoverypinginterval"></a>CWinApp::GetApplicationRecoveryPingInterval

Gibt die Zeitspanne zurück, die der Neustart-Manager auf die Rückgabe der Wiederherstellungsrückruffunktion wartet.

```
virtual DWORD GetApplicationRecoveryPingInterval();
```

### <a name="return-value"></a>Rückgabewert

Die Zeitdauer in Millisekunden.

### <a name="remarks"></a>Bemerkungen

Wenn eine Anwendung, die beim Neustart-Manager registriert ist, unerwartet beendet wird, versucht die Anwendung, geöffnete Dokumente zu speichern, und ruft die Wiederherstellungsrückruffunktion auf. Die standardmäßige Wiederherstellungsrückruffunktion ist [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).

Die Zeitspanne, die das Framework auf die Rückgabe der Wiederherstellungsrückruffunktion wartet, ist das Ping-Intervall. Sie können das Ping-Intervall `CWinApp::GetApplicationRecoveryPingInterval` anpassen, indem Sie `RegisterWithRestartManager`es überschreiben oder einen benutzerdefinierten Wert für bereitstellen.

## <a name="cwinappgetapplicationrestartflags"></a><a name="getapplicationrestartflags"></a>CWinApp::GetApplicationRestartFlags

Gibt die Flags für den Neustart-Manager zurück.

```
virtual DWORD GetApplicationRestartFlags();
```

### <a name="return-value"></a>Rückgabewert

Die Flags für den Neustart-Manager. Die Standardimplementierung gibt 0 zurück.

### <a name="remarks"></a>Bemerkungen

Die Flags für den Neustart-Manager haben keine Auswirkungen auf die Standardimplementierung. Sie werden für die zukünftige Verwendung bereitgestellt.

Sie legen die Flags fest, wenn Sie die Anwendung beim Neustart-Manager registrieren, indem Sie [CWinApp::RegisterWithRestartManager](#registerwithrestartmanager)verwenden.

Die möglichen Werte für die Neustart-Manager-Flags lauten wie folgt:

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

## <a name="cwinappgetappregistrykey"></a><a name="getappregistrykey"></a>CWinApp::GetAppRegistryKey

Gibt den Schlüssel\\für HKEY_CURRENT_USER "Software" zurück.

```
HKEY GetAppRegistryKey(CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parameter

*Ptm*<br/>
Zeiger auf `CAtlTransactionManager` ein Objekt.

### <a name="return-value"></a>Rückgabewert

Anwendungsschlüssel, wenn die Funktion erfolgreich ist; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

## <a name="cwinappgetdatarecoveryhandler"></a><a name="getdatarecoveryhandler"></a>CWinApp::GetDataRecoveryHandler

Ruft den Datenwiederherstellungshandler für diese Instanz der Anwendung ab.

```
virtual CDataRecoveryHandler *GetDataRecoveryHandler();
```

### <a name="return-value"></a>Rückgabewert

Der Datenwiederherstellungshandler für diese Instanz der Anwendung.

### <a name="remarks"></a>Bemerkungen

Jede Anwendung, die den Neustart-Manager verwendet, muss über eine Instanz der [CDataRecoveryHandler-Klasse](../../mfc/reference/cdatarecoveryhandler-class.md)verfügen. Diese Klasse ist für die Überwachung geöffneter Dokumente und das automatische Speichern von Dateien zuständig. Das Verhalten `CDataRecoveryHandler` des hängt von der Konfiguration des Neustart-Managers ab. Weitere Informationen finden Sie unter [CDataRecoveryHandler-Klasse](../../mfc/reference/cdatarecoveryhandler-class.md).

Diese Methode gibt NULL für Betriebssysteme zurück, die vor Windows Vista stehen. Der Neustart-Manager wird auf Betriebssystemen vor Windows Vista nicht unterstützt.

Wenn die Anwendung derzeit nicht über einen Datenwiederherstellungshandler verfügt, erstellt diese Methode einen und gibt einen Zeiger darauf zurück.

## <a name="cwinappgetfirstdoctemplateposition"></a><a name="getfirstdoctemplateposition"></a>CWinApp::GetFirstDocTemplatePosition

Ruft die Position der ersten Dokumentvorlage in der Anwendung ab.

```
POSITION GetFirstDocTemplatePosition() const;
```

### <a name="return-value"></a>Rückgabewert

Ein POSITION-Wert, der für den Iterations- oder Objektzeigerabruf verwendet werden kann; NULL, wenn die Liste leer ist.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie den POSITION-Wert, der in einem Aufruf von [GetNextDocTemplate](#getnextdoctemplate) zurückgegeben wird, um das erste [CDocTemplate-Objekt](../../mfc/reference/cdoctemplate-class.md) abzurufen.

## <a name="cwinappgethelpmode"></a><a name="gethelpmode"></a>CWinApp::GetHelpMode

Ruft den Von der Anwendung verwendeten Hilfetyp ab.

```
AFX_HELP_TYPE GetHelpMode();
```

### <a name="return-value"></a>Rückgabewert

Der von der Anwendung verwendete Hilfetyp. Weitere Informationen finden Sie unter [CWinApp::m_eHelpType.](#m_ehelptype)

## <a name="cwinappgetnextdoctemplate"></a><a name="getnextdoctemplate"></a>CWinApp::GetNextDocTemplate

Ruft die von *pos*identifizierte Dokumentvorlage ab und legt *pos* auf den POSITION-Wert fest.

```
CDocTemplate* GetNextDocTemplate(POSITION& pos) const;
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Ein Verweis auf einen POSITION-Wert, `GetNextDocTemplate` der von einem vorherigen Aufruf von oder [GetFirstDocTemplatePosition](#getfirstdoctemplateposition)zurückgegeben wird. Der Wert wird durch diesen Aufruf auf die nächste Position aktualisiert.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CDocTemplate-Objekt.](../../mfc/reference/cdoctemplate-class.md)

### <a name="remarks"></a>Bemerkungen

Sie können `GetNextDocTemplate` in einer Vorwärtsiterationsschleife verwendet werden, `GetFirstDocTemplatePosition`wenn Sie die Ausgangsposition mit einem Aufruf von festlegen.

Sie müssen sicherstellen, dass Ihr POSITION-Wert gültig ist. Wenn sie ungültig ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt.

Wenn die abgerufene Dokumentvorlage die letzte verfügbare ist, wird der neue Wert von *pos* auf NULL gesetzt.

## <a name="cwinappgetprinterdevicedefaults"></a><a name="getprinterdevicedefaults"></a>CWinApp::GetPrinterDeviceDefaults

Rufen Sie diese Memberfunktion auf, um einen Druckergerätekontext für den Druck vorzubereiten.

```
BOOL GetPrinterDeviceDefaults(struct tagPDA* pPrintDlg);
```

### <a name="parameters"></a>Parameter

*pPrintDlg*<br/>
Ein Zeiger auf eine [PRINTDLG-Struktur.](/windows/win32/api/commdlg/ns-commdlg-printdlga)

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Ruft die aktuellen Druckerstandards aus Dem Windows ab. INI-Datei nach Bedarf oder verwendet die letzte Druckerkonfiguration, die vom Benutzer in Print Setup festgelegt wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#40](../../mfc/reference/codesnippet/cpp/cwinapp-class_6.cpp)]

## <a name="cwinappgetprofilebinary"></a><a name="getprofilebinary"></a>CWinApp::GetProfileBinary

Rufen Sie diese Memberfunktion auf, um Binärdaten aus einem Eintrag innerhalb eines angegebenen Abschnitts der Registrierung der Anwendung oder abzurufen. INI-Datei.

```
BOOL GetProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE* ppData,
    UINT* pBytes);
```

### <a name="parameters"></a>Parameter

*lpszSection*<br/>
Zeigt auf eine auf NULL endende Zeichenfolge, die den Abschnitt mit dem Eintrag angibt.

*lpszEntry*<br/>
Zeigt auf eine auf NULL endende Zeichenfolge, die den Eintrag mit dem abzurufenden Wert enthält.

*ppData*<br/>
Zeigt auf einen Zeiger, der die Adresse der Daten empfängt.

*pBytes*<br/>
Zeigt auf ein UINT, das die Größe der Daten (in Bytes) empfängt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion ist nicht groß, daher können die Zeichenfolgen in den Parametern *lpszSection* und *lpszEntry* im Fall unterschiedlich sein.

> [!NOTE]
> `GetProfileBinary`ordnet einen Puffer zu und \* gibt seine Adresse in *ppData*zurück. Der Aufrufer ist dafür verantwortlich, den Puffer mit **delete []** freizugeben.

> [!IMPORTANT]
> Die von dieser Funktion zurückgegebenen Daten enden nicht notwendigerweise auf NULL, und der Aufrufer muss die Validierung ausführen. Weitere Informationen finden Sie unter [Vermeiden von Pufferüberläufen](/windows/win32/SecBP/avoiding-buffer-overruns).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#41](../../mfc/reference/codesnippet/cpp/cwinapp-class_7.cpp)]

Ein weiteres Beispiel finden Sie unter [CWinApp::WriteProfileBinary](#writeprofilebinary).

## <a name="cwinappgetprofileint"></a><a name="getprofileint"></a>CWinApp::GetProfileInt

Rufen Sie diese Memberfunktion auf, um den Ganzzahlwert aus einem Eintrag in einem angegebenen Abschnitt der Registrierung oder der INI-Datei einer Anwendung abzurufen.

```
UINT GetProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nDefault);
```

### <a name="parameters"></a>Parameter

*lpszSection*<br/>
Zeigt auf eine auf NULL endende Zeichenfolge, die den Abschnitt mit dem Eintrag angibt.

*lpszEntry*<br/>
Zeigt auf eine auf NULL endende Zeichenfolge, die den Eintrag mit dem abzurufenden Wert enthält.

*nDefault*<br/>
Gibt den zurückzugebenden Standardwert an, wenn der Eintrag vom Framework nicht gefunden werden kann.

### <a name="return-value"></a>Rückgabewert

Der dem bei erfolgreicher Funktion angegebene Eintrag folgende Ganzzahlwert der Zeichenfolge. Der Rückgabewert ist der Wert des *Parameters nDefault,* wenn die Funktion den Eintrag nicht findet. Der Rückgabewert ist null (0), wenn der dem angegebenen Eintrag entsprechende Wert keine ganze Zahl ist.

Diese Memberfunktion unterstützt Hexadezimalnotation für den Wert in der INI-Datei. Wenn Sie eine signierte ganzzahlig abrufen, sollten Sie den Wert in eine **int**umwerfen.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion ist nicht groß, daher können die Zeichenfolgen in den Parametern *lpszSection* und *lpszEntry* im Fall unterschiedlich sein.

> [!IMPORTANT]
> Die von dieser Funktion zurückgegebenen Daten enden nicht notwendigerweise auf NULL, und der Aufrufer muss die Validierung ausführen. Weitere Informationen finden Sie unter [Vermeiden von Pufferüberläufen](/windows/win32/SecBP/avoiding-buffer-overruns).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#42](../../mfc/reference/codesnippet/cpp/cwinapp-class_8.cpp)]

Ein weiteres Beispiel finden Sie unter [CWinApp::WriteProfileInt](#writeprofileint).

## <a name="cwinappgetprofilestring"></a><a name="getprofilestring"></a>CWinApp::GetProfileString

Rufen Sie diese Memberfunktion auf, um die Zeichenfolge abzurufen, die einem Eintrag innerhalb des angegebenen Abschnitts in der Registrierung der Anwendung oder zugeordnet ist. INI-Datei.

```
CString GetProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszDefault = NULL);
```

### <a name="parameters"></a>Parameter

*lpszSection*<br/>
Zeigt auf eine auf NULL endende Zeichenfolge, die den Abschnitt mit dem Eintrag angibt.

*lpszEntry*<br/>
Zeigt auf eine null-terminierte Zeichenfolge, die den Eintrag enthält, dessen Zeichenfolge abgerufen werden soll. Dieser Wert darf nicht NULL sein.

*lpszDefault*<br/>
Zeigt auf den Standardzeichenfolgenwert für den angegebenen Eintrag, wenn der Eintrag in der Initialisierungsdatei nicht gefunden werden kann.

### <a name="return-value"></a>Rückgabewert

Der Rückgabewert ist die Zeichenfolge aus der Anwendung . INI-Datei oder *lpszDefault,* wenn die Zeichenfolge nicht gefunden werden kann. Die maximale Zeichenfolgenlänge, die vom Framework unterstützt wird, ist _MAX_PATH. Wenn *lpszDefault* NULL ist, ist der Rückgabewert eine leere Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

> [!IMPORTANT]
> Die von dieser Funktion zurückgegebenen Daten enden nicht notwendigerweise auf NULL, und der Aufrufer muss die Validierung ausführen. Weitere Informationen finden Sie unter [Vermeiden von Pufferüberläufen](/windows/win32/SecBP/avoiding-buffer-overruns).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

Ein weiteres Beispiel finden Sie im Beispiel für [CWinApp::GetProfileInt](#getprofileint).

## <a name="cwinappgetsectionkey"></a><a name="getsectionkey"></a>CWinApp::GetSectionKey

Gibt den Schlüssel\\für HKEY_CURRENT_USER "Software" zurück.

```
HKEY GetSectionKey(
    LPCTSTR lpszSection,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parameter

*lpszSection*<br/>
Der Name des zu erhaltenden Schlüssels.

*Ptm*<br/>
Zeiger auf `CAtlTransactionManager` ein Objekt.

### <a name="return-value"></a>Rückgabewert

Abschnittsschlüssel, wenn die Funktion erfolgreich ist; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

## <a name="cwinapphideapplication"></a><a name="hideapplication"></a>CWinApp::HideApplication

Rufen Sie diese Memberfunktion auf, um eine Anwendung auszublenden, bevor Sie die geöffneten Dokumente schließen.

```cpp
void HideApplication();
```

## <a name="cwinapphtmlhelp"></a><a name="htmlhelp"></a>CWinApp::HtmlHilfe

Rufen Sie diese Memberfunktion auf, um die HTMLHelp-Anwendung aufzurufen.

```
virtual void HtmlHelp(
    DWORD_PTR dwData,
    UINT nCmd = 0x000F);
```

### <a name="parameters"></a>Parameter

*dwData*<br/>
Gibt zusätzliche Daten an. Der verwendete Wert hängt vom Wert des *parameters nCmd* ab. Standardwerte `0x000F` für [die HH_HELP_CONTEXT](/previous-versions/windows/desktop/htmlhelp/hh-help-context-command).

*nCmd*<br/>
Gibt den Typ der angeforderten Hilfe an. Eine Liste möglicher Werte und deren Auswirkungen auf den *parameter dwData* finden Sie im *Parameter uCommand,* der in den [HTMLHelpW-](/windows/win32/api/htmlhelp/nf-htmlhelp-htmlhelpw) oder [HtmlHelpA-API-Funktionen](/windows/win32/api/htmlhelp/nf-htmlhelp-htmlhelpa) im Windows SDK beschrieben wird.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Funktion auch auf, um die HTMLHelp-Anwendung aufzurufen.

Das Framework schließt die HTMLHelp-Anwendung automatisch, wenn die Anwendung beendet wird.

## <a name="cwinappinitinstance"></a><a name="initinstance"></a>CWinApp::InitInstance

Windows ermöglicht die gleichzeitige Ausführung mehrerer Kopien desselben Programms.

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Initialisierung erfolgreich ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Anwendungsinitialisierung ist konzeptionell in zwei Abschnitte unterteilt: einmalige Anwendungsinitialisierung, die bei der ersten Programmauslaufierung erfolgt, und Instanzinitialisierung, die jedes Mal ausgeführt wird, wenn eine Kopie des Programms ausgeführt wird, einschließlich des ersten Mals. Die Implementierung dieser `WinMain` Funktion durch den Rahmen ruft diese Funktion auf.

Überschreiben `InitInstance` Sie, um jede neue Instanz Ihrer Anwendung zu initialisieren, die unter Windows ausgeführt wird. In der Regel `InitInstance` überschreiben Sie, um `CWinThread::m_pMainWnd` das Hauptfensterobjekt zu erstellen, und legen den Datenmember so fest, dass es auf dieses Fenster zeigt. Weitere Informationen zum Überschreiben dieser Memberfunktion finden Sie unter [CWinApp: The Application Class](../../mfc/cwinapp-the-application-class.md).

> [!NOTE]
> MFC-Anwendungen müssen als Singlethread-Apartment (STA) initialisiert werden. Wenn Sie [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) `InitInstance` in Ihrer Außerkraftsetzung aufrufen, geben Sie COINIT_APARTMENTTHREADED (anstelle COINIT_MULTITHREADED) an.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCListView#9](../../atl/reference/codesnippet/cpp/cwinapp-class_10.cpp)]

## <a name="cwinappistaskbarinteractionenabled"></a><a name="istaskbarinteractionenabled"></a>CWinApp::IsTaskbarInteractionAktiviert

Gibt an, ob die Windows 7-Taskleisteninteraktion aktiviert ist.

```
virtual BOOL IsTaskbarInteractionEnabled();
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE `EnableTaskbarInteraction` zurück, wenn aufgerufen wurde und das Betriebssystem Windows 7 oder höher ist.

### <a name="remarks"></a>Bemerkungen

Taskleisteninteraktion bedeutet, dass die MDI-Anwendung den Inhalt von mDI-Untergeordneten in separaten Miniaturansichten mit Registerkarten anzeigt, die angezeigt werden, wenn sich der Mauszeiger über der Anwendungstaskleistenschaltfläche befindet.

## <a name="cwinapploadcursor"></a><a name="loadcursor"></a>CWinApp::LoadCursor

Lädt die Cursorressource mit dem Namen *lpszResourceName* oder die von *nIDResource* aus der aktuellen ausführbaren Datei angegeben.

```
HCURSOR LoadCursor(LPCTSTR lpszResourceName) const;  HCURSOR LoadCursor(UINT nIDResource) const;
```

### <a name="parameters"></a>Parameter

*lpszResourceName*<br/>
Verweist auf eine null-terminierte Zeichenfolge, die den Namen der Cursorressource enthält. Sie können `CString` eine für dieses Argument verwenden.

*nIDResource*<br/>
ID der Cursorressource. Eine Liste der Ressourcen finden Sie unter [LoadCursor](/windows/win32/api/winuser/nf-winuser-loadcursorw) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ein Handle für einen Cursor, wenn erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

`LoadCursor`lädt den Cursor nur dann in den Speicher, wenn er zuvor nicht geladen wurde; Andernfalls wird ein Handle der vorhandenen Ressource abgerufen.

Verwenden Sie die [Memberfunktion LoadStandardCursor](#loadstandardcursor) oder [LoadOEMCursor,](#loadoemcursor) um auf die vordefinierten Windows-Cursor zuzugreifen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#44](../../mfc/reference/codesnippet/cpp/cwinapp-class_11.cpp)]

## <a name="cwinapploadicon"></a><a name="loadicon"></a>CWinApp::LoadIcon

Lädt die Symbolressource mit dem Namen *lpszResourceName* oder die von *nIDResource* aus der ausführbaren Datei angegeben wird.

```
HICON LoadIcon(LPCTSTR lpszResourceName) const;  HICON LoadIcon(UINT nIDResource) const;
```

### <a name="parameters"></a>Parameter

*lpszResourceName*<br/>
Zeigt auf eine null-terminierte Zeichenfolge, die den Namen der Symbolressource enthält. Sie können auch `CString` eine für dieses Argument verwenden.

*nIDResource*<br/>
ID-Nummer der Symbolressource.

### <a name="return-value"></a>Rückgabewert

Ein Handle für ein Symbol, wenn erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

`LoadIcon`lädt das Symbol nur, wenn es nicht zuvor geladen wurde; Andernfalls wird ein Handle der vorhandenen Ressource abgerufen.

Sie können die [Memberfunktion LoadStandardIcon](#loadstandardicon) oder [LoadOEMIcon](#loadoemicon) verwenden, um auf die vordefinierten Windows-Symbole zuzugreifen.

> [!NOTE]
> Diese Memberfunktion ruft die Win32-API-Funktion [LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw)auf, die nur ein Symbol laden kann, dessen Größe den SM_CXICON- und SM_CYICON Systemmetrikwerten entspricht.

## <a name="cwinapploadoemcursor"></a><a name="loadoemcursor"></a>CWinApp::LoadOEMCursor

Lädt die von *nIDCursor*angegebene vordefinierte Windows-Cursorressource .

```
HCURSOR LoadOEMCursor(UINT nIDCursor) const;
```

### <a name="parameters"></a>Parameter

*nIDCursor*<br/>
Ein **OCR_** Manifestkonstantenbezeichner, der einen vordefinierten Windows-Cursor angibt. Sie müssen `#define OEMRESOURCE` `#include \<afxwin.h>` zuvor Zugriff auf die **OCR_** konstanten in WINDOWS erhalten. H.

### <a name="return-value"></a>Rückgabewert

Ein Handle für einen Cursor, wenn erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Verwenden `LoadOEMCursor` Sie die Memberfunktion oder [LoadStandardCursor,](#loadstandardcursor) um auf die vordefinierten Windows-Cursor zuzugreifen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#45](../../mfc/reference/codesnippet/cpp/cwinapp-class_12.h)]

[!code-cpp[NVC_MFCWindowing#46](../../mfc/reference/codesnippet/cpp/cwinapp-class_13.cpp)]

## <a name="cwinapploadoemicon"></a><a name="loadoemicon"></a>CWinApp::LoadOEMIcon

Lädt die von *nIDIcon*angegebene vordefinierte Windows-Symbolressource .

```
HICON LoadOEMIcon(UINT nIDIcon) const;
```

### <a name="parameters"></a>Parameter

*nIDIcon*<br/>
Ein **OIC_** Manifestkonstantenbezeichner, der ein vordefiniertes Windows-Symbol angibt. Sie müssen `#define OEMRESOURCE` `#include \<afxwin.h>` zuvor auf die **OIC_-Konstanten** in WINDOWS zugreifen müssen. H.

### <a name="return-value"></a>Rückgabewert

Ein Handle für ein Symbol, wenn erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Verwenden `LoadOEMIcon` Sie die Memberfunktion oder [LoadStandardIcon,](#loadstandardicon) um auf die vordefinierten Windows-Symbole zuzugreifen.

## <a name="cwinapploadstandardcursor"></a><a name="loadstandardcursor"></a>CWinApp::LoadStandardCursor

Lädt die vordefinierte Windows-Cursorressource, die *lpszCursorName* angibt.

```
HCURSOR LoadStandardCursor(LPCTSTR lpszCursorName) const;
```

### <a name="parameters"></a>Parameter

*lpszCursorName*<br/>
Ein **IDC_** Manifestkonstantenbezeichner, der einen vordefinierten Windows-Cursor angibt. Diese Bezeichner sind in WINDOWS definiert. H. Die folgende Liste zeigt die möglichen vordefinierten Werte und Bedeutungen für *lpszCursorName*:

- IDC_ARROW Standard-Pfeilcursor

- IDC_IBEAM Standard-Texteinfügecursor

- IDC_WAIT Hourglass-Cursor verwendet, wenn Windows eine zeitaufwändige Aufgabe ausführt

- IDC_CROSS Kreuzhaarcursor zur Auswahl

- IDC_UPARROW Pfeil, der gerade nach oben zeigt

- IDC_SIZE Veraltet und nicht unterstützt; verwenden Sie IDC_SIZEALL

- IDC_SIZEALL Ein vierzackigem Pfeil. Der Cursor, der zum Ändern der Größe eines Fensters verwendet werden soll.

- IDC_ICON Veraltet und nicht unterstützt. Verwenden Sie IDC_ARROW.

- IDC_SIZENWSE Zweiköpfiger Pfeil mit Enden oben links und unten rechts

- IDC_SIZENESW Zweiköpfiger Pfeil mit Enden oben rechts und unten links

- IDC_SIZEWE Horizontaler Zweikopfpfeil

- IDC_SIZENS Vertikaler Zweikopfpfeil

### <a name="return-value"></a>Rückgabewert

Ein Handle für einen Cursor, wenn erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Verwenden `LoadStandardCursor` Sie die Memberfunktion or [LoadOEMCursor,](#loadoemcursor) um auf die vordefinierten Windows-Cursor zuzugreifen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#47](../../mfc/reference/codesnippet/cpp/cwinapp-class_14.cpp)]

## <a name="cwinapploadstandardicon"></a><a name="loadstandardicon"></a>CWinApp::LoadStandardIcon

Lädt die vordefinierte Windows-Symbolressource, die *lpszIconName* angibt.

```
HICON LoadStandardIcon(LPCTSTR lpszIconName) const;
```

### <a name="parameters"></a>Parameter

*lpszIconName*<br/>
Ein Manifestkonstantenbezeichner, der ein vordefiniertes Windows-Symbol angibt. Diese Bezeichner sind in WINDOWS definiert. H. Eine Liste der möglichen vordefinierten Werte und deren Beschreibungen finden Sie im Parameter *lpIconName* in [LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ein Handle für ein Symbol, wenn erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Verwenden `LoadStandardIcon` Sie die Memberfunktion or [LoadOEMIcon,](#loadoemicon) um auf die vordefinierten Windows-Symbole zuzugreifen.

## <a name="cwinapploadstdprofilesettings"></a><a name="loadstdprofilesettings"></a>CWinApp::LoadStdProfileEinstellungen

Rufen Sie diese Memberfunktion innerhalb der [InitInstance-Memberfunktion](#initinstance) auf, um die Liste der zuletzt verwendeten (MRU)-Dateien und den letzten Vorschaustatus zu aktivieren und zu laden.

```cpp
void LoadStdProfileSettings(UINT nMaxMRU = _AFX_MRU_COUNT);
```

### <a name="parameters"></a>Parameter

*nMaxMRU*<br/>
Die Anzahl der zuletzt verwendeten Dateien, die nachverfolgt werden sollen.

### <a name="remarks"></a>Bemerkungen

Wenn *nMaxMRU* 0 ist, wird keine MRU-Liste beibehalten.

## <a name="cwinappm_bhelpmode"></a><a name="m_bhelpmode"></a>CWinApp::m_bHelpMode

TRUE, wenn sich die Anwendung im Hilfekontextmodus befindet (konventionell mit SHIFT + F1 aufgerufen); andernfalls FALSE.

```
BOOL m_bHelpMode;
```

### <a name="remarks"></a>Bemerkungen

Im Hilfekontextmodus wird der Cursor zu einem Fragezeichen, und der Benutzer kann ihn über den Bildschirm bewegen. Überprüfen Sie dieses Flag, wenn Sie im Hilfemodus eine spezielle Behandlung implementieren möchten. `m_bHelpMode`ist eine öffentliche Variable vom Typ BOOL.

## <a name="cwinappm_dwrestartmanagersupportflags"></a><a name="m_dwrestartmanagersupportflags"></a>CWinApp::m_dwRestartManagerSupportFlags

Flags, die das Verhalten des Neustart-Managers bestimmen.

```
DWORD m_dwRestartManagerSupportFlags;
```

### <a name="remarks"></a>Bemerkungen

Um den Neustart-Manager `m_dwRestartManagerSupportFlags` zu aktivieren, legen Sie das gewünschte Verhalten fest. Die folgende Tabelle zeigt die verfügbaren Flags.

|||
|-|-|
|Flag|BESCHREIBUNG|
|AFX_RESTART_MANAGER_SUPPORT_RESTART|Die Anwendung wird mit [CWinApp::RegisterWithRestartManager](#registerwithrestartmanager)registriert. Der Neustart-Manager ist für den Neustart der Anwendung verantwortlich, wenn sie unerwartet beendet wird.|
|- AFX_RESTART_MANAGER_SUPPORT_RECOVERY|Die Anwendung wird beim Neustart-Manager registriert, und der Neustart-Manager ruft die Wiederherstellungsrückruffunktion auf, wenn die Anwendung neu gestartet wird. Die standardmäßige Wiederherstellungsrückruffunktion ist [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).|
|- AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART|Autosave ist aktiviert, und der Neustart-Manager speichert alle geöffneten Dokumente automatisch, wenn die Anwendung neu gestartet wird.|
|- AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL|Autosave ist aktiviert, und der Neustart-Manager speichert alle geöffneten Dokumente in regelmäßigen Abständen automatisch. Das Intervall wird durch [CWinApp::m_nAutosaveInterval](#m_nautosaveinterval)definiert.|
|- AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES|Der Neustart-Manager öffnet zuvor geöffnete Dokumente, nachdem er die Anwendung nach einem unerwarteten Beenden neu gestartet hat. Die [CDataRecoveryHandler-Klasse](../../mfc/reference/cdatarecoveryhandler-class.md) verarbeitet das Speichern der Liste der geöffneten Dokumente und deren Wiederherstellung.|
|- AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES|Der Neustart-Manager fordert den Benutzer auf, automatisch gespeicherte Dateien nach dem Neustart der Anwendung wiederherzustellen. Die `CDataRecoveryHandler` Klasse fragt den Benutzer ab.|
|- AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE|Die Vereinigung von AFX_RESTART_MANAGER_SUPPORT_RESTART, AFX_RESTART_MANAGER_SUPPORT_RECOVER und AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES.|
|- AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS|Die Vereinigung von AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART, AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL und AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|
|- AFX_RESTART_MANAGER_SUPPORT_RESTART_ASPECTS|Die Vereinigung von AFX_RESTART_MANAGER_SUPPORT_RESTART, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES und AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|
|- AFX_RESTART_MANAGER_SUPPORT_RECOVERY_ASPECTS|Die Gewerkschaft ofAFX_RESTART_MANAGER_SUPPORT_RECOVERY, AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES und AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|

## <a name="cwinappm_ehelptype"></a><a name="m_ehelptype"></a>CWinApp::m_eHelpType

Der Typ dieses Datenmembers ist der aufgezählte Typ AFX_HELP_TYPE, der innerhalb der `CWinApp` Klasse definiert ist.

```
AFX_HELP_TYPE m_eHelpType;
```

### <a name="remarks"></a>Bemerkungen

Die AFX_HELP_TYPE-Enumeration ist wie folgt definiert:

```
enum AFX_HELP_TYPE {
    afxWinHelp = 0,
    afxHTMLHelp = 1
    };
```

- Um die Hilfe der Anwendung auf HTML-Hilfe festzulegen, rufen Sie [SetHelpMode](#sethelpmode) auf, und geben Sie an. `afxHTMLHelp`

- Um die Hilfe der Anwendung auf `SetHelpMode` WinHelp `afxWinHelp`festzulegen, rufen Sie an, und geben Sie an.

## <a name="cwinappm_hinstance"></a><a name="m_hinstance"></a>CWinApp::m_hInstance

Entspricht dem *hInstance-Parameter,* `WinMain`der von Windows an übergeben wird.

```
HINSTANCE m_hInstance;
```

### <a name="remarks"></a>Bemerkungen

Das `m_hInstance` Datenelement ist ein Handle für die aktuelle Instanz der Anwendung, die unter Windows ausgeführt wird. Dies wird von der globalen Funktion [AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle)zurückgegeben. `m_hInstance`ist eine öffentliche Variable vom Typ HINSTANCE.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#55](../../mfc/reference/codesnippet/cpp/cwinapp-class_15.cpp)]

## <a name="cwinappm_lpcmdline"></a><a name="m_lpcmdline"></a>CWinApp::m_lpCmdLine

Entspricht dem *parameter lpCmdLine,* `WinMain`der von Windows an übergeben wird.

```
LPTSTR m_lpCmdLine;
```

### <a name="remarks"></a>Bemerkungen

Zeigt auf eine null-terminierte Zeichenfolge, die die Befehlszeile für die Anwendung angibt. Verwenden `m_lpCmdLine` Sie diese Option, um auf alle Befehlszeilenargumente zuzugreifen, die der Benutzer beim Starten der Anwendung eingegeben hat. `m_lpCmdLine`ist eine öffentliche Variable vom Typ LPTSTR.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

## <a name="cwinappm_nautosaveinterval"></a><a name="m_nautosaveinterval"></a>CWinApp::m_nAutosaveInterval

Die Zeitdauer in Millisekunden zwischen Autosaves.

```
int m_nAutosaveInterval;
```

### <a name="remarks"></a>Bemerkungen

Sie können den Neustart-Manager so konfigurieren, dass geöffnete Dokumente in festgelegten Intervallen automatisch gespeichert werden. Wenn Ihre Anwendung Dateien nicht automatisch speichert, hat dieser Parameter keine Auswirkungen.

## <a name="cwinappm_ncmdshow"></a><a name="m_ncmdshow"></a>CWinApp::m_nCmdShow

Entspricht dem *nCmdShow-Parameter,* `WinMain`der von Windows an übergeben wird.

```
int m_nCmdShow;
```

### <a name="remarks"></a>Bemerkungen

Sie sollten `m_nCmdShow` als Argument übergeben werden, wenn Sie [CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow) für das Hauptfenster Ihrer Anwendung aufrufen. `m_nCmdShow`ist eine öffentliche Variable vom Typ **int**.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#56](../../mfc/reference/codesnippet/cpp/cwinapp-class_17.cpp)]

## <a name="cwinappm_pactivewnd"></a><a name="m_pactivewnd"></a>CWinApp::m_pActiveWnd

Verwenden Sie dieses Datenelement, um einen Zeiger auf das Hauptfenster der OLE-Containeranwendung zu speichern, für das Die OLE-Serveranwendung aktiviert ist.

### <a name="remarks"></a>Bemerkungen

Wenn dieses Datenelement NULL ist, ist die Anwendung nicht aktiv.

Das Framework legt diese Membervariable fest, wenn das Rahmenfenster von einer OLE-Containeranwendung aktiviert wird.

## <a name="cwinappm_pdatarecoveryhandler"></a><a name="m_pdatarecoveryhandler"></a>CWinApp::m_pDataRecoveryHandler

Zeiger auf den Datenwiederherstellungshandler für die Anwendung.

```
CDataRecoveryHandler* m_pDataRecoveryHandler;
```

### <a name="remarks"></a>Bemerkungen

Der Datenwiederherstellungshandler einer Anwendung überwacht geöffnete Dokumente und speichert sie automatisch. Das Framework verwendet den Datenwiederherstellungshandler, um automatisch gespeicherte Dateien wiederherzustellen, wenn eine Anwendung neu gestartet wird, nachdem sie unerwartet beendet wurde. Weitere Informationen finden Sie unter [CDataRecoveryHandler-Klasse](../../mfc/reference/cdatarecoveryhandler-class.md).

## <a name="cwinappm_pszappname"></a><a name="m_pszappname"></a>CWinApp::m_pszAppName

Gibt den Namen der Anwendung an.

```
LPCTSTR m_pszAppName;
```

### <a name="remarks"></a>Bemerkungen

Der Anwendungsname kann aus dem Parameter stammen, der an den [CWinApp-Konstruktor](#cwinapp) übergeben wird, oder, falls nicht angegeben, an die Ressourcenzeichenfolge mit der ID AFX_IDS_APP_TITLE. Wenn der Anwendungsname nicht in der Ressource gefunden wird, stammt er von der . EXE-Dateiname.

Von der globalen Funktion [AfxGetAppName](application-information-and-management.md#afxgetappname)zurückgegeben. `m_pszAppName`ist eine öffentliche Variable vom Typ **const char**<strong>\*</strong>.

> [!NOTE]
> Wenn Sie einen `m_pszAppName`Wert zuzuweisen, muss er dynamisch auf dem Heap zugewiesen werden. Der `CWinApp` Destruktor ruft mit diesem Zeiger **frei**( ) auf. Sie möchten die `_tcsdup`Laufzeitbibliotheksfunktion ( ) verwenden, um die Zuweisung durchzuführen. Geben Sie außerdem den Speicher frei, der dem aktuellen Zeiger zugeordnet ist, bevor Sie einen neuen Wert zuweisen. Beispiel:

[!code-cpp[NVC_MFCWindowing#57](../../mfc/reference/codesnippet/cpp/cwinapp-class_18.cpp)]

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#65](../../mfc/reference/codesnippet/cpp/cwinapp-class_19.cpp)]

## <a name="cwinappm_pszexename"></a><a name="m_pszexename"></a>CWinApp::m_pszExeName

Enthält den Namen der ausführbaren Datei der Anwendung ohne Erweiterung.

```
LPCTSTR m_pszExeName;
```

### <a name="remarks"></a>Bemerkungen

Im Gegensatz zu [m_pszAppName](#m_pszappname)darf dieser Name keine Leerzeichen enthalten. `m_pszExeName`ist eine öffentliche Variable vom Typ **const char**<strong>\*</strong>.

> [!NOTE]
> Wenn Sie einen `m_pszExeName`Wert zuzuweisen, muss er dynamisch auf dem Heap zugewiesen werden. Der `CWinApp` Destruktor ruft mit diesem Zeiger **frei**( ) auf. Sie möchten die `_tcsdup`Laufzeitbibliotheksfunktion ( ) verwenden, um die Zuweisung durchzuführen. Geben Sie außerdem den Speicher frei, der dem aktuellen Zeiger zugeordnet ist, bevor Sie einen neuen Wert zuweisen. Beispiel:

[!code-cpp[NVC_MFCWindowing#58](../../mfc/reference/codesnippet/cpp/cwinapp-class_20.cpp)]

## <a name="cwinappm_pszhelpfilepath"></a><a name="m_pszhelpfilepath"></a>CWinApp::m_pszHelpFilePath

Enthält den Pfad zur Hilfedatei der Anwendung.

```
LPCTSTR m_pszHelpFilePath;
```

### <a name="remarks"></a>Bemerkungen

Standardmäßig initialisiert `m_pszHelpFilePath` das Framework den Namen der Anwendung mit ". HLP" angehängt. Um den Namen der Hilfedatei `m_pszHelpFilePath` zu ändern, setzen Sie den Punkt auf eine Zeichenfolge, die den vollständigen Namen der gewünschten Hilfedatei enthält. Ein bequemer Ort, um dies zu tun, ist in der [InitInstance-Funktion](#initinstance) der Anwendung. `m_pszHelpFilePath`ist eine öffentliche Variable vom Typ **const char**<strong>\*</strong>.

> [!NOTE]
> Wenn Sie einen `m_pszHelpFilePath`Wert zuzuweisen, muss er dynamisch auf dem Heap zugewiesen werden. Der `CWinApp` Destruktor ruft mit diesem Zeiger **frei**( ) auf. Sie möchten die `_tcsdup`Laufzeitbibliotheksfunktion ( ) verwenden, um die Zuweisung durchzuführen. Geben Sie außerdem den Speicher frei, der dem aktuellen Zeiger zugeordnet ist, bevor Sie einen neuen Wert zuweisen. Beispiel:

[!code-cpp[NVC_MFCWindowing#59](../../mfc/reference/codesnippet/cpp/cwinapp-class_21.cpp)]

## <a name="cwinappm_pszprofilename"></a><a name="m_pszprofilename"></a>CWinApp::m_pszProfileName

Enthält den Namen der Anwendung . INI-Datei.

```
LPCTSTR m_pszProfileName;
```

### <a name="remarks"></a>Bemerkungen

`m_pszProfileName`ist eine öffentliche Variable vom Typ **const char**<strong>\*</strong>.

> [!NOTE]
> Wenn Sie einen `m_pszProfileName`Wert zuzuweisen, muss er dynamisch auf dem Heap zugewiesen werden. Der `CWinApp` Destruktor ruft mit diesem Zeiger **frei**( ) auf. Sie möchten die `_tcsdup`Laufzeitbibliotheksfunktion ( ) verwenden, um die Zuweisung durchzuführen. Geben Sie außerdem den Speicher frei, der dem aktuellen Zeiger zugeordnet ist, bevor Sie einen neuen Wert zuweisen. Beispiel:

[!code-cpp[NVC_MFCWindowing#60](../../mfc/reference/codesnippet/cpp/cwinapp-class_22.cpp)]

## <a name="cwinappm_pszregistrykey"></a><a name="m_pszregistrykey"></a>CWinApp::m_pszRegistryKey

Wird verwendet, um zu bestimmen, wo in der Registrierung oder in der INI-Datei Anwendungsprofileinstellungen gespeichert werden.

```
LPCTSTR m_pszRegistryKey;
```

### <a name="remarks"></a>Bemerkungen

Normalerweise wird dieses Datenelement als schreibgeschützt behandelt.

- Der Wert wird in einem Registrierungsschlüssel gespeichert. Der Name für die Anwendungsprofileinstellung wird an den folgenden Registrierungsschlüssel angehängt: HKEY_CURRENT_USER/Software/LocalAppWizard-Generated/.

Wenn Sie einen `m_pszRegistryKey`Wert zuzuweisen, muss er dynamisch auf dem Heap zugewiesen werden. Der `CWinApp` Destruktor ruft mit diesem Zeiger **frei**( ) auf. Sie möchten die `_tcsdup`Laufzeitbibliotheksfunktion ( ) verwenden, um die Zuweisung durchzuführen. Geben Sie außerdem den Speicher frei, der dem aktuellen Zeiger zugeordnet ist, bevor Sie einen neuen Wert zuweisen. Beispiel:

[!code-cpp[NVC_MFCWindowing#61](../../mfc/reference/codesnippet/cpp/cwinapp-class_23.cpp)]

## <a name="cwinappm_pszappid"></a><a name="m_pszappid"></a>CWinApp::m_pszAppID

Anwendungsbenutzermodell-ID.

```
LPCTSTR m_pszAppID;
```

### <a name="remarks"></a>Bemerkungen

## <a name="cwinapponcontexthelp"></a><a name="oncontexthelp"></a>CWinApp::OnContextHelp

Behandelt die SHIFT+F1-Hilfe in der Anwendung.

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>Bemerkungen

Sie müssen `ON_COMMAND( ID_CONTEXT_HELP, OnContextHelp )` ihrer `CWinApp` Klassennachrichtenzuordnung eine Anweisung hinzufügen und auch einen Beschleunigertabelleneintrag hinzufügen, in der Regel UMSCHALT+F1, um diese Memberfunktion zu aktivieren.

`OnContextHelp`versetzt die Anwendung in den Hilfemodus. Der Cursor ändert sich in einen Pfeil und ein Fragezeichen, und der Benutzer kann dann den Mauszeiger bewegen und die linke Maustaste drücken, um ein Dialogfeld, ein Fenster, ein Menü oder eine Befehlsschaltfläche auszuwählen. Diese Memberfunktion ruft den Hilfekontext des Objekts unter dem Cursor ab und ruft die Windows-Funktion WinHelp mit diesem Hilfekontext auf.

## <a name="cwinapponddecommand"></a><a name="onddecommand"></a>CWinApp::OnDDECommand

Wird vom Framework aufgerufen, wenn das Hauptrahmenfenster eine DDE-Ausführungsnachricht empfängt.

```
virtual BOOL OnDDECommand(LPTSTR lpszCommand);
```

### <a name="parameters"></a>Parameter

*lpszCommand*<br/>
Zeigt auf eine DDE-Befehlszeichenfolge, die von der Anwendung empfangen wird.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Befehl behandelt wird; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung prüft, ob es sich bei dem Befehl um eine Anforderung zum Öffnen eines Dokuments und, falls dies, um das angegebene Dokument handelt. Der Windows-Datei-Manager sendet normalerweise solche DDE-Befehlszeichenfolgen, wenn der Benutzer auf eine Datendatei doppelklickt. Überschreiben Sie diese Funktion, um andere DDE-Ausführungsbefehle zu behandeln, z. B. den zu druckenden Befehl.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#48](../../mfc/reference/codesnippet/cpp/cwinapp-class_24.cpp)]

## <a name="cwinapponfilenew"></a><a name="onfilenew"></a>CWinApp::OnFileNeu

Implementiert den Befehl ID_FILE_NEW.

```
afx_msg void OnFileNew();
```

### <a name="remarks"></a>Bemerkungen

Sie müssen `ON_COMMAND( ID_FILE_NEW, OnFileNew )` Ihrer `CWinApp` Klassennachrichtenzuordnung eine Anweisung hinzufügen, um diese Memberfunktion zu aktivieren. Wenn diese Funktion aktiviert ist, wird die Ausführung des Befehls Datei neu verarbeitet.

Informationen zum Standardverhalten und Anleitungen zum Überschreiben dieser Memberfunktion finden Sie unter [Technical Note 22.](../../mfc/tn022-standard-commands-implementation.md)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

## <a name="cwinapponfileopen"></a><a name="onfileopen"></a>CWinApp::OnFileÖffnen

Implementiert den Befehl ID_FILE_OPEN.

```
afx_msg void OnFileOpen();
```

### <a name="remarks"></a>Bemerkungen

Sie müssen `ON_COMMAND( ID_FILE_OPEN, OnFileOpen )` Ihrer `CWinApp` Klassennachrichtenzuordnung eine Anweisung hinzufügen, um diese Memberfunktion zu aktivieren. Wenn diese Funktion aktiviert ist, wird die Ausführung des Befehls Datei geöffnet verarbeitet.

Informationen zum Standardverhalten und Anleitungen zum Überschreiben dieser Memberfunktion finden Sie unter [Technischer Hinweis 22](../../mfc/tn022-standard-commands-implementation.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

## <a name="cwinapponfileprintsetup"></a><a name="onfileprintsetup"></a>CWinApp::OnFilePrintSetup

Implementiert den ID_FILE_PRINT_SETUP-Befehl.

```
afx_msg void OnFilePrintSetup();
```

### <a name="remarks"></a>Bemerkungen

Sie müssen `ON_COMMAND( ID_FILE_PRINT_SETUP, OnFilePrintSetup )` Ihrer `CWinApp` Klassennachrichtenzuordnung eine Anweisung hinzufügen, um diese Memberfunktion zu aktivieren. Wenn diese Option aktiviert ist, wird die Ausführung des Befehls Dateidruck verarbeitet.

Informationen zum Standardverhalten und Anleitungen zum Überschreiben dieser Memberfunktion finden Sie unter [Technischer Hinweis 22](../../mfc/tn022-standard-commands-implementation.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

## <a name="cwinapponhelp"></a><a name="onhelp"></a>CWinApp::Hilfe

Verarbeitet die F1-Hilfe in der Anwendung (unter Verwendung des aktuellen Kontexts).

```
afx_msg void OnHelp();
```

### <a name="remarks"></a>Bemerkungen

Normalerweise fügen Sie auch einen Accelerator-Key-Eintrag für die F1-Taste hinzu. Das Aktivieren des F1-Schlüssels ist nur eine Konvention und keine Anforderung.

Sie müssen `ON_COMMAND( ID_HELP, OnHelp )` Ihrer `CWinApp` Klassennachrichtenzuordnung eine Anweisung hinzufügen, um diese Memberfunktion zu aktivieren. Wenn aktiviert, wird vom Framework aufgerufen, wenn der Benutzer die Taste F1 drückt.

Die Standardimplementierung dieser Message-Handler-Funktion bestimmt den Hilfekontext, der dem aktuellen Fenster, Dialogfeld oder Menüelement entspricht, und ruft dann WINHELP auf. EXE. Wenn derzeit kein Kontext verfügbar ist, verwendet die Funktion den Standardkontext.

Überschreiben Sie diese Memberfunktion, um den Hilfekontext auf etwas anderes als das Fenster, das Dialogfeld, das Menüelement oder die Symbolleistenschaltfläche festzulegen, auf die derzeit der Fokus liegt. Rufen `WinHelp` Sie mit der gewünschten Hilfekontext-ID auf.

## <a name="cwinapponhelpfinder"></a><a name="onhelpfinder"></a>CWinApp::OnHelpFinder

Behandelt die ID_HELP_FINDER- und ID_DEFAULT_HELP-Befehle.

```
afx_msg void OnHelpFinder();
```

### <a name="remarks"></a>Bemerkungen

Sie müssen `ON_COMMAND( ID_HELP_FINDER, OnHelpFinder )` Ihrer `CWinApp` Klassennachrichtenzuordnung eine Anweisung hinzufügen, um diese Memberfunktion zu aktivieren. Wenn diese Option aktiviert ist, ruft das Framework diese Message-Handler-Funktion `WinHelp` auf, wenn der Benutzer Ihrer Anwendung den Befehl Hilfefinder auswählt, der mit dem **StandardHELP_FINDER** Thema aufgerufen werden soll.

## <a name="cwinapponhelpindex"></a><a name="onhelpindex"></a>CWinApp::OnHelpIndex

Behandelt den Befehl ID_HELP_INDEX und stellt ein Standardhilfethema bereit.

```
afx_msg void OnHelpIndex();
```

### <a name="remarks"></a>Bemerkungen

Sie müssen `ON_COMMAND( ID_HELP_INDEX, OnHelpIndex )` Ihrer `CWinApp` Klassennachrichtenzuordnung eine Anweisung hinzufügen, um diese Memberfunktion zu aktivieren. Wenn diese Option aktiviert ist, ruft das Framework diese Message-Handler-Funktion `WinHelp` auf, wenn der Benutzer der Anwendung den Befehl Hilfeindex auswählt, der mit dem **StandardHELP_INDEX** Thema aufgerufen werden soll.

## <a name="cwinapponhelpusing"></a><a name="onhelpusing"></a>CWinApp::OnHelpUsing

Behandelt den Befehl ID_HELP_USING.

```
afx_msg void OnHelpUsing();
```

### <a name="remarks"></a>Bemerkungen

Sie müssen `ON_COMMAND( ID_HELP_USING, OnHelpUsing )` Ihrer `CWinApp` Klassennachrichtenzuordnung eine Anweisung hinzufügen, um diese Memberfunktion zu aktivieren. Das Framework ruft diese Message-Handler-Funktion auf, wenn der Benutzer `WinHelp` Ihrer Anwendung den Befehl Hilfe verwenden auswählt, um die Anwendung mit dem **StandardHELP_HELPONHELP** Thema aufzurufen.

## <a name="cwinapponidle"></a><a name="onidle"></a>CwinApp::OnIdle

Überschreiben Sie diese Memberfunktion, um die Verarbeitung im Leerlauf durchzuführen.

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>Parameter

*lCount*<br/>
Ein Zähler, der `OnIdle` jedes Mal erhöht wird, wenn die Nachrichtenwarteschlange der Anwendung leer ist. Diese Anzahl wird jedes Mal auf 0 zurückgesetzt, wenn eine neue Nachricht verarbeitet wird. Sie können den *Parameter lCount* verwenden, um die relative Dauer der Dauer zu bestimmen, für die sich die Anwendung im Leerlauf befindet, ohne eine Nachricht zu verarbeiten.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, um mehr Verarbeitungszeit im Leerlauf zu erhalten; 0, wenn keine Leerlaufzeit mehr benötigt wird.

### <a name="remarks"></a>Bemerkungen

`OnIdle`wird in der Standardnachrichtenschleife aufgerufen, wenn die Nachrichtenwarteschlange der Anwendung leer ist. Verwenden Sie Ihre Außerkraftsetzung, um Ihre eigenen Aufgaben im Leerlauf im Leerlauf aufzurufen.

`OnIdle`0 zurückgeben, um anzugeben, dass keine Verarbeitungszeit im Leerlauf erforderlich ist. Der *lCount-Parameter* wird `OnIdle` jedes Mal erhöht, wenn die Nachrichtenwarteschlange leer ist, und wird jedes Mal auf 0 zurückgesetzt, wenn eine neue Nachricht verarbeitet wird. Basierend auf dieser Anzahl können Sie Ihre verschiedenen Leerlaufroutinen aufrufen.

Im Folgenden werden die Verarbeitung von Leerlaufschleifen zusammengefasst:

1. Wenn die Nachrichtenschleife in der Microsoft Foundation-Klassenbibliothek die Nachrichtenwarteschlange `OnIdle` überprüft und keine ausstehenden Nachrichten findet, ruft sie das Anwendungsobjekt auf und gibt 0 als *lCount-Argument* an.

2. `OnIdle`führt eine Verarbeitung durch und gibt einen Wert ungleich Null zurück, um anzugeben, dass er erneut aufgerufen werden sollte, um die weitere Verarbeitung zu erledigen.

3. Die Nachrichtenschleife überprüft die Nachrichtenwarteschlange erneut. Wenn keine Nachrichten ausstehen, werden sie erneut aufruft, `OnIdle` wodurch das argument *lCount* erhöht wird.

4. Beendet `OnIdle` schließlich die Verarbeitung aller Aufgaben im Leerlauf und gibt 0 zurück. Dadurch wird die Nachrichtenschleife `OnIdle` aufgefordert, den Aufruf zu beenden, bis die nächste Nachricht von der Nachrichtenwarteschlange empfangen wird.

Führen Sie während `OnIdle` der Bearbeitung nicht lange `OnIdle` Aufgaben aus, da die Anwendung Benutzereingaben erst verarbeiten kann, wenn sie zurückgegeben wird.

> [!NOTE]
> Die Standardimplementierung `OnIdle` von Updates Befehl Benutzeroberflächenobjekte wie Menüelemente und Symbolleistenschaltflächen, und es führt interne Datenstruktur Bereinigung. Wenn Sie also `OnIdle`überschreiben, `CWinApp::OnIdle` müssen `lCount` Sie mit der in Ihrer überschriebenen Version aufrufen. Rufen Sie zuerst die gesamte Leerlaufverarbeitung der `OnIdle` Basisklasse auf (d. h. bis die Basisklasse 0 zurückgibt). Wenn Sie arbeiten müssen, bevor die Basisklassenverarbeitung abgeschlossen ist, überprüfen Sie die Basisklassenimplementierung, um den richtigen *lCount* auszuwählen, während derEr Ihre Arbeit ausführen soll.

Wenn Sie nicht `OnIdle` aufgerufen werden möchten, wenn eine Nachricht aus der Nachrichtenwarteschlange abgerufen wird, können Sie die [CWinThreadIsIdleMessage](../../mfc/reference/cwinthread-class.md#isidlemessage)überschreiben. Wenn eine Anwendung einen sehr kurzen Timer festgelegt hat oder wenn `OnIdle` das System die WM_SYSTIMER Nachricht sendet, wird die Leistung wiederholt aufgerufen und die Leistung beeinträchtigt.

### <a name="example"></a>Beispiel

Die folgenden beiden Beispiele `OnIdle`zeigen, wie . Im ersten Beispiel werden zwei Aufgaben im Leerlauf mithilfe des Arguments *lCount* verarbeitet, um die Aufgaben zu priorisieren. Die erste Aufgabe hat hohe Priorität, und Sie sollten es tun, wann immer möglich. Die zweite Aufgabe ist weniger wichtig und sollte nur ausgeführt werden, wenn die Benutzereingabe lange pausiert. Beachten Sie den Aufruf der `OnIdle`Basisklasseversion von . Im zweiten Beispiel wird eine Gruppe von Leerlaufaufgaben mit unterschiedlichen Prioritäten verwaltet.

[!code-cpp[NVC_MFCWindowing#51](../../mfc/reference/codesnippet/cpp/cwinapp-class_27.cpp)]

## <a name="cwinappopendocumentfile"></a><a name="opendocumentfile"></a>CWinApp::DocumentFile öffnen

Das Framework ruft diese Methode auf, um die benannte [CDocument-Datei](../../mfc/reference/cdocument-class.md) für die Anwendung zu öffnen.

```
virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszFileName
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>Parameter

*lpszFileName*<br/>
[in] Der Name der zu öffnenden Datei.

*bAddToMRU*<br/>
[in] TRUE gibt an, dass das Dokument eine der neuesten Dateien ist. FALSE gibt an, dass das Dokument nicht zu den neuesten Dateien gehört.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CDocument` ein, wenn erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Wenn ein Dokument mit diesem Namen bereits geöffnet ist, erhält das erste Rahmenfenster, das dieses Dokument enthält, den Fokus. Wenn eine Anwendung mehrere Dokumentvorlagen unterstützt, verwendet das Framework die Dateinamenerweiterung, um die entsprechende Dokumentvorlage zu suchen, um zu versuchen, das Dokument zu laden. Wenn dies erfolgreich ist, erstellt die Dokumentvorlage ein Rahmenfenster und eine Ansicht für das Dokument.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

## <a name="cwinappparsecommandline"></a><a name="parsecommandline"></a>CWinApp::ParseCommandLine

Rufen Sie diese Memberfunktion auf, um die Befehlszeile zu analysieren und die Parameter nacheinander an [CCommandLineInfo::ParseParam](../../mfc/reference/ccommandlineinfo-class.md#parseparam)zu senden.

```cpp
void ParseCommandLine(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>Parameter

*rCmdInfo*<br/>
Ein Verweis auf ein [CCommandLineInfo-Objekt.](../../mfc/reference/ccommandlineinfo-class.md)

### <a name="remarks"></a>Bemerkungen

Wenn Sie ein neues MFC-Projekt mit dem Anwendungs-Assistenten starten, erstellt der Anwendungs-Assistent eine lokale Instanz von `CCommandLineInfo`und ruft dann und `ProcessShellCommand` `ParseCommandLine` in der [InitInstance-Memberfunktion](#initinstance) auf. Eine Befehlszeile folgt der unten beschriebenen Route:

1. Nach dem `InitInstance`Erstellen `CCommandLineInfo` in wird `ParseCommandLine`das Objekt an übergeben.

2. `ParseCommandLine`ruft `CCommandLineInfo::ParseParam` dann wiederholt auf, einmal für jeden Parameter.

3. `ParseParam`füllt das `CCommandLineInfo` Objekt aus, das dann an [ProcessShellCommand](#processshellcommand)übergeben wird.

4. `ProcessShellCommand`behandelt die Befehlszeilenargumente und -flags.

Beachten Sie, `ParseCommandLine` dass Sie bei Bedarf direkt anrufen können.

Eine Beschreibung der Befehlszeilenflags finden Sie unter [CCommandLineInfo::m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand).

## <a name="cwinapppretranslatemessage"></a><a name="pretranslatemessage"></a>CWinApp::PReTranslateMessage

Überschreiben Sie diese Funktion, um Fenstermeldungen zu filtern, bevor sie an die Windows-Funktionen [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) und `CWinApp::PreTranslateMessage` [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) gesendet werden Die Standardimplementierung führt eine Beschleunigerschlüsselübersetzung durch, sodass Sie die Memberfunktion in Ihrer überschriebenen Version aufrufen müssen.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parameter

*pMsg*<br/>
Ein Zeiger auf eine [MSG-Struktur,](/windows/win32/api/winuser/ns-winuser-msg) die die zu verarbeitende Nachricht enthält.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, `PreTranslateMessage` wenn die Nachricht vollständig verarbeitet wurde und nicht weiter verarbeitet werden sollte. Null, wenn die Nachricht auf die normale Weise verarbeitet werden soll.

## <a name="cwinappprocessmessagefilter"></a><a name="processmessagefilter"></a>CWinApp::ProcessMessageFilter

Die Hook-Funktion des Frameworks ruft diese Memberfunktion auf, um bestimmte Windows-Nachrichten zu filtern und darauf zu reagieren.

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parameter

*code*<br/>
Gibt einen Hookcode an. Diese Memberfunktion verwendet den Code, um zu bestimmen, wie *lpMsg* verarbeitet wird.

*lpMsg*<br/>
Ein Zeiger auf [MSG](/windows/win32/api/winuser/ns-winuser-msg)eine Windows MSG-Truktur.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Nachricht verarbeitet wird; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Eine Hook-Funktion verarbeitet Ereignisse, bevor sie an die normale Nachrichtenverarbeitung der Anwendung gesendet werden.

Wenn Sie diese erweiterte Funktion überschreiben, rufen Sie die Basisklasseversion auf, um die Hook-Verarbeitung des Frameworks beizubehalten.

## <a name="cwinappprocessshellcommand"></a><a name="processshellcommand"></a>CWinApp::ProcessShellCommand

Diese Memberfunktion wird von [InitInstance](#initinstance) aufgerufen, `CCommandLineInfo` um die Parameter zu akzeptieren, die von dem von *rCmdInfo*identifizierten Objekt übergeben werden, und die angegebene Aktion auszuführen.

```
BOOL ProcessShellCommand(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>Parameter

*rCmdInfo*<br/>
Ein Verweis auf ein [CCommandLineInfo-Objekt.](../../mfc/reference/ccommandlineinfo-class.md)

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Shellbefehl erfolgreich verarbeitet wurde. Wenn 0, geben Sie FALSE von [InitInstance](#initinstance)zurück.

### <a name="remarks"></a>Bemerkungen

Wenn Sie ein neues MFC-Projekt mit dem Anwendungs-Assistenten starten, erstellt der Anwendungs-Assistent eine lokale Instanz von `CCommandLineInfo`und ruft dann [parseCommandLine](#parsecommandline) in der `InitInstance` Memberfunktion auf. `ProcessShellCommand` Eine Befehlszeile folgt der unten beschriebenen Route:

1. Nach dem `InitInstance`Erstellen `CCommandLineInfo` in wird `ParseCommandLine`das Objekt an übergeben.

2. `ParseCommandLine`ruft [dann CCommandLineInfo::ParseParam](../../mfc/reference/ccommandlineinfo-class.md#parseparam) wiederholt auf, einmal für jeden Parameter.

3. `ParseParam`füllt das `CCommandLineInfo` Objekt aus, das `ProcessShellCommand`dann an übergeben wird.

4. `ProcessShellCommand`behandelt die Befehlszeilenargumente und -flags.

Die Datenmember `CCommandLineInfo` des Objekts, die durch [CCommandLineInfo::m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand)identifiziert werden, sind vom `CCommandLineInfo` folgenden aufgezählten Typ, der innerhalb der Klasse definiert ist.

```
enum {
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE
    };
```

Eine kurze Beschreibung der einzelnen Werte `CCommandLineInfo::m_nShellCommand`finden Sie unter .

## <a name="cwinappprocesswndprocexception"></a><a name="processwndprocexception"></a>CWinApp::ProcessWndProcAusnahme

Das Framework ruft diese Memberfunktion auf, wenn der Handler keine Ausnahme abfängt, die in einem der Nachrichten- oder Befehlshandler Ihrer Anwendung ausgelöst wird.

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>Parameter

*E*<br/>
Ein Zeiger auf eine nicht abgefangene Ausnahme.

*pMsg*<br/>
Eine [MSG](/windows/win32/api/winuser/ns-winuser-msg)MSG-Truktur, die Informationen über die Windows-Meldung enthält, die dazu geführt hat, dass das Framework eine Ausnahme auslöst.

### <a name="return-value"></a>Rückgabewert

Der Wert, der an Windows zurückgegeben werden soll. Normalerweise ist dies 0L für Windows-Meldungen, 1L ( TRUE) für Befehlsmeldungen.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Memberfunktion nicht direkt auf.

Die Standardimplementierung dieser Memberfunktion erstellt ein Meldungsfeld. Wenn die nicht abgefangene Ausnahme von einem Menü-, Symbolleisten- oder Beschleunigerbefehlsfehler stammt, wird im Meldungsfeld die Meldung "Befehl fehlgeschlagen" angezeigt. Andernfalls wird die Meldung "Interner Anwendungsfehler" angezeigt.

Überschreiben Sie diese Memberfunktion, um eine globale Behandlung Ihrer Ausnahmen bereitzustellen. Rufen Sie die Basisfunktionalität nur auf, wenn das Meldungsfeld angezeigt werden soll.

## <a name="cwinappregister"></a><a name="register"></a>CWinApp::Registrieren

Führt alle Registrierungsaufgaben aus, die nicht von `RegisterShellFileTypes`behandelt werden.

```
virtual BOOL Register();
```

### <a name="return-value"></a>Rückgabewert

Bei Erfolg ein Wert ungleich 0 (null), andernfalls 0 (null).

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung gibt einfach TRUE zurück. Überschreiben Sie diese Funktion, um benutzerdefinierte Registrierungsschritte bereitzustellen.

## <a name="cwinappregistershellfiletypes"></a><a name="registershellfiletypes"></a>CWinApp::RegisterShellFileTypes

Rufen Sie diese Memberfunktion auf, um alle Dokumenttypen Ihrer Anwendung beim Windows-Datei-Manager zu registrieren.

```cpp
void RegisterShellFileTypes(BOOL bCompat = FALSE);
```

### <a name="parameters"></a>Parameter

*bCompat*<br/>
[in] TRUE fügt Registrierungseinträge für Shellbefehle Drucken und Drucken an hinzu, sodass ein Benutzer Dateien direkt aus der Shell drucken oder die Datei in ein Druckerobjekt ziehen kann. Außerdem wird ein DefaultIcon-Schlüssel hinzugefügt. Standardmäßig ist dieser Parameter aus Gründen der Abwärtskompatibilität FALSE.

### <a name="remarks"></a>Bemerkungen

Dadurch kann der Benutzer eine von Ihrer Anwendung erstellte Datendatei öffnen, indem er im Datei-Manager auf sie doppelklickt. Rufen `RegisterShellFileTypes` Sie auf, nachdem Sie [AddDocTemplate](#adddoctemplate) für jede der Dokumentvorlagen in Ihrer Anwendung aufrufen. Rufen Sie auch die [EnableShellOpen-Memberfunktion](#enableshellopen) auf, wenn Sie aufrufen. `RegisterShellFileTypes`

`RegisterShellFileTypes`durch die Liste der [CDocTemplate-Objekte,](../../mfc/reference/cdoctemplate-class.md) die von der Anwendung verwaltet werden, und fügt für jede Dokumentvorlage Einträge zur Registrierungsdatenbank hinzu, die Windows für Dateizuordnungen verwaltet. File Manager verwendet diese Einträge, um eine Datendatei zu öffnen, wenn der Benutzer darauf doppelklickt. Dadurch entfällt die Notwendigkeit, eine zu versenden. REG-Datei mit Ihrer Anwendung.

> [!NOTE]
> `RegisterShellFileTypes`funktioniert nur, wenn der Benutzer das Programm mit Administratorrechten ausführt. Wenn das Programm nicht über Administratorrechte verfügt, kann es die Registrierungsschlüssel nicht ändern.

Wenn die Registrierungsdatenbank bereits eine bestimmte Dateinamenerweiterung einem anderen Dateityp zuordnet, wird keine neue Zuordnung erstellt. In `CDocTemplate` der Klasse finden Sie das Format der Zeichenfolgen, die zum Registrieren dieser Informationen erforderlich sind.

## <a name="cwinappregisterwithrestartmanager"></a><a name="registerwithrestartmanager"></a>CWinApp::RegisterWithRestartManager

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
|Parameter|BESCHREIBUNG|
|*bRegisterRecoveryCallback*|[in] TRUE gibt an, dass diese Instanz der Anwendung eine Wiederherstellungsrückruffunktion verwendet. FALSE gibt an, dass dies nicht der Fall ist. Das Framework ruft die Wiederherstellungsrückruffunktion auf, wenn die Anwendung unerwartet beendet wird. Weitere Informationen finden Sie unter [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).|
|*strRestartIdentifier*|[in] Die eindeutige Zeichenfolge, die diese Instanz des Neustart-Managers identifiziert. Der Neustart-Manager-Bezeichner ist für jede Instanz einer Anwendung eindeutig.|
|*pwzCommandLineArgs*|[in] Eine Zeichenfolge, die zusätzliche Argumente aus der Befehlszeile enthält.|
|*dwRestartFlags*|[in] Optionale Flags für den Neustart-Manager. Weitere Informationen finden Sie im Abschnitt mit Hinweisen.|
|*pRecoveryCallback*|[in] Die Wiederherstellungsrückruffunktion. Diese Funktion muss einen LPVOID-Parameter als Eingabe verwenden und ein DWORD zurückgeben. Die standardmäßige Wiederherstellungsrückruffunktion ist `CWinApp::ApplicationRecoveryCallback`.|
|*lpvParam*|[in] Der Eingabeparameter für die Wiederherstellungsrückruffunktion. Weitere Informationen finden Sie unter [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).|
|*dwPingInterval*|[in] Die Zeitdauer, die der Neustart-Manager auf die Rückgabe der Wiederherstellungsrückruffunktion wartet. Dieser Parameter ist in Millisekunden angegeben.|
|*dwCallbackFlags*|[in] Flags, die an die Wiederherstellungsrückruffunktion übergeben werden. Für die zukünftige Verwendung reserviert.|

### <a name="return-value"></a>Rückgabewert

S_OK, wenn die Methode erfolgreich ist. andernfalls ein Fehlercode.

### <a name="remarks"></a>Bemerkungen

Wenn Ihre Anwendung die standardmäßige MFC-Implementierung zum automatischen Speichern `RegisterWithRestartManager`von Dateien verwendet, sollten Sie die einfache Version von verwenden. Verwenden Sie die `RegisterWithRestartManager` komplexe Version von , wenn Sie das Autosave-Verhalten Ihrer Anwendung anpassen möchten.

Wenn Sie diese Methode mit einer leeren `RegisterWithRestartManager` Zeichenfolge für *strRestartIdentifier*aufrufen, wird eine eindeutige Bezeichnerzeichenfolge für diese Instanz des Neustart-Managers erstellt.

Wenn eine Anwendung unerwartet beendet wird, startet der Neustart-Manager die Anwendung über die Befehlszeile neu und stellt den eindeutigen Neustartbezeichner als optionales Argument bereit. In diesem Szenario ruft `RegisterWithRestartManager` das Framework zweimal auf. Der erste Aufruf kommt von [CWinApp::InitInstance](#initinstance) mit einer leeren Zeichenfolge für den Zeichenfolgenbezeichner. Anschließend ruft `RegisterWithRestartManager` die Methode [CWinApp::ProcessShellCommand](#processshellcommand) mit dem eindeutigen Neustartbezeichner auf.

Nachdem Sie eine Anwendung beim Neustart-Manager registriert haben, überwacht der Neustart-Manager die Anwendung. Wenn die Anwendung unerwartet beendet wird, ruft der Neustart-Manager die Wiederherstellungsrückruffunktion während des Herunterfahrens auf. Der Neustart-Manager wartet das *dwPingInterval* auf eine Antwort von der Wiederherstellungsrückruffunktion. Wenn die Wiederherstellungsrückruffunktion nicht innerhalb dieser Zeit reagiert, wird die Anwendung beendet, ohne die Wiederherstellungsrückruffunktion auszuführen.

Standardmäßig werden die dwRestartFlags nicht unterstützt, aber für die zukünftige Verwendung bereitgestellt. Die möglichen Werte für *dwRestartFlags* sind wie folgt:

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

## <a name="cwinappreopenpreviousfilesatrestart"></a><a name="reopenpreviousfilesatrestart"></a>CWinApp::PreviousFilesAtRestart neu öffnen

Legt fest, ob der Neustart-Manager die Dateien erneut öffnet, die beim unerwarteten Beenden der Anwendung geöffnet wurden.

```
virtual BOOL ReopenPreviousFilesAtRestart() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE gibt an, dass der Neustart-Manager die zuvor geöffneten Dateien erneut öffnet. FALSE gibt an, dass der Neustart-Manager dies nicht tut.

## <a name="cwinapprestartinstance"></a><a name="restartinstance"></a>CWinApp::RestartInstance

Behandelt einen vom Neustart-Manager initiierten Anwendungsneustart.

```
virtual BOOL CWinApp::RestartInstance();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Datenwiederherstellungshandler zuvor geöffnete Dokumente öffnet; FALSE, wenn der Datenwiederherstellungshandler einen Fehler aufweist oder keine zuvor geöffneten Dokumente vorhanden sind.

### <a name="remarks"></a>Bemerkungen

Wenn der Neustart-Manager eine Anwendung neu startet, ruft das Framework diese Methode auf. Diese Methode ruft den Datenwiederherstellungshandler ab und stellt die automatisch gespeicherten Dateien wieder her. Diese Methode ruft [CDataRecoveryHandler::RestoreAutosavedDocuments](../../mfc/reference/cdatarecoveryhandler-class.md#restoreautosaveddocuments) auf, um zu bestimmen, ob der Benutzer die automatisch gespeicherten Dateien wiederherstellen möchte.

Diese Methode gibt FALSE zurück, wenn der [CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md) feststellt, dass keine geöffneten Dokumente vorhanden waren. Wenn keine offenen Dokumente vorhanden sind, beginnt die Anwendung normalerweise.

## <a name="cwinapprestoreautosavedfilesatrestart"></a><a name="restoreautosavedfilesatrestart"></a>CWinApp::RestoreAutosavedFilesAtRestart

Legt fest, ob der Neustart-Manager die automatisch gespeicherten Dateien wiederherstellt, wenn die Anwendung neu gestartet wird.

```
virtual BOOL RestoreAutosavedFilesAtRestart() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE gibt an, dass der Neustart-Manager automatisch gespeicherte Dateien wiederherstellt. FALSE gibt an, dass der Neustart-Manager dies nicht tut.

## <a name="cwinapprun"></a><a name="run"></a>CWinApp::Ausführen

Stellt eine Standardnachrichtenschleife bereit.

```
virtual int Run();
```

### <a name="return-value"></a>Rückgabewert

Ein **int-Wert,** `WinMain`der von zurückgegeben wird.

### <a name="remarks"></a>Bemerkungen

`Run`erfasst und sendet Windows-Nachrichten, bis die Anwendung eine WM_QUIT Nachricht empfängt. Wenn die Nachrichtenwarteschlange der Anwendung derzeit `Run` keine Nachrichten enthält, ruft [OnIdle](#onidle) auf, um die Verarbeitung im Leerlauf durchzuführen. Eingehende Nachrichten gehen zur speziellen Verarbeitung in die [PreTranslateMessage-Memberfunktion](#pretranslatemessage) und dann zur Windows-Funktion `TranslateMessage` für die Standardtastaturübersetzung. schließlich wird `DispatchMessage` die Windows-Funktion aufgerufen.

`Run`wird selten überschrieben, aber Sie können es überschreiben, um ein spezielles Verhalten bereitzustellen.

## <a name="cwinapprunautomated"></a><a name="runautomated"></a>CWinApp::RunAutomatisiert

Rufen Sie diese Funktion auf, um zu bestimmen, ob die Option " **/Automation**" oder " **-Automation**" vorhanden ist, was angibt, ob die Serveranwendung von einer Clientanwendung gestartet wurde.

```
BOOL RunAutomated();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Option gefunden wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Falls vorhanden, wird die Option aus der Befehlszeile entfernt. Weitere Informationen zu OLE Automation finden Sie im Artikel [Automatisierungsserver](../../mfc/automation-servers.md).

## <a name="cwinapprunembedded"></a><a name="runembedded"></a>CWinApp::RunEmbedded

Rufen Sie diese Funktion auf, um zu bestimmen, ob die Option " **/Embedding**" oder " **-Embedding**" vorhanden ist, was angibt, ob die Serveranwendung von einer Clientanwendung gestartet wurde.

```
BOOL RunEmbedded();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Option gefunden wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Falls vorhanden, wird die Option aus der Befehlszeile entfernt. Weitere Informationen zum Einbetten finden Sie im Artikel [Server: Implementieren eines Servers](../../mfc/servers-implementing-a-server.md).

## <a name="cwinappsaveallmodified"></a><a name="saveallmodified"></a>CWinApp::SaveAllModified

Wird vom Framework aufgerufen, um alle Dokumente zu speichern, wenn das Hauptrahmenfenster der Anwendung geschlossen werden soll, oder durch eine WM_QUERYENDSESSION Nachricht.

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn sicher, um die Anwendung zu beenden; 0, wenn nicht sicher, um die Anwendung zu beenden.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung dieser Memberfunktion ruft die [Memberfunktion CDocument::SaveModified](../../mfc/reference/cdocument-class.md#savemodified) für alle geänderten Dokumente in der Anwendung auf.

## <a name="cwinappselectprinter"></a><a name="selectprinter"></a>CWinApp::SelectPrinter

Rufen Sie diese Memberfunktion auf, um einen bestimmten Drucker auszuwählen, und lassen Sie den Drucker los, der zuvor im Feld Druckdialog ausgewählt wurde.

```cpp
void SelectPrinter(
    HANDLE hDevNames,
    HANDLE hDevMode,
    BOOL bFreeOld = TRUE);
```

### <a name="parameters"></a>Parameter

*hDevNames*<br/>
Ein Handle [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)für eine DEVNAMES-Trukture, das die Treiber-, Geräte- und Ausgabeanschlussnamen eines bestimmten Druckers identifiziert.

*hDevMode*<br/>
Ein Handle für eine [DEVMODE-Struktur,](/windows/win32/api/wingdi/ns-wingdi-devmodea) das Informationen über die Geräteinitialisierung und die Umgebung eines Druckers angibt.

*bFreeOld*<br/>
Gibt den zuvor ausgewählten Drucker frei.

### <a name="remarks"></a>Bemerkungen

Wenn *sowohl hDevMode als* auch `SelectPrinter` *hDevNames* NULL sind, wird der aktuelle Standarddrucker verwendet.

## <a name="cwinappsethelpmode"></a><a name="sethelpmode"></a>CWinApp::SetHelpMode

Legt den Hilfetyp der Anwendung fest.

```cpp
void SetHelpMode(AFX_HELP_TYPE eHelpType);
```

### <a name="parameters"></a>Parameter

*eHelpType*<br/>
Gibt den Typ der zu verwendenden Hilfe an. Weitere Informationen finden Sie unter [CWinApp::m_eHelpType.](#m_ehelptype)

### <a name="remarks"></a>Bemerkungen

Legt den Hilfetyp der Anwendung fest.

Um den Hilfetyp Ihrer Anwendung auf HTMLHelp festzulegen, können Sie [EnableHTMLHelp](#enablehtmlhelp)aufrufen. Nach dem `EnableHTMLHelp`Aufruf muss Ihre Anwendung HTMLHelp als Hilfeanwendung verwenden. Wenn Sie die Verwendung von WinHelp `SetHelpMode` ändern möchten, können `afxWinHelp`Sie *eHelpType* aufrufen und auf festlegen.

## <a name="cwinappsetregistrykey"></a><a name="setregistrykey"></a>CWinApp::SetRegistryKey

Bewirkt, dass Anwendungseinstellungen in der Registrierung anstelle von INI-Dateien gespeichert werden.

```cpp
void SetRegistryKey(LPCTSTR lpszRegistryKey);
void SetRegistryKey(UINT nIDRegistryKey);
```

### <a name="parameters"></a>Parameter

*lpszRegistryKey*<br/>
Zeiger auf eine Zeichenfolge, die den Namen des Schlüssels enthält.

*nIDRegistryKey*<br/>
ID einer Zeichenfolgenressource, die den Namen des Registrierungsschlüssels enthält.

### <a name="remarks"></a>Bemerkungen

Diese Funktion legt *m_pszRegistryKey*fest, `GetProfileInt`die `GetProfileString` `WriteProfileInt`dann `WriteProfileString` von den `CWinApp`, , , und Memberfunktionen von verwendet werden. Wenn diese Funktion aufgerufen wurde, wird auch die Liste der zuletzt verwendeten (MRU)-Dateien in der Registrierung gespeichert. Der Registrierungsschlüssel ist in der Regel der Name eines Unternehmens. Sie wird in einem Schlüssel des folgenden\\ Formulars\> \\ gespeichert:\> \\ HKEY_CURRENT_USER-Software\> \\<\>Firmenname<Anwendungsname<Abschnittsnamen<Wertname .

## <a name="cwinappsupportsapplicationrecovery"></a><a name="supportsapplicationrecovery"></a>CWinApp::UnterstütztApplicationRecovery

Bestimmt, ob der Neustart-Manager eine Anwendung wiederherstellt, die unerwartet beendet wurde.

```
virtual BOOL SupportsApplicationRecovery() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE gibt an, dass der Neustart-Manager die Anwendung wiederhergibt. FALSE gibt an, dass der Neustart-Manager dies nicht tut.

## <a name="cwinappsupportsautosaveatinterval"></a><a name="supportsautosaveatinterval"></a>CWinApp::UnterstütztAutosaveAtInterval

Bestimmt, ob der Neustart-Manager geöffnete Dokumente in einem regelmäßigen Intervall automatisch speichert.

```
virtual BOOL SupportsAutosaveAtInterval() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE gibt an, dass der Neustart-Manager geöffnete Dokumente automatisch speichert. FALSE gibt an, dass der Neustart-Manager dies nicht tut.

## <a name="cwinappsupportsautosaveatrestart"></a><a name="supportsautosaveatrestart"></a>CWinApp::UnterstütztAutosaveAtRestart

Bestimmt, ob der Neustart-Manager alle geöffneten Dokumente automatisch speichert, wenn die Anwendung neu gestartet wird.

```
virtual BOOL SupportsAutosaveAtRestart() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE gibt an, dass der Neustart-Manager geöffnete Dokumente automatisch speichert, wenn die Anwendung neu gestartet wird. FALSE gibt an, dass der Neustart-Manager dies nicht tut.

## <a name="cwinappsupportsrestartmanager"></a><a name="supportsrestartmanager"></a>CWinApp::UnterstütztRestartManager

Bestimmt, ob die Anwendung den Neustart-Manager unterstützt.

```
virtual BOOL SupportsRestartManager() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE gibt an, dass die Anwendung den Neustart-Manager unterstützt. FALSE gibt an, dass die Anwendung dies nicht tut.

## <a name="cwinappunregister"></a><a name="unregister"></a>CWinApp::Registrieren

Entregistriert alle Vom Anwendungsobjekt registrierten Dateien.

```
virtual BOOL Unregister();
```

### <a name="return-value"></a>Rückgabewert

Bei Erfolg ein Wert ungleich 0 (null), andernfalls 0 (null).

### <a name="remarks"></a>Bemerkungen

Die `Unregister` Funktion macht die vom Anwendungsobjekt und der [Registerfunktion](#register) ausgeführte Registrierung auf. Normalerweise werden beide Funktionen implizit von MFC aufgerufen und werden daher nicht im Code angezeigt.

Überschreiben Sie diese Funktion, um benutzerdefinierte Schritte zum Entmelden auszuführen.

## <a name="cwinappunregistershellfiletypes"></a><a name="unregistershellfiletypes"></a>CWinApp::ShellFileTypes aufheben

Rufen Sie diese Memberfunktion auf, um die Registrierung aller Dokumenttypen Ihrer Anwendung beim Windows-Datei-Manager aufzuheben.

```cpp
void UnregisterShellFileTypes();
```

## <a name="cwinappwinhelp"></a><a name="winhelp"></a>CWinApp::WinHelp

Rufen Sie diese Memberfunktion auf, um die WinHelp-Anwendung aufzurufen.

```
virtual void WinHelp(
    DWORD_PTR dwData,
    UINT nCmd = HELP_CONTEXT);
```

### <a name="parameters"></a>Parameter

*dwData*<br/>
Gibt zusätzliche Daten an. Der verwendete Wert hängt vom Wert des *parameters nCmd* ab.

*nCmd*<br/>
Gibt den Typ der angeforderten Hilfe an. Eine Liste möglicher Werte und deren Auswirkungen auf den *dwData-Parameter* finden Sie in der [WinHelp](/windows/win32/api/winuser/nf-winuser-winhelpw) Windows-Funktion.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Funktion auch auf, um die WinHelp-Anwendung aufzurufen.

Das Framework schließt die WinHelp-Anwendung automatisch, wenn die Anwendung beendet wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#53](../../mfc/reference/codesnippet/cpp/cwinapp-class_28.cpp)]

## <a name="cwinappwriteprofilebinary"></a><a name="writeprofilebinary"></a>CWinApp::WriteProfileBinary

Rufen Sie diese Memberfunktion auf, um Binärdaten in den angegebenen Abschnitt der Registrierung der Anwendung oder zu schreiben. INI-Datei.

```
BOOL WriteProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE pData,
    UINT nBytes);
```

### <a name="parameters"></a>Parameter

*lpszSection*<br/>
Zeigt auf eine auf NULL endende Zeichenfolge, die den Abschnitt mit dem Eintrag angibt. Wenn der Abschnitt nicht vorhanden ist, wird er erstellt. Der Name des Abschnitts ist großfliegt. Die Zeichenfolge kann eine beliebige Kombination aus Groß- und Kleinbuchstaben sein.

*lpszEntry*<br/>
Zeigt auf eine null-terminierte Zeichenfolge, die den Eintrag enthält, in den der Wert geschrieben werden soll. Wenn der Eintrag im angegebenen Abschnitt nicht vorhanden ist, wird er erstellt.

*pData*<br/>
Zeigt auf die zu schreibenden Daten.

*nBytes*<br/>
Enthält die Anzahl der zu schreibenden Bytes.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

In diesem `CWinApp* pApp = AfxGetApp();` Beispiel wird in der CWinApp-Klasse eine Weise veranschaulicht, die `WriteProfileBinary` von jeder Funktion in einer MFC-Anwendung verwendet werden `GetProfileBinary` kann.

[!code-cpp[NVC_MFCWindowing#54](../../mfc/reference/codesnippet/cpp/cwinapp-class_29.cpp)]

Ein weiteres Beispiel finden Sie im Beispiel für [CWinApp::GetProfileBinary](#getprofilebinary).

## <a name="cwinappwriteprofileint"></a><a name="writeprofileint"></a>CWinApp::WriteProfileInt

Rufen Sie diese Memberfunktion auf, um den angegebenen Wert in den angegebenen Abschnitt der Registrierung der Anwendung oder zu schreiben. INI-Datei.

```
BOOL WriteProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nValue);
```

### <a name="parameters"></a>Parameter

*lpszSection*<br/>
Zeigt auf eine auf NULL endende Zeichenfolge, die den Abschnitt mit dem Eintrag angibt. Wenn der Abschnitt nicht vorhanden ist, wird er erstellt. Der Name des Abschnitts ist großfliegt. Die Zeichenfolge kann eine beliebige Kombination aus Groß- und Kleinbuchstaben sein.

*lpszEntry*<br/>
Zeigt auf eine null-terminierte Zeichenfolge, die den Eintrag enthält, in den der Wert geschrieben werden soll. Wenn der Eintrag im angegebenen Abschnitt nicht vorhanden ist, wird er erstellt.

*nValue*<br/>
Enthält den zu schreibenden Wert.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

In diesem `CWinApp* pApp = AfxGetApp();` Beispiel wird in der CWinApp-Klasse `GetProfileString`eine `GetProfileInt` Weise veranschaulicht, wie `WriteProfileString`, `WriteProfileInt`, und von jeder Funktion in einer MFC-Anwendung verwendet werden kann.

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

Ein weiteres Beispiel finden Sie im Beispiel für [CWinApp::GetProfileInt](#getprofileint).

## <a name="cwinappwriteprofilestring"></a><a name="writeprofilestring"></a>CWinApp::WriteProfileString

Rufen Sie diese Memberfunktion auf, um die angegebene Zeichenfolge in den angegebenen Abschnitt der Registrierung der Anwendung oder zu schreiben. INI-Datei.

```
BOOL WriteProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszValue);
```

### <a name="parameters"></a>Parameter

*lpszSection*<br/>
Zeigt auf eine auf NULL endende Zeichenfolge, die den Abschnitt mit dem Eintrag angibt. Wenn der Abschnitt nicht vorhanden ist, wird er erstellt. Der Name des Abschnitts ist großfliegt. Die Zeichenfolge kann eine beliebige Kombination aus Groß- und Kleinbuchstaben sein.

*lpszEntry*<br/>
Zeigt auf eine null-terminierte Zeichenfolge, die den Eintrag enthält, in den der Wert geschrieben werden soll. Wenn der Eintrag im angegebenen Abschnitt nicht vorhanden ist, wird er erstellt. Wenn dieser Parameter NULL ist, wird der von *lpszSection* angegebene Abschnitt gelöscht.

*lpszValue*<br/>
Zeigt auf die zu schreibende Zeichenfolge. Wenn dieser Parameter NULL ist, wird der vom Parameter *lpszEntry* angegebene Eintrag gelöscht.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

Ein weiteres Beispiel finden Sie im Beispiel für [CWinApp::GetProfileInt](#getprofileint).

## <a name="cwinappsetappid"></a><a name="setappid"></a>CWinApp::SetAppID

Legt explizit die Anwendungsbenutzermodell-ID für die Anwendung fest. Diese Methode sollte aufgerufen werden, bevor dem Benutzer eine Benutzeroberfläche angezeigt wird (der beste Ort ist der Anwendungskonstruktor).

```cpp
void SetAppID(LPCTSTR lpcszAppID);
```

### <a name="parameters"></a>Parameter

*lpcszAppID*<br/>
Gibt die Anwendungsbenutzermodell-ID an.

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Weitere Informationen

[CWinThread-Klasse](../../mfc/reference/cwinthread-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Vorgehensweise: Hinzufügen von Unterstützung für den Neustart-Manager](../../mfc/how-to-add-restart-manager-support.md)
