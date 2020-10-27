---
title: Schlüsselwort „_Noreturn“ und Makro „noreturn“ (C11)
description: In diesem Artikel werden das Schlüsselwort `_Noreturn` und das Makro `noreturn` beschrieben.
ms.date: 10/19/2020
f1_keywords:
- _Noreturn_c
- noreturn
helpviewer_keywords:
- keywords [C]
ms.openlocfilehash: 68448d8b8c999c92fb240100c25048fa94a559b9
ms.sourcegitcommit: 19016630f9d35f365e9ba249e0f3617515d7ca33
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2020
ms.locfileid: "92274695"
---
# <a name="_noreturn-keyword-and-noreturn-macro-c11"></a>Schlüsselwort `_Noreturn` und Makro `noreturn` (C11)

Das Schlüsselwort `_Noreturn` wurde in C11 eingeführt. Es teilt dem Compiler mit, dass die Funktion, auf die es angewendet wird, nichts an den Aufrufer zurückgibt. Der Compiler weiß, dass der Code, der auf einen Aufruf einer `_Noreturn`-Funktion folgt, nicht erreichbar ist. Ein Beispiel für eine Funktion, die nichts zurückgibt, ist [abort](../c-runtime-library/reference/abort.md). Wenn die Möglichkeit besteht, dass die Ablaufsteuerung etwas an den Aufrufer zurückgibt, darf die Funktion nicht über das `_Noreturn`-Attribut verfügen.

Das Schlüsselwort wird in der Regel über das in <stdnoreturn.h> bereitgestellte Hilfsmakro `noreturn` verwendet, das dem `_Noreturn`-Schlüsselwort zugeordnet ist.

Die Hauptvorteile der Verwendung von `_Noreturn` (oder der Entsprechung `noreturn`) sind, dass die Absicht der Funktion im Code für zukünftige Leser deutlich wird und unabsichtlich nicht erreichbarer Code erkannt wird.

Eine mit `noreturn` gekennzeichnete Funktion sollte keinen Rückgabetyp enthalten, da sie keinen Wert an den Aufrufer zurückgibt. Diese sollte `void` lauten.

## <a name="example-using-noreturn-macro-and-_noreturn-keyword"></a>Beispiel für die Verwendung des Makros `noreturn` und des Schlüsselworts `_Noreturn `

Das folgende Beispiel zeigt die Verwendung des Schlüsselworts `_Noreturn` und des entsprechenden Makros `noreturn`.

IntelliSense generiert bei Verwendung des Makros `noreturn` möglicherweise einen falschen Fehler (`E0065`), den Sie ignorieren können. Die Ausführung des Beispiels wird nicht verhindert.

```C
// Compile with Warning Level4 (/W4) and /std:c11
#include <stdio.h>
#include <stdlib.h>
#include <stdnoreturn.h>

noreturn void fatal_error(void)
{
    exit(3);
}

_Noreturn void not_coming_back(void)
{
    puts("There's no coming back");
    fatal_error();
    return; // warning C4645 - function declared with noreturn has a return statement
}

void done(void)
{
    puts("We'll never get here");
}

int main(void)
{
    not_coming_back();
    done(); // warning c4702 - unreachable code

    return 0;
}
```

## <a name="requirements"></a>Anforderungen

|Makro|Erforderlicher Header|
|-------------|---------------------|
|**`noreturn`**|\<stdnoreturn.h>|

## <a name="see-also"></a>Siehe auch

[/std (Angeben der Standardsprachversion)](../build/reference/std-specify-language-standard-version.md)\
[/W4 (Angeben der Warnstufe)](../build/reference/compiler-option-warning-level.md)\
[Warnung C4702](../error-messages\compiler-warnings\compiler-warning-level-4-c4702.md)\
[__declspec(noreturn)](../cpp/noreturn.md)
