---
title: isblank, iswblank, _isblank_l, _iswblank_l
ms.date: 4/2/2020
api_name:
- isblank
- _isblank_l
- iswblank
- _iswblank_l
- _o_isblank
- _o_iswblank
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
- _iswblank_l
- isblank
- _istblank_l
- _istblank
- _isblank_l
- iswblank
ms.assetid: 33ce96c0-f387-411a-8283-c3d2a69e56bd
ms.openlocfilehash: 736a0791f1e5ee4b11e61164861cc6dc0c7a9c87
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343892"
---
# <a name="isblank-iswblank-_isblank_l-_iswblank_l"></a>isblank, iswblank, _isblank_l, _iswblank_l

Bestimmt, ob eine ganze Zahl ein Leerzeichen darstellt.

## <a name="syntax"></a>Syntax

```C
int isblank(
   int c
);
int iswblank(
   wint_t c
);
int _isblank_l(
   int c,
   _locale_t locale
);
int _iswblank_l(
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

Jede dieser Routinen gibt einen Wert ungleich Null zurück, wenn *c* eine bestimmte Darstellung eines Leerzeichens oder horizontalen Registerkartenzeichens oder eine von einem gebietsschemaspezifischen Satz von Zeichen ist, die zum Trennen von Wörtern innerhalb einer Textzeile verwendet werden. **isblank** gibt einen Wert ungleich Null zurück, wenn *c* ein Leerzeichen (0x20) oder ein horizontales Tabstoppzeichen (0x09) ist. Das Ergebnis der Testbedingung für die **isblank-Funktionen** hängt von der **LC_CTYPE** Kategorieeinstellung des Gebietsschemas ab. Weitere Informationen finden Sie unter [setlocale, _wsetlocale](setlocale-wsetlocale.md). Die Versionen dieser Funktionen, die nicht über das **_l** Suffix verfügen, verwenden das aktuelle Gebietsschema für ein gebietsschemaabhängiges Verhalten. Die Versionen, die über das **_l** Suffix verfügen, sind identisch, außer dass sie stattdessen das Gebietsschema verwenden, das übergeben wird. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

**iswblank** gibt einen Wert ungleich Null zurück, wenn *c* ein breites Zeichen ist, das einem Standardraum oder einem horizontalen Tabstoppzeichen entspricht.

Das Verhalten von **isblank** und **_isblank_l** ist nicht definiert, wenn *c* nicht EOF ist oder im Bereich 0 bis 0xFF, einschließlich. Wenn eine Debug-CRT-Bibliothek verwendet wird und *c* nicht einer dieser Werte ist, werden die Funktionen eine Assertion aus.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istblank**|**isblank**|[_ismbcblank](ismbcgraph-functions.md)|**iswblank**|
|**_istblank_l**|**_isblank_l**|[_ismbcblank_l](ismbcgraph-functions.md)|**_iswblank_l**|

## <a name="remarks"></a>Bemerkungen

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**isblank**|\<ctype.h>|
|**iswblank**|\<ctype.h> oder \<wchar.h>|
|**_isblank_l**|\<ctype.h>|
|**_iswblank_l**|\<ctype.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Zeichenklassifizierung](../../c-runtime-library/character-classification.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[is, isw Routines](../../c-runtime-library/is-isw-routines.md)<br/>
