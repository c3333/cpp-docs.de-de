---
title: _ismbc-Routinen
ms.date: 11/04/2016
api_location:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ismbc
helpviewer_keywords:
- ismbc routines
- _ismbc routines
ms.assetid: b8995391-7857-4ac3-9a1e-de946eb4464d
ms.openlocfilehash: 056cc4bc5344ee8833b3f6e645616657f1958897
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839360"
---
# <a name="_ismbc-routines"></a>_ismbc-Routinen

Jede **_ismbc**-Routine prüft ein angegebenes Multibytezeichen `c` auf eine bestimmte Bedingung.

:::row:::
   :::column span="":::
      [_ismbcalnum, _ismbcalnum_l, _ismbcalpha, _ismbcalpha_l, _ismbcdigit](../c-runtime-library/reference/ismbcalnum-functions.md)\
      [_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)\
      [_ismbcgraph, _ismbcgraph_l, _ismbcprint, _ismbcprint_l, _ismbcpunct, _ismbcpunct_l, _ismbcblank, _ismbcblank_l, _ismbcspace](../c-runtime-library/reference/ismbcgraph-functions.md)\
      [_ismbclegal, _ismbclegal_l _ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)\
      [_ismbchira, _ismbchira_l _ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)\
      [_ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)
   :::column-end:::
:::row-end:::

## <a name="remarks"></a>Bemerkungen

Das Testergebnis jeder **_ismbc**-Routine hängt von der gültigen Multibyte-Codepage ab. Multibyte-Codepages verfügen über Einzelbytebuchstaben. Standardmäßig wird die Multibyte-Codepage auf die Standard-ANSI-Codepage des Systems festgelegt, die vom Betriebssystem beim Programmstart abgerufen wird. Sie können die verwendete Multibyte-Codepage mit [_getmbcp](../c-runtime-library/reference/getmbcp.md) oder [_setmbcp](../c-runtime-library/reference/setmbcp.md) abfragen bzw. ändern.

Der Ausgabewert ist von der `LC_CTYPE`-Kategorieeinstellung des Gebietsschemas betroffen; weitere Informationen finden Sie unter [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). Die Versionen dieser Funktionen ohne das **_l**-Suffix verwenden das aktuelle Gebietsschema für dieses vom Gebietsschema abhängige Verhalten; die Versionen mit dem **_l**-Suffix sind beinahe identisch, verwenden jedoch stattdessen den ihnen übergebenen Gebietsschemaparameter.

|-Routine zurückgegebener Wert|Testbedingung|Beispiel für Codepage 932|
|-------------|--------------------|---------------------------|
|[_ismbcalnum, _ismbcalnum_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Alphanumerisch|Gibt nur dann einen Wert ungleich Null zurück, wenn `c` eine Einzelbytedarstellung eines englischen ASCII-Buchstabens ist: siehe Beispiele für `_ismbcdigit` und `_ismbcalpha`.|
|[_ismbcalpha, _ismbcalpha_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Alphabetisch|Gibt nur dann einen Wert ungleich 0 (null) zurück, wenn `c` eine Einzelbytedarstellung eines englischen ASCII-Buchstabens ist: weitere Informationen finden Sie in den Beispielen für `_ismbcupper` und `_ismbclower`; oder ein Katakana-Buchstabe: 0xA6<=`c`<=0xDF.|
|[_ismbcdigit, _ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Ziffer|Gibt nur dann einen Wert ungleich null zurück, wenn `c` eine Einzelbytedarstellung einer ASCII-Ziffer ist: 0x30=<`c`<=0x39.|
|[_ismbcgraph, _ismbcgraph_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Graphic|Gibt einen Wert ungleich 0 (null) zurück, wenn `c` eine Einzelbytedarstellung jedes beliebigen ASCII- oder druckbaren Katakana-Zeichens außer eines Leerzeichens ( ) ist. Mehr dazu finden Sie in den Beispielen zu `_ismbcdigit`, `_ismbcalpha` und `_ismbcpunct`.|
|[_ismbclegal, _ismbclegal_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Gültiges Multibytezeichen|Gibt einen Wert ungleich 0 (null) nur dann zurück, wenn das erste Byte von `c` im Bereich 0x81-0x9F oder 0xE0-0xFC liegt, während das zweite Byte im Bereich 0x40-0x7E oder 0x80-FC liegt.|
|[_ismbclower, _ismbclower_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Kleinbuchstaben alphabetisch|Gibt nur dann einen Wert ungleich null zurück, wenn `c` eine Einzelbytedarstellung eines englischen ASCII-Kleinbuchstabens ist: 0x61<=`c`<=0x7A.|
|[_ismbcprint, _ismbcprint_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Druckbar|Gibt nur dann einen Wert ungleich 0 (null) zurück, wenn `c` eine Einzelbytedarstellung eines beliebigen druckbaren ASCII- oder Katakana-Zeichens einschließlich Leerzeichen ( ) ist: siehe Beispiele für `_ismbcspace`, `_ismbcdigit`, `_ismbcalpha` und `_ismbcpunct`.|
|[_ismbcpunct, _ismbcpunct_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Interpunktion|Gibt einen Wert ungleich 0 (null) zurück, wenn `c` eine Einzelbytedarstellung jedes beliebigen ASCII- oder Katakana-Interpunktionszeichens ist.|
|[_ismbcblank, _ismbcblank_l,](../c-runtime-library/reference/ismbcgraph-functions.md)|Leerzeichen oder horizontaler Tabulator|Gibt nur dann einen Wert ungleich 0 (null) zurück, wenn `c` eine Einzelbytedarstellung eines Leerzeichens oder eines horizontalen Tabstoppzeichens ist: `c` = 0x20 oder `c` = 0x09.|
|[_ismbcspace, _ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Leerraum|Gibt nur dann einen Wert ungleich 0 (null) zurück, wenn `c` ein Leerzeichen ist: `c`=0x20 oder 0x09<=`c`<=0x0D.|
|[_ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Multibytesymbol|Gibt nur dann einen Wert ungleich null zurück, wenn 0x8141<=`c`<=0x81AC ist.|
|[_ismbcupper, _ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Großbuchstaben alphabetisch|Gibt nur dann einen Wert ungleich null zurück, wenn `c` eine Einzelbytedarstellung eines englischen ASCII-Großbuchstabens ist: 0x41<=`c`<=0x5A.|

**Codepage 932-spezifisch**

Die folgenden Routinen gelten speziell für Codepage 932.

|-Routine zurückgegebener Wert|Testbedingung (nur Codepage 932)|
|-------------|-------------------------------------------|
|[_ismbchira, _ismbchira_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Doppelbyte Hiragana: 0x829F<=`c`<=0x82F1.|
|[_ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Doppelbyte Katakana: 0x8340<=`c`<=0x8396.|
|[_ismbcl0, _ismbcl0_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS, nicht Kanji: 0x8140<=`c`<= 0x889E.|
|[_ismbcl1, _ismbcl1_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS, Ebene 1: 0x889F<=`c`<= 0x9872.|
|[_ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS, Ebene 2: 0x989F<=`c`<=0xEA9E|

`_ismbcl0`, `_ismbcl1` und `_ismbcl2` überprüfen, ob der angegebene Wert `c` den in der vorigen Tabelle beschriebenen Testbedingungen entspricht. Es wird jedoch nicht überprüft, ob `c` ein gültiges Multibytezeichen ist. Wenn das untere Byte in den Bereichen 0x00–0x3F, 0x7F oder 0xFD–0xFF liegt, geben diese Funktionen einen Wert ungleich 0 (null) zurück. Dies gibt an, dass das Zeichen die Testbedingung erfüllt. Verwenden Sie [_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md), um zu prüfen, ob das Multibytezeichen definiert ist.

**Ende Codepage 932-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Zeichen Klassifizierung](../c-runtime-library/character-classification.md)<br/>
[is-, ISW-Routinen](../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb Routinen](../c-runtime-library/ismbb-routines.md)
