---
title: weak_ptr-Klasse
ms.date: 07/29/2019
f1_keywords:
- memory/std::weak_ptr
- memory/std::weak_ptr::element_type
- memory/std::weak_ptr::expired
- memory/std::weak_ptr::lock
- memory/std::weak_ptr::owner_before
- memory/std::weak_ptr::reset
- memory/std::weak_ptr::swap
- memory/std::weak_ptr::use_count
- memory/std::weak_ptr::operator=
helpviewer_keywords:
- std::weak_ptr [C++]
- std::weak_ptr [C++], element_type
- std::weak_ptr [C++], expired
- std::weak_ptr [C++], lock
- std::weak_ptr [C++], owner_before
- std::weak_ptr [C++], reset
- std::weak_ptr [C++], swap
- std::weak_ptr [C++], use_count
- std::weak_ptr [C++], element_type
- std::weak_ptr [C++], expired
- std::weak_ptr [C++], lock
- std::weak_ptr [C++], owner_before
- std::weak_ptr [C++], reset
- std::weak_ptr [C++], swap
- std::weak_ptr [C++], use_count
ms.assetid: 2db4afb2-c7be-46fc-9c20-34ec2f8cc7c2
ms.openlocfilehash: 5a4989b9ac29e6a35e50479343d6bcf5a39ae1b0
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831735"
---
# <a name="weak_ptr-class"></a>weak_ptr-Klasse

Umschließt einen schwach verknüpften Zeiger.

## <a name="syntax"></a>Syntax

```cpp
template<class T> class weak_ptr;
```

### <a name="parameters"></a>Parameter

*Bund*\
Der vom schwachen Zeiger gesteuerte Typ.

## <a name="remarks"></a>Bemerkungen

In der Klassen Vorlage wird ein Objekt beschrieben, das auf eine Ressource verweist, die von einem oder mehreren [shared_ptr](shared-ptr-class.md) Objekten verwaltet wird. Die `weak_ptr` Objekte, die auf eine Ressource verweisen, wirken sich nicht auf den Verweis Zähler der Ressource aus. Wenn das letzte `shared_ptr` Objekt, das diese Ressource verwaltet, zerstört wird, wird die Ressource freigegeben, auch wenn Objekte vorhanden sind, die `weak_ptr` auf diese Ressource verweisen. Dieses Verhalten ist für die Vermeidung von Zyklen in Datenstrukturen von entscheidender Bedeutung.

Ein `weak_ptr`-Objekt verweist auf eine Ressource, wenn es aus einem `shared_ptr`-Objekt erstellt wurde, das diese Ressource besitzt, wenn es aus einem `weak_ptr`-Objekt erstellt wurde, das auf diese Ressource verweist, oder wenn ihm diese Ressource mit [operator=](#op_eq) zugewiesen wurde. Ein- `weak_ptr` Objekt stellt keinen direkten Zugriff auf die Ressource bereit, auf die es verweist. Code, der auf die Ressource zugreifen muss, erledigt dies über ein `shared_ptr`-Objekt, das diese Ressource besitzt, die durch Aufrufen der Memberfunktion [lock](#lock) erstellt wurde. Ein- `weak_ptr` Objekt ist abgelaufen, wenn die Ressource, auf die es verweist, freigegeben wurde, weil alle `shared_ptr` Objekte, die die Ressource besitzen, zerstört wurden. Ein Aufrufen von `lock` für ein `weak_ptr`-Objekt, das abgelaufen ist, erstellt ein leeres shared_ptr-Objekt.

Ein leeres weak_ptr Objekt verweist nicht auf Ressourcen und verfügt über keinen Kontroll Block. Ihre Memberfunktion `lock` gibt ein leeres shared_ptr-Objekt zurück.

Ein Zyklus tritt auf, wenn es für zwei oder mehr Ressourcen, die von `shared_ptr`-Objekten gesteuert werden, `shared_ptr`-Objekte gibt, die gegenseitig auf sich verweisen. Angenommen, eine kreisförmig verknüpfte Liste mit drei Elementen hat den Kopfknoten `N0`; dieser Knoten enthält ein `shared_ptr`-Objekt, das den nächsten Knoten, `N1`, besitzt; dieser Knoten enthält ein `shared_ptr`-Objekt, das den nächsten Knoten, `N2`, besitzt; dieser Knoten wiederum enthält ein `shared_ptr`-Objekt, das den Kopfknoten `N0` besitzt, wodurch der Zyklus geschlossen wird. In dieser Situation wird der Verweis Zähler niemals auf NULL gesetzt, und die Knoten im-Schleifen werden nie freigegeben. Um den Zyklus zu vermeiden, sollte der letzte Knoten, `N2`, anstelle eines `shared_ptr`-Objekts ein `weak_ptr`-Objekt enthalten, das auf `N0` verweist. Da das `weak_ptr` Objekt nicht Besitzer `N0` ist, wirkt sich dies nicht `N0` auf den Verweis Zähler aus, und wenn der letzte Verweis des Programms auf den Haupt Knoten zerstört wurde, werden auch die Knoten in der Liste zerstört.

## <a name="members"></a>Member

|Name|Beschreibung|
|-|-|
| **Konstruktoren** | |
|[weak_ptr](#weak_ptr)|Erstellt ein Objekt vom Typ `weak_ptr`.|
| **Destruktoren** | |
|[~ weak_ptr](#tilde-weak_ptr)|Erstellt ein Objekt vom Typ `weak_ptr`.|
| **Typedefs** | |
|[element_type](#element_type)|Der Typ des Elements.|
| **Member-Funktionen** | |
|[Frist](#expired)|Überprüft, ob der Besitz abgelaufen ist.|
|[lock](#lock)|Bedingt exklusiven Besitz einer Ressource.|
|[owner_before](#owner_before)|Gibt zurück, **`true`** Wenn dieser `weak_ptr` vor (oder kleiner als) dem bereitgestellten Zeiger geordnet ist.|
|[reset](#reset)|Gibt eine in Besitz befindliche Ressource frei.|
|[swap](#swap)|Tauscht zwei `weak_ptr`-Objekte.|
|[use_count](#use_count)|Zählt die Anzahl der `shared_ptr` Objekte.|
| **Operatoren** | |
|[Operator =](#op_eq)|Ersetzt eine in Besitz befindliche Ressource.|

## <a name="element_type"></a><a name="element_type"></a> element_type

Der Typ des Elements.

```cpp
typedef T element_type; // through C++17
using element_type = remove_extent_t<T>; // C++20
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `T` dar.

### <a name="example"></a>Beispiel

```cpp
// std__memory__weak_ptr_element_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));
    std::weak_ptr<int> wp0(sp0);
    std::weak_ptr<int>::element_type val = *wp0.lock();

    std::cout << "*wp0.lock() == " << val << std::endl;

    return (0);
}
```

```Output
*wp0.lock() == 5
```

## <a name="expired"></a><a name="expired"></a> Frist

Testet, ob der Besitz abgelaufen ist, d. h. das Objekt, auf das verwiesen wird, wurde gelöscht.

```cpp
bool expired() const noexcept;
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt zurück **`true`** **`*this`** , wenn abgelaufen ist; andernfalls **`false`** .

### <a name="example"></a>Beispiel

```cpp
// std__memory__weak_ptr_expired.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int(10));
        wp = sp;
        std::cout << "wp.expired() == " << std::boolalpha
            << wp.expired() << std::endl;
        std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    }

    // check expired after sp is destroyed
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;
    std::cout << "(bool)wp.lock() == " << std::boolalpha
        << (bool)wp.lock() << std::endl;

    return (0);
}
```

```Output
wp.expired() == false
*wp.lock() == 10
wp.expired() == true
(bool)wp.lock() == false
```

## <a name="lock"></a><a name="lock"></a> Sperre

Ruft ein ab `shared_ptr` , das den Besitz einer Ressource freigibt.

```cpp
shared_ptr<T> lock() const noexcept;
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt ein leeres [shared_ptr](shared-ptr-class.md) Objekt zurück, wenn **`*this`** abgelaufen ist. andernfalls wird ein-Objekt zurückgegeben `shared_ptr<T>` , das die Ressource besitzt, **`*this`** auf die verweist. Gibt einen Wert zurück, der der atomaren Ausführung von entspricht `expired() ? shared_ptr<T>() : shared_ptr<T>(*this)` .

### <a name="example"></a>Beispiel

```cpp
// std__memory__weak_ptr_lock.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int(10));
        wp = sp;
        std::cout << "wp.expired() == " << std::boolalpha
            << wp.expired() << std::endl;
        std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    }

    // check expired after sp is destroyed
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;
    std::cout << "(bool)wp.lock() == " << std::boolalpha
        << (bool)wp.lock() << std::endl;

    return (0);
}
```

```Output
wp.expired() == false
*wp.lock() == 10
wp.expired() == true
(bool)wp.lock() == false
```

## <a name="operator"></a><a name="op_eq"></a> Operator =

Ersetzt eine in Besitz befindliche Ressource.

```cpp
weak_ptr& operator=(const weak_ptr& ptr) noexcept;

template <class Other>
weak_ptr& operator=(const weak_ptr<Other>& ptr) noexcept;

template <class Other>
weak_ptr& operator=(const shared_ptr<Other>& ptr) noexcept;
```

### <a name="parameters"></a>Parameter

*Außer*\
Der Typ, der vom freigegebenen Argument oder schwachen Zeiger gesteuert wird.

*PTR*\
Der schwache Zeiger oder freigegebene Zeiger, der kopiert werden soll.

### <a name="remarks"></a>Bemerkungen

Die Operatoren geben alle die Ressource frei, auf die derzeit von verwiesen wird **`*this`** , und weisen den Besitz der Ressource, die von *ptr* benannt wird, **`*this`** Wenn ein Operator fehlschlägt, bleibt er **`*this`** unverändert. Jeder Operator hat einen Effekt, der entspricht `weak_ptr(ptr).swap(*this)` .

### <a name="example"></a>Beispiel

```cpp
// std__memory__weak_ptr_operator_as.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));
    std::weak_ptr<int> wp0(sp0);
    std::cout << "*wp0.lock() == " << *wp0.lock() << std::endl;

    std::shared_ptr<int> sp1(new int(10));
    wp0 = sp1;
    std::cout << "*wp0.lock() == " << *wp0.lock() << std::endl;

    std::weak_ptr<int> wp1;
    wp1 = wp0;
    std::cout << "*wp1.lock() == " << *wp1.lock() << std::endl;

    return (0);
}
```

```Output
*wp0.lock() == 5
*wp0.lock() == 10
*wp1.lock() == 10
```

## <a name="owner_before"></a><a name="owner_before"></a> owner_before

Gibt zurück, **`true`** Wenn dieser `weak_ptr` vor (oder kleiner als) dem bereitgestellten Zeiger geordnet ist.

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

Die Template-Member-Funktion gibt zurück, **`true`** Wenn **`*this`** vor *ptr*geordnet ist.

## <a name="reset"></a><a name="reset"></a> Festlegen

Gibt die eigene Ressource frei.

```cpp
void reset() noexcept;
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt die Ressource frei, auf die von verwiesen wird **`*this`** , und konvertiert **`*this`** in ein leeres- `weak_ptr` Objekt.

### <a name="example"></a>Beispiel

```cpp
// std__memory__weak_ptr_reset.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp(new int(5));
    std::weak_ptr<int> wp(sp);
    std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;

    wp.reset();
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;

    return (0);
}
```

```Output
*wp.lock() == 5
wp.expired() == false
wp.expired() == true
```

## <a name="swap"></a><a name="swap"></a> Wechsel

Tauscht zwei `weak_ptr`-Objekte.

```cpp
void swap(weak_ptr& wp) noexcept;
```

Umfasst auch die Spezialisierung:

```cpp
template<class T>
void swap(weak_ptr<T>& a, weak_ptr<T>& b) noexcept;
```

### <a name="parameters"></a>Parameter

*UA*\
Der schwache Zeiger, mit dem getauscht werden soll.

### <a name="remarks"></a>Bemerkungen

Nach einem verweist auf `swap` die Ressource, auf die ursprünglich von verwiesen **`*this`** wurde, durch *WP*, und auf die Ressource, auf die von *WP* ursprünglich verwiesen wird, wird von verwiesen **`*this`** . Die Funktion ändert nicht die Verweis Zähler für die beiden Ressourcen und löst keine Ausnahmen aus. Die Auswirkung der Vorlagen Spezialisierung ist die Entsprechung von `a.swap(b)` .

### <a name="example"></a>Beispiel

```cpp
// std__memory__weak_ptr_swap.cpp
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

## <a name="use_count"></a><a name="use_count"></a> use_count

Zählt die Anzahl der `shared_ptr` Objekte, die die freigegebene Ressource besitzen.

```cpp
long use_count() const noexcept;
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt die Anzahl der Objekte zurück, die Besitzer `shared_ptr` der Ressource sind, auf die von verwiesen wird **`*this`** .

### <a name="example"></a>Beispiel

```cpp
// std__memory__weak_ptr_use_count.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::weak_ptr<int> wp(sp1);
    std::cout << "wp.use_count() == "
        << wp.use_count() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "wp.use_count() == "
        << wp.use_count() << std::endl;

    return (0);
}
```

```Output
wp.use_count() == 1
wp.use_count() == 2
```

## <a name="weak_ptr"></a><a name="weak_ptr"></a> weak_ptr

Erstellt ein Objekt vom Typ `weak_ptr`.

```cpp
constexpr weak_ptr() noexcept;

weak_ptr(const weak_ptr& wp) noexcept;

weak_ptr(weak_ptr&& wp) noexcept;

template <class Other>
weak_ptr(const weak_ptr<Other>& wp) noexcept;

template <class Other>
weak_ptr(weak_ptr<Other>&& sp) noexcept;

template <class Other>
weak_ptr(const shared_ptr<Other>& sp) noexcept;
```

### <a name="parameters"></a>Parameter

*Außer*\
Der Typ, der vom Argument für den gemeinsamen/schwachen Zeiger gesteuert wird. Diese Konstruktoren sind nicht an der Überladungs Auflösung beteiligt, es sei denn, _andere \* _ `element_type*` ist mit kompatibel

*UA*\
Der zu kopierende schwache Zeiger.

*El*\
Der zu kopierende gemeinsame Zeiger

### <a name="remarks"></a>Bemerkungen

Der Standardkonstruktor erstellt ein leeres- `weak_ptr` Objekt. Die Konstruktoren, die ein Argument annehmen, erstellen ein leeres `weak_ptr` Objekt, wenn der Argument Zeiger leer ist. Andernfalls erstellen Sie ein- `weak_ptr` Objekt, das auf die Ressource verweist, die durch das-Argument benannt wird. Der Verweis Zähler des freigegebenen Objekts wird nicht geändert.

### <a name="example"></a>Beispiel

```cpp
// std__memory__weak_ptr_construct.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::weak_ptr<int> wp0;
    std::cout << "wp0.expired() == " << std::boolalpha
        << wp0.expired() << std::endl;

    std::shared_ptr<int> sp1(new int(5));
    std::weak_ptr<int> wp1(sp1);
    std::cout << "*wp1.lock() == "
        << *wp1.lock() << std::endl;

    std::weak_ptr<int> wp2(wp1);
    std::cout << "*wp2.lock() == "
        << *wp2.lock() << std::endl;

    return (0);
}
```

```Output
wp0.expired() == true
*wp1.lock() == 5
*wp2.lock() == 5
```

## <a name="weak_ptr"></a><a name="tilde-weak_ptr"></a> ~ weak_ptr

Beschädigt ein Objekt vom Typ `weak_ptr`.

```cpp
~weak_ptr();
```

### <a name="remarks"></a>Bemerkungen

Der Dekonstruktor zerstört dies, `weak_ptr` aber hat keine Auswirkung auf den Verweis Zähler des Objekts, auf dessen gespeicherter Zeiger zeigt.

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](cpp-standard-library-header-files.md)\
[\<memory>](memory.md)\
[shared_ptr-Klasse](shared-ptr-class.md)
