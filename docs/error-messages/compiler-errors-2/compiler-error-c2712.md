---
title: Compilerfehler C2712
description: Beschreibt den Microsoft C/C++-Compilerfehler C2712.
ms.date: 08/25/2020
f1_keywords:
- C2712
helpviewer_keywords:
- C2712
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
ms.openlocfilehash: 2f0b883607241473a429919e06de9e975fa2e3c1
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898694"
---
# <a name="compiler-error-c2712"></a>Compilerfehler C2712

> kann nicht `__try` in Funktionen verwendet werden, die das Entwickeln von Objekten erfordern

## <a name="remarks"></a>Hinweise

Der Fehler C2712 kann auftreten, wenn Sie verwenden [`/EHsc`](../../build/reference/eh-exception-handling-model.md) und eine Funktion mit strukturierter Ausnahmebehandlung auch Objekte enthält, die eine Entwickelung erfordern (Zerstörung).

Mögliche Lösungen:

- Verschieben Sie Code, der SEH benötigt, zu einer anderen Funktion.

- Schreiben Sie Funktionen, die SEH verwenden, neu, um die Verwendung von lokalen Variablen und Parameter, die über Destruktoren verfügen, zu vermeiden. Verwenden Sie SEH nicht in Konstruktoren oder Destruktoren

- Kompilieren ohne /EHsc

Fehler C2712 kann auch auftreten, wenn eine Methode aufgerufen wird, die mit dem- [`__event`](../../cpp/event.md) Schlüsselwort deklariert wurde. Da das-Ereignis in einer Multithread-Umgebung verwendet werden kann, generiert der Compiler Code, der die Bearbeitung des zugrunde liegenden Ereignis Objekts verhindert und den generierten Code dann in eine Seh- [ `try-finally` Anweisung](../../cpp/try-finally-statement.md)einschließt. Folglich wird Fehler C2712 auftreten, wenn Sie die Ereignismethode aufrufen und ein Argument, dessen Typ einen Destruktor enthält, als Wert übergeben. Eine Lösung besteht in diesem Fall darin, das Argument als konstanten Verweis zu übergeben.

C2712 kann auch auftreten, wenn Sie mit kompilieren **`/clr:pure`** und ein statisches Array von Zeigern auf Funktionen in einem-Block deklarieren **`__try`** . Ein statischer Member erfordert, dass der Compiler die dynamische Initialisierung unter verwendet **`/clr:pure`** . Dies impliziert die C++-Ausnahmebehandlung. Die C++-Ausnahmebehandlung ist in einem-Block jedoch nicht zulässig **`__try`** .

Die **`/clr:pure`** **`/clr:safe`** Compileroptionen und sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 nicht unterstützt.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2712 generiert und gezeigt, wie Sie diesen Fehler beheben:

```cpp
// C2712.cpp
// compile with: /clr:pure /c
struct S1 {
   static int smf();
   void fnc();
};

void S1::fnc() {
   __try {
      static int (*array_1[])() = {smf,};   // C2712

      // OK
      static int (*array_2[2])();
      array_2[0] = smf;
    }
    __except(0) {}
}
```
