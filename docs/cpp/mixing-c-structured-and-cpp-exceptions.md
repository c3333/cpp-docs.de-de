---
title: Mischen von C (strukturiert)-und C++-Ausnahmen
ms.date: 08/14/2018
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
ms.openlocfilehash: 72ddde9bc284a005c77694d599a8e9a3908cb2d0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233690"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>Mischen von C (strukturiert)-und C++-Ausnahmen

Wenn Sie portablen Code schreiben möchten, wird die Verwendung der strukturierten Ausnahmebehandlung (SEH) in einem C++-Programm nicht empfohlen. Es kann jedoch vorkommen, dass Sie die Kompilierung mithilfe von [/EHa](../build/reference/eh-exception-handling-model.md) durcharbeiten und strukturierte Ausnahmen und C++-Quellcode mischen möchten, und einige Möglichkeiten benötigen, beide Arten von Ausnahmen zu verarbeiten. Da ein strukturierter Ausnahmehandler kein Konzept von Objekten oder typisierten Ausnahmen hat, kann er keine Ausnahmen verarbeiten, die von C++-Code ausgelöst werden. Allerdings können C++- **`catch`** Handler strukturierte Ausnahmen verarbeiten. Die Syntax der C++-Ausnahmebehandlung ( **`try`** , **`throw`** , **`catch`** ) wird vom C-Compiler nicht akzeptiert, aber die Syntax für die strukturierte Ausnahmebehandlung (**__try**, **`__except`** , **`__finally`** ) wird vom C++-Compiler unterstützt.

Informationen dazu, wie Sie strukturierte Ausnahmen als C++-Ausnahmen behandeln können, finden Sie unter [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) .

Wenn Sie strukturierte und C++-Ausnahmen kombinieren, beachten Sie diese potenziellen Probleme:

- C++-Ausnahmen und strukturierte Ausnahmen können nicht in derselben Funktion kombiniert werden.

- Beendigungs Handler ( **`__finally`** Blöcke) werden immer ausgeführt, auch während der Entwicklung, nachdem eine Ausnahme ausgelöst wurde.

- Durch die C++-Ausnahmebehandlung können Entlade Semantik in allen Modulen abgefangen und beibehalten werden, die mit den [/eh](../build/reference/eh-exception-handling-model.md) -Compileroptionen kompiliert werden, die die Entlade Semantik ermöglichen

- Es kann Situationen geben, in denen Destruktorfunktionen nicht für alle Objekte aufgerufen werden. Wenn beispielsweise eine strukturierte Ausnahme beim Versuch auftritt, einen Funktionsaufruf über einen nicht initialisierten Funktionszeiger durchführen, und diese Funktion als Parameter Objekte annimmt, die vor dem Aufruf erstellt wurden, werden die destrukturtoren dieser Objekte während der Stapel Entladung nicht aufgerufen.

## <a name="next-steps"></a>Nächste Schritte

- [Verwenden von setjmp oder longjmp in C++-Programmen](../cpp/using-setjmp-longjmp.md)

  Weitere Informationen zur Verwendung von `setjmp` und in C++-Programmen finden Sie unter `longjmp` .

- [Behandeln strukturierter Ausnahmen in C++](../cpp/exception-handling-differences.md)

  Weitere Informationen finden Sie unter Beispiele für die Verwendung von C++, um strukturierte Ausnahmen zu behandeln.

## <a name="see-also"></a>Siehe auch

[Modern C++ bewährte Methoden für Ausnahmen und Fehlerbehandlung](../cpp/errors-and-exception-handling-modern-cpp.md)
