---
title: break-Anweisung (C)
ms.date: 11/04/2016
f1_keywords:
- break
helpviewer_keywords:
- break keyword [C]
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
ms.openlocfilehash: b38ff6c535c142bd15ea09a4d7c80010c3fff31f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313362"
---
# <a name="break-statement-c"></a>break-Anweisung (C)

Die `break`-Anweisung beendet die Ausführung der nächsten einschließenden `do`, `for`, `switch` oder `while`-Anweisung, in der sie angezeigt wird. Das Steuerelement wird an die Anweisung übergeben, die auf die beendete Anweisung folgt.

## <a name="syntax"></a>Syntax

*jump-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**break ;**

Die Anweisung `break` wird häufig verwendet, um die Verarbeitung eines besonderen Falls in einer `switch`-Anweisung zu beenden. Eine fehlende iterative oder `switch`-Anweisung generiert einen Fehler.

Innerhalb von geschachtelten Anweisungen beendet die `break`-Anweisung lediglich die Anweisung `do`, `for`, `switch` oder `while`, von der sie direkt eingeschlossen ist. Sie können eine `return`-Anweisung oder eine `goto`-Anweisung verwenden, um das Steuerelement aus der geschachtelten Struktur an einen anderen Ort zu übertragen.

In diesem Beispiel wird die `break`-Anweisung veranschaulicht.

```
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
