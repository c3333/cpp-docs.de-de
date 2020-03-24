---
title: Compilerwarnung (Stufe 1) C4526
ms.date: 11/04/2016
f1_keywords:
- C4526
helpviewer_keywords:
- C4526
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
ms.openlocfilehash: d4d772f3e505979a6ea5c3e7923fefa621601370
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186503"
---
# <a name="compiler-warning-level-1-c4526"></a>Compilerwarnung (Stufe 1) C4526

"Funktion": die statische Member-Funktion kann die virtuelle Funktion "virtuelle Funktion nicht überschreiben" ignoriert, die virtuelle Funktion wird ausgeblendet.

Die statische Member-Funktion erfüllt die Kriterien, um die virtuelle Funktion zu überschreiben, wodurch der Member sowohl virtuell als auch statisch wird.

Der folgende Code generiert C4526:

```cpp
// C4526.cpp
// compile with: /W1 /c
// C4526 expected
struct myStruct1 {
   virtual void __stdcall func( int ) = 0;
};

struct myStruct2: public myStruct1 {
   static void __stdcall func( int );
};
```

Die folgenden Fehlerbehebungen sind möglich:

- Wenn die Funktion dazu gedacht war, die virtuelle Funktion der Basisklasse zu überschreiben, entfernen Sie den statischen Spezifizierer.

- Wenn die Funktion eine statische Element Funktion sein soll, benennen Sie Sie um, sodass Sie nicht mit der virtuellen Funktion der Basisklasse in Konflikt steht.
