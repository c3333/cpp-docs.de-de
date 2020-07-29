---
title: Compilerfehler C2348
ms.date: 11/04/2016
f1_keywords:
- C2348
helpviewer_keywords:
- C2348
ms.assetid: 4c4d701f-ccf1-46fe-9ddb-3f341684f269
ms.openlocfilehash: 716fdf244f19fa8f0960a0279da3c39af1546178
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218259"
---
# <a name="compiler-error-c2348"></a>Compilerfehler C2348

' Typname ': ist kein Aggregat im C-Stil, kann nicht in eingebetteter IDL exportiert werden.

Wenn Sie ein-Element **`struct`** in einer IDL-Datei mit dem [Export](../../windows/export.md) -Attribut platzieren möchten, **`struct`** darf nur Daten enthalten.

Im folgenden Beispiel wird C2348 generiert:

```cpp
// C2348.cpp
// C2348 error expected
[ module(name="SimpleMidlTest") ];

[export]
struct Point {
   // Delete the following two lines to resolve.
   Point() : m_i(0), m_j(0) {}
   Point(int i, int j) : m_i(i), m_j(j) {}

   int m_i;
   int m_j;
};
```
