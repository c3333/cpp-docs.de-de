---
title: __if_exists-Anweisung
ms.date: 11/04/2016
f1_keywords:
- __if_exists_cpp
helpviewer_keywords:
- identifiers, testing for existence
- symbols, testing for existence
- __if_exists keyword [C++]
ms.assetid: d3eb34b6-f3a9-4063-a286-b62a28c0c7fa
ms.openlocfilehash: 6522b1877dd2517032fc140de42671353ce9c357
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561400"
---
# <a name="__if_exists-statement"></a>__if_exists-Anweisung

Die- **`__if_exists`** Anweisung testet, ob der angegebene Bezeichner vorhanden ist. Wenn der Bezeichner vorhanden ist, wird der angegebene Anweisungsblock ausgeführt.

## <a name="syntax"></a>Syntax

```
__if_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>Parameter

*Bezeichner*\
Der Bezeichner, dessen Vorhandensein Sie überprüfen möchten.

*Äußerungen*\
Eine oder mehrere auszuführende Anweisungen, wenn der *Bezeichner* vorhanden ist.

## <a name="remarks"></a>Bemerkungen

> [!CAUTION]
> Um die zuverlässigsten Ergebnisse zu erzielen, verwenden Sie die- **`__if_exists`** Anweisung unter den folgenden Einschränkungen.

- Wenden Sie die- **`__if_exists`** Anweisung nur auf einfache Typen, nicht auf Vorlagen an.

- Wenden Sie die- **`__if_exists`** Anweisung auf Bezeichner innerhalb oder außerhalb einer Klasse an. Wenden Sie die- **`__if_exists`** Anweisung nicht auf lokale Variablen an.

- Verwenden Sie die- **`__if_exists`** Anweisung nur im Text einer Funktion. Außerhalb des Texts einer Funktion kann die- **`__if_exists`** Anweisung nur vollständig definierte Typen testen.

- Wenn Sie auf überladene Funktionen testen, können Sie nicht auf eine bestimmte Form der Überladung testen.

Das Komplement der- **`__if_exists`** Anweisung ist die [__if_not_exists](../cpp/if-not-exists-statement.md) -Anweisung.

## <a name="example"></a>Beispiel

Beachten Sie, dass in diesem Beispiel Vorlagen verwendet werden, was nicht empfohlen wird.

```cpp
// the__if_exists_statement.cpp
// compile with: /EHsc
#include <iostream>

template<typename T>
class X : public T {
public:
   void Dump() {
      std::cout << "In X<T>::Dump()" << std::endl;

      __if_exists(T::Dump) {
         T::Dump();
      }

      __if_not_exists(T::Dump) {
         std::cout << "T::Dump does not exist" << std::endl;
      }
   }
};

class A {
public:
   void Dump() {
      std::cout << "In A::Dump()" << std::endl;
   }
};

class B {};

bool g_bFlag = true;

class C {
public:
   void f(int);
   void f(double);
};

int main() {
   X<A> x1;
   X<B> x2;

   x1.Dump();
   x2.Dump();

   __if_exists(::g_bFlag) {
      std::cout << "g_bFlag = " << g_bFlag << std::endl;
   }

   __if_exists(C::f) {
      std::cout << "C::f exists" << std::endl;
   }

   return 0;
}
```

## <a name="output"></a>Output

```Output
In X<T>::Dump()
In A::Dump()
In X<T>::Dump()
T::Dump does not exist
g_bFlag = 1
C::f exists
```

## <a name="see-also"></a>Siehe auch

[Auswahlanweisungen](../cpp/selection-statements-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[__if_not_exists-Anweisung](../cpp/if-not-exists-statement.md)
