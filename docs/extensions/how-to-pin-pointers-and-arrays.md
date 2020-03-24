---
title: 'Gewusst wie: Anheften von Zeigern und Arrays'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- pointers, pinning
- arrays [C++], pinning
ms.assetid: ee783260-e676-46b8-a38e-11a06f1d57b0
ms.openlocfilehash: 8dc42690f0f56b97b2af3ed54dfb17d49b081695
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172216"
---
# <a name="how-to-pin-pointers-and-arrays"></a>Gewusst wie: Anheften von Zeigern und Arrays

Das Anheften eines untergeordneten Objekts, das in einem verwalteten Objekt definiert ist, hat den gleichen Effekt wie das Anheften des gesamten Objekts.  Wenn z.B. ein Element eines Arrays angeheftet wird, wird auch das gesamte Array angeheftet. Es gibt keine Erweiterungen für die Sprache zum Deklarieren eines angehefteten Arrays. Um ein Array anzuheften, deklarieren Sie einen festen Zeiger für dessen Elementtyp, und heften Sie eines seiner Elemente an.

## <a name="example"></a>Beispiel

### <a name="code"></a>Code

```cpp
// pin_ptr_array.cpp
// compile with: /clr
#include <stdio.h>
using namespace System;

int main() {
   array<Byte>^ arr = gcnew array<Byte>(4);
   arr[0] = 'C';
   arr[1] = '+';
   arr[2] = '+';
   arr[3] = '\0';
   pin_ptr<Byte> p = &arr[1];   // entire array is now pinned
   unsigned char * cp = p;

   printf_s("%s\n", cp); // bytes pointed at by cp
                         // will not move during call
}
```

```Output
++
```

## <a name="see-also"></a>Weitere Informationen

[pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)
