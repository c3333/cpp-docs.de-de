---
title: Compilerwarnung (Stufe 3) C4278
ms.date: 08/27/2018
f1_keywords:
- C4278
helpviewer_keywords:
- C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
ms.openlocfilehash: 7994ae05d6cb16b5ddc9775b1044de7f3a22d542
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174231"
---
# <a name="compiler-warning-level-3-c4278"></a>Compilerwarnung (Stufe 3) C4278

> "*Bezeichner*": der Bezeichner in der Typbibliothek "*tlb*" ist bereits ein Makro. "Rename"-Qualifizierer verwenden

Wenn Sie [#Import](../../preprocessor/hash-import-directive-cpp.md)verwenden, versucht ein Bezeichner in der Typbibliothek, die Sie importieren, einen bezeichnerbezeichner zu deklarieren. *identifier* Dies ist jedoch bereits ein gültiges Symbol.

Verwenden Sie das `#import` **Rename** -Attribut, um dem Symbol in der Typbibliothek einen Alias zuzuweisen.
