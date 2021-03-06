---
title: Linkertoolfehler LNK2022
ms.date: 11/04/2016
f1_keywords:
- LNK2022
helpviewer_keywords:
- LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
ms.openlocfilehash: 187a63cb4bd22fc5e0d35523d97f438ba56b8576
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686357"
---
# <a name="linker-tools-error-lnk2022"></a>Linkertoolfehler LNK2022

> Fehler beim Metadatenvorgang (*HRESULT*): *ERROR_MESSAGE*

Der Linker hat beim Zusammenführen von Metadaten einen Fehler festgestellt. Die Metadatenfehler müssen aufgelöst werden, damit Sie erfolgreich verknüpft werden können.

Eine Möglichkeit, dieses Problem zu diagnostizieren, besteht darin, **Ildasm-Tokens** für die Objektdateien auszuführen, um zu ermitteln, in welchen Typen die Token aufgelistet sind `error_message` , und nach Unterschieden zu suchen.  In Metadaten sind zwei verschiedene Typen mit dem gleichen Namen nicht gültig, auch wenn das Attribut "nur LayoutType" unterschiedlich ist.

Ein Grund für Linkertoolfehler LNK2022 ist, wenn ein Typ (z. b. eine Struktur) in mehreren Kompilierungen mit dem gleichen Namen vorhanden ist, jedoch mit in Konflikt stehenden Definitionen und bei der Kompilierung mit [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  Stellen Sie in diesem Fall sicher, dass der Typ in allen Kompilierungen über eine identische Definition verfügt.  Der Typname ist in aufgeführt `error_message` .

Eine weitere mögliche Ursache für Linkertoolfehler LNK2022 ist, wenn der Linker eine Metadatendatei an einem anderen Speicherort findet, als für den Compiler angegeben wurde (mit [#using](../../preprocessor/hash-using-directive-cpp.md) ). Stellen Sie sicher, dass sich die Metadatendatei (. dll oder. netmodule) am gleichen Speicherort befindet, wenn Sie an den Linker übermittelt wird, wie Sie an den Compiler übermittelt wurde.

Beim Erstellen einer ATL-Anwendung ist die Verwendung des Makros `_ATL_MIXED` in allen Kompilierungen erforderlich, wenn es in mindestens einem verwendet wird.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird ein leerer Typ definiert.

```cpp
// LNK2022_a.cpp
// compile with: /clr /c
public ref class Test {};
```

Dieses Beispiel zeigt, dass Sie nicht zwei Quell Code Dateien verknüpfen können, die Typen mit demselben Namen, aber unterschiedlichen Definitionen enthalten.

Im folgenden Beispiel wird Linkertoolfehler LNK2022 generiert.

```cpp
// LNK2022_b.cpp
// compile with: LNK2022_a.cpp /clr /LD
// LNK2022 expected
public ref class Test {
   void func() {}
   int var;
};
```
