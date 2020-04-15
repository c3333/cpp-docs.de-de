---
title: _stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l
ms.date: 4/2/2020
api_name:
- _mbsicoll_l
- _stricoll_l
- _mbsicoll
- _wcsicoll_l
- _wcsicoll
- _stricoll
- _o__mbsicoll
- _o__mbsicoll_l
- _o__stricoll
- _o__stricoll_l
- _o__wcsicoll
- _o__wcsicoll_l
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
- stricoll
- _stricoll
- _wcsicoll
- mbsicoll_l
- _mbsicoll
- _ftcsicoll
- wcsicoll_l
- _tcsicoll
- mbsicoll
- stricoll_l
helpviewer_keywords:
- code pages, using for string comparisons
- _ftcsicoll function
- _mbsicoll_l function
- _mbsicoll function
- mbsicoll function
- stricoll function
- tcsicoll function
- string comparison [C++], culture-specific
- _tcsicoll function
- _stricoll function
- _stricoll_l function
- _wcsicoll function
- mbsicoll_l function
- stricoll_l function
- strings [C++], comparing by code page
- ftcsicoll function
ms.assetid: 8ec93016-5a49-49d2-930f-721566661d82
ms.openlocfilehash: d726d2d33f8f775d09e6197dfeda6abb91106a53
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355328"
---
# <a name="_stricoll-_wcsicoll-_mbsicoll-_stricoll_l-_wcsicoll_l-_mbsicoll_l"></a>_stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l

Vergleicht Zeichenfolgen mithilfe gebietsschemaspezifischen Informationen.

> [!IMPORTANT]
> **_mbsicoll** und **_mbsicoll_l** können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
int _stricoll(
   const char *string1,
   const char *string2
);
int _wcsicoll(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbsicoll(
   const unsigned char *string1,
   const unsigned char *string2
);
int _stricoll_l(
   const char *string1,
   const char *string2,
   _locale_t locale
);
int _wcsicoll_l(
   const wchar_t *string1,
   const wchar_t *string2,
   _locale_t locale
);
int _mbsicoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*string1*, *string2*<br/>
Zu vergleichende mit NULL endende Zeichenfolgen.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Jede dieser Funktionen gibt wie folgt einen Wert zurück, der die Beziehung von *string1* zu *string2*angibt.

|Rückgabewert|Verhältnis von string1 zu string2|
|------------------|----------------------------------------|
|< 0|*string1* kleiner als *string2*|
|0|*string1* identisch mit *string2*|
|> 0|*String1* größer als *string2*|
|**_NLSCMPERROR**|Ein Fehler ist aufgetreten.|

Jede dieser Funktionen gibt **_NLSCMPERROR**zurück. Um **_NLSCMPERROR**zu \<verwenden, schließen \<Sie entweder string.h> oder mbstring.h> ein. **_wcsicoll** kann fehlschlagen, wenn *string1* oder *string2* breitstellige Codes außerhalb der Domäne der Sortiersequenz enthält. Wenn ein Fehler auftritt, **kann _wcsicoll** **errno** auf **EINVAL**setzen. Um bei einem Aufruf von **_wcsicoll**nach einem Fehler zu suchen, legen Sie **errno** auf 0 fest, und überprüfen Sie dann **errno,** nachdem Sie **_wcsicoll**aufgerufen haben.

## <a name="remarks"></a>Bemerkungen

Jede dieser Funktionen führt einen Vergleich von *String1* und *string2* gemäß der derzeit verwendenden Codepage durch. Diese Funktionen sollten nur verwendet werden, wenn es in der aktuellen Codepage einen Unterschied zwischen der Reihenfolge des Zeichensatzes und der lexikografischen Reihenfolge gibt, und dieser Unterschied für den Zeichenfolgenvergleich relevant ist.

**_stricmp** unterscheidet sich von **_stricoll** dadurch, dass der **_stricmp** Vergleich von **LC_CTYPE**beeinflusst wird, während der **_stricoll** Vergleich nach den **LC_CTYPE** und **LC_COLLATE** Kategorien des Gebietsschemas erfolgt. Weitere Informationen zu den **LC_COLLATE** Kategorie finden Sie unter [setlocale](setlocale-wsetlocale.md) und [Locale Categories](../../c-runtime-library/locale-categories.md). Die Versionen dieser Funktionen ohne das **_l** Suffix verwenden das aktuelle Gebietsschema; Die Versionen mit dem **Suffix _l** sind identisch, außer dass sie stattdessen das übergebene Gebietsschema verwenden. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Mit allen diesen Funktionen werden ihre Parameter überprüft. Wenn *string1* oder *string2* **NULL-Zeiger** sind, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, geben diese Funktionen **_NLSCMPERROR** zurück und setzen **errno** auf **EINVAL**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicoll**|**_stricoll**|**_mbsicoll**|**_wcsicoll**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_stricoll**, **_stricoll_l**|\<string.h>|
|**_wcsicoll**, **_wcsicoll_l**|\<wchar.h>, \<string.h>|
|**_mbsicoll**, **_mbsicoll_l**|\<mbstring.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Locale](../../c-runtime-library/locale.md)<br/>
[String-Manipulation](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll-Funktionen](../../c-runtime-library/strcoll-functions.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l](mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
