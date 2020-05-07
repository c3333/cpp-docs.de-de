---
title: _get_tzname
ms.date: 4/2/2020
api_name:
- _get_tzname
- _o__get_tzname
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_tzname
- get_tzname
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
ms.openlocfilehash: bf63b0ade0adc0a2dfa471bbfbeebc0cb2d04911
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919685"
---
# <a name="_get_tzname"></a>_get_tzname

Ruft die Darstellung der Zeichenfolge vom Namen der Zeitzone oder den Name der Standard-Sommerzeitzone (DST) ab.

## <a name="syntax"></a>Syntax

```C
errno_t _get_tzname(
    size_t* pReturnValue,
    char* timeZoneName,
    size_t sizeInBytes,
    int index
);
```

### <a name="parameters"></a>Parameter

*pReturnValue*<br/>
Die Zeichen folgen Länge von *timeZoneName* einschließlich eines NULL-Terminator.

*timeZoneName*<br/>
Die Adresse einer Zeichenfolge für die Darstellung des Zeit Zonen namens oder des standardmäßigen Sommerzeit Zonen namens (DST), abhängig vom *Index*.

*sizeInBytes*<br/>
Die Größe der *timeZoneName* -Zeichenfolge in Bytes.

*index*<br/>
Der Index eines der zwei abzurufenden Zeitzonen.

|*index*|Inhalt von *timeZoneName*|*timeZoneName* (Standardwert)|
|-|-|-|
|0|Name der Zeitzone|„PST“|
|1|Name der Standard-Sommerzeitzone|„PDT“|
|> 1 oder < 0|**errno** ist auf **EINVAL** festgelegt.|nicht geändert|

Werden die Werte nicht ausdrücklich während der Laufzeit geändert, sind die Standardwerte „PST“ und „PDT“.

## <a name="return-value"></a>Rückgabewert

NULL, wenn erfolgreich, andernfalls ein **errno** -Typwert.

Wenn *timeZoneName* **NULL ist, oder**Wenn *sizeInBytes* gleich 0 (null) oder kleiner als NULL (aber nicht beides) ist, wird ein ungültiger Parameter Handler aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, legt diese Funktion " **errno** " auf " **EINVAL** " fest und gibt " **EINVAL**" zurück.

### <a name="error-conditions"></a>Fehlerbedingungen

|*pReturnValue*|*timeZoneName*|*sizeInBytes*|*index*|Rückgabewert|Inhalt von *timeZoneName*|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|Größe des ZZ-Namens|**Normal**|0|0 oder 1|0|nicht geändert|
|Größe des ZZ-Namens|any|> 0|0 oder 1|0|ZZ-Name|
|nicht geändert|**Normal**|> 0|any|**Eingabe**|nicht geändert|
|nicht geändert|any|Null|any|**Eingabe**|nicht geändert|
|nicht geändert|any|> 0|> 1|**Eingabe**|nicht geändert|

## <a name="remarks"></a>Hinweise

Die **_get_tzname** -Funktion Ruft die Zeichen folgen Darstellung des aktuellen Zeit Zonen namens oder des standardmäßigen Sommerzeit Zonen namens (DST) in der Adresse von *timeZoneName* in Abhängigkeit vom Indexwert zusammen mit der Größe der Zeichenfolge in *pReturnValue*ab. Wenn *timeZoneName* **null** und *sizeInBytes* 0 (null) ist, wird die Größe der Zeichenfolge, die zum Speichern der angegebenen Zeitzone erforderlich ist, und das abschließende Null-Zeichen in Bytes in " *pReturnValue*" zurückgegeben. Die Indexwerte müssen für die Standard Zeitzone entweder 0 oder für die Sommer Zeitzone 1 lauten. alle anderen *Index* Werte weisen nicht ermittelte Ergebnisse auf.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="example"></a>Beispiel

In diesem Beispiel wird **_get_tzname** aufgerufen, um die erforderliche Puffergröße zum Anzeigen des aktuellen Zeit Zonen namens der Sommerzeit zu erhalten, einen Puffer dieser Größe zuzuweisen, **_get_tzname** erneut aufzurufen, um den Namen in den Puffer zu laden und ihn in der Konsole zu drucken.

```C
// crt_get_tzname.c
// Compile by using: cl /W4 crt_get_tzname.c
#include <stdio.h>
#include <time.h>
#include <malloc.h>

enum TZINDEX {
    STD,
    DST
};

int main()
{
    size_t tznameSize = 0;
    char * tznameBuffer = NULL;

    // Get the size of buffer required to hold DST time zone name
    if (_get_tzname(&tznameSize, NULL, 0, DST))
        return 1;    // Return an error value if it failed

    // Allocate a buffer for the name
    if (NULL == (tznameBuffer = (char *)(malloc(tznameSize))))
        return 2;    // Return an error value if it failed

    // Load the name in the buffer
    if (_get_tzname(&tznameSize, tznameBuffer, tznameSize, DST))
        return 3;    // Return an error value if it failed

    printf_s("The current Daylight standard time zone name is %s.\n", tznameBuffer);
    return 0;
}
```

### <a name="output"></a>Output

```Output
The current Daylight standard time zone name is PDT.
```

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_get_tzname**|\<time.h>|

Weitere Informationen finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Zeitmanagement](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
