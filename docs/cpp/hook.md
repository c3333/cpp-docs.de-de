---
title: __hook
ms.date: 11/04/2016
f1_keywords:
- __hook_cpp
helpviewer_keywords:
- __hook keyword [C++]
- event handlers [C++], connecting events to
ms.assetid: f4cabb10-d293-4c0e-a1d2-4745ef9cc22c
ms.openlocfilehash: 5a0eaf0a3bc0617dbcd1f43805af8a95291e7e47
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87188166"
---
# <a name="__hook"></a>__hook

Ordnet eine Handlermethode einem Ereignis zu.

## <a name="syntax"></a>Syntax

```
long __hook(
    &SourceClass::EventMethod,
    source,
    &ReceiverClass::HandlerMethod
    [, receiver = this]
);
long __hook(
    interface,
    source
);
```

### <a name="parameters"></a>Parameter

*&SourceClass:: EventMethod*<br/>
Ein Zeiger auf die Ereignismethode, an die Sie die Ereignishandlermethode binden:

- Native C++-Ereignisse: *SourceClass* ist die Ereignis Quellen Klasse, und *EventMethod* ist das Ereignis.

- COM-Ereignisse: *SourceClass* ist die Ereignis Quellen Schnittstelle, und *EventMethod* ist eine ihrer Methoden.

- Verwaltete Ereignisse: *SourceClass* ist die Ereignis Quellen Klasse, und *EventMethod* ist das Ereignis.

*interface*<br/>
Der Schnittstellen Name, der mit dem *Empfänger*verknüpft wird, nur für com-Ereignis Empfänger, in denen der *layout_dependent* -Parameter des [event_receiver](../windows/attributes/event-receiver.md) Attributs ist **`true`** .

*source*<br/>
Ein Zeiger auf eine Instanz der Ereignisquelle. Abhängig von dem `type` in angegebenen Code `event_receiver` kann die *Quelle* eine der folgenden sein:

- Ein systemeigener Ereignisquellen-Objektzeiger.

- Ein `IUnknown` -basierter Zeiger (com-Quelle).

- Ein Zeiger des verwalteten Objekts (für verwaltete Ereignisse).

*&ReceiverClass:: HandlerMethod*<br/>
Ein Zeiger, der an die Ereignishandlermethode gebunden werden soll. Der-Handler wird als Methode einer-Klasse oder als Verweis auf denselben angegeben. Wenn Sie den Klassennamen nicht angeben, **`__hook`** geht davon aus, dass es sich bei der Klasse um den Namen handelt, in dem Sie aufgerufen wird.

- Native C++-Ereignisse: *ReceiverClass* ist die Ereignis Empfängerklasse und `HandlerMethod` ist der Handler.

- COM-Ereignisse: *ReceiverClass* ist die Ereignis Empfänger Schnittstelle und `HandlerMethod` ist einer der zugehörigen Handler.

- Verwaltete Ereignisse: *ReceiverClass* ist die Ereignis Empfängerklasse und `HandlerMethod` ist der Handler.

*än*<br/>
Optionale Ein Zeiger auf eine Instanz der Ereignis Empfängerklasse. Wenn Sie keinen Empfänger angeben, ist der Standardwert die Empfängerklasse oder Struktur, in der **`__hook`** aufgerufen wird.

## <a name="usage"></a>Verbrauch

Kann in jedem Gültigkeitsbereich der Funktion verwendet werden, einschließlich Main, außerhalb der Ereignisempfängerklasse.

## <a name="remarks"></a>Bemerkungen

Verwenden **`__hook`** Sie die intrinsische Funktion in einem Ereignis Empfänger, um eine Handlermethode einer Ereignismethode zuzuordnen oder zu verknüpfen. Der angegebene Handler wird aufgerufen, wenn die Quelle das angegebene Ereignis auslöst. Sie können mehrere Handler an ein einzelnes Ereignis binden oder mehrere Ereignisse an einen einzigen Handler.

Es gibt zwei Formen von **`__hook`** . Sie können das erste Formular (vier Argumente) in den meisten Fällen verwenden, insbesondere für com-Ereignis Empfänger, in denen der *layout_dependent* -Parameter des [event_receiver](../windows/attributes/event-receiver.md) Attributs ist **`false`** .

In diesen Fällen müssen Sie nicht alle Methoden an eine Schnittstelle binden, bevor nicht bei einer der Methoden ein Ereignis ausgelöst wird; nur die Methode für die Ereignisbehandlung muss eingebunden werden. Sie können die zweite Form von (mit zwei Argumenten) **`__hook`** nur für einen com-Ereignis Empfänger verwenden, in dem *layout_dependent* **= true**ist.

**`__hook`** Gibt einen Long-Wert zurück. Ein Wert ungleich null gibt an, dass ein Fehler aufgetreten ist (verwaltete Ereignisse lösen eine Ausnahme aus).

Der Compiler überprüft, ob ein Ereignis vorhanden ist und ob die Ereignissignatur der Delegatsignatur entspricht.

Mit Ausnahme von com **`__hook`** -Ereignissen können und **`__unhook`** außerhalb des Ereignis Empfängers aufgerufen werden.

Eine Alternative zur Verwendung von **`__hook`** ist die Verwendung des + =-Operators.

Informationen zum Codieren verwalteter Ereignisse in der neuen Syntax finden Sie unter [Event](../extensions/event-cpp-component-extensions.md).

> [!NOTE]
> Eine von einer Vorlage gebildete Klasse oder Struktur kann keine Ereignisse enthalten.

## <a name="example"></a>Beispiel

Beispiele finden Sie unter [Ereignis Behandlung in nativem C++](../cpp/event-handling-in-native-cpp.md) und [Ereignis Behandlung in com](../cpp/event-handling-in-com.md) .

## <a name="see-also"></a>Weitere Informationen

[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[Ereignis Behandlung](../cpp/event-handling.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__unhook](../cpp/unhook.md)<br/>
[__raise](../cpp/raise.md)<br/>
