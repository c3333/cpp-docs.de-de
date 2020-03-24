---
title: Compilerfehler C3813
ms.date: 11/04/2016
f1_keywords:
- C3813
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
ms.openlocfilehash: c16ce501e25040a7ac7672a9ea131b4fe89570f5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165612"
---
# <a name="compiler-error-c3813"></a>Compilerfehler C3813

eine Eigenschaftendeklaration kann nur in der Definition eines verwalteten oder WinRT-Typs auftreten.

Eine [Eigenschaft](../../dotnet/how-to-use-properties-in-cpp-cli.md) kann nur innerhalb eines verwalteten oder Windows-Runtime Typs deklariert werden. Systemeigene Typen unterstützen das `property`-Schlüsselwort nicht.

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
