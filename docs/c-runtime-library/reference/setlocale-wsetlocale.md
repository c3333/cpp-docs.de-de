---
title: ':::no-loc(setlocale):::, :::no-loc(_wsetlocale):::'
description: 'Beschreibt die Funktionen der Microsoft C-Lauf Zeit Bibliothek (CRT) :::no-loc(setlocale)::: und :::no-loc(_wsetlocale)::: .'
ms.date: 4/2/2020
api_name:
- ':::no-loc(_wsetlocale):::'
- ':::no-loc(setlocale):::'
- '_o_:::no-loc(_wsetlocale):::'
- '_o_:::no-loc(setlocale):::'
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ':::no-loc(_wsetlocale):::'
- '_t:::no-loc(setlocale):::'
- ':::no-loc(setlocale):::'
helpviewer_keywords:
- 'w:::no-loc(setlocale)::: function'
- ':::no-loc(setlocale)::: function'
- 't:::no-loc(setlocale)::: function'
- locales, defining
- '_t:::no-loc(setlocale)::: function'
- defining locales
- ':::no-loc(_wsetlocale)::: function'
ms.assetid: 3ffb684e-5990-4202-9553-b5339af9520d
no-loc:
- ':::no-loc(setlocale):::'
- ':::no-loc(_wsetlocale):::'
ms.openlocfilehash: 05e4e96297e2237ed6768e05ff4cacfd63744e1a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226137"
---
# <a name="no-locsetlocale-no-loc_wsetlocale"></a>:::no-loc(setlocale):::, :::no-loc(_wsetlocale):::

Legt das Laufzeitgebietsschema fest oder ruft es ab.

## <a name="syntax"></a>Syntax

```C
char *:::no-loc(setlocale):::(
   int category,
   const char *locale
);
wchar_t *:::no-loc(_wsetlocale):::(
   int category,
   const wchar_t *locale
);
```

### <a name="parameters"></a>Parameter

*Kategorie*\
Vom Gebietsschema betroffene Kategorie.

*Konfigurations*\
Gebietsschemaspezifizierer.

## <a name="return-value"></a>Rückgabewert

Wenn ein gültiges Gebiets Schema und eine gültige *Kategorie* angegeben werden, gibt einen Zeiger auf die Zeichenfolge zurück, die *dem angegebenen Gebiets* *Schema und der* angegebenen *Kategorie*zugeordnet ist Wenn das Gebiets *Schema oder die* *Kategorie* ungültig ist, wird ein NULL-Zeiger zurückgegeben, und die aktuellen Gebiets Schema Einstellungen des Programms sind unverändert.

Beispiel: Der Aufruf

```C
:::no-loc(setlocale):::( LC_ALL, "en-US" );
```

legt alle Kategorien fest und gibt nur folgende Zeichenfolge zurück

```Output
en-US
```

Sie können die von zurückgegebene Zeichenfolge kopieren, **:::no-loc(setlocale):::** um diesen Teil der Gebiets Schema Informationen des Programms wiederherzustellen. Globaler oder lokaler Thread Speicher wird für die von zurückgegebene Zeichenfolge verwendet **:::no-loc(setlocale):::** . Später wird aufgerufen **:::no-loc(setlocale):::** , um die Zeichenfolge zu überschreiben, wodurch von früheren Aufrufen zurückgegebene Zeichen folgen Zeiger ungültig werden.

## <a name="remarks"></a>Bemerkungen

Verwenden **:::no-loc(setlocale):::** Sie die Funktion, um einige oder alle der aktuellen Programm Gebiets Schema Informationen festzulegen, zu ändern oder *locale* abzufragen, die vom Gebiets Schema und der *Kategorie*angegeben werden. *locale* bezieht sich auf den Ort (Land/Region und Sprache), für den Sie bestimmte Aspekte des Programms anpassen können. Vom Gebietsschema abhängig sind u. a. Datumsformat und Währungsformat. Wenn Sie das Gebiets Schema auf die Standard Zeichenfolge für eine Sprache *festlegen, die* mehrere Formulare auf dem Computer unterstützt, sollten Sie den Rückgabewert überprüfen, um festzustellen, **:::no-loc(setlocale):::** welche Sprache wirksam ist. Wenn Sie z. b. *locale* auf "Chinesisch" festlegen, kann der Rückgabewert entweder "Chinesisch-vereinfacht" oder "Chinesisch (traditionell)" lauten.

**:::no-loc(_wsetlocale):::** ist eine breit Zeichen Version von **:::no-loc(setlocale):::** . das Gebiets *locale* Schema Argument und der Rückgabewert von **:::no-loc(_wsetlocale):::** sind Zeichen folgen mit breit Zeichen. **:::no-loc(_wsetlocale):::** und **:::no-loc(setlocale):::** Verhalten sich andernfalls identisch.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_t:::no-loc(setlocale):::**|**:::no-loc(setlocale):::**|**:::no-loc(setlocale):::**|**:::no-loc(_wsetlocale):::**|

Das *Category* -Argument gibt die Teile der Gebiets Schema Informationen eines Programms an, die betroffen sind. Die für die *Kategorie* verwendeten Makros und die betroffenen Teile des Programms lauten wie folgt:

|*kategorieflag*|Betrifft|
|-|-|
| **LC_ALL** | Alle unten aufgeführten Kategorien. |
| **LC_COLLATE** | Die **Funktionen "** **strincoll**", " **_stricoll**", " **wcscoll**", " **_wcsicoll**", " **Straum**", " **_strncoll**", " **_strnicoll**", **"_wcsncoll"**, " **_wcsnicoll**" |
| **LC_CTYPE** | Die Funktionen zur Zeichen Behandlung (außer **IsDigit**, **isxdigit**, **mbstowcs**und **mbtowc**, die nicht betroffen sind). |
| **LC_MONETARY** | Informationen zur monetären Formatierung, die von der **localeconv** -Funktion zurückgegeben werden. |
| **LC_NUMERIC** | Ein Dezimaltrennzeichen für die formatierten Ausgaberoutinen (z. **b. printf**), für die Daten Konvertierungs Routinen und für die nicht monetären Formatierungsinformationen, die von **localeconv**zurückgegeben werden. Neben dem Dezimaltrennzeichen legt **LC_NUMERIC** das Tausender Trennzeichen und die Zeichenfolge für die Gruppierungs Steuerung fest, die von [localeconv](localeconv.md)zurückgegeben wurde. |
| **LC_TIME** | Die Funktionen " **Strauch Zeit** " und " **WCSF Time** ". |

Diese Funktion überprüft den Kategorienparameter. Wenn der Category-Parameter keiner der in der vorherigen Tabelle angegebenen Werte ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, legt die Funktion **errno** auf **EINVAL** fest und gibt **null**zurück.

Das *locale* -Argument ist ein Zeiger auf eine Zeichenfolge, die das Gebiets Schema angibt. Weitere Informationen zum *Format des Gebiets Schema Arguments finden* Sie unter Gebiets Schema [Namen, Sprachen und Länder-](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)/regionszeichenfolgen. Wenn *locale* auf eine leere Zeichenfolge zeigt, ist das Gebietsschema die durch die Implementierung definierte native Umgebung. Der Wert **C** gibt die minimale ANSI-konforme Umgebung für die C-Übersetzung an. Das **C** -Gebiets Schema geht davon aus, dass alle **`char`** Datentypen 1 Byte sind und ihr Wert immer kleiner als 256 ist.

Zum Programmstart wird die Entsprechung der folgenden Anweisung ausgeführt:

`:::no-loc(setlocale):::( LC_ALL, "C" );`

Das *locale* -Argument kann einen Gebiets Schema Namen, eine Sprachen Zeichenfolge, eine Sprachen Zeichenfolge und Länder-/Regionscode, eine Codepage oder eine Sprachen Zeichenfolge, einen Länder-/Regionscode und eine Codepage annehmen. Der Satz verfügbarer Gebiets Schema Namen, Sprachen, Länder-/Regionscodes und Codepages umfasst alle vom Windows-NLS API unterstützten Gebiets Schema Namen. Der von unterstützte Satz von Gebiets Schema Namen wird in Gebiets Schema **:::no-loc(setlocale):::** [Namen, Sprachen und Zeichen folgen für Länder/Regionen](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)beschrieben. Die von unterstützten sprach-und Länder-/regionszeichenfolgen **:::no-loc(setlocale):::** werden in [sprach](../../c-runtime-library/language-strings.md) Zeichenfolgen und Zeichen folgen für [Länder/Regionen](../../c-runtime-library/country-region-strings.md)aufgeführt. Wie empfehlen die Gebietsschema-Namensform aus Gründen der Leistung und leichteren Verwaltung von Gebietsschema-Zeichenfolgen, die in Code eingebettet sind oder für den Speicher serialisiert sind. Es ist weniger wahrscheinlich, dass Gebietsschema-Zeichenfolgen durch eine Betriebssystemaktualisierung geändert werden, als dies bei der Namensform für Sprache und Land/Region der Fall ist.

Ein als Gebiets *Schema Argument* übergebener NULL-Zeiger weist **:::no-loc(setlocale):::** an, die internationale Umgebung abzufragen, anstatt sie festzulegen. Wenn das *locale* -Argument ein NULL-Zeiger ist, wird die aktuelle Gebiets Schema Einstellung des Programms nicht geändert. Stattdessen **:::no-loc(setlocale):::** gibt einen Zeiger auf die Zeichenfolge zurück, die der *Kategorie* des aktuellen Gebiets Schemas des Threads zugeordnet ist. Wenn das *Category* -Argument **LC_ALL**ist, gibt die Funktion eine Zeichenfolge zurück, die die aktuelle Einstellung der einzelnen Kategorien angibt, getrennt durch Semikolons. Beispiel: Die Reihenfolge der Aufrufe

```C
// Set all categories and return "en-US"
:::no-loc(setlocale):::(LC_ALL, "en-US");
// Set only the LC_MONETARY category and return "fr-FR"
:::no-loc(setlocale):::(LC_MONETARY, "fr-FR");
printf("%s\n", :::no-loc(setlocale):::(LC_ALL, NULL));
```

gibt Folgendes zurück:

```Output
LC_COLLATE=en-US;LC_CTYPE=en-US;LC_MONETARY=fr-FR;LC_NUMERIC=en-US;LC_TIME=en-US
```

Dabei handelt es sich um die Zeichenfolge, die der **LC_ALL** Kategorie zugeordnet ist.

Die folgenden Beispiele beziehen sich auf die **LC_ALL** Kategorie. Beide Zeichen folgen ". OCP "und". ACP "kann anstelle einer Code Page Nummer verwendet werden, um die Verwendung der standardmäßigen OEM-Codepage des Benutzers und der standardmäßigen ANSI-Codepage des Benutzers für den jeweiligen Gebiets Schema Namen anzugeben.

- `:::no-loc(setlocale):::( LC_ALL, "" );`

   Legt das Gebietsschema auf den Standardwert fest, der die vom Betriebssystem abgerufene voreingestellte ANSI-Benutzercodepage ist. Der Gebiets Schema Name wird auf den Wert festgelegt, der von [getuserdefaultlocalename](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename)zurückgegeben wird. Die Codepage wird auf den von [GetACP](/windows/win32/api/winnls/nf-winnls-getacp)zurückgegebenen Wert festgelegt.

- `:::no-loc(setlocale):::( LC_ALL, ".OCP" );`

   Legt das Gebiets Schema auf die aktuelle OEM-Codepage fest, die vom Betriebssystem abgerufen wird. Der Gebiets Schema Name wird auf den Wert festgelegt, der von [getuserdefaultlocalename](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename)zurückgegeben wird. Die Codepage wird auf den [LOCALE_IDEFAULTCODEPAGE](/windows/win32/intl/locale-idefault-constants) Wert für den Benutzer-Standard Gebiets Schema Namen von [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex)festgelegt.

- `:::no-loc(setlocale):::( LC_ALL, ".ACP" );`

   Legt das Gebietsschema auf die vom Betriebssystem abgerufene voreingestellte ANSI-Benutzercodepage fest. Der Gebiets Schema Name wird auf den Wert festgelegt, der von [getuserdefaultlocalename](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename)zurückgegeben wird. Die Codepage wird auf den [LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) Wert für den Benutzer-Standard Gebiets Schema Namen von [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex)festgelegt.

- `:::no-loc(setlocale):::( LC_ALL, "<localename>" );`

   Legt das Gebiets Schema auf den Gebiets Schema Namen fest, der durch angegeben wird *\<localename>* . Die Codepage wird von [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex)auf den [LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) Wert für den angegebenen Gebiets Schema Namen festgelegt.

- `:::no-loc(setlocale):::( LC_ALL, "<language>_<country>" );`

   Legt das Gebiets Schema auf die Sprache und das Land/die Region fest, die durch *\<language>* und angegeben *\<country>* werden, sowie die Standard Codepage, die vom Host Betriebssystem abgerufen wird. Die Codepage wird von [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex)auf den [LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) Wert für den angegebenen Gebiets Schema Namen festgelegt.

- `:::no-loc(setlocale):::( LC_ALL, "<language>_<country>.<code_page>" );`

   Legt das Gebiets Schema auf die Sprache, das Land/die Region und die Codepage fest, die durch die Zeichen folgen *\<language>* , und angegeben werden *\<country>* *\<code_page>* . Sie können verschiedene Kombinationen von Sprache, Land/Region und Codepage verwenden. Bei diesem Aufruf wird beispielsweise das Gebetsschema auf Französisch (Kanada) festgelegt, mit der Codepage 1252:

   `:::no-loc(setlocale):::( LC_ALL, "French_Canada.1252" );`

   Bei diesem Aufruf wird das Gebietsschema auf Französisch (Kanada) mit der voreingestellten ANSI-Codepage festgelegt:

   `:::no-loc(setlocale):::( LC_ALL, "French_Canada.ACP" );`

   Bei diesem Aufruf wird das Gebietsschema auf Französisch (Kanada) mit der voreingestellten OEM-Codepage festgelegt:

   `:::no-loc(setlocale):::( LC_ALL, "French_Canada.OCP" );`

- `:::no-loc(setlocale):::( LC_ALL, "<language>" );`

   Legt das Gebiets Schema auf die Sprache fest, die von angegeben *\<language>* wird, und verwendet das Standardland bzw. die Standard Region für die angegebene Sprache und die Benutzer-Standard-ANSI-Codepage für das Land bzw. die Region, das vom Host Betriebssystem abgerufen wird. Beispielsweise sind die folgenden Aufrufe von **:::no-loc(setlocale):::** funktional äquivalent:

   `:::no-loc(setlocale):::( LC_ALL, "en-US" );`

   `:::no-loc(setlocale):::( LC_ALL, "English" );`

   `:::no-loc(setlocale):::( LC_ALL, "English_United States.1252" );`

   Aus Leistungsgründen und wegen der Wartbarkeit wird die erste Form empfohlen.

- `:::no-loc(setlocale):::( LC_ALL, ".<code_page>" );`

   Legt die Codepage auf den Wert fest, der durch *<Codepage>* angegeben ist, wobei zugleich das Standardland bzw. die Standardregion und Sprache (gemäß der Definition vom Hostbetriebssystem) für die angegebene Codepage verwendet wird.

Die Kategorie muss entweder **LC_ALL** oder **LC_CTYPE** sein, damit eine Änderung der Codepage wirksam wird. Wenn z. b. das Standardland bzw. die Standard Region und die Sprache des Host Betriebssystems "USA" und "Englisch" sind, sind die folgenden beiden Aufrufe von **:::no-loc(setlocale):::** funktional äquivalent:

`:::no-loc(setlocale):::( LC_ALL, ".1252" );`

`:::no-loc(setlocale):::( LC_ALL, "English_United States.1252");`

Weitere Informationen finden Sie in der [:::no-loc(setlocale):::](../../preprocessor/:::no-loc(setlocale):::.md) pragma-Direktive in der [C/C++-Präprozessorreferenz](../../preprocessor/c-cpp-preprocessor-reference.md).

Mithilfe der Funktion [_configthreadlocale](configthreadlocale.md) wird gesteuert, ob **:::no-loc(setlocale):::** das Gebiets Schema aller Threads in einem Programm oder nur das Gebiets Schema des aufrufenden Threads beeinflusst.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**:::no-loc(setlocale):::**|\<locale.h>|
|**:::no-loc(_wsetlocale):::**|\<locale.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_:::no-loc(setlocale):::.c
//
// This program demonstrates the use of :::no-loc(setlocale)::: when
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
           :::no-loc(setlocale):::(LC_ALL, locale));

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
           :::no-loc(setlocale):::(LC_ALL, "en-US"));

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

[Gebiets Schema Namen, Sprachen und Länder-/regionszeichenfolgen](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[_configthreadlocale](configthreadlocale.md)\
[_create_locale _wcreate_locale](create-locale-wcreate-locale.md)\
[Konfigurations](../../c-runtime-library/locale.md)\
[localeconv](localeconv.md)\
[_mbclen, Mblen, _mblen_l](mbclen-mblen-mblen-l.md)\
["strinlen", "wcslen", "_mbslen", "_mbslen_l _mbstrlen_l _mbstrlen"](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)\
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)\
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)\
[_setmbcp](setmbcp.md)\
[Funktionen von "strecoll"](../../c-runtime-library/strcoll-functions.md)\
["Strauch Zeit", "WCSF Time", "_strftime_l" _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)\
["strauxfrm", "wcsxfrm", "_strxfrm_l" _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)\
[wcstomsb, _wcstombs_l](wcstombs-wcstombs-l.md)\
[wctomb, _wctomb_l](wctomb-wctomb-l.md)
