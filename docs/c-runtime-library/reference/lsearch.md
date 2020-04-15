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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: a6ef3d86ffe8f03da34d4a374bddda1452815672
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341637"
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

*number*<br/>
Anzahl der Elemente.

*width*<br/>
Die Breite jedes Array-Elements.

*Vergleichen*<br/>
Ein Zeiger auf die Vergleichsroutine. Der erste Parameter ist ein Zeiger auf den Schlüssel für die Suche. Der zweite Parameter ist ein Zeiger auf das Arrayelement, das mit dem Schlüssel verglichen werden soll.

## <a name="return-value"></a>Rückgabewert

Wenn der Schlüssel gefunden wird, **gibt _lsearch** einen Zeiger auf das Element des Arrays an der *Basis* zurück, das mit dem *Schlüssel*übereinstimmt. Wenn der Schlüssel nicht gefunden wird, **gibt _lsearch** einen Zeiger auf das neu hinzugefügte Element am Ende des Arrays zurück.

## <a name="remarks"></a>Bemerkungen

Die **_lsearch-Funktion** führt eine lineare Suche nach dem *Wertschlüssel* in einem Array von *Zahlenelementen* mit jeweils *mehreren* Bytes durch. Im Gegensatz zu **bsearch** **erfordert _lsearch** nicht, dass das Array sortiert wird. Wenn *der Schlüssel* nicht gefunden wird, fügt **_lsearch** ihn am Ende des Arrays hinzu und erhöht die *Anzahl*.

Das *Argument compare* ist ein Zeiger auf eine vom Benutzer bereitgestellte Routine, die zwei Arrayelemente vergleicht und einen Wert zurückgibt, der ihre Beziehung angibt. **_lsearch** ruft die *Vergleichsroutine* ein oder mehrere Male während der Suche auf und übergibt Zeiger an zwei Arrayelemente bei jedem Aufruf. *compare* muss die Elemente vergleichen und entweder ungleich Null (d. h. die Elemente sind unterschiedlich) oder 0 (d. h. die Elemente sind identisch) zurückgeben.

Diese Funktion überprüft ihre Parameter. Wenn *compare*, *Key* oder *number* ist **NULL**, oder wenn *Basis* **NULL** ist und *Zahl* ungleich Null ist, oder wenn *die Breite* kleiner als Null ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, wird **errno** auf **EINVAL** gesetzt, und die Funktion gibt **NULL**zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

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

## <a name="see-also"></a>Siehe auch

[Suchen und Sortieren](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
