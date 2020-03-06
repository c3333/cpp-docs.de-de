---
title: Eventstack-Klasse
description: Die C++ Event Stack-Klassenreferenz für das Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6da2fd25082399b82d788c5d119a39e2f7388714
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334895"
---
# <a name="eventstack-class"></a>Eventstack-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `EventStack`-Klasse ist eine Auflistung von [Ereignis](event.md) Objekten. Alle Ereignisse, die C++ vom Build Insights SDK empfangen werden, sind in Form eines `EventStack` Objekts enthalten. Der letzte Eintrag in diesem Stapel ist das Ereignis, das derzeit verarbeitet wird. Die Einträge, die dem letzten Eintrag vorangestellt sind, sind die übergeordnete Hierarchie des aktuellen Ereignisses. Weitere Informationen zum in C++ buildinsights verwendeten Ereignis Modell finden Sie unter [Ereignis Tabelle](../event-table.md).

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

## <a name="members"></a>Members

### <a name="constructors"></a>Konstruktoren

[Ereignis Stapel](#event-stack)

### <a name="functions"></a>Functions

[Back](#back)
[[]](#subscript-operator) -
[Größe](#size)

## <a name="back"></a>Zurück

```cpp
RawEvent Back() const;
```

### <a name="return-value"></a>Rückgabewert

Ein [rawevent](raw-event.md) -Objekt, das den letzten Eintrag im Stapel darstellt. Der letzte Eintrag in einem Ereignis Stapel ist das Ereignis, das ausgelöst wurde.

## <a name="event-stack"></a>Ereignis Stapel

```cpp
EventStack(const EVENT_COLLECTION_DATA& data);
```

### <a name="parameters"></a>Parameter

*Daten*\
Die Rohdaten, aus denen die `EventStack` erstellt wird.

### <a name="remarks"></a>Bemerkungen

In der Regel müssen Sie `EventStack` Objekte nicht selbst erstellen. Sie werden Ihnen vom C++ Build Insights SDK bereitgestellt, wenn Ereignisse während einer Analyse-oder neuprotokollierungs Sitzung verarbeitet werden.

## <a name="subscript-operator"></a>[]-Operator

```cpp
RawEvent operator[] (size_t index) const;
```

### <a name="parameters"></a>Parameter

*Index*\
Der Index des Elements, auf das im Ereignis Stapel zugegriffen werden soll.

### <a name="return-value"></a>Rückgabewert

Ein [rawevent](raw-event.md) -Objekt, das das Ereignis darstellt, das an der durch den *Index* im Ereignis Stapel gekennzeichneten Position gespeichert wird.

## <a name="size"></a>Größe

```cpp
size_t Size() const;
```

### <a name="return-value"></a>Rückgabewert

Die Größe des Ereignis Stapels.

::: moniker-end
