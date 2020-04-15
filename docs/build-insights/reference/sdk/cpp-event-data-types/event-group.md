---
title: EventGroup-Klasse
description: Der C++ Build Insights SDK EventGroup-Klassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 596c18ca0e9b4d7b26c4ed5209b16871952c4af2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324988"
---
# <a name="eventgroup-class"></a>EventGroup-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `EventGroup` Klassenvorlage ist die Basisklasse für alle Gruppenerfassungsklassen.

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



[Size](#size) Back-Start-End-Frontoperator[][begin](#begin)
[end](#end)Größe[Front](#front)[operator[]](#subscript-operator)

## <a name="back"></a><a name="back"></a>Zurück

```cpp
const TActivity& Back() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das letzte Aktivitätsereignis in der Gruppe.

## <a name="begin"></a><a name="begin"></a>Beginnen

```cpp
std::deque<TActivity>::const_iterator begin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der am Anfang der Aktivitätsereignisgruppe zeigt.

## <a name="end"></a><a name="end"></a>Ende

```cpp
std::deque<TActivity>::const_iterator end() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der eine Position über das Ende der Aktivitätsereignisgruppe hinaus zeigt.

## <a name="front"></a><a name="front"></a>Vorder-

```cpp
const TActivity& Front() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das erste Aktivitätsereignis in der Gruppe.

## <a name="operator"></a><a name="subscript-operator"></a>Operator[]

```cpp
const TActivity& operator[](size_t index) const;
```

### <a name="parameters"></a>Parameter

*Index*\
Der Index des Elements, auf das in der Aktivitätsereignisgruppe zugreifen soll.

### <a name="return-value"></a>Rückgabewert

Das Ereignis aus dem Ereignisstapel, der an der durch *Index*angegebenen Position gespeichert ist.

## <a name="size"></a><a name="size"></a>-Größe

```cpp
size_t Size() const;
```

### <a name="return-value"></a>Rückgabewert

Die Größe der Ereignisgruppe.

::: moniker-end
