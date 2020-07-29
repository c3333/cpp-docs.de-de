---
title: Einschränkungen bei Beendigungshandlern
ms.date: 11/04/2016
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
ms.openlocfilehash: d53792afbc3d25fb21edafa7817919b63b79ab65
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225890"
---
# <a name="restrictions-on-termination-handlers"></a>Einschränkungen bei Beendigungshandlern

Eine-Anweisung kann nicht verwendet werden **`goto`** , um in einen **__try** Anweisungsblock oder einen **`__finally`** Anweisungsblock zu springen. Stattdessen müssen Sie den Anweisungsblock über die normale Ablaufsteuerung eingeben. (Sie können jedoch aus einem **__try** -Anweisungsblock herausspringen.) Außerdem ist es nicht möglich, einen Ausnahmehandler oder Beendigungs Handler innerhalb eines-Blocks zu Schachteln **`__finally`** .

Darüber hinaus erzeugen einige in einem Beendigungshandler zulässige Arten von Code fragliche Ergebnisse. Daher sollten Sie diese, wenn überhaupt, mit Vorsicht verwenden. Eine ist eine- **`goto`** Anweisung, die aus einem- **`__finally`** Anweisungsblock springt. Wenn der Block als Teil der normalen Beendigung ausgeführt wird, passiert nichts Ungewöhnliches. Aber wenn das System den Stapel entlädt, wird das Entladen gestoppt, und die aktuelle Funktion erhält die Steuerung,als ob keine nicht ordnungsgemäße Beendigung vorläge.

Eine- **`return`** Anweisung innerhalb eines **`__finally`** Anweisungsblocks stellt ungefähr dieselbe Situation dar. Die Steuerung wird an den unmittelbaren Aufrufer der Funktion zurückgegeben, die den Beendigungshandler enthält. Wenn das System beim Entladen des Stapels war, wird dieser Prozess unterbrochen, und das Programm wird fortgesetzt, als wäre keine Ausnahme ausgelöst worden.

## <a name="see-also"></a>Siehe auch

[Schreiben eines Beendigungshandlers](../cpp/writing-a-termination-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
