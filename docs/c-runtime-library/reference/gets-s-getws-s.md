---
title: gets_s, _getws_s
ms.date: 4/2/2020
api_name:
- _getws_s
- gets_s
- _o__getws_s
- _o_gets_s
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
- _getws_s
- gets_s
helpviewer_keywords:
- getws_s function
- _getws_s function
- lines, getting
- streams, getting lines
- buffers, avoiding overruns
- buffer overruns
- buffers, buffer overruns
- gets_s function
- standard input, reading from
ms.assetid: 5880c36f-122c-4061-a1a5-aeeced6fe58c
ms.openlocfilehash: b01456d3ed37c34dbc10980ebdfbe008e27f624a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913608"
---
# <a name="gets_s-_getws_s"></a>gets_s, _getws_s

Ruft eine Zeile aus dem **stdin** -Datenstrom ab. Diese Versionen von [gets, _getws](../../c-runtime-library/gets-getws.md) enthalten Sicherheitserweiterungen, wie unter [Sicherheitserweiterungen im CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben wird.

## <a name="syntax"></a>Syntax

```C
char *gets_s(
   char *buffer,
   size_t sizeInCharacters
);
wchar_t *_getws_s(
   wchar_t *buffer,
   size_t sizeInCharacters
);
```

```cpp
template <size_t size>
char *gets_s( char (&buffer)[size] ); // C++ only

template <size_t size>
wchar_t *_getws_s( wchar_t (&buffer)[size] ); // C++ only
```

### <a name="parameters"></a>Parameter

*ert*<br/>
Speicherort für die Eingabezeichenfolge.

*sizeInCharacters*<br/>
Die Größe des Puffers.

## <a name="return-value"></a>Rückgabewert

Gibt den *Puffer* zurück, wenn erfolgreich. Ein **NULL**-Zeiger weist auf einen Fehler oder eine Dateiendebedingung hin. Verwenden Sie [ferror](ferror.md) oder [feof](feof.md), um festzulegen, was aufgetreten ist.

## <a name="remarks"></a>Hinweise

Die **gets_s** -Funktion liest eine Zeile aus dem Standardeingabestream **stdin** und speichert Sie im *Puffer*. Die Zeile enthält alle Zeichen einschließlich des ersten Zeilenumbruchzeichens ('\n'). **gets_s** ersetzt dann das Zeilen vorzeilenzeichen durch ein NULL-Zeichen (' \ 0 '), bevor die Zeile zurückgegeben wird. Im Gegensatz dazu behält die **fgets_s** -Funktion das Zeilen einzeilenzeichen bei.

Wenn das erste gelesene Zeichen das Dateiendezeichen ist, wird ein NULL-Zeichen am Anfang des *Puffers* gespeichert, und es wird **null** zurückgegeben.

**_getws_s** ist eine breit Zeichen Version von **gets_s**. Das Argument und der Rückgabewert sind Zeichen folgen mit breit Zeichen.

Wenn *buffer* der Puffer **null** ist oder *sizeincharacter* kleiner oder gleich 0 (null) ist, oder wenn der Puffer zu klein ist, um die Eingabezeile und null-Terminator zu enthalten, rufen diese Funktionen einen Handler für ungültige Parameter auf, wie in [Parameter Validierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die weitere Ausführung zugelassen wird, geben diese Funktionen **null** zurück und legen errno auf **ERANGE**fest.

In C++ wird die Verwendung dieser Funktionen durch Vorlagenüberladungen vereinfacht; die Überladungen können automatisch Rückschlüsse auf die Pufferlänge ziehen (wodurch kein Größenargument mehr angegeben werden muss), und sie können automatisch die älteren, nicht sicheren Funktionen durch ihre neueren, sicheren Entsprechungen ersetzen. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_getts_s**|**gets_s**|**gets_s**|**_getws_s**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**gets_s**|\<stdio.h>|
|**_getws_s**|\<stdio.h> oder \<wchar.h>|

Die-Konsole wird in universelle Windows-Plattform-Apps (UWP) nicht unterstützt. Die Standarddaten Strom Handles, die der Konsole, **stdin**, **stdout**und **stderr**zugeordnet sind, müssen umgeleitet werden, bevor Sie von C-Lauf Zeitfunktionen in UWP-Apps verwendet werden können. Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_gets_s.c
// This program retrieves a string from the stdin and
// prints the same string to the console.

#include <stdio.h>

int main( void )
{
   char line[21]; // room for 20 chars + '\0'
   gets_s( line, 20 );
   printf( "The line entered was: %s\n", line );
}
```

```Input
Hello there!
```

```Output
The line entered was: Hello there!
```

## <a name="see-also"></a>Weitere Informationen

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[gets, _getws](../../c-runtime-library/gets-getws.md)<br/>
[fgets, fgetws](fgets-fgetws.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[puts, _putws](puts-putws.md)<br/>
