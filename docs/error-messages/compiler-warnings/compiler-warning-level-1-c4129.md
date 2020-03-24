---
title: Compilerwarnung (Stufe 1) C4129
ms.date: 11/04/2016
f1_keywords:
- C4129
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
ms.openlocfilehash: 1a48fc806f3274a59c99be25ac7a0e7b03a0454b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176220"
---
# <a name="compiler-warning-level-1-c4129"></a>Compilerwarnung (Stufe 1) C4129

' character ': nicht erkannte Escapesequenz für Zeichen

Die `character`, die auf einen umgekehrten Schrägstrich (\\) in einer Zeichen-oder Zeichen folgen Konstante folgt, werden nicht als gültige Escapesequenz erkannt. Der umgekehrte Schrägstrich wird ignoriert und nicht gedruckt. Das Zeichen, das dem umgekehrten Schrägstrich folgt, wird gedruckt.

Geben Sie einen doppelten umgekehrten Schrägstrich (\\\\) an, um einen einzelnen umgekehrten Schrägstrich zu drucken.

Der C++ Standard im Abschnitt 2.13.2 erläutert Escapesequenzen.

Im folgenden Beispiel wird C4129 generiert:

```cpp
// C4129.cpp
// compile with: /W1
int main() {
   char array1[] = "\/709";   // C4129
   char array2[] = "\n709";   // OK
}
```
