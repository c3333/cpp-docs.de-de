---
title: Compilerfehler C3495
ms.date: 11/04/2016
f1_keywords:
- C3495
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
ms.openlocfilehash: a67d4d859e3a9dd2241f14a476492df0fd3e6b8d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223420"
---
# <a name="compiler-error-c3495"></a>Compilerfehler C3495

'var': Eine Lambdaerfassung muss eine automatische Speicherdauer aufweisen.

Sie können keine Variable erfassen, die keine automatische Speicherdauer hat, z. b. eine Variable, die als oder gekennzeichnet ist **`static`** **`extern`** .

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Übergeben Sie keine- **`static`** oder- **`extern`** Variable an die Erfassungs Liste des Lambda Ausdrucks.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3495 generiert, da die **`static`** Variable `n` in der Erfassungs Liste eines Lambda-Ausdrucks angezeigt wird:

```cpp
// C3495.cpp

int main()
{
   static int n = 66;
   [&n]() { return n; }(); // C3495
}
```

## <a name="see-also"></a>Siehe auch

[Lambda-Ausdrücke](../../cpp/lambda-expressions-in-cpp.md)
