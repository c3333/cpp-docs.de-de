---
title: Übersicht über Windows-Programmierung in C++
ms.date: 09/17/2019
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: cd95332721f51ed2d17c3205cba5f1456a1037b9
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075488"
---
# <a name="overview-of-windows-programming-in-c"></a>Übersicht über Windows-Programmierung in C++

Es gibt mehrere allgemeine Kategorien von Windows-Anwendungen, die Sie mit C++erstellen können. Jede verfügt über ein eigenes Programmiermodell und eine Reihe von Windows-spezifischen Bibliotheken, C++ aber die Standardbibliothek und Bibliotheken C++ von Drittanbietern können in jedem verwendet werden.

In diesem Abschnitt wird erläutert, wie Visual Studio und die MFC/ATL-Wrapper Bibliotheken zum Erstellen von Windows-Programmen verwendet werden. Dokumentation zur Windows-Plattform selbst finden Sie in der [Windows-Dokumentation](/windows/index).

## <a name="command-line-console-applications"></a>Befehlszeilen Anwendungen (Konsolen Anwendungen)

C++Konsolen Anwendungen werden über die Befehlszeile in einem Konsolenfenster ausgeführt und können nur Textausgaben anzeigen. Weitere Informationen finden Sie unter [Erstellen eines C++ Konsolen-App-Projekts](../get-started/tutorial-console-cpp.md).

## <a name="native-desktop-client-applications"></a>Native Desktop-Client Anwendungen

Eine *native Desktop Client Anwendung* ist eine C- C++ oder Fenster-Anwendung, die die ursprünglichen System [eigenen Windows C-APIs oder-Component Object Model (com)-APIs](/windows/win32/apiindex/windows-api-list) für den Zugriff auf das Betriebssystem verwendet. Diese APIs werden größtenteils in C geschrieben. Es gibt mehrere Möglichkeiten, eine native Desktop-App zu erstellen: Sie können mithilfe der Win32-APIs direkt programmieren, indem Sie eine Nachrichten Schleife im C-Stil verwenden, die Betriebssystem Ereignisse verarbeitet. Oder Sie können mit *Microsoft Foundation Classes* (MFC) programmieren, einer leicht zu einem Objekt C++ orientierten Bibliothek, die Win32 umschließt. Beide Ansätze werden im Vergleich zum universelle Windows-Plattform (UWP) als "Modern" betrachtet, aber beide werden weiterhin vollständig unterstützt und verfügen heute über Millionen von Codezeilen. Eine Win32-Anwendung, die in einem-Fenster ausgeführt wird, erfordert, dass der Entwickler explizit mit Windows-Meldungen innerhalb einer Windows-Prozedur Funktion arbeitet. Trotz des Namens kann eine Win32-Anwendung als 32-Bit-(x86) oder 64-Bit-Binärdatei (x64) kompiliert werden. In der Visual Studio-IDE sind die Begriffe x86 und Win32 Synonym.

Informationen zu den ersten Schritten mit C++ der herkömmlichen Windows-Programmierung finden Sie unter [Get Started with Win32 and C++ ](/windows/win32/LearnWin32/learn-to-program-for-windows). Nachdem Sie sich mit Win32 vertraut machen, ist es einfacher, sich über [MFC-Desktop Anwendungen](../mfc/mfc-desktop-applications.md)zu informieren. Ein Beispiel für eine herkömmliche C++ Desktop Anwendung, die ausgereifte Grafiken verwendet, finden Sie unter [Hilo: entwickeln C++ von Anwendungen für Windows](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx).

### <a name="c-or-net"></a>C++oder .net?

Im Allgemeinen ist die .net- C# Programmierung in weniger komplex, weniger fehleranfällig und verfügt über eine modernere objektorientierte API als Win32 oder MFC. In den meisten Fällen ist die Leistung mehr als ausreichend. .Net bietet die Windows Presentation Foundation (WPF) für umfangreiche Grafiken, und Sie können sowohl Win32 als auch die moderne Windows-Runtime-API nutzen. Als allgemeine Regel empfiehlt es sich, für C++ Desktop Anwendungen zu verwenden, wenn Folgendes erforderlich ist:

- genaue Kontrolle der Speicherauslastung
- der größte Energieverbrauch im Energieverbrauch
- Verwendung der GPU für allgemeines Computing
- Zugriff auf DirectX
- hohe Nutzung von Standard C++ Bibliotheken

Es ist auch möglich, die Leistung und Effizienz von C++ mit der .NET-Programmierung zu kombinieren. Sie können in C# eine Benutzeroberfläche erstellen und/CLI C++verwenden, um die Anwendung für die Verwendung C++ nativer Bibliotheken zu aktivieren. Weitere Informationen finden Sie unter [.NET-Programmierung C++mit/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

## <a name="com-components"></a>COM-Komponenten

Der [Component Object Model (com)](/windows/win32/com/the-component-object-model) ist eine Spezifikation, mit der Programme, die in verschiedenen Sprachen geschrieben wurden, miteinander kommunizieren können. Viele Windows-Komponenten werden als COM-Objekte implementiert und befolgen die com-Standardregeln für Objekt Erstellung, Schnittstellen Ermittlung und Objekt Zerstörung.  Die Verwendung von com C++ -Objekten aus Desktop Anwendungen ist relativ unkompliziert, aber das Schreiben eines eigenen com-Objekts ist fortschrittlicher. Der [Active Template Library (ATL)](../atl/atl-com-desktop-components.md) stellt Makros und Hilfsfunktionen bereit, die die com-Entwicklung vereinfachen. Weitere Informationen finden Sie unter [ATL-COM-Desktop Komponenten](../atl/atl-com-desktop-components.md).

## <a name="universal-windows-platform-apps"></a>Universelle Windows-Plattform-Apps

Die universelle Windows-Plattform (UWP) ist die moderne Windows-API. UWP-Apps können auf jedem Windows 10-Gerät ausgeführt werden, verwenden XAML für die Benutzeroberfläche und sind vollständig Berührungs fähig. Weitere Informationen zu UWP finden Sie unter [Was ist eine universelle Windows-Plattform-app (UWP)?](/windows/uwp/get-started/whats-a-uwp) und [Leitfaden zu universellen Windows-apps](/windows/uwp/get-started/universal-application-platform-guide).

Die ursprüngliche C++ Unterstützung für UWP umfasste (1) C++/CX, einen Dialekt von C++ mit Syntax Erweiterungen oder (2) die Windows-Runtime-Bibliothek (WRL), die auf Standard C++ und com basiert. Sowohl C++/CX als auch WRL werden weiterhin unterstützt. Für neue Projekte wird [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)empfohlen, das vollständig auf Standard C++ basiert und eine schnellere Leistung bietet.

## <a name="desktop-bridge"></a>Desktop Bridge

In Windows 10 können Sie Ihre vorhandene Desktop Anwendung oder Ihr COM-Objekt als UWP-App Verpacken und UWP-Features wie Finger Eingaben hinzufügen oder APIs aus dem modernen Windows-API-Satz abrufen. Sie können eine UWP-APP auch einer Desktop Projekt Mappe in Visual Studio hinzufügen und Sie in einem einzelnen Paket Verpacken und Windows-APIs für die Kommunikation zwischen Ihnen verwenden.

Mit Visual Studio 2017 Version 15,4 und höher können Sie ein Windows-Anwendungspaket Projekt erstellen, um die Arbeit beim Verpacken Ihrer vorhandenen Desktop Anwendung erheblich zu vereinfachen. Es gelten einige Einschränkungen für die Registrierungs Aufrufe oder APIs, die von Ihrer Desktop Anwendung verwendet werden können. In vielen Fällen können Sie jedoch alternative Codepfade erstellen, um eine ähnliche Funktionalität zu erzielen, während Sie in einem App-Paket ausgeführt werden. Weitere Informationen finden Sie unter [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="games"></a>Spiele

DirectX-Spiele können auf dem PC oder der Xbox ausgeführt werden. Weitere Informationen finden Sie unter [DirectX-Grafiken und-Spiele](/windows/win32/directx).

## <a name="sql-server-database-clients"></a>Daten Bank Clients SQL Server

Verwenden Sie zum Zugreifen auf SQL Server Datenbanken aus nativem Code ODBC oder OLE DB. Weitere Informationen finden Sie unter [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

## <a name="windows-device-drivers"></a>Windows-Gerätetreiber

Treiber sind Low-Level-Komponenten, die Daten von Hardware Geräten für Anwendungen und andere Betriebssystemkomponenten zugänglich machen. Weitere Informationen finden Sie unter [Windows-Treiberkit (WDK)](/windows-hardware/drivers/index).

## <a name="windows-services"></a>Windows-Dienste

Ein Windows- *Dienst* ist ein Programm, das im Hintergrund mit wenig oder ohne Benutzerinteraktion ausgeführt werden kann. Diese Programme werden als *Daemons* auf UNIX-Systemen bezeichnet. Weitere Informationen finden Sie unter [Dienste](/windows/win32/services/services).

## <a name="sdks-libraries-and-header-files"></a>Sdche, Bibliotheken und Header Dateien

Visual Studio enthält die C-Lauf Zeit Bibliothek (C Runtime C++ Library, CRT), die Standard Bibliothek und andere Microsoft-spezifische Bibliotheken. Die meisten der include-Ordner, die Header Dateien für diese Bibliotheken enthalten, befinden sich im Visual Studio-Installationsverzeichnis im Ordner \vc\. Die Windows-und CRT-Header Dateien finden Sie im Windows SDK-Installationsordner.

Der [vcpkg-Paket-Manager](../build/vcpkg.md) ermöglicht Ihnen die bequeme Installation von Hunderten von Open-Source-Bibliotheken von Drittanbietern für Windows.

Die Microsoft-Bibliotheken umfassen Folgendes:

- Microsoft Foundation Classes (MFC): Ein objektorientiertes Framework zum Erstellen herkömmlicher Windows-Programme (im Besonderen Unternehmensanwendungen), die über komplexe Benutzeroberflächen mit Schaltflächen, Listenfeldern, Strukturansichten und anderen Steuerelementen verfügen. Weitere Informationen finden Sie unter [MFC Desktop Applications](../mfc/mfc-desktop-applications.md).

- Active Template Library (ATL): Eine leistungsstarke Hilfebibliothek zum Erstellen von COM-Komponenten. Weitere Informationen finden Sie unter [ATL COM Desktop Components](../atl/atl-com-desktop-components.md).

- C++ AMP (C++ Accelerated Massive Parallelism): Eine Bibliothek, die leistungsstarke allgemeine Computerarbeit auf der GPU ermöglicht. Weitere Informationen finden Sie unter [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Concurrency Runtime: Eine Bibliothek, mit der die Arbeit mit paralleler und asynchroner Programmierung für Viel- und Mehrkerngeräte vereinfacht wird. Weitere Informationen finden Sie unter [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

Viele Programmierszenarien bei Windows erfordern zudem das Windows SDK, in dem die Headerdateien enthalten sind, die den Zugriff auf Komponenten des Windows-Betriebssystems ermöglichen. Standardmäßig installiert Visual Studio die Windows SDK als Komponente der C++ Desktop Arbeitsauslastung, die die Entwicklung von universellen Windows-Apps ermöglicht. Zum Entwickeln von UWP-apps benötigen Sie die Windows 10-Version der Windows SDK. Weitere Informationen finden Sie unter [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk). (Weitere Informationen zu den Windows sdert für frühere Versionen von Windows finden Sie im [Windows SDK Archiv](https://developer.microsoft.com/windows/downloads/sdk-archive)).

**Programmdateien (x86) \Windows Kits** ist der Standard Speicherort für alle Versionen der Windows SDK, die Sie installiert haben.

Für andere Plattformen, wie Xbox und Azure, sind eigene SDKs verfügbar, die sie ggf. installieren müssen. Weitere Informationen finden Sie im DirectX-Developer Center sowie im Azure Developer Center.

## <a name="development-tools"></a>Entwicklungstools

Visual Studio bietet einen leistungsfähigen Debugger für nativen Code, Tools für statische Analyse, Grafikdebugtools, einen umfassenden Code-Editor, Unterstützung für Komponententests und viele weitere Tools und Hilfsprogramme. Weitere Informationen finden Sie unter "Einstieg in die Entwicklung [mit Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio)" und [ C++ in der Übersicht über die Entwicklung in Visual Studio](../overview/overview-of-cpp-development.md).

## <a name="in-this-section"></a>In diesem Abschnitt
|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Exemplarische Vorgehensweise: Erstellen C++ eines Standard Programms](walkthrough-creating-a-standard-cpp-program-cpp.md)| Erstellen Sie eine Windows-Konsolenanwendung.|
|[Exemplarische Vorgehensweise: Erstellen von Windows-Desktopanwendungen (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|Erstellen Sie eine native Windows-Desktop Anwendung.|
|[Windows-Desktopassistent](windows-desktop-wizard.md)|Verwenden Sie den Assistenten, um neue Windows-Projekte zu erstellen.|
|[Active Template Library (ATL)](../atl/atl-com-desktop-components.md)|Verwenden Sie die ATL-Bibliothek, um com C++-Komponenten in zu erstellen.|
|[Microsoft Foundation Classes (MFC)](../mfc/mfc-desktop-applications.md)|Verwenden von MFC zum Erstellen großer oder kleiner Windows-Anwendungen mit Dialogfeldern und Steuerelementen|
|[Freigegebene ATL- und MFC-Klassen](../atl-mfc-shared/atl-mfc-shared-classes.md)|Verwenden Sie Klassen wie CString, die in ATL und MFC gemeinsam verwendet werden.|
|[Datenzugriff](../data/data-access-in-cpp.md)| OLE DB und ODBC|
|[Text und Zeichenfolgen](../text/text-and-strings-in-visual-cpp.md)|Verschiedene Zeichen folgen Typen unter Windows.|
|[Ressourcen zum Erstellen eines Spiels mit DirectX](resources-for-creating-a-game-using-directx.md)
|[Gewusst wie: Verwenden des Windows 10-SDKs in einer Windows-Desktopanwendung](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Windows SDK|
|[Arbeiten mit Ressourcendateien](working-with-resource-files.md)|Hinzufügen von Bildern, Symbolen, Zeichen folgen Tabellen und anderen Ressourcen zu einer Desktop Anwendung.|
|[Ressourcen zum Erstellen eines Spiels mit DirectX (C++)](resources-for-creating-a-game-using-directx.md)|Links zu Inhalten zum Erstellen von spielen C++in.|
|[Gewusst wie: Verwenden des Windows 10-SDKs in einer Windows-Desktopanwendung](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Enthält Schritte zum Einrichten Ihres Projekts für das Erstellen mit dem Windows 10-SDK.|
|[Bereitstellen nativer Desktopanwendungen](deploying-native-desktop-applications-visual-cpp.md)|Stellen Sie native Anwendungen unter Windows bereit.|

## <a name="related-articles"></a>Verwandte Artikel

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[C++ in Visual Studio](../overview/visual-cpp-in-visual-studio.md)|Übergeordnetes Thema für C++ visuellen Entwickler Inhalt.|
[.NET-Entwicklung mit C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Erstellen Sie Wrapper für Native C++ Bibliotheken, die die Kommunikation mit .NET-Anwendungen und-Komponenten ermöglichen.|
|[Komponentenerweiterungen für .NET und UWP](../extensions/component-extensions-for-runtime-platforms.md)|Verweis für Syntax Elemente, die C++von/CX C++und/CLI. gemeinsam genutzt werden|
|[Universelle Windows-Apps (C++)](../cppcx/universal-windows-apps-cpp.md)|Schreiben Sie UWP- C++Anwendungen mithilfe von/CX oder Windows-Runtime Template Library (WRL).|
|[C++-Attribute für COM und .NET](attributes/cpp-attributes-com-net.md)|Nicht dem Standard entsprechende Attribute für die reine Windows-Programmierung mit .net oder com.|
