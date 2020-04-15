---
title: _lfind
ms.date: 4/2/2020
api_name:
- _lfind
- _o__lfind
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
- _lfind
helpviewer_keywords:
- linear searching
- lfind function
- arrays [CRT], searching
- searching, linear
- finding keys in arrays
- _lfind function
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
ms.openlocfilehash: 287cbd8bc9cc567a4a0d5b9505d57098197bc545
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342177"
---
# <a name="_lfind"></a>_lfind

Führt eine lineare Suche für den angegebenen Schlüssel aus. Es ist eine sicherere Version dieser Funktion verfügbar. Siehe [_lfind_s](lfind-s.md).

## <a name="syntax"></a>Syntax

```C
void *_lfind(
   const void *key,
   const void *base,
   unsigned int *num,
   unsigned int width,
   int (__cdecl *compare)(const void *, const void *)
);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Das Objekt, nach dem gesucht werden soll.

*base*<br/>
Zeiger auf die Basis der Suchdaten.

*number*<br/>
Die Anzahl der Arrayelemente.

*width*<br/>
Die Breite von Arrayelementen.

*Vergleichen*<br/>
Zeiger auf die Vergleichsroutine. Der erste Parameter ist ein Zeiger auf den Schlüssel für die Suche. Der zweite Parameter ist ein Zeiger auf das Arrayelement, das mit dem Schlüssel verglichen werden soll.

## <a name="return-value"></a>Rückgabewert

Wenn der Schlüssel gefunden wird, **gibt _lfind** einen Zeiger auf das Element des Arrays an der *Basis* zurück, das mit dem *Schlüssel*übereinstimmt. Wenn der Schlüssel nicht gefunden wird, **gibt _lfind** **NULL**zurück.

## <a name="remarks"></a>Bemerkungen

Die **_lfind-Funktion** führt eine lineare Suche nach dem *Wertschlüssel* in einem Array von *Zahlenelementen* mit jeweils *mehreren* Bytes durch. Im Gegensatz zu **bsearch** **erfordert _lfind** nicht, dass das Array sortiert wird. Das *Basisargument* ist ein Zeiger auf die Basis des zu durchsuchenden Arrays. Das *Argument compare* ist ein Zeiger auf eine vom Benutzer bereitgestellte Routine, die zwei Arrayelemente vergleicht und dann einen Wert zurückgibt, der ihre Beziehung angibt. **_lfind** ruft die *Vergleichsroutine* ein oder mehrere Male während der Suche auf und übergibt Zeiger an zwei Arrayelemente bei jedem Aufruf. Die *Vergleichsroutine* muss die Elemente vergleichen und dann ungleich Null zurückgeben (d. h. die Elemente sind unterschiedlich) oder 0 (d. h. die Elemente sind identisch).

Diese Funktion überprüft ihre Parameter. Wenn *compare*, *Key* oder *number* ist **NULL**, oder wenn *Basis* **NULL** ist und *Zahl* ungleich Null ist, oder wenn *die Breite* kleiner als Null ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, wird **errno** auf **EINVAL** gesetzt, und die Funktion gibt **NULL**zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_lfind**|\<search.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_lfind.c
// This program uses _lfind to search a string array
// for an occurrence of "hello".

#include <search.h>
#include <string.h>
#include <stdio.h>

int compare(const void *arg1, const void *arg2 )
{
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );
}

int main( )
{
   char *arr[] = {"Hi", "Hello", "Bye"};
   int n = sizeof(arr) / sizeof(char*);
   char **result;
   char *key = "hello";

   result = (char **)_lfind( &key, arr,
                      &n, sizeof(char *), compare );

   if( result )
      printf( "%s found\n", *result );
   else
      printf( "hello not found!\n" );
}
```

```Output
Hello found
```

## <a name="see-also"></a>Siehe auch

[Suchen und Sortieren](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
