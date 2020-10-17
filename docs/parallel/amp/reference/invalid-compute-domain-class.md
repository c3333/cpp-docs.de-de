---
title: invalid_compute_domain-Klasse
ms.date: 11/04/2016
f1_keywords:
- invalid_compute_domain
- AMPRT/invalid_compute_domain
- AMPRT/Concurrency::invalid_compute_domain::invalid_compute_domain
helpviewer_keywords:
- invalid_compute_domain class
ms.assetid: ac7a7166-8bdb-4db1-8caf-ea129ab5117e
ms.openlocfilehash: 09418991e805e494c1d79ef31980bbec66a2e172
ms.sourcegitcommit: ced5ff1431ffbd25b20d106901955532723bd188
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2020
ms.locfileid: "92135566"
---
# <a name="invalid_compute_domain-class"></a>invalid_compute_domain-Klasse

Die Ausnahme, die ausgelöst wird, wenn die Laufzeit einen Kernel nicht mithilfe der COMPUTE-Domäne starten kann, die auf der [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each) -anrufsite angegeben ist.

## <a name="syntax"></a>Syntax

```cpp
class invalid_compute_domain : public runtime_exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|BESCHREIBUNG|
|----------|-----------------|
|[invalid_compute_domain-Konstruktor](#ctor)|Initialisiert eine neue Instanz der `invalid_compute_domain`-Klasse.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`exception`

`runtime_exception`

`invalid_compute_domain`

## <a name="requirements"></a>Anforderungen

**Header:** amprt. h

**Namespace:** Parallelität

## <a name="invalid_compute_domain"></a><a name="ctor"></a> invalid_compute_domain

Initialisiert eine neue Instanz der Klasse.

### <a name="syntax"></a>Syntax

```cpp
explicit invalid_compute_domain(
    const char * _Message ) throw();

invalid_compute_domain() throw();
```

### <a name="parameters"></a>Parameter

*_Message*<br/>
Eine Beschreibung des Fehlers.

### <a name="return-value"></a>Rückgabewert

Eine Instanz der `invalid_compute_domain`-Klasse

## <a name="see-also"></a>Siehe auch

[Parallelitäts Namespace (C++ amp)](concurrency-namespace-cpp-amp.md)
