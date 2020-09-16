---
title: Compilerwarnung (Stufe 1) C4364
ms.date: 11/04/2016
f1_keywords:
- C4364
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
ms.openlocfilehash: 7f1c71cb3cd6a99d4ed9960032813e7cebca7591
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685078"
---
# <a name="compiler-warning-level-1-c4364"></a>Compilerwarnung (Stufe 1) C4364

\#Verwendung von für die Assembly "file", die zuvor am Speicherort (line_number) ohne As_friend-Attribut aufgetreten ist. as_friend nicht angewendet

Eine- `#using` Direktive wurde für eine angegebene Metadatendatei wiederholt, aber der **`as_friend`** Qualifizierer wurde beim ersten Vorkommen nicht verwendet. der Compiler ignoriert den zweiten **`as_friend`** .

Weitere Informationen finden Sie unter Friend-Assemblys [(C++)](../../dotnet/friend-assemblies-cpp.md).

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird eine Komponente erstellt.

```cpp
// C4364.cpp
// compile with: /clr /LD
ref class A {};
```

Im folgenden Beispiel wird C4364 generiert.

```cpp
// C4364_b.cpp
// compile with: /clr /W1 /c
#using " C4364.dll"
#using " C4364.dll" as_friend   // C4364
```
