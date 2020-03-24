---
title: _bstr_t::Assign
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::Assign
helpviewer_keywords:
- Assign method [C++]
ms.assetid: 2e209bbe-77ca-4598-86d5-6c2ea213f43c
ms.openlocfilehash: 09af33f4ed246c459d5c78d8d23d5316ad9c07c6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190641"
---
# <a name="_bstr_tassign"></a>_bstr_t::Assign

**Microsoft-spezifisch**

Kopiert eine `BSTR` in die von einem **_** -`bstr_t`umschließende `BSTR`.

## <a name="syntax"></a>Syntax

```
void Assign(
   BSTR s
);
```

#### <a name="parameters"></a>Parameter

*s*<br/>
Eine `BSTR`, das von einem `BSTR` umschlossen in `_bstr_t` kopiert werden soll.

## <a name="remarks"></a>Bemerkungen

**Assign** führt eine binäre Kopie aus. Dies bedeutet, dass die gesamte Länge des `BSTR` unabhängig vom Inhalt kopiert wird.

## <a name="example"></a>Beispiel

```cpp
// _bstr_t_Assign.cpp

#include <comdef.h>
#include <stdio.h>

int main()
{
    // creates a _bstr_t wrapper
    _bstr_t bstrWrapper;

    // creates BSTR and attaches to it
    bstrWrapper = "some text";
    wprintf_s(L"bstrWrapper = %s\n",
              static_cast<wchar_t*>(bstrWrapper));

    // bstrWrapper releases its BSTR
    BSTR bstr = bstrWrapper.Detach();
    wprintf_s(L"bstrWrapper = %s\n",
              static_cast<wchar_t*>(bstrWrapper));
    // "some text"
    wprintf_s(L"bstr = %s\n", bstr);

    bstrWrapper.Attach(SysAllocString(OLESTR("SysAllocedString")));
    wprintf_s(L"bstrWrapper = %s\n",
              static_cast<wchar_t*>(bstrWrapper));

    // assign a BSTR to our _bstr_t
    bstrWrapper.Assign(bstr);
    wprintf_s(L"bstrWrapper = %s\n",
              static_cast<wchar_t*>(bstrWrapper));

    // done with BSTR, do manual cleanup
    SysFreeString(bstr);

    // resuse bstr
    bstr= SysAllocString(OLESTR("Yet another string"));
    // two wrappers, one BSTR
    _bstr_t bstrWrapper2 = bstrWrapper;

    *bstrWrapper.GetAddress() = bstr;

    // bstrWrapper and bstrWrapper2 do still point to BSTR
    bstr = 0;
    wprintf_s(L"bstrWrapper = %s\n",
              static_cast<wchar_t*>(bstrWrapper));
    wprintf_s(L"bstrWrapper2 = %s\n",
              static_cast<wchar_t*>(bstrWrapper2));

    // new value into BSTR
    _snwprintf_s(bstrWrapper.GetBSTR(), 100, bstrWrapper.length(),
                 L"changing BSTR");
    wprintf_s(L"bstrWrapper = %s\n",
              static_cast<wchar_t*>(bstrWrapper));
    wprintf_s(L"bstrWrapper2 = %s\n",
              static_cast<wchar_t*>(bstrWrapper2));
}
```

```Output
bstrWrapper = some text
bstrWrapper = (null)
bstr = some text
bstrWrapper = SysAllocedString
bstrWrapper = some text
bstrWrapper = Yet another string
bstrWrapper2 = some text
bstrWrapper = changing BSTR
bstrWrapper2 = some text
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_bstr_t-Klasse](../cpp/bstr-t-class.md)
