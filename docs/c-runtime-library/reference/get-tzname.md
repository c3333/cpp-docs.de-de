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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 50f1f6e4320e3ef905b4eda67ba1d458a5b1df08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344872"
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

*Preturnvalue*<br/>
Die Zeichenfolgenlänge von *timeZoneName* einschließlich eines Nullabschlusses.

*Timezonename*<br/>
Die Adresse einer Zeichenfolge für die Darstellung des Zeitzonennamens oder des Sommerstandardzeitzonennamens (DST), abhängig vom *Index*.

*sizeInBytes*<br/>
Die Größe der *timeZoneName-Zeichenfolge* in Bytes.

*Index*<br/>
Der Index eines der zwei abzurufenden Zeitzonen.

|*Index*|Inhalt von *timeZoneName*|*timeZoneName-Standardwert*|
|-|-|-|
|0|Name der Zeitzone|„PST“|
|1|Name der Standard-Sommerzeitzone|„PDT“|
|> 1 oder < 0|**errno** auf **EINVAL** gesetzt|nicht geändert|

Werden die Werte nicht ausdrücklich während der Laufzeit geändert, sind die Standardwerte „PST“ und „PDT“.

## <a name="return-value"></a>Rückgabewert

Null bei Erfolg, andernfalls ein **Errno-Typwert.**

Wenn *timeZoneName* **NULL**oder *sizeInBytes* Null oder kleiner als Null (aber nicht beides) ist, wird ein ungültiger Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, setzt diese Funktion **errno** auf **EINVAL** und gibt **EINVAL**zurück.

### <a name="error-conditions"></a>Fehlerbedingungen

|*Preturnvalue*|*Timezonename*|*sizeInBytes*|*Index*|Rückgabewert|Inhalt von *timeZoneName*|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|Größe des ZZ-Namens|**Null**|0|0 oder 1|0|nicht geändert|
|Größe des ZZ-Namens|any|> 0|0 oder 1|0|ZZ-Name|
|nicht geändert|**Null**|> 0|any|**Einval**|nicht geändert|
|nicht geändert|any|Null|any|**Einval**|nicht geändert|
|nicht geändert|any|> 0|> 1|**Einval**|nicht geändert|

## <a name="remarks"></a>Bemerkungen

Die **_get_tzname-Funktion** ruft die Zeichenfolgendarstellung des aktuellen Zeitzonennamens oder des Sommerstandardzeitzonennamens (DST) in die Adresse von *timeZoneName* in Abhängigkeit vom Indexwert zusammen mit der Größe der Zeichenfolge in *pReturnValue*ab. Wenn *timeZoneName* **NULL** und *sizeInBytes* Null ist, wird die Größe der Zeichenfolge, die für die angegebene Zeitzone erforderlich ist, und ein beendender Nullwert in Bytes in *pReturnValue*zurückgegeben. Die Indexwerte müssen entweder 0 für die Standardzeitzone oder 1 für die Sommerzeitzone sein. alle anderen *Indexwerte* haben unbestimmte Ergebnisse.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="example"></a>Beispiel

In diesem Beispiel **wird _get_tzname** auf, um die erforderliche Puffergröße zum Anzeigen des aktuellen Sommerzeitzonennamens zu erhalten, einen Puffer dieser Größe zuzuweisen, **_get_tzname** erneut auf, um den Namen in den Puffer zu laden, und es in die Konsole druckt.

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

## <a name="see-also"></a>Siehe auch

[Zeitmanagement](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
