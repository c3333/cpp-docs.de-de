---
title: deprecated (C++)
ms.date: 03/28/2017
f1_keywords:
- deprecated_cpp
helpviewer_keywords:
- __declspec keyword [C++], deprecated
- deprecated __declspec keyword
ms.assetid: beef1129-9434-4cb3-8392-f1eb29e04805
ms.openlocfilehash: e4689d3cb1a1757e2ac3bf4ca9eef7670ad5c655
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189480"
---
# <a name="deprecated-c"></a>deprecated (C++)

In diesem Thema wird die Microsoft-spezifische Deklaration der Deklaration "declspec" erläutert. Weitere Informationen zum c++ 14-`[[deprecated]]`-Attribut sowie Anleitungen zur Verwendung dieses Attributs im Vergleich zu den Microsoft-spezifischen declspec-oder Pragma- [ C++ Attributen](attributes.md)finden Sie unter Standard Attribute.

Mit den unten aufgeführten Ausnahmen bietet die **Veraltete** Deklaration die gleiche Funktionalität wie das [veraltet](../preprocessor/deprecated-c-cpp.md) -Pragma:

- Mit der **veralteten** Deklaration können Sie bestimmte Formen von Funktions Überladungen als veraltet festlegen, während das Pragma-Formular für alle überladenen Formen eines Funktionsnamens gilt.

- Mit der **veralteten** Deklaration können Sie eine Meldung angeben, die zur Kompilierzeit angezeigt wird. Der Text der Meldung kann von einem Makro stammen.

- Makros können nur mit dem **veraltet** -Pragma als veraltet markiert werden.

Wenn der Compiler auf die Verwendung eines veralteten Bezeichners oder des Standard- [`[[deprecated]]`](attributes.md) Attributs stößt, wird eine [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) -Warnung ausgelöst.

## <a name="example"></a>Beispiel

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

## <a name="example"></a>Beispiel

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
