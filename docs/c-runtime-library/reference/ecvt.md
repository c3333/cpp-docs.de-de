---
title: _ecvt
ms.date: 4/2/2020
api_name:
- _ecvt
- _o__ecvt
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
- _ecvt
helpviewer_keywords:
- _ecvt function
- numbers, converting
- converting double numbers
- ecvt function
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
ms.openlocfilehash: 5e1760d5c68e650f6fbf44866d4e368b9d6233b6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348024"
---
# <a name="_ecvt"></a>_ecvt

Konvertiert eine **doppelte** Zahl in eine Zeichenfolge. Es ist eine sicherere Version dieser Funktion verfügbar. Informationen dazu finden Sie unter [_ecvt_s](ecvt-s.md).

## <a name="syntax"></a>Syntax

```C
char *_ecvt(
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
Anzahl der gespeicherten Ziffern.

*dec*<br/>
Gespeicherte Position der Dezimalstelle.

*Zeichen*<br/>
Vorzeichen der konvertierten Zahl.

## <a name="return-value"></a>Rückgabewert

**_ecvt** gibt einen Zeiger auf die Zeichenfolge der Ziffern zurück. **NULL,** wenn ein Fehler aufgetreten ist.

## <a name="remarks"></a>Bemerkungen

Die **_ecvt-Funktion** konvertiert eine Gleitkommazahl in eine Zeichenfolge. Der *Wertparameter* ist die zu konvertierende Gleitkommazahl. Diese Funktion speichert bis zu *zählenziffern* *wertals* Zeichenfolge und fügt ein Nullzeichen an (''''). Wenn die Anzahl der Ziffern im *Wert* die *Anzahl*überschreitet, wird die Ziffer niedriger Ordnung gerundet. Wenn weniger als *Zählziffern* vorhanden sind, wird die Zeichenfolge mit Nullen aufgepolstert.

Die Gesamtzahl der von **_ecvt** zurückgegebenen Ziffern darf **_CVTBUFSIZE**nicht überschreiten.

In der Zeichenfolge werden nur Ziffern gespeichert. Die Position des Dezimalkommas und das Vorzeichen des *Wertes* können von *dec* und *Zeichen* nach dem Aufruf erhalten werden. Der *Parameter dec* zeigt auf einen Ganzzahlwert, der die Position des Dezimalkommas in Bezug auf den Anfang der Zeichenfolge angibt. Der Wert 0 oder ein negativer Integer-Wert geben an, dass sich die Dezimalstelle links neben der ersten Ziffer befindet. Der *Vorzeichenparameter* zeigt auf eine ganze Zahl, die das Vorzeichen der konvertierten Zahl angibt. Wenn der Integer-Wert 0 ist, ist die Zahl positiv. Andernfalls ist die Zahl negativ.

Der Unterschied zwischen **_ecvt** und **_fcvt** liegt in der Interpretation des *Zählparameters.* **_ecvt** interpretiert *die Anzahl* als die Gesamtzahl der Ziffern in der Ausgabezeichenfolge, während **_fcvt** die *Anzahl* der Ziffern nach dem Dezimaltrennzeichen interpretiert.

**_ecvt** und **_fcvt** einen einzelnen statisch zugewiesenen Puffer für die Konvertierung verwenden. Jeder Aufruf dieser Routinen zerstört das Ergebnis des vorherigen Aufrufs.

Diese Funktion überprüft ihre Parameter. Wenn *dec* oder *sign* **NULL**oder *count* is 0 ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, wird **errno** auf **EINVAL** gesetzt und **NULL** zurückgegeben.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**_ecvt**|\<stdlib.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_ecvt.c
// compile with: /W3
// This program uses _ecvt to convert a
// floating-point number to a character string.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int     decimal,   sign;
   char    *buffer;
   int     precision = 10;
   double  source = 3.1415926535;

   buffer = _ecvt( source, precision, &decimal, &sign ); // C4996
   // Note: _ecvt is deprecated; consider using _ecvt_s instead
   printf( "source: %2.10f   buffer: '%s'  decimal: %d  sign: %d\n",
           source, buffer, decimal, sign );
}
```

```Output
source: 3.1415926535   buffer: '3141592654'  decimal: 1  sign: 0
```

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
