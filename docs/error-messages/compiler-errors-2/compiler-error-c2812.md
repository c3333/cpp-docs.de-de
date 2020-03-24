---
title: Compilerfehler C2812
ms.date: 11/04/2016
f1_keywords:
- C2812
helpviewer_keywords:
- C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
ms.openlocfilehash: cec92982646c64e6c5b669df328e4836d4f44df8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202099"
---
# <a name="compiler-error-c2812"></a>Compilerfehler C2812

> \#Import wird mit/CLR: pure und/CLR: Safe nicht unterstützt.

## <a name="remarks"></a>Bemerkungen

Die Compileroptionen **/clr: pure** und **/clr: Safe** sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 nicht unterstützt.

[#Import-Direktive](../../preprocessor/hash-import-directive-cpp.md) wird bei **/clr: pure** und **/clr: Safe** nicht unterstützt, da `#import` die Verwendung von systemeigenen compilerunterstützungs-Bibliotheken erfordert.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2812 generiert.

```cpp
// C2812.cpp
// compile with: /clr:pure /c
#import "importlib.tlb"   // C2812
```
