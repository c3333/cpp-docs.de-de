---
title: Compilerfehler C2019
ms.date: 11/04/2016
f1_keywords:
- C2019
helpviewer_keywords:
- C2019
ms.assetid: 4f37b1e1-9eca-418f-a4c3-141e8512d7b6
ms.openlocfilehash: 5343d6760a7a7f2c868d92790bf9930e431e3517
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757513"
---
# <a name="compiler-error-c2019"></a>Compilerfehler C2019

Präprozessordirektive erwartet, 'Zeichen' gefunden.

Das Zeichen folgte einem `#` Vorzeichen, aber es ist nicht der erste Buchstabe einer Präprozessordirektive.

Im folgenden Beispiel wird C2019 generiert:

```cpp
// C2019.cpp
#!define TRUE 1   // C2019
```

Mögliche Lösung:

```cpp
// C2019b.cpp
// compile with: /c
#define TRUE 1
```
