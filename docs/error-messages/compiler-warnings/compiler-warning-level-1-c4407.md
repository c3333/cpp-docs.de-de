---
title: Compilerwarnung (Stufe 1) C4407
ms.date: 11/04/2016
f1_keywords:
- C4407
helpviewer_keywords:
- C4407
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
ms.openlocfilehash: 8dd78872d4edf82fb61c8ab93639dbcd93085754
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162542"
---
# <a name="compiler-warning-level-1-c4407"></a>Compilerwarnung (Stufe 1) C4407

Umwandlung zwischen unterschiedlichen Zeigern auf Element Darstellungen generiert der Compiler möglicherweise falschen Code.

Eine falsche Umwandlung wurde erkannt.

C4407 kann aufgrund von compilerübereinstimmungs-Arbeitsaufgaben generiert werden, die in Visual Studio 2005 ausgeführt wurden. "Pointer-to-Member" erfordert nun einen qualifizierten Namen und den Address-of-Operator (&).

C4407 kann auftreten, wenn Sie eine Umwandlung zwischen einem Zeiger auf einen mehrfach Vererbungs Zeiger auf einen einzelnen Vererbungs Zeiger auf einen Member durchführen. Manchmal kann dies funktionieren, aber manchmal nicht, da die Einzel Vererbungs-Zeiger-auf-Member-Darstellung nicht genügend Informationen enthält. Die Kompilierung mit **/VMM** kann hilfreich sein (Weitere Informationen finden Sie unter [/VMM,/VMS,/vmv (universell Darstellung)](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)). Sie können auch versuchen, die Basisklassen neu anzuordnen. der Compiler erkennt einen Informationsverlust bei der Konvertierung, da sich eine Basisklasse bei einem Offset ungleich 0 (null) von der abgeleiteten-Klasse befindet.

Im folgenden Beispiel wird C4407 generiert:

```cpp
// C4407.cpp
// compile with: /W1 /c
struct C1 {};
struct C2 {};
struct C3 : C1, C2 {};

typedef void(C3::*PMF_C3)();
typedef void(C2::*PMF_C2)();

PMF_C2 f1(PMF_C3 pmf) {
   return (PMF_C2)pmf;   // C4407, change type of cast,
   // or reverse base class inheritance of C3 (i.e. : C2, C1)
}
```
