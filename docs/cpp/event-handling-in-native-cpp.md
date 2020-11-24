---
title: Ereignisbehandlung in nativem C++-Code
description: Erfahren Sie, wie Sie die Microsoft C++-Erweiterungen für die native C++-Ereignis Behandlung verwenden.
ms.date: 11/20/2020
helpviewer_keywords:
- event handling [C++]
ms.openlocfilehash: 5ad9128b7ff596674c3b08687b722c81b7a10aa8
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483177"
---
# <a name="event-handling-in-native-c"></a>Ereignisbehandlung in nativem C++-Code

In der nativen C++-Ereignis Behandlung richten Sie eine Ereignis Quelle und einen Ereignis Empfänger mithilfe der Attribute " [event_source](../windows/attributes/event-source.md) " und " [event_receiver](../windows/attributes/event-receiver.md) " ein, wobei Sie angeben `type` = `native` . Diese Attribute ermöglichen es, dass die Klassen, auf die Sie angewendet werden, Ereignisse auslösen und Ereignisse in einem nativen, nicht-COM-Kontext behandeln.

> [!NOTE]
> Ereignis Attribute in nativem C++ sind mit Standard-C++ nicht kompatibel. Sie werden nicht kompiliert, wenn Sie den [`/permissive-`](../build/reference/permissive-standards-conformance.md) Konformitäts Modus angeben.

## <a name="declaring-events"></a>Deklarieren von Ereignissen

Verwenden Sie in einer Ereignis Quell Klasse das- [`__event`](../cpp/event.md) Schlüsselwort in einer Methoden Deklaration, um die Methode als Ereignis zu deklarieren. Stellen Sie sicher, dass Sie die-Methode deklarieren, aber nicht definieren. Wenn Sie dies tun, generiert es einen Compilerfehler, da der Compiler die Methode implizit definiert, wenn Sie in einem Ereignis erstellt wird. Systemeigene Ereignisse können Methoden mit null oder mehr Parametern sein. Der Rückgabetyp kann **`void`** ein beliebiger ganzzahliger Typ sein.

## <a name="defining-event-handlers"></a>Definieren von Ereignis Handlern

In einer Ereignis Empfängerklasse definieren Sie Ereignishandler. Ereignishandler sind Methoden mit Signaturen (Rückgabe Typen, Aufruf Konventionen und Argumenten), die mit dem Ereignis übereinstimmen, das Sie behandeln.

## <a name="hooking-event-handlers-to-events"></a>Einbinden von Ereignis Handlern mit Ereignissen

Außerdem verwenden Sie in einer Ereignis Empfängerklasse die intrinsische Funktion, [`__hook`](../cpp/hook.md) um Ereignisse Ereignis Handlern zuzuordnen und [`__unhook`](../cpp/unhook.md) Ereignisse von Ereignis Handlern zu trennen. Sie können mehrere Ereignisse mit einem Ereignishandler oder mehrere Ereignishandler mit einem Ereignis verknüpfen.

## <a name="firing-events"></a>Auslösen von Ereignissen

Um ein Ereignis auszulösen, wenden Sie die Methode an, die in der Ereignis Quell Klasse als Ereignis deklariert wurde. Wenn Handler an das Ereignis geknüpft wurden, werden die Handler aufgerufen.

### <a name="native-c-event-code"></a>System eigener C++-Ereignis Code

Das folgende Beispiel zeigt, wie ein Ereignis im systemeigenen C++-Code ausgelöst wird. Informationen zum Kompilieren und Ausführen des Beispiels finden Sie in den Kommentaren im Code. Um den Code in der Visual Studio-IDE zu erstellen, vergewissern Sie sich, dass die **`/permissive-`** Option deaktiviert ist.

## <a name="example"></a>Beispiel

### <a name="code"></a>Code

```cpp
// evh_native.cpp
// compile by using: cl /EHsc /W3 evh_native.cpp
#include <stdio.h>

[event_source(native)]
class CSource {
public:
   __event void MyEvent(int nValue);
};

[event_receiver(native)]
class CReceiver {
public:
   void MyHandler1(int nValue) {
      printf_s("MyHandler1 was called with value %d.\n", nValue);
   }

   void MyHandler2(int nValue) {
      printf_s("MyHandler2 was called with value %d.\n", nValue);
   }

   void hookEvent(CSource* pSource) {
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);
   }

   void unhookEvent(CSource* pSource) {
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);
   }
};

int main() {
   CSource source;
   CReceiver receiver;

   receiver.hookEvent(&source);
   __raise source.MyEvent(123);
   receiver.unhookEvent(&source);
}
```

### <a name="output"></a>Output

```Output
MyHandler2 was called with value 123.
MyHandler1 was called with value 123.
```

## <a name="see-also"></a>Siehe auch

[Behandlung von Ereignissen](../cpp/event-handling.md)
