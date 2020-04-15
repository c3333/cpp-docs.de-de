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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: d71a061d9af5028c9bc6b4008f9904606a233592
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340877"
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

**_mbsbtype** und **_mbsbtype_l** gibt einen Ganzzahlwert zurück, der das Ergebnis des Tests für das angegebene Byte angibt. Die Manifestkonstanten in der folgenden Tabelle sind in Mbctype.h definiert.

|Rückgabewert|Bytetyp|
|------------------|---------------|
|**_MBC_SINGLE** (0)|Einzelbytezeichen. In Codepage 932 **gibt _mbsbtype** beispielsweise 0 zurück, wenn das angegebene Byte im Bereich 0x20 - 0x7E oder 0xA1 - 0xDF liegt.|
|**_MBC_LEAD** (1)|Führendes Byte des Multibytezeichens. In Codepage 932 **gibt _mbsbtype** beispielsweise 1 zurück, wenn das angegebene Byte im Bereich 0x81 - 0x9F oder 0xE0 - 0xFC liegt.|
|**_MBC_TRAIL** (2)|Nachfolgendes Byte des Multibytezeichens. In Codepage 932 **gibt _mbsbtype** beispielsweise 2 zurück, wenn das angegebene Byte im Bereich 0x40 - 0x7E oder 0x80 - 0xFC liegt.|
|**_MBC_ILLEGAL** (-1)|**NULL-Zeichenfolge,** ungültiges Zeichen oder NULL-Byte, das vor dem Byte bei *Offsetanzahl* in *mbstr*gefunden wurde.|

## <a name="remarks"></a>Bemerkungen

Die **_mbsbtype-Funktion** bestimmt den Typ eines Bytes in einer Zeichenfolge mit mehreren Byte. Die Funktion untersucht nur das Byte bei *Offsetanzahl* in *mbstr*und ignoriert ungültige Zeichen vor dem angegebenen Byte.

Der Ausgabewert ist von der Kategorieeinstellung **LC_CTYPE** des Gebietsschemas betroffen. Weitere Informationen finden Sie unter [setlocale](setlocale-wsetlocale.md). Die Version dieser Funktion ohne das **suffix _l** verwendet das aktuelle Gebietsschema für dieses gebietsschemaabhängige Verhalten. Die Version mit dem **Suffix _l** ist identisch, außer dass sie stattdessen den übergebenen Gebietsschemaparameter verwendet. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Wenn die Eingabezeichenfolge **NULL**ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, wird **errno** auf **EINVAL** gesetzt, und die Funktion gibt **_MBC_ILLEGAL**zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|**_mbsbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbsbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* Für Manifestkonstanten, die als Rückgabewerte verwendet werden.

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Byteklassifizierung](../../c-runtime-library/byte-classification.md)<br/>
