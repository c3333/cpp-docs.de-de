---
title: mbrtoc16, mbrtoc323
ms.date: 4/2/2020
api_name:
- mbrtoc16
- mbrtoc32
- _o_mbrtoc16
- _o_mbrtoc32
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrtoc16
- mbrtoc32
- uchar/mbrtoc16
- uchar/mbrtoc32
helpviewer_keywords:
- mbrtoc16 function
- mbrtoc32 function
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
ms.openlocfilehash: 91755d19eacf73f19700eed7fffbffc529d4e235
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340980"
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32

Übersetzt das erste UTF-8-Multibyte-Zeichen in einer Zeichenfolge in das entsprechende UTF-16- oder UTF-32-Zeichen.

## <a name="syntax"></a>Syntax

```C
size_t mbrtoc16(
   char16_t* destination,
   const char* source,
   size_t max_bytes,
   mbstate_t* state
);

size_t mbrtoc32(
   char32_t* destination,
   const char* source,
   size_t max_bytes,
   mbstate_t* state
);
```

### <a name="parameters"></a>Parameter

*Ziel*\
Zeiger auf die **char16_t** oder **char32_t** Äquivalent des zu konvertierenden UTF-8-Multibyte-Zeichens. Wenn null, speichert die Funktion keinen Wert.

*Quelle*\
Zeiger auf die zu konvertierende UTF-8-Multibyte-Zeichenfolge.

*max_bytes*\
Die maximale Anzahl von Bytes in der *Quelle,* die auf ein zu konvertierendes Zeichen untersucht werden soll. Dieses Argument sollte ein Wert zwischen einem und der Anzahl der Bytes sein, einschließlich eines beliebigen Nullabschlusses, der in *source*verbleibt.

*Staat*\
Zeiger auf ein **mbstate_t** Konvertierungsstatusobjekt, das zum Interpretieren der UTF-8-Multibyte-Zeichenfolge auf ein oder mehrere Ausgabezeichen verwendet wird.

## <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg den Wert der ersten dieser Bedingungen zurück, der unter dem aktuellen *Statuswert* gilt:

|Wert|Bedingung|
|-----------|---------------|
|0|Die nächsten *max_bytes* oder weniger zeichen konvertiert aus *der Quelle* entsprechen dem NULL Wide Zeichen, das ist der Wert gespeichert, wenn *Ziel* ist nicht null.<br /><br /> *Status* enthält den anfangs verschobenen Zustand.|
|Zwischen 1 und *max_bytes*, inklusive|Der zurückgegebene Wert ist die Anzahl der Bytes der *Quelle,* die ein gültiges Multibyte-Zeichen abschließen. Das konvertierte Breitzeichen wird gespeichert, wenn *das Ziel* nicht null ist.|
|-3|Das nächste breite Zeichen, das sich aus einem vorherigen Aufruf der Funktion ergibt, wurde im *Ziel* gespeichert, wenn *das Ziel* nicht null ist. Dieser Aufruf der Funktion verbraucht keine Bytes aus der *Quelle.*<br /><br /> Wenn *die Quelle* auf ein UTF-8-Multibyte-Zeichen verweist, für das mehr als ein breites Zeichen dargestellt werden muss (z. B. ein Ersatzzeichenpaar), wird der *Statuswert* aktualisiert, sodass der nächste Funktionsaufruf das zusätzliche Zeichen ausschreibt.|
|-2|Die nächsten *max_bytes* Bytes stellen ein unvollständiges, aber potenziell gültiges UTF-8-Multibyte-Zeichen dar. Im *Ziel*wird kein Wert gespeichert. Dieses Ergebnis kann auftreten, wenn *max_bytes* Null ist.|
|-1|Es ist ein Codierungsfehler aufgetreten. Die nächsten *max_bytes* oder weniger Bytes nicht zu einem vollständigen und gültigen UTF-8-Multibyte-Zeichen beitragen. Im *Ziel*wird kein Wert gespeichert.<br /><br /> **EILSEQ** wird in **errno** gespeichert, und der Umrechnungszustandswertstatus ist nicht angegeben. *state*|

## <a name="remarks"></a>Bemerkungen

Die **mbrtoc16-Funktion** liest bis zu *max_bytes* Bytes aus der *Quelle,* um das erste vollständige, gültige UTF-8-Multibyte-Zeichen zu finden, und speichert dann das entsprechende UTF-16-Zeichen im *Ziel*. Wenn das Zeichen mehr als ein UTF-16-Ausgabezeichen benötigt, z. B. ein Ersatzzeichenpaar, wird der *Statuswert* so festgelegt, dass das nächste UTF-16-Zeichen beim nächsten Aufruf von **mbrtoc16**im *Ziel* gespeichert wird. Die **mbrtoc32-Funktion** ist identisch, aber die Ausgabe wird als UTF-32-Zeichen gespeichert.

Wenn *source* null ist, geben diese Funktionen das Äquivalent eines `""` Aufrufs zurück, der mithilfe von Argumenten von **NULL** für *ziel*gemacht wurde (eine leere, null-terminierte Zeichenfolge) für *source*, und 1 für *max_bytes*. Die übergebenen Werte von *Ziel* und *max_bytes* werden ignoriert.

Wenn *die Quelle* nicht null ist, beginnt die Funktion am Anfang der Zeichenfolge und überprüft bis zu *max_bytes* Bytes, um die Anzahl der Bytes zu ermitteln, die erforderlich sind, um das nächste UTF-8-Multibyte-Zeichen abzuschließen, einschließlich aller Verschiebungssequenzen. Wenn die untersuchten Bytes ein gültiges und vollständiges UTF-8-Multibyte-Zeichen enthalten, konvertiert die Funktion das Zeichen in das entsprechende 16-Bit- oder 32-Bit-Breitzeichen oder Zeichen. Wenn *das Ziel* nicht null ist, speichert die Funktion das erste (und möglicherweise nur) Ergebniszeichen im Ziel. Wenn zusätzliche Ausgabezeichen erforderlich sind, wird ein Wert im *Zustand*gesetzt, sodass nachfolgende Aufrufe der Funktion die zusätzlichen Zeichen ausgeben und den Wert -3 zurückgeben. Wenn keine Ausgabezeichen mehr erforderlich sind, wird der *Status* auf den anfänglichen Verschiebungszustand festgelegt.

Um Nicht-UTF-8-Multibyte-Zeichen in UTF-16 LE-Zeichen zu konvertieren, verwenden Sie die Funktionen [mbrtowc](mbrtowc.md), [mbtowc oder _mbtowc_l.](mbtowc-mbtowc-l.md)

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|C-Header|C++-Header|
|--------------|--------------|------------------|
|**mbrtoc16**, **mbrtoc32**|\<uchar.h>|\<cuchar>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../compatibility.md).

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../data-conversion.md)\
[Locale](../locale.md)\
[Interpretation von Multibyte-Zeichen-Sequenzen](../interpretation-of-multibyte-character-sequences.md)\
[c16rtomb, c32rtomb](c16rtomb-c32rtomb1.md)\
[mbrtowc](mbrtowc.md)\
[mbsrtowcs](mbsrtowcs.md)\
[mbsrtowcs_s](mbsrtowcs-s.md)
