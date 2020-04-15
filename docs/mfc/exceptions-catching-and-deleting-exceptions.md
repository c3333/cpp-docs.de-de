---
title: 'Ausnahmen: Abfangen und Löschen von Ausnahmen'
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions [MFC], deleting
- AND_CATCH macro [MFC]
- try-catch exception handling [MFC], catching and deleting exceptions
- exception handling [MFC], catching and deleting exceptions
- catch blocks [MFC], catching and deleting exceptions
- execution [MFC], returns from within catch block
ms.assetid: 7c233ff0-89de-4de0-a68a-9e9cdb164311
ms.openlocfilehash: 74022c8bc6af1d2cdf74fa452d4e0483637e542e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365519"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>Ausnahmen: Abfangen und Löschen von Ausnahmen

Die folgenden Anweisungen und Beispiele zeigen Ihnen, wie Sie Ausnahmen abfangen und löschen. Weitere Informationen zu **try**, **catch**und **throw** keywords finden Sie unter Bewährte Methoden für [moderne C++-Methoden für Ausnahmen und Fehlerbehandlung](../cpp/errors-and-exception-handling-modern-cpp.md).

Die Ausnahmehandler müssen Ausnahmeobjekte löschen, die sie behandeln, da das Nichtlöschen der Ausnahme einen Speicherverlust verursacht, wenn dieser Code eine Ausnahme abfängt.

Ihr **catch-Block** muss eine Ausnahme löschen, wenn:

- Der **catch-Block** löst eine neue Ausnahme aus.

   Natürlich dürfen Sie die Ausnahme nicht löschen, wenn Sie dieselbe Ausnahme erneut auslösen:

   [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- Die Ausführung kehrt innerhalb des **catch-Blocks** zurück.

> [!NOTE]
> Verwenden Sie `CException`beim `Delete` Löschen einer , die Memberfunktion, um die Ausnahme zu löschen. Verwenden Sie das **Schlüsselwort delete** nicht, da es fehlschlagen kann, wenn sich die Ausnahme nicht auf dem Heap befindet.

#### <a name="to-catch-and-delete-exceptions"></a>So fangen und löschen Sie Ausnahmen

1. Verwenden Sie das Schlüsselwort **try,** um einen **try-Block** einzurichten. Führen Sie alle Programmanweisungen aus, die eine Ausnahme innerhalb eines **try-Blocks** auslösen können.

   Verwenden **catch** Sie das catch-Schlüsselwort, um einen **Catch-Block** einzurichten. Platzieren Sie Ausnahmebehandlungscode **catch** in einem catch-Block. Der Code im **catch-Block** wird nur ausgeführt, wenn der Code innerhalb des **try-Blocks** eine Ausnahme des in der **catch-Anweisung** angegebenen Typs auslöst.

   Das folgende Skelett **try** zeigt, wie Try-and-Catch-Blöcke normalerweise angeordnet sind: **catch**

   [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   Wenn eine Ausnahme ausgelöst wird, wird das Steuerelement an den ersten **catch-Block** übergibt, dessen Ausnahmedeklaration mit dem Typ der Ausnahme übereinstimmt. Sie können verschiedene Arten von Ausnahmen **catch** mit sequenziellen Catch-Blöcken wie unten aufgeführt selektiv behandeln:

   [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

Weitere Informationen finden Sie unter [Ausnahmen: Konvertieren von MFC-Ausnahmemakros](../mfc/exceptions-converting-from-mfc-exception-macros.md).

## <a name="see-also"></a>Siehe auch

[Ausnahmebehandlung](../mfc/exception-handling-in-mfc.md)
