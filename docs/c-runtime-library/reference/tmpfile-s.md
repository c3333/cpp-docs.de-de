---
title: tmpfile_s
ms.date: 4/2/2020
api_name:
- tmpfile_s
- _o_tmpfile_s
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
- tmpfile_s
helpviewer_keywords:
- temporary files
- tmpfile_s function
- temporary files, creating
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
ms.openlocfilehash: 48c599887a8a903d52c7dcd46b98046119c9d3ad
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919932"
---
# <a name="tmpfile_s"></a>tmpfile_s

Erstellt eine temporäre Datei. Dies ist eine Version von [tmpfile](tmpfile.md) mit Sicherheitserweiterungen wie in [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t tmpfile_s(
   FILE** pFilePtr
);
```

### <a name="parameters"></a>Parameter

*pFilePtr*<br/>
Die Adresse eines Zeigers, um die Adresse des generierten Zeigers in einen Stream zu speichern.

## <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg 0 (null) zurück und einen Fehlercode, wenn ein Fehler auftritt.

### <a name="error-conditions"></a>Fehlerbedingungen

|*pFilePtr*|**Rückgabewert**|**Inhalt von**  *pFilePtr*|
|----------------|----------------------|---------------------------------|
|**Normal**|**Eingabe**|nicht geändert|

Wenn der obengenannte Parametervalidierungsfehler auftritt, wird der ungültige Parameterhandler wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben aufgerufen. Wenn die weitere Ausführung zugelassen wird, wird **errno** auf **EINVAL** festgelegt, und der Rückgabewert ist **EINVAL**.

## <a name="remarks"></a>Hinweise

Die **tmpfile_s** -Funktion erstellt eine temporäre Datei und legt einen Zeiger auf diesen Stream im *pFilePtr* -Argument ab. Die temporäre Datei wird im Stammverzeichnis erstellt. Verwenden Sie zum Erstellen einer temporären Datei in einem anderen Verzeichnis als dem Stammverzeichnis [tmpnam_s](tmpnam-s-wtmpnam-s.md) oder [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) in Verbindung mit [fopen](fopen-wfopen.md).

Wenn die Datei nicht geöffnet werden kann, wird von **tmpfile_s** **null** in den *pFilePtr* -Parameter geschrieben. Diese temporäre Datei wird automatisch gelöscht, wenn die Datei geschlossen wird, wenn das Programm normal beendet wird, oder wenn **_rmtmp** aufgerufen wird, vorausgesetzt, dass das aktuelle Arbeitsverzeichnis nicht geändert wird. Die temporäre Datei wird im Modus " **w + b** " (binärer Lese-/Schreibmodus) geöffnet.

Ein Fehler kann auftreten, wenn Sie mehr als **TMP_MAX_S** versuchen (siehe stdio). H) Aufrufe mit **tmpfile_s**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**tmpfile_s**|\<stdio.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

> [!NOTE]
> Dieses Beispiel erfordert möglicherweise Administratorrechte, um unter Windows ausgeführt werden zu können.

```C
// crt_tmpfile_s.c
// This program uses tmpfile_s to create a
// temporary file, then deletes this file with _rmtmp.
//

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char tempstring[] = "String to be written";
   int  i;
   errno_t err;

   // Create temporary files.
   for( i = 1; i <= 3; i++ )
   {
      err = tmpfile_s(&stream);
      if( err )
         perror( "Could not open new temporary file\n" );
      else
         printf( "Temporary file %d was created\n", i );
   }

   // Remove temporary files.
   printf( "%d temporary files deleted\n", _rmtmp() );
}
```

```Output
Temporary file 1 was created
Temporary file 2 was created
Temporary file 3 was created
3 temporary files deleted
```

## <a name="see-also"></a>Weitere Informationen

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
