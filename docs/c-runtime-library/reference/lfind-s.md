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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 8f2983bee93c623eb936ed12422134281418076b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342188"
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

*number*<br/>
Die Anzahl der Arrayelemente.

*Größe*<br/>
Die Größe der Arrayelemente in Bytes.

*Vergleichen*<br/>
Zeiger auf die Vergleichsroutine. Der erste Parameter ist der *Kontextzeiger.* Der zweite Parameter ist ein Zeiger auf den Schlüssel für die Suche. Der dritte Parameter ist ein Zeiger auf das Arrayelement, das mit dem Schlüssel verglichen werden soll.

*context*<br/>
Ein Zeiger auf ein Objekt, auf das in der Vergleichsfunktion möglicherweise zugegriffen werden kann.

## <a name="return-value"></a>Rückgabewert

Wenn der Schlüssel gefunden wird, **gibt _lfind_s** einen Zeiger auf das Element des Arrays an der *Basis* zurück, das mit dem *Schlüssel*übereinstimmt. Wenn der Schlüssel nicht gefunden wird, **gibt _lfind_s** **NULL**zurück.

Wenn ungültige Parameter an die Funktion übergeben werden, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, wird **errno** auf **EINVAL** gesetzt, und die Funktion gibt **NULL**zurück.

### <a name="error-conditions"></a>Fehlerbedingungen

|Schlüssel|base|compare|num|size|errno|
|---------|----------|-------------|---------|----------|-----------|
|**Null**|any|any|any|any|**Einval**|
|any|**Null**|any|!= 0|any|**Einval**|
|any|any|any|any|Null|**Einval**|
|any|any|**Null**|ein|any|**Einval**|

## <a name="remarks"></a>Bemerkungen

Die **_lfind_s-Funktion** führt eine lineare Suche nach dem *Wertschlüssel* in einem Array von *Zahlenelementen* mit jeweils *mehreren* Bytes durch. Im Gegensatz zu **bsearch_s** **erfordert _lfind_s** nicht, dass das Array sortiert wird. Das *Basisargument* ist ein Zeiger auf die Basis des zu durchsuchenden Arrays. Das *Argument compare* ist ein Zeiger auf eine vom Benutzer bereitgestellte Routine, die zwei Arrayelemente vergleicht und dann einen Wert zurückgibt, der ihre Beziehung angibt. **_lfind_s** ruft die *Vergleichsroutine* ein oder mehrere Male während der Suche auf und übergibt den *Kontextzeiger* und die Zeiger an zwei Arrayelemente bei jedem Aufruf. Die *Vergleichsroutine* muss die Elemente vergleichen und dann ungleich Null zurückgeben (d. h. die Elemente sind unterschiedlich) oder 0 (d. h. die Elemente sind identisch).

**_lfind_s** ähnelt **_lfind** mit Ausnahme des Hinzufügens des *Kontextzeigers* zu den Argumenten der Vergleichsfunktion und der Parameterliste der Funktion. Der *Kontextzeiger* kann nützlich sein, wenn die gesuchte Datenstruktur Teil eines Objekts ist und die *Vergleichsfunktion* auf Member des Objekts zugreifen muss. Die *Vergleichsfunktion* kann den leeren Zeiger in den entsprechenden Objekttyp und die Zugriffselemente dieses Objekts umwerfen. Das Hinzufügen des *Kontextparameters* macht **_lfind_s** sicherer, da zusätzlicher Kontext verwendet werden kann, um Reentrancy-Fehler zu vermeiden, die mit der Verwendung statischer Variablen verbunden sind, um Daten für die *Vergleichsfunktion* verfügbar zu machen.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

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

## <a name="see-also"></a>Siehe auch

[Suchen und Sortieren](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort_s](qsort-s.md)<br/>
[_lfind](lfind.md)<br/>
