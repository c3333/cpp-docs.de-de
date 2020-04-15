---
title: 'Ausnahmen: Umwandeln von MFC-Ausnahmemakros'
ms.date: 08/27/2018
helpviewer_keywords:
- converting exceptions [MFC]
- exception objects [MFC]
- conversions [MFC], code written with MFC macros
- keywords [MFC], macros
- macrosv, C++ keywords
- exception objects [MFC], deleting
- CException class [MFC], deleting CException class objects
- exceptions [MFC], converting
- exceptions [MFC], deleting exception objects
- catch blocks [MFC], delimiting
- exception handling [MFC], converting exceptions
ms.assetid: bd3ac3b3-f3ce-4fdd-a168-a2cff13ed796
ms.openlocfilehash: 330f66b1f46542082637645ad53da016b434d4a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372015"
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>Ausnahmen: Umwandeln von MFC-Ausnahmemakros

Dies ist ein fortgeschrittenes Thema.

In diesem Artikel wird erläutert, wie Sie vorhandenen Code konvertieren, der mit Makros der Microsoft Foundation-Klasse geschrieben wurde – **TRY**, **CATCH**, **THROW**usw. –, um die C++-Ausnahmebehandlungsschlüsselwörter **try**, **catch**und **throw**zu verwenden. Dabei werden folgende Themen behandelt:

- [Konvertierungsvorteile](#_core_advantages_of_converting)

- [Konvertieren von Code mit Ausnahmemakros zur Verwendung von C++-Ausnahmen](#_core_doing_the_conversion)

## <a name="advantages-of-converting"></a><a name="_core_advantages_of_converting"></a>Vorteile des Konvertierens

Sie müssen wahrscheinlich keinen vorhandenen Code konvertieren, obwohl Sie sich der Unterschiede zwischen den Makroimplementierungen in MFC Version 3.0 und den Implementierungen in früheren Versionen bewusst sein sollten. Diese Unterschiede und nachfolgenden Änderungen im Codeverhalten werden in [Ausnahmen: Änderungen an Ausnahmemakros in Version 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)erläutert.

Die wichtigsten Vorteile der Konvertierung sind:

- Code, der die C++-Ausnahmebehandlungsschlüsselwörter verwendet, wird zu einer etwas kleineren kompiliert. EXE oder . Dll.

- Die C++-Ausnahmebehandlungsschlüsselwörter sind vielseitiger: Sie können Ausnahmen von jedem Datentyp **float**verarbeiten, der kopiert werden kann **(int**, float `CException` , **char**usw.), während die Makros Ausnahmen nur von Klassen und von ihr abgeleiteten Klassen behandeln.

Der Hauptunterschied zwischen den Makros und den Schlüsselwörtern besteht darin, dass Code, der die Makros "automatisch" verwendet, eine abgefangene Ausnahme löscht, wenn die Ausnahme den Gültigkeitsbereich verlässt. Code, der die Schlüsselwörter verwendet, ist dies nicht, daher müssen Sie eine abgefangene Ausnahme explizit löschen. Weitere Informationen finden Sie im Artikel [Ausnahmen: Abfangen und Löschen von Ausnahmen](../mfc/exceptions-catching-and-deleting-exceptions.md).

Ein weiterer Unterschied ist die Syntax. Die Syntax für Makros und Schlüsselwörter unterscheidet sich in drei Punkten:

1. Makroargumente und Ausnahmedeklarationen:

   Ein **CATCH** CATCH-Makroaufruf hat die folgende Syntax:

   **CATCH(** *exception_class*, *exception_object_pointer_name* **)**

   Beachten Sie das Komma zwischen dem Klassennamen und dem Objektzeigernamen.

   Die Ausnahmedeklaration für das **catch-Schlüsselwort** verwendet diese Syntax:

   **fang(** *exception_type* *exception_name* **)**

   Diese Ausnahmedeklarationsanweisung gibt den Typ der Ausnahme an, die der catch-Block behandelt.

2. Abgrenzung von Fangblöcken:

   Mit den Makros beginnt das **CATCH-Makro** (mit seinen Argumenten) den ersten catch-Block; Das **AND_CATCH-Makro** beginnt nachfolgende Catch-Blöcke, und das **END_CATCH-Makro** beendet die Sequenz der Catch-Blöcke.

   Mit den Schlüsselwörtern beginnt das **catch-Schlüsselwort** (mit seiner Ausnahmedeklaration) jeden catch-Block. Es gibt kein **END_CATCH** Gegenstück zum END_CATCH-Makro; der catch-Block endet mit seiner schließenden Klammer.

3. Der Wurfausdruck:

   Die Makros verwenden **THROW_LAST,** um die aktuelle Ausnahme erneut auszulösen. Das **throw** throw-Schlüsselwort ohne Argument hat den gleichen Effekt.

## <a name="doing-the-conversion"></a><a name="_core_doing_the_conversion"></a>Die Konvertierung durchführen

#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>So konvertieren Sie Code mithilfe von Makros zur Verwendung der C++-Ausnahmebehandlungsschlüsselwörter

1. Suchen Sie alle Vorkommen der MFC-Makros **TRY**, **CATCH**, **AND_CATCH**, **END_CATCH**, **THROW**und **THROW_LAST**.

2. Ersetzen oder löschen Sie alle Vorkommen der folgenden Makros:

   **TRY** (Ersetzen Sie es durch **versuchen**)

   **CATCH** (Ersetzen Sie es durch **catch**)

   **AND_CATCH** (Ersetzen Sie es durch **catch**)

   **END_CATCH** (Löschen)

   **THROW** (Ersetzen Sie es durch **Wurf**)

   **THROW_LAST** (Ersetzen Sie es durch **Wurf**)

3. Ändern Sie die Makroargumente so, dass sie gültige Ausnahmedeklarationen bilden.

   Ändern Sie beispielsweise

   [!code-cpp[NVC_MFCExceptions#6](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]

   zu

   [!code-cpp[NVC_MFCExceptions#7](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]

4. Ändern Sie den Code in den Catch-Blöcken so, dass bei Bedarf Ausnahmeobjekte gelöscht werden. Weitere Informationen finden Sie im Artikel [Ausnahmen: Abfangen und Löschen von Ausnahmen](../mfc/exceptions-catching-and-deleting-exceptions.md).

Hier ist ein Beispiel für Ausnahmebehandlungscode mit MFC-Ausnahmemakros. Da der Code im folgenden Beispiel die Makros `e` verwendet, wird die Ausnahme automatisch gelöscht:

[!code-cpp[NVC_MFCExceptions#8](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]

Der Code im nächsten Beispiel verwendet die C++-Ausnahmeschlüsselwörter, daher muss die Ausnahme explizit gelöscht werden:

[!code-cpp[NVC_MFCExceptions#9](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]

Weitere Informationen finden Sie unter [Ausnahmen: Verwenden von MFC-Makros und C++-Ausnahmen](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

## <a name="see-also"></a>Siehe auch

[Ausnahmebehandlung](../mfc/exception-handling-in-mfc.md)<br/>
