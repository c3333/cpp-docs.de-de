---
title: Einschränkungen bei Ereignishandlern
ms.date: 11/04/2016
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
ms.openlocfilehash: 1f80cb1574cbfef0783c7e55dcd198dfb822f566
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225903"
---
# <a name="restrictions-on-exception-handlers"></a>Einschränkungen bei Ereignishandlern

Die Haupteinschränkung bei der Verwendung von Ausnahme Handlern im Code besteht darin, dass Sie keine-Anweisung verwenden können **`goto`** , um in einen **__try** -Anweisungsblock zu springen. Stattdessen müssen Sie den Anweisungsblock über die normale Ablaufsteuerung eingeben. Sie können aus einem **__try** -Anweisungsblock springen und Ausnahmehandler bei der Auswahl Schachteln.

## <a name="see-also"></a>Siehe auch

[Schreiben eines Ausnahme Handlers](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
