---
title: Compilerwarnung (Stufe 1) C4218
ms.date: 11/04/2016
f1_keywords:
- C4218
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
ms.openlocfilehash: f7553b30a17f50f559351353552fd656fceb8657
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199796"
---
# <a name="compiler-warning-level-1-c4218"></a>Compilerwarnung (Stufe 1) C4218

nicht dem Standard entsprechende Erweiterung: Es muss mindestens eine Speicher Klasse oder ein Typ angegeben werden.

Mit den standardmäßigen Microsoft-Erweiterungen (/Ze) können Sie eine Variable deklarieren, ohne einen Typ oder eine Speicher Klasse anzugeben. Der Standardtyp ist `int`.

## <a name="example"></a>Beispiel

```cpp
// C4218.c
// compile with: /W4
i;  // C4218

int main()
{
}
```

Diese Deklarationen sind unter ANSI-Kompatibilität ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) ungültig.
