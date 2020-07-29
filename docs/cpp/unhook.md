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
ms.openlocfilehash: 84df5ad0ff27e6b09134b0f92f14f8e9b6fdc817
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233573"
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

**&***SourceClass* `::` *EventMethod* Ein Zeiger auf die Ereignismethode, von der aus die Ereignishandlermethode entfernt wird:

- Native C++-Ereignisse: *SourceClass* ist die Ereignis Quellen Klasse, und *EventMethod* ist das Ereignis.

- COM-Ereignisse: *SourceClass* ist die Ereignis Quellen Schnittstelle, und *EventMethod* ist eine ihrer Methoden.

- Verwaltete Ereignisse: *SourceClass* ist die Ereignis Quellen Klasse, und *EventMethod* ist das Ereignis.

*interface*<br/>
Der Schnittstellen Name, der aus dem *Empfänger*entfernt wird, nur für com-Ereignis Empfänger, in denen der *layout_dependent* -Parameter des [event_receiver](../windows/attributes/event-receiver.md) Attributs ist **`true`** .

*source*<br/>
Ein Zeiger auf eine Instanz der Ereignisquelle. Abhängig von dem `type` in angegebenen Code `event_receiver` kann die *Quelle* eine der folgenden sein:

- Ein systemeigener Ereignisquellen-Objektzeiger.

- Ein `IUnknown` -basierter Zeiger (com-Quelle).

- Ein Zeiger des verwalteten Objekts (für verwaltete Ereignisse).

**&***ReceiverClass* `::` `HandlerMethod`Ein Zeiger auf die Ereignishandlermethode, die von einem Ereignis entfernt werden soll. Der-Handler wird als Methode einer-Klasse oder als Verweis auf denselben angegeben. Wenn Sie den Klassennamen nicht angeben, **`__unhook`** geht davon aus, dass es sich bei der Klasse um den Namen handelt, in dem Sie aufgerufen wird.

- Native C++-Ereignisse: *ReceiverClass* ist die Ereignis Empfängerklasse und `HandlerMethod` ist der Handler.

- COM-Ereignisse: *ReceiverClass* ist die Ereignis Empfänger Schnittstelle und `HandlerMethod` ist einer der zugehörigen Handler.

- Verwaltete Ereignisse: *ReceiverClass* ist die Ereignis Empfängerklasse und `HandlerMethod` ist der Handler.

*Receiver*(optional) ein Zeiger auf eine Instanz der Ereignis Empfängerklasse. Wenn Sie keinen Empfänger angeben, ist der Standardwert die Empfängerklasse oder Struktur, in der **`__unhook`** aufgerufen wird.

## <a name="usage"></a>Verwendung

Kann in jedem Gültigkeitsbereich der Funktion verwendet werden, einschließlich Main, außerhalb der Ereignisempfängerklasse.

## <a name="remarks"></a>Bemerkungen

Verwenden **`__unhook`** Sie die intrinsische Funktion in einem Ereignis Empfänger, um eine Handlermethode von einer Ereignismethode zu trennen oder zu lösen.

Es gibt drei Formen von **`__unhook`** . Sie können in den meisten Fällen das erste (four-argument) Formular verwenden. Sie können die zweite Form von (mit zwei Argumenten) **`__unhook`** nur für einen com-Ereignis Empfänger verwenden. Dadurch wird die gesamte Ereignis Schnittstelle nicht mehr angezeigt. Sie können das dritte (one-argument) Formular verwenden, um bei allen Delegaten aus der angegebenen Quelle die Bindung zu lösen.

Ein Wert ungleich null gibt an, dass ein Fehler aufgetreten ist (verwaltete Ereignisse lösen eine Ausnahme aus).

Wenn Sie **`__unhook`** für ein Ereignis und einen Ereignishandler aufzurufen, die nicht bereits verknüpft sind, hat dies keine Auswirkungen.

Zur Kompilierzeit überprüft der Compiler, dass das Ereignis vorhanden ist und führt eine Parametertypüberprüfung mit dem angegebenen Handler aus.

Mit Ausnahme von com **`__hook`** -Ereignissen können und **`__unhook`** außerhalb des Ereignis Empfängers aufgerufen werden.

Eine Alternative zur Verwendung von **`__unhook`** ist die Verwendung des-=-Operators.

Informationen zum Codieren verwalteter Ereignisse in der neuen Syntax finden Sie unter [Event](../extensions/event-cpp-component-extensions.md).

> [!NOTE]
> Eine von einer Vorlage gebildete Klasse oder Struktur kann keine Ereignisse enthalten.

## <a name="example"></a>Beispiel

Beispiele finden Sie unter [Ereignis Behandlung in nativem C++](../cpp/event-handling-in-native-cpp.md) und [Ereignis Behandlung in com](../cpp/event-handling-in-com.md) .

## <a name="see-also"></a>Siehe auch

[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__raise](../cpp/raise.md)
