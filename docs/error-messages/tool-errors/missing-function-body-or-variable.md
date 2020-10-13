---
title: Fehlender Funktionsrumpf oder fehlende Variable
ms.date: 11/04/2016
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
ms.openlocfilehash: 835bd968035b355ded9636d446d44d4ce069c248
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008885"
---
# <a name="missing-function-body-or-variable"></a>Fehlender Funktionsrumpf oder fehlende Variable

Mit nur einem Funktionsprototyp kann der Compiler ohne Fehler fortfahren, aber der Linker kann einen Rückruf einer Adresse nicht auflösen, da kein Funktionscode oder variabler Speicherplatz reserviert ist. Dieser Fehler wird erst angezeigt, wenn Sie einen Rückruf für die Funktion erstellen, die der Linker auflösen muss.

## <a name="example-call-to-an-undefined-function"></a>Beispiel: Aufrufe einer nicht definierten Funktion

Der Funktions aufrufin Main bewirkt LNK2019, da der Prototyp dem Compiler den Eindruck gibt, dass die Funktion vorhanden ist.  Der Linker findet, dass dies nicht der Fall ist.

```cpp
// LNK2019_MFBV.cpp
// LNK2019 expected
void DoSomething(void);
int main() {
   DoSomething();
}
```

## <a name="example-call-to-an-implemented-function"></a>Beispiel: Aufrufe einer implementierten Funktion

Stellen Sie in C++ sicher, dass Sie die Implementierung einer bestimmten Funktion für eine Klasse und nicht nur einen Prototyp in der Klassendefinition einschließen. Wenn Sie die Klasse außerhalb der Header Datei definieren, achten Sie darauf, dass Sie den Klassennamen vor der Funktion ( `Classname::memberfunction` ) einschließen.

```cpp
// LNK2019_MFBV_2.cpp
// LNK2019 expected
struct A {
   static void Test();
};

// Should be void A::Test() {}
void Test() {}

int main() {
   A AObject;
   AObject.Test();
}
```

## <a name="see-also"></a>Siehe auch

[Linker-Tools-Fehler LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)
