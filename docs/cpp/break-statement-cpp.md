---
title: break-Anweisung (C++)
ms.date: 11/04/2016
f1_keywords:
- break_cpp
helpviewer_keywords:
- break keyword [C++]
ms.assetid: 63739928-8985-4b05-93ce-016322e6da3d
ms.openlocfilehash: 23d31e1456106d5f82c4a13079c72c231b8477bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190481"
---
# <a name="break-statement-c"></a>break-Anweisung (C++)

Die **break** -Anweisung beendet die Ausführung der nächsten einschließenden Schleife oder bedingten Anweisung, in der Sie angezeigt wird. Das Steuerelement wird an die Anweisung übergeben, die auf das Ende der Anweisung folgt, falls vorhanden.

## <a name="syntax"></a>Syntax

```
break;
```

## <a name="remarks"></a>Bemerkungen

Die **break** -Anweisung wird mit der Conditional [Switch](../cpp/switch-statement-cpp.md) -Anweisung und mit den Anweisungen [do](../cpp/do-while-statement-cpp.md), [for](../cpp/for-statement-cpp.md)und [while](../cpp/while-statement-cpp.md) Loop verwendet.

In einer **Switch** -Anweisung bewirkt die **break** -Anweisung, dass das Programm die nächste Anweisung außerhalb der **Switch** -Anweisung ausführt. Ohne eine **break** -Anweisung wird jede Anweisung der übereinstimmenden **Case** -Bezeichnung bis zum Ende der **Switch** -Anweisung ausgeführt, einschließlich der **default** -Klausel.

In Schleifen beendet die **break** -Anweisung die Ausführung der nächsten einschließenden **do**-, **for**-oder **while** -Anweisung. Das Steuerelement wird an die Anweisung übergeben, die auf die beendete Anweisung folgt, falls vorhanden.

In geschachtelten Anweisungen beendet die **break** -Anweisung nur die **do**-, **for**-, **Switch**-oder **while** -Anweisung, die Sie sofort umschließt. Sie können eine **Return** -oder **goto** -Anweisung verwenden, um die Steuerung von tiefer geschachtelten Strukturen zu übertragen.

## <a name="example"></a>Beispiel

Der folgende Code zeigt die Verwendung der **break** -Anweisung in einer **for** -Schleife.

```cpp
#include <iostream>
using namespace std;

int main()
{
    // An example of a standard for loop
    for (int i = 1; i < 10; i++)
    {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
    }

    // An example of a range-based for loop
int nums []{1, 2, 3, 4, 5, 6, 7, 8, 9, 10};

    for (int i : nums) {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
    }
}
```

```Output
In each case:
1
2
3
```

Der folgende Code zeigt, wie Sie die unter **Brechung** in einer **while** -Schleife und einer **do** -Schleife verwenden.

```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;

    while (i < 10) {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
        i++;
    }

    i = 0;
    do {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
        i++;
    } while (i < 10);
}
```

```Output
In each case:
0123
```

Der folgende Code zeigt, wie Sie **break** in einer Switch-Anweisung verwenden. Sie müssen unter **brechen** in jedem Fall verwenden, wenn Sie die einzelnen Fälle separat behandeln möchten. Wenn Sie keine unter **Brechung**verwenden, greift die Codeausführung auf den nächsten Fall zu.

```cpp
#include <iostream>
using namespace std;

enum Suit{ Diamonds, Hearts, Clubs, Spades };

int main() {

    Suit hand;
    . . .
    // Assume that some enum value is set for hand
    // In this example, each case is handled separately
    switch (hand)
    {
    case Diamonds:
        cout << "got Diamonds \n";
        break;
    case Hearts:
        cout << "got Hearts \n";
        break;
    case Clubs:
        cout << "got Clubs \n";
        break;
    case Spades:
        cout << "got Spades \n";
        break;
    default:
          cout << "didn't get card \n";
    }
    // In this example, Diamonds and Hearts are handled one way, and
    // Clubs, Spades, and the default value are handled another way
    switch (hand)
    {
    case Diamonds:
    case Hearts:
        cout << "got a red card \n";
        break;
    case Clubs:
    case Spades:
    default:
        cout << "didn't get a red card \n";
    }
}
```

## <a name="see-also"></a>Weitere Informationen

[Sprunganweisungen](../cpp/jump-statements-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[continue-Anweisung](../cpp/continue-statement-cpp.md)
