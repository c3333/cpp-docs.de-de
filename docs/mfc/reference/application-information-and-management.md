---
title: Anwendungsinformationen und Anwendungsverwaltung
description: Verweis auf die MFC-Anwendungsinformationen und Verwaltungsfunktionen (Microsoft Foundation Class Library).
ms.date: 01/27/2020
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
ms.openlocfilehash: fc0b4b09f6c48da68bebe4a2825f49bcf6ab7e23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372497"
---
# <a name="application-information-and-management"></a>Anwendungsinformationen und Anwendungsverwaltung

Wenn Sie eine Anwendung schreiben, erstellen Sie ein einzelnes [CWinApp-abgeleitetes](../../mfc/reference/cwinapp-class.md)Objekt. Manchmal möchten Sie möglicherweise Informationen zu diesem Objekt `CWinApp`von außerhalb des -derived-Objekts abrufen. Oder Sie benötigen Zugriff auf andere globale "Manager"-Objekte.

Die Microsoft Foundation-Klassenbibliothek bietet die folgenden globalen Funktionen, die Sie bei der Erfüllung dieser Aufgaben unterstützen:

## <a name="application-information-and-management-functions"></a>Anwendungsinformationen und Managementfunktionen

|||
|-|-|
|[AfxBeginThread](#afxbeginthread)|Erstellt einen neuen Thread.|
|[AfxContextMenuManager](#afxcontextmenumanager)|Zeiger auf den globalen [Kontextmenü-Manager](ccontextmenumanager-class.md).|
|[AfxEndThread](#afxendthread)|Beendet den aktuellen Thread.|
|[AfxFindResourceHandle](#afxfindresourcehandle)|Führt die Ressourcenkette auf, und suchen Sie eine bestimmte Ressource nach Ressourcen-ID und Ressourcentyp. |
|[AfxFreeLibrary](#afxfreelibrary)|Dekrementiert die Referenzanzahl des geladenen DLL-Moduls (Dynamic Link Library). Wenn die Referenzanzahl Null erreicht, wird das Modul nicht zugeordnet.|
|[AfxGetApp](#afxgetapp)|Gibt einen Zeiger auf das `CWinApp` einzelne Objekt der Anwendung zurück.|
|[AfxGetAppName](#afxgetappname)|Gibt eine Zeichenfolge zurück, die den Namen der Anwendung enthält.|
|[AfxGetInstanceHandle](#afxgetinstancehandle)|Gibt eine HINSTANCE zurück, die diese Instanz der Anwendung darstellt.|
|[AfxGetMainWnd](#afxgetmainwnd)|Gibt einen Zeiger auf das aktuelle "Hauptfenster" einer Nicht-OLE-Anwendung oder das platznahe Rahmenfenster einer Serveranwendung zurück.|
|[AfxGetPerUserRegistration](#afxgetperuserregistration)|Verwenden Sie diese Funktion, um zu bestimmen, ob die Anwendung den Registrierungszugriff auf den **Knoten HKEY_CURRENT_USER** (**HKCU**) umleitet.|
|[AfxGetResourceHandle](#afxgetresourcehandle)|Gibt eine HINSTANCE an die Quelle der Standardressourcen der Anwendung zurück. Verwenden Sie diese Verbindung, um direkt auf die Ressourcen der Anwendung zuzugreifen.|
|[AfxGetThread](#afxgetthread)|Ruft einen Zeiger auf das aktuelle [CWinThread-Objekt](../../mfc/reference/cwinthread-class.md) ab.|
|[AfxInitRichEdit](#afxinitrichedit)|Initialisiert das Rich-Edit-Steuerelement version 1.0 für die Anwendung.|
|[AfxInitRichEdit2](#afxinitrichedit2)|Initialisiert die Version 2.0 und später rich edit control für die Anwendung.|
|[AfxIsExtendedFrameClass](#afxisextendedframeclass)|Bestimmt, ob das jeweilige Fenster ein erweitertes Rahmenobjekt ist.|
|[AfxIsMFCToolBar](#afxismfctoolbar)|Bestimmt, ob es sich bei dem angegebenen Fenster um ein Symbolleistenobjekt handelt.|
|[AfxKeyboardManager](#afxkeyboardmanager)|Zeiger auf den globalen [Tastaturmanager](ckeyboardmanager-class.md).|
|[AfxLoadLibrary](#afxloadlibrary)|Ordnet ein DLL-Modul zu und gibt ein Handle zurück, das zum Abrufen der Adresse einer DLL-Funktion verwendet werden kann.|
|[AfxLoadLibraryEx](#afxloadlibraryex)|Ordnet ein DLL-Modul mit den angegebenen Optionen zu und gibt ein Handle zurück, das zum Abrufen der Adresse einer DLL-Funktion verwendet werden kann.|
|[AfxMenuTearOffManager](#afxmenutearoffmanager)|Zeiger auf den globalen [Abreißmenü-Manager](cmenutearoffmanager-class.md).|
|[AfxMouseManager](#afxmousemanager)|Zeiger auf den globalen [Mausmanager](cmousemanager-class.md).|
|[AfxRegisterClass](#afxregisterclass)|Registriert eine Fensterklasse in einer DLL, die MFC verwendet.|
|[AfxRegisterWndClass](#afxregisterwndclass)|Registriert eine Windows-Fensterklasse, um die automatisch von MFC registrierten zu ergänzen.|
|[AfxSetPerUserRegistration](#afxsetperuserregistration)|Legt fest, ob die Anwendung den Registrierungszugriff auf den **HKEY_CURRENT_USER** -**HKCU**) -Knoten umleitet.|
|[AfxSetResourceHandle](#afxsetresourcehandle)|Legt das HINSTANCE-Handle fest, in das die Standardressourcen der Anwendung geladen werden.|
|[AfxShellManager](#afxshellmanager)|Zeiger auf den globalen [Shell-Manager](cshellmanager-class.md). |
|[AfxSocketInit](#afxsocketinit)|Wird in `CWinApp::InitInstance` einer Außerkraftsetzung aufgerufen, um Windows Sockets zu initialisieren.|
|[AfxUserToolsManager](#afxusertoolsmanager)|Zeiger auf den globalen [Benutzertools-Manager](cusertoolsmanager-class.md).|
|[AfxWinInit](#afxwininit)|Wird von der von `WinMain` MFC bereitgestellten Funktion als Teil der [CWinApp-Initialisierung](../../mfc/reference/cwinapp-class.md) einer GUI-basierten Anwendung aufgerufen, um MFC zu initialisieren. Muss direkt für Konsolenanwendungen aufgerufen werden, die MFC verwenden.|

## <a name="afxbeginthread"></a><a name="afxbeginthread"></a>Afxbeginthread

Rufen Sie diese Funktion auf, um einen neuen Thread zu erstellen.

```cpp
CWinThread* AfxBeginThread(
    AFX_THREADPROC pfnThreadProc,
    LPVOID pParam,
    int nPriority = THREAD_PRIORITY_NORMAL,
    UINT nStackSize = 0,
    DWORD dwCreateFlags = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);

CWinThread* AfxBeginThread(
    CRuntimeClass* pThreadClass,
    int nPriority = THREAD_PRIORITY_NORMAL,
    UINT nStackSize = 0,
    DWORD dwCreateFlags = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```

### <a name="parameters"></a>Parameter

*pfnThreadProc*\
Zeigt auf die Steuerungsfunktion für den Arbeitsthread. Der Zeiger kann nicht NULL sein. Diese Funktion muss wie folgt deklariert werden:

`UINT __cdecl MyControllingFunction( LPVOID pParam );`

*pThreadClass*\
Die RUNTIME_CLASS eines von [CWinThread](../../mfc/reference/cwinthread-class.md)abgeleiteten Objekts .

*pParam*\
Parameter, der an die steuernde Funktion übergeben werden soll.

*nPriorität*\
Die für den Thread festzulegende Priorität. Eine vollständige Liste und Beschreibung der verfügbaren Prioritäten finden Sie unter [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) im Windows SDK.

*nStackSize*\
Gibt die Stapelgröße für den neuen Thread in Bytes an. Mit dem Wert 0 wird die Stapelgröße standardmäßig so groß wie die des erstellenden Threads.

*dwCreateFlags*\
Gibt ein zusätzliches Flag an, das die Erstellung des Threads steuert. Dieses Flag kann einen von zwei Werten enthalten:

- CREATE_SUSPENDED Starten Sie den Thread mit einer Suspend-Anzahl von 1. Verwenden Sie CREATE_SUSPENDED, wenn Sie Memberdaten `CWinThread` des Objekts initialisieren möchten, z. B. [m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete) oder Member der abgeleiteten Klasse, bevor der Thread ausgeführt wird. Sobald die Initialisierung abgeschlossen ist, verwenden Sie [CWinThread::ResumeThread,](../../mfc/reference/cwinthread-class.md#resumethread) um die Threadausführung zu starten. Der Thread wird erst `CWinThread::ResumeThread` ausgeführt, wenn er aufgerufen wird.

- **0** Starten Sie den Thread unmittelbar nach der Erstellung.

*lpSecurityAttrs*\
Verweist auf eine [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) Struktur, die die Sicherheitsattribute für den Thread angibt. Wenn NULL, werden dieselben Sicherheitsattribute wie der erstellende Thread verwendet. Weitere Informationen zu dieser Struktur finden Sie im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Zeiger auf das neu erstellte Threadobjekt oder NULL, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Mit der ersten Form von `AfxBeginThread` wird ein Arbeitsthread erstellt. Mit der zweiten Form wird ein Thread erstellt, der als Benutzeroberflächenthread oder als Arbeitsthread dienen kann.

`AfxBeginThread`erstellt ein `CWinThread` neues Objekt, ruft seine [CreateThread-Funktion](../../mfc/reference/cwinthread-class.md#createthread) auf, um mit der Ausführung des Threads zu beginnen, und gibt einen Zeiger auf den Thread zurück. Während der gesamten Prozedur wird überprüft, ob alle Objekte ordnungsgemäß freigegeben werden, falls ein Teil des Erstellungsprozesses fehlschlagen sollte. Um den Thread zu beenden, rufen Sie [AfxEndThread](#afxendthread) aus dem Thread auf, oder kehren Sie von der Steuerungsfunktion des Arbeitsthreads zurück.

Multithreading muss durch die Anwendung aktiviert werden, andernfalls erzeugt diese Funktion einen Fehler. Weitere Informationen zum Aktivieren von Multithreading finden Sie unter [/MD, /MT, /LD (Laufzeitbibliothek verwenden)](../../build/reference/md-mt-ld-use-run-time-library.md).

Weitere Informationen `AfxBeginThread`zu finden Sie in den Artikeln [Multithreading: Erstellen von Arbeitsthreads](../../parallel/multithreading-creating-worker-threads.md) und [Multithreading: Erstellen von Benutzeroberflächenthreads](../../parallel/multithreading-creating-user-interface-threads.md).

### <a name="example"></a>Beispiel

Siehe Beispiel für [CSocket::Attach](../../mfc/reference/csocket-class.md#attach).

### <a name="requirements"></a>Anforderungen

  **Header** afxwin.h

## <a name="afxcontextmenumanager"></a><a name="afxcontextmenumanager"></a>AfxContextMenuManager

Zeiger auf den globalen [Kontextmenü-Manager](ccontextmenumanager-class.md).

### <a name="syntax"></a>Syntax

```cpp
CContextMenuManager* afxContextMenuManager;
```

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxcontextmenumanager.h

## <a name="afxendthread"></a><a name="afxendthread"></a>AfxEndThread

Rufen Sie diese Funktion auf, um den aktuell ausgeführten Thread zu beenden.

```cpp
void AFXAPI AfxEndThread(
    UINT nExitCode,
    BOOL bDelete  = TRUE);
```

### <a name="parameters"></a>Parameter

*nExitCode*\
Gibt den Exitcode des Threads an.

*bLöschen*\
Löscht das Threadobjekt aus dem Speicher.

### <a name="remarks"></a>Bemerkungen

Muss innerhalb des Threads aufgerufen werden, um beendet zu werden.

Weitere Informationen `AfxEndThread`finden Sie im Artikel [Multithreading: Beenden von Threads](../../parallel/multithreading-terminating-threads.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxwin.h

## <a name="afxfindresourcehandle"></a><a name="afxfindresourcehandle"></a>AfxFindResourceHandle

Verwenden `AfxFindResourceHandle` Sie diese Datei, um die Ressourcenkette zu wechseln und eine bestimmte Ressource nach Ressourcen-ID und Ressourcentyp zu suchen.

### <a name="syntax"></a>Syntax

```cpp
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );
```

### <a name="parameters"></a>Parameter

*lpszName*\
Ein Zeiger auf eine Zeichenfolge, die die Ressourcen-ID enthält.
*lpszType*\
Ein Zeiger auf den Ressourcentyp. Eine Liste der Ressourcentypen finden Sie unter [FindResource](/windows/win32/api/winbase/nf-winbase-findresourcea) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ein Handle für das Modul, das die Ressource enthält.

### <a name="remarks"></a>Bemerkungen

`AfxFindResourceHandle`sucht die spezifische Ressource und gibt ein Handle an das Modul zurück, das die Ressource enthält. Die Ressource befindet sich möglicherweise in einer beliebigen MFC-Erweiterungs-DLL, die geladen wird. `AfxFindResourceHandle`sagt Ihnen, welche Ressource hat.

Die Module werden in dieser Reihenfolge durchsucht:

1. Das Hauptmodul, wenn es sich um eine MFC-Erweiterungs-DLL handelt.

1. Nicht-Systemmodule.

1. Sprachspezifische Module.

1. Das Hauptmodul, wenn es sich um eine System-DLL handelt.

1. Systemmodule.

### <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="afxfreelibrary"></a><a name="afxfreelibrary"></a>Afxfreelibrary

Beide `AfxFreeLibrary` `AfxLoadLibrary` und verwalten eine Referenzanzahl für jedes geladene Bibliotheksmodul.

```cpp
BOOL AFXAPI AfxFreeLibrary(HINSTANCE hInstLib);
```

### <a name="parameters"></a>Parameter

*hInstLib*\
Ein Handle des geladenen Bibliotheksmoduls. [AfxLoadLibrary](#afxloadlibrary) gibt dieses Handle zurück.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Funktion erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

`AfxFreeLibrary`dekrementiert die Referenzanzahl des geladenen DLL-Moduls (Dynamic Link Library). Wenn die Referenzanzahl Null erreicht, wird das Modul aus dem Adressraum des aufrufenden Prozesses nicht zugeordnet, und das Handle ist nicht mehr gültig. Diese Referenzanzahl wird bei `AfxLoadLibrary` jedem Aufruf erhöht.

Vor dem Aufheben der Zuordnung eines Bibliotheksmoduls ermöglicht das System der DLL, sich von den Prozessen zu lösen, die es verwenden. Auf diese Weise bietet die DLL die Möglichkeit, die für den aktuellen Prozess zugewiesenen Ressourcen zu bereinigen. Nachdem die Einstiegspunktfunktion zurückgegeben wurde, wird das Bibliotheksmodul aus dem Adressraum des aktuellen Prozesses entfernt.

Verwenden `AfxLoadLibrary` Sie diese Datei, um ein DLL-Modul zuzuordnen.

Achten Sie `AfxFreeLibrary` darauf, und `AfxLoadLibrary` (anstelle der `FreeLibrary` `LoadLibrary`Win32-Funktionen und ) zu verwenden, wenn Ihre Anwendung mehrere Threads verwendet. Verwenden `AfxLoadLibrary` `AfxFreeLibrary` und stellt sicher, dass der Start- und Herunterfahrcode, der ausgeführt wird, wenn die MFC-Erweiterungs-DLL geladen und entladen wird, den globalen MFC-Status nicht beschädigt.

### <a name="example"></a>Beispiel

Siehe Beispiel für [AfxLoadLibrary](#afxloadlibrary).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdll_.h

## <a name="afxgetapp"></a><a name="afxgetapp"></a>AfxGetApp

Der von dieser Funktion zurückgegebene Zeiger kann für den Zugriff auf Anwendungsinformationen wie den Hauptnachrichtenversandcode oder das oberste Fenster verwendet werden.

```cpp
CWinApp* AFXAPI AfxGetApp();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CWinApp` das einzelne Objekt für die Anwendung.

### <a name="remarks"></a>Bemerkungen

Wenn diese Methode NULL zurückgibt, kann dies darauf hinweisen, dass das Hauptfenster der Anwendung noch nicht vollständig initialisiert wurde. Es kann auch auf ein Problem hinweisen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#126](../../mfc/reference/codesnippet/cpp/application-information-and-management_1.cpp)]

### <a name="requirements"></a>Anforderungen

  **Header** afxwin.h

## <a name="afxgetappname"></a><a name="afxgetappname"></a>AfxGetAppName

Die zurückgegebene Zeichenfolge kann für Diagnosemeldungen oder als Stamm für temporäre Zeichenfolgennamen verwendet werden.

```cpp
LPCTSTR AFXAPI AfxGetAppName();
```

### <a name="return-value"></a>Rückgabewert

Eine null-terminierte Zeichenfolge, die den Namen der Anwendung enthält.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#127](../../mfc/reference/codesnippet/cpp/application-information-and-management_2.cpp)]

### <a name="requirements"></a>Anforderungen

  **Header** afxwin.h

## <a name="afxgetinstancehandle"></a><a name="afxgetinstancehandle"></a>AfxGetInstanceHandle

Mit dieser Funktion können Sie das Instanzhandle der aktuellen Anwendung abrufen.

```cpp
HINSTANCE  AFXAPI AfxGetInstanceHandle();
```

### <a name="return-value"></a>Rückgabewert

Eine HINSTANCE für die aktuelle Instanz der Anwendung. Wenn innerhalb einer DLL aufgerufen wird, die mit der USRDLL-Version von MFC verknüpft ist, wird eine HINSTANCE an die DLL zurückgegeben.

### <a name="remarks"></a>Bemerkungen

`AfxGetInstanceHandle`gibt immer die HINSTANCE Ihrer ausführbaren Datei zurück (. EXE), es sei denn, es wird innerhalb einer DLL aufgerufen, die mit der USRDLL-Version von MFC verknüpft ist. In diesem Fall wird eine HINSTANCE an die DLL zurückgegeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]

### <a name="requirements"></a>Anforderungen

  **Header** afxwin.h

## <a name="afxgetmainwnd"></a><a name="afxgetmainwnd"></a>AfxGetMainWnd

Wenn es sich bei Ihrer Anwendung um einen OLE-Server handelt, rufen Sie diese Funktion auf, um einen Zeiger auf das aktive Hauptfenster der Anwendung abzurufen. Verwenden Sie dieses Ergebnis, anstatt direkt auf das [m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd) Member des Anwendungsobjekts zu verweisen.

```cpp
CWnd* AFXAPI AfxGetMainWnd();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf das Rahmenfensterobjekt zurück, das das aktive Dokument an Ort und Stelle enthält, wenn der Server über ein Objekt verfügt, das in einem aktiven Container aktiv ist.

Wenn in einem Container kein Objekt vorhanden ist, das in einem Container aktiv ist, oder ihre Anwendung kein OLE-Server ist, gibt diese Funktion die *m_pMainWnd* des Anwendungsobjekts zurück.

Wenn `AfxGetMainWnd` vom primären Thread der Anwendung aufgerufen wird, wird das Hauptfenster der Anwendung gemäß den oben genannten Regeln zurückgegeben. Wenn die Funktion von einem sekundären Thread in der Anwendung aufgerufen wird, gibt die Funktion das Hauptfenster zurück, das dem aufrufenden Thread zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Wenn es sich bei Ihrer Anwendung nicht um einen OLE-Server handelt, entspricht das Aufrufen dieser Funktion dem direkten Verweis auf das *m_pMainWnd-Member* des Anwendungsobjekts.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#129](../../mfc/reference/codesnippet/cpp/application-information-and-management_4.cpp)]

### <a name="requirements"></a>Anforderungen

  **Header** afxwin.h

## <a name="afxgetperuserregistration"></a><a name="afxgetperuserregistration"></a>AfxGetPerUserRegistrierung

Verwenden Sie diese Funktion, um zu bestimmen, ob die Anwendung den Registrierungszugriff auf den **Knoten HKEY_CURRENT_USER** (**HKCU**) umleitet.

```cpp
BOOL AFXAPI AfxGetPerUserRegistration();
```

### <a name="return-value"></a>Rückgabewert

TRUE gibt an, dass die Registrierungsinformationen an den HKCU-Knoten weitergeleitet werden. FALSE gibt an, dass die Anwendung Registrierungsinformationen auf den Standardknoten schreibt. Der Standardknoten ist **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="remarks"></a>Bemerkungen

Wenn Sie die Registrierungsumleitung aktivieren, leitet das Framework den Zugriff von **HKCR** auf **HKEY_CURRENT_USER-Software-Klassen**um. Nur die MFC- und ATL-Frameworks sind von der Umleitung betroffen.

Um zu ändern, ob die Anwendung den Registrierungszugriff umleitet, verwenden Sie [AfxSetPerUserRegistration](#afxsetperuserregistration).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxstat_.h

## <a name="afxgetresourcehandle"></a><a name="afxgetresourcehandle"></a>AfxGetResourceHandle

Verwenden Sie das von dieser Funktion zurückgegebene HINSTANCE-Handle, um direkt auf `FindResource`die Ressourcen der Anwendung zuzugreifen, z. B. in Aufrufen der Windows-Funktion .

```cpp
extern HINSTANCE  AfxGetResourceHandle();
```

### <a name="return-value"></a>Rückgabewert

Ein HINSTANCE-Handle, bei dem die Standardressourcen der Anwendung geladen werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]

### <a name="requirements"></a>Anforderungen

  **Header** afxwin.h

## <a name="afxgetthread"></a><a name="afxgetthread"></a>AfxGetThread

Rufen Sie diese Funktion auf, um einen Zeiger auf das [CWinThread-Objekt](../../mfc/reference/cwinthread-class.md) abzurufen, das den aktuell ausgeführten Thread darstellt.

```cpp
CWinThread* AfxGetThread();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf den aktuell ausgeführten Thread; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Muss innerhalb des Threads aufgerufen werden.

> [!NOTE]
> Wenn Sie ein MFC-Projekt `AfxGetThread` portieren, das von Visual C++-Versionen 4.2, 5.0 oder 6.0 aufgerufen wird, `AfxGetThread` ruft [AfxGetApp](#afxgetapp) auf, wenn kein Thread gefunden wird. Gibt in neueren Versionen `AfxGetThread` des Compilers NULL zurück, wenn kein Thread gefunden wurde. Wenn Sie den Anwendungsthread verwenden `AfxGetApp`möchten, müssen Sie aufrufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]

### <a name="requirements"></a>Anforderungen

  **Header** afxwin.h

## <a name="afxinitrichedit"></a><a name="afxinitrichedit"></a>AfxInitRichBearbeiten

Rufen Sie diese Funktion auf, um das Rich-Edit-Steuerelement (Version 1.0) für die Anwendung zu initialisieren.

```cpp
BOOL AFXAPI AfxInitRichEdit();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist für die Abwärtskompatibilität vorgesehen. Neue Anwendungen sollten [AfxInitRichEdit2](#afxinitrichedit2)verwenden.

`AfxInitRichEdit`LASTEN RICHED32. DLL, um Version 1.0 des Rich-Edit-Steuerelements zu initialisieren. Um Version 2.0 und 3.0 des Rich-Edit-Steuerelements zu verwenden, RICHED20. DLL muss geladen werden. Es wird geladen, indem ein Aufruf von [AfxInitRichEdit2](#afxinitrichedit2).

Um umfangreiche Bearbeitungssteuerelemente in vorhandenen Visual C++-Anwendungen auf Version 2.0 zu aktualisieren, öffnen Sie die . RC-Datei als Text, ändern Sie den Klassennamen jedes Rich-Edit-Steuerelement von "RICHEDIT" in "RichEdit20a". Ersetzen Sie dann `AfxInitRichEdit` `AfxInitRichEdit2`den Aufruf an durch .

Diese Funktion initialisiert auch die allgemeine Steuerelementbibliothek, wenn die Bibliothek noch nicht für den Prozess initialisiert wurde. Wenn Sie das Rich-Edit-Steuerelement direkt aus Ihrer MFC-Anwendung verwenden, rufen Sie diese Funktion auf, um sicherzustellen, dass MFC die Laufzeit des Rich-Edit-Steuerelements ordnungsgemäß initialisiert hat. Wenn Sie `Create` die Methode [von CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md)oder [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)aufrufen, müssen Sie diese Funktion in der Regel nicht aufrufen, aber in einigen Fällen kann es notwendig sein.

### <a name="requirements"></a>Anforderungen

  **Header** afxwin.h

## <a name="afxinitrichedit2"></a><a name="afxinitrichedit2"></a>AfxInitRichBearbeiten2

Rufen Sie diese Funktion auf, um das Rich-Edit-Steuerelement (Version 2.0 und höher) für die Anwendung zu initialisieren.

```cpp
BOOL AFXAPI AfxInitRichEdit2();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um den RICHED20 zu laden. DLL und initialisieren Version 2.0 des Rich Edit-Steuerelements. Wenn Sie `Create` die Methode [von CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md)oder [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)aufrufen, müssen Sie diese Funktion in der Regel nicht aufrufen, aber in einigen Fällen kann es notwendig sein.

### <a name="requirements"></a>Anforderungen

  **Header** afxwin.h

## <a name="afxisextendedframeclass"></a><a name="afxisextendedframeclass"></a>AfxIsExtendedFrameClass

Bestimmt, ob das jeweilige Fenster ein erweitertes Rahmenobjekt ist.

### <a name="syntax"></a>Syntax

```cpp
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );
```

### <a name="parameters"></a>Parameter

*pWnd*\
[in] Ein Zeiger auf ein Objekt, `CWnd`das von abgeleitet wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das bereitgestellte Fenster ein erweitertes Frameobjekt ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt TRUE zurück, wenn *pWnd* von einer der folgenden Klassen ableitet:

- `CFrameWndEx`

- `CMDIFrameWndEx`

- `COleIPFrameWndEx`

- `COleDocIPFrameWndEx`

- `CMDIChildWndEx`

Diese Methode ist nützlich, wenn Sie überprüfen müssen, ob ein Funktions- oder Methodenparameter ein erweitertes Rahmenfenster ist.

### <a name="requirements"></a>Anforderungen

**Header:** „afxpriv.h“

## <a name="afxismfctoolbar"></a><a name="afxismfctoolbar"></a>AfxIsMFCToolBar

Bestimmt, ob es sich bei dem angegebenen Fenster um ein Symbolleistenobjekt handelt.

### <a name="syntax"></a>Syntax

```cpp
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*pWnd*\
[in] Ein Zeiger auf ein Objekt, `CWnd`das von abgeleitet wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das bereitgestellte Fenster ein Symbolleistenobjekt ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode `TRUE` wird zurückgegeben, wenn `CMFCToolBar` *pWnd* von ableitet. Diese Methode ist nützlich, wenn Sie überprüfen müssen, `CMFCToolBar` ob ein Funktions- oder Methodenparameter ein Objekt ist.

### <a name="requirements"></a>Anforderungen

**Header:** „afxpriv.h“

## <a name="afxkeyboardmanager"></a><a name="afxkeyboardmanager"></a>AfxKeyboardManager

Zeiger auf den globalen [Tastaturmanager](ckeyboardmanager-class.md).

### <a name="syntax"></a>Syntax

```cpp
CKeyboardManager* afxKeyboardManager;
```

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxkeyboardmanager.h

## <a name="afxloadlibrary"></a><a name="afxloadlibrary"></a>AfxLoadLibrary

Verwenden `AfxLoadLibrary` Sie diese Datei, um ein DLL-Modul zuzuordnen.

```cpp
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName);
```

### <a name="parameters"></a>Parameter

*lpszModuleName*\
Zeigt auf eine null-terminierte Zeichenfolge, die den Namen des Moduls enthält (entweder eine . DLL oder . EXE-Datei). Der angegebene Name ist der Dateiname des Moduls.

Wenn die Zeichenfolge einen Pfad angibt, die Datei jedoch nicht im angegebenen Verzeichnis vorhanden ist, schlägt die Funktion fehl.

Wenn kein Pfad angegeben ist und die Dateinamenerweiterung weggelassen wird, wird die Standarderweiterung . DLL wird angehängt. Die Dateinamenzeichenfolge kann jedoch ein nachgestelltes Punktzeichen (.) enthalten, um anzugeben, dass der Modulname keine Erweiterung hat. Wenn kein Pfad angegeben ist, verwendet die Funktion die [Suchreihenfolge für Desktopanwendungen](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications).

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, ist der Rückgabewert ein Handle für das Modul. Bei einem Fehler ist der Rückgabewert NULL.

### <a name="remarks"></a>Bemerkungen

Es gibt ein Handle zurück, das in [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) verwendet werden kann, um die Adresse einer DLL-Funktion abrufe. `AfxLoadLibrary`kann auch verwendet werden, um andere ausführbare Module zuzuordnen.

Jeder Prozess verwaltet eine Referenzanzahl für jedes geladene Bibliotheksmodul. Diese Referenzanzahl wird jedes `AfxLoadLibrary` Mal erhöht, wenn sie `AfxFreeLibrary` aufgerufen wird, und wird jedes Mal verringert, wenn sie aufgerufen wird. Wenn die Referenzanzahl Null erreicht, wird das Modul aus dem Adressraum des aufrufenden Prozesses nicht zugeordnet, und das Handle ist nicht mehr gültig.

Achten Sie `AfxLoadLibrary` darauf, und `AfxFreeLibrary` (anstelle der `LoadLibrary` `FreeLibrary`Win32-Funktionen und ) zu verwenden, wenn Ihre Anwendung mehrere Threads verwendet und wenn sie dynamisch eine MFC-Erweiterungs-DLL lädt. Durch `AfxLoadLibrary` `AfxFreeLibrary` die Verwendung und Die Versicherung wird sichergestellt, dass der Start- und Herunterfahrcode, der ausgeführt wird, wenn die MFC-Erweiterungs-DLL geladen und entladen wird, den globalen MFC-Status nicht beschädigt.

Für `AfxLoadLibrary` die Verwendung in einer Anwendung müssen Sie dynamisch eine Verknüpfung mit der DLL-Version von MFC herstellen. Die Headerdatei `AfxLoadLibrary`für , Afxdll_.h, ist nur enthalten, wenn MFC als DLL mit der Anwendung verknüpft ist. Diese Anforderung ist beabsichtigt, da Sie eine Verknüpfung mit der DLL-Version von MFC herstellen müssen, um MFC-Erweiterungs-DLLs zu verwenden oder zu erstellen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_DLLUser#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]
[!code-cpp[NVC_MFC_DLLUser#2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]
[!code-cpp[NVC_MFC_DLLUser#3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdll_.h

## <a name="afxloadlibraryex"></a><a name="afxloadlibraryex"></a>AfxLoadLibraryEx

Verwenden `AfxLoadLibraryEx` Sie diese Datei, um ein DLL-Modul zuzuordnen.

```cpp
HINSTANCE AFXAPI AfxLoadLibraryEx(LPCTSTR lpFileName, HANDLE hFile, DWORD dwFlags);
```

### <a name="parameters"></a>Parameter

*lpFileName*\
Zeigt auf eine null-terminierte Zeichenfolge, die den Namen des Moduls enthält (entweder eine . DLL oder . EXE-Datei). Der angegebene Name ist der Dateiname des Moduls.

Wenn die Zeichenfolge einen Pfad angibt, die Datei jedoch nicht im angegebenen Verzeichnis vorhanden ist, schlägt die Funktion fehl.

Wenn kein Pfad angegeben ist und die Dateinamenerweiterung weggelassen wird, wird die Standarderweiterung . DLL wird angehängt. Die Dateinamenzeichenfolge kann jedoch ein nachgestelltes Punktzeichen (.) enthalten, um anzugeben, dass der Modulname keine Erweiterung hat. Wenn kein Pfad angegeben ist, verwendet die Funktion die [Suchreihenfolge für Desktopanwendungen](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications).

*hDatei*\
Dieser Parameter ist für die zukünftige Verwendung reserviert. Es muss NULL sein.

*Dwflags*\
Die beim Laden des Moduls zu ergreifende Aktion. Wenn keine Flags angegeben sind, ist das `AfxLoadLibrary` Verhalten dieser Funktion mit der Funktion identisch. Die möglichen Werte dieses Parameters werden in der [LoadLibraryEx-Dokumentation](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) beschrieben.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, ist der Rückgabewert ein Handle für das Modul. Bei einem Fehler ist der Rückgabewert NULL.

### <a name="remarks"></a>Bemerkungen

`AfxLoadLibraryEx`gibt ein Handle zurück, das in [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) verwendet werden kann, um die Adresse einer DLL-Funktion abzufragen. `AfxLoadLibraryEx`kann auch verwendet werden, um andere ausführbare Module zuzuordnen.

Jeder Prozess verwaltet eine Referenzanzahl für jedes geladene Bibliotheksmodul. Diese Referenzanzahl wird jedes `AfxLoadLibraryEx` Mal erhöht, wenn sie `AfxFreeLibrary` aufgerufen wird, und wird jedes Mal verringert, wenn sie aufgerufen wird. Wenn die Referenzanzahl Null erreicht, wird das Modul aus dem Adressraum des aufrufenden Prozesses nicht zugeordnet, und das Handle ist nicht mehr gültig.

Achten Sie `AfxLoadLibraryEx` darauf, und `AfxFreeLibrary` (anstelle der `LoadLibraryEx` `FreeLibrary`Win32-Funktionen und ) zu verwenden, wenn Ihre Anwendung mehrere Threads verwendet und wenn sie dynamisch eine MFC-Erweiterungs-DLL lädt. Verwenden `AfxLoadLibraryEx` `AfxFreeLibrary` und stellt sicher, dass der Start- und Herunterfahrcode, der ausgeführt wird, wenn die MFC-Erweiterungs-DLL geladen und entladen wird, den globalen MFC-Status nicht beschädigt.

Für `AfxLoadLibraryEx` die Verwendung in einer Anwendung müssen Sie dynamisch eine Verknüpfung mit der DLL-Version von MFC herstellen. Die Headerdatei `AfxLoadLibraryEx`für , Afxdll_.h, ist nur enthalten, wenn MFC als DLL mit der Anwendung verknüpft ist. Diese Anforderung ist beabsichtigt, da Sie eine Verknüpfung mit der DLL-Version von MFC herstellen müssen, um MFC-Erweiterungs-DLLs zu verwenden oder zu erstellen.

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdll_.h

## <a name="afxmenutearoffmanager"></a><a name="afxmenutearoffmanager"></a>AfxMenuTearOffManager

Zeiger auf den globalen [Abreißmenü-Manager](cmenutearoffmanager-class.md).

### <a name="syntax"></a>Syntax

```cpp
CMenuTearOffManager* g_pTearOffMenuManager;
```

### <a name="requirements"></a>Anforderungen

**Kopf:** afxmenutearoffmanager.h

## <a name="afxmousemanager"></a><a name="afxmousemanager"></a>AfxMouseManager

Zeiger auf den globalen [Mausmanager](cmousemanager-class.md).

### <a name="syntax"></a>Syntax

```cpp
CMouseManager* afxMouseManager;
```

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxmousemanager.h

## <a name="afxregisterclass"></a><a name="afxregisterclass"></a>AfxRegisterClass

Verwenden Sie diese Funktion, um Fensterklassen in einer DLL zu registrieren, die MFC verwendet.

```cpp
BOOL AFXAPI AfxRegisterClass(WNDCLASS* lpWndClass);
```

### <a name="parameters"></a>Parameter

*lpWndKlasse*\
Zeiger auf eine [WNDCLASS-Struktur,](/windows/win32/api/winuser/ns-winuser-wndclassw) die Informationen über die zu registrierende Fensterklasse enthält. Weitere Informationen zu dieser Struktur finden Sie im Windows SDK.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Klasse erfolgreich registriert wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Wenn Sie diese Funktion verwenden, wird die Registrierung der Klasse automatisch abgemeldet, wenn die DLL entladen wird.

In Nicht-DLL-Builds `AfxRegisterClass` wird der Bezeichner als Makro `RegisterClass`definiert, das der Windows-Funktion zugeordnet ist, da in einer Anwendung registrierte Klassen automatisch nicht registriert werden. Wenn Sie `AfxRegisterClass` anstelle `RegisterClass`von verwenden, kann der Code ohne Änderung sowohl in einer Anwendung als auch in einer DLL verwendet werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_DLL#3](../../atl-mfc-shared/codesnippet/cpp/application-information-and-management_10.cpp)]

### <a name="requirements"></a>Anforderungen

  **Header** afxwin.h

## <a name="afxregisterwndclass"></a><a name="afxregisterwndclass"></a>AfxRegisterWndClass

Ermöglicht es Ihnen, Ihre eigenen Fensterklassen zu registrieren.

```cpp
LPCTSTR AFXAPI AfxRegisterWndClass(
    UINT nClassStyle,
    HCURSOR hCursor = 0,
    HBRUSH hbrBackground = 0,
    HICON hIcon = 0);
```

### <a name="parameters"></a>Parameter

*nClassStyle*\
Gibt den Windows-Klassenstil oder die Kombination von Stilen an, die mithilfe des Operators bitweise-ODER (**&#124;**) für die Fensterklasse erstellt wurden. Eine Liste der Klassenstile finden Sie in der [WNDCLASS-Struktur](/windows/win32/api/winuser/ns-winuser-wndclassw) im Windows SDK. Wenn NULL, werden die Standardwerte wie folgt festgelegt:

- Legt den Mausstil auf CS_DBLCLKS fest, der Doppelklicknachrichten an die Fensterprozedur sendet, wenn der Benutzer mit der Maus doppelklickt.

- Legt den Pfeilcursorstil auf den Windows-Standard formatieren IDC_ARROW.

- Legt den Hintergrundpinsel auf NULL fest, damit das Fenster seinen Hintergrund nicht löscht.

- Legt das Symbol auf das standardmäßige Windows-Logo-Symbol mit Schwenkflagge fest.

*hCursor*\
Gibt ein Handle für die Cursorressource an, die in jedem Fenster installiert werden soll, das aus der Fensterklasse erstellt wurde. Wenn Sie die Standardeinstellung **0**verwenden, erhalten Sie den Standard-IDC_ARROW-Cursor.

*hbrHintergrund*\
Gibt ein Handle für die Pinselressource an, die in jedem Fenster installiert werden soll, das aus der Fensterklasse erstellt wurde. Wenn Sie den Standardwert **0**verwenden, haben Sie einen NULL-Hintergrundpinsel, und standardmäßig löscht das Fenster seinen Hintergrund während der Verarbeitung [WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd)nicht.

*hIcon*\
Gibt ein Handle für die Symbolressource an, die in jedem Fenster installiert werden soll, das aus der Fensterklasse erstellt wurde. Wenn Sie die Standardeinstellung **0**verwenden, erhalten Sie das standardmäßige Windows-Logo-Symbol mit schwenkendem Schwenkflag.

### <a name="return-value"></a>Rückgabewert

Eine null-terminierte Zeichenfolge, die den Klassennamen enthält. Sie können diesen Klassennamen `Create` an `CWnd` die Memberfunktion in oder an andere **von CWnd**abgeleitete Klassen übergeben, um ein Fenster zu erstellen. Der Name wird von der Microsoft Foundation-Klassenbibliothek generiert.

> [!NOTE]
> Der Rückgabewert ist ein Zeiger auf einen statischen Puffer. Um diese Zeichenfolge zu speichern, weisen Sie sie einer `CString` Variablen zu.

### <a name="remarks"></a>Bemerkungen

Die Microsoft Foundation-Klassenbibliothek registriert automatisch mehrere Standardfensterklassen für Sie. Rufen Sie diese Funktion auf, wenn Sie Ihre eigenen Fensterklassen registrieren möchten.

Der Name, der `AfxRegisterWndClass` für eine Klasse registriert ist, hängt ausschließlich von den Parametern ab. Wenn Sie `AfxRegisterWndClass` mehrmals mit identischen Parametern aufrufen, wird nur eine Klasse beim ersten Aufruf registriert. Spätere `AfxRegisterWndClass` Aufrufe von mit identischen Parametern geben den bereits registrierten Klassennamen zurück.

Wenn Sie `AfxRegisterWndClass` mehrere von CWnd abgeleitete Klassen mit identischen Parametern aufrufen, anstatt eine separate Fensterklasse für jede Klasse abzurufen, verwendet jede Klasse dieselbe Fensterklasse. Diese Freigabe kann Probleme verursachen, wenn der CS_CLASSDC Klassenstil verwendet wird. Anstelle mehrerer CS_CLASSDC Fensterklassen haben Sie nur eine CS_CLASSDC Fensterklasse. Alle C++-Fenster, die diese Klasse verwenden, verwenden denselben Domänencontroller. Um dieses Problem zu vermeiden, rufen Sie [AfxRegisterClass](#afxregisterclass) auf, um die Klasse zu registrieren.

Weitere Informationen zur Fensterklassenregistrierung und zur `AfxRegisterWndClass` Funktion finden Sie unter Technical Note [TN001: Window Class Registration.](../../mfc/tn001-window-class-registration.md)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]

### <a name="requirements"></a>Anforderungen

  **Header** afxwin.h

## <a name="afxsetperuserregistration"></a><a name="afxsetperuserregistration"></a>AfxSetPerUserRegistrierung

Legt fest, ob die Anwendung den Registrierungszugriff auf den **HKEY_CURRENT_USER** -**HKCU**) -Knoten umleitet.

```cpp
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```

### <a name="parameters"></a>Parameter

*bEnable*\
[in] TRUE gibt an, dass die Registrierungsinformationen an den HKCU-Knoten weitergeleitet werden. FALSE gibt an, dass die Anwendung Registrierungsinformationen auf den Standardknoten schreibt. Der Standardknoten ist **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="remarks"></a>Bemerkungen

Vor Windows Vista verwendeten Anwendungen, die auf die Registrierung zugegriffen haben, häufig den **HKEY_CLASSES_ROOT** Knoten. Bei Windows Vista oder neueren Betriebssystemen müssen Sie jedoch eine Anwendung im erhöhten Modus ausführen, um in HKCR zu schreiben.

Mit dieser Methode kann die Anwendung lesen und in die Registrierung schreiben, ohne im erhöhten Modus ausgeführt zu werden. Es funktioniert durch umleiten Registry-Zugriff von HKCR zu HKCU. Weitere Informationen finden Sie unter [Linker-Eigenschaftenseiten](../../build/reference/linker-property-pages.md).

Wenn Sie die Registrierungsumleitung aktivieren, leitet das Framework den Zugriff von HKCR auf **HKEY_CURRENT_USER-Software-Klassen**um. Nur die MFC- und ATL-Frameworks sind von der Umleitung betroffen.

Die Standardimplementierung greift unter HKCR auf die Registrierung zu.

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxstat_.h

## <a name="afxsetresourcehandle"></a><a name="afxsetresourcehandle"></a>AfxSetResourceHandle

Verwenden Sie diese Funktion, um das HINSTANCE-Handle festzulegen, das bestimmt, wo die Standardressourcen der Anwendung geladen werden.

```cpp
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);
```

### <a name="parameters"></a>Parameter

*hInstResource*\
Die Instanz oder das Modulhandle für eine . EXE- oder DLL-Datei, aus der die Ressourcen der Anwendung geladen werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#135](../../mfc/reference/codesnippet/cpp/application-information-and-management_12.cpp)]

### <a name="requirements"></a>Anforderungen

  **Header** afxwin.h

## <a name="afxshellmanager"></a><a name="afxshellmanager"></a>AfxShellManager

Zeiger auf den globalen [Shell-Manager](cshellmanager-class.md).

### <a name="syntax"></a>Syntax

```cpp
CShellManager* afxShellManager;
```

### <a name="requirements"></a>Anforderungen

**Kopf:** afxshellmanager.h

## <a name="afxsocketinit"></a><a name="afxsocketinit"></a>AfxSocketInit

Rufen Sie diese `CWinApp::InitInstance` Funktion in Ihrer Außerkraftsetzung auf, um Windows Sockets zu initialisieren.

```cpp
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);
```

### <a name="parameters"></a>Parameter

*lpwsaData*\
Ein Zeiger auf eine [WSADATA-Struktur.](/windows/win32/api/winsock2/ns-winsock2-wsadata) Wenn *lpwsaData* nicht gleich NULL ist, wird `WSADATA` die Adresse der Struktur `WSAStartup`durch den Aufruf von gefüllt. Diese Funktion stellt `WSACleanup` auch sicher, dass für Sie aufgerufen wird, bevor die Anwendung beendet wird.

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Bemerkungen

Wenn Sie MFC-Sockets in sekundären Threads in einer `AfxSocketInit` statisch verknüpften MFC-Anwendung verwenden, müssen Sie in jedem Thread aufrufen, der Sockets verwendet, um die Socketbibliotheken zu initialisieren. Standardmäßig `AfxSocketInit` wird nur im primären Thread aufgerufen.

### <a name="requirements"></a>Anforderungen

  **Header** afxsock.h

## <a name="afxusertoolsmanager"></a><a name="afxusertoolsmanager"></a>AfxUserToolsManager

Zeiger auf den globalen [Benutzertools-Manager](cusertoolsmanager-class.md).

### <a name="syntax"></a>Syntax

```cpp
CUserToolsManager* afxUserToolsManager;
```

### <a name="requirements"></a>Anforderungen

**Kopf:** afxusertoolsmanager.h

## <a name="afxwininit"></a><a name="afxwininit"></a>AfxWinInit

Diese Funktion wird von der `WinMain` von MFC bereitgestellten Funktion als Teil der [CWinApp-Initialisierung](../../mfc/reference/cwinapp-class.md) einer GUI-basierten Anwendung aufgerufen, um MFC zu initialisieren.

```cpp
BOOL AFXAPI AfxWinInit(
    HINSTANCE hInstance,
    HINSTANCE hPrevInstance,
    LPTSTR lpCmdLine,
    int nCmdShow);
```

### <a name="parameters"></a>Parameter

*Hinstance*\
Das Handle des aktuell ausgeführten Moduls.

*hPrevInstance*\
Ein Handle für eine frühere Instanz der Anwendung. Für eine Win32-basierte Anwendung ist dieser Parameter immer **NULL**.

*lpCmdLine*\
Zeigt auf eine null-terminierte Zeichenfolge, die die Befehlszeile für die Anwendung angibt.

*nCmdShow*\
Gibt an, wie das Hauptfenster einer GUI-Anwendung angezeigt wird.

### <a name="remarks"></a>Bemerkungen

Bei einer Konsolenanwendung, die die von MFC bereitgestellte `WinMain` `AfxWinInit` Funktion nicht verwendet, müssen Sie direkt aufrufen, um MFC zu initialisieren.

Wenn Sie `AfxWinInit` sich selbst aufrufen, sollten `CWinApp` Sie eine Instanz einer Klasse deklarieren. Für eine Konsolenanwendung können Sie ihre eigene Klasse `CWinApp` nicht ableiten `CWinApp` und stattdessen eine Instanz direkt verwenden. Diese Technik ist geeignet, wenn Sie sich entscheiden, alle Funktionen für Ihre Anwendung in Der Implementierung von **main**zu belassen.

> [!NOTE]
> Wenn ein Aktivierungskontext für eine Assembly erstellt wird, verwendet MFC eine Manifestressource, die vom Benutzermodul bereitgestellt wird. Der Aktivierungskontext `AfxWinInit`wird in erstellt. Weitere Informationen finden Sie unter [Unterstützung für Aktivierungskontexte im MFC-Modulstatus](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]

### <a name="requirements"></a>Anforderungen

  **Header** afxwin.h

## <a name="see-also"></a>Siehe auch

[Makros und Globals](mfc-macros-and-globals.md)\
[CWinApp-Klasse](cwinapp-class.md)\
[CContextMenuManager-Klasse](ccontextmenumanager-class.md)\
[CWnd-Klasse](cwnd-class.md)\
[CFrameWndEx-Klasse](cframewndex-class.md)\
[CMFCToolBar-Klasse](cmfctoolbar-class.md)\
[CKeyboardManager-Klasse](ckeyboardmanager-class.md)\
[CMenuTearOffManager-Klasse](cmenutearoffmanager-class.md)\
[CMouseManager-Klasse](cmousemanager-class.md)\
[CShellManager-Klasse](cshellmanager-class.md)\
[CUserToolsManager-Klasse](cusertoolsmanager-class.md)
