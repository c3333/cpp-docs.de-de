---
title: Einschränkungen bei Ereignishandlern
ms.date: 11/04/2016
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
ms.openlocfilehash: 54bf4a44d06eacd22dc4b9819d160d3c6a66c684
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179080"
---
# <a name="restrictions-on-exception-handlers"></a>Einschränkungen bei Ereignishandlern

Die Prinzipal Einschränkung bei der Verwendung von Ausnahme Handlern im Code besteht darin, dass Sie keine **goto** -Anweisung verwenden können, um in einen **__try** Anweisungsblock zu springen. Stattdessen müssen Sie den Anweisungsblock über die normale Ablaufsteuerung eingeben. Sie können aus einem **__try** -Anweisungsblock springen und Ausnahmehandler bei der Auswahl Schachteln.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Ausnahmehandlers](../cpp/writing-an-exception-handler.md)<br/>
[Strukturierte Ausnahmebehandlung (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
