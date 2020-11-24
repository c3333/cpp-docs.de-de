---
title: Ereignisbehandlung
description: Erfahren Sie, wie Microsoft C++ Extensions sowohl com-als auch native Ereignis Behandlung unterstützen.
ms.date: 11/20/2020
helpviewer_keywords:
- event handling [C++]
ms.openlocfilehash: de8cd6dfac2b83e850ec62ff88e192d1c60e427e
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483126"
---
# <a name="event-handling"></a>Behandlung von Ereignissen

Ereignis Behandlung wird hauptsächlich für COM-Klassen unterstützt (C++-Klassen, die COM-Objekte implementieren, in der Regel mit ATL-Klassen oder dem [Co-Klasse](../windows/attributes/coclass.md) -Attribut). Weitere Informationen finden Sie unter [Ereignis Behandlung in com](../cpp/event-handling-in-com.md).

Die Ereignis Behandlung wird auch für Native C++-Klassen (C++-Klassen, die keine COM-Objekte implementieren) unterstützt. Die native C++-Unterstützung für die Ereignis Behandlung ist veraltet und wird in einer zukünftigen Version entfernt. Weitere Informationen finden Sie unter [Ereignis Behandlung in nativem C++](../cpp/event-handling-in-native-cpp.md).

> [!NOTE]
> Ereignis Attribute in nativem C++ sind mit Standard-C++ nicht kompatibel. Sie werden nicht kompiliert, wenn Sie den [`/permissive-`](../build/reference/permissive-standards-conformance.md) Konformitäts Modus angeben.

Die Ereignis Behandlung unterstützt sowohl die Verwendung von Einzel-als auch Multithread. Sie schützt Daten vor gleichzeitigem Multithreadzugriff. Sie können Unterklassen von Ereignis Quell-oder Empfänger Klassen ableiten. Diese Unterklassen unterstützen die Beschaffung und den Empfang erweiterter Ereignisse.

Der Microsoft C++-Compiler umfasst Attribute und Schlüsselwörter zum Deklarieren von Ereignissen und Ereignis Handlern. Die Ereignisattribute und Schlüsselwörter können in CLR-Programmen und in systemeigenen C++-Programmen verwendet werden.

| Artikel | BESCHREIBUNG |
|--|--|
| [`event_source`](../windows/attributes/event-source.md) | Erstellt eine Ereignisquelle. |
| [`event_receiver`](../windows/attributes/event-receiver.md) | Erstellt einen Ereignisempfänger (Senke). |
| [`__event`](../cpp/event.md) | Deklariert ein Ereignis. |
| [`__raise`](../cpp/raise.md) | Hebt die Aufrufsite eines Ereignisses hervor. |
| [`__hook`](../cpp/hook.md) | Ordnet eine Handlermethode einem Ereignis zu. |
| [`__unhook`](../cpp/unhook.md) | Trennt eine Handlermethode von einem Ereignis. |

## <a name="see-also"></a>Siehe auch

[C#-Programmiersprachenreferenz](../cpp/cpp-language-reference.md)\
[Schlüsselwörter](../cpp/keywords-cpp.md)
