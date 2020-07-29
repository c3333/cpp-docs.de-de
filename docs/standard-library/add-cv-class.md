---
title: add_cv-Klasse
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_cv
helpviewer_keywords:
- add_cv class
- add_cv
ms.assetid: a5572c78-a097-45d7-b476-ed4876889dea
ms.openlocfilehash: 0afeea71daf8358b2aeeefe8d368c135a54a6ad6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222627"
---
# <a name="add_cv-class"></a>add_cv-Klasse

Macht den **`const volatile`** Typ aus dem Typ.

## <a name="syntax"></a>Syntax

```cpp
template <class T>
struct add_cv;

template <class T>
using add_cv_t = typename add_cv<T>::type;
```

### <a name="parameters"></a>Parameter

*Bund*\
Der zu ändernde Typ.

## <a name="remarks"></a>Bemerkungen

Eine Instanz des geänderten Typs `add_cv<T>` weist ein Element `type` auf, das **`typedef`** von [add_volatile](add-volatile-class.md) und [add_const](add-const-class.md)geändert wird, es sei denn, *T* verfügt bereits über die CV-Qualifizierer, ist ein Verweis oder eine Funktion. *T*

Das `add_cv_t<T>`-Hilfsprogramm ist eine Verknüpfung für den Zugriff auf den `add_cv<T>`typedef-Member`type`.

## <a name="example"></a>Beispiel

```cpp
// add_cv.cpp
// compile by using: cl /EHsc /W4 add_cv.cpp
#include <type_traits>
#include <iostream>

struct S {
    void f() {
        std::cout << "invoked non-cv-qualified S.f()" << std::endl;
    }
    void f() const {
        std::cout << "invoked const S.f()" << std::endl;
    }
    void f() volatile {
        std::cout << "invoked volatile S.f()" << std::endl;
    }
    void f() const volatile {
        std::cout << "invoked const volatile S.f()" << std::endl;
    }
};

template <class T>
void invoke() {
    T t;
    ((T *)&t)->f();
}

int main()
{
    invoke<S>();
    invoke<std::add_const<S>::type>();
    invoke<std::add_volatile<S>::type>();
    invoke<std::add_cv<S>::type>();
}
```

```Output
invoked non-cv-qualified S.f()
invoked const S.f()
invoked volatile S.f()
invoked const volatile S.f()
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<type_traits>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[<type_traits>](type-traits.md)\
[remove_const-Klasse](remove-const-class.md)\
[remove_volatile-Klasse](remove-volatile-class.md)
