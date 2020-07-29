---
title: finally
ms.date: 11/04/2016
helpviewer_keywords:
- finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
ms.openlocfilehash: b3331c17fc2313cbd6146db3beb015cd8d8c1eeb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221457"
---
# <a name="finally"></a>finally

Zusätzlich zu den **`try`** -und- **`catch`** Klauseln unterstützt die CLR-Ausnahmebehandlung eine- **`finally`** Klausel. Die Semantik ist mit dem **`__finally`** Block in der strukturierten Ausnahmebehandlung (SEH) identisch. Ein- **`__finally`** Block kann einem- **`try`** oder-Block folgen **`catch`** .

## <a name="remarks"></a>Bemerkungen

Der Zweck des- **`finally`** Blocks ist das Bereinigen von Ressourcen, die nach dem Auftreten der Ausnahme verbleiben. Beachten Sie, dass der- **`finally`** Block immer ausgeführt wird, auch wenn keine Ausnahme ausgelöst wurde. Der- **`catch`** Block wird nur ausgeführt, wenn im zugeordneten-Block eine verwaltete Ausnahme ausgelöst wird **`try`** .

`finally`ist ein kontextsensitiv Schlüsselwort. Weitere Informationen finden Sie unter [kontextabhängige Schlüsselwörter](../extensions/context-sensitive-keywords-cpp-component-extensions.md) .

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird ein einfacher **`finally`** Block veranschaulicht:

```cpp
// keyword__finally.cpp
// compile with: /clr
using namespace System;

ref class MyException: public System::Exception{};

void ThrowMyException() {
   throw gcnew MyException;
}

int main() {
   try {
      ThrowMyException();
   }
   catch ( MyException^ e ) {
      Console::WriteLine(  "in catch" );
      Console::WriteLine( e->GetType() );
   }
   finally {
      Console::WriteLine(  "in finally" );
   }
}
```

```Output
in catch
MyException
in finally
```

## <a name="see-also"></a>Weitere Informationen

[Ausnahmebehandlung](../extensions/exception-handling-cpp-component-extensions.md)
