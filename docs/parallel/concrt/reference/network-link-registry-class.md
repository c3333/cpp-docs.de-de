---
title: network_link_registry-Klasse
ms.date: 11/04/2016
f1_keywords:
- network_link_registry
- AGENTS/concurrency::network_link_registry
- AGENTS/concurrency::network_link_registry::add
- AGENTS/concurrency::network_link_registry::begin
- AGENTS/concurrency::network_link_registry::contains
- AGENTS/concurrency::network_link_registry::count
- AGENTS/concurrency::network_link_registry::remove
helpviewer_keywords:
- network_link_registry class
ms.assetid: 3e7b4097-09f1-4252-964e-b15b8f7f7fc6
ms.openlocfilehash: 18fabd0e741c144201f299271cdd01eb9ac55fac
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222679"
---
# <a name="network_link_registry-class"></a>network_link_registry-Klasse

Die abstrakte `network_link_registry`-Basisklasse verwaltet die Verknüpfung zwischen Quell- und Zielblöcken.

## <a name="syntax"></a>Syntax

```cpp
template<class _Block>
class network_link_registry;
```

### <a name="parameters"></a>Parameter

*_Block*<br/>
Der Block Datentyp, der in der gespeichert wird `network_link_registry` .

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|`const_pointer`|Ein Typ, der einen Zeiger auf ein- **`const`** Element in einem-Objekt bereitstellt `network_link_registry` .|
|`const_reference`|Ein Typ, der einen Verweis auf ein-Element bereitstellt, das **`const`** in einem- `network_link_registry` Objekt zum Lesen und Ausführen von Konstanten Vorgängen gespeichert ist.|
|`iterator`|Ein Typ, der einen Iterator bereitstellt, mit dem jedes Element in einem-Objekt gelesen oder geändert werden kann `network_link_registry` .|
|`type`|Ein Typ, der den im-Objekt gespeicherten Blocktyp darstellt `network_link_registry` .|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[add](#add)|Fügt beim Überschreiben in einer abgeleiteten Klasse einen Link zum- `network_link_registry` Objekt hinzu.|
|[beginnen](#begin)|Gibt beim Überschreiben in einer abgeleiteten Klasse einen Iterator an das erste Element im- `network_link_registry` Objekt zurück.|
|[contains](#contains)|Durchsucht beim Überschreiben in einer abgeleiteten Klasse das- `network_link_registry` Objekt nach einem angegebenen-Block.|
|[count](#count)|Gibt beim Überschreiben in einer abgeleiteten Klasse die Anzahl der Elemente im- `network_link_registry` Objekt zurück.|
|[remove](#remove)|Entfernt beim Überschreiben in einer abgeleiteten Klasse einen angegebenen-Block aus dem- `network_link_registry` Objekt.|

## <a name="remarks"></a>Bemerkungen

Der `network link registry` ist für den gleichzeitigen Zugriff nicht sicher.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`network_link_registry`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** agents.h

**Namespace:** Parallelität

## <a name="add"></a><a name="add"></a>eren

Fügt beim Überschreiben in einer abgeleiteten Klasse einen Link zum- `network_link_registry` Objekt hinzu.

```cpp
virtual void add(_EType _Link) = 0;
```

### <a name="parameters"></a>Parameter

*_Link*<br/>
Ein Zeiger auf einen Block, der hinzugefügt werden soll.

## <a name="begin"></a><a name="begin"></a>beginnen

Gibt beim Überschreiben in einer abgeleiteten Klasse einen Iterator an das erste Element im- `network_link_registry` Objekt zurück.

```cpp
virtual iterator begin() = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der das erste Element im-Objekt adressiert `network_link_registry` .

### <a name="remarks"></a>Bemerkungen

Der Endzustand des Iterators wird durch einen Link angegeben `NULL` .

## <a name="contains"></a><a name="contains"></a>Inhalt

Durchsucht beim Überschreiben in einer abgeleiteten Klasse das- `network_link_registry` Objekt nach einem angegebenen-Block.

```cpp
virtual bool contains(_EType _Link) = 0;
```

### <a name="parameters"></a>Parameter

*_Link*<br/>
Ein Zeiger auf einen Block, der im-Objekt gesucht werden soll `network_link_registry` .

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der Block gefunden wurde, **`false`** andernfalls.

## <a name="count"></a><a name="count"></a>Countdown

Gibt beim Überschreiben in einer abgeleiteten Klasse die Anzahl der Elemente im- `network_link_registry` Objekt zurück.

```cpp
virtual size_t count() = 0;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente im `network_link_registry`-Objekt.

## <a name="remove"></a><a name="remove"></a>aufgeh

Entfernt beim Überschreiben in einer abgeleiteten Klasse einen angegebenen-Block aus dem- `network_link_registry` Objekt.

```cpp
virtual bool remove(_EType _Link) = 0;
```

### <a name="parameters"></a>Parameter

*_Link*<br/>
Ein Zeiger auf einen Block, der entfernt werden soll, sofern gefunden.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der Link gefunden und entfernt wurde, **`false`** andernfalls.

## <a name="see-also"></a>Weitere Informationen

[Parallelitäts Namespace](concurrency-namespace.md)<br/>
[Single_link_registry-Klasse](single-link-registry-class.md)<br/>
[Multi_link_registry-Klasse](multi-link-registry-class.md)
