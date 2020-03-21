---
title: 'Erstellen von Browseinformationsdateien: Übersicht'
ms.date: 05/06/2019
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
ms.openlocfilehash: 94cb5865e56e12f51ef4a8598a5df3fcbe69fa0f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078358"
---
# <a name="building-browse-information-files-overview"></a>Erstellen von Browseinformationsdateien: Übersicht

> [!WARNING]
> Obwohl BSCMAKE weiterhin mit Visual Studio installiert wird, wird es nicht mehr von der IDE verwendet. Seit Visual Studio 2008 werden Browse- und Symbolinformationen automatisch in einer SQL Server-.SDF-Datei im Projektmappenordner gespeichert.

Zum Erstellen von Suchinformationen für das Durchsuchen von Symbolen erstellt der Compiler eine SBR-Datei für jede Quelldatei in Ihrem Projekt und dann BSCMAKE. EXE verkettet die SBR-Dateien in eine BSC-Datei.

Das Erstellen von SBR-und BSC-Dateien nimmt Zeit in Kraft, sodass Visual Studio diese Funktionen standardmäßig deaktiviert. Wenn Sie die aktuellen Informationen durchsuchen möchten, müssen Sie die Optionen zum Durchsuchen aktivieren und das Projekt erneut erstellen.

Verwenden Sie [/fr](fr-fr-create-dot-sbr-file.md) oder [/fr](fr-fr-create-dot-sbr-file.md) , um dem Compiler mitzuteilen, dass SBR-Dateien erstellt werden sollen. Zum Erstellen von. BSC-Dateien können Sie [BSCMAKE](bscmake-command-line.md) von der Befehlszeile aus abrufen. Durch die Verwendung von BSCMAKE in der Befehlszeile erhalten Sie eine präzisere Kontrolle über die Bearbeitung von Browseinformationsdateien. Weitere Informationen finden Sie unter [BSCMAKE-Referenz](bscmake-reference.md) .

> [!TIP]
>  Sie können die SBR-Datei Generierung aktivieren, aber die Generierung von. BSC-Dateien deaktivieren. Dies bietet schnelle Builds, ermöglicht Ihnen aber auch, schnell eine neue BSC-Datei zu erstellen, indem Sie die Datei Generierung von BSC aktivieren und das Projekt erstellen.

Sie können die Zeit, den Arbeitsspeicher und den Speicherplatz verringern, die erforderlich sind, um eine BSC-Datei zu erstellen, indem Sie die Größe der BSC-Datei verringern.

Weitere Informationen zum Erstellen einer Browser Datei in der Entwicklungsumgebung finden Sie unter [Allgemeine Eigenschaften Seite (Projekt)](general-property-page-project.md) .

### <a name="to-create-a-smaller-bsc-file"></a>So erstellen Sie eine kleinere BSC-Datei

1. Verwenden Sie [BSCMAKE-Befehlszeilenoptionen](bscmake-options.md) , um Informationen aus der Datei mit den Browseinformationen auszuschließen.

1. Lassen Sie lokale Symbole in einer oder mehreren SBR-Dateien aus, wenn Sie kompilieren oder assemblieren.

1. Wenn eine Objektdatei keine Informationen enthält, die für die aktuelle Phase des Debuggens benötigt werden, lassen Sie die SBR-Datei aus dem BSCMAKE-Befehl Weg, wenn Sie die Datei zum Durchsuchen von Informationen neu erstellen.

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>So kombinieren Sie die Browseinformationen aus mehreren Projekten in einer Browser Datei (. BSC)

1. Erstellen Sie entweder die BSC-Datei nicht auf Projektebene, oder verwenden Sie den Schalter/n, um zu verhindern, dass die SBR-Dateien abgeschnitten werden.

1. Nachdem alle Projekte erstellt wurden, führen Sie BSCMAKE mit allen SBR-Dateien als Eingabe aus. Platzhalter werden akzeptiert. Wenn Sie z. b. die Projekt Verzeichnisse c:\x, c:\y haben, und c:\Z mit SBR-Dateien, die Sie in einer BSC-Datei kombinieren wollten. verwenden Sie dann BSCMAKE c:\x\\\*. SBR c:\y\\\*. SBR c:\Z\\\*. SBR/o c:\ whatever_directory \combined.BSC, um die kombinierte BSC-Datei zu erstellen.

## <a name="see-also"></a>Weitere Informationen

[Zusätzliche MSVC-Buildtools](c-cpp-build-tools.md)<br/>
[BSCMAKE-Referenz](bscmake-reference.md)
