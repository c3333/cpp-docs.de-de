---
title: Linkertoolfehler LNK1318
ms.date: 05/29/2018
f1_keywords:
- LNK1318
helpviewer_keywords:
- LNK1318
ms.openlocfilehash: a61c11a9cbb25fea6fddc0bf1c5c4c2a7af1cf4f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183578"
---
# <a name="linker-tools-error-lnk1318"></a>Linkertoolfehler LNK1318

> Unerwarteter PDB-Fehler. *Ursache* '*Details*'

Der Linker hat einen unerwarteten Fehler beim Öffnen, lesen oder schreiben in eine PDB-Datei feststellen.

Diese Fehlermeldung wird für ungewöhnliche Probleme in PDB-Dateien erzeugt. Die *Ursache* und die *Details* stellen die Informationen dar, die für den Linker verfügbar sind, als der Fehler aufgetreten ist. Dies ist möglicherweise nicht sehr nützlich, da häufige Fehler beim Umgang mit PDB-Dateien separate, informative Fehlermeldungen aufweisen.

Da die Fehlerquelle nicht üblich ist, stehen nur allgemeine Ratschläge zum Beheben dieses Problems zur Verfügung:

- Führen Sie einen sauberen Vorgang in den buildverzeichnissen aus, und führen Sie dann einen vollständigen Build der Projekt Mappe aus.

- Starten Sie den Computer neu, oder überprüfen Sie, ob die Prozesse "mspdbsrv. exe" oder "nicht verfügbar" sind

- Deaktivieren Sie die antivirenüberprüfungen in Ihren Projekt Verzeichnissen.

- Verwenden Sie die [/ZF](../../build/reference/zf.md) -Compileroption, wenn Sie [/MP](../../build/reference/mp-build-with-multiple-processes.md) mit MSBuild oder einem anderen parallelen Buildprozess verwenden.

- Versuchen Sie, mit dem 64-Bit-gehosteten Toolset zu entwickeln.

- Serialisieren Sie Verknüpfungen, um bei Bedarf parallele Link Probleme zu vermeiden. Dieser Fehler kann verursacht werden, wenn "mspdbsrv. exe" von einer Instanz von Link gestartet wird und heruntergefahren wird, bevor eine andere Instanz von Link verwendet wird. Der Nachteil dieser Lösung ist, dass die Erstellung Ihrer Projekt Builds erheblich länger dauern kann.
