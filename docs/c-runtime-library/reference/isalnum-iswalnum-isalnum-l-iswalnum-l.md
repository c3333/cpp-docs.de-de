---
title: isalnum, iswalnum, _isalnum_l, _iswalnum_l
ms.date: 4/2/2020
api_name:
- _iswalnum_l
- _isalnum_l
- iswalnum
- isalnum
- _o_isalnum
- _o_iswalnum
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
- _istalnum_l
- _iswalnum_l
- iswalnum
- _isalnum_l
- isalnum
- _istalnum
helpviewer_keywords:
- _istalnum function
- _ismbcalnum_l function
- iswalnum function
- isalnum function
- istalnum function
- _isalnum_l function
- _istalnum_l function
- _iswalnum_l function
ms.assetid: 0dc51306-ade8-4944-af27-e4176fc89093
ms.openlocfilehash: e32cdd2ad13ead282840e192e572757d759110f7
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919813"
---
# <a name="isalnum-iswalnum-_isalnum_l-_iswalnum_l"></a>isalnum, iswalnum, _isalnum_l, _iswalnum_l

Bestimmt, ob eine ganze Zahl ein alphanumerisches Zeichen darstellt.

## <a name="syntax"></a>Syntax

```C
int isalnum( int c );
int iswalnum( wint_t c );
int _isalnum_l( int c,  _locale_t locale );
int _iswalnum_l( wint_t c, _locale_t locale );
```

### <a name="parameters"></a>Parameter

*scher*<br/>
Zu testende ganze Zahl.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Jede dieser Routinen gibt einen Wert ungleich 0 (null) zurück, wenn *c* eine bestimmte Darstellung eines alphanumerischen Zeichens ist. **isalnum** gibt einen Wert ungleich 0 (null) zurück, wenn für *c*entweder **isalpha** oder **IsDigit** ungleich 0 (null) ist, d. h., wenn *c* innerhalb der Bereiche a-z, a-z oder 0-9 liegt. **iswalnum** gibt einen Wert ungleich 0 (null) zurück, wenn **iswalpha** oder **iswdigit** für *c*ungleich 0 (null) ist. Jede dieser Routinen gibt 0 zurück, wenn *c* die Test Bedingung nicht erfüllt.

Die Versionen dieser Funktionen mit dem **_l** -Suffix verwenden den Gebiets Schema Parameter, der anstelle des aktuellen Gebiets Schemas übergeben wurde. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Das Verhalten von **isalnum** und **_isalnum_l** ist nicht definiert, wenn *c* nicht EOF ist oder im Bereich von 0 bis 0xFF (einschließlich) liegt. Wenn eine Debug-CRT-Bibliothek verwendet wird und *c* keiner dieser Werte ist, wird von den Funktionen eine-Assertion erhoben.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istalnum**|**isalnum**|[_ismbcalnum](ismbcalnum-functions.md)|**iswalnum**|
|**_istalnum_l**|**_isalnum_l**|**_ismbcalnum_l**|**_iswalnum_l**|

## <a name="remarks"></a>Hinweise

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**isalnum**|\<ctype.h>|
|**iswalnum**|\<ctype.h> oder \<wchar.h>|
|**_isalnum_l**|\<ctype.h>|
|**_iswalnum_l**|\<ctype.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Zeichen Klassifizierung](../../c-runtime-library/character-classification.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[is-, ISW-Routinen](../../c-runtime-library/is-isw-routines.md)<br/>
