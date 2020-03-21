---
title: Compilerfehler C3446
ms.date: 07/21/2017
f1_keywords:
- C3446
helpviewer_keywords:
- C3446
ms.assetid: 33064548-24e4-46f1-beb1-476e3c3b3fbf
ms.openlocfilehash: 2e1e474b27fec6c1625136e526add0935e309746
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075021"
---
# <a name="compiler-error-c3446"></a>Compilerfehler C3446

>"*Klasse*": ein Standardmember-Initialisierer ist für einen Member einer Wert Klasse nicht zulässig.

In Visual Studio 2015 und früher, ließ der Compiler einen Standardmember-Initialisierer für einen Member einer Wertklasse zu, ignorierte diesen aber. Standardinitialisierung einer Wertklasse initialisiert die Elemente immer auf null; ein Standardkonstruktor ist nicht zulässig. In Visual Studio 2017 lösen Standardmember-Initialisierer einen Compilerfehler aus, wie im folgenden Beispiel gezeigt:

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3446 in Visual Studio 2017 und höher generiert:

```cpp
// C3446.cpp
value struct V
{
       int i = 0; // error C3446: 'V::i': a default member initializer
                  // is not allowed for a member of a value class
       int j {0}; // C3446
};
```

Entfernen Sie den Initialisierer, um den Fehler zu beheben:

```cpp
// C3446b.cpp
value struct V
{
       int i;
       int j;
};
```
