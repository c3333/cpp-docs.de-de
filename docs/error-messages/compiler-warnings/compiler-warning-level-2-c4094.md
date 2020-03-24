---
title: Compilerwarnung (Stufe 2) C4094
ms.date: 11/04/2016
f1_keywords:
- C4094
helpviewer_keywords:
- C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
ms.openlocfilehash: c90ad202e193f21955d396dd2aff6b39d3a968c7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174335"
---
# <a name="compiler-warning-level-2-c4094"></a>Compilerwarnung (Stufe 2) C4094

nicht markierte ' Token ' deklariert keine Symbole

Der Compiler hat eine leere Deklaration mit einer nicht markierten Struktur, Union oder Klasse erkannt. Die Deklaration wird ignoriert.

## <a name="example"></a>Beispiel

```cpp
// C4094.cpp
// compile with: /W2
struct
{
};   // C4094

int main()
{
}
```

Diese Bedingung generiert einen Fehler unter ANSI-Kompatibilität ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).
