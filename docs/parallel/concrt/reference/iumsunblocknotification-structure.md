---
title: IUMSUnblockNotification-Struktur
ms.date: 11/04/2016
f1_keywords:
- IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetContext
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetNextUnblockNotification
helpviewer_keywords:
- IUMSUnblockNotification structure
ms.assetid: eaca9529-c1cc-472b-8ec6-722a1ff0fa2a
ms.openlocfilehash: 0b88ddd4184e982a5e07c536efc301eaa16f4a41
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368073"
---
# <a name="iumsunblocknotification-structure"></a>IUMSUnblockNotification-Struktur

Stellt eine Benachrichtigung vom Ressourcen-Manager darüber dar, dass ein Threadproxy, der blockiert und eine Rückkehr zum festgelegten Planungskontext des Planers ausgelöst hatte, die Blockierung aufgehoben hat und zum Planen bereit ist. Diese Schnittstelle ist ungültig, sobald der zugeordnete Ausführungskontext des Threadproxys, der von der `GetContext`-Methode zurückgegeben wurde, neu geplant wird.

## <a name="syntax"></a>Syntax

```cpp
struct IUMSUnblockNotification;
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IUMSUnblockNotification::GetContext](#getcontext)|Gibt `IExecutionContext` die Schnittstelle für den Ausführungskontext zurück, der dem Threadproxy zugeordnet ist, der die Blockblockierte aufgehoben hat. Sobald diese Methode zurückgegeben wird und der zugrunde liegende `IThreadProxy::SwitchTo` Ausführungskontext über einen Aufruf der Methode neu geplant wurde, ist diese Schnittstelle nicht mehr gültig.|
|[IUMSUnblockNotification::GetNextUnblockNotification](#getnextunblocknotification)|Gibt die `IUMSUnblockNotification` nächste Schnittstelle in der `IUMSCompletionList::GetUnblockNotifications`Kette zurück, die von der Methode zurückgegeben wird.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IUMSUnblockNotification`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** concrtrm.h

**Namespace:** Parallelität

## <a name="iumsunblocknotificationgetcontext-method"></a><a name="getcontext"></a>IUMSUnblockNotification::GetContext-Methode

Gibt `IExecutionContext` die Schnittstelle für den Ausführungskontext zurück, der dem Threadproxy zugeordnet ist, der die Blockblockierte aufgehoben hat. Sobald diese Methode zurückgegeben wird und der zugrunde liegende `IThreadProxy::SwitchTo` Ausführungskontext über einen Aufruf der Methode neu geplant wurde, ist diese Schnittstelle nicht mehr gültig.

```cpp
virtual IExecutionContext* GetContext() = 0;
```

### <a name="return-value"></a>Rückgabewert

Eine `IExecutionContext` Schnittstelle für den Ausführungskontext zu einem Threadproxy, der die Blockblockierte aufgehoben hat.

## <a name="iumsunblocknotificationgetnextunblocknotification-method"></a><a name="getnextunblocknotification"></a>IUMSUnblockNotification::GetNextUnblockNotification-Methode

Gibt die `IUMSUnblockNotification` nächste Schnittstelle in der `IUMSCompletionList::GetUnblockNotifications`Kette zurück, die von der Methode zurückgegeben wird.

```cpp
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```

### <a name="return-value"></a>Rückgabewert

Die `IUMSUnblockNotification` nächste Schnittstelle in der `IUMSCompletionList::GetUnblockNotifications`Kette, die von der Methode zurückgegeben wurde.

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)<br/>
[IUMSScheduler-Struktur](iumsscheduler-structure.md)<br/>
[IUMSCompletionList-Struktur](iumscompletionlist-structure.md)
