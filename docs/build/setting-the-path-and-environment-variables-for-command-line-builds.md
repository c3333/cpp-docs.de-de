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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335582"
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>Festlegen der Pfad- und Umgebungsvariablen für Befehlszeilenbuilds

Die MSVC-Befehlszeilen-Buildtools (Microsoft C++) erfordern mehrere Umgebungsvariablen, die an Ihre Installation und Buildkonfiguration angepasst sind. Wenn eine C++-Arbeitsauslastung vom Visual Studio-Installer installiert wird, werden angepasste Befehlsdateien oder Batchdateien erstellt, die die erforderlichen Umgebungsvariablen festlegen. Der Installer verwendet diese Befehlsdateien dann, um Verknüpfungen für das Windows-Startmenü zum Öffnen eines Developer-Eingabeaufforderungsfenster zu erstellen. Diese Verknüpfungen richten die Umgebungsvariablen für eine bestimmte Buildkonfiguration ein. Wenn Sie die Befehlszeilentools verwenden möchten, können Sie eine dieser Verknüpfungen ausführen oder ein einfaches Eingabeaufforderungsfenster öffnen und dann eine der angepassten Befehlsdateien ausführen, um die Umgebung für die Buildkonfiguration selbst festzulegen. Weitere Informationen finden Sie unter [Verwenden des MSVC-Toolsets über die Befehlszeile](building-on-the-command-line.md). Informationen zum Verwenden der Befehlsdateien mit einer einfachen Eingabeaufforderung finden Sie im Abschnitt [Speicherorte der Developer-Befehlsdateien](building-on-the-command-line.md#developer_command_file_locations).

Die MSVC-Befehlszeilentools verwenden die Umgebungsvariablen PATH, TMP, INCLUDE, LIB und LIBPATH sowie andere für Ihre installierten Tools, Plattformen und SDKs spezifischen Umgebungsvariablen. Selbst bei einer einfachen Visual Studio-Installation werden möglicherweise 20 oder mehr Umgebungsvariablen festgelegt. Die Werte dieser Umgebungsvariablen sind spezifisch für Ihre Installation und die gewünschte Buildkonfiguration und können durch Produktupdates oder -upgrades geändert werden. Daher wird dringend empfohlen, dass Sie eine Verknüpfung der Developer-Eingabeaufforderung oder eine der angepassten Befehlsdateien verwenden, um diese festzulegen, anstatt sie in der Windows-Umgebung selbst festzulegen.

Sie können den SET-Befehl verwenden, um anzuzeigen, welche Umgebungsvariablen von einer Verknüpfung der Developer-Eingabeaufforderung festgelegt werden. Öffnen Sie ein einfaches Eingabeaufforderungsfenster, und erfassen Sie die Ausgabe des SET-Befehls für eine Baseline. Öffnen Sie ein Developer-Eingabeaufforderungsfenster, und erfassen Sie für den Vergleich die Ausgabe des SET-Befehls. Ein Diff-Tool wie das in der Visual Studio-IDE integrierte Tool kann beim Vergleich der Umgebungsvariablen und beim Anzeigen der von der Developer-Eingabeaufforderung festgelegten Werte hilfreich sein. Informationen zu den spezifischen vom Compiler und Linker verwendeten Umgebungsvariablen finden Sie unter [CL-Umgebungsvariablen](reference/cl-environment-variables.md).

> [!NOTE]
> Für mehrere Befehlszeilentools oder Tooloptionen sind möglicherweise Administratorberechtigungen erforderlich. Wenn bei der Verwendung dieser Tools solche Berechtigungsprobleme auftreten, empfiehlt es sich, das Developer-Eingabeaufforderungsfenster unter Verwendung der Option **Als Administrator ausführen** zu öffnen. Klicken Sie unter Windows 10 mit der rechten Maustaste, um das Kontextmenü für das Eingabeaufforderungsfenster zu öffnen, und klicken Sie dann auf **Mehr** und **Als Administrator ausführen**.

## <a name="see-also"></a>Siehe auch

[Verwenden des MSVC-Toolsets über die Befehlszeile](building-on-the-command-line.md)<br/>
[MSVC-Linkerreferenz](reference/linking.md)<br/>
[MSVC-Linkeroptionen](reference/linker-options.md)<br/>
[MSVC-Compilerreferenz](reference/compiling-a-c-cpp-program.md)<br/>
[MSVC-Compileroptionen](reference/compiler-options.md)
