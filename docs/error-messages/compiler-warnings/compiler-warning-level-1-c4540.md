---
title: Compilerwarnung (Stufe 1) C4540
ms.date: 11/04/2016
f1_keywords:
- C4540
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
ms.openlocfilehash: 13935e7eebdf3e7b7e89fad8c55d410cf2788e4d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230648"
---
# <a name="compiler-warning-level-1-c4540"></a>Compilerwarnung (Stufe 1) C4540

dynamic_cast, die verwendet werden, um in die nicht zugängliche oder mehrdeutige Basis der Lauf Zeit Test schlägt fehl ("Typ1" zu "Typ2").

Sie haben verwendet **`dynamic_cast`** , um von einem Typ in einen anderen zu konvertieren. Der Compiler hat festgestellt, dass die Umwandlung immer einen Fehler erzeugt (z. b. **null**zurückgeben), weil auf eine Basisklasse (z. b.) nicht zugegriffen werden kann (z. b. **`private`** in der Klassenhierarchie mehrmals angezeigt).

Im folgenden finden Sie ein Beispiel für diese Warnung. Klasse **B** ist von Klasse **a**abgeleitet. Das Programm verwendet **`dynamic_cast`** zum Umwandeln von Klasse **b** (die abgeleitete Klasse) in Klasse **A**, was immer fehlschlägt, weil Class **b** den Wert hat **`private`** und somit nicht zugänglich ist. Wenn **Sie den Zugriff eines in** ändern, **`public`** wird die Warnung aufgelöst.

```cpp
// C4540.cpp
// compile with: /W1

struct A {
   virtual void g() {}
};

struct B : private A {
   virtual void g() {}
};

int main() {
   B b;
   A * ap = dynamic_cast<A*>(&b);   // C4540
}
```
