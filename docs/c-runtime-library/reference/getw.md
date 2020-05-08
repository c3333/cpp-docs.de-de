---
title: _getw
ms.date: 4/2/2020
api_name:
- _getw
- _o__getw
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getw
helpviewer_keywords:
- _getw function
- integers, getting from streams
- getw function
ms.assetid: ef75facc-b84e-470f-9f5f-8746c90822a0
ms.openlocfilehash: fc1dfcc54259dfe40d2fc37be1e1c0ab63ab7c4a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916314"
---
# <a name="_getw"></a>_getw

Ruft eine Ganzzahl aus einem Stream ab.

## <a name="syntax"></a>Syntax

```C
int _getw(
   FILE *stream
);
```

### <a name="parameters"></a>Parameter

*Streich*<br/>
Zeiger zur **FILE**-Struktur.

## <a name="return-value"></a>Rückgabewert

**_getw** gibt den gelesenen ganzzahligen Wert zurück. Der Rückgabewert von **EOF** gibt entweder einen Fehler oder ein Dateiende an. Da der **EOF** -Wert auch ein berechtigter ganzzahliger Wert ist, verwenden Sie " **feof** " oder " **ferror** ", um eine dateiendebedingung oder eine Fehlerbedingung zu überprüfen. Wenn *stream* der Stream **null**ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, wird **errno** auf **EINVAL** festgelegt, und die Funktion gibt **EOF**zurück.

## <a name="remarks"></a>Hinweise

Die **_getw** -Funktion liest den nächsten binären Wert vom Typ " **int** " aus der Datei, die dem *Stream* zugeordnet ist, und erhöht den zugeordneten Dateizeiger (sofern vorhanden), um auf das nächste ungelesene Zeichen zu zeigen. **_getw** nimmt keine besondere Ausrichtung von Elementen im Stream an. Probleme beim Portieren können mit **_getw** auftreten, da die Größe des **int** -Typs und die Reihenfolge von Bytes innerhalb des Typs " **int** " zwischen Systemen unterschiedlich sind.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_getw**|\<stdio.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_getw.c
// This program uses _getw to read a word
// from a stream, then performs an error check.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   FILE *stream;
   int i;

   if( fopen_s( &stream, "crt_getw.txt", "rb" ) )
      printf( "Couldn't open file\n" );
   else
   {
      // Read a word from the stream:
      i = _getw( stream );

      // If there is an error...
      if( ferror( stream ) )
      {
         printf( "_getw failed\n" );
         clearerr_s( stream );
      }
      else
         printf( "First data word in file: 0x%.4x\n", i );
      fclose( stream );
   }
}
```

### <a name="input-crt_getwtxt"></a>Eingabe: crt_getw.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Output

```Output
First data word in file: 0x656e694c
```

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[_putw](putw.md)<br/>
