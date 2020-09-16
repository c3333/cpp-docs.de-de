---
title: Compilerfehler C3533
ms.date: 11/04/2016
f1_keywords:
- C3533
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
ms.openlocfilehash: 4e3c773d0498a35c7b5d053268bff26f9943103b
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686768"
---
# <a name="compiler-error-c3533"></a>Compilerfehler C3533

"Typ": ein Parameter darf keinen Typ aufweisen, der "Auto" enthält.

Eine Methode oder ein Vorlagen Parameter kann nicht mit dem **`auto`** Schlüsselwort deklariert werden, wenn die standardmäßige [/Zc: Auto](../../build/reference/zc-auto-deduce-variable-type.md) -Compileroption aktiviert ist.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Entfernen Sie das- **`auto`** Schlüsselwort aus der Parameter Deklaration.

## <a name="examples"></a>Beispiele

Das folgende Beispiel ergibt C3533, da es einen Funktionsparameter mit dem **`auto`** -Schlüsselwort deklariert und mit **/Zc: Auto**kompiliert wird.

```cpp
// C3533a.cpp
// Compile with /Zc:auto
void f(auto j) {} // C3533
```

Im folgenden Beispiel wird C3533 im c++ 14-Modus erstellt, da er einen Vorlagen Parameter mit dem **`auto`** -Schlüsselwort deklariert und mit **/Zc: Auto**kompiliert wird. (In c++ 17 ist dies eine gültige Definition einer Klassen Vorlage mit einem einzigen Nichttyp-Vorlagen Parameter, dessen Typ abgeleitet ist.)

```cpp
// C3533b.cpp
// Compile with /Zc:auto
template<auto T> class C {}; // C3533
```

## <a name="see-also"></a>Siehe auch

[Auto-Schlüsselwort](../../cpp/auto-keyword.md)<br/>
[/Zc: Auto (Variablentyp ableiten)](../../build/reference/zc-auto-deduce-variable-type.md)
