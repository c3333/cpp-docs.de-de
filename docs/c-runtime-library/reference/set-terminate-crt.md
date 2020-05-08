---
title: set_terminate (CRT)
ms.date: 4/2/2020
api_name:
- set_terminate
- _o_set_terminate
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
- set_terminate
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
ms.openlocfilehash: 29b760d8831411142aad052fdef510efb0486747
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914521"
---
# <a name="set_terminate-crt"></a>set_terminate (CRT)

Installiert ihre eigene Beendigungs Routine, um durch **Beenden**aufgerufen zu werden.

## <a name="syntax"></a>Syntax

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>Parameter

*termfunction*<br/>
Zeiger auf eine Funktion zum Beenden, die Sie schreiben.

## <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf die vorherige Funktion zurück, die von **Set_terminate** registriert wurde, sodass die vorherige Funktion später wieder hergestellt werden kann. Wenn keine vorherige Funktion festgelegt wurde, kann der Rückgabewert verwendet werden, um das Standardverhalten wiederherzustellen. Dieser Wert kann **null**sein.

## <a name="remarks"></a>Hinweise

Die **Set_terminate** -Funktion installiert *termfunction* als die Funktion, die durch **Beenden**aufgerufen wird. **Set_terminate** wird mit der C++-Ausnahmebehandlung verwendet und kann an einem beliebigen Punkt im Programm aufgerufen werden, bevor die Ausnahme ausgelöst wird. **Beendigungs Aufrufe werden** standardmäßig [abgebrochen](abort.md) . Sie können diesen Standardwert ändern, indem Sie eine eigene Beendigungs Funktion schreiben und **Set_terminate** mit dem Namen ihrer Funktion als Argument aufrufen. **Beenden** Ruft die letzte Funktion auf, die als Argument für **Set_terminate**angegeben wurde. Nach dem Ausführen gewünschter Bereinigungs Tasks sollte *termfunction* das Programm beenden. Wenn Sie nicht beendet wird (wenn Sie zu Ihrem Aufrufer zurückkehrt), wird [Abbruch](abort.md) aufgerufen.

In einer Multithreadumgebung werden die Beendigungsfunktionen für jeden Thread separat verwaltet. Jeder neue Thread muss eine eigene Beendigungsfunktion installieren. Daher ist jeder Thread für die eigene Beendigungsbehandlung verantwortlich.

Der **terminate_function** Typ ist in eh definiert. H als Zeiger auf eine benutzerdefinierte Beendigungs Funktion, *termfunction* , die **void**zurückgibt. Die benutzerdefinierte Funktion *termfunction* kann keine Argumente annehmen und sollte nicht an ihren Aufrufer zurückgegeben werden. Wenn dies der Fall ist, wird [Abbruch](abort.md) aufgerufen. Eine Ausnahme kann nicht innerhalb von *termfunction*ausgelöst werden.

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> Die **Set_terminate** Funktion funktioniert nur außerhalb des Debuggers.

Es gibt einen einzigen **Set_terminate** Handler für alle dynamisch verknüpften DLLs oder EXEs. auch wenn Sie **Set_terminate** , wird der Handler möglicherweise durch einen anderen ersetzt, oder Sie ersetzen einen Handler, der von einer anderen DLL oder exe festgelegt wurde.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**set_terminate**|\<eh.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Eine Abbildung finden Sie im Beispiel für [terminate](terminate-crt.md).

## <a name="see-also"></a>Weitere Informationen

[Ausnahmebehandlungsroutinen](../../c-runtime-library/exception-handling-routines.md)<br/>
[Abbruch](abort.md)<br/>
[_get_terminate](get-terminate.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[aufzu](terminate-crt.md)<br/>
[te](unexpected-crt.md)<br/>
