---
title: qsort
description: Beschreibt die schnell Sortier-API der Microsoft C-Laufzeit. `qsort`
ms.date: 10/23/2020
api_name:
- qsort
- _o_qsort
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- qsort
helpviewer_keywords:
- qsort function
- quick-sort algorithm
- sorting arrays
- arrays [CRT], sorting
ms.assetid: d6cb33eb-d209-485f-8d41-229eb743c027
ms.openlocfilehash: c658ffae69cd662809eb4dac09c06b6a13f4e051
ms.sourcegitcommit: faecabcdd12ff53eb79dc0df193fc3567f2f037c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92639119"
---
# <a name="qsort"></a>qsort

Führt eine schnelle Sortierung aus. Es ist eine sicherere Version dieser Funktion verfügbar. Informationen dazu finden Sie unter [qsort_s](qsort-s.md).

## <a name="syntax"></a>Syntax

```C
void qsort(
   void *base,
   size_t number,
   size_t width,
   int (__cdecl *compare )(const void *, const void *)
);
```

### <a name="parameters"></a>Parameter

*`base`*\
Start des Zielarrays.

*`number`*\
Arraygröße in Elementen.

*`width`*\
Elementgröße in Bytes.

*`compare`*\
Zeiger auf eine benutzerdefinierte Routine, die zwei Elemente des Arrays vergleicht und einen Wert zurückgibt, der ihre Beziehung angibt.

## <a name="remarks"></a>Hinweise

Die- **`qsort`** Funktion implementiert einen Quick-Sort-Algorithmus, um ein Array von *`number`* Elementen, jeweils von Bytes, zu sortieren *`width`* . Das-Argument *`base`* ist ein Zeiger auf die Basis des Arrays, das sortiert werden soll. **`qsort`** überschreibt dieses Array mit den sortierten Elementen.

**`qsort`** Ruft die- *`compare`* Routine einmal oder mehrmals während der Sortierung auf und übergibt bei jedem Aufruf Zeiger auf zwei Array Elemente. Wenn *`compare`* anzeigt, dass zwei Elemente identisch sind, ist die Reihenfolge im sich ergebenden sortierten Array nicht angegeben.

```C
compare( (void *) & elem1, (void *) & elem2 );
```

Die Routine vergleicht die Elemente und gibt einen der folgenden Werte zurück.

|Vergleich des Rückgabewerts der Funktion|BESCHREIBUNG|
|-----------------------------------|-----------------|
|< 0|**`elem1`** kleiner als **`elem2`**|
|0|**`elem1`** Äquivalent zu **`elem2`**|
|> 0|**`elem1`** größer als **`elem2`**|

Das Array wird in aufsteigender Reihenfolge sortiert, wie von der Vergleichsfunktion definiert. Kehren Sie den Sinn der „größer als“ und „kleiner als“ in der Vergleichsfunktion um, um ein Array in absteigender Reihenfolge zu sortieren.

Diese Funktion überprüft ihre Parameter. Wenn *`compare`* oder *`number`* ist oder **`NULL`** Wenn *`base`* **`NULL`** und *`number`* nicht NULL ist, oder wenn *`width`* kleiner als 0 (null) ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, gibt die Funktion zurück, und **`errno`** wird auf festgelegt **`EINVAL`** .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**`qsort`**|\<stdlib.h> und \<search.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_qsort.c
// arguments: every good boy deserves favor

/* This program reads the command-line
* parameters and uses qsort to sort them. It
* then displays the sorted arguments.
*/

#include <stdlib.h>
#include <string.h>
#include <stdio.h>

int compare( const void *arg1, const void *arg2 );

int main( int argc, char **argv )
{
   int i;
   /* Eliminate argv[0] from sort: */
   argv++;
   argc--;

   /* Sort remaining args using Quicksort algorithm: */
   qsort( (void *)argv, (size_t)argc, sizeof( char * ), compare );

   /* Output sorted list: */
   for( i = 0; i < argc; ++i )
      printf( " %s", argv[i] );
   printf( "\n" );
}

int compare( const void *arg1, const void *arg2 )
{
   /* Compare all of both strings: */
   return _stricmp( * ( char** ) arg1, * ( char** ) arg2 );
}
```

```Output
boy deserves every favor good
```

## <a name="see-also"></a>Weitere Informationen

[Suchen und Sortieren](../../c-runtime-library/searching-and-sorting.md)\
[`bsearch`](bsearch.md)\
[`_lsearch`](lsearch.md)
