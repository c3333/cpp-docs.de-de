---
title: task_options-Klasse (Concurrency Runtime)
ms.date: 11/04/2016
f1_keywords:
- ppltasks/concurrency::task_options
ms.assetid: f93d146b-70f7-46ec-8c2f-c33b8bb0af69
ms.openlocfilehash: e79dd7979b587ae807c8984a04b79be362b03758
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368598"
---
# <a name="task_options-class-concurrency-runtime"></a>task_options-Klasse (Concurrency Runtime)

Stellt die zulässigen Optionen zum Erstellen einer Aufgabe dar

## <a name="syntax"></a>Syntax

```cpp
class task_options;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[task_options::task_options-Konstruktor (Concurrency Runtime)](#ctor)|Ist überladen. Standardliste von Aufgabenerstellungsoptionen|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[task_options::get_cancellation_token-Methode (Concurrency Runtime)](#get_cancellation_token)|Gibt das Abbruchtoken zurück.|
|[task_options::get_continuation_context-Methode (Concurrency Runtime)](#get_continuation_context)|Gibt den Fortsetzungskontext zurück.|
|[task_options::get_scheduler-Methode (Concurrency Runtime)](#get_scheduler)|Gibt den Planer zurück.|
|[task_options::has_cancellation_token-Methode (Concurrency Runtime)](#has_cancellation_token)|Gibt an, ob ein Abbruchtoken vom Benutzer angegeben wurde.|
|[task_options::has_scheduler-Methode (Concurrency Runtime)](#has_scheduler)|Gibt an, ob ein Planer vom Benutzer angegeben wurde.|
|[task_options::set_cancellation_token-Methode (Concurrency Runtime)](#set_cancellation_token)|Legt das angegebene Token in den Optionen fest.|
|[task_options::set_continuation_context-Methode (Concurrency Runtime)](#set_continuation_context)|Legt den angegebenen Fortsetzungskontext in den Optionen fest.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`task_options`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** ppltasks.h

**Namespace:** Parallelität

## <a name="task_optionsget_cancellation_token-method-concurrency-runtime"></a><a name="get_cancellation_token"></a>task_options::get_cancellation_token-Methode (Concurrency Runtime)

Gibt das Abbruchtoken zurück.

```cpp
cancellation_token get_cancellation_token() const;
```

### <a name="return-value"></a>Rückgabewert

## <a name="task_optionsget_continuation_context-method-concurrency-runtime"></a><a name="get_continuation_context"></a>task_options::get_continuation_context-Methode (Parallelitätslaufzeit)

Gibt den Fortsetzungskontext zurück.

```cpp
task_continuation_context get_continuation_context() const;
```

### <a name="return-value"></a>Rückgabewert

## <a name="task_optionsget_scheduler-method-concurrency-runtime"></a><a name="get_scheduler"></a>task_options::get_scheduler-Methode (Concurrency Runtime)

Gibt den Planer zurück.

```cpp
scheduler_ptr get_scheduler() const;
```

### <a name="return-value"></a>Rückgabewert

## <a name="task_optionshas_cancellation_token-method-concurrency-runtime"></a><a name="has_cancellation_token"></a>task_options::has_cancellation_token-Methode (Concurrency Runtime)

Gibt an, ob ein Abbruchtoken vom Benutzer angegeben wurde.

```cpp
bool has_cancellation_token() const;
```

### <a name="return-value"></a>Rückgabewert

## <a name="task_optionshas_scheduler-method-concurrency-runtime"></a><a name="has_scheduler"></a>task_options::has_scheduler-Methode (Concurrency Runtime)

Gibt an, ob ein Planer vom Benutzer angegeben wurde.

```cpp
bool has_scheduler() const;
```

### <a name="return-value"></a>Rückgabewert

## <a name="task_optionsset_cancellation_token-method-concurrency-runtime"></a><a name="set_cancellation_token"></a>task_options::set_cancellation_token-Methode (Concurrency Runtime)

Legt das angegebene Token in den Optionen fest.

```cpp
void set_cancellation_token(cancellation_token _Token);
```

### <a name="parameters"></a>Parameter

`_Token`

## <a name="task_optionsset_continuation_context-method-concurrency-runtime"></a><a name="set_continuation_context"></a>task_options::set_continuation_context-Methode (Concurrency Runtime)

Legt den angegebenen Fortsetzungskontext in den Optionen fest.

```cpp
void set_continuation_context(task_continuation_context _ContinuationContext);
```

### <a name="parameters"></a>Parameter

`_ContinuationContext`

## <a name="task_optionstask_options-constructor-concurrency-runtime"></a><a name="ctor"></a>task_options::task_options Konstruktor (Parallelitätslaufzeit)

Standardliste von Aufgabenerstellungsoptionen

```cpp
task_options();

task_options(
    cancellation_token _Token);

task_options(
    task_continuation_context _ContinuationContext);

task_options(
    cancellation_token _Token,
    task_continuation_context _ContinuationContext);

template<typename _SchedType>
task_options(
    std::shared_ptr<_SchedType> _Scheduler);

task_options(
    scheduler_interface& _Scheduler);

task_options(
    scheduler_ptr _Scheduler);

task_options(
    const task_options& _TaskOptions);
```

### <a name="parameters"></a>Parameter

`_SchedType`

`_Token`

`_ContinuationContext`

`_Scheduler`

`_TaskOptions`

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)
