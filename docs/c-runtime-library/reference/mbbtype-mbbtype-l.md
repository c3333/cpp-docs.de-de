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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: dca59f2d31cc5ad843a48e9825ef6a617d46ae4a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919590"
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

*scher*<br/>
Das zu überprüfende Zeichen.

*type*<br/>
Der Typ des zu prüfenden Bytes.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

**_mbbtype** gibt den Bytetyp in einer Zeichenfolge zurück. Diese Entscheidung ist Kontext abhängig, wie durch den Wert vom *Typ*angegeben, der die Test Bedingung für das Steuerelement bereitstellt. *Type* ist der Typ des vorherigen Byte in der Zeichenfolge. Die Manifestkonstanten in der folgenden Tabelle sind in Mbctype.h definiert.

|Wert des *Typs*|**_mbbtype** Tests für|Rückgabewert|*scher*|
|---------------------|--------------------------|------------------|---------|
|Einen beliebiger Wert außer 1|Gültiges Einzelbyte oder führendes Byte|**_MBC_SINGLE** (0)|Einzelnes Byte (0x20-0x7E, 0xA1-0xDF)|
|Einen beliebiger Wert außer 1|Gültiges Einzelbyte oder führendes Byte|**_MBC_LEAD** (1)|Führendes Byte des multibytezeichens (0x81-0x9F, 0xE0-0xFC)|
|Einen beliebiger Wert außer 1|Gültiges Einzelbyte oder führendes Byte|**_MBC_ILLEGAL**<br /><br /> (-1)|Ungültiges Zeichen (beliebiger Wert außer 0x20-0x7E, 0xA1-0xDF, 0x81-0x9F, 0xE0-0xFC)|
|1|Gültiges nachfolgendes Byte|**_MBC_TRAIL** (2)|Nachfolgendes Byte des multibytezeichens (0x40-0x7E, 0x80-0xFC)|
|1|Gültiges nachfolgendes Byte|**_MBC_ILLEGAL**<br /><br /> (-1)|Ungültiges Zeichen (beliebiger Wert außer 0x20-0x7E, 0xA1-0xDF, 0x81-0x9F, 0xE0-0xFC)|

## <a name="remarks"></a>Hinweise

Die **_mbbtype** -Funktion bestimmt den Typ eines Bytes in einem Multibytezeichen. Wenn der Wert des *Typs* ein beliebiger Wert außer 1 ist, **_mbbtype** auf ein gültiges Einzel Byte oder führendes Byte eines multibytezeichens. Wenn der Wert des *Typs* 1 ist, **_mbbtype** testet auf ein gültiges nachfolgendes Byte eines multibytezeichens.

Der Ausgabewert wird von der Einstellung der **LC_CTYPE** Kategorieeinstellung des Gebiets Schemas beeinflusst. Weitere Informationen finden Sie [unter setlocale, _wsetlocale](setlocale-wsetlocale.md) . Die **_mbbtype** Version dieser Funktion verwendet das aktuelle Gebiets Schema für dieses vom Gebiets Schema abhängige Verhalten. die **_mbbtype_l** -Version ist beinahe identisch, verwendet jedoch stattdessen den übergebenen Gebiets Schema Parameter. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

In früheren Versionen hieß **_mbbtype** " **chkctype**". Verwenden Sie für neuen Code stattdessen **_mbbtype** .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|**_mbbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* Für Definitionen von Manifestkonstanten, die als Rückgabewerte verwendet werden.

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Byteklassifizierung](../../c-runtime-library/byte-classification.md)<br/>
