---
title: terminate (CRT)
ms.date: 4/2/2020
api_name:
- terminate
- _o_terminate
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- terminate
helpviewer_keywords:
- terminate function
- exception handling, termination
ms.assetid: 90e67402-08e9-4b2a-962c-66a8afd3ccb4
ms.openlocfilehash: 1aa95daeab424c933f10060fb4f87cb317aa188c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362541"
---
# <a name="terminate-crt"></a>terminate (CRT)

Ruft [abbrechen](abort.md) oder eine Funktion, die Sie mit **set_terminate angeben.**

## <a name="syntax"></a>Syntax

```C
void terminate( void );
```

## <a name="remarks"></a>Bemerkungen

Die **Terminate-Funktion** wird bei der C++-Ausnahmebehandlung verwendet und in den folgenden Fällen aufgerufen:

- Ein übereinstimmender Catch-Handler kann nicht für eine ausgelöste C++.Ausnahme gefunden werden.

- Eine Ausnahme wird während der Stapelentladung von einer Destruktorfunktion ausgelöst.

- Der Stapel ist nach dem Auslösen einer Ausnahme beschädigt.

**beenden** Anrufe standardmäßig [abbrechen.](abort.md) Sie können diese Standardeinstellung ändern, indem Sie Ihre eigene Beendigungsfunktion schreiben und **set_terminate** mit dem Namen Ihrer Funktion als Argument aufrufen. **terminate** ruft die letzte Funktion auf, die als Argument für **set_terminate**angegeben wurde. Weitere Informationen finden Sie unter [Nicht behandelte C++-Ausnahmen](../../cpp/unhandled-cpp-exceptions.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**Beenden**|\<eh.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```cpp
// crt_terminate.cpp
// compile with: /EHsc
#include <eh.h>
#include <process.h>
#include <iostream>
using namespace std;

void term_func();

int main()
{
    int i = 10, j = 0, result;
    set_terminate( term_func );
    try
    {
        if( j == 0 )
            throw "Divide by zero!";
        else
            result = i/j;
    }
    catch( int )
    {
        cout << "Caught some integer exception.\n";
    }
    cout << "This should never print.\n";
}

void term_func()
{
    cout << "term_func() was called by terminate().\n";

    // ... cleanup tasks performed here

    // If this function does not exit, abort is called.

    exit(-1);
}
```

```Output
term_func() was called by terminate().
```

## <a name="see-also"></a>Siehe auch

[Ausnahmebehandlungsroutinen](../../c-runtime-library/exception-handling-routines.md)<br/>
[Abbrechen](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[Unerwartete](unexpected-crt.md)<br/>
