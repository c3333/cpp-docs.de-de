---
title: _lfind_s
ms.date: 4/2/2020
api_name:
- _lfind_s
- _o__lfind_s
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
- api-ms-win-crt-utility-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- lfind_s
- _lfind_s
helpviewer_keywords:
- linear searching
- keys, finding in arrays
- lfind_s function
- arrays [CRT], searching
- searching, linear
- _lfind_s function
ms.assetid: f1d9581d-5c9d-4222-a31c-a6dfafefa40d
ms.openlocfilehash: 589a413c9f1fb49fbfe8cd1b5eacb9d452716523
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916507"
---
# <a name="_lfind_s"></a>_lfind_s

Führt eine lineare Suche für den angegebenen Schlüssel aus. Dies ist eine Version von [_lfind](lfind.md) mit Sicherheitserweiterungen, wie in den [Sicherheitsfunktionen in CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
void *_lfind_s(
   const void *key,
   const void *base,
   unsigned int *num,
   size_t size,
   int (__cdecl *compare)(void *, const void *, const void *),
   void * context
);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Das Objekt, nach dem gesucht werden soll.

*base*<br/>
Zeiger auf die Basis der Suchdaten.

*Zahl*<br/>
Die Anzahl der Arrayelemente.

*size*<br/>
Die Größe der Arrayelemente in Bytes.

*vergleichbar*<br/>
Zeiger auf die Vergleichsroutine. Der erste Parameter ist der *Kontext* Zeiger. Der zweite Parameter ist ein Zeiger auf den Schlüssel für die Suche. Der dritte Parameter ist ein Zeiger auf das Arrayelement, das mit dem Schlüssel verglichen werden soll.

*context*<br/>
Ein Zeiger auf ein Objekt, auf das in der Vergleichsfunktion möglicherweise zugegriffen werden kann.

## <a name="return-value"></a>Rückgabewert

Wenn der Schlüssel gefunden wird, gibt **_lfind_s** einen Zeiger auf das Element des Arrays an der *Basis* zurück, die mit dem *Schlüssel*übereinstimmt. Wenn der Schlüssel nicht gefunden wird, **_lfind_s** gibt _lfind_s **null**zurück.

Wenn ungültige Parameter an die Funktion übergeben werden, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, wird **errno** auf **EINVAL** festgelegt, und die Funktion gibt **null**zurück.

### <a name="error-conditions"></a>Fehlerbedingungen

|Schlüssel|base|compare|num|size|errno|
|---------|----------|-------------|---------|----------|-----------|
|**Normal**|any|any|any|any|**Eingabe**|
|any|**Normal**|any|!= 0|any|**Eingabe**|
|any|any|any|any|Null|**Eingabe**|
|any|any|**Normal**|ein|any|**Eingabe**|

## <a name="remarks"></a>Hinweise

Die **_lfind_s** -Funktion führt eine lineare Suche nach dem Wert *Schlüssel* in einem Array von *Zahlen* Elementen durch, wobei jede *Breite* Bytes beträgt. Anders als bei **bsearch_s**muss **_lfind_s** das Array nicht sortiert werden. Das *Basis* Argument ist ein Zeiger auf die Basis des zu durchsuchenden Arrays. Das *Compare* -Argument ist ein Zeiger auf eine vom Benutzer bereitgestellte Routine, die zwei Array Elemente vergleicht und dann einen Wert zurückgibt, der Ihre Beziehung angibt. **_lfind_s** die *Vergleichs* Routine während der Suche einmal oder mehrmals aufruft, wobei der *Kontext* Zeiger und Zeiger auf zwei Array Elemente bei jedem Aufruf übergeben werden. Die *Vergleichs* Routine muss die Elemente vergleichen und dann ungleich NULL (d.h. die Elemente unterscheiden sich) oder 0 (d.h. die Elemente sind identisch) zurückgeben.

**_lfind_s** ähnelt **_lfind** , mit Ausnahme der Addition des *Kontext* Zeigers zu den Argumenten der Vergleichsfunktion und der Parameterliste der Funktion. Der *Kontext* Zeiger kann nützlich sein, wenn die durchsuchte Datenstruktur Teil eines Objekts ist und die *Vergleichs* Funktion auf Member des Objekts zugreifen muss. Mit der *Compare* -Funktion kann der void-Zeiger in den entsprechenden Objekttyp umgewandelt und auf Member des Objekts zugegriffen werden. Durch das Hinzufügen des *Kontext* Parameters wird **_lfind_s** sicherer, da zusätzlicher Kontext verwendet werden kann, um Fehler beim erneuten eintreten zu vermeiden, die mit der Verwendung statischer Variablen zum Bereitstellen von Daten für die *Vergleichs* Funktion einhergehen.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_lfind_s**|\<search.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```cpp
// crt_lfind_s.cpp
// This program uses _lfind_s to search a string array,
// passing a locale as the context.
// compile with: /EHsc
#include <stdlib.h>
#include <stdio.h>
#include <search.h>
#include <process.h>
#include <locale.h>
#include <locale>
#include <windows.h>
using namespace std;

// The sort order is dependent on the code page.  Use 'chcp' at the
// command line to change the codepage.  When executing this application,
// the command prompt codepage must match the codepage used here:

#define CODEPAGE_850

#ifdef CODEPAGE_850
// Codepage 850 is the OEM codepage used by the command line,
// so \x00e1 is the German Sharp S

char *array1[] = { "wei\x00e1", "weis", "annehmen", "weizen", "Zeit",
                   "weit" };

#define GERMAN_LOCALE "German_Germany.850"

#endif

#ifdef CODEPAGE_1252
   // If using codepage 1252 (ISO 8859-1, Latin-1), use \x00df
   // for the German Sharp S
char *array1[] = { "wei\x00df", "weis", "annehmen", "weizen", "Zeit",
                   "weit" };

#define GERMAN_LOCALE "German_Germany.1252"

#endif

// The context parameter lets you create a more generic compare.
// Without this parameter, you would have stored the locale in a
// static variable, thus making it vulnerable to thread conflicts
// (if this were a multithreaded program).

int compare( void *pvlocale, const void *str1, const void *str2)
{
    char *s1 = *(char**)str1;
    char *s2 = *(char**)str2;

    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));

    return use_facet< collate<char> >(loc).compare(
       s1, s1+strlen(s1),
       s2, s2+strlen(s2) );
}

void find_it( char *key, char *array[], unsigned int num, locale &loc )
{
   char **result = (char **)_lfind_s( &key, array,
                      &num, sizeof(char *), compare, &loc );
   if( result )
      printf( "%s found\n", *result );
   else
      printf( "%s not found\n", key );
}

int main( )
{
   find_it( "weit", array1, sizeof(array1)/sizeof(char*), locale(GERMAN_LOCALE) );
}
```

```Output
weit found
```

## <a name="see-also"></a>Weitere Informationen

[Suchen und Sortieren](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort_s](qsort-s.md)<br/>
[_lfind](lfind.md)<br/>
