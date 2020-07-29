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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 1d2202bd1ca59ee42287c398da429df132e24fcb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234080"
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

*scher*<br/>
Zu testende ganze Zahl.

## <a name="return-value"></a>Rückgabewert

**isleadbyte** gibt einen Wert ungleich 0 (null) zurück, wenn das Argument die Test Bedingung erfüllt, oder 0, wenn dies nicht der Fall ist. Im Gebiets Schema "C" und in Einzel Byte-Zeichensatz (SBCS)-Gebiets Schemas gibt **isleadbyte** immer 0 (null) zurück.

## <a name="remarks"></a>Bemerkungen

Das **isleadbyte** -Makro gibt einen Wert ungleich 0 (null) zurück, wenn das Argument das erste Byte eines multibytezeichens ist. **isleadbyte** erzeugt ein sinnvolles Ergebnis für ein beliebiges ganzzahliges Argument von-1 (**EOF**) bis **UCHAR_MAX** (0xFF), einschließlich.

Der erwartete Argumenttyp von **isleadbyte** ist **`int`** . Wenn ein signiertes Zeichen übergeben wird, kann der Compiler ihn durch Vorzeichen Erweiterung in eine ganze Zahl konvertieren, was zu unvorhersehbaren Ergebnissen führt.

Die Version dieser Funktion mit dem **_l** -Suffix ist beinahe identisch, verwendet jedoch das übergebene Gebiets Schema anstelle des aktuellen Gebiets Schemas für Ihr vom Gebiets Schema abhängiges Verhalten.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istleadbyte**|Gibt immer "false" zurück|**_isleadbyte**|Gibt immer "false" zurück|

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**isleadbyte**|\<ctype.h>|
|**_isleadbyte_l**|\<ctype.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Byte Klassifizierung](../../c-runtime-library/byte-classification.md)<br/>
[Gebietsschema](../../c-runtime-library/locale.md)<br/>
[_ismbb Routinen](../../c-runtime-library/ismbb-routines.md)<br/>
