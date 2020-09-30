---
title: Compilerfehler C3707
ms.date: 11/04/2016
f1_keywords:
- C3707
helpviewer_keywords:
- C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
ms.openlocfilehash: a09bf080c72e154a37cec5cdb75e714c12dd7150
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507982"
---
# <a name="compiler-error-c3707"></a>Compilerfehler C3707

"Function": die dispinterface-Methode muss eine "DISPID" aufweisen.

Wenn Sie eine `dispinterface` Methode verwenden, müssen Sie Ihr eine zuweisen `dispid` . Um diesen Fehler zu beheben, weisen `dispid` Sie der-Methode einen zu `dispinterface` , indem Sie beispielsweise das- `id` Attribut für die-Methode im folgenden Beispiel auskommentieren. Weitere Informationen finden Sie in den Attributen " [dispinterface](../../windows/attributes/dispinterface.md) " und " [ID](../../windows/attributes/id.md)".

Im folgenden Beispiel wird C3707 generiert:

```cpp
// C3707.cpp
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>

[module(name="xx")];
[dispinterface]
__interface IEvents : IDispatch
{
   HRESULT event1([in] int i);   // C3707
   // try the following line instead
   // [id(1)] HRESULT event1([in] int i);
};

int main() {
}
```
