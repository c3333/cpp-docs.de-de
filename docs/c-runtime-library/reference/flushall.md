---
title: _flushall
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 93181c0fe941a1c5e259e706771495666329bcb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346625"
---
# <a name="_flushall"></a>_flushall

Leert alle Streams und löscht alle Puffer.

## <a name="syntax"></a>Syntax

```C
int _flushall( void );
```

## <a name="return-value"></a>Rückgabewert

**_flushall** gibt die Anzahl der offenen Streams (Eingang und Ausgang) zurück. Es gibt keine Fehlerrückgabe.

## <a name="remarks"></a>Bemerkungen

Standardmäßig schreibt die **_flushall-Funktion** in entsprechende Dateien den Inhalt aller Puffer, die offenen Ausgabestreams zugeordnet sind. Aus allen Puffern, die geöffneten Eingabestreams zugeordnet sind, wird der aktuelle Inhalt gelöscht. (Diese Puffer werden normalerweise vom Betriebssystem verwaltet, das die optimale Zeit zum automatischen Schreiben der Daten auf den Datenträger bestimmt: wenn ein Puffer ist voll, wenn ein Stream geschlossen wird oder wenn ein Programm normal beendet wird, ohne die Streams zu schließen.)

Wenn ein Lesefehler auf einen Aufruf **von _flushall**folgt, werden neue Daten aus den Eingabedateien in die Puffer gelesen. Alle Streams bleiben nach dem Aufruf zu **_flushall**geöffnet.

Mit der Datenträgercommitfunktion der Laufzeitbibliothek können Sie sicherstellen, dass wichtige Daten direkt auf den Datenträger anstatt in die Betriebssystempuffer geschrieben werden. Ohne ein vorhandenes Programm neu zu schreiben, können Sie diese Funktion aktivieren, indem Sie die Objektdateien des Programms mit Commode.obj verknüpfen. In der resultierenden ausführbaren Datei schreiben Aufrufe von **_flushall** den Inhalt aller Puffer auf den Datenträger. Nur **_flushall** und [fflush](fflush.md) sind von Commode.obj betroffen.

Weitere Informationen zum Steuern der Datenträgercommitfunktion finden Sie unter [Stream-E/A](../../c-runtime-library/stream-i-o.md), [fopen](fopen-wfopen.md) und [_fdopen](fdopen-wfdopen.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

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

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[_commit](commit.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[setvbuf](setvbuf.md)<br/>
