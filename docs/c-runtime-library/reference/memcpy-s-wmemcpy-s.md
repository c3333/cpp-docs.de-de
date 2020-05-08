---
title: memcpy_s, wmemcpy_s
ms.date: 4/2/2020
api_name:
- memcpy_s
- wmemcpy_s
- _o_memcpy_s
- _o_wmemcpy_s
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
- wmemcpy_s
- memcpy_s
helpviewer_keywords:
- memcpy_s function
- wmemcpy_s function
ms.assetid: 5504e20a-83d9-4063-91fc-3f55f7dabe99
ms.openlocfilehash: 7b3df3542974f99009285c8df652cff1fd4fa173
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915406"
---
# <a name="memcpy_s-wmemcpy_s"></a>memcpy_s, wmemcpy_s

Kopiert Bytes zwischen Puffern. Dabei handelt es sich um Versionen von [memcpy, wmemcpy](memcpy-wmemcpy.md) mit den unter [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschriebenen Erweiterungen.

## <a name="syntax"></a>Syntax

```C
errno_t memcpy_s(
   void *dest,
   size_t destSize,
   const void *src,
   size_t count
);
errno_t wmemcpy_s(
   wchar_t *dest,
   size_t destSize,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>Parameter

*dest*<br/>
Neuer Puffer.

*destSize*<br/>
Größe des Zielpuffers, in Bytes für memcpy_s und in Breitzeichen (wchar_t) für wmemcpy_s.

*src*<br/>
Der Puffer, aus dem kopiert werden soll.

*count*<br/>
Anzahl der zu kopierenden Zeichen.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, ein Fehlercode, wenn ein Fehler auftritt.

### <a name="error-conditions"></a>Fehlerbedingungen

|*dest*|*destSize*|*src*|*count*|Rückgabewert|Inhalt von *dest*|
|------------|----------------|-----------|---|------------------|------------------------|
|any|any|any|0|0|Nicht geändert|
|**Normal**|any|any|ungleich null|**Eingabe**|Nicht geändert|
|any|any|**Normal**|ungleich null|**Eingabe**|*dest* ist nulgerout|
|any|< *count*|any|ungleich null|**ERANGE**|*dest* ist nulgerout|

## <a name="remarks"></a>Hinweise

**memcpy_s** kopiert *Bytes* von *src* in *dest*. **wmemcpy_s** Kopien *zählen* breit Zeichen (zwei Bytes). Wenn sich Quelle und Ziel überlappen, ist das Verhalten von **memcpy_s** nicht definiert. Verwenden Sie **memmove_s** , um überlappende Bereiche zu behandeln.

Diese Funktionen überprüfen ihre Parameter. Wenn *count* ungleich NULL und *dest* oder *src* ein NULL-Zeiger ist oder *destSize* kleiner als *count*ist, rufen diese Funktionen den Handler für ungültige Parameter auf, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, geben diese Funktionen " **EINVAL** " oder " **ERANGE** " zurück und legen " **errno** " auf den Rückgabewert fest.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**memcpy_s**|\<memory.h> oder \<string.h>|
|**wmemcpy_s**|\<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_memcpy_s.c
// Copy memory in a more secure way.

#include <memory.h>
#include <stdio.h>

int main()
{
   int a1[10], a2[100], i;
   errno_t err;

   // Populate a2 with squares of integers
   for (i = 0; i < 100; i++)
   {
      a2[i] = i*i;
   }

   // Tell memcpy_s to copy 10 ints (40 bytes), giving
   // the size of the a1 array (also 40 bytes).
   err = memcpy_s(a1, sizeof(a1), a2, 10 * sizeof (int) );
   if (err)
   {
      printf("Error executing memcpy_s.\n");
   }
   else
   {
     for (i = 0; i < 10; i++)
       printf("%d ", a1[i]);
   }
   printf("\n");
}
```

```Output
0 1 4 9 16 25 36 49 64 81
```

## <a name="see-also"></a>Weitere Informationen

[Pufferbearbeitung](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memmove, wmemmove](memmove-wmemmove.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
