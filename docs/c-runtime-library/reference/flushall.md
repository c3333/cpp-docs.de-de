---
title: _flushall
description: API-Referenz für _flushall; , der alle Streams leert und alle Puffer löscht.
ms.date: 4/2/2020
api_name:
- _flushall
- _o__flushall
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _flushall
helpviewer_keywords:
- flushall function
- flushing streams
- streams, flushing
- _flushall function
ms.assetid: 2cd73562-6d00-4ca2-b13c-80d0ae7870b5
ms.openlocfilehash: c93dddea50c182b86bd4d09ae9f214e87491e830
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556722"
---
# <a name="_flushall"></a>_flushall

Leert alle Streams und löscht alle Puffer.

## <a name="syntax"></a>Syntax

```C
int _flushall( void );
```

## <a name="return-value"></a>Rückgabewert

**_flushall** gibt die Anzahl der geöffneten Streams (Eingabe und Ausgabe) zurück. Es gibt keine Fehlerrückgabe.

## <a name="remarks"></a>Hinweise

Standardmäßig schreibt die **_flushall** -Funktion den Inhalt aller Puffer, die mit geöffneten Ausgabestreams verknüpft sind, in die entsprechenden Dateien. Aus allen Puffern, die geöffneten Eingabestreams zugeordnet sind, wird der aktuelle Inhalt gelöscht. (Diese Puffer werden normalerweise vom Betriebssystem verwaltet, das die optimale Zeit zum automatischen Schreiben der Daten auf den Datenträger bestimmt: wenn ein Puffer ist voll, wenn ein Stream geschlossen wird oder wenn ein Programm normal beendet wird, ohne die Streams zu schließen.)

Wenn ein Lesevorgang auf einen **_flushall**-Aufrufe folgt, werden neue Daten aus den Eingabedateien in die Puffer gelesen. Alle Streams bleiben nach dem aufzurufenden **_flushall**geöffnet.

Mit der Datenträgercommitfunktion der Laufzeitbibliothek können Sie sicherstellen, dass wichtige Daten direkt auf den Datenträger anstatt in die Betriebssystempuffer geschrieben werden. Wenn Sie ein vorhandenes Programm nicht umschreiben, können Sie diese Funktion aktivieren, indem Sie die Objektdateien des Programms mit "COMMODE. obj" verknüpfen. In der resultierenden ausführbaren Datei **_flushall** den Inhalt aller Puffer auf den Datenträger schreiben. COMMODE. obj wirkt sich nur auf **_flushall** und [fflush](fflush.md) aus.

Weitere Informationen zum Steuern der Datenträgercommitfunktion finden Sie unter [Stream-E/A](../../c-runtime-library/stream-i-o.md), [fopen](fopen-wfopen.md) und [_fdopen](fdopen-wfdopen.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**_flushall**|\<stdio.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_flushall.c
// This program uses _flushall
// to flush all open buffers.

#include <stdio.h>

int main( void )
{
   int numflushed;

   numflushed = _flushall();
   printf( "There were %d streams flushed\n", numflushed );
}
```

```Output
There were 3 streams flushed
```

## <a name="see-also"></a>Weitere Informationen

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[_commit](commit.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[setvbuf](setvbuf.md)<br/>
