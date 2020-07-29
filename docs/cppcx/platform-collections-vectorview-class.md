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
ms.openlocfilehash: 207f5d517eaae475af1c65a284a3d1ebe50621af
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218389"
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

*Fresser*<br/>
Gibt ein binäres Prädikat zum Testen der Übereinstimmung mit Werten des Typs `T`an. Der Standardwert ist `std::equal_to<T>`.

### <a name="remarks"></a>Hinweise

Die `VectorView` -Klasse implementiert die [Windows:: Foundation:: Collections:: \<T> ivectorview](/uwp/api/windows.foundation.collections.ivectorview-1) -Schnittstelle und unterstützt die Standard Vorlagen Bibliothek-Iteratoren.

### <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Vector View:: Vector View](#ctor)|Initialisiert eine neue Instanz der VectorView-Klasse.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[Vector View:: First](#first)|Gibt einen Iterator zurück, der das erste Element in der VectorView angibt.|
|[Vector View:: GetAt](#getat)|Ruft das Element der aktuellen VectorView ab, das durch den angegebenen Index bezeichnet wird.|
|[Vector View:: getmany](#getmany)|Ruft eine Sequenz von Elementen von der aktuellen VectorView ab, die am angegebenen Index beginnt.|
|[Vector View:: IndexOf](#indexof)|Sucht das angegebene Element in der aktuellen VectorView und gibt, wenn es gefunden wurde, den Index des Elements zurück.|
|[VectorView::Size](#size)|Gibt die Anzahl von Elementen im aktuellen VectorView-Objekt zurück.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`VectorView`

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** collection.h

**Namespace:** Platform::Collections

## <a name="vectorviewfirst-method"></a><a name="first"></a>Vectorview:: First-Methode

Gibt einen Iterator zurück, der das erste Element in der VectorView angibt.

### <a name="syntax"></a>Syntax

```

virtual Windows::Foundation::Collections::IIterator<T>^
   First();
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der das erste Element in der VectorView angibt.

### <a name="remarks"></a>Bemerkungen

Eine bequeme Möglichkeit, den von First () zurückgegebenen Iterator zu halten, besteht darin, den Rückgabewert einer Variablen zuzuweisen, die mit dem **`auto`** typableitungs Schlüsselwort deklariert wird. Beispiel: `auto x = myVectorView->First();`.

## <a name="vectorviewgetat-method"></a><a name="getat"></a>Vectorview:: GetAt-Methode

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

Das Element, das durch den `index`-Parameter spezifiziert wird. Der Elementtyp wird durch den vectorview-Vorlagen Parameter *T*angegeben.

## <a name="vectorviewgetmany-method"></a><a name="getmany"></a>Vectorview:: getmany-Methode

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

## <a name="vectorviewindexof-method"></a><a name="indexof"></a>Vectorview:: IndexOf-Methode

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

Der *Index* -Parameter ist 0, wenn das Element entweder das erste Element des ist `VectorView` oder das Element nicht gefunden wurde. Wenn der Rückgabewert ist **`true`** , wurde das Element gefunden, und es ist das erste Element; andernfalls wurde das Element nicht gefunden.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das angegebene Element gefunden wurde. andernfalls **`false`** .

## <a name="vectorviewsize-method"></a><a name="size"></a>Vectorview:: size-Methode

Gibt die Anzahl von Elementen im aktuellen VectorView-Objekt zurück.

### <a name="syntax"></a>Syntax

```

virtual property unsigned int Size;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente in der aktuellen VectorView.

## <a name="vectorviewvectorview-constructor"></a><a name="ctor"></a>Vectorview:: vectorview-Konstruktor

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

*InIt*<br/>
Der Typ einer Auflistung von Objekten, die verwendet wird, um die aktuelle VectorView zu initialisieren.

*Il*<br/>
Ein [Std:: initializer_list](../standard-library/initializer-list-class.md) , dessen Elemente verwendet werden, um die Vector View zu initialisieren.

*N*<br/>
Die Anzahl von Elementen in einer Auflistung von Objekten, die verwendet wird, um die aktuelle VectorView zu initialisieren.

*size*<br/>
Die Anzahl von Elementen in der VectorView.

*value*<br/>
Ein Wert, der verwendet wird, um die einzelnen Elemente in der aktuellen VectorView zu initialisieren.

*Ramelow*<br/>
Ein [Lvalues und Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) für einen [Std:: Vector](../standard-library/vector-class.md) , der verwendet wird, um die aktuelle Vector View zu initialisieren.

*ptr*<br/>
Zeiger zu `std::vector`, der verwendet wird, um die aktuelle VectorView zu initialisieren.

*r*<br/>
Ein [Platform:: Array](../cppcx/platform-array-class.md) -Objekt, das verwendet wird, um die aktuelle vectorview zu initialisieren.

*ein*<br/>
Ein [Std:: Array](../standard-library/array-class-stl.md) -Objekt, das verwendet wird, um die aktuelle vectorview zu initialisieren.

*first*<br/>
Das erste Element in einer Sequenz von Objekten, die verwendet werden, um die aktuelle VectorView zu initialisieren. Der Typ von `first` wird durch eine *perfekte Weiterleitung*übermittelt. Weitere Informationen finden Sie unter [RValue-Verweisdeklarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

*last*<br/>
Das letzte Element in einer Sequenz von Objekten, die verwendet werden, um die aktuelle VectorView zu initialisieren. Der Typ von `last` wird durch eine *perfekte Weiterleitung*übermittelt. Weitere Informationen finden Sie unter [RValue-Verweisdeklarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Weitere Informationen

[Platform-Namespace](platform-namespace-c-cx.md)<br/>
[Erstellen von Windows-Runtime-Komponenten in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
