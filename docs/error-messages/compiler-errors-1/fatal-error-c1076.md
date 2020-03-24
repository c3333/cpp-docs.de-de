---
title: Schwerwiegender Fehler C1076
ms.date: 03/08/2019
f1_keywords:
- C1076
helpviewer_keywords:
- C1076
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
ms.openlocfilehash: ca5117342d406983e8cba675c2589d2431d09d38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204177"
---
# <a name="fatal-error-c1076"></a>Schwerwiegender Fehler C1076

> Compilerlimit: Interne Heapgrenze erreicht; Verwenden Sie /Zm, um eine höhere Grenze anzugeben

Dieser Fehler kann durch zu viele Symbole oder Vorlageninstanziierungen verursacht werden. Ab Visual Studio 2015 kann diese Meldung durch zu viele parallele Buildprozesse von der Auslastung des virtuellen Windows-Speichers verursacht werden. In diesem Fall sollte die Empfehlung zur Verwendung der **/ZM** -Option ignoriert werden, es sei denn, Sie verwenden eine `#pragma hdrstop` Direktive.

So beheben Sie diesen Fehler

1. Wenn der vorkompilierte Header eine `#pragma hdrstop`-Direktive verwendet, verwenden Sie die [/ZM](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) -Option, um das compilerarbeitsspeicherlimit auf den in der [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) -Fehlermeldung angegebenen Wert festzulegen. Weitere Informationen zum Festlegen dieses Werts in Visual Studio finden Sie im Abschnitt "Hinweise" unter [/ZM (Limit für die Speicher Belegung der vorkompilierten Header angeben)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).

1. Reduzieren Sie ggf. die Anzahl paralleler Prozesse, die mit der Option **/maxcpucount** für MSBuild angegeben werden. EXE in Verbindung mit der **/MP** -Option zu cl. Speichert. Weitere Informationen finden Sie unter [Probleme mit vorkompilierten Headern (PCH) und Empfehlungen](https://devblogs.microsoft.com/cppblog/precompiled-header-pch-issues-and-recommendations/).

1. Verwenden Sie in einem 64-Bit-Betriebssystem anstelle von gehosteten 32-Bit-Compilern gehostete 64-Bit-Compiler. Weitere Informationen finden Sie unter Gewusst [wie: Aktivieren eines C++ visuellen 64-Bit-Toolsets in der Befehlszeile](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).

1. Löschen Sie überflüssige Includedateien.

1. Entfernen Sie unnötige globale Variablen, indem Sie beispielsweise Speicher dynamisch belegen, anstatt ein umfangreiches Array zu deklarieren.

1. Entfernen Sie nicht benötigte Deklarationen.

Wenn C1076 unmittelbar nach dem Start des Builds auftritt, ist der für **/ZM** angegebene Wert für das Programm wahrscheinlich zu hoch. Reduzieren Sie den **/ZM** -Wert.
