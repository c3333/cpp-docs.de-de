---
title: Context-Klasse
ms.date: 11/04/2016
f1_keywords:
- Context
- CONCRT/concurrency::Context
- CONCRT/concurrency::Context::Block
- CONCRT/concurrency::Context::CurrentContext
- CONCRT/concurrency::Context::GetId
- CONCRT/concurrency::Context::GetScheduleGroupId
- CONCRT/concurrency::Context::GetVirtualProcessorId
- CONCRT/concurrency::Context::Id
- CONCRT/concurrency::Context::IsCurrentTaskCollectionCanceling
- CONCRT/concurrency::Context::IsSynchronouslyBlocked
- CONCRT/concurrency::Context::Oversubscribe
- CONCRT/concurrency::Context::ScheduleGroupId
- CONCRT/concurrency::Context::Unblock
- CONCRT/concurrency::Context::VirtualProcessorId
- CONCRT/concurrency::Context::Yield
helpviewer_keywords:
- Context class
ms.assetid: c0d553f3-961d-4ecd-9a29-4fa4351673b8
ms.openlocfilehash: 7c47d9db64b0af7d5413abed3f85e9d41a591fa2
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865492"
---
# <a name="context-class"></a>Context-Klasse

Stellt eine Abstraktion für einen Ausführungskontext dar.

## <a name="syntax"></a>Syntax

```cpp
class Context;
```

## <a name="members"></a>Members

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[~ Context-debugtor](#dtor)||

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Block](#block)|Blockiert den aktuellen Kontext.|
|[CurrentContext](#currentcontext)|Gibt einen Zeiger auf den aktuellen Kontext zurück.|
|[GetId](#getid)|Gibt einen Bezeichner für den Kontext zurück, der innerhalb des Planers eindeutig ist, zu dem der Kontext gehört.|
|[GetScheduleGroupId](#getschedulegroupid)|Gibt einen Bezeichner für die Planungsgruppe zurück, an der der Kontext gerade arbeitet.|
|[GetVirtualProcessorId](#getvirtualprocessorid)|Gibt einen Bezeichner für den virtuellen Prozessor zurück, auf dem der Kontext gerade ausgeführt wird.|
|[Id](#id)|Gibt einen Bezeichner für den aktuellen Kontext zurück, der innerhalb des Planers eindeutig ist, zu dem der aktuelle Kontext gehört.|
|[IsCurrentTaskCollectionCanceling](#iscurrenttaskcollectioncanceling)|Gibt zurück, ob die Aufgabenauflistung, die gerade inline für den aktuellen Kontext ausgeführt wird, in diesem Moment (oder in Kürze) einen Abbruch durchführt.|
|[IsSynchronouslyBlocked](#issynchronouslyblocked)|Bestimmt, ob der Kontext synchron blockiert ist. Ein Kontext wird als synchron blockiert angesehen, wenn er explizit eine zu einer Blockierung führende Aktion ausgeführt hat.|
|[Oversubscribe](#oversubscribe)|Fügt einen zusätzlichen virtuellen Prozessor für die Dauer eines Codeblocks in einen Planer ein, wenn er für einen Kontext aufgerufen wird, der auf einem der virtuellen Prozessoren in diesem Planer ausgeführt wird.|
|[ScheduleGroupId](#schedulegroupid)|Gibt einen Bezeichner für die Planungsgruppe zurück, an der der aktuelle Kontext arbeitet.|
|[Blockierung](#unblock)|Hebt die Blockierung des Kontexts auf und bewirkt, dass er ausführbar wird.|
|[VirtualProcessorId](#virtualprocessorid)|Gibt einen Bezeichner für den virtuellen Prozessor zurück, auf dem der aktuelle Kontext ausgeführt wird.|
|[Yield](#yield)|Setzt die Ausführung aus, damit ein anderer Kontext ausgeführt werden kann. Wenn kein anderer Kontext für eine Übergabe verfügbar ist, kann der Planer ggf. an einen anderen Betriebssystemthread übergeben.|

## <a name="remarks"></a>Bemerkungen

Der Concurrency Runtime Planer (siehe [Scheduler](scheduler-class.md)) verwendet Ausführungs Kontexte, um die von der Anwendung in die Warteschlange eingereihte Arbeit auszuführen. Ein Win32-Thread ist ein Beispiel für einen Ausführungskontext auf einem Windows-Betriebssystem.

Die Nebenläufigkeitsebene eines Planers ist immer gleich der Anzahl virtueller Prozessoren, die vom Ressourcen-Manager gewährt wurden. Ein virtueller Prozessor ist eine Abstraktion für eine Verarbeitungsressource und wird einem Hardwarethread des zugrunde liegenden Systems zugeordnet. Nur ein einzelner Planerkontext kann jeweils auf einem virtuellen Prozessor ausgeführt werden.

Der Planer ist grundsätzlich kooperativ, und ein Ausführungskontext kann seinen virtuellen Prozessor jederzeit für einen anderen Kontext freigeben, wenn er in einen Wartezustand wechseln möchte. Wenn der Wartevorgang erfüllt wurde, kann solange keine Fortsetzung erfolgen, bis ein verfügbarer virtueller Prozessor vom Planer mit der Ausführung beginnt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`Context`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ConcRT. h

**Namespace:** Parallelität

## <a name="block"></a>Baustein

Blockiert den aktuellen Kontext.

```cpp
static void __cdecl Block();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode führt dazu, dass der Standardplaner des Prozesses erstellt und/oder an den aufrufenden Kontext angefügt wird, wenn derzeit dem aufrufenden Kontext kein Planer zugeordnet ist.

Wenn der Aufruf Kontext auf einem virtuellen Prozessor ausgeführt wird, findet der virtuelle Prozessor einen anderen ausführbaren Kontext, der ausgeführt werden kann, oder er kann potenziell einen neuen erstellen.

Nachdem die `Block`-Methode aufgerufen wurde oder aufgerufen wird, müssen Sie Sie mit einem Aufruf der [Unblock](#unblock) -Methode von einem anderen Ausführungs Kontext koppeln, damit Sie erneut ausgeführt werden kann. Beachten Sie, dass es einen kritischen Zeitraum zwischen dem Punkt gibt, an dem Ihr Code den Kontext veröffentlicht, damit ein anderer Thread die `Unblock`-Methode und den Punkt, an dem der tatsächliche Methodenaufruf an `Block` erfolgt, aufruft. Während dieses Zeitraums dürfen Sie keine Methode aufzurufen, die wiederum aus eigenen Gründen blockieren und die Blockierung blockieren kann (z. b. das Abrufen einer Sperre). Bei Aufrufen der `Block`-und `Unblock`-Methode wird der Grund für die Blockierung und Aufhebung der Blockierung nicht nachverfolgt. Nur ein Objekt muss den Besitz eines `Block`- `Unblock` Paar haben.

Diese Methode kann eine Vielzahl von Ausnahmen auslösen, einschließlich [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md).

## <a name="dtor"></a>~ Kontext

```cpp
virtual ~Context();
```

## <a name="currentcontext"></a>CurrentContext

Gibt einen Zeiger auf den aktuellen Kontext zurück.

```cpp
static Context* __cdecl CurrentContext();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den aktuellen Kontext.

### <a name="remarks"></a>Bemerkungen

Diese Methode führt dazu, dass der Standardplaner des Prozesses erstellt und/oder an den aufrufenden Kontext angefügt wird, wenn derzeit dem aufrufenden Kontext kein Planer zugeordnet ist.

## <a name="getid"></a>GetId

Gibt einen Bezeichner für den Kontext zurück, der innerhalb des Planers eindeutig ist, zu dem der Kontext gehört.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein Bezeichner für den Kontext, der innerhalb des Planers eindeutig ist, zu dem der Kontext gehört.

## <a name="getschedulegroupid"></a>GetScheduleGroupId

Gibt einen Bezeichner für die Planungsgruppe zurück, an der der Kontext gerade arbeitet.

```cpp
virtual unsigned int GetScheduleGroupId() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein Bezeichner für die Zeit Plan Gruppe, an der der Kontext gerade arbeitet.

### <a name="remarks"></a>Bemerkungen

Der Rückgabewert dieser Methode ist eine sofortige Stichprobe der Zeit Plan Gruppe, in der der Kontext ausgeführt wird. Wenn diese Methode in einem anderen Kontext als dem aktuellen Kontext aufgerufen wird, kann der Wert in dem Moment, in dem er zurückgegeben wird, veraltet sein, und er kann nicht darauf basieren. Diese Methode wird in der Regel nur zum Debuggen oder zum Ablauf Verfolgungs Zweck verwendet.

## <a name="getvirtualprocessorid"></a>GetVirtualProcessorId

Gibt einen Bezeichner für den virtuellen Prozessor zurück, auf dem der Kontext gerade ausgeführt wird.

```cpp
virtual unsigned int GetVirtualProcessorId() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Wenn der Kontext zurzeit auf einem virtuellen Prozessor ausgeführt wird, ein Bezeichner für den virtuellen Prozessor, auf dem der Kontext derzeit ausgeführt wird; Andernfalls wird der Wert `-1`.

### <a name="remarks"></a>Bemerkungen

Der Rückgabewert dieser Methode ist eine sofortige Stichprobe des virtuellen Prozessors, auf dem der Kontext ausgeführt wird. Dieser Wert kann in dem Moment, in dem er zurückgegeben wird, veraltet sein und nicht mehr verlassen werden. Diese Methode wird in der Regel nur zum Debuggen oder zum Ablauf Verfolgungs Zweck verwendet.

## <a name="id"></a>Name

Gibt einen Bezeichner für den aktuellen Kontext zurück, der innerhalb des Planers eindeutig ist, zu dem der aktuelle Kontext gehört.

```cpp
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>Rückgabewert

, Wenn der aktuelle Kontext an einen Planer angefügt ist, ein Bezeichner für den aktuellen Kontext, der innerhalb des Planers eindeutig ist, zu dem der aktuelle Kontext gehört. Andernfalls wird der Wert `-1`.

## <a name="iscurrenttaskcollectioncanceling"></a>IsCurrentTaskCollectionCanceling

Gibt zurück, ob die Aufgabenauflistung, die gerade inline für den aktuellen Kontext ausgeführt wird, in diesem Moment (oder in Kürze) einen Abbruch durchführt.

```cpp
static bool __cdecl IsCurrentTaskCollectionCanceling();
```

### <a name="return-value"></a>Rückgabewert

Wenn ein Scheduler an den aufrufenden Kontext angefügt wird und eine Aufgaben Gruppe eine Aufgabe Inline in diesem Kontext ausführt, gibt dies Aufschluss darüber, ob sich diese Aufgaben Gruppe in der Mitte eines aktiven Abbruchs befindet (oder in Kürze). Andernfalls wird der Wert `false`.

## <a name="issynchronouslyblocked"></a>IsSynchronouslyBlocked

Bestimmt, ob der Kontext synchron blockiert ist. Ein Kontext wird als synchron blockiert angesehen, wenn er explizit eine zu einer Blockierung führende Aktion ausgeführt hat.

```cpp
virtual bool IsSynchronouslyBlocked() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Gibt an, ob der Kontext synchron blockiert wird.

### <a name="remarks"></a>Bemerkungen

Ein Kontext wird als synchron blockiert angesehen, wenn er explizit eine zu einer Blockierung führende Aktion ausgeführt hat. Auf dem Thread Planer würde dies auf einen direkten Aufrufder `Context::Block`-Methode oder ein Synchronisierungs Objekt hindeuten, das mit der `Context::Block`-Methode erstellt wurde.

Der Rückgabewert dieser Methode ist ein sofortiges Beispiel dafür, ob der Kontext synchron blockiert wird. Dieser Wert ist möglicherweise veraltet, wenn er zurückgegeben wird und nur unter sehr spezifischen Umständen verwendet werden kann.

## <a name="operator_delete"></a>Operator löschen

Ein `Context`-Objekt wird von der Common Language Runtime intern zerstört. Sie kann nicht explizit gelöscht werden.

```cpp
void operator delete(void* _PObject);
```

### <a name="parameters"></a>Parameter

*_PObject*<br/>
Ein Zeiger auf das Objekt, das gelöscht werden soll.

## <a name="oversubscribe"></a>Oversubscribe

Fügt einen zusätzlichen virtuellen Prozessor für die Dauer eines Codeblocks in einen Planer ein, wenn er für einen Kontext aufgerufen wird, der auf einem der virtuellen Prozessoren in diesem Planer ausgeführt wird.

```cpp
static void __cdecl Oversubscribe(bool _BeginOversubscription);
```

### <a name="parameters"></a>Parameter

*_BeginOversubscription*<br/>
Wenn der Wert **true**ist, ein Hinweis darauf, dass für die Dauer der Überzeichnung ein zusätzlicher virtueller Prozessor hinzugefügt werden soll. Wenn der Wert **false**ist, ein Hinweis darauf, dass die Überzeichnung enden soll und der zuvor hinzugefügte virtuelle Prozessor entfernt werden sollte.

## <a name="schedulegroupid"></a>ScheduleGroupId

Gibt einen Bezeichner für die Planungsgruppe zurück, an der der aktuelle Kontext arbeitet.

```cpp
static unsigned int __cdecl ScheduleGroupId();
```

### <a name="return-value"></a>Rückgabewert

Wenn der aktuelle Kontext an einen Planer angefügt und an einer Zeit Plan Gruppe arbeitet, ein Bezeichner für die Planergruppe, an der der aktuelle Kontext arbeitet. Andernfalls wird der Wert `-1`.

## <a name="unblock"></a>Blockierung

Hebt die Blockierung des Kontexts auf und bewirkt, dass er ausführbar wird.

```cpp
virtual void Unblock() = 0;
```

### <a name="remarks"></a>Bemerkungen

Es ist durchaus zulässig, dass ein aufrufungs Vorgang der `Unblock`-Methode vor einem entsprechenden aufrufungs Vorgang der [Block](#block) -Methode erfolgt. Solange Aufrufe an die Methoden `Block` und `Unblock` ordnungsgemäß gekoppelt sind, verarbeitet die Laufzeit das natürliche Race der beiden Reihenfolge ordnungsgemäß. Ein `Unblock`-Aufrufe, der vor einem `Block` aufgerufen wird, negiert einfach die Auswirkung des `Block`-Aufrufes.

Es gibt mehrere Ausnahmen, die von dieser Methode ausgelöst werden können. Wenn ein Kontext versucht, die `Unblock` Methode für sich selbst aufzurufen, wird eine [context_self_unblock](context-self-unblock-class.md) Ausnahme ausgelöst. Wenn Aufrufe von `Block` und `Unblock` nicht ordnungsgemäß gekoppelt sind (z. b. werden zwei Aufrufe von `Unblock` für einen Kontext erfolgen, der derzeit ausgeführt wird), wird eine [context_unblock_unbalanced](context-unblock-unbalanced-class.md) Ausnahme ausgelöst.

Beachten Sie, dass es einen kritischen Zeitraum zwischen dem Punkt gibt, an dem Ihr Code den Kontext veröffentlicht, damit ein anderer Thread die `Unblock`-Methode und den Punkt, an dem der tatsächliche Methodenaufruf an `Block` erfolgt, aufruft. Während dieses Zeitraums dürfen Sie keine Methode aufzurufen, die wiederum aus eigenen Gründen blockieren und die Blockierung blockieren kann (z. b. das Abrufen einer Sperre). Bei Aufrufen der `Block`-und `Unblock`-Methode wird der Grund für die Blockierung und Aufhebung der Blockierung nicht nachverfolgt. Nur ein Objekt muss den Besitz eines `Block`-und `Unblock` Paars haben.

## <a name="virtualprocessorid"></a>VirtualProcessorId

Gibt einen Bezeichner für den virtuellen Prozessor zurück, auf dem der aktuelle Kontext ausgeführt wird.

```cpp
static unsigned int __cdecl VirtualProcessorId();
```

### <a name="return-value"></a>Rückgabewert

, Wenn der aktuelle Kontext an einen Planer angefügt ist, ein Bezeichner für den virtuellen Prozessor, auf dem der aktuelle Kontext ausgeführt wird. Andernfalls wird der Wert `-1`.

### <a name="remarks"></a>Bemerkungen

Der Rückgabewert dieser Methode ist eine sofortige Stichprobe des virtuellen Prozessors, auf dem der aktuelle Kontext ausgeführt wird. Dieser Wert kann in dem Moment, in dem er zurückgegeben wird, veraltet sein und nicht mehr verlassen werden. Diese Methode wird in der Regel nur zum Debuggen oder zum Ablauf Verfolgungs Zweck verwendet.

## <a name="yield"></a>Yield

Setzt die Ausführung aus, damit ein anderer Kontext ausgeführt werden kann. Wenn kein anderer Kontext für eine Übergabe verfügbar ist, kann der Planer ggf. an einen anderen Betriebssystemthread übergeben.

```cpp
static void __cdecl Yield();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode führt dazu, dass der Standardplaner des Prozesses erstellt und/oder an den aufrufenden Kontext angefügt wird, wenn derzeit dem aufrufenden Kontext kein Planer zugeordnet ist.

## <a name="yieldexecution"></a>YieldExecution

Setzt die Ausführung aus, damit ein anderer Kontext ausgeführt werden kann. Wenn kein anderer Kontext für eine Übergabe verfügbar ist, kann der Planer ggf. an einen anderen Betriebssystemthread übergeben.

```cpp
static void __cdecl YieldExecution();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode führt dazu, dass der Standardplaner des Prozesses erstellt und/oder an den aufrufenden Kontext angefügt wird, wenn derzeit dem aufrufenden Kontext kein Planer zugeordnet ist.

Diese Funktion ist neu in Visual Studio 2015 und ist mit der [Yield](#yield) -Funktion identisch, steht jedoch nicht in Konflikt mit dem Yield-Makro in Windows. h.

## <a name="see-also"></a>Weitere Informationen

[Concurrency-Namespace](concurrency-namespace.md)<br/>
[Scheduler-Klasse](scheduler-class.md)<br/>
[Aufgabenplanung](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
