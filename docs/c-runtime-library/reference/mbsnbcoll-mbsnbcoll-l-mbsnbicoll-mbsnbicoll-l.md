---
title: _mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l
ms.date: 4/2/2020
api_name:
- _mbsnbicoll_l
- _mbsnbcoll_l
- _mbsnbcoll
- _mbsnbicoll
- _o__mbsnbcoll
- _o__mbsnbcoll_l
- _o__mbsnbicoll
- _o__mbsnbicoll_l
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbsnbcoll
- _mbsnbcoll_l
- _mbsnbicoll
- mbsnbcoll_l
helpviewer_keywords:
- _mbsnbcoll_l function
- mbsnbcoll_l function
- _mbsnbcoll function
- _tcsnicoll function
- mbsnbcoll function
- mbsnbicoll_l function
- mbsnbicoll function
- _tcsncoll function
- _mbsnbicoll function
- _mbsnbicoll_l function
- _tcsncoll_l function
- _tcsnicoll_l function
ms.assetid: d139ed63-ccba-4458-baa2-61cbcef03e94
ms.openlocfilehash: 0b02a34f9b721e4cfcf07ac3679d0dce166a4ff7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340745"
---
# <a name="_mbsnbcoll-_mbsnbcoll_l-_mbsnbicoll-_mbsnbicoll_l"></a>_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l

Vergleicht *n* Bytes von zwei Multibyte-Zeichen-Zeichenfolgen mithilfe von Multibyte-Codepageinformationen.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
int _mbsnbcoll(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsnbcoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
int _mbsnbicoll(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsnbicoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*string1*, *string2*<br/>
Zu vergleichende Zeichenfolgen.

*count*<br/>
Anzahl der zu vergleichenden Bytes.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Der Rückgabewert gibt die Beziehung der Teilzeichenfolgen von *string1* und *string2*an.

|Rückgabewert|BESCHREIBUNG|
|------------------|-----------------|
|< 0|*string1-Teilzeichenfolge* kleiner als *string2-Teilzeichenfolge.*|
|0|*string1-Teilzeichenfolge* identisch mit *string2-Teilzeichenfolge.*|
|> 0|*string1-Teilzeichenfolge* größer als *string2-Teilzeichenfolge.*|

Wenn *string1* oder *string2* **NULL** oder *Anzahl* größer als **INT_MAX**ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, geben diese Funktionen **_NLSCMPERROR** zurück und setzen **errno** auf **EINVAL**. Um **_NLSCMPERROR**zu verwenden, schließen Sie entweder String.h oder Mbstring.h ein.

## <a name="remarks"></a>Bemerkungen

Jede dieser Funktionen sammelt höchstens die ersten *Zählbytes* in *string1* und *string2* und gibt einen Wert zurück, der die Beziehung zwischen den resultierenden Teilzeichenfolgen *von string1* und *string2*angibt. Wenn das endgültige Byte in der Teilzeichenfolge von *string1* oder *string2* ein Leadbyte ist, wird es nicht in den Vergleich einbezogen. Diese Funktionen vergleichen nur vollständige Zeichen in den Teilzeichenfolgen. **_mbsnbicoll** ist eine Nicht-Groß-/Kleinschreibung von **_mbsnbcoll**. Wie [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md) und [_mbsnbicmp](mbsnbicmp-mbsnbicmp-l.md) **_mbsnbcoll** und **_mbsnbicoll** die beiden Multibyte-Zeichenzeichenfolgen entsprechend der lexikographischen Reihenfolge zusammenstellen, die durch die derzeit in Verwendung befindliche Multibyte-Codepage angegeben wird. [code page](../../c-runtime-library/code-pages.md)

Bei manchen Codepages und entsprechenden Zeichensätzen kann die Reihenfolge der Zeichen im Zeichensatz möglicherweise von der lexikografischen Reihenfolge abweichen. Im "C "-Gebietsschema ist dies nicht der Fall: Die Reihenfolge der Zeichen im ASCII-Zeichensatz entspricht der lexikografischen Reihenfolge der Zeichen. In bestimmten europäischen Codepages beispielsweise steht im Zeichensatz das Zeichen "a" (Wert 0x61) vor dem Zeichen "ä" (Wert 0xE4), das Zeichen "ä" steht lexikografisch gesehen jedoch vor dem Zeichen "a". Um einen lexikographischen Vergleich von Zeichenfolgen nach Bytes in einer solchen Instanz durchzuführen, verwenden Sie **_mbsnbcoll** anstelle **_mbsnbcmp**; , um nur auf Zeichenfolgengleichheit zu überprüfen, verwenden Sie **_mbsnbcmp**.

Da die **coll-Funktionen** Strings lexikographisch zum Vergleich zusammenfügen, während die **cmp-Funktionen** einfach auf Stringgleichheit testen, sind die **coll-Funktionen** viel langsamer als die entsprechenden **cmp-Versionen.** Daher sollten die **Coll-Funktionen** nur verwendet werden, wenn es einen Unterschied zwischen der Zeichensatzreihenfolge und der lexikographischen Zeichenreihenfolge in der aktuellen Codepage gibt und dieser Unterschied für den Vergleich von Interesse ist.

Der Ausgabewert ist von der Kategorieeinstellung **LC_CTYPE** des Gebietsschemas betroffen. Weitere Informationen finden Sie unter [setlocale](setlocale-wsetlocale.md). Die Versionen dieser Funktionen ohne das **_l**-Suffix verwenden das aktuelle Gebietsschema für dieses vom Gebietsschema abhängige Verhalten; die Versionen mit dem **_l**-Suffix sind beinahe identisch, verwenden jedoch stattdessen den ihnen übergebenen Gebietsschemaparameter. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncoll**|[_strncoll](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|**_mbsnbcoll**|[_wcsncoll](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|
|**_tcsncoll_l**|[_strncoll, _wcsncoll, _mbsncoll, _strncoll_l, _wcsncoll_l, _mbsncoll_l](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|**_mbsnbcoll_l**|[_wcsncoll_l](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|
|**_tcsnicoll**|[_strnicoll](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|**_mbsnbicoll**|[_wcsnicoll](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|
|**_tcsnicoll_l**|[_strnicoll_l](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|**_mbsnbicoll_l**|[_wcsnicoll_l](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_mbsnbcoll**|\<mbstring.h>|
|**_mbsnbcoll_l**|\<mbstring.h>|
|**_mbsnbicoll**|\<mbstring.h>|
|**_mbsnbicoll_l**|\<mbstring.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[String-Manipulation](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcoll-Funktionen](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
