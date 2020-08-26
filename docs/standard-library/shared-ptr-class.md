---
title: shared_ptr-Klasse
ms.date: 07/29/2019
f1_keywords:
- memory/std::shared_ptr
- memory/std::shared_ptr::element_type
- memory/std::shared_ptr::get
- memory/std::shared_ptr::owner_before
- memory/std::shared_ptr::reset
- memory/std::shared_ptr::swap
- memory/std::shared_ptr::unique
- memory/std::shared_ptr::use_count
- memory/std::shared_ptr::operator boolean-type
- memory/std::shared_ptr::operator*
- memory/std::shared_ptr::operator=
- memory/std::shared_ptr::operator->
helpviewer_keywords:
- std::shared_ptr [C++]
- std::shared_ptr [C++], element_type
- std::shared_ptr [C++], get
- std::shared_ptr [C++], owner_before
- std::shared_ptr [C++], reset
- std::shared_ptr [C++], swap
- std::shared_ptr [C++], unique
- std::shared_ptr [C++], use_count
- std::shared_ptr [C++], element_type
- std::shared_ptr [C++], get
- std::shared_ptr [C++], owner_before
- std::shared_ptr [C++], reset
- std::shared_ptr [C++], swap
- std::shared_ptr [C++], unique
- std::shared_ptr [C++], use_count
ms.assetid: 1469fc51-c658-43f1-886c-f4530dd84860
ms.openlocfilehash: e41c76e7bd3e77b34ad38d3998ee1d38cdc2fee4
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846211"
---
# <a name="shared_ptr-class"></a>shared_ptr-Klasse

Umschließt einen intelligenten Zeiger mit Verweiszählung um ein dynamisch zugeordnetes Objekt.

## <a name="syntax"></a>Syntax

```cpp
template <class T>
class shared_ptr;
```

## <a name="remarks"></a>Bemerkungen

Die `shared_ptr` Klasse beschreibt ein Objekt, das die Verweis Zählung verwendet, um Ressourcen zu verwalten. Ein Objekt vom Typ `shared_ptr` enthält einen Zeiger auf die Ressource, die es besitzt, oder es enthält einen NULL-Zeiger. Es können mehrere `shared_ptr`-Objekte eine Ressource besitzen. Wird das letzte `shared_ptr`-Objekt beschädigt, das eine bestimmte Ressource besitzt, wird die Ressource freigegeben.

Ein `shared_ptr` beendet den Besitz einer Ressource, wenn diese erneut zugewiesen oder zurückgesetzt wird.

Das Vorlagenargument `T` kann ein unvollständiger Typ sein, außer wie für bestimmte Memberfunktionen aufgeführt.

Wenn ein `shared_ptr<T>`-Objekt von einem Ressourcenzeiger des Typs `G*` oder von einem `shared_ptr<G>` erstellt wird, muss der Zeigertyp `G*` konvertierbar sein in `T*`. Wenn Sie nicht konvertierbar ist, wird der Code nicht kompiliert. Beispiel:

```cpp
#include <memory>
using namespace std;

class F {};
class G : public F {};

shared_ptr<G> sp0(new G);   // okay, template parameter G and argument G*
shared_ptr<G> sp1(sp0);     // okay, template parameter G and argument shared_ptr<G>
shared_ptr<F> sp2(new G);   // okay, G* convertible to F*
shared_ptr<F> sp3(sp0);     // okay, template parameter F and argument shared_ptr<G>
shared_ptr<F> sp4(sp2);     // okay, template parameter F and argument shared_ptr<F>
shared_ptr<int> sp5(new G); // error, G* not convertible to int*
shared_ptr<int> sp6(sp2);   // error, template parameter int and argument shared_ptr<F>
```

Ein `shared_ptr`-Objekt besitzt in diesen Fällen eine Ressource:

- Es wurde mit einem Zeiger auf diese Ressource erstellt.

- Es wurde von einem `shared_ptr`-Objekt erstellt, das diese Ressource besitzt.

- Wenn Sie von einem [weak_ptr](weak-ptr-class.md) Objekt erstellt wurde, das auf diese Ressource verweist, oder

- Wenn der Besitz dieser Ressource zugewiesen wurde, entweder mit [shared_ptr:: Operator =](#op_eq) oder durch Aufrufen der Member-Funktion [shared_ptr:: Reset](#reset).

Von den `shared_ptr`-Objekten, die eine Ressource besitzen, wird ein Kontrollblock gemeinsam verwendet. Der Kontrollblock enthält:

- Die Anzahl von `shared_ptr`-Objekten, die die Ressource besitzen

- Die Anzahl von `weak_ptr`-Objekten, die auf die Ressource verweisen

- Den Deleter für diese Ressource, falls vorhanden

- Die benutzerdefinierte Zuweisung für den Kontrollblock, falls vorhanden

Ein `shared_ptr`-Objekt, das mit einem Null-Zeiger initialisiert wird, verfügt über einen Kontrollblock und ist nicht leer. Eine von einem `shared_ptr`-Objekt freigegebene Ressource ist nicht mehr im Besitz dieses Objekts. Nachdem ein `weak_ptr`-Objekt eine Ressource freigegeben hat, verweist es nicht mehr darauf.

Wenn die Anzahl von `shared_ptr`-Objekten, die eine Ressource besitzen, Null ergibt, wird die Ressource freigegeben. Dazu wird sie entweder gelöscht, oder ihre Adresse wird an einen Deleter übergeben. Das Verfahren hängt davon ab, wie die Besitzrechte der Ressource ursprünglich erstellt wurden. Wenn die Anzahl von `shared_ptr`-Objekten, die eine Ressource besitzen, null ist und auch die Anzahl von `weak_ptr`-Objekten, die auf diese Ressource zeigen, null ist, wird der Kontrollblock freigegeben. Dazu wird die benutzerdefinierte Zuweisung für den Kontrollblock verwendet, falls vorhanden.

Ein leeres `shared_ptr`-Objekt besitzt keine Ressourcen und verfügt über keinen Kontrollblock.

Ein Deleter ist ein Funktionsobjekt mit einer Memberfunktion `operator()`. Für den Typ muss eine Kopie erstellt werden können. Vom Kopierkonstruktor und vom Destruktor dürfen keine Ausnahmen ausgelöst werden. Als Parameter akzeptiert wird das zu löschende Objekt.

Von einigen Funktionen wird eine Argumentliste verwendet, mit der Eigenschaften des resultierenden `shared_ptr<T>`- oder `weak_ptr<T>`-Objekts definiert werden. Sie können eine solche Argumentliste wie folgt angeben:

Keine Argumente -- das resultierende Objekt ist ein leeres `shared_ptr`-Objekt oder ein leeres `weak_ptr`-Objekt.

`ptr` --ein Zeiger des Typs `Other*` auf die zu verwaltende Ressource. `T` muss ein vollständiger Typ sein. Wenn die Funktion fehlschlägt (da der Kontroll Block nicht zugeordnet werden kann), wird der Ausdruck ausgewertet `delete ptr` .

`ptr, deleter` -- ein Zeiger des Typs `Other*` auf die zu verwaltende Ressource und ein Deleter für diese Ressource. Wenn die Funktion fehlschlägt (da der Kontroll Block nicht zugeordnet werden kann), wird aufgerufen `deleter(ptr)` , was klar definiert sein muss.

`ptr, deleter, alloc` -- ein Zeiger des Typs `Other*` auf die zu verwaltende Ressource, ein Deleter für diese Ressource und eine Zuweisung zum Verwalten von Speicher, der zugeordnet und freigegeben werden muss. Wenn die Funktion fehlschlägt (da der Kontroll Block nicht zugeordnet werden kann), wird aufgerufen `deleter(ptr)` , was klar definiert sein muss.

`sp` -- ein `shared_ptr<Other>`-Objekt, das die zu verwaltende Ressource besitzt.

`wp` -- ein `weak_ptr<Other>`-Objekt, das auf die zu verwaltende Ressource zeigt.

`ap` -- ein `auto_ptr<Other>`-Objekt, das einen Zeiger auf die zu verwaltende Ressource enthält. Wenn die Funktion erfolgreich ausgeführt wird, wird aufgerufen `ap.release()` . andernfalls bleibt Sie `ap` unverändert.

In allen Fällen muss der Zeigertyp `Other*` konvertiert werden können in `T*`.

## <a name="thread-safety"></a>Threadsicherheit

Mehrere Threads können verschiedene `shared_ptr`-Objekte gleichzeitig lesen und schreiben, auch wenn die Objekte Kopien sind, die sich den Besitz teilen.

## <a name="members"></a>Member

|Name|Beschreibung|
|-|-|
| **Konstruktoren** | |
|[shared_ptr](#shared_ptr)|Erstellt ein Objekt vom Typ `shared_ptr`.|
|[~ shared_ptr](#dtorshared_ptr)|Beschädigt ein Objekt vom Typ `shared_ptr`.|
| **Typedefs** | |
|[element_type](#element_type)|Der Typ eines Elements.|
|[weak_type](#weak_type)|Der Typ eines schwachen Zeigers auf ein Element.|
| **Member-Funktionen** | |
|[get](#get)|Ruft die Adresse der Ressource ab, die Eigentum ist.|
|[owner_before](#owner_before)|Gibt True zurück, wenn dieses `shared_ptr` vor dem bereitgestellten Zeiger sortiert wird (Operator "Before" oder "Less than").|
|[reset](#reset)|Ersetzt die Ressource, die Eigentum ist.|
|[swap](#swap)|Tauscht zwei `shared_ptr`-Objekte.|
|[unique](#unique)|Prüft, ob die Ressource eindeutig ist, die Eigentum ist.|
|[use_count](#use_count)|Zählt Ressourcenbesitzer.|
| **Operatoren** | |
|[Operator bool](#op_bool)|Prüft, ob eine Ressource vorhanden ist, die Eigentum ist.|
|[KOM](#op_star)|Ruft den angegebenen Wert ab.|
|[Operator =](#op_eq)|Ersetzt die Ressource, die Eigentum ist.|
|[KOM&gt;](#op_arrow)|Ruft einen Zeiger auf den angegebenen Wert ab.|

## <a name="element_type"></a><a name="element_type"></a> element_type

Der Typ eines Elements.

```cpp
typedef T element_type;                  // before C++17
using element_type = remove_extent_t<T>; // C++17
```

### <a name="remarks"></a>Bemerkungen

Der `element_type` Typ ist ein Synonym für den Vorlagen Parameter `T` .

### <a name="example"></a>Beispiel

```cpp
// std__memory__shared_ptr_element_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));
    std::shared_ptr<int>::element_type val = *sp0;

    std::cout << "*sp0 == " << val << std::endl;

    return (0);
}
```

```Output
*sp0 == 5
```

## <a name="get"></a><a name="get"></a> Erhalten

Ruft die Adresse der Ressource ab, die Eigentum ist.

```cpp
element_type* get() const noexcept;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die Adresse der im Besitz befindlichen Ressource zurück. Wenn das Objekt nicht Besitzer einer Ressource ist, wird 0 zurückgegeben.

### <a name="example"></a>Beispiel

```cpp
// std__memory__shared_ptr_get.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));

    std::cout << "sp0.get() == 0 == " << std::boolalpha
        << (sp0.get() == 0) << std::endl;
    std::cout << "*sp1.get() == " << *sp1.get() << std::endl;

    return (0);
}
```

```Output
sp0.get() == 0 == true
*sp1.get() == 5
```

## <a name="operator-bool"></a><a name="op_bool"></a> Operator bool

Prüft, ob eine Ressource vorhanden ist, die Eigentum ist.

```cpp
explicit operator bool() const noexcept;
```

### <a name="remarks"></a>Bemerkungen

Der-Operator gibt einen Wert von zurück **`true`** `get() != nullptr` , andernfalls **`false`** .

### <a name="example"></a>Beispiel

```cpp
// std__memory__shared_ptr_operator_bool.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));

    std::cout << "(bool)sp0 == " << std::boolalpha
        << (bool)sp0 << std::endl;
    std::cout << "(bool)sp1 == " << std::boolalpha
        << (bool)sp1 << std::endl;

    return (0);
}
```

```Output
(bool)sp0 == false
(bool)sp1 == true
```

## <a name="operator"></a><a name="op_star"></a> KOM

Ruft den angegebenen Wert ab.

```cpp
T& operator*() const noexcept;
```

### <a name="remarks"></a>Bemerkungen

Der Dereferenzierungsoperator gibt `*get()` zurück. Daher darf der gespeicherte Zeiger nicht NULL sein.

### <a name="example"></a>Beispiel

```cpp
// std__memory__shared_ptr_operator_st.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));

    std::cout << "*sp0 == " << *sp0 << std::endl;

    return (0);
}
```

```Output
*sp0 == 5
```

## <a name="operator"></a><a name="op_eq"></a> Operator =

Ersetzt die Ressource, die Eigentum ist.

```cpp
shared_ptr& operator=(const shared_ptr& sp) noexcept;

shared_ptr& operator=(shared_ptr&& sp) noexcept;

template <class Other>
shared_ptr& operator=(const shared_ptr<Other>& sp) noexcept;

template <class Other>
shared_ptr& operator=(shared_ptr<Other>&& sp) noexcept;

template <class Other>
shared_ptr& operator=(auto_ptr<Other>&& ap);    // deprecated in C++11, removed in C++17

template <class Other, class Deleter>
shared_ptr& operator=(unique_ptr<Other, Deleter>&& up);
```

### <a name="parameters"></a>Parameter

*El*\
Der freigegebene Zeiger, von dem kopiert oder verschoben werden soll.

*Unglücks*\
Der zu Verschieb gende automatische Zeiger. Die Überladung `auto_ptr` ist in c++ 11 veraltet und wurde in c++ 17 entfernt.

*gegründet*\
Der eindeutige Zeiger auf das-Objekt, dessen Besitz übernommen werden soll. *up* besitzt nach dem-Befehl kein-Objekt.

*Außer*\
Der Typ des Objekts, auf das von *SP*, *AP*oder *up*verwiesen wird.

*Deleter*\
Der Typ des Löschvorgangs für das besitzende Objekt, das zum späteren Löschen des Objekts gespeichert wird.

### <a name="remarks"></a>Bemerkungen

Die Operatoren verringern alle den Verweis Zähler für die Ressource, die derzeit im Besitz von ist **`*this`** , und weisen den Besitz der Ressource, die von der operandensequenz benannt wird, zu zu **`*this`** . Wenn die Verweisanzahl auf 0 (null) fällt, wird die Ressource freigegeben. Wenn ein Operator fehlschlägt, bleibt er **`*this`** unverändert.

### <a name="example"></a>Beispiel

```cpp
// std__memory__shared_ptr_operator_as.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));
    std::unique_ptr<int> up(new int(10));

    sp0 = sp1;
    std::cout << "*sp0 == " << *sp0 << std::endl;

    sp0 = up;
    std::cout << "*sp0 == " << *sp0 << std::endl;

    return (0);
}
```

```Output
*sp0 == 5
*sp0 == 10
```

## <a name="operator-"></a><a name="op_arrow"></a> Operator->

Ruft einen Zeiger auf den angegebenen Wert ab.

```cpp
T* operator->() const noexcept;
```

### <a name="remarks"></a>Bemerkungen

Der Auswahloperator gibt `get()` zurück, sodass der Ausdruck `sp->member` sich wie `(sp.get())->member` verhält, wobei `sp` ein Objekt von Klasse `shared_ptr<T>` ist. Daher darf der gespeicherte Zeiger nicht NULL sein, und `T` muss eine Klasse, eine Struktur oder ein Union-Typ mit einem member-`member` sein.

### <a name="example"></a>Beispiel

```cpp
// std__memory__shared_ptr_operator_ar.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

typedef std::pair<int, int> Mypair;
int main()
{
    std::shared_ptr<Mypair> sp0(new Mypair(1, 2));

    std::cout << "sp0->first == " << sp0->first << std::endl;
    std::cout << "sp0->second == " << sp0->second << std::endl;

    return (0);
}
```

```Output
sp0->first == 1
sp0->second == 2
```

## <a name="owner_before"></a><a name="owner_before"></a> owner_before

Gibt True zurück, wenn dieses `shared_ptr` vor dem bereitgestellten Zeiger sortiert wird (Operator "Before" oder "Less than").

```cpp
template <class Other>
bool owner_before(const shared_ptr<Other>& ptr) const noexcept;

template <class Other>
bool owner_before(const weak_ptr<Other>& ptr) const noexcept;
```

### <a name="parameters"></a>Parameter

*PTR*\
Ein Lvalue-Verweis auf ein `shared_ptr` oder ein `weak_ptr` .

### <a name="remarks"></a>Bemerkungen

Die Template-Member-Funktion gibt true zurück, wenn **`*this`** vor geordnet ist `ptr` .

## <a name="reset"></a><a name="reset"></a> Festlegen

Ersetzt die Ressource, die Eigentum ist.

```cpp
void reset() noexcept;

template <class Other>
void reset(Other *ptr);

template <class Other, class Deleter>
void reset(
    Other *ptr,
    Deleter deleter);

template <class Other, class Deleter, class Allocator>
void reset(
    Other *ptr,
    Deleter deleter,
    Allocator alloc);
```

### <a name="parameters"></a>Parameter

*Außer*\
Der vom Argumentzeiger gesteuerte Typ.

*Deleter*\
Der Deleter-Typ.

*PTR*\
Der zu kopierende Zeiger.

*Deleter*\
Der zu kopierende Deleter.

*Allocator*\
Der Zuweisungstyp.

*Zuordnungseinheits*\
Der zu kopierende Zuweiser.

### <a name="remarks"></a>Bemerkungen

Die Operatoren verringern alle den Verweis Zähler für die Ressource, die derzeit im Besitz von ist **`*this`** , und weisen den Besitz der Ressource, die von der operandensequenz benannt wird, zu zu **`*this`** . Wenn die Verweisanzahl auf 0 (null) fällt, wird die Ressource freigegeben. Wenn ein Operator fehlschlägt, bleibt er **`*this`** unverändert.

### <a name="example"></a>Beispiel

```cpp
// std__memory__shared_ptr_reset.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp(new int(5));

    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    sp.reset();
    std::cout << "(bool)sp == " << std::boolalpha
        << (bool)sp << std::endl;

    sp.reset(new int(10));
    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    sp.reset(new int(15), deleter());
    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    return (0);
}
```

```Output
*sp == 5
(bool)sp == false
*sp == 10
*sp == 15
```

## <a name="shared_ptr"></a><a name="shared_ptr"></a> shared_ptr

Erstellt ein Objekt vom Typ `shared_ptr`.

```cpp
constexpr shared_ptr() noexcept;

constexpr shared_ptr(nullptr_t) noexcept : shared_ptr() {}

shared_ptr(const shared_ptr& sp) noexcept;

shared_ptr(shared_ptr&& sp) noexcept;

template <class Other>
explicit shared_ptr(Other* ptr);

template <class Other, class Deleter>
shared_ptr(
    Other* ptr,
    Deleter deleter);

template <class Deleter>
shared_ptr(
    nullptr_t ptr,
    Deleter deleter);

template <class Other, class Deleter, class Allocator>
shared_ptr(
    Other* ptr,
    Deleter deleter,
    Allocator alloc);

template <class Deleter, class Allocator>
shared_ptr(
    nullptr_t ptr,
    Deleter deleter,
    Allocator alloc);

template <class Other>
shared_ptr(
    const shared_ptr<Other>& sp) noexcept;

template <class Other>
explicit shared_ptr(
    const weak_ptr<Other>& wp);

template <class &>
shared_ptr(
    std::auto_ptr<Other>& ap);

template <class &>
shared_ptr(
    std::auto_ptr<Other>&& ap);

template <class Other, class Deleter>
shared_ptr(
    unique_ptr<Other, Deleter>&& up);

template <class Other>
shared_ptr(
    const shared_ptr<Other>& sp,
    element_type* ptr) noexcept;

template <class Other>
shared_ptr(
    shared_ptr<Other>&& sp,
    element_type* ptr) noexcept;

template <class Other, class Deleter>
shared_ptr(
    const unique_ptr<Other, Deleter>& up) = delete;
```

### <a name="parameters"></a>Parameter

*Außer*\
Der vom Argumentzeiger gesteuerte Typ.

*PTR*\
Der zu kopierende Zeiger.

*Deleter*\
Der Deleter-Typ.

*Allocator*\
Der Zuweisungstyp.

*Deleter*\
Der Deleter.

*Zuordnungseinheits*\
Die Zuweisung.

*El*\
Der zu kopierende intelligente Zeiger.

*UA*\
Der schwache Zeiger.

*Unglücks*\
Der zu kopierende automatische Zeiger

### <a name="remarks"></a>Bemerkungen

Die Konstruktoren erstellen jeweils ein Objekt, dem die Ressource gehört, die von der Operatorensequenz benannt wird. Der-Konstruktor löst `shared_ptr(const weak_ptr<Other>& wp)` ein Exception-Objekt vom Typ [bad_weak_ptr](bad-weak-ptr-class.md) if aus `wp.expired()` .

### <a name="example"></a>Beispiel

```cpp
// std__memory__shared_ptr_construct.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp0;
    std::cout << "(bool)sp0 == " << std::boolalpha
        << (bool)sp0 << std::endl;

    std::shared_ptr<int> sp1(new int(5));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    std::shared_ptr<int> sp2(new int(10), deleter());
    std::cout << "*sp2 == " << *sp2 << std::endl;

    std::shared_ptr<int> sp3(sp2);
    std::cout << "*sp3 == " << *sp3 << std::endl;

    std::weak_ptr<int> wp(sp3);
    std::shared_ptr<int> sp4(wp);
    std::cout << "*sp4 == " << *sp4 << std::endl;

    std::auto_ptr<int> ap(new int(15));
    std::shared_ptr<int> sp5(ap);
    std::cout << "*sp5 == " << *sp5 << std::endl;

    return (0);
}
```

```Output
(bool)sp0 == false
*sp1 == 5
*sp2 == 10
*sp3 == 10
*sp4 == 10
*sp5 == 15
```

## <a name="shared_ptr"></a><a name="dtorshared_ptr"></a> ~ shared_ptr

Beschädigt ein Objekt vom Typ `shared_ptr`.

```cpp
~shared_ptr();
```

### <a name="remarks"></a>Bemerkungen

Der-Dekonstruktor Dekremente den Verweis Zähler für die Ressource, die derzeit im Besitz von ist **`*this`** . Wenn die Verweisanzahl auf 0 (null) fällt, wird die Ressource freigegeben.

### <a name="example"></a>Beispiel

```cpp
// std__memory__shared_ptr_destroy.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << "use count == " << sp1.use_count() << std::endl;

    {
        std::shared_ptr<int> sp2(sp1);
        std::cout << "*sp2 == " << *sp2 << std::endl;
        std::cout << "use count == " << sp1.use_count() << std::endl;
    }

    // check use count after sp2 is destroyed
    std::cout << "use count == " << sp1.use_count() << std::endl;

    return (0);
}
```

```Output
*sp1 == 5
use count == 1
*sp2 == 5
use count == 2
use count == 1
```

## <a name="swap"></a><a name="swap"></a> Wechsel

Tauscht zwei `shared_ptr`-Objekte.

```cpp
void swap(shared_ptr& sp) noexcept;
```

### <a name="parameters"></a>Parameter

*El*\
Der gemeinsame Zeiger, mit dem getauscht werden soll.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion verlässt die Ressource, die sich ursprünglich im Besitz **`*this`** von *SP*befand, und die Ressource, die ursprünglich im Besitz von *SP* war, danach im Besitz von **`*this`** . Die Funktion ändert die Verweisanzahlen für die beiden Ressourcen nicht und löst auch keine Ausnahmen aus.

### <a name="example"></a>Beispiel

```cpp
// std__memory__shared_ptr_swap.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::shared_ptr<int> sp2(new int(10));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    sp1.swap(sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;

    swap(sp1, sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << std::endl;

    std::weak_ptr<int> wp1(sp1);
    std::weak_ptr<int> wp2(sp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    wp1.swap(wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    swap(wp1, wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    return (0);
}
```

```Output
*sp1 == 5
*sp1 == 10
*sp1 == 5
*wp1 == 5
*wp1 == 10
*wp1 == 5
```

## <a name="unique"></a><a name="unique"></a> gem

Prüft, ob die Ressource eindeutig ist, die Eigentum ist. Diese Funktion wurde in c++ 17 als veraltet markiert und in c++ 20 entfernt.

```cpp
bool unique() const noexcept;
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt zurück **`true`** , wenn kein anderes `shared_ptr` Objekt die Ressource besitzt, die sich im Besitz von befindet **`*this`** , andernfalls **`false`** .

### <a name="example"></a>Beispiel

```cpp
// std__memory__shared_ptr_unique.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::cout << "sp1.unique() == " << std::boolalpha
        << sp1.unique() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "sp1.unique() == " << std::boolalpha
        << sp1.unique() << std::endl;

    return (0);
}
```

```Output
sp1.unique() == true
sp1.unique() == false
```

## <a name="use_count"></a><a name="use_count"></a> use_count

Zählt Ressourcenbesitzer.

```cpp
long use_count() const noexcept;
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt die Anzahl der- `shared_ptr` Objekte zurück, die Besitzer der Ressource sind, die im Besitz von ist **`*this`** .

### <a name="example"></a>Beispiel

```cpp
// std__memory__shared_ptr_use_count.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::cout << "sp1.use_count() == "
        << sp1.use_count() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "sp1.use_count() == "
        << sp1.use_count() << std::endl;

    return (0);
}
```

```Output
sp1.use_count() == 1
sp1.use_count() == 2
```

## <a name="weak_type"></a><a name="weak_type"></a> weak_type

Der Typ eines schwachen Zeigers auf ein Element.

```cpp
using weak_type = weak_ptr<T>; // C++17
```

### <a name="remarks"></a>Bemerkungen

Die `weak_type` Definition wurde in c++ 17 hinzugefügt.

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](cpp-standard-library-header-files.md)\
[\<memory>](memory.md)\
[unique_ptr](unique-ptr-class.md)\
[weak_ptr-Klasse](weak-ptr-class.md)
