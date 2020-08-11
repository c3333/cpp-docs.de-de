---
title: setlocale, _wsetlocale
description: Beschreibt die Funktionen der Microsoft C-Lauf Zeit Bibliothek (CRT) setlocale und _wsetlocale .
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 812aab43667416a5892d8e24d03d0e67cad8d0ac
ms.sourcegitcommit: b51703a96ee35ee2376d5f0775b70f03ccbe6d9a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/11/2020
ms.locfileid: "88086993"
---
# <a name="no-locsetlocale-no-loc_wsetlocale"></a>setlocale, _wsetlocale

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

Wenn ein gültiges Gebiets Schema und eine gültige *Kategorie* angegeben werden, gibt einen Zeiger auf die Zeichenfolge zurück, die *dem angegebenen Gebiets* *Schema und der* angegebenen *Kategorie*zugeordnet ist Wenn das Gebiets *Schema oder die* *Kategorie* ungültig ist, wird ein NULL-Zeiger zurückgegeben, und die aktuellen Gebiets Schema Einstellungen des Programms sind unverändert.

Beispiel: Der Aufruf

```C
setlocale( LC_ALL, "en-US" );
```

legt alle Kategorien fest und gibt nur folgende Zeichenfolge zurück

```Output
en-US
```

Sie können die von `setlocale` zurückgegebene Zeichenfolge kopieren, um diesen Teil der Gebietsschemainformation des Programms wiederherzustellen. Lokaler globaler Speicher oder lokaler Threadspeicher wird für die von `setlocale` zurückgegebene Zeichenfolge verwendet. Spätere Aufrufe von `setlocale` überschreiben die Zeichenfolge, sodass die von früheren Aufrufen zurückgegebenen Zeichenfolgenzeiger nicht mehr gültig sind.

## <a name="remarks"></a>Bemerkungen

Verwenden `setlocale` Sie die Funktion, um einige oder alle der aktuellen Programm Gebiets Schema Informationen festzulegen, zu ändern oder *locale* abzufragen, die vom Gebiets Schema und der *Kategorie*angegeben werden. *locale* bezieht sich auf den Ort (Land/Region und Sprache), für den Sie bestimmte Aspekte des Programms anpassen können. Vom Gebietsschema abhängig sind u. a. Datumsformat und Währungsformat. Wenn Sie das Gebiets Schema auf die Standard Zeichenfolge für eine Sprache *festlegen, die* mehrere Formulare auf dem Computer unterstützt, sollten Sie den Rückgabewert überprüfen, um festzustellen, `setlocale` welche Sprache wirksam ist. Wenn Sie z. b. *locale* auf "Chinesisch" festlegen, kann der Rückgabewert entweder "Chinesisch-vereinfacht" oder "Chinesisch (traditionell)" lauten.

`_wsetlocale`ist eine breit Zeichen Version von `setlocale` . das Gebiets *locale* Schema Argument und der Rückgabewert von `_wsetlocale` sind Zeichen folgen mit breit Zeichen. `_wsetlocale` und `setlocale` verhalten sich andernfalls identisch.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tsetlocale`|`setlocale`|`setlocale`|`_wsetlocale`|

Das *Category* -Argument gibt die Teile der Gebiets Schema Informationen eines Programms an, die betroffen sind. Die für die *Kategorie* verwendeten Makros und die betroffenen Teile des Programms lauten wie folgt:

|*kategorieflag*|Betrifft|
|-|-|
| `LC_ALL` | Alle unten aufgeführten Kategorien. |
| `LC_COLLATE` | Die Funktionen `strcoll`, `_stricoll`, `wcscoll`, `_wcsicoll`, `strxfrm`, `_strncoll`, `_strnicoll`, `_wcsncoll`, `_wcsnicoll` und `wcsxfrm`. |
| `LC_CTYPE` | Die Funktionen zur Zeichenbehandlung (außer `isdigit`, `isxdigit`, `mbstowcs` und `mbtowc`, die nicht betroffen sind). |
| `LC_MONETARY` | Durch die `localeconv`-Funktion zurückgegebene Informationen zur Währungsformatierung. |
| `LC_NUMERIC` | Dezimaltrennzeichen für die formatierten Ausgaberoutinen (wie `printf`), für die Datenkonvertierungsroutinen und für die nicht monetären Formatierungsinformationen, die von `localeconv` zurückgegeben werden. Neben dem Dezimaltrennzeichen legt `LC_NUMERIC` das Tausendertrennzeichen und die Zeichenfolge für gruppierte Steuerelemente fest, die von [localeconv](localeconv.md) zurückgegeben werden. |
| `LC_TIME` | Die Funktionen `strftime` und `wcsftime`. |

Diese Funktion überprüft den Kategorienparameter. Wenn der Category-Parameter keiner der in der vorherigen Tabelle angegebenen Werte ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, legt die Funktion `errno` auf `EINVAL` fest und gibt `NULL` zurück.

Das *locale* -Argument ist ein Zeiger auf eine Zeichenfolge, die das Gebiets Schema angibt. Weitere Informationen zum *Format des Gebiets Schema Arguments finden* Sie unter Gebiets Schema [Namen, Sprachen und Länder-](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)/regionszeichenfolgen. Wenn *locale* auf eine leere Zeichenfolge zeigt, ist das Gebietsschema die durch die Implementierung definierte native Umgebung. Ein Wert von `C` gibt die Umgebung mit minimaler ANSI-Konformität für die C-Übersetzung an. Das `C`-Gebietsschema setzt als gegeben voraus, dass alle ``char``-Datentypen 1 Byte groß sind und ihr Wert immer kleiner als 256 ist.

Zum Programmstart wird die Entsprechung der folgenden Anweisung ausgeführt:

`setlocale( LC_ALL, "C" );`

Das *locale* -Argument kann einen Gebiets Schema Namen, eine Sprachen Zeichenfolge, eine Sprachen Zeichenfolge und Länder-/Regionscode, eine Codepage oder eine Sprachen Zeichenfolge, einen Länder-/Regionscode und eine Codepage annehmen. Der Satz verfügbarer Gebiets Schema Namen, Sprachen, Länder-/Regionscodes und Codepages umfasst alle vom Windows-NLS API unterstützten Gebiets Schema Namen. Die Gebietsschemanamen, die von `setlocale` unterstützt werden, wird unter[Gebietsschema-Namen, Sprachen und Zeichenfolgen für Länder/Regionen](../../c-runtime-library/locale-names-languages-and-country-region-strings.md) beschrieben. Der von `setlocale` unterstützte Satz von Sprach- und Länder-/Regionszeichenfolgen ist in [Sprachzeichenfolgen](../../c-runtime-library/language-strings.md) und [Länder-/Regionszeichenfolgen](../../c-runtime-library/country-region-strings.md) aufgeführt. Wie empfehlen die Gebietsschema-Namensform aus Gründen der Leistung und leichteren Verwaltung von Gebietsschema-Zeichenfolgen, die in Code eingebettet sind oder für den Speicher serialisiert sind. Es ist weniger wahrscheinlich, dass Gebietsschema-Zeichenfolgen durch eine Betriebssystemaktualisierung geändert werden, als dies bei der Namensform für Sprache und Land/Region der Fall ist.

Ein als Gebiets *Schema Argument* übergebener NULL-Zeiger weist `setlocale` an, die internationale Umgebung abzufragen, anstatt sie festzulegen. Wenn das *locale* -Argument ein NULL-Zeiger ist, wird die aktuelle Gebiets Schema Einstellung des Programms nicht geändert. Stattdessen `setlocale` gibt einen Zeiger auf die Zeichenfolge zurück, die der *Kategorie* des aktuellen Gebiets Schemas des Threads zugeordnet ist. Wenn das *Category* -Argument ist `LC_ALL` , gibt die Funktion eine Zeichenfolge zurück, die die aktuelle Einstellung der einzelnen Kategorien angibt, getrennt durch Semikolons. Beispiel: Die Reihenfolge der Aufrufe

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

zurück, welches die Zeichenfolge ist, die der Kategorie `LC_ALL` zugeordnet ist.

Die folgenden Beispiele gehören zur `LC_ALL`-Kategorie. Beide Zeichen folgen ". OCP "und". ACP "kann anstelle einer Code Page Nummer verwendet werden, um die Verwendung der standardmäßigen OEM-Codepage des Benutzers und der standardmäßigen ANSI-Codepage des Benutzers für den jeweiligen Gebiets Schema Namen anzugeben.

- `setlocale( LC_ALL, "" );`

   Legt das Gebietsschema auf den Standardwert fest, der die vom Betriebssystem abgerufene voreingestellte ANSI-Benutzercodepage ist. Der Gebiets Schema Name wird auf den Wert festgelegt, der von [getuserdefaultlocalename](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename)zurückgegeben wird. Die Codepage wird auf den von [GetACP](/windows/win32/api/winnls/nf-winnls-getacp)zurückgegebenen Wert festgelegt.

- `setlocale( LC_ALL, ".OCP" );`

   Legt das Gebiets Schema auf die aktuelle OEM-Codepage fest, die vom Betriebssystem abgerufen wird. Der Gebiets Schema Name wird auf den Wert festgelegt, der von [getuserdefaultlocalename](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename)zurückgegeben wird. Die Codepage wird auf den [LOCALE_IDEFAULTCODEPAGE](/windows/win32/intl/locale-idefault-constants) Wert für den Benutzer-Standard Gebiets Schema Namen von [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex)festgelegt.

- `setlocale( LC_ALL, ".ACP" );`

   Legt das Gebietsschema auf die vom Betriebssystem abgerufene voreingestellte ANSI-Benutzercodepage fest. Der Gebiets Schema Name wird auf den Wert festgelegt, der von [getuserdefaultlocalename](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename)zurückgegeben wird. Die Codepage wird auf den [LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) Wert für den Benutzer-Standard Gebiets Schema Namen von [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex)festgelegt.

- `setlocale( LC_ALL, "<localename>" );`

   Legt das Gebiets Schema auf den Gebiets Schema Namen fest, der durch angegeben wird *\<localename>* . Die Codepage wird von [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex)auf den [LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) Wert für den angegebenen Gebiets Schema Namen festgelegt.

- `setlocale( LC_ALL, "<language>_<country>" );`

   Legt das Gebiets Schema auf die Sprache und das Land/die Region fest, die durch *\<language>* und angegeben *\<country>* werden, sowie die Standard Codepage, die vom Host Betriebssystem abgerufen wird. Die Codepage wird von [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex)auf den [LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) Wert für den angegebenen Gebiets Schema Namen festgelegt.

- `setlocale( LC_ALL, "<language>_<country>.<code_page>" );`

   Legt das Gebiets Schema auf die Sprache, das Land/die Region und die Codepage fest, die durch die Zeichen folgen *\<language>* , und angegeben werden *\<country>* *\<code_page>* . Sie können verschiedene Kombinationen von Sprache, Land/Region und Codepage verwenden. Bei diesem Aufruf wird beispielsweise das Gebetsschema auf Französisch (Kanada) festgelegt, mit der Codepage 1252:

   `setlocale( LC_ALL, "French_Canada.1252" );`

   Bei diesem Aufruf wird das Gebietsschema auf Französisch (Kanada) mit der voreingestellten ANSI-Codepage festgelegt:

   `setlocale( LC_ALL, "French_Canada.ACP" );`

   Bei diesem Aufruf wird das Gebietsschema auf Französisch (Kanada) mit der voreingestellten OEM-Codepage festgelegt:

   `setlocale( LC_ALL, "French_Canada.OCP" );`

- `setlocale( LC_ALL, "<language>" );`

   Legt das Gebiets Schema auf die Sprache fest, die von angegeben *\<language>* wird, und verwendet das Standardland bzw. die Standard Region für die angegebene Sprache und die Benutzer-Standard-ANSI-Codepage für das Land bzw. die Region, das vom Host Betriebssystem abgerufen wird. Beispiel: Die folgenden Aufrufe von `setlocale` sind funktional äquivalent:

   `setlocale( LC_ALL, "en-US" );`

   `setlocale( LC_ALL, "English" );`

   `setlocale( LC_ALL, "English_United States.1252" );`

   Aus Leistungsgründen und wegen der Wartbarkeit wird die erste Form empfohlen.

- `setlocale( LC_ALL, ".<code_page>" );`

   Legt die Codepage auf den Wert fest, der durch *<Codepage>* angegeben ist, wobei zugleich das Standardland bzw. die Standardregion und Sprache (gemäß der Definition vom Hostbetriebssystem) für die angegebene Codepage verwendet wird.

Die Kategorie muss entweder `LC_ALL` oder `LC_CTYPE` sein, um eine Codepageänderung zu bewirken. Wenn z. B. das Standardland bzw. die Standardregion und die Sprache des Hostbetriebssystems "USA" und "Englisch" sind, sind die folgenden beiden Aufrufe von `setlocale` funktional äquivalent:

`setlocale( LC_ALL, ".1252" );`

`setlocale( LC_ALL, "English_United States.1252");`

Weitere Informationen finden Sie in der [setlocale](../../preprocessor/setlocale.md) pragma-Direktive in der [C/C++-Präprozessorreferenz](../../preprocessor/c-cpp-preprocessor-reference.md).

Mit der Funktion [_configthreadlocale](configthreadlocale.md) wird gesteuert, ob `setlocale` das Gebietsschema aller Threads in einem Programm betrifft oder nur das Gebietsschema des aufrufenden Threads.

## <a name="utf-8-support"></a>UTF-8-Unterstützung

Ab Windows 10 Build 17134 (April 2018 Update) unterstützt die universelle C-Runtime die Verwendung einer UTF-8-Codepage. Dies bedeutet, dass Zeichen folgen `char` , die an C-Lauf Zeitfunktionen geleitet werden, Zeichen folgen in der UTF-8-Codierung erwarten Um den UTF-8-Modus zu aktivieren, verwenden Sie "UTF-8" als Codepage, wenn Sie verwenden `setlocale` . Verwendet beispielsweise `setlocale(LC_ALL, ".utf8")` die aktuelle standardmäßige Windows-ANSI-Codepage (ACP) für das Gebiets Schema und UTF-8 für die Codepage.

Nach dem Aufrufen von `setlocale(LC_ALL, ".UTF8")` können Sie " 😊 " an übergeben, `mbtowcs` und es wird ordnungsgemäß in eine `wchar_t` Zeichenfolge übersetzt, wohingegen bisher keine Gebiets Schema Einstellung zur Verfügung stand.

Der UTF-8-Modus ist auch für Funktionen aktiviert, die in der Vergangenheit übersetzte Zeichen folgen `char` unter Verwendung der standardmäßigen Windows-ANSI-Codepage (ACP) Wenn Sie z. b. [`_mkdir("😊")`](../reference/mkdir-wmkdir.md) mit einer UTF-8-Codepage aufrufen, wird ein Verzeichnis mit diesem Emoji als Ordnernamen erstellt, anstatt dass die ACP vor der Ausführung des Programms in UTF-8 geändert werden muss. Ebenso wird beim Aufrufen [`_getcwd()`](../reference/getcwd-wgetcwd.md) von innerhalb dieses Ordners eine UTF-8-codierte Zeichenfolge zurückgegeben. Aus Kompatibilitätsgründen wird die ACP weiterhin verwendet, wenn die C-Gebiets Schema-Codepage nicht auf UTF-8 festgelegt ist.

Die folgenden Aspekte der C-Laufzeit, die nicht in der Lage sind, UTF-8 zu verwenden, da Sie während des Programmstarts festgelegt werden und die standardmäßige Windows-ANSI-Codepage (ACP) verwenden müssen: [`__argv`](../argc-argv-wargv.md) , [`_acmdln`](../acmdln-tcmdln-wcmdln.md) und [`_pgmptr`](../pgmptr-wpgmptr.md) .

Vor dieser Unterstützung waren [ `mbrtoc16` `mbrtoc32` , ](../reference/mbrtoc16-mbrtoc323.md),, [ `c16rtomb` und `c32rtomb` ](../reference/c16rtomb-c32rtomb1.md) vorhanden, um zwischen UTF-8-schmalen Zeichen folgen, UTF-16 (gleiche Codierung wie `wchar_t` auf Windows-Plattformen) und UTF-32 zu übersetzen. Aus Kompatibilitätsgründen übersetzen diese APIs immer noch nur in UTF-8 und nicht in die Codepage, die über festgelegt wird `setlocale` .

Um dieses Feature unter einem Betriebssystem vor Windows 10 (z. b. Windows 7) verwenden zu können, müssen Sie die [lokale App-Bereitstellung](../../windows/universal-crt-deployment.md#local-deployment) oder die Verknüpfung mit Version 17134 des Windows SDK oder höher verwenden. Bei Windows 10-Betriebssystemen vor 17134 wird nur die statische Verknüpfung unterstützt.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|`setlocale`|\<locale.h>|
|`_wsetlocale`|\<locale.h> oder \<wchar.h>|

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

## <a name="see-also"></a>Weitere Informationen

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
