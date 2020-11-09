---
title: EventStack-Klasse
description: Die Referenz zur EventStack-Klasse im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b4f1e92011acdf8272fe631843c03c2f960a1234
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920709"
---
# <a name="eventstack-class"></a>EventStack-Klasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `EventStack`-Klasse ist eine Sammlung von [Event](event.md)-Objekten. Alle vom C++ Build Insights SDK empfangenen Ereignisse haben die Form eines `EventStack`-Objekts. Der letzte Eintrag in diesem Stapel ist das Ereignis, das gerade verarbeitet wird. Die Einträge vor dem letzten Eintrag bilden die übergeordnete Hierarchie des aktuellen Ereignisses. Weitere Informationen zum Ereignismodell in C++ Build Insights finden Sie unter [Ereignistabelle](../event-table.md).

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
[operator[]](#subscript-operator)
[Size](#size)

## <a name="back"></a><a name="back"></a> Back

```cpp
RawEvent Back() const;
```

### <a name="return-value"></a>Rückgabewert

Ein [RawEvent](raw-event.md)-Objekt, das den letzten Eintrag im Stapel darstellt. Der letzte Eintrag in einem Ereignisstapel ist das Ereignis, das ausgelöst wurde.

## <a name="eventstack"></a><a name="event-stack"></a> EventStack

```cpp
EventStack(const EVENT_COLLECTION_DATA& data);
```

### <a name="parameters"></a>Parameter

*data*\
Die Rohdaten, aus denen `EventStack` erstellt wird.

### <a name="remarks"></a>Hinweise

In der Regel müssen Sie `EventStack`-Objekte nicht selbst erstellen. Sie werden Ihnen vom C++ Build Insights SDK zur Verfügung gestellt, wenn Ereignisse während einer Analyse- oder Neuprotokollierungssitzung verarbeitet werden.

## <a name="operator"></a><a name="subscript-operator"></a> operator[]

```cpp
RawEvent operator[] (size_t index) const;
```

### <a name="parameters"></a>Parameter

*index*\
Der Index des Elements, auf das im Ereignisstapel zugegriffen werden soll.

### <a name="return-value"></a>Rückgabewert

Ein [RawEvent](raw-event.md)-Objekt, das das Ereignis darstellt, welches an der durch *Index* angegebenen Position im Ereignisstapel gespeichert ist.

## <a name="size"></a><a name="size"></a>-Größe

```cpp
size_t Size() const;
```

### <a name="return-value"></a>Rückgabewert

Die Größe des Ereignisstapels.

::: moniker-end
