---
title: 'Ausnahmen: Freigeben von Objekten in Ausnahmen'
ms.date: 11/04/2016
helpviewer_keywords:
- throwing exceptions [MFC], freeing objects in exceptions
- local exception handling
- memory leaks, caused by exception
- try-catch exception handling [MFC], destroying objects
- destroying objects [MFC]
- freeing objects [MFC]
- throwing exceptions [MFC], after destroying
- exception handling [MFC], destroying objects
ms.assetid: 3b14b4ee-e789-4ed2-b8e3-984950441d97
ms.openlocfilehash: e4fafd12d22f6ff7635380e139f60c110a193d9d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622828"
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>Ausnahmen: Freigeben von Objekten in Ausnahmen

In diesem Artikel werden die Notwendigkeit und die Methode zum Freigeben von Objekten erläutert, wenn eine Ausnahme auftritt. Dabei werden folgende Themen behandelt:

- [Lokales behandeln der Ausnahme](#_core_handling_the_exception_locally)

- [Auslösen von Ausnahmen nach dem Zerstören von Objekten](#_core_throwing_exceptions_after_destroying_objects)

Ausnahmen, die vom Framework oder von Ihrer Anwendung ausgelöst werden, unterbrechen den normalen Programmfluss. Daher ist es sehr wichtig, die Objekte zu schließen, damit Sie sie ordnungsgemäß verwerfen können, wenn eine Ausnahme ausgelöst wird.

Hierfür gibt es zwei primäre Methoden.

- Behandeln Sie Ausnahmen lokal mithilfe der Schlüsselwörter "Try" und " **catch** ", und zerstören **Sie** alle Objekte mit einer Anweisung.

- Zerstören Sie alle-Objekte im **catch** -Block, bevor Sie die Ausnahme außerhalb des-Blocks zur weiteren Behandlung auslösen.

Diese beiden Ansätze sind unten als Lösungen für das folgende problematische Beispiel dargestellt:

[!code-cpp[NVC_MFCExceptions#14](codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]

Wie oben beschrieben, `myPerson` wird nicht gelöscht, wenn eine Ausnahme von ausgelöst wird `SomeFunc` . Die Ausführung springt direkt zum nächsten äußeren Ausnahmehandler und umgeht dabei den normalen Funktions Abschluss und den Code, der das Objekt löscht. Der Zeiger auf das Objekt verlässt den Gültigkeitsbereich, wenn die Ausnahme die Funktion verlässt, und der vom Objekt belegte Arbeitsspeicher wird nie wieder hergestellt, solange das Programm ausgeführt wird. Dies ist ein Arbeits Speicherleck. Es wird mithilfe der Speicher Diagnose erkannt.

## <a name="handling-the-exception-locally"></a><a name="_core_handling_the_exception_locally"></a>Lokales behandeln der Ausnahme

Das **try/catch-** Paradigma bietet eine defensive Programmiermethode, um Speicher Verluste zu vermeiden und sicherzustellen, dass Ihre Objekte zerstört werden, wenn Ausnahmen auftreten. Das Beispiel, das weiter oben in diesem Artikel gezeigt wurde, könnte z. b. wie folgt umgeschrieben werden:

[!code-cpp[NVC_MFCExceptions#15](codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]

Dieses neue Beispiel richtet einen Ausnahmehandler ein, um die Ausnahme abzufangen und lokal zu verarbeiten. Anschließend wird die Funktion normal beendet und das-Objekt zerstört. Der wichtige Aspekt dieses Beispiels ist, dass ein Kontext zum Abfangen der Ausnahme mit den **try/catch-** Blöcken hergestellt wird. Ohne einen lokalen Ausnahme Rahmen hätte die Funktion nie festzustellen, dass eine Ausnahme ausgelöst wurde und nicht die Möglichkeit hat, normal zu beenden und das Objekt zu zerstören.

## <a name="throwing-exceptions-after-destroying-objects"></a><a name="_core_throwing_exceptions_after_destroying_objects"></a>Auslösen von Ausnahmen nach dem Zerstören von Objekten

Eine andere Möglichkeit, Ausnahmen zu behandeln, besteht darin, Sie an den nächsten äußeren Ausnahme behandlungskontext zu übergeben. In Ihrem **catch** -Block können Sie einige Bereinigungs Vorgänge für Ihre lokal zugeordneten Objekte durchführen und dann die Ausnahme für zur weiteren Verarbeitung auslösen.

Die auslösende Funktion muss möglicherweise Heap Objekte nicht mehr zuordnen. Wenn die Funktion immer das Heap Objekt zuordnet, bevor Sie im Normalfall zurückgegeben wird, sollte die Funktion die Zuordnung des Heap Objekts vor dem Auslösen der Ausnahme auch aufgehoben. Wenn die Funktion die Zuordnung des Objekts in der Regel vor der Rückgabe im Normalfall jedoch nicht durchführt, müssen Sie sich für eine Fall Weise entscheiden, ob die Zuordnung des Heap Objekts aufgehoben werden soll.

Im folgenden Beispiel wird gezeigt, wie lokal zugeordnete Objekte bereinigt werden können:

[!code-cpp[NVC_MFCExceptions#16](codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]

Der Ausnahme Mechanismus hebt automatisch die Zuordnung von Frame Objekten auf. der Dekonstruktor des Frame-Objekts wird ebenfalls aufgerufen.

Wenn Sie Funktionen aufzurufen, die Ausnahmen auslösen können, können Sie **try/catch-** Blöcke verwenden, um sicherzustellen, dass Sie die Ausnahmen abfangen und die Möglichkeit haben, alle von Ihnen erstellten Objekte zu zerstören. Beachten Sie insbesondere, dass viele MFC-Funktionen Ausnahmen auslösen können.

Weitere Informationen finden Sie unter [Ausnahmen: abfangen und Löschen von Ausnahmen](exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Siehe auch

[Ausnahmebehandlung](exception-handling-in-mfc.md)
