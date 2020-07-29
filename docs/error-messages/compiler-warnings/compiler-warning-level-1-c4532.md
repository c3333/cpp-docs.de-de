---
title: Compilerwarnung (Stufe 1) C4532
ms.date: 11/04/2016
f1_keywords:
- C4532
helpviewer_keywords:
- C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
ms.openlocfilehash: b8c7503c7d1c1b711006415a327c360731222042
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87196343"
---
# <a name="compiler-warning-level-1-c4532"></a>Compilerwarnung (Stufe 1) C4532

"Continue": springen aus __finally/finally-Block weist ein undefiniertes Verhalten während der Abbruch Behandlung auf.

Der Compiler hat eines der folgenden Schlüsselwörter gefunden:

- [continue](../../cpp/continue-statement-cpp.md)

- [break](../../cpp/break-statement-cpp.md)

- [goto](../../cpp/goto-statement-cpp.md)

Auslösen eines [__finally](../../cpp/try-finally-statement.md) [oder letzten](../../dotnet/finally.md) Blocks während der nicht ordnungsgemäßen Beendigung.

Wenn eine Ausnahme auftritt und der Stapel während der Ausführung der Beendigungs Handler entladen wird (die **`__finally`** -oder schließlich-Blöcke) und der Code aus einem Block springt, **`__finally`** bevor der- **`__finally`** Block beendet wird, ist das Verhalten nicht definiert. Das Steuerelement wird möglicherweise nicht zum Entwicklungscode zurückgegeben, sodass die Ausnahme möglicherweise nicht ordnungsgemäß behandelt wird.

Wenn Sie aus einem-Block herausspringen müssen **`__finally`** , überprüfen Sie zunächst, ob eine ungewöhnliche Beendigung auftritt.

Im folgenden Beispiel wird C4532 generiert. kommentieren Sie einfach die Jump-Anweisungen aus, um die Warnungen aufzulösen.

```cpp
// C4532.cpp
// compile with: /W1
// C4532 expected
int main() {
   int i;
   for (i = 0; i < 10; i++) {
      __try {
      } __finally {
         // Delete the following line to resolve.
         continue;
      }

      __try {
      } __finally {
         // Delete the following line to resolve.
         break;
      }
   }
}
```
