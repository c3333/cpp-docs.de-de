---
title: Vorteile von Inlineassemblys
ms.date: 08/30/2018
helpviewer_keywords:
- assembler [C++], advantages
- inline assembly [C++], about inline assembly
- inline assembly [C++], using
ms.assetid: 94364d97-faa7-4bdf-8473-570956986c51
ms.openlocfilehash: 7e634f78eca753487cf122ac95df55828bb64625
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169655"
---
# <a name="advantages-of-inline-assembly"></a>Vorteile von Inlineassemblys

**Microsoft-spezifisch**

Da der Inlineassembler keine separaten Assembly- und Verknüpfungsschritte erfordert, ist er einfacher als ein getrennter Assembler. Der Inlineassemblycode kann alle C-Variablen und -Funktionsnamen verwenden, die sich im Gültigkeitsbereich befinden. Daher ist es einfach, ihn in den C-Programmcode zu integrieren. Da der Assemblycode Inline mit c-oder C++ -Anweisungen gemischt werden kann, kann er Aufgaben ausführen, die in c C++oder nicht möglich sind.

Die Verwendung der Inlineassembly umfasst Folgendes:

- Schreiben von Funktionen in Assemblysprache.

- Punktuelles Optimieren von Geschwindigkeits kritischen Code Abschnitten.

- Herstellen von direktem Hardware Zugriff für Gerätetreiber.

- Schreiben von Prolog-und Epilogcode für "Naked"-Aufrufe.

Die Inlineassembly ist ein spezielles Tool. Wenn Sie beabsichtigen, eine Anwendung auf verschiedene Computer zu portieren, möchten Sie wahrscheinlich computerspezifischen Code in einem separaten Modul platzieren. Da der Inline Assembler nicht alle MASM-Makros und Daten Direktiven von Microsoft Macro Assembler unterstützt, ist es möglicherweise bequemer, MASM für solche Module zu verwenden.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Inlineassembler](../../assembler/inline/inline-assembler.md)<br/>
