---
title: Compilerfehler C2712
ms.date: 11/04/2016
f1_keywords:
- C2712
helpviewer_keywords:
- C2712
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
ms.openlocfilehash: a25c59fa5c9ba0102666f6c8922a61b063e7627a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202305"
---
# <a name="compiler-error-c2712"></a>Compilerfehler C2712

> __try kann nicht in Funktionen verwendet werden, die eine Objektentladung benötigen

## <a name="remarks"></a>Bemerkungen

Der Fehler C2712 kann auftreten, wenn Sie [/EHsc](../../build/reference/eh-exception-handling-model.md)verwenden, und eine Funktion mit strukturierter Ausnahmebehandlung enthält auch Objekte, die entlädt (Zerstörung).

Lösungsvorschläge:

- Verschieben Sie Code, der SEH benötigt, zu einer anderen Funktion.

- Schreiben Sie Funktionen, die SEH verwenden, neu, um die Verwendung von lokalen Variablen und Parameter, die über Destruktoren verfügen, zu vermeiden. Verwenden Sie SEH nicht in Konstruktoren oder Destruktoren

- Kompilieren ohne /EHsc

Fehler C2712 kann auch auftreten, wenn Sie eine Methode aufzurufen, die mit dem [__event](../../cpp/event.md) -Schlüsselwort deklariert wurde. Da das Ereignis in einer Multithread-Umgebung verwendet werden kann, generiert der Compiler Code, der die Bearbeitung des zugrunde liegenden Ereignis Objekts verhindert und den generierten Code dann in eine Seh [-try-schließlich-Anweisung](../../cpp/try-finally-statement.md)einschließt. Folglich wird Fehler C2712 auftreten, wenn Sie die Ereignismethode aufrufen und ein Argument, dessen Typ einen Destruktor enthält, als Wert übergeben. Eine Lösung besteht in diesem Fall darin, das Argument als konstanten Verweis zu übergeben.

C2712 kann auch auftreten, wenn Sie mit **/clr: pure** kompilieren und ein statisches Array von Zeigern auf Funktionen in einem `__try`-Block deklarieren. Ein statischer Member erfordert, dass der Compiler die dynamische Initialisierung unter **/clr: pure**verwendet C++ , was eine Ausnahmebehandlung impliziert. Eine C++-Ausnahmebehandlung ist jedoch in einem `__try`-Block nicht zulässig.

Die Compileroptionen **/clr: pure** und **/clr: Safe** sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 nicht unterstützt.

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
