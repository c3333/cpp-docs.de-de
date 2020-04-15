---
title: scheduler_interface-Struktur
ms.date: 11/04/2016
f1_keywords:
- scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface::scheduler_interface::schedule
ms.assetid: 4de61c78-a2c6-4698-bd47-964baf7fa287
ms.openlocfilehash: da2ebc2f9c2878baefcfa792bac08f420dbbb281
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358791"
---
# <a name="scheduler_interface-structure"></a>scheduler_interface-Struktur

Planerschnittstelle

## <a name="syntax"></a>Syntax

```cpp
struct __declspec(novtable) scheduler_interface;
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[scheduler_interface::Zeitplan](#schedule)||

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`scheduler_interface`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** pplinterface.h

**Namespace:** Parallelität

## <a name="scheduler_interfaceschedule-method"></a><a name="schedule"></a>scheduler_interface::Zeitplanmethode

```cpp
virtual void schedule(
    TaskProc_t,
void*) = 0;
```

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)
