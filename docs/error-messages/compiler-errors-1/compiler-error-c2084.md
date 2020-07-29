---
title: Compilerfehler C2084
ms.date: 11/04/2016
f1_keywords:
- C2084
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
ms.openlocfilehash: f217e0b94e27c0f85879e80b3ae887cb4f76f486
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216361"
---
# <a name="compiler-error-c2084"></a>Compilerfehler C2084

die Funktion "*Function*" hat bereits einen Text.

Die Funktion wurde bereits definiert.

Vor Visual Studio 2002,

- Der Compiler würde mehrere Vorlagen spezizierungen akzeptieren, die in denselben tatsächlichen Typ aufgelöst wurden, obwohl die zusätzlichen Definitionen nie verfügbar wären. Der Compiler erkennt jetzt diese mehrere Definitionen.

- **`__int32`** und **`int`** wurden als separate Typen behandelt. Der Compiler behandelt nun **`__int32`** als Synonym für **`int`** . Dies bedeutet, dass der Compiler mehrere Definitionen erkennt, wenn eine Funktion sowohl in als auch in überlastet ist **`__int32`** **`int`** und einen Fehler liefert.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2084 generiert:

```cpp
// C2084.cpp
void Func(int);
void Func(int) {}   // define function
void Func(int) {}   // C2084 second definition
```

Entfernen Sie die doppelte Definition, um diesen Fehler zu beheben:

```cpp
// C2084b.cpp
// compile with: /c
void Func(int);
void Func(int) {}
```
