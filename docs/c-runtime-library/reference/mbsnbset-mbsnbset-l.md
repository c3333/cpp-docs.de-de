---
title: _mbsnbset, _mbsnbset_l
ms.date: 4/2/2020
api_name:
- _mbsnbset
- _mbsnbset_l
- _o__mbsnbset
- _o__mbsnbset_l
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsnbset
- mbsnbset_l
- _mbsnbset
- _mbsnbset_l
helpviewer_keywords:
- tcsnset function
- _tcsnset_l function
- _mbsnbset function
- _tcsnset function
- _mbsnbset_l function
- mbsnbset_l function
- tcsnset_l function
- mbsnbset function
ms.assetid: 8e46ef75-9a56-42d2-a522-a08450c67c19
ms.openlocfilehash: 6af5dd101de74c9f25451c7b72ee561db35505d4
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915554"
---
# <a name="_mbsnbset-_mbsnbset_l"></a>_mbsnbset, _mbsnbset_l

Legt die ersten **n** Bytes einer Multibytezeichenfolge auf ein angegebenes Zeichen fest. Sicherere Versionen dieser Funktionen sind verfügbar. Informationen dazu finden Sie unter [_mbsnbcpy_s, _mbsnbcpy_s_l](mbsnbset-s-mbsnbset-s-l.md).

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
unsigned char *_mbsnbset(
   unsigned char *str,
   unsigned int c,
   size_t count
);
unsigned char *_mbsnbset_l(
   unsigned char *str,
   unsigned int c,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*SRT*<br/>
Zu ändernde Zeichenfolge.

*scher*<br/>
Einzelbyte- oder Multibytezeicheneinstellung.

*count*<br/>
Zahl der festzulegenden Bytes.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

**_mbsnbset** gibt einen Zeiger auf die geänderte Zeichenfolge zurück.

## <a name="remarks"></a>Hinweise

Die **_mbsnbset** -und **_mbsnbset_l** Funktionen legen höchstens die ersten Byte *Anzahl* von *Str* bis *c*fest. Wenn *count* größer als die Länge von *Str*ist, wird die Länge von *Str* anstelle von *count*verwendet. Wenn *c* ein Multibytezeichen ist und nicht vollständig auf das von *count*angegebene letzte Byte festgelegt werden kann, wird das letzte Byte mit einem Leerzeichen aufgefüllt. **_mbsnbset** und **_mbsnbset_l** platzieren keinen abschließenden NULL-Wert am Ende von *Str*.

**_mbsnbset** und **_mbsnbset_l** ähnelt **_mbsnset**, mit dem Unterschied, dass die *Anzahl* der Bytes und nicht die *Anzahl* von Zeichen *c*festgelegt wird.

Wenn *Str* **null** oder *count* 0 ist, generiert diese Funktion eine Ausnahme wegen eines ungültigen Parameters, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, wird **errno** auf **EINVAL** festgelegt, und die Funktion gibt **null**zurück. Auch wenn *c* kein gültiges Multibytezeichen ist, wird **errno** auf **EINVAL** festgelegt, und stattdessen wird ein Leerzeichen verwendet.

Der Ausgabewert ist von der Kategorieeinstellung **LC_CTYPE** des Gebietsschemas betroffen. Weitere Informationen finden Sie unter [setlocale](setlocale-wsetlocale.md). Die **_mbsnbset** Version dieser Funktion verwendet das aktuelle Gebiets Schema für dieses vom Gebiets Schema abhängige Verhalten. die **_mbsnbset_l** -Version ist beinahe identisch, verwendet jedoch stattdessen den übergebenen Gebiets Schema Parameter. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

**Sicherheitshinweis** Diese API stellt eine mögliche Bedrohung aufgrund eines Pufferüberlaufproblems dar. Pufferüberlaufprobleme werden häufig bei Systemangriffen eingesetzt, da sie zu einer unbefugten Ausweitung der Berechtigungen führen. Weitere Informationen finden Sie unter [Vermeiden von Pufferüberläufen](/windows/win32/SecBP/avoiding-buffer-overruns).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnset**|**_strnset**|**_mbsnbset**|**_wcsnset**|
|**_tcsnset_l**|**_strnset_l**|**_mbsnbset_l**|**_wcsnset_l**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_mbsnbset**|\<mbstring.h>|
|**_mbsnbset_l**|\<mbstring.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_mbsnbset.c
// compile with: /W3
#include <mbstring.h>
#include <stdio.h>

int main( void )
{
   char string[15] = "This is a test";
   /* Set not more than 4 bytes of string to be *'s */
   printf( "Before: %s\n", string );
   _mbsnbset( string, '*', 4 ); // C4996
   // Note; _mbsnbset is deprecated; consider _mbsnbset_s
   printf( "After:  %s\n", string );
}
```

### <a name="output"></a>Output

```Output
Before: This is a test
After:  **** is a test
```

## <a name="see-also"></a>Siehe auch

[Zeichen folgen Bearbeitung](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
