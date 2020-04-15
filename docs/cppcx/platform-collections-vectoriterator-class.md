---
title: Platform::Collections::VectorIterator-Klasse
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorIterator::VectorIterator
helpviewer_keywords:
- VectorIterator Class
ms.assetid: d531cb42-27e0-48a6-bf5e-c265891a18ff
ms.openlocfilehash: e649027c2ba3f637c42765af691f4d321913fb28
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354367"
---
# <a name="platformcollectionsvectoriterator-class"></a>Platform::Collections::VectorIterator-Klasse

Stellt einen Standardvorlagenbibliotheks-Iterator für Objekte bereit, die von der Windows Runtime IVector-Schnittstelle abgeleitet wurden.

VectorIterator ist ein Proxy-Iterator, der\<Elemente vom Typ VectorProxy T> speichert. Allerdings ist das Proxyobjekt fast nie für Benutzercode sichtbar. Weitere Informationen finden Sie unter [Auflistungen (C++/CX)](../cppcx/collections-c-cx.md).

## <a name="syntax"></a>Syntax

```
template <typename T>
class VectorIterator;
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Typname der VectorIterator-Vorlagenklasse.

### <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|`difference_type`|Ein Zeigerunterschied (ptrdiff_t).|
|`iterator_category`|Die Kategorie eines direkten Iterators (::std::random_access_iterator_tag).|
|`pointer`|Ein Zeiger auf einen internen Typ, Platform::Collections::Details::VectorProxy\<T>, der für die Implementierung von VectorIterator erforderlich ist.|
|`reference`|Ein Verweis auf einen internen Typ, Platform::Collections::Details::VectorProxy\<T>, der für die Implementierung von VectorIterator erforderlich ist.|
|`value_type`|Der `T` -Typname.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[VectorIterator::VectorIterator](#ctor)|Initialisiert eine neue Instanz der VectorIterator-Klasse.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[VectorIterator::operator- Operator](#operator-minus)|Subtrahiert entweder eine angegebene Anzahl von Elementen vom aktuellen Iterator und bildet einen neuen Iterator, oder subtrahiert einen angegebenen Iterator vom aktuellen Iterator, und gibt die Anzahl von Elementen zwischen den Iteratoren zurück.|
|[VectorIterator::operator-- Operator](#operator-decrement)|Dekrementiert den aktuellen VectorIterator.|
|[VectorIterator::operator!= Operator](#operator-inequality)|Gibt an, ob der aktuelle VectorIterator ungleich einem angegebenen VectorIterator ist.|
|[VectorIterator::operator* Operator](#operator-dereference)|Ruft einen Verweis auf das Element ab, das vom aktuellen VectorIterator angegeben wird.|
|[VectorIterator::Operator\[\]](#operator-at)|Ruft einen Verweis auf das Element ab, das eine angegebene Verschiebung vom aktuellen VectorIterator ist.|
|[VectorIterator::operator+ Operator](#operator-plus)|Gibt einen VectorIterator zurück, der auf das Element an der angegebenen Verschiebung von dem angegebenen VectorIterator verweist.|
|[VectorIterator::operator++ Operator](#operator-increment)|Inkrementiert den aktuellen VectorIterator.|
|[VectorIterator::operator+= Operator](#operator-plus-assign)|Inkrementiert den aktuellen VectorIterator um die angegebene Verschiebung.|
|[VectorIterator::operator< Operator](#operator-less-than)|Gibt an, ob der aktuelle VectorIterator kleiner einem angegebenen VectorIterator ist.|
|[VectorIterator::operator\<= Operator](#operator-less-than-or-equals)|Gibt an, ob der aktuelle VectorIterator kleiner oder gleich einem angegebenen VectorIterator ist.|
|[VectorIterator::operator-= Operator](#operator-minus-equals)|Dekrementiert den aktuellen VectorIterator um die angegebene Verschiebung.|
|[VectorIterator::operator== Operator](#operator-equality)|Gibt an, ob der aktuelle VectorIterator gleich einem angegebenen VectorIterator ist.|
|[VectorIterator::operator>-Operator](#operator-greater-than)|Gibt an, ob der aktuelle VectorIterator größer als ein angegebener VectorIterator ist.|
|[VectorIterator::operator-> Operator](#operator-arrow)|Ruft die Adresse des Elements ab, auf das vom aktuellen VectorIterator verwiesen wird.|
|[VectorIterator::operator>= Operator](#operator-greater-than-or-equals)|Gibt an, ob der aktuelle VectorIterator größer oder gleich einem angegebenen VectorIterator ist.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`VectorIterator`

### <a name="requirements"></a>Anforderungen

**Header:** collection.h

**Namespace:** Platform::Collections

## <a name="vectoriteratoroperator-gt-operator"></a><a name="operator-arrow"></a>VectorIterator::operator-&gt; Operator

Ruft die Adresse des Elements ab, auf das vom aktuellen VectorIterator verwiesen wird.

### <a name="syntax"></a>Syntax

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>Rückgabewert

Der Wert des Elements, auf das vom aktuellen VectorIterator verwiesen wird.

Der Typ des Rückgabewerts ist ein nicht angegebener interner Typ, der für die Implementierung dieses Operators erforderlich ist.

## <a name="vectoriteratoroperator---operator"></a><a name="operator-decrement"></a>VectorIterator::operator-- Operator

Dekrementiert den aktuellen VectorIterator.

### <a name="syntax"></a>Syntax

```

VectorIterator& operator--();
VectorIterator operator--(int);
```

### <a name="return-value"></a>Rückgabewert

Die erste Syntax dekrementiert und gibt dann den aktuellen VectorIterator zurück. Die zweite Syntax gibt eine Kopie des aktuellen VectorIterator zurück und dekrementiert dann den aktuellen VectorIterator.

### <a name="remarks"></a>Bemerkungen

Die erste VectorIterator-Syntax prädekrementiert den aktuellen VectorIterator.

Die zweite Syntax postdekrementiert den aktuellen VectorIterator. Der Typ `int` in der zweiten Syntax gibt eine Nach-Dekrementierungsoperation an, keinen tatsächlichen ganzzahligen Operanden.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-dereference"></a>VectorIterator::Operatoroperator\*

Ruft die Adresse des Elements ab, das vom aktuellen VectorIterator angegeben wird.

### <a name="syntax"></a>Syntax

```
reference operator*() const;
```

### <a name="return-value"></a>Rückgabewert

Das vom aktuellen VectorIterator angegebene Element.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-equality"></a>VectorIterator::operator== Operator

Gibt an, ob der aktuelle VectorIterator gleich einem angegebenen VectorIterator ist.

### <a name="syntax"></a>Syntax

```
bool operator==(const VectorIterator& other) const;
```

### <a name="parameters"></a>Parameter

*Andere*<br/>
Ein weiterer VectorIterator.

### <a name="return-value"></a>Rückgabewert

**true,** wenn der aktuelle VectorIterator gleich *anderen*ist; andernfalls **false**.

## <a name="vectoriteratoroperatorgt-operator"></a><a name="operator-greater-than"></a>VectorIterator::Operatoroperator&gt;

Gibt an, ob der aktuelle VectorIterator größer als ein angegebener VectorIterator ist.

### <a name="syntax"></a>Syntax

```cpp
bool operator>(const VectorIterator& other) const
```

### <a name="parameters"></a>Parameter

*Andere*<br/>
Ein weiterer VectorIterator.

### <a name="return-value"></a>Rückgabewert

**true,** wenn der aktuelle VectorIterator größer als *andere*ist; andernfalls **false**.

## <a name="vectoriteratoroperatorgt-operator"></a><a name="operator-greater-than-or-equals"></a>VectorIterator::operator&gt;= Operator

Gibt an, ob der aktuelle VectorIterator größer oder gleich dem angegebenen VectorIterator ist.

### <a name="syntax"></a>Syntax

```cpp
bool operator>=(const VectorIterator& other) const
```

### <a name="parameters"></a>Parameter

*Andere*<br/>
Ein weiterer VectorIterator.

### <a name="return-value"></a>Rückgabewert

**true,** wenn der aktuelle VectorIterator größer oder gleich *anderen*ist; andernfalls **false**.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-increment"></a>VectorIterator::operator++ Operator

Inkrementiert den aktuellen VectorIterator.

### <a name="syntax"></a>Syntax

```
VectorIterator& operator++();
VectorIterator operator++(int);
```

### <a name="return-value"></a>Rückgabewert

Die erste Syntax inkrementiert und gibt dann den aktuellen VectorIterator zurück. Die zweite Syntax gibt eine Kopie des aktuellen VectorIterator zurück und inkrementiert dann den aktuellen VectorIterator.

### <a name="remarks"></a>Bemerkungen

Die erste VectorIterator-Syntax präinkrementiert den aktuellen VectorIterator.

Die zweite Syntax postinkrementiert den aktuellen VectorIterator. Der Typ `int` in der zweiten Syntax gibt eine Nach-Inkrementierungsoperation an, keinen tatsächlichen ganzzahligen Operanden.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-inequality"></a>VectorIterator::operator!= Operator

Gibt an, ob der aktuelle VectorIterator ungleich einem angegebenen VectorIterator ist.

### <a name="syntax"></a>Syntax

```
bool operator!=(const VectorIterator& other) const;
```

### <a name="parameters"></a>Parameter

*Andere*<br/>
Ein weiterer VectorIterator.

### <a name="return-value"></a>Rückgabewert

**true,** wenn der aktuelle VectorIterator nicht gleich *mit anderen*ist; andernfalls **false**.

## <a name="vectoriteratoroperatorlt-operator"></a><a name="operator-less-than"></a>VectorIterator::Operatoroperator&lt;

Gibt an, ob der aktuelle VectorIterator kleiner einem angegebenen VectorIterator ist.

### <a name="syntax"></a>Syntax

```cpp
bool operator<(const VectorIterator& other) const
```

### <a name="parameters"></a>Parameter

*Andere*<br/>
Ein weiterer VectorIterator.

### <a name="return-value"></a>Rückgabewert

**true,** wenn der aktuelle VectorIterator kleiner ist als *andere*; andernfalls **false**.

## <a name="vectoriteratoroperatorlt-operator"></a><a name="operator-less-than-or-equals"></a>VectorIterator::operator&lt;= Operator

Gibt an, ob der aktuelle VectorIterator kleiner oder gleich einem angegebenen VectorIterator ist.

### <a name="syntax"></a>Syntax

```cpp
bool operator<=(const VectorIterator& other) const
```

### <a name="parameters"></a>Parameter

*Andere*<br/>
Ein weiterer VectorIterator.

### <a name="return-value"></a>Rückgabewert

**true,** wenn der aktuelle VectorIterator kleiner oder gleich *anderen*ist; andernfalls **false**.

## <a name="vectoriteratoroperator--operator"></a><a name="operator-minus"></a>VectorIterator::operator- Operator

Subtrahiert entweder eine angegebene Anzahl von Elementen vom aktuellen Iterator und bildet einen neuen Iterator, oder subtrahiert einen angegebenen Iterator vom aktuellen Iterator, und gibt die Anzahl von Elementen zwischen den Iteratoren zurück.

### <a name="syntax"></a>Syntax

```

VectorIterator operator-(difference_type n) const;

difference_type operator-(const VectorIterator& other) const;
```

### <a name="parameters"></a>Parameter

*n*<br/>
Eine Anzahl von Elementen.

*Andere*<br/>
Ein weiterer VectorIterator.

### <a name="return-value"></a>Rückgabewert

Die erste Operatorsyntax gibt ein VectorIterator-Objekt zurück, das `n` Elemente kleiner ist, als der aktuelle VectorIterator. Die zweite Operatorsyntax gibt die Anzahl von Elementen zwischen dem aktuellen und dem `other` VectorIterator zurück.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-plus-assign"></a>VectorIterator::operator+= Operator

Inkrementiert den aktuellen VectorIterator um die angegebene Verschiebung.

### <a name="syntax"></a>Syntax

```
VectorIterator& operator+=(difference_type n);
```

### <a name="parameters"></a>Parameter

*n*<br/>
Eine ganzzahlige Verschiebung.

### <a name="return-value"></a>Rückgabewert

Der aktualisierte VectorIterator.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-plus"></a>VectorIterator::operator+ Operator

Gibt einen VectorIterator zurück, der auf das Element an der angegebenen Verschiebung von dem angegebenen VectorIterator verweist.

### <a name="syntax"></a>Syntax

```

VectorIterator operator+(difference_type n);

template <typename T>
inline VectorIterator<T> operator+(
  ptrdiff_t n,
  const VectorIterator<T>& i);
```

### <a name="parameters"></a>Parameter

*T*<br/>
In der zweiten Syntax der Typname vom VectorIterator.

*n*<br/>
Eine ganzzahlige Verschiebung.

*Ⅰ*<br/>
In der zweiten Syntax ein VectorIterator.

### <a name="return-value"></a>Rückgabewert

In der ersten Syntax ein VectorIterator, der auf das Element an der angegebenen Verschiebung vom aktuellen VectorIterator verweist.

In der zweiten Syntax ein VectorIterator, der auf das Element an der angegebenen Verschiebung vom Anfang des Parameters `i` verweist.

### <a name="remarks"></a>Bemerkungen

Das erste Syntaxbeispiel

## <a name="vectoriteratoroperator--operator"></a><a name="operator-minus-equals"></a>VectorIterator::operator-= Operator

Dekrementiert den aktuellen VectorIterator um die angegebene Verschiebung.

### <a name="syntax"></a>Syntax

```
VectorIterator& operator-=(difference_type n);
```

### <a name="parameters"></a>Parameter

*n*<br/>
Eine ganzzahlige Verschiebung.

### <a name="return-value"></a>Rückgabewert

Der aktualisierte VectorIterator.

## <a name="vectoriteratoroperator"></a><a name="operator-at"></a>VectorIterator::Operator\[\]

Ruft einen Verweis auf das Element ab, das eine angegebene Verschiebung vom aktuellen VectorIterator ist.

### <a name="syntax"></a>Syntax

```
reference operator[](difference_type n) const;
```

### <a name="parameters"></a>Parameter

*n*<br/>
Eine ganzzahlige Verschiebung.

### <a name="return-value"></a>Rückgabewert

Das Element, das vom aktuellen VectorIterator durch die `n`-Elemente ersetzt wird.

## <a name="vectoriteratorvectoriterator-constructor"></a><a name="ctor"></a>VectorIterator::VectorIterator Konstruktor

Initialisiert eine neue Instanz der VectorIterator-Klasse.

### <a name="syntax"></a>Syntax

```
VectorIterator();

explicit VectorIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

### <a name="parameters"></a>Parameter

*V*<br/>
Ein IVector\<T> Objekt.

### <a name="remarks"></a>Bemerkungen

Das erste Syntaxbeispiel ist der Standardkonstruktor. Das zweite Syntaxbeispiel ist ein expliziter Konstruktor, der verwendet wird,\<um einen VectorIterator aus einem IVector T>-Objekt zu erstellen.

## <a name="see-also"></a>Siehe auch

[Plattform-Namespace](platform-namespace-c-cx.md)
