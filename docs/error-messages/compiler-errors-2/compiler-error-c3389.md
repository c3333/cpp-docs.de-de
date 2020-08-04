---
title: Compilerfehler C3389
ms.date: 11/04/2016
f1_keywords:
- C3389
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
ms.openlocfilehash: 8a040e649074e115b1b86ea56db6c9ef48f4c0d0
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520472"
---
# <a name="compiler-error-c3389"></a>Compilerfehler C3389

> __declspec (*Schlüsselwort*) kann nicht mit/CLR: pure oder/CLR: Safe verwendet werden.

## <a name="remarks"></a>Bemerkungen

Die **`/clr:pure`** **`/clr:safe`** Compileroptionen und sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 nicht unterstützt.

Ein [`__declspec`](../../cpp/declspec.md) verwendeter Modifizierer impliziert einen prozessspezifischen Zustand.  [`/clr:pure`](../../build/reference/clr-common-language-runtime-compilation.md)impliziert einen pro- [`appdomain`](../../cpp/appdomain.md) Zustand.  Daher ist das Deklarieren einer Variablen *mit dem* schlüsselworgenmodifizierer **`__declspec`** und dem Kompilieren mit **`/clr:pure`** nicht zulässig.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3389 generiert:

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```
