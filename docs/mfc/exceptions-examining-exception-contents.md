---
title: 'Ausnahmen: Untersuchen von Ausnahmeinhalten'
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [MFC], MFC
- try-catch exception handling [MFC], MFC function exceptions
- catch blocks, MFC function exceptions
- CException class [MFC], class exceptions
- try-catch exception handling [MFC], exception contents
- throwing exceptions [MFC], exception contents
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
ms.openlocfilehash: 8554dda2f465aa058cea3d257c22ec38bc6e2c18
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625891"
---
# <a name="exceptions-examining-exception-contents"></a>Ausnahmen: Untersuchen von Ausnahmeinhalten

Obwohl das-Argument eines **catch** -Blocks fast jeden Datentyp aufweisen kann, lösen die MFC-Funktionen Ausnahmen von Typen aus, die von der-Klasse abgeleitet werden `CException` . Wenn Sie eine Ausnahme abfangen möchten, die von einer MFC-Funktion ausgelöst wird, schreiben Sie einen **catch** -Block, dessen Argument ein Zeiger auf ein- `CException` Objekt ist (oder ein von abgeleitetes Objekt `CException` , z `CMemoryException` . b.). Abhängig vom exakten Typ der Ausnahme können Sie die Datenmember des Ausnahme Objekts überprüfen, um Informationen über die jeweilige Ursache der Ausnahme zu sammeln.

Der- `CFileException` Typ verfügt beispielsweise über den- `m_cause` Datenmember, der einen enumerierten Typ enthält, der die Ursache der Datei Ausnahme angibt. Einige Beispiele für die möglichen Rückgabewerte sind `CFileException::fileNotFound` und `CFileException::readOnly` .

Im folgenden Beispiel wird gezeigt, wie der Inhalt eines untersucht wird `CFileException` . Andere Ausnahme Typen können ähnlich überprüft werden.

[!code-cpp[NVC_MFCExceptions#13](codesnippet/cpp/exceptions-examining-exception-contents_1.cpp)]

Weitere Informationen finden Sie unter [Ausnahmen: Freigeben von Objekten in Ausnahmen](exceptions-freeing-objects-in-exceptions.md) und [Ausnahmen: abfangen und Löschen von Ausnahmen](exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Siehe auch

[Ausnahmebehandlung](exception-handling-in-mfc.md)
