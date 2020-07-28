---
title: invalid_oversubscribe_operation-Klasse
ms.date: 11/04/2016
f1_keywords:
- invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation::invalid_oversubscribe_operation
helpviewer_keywords:
- invalid_oversubscribe_operation class
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
ms.openlocfilehash: 0c95d234fee412c1dacb014dd135ca56fc73bf5e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87193964"
---
# <a name="invalid_oversubscribe_operation-class"></a>invalid_oversubscribe_operation-Klasse

Diese Klasse beschreibt eine Ausnahme, die ausgelöst `Context::Oversubscribe` wird, wenn die-Methode aufgerufen wird, wobei der- `_BeginOversubscription` Parameter auf festgelegt ist, **`false`** ohne dass ein vorheriger Aufruf der-Methode auf `Context::Oversubscribe` `_BeginOversubscription` festgelegt ist **`true`** .

## <a name="syntax"></a>Syntax

```cpp
class invalid_oversubscribe_operation : public std::exception;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|BESCHREIBUNG|
|----------|-----------------|
|[invalid_oversubscribe_operation](#ctor)|Ist überladen. Erstellt ein `invalid_oversubscribe_operation`-Objekt.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`exception`

`invalid_oversubscribe_operation`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ConcRT. h

**Namespace:** Parallelität

## <a name="invalid_oversubscribe_operation"></a><a name="ctor"></a>invalid_oversubscribe_operation

Erstellt ein `invalid_oversubscribe_operation`-Objekt.

```cpp
explicit _CRTIMP invalid_oversubscribe_operation(_In_z_ const char* _Message) throw();

invalid_oversubscribe_operation() throw();
```

### <a name="parameters"></a>Parameter

*_Message*<br/>
Eine beschreibende Fehlermeldung.

## <a name="see-also"></a>Weitere Informationen

[Parallelitäts Namespace](concurrency-namespace.md)
