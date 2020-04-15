---
title: _fcvt
ms.date: 4/2/2020
api_name:
- _fcvt
- _o__fcvt
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
- _fcvt
helpviewer_keywords:
- converting floating point, to strings
- _fcvt function
- floating-point functions, converting number to string
- fcvt function
- floating-point functions
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
ms.openlocfilehash: a017ed58b962520793d5b10b088793dbc9b8a83d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347429"
---
# <a name="_fcvt"></a>_fcvt

Konvertiert eine Gleitkommazahl in eine Zeichenfolge. Es ist eine sicherere Version dieser Funktion verfügbar. Informationen dazu finden Sie unter [_fcvt_s](fcvt-s.md).

## <a name="syntax"></a>Syntax

```C
char *_fcvt(
   double value,
   int count,
   int *dec,
   int *sign
);
```

### <a name="parameters"></a>Parameter

*value*<br/>
Zu konvertierende Zahl.

*count*<br/>
Anzahl der Ziffern nach dem Dezimaltrennzeichen.

*dec*<br/>
Zeiger auf die gespeicherte Position der Dezimalstelle.

*Zeichen*<br/>
Zeiger auf den gespeicherten Zeichen-Indikator.

## <a name="return-value"></a>Rückgabewert

**_fcvt** gibt einen Zeiger auf die Zeichenfolge der Ziffern, **NULL** bei Fehler.

## <a name="remarks"></a>Bemerkungen

Die **_fcvt-Funktion** konvertiert eine Gleitkommazahl in eine null-terminierte Zeichenfolge. Der *Wertparameter* ist die zu konvertierende Gleitkommazahl. **_fcvt** speichert die *Werteziffern* als Zeichenfolge und fügt ein Nullzeichen an . Der *Parameter count* gibt die Anzahl der Ziffern an, die nach dem Dezimaltrennzeichen gespeichert werden sollen. Überschüssige Ziffern werden abgerundet, um Orte zu *zählen.* Wenn es weniger als *Genauigkeitsziffern* zählen, wird die Zeichenfolge mit Nullen aufgepolstert.

Die Gesamtzahl der von **_fcvt** zurückgegebenen Ziffern darf **_CVTBUFSIZE**nicht überschreiten.

In der Zeichenfolge werden nur Ziffern gespeichert. Die Position des Dezimalkommas und das Vorzeichen des *Wertes* können von *dec* und Zeichen nach dem Aufruf erhalten werden. Der *Parameter dec* zeigt auf einen Ganzzahlwert; Dieser ganzzahlige Wert gibt die Position des Dezimalkommas in Bezug auf den Anfang der Zeichenfolge an. Der Wert null oder ein negativer ganzzahliger Wert geben an, dass sich die Dezimalstelle links neben der ersten Ziffer befindet. Das *Parameterzeichen* zeigt auf eine ganze Zahl, die das Vorzeichen des *Werts*angibt. Die ganze Zahl wird auf 0 gesetzt, wenn *der Wert* positiv ist, und wird auf eine Zahl ungleich Null gesetzt, wenn *der Wert* negativ ist.

Der Unterschied zwischen **_ecvt** und **_fcvt** liegt in der Interpretation des *Zählparameters.* **_ecvt** interpretiert *die Anzahl* als die Gesamtzahl der Ziffern in der Ausgabezeichenfolge, während **_fcvt** die *Anzahl* der Ziffern nach dem Dezimaltrennzeichen interpretiert.

**_ecvt** und **_fcvt** einen einzelnen statisch zugewiesenen Puffer für die Konvertierung verwenden. Jeder Aufruf einer dieser Routinen zerstört das Ergebnis des vorherigen Aufrufs.

Diese Funktion überprüft ihre Parameter. Wenn *dec* oder *sign* **NULL**oder *count* is 0 ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, wird **errno** auf **EINVAL** gesetzt und **NULL** zurückgegeben.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**_fcvt**|\<stdlib.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_fcvt.c
// compile with: /W3
// This program converts the constant
// 3.1415926535 to a string and sets the pointer
// buffer to point to that string.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int  decimal, sign;
   char *buffer;
   double source = 3.1415926535;

   buffer = _fcvt( source, 7, &decimal, &sign ); // C4996
   // Note: _fcvt is deprecated; consider using _fcvt_s instead
   printf( "source: %2.10f   buffer: '%s'   decimal: %d   sign: %d\n",
            source, buffer, decimal, sign );
}
```

```Output
source: 3.1415926535   buffer: '31415927'   decimal: 1   sign: 0
```

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_gcvt](gcvt.md)<br/>
