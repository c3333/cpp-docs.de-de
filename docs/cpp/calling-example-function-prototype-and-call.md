---
title: Aufrufbeispiel:Funktionsprototyp und Aufruf
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
ms.openlocfilehash: c41d7679be8b7faa3c8df1368d14815a1b840284
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190169"
---
# <a name="calling-example-function-prototype-and-call"></a>Aufrufbeispiel:Funktionsprototyp und Aufruf

**Microsoft-spezifisch**

Das folgende Beispiel zeigt die Ergebnisse eines Funktionsaufrufs mit unterschiedlichen Aufrufkonventionen.

Dieses Beispiel basiert auf dem folgenden Funktionsskelett. Ersetzen Sie `calltype` durch die entsprechende Aufrufkonvention.

```cpp
void    calltype MyFunc( char c, short s, int i, double f );
.
.
.
void    MyFunc( char c, short s, int i, double f )
    {
    .
    .
    .
    }
.
.
.
MyFunc ('x', 12, 8192, 2.7183);
```

Weitere Informationen finden Sie unter [Ergebnisse des aufrufenden Beispiels](../cpp/results-of-calling-example.md).

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Aufrufkonventionen](../cpp/calling-conventions.md)
