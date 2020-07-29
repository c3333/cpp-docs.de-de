---
title: Platform::Collections::InputIterator-Klasse
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::InputIterator::InputIterator
helpviewer_keywords:
- InputIterator Class
ms.assetid: ef72eea4-32a9-42b9-8119-ce87dbdcd3be
ms.openlocfilehash: 4aeef07a34c04bd1ab47acf808026024faada567
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218428"
---
# <a name="platformcollectionsinputiterator-class"></a>Platform::Collections::InputIterator-Klasse

Stellt einen InputIterator der Standard Vorlagen Bibliothek für Auflistungen bereit, die vom Windows-Runtime abgeleitet werden.

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

|name|BESCHREIBUNG|
|----------|-----------------|
|[InputIterator:: InputIterator](#ctor)|Initialisiert eine neue Instanz der InputIterator-Klasse.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[InputIterator:: Operator! =-Operator](#operator-inequality)|Gibt an, ob der aktuelle InputIterator ungleich einem angegebenen InputIterator ist.|
|[InputIterator::operator*-Operator](#operator-dereference)|Ruft einen Verweis auf das Element ab, das vom aktuellen InputIterator angegeben wird.|
|[InputIterator:: Operator + +-Operator](#operator-increment)|Inkrementiert den aktuellen InputIterator.|
|[InputIterator:: Operator = =-Operator](#operator-equality)|Gibt an, ob der aktuelle InputIterator gleich einem angegebenen InputIterator ist.|
|[InputIterator:: Operator->-Operator](#operator-arrow)|Ruft die Adresse des Elements ab, auf das vom aktuellen InputIterator verwiesen wird.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`InputIterator`

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** collection.h

**Namespace:** Platform::Collections

## <a name="inputiteratorinputiterator-constructor"></a><a name="ctor"></a>InputIterator:: InputIterator-Konstruktor

Initialisiert eine neue Instanz der InputIterator-Klasse.

### <a name="syntax"></a>Syntax

```
InputIterator();
explicit InputIterator(Windows::Foundation::Collections<X>^ iterator);
```

### <a name="parameters"></a>Parameter

*Iterator*<br/>
Ein Iteratorobjekt.

## <a name="inputiteratoroperator-gt-operator"></a><a name="operator-arrow"></a>InputIterator:: Operator- &gt; Operator

Ruft die Adresse des Elements ab, das vom aktuellen InputIterator angegeben wird.

### <a name="syntax"></a>Syntax

```
pointer operator->() const;
```

### <a name="return-value"></a>Rückgabewert

Die Adresse des Elements, das vom aktuellen InputIterator angegeben wird.

## <a name="inputiteratoroperator-operator"></a><a name="operator-dereference"></a>InputIterator:: Operator- \* Operator

Ruft einen Verweis auf das Element ab, das vom aktuellen InputIterator angegeben wird.

### <a name="syntax"></a>Syntax

```
reference operator*() const;
```

### <a name="return-value"></a>Rückgabewert

Das Element, das durch den aktuellen InputIterator angegeben wird.

## <a name="inputiteratoroperator-operator"></a><a name="operator-equality"></a>InputIterator:: Operator = =-Operator

Gibt an, ob der aktuelle InputIterator gleich einem angegebenen InputIterator ist.

### <a name="syntax"></a>Syntax

```
bool operator== (const InputIterator& other) const;
```

### <a name="parameters"></a>Parameter

*außer*<br/>
Ein weiterer InputIterator.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der aktuelle InputIterator gleich einem *anderen*ist. andernfalls **`false`** .

## <a name="inputiteratoroperator-operator"></a><a name="operator-increment"></a>InputIterator:: Operator + +-Operator

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

Die zweite Syntax nachinkrementiert den aktuellen InputIterator. Der **`int`** Typ in der zweiten Syntax gibt einen Vorgang nach dem Inkrement an, nicht einen tatsächlichen ganzzahligen Operanden.

## <a name="inputiteratoroperator-operator"></a><a name="operator-inequality"></a>InputIterator:: Operator! =-Operator

Gibt an, ob der aktuelle InputIterator ungleich einem angegebenen InputIterator ist.

### <a name="syntax"></a>Syntax

```
bool operator!=(const InputIterator& other) const;
```

### <a name="parameters"></a>Parameter

*außer*<br/>
Ein weiterer InputIterator.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der aktuelle InputIterator nicht gleich dem *anderen*ist. andernfalls **`false`** .

## <a name="see-also"></a>Weitere Informationen

[Platform-Namespace](platform-namespace-c-cx.md)
