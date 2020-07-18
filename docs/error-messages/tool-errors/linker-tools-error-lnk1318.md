---
title: Linkertoolfehler LNK1318
ms.date: 05/29/2018
f1_keywords:
- LNK1318
helpviewer_keywords:
- LNK1318
ms.openlocfilehash: cce2c03783039a62b5cb6f60ecf8d76b23589483
ms.sourcegitcommit: e15b46ea7888dbdd7e0bb47da76aeed680c3c1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2020
ms.locfileid: "86446700"
---
# <a name="linker-tools-error-lnk1318"></a>Linkertoolfehler LNK1318

> Unerwarteter PDB-Fehler. *Ursache* '*Details*'

Der Linker hat einen unerwarteten Fehler beim Öffnen, lesen oder schreiben in eine PDB-Datei feststellen.

Diese Fehlermeldung wird für ungewöhnliche Probleme in PDB-Dateien erzeugt. Die *Ursache* und die *Details* stellen die Informationen dar, die für den Linker verfügbar sind, als der Fehler aufgetreten ist. Dies ist möglicherweise nicht sehr nützlich, da häufige Fehler beim Umgang mit PDB-Dateien separate, informative Fehlermeldungen aufweisen.

Da die Fehlerquelle nicht üblich ist, stehen nur allgemeine Ratschläge zum Beheben dieses Problems zur Verfügung:

- Führen Sie einen sauberen Vorgang in den buildverzeichnissen aus, und führen Sie dann einen vollständigen Build der Projekt Mappe aus.

- Starten Sie den Computer neu, oder überprüfen Sie, ob mspdbsrv.exe Prozesse nicht reagiert oder nicht reagiert, und beenden Sie Sie in Task Manager.

- Deaktivieren Sie die antivirenüberprüfungen in Ihren Projekt Verzeichnissen.

- Verwenden Sie die [/ZF](../../build/reference/zf.md) -Compileroption, wenn Sie [/MP](../../build/reference/mp-build-with-multiple-processes.md) mit MSBuild oder einem anderen parallelen Buildprozess verwenden.

- Versuchen Sie, mit dem 64-Bit-gehosteten Toolset zu entwickeln.

- Serialisieren Sie Verknüpfungen, um bei Bedarf parallele Link Probleme zu vermeiden. Dieser Fehler kann verursacht werden, wenn mspdbsrv.exe durch eine Instanz von Link gestartet wird und heruntergefahren wird, bevor eine andere Instanz von Link verwendet wird. Der Nachteil dieser Lösung ist, dass die Erstellung Ihrer Projekt Builds erheblich länger dauern kann.
