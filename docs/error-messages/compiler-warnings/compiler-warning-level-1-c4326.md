---
title: Compilerwarnung (Stufe 1) C4326
ms.date: 08/27/2018
f1_keywords:
- C4326
helpviewer_keywords:
- C4326
ms.assetid: d44d2c4e-9456-42d3-b35b-4ba4b2d42ec7
ms.openlocfilehash: 32bcd85b1cd1bb6c89678daae02f4f31a9318b6d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162971"
---
# <a name="compiler-warning-level-1-c4326"></a>Compilerwarnung (Stufe 1) C4326

> der Rückgabetyp von "*Function*" sollte "*Typ1*" anstelle von "*Typ2*" lauten.

## <a name="remarks"></a>Bemerkungen

Eine Funktion hat einen anderen Typ als *Typ1*zurückgegeben. Bei Verwendung von [/Za](../../build/reference/za-ze-disable-language-extensions.md)hat **Main** z. b. keinen **int**-Wert zurückgegeben.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4326 generiert und gezeigt, wie Sie diesen Fehler beheben:

```cpp
// C4326.cpp
// compile with: /Za /W1
char main()
{
    // C4326, instead use int main()
}
```
