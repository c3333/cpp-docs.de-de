---
title: Compilerwarnung (Stufe 1) C4312
ms.date: 11/04/2016
f1_keywords:
- C4312
helpviewer_keywords:
- C4312
ms.assetid: 541906ed-4f62-4bcb-947f-cf9ae7411bcb
ms.openlocfilehash: 379803260492449da4985e62d36750f121b4e7fa
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233261"
---
# <a name="compiler-warning-level-1-c4312"></a>Compilerwarnung (Stufe 1) C4312

'Operation': Konvertierung von 'Typ1' in größeren Typ 'Typ2'

Diese Warnung erkennt den Versuch, einem 64-Bit-Zeigertyp einen 32-Bit-Wert zuzuweisen, z. b. das Umwandeln eines 32-Bit-Werts **`int`** oder **`long`** eines 64-Bit-Zeigers.

Dabei kann es sich um eine unsichere Konvertierung auch für Zeigerwerte handeln, die in 32 Bits passen, wenn die Vorzeichenerweiterung vorhanden ist. Wenn eine negative 32-Bit-Ganzzahl einem 64-Bit-Zeigertyp zugeordnet wird, verweist der Zeigerwert aufgrund der Vorzeichenerweiterung auf eine Speicheradresse, die sich vom Wert der Ganzzahl unterscheidet.

Diese Warnung wird nur für 64-Bit-Kompilierungsziele ausgegeben. Weitere Informationen finden Sie unter [Regeln für die Verwendung von Zeigern](/windows/win32/WinProg64/rules-for-using-pointers).

Im folgenden Codebeispiel wird C4312 generiert, wenn dies für 64-Bit-Ziele kompiliert wird:

```cpp
// C4312.cpp
// compile by using: cl /W1 /LD C4312.cpp
void* f(int i) {
   return (void*)i;   // C4312 for 64-bit targets
}

void* f2(__int64 i) {
   return (void*)i;   // OK
}
```
