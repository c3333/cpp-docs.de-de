---
title: Compilerfehler C2507
ms.date: 11/04/2016
f1_keywords:
- C2507
helpviewer_keywords:
- C2507
ms.assetid: f102aff5-de7d-4c3f-9cac-2ddf9ce02b14
ms.openlocfilehash: 944eaeadb038e6466d65859f72900db164cfe34d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221158"
---
# <a name="compiler-error-c2507"></a>Compilerfehler C2507

' Identifier ': zu viele virtuelle Modifizierer für die Basisklasse.

Eine Klasse oder Struktur ist mehrmals deklariert **`virtual`** . Nur ein **`virtual`** Modifizierer kann für jede Klasse in einer Liste von Basisklassen angezeigt werden.

Im folgenden Beispiel wird C2507 generiert:

```cpp
// C2507.cpp
// compile with: /c
class A {};
class B : virtual virtual public A {};   // C2507
class C : virtual public A {};   // OK
```
