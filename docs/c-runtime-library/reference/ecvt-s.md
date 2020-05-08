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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 9ac623c6cb80c774184dcb005e6d1d631c498040
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915139"
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

*_Value*<br/>
Zu konvertierende Zahl.

*_Count*<br/>
Anzahl der gespeicherten Ziffern.

*_Dec*<br/>
Gespeicherte Position der Dezimalstelle.

*_Sign*<br/>
Vorzeichen der konvertierten Zahl.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich. Der Rückgabewert ist ein Fehlercode, wenn ein Fehler auftritt. Fehlercodes sind in Errno.h definiert. Weitere Informationen finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Bei einem in der folgenden Tabelle enthaltenen ungültigen Parameter wird von dieser Funktion der Handler für ungültige Parameter aufgerufen, wie unter [Parameter Validation (Parameterüberprüfung)](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die weitere Ausführung zugelassen wird, legt diese Funktion " **errno** " auf " **EINVAL** " fest und gibt " **EINVAL**" zurück.

### <a name="error-conditions"></a>Fehlerbedingungen

|*_Buffer*|*_SizeInBytes*|_Value|_Count|_Dec|_Sign|Rückgabewert|Wert im *Puffer*|
|---------------|--------------------|-------------|-------------|-----------|------------|------------------|-----------------------|
|**Normal**|any|any|any|any|any|**Eingabe**|Nicht geändert.|
|Not **null** (zeigt auf gültigen Speicher)|<=0|any|any|any|any|**Eingabe**|Nicht geändert.|
|any|any|any|any|**Normal**|any|**Eingabe**|Nicht geändert.|
|any|any|any|any|any|**Normal**|**Eingabe**|Nicht geändert.|

## <a name="security-issues"></a>Sicherheitsprobleme

**_ecvt_s** generiert möglicherweise eine Zugriffsverletzung, wenn der *Puffer* nicht auf einen gültigen Speicher verweist und nicht **null**ist.

## <a name="remarks"></a>Hinweise

Die **_ecvt_s** -Funktion konvertiert eine Gleit Komma Zahl in eine Zeichenfolge. Der *_Value* -Parameter ist die zu konvertierende Gleit Komma Zahl. Diese Funktion speichert bis zum *zählen* von Ziffern *_Value* als Zeichenfolge und fügt ein NULL-Zeichen (' \ 0 ') an. Wenn die Anzahl der Ziffern in *_Value* *_Count*überschreitet, wird die nieder wertige Ziffer gerundet. Wenn weniger als *Zähl* Ziffern vorhanden sind, wird die Zeichenfolge mit Nullen aufgefüllt.

In der Zeichenfolge werden nur Ziffern gespeichert. Die Position des Dezimal Trennzeichens und das Vorzeichen des *_Value* können von *_Dec* abgerufen und nach dem- *aufruf_Sign* werden. Der *_Dec* -Parameter verweist auf einen ganzzahligen Wert, der die Position des Dezimal Trennzeichens in Bezug auf den Anfang der Zeichenfolge gibt. Der Wert 0 oder ein negativer Integer-Wert geben an, dass sich die Dezimalstelle links neben der ersten Ziffer befindet. Der *_Sign* -Parameter verweist auf eine Ganzzahl, die das Vorzeichen der konvertierten Zahl angibt. Wenn der Integer-Wert 0 ist, ist die Zahl positiv. Andernfalls ist die Zahl negativ.

Ein Puffer mit einer Länge von **_CVTBUFSIZE** ist für alle Gleit Komma Werte ausreichend.

Der Unterschied zwischen **_ecvt_s** und **_fcvt_s** ist die Interpretation des *_Count* -Parameters. **_ecvt_s** interpretiert *_Count* als die Gesamtanzahl der Ziffern in der Ausgabe Zeichenfolge, während **_fcvt_s** *_Count* als die Anzahl der Ziffern nach dem Dezimaltrennzeichen interpretiert.

Die Verwendung dieser Funktion in C++ wird durch eine Überladung (als Vorlagen vorhanden) vereinfacht. Eine Überladung kann automatisch die Pufferlänge ableiten, sodass kein Größenargument angegeben werden muss. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Die Debugversion dieser Funktion füllt den Puffer zuerst mit "0xFE" auf. Um dieses Verhalten zu deaktivieren, verwenden Sie [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

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

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
