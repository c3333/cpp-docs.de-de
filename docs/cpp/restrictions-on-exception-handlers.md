---
title: Einschränkungen bei Ereignishandlern
description: Beschreibt die Einschränkungen beim springen in strukturierte Ausnahme Behandlungs Blöcke.
ms.date: 08/24/2020
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
ms.openlocfilehash: c4182f065789533bf7599621d8d2829b2d52d6ed
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898455"
---
# <a name="restrictions-on-exception-handlers"></a>Einschränkungen bei Ereignishandlern

Die Haupteinschränkung bei der Verwendung von Ausnahme Handlern im Code besteht darin, dass Sie keine-Anweisung verwenden können **`goto`** , um in einen- **`__try`** Anweisungsblock zu springen. Stattdessen müssen Sie den Anweisungsblock über die normale Ablaufsteuerung eingeben. Sie können aus einem **`__try`** -Anweisungsblock herausspringen, und Sie können die von Ihnen ausgewählten Ausnahmehandler verschachteln.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Ausnahmehandlers](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
