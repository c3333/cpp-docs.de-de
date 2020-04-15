---
title: Dateien in MFC
ms.date: 11/04/2016
helpviewer_keywords:
- serialization [MFC], MFC files
- I/O [MFC], MFC classes
- files [MFC], MFC
- files [MFC], serialization
- binary access, binary file operations in MFC
- file I/O classes [MFC]
- I/O [MFC]
- persistence [MFC]
- MFC, file operations
- files [MFC], manipulating
- binary access [MFC]
ms.assetid: ae25e2c5-2859-4679-ab97-438824e93ce1
ms.openlocfilehash: 3a99c4143bbd27ba765b0289b80be8870a940f63
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365315"
---
# <a name="files-in-mfc"></a>Dateien in MFC

In der Microsoft Foundation Class Library (MFC) verarbeitet die Klasse [CFile](../mfc/reference/cfile-class.md) normale Datei-E/A-Vorgänge. Diese Artikelfamilie erklärt, wie Sie Dateien öffnen und schließen sowie Daten in diese Dateien lesen und schreiben. Außerdem werden Dateistatusvorgänge erläutert. Eine Beschreibung der Verwendung der objektbasierten Serialisierungsfunktionen von MFC als alternative Möglichkeit zum Lesen und Schreiben von Daten in Dateien finden Sie im Artikel [Serialisierung](../mfc/serialization-in-mfc.md).

> [!NOTE]
> Wenn Sie MFC-Objekte `CDocument` verwenden, übernimmt das Framework einen Großteil der Serialisierungsarbeit für Sie. Insbesondere erstellt und verwendet das `CFile` Framework das Objekt. Sie müssen nur Code in Ihre `Serialize` Außerkraftsetzung `CDocument`der Memberfunktion der Klasse schreiben.

Die `CFile` Klasse stellt eine Schnittstelle für allgemeine Binärdateioperationen bereit. Die `CStdioFile` `CMemFile` und-Klassen, die von `CFile` und von der `CSharedFile` Klasse abgeleitet abgeleitet `CMemFile` abgeleitet werden, liefern spezialisiertere Dateidienste.

Weitere Informationen zu Alternativen zur MFC-Dateibehandlung finden Sie unter [Dateiverarbeitung](../c-runtime-library/file-handling.md) in der *Laufzeitbibliotheksreferenz*.

Informationen zu `CFile` abgeleiteten Klassen finden Sie im [MFC-Hierarchiediagramm](../mfc/hierarchy-chart.md).

## <a name="what-do-you-want-to-do"></a>Was möchten Sie tun?

*CFile verwenden*

- [Öffnen einer Datei mit CFile](../mfc/opening-files.md)

- [Lesen und Schreiben einer Datei mit CFile](../mfc/reading-and-writing-files.md)

- [Schließen einer Datei mit CFile](../mfc/closing-files.md)

- [Zugriff auf Dateistatus mit CFile](../mfc/accessing-file-status.md)

*MFC Serialisierung verwenden (Objektpersistenz)*

- [Erstellen einer serialisierbaren Klasse](../mfc/serialization-making-a-serializable-class.md)

- [Serialisieren eines Objekts über ein CArchive-Objekt](../mfc/serialization-serializing-an-object.md)

- [Erstellen eines CArchive-Objekts](../mfc/two-ways-to-create-a-carchive-object.md)

- [CArchive-<\< und >> -Operatoren verwenden](../mfc/using-the-carchive-output-and-input-operators.md)

- [Speichern und Laden von CObjects und von CObject abgeleiteten Objekten über ein Archiv](../mfc/storing-and-loading-cobjects-via-an-archive.md)

## <a name="see-also"></a>Siehe auch

[Konzepte](../mfc/mfc-concepts.md)<br/>
[Allgemeine MFC-Themen](../mfc/general-mfc-topics.md)<br/>
[CArchive-Klasse](../mfc/reference/carchive-class.md)<br/>
[CObject-Klasse](../mfc/reference/cobject-class.md)
