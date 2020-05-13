---
title: 'Erstellen von Browseinformationsdateien: Übersicht'
ms.date: 05/06/2019
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
ms.openlocfilehash: ffacb7aaf9ac1f7ad6fc4cf12ab479099dc57725
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320674"
---
# <a name="building-browse-information-files-overview"></a>Erstellen von Browseinformationsdateien: Übersicht

> [!WARNING]
> Obwohl BSCMAKE weiterhin mit Visual Studio installiert wird, wird es nicht mehr von der IDE verwendet. Seit Visual Studio 2008 werden Browse- und Symbolinformationen automatisch in einer SQL Server-.SDF-Datei im Projektmappenordner gespeichert.

Um Suchinformationen für das Durchsuchen von Symbolen zu erstellen, erstellt der Compiler eine .sbr-Datei für jede Quelldatei in Ihrem Projekt und dann BSCMAKE. EXE verkettet die .sbr-Dateien in einer BSC-Datei.

Das Generieren von .sbr- und .bsc-Dateien nimmt Zeit in Anspruch, sodass Visual Studio diese Funktionen standardmäßig deaktiviert. Wenn Sie aktuelle Informationen durchsuchen möchten, müssen Sie die Suchoptionen aktivieren und Das Projekt erneut erstellen.

Verwenden Sie [/FR](fr-fr-create-dot-sbr-file.md) oder [/Fr,](fr-fr-create-dot-sbr-file.md) um den Compiler anzuweisen, .sbr-Dateien zu erstellen. Um BSC-Dateien zu erstellen, können Sie [BSCMAKE](bscmake-command-line.md) über die Befehlszeile aufrufen. Mit BSCMAKE über die Befehlszeile können Sie die Manipulation von Suchinformationsdateien genauer steuern. Weitere Informationen finden Sie unter [BSCMAKE-Referenz.](bscmake-reference.md)

> [!TIP]
> Sie können die .sbr-Dateigenerierung aktivieren, aber die .bsc-Dateigenerierung deaktiviert lassen. Dies bietet schnelle Builds, ermöglicht es Ihnen aber auch, schnell eine neue BSC-Datei zu erstellen, indem Sie .bsc-Dateigenerierung aktivieren und das Projekt erstellen.

Sie können den Zeit-, Arbeitsspeicher- und Festplattenspeicher reduzieren, der zum Erstellen einer BSC-Datei erforderlich ist, indem Sie die Größe der BSC-Datei reduzieren.

Informationen zum Erstellen einer Browserdatei in der Entwicklungsumgebung finden Sie unter [General Property Page (Project).](general-property-page-project.md)

### <a name="to-create-a-smaller-bsc-file"></a>So erstellen Sie eine kleinere .bsc-Datei

1. Verwenden Sie [BSCMAKE-Befehlszeilenoptionen,](bscmake-options.md) um Informationen aus der Suchinformationsdatei auszuschließen.

1. Lassen Sie beim Kompilieren oder Zusammenstellen lokale Symbole in einer oder mehreren .sbr-Dateien weg.

1. Wenn eine Objektdatei keine Informationen enthält, die für die aktuelle Phase des Debuggens erforderlich sind, lassen Sie die .sbr-Datei aus dem Befehl BSCMAKE weg, wenn Sie die Suchinformationsdatei neu erstellen.

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>So kombinieren Sie die Suchinformationen aus mehreren Projekten in einer Browserdatei (.bsc)

1. Erstellen Sie die BSC-Datei nicht auf Projektebene, oder verwenden Sie den Schalter /n, um zu verhindern, dass die .sbr-Dateien abgeschnitten werden.

1. Nachdem alle Projekte erstellt wurden, führen Sie BSCMAKE mit allen .sbr-Dateien als Eingabe aus. Wildcards werden akzeptiert. Wenn Sie z. B. Projektverzeichnisse C:-X, C:-Y und C:-Z mit .sbr-Dateien in sich hatten und sie alle in\\\*einer BSC-Datei\\\*kombinieren möchten, verwenden\\\*Sie bscMAKE C:'X .sbr C:'Y .sbr C:'Z .sbr /o c:'whatever_directory'combined.bsc, um die kombinierte .bsc-Datei zu erstellen.

## <a name="see-also"></a>Siehe auch

[Zusätzliche MSVC-Buildtools](c-cpp-build-tools.md)<br/>
[BSCMAKE-Referenz](bscmake-reference.md)
