---
title: Auswählen einer Bereitstellungsmethode
ms.date: 03/14/2019
helpviewer_keywords:
- redistributing DLLs
- manifests [C++]
- DLLs [C++], redistributing
- side-by-side assemblies [C++]
- dynamic linking [C++]
- application deployment [C++], methods
- deploying applications [C++], methods
- static linking [C++]
- libraries [C++], application deployment issues
ms.assetid: fd8eb956-f4a0-4ffb-b401-328c73e66986
ms.openlocfilehash: 633b76458fdc24ef9ba551d8209c5c99720df37e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377405"
---
# <a name="choosing-a-deployment-method"></a>Auswählen einer Bereitstellungsmethode

Wenn Ihre Visual C++-Anwendung in sich geschlossen ist und mithilfe eines Kopierbefehls bereitgestellt werden kann, wird empfohlen, dass Sie zur Bereitstellung Windows Installer verwenden. Windows Installer unterstützt die Installation, Reparatur und Deinstallation, und es unterstützt das atomische Aktualisieren von Anwendungsdateien, Abhängigkeiten und Registrierungseinträgen.

> [!NOTE]
> Obwohl die [ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)-Bereitstellung für native Visual C++-Anwendungen in Visual Studio möglich ist, sind dafür zusätzliche Schritte erforderlich. Weitere Informationen finden Sie unter [ClickOnce Deployment for Visual C++ Applications](clickonce-deployment-for-visual-cpp-applications.md).

## <a name="visual-c-libraries-are-shared-dlls"></a>Visual C++-Bibliotheken sind gemeinsam genutzte DLLs

Da Visual C++-Bibliotheken durch das Visual Studio-Installationsprogramm im Verzeichnis „%windir%\system32\“ installiert werden, wenn Sie eine Visual C++-Anwendung entwickeln, die von ihnen abhängen, wird sie wie erwartet ausgeführt. Um jedoch die Anwendung auf Computern bereitzustellen, die möglicherweise Visual Studio nicht haben, wird empfohlen, sich zu vergewissern, dass die Bibliotheken auf diesen Computer zusammen mit der Anwendung installiert werden.

## <a name="redistributing-visual-c-libraries"></a>Verteilen von Visual C++-Bibliotheken

In Ihren Bereitstellungen können Sie jede Version einer Visual C++-Bibliothek weiter verteilen, die für die Weiterverteilung lizenziert ist. Hierfür gibt es drei Möglichkeiten, sie bereitzustellen:

- Zentrale Bereitstellung mithilfe von verteilbaren Paketen, wobei Visual C++-Bibliotheken als freigegebene DLLs in %windir%\system32\\ installiert werden. (Für die Installation in diesem Ordner sind Administratorrechte erforderlich.) Sie können ein Skript oder Setupprogramm erstellen, das das verteilbare Paket ausführt, bevor Sie die Anwendung auf dem Zielcomputer installieren. Verteilbare Pakete sind für die Plattformen x86, x64 und ARM (VCRedist_x86.exe, VCRedist_x64.exe oder VCRedist_arm.exe) verfügbar. Visual Studio umfasst diese Pakete in %Programme (x86)%\Microsoft Visual Studio `version`\VC\Redist\\`locale ID`\\. Sie können sie auch vom [Microsoft Download Center](https://www.microsoft.com/download) herunterladen. (Verwenden Sie das Suchfeld im Download Center, um nach dem „Visual C++ Redistributable Package *Visual Studio-Version und Update*“ zu suchen, das mit Ihrer Anwendung übereinstimmt. Wenn Sie beispielsweise Visual Studio 2015 update 3 zum Erstellen Ihrer Anwendung verwendet haben, suchen Sie nach "Visual C++ Redistributable Package 2015 update 3".) Informationen zur Verwendung eines verteilbaren Pakets finden Sie unter [Exemplarische Vorgehensweise: Bereitstellen einer Visual C++-Anwendung mithilfe des Visual C++ Redistributable Package](deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).

- Zentrale Bereitstellung mithilfe von Mergemodulen, von denen jedes eine bestimmte Visual C++-Bibliothek als eine freigegebene DLL in %windir%\system32\\ installiert. (Für die Installation in diesen Ordner sind Administratorrechte erforderlich.) Mergemodule werden Teil der MSI-Installationsdatei für Ihre Anwendung. Verteilbare Visual C++-Mergemodule sind in Visual Studio unter \Program Files (x86)\Common Files\Merge Modules\\ enthalten. Weitere Informationen finden Sie unter [Redistributing By Using Merge Modules (Verteilen von Komponenten mithilfe von Mergemodulen)](redistributing-components-by-using-merge-modules.md).

- Eine lokale Bereitstellung, bei der Sie bestimmte Visual C++-DLLs aus Ihrer Visual Studio-Installation kopieren, die sich normalerweise unter \Programme (x86)\Microsoft Visual Studio `version`\VC\Redist\\`platform`\\`library`\ befindet, und diese auf Zielcomputer im selben Ordner wie die ausführbaren Anwendungsdateien installieren. Sie können mithilfe dieser Bereitstellungsmethode die Installation durch Benutzer ermöglichen, die über keine Administratorrechte verfügen oder für Anwendungen, die von einer Netzwerkfreigabe aus ausgeführt werden können.

Wenn eine Bereitstellung verteilbare Mergemodule verwendet und eine Installation von einem Benutzer ausgeführt wird, der nicht über Administratorrechte verfügt, werden die Visual C++-DLLs nicht installiert, und die Anwendung wird nicht ausgeführt. Zudem installieren Anwendungsinstallationsprogramm, die mit Mergemodulen erstellt wurden, die die Installation pro Benutzer ermöglichen, die Bibliotheken an einem freigegebenen Speicherort, was sich auf alle Benutzer des Systems auswirkt. Sie können mithilfe einer lokalen Bereitstellung die erforderlichen Visual C++-DLLs im Verzeichnis einer Anwendung eines bestimmten Benutzers installieren, ohne dass sich dies auf andere Benutzer auswirkt oder Administratorrechte erforderlich sind. Weil dies zu Problemen bei der Wartbarkeit führen kann, wird die lokale Bereitstellung von verteilbaren Visual C++-DLLs nicht empfohlen.

Die falsche Bereitstellung von Visual C++-Bibliotheken kann Laufzeitfehler während der Ausführung einer Anwendung, die diese Bibliotheken benötigt, verursachen. Wenn das Betriebssystem die Anwendung lädt, verwendet es die in [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)beschriebene Suchreihenfolge.

## <a name="dynamic-linking-is-better-than-static-linking"></a>Dynamisches Verknüpfen ist besser als statisches Verknüpfen

Es wird empfohlen, statisches Verknüpfen zu vermeiden, wenn Sie Visual C++-Bibliotheken verteilen. Obwohl statisches Verknüpfen die Anwendungsleistung nie deutlich verbessert, wird dadurch fast immer die Wartung teurer. Denken Sie beispielsweise an eine Anwendung, die statisch mit einer Bibliothek verknüpft ist, die mit Sicherheitserweiterungen aktualisiert wurde – die Anwendung kann nicht davon profitieren, es sei denn, sie wird erneut kompiliert und erneut bereitgestellt. Statt dessen empfehlen wir, dass Sie Ihre Anwendungen dynamisch mit Bibliotheken verknüpfen, von denen Sie abhängen. Auf diese Weise können die Bibliotheken überall aktualisiert werden, wo sie bereitgestellt werden.

## <a name="see-also"></a>Siehe auch

[Deploying Desktop Applications (Bereitstellen von Desktopanwendungen)](deploying-native-desktop-applications-visual-cpp.md)<br>
[ClickOnce-Sicherheit und Bereitstellung](/visualstudio/deployment/clickonce-security-and-deployment)<br>
[Bereitstellungsbeispiele](deployment-examples.md)
