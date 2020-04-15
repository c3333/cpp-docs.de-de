---
title: setvbuf
ms.date: 4/2/2020
api_name:
- setvbuf
- _o_setvbuf
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
- setvbuf
helpviewer_keywords:
- controlling stream buffering
- stream buffering
- setvbuf function
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
ms.openlocfilehash: 203265a8dd85854bcedd737359b856fdc4cce04d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316264"
---
# <a name="setvbuf"></a>setvbuf

Steuert die Streampufferung und die Puffergröße.

## <a name="syntax"></a>Syntax

```C
int setvbuf(
   FILE *stream,
   char *buffer,
   int mode,
   size_t size
);
```

### <a name="parameters"></a>Parameter

*Stream*<br/>
Zeiger auf die **FILE**-Struktur.

*Puffer*<br/>
Vom Benutzer zugeordneter Speicher.

*Modus*<br/>
Pufferungsmodus.

*Größe*<br/>
Puffergröße in Bytes. Zulässiger Bereich: 2 <= *Größe* <= INT_MAX (2147483647). Intern wird der für *die Größe* angegebene Wert auf das nächste Vielfache von 2 abgerundet.

## <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg 0 zurück.

Wenn *der Stream* **NULL**ist oder der *Modus* oder die *Größe* nicht innerhalb einer gültigen Änderung liegt, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung weiterhin zugelassen wird, gibt diese Funktion -1 zurück und legt **errno** auf **EINVAL** fest.

Weitere Informationen zu diesen und anderen Fehlercodes finden Sie unter [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **setvbuf-Funktion** ermöglicht es dem Programm, sowohl die Pufferung als auch die Puffergröße für *stream*zu steuern. *Stream* muss sich auf eine geöffnete Datei beziehen, die seit dem Öffnen keiner E/A-Operation unterzogen wurde. Das Array, auf das durch *Puffer* verwiesen wird, wird als Puffer verwendet, es sei denn, \* es ist **NULL**, in diesem Fall verwendet **setvbuf** einen automatisch zugewiesenen Puffer der *Längengröße*/2 2 Bytes.

Der Modus muss **_IOFBF**, **_IOLBF**oder **_IONBF**sein. Wenn der *Modus* **_IOFBF** oder **_IOLBF**ist, wird die *Größe* als Größe des Puffers verwendet. Wenn *der Modus* **_IONBF**ist, wird der Stream entpuffert, und *Größe* und *Puffer* werden ignoriert. Werte für *den Modus* und ihre Bedeutung sind:

|*Moduswert*|Bedeutung|
|-|-|
| **_IOFBF** | Vollständige Pufferung; Das heißt, *Puffer* wird als Puffer und *Größe* als Größe des Puffers verwendet. Wenn *Puffer* **NULL**ist, wird eine automatisch zugewiesene *Puffergröße* Bytes long verwendet. |
| **_IOLBF** | Für einige Systeme bietet dies Zeilenpufferung. Für Win32 ist das Verhalten jedoch das gleiche wie **_IOFBF** - Vollpufferung. |
| **_IONBF** | Es wird kein Puffer verwendet, unabhängig von *Puffer* oder *Größe*. |

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**setvbuf**|\<stdio.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

```C
// crt_setvbuf.c
// This program opens two streams: stream1
// and stream2. It then uses setvbuf to give stream1 a
// user-defined buffer of 1024 bytes and stream2 no buffer.
//

#include <stdio.h>

int main( void )
{
   char buf[1024];
   FILE *stream1, *stream2;

   if( fopen_s( &stream1, "data1", "a" ) == 0 &&
       fopen_s( &stream2, "data2", "w" ) == 0 )
   {
      if( setvbuf( stream1, buf, _IOFBF, sizeof( buf ) ) != 0 )
         printf( "Incorrect type or size of buffer for stream1\n" );
      else
         printf( "'stream1' now has a buffer of 1024 bytes\n" );
      if( setvbuf( stream2, NULL, _IONBF, 0 ) != 0 )
         printf( "Incorrect type or size of buffer for stream2\n" );
      else
         printf( "'stream2' now has no buffer\n" );
      _fcloseall();
   }
}
```

```Output
'stream1' now has a buffer of 1024 bytes
'stream2' now has no buffer
```

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[setbuf](setbuf.md)<br/>
