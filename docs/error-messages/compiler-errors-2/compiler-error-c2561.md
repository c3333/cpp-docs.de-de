---
title: Compilerfehler C2561
ms.date: 11/04/2016
f1_keywords:
- C2561
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
ms.openlocfilehash: 9c42a2da662a286f3e6887f6a1dba381687136bf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87206964"
---
# <a name="compiler-error-c2561"></a>Compilerfehler C2561

"Bezeichner": die Funktion muss einen Wert zurückgeben.

Die Funktion wurde als Rückgabe eines Werts deklariert, aber die Funktionsdefinition enthält keine- **`return`** Anweisung.

Dieser Fehler kann durch einen falschen Funktionsprototyp verursacht werden:

1. Wenn die Funktion keinen Wert zurückgibt, deklarieren Sie die Funktion mit dem Rückgabetyp [void](../../cpp/void-cpp.md).

1. Überprüfen Sie, ob alle möglichen Verzweigungen der Funktion einen Wert des im Prototyp deklarierten Typs zurückgeben.

1. C++-Funktionen, die Inline-Assemblyroutinen enthalten, die den Rückgabewert im Register speichern, `AX` benötigen möglicherweise eine Return-Anweisung Kopieren Sie den Wert in `AX` eine temporäre Variable, und geben Sie diese Variable von der-Funktion zurück.

Im folgenden Beispiel wird C2561 generiert:

```cpp
// C2561.cpp
int Test(int x) {
   if (x) {
      return;   // C2561
      // try the following line instead
      // return 1;
   }
   return 0;
}

int main() {
   Test(1);
}
```
