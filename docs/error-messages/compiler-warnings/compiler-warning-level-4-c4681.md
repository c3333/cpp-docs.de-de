---
title: Compilerwarnung (Stufe 4) C4681
ms.date: 11/04/2016
f1_keywords:
- C4681
helpviewer_keywords:
- C4681
ms.assetid: a4e6d85f-3e21-4b45-a551-c23d3c554d3f
ms.openlocfilehash: 97fbaf03b8c505f8d0a9e01ed7b85a6b42c25667
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91510024"
---
# <a name="compiler-warning-level-4-c4681"></a>Compilerwarnung (Stufe 4) C4681

„class“: Die Co-Klasse gibt keine Standardschnittstelle an, die eine Ereignisquelle ist.

Eine [source](../../windows/attributes/source-cpp.md) -Schnittstelle wurde für eine Klasse nicht angegeben.

Im folgenden Beispiel wird C4681 generiert:

```cpp
// C4681.cpp
// compile with: /W4 /c
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[module(name="test")];

[dual, uuid("00000000-0000-0000-0000-000000000000")]
__interface IEvent { [id(3)] HRESULT myEvent(); };

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface ISource { HRESULT Fire(); };

[ coclass,
  source(IEvent),
  default(ISource),
  // Uncomment the following line to resolve.
  // default(IEvent),
  uuid("00000000-0000-0000-0000-000000000002")
]
struct CSource : ISource {   // C4681
   HRESULT Fire() { return 0; }
};
```
