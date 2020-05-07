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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 0e3d5ceffa5adc9e9f6ba96cccb46a3fbcfca69a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919566"
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32

Übersetzt das erste UTF-8-Multibytezeichen in einer Zeichenfolge in das entsprechende UTF-16-oder UTF-32-Zeichen.

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

*entwickelt*\
Ein Zeiger auf die **char16_t** oder **char32_t** -Entsprechung des zu konvertierenden UTF-8-multibytezeichens. Wenn der Wert NULL ist, speichert die Funktion keinen Wert.

*Ausgangs*\
Zeiger auf die zu konvertierende UTF-8-Multibytezeichenfolge.

*max_bytes*\
Die maximale Anzahl von Bytes in der *Quelle* , die für ein zu konvertierendes Zeichen untersucht werden soll. Dieses Argument muss ein Wert zwischen 1 und der Anzahl von Bytes sein, einschließlich eines beliebigen null-Terminator, der in der *Quelle*verbleiben kann.

*Land*\
Zeiger auf ein **mbstate_t** Konvertierungs Zustands Objekt, mit dem die UTF-8-Multibytezeichenfolge mit einem oder mehreren Ausgabe Zeichen interpretiert wird.

## <a name="return-value"></a>Rückgabewert

Bei Erfolg wird der Wert der ersten dieser Bedingungen mit dem aktuellen *Zustands* Wert zurückgegeben:

|Value|Bedingung|
|-----------|---------------|
|0|Die nächsten *max_bytes* oder weniger Zeichen, die aus der *Quelle* konvertiert werden, entsprechen dem NULL-breit Zeichen. Hierbei handelt es sich um den Wert, der *bei nicht-* NULL-<br /><br /> *State* enthält den anfänglichen Verschiebungs Zustand.|
|Zwischen 1 und *max_bytes*, einschließlich|Der zurückgegebene Wert ist die Anzahl der Bytes der *Quelle* , die ein gültiges Multibytezeichen vervollständigen. Das konvertierte breit Zeichen wird gespeichert, wenn *Destination* nicht NULL ist.|
|-3|Das nächste breit Zeichen, das sich aus einem vorherigen Aufrufe der Funktion ergibt, wurde im *Ziel* gespeichert, wenn *Destination* nicht NULL ist. Von diesem Aufrufe der-Funktion werden keine Bytes aus der *Quelle* verwendet.<br /><br /> Wenn die *Quelle* auf ein UTF-8-Multibytezeichen verweist, für das mehr als ein breit Zeichen erforderlich ist (z. b. ein Ersatz Zeichenpaar), wird der *Zustands* Wert aktualisiert, sodass der nächste Funktions Aufrufer das zusätzliche Zeichen ausgibt.|
|-2|Die nächsten *max_bytes* Bytes stellen ein unvollständiges, aber potenziell gültiges UTF-8-Multibytezeichen dar. Es ist kein Wert im *Ziel*gespeichert. Dieses Ergebnis kann auftreten, wenn *max_bytes* 0 (null) ist.|
|-1|Es ist ein Codierungsfehler aufgetreten. Die nächsten *max_bytes* oder weniger Bytes tragen nicht zu einem kompletten und gültigen UTF-8-Multibytezeichen bei. Es ist kein Wert im *Ziel*gespeichert.<br /><br /> " **EILSEQ** " wird in " **errno** " gespeichert, und der *Status* Wert des Konvertierungs Zustands ist nicht angegeben.|

## <a name="remarks"></a>Hinweise

Die **mbrtoc16** -Funktion liest bis zu *max_bytes* Bytes aus der *Quelle* , um das erste komplette, gültige UTF-8-Multibytezeichen zu finden, und speichert dann das entsprechende UTF-16-Zeichen im *Ziel*. Wenn für das Zeichen mehr als ein UTF-16-Ausgabe Zeichen erforderlich ist (z. b. ein Ersatz Zeichenpaar), wird der *Zustands* Wert so festgelegt, dass beim nächsten **mbrtoc16**-Aufrufe das nächste UTF-16-Zeichen im *Ziel* gespeichert wird. Die **mbrtoc32** -Funktion ist identisch, die Ausgabe wird jedoch als UTF-32-Zeichen gespeichert.

Wenn *die Quelle* NULL ist, geben diese Funktionen das Äquivalent eines Aufrufes mit Argumenten **von NULL** für *Destination* `""` , (eine leere, mit NULL beendete Zeichenfolge) für die *Quelle*und 1 für *max_bytes*zurück. Die bestandenen Werte von *Destination* und *max_bytes* werden ignoriert.

Wenn die *Quelle* nicht NULL ist, beginnt die Funktion am Anfang der Zeichenfolge und untersucht bis zu *max_bytes* Byte, um die Anzahl der Bytes zu bestimmen, die erforderlich sind, um das nächste UTF-8-Multibytezeichen abzuschließen, einschließlich der Verschiebe Sequenzen. Wenn die untersuchten Bytes ein gültiges und ganzes UTF-8-Multibytezeichen enthalten, konvertiert die Funktion das Zeichen in das entsprechende 16-Bit-oder 32-Bit-breit Zeichen. Wenn *Destination* nicht NULL ist, speichert die Funktion das erste (und möglicherweise einzige) Ergebnis Zeichen im Ziel. Wenn zusätzliche Ausgabe Zeichen erforderlich sind, wird ein Wert im *Zustand*festgelegt, sodass nachfolgende Aufrufe der Funktion die zusätzlichen Zeichen ausgeben und den Wert-3 zurückgeben. Wenn keine weiteren Ausgabe Zeichen erforderlich sind, wird *State* auf den anfänglichen Verschiebungs Zustand festgelegt.

Um nicht-UTF-8-Multibytezeichen in UTF-16-Le-Zeichen zu konvertieren, verwenden Sie die Funktionen [mbrtowc](mbrtowc.md), [mbtowc oder _mbtowc_l](mbtowc-mbtowc-l.md) .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|C-Header|C++-Header|
|--------------|--------------|------------------|
|**mbrtoc16**, **mbrtoc32**|\<uchar.h>|\<cuchar>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../data-conversion.md)\
[Konfigurations](../locale.md)\
[Interpretation von Multibyte-Zeichensequenzen](../interpretation-of-multibyte-character-sequences.md)\
[c16rtomb, c32rtomb](c16rtomb-c32rtomb1.md)\
[mbrtowc](mbrtowc.md)\
[mbsrtowcs](mbsrtowcs.md)\
[mbsrtowcs_s](mbsrtowcs-s.md)
