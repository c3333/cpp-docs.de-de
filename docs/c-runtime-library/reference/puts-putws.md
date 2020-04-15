---
title: puts, _putws
ms.date: 4/2/2020
api_name:
- _putws
- puts
- _o__putws
- _o_puts
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
- _putts
- _putws
- puts
helpviewer_keywords:
- strings [C++], writing
- _putts function
- standard output, writing to
- putws function
- puts function
- putts function
- _putws function
ms.assetid: 32dada12-ed45-40ac-be06-3feeced9ecd6
ms.openlocfilehash: 9681373ccf338daf05be3120fbadd39ba471e86a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332961"
---
# <a name="puts-_putws"></a>puts, _putws

Schreibt eine Zeichenfolge in **stdout**.

## <a name="syntax"></a>Syntax

```C
int puts(
   const char *str
);
int _putws(
   const wchar_t *str
);
```

### <a name="parameters"></a>Parameter

*Str*<br/>
Ausgabezeichenfolge.

## <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg einen nicht negativen Wert zurück. Wenn **Puts** fehlschlägt, gibt er **EOF**zurück; Wenn **_putws** fehlschlägt, gibt er **WEOF**zurück. Wenn *str* ein Nullzeiger ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, setzen die Funktionen **errno** auf **EINVAL** und geben **EOF** oder **WEOF**zurück.

Weitere Informationen zu diesen und anderen Fehlercodes finden Sie unter [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **puts-Funktion** schreibt *str* in den Standardausgabestream **stdout**und ersetzt das beendende Nullzeichen der Zeichenfolge ('''') durch ein Zeilenumleinenzeichen ('''') im Ausgabestream.

**_putws** ist die breitstellige Version von **Puts**; Die beiden Funktionen verhalten sich identisch, wenn der Stream im ANSI-Modus geöffnet wird. **stellt** die Ausgabe in einem UNICODE-Stream derzeit nicht vor.

**_putwch** schreibt Unicode-Zeichen mit der aktuellen CONSOLE LOCALE-Einstellung.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_putts**|**puts**|**puts**|**_putws**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**puts**|\<stdio.h>|
|**_putws**|\<stdio.h>|

Die Konsole wird in UWP-Apps (Universelle Windows-Plattform) nicht unterstützt. Die Standard-Stream-Handles, die der Konsole, **stdin**, **stdout**und **stderr**zugeordnet sind, müssen umgeleitet werden, bevor C-Laufzeitfunktionen sie in UWP-Apps verwenden können. Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

```C
// crt_puts.c
// This program uses puts to write a string to stdout.

#include <stdio.h>

int main( void )
{
   puts( "Hello world from puts!" );
}
```

### <a name="output"></a>Output

```Output
Hello world from puts!
```

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[fgets, fgetws](fgets-fgetws.md)<br/>
