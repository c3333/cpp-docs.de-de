---
title: Compilerwarnung (Stufe 1) C4055
ms.date: 11/04/2016
f1_keywords:
- C4055
helpviewer_keywords:
- C4055
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
ms.openlocfilehash: 47883f60c3205125a8ee88b804c1d622b3ba0b41
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041028"
---
# <a name="compiler-warning-level-1-c4055"></a>Compilerwarnung (Stufe 1) C4055

> '*Konvertierung*': von Datenzeiger '*Typ1*' zu Funktionszeiger '*Typ2*'

## <a name="remarks"></a>Bemerkungen

**Veraltet:** Diese Warnung wird nicht von Visual Studio 2017 und höheren Versionen generiert.

Ein Datenzeiger wird (möglicherweise falsch) in einen Funktionszeiger umgewandelt. Dies ist unter „/Za“ eine Warnung der Stufe 1 und unter „/Ze“ eine Warnung der Stufe 4.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4055 generiert:

```C
// C4055.c
// compile with: /Za /W1 /c
typedef int (*PFUNC)();
int *pi;
PFUNC f() {
   return (PFUNC)pi;   // C4055
}
```

Unter „/Ze“ ist dies eine Warnung der Stufe 4.

```C
// C4055b.c
// compile with: /W4 /c
typedef int (*PFUNC)();
int *pi;
PFUNC f() {
return (PFUNC)pi;   // C4055
}
```
