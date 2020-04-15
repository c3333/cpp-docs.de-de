---
title: Compilerfehler C2555
description: Referenz für Visual Studio C++-Compilerfehler C2555.
ms.date: 03/30/2020
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: fe0e6379e783387506e6098c9b14a047baa8e6c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374175"
---
# <a name="compiler-error-c2555"></a>Compilerfehler C2555

> '*class1*::*function1*': überschreibender virtueller Funktionsrückgabetyp unterscheidet sich und ist nicht kovariant von '*class2*::*function2*'

Eine virtuelle Funktion und eine abgeleitete Überschreibenfunktion haben identische Parameterlisten, aber unterschiedliche Rückgabetypen.

## <a name="remarks"></a>Bemerkungen

In C++ kann sich eine übergeordnete Funktion in einer abgeleiteten Klasse nicht nur durch den Rückgabetyp von einer virtuellen Funktion in einer Basisklasse unterscheiden.

Es gibt eine Ausnahme von dieser Regel für bestimmte Rückgabetypen. Wenn eine abgeleitete Klasse eine öffentliche Basisklasse überschreibt, kann sie einen Zeiger oder Verweis auf die abgeleitete Klasse anstelle eines Basisklassenzeigers oder Verweises zurückgeben. Diese Rückgabetypen werden als *kovariant*bezeichnet, da sie zusammen mit dem Typ variieren. Diese Regelausnahme lässt keine kovarianten Verweis-auf-Zeiger- oder Zeiger-zu-Zeiger-Typen zu.

Eine Möglichkeit, den Fehler zu beheben, besteht darin, denselben Typ wie die Basisklasse zurückzugeben. Geben Sie dann den Rückgabewert um, nachdem die virtuelle Funktion aufgerufen wurde. Eine andere besteht darin, auch die Parameterliste zu ändern, um die abgeleitete Klassenmemberfunktion zu einer Überladung anstelle einer Außerkraftsetzung zu machen.

## <a name="examples"></a>Beispiele

Dieser Fehler wird möglicherweise angezeigt, wenn Sie mit **`/clr`** kompilieren. Die C++-Äquivalente zur folgenden C-Deklaration sind z. B.:

```csharp
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

is

```cpp
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];
```

Die folgende Stichprobe generiert C2555:

```cpp
// C2555.cpp
// compile with: /c
struct X {
   virtual void func();
};
struct Y : X {
   char func();  // C2555
   void func2();   // OK
};
```

Um dies zu beheben, `Y::func` `void`ändern Sie den Rückgabetyp von in .
