---
title: source_link_manager-Klasse
ms.date: 11/04/2016
f1_keywords:
- source_link_manager
- AGENTS/concurrency::source_link_manager
- AGENTS/concurrency::source_link_manager::source_link_manager
- AGENTS/concurrency::source_link_manager::add
- AGENTS/concurrency::source_link_manager::begin
- AGENTS/concurrency::source_link_manager::contains
- AGENTS/concurrency::source_link_manager::count
- AGENTS/concurrency::source_link_manager::reference
- AGENTS/concurrency::source_link_manager::register_target_block
- AGENTS/concurrency::source_link_manager::release
- AGENTS/concurrency::source_link_manager::remove
- AGENTS/concurrency::source_link_manager::set_bound
helpviewer_keywords:
- source_link_manager class
ms.assetid: 287487cf-e0fe-4c35-aa3c-24f081d1ddae
ms.openlocfilehash: 98f99bb5aec85a640eaf83a07fae3a1b667f7d91
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228426"
---
# <a name="source_link_manager-class"></a>source_link_manager-Klasse

Das `source_link_manager`-Objekt verwaltet Meldungsblock-Netzwerklinks zu `ISource`-Blöcken.

## <a name="syntax"></a>Syntax

```cpp
template<class _LinkRegistry>
class source_link_manager;
```

### <a name="parameters"></a>Parameter

*_LinkRegistry*<br/>
Die Registrierung der Netzwerkverbindung.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|Beschreibung|
|----------|-----------------|
|`const_pointer`|Ein Typ, der einen Zeiger auf ein- **`const`** Element in einem-Objekt bereitstellt `source_link_manager` .|
|`const_reference`|Ein Typ, der einen Verweis auf ein-Element bereitstellt, das **`const`** in einem- `source_link_manager` Objekt zum Lesen und Ausführen von Konstanten Vorgängen gespeichert ist.|
|`iterator`|Ein Typ, der einen Iterator bereitstellt, mit dem jedes Element im-Objekt gelesen oder geändert werden kann `source_link_manager` .|
|`type`|Der Typ der Link Registrierung, der vom- `source_link_manager` Objekt verwaltet wird.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[source_link_manager](#ctor)|Erstellt ein `source_link_manager`-Objekt.|
|[~ source_link_manager-Dekonstruktor](#dtor)|Zerstört das `source_link_manager`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[add](#add)|Fügt dem-Objekt einen quelllink hinzu `source_link_manager` .|
|[beginnen](#begin)|Gibt einen Iterator zum ersten Element im- `source_link_manager` Objekt zurück.|
|[contains](#contains)|Durchsucht den `network_link_registry` innerhalb dieses- `source_link_manager` Objekts nach einem angegebenen-Block.|
|[count](#count)|Zählt die Anzahl der verknüpften Blöcke im- `source_link_manager` Objekt.|
|[Referenz](#reference)|Ruft einen Verweis auf das- `source_link_manager` Objekt ab.|
|[register_target_block](#register_target_block)|Registriert den Zielblock, der dieses- `source_link_manager` Objekt enthält.|
|[Abgabe](#release)|Gibt den Verweis auf das- `source_link_manager` Objekt frei.|
|[remove](#remove)|Entfernt einen Link aus dem- `source_link_manager` Objekt.|
|[set_bound](#set_bound)|Legt die maximale Anzahl von Quell Verknüpfungen fest, die diesem-Objekt hinzugefügt werden können `source_link_manager` .|

## <a name="remarks"></a>Bemerkungen

Derzeit sind die Quell Blöcke Verweis gezählt. Dabei handelt es sich um einen Wrapper für ein `network_link_registry` -Objekt, das gleichzeitigen Zugriff auf die Verknüpfungen ermöglicht und die Möglichkeit bietet, auf die Links durch Rückrufe zu verweisen. Nachrichten Blöcke `target_block` `propagator_block` sollten diese Klasse für Ihre Quell Verknüpfungen verwenden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`source_link_manager`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** agents.h

**Namespace:** Parallelität

## <a name="add"></a><a name="add"></a>eren

Fügt dem-Objekt einen quelllink hinzu `source_link_manager` .

```cpp
void add(_EType _Link);
```

### <a name="parameters"></a>Parameter

*_Link*<br/>
Ein Zeiger auf einen Block, der hinzugefügt werden soll.

## <a name="begin"></a><a name="begin"></a>beginnen

Gibt einen Iterator zum ersten Element im- `source_link_manager` Objekt zurück.

```cpp
iterator begin();
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der das erste Element im-Objekt adressiert `source_link_manager` .

### <a name="remarks"></a>Bemerkungen

Der Endzustand des Iterators wird durch einen Link angegeben `NULL` .

## <a name="contains"></a><a name="contains"></a>Inhalt

Durchsucht den `network_link_registry` innerhalb dieses- `source_link_manager` Objekts nach einem angegebenen-Block.

```cpp
bool contains(_EType _Link);
```

### <a name="parameters"></a>Parameter

*_Link*<br/>
Ein Zeiger auf einen Block, der im-Objekt gesucht werden soll `source_link_manager` .

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der angegebene Block gefunden wurde, **`false`** andernfalls.

## <a name="count"></a><a name="count"></a>Countdown

Zählt die Anzahl der verknüpften Blöcke im- `source_link_manager` Objekt.

```cpp
size_t count();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der verknüpften Blöcke im- `source_link_manager` Objekt.

## <a name="reference"></a><a name="reference"></a>Angabe

Ruft einen Verweis auf das- `source_link_manager` Objekt ab.

```cpp
void reference();
```

## <a name="register_target_block"></a><a name="register_target_block"></a>register_target_block

Registriert den Zielblock, der dieses- `source_link_manager` Objekt enthält.

```cpp
void register_target_block(_Inout_ ITarget<typename _Block::source_type>* _PTarget);
```

### <a name="parameters"></a>Parameter

*_PTarget*<br/>
Der Zielblock, der dieses- `source_link_manager` Objekt enthält.

## <a name="release"></a><a name="release"></a>Abgabe

Gibt den Verweis auf das- `source_link_manager` Objekt frei.

```cpp
void release();
```

## <a name="remove"></a><a name="remove"></a>aufgeh

Entfernt einen Link aus dem- `source_link_manager` Objekt.

```cpp
bool remove(_EType _Link);
```

### <a name="parameters"></a>Parameter

*_Link*<br/>
Ein Zeiger auf einen Block, der entfernt werden soll, sofern gefunden.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der Link gefunden und entfernt wurde, **`false`** andernfalls.

## <a name="set_bound"></a><a name="set_bound"></a>set_bound

Legt die maximale Anzahl von Quell Verknüpfungen fest, die diesem-Objekt hinzugefügt werden können `source_link_manager` .

```cpp
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>Parameter

*_MaxLinks*<br/>
Die maximale Anzahl von Links.

## <a name="source_link_manager"></a><a name="ctor"></a>source_link_manager

Erstellt ein `source_link_manager`-Objekt.

```cpp
source_link_manager();
```

## <a name="source_link_manager"></a><a name="dtor"></a>~ source_link_manager

Zerstört das `source_link_manager`-Objekt.

```cpp
~source_link_manager();
```

## <a name="see-also"></a>Siehe auch

[Parallelitäts Namespace](concurrency-namespace.md)<br/>
[Single_link_registry-Klasse](single-link-registry-class.md)<br/>
[Multi_link_registry-Klasse](multi-link-registry-class.md)
