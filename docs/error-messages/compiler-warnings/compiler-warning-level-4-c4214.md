---
title: Compilerwarnung (Stufe 4) C4214
ms.date: 11/04/2016
f1_keywords:
- C4214
helpviewer_keywords:
- C4214
ms.assetid: 9b8db279-1f12-4a6b-a923-2db22acd1947
ms.openlocfilehash: 70dadb7d424352fbde8c5904053b22fe7cc6b77e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161281"
---
# <a name="compiler-warning-level-4-c4214"></a>Compilerwarnung (Stufe 4) C4214

nicht dem Standard entsprechende Erweiterung: bitfeldtypen außer int

Mit den standardmäßigen Microsoft-Erweiterungen (/Ze) können Bitfeld-Strukturmember einen beliebigen ganzzahligen Typ aufweisen.

## <a name="example"></a>Beispiel

```c
// C4214.c
// compile with: /W4
struct bitfields
{
   unsigned short j:4;  // C4214
};

int main()
{
}
```

Diese Bitfelder sind unter ANSI-Kompatibilität ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) ungültig.
