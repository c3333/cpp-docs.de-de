---
title: Prolog und Epilog bei x64-Systemen
ms.date: 12/17/2018
ms.assetid: 0453ed1a-3ff1-4bee-9cc2-d6d3d6384984
ms.openlocfilehash: d0b7444af6e434a09f6af5f5b1c144b46c79ad56
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328430"
---
# <a name="x64-prolog-and-epilog"></a>Prolog und Epilog bei x64-Systemen

Jede Funktion, die Stapelspeicherplatz zuweist, andere Funktionen aufruft, permanente Register speichert oder die Ausnahmebehandlung verwendet, muss über einen Prolog verfügen, dessen Adressgrenzen in den Entladedaten beschrieben sind, die mit dem jeweiligen Funktionstabelleneintrag verbunden sind. Weitere Informationen finden Sie unter [Ausnahmebehandlung bei x64-Systemen](../build/exception-handling-x64.md). Der Prolog speichert Argumentregister bei Bedarf in ihren Heimatadressen, schiebt nichtflüchtige Register auf den Stapel, weist den festen Teil des Stapels für lokale und temporäre Objekte zu und erstellt optional einen Framezeiger. Die zugeordneten Entladedaten müssen die Aktion des Prologs beschreiben und die erforderlichen Informationen bereitstellen, um die Auswirkungen des Prologcodes rückgängig zu machen.

Wenn die feste Zuordnung im Stapel mehr als eine Seite (also mehr als 4096 Bytes) umfasst, kann es vorkommen, dass die Stapelzuordnung mehr als eine Seite des virtuellen Arbeitsspeichers umfasst. Daher muss die Zuordnung vor dem Zuordnen überprüft werden. Hierzu wird eine spezielle Routine bereitgestellt, die vom Prolog aufgerufen werden kann und keines der Argumentregister zerstört.

Die bevorzugte Methode zum Speichern permanenter Register besteht darin, sie vor der festen Stapelzuordnung auf den Stapel zu verschieben. Wenn die feste Stapelzuordnung vor dem Speichern der permanenten Register durchgeführt wird, ist wahrscheinlich eine 32-Bit-Verschiebung erforderlich, um den gespeicherten Registerbereich zu adressieren. (Angeblich sind Pushvorgänge von Registern so schnell wie Verschiebungen und dürften dies auf absehbare Zeit trotz der impliziten Abhängigkeit zwischen den Pushvorgängen auch bleiben.) Permanente Register können in beliebiger Reihenfolge gespeichert werden. Allerdings muss die erste Verwendung eines permanenten Registers im Prolog darin bestehen, es zu speichern.

## <a name="prolog-code"></a>Prologcode

Der Code für einen typischen Prolog könnte wie folgt lauten:

```MASM
    mov    [RSP + 8], RCX
    push   R15
    push   R14
    push   R13
    sub    RSP, fixed-allocation-size
    lea    R13, 128[RSP]
    ...
```

Dieser Prolog speichert das Argumentregister RCX an seinem Hauptspeicherort, speichert die permanenten Register R13-R15, ordnet den festen Teil des Stapelrahmens zu und erstellt einen Framezeiger, bei dem 128 Bytes in den festen Zuordnungsbereich zeigen. Durch die Verwendung eines Offsets kann ein größerer Teil des festen Zuordnungsbereichs mit Ein-Byte-Offsets adressiert werden.

Wenn die feste Zuordnungsgröße größer oder gleich einer Speicherseite ist, muss vor dem Ändern der RSP-Datei eine Hilfsfunktion aufgerufen werden. Dieses Hilfsprogramm (`__chkstk`) prüft den für die Zuordnung vorgesehenen Stapelbereich, um sicherzustellen, dass der Stapel ordnungsgemäß erweitert wird. In diesem Fall würde das vorherige Prologbeispiel somit wie folgt lauten:

```MASM
    mov    [RSP + 8], RCX
    push   R15
    push   R14
    push   R13
    mov    RAX,  fixed-allocation-size
    call   __chkstk
    sub    RSP, RAX
    lea    R13, 128[RSP]
    ...
```

Das `__chkstk`-Hilfsprogramm ändert nur die Register R10 und R11 sowie die Bedingungscodes. Insbesondere RAX wird unverändert zurückgegeben, und alle permanenten Register und Argumentübergaberegister bleiben unverändert.

## <a name="epilog-code"></a>Epilogcode

Epilogcode existiert an jedem Ausstieg einer Funktion. Es gibt zwar normalerweise nur einen Prolog, aber es können mehrere Epiloge vorhanden sein. Der Epilogcode schneidet den Stapel (falls erforderlich) auf seine feste Zuordnungsgröße zu, hebt die feste Stapelzuordnung auf, stellt permanente Register wieder her, indem er ihre gespeicherten Werte per Pop aus dem Stapel entfernt, und kehrt zurück.

Der Epilogcode muss einem strengen Satz von Regeln folgen, damit der Entladecode Entladevorgänge trotz Ausnahmen und Unterbrechungen zuverlässig ausführen kann. Diese Regeln reduzieren die erforderliche Menge an Entladedaten, da keine zusätzlichen Daten erforderlich sind, um die einzelnen Epiloge zu beschreiben. Stattdessen kann der Entladecode feststellen, dass ein Epilog ausgeführt wird, indem er einen Codestrom in Vorwärtsrichtung überprüft, um einen Epilog zu identifizieren.

Wenn kein Framezeiger in der Funktion verwendet wird, muss der Epilog zunächst die Zuordnung des festen Teils des Stapels aufheben, die permanenten Register werden per Pop entfernt, und die Steuerung wird an die aufrufende Funktion zurückgegeben. Ein auf ein Objekt angewendeter

```MASM
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

Wenn ein Framezeiger in der Funktion verwendet wird, muss der Stapel vor der Ausführung des Epilogs auf die Größe seiner festen Zuordnung zugeschnitten werden. Diese Aktion ist technisch gesehen nicht Teil des Epilogs. Der folgende Epilog könnte beispielsweise verwendet werden, um den zuvor verwendeten Prolog rückgängig zu machen:

```MASM
    lea      RSP, -128[R13]
    ; epilogue proper starts here
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

In der Praxis gibt es bei Verwendung eines Framezeigers keinen guten Grund, RSP in zwei Schritten anzupassen, sodass stattdessen der folgende Epilog verwendet würde:

```MASM
    lea      RSP, fixed-allocation-size - 128[R13]
    pop      R13
    pop      R14
    pop      R15
    ret
```

Nur diese Formen sind für einen Epilog zulässig. Er muss entweder aus einer `add RSP,constant` oder `lea RSP,constant[FPReg]` bestehen, gefolgt von einer Reihe von null oder mehr 8-Byte-Registerpopvorgängen und einem `return` oder `jmp`. (Im Epilog ist nur eine Teilmenge der `jmp`-Anweisungen zulässig. Bei der Teilmenge handelt es sich ausschließlich um die Klasse der `jmp`-Anweisungen mit ModRM-Speicherverweisen, wobei der ModRM-Mod-Feldwert 00 ist. Die Verwendung von `jmp`-Anweisungen im Epilog mit einem ModRM-Mod-Feldwert von 01 oder 10 ist nicht zulässig. Weitere Informationen zu den zulässigen ModRM-Verweisen finden Sie in Tabelle A-15 in Band 3 des AMD x86-64 Architecture Programmer's Manual: „General Purpose and System Instructions“.) Anderer Code ist nicht möglich. Insbesondere kann nichts innerhalb eines Epilogs geplant werden, auch nicht das Laden eines Rückgabewerts.

Wenn kein Framezeiger verwendet wird, muss der Epilog `add RSP,constant` verwenden, um die Zuordnung des festen Teils des Stapels aufzuheben. Möglicherweise wird stattdessen nicht `lea RSP,constant[RSP]` verwendet. Diese Einschränkung ist vorhanden, damit der Entladecode bei der Suche nach Epilogen weniger Muster erkennen muss.

Durch das Befolgen dieser Regeln kann der Entladecode feststellen, dass aktuell ein Epilog ausgeführt wird, und er kann die Ausführung des restlichen Epilogs simulieren, um die erneute Erstellung des Kontexts der aufrufenden Funktion zu ermöglichen.

## <a name="see-also"></a>Siehe auch

[x64-Softwarekonventionen](x64-software-conventions.md)
