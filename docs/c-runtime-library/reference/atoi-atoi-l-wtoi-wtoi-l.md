---
title: atoi, _atoi_l, _wtoi, _wtoi_l
ms.date: 4/2/2020
api_name:
- _wtoi
- _wtoi_l
- atoi
- _atoi_l
- _o__atoi_l
- _o__wtoi
- _o__wtoi_l
- _o_atoi
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tstoi
- _wtoi
- _ttoi
- atoi
- _atoi_l
- _wtoi_l
helpviewer_keywords:
- _atoi_l function
- ttoi function
- atoi_l function
- string conversion, to integers
- _wtoi function
- wtoi_l function
- tstoi function
- _ttoi function
- _tstoi function
- _wtoi_l function
- atoi function
- wtoi function
ms.assetid: ad7fda30-28ab-421f-aaad-ef0b8868663a
ms.openlocfilehash: ef65f8986cf02b6385cbce71e5e81fa690b38b2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348867"
---
# <a name="atoi-_atoi_l-_wtoi-_wtoi_l"></a>atoi, _atoi_l, _wtoi, _wtoi_l

Konvertieren einer Zeichenfolge in eine Ganzzahl.

## <a name="syntax"></a>Syntax

```C
int atoi(
   const char *str
);
int _wtoi(
   const wchar_t *str
);
int _atoi_l(
   const char *str,
   _locale_t locale
);
int _wtoi_l(
   const wchar_t *str,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*Str*<br/>
Zu konvertierende Zeichenfolge.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Jede Funktion gibt den **int-Wert zurück,** der erzeugt wird, indem die Eingabezeichen als Zahl interpretiert werden. Der Rückgabewert ist 0 für **atoi** und **_wtoi**, wenn die Eingabe nicht in einen Wert dieses Typs konvertiert werden kann.

Bei Überlauf mit großen negativen Integralwerten **wird LONG_MIN** zurückgegeben. **und** **_wtoi** **INT_MAX** und **INT_MIN** zu diesen Bedingungen zurückgeben. In allen Fällen a-of-range wird **errno** auf **ERANGE**gesetzt. Wenn der übergebene Parameter **NULL**ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, setzen diese Funktionen **errno** auf **EINVAL** und geben 0 zurück.

## <a name="remarks"></a>Bemerkungen

Diese Funktionen konvertieren eine Zeichenfolge in einen Ganzzahlwert (**atoi** und **_wtoi**). Die Eingabezeichenfolge ist eine Sequenz von Zeichen, die als numerischer Wert des angegebenen Typs interpretiert werden. Die Funktion beendet das Lesen der Eingabezeichenfolge am ersten Zeichen, das nicht als Teil einer Zahl erkannt wird. Möglicherweise ist dies das Zeichen NULL ('\0' oder L'\0'), das am Ende der Zeichenfolge steht.

Das *Argument str* zu **atoi** und **_wtoi** hat die folgende Form:

> [*Leerzeichen*] [*Zeichen*] [*Ziffern*]]

Ein *Leerzeichen* besteht aus Leerzeichen oder Registerkartenzeichen, die ignoriert werden. *Zeichen* ist entweder plus (+) oder minus (-); und *Ziffern* sind eine oder mehrere Ziffern.

Die Versionen dieser Funktionen mit dem **Suffix _l** sind identisch, außer dass sie den übergebenen Gebietsschemaparameter anstelle des aktuellen Gebietsschemas verwenden. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstoi**|**atoi**|**atoi**|**_wtoi**|
|**_ttoi**|**atoi**|**atoi**|**_wtoi**|

## <a name="requirements"></a>Anforderungen

|Routinen|Erforderlicher Header|
|--------------|---------------------|
|**atoi**|\<stdlib.h>|
|**_atoi_l**, **_wtoi**, **_wtoi_l**|\<stdlib.h> oder \<wchar.h>|

## <a name="example"></a>Beispiel

Dieses Programm zeigt, wie als Zeichenfolgen gespeicherte Zahlen mithilfe der **atoi-Funktionen** in numerische Werte konvertiert werden können.

```C
// crt_atoi.c
// This program shows how numbers
// stored as strings can be converted to
// numeric values using the atoi functions.

#include <stdlib.h>
#include <stdio.h>
#include <errno.h>

int main( void )
{
    char    *str = NULL;
    int     value = 0;

    // An example of the atoi function.
    str = "  -2309 ";
    value = atoi( str );
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );

    // Another example of the atoi function.
    str = "31412764";
    value = atoi( str );
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );

    // Another example of the atoi function
    // with an overflow condition occurring.
    str = "3336402735171707160320";
    value = atoi( str );
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );
    if (errno == ERANGE)
    {
       printf("Overflow condition occurred.\n");
    }
}
```

```Output
Function: atoi( "  -2309 " ) = -2309
Function: atoi( "31412764" ) = 31412764
Function: atoi( "3336402735171707160320" ) = 2147483647
Overflow condition occurred.
```

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)<br/>
