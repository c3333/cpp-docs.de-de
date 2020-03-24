---
title: Compilerwarnung (Stufe 2) C4099
ms.date: 11/04/2016
f1_keywords:
- C4099
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
ms.openlocfilehash: 97ead14dc9771dc02ad722843ec9fe1a8056e3f6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174283"
---
# <a name="compiler-warning-level-2-c4099"></a>Compilerwarnung (Stufe 2) C4099

"Bezeichner": der Typname wird zuerst mithilfe von "objecttype1" angezeigt und wird jetzt mit "objecttype2" angezeigt.

Ein-Objekt, das als-Struktur deklariert ist, wird als-Klasse definiert, oder ein Objekt, das als Klasse deklariert wird, wird als Struktur definiert. Der Compiler verwendet den Typ, der in der Definition angegeben ist.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4099 generiert.

```cpp
// C4099.cpp
// compile with: /W2 /c
struct A;
class A {};   // C4099, use different identifer or use same object type
```
