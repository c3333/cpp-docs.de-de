---
title: Schreiben eines Beendigungshandlers
ms.date: 11/04/2016
helpviewer_keywords:
- structured exception handling [C++], termination handlers
- exceptions [C++], terminating
- termination handlers [C++], writing
- handlers [C++]
- handlers [C++], termination
- termination handlers
- exception handling [C++], termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 52aa1f8f-f8dd-44b8-be94-5e2fc88d44fb
ms.openlocfilehash: 8a243281e0d984a42cd4b4d9f249d867812d8bca
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187309"
---
# <a name="writing-a-termination-handler"></a>Schreiben eines Beendigungshandlers

Im Gegensatz zu einem Ausnahmehandler wird ein Beendigungshandler immer ausgeführt, unabhängig davon, ob der geschützte Codeblock ordnungsgemäß beendet wurde. Der Beendigungshandler sollte nur sicherstellen, dass Ressourcen, wie Arbeitsspeicher, Handles und Dateien ordnungsgemäß geschlossen werden, unabhängig davon, wie die Ausführung eines Codeabschnitts beendet wird.

Beendigungshandler verwenden die try-finally-Anweisung.

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [Die try-endlich-Anweisung](../cpp/try-finally-statement.md)

- [Bereinigen von Ressourcen](../cpp/cleaning-up-resources.md)

- [Zeitliche Steuerung von Aktionen in der Ausnahmebehandlung](../cpp/timing-of-exception-handling-a-summary.md)

- [Einschränkungen bei Beendigungs Handlern](../cpp/restrictions-on-termination-handlers.md)

## <a name="see-also"></a>Weitere Informationen

[Strukturierte Ausnahmebehandlung (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
