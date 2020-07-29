---
title: unique_ptr-Klasse
ms.date: 11/04/2016
f1_keywords:
- memory/std::unique_ptr
- memory/std::unique_ptr::deleter_type
- memory/std::unique_ptr::element_type
- memory/std::unique_ptr::pointer
- memory/std::unique_ptr::get
- memory/std::unique_ptr::get_deleter
- memory/std::unique_ptr::release
- memory/std::unique_ptr::reset
- memory/std::unique_ptr::swap
helpviewer_keywords:
- std::unique_ptr [C++]
- std::unique_ptr [C++], deleter_type
- std::unique_ptr [C++], element_type
- std::unique_ptr [C++], pointer
- std::unique_ptr [C++], get
- std::unique_ptr [C++], get_deleter
- std::unique_ptr [C++], release
- std::unique_ptr [C++], reset
- std::unique_ptr [C++], swap
ms.assetid: acdf046b-831e-4a4a-83aa-6d4ee467db9a
ms.openlocfilehash: 694ea94ac0e9dcd31d89a3a83bd3400bac3e8e4f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222185"
---
# <a name="unique_ptr-class"></a>unique_ptr-Klasse

Es wird ein Zeiger auf ein im Besitz befindliches Objekt oder Array gespeichert. Das Objekt/Array ist nicht im Besitz eines anderen `unique_ptr`-Elements. Das Objekt/Array wird zerstört, wenn `unique_ptr` zerstört wird.

## <a name="syntax"></a>Syntax

```cpp
class unique_ptr {
public:
    unique_ptr();
    unique_ptr(nullptr_t Nptr);
    explicit unique_ptr(pointer Ptr);
    unique_ptr(pointer Ptr,
        typename conditional<is_reference<Del>::value, Del,
        typename add_reference<const Del>::type>::type Deleter);
    unique_ptr(pointer Ptr,
        typename remove_reference<Del>::type&& Deleter);
    unique_ptr(unique_ptr&& Right);
    template <class T2, Class Del2>
    unique_ptr(unique_ptr<T2, Del2>&& Right);
    unique_ptr(const unique_ptr& Right) = delete;
    unique_ptr& operator=(const unique_ptr& Right) = delete;
};

//Specialization for arrays:
template <class T, class D>
class unique_ptr<T[], D> {
public:
    typedef pointer;
    typedef T element_type;
    typedef D deleter_type;
    constexpr unique_ptr() noexcept;
    template <class U>
    explicit unique_ptr(U p) noexcept;
    template <class U>
    unique_ptr(U p, see below d) noexcept;
    template <class U>
    unique_ptr(U p, see below d) noexcept;
    unique_ptr(unique_ptr&& u) noexcept;
    constexpr unique_ptr(nullptr_t) noexcept : unique_ptr() { }     template <class U, class E>
        unique_ptr(unique_ptr<U, E>&& u) noexcept;
    ~unique_ptr();
    unique_ptr& operator=(unique_ptr&& u) noexcept;
    template <class U, class E>
    unique_ptr& operator=(unique_ptr<U, E>&& u) noexcept;
    unique_ptr& operator=(nullptr_t) noexcept;
    T& operator[](size_t i) const;

    pointer get() const noexcept;
    deleter_type& get_deleter() noexcept;
    const deleter_type& get_deleter() const noexcept;
    explicit operator bool() const noexcept;
    pointer release() noexcept;
    void reset(pointer p = pointer()) noexcept;
    void reset(nullptr_t = nullptr) noexcept;
    template <class U>
    void reset(U p) noexcept = delete;
    void swap(unique_ptr& u) noexcept;  // disable copy from lvalue unique_ptr(const unique_ptr&) = delete;
    unique_ptr& operator=(const unique_ptr&) = delete;
};
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein `unique_ptr`.

*Nptr*\
Ein `rvalue` vom Typ `std::nullptr_t`.

*PTR*\
Ein `pointer`.

*Deleter*\
Eine `deleter`-Funktion, die an `unique_ptr` gebunden ist.

## <a name="exceptions"></a>Ausnahmen

Es werden keine Ausnahmen von `unique_ptr` generiert.

## <a name="remarks"></a>Bemerkungen

Die `unique_ptr`-Klasse löst `auto_ptr` ab und kann als Element von C++Standardbibliothek-Containern verwendet werden.

Verwenden Sie die [make_unique](../standard-library/memory-functions.md#make_unique)-Hilfsfunktion, um neue Instanzen von `unique_ptr` effizient zu erstellen.

`unique_ptr` verwaltet eine Ressource eindeutig. Jedes `unique_ptr`-Objekt speichert einen Zeiger auf das Objekt, das es besitzt, oder speichert einen NULL-Zeiger. Es kann höchstens ein `unique_ptr`-Objekt eine Ressource besitzen. Wird ein `unique_ptr`-Objekt, das eine bestimmte Ressource besitzt, zerstört, wird die Ressource freigegeben. Ein `unique_ptr`-Objekt kann verschoben, aber nicht kopiert werden. Weitere Informationen finden Sie unter [Rvalue-Verweisdeklarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

Die Ressource wird freigegeben, indem ein gespeichertes `deleter`-Objekt vom Typ `Del` aufgerufen wird, dem bekannt ist, wie Ressourcen für ein bestimmtes `unique_ptr`-Objekt zugeordnet werden. Standardmäßig `deleter` `default_delete<T>` wird davon ausgegangen, dass die Ressource, auf die von verwiesen `ptr` wird, zugeordnet wird **`new`** , und dass Sie durch Aufrufen von freigegeben werden kann `delete _Ptr` . (Eine partielle `unique_ptr<T[]>`-Spezialisierung verwaltet Arrayobjekte, die `new[]` zugeordnet sind, und hat den Standardwert `deleter` `default_delete<T[]>`, der auf das Aufrufen von delete[] `ptr` spezialisiert ist.)

Der gespeicherte Zeiger auf eine zugehörige Ressource `stored_ptr` ist vom Typ `pointer`. Er lautet `Del::pointer`, wenn er definiert ist, und `T *`, wenn er nicht definiert ist. Das gespeicherte `deleter`-Objekt `stored_deleter` belegt keinen Speicherplatz im Objekt, wenn `deleter` zustandslos ist. Beachten Sie, dass `Del` ein Verweistyp sein kann.

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

|||
|-|-|
|[unique_ptr](#unique_ptr)|Es gibt sieben Konstruktoren für `unique_ptr`.|

### <a name="typedefs"></a>TypeDefs

|||
|-|-|
|[deleter_type](#deleter_type)|Ein Synonym für den Vorlagenparameter `Del`.|
|[element_type](#element_type)|Ein Synonym für den Vorlagenparameter `T`.|
|[Zeichner](#pointer)|Ein Synonym für `Del::pointer`, wenn der Wert definiert ist; andernfalls `T *`.|

### <a name="functions"></a>Functions

|||
|-|-|
|[get](#get)|Gibt `stored_ptr`zurück.|
|[get_deleter](#get_deleter)|Gibt einen Verweis auf `stored_deleter`zurück.|
|[Abgabe](#release)|speichert `pointer()` in `stored_ptr` und gibt seinen vorherigen Inhalt zurück.|
|[reset](#reset)|Gibt die zurzeit zugehörige Ressource frei und akzeptiert eine neue Ressource.|
|[swap](#swap)|Tauscht die Ressource und `deleter` mit dem bereitgestellten `unique_ptr`-Objekt aus.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|**Operator bool**|Der-Operator gibt einen Wert eines Typs zurück, der in konvertierbar ist **`bool`** . Das Ergebnis der Konvertierung in **`bool`** ist **`true`** , wenn `get() != pointer()` , andernfalls **`false`** .|
|`operator->`|Die Memberfunktion gibt `stored_ptr` zurück.|
|`operator*`|Die Memberfunktion gibt `*stored_ptr` zurück.|
|[Operator =](#unique_ptr_operator_eq)|Weist den Wert eines `unique_ptr` (oder eines `pointer-type`) dem aktuellen `unique_ptr` zu.|

### <a name="deleter_type"></a><a name="deleter_type"></a>deleter_type

Der Type stellt ein Synonym für den Vorlagenparameter `Del` dar.

```cpp
typedef Del deleter_type;
```

#### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `Del` dar.

### <a name="element_type"></a><a name="element_type"></a>element_type

Der Type stellt ein Synonym für den Vorlagenparameter `Type` dar.

```cpp
typedef Type element_type;
```

#### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `Ty` dar.

### <a name="get"></a><a name="get"></a>Erhalten

Gibt `stored_ptr`zurück.

```cpp
pointer get() const;
```

#### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt `stored_ptr` zurück.

### <a name="get_deleter"></a><a name="get_deleter"></a>get_deleter

Gibt einen Verweis auf `stored_deleter`zurück.

```cpp
Del& get_deleter();

const Del& get_deleter() const;
```

#### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt einen Verweis auf `stored_deleter` zurück.

### <a name="operator"></a><a name="unique_ptr_operator_eq"></a>Operator =

Weist die Adresse des bereitgestellten `unique_ptr`-Objekts dem aktuellen Objekt zu.

```cpp
unique_ptr& operator=(unique_ptr&& right);
template <class U, Class Del2>
unique_ptr& operator=(unique_ptr<Type, Del>&& right);
unique_ptr& operator=(pointer-type);
```

#### <a name="parameters"></a>Parameter

Ein `unique_ptr`-Verweis, der verwendet wird, um den Wert des aktuellen `unique_ptr`-Objekts zuzuweisen.

#### <a name="remarks"></a>Bemerkungen

Der Member Functions ruft `reset(right.release())` auf und wechselt `right.stored_deleter` zu und `stored_deleter` gibt dann zurück **`*this`** .

### <a name="pointer"></a><a name="pointer"></a>-Zeiger

Ein Synonym für `Del::pointer`, wenn der Wert definiert ist; andernfalls `Type *`.

```cpp
typedef T1 pointer;
```

#### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für `Del::pointer`, sofern dieser definiert ist; andernfalls `Type *`.

### <a name="release"></a><a name="release"></a>Abgabe

Gibt den Besitz des zurückgegebenen gespeicherten Zeigers für den Aufrufer frei und legt den gespeicherten Zeiger Wert auf fest **`nullptr`** .

```cpp
pointer release();
```

#### <a name="remarks"></a>Bemerkungen

Verwenden Sie `release`, um den Besitz des von `unique_ptr` gespeicherten unformatierten Zeigers zu übernehmen. Der Aufrufer ist für das Löschen des zurückgegebenen Zeigers verantwortlich. `unique-ptr` wird in seinen leeren, standardmäßig konstruierten Zustand gesetzt. Sie können `unique_ptr` einen anderen Zeiger mit kompatiblem Typ nach dem Aufruf von `release` zuweisen.

#### <a name="example"></a>Beispiel

Dieses Beispiel zeigt, inwiefern der Aufrufer von „release“ für das zurückgegebene Objekt verantwortlich ist:

```cpp
// stl_release_unique.cpp
// Compile by using: cl /W4 /EHsc stl_release_unique.cpp
#include <iostream>
#include <memory>

struct Sample {
   int content_;
   Sample(int content) : content_(content) {
      std::cout << "Constructing Sample(" << content_ << ")" << std::endl;
   }
   ~Sample() {
      std::cout << "Deleting Sample(" << content_ << ")" << std::endl;
   }
};

void ReleaseUniquePointer() {
   // Use make_unique function when possible.
   auto up1 = std::make_unique<Sample>(3);
   auto up2 = std::make_unique<Sample>(42);

   // Take over ownership from the unique_ptr up2 by using release
   auto ptr = up2.release();
   if (up2) {
      // This statement does not execute, because up2 is empty.
      std::cout << "up2 is not empty." << std::endl;
   }
   // We are now responsible for deletion of ptr.
   delete ptr;
   // up1 deletes its stored pointer when it goes out of scope.
}

int main() {
   ReleaseUniquePointer();
}
```

```Output
Constructing Sample(3)
Constructing Sample(42)
Deleting Sample(42)
Deleting Sample(3)
```

### <a name="reset"></a><a name="reset"></a>Festlegen

Übernimmt den Besitz des Zeigerparameters und löscht dann den ursprünglich gespeicherten Zeiger. Wenn der neue Zeiger mit dem ursprünglich gespeicherten Zeiger identisch ist, `reset` Löscht den Zeiger und legt den gespeicherten Zeiger auf fest **`nullptr`** .

```cpp
void reset(pointer ptr = pointer());
void reset(nullptr_t ptr);
```

#### <a name="parameters"></a>Parameter

*PTR*\
Ein Zeiger auf die Ressource, deren Besitz übernommen werden soll.

#### <a name="remarks"></a>Bemerkungen

Verwenden `reset` Sie, um den gespeicherten [Zeiger](#pointer) im Besitz von `unique_ptr` in *ptr* zu ändern, und löschen Sie dann den ursprünglich gespeicherten Zeiger. Wenn `unique_ptr` nicht leer war, ruft `reset` die Deleter-Funktion, die von [get_deleter](#get_deleter) zurückgegeben wurde, auf dem ursprünglich gespeicherten Zeiger auf.

Da `reset` zuerst den neuen Zeiger *ptr*speichert und dann den ursprünglich gespeicherten Zeiger löscht, ist es möglich, `reset` *ptr* sofort zu löschen, wenn er mit dem ursprünglich gespeicherten Zeiger identisch ist.

### <a name="swap"></a><a name="swap"></a>Wechsel

Tauscht Zeiger zwischen zwei `unique_ptr`-Objekten aus.

```cpp
void swap(unique_ptr& right);
```

#### <a name="parameters"></a>Parameter

*Richting*\
Ein `unique_ptr`-Objekt, das zum Tauschen von Zeigern verwendet wird.

#### <a name="remarks"></a>Bemerkungen

Die Memberfunktion tauscht `stored_ptr` mit `right.stored_ptr` und `stored_deleter` mit `right.stored_deleter`.

### <a name="unique_ptr"></a><a name="unique_ptr"></a>unique_ptr

Es gibt sieben Konstruktoren für `unique_ptr`.

```cpp
unique_ptr();

unique_ptr(nullptr_t);
explicit unique_ptr(pointer ptr);

unique_ptr(
    Type* ptr,
    typename conditional<
    is_reference<Del>::value,
    Del,
    typename add_reference<const Del>::type>::type _Deleter);

unique_ptr(pointer ptr, typename remove_reference<Del>::type&& _Deleter);
unique_ptr(unique_ptr&& right);
template <class Ty2, Class Del2>
    unique_ptr(unique_ptr<Ty2, Del2>&& right);
```

#### <a name="parameters"></a>Parameter

*PTR*\
Ein Zeiger auf die Ressource, die einem zugewiesen werden soll `unique_ptr` .

*_Deleter*\
Eine `deleter`-Funktion, die einem `unique_ptr`-Objekt zugewiesen werden soll.

*Richting*\
Eine `rvalue reference` auf ein `unique_ptr`-Objekt, aus dem `unique_ptr`-Felder dem neu erstellten `unique_ptr`-Objekt zugewiesen werden.

#### <a name="remarks"></a>Bemerkungen

Die ersten beiden Konstruktoren erstellen ein Objekt, das keine Ressource verwaltet. Der dritte Konstruktor speichert *ptr* in `stored_ptr` . Der vierte Konstruktor speichert *ptr* in `stored_ptr` und `deleter` in `stored_deleter` .

Der fünfte Konstruktor speichert *ptr* in `stored_ptr` und wechselt `deleter` in `stored_deleter` . Der sechste und der siebte Konstruktor speichern `right.release()` in `stored_ptr` und verschieben `right.get_deleter()` in `stored_deleter`.

### <a name="unique_ptr"></a><a name="dtorunique_ptr"></a>~ unique_ptr

Der Destruktor für `unique_ptr` zerstört ein `unique_ptr`-Objekt.

```cpp
~unique_ptr();
```

#### <a name="remarks"></a>Bemerkungen

Der Destruktor ruft `get_deleter()(stored_ptr)` auf.
