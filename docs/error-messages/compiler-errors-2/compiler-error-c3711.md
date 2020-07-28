---
title: Compilerfehler C3711
ms.date: 11/04/2016
f1_keywords:
- C3711
helpviewer_keywords:
- C3711
ms.assetid: 26d581cc-2153-4ee0-b814-a371184be3e1
ms.openlocfilehash: bf8d1ea745ed96d782fdc95d825e278e894066ef
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220183"
---
# <a name="compiler-error-c3711"></a>Compilerfehler C3711

"Methode": eine nicht verwaltete Ereignis Quell Methode muss "void" oder einen ganzzahligen Typ zurückgeben.

Sie haben in der Ereignis Quelle eine Methode definiert, die nicht "void" oder einen ganzzahligen Typ zurückgegeben hat. Legen Sie zum Beheben dieses Fehlers fest, dass das Ereignis und der Ereignishandler den Rückgabetyp oder einen ganzzahligen **`void`** Typ wie **`int`** oder aufweisen **`long`** .

Im folgenden Beispiel wird C3711 generiert:

```cpp
// C3711.cpp
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>

[event_source(native)]
class CEventSrc {
public:
   __event float event1();   // C3711
   // try the following line instead
   // __event int event1();
   // also change the handler, below
};

[event_receiver(native)]
class CEventRec {
public:
   float handler1() {         // change float to int
      return 0.0;             // change 0.0 to 0
   }
   void HookEvents(CEventSrc* pSrc) {
      __hook(CEventSrc::event1, pSrc, CEventRec::handler1);
   }
   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(CEventSrc::event1, pSrc, CEventRec::handler1);
   }
};

int main() {
}
```
