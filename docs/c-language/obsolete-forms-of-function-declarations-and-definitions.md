---
title: Veraltete Formen von Funktionsdeklarationen und -definitionen
ms.date: 11/04/2016
helpviewer_keywords:
- old style function declarations
ms.assetid: 67c5038f-0529-4f29-9d0f-c27580977b50
ms.openlocfilehash: 3311fc846ad0f4f80c2e3b61508edd626a13fbb2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218792"
---
# <a name="obsolete-forms-of-function-declarations-and-definitions"></a>Veraltete Formen von Funktionsdeklarationen und -definitionen

Die Funktionsdeklarationen und -definitionen im alten Stil verwenden etwas andere Regeln für das Deklarieren von Parametern als die im ANSI-Standard empfohlene C-Syntax. Erstens besitzen die Deklarationen im alten Stil keine Parameterliste. Zweitens werden die Parameter in der Funktionsdefinition aufgeführt, allerdings werden ihre Typen nicht in der Parameterliste deklariert. Die Typdeklarationen gehen der Verbundanweisung voran, die den Funktionsrumpf bildet. Der alte Syntaxstil ist hinfällig und sollte im neuen Code nicht mehr verwendet werden. Code mit der alten Syntax wird jedoch weiterhin unterstützt. Dieses Beispiel veranschaulicht die veralteten Formen von Deklarationen und Definitionen:

```
double old_style();           /* Obsolete function declaration */

double alt_style( a , real )  /* Obsolete function definition */
    double *real;
    int a;
{
    return ( *real + a ) ;
}
```

Die Funktionen, die eine ganze Zahl oder einen Zeiger mit derselben Größe wie **`int`** zurückgeben, müssen keine Deklaration aufweisen, obwohl die Deklaration empfohlen wird.

Um die Einhaltung des ANSI-C-Standards zu gewährleisten, generieren Funktionsdeklarationen alten Stils mit Auslassungszeichen jetzt beim Kompilieren mit der /Za-Option einen Fehler. Beim Kompilieren mit "/Ze" wird eine Warnung der Stufe 4 generiert. Zum Beispiel:

```cpp
void funct1( a, ... )  /* Generates a warning under /Ze or */
int a;                 /* an error when compiling with /Za */
{
}
```

Sie sollten diese Deklaration als Prototyp neu schreiben:

```cpp
void funct1( int a, ... )
{
}
```

Funktionsdeklarationen im alten Stil generieren außerdem Warnungen, wenn Sie danach die gleiche Funktion entweder mit Auslassungszeichen oder einem Parameter mit einem Typ deklarieren oder definieren, der nicht der gleiche ist wie sein höhergestufter Typ.

Im nächsten Abschnitt [C-Funktionsdefinitionen](../c-language/c-function-definitions.md) wird die Syntax von Funktionsdefinitionen aufgezeigt, einschließlich des alten Syntaxstils. Das Nichtterminal für die Parameterliste im alten Syntaxstil ist *identifier-list*.

## <a name="see-also"></a>Siehe auch

[Übersicht über die Funktionen](../c-language/overview-of-functions.md)
