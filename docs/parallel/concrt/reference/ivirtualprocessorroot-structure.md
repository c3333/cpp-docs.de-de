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
ms.openlocfilehash: f642a29d0a80568f7a5f2a5e89f6951d4819243e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364261"
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot-Struktur

Eine Abstraktion für einen Hardwarethread, auf dem ein Threadproxy ausgeführt werden kann.

## <a name="syntax"></a>Syntax

```cpp
struct IVirtualProcessorRoot : public IExecutionResource;
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IVirtualProcessorRoot::Aktivieren](#activate)|Bewirkt, dass der der `pContext` Ausführungskontextschnittstelle zugeordnete Threadproxy mit der Ausführung dieses virtuellen Prozessorstamms beginnt.|
|[IVirtualProcessorRoot::Deactivate](#deactivate)|Bewirkt, dass der Threadproxy, der derzeit auf diesem virtuellen Prozessorstamm ausgeführt wird, den Dispatching des Ausführungskontexts beendet. Der Threadproxy setzt die Ausführung bei `Activate` einem Aufruf der Methode fort.|
|[IVirtualProcessorRoot::EnsureAllTasksVisible](#ensurealltasksvisible)|Bewirkt, dass daten, die in der Speicherhierarchie einzelner Prozessoren gespeichert sind, für alle Prozessoren auf dem System sichtbar werden. Es stellt sicher, dass ein vollständiger Speicherzaun auf allen Prozessoren ausgeführt wurde, bevor die Methode zurückgegeben wird.|
|[IVirtualProcessorRoot::GetId](#getid)|Gibt einen eindeutigen Bezeichner für den Stamm des virtuellen Prozessors zurück.|

## <a name="remarks"></a>Bemerkungen

Jedem virtuellen Prozessorstamm ist eine Ausführungsressource zugeordnet. Die `IVirtualProcessorRoot` Schnittstelle erbt von der [IExecutionResource-Schnittstelle.](iexecutionresource-structure.md) Mehrere virtuelle Prozessorwurzeln können demselben zugrunde liegenden Hardwarethread entsprechen.

Der Ressourcen-Manager gewährt Planern als Reaktion auf Ressourcenanforderungen virtuelle Prozessorstämme. Ein Planer kann einen virtuellen Prozessorstamm verwenden, um Die Arbeit auszuführen, indem er ihn mit einem Ausführungskontext aktiviert.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[IExecutionResource](iexecutionresource-structure.md)

`IVirtualProcessorRoot`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** concrtrm.h

**Namespace:** Parallelität

## <a name="ivirtualprocessorrootactivate-method"></a><a name="activate"></a>IVirtualProcessorRoot::Activate-Methode

Bewirkt, dass der der `pContext` Ausführungskontextschnittstelle zugeordnete Threadproxy mit der Ausführung dieses virtuellen Prozessorstamms beginnt.

```cpp
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parameter

*pContext*<br/>
Eine Schnittstelle zum Ausführungskontext, die auf diesem virtuellen Prozessorstamm ausgelöst wird.

### <a name="remarks"></a>Bemerkungen

Der Ressourcen-Manager stellt einen Threadproxy bereit, wenn der Ausführungskontextschnittstelle nicht zugeordnet ist.`pContext`

Die `Activate` Methode kann verwendet werden, um mit der Ausführung der Arbeit an einem neuen virtuellen Prozessorstamm zu beginnen, der vom Ressourcen-Manager zurückgegeben wird, oder um den Threadproxy auf einem virtuellen Prozessorstamm fortzusetzen, der deaktiviert wurde oder gerade deaktiviert werden soll. Weitere Informationen zur Deaktivierung finden Sie unter [IVirtualProcessorRoot::Deactivate.](#deactivate) Wenn Sie einen deaktivierten virtuellen Prozessorstamm wieder `pContext` verwenden, muss der Parameter mit dem Parameter identisch sein, der zum Deaktivieren des virtuellen Prozessorstamms verwendet wird.

Sobald ein virtueller Prozessorstamm zum ersten Mal aktiviert `Deactivate` wurde, können nachfolgende Paare von Aufrufen an einander `Activate` und können miteinander antreten. Dies bedeutet, dass es für den `Activate` Ressourcen-Manager `Deactivate` akzeptabel ist, einen Anruf zu erhalten, bevor er den Anruf erhält, für den er gedacht war.

Wenn Sie einen virtuellen Prozessorstamm aktivieren, signalisieren Sie dem Ressourcen-Manager, dass dieser Stamm des virtuellen Prozessors derzeit mit der Arbeit beschäftigt ist. Wenn der Planer keine Arbeit für diesen Stamm finden kann, `Deactivate` wird erwartet, dass er die Methode aufruft, die den Ressourcen-Manager darüber informiert, dass sich der Stamm des virtuellen Prozessors im Leerlauf befindet. Der Ressourcen-Manager verwendet diese Daten, um den Lastenausgleich des Systems zu erreichen.

`invalid_argument`wird ausgelöst, `pContext` wenn das `NULL`Argument den Wert hat.

`invalid_operation`wird ausgelöst, `pContext` wenn das Argument nicht den Ausführungskontext darstellt, der zuletzt von diesem virtuellen Prozessorstamm ausgelöst wurde.

Der Akt der Aktivierung eines virtuellen Prozessorstamms erhöht die Abonnementebene des zugrunde liegenden Hardwarethreads um eins. Weitere Informationen zu Abonnementebenen finden Sie unter [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ivirtualprocessorrootdeactivate-method"></a><a name="deactivate"></a>IVirtualProcessorRoot::Deactivate-Methode

Bewirkt, dass der Threadproxy, der derzeit auf diesem virtuellen Prozessorstamm ausgeführt wird, den Dispatching des Ausführungskontexts beendet. Der Threadproxy setzt die Ausführung bei `Activate` einem Aufruf der Methode fort.

```cpp
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parameter

*pContext*<br/>
Der Kontext, der derzeit von diesem Stamm ausgelöst wird.

### <a name="return-value"></a>Rückgabewert

Ein boolescher Wert. Der Wert **true** gibt an, dass `Deactivate` der Threadproxy von `Activate` der Methode als Reaktion auf einen Aufruf der Methode zurückgegeben wurde. Der Wert `false` von gibt an, dass der Threadproxy von der Methode als Reaktion auf ein Benachrichtigungsereignis im Ressourcen-Manager zurückgegeben wurde. Auf einem UMS-Threadplaner (User Mode schedulable) weist dies darauf hin, dass Elemente in der Abschlussliste des Planers angezeigt wurden und der Planer diese verarbeiten muss.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um die Ausführung eines virtuellen Prozessorstamms vorübergehend zu beenden, wenn Sie keine Arbeit in Ihrem Planer finden. Ein Aufruf `Deactivate` der Methode muss `Dispatch` innerhalb der Methode des Ausführungskontexts stammen, mit dem der Stamm des virtuellen Prozessors zuletzt aktiviert wurde. Mit anderen Worten, der Threadproxy, der die `Deactivate` Methode aufruft, muss derjenige sein, der derzeit auf dem Stamm des virtuellen Prozessors ausgeführt wird. Das Aufrufen der Methode auf einem virtuellen Prozessorstamm, den Sie nicht ausführen, kann zu einem undefinierten Verhalten führen.

Ein deaktivierter virtueller Prozessorstamm kann mit einem `Activate` Aufruf der Methode geweckt werden, `Deactivate` mit demselben Argument, das an die Methode übergeben wurde. Der Planer ist dafür verantwortlich, `Activate` sicherzustellen, dass Aufrufe der und `Deactivate` Methoden gekoppelt werden, aber sie müssen nicht in einer bestimmten Reihenfolge empfangen werden. Der Ressourcen-Manager kann den `Activate` Empfang eines Aufrufs der `Deactivate` Methode verarbeiten, bevor er einen Aufruf der Methode empfängt, für die er gedacht war.

Wenn ein virtueller Prozessorstamm erwacht `Deactivate` und der Rückgabewert der Methode der Wert **false**ist, sollte der Planer die UMS-Vervollständigungsliste über die `IUMSCompletionList::GetUnblockNotifications` Methode abfragen, auf diese Informationen reagieren und die `Deactivate` Methode anschließend erneut aufrufen. Dies sollte wiederholt werden, `Deactivate` bis die `true`Methode den Wert zurückgibt.

`invalid_argument`wird ausgelöst, `pContext` wenn das Argument den Wert NULL hat.

`invalid_operation`wird ausgelöst, wenn der Stamm des virtuellen `pContext` Prozessors nie aktiviert wurde oder das Argument nicht den Ausführungskontext darstellt, der zuletzt von diesem virtuellen Prozessorstamm ausgelöst wurde.

Der Akt der Deaktivierung eines virtuellen Prozessorstamms verringert die Abonnementebene des zugrunde liegenden Hardwarethreads um eins. Weitere Informationen zu Abonnementebenen finden Sie unter [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ivirtualprocessorrootensurealltasksvisible-method"></a><a name="ensurealltasksvisible"></a>IVirtualProcessorRoot::EnsureAllTasksVisible-Methode

Bewirkt, dass daten, die in der Speicherhierarchie einzelner Prozessoren gespeichert sind, für alle Prozessoren auf dem System sichtbar werden. Es stellt sicher, dass ein vollständiger Speicherzaun auf allen Prozessoren ausgeführt wurde, bevor die Methode zurückgegeben wird.

```cpp
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parameter

*pContext*<br/>
Der Kontext, der derzeit von diesem virtuellen Prozessorstamm ausgelöst wird.

### <a name="remarks"></a>Bemerkungen

Sie können diese Methode nützlich finden, wenn Sie die Deaktivierung eines virtuellen Prozessorstamms mit dem Hinzufügen neuer Arbeit in den Planer synchronisieren möchten. Aus Leistungsgründen können Sie entscheiden, dem Planer Arbeitsaufgaben hinzuzufügen, ohne eine Speicherbarriere auszuführen, d. h., Arbeitsaufgaben, die von einem Thread hinzugefügt werden, der auf einem Prozessor ausgeführt wird, sind nicht sofort für alle anderen Prozessoren sichtbar. Mit dieser Methode in `Deactivate` Verbindung mit der Methode können Sie sicherstellen, dass der Planer nicht alle virtuellen Prozessorwurzeln deaktiviert, während Arbeitsaufgaben in den Auflistungen des Planers vorhanden sind.

Ein Aufruf `EnsureAllTasksVisibleThe` der Methode muss `Dispatch` innerhalb der Methode des Ausführungskontexts stammen, mit dem der Stamm des virtuellen Prozessors zuletzt aktiviert wurde. Mit anderen Worten, der Threadproxy, der die `EnsureAllTasksVisible` Methode aufruft, muss derjenige sein, der derzeit auf dem Stamm des virtuellen Prozessors ausgeführt wird. Das Aufrufen der Methode auf einem virtuellen Prozessorstamm, den Sie nicht ausführen, kann zu einem undefinierten Verhalten führen.

`invalid_argument`wird ausgelöst, `pContext` wenn das `NULL`Argument den Wert hat.

`invalid_operation`wird ausgelöst, wenn der Stamm des virtuellen `pContext` Prozessors nie aktiviert wurde oder das Argument nicht den Ausführungskontext darstellt, der zuletzt von diesem virtuellen Prozessorstamm ausgelöst wurde.

## <a name="ivirtualprocessorrootgetid-method"></a><a name="getid"></a>IVirtualProcessorRoot::GetId-Methode

Gibt einen eindeutigen Bezeichner für den Stamm des virtuellen Prozessors zurück.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein Ganzzahlbezeichner.

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)
