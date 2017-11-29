---
title: Probleme bei Inlinefunktionen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs: C++
helpviewer_keywords:
- /Ob1 C++ compiler option
- inline functions, problems
- -Ob1 C++ compiler option
- /Ob2 C++ compiler option
- -Ob2 C++ compiler option
- function inlining problems
ms.assetid: 65d59943-4b3c-4a43-aeb6-dccbf7686740
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4817093bf52ab5398f1d4a788b96bcff16384c1f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="function-inlining-problems"></a>Probleme bei Inlinefunktionen
Wenn Sie Inlinefunktionen verwenden, müssen Sie folgende Schritte ausführen:  
  
-   Haben Sie die Inlinefunktionen, die in der Headerdatei, die Sie einschließen implementiert.  
  
-   Haben inlining in der Headerdatei ist aktiviert.  
  
```  
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
  
```  
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
  
 Bei Verwendung der `#pragma inline_depth` Compiler, stellen Sie sicher, dass Sie einen Wert von 2 oder höher festgelegt haben. Der Wert 0 (null) deaktiviert inlining. Außerdem stellen Sie sicher, dass Sie die **/Ob1** oder **/Ob2** Compileroptionen.  
  
 Mischen von Inline- und nicht Kompilierungsoptionen auf andere Module kann in einigen Fällen Probleme verursachen. Wenn eine C++-Bibliothek mit Inlinefunktionen eingeschaltet erstellt wird ([/Ob1](../../build/reference/ob-inline-function-expansion.md) oder [/Ob2](../../build/reference/ob-inline-function-expansion.md)), aber die entsprechende Headerdatei, beschreibt die Funktionen hat inlining deaktiviert (keine Option), erhalten Sie die Fehlermeldung LNK2001. Die Funktionen erhalten keine Inline in den Code aus der Headerdatei, aber da sie nicht in die Bibliotheksdatei sind ist keine Adresse zum Auflösen des Verweises.  
  
 Auf ähnliche Weise definiert ein Projekt, das Inlinefunktionen verwendet noch die Funktionen in einer CPP-Datei statt in den Header-Datei auch LNK2019 erhalten. Die Header-Datei enthalten ist überall als geeignet eingestuft, aber die Funktionen sind nur inline, wenn der Compiler; die CPP-Datei durchläuft Daher erkennt der Linker die Funktionen als nicht aufgelösten externen bei der Verwendung in anderen Modulen ausgeführt werden.  
  
```  
// LNK2019_FIP.h  
struct testclass {  
   void PublicStatMemFunc1(void);  
};  
```  
  
 Und dann  
  
```  
// LNK2019_FIP.cpp  
// compile with: /c  
#include "LNK2019_FIP.h"  
inline void testclass::PublicStatMemFunc1(void) {}  
```  
  
 Und dann  
  
```  
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
  
## <a name="see-also"></a>Siehe auch  
 [Linkertoolfehler LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)