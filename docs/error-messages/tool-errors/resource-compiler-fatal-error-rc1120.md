---
title: 'Ressourcencompiler: Schwerwiegender Fehler RC1120'
ms.date: 11/04/2016
f1_keywords:
- RC1120
helpviewer_keywords:
- RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
ms.openlocfilehash: 855a76ff63145695a7063944701d7acc684e0084
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173009"
---
# <a name="resource-compiler-fatal-error-rc1120"></a>Ressourcencompiler: Schwerwiegender Fehler RC1120

nicht genügend Arbeitsspeicher, benötigte Anzahl von Bytes

Der Ressourcen Compiler hat nicht genügend Speicher für Elemente, die in seinem Heap gespeichert werden. Normalerweise ist dies das Ergebnis einer zu großen Anzahl von Symbolen.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>So beheben Sie den Fehler (unterschiedliche Lösungsmöglichkeiten)

1. Vergrößern Sie den Bereich der Windows-Auslagerungs Datei. Weitere Informationen zum Vergrößern des Auslagerungs Datei-Speicherplatzes finden Sie unter Virtueller Arbeitsspeicher in der Windows-Hilfe.

1. Vermeiden Sie unnötige Includedateien, insbesondere nicht benötigte `#define`s und Funktionsprototypen.

1. Aufteilen Sie die aktuelle Datei in zwei oder mehr Dateien, und kompilieren Sie Sie separat.

1. Entfernen Sie andere Programme oder Treiber, die im System ausgeführt werden, was viel Arbeitsspeicher beanspruchen könnte.
