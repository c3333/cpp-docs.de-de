---
title: Compilerfehler C3646
ms.date: 06/14/2018
f1_keywords:
- C3646
helpviewer_keywords:
- C3646
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
ms.openlocfilehash: 13a3ebeb6e7783687abc73cd0dcc018abe827809
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200472"
---
# <a name="compiler-error-c3646"></a>Compilerfehler C3646

> "Spezifizierer": Unbekannter Überschreibungsspezifizierer.

## <a name="remarks"></a>Bemerkungen

Der Compiler hat an der Position, an der er einen Überschreibungsspezifizierer erwartet hat, ein Token gefunden, aber das Token wurde vom Compiler nicht erkannt.

Wenn der unbekannte *Spezifizierer* beispielsweise **_NOEXCEPT**ist, ersetzen Sie ihn durch das Schlüsselwort **noaußer**.

Weitere Informationen finden Sie unter [Überschreibungsspezifizierer](../../extensions/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3646 generiert und eine Möglichkeit gezeigt, Sie zu beheben:

```cpp
// C3646.cpp
// compile with: /clr /c
ref class C {
   void f() unknown;   // C3646
   // try the following line instead
   // virtual void f() abstract;
};
```
