---
title: Bereitstellung der universellen CRT
description: Erfahren Sie, wann und wo die universelle CRT-Bibliothek für Ihre APP bereitgestellt wird.
ms.date: 10/23/2020
helpviewer_keywords:
- deploying the CRT [C++]
- application CRT deployment [C++]
ms.openlocfilehash: 50ab23f3b0276b058685e9c9ef6634caf5a96186
ms.sourcegitcommit: bf54b407169900bb668c85a67b31dbc0f069fe65
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92497189"
---
# <a name="universal-crt-deployment"></a>Bereitstellung der universellen CRT

Von Visual Studio .NET bis Visual Studio 2013 enthielt jedes Hauptrelease der C++-Compiler und -Tools eine neue, eigenständige Version der Microsoft C-Laufzeitbibliothek (CRT). Diese eigenständigen Versionen der CRT waren unabhängig voneinander und teilweise nicht miteinander kompatibel. Die CRT-Bibliothek, die von Visual Studio 2012 verwendet wurde, war beispielsweise Version 11 (msvcr110.dll), und die CRT, die von Visual Studio 2013 verwendet wurde, war Version 12 (msvcr120.dll). Ab Visual Studio 2015 ist es nicht mehr der Fall. Visual Studio 2015 und höhere Versionen von Visual Studio verwenden die universelle CRT.

Die universelle CRT (ucrt) ist eine Komponente des Microsoft Windows-Betriebssystems. Er ist als Teil des Betriebssystems in Windows 10 und Windows Server 2016 oder höher enthalten. Die ucrt ist verfügbar, wenn Sie Windows Update auf älteren Betriebssystemen verwenden, die noch über erweiterte Unterstützung verfügen. Die lokale Bereitstellung der universellen CRT wird mit einigen Einschränkungen unterstützt.

## <a name="central-deployment"></a>Zentrale Bereitstellung

Die bevorzugte Methode zur zentralen Installation der universellen CRT ist die Verwendung von Microsoft Windows Update. Bei der universellen CRT handelt es sich um ein empfohlenes Update für alle unterstützten Microsoft Windows-Betriebssysteme. Deshalb wird sie auf den meisten Computern standardmäßig im Rahmen des regulären Updatevorgangs installiert. Die erste Version der Universal CRT war [KB2999226](https://support.microsoft.com/kb/2999226). Ein späteres Update mit verschiedenen Fehlerbehebungen wurde in [KB3118401](https://support.microsoft.com/kb/3118401)erstellt, und es wurden zusätzliche Updates mit weiteren Fehlerbehebungen und neuen Features erstellt. Weitere Informationen zu aktuelleren Updates finden Sie, wenn Sie [support.microsoft.com](https://support.microsoft.com) nach „Universal C Runtime“ oder „Universal CRT“ durchsuchen.

Nicht alle Microsoft Windows-Computer installieren regelmäßig Updates über Windows Update, und manche installieren möglicherweise nicht alle empfohlenen Updates. Um die Verwendung von Anwendungen zu unterstützen, die mit Visual Studio 2015 und neueren C++-Toolsets auf diesen Computern erstellt wurden, sind universelle CRT-weitervertreibbare Dateien für die Offline Verteilung verfügbar. Diese weitervertreibbaren Dateien können von einem der oben aufgeführten KB-Links heruntergeladen werden. Die universelle CRT-verteilbare Komponente erfordert, dass der Computer auf die aktuelle Service Pack aktualisiert wurde. Die verteilbare Komponente für Windows 7 kann also beispielsweise nur unter Windows 7 SP1, nicht unter Windows 7 RTM installiert werden.

Da die universelle CRT eine grundlegende Abhängigkeit von den C++-Bibliotheken ist, installiert die Visual C++ Redistributable (Vcredist) die anfängliche Version der universellen CRT (Version 10.0.10240) auf Computern, auf denen noch keine installiert ist. Diese Version reicht aus, um die Abhängigkeiten der C++-Bibliothek zu erfüllen. Wenn Ihre Anwendung von einer neueren Version der Universal CRT abhängt, müssen Sie Windows Update verwenden, um den Computer vollständig auf den neuesten Stand zu bringen, oder Sie müssen die Version explizit installieren. Es empfiehlt sich, die universelle C-Runtime über Windows Update oder eine MSU vor der Installation von Vcredist zu installieren, um potenzielle mehrere erforderliche Neustarts zu vermeiden.

Nicht alle Betriebssysteme sind über Windows Update für die aktuellste universelle C-Laufzeit qualifiziert. Unter Windows 10 entspricht die zentral bereitgestellte Version der Version des Betriebssystems. Um die universelle C-Laufzeit weiter zu aktualisieren, müssen Sie das Betriebssystem aktualisieren. Für Windows Vista bis Windows 8.1 basiert die neueste verfügbare universelle C-Laufzeit derzeit auf der Version, die im Windows 10 Anniversary Update enthalten ist, mit zusätzlichen Korrekturen (Version 10.0.14393).

## <a name="local-deployment"></a>Lokale Bereitstellung

Die lokale Bereitstellung der App der universellen CRT wird zwar unterstützt, aber aus Leistungs- und Sicherheitsgründen nicht empfohlen. Die DLLs für die lokale Bereitstellung sind im Windows SDK im Unterverzeichnis Windows Kits\\10\\Redist\\ucrt\\DLLs (je nach Computerarchitektur) enthalten. Die erforderlichen DLLs enthalten „ucrtbase.dll“ und mehrere APISet-Weiterleitungs-DLLs namens „api-ms-win-\*.dll“. Der für jedes Betriebssystem erforderliche DLLs-Satz variiert je nach Betriebssystem. Es wird dringend empfohlen, dass Sie alle DLLs einbeziehen, wenn Sie lokal bereitstellen.

Es gibt zwei Einschränkungen bei der lokalen Bereitstellung, die Sie berücksichtigen müssen:

- Unter Windows 10 wird immer die universelle CRT im Systemverzeichnis verwendet, auch wenn eine Anwendung eine anwendungsspezifische Kopie der universellen CRT enthält. Dies ist auch dann der Fall, wenn die lokale Kopie neuer ist, da die universelle CRT eine zentrale Betriebssystem Komponente unter Windows 10 ist.

- Bei Windows-Versionen vor Windows 8 kann die universelle CRT nicht lokal mit einem Plug-in verpackt werden, wenn Sie sich in einem anderen Verzeichnis als dem Verzeichnis der ausführbaren Datei der Haupt-App befindet. Die APISet-Weiterleitungs-DLLs können „ucrtbase.dll“ in diesem Fall nicht erfolgreich auflösen. Folgende alternative Lösungen werden empfohlen:

  - Verknüpfen Sie die universelle CRT statisch,
  - stellen Sie sie zentral bereit, oder
  - platzieren Sie die Dateien der universellen CRT im selben Verzeichnis wie die App.

## <a name="deployment-on-microsoft-windows-xp"></a>Bereitstellung unter Microsoft Windows XP

Visual Studio 2015 und Visual Studio 2017 unterstützen die Entwicklung von Software für Microsoft Windows XP weiterhin. Zur Unterstützung dieser Entwicklung funktioniert eine Version der universellen CRT unter Microsoft Windows XP. Das Betriebssystem Microsoft Windows XP wird nicht mehr grundlegend oder erweitert unterstützt, deshalb unterscheidet die zentrale Bereitstellung der universellen CRT unter Microsoft Windows XP sich von der unter anderen Betriebssystemen.

Wenn die Visual C++ Redistributable unter Windows XP installiert ist, installiert Sie die universelle CRT und alle zugehörigen Abhängigkeiten direkt im System Verzeichnis. Er wird nicht installiert oder ist nicht von Windows Update abhängig. Für die verteilbaren Mergemodule (die Microsoft_VC*version*_CRT_\*.msm-Dateien) gilt das gleiche.

Die lokale Bereitstellung der universellen CRT unter Windows XP unterscheidet sich nicht von der auf anderen unterstützten Betriebssystemen.

## <a name="see-also"></a>Weitere Informationen

- [Bereitstellung in Visual C++](deployment-in-visual-cpp.md)
