---
title: 'Ausnahmen: Verwenden von MFC-Makros und C++-Ausnahmen'
ms.date: 11/04/2016
helpviewer_keywords:
- exception objects [MFC]
- memory leaks [MFC], exception object not deleted
- exception handling [MFC], MFC
- try-catch exception handling [MFC], mixing MFC macros and C++ keywords
- exception objects [MFC], deleting
- exceptions [MFC], MFC macros vs. C++ keywords
- catch blocks [MFC], mixed
- exception handling [MFC], mixed-language
- nested try blocks [MFC]
- catch blocks [MFC], explicitly deleting code in
- try-catch exception handling [MFC], nested try blocks
- heap corruption [MFC]
- nested catch blocks [MFC]
ms.assetid: d664a83d-879b-44d4-bdf0-029f0aca69e9
ms.openlocfilehash: afad5335bedf001329ecb401a8a16c663afb5571
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371590"
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>Ausnahmen: Verwenden von MFC-Makros und C++-Ausnahmen

In diesem Artikel werden Überlegungen zum Schreiben von Code erläutert, der sowohl die MFC-Ausnahmebehandlungsmakros als auch die C++-Schlüsselwörter für die Ausnahmebehandlung verwendet.

In diesem Artikel werden die folgenden Themen behandelt:

- [Mischen von Ausnahmeschlüsselwörtern und Makros](#_core_mixing_exception_keywords_and_macros)

- [Versuchen Sie Blöcke in Catch-Blöcken](#_core_try_blocks_inside_catch_blocks)

## <a name="mixing-exception-keywords-and-macros"></a><a name="_core_mixing_exception_keywords_and_macros"></a>Mischen von Ausnahmeschlüsselwörtern und Makros

Sie können MFC-Ausnahmemakros und C++-Ausnahmeschlüsselwörter im selben Programm mischen. Sie können jedoch MFC-Makros nicht mit C++-Ausnahmeschlüsselwörtern im gleichen Block mischen, da die Makros Ausnahmeobjekte automatisch löschen, wenn sie den Gültigkeitsbereich nicht erweitern, während Code, der die Schlüsselwörter für die Ausnahmebehandlung verwendet, dies nicht tut. Weitere Informationen finden Sie im Artikel [Ausnahmen: Abfangen und Löschen von Ausnahmen](../mfc/exceptions-catching-and-deleting-exceptions.md).

Der Hauptunterschied zwischen den Makros und den Schlüsselwörtern besteht darin, dass die Makros "automatisch" eine abgefangene Ausnahme löschen, wenn die Ausnahme den Gültigkeitsbereich verlässt. Code, der die Schlüsselwörter verwendet, nicht; Ausnahmen, die in einem Catch-Block abgefangen werden, müssen explizit gelöscht werden. Das Mischen von Makros und C++-Ausnahmeschlüsselwörtern kann speicherfehler verursachen, wenn ein Ausnahmeobjekt nicht gelöscht wird, oder zu einer Heapbeschädigung, wenn eine Ausnahme zweimal gelöscht wird.

Der folgende Code macht z. B. den Ausnahmezeiger ungültig:

[!code-cpp[NVC_MFCExceptions#10](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]

Das Problem `e` tritt auf, weil gelöscht wird, wenn die Ausführung aus dem "inneren" **CATCH-Block** herausgeht. Die **THROW_LAST** Verwendung des THROW_LAST-Makros anstelle der **THROW-Anweisung** bewirkt, dass der "äußere" **CATCH-Block** einen gültigen Zeiger erhält:

[!code-cpp[NVC_MFCExceptions#11](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]

## <a name="try-blocks-inside-catch-blocks"></a><a name="_core_try_blocks_inside_catch_blocks"></a>Versuchen Sie Blöcke in Catch Blocks

Sie können die aktuelle Ausnahme nicht **try** innerhalb eines try-Blocks, der sich innerhalb eines **CATCH-Blocks** befindet, erneut auslösen. Das folgende Beispiel ist ungültig:

[!code-cpp[NVC_MFCExceptions#12](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]

Weitere Informationen finden Sie unter [Ausnahmen: Untersuchen von Ausnahmeinhalten](../mfc/exceptions-examining-exception-contents.md).

## <a name="see-also"></a>Siehe auch

[Ausnahmebehandlung](../mfc/exception-handling-in-mfc.md)
