---
title: Ganzzahltypen
ms.date: 11/04/2016
helpviewer_keywords:
- integer data type, integer types in C++
- integer constants
- integer types
- integers, types
ms.assetid: c8926a5e-0e98-4e37-9b05-ce97961379bd
ms.openlocfilehash: 23da055b56e2ae77fed796d9ba8e7f227e572a9f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232851"
---
# <a name="integer-types"></a>Ganzzahltypen

Allen Integerkonstanten wird ein Typ anhand ihres Werts und der Ausdrucksmethode zugewiesen. Sie können erzwingen, dass eine Integerkonstante den Typ **long** aufweist, indem Sie den Buchstaben **l** oder **L** am Ende der Konstante anfügen; ebenso können Sie erzwingen, dass die Integerkonstante den Typ `unsigned` aufweist, indem Sie **u** oder **U** an den Wert anfügen. Der Kleinbuchstabe **l** kann mit der Ziffer 1 verwechselt werden und sollte daher nicht angefügt werden. Dies sind einige Formen der **long**-Integerkonstanten:

```
/* Long decimal constants */
10L
79L

/* Long octal constants */
012L
0115L

/* Long hexadecimal constants */
0xaL or 0xAL
0X4fL or 0x4FL

/* Unsigned long decimal constant */
776745UL
778866LU
```

Der Typ, den Sie einer Konstanten zuweisen, hängt von dem Wert ab, den die Konstante darstellt. Der Wert einer Konstante muss im Bereich der darstellbaren Werte für ihren Typ liegen. Ein Konstantentyp bestimmt, welche Konvertierungen ausgeführt werden, wenn die Konstante in einem Ausdruck verwendet oder das Minuszeichen ( **-** ) angewendet wird. In dieser Liste werden die Konvertierungsregeln für Integerkonstanten zusammengefasst.

- Eine Dezimalkonstante ohne Suffix ist vom Typ `int`, **long int** oder **unsigned long int**. Der erste dieser drei Typen, in der der Wert der Konstante dargestellt werden kann, ist der Typ, der der Konstante zugewiesen wird.

- Je nach Größe der Konstanten wird der Typ `int`, `unsigned int`, **long int** oder **unsigned long int** den Oktal- und Hexadezimalkonstanten ohne Suffixe zugewiesen.

- Je nach Größe der Konstanten wird der Typ **unsigned int** oder **unsigned long int** den Konstanten mit einem **u**- oder **U**-Suffix zugewiesen.

- Je nach Größe der Konstanten wird der Typ **long int** oder **unsigned long int** den Konstanten mit dem **l**- oder **L**-Suffix zugewiesen.

- Konstanten mit einem **u**- oder **U**- und einem **l**- oder **L**-Suffix wird der Typ **unsigned long int** zugewiesen.

## <a name="see-also"></a>Siehe auch

[C-Ganzzahlkonstanten](../c-language/c-integer-constants.md)
