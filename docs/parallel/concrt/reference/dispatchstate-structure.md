---
title: DispatchState-Struktur
ms.date: 11/04/2016
f1_keywords:
- DispatchState
- CONCRTRM/concurrency::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::m_dispatchStateSize
- CONCRTRM/concurrency::DispatchState::DispatchState::m_fIsPreviousContextAsynchronouslyBlocked
- CONCRTRM/concurrency::DispatchState::DispatchState::m_reserved
helpviewer_keywords:
- DispatchState structure
ms.assetid: 8c52546e-1650-48a0-985f-7e4a0fc26a90
ms.openlocfilehash: 2c4103f89f7fc74c5368bafac3c82685ff9b6e03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372698"
---
# <a name="dispatchstate-structure"></a>DispatchState-Struktur

Die `DispatchState`-Struktur wird zur Zustandsübertragung auf die `IExecutionContext::Dispatch`-Methode verwendet. Sie beschreibt die Umstände, unter denen die `Dispatch`-Methode für eine `IExecutionContext`-Schnittstelle aufgerufen wird.

## <a name="syntax"></a>Syntax

```cpp
struct DispatchState;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[DispatchState::DispatchState](#ctor)|Erstellt ein neues `DispatchState`-Objekt.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[DispatchState::m_dispatchStateSize](#m_dispatchstatesize)|Größe dieser Struktur, die für die Versionsänderung verwendet wird.|
|[DispatchState::m_fIsPreviousContextAsynchronouslyBlocked](#m_fispreviouscontextasynchronouslyblocked)|Gibt an, ob `Dispatch` dieser Kontext in die Methode eingegeben wurde, da der vorherige Kontext asynchron blockiert wurde. Dies wird nur für den UMS-Planungskontext `0` verwendet und ist auf den Wert für alle anderen Ausführungskontexte festgelegt.|
|[DispatchState::m_reserved](#m_reserved)|Bits, die für die zukünftige Weitergabe von Informationen reserviert sind.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`DispatchState`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** concrtrm.h

**Namespace:** Parallelität

## <a name="dispatchstatedispatchstate-constructor"></a><a name="ctor"></a>DispatchState::DispatchState Konstruktor

Erstellt ein neues `DispatchState`-Objekt.

```cpp
DispatchState();
```

## <a name="dispatchstatem_dispatchstatesize-data-member"></a><a name="m_dispatchstatesize"></a>DispatchState::m_dispatchStateSize Datenmitglied

Größe dieser Struktur, die für die Versionsänderung verwendet wird.

```cpp
unsigned long m_dispatchStateSize;
```

## <a name="dispatchstatem_fispreviouscontextasynchronouslyblocked-data-member"></a><a name="m_fispreviouscontextasynchronouslyblocked"></a>DispatchState::m_fIsPreviousContextAsynchronouslyBlocked Datenmitglied

Gibt an, ob `Dispatch` dieser Kontext in die Methode eingegeben wurde, da der vorherige Kontext asynchron blockiert wurde. Dies wird nur für den UMS-Planungskontext `0` verwendet und ist auf den Wert für alle anderen Ausführungskontexte festgelegt.

```cpp
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```

## <a name="dispatchstatem_reserved-data-member"></a><a name="m_reserved"></a>DispatchState::m_reserved Datenmitglied

Bits, die für die zukünftige Weitergabe von Informationen reserviert sind.

```cpp
unsigned int m_reserved : 31;
```

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)
