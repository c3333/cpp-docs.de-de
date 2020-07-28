---
title: IVirtualProcessorRoot-Struktur
ms.date: 11/04/2016
f1_keywords:
- IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Activate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Deactivate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::EnsureAllTasksVisible
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::GetId
helpviewer_keywords:
- IVirtualProcessorRoot structure
ms.assetid: 5ef371b8-9e4f-4fef-bb0d-49099693dd2b
ms.openlocfilehash: 869d51144b686dd684f62b337bb90eff8a9a5589
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87193951"
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot-Struktur

Eine Abstraktion für einen Hardwarethread, auf dem ein Threadproxy ausgeführt werden kann.

## <a name="syntax"></a>Syntax

```cpp
struct IVirtualProcessorRoot : public IExecutionResource;
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[IVirtualProcessorRoot:: Aktivierung](#activate)|Bewirkt, dass der Thread Proxy, der der Ausführungs Kontext Schnittstelle zugeordnet ist, mit der Ausführung `pContext` auf diesem virtuellen Prozessor Stamm gestartet wird.|
|[IVirtualProcessorRoot::D eaktivierung](#deactivate)|Bewirkt, dass der Thread Proxy, der derzeit auf diesem virtuellen Prozessor Stamm ausgeführt wird, den Ausführungs Kontext nicht mehr sendet. Der Thread Proxy wird die Ausführung beim Abrufen der-Methode fortsetzen `Activate` .|
|[IVirtualProcessorRoot:: ensurealltasksvisible](#ensurealltasksvisible)|Bewirkt, dass die in der Speicher Hierarchie der einzelnen Prozessoren gespeicherten Daten für alle Prozessoren im System sichtbar werden. Dadurch wird sichergestellt, dass vor der Rückgabe der Methode ein vollständiger arbeitsspeicherfence auf allen Prozessoren ausgeführt wurde.|
|[IVirtualProcessorRoot:: GetId](#getid)|Gibt einen eindeutigen Bezeichner für den Stamm des virtuellen Prozessors zurück.|

## <a name="remarks"></a>Bemerkungen

Jedem virtuellen Prozessor Stamm ist eine Ausführungs Ressource zugeordnet. Die- `IVirtualProcessorRoot` Schnittstelle erbt von der [IExecutionResource](iexecutionresource-structure.md) -Schnittstelle. Mehrere virtuelle Prozessor Stämme entsprechen möglicherweise dem gleichen zugrunde liegenden Hardware Thread.

Der Ressourcen-Manager gibt Zeit Planungs Modulen virtuelle Prozessor Stämme als Reaktion auf Ressourcenanforderungen. Ein Planer kann einen virtuellen Prozessor Stamm zum Ausführen von Arbeiten verwenden, indem er ihn mit einem Ausführungs Kontext aktiviert.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[IExecutionResource](iexecutionresource-structure.md)

`IVirtualProcessorRoot`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** concrtrm. h

**Namespace:** Parallelität

## <a name="ivirtualprocessorrootactivate-method"></a><a name="activate"></a>IVirtualProcessorRoot:: Aktivierungs-Methode

Bewirkt, dass der Thread Proxy, der der Ausführungs Kontext Schnittstelle zugeordnet ist, mit der Ausführung `pContext` auf diesem virtuellen Prozessor Stamm gestartet wird.

```cpp
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parameter

*pContext*<br/>
Eine Schnittstelle zum Ausführungs Kontext, die auf diesem virtuellen Prozessor Stamm verteilt wird.

### <a name="remarks"></a>Bemerkungen

Der Ressourcen-Manager wird einen Thread Proxy bereitstellen, wenn dieser der Ausführungs Kontext Schnittstelle nicht zugeordnet ist.`pContext`

Die- `Activate` Methode kann verwendet werden, um mit der Ausführung von Arbeiten an einem neuen virtuellen Prozessor Stamm, der vom Ressourcen-Manager zurückgegeben wird, oder zum Fortsetzen des Thread Proxys in einem virtuellen Prozessor Stamm, der deaktiviert wurde oder gerade deaktiviert wird. Weitere Informationen zur Deaktivierung finden Sie unter [IVirtualProcessorRoot::D eaktivierung](#deactivate) . Wenn Sie einen deaktivierten virtuellen Prozessor Stamm wieder aufnehmen, muss der Parameter `pContext` mit dem Parameter identisch sein, der zum Deaktivieren des virtuellen Prozessor Stamms verwendet wird.

Nachdem der Stamm eines virtuellen Prozessors zum ersten Mal aktiviert wurde, können nachfolgende Paare von Aufrufen von `Deactivate` und `Activate` mit einander aufrüsten. Dies bedeutet, dass die Ressourcen-Manager einen-Rückruf empfangen kann, `Activate` bevor Sie den-Befehl empfängt, `Deactivate` für den Sie gedacht war.

Wenn Sie einen virtuellen Prozessor Stamm aktivieren, signalisieren Sie den Ressourcen-Manager, dass dieser virtuelle Prozessor Stamm derzeit ausgelastet ist. Wenn Ihr Planer keine für diesen Stamm auszuführenden Aufgaben finden kann, wird erwartet, dass die-Methode aufgerufen wird, um `Deactivate` die Ressourcen-Manager zu informieren, dass sich der virtuelle Prozessor Stamm im Leerlauf befindet. Der Ressourcen-Manager verwendet diese Daten für den Lastenausgleich des Systems.

`invalid_argument`wird ausgelöst, wenn das-Argument `pContext` den Wert hat `NULL` .

`invalid_operation`wird ausgelöst, wenn das-Argument `pContext` nicht den Ausführungs Kontext darstellt, der zuletzt von diesem virtuellen Prozessor Stamm gesendet wurde.

Durch das Aktivieren eines virtuellen Prozessor Stamms wird die Abonnement Ebene des zugrunde liegenden Hardware Threads um 1 erhöht. Weitere Informationen zu Abonnement Ebenen finden Sie unter [IExecutionResource:: currentabonneptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ivirtualprocessorrootdeactivate-method"></a><a name="deactivate"></a>IVirtualProcessorRoot::D eaktivierungs Methode

Bewirkt, dass der Thread Proxy, der derzeit auf diesem virtuellen Prozessor Stamm ausgeführt wird, den Ausführungs Kontext nicht mehr sendet. Der Thread Proxy wird die Ausführung beim Abrufen der-Methode fortsetzen `Activate` .

```cpp
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parameter

*pContext*<br/>
Der Kontext, der zurzeit von diesem Stamm gesendet wird.

### <a name="return-value"></a>Rückgabewert

Ein boolescher Wert. **`true`** Der Wert gibt an, dass der Thread Proxy, der von der-Methode zurückgegeben wurde `Deactivate` , als Reaktion auf einen-Rückruf der- `Activate` Methode. **`false`** Der Wert gibt an, dass der Thread Proxy, der von der-Methode zurückgegeben wird, als Reaktion auf ein Benachrichtigungs Ereignis in der Ressourcen-Manager. In einem im Benutzermodus planbarer (ums) Thread Planer ist dies ein Hinweis darauf, dass Elemente in der Vervollständigungsliste des Schedulers angezeigt werden und der Scheduler diese verarbeiten muss.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um die Ausführung eines virtuellen Prozessor Stamms vorübergehend zu beenden, wenn Sie keine Arbeit im Scheduler finden. Ein Aufrufe der- `Deactivate` Methode muss aus der- `Dispatch` Methode des Ausführungs Kontexts stammen, mit dem der virtuelle Prozessor Stamm zuletzt aktiviert wurde. Anders ausgedrückt: der Thread Proxy, der die `Deactivate` Methode aufruft, muss der Thread Proxy sein, der zurzeit auf dem Stamm des virtuellen Prozessors ausgeführt wird. Das Aufrufen der-Methode für einen virtuellen Prozessor Stamm, den Sie nicht ausführen, kann zu undefiniertem Verhalten führen.

Ein deaktivierter virtueller Prozessor Stamm kann mit einem Rückruf der-Methode reaktiviert werden `Activate` , und zwar mit demselben Argument, das an die-Methode übermittelt wurde `Deactivate` . Der Planer ist dafür verantwortlich, sicherzustellen, dass Aufrufe der `Activate` -Methode und der- `Deactivate` Methode gekoppelt sind, aber nicht in einer bestimmten Reihenfolge empfangen werden müssen. Der Ressourcen-Manager kann den Empfang eines Aufrufes-Methoden Handles verarbeiten, `Activate` bevor er einen aufzurufenden Methoden aufzurufen `Deactivate` .

Wenn ein virtueller Prozessor Stamm erwacht und der Rückgabewert der- `Deactivate` Methode der Wert ist **`false`** , sollte der Planer die ums-Vervollständigungsliste über die- `IUMSCompletionList::GetUnblockNotifications` Methode Abfragen, diese Informationen verarbeiten und anschließend die- `Deactivate` Methode erneut aufzurufen. Dieser Wert sollte bis zu diesem Zeitpunkt wiederholt werden, wenn die `Deactivate` Methode den Wert zurückgibt **`true`** .

`invalid_argument`wird ausgelöst, wenn das-Argument `pContext` den Wert NULL aufweist.

`invalid_operation`wird ausgelöst, wenn der virtuelle Prozessor Stamm nie aktiviert wurde, oder das-Argument `pContext` stellt nicht den Ausführungs Kontext dar, der zuletzt von diesem virtuellen Prozessor Stamm gesendet wurde.

Der Vorgang der Deaktivierung eines virtuellen Prozessor Stamms verringert die Abonnement Ebene des zugrunde liegenden Hardware Threads um 1. Weitere Informationen zu Abonnement Ebenen finden Sie unter [IExecutionResource:: currentabonneptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ivirtualprocessorrootensurealltasksvisible-method"></a><a name="ensurealltasksvisible"></a>IVirtualProcessorRoot:: ensurealltasksvisible-Methode

Bewirkt, dass die in der Speicher Hierarchie der einzelnen Prozessoren gespeicherten Daten für alle Prozessoren im System sichtbar werden. Dadurch wird sichergestellt, dass vor der Rückgabe der Methode ein vollständiger arbeitsspeicherfence auf allen Prozessoren ausgeführt wurde.

```cpp
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parameter

*pContext*<br/>
Der Kontext, der zurzeit von diesem virtuellen Prozessor Stamm gesendet wird.

### <a name="remarks"></a>Bemerkungen

Diese Methode kann nützlich sein, wenn Sie die Deaktivierung eines virtuellen Prozessor Stamms mit dem Hinzufügen neuer Aufgaben in den Scheduler synchronisieren möchten. Aus Leistungsgründen können Sie dem Scheduler Arbeitselemente hinzufügen, ohne eine Arbeitsspeicher Barriere auszuführen. Dies bedeutet, dass Arbeitselemente, die von einem Thread hinzugefügt werden, der auf einem Prozessor ausgeführt wird, nicht sofort für alle anderen Prozessoren sichtbar sind. Wenn Sie diese Methode in Verbindung mit der `Deactivate` -Methode verwenden, können Sie sicherstellen, dass Ihr Scheduler nicht alle seine virtuellen Prozessor Stämme deaktiviert, wenn Arbeitselemente in den Auflistungen des Schedulers vorhanden sind.

Ein Aufrufe der- `EnsureAllTasksVisibleThe` Methode muss aus der- `Dispatch` Methode des Ausführungs Kontexts stammen, mit dem der virtuelle Prozessor Stamm zuletzt aktiviert wurde. Anders ausgedrückt: der Thread Proxy, der die `EnsureAllTasksVisible` Methode aufruft, muss der Thread Proxy sein, der zurzeit auf dem Stamm des virtuellen Prozessors ausgeführt wird. Das Aufrufen der-Methode für einen virtuellen Prozessor Stamm, den Sie nicht ausführen, kann zu undefiniertem Verhalten führen.

`invalid_argument`wird ausgelöst, wenn das-Argument `pContext` den Wert hat `NULL` .

`invalid_operation`wird ausgelöst, wenn der virtuelle Prozessor Stamm nie aktiviert wurde, oder das-Argument `pContext` stellt nicht den Ausführungs Kontext dar, der zuletzt von diesem virtuellen Prozessor Stamm gesendet wurde.

## <a name="ivirtualprocessorrootgetid-method"></a><a name="getid"></a>IVirtualProcessorRoot:: GetId-Methode

Gibt einen eindeutigen Bezeichner für den Stamm des virtuellen Prozessors zurück.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein ganzzahliger Bezeichner.

## <a name="see-also"></a>Weitere Informationen

[Parallelitäts Namespace](concurrency-namespace.md)
