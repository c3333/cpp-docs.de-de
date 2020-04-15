---
title: isascii, __isascii, iswascii
ms.date: 4/2/2020
api_name:
- iswascii
- __isascii
- _o_iswascii
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- iswascii
- istascii
- __isascii
- _istascii
- isascii
- ctype/isascii
- ctype/__isascii
- corecrt_wctype/iswascii
helpviewer_keywords:
- __isascii function
- _isascii function
- isascii function
- _istascii function
- istascii function
- iswascii function
ms.assetid: ba4325ad-7cb3-4fb9-b096-58906d67971a
ms.openlocfilehash: aeb9c27fee4d179cc16caa50c6f0aae521402beb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343913"
---
# <a name="isascii-__isascii-iswascii"></a>isascii, __isascii, iswascii

Bestimmt, ob ein angegebenes Zeichen ein ASCII-Zeichen ist.

## <a name="syntax"></a>Syntax

```C
int __isascii(
   int c
);
int iswascii(
   wint_t c
);

#define isascii __isascii
```

### <a name="parameters"></a>Parameter

*C*<br/>
Zu testende ganze Zahl.

## <a name="return-value"></a>Rückgabewert

Jede dieser Routinen gibt einen Wert ungleich Null zurück, wenn **c** eine bestimmte Darstellung eines ASCII-Zeichens ist. **__isascii** gibt einen Wert ungleich Null zurück, wenn **c** ein ASCII-Zeichen ist (im Bereich 0x00 - 0x7F). **iswascii** gibt einen Wert ungleich Null zurück, wenn **c** eine Breitzeichendarstellung eines ASCII-Zeichens ist. Jede dieser Routinen gibt 0 zurück, wenn **c** die Testbedingung nicht erfüllt.

## <a name="remarks"></a>Bemerkungen

Sowohl **__isascii als** auch **iswascii** werden als Makros implementiert, es sei denn, das Präprozessormakro _CTYPE_DISABLE_MACROS definiert ist.

Aus Gründen der Abwärtskompatibilität wird **isascii** nur dann als Makro implementiert, wenn [&#95;&#95;STDC-&#95;&#95;](../../preprocessor/predefined-macros.md) nicht oder als 0 definiert ist. andernfalls ist sie nicht definiert.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istascii**|**__isascii**|**__isascii**|**iswascii**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**isascii**, **__isascii**|C: \<ctype.h><br /><br /> C++: \<cctype> oder \<ctype.h>|
|**iswascii**|C: \<wctype.h>, \<ctype.h>, oder \<wchar.h><br /><br /> C++: \<cwctype>, \<cctype>, \<wctype.h>, \<ctype.h>, oder \<wchar.h>|

Die **Funktionen isascii**, **__isascii** und **iswascii** sind Microsoft-spezifisch. Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Zeichenklassifizierung](../../c-runtime-library/character-classification.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[is, isw Routines](../../c-runtime-library/is-isw-routines.md)<br/>
