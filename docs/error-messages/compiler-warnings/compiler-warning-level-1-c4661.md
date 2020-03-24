---
title: Compilerwarnung (Stufe 1) C4661
ms.date: 11/04/2016
f1_keywords:
- C4661
helpviewer_keywords:
- C4661
ms.assetid: 603bb8b7-356d-4eef-924b-64d769bac5bd
ms.openlocfilehash: 43a3287787f831db23423412a9baf959929adfae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199460"
---
# <a name="compiler-warning-level-1-c4661"></a>Compilerwarnung (Stufe 1) C4661

"Bezeichner": für die explizite Vorlagen Instanziierung-Anforderung wurde keine passende Definition bereitgestellt.

Ein Member der Vorlagen Klasse ist nicht definiert.

## <a name="example"></a>Beispiel

```cpp
// C4661.cpp
// compile with: /W1 /LD
template<class T> class MyClass {
public:
   void i();   // declaration but not definition
};
template MyClass< int >;  // C4661
```
