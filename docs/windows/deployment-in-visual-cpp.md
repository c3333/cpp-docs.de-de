---
title: Bereitstellung in Visual C++
ms.date: 05/11/2018
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
ms.assetid: d4b4ffc0-d2bd-4e4a-84a6-62f1c26f6a09
ms.openlocfilehash: 5c4b75a65fcfb34a4988b176ffcb5b2afcb7ea13
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377380"
---
# <a name="deployment-in-visual-c"></a>Bereitstellung in Visual C++

Die Installation einer Anwendung auf einem anderen Computer als Ihrem Entwicklungscomputer wird als *Bereitstellung* bezeichnet. Wenn eine Visual C++-Anwendung auf einem anderen Computer bereitgestellt werden soll, müssen sowohl die Anwendung selbst sowie alle Bibliotheksdateien installiert werden, von denen sie abhängt. Visual Studio bietet drei Möglichkeiten, die Visual C++-Bibliotheken zusammen mit Ihrer Anwendung bereitzustellen: die *zentrale Bereitstellung*, die *lokale Bereitstellung* und die *statische Verknüpfung*. Bei der zentralen Bereitstellung werden die Bibliotheksdateien im Windows-Verzeichnis gespeichert. Dort kann der Windows Update-Dienst diese automatisch aktualisieren. Bei der lokalen Bereitstellung werden die Bibliotheksdateien im selben Verzeichnis wie die Anwendung gespeichert. Sie müssen alle lokal bereitgestellten Bibliotheken manuell erneut bereitstellen, um diese zu aktualisieren. Bei der statischen Verknüpfung wird der Bibliothekscode an Ihre Anwendung gebunden. Bei der statischen Verknüpfung müssen Sie Ihre Anwendung erneut kompilieren und bereitstellen, um Updates an der Bibliothek zu nutzen.

In Visual Studio 2015 wurde die Microsoft C-Laufzeitbibliothekibliothek in versionsspezifische lokale Bibliothekskomponenten umgestaltet. Außerdem gibt es eine neue universelle C-Laufzeitbibliothek, die jetzt in Windows enthalten ist. Weitere Informationen zur Bereitstellung der universellen CRT finden Sie unter [Universal CRT deployment (Bereitstellung der universellen CRT)](universal-crt-deployment.md).

## <a name="central-deployment"></a>Zentrale Bereitstellung

Bei der zentralen Bereitstellung werden DLL-Bibliotheksdateien im Verzeichnis „Windows\System32“ installiert. Auf x64-Systemen werden 32-Bit-Bibliotheksdateien im Verzeichnis „Windows\SysWow64“ installiert. Microsoft aktualisiert die zentral bereitgestellten Bibliotheken automatisch. Für Visual C++-Bibliotheken, die lokal bereitgestellt oder statisch verknüpft sind, müssen Sie die Updates bereitstellen.

Wenn Sie Visual C++-Bibliotheken zentral bereitstellen möchten, können Sie eine dieser beiden Quellen verwenden, um die Dateien zu installieren:

- Dateien für *verteilbare Pakete*, die eigenständige ausführbare Befehlszeilendateien sind und alle verteilbaren Visual C++ Bibliotheken enthalten, oder

- *Verteilbare Mergemodule* (.msm-Dateien), die Sie zum Bereitstellen bestimmter Bibliotheken verwenden können und die Sie in die Windows Installer-Datei (.msi) Ihrer Anwendung aufnehmen.

Eine verteilbare Paketdatei installiert alle Visual C++-Bibliotheken für eine bestimmte Systemarchitektur. Wenn Ihre Anwendung beispielsweise für x64 erstellt wurde, können Sie das verteilbare Paket „vcredist_x64.exe“ verwenden, um alle Visual C++-Bibliotheken zu installieren, die Ihre Anwendung verwendet. Sie können den Installer Ihrer Anwendung so programmieren, dass verteilbare Pakete ausgeführt werden, bevor Sie die Anwendung installieren.

Ein Mergemodul aktiviert die Einbeziehung einer Setuplogik für eine bestimmte Visual C++-Bibliothek in einer Anwendungssetupdatei von Windows Installer. Sie können so viele Mergemodule einschließen, wie Sie für die Anwendung benötigen. Verwenden Sie Mergemodule, wenn Sie die Größe der Binärdateien für Ihre Bereitstellung minimieren müssen.

Da Windows Update bei der zentralen Bereitstellung mithilfe von verteilbaren Paketen oder Mergemodulen die Visual C++-Bibliotheken automatisch aktualisieren kann, wird empfohlen, die Bibliotheks-DLLs anstelle der statischen Bibliotheken in Ihrer Anwendung zu verwenden. Verwenden Sie deshalb die zentrale statt der lokalen Bereitstellung.

## <a name="local-deployment"></a>Lokale Bereitstellung

Bei der lokalen Bereitstellung werden Bibliotheksdateien im Anwendungsordner zusammen mit der ausführbaren Datei installiert. Verschiedene Versionen von verteilbaren Visual C++-Bibliotheken können im selben Ordner installiert werden, da der Dateiname jeder Version die Versionsnummer enthält. Version 12 der C++-Laufzeitbibliothek ist beispielsweise „msvcp120.dll“. Version 14 ist „msvcp140.dll“.

Eine Bibliothek kann über mehrere zusätzliche DLLs (sogenannte *dot-Bibliotheken*) verteilt werden. Beispielsweise wurden einige Funktionen der in Visual Studio 2017, Version 15.6 veröffentlichten Standardbibliothek zu „msvcp140_1.dll“ hinzugefügt, um die ABI-Kompatibilität von „msvcp140.dll“ beizubehalten. Wenn Sie Visual Studio 2017 Version 15.6 (Toolset 14.13) oder ein höheres Toolset von Visual Studio 2017 verwenden, müssen Sie diese dot-Bibliotheken und die Hauptbibliothek lokal bereitstellen. Die einzelnen dot-Bibliotheken werden dann in die nächste Hauptversion der Basisbibliothek eingefügt, wenn die ABI sich ändert.

Da Microsoft lokal bereitgestellte Visual C++-Bibliotheken nicht automatisch aktualisieren kann, wird die lokale Bereitstellung dieser Bibliotheken nicht empfohlen. Wenn Sie sich für die lokale Bereitstellung von weiter verteilbaren Bibliotheken entscheiden, wird empfohlen, dass Sie eine eigene Methode zur automatischen Aktualisierung von lokal bereitgestellten Bibliotheken implementieren.

## <a name="static-linking"></a>Statische Verknüpfung

Zusätzlich zu den dynamisch verknüpften Bibliotheken stellt Visual Studio die meisten Bibliotheken als statische Bibliotheken bereit. Sie können eine statische Bibliothek statisch mit Ihrer Anwendung verknüpfen. Das bedeutet, dass der Objektcode der Bibliothek direkt in der Anwendung verknüpft wird. Dadurch wird eine einzige Binärdatei ohne DLL-Abhängigkeiten erstellt, sodass Sie die Visual C++-Bibliotheksdateien nicht separat bereitstellen müssen. Dieser Ansatz wird jedoch nicht empfohlen, da statisch verknüpfte Bibliotheken nicht direkt aktualisiert werden können. Wenn Sie statische Verknüpfung verwenden und eine verknüpfte Bibliothek aktualisieren möchten, müssen Sie die Anwendung erneut kompilieren und erneut bereitstellen.

## <a name="troubleshooting-deployment-issues"></a>Beheben von Problemen bei der Bereitstellung

Die Ladereihenfolge von Visual C++-Bibliotheken hängt vom System ab. Verwenden Sie "depends.exe" oder "where.exe", um Ladeprogrammprobleme zu diagnostizieren. Weitere Informationen finden Sie unter [Dynamic-Link Library Search Order (Windows) (Dynamic Link Library-Suchreihenfolge (Windows))](/windows/win32/Dlls/dynamic-link-library-search-order).

## <a name="see-also"></a>Siehe auch

- [Deploying Desktop Applications (Bereitstellen von Desktopanwendungen)](deploying-native-desktop-applications-visual-cpp.md)
- [Bereitstellung der universellen CRT](universal-crt-deployment.md)
