---
title: Compilerwarnung C4867
ms.date: 11/04/2016
f1_keywords:
- C4867
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
ms.openlocfilehash: a2298f5369ff941a9d5ac38838f531d6db478739
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165092"
---
# <a name="compiler-warning-c4867"></a>Compilerwarnung C4867

"Function": Funktionsaufrufe fehlen Argumentliste; Verwenden Sie "rufen", um einen Zeiger auf den Member zu erstellen.

Ein Zeiger auf die Member-Funktion wurde nicht ordnungsgemäß initialisiert.

Diese Warnung kann als Ergebnis einer compilerübereinstimmungs-Arbeit generiert werden, die für Visual Studio 2005 ausgeführt wurde: Erweiterte Zeiger-zu-Member-Konformität.  Code, der vor Visual Studio 2005 kompiliert wurde, generiert jetzt C4867.

Diese Warnmeldung wird immer als Fehler ausgegeben. Verwenden Sie das [warning](../../preprocessor/warning.md) -Pragma, um diese Warnung zu deaktivieren. Weitere Informationen zu C4867 und MFC/ATL finden Sie unter [_ATL_ENABLE_PTM_WARNING](../../atl/reference/compiler-options-macros.md#_atl_enable_ptm_warning).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4867 generiert.

```cpp
// C4867.cpp
// compile with: /c
class A {
public:
   void f(int) {}

   typedef void (A::*TAmtd)(int);

   struct B {
      TAmtd p;
   };

   void g() {
      B b = {f};   // C4867
      B b2 = {&A::f};   // OK
   }
};
```
