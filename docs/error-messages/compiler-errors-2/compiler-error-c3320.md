---
title: Compilerfehler C3320
ms.date: 11/04/2016
f1_keywords:
- C3320
helpviewer_keywords:
- C3320
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
ms.openlocfilehash: 0289d49ebbb0e30153beb6b0b2bc758bff5ef118
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201304"
---
# <a name="compiler-error-c3320"></a>Compilerfehler C3320

'Typ': Typ kann nicht den gleichen Namen besitzen wie die name-Moduleigenschaft.

Ein exportierter benutzerdefinierter Typ (User-Defined Type, UDT), der eine Struktur, Klasse, Enumeration oder Union sein kann, kann nicht den gleichen Namen wie der Parameter aufweisen, der an die Name-Eigenschaft des [Modul](../../windows/module-cpp.md) Attributs übergeben wird.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3320 generiert:

```cpp
// C3320.cpp
#include "unknwn.h"
[module(name="xx")];

[export] struct xx {   // C3320
// Try the following line instead
// [export] struct yy {
   int i;
};
```
