---
title: _fpieee_flt
ms.date: 04/05/2018
api_name:
- _fpieee_flt
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fpieee_flt
- _fpieee_flt
helpviewer_keywords:
- _fpieee_flt function
- exception handling, floating-point
- floating-point exception handling
- fpieee_flt function
ms.assetid: 2bc4801e-0eed-4e73-b518-215da8cc9740
ms.openlocfilehash: c6a77dcba06b58191781900d4e24202c6335cfb8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213566"
---
# <a name="_fpieee_flt"></a>_fpieee_flt

Ruft einen benutzerdefinierten Traphandler für IEEE-Gleitkommaausnahmen auf.

## <a name="syntax"></a>Syntax

```C
int _fpieee_flt(
   unsigned long excCode,
   struct _EXCEPTION_POINTERS *excInfo,
   int handler(_FPIEEE_RECORD *)
);
```

### <a name="parameters"></a>Parameter

*exccode*<br/>
Ausnahmecode.

*excinfo*<br/>
Zeiger zur Windows NT-Ausnahmeinformationsstruktur

*lers*<br/>
Zeiger zur IEEE-Traphandlerroutine des Benutzers.

## <a name="return-value"></a>Rückgabewert

Der Rückgabewert von **_fpieee_flt** ist der Wert, der vom *Handler*zurückgegeben wird. Daher wird die IEEE-Filterroutine möglicherweise in der except-Klausel eines strukturierten Ausnahmebehandlungsmechanismus (SEH) verwendet.

## <a name="remarks"></a>Bemerkungen

Die **_fpieee_flt** -Funktion Ruft einen benutzerdefinierten Trap Handler für IEEE-Gleit Komma Ausnahmen auf und stellt alle relevanten Informationen bereit. Diese Routine dient als Ausnahmefilter im SEH-Mechanismus, der bei Bedarf einen eigenen IEEE-Ausnahmehandler aufruft.

Die in fpieee. h definierte **_FPIEEE_RECORD** Struktur enthält Informationen zu einer IEEE-Gleit Komma Ausnahme. Diese Struktur wird von **_fpieee_flt**an den benutzerdefinierten Trap Handler übermittelt.

|_FPIEEE_RECORD-Feld|BESCHREIBUNG|
|----------------------------|-----------------|
|**Von roundingmode**<br/>**Genauigkeit**|Diese **`unsigned int`** Felder enthalten Informationen zur Gleit Komma Umgebung zu dem Zeitpunkt, zu dem die Ausnahme aufgetreten ist.|
|**Vorgang**|Dieses **`unsigned int`** Feld gibt den Typ des Vorgangs an, der das Trap verursacht hat. Wenn der Typ ein Vergleich (**_FpCodeCompare**) ist, können Sie einen der speziellen **_FPIEEE_COMPARE_RESULT** Werte (gemäß Definition in "f. h") im **Ergebnis. Value** -Feld angeben. Der Konvertierungstyp (**_FpCodeConvert**) gibt an, dass das Trap während einer Gleit Komma Konvertierung aufgetreten ist. Sie können den **Operand1** -und den **Ergebnistyp** betrachten, um den Typ der versuchten Konvertierung zu ermitteln.|
|**Operand1**<br/>**Operand2**<br/>**Ergebnis**|Diese **_FPIEEE_VALUE** Strukturen geben die Typen und Werte des vorgeschlagenen Ergebnisses und der Operanden an. Jede Struktur enthält die folgenden Felder:<br /><br /> **Operandvalid** -Flag, das angibt, ob der Antwort Wert gültig ist.<br />**Format** -Datentyp des entsprechenden Werts. Der Formattyp kann zurückgegeben werden, wenn der entsprechende Wert ungültig ist.<br />**Wert** -Ergebnis oder Operanden Datenwert.|
|**Ursache**<br/>**Aktivieren**<br/>**Status**|**_FPIEEE_EXCEPTION_FLAGS** enthält ein Bitfeld pro Typ der Gleit Komma Ausnahme. Es gibt eine Entsprechung zwischen diesen Feldern und den Argumenten, die verwendet werden, um die für [_controlfp](control87-controlfp-control87-2.md) bereitgestellten Ausnahmen zu maskieren. Die genaue Bedeutung der einzelnen Bits hängt vom Kontext ab:<br /><br /> **Ursache** : jedes festgelegte Bit gibt die bestimmte Ausnahme an, die ausgelöst wurde.<br />**Enable** -jedes festgelegte Bit gibt an, dass die bestimmte Ausnahme zurzeit nicht maskiert ist.<br />**Status** : jedes festgelegte Bit gibt an, dass die bestimmte Ausnahme zurzeit aussteht. Dies schließt Ausnahmen ein, die nicht ausgelöst wurden, da Sie durch **_controlfp**maskiert wurden.|

Ausstehende, deaktivierte Ausnahmen werden bei Aktivierung ausgelöst. Dies kann zu nicht definiertem Verhalten führen, wenn **_fpieee_flt** als Ausnahme Filter verwendet wird. Rufen Sie vor der Aktivierung von Gleitkommaausnahmen immer [_clearfp](clear87-clearfp.md) auf.

## <a name="requirements"></a>Requirements (Anforderungen)

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**_fpieee_flt**|\<fpieee.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_fpieee.c
// This program demonstrates the implementation of
// a user-defined floating-point exception handler using the
// _fpieee_flt function.

#include <fpieee.h>
#include <excpt.h>
#include <float.h>
#include <stddef.h>

int fpieee_handler( _FPIEEE_RECORD * );

int fpieee_handler( _FPIEEE_RECORD *pieee )
{
   // user-defined ieee trap handler routine:
   // there is one handler for all
   // IEEE exceptions

   // Assume the user wants all invalid
   // operations to return 0.

   if ((pieee->Cause.InvalidOperation) &&
       (pieee->Result.Format == _FpFormatFp32))
   {
        pieee->Result.Value.Fp32Value = 0.0F;

        return EXCEPTION_CONTINUE_EXECUTION;
   }
   else
      return EXCEPTION_EXECUTE_HANDLER;
}

#define _EXC_MASK    \
    _EM_UNDERFLOW  + \
    _EM_OVERFLOW   + \
    _EM_ZERODIVIDE + \
    _EM_INEXACT

int main( void )
{
   // ...

   __try {
      // unmask invalid operation exception
      _controlfp_s(NULL, _EXC_MASK, _MCW_EM);

      // code that may generate
      // fp exceptions goes here
   }
   __except ( _fpieee_flt( GetExceptionCode(),
                GetExceptionInformation(),
                fpieee_handler ) ){

      // code that gets control

      // if fpieee_handler returns
      // EXCEPTION_EXECUTE_HANDLER goes here

   }

   // ...
}
```

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[_control87, _controlfp \_ _control87_2](control87-controlfp-control87-2.md)<br/>
[_controlfp_s](controlfp-s.md)<br/>
