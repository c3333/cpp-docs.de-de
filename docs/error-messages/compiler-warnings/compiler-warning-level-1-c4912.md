---
title: Compilerwarnung (Stufe 1) C4912
ms.date: 11/04/2016
f1_keywords:
- C4912
helpviewer_keywords:
- C4912
ms.assetid: ba1f1a66-8c20-4792-9ac8-43e49f729ae2
ms.openlocfilehash: dacde50fe10151d42110a30a699e1e772c8d8b45
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174686"
---
# <a name="compiler-warning-level-1-c4912"></a>Compilerwarnung (Stufe 1) C4912

'Attribut': Das Attribut besitzt ein nicht definiertes Verhalten für ein geschachteltes UDT.

Auf geschachtelte UDTs (benutzerdefinierter Typ, z. B. eine Typdefinition, Union oder Struktur) anwendbare Attribute werden möglicherweise ignoriert.

Der folgende Code zeigt, wie diese Warnung generiert werden würde:

```cpp
// C4912.cpp
// compile with: /W1
#include <windows.h>
[emitidl, module(name="xx")];

[object, uuid("00000000-0000-0000-0000-000000000002")]
__interface IMy
{
};

[coclass, default(IMy), appobject, uuid("00000000-0000-0000-0000-000000000001")]
class CMy : public IMy
{
   [export, v1_enum] typedef enum myEnum { k3_1 = 1, k3_2 = 2 } myEnumv;   // C4912
};
int main()
{
}
```
