---
title: Mischen von C (strukturiert)-und C++-Ausnahmen
description: So mischen Sie die strukturierte Ausnahmebehandlung und C++-Ausnahmen sowie einige potenzielle Probleme.
ms.date: 08/24/2020
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
ms.openlocfilehash: 98ce2335ff3b08b7a5d71e03305c481ba068e5e6
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898404"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>Mischen von C (strukturiert)-und C++-Ausnahmen

Wenn Sie portablen Code schreiben möchten, wird die Verwendung der strukturierten Ausnahmebehandlung (SEH) in einem C++-Programm nicht empfohlen. Es kann jedoch vorkommen, dass Sie mithilfe [`/EHa`](../build/reference/eh-exception-handling-model.md) von kompilieren und strukturierte Ausnahmen und C++-Quellcode kombinieren möchten, und einige Möglichkeiten zum Behandeln beider Arten von Ausnahmen benötigen. Da ein strukturierter Ausnahmehandler kein Konzept von Objekten oder typisierten Ausnahmen hat, kann er keine Ausnahmen verarbeiten, die von C++-Code ausgelöst werden. Allerdings können C++- **`catch`** Handler strukturierte Ausnahmen verarbeiten. Die Syntax der C++-Ausnahmebehandlung ( **`try`** , **`throw`** , **`catch`** ) wird vom C-Compiler nicht akzeptiert, aber die Syntax für die strukturierte Ausnahmebehandlung ( **`__try`** , **`__except`** , **`__finally`** ) wird vom C++-Compiler unterstützt.

[`_set_se_translator`](../c-runtime-library/reference/set-se-translator.md)Informationen dazu, wie strukturierte Ausnahmen als C++-Ausnahmen behandelt werden, finden Sie unter.

Wenn Sie strukturierte und C++-Ausnahmen kombinieren, beachten Sie diese potenziellen Probleme:

- C++-Ausnahmen und strukturierte Ausnahmen können nicht innerhalb derselben Funktion gemischt werden.

- Beendigungs Handler ( **`__finally`** Blöcke) werden immer ausgeführt, auch während der Entwicklung, nachdem eine Ausnahme ausgelöst wurde.

- Die C++-Ausnahmebehandlung kann die Entlade Semantik in allen Modulen, die mit den [`/EH`](../build/reference/eh-exception-handling-model.md) Compileroptionen kompiliert werden, erfassen und beibehalten, wodurch die Entlade Semantik aktiviert wird.

- Es kann Situationen geben, in denen Debuggerfunktionen nicht für alle Objekte aufgerufen werden. Beispielsweise kann eine strukturierte Ausnahme auftreten, wenn versucht wird, einen Funktions aufzurufen über einen nicht initialisierten Funktionszeiger zu erstellen. Wenn es sich bei den Funktionsparametern um Objekte handelt, die vor dem Aufruf erstellt werden, werden die Dekonstruktoren dieser Objekte nicht während der Stapel Entladung aufgerufen.

## <a name="next-steps"></a>Nächste Schritte

- [Verwenden von `setjmp` oder `longjmp` in C++-Programmen](../cpp/using-setjmp-longjmp.md)

  Weitere Informationen zur Verwendung von `setjmp` und in C++-Programmen finden Sie unter `longjmp` .

- [Behandeln strukturierter Ausnahmen in C++](../cpp/exception-handling-differences.md)

  Weitere Informationen finden Sie unter Beispiele für die Verwendung von C++, um strukturierte Ausnahmen zu behandeln.

## <a name="see-also"></a>Weitere Informationen

[Modern C++ bewährte Methoden für Ausnahmen und Fehlerbehandlung](../cpp/errors-and-exception-handling-modern-cpp.md)
