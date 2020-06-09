---
title: Klassen für Debugging und Ausnahmen
ms.date: 11/04/2016
f1_keywords:
- vc.classes.debug
helpviewer_keywords:
- debugging [MFC], exception classes
- debugging [MFC], classes for debugging
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
ms.openlocfilehash: 6c7d1fc20556993c3c6690122786d7a767d895ad
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625938"
---
# <a name="debugging-and-exception-classes"></a>Klassen für Debugging und Ausnahmen

Diese Klassen bieten Unterstützung für das Debuggen der dynamischen Speicher Belegung und das Übergeben von Ausnahme Informationen von der Funktion, bei der die Ausnahme an die Funktion ausgelöst wird, in der Sie abgefangen wird.

Verwenden Sie die Klassen [CDumpContext](reference/cdumpcontext-class.md) und [CMemoryState](reference/cmemorystate-structure.md) während der Entwicklung, um das Debuggen zu unterstützen, wie unter [Debugging MFC-Anwendungen](/visualstudio/debugger/mfc-debugging-techniques)beschrieben. Verwenden Sie [CRuntimeClass](reference/cruntimeclass-structure.md) , um die Klasse eines beliebigen Objekts zur Laufzeit zu bestimmen, wie im Artikel [zugreifen auf Lauf Zeit Klassen Informationen](accessing-run-time-class-information.md)beschrieben. Das Framework verwendet `CRuntimeClass` , um Objekte einer bestimmten Klasse dynamisch zu erstellen.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](class-library-overview.md)
