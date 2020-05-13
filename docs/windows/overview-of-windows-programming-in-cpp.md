---
title: Übersicht über Windows-Programmierung in C++
ms.date: 09/17/2019
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 8ab7fbf7c955b1c828ef583aa639eda7409cf167
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359947"
---
# <a name="overview-of-windows-programming-in-c"></a>Übersicht über Windows-Programmierung in C++

Es gibt mehrere allgemeine Kategorien von Windows-Anwendungen, die Sie mit C++ erstellen können. Jede verfügt über ein eigenes Programmiermodell und einen Satz von Windows-spezifischen Bibliotheken, aber die C++-Standardbibliothek und c++-Bibliotheken von Drittanbietern können in jedem dieser Bibliotheken verwendet werden.

In diesem Abschnitt wird erläutert, wie Sie Visual Studio und die MFC/ATL-Wrapperbibliotheken zum Erstellen von Windows-Programmen verwenden. Dokumentation zur Windows-Plattform selbst finden Sie in der [Windows-Dokumentation](/windows/index).

## <a name="command-line-console-applications"></a>Befehlszeilenanwendungen (Konsole)

C++-Konsolenanwendungen werden über die Befehlszeile in einem Konsolenfenster ausgeführt und können nur Textausgabe anzeigen. Weitere Informationen finden Sie unter [Erstellen eines C++-Konsolen-App-Projekts](../get-started/tutorial-console-cpp.md).

## <a name="native-desktop-client-applications"></a>Native Desktop-Clientanwendungen

Eine *systemeigene Desktopclientanwendung* ist eine C- oder C++-Fensteranwendung, die die ursprünglichen systemeigenen [Windows C-APIs oder COM-APIs (Component Object Model)](/windows/win32/apiindex/windows-api-list) für den Zugriff auf das Betriebssystem verwendet. Diese APIs sind selbst meist in C geschrieben. Es gibt mehr als eine Möglichkeit, eine native Desktop-App zu erstellen: Sie können die Win32-APIs direkt mit einer Nachrichtenschleife im C-Stil programmieren, die Betriebssystemereignisse verarbeitet. Sie können auch mit *Microsoft Foundation Classes* (MFC) programmieren, einer leicht objektorientierten C++-Bibliothek, die Win32 umschließt. Keiner der beiden Ansätze gilt im Vergleich zur universellen Windows-Plattform (UWP) als "modern", aber beide werden immer noch vollständig unterstützt und haben heute Millionen von Codezeilen, die auf der Welt ausgeführt werden. Eine Win32-Anwendung, die in einem Fenster ausgeführt wird, erfordert, dass der Entwickler explizit mit Windows-Nachrichten innerhalb einer Windows-Prozedurfunktion arbeitet. Trotz des Namens kann eine Win32-Anwendung als 32-Bit-Binärdatei (x86) oder 64-Bit (x64) kompiliert werden. In der Visual Studio-IDE sind die Begriffe x86 und Win32 synonym.

Informationen zu den ersten Informationen zur herkömmlichen Windows C++-Programmierung finden Sie [unter Erste Schritte mit Win32 und C++](/windows/win32/LearnWin32/learn-to-program-for-windows). Nachdem Sie sich mit Win32 ausgebessert haben, ist es einfacher, mehr über [MFC Desktop Applications](../mfc/mfc-desktop-applications.md)zu erfahren. Ein Beispiel für eine herkömmliche C++-Desktopanwendung, die anspruchsvolle Grafiken verwendet, finden Sie unter [Hilo: Entwickeln von C++-Anwendungen für Windows](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx).

### <a name="c-or-net"></a>C++ oder .NET?

Im Allgemeinen ist die .NET-Programmierung in C-Code weniger komplex, weniger fehleranfällig und verfügt über eine modernere objektorientierte API als Win32 oder MFC. In den meisten Fällen ist seine Leistung mehr als ausreichend. .NET verfügt über die Windows Presentation Foundation (WPF) für umfangreiche Grafiken, und Sie können sowohl Win32 als auch die moderne Windows-Runtime-API verwenden. In der Regel empfehlen wir die Verwendung von C++ für Desktopanwendungen, wenn Sie:

- präzise Steuerung der Speichernutzung
- die höchste Wirtschaftlichkeit beim Stromverbrauch
- Nutzung der GPU für allgemeines Computing
- Zugriff auf DirectX
- starker Einsatz von Standard-C++-Bibliotheken

Es ist auch möglich, die Leistung und Effizienz von C++ mit .NET-Programmierung zu kombinieren. Sie können eine Benutzeroberfläche in C- erstellen und C++/CLI verwenden, um die Anwendung in die Nutzung systemeigener C++-Bibliotheken zu versetzen. Weitere Informationen finden Sie unter [.NET Programming mit C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

## <a name="com-components"></a>COM-Komponenten

Das [Component Object Model (COM)](/windows/win32/com/the-component-object-model) ist eine Spezifikation, die es Programmen, die in verschiedenen Sprachen geschrieben sind, ermöglicht, miteinander zu kommunizieren. Viele Windows-Komponenten werden als COM-Objekte implementiert und folgen standardmäßigen COM-Regeln für die Objekterstellung, Schnittstellenermittlung und Objektzerstörung.  Die Verwendung von COM-Objekten aus C++-Desktopanwendungen ist relativ einfach, das Schreiben eines eigenen COM-Objekts ist jedoch erweitert. Die [Active Template Library (ATL)](../atl/atl-com-desktop-components.md) stellt Makros und Hilfsfunktionen bereit, die die COM-Entwicklung vereinfachen. Weitere Informationen finden Sie unter [ATL COM-Desktopkomponenten](../atl/atl-com-desktop-components.md).

## <a name="universal-windows-platform-apps"></a>Universelle Windows-Plattform-Apps

Die universelle Windows-Plattform (UWP) ist die moderne Windows-API. UWP-Apps werden auf jedem Windows 10-Gerät ausgeführt, verwenden XAML für die Benutzeroberfläche und sind vollständig berührungslos. Weitere Informationen zu UWP finden Sie unter [Was ist eine UWP-App (Universelle Windows-Plattform)?](/windows/uwp/get-started/whats-a-uwp) und [Anleitung zu Windows Universal Apps](/windows/uwp/get-started/universal-application-platform-guide).

Die ursprüngliche C++-Unterstützung für UWP bestand aus (1) C++/CX, einem Dialekt von C++ mit Syntaxerweiterungen oder (2) der Windows-Runtime-Bibliothek (WRL), die auf Standard-C++- und COM-Code basiert. Sowohl C++/CX als auch WRL werden weiterhin unterstützt. Für neue Projekte empfehlen wir [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), das vollständig auf Standard-C++ basiert und eine schnellere Leistung bietet.

## <a name="desktop-bridge"></a>Desktop-Brücke

In Windows 10 können Sie Ihre vorhandene Desktopanwendung oder Ihr COM-Objekt als UWP-App verpacken und UWP-Features wie Touch oder Aufruf-APIs aus dem modernen Windows-API-Satz hinzufügen. Sie können einer Desktoplösung in Visual Studio auch eine UWP-App hinzufügen und sie in einem einzigen Paket zusammenpacken und Windows-APIs für die Kommunikation zwischen ihnen verwenden.

Mit Visual Studio 2017 Version 15.4 und höher können Sie ein Windows-Anwendungspaketprojekt erstellen, um die Paketerstellung Ihrer vorhandenen Desktopanwendung erheblich zu vereinfachen. Für registrierungsaufrufe oder APIs, die Ihre Desktopanwendung verwenden kann, gelten einige Einschränkungen. In vielen Fällen können Sie jedoch alternative Codepfade erstellen, um ähnliche Funktionen zu erzielen, während Sie in einem App-Paket ausgeführt werden. Weitere Informationen finden Sie unter [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="games"></a>Spiele

DirectX-Spiele können auf dem PC oder auf der Xbox ausgeführt werden. Weitere Informationen finden Sie unter [DirectX Graphics and Gaming](/windows/win32/directx).

## <a name="sql-server-database-clients"></a>SQL Server-Datenbankclients

Verwenden Sie ODBC oder OLE DB, um über systemeigenen Code auf SQL Server-Datenbanken zuzugreifen. Weitere Informationen finden Sie unter [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

## <a name="windows-device-drivers"></a>Windows-Gerätetreiber

Treiber sind Low-Level-Komponenten, die Daten von Hardwaregeräten für Anwendungen und andere Betriebssystemkomponenten zugänglich machen. Weitere Informationen finden Sie unter [Windows Driver Kit (WDK)](/windows-hardware/drivers/index).

## <a name="windows-services"></a>Windows-Dienste

Ein *Windows-Dienst* ist ein Programm, das im Hintergrund mit wenig oder gar keiner Benutzerinteraktion ausgeführt werden kann. Diese Programme werden auf UNIX-Systemen *als Daemons* bezeichnet. Weitere Informationen finden Sie unter [Dienste](/windows/win32/services/services).

## <a name="sdks-libraries-and-header-files"></a>SDKs, Bibliotheken und Headerdateien

Visual Studio enthält die C-Runtime-Bibliothek (CRT), die C++-Standardbibliothek und andere Microsoft-spezifische Bibliotheken. Die meisten Include-Ordner, die Headerdateien für diese Bibliotheken enthalten, befinden sich im Visual Studio-Installationsverzeichnis unter dem Ordner "VC". Die Windows- und CRT-Headerdateien befinden sich im Windows SDK-Installationsordner.

Mit dem [Vcpkg-Paket-Manager](../build/vcpkg.md) können Sie bequem Hunderte von Open-Source-Bibliotheken von Drittanbietern für Windows installieren.

Zu den Microsoft-Bibliotheken gehören:

- Microsoft Foundation Classes (MFC): Ein objektorientiertes Framework zum Erstellen herkömmlicher Windows-Programme (im Besonderen Unternehmensanwendungen), die über komplexe Benutzeroberflächen mit Schaltflächen, Listenfeldern, Strukturansichten und anderen Steuerelementen verfügen. Weitere Informationen finden Sie unter [MFC Desktop Applications](../mfc/mfc-desktop-applications.md).

- Active Template Library (ATL): Eine leistungsstarke Hilfebibliothek zum Erstellen von COM-Komponenten. Weitere Informationen finden Sie unter [ATL COM Desktop Components](../atl/atl-com-desktop-components.md).

- C++ AMP (C++ Accelerated Massive Parallelism): Eine Bibliothek, die leistungsstarke allgemeine Computerarbeit auf der GPU ermöglicht. Weitere Informationen finden Sie unter [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Concurrency Runtime: Eine Bibliothek, mit der die Arbeit mit paralleler und asynchroner Programmierung für Viel- und Mehrkerngeräte vereinfacht wird. Weitere Informationen finden Sie unter [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

Viele Programmierszenarien bei Windows erfordern zudem das Windows SDK, in dem die Headerdateien enthalten sind, die den Zugriff auf Komponenten des Windows-Betriebssystems ermöglichen. Standardmäßig installiert Visual Studio das Windows SDK als Komponente der C++-Desktop-Workload, die die Entwicklung universeller Windows-Apps ermöglicht. Zum Entwickeln von UWP-Apps benötigen Sie die Windows 10-Version des Windows SDK. Weitere Informationen finden Sie unter [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk). (Weitere Informationen zu den Windows-SDKs für frühere Versionen von Windows finden Sie im [Windows SDK-Archiv](https://developer.microsoft.com/windows/downloads/sdk-archive)).

**Programmdateien (x86) - Windows Kits** ist der Standardspeicherort für alle Versionen des Windows SDK, die Sie installiert haben.

Für andere Plattformen, wie Xbox und Azure, sind eigene SDKs verfügbar, die sie ggf. installieren müssen. Weitere Informationen finden Sie im DirectX-Developer Center sowie im Azure Developer Center.

## <a name="development-tools"></a>Entwicklungstools

Visual Studio bietet einen leistungsfähigen Debugger für nativen Code, Tools für statische Analyse, Grafikdebugtools, einen umfassenden Code-Editor, Unterstützung für Komponententests und viele weitere Tools und Hilfsprogramme. Weitere Informationen finden Sie unter [Erste Schritte mit der Entwicklung mit Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio)und Übersicht über die [C++-Entwicklung in Visual Studio](../overview/overview-of-cpp-development.md).

## <a name="in-this-section"></a>In diesem Abschnitt

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Exemplarische Vorgehensweise: Erstellen eines Standard-C++-Programms](walkthrough-creating-a-standard-cpp-program-cpp.md)| Erstellen Sie eine Windows-Konsolenanwendung.|
|[Exemplarische Vorgehensweise: Erstellen von Windows-Desktopanwendungen (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|Erstellen Sie eine systemeigene Windows-Desktopanwendung.|
|[Windows Desktop-Assistent](windows-desktop-wizard.md)|Verwenden Sie den Assistenten, um neue Windows-Projekte zu erstellen.|
|[Active Template Library (ATL)](../atl/atl-com-desktop-components.md)|Verwenden Sie die ATL-Bibliothek, um COM-Komponenten in C++ zu erstellen.|
|[Microsoft Foundation Classes (MFC)](../mfc/mfc-desktop-applications.md)|Verwenden von MFC zum Erstellen großer oder kleiner Windows-Anwendungen mit Dialogfeldern und Steuerelementen|
|[FREIGEGEBENe ATL- und MFC-Klassen](../atl-mfc-shared/atl-mfc-shared-classes.md)|Verwenden Sie Klassen wie CString, die in ATL und MFC gemeinsam genutzt werden.|
|[Datenzugriff](../data/data-access-in-cpp.md)| OLE DB und ODBC|
|[Text und Zeichenfolgen](../text/text-and-strings-in-visual-cpp.md)|Verschiedene Zeichenfolgentypen unter Windows.|
|[Ressourcen zum Erstellen eines Spiels mit DirectX](resources-for-creating-a-game-using-directx.md)
|[Gewusst wie: Verwenden des Windows 10-SDKs in einer Windows-Desktopanwendung](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Windows SDK|
|[Arbeiten mit Ressourcendateien](working-with-resource-files.md)|Hinzufügen von Bildern, Symbolen, Zeichenfolgentabellen und anderen Ressourcen zu einer Desktopanwendung.|
|[Ressourcen zum Erstellen eines Spiels mit DirectX (C++)](resources-for-creating-a-game-using-directx.md)|Links zu Inhalten zum Erstellen von Spielen in C++.|
|[Gewusst wie: Verwenden des Windows 10-SDKs in einer Windows-Desktopanwendung](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Enthält Schritte zum Einrichten Ihres Projekts für das Erstellen mit dem Windows 10-SDK.|
|[Bereitstellen nativer Desktopanwendungen](deploying-native-desktop-applications-visual-cpp.md)|Stellen Sie systemeigene Anwendungen unter Windows bereit.|

## <a name="related-articles"></a>Verwandte Artikel

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[C++ in Visual Studio](../overview/visual-cpp-in-visual-studio.md)|Übergeordnetes Thema für Visual C++-Entwicklerinhalte.|
[.NET Entwicklung mit C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Erstellen Sie Wrapper für systemeigene C++-Bibliotheken, mit denen Sie mit .NET-Anwendungen und -Komponenten kommunizieren können.|
|[Komponentenerweiterungen für .NET und UWP](../extensions/component-extensions-for-runtime-platforms.md)|Referenz für Syntaxelemente, die von C++/CX und C++/CLI gemeinsam genutzt werden.|
|[Universelle Windows-Apps (C++)](../cppcx/universal-windows-apps-cpp.md)|Schreiben Sie UWP-Anwendungen mithilfe von C++/CX oder Windows Runtime Template Library (WRL).|
|[C++-Attribute für COM und .NET](attributes/cpp-attributes-com-net.md)|Nicht standardmäßige Attribute für die reine Windows-Programmierung mit .NET oder COM.|
