---
title: Verwenden von setjmp und longjmp
ms.date: 08/14/2018
f1_keywords:
- longjmp_cpp
- setjmp_cpp
helpviewer_keywords:
- C++ exception handling, setjmp/longjmp functions
- setjmpex.h
- longjmp function in C++ programs
- setjmp.h
- setjmp function
- setjmp function, C++ programs
ms.assetid: 96be8816-f6f4-4567-9a9c-0c3c720e37c5
ms.openlocfilehash: 6adbe22eb684c9a1dda080f6d35a99c55d6c3d30
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226996"
---
# <a name="using-setjmp-and-longjmp"></a>Verwenden von setjmp und longjmp

Wenn [setjmp](../c-runtime-library/reference/setjmp.md) und [longjmp](../c-runtime-library/reference/longjmp.md) verwendet werden, bieten Sie eine Möglichkeit, eine nicht lokale auszuführen **`goto`** . Sie werden in der Regel in C-Code verwendet, um die Ausführungs Steuerung an den Fehler Behandlungs-oder Wiederherstellungscode in einer vorher aufgerufenen Routine zu übergeben, ohne die Standard Aufruf-oder Rückgabe Konventionen zu verwenden

> [!CAUTION]
> Da `setjmp` und `longjmp` die korrekte Zerstörung von Stapel Rahmen Objekten zwischen C++-Compilern nicht unterstützen, und da Sie die Leistung beeinträchtigen können, indem Sie die Optimierung lokaler Variablen verhindern, wird die Verwendung in C++-Programmen nicht empfohlen. Es wird empfohlen, **`try`** stattdessen und- **`catch`** Konstrukte zu verwenden.

Wenn Sie sich entscheiden, `setjmp` und `longjmp` in einem C++-Programm zu verwenden, schließen Sie auch oder ein, \<setjmp.h> \<setjmpex.h> um die korrekte Interaktion zwischen den Funktionen und der Strukturierung (strukturierte Ausnahmebehandlung) oder der C++-Ausnahmebehandlung sicherzustellen.

**Microsoft-spezifisch**

Wenn Sie C++-Code mithilfe einer [/eh](../build/reference/eh-exception-handling-model.md) -Option kompilieren, werden debugtoren für lokale Objekte während der Stapel Entladung aufgerufen. Wenn Sie jedoch " **/EHS** " oder " **/EHsc** " verwenden, um zu kompilieren, und eine der Funktionen, die " [noaußer](../cpp/noexcept-cpp.md) "-Aufrufe verwenden `longjmp` , kann die debuggerentladung für diese Funktion abhängig vom Status des Optimierers möglicherweise nicht ausgeführt werden.

Wenn in tragbarem Code ein-Befehl `longjmp` ausgeführt wird, wird die korrekte Zerstörung von Frame basierten Objekten explizit nicht durch den Standard gewährleistet und wird möglicherweise von anderen Compilern nicht unterstützt. Um Sie auf Warnstufe 4 zu informieren, verursacht ein-Rückruf eine `setjmp` Warnung C4611: die Interaktion zwischen ' _setjmp ' und der C++-Objekt Zerstörung ist nicht portabel.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Mischen von C (strukturiert)-und C++-Ausnahmen](../cpp/mixing-c-structured-and-cpp-exceptions.md)
