---
title: agent-Klasse
ms.date: 11/04/2016
f1_keywords:
- agent
- AGENTS/concurrency::agent
- AGENTS/concurrency::agent::agent
- AGENTS/concurrency::agent::cancel
- AGENTS/concurrency::agent::start
- AGENTS/concurrency::agent::status
- AGENTS/concurrency::agent::status_port
- AGENTS/concurrency::agent::wait
- AGENTS/concurrency::agent::wait_for_all
- AGENTS/concurrency::agent::wait_for_one
- AGENTS/concurrency::agent::done
- AGENTS/concurrency::agent::run
helpviewer_keywords:
- agent class
ms.assetid: 1b09e3d2-5e37-4966-b016-907ef1512456
ms.openlocfilehash: f0092f5f90bbdf253c09dbdc80849c3db472212f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78882937"
---
# <a name="agent-class"></a>agent-Klasse

Diese Klasse ist als Basisklasse für alle unabhängigen Agents vorgesehen. Sie wird verwendet, um den Zustand von anderen Agents auszublenden und mithilfe von Meldungsübergabe zu interagieren.

## <a name="syntax"></a>Syntax

```cpp
class agent;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Büros](#ctor)|Ist überladen. Erstellt einen Agent.|
|[~ Agent-Dekonstruktor](#dtor)|Zerstört den Agent.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[cancel](#cancel)|Verschiebt einen Agent entweder vom `agent_created` oder `agent_runnable` Status in den `agent_canceled` Zustand.|
|[start](#start)|Verschiebt einen Agent vom `agent_created` in den Zustand `agent_runnable` und plant die Ausführung.|
|[status](#status)|Eine synchrone Quelle von Statusinformationen vom Agent.|
|[status_port](#status_port)|Eine asynchrone Quelle von Statusinformationen vom Agent.|
|[Warte](#wait)|Wartet darauf, dass ein Agent seine Aufgabe abschließt.|
|[wait_for_all](#wait_for_all)|Wartet darauf, dass alle angegebenen Agents Ihre Tasks ausführen.|
|[wait_for_one](#wait_for_one)|Wartet darauf, dass einer der angegebenen Agents seine Aufgabe abschließt.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ausgeführt](#done)|Verschiebt einen Agent in den `agent_done`-Zustand, der angibt, dass der Agent abgeschlossen wurde.|
|[run](#run)|Stellt die Hauptaufgabe eines Agents dar. `run` sollte in einer abgeleiteten Klasse überschrieben werden und gibt an, was der Agent nach dem Start tun soll.|

## <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [asynchrone Agents](../../../parallel/concrt/asynchronous-agents.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`agent`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** agents.h

**Namespace:** Parallelität

## <a name="ctor"></a>Büros

Erstellt einen Agent.

```cpp
agent();

agent(Scheduler& _PScheduler);

agent(ScheduleGroup& _PGroup);
```

### <a name="parameters"></a>Parameter

*_PScheduler*<br/>
Das `Scheduler` Objekt, in dem die Ausführungs Aufgabe des Agents geplant ist.

*_PGroup*<br/>
Das `ScheduleGroup` Objekt, in dem die Ausführungs Aufgabe des Agents geplant ist. Das verwendete `Scheduler` -Objekt wird von der Planungsgruppe impliziert.

### <a name="remarks"></a>Bemerkungen

Die Runtime verwendet das Standardplanungsprogramm, wenn Sie den `_PScheduler` -Parameter oder den `_PGroup` -Parameter nicht angeben.

## <a name="dtor"></a>~ Agent

Zerstört den Agent.

```cpp
virtual ~agent();
```

### <a name="remarks"></a>Bemerkungen

Es ist ein Fehler, einen Agent zu zerstören, der sich nicht in einem Endzustand befindet (entweder `agent_done` oder `agent_canceled`). Dies kann vermieden werden, indem Sie darauf warten, dass der Agent einen Endzustand im Dekonstruktor einer Klasse erreicht, die von der `agent` Klasse erbt.

## <a name="cancel"></a>Abbrechen

Verschiebt einen Agent entweder vom `agent_created` oder `agent_runnable` Status in den `agent_canceled` Zustand.

```cpp
bool cancel();
```

### <a name="return-value"></a>Rückgabewert

**true** , wenn der Agent abgebrochen wurde, andernfalls **false** . Ein Agent kann nicht abgebrochen werden, wenn er bereits ausgeführt wurde oder bereits abgeschlossen ist.

## <a name="done"></a>ausgeführt

Verschiebt einen Agent in den `agent_done`-Zustand, der angibt, dass der Agent abgeschlossen wurde.

```cpp
bool done();
```

### <a name="return-value"></a>Rückgabewert

**true** , wenn der Agent in den `agent_done`-Zustand verschoben wird, andernfalls **false** . Ein Agent, der abgebrochen wurde, kann nicht in den `agent_done` Zustand verschoben werden.

### <a name="remarks"></a>Bemerkungen

Diese Methode sollte am Ende der `run`-Methode aufgerufen werden, wenn Sie wissen, dass die Ausführung des Agents abgeschlossen wurde.

## <a name="run"></a>Lauf

Stellt die Hauptaufgabe eines Agents dar. `run` sollte in einer abgeleiteten Klasse überschrieben werden und gibt an, was der Agent nach dem Start tun soll.

```cpp
virtual void run() = 0;
```

### <a name="remarks"></a>Bemerkungen

Der Agent-Status wird in `agent_started` geändert, bevor diese Methode aufgerufen wird. Die-Methode sollte `done` auf dem Agent mit einem entsprechenden Status vor der Rückgabe aufrufen und möglicherweise keine Ausnahmen auslösen.

## <a name="start"></a>begonnen

Verschiebt einen Agent vom `agent_created` in den Zustand `agent_runnable` und plant die Ausführung.

```cpp
bool start();
```

### <a name="return-value"></a>Rückgabewert

**true** , wenn der Agent ordnungsgemäß gestartet wurde, andernfalls **false** . Ein Agent, der abgebrochen wurde, kann nicht gestartet werden.

## <a name="status"></a>Stands

Eine synchrone Quelle von Statusinformationen vom Agent.

```cpp
agent_status status();
```

### <a name="return-value"></a>Rückgabewert

Gibt den aktuellen Status des Agents zurück. Beachten Sie, dass sich der zurückgegebene Status unmittelbar nach der Rückgabe ändern kann.

## <a name="status_port"></a>status_port

Eine asynchrone Quelle von Statusinformationen vom Agent.

```cpp
ISource<agent_status>* status_port();
```

### <a name="return-value"></a>Rückgabewert

Gibt eine Nachrichtenquelle zurück, die Nachrichten über den aktuellen Status des Agents senden kann.

## <a name="wait"></a>Warte

Wartet darauf, dass ein Agent seine Aufgabe abschließt.

```cpp
static agent_status __cdecl wait(
    _Inout_ agent* _PAgent,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parameter

*_PAgent*<br/>
Ein Zeiger auf den Agent, auf den gewartet werden soll.

*_Timeout*<br/>
Die maximale Wartezeit in Millisekunden.

### <a name="return-value"></a>Rückgabewert

Die `agent_status` des Agents, wenn der Warte Vorgang abgeschlossen ist. Dies kann entweder `agent_canceled` oder `agent_done`sein.

### <a name="remarks"></a>Bemerkungen

Eine Agent-Aufgabe wird abgeschlossen, wenn der Agent in die `agent_canceled` oder `agent_done` Zustände eintritt.

Wenn der Parameter `_Timeout` einen anderen Wert als die Konstante `COOPERATIVE_TIMEOUT_INFINITE`aufweist, wird die Ausnahme [Operation_timed_out](operation-timed-out-class.md) ausgelöst, wenn die angegebene Zeitspanne abläuft, bevor der Agent die Aufgabe abgeschlossen hat.

## <a name="wait_for_all"></a>wait_for_all

Wartet darauf, dass alle angegebenen Agents Ihre Tasks ausführen.

```cpp
static void __cdecl wait_for_all(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    _Out_writes_opt_(count) agent_status* _PStatus = NULL,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parameter

*count*<br/>
Die Anzahl der Agent-Zeiger, die im Array `_PAgents`vorhanden sind.

*_PAgents*<br/>
Ein Array von Zeigern auf die Agents, auf die gewartet werden soll.

*_PStatus*<br/>
Ein Zeiger auf ein Array von Agent-Status. Jeder Statuswert stellt den Status des entsprechenden Agents dar, wenn die Methode zurückgegeben wird.

*_Timeout*<br/>
Die maximale Wartezeit in Millisekunden.

### <a name="remarks"></a>Bemerkungen

Eine Agent-Aufgabe wird abgeschlossen, wenn der Agent in die `agent_canceled` oder `agent_done` Zustände eintritt.

Wenn der Parameter `_Timeout` einen anderen Wert als die Konstante `COOPERATIVE_TIMEOUT_INFINITE`aufweist, wird die Ausnahme [Operation_timed_out](operation-timed-out-class.md) ausgelöst, wenn die angegebene Zeitspanne abläuft, bevor der Agent die Aufgabe abgeschlossen hat.

## <a name="wait_for_one"></a>wait_for_one

Wartet darauf, dass einer der angegebenen Agents seine Aufgabe abschließt.

```cpp
static void __cdecl wait_for_one(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    agent_status& _Status,
    size_t& _Index,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parameter

*count*<br/>
Die Anzahl der Agent-Zeiger, die im Array `_PAgents`vorhanden sind.

*_PAgents*<br/>
Ein Array von Zeigern auf die Agents, auf die gewartet werden soll.

*_Status*<br/>
Ein Verweis auf eine Variable, in der der Agentstatus platziert wird.

*_Index*<br/>
Ein Verweis auf eine Variable, in der der agentindex platziert wird.

*_Timeout*<br/>
Die maximale Wartezeit in Millisekunden.

### <a name="remarks"></a>Bemerkungen

Eine Agent-Aufgabe wird abgeschlossen, wenn der Agent in die `agent_canceled` oder `agent_done` Zustände eintritt.

Wenn der Parameter `_Timeout` einen anderen Wert als die Konstante `COOPERATIVE_TIMEOUT_INFINITE`aufweist, wird die Ausnahme [Operation_timed_out](operation-timed-out-class.md) ausgelöst, wenn die angegebene Zeitspanne abläuft, bevor der Agent die Aufgabe abgeschlossen hat.

## <a name="see-also"></a>Weitere Informationen

[Concurrency-Namespace](concurrency-namespace.md)
