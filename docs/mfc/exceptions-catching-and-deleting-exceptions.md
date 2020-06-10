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
ms.openlocfilehash: 50e3a3f8c064b2a054f0018e87c4e8782a5dc363
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618847"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>Ausnahmen: Abfangen und Löschen von Ausnahmen

Die folgenden Anweisungen und Beispiele veranschaulichen, wie Sie Ausnahmen abfangen und löschen. Weitere Informationen zu den Schlüsselwörtern "Try", " **catch**" und " **throw** " finden **Sie**unter [modern C++ bewährte Methoden für Ausnahmen und Fehlerbehandlung](../cpp/errors-and-exception-handling-modern-cpp.md).

Die Ausnahmehandler müssen Ausnahme Objekte löschen, die Sie behandeln, da ein Fehler beim Löschen der Ausnahme immer dann einen Speicherplatz verursacht, wenn der Code eine Ausnahme abfängt.

Der **catch** -Block muss eine Ausnahme löschen, wenn Folgendes erforderlich ist:

- Der **catch** -Block löst eine neue Ausnahme aus.

   Natürlich dürfen Sie die Ausnahme nicht löschen, wenn Sie die gleiche Ausnahme erneut auslösen:

   [!code-cpp[NVC_MFCExceptions#3](codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- Die Ausführung wird von innerhalb des **catch** -Blocks zurückgegeben.

> [!NOTE]
> Verwenden Sie beim Löschen eines `CException` die-Member-Funktion, `Delete` um die Ausnahme zu löschen. Verwenden Sie das Schlüsselwort **Delete** nicht, da es möglicherweise fehlschlägt, wenn sich die Ausnahme nicht auf dem Heap befindet.

#### <a name="to-catch-and-delete-exceptions"></a>So fangen Sie Ausnahmen ab und löschen Sie

1. Verwenden Sie das **try** -Schlüsselwort, um einen **try** -Block einzurichten. Führen Sie alle Programm Anweisungen aus, die möglicherweise eine Ausnahme in einem **try** -Block auslösen.

   Verwenden Sie das **catch** -Schlüsselwort, um einen **catch** -Block einzurichten. Platzieren Sie den Ausnahme Behandlungs Code in einem **catch** -Block. Der Code im **catch** -Block wird nur ausgeführt, wenn der Code im **try** -Block eine Ausnahme des Typs auslöst, der in der **catch** -Anweisung angegeben ist.

   Das folgende Gerüst zeigt, wie **try** -und **catch** -Blöcke normalerweise angeordnet werden:

   [!code-cpp[NVC_MFCExceptions#4](codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   Wenn eine Ausnahme ausgelöst wird, wird die Steuerung an den ersten **catch** -Block weitergeleitet, dessen Exception-Declaration mit dem Typ der Ausnahme übereinstimmt. Sie können verschiedene Typen von Ausnahmen mit sequenziellen **catch** -Blöcken selektiv verarbeiten, wie unten aufgeführt:

   [!code-cpp[NVC_MFCExceptions#5](codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

Weitere Informationen finden Sie unter [Ausnahmen: Umstellen von MFC-Ausnahme Makros](exceptions-converting-from-mfc-exception-macros.md).

## <a name="see-also"></a>Siehe auch

[Ausnahmebehandlung](exception-handling-in-mfc.md)
