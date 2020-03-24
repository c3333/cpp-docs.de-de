---
title: Erstellen von isolierten Anwendungen und parallelen Assemblys (C/C++)
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
- WinSxS [C++]
- native assembly cache [C++]
- builds [C++], isolated applications
- side-by-side applications [C++]
- builds [C++], side-by-side assemblies
ms.assetid: 9465904e-76f7-48bd-bb3f-c55d8f1699b6
ms.openlocfilehash: db2978c054362b6c329fb786d0f7da322d4c9201
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169876"
---
# <a name="building-cc-isolated-applications-and-side-by-side-assemblies"></a>Erstellen von isolierten Anwendungen und parallelen Assemblys (C/C++)

Visual Studio unterstützt ein Bereitstellungs Modell für Windows-Client Anwendungen, das auf der Idee von [isolierten Anwendungen](/windows/win32/SbsCs/isolated-applications) [und parallelen](/windows/win32/SbsCs/about-side-by-side-assemblies-)Assemblys basiert. Standardmäßig erstellt Visual Studio alle nativen C/C++ Anwendungen als isolierte Anwendungen, die [Manifeste](/windows/win32/sbscs/manifests) verwenden, um ihre Abhängigkeiten C++ von visuellen Bibliotheken zu beschreiben.

Das Erstellen von C/C++-Programmen als isolierte Anwendungen bietet eine Reihe von Vorteilen. Eine isolierte Anwendung ist beispielsweise nicht betroffen, wenn andere C/C++-Anwendungen Visual C++-Bibliotheken installieren oder deinstallieren. Visual C++-Bibliotheken, die von isolierten Anwendungen verwendet werden, können trotzdem entweder in den lokalen Ordner der Anwendung oder durch Installation in den nativen Assemblycache (WinSxS) neu verteilt werden. Dennoch kann die Wartung von Visual C++-Bibliotheken für bereits bereitgestellte Anwendungen durch die Verwendung einer [Herausgeberkonfigurationsdatei](/windows/win32/SbsCs/publisher-configuration)vereinfacht werden. Mit dem isolierten Anwendungsbereitstellungsmodell können Sie einfacher sicherstellen, dass C/C++-Anwendungen, die auf einem bestimmten Computer ausgeführt werden, die neueste Version der Visual C++-Bibliotheken verwenden, aber gleichzeitig die Möglichkeit offenhalten, dass Systemadministratoren und Anwendungsentwickler die explizite Versionsbindung von Anwendungen an ihre abhängigen DLLs steuern können.

In diesem Abschnitt wird erläutert, wie Sie eine C/C++-Anwendung als isolierte Anwendung erstellen und sicherstellen können, dass sie über ein Manifest an Visual C++-Bibliotheken gebunden ist. Die Informationen in diesem Abschnitt gelten in erster Linie für Native oder nicht verwaltete C++ Anwendungen. Informationen zum Bereitstellen von C++ nativen Anwendungen, die mit Visual Studio erstellt wurden, finden Sie unter [Verteilen von visuellen C++ Dateien](../windows/redistributing-visual-cpp-files.md).

## <a name="in-this-section"></a>In diesem Abschnitt

[Konzept der isolierten Anwendungen und der parallelen Assemblys](concepts-of-isolated-applications-and-side-by-side-assemblies.md)

[Erstellen isolierter C/C++-Anwendungen](building-c-cpp-isolated-applications.md)

[Erstellen von parallelen C/C++-Assemblys](building-c-cpp-side-by-side-assemblies.md)

[Vorgehensweise: Erstellen von COM-Komponenten ohne Registrierung](how-to-build-registration-free-com-components.md)

[Vorgehensweise: Erstellen von isolierten Anwendungen zur Verwendung von COM-Komponenten](how-to-build-isolated-applications-to-consume-com-components.md)

[Manifestgenerierung für C/C++-Programme](understanding-manifest-generation-for-c-cpp-programs.md)

[Problembehandlung bei isolierten Anwendungen und parallelen Assemblys (C/C++)](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

## <a name="related-sections"></a>Verwandte Abschnitte

[Isolierte Anwendungen und parallele Assemblys](/windows/win32/SbsCs/isolated-applications-and-side-by-side-assemblies-portal)

[Deploying Desktop Applications (Bereitstellen von Desktopanwendungen)](../windows/deploying-native-desktop-applications-visual-cpp.md)
