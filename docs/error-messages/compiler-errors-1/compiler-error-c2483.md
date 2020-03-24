---
title: Compilerfehler C2483
ms.date: 09/15/2017
f1_keywords:
- C2483
helpviewer_keywords:
- C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
ms.openlocfilehash: 20b08c0d2cd89224ed3d3b8b34915deb947b0b4b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205113"
---
# <a name="compiler-error-c2483"></a>Compilerfehler C2483

>"*Bezeichner*": das Objekt mit dem Konstruktor oder Dekonstruktor kann nicht als "Thread" deklariert werden.

Diese Fehlermeldung ist in Visual Studio 2015 und höheren Versionen veraltet. In früheren Versionen können Variablen, die mit dem `thread`-Attribut deklariert wurden, nicht mit einem Konstruktor oder einem anderen Ausdruck initialisiert werden, der eine Lauf Zeit Auswertung erfordert. Ein statischer Ausdruck ist erforderlich, um `thread` Daten zu initialisieren.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2483 in Visual Studio 2013 und früheren Versionen generiert.

```cpp
// C2483.cpp
// compile with: /c
__declspec(thread) struct A {
   A(){}
   ~A(){}
} aa;   // C2483 error

__declspec(thread) struct B {} b;   // OK
```

## <a name="see-also"></a>Weitere Informationen

[thread](../../cpp/thread.md)
