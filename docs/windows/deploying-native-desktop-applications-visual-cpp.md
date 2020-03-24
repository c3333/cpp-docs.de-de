---
title: Bereitstellen von systemeigenen Desktopanwendungen (Visual C++)
ms.date: 05/11/2018
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
- Visual C++, application deployment
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- distributing applications [C++]
ms.assetid: 37f1691e-d67c-41e4-926e-528a237a9bac
ms.topic: overview
ms.openlocfilehash: e9ae5db05c0835bb65a65cdccf58ab7f7d1b789f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160189"
---
# <a name="deploying-native-desktop-applications-visual-c"></a>Bereitstellen von systemeigenen Desktopanwendungen (Visual C++)

Die Verteilung einer fertigen Anwendung oder Komponente zur Installation auf anderen Computern wird als Bereitstellung bezeichnet. Die Bereitstellungsplanung beginnt, wenn eine Anwendung auf dem Computer eines Entwicklers erstellt wird. Die Bereitstellung endet, wenn die Anwendung installiert wurde und auf dem Computer eines Benutzers ausgeführt werden kann.

Visual Studio bietet verschiedene Technologien für die Bereitstellung von Windows-Anwendungen. Dazu zählen die Bereitstellung mit ClickOnce und dem Windows Installer.

- ClickOnce kann zum Bereitstellen von C++-Anwendungen für die Common Language Runtime (CLR) verwendet werden (gemischte, reine und überprüfbare Assemblys). Obwohl Sie mit Windows Installer eine verwaltete Anwendung bereitstellen können, wird empfohlen, dass Sie ClickOnce verwenden, da es .NET Framework-Sicherheitsfeatures wie das Signieren von Manifesten verwendet. ClickOnce unterstützt die Bereitstellung von nativen C++-Anwendungen nicht. Weitere Informationen finden Sie unter [ClickOnce Deployment for Visual C++ Applications](clickonce-deployment-for-visual-cpp-applications.md).

- Mithilfe der Windows Installer-Technologie können systemeigene C++-Anwendungen oder C++-Anwendungen bereitgestellt werden, die auf die Common Language Runtime (CLR) ausgerichtet sind.

In den Artikeln dieses Abschnitts der Dokumentation wird erläutert, wie sichergestellt werden kann, dass eine systemeigene Visual C++-Anwendung auf jedem Computer ausgeführt werden kann, der eine unterstützte Zielplattform bietet. Zudem werden die in ein Installationspaket einzubeziehenden Dateien und die empfohlenen Methoden zum Verteilen von Komponenten beschrieben, von denen die Anwendung abhängt.

## <a name="in-this-section"></a>In diesem Abschnitt

- [Bereitstellung in Visual C++](deployment-in-visual-cpp.md)

- [Bereitstellungskonzepte](deployment-concepts.md)

- [Grundlegendes zu den Abhängigkeiten einer Visual C++-Anwendung](understanding-the-dependencies-of-a-visual-cpp-application.md)

- [Ermitteln der neu zu verteilenden DLLs](determining-which-dlls-to-redistribute.md)

- [Auswählen einer Bereitstellungsmethode](choosing-a-deployment-method.md)

- [Universal CRT deployment (Universelle CRT-Bereitstellung)](universal-crt-deployment.md)

- [Verteilen von Visual C++-Dateien](redistributing-visual-cpp-files.md)

- [Bereitstellungsbeispiele](deployment-examples.md)

- [Neuverteilen von Webclientanwendungen](redistributing-web-client-applications.md)

- [ClickOnce Deployment for Visual C++ Applications](clickonce-deployment-for-visual-cpp-applications.md)

- [Running a C++ /clr Application on a Previous Runtime Version (Ausführen einer C++- oder CLR-Anwendung auf einer früheren Laufzeitversion)](running-a-cpp-clr-application-on-a-previous-runtime-version.md)

## <a name="related-sections"></a>Verwandte Abschnitte

- [Erstellen von isolierten Anwendungen und parallelen Assemblys (C/C++)](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

- [Bereitstellung](/dotnet/framework/deployment/index)

- [Problembehandlung bei isolierten Anwendungen und parallelen Assemblys (C/C++)](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
