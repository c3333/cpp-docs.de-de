---
title: Prolog und Epilog bei x64-Systemen
ms.date: 12/17/2018
ms.assetid: 0453ed1a-3ff1-4bee-9cc2-d6d3d6384984
ms.openlocfilehash: d0b7444af6e434a09f6af5f5b1c144b46c79ad56
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328430"
---
# <a name="x64-prolog-and-epilog"></a>Prolog und Epilog bei x64-Systemen

Jede Funktion, die Stapelspeicher zuweist, andere Funktionen aufruft, nichtflüchtige Register speichert oder Ausnahmebehandlung verwendet, muss über einen Prolog verfügen, dessen Adressgrenzen in den Entladungsdaten beschrieben werden, die dem jeweiligen Funktionstabelleneintrag zugeordnet sind. Weitere Informationen finden Sie unter [x64-Ausnahmebehandlung](../build/exception-handling-x64.md). Der Prolog speichert bei Bedarf Argumentregister in ihren Privatadressen, schiebt nichtflüchtige Register auf den Stapel, ordnet den festen Teil des Stapels für Locals und Temporäre zu und erstellt optional einen Framezeiger. Die zugehörigen Entladungsdaten müssen die Wirkung des Prologs beschreiben und die Informationen bereitstellen, die erforderlich sind, um die Wirkung des Prologcodes rückgängig zu machen.

Wenn die feste Zuordnung im Stapel mehr als eine Seite (d. h. mehr als 4096 Bytes) ist, ist es möglich, dass sich die Stapelzuordnung über mehr als eine virtuelle Speicherseite erstreckt, und daher muss die Zuordnung überprüft werden, bevor sie zugewiesen wird. Eine spezielle Routine, die aus dem Prolog aufrufbar ist und keines der Argumentregister zerstört, wird zu diesem Zweck bereitgestellt.

Die bevorzugte Methode zum Speichern nichtflüchtiger Register besteht darin, sie vor der festen Stapelzuordnung auf den Stapel zu verschieben. Wenn die feste Stapelzuordnung vor dem Speichern der nichtflüchtigen Register durchgeführt wird, ist höchstwahrscheinlich eine 32-Bit-Verschiebung erforderlich, um den gespeicherten Registerbereich zu adressieren. (Berichten zufolge sind Registerverschiebungen so schnell wie Bewegungen und sollten dies auf absehbare Zeit trotz der impliziten Abhängigkeit zwischen Pushs bleiben.) Nichtflüchtige Register können in beliebiger Reihenfolge gespeichert werden. Die erste Verwendung eines nichtflüchtigen Registers im Prolog muss jedoch darin bestehen, es zu speichern.

## <a name="prolog-code"></a>Prolog-Code

Der Code für einen typischen Prolog könnte sein:

```MASM
    mov    [RSP + 8], RCX
    push   R15
    push   R14
    push   R13
    sub    RSP, fixed-allocation-size
    lea    R13, 128[RSP]
    ...
```

Dieser Prolog speichert das Argumentregister RCX an seinem Heimatstandort, speichert nichtflüchtige Register R13-R15, ordnet den festen Teil des Stapelrahmens zu und richtet einen Framezeiger ein, der 128 Bytes in den festen Zuordnungsbereich zeigt. Durch die Verwendung eines Offsets kann ein großteil der festen Zuordnungsfläche mit Einbysatz-Offsets adressiert werden.

Wenn die feste Zuweisungsgröße größer oder gleich einer Speicherseite ist, muss eine Hilfsfunktion aufgerufen werden, bevor RSP geändert wird. Dieser Hilfsprogramm `__chkstk`, untersucht den zuzuweisenden Stapelbereich, um sicherzustellen, dass der Stapel ordnungsgemäß erweitert wird. In diesem Fall wäre das vorherige Prolog-Beispiel stattdessen:

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

Der `__chkstk` Helfer ändert keine anderen Register als R10, R11 und die Konditionscodes. Insbesondere wird raX unverändert zurückgegeben und alle nichtflüchtigen Register und Argumentübergaberegister unverändert bleiben.

## <a name="epilog-code"></a>Epilog-Code

Epilog-Code ist bei jedem Ausgang einer Funktion vorhanden. Während es normalerweise nur einen Prolog gibt, kann es viele Epilogs geben. Der Epilog-Code schneidet den Stapel auf seine feste Zuweisungsgröße (falls erforderlich), ordnet die feste Stapelzuordnung auf, stellt nichtflüchtige Register wieder her, indem die gespeicherten Werte aus dem Stapel entfernt werden, und gibt zurück.

Der Epilogcode muss einem strengen Satz von Regeln folgen, damit der Entladungscode zuverlässig durch Ausnahmen und Interrupts abgesendet werden kann. Diese Regeln reduzieren die Menge an Entladungsdaten, da keine zusätzlichen Daten erforderlich sind, um jeden Epilog zu beschreiben. Stattdessen kann der Entladungscode feststellen, dass ein Epilog ausgeführt wird, indem ein Codestream vorwärts scannt wird, um einen Epilog zu identifizieren.

Wenn in der Funktion kein Framezeiger verwendet wird, muss der Epilog zuerst den festen Teil des Stapels aufheben, die nichtflüchtigen Register werden geknallt, und die Steuerung wird an die aufrufende Funktion zurückgegeben. Beispiel:

```MASM
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

Wenn ein Framezeiger in der Funktion verwendet wird, muss der Stapel vor der Ausführung des Epilogs auf seine feste Zuordnung getrimmt werden. Diese Aktion ist technisch nicht Teil des Epilogs. Beispielsweise könnte der folgende Epilog verwendet werden, um den zuvor verwendeten Prolog rückgängig zu machen:

```MASM
    lea      RSP, -128[R13]
    ; epilogue proper starts here
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

In der Praxis gibt es keinen guten Grund, RSP in zwei Schritten anzupassen, wenn ein Framezeiger verwendet wird, sodass stattdessen der folgende Epilog verwendet wird:

```MASM
    lea      RSP, fixed-allocation-size - 128[R13]
    pop      R13
    pop      R14
    pop      R15
    ret
```

Diese Formulare sind die einzigen legalen für einen Epilog. Es muss entweder `add RSP,constant` aus `lea RSP,constant[FPReg]`einem oder bestehen, gefolgt von einer Reihe von `return` Null- `jmp`oder mehr 8-Byte-Register-Pops und einem oder einem . (Nur eine Teilmenge von `jmp` Anweisungen ist im Epilog zulässig. Die Teilmenge ist ausschließlich `jmp` die Klasse von Anweisungen mit ModRM-Speicherverweisen, wobei der ModRM-Modfeldwert 00 ist. Die Verwendung `jmp` von Anweisungen im Epilog mit ModRM Mod Feldwert 01 oder 10 ist verboten. Weitere Informationen zu den zulässigen ModRM-Referenzen finden Sie in Tabelle A-15 im AMD x86-64 Architecture Programmer es Manual Volume 3: General Purpose and System Instructions.) Es kann kein anderer Code angezeigt werden. Insbesondere kann innerhalb eines Epilogs nichts geplant werden, einschließlich des Ladens eines Rückgabewerts.

Wenn kein Framezeiger verwendet wird, muss `add RSP,constant` der Epilog verwendet werden, um den festen Teil des Stapels zuverteilen. Es darf `lea RSP,constant[RSP]` stattdessen nicht verwendet werden. Diese Einschränkung ist vorhanden, sodass der Entladungscode bei der Suche nach Epilogs weniger Muster zu erkennen hat.

Wenn Sie diese Regeln befolgen, kann der Entladungscode feststellen, ob derzeit ein Epilog ausgeführt wird, und die Ausführung des restlichen Epilogs simulieren, um das Erneuterstellen des Kontexts der aufrufenden Funktion zu ermöglichen.

## <a name="see-also"></a>Siehe auch

[x64 Software-Konventionen](x64-software-conventions.md)
