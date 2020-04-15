---
title: EventStack-Klasse
description: Der C++ Build Insights SDK EventStack-Klassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: eaaaedcbf57fdaf8e437a80a7823488febac3e1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324978"
---
# <a name="eventstack-class"></a>EventStack-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `EventStack` Klasse ist eine Auflistung von [Event-Objekten.](event.md) Alle Ereignisse, die vom C++ Build Insights SDK empfangen werden, werden in Form eines `EventStack` Objekts verwendet. Der letzte Eintrag in diesem Stapel ist das Ereignis, das gerade verarbeitet wird. Die Einträge, die dem letzten Eintrag vorausgehen, sind die übergeordnete Hierarchie des aktuellen Ereignisses. Weitere Informationen zum Ereignismodell, das in C++-Build-Insights verwendet wird, finden Sie in der [Ereignistabelle](../event-table.md).

## <a name="syntax"></a>Syntax

```cpp
class EventStack
{
public:
    EventStack(const EVENT_COLLECTION_DATA& data);

    size_t      Size() const;
    RawEvent    Back() const;
    RawEvent    operator[] (size_t index) const;
};
```

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

[EventStack](#event-stack)

### <a name="functions"></a>Functions

[Back](#back)
[Zurück-Operator[]](#subscript-operator)
[Größe](#size)

## <a name="back"></a><a name="back"></a>Zurück

```cpp
RawEvent Back() const;
```

### <a name="return-value"></a>Rückgabewert

Ein [RawEvent-Objekt,](raw-event.md) das den letzten Eintrag im Stapel darstellt. Der letzte Eintrag in einem Ereignisstapel ist das Ereignis, das ausgelöst wurde.

## <a name="eventstack"></a><a name="event-stack"></a>EventStack

```cpp
EventStack(const EVENT_COLLECTION_DATA& data);
```

### <a name="parameters"></a>Parameter

*Daten*\
Die Rohdaten, `EventStack` aus denen der erstellt wird.

### <a name="remarks"></a>Bemerkungen

Sie müssen normalerweise keine `EventStack` Objekte selbst erstellen. Sie werden Ihnen vom C++ Build Insights SDK bereitgestellt, wenn Ereignisse während einer Analyse- oder Reloggingsitzung verarbeitet werden.

## <a name="operator"></a><a name="subscript-operator"></a>Operator[]

```cpp
RawEvent operator[] (size_t index) const;
```

### <a name="parameters"></a>Parameter

*Index*\
Der Index des Elements, auf das im Ereignisstapel zugreifen soll.

### <a name="return-value"></a>Rückgabewert

Ein [RawEvent-Objekt,](raw-event.md) das das Ereignis darstellt, das an der position gespeichert ist, die durch *den Index* im Ereignisstapel angegeben ist.

## <a name="size"></a><a name="size"></a>-Größe

```cpp
size_t Size() const;
```

### <a name="return-value"></a>Rückgabewert

Die Größe des Ereignisstapels.

::: moniker-end
