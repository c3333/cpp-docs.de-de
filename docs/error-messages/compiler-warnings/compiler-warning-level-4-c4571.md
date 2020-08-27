---
title: Compilerwarnung (Stufe 4) C4571
description: Dokumentiert die Microsoft C++-Compilerwarnung C4571.
ms.date: 08/24/2020
f1_keywords:
- C4571
helpviewer_keywords:
- C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
ms.openlocfilehash: 35f2b30a8ab7cfcc27ed7aae3aedd9bc81efacc8
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898549"
---
# <a name="compiler-warning-level-4-c4571"></a>Compilerwarnung (Stufe 4) C4571

> Information: `catch(...)` die Semantik wurde seit Visual C++ 7,1 geändert; strukturierte Ausnahmen (SEH) werden nicht mehr abgefangen.

C4571 wird für jeden Block generiert, `catch(...)` Wenn Sie die- **`/EHs`** Compileroption angeben.

## <a name="remarks"></a>Hinweise

Wenn Sie die- **`/EHs`** Compileroption angeben, `catch(...)` fangen-Blöcke keine strukturierten Ausnahmen ab. (Z. b. Division durch Null oder NULL-Zeiger Ausnahmen, z. b.). Ein- `catch(...)` Block fängt nur explizit ausgelöste C++-Ausnahmen ab. Weitere Informationen finden Sie unter [Ausnahmebehandlung (Task Parallel Library)](../../cpp/exception-handling-in-visual-cpp.md).

Diese Warnung ist standardmäßig deaktiviert.  Aktivieren Sie diese Warnung, um sicherzustellen, dass bei der Kompilierung mit **`/EHs`** Ihren- `catch (...)` Blöcken keine strukturierten Ausnahmen abgefangen werden. Weitere Informationen finden Sie unter [standardmäßig](../../preprocessor/compiler-warnings-that-are-off-by-default.md)deaktivierte Compilerwarnungen.

Sie können C4571 auf eine der folgenden Arten auflösen:

- Kompilieren **`/EHa`** Sie mit, wenn Sie möchten `catch(...)` , dass Ihre Blöcke strukturierte Ausnahmen abfangen.

- Aktivieren Sie C4571 nicht, wenn Sie nicht möchten, dass Ihre `catch(...)` Blöcke strukturierte Ausnahmen abfangen, Sie aber weiterhin Blöcke verwenden möchten `catch(...)` .  Sie können strukturierte Ausnahmen weiterhin mithilfe der Schlüsselwörter für die strukturierte Ausnahmebehandlung ( **`__try`** , **`__except`** und) abfangen **`__finally`** .  Beachten Sie jedoch, dass bei der Kompilierung von deerdeerdektoren **`/EHs`** nur aufgerufen werden, wenn eine C++-Ausnahme ausgelöst wird, nicht wenn eine SEH-Ausnahme auftritt

- Ersetzen `catch(...)` Sie Blöcke durch Catch-Blöcke für bestimmte C++-Ausnahmen, und fügen Sie optional eine strukturierte Ausnahmebehandlung um die C++-Ausnahmebehandlung ( **`__try`** , **`__except`** und **`__finally`** ) hinzu.   Weitere Informationen finden Sie unter [strukturierte Ausnahmebehandlung (C/C++)](../../cpp/structured-exception-handling-c-cpp.md) und [ `/EH` (Ausnahme Behandlungsmodell)](../../build/reference/eh-exception-handling-model.md).

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
