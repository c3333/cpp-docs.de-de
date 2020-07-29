---
title: Compilerwarnung (Stufe 4) C4571
ms.date: 11/04/2016
f1_keywords:
- C4571
helpviewer_keywords:
- C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
ms.openlocfilehash: 4fe99e12c5d2dfb725e1e4aa0ac2fb0b1ccb4f28
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219884"
---
# <a name="compiler-warning-level-4-c4571"></a>Compilerwarnung (Stufe 4) C4571

Information: die catch (...)-Semantik wurde seit Visual C++ 7,1 geändert. strukturierte Ausnahmen (SEH) werden nicht mehr abgefangen.

C4571 wird für jeden catch-Block (...) bei der Kompilierung mit **/EHS**generiert.

Beim Kompilieren mit **/EHS**fängt ein catch-Block (...) keine strukturierte Ausnahme ab (z. b. Division durch 0 (null), z. b. NULL-Zeiger); ein catch-Block (...) fängt nur explizit ausgelöste C++-Ausnahmen ab.  Weitere Informationen finden Sie unter [Ausnahmebehandlung (Task Parallel Library)](../../cpp/exception-handling-in-visual-cpp.md).

Diese Warnung ist standardmäßig deaktiviert.  Aktivieren Sie diese Warnung, um sicherzustellen, dass Ihre Catch-Blöcke (...) bei der Kompilierung mit **/EHS** keine strukturierten Ausnahmen abfangen möchten.  Weitere Informationen finden Sie unter [Standardmäßig deaktivierte Compilerwarnungen](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Sie können C4571 auf eine der folgenden Arten auflösen:

- Kompilieren Sie mit **/EHa** , wenn Sie möchten, dass Ihre catch (...)-Blöcke strukturierte Ausnahmen abfangen.

- Aktivieren Sie C4571 nicht, wenn Sie nicht möchten, dass Ihre catch (...)-Blöcke strukturierte Ausnahmen abfangen, Sie aber weiterhin catch-Blöcke (...) verwenden möchten.  Sie können auch strukturierte Ausnahmen mithilfe der Schlüsselwörter für die strukturierte Ausnahmebehandlung (**__try**, **`__except`** und) auffangen **`__finally`** .  Beachten Sie jedoch, dass kompilierte **/EHS** -dededektoren nur aufgerufen werden, wenn eine C++-Ausnahme ausgelöst wird, und nicht, wenn eine SEH-Ausnahme auftritt.

- Ersetzen Sie catch (...)-Block durch Catch-Blöcke für bestimmte C++-Ausnahmen, und fügen Sie optional eine strukturierte Ausnahmebehandlung um die C++-Ausnahmebehandlung (**__try**, **`__except`** und **`__finally`** ) hinzu.  Weitere Informationen finden Sie unter [strukturierte Ausnahmebehandlung (C/C++)](../../cpp/structured-exception-handling-c-cpp.md) .

Weitere Informationen finden Sie unter [/eh (Ausnahme Behandlungsmodell)](../../build/reference/eh-exception-handling-model.md) .

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4571 generiert.

```cpp
// C4571.cpp
// compile with: /EHs /W4 /c
#pragma warning(default : 4571)
int main() {
   try {
      int i = 0, j = 1;
      j /= i;   // this will throw a SE (divide by zero)
   }
   catch(...) {}   // C4571 warning
}
```
