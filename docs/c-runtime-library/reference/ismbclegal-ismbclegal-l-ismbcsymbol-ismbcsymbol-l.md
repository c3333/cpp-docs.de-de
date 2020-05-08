---
title: _ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l
ms.date: 4/2/2020
api_name:
- _ismbclegal_l
- _ismbclegal
- _ismbcsymbol
- _ismbcsymbol_l
- _o__ismbclegal
- _o__ismbclegal_l
- _o__ismbcsymbol
- _o__ismbcsymbol_l
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
- ismbcsymbol_l
- _ismbcsymbol_l
- _ismbcsymbol
- _ismbclegal_l
- _ismbclegal
- ismbclegal_l
- ismbcsymbol
- ismbclegal
helpviewer_keywords:
- ismbcsymbol function
- ismbclegal_l function
- _istlegal_l function
- istlegal function
- _istlegal function
- _ismbcsymbol function
- _ismbclegal_l function
- ismbclegal function
- ismbcsymbol_l function
- _ismbclegal function
- _ismbcsymbol_l function
- istlegal_l function
ms.assetid: 31bf1ea5-b56f-4e28-b21e-b49a2cf93ffc
ms.openlocfilehash: 295eabdef37a7b8d6bfb8408ba0d3d683a59c42d
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919720"
---
# <a name="_ismbclegal-_ismbclegal_l-_ismbcsymbol-_ismbcsymbol_l"></a>_ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l

Überprüft, ob ein Multibytezeichen ein gültiges Zeichen oder ein Symbolzeichen ist.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
int _ismbclegal(
   unsigned int c
);
int _ismbclegal_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcsymbol(
   unsigned int c
);
int _ismbcsymbol_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*scher*<br/>
Zu testende Zeichen.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Jede dieser Routinen gibt einen Wert ungleich 0 zurück, wenn das Zeichen die Testbedingung erfüllt, bzw. 0, wenn es sie nicht erfüllt. Wenn *c*<= 255 und es eine entsprechende **_ismbb** Routine gibt (z. b. **_ismbcalnum** entspricht **_ismbbalnum**), ist das Ergebnis der Rückgabewert der entsprechenden **_ismbb** -Routine.

## <a name="remarks"></a>Hinweise

Jede dieser Funktionen testet ein angegebenes Mehrbytezeichen auf eine angegebene Bedingung.

Die Versionen dieser Funktionen mit dem **_l** -Suffix sind beinahe identisch, verwenden jedoch das übergebene Gebiets Schema anstelle des aktuellen Gebiets Schemas für Ihr vom Gebiets Schema abhängiges Verhalten. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

|Routine|Testbedingung|Beispiel für Codepage 932|
|-------------|--------------------|---------------------------|
|**_ismbclegal**|Gültiges Multibyte|Gibt nur dann einen Wert ungleich 0 (null) zurück, wenn das erste Byte von *c* innerhalb der Bereiche 0x81-0x9F oder 0xE0-0xFC liegt, während das zweite Byte im Bereich 0x40-0x7E oder 0x80-FC liegt.|
|**_ismbcsymbol**|Multibytesymbol|Gibt nur dann einen Wert ungleich 0 (null) zurück, wenn 0x8141<=*c*<= 0x81ac.|

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istlegal**|Gibt immer "false" zurück|**_ismbclegal**|Gibt immer false zurück.|
|**_istlegal_l**|Gibt immer "false" zurück|**_ismbclegal_l**|Gibt immer false zurück.|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_ismbclegal** **_ismbclegal_l**|\<mbstring.h>|
|**_ismbcsymbol** **_ismbcsymbol_l**|\<mbstring.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Zeichen Klassifizierung](../../c-runtime-library/character-classification.md)<br/>
[_ismbc-Routinen](../../c-runtime-library/ismbc-routines.md)<br/>
[is-, ISW-Routinen](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb Routinen](../../c-runtime-library/ismbb-routines.md)<br/>
