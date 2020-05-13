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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 491a652f19e9e1895aa62092c5c890923008f6e1
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911907"
---
# <a name="_mbsnbcoll-_mbsnbcoll_l-_mbsnbicoll-_mbsnbicoll_l"></a>_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l

Vergleicht *n* Bytes von zwei Multibytezeichen-Zeichen folgen mithilfe von Multibytezeichen-Codepage-Informationen.

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

*Zeichenfolge1*, *Zeichenfolge2*<br/>
Zu vergleichende Zeichenfolgen.

*count*<br/>
Anzahl der zu vergleichenden Bytes.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Der Rückgabewert gibt die Beziehung der Teil Zeichenfolgen von *Zeichenfolge1* und *Zeichenfolge2*an.

|Rückgabewert|Beschreibung|
|------------------|-----------------|
|< 0|*Zeichenfolge1* Teil Zeichenfolge kleiner als *Zeichenfolge2* Teil Zeichenfolge.|
|0|*Zeichenfolge1* Teil Zeichenfolge, die mit *Zeichenfolge2* Teil Zeichenfolge identisch ist.|
|> 0|*Zeichenfolge1* Teil Zeichenfolge größer als *Zeichenfolge2* Teil Zeichenfolge.|

Wenn *Zeichenfolge1* oder *Zeichenfolge2* **null** ist oder *count* größer als **INT_MAX**ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, geben diese Funktionen **_NLSCMPERROR** zurück und legen **errno** auf **EINVAL**fest. Um **_NLSCMPERROR**zu verwenden, fügen Sie entweder String. h oder mbstring. h ein.

## <a name="remarks"></a>Hinweise

Jede dieser Funktionen sortiert höchstens die ersten *Anzahl* Bytes in *Zeichenfolge1* und *Zeichenfolge2* und gibt einen Wert zurück, der die Beziehung zwischen den resultierenden Teil Zeichenfolgen von *Zeichenfolge1* und *Zeichenfolge2*angibt. Wenn das letzte Byte in der Teil Zeichenfolge von " *Zeichenfolge1* " oder " *Zeichenfolge2* " ein führendes Byte ist, ist es nicht im Vergleich enthalten. Diese Funktionen vergleichen nur die kompletten Zeichen in den Teil Zeichenfolgen. **_mbsnbicoll** ist eine Version von **_mbsnbcoll**ohne Beachtung der Groß-/Kleinschreibung. Wie [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md) und [_mbsnbicmp](mbsnbicmp-mbsnbicmp-l.md) **_mbsnbcoll** und **_mbsnbicoll** die beiden Multibytezeichen-Zeichen folgen entsprechend der lexikografischen Reihenfolge, die von der derzeit verwendeten Multibytezeichen- [Codepage](../../c-runtime-library/code-pages.md) angegeben wird.

Bei manchen Codepages und entsprechenden Zeichensätzen kann die Reihenfolge der Zeichen im Zeichensatz möglicherweise von der lexikografischen Reihenfolge abweichen. Im "C "-Gebietsschema ist dies nicht der Fall: Die Reihenfolge der Zeichen im ASCII-Zeichensatz entspricht der lexikografischen Reihenfolge der Zeichen. In bestimmten europäischen Codepages beispielsweise steht im Zeichensatz das Zeichen "a" (Wert 0x61) vor dem Zeichen "ä" (Wert 0xE4), das Zeichen "ä" steht lexikografisch gesehen jedoch vor dem Zeichen "a". Wenn Sie in einer solchen Instanz einen lexikografischen Vergleich von Zeichen folgen nach Bytes durchführen möchten, verwenden Sie **_mbsnbcoll** statt **_mbsnbcmp**. Verwenden Sie **_mbsnbcmp**, um nur die Zeichen folgen Gleichheit zu überprüfen.

Da die **Coll** -Funktionen Zeichen folgen für Vergleiche lexikografisch sortieren, während die **CMP** -Funktionen einfach auf Zeichen folgen Gleichheit testen, sind die **Coll** -Funktionen viel langsamer als die entsprechenden **CMP** -Versionen. Daher sollten die **Coll** -Funktionen nur verwendet werden, wenn es in der aktuellen Codepage einen Unterschied zwischen der Reihenfolge des Zeichensatzes und der lexikografischen Zeichen Reihenfolge gibt, und dieser Unterschied für den Vergleich von Interesse ist.

Der Ausgabewert ist von der Kategorieeinstellung **LC_CTYPE** des Gebietsschemas betroffen. Weitere Informationen finden Sie unter [setlocale](setlocale-wsetlocale.md). Die Versionen dieser Funktionen ohne das **_l**-Suffix verwenden das aktuelle Gebietsschema für dieses vom Gebietsschema abhängige Verhalten; die Versionen mit dem **_l**-Suffix sind beinahe identisch, verwenden jedoch stattdessen den ihnen übergebenen Gebietsschemaparameter. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

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

## <a name="see-also"></a>Weitere Informationen

[Zeichen folgen Bearbeitung](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[Funktionen von "strecoll"](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
