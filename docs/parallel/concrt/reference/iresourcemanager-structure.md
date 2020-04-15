---
title: IResourceManager-Struktur
ms.date: 03/27/2019
f1_keywords:
- IResourceManager
- CONCRTRM/concurrency::IResourceManager
- CONCRTRM/concurrency::IResourceManager::IResourceManager::OSVersion
- CONCRTRM/concurrency::IResourceManager::IResourceManager::CreateNodeTopology
- CONCRTRM/concurrency::IResourceManager::IResourceManager::GetAvailableNodeCount
- CONCRTRM/concurrency::IResourceManager::IResourceManager::GetFirstNode
- CONCRTRM/concurrency::IResourceManager::IResourceManager::Reference
- CONCRTRM/concurrency::IResourceManager::IResourceManager::RegisterScheduler
- CONCRTRM/concurrency::IResourceManager::IResourceManager::Release
helpviewer_keywords:
- IResourceManager structure
ms.assetid: 3dd5ec2c-fe53-4121-ae77-1bc1d1167ff4
ms.openlocfilehash: 15e27a586fc039791255c01a053f6a1109183f90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368190"
---
# <a name="iresourcemanager-structure"></a>IResourceManager-Struktur

Eine Schnittstelle zum Ressourcen-Manager der Concurrency Runtime. Dies ist die Schnittstelle, über die Planer mit dem Ressourcen-Manager kommunizieren.

## <a name="syntax"></a>Syntax

```cpp
struct IResourceManager;
```

## <a name="members"></a>Member

### <a name="public-enumerations"></a>Öffentliche Enumerationen

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IResourceManager::OSVersion](#osversion)|Ein enumerierter Typ, der die Betriebssystemversion darstellt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IResourceManager::CreateNodeTopology](#createnodetopology)|Diese Methode, die nur in Debugbuilds der Laufzeit vorhanden ist, ist ein Test-Hook, der das Testen des Resource Managers auf unterschiedlichen Hardwaretopologien erleichtert, ohne dass die tatsächliche Hardware erforderlich ist, die mit der Konfiguration übereinstimmt. Bei Einzelhandelsbuilds der Laufzeit wird diese Methode zurückgegeben, ohne dass eine Aktion ausgeführt wird.|
|[IResourceManager::GetAvailableNodeCount](#getavailablenodecount)|Gibt die Anzahl der knotenverfügbaren Knoten für den Ressourcen-Manager zurück.|
|[IResourceManager::GetFirstNode](#getfirstnode)|Gibt den ersten Knoten in der Enumerationsreihenfolge zurück, wie vom Ressourcen-Manager definiert.|
|[IResourceManager::Referenz](#reference)|Erhöht die Referenzanzahl für die Resource Manager-Instanz.|
|[IResourceManager::RegisterScheduler](#registerscheduler)|Registriert einen Planer beim Ressourcen-Manager. Sobald der Planer registriert ist, sollte er mit `ISchedulerProxy` dem Ressourcen-Manager über die zurückgegebene Schnittstelle kommunizieren.|
|[IResourceManager::Release](#release)|Dekrementiert die Verweisanzahl auf die Resource Manager-Instanz. Der Ressourcen-Manager wird zerstört, `0`wenn die Referenzanzahl an geht.|

## <a name="remarks"></a>Bemerkungen

Verwenden Sie die [CreateResourceManager-Funktion,](concurrency-namespace-functions.md) um eine Schnittstelle zur singleton Resource Manager-Instanz abzubilden. Die Methode erhöht eine Verweisanzahl für den Ressourcen-Manager, und Sie sollten die [IResourceManager::Release-Methode](#release) aufrufen, um den Verweis freizugeben, wenn Sie mit Resource Manager fertig sind. In der Regel ruft jeder Planer, den Sie erstellen, diese Methode während der Erstellung auf und gibt den Verweis auf den Ressourcen-Manager frei, nachdem er heruntergefahren wurde.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IResourceManager`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** concrtrm.h

**Namespace:** Parallelität

## <a name="iresourcemanagercreatenodetopology-method"></a><a name="createnodetopology"></a>IResourceManager::CreateNodeTopology-Methode

Diese Methode, die nur in Debugbuilds der Laufzeit vorhanden ist, ist ein Test-Hook, der das Testen des Resource Managers auf unterschiedlichen Hardwaretopologien erleichtert, ohne dass die tatsächliche Hardware erforderlich ist, die mit der Konfiguration übereinstimmt. Bei Einzelhandelsbuilds der Laufzeit wird diese Methode zurückgegeben, ohne dass eine Aktion ausgeführt wird.

```cpp
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```

### <a name="parameters"></a>Parameter

*nodeCount*<br/>
Die Anzahl der simulierten Prozessorknoten.

*pCoreCount*<br/>
Ein Array, das die Anzahl der Kerne auf jedem Knoten angibt.

*pNodeDistance*<br/>
Eine Matrix, die den Knotenabstand zwischen zwei beliebigen Knoten angibt. Dieser Parameter kann `NULL`den Wert haben.

*pProcessorGroups*<br/>
Ein Array, das die Prozessorgruppe angibt, zu der jeder Knoten gehört.

### <a name="remarks"></a>Bemerkungen

[invalid_argument](../../../standard-library/invalid-argument-class.md) wird ausgelöst, `nodeCount` wenn `0` der Parameter den Wert `pCoreCount` übergeben hat `NULL`oder wenn der Parameter den Wert hat.

[invalid_operation](invalid-operation-class.md) wird ausgelöst, wenn diese Methode aufgerufen wird, während andere Planer im Prozess vorhanden sind.

## <a name="iresourcemanagergetavailablenodecount-method"></a><a name="getavailablenodecount"></a>IResourceManager::GetAvailableNodeCount-Methode

Gibt die Anzahl der knotenverfügbaren Knoten für den Ressourcen-Manager zurück.

```cpp
virtual unsigned int GetAvailableNodeCount() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Knoten, die für den Ressourcen-Manager verfügbar sind.

## <a name="iresourcemanagergetfirstnode-method"></a><a name="getfirstnode"></a>IResourceManager::GetFirstNode-Methode

Gibt den ersten Knoten in der Enumerationsreihenfolge zurück, wie vom Ressourcen-Manager definiert.

```cpp
virtual ITopologyNode* GetFirstNode() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Der erste Knoten in der Enumerationsreihenfolge, wie vom Ressourcen-Manager definiert.

## <a name="iresourcemanagerosversion-enumeration"></a><a name="osversion"></a>IResourceManager::OSVersion-Enumeration

Ein enumerierter Typ, der die Betriebssystemversion darstellt.

```cpp
enum OSVersion;
```

## <a name="iresourcemanagerreference-method"></a><a name="reference"></a>IResourceManager::Referenzmethode

Erhöht die Referenzanzahl für die Resource Manager-Instanz.

```cpp
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>Rückgabewert

Die resultierende Referenzanzahl.

## <a name="iresourcemanagerregisterscheduler-method"></a><a name="registerscheduler"></a>IResourceManager::RegisterScheduler-Methode

Registriert einen Planer beim Ressourcen-Manager. Sobald der Planer registriert ist, sollte er mit `ISchedulerProxy` dem Ressourcen-Manager über die zurückgegebene Schnittstelle kommunizieren.

```cpp
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```

### <a name="parameters"></a>Parameter

*pScheduler*<br/>
Eine `IScheduler` Schnittstelle zum zu registrierenden Planer.

*version*<br/>
Die Version der Kommunikationsschnittstelle, die der Planer für die Kommunikation mit dem Ressourcen-Manager verwendet. Die Verwendung einer Version ermöglicht es dem Ressourcen-Manager, die Kommunikationsschnittstelle weiterzuentwickeln und gleichzeitig Planern zugriff auf ältere Funktionen zu erhalten. Planer, die Resource Manager-Features in Visual Studio 2010 `CONCRT_RM_VERSION_1`verwenden möchten, sollten die Version verwenden.

### <a name="return-value"></a>Rückgabewert

Die `ISchedulerProxy` Schnittstelle, die der Ressourcen-Manager Ihrem Planer zugeordnet hat. Der Planer sollte diese Schnittstelle verwenden, um von diesem Zeitpunkt an mit Resource Manager zu kommunizieren.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um die Kommunikation mit dem Ressourcen-Manager zu initiieren. Die Methode `IScheduler` ordnet die Schnittstelle für `ISchedulerProxy` Ihren Planer einer Schnittstelle zu und übergibt sie an Sie. Sie können die zurückgegebene Schnittstelle verwenden, um Ausführungsressourcen für die Verwendung durch Den Planer anzufordern oder Threads mit dem Ressourcen-Manager zu abonnieren. Der Ressourcen-Manager verwendet Richtlinienelemente aus der Planerrichtlinie, die von der [IScheduler::GetPolicy-Methode](ischeduler-structure.md#getpolicy) zurückgegeben wird, um zu bestimmen, welchen Threadtyp der Planer zum Ausführen der Arbeit benötigt. Wenn `SchedulerKind` Ihr Richtlinienschlüssel `UmsThreadDefault` den Wert hat und der Wert als `UmsThreadDefault`Wert `IScheduler` aus der Richtlinie zurückgelesen wird, muss die an die Methode übergebene Schnittstelle eine `IUMSScheduler` Schnittstelle sein.

Die Methode `invalid_argument` löst eine `pScheduler` Ausnahme aus, wenn der Parameter den Wert `NULL` hat oder wenn der Parameter `version` keine gültige Version für die Kommunikationsschnittstelle ist.

## <a name="iresourcemanagerrelease-method"></a><a name="release"></a>IResourceManager::Release-Methode

Dekrementiert die Verweisanzahl auf die Resource Manager-Instanz. Der Ressourcen-Manager wird zerstört, `0`wenn die Referenzanzahl an geht.

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Rückgabewert

Die resultierende Referenzanzahl.

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)<br/>
[ISchedulerProxy-Struktur](ischedulerproxy-structure.md)<br/>
[IScheduler-Struktur](ischeduler-structure.md)
