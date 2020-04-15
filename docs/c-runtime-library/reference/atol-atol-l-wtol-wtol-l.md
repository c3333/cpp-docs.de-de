---
title: atol, _atol_l, _wtol, _wtol_l
ms.date: 4/2/2020
api_name:
- atol
- _wtol_l
- _wtol
- _atol_l
- _o__atol_l
- _o__wtol
- _o__wtol_l
- _o_atol
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
- _atol_l
- _ttol_l
- _tstol_l
- _tstol
- _wtol
- _ttol
- _wtol_l
helpviewer_keywords:
- tstol function
- atol function
- ttol function
- _atol_l function
- _tstol_l function
- string conversion, to integers
- _tstol function
- _ttol function
- _ttol_l function
- atol_l function
- wtol_l function
- _wtol_l function
- wtol function
- _wtol function
ms.assetid: cedfc21c-2d64-4e9c-bd04-bdf60b12db46
ms.openlocfilehash: 30f8375814259cac8c3d7216c636b69acbc7e90a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348755"
---
# <a name="atol-_atol_l-_wtol-_wtol_l"></a>atol, _atol_l, _wtol, _wtol_l

Konvertiert eine Zeichenfolge in eine lange ganze Zahl.

## <a name="syntax"></a>Syntax

```C
long atol(
   const char *str
);
long _atol_l(
   const char *str,
   _locale_t locale
);
long _wtol(
   const wchar_t *str
);
long _wtol_l(
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

Jede Funktion gibt den **langen** Wert zurück, der erzeugt wird, indem die Eingabezeichen als Zahl interpretiert werden. Der Rückgabewert ist 0L für **atol,** wenn die Eingabe nicht in einen Wert dieses Typs konvertiert werden kann.

Bei Überlauf mit großen positiven Integralwerten gibt **atol** **LONG_MAX**zurück; bei Überlauf mit großen negativen Integralwerten **wird LONG_MIN** zurückgegeben. In allen Fällen a-of-range wird **errno** auf **ERANGE**gesetzt. Wenn der übergebene Parameter **NULL**ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, setzen diese Funktionen **errno** auf **EINVAL** und geben 0 zurück.

## <a name="remarks"></a>Bemerkungen

Diese Funktionen konvertieren eine Zeichenfolge in einen Long Integer-Wert (**atol**).

Die Eingabezeichenfolge ist eine Sequenz von Zeichen, die als numerischer Wert des angegebenen Typs interpretiert werden. Die Funktion beendet das Lesen der Eingabezeichenfolge am ersten Zeichen, das nicht als Teil einer Zahl erkannt wird. Möglicherweise ist dies das Zeichen NULL ('\0' oder L'\0'), das am Ende der Zeichenfolge steht.

Das *argument* zu **atol** hat die folgende Form:

> [*Leerzeichen*] [*Zeichen*] [*Ziffern*]]

Ein *Leerzeichen* besteht aus Leerzeichen oder Registerkartenzeichen, die ignoriert werden. *Zeichen* ist entweder plus (+) oder minus (-); und *Ziffern* sind eine oder mehrere Ziffern.

**_wtol** ist identisch mit **atol,** außer dass es eine breite Zeichenkette benötigt.

Die Versionen dieser Funktionen mit dem **Suffix _l** sind identisch, außer dass sie den übergebenen Gebietsschemaparameter anstelle des aktuellen Gebietsschemas verwenden. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstol**|**atol**|**atol**|**_wtol**|
|**_ttol**|**atol**|**atol**|**_wtol**|

## <a name="requirements"></a>Anforderungen

|Routinen|Erforderlicher Header|
|--------------|---------------------|
|**atol**|\<stdlib.h>|
|**_atol_l**, **_wtol**, **_wtol_l**|\<stdlib.h> und \<wchar.h>|

## <a name="example"></a>Beispiel

Dieses Programm zeigt, wie als Zeichenfolgen gespeicherte Zahlen mit der **atol-Funktion** in numerische Werte konvertiert werden können.

```C
// crt_atol.c
// This program shows how numbers stored as
// strings can be converted to numeric values
// using the atol functions.
#include <stdlib.h>
#include <stdio.h>
#include <errno.h>

int main( void )
{
    char    *str = NULL;
    long    value = 0;

    // An example of the atol function
    // with leading and trailing white spaces.
    str = "  -2309 ";
    value = atol( str );
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );

    // Another example of the atol function
    // with an arbitrary decimal point.
    str = "314127.64";
    value = atol( str );
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );

    // Another example of the atol function
    // with an overflow condition occurring.
    str = "3336402735171707160320";
    value = atol( str );
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );
    if (errno == ERANGE)
    {
       printf("Overflow condition occurred.\n");
    }
}
```

```Output
Function: atol( "  -2309 " ) = -2309
Function: atol( "314127.64" ) = 314127
Function: atol( "3336402735171707160320" ) = 2147483647
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
