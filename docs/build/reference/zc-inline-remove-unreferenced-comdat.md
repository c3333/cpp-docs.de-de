---
title: /Zc:inline (unreferenzierte COMDAT entfernen)
ms.date: 09/05/2019
f1_keywords:
- /Zc:inline
- VC.Project.VCCLCompilerTool.RemoveUnreferencedCodeData
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
- /Zc:inline
ms.assetid: a4c94224-1d73-4bea-a9d5-4fa73dc924df
ms.openlocfilehash: 290252262254521c024d7b0d6355472199d1f55d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218961"
---
# <a name="zcinline-remove-unreferenced-comdat"></a>/Zc:inline (unreferenzierte COMDAT entfernen)

Entfernt nicht referenzierte Daten oder Funktionen, die COMDATs sind oder nur über eine interne Verknüpfung verfügen. Unter **/Zc: Inline**gibt der Compiler an, dass Übersetzungseinheiten mit Inline Daten oder Funktionen auch ihre Definitionen einschließen müssen.

## <a name="syntax"></a>Syntax

> **/Zc: Inline**[ **-** ]

## <a name="remarks"></a>Bemerkungen

Wenn **/Zc: Inline** angegeben wird, gibt der Compiler keine Symbol Informationen für nicht referenzierte COMDAT-Funktionen oder-Daten aus. Oder für Daten oder Funktionen, die nur über interne Verknüpfungen verfügen. Diese Optimierung vereinfacht einige der Aufgaben, die der Linker in Releasebuilds durchführt, oder wenn Sie die Linkeroption [/OPT: Ref](opt-optimizations.md) angeben. Diese Compileroptimierung kann die Größe der obj-Datei erheblich reduzieren und die Linker-Geschwindigkeit verbessern. Die-Compileroption ist nicht aktiviert, wenn Sie Optimierungen deaktivieren ([/od](od-disable-debug.md)). Oder, wenn Sie [/GL (Optimierung des ganzen Programms)](gl-whole-program-optimization.md)angeben.

Standardmäßig ist diese Option deaktiviert (**/Zc: Inline-**) in Befehlszeilenbuilds. Die [/permissive-](permissive-standards-conformance.md) -Option aktiviert **/Zc: Inline**nicht. In MSBuild-Projekten wird die-Option durch die **Konfigurations Eigenschaften**  >  **C/C++**  >  **Language**  >  **Remove unreferenzierten Code und die Daten** Eigenschaft festgelegt, die standardmäßig auf **Yes** festgelegt ist.

Wenn **/Zc: Inline** angegeben ist, erzwingt der Compiler die c++ 11-Anforderung, dass alle deklarierten Funktionen über **`inline`** eine Definition verfügen müssen, die in derselben Übersetzungseinheit verfügbar ist, wenn Sie verwendet werden. Wenn die Option nicht angegeben wird, lässt der Microsoft-Compiler nicht kompatiblen Code zu, der Funktionen aufruft, die auch dann deklariert werden, **`inline`** Wenn keine Definition sichtbar ist. Weitere Informationen finden Sie unter „C++11-Standard“ in den Abschnitten 3.2 und 7.1.2. Diese Compileroption wurde in Visual Studio 2013 Update 2 eingeführt.

Aktualisieren Sie den nicht kompatiblen Code, um die **/Zc: Inline** -Option zu verwenden.

Dieses Beispiel zeigt, wie die nicht kompatible Verwendung einer Inline Funktionsdeklaration ohne Definition weiterhin kompiliert und verknüpft wird, wenn die standardmäßige **/Zc: Inline-** Option verwendet wird:

```cpp
// example.h
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp
#pragma once

class Example {
public:
   inline void inline_call(); // declared but not defined inline
   void normal_call();
   Example() {};
};
```

```cpp
// example.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp
#include <stdio.h>
#include "example.h"

void Example::inline_call() {
   printf("inline_call was called.\n");
}

void Example::normal_call() {
   printf("normal_call was called.\n");
   inline_call(); // with /Zc:inline-, inline_call forced into .obj file
}
```

```cpp
// zcinline.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp
#include "example.h"

int main() {
   Example example;
   example.inline_call(); // normal call when definition unavailable
}
```

Wenn **/Zc: Inline** aktiviert ist, verursacht derselbe Code einen [LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md) -Fehler, da der Compiler keinen nicht Inline-Code Körper für `Example::inline_call` in example. obj ausgibt. Dies bewirkt, dass der nicht-Inline-Aufrufvorgang in `main` auf ein nicht definiertes externes Symbol verweist.

Um diesen Fehler zu beheben, können Sie das- **`inline`** Schlüsselwort aus der Deklaration von entfernen `Example::inline_call` , die Definition von `Example::inline_call` in die Header Datei verschieben oder die Implementierung von `Example` in "Main. cpp" verschieben. Im nächsten Beispiel wird die Definition in die Headerdatei verschoben, in der sie für jeden Aufrufer sichtbar ist, der den Header enthält.

```cpp
// example2.h
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp
#pragma once
#include <stdio.h>

class Example2 {
public:
   inline void inline_call() {
      printf("inline_call was called.\n");
   }
   void normal_call();
   Example2() {};
};
```

```cpp
// example2.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp
#include "example2.h"

void Example2::normal_call() {
   printf("normal_call was called.\n");
   inline_call();
}
```

```cpp
// zcinline2.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp
#include "example2.h"

int main() {
   Example2 example2;
   example2.inline_call(); // normal call when definition unavailable
}
```

Weitere Informationen über Konformitätsprobleme in Visual C++ finden Sie unter [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Sprache** aus.

1. Ändern Sie die Eigenschaft **nicht referenzierten Code und die Daten entfernen** , und klicken Sie dann auf **OK**.

## <a name="see-also"></a>Weitere Informationen

[/Zc (Übereinstimmung)](zc-conformance.md)<br/>
