---
title: Byteklassifizierung
ms.date: 04/04/2018
f1_keywords:
- c.types.bytes
helpviewer_keywords:
- code page 932
- byte classification routines
- bytes, testing
ms.assetid: 1cb52d71-fb0c-46ca-aad7-6472c1103370
ms.openlocfilehash: 7272170bd3a1e765e728451afc245947111ee947
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171566"
---
# <a name="byte-classification"></a>Byteklassifizierung

Jede dieser Routinen testet, ob ein angegebenes Byte eines Multibytezeichens eine Bedingung erfüllt. Wenn nicht anders angegeben, ist der Ausgabewert von der Kategorieeinstellung **LC_CTYPE** des Gebietsschemas betroffen. Weitere Informationen finden Sie unter [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). Die Versionen dieser Funktionen ohne das **_l**-Suffix verwenden das aktuelle Gebietsschema für dieses vom Gebietsschema abhängige Verhalten; die Versionen mit dem **_l**-Suffix sind beinahe identisch, verwenden jedoch stattdessen den ihnen übergebenen Gebietsschemaparameter.

> [!NOTE]
> Die ASCII-Zeichen zwischen 0 und 127 sind definitionsgemäß eine Teilmenge jedes Multibyte-Zeichensatzes. Beispielsweise enthält der japanische Katakana-Zeichensatz sowohl ASCII- als auch Nicht-ASCII-Zeichen.

Die vordefinierten Konstanten in der folgenden Tabelle sind in \<ctype.h> definiert.

## <a name="multibyte-character-byte-classification-routines"></a>Byteklassifizierungsroutinen für Multibytezeichen

|Routine|Bytetestbedingung|
|-------------|-------------------------|
|[isleadbyte, _isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|Führendes Byte; Testergebnis hängt von der Kategorieeinstellung **LC_CTYPE** des aktuellen Gebietsschemas ab|
|[_ismbbalnum, _ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|**isalnum** &#124;&#124; **_ismbbkalnum**|
|[_ismbbalpha, _ismbbalpha_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|**isalpha** &#124;&#124; **_ismbbkalnum**|
|[_ismbbgraph, _ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|Entspricht **_ismbbprint**, **_ismbbgraph** enthält jedoch nicht das Leerzeichen (0x20)|
|[_ismbbkalnum, _ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|Nicht-ASCII-Textsymbol, das kein Interpunktionszeichen ist. Beispielsweise testet **_ismbbkalnum** nur in Codepage 932 auf alphanumerische Katakana-Zeichen|
|[_ismbbkana, _ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|Katakana (0xA1-0xDF), nur Codepage 932|
|[_ismbbkprint, _ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|Nicht-ASCII-Textsymbol oder Nicht-ASCII-Interpunktionssymbol. **_ismbbkprint** testet beispielsweise in Codepage 932 nur auf alphanumerische Katakana-Zeichen oder Katakana-Interpunktion (Bereich: 0xA1–0xDF).|
|[_ismbbkpunct, _ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|Nicht-ASCII-Interpunktion. Beispielsweise testet **_ismbbkpunct** nur in Codepage 932 auf Katakana-Interpunktion.|
|[_ismbblead, _ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|Erstes Byte eines Multibytezeichens. Gültige Bereiche sind in Codepage 932 beispielsweise nur 0x81–0x9F, 0xE0–0xFC.|
|[_ismbbprint, _ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|**isprint** &#124;&#124; **_ismbbkprint**. **ismbbprint** schließt das Leerzeichen ein (0x20)|
|[_ismbbpunct, _ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|**ispunct** &#124;&#124; **_ismbbkpunct**|
|[_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|Zweites Byte eines Multibytezeichens. Gültige Bereiche sind in Codepage 932 beispielsweise nur 0x40–0x7E, 0x80–0xEC.|
|[_ismbslead, _ismbslead_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|Führendes Byte (im Zeichenfolgenkontext)|
|[ismbstrail, _ismbstrail_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|Nachfolgendes Byte (im Zeichenfolgenkontext)|
|[_mbbtype, _mbbtype_l](../c-runtime-library/reference/mbbtype-mbbtype-l.md)|Gibt den Bytetyp basierend auf dem vorherigen Byte zurück|
|[_mbsbtype, _mbsbtype_l](../c-runtime-library/reference/mbsbtype-mbsbtype-l.md)|Gibt den Bytetyp in der Zeichenfolge zurück|
|[mbsinit](../c-runtime-library/reference/mbsinit.md)|Verfolgt den Zustand einer Multibytezeichen-Konvertierung.|

Das in **limits.h> definierte Makro** MB_LEN_MAX\< erweitert auf die maximale Länge in Bytes, die ein Multibytezeichen aufweisen kann. Das in **stdlib.h> definierte** MB_CUR_MAX\< erweitert auf die maximale Länge in Bytes eines beliebigen Multibytezeichens im aktuellen Gebietsschema.

## <a name="see-also"></a>Weitere Informationen

[Universelle C-Laufzeitroutinen nach Kategorie](../c-runtime-library/run-time-routines-by-category.md)
