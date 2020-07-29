---
title: Compilerfehler C2289
ms.date: 11/04/2016
f1_keywords:
- C2289
helpviewer_keywords:
- C2289
ms.assetid: cb41a29e-1b06-47dc-bfce-8d73bd63a0df
ms.openlocfilehash: 239552eb383197e57fcc6285cbf416c7c71c858b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216270"
---
# <a name="compiler-error-c2289"></a>Compilerfehler C2289

Der gleiche Typqualifizierer wurde mehrmals verwendet

Eine Typdeklaration oder-Definition verwendet mehrmals einen **`const`** Typqualifizierer (, **`volatile`** , **`signed`** oder **`unsigned`** ). Dies führt zu einem Fehler unter ANSI-Kompatibilität (**/Za**).

Im folgenden Beispiel wird C2286 generiert:

```cpp
// C2289.cpp
// compile with: /Za /c
volatile volatile int i;   // C2289
volatile int j;   // OK
```
