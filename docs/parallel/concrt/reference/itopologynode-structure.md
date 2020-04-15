---
title: ITopologyNode-Struktur
ms.date: 11/04/2016
f1_keywords:
- ITopologyNode
- CONCRTRM/concurrency::ITopologyNode
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetExecutionResourceCount
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetFirstExecutionResource
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetId
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNext
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNumaNode
helpviewer_keywords:
- ITopologyNode structure
ms.assetid: 92e7e032-04f6-4c7c-be36-8f9a35fc4734
ms.openlocfilehash: 7cb815c4f7dc5ad09e8d352abc3f3375b8d9e205
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368109"
---
# <a name="itopologynode-structure"></a>ITopologyNode-Struktur

Eine Schnittstelle für einen vom Ressourcen-Manager definierten Topologieknoten. Ein Knoten enthält mindestens eine Ausführungsressource.

## <a name="syntax"></a>Syntax

```cpp
struct ITopologyNode;
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ITopologyNode::GetExecutionResourceCount](#getexecutionresourcecount)|Gibt die Anzahl der Ausführungsressourcen zurück, die unter diesem Knoten gruppiert sind.|
|[ITopologyNode::GetFirstExecutionResource](#getfirstexecutionresource)|Gibt die erste Ausführungsressource zurück, die unter diesem Knoten in der Enumerationsreihenfolge gruppiert ist.|
|[ITopologyNode::GetId](#getid)|Gibt den eindeutigen Bezeichner des Ressourcen-Managers für diesen Knoten zurück.|
|[ITopologyNode::GetNext](#getnext)|Gibt eine Schnittstelle an den nächsten Topologieknoten in Enumerationsreihenfolge zurück.|
|[ITopologyNode::GetNumaNode](#getnumanode)|Gibt die von Windows zugewiesene NUMA-Knotenzahl zurück, zu der dieser Ressource-Manager-Knoten gehört.|

## <a name="remarks"></a>Bemerkungen

Diese Schnittstelle wird in der Regel verwendet, um die Topologie des Systems zu gehen, wie vom Ressourcen-Manager beobachtet.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ITopologyNode`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** concrtrm.h

**Namespace:** Parallelität

## <a name="itopologynodegetexecutionresourcecount-method"></a><a name="getexecutionresourcecount"></a>ITopologyNode::GetExecutionResourceCount-Methode

Gibt die Anzahl der Ausführungsressourcen zurück, die unter diesem Knoten gruppiert sind.

```cpp
virtual unsigned int GetExecutionResourceCount() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Ausführungsressourcen, die unter diesem Knoten gruppiert sind.

## <a name="itopologynodegetfirstexecutionresource-method"></a><a name="getfirstexecutionresource"></a>ITopologyNode::GetFirstExecutionResource-Methode

Gibt die erste Ausführungsressource zurück, die unter diesem Knoten in der Enumerationsreihenfolge gruppiert ist.

```cpp
virtual ITopologyExecutionResource *GetFirstExecutionResource() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Die erste Ausführungsressource, die unter diesem Knoten in der Enumerationsreihenfolge gruppiert ist.

## <a name="itopologynodegetid-method"></a><a name="getid"></a>ITopologyNode::GetId-Methode

Gibt den eindeutigen Bezeichner des Ressourcen-Managers für diesen Knoten zurück.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Der eindeutige Bezeichner des Ressourcen-Managers für diesen Knoten.

### <a name="remarks"></a>Bemerkungen

Die Concurrency Runtime stellt Hardwarethreads auf dem System in Gruppen von Prozessorknoten dar. Knoten werden in der Regel von der Hardwaretopologie des Systems abgeleitet. Beispielsweise können alle Prozessoren auf einem bestimmten Socket oder einem bestimmten NUMA-Knoten zum gleichen Prozessorknoten gehören. Der Ressourcen-Manager weist diesen Knoten eindeutige `0` Bezeichner `nodeCount - 1`zu, beginnend mit bis zu und einschließlich , wobei `nodeCount` die Gesamtzahl der Prozessorknoten auf dem System angezeigt wird.

Die Anzahl der Knoten kann über die Funktion [GetProcessorNodeCount](concurrency-namespace-functions.md)abgerufen werden.

## <a name="itopologynodegetnext-method"></a><a name="getnext"></a>ITopologyNode::GetNext-Methode

Gibt eine Schnittstelle an den nächsten Topologieknoten in Enumerationsreihenfolge zurück.

```cpp
virtual ITopologyNode *GetNext() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Eine Schnittstelle zum nächsten Knoten in Enumerationsreihenfolge. Wenn in der Enumerationsreihenfolge der Systemtopologie keine Knoten mehr vorhanden `NULL`sind, gibt diese Methode den Wert zurück.

## <a name="itopologynodegetnumanode-method"></a><a name="getnumanode"></a>ITopologyNode::GetNumaNode-Methode

Gibt die von Windows zugewiesene NUMA-Knotenzahl zurück, zu der dieser Ressource-Manager-Knoten gehört.

```cpp
virtual unsigned long GetNumaNode() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Die von Windows zugewiesene NUMA-Knotenzahl, zu der dieser Ressource-Manager-Knoten gehört.

### <a name="remarks"></a>Bemerkungen

Ein Threadproxy, der auf einem virtuellen Prozessorstamm ausgeführt wird, der zu diesem Knoten gehört, verfügt über Affinität zu mindestens der NUMA-Knotenebene für den NUMA-Knoten, der von dieser Methode zurückgegeben wird.

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)
