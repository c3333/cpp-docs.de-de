---
title: Compilerfehler C3739
ms.date: 11/04/2016
f1_keywords:
- C3739
helpviewer_keywords:
- C3739
ms.assetid: acffe894-08b8-4bf2-9249-9501e6e2bad3
ms.openlocfilehash: 7235d86ed00663b81aaddb87fdeae957c0f73053
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500429"
---
# <a name="compiler-error-c3739"></a>Compilerfehler C3739

"Class": die Syntax wird nur unterstützt, wenn der Parameter "layout_dependent" event_receiver "true" ist.

Sie haben versucht, eine gesamte Schnittstelle von Ereignissen zu verbinden, aber wenn `layout_dependent` [event_receiver](../../windows/attributes/event-receiver.md) Attribut nicht true ist, müssen Sie ein einzelnes Ereignis gleichzeitig verbinden.

Im folgenden Beispiel wird C3739 generiert:

```cpp
// C3739.cpp
struct A
{
   __event void e();
};

// event_receiver is implied
// [ event_receiver(layout_dependent=false)]

// use the following line instead
// [event_receiver(com, layout_dependent=true), coclass ]
struct B
{
   void f();
   B(A* a)
   {
      __hook(A, a, &B::f);   // C3739
      // use the following line instead to hook a single event
      // __hook(&A::e, a, &B::f);
   }
};

int main()
{
}
```
