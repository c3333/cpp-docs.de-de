---
title: _mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l
ms.date: 4/2/2020
api_name:
- _mbctohira
- _mbctohira_l
- _mbctokata
- _mbctokata_l
- _o__mbctohira
- _o__mbctohira_l
- _o__mbctokata
- _o__mbctokata_l
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
- _mbctokata
- mbctohira
- _mbctohira
- _mbctohira_l
- mbctokata
- mbctokata_l
- mbctohira_l
- _mbctokata_l
helpviewer_keywords:
- _mbctokata function
- _mbctokata_l function
- _mbctohira_l function
- mbctohira_l function
- mbctohira function
- mbctokata_l function
- _mbctohira function
- mbctokata function
ms.assetid: f949afd7-44d4-4f08-ac8f-1fef2c915a1c
ms.openlocfilehash: b5af94932fc90e6bcaee584e16f3056ee36dab51
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914375"
---
# <a name="_mbctohira-_mbctohira_l-_mbctokata-_mbctokata_l"></a>_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l

Konvertiert zwischen Hiragana- und Katakana-Zeichen.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
unsigned int _mbctohira(
   unsigned int c
);
unsigned int _mbctohira_l(
   unsigned int c,
   _locale_t locale
);
unsigned int _mbctokata(
   unsigned int c
);
unsigned int _mbctokata_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*scher*<br/>
Zu konvertierendes Multibytezeichen.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Jede dieser Funktionen gibt, sofern möglich, das konvertierte Zeichen *c*zurück. Andernfalls wird das Zeichen *c* unverändert zurückgegeben.

## <a name="remarks"></a>Hinweise

Die Funktionen " **_mbctohira** " und " **_mbctokata** " testen ein Zeichen *c* und wenden, wenn möglich, eine der folgenden Konvertierungen an.

|Routinen|Konvertiert|
|--------------|--------------|
|**_mbctohira** **_mbctohira_l**|Multibyte-Katakana in Multibyte-Hiragana.|
|**_mbctokata** **_mbctokata_l**|Multibyte-Hiragana in Multibyte-Katakana.|

Der Ausgabewert ist von der Kategorieeinstellung **LC_CTYPE** des Gebietsschemas betroffen. Weitere Informationen finden Sie unter [setlocale](setlocale-wsetlocale.md). Die Versionen dieser Funktionen sind identisch, mit der Ausnahme, dass diejenigen, die nicht über das **_l** -Suffix verfügen, das aktuelle Gebiets Schema für dieses vom Gebiets Schema abhängige Verhalten verwenden, und diejenigen, die über das **_l** -Suffix verfügen, verwenden stattdessen den übergebenen Gebiets Schema Parameter. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

In früheren Versionen hieß **_mbctohira** " **jdehira** ", und **_mbctokata** wurde als " **jykata**" bezeichnet. Verwenden Sie bei neuem Code die neuen Namen.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_mbctohira**|\<mbstring.h>|
|**_mbctohira_l**|\<mbstring.h>|
|**_mbctokata**|\<mbstring.h>|
|**_mbctokata_l**|\<mbstring.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)<br/>
[_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)<br/>
[_mbctombb, _mbctombb_l](mbctombb-mbctombb-l.md)<br/>
