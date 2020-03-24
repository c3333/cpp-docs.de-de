---
title: Schwerwiegender Fehler C1060
ms.date: 11/04/2016
f1_keywords:
- C1060
helpviewer_keywords:
- C1060
ms.assetid: feaf305c-c84c-4160-b974-50e283412849
ms.openlocfilehash: f1a7c3ccab716a9281d4520f4c5fce2afff60187
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204437"
---
# <a name="fatal-error-c1060"></a>Schwerwiegender Fehler C1060

Kein verfügbarer Speicher mehr im Heap

Das Betriebssystem oder die Laufzeitbibliothek können keine Speicheranforderung füllen.

### <a name="to-fix-this-error-try-the-following-possible-solutions"></a>Versuchen Sie zum Beheben dieses Fehlers die folgenden Lösungen

1. Wenn der Compiler auch Fehler [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) und [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md)ausgibt, verwenden Sie die [/ZM](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) -Compileroption, um das Limit für die Speicher Belegung zu verringern. Mehr Heapspeicher ist für Ihre Anwendung verfügbar, wenn Sie die verbleibende Speicherzuweisung reduzieren.

   Wenn die [/ZM](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) -Option bereits festgelegt ist, versuchen Sie, Sie zu entfernen. Der Heap-Speicher ist möglicherweise erschöpft, weil die in der Option angegebene maximale Speicherzuweisung zu hoch ist. Der Compiler verwendet ein Standard Limit, wenn Sie die [/ZM](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) -Option entfernen.

1. Wenn Sie auf einer 64-Bit-Plattform kompilieren, verwenden Sie das 64-Bit-Compilertoolset. Weitere Informationen finden Sie unter Gewusst [wie: Aktivieren eines C++ visuellen 64-Bit-Toolsets in der Befehlszeile](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).

1. Verwenden Sie unter 32-Bit-Windows den Schalter [/3GB](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) Boot. ini.

1. Vergrößern Sie die Windows-Auslagerungsdatei.

1. Schließen Sie andere ausgeführte Programme.

1. Löschen Sie überflüssige Includedateien.

1. Entfernen Sie unnötige globale Variablen, indem Sie beispielsweise Speicher dynamisch belegen, anstatt ein umfangreiches Array zu deklarieren.

1. Entfernen Sie nicht benötigte Deklarationen.

9. Teilen Sie die aktuelle Datei in kleinere Dateien auf.
