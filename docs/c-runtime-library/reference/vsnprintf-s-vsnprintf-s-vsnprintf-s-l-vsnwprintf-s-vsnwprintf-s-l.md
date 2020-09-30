---
title: vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l
ms.date: 11/04/2016
api_name:
- _vsnwprintf_s
- _vsnwprintf_s_l
- _vsnprintf_s
- vsnprintf_s
- _vsnprintf_s_l
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _vsnprintf_s
- _vsntprintf_s
- _vsnwprintf_s
helpviewer_keywords:
- vsnwprintf_s function
- _vsntprintf_s function
- _vsntprintf_s_l function
- vsntprintf_s function
- vsnwprintf_s_l function
- vsnprintf_s_l function
- vsntprintf_s_l function
- _vsnwprintf_s_l function
- _vsnprintf_s function
- vsnprintf_s function
- _vsnprintf_s_l function
- _vsnwprintf_s function
- formatted text [C++]
ms.assetid: 147ccfce-58c7-4681-a726-ef54ac1c604e
ms.openlocfilehash: edb534eb533d63c9298b7b7e9aced1be3e8652d9
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502793"
---
# <a name="vsnprintf_s-_vsnprintf_s-_vsnprintf_s_l-_vsnwprintf_s-_vsnwprintf_s_l"></a>vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l

Schreiben von formatierter Ausgabe mithilfe eines Zeigers, der auf eine Liste von Argumenten zeigt. Dies sind Versionen von [vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf, _vsnwprintf_l](vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) mit Sicherheitsverbesserungen, wie in [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
int vsnprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_s_l(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vsnwprintf_s(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const wchar_t *format,
   va_list argptr
);
int _vsnwprintf_s_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
template <size_t size>
int _vsnprintf_s(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf_s(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   va_list argptr
); // C++ only
```

### <a name="parameters"></a>Parameter

*ert*<br/>
Speicherort für die Ausgabe.

*sizeOfBuffer*<br/>
Die Größe des *Puffers* für die Ausgabe als Zeichen Anzahl.

*count*<br/>
Die maximale Anzahl von zu schreibenden Zeichen (ohne das abschließende Zeichen NULL) oder [_TRUNCATE](../../c-runtime-library/truncate.md).

*format*<br/>
Formatangabe.

*argptr*<br/>
Zeiger zur Liste der Argumente.

*locale*<br/>
Das zu verwendende Gebietsschema.

Weitere Informationen finden Sie unter [Formatangaben](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Rückgabewert

**vsnprintf_s**, **_vsnprintf_s** und **_vsnwprintf_s** die Anzahl der geschriebenen Zeichen ohne das abschließende Null-Zeichen oder einen negativen Wert zurückgeben, wenn entweder das Abschneiden der Daten oder ein Ausgabefehler auftritt.

* Wenn *count* kleiner als *sizeOfBuffer* und die Anzahl der Daten Zeichen kleiner als oder gleich *count*ist, oder *count* [_TRUNCATE](../../c-runtime-library/truncate.md) und die Anzahl der Daten Zeichen kleiner als *sizeOfBuffer*ist, werden alle Daten geschrieben und die Anzahl der Zeichen zurückgegeben.

* Wenn *count* kleiner als *sizeOfBuffer* ist, aber die Daten die *Anzahl* der Zeichen überschreiten, werden die ersten *Anzahl* Zeichen geschrieben. Die verbleibenden Daten werden abgeschnitten, und-1 wird zurückgegeben, ohne dass der Handler für ungültige Parameter aufgerufen wird.

* Wenn *count* [_TRUNCATE](../../c-runtime-library/truncate.md) und die Anzahl der Zeichen von Daten dem *sizeOfBuffer*entspricht oder überschreitet, wird der Großteil der Zeichenfolge, die in den *Puffer* passt (mit abschließendem NULL-Wert), geschrieben. Die verbleibenden Daten werden abgeschnitten, und-1 wird zurückgegeben, ohne dass der Handler für ungültige Parameter aufgerufen wird.

* Wenn *count* gleich oder größer als *sizeOfBuffer* ist, aber die Anzahl der Zeichen der Daten kleiner als *sizeOfBuffer*ist, werden alle Daten geschrieben (mit abschließendem NULL-Wert), und die Anzahl der Zeichen wird zurückgegeben.

* Wenn *count* und die Anzahl der Daten Zeichen gleich dem Wert *sizeOfBuffer*sind, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die Ausführung nach dem Handler für ungültige Parameter fortgesetzt wird, legen diese Funktionen den *Puffer* auf eine leere Zeichenfolge fest, legen **errno** auf **ERANGE**fest und geben-1 zurück.

* Wenn der *Puffer* oder das *Format* ein **null** -Zeiger ist oder die *Anzahl* kleiner oder gleich 0 (null) ist, wird der Handler für ungültige Parameter aufgerufen. Wenn die weitere Ausführung zugelassen wird, legen diese Funktionen **errno** auf **EINVAL** fest und geben-1 zurück.

### <a name="error-conditions"></a>Fehlerbedingungen

|**Condition**|Rückgabewert|**errno**|
|-----------------|------------|-------------|
|der *Puffer* ist **null** .|-1|**Eingabe**|
|*Format* ist **null**|-1|**Eingabe**|
|*Anzahl* <= 0|-1|**Eingabe**|
|*sizeOfBuffer* zu klein (und *count* ! = **_TRUNCATE**)|-1 (und der *Puffer* auf eine leere Zeichenfolge festgelegt)|**ERANGE**|

## <a name="remarks"></a>Bemerkungen

**vsnprintf_s** ist mit **_vsnprintf_s**identisch. **vsnprintf_s** ist für die Kompatibilität mit dem ANSI-Standard enthalten. **_vnsprintf** wird aus Gründen der Abwärtskompatibilität beibehalten.

Jede dieser Funktionen nimmt einen Zeiger auf eine Argumentliste und formatiert und schreibt dann bis zu *Zähl* Zeichen der angegebenen Daten in den Speicher, auf den der *Puffer* zeigt, und fügt einen abschließenden NULL-Wert an.

Wenn *count* [_TRUNCATE](../../c-runtime-library/truncate.md)ist, schreiben diese Funktionen den Großteil der Zeichenfolge so, dass Sie in den *Puffer* passt, wobei Platz für das abschließende Null-Zeichen bleibt. Wenn die gesamte Zeichenfolge (mit abschließendem NULL-Wert) in den *Puffer*passt, geben diese Funktionen die Anzahl der geschriebenen Zeichen zurück (ohne das abschließende Null-Zeichen). Andernfalls geben diese Funktionen "-1" zurück, um anzugeben, dass ein Abschneiden aufgetreten ist.

Die Versionen dieser Funktionen mit dem **_l** -Suffix sind beinahe identisch, verwenden jedoch den Gebiets Schema Parameter, der anstelle des aktuellen Thread Gebiets Schemas übergeben wurde.

> [!IMPORTANT]
> Stellen Sie sicher, dass *format* keine benutzerdefinierte Zeichenfolge ist. Weitere Informationen finden Sie unter [Vermeiden von Pufferüberläufen](/windows/win32/SecBP/avoiding-buffer-overruns).

> [!NOTE]
> Um sicherzustellen, dass genügend Platz für das abschließende Null-Zeichen vorhanden ist, stellen Sie sicher, dass die *Anzahl* streng kleiner als die Pufferlänge ist, oder verwenden Sie **_TRUNCATE**.

In C++ wird die Verwendung dieser Funktionen durch Vorlagenüberladungen vereinfacht; die Überladungen können automatisch Rückschlüsse auf die Pufferlänge ziehen (wodurch kein Größenargument mehr angegeben werden muss), und sie können automatisch die älteren, nicht sicheren Funktionen durch ihre neueren, sicheren Entsprechungen ersetzen. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsntprintf_s**|**_vsnprintf_s**|**_vsnprintf_s**|**_vsnwprintf_s**|
|**_vsntprintf_s_l**|**_vsnprintf_s_l**|**_vsnprintf_s_l**|**_vsnwprintf_s_l**|

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|Optionale Header|
|-------------|---------------------|----------------------|
|**vsnprintf_s**|\<stdio.h> und \<stdarg.h>|\<varargs.h>*|
|**_vsnprintf_s** **_vsnprintf_s_l**|\<stdio.h> und \<stdarg.h>|\<varargs.h>*|
|**_vsnwprintf_s** **_vsnwprintf_s_l**|\<stdio.h> oder \<wchar.h> , und \<stdarg.h>|\<varargs.h>*|

\* Benötigt für die Kompatibilität mit UNIX V.

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```cpp
// crt_vsnprintf_s.cpp
#include <stdio.h>
#include <wtypes.h>

void FormatOutput(LPCSTR formatstring, ...)
{
   int nSize = 0;
   char buff[10];
   memset(buff, 0, sizeof(buff));
   va_list args;
   va_start(args, formatstring);
   nSize = vsnprintf_s( buff, _countof(buff), _TRUNCATE, formatstring, args);
   printf("nSize: %d, buff: %s\n", nSize, buff);
   va_end(args);
}

int main() {
   FormatOutput("%s %s", "Hi", "there");
   FormatOutput("%s %s", "Hi", "there!");
   FormatOutput("%s %s", "Hi", "there!!");
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: -1, buff: Hi there!
```

## <a name="see-also"></a>Weitere Informationen

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf-Funktionen](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, Austausch printf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
