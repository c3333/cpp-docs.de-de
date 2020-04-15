---
title: _mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l
ms.date: 4/2/2020
api_name:
- _mbcjistojms
- _mbcjmstojis
- _mbcjistojms_l
- _mbcjmstojis_l
- _o__mbcjistojms
- _o__mbcjistojms_l
- _o__mbcjmstojis
- _o__mbcjmstojis_l
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
- mbcjistojms
- _mbcjistojms
- _mbcjistojms_l
- _mbcjmstojis_l
- _mbcjmstojis
- mbcjmstojis_l
- mbcjistojms_l
- mbcjmstojis
helpviewer_keywords:
- _mbcjmstojis_l function
- _mbcjistojms function
- mbcjmstojis function
- _mbcjistojms_l function
- _mbcjmstojis function
- mbcjistojms function
- mbcjmstojis_l function
- mbcjistojms_l function
ms.assetid: dece5127-b337-40a4-aa10-53320a2c9432
ms.openlocfilehash: ef0010088543f1c580e536f120cae681a7582491
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341179"
---
# <a name="_mbcjistojms-_mbcjistojms_l-_mbcjmstojis-_mbcjmstojis_l"></a>_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l

Konvertiert zwischen Zeichen aus den Zeichensätzen Japan Industry Standard (JIS) und Japan Microsoft (JMS).

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
unsigned int _mbcjistojms(
   unsigned int c
);
unsigned int _mbcjistojms_l(
   unsigned int c,
   _locale_t locale
);
unsigned int _mbcjmstojis(
   unsigned int c
);
unsigned int _mbcjmstojis_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*C*<br/>
Zu konvertierendes Zeichen.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Bei einem japanischen Gebietsschema geben diese Funktionen ein konvertiertes Zeichen zurück. Wenn keine Konvertierung möglich ist, wir 0 (null) zurückgegeben. Bei einem nicht japanischen Gebietsschema geben diese Funktionen das Zeichen zurück, das übergeben wurde.

## <a name="remarks"></a>Bemerkungen

Die **_mbcjistojms-Funktion** konvertiert ein JIS-Zeichen (Japan Industry Standard) in ein Microsoft Kanji -Zeichen (Shift JIS). Das Zeichen wird nur konvertiert, wenn die Lead- und Trail-Bytes im Bereich 0x21 - 0x7E liegen. Wenn sich das Lead- oder Testbyte außerhalb dieses Bereichs befindet, wird **errno** auf **EILSEQ**gesetzt. Weitere Informationen hierzu und über andere Fehlercodes finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Die **_mbcjmstojis-Funktion** konvertiert ein Shift-JIS-Zeichen in ein JIS-Zeichen. Das Zeichen wird nur konvertiert, wenn das Leadbyte im Bereich 0x81 - 0x9F oder 0xE0 - 0xFC liegt und das Trailbyte im Bereich 0x40 - 0x7E oder 0x80 - 0xFC liegt. Beachten Sie, dass einigen Codepunkten in diesem Bereich kein Zeichen zugewiesen ist und sie daher nicht konvertiert werden können.

Der Wert *c* sollte ein 16-Bit-Wert sein, dessen obere 8 Bits das Leadbyte des zu konvertierenden Zeichens darstellen und dessen untere 8 Bits das Trailbyte darstellen.

Der Ausgabewert ist von der Kategorieeinstellung **LC_CTYPE** des Gebietsschemas betroffen. Weitere Informationen finden Sie unter [setlocale](setlocale-wsetlocale.md). Die Versionen dieser Funktionen ohne das **_l**-Suffix verwenden das aktuelle Gebietsschema für dieses vom Gebietsschema abhängige Verhalten; die Versionen mit dem **_l**-Suffix sind beinahe identisch, verwenden jedoch stattdessen den ihnen übergebenen Gebietsschemaparameter. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

In früheren Versionen wurden **_mbcjistojms** und **_mbcjmstojis** **jistojms** bzw. **jmstojis**genannt. **stattdessen**sollten _mbcjistojms , **_mbcjistojms_l**, **_mbcjmstojis** und **_mbcjmstojis_l** verwendet werden.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_mbcjistojms**|\<mbstring.h>|
|**_mbcjistojms_l**|\<mbstring.h>|
|**_mbcjmstojis**|\<mbstring.h>|
|**_mbcjmstojis_l**|\<mbstring.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[_ismbb Routinen](../../c-runtime-library/ismbb-routines.md)<br/>
