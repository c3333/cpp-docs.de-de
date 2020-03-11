---
title: '&lt;memory&gt;-Funktionen'
ms.date: 08/05/2019
f1_keywords:
- memory/std::addressof
- memory/std::align
- memory/std::allocate_shared
- memory/std::const_pointer_cast
- memory/std::declare_no_pointers
- memory/std::declare_reachable
- memory/std::default_delete
- memory/std::dynamic_pointer_cast
- memory/std::get_deleter
- memory/std::get_pointer_safety
- memory/std::get_temporary_buffer
- xmemory/std::get_temporary_buffer
- memory/std::make_shared
- memory/std::make_unique
- memory/std::owner_less
- memory/std::reinterpret_pointer_cast
- memory/std::return_temporary_buffer
- xmemory/std::return_temporary_buffer
- memory/std::static_pointer_cast
- memory/std::swap
- memory/std::undeclare_no_pointers
- memory/std::undeclare_reachable
- memory/std::uninitialized_copy
- memory/std::uninitialized_copy_n
- memory/std::uninitialized_fill
- memory/std::uninitialized_fill_n
- memory/std::get_temporary_buffer
- memory/std::return_temporary_buffer
ms.assetid: 3e1898c2-44b7-4626-87ce-84962e4c6f1a
helpviewer_keywords:
- std::addressof [C++]
- std::align [C++]
- std::allocate_shared [C++]
- std::const_pointer_cast [C++]
- std::declare_no_pointers [C++]
- std::declare_reachable [C++]
- std::default_delete [C++]
- std::dynamic_pointer_cast [C++]
- std::get_deleter [C++]
- std::get_pointer_safety [C++]
- std::get_temporary_buffer [C++]
- std::make_shared [C++]
- std::make_unique [C++]
- std::owner_less [C++]
- std::return_temporary_buffer [C++]
- std::static_pointer_cast [C++]
- std::swap [C++]
- std::undeclare_no_pointers [C++]
- std::undeclare_reachable [C++]
- std::uninitialized_copy [C++]
- std::uninitialized_copy_n [C++]
- std::uninitialized_fill [C++]
- std::uninitialized_fill_n [C++]
- std::addressof [C++]
- std::align [C++]
- std::allocate_shared [C++]
- std::const_pointer_cast [C++]
- std::declare_no_pointers [C++]
- std::declare_reachable [C++]
- std::default_delete [C++]
- std::dynamic_pointer_cast [C++]
- std::get_deleter [C++]
- std::get_pointer_safety [C++]
- std::get_temporary_buffer [C++]
- std::make_shared [C++]
- std::make_unique [C++]
- std::owner_less [C++]
- std::return_temporary_buffer [C++]
- std::static_pointer_cast [C++]
- std::undeclare_no_pointers [C++]
- std::undeclare_reachable [C++]
- std::uninitialized_copy [C++]
- std::uninitialized_copy_n [C++]
- std::uninitialized_fill [C++]
- std::uninitialized_fill_n [C++]
ms.openlocfilehash: 2aceb96fcda49df8a1fd40a1bd8011170dccd8ef
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856682"
---
# <a name="ltmemorygt-functions"></a>&lt;memory&gt;-Funktionen

## <a name="addressof"></a>AddressOf

Ruft die echte Adresse eines Objekts ab.

```cpp
template <class T>
T* addressof(
    T& value) noexcept;    // before C++17

template <class T>
constexpr T* addressof(
    T& value) noexcept;    // C++17

template <class T>
const T* addressof(
    const T&& value) = delete;   // C++17
```

### <a name="parameters"></a>Parameter

*value*\
Das Objekt oder die Funktion, für das bzw. die die echte Adresse abgerufen wird.

### <a name="return-value"></a>Rückgabewert

Die tatsächliche Adresse des Objekts oder der Funktion, auf die als *Wert*verwiesen wird, selbst wenn ein überladener `operator&()` vorhanden ist.

### <a name="remarks"></a>Bemerkungen

## <a name="align"></a>abzustimmen

Passt den Speicher der angegebenen Größe, die durch die angegebene Ausrichtungs Spezifikation ausgerichtet ist, in die erste mögliche Adresse des angegebenen Speichers an.

```cpp
void* align(
    size_t alignment, // input
    size_t size,      // input
    void*& ptr,       // input/output
    size_t& space     // input/output
);
```

### <a name="parameters"></a>Parameter

*Ausrichtungs*\
Die auszuprobierende Ausrichtungsgrenze.

*size*\
Die Größe in Bytes für den ausgerichteten Speicher.

*ptr* -\
Die Startadresse des verfügbaren zusammenhängenden Speicherpools, der verwendet werden soll. Dieser Parameter ist auch ein Output-Parameter und wird so festgelegt, dass die neue Startadresse enthalten ist, wenn die Ausrichtung erfolgreich ist. Wenn `align()` nicht erfolgreich ist, wird dieser Parameter nicht geändert.

*Leerraum*\
Der gesamte verfügbare Speicherplatz, den `align()` beim Erstellen des ausgerichteten Speichers verwendet. Dieser Parameter ist auch ein Ausgabeparameter und enthält den angepassten Speicherplatz, der im Speicherpuffer verblieben ist, nachdem der ausgerichtete Speicher und der zugeordnete Mehraufwand subtrahiert wurden.

Wenn `align()` nicht erfolgreich ist, wird dieser Parameter nicht geändert.

### <a name="return-value"></a>Rückgabewert

Ein NULL-Zeiger, wenn der angeforderte ausgerichtete Puffer nicht in den verfügbaren Platz passt. andernfalls der neue Wert von *ptr*.

### <a name="remarks"></a>Bemerkungen

Mit den geänderten *ptr* -und *Space* -Parametern können Sie `align()` wiederholt im gleichen Puffer aufzurufen, möglicherweise mit verschiedenen Werten für *Ausrichtung* und *Größe*. Im folgenden Codeausschnitt wird eine Verwendung von `align()` veranschaulicht:

```cpp
#include <type_traits> // std::alignment_of()
#include <memory>
//...
char buffer[256]; // for simplicity
size_t alignment = std::alignment_of<int>::value;
void * ptr = buffer;
std::size_t space = sizeof(buffer); // Be sure this results in the true size of your buffer

while (std::align(alignment, sizeof(MyObj), ptr, space)) {
    // You now have storage the size of MyObj, starting at ptr, aligned on
    // int boundary. Use it here if you like, or save off the starting address
    // contained in ptr for later use.
    // ...
    // Last, move starting pointer and decrease available space before
    // the while loop restarts.
    ptr = reinterpret_cast<char*>(ptr) + sizeof(MyObj);
    space -= sizeof(MyObj);
}
// At this point, align() has returned a null pointer, signaling it is not
// possible to allow more aligned storage in this buffer.
```

## <a name="allocate_shared"></a>allocate_shared

Erstellt eine [shared_ptr](shared-ptr-class.md) mit Objekten, die für einen angegebenen Typ mithilfe einer angegebenen Zuweisung zugeordnet und erstellt werden. Gibt `shared_ptr` zurück.

```cpp
template <class T, class Allocator, class... Args>
shared_ptr<T> allocate_shared(
    Allocator alloc,
    Args&&... args);
```

### <a name="parameters"></a>Parameter

*Zuordnung*\
Die Zuweisung wird zur Erstellung von Objekten verwendet.

*args*\
Keine oder mehrere Argumente, die zu Objekten werden.

### <a name="remarks"></a>Bemerkungen

Die-Funktion erstellt das Objekt `shared_ptr<T>`, einen Zeiger auf `T(args...)`, *wie von der Zuweisung zugeordnet*und erstellt.

## <a name="atomic_compare_exchange_strong"></a>atomic_compare_exchange_strong

```cpp
template<class T>
bool atomic_compare_exchange_strong(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w);
```

## <a name="atomic_compare_exchange_weak"></a>atomic_compare_exchange_weak

```cpp
template<class T>
bool atomic_compare_exchange_weak(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w);
```

## <a name="atomic_compare_exchange_strong_explicit"></a>atomic_compare_exchange_strong_explicit

```cpp
template<class T>
bool atomic_compare_exchange_strong_explicit(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w,
    memory_order success,
    memory_order failure);
```

## <a name="atomic_compare_exchange_weak_explicit"></a>atomic_compare_exchange_weak_explicit

```cpp
template<class T>
bool atomic_compare_exchange_weak_explicit(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w,
    memory_order success,
    memory_order failure);
```

## <a name="atomic_exchange"></a>atomic_exchange

```cpp
template<class T>
shared_ptr<T> atomic_exchange(
    shared_ptr<T>* u,
    shared_ptr<T> r);
```

## <a name="atomic_exchange_explicit"></a>atomic_exchange_explicit

```cpp
template<class T>
shared_ptr<T> atomic_exchange_explicit(
    shared_ptr<T>* u,
    shared_ptr<T> r,
    memory_order mo);
```

## <a name="atomic_is_lock_free"></a>atomic_is_lock_free

```cpp
template<class T>
bool atomic_is_lock_free(
    const shared_ptr<T>* u);
```

## <a name="atomic_load"></a>atomic_load

```cpp
template<class T>
shared_ptr<T> atomic_load(
    const shared_ptr<T>* u);
```

## <a name="atomic_load_explicit"></a>atomic_load_explicit

```cpp
template<class T>
shared_ptr<T> atomic_load_explicit(
    const shared_ptr<T>* u,
    memory_order mo);
```

## <a name="atomic_store"></a>atomic_store

```cpp
template<class T>
void atomic_store(
    shared_ptr<T>* u,
    shared_ptr<T> r);
```

## <a name="atomic_store_explicit"></a>atomic_store_explicit

```cpp
template<class T>
void atomic_store_explicit(
    shared_ptr<T>* u,
    shared_ptr<T> r,
    memory_order mo);
```

## <a name="const_pointer_cast"></a>const_pointer_cast

Konstante Umwandlung in [shared_ptr](shared-ptr-class.md).

```cpp
template <class T, class Other>
shared_ptr<T> const_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> const_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>Parameter

*T*\
Der Typ, der vom zurückgegebenen gemeinsamen Zeiger (shared pointer) gesteuert wird.

*Andere*\
Der Typ, der vom Argument für den gemeinsamen Zeiger gesteuert wird.

*SP* -\
Das Argument für den gemeinsamen Zeiger.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt ein leeres `shared_ptr` Objekt zurück, wenn `const_cast<T*>(sp.get())` einen NULL-Zeiger zurückgibt. Andernfalls wird ein `shared_ptr<T>` Objekt zurückgegeben, das die Ressource besitzt, die im Besitz von *SP*ist. Der Ausdruck `const_cast<T*>(sp.get())` muss gültig sein.

### <a name="example"></a>Beispiel

```cpp
// std__memory__const_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int);
    std::shared_ptr<const int> sp1 =
        std::const_pointer_cast<const int>(sp0);

    *sp0 = 3;
    std::cout << "sp1 == " << *sp1 << std::endl;

    return (0);
}
```

```Output
sp1 == 3
```

## <a name="declare_no_pointers"></a>declare_no_pointers

Einem Garbage Collector wird mitgeteilt, dass die Zeichen im Speicherblock, der von einem Basisadressenzeiger und -blockgröße definiert wurde, keine nachweisbaren Zeiger enthalten.

```cpp
void declare_no_pointers(
    char* ptr,
    size_t size);
```

### <a name="parameters"></a>Parameter

*ptr* -\
Adresse des ersten Zeichens, das keinen nachweisbaren Zeiger mehr enthält.

*size*\
Blockgröße, die bei *ptr* beginnt und keine nachvollziehbaren Zeiger enthält.

### <a name="remarks"></a>Bemerkungen

Die-Funktion informiert alle Garbage Collector, dass die Adressen im Bereich `[ ptr, ptr + size)` keine nachvollziehbaren Zeiger mehr enthalten. (Alle Zeiger auf zugeordneten Speicher dürfen nicht dereferenziert werden, es sei denn, Sie wurden erreichbar gemacht.)

## <a name="declare_reachable"></a>declare_reachable

Der Garbage Collection wird mitgeteilt, dass die angegebene Adresse von zugewiesenem Speicher erreichbar ist.

```cpp
void declare_reachable(
    void* ptr);
```

### <a name="parameters"></a>Parameter

*ptr* -\
Ein Zeiger auf einen erreichbaren zugewiesenen gültigen Speicherbereich.

### <a name="remarks"></a>Bemerkungen

Wenn *ptr* nicht NULL ist, informiert die Funktion jeden Garbage Collector, dass *ptr* nun erreichbar ist, d. h., er verweist auf einen gültigen zugeordneten Speicher.

## <a name="default_delete"></a>default_delete

Löscht mit **Operator new**zugeordnete-Objekte. Geeignet für die Verwendung mit [unique_ptr](unique-ptr-class.md).

```cpp
struct default_delete
{
    constexpr default_delete() noexcept = default;

    template <class Other, class = typename enable_if<is_convertible<Other*, T*>::value, void>::type>>
    default_delete(const default_delete<Other>&) noexcept;

    void operator()(T* ptr) const noexcept;
};
```

### <a name="parameters"></a>Parameter

*ptr* -\
Zeiger auf das zu löschende Objekt.

*Andere*\
Die anderen Typen von Elementen im Array, die gelöscht werden sollen.

### <a name="remarks"></a>Bemerkungen

Die Klassen Vorlage beschreibt einen Deleter, der mit **Operator new**zugewiesene skalare Objekte löscht, die für die Verwendung mit Klassen Vorlagen `unique_ptr`geeignet sind. Außerdem ist die explizite Spezialisierung `default_delete<T[]>` vorhanden.

## <a name="destroy_at"></a>destroy_at

```cpp
template <class T>
void destroy_at(
    T* location);
```

Identisch mit `location->~T()`.

## <a name="destroy"></a>zerstören

```cpp
template <class ForwardIterator>
void destroy(
    ForwardIterator first,
    ForwardIterator last);
```

Identisch mit:

```cpp
for (; first != last; ++first)
    destroy_at(addressof(*first));
```

## <a name="destroy_n"></a>destroy_n

```cpp
template <class ForwardIterator, class Size>
ForwardIterator destroy_n(
    ForwardIterator first,
    Size count);
```

Identisch mit:

```cpp
for (; count > 0; (void)++first, --count)
    destroy_at(addressof(*first));
return first;
```

## <a name="dynamic_pointer_cast"></a>dynamic_pointer_cast

Dynamische Umwandlung in [shared_ptr](shared-ptr-class.md).

```cpp
template <class T, class Other>
shared_ptr<T> dynamic_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> dynamic_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>Parameter

*T*\
Der Typ, der vom zurückgegebenen gemeinsamen Zeiger (shared pointer) gesteuert wird.

*Andere*\
Der Typ, der vom Argument für den gemeinsamen Zeiger gesteuert wird.

*SP* -\
Das Argument für den gemeinsamen Zeiger.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt ein leeres `shared_ptr` Objekt zurück, wenn `dynamic_cast<T*>(sp.get())` einen NULL-Zeiger zurückgibt. Andernfalls wird ein `shared_ptr<T>` Objekt zurückgegeben, das die Ressource besitzt, die im Besitz von *SP*ist. Der Ausdruck `dynamic_cast<T*>(sp.get())` muss gültig sein.

### <a name="example"></a>Beispiel

```cpp
// std__memory__dynamic_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    virtual ~base() {}
    int value;
};

struct derived
    : public base
{
};

int main()
{
    std::shared_ptr<base> sp0(new derived);
    std::shared_ptr<derived> sp1 =
        std::dynamic_pointer_cast<derived>(sp0);

    sp0->value = 3;
    std::cout << "sp1->value == " << sp1->value << std::endl;

    return (0);
}
```

```Output
sp1->value == 3
```

## <a name="get_deleter"></a>get_deleter

Löschen Sie den Deleter aus einer [shared_ptr](shared-ptr-class.md).

```cpp
template <class Deleter, class T>
Deleter* get_deleter(
    const shared_ptr<T>& sp) noexcept;
```

### <a name="parameters"></a>Parameter

*Deleter* -\
Der Deleter-Typ.

*T*\
Der vom freigegebenen Zeiger gesteuerte Typ.

*SP* -\
Der freigegebene Zeiger.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt einen Zeiger auf den Deleter vom Typ *Deleter* zurück, der zum `shared_ptr` Objekt *SP*gehört. Wenn *SP* keinen Deleter hat oder der Deleter nicht vom Typ *Deleter*ist, gibt die Funktion 0 zurück.

### <a name="example"></a>Beispiel

```cpp
// std__memory__get_deleter.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int value;
};

struct deleter
{
    void operator()(base *pb)
    {
        delete pb;
    }
};

int main()
{
    std::shared_ptr<base> sp0(new base);

    sp0->value = 3;
    std::cout << "get_deleter(sp0) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp0) != 0) << std::endl;

    std::shared_ptr<base> sp1(new base, deleter());

    sp0->value = 3;
    std::cout << "get_deleter(sp1) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp1) != 0) << std::endl;

    return (0);
}
```

```Output
get_deleter(sp0) != 0 == false
get_deleter(sp1) != 0 == true
```

## <a name="get_pointer_safety"></a>get_pointer_safety

Gibt den Typ der Zeigersicherheit zurück, der von einem Garbage Collector angenommen wird.

```cpp
pointer_safety get_pointer_safety() noexcept;
```

### <a name="remarks"></a>Bemerkungen

Die-Funktion gibt den Typ der Zeiger Sicherheit zurück, der von allen automatischen Garbage Collector angenommen wird.

## <a name="get_temporary_buffer"></a>get_temporary_buffer

Weist temporären Speicher für eine Sequenz von Elementen zu, die eine angegebene Anzahl von Elementen nicht überschreitet.

```cpp
template <class T>
pair<T *, ptrdiff_t> get_temporary_buffer(
    ptrdiff_t count);
```

### <a name="parameters"></a>Parameter

*Anzahl*\
Die maximale Anzahl der angeforderten Elemente, denen Speicher zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Ein `pair`, dessen erste Komponente ein Zeiger auf den zugewiesenen Speicher ist, und dessen zweite Komponente die Größe des Puffers angibt; sie gibt die maximale Zahl an Elementen an, die gespeichert werden kann.

### <a name="remarks"></a>Bemerkungen

Die Funktion fordert Speicher an; möglicherweise wird diese Anforderung aber zurückgewiesen. Wenn kein Puffer zugewiesen ist, gibt die Funktion „pair“ zurück; dabei ist die zweite Komponente entspricht null und die erste Komponente dem NULL-Zeiger.

Verwenden Sie diese Funktion nur für temporären Speicherplatz.

### <a name="example"></a>Beispiel

```cpp
// memory_get_temp_buf.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

int main( )
{
    // Create an array of ints
    int intArray [] = { 10, 20, 30, 40, 100, 200, 300, 1000, 2000 };
    int count = sizeof ( intArray ) / sizeof ( int );
    cout << "The number of integers in the array is: "
        << count << "." << endl;

    pair<int *, ptrdiff_t> resultPair;
    resultPair = get_temporary_buffer<int>( count );

    cout << "The number of elements that the allocated memory\n"
        << "could store is given by: resultPair.second = "
        << resultPair.second << "." << endl;
}
```

```Output
The number of integers in the array is: 9.
The number of elements that the allocated memory
could store is given by: resultPair.second = 9.
```

## <a name="make_shared"></a>make_shared

Erstellt eine [shared_ptr](shared-ptr-class.md) , die auf die zugeordneten Objekte zeigt, die mithilfe der Standardzuweisung aus null oder mehreren Argumenten erstellt werden, und gibt diese zurück. Weist sowohl ein Objekt des angegebenen Typs als auch `shared_ptr` zu und erstellt sie, um die Freigabe des Objekts zu verwalten, und gibt `shared_ptr` zurück.

```cpp
template <class T, class... Args>
shared_ptr<T> make_shared(
    Args&&... args);
```

### <a name="parameters"></a>Parameter

*args*\
Null oder mehr Konstruktorargumente. Die Funktion leitet auf Grundlage der bereitgestellten Argumente die erforderliche die Konstruktorüberladung ab.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie `make_shared` als einfache und effizientere Möglichkeit, um ein Objekt und `shared_ptr` zu erstellen, um den gemeinsamen, gleichzeitigen Zugriff auf das Objekt zu verwalten. Semantisch gesehen sind diese beiden Anweisungen äquivalent:

```cpp
auto sp = std::shared_ptr<Example>(new Example(argument));
auto msp = std::make_shared<Example>(argument);
```

Die erste Anweisung ergibt jedoch zwei Zuordnungen, und wenn die Zuordnung von `shared_ptr` fehlschlägt, nachdem die Zuordnung des `Example`-Objekts erfolgreich war, geht das unbenannte `Example`-Objekt verloren. Die Anweisung, die `make_shared` verwendet, ist einfacher, da nur ein Funktionsaufruf beteiligt ist. Sie ist effizienter, da die Bibliothek eine einzige Zuordnung für das Objekt und den intelligenten Zeiger vornehmen kann. Diese Funktion ist schneller und führt zu einer geringeren Speicherfragmentierung, und es besteht keine Möglichkeit, eine Ausnahme für eine Zuordnung, aber nicht für die andere zu erhalten. Die Leistung wird durch einen besseren Speicherort für den Code verbessert, der auf das Objekt verweist und den Verweiszähler im intelligenten Zeiger aktualisiert.

Verwenden Sie [make_unique](memory-functions.md#make_unique) , wenn Sie keinen gemeinsamen Zugriff auf das Objekt benötigen. Verwenden Sie [allocate_shared](memory-functions.md#allocate_shared), wenn Sie eine benutzerdefinierte Zuweisung für das Objekt angeben müssen. Sie können `make_shared` nicht verwenden, wenn das Objekt einen benutzerdefinierten Deleter benötigt, da es keine Möglichkeit gibt, den Deleter als Argument zu übergeben.

Im folgenden Beispiel wird die Erstellung freigegebener Zeiger auf einen Typ mithilfe bestimmter Konstruktorüberladungen veranschaulicht.

### <a name="example"></a>Beispiel

```cpp
// stl_make_shared.cpp
// Compile by using: cl /W4 /EHsc stl_make_shared.cpp
#include <iostream>
#include <string>
#include <memory>
#include <vector>

class Song {
public:
    std::wstring title_;
    std::wstring artist_;

    Song(std::wstring title, std::wstring artist) : title_(title), artist_(artist) {}
    Song(std::wstring title) : title_(title), artist_(L"Unknown") {}
};

void CreateSharedPointers()
{
    // Okay, but less efficient to have separate allocations for
    // Song object and shared_ptr control block.
    auto song = new Song(L"Ode to Joy", L"Beethoven");
    std::shared_ptr<Song> sp0(song);

    // Use make_shared function when possible. Memory for control block
    // and Song object are allocated in the same call:
    auto sp1 = std::make_shared<Song>(L"Yesterday", L"The Beatles");
    auto sp2 = std::make_shared<Song>(L"Blackbird", L"The Beatles");

    // make_shared infers which constructor to use based on the arguments.
    auto sp3 = std::make_shared<Song>(L"Greensleeves");

    // The playlist vector makes copies of the shared_ptr pointers.
    std::vector<std::shared_ptr<Song>> playlist;
    playlist.push_back(sp0);
    playlist.push_back(sp1);
    playlist.push_back(sp2);
    playlist.push_back(sp3);
    playlist.push_back(sp1);
    playlist.push_back(sp2);
    for (auto&& sp : playlist)
    {
        std::wcout << L"Playing " << sp->title_ <<
            L" by " << sp->artist_ << L", use count: " <<
            sp.use_count() << std::endl;
    }
}

int main()
{
    CreateSharedPointers();
}
```

Das Beispiel generiert die folgende Ausgabe:

```Output
Playing Ode to Joy by Beethoven, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
Playing Greensleeves by Unknown, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
```

## <a name="make_unique"></a>make_unique

Erstellt ein [unique_ptr](unique-ptr-class.md)-Element und gibt es an ein Objekt des angegebenen Typs zurück, das mithilfe der angegebenen Argumente erstellt wird.

```cpp
// make_unique<T>
template <class T, class... Args>
unique_ptr<T> make_unique(Args&&... args);

// make_unique<T[]>
template <class T>
unique_ptr<T> make_unique(size_t size);

// make_unique<T[N]> disallowed
template <class T, class... Args>
/* unspecified */ make_unique(Args&&...) = delete;
```

### <a name="parameters"></a>Parameter

*T*\
Der Typ des Objekts, auf das `unique_ptr` zeigt.

*Args*\
Die von *args*angegebenen Typen der Konstruktorargumente.

*args*\
Die Argumente, die an den Konstruktor des Objekts vom Typ *T*übergeben werden.

*Elemente*\
Ein Array von Elementen des Typs *T*.

*size*\
Die Anzahl von Elementen, denen im neue Array ein Bereich zugeordnet werden soll.

### <a name="remarks"></a>Bemerkungen

Die erste Überladung wird für einzelne Objekte verwendet. Die zweite Überladung wird für Arrays aufgerufen. Die dritte Überladung verhindert die Angabe einer Array Größe im Typargument (make_unique\<t [N] >); Diese Konstruktion wird nicht vom aktuellen Standard unterstützt. Wenn Sie `make_unique` verwenden, um `unique_ptr` in ein Array zu erstellen, müssen die Arrayelemente separat initialisiert werden. Anstatt diese Überladung zu verwenden, ist die Verwendung von [Std:: Vector](vector-class.md)möglicherweise eine bessere Wahl.

Da `make_unique` sorgfältig für die Ausnahmesicherheit implementiert wird, wird empfohlen, `make_unique` zu verwenden, anstatt `unique_ptr` -Konstruktoren direkt aufzurufen.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `make_unique`. Weitere Beispiele finden Sie unter [Vorgehensweise: Erstellen und Verwenden von unique_ptr-Instanzen](../cpp/how-to-create-and-use-unique-ptr-instances.md).

[!code-cpp[stl_smart_pointers#214](../cpp/codesnippet/CPP/memory-functions_1.cpp)]

Wenn der Fehler "C2280" in Verbindung mit `unique_ptr` angezeigt wird, ist der Grund dafür fast sicherlich, der Versuch, den Kopierkonstruktor aufzurufen, der eine gelöschte Funktion ist.

## <a name="owner_less"></a>owner_less

Ermöglicht Mischvergleiche, die auf Besitz basieren, freigegebener und schwacher Zeiger. Gibt **true** zurück, wenn der linke Parameter von der Element Funktion `owner_before`vor dem rechten Parameter geordnet ist.

```cpp
template <class T>
    struct owner_less; // not defined

template <class T>
struct owner_less<shared_ptr<T>>
{
    bool operator()(
        const shared_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;

    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;

    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;
};

template <class T>
struct owner_less<weak_ptr<T>>
    bool operator()(
        const weak_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;

    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;

    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;
};

template<> struct owner_less<void>
{
    template<class T, class U>
    bool operator()(
        const shared_ptr<T>& left,
        const shared_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const weak_ptr<T>& left,
        const weak_ptr<U>& right) const noexcept;
};
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein freigegebener oder schwacher Zeiger.

*Rechte*\
Ein freigegebener oder schwacher Zeiger.

### <a name="remarks"></a>Bemerkungen

Die Klassen Vorlagen definieren alle Member-Operatoren als Rückgabe `left.owner_before(right)`.

## <a name="reinterpret_pointer_cast"></a>reinterpret_pointer_cast

Erstellt eine neue `shared_ptr` aus einem vorhandenen freigegebenen Zeiger mithilfe einer Umwandlung.

```cpp
template<class T, class U>
shared_ptr<T> reinterpret_pointer_cast(
    const shared_ptr<U>& ptr) noexcept;

template<class T, class U>
shared_ptr<T> reinterpret_pointer_cast(
    shared_ptr<U>&& ptr) noexcept;
```

### <a name="parameters"></a>Parameter

*ptr* -\
Ein Verweis auf einen `shared_ptr<U>`.

### <a name="remarks"></a>Bemerkungen

Wenn *ptr* leer ist, ist der neue `shared_ptr` ebenfalls leer; andernfalls wird der Besitz mit *ptr*geteilt. Der neue freigegebene Zeiger ist das Ergebnis der Auswertung von `reinterpret_cast<Y*>(ptr.get())`, bei der `Y` `typename std::shared_ptr<T>::element_type`ist. Das Verhalten ist nicht definiert, wenn `reinterpret_cast<T*>((U*)nullptr)` nicht wohl geformt ist.

Die Vorlagen Funktion, die einen Lvalue-Verweis annimmt, ist neu in c++ 17. Die Vorlagen Funktion, die einen rvalue-Verweis annimmt, ist neu in c++ 20.

## <a name="return_temporary_buffer"></a>return_temporary_buffer

Gibt den temporären Speicher frei, der mithilfe der `get_temporary_buffer`-Vorlagenfunktion zugeordnet wurde.

```cpp
template <class T>
void return_temporary_buffer(
    T* buffer);
```

### <a name="parameters"></a>Parameter

*Puffer*\
Ein Zeiger auf dem freizugebenden Speicher.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion nur für temporären Speicherplatz.

### <a name="example"></a>Beispiel

```cpp
// memory_ret_temp_buf.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

int main( )
{
    // Create an array of ints
    int intArray [] = { 10, 20, 30, 40, 100, 200, 300 };
    int count = sizeof ( intArray ) / sizeof ( int );
    cout << "The number of integers in the array is: "
         << count << "." << endl;

    pair<int *, ptrdiff_t> resultPair;
    resultPair = get_temporary_buffer<int>( count );

    cout << "The number of elements that the allocated memory\n"
         << " could store is given by: resultPair.second = "
         << resultPair.second << "." << endl;

    int* tempBuffer = resultPair.first;

    // Deallocates memory allocated with get_temporary_buffer
    return_temporary_buffer( tempBuffer );
}
```

```Output
The number of integers in the array is: 7.
The number of elements that the allocated memory
could store is given by: resultPair.second = 7.
```

## <a name="static_pointer_cast"></a>static_pointer_cast

Statische Umwandlung in [shared_ptr](shared-ptr-class.md).

```cpp
template <class T, class Other>
shared_ptr<T> static_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> static_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>Parameter

*T*\
Der Typ, der vom zurückgegebenen gemeinsamen Zeiger (shared pointer) gesteuert wird.

*Andere*\
Der Typ, der vom Argument für den gemeinsamen Zeiger gesteuert wird.

*SP* -\
Das Argument für den gemeinsamen Zeiger.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt ein leeres `shared_ptr` Objekt zurück, wenn *SP* ein leeres `shared_ptr` Objekt ist. Andernfalls wird ein `shared_ptr<T>` Objekt zurückgegeben, das die Ressource besitzt, die im Besitz von *SP*ist. Der Ausdruck `static_cast<T*>(sp.get())` muss gültig sein.

### <a name="example"></a>Beispiel

```cpp
// std__memory__static_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int value;
};

struct derived
    : public base
{
};

int main()
{
    std::shared_ptr<base> sp0(new derived);
    std::shared_ptr<derived> sp1 =
        std::static_pointer_cast<derived>(sp0);

    sp0->value = 3;
    std::cout << "sp1->value == " << sp1->value << std::endl;

    return (0);
}
```

```Output
sp1->value == 3
```

## <a name="swap"></a>Wechsel

Tauschen Sie zwei [shared_ptr](shared-ptr-class.md)-, [unique_ptr](unique-ptr-class.md)-oder [weak_ptr](weak-ptr-class.md) -Objekte aus.

```cpp
template <class T>
void swap(
    shared_ptr<T>& left,
    shared_ptr<T>& right) noexcept;

template <class T, class Deleter>
void swap(
    unique_ptr<T, Deleter>& left,
    unique_ptr<T, Deleter>& right) noexcept;

template <class T>
void swap(
    weak_ptr<T>& left,
    weak_ptr<T>& right) noexcept;

```

### <a name="parameters"></a>Parameter

*T*\
Der vom Argumentzeiger gesteuerte Typ.

*Deleter* -\
Der Deleter des eindeutigen Zeiger Typs.

*Linker*\
Der linke Zeiger.

*Rechte*\
Der Rechte Zeiger.

### <a name="remarks"></a>Bemerkungen

Die Vorlagenfunktionen rufen `left.swap(right)` auf.

### <a name="example"></a>Beispiel

```cpp
// std__memory__swap.cpp
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

## <a name="undeclare_no_pointers"></a>undeclare_no_pointers

Einem Garbage Collector wird mitgeteilt, dass die Zeichen im Speicherblock, der von einem Basisadressenzeiger und -blockgröße definiert wurde, jetzt möglicherweise nachweisbare Zeiger enthalten.

```cpp
void undeclare_no_pointers(
    char* ptr,
    size_t size);
```

### <a name="parameters"></a>Parameter

*ptr* -\
Ein Zeiger auf die Speicheradresse, die zuvor mit [declare_no_pointers](#declare_no_pointers)gekennzeichnet wurde.

*size*\
Die Anzahl der Bytes im Speicherbereich. Dieser Wert muss der im `declare_no_pointers`-Befehl verwendeten Zahl entsprechen.

### <a name="remarks"></a>Bemerkungen

Die-Funktion informiert alle Garbage Collector, dass der Adressbereich `[ptr, ptr + size)` jetzt möglicherweise nachvollziehbare Zeiger enthält.

## <a name="undeclare_reachable"></a>undeclare_reachable

Widerruft eine Deklaration der Erreichbarkeit für einen angegebenen Speicher Speicherort.

```cpp
template <class T>
T *undeclare_reachable(
    T* ptr);
```

### <a name="parameters"></a>Parameter

*ptr* -\
Ein Zeiger auf die Speicheradresse, die zuvor mit [declare_reachable](#declare_reachable)gekennzeichnet wurde.

### <a name="remarks"></a>Bemerkungen

Wenn *ptr* nicht **nullptr**ist, informiert die Funktion alle Garbage Collector, dass *ptr* nicht mehr erreichbar ist. Er gibt einen sicheren abgeleiteten Zeiger zurück, der mit *ptr*übereinstimmt.

## <a name="uninitialized_copy"></a>uninitialized_copy

Es werden Objekte aus einem angegebenen Quellbereich in einen nicht initialisierten Zielbereich kopiert.

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(
    ExecutionPolicy&& policy,
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);
```

### <a name="parameters"></a>Parameter

*Richtlinien*\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Eingabeiterator, der das erste Element im Quellbereich adressiert.

*Letzter*\
Ein Eingabeiterator, der das letzte Element im Quellbereich adressiert.

*dest* -\
Ein Forward-Iterator, der das erste Element im Zielbereich adressiert.

### <a name="return-value"></a>Rückgabewert

Ein forward-Iterator, der die erste Position über dem Zielbereich hinaus adressiert, es sei denn, der Quellbereich war leer.

### <a name="remarks"></a>Bemerkungen

Dieser Algorithmus ermöglicht die Entkopplung der Speicherbelegung von der Objekterstellung.

Die Vorlagenfunktion führt Folgendes aus:

```cpp
while (first != last)
{
    new (static_cast<void*>(&* dest++))
        typename iterator_traits<InputIterator>::value_type(*first++);
}
return dest;
```

es sei denn, der Code löst eine Ausnahme aus. In diesem Fall sind alle erstellten Objekte zerstört und die Ausnahme wird erneut ausgelöst.

Die Überladung mit einer Ausführungs Richtlinie ist neu in c++ 17.

### <a name="example"></a>Beispiel

```cpp
// memory_uninit_copy.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    Integer(int x) : value(x) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    int Array[] = { 10, 20, 30, 40 };
    const int N = sizeof(Array) / sizeof(int);

    cout << "The initialized Array contains " << N << " elements: ";
    for (int i = 0; i < N; i++)
    {
        cout << " " << Array[i];
    }
    cout << endl;

    Integer* ArrayPtr = (Integer*)malloc(N * sizeof(int));
    Integer* LArrayPtr = uninitialized_copy(
        Array, Array + N, ArrayPtr);  // C4996

    cout << "Address of position after the last element in the array is: "
        << &Array[0] + N << endl;
    cout << "The iterator returned by uninitialized_copy addresses: "
        << (void*)LArrayPtr << endl;
    cout << "The address just beyond the last copied element is: "
        << (void*)(ArrayPtr + N) << endl;

    if ((&Array[0] + N) == (void*)LArrayPtr)
        cout << "The return value is an iterator "
        << "pointing just beyond the original array." << endl;
    else
        cout << "The return value is an iterator "
        << "not pointing just beyond the original array." << endl;

    if ((void*)LArrayPtr == (void*)(ArrayPtr + N))
        cout << "The return value is an iterator "
        << "pointing just beyond the copied array." << endl;
    else
        cout << "The return value is an iterator "
        << "not pointing just beyond the copied array." << endl;

    free(ArrayPtr);

    cout << "Note that the exact addresses returned will vary\n"
        << "with the memory allocation in individual computers."
        << endl;
}
```

## <a name="uninitialized_copy_n"></a>uninitialized_copy_n

Eine Kopie einer angegebenen Anzahl von Elementen aus einem Eingabeiterator wird erstellt. Die Kopien werden in einen Forward-Iterator abgelegt.

```cpp
template <class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    ExecutionPolicy&& policy,
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>Parameter

*Richtlinien*\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Eingabeiterator, der auf das zu kopierende Objekt verweist.

*Anzahl*\
Ein Ganzzahltyp mit oder ohne Vorzeichen, der die Anzahl von Kopiervorgängen für das Objekt angibt.

*dest* -\
Ein Forward-Iterator, der auf den Speicherort der neuen Kopien verweist.

### <a name="return-value"></a>Rückgabewert

Ein Forward-Iterator, der die erste Position nach dem Ziel adressiert. Wenn der Quellbereich leer war, adressiert der Iterator *zuerst*.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion führt effektiv den folgenden Code aus:

```cpp
    for (; 0 < count; --count)
        new (static_cast<void*>(&* dest++))
            typename iterator_traits<InputIterator>::value_type(*first++);
    return dest;
```

es sei denn, der Code löst eine Ausnahme aus. In diesem Fall sind alle erstellten Objekte zerstört und die Ausnahme wird erneut ausgelöst.

Die Überladung mit einer Ausführungs Richtlinie ist neu in c++ 17.

## <a name="uninitialized_default_construct"></a>uninitialized_default_construct

Standardmäßig erstellt Objekte des `value_type` der Iteratoren im angegebenen Bereich.

```cpp
template <class ForwardIterator>
void uninitialized_default_construct(
    ForwardIterator first,
    ForwardIterator last);

template <class ExecutionPolicy, class ForwardIterator>
void uninitialized_default_construct(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last);
```

### <a name="parameters"></a>Parameter

*Richtlinien*\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Iterator, der das erste Element im zu erstellende Bereich adressiert.

*Letzter*\
Ein Iterator, der ein Element hinter dem letzten Element im zu erstellende Bereich adressiert.

### <a name="remarks"></a>Bemerkungen

Die Version ohne Ausführungs Richtlinie ist praktisch identisch mit der folgenden:

```cpp
for (; first != last; ++first)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type;
```

Wenn eine Ausnahme ausgelöst wird, werden zuvor erstellte Objekte in einer nicht angegebenen Reihenfolge zerstört.

Die Version mit einer Ausführungs Richtlinie hat dasselbe Ergebnis, wird aber entsprechend der angegebenen *Richtlinie*ausgeführt.

Diese Funktionen sind neu in c++ 17.

## <a name="uninitialized_default_construct_n"></a>uninitialized_default_construct_n

Standard erstellt eine angegebene Anzahl von Objekten des `value_type`des Iterators, beginnend an der angegebenen Position.

```cpp
template <class ForwardIterator, class Size>
ForwardIterator uninitialized_default_construct_n(
    ForwardIterator first,
    Size count);

template <class ExecutionPolicy, class ForwardIterator, class Size>
ForwardIterator uninitialized_default_construct_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count);
```

### <a name="parameters"></a>Parameter

*Richtlinien*\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Iterator, der das erste Element im Zielbereich adressiert, der erstellt werden soll.

*Anzahl*\
Die Anzahl der Elemente im zu erstellenden Zielbereich.

### <a name="return-value"></a>Rückgabewert

Ein forward-Iterator, der die erste Position über dem Zielbereich hinaus adressiert, es sei denn, der Quellbereich war leer.

### <a name="remarks"></a>Bemerkungen

Die Version ohne Ausführungs Richtlinie ist praktisch identisch mit der folgenden:

```cpp
for (; count>0; (void)++first, --count)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type;
return first;
```

Wenn eine Ausnahme ausgelöst wird, werden zuvor erstellte Objekte in einer nicht angegebenen Reihenfolge zerstört.

Die Version mit einer Ausführungs Richtlinie hat dasselbe Ergebnis, wird aber entsprechend der angegebenen *Richtlinie*ausgeführt.

Diese Funktionen sind neu in c++ 17.

## <a name="uninitialized_fill"></a>uninitialized_fill

Objekte eines angegebenen Werts werden in einen nicht initialisierten Zielbereich kopiert.

```cpp
template <class ForwardIterator, class T>
void uninitialized_fill(
    ForwardIterator first,
    ForwardIterator last,
    const T& value);

template <class ExecutionPolicy, class ForwardIterator, class T>
void uninitialized_fill(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last,
    const T& value);
```

### <a name="parameters"></a>Parameter

*Richtlinien*\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein forward-Iterator, der das erste Element im Zielbereich adressiert, das initialisiert werden soll.

*Letzter*\
Ein forward-Iterator, der das letzte Element im Zielbereich adressiert, das initialisiert werden soll.

*value*\
Der Wert, der zum Initialisieren des Zielbereichs verwendet wird.

### <a name="remarks"></a>Bemerkungen

Dieser Algorithmus ermöglicht die Entkopplung der Speicherbelegung von der Objekterstellung.

Die Vorlagenfunktion führt Folgendes aus:

```cpp
while (first != last)
    new (static_cast<void*>(&* first ++))
        typename iterator_traits<ForwardIterator>::value_type (value);
```

es sei denn, der Code löst eine Ausnahme aus. In diesem Fall sind alle erstellten Objekte zerstört und die Ausnahme wird erneut ausgelöst.

Die Überladung mit einer Ausführungs Richtlinie ist neu in c++ 17.

### <a name="example"></a>Beispiel

```cpp
// memory_uninit_fill.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    // No default constructor
    Integer( int x ) : value( x ) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    const int N = 10;
    Integer value ( 25 );
    Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
    uninitialized_fill( Array, Array + N, value );
    cout << "The initialized Array contains: ";
    for ( int i = 0; i < N; i++ )
        {
            cout << Array[ i ].get() << " ";
        }
    cout << endl;
}
```

```Output
The initialized Array contains: 25 25 25 25 25 25 25 25 25 25
```

## <a name="uninitialized_fill_n"></a>uninitialized_fill_n

Kopiert Objekte eines angegebenen Werts in die angegebene Anzahl von Elementen eines nicht initialisierten Zielbereichs.

```cpp
template <class ForwardIterator, class Size, class T>
ForwardIterator uninitialized_fill_n(
    ForwardIterator first,
    Size count,
    const T& value);

template <class ExecutionPolicy, class ForwardIterator, class Size, class T>
ForwardIterator uninitialized_fill_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count,
    const T& value);
```

### <a name="parameters"></a>Parameter

*Richtlinien*\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein forward-Iterator, der das erste Element im Zielbereich adressiert, das initialisiert werden soll.

*Anzahl*\
Die Anzahl der zu initialisierenden Elemente.

*value*\
Der Wert, der zum Initialisieren des Zielbereichs verwendet werden soll.

### <a name="remarks"></a>Bemerkungen

Dieser Algorithmus ermöglicht die Entkopplung der Speicherbelegung von der Objekterstellung.

Die Vorlagenfunktion führt Folgendes aus:

```cpp
while (0 < count--)
    new (static_cast<void*>(&* first++))
        typename iterator_traits<ForwardIterator>::value_type(value);
return first;
```

es sei denn, der Code löst eine Ausnahme aus. In diesem Fall sind alle erstellten Objekte zerstört und die Ausnahme wird erneut ausgelöst.

Die Überladung mit einer Ausführungs Richtlinie ist neu in c++ 17.

### <a name="example"></a>Beispiel

```cpp
// memory_uninit_fill_n.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    // No default constructor
    Integer( int x ) : value( x ) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    const int N = 10;
    Integer value( 60 );
    Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
    uninitialized_fill_n( Array, N, value );  // C4996
    cout << "The uninitialized Array contains: ";
    for ( int i = 0; i < N; i++ )
        cout << Array[ i ].get() <<  " ";
}
```

## <a name="uninitialized_move"></a>uninitialized_move

Verschiebt Elemente aus einem Quellbereich in einen nicht initialisierten Zielspeicher Bereich.

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_move(
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_move(
    ExecutionPolicy&& policy,
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);
```

### <a name="parameters"></a>Parameter

*Richtlinien*\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein eingabeiterator, der das erste Element im Quellbereich adressiert, das verschoben werden soll.

*Letzter*\
Ein eingabeiterator, der ein Element hinter dem letzten Element im zu verschiebende Quellbereich adressiert.

*dest* -\
Der Anfang des Zielbereichs.

### <a name="remarks"></a>Bemerkungen

Die Version ohne Ausführungs Richtlinie ist praktisch identisch mit der folgenden:

```cpp
for (; first != last; (void)++dest, ++first)
    ::new (static_cast<void*>(addressof(*dest)))
        typename iterator_traits<ForwardIterator>::value_type(std::move(*first));
return dest;
```

Wenn eine Ausnahme ausgelöst wird, bleiben einige Objekte im Quellbereich möglicherweise in einem gültigen, aber nicht angegebenen Zustand. Zuvor erstellte Objekte werden in einer nicht angegebenen Reihenfolge zerstört.

Die Version mit einer Ausführungs Richtlinie hat dasselbe Ergebnis, wird aber entsprechend der angegebenen *Richtlinie*ausgeführt.

Diese Funktionen sind neu in c++ 17.

## <a name="uninitialized_move_n"></a>uninitialized_move_n

Verschiebt eine angegebene Anzahl von Elementen aus einem Quellbereich in einen nicht initialisierten Zielspeicher Bereich.

```cpp
template <class InputIterator, class Size, class ForwardIterator>
pair<InputIterator, ForwardIterator> uninitialized_move_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class Size, class ForwardIterator>
pair<InputIterator, ForwardIterator> uninitialized_move_n(
    ExecutionPolicy&& policy,
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>Parameter

*Richtlinien*\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein eingabeiterator, der das erste Element im Quellbereich adressiert, das verschoben werden soll.

*Anzahl*\
Die Anzahl der Elemente im zu verschiebenden Quellbereich.

*dest* -\
Der Anfang des Zielbereichs.

### <a name="remarks"></a>Bemerkungen

Die Version ohne Ausführungs Richtlinie ist praktisch identisch mit der folgenden:

```cpp
for (; count > 0; ++dest, (void) ++first, --count)
    ::new (static_cast<void*>(addressof(*dest)))
        typename iterator_traits<ForwardIterator>::value_type(std::move(*first));
return {first, dest};
```

Wenn eine Ausnahme ausgelöst wird, bleiben einige Objekte im Quellbereich möglicherweise in einem gültigen, aber nicht angegebenen Zustand. Zuvor erstellte Objekte werden in einer nicht angegebenen Reihenfolge zerstört.

Die Version mit einer Ausführungs Richtlinie hat dasselbe Ergebnis, wird aber entsprechend der angegebenen *Richtlinie*ausgeführt.

Diese Funktionen sind neu in c++ 17.

## <a name="uninitialized_value_construct"></a>uninitialized_value_construct

Erstellt Objekte der Iteratoren `value_type` nach Wert Initialisierung im angegebenen Bereich.

```cpp
template <class ForwardIterator>
void uninitialized_value_construct(
    ForwardIterator first,
    ForwardIterator last);

template <class ExecutionPolicy, class ForwardIterator>
void uninitialized_value_construct(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last);
```

### <a name="parameters"></a>Parameter

*Richtlinien*\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Iterator, der das erste Element im zu-Wert-Konstrukt adressiert.

*Letzter*\
Ein Iterator, der ein Element hinter dem letzten Element im "Range to Value"-Konstrukt adressiert.

### <a name="remarks"></a>Bemerkungen

Die Version ohne Ausführungs Richtlinie ist praktisch identisch mit der folgenden:

```cpp
for (; first != last; ++first)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type();
```

Wenn eine Ausnahme ausgelöst wird, werden zuvor erstellte Objekte in einer nicht angegebenen Reihenfolge zerstört.

Die Version mit einer Ausführungs Richtlinie hat dasselbe Ergebnis, wird aber entsprechend der angegebenen *Richtlinie*ausgeführt.

Wenn ein Fehler bei der Speicher Belegung auftritt, wird eine `std::bad_alloc` Ausnahme ausgelöst.

Diese Funktionen sind neu in c++ 17.

## <a name="uninitialized_value_construct_n"></a>uninitialized_value_construct_n

Erstellt eine angegebene Anzahl von Objekten des `value_type` des Iterators nach Wert Initialisierung, beginnend an der angegebenen Position.

```cpp
template <class ForwardIterator, class Size>
ForwardIterator uninitialized_value_construct_n(
    ForwardIterator first,
    Size count);

template <class ExecutionPolicy, class ForwardIterator, class Size>
ForwardIterator uninitialized_value_construct_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count);
```

### <a name="parameters"></a>Parameter

*Richtlinien*\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Iterator, der das erste Element im Zielbereich adressiert, der erstellt werden soll.

*Anzahl*\
Die Anzahl der Elemente im zu erstellenden Zielbereich.

### <a name="remarks"></a>Bemerkungen

Die Version ohne Ausführungs Richtlinie ist praktisch identisch mit der folgenden:

```cpp
for (; count > 0; (void)++first, --count)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type();
return first;
```

Wenn eine Ausnahme ausgelöst wird, werden zuvor erstellte Objekte in einer nicht angegebenen Reihenfolge zerstört.

Die Version mit einer Ausführungs Richtlinie hat dasselbe Ergebnis, wird aber entsprechend der angegebenen *Richtlinie*ausgeführt.

Wenn ein Fehler bei der Speicher Belegung auftritt, wird eine `std::bad_alloc` Ausnahme ausgelöst.

Diese Funktionen sind neu in c++ 17.

## <a name="uses_allocator_v"></a>uses_allocator_v

Eine hilfsvariablenvorlage für den Zugriff auf den Wert der `uses_allocator`-Vorlage.

```cpp
template <class T, class Alloc>
inline constexpr bool uses_allocator_v = uses_allocator<T, Alloc>::value;
```

## <a name="see-also"></a>Weitere Informationen

[\<memory>](memory.md)
