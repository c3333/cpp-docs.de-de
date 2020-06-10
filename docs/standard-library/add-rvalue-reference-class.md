---
title: add_rvalue_reference-Klasse
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_rvalue_reference
helpviewer_keywords:
- add_rvalue_reference Class
ms.assetid: 76b0cb7c-1031-45d0-b409-f03ab0297580
ms.openlocfilehash: 6d7cc1d45ed3b963de0a0a004c1696ddbf0af440
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623921"
---
# <a name="add_rvalue_reference-class"></a>add_rvalue_reference-Klasse

Erstellt einen rvalue-Verweistyp des Vorlagenparameters, wenn es sich dabei um einen Objekt- oder Funktionstyp handelt. Ansonsten ist der Typ aufgrund der Semantik der Verweisreduzierung der Gleiche wie der Vorlagenparameter.

## <a name="syntax"></a>Syntax

```cpp
template <class T>
struct add_rvalue_reference;

template <class T>
using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;
```

### <a name="parameters"></a>Parameter

*Bund*\
Der zu ändernde Typ.

## <a name="remarks"></a>Hinweise

Die- `add_rvalue_reference` Klasse verfügt über einen Member mit dem Namen `type` , bei dem es sich um einen Alias für den Typ eines Rvalue-Verweises auf den Vorlagen Parameter *T*handelt. Die Semantik der Verweis Reduzierung impliziert, dass für nicht-Objekt-und nicht-Funktions *T*Typen t `T&&` ein *t*ist. Wenn *T* beispielsweise ein Lvalue-Verweistyp ist, `add_rvalue_reference<T>::type` ist der lvalue-Verweistyp und kein rvalue-Verweis.

Aus Gründen der praktische Definition \<type_traits> definiert eine hilfsvorlage, `add_rvalue_reference_t` die das-Element von Aliase Alias `type` `add_rvalue_reference` .

## <a name="example"></a>Beispiel

Dieses Codebeispiel verwendet static_assert, um anzuzeigen, wie rvalue-Verweistypen mithilfe von `add_rvalue_reference` und `add_rvalue_reference_t` erstellt werden, und wie das Ergebnis von `add_rvalue_reference` eines rvalue-Verweistyps kein rvalue-Verweis ist, sondern auf einen lvalue-Typ reduziert wird.

```cpp
// ex_add_rvalue_reference.cpp
// Build by using: cl /EHsc /W4 ex_add_rvalue_reference.cpp
#include <type_traits>
#include <iostream>
#include <string>

using namespace std;
int main()
{
    static_assert(is_same<add_rvalue_reference<string>::type, string&&>::value,
        "Expected add_rvalue_reference_t<string> to be string&&");
    static_assert(is_same<add_rvalue_reference_t<string*>, string*&&>::value,
        "Expected add_rvalue_reference_t<string*> to be string*&&");
    static_assert(is_same<add_rvalue_reference<string&>::type, string&>::value,
        "Expected add_rvalue_reference_t<string&> to be string&");
    static_assert(is_same<add_rvalue_reference_t<string&&>, string&&>::value,
        "Expected add_rvalue_reference_t<string&&> to be string&&");
    cout << "All static_assert tests of add_rvalue_reference passed." << endl;
    return 0;
}

/*Output:
All static_assert tests of add_rvalue_reference passed.
*/
```

## <a name="requirements"></a>Requirements (Anforderungen)

Header: \<type_traits>

Namespace: std

## <a name="see-also"></a>Siehe auch

[<type_traits>](type-traits.md)\
[add_lvalue_reference-Klasse](add-lvalue-reference-class.md)\
[is_rvalue_reference-Klasse](is-rvalue-reference-class.md)
