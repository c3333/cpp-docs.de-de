---
title: _gcvt_s
ms.date: 4/2/2020
api_name:
- _gcvt_s
- _o__gcvt_s
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
- _gcvt_s
- gcvt_s
helpviewer_keywords:
- _gcvt_s function
- _CVTBUFSIZE
- floating-point functions, converting number to string
- gcvt_s function
- numbers, converting to strings
- conversions, floating point to strings
- strings [C++], converting from floating point
- CVTBUFSIZE
ms.assetid: 0a8d8a26-5940-4ae3-835e-0aa6ec1b0744
ms.openlocfilehash: 83e34bffbe62bf07d2d3f9f649d12607b0e08be7
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919425"
---
# <a name="_gcvt_s"></a>_gcvt_s

Konvertiert einen Gleitkommawert in eine Zeichenfolge. Dies ist eine sicherere Version von [_gcvt](gcvt.md), wie in [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben wird.

## <a name="syntax"></a>Syntax

```C
errno_t _gcvt_s(
   char *buffer,
   size_t sizeInBytes,
   double value,
   int digits
);
template <size_t cchStr>
errno_t _gcvt_s(
   char (&buffer)[cchStr],
   double value,
   int digits
); // C++ only
```

### <a name="parameters"></a>Parameter

*ert*<br/>
Puffer, um das Ergebnis der Konvertierung zu speichern

*sizeInBytes*<br/>
Größe des Puffers.

*value*<br/>
Zu konvertierender Wert.

*Zahlen*<br/>
Anzahl der gespeicherten signifikanten Ziffern.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich. Tritt ein Fehler aufgrund eines ungültigen Parameters auf (siehe folgende Tabelle für ungültige Werte), wird der ungültige Parameterhandler aufgerufen, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben wird. Wenn die weitere Ausführung zugelassen wird, wird ein Fehlercode zurückgegeben. Fehlercodes sind in Errno.h definiert. Eine Liste dieser Fehler finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Fehlerbedingungen

|*ert*|*sizeInBytes*|*value*|*Zahlen*|Rückgabewert|Wert im *Puffer*|
|--------------|-------------------|-------------|--------------|------------|-----------------------|
|**Normal**|any|any|any|**Eingabe**|Nicht geändert.|
|Not **null** (zeigt auf gültigen Speicher)|Null|any|any|**Eingabe**|Nicht geändert.|
|Not **null** (zeigt auf gültigen Speicher)|any|any|>= *sizeInBytes*|**Eingabe**|Nicht geändert.|

**Sicherheitsprobleme**

**_gcvt_s** kann eine Zugriffsverletzung generieren, wenn der *Puffer* nicht auf einen gültigen Speicher verweist und nicht **null**ist.

## <a name="remarks"></a>Hinweise

Die **_gcvt_s** -Funktion konvertiert einen Gleit Komma *Wert* in eine Zeichenfolge (mit einem Dezimaltrennzeichen und einem möglichen Byte) und speichert die Zeichenfolge im *Puffer*. der *Puffer* sollte groß genug sein, um den konvertierten Wert und ein abschließendes NULL-Zeichen zu berücksichtigen, das automatisch angefügt wird. Ein Puffer der Länge **_CVTBUFSIZE** ist für alle Gleit Komma Werte ausreichend. Wenn eine Puffergröße von *Ziffern* + 1 verwendet wird, überschreibt die Funktion das Ende des Puffers nicht. Stellen Sie daher sicher, dass Sie für diesen Vorgang einen ausreichenden Puffer angeben. **_gcvt_s** versucht, *Ziffern* Ziffern im Dezimal Format zu liefern. Wenn dies nicht möglich ist, werden *Ziffern* Ziffern im exponentiellen Format erzeugt. Bei der Konvertierung können Nachstellen von Nullen unterdrückt werden.

Die Verwendung dieser Funktion in C++ wird durch eine Überladung (als Vorlagen vorhanden) vereinfacht. Eine Überladung kann automatisch die Pufferlänge ableiten, sodass kein Größenargument angegeben werden muss. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Die Debugversion dieser Funktion füllt den Puffer zuerst mit "0xFE" auf. Um dieses Verhalten zu deaktivieren, verwenden Sie [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|**_gcvt_s**|\<stdlib.h>|\<error.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_gcvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main()
{
    char buf[_CVTBUFSIZE];
    int decimal;
    int sign;
    int err;

    err = _gcvt_s(buf, _CVTBUFSIZE, 1.2, 5);

    if (err != 0)
    {
        printf("_gcvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 1.2
```

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt](gcvt.md)<br/>
