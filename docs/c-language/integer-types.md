---
title: Ganzzahltypen
ms.date: 07/22/2020
helpviewer_keywords:
- integer data type, integer types in C++
- integer constants
- integer types
- integers, types
ms.assetid: c8926a5e-0e98-4e37-9b05-ce97961379bd
ms.openlocfilehash: 61ed64c613bc88ed5bf62999ba77fa4090c1ec4a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211800"
---
# <a name="integer-types"></a>Ganzzahltypen

Allen Integerkonstanten wird ein Typ anhand ihres Werts und der Ausdrucksmethode zugewiesen. Sie können erzwingen, dass eine Integerkonstante den Typ **`long`** aufweist, indem Sie den Buchstaben **`l`** oder **`L`** am Ende der Konstante anfügen. Ebenso können Sie erzwingen, dass die Integerkonstante den Typ **`unsigned`** aufweist, indem Sie **`u`** oder **`U`** an den Wert anfügen. Der Kleinbuchstabe **`l`** kann mit der Ziffer 1 verwechselt werden und sollte daher vermieden werden. Im Folgenden werden einige Formen der **`long`** -Integerkonstanten aufgeführt:

```C
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

Der Typ, den Sie einer Konstanten zuweisen, hängt von dem Wert ab, den die Konstante darstellt. Der Wert einer Konstante muss im Bereich der darstellbaren Werte für ihren Typ liegen. Ein Konstantentyp bestimmt, welche Konvertierungen ausgeführt werden, wenn die Konstante in einem Ausdruck verwendet oder das Minuszeichen ( **`-`** ) angewendet wird. In dieser Liste werden die Konvertierungsregeln für Integerkonstanten zusammengefasst.

- Der Typ für eine Dezimalkonstante ohne Suffix lautet **`int`** , **`long int`** oder **`unsigned long int`** . Der erste dieser drei Typen, in der der Wert der Konstante dargestellt werden kann, ist der Typ, der der Konstante zugewiesen wird.

- Der Typ, der Oktal- oder Hexadezimalkonstanten ohne Suffixe zugewiesen wird, lautet je nach Größe der Konstante **`int`** , **`unsigned int`** , **`long int`** oder **`unsigned long int`** .

- Der Typ, der Konstanten mit den Suffixen **`u`** oder **`U`** zugewiesen wird, lautet je nach Größe **`unsigned int`** oder **`unsigned long int`** .

- Der Typ, der Konstanten mit den Suffixen **`l`** oder **`L`** zugewiesen wird, lautet je nach Größe **`long int`** oder **`unsigned long int`** .

- Der Typ, der Konstanten mit **`u`** oder **`U`** und den Suffixen **`l`** oder **`L`** zugewiesen wird, lautet **`unsigned long int`** .

## <a name="see-also"></a>Siehe auch

[C-Ganzzahlkonstanten](../c-language/c-integer-constants.md)
