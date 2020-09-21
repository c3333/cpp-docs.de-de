---
title: Compilerfehler C2092
ms.date: 11/04/2016
f1_keywords:
- C2092
helpviewer_keywords:
- C2092
ms.assetid: 037e44ae-16c8-489a-a512-dcdf7f7795a6
ms.openlocfilehash: 8f2b83b4099308ea1d0bb127d8cea377ab65da96
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90741890"
---
# <a name="compiler-error-c2092"></a>Compilerfehler C2092

der Array Elementtyp "Array Name" kann nicht funktionsfähig sein.

Funktions Arrays sind nicht zulässig. Verwenden Sie ein Array von Zeigern auf Funktionen.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C2092 generiert:

```cpp
// C2092.cpp
typedef void (F) ();
typedef F AT[10];   // C2092
```

Mögliche Lösung:

```cpp
// C2092b.cpp
// compile with: /c
typedef void (F) ();
typedef F * AT[10];
```
