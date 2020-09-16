---
title: Linkertoolfehler LNK1313
ms.date: 11/04/2016
f1_keywords:
- LNK1313
helpviewer_keywords:
- LNK1313
ms.assetid: 5df0b72e-bb3f-428c-8d84-6084238f9827
ms.openlocfilehash: 03ff61a1f3501b3ea106138e957a657ed064e645
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90683441"
---
# <a name="linker-tools-error-lnk1313"></a>Linkertoolfehler LNK1313

> IJW/Native-Modul gefunden; kann mit reinen Modulen nicht verknüpft werden

## <a name="remarks"></a>Bemerkungen

Die aktuelle Version von Visual C++ unterstützt nicht das Verknüpfen von systemeigenen oder gemischten verwalteten/nativen. obj-Dateien mit mit **/clr: pure**kompilierten OBJ-Dateien.

Die **/clr: pure** -Compileroption ist in Visual Studio 2015 veraltet und wird in Visual Studio 2017 nicht unterstützt.

## <a name="examples"></a>Beispiele

```cpp
// LNK1313.cpp
// compile with: /c /clr:pure
// a pure module
int main() {}
```

```cpp
// LNK1313_b.cpp
// compile with: /c /clr
// an IJW module
void test(){}
```

Im folgende Beispiel wird LNK1313 generiert.

```cpp
// LNK1313_c.cpp
// compile with: /link LNK1313.obj LNK1313_b.obj
// LNK1313 warning expected
```
