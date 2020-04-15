---
title: isleadbyte, _isleadbyte_l
ms.date: 4/2/2020
api_name:
- _isleadbyte_l
- isleadbyte
- _o__isleadbyte_l
- _o_isleadbyte
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _istleadbyte
- _isleadbyte_l
- isleadbyte
helpviewer_keywords:
- lead bytes
- _isleadbyte_l function
- _istleadbyte function
- istleadbyte function
- isleadbyte function
ms.assetid: 3b2bcf09-d82b-4803-9e80-59d04942802a
ms.openlocfilehash: dddf1d669f77805df8e00f506b6427603ac8fd9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343841"
---
# <a name="isleadbyte-_isleadbyte_l"></a>isleadbyte, _isleadbyte_l

Bestimmt, ob ein Zeichen das führende Byte eines Multibytezeichens ist.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
int isleadbyte( int c );
int _isleadbyte_l( int c );
```

### <a name="parameters"></a>Parameter

*C*<br/>
Zu testende ganze Zahl.

## <a name="return-value"></a>Rückgabewert

**isleadbyte** gibt einen Wert ungleich Null zurück, wenn das Argument die Testbedingung erfüllt, oder 0, wenn dies nicht der Fall ist. Im Gebietsschema "C" und in SBCS-Gebietsschemas (Single-Byte-Zeichensatz) gibt **isleadbyte** immer 0 zurück.

## <a name="remarks"></a>Bemerkungen

Das **isleadbyte-Makro** gibt einen Wert ungleich Null zurück, wenn sein Argument das erste Byte eines Multibyte-Zeichens ist. **isleadbyte** erzeugt ein aussagekräftiges Ergebnis für jedes ganzzahlige Argument von -1 (**EOF**) bis **UCHAR_MAX** (0xFF), einschließlich.

Der erwartete Argumenttyp von **isleadbyte** ist **int**; Wenn ein signiertes Zeichen übergeben wird, kann der Compiler es in eine ganzzahlige durch Vorzeichenerweiterung konvertieren, was zu unvorhersehbaren Ergebnissen führt.

Die Version dieser Funktion mit dem **Suffix _l** ist identisch, außer dass sie das übergebene Gebietsschema anstelle des aktuellen Gebietsschemas für sein gebietsschemaabhängiges Verhalten verwendet.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istleadbyte**|Gibt immer "false" zurück|**_isleadbyte**|Gibt immer "false" zurück|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**isleadbyte**|\<ctype.h>|
|**_isleadbyte_l**|\<ctype.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Byteklassifizierung](../../c-runtime-library/byte-classification.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[_ismbb Routinen](../../c-runtime-library/ismbb-routines.md)<br/>
