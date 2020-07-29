---
title: vscanf_s, vwscanf_s
ms.date: 11/04/2016
api_name:
- vscanf_s
- vwscanf_s
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
- _vtscanf_s
- vscanf_s
- vwscanf_s
ms.assetid: 23a1c383-5b01-4887-93ce-534a1e38ed93
ms.openlocfilehash: 9fb58e38362d709ef6d203c5602aa32727efa763
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215100"
---
# <a name="vscanf_s-vwscanf_s"></a>vscanf_s, vwscanf_s

Liest formatierte Daten aus dem Standardeingabestream. Diese Versionen von [vscanf, vwscanf](vscanf-vwscanf.md) enthalten Sicherheitserweiterungen, wie unter [Security Features in the CRT (Sicherheitserweiterungen in der CRT)](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
int vscanf_s(
   const char *format,
   va_list arglist
);
int vwscanf_s(
   const wchar_t *format,
   va_list arglist
);
```

### <a name="parameters"></a>Parameter

*format*<br/>
Formatsteuerzeichenfolge.

*Arglist*<br/>
Variablenargumentenliste.

## <a name="return-value"></a>Rückgabewert

Gibt die Anzahl von Feldern zurück, die erfolgreich konvertiert und zugewiesen wurden; der Rückgabewert umfasst keine Felder, die gelesen, aber nicht zugewiesen wurden. Ein Rückgabewert von 0 gibt an, dass keine Felder zugewiesen wurden. Der Rückgabewert ist **EOF** für einen Fehler oder, wenn beim ersten Versuch, ein Zeichen zu lesen, das Dateiendezeichen oder das Zeichen foldezeichen gefunden wird. Wenn *Format* ein **null** -Zeiger ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, geben **vscanf_s** und **vwscanf_s** **EOF** zurück und legen **errno** auf **EINVAL**fest.

Weitere Informationen zu diesen und anderen Fehlercodes finden Sie unter [errno, _doserrno, _sys_errlist, and _sys_nerr (errno, _doserrno, _sys_errlist und _sys_nerr)](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **vscanf_s** -Funktion liest Daten aus dem Standardeingabestream **stdin** und schreibt die Daten in die Speicherorte, die von der *Arglist* -Argumentliste angegeben werden. Jedes Argument in der Liste muss ein Zeiger auf eine Variable eines Typs sein, der einem Typspezifizierer im- *Format*entspricht. Wenn der Kopiervorgang zwischen Zeichenfolgen ausgeführt wird, die sich überschneiden, ist das Verhalten nicht definiert.

**vwscanf_s** ist eine breit Zeichen Version von **vscanf_s**. Das *Format* Argument für **vwscanf_s** ist eine Zeichenfolge mit breit Zeichen. **vwscanf_s** und **vscanf_s** Verhalten sich identisch, wenn der Stream im ANSI-Modus geöffnet ist. **vscanf_s** unterstützt keine Eingaben aus einem Unicode-Stream.

Im Gegensatz zu **vscanf** und **vwscanf**müssen für **vscanf_s** und **vwscanf_s** die Puffergröße für alle Eingabeparameter vom Typ **c**, **c**, **s**, **s**oder Zeichen folgen-Steuerungs Sätzen, die in **[]** eingeschlossen sind, angegeben werden. Die Puffergröße in Zeichen wird als zusätzlicher Parameter direkt nach dem Zeiger auf den Puffer oder die Variable übergeben. Die Puffergröße in Zeichen für eine **`wchar_t`** Zeichenfolge entspricht nicht der Größe in Bytes.

Die Puffergröße enthält das abschließende NULL-Zeichen. Sie können ein Feld für die Breitenangabe verwenden, um sicherzustellen, dass das eingelesene Token in den Puffer passt. Wenn kein Feld für die Breiteangabe verwendet wird und das eingelesen Token zu groß für den Puffer ist, wird nichts in diesen Puffer geschrieben.

> [!NOTE]
> Der *size* -Parameter ist vom Typ **`unsigned`** und nicht vom **size_t**.

Weitere Informationen finden Sie unter [scanf Width Specification (scanf-Breitenangabe)](../../c-runtime-library/scanf-width-specification.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vtscanf_s**|**vscanf_s**|**vscanf_s**|**vwscanf_s**|

Weitere Informationen finden Sie unter [Format Specification Fields: scanf and wscanf Functions (Formatspezifikationsfelder: Funktionen scanf und wscanf)](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**vscanf_s**|\<stdio.h>|
|**wscanf_s**|\<stdio.h> oder \<wchar.h>|

Die-Konsole wird in universelle Windows-Plattform-Apps (UWP) nicht unterstützt. Die Standarddaten Strom Handles, die der Konsole, **stdin**, **stdout**und **stderr**zugeordnet sind, müssen umgeleitet werden, bevor Sie von C-Lauf Zeitfunktionen in UWP-Apps verwendet werden können. Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_vscanf_s.c
// compile with: /W3
// This program uses the vscanf_s and vwscanf_s functions
// to read formatted input.

#include <stdio.h>
#include <stdarg.h>
#include <stdlib.h>

int call_vscanf_s(char *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vscanf_s(format, arglist);
    va_end(arglist);
    return result;
}

int call_vwscanf_s(wchar_t *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vwscanf_s(format, arglist);
    va_end(arglist);
    return result;
}

int main( void )
{
    int   i, result;
    float fp;
    char  c, s[81];
    wchar_t wc, ws[81];
    result = call_vscanf_s("%d %f %c %C %s %S", &i, &fp, &c, 1,
                           &wc, 1, s, _countof(s), ws, _countof(ws) );
    printf( "The number of fields input is %d\n", result );
    printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c, wc, s, ws);
    result = call_vwscanf_s(L"%d %f %hc %lc %S %ls", &i, &fp, &c, 2,
                            &wc, 1, s, _countof(s), ws, _countof(ws) );
    wprintf( L"The number of fields input is %d\n", result );
    wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp, c, wc, s, ws);
}
```

Wenn diesem Programm die Eingabe aus dem Beispiel übergeben wird, erzeugt es Folgendes:

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
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[vscanf, vwscanf](vscanf-vwscanf.md)<br/>
