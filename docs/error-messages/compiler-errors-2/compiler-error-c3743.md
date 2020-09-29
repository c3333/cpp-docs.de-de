---
title: Compilerfehler C3743
ms.date: 11/04/2016
f1_keywords:
- C3743
helpviewer_keywords:
- C3743
ms.assetid: 7ca9a76e-7b60-46d1-ab8b-18600cf1a306
ms.openlocfilehash: b4bb198ae883e53e7947ce7f123bb0d3f092aaf3
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500404"
---
# <a name="compiler-error-c3743"></a>Compilerfehler C3743

eine gesamte Schnittstelle kann nur ein Hook/unhook erhalten werden, wenn der Parameter "layout_dependent" event_receiver "true" ist.

Die [__unhook](../../cpp/unhook.md) -Funktion variiert in Abhängigkeit von der Anzahl der Parameter, die Sie auf Grundlage des Werts annimmt, der an den- `layout_dependent` Parameter in der [event_receiver](../../windows/attributes/event-receiver.md) -Klasse übergeben wird.

Im folgenden Beispiel wird C3743 generiert:

```cpp
// C3743.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
[module(name="xx")];
[object] __interface I { HRESULT f(); };

[event_receiver(com, layout_dependent=true), coclass]
struct R : I {
        HRESULT f() {
      return 0;
   }
        R() {
   }

   R(I* a) {
      __hook(I, a, &R::f);   // C3743
      // The following line resolves the error.
      // __hook(I, a);
   }
};
```
