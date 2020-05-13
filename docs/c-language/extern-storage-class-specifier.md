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
ms.openlocfilehash: 6bbae7c778f5196ac0dca387265499b27119a367
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233833"
---
# <a name="extern-storage-class-specifier"></a>Speicherklassenspezifizierer "extern"

Eine Variable, die mit dem Speicherklassenspezifizierer **extern** deklariert wird, ist ein Verweis auf eine Variable mit demselben Namen, die in einer anderen Quelldatei definiert ist. Durch diese Deklaration wird die Definition der Variablen auf externer Ebene sichtbar. Einer als **extern** deklarierten Variable ist kein eigener Speicher zugewiesen, es handelt sich nur um einen Namen.

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

In diesem Beispiel wird die Variable `i` in „Source1.c“ mit dem Anfangswert 1 definiert. Eine Deklaration als **extern** in „Source2.c“ macht „i“ in dieser Datei sichtbar.

In der `func`-Funktion wird die Adresse der globalen Variablen `i` verwendet, um die **statische** Zeigervariable `external_i` zu initialisieren. Dies funktioniert, da die globale Variable über eine **statische** Lebensdauer verfügt. Das bedeutet, dass ihre Adresse während der Programmausführung nicht geändert wird. Als Nächstes wird eine Variable `i` innerhalb des Bereichs von `func` als lokale Variable mit dem Anfangswert 16 definiert. Diese Definition wirkt sich nicht auf den Wert der Variablen `i` auf der externen Ebene aus, die durch Verwendung ihres Namens für die lokale Variable verdeckt wird. Auf den Wert der globalen `i`-Variablen kann jetzt nur über den Zeiger `external_i` zugegriffen werden.

## <a name="see-also"></a>Siehe auch

[Speicherklassenspezifizierer für Deklarationen der internen Ebene](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
