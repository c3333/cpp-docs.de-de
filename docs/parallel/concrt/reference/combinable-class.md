---
title: combinable-Klasse
ms.date: 11/04/2016
f1_keywords:
- combinable
- PPL/concurrency::combinable
- PPL/concurrency::combinable::combinable
- PPL/concurrency::combinable::clear
- PPL/concurrency::combinable::combine
- PPL/concurrency::combinable::combine_each
- PPL/concurrency::combinable::local
helpviewer_keywords:
- combinable class
ms.assetid: fe0bfbf6-6250-47da-b8d0-f75369f0b5be
ms.openlocfilehash: d445b8ac1d2a8487e9e1ec4f21f63cf5ef071e91
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224967"
---
# <a name="combinable-class"></a>combinable-Klasse

Das `combinable<T>`-Objekt ist dazu gedacht, threadprivate Kopien von Daten bereitzustellen, mit denen sperrenfreie, threadlokale Unterberechnungen in parallelen Algorithmen durchgeführt werden können. Am Ende des Parallelvorgangs können die threadprivaten Unterbrechungen in einem Endergebnis zusammengeführt werden. Diese Klasse kann anstelle einer freigegebenen Variable verwendet werden, und sie kann zu einer Leistungsverbesserung führen, wenn andernfalls Konflikte mit dieser freigegebenen Variable entstehen würden.

## <a name="syntax"></a>Syntax

```cpp
template<typename T>
class combinable;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Datentyp des abschließenden zusammengeführten Ergebnisses. Der Typ muss einen Kopierkonstruktor und einen Standardkonstruktor aufweisen.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[kombinierbar](#ctor)|Ist überladen. Erstellt ein neues `combinable`-Objekt.|
|[~ kombinierbar-Dekonstruktor](#dtor)|Zerstört ein `combinable` -Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[Löschen](#clear)|Löscht alle zwischen Berechnungsergebnisse aus einer vorherigen Verwendung.|
|[Combine](#combine)|Berechnet einen endgültigen Wert aus dem Satz der Thread lokalen unter Berechnungen durch Aufrufen des bereitgestellten funktors "kombinieren".|
|[combine_each](#combine_each)|Berechnet einen Endwert aus dem Satz von Thread lokalen unter Berechnungen, indem der angegebene kombinierungs Funktions tüktor einmal pro Thread lokaler unter Berechnung aufgerufen wird. Das Endergebnis wird vom Funktions Objekt akkumuliert.|
|[nah](#local)|Ist überladen. Gibt einen Verweis auf die Thread private-unter Berechnung zurück.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|----------|-----------------|
|[Operator =](#operator_eq)|Weist ein- `combinable` Objekt aus einem anderen- `combinable` Objekt zu.|

## <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [parallele Container und Objekte](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`combinable`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ppl. h

**Namespace:** Parallelität

## <a name="clear"></a><a name="clear"></a>Klartext

Löscht alle zwischen Berechnungsergebnisse aus einer vorherigen Verwendung.

```cpp
void clear();
```

## <a name="combinable"></a><a name="ctor"></a>combinable

Erstellt ein neues `combinable`-Objekt.

```cpp
combinable();

template <typename _Function>
explicit combinable(_Function _FnInitialize);

combinable(const combinable& _Copy);
```

### <a name="parameters"></a>Parameter

*_Function*<br/>
Der Typ des Initialisierungs-Funktionselement-Objekts.

*_FnInitialize*<br/>
Eine Funktion, die aufgerufen wird, um jeden neuen Thread privaten Wert des Typs zu initialisieren `T` . Er muss einen Funktions Aufrufoperator mit der Signatur unterstützen `T ()` .

*_Copy*<br/>
Ein vorhandenes- `combinable` Objekt, das in dieses kopiert werden soll.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert neue Elemente mit dem Standardkonstruktor für den Typ `T` .

Der zweite Konstruktor initialisiert neue Elemente mithilfe des Initialisierungs-funktors, der als-Parameter angegeben wird `_FnInitialize` .

Der dritte Konstruktor ist der Kopierkonstruktor.

## <a name="combinable"></a><a name="dtor"></a>~ kombinierbar

Zerstört ein `combinable` -Objekt.

```cpp
~combinable();
```

## <a name="combine"></a><a name="combine"></a>Combine

Berechnet einen endgültigen Wert aus dem Satz der Thread lokalen unter Berechnungen durch Aufrufen des bereitgestellten funktors "kombinieren".

```cpp
template<typename _Function>
T combine(_Function _FnCombine) const;
```

### <a name="parameters"></a>Parameter

*_Function*<br/>
Der Typ des Funktions Objekts, das aufgerufen wird, um zwei Thread lokale unter Berechnungen zu kombinieren.

*_FnCombine*<br/>
Das Funktor, das verwendet wird, um die unter Berechnungen zu kombinieren. Die Signatur ist `T (T, T)` oder `T (const T&, const T&)` , und Sie muss assoziativ und kommutativ sein.

### <a name="return-value"></a>Rückgabewert

Das Endergebnis, bei dem alle Thread privaten Teil Berechnungen kombiniert werden.

## <a name="combine_each"></a><a name="combine_each"></a>combine_each

Berechnet einen Endwert aus dem Satz von Thread lokalen unter Berechnungen, indem der angegebene kombinierungs Funktions tüktor einmal pro Thread lokaler unter Berechnung aufgerufen wird. Das Endergebnis wird vom Funktions Objekt akkumuliert.

```cpp
template<typename _Function>
void combine_each(_Function _FnCombine) const;
```

### <a name="parameters"></a>Parameter

*_Function*<br/>
Der Typ des Funktions Objekts, das aufgerufen wird, um eine einzelne Thread lokale unter Berechnung zu kombinieren.

*_FnCombine*<br/>
Das Funktor, das verwendet wird, um eine unter Berechnung zu kombinieren. Die Signatur ist `void (T)` oder `void (const T&)` , und Sie muss assoziativ und kommutativ sein.

## <a name="local"></a><a name="local"></a>nah

Gibt einen Verweis auf die Thread private-unter Berechnung zurück.

```cpp
T& local();

T& local(bool& _Exists);
```

### <a name="parameters"></a>Parameter

*_Exists*<br/>
Ein Verweis auf einen booleschen Wert. Der boolesche Wert, auf den durch dieses Argument verwiesen wird, wird auf festgelegt **`true`** , wenn die unter Berechnung bereits in diesem Thread vorhanden war, und auf festgelegt, **`false`** Wenn dies die erste unter Berechnung für diesen Thread war.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf die Thread private-unter Berechnung.

## <a name="operator"></a><a name="operator_eq"></a>Operator =

Weist ein- `combinable` Objekt aus einem anderen- `combinable` Objekt zu.

```cpp
combinable& operator= (const combinable& _Copy);
```

### <a name="parameters"></a>Parameter

*_Copy*<br/>
Ein vorhandenes- `combinable` Objekt, das in dieses kopiert werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das `combinable`-Objekt.

## <a name="see-also"></a>Siehe auch

[Parallelitäts Namespace](concurrency-namespace.md)
