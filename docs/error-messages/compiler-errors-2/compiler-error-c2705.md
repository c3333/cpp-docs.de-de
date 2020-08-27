---
title: Compilerfehler C2705
description: Beschreibt den Microsoft C/C++-Compilerfehler C2705.
ms.date: 08/25/2020
f1_keywords:
- C2705
helpviewer_keywords:
- C2705
ms.assetid: 29249ea3-4ea7-4105-944b-bdb83e8d6852
ms.openlocfilehash: 40d0f70ee379f5d1347b7443817713a53e097f89
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898752"
---
# <a name="compiler-error-c2705"></a>Compilerfehler C2705

> '*Bezeichnung*': Unzulässiger Sprung in den Bereich für den Ausnahmehandlerblock.

## <a name="remarks"></a>Hinweise

Die Ausführung springt zu einer Bezeichnung innerhalb eines- **`try`** / **`catch`** ,- **`__try`** / **`__except`** oder- **`__try`** / **`__finally`** Blocks. Der Compiler lässt dieses Verhalten nicht zu. Weitere Informationen finden Sie unter [Ausnahmebehandlung](../../cpp/exception-handling-in-visual-cpp.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2705 generiert:

```cpp
// C2705.cpp
int main() {
goto trouble;
   __try {
      trouble: ;   // C2705
   }
   __finally {}

   // try the following line instead
   // trouble: ;
}
```
