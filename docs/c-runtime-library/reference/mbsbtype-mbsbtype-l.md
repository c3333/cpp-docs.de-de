---
title: _mbsbtype, _mbsbtype_l
ms.date: 4/2/2020
api_name:
- _mbsbtype_l
- _mbsbtype
- _o__mbsbtype
- _o__mbsbtype_l
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
- mbsbtype
- mbsbtype_l
- _mbsbtype_l
- _mbsbtype
helpviewer_keywords:
- _mbsbtype function
- mbsbtype function
- _mbsbtype_l function
- mbsbtype_l function
ms.assetid: 0d5dd91a-d32d-4f98-ac57-98dfc9e98eac
ms.openlocfilehash: c1431a2d0886ffd3d16b43abf82b7342c166273a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909478"
---
# <a name="_mbsbtype-_mbsbtype_l"></a>_mbsbtype, _mbsbtype_l

Gibt den Bytetyp in einer Zeichenfolge zurück.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
int _mbsbtype(
   const unsigned char *mbstr,
   size_t count
);
int _mbsbtype_l(
   const unsigned char *mbstr,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*mbstr*<br/>
Adresse einer Sequenz von Multibytezeichen.

*count*<br/>
Byte-Offset vom Anfang der Zeichenfolge.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

**_mbsbtype** und **_mbsbtype_l** gibt einen ganzzahligen Wert zurück, der das Ergebnis des Tests für das angegebene Byte angibt. Die Manifestkonstanten in der folgenden Tabelle sind in Mbctype.h definiert.

|Rückgabewert|Bytetyp|
|------------------|---------------|
|**_MBC_SINGLE** (0)|Einzelbytezeichen. In der Codepage 932 gibt **_mbsbtype** z. b. 0 (null) zurück, wenn das angegebene Byte im Bereich 0x20-0x7E oder 0xA1-0xDF liegt.|
|**_MBC_LEAD** (1)|Führendes Byte des Multibytezeichens. In der Codepage 932 gibt **_mbsbtype** z. b. 1 zurück, wenn das angegebene Byte im Bereich 0x81-0x9F oder 0xE0-0xFC liegt.|
|**_MBC_TRAIL** (2)|Nachfolgendes Byte des Multibytezeichens. In der Codepage 932 gibt **_mbsbtype** beispielsweise 2 zurück, wenn das angegebene Byte im Bereich 0x40-0x7E oder 0x80-0xFC liegt.|
|**_MBC_ILLEGAL** (-1)|**Null** -Zeichenfolge, ungültiges Zeichen oder NULL-Byte gefunden vor dem Byte bei der Offset *Anzahl* in *mbstr*.|

## <a name="remarks"></a>Hinweise

Die **_mbsbtype** -Funktion bestimmt den Typ eines Bytes in einer Multibytezeichenfolge. Die-Funktion überprüft nur das Byte bei der Offset *Anzahl* in *mbstr*, wobei ungültige Zeichen vor dem angegebenen Byte ignoriert werden.

Der Ausgabewert ist von der Kategorieeinstellung **LC_CTYPE** des Gebietsschemas betroffen. Weitere Informationen finden Sie unter [setlocale](setlocale-wsetlocale.md). Die Version dieser Funktion ohne das **_l** -Suffix verwendet das aktuelle Gebiets Schema für dieses vom Gebiets Schema abhängige Verhalten. die Version mit dem **_l** -Suffix ist beinahe identisch, verwendet jedoch stattdessen den übergebenen Gebiets Schema Parameter. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Wenn die Eingabe Zeichenfolge **null**ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, wird **errno** auf **EINVAL** festgelegt, und die Funktion gibt **_MBC_ILLEGAL**zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|**_mbsbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbsbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* Für Manifestkonstanten, die als Rückgabewerte verwendet werden.

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Byteklassifizierung](../../c-runtime-library/byte-classification.md)<br/>
