---
title: Platform::Collections::Vector-Klasse
ms.date: 12/04/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::Vector::Vector
- COLLECTION/Platform::Collections::Vector::Append
- COLLECTION/Platform::Collections::Vector::Clear
- COLLECTION/Platform::Collections::Vector::First
- COLLECTION/Platform::Collections::Vector::GetAt
- COLLECTION/Platform::Collections::Vector::GetMany
- COLLECTION/Platform::Collections::Vector::GetView
- COLLECTION/Platform::Collections::Vector::IndexOf
- COLLECTION/Platform::Collections::Vector::InsertAt
- COLLECTION/Platform::Collections::Vector::ReplaceAll
- COLLECTION/Platform::Collections::Vector::RemoveAt
- COLLECTION/Platform::Collections::Vector::RemoveAtEnd
- COLLECTION/Platform::Collections::Vector::SetAt
- COLLECTION/Platform::Collections::Vector::Size
- COLLECTION/Platform::Collections::Vector::VectorChanged
helpviewer_keywords:
- Vector Class (C++/Cx)
ms.assetid: aee8c076-9700-47c3-99b6-799fd3edb0ca
ms.openlocfilehash: 5a35efb3ca1590931ce1db5fd12d7c930b258286
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218402"
---
# <a name="platformcollectionsvector-class"></a>Platform::Collections::Vector-Klasse

Stellt eine sequenzielle Auflistung von Objekten dar, auf die einzeln über einen Index zugegriffen werden kann. Implementiert [Windows:: Foundation:: Collections:: iobservablevector](/uwp/api/windows.foundation.collections.iobservablevector-1) , um die XAML- [Datenbindung](/windows/uwp/data-binding/data-binding-in-depth)zu unterstützen.

## <a name="syntax"></a>Syntax

```
template <typename T, typename E>
   ref class Vector sealed;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ der im Vektorobjekt enthaltenen Elemente.

*Fresser*<br/>
Gibt ein binäres Prädikat zum Testen der Gleichheit mit Werten des Typs *T*an. Der Standardwert ist `std::equal_to<T>` .

### <a name="remarks"></a>Bemerkungen

Folgende Typen sind zulässig:

1. integers

1. Schnittstellen Klasse ^

1. Öffentliche Referenzklasse^

1. value struct

1. Öffentliche Enumerationsklasse

Die **Vektor** Klasse ist die konkrete C++ Implementierung der [Windows:: Foundation:: Collections:: IVector](/uwp/api/windows.foundation.collections.ivector-1) -Schnittstelle.

Wenn Sie versuchen, einen **Vector** -Typ in einem öffentlichen Rückgabewert oder Parameter zu verwenden, wird der Compilerfehler C3986 ausgelöst. Sie können den Fehler beheben, indem Sie den Typ des Parameters oder des Rückgabewerts in [Windows::Foundation::Collections::IVector](/uwp/api/windows.foundation.collections.ivector-1)ändern. Weitere Informationen finden Sie unter [Auflistungen (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Vector:: Vector](#ctor)|Initialisiert eine neue Instanz der Vector-Klasse.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[Vector::Append](#append)|Fügt das angegebene Element nach dem letzten Element im aktuellen Vektor ein.|
|[Vector:: Clear](#clear)|Löscht alle Elemente im aktuellen Vector.|
|[Vector:: First](#first)|Gibt einen Iterator zurück, der das erste Element im Vektor angibt.|
|[Vector:: GetAt](#getat)|Ruft das Element des aktuellen Vector ab, das durch den angegebenen Index bezeichnet wird.|
|[Vector:: getmany](#getmany)|Ruft eine Sequenz von Elementen vom aktuellen Vektor ab, die am angegebenen Index beginnt.|
|[Vector:: GetView](#getview)|Gibt eine schreibgeschützte Ansicht eines Vektors zurück; also [Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md).|
|[Vector:: IndexOf](#indexof)|Sucht das angegebene Element im aktuellen Vector und gibt, wenn es gefunden wurde, den Index des Elements zurück.|
|[Vector::InsertAt](#insertat)|Fügt das angegebene Element in den aktuellen Vektor an dem Element ein, das durch den angegebenen Index identifiziert wird.|
|[Vector::ReplaceAll](#replaceall)|Löscht die Elemente im aktuellen Vektor und fügt dann die Elemente aus dem angegebenen Array ein.|
|[Vector::RemoveAt](#removeat)|Löscht das Element, das durch den angegebenen Index von dem aktuellen Vektor identifiziert wird.|
|[Vector::RemoveAtEnd](#removeatend)|Löscht das Element am Ende des aktuellen Vektors.|
|[Vector::SetAt](#setat)|Weist den angegebenen Wert dem Element im aktuellen Vektor zu, der vom angegebenen Index identifiziert wird.|
|[Vector:: size](#size)|Gibt die Anzahl von Elementen im aktuellen Vector-Objekt zurück.|

### <a name="events"></a>Ereignisse

|||
|-|-|
|Name|BESCHREIBUNG|
|Event [Windows:: Foundation:: Collection:: Vector changedeventhandler \<T> ^ Vector Changed](/uwp/api/windows.foundation.collections.vectorchangedeventhandler-1)|Tritt auf, wenn sich der Vektor ändert.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`Vector`

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** collection.h

**Namespace:** Platform::Collections

## <a name="vectorappend-method"></a><a name="append"></a>Vector:: Append-Methode

Fügt das angegebene Element nach dem letzten Element im aktuellen Vektor ein.

### <a name="syntax"></a>Syntax

```cpp
virtual void Append(T item);
```

### <a name="parameters"></a>Parameter

*Index*<br/>
Das Element, das in den Vektor eingefügt werden soll. Der Typ des *Elements* wird durch den *T* -Typnamen definiert.

## <a name="vectorclear-method"></a><a name="clear"></a>Vector:: Clear-Methode

Löscht alle Elemente im aktuellen Vector.

### <a name="syntax"></a>Syntax

```cpp
virtual void Clear();
```

## <a name="vectorfirst-method"></a><a name="first"></a>Vector:: First-Methode

Gibt einen Iterator zurück, der auf das erste Element im Vektor verweist.

### <a name="syntax"></a>Syntax

```cpp
virtual Windows::Foundation::Collections::IIterator <T>^ First();
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der auf das erste Element im Vektor verweist.

### <a name="remarks"></a>Bemerkungen

Eine bequeme Möglichkeit, den von First () zurückgegebenen Iterator zu halten, besteht darin, den Rückgabewert einer Variablen zuzuweisen, die mit dem **`auto`** typableitungs Schlüsselwort deklariert wird. Beispiel: `auto x = myVector->First();`. Dieser Iterator kennt die Länge der Auflistung.

Wenn Sie ein Iteratorpaar benötigen, das an eine STL-Funktion übergeben werden soll, verwenden Sie die kostenlosen Funktionen [Windows:: Foundation:: Collections:: begin](../cppcx/begin-function.md) und [Windows:: Foundation:: Collections:: End](../cppcx/end-function.md) .

## <a name="vectorgetat-method"></a><a name="getat"></a>Vector:: GetAt-Methode

Ruft das Element des aktuellen Vector ab, das durch den angegebenen Index bezeichnet wird.

### <a name="syntax"></a>Syntax

```cpp
virtual T GetAt(unsigned int index);
```

### <a name="parameters"></a>Parameter

*Index*<br/>
Eine nullbasierte, ganze Zahl ohne Vorzeichen, die ein bestimmtes Element im Vector-Objekt spezifiziert.

### <a name="return-value"></a>Rückgabewert

Das Element, das durch den *Index* -Parameter angegeben wird. Der Elementtyp wird durch den *T* -Typnamen definiert.

## <a name="vectorgetmany-method"></a><a name="getmany"></a>Vector:: getmany-Methode

Ruft eine Sequenz von Elementen vom aktuellen Vektor ab, die am angegebenen Index beginnt, und kopiert sie in das vom Aufrufer reservierten Array.

### <a name="syntax"></a>Syntax

```cpp
virtual unsigned int GetMany(
    unsigned int startIndex,
    Platform::WriteOnlyArray<T>^ dest);
```

### <a name="parameters"></a>Parameter

*startIndex*<br/>
Der nullbasierte Index des Anfangs der Elemente, die abgerufen werden sollen.

*dest*<br/>
Ein vom Aufrufer zugewiesenes Array von Elementen, die bei dem durch *startIndex* angegebenen Element beginnen und am letzten Element im Vektor enden.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der abgerufenen Elemente.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist nicht für die direkte Verwendung durch Clientcode vorgesehen. Sie wird intern in der [to_vector-Funktion](../cppcx/to-vector-function.md) verwendet, um eine effiziente Konvertierung von Platform:: Vector-intanzen in Std:: Vector-Instanzen zu ermöglichen.

## <a name="vectorgetview-method"></a><a name="getview"></a>Vector:: GetView-Methode

Gibt eine schreibgeschützte Ansicht eines Vektors zurück, das heißt, eine IVectorView.

### <a name="syntax"></a>Syntax

```cpp
Windows::Foundation::Collections::IVectorView<T>^ GetView();
```

### <a name="return-value"></a>Rückgabewert

Ein IVectorView-Objekt.

## <a name="vectorindexof-method"></a><a name="indexof"></a>Vector:: IndexOf-Methode

Sucht das angegebene Element im aktuellen Vector und gibt, wenn es gefunden wurde, den Index des Elements zurück.

### <a name="syntax"></a>Syntax

```cpp
virtual bool IndexOf(T value, unsigned int* index);
```

### <a name="parameters"></a>Parameter

*value*<br/>
Das Element, das gesucht werden soll.

*Index*<br/>
Der null basierte Index des Elements, wenn der Parameter *Wert* gefunden wird. andernfalls 0.

Der *Index* -Parameter ist 0, wenn das Element entweder das erste Element des Vektors ist oder das Element nicht gefunden wurde. Wenn der Rückgabewert ist **`true`** , wurde das Element gefunden, und es ist das erste Element; andernfalls wurde das Element nicht gefunden.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das angegebene Element gefunden wurde. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

IndexOf verwendet std::find_if, um das Element zu suchen. Benutzerdefinierte Elementtypen sollten deshalb den Operator == und != überladen, um die Übereinstimmungsvergleiche zu ermöglichen, die für "find_if" erforderlich sind.

## <a name="vectorinsertat-method"></a><a name="insertat"></a>Vector:: InsertAt-Methode

Fügt das angegebene Element in den aktuellen Vektor an dem Element ein, das durch den angegebenen Index identifiziert wird.

### <a name="syntax"></a>Syntax

```cpp
virtual void InsertAt(unsigned int index, T item)
```

### <a name="parameters"></a>Parameter

*Index*<br/>
Eine nullbasierte, ganze Zahl ohne Vorzeichen, die ein bestimmtes Element im Vector-Objekt spezifiziert.

*item*<br/>
Ein Element, das in den Vektor an dem durch *Index*angegebenen Element eingefügt werden soll. Der Typ des *Elements* wird durch den *T* -Typnamen definiert.

## <a name="vectorremoveat-method"></a><a name="removeat"></a>Vector:: RemoveAt-Methode

Löscht das Element, das durch den angegebenen Index von dem aktuellen Vektor identifiziert wird.

### <a name="syntax"></a>Syntax

```cpp
virtual void RemoveAt(unsigned int index);
```

### <a name="parameters"></a>Parameter

*Index*<br/>
Eine nullbasierte, ganze Zahl ohne Vorzeichen, die ein bestimmtes Element im Vector-Objekt spezifiziert.

## <a name="vectorremoveatend-method"></a><a name="removeatend"></a>Vector:: removeatend-Methode

Löscht das Element am Ende des aktuellen Vektors.

### <a name="syntax"></a>Syntax

```cpp
virtual void RemoveAtEnd();
```

## <a name="vectorreplaceall-method"></a><a name="replaceall"></a>Vector:: ReplaceAll-Methode

Löscht die Elemente im aktuellen Vektor und fügt dann die Elemente aus dem angegebenen Array ein.

### <a name="syntax"></a>Syntax

```cpp
virtual void ReplaceAll(const ::Platform::Array<T>^ arr);
```

### <a name="parameters"></a>Parameter

*r*<br/>
Ein Array von-Objekten, deren Typ durch den *T* -Typnamen definiert wird.

## <a name="vectorsetat-method"></a><a name="setat"></a>Vector:: "-Methode

Weist den angegebenen Wert dem Element im aktuellen Vektor zu, der vom angegebenen Index identifiziert wird.

### <a name="syntax"></a>Syntax

```cpp
virtual void SetAt(unsigned int index, T item);
```

### <a name="parameters"></a>Parameter

*Index*<br/>
Eine nullbasierte, ganze Zahl ohne Vorzeichen, die ein bestimmtes Element im Vector-Objekt spezifiziert.

*item*<br/>
Der dem angegebenen Element zuzuweisende Wert. Der Typ des *Elements* wird durch den *T* -Typnamen definiert.

## <a name="vectorsize-method"></a><a name="size"></a>Vector:: size-Methode

Gibt die Anzahl von Elementen im aktuellen Vector-Objekt zurück.

### <a name="syntax"></a>Syntax

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente im aktuellen Vector.

## <a name="vectorvector-constructor"></a><a name="ctor"></a>Vector:: Vector-Konstruktor

Initialisiert eine neue Instanz der Vector-Klasse.

### <a name="syntax"></a>Syntax

```cpp
Vector();

explicit Vector(unsigned int size);
Vector( unsigned int size, T value);
template <typename U> explicit Vector( const ::std::vector<U>& v);
template <typename U> explicit Vector( std::vector<U>&& v);

Vector( const T * ptr, unsigned int size);
template <size_t N> explicit Vector(const T(&arr)[N]);
template <size_t N> explicit Vector(const std::array<T, N>& a);
explicit Vector(const Array<T>^ arr);

template <typename InIt> Vector(InIt first, InIt last);
Vector(std::initializer_list<T> il);
```

### <a name="parameters"></a>Parameter

*ein*<br/>
Ein [Std:: Array](../standard-library/array-class-stl.md) , das verwendet wird, um den Vektor zu initialisieren.

*r*<br/>
Ein [Platform:: Array](../cppcx/platform-array-class.md) , das verwendet wird, um den Vektor zu initialisieren.

*InIt*<br/>
Der Typ einer Auflistung von Objekten, die verwendet werden, um den aktuelle Vector zu initialisieren.

*Il*<br/>
Eine [Std:: initializer_list](../standard-library/initializer-list-class.md) von Objekten vom Typ *T* , die verwendet werden, um den Vektor zu initialisieren.

*N*<br/>
Die Anzahl von Elementen in einer Auflistung von Objekten, die verwendet wird, um den aktuellen Vector zu initialisieren.

*size*<br/>
Die Anzahl von Elementen im Vector.

*value*<br/>
Ein Wert, der verwendet wird, um die einzelnen Elemente im aktuellen Vector zu initialisieren.

*Ramelow*<br/>
Ein [Lvalues und Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) für einen [Std:: Vector](../standard-library/vector-class.md) , der verwendet wird, um den aktuellen Vektor zu initialisieren.

*ptr*<br/>
Zeiger zu `std::vector`, der verwendet wird, um den aktuellen Vector zu initialisieren.

*first*<br/>
Das erste Element in einer Sequenz von Objekten, die verwendet werden, um den aktuellen Vector zu initialisieren. Der Typ des *ersten* wird mithilfe der *perfekten Weiterleitung*übermittelt. Weitere Informationen finden Sie unter [RValue-Verweisdeklarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

*last*<br/>
Das letzte Element in einer Sequenz von Objekten, die verwendet werden, um den aktuellen Vector zu initialisieren. Der Typ des *letzten* wird über eine *perfekte Weiterleitung*übermittelt. Weitere Informationen finden Sie unter [RValue-Verweisdeklarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Weitere Informationen

[Auflistungen (C++/CX)](collections-c-cx.md)<br/>
[Platform-Namespace](platform-namespace-c-cx.md)<br/>
[Erstellen von Windows-Runtime-Komponenten in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
