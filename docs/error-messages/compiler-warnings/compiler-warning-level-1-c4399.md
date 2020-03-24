---
title: Compilerwarnung (Stufe 1) C4399
ms.date: 11/04/2016
f1_keywords:
- C4399
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
ms.openlocfilehash: a556fbffad41d04b3eb0ea1acfd5e8739ddd5b68
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186802"
---
# <a name="compiler-warning-level-1-c4399"></a>Compilerwarnung (Stufe 1) C4399

> '*Symbol*': ein prozessbezogenes Symbol sollte bei der Kompilierung mit/CLR: pure nicht mit __declspec (dllimport) markiert werden.

## <a name="remarks"></a>Bemerkungen

Die **/clr: pure** -Compileroption ist in Visual Studio 2015 veraltet und wird in Visual Studio 2017 nicht unterstützt.

Daten aus einem systemeigenen Image oder einem Image mit nativem und CLR-Konstrukten können nicht in ein reines Image importiert werden. Um diese Warnung zu beheben, kompilieren Sie mit **/CLR** (nicht **/clr: pure**) oder DELETE `__declspec(dllimport)`.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4399 generiert.

```cpp
// C4399.cpp
// compile with: /clr:pure /doc /W1 /c
__declspec(dllimport) __declspec(process) extern const int i;   // C4399
```
