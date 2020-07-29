---
title: __interface
ms.date: 05/07/2019
f1_keywords:
- __interface_cpp
helpviewer_keywords:
- __interface keyword [C++]
ms.assetid: ca5d400b-d6d8-4ba2-89af-73f67e5ec056
ms.openlocfilehash: 9ca13ed91601fa3a64071304c14d483e84c314a3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233716"
---
# <a name="__interface"></a>__interface

**Microsoft-spezifisch**

Eine Microsoft C++-Schnittstelle kann wie folgt definiert werden:

- Kann von null oder mehreren Basisschnittstellen erben.

- Kann nicht von einer Basisklasse erben.

- Kann nur öffentliche, rein virtuelle Methoden enthalten.

- Kann keine Konstruktoren, Destruktoren oder Operatoren enthalten.

- Kann keine statischen Methoden enthalten.

- Kann keine Datenmember enthalten. Eigenschaften sind zulässig.

## <a name="syntax"></a>Syntax

```
modifier __interface interface-name {interface-definition};
```

## <a name="remarks"></a>Bemerkungen

Eine C++- [Klasse](../cpp/class-cpp.md) oder- [Struktur](../cpp/struct-cpp.md) kann mit diesen Regeln implementiert werden, setzt Sie aber durch **`__interface`** .

Im Folgenden ist eine Beispiel-Schnittstellendefinition angegeben:

```cpp
__interface IMyInterface {
   HRESULT CommitX();
   HRESULT get_X(BSTR* pbstrName);
};
```

Informationen zu verwalteten Schnittstellen finden Sie unter [Interface-Klasse](../extensions/interface-class-cpp-component-extensions.md).

Sie müssen nicht explizit angeben, dass die `CommitX`- und `get_X`-Funktionen rein virtuell sind. Eine entsprechende Deklaration für die erste Funktion wäre:

```cpp
virtual HRESULT CommitX() = 0;
```

**`__interface`** impliziert den [novtable](../cpp/novtable.md) - **`__declspec`** Modifizierer.

## <a name="example"></a>Beispiel

Die folgenden Beispiele zeigen, wie die in einer Schnittstelle deklarierten Eigenschaften verwendet werden.

```cpp
// deriv_interface.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include <string.h>
#include <comdef.h>
#include <stdio.h>

[module(name="test")];

[ object, uuid("00000000-0000-0000-0000-000000000001"), library_block ]
__interface IFace {
   [ id(0) ] int int_data;
   [ id(5) ] BSTR bstr_data;
};

[ coclass, uuid("00000000-0000-0000-0000-000000000002") ]
class MyClass : public IFace {
private:
    int m_i;
    BSTR m_bstr;

public:
    MyClass()
    {
        m_i = 0;
        m_bstr = 0;
    }

    ~MyClass()
    {
        if (m_bstr)
            ::SysFreeString(m_bstr);
    }

    int get_int_data()
    {
        return m_i;
    }

    void put_int_data(int _i)
    {
        m_i = _i;
    }

    BSTR get_bstr_data()
    {
        BSTR bstr = ::SysAllocString(m_bstr);
        return bstr;
    }

    void put_bstr_data(BSTR bstr)
    {
        if (m_bstr)
            ::SysFreeString(m_bstr);
        m_bstr = ::SysAllocString(bstr);
    }
};

int main()
{
    _bstr_t bstr("Testing");
    CoInitialize(NULL);
    CComObject<MyClass>* p;
    CComObject<MyClass>::CreateInstance(&p);
    p->int_data = 100;
    printf_s("p->int_data = %d\n", p->int_data);
    p->bstr_data = bstr;
    printf_s("bstr_data = %S\n", p->bstr_data);
}
```

```Output
p->int_data = 100
bstr_data = Testing
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[Schnittstellen Attribute](../windows/attributes/interface-attributes.md)
