---
title: _set_abort_behavior
ms.date: 4/2/2020
api_name:
- _set_abort_behavior
- _o__set_abort_behavior
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_abort_behavior
- set_abort_behavior
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
ms.openlocfilehash: 06f72597a384cc5c90b2e345e62e13dee96c4dca
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913128"
---
# <a name="_set_abort_behavior"></a>_set_abort_behavior

Gibt die Aktion an, die ausgeführt werden soll, wenn ein Programm nicht normal beendet wird.

> [!NOTE]
> Verwenden Sie die [Abbruch](abort.md) -Funktion nicht zum Herunterfahren einer Microsoft Store-App, mit Ausnahme von Test-oder Debugszenarien. Programmgesteuerte oder UI-Methoden zum Schließen einer Store-App sind gemäß den [Microsoft Store Richtlinien](/legal/windows/agreements/store-policies)nicht zulässig. Weitere Informationen finden Sie unter [UWP-App-Lebenszyklus](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Syntax

```C
unsigned int _set_abort_behavior(
   unsigned int flags,
   unsigned int mask
);
```

### <a name="parameters"></a>Parameter

*flags*<br/>
Neuer Wert der [Abbruch](abort.md) -Flags.

*mask*<br/>
Maske für die festzulegenden [Abbruch](abort.md) -Flags-Bits.

## <a name="return-value"></a>Rückgabewert

Der alte Wert der Flags.

## <a name="remarks"></a>Hinweise

Es gibt zwei [Abbruch](abort.md) -Flags: **_WRITE_ABORT_MSG** und **_CALL_REPORTFAULT**. **_WRITE_ABORT_MSG** bestimmt, ob eine hilfreiche Textnachricht gedruckt wird, wenn ein Programm nicht normal beendet wird. Die Meldung besagt, dass die Anwendung die [Abbruch](abort.md) -Funktion aufgerufen hat. Beim Standardverhalten wird die Meldung ausgeben. Wenn festgelegt ist, gibt **_CALL_REPORTFAULT**an, dass ein Watson-Absturz Abbild generiert und gemeldet wird, wenn [Abbruch](abort.md) aufgerufen wird. Standardmäßig ist die Absturzabbildberichterstellung in den Nichtdebugversionen aktiviert.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_set_abort_behavior**|\<stdlib.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_set_abort_behavior.c
// compile with: /TC
#include <stdlib.h>

int main()
{
   printf("Suppressing the abort message. If successful, this message"
          " will be the only output.\n");
   // Suppress the abort message
   _set_abort_behavior( 0, _WRITE_ABORT_MSG);
   abort();
}
```

```Output
Suppressing the abort message. If successful, this message will be the only output.
```

## <a name="see-also"></a>Weitere Informationen

[Abbruch](abort.md)<br/>
