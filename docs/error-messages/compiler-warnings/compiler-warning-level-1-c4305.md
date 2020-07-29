---
title: Compilerwarnung (Stufe 1) C4305
ms.date: 01/17/2018
f1_keywords:
- C4305
helpviewer_keywords:
- C4305
ms.openlocfilehash: 567442bc48487e4f7d1f905f871d15f913646e87
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233287"
---
# <a name="compiler-warning-level-1-c4305"></a>Compilerwarnung (Stufe 1) C4305

> '*context*': Abschneiden von '*Typ1*' zu '*Typ2*'

## <a name="remarks"></a>Bemerkungen

Diese Warnung wird ausgegeben, wenn ein Wert in einer Initialisierung oder als Konstruktorargument in einen kleineren Typ konvertiert wird, was zu einem Verlust von Informationen führt.

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt zwei Möglichkeiten, wie Sie diese Warnung sehen können:

```cpp
// C4305.cpp
// Compile by using: cl /EHsc /W4 C4305.cpp

struct item
{
    item(float) {}
};

int main()
{
    float f = 2.71828;          // C4305 'initializing'
    item i(3.14159);            // C4305 'argument'
    return static_cast<int>(f);
}
```

Um dieses Problem zu beheben, initialisieren Sie mit einem Wert des richtigen Typs, oder verwenden Sie eine explizite Umwandlung in den richtigen Typ. Verwenden Sie z. b. ein **`float`** Literalzeichen, z. b. 2.71828 f anstelle von a **`double`** (der Standardtyp für Gleit Komma Literale), um eine Variable zu initialisieren **`float`** , oder um Sie an einen Konstruktor zu übergeben, der ein- **`float`** Argument annimmt
