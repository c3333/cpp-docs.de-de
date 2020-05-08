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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 4721ba96e145b3c2fde4ce0bb73157bbbcab4dff
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916460"
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

*Zahl*<br/>
Die Anzahl der Arrayelemente.

*width*<br/>
Die Breite von Arrayelementen.

*vergleichbar*<br/>
Zeiger auf die Vergleichsroutine. Der erste Parameter ist ein Zeiger auf den Schlüssel für die Suche. Der zweite Parameter ist ein Zeiger auf das Arrayelement, das mit dem Schlüssel verglichen werden soll.

## <a name="return-value"></a>Rückgabewert

Wenn der Schlüssel gefunden wird, gibt **_lfind** einen Zeiger auf das Element des Arrays an der *Basis* zurück, die mit dem *Schlüssel*übereinstimmt. Wenn der Schlüssel nicht gefunden wird, **_lfind** gibt _lfind **null**zurück.

## <a name="remarks"></a>Hinweise

Die **_lfind** -Funktion führt eine lineare Suche nach dem Wert *Schlüssel* in einem Array von *Zahlen* Elementen durch, wobei jede *Breite* Bytes beträgt. Anders als bei **bsearch**erfordert **_lfind** nicht, dass das Array sortiert wird. Das *Basis* Argument ist ein Zeiger auf die Basis des zu durchsuchenden Arrays. Das *Compare* -Argument ist ein Zeiger auf eine vom Benutzer bereitgestellte Routine, die zwei Array Elemente vergleicht und dann einen Wert zurückgibt, der Ihre Beziehung angibt. **_lfind** die *Vergleichs* Routine während der Suche einmal oder mehrmals aufruft, wobei bei jedem Aufruf Zeiger auf zwei Array Elemente übergeben werden. Die *Vergleichs* Routine muss die Elemente vergleichen und dann ungleich NULL (d.h. die Elemente unterscheiden sich) oder 0 (d.h. die Elemente sind identisch) zurückgeben.

Diese Funktion überprüft ihre Parameter. Wenn *Compare*, *Key* oder *Number* **null**ist, oder wenn *Base* **null** und *Number* ungleich NULL ist, oder wenn *Width* kleiner als 0 (null) ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, wird **errno** auf **EINVAL** festgelegt, und die Funktion gibt **null**zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

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

## <a name="see-also"></a>Weitere Informationen

[Suchen und Sortieren](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
