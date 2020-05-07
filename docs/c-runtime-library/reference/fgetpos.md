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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: b57a07dbe5c2c746e8af6b96f1864e4f4534849f
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920361"
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

*Streich*<br/>
Der Zielstream

*POS*<br/>
Speicher des Positionsindikators

## <a name="return-value"></a>Rückgabewert

Wenn der Vorgang erfolgreich ist, gibt die Funktion " **f** . Bei einem Fehler wird ein Wert ungleich 0 (null) zurückgegeben, und **errno** wird auf eine der folgenden Manifest-Konstanten (definiert in stdio) festgelegt. H): **EBADF**, d. H. der angegebene Stream ist kein gültiger Dateizeiger, oder der Zugriff darauf ist nicht möglich, oder **EINVAL**, d. H. der *Streamwert* oder der Wert von *POS* ist ungültig, z. b. Wenn ein NULL-Zeiger ist. Wenn *Stream* oder *POS* ein **null** -Zeiger ist, ruft die Funktion den Handler für ungültige Parameter auf, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben.

## <a name="remarks"></a>Hinweise

Die **fgetpos** -Funktion Ruft den aktuellen Wert des Datei Positions Indikators des *Stream* -Arguments ab und speichert ihn in dem Objekt, auf *das von Torys verwiesen wird.* Die **fsetpos** -Funktion kann später in *POS* gespeicherte Informationen verwenden, um den Zeiger des *Stream* -Arguments auf seine Position zum Zeitpunkt des Aufrufs von **fgetpos** zurückzusetzen. Der *POS* -Wert wird in einem internen Format gespeichert und ist nur für die Verwendung durch " **f** " und " **ssetpos**" vorgesehen.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

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

## <a name="see-also"></a>Weitere Informationen

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[fsetpos](fsetpos.md)<br/>
