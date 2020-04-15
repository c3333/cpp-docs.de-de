---
title: Neuverteilen von Visual C++ ActiveX-Steuerelementen
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], redistributing
- controls [C++], distributing
ms.assetid: eefbb7e4-d28c-4c35-98bf-d9540cfaae83
ms.openlocfilehash: 4c7806502024789ed41f3043d7db6c87c7c71ee3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359883"
---
# <a name="redistributing-visual-c-activex-controls"></a>Neuverteilen von Visual C++ ActiveX-Steuerelementen

Visual C++ 6.0 stellt ActiveX-Steuerelemente bereit, die Sie in Anwendungen verwenden können, die Sie dann verteilen. Diese Steuerelemente sind nicht mehr in Visual C++ enthalten. Aufgrund der Lizenzvereinbarungen für Visual C++ 6.0 können Sie diese Steuerelemente mit Anwendungen verteilen, die in Visual C++ entwickelt wurden.

> [!NOTE]
> Visual C++ 6.0 wird jedoch nicht mehr von Microsoft unterstützt.

Eine Liste der verteilbaren Visual C++ 6.0 ActiveX-Steuerelemente finden Sie unter Common\Redist\Redist.txt auf Disk 1 der Visual C++ 6.0-Produkt-CD.

Wenn Sie Anwendungen verteilen, müssen Sie die OCX-Datei für das ActiveX-Steuerelement mithilfe von „Regsvr32.exe“ installieren und registrieren. Darüber hinaus sollten Sie sicherstellen, dass der Zielcomputer über die aktuellen Versionen der folgenden Systemdateien verfügt (die Sternchen geben Dateien an, die registriert werden müssen):

- Asycfilt.dll

- Comcat.dll \*

- Oleaut32.dll \*

- Olepro32.dll \*

- Stdole2.tlb

Wenn diese DLLs nicht auf dem Zielsystem verfügbar sind, müssen Sie sie mithilfe des vorgeschriebenen Mechanismus zum Aktualisieren des entsprechenden Betriebssystems aktualisieren. Sie können die neuesten Service Packs [http://windowsupdate.microsoft.com](https://windowsupdate.microsoft.com)für Windows-Betriebssysteme von herunterladen.

Wenn Sie ein ActiveX-Steuerelement verwenden, das eine Verbindung zu einer Datenbank herstellt, müssen Sie auch den Namen der Datenquelle auf dem Zielcomputer replizieren. Diesen Vorgang können Sie mit Funktionen wie `ConfigDSN` programmgesteuert durchführen.

Einige verteilbare ActiveX-Steuerelemente verfügen über zusätzliche Abhängigkeiten. Für jede OCX-Datei im Ordner „Os\System“ auf der Visual C++ 6.0-Produkt-CD gibt es auch eine DEP-Datei. Sehen Sie sich für jede OCX-Datei, die Sie verteilen möchten, mindestens einen der Einträge zur Verwendung in den entsprechenden DEP-Dateien an. Wenn eine Datei aufgeführt wird, müssen Sie sicherstellen, dass die Datei sich auch auf dem Zielcomputer befindet. Alle DLLs, die eine OCX-Datei direkt unterstützen, müssen registriert werden. (Damit Regsvr32.exe erfolgreich ist, muss der Zielcomputer zunächst alle DLLs enthalten, die das Steuerelement statisch lädt.) Wenn eine DLL, die als Abhängigkeit aufgeführt ist, auch eine .dep-Datei im Ordner Os-System auf der Visual C++ 6.0-CD enthält, müssen Sie auch diese .dep-Datei für USES-Einträge untersuchen.

## <a name="see-also"></a>Siehe auch

[Verteilen von Visual C++-Dateien](redistributing-visual-cpp-files.md)
