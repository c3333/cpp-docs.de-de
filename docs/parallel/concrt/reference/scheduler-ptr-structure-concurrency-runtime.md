---
title: scheduler_ptr Struktur
ms.date: 11/04/2016
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
ms.openlocfilehash: 60d71a26e5dffcadfb900ef15c26a6d9dc6d6f8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358768"
---
# <a name="scheduler_ptr-structure"></a>scheduler_ptr Struktur

Stellt einen Zeiger auf einen Planer dar. Diese Klasse ist vorhanden, um die Spezifikation einer gemeinsamen Lebensdauer mithilfe von shared_ptr oder nur einen einfachen Verweis mithilfe eines unformatierten Zeigers zu ermöglichen.

## <a name="syntax"></a>Syntax

```cpp
struct scheduler_ptr;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[scheduler_ptr::scheduler_ptr](#ctor)|Ist überladen. Erstellt einen scheduler-Zeiger von "shared_ptr" auf "scheduler".|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[scheduler_ptr::get](#get)|Gibt den Rohzeiger auf den Planer zurück.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[scheduler_ptr::operator bool](#operator_bool)|Testet, dass der scheduler-Zeiger nicht NULL ist.|
|[scheduler_ptr::Operator-&gt;](#operator_ptr)|Verhält sich wie ein Zeiger.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`scheduler_ptr`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** pplinterface.h

**Namespace:** Parallelität

## <a name="scheduler_ptrget-method"></a><a name="get"></a>scheduler_ptr::Methode abrufen

Gibt den Rohzeiger an den Planer zurück.

```cpp
scheduler_interface* get() const;
```

### <a name="return-value"></a>Rückgabewert

## <a name="scheduler_ptroperator-bool"></a><a name="operator_bool"></a>scheduler_ptr::operator bool

Testet, ob der Planerzeiger ungleich NULL ist.

```cpp
operator bool() const;
```

## <a name="scheduler_ptroperator-gt"></a><a name="operator_ptr"></a>scheduler_ptr::Operator-&gt;

Verhält sich wie ein Zeiger.

```cpp
scheduler_interface* operator->() const;
```

### <a name="return-value"></a>Rückgabewert

## <a name="scheduler_ptrscheduler_ptr-constructor"></a><a name="ctor"></a>scheduler_ptr::scheduler_ptr Konstrukteur

Erstellt einen Planerzeiger von shared_ptr zum Planer.

```cpp
explicit scheduler_ptr(std::shared_ptr<scheduler_interface> scheduler);
explicit scheduler_ptr(_In_opt_ scheduler_interface* pScheduler);
```

### <a name="parameters"></a>Parameter

*Scheduler*<br/>
Der zu konvertierende Planer.

*pScheduler*<br/>
Der zu konvertierende Planerzeiger.

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)
