---
title: IUMSCompletionList-Struktur
ms.date: 11/04/2016
f1_keywords:
- IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList::IUMSCompletionList::GetUnblockNotifications
helpviewer_keywords:
- IUMSCompletionList structure
ms.assetid: 81b5250e-3065-492c-b20d-2cdabf12271a
ms.openlocfilehash: c388cc98aedbd35b2d0e00a4653a85a47abcb838
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368120"
---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList-Struktur

Stellt eine UMS-Vervollständigungsliste dar. Wenn ein UMS-Thread blockiert wird, wird der festgelegte Planungskontext des Planers weitergeleitet, um zu entscheiden, was für den Stamm des zugrunde liegenden virtuellen Prozessors geplant werden soll, während der ursprüngliche Thread blockiert ist. Wenn die Blockierung des ursprünglichen Threads aufgehoben wird, stellt das Betriebssystem ihn in die Warteschlange für die Vervollständigungsliste, auf die über diese Schnittstelle zugegriffen werden kann. Der Planer kann die Vervollständigungsliste für den festgelegten Planungskontext oder eine beliebige andere Stelle abfragen, in der er nach Arbeit sucht.

## <a name="syntax"></a>Syntax

```cpp
struct IUMSCompletionList;
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IUMSCompletionList::GetUnblockNotifications](#getunblocknotifications)|Ruft eine Kette `IUMSUnblockNotification` von Schnittstellen ab, die Ausführungskontexte darstellen, deren zugeordnete Threadproxys seit dem letzten Aufruf dieser Methode die Blockblockierte aufgehoben haben.|

## <a name="remarks"></a>Bemerkungen

Ein Planer muss außerordentlich vorsichtig sein, welche Aktionen ausgeführt werden, nachdem er diese Schnittstelle verwendet hat, um Elemente aus der Abschlussliste zu entren. Die Elemente sollten in die Liste der ausfetzbaren Kontexte des Planers aufgenommen werden und so schnell wie möglich allgemein zugänglich sein. Es ist durchaus möglich, dass einem der aus der Warteschlange entfernten Elemente das Eigentum an einer willkürlichen Sperre übertragen wurde. Der Planer kann keine beliebigen Funktionsaufrufe tätigen, die zwischen dem Aufruf zum Entstellen von Elementen und der Platzierung dieser Elemente in einer Liste blockieren können, auf die im Allgemeinen innerhalb des Planers zugegriffen werden kann.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IUMSCompletionList`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** concrtrm.h

**Namespace:** Parallelität

## <a name="iumscompletionlistgetunblocknotifications-method"></a><a name="getunblocknotifications"></a>IUMSCompletionList::GetUnblockNotifications-Methode

Ruft eine Kette `IUMSUnblockNotification` von Schnittstellen ab, die Ausführungskontexte darstellen, deren zugeordnete Threadproxys seit dem letzten Aufruf dieser Methode die Blockblockierte aufgehoben haben.

```cpp
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```

### <a name="return-value"></a>Rückgabewert

Eine Kette `IUMSUnblockNotification` von Schnittstellen.

### <a name="remarks"></a>Bemerkungen

Die zurückgegebenen Benachrichtigungen sind ungültig, sobald die Ausführungskontexte neu geplant werden.

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)<br/>
[IUMSScheduler-Struktur](iumsscheduler-structure.md)<br/>
[IUMSUnblockNotification-Struktur](iumsunblocknotification-structure.md)
