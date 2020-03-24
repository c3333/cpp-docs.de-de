---
title: __func__
ms.date: 10/19/2017
f1_keywords:
- __func__
ms.assetid: a5299b8d-f0ee-4af2-91dd-8fb165e68798
ms.openlocfilehash: 8e94caffe120c325478d8b4f24c1915a516d69f4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179821"
---
# <a name="__func__"></a>__func__

**(C++ 11)** Der vordefinierte &#95; &#95;bezeichnerfunc&#95; &#95; ist implizit als Zeichenfolge definiert, die den nicht qualifizierten und undekorierten Namen der einschließenden Funktion enthält. &#95;&#95;Func&#95; &#95; wird vom C++ Standard vorgeschrieben und ist keine Microsoft-Erweiterung.

## <a name="syntax"></a>Syntax

```cpp
__func__
```

## <a name="return-value"></a>Rückgabewert

Gibt ein mit Null endendes Konstanten Zeichen Array mit Zeichen zurück, das den Funktionsnamen enthält.

## <a name="example"></a>Beispiel

```cpp
#include <string>
#include <iostream>

namespace Test
{
    struct Foo
    {
        static void DoSomething(int i, std::string s)
        {
           std::cout << __func__ << std::endl; // Output: DoSomething
        }
    };
}

int main()
{
    Test::Foo::DoSomething(42, "Hello");

    return 0;
}
```

## <a name="requirements"></a>Requirements (Anforderungen)

C++11
