---
title: scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l
ms.date: 03/26/2019
api_name:
- wscanf_s
- _wscanf_s_l
- scanf_s
- _scanf_s_l
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
- wscanf_s
- _tscanf_s_l
- _wscanf_s_l
- scanf_s
- _tscanf_s
- _scanf_s_l
helpviewer_keywords:
- reading data [C++], from input streams
- buffers [C++], buffer overruns
- _scanf_s_l function
- _wscanf_s_l function
- tscanf_s_l function
- tscanf_s function
- scanf_s function
- data [C++], reading from input stream
- wscanf_s function
- _tscanf_s_l function
- _tscanf_s function
- scanf_s_l function
- formatted data [C++], from input streams
- wscanf_s_l function
- buffers [C++], avoiding overruns
ms.assetid: 42cafcf7-52d6-404a-80e4-b056a7faf2e5
ms.openlocfilehash: 8811bd0b6e4009cd6aba570e65d0687fab465614
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231363"
---
# <a name="scanf_s-_scanf_s_l-wscanf_s-_wscanf_s_l"></a>scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l

Liest formatierte Daten aus dem Standardeingabestream. Diese Versionen von [scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md) enthalten Sicherheitsverbesserungen, wie unter [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
int scanf_s(
   const char *format [,
   argument]...
);
int _scanf_s_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int wscanf_s(
   const wchar_t *format [,
   argument]...
);
int _wscanf_s_l(
   const wchar_t *format,
   locale_t locale [,
   argument]...
);
```

### <a name="parameters"></a>Parameter

*format*<br/>
Formatsteuerzeichenfolge.

*argument*<br/>
Optionale Argumente.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Felder zurück, die erfolgreich konvertiert und zugewiesen wurden. Der Rückgabewert enthält keine Felder, die gelesen, aber nicht zugewiesen wurden. Der Rückgabewert 0 gibt an, dass keine Felder zugewiesen wurden. Der Rückgabewert ist **EOF** für einen Fehler oder, wenn beim ersten Versuch, ein Zeichen zu lesen, das Dateiendezeichen oder das Zeichen foldezeichen gefunden wurde. Wenn *Format* ein **null** -Zeiger ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, geben **scanf_s** und **wscanf_s** **EOF** zurück und legen **errno** auf **EINVAL**fest.

Weitere Informationen zu diesen und anderen Fehlercodes finden Sie unter [errno, _doserrno, _sys_errlist, and _sys_nerr (errno, _doserrno, _sys_errlist und _sys_nerr)](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **scanf_s** -Funktion liest Daten aus dem Standardeingabestream ( **stdin**) und schreibt Sie in das- *Argument*. Jedes *Argument* muss ein Zeiger auf einen Variablentyp sein, der dem Typspezifizierer im- *Format*entspricht. Wenn der Kopiervorgang zwischen Zeichenfolgen ausgeführt wird, die sich überschneiden, ist das Verhalten nicht definiert.

**wscanf_s** ist eine breit Zeichen Version von **scanf_s**. Das *Format* Argument für **wscanf_s** ist eine Zeichenfolge mit breit Zeichen. **wscanf_s** und **scanf_s** Verhalten sich identisch, wenn der Stream im ANSI-Modus geöffnet ist. **scanf_s** unterstützt derzeit keine Eingaben aus einem Unicode-Stream.

Die Versionen dieser Funktionen mit dem **_l** -Suffix sind identisch, außer Sie verwenden den *locale* -Parameter anstelle des aktuellen Thread Gebiets Schemas.

Anders als bei **scanf** und **wscanf**erfordern **scanf_s** und **wscanf_s** , dass Sie Puffergrößen für einige Parameter angeben. Geben Sie die Größen für alle **c**-, **c**-, **s**-, **s**-oder String Control Set **[]** -Parameter an. Die Puffergröße in Zeichen wird als zusätzlicher Parameter übergeben. Sie folgt unmittelbar auf den Zeiger auf den Puffer oder die Variable. Wenn Sie z. b. eine Zeichenfolge lesen, wird die Puffergröße für diese Zeichenfolge wie folgt übermittelt:

```C
char s[10];
scanf_s("%9s", s, (unsigned)_countof(s)); // buffer size is 10, width specification is 9
```

Die Puffergröße schließt das Terminal NULL ein. Sie können ein Feld für die breiten Angabe verwenden, um sicherzustellen, dass das eingelesene Token in den Puffer passt. Wenn ein Token zu groß für die Anpassung ist, wird nichts in den Puffer geschrieben, es sei denn, es gibt eine Width-Angabe.

> [!NOTE]
> Der Size-Parameter ist vom Typ **`unsigned`** und nicht vom **size_t**. Verwenden Sie eine statische Umwandlung, um einen **size_t** Wert **`unsigned`** für 64-Bit-Buildkonfigurationen in zu konvertieren.

Der Puffergrößen Parameter beschreibt die maximale Anzahl von Zeichen, nicht Bytes. In diesem Beispiel stimmt die Breite des Puffer Typs nicht mit der Breite des Format Bezeichnern ab.

```C
wchar_t ws[10];
wscanf_s(L"%9S", ws, (unsigned)_countof(ws));
```

Der **S** -Format Bezeichner bedeutet, dass die Zeichenbreite, die der-Funktion unterstützt wird, als "Gegenstück" verwendet wird. Die Zeichenbreite ist ein einzelnes Byte, aber die Funktion unterstützt Doppelbyte Zeichen. In diesem Beispiel wird eine Zeichenfolge mit bis zu neun Einzel Byte Zeichen gelesen und in einen Doppelbyte-Zeichen Puffer eingefügt. Die Zeichen werden als Einzelbytewerte behandelt; die ersten zwei Zeichen werden in `ws[0]` gespeichert, die zweiten zwei Zeichen in `ws[1]` usw.

In diesem Beispiel wird ein einzelnes Zeichen gelesen:

```C
char c;
scanf_s("%c", &c, 1);
```

Wenn mehrere Zeichen für Zeichen folgen, die keine NULL-Werte sind, gelesen werden, werden ganze Zahlen für die breiten Angabe und die Puffergröße verwendet.

```C
char c[4];
scanf_s("%4c", c, (unsigned)_countof(c)); // not null terminated
```

Weitere Informationen finden Sie unter [scanf Width Specification (scanf-Breitenangabe)](../../c-runtime-library/scanf-width-specification.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tscanf_s**|**scanf_s**|**scanf_s**|**wscanf_s**|
|**_tscanf_s_l**|**_scanf_s_l**|**_scanf_s_l**|**_wscanf_s_l**|

Weitere Informationen finden Sie unter [Format Specification Fields: scanf and wscanf Functions (Formatspezifikationsfelder: Funktionen scanf und wscanf)](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**scanf_s** **_scanf_s_l**|\<stdio.h>|
|**wscanf_s** **_wscanf_s_l**|\<stdio.h> oder \<wchar.h>|

Die-Konsole wird in universelle Windows-Plattform-Apps (UWP) nicht unterstützt. Der Standardstream verarbeitet **stdin**, **stdout**und **stderr** und muss umgeleitet werden, bevor Sie von C-Lauf Zeitfunktionen in UWP-Apps verwendet werden können. Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_scanf_s.c
// This program uses the scanf_s and wscanf_s functions
// to read formatted input.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int      i,
            result;
   float    fp;
   char     c,
            s[80];
   wchar_t  wc,
            ws[80];

   result = scanf_s( "%d %f %c %C %s %S", &i, &fp, &c, 1,
                     &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );
   printf( "The number of fields input is %d\n", result );
   printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c,
           wc, s, ws);
   result = wscanf_s( L"%d %f %hc %lc %S %ls", &i, &fp, &c, 2,
                      &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );
   wprintf( L"The number of fields input is %d\n", result );
   wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp,
            c, wc, s, ws);
}
```

Dieses Programm generiert bei dieser Eingabe die folgende Ausgabe:

```Input
71 98.6 h z Byte characters
36 92.3 y n Wide characters
```

```Output
The number of fields input is 6
The contents are: 71 98.599998 h z Byte characters
The number of fields input is 6
The contents are: 36 92.300003 y n Wide characters
```

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[Gebietsschema](../../c-runtime-library/locale.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, Austausch printf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
