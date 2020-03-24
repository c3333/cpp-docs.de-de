---
title: Linkertoolwarnung LNK4217
ms.date: 07/23/2019
f1_keywords:
- LNK4217
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
ms.openlocfilehash: 1ce410312493b353bb68ea7264fce9cd6a394e0d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183110"
---
# <a name="linker-tools-warning-lnk4217"></a>Linkertoolwarnung LNK4217

> das Symbol '*Symbol*', das in '*filename_1. obj*' definiert ist, wird von '*filename_2. obj*' in Funktion '*Function*' importiert.

[__declspec (dllimport)](../../cpp/dllexport-dllimport.md) wurde für ein Symbol angegeben, obwohl das Symbol in einer Objektdatei im selben Bild definiert ist. Entfernen Sie den `__declspec(dllimport)` Modifizierer, um diese Warnung zu beheben.

## <a name="remarks"></a>Bemerkungen

*Symbol* ist der Symbol Name, der innerhalb des Bilds definiert ist. *Funktion* ist die Funktion, die das Symbol importiert.

Diese Warnung wird nicht angezeigt, wenn Sie mit der [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) -Option kompilieren.

Linkertoolwarnung LNK4217 kann auch auftreten, wenn Sie versuchen, zwei Module miteinander zu verknüpfen, wenn Sie stattdessen das zweite Modul mit der Import Bibliothek des ersten Moduls kompilieren müssen.

```cpp
// main.cpp
__declspec(dllimport) void func();

int main()
{
    func();
    return 0;
}

```

und anschließend

```cpp
// tt.cpp
// compile with: /c
void func() {}
```

Der Versuch, diese beiden Module zu kompilieren, wie hier gezeigt, führt zu Linkertoolwarnung LNK4217:

```cmd
cl.exe /c main.cpp tt.cpp
link.exe main.obj tt.obj
```

Um den Fehler zu beheben, übergeben Sie nach dem Kompilieren der beiden Dateien TT. obj an lib. exe, um eine LIB-Datei zu erstellen, und verknüpfen Sie anschließend Main. obj mit TT. lib, wie hier gezeigt:

```cmd
cl.exe /c main.cpp tt.cpp
lib.exe tt.obj /export:func /def
link.exe main.obj tt.lib
```

## <a name="see-also"></a>Weitere Informationen

[Warnmeldungen für Linker-Tools Linkertoolwarnung LNK4049](linker-tools-warning-lnk4049.md) \
[Warnmeldungen für Linker-Tools LNK4286](linker-tools-warning-lnk4286.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)
