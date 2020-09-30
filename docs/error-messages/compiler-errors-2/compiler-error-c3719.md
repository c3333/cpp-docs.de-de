---
title: Compilerfehler C3719
ms.date: 11/04/2016
f1_keywords:
- C3719
helpviewer_keywords:
- C3719
ms.assetid: d0d59d4e-babb-4480-9ef7-70cf1a28165c
ms.openlocfilehash: 9dce5fad3b38b0b0b396ff036f437af90e3e6d38
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91510089"
---
# <a name="compiler-error-c3719"></a>Compilerfehler C3719

' Schnittstelle ': eine Schnittstellen basierte Ereignis Quelle kann nur für COM-Ereignisse verwendet werden.

Sie haben eine Schnittstelle in einem nicht-COM-Kontext deklariert.

Im folgenden Beispiel wird C3719 generiert:

```cpp
// C3719a.cpp
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];

[object]
__interface I {
   HRESULT func1();
};

[event_source(native), coclass]
struct A {
   __event __interface I;   // C3719

   // try the following line instead
   // __event func2();
};

int main() {
}
```

Um diesen Fehler zu beheben, wenden Sie das [Objekt](../../windows/attributes/object-cpp.md), die [Co-Klasse](../../windows/attributes/coclass.md)-, [event_source](../../windows/attributes/event-source.md)-und [event_receiver](../../windows/attributes/event-receiver.md) Attribute entsprechend an, um die Klassen zu erstellen, in denen Sie die com-Klassen der-Schnittstelle verwenden. Beispiel:

```cpp
// C3719b.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[module(name="xx")];
[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface I {
   HRESULT f();
};

[coclass, event_source(com) , uuid("00000000-0000-0000-0000-000000000002")]
struct MyStruct {
   __event __interface I;
};

[event_receiver(com)]
struct MyStruct2 {
   void f() {
   }
   MyStruct2(I* pB) {
      __hook(&I::f, pB, &MyStruct2::f);
   }
};

int main()
{
}
```
