---
title: Compilerwarnung C4693
ms.date: 10/25/2017
f1_keywords:
- C4693
helpviewer_keywords:
- C4693
ms.assetid: 72d8db01-5e6f-4794-8731-76107e8f064a
ms.openlocfilehash: 71c3db18b400ce94bff3c643d6728a6613061039
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165131"
---
# <a name="compiler-warning-c4693"></a>Compilerwarnung C4693

> "class": Eine versiegelte abstrakte Klasse kann keine Test-Instanzmember aufweisen

Wenn ein Typ als [versiegelt](../../extensions/sealed-cpp-component-extensions.md) und [abstrakt](../../extensions/abstract-cpp-component-extensions.md)markiert ist, kann er nur statische Member aufweisen.

Diese Warnung wird automatisch zu einem Fehler heraufgestuft. Wenn Sie dieses Verhalten ändern möchten, verwenden Sie [#pragma Warnung](../../preprocessor/warning.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4693 generiert:

```cpp
// C4693.cpp
// compile with: /clr /c
public ref class Public_Ref_Class sealed abstract {
public:
   void Test() {}   // C4693
   static void Test2() {}   // OK
};
```
