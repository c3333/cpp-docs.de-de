---
title: Verteilen von Visual C++-Dateien
description: Visual Studio enthält verteilbare Bibliotheken und Komponenten, die Sie mit Ihrer APP bereitstellen können.
ms.date: 07/16/2020
helpviewer_keywords:
- application deployment [C++], file redistributing
- redistributing applications [C++]
- deploying applications [C++], file redistributing
- file redistribution [C++]
- redistributing applications [C++], about redistributing applications
ms.assetid: d201b2ce-36f1-44e5-a96c-0db81a1ba652
ms.openlocfilehash: 7a639f7ad7deb76cade47b0162012dcb70cb0d69
ms.sourcegitcommit: e15b46ea7888dbdd7e0bb47da76aeed680c3c1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2020
ms.locfileid: "86446752"
---
# <a name="redistributing-visual-c-files"></a>Verteilen von Visual C++-Dateien

> [!NOTE]
> Sind Sie hier, weil Sie einen Download einer der Visual C++ Laufzeitdateien suchen? Wechseln Sie zur [Microsoft-Website](https://www.microsoft.com/) , und geben Sie **Visual C++ verteilbaren** Wert in das Suchfeld ein. Laden Sie das verteilbare Paket für die Architektur Ihres Computers (z.B. x64, wenn Sie 64-Bit-Windows ausführen) und die erforderliche Version von Visual C++ (z.B. 2015) herunter, und installieren Sie diese.

## <a name="redistributable-files-and-licensing"></a>Verteilbare Dateien und Lizenzierung

Wenn Sie eine Anwendung bereitstellen, müssen Sie auch die Dateien bereitstellen, die zu ihrer Unterstützung erforderlich sind. Wenn eine dieser Dateien von Microsoft bereitgestellt wird, überprüfen Sie, ob Sie diese Dateien weiterverteilen dürfen. Sie finden einen Link zu den Visual Studio-Lizenzbedingungen in der IDE. Verwenden Sie den Link Lizenzbedingungen im Dialogfeld Info Microsoft Visual Studio. Alternativ können Sie die relevanten EULAs und Lizenzen aus dem Visual Studio- [Lizenz Verzeichnis](https://visualstudio.microsoft.com/license-terms/)herunterladen.

::: moniker range="vs-2019"

Informationen zum Anzeigen der "Redist-Liste", auf die im Abschnitt "verteilbarer Code" der Microsoft-Software-Lizenzbedingungen für Visual Studio 2019 verwiesen wird, finden Sie unter [verteilbare Code Dateien für Microsoft Visual Studio 2019](/visualstudio/releases/2019/redistribution#-distributable-code-files-for-visual-studio-2019)

::: moniker-end

::: moniker range="vs-2017"

Informationen zum Anzeigen der "Redist-Liste", auf die im Abschnitt "verteilbarer Code" der Microsoft-Software-Lizenzbedingungen für Visual Studio 2017 verwiesen wird, finden Sie unter [verteilbare Code Dateien für Microsoft Visual Studio 2017](/visualstudio/productinfo/2017-redistribution-vs#-distributable-code-files-for-visual-studio-2017).

::: moniker-end

::: moniker range="vs-2015"

Informationen zum Anzeigen der "Redist-Liste", auf die im Abschnitt "verteilbarer Code" der Microsoft-Software-Lizenzbedingungen für Visual Studio 2015 verwiesen wird, finden Sie unter [verteilbare Code Dateien für Microsoft Visual Studio 2015](/visualstudio/productinfo/2015-redistribution-vs#-distributable-code-files-for-visual-studio-2015).

::: moniker-end

Weitere Informationen zu verteilbaren Dateien finden [Sie unter Bestimmen der weitervertreibenden DLLs](determining-which-dlls-to-redistribute.md) und [Bereitstellungs Beispiele](deployment-examples.md).

## <a name="locate-the-redistributable-files"></a>Suchen der weitervertreibbaren Dateien

Zum Bereitstellen von verteilbaren Dateien können Sie die verteilbaren Pakete verwenden, die von Visual Studio installiert werden. In Versionen von Visual Studio seit 2017 heißen diese Dateien *`vc_redist.arm64.exe`* , *`vc_redist.x64.exe`* und *`vc_redist.x86.exe`* . In Visual Studio 2015, Visual Studio 2017 und Visual Studio 2019 sind Sie auch unter den Namen, *`vcredist_x86.exe`* *`vcredist_x64.exe`* und *`vcredist_arm.exe`* (nur 2015) verfügbar.

Die einfachste Möglichkeit zum Auffinden der weitervertreibbaren Dateien ist die Verwendung von Umgebungsvariablen, die in einer Developer-Eingabeaufforderung festgelegt sind. In der neuesten Version von Visual Studio 2019 finden Sie die verteilbaren Dateien im *`%VCINSTALLDIR%Redist\MSVC\v142`* Ordner. Sowohl in Visual Studio 2017 als auch in Visual Studio 2019 sind Sie auch in enthalten *`%VCToolsRedistDir%`* . In Visual Studio 2015 finden Sie diese Dateien in *`%VCINSTALLDIR%redist\<locale>`* , wobei das Gebiets Schema *`<locale>`* der verteilbaren Pakete ist.

Eine andere Bereitstellungs Option ist die Verwendung von verteilbaren Mergemodulen ( *`.msm`* Dateien). In Visual Studio 2019 sind diese Dateien Teil einer optionalen installierbaren Komponente mit dem Namen **C++ 2019 Redistributable MSMs** in der Visual Studio-Installer. Die Mergemodule werden standardmäßig als Teil einer C++-Installation in Visual Studio 2017 und Visual Studio 2015 installiert. Wenn Sie in der neuesten Version von Visual Studio 2019 installiert sind, finden Sie die verteilbaren Mergemodule in *`%VCINSTALLDIR%Redist\MSVC\v142\MergeModules`* . Sowohl in Visual Studio 2019 als auch in Visual Studio 2017 sind Sie auch in enthalten *`%VCToolsRedistDir%MergeModules`* . In Visual Studio 2015 befinden Sie sich in *`Program Files [(x86)]\Common Files\Merge Modules`* .

## <a name="install-the-redistributable-packages"></a>Installieren der verteilbaren Pakete

Die weiterverteilbaren Visual C++-Pakete installieren und registrieren alle Visual C++-Bibliotheken. Wenn Sie eines verwenden, führen Sie es als erforderliche Komponente auf dem Zielsystem aus, bevor Sie die Anwendung installieren. Es wird empfohlen, dass Sie diese Pakete für die Bereitstellungen verwenden, da Sie die automatische Aktualisierung von Visual C++-Bibliotheken ermöglichen. Ein Beispiel zur Verwendung dieser Pakete finden Sie unter [Exemplarische Vorgehensweise: Bereitstellen einer Visual C++-Anwendung mithilfe von Visual C++ Redistributable Package](deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).

Jedes Visual C++ Redistributable Package überprüft das Vorhandensein einer aktuelleren Version auf dem Computer. Wenn eine neuere Version gefunden wird, wird das Paket nicht installiert. Ab Visual Studio 2015 zeigen verteilbare Pakete eine Fehlermeldung an, die darauf hinweist, dass ein Fehler beim Setup aufgetreten ist. Wenn ein Paket mit dem-Flag ausgeführt wird **`/quiet`** , wird keine Fehlermeldung angezeigt. In beiden Fällen wird ein Fehler im Microsoft Installer protokolliert und ein Fehlerergebnis wird an den Aufrufenden zurückgegeben. Mit Paketen ab Visual Studio 2015 können Sie diesen Fehler vermeiden, indem Sie die Registrierung überprüfen, um herauszufinden, ob eine neuere Version installiert ist. Die aktuelle installierte Versionsnummer wird im Schlüssel gespeichert `HKEY_LOCAL_MACHINE\SOFTWARE[\Wow6432Node]\Microsoft\VisualStudio\14.0\VC\Runtimes\{x86|x64|ARM}` . Die Versionsnummer ist 14,0 für Visual Studio 2015, Visual Studio 2017 und Visual Studio 2019, da die neueste verteilbare Binärdatei mit der 2015-Version binär kompatibel ist. Der Schlüssel ist `ARM` , `x86` oder, `x64` abhängig von den installierten Vcredist-Versionen für die Plattform. (Sie müssen nur unter dem `Wow6432Node` Unterschlüssel suchen, wenn Sie regedit verwenden, um die Version des installierten x86-Pakets auf einer x64-Plattform anzuzeigen.) Die Versionsnummer wird im REG_SZ Zeichen folgen Wert **`Version`** und auch in der Menge der **`Major`** Werte, **`Minor`** , **`Bld`** und gespeichert **`Rbld`** `REG_DWORD` . Sie können einen Fehler zur Installationszeit vermeiden, indem Sie die Installation des Redistributable Packages überspringen, wenn die derzeit installierte Version aktueller ist.

## <a name="install-the-redistributable-merge-modules"></a>Installieren der verteilbaren Mergemodule

Verteilbare Mergemodule müssen in das Windows Installer Paket (oder ein ähnliches Installationspaket) eingeschlossen werden, das Sie zum Bereitstellen der Anwendung verwenden. Weitere Informationen finden Sie unter [Redistributing By Using Merge Modules (Verteilen von Komponenten mithilfe von Mergemodulen)](redistributing-components-by-using-merge-modules.md). Ein Beispiel finden Sie unter Exemplarische Vorgehensweise: bereitstellen [einer Visual C++ Anwendung mithilfe eines Setup-Projekts](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

## <a name="install-individual-redistributable-files"></a>Einzelne verteilbare Dateien installieren

Es ist auch möglich, die verteilbaren DLLs direkt im *lokalen Anwendungsordner*zu installieren. Das ist der Ordner, der die ausführbare Anwendungsdatei enthält. Aus Wartungsgründen wird empfohlen, diesen Installationsort nicht zu verwenden.

## <a name="potential-run-time-errors"></a>Potenzielle Laufzeitfehler

Wenn Windows eine der für Ihre Anwendung erforderlichen weitervertreibbaren Bibliotheks-DLLs nicht finden kann, wird möglicherweise eine Meldung ähnlich der folgenden angezeigt: "diese Anwendung konnte nicht gestartet werden, da *Library*. dll nicht gefunden wurde. Das Problem kann möglicherweise durch eine Neuinstallation der Anwendung behoben werden. "

Um diese Art von Fehler zu beheben, stellen Sie sicher, dass der Anwendungsinstaller ordnungsgemäß erstellt wird. Überprüfen Sie, ob die verteilbaren Bibliotheken auf dem Zielsystem ordnungsgemäß bereitgestellt werden. Weitere Informationen finden Sie unter [Grundlegendes zu den Abhängigkeiten einer Visual C++-Anwendung](understanding-the-dependencies-of-a-visual-cpp-application.md).

## <a name="related-articles"></a>Verwandte Artikel

[Neuverteilen mithilfe von Mergemodulen](redistributing-components-by-using-merge-modules.md)\
Beschreibt, wie Visual C++ verteilbaren Mergemodule verwendet werden, um die Visual C++-Laufzeitbibliotheken als freigegebene DLLs im Ordner zu installieren *`%windir%\system32\`* .

[Neuverteilen Visual C++ ActiveX-Steuerelementen](redistributing-visual-cpp-activex-controls.md)\
Beschreibt, wie eine Anwendung, die ActiveX-Steuerelemente verwendet, verteilt wird.

[Neuverteilen der MFC-Bibliothek](redistributing-the-mfc-library.md)\
Beschreibt, wie eine Anwendung, die MFC verwendet, verteilt wird.

[Neuverteilen von ATL-Anwendungen](redistributing-an-atl-application.md)\
Beschreibt, wie eine Anwendung, die ATL verwendet, neu verteilt wird. Ab Visual Studio 2012 ist keine verteilbare Bibliothek für ATL erforderlich.

[Bereitstellungs Beispiele](deployment-examples.md)\
Links zu Beispielen, die veranschaulichen, wie Visual C++-Anwendungen bereitgestellt werden.

[Bereitstellen von Desktop Anwendungen](deploying-native-desktop-applications-visual-cpp.md)\
Bietet eine Einführung in Visual C++-Bereitstellungskonzepte und -technologien.
