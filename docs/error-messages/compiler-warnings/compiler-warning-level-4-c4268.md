---
title: Compilerwarnung (Stufe 4) C4268
ms.date: 11/04/2016
f1_keywords:
- C4268
helpviewer_keywords:
- C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
ms.openlocfilehash: 1db8f67591560c130bc25c40c63232f54b3b7884
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219910"
---
# <a name="compiler-warning-level-4-c4268"></a>Compilerwarnung (Stufe 4) C4268

' Identifier ': ' Konstante ' statische/globale Daten, die mit dem vom Compiler generierten Standardkonstruktor initialisiert wurden, füllen das Objekt mit Nullen

Eine **`const`** globale oder statische Instanz einer nicht trivialen Klasse wird mit einem vom Compiler generierten Standardkonstruktor initialisiert.

## <a name="example"></a>Beispiel

```cpp
// C4268.cpp
// compile with: /c /LD /W4
class X {
public:
   int m_data;
};

const X x1;   // C4268
```

Da diese Instanz der-Klasse ist **`const`** , kann der Wert von `m_data` nicht geändert werden.
