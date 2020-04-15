---
title: out_of_memory-Klasse
ms.date: 11/04/2016
f1_keywords:
- out_of_memory
- AMPRT/out_of_memory
- AMPRT/Concurrency::out_of_memory::out_of_memory
helpviewer_keywords:
- out_of_memory class
ms.assetid: 3aa7e682-8f13-4ae6-9188-31fb423956e4
ms.openlocfilehash: e716d4952bdb9634cc0d195285d3a65c5c06b0a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336801"
---
# <a name="out_of_memory-class"></a>out_of_memory-Klasse

Die Ausnahme, die ausgelöst wird, wenn eine Methode aufgrund unzureichenden System- oder Gerätearbeitsspeichers fehlschlägt.

## <a name="syntax"></a>Syntax

```cpp
class out_of_memory : public runtime_exception;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[out_of_memory Konstruktor](#ctor)|Initialisiert eine neue Instanz der Klasse `out_of_memory`.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** amprt.h

**Namespace:** Parallelität

## <a name="out_of_memory"></a><a name="ctor"></a>out_of_memory

Initialisiert eine neue Instanz der Klasse.

### <a name="syntax"></a>Syntax

```cpp
explicit out_of_memory(
    const char * _Message ) throw();

out_of_memory () throw();
```

### <a name="parameters"></a>Parameter

*_Message*<br/>
Eine Beschreibung des Fehlers.

### <a name="return-value"></a>Rückgabewert

Eine neue Instanz der `out_of_memory`-Klasse.

## <a name="see-also"></a>Siehe auch

[Parallelitätsnamespace (C++ AMP)](concurrency-namespace-cpp-amp.md)
