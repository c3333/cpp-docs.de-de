---
title: Compilerwarnung (Stufe 1) C4612
ms.date: 08/27/2018
f1_keywords:
- C4612
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
ms.openlocfilehash: f9478caef9eaba9c72dc282179100daf2d94c6d5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185983"
---
# <a name="compiler-warning-level-1-c4612"></a>Compilerwarnung (Stufe 1) C4612

> Fehler im Namen der Includedatei

## <a name="remarks"></a>Bemerkungen

Diese Warnung tritt bei **#pragma include_alias** auf, wenn ein Dateiname falsch ist oder fehlt.

Die Argumente für die **#pragma Include_alias** -Anweisung können das Anführungszeichen ("*Dateiname*") oder das Winkel Klammer Formular (\<*filename*->) verwenden, beide müssen jedoch dieselbe Form verwenden.

## <a name="example"></a>Beispiel

```cpp
// C4612.cpp
// compile with: /W1 /LD
#pragma include_alias("StandardIO", <stdio.h>) // C4612
```
