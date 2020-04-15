---
title: strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l
ms.date: 4/2/2020
api_name:
- _mbstok_l
- _mbstok
- wcstok
- _mbstok
- strtok
- _wcstok_l
- _o__mbstok
- _o__mbstok_l
- _o_strtok
- _o_wcstok
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbstok
- strtok
- _tcstok
- wcstok
helpviewer_keywords:
- mbstok_l function
- strings [C++], searching
- tcstok function
- _tcstok function
- _strtok_l function
- strtok function
- mbstok function
- wcstok_l function
- _mbstok function
- tcstok_l function
- tokens, finding in strings
- _mbstok_l function
- wcstok function
- _wcstok_l function
- _tcstok_l function
- strtok_l function
ms.assetid: 904cb734-f0d7-4d77-ba81-4791ddf461ae
ms.openlocfilehash: d228d9824c534a21e4a22797e4b070e6d8d0b179
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365195"
---
# <a name="strtok-_strtok_l-wcstok-_wcstok_l-_mbstok-_mbstok_l"></a>strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l

Sucht das nächste Token in einer Zeichenfolge unter Verwendung des angegebenen Gebietsschemas oder eines Gebietsschemas, das übergeben wird. Sicherere Versionen dieser Funktionen sind verfügbar. Informationen dazu finden Sie unter [strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l](strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md).

> [!IMPORTANT]
> **_mbstok** und **_mbstok_l** können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
char *strtok(
   char *strToken,
   const char *strDelimit
);
char *strtok_l(
   char *strToken,
   const char *strDelimit,
   _locale_t locale
);
wchar_t *wcstok(
   wchar_t *strToken,
   const wchar_t *strDelimit
);
wchar_t *wcstok_l(
   wchar_t *strToken,
   const wchar_t *strDelimit,
   _locale_t locale
);
unsigned char *_mbstok(
   unsigned char *strToken,
   const unsigned char *strDelimit
);
unsigned char *_mbstok_l(
   unsigned char *strToken,
   const unsigned char *strDelimit,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*Strtoken*<br/>
Zeichenfolge, die mindestens ein Token enthält.

*strDelimit*<br/>
Gruppe von Trennzeichen.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf das nächste Token zurück, das in *strToken*gefunden wurde. Die Funktionen geben **NULL** zurück, wenn keine weiteren Token gefunden werden. Jeder Aufruf ändert *strToken,* indem ein Nullzeichen durch das erste Trennzeichen ersetzt wird, das nach dem zurückgegebenen Token auftritt.

## <a name="remarks"></a>Bemerkungen

Die **strtok-Funktion** findet das nächste Token in *strToken*. Der Satz von Zeichen in *strDelimit* gibt mögliche Trennzeichen des Tokens an, die beim aktuellen Aufruf in *strToken* zu finden sind. **wcstok** und **_mbstok** sind breit-zeichen- und multibyte-Zeichen-Versionen von **strtok**. Die Argumente und der Rückgabewert von **wcstok** sind Zeichenfolgen mit großen Zeichen. bei **_mbstok** sind Zeichenfolgen mit mehreren Bytezeichen. Diese drei Funktionen verhalten sich andernfalls identisch.

> [!IMPORTANT]
> Diese Funktionen stellen eine mögliche Bedrohung aufgrund eines Pufferüberlaufproblems dar. Pufferüberlaufprobleme werden häufig bei Systemangriffen eingesetzt, da sie zu einer unbefugten Ausweitung der Berechtigungen führen. Weitere Informationen finden Sie unter [Vermeiden von Pufferüberläufen](/windows/win32/SecBP/avoiding-buffer-overruns).

Beim ersten Aufruf von **strtok**überspringt die Funktion führende Trennzeichen und gibt einen Zeiger auf das erste Token in *strToken*zurück, wodurch das Token mit einem Nullzeichen beendet wird. Weitere Token können aus dem Rest von *strToken* durch eine Reihe von Aufrufen von **strtok**ausbrochen werden. Jeder Aufruf von **strtok** ändert *strToken,* indem ein Nullzeichen nach dem von diesem Aufruf zurückgegebenen **Token** eingefügt wird. Um das nächste Token aus *strToken*zu lesen, rufen Sie **strtok** mit einem **NULL-Wert** für das *argument strToken* auf. Das Argument **NULL** *strToken* bewirkt, dass **strtok** nach dem nächsten Token im geänderten *strToken*sucht. Das *argument strDelimit* kann einen beliebigen Wert von einem Aufruf zum nächsten annehmen, sodass der Satz von Trennzeichen variieren kann.

Der Ausgabewert wird durch die Einstellung der **LC_CTYPE** Kategorieeinstellung des Gebietsschemas beeinflusst. Weitere Informationen finden Sie unter [setlocale](setlocale-wsetlocale.md).

Die Versionen dieser Funktionen ohne das **_l** Suffix verwenden das aktuelle Gebietsschema für dieses gebietsschemaabhängige Verhalten. Die Versionen mit dem **Suffix _l** sind identisch, außer dass sie stattdessen den übergebenen Gebietsschemaparameter verwenden. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

> [!NOTE]
> Jede Funktion verwendet eine statische Variable eines lokalen Threads, um die Zeichenfolge in Token zu analysieren. Daher können mehrere Threads diese Funktionen gleichzeitig aufrufen, ohne dass unerwünschte Auswirkungen auftreten. Innerhalb eines einzelnen Threads ist es jedoch wahrscheinlich, dass ein überlappendes Aufrufen von einer dieser Funktionen zu Datenbeschädigung und ungenauen Ergebnissen führt. Beim Analysieren verschiedener Zeichenfolgen sollte zuerst eine Zeichenfolge zu Ende analysiert werden, bevor mit dem Analysieren der nächsten Zeichenfolge begonnen wird. Berücksichtigen Sie auch das mögliche Risiko, wenn Sie eine dieser Funktionen aus einer Schleife heraus aufrufen, in der eine andere Funktion aufgerufen wird. Wenn die andere Funktion eine dieser Funktionen verwendet, kommt es zu einer überlappenden Sequenz von Aufrufen und Datenbeschädigung ist die Folge.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstok**|**strtok**|**_mbstok**|**wcstok**|
|**_tcstok**|**_strtok_l**|**_mbstok_l**|**_wcstok_l**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**strtok**|\<string.h>|
|**wcstok**|\<string.h> oder \<wchar.h>|
|**_mbstok**, **_mbstok_l**|\<mbstring.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_strtok.c
// compile with: /W3
// In this program, a loop uses strtok
// to print all the tokens (separated by commas
// or blanks) in the string named "string".
//
#include <string.h>
#include <stdio.h>

char string[] = "A string\tof ,,tokens\nand some  more tokens";
char seps[]   = " ,\t\n";
char *token;

int main( void )
{
   printf( "Tokens:\n" );

   // Establish string and get the first token:
   token = strtok( string, seps ); // C4996
   // Note: strtok is deprecated; consider using strtok_s instead
   while( token != NULL )
   {
      // While there are tokens in "string"
      printf( " %s\n", token );

      // Get next token:
      token = strtok( NULL, seps ); // C4996
   }
}
```

```Output
Tokens:
A
string
of
tokens
and
some
more
tokens
```

## <a name="see-also"></a>Siehe auch

[String-Manipulation](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
