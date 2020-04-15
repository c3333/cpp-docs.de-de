---
title: isxdigit, iswxdigit, _isxdigit_l, _iswxdigit_l
ms.date: 4/2/2020
api_name:
- _iswxdigit_l
- iswxdigit
- isxdigit
- _isxdigit_l
- _o_iswxdigit
- _o_isxdigit
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- iswxdigit
- isxdigit
- _istxdigit
helpviewer_keywords:
- isxdigit function
- istxdigit function
- _iswxdigit_l function
- _istxdigit function
- _isxdigit_l function
- iswxdigit_l function
- isxdigit_l function
- hexadecimal characters
- iswxdigit function
ms.assetid: c8bc5146-0b58-4e3f-bee3-f2318dd0f829
ms.openlocfilehash: c2f6e7956048a30313ba8eb9a11a37fccdc49197
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342741"
---
# <a name="isxdigit-iswxdigit-_isxdigit_l-_iswxdigit_l"></a>isxdigit, iswxdigit, _isxdigit_l, _iswxdigit_l

Bestimmt, ob eine ganze Zahl ein Zeichen darstellt, das eine Hexadezimalziffer ist.

## <a name="syntax"></a>Syntax

```C
int isxdigit(
   int c
);
int iswxdigit(
   wint_t c
);
int _isxdigit_l(
   int c,
   _locale_t locale
);
int _iswxdigit_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*C*<br/>
Zu testende ganze Zahl.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Jede dieser Routinen gibt einen Wert ungleich Null zurück, wenn *c* eine bestimmte Darstellung einer hexadezimalen Ziffer ist. **isxdigit** gibt einen Wert ungleich Null zurück, wenn *c* eine hexadezimale Ziffer ist (A - F, a - f oder 0 - 9). **iswxdigit** gibt einen Wert ungleich Null zurück, wenn *c* ein breites Zeichen ist, das einem hexadezimalen Ziffernzeichen entspricht. Jede dieser Routinen gibt 0 zurück, wenn *c* die Testbedingung nicht erfüllt.

Für das Gebietsschema "C" unterstützt die **iswxdigit-Funktion** keine Unicode-Hexadezimalzeichen mit voller Breite.

Die Versionen dieser Funktionen mit dem **suffix _l** verwenden das Gebietsschema, das übergeben wird, anstelle des aktuellen Gebietsschemas für ihr gebietsschemaabhängiges Verhalten. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Das Verhalten von **isxdigit** und **_isxdigit_l** ist nicht definiert, wenn *c* nicht EOF ist oder im Bereich 0 bis 0xFF, einschließlich. Wenn eine Debug-CRT-Bibliothek verwendet wird und *c* nicht einer dieser Werte ist, werden die Funktionen eine Assertion aus.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istxdigit**|**isxdigit**|**isxdigit**|**iswxdigit**|

## <a name="remarks"></a>Bemerkungen

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**isxdigit**|\<ctype.h>|
|**iswxdigit**|\<ctype.h> oder \<wchar.h>|
|**_isxdigit_l**|\<ctype.h>|
|**_iswxdigit_l**|\<ctype.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Zeichenklassifizierung](../../c-runtime-library/character-classification.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[is, isw Routines](../../c-runtime-library/is-isw-routines.md)<br/>
