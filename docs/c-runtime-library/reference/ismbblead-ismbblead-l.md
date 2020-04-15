---
title: _ismbblead, _ismbblead_l
description: Beschreibt die Microsoft C Runtime Library (CRT) _ismbblead und _ismbblead_l Funktionen.
ms.date: 4/2/2020
api_name:
- _ismbblead_l
- _ismbblead
- _o__ismbblead
- _o__ismbblead_l
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
- ismbblead_l
- istlead
- _ismbblead
- _ismbblead_l
- ismbblead
- _istlead
helpviewer_keywords:
- _ismbblead_l function
- ismbblead function
- _ismbblead function
- istlead function
- ismbblead_l function
- _istlead function
ms.assetid: 2abc6f75-ed5c-472e-bfd0-e905a1835ccf
ms.openlocfilehash: ee3085d49a27f2f3c97c6578463cf3a0598b73c7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343581"
---
# <a name="_ismbblead-_ismbblead_l"></a>_ismbblead, _ismbblead_l

Testet ein Zeichen, um festzustellen, ob es sich um ein Leadbyte eines Multibyte-Zeichens handelt.

## <a name="syntax"></a>Syntax

```C
int _ismbblead(
   unsigned int c
);
int _ismbblead_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*C*\
Die zu testende ganze Zahl.

*locale*\
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Gibt einen Wert ungleich Null zurück, wenn die ganze Zahl *c* das erste Byte eines Multibyte-Zeichens ist.

## <a name="remarks"></a>Bemerkungen

Multibytezeichen bestehen aus einem führenden Byte gefolgt von einem nachfolgendem Byte. Führende Bytes werden anhand ihrer Zugehörigkeit zu einem bestimmten Bereich für einen gegebenen Zeichensatz unterschieden. Beispielsweise reichen Leadbytes nur in Codepage 932 von 0x81 - 0x9F und 0xE0 - 0xFC.

**_ismbblead** verwendet das aktuelle Gebietsschema für gebietsschemaabhängiges Verhalten. **_ismbblead_l** identisch ist, außer dass es stattdessen das übergebene Gebietsschema verwendet. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Wenn das Gebietsschema UTF-8 ist, **geben _ismbblead** und **_ismbblead_l** immer 0 (false) zurück, unabhängig davon, ob *c* ein Leadbyte ist oder nicht.

**_ismbblead** und **_ismbblead_l** sind Microsoft-spezifisch und nicht Teil der Standard-C-Bibliothek. Wir empfehlen Ihnen nicht, sie dort zu verwenden, wo Sie portablen Code benötigen. Verwenden Sie für die Kompatibilität nach Standard C stattdessen **mbrlen.**

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Generische Sertägliche Routinezuordnungen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istlead**|Gibt immer "false" zurück|**_ismbblead**|Gibt immer "false" zurück|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|**_ismbblead**|\<mbctype.h> oder \<mbstring.h>|\<ctype.h>,* \<limits.h>, \<stdlib.h>|
|**_ismbblead_l**|\<mbctype.h> oder \<mbstring.h>|\<ctype.h>,* \<limits.h>, \<stdlib.h>|

\* Für Manifestkonstanten für die Testbedingungen.

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Byte-Klassifizierung](../../c-runtime-library/byte-classification.md)\
[_ismbb Routinen](../../c-runtime-library/ismbb-routines.md)\
[mbrlen](mbrlen.md)
