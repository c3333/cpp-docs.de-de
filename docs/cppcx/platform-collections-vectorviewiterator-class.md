---
title: Platform::Collections::VectorViewIterator-Klasse
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorViewIterator::VectorViewIterator
helpviewer_keywords:
- VectorViewIterator Class
ms.assetid: be3aa1ae-e6ba-4a06-8d6b-86d8128026f7
ms.openlocfilehash: 3fed25b975eefe33f9eb7014ca91a52ba419c936
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211566"
---
# <a name="platformcollectionsvectorviewiterator-class"></a>Platform::Collections::VectorViewIterator-Klasse

Stellt einen Standardvorlagen Bibliothek-Iterator für Objekte bereit, die von der Windows-Runtime- `IVectorView` Schnittstelle abgeleitet werden

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

|name|BESCHREIBUNG|
|----------|-----------------|
|[Vector viewiterator:: Vector viewiterator](#ctor)|Initialisiert eine neue Instanz der VectorViewIterator-Klasse.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Vector viewiterator:: Operator-Operator](#operator-minus)|Subtrahiert entweder eine angegebene Anzahl von Elementen vom aktuellen Iterator und bildet einen neuen Iterator, oder subtrahiert einen angegebenen Iterator vom aktuellen Iterator, und gibt die Anzahl von Elementen zwischen den Iteratoren zurück.|
|[Vector viewiterator:: Operator--Operator](#operator-decrement)|Dekrementiert den aktuellen VectorViewIterator.|
|[Vector viewiterator:: Operator! =-Operator](#operator-inequality)|Gibt an, ob der aktuelle VectorViewIterator ungleich einem angegebenen VectorViewIterator ist.|
|[Vector viewiterator:: Operator *-Operator](#operator-dereference)|Ruft einen Verweis auf das Element ab, das vom aktuellen VectorViewIterator angegeben wird.|
|[Vector viewiterator::-Operator\[\]](#operator-at)|Ruft einen Verweis auf das Element ab, das eine angegebene Verschiebung vom aktuellen VectorViewIterator ist.|
|[Vector viewiterator:: Operator +-Operator](#operator-plus)|Gibt einen VectorViewIterator zurück, der auf das Element an der angegebenen Verschiebung von dem angegebenen VectorViewIterator verweist.|
|[Vector viewiterator:: Operator + +-Operator](#operator-increment)|Inkrementiert den aktuellen VectorViewIterator.|
|[Vector viewiterator:: Operator + =-Operator](#operator-plus-equals)|Inkrementiert den aktuellen VectorViewIterator um die angegebene Verschiebung.|
|[Vector viewiterator:: Operator<-Operator](#operator-less-than)|Gibt an, ob der aktuelle VectorViewIterator kleiner einem angegebenen VectorViewIterator ist.|
|[Vector viewiterator:: Operator \< =-Operator](#operator-less-than-or-equals)|Gibt an, ob der aktuelle VectorViewIterator kleiner oder gleich einem angegebenen VectorViewIterator ist.|
|[Vector viewiterator:: Operator-=-Operator](#operator-minus-assign)|Dekrementiert den aktuellen VectorViewIterator durch die angegebene Verschiebung.|
|[Vector viewiterator:: Operator = =-Operator](#operator-equality)|Gibt an, ob der aktuelle VectorViewIterator gleich einem angegebenen VectorViewIterator ist.|
|[VectorViewIterator::operator>-Operator](#operator-greater-than)|Gibt an, ob der aktuelle VectorViewIterator größer einem angegebenen VectorViewIterator ist.|
|[Vector viewiterator:: Operator->-Operator](#operator-arrow)|Ruft die Adresse des Elements ab, auf das vom aktuellen VectorViewIterator verwiesen wird.|
|[Vector viewiterator:: Operator>=-Operator](#operator-greater-than-or-equals)|Gibt an, ob der aktuelle VectorViewIterator größer oder gleich einem angegebenen VectorViewIterator ist.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`VectorViewIterator`

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** collection.h

**Namespace:** Platform::Collections

## <a name="vectorviewiteratoroperator-gt-operator"></a><a name="operator-arrow"></a>Vector viewiterator:: Operator- &gt; Operator

Ruft die Adresse des Elements ab, auf das vom aktuellen VectorViewIterator verwiesen wird.

### <a name="syntax"></a>Syntax

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>Rückgabewert

Der Wert des Elements, auf das vom aktuellen VectorViewIterator verwiesen wird.

Der Typ des Rückgabewerts ist ein nicht angegebener interner Typ, der für die Implementierung dieses Operators erforderlich ist.

## <a name="vectorviewiteratoroperator---operator"></a><a name="operator-decrement"></a>Vector viewiterator:: Operator--Operator

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

In der zweiten Syntax wird der aktuelle VectorViewIterator nachdekrementiert. Der- **`int`** Typ in der zweiten Syntax gibt eine postdekrement-Operation an, nicht einen tatsächlichen ganzzahligen Operanden.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-dereference"></a>Vector viewiterator:: Operator- \* Operator

Ruft einen Verweis auf das Element ab, das vom aktuellen VectorViewIterator angegeben wird.

### <a name="syntax"></a>Syntax

```
reference operator*() const;
```

### <a name="return-value"></a>Rückgabewert

Das vom aktuellen VectorViewIterator angegebene Element.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-equality"></a>Vector viewiterator:: Operator = =-Operator

Gibt an, ob der aktuelle VectorViewIterator gleich einem angegebenen VectorViewIterator ist.

### <a name="syntax"></a>Syntax

```
bool operator==(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parameter

*außer*<br/>
Ein weiterer VectorViewIterator.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der aktuelle `VectorViewIterator` gleich dem *anderen*ist, andernfalls **`false`** .

## <a name="vectorviewiteratoroperatorgt-operator"></a><a name="operator-greater-than"></a>Vector viewiterator:: Operator- &gt; Operator

Gibt an, ob der aktuelle VectorViewIterator größer einem angegebenen VectorViewIterator ist.

### <a name="syntax"></a>Syntax

```

bool operator>(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parameter

*außer*<br/>
Ein weiterer VectorViewIterator.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der aktuelle Vector viewiterator größer als ein *anderer*ist. andernfalls **`false`** .

## <a name="vectorviewiteratoroperatorgt-operator"></a><a name="operator-greater-than-or-equals"></a>Vector viewiterator:: Operator &gt; =-Operator

Gibt an, ob die aktuelle `VectorViewIterator` größer oder gleich der angegebenen ist `VectorViewIterator` .

### <a name="syntax"></a>Syntax

```

bool operator>=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parameter

*außer*<br/>
Ein weiterer VectorViewIterator.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der aktuelle `VectorViewIterator` größer als oder gleich einem *anderen*ist, andernfalls **`false`** .

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-increment"></a>Vector viewiterator:: Operator + +-Operator

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

In der zweiten Syntax wird der aktuelle VectorViewIterator nachinkrementiert. Der **`int`** Typ in der zweiten Syntax gibt einen Vorgang nach dem Inkrement an, nicht einen tatsächlichen ganzzahligen Operanden.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-inequality"></a>Vector viewiterator:: Operator! =-Operator

Gibt an, ob der aktuelle VectorViewIterator ungleich einem angegebenen VectorViewIterator ist.

### <a name="syntax"></a>Syntax

```
bool operator!=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parameter

*außer*<br/>
Ein weiterer VectorViewIterator.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der aktuelle `VectorViewIterator` nicht gleich dem *anderen*ist, andernfalls **`false`** .

## <a name="vectorviewiteratoroperatorlt-operator"></a><a name="operator-less-than"></a>Vector viewiterator:: Operator- &lt; Operator

Gibt an, ob der aktuelle VectorIterator kleiner einem angegebenen VectorIterator ist.

### <a name="syntax"></a>Syntax

```
bool operator<(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parameter

*außer*<br/>
Eine andere `VectorIterator`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der aktuelle `VectorIterator` kleiner als ein *anderer*ist, andernfalls **`false`** .

## <a name="vectorviewiteratoroperatorlt-operator"></a><a name="operator-less-than-or-equals"></a>Vector viewiterator:: Operator &lt; =-Operator

Gibt an, ob der aktuelle `VectorIterator` kleiner als oder gleich einem angegebenen ist `VectorIterator` .

### <a name="syntax"></a>Syntax

```

bool operator<=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parameter

*außer*<br/>
Eine andere `VectorIterator`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der aktuelle `VectorIterator` kleiner als oder gleich einem *anderen*ist, andernfalls **`false`** .

## <a name="vectorviewiteratoroperator--operator"></a><a name="operator-minus"></a>Vector viewiterator:: Operator-Operator

Subtrahiert entweder eine angegebene Anzahl von Elementen vom aktuellen Iterator und bildet einen neuen Iterator, oder subtrahiert einen angegebenen Iterator vom aktuellen Iterator, und gibt die Anzahl von Elementen zwischen den Iteratoren zurück.

### <a name="syntax"></a>Syntax

```

VectorViewIterator operator-(difference_type n) const;

difference_type operator-(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parameter

*n*<br/>
Eine Anzahl von Elementen.

*außer*<br/>
Ein weiterer VectorViewIterator.

### <a name="return-value"></a>Rückgabewert

Die erste Operatorsyntax gibt ein VectorViewIterator-Objekt zurück, das `n` Elemente kleiner ist, als der aktuelle VectorViewIterator. Die zweite Operatorsyntax gibt die Anzahl von Elementen zwischen dem aktuellen und dem `other` VectorViewIterator zurück.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-plus-equals"></a>Vector viewiterator:: Operator + =-Operator

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

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-plus"></a>Vector viewiterator:: Operator +-Operator

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

*i*<br/>
In der zweiten Syntax ein VectorViewIterator.

### <a name="return-value"></a>Rückgabewert

In der ersten Syntax ein VectorViewIterator, der auf das Element an der angegebenen Verschiebung vom aktuellen VectorViewIterator verweist.

In der zweiten Syntax ein VectorViewIterator, der auf das Element an der angegebenen Verschiebung vom Anfang des Parameters `i` verweist.

## <a name="vectorviewiteratoroperator--operator"></a><a name="operator-minus-assign"></a>Vector viewiterator:: Operator-=-Operator

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

## <a name="vectorviewiteratoroperator"></a><a name="operator-at"></a>Vector viewiterator::-Operator\[\]

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

## <a name="vectorviewiteratorvectorviewiterator-constructor"></a><a name="ctor"></a>Vectorviewiterator:: vectorviewiterator-Konstruktor

Initialisiert eine neue Instanz der VectorViewIterator-Klasse.

### <a name="syntax"></a>Syntax

```

VectorViewIterator();

explicit VectorViewIterator(
   Windows::Foundation::Collections::IVectorView<T>^ v
);
```

### <a name="parameters"></a>Parameter

*Ramelow*<br/>
Ein ivectorview- \<T> Objekt.

### <a name="remarks"></a>Bemerkungen

Das erste Syntaxbeispiel ist der Standardkonstruktor. Das zweite Syntax Beispiel ist ein expliziter Konstruktor, der zum Erstellen eines vectorviewiterator-Objekts aus einem ivectorview-Objekt verwendet wird \<T> .

## <a name="see-also"></a>Weitere Informationen

[Platform-Namespace](platform-namespace-c-cx.md)
