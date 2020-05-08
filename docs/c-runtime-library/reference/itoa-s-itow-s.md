---
title: _itoa_s, _itow_s Funktionen
ms.date: 4/2/2020
api_name:
- _itoa_s
- _ltoa_s
- _ultoa_s
- _i64toa_s
- _ui64toa_s
- _itow_s
- _ltow_s
- _ultow_s
- _i64tow_s
- _ui64tow_s
- _o__i64toa_s
- _o__i64tow_s
- _o__itoa_s
- _o__itow_s
- _o__ltoa_s
- _o__ltow_s
- _o__ui64toa_s
- _o__ui64tow_s
- _o__ultoa_s
- _o__ultow_s
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _itoa_s
- _ltoa_s
- _ultoa_s
- _i64toa_s
- _ui64toa_s
- _itow_s
- _ltow_s
- _ultow_s
- _i64tow_s
- _ui64tow_s
- _itot_s
- _ltot_s
- _ultot_s
- _i64tot_s
- _ui64tot_s
- itoa_s
- ltoa_s
- ultoa_s
- i64toa_s
- ui64toa_s
- itow_s
- ltow_s
- ultow_s
- i64tow_s
- ui64tow_s
- itot_s
- ltot_s
- ultot_s
- i64tot_s
- ui64tot_s
helpviewer_keywords:
- _ui64toa_s function
- _itow_s function
- _i64tow_s function
- _itot_s function
- converting integers
- itow_s function
- i64toa_s function
- _ui64tow_s function
- integers, converting
- _i64tot_s function
- itoa_s function
- _itoa_s function
- ui64toa_s function
- i64tow_s function
- converting numbers, to strings
- _ui64tot_s function
- _i64toa_s function
ms.assetid: eb746581-bff3-48b5-a973-bfc0a4478ecf
ms.openlocfilehash: 5cc3706abd07e11c819d4b2d37ff89e9b9137a22
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916558"
---
# <a name="_itoa_s-_ltoa_s-_ultoa_s-_i64toa_s-_ui64toa_s-_itow_s--_ltow_s--_ultow_s-_i64tow_s-_ui64tow_s"></a>_itoa_s, _ltoa_s, _ultoa_s, _i64toa_s, _ui64toa_s, _itow_s, _ltow_s, _ultow_s, _i64tow_s

Konvertiert eine ganze Zahl in eine Zeichenfolge. Dies sind Versionen der [_itoa _itow Funktionen](itoa-itow.md) mit Sicherheitsverbesserungen, wie in [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md)beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t _itoa_s( int value, char * buffer, size_t size, int radix );
errno_t _ltoa_s( long value, char * buffer, size_t size, int radix );
errno_t _ultoa_s( unsigned long value, char * buffer, size_t size, int radix );
errno_t _i64toa_s( long long value, char *buffer,
   size_t size, int radix );
errno_t _ui64toa_s( unsigned long long value, char *buffer,
   size_t size, int radix );

errno_t _itow_s( int value, wchar_t *buffer,
   size_t size, int radix );
errno_t _ltow_s( long value, wchar_t *buffer,
   size_t size, int radix );
errno_t _ultow_s( unsigned long value, wchar_t *buffer,
   size_t size, int radix );
errno_t _i64tow_s( long long value, wchar_t *buffer,
   size_t size, int radix );
errno_t _ui64tow_s( unsigned long long value, wchar_t *buffer,
   size_t size, int radix
);

// These template functions are C++ only:
template <size_t size>
errno_t _itoa_s( int value, char (&buffer)[size], int radix );

template <size_t size>
errno_t _ltoa_s( long value, char (&buffer)[size], int radix );

template <size_t size>
errno_t _ultoa_s( unsigned long value, char (&buffer)[size], int radix );

template <size_t size>
errno_t _itow_s( int value, wchar_t (&buffer)[size], int radix );

template <size_t size>
errno_t _ltow_s( long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
errno_t _ultow_s( unsigned long value, wchar_t (&buffer)[size], int radix );
```

### <a name="parameters"></a>Parameter

*value*<br/>
Zu konvertierende Zahl.

*ert*<br/>
Ausgabepuffer, der das Ergebnis der Konvertierung enthält.

*size*<br/>
Größe des *Puffers* in Zeichen oder breit Zeichen.

*Basis*<br/>
Die Basis-oder numerische Basis, die zum Konvertieren des *Werts*verwendet werden soll, der im Bereich 2-36 liegen muss.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, ein Fehlercode, wenn ein Fehler auftritt. Wenn eine der folgenden Bedingungen zutrifft, ruft die Funktion einen ungültigen Parametertyphandler auf, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben.

### <a name="error-conditions"></a>Fehlerbedingungen

|value|Puffer|size|radix|Rückgabewert|
|-----------|------------|----------------------|-----------|------------|
|any|**Normal**|any|any|**Eingabe**|
|any|any|<=0|any|**Eingabe**|
|any|any|<= Länge der erforderlichen Ergebniszeichenfolge|any|**Eingabe**|
|any|any|any|*Basis* < 2 oder *Basis* > 36|**Eingabe**|

### <a name="security-issues"></a>Sicherheitsprobleme

Diese Funktionen können eine Zugriffsverletzung generieren, wenn der *Puffer* nicht auf einen gültigen Speicher verweist und nicht **null**ist, oder wenn die Länge des Puffers nicht lang genug ist, um die Ergebnis Zeichenfolge zu speichern.

## <a name="remarks"></a>Hinweise

Mit Ausnahme der Parameter und des Rückgabewerts haben die **_itoa_s** -und **_itow_s** Funktions Familien das gleiche Verhalten wie die entsprechenden weniger sicheren **_itoa** und **_itow** Versionen.

In C++ wird die Verwendung dieser Funktionen durch Vorlagenüberladungen vereinfacht; die Überladungen können automatisch Rückschlüsse auf die Pufferlänge ziehen (wodurch kein Größenargument mehr angegeben werden muss), und sie können automatisch die älteren, nicht sicheren Funktionen durch ihre neueren, sicheren Entsprechungen ersetzen. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Die Debug-Bibliotheksversionen dieser Funktionen füllen zunächst den Puffer mit "0xFE" auf. Um dieses Verhalten zu deaktivieren, verwenden Sie [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Die CRT umfasst bequeme Makros zum Definieren der Größe des Puffers, der zum Konvertieren des längsten möglichen Werts der einzelnen ganzzahligen Typen, einschließlich des NULL-Abschluss Zeichens und des Zeichen Zeichens, für mehrere allgemeine Basen erforderlich ist. Weitere Informationen finden Sie unter [Maximale Anzahl von Konvertierungs Makros](itoa-itow.md#maximum-conversion-count-macros).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_itot_s**|**_itoa_s**|**_itoa_s**|**_itow_s**|
|**_ltot_s**|**_ltoa_s**|**_ltoa_s**|**_ltow_s**|
|**_ultot_s**|**_ultoa_s**|**_ultoa_s**|**_ultow_s**|
|**_i64tot_s**|**_i64toa_s**|**_i64toa_s**|**_i64tow_s**|
|**_ui64tot_s**|**_ui64toa_s**|**_ui64toa_s**|**_ui64tow_s**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_itoa_s**, **_ltoa_s**, **_ultoa_s**, **_i64toa_s**, **_ui64toa_s**|\<stdlib.h>|
|**_itow_s**, **_ltow_s**, **_ultow_s**, **_i64tow_s**, **_ui64tow_s**|\<stdlib.h> oder \<wchar.h>|

Diese Funktionen sind Microsoft-spezifisch. Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Dieses Beispiel veranschaulicht die Verwendung einiger ganzzahliger Konvertierungs Funktionen. Beachten Sie, dass das [_countof](countof-macro.md) -Makro nur zum Ermitteln der Puffergröße verwendet werden kann, wenn die Array Deklaration für den Compiler sichtbar ist, nicht aber für Parameter, die in Zeiger abgeblendet sind.

```C
// crt_itoa_s.c
// Compile by using: cl /W4 crt_itoa_s.c
#include <stdlib.h>     // for _itoa_s functions, _countof, count macro
#include <stdio.h>      // for printf
#include <string.h>     // for strnlen

int main( void )
{
    char buffer[_MAX_U64TOSTR_BASE2_COUNT];
    int r;
    for ( r = 10; r >= 2; --r )
    {
        _itoa_s( -1, buffer, _countof(buffer), r );
        printf( "base %d: %s (%d chars)\n",
            r, buffer, strnlen(buffer, _countof(buffer)) );
    }
    printf( "\n" );
    for ( r = 10; r >= 2; --r )
    {
        _i64toa_s( -1LL, buffer, _countof(buffer), r );
        printf( "base %d: %s (%d chars)\n",
            r, buffer, strnlen(buffer, _countof(buffer)) );
    }
    printf( "\n" );
    for ( r = 10; r >= 2; --r )
    {
        _ui64toa_s( 0xffffffffffffffffULL, buffer, _countof(buffer), r );
        printf( "base %d: %s (%d chars)\n",
            r, buffer, strnlen(buffer, _countof(buffer)) );
    }
}
```

```Output
base 10: -1 (2 chars)
base 9: 12068657453 (11 chars)
base 8: 37777777777 (11 chars)
base 7: 211301422353 (12 chars)
base 6: 1550104015503 (13 chars)
base 5: 32244002423140 (14 chars)
base 4: 3333333333333333 (16 chars)
base 3: 102002022201221111210 (21 chars)
base 2: 11111111111111111111111111111111 (32 chars)

base 10: -1 (2 chars)
base 9: 145808576354216723756 (21 chars)
base 8: 1777777777777777777777 (22 chars)
base 7: 45012021522523134134601 (23 chars)
base 6: 3520522010102100444244423 (25 chars)
base 5: 2214220303114400424121122430 (28 chars)
base 4: 33333333333333333333333333333333 (32 chars)
base 3: 11112220022122120101211020120210210211220 (41 chars)
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)

base 10: 18446744073709551615 (20 chars)
base 9: 145808576354216723756 (21 chars)
base 8: 1777777777777777777777 (22 chars)
base 7: 45012021522523134134601 (23 chars)
base 6: 3520522010102100444244423 (25 chars)
base 5: 2214220303114400424121122430 (28 chars)
base 4: 33333333333333333333333333333333 (32 chars)
base 3: 11112220022122120101211020120210210211220 (41 chars)
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)
```

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[_itoa, _itow Funktionen](itoa-itow.md)<br/>
