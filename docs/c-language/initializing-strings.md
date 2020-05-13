---
title: Initialisieren von Zeichenfolgen
ms.date: 11/04/2016
helpviewer_keywords:
- character arrays, initializing
- strings [C++], initializing
- initializing arrays, strings
ms.assetid: 0ab8079d-d0d3-48f9-afd1-36a7bb439b29
ms.openlocfilehash: c9dbad72314e9ce01d022d26209e2132c29c106a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326000"
---
# <a name="initializing-strings"></a>Initialisieren von Zeichenfolgen

Sie können ein Zeichenarray (oder Breitzeichen) mit einem Zeichenfolgenliteral (oder Breitzeichenfolgenliteral) initialisieren. Zum Beispiel:

```
char code[ ] = "abc";
```

initialisiert `code` als Zeichenarray mit vier Elementen. Das vierte Element ist das Nullzeichen, welches alle Zeichenfolgenliterale beendet.

Eine Bezeichnerliste kann nur so lang sein, wie die Anzahl von zu initialisierenden Bezeichnern. Beim Erstellen einer Arraygröße, die kürzer als die Zeichenfolge ist, werden die zusätzlichen Zeichen ignoriert. Zum Beispiel initialisiert die folgende Deklaration `code` als ein Drei-Elemente-Zeichenarray:

```
char code[3] = "abcd";
```

Nur die ersten drei Zeichen des Initialisierers werden `code` zugewiesen. Das Zeichen `d` und das eine Zeichenfolge beendete NULL-Zeichen werden verworfen. Beachten Sie, dass dies eine nicht terminierte Zeichenfolge (d. h. eine Zeichenfolge ohne einen 0-Wert, um ihr Ende zu markieren) erstellt und eine Diagnosemeldung generiert, die diese Bedingung angibt.

Die Deklaration

```
char s[] = "abc", t[3] = "abc";
```

ist identisch mit

```
char s[]  = {'a', 'b', 'c', '\0'},
     t[3] = {'a', 'b', 'c' };
```

Wenn die Zeichenfolge kürzer ist als die angegebene Arraygröße, werden die verbleibenden Elemente des Arrays mit 0 initialisiert.

**Microsoft-spezifisch**

In Microsoft C können Zeichenfolgenliterale bis 2048 Byte lang sein.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Initialisierung](../c-language/initialization.md)
