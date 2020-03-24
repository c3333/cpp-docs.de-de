---
title: Compilerwarnung (Stufe 1) C4772
ms.date: 11/04/2016
f1_keywords:
- C4772
helpviewer_keywords:
- C4772
ms.assetid: dafe6fd8-9faf-41f5-9d66-a55838742c14
ms.openlocfilehash: 89156b2f29fd21160e6abddc3ecb21efaee6dde1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175130"
---
# <a name="compiler-warning-level-1-c4772"></a>Compilerwarnung (Stufe 1) C4772

> \#Import hat auf einen Typ aus einer fehlenden Typbibliothek verwiesen. "*Missing-Type*" wird als Platzhalter verwendet.

Auf eine Typbibliothek wurde mit der [#Import](../../preprocessor/hash-import-directive-cpp.md) -Direktive verwiesen. Allerdings enthielt die Typbibliothek einen Verweis auf eine andere Typbibliothek, auf die mit `#import`nicht verwiesen wurde. Diese andere TLB-Datei wurde vom Compiler nicht gefunden.

Beachten Sie, dass der Compiler Typbibliotheken nicht in verschiedenen Verzeichnissen findet, wenn Sie die Compileroption [/I (Zusätzliche Includeverzeichnisse)](../../build/reference/i-additional-include-directories.md) verwenden, um diese Verzeichnisse anzugeben. Wenn der Compiler Typbibliotheken in verschiedenen Verzeichnissen finden soll, fügen Sie diese Verzeichnisse der PATH-Umgebungsvariablen hinzu.

Diese Warnung wird standardmäßig als Fehler ausgegeben. C4772 kann nicht mit/W0. unterdrückt werden.

## <a name="example"></a>Beispiel

Dies ist die erste Typbibliothek, die benötigt wird, um C4772 zu reproduzieren.

```IDL
// c4772a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library C4772aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c100")]
   enum E_C4772a
   {
      one, two, three
   };
};
```

Dies ist die zweite Typbibliothek, die benötigt wird, um C4772 zu reproduzieren.

```IDL
// c4772b.idl
// post-build command: del /f C4772a.tlb
// C4772a.tlb is available when c4772b.tlb is built
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
library C4772bLib
{
   importlib ("c4772a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
   struct S_C4772b
   {
      enum E_C4772a e;
   };
};
```

Im folgenden Beispiel wird C4772 generiert:

```cpp
// C4772.cpp
// assumes that C4772a.tlb is not available to the compiler
// #import "C4772a.tlb"
#import "C4772b.tlb"   // C4772 uncomment previous line to resolve
                       // and make sure c4772a.tlb is on disk
```
