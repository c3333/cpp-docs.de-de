---
title: Compilerfehler C2720
ms.date: 11/04/2016
f1_keywords:
- C2720
helpviewer_keywords:
- C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
ms.openlocfilehash: 24f4329ee631eafc7c2670d9ebf28609c22e7592
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202132"
---
# <a name="compiler-error-c2720"></a>Compilerfehler C2720

> "*Bezeichner*": der Speicherklassenspezifizierer "*Spezifizierer*" ist für Member unzulässig.

Die Speicherklasse kann für Klassenmember außerhalb der Variablendeklaration verwendet werden. Um diesen Fehler zu beheben, entfernen Sie den nicht benötigten [Speicherklassenspezifizierer](../../cpp/storage-classes-cpp.md) aus der Definition des Members außerhalb der Klassen Deklaration.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2720 generiert und gezeigt, wie Sie diesen Fehler beheben:

```cpp
// C2720.cpp
struct S {
   static int i;
};
static S::i;   // C2720 - remove the unneeded 'static' to fix it
```
