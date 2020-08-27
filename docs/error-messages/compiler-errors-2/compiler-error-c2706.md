---
title: Compilerfehler C2706
description: Beschreibt den Microsoft C/C++-Compilerfehler C2706.
ms.date: 08/25/2020
f1_keywords:
- C2706
helpviewer_keywords:
- C2706
ms.assetid: e18da924-c42d-4b09-8e29-f4e0382d7dc6
ms.openlocfilehash: 11e1e878f82ad59bb712155747696c0d6c6a239e
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898741"
---
# <a name="compiler-error-c2706"></a>Compilerfehler C2706

> unzulässig `__except` ohne Übereinstimmung `__try` (fehlendes '} ' in `__try` Block?)

Der Compiler hat keine schließende geschweifte Klammer für einen- **`__try`** Block gefunden.

Im folgenden Beispiel wird C2706 generiert:

```cpp
// C2706.cpp
int main() {
   __try {
      void f();
   // C2706  } missing here
   __except(GetExceptionCode() == 0x0) {
   }
}
```
