---
title: __unhook
ms.date: 11/04/2016
f1_keywords:
- __unhook
- __unhook_cpp
helpviewer_keywords:
- event handlers [C++], dissociating events
- __unhook keyword [C++]
ms.assetid: 953a14f3-5199-459d-81e5-fcf015a19878
ms.openlocfilehash: 221ffc30a9b8a40c44f8009dfa511b72aa160e01
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337565"
---
# <a name="__unhook"></a>__unhook

Trennt eine Handlermethode von einem Ereignis.

## <a name="syntax"></a>Syntax

```cpp
long  __unhook(
   &SourceClass::EventMethod,
   source,
   &ReceiverClass::HandlerMethod
   [, receiver = this]
);
long  __unhook(
   interface,
   source
);
long  __unhook(
   source
);
```

#### <a name="parameters"></a>Parameter

**&***SourceClass* `::` *EventMethod* Ein Zeiger auf die Ereignismethode, von der aus Sie die Ereignishandlermethode aufhaken:

- Native C++-Ereignisse: *SourceClass* ist die Ereignisquellklasse und *EventMethod* das Ereignis.

- COM-Ereignisse: *SourceClass* ist die Ereignisquellschnittstelle und *EventMethod* ist eine ihrer Methoden.

- Verwaltete Ereignisse: *SourceClass* ist die Ereignisquellklasse und *EventMethod* ist das Ereignis.

*interface*<br/>
Der Schnittstellenname, der vom *Empfänger*abgehakt wird, nur für COM-Ereignisempfänger, bei denen der *layout_dependent* Parameter des [event_receiver-Attributs](../windows/attributes/event-receiver.md) **true**ist.

*Quelle*<br/>
Ein Zeiger auf eine Instanz der Ereignisquelle. Abhängig von `type` dem `event_receiver`in angegebenen Code kann *die Quelle* eine der folgenden sein:

- Ein systemeigener Ereignisquellen-Objektzeiger.

- Ein `IUnknown`-basierter Zeiger (COM-Quelle).

- Ein Zeiger des verwalteten Objekts (für verwaltete Ereignisse).

**&***ReceiverClass* `::` `HandlerMethod` A-Zeiger auf die Ereignishandlermethode, die von einem Ereignis abgehakt werden soll. Der Handler wird als Methode einer Klasse oder als Verweis auf diese angegeben. Wenn Sie den Klassennamen nicht angeben, **nimmt __unhook** an, dass die Klasse die Klasse ist, in der sie aufgerufen wird.

- Native C++-Ereignisse: *ReceiverClass* ist `HandlerMethod` die Ereignisempfängerklasse und der Handler.

- COM-Ereignisse: *ReceiverClass* ist die `HandlerMethod` Ereignisempfängerschnittstelle und einer seiner Handler.

- Verwaltete Ereignisse: *ReceiverClass* ist `HandlerMethod` die Ereignisempfängerklasse und der Handler.

*Empfänger*(optional) Ein Zeiger auf eine Instanz der Ereignisempfängerklasse. Wenn Sie keinen Empfänger angeben, ist der Standardwert die Empfängerklasse oder -struktur, in der **__unhook** aufgerufen wird.

## <a name="usage"></a>Verwendung

Kann in jedem Gültigkeitsbereich der Funktion verwendet werden, einschließlich Main, außerhalb der Ereignisempfängerklasse.

## <a name="remarks"></a>Bemerkungen

Verwenden Sie die systeminterne Funktion **__unhook** in einem Ereignisempfänger, um eine Handlermethode von einer Ereignismethode zu trennen oder zu "enthaken".

Es gibt drei Formen der **__unhook**. Sie können in den meisten Fällen das erste (four-argument) Formular verwenden. Sie können die zweite Form (zwei Argumente) der **__unhook** nur für einen COM-Ereignisempfänger verwenden. Dadurch wird die gesamte Ereignisschnittstelle abgehängt. Sie können das dritte (one-argument) Formular verwenden, um bei allen Delegaten aus der angegebenen Quelle die Bindung zu lösen.

Ein Wert ungleich null gibt an, dass ein Fehler aufgetreten ist (verwaltete Ereignisse lösen eine Ausnahme aus).

Wenn Sie **__unhook** für ein Ereignis und einen Ereignishandler aufrufen, die noch nicht hooked sind, hat dies keine Auswirkungen.

Zur Kompilierzeit überprüft der Compiler, dass das Ereignis vorhanden ist und führt eine Parametertypüberprüfung mit dem angegebenen Handler aus.

Mit Ausnahme von COM-Ereignissen können **__hook** und **__unhook** außerhalb des Ereignisempfängers aufgerufen werden.

Eine Alternative zur Verwendung **von __unhook** ist die Verwendung des Operators -=.

Informationen zum Codieren verwalteter Ereignisse in der neuen Syntax finden Sie unter [ereignis](../extensions/event-cpp-component-extensions.md).

> [!NOTE]
> Eine von einer Vorlage gebildete Klasse oder Struktur kann keine Ereignisse enthalten.

## <a name="example"></a>Beispiel

Beispiele finden Sie [unter Ereignisbehandlung in nativem C++](../cpp/event-handling-in-native-cpp.md) und [Ereignisbehandlung in COM.](../cpp/event-handling-in-com.md)

## <a name="see-also"></a>Siehe auch

[Keywords](../cpp/keywords-cpp.md)<br/>
[Event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__raise](../cpp/raise.md)
