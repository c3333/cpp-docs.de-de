---
title: Compilerfehler C3484
ms.date: 11/04/2016
f1_keywords:
- C3484
helpviewer_keywords:
- C3484
ms.assetid: 2fe847fa-f6ee-4978-bc1d-b6dc6ae906ac
ms.openlocfilehash: ded4a183f69e4903afb4c9dfeae22f7751ef76ad
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686279"
---
# <a name="compiler-error-c3484"></a>Compilerfehler C3484

Vor dem Rückgabetyp wird '->' erwartet.

Sie müssen vor dem Rückgabetyp eines Lambdaausdrucks `->` bereitstellen.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Stellen Sie `->` vor dem Rückgabetyp bereit.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird der Fehler C3484 generiert:

```cpp
// C3484a.cpp

int main()
{
   return []() . int { return 42; }(); // C3484
}
```

Im folgende Beispiel wird C3484 durch Bereitstellen von `->` vor dem Rückgabetyp des Lambdaausdrucks behoben:

```cpp
// C3484b.cpp

int main()
{
   return []() -> int { return 42; }();
}
```

## <a name="see-also"></a>Siehe auch

[Lambda-Ausdrücke](../../cpp/lambda-expressions-in-cpp.md)
