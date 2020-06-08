---
title: printf, _printf_l, wprintf, _wprintf_l
ms.date: 11/04/2016
api_name:
- _printf_l
- wprintf
- _wprintf_l
- printf
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- printf
- _tprintf
- wprintf
helpviewer_keywords:
- printf function
- printf_l function
- tprintf_l function
- tprintf function
- _printf_l function
- wprintf function
- writing to console
- wprintf_l function
- _tprintf_l function
- _wprintf_l function
- _tprintf function
- printf function, format specification fields
- printf function, using
- formatted text [C++]
ms.assetid: 77a854ae-5b48-4865-89f4-f2dc5cf80f52
ms.openlocfilehash: 73de90667479fff647e399068f9b97453819d27c
ms.sourcegitcommit: fe146adb3a02872538637196bb3c45aeeeaaf5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84507052"
---
# <a name="printf-_printf_l-wprintf-_wprintf_l"></a>printf, _printf_l, wprintf, _wprintf_l

Druckt eine formatierte Ausgabe an den Standardausgabestream. Sicherere Versionen dieser Funktionen sind verfügbar. Informationen dazu finden Sie unter [printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](printf-s-printf-s-l-wprintf-s-wprintf-s-l.md).

## <a name="syntax"></a>Syntax

```C
int printf(
   const char *format [,
   argument]...
);
int _printf_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int wprintf(
   const wchar_t *format [,
   argument]...
);
int _wprintf_l(
   const wchar_t *format,
   locale_t locale [,
   argument]...
);
```

### <a name="parameters"></a>Parameter

*format*<br/>
Formatsteuerung

*argument*<br/>
Optionale Argumente.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Gibt die Anzahl gedruckter Zeichen oder einen negativen Wert zurück, wenn ein Fehler auftritt. Wenn *Format* **null**ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, gibt die Funktion-1 zurück und legt **errno** auf **EINVAL**fest. Wenn **EOF** (0xFFFF) im *Argument*gefunden wird, gibt die Funktion-1 zurück.

Weitere Informationen zu **errno** und Fehlercodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **printf** -Funktion formatiert und druckt eine Reihe von Zeichen und Werten für den **Standardausgabestream "stdout**". Wenn Argumente der *Format* Zeichenfolge folgen, muss die *Format* Zeichenfolge Spezifikationen enthalten, die das Ausgabeformat für die Argumente bestimmen. **printf** und [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md) Verhalten sich identisch, mit dem Unterschied, dass **printf** die Ausgabe in **stdout** und nicht in ein Ziel vom Typ **File**schreibt.

**wprintf** ist eine breit Zeichen Version von **printf**. *Format* ist eine Zeichenfolge mit breit Zeichen. **wprintf** und **printf** Verhalten sich identisch, wenn der Stream im ANSI-Modus geöffnet ist. die Ausgabe in einen Unicode-Stream wird von **printf** derzeit nicht unterstützt.

Die Versionen dieser Funktionen mit dem **_l** -Suffix sind beinahe identisch, verwenden jedoch den Gebiets Schema Parameter, der anstelle des aktuellen Thread Gebiets Schemas übergeben wurde.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_unicode definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tprintf**|**printf**|**printf**|**wprintf**|

Das *Format* -Argument besteht aus normalen Zeichen, Escapesequenzen und (wenn Argumente den *Format*Spezifikationen folgen). Die normalen Zeichen und Escapesequenzen werden in der Reihenfolge ihrer Darstellung in **stdout** kopiert. Zum Beispiel die Zeile:

```C
printf("Line one\n\t\tLine two\n");
```

erzeugt die Ausgabe:

```Output
Line one
        Line two
```

[Format Spezifikationen](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md) beginnen immer mit einem Prozentzeichen ( **%** ) und werden von links nach rechts gelesen. Wenn in **printf** die erste Format Spezifikation (falls vorhanden) erkannt wird, wird der Wert des ersten Arguments nach *Format* konvertiert und entsprechend ausgegeben. Mit der zweiten Formatspezifikation wird das zweite Argument konvertiert und ausgegeben, usw. Wenn es mehrere Argumente als Formatspezifikationen gibt, werden die zusätzlichen Argumente ignoriert. Die Ergebnisse sind nicht definiert, wenn nicht genügend Argumente für alle Formatspezifikationen vorhanden sind.

> [!IMPORTANT]
> Stellen Sie sicher, dass *format* keine benutzerdefinierte Zeichenfolge ist.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tprintf**|**printf**|**printf**|**wprintf**|
|**_tprintf_l**|**_printf_l**|**_printf_l**|**_wprintf_l**|

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**printf**, **_printf_l**|\<stdio.h>|
|**wprintf**, **_wprintf_l**|\<stdio.h> oder \<wchar.h>|

Die-Konsole wird in universelle Windows-Plattform-Apps (UWP) nicht unterstützt. Die Standarddaten Strom Handles, die der Konsole, **stdin**, **stdout**und **stderr**zugeordnet sind, müssen umgeleitet werden, bevor Sie von C-Lauf Zeitfunktionen in UWP-Apps verwendet werden können. Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

> [!IMPORTANT]
> Ab Windows 10, Version 2004 (Build 19041), druckt die- `printf` Funktions Familie genau darstellbare Gleit Komma Zahlen gemäß den IEEE 754-Regeln für die Rundung. In früheren Versionen von Windows würden genau darstellbare Gleit Komma Zahlen, die auf ' 5 ' enden, immer aufgerundet werden. IEEE 754 gibt an, dass Sie auf die nächstgelegene, gerade Ziffer (auch bekannt als "Banker ung") gerundet werden müssen. Beispielsweise sollten sowohl 1,5 als auch 2,5 auf 2 gerundet werden. Zuvor war 1,5 auf 2 und 2,5 auf 3 gerundet. Diese Änderung wirkt sich nur auf genau darstellbare Zahlen aus. Beispielsweise wird 2,35 (bei Darstellung im Arbeitsspeicher näher an 2.35000000000000008) weiter auf 2,4 gerundet. Durch die Rundung durch diese Funktionen wird nun auch der durch [fesetround](fegetround-fesetround2.md)festgelegte Gleit Komma Rundungs Modus respektiert. Zuvor wählte die Rundung immer FE_TONEAREST Verhalten. Diese Änderung betrifft nur Programme, die mit Visual Studio 2019, Version 16,2 und höher, erstellt wurden. Um das Legacy-Gleit Komma-Rundungs Verhalten zu verwenden, verknüpfen Sie mit [legacy_stdio_float_rounding. obj](../link-options.md).

## <a name="example"></a>Beispiel

```C
// crt_printf.c
// This program uses the printf and wprintf functions
// to produce formatted output.

#include <stdio.h>

int main( void )
{
   char     ch = 'h',
            *string = "computer";
   wchar_t  wch = L'w',
            *wstring = L"Unicode";
   int      count = -9234;
   double   fp = 251.7366;

   // Display integers
   printf( "Integer formats:\n"
           "   Decimal: %d  Justified: %.6d  "
           "Unsigned: %u\n",
           count, count, count, count );

   // Display decimals
   printf( "Decimal %d as:\n   Hex: %Xh  "
           "C hex: 0x%x  Octal: %o\n",
            count, count, count, count );

   // Display in different radixes
   printf( "Digits 10 equal:\n   Hex: %i  "
           "Octal: %i  Decimal: %i\n",
            0x10, 010, 10 );

   // Display characters
   printf("Characters in field (1):\n"
          "%10c%5hc%5C%5lc\n",
          ch, ch, wch, wch);
   wprintf(L"Characters in field (2):\n"
           L"%10C%5hc%5c%5lc\n",
           ch, ch, wch, wch);

   // Display strings
   printf("Strings in field (1):\n%25s\n"
          "%25.4hs\n   %S%25.3ls\n",
          string, string, wstring, wstring);
   wprintf(L"Strings in field (2):\n%25S\n"
           L"%25.4hs\n   %s%25.3ls\n",
           string, string, wstring, wstring);

   // Display real numbers
   printf("Real numbers:\n   %f %.2f %e %E\n",
          fp, fp, fp, fp );

   // Display pointer
   printf( "\nAddress as:   %p\n", &count);
}
```

### <a name="sample-output"></a>Beispielausgabe

```Output
Integer formats:
   Decimal: -9234  Justified: -009234  Unsigned: 4294958062
Decimal -9234 as:
   Hex: FFFFDBEEh  C hex: 0xffffdbee  Octal: 37777755756
Digits 10 equal:
   Hex: 16  Octal: 8  Decimal: 10
Characters in field (1):
         h    h    w    w
Characters in field (2):
         h    h    w    w
Strings in field (1):
                 computer
                     comp
   Unicode                      Uni
Strings in field (2):
                 computer
                     comp
   Unicode                      Uni
Real numbers:
   251.736600 251.74 2.517366e+002 2.517366E+002

Address as:   0012FF3C
```

## <a name="see-also"></a>Weitere Informationen:

[Syntax der Format Angabe: printf-und wprintf-Funktionen](../format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[Konfigurations](../../c-runtime-library/locale.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l](fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sprintf, _sprintf_l, Austausch printf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[vprintf-Funktionen](../../c-runtime-library/vprintf-functions.md)<br/>
[_set_output_format](../../c-runtime-library/set-output-format.md)<br/>
