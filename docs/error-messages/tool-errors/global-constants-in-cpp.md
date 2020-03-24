---
title: Globale Konstanten in C++
ms.date: 11/04/2016
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
ms.openlocfilehash: cabe5e92a496181d60536d7274eca388aba5c068
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195473"
---
# <a name="global-constants-in-c"></a>Globale Konstanten in C++

C++Globale Konstanten haben eine statische Verknüpfung. Dies unterscheidet sich von C. Wenn Sie versuchen, eine globale Konstante in C++ mehreren Dateien zu verwenden, erhalten Sie einen nicht aufgelösten externen Fehler. Der Compiler optimiert globale Konstanten und gibt keinen Speicherplatz für die Variable reserviert.

Eine Möglichkeit, diesen Fehler zu beheben, besteht darin, die Konstanten Initialisierungen in eine Header Datei einzufügen und diesen Header bei Bedarf in die CPP-Dateien einzubeziehen, als wäre es ein Funktionsprototyp. Eine andere Möglichkeit besteht darin, die Variable als nicht konstant zu gestalten und bei der Bewertung einen konstanten Verweis zu verwenden.

Im folgenden Beispiel wird C2019 generiert:

```cpp
// global_constants.cpp
// LNK2019 expected
void test(void);
const int lnktest1 = 0;

int main() {
   test();
}
```

und anschließend

```cpp
// global_constants_2.cpp
// compile with: global_constants.cpp
extern int lnktest1;

void test() {
  int i = lnktest1;   // LNK2019
}
```

## <a name="see-also"></a>Weitere Informationen

[Linkertoolfehler LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)
