---
title: Compilerfehler C2555
description: Referenz für Visual Studio C++ Compilerfehler C2555.
ms.date: 03/30/2020
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: ecac92bc663a6344e9ddafe13c194a92ab944c51
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87207796"
---
# <a name="compiler-error-c2555"></a>Compilerfehler C2555

> '*Class1*::*Funktion1*': der Rückgabetyp der virtuellen Funktion wird unterschiedlich und ist nicht kovariant von '*Klasse2*::*Funktion2*'.

Eine virtuelle Funktion und eine abgeleitete Überschreibungs Funktion verfügen über identische Parameterlisten, aber unterschiedliche Rückgabe Typen.

## <a name="remarks"></a>Bemerkungen

In C++ kann eine über schreibende Funktion in einer abgeleiteten Klasse sich nicht nur durch den Rückgabetyp einer virtuellen Funktion in einer Basisklasse unterscheiden.

Für bestimmte Rückgabe Typen gibt es eine Ausnahme von dieser Regel. Wenn eine abgeleitete Klasse eine öffentliche Basisklasse überschreibt, gibt Sie möglicherweise einen Zeiger oder Verweis auf die abgeleitete Klasse anstelle eines Basisklassen Zeigers oder Verweises zurück. Diese Rückgabe Typen werden als *kovariant*bezeichnet, da Sie sich zusammen mit dem Typ unterscheiden. Diese Regel Ausnahme lässt keinen kovarianten Verweis auf Zeiger-oder Zeiger-Zeiger-Typen zu.

Eine Möglichkeit, den Fehler zu beheben, besteht darin, den gleichen Typ wie die Basisklasse zurückzugeben. Wandeln Sie anschließend den Rückgabewert um, nachdem die virtuelle Funktion aufgerufen wurde. Eine andere besteht darin, auch die Parameterliste zu ändern, damit die abgeleitete Klassenmember-Funktion eine Überladung anstelle einer außer Kraft Setzung ist.

## <a name="examples"></a>Beispiele

Dieser Fehler wird möglicherweise angezeigt, wenn Sie mit kompilieren **`/clr`** . Beispielsweise entspricht die C++ der folgenden c#-Deklaration:

```csharp
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

is

```cpp
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];
```

Im folgenden Beispiel wird C2555 generiert:

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

Um dieses Problem zu beheben, ändern Sie den Rückgabetyp von `Y::func` in **`void`** .
