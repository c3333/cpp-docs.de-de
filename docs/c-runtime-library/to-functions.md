---
title: to-Funktionen
ms.date: 11/04/2016
api_location:
- msvcr120.dll
- msvcr90.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- To
helpviewer_keywords:
- to functions
- string conversion, to different characters
- string conversion, case
- lowercase, converting strings
- uppercase, converting strings
- case, converting
- characters, converting
ms.assetid: f636a4c6-8c9f-4be2-baac-064f9dbae300
ms.openlocfilehash: a54f20d6ae4dead5ba7c606fd28d456e96ff31d6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836077"
---
# <a name="to-functions"></a>to-Funktionen

Jede der **to**-Funktionen und ggf. das zugehörige Makro konvertiert ein einzelnes Zeichen in ein anderes Zeichen.

[__toascii](../c-runtime-library/reference/toascii-toascii.md)\
[ToLower, _tolower, towlower](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)\
[toupper, _toupper, towupper](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)

## <a name="remarks"></a>Bemerkungen

Es gibt folgende **to**-Funktionen und Makrokonvertierungen:

|-Routine zurückgegebener Wert|Makro|Beschreibung|
|-------------|-----------|-----------------|
|`__toascii`|`__toascii`|Konvertiert `c` in ASCII-Zeichen|
|`tolower`|`tolower`|Konvertiert `c` gegebenenfalls in Kleinbuchstaben|
|`_tolower`|`_tolower`|Konvertiert `c` in Kleinbuchstaben|
|`towlower`|Keine|Konvertiert `c` in entsprechende Breitzeichen-Kleinbuchstaben|
|`toupper`|`toupper`|Konvertiert `c` gegebenenfalls in Großbuchstaben|
|`_toupper`|`_toupper`|Konvertiert `c` in Großbuchstaben|
|`towupper`|Keine|Konvertiert c in entsprechende Breitzeichen-Kleinbuchstaben|

Um die Funktionsversionen der **to**-Routinen zu nutzen, die auch als Makros definiert sind, entfernen Sie entweder die Makrodefinitionen mit `#undef`-Direktiven, oder schließen Sie nicht CTYPE.H ein. Wenn Sie die Compileroption /Za wählen, verwendet der Compiler die Funktionsversion von `toupper` oder `tolower`. Deklarationen der Funktionen `toupper` und `tolower` sind in STDLIB.H enthalten.

Die Routine `__toascii` setzt alle außer die unteren 7 Bits von `c` auf 0, damit der konvertierte Wert ein Zeichen im ASCII-Zeichensatz darstellt. Wenn `c` bereits ein ASCII-Zeichen darstellt, bleibt `c` unverändert.

Die Routinen `tolower` und `toupper`:

- Hängen von der Kategorie `LC_CTYPE` des aktuellen Gebietsschemas ab (`tolower` ruft `isupper` auf und `toupper` ruft `islower` auf).

- Konvertieren `c`, wenn `c` einen konvertierbaren Buchstaben des entsprechenden Falls im aktuellen Gebietsschema darstellt und der entgegengesetzte Fall für dieses Gebietsschema vorhanden ist. Andernfalls bleibt `c` unverändert.

Die Routinen `_tolower` und `_toupper`:

- Sind vom Gebietsschema unabhängige, viel schnellere Versionen von `tolower` und **.**

- Kann nur verwendet werden, wenn **isascii (** `c` **)** und entweder **IsUpper (** `c` **)** oder **IsLower (** `c` **)** bzw. nicht NULL sind.

- Haben nicht definierte Ergebnisse, wenn `c` kein ASCII-Buchstabe des entsprechenden zu konvertierenden Falls ist.

Die Funktionen `towlower` und `towupper` geben nur eine konvertierte Kopie von `c` zurück, wenn beide der folgenden Bedingungen ungleich null sind. Andernfalls bleibt `c` unverändert.

- `c` ist ein Breitzeichen des entsprechenden Falls (d.h. für das `iswupper` oder **iswlower** ungleich null ist).

- Es gibt ein entsprechendes Breitzeichen des Zielfalls (d.h. für das `iswlower` oder **iswupper** ungleich null ist).

## <a name="example"></a>Beispiel

```c
// crt_toupper.c
/* This program uses toupper and tolower to
 * analyze all characters between 0x0 and 0x7F. It also
 * applies _toupper and _tolower to any code in this
 * range for which these functions make sense.
 */

#include <ctype.h>
#include <string.h>

char msg[] = "Some of THESE letters are Capitals.";
char *p;

int main( void )
{
   printf( "%s\n", msg );

   /* Reverse case of message. */
   for( p = msg; p < msg + strlen( msg ); p++ )
   {
      if( islower( *p ) )
         putchar( _toupper( *p ) );
      else if( isupper( *p ) )
         putchar( _tolower( *p ) );
      else
         putchar( *p );
   }
}
```

```Output
Some of THESE letters are Capitals.
sOME OF these LETTERS ARE cAPITALS.
```

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../c-runtime-library/data-conversion.md)<br/>
[Gebietsschema](../c-runtime-library/locale.md)<br/>
[is-, ISW-Routinen](../c-runtime-library/is-isw-routines.md)
