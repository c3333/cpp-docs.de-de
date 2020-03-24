---
title: Compilerwarnung (Stufe 1) C4138
ms.date: 11/04/2016
f1_keywords:
- C4138
helpviewer_keywords:
- C4138
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
ms.openlocfilehash: e1f28f5afb1879229ff0d408cb576312966e1c81
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200108"
---
# <a name="compiler-warning-level-1-c4138"></a>Compilerwarnung (Stufe 1) C4138

"*/" wurde außerhalb des Kommentars gefunden

Dem schließenden Kommentartrennzeichen geht kein öffnendes Kommentartrennzeichen voran. Der Compiler nimmt an, dass zwischen dem Sternchen (<strong>\*</strong>) und dem Schrägstrich (/) ein Leerzeichen steht.

## <a name="example"></a>Beispiel

```cpp
// C4138a.cpp
// compile with: /W1
int */*comment*/ptr;   // C4138 Ambiguous first delimiter causes warning
int main()
{
}
```

Diese Warnung kann auf den Versuch zurückzuführen sein, Kommentare zu schachteln.

Die Warnung kann behoben werden, wenn Sie Codeabschnitte, die Kommentare enthalten, auskommentieren, den Code in einen **#if/#endif** -Block einschließen und den steuernden Ausdruck auf 0 (null) festlegen:

```cpp
// C4138b.cpp
// compile with: /W1
#if 0
int my_variable;   /* Declaration currently not needed */
#endif
int main()
{
}
```
