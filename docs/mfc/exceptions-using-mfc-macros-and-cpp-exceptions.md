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
ms.openlocfilehash: d669c58da04a1cd0ead424d93f6fad6adcd4c56c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622730"
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>Ausnahmen: Verwenden von MFC-Makros und C++-Ausnahmen

In diesem Artikel werden Überlegungen zum Schreiben von Code erläutert, der sowohl die MFC-Ausnahme Behandlungs Makros als auch die Schlüsselwörter der C++-Ausnahmebehandlung verwendet.

In diesem Artikel werden die folgenden Themen behandelt:

- [Mischen von Ausnahme Schlüsselwörtern und Makros](#_core_mixing_exception_keywords_and_macros)

- [Try-Blöcke innerhalb von catch-Blöcken](#_core_try_blocks_inside_catch_blocks)

## <a name="mixing-exception-keywords-and-macros"></a><a name="_core_mixing_exception_keywords_and_macros"></a>Mischen von Ausnahme Schlüsselwörtern und Makros

Sie können MFC-Ausnahme Makros und C++-Ausnahme Schlüsselwörter in demselben Programm mischen. MFC-Makros können jedoch nicht mit C++ Exception-Schlüsselwörtern im selben Block gemischt werden, da die Makros Ausnahme Objekte automatisch löschen, wenn Sie den Gültigkeitsbereich verlassen, während der Code, der die Schlüsselwörter für die Ausnahmebehandlung verwendet, nicht funktioniert. Weitere Informationen finden Sie im Artikel [Ausnahmen: abfangen und Löschen von Ausnahmen](exceptions-catching-and-deleting-exceptions.md).

Der Hauptunterschied zwischen den Makros und den Schlüsselwörtern besteht darin, dass die Makros automatisch eine abgefangene Ausnahme löschen, wenn die Ausnahme den Gültigkeitsbereich verlässt. Code, der die Schlüsselwörter verwendet, ist nicht. in einem catch-Block aufgefangene Ausnahmen müssen explizit gelöscht werden. Das Mischen von Makros und C++-Ausnahme Schlüsselwörtern kann zu Speicher Verlusten führen, wenn ein Ausnahme Objekt nicht gelöscht wird, oder eine Heap Beschädigung, wenn eine Ausnahme zweimal gelöscht wird.

Der folgende Code macht z. b. den Ausnahme Zeiger ungültig:

[!code-cpp[NVC_MFCExceptions#10](codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]

Das Problem tritt auf `e` , weil gelöscht wird, wenn die Ausführung aus dem "inneren" **catch** -Block übergeht. Wenn das **THROW_LAST** -Makro anstelle der **throw** -Anweisung verwendet wird, erhält der "äußere" **catch** -Block einen gültigen Zeiger:

[!code-cpp[NVC_MFCExceptions#11](codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]

## <a name="try-blocks-inside-catch-blocks"></a><a name="_core_try_blocks_inside_catch_blocks"></a>Try-Blöcke innerhalb von catch-Blöcken

Sie können die aktuelle Ausnahme nicht innerhalb eines **try** -Blocks, der sich innerhalb eines **catch** -Blocks befindet, erneut auslösen. Das folgende Beispiel ist ungültig:

[!code-cpp[NVC_MFCExceptions#12](codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]

Weitere Informationen finden Sie unter [Ausnahmen: Untersuchen von Ausnahme Inhalten](exceptions-examining-exception-contents.md).

## <a name="see-also"></a>Siehe auch

[Ausnahmebehandlung](exception-handling-in-mfc.md)
