---
title: toupper, _toupper, towupper, _toupper_l, _towupper_l
ms.date: 4/2/2020
api_name:
- _toupper_l
- towupper
- toupper
- _towupper_l
- _toupper
- _o__toupper
- _o__toupper_l
- _o__towupper_l
- _o_toupper
- _o_towupper
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
- towupper
- _toupper
- _totupper
- toupper
helpviewer_keywords:
- _toupper function
- towupper function
- uppercase, converting strings to
- totupper function
- string conversion, to different characters
- towupper_l function
- toupper_l function
- string conversion, case
- _toupper_l function
- _towupper_l function
- _totupper function
- case, converting
- characters, converting
- toupper function
ms.assetid: cdef1b0f-b19c-4d11-b7d2-cf6334c9b6cc
ms.openlocfilehash: 85c218fdb3f5153e572e434bffbdb64510554d07
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362325"
---
# <a name="toupper-_toupper-towupper-_toupper_l-_towupper_l"></a>toupper, _toupper, towupper, _toupper_l, _towupper_l

Zeichen in Großbuchstaben konvertieren.

## <a name="syntax"></a>Syntax

```C
int toupper(
   int c
);
int _toupper(
   int c
);
int towupper(
   wint_t c
);
int _toupper_l(
   int c ,
   _locale_t locale
);
int _towupper_l(
   wint_t c ,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*C*<br/>
Zu konvertierendes Zeichen.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Jede dieser Routinen konvertiert nach Möglichkeit eine Kopie von *c*und gibt das Ergebnis zurück.

Wenn *c* ein breites Zeichen ist, für das **iswlower** ungleich Null ist und ein entsprechendes breites Zeichen vorhanden ist, für das [iswupper](isupper-isupper-l-iswupper-iswupper-l.md) ungleich Null ist, gibt **Towupper** das entsprechende breit zeichen zurück; Andernfalls kehrt **das Abwupper** *c* unverändert zurück.

Es ist kein Rückgabewert zur Fehleranzeige reserviert.

Damit **toupper** die erwarteten Ergebnisse liefert, müssen [__isascii](isascii-isascii-iswascii.md) und [islower](islower-iswlower-islower-l-iswlower-l.md) beide ungleich Null zurückgeben.

## <a name="remarks"></a>Bemerkungen

Jede dieser Routinen konvertiert einen vorhandenen Kleinbuchstaben in einen Großbuchstaben, wenn dies möglich und relevant ist. Die Fallkonvertierung von **Towupper** ist gebietsschemaspezifisch. Es werden nur die für das aktuelle Gebietsschema relevanten Zeichen geändert. Die Funktionen ohne **das _l** Suffix verwenden das aktuell festgelegte Gebietsschema. Die Versionen dieser Funktionen mit dem **Suffix _l** nehmen das Gebietsschema als Parameter und verwenden das anstelle des aktuell festgelegten Gebietsschemas. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Damit **toupper** die erwarteten Ergebnisse liefert, müssen [__isascii](isascii-isascii-iswascii.md) und [isupper](isupper-isupper-l-iswupper-iswupper-l.md) beide ungleich Null zurückgeben.

[Datenkonvertierungsroutinen](../../c-runtime-library/data-conversion.md)

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totupper**|**Toupper**|**_mbctoupper**|**towupper**|
|**_totupper_l**|**_toupper_l**|**_mbctoupper_l**|**_towupper_l**|

> [!NOTE]
> **_toupper_l** und **_towupper_l** haben keine Gebietsabhängigkeit und sollen nicht direkt aufgerufen werden. Sie werden für den internen Gebrauch durch **_totupper_l**zur Verfügung gestellt.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**Toupper**|\<ctype.h>|
|**_toupper**|\<ctype.h>|
|**towupper**|\<ctype.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Siehe das Beispiel in [to-Funktionen](../../c-runtime-library/to-functions.md).

## <a name="see-also"></a>Siehe auch

[is, isw Routines](../../c-runtime-library/is-isw-routines.md)<br/>
[zu Funktionen](../../c-runtime-library/to-functions.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
