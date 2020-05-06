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
ms.openlocfilehash: 0d573fac938f5e4d62c99c8cd6e676b96123a0c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232916"
---
# <a name="multibyte-and-wide-characters"></a>Mehrbyte- und Breitzeichen

Ein Mehrbytezeichen ist ein Zeichen, das aus einem oder mehreren Bytesequenzen besteht. Jede Bytesequenz stellt ein einzelnes Zeichen im erweiterten Zeichensatz dar. Mehrbytezeichen werden in Zeichensätzen wie Kanji verwendet.

Breitzeichen sind mehrsprachige Zeichencodes, deren Breite immer 16 Bit beträgt. Der Typ für Zeichenkonstanten ist `char`. Der Typ ist für Breitzeichen ist `wchar_t`. Da Breitzeichen stets eine feste Größe aufweisen, vereinfachen diese das Programmieren mit internationalen Zeichensätzen.

Das Breitzeichen-Zeichenfolgenliteral `L"hello"` wird zu einem Array mit sechs Ganzzahlen vom Typ `wchar_t`.

```
{L'h', L'e', L'l', L'l', L'o', 0}
```

Die Unicode-Spezifikation entspricht der Spezifikation für Breitzeichen. Die Laufzeitbibliotheksroutinen für Übersetzungen zwischen Multibyte- und Breitzeichen enthalten `mbstowcs`, `mbtowc`, `wcstombs` und `wctomb`.

## <a name="see-also"></a>Siehe auch

[C-Bezeichner](../c-language/c-identifiers.md)
