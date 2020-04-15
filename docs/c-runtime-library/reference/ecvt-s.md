---
title: _ecvt_s
ms.date: 4/2/2020
api_name:
- _ecvt_s
- _o__ecvt_s
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ecvt_s
- _ecvt_s
helpviewer_keywords:
- _ecvt_s function
- ecvt_s function
- numbers, converting
- converting double numbers
ms.assetid: d52fb0a6-cb91-423f-80b3-952a8955d914
ms.openlocfilehash: e33840e772de770e0f05ae45d2c2d4bec7e09939
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348044"
---
# <a name="_ecvt_s"></a>_ecvt_s

Konvertiert eine **doppelte** Zahl in eine Zeichenfolge. Dies ist eine sicherere Version von [_ecvt](ecvt.md), wie unter [Security Features in the CRT (Sicherheitsfunktionen in der CRT)](../../c-runtime-library/security-features-in-the-crt.md) beschrieben wird.

## <a name="syntax"></a>Syntax

```C
errno_t _ecvt_s(
   char * _Buffer,
   size_t _SizeInBytes,
   double _Value,
   int _Count,
   int *_Dec,
   int *_Sign
);
template <size_t size>
errno_t _ecvt_s(
   char (&_Buffer)[size],
   double _Value,
   int _Count,
   int *_Dec,
   int *_Sign
); // C++ only
```

### <a name="parameters"></a>Parameter

*_Buffer*<br/>
Wird mit dem Zeiger auf die Zeichenfolge mit Ziffern aufgefüllt, die sich aus der Konvertierung ergeben.

*_SizeInBytes*<br/>
Größe des Puffers in Byte.

*_value*<br/>
Zu konvertierende Zahl.

*_count*<br/>
Anzahl der gespeicherten Ziffern.

*_Dec*<br/>
Gespeicherte Position der Dezimalstelle.

*_Sign*<br/>
Vorzeichen der konvertierten Zahl.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich. Der Rückgabewert ist ein Fehlercode, wenn ein Fehler auftritt. Fehlercodes sind in Errno.h definiert. Weitere Informationen finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Bei einem in der folgenden Tabelle enthaltenen ungültigen Parameter wird von dieser Funktion der Handler für ungültige Parameter aufgerufen, wie unter [Parameter Validation (Parameterüberprüfung)](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die Ausführung fortgesetzt werden darf, setzt diese Funktion **errno** auf **EINVAL** und gibt **EINVAL**zurück.

### <a name="error-conditions"></a>Fehlerbedingungen

|*_Buffer*|*_SizeInBytes*|_Value|_Count|_Dec|_Sign|Rückgabewert|Wert im *Puffer*|
|---------------|--------------------|-------------|-------------|-----------|------------|------------------|-----------------------|
|**Null**|any|any|any|any|any|**Einval**|Nicht geändert.|
|Nicht **NULL** (zeigt auf gültigen Speicher)|<=0|any|any|any|any|**Einval**|Nicht geändert.|
|any|any|any|any|**Null**|any|**Einval**|Nicht geändert.|
|any|any|any|any|any|**Null**|**Einval**|Nicht geändert.|

## <a name="security-issues"></a>Sicherheitsprobleme

**_ecvt_s** eine Zugriffsverletzung generieren, wenn *der Puffer* nicht auf gültigen Speicher hinweist und nicht **NULL**ist.

## <a name="remarks"></a>Bemerkungen

Die **_ecvt_s-Funktion** konvertiert eine Gleitkommazahl in eine Zeichenfolge. Der *parameter _Value* ist die zu konvertierende Gleitkommazahl. Diese Funktion speichert bis zu *Ziffern* von *_Value* als Zeichenfolge und fügt ein Nullzeichen an . Wenn die Anzahl der Ziffern in *_Value* *_Count*überschreitet, wird die Ziffer niedriger Ordnung gerundet. Wenn weniger als *Zählziffern* vorhanden sind, wird die Zeichenfolge mit Nullen aufgepolstert.

In der Zeichenfolge werden nur Ziffern gespeichert. Die Position des Dezimalkommas und das Vorzeichen von *_Value* können von *_Dec* und *_Sign* nach dem Aufruf abgerufen werden. Der *parameter _Dec* zeigt auf einen Ganzzahlwert, der die Position des Dezimalkommas in Bezug auf den Anfang der Zeichenfolge angibt. Der Wert 0 oder ein negativer Integer-Wert geben an, dass sich die Dezimalstelle links neben der ersten Ziffer befindet. Der *_Sign* Parameter zeigt auf eine ganze Zahl, die das Vorzeichen der konvertierten Zahl angibt. Wenn der Integer-Wert 0 ist, ist die Zahl positiv. Andernfalls ist die Zahl negativ.

Ein Puffer mit länge **_CVTBUFSIZE** ist für jeden Gleitkommawert ausreichend.

Der Unterschied zwischen **_ecvt_s** und **_fcvt_s** liegt in der Interpretation des *_Count* Parameters. **_ecvt_s** interpretiert *_Count* als die Gesamtzahl der Ziffern in der Ausgabezeichenfolge, während **_fcvt_s** *_Count* als die Anzahl der Ziffern nach dem Dezimaltrennzeichen interpretiert.

Die Verwendung dieser Funktion in C++ wird durch eine Überladung (als Vorlagen vorhanden) vereinfacht. Eine Überladung kann automatisch die Pufferlänge ableiten, sodass kein Größenargument angegeben werden muss. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Die Debugversion dieser Funktion füllt zunächst den Puffer mit 0xFE. Um dieses Verhalten zu deaktivieren, verwenden Sie [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|Optionaler Header|
|--------------|---------------------|---------------------|
|**_ecvt_s**|\<stdlib.h>|\<errno.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// ecvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main( )
{
    char * buf = 0;
    int decimal;
    int sign;
    int err;

    buf = (char*) malloc(_CVTBUFSIZE);
    err = _ecvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);

    if (err != 0)
    {
        printf("_ecvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 12000
```

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
