---
title: Compilerfehler C3386
ms.date: 11/04/2016
f1_keywords:
- C3386
helpviewer_keywords:
- C3386
ms.assetid: 93fa8c33-0f10-402b-8eec-b0a217a1f8dc
ms.openlocfilehash: 0cb6235f1b6bc868655cc6a6ba301be1308402cd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221080"
---
# <a name="compiler-error-c3386"></a>Compilerfehler C3386

"Typ": __declspec (dllexport)/ \_ _declspec (dllimport) kann nicht auf einen verwalteten oder winrttype angewendet werden.

Die `dllimport` -und [dllexport](../../cpp/dllexport-dllimport.md) **`__declspec`** c ' * *-Modifizierer sind für einen verwalteten oder Windows-Runtime-Typ ungültig.

Im folgenden Beispiel wird C3386 generiert und gezeigt, wie Sie diesen Fehler beheben:

```cpp
// C3386.cpp
// compile with: /clr /c
ref class __declspec(dllimport) X1 {   // C3386
// try the following line instead
// ref class X1 {
};
```
