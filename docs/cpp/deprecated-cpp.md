---
title: deprecated (C++)
ms.date: 03/28/2017
f1_keywords:
- deprecated_cpp
helpviewer_keywords:
- __declspec keyword [C++], deprecated
- deprecated __declspec keyword
ms.assetid: beef1129-9434-4cb3-8392-f1eb29e04805
ms.openlocfilehash: 44cb33bae43b32b12dda95423aec5484f61aa596
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90683415"
---
# <a name="deprecated-c"></a>deprecated (C++)

In diesem Thema wird die Microsoft-spezifische Deklaration der Deklaration "declspec" erläutert. Weitere Informationen zum C++ 14 `[[deprecated]]` -Attribut und Anleitungen zur Verwendung dieses Attributs im Vergleich zu Microsoft-spezifischen declspec-oder pragma finden Sie unter [C++-Standard Attribute](attributes.md).

Mit den unten aufgeführten Ausnahmen bietet die- **`deprecated`** Deklaration die gleiche Funktionalität wie das [veraltet](../preprocessor/deprecated-c-cpp.md) -Pragma:

- Die- **`deprecated`** Deklaration ermöglicht es Ihnen, bestimmte Formen von Funktions Überladungen als veraltet anzugeben, während das Pragma-Formular für alle überladenen Formen eines Funktionsnamens gilt.

- Mit der- **`deprecated`** Deklaration können Sie eine Meldung angeben, die zur Kompilierzeit angezeigt wird. Der Text der Meldung kann von einem Makro stammen.

- Makros können nur mit dem Pragma als veraltet markiert werden **`deprecated`** .

Wenn der Compiler auf die Verwendung eines veralteten Bezeichners oder des Standard [`[[deprecated]]`](attributes.md) Attributs stößt, wird eine [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) -Warnung ausgelöst.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird gezeigt, wie Funktionen als veraltet gekennzeichnet werden und wie eine Meldung angegeben wird, die bei Verwendung einer veralteten Funktion zur Kompilierzeit angezeigt wird.

```cpp
// deprecated.cpp
// compile with: /W3
#define MY_TEXT "function is deprecated"
void func1(void) {}
__declspec(deprecated) void func1(int) {}
__declspec(deprecated("** this is a deprecated function **")) void func2(int) {}
__declspec(deprecated(MY_TEXT)) void func3(int) {}

int main() {
   func1();
   func1(1);   // C4996
   func2(1);   // C4996
   func3(1);   // C4996
}
```

Im folgenden Beispiel wird gezeigt, wie Klassen als veraltet gekennzeichnet werden und wie eine Meldung angegeben wird, die bei Verwendung einer veralteten Klasse zur Kompilierzeit angezeigt wird.

```cpp
// deprecate_class.cpp
// compile with: /W3
struct __declspec(deprecated) X {
   void f(){}
};

struct __declspec(deprecated("** X2 is deprecated **")) X2 {
   void f(){}
};

int main() {
   X x;   // C4996
   X2 x2;   // C4996
}
```

## <a name="see-also"></a>Weitere Informationen

[__declspec](../cpp/declspec.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
