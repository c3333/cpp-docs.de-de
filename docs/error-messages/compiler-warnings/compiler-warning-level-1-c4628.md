---
title: Compilerwarnung (Stufe 1) C4628
ms.date: 11/04/2016
f1_keywords:
- C4628
helpviewer_keywords:
- C4628
ms.assetid: 20fdc6f8-5f6a-40cc-aff8-c7ccf3d8ec26
ms.openlocfilehash: affb2b5231d3745d4826e92657e355ec99570e7e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199666"
---
# <a name="compiler-warning-level-1-c4628"></a>Compilerwarnung (Stufe 1) C4628

'digraphs' werden mit '-Ze' nicht unterstützt. Die Zeichensequenz 'Digraph' wird nicht als alternativer Token für 'Zeichen' interpretiert.

Digraphen werden unter [/Ze](../../build/reference/za-ze-disable-language-extensions.md)nicht unterstützt. Auf diese Warnung folgt ein Fehler.

Diese Warnung ist standardmäßig deaktiviert. Weitere Informationen finden Sie unter [Standardmäßig deaktivierte Compilerwarnungen](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Im folgenden Beispiel wird C4628 generiert:

```cpp
// C4628.cpp
// compile with: /WX
#pragma warning(default : 4628)
int main()
<%   // C4628 <% digraph for {
}
```
