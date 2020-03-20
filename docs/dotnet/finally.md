---
title: finally
ms.date: 11/04/2016
helpviewer_keywords:
- finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
ms.openlocfilehash: 2574ba5a10bbf5eddc68d6e0265d5dfc99c6d8fc
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545096"
---
# <a name="finally"></a>finally

Zusätzlich zu den `try`-und `catch`-Klauseln unterstützt die CLR-Ausnahmebehandlung eine `finally`-Klausel. Die Semantik ist mit dem `__finally`-Block in der strukturierten Ausnahmebehandlung (SEH) identisch. Ein `__finally`-Block kann einem `try`-oder `catch`-Block folgen.

## <a name="remarks"></a>Hinweise

Der Zweck des `finally` Blocks besteht darin, alle Ressourcen zu bereinigen, die nach dem Auftreten der Ausnahme verbleiben. Beachten Sie, dass der `finally`-Block immer ausgeführt wird, auch wenn keine Ausnahme ausgelöst wurde. Der `catch`-Block wird nur ausgeführt, wenn im zugeordneten `try` Block eine verwaltete Ausnahme ausgelöst wird.

`finally` ist ein kontextsensitiv Schlüsselwort. Weitere Informationen finden Sie unter [kontextabhängige Schlüsselwörter](../extensions/context-sensitive-keywords-cpp-component-extensions.md) .

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht einen einfachen `finally`-Block:

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

## <a name="see-also"></a>Siehe auch

[Behandlung von Ausnahmen](../extensions/exception-handling-cpp-component-extensions.md)
