---
title: Compilerwarnung (Stufe 1) C4342
ms.date: 11/04/2016
f1_keywords:
- C4342
helpviewer_keywords:
- C4342
ms.assetid: 47d4d5ab-069f-4cdc-98c3-10d649577a37
ms.openlocfilehash: 8ac00d3d57f8cf7d6c85f3106dbe9b8c3cb9adf0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162919"
---
# <a name="compiler-warning-level-1-c4342"></a>Compilerwarnung (Stufe 1) C4342

Behavior Change: "*Function*" aufgerufen, aber in früheren Versionen wurde ein Member-Operator aufgerufen.

In Visual C++ Studio-Versionen vor Visual Studio 2002 wurde ein Member aufgerufen, aber dieses Verhalten wurde geändert, und der Compiler findet nun die beste Entsprechung im Namespace Bereich.

Wenn ein Member-Operator gefunden wurde, hat der Compiler zuvor keine Namespace-Bereichs Operatoren in Erwägung gezogen. Wenn der Namespace Bereich besser abgeglichen wird, ruft der aktuelle Compiler ihn ordnungsgemäß auf, während vorherige Compiler ihn nicht in Erwägung gezogen haben.

Diese Warnung sollte deaktiviert werden, nachdem Sie den Code erfolgreich auf die aktuelle Version portieren.  Der Compiler kann falsch positive Ergebnisse erzeugen und diese Warnung für Code generieren, bei dem keine Behavior Change vorhanden ist.

Diese Warnung ist standardmäßig deaktiviert. Weitere Informationen finden Sie unter [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

Im folgenden Beispiel wird C4342 generiert:

```cpp
// C4342.cpp
// compile with: /EHsc /W1
#include <fstream>
#pragma warning(default: 4342)
using namespace std;
struct X : public ofstream {
   X();
};

X::X() {
   open( "ofs_bug_ev.txt." );
   if ( is_open() ) {
      *this << "Text" << "<-should be text" << endl;   // C4342
      *this << ' ' << "<-should be space symbol" << endl;   // C4342
   }
}

int main() {
   X b;
   b << "Text" << "<-should be text" << endl;
   b << ' ' << "<-should be space symbol" << endl;
}
```
