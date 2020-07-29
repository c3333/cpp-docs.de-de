---
title: Compilerfehler C3389
ms.date: 11/04/2016
f1_keywords:
- C3389
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
ms.openlocfilehash: 823b28deae3e3cfc18cdad8d37007bf8e8cff494
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221054"
---
# <a name="compiler-error-c3389"></a>Compilerfehler C3389

> __declspec (*Schlüsselwort*) kann nicht mit/CLR: pure oder/CLR: Safe verwendet werden.

## <a name="remarks"></a>Bemerkungen

Die Compileroptionen **/clr: pure** und **/clr: Safe** sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 nicht unterstützt.

Ein [__declspec](../../cpp/declspec.md) Modifizierer, der verwendet wird, impliziert einen Prozess pro Prozess.  [/clr: pure](../../build/reference/clr-common-language-runtime-compilation.md) impliziert einen pro [AppDomain](../../cpp/appdomain.md) -Zustand.  Daher ist das Deklarieren einer Variablen mit dem `keyword` **`__declspec`** Modifizierer und dem Kompilieren mit **/clr: pure** nicht zulässig.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3389 generiert:

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```
