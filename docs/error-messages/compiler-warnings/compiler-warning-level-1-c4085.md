---
title: Compilerwarnung (Stufe 1) C4085
ms.date: 11/04/2016
f1_keywords:
- C4085
helpviewer_keywords:
- C4085
ms.assetid: 2bc6eb25-058f-4597-b351-fd69587b5170
ms.openlocfilehash: 8fc8ddc900299f372f0592b660b132188128c3d3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200199"
---
# <a name="compiler-warning-level-1-c4085"></a>Compilerwarnung (Stufe 1) C4085

Pragma-Parameter "on" oder "off" erwartet

Das Pragma erfordert einen **on** - oder **off** -Parameter. Das Pragma wird ignoriert.

Im folgenden Beispiel wird C4085 generiert:

```cpp
// C4085.cpp
// compile with: /W1 /LD
#pragma optimize( "t", maybe )  // C4085
```
