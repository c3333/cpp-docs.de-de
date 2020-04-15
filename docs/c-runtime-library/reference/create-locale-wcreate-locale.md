---
title: _create_locale, _wcreate_locale
ms.date: 4/2/2020
api_name:
- _create_locale
- __create_locale
- _wcreate_locale
- _o__create_locale
- _o__wcreate_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- create_locale
- _create_locale
- __create_locale
helpviewer_keywords:
- locales, creating
- _create_locale function
- create_locale function
- __create_locale function
ms.assetid: ca362464-9f4a-4ec6-ab03-316c55c5be81
ms.openlocfilehash: 611eaf342776b9a0f57c4f55c52a841c3fd13fb5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348257"
---
# <a name="_create_locale-_wcreate_locale"></a>_create_locale, _wcreate_locale

Erstellt ein locale-Objekt.

## <a name="syntax"></a>Syntax

```C
_locale_t _create_locale(
   int category,
   const char *locale
);
_locale_t _wcreate_locale(
   int category,
   const wchar_t *locale
);
```

### <a name="parameters"></a>Parameter

*category*<br/>
Kategorie.

*locale*<br/>
Gebietsschemaspezifizierer.

## <a name="return-value"></a>Rückgabewert

Wenn ein gültiges *Gebietsschema* und eine *gültige Kategorie* angegeben sind, werden die angegebenen Gebietsschemaeinstellungen als **_locale_t** Objekt zurückgegeben. Die aktuellen Gebietsschemaeinstellungen des Programms werden nicht geändert.

## <a name="remarks"></a>Bemerkungen

Mit **der Funktion _create_locale** können Sie ein Objekt erstellen, das bestimmte regionsspezifische Einstellungen darstellt, und das in gebietsschemaspezifischen Versionen vieler CRT-Funktionen (Funktionen mit dem **suffixen _l)** verwendet werden kann. Das Verhalten ähnelt **setlocale**, mit der Ausnahme, dass die Einstellungen in einer **zurückgegebenen _locale_t-Struktur** gespeichert werden, anstatt die angegebenen Gebietsschemaeinstellungen auf die aktuelle Umgebung anzuwenden. Die **_locale_t** Struktur sollte mit [_free_locale](free-locale.md) freigegeben werden, wenn sie nicht mehr benötigt wird.

**_wcreate_locale** ist eine breitgefächerte Version von **_create_locale**; Das zu **_wcreate_locale** *Gebietsschemaargument* ist eine Zeichenfolge mit großen Zeichen. **_wcreate_locale** und **_create_locale** verhalten sich ansonsten gleich.

Das *Kategorieargument* gibt die Betroffenen Teile des gebietsschemaspezifischen Verhaltens an. Die Flags, die für die *Kategorie* verwendet werden, und die Teile des Programms, die sie beeinflussen, sind wie in dieser Tabelle dargestellt:

| *Kategorie-Flag* | Betrifft |
|-----------------|---------|
| **LC_ALL** |Alle unten aufgeführten Kategorien. |
| **LC_COLLATE** |Die Funktionen **strcoll**, **_stricoll**, **wcscoll**, **_wcsicoll**, **strxfrm**, **_strncoll**, **_strnicoll**, **_wcsncoll**, **_wcsnicoll**und **wcsxfrm.** |
| **LC_CTYPE** | Die Zeichenbehandlungsfunktionen (außer **isdigit**, **isxdigit**, **mbstowcs**und **mbtowc**, die davon nicht betroffen sind). |
| **LC_MONETARY** | Informationen zur Währungsformatierung, die von der **localeconv-Funktion** zurückgegeben werden. |
| **LC_NUMERIC** | Dezimalzeichen für die formatierten Ausgaberoutinen (z. B. **printf**), für die Datenkonvertierungsroutinen und für die nicht monetären Formatierungsinformationen, die von **localeconv**zurückgegeben werden. Zusätzlich zum Dezimalzeichen legt **LC_NUMERIC** das Tausendertrennzeichen und die Gruppierungssteuerungszeichenfolge fest, die von [localeconv](localeconv.md)zurückgegeben wird. |
| **LC_TIME** | Die Funktionen **strftime** und **wcsftime.** |

Diese Funktion überprüft die *Kategorie-* und *Gebietsschemaparameter.* Wenn der Kategorieparameter nicht einer der in der vorherigen Tabelle angegebenen Werte ist oder wenn *das Gebietsschema* **NULL**ist, gibt die Funktion **NULL**zurück.

Das *Gebietsschemaargument* ist ein Zeiger auf eine Zeichenfolge, die das Gebietsschema angibt. Informationen zum Format des *Gebietsschemaarguments* finden Sie unter [Gebietsschemanamen, Sprachen und Länder-/Regionszeichenfolgen](../../c-runtime-library/locale-names-languages-and-country-region-strings.md).

Das *Gebietsschemaargument* kann einen Gebietsschemanamen, eine Sprachzeichenfolge, eine Sprachzeichenfolge und einen Länder-/Regionscode, eine Codepage oder eine Sprachzeichenfolge, einen Länder-/Regionscode und eine Codepage verwenden. Der Satz verfügbarer Gebietsschemanamen, Sprachen, Länder-/Regionscodes und Codepages enthält alle, die von der Windows NLS-API unterstützt werden. Der Satz von Gebietsschemanamen, die von **_create_locale** unterstützt werden, werden unter [Gebietsschemanamen, Sprachen und Länder-/Regionszeichenfolgen](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)beschrieben. Der Satz von Sprach- und Länder-/Regionszeichenfolgen, die von **_create_locale** unterstützt werden, sind in [Language Strings](../../c-runtime-library/language-strings.md) und [Country/Region Strings](../../c-runtime-library/country-region-strings.md)aufgeführt.

Weitere Informationen zu Gebietsschemaeinstellungen finden Sie unter [setlocale, _wsetlocale](setlocale-wsetlocale.md).

Der vorherige Name dieser Funktion, **__create_locale** (mit zwei führenden Unterstrichen), wurde veraltet.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_create_locale**|\<locale.h>|
|**_wcreate_locale**|\<locale.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_create_locale.c
// Sets the current locale to "de-CH" using the
// setlocale function and demonstrates its effect on the strftime
// function.

#include <stdio.h>
#include <locale.h>
#include <time.h>

int main(void)
{
    time_t ltime;
    struct tm thetime;
    unsigned char str[100];
    _locale_t locale;

    // Create a locale object representing the German (Switzerland) locale
    locale = _create_locale(LC_ALL, "de-CH");
    time (&ltime);
    _gmtime64_s(&thetime, &ltime);

    // %#x is the long date representation, appropriate to
    // the current locale
    if (!_strftime_l((char *)str, 100, "%#x",
                     (const struct tm *)&thetime, locale))
    {
        printf("_strftime_l failed!\n");
    }
    else
    {
        printf("In de-CH locale, _strftime_l returns '%s'\n", str);
    }

    _free_locale(locale);

    // Create a locale object representing the default C locale
    locale = _create_locale(LC_ALL, "C");
    time(&ltime);
    _gmtime64_s(&thetime, &ltime);

    if (!_strftime_l((char *)str, 100, "%#x",
                     (const struct tm *)&thetime, locale))
    {
        printf("_strftime_l failed!\n");
    }
    else
    {
        printf("In 'C' locale, _strftime_l returns '%s'\n", str);
    }

    _free_locale(locale);
}
```

```Output
In de-CH locale, _strftime_l returns 'Samstag, 9. Februar 2002'
In 'C' locale, _strftime_l returns 'Saturday, February 09, 2002'
```

## <a name="see-also"></a>Siehe auch

[Gebietsschemanamen, Sprachen und Länder-/Regionszeichenfolgen](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Language Strings](../../c-runtime-library/language-strings.md)<br/>
[Länder-/Regionszeichenfolgen](../../c-runtime-library/country-region-strings.md)<br/>
[_free_locale](free-locale.md)<br/>
[_configthreadlocale](configthreadlocale.md)<br/>
[Setlocale](../../preprocessor/setlocale.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strcoll-Funktionen](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
