---
title: Linkertoolwarnung LNK4224
ms.date: 11/04/2016
f1_keywords:
- LNK4224
helpviewer_keywords:
- LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
ms.openlocfilehash: 9e52dd533d897e729aba5f2b43ea6c019a024d43
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182980"
---
# <a name="linker-tools-warning-lnk4224"></a>Linkertoolwarnung LNK4224

> die *Option* wird nicht mehr unterstützt. erten

## <a name="remarks"></a>Bemerkungen

Es wurde eine ungültige, veraltete Linkeroption angegeben und ignoriert.

Beispielsweise kann Linkertoolwarnung Lnk4224 auftreten, wenn eine/comment-Direktive in. obj angezeigt wird. Die/comment-Direktive würde über das [comment-Pragma (C++C/)](../../preprocessor/comment-c-cpp.md) mithilfe der veralteten exestr-Option hinzugefügt worden sein. Verwenden Sie (dumpbin [/all](../../build/reference/all.md) , um die Linker-Direktiven in einer OBJ-Datei anzuzeigen.

Ändern Sie nach Möglichkeit die Quelle für die OBJ-Datei, und entfernen Sie das Pragma. Wenn Sie diese Warnung ignorieren, ist es möglich, dass eine mit **/clr: pure** kompilierte ausführbare Datei nicht erwartungsgemäß ausgeführt wird. Die **/clr: pure** -Compileroption ist in Visual Studio 2015 veraltet und wird in Visual Studio 2017 nicht unterstützt.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird Linkertoolwarnung Lnk4224 generiert.

```cpp
// LNK4224.cpp
// compile with: /c /Zi
// post-build command: link LNK4224.obj /debug /debugtype:map
int main () {
   return 0;
}
```
