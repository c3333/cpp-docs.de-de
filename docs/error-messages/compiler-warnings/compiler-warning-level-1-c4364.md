---
title: Compilerwarnung (Stufe 1) C4364
ms.date: 11/04/2016
f1_keywords:
- C4364
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
ms.openlocfilehash: 79c8809b4de9d6853aaacec4283bf01d0e89305e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187101"
---
# <a name="compiler-warning-level-1-c4364"></a>Compilerwarnung (Stufe 1) C4364

\#mithilfe von für die Assembly "file", die zuvor am Speicherort (line_number) ohne As_friend-Attribut aufgetreten ist. as_friend nicht angewendet

Eine `#using`-Direktive wurde für eine angegebene Metadatendatei wiederholt, aber der `as_friend` Qualifizierer wurde beim ersten Vorkommen nicht verwendet. der Compiler ignoriert die zweite `as_friend`.

Weitere Informationen finden Sie unter Friend-Assemblys [(C++)](../../dotnet/friend-assemblies-cpp.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird eine Komponente erstellt:

```cpp
// C4364.cpp
// compile with: /clr /LD
ref class A {};
```

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4364 generiert.

```cpp
// C4364_b.cpp
// compile with: /clr /W1 /c
#using " C4364.dll"
#using " C4364.dll" as_friend   // C4364
```
