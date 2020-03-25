---
title: Verteilen von Visual C++-Dateien
ms.date: 11/04/2016
helpviewer_keywords:
- application deployment [C++], file redistributing
- redistributing applications [C++]
- deploying applications [C++], file redistributing
- file redistribution [C++]
- redistributing applications [C++], about redistributing applications
ms.assetid: d201b2ce-36f1-44e5-a96c-0db81a1ba652
ms.openlocfilehash: 46192fe7ff5b29c22a5001cc460c74f5ddf6d1bb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167926"
---
# <a name="redistributing-visual-c-files"></a>Verteilen von Visual C++-Dateien

> [!NOTE]
> Möchten Sie eine der Visual C++-Runtimedateien herunterladen? Wechseln Sie zur [Microsoft-Website](https://www.microsoft.com/) , und geben Sie **Visual C++ Redistributable** in das Suchfeld ein. Laden Sie das verteilbare Paket für die Architektur Ihres Computers (z.B. x64, wenn Sie 64-Bit-Windows ausführen) und die erforderliche Version von Visual C++ (z.B. 2015) herunter, und installieren Sie diese.

Wenn Sie eine Anwendung bereitstellen, müssen Sie auch die Dateien bereitstellen, die zu ihrer Unterstützung erforderlich sind. Wenn eine dieser Dateien von Microsoft zur Verfügung gestellt wird, überprüfen Sie, ob Sie sie weiterverteilen dürfen. Weitere Informationen zu den Visual Studio-Lizenzbedingungen finden Sie über den Link „Lizenzbedingungen“ im Dialogfeld „Info zu Microsoft Visual Studio“ in der IDE. Alternativ können Sie die Datei [Microsoft-Softwarelizenzbedingungen](https://visualstudio.microsoft.com/license-terms/mlt687465/) herunterladen. Informationen zum Anzeigen der „REDIST-Liste“, auf die im Abschnitt „Verteilbarer Code“ der Microsoft-Softwarelizenzbedingungen für bestimmte Editionen von Visual Studio verwiesen wird, finden Sie unter [Distributable Code for Microsoft Visual Studio 2017 and Microsoft Visual Studio 2017 SDK (Includes Utilities and BuildServer Files) (Verteilbarer Code für Microsoft Visual Studio 2017 oder Microsoft Visual Studio 2017 SDK (einschließlich Hilfsprogramme und BuildServer-Dateien))](/visualstudio/productinfo/2017-redistribution-vs). Für Visual Studio 2015 finden Sie diese unter [Distributable Code for Microsoft Visual Studio 2015 and Microsoft Visual Studio 2015 SDK (Verteilbarer Code für Microsoft Visual Studio 2015 und Microsoft Visual Studio 2015 SDK)](/visualstudio/productinfo/2015-redistribution-vs). Weitere Informationen zu verteilbaren Dateien finden Sie unter [Ermitteln der zu verteilenden DLLs](determining-which-dlls-to-redistribute.md) und [Bereitstellungsbeispiele](deployment-examples.md).

Zum Bereitstellen von verteilbaren Visual C++-Dateien können Sie die Visual C++ Redistributable Packages (VCRedist\_x86.exe, VCRedist\_x64.exe, oder VCRedist\_arm.exe) verwenden, die in Visual Studio enthalten sind. Für Visual Studio 2017 befinden sich diese Dateien im Ordner „Programme (x86)\\Microsoft Visual Studio\\2017\\_Edition_\\VC\\Redist\\MSVC\\_Bibliotheksversion_“. Hierbei steht _Edition_ für die installierte Edition von Visual Studio und _Bibliotheksversion_ für die Version der zu verteilenden Bibliotheken. In Visual Studio 2015 befinden sich diese Dateien im Visual Studio-Installationsverzeichnis unter „Programme (x86)\Microsoft Visual Studio *version*\VC\redist\\*locale*\\“. Eine weitere Möglichkeit besteht in der Verwendung von verteilbaren Mergemodulen (MSM-Dateien), die sich in Visual Studio 2017 im Ordner „Programme (x86)\\Microsoft Visual Studio\\2017\\_Edition_\\VC\\Redist\\MSVC\\_Bibliotheksversion_\\MergeModules\\“ befinden. In Visual Studio 2015 befinden sich diese unter „Programme (x86)\Common Files\Merge Modules\\“. Es ist auch möglich, verteilbare Visual C++-DLLs direkt in den *lokalen Anwendungsordner* zu installieren. Dabei handelt es sich um den Ordner, der die ausführbare Anwendungsdatei enthält. Aus Wartungsgründen empfehlen wir, diesen Speicherort nicht für die Installation zu verwenden.

Die weiterverteilbaren Visual C++-Pakete installieren und registrieren alle Visual C++-Bibliotheken. Wenn Sie eines von ihnen verwenden, müssen Sie es so konfigurieren, dass es auf dem Zielsystem als erforderliche Komponente für die Installation Ihrer Anwendung ausgeführt wird. Es wird empfohlen, dass Sie diese Pakete für die Bereitstellungen verwenden, da Sie die automatische Aktualisierung von Visual C++-Bibliotheken ermöglichen. Ein Beispiel zur Verwendung dieser Pakete finden Sie unter [Exemplarische Vorgehensweise: Bereitstellen einer Visual C++-Anwendung mithilfe von Visual C++ Redistributable Package](deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).

Jedes Visual C++ Redistributable Package überprüft das Vorhandensein einer aktuelleren Version auf dem Computer. Wenn eine neuere Version gefunden wird, wird das Paket nicht installiert. Ab Visual Studio 2015 zeigen verteilbare Pakete eine Fehlermeldung an, die darauf hinweist, dass ein Fehler beim Setup aufgetreten ist. Wenn ein Paket mit dem Flag **/quiet** ausgeführt wird, wird keine Fehlermeldung angezeigt. In beiden Fällen wird ein Fehler im Microsoft Installer protokolliert und ein Fehlerergebnis wird an den Aufrufenden zurückgegeben. Mit Paketen ab Visual Studio 2015 können Sie diesen Fehler vermeiden, indem Sie die Registrierung überprüfen, um herauszufinden, ob eine neuere Version installiert ist. Die derzeit installierte Version wird im Schlüssel „HKEY_LOCAL_MACHINE\SOFTWARE[\Wow6432Node]\Microsoft\VisualStudio\\_vs-version_\VC\Runtimes\\{x86|x64|ARM}“ gespeichert. Hierbei entspricht _vs-version_ der Versionsnummer von Visual Studio (14.0 für Visual Studio 2015 und 2017, da die verteilbare Komponente für 2017 mit der 2015-Version binärkompatibel ist). Der Schlüssel ist „ARM“, „x86“ oder „x64“, je nachdem, welche vcredist-Versionen für die Plattform installiert wurden. (Sie müssen nicht den Wow6432Node-Unterschlüssel überprüfen, es sei denn, Sie verwenden regedit, um die Version des installierten x86-Pakets auf einer x64-Plattform anzuzeigen.) Die Versionsnummer wird in der REG_SZ-Zeichen folgen Wert **Version** und auch im Satz der REG_DWORD Werte " **Major**", " **Minor**", " **bld**" und " **rbld** " gespeichert. Sie können einen Fehler zur Installationszeit vermeiden, indem Sie die Installation des Redistributable Packages überspringen, wenn die derzeit installierte Version aktueller ist.

Wenn Sie ein Mergemodul verwenden, das eine Visual C++-DLL enthält, müssen Sie es in das Windows Installer-Paket einschließen (oder in ein ähnliches Installationspaket), mit dem Sie die Anwendung bereitstellen. Weitere Informationen finden Sie unter [Redistributing By Using Merge Modules (Verteilen von Komponenten mithilfe von Mergemodulen)](redistributing-components-by-using-merge-modules.md). Ein Beispiel finden Sie unter [Exemplarische Vorgehensweise: Bereitstellen einer Visual C++-Anwendung mithilfe eines Setup-Projekts](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md). Dort wird außerdem gezeigt, wie Sie InstallShield Limited Edition verwenden, um ein Installationspaket zu erstellen.

## <a name="potential-run-time-errors"></a>Potenzielle Laufzeitfehler

Wenn Windows keine der für Ihre Anwendung erforderlichen DLLs der verteilbaren Bibliotheken finden kann, wird eine Meldung angezeigt, die folgender ähnelt: „This application has failed to start because *library*.dll was not found. Re-installing the application may fix this problem.“ (Diese Anwendung konnte nicht gestartet werden, da „library.dll“ nicht gefunden wurde. Eine Neuinstallation der Anwendung könnte das Problem beheben.)

Stellen Sie sicher, dass der Installer die Anwendung richtig erstellt und dass die verteilbaren Bibliotheken ordnungsgemäß im Zielsystem bereitgestellt wurden, um diese Art von Fehler zu beheben. Weitere Informationen finden Sie unter [Grundlegendes zu den Abhängigkeiten einer Visual C++-Anwendung](understanding-the-dependencies-of-a-visual-cpp-application.md).

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Redistributing By Using Merge Modules (Verteilen mithilfe von Mergemodulen)](redistributing-components-by-using-merge-modules.md)|Beschreibt die Verwendung von verteilbaren Visual C++-Mergemodulen zur Installation der Visual C++-Laufzeitbibliotheken als freigegebene DLLs im Ordner „%windir%\system32\“.|
|[Neuverteilen von Visual C++ ActiveX-Steuerelementen](redistributing-visual-cpp-activex-controls.md)|Beschreibt, wie eine Anwendung, die ActiveX-Steuerelemente verwendet, verteilt wird.|
|[Neuverteilen der MFC-Bibliothek](redistributing-the-mfc-library.md)|Beschreibt, wie eine Anwendung, die MFC verwendet, verteilt wird.|
|[Neuverteilen von ATL-Anwendungen](redistributing-an-atl-application.md)|Beschreibt, wie eine Anwendung, die ATL verwendet, neu verteilt wird. Ab Visual Studio 2012 ist keine verteilbare Bibliothek für ATL erforderlich.|
|[Bereitstellungsbeispiele](deployment-examples.md)|Links zu Beispielen, die veranschaulichen, wie Visual C++-Anwendungen bereitgestellt werden.|
|[Deploying Desktop Applications (Bereitstellen von Desktopanwendungen)](deploying-native-desktop-applications-visual-cpp.md)|Bietet eine Einführung in Visual C++-Bereitstellungskonzepte und -technologien.|
