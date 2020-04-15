---
title: fgetpos
ms.date: 4/2/2020
api_name:
- fgetpos
- _o_fgetpos
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
- fgetpos
helpviewer_keywords:
- fgetpos function
- streams, file position indicator
ms.assetid: bfa05c38-1135-418c-bda1-d41be51acb62
ms.openlocfilehash: 0c16150a6240068e1453ec90b396c87ab9ece5a4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346914"
---
# <a name="fgetpos"></a>fgetpos

Ruft den Dateipositionsindikator eines Streams ab

## <a name="syntax"></a>Syntax

```C
int fgetpos(
   FILE *stream,
   fpos_t *pos
);
```

### <a name="parameters"></a>Parameter

*Stream*<br/>
Der Zielstream

*Pos*<br/>
Speicher des Positionsindikators

## <a name="return-value"></a>Rückgabewert

Wenn dies erfolgreich ist, gibt **fgetpos** 0 zurück. Bei einem Fehler gibt er einen Wert ungleich Null zurück und legt **errno** auf eine der folgenden Manifestkonstanten fest (definiert in STDIO). H): **EBADF**, was bedeutet, dass der angegebene Stream kein gültiger Dateizeiger ist oder nicht zugänglich ist, oder **EINVAL**, was bedeutet, dass der *Streamwert* oder der Wert von *pos* ungültig ist, z. B. wenn einer der beiden Einen Nullzeiger ist. Wenn *Stream* oder *pos* ein **NULL-Zeiger** ist, ruft die Funktion den ungültigen Parameterhandler auf, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben.

## <a name="remarks"></a>Bemerkungen

Die **fgetpos-Funktion** ruft den aktuellen Wert des Dateipositionsindikators des *Stream-Arguments* ab und speichert ihn im Objekt, auf das *pos*zeigt. Die **fsetpos-Funktion** kann später Informationen verwenden, die in *pos* gespeichert sind, um den Zeiger des *Streamarguments* auf seine Position zum Zeitpunkt des Aufrufs von **fgetpos** zurückzusetzen. Der *pos-Wert* wird in einem internen Format gespeichert und ist nur für die Verwendung durch **fgetpos** und **fsetpos**bestimmt.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**fgetpos**|\<stdio.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_fgetpos.c
// This program uses fgetpos and fsetpos to
// return to a location in a file.

#include <stdio.h>

int main( void )
{
   FILE   *stream;
   fpos_t pos;
   char   buffer[20];

   if( fopen_s( &stream, "crt_fgetpos.txt", "rb" ) ) {
      perror( "Trouble opening file" );
      return -1;
   }

   // Read some data and then save the position.
   fread( buffer, sizeof( char ), 8, stream );
   if( fgetpos( stream, &pos ) != 0 ) {
      perror( "fgetpos error" );
      return -1;
   }

   fread( buffer, sizeof( char ), 13, stream );
   printf( "after fgetpos: %.13s\n", buffer );

   // Restore to old position and read data
   if( fsetpos( stream, &pos ) != 0 ) {
      perror( "fsetpos error" );
      return -1;
   }

   fread( buffer, sizeof( char ), 13, stream );
   printf( "after fsetpos: %.13s\n", buffer );
   fclose( stream );
}
```

## <a name="input-crt_fgetpostxt"></a>Eingabe: crt_fgetpos.txt

```Input
fgetpos gets a stream's file-position indicator.
```

### <a name="output-crt_fgetpostxt"></a>Ausgabe: crt_fgetpos.txt

```Output
after fgetpos: gets a stream
after fsetpos: gets a stream
```

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[fsetpos](fsetpos.md)<br/>
