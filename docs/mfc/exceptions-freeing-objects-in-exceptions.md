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
ms.openlocfilehash: 49c7c6b0481f90baa23609c1bb1596deda49f7bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371989"
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>Ausnahmen: Freigeben von Objekten in Ausnahmen

In diesem Artikel werden die Notwendigkeit und die Methode zum Freiwerden von Objekten erläutert, wenn eine Ausnahme auftritt. Dabei werden folgende Themen behandelt:

- [Behandeln der Ausnahme lokal](#_core_handling_the_exception_locally)

- [Auslösen von Ausnahmen nach dem Zerstören von Objekten](#_core_throwing_exceptions_after_destroying_objects)

Ausnahmen, die vom Framework oder von Ihrer Anwendung ausgelöst werden, unterbrechen den normalen Programmfluss. Daher ist es sehr wichtig, Objekte genau zu verfolgen, damit Sie sie ordnungsgemäß entsorgen können, falls eine Ausnahme ausgelöst wird.

Dazu gibt es zwei primäre Methoden.

- Behandeln Sie Ausnahmen lokal mit den **try** and **catch-Schlüsselwörtern,** und zerstören Sie dann alle Objekte mit einer Anweisung.

- Zerstören Sie jedes Objekt im **Catch-Block,** bevor Sie die Ausnahme zur weiteren Behandlung außerhalb des Blocks auslösen.

Diese beiden Ansätze werden im Folgenden als Lösung für das folgende problematische Beispiel veranschaulicht:

[!code-cpp[NVC_MFCExceptions#14](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]

Wie oben `myPerson` geschrieben, wird nicht gelöscht, `SomeFunc`wenn eine Ausnahme von ausgelöst wird. Die Ausführung springt direkt zum nächsten äußeren Ausnahmehandler, unter Umgehung des normalen Funktionsausgangs und des Codes, der das Objekt löscht. Der Zeiger auf das Objekt geht aus dem Gültigkeitsbereich, wenn die Ausnahme die Funktion verlässt, und der vom Objekt belegte Speicher wird nie wiederhergestellt, solange das Programm ausgeführt wird. Dies ist ein Speicherleck; Sie wird mithilfe der Speicherdiagnose erkannt.

## <a name="handling-the-exception-locally"></a><a name="_core_handling_the_exception_locally"></a>Behandeln der Ausnahme lokal

Das **try/catch-Paradigma** bietet eine defensive Programmiermethode, um Speicherverluste zu vermeiden und sicherzustellen, dass Ihre Objekte zerstört werden, wenn Ausnahmen auftreten. Beispielsweise könnte das oben in diesem Artikel gezeigte Beispiel wie folgt umgeschrieben werden:

[!code-cpp[NVC_MFCExceptions#15](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]

In diesem neuen Beispiel wird ein Ausnahmehandler eingerichtet, um die Ausnahme abzufangen und lokal zu behandeln. Anschließend wird die Funktion normal beendet und das Objekt zerstört. Der wichtige Aspekt dieses Beispiels ist, dass ein Kontext zum Abfangen der Ausnahme mit den **try/catch-Blöcken** eingerichtet wird. Ohne einen lokalen Ausnahmerahmen würde die Funktion nie wissen, dass eine Ausnahme ausgelöst wurde, und hätte nicht die Möglichkeit, das Objekt normal zu beenden und zu zerstören.

## <a name="throwing-exceptions-after-destroying-objects"></a><a name="_core_throwing_exceptions_after_destroying_objects"></a>Auslösen von Ausnahmen nach dem Zerstören von Objekten

Eine andere Möglichkeit, Ausnahmen zu behandeln, besteht darin, sie an den nächsten äußeren Ausnahmebehandlungskontext weiterzugeben. In Ihrem **Catch-Block** können Sie einige Bereinigungen Ihrer lokal zugewiesenen Objekte tun und dann die Ausnahme zur weiteren Verarbeitung auslösen.

Die Wurffunktion muss heap-Objekte möglicherweise deallocatezuweisen. Wenn die Funktion das Heapobjekt immer auflöst, bevor es im normalen Fall zurückgegeben wird, sollte die Funktion auch das Heapobjekt aufteilen, bevor die Ausnahme ausgelöst wird. Wenn die Funktion hingegen das Objekt normalerweise nicht abteilt, bevor es im Normalfall zurückgegeben wird, müssen Sie von Fall zu Fall entscheiden, ob das Heapobjekt zugeordnet werden soll.

Das folgende Beispiel zeigt, wie lokal zugeordnete Objekte bereinigt werden können:

[!code-cpp[NVC_MFCExceptions#16](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]

Der Ausnahmemechanismus weist Frameobjekte automatisch auf. der Destruktor des Frameobjekts wird auch aufgerufen.

Wenn Sie Funktionen aufrufen, die Ausnahmen auslösen können, können Sie **try/catch-Blöcke** verwenden, um sicherzustellen, dass Sie die Ausnahmen abfangen und die Möglichkeit haben, alle von Ihnen erstellten Objekte zu zerstören. Beachten Sie insbesondere, dass viele MFC-Funktionen Ausnahmen auslösen können.

Weitere Informationen finden Sie unter [Ausnahmen: Abfangen und Löschen von Ausnahmen](../mfc/exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Siehe auch

[Ausnahmebehandlung](../mfc/exception-handling-in-mfc.md)
