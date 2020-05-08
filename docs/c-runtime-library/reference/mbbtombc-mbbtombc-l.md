---
title: _mbbtombc, _mbbtombc_l
ms.date: 4/2/2020
api_name:
- _mbbtombc_l
- _mbbtombc
- _o__mbbtombc
- _o__mbbtombc_l
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
- _mbbtombc_l
- _mbbtombc
- mbbtombc_l
- mbbtombc
helpviewer_keywords:
- mbbtombc_l function
- mbbtombc function
- _mbbtombc_l function
- _mbbtombc function
ms.assetid: 78593389-b0fc-43b6-8c1f-2a6bf702d64e
ms.openlocfilehash: b2088ea83729a74a60e75d1710529480f34cd638
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919604"
---
# <a name="_mbbtombc-_mbbtombc_l"></a>_mbbtombc, _mbbtombc_l

Konvertiert ein Einzelbyte-Multibytezeichen in ein entsprechendes Doppelbyte-Multibytezeichen.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
unsigned int _mbbtombc(
   unsigned int c
);
unsigned int _mbbtombc_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*scher*<br/>
Zu konvertierendes Einzelbytezeichen.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Wenn **_mbbtombc** erfolgreich *c*konvertiert, wird ein Multibytezeichen zurückgegeben. Andernfalls wird *c*zurückgegeben.

## <a name="remarks"></a>Hinweise

Die **_mbbtombc** -Funktion konvertiert ein angegebenes Einzel Byte-Multibytezeichen in ein entsprechendes Doppelbyte-Multibytezeichen. Zeichen müssen innerhalb des Bereichs 0x20-0x7E oder 0xA1-0xDF liegen, um konvertiert zu werden.

Der Ausgabewert wird von der Einstellung der **LC_CTYPE** Kategorieeinstellung des Gebiets Schemas beeinflusst. Weitere Informationen finden Sie [unter setlocale, _wsetlocale](setlocale-wsetlocale.md) . Die Versionen dieser Funktion sind identisch, mit dem Unterschied, dass **_mbbtombc** das aktuelle Gebiets Schema für dieses vom Gebiets Schema abhängige Verhalten verwendet, und **_mbbtombc_l** stattdessen den übergebenen Gebiets Schema Parameter verwendet. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

In früheren Versionen hieß **_mbbtombc** den Namen **handezen**. Verwenden Sie für neuen Code **_mbbtombc**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_mbbtombc**|\<mbstring.h>|
|**_mbbtombc_l**|\<mbstring.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[_mbctombb, _mbctombb_l](mbctombb-mbctombb-l.md)<br/>
