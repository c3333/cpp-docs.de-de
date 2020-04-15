---
title: ITopologyExecutionResource-Struktur
ms.date: 11/04/2016
f1_keywords:
- ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetId
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetNext
helpviewer_keywords:
- ITopologyExecutionResource structure
ms.assetid: e36756f7-4cd9-4fa6-ba60-23fea58ef2bf
ms.openlocfilehash: 2c9221cab1ac2d48bd099a769188e4bee797823c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368150"
---
# <a name="itopologyexecutionresource-structure"></a>ITopologyExecutionResource-Struktur

Eine Schnittstelle zu einer vom Ressourcen-Manager definierten Ausführungsressource.

## <a name="syntax"></a>Syntax

```cpp
struct ITopologyExecutionResource;
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ITopologyExecutionResource::GetId](#getid)|Gibt den eindeutigen Bezeichner des Ressourcen-Managers für diese Ausführungsressource zurück.|
|[ITopologyExecutionResource::GetNext](#getnext)|Gibt eine Schnittstelle an die nächste Ausführungsressource in der Enumerationsreihenfolge zurück.|

## <a name="remarks"></a>Bemerkungen

Diese Schnittstelle wird in der Regel verwendet, um die Topologie des Systems zu gehen, wie vom Ressourcen-Manager beobachtet.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ITopologyExecutionResource`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** concrtrm.h

**Namespace:** Parallelität

## <a name="itopologyexecutionresourcegetid-method"></a><a name="getid"></a>ITopologyExecutionResource::GetId-Methode

Gibt den eindeutigen Bezeichner des Ressourcen-Managers für diese Ausführungsressource zurück.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Der eindeutige Bezeichner des Ressourcen-Managers für diese Ausführungsressource.

## <a name="itopologyexecutionresourcegetnext-method"></a><a name="getnext"></a>ITopologyExecutionResource::GetNext-Methode

Gibt eine Schnittstelle an die nächste Ausführungsressource in der Enumerationsreihenfolge zurück.

```cpp
virtual ITopologyExecutionResource *GetNext() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Eine Schnittstelle zur nächsten Ausführungsressource in Enumerationsreihenfolge. Wenn keine weiteren Knoten in der Enumerationsreihenfolge des Knotens vorhanden sind, zu `NULL`dem diese Ausführungsressource gehört, gibt diese Methode den Wert zurück.

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)
