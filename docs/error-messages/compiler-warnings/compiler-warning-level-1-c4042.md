---
title: Compilerwarnung (Stufe 1) C4042
ms.date: 11/04/2016
f1_keywords:
- C4042
helpviewer_keywords:
- C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
ms.openlocfilehash: cd8d8addb8441bd32d242c4f4858104048f7a62e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87197071"
---
# <a name="compiler-warning-level-1-c4042"></a>Compilerwarnung (Stufe 1) C4042

"Identifier": weist eine ungültige Speicher Klasse auf.

Die angegebene Speicher Klasse kann in diesem Kontext nicht mit diesem Bezeichner verwendet werden. Der Compiler verwendet stattdessen die Standard Speicher Klasse:

- **`extern`**, wenn der *Bezeichner* eine Funktion ist.

- **`auto`**, wenn der *Bezeichner* ein formaler Parameter oder eine lokale Variable ist.

- Keine Speicher Klasse, wenn der *Bezeichner* eine globale Variable ist.

Diese Warnung kann dadurch verursacht werden, dass eine andere Speicher Klasse als **`register`** in einer Parameter Deklaration angegeben wird.

Im folgenden Beispiel wird C4042 generiert.

```cpp
// C4042.cpp
// compile with: /W1 /LD
int func2( __declspec( thread ) int tls_i )    // C4042
// try the following line instead
// int func2( int tls_i )
{
   return tls_i;
}
```
