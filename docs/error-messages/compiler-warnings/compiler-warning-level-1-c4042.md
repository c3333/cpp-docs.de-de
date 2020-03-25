---
title: Compilerwarnung (Stufe 1) C4042
ms.date: 11/04/2016
f1_keywords:
- C4042
helpviewer_keywords:
- C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
ms.openlocfilehash: 0ffc4c4aeb7d37ffa45f503a34fd369d36c00ce4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164208"
---
# <a name="compiler-warning-level-1-c4042"></a>Compilerwarnung (Stufe 1) C4042

"Identifier": weist eine ungültige Speicher Klasse auf.

Die angegebene Speicher Klasse kann in diesem Kontext nicht mit diesem Bezeichner verwendet werden. Der Compiler verwendet stattdessen die Standard Speicher Klasse:

- `extern`, wenn der *Bezeichner* eine Funktion ist.

- **Auto**, wenn der *Bezeichner* ein formaler Parameter oder eine lokale Variable ist.

- Keine Speicher Klasse, wenn der *Bezeichner* eine globale Variable ist.

Diese Warnung kann dadurch verursacht werden, dass eine andere Speicher Klasse als " **Register** " in einer Parameter Deklaration angegeben wird.

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
