---
title: Einfache Zuweisung (C)
ms.date: 11/04/2016
helpviewer_keywords:
- type conversion [C++], simple assignment
- data type conversion [C++], simple assignment
- operators [C], simple assignment
- assignment operators [C++], simple
- simple assignment operator
- equal sign
ms.assetid: e7140a0a-7104-4b3a-b293-7adcc1fdd52b
ms.openlocfilehash: 77c61101e9540a0d9469e7176eb15992a73b4b09
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158279"
---
# <a name="simple-assignment-c"></a>Einfache Zuweisung (C)

Der einfache Zuweisungsoperator weist seinen rechten Operanden dem linken Operanden zu. Der Wert des rechten Operanden wird in den Typ des Zuweisungsausdrucks konvertiert und ersetzt den Wert, der im Objekt gespeichert wird, das durch den linken Operanden festgelegt ist. Es gelten die Konvertierungsregeln für die Zuweisung (siehe [Zuweisungskonvertierungen](../c-language/assignment-conversions.md)).

```
double x;
int y;

x = y;
```

In diesem Beispiel wird der Wert von `y` in den Typ **double** konvertiert und `x` zugewiesen.

## <a name="see-also"></a>Siehe auch

[C-Zuweisungsoperatoren](../c-language/c-assignment-operators.md)
