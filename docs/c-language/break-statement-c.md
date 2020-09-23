---
title: break-Anweisung (C)
ms.date: 11/04/2016
f1_keywords:
- break
helpviewer_keywords:
- break keyword [C]
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
ms.openlocfilehash: 5322f8cb5218882d891e2cd66704f9dbfd1bc149
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90683467"
---
# <a name="break-statement-c"></a>break-Anweisung (C)

Die **`break`** -Anweisung beendet die Ausführung der nächsten einschließenden **`do`** -, **`for`** -, **`switch`** - oder **`while`** -Anweisung, in der sie enthalten ist. Das Steuerelement wird an die Anweisung übergeben, die auf die beendete Anweisung folgt.

## <a name="syntax"></a>Syntax

*jump-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**break ;**

Die **`break`** -Anweisung wird häufig verwendet, um die Verarbeitung eines besonderen Falls in einer **`switch`** -Anweisung zu beenden. Eine fehlende iterative oder **`switch`** -Anweisung generiert einen Fehler.

In geschachtelten Anweisungen beendet die **`break`** -Anweisung lediglich die **`do`** -, **`for`** -, **`switch`** - oder **`while`** -Anweisung, von der sie direkt umschlossen ist. Sie können eine **`return`** - oder **`goto`** -Anweisung verwenden, um die Steuerung aus der geschachtelten Struktur an eine andere Stelle zu übertragen.

Dieses Beispiel veranschaulicht die **`break`** -Anweisung:

```C
#include <stdio.h>
int main() {
   char c;
   for(;;) {
      printf_s( "\nPress any key, Q to quit: " );

      // Convert to character value
      scanf_s("%c", &c);
      if (c == 'Q')
          break;
   }
} // Loop exits only when 'Q' is pressed
```

## <a name="see-also"></a>Siehe auch

[break-Anweisung](../cpp/break-statement-cpp.md)
