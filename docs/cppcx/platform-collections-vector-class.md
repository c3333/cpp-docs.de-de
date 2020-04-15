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
ms.openlocfilehash: b2d08461b4ab57ed8479549c18c35c872d0eb9f1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354376"
---
# <a name="platformcollectionsvector-class"></a>Platform::Collections::Vector-Klasse

Stellt eine sequenzielle Auflistung von Objekten dar, auf die einzeln über einen Index zugegriffen werden kann. Implementiert [Windows::Foundation::Collections::IObservableVector](/uwp/api/Windows.Foundation.Collections.IObservableVector_T_) zur Hilfe bei der XAML-Datenbindung . [data binding](/windows/uwp/data-binding/data-binding-in-depth)

## <a name="syntax"></a>Syntax

```
template <typename T, typename E>
   ref class Vector sealed;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ der im Vektorobjekt enthaltenen Elemente.

*E*<br/>
Gibt ein binäres Prädikat zum Testen der Gleichheit mit Werten vom Typ *T*an. Der Standardwert `std::equal_to<T>`ist .

### <a name="remarks"></a>Bemerkungen

Folgende Typen sind zulässig:

1. Ganze Zahlen

1. Schnittstellenklasse

1. Öffentliche Referenzklasse^

1. value struct

1. Öffentliche Enumerationsklasse

Die **Vector-Klasse** ist die c++-Betonimplementierung der [Windows::Foundation::Collections::IVector-Schnittstelle.](/uwp/api/Windows.Foundation.Collections.IVector_T_)

Wenn Sie versuchen, einen **Vector-Typ** in einem öffentlichen Rückgabewert oder Parameter zu verwenden, wird der Compilerfehler C3986 ausgelöst. Sie können den Fehler beheben, indem Sie den Typ des Parameters oder des Rückgabewerts in [Windows::Foundation::Collections::IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_)ändern. Weitere Informationen finden Sie unter [Auflistungen (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Vektor::Vektor](#ctor)|Initialisiert eine neue Instanz der Vector-Klasse.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Vector::Append](#append)|Fügt das angegebene Element nach dem letzten Element im aktuellen Vektor ein.|
|[Vektor::Klar](#clear)|Löscht alle Elemente im aktuellen Vector.|
|[Vektor::Erste](#first)|Gibt einen Iterator zurück, der das erste Element im Vektor angibt.|
|[Vektor::GetAt](#getat)|Ruft das Element des aktuellen Vector ab, das durch den angegebenen Index bezeichnet wird.|
|[Vektor::GetMany](#getmany)|Ruft eine Sequenz von Elementen vom aktuellen Vektor ab, die am angegebenen Index beginnt.|
|[Vektor::GetView](#getview)|Gibt eine schreibgeschützte Ansicht eines Vektors zurück; also [Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md).|
|[Vektor::IndexOf](#indexof)|Sucht das angegebene Element im aktuellen Vector und gibt, wenn es gefunden wurde, den Index des Elements zurück.|
|[Vector::InsertAt](#insertat)|Fügt das angegebene Element in den aktuellen Vektor an dem Element ein, das durch den angegebenen Index identifiziert wird.|
|[Vector::ReplaceAll](#replaceall)|Löscht die Elemente im aktuellen Vektor und fügt dann die Elemente aus dem angegebenen Array ein.|
|[Vector::RemoveAt](#removeat)|Löscht das Element, das durch den angegebenen Index von dem aktuellen Vektor identifiziert wird.|
|[Vector::RemoveAtEnd](#removeatend)|Löscht das Element am Ende des aktuellen Vektors.|
|[Vector::SetAt](#setat)|Weist den angegebenen Wert dem Element im aktuellen Vektor zu, der vom angegebenen Index identifiziert wird.|
|[Vektor::Größe](#size)|Gibt die Anzahl von Elementen im aktuellen Vector-Objekt zurück.|

### <a name="events"></a>Ereignisse

|||
|-|-|
|Name|BESCHREIBUNG|
|Ereignis [Windows::Foundation::Collection::VectorChangedEventHandler\<T>](/uwp/api/windows.foundation.collections.vectorchangedeventhandler)|Tritt auf, wenn sich der Vektor ändert.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`Vector`

### <a name="requirements"></a>Anforderungen

**Header:** collection.h

**Namespace:** Platform::Collections

## <a name="vectorappend-method"></a><a name="append"></a>Vektor::Anfügen-Methode

Fügt das angegebene Element nach dem letzten Element im aktuellen Vektor ein.

### <a name="syntax"></a>Syntax

```cpp
virtual void Append(T item);
```

### <a name="parameters"></a>Parameter

*Index*<br/>
Das Element, das in den Vektor eingefügt werden soll. Der Elementtyp *wird* durch den *T-Typnamen* definiert.

## <a name="vectorclear-method"></a><a name="clear"></a>Vektor::Clear-Methode

Löscht alle Elemente im aktuellen Vector.

### <a name="syntax"></a>Syntax

```cpp
virtual void Clear();
```

## <a name="vectorfirst-method"></a><a name="first"></a>Vektor::Erste Methode

Gibt einen Iterator zurück, der auf das erste Element im Vektor verweist.

### <a name="syntax"></a>Syntax

```cpp
virtual Windows::Foundation::Collections::IIterator <T>^ First();
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der auf das erste Element im Vektor verweist.

### <a name="remarks"></a>Bemerkungen

Eine bequeme Möglichkeit, den von First() zurückgegebenen Iterator zu halten, besteht darin, den Rückgabewert einer Variablen zuzuweisen, die mit dem Schlüsselwort **"Auto** type deduction" deklariert wird. Beispiel: `auto x = myVector->First();`. Dieser Iterator kennt die Länge der Auflistung.

Wenn Sie ein Iteratorenpaar benötigen, um an eine STL-Funktion zu übergeben, verwenden Sie die freien Funktionen [Windows::Foundation::Collections::begin](../cppcx/begin-function.md) und [Windows::Foundation::Collections::end](../cppcx/end-function.md)

## <a name="vectorgetat-method"></a><a name="getat"></a>Vektor::GetAt-Methode

Ruft das Element des aktuellen Vector ab, das durch den angegebenen Index bezeichnet wird.

### <a name="syntax"></a>Syntax

```cpp
virtual T GetAt(unsigned int index);
```

### <a name="parameters"></a>Parameter

*Index*<br/>
Eine nullbasierte, ganze Zahl ohne Vorzeichen, die ein bestimmtes Element im Vector-Objekt spezifiziert.

### <a name="return-value"></a>Rückgabewert

Das durch den *Indexparameter* angegebene Element. Der Elementtyp wird durch den *TypName T* definiert.

## <a name="vectorgetmany-method"></a><a name="getmany"></a>Vektor::GetMany-Methode

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
Ein vom Aufrufer zugewiesenes Array von Elementen, die an dem von *startIndex* angegebenen Element beginnen und am letzten Element im Vektor enden.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der abgerufenen Elemente.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist nicht für die direkte Verwendung durch Clientcode vorgesehen. Es wird intern in der [to_vector-Funktion](../cppcx/to-vector-function.md) verwendet, um eine effiziente Konvertierung von Platform::Vector-Intances in std::vector-Instanzen zu ermöglichen.

## <a name="vectorgetview-method"></a><a name="getview"></a>Vektor::GetView-Methode

Gibt eine schreibgeschützte Ansicht eines Vektors zurück, das heißt, eine IVectorView.

### <a name="syntax"></a>Syntax

```cpp
Windows::Foundation::Collections::IVectorView<T>^ GetView();
```

### <a name="return-value"></a>Rückgabewert

Ein IVectorView-Objekt.

## <a name="vectorindexof-method"></a><a name="indexof"></a>Vektor::IndexOf-Methode

Sucht das angegebene Element im aktuellen Vector und gibt, wenn es gefunden wurde, den Index des Elements zurück.

### <a name="syntax"></a>Syntax

```cpp
virtual bool IndexOf(T value, unsigned int* index);
```

### <a name="parameters"></a>Parameter

*value*<br/>
Das Element, das gesucht werden soll.

*Index*<br/>
Der nullbasierte Index des Elements, wenn der *Parameterwert* gefunden wird; andernfalls 0.

Der *Indexparameter* ist 0, wenn das Element entweder das erste Element des Vektors ist oder das Element nicht gefunden wurde. Wenn der Rückgabewert **true**ist, wurde das Element gefunden, und es ist das erste Element. Andernfalls wurde das Element nicht gefunden.

### <a name="return-value"></a>Rückgabewert

**true,** wenn das angegebene Element gefunden wird; andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

IndexOf verwendet std::find_if, um das Element zu suchen. Benutzerdefinierte Elementtypen sollten deshalb den Operator == und != überladen, um die Übereinstimmungsvergleiche zu ermöglichen, die für "find_if" erforderlich sind.

## <a name="vectorinsertat-method"></a><a name="insertat"></a>Vektor::InsertAt-Methode

Fügt das angegebene Element in den aktuellen Vektor an dem Element ein, das durch den angegebenen Index identifiziert wird.

### <a name="syntax"></a>Syntax

```cpp
virtual void InsertAt(unsigned int index, T item)
```

### <a name="parameters"></a>Parameter

*Index*<br/>
Eine nullbasierte, ganze Zahl ohne Vorzeichen, die ein bestimmtes Element im Vector-Objekt spezifiziert.

*item*<br/>
Ein Element, das in den Vektor an dem durch *Index*angegebenen Element eingefügt werden soll. Der Elementtyp *wird* durch den *T-Typnamen* definiert.

## <a name="vectorremoveat-method"></a><a name="removeat"></a>Vektor::RemoveAt-Methode

Löscht das Element, das durch den angegebenen Index von dem aktuellen Vektor identifiziert wird.

### <a name="syntax"></a>Syntax

```cpp
virtual void RemoveAt(unsigned int index);
```

### <a name="parameters"></a>Parameter

*Index*<br/>
Eine nullbasierte, ganze Zahl ohne Vorzeichen, die ein bestimmtes Element im Vector-Objekt spezifiziert.

## <a name="vectorremoveatend-method"></a><a name="removeatend"></a>Vektor::RemoveAtEnd-Methode

Löscht das Element am Ende des aktuellen Vektors.

### <a name="syntax"></a>Syntax

```cpp
virtual void RemoveAtEnd();
```

## <a name="vectorreplaceall-method"></a><a name="replaceall"></a>Vektor::Alle-Methode ersetzen

Löscht die Elemente im aktuellen Vektor und fügt dann die Elemente aus dem angegebenen Array ein.

### <a name="syntax"></a>Syntax

```cpp
virtual void ReplaceAll(const ::Platform::Array<T>^ arr);
```

### <a name="parameters"></a>Parameter

*Arr*<br/>
Ein Array von Objekten, deren Typ durch den *T-Typnamen* definiert ist.

## <a name="vectorsetat-method"></a><a name="setat"></a>Vektor::SetAt-Methode

Weist den angegebenen Wert dem Element im aktuellen Vektor zu, der vom angegebenen Index identifiziert wird.

### <a name="syntax"></a>Syntax

```cpp
virtual void SetAt(unsigned int index, T item);
```

### <a name="parameters"></a>Parameter

*Index*<br/>
Eine nullbasierte, ganze Zahl ohne Vorzeichen, die ein bestimmtes Element im Vector-Objekt spezifiziert.

*item*<br/>
Der dem angegebenen Element zuzuweisende Wert. Der Elementtyp *wird* durch den *T-Typnamen* definiert.

## <a name="vectorsize-method"></a><a name="size"></a>Vektor::Size-Methode

Gibt die Anzahl von Elementen im aktuellen Vector-Objekt zurück.

### <a name="syntax"></a>Syntax

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente im aktuellen Vector.

## <a name="vectorvector-constructor"></a><a name="ctor"></a>Vektor::Vektorkonstruktor

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

*Eine*<br/>
Ein [std::array,](../standard-library/array-class-stl.md) das zum Initialisieren des Vektors verwendet wird.

*Arr*<br/>
Eine [Plattform::Array,](../cppcx/platform-array-class.md) die zum Initialisieren des Vektors verwendet wird.

*Init*<br/>
Der Typ einer Auflistung von Objekten, die verwendet werden, um den aktuelle Vector zu initialisieren.

*Il*<br/>
Eine [std::initializer_list](../standard-library/initializer-list-class.md) von Objekten des Typs *T,* die zum Initialisieren des Vektors verwendet werden.

*N*<br/>
Die Anzahl von Elementen in einer Auflistung von Objekten, die verwendet wird, um den aktuellen Vector zu initialisieren.

*Größe*<br/>
Die Anzahl von Elementen im Vector.

*value*<br/>
Ein Wert, der verwendet wird, um die einzelnen Elemente im aktuellen Vector zu initialisieren.

*V*<br/>
Ein [Lvalues und Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) zu einem [std::vector,](../standard-library/vector-class.md) der zum Initialisieren des aktuellen Vektors verwendet wird.

*Ptr*<br/>
Zeiger zu `std::vector`, der verwendet wird, um den aktuellen Vector zu initialisieren.

*first*<br/>
Das erste Element in einer Sequenz von Objekten, die verwendet werden, um den aktuellen Vector zu initialisieren. Die Art der *ersten* wird durch *perfekte Weiterleitung*übergeben. Weitere Informationen finden Sie unter [RValue-Verweisdeklarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

*last*<br/>
Das letzte Element in einer Sequenz von Objekten, die verwendet werden, um den aktuellen Vector zu initialisieren. Die Art der *letzten* wird durch *perfekte Weiterleitung*übergeben. Weitere Informationen finden Sie unter [RValue-Verweisdeklarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Siehe auch

[Sammlungen (C++/CX)](collections-c-cx.md)<br/>
[Plattform-Namespace](platform-namespace-c-cx.md)<br/>
[Erstellen von Windows-Runtime-Komponenten in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
