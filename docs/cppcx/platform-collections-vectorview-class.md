---
title: Platform::Collections::VectorView-Klasse
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorView::VectorView
- COLLECTION/Platform::Collections::VectorView::First
- COLLECTION/Platform::Collections::VectorView::GetAt
- COLLECTION/Platform::Collections::VectorView::GetMany
- COLLECTION/Platform::Collections::VectorView::IndexOf
- COLLECTION/Platform::Collections::VectorView::Size
helpviewer_keywords:
- VectorView Class
ms.assetid: 05cd461d-dce7-49d3-b0e7-2e5c78ed8192
ms.openlocfilehash: cecbd61ad8862d5046cab9e0b418d5c4d16829d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363802"
---
# <a name="platformcollectionsvectorview-class"></a>Platform::Collections::VectorView-Klasse

Stellt eine schreibgeschützte Ansicht einer sequenziellen Auflistung von Objekten dar, auf die einzeln nach Index zugegriffen werden kann. Der Typ der einzelnen Objekte in der Auflistung wird durch den Vorlagenparameter spezifiziert.

## <a name="syntax"></a>Syntax

```
template <typename T, typename E>
   ref class VectorView sealed;
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ der im `VectorView` -Objekt enthaltenen Elemente.

*E*<br/>
Gibt ein binäres Prädikat zum Testen der Übereinstimmung mit Werten des Typs `T`an. Der Standardwert ist `std::equal_to<T>`.

### <a name="remarks"></a>Bemerkungen

Die `VectorView` Klasse implementiert die [Windows::Foundation::Collections::IVectorView\<T>-Schnittstelle](/uwp/api/Windows.Foundation.Collections.IVectorView_T_) und unterstützt Standardvorlagenbibliotheksiteratoren.

### <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[VectorView::VectorView](#ctor)|Initialisiert eine neue Instanz der VectorView-Klasse.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[VectorView::Erste](#first)|Gibt einen Iterator zurück, der das erste Element in der VectorView angibt.|
|[VectorView::GetAt](#getat)|Ruft das Element der aktuellen VectorView ab, das durch den angegebenen Index bezeichnet wird.|
|[VectorView::GetMany](#getmany)|Ruft eine Sequenz von Elementen von der aktuellen VectorView ab, die am angegebenen Index beginnt.|
|[VectorView::IndexOf](#indexof)|Sucht das angegebene Element in der aktuellen VectorView und gibt, wenn es gefunden wurde, den Index des Elements zurück.|
|[VectorView::Size](#size)|Gibt die Anzahl von Elementen im aktuellen VectorView-Objekt zurück.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`VectorView`

### <a name="requirements"></a>Anforderungen

**Header:** collection.h

**Namespace:** Platform::Collections

## <a name="vectorviewfirst-method"></a><a name="first"></a>VectorView::Erste Methode

Gibt einen Iterator zurück, der das erste Element in der VectorView angibt.

### <a name="syntax"></a>Syntax

```

virtual Windows::Foundation::Collections::IIterator<T>^
   First();
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der das erste Element in der VectorView angibt.

### <a name="remarks"></a>Bemerkungen

Eine bequeme Möglichkeit, den von First() zurückgegebenen Iterator zu halten, besteht darin, den Rückgabewert einer Variablen zuzuweisen, die mit dem Schlüsselwort **"Auto** type deduction" deklariert wird. Beispiel: `auto x = myVectorView->First();`.

## <a name="vectorviewgetat-method"></a><a name="getat"></a>VectorView::GetAt-Methode

Ruft das Element der aktuellen VectorView ab, das durch den angegebenen Index bezeichnet wird.

### <a name="syntax"></a>Syntax

```

T GetAt(
   UInt32 index
);
```

### <a name="parameters"></a>Parameter

*Index*<br/>
Eine nullbasierte ganze Zahl, die ein bestimmtes Element im VectorView-Objekt angibt.

### <a name="return-value"></a>Rückgabewert

Das Element, das durch den `index`-Parameter spezifiziert wird. Der Elementtyp wird durch den VectorView-Vorlagenparameter *T*angegeben.

## <a name="vectorviewgetmany-method"></a><a name="getmany"></a>VectorView::GetMany-Methode

Ruft eine Sequenz von Elementen von der aktuellen VectorView ab, die am angegebenen Index beginnt.

### <a name="syntax"></a>Syntax

```

virtual unsigned int GetMany(
   unsigned int startIndex,
   ::Platform::WriteOnlyArray<T>^ dest
);
```

### <a name="parameters"></a>Parameter

*startIndex*<br/>
Der nullbasierte Index des Anfangs der Elemente, die abgerufen werden sollen.

*dest*<br/>
Wenn die Operation abgeschlossen wird, ein Array von Elementen, die bei dem Element beginnen, das durch `startIndex` angegeben ist, und beim letzten Element im Vektor enden.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der abgerufenen Elemente.

## <a name="vectorviewindexof-method"></a><a name="indexof"></a>VectorView::IndexOf-Methode

Sucht das angegebene Element in der aktuellen VectorView und gibt, wenn es gefunden wurde, den Index des Elements zurück.

### <a name="syntax"></a>Syntax

```

virtual bool IndexOf(
   T value,
   unsigned int* index
);
```

### <a name="parameters"></a>Parameter

*value*<br/>
Das Element, das gesucht werden soll.

*Index*<br/>
Der nullbasierte Index des Elements, wenn der Parameter `value` gefunden wurde, andernfalls 0.

Der *Indexparameter* ist 0, wenn das Element `VectorView` entweder das erste Element des Elements ist oder das Element nicht gefunden wurde. Wenn der Rückgabewert **true**ist, wurde das Element gefunden, und es ist das erste Element. Andernfalls wurde das Element nicht gefunden.

### <a name="return-value"></a>Rückgabewert

**true,** wenn das angegebene Element gefunden wird; andernfalls **false**.

## <a name="vectorviewsize-method"></a><a name="size"></a>VectorView::Size-Methode

Gibt die Anzahl von Elementen im aktuellen VectorView-Objekt zurück.

### <a name="syntax"></a>Syntax

```

virtual property unsigned int Size;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente in der aktuellen VectorView.

## <a name="vectorviewvectorview-constructor"></a><a name="ctor"></a>VectorView::VectorView-Konstruktor

Initialisiert eine neue Instanz der VectorView-Klasse.

### <a name="syntax"></a>Syntax

```
VectorView();
explicit VectorView(
   UInt32 size
);
VectorView(
   UInt32 size,
   T value
);
explicit VectorView(
   const ::std::vector<T>& v
);
explicit VectorView(
   ::std::vector<T>&& v
);
VectorView(
   const T * ptr,
   UInt32 size
);

template <
   size_t N
>
explicit VectorView(
   const T (&arr)[N]
);

template <
   size_t N
>
explicit VectorView(
   const ::std::array<T,
   N>& a
);

explicit VectorView(
   const ::Platform::Array<T>^ arr
);

template <
   typename InIt
>
VectorView(
   InItfirst,
   InItlast
);

VectorView(
   std::initializer_list<T> il
);
```

### <a name="parameters"></a>Parameter

*Init*<br/>
Der Typ einer Auflistung von Objekten, die verwendet wird, um die aktuelle VectorView zu initialisieren.

*Il*<br/>
Ein [std::initializer_list](../standard-library/initializer-list-class.md) dessen Elemente zum Initialisieren der VectorView verwendet werden.

*N*<br/>
Die Anzahl von Elementen in einer Auflistung von Objekten, die verwendet wird, um die aktuelle VectorView zu initialisieren.

*Größe*<br/>
Die Anzahl von Elementen in der VectorView.

*value*<br/>
Ein Wert, der verwendet wird, um die einzelnen Elemente in der aktuellen VectorView zu initialisieren.

*V*<br/>
Ein [Lvalues und Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) zu einem [std::vector,](../standard-library/vector-class.md) der zum Initialisieren der aktuellen VectorView verwendet wird.

*Ptr*<br/>
Zeiger zu `std::vector`, der verwendet wird, um die aktuelle VectorView zu initialisieren.

*Arr*<br/>
Ein [Platform::Array-Objekt,](../cppcx/platform-array-class.md) das zum Initialisieren der aktuellen VectorView verwendet wird.

*Eine*<br/>
Ein [std::array-Objekt,](../standard-library/array-class-stl.md) das zum Initialisieren der aktuellen VectorView verwendet wird.

*first*<br/>
Das erste Element in einer Sequenz von Objekten, die verwendet werden, um die aktuelle VectorView zu initialisieren. Die Art `first` der wird durch *perfekte Weiterleitung*übergeben. Weitere Informationen finden Sie unter [RValue-Verweisdeklarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

*last*<br/>
Das letzte Element in einer Sequenz von Objekten, die verwendet werden, um die aktuelle VectorView zu initialisieren. Die Art `last` der wird durch *perfekte Weiterleitung*übergeben. Weitere Informationen finden Sie unter [RValue-Verweisdeklarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Siehe auch

[Plattform-Namespace](platform-namespace-c-cx.md)<br/>
[Erstellen von Windows-Runtime-Komponenten in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
