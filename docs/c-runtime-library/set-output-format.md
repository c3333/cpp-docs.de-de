---
title: _set_output_format
ms.date: 11/04/2016
api_name:
- _set_output_format
api_location:
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_output_format
- _set_output_format
helpviewer_keywords:
- _TWO_DIGIT_EXPONENT constant
- output formatting
- TWO_DIGIT_EXPONENT constant
- _set_output_format function
- set_output_format function
ms.assetid: 1cb48df8-44b4-4400-bd27-287831d6b3ff
ms.openlocfilehash: c855df4c29a53fd898b920f6446afe4e568ba5bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360921"
---
# <a name="_set_output_format"></a>_set_output_format

Passt die von den Funktionen für formatierte E/A verwendeten Ausgabeformate an.

> [!IMPORTANT]
> Diese Funktion ist veraltet. Von Visual Studio 2015 an ist sie nicht in der CRT verfügbar.

## <a name="syntax"></a>Syntax

```
unsigned int _set_output_format(
   unsigned int format
);
```

#### <a name="parameters"></a>Parameter

*format*<br/>
[in]: Ein Wert, der das zu verwendende Format darstellt.

## <a name="return-value"></a>Rückgabewert

Das vorherige Ausgabeformat.

## <a name="remarks"></a>Bemerkungen

`_set_output_format` wird verwendet, um die Ausgabe von formatierten E/A-Funktionen, wie z.B. [printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md), zu konfigurieren. Zurzeit ist die einzige Formatierungskonvention, die von dieser Funktion geändert werden kann, die Anzahl der Stellen, die in Exponenten in der Ausgabe von Gleitkommazahlen angezeigt werden.

Standardmäßig erfolgt die Ausgabe von Gleitkommazahlen durch Funktionen wie `printf_s`, `wprintf_s`und ähnliche Funktionen in der Standard-C-Bibliothek von Visual C++ mit drei Stellen für den Exponenten, selbst wenn keine drei Stellen für die Darstellung des Werts des Exponenten erforderlich sind. Nullen werden verwendet, um den Wert auf drei Stellen aufzufüllen. `_set_output_format` ermöglicht Ihnen, dieses Verhalten zu ändern, sodass nur zwei Stellen im Exponenten geduckt werden, es sei denn, die Größe des Exponenten macht eine dritte Stelle erforderlich.

Um zweistellige Exponenten zu aktivieren, rufen Sie diese Funktion mit dem Parameter `_TWO_DIGIT_EXPONENT`auf, wie im Beispiel gezeigt. Um die zweistelligen Exponenten zu deaktivieren, rufen Sie diese Funktion mit dem Argument „0“ auf.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|`_set_output_format`|\<stdio.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../c-runtime-library/compatibility.md) in der Einführung.

## <a name="example"></a>Beispiel

```C
// crt_set_output_format.c
#include <stdio.h>

void printvalues(double x, double y)
{
   printf_s("%11.4e %11.4e\n", x, y);
   printf_s("%11.4E %11.4E\n", x, y);
   printf_s("%11.4g %11.4g\n", x, y);
   printf_s("%11.4G %11.4G\n", x, y);
}

int main()
{
   double x = 1.211E-5;
   double y = 2.3056E-112;
   unsigned int old_exponent_format;

   // Use the default format
   printvalues(x, y);

   // Enable two-digit exponent format
   old_exponent_format = _set_output_format(_TWO_DIGIT_EXPONENT);

   printvalues(x, y);

   // Disable two-digit exponent format
   _set_output_format( old_exponent_format );

   printvalues(x, y);
}
```

```Output
1.2110e-005 2.3056e-112
1.2110E-005 2.3056E-112
1.211e-005  2.306e-112
1.211E-005  2.306E-112
1.2110e-05 2.3056e-112
1.2110E-05 2.3056E-112
  1.211e-05  2.306e-112
  1.211E-05  2.306E-112
1.2110e-005 2.3056e-112
1.2110E-005 2.3056E-112
1.211e-005  2.306e-112
1.211E-005  2.306E-112
```

## <a name="see-also"></a>Siehe auch

[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[_get_output_format](../c-runtime-library/get-output-format.md)
