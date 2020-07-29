---
title: deprecated-Pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.deprecated
helpviewer_keywords:
- deprecated pragma
- pragmas, deprecated
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
ms.openlocfilehash: 52d9deb4ad68dacc99fab9d12bc9eb21bc0d360e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231610"
---
# <a name="deprecated-pragma"></a>deprecated-Pragma

Das- **`deprecated`** pragma ermöglicht Ihnen anzugeben, dass eine Funktion, ein Typ oder ein anderer Bezeichner in einem zukünftigen Release möglicherweise nicht mehr unterstützt wird oder nicht mehr verwendet werden soll.

> [!NOTE]
> Weitere Informationen zum C++ 14 `[[deprecated]]` -Attribut und Anleitungen dazu, wann dieses Attribut anstelle des Microsoft- `__declspec(deprecated)` Modifizierers oder des- **`deprecated`** Pragmas verwendet werden sollte, finden Sie unter [Attribute in C++](../cpp/attributes.md).

## <a name="syntax"></a>Syntax

> **#pragma veraltet (** *Bezeichner1* [ **,** *Bezeichner2* ...] **)**

## <a name="remarks"></a>Bemerkungen

Wenn der Compiler auf einen Bezeichner stößt, der von einem **`deprecated`** pragma angegeben wird, gibt er Compilerwarnung [C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)aus.

Sie können Makronamen als veraltet deklarieren. Platzieren Sie den Makronamen in Anführungszeichen; andernfalls tritt eine Makroerweiterung auf.

Da das **`deprecated`** pragma für alle übereinstimmenden Bezeichner funktioniert und keine Signaturen berücksichtigt, ist es nicht die beste Option, um bestimmte Versionen von überladenen Funktionen als veraltet zu kennzeichnen. Alle übereinstimmenden Funktionsnamen, die in den Bereich eingefügt werden, lösen die Warnung aus.

Es wird empfohlen, anstelle des-Pragmas das c++ 14- `[[deprecated]]` Attribut zu verwenden **`deprecated`** . Der Microsoft-spezifische [__declspec (veraltet)](../cpp/deprecated-cpp.md) deklarationsmodifizierer ist in vielen Fällen auch eine bessere Wahl als das **`deprecated`** pragma. `[[deprecated]]`Mit dem-Attribut und dem- `__declspec(deprecated)` Modifizierer können Sie den veralteten Status für bestimmte Formen überladener Funktionen angeben. Die Diagnose Warnung wird nur bei verweisen auf die spezifische überladene Funktion angezeigt, auf die das Attribut oder der Modifizierer angewendet wird.

## <a name="example"></a>Beispiel

```cpp
// pragma_directive_deprecated.cpp
// compile with: /W3
#include <stdio.h>
void func1(void) {
}

void func2(void) {
}

int main() {
   func1();
   func2();
   #pragma deprecated(func1, func2)
   func1();   // C4995
   func2();   // C4995
}
```

Das folgende Beispiel zeigt, wie Sie eine Klasse als veraltet deklarieren:

```cpp
// pragma_directive_deprecated2.cpp
// compile with: /W3
#pragma deprecated(X)
class X {  // C4995
public:
   void f(){}
};

int main() {
   X x;   // C4995
}
```

## <a name="see-also"></a>Weitere Informationen

[Pragma-Anweisungen und das __pragma-Schlüsselwort](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
