---
title: Festlegen der Pfad- und Umgebungsvariablen für Befehlszeilenbuilds
ms.custom: conceptual
ms.date: 07/24/2019
helpviewer_keywords:
- environment variables [C++]
- VCVARS32.bat file
- cl.exe compiler [C++], environment variables
- LINK tool [C++], environment variables
- PATH reserved word
- INCLUDE reserved word
- LINK tool [C++], path
- LIB environment variable
- compiling source code [C++], from command line
- environment variables [C++], CL compiler
ms.assetid: 99389528-deb5-43b9-b99a-03c8773ebaf4
ms.openlocfilehash: aeafe806e5d29b89c243586974814aa7cfc16d1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335582"
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>Festlegen der Pfad- und Umgebungsvariablen für Befehlszeilenbuilds

Die Microsoft C++ (MSVC)-Befehlszeilenerstellungstools erfordern mehrere Umgebungsvariablen, die für Ihre Installations- und Buildkonfiguration angepasst sind. Wenn eine C++-Workload vom Visual Studio-Installationsprogramm installiert wird, werden benutzerdefinierte Befehlsdateien oder Batchdateien erstellt, die die erforderlichen Umgebungsvariablen festlegen. Das Installationsprogramm verwendet dann diese Befehlsdateien, um Verknüpfungen für das Windows-Startmenü zu erstellen, um ein Eingabeaufforderungsfenster für Entwickler zu öffnen. Diese Verknüpfungen richten die Umgebungsvariablen für eine bestimmte Buildkonfiguration ein. Wenn Sie die Befehlszeilentools verwenden möchten, können Sie eine dieser Verknüpfungen ausführen, oder Sie können ein einfaches Eingabeaufforderungsfenster öffnen und dann eine der benutzerdefinierten Befehlsdateien ausführen, um die Buildkonfigurationsumgebung selbst festzulegen. Weitere Informationen finden Sie unter [Verwenden des MSVC-Toolsets in der Befehlszeile](building-on-the-command-line.md). Informationen zur Verwendung der Befehlsdateien mit einer einfachen Eingabeaufforderung finden Sie im Abschnitt [Developer-Befehlsdateispeicherorte](building-on-the-command-line.md#developer_command_file_locations).

Die MSVC-Befehlszeilentools verwenden die Umgebungsvariablen PATH, TMP, INCLUDE, LIB und LIBPATH sowie andere Umgebungsvariablen, die für Ihre installierten Tools, Plattformen und SDKs spezifisch sind. Selbst eine einfache Visual Studio-Installation kann zwanzig oder mehr Umgebungsvariablen festlegen. Da die Werte dieser Umgebungsvariablen für Ihre Installation und die Wahl der Buildkonfiguration spezifisch sind und durch Produktupdates oder Upgrades geändert werden können, wird dringend empfohlen, dass Sie eine Eingabeaufforderungsverknüpfung für Entwickler oder eine der benutzerdefinierten Befehlsdateien verwenden, um sie festzulegen, anstatt sie selbst in der Windows-Umgebung festzulegen.

Um zu sehen, welche Umgebungsvariablen durch eine Eingabeaufforderungsverknüpfung für Entwickler festgelegt werden, können Sie den Befehl SET verwenden. Öffnen Sie ein einfaches Eingabeaufforderungsfenster, und erfassen Sie die Ausgabe des SET-Befehls für eine Baseline. Öffnen Sie ein Eingabeaufforderungsfenster für Entwickler, und erfassen Sie die Ausgabe des Befehls SET zum Vergleich. Ein Diff-Tool, wie das in der Visual Studio-IDE integrierte, kann nützlich sein, um die Umgebungsvariablen zu vergleichen und zu sehen, was von der Entwicklereingabeaufforderung festgelegt wird. Informationen zu den spezifischen Umgebungsvariablen, die vom Compiler und Linker verwendet werden, finden Sie unter [CL-Umgebungsvariablen](reference/cl-environment-variables.md).

> [!NOTE]
> Für mehrere Befehlszeilentools oder Werkzeugoptionen ist möglicherweise die Administratorberechtigung erforderlich. Wenn bei der Verwendung Berechtigungsprobleme auftreten, wird empfohlen, das Eingabeaufforderungsfenster für Entwickler mithilfe der Option **Als Administrator ausführen zu** öffnen. Klicken Sie unter Windows 10 mit der rechten Maustaste, um das Kontextmenü für das Eingabeaufforderungsfenster zu öffnen, und wählen Sie dann **Mehr**, **Ausführen als Administrator**aus.

## <a name="see-also"></a>Siehe auch

[Verwenden des MSVC-Toolsets über die Befehlszeile](building-on-the-command-line.md)<br/>
[MSVC-Linkerreferenz](reference/linking.md)<br/>
[MSVC-Linkeroptionen](reference/linker-options.md)<br/>
[MSVC-Compilerreferenz](reference/compiling-a-c-cpp-program.md)<br/>
[MSVC-Compileroptionen](reference/compiler-options.md)
