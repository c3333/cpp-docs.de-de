---
title: Hinzufügen einer Anmerkung zu Strukturen und Klassen
ms.date: 06/28/2019
ms.topic: conceptual
f1_keywords:
- _Field_size_bytes_part_
- _Field_size_bytes_full_opt_
- _Field_size_bytes_
- _Field_size_opt_
- _Field_size_part_
- _Field_size_bytes_part_opt_
- _Field_range_
- _Field_size_part_opt_
- _Field_size_
- _Field_size_bytes_opt_
- _Struct_size_bytes_
- _Field_size_bytes_full_
- _Field_size_full_
- _Field_size_full_opt_
- _Field_z_
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
ms.openlocfilehash: e6b08c18d2524f1240eed99dd45320a7f4c00ac3
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "79466063"
---
# <a name="annotating-structs-and-classes"></a>Hinzufügen einer Anmerkung zu Strukturen und Klassen

Sie können Struktur-und Klassenmember mit Anmerkungen versehen, die wie invarianten funktionieren – Sie werden als true an jedem Funktions-oder Funktions Eintrag bzw. in einem Funktionswert, der die einschließende Struktur als Parameter oder Ergebniswert einschließt, angenommen.

## <a name="struct-and-class-annotations"></a>Struktur- und Klassen-Anmerkungen

- `_Field_range_(low, high)`

     Das Feld befindet sich im Bereich (einschließlich) von `low` bis `high`.  Äquivalent zu `_Satisfies_(_Curr_ >= low && _Curr_ <= high)`, die auf das mit Anmerkungen versehene Objekt angewendet werden, indem die entsprechenden Pre-oder Post-Bedingungen verwendet werden.

- `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`

     Ein Feld mit einer beschreibbaren Größe in Elementen (oder Bytes), wie in `size`angegeben.

- `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)``_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`

     Ein Feld mit einer beschreibbaren Größe in Elementen (oder Bytes), wie durch `size`angegeben, und die `count` dieser Elemente (Bytes), die lesbar sind.

- `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`

     Ein Feld, das sowohl lesbare als auch beschreibbare Größe in Elementen (oder Bytes) aufweist, wie durch `size`angegeben.

- `_Field_z_`

     Ein Feld, das eine NULL-terminierte Zeichenfolge aufweist.

- `_Struct_size_bytes_(size)`

     Gilt für die Struktur-oder Klassen Deklaration.  Gibt an, dass ein gültiges Objekt dieses Typs möglicherweise größer als der deklarierte Typ und die Anzahl der Bytes ist, die durch `size`angegeben werden.  Beispiel:

    ```cpp

    typedef _Struct_size_bytes_(nSize)
    struct MyStruct {
        size_t nSize;
        ...
    };

    ```

     Die Puffergröße eines Parameter `pM` vom Typ `MyStruct *` wird dann wie folgt angenommen:

    ```cpp
    min(pM->nSize, sizeof(MyStruct))
    ```

## <a name="example"></a>Beispiel

```cpp
#include <sal.h>

// This _Struct_size_bytes_ is equivalent to what below _Field_size_ means.
_Struct_size_bytes_(__builtin_offsetof(MyBuffer, buffer) + bufferSize * sizeof(int))
struct MyBuffer
{
    static int MaxBufferSize;

    _Field_z_
    const char* name;

    int firstField;

    // ... other fields

    _Field_range_(1, MaxBufferSize)
    int bufferSize;

    _Field_size_(bufferSize)        // Prefered way - easier to read and maintain.
    int buffer[]; // Using C99 Flexible array member
};
```

Hinweise für dieses Beispiel:

- `_Field_z_` entspricht `_Null_terminated_`.  `_Field_z_` für das Feld Name gibt an, dass das Feld Name eine NULL-terminierte Zeichenfolge ist.
- `_Field_range_` für `bufferSize` gibt an, dass der Wert von `bufferSize` innerhalb von 1 und `MaxBufferSize` (beide inklusiv) liegen muss.
- Die Endergebnisse der `_Struct_size_bytes_` und `_Field_size_` Anmerkungen sind gleichwertig. Für Strukturen oder Klassen, die über ein ähnliches Layout verfügen, ist `_Field_size_` leichter zu lesen und zu verwalten, da es weniger Verweise und Berechnungen als die entsprechende `_Struct_size_bytes_` Anmerkung aufweist. `_Field_size_` müssen nicht in die Bytegröße konvertiert werden. Wenn die Byte Größe die einzige Option ist, z. b. für ein void-Zeiger Feld, können `_Field_size_bytes_` verwendet werden. Wenn sowohl `_Struct_size_bytes_` als auch `_Field_size_` vorhanden sind, sind beide für Tools verfügbar. Es liegt an dem Tool, was zu tun ist, wenn die zwei Anmerkungen nicht übereinstimmen.

## <a name="see-also"></a>Weitere Informationen

- [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Einführung in SAL](../code-quality/understanding-sal.md)
- [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md)
- [Hinzufügen einer Anmerkung zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)
- [Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md)
- [Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Systeminterne Funktionen](../code-quality/intrinsic-functions.md)
- [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)
