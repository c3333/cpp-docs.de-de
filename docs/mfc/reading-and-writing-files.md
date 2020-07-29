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
ms.openlocfilehash: f68fd5c48bce214329437cc13fc39da0c3ca7d2b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228582"
---
# <a name="reading-and-writing-files"></a>Lesen und Schreiben von Dateien

Wenn Sie die Datei Behandlungs Funktionen der C-Lauf Zeit Bibliothek verwendet haben, werden MFC-Lese-und-Schreibvorgänge vertraut angezeigt. In diesem Artikel wird beschrieben, wie Sie direkt aus einem-Objekt lesen und direkt darin schreiben `CFile` . Sie können auch eine gepufferte Datei-e/a mit der [CArchive](../mfc/reference/carchive-class.md) -Klasse ausführen.

#### <a name="to-read-from-and-write-to-the-file"></a>So lesen Sie und Schreiben in die Datei

1. Verwenden `Read` Sie die-und-Element `Write` Funktionen, um Daten in der Datei zu lesen und zu schreiben.

     Oder

1. Die `Seek` Member-Funktion ist auch zum Verschieben zu einem bestimmten Offset in der Datei verfügbar.

`Read`nimmt einen Zeiger auf einen Puffer und die Anzahl der zu lesenden Bytes und gibt die tatsächliche Anzahl von gelesenen Bytes zurück. Wenn die erforderliche Anzahl von Bytes nicht gelesen werden konnte, weil das Ende der Datei (EOF) erreicht ist, wird die tatsächliche Anzahl von gelesenen Bytes zurückgegeben. Wenn ein Lesefehler auftritt, wird eine Ausnahme ausgelöst. `Write`ähnelt `Read` , aber die Anzahl der geschriebenen Bytes wird nicht zurückgegeben. Wenn ein Schreibfehler auftritt und nicht alle angegebenen Bytes geschrieben werden, wird eine Ausnahme ausgelöst. Wenn Sie über ein gültiges- `CFile` Objekt verfügen, können Sie es aus dem Objekt lesen oder schreiben, wie im folgenden Beispiel gezeigt:

[!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]

> [!NOTE]
> Normalerweise sollten Eingabe-/Ausgabevorgänge innerhalb eines **`try`** / **`catch`** Ausnahme Behandlungs Blocks durchgeführt werden. Weitere Informationen finden Sie unter [Ausnahmebehandlung (MFC)](../mfc/exception-handling-in-mfc.md).

## <a name="see-also"></a>Siehe auch

[Dateien](../mfc/files-in-mfc.md)
