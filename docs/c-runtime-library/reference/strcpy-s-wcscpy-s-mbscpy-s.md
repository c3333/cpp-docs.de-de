---
title: strcpy_s, wcscpy_s, _mbscpy_s, _mbscpy_s_l
ms.date: 4/2/2020
api_name:
- wcscpy_s
- _mbscpy_s
- _mbscpy_s_l
- strcpy_s
- _o__mbscpy_s
- _o__mbscpy_s_l
- _o_strcpy_s
- _o_wcscpy_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strcpy_s
- _mbscpy_s
- _mbscpy_s_l
- _tcscpy_s
- wcscpy_s
helpviewer_keywords:
- strcpy_s function
- _tcscpy_s function
- _mbscpy_s function
- _mbscpy_s_l function
- copying strings
- strings [C++], copying
- tcscpy_s function
- wcscpy_s function
ms.assetid: 611326f3-7929-4a5d-a465-a4683af3b053
ms.openlocfilehash: d2d13939f0edde278b96a9d82fcbe82b6abe5d0a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911845"
---
# <a name="strcpy_s-wcscpy_s-_mbscpy_s-_mbscpy_s_l"></a>strcpy_s, wcscpy_s, _mbscpy_s, _mbscpy_s_l

Kopiert eine Zeichenfolge. Diese Versionen von [strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md) enthalten Sicherheitsverbesserungen, wie unter [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

> [!IMPORTANT]
> **_mbscpy_s** und **_mbscpy_s_l** können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
errno_t strcpy_s(
   char *dest,
   rsize_t dest_size,
   const char *src
);
errno_t wcscpy_s(
   wchar_t *dest,
   rsize_t dest_size,
   const wchar_t *src
);
errno_t _mbscpy_s(
   unsigned char *dest,
   rsize_t dest_size,
   const unsigned char *src
);
errno_t _mbscpy_s_l(
   unsigned char *dest,
   rsize_t dest_size,
   const unsigned char *src,
   _locale_t locale
);
```

```cpp
// Template functions are C++ only:
template <size_t size>
errno_t strcpy_s(
   char (&dest)[size],
   const char *src
); // C++ only
template <size_t size>
errno_t wcscpy_s(
   wchar_t (&dest)[size],
   const wchar_t *src
); // C++ only
template <size_t size>
errno_t _mbscpy_s(
   unsigned char (&dest)[size],
   const unsigned char *src
); // C++ only
template <size_t size>
errno_t _mbscpy_s_l(
   unsigned char (&dest)[size],
   const unsigned char *src,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parameter

*dest*<br/>
Speicherort des Zielzeichenfolgenpuffers.

*dest_size*<br/>
Größe des Ziel Zeichen folgen Puffers in **char** -Einheiten für schmale und Multi-Byte-Funktionen und **wchar_t** Einheiten für Wide Functions. Dieser Wert muss größer als 0 (null) und nicht größer als **RSIZE_MAX**sein.

*src*<br/>
Auf NULL endender Quellzeichenfolgepuffer.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Null (0), wenn erfolgreich; andernfalls ein Fehler.

### <a name="error-conditions"></a>Fehlerbedingungen

|*dest*|*dest_size*|*src*|Rückgabewert|Inhalt von *dest*|
|----------------------|------------------------|-----------------|------------------|----------------------------------|
|**Normal**|any|any|**Eingabe**|nicht geändert|
|any|any|**Normal**|**Eingabe**|*dest*[0] auf 0 festgelegt|
|any|0 oder zu klein|any|**ERANGE**|*dest*[0] auf 0 festgelegt|

## <a name="remarks"></a>Hinweise

Die **strcpy_s** -Funktion kopiert den Inhalt in die Adresse von *src*, einschließlich des abschließenden NULL-Zeichens, an den Speicherort, der von *dest*angegeben wird. Die Zielzeichenfolge muss groß genug sein, um die Quellzeichenfolge und ihr beendendes NULL-Zeichen zu enthalten. Das Verhalten **strcpy_s** ist nicht definiert, wenn sich die Quell-und Ziel Zeichenfolgen überlappen.

**wcscpy_s** ist die breit Zeichen Version von **strcpy_s**, und **_mbscpy_s** ist die multibytezeichenversion. Die Argumente von **wcscpy_s** sind Zeichen folgen mit breit Zeichen. bei den **_mbscpy_s** und **_mbscpy_s_l** handelt es sich um Multibyte-Zeichen folgen. Anderenfalls verhalten sich diese Funktionen identisch. **_mbscpy_s_l** ist mit **_mbscpy_s** identisch, außer dass es den Gebiets Schema Parameter verwendet, der anstelle des aktuellen Gebiets Schemas übergeben wurde. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Wenn *dest* oder *src* ein NULL-Zeiger ist oder wenn die Größe der Ziel Zeichenfolge *dest_size* zu klein ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, geben diese Funktionen **EINVAL** zurück und **legen errno** auf **EINVAL** fest, wenn *dest* oder *src* ein NULL-Zeiger ist, und Sie geben **ERANGE** zurück und legen **errno** auf **ERANGE** fest, wenn die Ziel Zeichenfolge zu klein ist.

Nach erfolgreicher Ausführung endet die Zielzeichenfolge immer auf NULL.

In C++ wird die Verwendung dieser Funktionen durch Vorlagenüberladungen vereinfacht; die Überladungen können automatisch Rückschlüsse auf die Pufferlänge ziehen, wodurch kein Größenargument mehr angegeben werden muss, und sie können automatisch die älteren, weniger sicheren Funktionen durch ihre neueren, sichereren Entsprechungen ersetzen. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Die Debug-Bibliotheksversionen dieser Funktionen füllen zunächst den Puffer mit "0xFE" auf. Um dieses Verhalten zu deaktivieren, verwenden Sie [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscpy_s**|**strcpy_s**|**_mbscpy_s**|**wcscpy_s**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**strcpy_s**|\<string.h>|
|**wcscpy_s**|\<string.h> oder \<wchar.h>|
|**_mbscpy_s**|\<mbstring.h>|

Diese Funktionen sind Microsoft-spezifisch. Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Im Gegensatz zum Code der Produktionsqualität werden in diesem Beispiel die Funktionen der sicheren Zeichenfolge aufgerufen, ohne dass auf Fehler hin

```C
// crt_strcpy_s.c
// Compile by using: cl /W4 crt_strcpy_s.c
// This program uses strcpy_s and strcat_s
// to build a phrase.

#include <string.h>     // for strcpy_s, strcat_s
#include <stdlib.h>     // for _countof
#include <stdio.h>      // for printf
#include <errno.h>      // for return values

int main(void)
{
    char string[80];

    strcpy_s(string, _countof(string), "Hello world from ");
    strcat_s(string, _countof(string), "strcpy_s ");
    strcat_s(string, _countof(string), "and ");
    strcat_s(string, _countof(string), "strcat_s!");

    printf("String = %s\n", string);
}
```

```Output
String = Hello world from strcpy_s and strcat_s!
```

Wenn Sie C++-Code erstellen, sind die Vorlagen Versionen möglicherweise einfacher zu verwenden.

```cpp
// crt_wcscpy_s.cpp
// Compile by using: cl /EHsc /W4 crt_wcscpy_s.cpp
// This program uses wcscpy_s and wcscat_s
// to build a phrase.

#include <cstring>  // for wcscpy_s, wcscat_s
#include <cstdlib>  // for _countof
#include <iostream> // for cout, includes <cstdlib>, <cstring>
#include <errno.h>  // for return values

int main(void)
{
    wchar_t string[80];
    // using template versions of wcscpy_s and wcscat_s:
    wcscpy_s(string, L"Hello world from ");
    wcscat_s(string, L"wcscpy_s ");
    wcscat_s(string, L"and ");
    // of course we can supply the size explicitly if we want to:
    wcscat_s(string, _countof(string), L"wcscat_s!");

    std::wcout << L"String = " << string << std::endl;
}
```

```Output
String = Hello world from wcscpy_s and wcscat_s!
```

## <a name="see-also"></a>Weitere Informationen

[Zeichen folgen Bearbeitung](../../c-runtime-library/string-manipulation-crt.md) <br/>
["ercat", "wcscat", "_mbscat" _mbscat_l](strcat-wcscat-mbscat.md) <br/>
[strcmp, wcscmp, _mbscmp, _mbscmp_l](strcmp-wcscmp-mbscmp.md) <br/>
[strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md) <br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md) <br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md) <br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md) <br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md) <br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
