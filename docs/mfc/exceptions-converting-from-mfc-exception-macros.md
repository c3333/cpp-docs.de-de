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
ms.openlocfilehash: 8a936a0af9927aa0dc453a93c98676a77f4ad6dc
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621753"
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>Ausnahmen: Umwandeln von MFC-Ausnahmemakros

Dies ist ein erweitertes Thema.

In diesem Artikel wird erläutert, wie vorhandener Code, der mit Microsoft Foundation Class-Makros – **try**, **catch**, **throw**usw. – geschrieben wurde, mit den Schlüsselwörtern " **try**", " **catch**" und " **throw**" der C++-Ausnahmebehandlung konvertiert wird Dabei werden folgende Themen behandelt:

- [Konvertierungs Vorteile](#_core_advantages_of_converting)

- [Umrechnen von Code mit Ausnahme Makros zur Verwendung von C++-Ausnahmen](#_core_doing_the_conversion)

## <a name="advantages-of-converting"></a><a name="_core_advantages_of_converting"></a>Vorteile der Umstellung

Sie müssen wahrscheinlich keinen vorhandenen Code konvertieren, obwohl Sie die Unterschiede zwischen den Makro Implementierungen in MFC-Version 3,0 und den Implementierungen in früheren Versionen kennen sollten. Diese Unterschiede und nachfolgende Änderungen im Code Verhalten werden unter [Ausnahmen: Änderungen an Ausnahme Makros in Version 3,0](exceptions-changes-to-exception-macros-in-version-3-0.md)erläutert.

Die wichtigsten Vorteile der-Typumwandlung sind:

- Code, der die C++-Ausnahme Behandlungs Schlüsselwörter verwendet, wird in eine etwas kleinere kompiliert. EXE oder. DLL.

- Die Schlüsselwörter der C++-Ausnahmebehandlung sind vielseitiger: Sie können Ausnahmen eines beliebigen Datentyps behandeln, der kopiert werden kann (**int**, **float**, **char**usw.), während die Makros nur Ausnahmen von Klassen und Klassen behandeln, die davon `CException` abgeleitet sind.

Der Hauptunterschied zwischen den Makros und den Schlüsselwörtern besteht darin, dass der Code, der die Makros verwendet, automatisch eine abgefangene Ausnahme löscht, wenn die Ausnahme den Gültigkeitsbereich verlässt. Code, der die Schlüsselwörter verwendet, ist nicht erforderlich, daher müssen Sie eine abgefangene Ausnahme explizit löschen. Weitere Informationen finden Sie im Artikel [Ausnahmen: abfangen und Löschen von Ausnahmen](exceptions-catching-and-deleting-exceptions.md).

Ein weiterer Unterschied ist die Syntax. Die Syntax für Makros und Schlüsselwörter unterscheidet sich in drei Punkten:

1. Makro Argumente und Ausnahme Deklarationen:

   Ein **catch** -Makro Aufruf weist die folgende Syntax auf:

   **Catch (** *exception_class*, *exception_object_pointer_name* **)**

   Beachten Sie das Komma zwischen dem Klassennamen und dem Namen des Objekt Zeigers.

   Die Ausnahme Deklaration für das **catch** -Schlüsselwort verwendet diese Syntax:

   **catch (** *exception_type* *exception_name* **)**

   Diese Ausnahme Deklarations Anweisung gibt den Typ der Ausnahme an, die der catch-Block behandelt.

2. Abgrenzung von catch-Blöcken:

   Mit den Makros beginnt das **catch** -Makro (mit den zugehörigen Argumenten) mit dem ersten catch-Block. Das **AND_CATCH** -Makro beginnt mit nachfolgenden catch-Blöcken, und das **END_CATCH** -Makro beendet die Sequenz der catch-Blöcke.

   Mit den Schlüsselwörtern beginnt das **catch** -Schlüsselwort (mit seiner Ausnahme Deklaration) jeden catch-Block. Es ist kein Pendant zum **END_CATCH** -Makro vorhanden. der catch-Block endet mit der schließenden geschweifte Klammer.

3. Der Throw-Ausdruck:

   Die Makros verwenden **THROW_LAST** , um die aktuelle Ausnahme erneut auszulösen. Das **throw** -Schlüsselwort ohne Argument hat denselben Effekt.

## <a name="doing-the-conversion"></a><a name="_core_doing_the_conversion"></a>Durchführung der Konvertierung

#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>So konvertieren Sie Code mithilfe von Makros für die Verwendung der C++-Ausnahme Behandlungs Schlüsselwörter

1. Suchen **Sie**alle Vorkommen der MFC-Makros try, **catch**, **AND_CATCH**, **END_CATCH**, **throw**und **THROW_LAST**.

2. Ersetzen oder löschen Sie alle Vorkommen der folgenden Makros:

   **Versuchen** Sie es (durch **try**ersetzen).

   **Catch** (durch **catch**ersetzen)

   **AND_CATCH** (durch **catch**ersetzen)

   **END_CATCH** (Löschen)

   **Throw** (durch **throw**ersetzen)

   **THROW_LAST** (durch **throw**ersetzen)

3. Ändern Sie die Makro Argumente so, dass Sie gültige Ausnahme Deklarationen bilden.

   Ändern Sie beispielsweise

   [!code-cpp[NVC_MFCExceptions#6](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]

   zu

   [!code-cpp[NVC_MFCExceptions#7](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]

4. Ändern Sie den Code in den catch-Blöcken, damit Ausnahme Objekte nach Bedarf gelöscht werden. Weitere Informationen finden Sie im Artikel [Ausnahmen: abfangen und Löschen von Ausnahmen](exceptions-catching-and-deleting-exceptions.md).

Im folgenden finden Sie ein Beispiel für einen Code zur Ausnahmebehandlung mithilfe von MFC-Ausnahme Makros. Beachten Sie, dass die Ausnahme automatisch gelöscht wird, da der Code im folgenden Beispiel die Makros verwendet `e` :

[!code-cpp[NVC_MFCExceptions#8](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]

Der Code im nächsten Beispiel verwendet die C++ Exception-Schlüsselwörter, daher muss die Ausnahme explizit gelöscht werden:

[!code-cpp[NVC_MFCExceptions#9](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]

Weitere Informationen finden Sie unter [Ausnahmen: Verwenden von MFC-Makros und C++-Ausnahmen](exceptions-using-mfc-macros-and-cpp-exceptions.md).

## <a name="see-also"></a>Siehe auch

[Ausnahmebehandlung](exception-handling-in-mfc.md)<br/>
