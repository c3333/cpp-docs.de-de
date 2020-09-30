---
title: Compilerfehler C3706
ms.date: 11/04/2016
f1_keywords:
- C3706
helpviewer_keywords:
- C3706
ms.assetid: d20a33eb-d625-46c5-ac87-32075a590d07
ms.openlocfilehash: 461850b2c1686343f23c77274b8fb2ca6fd9071e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508009"
---
# <a name="compiler-error-c3706"></a>Compilerfehler C3706

"Function": muss eine COM-Schnittstelle zum Auslösen von COM-Ereignissen sein.

Die Ereignis Schnittstelle, mit der com-Ereignisse ausgelöst werden, muss eine COM-Schnittstelle sein. In dieser Situation muss die Schnittstelle entweder mithilfe eines Visual C++ Attributs definiert oder mithilfe [#Import](../../preprocessor/hash-import-directive-cpp.md) aus einer Typbibliothek mit #Import embedded_idl Attribute importiert werden.

Beachten Sie, dass die `#include` Zeilen der ATL-Header Dateien, die im folgenden Beispiel angezeigt werden, für die Verwendung von COM-Ereignissen erforderlich sind. Um diesen Fehler zu beheben, erstellen Sie `IEvents` (die Ereignis Schnittstelle) eine COM-Schnittstelle, indem Sie eines der folgenden Attribute auf die Schnittstellen Definition anwenden: [Object](../../windows/attributes/object-cpp.md), [Dual](../../windows/attributes/dual.md)oder [dispinterface](../../windows/attributes/dispinterface.md).

Wenn eine Schnittstelle aus einer von "Mittel l" generierten Header Datei besteht, wird Sie vom Compiler nicht als COM-Schnittstelle erkannt.

Im folgenden Beispiel wird C3706 generiert:

```cpp
// C3706.cpp
// compile with: /c
// C3706 expected
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>

[module(dll, name="idid", uuid="12341234-1234-1234-1234-123412341234")];

// Uncomment the following line to resolve.
// [object, uuid="12341234-1234-1234-1234-123412341237"]
__interface IEvents : IUnknown {
   HRESULT event1(/*[in]*/ int i);   // uncomment [in]
};

[dual, uuid="12341234-1234-1234-1234-123412341235"]
__interface IBase {
   HRESULT fireEvents();
};

[coclass, event_source(com), uuid="12341234-1234-1234-1234-123412341236"]
class CEventSrc : public IBase {
   public:
   __event __interface IEvents;

   HRESULT fireEvents() {
      HRESULT hr = IEvents_event1(123);
      return hr;
   }
};
```
