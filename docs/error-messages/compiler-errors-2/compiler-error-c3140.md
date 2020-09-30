---
title: Compilerfehler C3140
ms.date: 11/04/2016
f1_keywords:
- C3140
helpviewer_keywords:
- C3140
ms.assetid: 122f8943-fac3-4db8-a3a8-2c5d19233de6
ms.openlocfilehash: 672930d8c1d864c8ee5c2a08daca663bd29df167
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506155"
---
# <a name="compiler-error-c3140"></a>Compilerfehler C3140

Es können nicht mehrere "Module"-Attribute in derselben Kompilierungseinheit vorhanden sein.

Das [Modul](../../windows/attributes/module-cpp.md) Attribut kann nur einmal pro Projekt definiert werden.

Im folgenden Beispiel wird C3140 generiert:

```cpp
// C3140.cpp
// compile with: /c
[emitidl];
[module(name = "MyLibrary")];
[module(name = "MyLibrary2")];   // C3140
```
