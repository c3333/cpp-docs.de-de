---
title: _fgetchar, _fgetwchar
ms.date: 4/2/2020
api_name:
- _fgetchar
- _fgetwchar
- _o__fgetchar
- _o__fgetwchar
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
- fgetwchar
- _fgettchar
- _fgetchar
- _fgetwchar
- fgettchar
helpviewer_keywords:
- fgetwchar function
- _fgetchar function
- fgettchar function
- _fgetwchar function
- _fgettchar function
- standard input, reading from
- fgetchar function
ms.assetid: 8bce874c-701a-41a3-b1b2-feff266fb5b9
ms.openlocfilehash: 99febac7de2c2fa4e6587654e854b32b702d299e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232533"
---
# <a name="_fgetchar-_fgetwchar"></a>_fgetchar, _fgetwchar

Liest ein Zeichen aus **stdin**.

## <a name="syntax"></a>Syntax

```C
int _fgetchar( void );
wint_t _fgetwchar( void );
```

## <a name="return-value"></a>Rückgabewert

** \_ fgetchar** gibt das als gelesene Zeichen als zurück **`int`** oder gibt zurück `EOF` , um einen Fehler oder ein Dateiende anzugeben. ** \_ fgetwchar** gibt als [wint_t](../../c-runtime-library/standard-types.md)das breit Zeichen zurück, das dem gelesenen Zeichen entspricht, oder gibt zurück, `WEOF` um einen Fehler oder ein Dateiende anzugeben. Verwenden Sie für beide Funktionen **feof** oder **ferror** , um zwischen einem Fehler und einer dateiendebedingung zu unterscheiden.

## <a name="remarks"></a>Bemerkungen

Diese Funktionen lesen ein einzelnes Zeichen aus **stdin**. Die Funktion erhöht dann den zugeordneten Dateizeiger (sofern definiert), um auf das nächste Zeichen zu zeigen. Wenn der Stream am Dateiende ist, wird der Dateiende-Indikator für den Stream festgelegt.

**_fgetchar** entspricht `fgetc( stdin )` . Sie entspricht auch **GetChar**, wird jedoch nur als Funktion und nicht als Funktion und Makro implementiert. **_fgetwchar** ist die breit Zeichen Version von **_fgetchar**.

Diese Funktionen sind nicht dem ANSI-Standard kompatibel.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_fgettchar**|**_fgetchar**|**_fgetchar**|**_fgetwchar**|

## <a name="requirements"></a>Requirements (Anforderungen)

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**_fgetchar**|\<stdio.h>|
|**_fgetwchar**|\<stdio.h> oder \<wchar.h>|

Die-Konsole wird in universelle Windows-Plattform-Apps (UWP) nicht unterstützt. Die Standarddaten Strom Handles, die der Konsole –**stdin**, **stdout**und **stderr**– zugeordnet sind, müssen umgeleitet werden, bevor Sie von C-Lauf Zeitfunktionen in UWP-Apps verwendet werden können. Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_fgetchar.c
// This program uses _fgetchar to read the first
// 80 input characters (or until the end of input)
// and place them into a string named buffer.
//

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char buffer[81];
   int  i, ch;

   // Read in first 80 characters and place them in "buffer":
   ch = _fgetchar();
   for( i=0; (i < 80 ) && ( feof( stdin ) == 0 ); i++ )
   {
      buffer[i] = (char)ch;
      ch = _fgetchar();
   }

   // Add null to end string
   buffer[i] = '\0';
   printf( "%s\n", buffer );
}
```

```Output

      Line one.
Line two.Line one.
Line two.
```

## <a name="see-also"></a>Weitere Informationen

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
