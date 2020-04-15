---
title: BSCMAKE-Referenz
ms.date: 05/06/2019
helpviewer_keywords:
- BSCMAKE, reference
- Microsoft Browse Information Maintenance Utility
- browse windows
- browse information files (.bsc), building
- .bsc files, building
- bsc files, building
- BSCMAKE
ms.assetid: b97ad994-1355-4809-98db-6abc12c6fb13
ms.openlocfilehash: f95e34b9599de628463b9f92ebf8f01036237891
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320739"
---
# <a name="bscmake-reference"></a>BSCMAKE-Referenz

> [!WARNING]
> Obwohl BSCMAKE weiterhin mit Visual Studio installiert wird, wird es nicht mehr von der IDE verwendet. Seit Visual Studio 2008 werden Browse- und Symbolinformationen automatisch in einer SQL Server-.SDF-Datei im Projektmappenordner gespeichert.

Das Microsoft Browse Information Maintenance-Programm (BSCMAKE.EXE) erstellt eine neue Browseinformationsdatei (.bsc) aus SBR-Dateien, die während der Kompilierung erstellt wurden. Bestimmte Tools von Drittanbietern verwenden BSC-Dateien für die Codeanalyse.

Wenn Sie ein Programm erstellen, können Sie eine Browseinformationsdatei für das Programm automatisch mithilfe von BSCMAKE zum Erstellen der Datei erstellen. Sie müssen nicht wissen, wie BSCMAKE ausgeführt wird, wenn Sie Ihre Suchinformationsdatei in der Visual Studio-Entwicklungsumgebung erstellen. Vielleicht möchten Sie dieses Thema jedoch lesen, um die verfügbaren Optionen kennenzulernen.

Wenn Sie ein Programm außerhalb der Entwicklungsumgebung erstellen, können Sie weiterhin eine benutzerdefinierte BSC-Datei erstellen, die Sie in der Umgebung untersuchen können. Führen Sie BSCMAKE für die SBR-Dateien aus, die Sie während der Kompilierung erstellt haben.

> [!NOTE]
> Sie können dieses Tool nur über die Eingabeaufforderung für den Befehl Visual Studio Developer starten. Sie können es nicht von einer Systemeingabeaufforderung oder vom Datei-Explorer aus starten.

Dieser Abschnitt umfasst die folgenden Themen:

- [Erstellen von Browseinformationsdateien: Übersicht](building-browse-information-files-overview.md)

- [Erstellen einer BSC-Datei](building-a-dot-bsc-file.md)

- [BSCMAKE-Befehlszeile](bscmake-command-line.md)

- [BSCMAKE-Befehlszeile](bscmake-command-file-response-file.md)

- [BSCMAKE-Optionen](bscmake-options.md)

- [BSCMAKE-Ausgangscodes](bscmake-exit-codes.md)

## <a name="see-also"></a>Siehe auch

[Zusätzliche MSVC-Buildtools](c-cpp-build-tools.md)
