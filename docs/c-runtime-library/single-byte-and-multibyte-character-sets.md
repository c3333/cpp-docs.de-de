---
title: Einzelbyte- und Mehrbyte-Zeichensätze
description: Eine Einführung in Einzel-und Multibyte-Zeichensätze in der Microsoft-Lauf Zeit Bibliothek.
ms.topic: conceptual
ms.date: 11/04/2016
helpviewer_keywords:
- SBCS (single byte character set)
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- character sets [C++], single byte
ms.assetid: 2cbc78ea-33c0-4cfb-b0df-7ce2458431ce
ms.openlocfilehash: 6668285915ab9f1939c1baf8a2d3da2d00543528
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590172"
---
# <a name="single-byte-and-multibyte-character-sets"></a>Einzelbyte- und Mehrbyte-Zeichensätze

Mit dem ASCII-Zeichensatz werden Zeichen im Bereich von 0x00 bis 0x7F definiert. Von einigen anderen Zeichensätzen (hauptsächlich europäischer Herkunft) werden wie beim ASCII-Zeichensatz die Zeichen im Bereich von 0x00 bis 0x7F definiert; zusätzlich wird ein erweiterter Zeichensatz im Bereich von 0x80 bis 0xFF definiert.  Ein 8-Bit-Einzel Byte-Zeichensatz (Single-Byte Character Set, SBCS) ist ausreichend, um den ASCII-Zeichensatz und die Zeichensätze für viele europäische Sprachen darzustellen. Einige nicht Europäische Zeichensätze, wie z. b. japanische Kanji, enthalten jedoch viel mehr Zeichen, als in einem Einzel Byte-Codierungsschema dargestellt werden können, und erfordern daher eine Multibyte-Zeichensatz Codierung (MBCS).

> [!NOTE]
> Viele SBCS-Routinen in der Microsoft-Laufzeitbibliothek behandeln Multibyte-Bytes, Zeichen und Zeichenfolgen entsprechend. Viele Multibyte-Zeichensätze definieren den ASCII-Zeichensatz als Teilmenge. In vielen Multibyte-Zeichensätzen sind die Zeichen im Bereich von 0x00 bis 0x7F mit den gleichwertigen Zeichen des ASCII-Zeichensatzes identisch. Das ein Byte lange Zeichen NULL („\0“) hat z.B. in ASCII- und MBCS-Zeichenfolgen den Wert 0x00 und steht für das abschließende NULL-Zeichen.

Ein Multibytezeichen-Zeichensatz kann sowohl aus 1-Byte-als auch aus 2-Byte-Zeichen bestehen. Eine Multibytezeichenfolge kann eine Mischung aus Einzel Byte-und Doppelbyte Zeichen enthalten. Ein 2-Byte-Multibytezeichen verfügt über ein führendes Byte und ein nachfolgendes Byte. In einem bestimmten Mehrbyte-Zeichensatz liegen die führenden Bytes ebenso wie die nachfolgenden Bytes innerhalb eines bestimmten Bereichs. Wenn sich diese Bereiche überschneiden, müssen Sie möglicherweise den Kontext auswerten, um zu bestimmen, ob ein bestimmtes Byte als führendes Byte oder als nachfolgendes Byte fungiert.

## <a name="see-also"></a>Weitere Informationen

[Internationalisierung](../c-runtime-library/internationalization.md)<br/>
[Universelle C-Laufzeitroutinen nach Kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
