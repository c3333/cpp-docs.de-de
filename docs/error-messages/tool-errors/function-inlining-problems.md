---
title: Probleme bei Inlinefunktionen
ms.date: 11/04/2016
helpviewer_keywords:
- /Ob1 C++ compiler option
- inline functions, problems
- -Ob1 C++ compiler option
- /Ob2 C++ compiler option
- -Ob2 C++ compiler option
- function inlining problems
ms.assetid: 65d59943-4b3c-4a43-aeb6-dccbf7686740
ms.openlocfilehash: cb4653bd2f03683b9abad1eea0e9ffa88222090e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184241"
---
# <a name="function-inlining-problems"></a>Probleme bei Inlinefunktionen

Wenn Sie das Inlining von Funktionen verwenden, müssen Sie folgende Schritte ausführen:

- Die Inline Funktionen müssen in der Header Datei implementiert werden, die Sie einschließen.

- Aktivieren von Inlining in der Header Datei.

```cpp
// LNK2019_function_inline.cpp
// compile with: /c
// post-build command: lib LNK2019_function_inline.obj
#include <stdio.h>
struct _load_config_used {
   void Test();
   void Test2() { printf("in Test2\n"); }
};

void _load_config_used::Test() { printf("in Test\n"); }
```

und anschließend

```cpp
// LNK2019_function_inline_2.cpp
// compile with: LNK2019_function_inline.lib
struct _load_config_used {
   void Test();
   void Test2();
};

int main() {
   _load_config_used x;
   x.Test();
   x.Test2();   // LNK2019
}
```

Wenn Sie die `#pragma inline_depth`-Compilerdirektive verwenden, stellen Sie sicher, dass Sie den Wert 2 oder höher festgelegt haben. Der Wert 0 deaktiviert das inlining. Stellen Sie außerdem sicher, dass Sie die **/ob1** -oder **/Ob2** -Compileroptionen verwenden.

Das Mischen von Inline-und nicht-Inline-Kompilierungsoptionen für verschiedene Module kann manchmal zu Problemen führen. Wenn eine C++ Bibliothek mit aktivierter Funktion Inlining ([/ob1](../../build/reference/ob-inline-function-expansion.md) oder [/Ob2](../../build/reference/ob-inline-function-expansion.md)) erstellt wird, aber in der entsprechenden Header Datei, die die Funktionen beschreibt, das Inlining deaktiviert ist (keine Option), erhalten Sie den Fehler LNK2001. Die Funktionen werden nicht in den Code aus der Header Datei eingefügt, aber da Sie sich nicht in der Bibliotheksdatei befinden, gibt es keine Adresse zum Auflösen des Verweises.

Ebenso werden von einem Projekt, das Funktionen Inlining verwendet, die Funktionen in einer CPP-Datei und nicht in der Header Datei definiert. Außerdem wird LNK2019 angezeigt. Die Header Datei ist überall als geeignet enthalten, aber die Funktionen sind nur ineinandergeschaltet, wenn die CPP-Datei den Compiler durchläuft. Daher sieht der Linker die Funktionen als nicht aufgelöste externe, wenn Sie in anderen Modulen verwendet werden.

```cpp
// LNK2019_FIP.h
struct testclass {
   void PublicStatMemFunc1(void);
};
```

Und dann

```cpp
// LNK2019_FIP.cpp
// compile with: /c
#include "LNK2019_FIP.h"
inline void testclass::PublicStatMemFunc1(void) {}
```

Und dann

```cpp
// LNK2019_FIP_2.cpp
// compile with: LNK2019_FIP.cpp
// LNK2019 expected
#include "LNK2019_FIP.h"
int main() {
   testclass testclsObject;

   // module cannot see the implementation of PublicStatMemFunc1
   testclsObject.PublicStatMemFunc1();
}
```

## <a name="see-also"></a>Weitere Informationen

[Linkertoolfehler LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)
