---
title: Compilerfehler C2021
ms.date: 11/04/2016
f1_keywords:
- C2021
helpviewer_keywords:
- C2021
ms.assetid: 064f32e2-3794-48d5-9767-991003dcb36a
ms.openlocfilehash: 97d1776bb3b29b3691ae31bb060410a83d581e2d
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743294"
---
# <a name="compiler-error-c2021"></a>Compilerfehler C2021

Exponentwert erwartet und nicht „character“.

Das Zeichen, das als Exponent einer Gleit Komma Konstante verwendet wird, ist keine gültige Zahl. Achten Sie darauf, einen Exponenten zu verwenden, der sich im Bereich befindet.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C2021 generiert:

```cpp
// C2021.cpp
float test1=1.175494351E;   // C2021
```

Mögliche Lösung:

```cpp
// C2021b.cpp
// compile with: /c
float test2=1.175494351E8;
```
