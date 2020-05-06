---
title: Zeichentypen
ms.date: 11/04/2016
helpviewer_keywords:
- character data types [C]
- types [C], character
ms.assetid: d3ca8cda-c0d7-43af-9472-697e8ef015ce
ms.openlocfilehash: f894114d4e980b11edf55c4d4b7c4e60af396fb1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312634"
---
# <a name="character-types"></a>Zeichentypen

Eine ganzzahlige Zeichenkonstante, der nicht der Buchstabe **L** vorangestellt ist, ist vom Typ `int`. Der Wert einer ganzzahligen Zeichenkonstante, die ein einzelnes Zeichen enthält, ist der numerische Wert des Zeichens, das als ganze Zahl interpretiert wird. Beispielsweise ist der numerische Wert des Zeichens `a` 97 in dezimalen und 61 in hexadezimalen Zahlen.

Syntaktisch ist eine „Breitzeichenkonstante“ eine Zeichenkonstante, der der Buchstabe **L** vorangestellt ist. Eine Breitzeichenkonstante hat den Typ `wchar_t`, ein ganzzahliger Typ, der in der STDDEF.H-Headerdatei definiert ist. Zum Beispiel:

```
char    schar =  'x';   /* A character constant          */
wchar_t wchar = L'x';   /* A wide-character constant for
                            the same character           */
```

Breitzeichenkonstanten sind 16 Bit breit und geben Member des erweiterten Ausführungszeichensatzes an. Sie ermöglichen es, Zeichen in Alphabeten auszudrücken, die zu groß sind, um durch den Typ `char` dargestellt zu werden. Weitere Informationen über Breitzeichen erhalten Sie unter [Multibyte- und Breitzeichen](../c-language/multibyte-and-wide-characters.md).

## <a name="see-also"></a>Siehe auch

[C-Zeichenkonstanten](../c-language/c-character-constants.md)
