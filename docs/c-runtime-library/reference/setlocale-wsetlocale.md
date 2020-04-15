---
title: setlocale, _wsetlocale
description: Beschreibt die CrT-Bibliotheksfunktionen setlocale (Microsoft _wsetlocaleC-Laufzeit) und .
ms.date: 4/2/2020
api_name:
- _wsetlocale
- setlocale
- _o__wsetlocale
- _o_setlocale
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
- _wsetlocale
- _tsetlocale
- setlocale
helpviewer_keywords:
- wsetlocale function
- setlocale function
- tsetlocale function
- locales, defining
- _tsetlocale function
- defining locales
- _wsetlocale function
ms.assetid: 3ffb684e-5990-4202-9553-b5339af9520d
no-loc:
- setlocale
- _wsetlocale
ms.openlocfilehash: 2834229839153c3154caadf71e5fb30d84ed2f1a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353714"
---
# <a name="setlocale-_wsetlocale"></a>setlocale, _wsetlocale

Legt das Laufzeitgebietsschema fest oder ruft es ab.

## <a name="syntax"></a>Syntax

```C
char *setlocale(
   int category,
   const char *locale
);
wchar_t *_wsetlocale(
   int category,
   const wchar_t *locale
);
```

### <a name="parameters"></a>Parameter

*Kategorie*\
Vom Gebietsschema betroffene Kategorie.

*locale*\
Gebietsschemaspezifizierer.

## <a name="return-value"></a>Rückgabewert

Wenn ein gültiges *Gebietsschema* und eine *gültige Kategorie* angegeben sind, wird ein Zeiger auf die Zeichenfolge zurückgegeben, die dem angegebenen *Gebietsschema* und der *angegebenen Kategorie*zugeordnet ist. Wenn das *Gebietsschema* oder die *Kategorie* ungültig ist, gibt ein Nullzeiger zurück, und die aktuellen Gebietsschemaeinstellungen des Programms bleiben unverändert.

Beispiel: Der Aufruf

```C
setlocale( LC_ALL, "en-US" );
```

legt alle Kategorien fest und gibt nur folgende Zeichenfolge zurück

```Output
en-US
```

Sie können die von **setlocale** zurückgegebene Zeichenfolge kopieren, um diesen Teil der Gebietsschemainformationen des Programms wiederherzustellen. Globaler oder threadlokaler Speicher wird für die von **setlocale**zurückgegebene Zeichenfolge verwendet. Spätere Aufrufe von **setlocale** überschreiben die Zeichenfolge, wodurch Zeichenfolgenzeiger ungültig werden, die von früheren Aufrufen zurückgegeben wurden.

## <a name="remarks"></a>Bemerkungen

Verwenden Sie die **Setlocale-Funktion,** um einige oder alle aktuellen Programmgebietsschemainformationen festzulegen, zu ändern oder abzufragen, die von *Gebietsschema* und *Kategorie*angegeben sind. *Gebietsschema* bezieht sich auf die Lokalität (Land/Region und Sprache), für die Sie bestimmte Aspekte Ihres Programms anpassen können. Vom Gebietsschema abhängig sind u. a. Datumsformat und Währungsformat. Wenn Sie *Gebietsschema* auf die Standardzeichenfolge für eine Sprache festlegen, für die mehrere Formulare auf Ihrem Computer unterstützt werden, sollten Sie den **Rückgabewert setlocale** überprüfen, um festzustellen, welche Sprache wirksam ist. Wenn Sie z. B. *Gebietsschema* auf "chinesisch" setzen, kann der Rückgabewert entweder "chinesisch vereinfacht" oder "chinesisch-traditionell" sein.

**_wsetlocale** ist eine breitgefächerte Version von **setlocale**; Das *Gebietsschemaargument* und der Rückgabewert von **_wsetlocale** sind Zeichenfolgen mit großen Zeichen. **_wsetlocale** und **setlocale** verhalten sich ansonsten identisch.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsetlocale**|**Setlocale**|**Setlocale**|**_wsetlocale**|

Das *Kategorieargument* gibt die betroffenen Teile der Gebietsschemainformationen eines Programms an. Die für die *Kategorie* verwendeten Makros und die Teile des Programms, die sie beeinflussen, lauten wie folgt:

|*Kategorie-Flag*|Betrifft|
|-|-|
| **LC_ALL** | Alle unten aufgeführten Kategorien. |
| **LC_COLLATE** | Die Funktionen **strcoll**, **_stricoll**, **wcscoll**, **_wcsicoll**, **strxfrm**, **_strncoll**, **_strnicoll**, **_wcsncoll**, **_wcsnicoll**und **wcsxfrm.** |
| **LC_CTYPE** | Die Zeichenbehandlungsfunktionen (außer **isdigit**, **isxdigit**, **mbstowcs**und **mbtowc**, die davon nicht betroffen sind). |
| **LC_MONETARY** | Informationen zur Währungsformatierung, die von der **localeconv-Funktion** zurückgegeben werden. |
| **LC_NUMERIC** | Dezimalzeichen für die formatierten Ausgaberoutinen (z. B. **printf**), für die Datenkonvertierungsroutinen und für die nicht monetären Formatierungsinformationen, die von **localeconv**zurückgegeben werden. Zusätzlich zum Dezimalzeichen legt **LC_NUMERIC** das Tausendertrennzeichen und die Gruppierungssteuerungszeichenfolge fest, die von [localeconv](localeconv.md)zurückgegeben wird. |
| **LC_TIME** | Die Funktionen **strftime** und **wcsftime.** |

Diese Funktion überprüft den Kategorienparameter. Wenn der Kategorieparameter nicht einer der in der vorherigen Tabelle angegebenen Werte ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, setzt die Funktion **errno** auf **EINVAL** und gibt **NULL**zurück.

Das *Gebietsschemaargument* ist ein Zeiger auf eine Zeichenfolge, die das Gebietsschema angibt. Informationen zum Format des *Gebietsschemaarguments* finden Sie unter [Gebietsschemanamen, Sprachen und Länder-/Regionszeichenfolgen](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Wenn *locale* auf eine leere Zeichenfolge zeigt, ist das Gebietsschema die durch die Implementierung definierte native Umgebung. Der Wert **C** gibt die minimale ANSI-konforme Umgebung für die C-Übersetzung an. Das **C** C-Gebietsschema geht davon aus, dass alle **Char-Datentypen** 1 Byte sind und dass ihr Wert immer kleiner als 256 ist.

Zum Programmstart wird die Entsprechung der folgenden Anweisung ausgeführt:

`setlocale( LC_ALL, "C" );`

Das *Gebietsschemaargument* kann einen Gebietsschemanamen, eine Sprachzeichenfolge, eine Sprachzeichenfolge und einen Länder-/Regionscode, eine Codepage oder eine Sprachzeichenfolge, einen Länder-/Regionscode und eine Codepage verwenden. Der Satz verfügbarer Gebietsschemanamen, Sprachen, Länder-/Regionscodes und Codepages enthält alle von der Windows NLS-API unterstützten. Die von **setlocale** unterstützten Gebietsschemanamen werden unter [Gebietsschemanamen, Sprachen und Länder-/Regionszeichenfolgen](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)beschrieben. Der Satz von Sprach- und Länder-/Regionszeichenfolgen, die von **setlocale** unterstützt werden, sind in [Language Strings](../../c-runtime-library/language-strings.md) und [Country/Region Strings](../../c-runtime-library/country-region-strings.md)aufgeführt. Wie empfehlen die Gebietsschema-Namensform aus Gründen der Leistung und leichteren Verwaltung von Gebietsschema-Zeichenfolgen, die in Code eingebettet sind oder für den Speicher serialisiert sind. Es ist weniger wahrscheinlich, dass Gebietsschema-Zeichenfolgen durch eine Betriebssystemaktualisierung geändert werden, als dies bei der Namensform für Sprache und Land/Region der Fall ist.

Ein Nullzeiger, der übergeben wird, wenn das *locale-Argument* **setlocale** anweist, abzufragen, anstatt die internationale Umgebung festzulegen. Wenn das *Gebietsschemaargument* ein Nullzeiger ist, wird die aktuelle Gebietsschemaeinstellung des Programms nicht geändert. Stattdessen gibt **setlocale** einen Zeiger auf die Zeichenfolge zurück, die der *Kategorie* des aktuellen Gebietsschemas des Threads zugeordnet ist. Wenn das *Kategorieargument* **LC_ALL**ist, gibt die Funktion eine Zeichenfolge zurück, die die aktuelle Einstellung jeder Kategorie angibt, getrennt durch Semikolons. Beispiel: Die Reihenfolge der Aufrufe

```C
// Set all categories and return "en-US"
setlocale(LC_ALL, "en-US");
// Set only the LC_MONETARY category and return "fr-FR"
setlocale(LC_MONETARY, "fr-FR");
printf("%s\n", setlocale(LC_ALL, NULL));
```

gibt Folgendes zurück:

```Output
LC_COLLATE=en-US;LC_CTYPE=en-US;LC_MONETARY=fr-FR;LC_NUMERIC=en-US;LC_TIME=en-US
```

Dies ist die Zeichenfolge, die der **LC_ALL-Kategorie** zugeordnet ist.

Die folgenden Beispiele beziehen sich auf die **LC_ALL** Kategorie. Entweder die Saiten ". OCP" und ". ACP" kann anstelle einer Codepagenummer verwendet werden, um die Verwendung der standardmäßigen OEM-Codepage bzw. der benutzerdefinierten ANSI-Codepage für diesen Gebietsschemanamen anzugeben.

- `setlocale( LC_ALL, "" );`

   Legt das Gebietsschema auf den Standardwert fest, der die vom Betriebssystem abgerufene voreingestellte ANSI-Benutzercodepage ist. Der Gebietsschemaname wird auf den von [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename)zurückgegebenen Wert festgelegt. Die Codepage wird auf den von [GetACP](/windows/win32/api/winnls/nf-winnls-getacp)zurückgegebenen Wert festgelegt.

- `setlocale( LC_ALL, ".OCP" );`

   Legt das Gebietsschema auf die aktuelle OEM-Codepage fest, die vom Betriebssystem abgerufen wurde. Der Gebietsschemaname wird auf den von [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename)zurückgegebenen Wert festgelegt. Die Codepage wird auf den [LOCALE_IDEFAULTCODEPAGE](/windows/win32/intl/locale-idefault-constants) Wert für den Benutzerstandardgebietsschemanamen durch [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex)festgelegt.

- `setlocale( LC_ALL, ".ACP" );`

   Legt das Gebietsschema auf die vom Betriebssystem abgerufene voreingestellte ANSI-Benutzercodepage fest. Der Gebietsschemaname wird auf den von [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename)zurückgegebenen Wert festgelegt. Die Codepage wird auf den [LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) Wert für den Benutzerstandardgebietsschemanamen durch [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex)festgelegt.

- `setlocale( LC_ALL, "<localename>" );`

   Legt das Gebietsschema auf den Gebietsschemanamen fest, der durch * \<localename>* angegeben ist. Die Codepage wird durch [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex)auf den [LOCALE_IDEFAULTANSICODEPAGE-Wert](/windows/win32/intl/locale-idefault-constants) für den angegebenen Gebietsschemanamen festgelegt.

- `setlocale( LC_ALL, "<language>_<country>" );`

   Legt das Gebietsschema auf die Sprache * \<* und das Land/die Region fest, die durch Sprache>und * \<Land>* angegeben sind, zusammen mit der Standardcodepage, die vom Hostbetriebssystem abgerufen wurde. Die Codepage wird durch [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex)auf den [LOCALE_IDEFAULTANSICODEPAGE-Wert](/windows/win32/intl/locale-idefault-constants) für den angegebenen Gebietsschemanamen festgelegt.

- `setlocale( LC_ALL, "<language>_<country>.<code_page>" );`

   Legt das Gebietsschema auf die Sprache, das Land/die Region und die Codepage fest, die durch die * \<Sprache>*, * \<Land>* und * \<code_page>* Zeichenfolgen angegeben sind. Sie können verschiedene Kombinationen von Sprache, Land/Region und Codepage verwenden. Bei diesem Aufruf wird beispielsweise das Gebetsschema auf Französisch (Kanada) festgelegt, mit der Codepage 1252:

   `setlocale( LC_ALL, "French_Canada.1252" );`

   Bei diesem Aufruf wird das Gebietsschema auf Französisch (Kanada) mit der voreingestellten ANSI-Codepage festgelegt:

   `setlocale( LC_ALL, "French_Canada.ACP" );`

   Bei diesem Aufruf wird das Gebietsschema auf Französisch (Kanada) mit der voreingestellten OEM-Codepage festgelegt:

   `setlocale( LC_ALL, "French_Canada.OCP" );`

- `setlocale( LC_ALL, "<language>" );`

   Legt das Gebietsschema auf die Sprache * \< *fest, die durch die Sprache>angegeben ist, und verwendet das Standardland/die Standardregion für die angegebene Sprache und die standardmäßige ANSI-Codepage für dieses Land/die Region, wie sie vom Hostbetriebssystem abgerufen wurde. Die folgenden Aufrufe von **setlocale** sind z. B. funktional äquivalent:

   `setlocale( LC_ALL, "en-US" );`

   `setlocale( LC_ALL, "English" );`

   `setlocale( LC_ALL, "English_United States.1252" );`

   Aus Leistungsgründen und wegen der Wartbarkeit wird die erste Form empfohlen.

- `setlocale( LC_ALL, ".<code_page>" );`

   Legt die Codepage auf den Wert fest, der durch *<Codepage>* angegeben ist, wobei zugleich das Standardland bzw. die Standardregion und Sprache (gemäß der Definition vom Hostbetriebssystem) für die angegebene Codepage verwendet wird.

Die Kategorie muss entweder **LC_ALL** oder **LC_CTYPE** sein, um eine Änderung der Codepage vorzunehmen. Wenn z. B. das Standardland/die Standardregion und die Sprache des Hostbetriebssystems "Vereinigte Staaten" und "Englisch" sind, sind die beiden folgenden Aufrufe von **setlocale** funktional äquivalent:

`setlocale( LC_ALL, ".1252" );`

`setlocale( LC_ALL, "English_United States.1252");`

Weitere Informationen finden Sie unter [setlocale](../../preprocessor/setlocale.md)-Pragmadirektive in der [C/C++-Präprozessorreferenz](../../preprocessor/c-cpp-preprocessor-reference.md).

Die Funktion [_configthreadlocale](configthreadlocale.md) wird verwendet, um zu steuern, ob **setlocale** das Gebietsschema aller Threads in einem Programm oder nur das Gebietsschema des aufrufenden Threads beeinflusst.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**setlocale**|\<locale.h>|
|**_wsetlocale**|\<locale.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_setlocale.c
//
// This program demonstrates the use of setlocale when
// using two independent threads.
//

#include <locale.h>
#include <process.h>
#include <windows.h>
#include <stdio.h>
#include <time.h>

#define BUFF_SIZE 100

// Retrieve the date in the current
// locale's format.
int get_date(unsigned char* str)
{
    __time64_t ltime;
    struct tm  thetime;

    // Retrieve the current time
    _time64(&ltime);
    _gmtime64_s(&thetime, &ltime);

    // Format the current time structure into a string
    // "%#x" is the long date representation in the
    // current locale
    if (!strftime((char *)str, BUFF_SIZE, "%#x",
                  (const struct tm *)&thetime))
    {
        printf("strftime failed!\n");
        return -1;
    }
    return 0;
}

// This thread sets its locale to the argument
// and prints the date.
uintptr_t __stdcall SecondThreadFunc( void* pArguments )
{
    unsigned char str[BUFF_SIZE];
    char * locale = (char *)pArguments;

    // Set the thread locale
    printf("The thread locale is now set to %s.\n",
           setlocale(LC_ALL, locale));

    // Retrieve the date string from the helper function
    if (get_date(str) == 0)
    {
        printf("The date in %s locale is: '%s'\n", locale, str);
    }

    _endthreadex( 0 );
    return 0;
}

// The main thread sets the locale to English
// and then spawns a second thread (above) and prints the date.
int main()
{
    HANDLE          hThread;
    unsigned        threadID;
    unsigned char   str[BUFF_SIZE];

    // Enable per-thread locale causes all subsequent locale
    // setting changes in this thread to only affect this thread.
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);

    // Set the locale of the main thread to US English.
    printf("The thread locale is now set to %s.\n",
           setlocale(LC_ALL, "en-US"));

    // Create the second thread with a German locale.
    // Our thread function takes an argument of the locale to use.
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc,
                                      "de-DE", 0, &threadID );

    if (get_date(str) == 0)
    {
        // Retrieve the date string from the helper function
        printf("The date in en-US locale is: '%s'\n\n", str);
    }

    // Wait for the created thread to finish.
    WaitForSingleObject( hThread, INFINITE );

    // Destroy the thread object.
    CloseHandle( hThread );
}
```

```Output
The thread locale is now set to en-US.
The time in en-US locale is: 'Wednesday, May 12, 2004'

The thread locale is now set to de-DE.
The time in de-DE locale is: 'Mittwoch, 12. Mai 2004'
```

## <a name="see-also"></a>Siehe auch

[Gebietsschemanamen, Sprachen und Länder-/Regionszeichenfolgen](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[_configthreadlocale](configthreadlocale.md)\
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)\
[Locale](../../c-runtime-library/locale.md)\
[Localeconv](localeconv.md)\
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)\
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)\
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)\
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)\
[_setmbcp](setmbcp.md)\
[strcoll-Funktionen](../../c-runtime-library/strcoll-functions.md)\
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)\
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)\
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)\
[wctomb, _wctomb_l](wctomb-wctomb-l.md)
