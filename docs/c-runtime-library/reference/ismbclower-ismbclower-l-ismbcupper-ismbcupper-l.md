---
title: _ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l
ms.date: 4/2/2020
api_name:
- _ismbclower
- _ismbclower_l
- _ismbcupper_l
- _ismbcupper
- _o__ismbclower
- _o__ismbclower_l
- _o__ismbcupper
- _o__ismbcupper_l
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
- _ismbcupper
- _ismbclower
helpviewer_keywords:
- _ismbcupper function
- ismbclower function
- _ismbclower_l function
- ismbcupper_l function
- _ismbclower function
- ismbcupper function
- ismbclower_l function
- _ismbcupper_l function
ms.assetid: 17d89587-65bc-477c-ba8f-a84e63cf59e7
ms.openlocfilehash: 9a0991d974c33cff22044364f7a4351f160215a8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342932"
---
# <a name="_ismbclower-_ismbclower_l-_ismbcupper-_ismbcupper_l"></a>_ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l

Überprüft, ob ein Multibytezeichen in Klein- oder Großschreibung vorliegt.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
int _ismbclower(
   unsigned int c
);
int _ismbclower_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcupper(
   unsigned int c
);
int _ismbcupper_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*C*<br/>
Zu testende Zeichen.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Jede dieser Routinen gibt einen Wert ungleich 0 zurück, wenn das Zeichen die Testbedingung erfüllt, bzw. 0, wenn es sie nicht erfüllt. Wenn *c*<= 255 und es eine entsprechende **_ismbb** Routine gibt (z. B. **entspricht _ismbcalnum** **_ismbbalnum),** ist das Ergebnis der Rückgabewert der entsprechenden **_ismbb** Routine.

## <a name="remarks"></a>Bemerkungen

Jede dieser Funktionen testet ein angegebenes Mehrbytezeichen auf eine angegebene Bedingung.

Die Versionen dieser Funktionen mit dem **Suffix _l** sind identisch, außer dass sie das übergebene Gebietsschema anstelle des aktuellen Gebietsschemas für ihr gebietsschemaabhängiges Verhalten verwenden. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

|Routine|Testbedingung|Beispiel für Codepage 932|
|-------------|--------------------|---------------------------|
|**_ismbclower**|Kleinbuchstaben alphabetisch|Gibt einen Wert ungleich Null zurück, wenn c eine Einzelbyte-Darstellung eines ENGLISCHEN BUCHSTABENs in Kleinbuchstaben ist: 0x61<=*c*<=0x7A. *c*|
|**_ismbclower_l**|Kleinbuchstaben alphabetisch|Gibt einen Wert ungleich Null zurück, wenn c eine Einzelbyte-Darstellung eines ENGLISCHEN BUCHSTABENs in Kleinbuchstaben ist: 0x61<=*c*<=0x7A. *c*|
|**_ismbcupper**|Großbuchstaben alphabetisch|Gibt einen Wert ungleich Null zurück, wenn c eine Einzelbyte-Darstellung eines englischen ASCII-Großbuchstabens *ist:* 0x41<=*c*<=0x5A.|
|**_ismbcupper_l**|Großbuchstaben alphabetisch|Gibt einen Wert ungleich Null zurück, wenn c eine Einzelbyte-Darstellung eines englischen ASCII-Großbuchstabens *ist:* 0x41<=*c*<=0x5A.|

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_ismbclower**|\<mbstring.h>|
|**_ismbclower_l**|\<mbstring.h>|
|**_ismbcupper**|\<mbstring.h>|
|**_ismbcupper_l**|\<mbstring.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Zeichenklassifizierung](../../c-runtime-library/character-classification.md)<br/>
[_ismbc-Routinen](../../c-runtime-library/ismbc-routines.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[is, isw Routines](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb Routinen](../../c-runtime-library/ismbb-routines.md)<br/>
