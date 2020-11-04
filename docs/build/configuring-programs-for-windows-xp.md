---
title: Konfigurieren von Programmen für Windows XP
description: Erfahren Sie, wie Sie C++-Toolsets für Windows XP in Visual Studio installieren und verwenden.
ms.date: 03/16/2020
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
ms.openlocfilehash: 09fe1a511c92f999e02646b9e606a3631a175215
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919370"
---
# <a name="configuring-programs-for-windows-xp"></a>Konfigurieren von Programmen für Windows XP

Visual Studio unterstützt mehrere Plattformtoolsets. Das bedeutet, Sie können Zielbetriebssysteme und Ziellaufzeitbibliotheken festlegen, die nicht vom Standardtoolset unterstützt werden. Indem Sie das Plattformtoolset wechseln, können Sie beispielsweise den Visual Studio 2017-C++-Compiler verwenden, um Apps für Windows XP und Windows Server 2003 zu erstellen. Sie können auch ältere Plattformtoolsets verwenden, um binärkompatiblen Legacycode zu verwalten und dennoch die neuesten Funktionen der Visual Studio-IDE zu nutzen.

::: moniker range="msvc-160"

Das v142-Toolset, das in Visual Studio 2019 enthalten ist, umfasst keine Unterstützung zum Erstellen von Code für Windows XP. Die Unterstützung der Windows XP-Entwicklung mithilfe des Visual Studio 2017-v141_xp-Toolsets steht im Visual Studio-Installer als Einzelkomponente zur Verfügung.

::: moniker-end

## <a name="install-the-windows-xp-platform-toolset"></a>Installieren des Windows XP-Plattformtoolsets

::: moniker range="<=msvc-150"

Führen Sie den Visual Studio-Installer aus, um das Visual Studio 2017-Plattformtoolset und die -Komponenten für Windows XP und Windows Server 2003 abzurufen. Achten Sie bei der erstmaligen Installation von Visual Studio oder beim Anpassen einer bestehenden Installation darauf, dass die Workload **Desktopentwicklung mit C++** ausgewählt ist. Wählen Sie in der Liste der optionalen Komponenten für diese Workload **Windows XP-Unterstützung für C++** und dann **Installieren** oder **Ändern** aus.

::: moniker-end

::: moniker range="msvc-160"

Führen Sie den Visual Studio-Installer aus, um das v141_xp-Plattformtoolset und die -Komponenten für Windows XP und Windows Server 2003 abzurufen. Achten Sie bei der erstmaligen Installation von Visual Studio oder beim Anpassen einer bestehenden Installation darauf, dass die Workload **Desktopentwicklung mit C++** ausgewählt ist. Wählen Sie auf der Registerkarte **Einzelne Komponenten** unter **Compilers, build tools, and runtimes** (Compiler, Buildtools und Runtimes) die Option **C++-Windows XP-Unterstützung für Tools in VS 2017 (v141) \[veraltet]** aus, und klicken Sie dann auf **Installieren** oder **Modify**.

::: moniker-end

## <a name="windows-xp-targeting-experience"></a>Windows XP als Ziel

Das in Visual Studio enthaltene Windows XP-Plattformtoolset ist eine Version des Windows 7 SDK, es verwendet jedoch den Visual Studio 2017-C++-Compiler. Es konfiguriert außerdem Projekteigenschaften auf entsprechende Standardwerte, beispielsweise durch Angabe eines mit älteren Zielplattformen kompatiblen Linkers. Nur Windows-Desktop-Apps, die mithilfe eines Windows XP-Plattformtoolsets erstellt wurden, können unter Windows XP und Windows Server 2003 ausgeführt werden. Diese Apps können auch auf aktuelleren Windows-Betriebssystemen ausgeführt werden.

### <a name="to-target-windows-xp"></a>So entwickeln Sie für Windows XP

1. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für das Projekt, und wählen Sie **Eigenschaften** aus.

1. Klicken Sie im Dialogfeld **Eigenschaftenseiten** für das Projekt auf **Konfigurationseigenschaften** > **Allgemein**. Legen Sie die Eigenschaft **Plattformtoolset** auf Ihr bevorzugtes Windows XP-Toolset fest. Wählen Sie beispielsweise **Visual Studio 2017 – Windows XP (v141_xp)** aus, um Code für Windows XP und Windows Server 2003 mithilfe des Microsoft C++-Compilers in Visual Studio 2017 zu erstellen.

### <a name="c-runtime-support"></a>C++-Laufzeitunterstützung

Neben dem Windows XP-Plattformtoolset umfassen mehrere Bibliotheken die Runtimeunterstützung für Windows XP und Windows Server 2003. Dazu gehören die folgenden: die C-Laufzeitbibliothek (CRT), die C++-Standardbibliothek, die Active Template Library (ATL), die Concurrency Runtime-Bibliothek (ConCRT), die Parallel Patterns Library (PPL), die Microsoft Foundation Class-Bibliothek (MFC) und die C++ AMP-Bibliothek (C++ Accelerated Massive Programming). Die unterstützten Mindestversionen für diese Betriebssysteme sind: Windows XP Service Pack 3 (SP3) für x86, Windows XP Service Pack 2 (SP2) für x64 und Windows Server 2003 Service Pack 2 (SP2) sowohl für x86 als auch für x64.

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

Aufgrund von Unterschieden bei Plattform- und Bibliotheksunterstützung ist die Entwicklungsumgebung für Apps, die ein Windows XP-Plattformtoolset verwenden, nicht so umfassend wie für Apps, die das standardmäßige Visual Studio-Plattformtoolset verwenden.

- **Funktionen der Programmiersprache C++**

   In Apps, die das v110\_xp-Plattformtoolset verwenden, werden nur die Funktionen der Programmiersprache C++unterstützt, die in Visual Studio 2012 implementiert sind. In Apps, die das v120\_xp-Plattformtoolset verwenden, werden nur die Funktionen der Programmiersprache C++unterstützt, die in Visual Studio 2013 implementiert sind. In Apps, die das v140\_xp-Plattformtoolset verwenden, werden nur die Funktionen der Programmiersprache C++unterstützt, die in Visual Studio 2015 implementiert sind. In Apps, die das v141\_xp-Plattformtoolset verwenden, werden nur die Funktionen der Programmiersprache C++unterstützt, die in Visual Studio 2017 implementiert sind. Visual Studio verwendet für Builds mit den älteren Plattformtoolsets den entsprechenden Compiler. Verwenden Sie das neueste Windows XP-Plattformtoolset, um weitere C++-Features zu nutzen, die in dieser Version des Compilers implementiert sind.

- **Remotedebuggen**

   Die Remotetools für Visual Studio unterstützen kein Remotedebuggen unter Windows XP oder Windows Server 2003. Verwenden Sie einen Debugger einer älteren Version von Visual Studio, um eine App lokal oder remote unter Windows XP oder Windows Server 2003 zu debuggen. Dies ähnelt dem Debuggen einer App unter Windows Vista, das ein Runtimeziel des Plattformtoolsets, aber kein Remotedebuggingziel ist.

- **Statische Analyse**

   Die Windows XP-Plattformtoolsets unterstützen keine statischen Analysen, da die SAL-Anmerkungen für das Windows 7-SDK und die Laufzeitbibliotheken nicht kompatibel sind. Sie können weiterhin statische Analysen für eine App durchführen, die Windows XP oder Windows Server 2003 unterstützt. Wechseln Sie das Ziel der Lösung für die Analyse vorübergehend zum Standardplattformtoolset, und wechseln Sie dann zurück zum Windows XP-Plattformtoolset, um die App zu erstellen.

- **Debuggen von DirectX-Grafiken**

   Da der Grafikdebugger die Direct3D 9-API nicht unterstützt, kann er nicht zum Debuggen von Apps verwendet werden, die Direct3D unter Windows XP oder Windows Server 2003 verwenden. Wenn die App jedoch einen alternativen Renderer implementiert, der auf der Direct3D 10- oder der Direct3D 11-API basiert, können Sie den Grafikdebugger zum Diagnostizieren von Problemen verwenden.

- **Erstellen von HLSL**

   Standardmäßig kompiliert das Windows XP-Toolset keine HLSL-Quellcodedateien. Zur Kompilierung von HLSL-Dateien laden Sie das June 2010 DirectX SDK herunter und installieren es und legen dann die VC-Verzeichnisse des Projekts so fest, dass es eingeschlossen ist. Weitere Informationen finden Sie im Abschnitt „DirectX-SDK registriert keine Include/Library-Pfade bei Visual Studio 2010“ der [June 2010 DirectX SDK-Downloadseite](https://www.microsoft.com/download/details.aspx?displaylang=en&id=6812).
