---
title: Compilerfehler C3386
ms.date: 11/04/2016
f1_keywords:
- C3386
helpviewer_keywords:
- C3386
ms.assetid: 93fa8c33-0f10-402b-8eec-b0a217a1f8dc
ms.openlocfilehash: efe882db447b9ebc69d02e3b10d9e484a3cfd8a8
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520447"
---
# <a name="compiler-error-c3386"></a>Compilerfehler C3386

> "*Type-Name*": `__declspec(dllexport)` / `__declspec(dllimport)` kann nicht auf einen verwalteten oder WinRT-Typ angewendet werden.

Die [`dllimport`](../../cpp/dllexport-dllimport.md) [`dllexport`](../../cpp/dllexport-dllimport.md) **`__declspec`** modifiziererer und sind für verwaltete oder Windows-Runtime Typen ungültig.

Im folgenden Beispiel wird C3386 generiert und gezeigt, wie Sie diesen Fehler beheben:

```cpp
// C3386.cpp
// compile with: /clr /c
ref class __declspec(dllimport) X1 {   // C3386
// try the following line instead
// ref class X1 {
};
```
