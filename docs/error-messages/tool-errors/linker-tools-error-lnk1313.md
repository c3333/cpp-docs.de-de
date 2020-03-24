---
title: Linkertoolfehler LNK1313
ms.date: 11/04/2016
f1_keywords:
- LNK1313
helpviewer_keywords:
- LNK1313
ms.assetid: 5df0b72e-bb3f-428c-8d84-6084238f9827
ms.openlocfilehash: a2314f160dc6add45547082c7804ec5e2c8f2349
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194862"
---
# <a name="linker-tools-error-lnk1313"></a>Linkertoolfehler LNK1313

> IJW/Native-Modul gefunden; kann mit reinen Modulen nicht verknüpft werden

## <a name="remarks"></a>Bemerkungen

Die aktuelle Version von Visual C++ unterstützt das Verknüpfen von systemeigenen oder gemischten verwalteten/systemeigenen. obj-Dateien mit mit **/clr: pure**kompilierten OBJ-Dateien nicht.

Die **/clr: pure** -Compileroption ist in Visual Studio 2015 veraltet und wird in Visual Studio 2017 nicht unterstützt.

## <a name="example"></a>Beispiel

```cpp
// LNK1313.cpp
// compile with: /c /clr:pure
// a pure module
int main() {}
```

## <a name="example"></a>Beispiel

```cpp
// LNK1313_b.cpp
// compile with: /c /clr
// an IJW module
void test(){}
```

## <a name="example"></a>Beispiel

Im folgende Beispiel wird LNK1313 generiert.

```cpp
// LNK1313_c.cpp
// compile with: /link LNK1313.obj LNK1313_b.obj
// LNK1313 warning expected
```
