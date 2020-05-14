---
title: Suchen nach Speicherüberschreibungen
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
ms.openlocfilehash: 2c59cb96d640df6dcd96b9e0eafbcd325ed475f5
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342258"
---
# <a name="checking-for-memory-overwrites"></a>Suchen nach Speicherüberschreibungen

Wenn bei einem Aufruf einer Heapbearbeitungsfunktion eine Zugriffsverletzung auftritt, hat das Programm möglicherweise den Heap beschädigt. Ein typisches Symptom für diese Situation wäre:

```
Access Violation in _searchseg
```

Die [_heapchk](../c-runtime-library/reference/heapchk.md)-Funktion ist sowohl in Debug- als auch in Releasebuilds verfügbar (nur Windows NT), um die Integrität des Laufzeitbibliotheksheaps zu überprüfen. Sie können `_heapchk` ähnlich wie die `AfxCheckMemory`-Funktion verwenden, um eine Heapüberschreibung zu isolieren, z. B.:

```
if(_heapchk()!=_HEAPOK)
   DebugBreak();
```

Sollte diese Funktion jemals fehlschlagen, müssen Sie die Isolierung an dem Punkt vornehmen, an dem der Heap beschädigt wurde.

## <a name="see-also"></a>Siehe auch

[Beheben von Problemen mit dem Releasebuild](fixing-release-build-problems.md)
