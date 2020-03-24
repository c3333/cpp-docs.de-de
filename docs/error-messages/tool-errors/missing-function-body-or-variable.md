---
title: Fehlender Funktionsrumpf oder fehlende Variable
ms.date: 11/04/2016
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
ms.openlocfilehash: 6d2ef22b90009d320485fb6fe3f7e308ae05c442
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173620"
---
# <a name="missing-function-body-or-variable"></a>Fehlender Funktionsrumpf oder fehlende Variable

Mit nur einem Funktionsprototyp kann der Compiler ohne Fehler fortfahren, aber der Linker kann einen Rückruf einer Adresse nicht auflösen, da kein Funktionscode oder variabler Speicherplatz reserviert ist. Dieser Fehler wird erst angezeigt, wenn Sie einen Rückruf für die Funktion erstellen, die der Linker auflösen muss.

## <a name="example"></a>Beispiel

Der Funktions aufrufin Main bewirkt LNK2019, da der Prototyp dem Compiler den Eindruck gibt, dass die Funktion vorhanden ist.  Der Linker findet, dass dies nicht der Fall ist.

```cpp
// LNK2019_MFBV.cpp
// LNK2019 expected
void DoSomething(void);
int main() {
   DoSomething();
}
```

## <a name="example"></a>Beispiel

Stellen C++Sie in sicher, dass Sie die Implementierung einer bestimmten Funktion für eine Klasse und nicht nur einen Prototyp in der Klassendefinition einschließen. Wenn Sie die Klasse außerhalb der Header Datei definieren, achten Sie darauf, dass Sie den Klassennamen vor der Funktion (`Classname::memberfunction`) einschließen.

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

## <a name="see-also"></a>Weitere Informationen

[Linkertoolfehler LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)
