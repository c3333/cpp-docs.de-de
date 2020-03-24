---
title: Compilerwarnung (Stufe 1) C4615
ms.date: 11/04/2016
f1_keywords:
- C4615
helpviewer_keywords:
- C4615
ms.assetid: 7b107c01-0da2-4e01-8b40-93813e30b94c
ms.openlocfilehash: 5d8c5ae1214b3e823bb3754e3b200a430026f1b9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185918"
---
# <a name="compiler-warning-level-1-c4615"></a>Compilerwarnung (Stufe 1) C4615

\#pragma-Warnung: Unbekannter Benutzer Warnungstyp.

Ein ungültiger Warnungs Spezifizierer wurde mit der **pragma** - [Warnung](../../preprocessor/warning.md)verwendet. Um den Fehler zu beheben, verwenden Sie einen gültigen Warnungs Spezifizierer.

Im folgenden Beispiel wird C4615 generiert:

```cpp
// C4615.cpp
// compile with: /W1 /LD
#pragma warning(enable : 4401)   // C4615, 'enable' not valid specifier

// use the code below to resolve the error
// #pragma warning(default : 4401)
```
