---
title: '&lt;type_traits&gt;-Funktionen'
ms.date: 11/04/2016
ms.assetid: dce4492f-f3e4-4d5e-bdb4-5875321254ec
helpviewer_keywords:
- std::is_assignable
- std::is_copy_assignable
- std::is_copy_constructible
- std::is_default_constructible
- std::is_move_assignable
- std::is_move_constructible
- std::is_nothrow_move_assignable
- std::is_trivially_copy_assignable
- std::is_trivially_move_assignable
- std::is_trivially_move_constructible
ms.openlocfilehash: 40ebd24a286039391dedacf289d305ee5ec9ca95
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447481"
---
# <a name="lttype_traitsgt-functions"></a>&lt;type_traits&gt;-Funktionen

||||
|-|-|-|
|[is_assignable](#is_assignable)|[is_copy_assignable](#is_copy_assignable)|[is_copy_constructible](#is_copy_constructible)|
|[is_default_constructible](#is_default_constructible)|[is_move_assignable](#is_move_assignable)|[is_move_constructible](#is_move_constructible)|
|[is_nothrow_move_assignable](#is_nothrow_move_assignable)|[is_nothrow_swappable](#is_nothrow_swappable)|[is_nothrow_swappable_with](#is_nothrow_swappable_with)|
|[is_swappable](#is_swappable)|[is_swappable_with](#is_swappable_with)|[is_trivially_copy_assignable](#is_trivially_copy_assignable)|
|[is_trivially_move_assignable](#is_trivially_move_assignable)|[is_trivially_move_constructible](#is_trivially_move_constructible)|

## <a name="is_assignable"></a> is_assignable

Testet, ob ein Wert *vom* Typ einem *zu* Typ zugewiesen werden kann.

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>Parameter

*Zum*\
Der Typ des Objekts, das die Zuweisung empfängt.

*Von*\
Der Typ des Objekts, das den Wert bereitstellt.

### <a name="remarks"></a>Bemerkungen

Der ausgewertete Ausdruck `declval<To>() = declval<From>()` muss wohlgeformt sein. Sowohl *von* als auch *bis* müssen komplette Typen, **void**oder Arrays mit unbekannter Grenze sein.

## <a name="is_copy_assignable"></a> is_copy_assignable

Testet, ob der Typ durch Zuweisung kopiert werden kann.

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>Parameter

*Ty* -\
Der abzufragende Typ.

### <a name="remarks"></a>Bemerkungen

Eine Instanz des typprädikats ist "true", wenn die *typität* eine Klasse ist, die einen Kopier Zuweisungs Operator aufweist; andernfalls "false". Entspricht is_assignable\<Ty&, const Ty&>.

## <a name="is_copy_constructible"></a> is_copy_constructible

Testet, ob der Typ einen Kopierkonstruktor aufweist.

```cpp
template <class Ty>
struct is_copy_constructible;
```

### <a name="parameters"></a>Parameter

*Ty* -\
Der abzufragende Typ.

### <a name="remarks"></a>Bemerkungen

Eine Instanz des typprädikats ist "true", wenn die *typty* eine Klasse ist, die einen Kopierkonstruktor aufweist; andernfalls "false".

### <a name="example"></a>Beispiel

```cpp
#include <type_traits>
#include <iostream>

struct Copyable
{
    int val;
};

struct NotCopyable
{
   NotCopyable(const NotCopyable&) = delete;
   int val;

};

int main()
{
    std::cout << "is_copy_constructible<Copyable> == " << std::boolalpha
        << std::is_copy_constructible<Copyable>::value << std::endl;
    std::cout << "is_copy_constructible<NotCopyable> == " << std::boolalpha
        << std::is_copy_constructible<NotCopyable>::value << std::endl;

    return (0);
}
```

```Output
is_copy_constructible<Copyable> == true
is_copy_constructible<NotCopyable > == false
```

## <a name="is_default_constructible"></a> is_default_constructible

Testet, ob ein Typ einen Standardkonstruktor besitzt.

```cpp
template <class Ty>
struct is_default_constructible;
```

### <a name="parameters"></a>Parameter

*T*\
Der abzufragende Typ.

### <a name="remarks"></a>Bemerkungen

Eine Instanz des typprädikats ist true, wenn der Typ *T* ein Klassentyp ist, der einen Standardkonstruktor aufweist; andernfalls false. Dies entspricht dem Prädikat `is_constructible<T>`. Der Typ " *T* " muss ein kompletter Typ, " **void**" oder ein Array mit unbekannter Grenze sein.

### <a name="example"></a>Beispiel

```cpp
#include <type_traits>
#include <iostream>

struct Simple
{
    Simple() : val(0) {}
    int val;
};

struct Simple2
{
    Simple2(int v) : val(v) {}
    int val;
};

int main()
{
    std::cout << "is_default_constructible<Simple> == " << std::boolalpha
        << std::is_default_constructible<Simple>::value << std::endl;
    std::cout << "is_default_constructible<Simple2> == " << std::boolalpha
        << std::is_default_constructible<Simple2>::value << std::endl;

    return (0);
}
```

```Output
is_default_constructible<Simple> == true
is_default_constructible<Simple2> == false
```

## <a name="is_move_assignable"></a> is_move_assignable

Prüft, ob dem Typ eine Verschiebung zugewiesen werden kann.

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>Parameter

*T*\
Der abzufragende Typ.

### <a name="remarks"></a>Bemerkungen

Einem Typ kann eine Verschiebung zugewiesen werden, wenn ein rvalue-Verweis auf den Typ einem Verweis auf den Typ zugewiesen werden kann. Das Typprädikat entspricht `is_assignable<T&, T&&>`. Verschieben von zuweisbaren Typen beinhaltet verweisbare skalare Typen und Klassentypen, die entweder vom Compiler generierte oder benutzerdefinierte Bewegungszuweisungsoperatoren haben.

## <a name="is_move_constructible"></a> is_move_constructible

Testet, ob der Typ über einen Bewegungskonstruktor verfügt.

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Parameter

*T*\
Der auszuwertende Typ.

### <a name="remarks"></a>Bemerkungen

Ein typprädikat, das zu true ausgewertet wird, wenn der Typ *T* mit einem Verschiebungs Vorgang erstellt werden kann. Das Prädikat entspricht `is_constructible<T, T&&>`.

## <a name="is_nothrow_move_assignable"></a> is_nothrow_move_assignable

Testet, ob der Typ einen **nothrow**-Bewegungszuweisungsoperator aufweist.

```cpp
template <class Ty>
struct is_nothrow_move_assignable;
```

### <a name="parameters"></a>Parameter

*Ty* -\
Der abzufragende Typ.

### <a name="remarks"></a>Bemerkungen

Eine Instanz des typprädikats ist "true", wenn die *typty* einen nothrow-Verschiebungs Zuweisungs Operator aufweist; andernfalls "false".

## <a name="is_nothrow_swappable"></a>is_nothrow_swappable

```cpp
template <class T> struct is_nothrow_swappable;
```

## <a name="is_nothrow_swappable_with"></a>is_nothrow_swappable_with

```cpp
template <class T, class U> struct is_nothrow_swappable_with;
```

## <a name="is_swappable"></a>is_swappable

```cpp
template <class T> struct is_swappable;
```

## <a name="is_swappable_with"></a>is_swappable_with

```cpp
template <class T, class U> struct is_swappable_with;
```

## <a name="is_trivially_copy_assignable"></a> is_trivially_copy_assignable

Testet, ob der Typ einen trivialen Kopierzuweisungsoperator aufweist.

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>Parameter

*T*\
Der abzufragende Typ.

### <a name="remarks"></a>Bemerkungen

Eine Instanz des typprädikats ist "true", wenn der Typ " *T* " eine Klasse ist, die einen trivialen Kopier Zuweisungs Operator aufweist; andernfalls "false".

Ein Zuweisungskonstruktor für eine Klasse *t* ist trivial, wenn er implizit bereitgestellt wird. die Klasse *t* verfügt über keine virtuellen Funktionen, die Klasse *t* verfügt über keine virtuellen Basen, die Klassen aller nicht statischen Datenmember des Klassen Typs haben triviale Zuweisungs Operatoren, und die Klassen aller nicht statischen Datenmember des Typarray der Klasse haben triviale Zuweisungs Operatoren.

## <a name="is_trivially_move_assignable"></a> is_trivially_move_assignable

Testet, ob der Typ einen trivialen Verschiebezuweisungsoperator aufweist.

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Parameter

*Ty* -\
Der abzufragende Typ.

### <a name="remarks"></a>Bemerkungen

Eine Instanz des typprädikats ist "true", wenn die *typität* eine Klasse ist, die einen trivialen Verschiebungs Zuweisungs Operator aufweist; andernfalls "false".

Ein Verschiebungs Zuweisungs Operator für eine Klassen- *Ty* ist in folgenden Fällen trivial:

Er wird impliziert bereitgestellt

die Klasse *Ty* hat keine virtuellen Funktionen.

die Klasse *Ty* hat keine virtuellen Basen.

Die Klassen aller nicht statischen Datenmember des Klassentyps haben triviale Verschiebungszuweisungsoperatoren

Die Klassen aller nicht statischen Datenmember des Typarrays der Klasse haben triviale Verschiebungszuweisungsoperatoren

## <a name="is_trivially_move_constructible"></a> is_trivially_move_constructible

Testet, ob der Typ einen trivialen Bewegungskonstruktor aufweist.

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Parameter

*Ty* -\
Der abzufragende Typ.

### <a name="remarks"></a>Bemerkungen

Eine Instanz des typprädikats ist true, wenn die *typität* eine Klasse ist, die einen trivialen bewegungskonstruktor aufweist; andernfalls false.

Ein bewegungskonstruktor für eine Klasse *Ty* ist in folgenden Fällen trivial:

Er wird implizit deklariert.

die Parametertypen entsprechen den einer impliziten Deklaration

die Klasse *Ty* hat keine virtuellen Funktionen.

die Klasse *Ty* hat keine virtuellen Basen.

die Klasse verfügt über keine flüchtigen nicht statischen Datenmember

alle direkten Basen der Klasse *Ty* verfügen über triviale bewegungskonstruktoren.

die Klassen aller nicht statischen Datenmember des Klassentyps haben triviale Bewegungskonstruktoren

die Klassen aller nicht statischen Datenmember vom Typarray der Klasse haben triviale Bewegungskonstruktoren

## <a name="see-also"></a>Weitere Informationen

[<type_traits>](../standard-library/type-traits.md)
