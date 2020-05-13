---
title: _lsearch
ms.date: 4/2/2020
api_name:
- _lsearch
- _o__lsearch
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
- _lsearch
helpviewer_keywords:
- _lsearch function
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- linear searches
- searching, linear
- lsearch function
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
ms.openlocfilehash: 73bc82ed57692dee348448d2b523961324203ca9
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911333"
---
# <a name="_lsearch"></a>_lsearch

Führt eine lineare Suche nach einem Wert aus. Fügt ihn am Ende der Liste hinzu, falls nicht gefunden. Es ist eine sicherere Version dieser Funktion verfügbar. Informationen dazu finden Sie unter [_lsearch_s](lsearch-s.md).

## <a name="syntax"></a>Syntax

```C
void *_lsearch(
   const void *key,
   void *base,
   unsigned int *num,
   unsigned int width,
   int (__cdecl *compare)(const void *, const void *)
);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Das Objekt, nach dem gesucht werden soll.

*base*<br/>
Zeiger auf der Basis des zu durchsuchenden Arrays.

*Zahl*<br/>
Anzahl der Elemente.

*width*<br/>
Die Breite jedes Array-Elements.

*vergleichbar*<br/>
Ein Zeiger auf die Vergleichsroutine. Der erste Parameter ist ein Zeiger auf den Schlüssel für die Suche. Der zweite Parameter ist ein Zeiger auf das Arrayelement, das mit dem Schlüssel verglichen werden soll.

## <a name="return-value"></a>Rückgabewert

Wenn der Schlüssel gefunden wird, gibt **_lsearch** einen Zeiger auf das Element des Arrays an der *Basis* zurück, die mit dem *Schlüssel*übereinstimmt. Wenn der Schlüssel nicht gefunden wird, gibt **_lsearch** einen Zeiger auf das neu hinzugefügte Element am Ende des Arrays zurück.

## <a name="remarks"></a>Hinweise

Die **_lsearch** -Funktion führt eine lineare Suche nach dem Wert *Schlüssel* in einem Array von *Zahlen* Elementen durch, wobei jede *Breite* Bytes beträgt. Anders als bei **bsearch**erfordert **_lsearch** nicht, dass das Array sortiert wird. Wenn *Key* nicht gefunden wird, fügt **_lsearch** ihn am Ende des Arrays hinzu und erhöht die *Zahl*.

Das *Compare* -Argument ist ein Zeiger auf eine vom Benutzer bereitgestellte Routine, die zwei Array Elemente vergleicht und einen Wert zurückgibt, der Ihre Beziehung angibt. **_lsearch** die *Vergleichs* Routine während der Suche einmal oder mehrmals aufruft, wobei bei jedem Aufruf Zeiger auf zwei Array Elemente übergeben werden. *Compare* muss die Elemente vergleichen und entweder ungleich NULL (d.h. die Elemente unterscheiden sich) oder 0 (d.h. die Elemente sind identisch) zurückgeben.

Diese Funktion überprüft ihre Parameter. Wenn *Compare*, *Key* oder *Number* **null**ist, oder wenn *Base* **null** und *Number* ungleich NULL ist, oder wenn *Width* kleiner als 0 (null) ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, wird **errno** auf **EINVAL** festgelegt, und die Funktion gibt **null**zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_lsearch**|\<search.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_lsearch.c
#include <search.h>
#include <string.h>
#include <stdio.h>

int compare( const void *arg1, const void *arg2 );

int main(void)
{
   char * wordlist[4] = { "hello", "thanks", "bye" };
                            // leave room to grow...
   int n = 3;
   char **result;
   char *key = "extra";
   int i;

   printf( "wordlist before _lsearch:" );
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );
   printf( "\n" );

   result = (char **)_lsearch( &key, wordlist,
                      &n, sizeof(char *), compare );

   printf( "wordlist after _lsearch:" );
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );
   printf( "\n" );
}

int compare(const void *arg1, const void *arg2 )
{
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );
}
```

```Output
wordlist before _lsearch: hello thanks bye
wordlist after _lsearch: hello thanks bye extra
```

## <a name="see-also"></a>Weitere Informationen

[Suchen und Sortieren](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
