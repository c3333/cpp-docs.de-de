---
title: Verwenden des Debugbuilds zur Suche nach Speicherüberschreibungen
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: 1345eb4d-24ba-4595-b1cc-2da66986311e
ms.openlocfilehash: 42e3a7f1f1c34ba5a263adfca7496c24e162ab5d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314285"
---
# <a name="using-the-debug-build-to-check-for-memory-overwrite"></a>Verwenden des Debugbuilds zur Suche nach Speicherüberschreibungen

Zum Verwenden des Debugbuilds zur Überprüfung auf Speicherüberschreibungen müssen Sie Ihr Projekt zunächst zum Debuggen neu erstellen. Wechseln Sie dann zum Anfang der `InitInstance`-Funktion Ihrer Anwendung, und fügen Sie die folgende Zeile hinzu:

```
afxMemDF |= checkAlwaysMemDF;
```

Mit der Debug-Speicherbelegungsfunktion werden Wächterbytes um alle Speicherbelegungen gelegt. Diese Wächterbytes helfen jedoch nur, wenn Sie sie auf Veränderungen überprüfen (die auf eine Speicherüberschreibung hindeuten). Andernfalls wird dadurch nur ein Puffer bereitgestellt, der es Ihnen tatsächlich ermöglicht, mit einer Speicherüberschreibung davonzukommen.

Wenn Sie `checkAlwaysMemDF` aktivieren, zwingen Sie MFC jedes Mal, wenn ein Aufruf von **new** oder **delete** erfolgt, zu einem Aufruf der `AfxCheckMemory`-Funktion. Wenn eine Speicherüberschreibung erkannt wurde, wird eine TRACE-Meldung generiert, die in etwa wie folgt aussieht:

```
Damage Occurred! Block=0x5533
```

Wenn eine dieser Meldungen angezeigt wird, müssen Sie den Code schrittweise durchlaufen, um zu bestimmen, an welcher Stelle der Schaden aufgetreten ist. Sie können selbst explizite Aufrufe von `AfxCheckMemory` durchführen, um die Stelle der Speicherüberschreibung genauer einzugrenzen. Zum Beispiel:

```
ASSERT(AfxCheckMemory());
    DoABunchOfStuff();
    ASSERT(AfxCheckMemory());
```

Wenn die erste ASSERT-Anweisung erfolgreich ist und die zweite nicht, bedeutet dies, dass die Speicherüberschreibung in der Funktion zwischen den beiden Aufrufen aufgetreten sein muss.

Abhängig von der Art Ihrer Anwendung stellen Sie möglicherweise fest, dass `afxMemDF` dazu führt, dass Ihr Programm so langsam ausgeführt wird, dass Sie es nicht einmal testen können. Die `afxMemDF`-Variable bewirkt, dass `AfxCheckMemory` für jeden Aufruf von „new“ und „delete“ aufgerufen wird. In diesem Fall sollten Sie Ihre eigenen Aufrufe von `AfxCheckMemory`( ) wie oben gezeigt durchführen und versuchen, die Speicherüberschreibung auf diese Weise einzugrenzen.

## <a name="see-also"></a>Siehe auch

[Beheben von Problemen mit dem Releasebuild](fixing-release-build-problems.md)
