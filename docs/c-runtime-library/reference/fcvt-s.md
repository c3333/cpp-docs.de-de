---
title: _fcvt_s
ms.date: 4/2/2020
api_name:
- _fcvt_s
- _o__fcvt_s
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
- fcvt_s
- _fcvt_s
helpviewer_keywords:
- fcvt_s function
- converting floating point, to strings
- floating-point functions, converting number to string
- _fcvt_s function
ms.assetid: 48671197-1d29-4c2b-a5d8-d2368f5f68a1
ms.openlocfilehash: 557a1d359c389f0eb7477aab4bf9cbb51558703a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920202"
---
# <a name="_fcvt_s"></a>_fcvt_s

Konvertiert eine Gleitkommazahl in eine Zeichenfolge. Dies ist eine sicherere Version von [_fcvt](fcvt.md), wie in [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t _fcvt_s(
   char* buffer,
   size_t sizeInBytes,
   double value,
   int count,
   int *dec,
   int *sign
);
template <size_t size>
errno_t _fcvt_s(
   char (&buffer)[size],
   double value,
   int count,
   int *dec,
   int *sign
); // C++ only
```

### <a name="parameters"></a>Parameter

*ert*<br/>
Der angegebene Puffer, der das Ergebnis der Konvertierung enthält.

*sizeInBytes*<br/>
Die Größe des Puffers in Byte.

*value*<br/>
Zu konvertierende Zahl.

*count*<br/>
Anzahl der Ziffern nach dem Dezimaltrennzeichen.

*31.12.2012*<br/>
Zeiger auf die gespeicherte Position der Dezimalstelle.

*Gebärden*<br/>
Zeiger auf den gespeicherten Zeichen-Indikator.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich. Der Rückgabewert ist ein Fehlercode, wenn ein Fehler auftritt. Fehlercodes sind in Errno.h definiert. Eine Liste dieser Fehler finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Bei einem in der folgenden Tabelle enthaltenen ungültigen Parameter wird von dieser Funktion der Handler für ungültige Parameter aufgerufen, wie unter [Parameter Validation (Parameterüberprüfung)](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die weitere Ausführung zugelassen wird, legt diese Funktion " **errno** " auf " **EINVAL** " fest und gibt " **EINVAL**" zurück.

### <a name="error-conditions"></a>Fehlerbedingungen

|*ert*|*sizeInBytes*|value|count|dec|Signieren|Rückgabewert|Wert im *Puffer*|
|--------------|-------------------|-----------|-----------|---------|----------|------------|-----------------------|
|**Normal**|any|any|any|any|any|**Eingabe**|Nicht geändert.|
|Not **null** (zeigt auf gültigen Speicher)|<=0|any|any|any|any|**Eingabe**|Nicht geändert.|
|any|any|any|any|**Normal**|any|**Eingabe**|Nicht geändert.|
|any|any|any|any|any|**Normal**|**Eingabe**|Nicht geändert.|

## <a name="security-issues"></a>Sicherheitsprobleme

**_fcvt_s** generiert möglicherweise eine Zugriffsverletzung, wenn der *Puffer* nicht auf einen gültigen Speicher verweist und nicht **null**ist.

## <a name="remarks"></a>Hinweise

Die **_fcvt_s** -Funktion konvertiert eine Gleit Komma Zahl in eine NULL terminierte Zeichenfolge. Der *value* -Parameter ist die zu konvertierende Gleit Komma Zahl. **_fcvt_s** speichert die Ziffern des *Werts* als Zeichenfolge und fügt ein NULL-Zeichen (' \ 0 ') an. Der *count* -Parameter gibt die Anzahl der Ziffern an, die nach dem Dezimaltrennzeichen gespeichert werden sollen. Überschüssige Ziffern werden auf *Anzahl* von Stellen gerundet. Wenn weniger als *zählungs* Ziffern vorhanden sind, wird die Zeichenfolge mit Nullen aufgefüllt.

In der Zeichenfolge werden nur Ziffern gespeichert. Die Position des Dezimal Trennzeichens und das Vorzeichen des *Werts* können aus *Dec* abgerufen und nach dem-Befehl *signiert* werden. Der *Dec* -Parameter verweist auf einen ganzzahligen Wert. dieser ganzzahlige Wert gibt die Position des Dezimal Trennzeichens in Bezug auf den Anfang der Zeichenfolge an. Der Wert null oder ein negativer ganzzahliger Wert geben an, dass sich die Dezimalstelle links neben der ersten Ziffer befindet. Das Parameter *Vorzeichen* verweist auf eine Ganzzahl, die das Vorzeichen des *Werts*angibt. Die Ganzzahl wird auf 0 festgelegt, wenn *value* positiv ist und auf eine Zahl ungleich 0 (null) festgelegt ist, wenn der *Wert* negativ ist.

Ein Puffer der Länge **_CVTBUFSIZE** ist für alle Gleit Komma Werte ausreichend.

Der Unterschied zwischen **_ecvt_s** und **_fcvt_s** ist die Interpretation des *count* -Parameters. **_ecvt_s** interpretiert *count* als die Gesamtanzahl der Ziffern in der Ausgabe Zeichenfolge, und **_fcvt_s** interpretiert *count* als die Anzahl der Ziffern nach dem Dezimaltrennzeichen.

Die Verwendung dieser Funktion in C++ wird durch eine Überladung (als Vorlagen vorhanden) vereinfacht. Eine Überladung kann automatisch die Pufferlänge ableiten, sodass kein Größenargument angegeben werden muss. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Die Debugversion dieser Funktion füllt den Puffer zuerst mit "0xFE" auf. Um dieses Verhalten zu deaktivieren, verwenden Sie [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|Optionaler Header|
|--------------|---------------------|---------------------|
|**_fcvt_s**|\<stdlib.h>|\<errno.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

**Bibliotheken:** Alle Versionen der [CRT-Bibliotheksfunktionen](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

```C
// fcvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main()
{
    char * buf = 0;
    int decimal;
    int sign;
    int err;

    buf = (char*) malloc(_CVTBUFSIZE);
    err = _fcvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);

    if (err != 0)
    {
        printf("_fcvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 120000
```

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
[_fcvt](fcvt.md)<br/>
