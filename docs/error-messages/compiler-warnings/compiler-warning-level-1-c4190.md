---
title: Compilerwarnung (Stufe 1) C4190
ms.date: 11/04/2016
f1_keywords:
- C4190
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
ms.openlocfilehash: 8187926f2477a4d3f1ca3019cc8c3c71710c1dff
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233300"
---
# <a name="compiler-warning-level-1-c4190"></a>Compilerwarnung (Stufe 1) C4190

für "Bezeichner1" wurde eine C-Verknüpfung angegeben, es wird jedoch der UDT "Bezeichner2" zurückgegeben, der nicht mit C kompatibel ist

Eine Funktion oder ein Zeiger auf die Funktion verfügt über einen UDT (benutzerdefinierter Typ, d. h. eine Klasse, Struktur, Enumeration oder Union) als Rückgabetyp und `extern "C"` Verknüpfung. Dies ist zulässig, wenn Folgendes gilt:

- Alle Aufrufe dieser Funktion treten von C++ auf.

- Die Definition der Funktion befindet sich in C++.

## <a name="example"></a>Beispiel

```cpp
// C4190.cpp
// compile with: /W1 /LD
struct X
{
   int i;
   X ();
   virtual ~X ();
};

extern "C" X func ();   // C4190
```
