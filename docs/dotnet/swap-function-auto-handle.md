---
title: swap-Funktion (auto_handle)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- swap function
ms.assetid: 7dd91b5c-f0de-4634-a2e2-642626706e27
ms.openlocfilehash: ed0e4ab7bce52d4dee54e7f9149edae535445d65
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91498583"
---
# <a name="swap-function-auto_handle"></a>swap-Funktion (auto_handle)

Vertauscht Objekte zwischen einem `auto_handle` und einem anderen.

## <a name="syntax"></a>Syntax

```
template<typename _element_type>
void swap(
   auto_handle<_element_type> % _left,
   auto_handle<_element_type> % _right
);
```

#### <a name="parameters"></a>Parameter

*_left*<br/>
Eine `auto_handle`.

*_right*<br/>
Eine andere `auto_handle`.

## <a name="example"></a>Beispiel

```cpp
// msl_swap_auto_handle.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

int main() {
   auto_handle<String> s1 = "string one";
   auto_handle<String> s2 = "string two";

   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",
      s1->ToString(), s2->ToString() );
   swap( s1, s2 );
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",
      s1->ToString(), s2->ToString() );
}
```

```Output
s1 = 'string one', s2 = 'string two'
s1 = 'string two', s2 = 'string one'
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Headerdatei** \<msclr\auto_handle.h>

**Namespace** -msclr

## <a name="see-also"></a>Weitere Informationen

[auto_handle](../dotnet/auto-handle.md)<br/>
[auto_handle::swap](./auto-handle-class.md#swap)
