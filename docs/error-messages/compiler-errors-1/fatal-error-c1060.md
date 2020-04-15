---
title: Schwerwiegender Fehler C1060
ms.date: 11/04/2016
f1_keywords:
- C1060
helpviewer_keywords:
- C1060
ms.assetid: feaf305c-c84c-4160-b974-50e283412849
ms.openlocfilehash: 83135b77ceb75b4c2b05211260d1aed8fac6777f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320294"
---
# <a name="fatal-error-c1060"></a>Schwerwiegender Fehler C1060

Kein verfügbarer Speicher mehr im Heap

Das Betriebssystem oder die Laufzeitbibliothek können keine Speicheranforderung füllen.

### <a name="to-fix-this-error-try-the-following-possible-solutions"></a>Versuchen Sie zum Beheben dieses Fehlers die folgenden Lösungen 

1. Wenn der Compiler auch die Fehler [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) und [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md)ausgibt, verwenden Sie die Compileroption [/Zm,](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) um das Speicherzuweisungslimit zu senken. Mehr Heapspeicher ist für Ihre Anwendung verfügbar, wenn Sie die verbleibende Speicherzuweisung reduzieren.

   Wenn die Option [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) bereits festgelegt ist, versuchen Sie, sie zu entfernen. Der Heap-Speicher ist möglicherweise erschöpft, weil die in der Option angegebene maximale Speicherzuweisung zu hoch ist. Der Compiler verwendet ein Standardlimit, wenn Sie die Option [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) entfernen.

1. Wenn Sie auf einer 64-Bit-Plattform kompilieren, verwenden Sie das 64-Bit-Compilertoolset. Weitere Informationen finden Sie unter [Gewusst wie: Aktivieren eines 64-Bit Visual C++ Toolsets in der Befehlszeile](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).

1. Versuchen Sie unter 32-Bit-Windows, den Schalter [/3GB](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) boot.ini zu verwenden.

1. Vergrößern Sie die Windows-Auslagerungsdatei.

1. Schließen Sie andere ausgeführte Programme.

1. Löschen Sie überflüssige Includedateien.

1. Entfernen Sie unnötige globale Variablen, indem Sie beispielsweise Speicher dynamisch belegen, anstatt ein umfangreiches Array zu deklarieren.

1. Entfernen Sie nicht benötigte Deklarationen.

1. Teilen Sie die aktuelle Datei in kleinere Dateien auf.
