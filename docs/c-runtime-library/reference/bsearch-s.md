---
title: bsearch_s
ms.date: 4/2/2020
api_name:
- bsearch_s
- _o_bsearch_s
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- bsearch_s
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch_s function
ms.assetid: d5690d5e-6be3-4f1d-aa0b-5ca6dbded276
ms.openlocfilehash: ef8a68f0db45e718af6b17fe0d08c33a6fd61d6c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333847"
---
# <a name="bsearch_s"></a>bsearch_s

Führt eine binäre Suche eines sortierten Arrays aus. Diese Funktion ist eine Version von [bsearch](bsearch.md) mit Sicherheitsverbesserungen, wie unter [Sicherheitsfeatures in der CRT](../../c-runtime-library/security-features-in-the-crt.md)beschrieben.

## <a name="syntax"></a>Syntax

```C
void *bsearch_s(
   const void *key,
   const void *base,
   size_t number,
   size_t width,
   int ( __cdecl *compare ) ( void *, const void *key, const void *datum),
   void * context
);
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Zeiger auf die zu suchende Taste.

*Basis*\
Zeiger auf die Basis der Suchdaten.

*Anzahl*\
Anzahl der Elemente.

*Breite*\
Breite der Elemente.

*Vergleichen*\
Rückruffunktion, die zwei Elemente vergleicht. Das erste Argument ist der *Kontextzeiger.* Das zweite Argument ist ein Zeiger auf den *Schlüssel* für die Suche. Das dritte Argument ist ein Zeiger auf das Arrayelement, das mit *key*verglichen werden soll.

*Kontext*\
Ein Zeiger auf ein Objekt, auf das in der Vergleichsfunktion zugegriffen werden kann.

## <a name="return-value"></a>Rückgabewert

**bsearch_s** gibt einen Zeiger auf ein Vorkommen des *Schlüssels* im Array zurück, auf das von *Base*verwiesen wird. Wenn der *Schlüssel* nicht gefunden wird, gibt die Funktion **NULL**zurück. Wenn das Array nicht in aufsteigender Reihenfolge sortiert ist oder doppelte Datensätze mit identischen Schlüsseln enthält, ist das Ergebnis nicht vorhersehbar.

Wenn ungültige Parameter an die Funktion übergeben werden, ruft sie den ungültigen Parameterhandler auf, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, wird **errno** auf **EINVAL** gesetzt, und die Funktion gibt **NULL**zurück. Weitere Informationen finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Fehlerbedingungen

|||||||
|-|-|-|-|-|-|
|*key*|*base*|*Vergleichen*|*number*|*width*|**errno**|
|**Null**|any|any|any|any|**Einval**|
|any|**Null**|any|!= 0|any|**Einval**|
|any|any|any|any|= 0|**Einval**|
|any|any|**Null**|ein|any|**Einval**|

## <a name="remarks"></a>Bemerkungen

Die **bsearch_s-Funktion** führt eine binäre Suche nach einem sortierten Array von *Zahlenelementen* durch, die jeweils eine Größe von *Breitenbytes* aufweisen. Der *Basiswert* ist ein Zeiger auf die Basis des zu durchsuchenden Arrays, und *der Schlüssel* ist der gesuchte Wert. Der *Vergleichsparameter* ist ein Zeiger auf eine vom Benutzer bereitgestellte Routine, die den angeforderten Schlüssel mit einem Arrayelement vergleicht und einen der folgenden Werte zurückgibt, der deren Beziehung angibt:

|Wert, der von *der Vergleichsroutine* zurückgegeben wird|BESCHREIBUNG|
|-----------------------------------------|-----------------|
|\< 0|Der Schlüssel ist kleiner als das Arrayelement.|
|0|Schlüssel und Arrayelement sind gleich.|
|> 0|Der Schlüssel ist größer als das Arrayelement.|

Der *Kontextzeiger* kann nützlich sein, wenn die gesuchte Datenstruktur Teil eines Objekts ist und die Vergleichsfunktion auf Member des Objekts zugreifen muss. Die *Vergleichsfunktion* kann den leeren Zeiger in den entsprechenden Objekttyp und die Zugriffsmember dieses Objekts umwerfen. Das Hinzufügen des *Kontextparameters* macht **bsearch_s** sicherer, da zusätzlicher Kontext verwendet werden kann, um Reentrancy-Fehler zu vermeiden, die mit der Verwendung statischer Variablen verbunden sind, um Daten für die *Vergleichsfunktion* verfügbar zu machen.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**bsearch_s**|\<stdlib.h> und \<search.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Dieses Programm sortiert ein Zeichenfolgenarray mit [qsort_s](qsort-s.md) und verwendet anschließend „bsearch_s“, um nach dem Wort „cat“ zu suchen.

```cpp
// crt_bsearch_s.cpp
// This program uses bsearch_s to search a string array,
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
#define ENGLISH_LOCALE "English_US.850"
#endif

#ifdef CODEPAGE_1252
#define ENGLISH_LOCALE "English_US.1252"
#endif

// The context parameter lets you create a more generic compare.
// Without this parameter, you would have stored the locale in a
// static variable, thus making it vulnerable to thread conflicts
// (if this were a multithreaded program).

int compare( void *pvlocale, char **str1, char **str2)
{
    char *s1 = *str1;
    char *s2 = *str2;

    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));

    return use_facet< collate<char> >(loc).compare(
       s1, s1+strlen(s1),
       s2, s2+strlen(s2) );
}

int main( void )
{
   char *arr[] = {"dog", "pig", "horse", "cat", "human", "rat", "cow", "goat"};

   char *key = "cat";
   char **result;
   int i;

   /* Sort using Quicksort algorithm: */
   qsort_s( arr,
            sizeof(arr)/sizeof(arr[0]),
            sizeof( char * ),
            (int (*)(void*, const void*, const void*))compare,
            &locale(ENGLISH_LOCALE) );

   for( i = 0; i < sizeof(arr)/sizeof(arr[0]); ++i )    /* Output sorted list */
      printf( "%s ", arr[i] );

   /* Find the word "cat" using a binary search algorithm: */
   result = (char **)bsearch_s( &key,
                                arr,
                                sizeof(arr)/sizeof(arr[0]),
                                sizeof( char * ),
                                (int (*)(void*, const void*, const void*))compare,
                                &locale(ENGLISH_LOCALE) );
   if( result )
      printf( "\n%s found at %Fp\n", *result, result );
   else
      printf( "\nCat not found!\n" );
}
```

```Output
cat cow dog goat horse human pig rat
cat found at 002F0F04
```

## <a name="see-also"></a>Siehe auch

[Suchen und Sortieren](../../c-runtime-library/searching-and-sorting.md)\
[_lfind](lfind.md)\
[_lsearch](lsearch.md)\
[qsort](qsort.md)
