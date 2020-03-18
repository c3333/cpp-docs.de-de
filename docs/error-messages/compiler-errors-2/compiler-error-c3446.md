---
title: Compilerfehler C3446
ms.date: 07/21/2017
f1_keywords:
- C3446
helpviewer_keywords:
- C3446
ms.assetid: 33064548-24e4-46f1-beb1-476e3c3b3fbf
ms.openlocfilehash: 0f9ebd274a90dffe00b0e8375cc374acf46e7a08
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447119"
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

