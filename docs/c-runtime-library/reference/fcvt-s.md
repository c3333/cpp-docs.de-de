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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 80f02467e160e3196982c10576ad55f5487e5fc1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347447"
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

*Puffer*<br/>
Der angegebene Puffer, der das Ergebnis der Konvertierung enthält.

*sizeInBytes*<br/>
Die Größe des Puffers in Byte.

*value*<br/>
Zu konvertierende Zahl.

*count*<br/>
Anzahl der Ziffern nach dem Dezimaltrennzeichen.

*dec*<br/>
Zeiger auf die gespeicherte Position der Dezimalstelle.

*Zeichen*<br/>
Zeiger auf den gespeicherten Zeichen-Indikator.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich. Der Rückgabewert ist ein Fehlercode, wenn ein Fehler auftritt. Fehlercodes sind in Errno.h definiert. Eine Liste dieser Fehler finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Bei einem in der folgenden Tabelle enthaltenen ungültigen Parameter wird von dieser Funktion der Handler für ungültige Parameter aufgerufen, wie unter [Parameter Validation (Parameterüberprüfung)](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die Ausführung fortgesetzt werden darf, setzt diese Funktion **errno** auf **EINVAL** und gibt **EINVAL**zurück.

### <a name="error-conditions"></a>Fehlerbedingungen

|*Puffer*|*sizeInBytes*|value|count|dec|Signieren|Rückgabewert|Wert im *Puffer*|
|--------------|-------------------|-----------|-----------|---------|----------|------------|-----------------------|
|**Null**|any|any|any|any|any|**Einval**|Nicht geändert.|
|Nicht **NULL** (zeigt auf gültigen Speicher)|<=0|any|any|any|any|**Einval**|Nicht geändert.|
|any|any|any|any|**Null**|any|**Einval**|Nicht geändert.|
|any|any|any|any|any|**Null**|**Einval**|Nicht geändert.|

## <a name="security-issues"></a>Sicherheitsprobleme

**_fcvt_s** eine Zugriffsverletzung generieren, wenn *der Puffer* nicht auf gültigen Speicher hinweist und nicht **NULL**ist.

## <a name="remarks"></a>Bemerkungen

Die **_fcvt_s-Funktion** konvertiert eine Gleitkommazahl in eine null-terminierte Zeichenfolge. Der *Wertparameter* ist die zu konvertierende Gleitkommazahl. **_fcvt_s** speichert die *Werteziffern* als Zeichenfolge und fügt ein Nullzeichen an . Der *Parameter count* gibt die Anzahl der Ziffern an, die nach dem Dezimaltrennzeichen gespeichert werden sollen. Überschüssige Ziffern werden abgerundet, um Orte zu *zählen.* Wenn es weniger als *Genauigkeitsziffern* zählen, wird die Zeichenfolge mit Nullen aufgepolstert.

In der Zeichenfolge werden nur Ziffern gespeichert. Die Position des Dezimalkommas und das Vorzeichen des *Wertes* können von *dec* und *Zeichen* nach dem Aufruf erhalten werden. Der *Parameter dec* zeigt auf einen Ganzzahlwert; Dieser ganzzahlige Wert gibt die Position des Dezimalkommas in Bezug auf den Anfang der Zeichenfolge an. Der Wert null oder ein negativer ganzzahliger Wert geben an, dass sich die Dezimalstelle links neben der ersten Ziffer befindet. Das *Parameterzeichen* zeigt auf eine ganze Zahl, die das Vorzeichen des *Werts*angibt. Die ganze Zahl wird auf 0 gesetzt, wenn *der Wert* positiv ist, und wird auf eine Zahl ungleich Null gesetzt, wenn *der Wert* negativ ist.

Ein Puffer mit länge **_CVTBUFSIZE** ist für jeden Gleitkommawert ausreichend.

Der Unterschied zwischen **_ecvt_s** und **_fcvt_s** liegt in der Interpretation des *Zählparameters.* **_ecvt_s** *interpretiert, zählen* als die Gesamtzahl der Ziffern in der Ausgabezeichenfolge, und **_fcvt_s** *interpretiert, zählen* als die Anzahl der Ziffern nach dem Dezimaltrennzeichen.

Die Verwendung dieser Funktion in C++ wird durch eine Überladung (als Vorlagen vorhanden) vereinfacht. Eine Überladung kann automatisch die Pufferlänge ableiten, sodass kein Größenargument angegeben werden muss. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Die Debugversion dieser Funktion füllt zunächst den Puffer mit 0xFE. Um dieses Verhalten zu deaktivieren, verwenden Sie [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

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

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
[_fcvt](fcvt.md)<br/>
