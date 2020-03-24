---
title: Compilerfehler C2857
ms.date: 09/13/2018
f1_keywords:
- C2857
helpviewer_keywords:
- C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
ms.openlocfilehash: 11b620f9748ac85e731d79b0652c0392375b2ea4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201850"
---
# <a name="compiler-error-c2857"></a>Compilerfehler C2857

> die mit der/YC*filename* -Befehlszeilenoption angegebene ' #include '-Anweisung wurde in der Quelldatei nicht gefunden.

Die Option [/Yc](../../build/reference/yc-create-precompiled-header-file.md) gibt den Namen einer Include-Datei an, die nicht in der zu kompilierenden Quelldatei enthalten ist.

## <a name="remarks"></a>Bemerkungen

Wenn Sie die Option **/Yc**<em>filename</em> für eine Quelldatei verwenden, um eine vorkompilierte Header Datei (PCH) zu erstellen, muss diese Quelldatei die Datei *Namen* Header Datei enthalten. Alle Dateien, die in der Quelldatei enthalten sind, einschließlich des angegebenen Datei *namens*, sind in der PCH-Datei enthalten. In anderen Quelldateien, die mit der **/Yu**<em>filename</em> -Option kompiliert wurden, um die PCH-Datei zu verwenden, muss der *Dateiname "filename* " die erste nicht-Kommentarzeile in der Datei sein. Der Compiler ignoriert vor diesem einschließen alles in der Quelldatei.

Dieser Fehler kann durch eine `#include "filename"` Anweisung in einem Block für die bedingte Kompilierung verursacht werden, der nicht in der PCH-Quelldatei kompiliert wird.

## <a name="example"></a>Beispiel

Bei der typischen Verwendung wird eine Quelldatei in Ihrem Projekt als PCH-Quelldatei festgelegt, und eine Header Datei wird als PCH-Header Datei verwendet. Eine typische PCH-Header Datei enthält alle Bibliotheks Header, die in Ihrem Projekt verwendet werden, aber keine lokalen Header, die sich noch in der Entwicklung befinden. In diesem Beispiel hat die PCH-Header Datei den Namen *my_pch. h*.

```cpp
// my_pch.h
#pragma once
#include <stdio.h>
```

Die PCH-Quelldatei wird mithilfe der Option **/Yc**<em>my_pch. h</em> kompiliert. Wenn der Compiler keinen include-Vorgang für diese PCH-Header Datei findet, generiert er C2857:

```cpp
// my_pch.cpp
// Compile by using: cl /EHsc /W4 /Yumy_pch.h /c my_pch.cpp

#if 0
#include "my_pch.h"  // C2857; remove conditional directives to fix
#endif
```

Um diese PCH-Datei zu verwenden, müssen Quelldateien mit der Option **/Yu**<em>my_pch. h</em> kompiliert werden. Die PCH-Header Datei muss zuerst in Quelldateien eingeschlossen werden, die den PCH verwenden:

```cpp
// C2857.cpp
// Compile my_pch.cpp first, then
// compile by using: cl /EHsc /W4 /Yumy_pch.h my_project.cpp my_pch.obj
// Include the pch header before any other non-comment line
#include "my_pch.h"

int main()
{
    puts("Using a precompiled header file.\n");
}
```
