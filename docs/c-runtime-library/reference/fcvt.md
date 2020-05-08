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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 2ca8a7fcd58e91ffa8982f30117b09af587d96cf
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920187"
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

*31.12.2012*<br/>
Zeiger auf die gespeicherte Position der Dezimalstelle.

*Gebärden*<br/>
Zeiger auf den gespeicherten Zeichen-Indikator.

## <a name="return-value"></a>Rückgabewert

**_fcvt** gibt einen Zeiger auf die Zeichenfolge zurück, bei einem Fehler **null** .

## <a name="remarks"></a>Hinweise

Die **_fcvt** -Funktion konvertiert eine Gleit Komma Zahl in eine NULL terminierte Zeichenfolge. Der *value* -Parameter ist die zu konvertierende Gleit Komma Zahl. **_fcvt** speichert die Ziffern des *Werts* als Zeichenfolge und fügt ein NULL-Zeichen (' \ 0 ') an. Der *count* -Parameter gibt die Anzahl der Ziffern an, die nach dem Dezimaltrennzeichen gespeichert werden sollen. Überschüssige Ziffern werden auf *Anzahl* von Stellen gerundet. Wenn weniger als *zählungs* Ziffern vorhanden sind, wird die Zeichenfolge mit Nullen aufgefüllt.

Die Gesamtanzahl der von **_fcvt** zurückgegebenen Ziffern wird **_CVTBUFSIZE**nicht überschreiten.

In der Zeichenfolge werden nur Ziffern gespeichert. Die Position des Dezimal Trennzeichens und das Vorzeichen des *Werts* können aus *Dec* abgerufen und nach dem-Befehl signiert werden. Der *Dec* -Parameter verweist auf einen ganzzahligen Wert. dieser ganzzahlige Wert gibt die Position des Dezimal Trennzeichens in Bezug auf den Anfang der Zeichenfolge an. Der Wert null oder ein negativer ganzzahliger Wert geben an, dass sich die Dezimalstelle links neben der ersten Ziffer befindet. Das Parameter *Vorzeichen* verweist auf eine Ganzzahl, die das Vorzeichen des *Werts*angibt. Die Ganzzahl wird auf 0 festgelegt, wenn *value* positiv ist und auf eine Zahl ungleich 0 (null) festgelegt ist, wenn der *Wert* negativ ist.

Der Unterschied zwischen **_ecvt** und **_fcvt** ist die Interpretation des *count* -Parameters. **_ecvt** interpretiert *count* als die Gesamtanzahl der Ziffern in der Ausgabe Zeichenfolge, während **_fcvt** die *Anzahl als Anzahl* der Ziffern nach dem Dezimaltrennzeichen interpretiert.

**_ecvt** und **_fcvt** verwenden einen einzelnen statisch zugeordneten Puffer für die Konvertierung. Jeder Aufruf einer dieser Routinen zerstört das Ergebnis des vorherigen Aufrufs.

Diese Funktion überprüft ihre Parameter. Wenn *Dec* oder *Sign* **null**ist oder *count* 0 ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, wird **errno** auf **EINVAL** festgelegt, und es wird **null** zurückgegeben.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

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

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_gcvt](gcvt.md)<br/>
