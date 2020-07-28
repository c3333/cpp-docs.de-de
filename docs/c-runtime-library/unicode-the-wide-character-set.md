---
title: 'Unicode: Der Breitzeichensatz'
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode [C++], wide character set
- wide characters [C++], Unicode
ms.assetid: b6a05a21-59a5-4d30-8c85-2dbe185f7a74
ms.openlocfilehash: b27641b9843d4f6f1ef39d893df5d3f26af372e3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220651"
---
# <a name="unicode-the-wide-character-set"></a>Unicode: Der Breitzeichensatz

Ein Breitzeichen ist ein mehrsprachiger 2-Byte-Zeichencode. Alle in der modernen Computerwelt verwendeten Zeichen, einschließlich technischer Symbole und spezieller Veröffentlichungszeichen, können nach der Unicode-Spezifikation als Breitzeichen dargestellt werden. Der Unicode-Standard wurde von einem großen Konsortium entwickelt und überarbeitet, zu dem auch Microsoft gehört, und zählt heute zu den etablierten Standards.

Ein breit Zeichen weist den Typ auf **`wchar_t`** . Eine Breitzeichenzeichenfolge wird als **wchar_t[]**-Array dargestellt, auf das mit einem `wchar_t*`-Zeiger gezeigt wird. Sie können jedes ASCII-Zeichen als Breitzeichen darstellen, indem Sie den Buchstaben **L** dem Zeichen voranstellen. L'\0' ist beispielsweise das abschließende (16-Bit) NULL-Breitzeichen. Auf ähnliche Weise können Sie jedes ASCII-Zeichenfolgenliteral als Breitzeichen-Zeichenfolgenliteral darstellen, indem Sie einfach den Buchstabe L dem ASCII-Literal voranstellen (L"Hello").

Im Allgemeinen nehmen Breitzeichen mehr Arbeitsspeicher in Anspruch als Multibytezeichen, werden aber schneller verarbeitet. Darüber hinaus kann jeweils nur ein Gebietsschema in der Multibytecodierung dargestellt werden, während alle Zeichensätze der Welt gleichzeitig von der Unicode-Darstellung dargestellt werden können.

## <a name="see-also"></a>Weitere Informationen

[Internationalisierung](../c-runtime-library/internationalization.md)<br/>
[Universelle C-Laufzeitroutinen nach Kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
