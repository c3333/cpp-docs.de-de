---
title: Compilerfehler C3741
ms.date: 11/04/2016
f1_keywords:
- C3741
helpviewer_keywords:
- C3741
ms.assetid: ed311315-cc32-49c9-97fa-01b293d81526
ms.openlocfilehash: e551fa3dbf67d2158081bea9d19051d4703d9c43
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501305"
---
# <a name="compiler-error-c3741"></a>Compilerfehler C3741

"Class": muss eine Co-Klasse sein, wenn der Parameter "layout_dependent" von event_receiver = True ist.

Wenn `layout_dependent=true` für eine [event_receiver](../../windows/attributes/event-receiver.md) Klasse, muss die Klasse auch über das [Co-Klasse](../../windows/attributes/coclass.md) -Attribut verfügen.

Im folgenden Beispiel wird C3741 generiert.

```cpp
// C3741.cpp
// compile with: /c
// C3741 expected
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
[module(name="xx")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface I{ HRESULT f(); };

// Delete the following line to resolve.
[ event_receiver(com, layout_dependent=true)]

// class or struct must be declared with coclass
// Uncomment the following line to resolve.
// [ event_receiver(com, layout_dependent=true), coclass, uuid("00000000-0000-0000-0000-000000000002")]
struct R : I {
   HRESULT f(){ return 0; }
   R(){}
   R(I* a){ __hook(I, a); }
};
```
