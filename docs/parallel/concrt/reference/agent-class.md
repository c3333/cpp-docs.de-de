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
ms.openlocfilehash: f1d98cdc6237f182e0240a85f2fdce3410232195
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213891"
---
# <a name="agent-class"></a>agent-Klasse

Diese Klasse ist als Basisklasse für alle unabhängigen Agents vorgesehen. Sie wird verwendet, um den Zustand von anderen Agents auszublenden und mithilfe von Meldungsübergabe zu interagieren.

## <a name="syntax"></a>Syntax

```cpp
class agent;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Agent](#ctor)|Ist überladen. Erstellt einen Agent.|
|[~ Agent-Dekonstruktor](#dtor)|Zerstört den Agent.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[cancel](#cancel)|Verschiebt einen Agent entweder vom- `agent_created` Zustand oder vom- `agent_runnable` Zustand in den- `agent_canceled` Zustand.|
|[start](#start)|Verschiebt einen Agent aus dem `agent_created` Zustand in den `agent_runnable` Zustand und plant die Ausführung.|
|[status](#status)|Eine synchrone Quelle von Statusinformationen vom Agent.|
|[status_port](#status_port)|Eine asynchrone Quelle von Statusinformationen vom Agent.|
|[Warte](#wait)|Wartet darauf, dass ein Agent seine Aufgabe abschließt.|
|[wait_for_all](#wait_for_all)|Wartet darauf, dass alle angegebenen Agents Ihre Tasks ausführen.|
|[wait_for_one](#wait_for_one)|Wartet darauf, dass einer der angegebenen Agents seine Aufgabe abschließt.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Fertig](#done)|Verschiebt einen Agent in den `agent_done` Zustand, der angibt, dass der Agent abgeschlossen wurde.|
|[Lauf](#run)|Stellt die Hauptaufgabe eines Agents dar. `run`sollte in einer abgeleiteten Klasse überschrieben werden und gibt an, was der Agent nach dem Start tun soll.|

## <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [asynchrone Agents](../../../parallel/concrt/asynchronous-agents.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`agent`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** agents.h

**Namespace:** Parallelität

## <a name="agent"></a><a name="ctor"></a>Büros

Erstellt einen Agent.

```cpp
agent();

agent(Scheduler& _PScheduler);

agent(ScheduleGroup& _PGroup);
```

### <a name="parameters"></a>Parameter

*_PScheduler*<br/>
Das- `Scheduler` Objekt, in dem die Ausführungs Aufgabe des Agents geplant ist.

*_PGroup*<br/>
Das- `ScheduleGroup` Objekt, in dem die Ausführungs Aufgabe des Agents geplant ist. Das verwendete `Scheduler` -Objekt wird von der Planungsgruppe impliziert.

### <a name="remarks"></a>Bemerkungen

Die Runtime verwendet das Standardplanungsprogramm, wenn Sie den `_PScheduler` -Parameter oder den `_PGroup` -Parameter nicht angeben.

## <a name="agent"></a><a name="dtor"></a>~ Agent

Zerstört den Agent.

```cpp
virtual ~agent();
```

### <a name="remarks"></a>Bemerkungen

Es ist ein Fehler, einen Agent zu zerstören, der sich nicht in einem Endzustand befindet (entweder `agent_done` oder `agent_canceled` ). Dies kann vermieden werden, indem Sie darauf warten, dass der Agent einen Endzustand im Dekonstruktor einer Klasse erreicht, die von der-Klasse erbt `agent` .

## <a name="cancel"></a><a name="cancel"></a>Abbrechen

Verschiebt einen Agent entweder vom- `agent_created` Zustand oder vom- `agent_runnable` Zustand in den- `agent_canceled` Zustand.

```cpp
bool cancel();
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der Agent abgebrochen wurde, **`false`** andernfalls. Ein Agent kann nicht abgebrochen werden, wenn er bereits ausgeführt wurde oder bereits abgeschlossen ist.

## <a name="done"></a><a name="done"></a>ausgeführt

Verschiebt einen Agent in den `agent_done` Zustand, der angibt, dass der Agent abgeschlossen wurde.

```cpp
bool done();
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der Agent in den Zustand versetzt wird `agent_done` , **`false`** andernfalls. Ein Agent, der abgebrochen wurde, kann nicht in den Zustand versetzt werden `agent_done` .

### <a name="remarks"></a>Bemerkungen

Diese Methode sollte am Ende der-Methode aufgerufen werden `run` , wenn Sie wissen, dass die Ausführung des Agents abgeschlossen wurde.

## <a name="run"></a><a name="run"></a>Lauf

Stellt die Hauptaufgabe eines Agents dar. `run`sollte in einer abgeleiteten Klasse überschrieben werden und gibt an, was der Agent nach dem Start tun soll.

```cpp
virtual void run() = 0;
```

### <a name="remarks"></a>Bemerkungen

Der Agent-Status wird in "Right" geändert, `agent_started` bevor diese Methode aufgerufen wird. Die-Methode sollte `done` vor der Rückgabe von für den Agent mit einem entsprechenden Status aufrufen und kann ggf. keine Ausnahmen auslösen.

## <a name="start"></a><a name="start"></a>begonnen

Verschiebt einen Agent aus dem `agent_created` Zustand in den `agent_runnable` Zustand und plant die Ausführung.

```cpp
bool start();
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der Agent ordnungsgemäß gestartet wurde, **`false`** andernfalls. Ein Agent, der abgebrochen wurde, kann nicht gestartet werden.

## <a name="status"></a><a name="status"></a>Stands

Eine synchrone Quelle von Statusinformationen vom Agent.

```cpp
agent_status status();
```

### <a name="return-value"></a>Rückgabewert

Gibt den aktuellen Status des Agents zurück. Beachten Sie, dass sich der zurückgegebene Status unmittelbar nach der Rückgabe ändern kann.

## <a name="status_port"></a><a name="status_port"></a>status_port

Eine asynchrone Quelle von Statusinformationen vom Agent.

```cpp
ISource<agent_status>* status_port();
```

### <a name="return-value"></a>Rückgabewert

Gibt eine Nachrichtenquelle zurück, die Nachrichten über den aktuellen Status des Agents senden kann.

## <a name="wait"></a><a name="wait"></a>Warte

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

Der `agent_status` des Agents, wenn der Warte Vorgang abgeschlossen ist. Dies kann entweder `agent_canceled` oder sein `agent_done` .

### <a name="remarks"></a>Bemerkungen

Eine agentaufgabe wird abgeschlossen, wenn der Agent in den Zustand `agent_canceled` oder Eintritt `agent_done` .

Wenn der-Parameter `_Timeout` einen anderen Wert als die-Konstante aufweist `COOPERATIVE_TIMEOUT_INFINITE` , wird die Ausnahme [Operation_timed_out](operation-timed-out-class.md) ausgelöst, wenn die angegebene Zeitspanne abläuft, bevor der Agent die Aufgabe abgeschlossen hat.

## <a name="wait_for_all"></a><a name="wait_for_all"></a>wait_for_all

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
Die Anzahl der im Array vorhandenen Agent-Zeiger `_PAgents` .

*_PAgents*<br/>
Ein Array von Zeigern auf die Agents, auf die gewartet werden soll.

*_PStatus*<br/>
Ein Zeiger auf ein Array von Agent-Status. Jeder Statuswert stellt den Status des entsprechenden Agents dar, wenn die Methode zurückgegeben wird.

*_Timeout*<br/>
Die maximale Wartezeit in Millisekunden.

### <a name="remarks"></a>Bemerkungen

Eine agentaufgabe wird abgeschlossen, wenn der Agent in den Zustand `agent_canceled` oder Eintritt `agent_done` .

Wenn der-Parameter `_Timeout` einen anderen Wert als die-Konstante aufweist `COOPERATIVE_TIMEOUT_INFINITE` , wird die Ausnahme [Operation_timed_out](operation-timed-out-class.md) ausgelöst, wenn die angegebene Zeitspanne abläuft, bevor der Agent die Aufgabe abgeschlossen hat.

## <a name="wait_for_one"></a><a name="wait_for_one"></a>wait_for_one

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
Die Anzahl der im Array vorhandenen Agent-Zeiger `_PAgents` .

*_PAgents*<br/>
Ein Array von Zeigern auf die Agents, auf die gewartet werden soll.

*_Status*<br/>
Ein Verweis auf eine Variable, in der der Agentstatus platziert wird.

*_Index*<br/>
Ein Verweis auf eine Variable, in der der agentindex platziert wird.

*_Timeout*<br/>
Die maximale Wartezeit in Millisekunden.

### <a name="remarks"></a>Bemerkungen

Eine agentaufgabe wird abgeschlossen, wenn der Agent in den Zustand `agent_canceled` oder Eintritt `agent_done` .

Wenn der-Parameter `_Timeout` einen anderen Wert als die-Konstante aufweist `COOPERATIVE_TIMEOUT_INFINITE` , wird die Ausnahme [Operation_timed_out](operation-timed-out-class.md) ausgelöst, wenn die angegebene Zeitspanne abläuft, bevor der Agent die Aufgabe abgeschlossen hat.

## <a name="see-also"></a>Weitere Informationen

[Parallelitäts Namespace](concurrency-namespace.md)
