---
title: Speicherklassenspezifizierer "extern"
ms.date: 07/10/2018
helpviewer_keywords:
- extern keyword [C]
- storage class specifiers, extern
- extern keyword [C], storage class specifier
- external linkage, storage-class specifiers
- external linkage, extern modifier
ms.assetid: 6e16d927-291f-49e4-986c-9d91a482a441
ms.openlocfilehash: e3242f86e30dcf3227586400b83266ad366ec7e8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217102"
---
# <a name="extern-storage-class-specifier"></a>Speicherklassenspezifizierer "extern"

Eine Variable, die mit dem Speicherklassenspezifizierer **`extern`** deklariert wird, ist ein Verweis auf eine Variable mit demselben Namen, die in einer anderen Quelldatei definiert ist. Durch diese Deklaration wird die Definition der Variablen auf externer Ebene sichtbar. Einer als **`extern`** deklarierten Variable ist kein eigener Speicher zugewiesen, es handelt sich nur um einen Namen.

## <a name="example"></a>Beispiel

Dieses Beispiel veranschaulicht Deklarationen auf interner und externer Ebene:

```c

// Source1.c

int i = 1;

// Source2. c

#include <stdio.h>

// Refers to the i that is defined in Source1.c:
extern int i;

void func(void);

int main()
{
    // Prints 1:
    printf_s("%d\n", i);
    func();
    return;
}

void func(void)
{
    // Address of global i assigned to pointer variable:
    static int *external_i = &i;

    // This definition of i hides the global i in Source.c:
    int i = 16;

    // Prints 16, 1:
    printf_s("%d\n%d\n", i, *external_i);
}
```

In diesem Beispiel wird die Variable `i` in „Source1.c“ mit dem Anfangswert 1 definiert. Eine **`extern`** -Deklaration in „Source2.c“ macht „i“ in dieser Datei sichtbar.

In der `func`-Funktion wird die Adresse der globalen Variable `i` verwendet, um die **`static`** -Zeigervariable `external_i` zu initialisieren. Das funktioniert, weil die globale Variable über eine Lebensdauer vom Typ **`static`** verfügt. Das bedeutet, dass ihre Adresse sich während der Programmausführung nicht ändert. Als Nächstes wird eine Variable `i` innerhalb des Bereichs von `func` als lokale Variable mit dem Anfangswert 16 definiert. Diese Definition wirkt sich nicht auf den Wert der Variablen `i` auf der externen Ebene aus, die durch Verwendung ihres Namens für die lokale Variable verdeckt wird. Auf den Wert der globalen `i`-Variablen kann jetzt nur über den Zeiger `external_i` zugegriffen werden.

## <a name="see-also"></a>Siehe auch

[Speicherklassenspezifizierer für Deklarationen der internen Ebene](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
