---
title: atoll, _atoll_l, _wtoll, _wtoll_l
ms.date: 4/2/2020
api_name:
- _wtoll
- _atoll_l
- _wtoll_l
- atoll
- _o__atoll_l
- _o__wtoll
- _o__wtoll_l
- _o_atoll
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
- _tstoll_l
- _wtoll
- _atoll_l
- _ttoll
- _tstoll
- _wtoll_l
- atoll
helpviewer_keywords:
- atoll function
- _wtoll_l function
- _wtoll function
- _atoll_l function
ms.assetid: 5e85fcac-b351-4882-bff2-6e7c469b7fa8
ms.openlocfilehash: 89a4d94a98e58f4ef5489554e02866a8471ade20
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913521"
---
# <a name="atoll-_atoll_l-_wtoll-_wtoll_l"></a>atoll, _atoll_l, _wtoll, _wtoll_l

Konvertiert eine Zeichenfolge in eine **lange** **ganze Zahl** .

## <a name="syntax"></a>Syntax

```C
long long atoll(
   const char *str
);
long long _wtoll(
   const wchar_t *str
);
long long _atoll_l(
   const char *str,
   _locale_t locale
);
long long _wtoll_l(
   const wchar_t *str,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*SRT*<br/>
Zu konvertierende Zeichenfolge.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Jede Funktion gibt den **Long** **Long** -Wert zurück, der erzeugt wird, indem die Eingabezeichen als Zahl interpretiert werden. Der Rückgabewert für das **Atoll** ist 0, wenn die Eingabe nicht in einen Wert dieses Typs konvertiert werden kann.

Bei einem Überlauf mit großen positiven ganzzahligen Werten gibt das **Atoll** **LLONG_MAX**zurück, und bei einem Überlauf mit großen negativen ganzzahligen Werten wird **LLONG_MIN**zurückgegeben.

In allen Fällen außerhalb des gültigen Bereichs wird **errno** auf **ERANGE**festgelegt. Wenn der übergebenen Parameter **null**ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, legen diese Funktionen **errno** auf **EINVAL** fest und geben 0 zurück.

## <a name="remarks"></a>Hinweise

Diese Funktionen konvertieren eine Zeichenfolge in einen **langen** **langen** ganzzahligen Wert.

Die Eingabezeichenfolge ist eine Sequenz von Zeichen, die als numerischer Wert des angegebenen Typs interpretiert werden. Die Funktion beendet das Lesen der Eingabezeichenfolge am ersten Zeichen, das nicht als Teil einer Zahl erkannt wird. Dieses Zeichen kann das NULL-Zeichen ('\0' or L'\0') sein, das die Zeichenfolge beendet.

Das *Str* -Argument für das **Atoll** weist die folgende Form auf:

> [*Leerzeichen*] [*Sign*] [*Ziffern*]

Ein *Leerraum* besteht aus Leerzeichen oder Tabulator Zeichen, die ignoriert werden. das Vorzeichen ist entweder Pluszeichen (+) oder minus *Zeichen* (-); und *Ziffern* sind eine oder mehrere Ziffern.

**_wtoll** ist mit dem **Atoll** identisch, außer dass es eine Zeichenfolge mit breit Zeichen als Parameter annimmt.

Die Versionen dieser Funktionen mit dem **_l** -Suffix sind identisch mit den Versionen, die Sie nicht haben, mit dem Unterschied, dass Sie den Gebiets Schema Parameter verwenden, der anstelle des aktuellen Gebiets Schemas übergeben wurde. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tstoll**|**atoll**|**atoll**|**_wtoll**|
|**_tstoll_l**|**_atoll_l**|**_atoll_l**|**_wtoll_l**|
|**_ttoll**|**_atoll**|**_atoll**|**_wtoll**|

## <a name="requirements"></a>Anforderungen

|Routinen|Erforderlicher Header|
|--------------|---------------------|
|**Atoll**, **_atoll_l**|\<stdlib.h>|
|**_wtoll** **_wtoll_l**|\<stdlib.h> oder \<wchar.h>|

## <a name="example"></a>Beispiel

Dieses Programm zeigt, wie die **Atoll** -Funktionen verwendet werden, um als Zeichen folgen gespeicherte Zahlen in numerische Werte zu konvertieren.

```C
// crt_atoll.c
// Build with: cl /W4 /Tc crt_atoll.c
// This program shows how to use the atoll
// functions to convert numbers stored as
// strings to numeric values.
#include <stdlib.h>
#include <stdio.h>
#include <errno.h>

int main(void)
{
    char *str = NULL;
    long long value = 0;

    // An example of the atoll function
    // with leading and trailing white spaces.
    str = "  -27182818284 ";
    value = atoll(str);
    printf("Function: atoll(\"%s\") = %lld\n", str, value);

    // Another example of the atoll function
    // with an arbitrary decimal point.
    str = "314127.64";
    value = atoll(str);
    printf("Function: atoll(\"%s\") = %lld\n", str, value);

    // Another example of the atoll function
    // with an overflow condition occurring.
    str = "3336402735171707160320";
    value = atoll(str);
    printf("Function: atoll(\"%s\") = %lld\n", str, value);
    if (errno == ERANGE)
    {
       printf("Overflow condition occurred.\n");
    }
}
```

```Output
Function: atoll("  -27182818284 ") = -27182818284
Function: atoll("314127.64") = 314127
Function: atoll("3336402735171707160320") = 9223372036854775807
Overflow condition occurred.
```

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)<br/>
