---
title: Platform::Collections::VectorIterator-Klasse
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorIterator::VectorIterator
helpviewer_keywords:
- VectorIterator Class
ms.assetid: d531cb42-27e0-48a6-bf5e-c265891a18ff
ms.openlocfilehash: bade67a104774c3ab6187e250c6faf6969002c0c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218415"
---
# <a name="platformcollectionsvectoriterator-class"></a>Platform::Collections::VectorIterator-Klasse

Stellt einen Standardvorlagen Bibliothek-Iterator für Objekte bereit, die von der Windows-Runtime IVector-Schnittstelle abgeleitet werden

Vectoriterator ist ein proxyiterator, der Elemente des Typs vectorproxy speichert \<T> . Allerdings ist das Proxyobjekt fast nie für Benutzercode sichtbar. Weitere Informationen finden Sie unter [Auflistungen (C++/CX)](../cppcx/collections-c-cx.md).

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
|`pointer`|Ein Zeiger auf einen internen Typ, Platform:: Collections::D etails:: vectorproxy \<T> , der für die Implementierung von vectoriterator erforderlich ist.|
|`reference`|Ein Verweis auf einen internen Typ, Platform:: Collections::D etails:: vectorproxy \<T> ,, der für die Implementierung von vectoriterator erforderlich ist.|
|`value_type`|Der `T` -Typname.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|BESCHREIBUNG|
|----------|-----------------|
|[Vectoriterator:: vectoriterator](#ctor)|Initialisiert eine neue Instanz der VectorIterator-Klasse.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Vectoriterator:: Operator-Operator](#operator-minus)|Subtrahiert entweder eine angegebene Anzahl von Elementen vom aktuellen Iterator und bildet einen neuen Iterator, oder subtrahiert einen angegebenen Iterator vom aktuellen Iterator, und gibt die Anzahl von Elementen zwischen den Iteratoren zurück.|
|[Vectoriterator:: Operator--Operator](#operator-decrement)|Dekrementiert den aktuellen VectorIterator.|
|[Vectoriterator:: Operator! =-Operator](#operator-inequality)|Gibt an, ob der aktuelle VectorIterator ungleich einem angegebenen VectorIterator ist.|
|[Vectoriterator:: Operator *-Operator](#operator-dereference)|Ruft einen Verweis auf das Element ab, das vom aktuellen VectorIterator angegeben wird.|
|[Vectoriterator::-Operator\[\]](#operator-at)|Ruft einen Verweis auf das Element ab, das eine angegebene Verschiebung vom aktuellen VectorIterator ist.|
|[Vectoriterator:: Operator +-Operator](#operator-plus)|Gibt einen VectorIterator zurück, der auf das Element an der angegebenen Verschiebung von dem angegebenen VectorIterator verweist.|
|[Vectoriterator:: Operator + +-Operator](#operator-increment)|Inkrementiert den aktuellen VectorIterator.|
|[Vectoriterator:: Operator + =-Operator](#operator-plus-assign)|Inkrementiert den aktuellen VectorIterator um die angegebene Verschiebung.|
|[Vectoriterator:: Operator<-Operator](#operator-less-than)|Gibt an, ob der aktuelle VectorIterator kleiner einem angegebenen VectorIterator ist.|
|[Vectoriterator:: Operator \< =-Operator](#operator-less-than-or-equals)|Gibt an, ob der aktuelle VectorIterator kleiner oder gleich einem angegebenen VectorIterator ist.|
|[Vectoriterator:: Operator-=-Operator](#operator-minus-equals)|Dekrementiert den aktuellen VectorIterator um die angegebene Verschiebung.|
|[Vectoriterator:: Operator = =-Operator](#operator-equality)|Gibt an, ob der aktuelle VectorIterator gleich einem angegebenen VectorIterator ist.|
|[VectorIterator::operator>-Operator](#operator-greater-than)|Gibt an, ob der aktuelle VectorIterator größer als ein angegebener VectorIterator ist.|
|[Vectoriterator:: Operator->-Operator](#operator-arrow)|Ruft die Adresse des Elements ab, auf das vom aktuellen VectorIterator verwiesen wird.|
|[Vectoriterator:: Operator>=-Operator](#operator-greater-than-or-equals)|Gibt an, ob der aktuelle VectorIterator größer oder gleich einem angegebenen VectorIterator ist.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`VectorIterator`

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** collection.h

**Namespace:** Platform::Collections

## <a name="vectoriteratoroperator-gt-operator"></a><a name="operator-arrow"></a>Vectoriterator:: Operator- &gt; Operator

Ruft die Adresse des Elements ab, auf das vom aktuellen VectorIterator verwiesen wird.

### <a name="syntax"></a>Syntax

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>Rückgabewert

Der Wert des Elements, auf das vom aktuellen VectorIterator verwiesen wird.

Der Typ des Rückgabewerts ist ein nicht angegebener interner Typ, der für die Implementierung dieses Operators erforderlich ist.

## <a name="vectoriteratoroperator---operator"></a><a name="operator-decrement"></a>Vectoriterator:: Operator--Operator

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

Die zweite Syntax postdekrementiert den aktuellen VectorIterator. Der- **`int`** Typ in der zweiten Syntax gibt eine postdekrement-Operation an, nicht einen tatsächlichen ganzzahligen Operanden.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-dereference"></a>Vectoriterator:: Operator- \* Operator

Ruft die Adresse des Elements ab, das vom aktuellen VectorIterator angegeben wird.

### <a name="syntax"></a>Syntax

```
reference operator*() const;
```

### <a name="return-value"></a>Rückgabewert

Das vom aktuellen VectorIterator angegebene Element.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-equality"></a>Vectoriterator:: Operator = =-Operator

Gibt an, ob der aktuelle VectorIterator gleich einem angegebenen VectorIterator ist.

### <a name="syntax"></a>Syntax

```
bool operator==(const VectorIterator& other) const;
```

### <a name="parameters"></a>Parameter

*außer*<br/>
Ein weiterer VectorIterator.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der aktuelle vectoriterator gleich einem *anderen*ist. andernfalls **`false`** .

## <a name="vectoriteratoroperatorgt-operator"></a><a name="operator-greater-than"></a>Vectoriterator:: Operator- &gt; Operator

Gibt an, ob der aktuelle VectorIterator größer als ein angegebener VectorIterator ist.

### <a name="syntax"></a>Syntax

```cpp
bool operator>(const VectorIterator& other) const
```

### <a name="parameters"></a>Parameter

*außer*<br/>
Ein weiterer VectorIterator.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der aktuelle vectoriterator größer als ein *anderer*ist. andernfalls **`false`** .

## <a name="vectoriteratoroperatorgt-operator"></a><a name="operator-greater-than-or-equals"></a>Vectoriterator:: Operator &gt; =-Operator

Gibt an, ob der aktuelle VectorIterator größer oder gleich dem angegebenen VectorIterator ist.

### <a name="syntax"></a>Syntax

```cpp
bool operator>=(const VectorIterator& other) const
```

### <a name="parameters"></a>Parameter

*außer*<br/>
Ein weiterer VectorIterator.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der aktuelle vectoriterator größer oder gleich einem *anderen*ist. andernfalls **`false`** .

## <a name="vectoriteratoroperator-operator"></a><a name="operator-increment"></a>Vectoriterator:: Operator + +-Operator

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

Die zweite Syntax postinkrementiert den aktuellen VectorIterator. Der **`int`** Typ in der zweiten Syntax gibt einen Vorgang nach dem Inkrement an, nicht einen tatsächlichen ganzzahligen Operanden.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-inequality"></a>Vectoriterator:: Operator! =-Operator

Gibt an, ob der aktuelle VectorIterator ungleich einem angegebenen VectorIterator ist.

### <a name="syntax"></a>Syntax

```
bool operator!=(const VectorIterator& other) const;
```

### <a name="parameters"></a>Parameter

*außer*<br/>
Ein weiterer VectorIterator.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der aktuelle vectoriterator nicht gleich dem *anderen*ist. andernfalls **`false`** .

## <a name="vectoriteratoroperatorlt-operator"></a><a name="operator-less-than"></a>Vectoriterator:: Operator- &lt; Operator

Gibt an, ob der aktuelle VectorIterator kleiner einem angegebenen VectorIterator ist.

### <a name="syntax"></a>Syntax

```cpp
bool operator<(const VectorIterator& other) const
```

### <a name="parameters"></a>Parameter

*außer*<br/>
Ein weiterer VectorIterator.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der aktuelle vectoriterator kleiner als der *andere*ist. andernfalls **`false`** .

## <a name="vectoriteratoroperatorlt-operator"></a><a name="operator-less-than-or-equals"></a>Vectoriterator:: Operator &lt; =-Operator

Gibt an, ob der aktuelle VectorIterator kleiner oder gleich einem angegebenen VectorIterator ist.

### <a name="syntax"></a>Syntax

```cpp
bool operator<=(const VectorIterator& other) const
```

### <a name="parameters"></a>Parameter

*außer*<br/>
Ein weiterer VectorIterator.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der aktuelle vectoriterator kleiner oder gleich einem *anderen*ist. andernfalls **`false`** .

## <a name="vectoriteratoroperator--operator"></a><a name="operator-minus"></a>Vectoriterator:: Operator-Operator

Subtrahiert entweder eine angegebene Anzahl von Elementen vom aktuellen Iterator und bildet einen neuen Iterator, oder subtrahiert einen angegebenen Iterator vom aktuellen Iterator, und gibt die Anzahl von Elementen zwischen den Iteratoren zurück.

### <a name="syntax"></a>Syntax

```

VectorIterator operator-(difference_type n) const;

difference_type operator-(const VectorIterator& other) const;
```

### <a name="parameters"></a>Parameter

*n*<br/>
Eine Anzahl von Elementen.

*außer*<br/>
Ein weiterer VectorIterator.

### <a name="return-value"></a>Rückgabewert

Die erste Operatorsyntax gibt ein VectorIterator-Objekt zurück, das `n` Elemente kleiner ist, als der aktuelle VectorIterator. Die zweite Operatorsyntax gibt die Anzahl von Elementen zwischen dem aktuellen und dem `other` VectorIterator zurück.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-plus-assign"></a>Vectoriterator:: Operator + =-Operator

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

## <a name="vectoriteratoroperator-operator"></a><a name="operator-plus"></a>Vectoriterator:: Operator +-Operator

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

*i*<br/>
In der zweiten Syntax ein VectorIterator.

### <a name="return-value"></a>Rückgabewert

In der ersten Syntax ein VectorIterator, der auf das Element an der angegebenen Verschiebung vom aktuellen VectorIterator verweist.

In der zweiten Syntax ein VectorIterator, der auf das Element an der angegebenen Verschiebung vom Anfang des Parameters `i` verweist.

### <a name="remarks"></a>Bemerkungen

Das erste Syntaxbeispiel

## <a name="vectoriteratoroperator--operator"></a><a name="operator-minus-equals"></a>Vectoriterator:: Operator-=-Operator

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

## <a name="vectoriteratoroperator"></a><a name="operator-at"></a>Vectoriterator::-Operator\[\]

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

## <a name="vectoriteratorvectoriterator-constructor"></a><a name="ctor"></a>Vectoriterator:: vectoriterator-Konstruktor

Initialisiert eine neue Instanz der VectorIterator-Klasse.

### <a name="syntax"></a>Syntax

```
VectorIterator();

explicit VectorIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

### <a name="parameters"></a>Parameter

*Ramelow*<br/>
Ein IVector- \<T> Objekt.

### <a name="remarks"></a>Bemerkungen

Das erste Syntaxbeispiel ist der Standardkonstruktor. Das zweite Syntax Beispiel ist ein expliziter Konstruktor, der zum Erstellen eines vectoriterator aus einem IVector-Objekt verwendet wird \<T> .

## <a name="see-also"></a>Weitere Informationen

[Platform-Namespace](platform-namespace-c-cx.md)
