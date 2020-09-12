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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 348638b2a6b5a97491d9929b22a983b43794da9a
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041626"
---
# <a name="bsearch_s"></a>bsearch_s

Führt eine binäre Suche eines sortierten Arrays aus. Diese Funktion ist eine Version von [bsearch](bsearch.md) mit Sicherheitsverbesserungen, wie in [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md)beschrieben.

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

*wichtigen*\
Zeiger auf den Schlüssel, nach dem gesucht werden soll.

*sock*\
Ein Zeiger auf die Basis der Suchdaten.

*einigen*\
Anzahl der Elemente.

*Breite*\
Breite der Elemente.

*vergleichbar*\
Rückruffunktion, die zwei Elemente vergleicht. Das erste Argument ist der *Kontext* Zeiger. Das zweite Argument ist ein Zeiger auf den *Schlüssel* für die Suche. Das dritte Argument ist ein Zeiger auf das Array Element, das mit *Key*verglichen werden soll.

*Kontext*\
Ein Zeiger auf ein Objekt, auf das in der Vergleichsfunktion zugegriffen werden kann.

## <a name="return-value"></a>Rückgabewert

**bsearch_s** gibt einen Zeiger auf ein Vorkommen von *Key* in dem Array zurück, auf das von *Base*verwiesen wird. Wenn *Key* nicht gefunden wird, gibt die Funktion **null**zurück. Wenn das Array nicht in aufsteigender Reihenfolge sortiert ist oder doppelte Datensätze mit identischen Schlüsseln enthält, ist das Ergebnis nicht vorhersehbar.

Wenn ungültige Parameter an die Funktion übergeben werden, ruft Sie den Handler für ungültige Parameter auf, wie unter [Parameter Validierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die weitere Ausführung zugelassen wird, wird **errno** auf **EINVAL** festgelegt, und die Funktion gibt **null**zurück. Weitere Informationen finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Fehlerbedingungen

|*key*|*base*|*vergleichbar*|*Zahl*|*width*|**`errno`** Wert|
|-|-|-|-|-|-|
|**NULL**|any|any|any|any|**Eingabe**|
|any|**NULL**|any|!= 0|any|**Eingabe**|
|any|any|any|any|= 0|**Eingabe**|
|any|any|**NULL**|ein|any|**Eingabe**|

## <a name="remarks"></a>Bemerkungen

Die **bsearch_s** -Funktion führt eine binäre Suche eines sortierten Arrays aus *Zahlen* Elementen durch, wobei jede *Breite* Byte groß ist. Der *Basiswert* ist ein Zeiger auf die Basis des zu durchsuchenden Arrays, und *Key* ist der Wert, der gesucht wird. Der *Compare* -Parameter ist ein Zeiger auf eine vom Benutzer bereitgestellte Routine, die den angeforderten Schlüssel mit einem Array Element vergleicht und einen der folgenden Werte zurückgibt, die die zugehörige Beziehung angeben:

|Von der *Vergleichs* Routine zurückgegebener Wert|BESCHREIBUNG|
|-----------------------------------------|-----------------|
|\< 0|Der Schlüssel ist kleiner als das Arrayelement.|
|0|Schlüssel und Arrayelement sind gleich.|
|> 0|Der Schlüssel ist größer als das Arrayelement.|

Der *Kontext* Zeiger kann nützlich sein, wenn die durchsuchte Datenstruktur Teil eines Objekts ist und die Vergleichsfunktion auf Member des Objekts zugreifen muss. Mit der *Compare* -Funktion kann der void-Zeiger in den entsprechenden Objekttyp umgewandelt und auf Member des Objekts zugegriffen werden. Durch das Hinzufügen des *Kontext* Parameters wird **bsearch_s** sicherer, da zusätzlicher Kontext verwendet werden kann, um Fehler beim erneuten eintreten zu vermeiden, die mit der Verwendung statischer Variablen zum Bereitstellen von Daten für die *Vergleichs* Funktion einhergehen.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
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

## <a name="see-also"></a>Weitere Informationen

[Suchen und Sortieren](../../c-runtime-library/searching-and-sorting.md)\
[_lfind](lfind.md)\
[_lsearch](lsearch.md)\
[qsort](qsort.md)
