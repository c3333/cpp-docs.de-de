---
title: 'Unicode: Der Breitzeichensatz'
description: Eine Einführung in den Unicode-breit Zeichensatz in der Microsoft C-Laufzeit.
ms.topic: conceptual
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode [C++], wide character set
- wide characters [C++], Unicode
ms.assetid: b6a05a21-59a5-4d30-8c85-2dbe185f7a74
ms.openlocfilehash: 751017a62a960eaf2afa2354a43a13971b89252a
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590159"
---
# <a name="unicode-the-wide-character-set"></a>Unicode: Der Breitzeichensatz

Ein Breitzeichen ist ein mehrsprachiger 2-Byte-Zeichencode. Alle in der modernen Computerwelt verwendeten Zeichen, einschließlich technischer Symbole und spezieller Veröffentlichungszeichen, können nach der Unicode-Spezifikation als Breitzeichen dargestellt werden. Der Unicode-Standard wurde von einem großen Konsortium entwickelt und überarbeitet, zu dem auch Microsoft gehört, und zählt heute zu den etablierten Standards.

Ein breit Zeichen weist den Typ auf **`wchar_t`** . Eine Zeichenfolge mit breit Zeichen wird als- **`wchar_t[]`** Array dargestellt. Sie zeigen auf das Array mit einem `wchar_t*` Zeiger. 

Sie können jedes ASCII-Zeichen als breit Zeichen darstellen, indem Sie den Buchstaben vorangestellt wird `L` . Beispielsweise `L'\0'` ist das abschließende Breite Zeichen (16-Bit) NULL.

Sie können beliebige ASCII-Zeichenfolgenliterale als Zeichen folgen Literale für breit Zeichen darstellen, indem Sie den Buchstaben vorangestellt `L` Beispiel: `L"Hello"`.

Im Allgemeinen verwenden breit Zeichen mehr Speicherplatz als Multibytezeichen. Breit Zeichen sind jedoch schneller zu verarbeiten. Es kann jeweils nur ein Gebiets Schema in der multibytecodierung dargestellt werden. Alle Zeichensätze der Welt werden gleichzeitig von der Unicode-Darstellung dargestellt.

## <a name="see-also"></a>Weitere Informationen

[Internationalisierung](../c-runtime-library/internationalization.md)\
[Universelle C-Laufzeitroutinen nach Kategorie](../c-runtime-library/run-time-routines-by-category.md)
