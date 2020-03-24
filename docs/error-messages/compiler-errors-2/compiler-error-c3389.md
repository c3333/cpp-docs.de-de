---
title: Compilerfehler C3389
ms.date: 11/04/2016
f1_keywords:
- C3389
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
ms.openlocfilehash: b166096390169939f01bcb976a57612f10f7df2e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201135"
---
# <a name="compiler-error-c3389"></a>Compilerfehler C3389

> __declspec (*Schlüsselwort*) kann nicht mit/CLR: pure oder/CLR: Safe verwendet werden.

## <a name="remarks"></a>Bemerkungen

Die Compileroptionen **/clr: pure** und **/clr: Safe** sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 nicht unterstützt.

Ein [__declspec](../../cpp/declspec.md) Modifizierer, der verwendet wird, impliziert einen Prozess pro Prozess.  [/clr: pure](../../build/reference/clr-common-language-runtime-compilation.md) impliziert einen pro [AppDomain](../../cpp/appdomain.md) -Zustand.  Daher ist das Deklarieren einer Variablen mit dem `keyword` **__declspec** Modifizierers und der Kompilierung mit **/clr: pure** nicht zulässig.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3389 generiert:

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```
