---
title: Compilerwarnung (Stufe 1) C4117
ms.date: 11/04/2016
f1_keywords:
- C4117
helpviewer_keywords:
- C4117
ms.assetid: c45aa281-4cc1-4dfd-bd32-bd7a60ddd577
ms.openlocfilehash: 2474645a555748b559b1661a2b5327ca1b83e534
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176377"
---
# <a name="compiler-warning-level-1-c4117"></a>Compilerwarnung (Stufe 1) C4117

Makroname 'Name' ist reserviert. 'Befehl' wird ignoriert.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. Versuchen Sie, ein vordefiniertes Makro zu definieren bzw. dessen Definition aufzuheben.

1. Versuchen Sie, den **defined**-Präprozessoroperator zu definieren bzw. dessen Definition aufzuheben.

Im folgenden Beispiel wird C4117 generiert:

```cpp
// C4117.cpp
// compile with: /W1
#define __FILE__ test         // C4117. __FILE__ is a predefined macro
#define ValidMacroName test   // ok

int main() {
}
```
