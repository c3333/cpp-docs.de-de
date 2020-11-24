---
title: __unhook
description: Erfahren Sie, wie Sie das Microsoft C++-Erweiterungs Schlüsselwort `__unhook` für die native Ereignis Behandlung verwenden.
ms.date: 11/04/2016
f1_keywords:
- __unhook
- __unhook_cpp
helpviewer_keywords:
- event handlers [C++], dissociating events
- __unhook keyword [C++]
ms.openlocfilehash: 74f8b814ea23c5513b7b73bf90ef59984742a266
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483320"
---
# <a name="__unhook-keyword"></a>`__unhook` Schlüsselwort

Trennt eine Handlermethode von einem Ereignis.

> [!NOTE]
> Ereignis Attribute in nativem C++ sind mit Standard-C++ nicht kompatibel. Sie werden nicht kompiliert, wenn Sie den [`/permissive-`](../build/reference/permissive-standards-conformance.md) Konformitäts Modus angeben.

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

### <a name="parameters"></a>Parameter

*`&SourceClass::EventMethod`*\
Ein Zeiger auf die Ereignismethode, von der Sie die Ereignishandlermethode lösen:

- Native C++-Ereignisse: *`SourceClass`* ist die Ereignis Quellen Klasse und *`EventMethod`* ist das-Ereignis.

- COM-Ereignisse: *`SourceClass`* ist die Ereignis Quellen Schnittstelle und *`EventMethod`* ist eine ihrer Methoden.

- Verwaltete Ereignisse: *`SourceClass`* ist die Ereignis Quellen Klasse und *`EventMethod`* ist das-Ereignis.

*`interface`*\
Der Schnittstellen Name, der aus dem *Empfänger* entfernt wird, nur für com-Ereignis Empfänger, in denen der *layout_dependent* -Parameter des [`event_receiver`](../windows/attributes/event-receiver.md) Attributs ist **`true`** .

*`source`*\
Ein Zeiger auf eine Instanz der Ereignisquelle. Abhängig von dem `type` in angegebenen Code `event_receiver` kann die *Quelle* einen der folgenden Typen aufweisen:

- Ein systemeigener Ereignisquellen-Objektzeiger.

- Ein `IUnknown` -basierter Zeiger (com-Quelle).

- Ein Zeiger des verwalteten Objekts (für verwaltete Ereignisse).

*`&ReceiverClass::HandlerMethod`* Ein Zeiger auf die Ereignishandlermethode, die von einem Ereignis entfernt werden soll. Der-Handler wird als Methode einer-Klasse oder als Verweis auf denselben angegeben. Wenn Sie den Klassennamen nicht angeben, **`__unhook`** geht davon aus, dass die Klasse die Klasse ist, in der Sie aufgerufen wird.

- Native C++-Ereignisse: *`ReceiverClass`* ist die Ereignis Empfängerklasse und `HandlerMethod` ist der Handler.

- COM-Ereignisse: *`ReceiverClass`* ist die Ereignis Empfänger Schnittstelle und *`HandlerMethod`* ist einer der zugehörigen Handler.

- Verwaltete Ereignisse: *`ReceiverClass`* ist die Ereignis Empfängerklasse und *`HandlerMethod`* ist der Handler.

*`receiver`* optionale Ein Zeiger auf eine Instanz der Ereignis Empfängerklasse. Wenn Sie keinen Empfänger angeben, ist der Standardwert die Empfängerklasse oder Struktur, in der **`__unhook`** aufgerufen wird.

## <a name="usage"></a>Verwendung

Kann in einem beliebigen Funktionsbereich verwendet werden, einschließlich `main` , außerhalb der Ereignis Empfängerklasse.

## <a name="remarks"></a>Bemerkungen

Verwenden **`__unhook`** Sie die intrinsische Funktion in einem Ereignis Empfänger, um eine Handlermethode von einer Ereignismethode zu trennen oder zu trennen.

Es gibt drei Formen von **`__unhook`** . Sie können in den meisten Fällen das erste (four-argument) Formular verwenden. Sie können das zweite Format (mit zwei Argumenten) **`__unhook`** nur für einen com-Ereignis Empfänger verwenden. es wird die gesamte Ereignis Schnittstelle entzickt. Sie können das dritte (one-argument) Formular verwenden, um bei allen Delegaten aus der angegebenen Quelle die Bindung zu lösen.

Ein Wert ungleich null gibt an, dass ein Fehler aufgetreten ist (verwaltete Ereignisse lösen eine Ausnahme aus).

Wenn Sie **`__unhook`** für ein Ereignis und einen Ereignishandler aufzurufen, die nicht bereits verknüpft sind, hat dies keine Auswirkungen.

Zur Kompilierzeit überprüft der Compiler, dass das Ereignis vorhanden ist und führt eine Parametertypüberprüfung mit dem angegebenen Handler aus.

**`__hook`** **`__unhook`** Mit Ausnahme von COM-Ereignissen können Sie und außerhalb des Ereignis Empfängers abrufen.

Eine Alternative zur Verwendung von **`__unhook`** ist die Verwendung des-=-Operators.

Informationen zum Codieren verwalteter Ereignisse in der neuen Syntax finden Sie unter [Event](../extensions/event-cpp-component-extensions.md).

> [!NOTE]
> Eine von einer Vorlage gebildete Klasse oder Struktur kann keine Ereignisse enthalten.

## <a name="example"></a>Beispiel

Beispiele finden Sie unter [Ereignis Behandlung in nativem C++](../cpp/event-handling-in-native-cpp.md) und [Ereignis Behandlung in com](../cpp/event-handling-in-com.md) .

## <a name="see-also"></a>Siehe auch

[Keywords](../cpp/keywords-cpp.md)\
[`event_source`](../windows/attributes/event-source.md)\
[`event_receiver`](../windows/attributes/event-receiver.md)\
[`__event`](../cpp/event.md)\
[`__hook`](../cpp/hook.md)\
[`__raise`](../cpp/raise.md)
