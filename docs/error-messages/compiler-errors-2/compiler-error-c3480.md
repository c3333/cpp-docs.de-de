---
title: Compilerfehler C3480
ms.date: 11/04/2016
f1_keywords:
- C3480
helpviewer_keywords:
- C3480
ms.assetid: 7b2e055a-9604-4d13-861b-b38bda1a6940
ms.openlocfilehash: a2fa1a8b02cf05d332210f359ae3ff33ed7d6e35
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686305"
---
# <a name="compiler-error-c3480"></a>Compilerfehler C3480

"Var": Eine Lambdaerfassungsvariable muss aus einem einschließenden Funktionsbereich stammen.

Die Lambdaerfassungsvariable stammt nicht aus einem einschließenden Funktionsbereich.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Entfernen Sie die Variable aus der Erfassungsliste des Lambda-Ausdrucks.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C3480 generiert, da die Variable `global` nicht aus einem einschließenden Funktionsbereich stammt:

```cpp
// C3480a.cpp

int global = 0;
int main()
{
   [&global] { global = 5; }(); // C3480
}
```

Im folgenden Beispiel wird C3480 durch Entfernen der Variablen `global` aus der Erfassungsliste des Lambdaausdrucks behoben:

```cpp
// C3480b.cpp

int global = 0;
int main()
{
   [] { global = 5; }();
}
```

## <a name="see-also"></a>Siehe auch

[Lambda-Ausdrücke](../../cpp/lambda-expressions-in-cpp.md)
