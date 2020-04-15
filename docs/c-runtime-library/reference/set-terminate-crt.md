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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 08ea5bb8c446fadac6a7bcf7ca172c5d14546776
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332100"
---
# <a name="set_terminate-crt"></a>set_terminate (CRT)

Installiert Ihre eigene Beendigungsroutine, die von **terminate**aufgerufen werden soll.

## <a name="syntax"></a>Syntax

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>Parameter

*termFunktion*<br/>
Zeiger auf eine Funktion zum Beenden, die Sie schreiben.

## <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf die vorherige Funktion zurück, die von **set_terminate** registriert wurde, damit die vorherige Funktion später wiederhergestellt werden kann. Wenn keine vorherige Funktion festgelegt wurde, kann der Rückgabewert verwendet werden, um das Standardverhalten wiederherzustellen. Dieser Wert kann **NULL**sein.

## <a name="remarks"></a>Bemerkungen

Die **set_terminate-Funktion** installiert *termFunction* als Funktion, die von **terminate**aufgerufen wird. **set_terminate** wird mit C++-Ausnahmebehandlung verwendet und kann an jedem beliebigen Punkt in Ihrem Programm aufgerufen werden, bevor die Ausnahme ausgelöst wird. **beenden** Anrufe standardmäßig [abbrechen.](abort.md) Sie können diese Standardeinstellung ändern, indem Sie Ihre eigene Beendigungsfunktion schreiben und **set_terminate** mit dem Namen Ihrer Funktion als Argument aufrufen. **terminate** ruft die letzte Funktion auf, die als Argument für **set_terminate**angegeben wurde. Nachdem Sie die gewünschten Bereinigungsaufgaben ausgeführt haben, sollte *termFunction* das Programm beenden. Wenn er nicht beendet wird (wenn er zu seinem Aufrufer zurückkehrt), wird [abort](abort.md) aufgerufen.

In einer Multithreadumgebung werden die Beendigungsfunktionen für jeden Thread separat verwaltet. Jeder neue Thread muss eine eigene Beendigungsfunktion installieren. Daher ist jeder Thread für die eigene Beendigungsbehandlung verantwortlich.

Der **terminate_function** Typ ist in EH definiert. H als Zeiger auf eine benutzerdefinierte Beendigungsfunktion, *termFunction,* die **void**zurückgibt. Ihre benutzerdefinierte Funktion *termFunction* kann keine Argumente annehmen und sollte nicht zu ihrem Aufrufer zurückkehren. Wenn dies der Zuspruch besteht, wird [abort](abort.md) aufgerufen. Eine Ausnahme darf nicht innerhalb von *termFunction*ausgelöst werden.

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> Die **set_terminate** Funktion funktioniert nur außerhalb des Debuggers.

Es gibt einen einzigen **set_terminate** Handler für alle dynamisch verknüpften DLLs oder EXEs. Auch wenn Sie **set_terminate** wird ihr Handler durch einen anderen ersetzt, oder Sie ersetzen einen Handler, der durch eine andere DLL oder EXE festgelegt wurde.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**set_terminate**|\<eh.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Eine Abbildung finden Sie im Beispiel für [terminate](terminate-crt.md).

## <a name="see-also"></a>Siehe auch

[Ausnahmebehandlungsroutinen](../../c-runtime-library/exception-handling-routines.md)<br/>
[Abbrechen](abort.md)<br/>
[_get_terminate](get-terminate.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[Beenden](terminate-crt.md)<br/>
[Unerwartete](unexpected-crt.md)<br/>
