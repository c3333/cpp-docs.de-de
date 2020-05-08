---
title: memmove_s, wmemmove_s
ms.date: 4/2/2020
api_name:
- wmemmove_s
- memmove_s
- _o_wmemmove_s
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wmemmove_s
- memmove_s
helpviewer_keywords:
- wmemmove_s function
- memmove_s function
ms.assetid: a17619e4-1307-4bb0-98c6-77f8c68dab2d
ms.openlocfilehash: 04f920543c4f6a3d433e6426a96d617a3608a270
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914094"
---
# <a name="memmove_s-wmemmove_s"></a>memmove_s, wmemmove_s

Verschiebt einen Puffer in einen anderen. Dabei handelt es sich um Versionen von [memmove, wmemmove](memmove-wmemmove.md) mit den unter [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschriebenen Erweiterungen.

## <a name="syntax"></a>Syntax

```C
errno_t memmove_s(
   void *dest,
   size_t numberOfElements,
   const void *src,
   size_t count
);
errno_t wmemmove_s(
   wchar_t *dest,
   size_t numberOfElements,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>Parameter

*dest*<br/>
Zielobjekt.

*numberOfElements*<br/>
Größe des Zielpuffers.

*src*<br/>
Quellobjekt.

*count*<br/>
Anzahl der zu kopierenden Bytes (**memmove_s**) oder Zeichen (**wmemmove_s**).

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich; ein Fehlercode, wenn ein Fehler auftritt

### <a name="error-conditions"></a>Fehlerbedingungen

|*dest*|*numberOfElements*|*src*|Rückgabewert|Inhalt von *dest*|
|------------|------------------------|-----------|------------------|------------------------|
|**Normal**|any|any|**Eingabe**|nicht geändert|
|any|any|**Normal**|**Eingabe**|nicht geändert|
|any|< *count*|any|**ERANGE**|nicht geändert|

## <a name="remarks"></a>Hinweise

Kopiert die *Anzahl* von Bytes von Zeichen von *src* in *dest*. Wenn sich einige Bereiche des Quell-und des Zielbereichs überlappen, stellt **memmove_s** sicher, dass die ursprünglichen Quell Bytes im überlappenden Bereich kopiert werden, bevor Sie überschrieben werden.

Wenn der Wert *dest* oder wenn *src* ein NULL-Zeiger ist oder wenn die Ziel Zeichenfolge zu klein ist, rufen diese Funktionen einen Handler für ungültige Parameter auf, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md) Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, geben diese Funktionen " **EINVAL** " zurück und legen " **errno** " auf " **EINVAL**" fest.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**memmove_s**|\<string.h>|
|**wmemmove_s**|\<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_memmove_s.c
//
// The program demonstrates the
// memmove_s function which works as expected
// for moving overlapping regions.

#include <stdio.h>
#include <string.h>

int main()
{
   char str[] = "0123456789";

   printf("Before: %s\n", str);

   // Move six bytes from the start of the string
   // to a new position shifted by one byte. To protect against
   // buffer overrun, the secure version of memmove requires the
   // the length of the destination string to be specified.

   memmove_s((str + 1), strnlen(str + 1, 10), str, 6);

   printf_s(" After: %s\n", str);
}
```

### <a name="output"></a>Output

```Output
Before: 0123456789
After: 0012345789
```

## <a name="see-also"></a>Siehe auch

[Pufferbearbeitung](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[strcpy_s, wcscpy_s, _mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
