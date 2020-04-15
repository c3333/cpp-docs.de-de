---
title: _itoa, _itow Funktionen
ms.date: 4/2/2020
api_name:
- itoa
- _itoa
- ltoa
- _ltoa
- ultoa
- _ultoa
- _i64toa
- _ui64toa
- _itow
- _ltow
- _ultow
- _i64tow
- _ui64tow
- _o__i64toa
- _o__i64tow
- _o__itoa
- _o__itow
- _o__ltoa
- _o__ltow
- _o__ui64toa
- _o__ui64tow
- _o__ultoa
- _o__ultow
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _itoa
- _ltoa
- _ultoa
- _i64toa
- _ui64toa
- _itow
- _ltow
- _ultow
- _i64tow
- _ui64tow
- itoa
- ltoa
- ultoa
- i64toa
- ui64toa
- itow
- ltow
- ultow
- i64tow
- ui64tow
- itot
- _itot
- ltot
- _ltot
- ultot
- _ultot
- i64tot
- _i64tot
- ui64tot
- _ui64tot
- _MAX_ITOSTR_BASE16_COUNT
- _MAX_ITOSTR_BASE10_COUNT
- _MAX_ITOSTR_BASE8_COUNT
- _MAX_ITOSTR_BASE2_COUNT
- _MAX_LTOSTR_BASE16_COUNT
- _MAX_LTOSTR_BASE10_COUNT
- _MAX_LTOSTR_BASE8_COUNT
- _MAX_LTOSTR_BASE2_COUNT
- _MAX_ULTOSTR_BASE16_COUNT
- _MAX_ULTOSTR_BASE10_COUNT
- _MAX_ULTOSTR_BASE8_COUNT
- _MAX_ULTOSTR_BASE2_COUNT
- _MAX_I64TOSTR_BASE16_COUNT
- _MAX_I64TOSTR_BASE10_COUNT
- _MAX_I64TOSTR_BASE8_COUNT
- _MAX_I64TOSTR_BASE2_COUNT
- _MAX_U64TOSTR_BASE16_COUNT
- _MAX_U64TOSTR_BASE10_COUNT
- _MAX_U64TOSTR_BASE8_COUNT
- _MAX_U64TOSTR_BASE2_COUNT
helpviewer_keywords:
- _itot function
- ui64toa function
- _ui64toa function
- converting integers
- itot function
- _i64tow function
- _i64toa function
- _itow function
- ui64tow function
- integers, converting
- itoa function
- _ui64tow function
- i64tow function
- itow function
- i64toa function
- converting numbers, to strings
- _itoa function
ms.assetid: 46592a00-77bb-4e73-98c0-bf629d96cea6
ms.openlocfilehash: 0cc084076c5e39843ecc1afa08671ce6b2f06d1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342700"
---
# <a name="itoa-_itoa-ltoa-_ltoa-ultoa-_ultoa-_i64toa-_ui64toa-_itow-_ltow-_ultow-_i64tow-_ui64tow"></a>itoa, _itoa, ltoa, _ltoa, ultoa, _ultoa, _i64toa, _ui64toa, _itow, _ltow, _ultow, _i64tow, _ui64tow

Konvertiert eine ganze Zahl in eine Zeichenfolge. Sicherere Versionen dieser Funktionen sind verfügbar; siehe [_itoa_s, _itow_s Funktionen](itoa-s-itow-s.md).

## <a name="syntax"></a>Syntax

```C
char * _itoa( int value, char *buffer, int radix );
char * _ltoa( long value, char *buffer, int radix );
char * _ultoa( unsigned long value, char *buffer, int radix );
char * _i64toa( long long value, char *buffer, int radix );
char * _ui64toa( unsigned long long value, char *buffer, int radix );

wchar_t * _itow( int value, wchar_t *buffer, int radix );
wchar_t * _ltow( long value, wchar_t *buffer, int radix );
wchar_t * _ultow( unsigned long value, wchar_t *buffer, int radix );
wchar_t * _i64tow( long long value, wchar_t *buffer, int radix );
wchar_t * _ui64tow( unsigned long long value, wchar_t *buffer, int radix );

// These POSIX versions of the functions have deprecated names:
char * itoa( int value, char *buffer, int radix );
char * ltoa( long value, char *buffer, int radix );
char * ultoa( unsigned long value, char *buffer, int radix );

// The following template functions are C++ only:
template <size_t size>
char *_itoa( int value, char (&buffer)[size], int radix );

template <size_t size>
char *_itoa( long value, char (&buffer)[size], int radix );

template <size_t size>
char *_itoa( unsigned long value, char (&buffer)[size], int radix );

template <size_t size>
char *_i64toa( long long value, char (&buffer)[size], int radix );

template <size_t size>
char * _ui64toa( unsigned long long value, char (&buffer)[size], int radix );

template <size_t size>
wchar_t * _itow( int value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ltow( long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ultow( unsigned long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _i64tow( long long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ui64tow( unsigned long long value, wchar_t (&buffer)[size],
   int radix );
```

### <a name="parameters"></a>Parameter

*value*<br/>
Zu konvertierende Zahl.

*Puffer*<br/>
Puffer, der das Ergebnis der Konvertierung enthält.

*Radix*<br/>
Die Basis, die für die Konvertierung des *Wertes*verwendet werden soll, der im Bereich 2-36 liegen muss.

*Größe*<br/>
Länge des Puffers in Einheiten des Zeichentyps. Dieser Parameter wird aus dem *Pufferargument* in C++ abgeleitet.

## <a name="return-value"></a>Rückgabewert

Jede dieser Funktionen gibt einen Zeiger auf *den Puffer*zurück. Es gibt keine Fehlerrückgabe.

## <a name="remarks"></a>Bemerkungen

Die **Funktionen _itoa**, **_ltoa**, **_ultoa**, **_i64toa**und **_ui64toa** konvertieren die Ziffern des angegebenen *Wertarguments* in eine null-terminierte Zeichenfolge und speichern das Ergebnis (bis zu 33 Zeichen für **_itoa**, **_ltoa**und **_ultoa**und 65 für **_i64toa** und **_ui64toa**) in *Puffer.* Wenn *radix* gleich 10 ist und der *Wert* negativ ist, ist**-** das erste Zeichen der gespeicherten Zeichenfolge das Minuszeichen ( ). Die Funktionen **_itow**, **_ltow**, **_ultow**, **_i64tow**und **_ui64tow** sind Breitzeichenversionen von **_itoa**, **_ltoa**, **_ultoa** **, _i64toa**und **_ui64toa**.

> [!IMPORTANT]
> Diese Funktionen können über das Ende eines Puffers hinaus schreiben, der zu klein ist. Um Pufferüberläufe zu vermeiden, stellen Sie sicher, dass der *Puffer* groß genug ist, um die konvertierten Ziffern sowie das nachfolgende Nullzeichen und ein Vorzeichenzeichen zu enthalten. Der Missbrauch dieser Funktionen kann zu schwerwiegenden Sicherheitsproblemen im Code führen.

Aufgrund ihres Potenzials für Sicherheitsprobleme verursachen diese Funktionen standardmäßig eine Veraltungswarnung [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md): **Diese Funktion oder Variable kann unsicher sein. Erwägen Sie** stattdessen die Verwendung *safe_function.* ** Um die Veraltung zu deaktivieren, verwenden Sie _CRT_SECURE_NO_WARNINGS.** Es wird empfohlen, den Quellcode so zu ändern, dass die in der Warnmeldung vorgeschlagenen *safe_function* verwendet werden. Die sichereren Funktionen schreiben nicht mehr Zeichen als die angegebene Puffergröße. Weitere Informationen finden Sie unter [_itoa_s, _itow_s Funktionen](itoa-s-itow-s.md).

Um diese Funktionen ohne die Veraltungswarnung zu verwenden, definieren Sie das **_CRT_SECURE_NO_WARNINGS** Präprozessormakros, bevor Sie CRT-Header einschließen. Sie können dies in der Befehlszeile in einer Entwickler-Eingabeaufforderung tun, indem Sie dem Befehl **cl** die Compileroption **/D_CRT_SECURE_NO_WARNINGS** hinzufügen. Definieren Sie andernfalls das Makro in den Quelldateien. Wenn Sie vorkompilierte Header verwenden, definieren Sie das Makro oben in der vorkompilierten Header-Include-Datei *pch.h* (*stdafx.h* in Visual Studio 2017 und früher). Um das Makro im Quellcode zu **#define** definieren, verwenden Sie eine #define-Direktive, bevor Sie einen CRT-Header einschließen, wie in diesem Beispiel:

```C
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

In C++ verfügen diese Funktionen über Vorlagenüberladungen, die ihre sichereren Gegenstücke aufrufen. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Die POSIX-Namen **itoa**, **ltoa**und **ultoa** existieren als Aliase für die Funktionen **_itoa**, **_ltoa**und **_ultoa.** Die POSIX-Namen sind veraltet, da sie nicht den implementierungsspezifischen globalen Funktionsnamenkonventionen von ISO C entsprechen. Standardmäßig führen diese Funktionen zu einer Veraltungswarnung [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md): **Der POSIX-Name für dieses Element ist veraltet. Verwenden Sie stattdessen den ISO C- und C++-konformen Namen:** *new_name*. Es wird empfohlen, den Quellcode so zu ändern, dass die sichereren Versionen dieser **Funktionen, _itoa_s**, **_ltoa_s**oder **_ultoa_s**verwendet werden. Weitere Informationen finden Sie unter [_itoa_s, _itow_s Funktionen](itoa-s-itow-s.md).

Für die Portabilität des Quellcodes können Sie es vorziehen, die POSIX-Namen in Ihrem Code beizubehalten. Um diese Funktionen ohne die Veraltungswarnung zu verwenden, definieren Sie sowohl die **_CRT_NONSTDC_NO_WARNINGS-** als auch **die _CRT_SECURE_NO_WARNINGS** Präprozessormakros, bevor Sie CRT-Header einschließen. Sie können dies in der Befehlszeile in einer Entwicklereingabeaufforderung tun, indem Sie dem Befehl **/D_CRT_SECURE_NO_WARNINGS** und **/D_CRT_NONSTDC_NO_WARNINGS** die Compileroptionen hinzufügen. **cl** Definieren Sie andernfalls die Makros in den Quelldateien. Wenn Sie vorkompilierte Header verwenden, definieren Sie die Makros oben in der vorkompilierten Header-Include-Datei. Um die Makros im Quellcode zu definieren, verwenden Sie **#define** Direktiven, bevor Sie einen CRT-Header einschließen, wie in diesem Beispiel:

```C
#define _CRT_NONSTDC_NO_WARNINGS 1
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

### <a name="maximum-conversion-count-macros"></a>Maximale Conversion-Anzahl von Makros

Um Ihnen beim Erstellen sicherer Puffer für Konvertierungen zu helfen, enthält die CRT einige praktische Makros. Diese definieren die Größe des Puffers, der erforderlich ist, um den am längsten möglichen Wert jedes ganzzahligen Typs, einschließlich des Nullabschlusszeichens und des Zeichenzeichens, für mehrere gemeinsame Basen zu konvertieren. Um sicherzustellen, dass der Konvertierungspuffer groß genug ist, um eine Konvertierung in der von *radix*angegebenen Basis zu empfangen, verwenden Sie eines dieser definierten Makros, wenn Sie den Puffer zuweisen. Dies hilft, Pufferüberlauffehler zu verhindern, wenn Sie integrale Typen in Zeichenfolgen konvertieren. Diese Makros werden definiert, wenn Sie entweder stdlib.h oder wchar.h in die Quelle aufnehmen.

Um eines dieser Makros in einer Zeichenfolgenkonvertierungsfunktion zu verwenden, deklarieren Sie den Konvertierungspuffer des entsprechenden Zeichentyps, und verwenden Sie den Makrowert für den Ganzzahltyp und die Basis als Pufferdimension. In dieser Tabelle sind die Makros aufgeführt, die für jede Funktion für die aufgeführten Basen geeignet sind:

||||
|-|-|-|
|Functions|radix|Makros|
|**_itoa**, **_itow**|16<br/>10<br/>8<br/>2|**_MAX_ITOSTR_BASE16_COUNT**<br/>**_MAX_ITOSTR_BASE10_COUNT**<br/>**_MAX_ITOSTR_BASE8_COUNT**<br/>**_MAX_ITOSTR_BASE2_COUNT**|
|**_ltoa**, **_ltow**|16<br/>10<br/>8<br/>2|**_MAX_LTOSTR_BASE16_COUNT**<br/>**_MAX_LTOSTR_BASE10_COUNT**<br/>**_MAX_LTOSTR_BASE8_COUNT**<br/>**_MAX_LTOSTR_BASE2_COUNT**|
|**_ultoa**, **_ultow**|16<br/>10<br/>8<br/>2|**_MAX_ULTOSTR_BASE16_COUNT**<br/>**_MAX_ULTOSTR_BASE10_COUNT**<br/>**_MAX_ULTOSTR_BASE8_COUNT**<br/>**_MAX_ULTOSTR_BASE2_COUNT**|
|**_i64toa**, **_i64tow**|16<br/>10<br/>8<br/>2|**_MAX_I64TOSTR_BASE16_COUNT**<br/>**_MAX_I64TOSTR_BASE10_COUNT**<br/>**_MAX_I64TOSTR_BASE8_COUNT**<br/>**_MAX_I64TOSTR_BASE2_COUNT**|
|**_ui64toa**, **_ui64tow**|16<br/>10<br/>8<br/>2|**_MAX_U64TOSTR_BASE16_COUNT**<br/>**_MAX_U64TOSTR_BASE10_COUNT**<br/>**_MAX_U64TOSTR_BASE8_COUNT**<br/>**_MAX_U64TOSTR_BASE2_COUNT**|

In diesem Beispiel wird ein Konvertierungszählmakro verwendet, um einen Puffer zu definieren, der groß genug ist, um eine **lange Länge ohne Vorzeichen** in Basis 2 zu enthalten:

```cpp
#include <wchar.h>
#include <iostream>
int main()
{
    wchar_t buffer[_MAX_U64TOSTR_BASE2_COUNT];
    std:wcout << _ui64tow(0xFFFFFFFFFFFFFFFFull, buffer, 2) << std::endl;
}
```

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_itot**|**_itoa**|**_itoa**|**_itow**|
|**_ltot**|**_ltoa**|**_ltoa**|**_ltow**|
|**_ultot**|**_ultoa**|**_ultoa**|**_ultow**|
|**_i64tot**|**_i64toa**|**_i64toa**|**_i64tow**|
|**_ui64tot**|**_ui64toa**|**_ui64toa**|**_ui64tow**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**itoa**, **ltoa**, **ultoa**|\<stdlib.h>|
|**_itoa**, **_ltoa**, **_ultoa**, **_i64toa**, **_ui64toa**|\<stdlib.h>|
|**_itow**, **_ltow**, **_ultow**, **_i64tow**, **_ui64tow**|\<stdlib.h> oder \<wchar.h>|

Diese Funktionen und Makros sind Microsoft-spezifisch. Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

In diesem Beispiel wird die Verwendung einiger ganzzahliger Konvertierungsfunktionen veranschaulicht. Beachten Sie die **_CRT_SECURE_NO_WARNINGS** Verwendung des _CRT_SECURE_NO_WARNINGS-Makros, um die Warnung C4996 zum Schweigen zu bringen.

```C
// crt_itoa.c
// Compile by using: cl /W4 crt_itoa.c
// This program makes use of the _itoa functions
// in various examples.

#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>      // for printf
#include <string.h>     // for strnlen
#include <stdlib.h>     // for _countof, _itoa fns, _MAX_COUNT macros

int main(void)
{
    char buffer[_MAX_U64TOSTR_BASE2_COUNT];
    int r;

    for (r = 10; r >= 2; --r)
    {
        _itoa(-1, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
    printf("\n");

    for (r = 10; r >= 2; --r)
    {
        _i64toa(-1LL, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
    printf("\n");

    for (r = 10; r >= 2; --r)
    {
        _ui64toa(0xffffffffffffffffULL, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
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

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[_itoa_s, _itow_s Funktionen](itoa-s-itow-s.md)<br/>
