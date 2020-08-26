---
title: reference_wrapper-Klasse
ms.date: 11/04/2016
f1_keywords:
- functional/std::reference_wrapper
- type_traits/std::reference_wrapper
- xrefwrap/std::reference_wrapper
- type_traits/std::reference_wrapper::get
- type_traits/std::reference_wrapper::operator()
- functional/std::reference_wrapper::result_type
- functional/std::reference_wrapper::type
- functional/std::reference_wrapper::get
- functional/std::reference_wrapper::operator()
helpviewer_keywords:
- std::reference_wrapper [C++]
- std::reference_wrapper [C++]
- std::reference_wrapper [C++], result_type
- std::reference_wrapper [C++], type
- std::reference_wrapper [C++], get
ms.assetid: 90b8ed62-e6f1-44ed-acc7-9619bd58865a
ms.openlocfilehash: 623e1480bdec85120e504c8dc71b28d017c8872a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845067"
---
# <a name="reference_wrapper-class"></a>reference_wrapper-Klasse

Umschließt einen Verweis.

## <a name="syntax"></a>Syntax

```cpp
template <class Ty>
class reference_wrapper
{
    typedef Ty type;

    reference_wrapper(Ty&) noexcept;
    operator Ty&() const noexcept;
    Ty& get() const noexcept;

    template <class... Types>
    auto operator()(Types&&... args) const ->
        decltype(std::invoke(get(), std::forward<Types>(args)...));
};
```

## <a name="remarks"></a>Bemerkungen

Ein `reference_wrapper<Ty>`-Wrapper kann um einen Verweis auf ein Objekt oder eine Funktion des Typs `Ty` über eine Kopie erstellt und zugewiesen werden und enthält einen Zeiger, der auf ein Objekt dieses Typs zeigt. Ein `reference_wrapper` kann zum Speichern von Verweisen in Standardcontainern und zum Übergeben von Objekten durch einen Verweis auf `std::bind` verwendet werden.

Der `Ty`-Typ muss ein Objekttyp oder Funktionstyp sein, oder eine statische Assertion kann nicht zum Zeitpunkt der Kompilierung ausgeführt werden.

Die Hilfsfunktionen [std::ref](functional-functions.md#ref) und [std::cref](functional-functions.md#cref) dienen zum Erstellen von `reference_wrapper`-Objekten.

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

|Name|Beschreibung|
|-|-|
|[reference_wrapper](#reference_wrapper)|Erstellt ein Objekt vom Typ `reference_wrapper`.|

### <a name="typedefs"></a>TypeDefs

|Name|Beschreibung|
|-|-|
|[result_type](#result_type)|Der schwache Ergebnistyp des umschlossenen Verweises.|
|[type](#type)|Der Typ des umschlossenen Verweises.|

### <a name="functions"></a>Functions

|Name|Beschreibung|
|-|-|
|[get](#get)|Ruft den umschlossenen Verweis ab.|

### <a name="operators"></a>Operatoren

|Name|Beschreibung|
|-|-|
|[Operator Ty&amp;](#op_ty_amp)|Ruft einen Zeiger auf den umschlossenen Verweis ab.|
|[Operator ()](#op_call)|Ruft den umschlossenen Verweis auf.|

## <a name="get"></a><a name="get"></a> Erhalten

Ruft den umschlossenen Verweis ab.

```cpp
Ty& get() const noexcept;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt den umschlossenen Verweis zurück.

### <a name="example"></a>Beispiel

```cpp
// std__functional__reference_wrapper_get.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int main() {
    int i = 1;
    std::reference_wrapper<int> rwi(i);

    std::cout << "i = " << i << std::endl;
    std::cout << "rwi = " << rwi << std::endl;
    rwi.get() = -1;
    std::cout << "i = " << i << std::endl;

    return (0);
}
```

```Output
i = 1
rwi = 1
i = -1
```

## <a name="operator-tyamp"></a><a name="op_ty_amp"></a> Operator Ty&amp;

Ruft den umschlossenen Verweis auf.

```cpp
operator Ty&() const noexcept;
```

### <a name="remarks"></a>Bemerkungen

Der Memberoperator gibt `*ptr`zurück.

### <a name="example"></a>Beispiel

```cpp
// std__functional__reference_wrapper_operator_cast.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int main() {
    int i = 1;
    std::reference_wrapper<int> rwi(i);

    std::cout << "i = " << i << std::endl;
    std::cout << "(int)rwi = " << (int)rwi << std::endl;

    return (0);
}
```

```Output
i = 1
(int)rwi = 1
```

## <a name="operator"></a><a name="op_call"></a> Operator ()

Ruft den umschlossenen Verweis auf.

```cpp
template <class... Types>
auto operator()(Types&&... args);
```

### <a name="parameters"></a>Parameter

*Solche*\
Die Argumentlisttypen.

*args*\
Die Argumentliste.

### <a name="remarks"></a>Bemerkungen

Das Vorlagenmember `operator()` gibt `std::invoke(get(), std::forward<Types>(args)...)` zurück.

### <a name="example"></a>Beispiel

```cpp
// std__functional__reference_wrapper_operator_call.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val) {
    return (-val);
}

int main() {
    std::reference_wrapper<int (int)> rwi(neg);

    std::cout << "rwi(3) = " << rwi(3) << std::endl;

    return (0);
}
```

```Output
rwi(3) = -3
```

## <a name="reference_wrapper"></a><a name="reference_wrapper"></a> reference_wrapper

Erstellt ein Objekt vom Typ `reference_wrapper`.

```cpp
reference_wrapper(Ty& val) noexcept;
```

### <a name="parameters"></a>Parameter

*Genossenschaft*\
Der zu umschließende Typ.

*ster*\
Der zu umschließende Wert.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor legt den gespeicherten Wert `ptr` auf `&val` fest.

### <a name="example"></a>Beispiel

```cpp
// std__functional__reference_wrapper_reference_wrapper.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val) {
    return (-val);
}

int main() {
    int i = 1;
    std::reference_wrapper<int> rwi(i);

    std::cout << "i = " << i << std::endl;
    std::cout << "rwi = " << rwi << std::endl;
    rwi.get() = -1;
    std::cout << "i = " << i << std::endl;

    return (0);
}
```

```Output
i = 1
rwi = 1
i = -1
```

## <a name="result_type"></a><a name="result_type"></a> result_type

Der schwache Ergebnistyp des umschlossenen Verweises.

```cpp
typedef R result_type;
```

### <a name="remarks"></a>Bemerkungen

Die `result_type`-Typedefinition ist ein Synonym für den schwachen Ergebnistyp einer umschlossenen Funktion. Diese Typdefinition gilt nur für Funktionstypen.

### <a name="example"></a>Beispiel

```cpp
// std__functional__reference_wrapper_result_type.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val) {
    return (-val);
}

int main() {
    typedef std::reference_wrapper<int (int)> Mywrapper;
    Mywrapper rwi(neg);
    Mywrapper::result_type val = rwi(3);

    std::cout << "val = " << val << std::endl;

    return (0);
}
```

```Output
val = -3
```

## <a name="type"></a><a name="type"></a>-Typ

Der Typ des umschlossenen Verweises.

```cpp
typedef Ty type;
```

### <a name="remarks"></a>Bemerkungen

Die Typedef stellt ein Synonym für das Vorlagenargument `Ty`dar.

### <a name="example"></a>Beispiel

```cpp
// std__functional__reference_wrapper_type.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val) {
    return (-val);
}

int main() {
    int i = 1;
    typedef std::reference_wrapper<int> Mywrapper;
    Mywrapper rwi(i);
    Mywrapper::type val = rwi.get();

    std::cout << "i = " << i << std::endl;
    std::cout << "rwi = " << val << std::endl;

    return (0);
}
```

```Output
i = 1
rwi = 1
```
