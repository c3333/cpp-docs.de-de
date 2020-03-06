---
title: Eventgroup-Klasse
description: Die C++ Referenz für den Build Insights SDK-eventgroup-Klasse.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ac8ac70f3fc160714b86dd0c483808a4d06e7699
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334919"
---
# <a name="eventgroup-class"></a>Eventgroup-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `EventGroup`-Klassen Vorlage ist die Basisklasse für alle Gruppen Erfassungs Klassen.

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

*Tactivity* Der Aktivitätstyp, der in der Gruppe enthalten ist.

## <a name="members"></a>Members

### <a name="functions"></a>Functions

[Back](#back)
[Anfang](#begin)
[Ende](#end)
[Front](#front)
[Operator []](#subscript-operator)
[Größe](#size)

## <a name="back"></a>Zurück

```cpp
const TActivity& Back() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das letzte Aktivitäts Ereignis in der Gruppe.

## <a name="begin"></a>beginnen

```cpp
std::deque<TActivity>::const_iterator begin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der auf den Anfang der Aktivitäts Ereignis Gruppe zeigt.

## <a name="end"></a>Schließlich

```cpp
std::deque<TActivity>::const_iterator end() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der eine Position hinter dem Ende der Aktivitäts Ereignis Gruppe zeigt.

## <a name="front"></a>Beifahrer

```cpp
const TActivity& Front() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das erste Aktivitäts Ereignis in der Gruppe.

## <a name="subscript-operator"></a>[]-Operator

```cpp
const TActivity& operator[](size_t index) const;
```

### <a name="parameters"></a>Parameter

*Index*\
Der Index des Elements, auf das in der Aktivitäts Ereignis Gruppe zugegriffen werden soll.

### <a name="return-value"></a>Rückgabewert

Das Ereignis aus dem Ereignis Stapel, das an der durch den *Index*gekennzeichneten Position gespeichert wird.

## <a name="size"></a>Größe

```cpp
size_t Size() const;
```

### <a name="return-value"></a>Rückgabewert

Die Größe der Ereignis Gruppe.

::: moniker-end
