---
title: Einschränkungen bei Beendigungshandlern
ms.date: 11/04/2016
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
ms.openlocfilehash: befe181a41ed418a4a824b131e741a9f02f90e38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179067"
---
# <a name="restrictions-on-termination-handlers"></a>Einschränkungen bei Beendigungshandlern

Sie können keine **goto** -Anweisung verwenden, um in einen **__try** Anweisungsblock oder einen **__finally** -Anweisungsblock zu springen. Stattdessen müssen Sie den Anweisungsblock über die normale Ablaufsteuerung eingeben. (Sie können jedoch aus einem **__try** -Anweisungsblock herausspringen.) Außerdem ist es nicht möglich, einen Ausnahmehandler oder Beendigungs Handler in einem **__finally** Block zu schachteln.

Darüber hinaus erzeugen einige in einem Beendigungshandler zulässige Arten von Code fragliche Ergebnisse. Daher sollten Sie diese, wenn überhaupt, mit Vorsicht verwenden. Eine ist eine **goto** -Anweisung, die aus einem **__finally** -Anweisungsblock springt. Wenn der Block als Teil der normalen Beendigung ausgeführt wird, passiert nichts Ungewöhnliches. Aber wenn das System den Stapel entlädt, wird das Entladen gestoppt, und die aktuelle Funktion erhält die Steuerung,als ob keine nicht ordnungsgemäße Beendigung vorläge.

Eine **Return** -Anweisung in einem **__finally** -Anweisungsblock stellt ungefähr dieselbe Situation dar. Die Steuerung wird an den unmittelbaren Aufrufer der Funktion zurückgegeben, die den Beendigungshandler enthält. Wenn das System beim Entladen des Stapels war, wird dieser Prozess unterbrochen, und das Programm wird fortgesetzt, als wäre keine Ausnahme ausgelöst worden.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Beendigungs Handlers](../cpp/writing-a-termination-handler.md)<br/>
[Strukturierte Ausnahmebehandlung (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
