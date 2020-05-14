---
title: 'Vorgehensweise: Debuggen eines Releasebuilds'
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [C++], release builds
- release builds, debugging
ms.assetid: d333e4d1-4e6c-4384-84a9-cb549702da25
ms.openlocfilehash: 6d93fac4e980085c322acb55e6f8758e6cea0a00
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188963"
---
# <a name="how-to-debug-a-release-build"></a>Vorgehensweise: Debuggen eines Releasebuilds

Sie können einen Releasebuild einer Anwendung debuggen.

### <a name="to-debug-a-release-build"></a>Debuggen eines Releasebuilds

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** für das Projekt. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](working-with-project-properties.md).

1. Klicken Sie auf den Knoten **C/C++** . Legen Sie **Debuginformationsformat** auf [C7-Kompatibel (/Z7)](reference/z7-zi-zi-debug-information-format.md) oder **Programmdatenbank (/Zi)** fest.

1. Erweitern Sie **Linker**, und klicken Sie auf den Knoten **Allgemein**. Legen Sie **Inkrementelles Verknüpfen aktivieren** auf [Nein (/INCREMENTAL:NO)](reference/incremental-link-incrementally.md) fest.

1. Klicken Sie auf den Knoten **Debuggen**. Legen Sie **Debuginformationen generieren** auf [Ja (/DEBUG)](reference/debug-generate-debug-info.md) fest.

1. Klicken Sie auf den Knoten **Optimierung**. Legen Sie **Verweise** auf [/OPT:REF](reference/opt-optimizations.md) und **COMDAT-Faltung aktivieren** auf [/OPT:ICF](reference/opt-optimizations.md) fest.

1. Sie können nun Ihre Releasebuildanwendung debuggen. Gehen Sie den Code bei der Suche nach einem Problem durch (oder verwenden Sie das Just-In-Time-Debuggen), bis Sie herausgefunden haben, wo der Fehler auftritt, und ermitteln Sie dann die falschen Parameter bzw. den fehlerhaften Code.

   Wenn eine Anwendung in einem Debugbuild funktioniert, in einem Releasebuild aber fehlschlägt, kann eine der Compileroptimierungen einen Fehler im Quellcode anzeigen. Deaktivieren Sie zum Isolieren des Problems ausgewählte Optimierungen für jede Quellcodedatei, bis Sie die Datei und die Optimierung finden, die das Problem verursachen. (Sie können die Dateien zur Beschleunigung des Prozesses in zwei Gruppen unterteilen und die Optimierung für eine Gruppe deaktivieren. Wenn Sie ein Problem in einer Gruppe feststellen, teilen Sie diese weiter auf, bis Sie die Problemdatei isoliert haben.)

   Mit [/RTC](reference/rtc-run-time-error-checks.md) können Sie versuchen, solche Fehler in Debugbuilds zu ermitteln.

   Weitere Informationen finden Sie unter [Codeoptimierung](optimizing-your-code.md).

## <a name="see-also"></a>Siehe auch

[Beheben von Problemen mit dem Releasebuild](fixing-release-build-problems.md)
