---
title: tmpnam_s, _wtmpnam_s
ms.date: 4/2/2020
api_name:
- tmpnam_s
- _wtmpnam_s
- _o__wtmpnam_s
- _o_tmpnam_s
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
- tmpnam_s
- _wtmpnam_s
- L_tmpnam_s
helpviewer_keywords:
- tmpnam_s function
- file names [C++], creating temporary
- _wtmpnam_s function
- L_tmpnam_s constant
- temporary files, creating
- file names [C++], temporary
- wtmpnam_s function
ms.assetid: e70d76dc-49f5-4aee-bfa2-f1baa2bcd29f
ms.openlocfilehash: e34fbe64d342205659a4b0bdaf703248e62ed733
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362418"
---
# <a name="tmpnam_s-_wtmpnam_s"></a>tmpnam_s, _wtmpnam_s

Generiert Namen, die Sie verwenden können, um temporäre Dateien zu erstellen. Dabei handelt es sich um Versionen von [tmpnam und _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md) mit den unter [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschriebenen Erweiterungen.

## <a name="syntax"></a>Syntax

```C
errno_t tmpnam_s(
   char * str,
   size_t sizeInChars
);
errno_t _wtmpnam_s(
   wchar_t *str,
   size_t sizeInChars
);
template <size_t size>
errno_t tmpnam_s(
   char (&str)[size]
); // C++ only
template <size_t size>
errno_t _wtmpnam_s(
   wchar_t (&str)[size]
); // C++ only
```

### <a name="parameters"></a>Parameter

*Str*<br/>
Zeiger, der den generierten Namen enthalten wird.

*sizeInChars*<br/>
Größe des Puffers in Zeichen.

## <a name="return-value"></a>Rückgabewert

Beide Funktionen geben bei Erfolg 0 zurück und bei einem Fehler eine Fehlernummer zurück.

### <a name="error-conditions"></a>Fehlerbedingungen

|||||
|-|-|-|-|
|*Str*|*sizeInChars*|**Rückgabewert**|**Inhalt der***str*  |
|**Null**|any|**Einval**|nicht geändert|
|nicht **NULL** (zeigt auf gültigen Speicher)|zu kurz|**ERANGE**|nicht geändert|

Wenn *str* **NULL**ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, setzen diese Funktionen **errno** auf **EINVAL** und geben **EINVAL**zurück.

## <a name="remarks"></a>Bemerkungen

Jede dieser Funktionen gibt den Namen einer Datei zurück, die derzeit nicht vorhanden ist. **tmpnam_s** gibt einen eindeutigen Namen im angegebenen temporären Windows-Verzeichnis zurück, das von [GetTempPathW](/windows/win32/api/fileapi/nf-fileapi-gettemppathw)zurückgegeben wird. Wenn einem Dateinamen ohne Pfadinformationen ein umgekehrter Schrägstrich vorangestellt ist, wie z.B. \fname21, weist dies darauf hin, dass der Name für das aktuelle Arbeitsverzeichnis gültig ist.

Für **tmpnam_s**können Sie diesen generierten Dateinamen in *str*speichern. Die maximale Länge einer Zeichenfolge, die von **tmpnam_s** zurückgegeben wird, ist **L_tmpnam_s**, definiert in STDIO. H. Wenn *str* **NULL**ist, lässt **tmpnam_s** das Ergebnis in einem internen statischen Puffer. Alle nachfolgenden Aufrufe zerstören deshalb diesen Wert. Der von **tmpnam_s** generierte Name besteht aus einem programmgenerierten Dateinamen und nach dem ersten Aufruf **von tmpnam_s**aus einer Dateierweiterung mit fortlaufenden Nummern in Basis 32 (.1-.1vvvvvu, wenn **TMP_MAX_S** in STDIO. H ist **INT_MAX**).

**tmpnam_s** verarbeitet automatisch Zeichenfolgenargumente mit mehreren Byte-Zeichen, wobei Multibyte-Zeichensequenzen entsprechend der VOM Betriebssystem abgerufenen OEM-Codepage erkannt werden. **_wtmpnam_s** ist eine breit gefächerte Version von **tmpnam_s**; Das Argument und der Rückgabewert von **_wtmpnam_s** sind Zeichenfolgen mit großen Zeichen. **_wtmpnam_s** und **tmpnam_s** verhalten sich identisch, außer dass **_wtmpnam_s** keine Zeichenfolgen mit mehreren Byte-Zeichen verarbeitet.

Die Verwendung dieser Funktionen in C++ wird durch Überladungen (als Vorlagen vorhanden) vereinfacht. Überladungen können automatisch die Pufferlänge ableiten, sodass kein Größenargument angegeben werden muss. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam_s**|**tmpnam_s**|**tmpnam_s**|**_wtmpnam_s**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**tmpnam_s**|\<stdio.h>|
|**_wtmpnam_s**|\<stdio.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_tmpnam_s.c
// This program uses tmpnam_s to create a unique filename in the
// current working directory.
//

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char name1[L_tmpnam_s];
   errno_t err;
   int i;

   for (i = 0; i < 15; i++)
   {
      err = tmpnam_s( name1, L_tmpnam_s );
      if (err)
      {
         printf("Error occurred creating unique filename.\n");
         exit(1);
      }
      else
      {
         printf( "%s is safe to use as a temporary file.\n", name1 );
      }
   }
}
```

```Output
C:\Users\LocalUser\AppData\Local\Temp\u19q8.0 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.1 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.2 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.3 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.4 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.5 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.6 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.7 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.8 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.9 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.a is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.b is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.c is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.d is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.e is safe to use as a temporary file.
```

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
