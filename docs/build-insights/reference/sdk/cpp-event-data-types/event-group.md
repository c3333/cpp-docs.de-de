---
title: EventGroup-Klasse
description: Die Referenz zur EventGroup-Klasse im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 57cbc7a053132909149aee182b9560e2ee33c161
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923304"
---
# <a name="eventgroup-class"></a>EventGroup-Klasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die Klassenvorlage `EventGroup` ist die Basisklasse für alle Gruppenerfassungsklassen.

## <a name="syntax"></a>Syntax

```cpp
template <typename TActivity>
class EventGroup;
{
public:
    size_t Size() const;

    const TActivity& operator[](size_t index) const;
    const TActivity& Front() const;
    const TActivity& Back() const;

    std::deque<TActivity>::const_iterator begin() const;
    std::deque<TActivity>::const_iterator end() const;
};
```

### <a name="parameters"></a>Parameter

*TActivity* Der in der Gruppe enthaltene Aktivitätstyp.

## <a name="members"></a>Member

### <a name="functions"></a>Functions

[Back](#back)
[begin](#begin)
[end](#end)
[Front](#front)
[operator[]](#subscript-operator)
[Size](#size)

## <a name="back"></a><a name="back"></a> Back

```cpp
const TActivity& Back() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das letzte Aktivitätsereignis in der Gruppe.

## <a name="begin"></a><a name="begin"></a> begin

```cpp
std::deque<TActivity>::const_iterator begin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der auf den Anfang der Aktivitätsereignisgruppe zeigt.

## <a name="end"></a><a name="end"></a> end

```cpp
std::deque<TActivity>::const_iterator end() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der auf eine Position hinter dem Ende der Ereignisgruppe der Aktivität zeigt.

## <a name="front"></a><a name="front"></a> Front

```cpp
const TActivity& Front() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das erste Aktivitätsereignis in der Gruppe.

## <a name="operator"></a><a name="subscript-operator"></a> operator[]

```cpp
const TActivity& operator[](size_t index) const;
```

### <a name="parameters"></a>Parameter

*index*\
Der Index des Elements, auf das in der Aktivitätsereignisgruppe zugegriffen werden soll.

### <a name="return-value"></a>Rückgabewert

Das Ereignis aus dem Ereignisstapel, das an der von *Index* angegebenen Position gespeichert ist.

## <a name="size"></a><a name="size"></a>-Größe

```cpp
size_t Size() const;
```

### <a name="return-value"></a>Rückgabewert

Die Größe der Ereignisgruppe.

::: moniker-end
