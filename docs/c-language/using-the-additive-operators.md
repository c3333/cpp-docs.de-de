---
title: Verwenden von additiven Operatoren
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
ms.openlocfilehash: 06d71f3ad1944976a8d415be9487cb5ea365fa26
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213683"
---
# <a name="using-the-additive-operators"></a>Verwenden von additiven Operatoren

Die folgenden Beispiele, welche die Additions- und Subtraktionsoperatoren veranschaulichen, verwenden diese Deklarationen:

```
int i = 4, j;
float x[10];
float *px;
```

Diese Anweisungen sind gleichwertig:

```
px = &x[4 + i];
px = &x[4] + i;
```

Der Wert von `i` wird mit der Länge eines **`float`** multipliziert und zu `&x[4]` hinzugefügt. Das Zeigerwertergebnis ist die Adresse von `x[8]`.

```
j = &x[i] - &x[i-2];
```

In diesem Beispiel wird die Adresse des dritten Elements von `x` (angegeben durch `x[i-2]`) von der Adresse des fünften Elements von `x` (angegeben durch `x[i]`) subtrahiert. Die Differenz wird durch die Länge eines **`float`** geteilt. Das Ergebnis ist der Integerwert 2.

## <a name="see-also"></a>Siehe auch

[C-Operatoren (additiv)](../c-language/c-additive-operators.md)
