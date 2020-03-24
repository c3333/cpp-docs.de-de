---
title: Compilerwarnung (Stufe 1) C4683
ms.date: 08/27/2018
f1_keywords:
- C4683
helpviewer_keywords:
- C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
ms.openlocfilehash: f86cf8f6d894d6efaa1b49977634956dc1979a98
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175428"
---
# <a name="compiler-warning-level-1-c4683"></a>Compilerwarnung (Stufe 1) C4683

> '*Function*': die Ereignis Quelle hat einen ' out'-Parameter; Vorsicht beim Einbinden mehrerer Ereignishandler

## <a name="remarks"></a>Bemerkungen

Wenn mehr als eine Ereignis Senke an einer com-Ereignis Quelle lauscht, wird der Wert eines out-Parameters möglicherweise ignoriert.

Beachten Sie, dass in den folgenden Situationen ein Speichermangel auftritt:

1. Wenn eine Methode über einen intern zugewiesenen out-Parameter verfügt, z. b. ein BSTR *.

2. , Wenn das Ereignis mehr als einen Handler aufweist (ist ein Multicast-Ereignis).

Der Grund für den Austritt besteht darin, dass der Out-Parameter von mehreren Handlern festgelegt wird, aber nur durch den letzten Handler an die aufrufssite zurückgegeben wird.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4683 generiert und gezeigt, wie Sie diesen Fehler beheben:

```cpp
// C4683.cpp
// compile with: /W1 /LD
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[ module(name="xx") ];

[ object ]
__interface I {
   HRESULT f([out] int* pi);
   // try the following line instead
   // HRESULT f(int* pi);
};

[ coclass, event_source(com) ]
struct E {
   __event __interface I;   // C4683
};
```
