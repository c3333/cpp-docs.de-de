---
title: Compilerfehler C2094
ms.date: 11/04/2016
f1_keywords:
- C2094
helpviewer_keywords:
- C2094
ms.assetid: 9e4f8f88-f189-46e7-91c9-481bacc7af87
ms.openlocfilehash: 022fca01706fefca2a14ea952586ec91b0c5b240
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80207678"
---
# <a name="compiler-error-c2094"></a>Compilerfehler C2094

Bezeichnung "identifier" nicht definiert

Die von einer [goto](../../cpp/goto-statement-cpp.md) -Anweisung verwendete Bezeichnung ist in der Funktion nicht vorhanden.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2094 generiert:

```cpp
// C2094.c
int main() {
   goto test;
}   // C2094
```

Mögliche Lösung:

```cpp
// C2094b.c
int main() {
   goto test;
   test:
   {
   }
}
```
