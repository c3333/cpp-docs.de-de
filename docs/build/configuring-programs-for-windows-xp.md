---
title: Konfigurieren von Programmen für Windows XP
description: Installieren und Verwenden der C++ Windows XP-Toolsets in Visual Studio
ms.date: 03/16/2020
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
ms.openlocfilehash: 92364d7fd25ac617baacc125b279fb0ee9c92f62
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440480"
---
# <a name="configuring-programs-for-windows-xp"></a>Konfigurieren von Programmen für Windows XP

Visual Studio unterstützt mehrere Platt Form Toolsets. Dies bedeutet, dass es möglich ist, Betriebssysteme und Laufzeitbibliotheken als Ziel festzulegen, die vom Standard Toolset nicht unterstützt werden. Wenn Sie z. b. das Platt Form Toolset wechseln, können Sie den Visual C++ Studio 2017-Compiler verwenden, um apps zu erstellen, die auf Windows XP und Windows Server 2003 abzielen. Sie können auch ältere Plattformtoolsets verwenden, um binärkompatiblen Legacycode zu verwalten und dennoch die neuesten Funktionen der Visual Studio-IDE zu nutzen.

::: moniker range="vs-2019"

Das in Visual Studio 2019 bereitgestellte v142-Toolset bietet keine Unterstützung für das Erstellen von Code für Windows XP. Unterstützung für die Windows XP-Entwicklung mithilfe von Visual Studio 2017 v141_xp Toolset ist als einzelne Komponenten Option in der Visual Studio-Installer verfügbar.

::: moniker-end

## <a name="install-the-windows-xp-platform-toolset"></a>Installieren des Windows XP-Plattformtoolsets

::: moniker range="<=vs-2017"

Um das Visual Studio 2017-Platt Form Toolset und die Komponenten für Windows XP und Windows Server 2003 zu erhalten, führen Sie den Visual Studio-Installer aus. Wenn Sie Visual Studio zum ersten Mal installieren oder eine vorhandene Installation ändern, stellen Sie sicher, dass die Option **Desktop Entwicklung mit C++**  Arbeitsauslastung ausgewählt ist. Wählen Sie in der Liste der optionalen Komponenten für diese Workload **Windows XP-Unterstützung für C++** und dann **Installieren** oder **Ändern** aus.

::: moniker-end

::: moniker range="vs-2019"

Um das v141_xp Platt Form Toolset und die Komponenten für Windows XP und Windows Server 2003 zu erhalten, führen Sie den Visual Studio-Installer aus. Wenn Sie Visual Studio zum ersten Mal installieren oder wenn Sie eine vorhandene Installation ändern, stellen Sie sicher, dass die Option **Desktop Entwicklung mit C++**  Arbeitsauslastung ausgewählt ist. Wählen Sie **Install** **Modify** **Individual components** **Compilers, build tools, and runtimes**auf der Registerkarte einzelne Komponenten unter Compiler, Buildtools und Laufzeiten die Option **Windows XP-Unterstützung für vs 2017 (v141) Tools aus, \[veraltet], und wählen Sie dann installieren oder ändern aus. C++**

::: moniker-end

## <a name="windows-xp-targeting-experience"></a>Windows XP als Ziel

Das Windows XP-Platt Form Toolset, das in Visual Studio enthalten ist, ist eine Version des Windows 7 SDK, aber es verwendet den C++ Visual Studio 2017-Compiler. Es konfiguriert außerdem Projekteigenschaften auf entsprechende Standardwerte, beispielsweise durch Angabe eines mit älteren Zielplattformen kompatiblen Linkers. Nur Windows-Desktop-Apps, die mit einem Windows XP-Platt Form Toolset erstellt wurden, können unter Windows XP und Windows Server 2003 ausgeführt werden. Diese Apps können auch auf neueren Windows-Betriebssystemen ausgeführt werden.

### <a name="to-target-windows-xp"></a>So entwickeln Sie für Windows XP

1. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für das Projekt, und wählen Sie **Eigenschaften** aus.

1. Wählen Sie im Dialogfeld Eigenschaften **Seiten** für das Projekt die Option **Konfigurations Eigenschaften** > **Allgemein**aus. Legen Sie die Eigenschaft **Platt Form Toolset** auf Ihr bevorzugtes Windows XP-Toolset fest. Wählen Sie beispielsweise **Visual Studio 2017 – Windows XP (v141_xp)** aus, um Code für Windows XP und Windows Server 2003 mithilfe des Microsoft C++-Compilers in Visual Studio 2017 zu erstellen.

### <a name="c-runtime-support"></a>C++-Laufzeitunterstützung

Zusammen mit dem Windows XP-Platt Form Toolset enthalten mehrere Bibliotheken Laufzeitunterstützung für Windows XP und Windows Server 2003. Diese Bibliotheken sind: die C-Lauf Zeit Bibliothek (CRT C++ ), Standard Bibliothek, Active Template Library (ATL), Concurrency Runtime Library (ConcRT), Parallel Patterns Library (PPL), Microsoft Foundation Class-Bibliothek (MFC) C++ und ampC++ (Accelerated massive Programming) Library. Für diese Betriebssysteme gelten die mindestens unterstützten Versionen: Windows XP Service Pack 3 (SP3) für x86, Windows XP Service Pack 2 (SP2) für x64 und Windows Server 2003 Service Pack 2 (SP2) für x86 und x64.

Diese Bibliotheken werden von den von Visual Studio installierten Plattformtoolsets unterstützt, abhängig vom Ziel:

|Bibliothek|Standard-Plattformtoolset mit Windows-Desktop-Apps als Ziel|Standard-Plattformtoolset mit Store-Apps als Ziel|Windows XP-Plattformtoolset mit Windows XP, Windows Server 2003 als Ziel|
|---|---|---|---|
|CRT|X|X|X|
|C++-Standardbibliothek|X|X|X|
|ATL|X|X|X|
|ConCRT/PPL|X|X|X|
|MFC|X||X|
|C++ AMP|X|X||

> [!NOTE]
> Apps, die in C++/CLI geschrieben sind und .NET Framework 4 als Ziel haben, können unter Windows XP und Windows Server 2003 ausgeführt werden.

### <a name="differences-between-the-toolsets"></a>Unterschiede zwischen den Toolsets

Aufgrund von Unterschieden bei der Platt Form-und Bibliotheks Unterstützung ist das Entwicklungsverfahren für apps, die ein Windows XP-Platt Form Toolset verwenden, nicht so komplett wie für apps, die das standardmäßige Visual Studio-Platt Form Toolset verwenden.

- **Funktionen der Programmiersprache C++**

   In Apps, die das v110\_xp-Plattformtoolset verwenden, werden nur die Funktionen der Programmiersprache C++unterstützt, die in Visual Studio 2012 implementiert sind. In Apps, die das v120\_xp-Plattformtoolset verwenden, werden nur die Funktionen der Programmiersprache C++unterstützt, die in Visual Studio 2013 implementiert sind. In Apps, die das v140\_xp-Plattformtoolset verwenden, werden nur die Funktionen der Programmiersprache C++unterstützt, die in Visual Studio 2015 implementiert sind. In C++ apps, die das v141\_XP-Platt Form Toolset verwenden, werden nur sprach Features unterstützt, die in Visual Studio 2017 implementiert werden. Visual Studio verwendet für Builds mit den älteren Plattformtoolsets den entsprechenden Compiler. Verwenden Sie das neueste Windows XP-Plattformtoolset, um weitere C++-Features zu nutzen, die in dieser Version des Compilers implementiert sind.

- **Remotedebuggen**

   Die Remotetools für Visual Studio unterstützen kein Remotedebuggen unter Windows XP oder Windows Server 2003. Verwenden Sie zum lokalen Debuggen einer APP unter Windows XP oder Windows Server 2003 einen Debugger aus einer älteren Version von Visual Studio. Dies ähnelt dem Debuggen einer APP unter Windows Vista, bei der es sich um ein Lauf Zeit Ziel des Platt Form Toolsets handelt, aber kein remotedebuggingziel.

- **Statische Analyse**

   Die Windows XP-Plattformtoolsets unterstützen keine statischen Analysen, da die SAL-Anmerkungen für das Windows 7-SDK und die Laufzeitbibliotheken nicht kompatibel sind. Sie können weiterhin eine statische Analyse für eine APP durchführen, die Windows XP oder Windows Server 2003 unterstützt. Wechseln Sie vorübergehend zum Ziel der Standardplattform für die Analyse, und wechseln Sie dann zurück zum Windows XP-Platt Form Toolset, um die APP zu erstellen.

- **Debuggen von DirectX-Grafiken**

   Da der Grafik Debugger die Direct3D 9-API nicht unterstützt, kann er nicht zum Debuggen von apps verwendet werden, die Direct3D unter Windows XP oder Windows Server 2003 verwenden. Wenn die APP jedoch einen alternativen Renderer implementiert, der auf Direct3D 10-oder Direct3D 11-APIs basiert, können Sie den Grafik Debugger verwenden, um Probleme zu diagnostizieren.

- **Erstellen von HLSL**

   Der Windows XP-Toolset kompiliert standardmäßig keine HLSL-Quell Code Dateien. Zur Kompilierung von HLSL-Dateien laden Sie das June 2010 DirectX SDK herunter und installieren es und legen dann die VC-Verzeichnisse des Projekts so fest, dass es eingeschlossen ist. Weitere Informationen finden Sie im Abschnitt „DirectX-SDK registriert keine Include/Library-Pfade bei Visual Studio 2010“ der [June 2010 DirectX SDK-Downloadseite](https://www.microsoft.com/download/details.aspx?displaylang=en&id=6812).
