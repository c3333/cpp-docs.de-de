---
title: Lesen und Schreiben von Dateien
ms.date: 11/04/2016
helpviewer_keywords:
- CFile class [MFC], objects
- examples [MFC], reading files
- files [MFC], writing to
- examples [MFC], writing to files
- files [MFC], reading
- MFC, file operations
- CFile class [MFC], reading and writing CFile objects
- reading files
- writing to files [MFC]
ms.assetid: cac0c826-ba56-495f-99b3-ce6336f65763
ms.openlocfilehash: 6c4b2b21bbfa19fb73997f8475cfa9a4047dc0ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371804"
---
# <a name="reading-and-writing-files"></a>Lesen und Schreiben von Dateien

Wenn Sie die Dateibearbeitungsfunktionen der C-Laufzeitbibliothek verwendet haben, werden MFC-Lese- und Schreibvorgänge vertraut angezeigt. In diesem Artikel wird beschrieben, `CFile` wie Sie direkt aus einem Objekt lesen und direkt in ein Objekt schreiben. Sie können auch gepufferte Datei-E/A mit der [CArchive-Klasse](../mfc/reference/carchive-class.md) erstellen.

#### <a name="to-read-from-and-write-to-the-file"></a>So lesen Sie aus der Datei und schreiben in die Datei

1. Verwenden `Read` Sie `Write` die und Memberfunktionen, um Daten in der Datei zu lesen und zu schreiben.

     - oder -

1. Die `Seek` Memberfunktion ist auch für den Wechsel zu einem bestimmten Offset innerhalb der Datei verfügbar.

`Read`nimmt einen Zeiger auf einen Puffer und die Anzahl der zu lesenden Bytes und gibt die tatsächliche Anzahl der gelesenen Bytes zurück. Wenn die erforderliche Anzahl von Bytes nicht gelesen werden konnte, da das Ende der Datei (EOF) erreicht ist, wird die tatsächliche Anzahl der gelesenen Bytes zurückgegeben. Wenn ein Lesefehler auftritt, wird eine Ausnahme ausgelöst. `Write`ist ähnlich `Read`wie , aber die Anzahl der geschriebenen Bytes wird nicht zurückgegeben. Wenn ein Schreibfehler auftritt, einschließlich nicht des Schreibens aller angegebenen Bytes, wird eine Ausnahme ausgelöst. Wenn Sie über `CFile` ein gültiges Objekt verfügen, können Sie daraus lesen oder darauf schreiben, wie im folgenden Beispiel gezeigt:

[!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]

> [!NOTE]
> Sie sollten normalerweise Eingabe-/Ausgabevorgänge innerhalb eines **try**/**catch-Ausnahmebehandlungsblocks** ausführen. Weitere Informationen finden Sie unter [Ausnahmebehandlung (Exception Handling, MFC)](../mfc/exception-handling-in-mfc.md).

## <a name="see-also"></a>Siehe auch

[Dateien](../mfc/files-in-mfc.md)
