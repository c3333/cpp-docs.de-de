---
title: Compilerfehler C3813
ms.date: 11/04/2016
f1_keywords:
- C3813
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
ms.openlocfilehash: 88aca16363af22a6671832264889b1a26e43d460
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223368"
---
# <a name="compiler-error-c3813"></a>Compilerfehler C3813

eine Eigenschaftendeklaration kann nur in der Definition eines verwalteten oder WinRT-Typs auftreten.

Eine [Eigenschaft](../../dotnet/how-to-use-properties-in-cpp-cli.md) kann nur innerhalb eines verwalteten oder Windows-Runtime Typs deklariert werden. Native Typen unterstützen das- **`property`** Schlüsselwort nicht.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3813 generiert und gezeigt, wie Sie diesen Fehler beheben:

```cpp
// C3813.cpp
// compile by using: cl /c /clr C3813.cpp
class A
{
   property int Int; // C3813
};

ref class B
{
   property int Int; // OK - declared within managed type
};
```
