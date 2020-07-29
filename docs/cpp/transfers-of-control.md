---
title: Übertragung der Steuerung
ms.date: 11/04/2016
helpviewer_keywords:
- control flow, branching
- control flow, transferring control
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
ms.openlocfilehash: ef437d0a691ceff72485be1ff9584052f540031a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232182"
---
# <a name="transfers-of-control"></a>Übertragung der Steuerung

Sie können die- **`goto`** Anweisung oder eine **`case`** Bezeichnung in einer- **`switch`** Anweisung verwenden, um ein Programm anzugeben, das sich hinter einem Initialisierer verzweigt. Solcher Code ist nicht zulässig, es sei denn, die Deklaration, die den Initialisierer enthält, befindet sich in einem Block, der von dem Block eingeschlossen wird, in dem die Sprunganweisung auftritt.

Das folgende Beispiel zeigt eine Schleife, welche die Objekte `total`, `ch` und `i` deklariert und initialisiert. Es gibt auch eine fehlerhafte **`goto`** Anweisung, die die Steuerung über einen Initialisierer überträgt.

```cpp
// transfers_of_control.cpp
// compile with: /W1
// Read input until a nonnumeric character is entered.
int main()
{
   char MyArray[5] = {'2','2','a','c'};
   int i = 0;
   while( 1 )
   {
      int total = 0;

      char ch = MyArray[i++];

      if ( ch >= '0' && ch <= '9' )
      {
         goto Label1;

         int i = ch - '0';
      Label1:
         total += i;   // C4700: transfers past initialization of i.
      } // i would be destroyed here if  goto error were not present
   else
      // Break statement transfers control out of loop,
      //  destroying total and ch.
      break;
   }
}
```

Im vorherigen Beispiel versucht die- **`goto`** Anweisung, die Steuerung hinter der Initialisierung von zu übertragen `i` . Wenn jedoch `i` zwar deklariert, aber nicht initialisiert ist, wäre die Übertragung gültig.

Die `total` -Objekte und `ch` , die im-Block deklariert werden, der als *Anweisung* der-Anweisung fungiert **`while`** , werden zerstört, wenn dieser Block mithilfe der-Anweisung beendet wird **`break`** .
