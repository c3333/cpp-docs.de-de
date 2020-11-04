---
title: Ermitteln der neu zu verteilenden DLLs
ms.date: 07/15/2019
helpviewer_keywords:
- redistributing DLLs
- DLLs [C++], redistributing
- dependencies [C++], application deployment and
- application deployment [C++], DLL redistribution
- deploying applications [C++], DLL redistribution
ms.assetid: f7a2cb42-fb48-42ab-abd2-b35e2fd5601a
ms.openlocfilehash: 079bfa33ced9f62d6abbccca86435b1b5654a2de
ms.sourcegitcommit: d77159732a8e782b2a1b7abea552065f2b6f61c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2020
ms.locfileid: "93344708"
---
# <a name="determining-which-dlls-to-redistribute"></a>Ermitteln der neu zu verteilenden DLLs

Beim Erstellen einer Anwendung, die von Visual Studio bereitgestellte Bibliotheks-DLLs verwendet, müssen Benutzer der Anwendung auch diese DLLs auf ihren Computern haben, damit die Anwendung ausgeführt werden kann. Da die meisten Benutzer wahrscheinlich nicht Visual Studio installiert haben, müssen Sie diese DLLs für sie bereitstellen. Visual Studio stellt diese DLLs als *verteilbare Dateien* zur Verfügung, die Sie in den Installer der Anwendung einschließen können.

Damit das Einfügen der verteilbaren DLLs mit dem Installer einfacher ist, sind diese als eigenständige *verteilbare Pakete* verfügbar. Dabei handelt es sich um architekturspezifische ausführbare Dateien, die die zentrale Bereitstellung verwenden, um die verteilbaren Dateien auf dem Computer eines Benutzers zu installieren. Vcredistx86.exe z. b. \_ die 32-Bit-Bibliotheken für x86-und x64-Computer installiert, Vcredist \_x64.exe die 64-Bit-Bibliotheken für x64-Computer installiert, und Vcredist \_ARM.exe installiert die Bibliotheken für Arm-Computer. Die zentrale Bereitstellung wird empfohlen, da Microsoft den Windows Update-Dienst verwenden kann, um diese Bibliotheken unabhängig zu aktualisieren. Zusätzlich zu der Kopie in Ihrer Visual Studio-Installation können die aktuellen verteilbaren Pakete heruntergeladen werden. Links zu den aktuellen unterstützten verteilbaren Paketen für aktuelle und ältere Toolsets finden Sie unter [The latest supported Visual C++ downloads (Aktuelle unterstützte Visual C++-Downloads)](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads). Bestimmte frühere Versionen von verteilbaren Paketen finden Sie, wenn Sie das [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=158431) nach „Visual C++ Redistributable Packages“ durchsuchen.

Die Hauptversionsnummer des verteilbaren Pakets, das Sie bereitstellen, muss der Version des Visual Studio-Toolsets entsprechen, das Sie für das Erstellen Ihrer Anwendung verwendet haben. Die Nebenversion muss identisch oder höher sein. Die Versionsnummern der Toolsets von Visual Studio 2017 und Visual Studio 2015 sind kompatibel. Das bedeutet, dass die verteilbaren Visual Studio 2017-Dateien von Apps verwendet werden können, die mit dem 2015-Toolset erstellt wurden. Die verteilbaren 2015-Dateien sind zwar kompatibel, es wird jedoch nicht unterstützt, diese in Apps zu verwenden, die mit dem 2017-Toolset erstellt wurden. Es werden nur verteilbare Pakete unterstützt, die aus Ihrer oder einer neueren Toolsetversion stammen.

Sie können verteilbare DLLs ebenfalls mit Ihrem Installer einfügen, indem Sie *Mergemodule* verwenden. Diese Microsoft Installer-Module sind im Installer Ihrer Anwendung enthalten und werden von diesem installiert. Mergemodule für die verteilbaren DLLs finden Sie in Ihrem Visual Studio-Installationsverzeichnis unter \\ VC \\ redist\msvc \\ *Version* \\ mergemodules \\ . In früheren Versionen von Visual Studio befinden diese Dateien sich im Verzeichnis \\Programme oder \\Programme (x86) im Unterverzeichnis Common Files\\Merge Modules. Weitere Informationen zur Verwendung dieser Dateien finden Sie unter [Redistributing Components by using Merge Modules (Verteilen von Komponenten mit Mergemodulen)](redistributing-components-by-using-merge-modules.md).

Die einzelnen verteilbaren DLLs sind ebenfalls in der Installation von Visual Studio enthalten. Diese werden standardmäßig im Visual Studio-Installationsverzeichnis im Ordner \\VC\\Redist\\MSVC\\*Version* installiert. Die *Versionsnummer* kann unterschiedliche Buildnummern einer allgemeinen Reihe von verteilbaren Dateien darstellen. Verwenden Sie die aktuelle Version von DLL-Bibliotheksdateien, verteilbaren Paketen und Mergemodulen in diesen Verzeichnissen. Sie können diese Bibliotheken für die lokale Bereitstellung verwenden, indem Sie diese im selben Verzeichnis wie Ihre Anwendung installieren. Die lokale Bereitstellung wird nicht empfohlen, da Sie bei dieser selbst dafür verantwortlich sind, Updates für die bereitgestellte Anwendung zu liefern. Bei der zentralen Bereitstellung mithilfe von verteilbaren Paketen handelt es sich um die bevorzugte Methode.

Um zu bestimmen, welche DLLs mit der Anwendung verteilt werden müssen, sammeln Sie eine Liste der DLLs, von denen die Anwendung abhängig ist. Diese werden üblicherweise als Importbibliothekseingaben für den Linker aufgeführt. Bestimmte Bibliotheken wie „vcruntime“ und die universelle C-Laufzeitbibliothek (UCRT) sind standardmäßig enthalten. Wenn Ihre App oder eine der Abhängigkeiten „LoadLibrary“ verwendet, um eine DLL dynamisch zu laden, wird diese nicht als Eingabe für den Linker aufgeführt. Eine Möglichkeit zum Erstellen der Liste der dynamisch geladenen DLLs besteht in der Ausführung von „Dependency Walker“ (depends.exe) für Ihre App. Dies wird unter [Understanding the Dependencies of a Visual C++ Application (Grundlegendes zu den Abhängigkeiten einer Visual C++-Anwendung)](understanding-the-dependencies-of-a-visual-cpp-application.md) beschrieben. Dieses Tool ist leider veraltet und gibt möglicherweise die Meldung aus, dass bestimmte DLLs nicht gefunden werden können.

Wenn die Liste der Abhängigkeiten vorliegt, vergleichen Sie sie mit der verknüpften Liste in einer Redist.txt-Datei im Microsoft Visual Studio-Installationsverzeichnis oder mit der REDIST-Liste verteilbarer DLLs, auf die im Abschnitt „Verteilbare Codedateien“ der Microsoft-Softwarelizenzbedingungen für Ihre Version von Visual Studio verwiesen wird. Für Visual Studio 2017 finden Sie weitere Informationen unter [Verteilbarer Code für Microsoft Visual Studio 2017 (einschließlich Hilfsprogramme, Erweiterbarkeit und BuildServer-Dateien)](/visualstudio/productinfo/2017-redistribution-vs). Für Visual Studio 2015 finden Sie weitere Informationen unter [Verteilbarer Code für Microsoft Visual Studio 2015 und Microsoft Visual Studio 2015 SDK (einschließlich Hilfsprogramme und BuildServer-Dateien)](/visualstudio/productinfo/2015-redistribution-vs). Für Visual Studio 2013 finden Sie die Liste online unter [Verteilbarer Code für Microsoft Visual Studio 2013 und Microsoft Visual Studio 2013 SDK](/visualstudio/productinfo/2013-redistribution-vs).

In Versionen vor Visual Studio 2015 war die C-Laufzeitbibliothek (CRT) als verteilbare DLL in „msvc *version*.dll“ enthalten. Ab Visual Studio 2015 wurden die Funktionen der CRT in „vcruntime“ und in die UCRT umgestaltet. Die UCRT ist nun eine Systemkomponente unter Windows 10 und wird von Windows Update verwaltet. Sie ist auf alle Windows 10-Betriebssystemen verfügbar. Wenn Sie Anwendungen für frühere Betriebssysteme bereitstellen möchten, müssen Sie die UCRT möglicherweise ebenfalls verteilen. Eine frühere Version der UCRT ist in den verteilbaren Visual Studio-Dateien enthalten, die nur auf Betriebssystemen vor Windows 10 installiert werden, wenn dort noch keine Version der UCRT installiert ist. Eine installierbare Version der UCRT für ältere Systeme finden Sie im Microsoft Download Center unter [Windows 10 Universal C Runtime (Windows 10: Universelle C-Runtime)](https://www.microsoft.com/download/details.aspx?id=48234) als Updatepaket für Microsoft-Systeme.

Sie können nicht alle Dateien weiterverteilen, die in Visual Studio enthalten sind. Sie sind nur zur Weiterverteilung der Dateien berechtigt, die in "Redist.txt" oder in der "REDIST-Liste" online angegeben sind. Debugversionen von Anwendungen und die verschiedenen Visual C++-Debug-DLLs sind nicht weiterverteilbar. Weitere Informationen finden Sie unter [Choosing a Deployment Method (Auswählen einer Bereitstellungsmethode)](choosing-a-deployment-method.md).

In der folgenden Tabelle werden einige der Visual C++-DLLs beschrieben, von denen Ihre Anwendung möglicherweise abhängig ist.

|Visual C++-Bibliothek|Beschreibung|Anwendungsbereich|
|--------------------------|-----------------|----------------|
|vcruntime *version*.dll|Laufzeitbibliothek für nativen Code.|Anwendungen, die die normalen C- und C++-Sprachdienste zum Starten und Beenden verwenden.|
|vccorlib *version*.dll|Laufzeitbibliothek für verwalteten Code.|Anwendungen, die die C++-Sprachdienste für verwalteten Code verwenden.|
|msvcp *version*.dll und msvcp *version* _ *dotnumber*.dll|C++-Standardbibliothek für nativen Code.|Anwendungen, die die [C++-Standardbibliothek](../standard-library/cpp-standard-library-reference.md) verwenden.|
|concrt *version*.dll|Concurrency Runtime-Bibliothek für nativen Code.|Anwendungen, die [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md) verwenden.|
|mfc *version*.dll|Microsoft Foundation Class-Bibliothek (MFC-Bibliothek).|Anwendungen, die die [MFC-Bibliothek](../mfc/mfc-desktop-applications.md) verwenden.|
|mfc *version* *language*.dll|Microsoft Foundation Classes-Bibliotheksressourcen (MFC).|Anwendungen, die bestimmte Sprachressourcen für MFC verwenden.|
|mfc *version* u.dll|MFC-Bibliothek mit Unicode-Unterstützung.|Anwendungen, die die [MFC-Bibliothek](../mfc/mfc-desktop-applications.md) verwenden und Unicode-Unterstützung erfordern.|
|mfcmifc80.dll|MFC-Bibliothek für verwaltete Schnittstellen.|Anwendungen, die die [MFC-Bibliothek](../mfc/mfc-desktop-applications.md) mit [Windows Forms-Steuerelementen](/dotnet/framework/winforms/controls/index) verwenden.|
|mfcm *version*.dll|Verwaltete MFC-Bibliothek.|Anwendungen, die die [MFC-Bibliothek](../mfc/mfc-desktop-applications.md) mit [Windows Forms-Steuerelementen](/dotnet/framework/winforms/controls/index) verwenden.|
|mfcm *version* u.dll|Verwaltete MFC-Bibliothek mit Unicode-Unterstützung.|Anwendungen, die die [MFC-Bibliothek](../mfc/mfc-desktop-applications.md) mit [Windows Forms-Steuerelementen](/dotnet/framework/winforms/controls/index) verwenden sowie Unicode-Unterstützung erfordern.|
|vcamp *version*.dll|AMP-Bibliothek für nativen Code.|Anwendungen, die den Code der [AMP-Bibliothek für C++](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md) verwenden.|
|vcomp *version*.dll|OpenMP-Bibliothek für nativen Code.|Anwendungen, die den Code der [OpenMP-Bibliothek für C++](../parallel/openmp/openmp-in-visual-cpp.md) verwenden.|

> [!NOTE]
> Sie müssen nicht mehr die Active Template Library als eine separate DLL weiterverteilen. Die Funktionalität wurde in Header und eine statische Bibliothek verschoben.

Weitere Informationen zur Verteilung dieser DLLs mit der Anwendung finden Sie unter [Verteilen von Visual C++-Dateien](redistributing-visual-cpp-files.md). Beispiele finden Sie unter [Bereitstellungsbeispiele](deployment-examples.md).

In der Regel müssen Sie keinen System-DLLs zu verteilen, da sie Teil des Betriebssystems sind. Allerdings gelten möglicherweise Ausnahmen, z. B., wenn die Anwendung auf mehreren Versionen von Microsoft-Betriebssystemen ausgeführt wird. In diesem Fall müssen Sie die entsprechenden Lizenzbedingungen lesen. Versuchen Sie außerdem, die System-DLLs entweder mittels Windows Update, Service Packs oder verteilbarer Pakete von Microsoft zu aktualisieren.

## <a name="see-also"></a>Weitere Informationen:

[Auswählen einer Bereitstellungsmethode](choosing-a-deployment-method.md)<br/>
[Deploying Desktop Applications (Bereitstellen von Desktopanwendungen)](deploying-native-desktop-applications-visual-cpp.md)
