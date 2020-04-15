---
title: 'Exemplarische Vorgehensweise: Erstellen einer herkömmlichen Windows Desktop-Anwendung (C++)'
description: Erstellen einer minimalen, traditionellen Windows Desktop-Anwendung mit Visual Studio, C++ und der Win32-API
ms.custom: get-started-article
ms.date: 11/03/2019
helpviewer_keywords:
- Windows applications [C++], Win32
- Windows Desktop applications [C++]
- Windows API [C++]
ms.openlocfilehash: da74778e79a08dd3ed2b5be0675981425264bdc0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351848"
---
# <a name="walkthrough-create-a-traditional-windows-desktop-application-c"></a>Exemplarische Vorgehensweise: Erstellen einer herkömmlichen Windows Desktop-Anwendung (C++)

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie eine herkömmliche Windows-Desktopanwendung in Visual Studio erstellen. Die Beispielanwendung, die Sie erstellen, verwendet die Windows-API, um "Hallo, Windows-Desktop!" anzuzeigen. in einem Fenster anzeigt. Sie können den Code verwenden, den Sie in dieser exemplarischen Vorgehensweise als Muster entwickeln, um andere Windows-Desktopanwendungen zu erstellen.

Die Windows-API (auch als Win32-API, Windows-Desktop-API und Windows Classic-API bezeichnet) ist ein C-Sprach-basiertes Framework zum Erstellen von Windows-Anwendungen. Es besteht seit den 1980er Jahren und wird seit Jahrzehnten verwendet, um Windows-Anwendungen zu erstellen. Erweiterte und programmiereinfachere Frameworks wurden auf der Windows-API erstellt. Beispiel: MFC, ATL, die .NET-Frameworks. Selbst der modernste Windows-Runtime-Code für UWP- und Store-Apps, die in C++/WinRT geschrieben wurden, verwendet die darunter liegende Windows-API. Weitere Informationen zur Windows-API finden Sie unter [Windows API Index](/windows/win32/apiindex/windows-api-list). Es gibt viele Möglichkeiten, Windows-Anwendungen zu erstellen, aber der obige Prozess war der erste.

> [!IMPORTANT]
> Aus Gründen der Kürze werden einige Codeanweisungen im Text weggelassen. Im Abschnitt [Erstellen des Codes](#build-the-code) am Ende dieses Dokuments wird der vollständige Code angezeigt.

## <a name="prerequisites"></a>Voraussetzungen

- Ein Computer, auf dem Microsoft Windows 7 oder eine höhere Version ausgeführt wird. Für ein optimales Entwicklungserlebnis empfehlen wir Windows 10.

- Eine Kopie von Visual Studio. Informationen zum Herunterladen und Installieren von Visual Studio finden Sie unter [Installieren von Visual Studio](/visualstudio/install/install-visual-studio). Wenn Sie das Installationsprogramm ausführen, stellen Sie sicher, dass die Workload **Desktopentwicklung mit C++** aktiviert ist. Machen Sie sich keine Sorgen, wenn Sie diese Workload beim Installieren von Visual Studio nicht installiert haben. Sie können das Installationsprogramm erneut ausführen und die Workload jetzt installieren.

   ![Desktopentwicklung mit C++](../build/media/desktop-development-with-cpp.png "Desktopentwicklung mit C++")

- Grundkenntnisse der Verwendung der Visual Studio-IDE. Wenn Sie bereits früher Windows-Desktop-Apps verwendet haben, dürften keine Verständnisprobleme auftreten. Eine Einführung finden Sie unter [Willkommen in der Visual Studio-IDE](/visualstudio/ide/visual-studio-ide).

- Grundlegende Kenntnisse der Programmiersprache C++. Keine Sorge: Wir verwenden keine allzu komplizierten Verfahren.

## <a name="create-a-windows-desktop-project"></a>Erstellen eines Windows-Desktopprojekts

Führen Sie die folgenden Schritte aus, um Ihr erstes Windows-Desktopprojekt zu erstellen. Während Sie gehen, geben Sie den Code für eine funktionierende Windows-Desktopanwendung ein. Verwenden Sie das Versionsauswahlsteuerelement, um die **Version** Dokumentation für Ihre bevorzugte Version von Visual Studio anzuzeigen. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker range="vs-2019"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2019"></a>So erstellen Sie ein Windows-Desktopprojekt in Visual Studio 2019

1. Klicken Sie im Hauptmenü auf **Datei** > **Neu** > **Projekt**, um das Dialogfeld **Neues Projekt erstellen** zu öffnen.

1. Legen Sie oben im Dialogfeld **Sprache** auf **C++** fest, legen Sie **Plattform** auf **Windows**fest, und legen Sie den Projekttyp auf **Desktop** **fest.**

1. Wählen Sie in der gefilterten Liste der Projekttypen **den Windows-Desktop-Assistenten** aus, und wählen Sie dann **Weiter**aus. Geben Sie auf der nächsten Seite einen Namen für das Projekt ein, z. B. *DesktopApp*.

1. Klicken Sie auf die Schaltfläche **Erstellen**, um das Projekt zu erstellen.

1. Das Dialogfeld **Windows Desktop Project** wird nun angezeigt. Wählen Sie unter **Anwendungstyp**die Option **Desktopanwendung (.exe)** aus. Wählen Sie unter **Zusätzliche Optionen**die Option **Leeres Projekt**aus. Wählen Sie **OK,** um das Projekt zu erstellen.

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf das **DesktopApp-Projekt,** wählen **Sie Hinzufügen**aus, und wählen Sie dann **Neues Element**aus.

   ![Hinzufügen eines neuen Elements zu DesktopApp Project](../build/media/desktop-app-project-add-new-item-153.gif "Hinzufügen eines neuen Elements zu DesktopApp Project")

1. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **C++-Datei (.cpp)**. Geben Sie im Feld **Name** einen Namen für die Datei ein, z. B. *HelloWindowsDesktop.cpp*. Wählen Sie **Hinzufügen**von .

   ![.cpp-Datei zu DesktopApp Project hinzufügen](../build/media/desktop-app-add-cpp-file-153.png ".cpp-Datei zu DesktopApp Project hinzufügen")

Ihr Projekt wird nun erstellt, und die Quelldatei wird im Editor geöffnet. Um fortzufahren, fahren Sie mit [Create the code](#create-the-code)fort.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2017"></a>So erstellen Sie ein Windows-Desktopprojekt in Visual Studio 2017

1. Wählen Sie im Menü **Datei** die Option **Neu** und anschließend **Projekt** aus.

1. Erweitern Sie im Dialogfeld **Neues Projekt** im linken Bereich **Installiertes** > **visuelles C++,** und wählen Sie dann **Windows Desktop aus.** Wählen Sie im mittleren Bereich **den Windows-Desktop-Assistenten**aus.

   Geben Sie im Feld **Name** einen Namen für das Projekt ein, z. B. *DesktopApp*. Wählen Sie **OK**.

   ![Benennen des DesktopApp-Projekts](../build/media/desktop-app-new-project-name-153.png "Benennen des DesktopApp-Projekts")

1. Wählen Sie im Dialogfeld **Windows Desktop Project** unter **Anwendungstyp** **windows application (.exe)** aus. Wählen Sie unter **Zusätzliche Optionen**die Option **Leeres Projekt**aus. Stellen Sie sicher, dass der **vorkompilierte Header** nicht ausgewählt ist. Wählen Sie **OK,** um das Projekt zu erstellen.

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf das **DesktopApp-Projekt,** wählen **Sie Hinzufügen**aus, und wählen Sie dann **Neues Element**aus.

   ![Hinzufügen eines neuen Elements zu DesktopApp Project](../build/media/desktop-app-project-add-new-item-153.gif "Hinzufügen eines neuen Elements zu DesktopApp Project")

1. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **C++-Datei (.cpp)**. Geben Sie im Feld **Name** einen Namen für die Datei ein, z. B. *HelloWindowsDesktop.cpp*. Wählen Sie **Hinzufügen**von .

   ![.cpp-Datei zu DesktopApp Project hinzufügen](../build/media/desktop-app-add-cpp-file-153.png ".cpp-Datei zu DesktopApp Project hinzufügen")

Ihr Projekt wird nun erstellt, und die Quelldatei wird im Editor geöffnet. Um fortzufahren, fahren Sie mit [Create the code](#create-the-code)fort.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2015"></a>So erstellen Sie ein Windows-Desktopprojekt in Visual Studio 2015

1. Wählen Sie im Menü **Datei** die Option **Neu** und anschließend **Projekt** aus.

1. Erweitern Sie im Dialogfeld Neues **Projekt** im linken Bereich **Visual** > **Templates** > **C++**, und wählen Sie dann **Win32**aus. Wählen Sie im mittleren Bereich **Win32-Projekt**aus.

   Geben Sie im Feld **Name** einen Namen für das Projekt ein, z. B. *DesktopApp*. Wählen Sie **OK**.

   ![Benennen des DesktopApp-Projekts](../build/media/desktop-app-new-project-name-150.png "Benennen des DesktopApp-Projekts")

1. Wählen Sie auf der **Übersichtsseite** des **Win32-Anwendungs-Assistenten**die Option **Weiter**aus.

   ![Erstellen von DesktopApp in Win32 Application Wizard Übersicht](../build/media/desktop-app-win32-wizard-overview-150.png "Erstellen von DesktopApp in Win32 Application Wizard Übersicht")

1. Wählen Sie auf der Seite **Anwendungseinstellungen** unter **Anwendungstyp** **windows application**aus. Unter **Zusätzliche Optionen**deaktivieren Sie die Option **Vorkompilierte Kopfzeile**, und wählen Sie dann **Leeres Projekt**aus. Wählen Sie **Fertig stellen** aus, um das Projekt zu erstellen.

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf das DesktopApp-Projekt, wählen **Sie Hinzufügen**aus, und wählen Sie dann **Neues Element**aus.

   ![Hinzufügen eines neuen Elements zu DesktopApp Project](../build/media/desktop-app-project-add-new-item-150.gif "Hinzufügen eines neuen Elements zu DesktopApp Project")

1. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **C++-Datei (.cpp)**. Geben Sie im Feld **Name** einen Namen für die Datei ein, z. B. *HelloWindowsDesktop.cpp*. Wählen Sie **Hinzufügen**von .

   ![.cpp-Datei zu DesktopApp Project hinzufügen](../build/media/desktop-app-add-cpp-file-150.png ".cpp-Datei zu DesktopApp Project hinzufügen")

Ihr Projekt wird nun erstellt, und die Quelldatei wird im Editor geöffnet.

::: moniker-end

## <a name="create-the-code"></a>Erstellen des Codes

Als Nächstes erfahren Sie, wie Sie den Code für eine Windows-Desktopanwendung in Visual Studio erstellen.

### <a name="to-start-a-windows-desktop-application"></a>So beginnen Sie eine Windows-Desktopanwendung

1. Genauso wie jede C-Anwendung und C++-Anwendung eine `main` Funktion als Ausgangspunkt `WinMain` haben muss, muss jede Windows-Desktopanwendung eine Funktion haben. `WinMain` besitzt die folgende Syntax.

   ```cpp
   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_opt_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   );
   ```

   Informationen zu den Parametern und dem Rückgabewert dieser Funktion finden Sie unter [WinMain-Einstiegspunkt](/windows/win32/api/winbase/nf-winbase-winmain).

   > [!NOTE]
   > Was sind all diese zusätzlichen `CALLBACK`Wörter, z. B. oder `HINSTANCE`, oder `_In_`? Die herkömmliche Windows-API verwendet typedefs und Präprozessormakros ausgiebig, um einige Details von Typen und plattformspezifischen Code, wie Z. B. Aufrufkonventionen, **__declspec** Deklarationen und Compilerpragmas, abzustrahieren. In Visual Studio können Sie die [IntelliSense-Schnellinfo-Funktion](/visualstudio/ide/using-intellisense#quick-info) verwenden, um zu sehen, was diese typedefs und Makros definieren. Bewegen Sie den Mauszeiger über das Wort von Interesse, oder wählen Sie es aus und drücken Sie **Strg**+**K**, **Strg**+**I** für ein kleines Popup-Fenster, das die Definition enthält. Weitere Informationen finden Sie unter [Verwenden von IntelliSense](/visualstudio/ide/using-intellisense). Parameter und Rückgabetypen verwenden häufig *SAL-Anmerkungen,* um Programmierfehler abzufangen. Weitere Informationen finden Sie unter [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](/cpp/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects).

1. Windows-Desktopprogramme &lt;erfordern windows.h->. &lt;tchar.h> definiert `TCHAR` das Makro, das letztlich **in wchar_t** auflöst, wenn das UNICODE-Symbol in Ihrem Projekt definiert ist, andernfalls wird es in **char**aufgelöst.  Wenn Sie immer mit aktiviertem UNICODE bauen, benötigen Sie TCHAR nicht und können **wchar_t** einfach direkt verwenden.

   ```cpp
   #include <windows.h>
   #include <tchar.h>
   ```

1. Neben der `WinMain` Funktion muss jede Windows-Desktopanwendung auch über eine Fensterprozedurfunktion verfügen. Diese Funktion wird `WndProc`in der Regel genannt, aber Sie können sie benennen, was immer Sie möchten. `WndProc` besitzt die folgende Syntax.

   ```cpp
   LRESULT CALLBACK WndProc(
      _In_ HWND   hWnd,
      _In_ UINT   message,
      _In_ WPARAM wParam,
      _In_ LPARAM lParam
   );
   ```

   In dieser Funktion schreiben Sie Code, um *Nachrichten* zu verarbeiten, die die Anwendung von Windows empfängt, wenn *Ereignisse* auftreten. Wenn ein Benutzer beispielsweise eine SCHALTFLÄCHE OK in Ihrer Anwendung auswählt, sendet Windows eine `WndProc` Nachricht an Sie, und Sie können Code in Ihre Funktion schreiben, der die arbeitsuchende Arbeit ausführt. Es wird *als Umgang mit* einem Ereignis bezeichnet. Sie behandeln nur die Ereignisse, die für Ihre Anwendung relevant sind.

   Weitere Informationen finden Sie unter [Window Procedures](/windows/win32/winmsg/window-procedures).

### <a name="to-add-functionality-to-the-winmain-function"></a>So fügen Sie der WinMain-Funktion Funktionen hinzu

1. In `WinMain` der Funktion füllen Sie eine Struktur vom Typ [WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw). Die Struktur enthält Informationen über das Fenster: das Anwendungssymbol, die Hintergrundfarbe des Fensters, den Namen, der unter anderem in der Titelleiste angezeigt werden soll. Wichtig ist, dass es einen Funktionszeiger auf Ihre Fensterprozedur enthält. Das folgende Beispiel zeigt eine typische `WNDCLASSEX` -Struktur.

   ```cpp
   WNDCLASSEX wcex;

   wcex.cbSize         = sizeof(WNDCLASSEX);
   wcex.style          = CS_HREDRAW | CS_VREDRAW;
   wcex.lpfnWndProc    = WndProc;
   wcex.cbClsExtra     = 0;
   wcex.cbWndExtra     = 0;
   wcex.hInstance      = hInstance;
   wcex.hIcon          = LoadIcon(hInstance, IDI_APPLICATION);
   wcex.hCursor        = LoadCursor(NULL, IDC_ARROW);
   wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1);
   wcex.lpszMenuName   = NULL;
   wcex.lpszClassName  = szWindowClass;
   wcex.hIconSm        = LoadIcon(wcex.hInstance, IDI_APPLICATION);
   ```

   Informationen zu den Feldern der obigen Struktur finden Sie unter [WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw).

1. Registrieren `WNDCLASSEX` Sie die mit Windows, damit es über Ihr Fenster und das Senden von Nachrichten an Windows Bescheid weiß. Verwenden Sie die [RegisterClassEx](/windows/win32/api/winuser/nf-winuser-registerclassexw) -Funktion, und übergeben Sie die Fensterklassenstruktur als Argument. Das `_T` Makro wird verwendet, `TCHAR` da wir den Typ verwenden.

   ```cpp
   if (!RegisterClassEx(&wcex))
   {
      MessageBox(NULL,
         _T("Call to RegisterClassEx failed!"),
         _T("Windows Desktop Guided Tour"),
         NULL);

      return 1;
   }
   ```

1. Sie können nun ein Fenster erstellen. Verwenden Sie die [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) -Funktion.

   ```cpp
   static TCHAR szWindowClass[] = _T("DesktopApp");
   static TCHAR szTitle[] = _T("Windows Desktop Guided Tour Application");

   // The parameters to CreateWindow explained:
   // szWindowClass: the name of the application
   // szTitle: the text that appears in the title bar
   // WS_OVERLAPPEDWINDOW: the type of window to create
   // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y)
   // 500, 100: initial size (width, length)
   // NULL: the parent of this window
   // NULL: this application does not have a menu bar
   // hInstance: the first parameter from WinMain
   // NULL: not used in this application
   HWND hWnd = CreateWindow(
      szWindowClass,
      szTitle,
      WS_OVERLAPPEDWINDOW,
      CW_USEDEFAULT, CW_USEDEFAULT,
      500, 100,
      NULL,
      NULL,
      hInstance,
      NULL
   );
   if (!hWnd)
   {
      MessageBox(NULL,
         _T("Call to CreateWindow failed!"),
         _T("Windows Desktop Guided Tour"),
         NULL);

      return 1;
   }
   ```

   Diese Funktion `HWND`gibt ein zurück, bei dem es sich um ein Handle für ein Fenster handelt. Ein Handle ähnelt einem Zeiger, den Windows verwendet, um geöffnete Fenster nachzuverfolgen. Weitere Informationen finden Sie unter [Windows-Datentypen](/windows/win32/WinProg/windows-data-types).

1. An diesem Punkt wurde das Fenster erstellt, aber wir müssen Windows noch anweisen, es sichtbar zu machen. Das ist, was dieser Code tut:

   ```cpp
   // The parameters to ShowWindow explained:
   // hWnd: the value returned from CreateWindow
   // nCmdShow: the fourth parameter from WinMain
   ShowWindow(hWnd,
      nCmdShow);
   UpdateWindow(hWnd);
   ```

   Das angezeigte Fenster hat nicht viel Inhalt, da `WndProc` Sie die Funktion noch nicht implementiert haben. Mit anderen Worten, die Anwendung verarbeitet noch nicht die Nachrichten, die Windows jetzt an sie sendet.

1. Um die Nachrichten zu verarbeiten, fügen wir zunächst eine Nachrichtenschleife hinzu, um die von Windows gesendeten Nachrichten zu hören. Wenn die Anwendung eine Nachricht empfängt, sendet `WndProc` diese Schleife sie an Ihre zu verarbeitende Funktion. Die Nachrichtenschleife ähnelt dem folgenden Code.

   ```cpp
   MSG msg;
   while (GetMessage(&msg, NULL, 0, 0))
   {
      TranslateMessage(&msg);
      DispatchMessage(&msg);
   }

   return (int) msg.wParam;
   ```

   Weitere Informationen über die in der Nachrichtenschleife verwendeten Strukturen und Funktionen finden Sie unter [MSG](/windows/win32/api/winuser/ns-winuser-msg), [GetMessage](/windows/win32/api/winuser/nf-winuser-getmessage), [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)und [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).

   An diesem Punkt sollte die `WinMain` -Funktion in etwa dem folgenden Code entsprechen.

   ```cpp
   int WINAPI WinMain(HINSTANCE hInstance,
                      HINSTANCE hPrevInstance,
                      LPSTR lpCmdLine,
                      int nCmdShow)
   {
      WNDCLASSEX wcex;

      wcex.cbSize = sizeof(WNDCLASSEX);
      wcex.style          = CS_HREDRAW | CS_VREDRAW;
      wcex.lpfnWndProc    = WndProc;
      wcex.cbClsExtra     = 0;
      wcex.cbWndExtra     = 0;
      wcex.hInstance      = hInstance;
      wcex.hIcon          = LoadIcon(hInstance, IDI_APPLICATION);
      wcex.hCursor        = LoadCursor(NULL, IDC_ARROW);
      wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1);
      wcex.lpszMenuName   = NULL;
      wcex.lpszClassName  = szWindowClass;
      wcex.hIconSm        = LoadIcon(wcex.hInstance, IDI_APPLICATION);

      if (!RegisterClassEx(&wcex))
      {
         MessageBox(NULL,
            _T("Call to RegisterClassEx failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // Store instance handle in our global variable
      hInst = hInstance;

      // The parameters to CreateWindow explained:
      // szWindowClass: the name of the application
      // szTitle: the text that appears in the title bar
      // WS_OVERLAPPEDWINDOW: the type of window to create
      // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y)
      // 500, 100: initial size (width, length)
      // NULL: the parent of this window
      // NULL: this application dows not have a menu bar
      // hInstance: the first parameter from WinMain
      // NULL: not used in this application
      HWND hWnd = CreateWindow(
         szWindowClass,
         szTitle,
         WS_OVERLAPPEDWINDOW,
         CW_USEDEFAULT, CW_USEDEFAULT,
         500, 100,
         NULL,
         NULL,
         hInstance,
         NULL
      );

      if (!hWnd)
      {
         MessageBox(NULL,
            _T("Call to CreateWindow failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // The parameters to ShowWindow explained:
      // hWnd: the value returned from CreateWindow
      // nCmdShow: the fourth parameter from WinMain
      ShowWindow(hWnd,
         nCmdShow);
      UpdateWindow(hWnd);

      // Main message loop:
      MSG msg;
      while (GetMessage(&msg, NULL, 0, 0))
      {
         TranslateMessage(&msg);
         DispatchMessage(&msg);
      }

      return (int) msg.wParam;
   }
   ```

### <a name="to-add-functionality-to-the-wndproc-function"></a>So fügen Sie der WndProc-Funktion Funktionen hinzu

1. Damit die `WndProc` -Funktion die Nachrichten behandeln kann, die von der Anwendung empfangen werden, implementieren Sie eine switch-Anweisung.

   Eine wichtige Nachricht, die behandelt werden soll, ist die [WM_PAINT](/windows/win32/gdi/wm-paint) Nachricht. Die Anwendung `WM_PAINT` erhält die Meldung, wenn ein Teil des angezeigten Fensters aktualisiert werden muss. Das Ereignis kann auftreten, wenn ein Benutzer ein Fenster vor das Fenster verschiebt und es dann wieder wegverschiebt. Ihre Anwendung weiß nicht, wann diese Ereignisse auftreten. Nur Windows weiß, so dass es `WM_PAINT` Ihre App mit einer Nachricht benachrichtigt. Wenn das Fenster zum ersten Mal angezeigt wird, muss es alle aktualisiert werden.

   Rufen Sie zur Behandlung einer `WM_PAINT` -Nachricht zuerst [BeginPaint](/windows/win32/api/winuser/nf-winuser-beginpaint)auf, behandeln Sie anschließend die gesamte Logik, um das Layout von Text, Schaltflächen und anderen Steuerelementen im Fenster zu behandeln, und rufen Sie anschließend [EndPaint](/windows/win32/api/winuser/nf-winuser-endpaint)auf. Für die Anwendung besteht die Logik zwischen dem Anfangsaufruf und dem Endaufruf darin, die Zeichenfolge "Hello, Windows desktop!" anzuzeigen. im Fenster. Im folgenden Code wird die [TextOut](/windows/win32/api/wingdi/nf-wingdi-textoutw) -Funktion zur Anzeige der Zeichenfolge verwendet.

   ```cpp
   PAINTSTRUCT ps;
   HDC hdc;
   TCHAR greeting[] = _T("Hello, Windows desktop!");

   switch (message)
   {
   case WM_PAINT:
      hdc = BeginPaint(hWnd, &ps);

      // Here your application is laid out.
      // For this introduction, we just print out "Hello, Windows desktop!"
      // in the top left corner.
      TextOut(hdc,
         5, 5,
         greeting, _tcslen(greeting));
      // End application-specific layout section.

      EndPaint(hWnd, &ps);
      break;
   }
   ```

   `HDC`Im Code handelt es sich um ein Handle für einen Gerätekontext, bei dem es sich um eine Datenstruktur handelt, die Windows verwendet, um die Kommunikation ihrer Anwendung mit dem Grafiksubsystem zu ermöglichen. Die `BeginPaint` `EndPaint` und Funktionen machen Ihre Anwendung verhalten sich wie ein guter Bürger und verwendet nicht den Gerätekontext länger als es erforderlich ist. Die Funktionen, mit denen das Grafiksubsystem für andere Anwendungen verfügbar ist.

1. Eine Anwendung verarbeitet in der Regel viele andere Nachrichten. [WM_CREATE](/windows/win32/winmsg/wm-create) z. B. wenn ein Fenster zum ersten Mal erstellt wird, und [WM_DESTROY,](/windows/win32/winmsg/wm-destroy) wenn das Fenster geschlossen wird. Der folgende Code zeigt eine grundlegende, jedoch vollständige `WndProc` -Funktion.

   ```cpp
   LRESULT CALLBACK WndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam)
   {
      PAINTSTRUCT ps;
      HDC hdc;
      TCHAR greeting[] = _T("Hello, Windows desktop!");

      switch (message)
      {
      case WM_PAINT:
         hdc = BeginPaint(hWnd, &ps);

         // Here your application is laid out.
         // For this introduction, we just print out "Hello, Windows desktop!"
         // in the top left corner.
         TextOut(hdc,
            5, 5,
            greeting, _tcslen(greeting));
         // End application specific layout section.

         EndPaint(hWnd, &ps);
         break;
      case WM_DESTROY:
         PostQuitMessage(0);
         break;
      default:
         return DefWindowProc(hWnd, message, wParam, lParam);
         break;
      }

      return 0;
   }
   ```

## <a name="build-the-code"></a>Erstellen des Codes

Wie versprochen, hier ist der komplette Code für die Arbeitsanwendung.

### <a name="to-build-this-example"></a>So erstellen Sie dieses Beispiel

1. Löschen Sie den Code, den Sie in *HelloWindowsDesktop.cpp* im Editor eingegeben haben. Kopieren Sie diesen Beispielcode, und fügen Sie ihn dann in *HelloWindowsDesktop.cpp*ein:

   ```cpp
   // HelloWindowsDesktop.cpp
   // compile with: /D_UNICODE /DUNICODE /DWIN32 /D_WINDOWS /c

   #include <windows.h>
   #include <stdlib.h>
   #include <string.h>
   #include <tchar.h>

   // Global variables

   // The main window class name.
   static TCHAR szWindowClass[] = _T("DesktopApp");

   // The string that appears in the application's title bar.
   static TCHAR szTitle[] = _T("Windows Desktop Guided Tour Application");

   HINSTANCE hInst;

   // Forward declarations of functions included in this code module:
   LRESULT CALLBACK WndProc(HWND, UINT, WPARAM, LPARAM);

   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_opt_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   )
   {
      WNDCLASSEX wcex;

      wcex.cbSize = sizeof(WNDCLASSEX);
      wcex.style          = CS_HREDRAW | CS_VREDRAW;
      wcex.lpfnWndProc    = WndProc;
      wcex.cbClsExtra     = 0;
      wcex.cbWndExtra     = 0;
      wcex.hInstance      = hInstance;
      wcex.hIcon          = LoadIcon(hInstance, IDI_APPLICATION);
      wcex.hCursor        = LoadCursor(NULL, IDC_ARROW);
      wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1);
      wcex.lpszMenuName   = NULL;
      wcex.lpszClassName  = szWindowClass;
      wcex.hIconSm        = LoadIcon(wcex.hInstance, IDI_APPLICATION);

      if (!RegisterClassEx(&wcex))
      {
         MessageBox(NULL,
            _T("Call to RegisterClassEx failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // Store instance handle in our global variable
      hInst = hInstance;

      // The parameters to CreateWindow explained:
      // szWindowClass: the name of the application
      // szTitle: the text that appears in the title bar
      // WS_OVERLAPPEDWINDOW: the type of window to create
      // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y)
      // 500, 100: initial size (width, length)
      // NULL: the parent of this window
      // NULL: this application does not have a menu bar
      // hInstance: the first parameter from WinMain
      // NULL: not used in this application
      HWND hWnd = CreateWindow(
         szWindowClass,
         szTitle,
         WS_OVERLAPPEDWINDOW,
         CW_USEDEFAULT, CW_USEDEFAULT,
         500, 100,
         NULL,
         NULL,
         hInstance,
         NULL
      );

      if (!hWnd)
      {
         MessageBox(NULL,
            _T("Call to CreateWindow failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // The parameters to ShowWindow explained:
      // hWnd: the value returned from CreateWindow
      // nCmdShow: the fourth parameter from WinMain
      ShowWindow(hWnd,
         nCmdShow);
      UpdateWindow(hWnd);

      // Main message loop:
      MSG msg;
      while (GetMessage(&msg, NULL, 0, 0))
      {
         TranslateMessage(&msg);
         DispatchMessage(&msg);
      }

      return (int) msg.wParam;
   }

   //  FUNCTION: WndProc(HWND, UINT, WPARAM, LPARAM)
   //
   //  PURPOSE:  Processes messages for the main window.
   //
   //  WM_PAINT    - Paint the main window
   //  WM_DESTROY  - post a quit message and return
   LRESULT CALLBACK WndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam)
   {
      PAINTSTRUCT ps;
      HDC hdc;
      TCHAR greeting[] = _T("Hello, Windows desktop!");

      switch (message)
      {
      case WM_PAINT:
         hdc = BeginPaint(hWnd, &ps);

         // Here your application is laid out.
         // For this introduction, we just print out "Hello, Windows desktop!"
         // in the top left corner.
         TextOut(hdc,
            5, 5,
            greeting, _tcslen(greeting));
         // End application-specific layout section.

         EndPaint(hWnd, &ps);
         break;
      case WM_DESTROY:
         PostQuitMessage(0);
         break;
      default:
         return DefWindowProc(hWnd, message, wParam, lParam);
         break;
      }

      return 0;
   }
   ```

1. Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen**. Die Ergebnisse der Kompilierung sollten im **Ausgabefenster** in Visual Studio angezeigt werden.

   ![Erstellen des DesktopApp-Projekts](../build/media/desktop-app-project-build-150.gif "Erstellen des DesktopApp-Projekts")

1. Drücken Sie **F5**, um die Anwendung auszuführen. Ein Fenster mit dem Text "Hallo, Windows-Desktop!" sollte in der oberen linken Ecke der Anzeige angezeigt werden.

   ![Ausführen des DesktopApp-Projekts](../build/media/desktop-app-project-run-157.PNG "Ausführen des DesktopApp-Projekts")

Glückwunsch! Sie haben diese exemplarische Vorgehensweise abgeschlossen und eine herkömmliche Windows-Desktopanwendung erstellt.

## <a name="see-also"></a>Siehe auch

[Windows-Desktopanwendungen](../windows/windows-desktop-applications-cpp.md)
