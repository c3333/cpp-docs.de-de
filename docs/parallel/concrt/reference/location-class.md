---
title: location-Klasse
ms.date: 11/04/2016
f1_keywords:
- location
- CONCRT/concurrency::location
- CONCRT/concurrency::location::location
- CONCRT/concurrency::location::current
- CONCRT/concurrency::location::from_numa_node
helpviewer_keywords:
- location class
ms.assetid: c3289f51-5bf1-4dff-a18d-d0dab8e5d9c7
ms.openlocfilehash: 848be3131e23ff53f2dec16364b132ee7c218195
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87182693"
---
# <a name="location-class"></a>location-Klasse

Die Abstraktion eines physischen Speicherorts auf der Hardware.

## <a name="syntax"></a>Syntax

```cpp
class location;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[location](#ctor)|Ist überladen. Erstellt ein `location`-Objekt.|
|[~ Location-debugtor](#dtor)|Zerstört ein `location` -Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[Strömung](#current)|Gibt ein-Objekt zurück, `location` das die spezifischere Stelle darstellt, die der aufrufende Thread ausführt.|
|[from_numa_node](#from_numa_node)|Gibt ein- `location` Objekt zurück, das einen angegebenen NUMA-Knoten darstellt.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Operator! =](#operator_neq)|Bestimmt, ob zwei- `location` Objekte unterschiedliche Speicherorte darstellen.|
|[Operator =](#operator_eq)|Weist diesem den Inhalt eines anderen `location` Objekts zu.|
|[Operator = =](#operator_eq_eq)|Bestimmt, ob zwei- `location` Objekte denselben Speicherort darstellen.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`location`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ConcRT. h

**Namespace:** Parallelität

## <a name="location"></a><a name="dtor"></a>~ Speicherort

Zerstört ein `location` -Objekt.

```cpp
~location();
```

## <a name="current"></a><a name="current"></a>Strömung

Gibt ein-Objekt zurück, `location` das die spezifischere Stelle darstellt, die der aufrufende Thread ausführt.

```cpp
static location __cdecl current();
```

### <a name="return-value"></a>Rückgabewert

Ein Speicherort, der den spezifischsten Speicherort darstellt, den der aufrufende Thread ausführt.

## <a name="from_numa_node"></a><a name="from_numa_node"></a>from_numa_node

Gibt ein- `location` Objekt zurück, das einen angegebenen NUMA-Knoten darstellt.

```cpp
static location __cdecl from_numa_node(unsigned short _NumaNodeNumber);
```

### <a name="parameters"></a>Parameter

*_NumaNodeNumber*<br/>
Die NUMA-Knotennummer, für die ein Speicherort erstellt werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Speicherort, der den durch den-Parameter angegebenen NUMA-Knoten darstellt `_NumaNodeNumber` .

## <a name="location"></a><a name="ctor"></a>Hotels

Erstellt ein `location`-Objekt.

```cpp
location();

location(
    const location& _Src);

location(
    T _LocationType,
    unsigned int _Id,
    unsigned int _BindingId = 0,
    _Inout_opt_ void* _PBinding = NULL);
```

### <a name="parameters"></a>Parameter

*_Src*<br/>

*_LocationType*<br/>

*_Id*<br/>

*_BindingId*<br/>

*_PBinding*<br/>
Optionale Bindungs Zeiger.

### <a name="remarks"></a>Bemerkungen

Ein standardmäßiger erstellter Speicherort stellt das System als Ganzes dar.

## <a name="operator"></a><a name="operator_neq"></a>Operator! =

Bestimmt, ob zwei- `location` Objekte unterschiedliche Speicherorte darstellen.

```cpp
bool operator!= (const location& _Rhs) const;
```

### <a name="parameters"></a>Parameter

*_Rhs*<br/>
Operand `location` .

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn sich die beiden Speicherorte unterscheiden, **`false`** andernfalls.

## <a name="operator"></a><a name="operator_eq"></a>Operator =

Weist diesem den Inhalt eines anderen `location` Objekts zu.

```cpp
location& operator= (const location& _Rhs);
```

### <a name="parameters"></a>Parameter

*_Rhs*<br/>
Das `location`-Quellobjekt.

### <a name="return-value"></a>Rückgabewert

## <a name="operator"></a><a name="operator_eq_eq"></a>Operator = =

Bestimmt, ob zwei- `location` Objekte denselben Speicherort darstellen.

```cpp
bool operator== (const location& _Rhs) const;
```

### <a name="parameters"></a>Parameter

*_Rhs*<br/>
Operand `location` .

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die beiden Speicherorte identisch sind, **`false`** andernfalls.

## <a name="see-also"></a>Weitere Informationen

[Parallelitäts Namespace](concurrency-namespace.md)
