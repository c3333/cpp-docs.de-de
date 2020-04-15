---
title: _mbbtype, _mbbtype_l
ms.date: 4/2/2020
api_name:
- _mbbtype
- _mbbtype_l
- _o__mbbtype
- _o__mbbtype_l
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
- _mbbtype_l
- mbbtype
- mbbtype_l
- _mbbtype
helpviewer_keywords:
- _mbbtype function
- _mbbtype_l function
- mbbtype function
- mbbtype_l function
ms.assetid: b8e34b40-842a-4298-aa39-0bd2d8e51c2a
ms.openlocfilehash: 7e2e818ed70ec393e4f81008f76ca9efe9cfa7e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341409"
---
# <a name="_mbbtype-_mbbtype_l"></a>_mbbtype, _mbbtype_l

Gibt den Bytetyp basierend auf dem vorherigen Byte zurück.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
int _mbbtype(
   unsigned char c,
   int type
);
int _mbbtype_l(
   unsigned char c,
   int type,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*C*<br/>
Das zu überprüfende Zeichen.

*type*<br/>
Der Typ des zu prüfenden Bytes.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

**_mbbtype** gibt den Bytetyp in einer Zeichenfolge zurück. Diese Entscheidung ist kontextabhängig, wie durch den Wert von *Typ*angegeben, der die Kontrolltestbedingung bereitstellt. *Typ* ist der Typ des vorherigen Bytes in der Zeichenfolge. Die Manifestkonstanten in der folgenden Tabelle sind in Mbctype.h definiert.

|Wert des *Typs*|**_mbbtype** Tests für|Rückgabewert|*C*|
|---------------------|--------------------------|------------------|---------|
|Einen beliebiger Wert außer 1|Gültiges Einzelbyte oder führendes Byte|**_MBC_SINGLE** (0)|Einzelbyte (0x20 - 0x7E, 0xA1 - 0xDF)|
|Einen beliebiger Wert außer 1|Gültiges Einzelbyte oder führendes Byte|**_MBC_LEAD** (1)|Leadbyte mit Multibyte-Charakter (0x81 - 0x9F, 0xE0 - 0xFC)|
|Einen beliebiger Wert außer 1|Gültiges Einzelbyte oder führendes Byte|**_MBC_ILLEGAL**<br /><br /> ( -1)|Ungültiges Zeichen (beliebiger Wert außer 0x20 - 0x7E, 0xA1 - 0xDF, 0x81 - 0x9F, 0xE0 - 0xFC|
|1|Gültiges nachfolgendes Byte|**_MBC_TRAIL** (2)|Trailing Byte mit Multibyte-Zeichen (0x40 - 0x7E, 0x80 - 0xFC)|
|1|Gültiges nachfolgendes Byte|**_MBC_ILLEGAL**<br /><br /> ( -1)|Ungültiges Zeichen (beliebiger Wert außer 0x20 - 0x7E, 0xA1 - 0xDF, 0x81 - 0x9F, 0xE0 - 0xFC|

## <a name="remarks"></a>Bemerkungen

Die **_mbbtype-Funktion** bestimmt den Typ eines Bytes in einem Multibyte-Zeichen. Wenn der Wert des *Typs* ein beliebiger Wert außer 1 ist, **_mbbtype** Tests für ein gültiges Einzelbyte oder Leadbyte eines Multibyte-Zeichens. Wenn der Wert des *Typs* 1 ist, **_mbbtype** Tests für ein gültiges Trailbyte eines Multibyte-Zeichens.

Der Ausgabewert wird durch die Einstellung der **LC_CTYPE** Kategorieeinstellung des Gebietsschemas beeinflusst. weitere Informationen finden Sie unter [setlocale, _wsetlocale.](setlocale-wsetlocale.md) Die **_mbbtype** Version dieser Funktion verwendet das aktuelle Gebietsschema für dieses gebietsschemaabhängige Verhalten. **Die _mbbtype_l** Version identisch ist, außer dass sie den Gebietsschemaparameter verwendet, der stattdessen übergeben wird. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

In früheren Versionen wurde **_mbbtype** **chkctype**genannt. Verwenden Sie für neuen Code **stattdessen _mbbtype.**

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|**_mbbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* Für Definitionen von Manifestkonstanten, die als Rückgabewerte verwendet werden.

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Byteklassifizierung](../../c-runtime-library/byte-classification.md)<br/>
