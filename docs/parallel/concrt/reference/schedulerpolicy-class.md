---
title: SchedulerPolicy-Klasse
ms.date: 11/04/2016
f1_keywords:
- SchedulerPolicy
- concrt/concurrency::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::GetPolicyValue
- concrt/concurrency::SchedulerPolicy::SetConcurrencyLimits
- concrt/concurrency::SchedulerPolicy::SetPolicyValue
helpviewer_keywords:
- SchedulerPolicy class
ms.assetid: bcebf51a-65f8-45a3-809b-d1ff93527dc4
ms.openlocfilehash: b7b99dae2ffb58123c05a65872e4c71e149ac12c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219572"
---
# <a name="schedulerpolicy-class"></a>SchedulerPolicy-Klasse

Die `SchedulerPolicy`-Klasse enthält einen Satz von Schlüssel-Wert-Paaren. Einen für jedes Richtlinienelement, von dem das Verhalten einer Planerinstanz gesteuert wird.

## <a name="syntax"></a>Syntax

```cpp
class SchedulerPolicy;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[SchedulerPolicy](#ctor)|Ist überladen. Erstellt eine neue Scheduler-Richtlinie und füllt sie mit Werten für [Richtlinien Schlüssel](concurrency-namespace-enums.md) auf, die von Concurrency Runtime Planer und der Ressourcen-Manager unterstützt werden.|
|[~ SchedulerPolicy-Dekonstruktor](#dtor)|Zerstört eine Planerrichtlinie.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[GetPolicyValue](#getpolicyvalue)|Ruft den Wert des als `key`-Parameter angegebenen Richtlinienschlüssels ab.|
|[SetConcurrencyLimits](#setconcurrencylimits)|Legt gleichzeitig die `MinConcurrency`-Richtlinie und die `MaxConcurrency`-Richtlinie des `SchedulerPolicy`-Objekts fest.|
|[SetPolicyValue](#setpolicyvalue)|Legt den Wert des Richtlinienschlüssels fest, der als `key`-Parameter angegeben wurde, und gibt den alten Wert zurück.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Operator =](#operator_eq)|Weist die Planerrichtlinie von einer anderen Planerrichtlinie zu.|

## <a name="remarks"></a>Bemerkungen

Weitere Informationen zu den Richtlinien, die mithilfe der-Klasse gesteuert werden können `SchedulerPolicy` , finden Sie unter [PolicyElementKey](concurrency-namespace-enums.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`SchedulerPolicy`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ConcRT. h, concrtrm. h

**Namespace:** Parallelität

## <a name="getpolicyvalue"></a><a name="getpolicyvalue"></a>GetPolicyValue

Ruft den Wert des als `key`-Parameter angegebenen Richtlinienschlüssels ab.

```cpp
unsigned int GetPolicyValue(PolicyElementKey key) const;
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Richtlinien Schlüssel, für den ein Wert abgerufen werden soll.

### <a name="return-value"></a>Rückgabewert

Wenn der vom-Parameter angegebene Schlüssel `key` unterstützt wird, wird der Richtlinien Wert für den Schlüssel in einen umgewandelt **`unsigned int`** .

### <a name="remarks"></a>Bemerkungen

Die Methode löst [Invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) für einen ungültigen Richtlinien Schlüssel aus.

## <a name="operator"></a><a name="operator_eq"></a>Operator =

Weist die Planerrichtlinie von einer anderen Planerrichtlinie zu.

```cpp
SchedulerPolicy& operator= (const SchedulerPolicy& _RhsPolicy);
```

### <a name="parameters"></a>Parameter

*_RhsPolicy*<br/>
Die Richtlinie, die dieser Richtlinie zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf die Scheduler-Richtlinie.

### <a name="remarks"></a>Bemerkungen

Oft ist die zweckmäßigste Art, eine neue Planerrichtlinie zu definieren, das Kopieren einer vorhandenen Richtlinie und das anschließende Bearbeiten mit der `SetPolicyValue`-Methode oder der `SetConcurrencyLimits`-Methode.

## <a name="schedulerpolicy"></a><a name="ctor"></a>SchedulerPolicy

Erstellt eine neue Scheduler-Richtlinie und füllt sie mit Werten für [Richtlinien Schlüssel](concurrency-namespace-enums.md) auf, die von Concurrency Runtime Planer und der Ressourcen-Manager unterstützt werden.

```cpp
SchedulerPolicy();

SchedulerPolicy(
    size_t _PolicyKeyCount,
...);

SchedulerPolicy(
    const SchedulerPolicy& _SrcPolicy);
```

### <a name="parameters"></a>Parameter

*_PolicyKeyCount*<br/>
Die Anzahl der Schlüssel-Wert-Paare, die dem `_PolicyKeyCount`-Parameter folgen.

*_SrcPolicy*<br/>
Die zu kopierende Quellrichtlinie.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor erstellt eine neue Planerrichtlinie, bei der alle Richtlinien mit ihren Standardwerten initialisiert werden.

Der zweite Konstruktor erstellt eine neue Planerrichtlinie, die ein Initialisierungsformat mit benannten Parametern verwendet. Werte, nach dem der `_PolicyKeyCount`-Parameter als Schlüssel-Wert-Paare angegeben wird. Jeder Richtlinienschlüssel, der nicht in diesem Konstruktor angegeben wird, verfügt über seinen Standardwert. Dieser Konstruktor kann die Ausnahmen [Invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md), [Invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) oder [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md)auslösen.

Der dritte Konstruktor ist ein Kopierkonstruktor. Oft ist die zweckmäßigste Art, eine neue Planerrichtlinie zu definieren, das Kopieren einer vorhandenen Richtlinie und das anschließende Bearbeiten mit der `SetPolicyValue`-Methode oder der `SetConcurrencyLimits`-Methode.

## <a name="schedulerpolicy"></a><a name="dtor"></a>~ SchedulerPolicy

Zerstört eine Planerrichtlinie.

```cpp
~SchedulerPolicy();
```

## <a name="setconcurrencylimits"></a><a name="setconcurrencylimits"></a>SetConcurrencyLimits

Legt gleichzeitig die `MinConcurrency`-Richtlinie und die `MaxConcurrency`-Richtlinie des `SchedulerPolicy`-Objekts fest.

```cpp
void SetConcurrencyLimits(
    unsigned int _MinConcurrency,
    unsigned int _MaxConcurrency = MaxExecutionResources);
```

### <a name="parameters"></a>Parameter

*_MinConcurrency*<br/>
Der Wert für den `MinConcurrency` Richtlinien Schlüssel.

*_MaxConcurrency*<br/>
Der Wert für den `MaxConcurrency` Richtlinien Schlüssel.

### <a name="remarks"></a>Bemerkungen

Die Methode löst [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md) aus, wenn der für die `MinConcurrency` Richtlinie angegebene Wert größer ist als der für die `MaxConcurrency` Richtlinie angegebene Wert.

Die-Methode kann auch [Invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) für andere ungültige Werte auslösen.

## <a name="setpolicyvalue"></a><a name="setpolicyvalue"></a>SetPolicyValue

Legt den Wert des Richtlinienschlüssels fest, der als `key`-Parameter angegeben wurde, und gibt den alten Wert zurück.

```cpp
unsigned int SetPolicyValue(
    PolicyElementKey key,
    unsigned int value);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Richtlinien Schlüssel, für den ein Wert festgelegt werden soll.

*value*<br/>
Der Wert, auf den der Richtlinien Schlüssel festgelegt wird.

### <a name="return-value"></a>Rückgabewert

Wenn der vom-Parameter angegebene Schlüssel `key` unterstützt wird, wird der alte Richtlinien Wert für den Schlüssel in einen umgewandelt **`unsigned int`** .

### <a name="remarks"></a>Bemerkungen

Die-Methode löst [Invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) für einen ungültigen Richtlinien Schlüssel oder einen beliebigen Richtlinien Schlüssel aus, dessen Wert nicht durch die-Methode festgelegt werden kann `SetPolicyValue` .

Die-Methode löst [Invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) für einen Wert aus, der für den im-Parameter angegebenen Schlüssel nicht unterstützt wird `key` .

Beachten Sie, dass diese Methode das Festlegen der `MinConcurrency` Richtlinien oder nicht gestattet `MaxConcurrency` . Um diese Werte festzulegen, verwenden Sie die [setkonaccesscylimits](#setconcurrencylimits) -Methode.

## <a name="see-also"></a>Weitere Informationen

[Parallelitäts Namespace](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[CurrentScheduler-Klasse](currentscheduler-class.md)<br/>
[Scheduler-Klasse](scheduler-class.md)<br/>
[Taskplaner](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
