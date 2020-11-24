---
title: __hook
description: Erfahren Sie, wie Sie das Microsoft C++-Erweiterungs Schlüsselwort `__hook` für die native Ereignis Behandlung verwenden.
ms.date: 11/20/2020
f1_keywords:
- __hook_cpp
- __hook
helpviewer_keywords:
- __hook keyword [C++]
- event handlers [C++], connecting events to
ms.openlocfilehash: 2a2bde221c53f0e1d420e2ab3a88eb299f6c284c
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483255"
---
# <a name="__hook-keyword"></a>`__hook` Schlüsselwort

Ordnet eine Handlermethode einem Ereignis zu.

> [!NOTE]
> Ereignis Attribute in nativem C++ sind mit Standard-C++ nicht kompatibel. Sie werden nicht kompiliert, wenn Sie den [`/permissive-`](../build/reference/permissive-standards-conformance.md) Konformitäts Modus angeben.

## <a name="syntax"></a>Syntax

```cpp
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

*`&SourceClass::EventMethod`*\
Ein Zeiger auf die Ereignismethode, an die Sie die Ereignishandlermethode binden:

- Native C++-Ereignisse: *`SourceClass`* ist die Ereignis Quellen Klasse und *`EventMethod`* ist das-Ereignis.

- COM-Ereignisse: *`SourceClass`* ist die Ereignis Quellen Schnittstelle und *`EventMethod`* ist eine ihrer Methoden.

- Verwaltete Ereignisse: *`SourceClass`* ist die Ereignis Quellen Klasse und *`EventMethod`* ist das-Ereignis.

*`interface`*\
Der Schnittstellen Name, mit dem verknüpft wird *`receiver`* , nur für com-Ereignis Empfänger, in denen der- *`layout_dependent`* Parameter des- [`event_receiver`](../windows/attributes/event-receiver.md) Attributs ist **`true`** .

*`source`*\
Ein Zeiger auf eine Instanz der Ereignisquelle. Abhängig von dem `type` in angegebenen Code `event_receiver` *`source`* kann einer der folgenden Typen sein:

- Ein systemeigener Ereignisquellen-Objektzeiger.

- Ein `IUnknown` -basierter Zeiger (com-Quelle).

- Ein Zeiger des verwalteten Objekts (für verwaltete Ereignisse).

*`&ReceiverClass::HandlerMethod`*\
Ein Zeiger, der an die Ereignishandlermethode gebunden werden soll. Der-Handler wird als Methode einer-Klasse oder als Verweis auf denselben angegeben. Wenn Sie den Klassennamen nicht angeben, **`__hook`** geht davon aus, dass die Klasse die Klasse ist, von der Sie aufgerufen wird.

- Native C++-Ereignisse: *`ReceiverClass`* ist die Ereignis Empfängerklasse und `HandlerMethod` ist der Handler.

- COM-Ereignisse: *`ReceiverClass`* ist die Ereignis Empfänger Schnittstelle und *`HandlerMethod`* ist einer der zugehörigen Handler.

- Verwaltete Ereignisse: *`ReceiverClass`* ist die Ereignis Empfängerklasse und *`HandlerMethod`* ist der Handler.

*`receiver`*\
Optionale Ein Zeiger auf eine Instanz der Ereignis Empfängerklasse. Wenn Sie keinen Empfänger angeben, ist der Standardwert die Empfängerklasse oder Struktur, in der **`__hook`** aufgerufen wird.

## <a name="usage"></a>Verwendung

Kann in jedem Gültigkeitsbereich der Funktion verwendet werden, einschließlich Main, außerhalb der Ereignisempfängerklasse.

## <a name="remarks"></a>Bemerkungen

Verwenden **`__hook`** Sie die intrinsische Funktion in einem Ereignis Empfänger, um eine Handlermethode einer Ereignismethode zuzuordnen oder zu verknüpfen. Der angegebene Handler wird aufgerufen, wenn die Quelle das angegebene Ereignis auslöst. Sie können mehrere Handler an ein einzelnes Ereignis binden oder mehrere Ereignisse an einen einzigen Handler.

Es gibt zwei Formen von **`__hook`** . Sie können das erste Formular (vier Argumente) in den meisten Fällen verwenden, insbesondere für com-Ereignis Empfänger, in denen der *layout_dependent* -Parameter des- [`event_receiver`](../windows/attributes/event-receiver.md) Attributs ist **`false`** .

In diesen Fällen müssen Sie nicht alle Methoden in einer Schnittstelle verbinden, bevor Sie ein Ereignis für eine der Methoden auslösen. Sie müssen die Methode, die das Ereignis behandelt, nur mit einem Hook verbinden. Sie können die zweite Form von (zwei-Argument) **`__hook`** nur für einen com-Ereignis Empfänger verwenden, in dem *`layout_dependent`* **`= true`** .

**`__hook`** Gibt einen Long-Wert zurück. Ein Wert ungleich null gibt an, dass ein Fehler aufgetreten ist (verwaltete Ereignisse lösen eine Ausnahme aus).

Der Compiler überprüft, ob ein Ereignis vorhanden ist und ob die Ereignissignatur der Delegatsignatur entspricht.

**`__hook`** **`__unhook`** Mit Ausnahme von COM-Ereignissen können Sie und außerhalb des Ereignis Empfängers abrufen.

Eine Alternative zur Verwendung von **`__hook`** ist die Verwendung des + =-Operators.

Informationen zum Codieren verwalteter Ereignisse in der neuen Syntax finden Sie unter [`event`](../extensions/event-cpp-component-extensions.md) .

> [!NOTE]
> Eine von einer Vorlage gebildete Klasse oder Struktur kann keine Ereignisse enthalten.

## <a name="example"></a>Beispiel

Beispiele finden Sie unter [Ereignis Behandlung in nativem C++](../cpp/event-handling-in-native-cpp.md) und [Ereignis Behandlung in com](../cpp/event-handling-in-com.md) .

## <a name="see-also"></a>Siehe auch

[Keywords](../cpp/keywords-cpp.md)\
[Ereignis Behandlung](../cpp/event-handling.md)\
[`event_source`](../windows/attributes/event-source.md)\
[`event_receiver`](../windows/attributes/event-receiver.md)\
[`__event`](../cpp/event.md)\
[`__unhook`](../cpp/unhook.md)\
[`__raise`](../cpp/raise.md)
