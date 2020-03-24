---
title: Ereignisbehandlung
ms.date: 05/07/2019
helpviewer_keywords:
- event handling [C++]
ms.assetid: 82de3f9a-2d88-470c-9527-8a5b54c8ced4
ms.openlocfilehash: cf16ea0e6e14981f1105456a5f17d68c05a9c3fa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189207"
---
# <a name="event-handling"></a>Ereignisbehandlung

Ereignis Behandlung wird hauptsächlich für COM-KlassenC++ (Klassen, die COM-Objekte implementieren, in der Regel mit ATL-Klassen oder dem [Co-Klasse](../windows/coclass.md) -Attribut) unterstützt. Weitere Informationen finden Sie unter [Ereignis Behandlung in com](../cpp/event-handling-in-com.md).

Ereignisbehandlung wird auch für systemeigene C++-Klassen (C++-Klassen, die keine COM-Objekte implementieren) unterstützt. Die Unterstützung ist jedoch veraltet und wird in einer der nächsten Versionen entfernt werden.  Weitere Informationen finden Sie unter [Ereignis Behandlung in nativem C++ ](../cpp/event-handling-in-native-cpp.md)Modus.

Die Ereignisbehandlung unterstützt Einzel- und Multithreadverwendung und schützt Daten vor gleichzeitigem Multithreadzugriff. Sie ermöglicht Ihnen auch das Ableiten von Unterklassen aus Ereignisquellklassen oder Ereignisempfängerklassen und unterstützt die erweiterte Ereignisquellentnahme bzw. den Ereignisempfang in der abgeleiteten Klasse.

Der Microsoft C++ -Compiler umfasst Attribute und Schlüsselwörter zum Deklarieren von Ereignissen und Ereignis Handlern. Die Ereignisattribute und Schlüsselwörter können in CLR-Programmen und in systemeigenen C++-Programmen verwendet werden.

|Thema|BESCHREIBUNG|
|-----------|-----------------|
|[event_source](../windows/attributes/event-source.md)|Erstellt eine Ereignisquelle.|
|[event_receiver](../windows/attributes/event-receiver.md)|Erstellt einen Ereignisempfänger (Senke).|
|[__event](../cpp/event.md)|Deklariert ein Ereignis.|
|[__raise](../cpp/raise.md)|Hebt die Aufrufsite eines Ereignisses hervor.|
|[__hook](../cpp/hook.md)|Ordnet eine Handlermethode einem Ereignis zu.|
|[__unhook](../cpp/unhook.md)|Trennt eine Handlermethode von einem Ereignis.|

## <a name="see-also"></a>Weitere Informationen

[C++-Programmiersprachenreferenz](../cpp/cpp-language-reference.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
