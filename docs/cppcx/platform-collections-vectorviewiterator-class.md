---
title: Platform::Collections::VectorViewIterator-Klasse
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorViewIterator::VectorViewIterator
helpviewer_keywords:
- VectorViewIterator Class
ms.assetid: be3aa1ae-e6ba-4a06-8d6b-86d8128026f7
ms.openlocfilehash: 01ae4286e996db9819cb697360f6de9c344edd21
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363697"
---
# <a name="platformcollectionsvectorviewiterator-class"></a>Platform::Collections::VectorViewIterator-Klasse

Stellt einen Standardvorlagenbibliotheks-Iterator für Objekte`IVectorView` bereit, die von der Windows-Runtime-Schnittstelle abgeleitet wurden.

`ViewVectorIterator` ist ein Proxyiterator, der Elemente des Typs `VectorProxy<T>`speichert. Allerdings ist das Proxyobjekt fast nie für Benutzercode sichtbar. Weitere Informationen finden Sie unter [Auflistungen (C++/CX)](../cppcx/collections-c-cx.md).

## <a name="syntax"></a>Syntax

```
template <typename T>
class VectorViewIterator;
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Typname der VectorViewIterator-Vorlagenklasse.

### <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|`difference_type`|Ein Zeigerunterschied (ptrdiff_t).|
|`iterator_category`|Die Kategorie eines direkten Iterators (::std::random_access_iterator_tag).|
|`pointer`|Ein Zeiger auf einen internen Typ, der für die Implementierung von VectorViewIterator erforderlich ist.|
|`reference`|Ein Verweis auf einen internen Typ, der für die Implementierung von VectorViewIterator erforderlich ist.|
|`value_type`|Der `T` -Typname.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[VectorViewIterator::VectorViewIterator](#ctor)|Initialisiert eine neue Instanz der VectorViewIterator-Klasse.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[VectorViewIterator::operator- Operator](#operator-minus)|Subtrahiert entweder eine angegebene Anzahl von Elementen vom aktuellen Iterator und bildet einen neuen Iterator, oder subtrahiert einen angegebenen Iterator vom aktuellen Iterator, und gibt die Anzahl von Elementen zwischen den Iteratoren zurück.|
|[VectorViewIterator::operator-- Operator](#operator-decrement)|Dekrementiert den aktuellen VectorViewIterator.|
|[VectorViewIterator::operator!= Operator](#operator-inequality)|Gibt an, ob der aktuelle VectorViewIterator ungleich einem angegebenen VectorViewIterator ist.|
|[VectorViewIterator::operator* Operator](#operator-dereference)|Ruft einen Verweis auf das Element ab, das vom aktuellen VectorViewIterator angegeben wird.|
|[VectorViewIterator::Operator\[\]](#operator-at)|Ruft einen Verweis auf das Element ab, das eine angegebene Verschiebung vom aktuellen VectorViewIterator ist.|
|[VectorViewIterator::operator+ Operator](#operator-plus)|Gibt einen VectorViewIterator zurück, der auf das Element an der angegebenen Verschiebung von dem angegebenen VectorViewIterator verweist.|
|[VectorViewIterator::operator++ Operator](#operator-increment)|Inkrementiert den aktuellen VectorViewIterator.|
|[VectorViewIterator::operator+= Operator](#operator-plus-equals)|Inkrementiert den aktuellen VectorViewIterator um die angegebene Verschiebung.|
|[VectorViewIterator::operator< Operator](#operator-less-than)|Gibt an, ob der aktuelle VectorViewIterator kleiner einem angegebenen VectorViewIterator ist.|
|[VectorViewIterator::operator\<= Operator](#operator-less-than-or-equals)|Gibt an, ob der aktuelle VectorViewIterator kleiner oder gleich einem angegebenen VectorViewIterator ist.|
|[VectorViewIterator::operator-= Operator](#operator-minus-assign)|Dekrementiert den aktuellen VectorViewIterator durch die angegebene Verschiebung.|
|[VectorViewIterator::operator== Operator](#operator-equality)|Gibt an, ob der aktuelle VectorViewIterator gleich einem angegebenen VectorViewIterator ist.|
|[VectorViewIterator::operator>-Operator](#operator-greater-than)|Gibt an, ob der aktuelle VectorViewIterator größer einem angegebenen VectorViewIterator ist.|
|[VectorViewIterator::operator-> Operator](#operator-arrow)|Ruft die Adresse des Elements ab, auf das vom aktuellen VectorViewIterator verwiesen wird.|
|[VectorViewIterator::operator>= Operator](#operator-greater-than-or-equals)|Gibt an, ob der aktuelle VectorViewIterator größer oder gleich einem angegebenen VectorViewIterator ist.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`VectorViewIterator`

### <a name="requirements"></a>Anforderungen

**Header:** collection.h

**Namespace:** Platform::Collections

## <a name="vectorviewiteratoroperator-gt-operator"></a><a name="operator-arrow"></a>VectorViewIterator::operator-&gt; Operator

Ruft die Adresse des Elements ab, auf das vom aktuellen VectorViewIterator verwiesen wird.

### <a name="syntax"></a>Syntax

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>Rückgabewert

Der Wert des Elements, auf das vom aktuellen VectorViewIterator verwiesen wird.

Der Typ des Rückgabewerts ist ein nicht angegebener interner Typ, der für die Implementierung dieses Operators erforderlich ist.

## <a name="vectorviewiteratoroperator---operator"></a><a name="operator-decrement"></a>VectorViewIterator::operator-- Operator

Dekrementiert den aktuellen VectorViewIterator.

### <a name="syntax"></a>Syntax

```
VectorViewIterator& operator--();
VectorViewIterator operator--(int);
```

### <a name="return-value"></a>Rückgabewert

Die erste Syntax dekrementiert den aktuellen VectorViewIterator und gibt ihn dann zurück. Die zweite Syntax gibt eine Kopie des aktuellen VectorViewIterator zurück und dekrementiert dann den aktuellen VectorViewIterator.

### <a name="remarks"></a>Bemerkungen

In der ersten VectorViewIterator-Syntax wird der aktuelle VectorViewIterator vordekrementiert.

In der zweiten Syntax wird der aktuelle VectorViewIterator nachdekrementiert. Der Typ `int` in der zweiten Syntax gibt eine Nach-Dekrementierungsoperation an, keinen tatsächlichen ganzzahligen Operanden.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-dereference"></a>VectorViewIterator::Operatoroperator\*

Ruft einen Verweis auf das Element ab, das vom aktuellen VectorViewIterator angegeben wird.

### <a name="syntax"></a>Syntax

```
reference operator*() const;
```

### <a name="return-value"></a>Rückgabewert

Das vom aktuellen VectorViewIterator angegebene Element.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-equality"></a>VectorViewIterator::operator== Operator

Gibt an, ob der aktuelle VectorViewIterator gleich einem angegebenen VectorViewIterator ist.

### <a name="syntax"></a>Syntax

```
bool operator==(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parameter

*Andere*<br/>
Ein weiterer VectorViewIterator.

### <a name="return-value"></a>Rückgabewert

**true,** wenn `VectorViewIterator` der Strom gleich *anderen*ist; andernfalls **false**.

## <a name="vectorviewiteratoroperatorgt-operator"></a><a name="operator-greater-than"></a>VectorViewIterator::Operatoroperator&gt;

Gibt an, ob der aktuelle VectorViewIterator größer einem angegebenen VectorViewIterator ist.

### <a name="syntax"></a>Syntax

```

bool operator>(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parameter

*Andere*<br/>
Ein weiterer VectorViewIterator.

### <a name="return-value"></a>Rückgabewert

**true,** wenn der aktuelle VectorViewIterator größer als *andere*ist; andernfalls **false**.

## <a name="vectorviewiteratoroperatorgt-operator"></a><a name="operator-greater-than-or-equals"></a>VectorViewIterator::operator&gt;= Operator

Gibt an, `VectorViewIterator` ob der Strom größer `VectorViewIterator`oder gleich der angegebenen ist.

### <a name="syntax"></a>Syntax

```

bool operator>=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parameter

*Andere*<br/>
Ein weiterer VectorViewIterator.

### <a name="return-value"></a>Rückgabewert

**wahr,** wenn `VectorViewIterator` der Strom größer oder gleich *dem anderen*ist; andernfalls **false**.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-increment"></a>VectorViewIterator::operator++ Operator

Inkrementiert den aktuellen VectorViewIterator.

### <a name="syntax"></a>Syntax

```

VectorViewIterator& operator++();
VectorViewIterator operator++(int);
```

### <a name="return-value"></a>Rückgabewert

Die erste Syntax inkrementiert den aktuellen VectorViewIterator und gibt ihn dann zurück. Die zweite Syntax gibt eine Kopie des aktuellen VectorViewIterator zurück und inkrementiert dann den aktuellen VectorViewIterator.

### <a name="remarks"></a>Bemerkungen

In der ersten VectorViewIterator-Syntax wird der aktuelle VectorViewIterator vorinkrementiert.

In der zweiten Syntax wird der aktuelle VectorViewIterator nachinkrementiert. Der Typ `int` in der zweiten Syntax gibt eine Nach-Inkrementierungsoperation an, keinen tatsächlichen ganzzahligen Operanden.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-inequality"></a>VectorViewIterator::operator!= Operator

Gibt an, ob der aktuelle VectorViewIterator ungleich einem angegebenen VectorViewIterator ist.

### <a name="syntax"></a>Syntax

```
bool operator!=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parameter

*Andere*<br/>
Ein weiterer VectorViewIterator.

### <a name="return-value"></a>Rückgabewert

**wahr,** wenn `VectorViewIterator` der Strom nicht gleich *mit anderen*ist; andernfalls **false**.

## <a name="vectorviewiteratoroperatorlt-operator"></a><a name="operator-less-than"></a>VectorViewIterator::Operatoroperator&lt;

Gibt an, ob der aktuelle VectorIterator kleiner einem angegebenen VectorIterator ist.

### <a name="syntax"></a>Syntax

```
bool operator<(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parameter

*Andere*<br/>
Eine andere `VectorIterator`.

### <a name="return-value"></a>Rückgabewert

**true,** wenn `VectorIterator` der Strom kleiner ist als *der andere*; andernfalls **false**.

## <a name="vectorviewiteratoroperatorlt-operator"></a><a name="operator-less-than-or-equals"></a>VectorViewIterator::operator&lt;= Operator

Gibt an, `VectorIterator` ob der Strom kleiner `VectorIterator`oder gleich einer angegebenen ist.

### <a name="syntax"></a>Syntax

```

bool operator<=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parameter

*Andere*<br/>
Eine andere `VectorIterator`.

### <a name="return-value"></a>Rückgabewert

**true,** wenn `VectorIterator` der Strom kleiner oder gleich *dem anderen*ist; andernfalls **false**.

## <a name="vectorviewiteratoroperator--operator"></a><a name="operator-minus"></a>VectorViewIterator::operator- Operator

Subtrahiert entweder eine angegebene Anzahl von Elementen vom aktuellen Iterator und bildet einen neuen Iterator, oder subtrahiert einen angegebenen Iterator vom aktuellen Iterator, und gibt die Anzahl von Elementen zwischen den Iteratoren zurück.

### <a name="syntax"></a>Syntax

```

VectorViewIterator operator-(difference_type n) const;

difference_type operator-(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parameter

*n*<br/>
Eine Anzahl von Elementen.

*Andere*<br/>
Ein weiterer VectorViewIterator.

### <a name="return-value"></a>Rückgabewert

Die erste Operatorsyntax gibt ein VectorViewIterator-Objekt zurück, das `n` Elemente kleiner ist, als der aktuelle VectorViewIterator. Die zweite Operatorsyntax gibt die Anzahl von Elementen zwischen dem aktuellen und dem `other` VectorViewIterator zurück.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-plus-equals"></a>VectorViewIterator::operator+= Operator

Inkrementiert den aktuellen VectorViewIterator um die angegebene Verschiebung.

### <a name="syntax"></a>Syntax

```
VectorViewIterator& operator+=(difference_type n);
```

### <a name="parameters"></a>Parameter

*n*<br/>
Eine ganzzahlige Verschiebung.

### <a name="return-value"></a>Rückgabewert

Der aktualisierte VectorViewIterator.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-plus"></a>VectorViewIterator::operator+ Operator

Gibt einen VectorViewIterator zurück, der auf das Element an der angegebenen Verschiebung von dem angegebenen VectorViewIterator verweist.

### <a name="syntax"></a>Syntax

```

VectorViewIterator operator+(difference_type n) const;

template <typename T>
inline VectorViewIterator<T> operator+
   (ptrdiff_t n,
   const VectorViewIterator<T>& i);
```

### <a name="parameters"></a>Parameter

*T*<br/>
In der zweiten Syntax der Typname vom VectorViewIterator.

*n*<br/>
Eine ganzzahlige Verschiebung.

*Ⅰ*<br/>
In der zweiten Syntax ein VectorViewIterator.

### <a name="return-value"></a>Rückgabewert

In der ersten Syntax ein VectorViewIterator, der auf das Element an der angegebenen Verschiebung vom aktuellen VectorViewIterator verweist.

In der zweiten Syntax ein VectorViewIterator, der auf das Element an der angegebenen Verschiebung vom Anfang des Parameters `i` verweist.

## <a name="vectorviewiteratoroperator--operator"></a><a name="operator-minus-assign"></a>VectorViewIterator::operator-= Operator

Dekrementiert den aktuellen VectorIterator um die angegebene Verschiebung.

### <a name="syntax"></a>Syntax

```
VectorViewIterator& operator-=(difference_type n);
```

### <a name="parameters"></a>Parameter

*n*<br/>
Eine ganzzahlige Verschiebung.

### <a name="return-value"></a>Rückgabewert

Der aktualisierte VectorIterator.

## <a name="vectorviewiteratoroperator"></a><a name="operator-at"></a>VectorViewIterator::Operator\[\]

Ruft einen Verweis auf das Element ab, das eine angegebene Verschiebung vom aktuellen VectorViewIterator ist.

### <a name="syntax"></a>Syntax

```
reference operator[](difference_type n) const;
```

### <a name="parameters"></a>Parameter

*n*<br/>
Eine ganzzahlige Verschiebung.

### <a name="return-value"></a>Rückgabewert

Das Element, das vom aktuellen VectorViewIterator um `n` Elemente verschoben wird.

## <a name="vectorviewiteratorvectorviewiterator-constructor"></a><a name="ctor"></a>VectorViewIterator::VectorViewIterator-Konstruktor

Initialisiert eine neue Instanz der VectorViewIterator-Klasse.

### <a name="syntax"></a>Syntax

```

VectorViewIterator();

explicit VectorViewIterator(
   Windows::Foundation::Collections::IVectorView<T>^ v
);
```

### <a name="parameters"></a>Parameter

*V*<br/>
Ein IVectorView\<T> Objekt.

### <a name="remarks"></a>Bemerkungen

Das erste Syntaxbeispiel ist der Standardkonstruktor. Das zweite Syntaxbeispiel ist ein expliziter Konstruktor, der verwendet wird, um\<einen VectorViewIterator aus einem IVectorView T->-Objekt zu erstellen.

## <a name="see-also"></a>Siehe auch

[Plattform-Namespace](platform-namespace-c-cx.md)
