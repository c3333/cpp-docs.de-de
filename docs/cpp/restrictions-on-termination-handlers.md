---
title: Einschränkungen bei Beendigungshandlern
description: Die Einschränkungen bei der Behandlung von Beendigungs Handlern für die strukturierte Ausnahmebehandlung
ms.date: 08/24/2020
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
ms.openlocfilehash: 60fdb4c2a105f2fce4a32f475563a04f8e7bfaf9
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898271"
---
# <a name="restrictions-on-termination-handlers"></a>Einschränkungen bei Beendigungshandlern

Sie können keine- **`goto`** Anweisung verwenden, um in einen **`__try`** Anweisungsblock oder einen **`__finally`** Anweisungsblock zu springen. Stattdessen müssen Sie den Anweisungsblock über die normale Ablaufsteuerung eingeben. (Sie können jedoch aus einem **`__try`** Anweisungsblock herausspringen.) Außerdem ist es nicht möglich, einen Ausnahmehandler oder Beendigungs Handler innerhalb eines-Blocks zu Schachteln **`__finally`** .

Einige Arten von Code, die in einem Beendigungs Handler zulässig sind, führen zu fragwürdigen Ergebnissen. Sie sollten Sie daher mit Bedacht verwenden, wenn überhaupt. Eine ist eine- **`goto`** Anweisung, die aus einem- **`__finally`** Anweisungsblock springt. Wenn der Block im Rahmen der normalen Beendigung ausgeführt wird, passiert nichts Ungewöhnliches. Wenn das System jedoch den Stapel entwickelt, wird die Entwickelung angehalten. Dann erhält die aktuelle Funktion die Steuerung so, als ob keine ungewöhnliche Beendigung vorhanden wäre.

Eine- **`return`** Anweisung innerhalb eines **`__finally`** Anweisungsblocks stellt ungefähr dieselbe Situation dar. Die Steuerung wird an den unmittelbaren Aufrufer der Funktion zurückgegeben, die den Beendigungs Handler enthält. Wenn das System den Stapel entwickelt, wird dieser Prozess angehalten. Anschließend wird das Programm fortgesetzt, als ob keine Ausnahme ausgelöst wurde.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Beendigungshandlers](../cpp/writing-a-termination-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
