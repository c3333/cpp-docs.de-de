---
title: tolower, _tolower, towlower, _tolower_l, _towlower_l
ms.date: 4/2/2020
api_name:
- _tolower_l
- towlower
- tolower
- _tolower
- _towlower_l
- _o__tolower
- _o__tolower_l
- _o__towlower_l
- _o_tolower
- _o_towlower
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _totlower
- tolower
- _tolower
- towlower
helpviewer_keywords:
- tolower_l function
- _tolower_l function
- totlower function
- string conversion, to different characters
- lowercase, converting to
- tolower function
- string conversion, case
- towlower function
- _tolower function
- _totlower function
- towlower_l function
- case, converting
- characters, converting
- _towlower_l function
ms.assetid: 86e0fc02-94ae-4472-9631-bf8e96f67b92
ms.openlocfilehash: 560fde4ae2167256acd54856fced15bc6ccecae6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362362"
---
# <a name="tolower-_tolower-towlower-_tolower_l-_towlower_l"></a>tolower, _tolower, towlower, _tolower_l, _towlower_l

Konvertiert ein Zeichen in Kleinbuchstaben.

## <a name="syntax"></a>Syntax

```C
int tolower(
   int c
);
int _tolower(
   int c
);
int towlower(
   wint_t c
);
int _tolower_l(
   int c,
   _locale_t locale
);
int _towlower_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*C*<br/>
Zu konvertierendes Zeichen.

*locale*<br/>
Für die gebietsschemaspezifische Übersetzung zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Jede dieser Routinen konvertiert eine Kopie von *c* in Kleinbuchstaben, wenn die Konvertierung möglich ist, und gibt das Ergebnis zurück. Es ist kein Rückgabewert zur Fehleranzeige reserviert.

## <a name="remarks"></a>Bemerkungen

Jede dieser Routinen konvertiert einen vorhandenen Großbuchstaben in einen Kleinbuchstaben, wenn dies möglich und relevant ist. Die Fallkonvertierung von **Towlower** ist gebietsschemaspezifisch. Es werden nur die für das aktuelle Gebietsschema relevanten Zeichen geändert. Die Funktionen ohne **das _l** Suffix verwenden das aktuell festgelegte Gebietsschema. Die Versionen dieser Funktionen, die über das **suffix _l** verfügen, nehmen das Gebietsschema als Parameter und verwenden es anstelle des aktuell festgelegten Gebietsschemas. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Damit **_tolower** die erwarteten Ergebnisse erzielen können, müssen [__isascii](isascii-isascii-iswascii.md) und [isupper](isupper-isupper-l-iswupper-iswupper-l.md) beide ungleich Null zurückgeben.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totlower**|**Tolower**|**_mbctolower**|**towlower**|
|**_totlower_l**|**_tolower_l**|**_mbctolower_l**|**_towlower_l**|

> [!NOTE]
> **_tolower_l** und **_towlower_l** haben keine Gebietsabhängigkeit und sollen nicht direkt aufgerufen werden. Sie werden für den internen Gebrauch durch **_totlower_l**zur Verfügung gestellt.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**Tolower**|\<ctype.h>|
|**_tolower**|\<ctype.h>|
|**towlower**|\<ctype.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Siehe das Beispiel in [to-Funktionen](../../c-runtime-library/to-functions.md).

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[is, isw Routines](../../c-runtime-library/is-isw-routines.md)<br/>
[zu Funktionen](../../c-runtime-library/to-functions.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
