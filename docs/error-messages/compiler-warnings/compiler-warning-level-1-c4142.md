---
title: Compilerwarnung (Stufe 1) C4142
ms.date: 11/04/2016
f1_keywords:
- C4142
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
ms.openlocfilehash: c1721d472c81c62ba01282f43c7e678d7f84206b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200082"
---
# <a name="compiler-warning-level-1-c4142"></a>Compilerwarnung (Stufe 1) C4142

ungutartige Neudefinition des Typs

Ein Typ wird auf eine Weise neu definiert, die keine Auswirkung auf den generierten Code hat.

Dieser Fehler kann eine der folgenden Ursachen haben:

- Eine Member-Funktion einer abgeleiteten Klasse weist einen anderen Rückgabetyp aus der entsprechenden Member-Funktion der Basisklasse auf.

- Ein mit dem `typedef`-Befehl definierter Typ wird mit einer anderen Syntax neu definiert.

Im folgenden Beispiel wird C4142 generiert:

```c
// C4142.c
// compile with: /W1
float X2;
X2 = 2.0 + 1.0;   // C4142

int main() {
   float X2;
   X2 = 2.0 + 1.0;   // OK
}
```
