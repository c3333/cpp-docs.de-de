---
title: Mehrbyte- und Breitzeichen
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- character data types [C]
- Unicode [C++], wide character set
- types [C], character
- characters [C++], wide
- international applications [C++], character display
- multibyte characters [C++]
- wide characters [C++]
- characters [C++], codes
- character codes [C++], wide
- character codes [C++], multibyte
ms.assetid: 1943c469-200d-4724-b18f-781d70520f9e
ms.openlocfilehash: 8e27a1832284c109cc2d8a4655f6d093bf7a2d99
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87199658"
---
# <a name="multibyte-and-wide-characters"></a>Mehrbyte- und Breitzeichen

Ein Mehrbytezeichen ist ein Zeichen, das aus einem oder mehreren Bytesequenzen besteht. Jede Bytesequenz stellt ein einzelnes Zeichen im erweiterten Zeichensatz dar. Mehrbytezeichen werden in Zeichensätzen wie Kanji verwendet.

Breitzeichen sind mehrsprachige Zeichencodes, deren Breite immer 16 Bit beträgt. Der Typ für Zeichenkonstanten ist **`char`** . Der Typ für Breitzeichen ist **`wchar_t`** . Da Breitzeichen stets eine feste Größe aufweisen, vereinfachen diese das Programmieren mit internationalen Zeichensätzen.

Das Breitzeichen-Zeichenfolgenliteral `L"hello"` wird zu einem Array mit sechs Integern vom Typ **`wchar_t`** .

```
{L'h', L'e', L'l', L'l', L'o', 0}
```

Die Unicode-Spezifikation entspricht der Spezifikation für Breitzeichen. Die Laufzeitbibliotheksroutinen für Übersetzungen zwischen Multibyte- und Breitzeichen enthalten `mbstowcs`, `mbtowc`, `wcstombs` und `wctomb`.

## <a name="see-also"></a>Siehe auch

[C-Bezeichner](../c-language/c-identifiers.md)
