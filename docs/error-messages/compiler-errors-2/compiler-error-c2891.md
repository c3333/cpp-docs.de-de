---
title: Compilerfehler C2891
ms.date: 11/04/2016
f1_keywords:
- C2891
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
ms.openlocfilehash: 2544cfc9e8cff283a7c3e0ace499408bb84cd046
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201635"
---
# <a name="compiler-error-c2891"></a>Compilerfehler C2891

"Parameter": die Adresse eines Vorlagen Parameters kann nicht übernommen werden.

Sie können die Adresse eines Vorlagen Parameters nur dann übernehmen, wenn es sich um einen lvalue handelt. Typparameter sind keine Lvalues, da Sie keine Adresse aufweisen. Nicht-Typwerte in Vorlagen Parameterlisten, bei denen es sich nicht um Lvalues handelt, verfügen auch nicht über eine Adresse. Dies ist ein Beispiel für Code, der Compilerfehler C2891 verursacht, da der als Vorlagen Parameter übergebener Wert eine vom Compiler generierte Kopie des Vorlagen Arguments ist.

```
template <int i> int* f() { return &i; }
```

Bei Vorlagen Parametern, bei denen es sich um Lvalues handelt, z. b. Verweis Typen, kann Ihre Adresse übernommen werden

```
template <int& r> int* f() { return &r; }
```

Um diesen Fehler zu beheben, nehmen Sie die Adresse eines Vorlagen Parameters nur dann an, wenn es sich um einen lvalue handelt.
