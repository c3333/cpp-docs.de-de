---
title: Compilerwarnung (Stufe 1) C4190
ms.date: 11/04/2016
f1_keywords:
- C4190
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
ms.openlocfilehash: 6d110aa70a470382e274546e95599804fa3bc7d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199874"
---
# <a name="compiler-warning-level-1-c4190"></a>Compilerwarnung (Stufe 1) C4190

für "Bezeichner1" wurde eine C-Verknüpfung angegeben, es wird jedoch der UDT "Bezeichner2" zurückgegeben, der nicht mit C kompatibel ist

Eine Funktion oder ein Zeiger auf die Funktion verfügt über einen UDT (benutzerdefinierter Typ, bei dem es sich um eine Klasse, Struktur, Enumeration oder Union handelt) als Rückgabetyp und `extern` "C"-Verknüpfung. Dies ist zulässig, wenn Folgendes gilt:

- Alle Aufrufe dieser Funktion erfolgen von C++.

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
