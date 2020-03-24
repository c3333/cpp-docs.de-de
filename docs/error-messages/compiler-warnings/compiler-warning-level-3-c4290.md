---
title: Compilerwarnung (Stufe 3) C4290
ms.date: 11/04/2016
f1_keywords:
- C4290
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
ms.openlocfilehash: 5970aa439a450bda4c1a2036da299d5c3cfbdb7a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198899"
---
# <a name="compiler-warning-level-3-c4290"></a>Compilerwarnung (Stufe 3) C4290

C++Ausnahme Spezifikation ignoriert, außer um anzugeben, dass eine Funktion nicht __declspec (nothrow)

Eine Funktion wird mit der Ausnahme Spezifikation deklariert, die C++ von Visual akzeptiert, aber nicht implementiert wird. Code mit Ausnahme Spezifikationen, die während der Kompilierung ignoriert werden, müssen möglicherweise erneut kompiliert und verknüpft werden, damit Sie in zukünftigen Versionen unterstützt werden, die Ausnahme Spezifikationen unterstützen

Weitere Informationen finden Sie unter [Ausnahme Spezifikationen (Throw)](../../cpp/exception-specifications-throw-cpp.md) .

Sie können diese Warnung vermeiden, indem Sie das [Warning](../../preprocessor/warning.md) -Pragma verwenden:

```cpp
#pragma warning( disable : 4290 )
```

Im folgenden Codebeispiel wird C4290 generiert:

```cpp
// C4290.cpp
// compile with: /EHs /W3 /c
void f1(void) throw(int) {}   // C4290

// OK
void f2(void) throw() {}
void f3(void) throw(...) {}
```
