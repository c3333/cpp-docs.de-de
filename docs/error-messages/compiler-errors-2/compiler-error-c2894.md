---
title: Compilerfehler C2894
ms.date: 11/04/2016
f1_keywords:
- C2894
helpviewer_keywords:
- C2894
ms.assetid: 4e250579-2b59-4993-a6f4-49273e7ecf06
ms.openlocfilehash: 6909843539747b285a5390a66a7a323e4e9c5d00
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223459"
---
# <a name="compiler-error-c2894"></a>Compilerfehler C2894

Vorlagen können nicht als "C"-Verknüpfung deklariert werden.

Dieser Fehler kann durch eine in einem-Block definierte Vorlage verursacht werden `extern "C"` .

Im folgenden Beispiel wird C2894 generiert:

```cpp
// C2894.cpp
extern "C" {
   template<class T> class stack {};   // C2894 fail

   template<class T> void f(const T &aT) {}   // C2894
}
```

Im folgenden Beispiel wird C2894 generiert:

```cpp
// C2894b.cpp
// compile with: /c
extern "C" template<class T> void f(const T &aT) {}   // C2894

template<class T> void f2(const T &aT) {}   // OK
```
