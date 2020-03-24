---
title: Compilerfehler C2871
ms.date: 11/04/2016
f1_keywords:
- C2871
helpviewer_keywords:
- C2871
ms.assetid: 44aeb84d-61f0-45e0-8dad-22a3cd46b7f8
ms.openlocfilehash: cc24e5fefe9ffd67dc6b01520ea32805a22f70c3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201681"
---
# <a name="compiler-error-c2871"></a>Compilerfehler C2871

"Name": ein Namespace mit diesem Namen ist nicht vorhanden.

Dieser Fehler tritt auf, wenn Sie einen Bezeichner, der kein Namespace ist, an eine [using](../../cpp/namespaces-cpp.md#using_directives) -Direktive übergeben.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2871 generiert:

```cpp
// C2871.cpp
// compile with: /c
namespace a {
   int fn(int i) { return i; }
}
namespace b {
   using namespace d;   // C2871 because d is not a namespace
   using namespace a;   // OK
}
```
