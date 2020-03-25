---
title: property (C++)
ms.date: 11/04/2016
f1_keywords:
- property_cpp
helpviewer_keywords:
- property __declspec keyword
- __declspec keyword [C++], property
ms.assetid: f3b850ba-bf48-4df7-a1d6-8259d97309ce
ms.openlocfilehash: 03f71739698fd20a01fd72567ce5b9babc176327
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179301"
---
# <a name="property-c"></a>property (C++)

**Microsoft-spezifisch**

Dieses Attribut kann auf nicht statische "virtuelle Datenmember" in einer Klassen- oder Strukturdefinition angewendet werden. Der Compiler behandelt diese "virtuellen Datenmember" als Datenmember, indem er ihre Verweise in Funktionsaufrufe ändert.

## <a name="syntax"></a>Syntax

```
   __declspec( property( get=get_func_name ) ) declarator
   __declspec( property( put=put_func_name ) ) declarator
   __declspec( property( get=get_func_name, put=put_func_name ) ) declarator
```

## <a name="remarks"></a>Bemerkungen

Wenn der Compiler einen Datenmember erkennt, der mit diesem Attribut auf der rechten Seite eines Elementauswahl Operators (" **.** " oder " **->** ") deklariert wurde, konvertiert er den Vorgang in eine `get`-oder `put` Funktion, je nachdem, ob ein solcher Ausdruck ein l-Wert oder ein r-Wert ist. In komplizierteren Kontexten, wie z. b. "`+=`", wird ein umschreiben durchgeführt, indem sowohl `get` als auch `put`ausgeführt werden.

Dieses Attribut kann in der Deklaration eines leeren Arrays in einer Klassen- oder Strukturdefinition ebenfalls verwendet werden. Beispiel:

```cpp
__declspec(property(get=GetX, put=PutX)) int x[];
```

Die oben genannte Anweisung gibt an, dass `x[]` mit einem oder mehreren Arrayindizes verwendet werden kann. In diesem Fall wird `i=p->x[a][b]` in `i=p->GetX(a, b)` umgewandelt und `p->x[a][b] = i` in `p->PutX(a, b, i);`.

**Ende Microsoft-spezifisch**

## <a name="example"></a>Beispiel

```cpp
// declspec_property.cpp
struct S {
   int i;
   void putprop(int j) {
      i = j;
   }

   int getprop() {
      return i;
   }

   __declspec(property(get = getprop, put = putprop)) int the_prop;
};

int main() {
   S s;
   s.the_prop = 5;
   return s.the_prop;
}
```

## <a name="see-also"></a>Weitere Informationen

[__declspec](../cpp/declspec.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
