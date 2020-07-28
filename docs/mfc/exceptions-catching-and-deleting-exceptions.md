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
ms.openlocfilehash: 5c1edd4c5d31d9a0e8e5270d074d25b5dd129a0f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87184246"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>Ausnahmen: Abfangen und Löschen von Ausnahmen

Die folgenden Anweisungen und Beispiele veranschaulichen, wie Sie Ausnahmen abfangen und löschen. Weitere Informationen zu den **`try`** **`catch`** Schlüsselwörtern, und **`throw`** finden Sie unter [modern C++ bewährte Methoden für Ausnahmen und Fehlerbehandlung](../cpp/errors-and-exception-handling-modern-cpp.md).

Die Ausnahmehandler müssen Ausnahme Objekte löschen, die Sie behandeln, da ein Fehler beim Löschen der Ausnahme immer dann einen Speicherplatz verursacht, wenn der Code eine Ausnahme abfängt.

Der- **`catch`** Block muss eine Ausnahme löschen, wenn:

- Der- **`catch`** Block löst eine neue-Ausnahme aus.

   Natürlich dürfen Sie die Ausnahme nicht löschen, wenn Sie die gleiche Ausnahme erneut auslösen:

   [!code-cpp[NVC_MFCExceptions#3](codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- Die Ausführung wird innerhalb des-Blocks zurückgegeben **`catch`** .

> [!NOTE]
> Verwenden Sie beim Löschen eines `CException` die-Member-Funktion, `Delete` um die Ausnahme zu löschen. Verwenden **`delete`** Sie das Schlüsselwort nicht, da es möglicherweise fehlschlägt, wenn die Ausnahme nicht auf dem Heap liegt.

#### <a name="to-catch-and-delete-exceptions"></a>So fangen Sie Ausnahmen ab und löschen Sie

1. Verwenden Sie das- **`try`** Schlüsselwort, um einen- **`try`** Block einzurichten. Führen Sie alle Programm Anweisungen aus, die möglicherweise eine Ausnahme in einem- **`try`** Block auslösen.

   Verwenden Sie das- **`catch`** Schlüsselwort, um einen- **`catch`** Block einzurichten. Platzieren Sie den Code für die Ausnahmebehandlung in einem- **`catch`** Block. Der Code im- **`catch`** Block wird nur ausgeführt, wenn der Code innerhalb des- **`try`** Blocks eine Ausnahme des Typs auslöst, der in der-Anweisung angegeben ist **`catch`** .

   Das folgende Gerüst zeigt, wie **`try`** -und- **`catch`** Blöcke normal angeordnet werden:

   [!code-cpp[NVC_MFCExceptions#4](codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   Wenn eine Ausnahme ausgelöst wird, übergibt die Steuerung an den ersten **`catch`** Block, dessen Exception-Declaration mit dem Typ der Ausnahme übereinstimmt. Sie können verschiedene Typen von Ausnahmen mit sequenziellen Blöcken selektiv verarbeiten, **`catch`** wie unten aufgeführt:

   [!code-cpp[NVC_MFCExceptions#5](codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

Weitere Informationen finden Sie unter [Ausnahmen: Umstellen von MFC-Ausnahme Makros](exceptions-converting-from-mfc-exception-macros.md).

## <a name="see-also"></a>Weitere Informationen

[Ausnahmebehandlung](exception-handling-in-mfc.md)
