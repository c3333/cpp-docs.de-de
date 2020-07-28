---
title: Compilerwarnung (Stufen 3 und 4) C4244
ms.date: 11/04/2016
ms.assetid: f116bb09-c479-4b4e-a647-fe629a1383f6
ms.openlocfilehash: cadba931af9c4497ec78938c37f94fe13daab0af
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214320"
---
# <a name="compiler-warning-levels-3-and-4-c4244"></a>Compilerwarnung (Stufen 3 und 4) C4244

'conversion': Umwandlung von 'type1' in 'type2', Datenverlust ist möglich

Ein ganzzahliger Typ wird in einen kleineren ganzzahligen Typ konvertiert. Dies ist eine Warnung der Stufe 4, *type1* wenn Typ1 **`int`** und *Typ2* kleiner als ist **`int`** . Andernfalls ist es eine Ebene 3 (ein Wert vom Typ [__int64](../../cpp/int8-int16-int32-int64.md) einer Variablen vom Typ zugewiesen **`unsigned int`** ). Möglicherweise ist ein Datenverlust aufgetreten.

Wenn C4244 angezeigt wird, sollten Sie das Programm für das Verwenden von kompatiblen Typen ändern Logik zu Ihrem Code hinzufügen, um sicherzustellen, dass der Bereich möglicher Werte immer mit den verwendeten Typen kompatibel sind.

C4244 kann auch auf Ebene 2 ausgelöst werden; Weitere Informationen finden Sie unter [Compilerwarnung (Stufe 2) C4244](../../error-messages/compiler-warnings/compiler-warning-level-2-c4244.md) .

Die Konvertierung hat möglicherweise ein Problem durch implizite Konvertierungen.

Im folgenden Beispiel wird C4244 generiert:

```cpp
// C4244_level4.cpp
// compile with: /W4
int aa;
unsigned short bb;
int main() {
   int b = 0, c = 0;
   short a = b + c;   // C4244

   bb += c;   // C4244
   bb = bb + c;   // C4244
   bb += (unsigned short)aa;   // C4244
   bb = bb + (unsigned short)aa;   // OK
}
```

Weitere Informationen finden Sie unter [übliche arithmetische Konvertierungen](../../c-language/usual-arithmetic-conversions.md).

```cpp
// C4244_level3.cpp
// compile with: /W3
int main() {
   __int64 i = 8;
   unsigned int ii = i;   // C4244
}
```

Warnung C4244 kann auftreten, wenn Code für 64-Bit-Ziele erstellt wird, der keine Warnung generiert, wenn er für 32-Bit-Ziele erstellt wird. Beispielsweise ist ein Unterschied zwischen Zeigern eine 32-Bit-Menge auf 32-Bit-Plattformen, aber eine 64-Bit-Menge auf 64-Bit-Plattformen.

Im folgenden Beispiel wird C4244 generiert, wenn für 64-Bit-Ziele kompiliert wird:

```cpp
// C4244_level3_b.cpp
// compile with: /W3
int main() {
   char* p1 = 0;
   char* p2 = 0;
   int x = p2 - p1;   // C4244
}
```
