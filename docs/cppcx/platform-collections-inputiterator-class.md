---
title: Platform::Collections::InputIterator-Klasse
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::InputIterator::InputIterator
helpviewer_keywords:
- InputIterator Class
ms.assetid: ef72eea4-32a9-42b9-8119-ce87dbdcd3be
ms.openlocfilehash: 92f9b15f474a5aa3d063f0ccfb663f56baf8de31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354568"
---
# <a name="platformcollectionsinputiterator-class"></a>Platform::Collections::InputIterator-Klasse

Stellt einen Standardvorlagenbibliotheks-InputIterator für Sammlungen bereit, die von der Windows-Runtime abgeleitet wurden.

## <a name="syntax"></a>Syntax

```
template <typename X>
class InputIterator;
```

#### <a name="parameters"></a>Parameter

*X*<br/>
Der Typname der InputIterator-Vorlagenklasse.

### <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|`difference_type`|Ein Zeigerunterschied (ptrdiff_t).|
|`iterator_category`|Die Kategorie eines Eingabeiterators (::std::input_iterator_tag).|
|`pointer`|Ein Zeiger auf eine `const X`|
|`reference`|Ein Verweis auf eine `const X`|
|`value_type`|Der `X` -Typname.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[InputIterator::InputIterator](#ctor)|Initialisiert eine neue Instanz der InputIterator-Klasse.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[InputIterator::operator!= Operator](#operator-inequality)|Gibt an, ob der aktuelle InputIterator ungleich einem angegebenen InputIterator ist.|
|[InputIterator::operator*-Operator](#operator-dereference)|Ruft einen Verweis auf das Element ab, das vom aktuellen InputIterator angegeben wird.|
|[InputIterator::operator++ Operator](#operator-increment)|Inkrementiert den aktuellen InputIterator.|
|[InputIterator::operator== Operator](#operator-equality)|Gibt an, ob der aktuelle InputIterator gleich einem angegebenen InputIterator ist.|
|[InputIterator::operator-> Operator](#operator-arrow)|Ruft die Adresse des Elements ab, auf das vom aktuellen InputIterator verwiesen wird.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`InputIterator`

### <a name="requirements"></a>Anforderungen

**Header:** collection.h

**Namespace:** Platform::Collections

## <a name="inputiteratorinputiterator-constructor"></a><a name="ctor"></a>InputIterator::InputIterator-Konstruktor

Initialisiert eine neue Instanz der InputIterator-Klasse.

### <a name="syntax"></a>Syntax

```
InputIterator();
explicit InputIterator(Windows::Foundation::Collections<X>^ iterator);
```

### <a name="parameters"></a>Parameter

*Iterator*<br/>
Ein Iteratorobjekt.

## <a name="inputiteratoroperator-gt-operator"></a><a name="operator-arrow"></a>InputIterator::operator-&gt; Operator

Ruft die Adresse des Elements ab, das vom aktuellen InputIterator angegeben wird.

### <a name="syntax"></a>Syntax

```
pointer operator->() const;
```

### <a name="return-value"></a>Rückgabewert

Die Adresse des Elements, das vom aktuellen InputIterator angegeben wird.

## <a name="inputiteratoroperator-operator"></a><a name="operator-dereference"></a>InputIterator::operator\* Operator

Ruft einen Verweis auf das Element ab, das vom aktuellen InputIterator angegeben wird.

### <a name="syntax"></a>Syntax

```
reference operator*() const;
```

### <a name="return-value"></a>Rückgabewert

Das Element, das durch den aktuellen InputIterator angegeben wird.

## <a name="inputiteratoroperator-operator"></a><a name="operator-equality"></a>InputIterator::operator== Operator

Gibt an, ob der aktuelle InputIterator gleich einem angegebenen InputIterator ist.

### <a name="syntax"></a>Syntax

```
bool operator== (const InputIterator& other) const;
```

### <a name="parameters"></a>Parameter

*Andere*<br/>
Ein weiterer InputIterator.

### <a name="return-value"></a>Rückgabewert

**true,** wenn der aktuelle InputIterator gleich *anderen*ist; andernfalls **false**.

## <a name="inputiteratoroperator-operator"></a><a name="operator-increment"></a>InputIterator::operator++ Operator

Inkrementiert den aktuellen InputIterator.

### <a name="syntax"></a>Syntax

```
InputIterator& operator++();
InputIterator operator++(int);
```

### <a name="return-value"></a>Rückgabewert

Die erste Syntax inkrementiert den aktuellen InputIterator und gibt ihn dann zurück. Die zweite Syntax gibt eine Kopie des aktuellen InputIterator zurück und inkrementiert dann den aktuellen InputIterator.

### <a name="remarks"></a>Bemerkungen

Die ersten InputIterator-Syntax vorinkrementiert den aktuellen InputIterator.

Die zweite Syntax nachinkrementiert den aktuellen InputIterator. Der Typ `int` in der zweiten Syntax gibt eine Nach-Inkrementierungsoperation an, keinen tatsächlichen ganzzahligen Operanden.

## <a name="inputiteratoroperator-operator"></a><a name="operator-inequality"></a>InputIterator::operator!= Operator

Gibt an, ob der aktuelle InputIterator ungleich einem angegebenen InputIterator ist.

### <a name="syntax"></a>Syntax

```
bool operator!=(const InputIterator& other) const;
```

### <a name="parameters"></a>Parameter

*Andere*<br/>
Ein weiterer InputIterator.

### <a name="return-value"></a>Rückgabewert

**true,** wenn der aktuelle InputIterator nicht gleich *mit anderen*ist; andernfalls **false**.

## <a name="see-also"></a>Siehe auch

[Plattform-Namespace](platform-namespace-c-cx.md)
