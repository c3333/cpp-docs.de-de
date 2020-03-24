---
title: Schreiben eines Ausnahmehandlers
ms.date: 11/04/2016
helpviewer_keywords:
- structured exception handling [C++], exception handlers
- exception handling [C++], exception handlers
ms.assetid: 71473fee-f773-4a34-bf12-82a3af79579c
ms.openlocfilehash: 201dcaa6a90584d1f9535df11d5722a37bdceb89
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187283"
---
# <a name="writing-an-exception-handler"></a>Schreiben eines Ausnahmehandlers

Ausnahmehandler werden in der Regel verwendet, um auf bestimmte Fehler zu reagieren. Sie können die Syntax für die Ausnahmebehandlung nutzen, um alle Ausnahmen außer denen zu filtern, deren Behandlung bekannt ist. Andere Ausnahmen sollten an andere Handler übergeben werden (möglicherweise in der Laufzeitbibliothek oder im Betriebssystem), die geschrieben wurden, um nach diesen speziellen Ausnahmen zu suchen.

Ausnahmehandler verwenden die try-except-Anweisung.

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [Die Try-außer-Anweisung](../cpp/try-except-statement.md)

- [Schreiben eines Ausnahme Filters](../cpp/writing-an-exception-filter.md)

- [Auswerfen von Software Ausnahmen](../cpp/raising-software-exceptions.md)

- [Hardware Ausnahmen](../cpp/hardware-exceptions.md)

- [Einschränkungen bei Ausnahme Handlern](../cpp/restrictions-on-exception-handlers.md)

## <a name="see-also"></a>Weitere Informationen

[Strukturierte Ausnahmebehandlung (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
