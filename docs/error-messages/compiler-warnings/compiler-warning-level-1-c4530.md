---
title: Compilerwarnung (Stufe 1) C4530
description: Referenzhandbuch zu Microsoft C++ Compiler Warning C4530.
ms.date: 04/02/2020
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: fe0a2b4c8eb881327f3e59d66e7e6941f0a2cad8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230661"
---
# <a name="compiler-warning-level-1-c4530"></a>Compilerwarnung (Stufe 1) C4530

> Der C++-Ausnahmehandler wurde verwendet, aber die Entlade Semantik ist nicht aktiviert. /EHsc angeben

Der Code verwendet die C++-Ausnahmebehandlung, aber [/EHsc](../../build/reference/eh-exception-handling-model.md) war nicht in den Compileroptionen enthalten.

## <a name="remarks"></a>Bemerkungen

Der Compiler benötigt die **`/EHsc`** Option zum Erstellen von C++-Code, der auf den C++-Standard für die Ausnahmebehandlung folgt. Die Entladungs *Semantik* Standard C++ gibt an, dass Objekte und Stapel Rahmen, die zwischen dem Auslösen einer Ausnahme und dem erfassten Vorgang erstellt werden, zerstört und ihre Ressourcen wieder hergestellt werden müssen. Dieser Prozess wird als *entwickeln des Stapels*bezeichnet.

Die- **`/EHsc`** Option weist den Compiler an, Code zu generieren, der die debugtoren für automatische Speicher Objekte aufruft, wenn eine Ausnahme den enthaltenden Stapel Rahmen durchläuft. *Automatische Speicher* Objekte sind Objekte, die auf dem Stapel zugeordnet sind, z. b. lokale Variablen. Er wird als automatischer Speicher bezeichnet, da er automatisch zugewiesen wird, wenn Funktionen aufgerufen werden, und bei Rückgabe automatisch freigegeben wird. Ein *Stapel Rahmen* ist die Daten, die auf dem Stapel abgelegt werden, wenn eine Funktion zusammen mit dem automatischen Speicher aufgerufen wird.

Wenn eine Ausnahme ausgelöst wird, kann Sie mehrere Stapel Rahmen durchlaufen, bevor Sie abgefangen wird. Diese Stapel Rahmen müssen entwickelt werden, wenn die Ausnahme Sie in umgekehrter Aufruf Reihenfolge durchläuft. Die automatischen Speicher Objekte in jedem Stapel Rahmen müssen zerstört werden, um Ihre Ressourcen ordnungsgemäß wiederherzustellen. Dabei handelt es sich um denselben Zerstörungs-und Wiederherstellungsprozess, der automatisch erfolgt, wenn eine Funktion normal zurückgibt.

Wenn die **`/EHsc`** Option nicht aktiviert ist, werden automatische Speicher Objekte in den Stapel Rahmen zwischen der auslösenden Funktion und der Funktion, in der die Ausnahme abgefangen wird, nicht zerstört. Nur die in einem-oder-Block erstellten automatischen Speicher Objekte **`try`** **`catch`** werden zerstört, was zu erheblichen Ressourcenverlusten und anderem unerwartetem Verhalten führen kann.

Wenn in der ausführbaren Datei keine Ausnahmen ausgelöst werden können, wird diese Warnung möglicherweise ignoriert. In einigen Codes sind möglicherweise andere Optionen für die Ausnahmebehandlung erforderlich. Weitere Informationen finden Sie unter [/eh](../../build/reference/eh-exception-handling-model.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4530 generiert:

```cpp
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

Kompilieren Sie das Beispiel mit **`/EHsc`** , um die Warnung zu beheben.
