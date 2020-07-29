---
title: Zeichenzuweisungen
ms.date: 11/04/2016
helpviewer_keywords:
- characters [C++], assignments
- MBCS [C++], character assignments
ms.assetid: dcc329cd-92df-4e20-817d-364be62ff28f
ms.openlocfilehash: 0f627f88ca2b1d3533d3690cd0316ee047a327ad
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217310"
---
# <a name="character-assignment"></a>Zeichenzuweisungen

Sehen Sie sich das folgende Beispiel an, in dem die- **`while`** Schleife eine Zeichenfolge scannt und alle Zeichen außer "X" in eine andere Zeichenfolge kopiert:

```cpp
while( *sz2 )
{
    if( *sz2 != 'X' )
        *sz1++ = *sz2++;
    else
        sz2++;
}
```

Der Code kopiert das Byte an `sz2` in den Speicherort, auf den von verwiesen `sz1` wird, und erhöht dann `sz1` das nächste Byte. Wenn das nächste Zeichen in `sz2` ein Doppelbyte Zeichen ist, kopiert die Zuweisung `sz1` nur das erste Byte. Im folgenden Code wird eine Portable Funktion verwendet, um das Zeichen sicher und ein anderes zu kopieren und ordnungsgemäß zu erhöhen `sz1` `sz2` :

```cpp
while( *sz2 )
{
    if( *sz2 != 'X' )
    {
        _mbscpy_s( sz1, 1, sz2 );
        sz1 = _mbsinc( sz1 );
        sz2 = _mbsinc( sz2 );
    }
    else
        sz2 = _mbsinc( sz2 );
}
```

## <a name="see-also"></a>Weitere Informationen

[Tipps für die MBCS-Programmierung](../text/mbcs-programming-tips.md)<br/>
[Zeichen Vergleich](../text/character-comparison.md)
