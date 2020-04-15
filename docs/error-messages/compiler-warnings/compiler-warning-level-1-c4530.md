---
title: Compilerwarnung (Stufe 1) C4530
description: Referenzhandbuch zur Microsoft C++-Compilerwarnung C4530.
ms.date: 04/02/2020
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: 9de88a4b0b6c7176ff82b68c92d09d9fe75a70b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369780"
---
# <a name="compiler-warning-level-1-c4530"></a>Compilerwarnung (Stufe 1) C4530

> C++-Ausnahmehandler verwendet, aber Abwickeln semantisch sind nicht aktiviert. Angeben von /EHsc

Der Code verwendet die C++-Ausnahmebehandlung, [aber /EHsc](../../build/reference/eh-exception-handling-model.md) war nicht in den Compileroptionen enthalten.

## <a name="remarks"></a>Bemerkungen

Der Compiler **`/EHsc`** benötigt die Option zum Erstellen von C++-Code, der dem C++-Standard für die Ausnahmebehandlung folgt. Die Standard-C++-Absemantik vom *Abwickeln* gibt an, dass Objekte und Stapelrahmen, die zwischen dem Ort, an dem eine Ausnahme ausgelöst wird, und dem Ort, an dem sie gefangen wird, zerstört und ihre Ressourcen wiederhergestellt werden müssen. Dieser Prozess wird als *Entladen des Stapels*bezeichnet.

Die **`/EHsc`** Option weist den Compiler an, Code zu generieren, der die Destruktoren für automatische Speicherobjekte aufruft, wenn eine Ausnahme den enthaltenden Stapelrahmen durchläuft. *Automatische Speicherobjekte* sind Objekte, die auf dem Stapel zugewiesen sind, z. B. lokale Variablen. Es wird als automatischer Speicher bezeichnet, da es automatisch zugewiesen wird, wenn Funktionen aufgerufen werden, und automatisch freigegeben wird, wenn sie zurückgegeben werden. Ein *Stapelrahmen* sind die Daten, die auf dem Stapel platziert werden, wenn eine Funktion aufgerufen wird, zusammen mit ihrer automatischen Speicherung.

Wenn eine Ausnahme ausgelöst wird, kann sie mehrere Stapelrahmen durchlaufen, bevor sie abgefangen wird. Diese Stapelrahmen müssen aufgewickelt werden, da die Ausnahme sie in umgekehrter Aufrufreihenfolge durchläuft. Die automatischen Speicherobjekte in jedem Stapelrahmen müssen zerstört werden, um ihre Ressourcen sauber wiederherzustellen. Es ist derselbe Zerstörungs- und Wiederherstellungsprozess, der automatisch stattfindet, wenn eine Funktion normal zurückkehrt.

Wenn **`/EHsc`** die Option nicht aktiviert ist, werden automatische Speicherobjekte in den Stapelrahmen zwischen der Auswerfenfunktion und der Funktion, bei der die Ausnahme abgefangen wird, nicht zerstört. Nur die automatischen Speicherobjekte, die in einem **Try-** oder **Catch-Block** erstellt wurden, werden zerstört, was zu erheblichen Ressourcenlecks und anderem unerwarteten Verhalten führen kann.

Wenn in Ihrer ausführbaren Datei möglicherweise keine Ausnahmen ausgelöst werden können, ignorieren Sie diese Warnung möglicherweise ignorieren. Für einige Codes sind möglicherweise andere Optionen für die Ausnahmebehandlung erforderlich. Weitere Informationen finden Sie unter [/EH](../../build/reference/eh-exception-handling-model.md).

## <a name="example"></a>Beispiel

Die folgende Stichprobe generiert C4530:

```cpp
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

Kompilieren **`/EHsc`** Sie das Beispiel mit, um die Warnung zu beheben.
